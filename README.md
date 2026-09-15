<div align="center">

<img src="https://raw.githubusercontent.com/ParallaxCloud/.github/main/assets/parallax-logo.png" width="120" alt="ParallaxCloud logo">

# ParallaxCloud

### Infrastructure for secure, observable and distributed networking.

Building a cohesive networking ecosystem — from low-level network cores and VPN clients to orchestration, observability and infrastructure control.

<br>

![Go](https://img.shields.io/badge/Go-00ADD8?style=for-the-badge&logo=go&logoColor=white)
![Rust](https://img.shields.io/badge/Rust-000000?style=for-the-badge&logo=rust&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white)
![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![gRPC](https://img.shields.io/badge/gRPC-0A8080?style=for-the-badge)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)

</div>

---

## 🌌 About ParallaxCloud

**ParallaxCloud** develops software for operating and connecting distributed network infrastructure.

The ecosystem is designed around a simple idea: networking software should be **fast, observable, modular, automatable and maintainable** from the first production deployment to a large distributed fleet.

Our projects cover multiple layers of the stack:

- infrastructure control planes;
- VPN and proxy clients;
- distributed node management;
- network-core development;
- telemetry and observability;
- subscription and configuration delivery;
- secure control-plane communication;
- cross-platform desktop and mobile applications.

---

## 🚀 Projects

<table>
<tr>
<td width="50%" valign="top">

### ⚡ Parallax Axis

Distributed VPN infrastructure control plane.

Axis brings servers, users, subscriptions, fleet operations, telemetry and configuration delivery into a single operational environment.

**Highlights**

- Centralized server and inbound management
- User, group and tariff management
- gRPC + mTLS control plane
- Visor agents for remote VPS nodes
- Fleet deploy / reinstall / update orchestration
- Runtime configuration synchronization
- Streaming telemetry and traffic statistics
- Event-sourced fleet update journal
- Subscription delivery for compatible clients
- PostgreSQL + Redis backend
- Desktop manager built with Wails + React

</td>
<td width="50%" valign="top">

### 🖥️ Parallax Client

Cross-platform desktop VPN client for Windows and Linux.

The client is built around multiple network cores and flexible routing rather than a single fixed tunnel model.

**Highlights**

- sing-box and Xray-core support
- Per-process UDP filtering
- Smart direct / proxy routing
- Hot-swap server switching
- Kill switch
- TUN mode
- Subscription and configuration import
- Windows and Linux support
- Local-first logs and crash diagnostics

</td>
</tr>

<tr>
<td width="50%" valign="top">

### 📱 ParallaxVPN Android

Mobile client for the Parallax ecosystem.

Designed to provide a native Android entry point for Parallax-managed infrastructure and compatible network configurations.

> **Status:** active development.

</td>
<td width="50%" valign="top">

### ⚙️ Axion Core

Next-generation network core being developed as part of the Parallax ecosystem.

Axion focuses on a clean, modular architecture with first-class telemetry, explicit APIs and a design suitable for embedding into other software.

**Design goals**

- Modular protocol architecture
- Direct metrics APIs instead of log parsing
- Per-user observability and bandwidth controls
- Accurate runtime session state
- Extensible configuration sources
- Importable core modules
- High-performance networking
- Compatibility paths with existing ecosystems

> **Status:** experimental / active development.

</td>
</tr>
</table>

---

## 🏗️ Ecosystem architecture

```text
                              ParallaxCloud

             ┌────────────────────┬────────────────────┐
             │                    │                    │
             ▼                    ▼                    ▼
      Desktop Client       Android Client        Operator UI
      Parallax Client      ParallaxVPN           Axis Manager
             │                    │                    │
             └──────────────┬─────┴──────────────┬─────┘
                            │                    │
                      subscriptions          gRPC / mTLS
                            │                    │
                            ▼                    ▼
                   ┌──────────────────────────────────┐
                   │        Parallax Axis             │
                   │       Control Plane              │
                   │                                  │
                   │ Users • Servers • Fleet • PKI   │
                   │ Telemetry • Audit • Delivery    │
                   └────────────────┬─────────────────┘
                                    │
                              gRPC mTLS
                                    │
                                    ▼
                     ┌──────────────────────────┐
                     │      Visor Agents        │
                     │   Distributed VPS nodes  │
                     └─────────────┬────────────┘
                                   │
                                   ▼
                     ┌──────────────────────────┐
                     │      Network Core        │
                     │    Xray / Axion / ...    │
                     └──────────────────────────┘
```

---

## 🧠 Engineering principles

### Security by default

Control-plane communication should use authenticated and encrypted channels. Sensitive infrastructure operations are designed around explicit trust boundaries, PKI and auditability.

### Observability is part of the architecture

Metrics, runtime state, audit data and diagnostics should be first-class interfaces rather than information reconstructed from logs after something breaks.

### Clean boundaries

Core networking, orchestration, UI, persistence and delivery systems should evolve independently through versioned contracts and well-defined modules.

### Automation over repetitive operations

Provisioning, fleet updates, runtime synchronization, recovery and configuration delivery should be automated wherever practical.

### Compatibility without architectural lock-in

ParallaxCloud projects aim to interoperate with established networking ecosystems while preserving the ability to evolve their own architecture.

### Performance with maintainability

Low-level performance matters, but not at the cost of turning infrastructure into an unmaintainable collection of special cases.

---

## 🔐 Security model

Security-sensitive components of the ecosystem are built around explicit trust and transport boundaries.

Current Axis architecture includes:

- mTLS for manager ↔ backend communication;
- mTLS for backend ↔ visor agent communication;
- automated PKI provisioning;
- SSH host-key pinning for remote deployment workflows;
- API version negotiation;
- audit logging for critical operations;
- rollback and recovery paths for fleet updates.

Security work is treated as an ongoing engineering process rather than a one-time feature.

---

## 📊 Observability

ParallaxCloud treats observability as a core capability of infrastructure software.

The current platform direction includes:

- live CPU, RAM, disk and network metrics;
- per-server traffic statistics;
- runtime status streaming;
- historical time-series rollups;
- audit logs;
- system profiling;
- diagnostic snapshots and dumps;
- direct metrics APIs for future network-core components.

---

## 🧰 Technology

| Area | Technologies |
|---|---|
| Backend services | Go |
| Network-core development | Go / Rust |
| Desktop applications | Rust / Go + React |
| Frontend | TypeScript, React |
| RPC & contracts | gRPC, Protocol Buffers |
| Primary database | PostgreSQL |
| Events / streaming | Redis |
| Infrastructure | Docker, Linux |
| Security | mTLS, PKI, SSH host-key pinning |
| Existing network runtimes | Xray-core, sing-box |

---

## 🧩 Current platform components

### Axis control plane

The current Axis backend manages multiple bounded operational areas including infrastructure, identity, telemetry, subscriptions, audit, PKI and releases.

### Visor agents

Visor agents run on distributed VPS nodes and provide the control plane with a secure operational channel for configuration, health state, telemetry and runtime lifecycle management.

### Subscription delivery

Axis can generate configuration formats compatible with existing client applications and provide persistent per-user subscription endpoints.

### Desktop clients

Parallax desktop software targets native Windows and Linux workflows while keeping modern React-based interfaces and native networking capabilities.

---

## 🛣️ Direction

ParallaxCloud is moving toward a more integrated networking platform where infrastructure, clients and the network core can share common concepts and contracts.

Key areas of active development include:

- Axion Core;
- broader client coverage;
- richer network observability;
- protocol and runtime extensibility;
- safer fleet orchestration;
- compatibility with established network-core ecosystems;
- stronger automation around deployment and recovery.

---

## 🚧 Project status

ParallaxCloud is under active development.

Some repositories are private while architecture, compatibility layers, security boundaries and public interfaces are still evolving.

Public APIs, repository visibility and release policies may change as individual projects mature.

---

## 🤝 Contributing

Contribution rules depend on the individual repository.

Some ParallaxCloud projects are currently proprietary or source-available rather than open source. Check the repository's `LICENSE`, `CONTRIBUTING.md` and development guidelines before submitting changes or redistributing code.

---

## 📬 Contact

For project-related communication, use the contact details published in the corresponding repository.

For security-sensitive reports, avoid posting private infrastructure details in public issues.

---

<div align="center">

## ParallaxCloud

### Build. Connect. Observe. Control.

**Infrastructure for secure, observable and distributed networking.**

</div>
