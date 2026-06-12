---
title: "dual boot install on umpc with no CD"
date: 2008-08-24
forum: Installation &amp; Upgrades
---

### Post by photonfix on 2008-08-24
I found a relatively easy way to install Ubuntu onto a USB HDD for an UMPC (fujitsu u810).  I'm a nube and wanted to stay away from too many command entries. The u810 doesn't have a CD drive and the internal HDD has Vista.
I did several approaches, so I hope I have this sequence about right.
Partition USB HDD with Vista disk manager. Drive is shown as F:   Create G: partition for fat32, about 2 G , just need to hold the files from the Ubuntu Live CD
Download the Ubuntu Live CD, I used a different machine and burned files to a CD.  I see there is info out there on converting iso file and putting it directly onto HDD. 
I plugged the usb HDD into a machine with live CD and copied files to the G: partition
I put usb HDD back onto UMPC and downloaded syslinux.exe and put it on G:
on G: I changed the isolinux folder name to syslinux and inside that folder, changed the isolinux.cfg name to syslinux.cfg
from G:  run syslinux in windows command screen using this:   syslinux -f -s -m G:
from G:  run wubi,  I told it to put Ubuntu on F:
choose to reboot later
if you've messed with the bios, make sure it's set to boot from internal HDD before the usb HDD.
use easyBCD program to configure the vista boot manager

This gives me full dual boot Vista / Ubuntu while preserving the original internal HDD.  The Ubuntu os is contained on the external USB HDD and doesn't touch the internal drive.

I hope this helps some others.  Now I just have to figure out the touch screen thing....

---

### Post by photonfix on 2008-08-25
Just had a thought. Using this method ie wubi, could I set up a partition or folder for different laptops and use same USB HDD to dual boot multiple machines?  Each one would have it's own configuration.  That would be coool.
Has anyone done this?

---

