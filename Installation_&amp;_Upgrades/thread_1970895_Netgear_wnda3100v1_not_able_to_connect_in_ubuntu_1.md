---
title: "Netgear wnda3100v1 not able to connect in ubuntu 12.04"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by Badshaah on 2012-05-01
**Netgear wnda3100v1 Wireless Adapter** not able to connect in **ubuntu 12.04** **64 bit**.. I can't understand what wrong with it.. I spend almost 2 days before it was working fine when i initially install **ubuntu 11.10 64 bit**.. Although disconnect after 30 to 40 minutes but still it let me do my work but after installing **12.04** **64 bit**.. I wish i could connect once.. It would be great if any one from here help me in this thanks.. I alread did lot research to find a way to get fised but in vain..Below is some command which i run to diagnose problem but not helpful.. 

** $ nm-tool**

NetworkManager Tool

State: connecting

- Device: wlan0  [Home] --------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            carl9170
  State:             connecting (configuring)
  Default:           no
  HW Address:        00:1F:33:E8:18:F0

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    BH-IT:           Infra, 14:D6:4D:16:1D:AF, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA
    BLUEBIRD_Ph:03444111108: Infra, 00:02:6F:4C:E2:F3, Freq 2412 MHz, Rate 11 Mb/s, Strength 57 WEP
    Home:            Infra, 00:1E:E3:EF:20:FE, Freq 2412 MHz, Rate 54 Mb/s, Strength 72 WPA


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unavailable
  Default:           no
  HW Address:        00:10:B5:C0:B8:4A

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        00:13:20:AF:AB:EB

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

**$ lsusb**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0846:9010 NetGear, Inc. WNDA3100v1 802.11abgn [Atheros AR9170+AR9104]
Bus 001 Device 004: ID 0951:1643 Kingston Technology DataTraveler G3 4GB
Bus 003 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

---

### Post by andymnc on 2012-05-06
same problem here. also with 32bit version!
i can see the connection up, but no data transfer, so navigation is completely lost

---

