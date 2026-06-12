---
title: "Quake 3"
date: 2006-12-25
forum: Installation &amp; Upgrades
---

### Post by GregaS on 2006-12-25
When I want to change system settings in quake (resolution...) it crashes and this is output from console:

> Loading dll file ui.
Failed to load dll, looking for qvm.
Loading vm file vm/ui.qvm.
VM file ui compiled to 902626 bytes of code
30 arenas parsed
32 bots parsed
RE_Shutdown( 1 )
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  135 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x3800002
  Serial number of failed request:  81
  Current serial number in output stream:  83

The second problem is with installation of patch 1.16. I try to install patch with:

sudo sh linuxq3apoint-1.16n.x86.run

This is console output:

> X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
konsole: ERROR: can not execute ./linuxq3apoint-1.16n.x86.run

Any ideas? Help please.

---

