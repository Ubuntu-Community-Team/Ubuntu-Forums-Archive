---
title: "restarting at the end of installation dual boot"
date: 2017-03-04
forum: Installation &amp; Upgrades
---

### Post by tulliod on 2017-03-04
Hello, 
I'm trying to do a dual boot windows-ubuntu installation from USB, everything runs smooth but at the end of the installation I re-start following the instructions and the machine restarts windows 10 without showing the Grub screen. I reinstalled
from USB and the system asked if I wanted to erase ubuntu and re install it,  I did it but it restarts windows again. 
I used the same USB in another laptop and it worked. I'm lost...:confused:
thank you

---

### Post by yancek on 2017-03-04
Windows 10 pre-installed is uefi.  Dual booting windows 10 uefi with Ubuntu is explained at the link below.  The first thing you need to verify is whether your windows is uefi.  See the link below for dual booting Uefi.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Bucky Ball on 2017-03-04
And then verify you have Ubuntu installed in the same mode. If Windows is UEFI, you need Ubuntu installed in UEFI. 

When you boot the machine, hit escape repeatedly before Windows boots. Does that get you to a grub menu list to choose OSs? If not, try the same thing with the shift key. (You need to hit escape or shift, can't remember which, if UEFI and the other if legacy. Can't remember which goes with which sorry so you'll need to experiment. :))

---

### Post by tulliod on 2017-03-06
I tried many things and this one is the only one that worked
[Fix Grub Not Showing For Windows 10 Linux Dual Boot]("https://itsfoss.com/no-grub-windows-linux/").[URL="https://itsfoss.com/no-grub-windows-linux/"]

[/URL]

---

