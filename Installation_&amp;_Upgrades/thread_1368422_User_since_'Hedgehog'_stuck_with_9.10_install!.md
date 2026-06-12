---
title: "User since 'Hedgehog' stuck with 9.10 install?!"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by Affejunge on 2009-12-30
So, I have used Ubuntu since its Hoary Hedgehog (5.04) release.  I am not a Linux god, but I have done many, many installs and of the few problems I have had over the years, I have been able to figure them out (either on my own or with a little google), but this one has me stumped.

I had no problem installing 9.10 on both my home machine and my laptop.  Now came to upgrade my file server/HTPC from 8.04.  I first tried Mythbuntu, booted up and found I could only install on my slave device of IDE 1 (sdb).  sda was not even an option to install onto. So I quit the install and was dropped into the desktop.  I popped open a shell and did an fdisk.  sda was there...hmmm...so I ran parted, sda showed up!  Weird, I tried to mount sda1 and got "Device does not exist"....hmmm.

So, since it was my first time messing with Mythbuntu, I went back to good old Ubuntu.  Boot up, started the installer...and..same issue, sda did not show up as a drive to install on...dang.

Dropped back into the desktop, ran gparted, sda1/2/3 all there and with Ubuntu, I could mount sda1 with no problem...

So, I figure since I was doing a clean install anyway, I would wipe sda1 (it was my old ubuntu root (yes, everything has been backed up, twice!)) Formatted with no problem, so ran the ubiquity to install again...and...no sda, just sdb! what the heck?! 

Maybe I am missing something really obvious, but seriously, what's going on?  I am installing a 32 bit OS onto a 64bit Sempron, but that should not really make a difference...
:confused:
Any ideas?

---

### Post by dstew on 2009-12-31
This is a bug in the 9.10 partitioner that runs under the Ubiquity installation system. It is caused by the dmraid program, and appears on systems with RAID BIOS extensions. The workaround is to remove the dmraid program from the Live CD system:```
sudo apt-get remove dmraid
```Do that, then try the installation again.

---

