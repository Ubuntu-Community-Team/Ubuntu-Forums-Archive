---
title: "Disk Utility runs only internittantly"
date: 2010-09-03
forum: Installation &amp; Upgrades
---

### Post by lisa374 on 2010-09-03
When I boot 10.04 I find that "Disk Utility" will only run intermittently; that is with some boots it will not run at all and with some it will run always.
Box has Win XP SP3 and Ubuntu 10.04 installed.
Booting Win first, or not, doesn't seem to make a difference.
I've removed and reinstalled the "Disk Utility" using "System Update" pgm.
Any log files I could look at to help resolve the prob?
I'm a noob to Linux so any help as to where/what to look at would be appreciated.
Need any more info.? Just ask.

---

### Post by oldfred on 2010-09-03
Try running chkdsk on your XP install.

My gparted behaved somewhat like that, then it would not show my sda drive at all and took forever to show sdb & sdc.

Even though I could boot XP without any obvious issues, I ran chkdsk and then gparted had no issues mount sda.

---

### Post by lisa374 on 2010-09-03
Thanks Oldfred,:D
Chkdsk did the trick.:)

---

