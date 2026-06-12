---
title: "I haven't sound after upgrade :("
date: 2006-11-06
forum: Installation &amp; Upgrades
---

### Post by Markosek on 2006-11-06
Hello everyone! I don't speak English very well and I have a big problem.
I lose sound after upgrade my Ubuntu Dapper to Edgy Elf. :( I've got two sound cards - VIA AC97 on mobo and C-Media on PCI.
```
arkos@markos-desktop $ cat /proc/asound/cards 
 0 [rev50          ]: VIA686A - VIA 82C686A/B rev50 
                      VIA 82C686A/B rev50 with ALC100,100P at 0xdc00, irq 5 
 1 [CMI8738MC6     ]: CMI8738-MC6 - C-Media PCI CMI8738-MC6 
                      C-Media PCI CMI8738-MC6 (model 55) at 0xe800, irq 10
```
When I start amaroK in console it show:
```
X Error: BadDevice, invalid or uninitialized input device 154 
  Major opcode:  143 
  Minor opcode:  3 
  Resource id:  0x0 
Failed to open device 
X Error: BadDevice, invalid or uninitialized input device 154 
  Major opcode:  143 
  Minor opcode:  3 
  Resource id:  0x0 
Failed to open device 
Amarok: [Loader] Starting amarokapp.. 
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp. 
X Error: BadDevice, invalid or uninitialized input device 154 
  Major opcode:  143 
  Minor opcode:  3 
  Resource id:  0x0 
Failed to open device 
X Error: BadDevice, invalid or uninitialized input device 154 
  Major opcode:  143 
  Minor opcode:  3 
  Resource id:  0x0 
Failed to open device 
QLayout "unnamed" added to QVBox "unnamed", which already has a layout 
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow 
Amarok: [Loader] Amarok is taking a long time to load! Perhaps something has gone wrong?
```
And in X I see window:
```
Xine can't start any sound drivers
```
What I do wrong? Please help me! :(

---

