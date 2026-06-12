---
title: "Help!  Grub installed on wrong partition"
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by PakRX8 on 2008-11-04
Ok, I was installing Ubuntu 8.10 on my wife's computer and accidentally selected her data partition for the installation of Grub.  I'm trying to restore the partition table so that all the data is readable again by Windows.  This partition contains all of her pictures, music, documents.  She's extremely worried that I totally toasted all of this, which I know isn't true, but I can't figure out a way to get rid of grub from that partition.

I tried the following with the Ubuntu Live CD:

dd if=/dev/zero of=/dev/sda5 bs=1 count=446

I got an admin error if I remember correctly.  Could anyone help me get rid of grub from her D: partition and restore the partition the way it used to be.  

Also, I can't get into my Ubuntu installation because I'm never given the option to dual-boot between XP and Ubuntu.

---

### Post by taurus on 2008-11-04
If you have a windows CD, you can boot from it and restore the MBR.  Otherwise, maybe this link helps.

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by caljohnsmith on 2008-11-05
Have you tried to mount the partition from the Live CD yet? Is it a NTFS partition as opposed to FAT32? If it is NTFS, try:
```
sudo mount -t ntfs-3g /dev/sda5 /mnt -o force
```
If that doesn't work, there a good possibility that "testdisk" can repair the partition boot sector, assuming it is NTFS:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the NTFS data partition, choose "boot", then choose "Backup BS", and have testdisk write the backup boot sector to the partition boot sector. After that try mounting the partition again:
```
sudo mount /dev/sda5 /mnt
```
Or if the above doesn't work, try again:
```
sudo mount -t ntfs-3g /dev/sda5 /mnt -o force
```
And if either works, you should see the data partition's files in /mnt. Let me know how it goes.

EDIT: I also wanted to mention that you can accomplish the same thing with a Windows Install CD as the testdisk procedure above; after booting the Windows CD, go to the "recovery console", and do:
```
map
```
That will show a list of the Windows partitions. Once you know the drive letter of your NTFS data partition, e.g. D, then you can do:
```
fixboot D:
```

---

### Post by PakRX8 on 2008-11-05
Thanks for the info caljohnsmith!  I'll try this first thing when I get home.  I was going to buy a data recovery software, but maybe I'll try what you suggested first.

---

### Post by PakRX8 on 2008-11-05
You are awesome!  I used your method for the XP cd and it worked perfectly!  Thank you so much!

---

### Post by caljohnsmith on 2008-11-05
That's great news, glad to hear you have your data partition back. Now your wife can breath a big sigh of relief I hope. Cheers and have fun with Ubuntu. :)

---

### Post by amarti on 2010-11-15
Dear caljohnsmith!

I had the same problem and your contribution solved it!

Thousand thanks!
Cheers Andreu.-

---

