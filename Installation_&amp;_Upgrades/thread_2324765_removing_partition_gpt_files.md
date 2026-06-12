---
title: "removing partition gpt files"
date: 2016-05-16
forum: Installation &amp; Upgrades
---

### Post by angel mike on 2016-05-16
I am trying to reload 14.04 using gmsl rescue but when I run the iso file listed in the Grub2 menu I get an error "installer needs to commit changes to partition table on the following mount points could not be unmounted   /iso device " 
I suspect that the media disk has gpt files on it because I mounted a Seagate external drive which uses the gpt file system.

I ran mount|grep ^'/dev' which listed the following

/dev/dsa2 on /type ext4 (rw, errors=remount-ro)
/dev/sda1 on /boot/efi type vfat (rw)
/dev/sdb1 on /media/michael/SEA_DISK type vfat (rw ........)

I have backed up my files.

I have looked at fixparts( to remove gpt files) and gparted( to remove the partition  sdb1)  but could someone confirm the best way with some commands as well.
Mike

---

### Post by yancek on 2016-05-16
I'm not sure what you are trying to do "reload 14.04".  You have one Linux filesystem partition (sda1) and one vfat efi partition (sda2) and another vfat partition on another drive.  So where is the iso file you are trying to boot from and what are you trying to do with it?

---

### Post by oldfred on 2016-05-16
I get that error when loopmount booting ISO on hard drive.
There is a bug report as it should unmount partitions, and you manually can unmount /ISO. 
But correct solution seems to be to use toram boot parameter.

       # Required as /isodevice usually mounts to a partition and installer does not correctly unmount
sudo umount -lrf /isodevice
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/115521](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/115521)
Says to use toram boot parameter

---

### Post by angel mike on 2016-05-16
Thanks Oldfred for that info and will follow it up. 
My existing 14.04 has become corrupted as I have no toolbars ( side or top ) and mouse clicks do not work. Tried reloading Unity but this fails for some reason.
 Regards Mike

---

### Post by angel mike on 2016-05-17
Oldfred, the command was not recognized - could you add some more info? The link seems to be about loading ram but not sure that I am that familar with the commands. Would gparted remove the media  partition sdb even if it contained gpt files ?

---

### Post by oldfred on 2016-05-17
I am a proponent of gpt and have essentially only used it since about version 10.10 with that install. And started converted every new or totally reformatted drive to gpt.
The only reason to use MBR anymore is for a BIOS boot version of Windows.
Ubuntu can boot with BIOS or UEFI from gpt if you have correct supporting partition.

I normally just use grub to loopmont boot ISO. And once I learned that found it not very difficult. Issue is often path & drive number. In fact yesterday I had the drive number issue as my flash drive became hd0 so my hard drive needed to change from hd0 to hd1 to have grub's entry work.

Do not know details of grml. But thought it was like my grub loopmount of ISO?
Can you edit grml boot entry to add toram boot parameter?

Can you not just boot Ubuntu live installer flash drive?

---

### Post by angel mike on 2016-05-18
Yes, I just used fdisk on sda and it gave Device Boot /ID ee /System GPT  so it is an essential item. What is throwing me is a warning about GPT when I tried to install the ISO from the Downloads due to a mount point not unmounting. Also running unmount gives warning that a GPT(Partition Table) detected on /dev/sda
I have the ISO on a Flash Drive but do not know how to get it to show on the Grub2 menu. I did put the Download ISO there so presumably just need the correct path. The gmsl package does make this easier.
I have just spotted Sudodus post Jan 2015 One Pendrive for all PC etc so will have a look at that in detail. 
I did originally put 14.04 on my Dell XPS 11 using a USB and removing Windows 8 but for some reason the USB is not loading automatically this time.
Thanks Oldfred for your comments. Mike

---

### Post by oldfred on 2016-05-18
Fdisk on any version of Ubuntu prior to 16.04 does not know about gpt. But gpt partitioned drives create a protective MBR with one entry for entire drive that says gpt. And then fdisk and other older tools should at least warn you not to use them as drive is gpt. It is just a warning.
Use parted, gparted, gdisk or if 16.04 then can use fdisk(I think).

       This will boot an ISO from a hard drive or any second drive or flash drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
UEFI grub install and example grub boot stanzas, Also Windows
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)

---

### Post by angel mike on 2016-05-23
This post was initiated because I could not get the Download file Ubuntu 14.04 ISO to install  - it hung on 'Detecting File Systems' after starting the install process. Other posts I notice have had the same problem so there must be a bug somewhere. The ISO file loads from a USB so it might be something to do with the installer? This made me consider booting from the USB which I have only just discovered how on my Dell XPS 11. Cannot mark as solved - pity though.

---

### Post by oldfred on 2016-05-23
Is Detecting File system on installer flash drive or during install from flash drive?

Post this with correct drive:
sudo parted -l
sudo gdisk -l /dev/sda

---

