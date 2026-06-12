---
title: "Live CD install hangs on file copy"
date: 2007-01-12
forum: Installation &amp; Upgrades
---

### Post by SquidgeForceOne on 2007-01-12
Hi,

I'm installing Edgy Eft on an older Dell Latitude C800 PIII 1Ghz 256MB RAM 5GB HDD.  I know the hard drive is SMALL but it was free.  I've read install requires 2GB.  Right now I'm just trying to get things to work so I've got a laptop to take to school.

First off, I've found that the Live CD's video drivers hate my computer, which is fine.  I've read about how to fix this.  The other people experiencing this issue (on a C800) were able to do a full install and go back and fix it.

I'm doing a graphical install from the live CD.  The touchpad jumps everywhere so I either do my best to deal or use a USB mouse.  The result is the same.  Booting takes eons (15 minutes maybe).

I get to copying files and it seems to completely lock up around 39%.  It could just be that the HDD is too small.  I don't think it's malfunctioning hardware since winXP will install fine.  I couldn't find anywhere that tells me if the HDD needs to be completely blank or reformatted or unpartitioned when starting a new installation each time.  I know I can't format it with a windows format like NTFS.

An easy possibility is trying another distro like Damn Small in case it's HDD space.  A lot of people seem to be saying if one doesn't work a lot of the others don't.  I'd really like Ubuntu to work for me.  I guess the other possibility is that the CD is bad.  It took for freakin' ever to download that ISO too, even with cable.  Any ideas?

---

### Post by icefaerie on 2007-01-12
You will need to partition your HDD.   You will need at least a linux partition and a Windows parition at the very least.  Realistically, 5 GB is probably too small to dual boot Windows and anything except maybe DSL.

If you want to go for Ubuntu, I would recommend using Xubuntu with your hardware, especially since you only have 256 MB ram.  You will either have to completely format the HDD or make separate paritions for WinXP and *ubuntu.  If you want to dual boot, make sure you've defragmented your NTFS partition under the Windows Disk Defragmentation utility.  It might take 2 or 3 runs to get it defragmented enough.

But 5gb is really small, so you might want to consider using the whole HDD for just one OS.  If that OS is *ubuntu, then you should completely format the HDD, and the install should go fine.

---

