---
title: "Completely fresh install"
date: 2012-09-06
forum: Installation &amp; Upgrades
---

### Post by Unotforme on 2012-09-06
I would like to do a 'brand new' install of Ubuntu 11.10 (I don't want 12.04/10 for various reasons). I have backed up all my data, so I'm ready to go. I want to completely delete (format) everything on both hard drives (including Grub if possible - I find old items linger in Grub when I do a new installation), and do a completely fresh install. Essentially treat it like new hardware that has nothing on it. Is it possibe, and if so can you help me or direct to a link that shows how to do so. There will be no other operating systems on the computer.

Thanks..

---

### Post by Bashing-om on 2012-09-06
--forme;

 Yes it is possible, the quickest and easiest way is from the live (install) cd.
Boot up -try ubuntu option => load gparted from the menu.
in gparted: select the device (sda or other devices you are working with) =>format
[to the best of my poor memory, not able to verify ATT]
for linux install use the ms-dos option (default).
This in-effect wipes all data off of the disk.

Now would be a good time to set up the partitions on your disk, if you have a good idea as to how you want your system set up. (separate /home and  /data or /somedata partitions )???

[INDENT]regards <==BDQ

[/INDENT]

---

### Post by Unotforme on 2012-09-06
Thanks. I will give it a try. Not to worried about partitions at this point as both drives are > than 600 GB. Will your suggestion remove grub? That seems to be a sticky point, much like windows bootloader. Not the end of the world, I can always edit the grub menu after I suppose; but I'd rather just 'start fresh'..

Just as a side note, I currently have both Xubuntu 12.04 and Ubuntu 11.10 on my hard drives. I was evaluating both, but find myself using Ubuntu almost exclusively now, so thought I would 'go all in'

Cheers and beers..

---

### Post by Bashing-om on 2012-09-06
--forme:
  When gparted advises that all data will be lost ...I believe grub to be a part of that lost data.(trying to correlate within my memory the position of the MBR and the action of Gparted on the partition table.... but I think when the new format is invoked, MBR is gone).

on my aside: the more I use 12.04 the less I use my older installation and the more appreciation I have for 12.04 ....12.04 is intuitive and I am amazed at how much faster my system runs!

[INDENT]Regards <==BDQ

[/INDENT]

---

### Post by grahammechanical on 2012-09-07
I have just done a fresh install of 11.10 into another partition. I am using it to test the distribution upgrade to 12.10 Beta 1. I will also install 12.04 and 10.04 for the same purpose. I can tell you this:

Every fresh install of Ubuntu will put its own grub file into the MBR (Master Boot Record) of the first hard disk (sda) by default and it will overwrite any boot loader information already in the MBR. This happens every time, I can assure you. It will detect other operating systems on the hard disk/s and put them into the grub menu.

If you run Install Ubuntu from the 11.10 live CD at the third screen you will get three opotions:

1) Install Ubuntu alongside them - that is other operating systems. at present you have at least 1.

2) Erase disk and install Ubuntu. It will do what it says. It will erase all the data from the disk. In your case it might not do it to both disks. I do not know.

3) Something Else. This lets you choose the partition to install Ubuntu in or to change the sizes of the partitions. You do this at the next screen where you will see a panel with the label "Device for boot loader installation." On my machine the default is /dev/sda. I guess the same is true for your machine. There will be a drop down menu that will allow you to put the boot loader into other partitions if you have them. In your case you could, if you wanted to, chose the MBR of the second hard disk (sdb) but that choice will not remove the existing boot loader from the MBR of sda.

At every point you will have the option to go back until you click Install now.

[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

[https://help.ubuntu.com/community/GraphicalInstall]("https://help.ubuntu.com/community/GraphicalInstall")

Regards.

---

### Post by Unotforme on 2012-09-11
Thanks for your help. Looks like a 'fresh' install did the trick. Grub only sees 11.10. The reason I'm sticking wiuth 11.10 is solely for my daughter's 3rd gen Ipod, apaarently, best I've been able to anyways, is that Banshee and GTKpod do not work with 12.XX at this point. Damn you Apple!

---

