---
title: "Cannot install Ubuntu (or any distro); no configuration file found error on usb."
date: 2014-08-20
forum: Installation &amp; Upgrades
---

### Post by mujin2 on 2014-08-20
Hey all. I've spent the past few hours messing around and attempting to install Ubuntu with no success.

I have an 8GB Lexar USB drive which I used previously to install Linux Mint on another machine. Fast forward to several months later, I wanna put Ubuntu on another machine here. I've tried everything from formatting this drive to NTFS by changing drive policies and formatting to exFAT (both not even recognizing the USB at all). Using FAT32 gives me the "no configuration file found" error involving syslinux. I've tried renaming isolinux folder to syslinux, as well as the .bin and .cfg files. I've checked md5 hashes and verified they were correct as well as try other distros like Lubuntu and Mint again, but I keep getting the same error.

I'm at a total loss here. Is it my USB drive? Is there something I am doing wrong? Hoping for a timely response on this.

---

### Post by yancek on 2014-08-20
Did you put Ubuntu on the Lexar you previously used with Mint to try to install to a hard drive?  What software or method did you use to do this?  I'm not sure I'm understanding the problem, but it seems you are unable to boot from the flash to install, correct?

---

### Post by oldfred on 2014-08-20
Did you use the dd procedure to create the Mint installer?
That creates a image on the flash drive not a partitioned drive. It then will not work as the partition table has some data in it from the image. You may just need to zero out the entire MBR or first sector on the flash drive.

May double sure that flash drive is mounted as sdb. It run on any other drive it in effect erases drive boot loader and partition table.

       dd if=/dev/zero of=/dev/sdb bs=512 count=1

Then see if you can partition and format flash drive with gparted.

---

### Post by mujin2 on 2014-08-21
> **oldfred said:**
> Did you use the dd procedure to create the Mint installer?
That creates a image on the flash drive not a partitioned drive. It then will not work as the partition table has some data in it from the image. You may just need to zero out the entire MBR or first sector on the flash drive.

May double sure that flash drive is mounted as sdb. It run on any other drive it in effect erases drive boot loader and partition table.

       dd if=/dev/zero of=/dev/sdb bs=512 count=1

Then see if you can partition and format flash drive with gparted.

I'm fairly new to all this. How would I go about to zeroing out the MBR of the flash drive?

---

### Post by oldfred on 2014-08-21
If you did not use dd to create the Mint installer then that is not the issue.

The dd command is dangerous to use as any typo can destroy something you did not intend. You must have correct from & to drives. If not familiar with that then do not use dd. I actually posted command to delete MBR using dd if flash drive is sdb. If you have another drive that really is sdb, that command will destroy it and you have to change to sdc, sdf, etc.

       Powerful command, but often misused and then nicknamed "dd" Data Destroyer
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

---

