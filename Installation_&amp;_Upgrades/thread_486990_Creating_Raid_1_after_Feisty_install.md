---
title: "Creating Raid 1 after Feisty install"
date: 2007-06-28
forum: Installation &amp; Upgrades
---

### Post by jarmen on 2007-06-28
I already have an up and running Feisty install, with Samba and NTFS support that I plan on using as a file server.  I'm adding two IDE 300 gig drives that I want to setup as Raid 1.  All the installs I see explain how to setup the Raid from fresh install.  Can I use Gparted to just reformat those drives and create the Raid from within the GUI?  Also, I had initially formatted them as NTFS in case I had to pull them and stick them in a Windows machine as a precaution, will this work with the Raid or do they need to be ext3 or at least Fat32?

I've already install mdadm but not quite sure how to use.  Any feedback would be appreciated.

---

### Post by Yoooder on 2007-06-28
Keep looking for software RAID tutorials, lots will cover your exact needs.

As far as formatting, you can go into the drives with gparted and delete all partitions (NTFS, Ext3, Fat are not compatible with RAID).  

There is a partition type called "Linux RAID", and if you can find it in gparted you can go ahead and set a single partiton of that type to use the whole disk.  If you can't find it in gparted, then your tutorials will most likely tell you how you need to format the drive.

---

### Post by Yoooder on 2007-06-28
... if you use cfdisk for your partitoning the Linux RAID partition type is "FD" without the quotes.  Just do the following:

1) run cfdisk as root
> sudo cfdisk /dev/[device]

2) delete all partitons present on the drive by pressing "d"

3) Create a single new partition, setting it to fill the whole drive:
   - Press "n"
   - Select Primary (default)
   - Press "enter" to use the default (full) size

4) Set the partition to Linux Raid Autodetect
   - Press "t"
   - Press "space" to get to the end of the list, where you can input the type
   - enter "FD" without quotes and prett "enter"

5) Press "W" and then type "Yes" to write / save the partition changes

---

### Post by jarmen on 2007-06-28
Thanks.  I think I got it work based on this tutorial - [http://bfish.xaedalus.net/?p=188](http://bfish.xaedalus.net/?p=188)
I'll post my final result after I've tried it for a few days in case anyone else wants to go this route.

---

