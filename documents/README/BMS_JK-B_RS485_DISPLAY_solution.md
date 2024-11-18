# YamBMS - JK-B BMS RS485 DISPLAY Solution

[![Badge License: GPLv3](https://img.shields.io/badge/License-GPLv3-brightgreen.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![Badge Version](https://img.shields.io/github/v/release/Sleeper85/esphome-yambms?include_prereleases&color=yellow&logo=DocuSign&logoColor=white)](https://github.com/Sleeper85/esphome-yambms/releases/latest)
![GitHub stars](https://img.shields.io/github/stars/Sleeper85/esphome-yambms)
![GitHub forks](https://img.shields.io/github/forks/Sleeper85/esphome-yambms)
![GitHub watchers](https://img.shields.io/github/watchers/Sleeper85/esphome-yambms)

## External component

[esphome-jk-bms](https://github.com/syssi/esphome-jk-bms) by [@syssi](https://github.com/syssi)

## Schematic and setup instructions

> [!CAUTION]
> The `jk_bms_display` component does not provide all the information needed for an optimal operation of `YamBMS`.
> The missing information has been added in the code by fixed values.
> e.g. it's not possible to know if the BMS is `online` or if the BMS is `equalizing` the cells.

### JK-B2A8S20P

```

│                   JK-B2A8S20P                   │
│                                                 │
│   Temp    CAN    GPS     Display    Balancer    │
└──[oooo]──[ooo]──[oooo]──[oooooo]──[oooooooooo]──┘
                           ││││││
                           │││││└─ K-
                           ││││└── K+
                           │││└─── GND ( not common with B- , isolated ? )
                           ││└──── B
                           │└───── A
                           └────── VCC = +/- 11.5V
```

### JK-BD6A2xS10P and JK-BxA24SxxP

```

│           JK-BD6A2xS10P, JK-BxA24SxxP           │
│                                                 │
│     CAN   GPS      Display     Heat             │
└────[ooo]─[oooo]───[oooooo]───[ooooooo]──────────┘
                     ││││││
                     │││││└─ VCC       ┌───────────────┐        ┌─────────────────┐
                     ││││└── A ────────│A+          GND│────────│GND              │
                     │││└─── B ────────│B-  RS485   RXD│────────│RX    ESP32/     │
                     ││└──── GND       │    to TTL  TXD│        │TX    ESP8266 GND│──────
                     │└───── K+        │    module  VCC│────────│5V            VCC│──────
                     └────── K-        └───────────────┘        └─────────────────┘
```

### Power Button

```
K-   o-------[ 100kΩ ]-----o  /
                             /---|
K+   o---------------------o/
```