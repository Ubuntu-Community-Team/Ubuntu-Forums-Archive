---
title: "[Ubuntu] Boot-Repair"
date: 2016-07-29
forum: Installation &amp; Upgrades
---

### Post by luismorais2 on 2016-07-29
Hello!

I have my laptop with dual boot (Windows 8.1 and Ubuntu 16.04) and today I managed to upgrade the version of Windows.

The update messed up my GRUB and the menu grub rescue appeared after rebooting.
I used the tool Super Grub2 Disk to boot to Windows, although it did not find any grub files to boot to Ubuntu OS.

After that, I made a Live USB with Ubuntu 16.04 image and tried to run Boot-Repair to restore the GRUB, which was not successful.

Here is the report from Boot-Repair after I tried to repair: [http://paste2.org/YwNxMx6D](http://paste2.org/YwNxMx6D)


I would like to ask if somebody is able to help me with this issue.

Thank you very much!

---

### Post by yancek on 2016-07-29
The windows upgrade appears to have re-written the partition table and not included the Ubuntu partition as your fdisk output shows.  There is a lot of space between the start of the Extended partition "/dev/sda3         437,202,942" (/dev/sda3) and the start of the swap partition "/dev/sda5         491,802,624"(/dev/sda4) which in all likelihood was your Ubuntu partition.  I'm not sure this can be repaired with boot repair but it can be with testdisk.  I've seen a number of posts here with this exact problem.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

