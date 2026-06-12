---
title: "Lost Ubuntu Partition after Win 10 update"
date: 2015-11-26
forum: Installation &amp; Upgrades
---

### Post by Martin_OConnor on 2015-11-26
Hi all, 

I am new to Ubuntu and have been looking over the forums for a solution to my problem but keep coming up short.

Ive updated to Win 10 and in doingso lost access to my Ubuntu 12.04 partition. 

Initially it gave me a grub rescue screen, which stopped me from using with OS. 
I solved this issue with a LiveUSB and using boot repair guides from the forums, so thanks for that to begin with.

Now I can access Win 10 perfectly but can only get on ubuntu using the "try ubuntu" off the LiveUSB.
I need access to my Ubuntu for my college work as I am using WRF (Weather Research anf Forecasting model), which took a lot of effort to install so I dont want to just reinstall Ubuntu without running out of other options.

My partition seems to be hidden and will not launch. I have tried using sudo fdisk -l.
And i believe that my Ubuntu partition is on /dev/sda2

[PHP]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc1e1166c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   311836144   155814648+   7  HPFS/NTFS/exFAT
/dev/sda3       311836672   312756223      459776   27  Hidden NTFS WinRE
/dev/sda4       312758270   488396799    87819265    5  Extended
/dev/sda5       482390016   488396799     3003392   82  Linux swap / Solaris

Disk /dev/sdb: 4083 MB, 4083351552 bytes
36 heads, 24 sectors/track, 9230 cylinders, total 7975296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *         920     7975295     3987188    c  W95 FAT32 (LBA)
[/PHP]

I have followed the instructions in this post [http://ubuntuforums.org/showthread.php?t=2008437](http://ubuntuforums.org/showthread.php?t=2008437)
 but I have no idea how to restore or access this partition.

There must be something im doing wrong or my problem is worse than I expected.

Any suggestion and help would be great,

Thanks a lot in advance.

---

### Post by yancek on 2015-11-26
What did you update from, an earlier version of windows or did you have windows 10 and just did a recent update?  Looking at the fdisk output you posted, there is no Linux partition other than swap.  You could post the output of the boot repair script here if you have it or run it again and just select the option to Create BootInfo summary.  sda2 is a windows partition so you would not be able to install a Linux system on it.

---

### Post by oldfred on 2015-11-26
Your Linux partition was sda5 & swap was sda6, both inside the extended partition sda4.
Windows rewrote partition table, left off sda5 & changed swap to sda5.
We can easily recover old Linux partition, whether sda6 or not does not matter as Ubuntu boots with UUID.

       sudo parted /dev/sda unit s print
[http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080](http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080)
Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462)

---

