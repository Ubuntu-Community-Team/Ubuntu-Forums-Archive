---
title: "Problems with partitions during install"
date: 2010-12-20
forum: Installation &amp; Upgrades
---

### Post by ChrisCobb on 2010-12-20
Installing 10.10 from USB stick onto Acer Revo 3700.  The PC already has Win7 installed and I want to install Ubuntu alongside.

I've partitioned the drive via Win7 accordingly:
C: 108GB for Win7
D: 70GB for data
E: 40GB for Ubuntu

I've downloaded 10.10 and have a bootable USB stick with the install on.  Trying to follow the instructions ([http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)) but having problems when being asked to allocate drive space.

The instructions show there should be a "Install alongside other operating systems" option.  This doesn't exist on mine - I only see "Erase and use the entire disk" and "Specify partitions manually (advanced)".

I decided to try specifying partitions, as I definitely don't want to erase the whole disk.  Continuing with this option shows the following info:

dev/sda
dev/sda1 1MB
dev/sda2 (ntfs) 17.2GB
dev/sda3 (ntfs) 104.9MB
dev/sda4 (ntfs) 115.9GB
unusable 116.9GB

The above figures appear completely different to the partitions as per Windows above.

Questions:

1. Why didn't the "Install alongside other operating systems" option appear, as per the install instructions?

2. How can I get Ubuntu to install on the 40GB E: drive?

---

### Post by Quackers on 2010-12-20
Please will you boot into Windows and go to the disk management screen then post a screenshot of your current disk layout - as Windows sees it.

---

### Post by ChrisCobb on 2010-12-20
Quackers - screen shot attached.

---

### Post by srs5694 on 2010-12-20
Your computer uses the Windows "dynamic disks" system (aka Logical Disk Manager, or LDM). Linux has some limited support for LDM, but it's basically a Microsoft-only system that's similar to Linux's Logical Volume Manager (LVM).

AFAIK, your best bet is to convert the disk to use conventional partitions rather than LDM. The [Partition Wizard](http://www.partitionwizard.com/) utility is supposed to be able to do this, but I've never used it, so I can't promise it'll work or give more specific advice.

Another option is to install Linux in a virtual machine, such as VMWare, inside Windows. Perhaps a WUBI install would work, too, but I'm not sure of that.

Perhaps somebody else can suggest another way to get this to work.

---

### Post by sikander3786 on 2010-12-20
Windows own partition manager is supposed to convert the dynamic disks into basic one's without losing any data. But there might be complications. So if you decide to go that way, make sure you've got strong backups.

Probably, installing Ubuntu using Wubi would be much better and safer in your case and if you decide to do that, you can make your Wubi install far more stable by following the 'Permanent Fix' from this page.

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)
courtesy of forum member *Rubi1200* and others.

Or add an external drive and install Ubuntu to that one. If you decide to go that way, let us know so we can guide you regarding the install of Grub (Ubuntu bootloader) so it doesn't mess up your existing setup.

Good Luck!

---

### Post by ezsit on 2010-12-20
Even if you converted the disk to a Basic disk, you still have four primary partitions used, which means deleting at least one of them to create an extended partition to hold the Linux system. You have a  lot of work ahead.

---

### Post by hello2012 on 2010-12-20
[FONT=Times New Roman][SIZE=3]I heard about the Ubuntu from my friends, and I found that I interested in this Linux desk OS, certainly, I just known a little information about it so far, I noticed your problem, and as sikander3786 said, convert dynamic disk to basic with data back up or data security is necessary. So, I introduce you Dynamic Disk Converter to [/SIZE][/FONT][[FONT=Times New Roman][SIZE=3]convert dynamic disk to basic windows 7[/SIZE][/FONT]]("http://www.dynamic-disk.com/windows-7-convert-dynamic-disk-to-basic.html")[SIZE=3][FONT=Times New Roman], I used this software, it can guarantee the data security, you need not back up the large amount of data. Hope you can solve your problem soon, and I will pay close attention to this topic, certainly I want to know the solution in case of troubling me someday.[/FONT][/SIZE]

---

