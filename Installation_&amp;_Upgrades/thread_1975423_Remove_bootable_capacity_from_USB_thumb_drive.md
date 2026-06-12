---
title: "Remove bootable capacity from USB thumb drive"
date: 2012-05-07
forum: Installation &amp; Upgrades
---

### Post by brm on 2012-05-07
I am seeking to do the reverse of most users. I want to *_purge_* the Live USB installation from a USB thumb drive (formatted as FAT32 aka vfat, like almost all USB drives) and to use another USB drive as the emergency-cum-demonstration Ubuntu drive.

Briefly, the story is that my most compact USB drive (which also is the one with the largest capacity) is loaded with an old version of Ubuntu. I have moved it onto the key ring with my house keys and want to use it from now on purely as a data backup device. I do *_not_* want it to bring up a Linux install menu on computers that have a USB device as the first line in their boot path (which is the case of many modern laptops).

It appears that I should replace the existing GRUB bootloader on the USB drive with something more plain vanilla. After doing that, I can presumably simply erase the Linux install directories. These take up over 2GB, so I will also recover a lot of space on my data backup drive.

How do I replace the bootable GRUB setup with something "plain vanilla"?

---

### Post by kurt18947 on 2012-05-07
I would think you could remove the partition.  That should remove **everything** including grub, MBR, everything. Gparted should work for this, not sure if the included disk utility will work or not.  If you don't have Gparted, it's in the repositories.  Then recreate a FAT32 partition.  You would have to unmount the USB drive first to nuke the partition I think.

If you're using this drive in both Windows and Linux, you might want to format the drive using Windows.  I've had some Gparted formatted drives that were not recognized in Windows.  I don't think I've ever had a drive formatted in Windows not be recognized by linux.  This is more of a Windows problem than a Linux problem but still......

---

### Post by brm on 2012-05-07
I did not explain myself well in the original post. There is **no** Linux partition on the USB drive. There is only one  partition, and it is FAT32. Here is the proof:

```
$ sudo blkid
[sudo] password for xxxxx: 
   . . .
/dev/sdi1: LABEL="abcde" UUID="AnAn-AnAn" TYPE="vfat"
```
Therefore, my question remains: What to do with the device master boot record to stop it from booting an operating system and having it instead simply mount a data partition?

---

### Post by darkod on 2012-05-07
It might sound silly, but formatting doesn't remove it? I'm not sure myself if the bootloader section gets formatted too.

Try it. Of course, if you have data on it you want to keep, copy it first. :)

---

### Post by darkod on 2012-05-07
OK, I found it. I wasn't sure how many bytes needed to be zeroed out.

If you zero out the first 446 bytes it will delete the bootloader. If you zero out the first 512 bytes it will delete both bootloader and partition table.
Instructions here:
[http://www.cyberciti.biz/faq/linux-how-to-uninstall-grub/](http://www.cyberciti.biz/faq/linux-how-to-uninstall-grub/)

I don't need to say this, but I will. BE CAREFUL TO USE THE CORRECT DEVICE!!!

If you specify your hdd as a destination... well, you know what happens. :)

PS. Now that I think about that link I'm not so sure it should be null or zero, like if=/dev/zero. Try it with null first, as suggested.

---

