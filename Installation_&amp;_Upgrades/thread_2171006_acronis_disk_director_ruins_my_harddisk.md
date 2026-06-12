---
title: "acronis disk director ruins my harddisk"
date: 2013-08-28
forum: Installation &amp; Upgrades
---

### Post by eekie on 2013-08-28
On my packard-bell netbook i have windows 8 installed but all of a sudden at my holiday address it started up with only a pointer on a black screen. I could not access the troubleshoot mode as F8 and shift F8 did not work. So I bought a 4 GB usb stick and loaded it with Ubuntu live at the local library that let me use their computer and installed it on my harddisk in order to access my data and mail. Next I formatted the usb stick with  ntfs, downloaded the test version of windows 8.1 and loaded the image using the 494 version of unetbootin (newer versions don't work). Using the stick I have repaired the file system and restored windows with a restore point. Now everything worked fine but I liked to have a system back-up and for this purpose I had to expand my back-up partition. I have used acronis disk director whereas I had better switched to Ubuntu to let Gparted do the job. This operation required a restart and now both operation systems had gone. Starting from the usb stick produced a blue screen telling that I should use the repair or installation disks. There was no way to get away from this screen and to use the repair mode of the stick.  The library came to the rescue again by providing me with ubuntu-live again. Now I am working  with Ubuntu live, hoping to repair my harddisk. Gparted  gives warnings:
Invalid argument during seek for read on /dev/sda
Invalid partition table on /dev/sda-wrong signature 0
If the warnings are ignored Gparted shows all ntfs partitions, ext. 4 partitions have disappeared and show as unallocated.
I can access all ntfs partitions with nautilus all mounted  as /media/ubuntu/(label) .
What can I do to save my ntfs partitions when I reinstall Ubuntu. The installer can only see a completely unallocated disk

---

### Post by VMC on 2013-08-28
Depending on what your doing, but I have never had issues with Acronis. Just the opposite. Gparted can take hours moving or enlarging a partition. Especially if your moving data along with it. On partitions where there isn't much to move, it does ok, but Disk Director takes far less time no matter what I'm moving. Also, I've never had trouble with any partitions using Disk Director.

---

