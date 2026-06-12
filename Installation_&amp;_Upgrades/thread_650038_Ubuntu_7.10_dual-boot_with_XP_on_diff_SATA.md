---
title: "Ubuntu 7.10 dual-boot with XP on diff SATA"
date: 2007-12-25
forum: Installation &amp; Upgrades
---

### Post by cal1277 on 2007-12-25
I'm new to this and just bought 1TB SATA drive and installed this on a machine that already has a 200G SATA drive with XP Media Center installed (only ~40G free).

I'd like to install Ubuntu 7.10 on my new SATA drive, have the option to boot XP at startup, and be able to share files between XP and Ubuntu.

I went through the Ubuntu installation and partitioned the drive as pictured below:
#1: 98M, /boot, primary, ext3
#2: 20G, /, primary, ext3
#3: 4G, swap (I have 2G of RAM)
#4: >900G, /home, primary, ext3

[CENTER][IMG]http://picasaweb.google.com/jonnajman/UbuntuGutsyGibbonInstallation/photo#5148077060421705778[/IMG][/CENTER]
[COLOR="Gray"][SIZE="2"]Link: [http://lh6.google.com/jonnajman/R3Gkz47F4DI/AAAAAAAAAOw/NoS28CJtq-w/Screenshot.jpg?imgmax=640](http://lh6.google.com/jonnajman/R3Gkz47F4DI/AAAAAAAAAOw/NoS28CJtq-w/Screenshot.jpg?imgmax=640)
[/SIZE][/COLOR]
After partitions are created, there is an Advanced tab to Install Boot Loader.

[CENTER][IMG]http://picasaweb.google.com/jonnajman/UbuntuGutsyGibbonInstallation/photo#5148081101985931330[/IMG][/CENTER]
[SIZE="2"][COLOR="Gray"]Link: [http://picasaweb.google.com/jonnajman/UbuntuGutsyGibbonInstallation/photo#5148081101985931330](http://picasaweb.google.com/jonnajman/UbuntuGutsyGibbonInstallation/photo#5148081101985931330)
[/COLOR][/SIZE]

The last unsuccessful attempt I entered (HD1,0) in the advanced tab thinking this would install the boot loader (GRUB?) on the /boot partition of the 1T drive. I restarted and was prompted to remove the Install disc. It booted to XP as usual. I restarted the computer with the Ubuntu install disc and am going through these steps again, except that the drives were partitioned, I only needed to mount them.

My questions are:
(1) Is this a good way to partition my new SATA drive?
(2) Can I partition #4 on my 1T drive into 2 subdivisions, and if so, what would be the best way to go about this (ie. ext3, ntfs)?
(3) What will I need to do in order to have both Linux and Windows access files on the ext3 partition #4 on the 1T drive?
(4) How do I finish this installation and be able to have OPTION to boot into XP at startup?

---

### Post by Pumalite on 2007-12-25
I would dual boot installing Ubuntu in the free space in your original SATA and save the second SATA for storage and other purposes. You'll have less problems with the installation. You can use Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Boot from it and resize your XP partition (right click on partition, choose 'resize' from the menu). In the new partition, a good scheme could be:
10 GB for '/'
1 GB for /swap
The rest for /home. 
Then install Ubuntu going Manual and using the partitions already made. Let Grub install to MBR. You'll have dual boot.

---

### Post by cal1277 on 2007-12-25
Thank you. I did as instructed. Using GParted, I resized #2 partition on my 250G drive containing the XP O/S. I then made the free space created as #3 primary partition as ext3. Now I cannot get XP to boot, or Ubuntu for that matter.

Using the install CD for Ubuntu, the partitions look like this:

Device | Type | Mount Type | Format? | Size | Used

/dev/sda
/dev/sda1  ntfs  /media/sda1  7517M  4200M
/dev/sda2  ntfs  /media/sda2  174408M  150400M
/dev/sda3  ext3  /media/sda3  21994M  525M

/dev/sdb
/dev/sdb1  ext3  /media/sdb1  98M  27M
/dev/sdb2  ext3  /media/sdb2  20003M  2700M
/dev/sdb3  swap                    3997M  0M
/dev/sdb4  ext3  /media/sdb4  976102M  15500M

Help!

---

### Post by meierfra on 2007-12-25
Did you  reinstall Ubuntu to /dev/sda3?  Where did you install Grub?

---

### Post by cal1277 on 2007-12-25
The original installation, if it installed correctly should be on sdb. I did not reformat the new drive after resizing sda. Should I go ahead and install Ubuntu again on sda3 and not touch new drive? Also, Grub is Boot Installer right? Should I use Gparted again to partition sda3 further, or will the install CD do this automatically? Right now sda3 is large, single primary ext3 partition. Is there any need to recover MBR for XP? - I can't get it to boot. Or will Grub be able to handle this? Thanks.

---

### Post by c0met on 2007-12-25
Hi Cal,

I'm not an expert in this, but I have been playing around with Ubuntu 7.10 on a couple of machines. I have been repartitioning, resizing, etc, just to see what happens.

(1)
Grub can certainly be set up to boot both Ubuntu and Windows - this is how I presently have it set on the machine I am currently using.

(2)
Given that you repartitioned your first drive, it is possible that you have damaged the XP installation. When I was playing around with repartitioning, there were a limited number of circumstances under which I could repartition without damaging or losing data. You should be able to see if XP is still there after you have booted from the LiveCD. If it is, leave well enough alone and just work on the second drive. You can then work on getting the first drive operational after Ubuntu is going.

(3)
I'd encourage you to leave your first hard drive alone, at present, and install Ubuntu on your second hard drive (sdb). To do this, you will need to set a mount point for one of the partitions to be " / " (without the inverted commas). You can do this using the "Manual Install". Note: For Ubuntu to install, you will probably have to check-mark "format"for the partition you have set as /.

Regards,
c0met

---

### Post by c0met on 2007-12-26
Hi again, Cal.

A couple of points when working with Grub. How I understand it is...

hd(0.0) means hard drive A, partition 1

hd(0,1) means hard drive A partition 2

hd(1,0) means hard drive B, paritition 1

hd (1,4) means hard drive B, parition 5

This would indicate that your previous installation of Grub was wrongly located.

---

