---
title: "ubuntu 7.04 post-installation boot error"
date: 2007-05-14
forum: Installation &amp; Upgrades
---

### Post by gracexunbound on 2007-05-14
hello everyone! i'm sorry i do not have the time to search through the forums to see if anyone has had my exact problem. anyhow here goes. I've got a completely wiped Pentium III machine with 2 30Gb harddrives, on which i automatically installed ubuntu 7.04 on. i restart the PC and i get this:

"RPL-ROM-ADR: 00D0 09C8 5FAF
RPL-ROM-IRQ: 11
RPL-ROM-PIO: E400
RPL-ROM-SLT: 1

RPL-ROM-FFC: 5 DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER"


i have gone into the bios and tried both harddrives as the first boot drive. same error for both.
i'm really hoping i can get some help! :confused:

---

### Post by gracexunbound on 2007-05-14
anyone? :(

---

### Post by az on 2007-05-14
Was the computer working beforehand?

---

### Post by gracexunbound on 2007-05-15
well it was running windows XP professional before i used Darik's Boot & Nuke to wipe everything.

i used the live disk and installed from the desktop without a hitch, took the cd out and rebooted just to get that error up top...

---

### Post by gracexunbound on 2007-05-17
PLEEEEEEEEEEEEEEEEEEEASE??

noone has a clue as to what it could be? i've heard great things about the ubuntu community, so i'm not shaken, i know theres gotta be SOMEone who can help me here...

---

### Post by gracexunbound on 2007-05-23
BUMP. 

can i get some help at all? i'm seriously considering just trying another version of linux.

---

### Post by gracexunbound on 2007-05-25
... then another flavor it is. :X

---

### Post by LifeIsShort on 2007-05-25
if you haven't installed the new version yet....
you might want to try manually reformatting the drive...I had a similar boot disk error. had drive reformatted, then repeated install from the start, everything worked ok after that.

take a look at my thread...I hope it helps a bit

[http://ubuntuforums.org/showthread.php?t=448844](http://ubuntuforums.org/showthread.php?t=448844)

you'll likely need a boot partition allocated as well...

here is what I have set up...

# df -t ext3
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda3            306114132   2466776 288097644   1% /
/dev/hda1               101086     22673     73194  24% /boot

I also set up a swap partition a little over 2 times my memory


but that said....every installation has its own little nuances...

good luck

---

