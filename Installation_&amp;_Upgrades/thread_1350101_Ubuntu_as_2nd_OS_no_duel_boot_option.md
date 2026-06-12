---
title: "Ubuntu as 2nd OS no duel boot option"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by RoninGT on 2009-12-09
Hello i am new to ubuntu and i am trying to get it to duel boot with windows 7.

I followed this 

[https://help.ubuntu.com/community/WindowsDualBoot#head-6852d2e9b3e03d350a4271b58e3bdea4bbe81ad8](https://help.ubuntu.com/community/WindowsDualBoot#head-6852d2e9b3e03d350a4271b58e3bdea4bbe81ad8)

On how to install with windows and duel boot, I choose to install ubuntu side by side with windows (Options in install) gave unbuntu 100gigs of space and finished the install without any problems. However when i reboot the pc it goes to windows and does not give me an option to boot to ubuntu. Anything i could be doing wrong?

I am now finishing reinstalling windows 7 again (Fresh installs) to try again.

Thanks in advance.

Ronin

---

### Post by darkod on 2009-12-09
After the first (unsuccessful) Ubuntu install, is your hdd now divided in two partitions between win7 and ubuntu? If it is, are you installing win7 again now on it's own partition or the whole hdd?
You should have waited to try find the problem, not reinstall immediately.

---

### Post by tommcd on 2009-12-09
> **RoninGT said:**
>  However when i reboot the pc it goes to windows and does not give me an option to boot to ubuntu. Anything i could be doing wrong?
I am now finishing reinstalling windows 7 again (Fresh installs) to try again.

How many hard drives are on the system? If there is only one hard drive then the install should be pretty straightforward. If you have more than one drive, then grub may be getting installed to the wrong place. 
Are you installing Ubuntu and or Windows to an external hard drive or something like that? 
Also, if you only have 1 hard drive, when you install Ubuntu don't have anything like an external hard drive, a flash drive, or a memory card connected to the system. It is unlikely, but grub could be inadvertently getting installed to those devices if they are connected to the system.
Since you reinstalled Windows, boot up the Ubuntu live CD again. Open a terminal (applications > accessories > terminal) and post the output of this command:
```
sudo fdisk -l
```
(Note, that is a lower case "L" at the end of that command, not a number 1).
Since you reinstalled Windows, go ahead and reinstall Ubuntu. If you do not get the grub menu with a choice of booting Ubuntu or Windows, write back with what happened.
Also, are you installing Ubuntu 9.10? That is the current version of Ubuntu.

---

### Post by RoninGT on 2009-12-09
```

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd2b204e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38914   312567808    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x730c93dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2              13       60802   488282112    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd2b204e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38914   312568832    7  HPFS/NTFS

Disk /dev/sdd: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30401   244196001    7  HPFS/NTFS
ubuntu@ubuntu:~$ 


```Yes i do have 3 harddrives in the pc and one ex i am trying to put it all on the main HDD thou. Here is the output of that command

Ronin

EDIT: and yes the latest ver of ubuntu

---

### Post by audiomick on 2009-12-09
Hallo.
I am not the big expert, but to me it looks like your re-install of windows has taken over all of the discs. They are all showing as ntfs, which is a windows file system.
Looks like you will have to install Ubuntu again.

---

### Post by presence1960 on 2009-12-09
You do not have Ubuntu on any of those disks from fdisk output, was your external HDD unplugged when you ran that command? Is ubuntu on the external?

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB with your external HDD plugged in.. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by raymondh on 2009-12-09
> **presence1960 said:**
> You do not have Ubuntu on any of those disks from fdisk output, was your external HDD unplugged when you ran that command? Is ubuntu on the external?

sorry .... wrong post

---

### Post by darkod on 2009-12-10
If /dev/sda (the 320GB drive) is the one you call main hdd, you let win7 take all of it. Since this is a new install of win7 and you plan to have ubuntu on the same drive, that's very bad practice.
Depending how are you installing win7 (it doesn't look like from recovery partition), give win7 only how much space you want for it, not the whole drive. That way you don't have to shrink win7 to make space for ubuntu.
If you want 100GB for ubuntu as you said, that means give win7 around 220GB (have in mind a 320GB doesn't actually have 320 "real" GB due to 1000 vs 1024 difference).
Because your win7 is fresh, and if the above is correct, I would suggest reinstalling win7 again and NOT on the whole drive. Then install ubuntu in the unallocated unpartitioned space.
Another suggestion, during installation of the OS unplug the external hdd, just in case.

---

### Post by tommcd on 2009-12-10
If the first 320GB drive (identified as /dev/sda1 in the output of "fdisk -l") is the one you plan to use to dual boot Windows7 + Ubuntu, make sure that is set as the first hard drive in the computer's BIOS. Install Ubuntu there, and grub should go to the master boot record (MBR) on that drive.
You could even disconnect all the other hard drives before you install Ubuntu. That way there is only one MBR for grub to be installed to, so you can't go wrong. You can then reconnect the other drives and add mount points for them in your Ubuntu system if you wish to do that.

---

