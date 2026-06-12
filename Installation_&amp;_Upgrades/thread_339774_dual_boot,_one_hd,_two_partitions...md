---
title: "dual boot, one hd, two partitions.."
date: 2007-01-16
forum: Installation &amp; Upgrades
---

### Post by Mia_tech on 2007-01-16
guys, I have looked at some examples of the "grub.lst" file to try solving my dilemma, but I want to know what actually on that file do I need to change in order to boot windows by default, because several people are using my computer in which I have a dual boot systems Winxp and ubuntu both on same hard drive and by default boots up in ubuntu and people don't know what it is, so I have to boot up the coputer and select windows at boot up time, anyhow, what exactly do I need to change in the grub.lst file to set winxp as default during boot up?

thanks all

---

### Post by taurus on 2007-01-16
Change the "default     0" to whatever entry your XP is, probably the fourth entry which means it should look like "default     3" in /boot/grub/menu.lst.

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by Bartender on 2007-01-16
HI, Mia - 
GRUB will automatically boot Linux.  Hey, Windows doesn't share anything willingly, so it's only fair.

[http://www.ubuntuforums.org/showthread.php?t=297136&highlight=windows+first](http://www.ubuntuforums.org/showthread.php?t=297136&highlight=windows+first)

---

### Post by Mia_tech on 2007-01-16
> **Bartender said:**
> HI, Mia - 
GRUB will automatically boot Linux.  Hey, Windows doesn't share anything willingly, so it's only fair.

[http://www.ubuntuforums.org/showthread.php?t=297136&highlight=windows+first](http://www.ubuntuforums.org/showthread.php?t=297136&highlight=windows+first)

no, I agree with that, usually every time you install multiple operating systems in your computer, the computer will by default boot to the last install, unless you change it at the boot.ini file, but in this case Im using linux(ubuntu) which I'm completely hooked on, been a network admin for quite some time, since started to use ubuntu has become my linux of choice.
thanks all for the help

---

