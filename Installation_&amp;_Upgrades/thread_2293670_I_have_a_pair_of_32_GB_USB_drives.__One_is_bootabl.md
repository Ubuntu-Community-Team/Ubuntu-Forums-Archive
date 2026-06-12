---
title: "I have a pair of 32 GB USB drives.  One is bootable the other is blank.  Next?"
date: 2015-09-06
forum: Installation &amp; Upgrades
---

### Post by Boyntonstu on 2015-09-06
Using Universal-USB-Installer-1.9.6.1,  I installed lubuntu-14.04.3-desktop-amd64.iso to USB stick #1 with a FAT32 format.

Next, I want to install Lubuntu on the blank 32 GB stick.

I want the format, the boot and the swap files to be correct.

My goal is to run this USB as an independent OS.

Before I press Continue:

Do I remove USB #1 and insert USB 2?

What is my next step with regards to formatting, positioning the root, sizing the swap, etc.

I wish that I could call someone, to walk me through it.

Many thanks,

BoyntonStu

---

### Post by yancek on 2015-09-06
> Using Universal-USB-Installer-1.9.6.1,  I installed lubuntu-14.04.3-desktop-amd64.iso to USB stick #1 with a FAT32 format.


The first thing I would suggest if you have not done so, is boot the flash drive to test it to verify that you can boot to the Desktop.

> 
Do I remove USB #1 and insert USB 2?

No.  After verifying that the first usb you created does boot, you need to ascertain how it is seen.  You can run the command:  sudo fdisk -l(Lower Case Letter L in the command) while booted to the Lubuntu flash drive.  You should be able to determine which device it is based on the size which should show in the output which will show drives and partitions.  Once you determine that, put the second flash drive in and repeat the command.  You should show a new device in the output.  If you have one hard drive, it should show as sda, the second drive (your usb) probably sdb and the third sdc.  Without this information you may end up trying to install to the device you are installing from which won't work.

When you start the install, you will get to an Installation Type window.  Before that select the Manual option which may be called Something Else.  Make sure you select the correct device here and you can create partitions, select a filesystem type to format (default is ext4) and a Mount point of /, the symbol for root.  Use 2GB for swap if you want and the rest for the root of the filesystem.  If you want, you can create other partitions for data later but not much point on a small drive.

You might take a close look at the link below.  It's a very detailed tutorial on installing Ubuntu 14.04 but I believe Lubuntu uses the same installer so everything should be very similar. 
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by oldfred on 2015-09-06
First is system newer UEFI or older BIOS?
But either way generally better to partition in advance.

A BIOS install requires Something Else and most importantly selecting the flash drive that you are installing to as the drive's MBR of the grub2 boot loader.
Flash drive, external drive or second drive in a system all install the same way.
Link from yancek is one of the good ones.
several others, essentially the same. Review several so it may make more sense.

 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):

If you and UEFI boot come back with more questions, as a bit more complicated. Gpt partitioning and you must partition in advance with the ESP partition, but grub will not use it like it should.

---

### Post by Boyntonstu on 2015-09-06
[QUOTE=yancek;13351459]The first thing I would suggest if you have not done so, is boot the flash drive to test it to verify that you can boot to the Desktop.


Yes it boots and I can browse the web with it.

If you want, you can create other partitions for data later but not much point on a small drive.

Is 32 GB a small drive?

(default is ext4)  I read that ext3 is a better choice.  Has time changed that opinion?


Thanks!

---

### Post by ubfan1 on 2015-09-06
ext4 without journaling is what I use these days for USB sticks.  Never used swap on them.  Take a look at some of the optimizations to increase the longevity of the stick (limited number of writes) in places like [http://ghanima.net/doku.php?id=wiki:linuxtips:runningfromusb](http://ghanima.net/doku.php?id=wiki:linuxtips:runningfromusb)  With the availability of "guest sessions" in ram, using them will also help reduce disk writes.  Basically, try to move any heavily written location into a ramdisk mounted there.  The "toram" kernel line option works now, and gives a really good performance boost, but at the expense of a longer boot time.

---

### Post by yancek on 2015-09-06
> 
Is 32 GB a small drive?

Relative to the size of hard drives which are in the multiples of thousands of GB it is.  As far as a flash drive no.  ext2 or ext3 should be alright, I was just saying ext4 is the default so use what you want.

---

### Post by Boyntonstu on 2015-09-07
[QUOTE=yancek;13351459]The first thing I would suggest if you have not done so, is boot the flash drive to test it to  Make sure you select the correct device here and you can create partitions, select a filesystem type to format (default is ext4) and a Mount point of /, the symbol for root.  Use 2GB for swap if you want and the rest for the root of the filesystem.  If you want, you can create other partitions for data later but not much point on a small drive.

Install USB boots and works.

I could not get sudo fdisk-l to work from Command.

Using Terminal on he install USB and sudo fdisk-l I could see the install USB but not the blank USB.

When I plug it in it mounts fine.

I used files instead.

I determined that the OS drive will be /dev/sdg1.


The choices to mount are /  and /root.

I quit there.  

Which one?

---

### Post by Dennis N on 2015-09-07
Greetings;

Could be, but **sdg** does not seem right, because **sda** would be your first drive, **sdb** your second, and so on. How many physical drives (hard drives + flash drives) do you have connected? Also, **sdg1** would not designate a drive in Linux, but a partition.

I suggest you run

```
sudo parted -l
```

to survey the system. Here is what I get on this computer, for example:

```
dmn@Sydney:~$ sudo parted -l
[sudo] password for dmn: 
Model: ATA WDC WD5000AAKX-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  538MB   537MB   fat32                 boot
 2      538MB   42.5GB  41.9GB  ext4
 3      42.5GB  46.7GB  4194MB  linux-swap(v1)
 4      46.7GB  90.7GB  44.0GB  ext4


Model: ATA WDC WD10EZEX-22B (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  211MB   210MB   fat32                 boot
 2      211MB   33.8GB  33.6GB  ext4
 3      33.8GB  38.0GB  4194MB  linux-swap(v1)
 4      38.0GB  58.9GB  21.0GB  ext4
 5      58.9GB  86.2GB  27.3GB  ext4
 6      86.2GB  113GB   27.3GB  ext4
 7      113GB   141GB   27.3GB  ext4


Model: Kingston DataTraveler G3 (scsi)
Disk /dev/sdc: 8010MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  8010MB  8009MB  primary  fat32



```

You can see two disk drives (sda and sdb) here, and a flash drive (sdc) I plugged in. In Linux, partition #4 of sdb would be designated sdb4

Could you post your results in code tags?

---

### Post by Boyntonstu on 2015-09-07
Have a HD and 2 external USB HD's, also an SD card, and the pair of 32 GB USB's.

Should the mount be /  or /root?

---

### Post by Dennis N on 2015-09-07
OK, I trust you have the right partition. You select / as the mount point. 

Good luck. Let us know how it works out.

---

### Post by Boyntonstu on 2015-09-07
Installed.  Need to add headset.  See new post.  Thanks again.

---

