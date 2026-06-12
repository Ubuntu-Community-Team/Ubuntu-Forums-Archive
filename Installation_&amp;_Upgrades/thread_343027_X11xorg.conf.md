---
title: "X11/xorg.conf"
date: 2007-01-20
forum: Installation &amp; Upgrades
---

### Post by DapperMe17 on 2007-01-20
Fresh install of Kubuntu 6.10, in an attempt to open the xorg.conf file to update nvidia driver detail, I received the following error. 

Any ideas?


xx@xx-desktop:~$ sudo kwrite /etc/X11/xorg.conf
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

---

### Post by meng on 2007-01-20
What about:
kdesu kwrite /etc/X11/xorg.conf

---

### Post by NeoLithium on 2007-01-20
well, sudo is meant for command line stuff; basically, if you're using a program that will open up a GUI window, like kwrite, use kdesu instead:

kdesu kwrite /etc/X11/xorg.conf

There are a few reasons to do so; there's a threat somewhere on it; but I'm not sure where it is ;)

---

### Post by DapperMe17 on 2007-01-20
Thanks guys!

I gave your advise a whirl & came up with this...


(ps...the xorg.conf file DOES come up after the following error report...should I just be disregarding the terminal error report as a meaningless quirk?



xx@xx-desktop:~$ kdesu kwrite /etc/X11/xorg.conf
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

---

