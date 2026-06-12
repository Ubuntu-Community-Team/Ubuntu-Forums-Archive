---
title: "Grub Loading Error 21"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by hardwarecompugeek on 2007-06-09
I finally got ubuntu 7.04 to install today, but when I reboot to load up ubuntu, grub gives me error 21 while it's loading, so I cannot access the Grub command line. I am using two 40 GB hard drives, my primary is set for WinXP Pro and my secondary is set for ubuntu.

I was thinking of several options:

Not use grub at all, and use boot.ini in windows (can't get to windows...., and I don't know what to edit in boot.ini)

Use grub, but figure out how to edit it, so it recognizes XP and ubuntu



Thanks in advance for your help!

---

### Post by logos34 on 2007-06-10
> I was thinking of several options:

Not use grub at all, and use boot.ini in windows (can't get to windows...., and I don't know what to edit in boot.ini)

Too involved...You'd need to extract grldr to C:\, add a 'boot' directory with a menu.lst, then put an entry in boot.ini, etc etc -- Grub is a lot better. 

> ...when I reboot to load up ubuntu, grub gives me error 21 while it's loading, so I cannot access the Grub command line. I am using two 40 GB hard drives, my primary is set for WinXP Pro and my secondary is set for ubuntu.

check this out
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#21](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#21)

---

### Post by confused57 on 2007-06-10
> **hardwarecompugeek said:**
> I finally got ubuntu 7.04 to install today, but when I reboot to load up ubuntu, grub gives me error 21 while it's loading, so I cannot access the Grub command line. I am using two 40 GB hard drives, my primary is set for WinXP Pro and my secondary is set for ubuntu.

I was thinking of several options:

Not use grub at all, and use boot.ini in windows (can't get to windows...., and I don't know what to edit in boot.ini)

Use grub, but figure out how to edit it, so it recognizes XP and ubuntu



Thanks in advance for your help!

My one experience with grub error 21, I entered bios setup, changed the slave hard drive controller from "off" to "auto".  If this doesn't work, the Hermanzone website has some other possible solutions.

---

### Post by hardwarecompugeek on 2007-06-10
Thanks, that was it!

---

