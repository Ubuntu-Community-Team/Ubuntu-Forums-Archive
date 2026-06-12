---
title: "Inode errors after install of ANY Linux distro"
date: 2007-12-14
forum: Installation &amp; Upgrades
---

### Post by Elexwiz on 2007-12-14
Ok, so I haven't installed ALL the distros, only 3. I've installed Ubuntu 7.10, 6.06, and openSUSE 10.3 and they all encountered the same problem. I'm new to Linux but not computers or Windows.

After each install I would reboot from the hard disk and after about 60 seconds my laptop would just shut down. It wouldn't even restart, it would just turn off. I ran the recovery mode boot-up after each install and the same errors happened every time; INODE errors and incorrect counts each time. It would open a maint shell and tell me to run FSCK which I did and it said that the errors were fixed but the same thing happened on every boot-up. I'm using a spare 80 gig hard drive which I'm pretty sure works fine. Please help.

I'm running a HP Pavilion Laptop zd8215us. P4 2.8Ghz processor, 1.25g ram, Intel 8280 IDE controller.

Thanks,
Shawn

---

### Post by ectospasm on 2007-12-14
Sounds like you've got a bad hard drive.  I would run as many check utilities as you can think of.  I'd start with [The Ultimate Boot CD]("http://www.ultimatebootcd.com/download.html"), which contains quite a few hard drive check utilities on it.  Make sure you pick utilities that examine the S.M.A.R.T. status of the HDD, that may tell you more information if it is indeed failing.

HTH

---

### Post by Elexwiz on 2007-12-15
I downloaded UBCD and ran the Seageate hard drive utilities and it found 10 bad sectors which I repaired, or at least were reported as repaired. I reinstalled Ubuntu but still had the same problems. I'm going to get a hold of another hard drive and try again. Thanks much for your help.

Shawn

---

