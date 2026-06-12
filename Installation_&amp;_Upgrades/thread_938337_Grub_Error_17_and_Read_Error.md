---
title: "Grub Error 17 and Read Error"
date: 2008-10-04
forum: Installation &amp; Upgrades
---

### Post by PostersandGuitar on 2008-10-04
After installing Ubuntu Studio on a second hard drive, I got Grub Error 17. After researching it,and changing the orders of the hard drives in the BIOS, I now get a read error from grub.

One hard drive is SATA, the one Linux is on is IDE. The SATA is Primary Master, the IDE is Secondary Master(the primary is my CD/DVD drive).
What should I do?

---

### Post by Pumalite on 2008-10-04
Check this thread:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by PostersandGuitar on 2008-10-04
I want to use GRUB, and because of the way i have my hard drives set up, cant set one as slave.

---

### Post by caljohnsmith on 2008-10-04
How about first posting:
```
sudo fdisk -l
```
When you boot the Ubuntu IDE drive, what happens? Is it the Grub read error or Grub 17? And if you get Grub 17, does that happen before you get the Grub menu, or after you get the Grub menu and select Ubuntu to boot?

---

### Post by PostersandGuitar on 2008-10-04
I can't post sudo fdisk -l 

I can't get to a terminal of any kind. Right after the bios, it goes to grub error 17. It got read error when I tried to fix the problem by setting the IDE to 1, and the SATA to 2 in the BIOS.

---

### Post by caljohnsmith on 2008-10-04
Do you have your Ubuntu Live CD? If you do, boot that up and you can open a terminal from there. I think the best way to troubleshoot your problem at this point is from a Live CD, so if you don't have one, I would recommend downloading one.

---

### Post by Pumalite on 2008-10-04
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by PostersandGuitar on 2008-10-04
caljohn: I'm running Ubuntu _Studio_. It has no live cd. Would the terminal from my Gparted Live CD work?


I tried switching the hard disk boot priority, which lead to a read error. What would this mean?

---

