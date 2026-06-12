---
title: "Hardy Triple boot with XP and Vista Error 15 on boot"
date: 2008-06-29
forum: Installation &amp; Upgrades
---

### Post by spoons27 on 2008-06-29
Hello can you help me please I have 4 Drives on my PC C,D,E,F.
C = XP Professional
D = Data
E = Data
F = Vista Premium
I ran the install CD from within XP and set it to use 10Gb on C drive. On rebooting I was presented with the following boot options  1:XP, 2:Vista, 3:Ubuntu.
Both windows options function normally but selecting Ubuntu gives an error 15 file not found.
I should say that the default OS is Vista.

---

### Post by Licurgo on 2008-07-01
spoons27:
I can see that you're new in Ubuntu (It's your first post)
First: Insert and run your Ubuntu CD and select the LIVE mode
Second:
-Open a terminal (Type Applications-Accessories-Terminal)
-Type in the terminal sudo grub
-Type find /boot/grub/stage1
-Appears an output
-Type root (hd?,?) ? is the output
-Type setup (hd0)
-Type quit

Then go to /boot/grub/menu.lst
edit the file menu.lst
at the end write:

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:

# This entry automatically added by the Debian installer for an existing
# Windows installation on /dev/hda1.
title		Windows 95/98/NT/2000
root		(hd0,0)
makeactive
chainloader	+1



Why you installed Vista and XP?
There are many problems on dual boot's with vista and ubuntu
Enjoy your new operating system
:lolflag:

---

### Post by Licurgo on 2008-07-02
spoons27:
What happened ?
Succeed ??
:guitar:

---

