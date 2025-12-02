# ⚡ NovaTronix

> **The Operating System for Circular Electronics.**
> Management of e-waste, repair documentation, modular refurbishment, and critical material recovery.

[](https://www.google.com/search?q=https://github.com/novaeco-tech/novatronix/actions)
[](https://opensource.org/licenses/MIT)
[](https://www.google.com/search?q=https://electronics.novaeco.tech)

**NovaTronix** is the Vertical Sector dedicated to keeping electronics alive longer and recovering them efficiently when they die. While `NovaMake` handles the creation of new goods, **NovaTronix** handles the complex diagnostics, repair, and disassembly of complex circuitry.

It acts as the compliance engine for the **EU WEEE Directive** (Waste Electrical and Electronic Equipment) and the **Right to Repair** movement.

-----

## 🎯 Value Proposition

E-waste is the world's fastest-growing waste stream. **NovaTronix** solves the "Black Box" problem of modern electronics:

1.  **Democratized Repair:** Providing technicians with schematics, firmware tools, and 3D-printable spare part files (via `NovaMake`) for proprietary devices.
2.  **Urban Mining:** Identifying valuable components (Gold, Palladium, Lithium) on a scrap PCB before it is shredded, shifting from "Waste Management" to "Asset Recovery."
3.  **Component Harvesting:** Facilitating the testing and resale of working chips/screens from dead devices back into the market via `NovaTrade`.

-----

## 🏗️ Architecture (The Diagnostics Loop)

NovaTronix is a data-heavy sector. It links physical diagnostic tools (multimeters, battery testers) with cloud intelligence.

```mermaid
graph TD
    User((Technician)) -->|HTTPS| UI[NovaTronix Dashboard]
    UI -->|REST| API[NovaTronix API]
    
    subgraph "The Workbench (NovaInfra)"
        API -->|USB/Serial| Device[Connected Device]
        Device -->|Telemetry| Health[Battery/Chip Stats]
    end

    subgraph "The Intelligence Layer"
        UI -->|Upload Photo| Mind[NovaMind]
        Mind -->|Identify Component| API
        Mind -->|Suggest Repair| Policy[Repair Guide DB]
    end

    subgraph "The Value Chain"
        API -->|Update History| Mat[NovaMaterial (DPP)]
        API -->|Sell Spare Part| Trade[NovaTrade]
        API -->|Log E-Waste| Recycle[NovaRecycle]
    end
```

### Integrated Services

  * **[NovaMaterial](https://www.google.com/search?q=https://materials.novaeco.tech):** Hosts the "Electronics Passport." Tracks the specific chemical composition of batteries and the origin of conflict minerals (Tantalum, Cobalt).
  * **[NovaMind](https://www.google.com/search?q=https://mind.novaeco.tech):** The visual cortex. Uses Computer Vision to identify specific capacitors or burnt fuses on a circuit board.
  * **[NovaRecycle](https://www.google.com/search?q=https://recycling.novaeco.tech):** The destination for boards that cannot be fixed. NovaTronix tells NovaRecycle *exactly* what metals are in the shredder load.
  * **[NovaSkills](https://www.google.com/search?q=https://skills.novaeco.tech):** Verifies that the person performing a dangerous Li-Ion battery swap is certified to do so.

-----

## ✨ Key Features

### 1\. The "Fix-It" Engine

A collaborative library of repair guides.

  * **Input:** Scan the barcode of a washing machine or smartphone.
  * **Output:** Exploded view schematics, error code lookup, and a "Repairability Score."
  * **Parts Link:** One-click ordering of replacement fuses or screens via `NovaTrade`.

### 2\. PCB Value Scanner

Used by e-waste processors.

  * **Process:** A camera scans a bin of old motherboards.
  * **Analysis:** `NovaMind` identifies "Intel i7 CPU" (Resell) vs "Generic Capacitor" (Recycle).
  * **Valuation:** Estimates the recoverable gold/copper yield based on current market prices.

### 3\. Battery Health Ledger

Batteries are the weak link in electronics.

  * Reads the BMS (Battery Management System) data via `NovaInfra`.
  * Determines if a battery is:
      * **Healthy (\>80%):** Keep in device.
      * **Second Life (60-80%):** Repurpose for stationary grid storage (`NovaEnergy`).
      * **Dead (\<60%):** Send to chemical recycling (`NovaChem`).

### 4\. Critical Raw Materials (CRM) Tracking

Automated reporting for the **EU Critical Raw Materials Act**.

  * Calculates exactly how much Lithium, Cobalt, and Rare Earth Elements are passing through the repair facility.

-----

## 🚀 Getting Started

We use **DevContainers** to provide a consistent development environment.

### Prerequisites

  * Docker Desktop
  * VS Code (with Remote Containers extension)

### Installation

1.  **Clone the repo:**
    ```bash
    git clone https://github.com/novaeco-tech/novatronix.git
    cd novatronix
    ```
2.  **Open in VS Code:**
      * Run `code .`
      * Click **"Reopen in Container"** when prompted.
3.  **Start the Sector:**
    ```bash
    make dev
    ```
      * **Dashboard:** http://localhost:3000
      * **API:** http://localhost:8000/docs

### Configuration (`.env`)

```ini
# Sector Config
REPAIR_DATABASE_SOURCE=OPEN_REPAIR_ALLIANCE
WEEE_COMPLIANCE_MODE=EU_2026

# Integrations
NOVAMIND_URL=http://novamind-api:50051
NOVAMATERIAL_URL=http://novamaterial-api:8000
NOVARECYCLE_URL=http://novarecycle-api:8000
```

-----

## 📂 Repository Structure

This is a Monorepo containing the sector's specific logic.

```text
novatronix/
├── api/                # Python/FastAPI (Domain Logic)
│   ├── src/
│   │   ├── diagnostics/ # Logic to parse error codes/BMS data
│   │   ├── valuation/   # Algorithms for scrap value calc
│   │   └── manuals/     # Indexer for repair PDFs/XMLs
├── app/                # React/Next.js Frontend (Technician Dashboard)
│   ├── src/
│   │   ├── scanner/     # Camera UI for PCB recognition
│   │   └── guides/      # Interactive Step-by-Step UI
├── website/            # Documentation (Docusaurus)
└── tests/              # Integration tests
```

-----

## 🧪 Testing

We use **Hardware Simulation** for testing.

  * **BMS Test:** `make test-battery`
      * Simulates a battery reporting 70% State of Health (SoH). Asserts that the system flags it for "Stationary Storage Reuse" rather than "Recycling."
  * **Valuation Test:** `make test-value`
      * Inputs a list of 50 PCBs. Verifies that the calculated gold recovery value matches the reference commodity price index.

-----

## 🤝 Contributing

We need contributors with backgrounds in **Electrical Engineering**, **Hardware Hacking**, and **Computer Vision**.
See [CONTRIBUTING.md](https://www.google.com/search?q=../.github/CONTRIBUTING.md) for details.

**Maintainers:** `@novaeco-tech/maintainers-sector-novatronix`