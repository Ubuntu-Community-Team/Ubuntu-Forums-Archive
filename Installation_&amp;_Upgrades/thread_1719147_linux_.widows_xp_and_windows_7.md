---
title: "linux .widows xp and windows 7"
date: 2011-04-01
forum: Installation &amp; Upgrades
---

### Post by vinycool on 2011-04-01
can i have three os in my system i mean windows 7 , windows xp and linux any tutorials will be helpfull to me

should i install all 3 os in different drives  or else in all in one drive that is c drive

---

### Post by Dutch70 on 2011-04-01
> **vinycool said:**
> can i have three os in my system i mean windows 7 , windows xp and linux any tutorials will be helpfull to me

should i install all 3 os in different drives  or else in all in one drive that is c drive
This is assuming you are using one hard drive.

Yes, you can have just about as many as you want. You have a lot of options on how to install them. Too many to name here, but I would suggest installing windows into primary partitions first. You can have a maximum of 4 primary partitions. 

Then install Ubuntu into an extended partition, which counts as one of your primary's. You can create more than 60 logical partitions inside the extended partition. Ubuntu is happy in a logical part. windows is not.

[[COLOR="Blue"]http://lifehacker.com/#!5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony[/COLOR]]("http://lifehacker.com/#!5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony")
[[COLOR="Blue"]https://help.ubuntu.com/community/WindowsDualBoot[/COLOR]]("https://help.ubuntu.com/community/WindowsDualBoot")

[[COLOR="Blue"]https://help.ubuntu.com/community/HowtoPartition[/COLOR]]("https://help.ubuntu.com/community/HowtoPartition")

That should get you started.

---

### Post by oldfred on 2011-04-01
I prefer an operating system on each drive. It helps isolate issues. If you install both windows on one drive, it will combine boots into one and grub will only boot the first windows as the second install of windows has no boot files. With two drives you can hide the first install so each windows is separate.

Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate them from drive to drive.

Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

### Post by vinycool on 2011-04-01
[_[COLOR=Black]first of all i want to thank  [/COLOR]_]("http://ubuntuforums.org/member.php?u=595401")[oldfred and ]("http://ubuntuforums.org/member.php?u=852711")[Dutch70 for their reply ]("http://ubuntuforums.org/member.php?u=595401")
thanks for the links it will take a week for me to understand all the links  
i am using   one hard drive** still confused about the drives** . what happenes if i install 3 os in 3 different drives.one of my friend told first install xp then windows 7 then linux but make sure to install linux in last drive.and another friend told all 3 os should be in one drive.:(
now i had installed 2os that is** windows 7** and **linux**. first i had installed windows 7 then using wubi software i had installed **ubuntu-10.10-desktop** both are in same drive that is c drive its working fine,
i am new to this website

---

### Post by oldfred on 2011-04-01
Do you really have 3 physical drives? Windows confuses drives and partitions as it calls both drives. Your C: drive and D: drive may be two physical drives sda & sdb in Linux or two partitions sda1 & sda2 in Linux.

If you only have one drive then be sure to use primary partitions for both installs of windows. Linux is perfectly fine in logical partitions and if you want a NTFS data partition windows will read that from a logical partition also. 

Windows will let you install a second windows into a logical but if you ever uninstall the first you will not be able to repair the second as the install in a logical can only boot thru a primary partition.

Basics of partitions:
[https://help.ubuntu.com/community/DualBoot/Partitions](https://help.ubuntu.com/community/DualBoot/Partitions)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by vinycool on 2011-04-01
i have only one  hard disk and it  is 500bg ,having 5 drives each of 100 gb ntfs  format

---

### Post by Dutch70 on 2011-04-01
You're confusing drives & partitions. A drive (hard drive) is like a house. Partitions are like rooms inside the house. 

*I'm talking in Linux terminology here.*

You can't install 2 OS's inside the same partition. Decide how much space you want to give to each OS.

eg.
Window Vista/xp = 150GB
Windows7 = 150GB
Ubuntu = 200GB

Create 1 primary partition for Vista/xp. 1 primary partition for windows7, and then create an extended partition with the remainder of your disk. Inside that extended partition, you need at least 2 for Ubuntu. 1 for Swap equal to the size of your RAM, (plus a little if you want) and the rest for Ubuntu. 

Get used to this symbol "/" ...just the slash without the quotes. It means "root" and basically it is the Ubuntu system.

I've included a pic of my hard drive to give you an idea of partitions. I'ts only one drive, but has several partitions.

Partitions outlined in dark blue are primary. The big space with smaller partitions is extended. The partitions inside the extended, are logical partitions. It'll come to you, There's only 3 diff kinds.

---

### Post by oldfred on 2011-04-01
If you have 5 partitions you may have a problem. MBR(msdos) only allows 4 partitions. Windows often converts from standard partitions to a logical volume system that is not compatible with anything. When you look at your partitions in windows are they basic or dynamic? If basic you are ok.

---

