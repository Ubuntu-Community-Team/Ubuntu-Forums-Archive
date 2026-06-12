---
title: "no room in /boot for updates"
date: 2015-11-05
forum: Installation &amp; Upgrades
---

### Post by chris405 on 2015-11-05
Hello, my Ubuntu 14.04 LTS had some updates to install but it said I didn't have enough space in /boot to update. My Terabyte drive has only 40 GB used :) What the heck is Ubuntu talking about. How do I increase the space in the /boot folder that it is requesting? it recommended doing an apt-clean and emptying my trash which didn't help. Thx

---

### Post by oldfred on 2015-11-05
Did you use the Advanced LVM partitioning?
I do not know LVM, but it does not make a generous /boot partition and you have to regularly houseclean out old kernels.

Unless you have to have full drive encryption better not to use LVM until experienced with Ubuntu or any Linux.
       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[URL="https://help.ubuntu.com/community/UbuntuDesktopLVM"]https://help.ubuntu.com/community/UbuntuDesktopLVM

      [/URL]
 Check current kernel I also keep one older just in case:
#Current kernel:
uname -a
# kernels, shows older also?
dpkg --list | grep linux-image

I prefer to use synaptic:
 sudo apt-get install synaptic
In synaptic search for linux-image to choose to delete old ones
Using synaptic
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

Command line:
      cd /boot
ls -l /boot/vmlinuz*
sudo apt-get purge  linux-image-[version]-generic linux-image-[version]-generic
Multiples, just be sure not to delete your current kernel:
sudo apt-get purge linux-image-3.13.0-{XX,XX,XX,XX,XX,XX}-generic
sudo apt-get purge linux-image-3.13.0-{54,55,57}-generic
Also headers:
dpkg -S /usr/src/*
Example, some did not have -generic at end:
sudo apt-get purge linux-headers-3.13.0-39-generic[URL="https://help.ubuntu.com/community/UbuntuDesktopLVM"]
[/URL]

---

### Post by chris405 on 2015-11-05
Hi, thx for responding,  not sure what "[COLOR=#000000]Advanced LVM partitioning" is and if I don't need it then I can remove it.[/COLOR] I'm new to Ubuntu. 
I thought I just selected the defaults when I installed it on my machine. What do you advise me to do? I do have [COLOR=#000000]synaptic already installed.
[/COLOR]This is what I have; 

**uname -a**
Linux ZinoHD 3.19.0-31-generic #36~14.04.1-Ubuntu SMP Thu Oct 8 10:21:08 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

**dpkg --list | grep linux-image**
rc  linux-image-3.19.0-25-generic                         3.19.0-25.26~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-26-generic                         3.19.0-26.28~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-28-generic                         3.19.0-28.30~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-30-generic                         3.19.0-30.34~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-31-generic                         3.19.0-31.36~14.04.1                                amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-25-generic                   3.19.0-25.26~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-26-generic                   3.19.0-26.28~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-28-generic                   3.19.0-28.30~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-30-generic                   3.19.0-30.34~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-31-generic                   3.19.0-31.36~14.04.1                                amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-vivid                         3.19.0.31.18                                        amd64        Generic Linux kernel image

---

### Post by yancek on 2015-11-05
> What do you advise me to do?

Do what oldfred suggested below, use the search function in synaptic to find kernels by search for linux-image.  You know the current one so make sure you don't delete that.  Usually best to keep at least the two most recent.  Check the link oldfred posted for more details on doing this.

> In synaptic search for linux-image to choose to delete old ones

I'd suggest bookmarking the link oldfred posted, especially if you have a small boot partition.

---

### Post by ajgreeny on 2015-11-05
And so we know exactly what we are dealing with can you show us the output of the terminal command ```
sudo parted -l
```

---

### Post by chris405 on 2015-11-05
Ok, I'll try and delete some Kernels. 

**sudo parted -l**
 
Model: ATA SAMSUNG HD103SJ (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      1049kB  256MB   255MB   primary   ext2         boot
 2      257MB   1000GB  1000GB  extended
 5      257MB   1000GB  1000GB  logical                lvm

Model: WD My Passport 0748 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary  ntfs

Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 8586MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  8586MB  8586MB  linux-swap(v1)

Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 991GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  991GB  991GB  ext4

---

### Post by oldfred on 2015-11-05
That is the LVM install option.
LVM is only the default with full drive encryption. Did you select full drive encryption as part of your install?
Otherwise is is an advanced logical partition overlay over standard physical partitions and requires different tools to modify. And with the smaller /boot partition needs regular maintenance.

Most desktops do not need the /boot partition, but LVM does have it, and encrypted drives have to have a separate /boot as the boot is not encrypted, but everything else is.

---

### Post by chris405 on 2015-11-05
Ok, I must have selected full drive, thinking it was asking me if I wanted to use the full drive for Ubuntu like the way a Windows asks you if you want to use the full drive during install, as I wasn't planning on creating a duel boot system.
So as long as it keep removing old kernels and emptying my recycle bin I should be ok from now on? so there isn't an option to turn encryption off or to decrypt it?
Ok, now I wait until the next update prompt and see what happens :)

---

### Post by oldfred on 2015-11-05
You cannot just turn off encryption and have a standard install. 
LVM is partitioning and to change to standard partitioning, you would have to backup all your data and reinstall. 
Of course with full drive encryption, you need to have very good backup procedures as drive hiccups or any issue can be much more difficult to repair. Standard tools to try to recover data do not work with encrypted data. Only if system is still good enough that you can mount and use pass phase is there any hope of recovering data.

---

