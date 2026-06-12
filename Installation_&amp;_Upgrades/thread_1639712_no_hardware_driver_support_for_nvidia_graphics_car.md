---
title: "no hardware driver support for nvidia graphics card"
date: 2010-12-07
forum: Installation &amp; Upgrades
---

### Post by jimbean on 2010-12-07
I have a nvidia gt 240 ddr5 card.

i try to enable it in system/administration/harware drivers tab 
and it stops and says instalation of this driver is not possible
then it tells me to look in my /var/log/jockey.log
this is what some of it says it ubuntu forums wont let me paste more than what is under this paragraph something about images more than 8



2010-12-07 01:23:15,358 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x904572c> about HardwareID('modalias', 'usb:v1532p0012d0100dc00dsc00dp00ic03isc01ip02')
2010-12-07 01:23:15,358 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x904572c> about HardwareID('modalias', 'usb:v046DpC215d0204dc00dsc00dp00ic03isc00ip00')
2010-12-07 01:23:15,358 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x904572c> about HardwareID('modalias', 'acpi:LNXSYSTM:')
2010-12-07 01:23:15,359 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x904572c> about HardwareID('modalias', 'acpi:PNP0303:PNP030B:')
2010-12-07 01:23:15,359 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x904572c> about HardwareID('modalias', 'pci:v000010DEd0000036Dsv0000105Bsd00000D06bc0Csc03i20')
2010-12-07 01:23:15,359 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x904572c> about HardwareID('modalias', 'pci:v000010DEd000002F9sv00000000sd00000000bc05sc00i00')
2010-12-07 01:23:15,359 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x904572c> about HardwareID('modalias', 'pci:v00001022d00001103sv00000000sd00000000bc06sc00i00')
2010-12-07 01:23:15,359 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x904572c> about HardwareID('modalias', 'pci:v000010DEd0000036Asv0000105Bsd00000D06bc05sc00i00')
2010-12-07 01:23:15,359 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x904572c> about HardwareID('modalias', 'pci:v000010DEd00000BE4sv00001682sd00003001bc04sc03i00')
2010-12-07 01:23:15,359 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x904572c> about HardwareID('modalias', 'input:b0017v0001p0001e0100-e0,1,2,k110,111,112,r0,1,amlsfw')
2010-12-07 01:23:15,359 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x904572c> about HardwareID('modalias', 'acpi:PNP0000:')
2010-12-07 01:23:15,359 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x904572c> about HardwareID('modalias', 'usb:v1D6Bp0002d0206dc09dsc00dp00ic09isc00ip00')
2010-12-07 01:23:15,360 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x904572c> about HardwareID('modalias', 'pci:v000010DEd00000369sv0000105Bsd00000D06bc05sc00i00')
2010-12-07 01:23:15,360 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x904572c> about HardwareID('modalias', 'pci:v00001022d00001101sv00000000sd00000000bc06sc00i00')
2010-12-07 01:23:15,360 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x904572c> about HardwareID('modalias', 'pci:v000010DEd00000368sv0000105Bsd00000D06bc0Csc05i00')
2010-12-07 01:23:15,360 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x904572c> about HardwareID('modalias', 'input:b0019v0000p0001e0000-e0,1,k74,ramlsfw')
2010-12-07 01:23:15,360 DEBUG: querying driver db <jockey.detection.OpenPrintingDriverDB instance at 0x904572c> about HardwareID('modalias', 'acpi:PNP0C01:')
2010-12-07 01:23:24,546 DEBUG: Installing package: nvidia-glx-195
2010-12-07 01:23:26,473 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-12-07 01:23:26,474 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2010-12-07 01:24:10,902 DEBUG: Installing package: nvidia-glx-190
2010-12-07 01:24:11,796 WARNING: modinfo for module nvidia failed: ERROR: modinfo: could not find module nvidia

2010-12-07 01:24:11,797 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting

---

