---
title: "Flash drive can't be formatted"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by cozski on 2010-01-10
Hey... I'm trying to install Netbook Remix using flash drive. When I use the USB Startup Creator it tells me I need to format my flash drive but doesn't respond when I try. Any ideas?

Thanks :)

---

### Post by underquark on 2010-01-10
I managed to do this fine a couple of months back then hit the format problem just a few weeks ago.  Ended up using UNetbootin to put 9.04 onto a 1Gb stick and install it onto another PC.

---

### Post by darkod on 2010-01-10
Open Gparted and format the stick as FAT32 first separately. Then use USB Startup disc creator without formatting.
You can also format it as FAT32 on any windows machine, doesn't matter.

---

### Post by cozski on 2010-01-10
Gparted is not seeing the drive even though it pops up as a separate window when I mount it... when I refresh the list in Gparted it doesn't see it.

---

### Post by darkod on 2010-01-10
> **cozski said:**
> Gparted is not seeing the drive even though it pops up as a separate window when I mount it... when I refresh the list in Gparted it doesn't see it.

There is a drop down list in Gparted in top right area, where you select the disk you are looking at. By default it would usually be the internal hdd. The stick should be in that drop down list, probably as /dev/sdb. If it doesn't show it there, I'm really puzzled.

---

### Post by efflandt on 2010-01-10
Make sure that you format the "partition" and not the "drive".  Maybe the format error is because it is mounted (umounting it first may help).

I have often noticed that format error often with the USB Startup Disk Creator, but somethings that is because I attempt to format sdb instead of sdb1, and after that, in some cases I need to recreate an msdos partition table on it first before I can format it with gparted.  So now I usually just format it first and then make sure that I have the partition selected instead of the drive.

---

### Post by cozski on 2010-01-12
The formatting still wasn't happening. The sequence I followed was this:


[LIST=1]
[*]Open USB Creator Utility
[*]Point to source image (ISO file)
[*]Insert Flash drive
[*]Unmount Flash Drive
[*]Hit Format button
[/LIST]
Still no response... HOWEVER, after I unmount the flash drive (step 4), another window pops up (B5D5-5FBE) which is the location of the flash drive and then in the usb utility window below the original flash drive another flas drive became available (/dev/sdb1) and it is this drive that I had to select. I still couldn't format it but it did'nt matter as the option to Make start-up disk became available... and  hey presto I was able to do just that!

[IMG]http://i47.tinypic.com/2djp11c.png[/IMG]

Not as straight forward as i anticipated but got there in the end. Thanks for help everyone.

---

### Post by sgosnell on 2010-01-12
Connect the USB drive first.  Then start the USB Drive Creator.  That's the way it's supposed to work.  It takes a few seconds for the inserted drive to be recognized and dealt with.

---

