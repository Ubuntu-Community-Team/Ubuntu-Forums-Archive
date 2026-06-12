---
title: "bluetooth services missing"
date: 2008-10-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by m.hataj on 2008-10-19
i can't configure services by bluetooth-applet, the services tab is missing.

that's been a neat thing on hardy to set up bt-networking - why is it missing?

it's an actual intrepid ubuntu
Linux corona 2.6.27-7-generic #1 SMP Fri Oct 17 22:24:30 UTC 2008 x86_64 GNU/Linux

bluetooth-services are available, i need pan and dunroot@corona:/etc/bluetooth# sdptool browse local
Browsing FF:FF:FF:00:00:00 ...
Service Name: Headset Audio Gateway
Service RecHandle: 0x10000
Service Class ID List:
  "Headset Audio Gateway" (0x1112)
  "Generic Audio" (0x1203)
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 12
Profile Descriptor List:
  "Headset" (0x1108)
    Version: 0x0100

Service Name: Audio Source
Service RecHandle: 0x10001
Service Class ID List:
  "Audio Source" (0x110a)
Protocol Descriptor List:
  "L2CAP" (0x0100)
    PSM: 25
  "AVDTP" (0x0019)
    uint16: 0x100
Profile Descriptor List:
  "Advanced Audio" (0x110d)
    Version: 0x0100

Service Name: AVRCP TG
Service RecHandle: 0x10002
Service Class ID List:
  "AV Remote Target" (0x110c)
Protocol Descriptor List:
  "L2CAP" (0x0100)
    PSM: 23
  "AVCTP" (0x0017)
    uint16: 0x103
Profile Descriptor List:
  "AV Remote" (0x110e)
    Version: 0x0103

Service Name: AVRCP CT
Service RecHandle: 0x10003
Service Class ID List:
  "AV Remote" (0x110e)
Protocol Descriptor List:
  "L2CAP" (0x0100)
    PSM: 23
  "AVCTP" (0x0017)
    uint16: 0x103
Profile Descriptor List:
  "AV Remote" (0x110e)
    Version: 0x0103

Service Name: BlueZ PANU service
Service Description: BlueZ PAN service
Service RecHandle: 0x10004
Service Class ID List:
  "PAN User" (0x1115)
Protocol Descriptor List:
  "L2CAP" (0x0100)
    PSM: 15
  "BNEP" (0x000f)
    Version: 0x0100
    SEQ16: 800 806
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "PAN User" (0x1115)
    Version: 0x0100

Service Name: BlueZ GN service
Service Description: BlueZ PAN service
Service RecHandle: 0x10005
Service Class ID List:
  "PAN Group Network" (0x1117)
Protocol Descriptor List:
  "L2CAP" (0x0100)
    PSM: 15
  "BNEP" (0x000f)
    Version: 0x0100
    SEQ16: 800 806
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "PAN Group Network" (0x1117)
    Version: 0x0100

Service Name: BlueZ NAP service
Service Description: BlueZ PAN service
Service RecHandle: 0x10006
Service Class ID List:
  "Network Access Point" (0x1116)
Protocol Descriptor List:
  "L2CAP" (0x0100)
    PSM: 15
  "BNEP" (0x000f)
    Version: 0x0100
    SEQ16: 800 806
Language Base Attr List:
  code_ISO639: 0x656e
  encoding:    0x6a
  base_offset: 0x100
Profile Descriptor List:
  "Network Access Point" (0x1116)
    Version: 0x0100

root@corona:/etc/bluetooth#

---

