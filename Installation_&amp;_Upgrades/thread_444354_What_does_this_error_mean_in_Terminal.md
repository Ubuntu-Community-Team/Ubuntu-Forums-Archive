---
title: "What does this error mean in Terminal?"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by geek2330 on 2007-05-15
I am looking to edit the grub and typed the following command in Terminal:

gksudo gedit /boot/grub/menu.lst

[COLOR="Red"]X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device[/COLOR]


However grub opened fine.

---

### Post by Topsiho on 2007-05-15
The command is OK, I just tried it myself, and all is OK: gedit was openened after I entered my password, with the menu.lst file in it.

What caused the error messages: me don' t know :)

Topsiho

---

