---
title: "Blank screen during installation - both 32bit and 64bit version"
date: 2006-08-19
forum: Installation &amp; Upgrades
---

### Post by carboto on 2006-08-19
Just around 15mn before finishing installation, the screen goes blank with two small rectangle - one in the center and another one at the left of the screen. Installation proceeds as normal, but I can't see what is going on. After the disk activity is low, I press enter several times, system reboots and Ubuntu runs with no problem.

The problem is I can't manually choose the partition to install GRUB when the screen is blank. My system specs below:

Intel Celeron D 331
Gigabyte 8i945GZME with Intel 945GZ chipset (GMA 950 onboard graphic card)
512 DDR2 533Mhz RAM
80GB Hard disk

---

### Post by taurus on 2006-08-19
I guess the LiveCD version somehow doesn't like your graphic card!  Maybe you want to try to install Dapper using the alternate CD.  It uses text base installer...

---

### Post by carboto on 2006-08-20
I always use the alternate version since it allows manual installation of grub. The alternate version causes this problem.

---

### Post by K.Mandla on 2006-08-20
I had that same problem with an Intel 9xx chipset. It's something about switching back from the video probe. I handled it the same manner you did: I waited for the CD to pop out and hit return to trigger the reboot.

My best suggestion is to search for help on reconfiguring/repositioning grub. Since you've finished your install, I can't imagine that it's impossible to move that little beggar around. Certainly someone has run into that issue before. Maybe start with the [wiki]("https://help.ubuntu.com/community/GrubHowto")?

Sorry. :( Hope that helps.

---

### Post by carboto on 2006-08-20
Thanks for all your help!!! :D

I think this is a bug in Ubuntu in the way it handles Intel graphic adaptor in text mode. I hope the developer will solve this issue in the next release.

I will use Super Grub Disk to reinstall the GRUB in a different partition. Everything should work, and now I have WinXP, SLED 10, Solaris 10 and Ubuntu on the same disk using NT bootloader. :D

---

