---
title: "error 29: Disk Write Error?"
date: 2007-02-04
forum: Installation &amp; Upgrades
---

### Post by John_austin on 2007-02-04
I am having an odd problem with a new install on a Dell Dimension 4100 (867 512M RAM)  I've got an 80 gig Western Digital Caviar Drive that I just bought.  I've formatted the drive and tested it using the western digital utility cd, and fully installed 6.10 without problems however when I get to grub after the reboot it immediately gives me an "error 29: Disk write error" and puts me back to the grub menu.  When I choose the Recovery option it boots like normal (without the CD in) and I can use the command line.

I've now successfully installed Windows xp twice on this drive, but it always seems to have problems with Ubuntu.

anyone have any ideas?

---

### Post by Michelpt on 2007-02-27
I had the same problem, I fixed this problem this way: 
first you may need is to check your BIOS settings and to find there something like "HardDisk write protect" and put this option to "Disabled", then you can boot Ubuntu. 
Then if you cannot boot Windows XP, insert windows install CD, choose "R" (recovery mode) and type **fixmbr**, press "Y" to rewrite the Master Boot Record. After, type **fixboot** and press "Y" too.
Now I am trying to reinstall grub from the LiveCD, I 'll tell you later my result. At least you can run windowsXP and still have installed Ubuntu on your another partitions.
Hope it helps

---

### Post by Michelpt on 2007-02-27
To be continued: 
then run your Live CD and follow the first post of [this]("http://ubuntuforums.org/showthread.php?t=224351") thread , exactly as I did and fixed this problem

---

