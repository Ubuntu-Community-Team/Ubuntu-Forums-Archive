---
title: "how to partition when your hard disk is in linux format"
date: 2011-05-20
forum: Installation &amp; Upgrades
---

### Post by neo_phyte on 2011-05-20
Hi guys,

This is my situation, I had installed Ubuntu in my whole drive in 640Gig. Now, I want to partition it, without affecting my Ubuntu operating system. I just want 320Gig for my Ubuntu and 320 for my Windows.

I know how partition using Windows but from Linux, that I don't know. Need help on this.

---

### Post by Telengard C64 on 2011-05-21
**_Step #1_**
[Backup](http://blog.wisefaq.com/2010/01/05/backups-with-the-3-2-1-rule/) your data to two separate external media before proceeding. 

[GParted](http://gparted.sourceforge.net/livecd.php) is capable of resizing partitions. You should be able to boot the live CD and resize the partition without any data loss. I have done so in the past without troubles.

HTH

---

### Post by oldfred on 2011-05-21
You need to use LiveCD or download gparted liveCD and swapoff so nothing is mounted. For windows you will need a primary partition, NTFS format with the boot flag. I would suggest another NTFS either primary or logical to use for any data you may want to share. Only set windows system partition as read only if you even want to mount it at all. Windows does not like others writing into its system.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

After you install windows you will have to reinstall grub2's boot loader to the MBR. and run an update to get grub2's os-prober to find windows.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)
```

sudo update-grub
```

---

