---
title: "Filesystem messed up because of Apple's Mac OS X Disk Utility"
date: 2014-02-28
forum: Installation &amp; Upgrades
---

### Post by djpredator17 on 2014-02-28
I'm a happy Ubuntu user (Elementary OS 0.2 Luna).
I installed Luna on my Macbook 5,1 (late 2008). Everything works perfectly, even better than Mac OS X, but here is my problem:
- I used Utility Disk on the Mac partition, and it converted the Ubuntu's partition from ext4 to FAT32. 
- The data are still there, but when I try to boot from Ubuntu it returns an 'unknown filesystem' error.
- I managed to boot from the grub rescue command line, and everything is working correctly.
- I booted from an USB stick
- How can I convert the filesystem back to EXT4 without losing data?
I can backup the whole thing and recreate the partition, but I'd prefer not to do it if possible.

Thank you!
Carlo

Here is my fdisk -l
    Device Boot      Start         End      Blocks   Id  System/dev/sda1               1      409639      204819+  ee  GPT
/dev/sda2   *      409640   283217471   141403916   af  HFS / HFS+
/dev/sda3       311954080   313223615      634768   af  HFS / HFS+
/dev/sda4       313227264   492304383    89538560    c  W95 FAT32 (LBA)

---

### Post by lukeiamyourfather on 2014-02-28
There's no such thing as converting from ext4 to FAT32 and vice versa. They are vastly different in design and implementation. The Disk Utility in OS X probably just changed some metadata and not the actual filesystem. If you can see your data in OS X at this point I'd take the opportunity to backup anything you haven't already.

---

### Post by tgalati4 on 2014-02-28
You need to perform data rescue at this point--grab the important data and save it to a safe location.  Changing file systems will normally resulting in wiping the partition and losing your data.

Install *testdisk* and run it and *photorec* (which comes with it).

---

### Post by oldfred on 2014-02-28
Not sure if it applies to a Mac or not, but you can change the partition table entry to a different code and partition table will show one type of format when partition is actually another type.
Also Macs sometimes use hybrid partitioning. That is required for Windows as Windows only booted with MBR, but drive is really gpt partitioned. But then you have to keep them sync'd.
 [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)


If you do not have gdisk on your live installer
sudo apt-get install gdisk
 sudo gdisk -l /dev/sda
sudo fdisk -lu

---

### Post by djpredator17 on 2014-02-28
Thanks to everybody for the quick replies, I'm gonna try some of your suggestions before wiping the disk if necessary.

---

### Post by tgalati4 on 2014-02-28
*Testdisk* will fix the partition if it is fixable.  Don't know how deep the Mac Disk Utility goes as far as formating.  With luck, *testdisk* will get you back.

---

