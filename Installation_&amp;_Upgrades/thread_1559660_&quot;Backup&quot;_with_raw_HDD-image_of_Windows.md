---
title: "&quot;Backup&quot; with raw HDD-image of Windows?"
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by bokopperud on 2010-08-23
I've bought an Eee with WindowsXP preinstalled.  Naturally my first thought was to exorcise the demon (Windows) with cross, stake and holy-water (and perhaps some garlic), but since I've already have paid for it, I was wondering if I can chuck it elsewhere...

My thought is to use dd to make a raw-image of the harddisk -- either the complete harddisk (e.g. /dev/sda) or the partition with Windows (e.g. /dev/sda1) -- compress it (it should be mostly nothing, right), and store the image on some other drive.  I don't expect any trouble with this...

What I wonder about, is if it will be possible to restore Windows from such an image -- e.g. dd-ing the uncompressed image back to the disk, (probably) using the whole disk (/dev/sda)...  Will it work?  Or is there something that will prevent it from working?  I intend to make a full image of the disk; MBR, partition-table, partitions and all...

It's a rather small harddisk, so I' opting-out dual-boot... (besides, it's not like I intend to use Windows...)

Any thoughts?

---

### Post by Herman on 2010-08-23
:D The method I have used quite often and found to be reliable is to remove any files first and keep those in a separate backup, so that you are only making a backup of the operating system and installed software and settings, (or the lack of same if it's a new, clean install).
Then resize the partition as small as possible with GParted.
Finally, use the dd command to back up the partition.
The dd command does not care what operating system is in the partition or what file system it uses, it will back up anything.

You'll need to have some other operating system such as a USB flash memory Ubuntu installation to to that from and some other media organized to write the resulting file to such as another USB drive with enough room in a partition for the file.
```
dd if=/dev/sda1 of=/media/otherUSB/partition.image bs=4096 conv=notrunc,noerror
```Where 'partition image' is the name you want to give to the output file.
Where 'otherUSB' is the drive, mounted in /media, that has room for the file you want the dd command to make for you.
Where' '/dev/sda1' is your partition containing the operating system that you wish to make a back up of.

I have even copied an unbootable operating system off a damaged hard disk once and onto a new hard disk and got it booting again using this method, it was a Vista install too. 

With Linux operating systems, now that we use the file system UUID numbers for booting, this command is also very useful because we're making the partition into a file, so it doesn't cause any confusion for the boot loader like it might if we only copied it to another disk and kept that in the same computer.

---

### Post by Herman on 2010-08-23
The restore command,
```
dd if=/media/otherUSB/partition.image of=/dev/sda1 bs=4096 conv=notrunc,noerror
```

---

