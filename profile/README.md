<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="profile/images/logo-dark.png">
    <img alt="uLogger" src="profile/images/logo-light.png" width="420">
  </picture>
</p>

<h3 align="center">Stop guessing at field failures. See what really happened.</h3>

uLogger is an AI-first observability platform for embedded systems. A tiny on-device agent continuously records what your firmware is doing — log events, crash state, register snapshots — and streams it to the cloud so you can debug field failures without ever physically touching the device.

Built for the embedded engineers who keep hearing *"can't reproduce"* on tickets from devices half a continent away.

---

## What it does

- **Pre-crash context capture.** A circular ring buffer records events on-device continuously. When a fault fires, the entire history leading up to it is preserved automatically — no rebuilds, no waiting for the bug to happen again.
- **Automatic crash reports.** Intercepts HardFault, BusFault, stack overflow, and watchdog resets. Captures registers, call stack, and buffered logs; persists across reboots.
- **Binary log compression up to ~90%.** Microsecond logging calls and a non-blocking write path, sized for LTE/NB-IoT and other constrained links.
- **Tiny footprint.** Core library under 4 KB of flash on ARM Cortex-M. Configurable static ring buffer, no heap dependency. Runs on devices with 64 KB flash / 8 KB RAM.
- **Fleet-wide correlation.** Group crashes across thousands of devices, detect regressions, and get alerted before customers report them.
- **AI root-cause analysis.** Structured crash data feeds AI tooling that pinpoints the offending code path — and can open a GitHub PR with a proposed fix.

## How you interact with it

- **Embedded agent (C library)** — `ulogger_init(&config)` at startup, `ulogger_log(...)` / `ulogger_assert(...)` macros throughout your firmware. See [`embedded_agent`](https://github.com/ulogger-ai/embedded_agent).
- **Holodeck** — the cloud dashboard at [holodeck.ulogger.ai](https://holodeck.ulogger.ai). Log search, crash reports, fleet correlation, anomaly alerts, API tokens.
- **uLogger Data Client + AI Skill** — a CLI that doubles as a skill for Claude Code, Cursor, GitHub Copilot, and other coding agents. Lets an agent query device logs, push log configurations, list debug modules, download cert bundles, and bootstrap uLogger into a project from natural language. See [ulogger.ai/ai-skill](https://ulogger.ai/ai-skill.html).
- **Examples** — working integrations in [`example-bluetooth-demo`](https://github.com/ulogger-ai/example-bluetooth-demo) (Silicon Labs EFR32BG22) and [`example-wifi-demo`](https://github.com/ulogger-ai/example-wifi-demo) (Silicon Labs SiWx917, Wi-Fi 6 direct-to-cloud). General library of examples in [`examples`](https://github.com/ulogger-ai/examples).

## Supported targets

ARM Cortex-M (STM32, nRF52, SAM/SAMD), Xtensa (ESP32/ESP8266), RISC-V (GD32VF, SiFive), and Linux gateways (Raspberry Pi, Yocto, Buildroot). Transport is MQTT-primary over mutual TLS, with adapters for Wi-Fi, Bluetooth, LoRa, Matter, Thread, 802.15.4, Ethernet, and Cellular LTE/NB-IoT. Offline buffering in non-volatile memory with store-and-forward on reconnect.

## Pricing

One usage-based plan, billed per active device per month. Every tier includes 400 KB/device/day and 90-day retention. 14-day free trial — no credit card.

| Devices | Price |
| --- | --- |
| 1–10 | Free |
| 11–100 | $0.50/device/mo |
| 101–500 | $0.30/device/mo |
| 501–2,500 | $0.20/device/mo |
| 2,501–20,000 | $0.15/device/mo |
| 20,000+ | [Custom — talk to us](https://ulogger.ai/book-demo.html) |

Full pricing at [ulogger.ai/pricing](https://ulogger.ai/pricing.html).

## Get started

- **Try it free** → [holodeck.ulogger.ai](https://holodeck.ulogger.ai?action=create-account)
- **Read the docs** → [ulogger.ai/documentation](https://ulogger.ai/documentation.html)
- **Book a technical demo** → [ulogger.ai/book-demo](https://ulogger.ai/book-demo.html)
- **Engineering blog (Breakpoint)** → [ulogger.ai/breakpoint](https://ulogger.ai/breakpoint.html)

---

<p align="center"><em>Built by engineers who've deployed more than a million devices in production IoT environments.</em></p>
