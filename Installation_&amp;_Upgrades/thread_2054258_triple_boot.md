---
title: "triple boot"
date: 2012-09-06
forum: Installation &amp; Upgrades
---

### Post by KRITI DUDHIYA on 2012-09-06
Is it possible to keep win7 and ubuntu on one partition and fedora or any other linux distribution on second partition of the same hard disk?
if yes, then does it require any special sequence??
thenx in advance :)

---

### Post by oldfred on 2012-09-07
The only way to install Ubuntu on the same partition as Windows is with wubi. Linux systems require Linux formats & Windows requires NTFS formats.

Wubi is a version for Windows users who do not want to partition and want an extended test of Ubuntu over just running liveCD or USB.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

But if creating a partition for Fedora you can also create partition(s) for other installs also.
Some suggest with Fedora not using the default of LVM and separate /boot, but just use a standard ext4 partition. The advantage of LVM is resizing multiple partitions, but with one partition only, it just adds a level of complication.

---

### Post by KRITI DUDHIYA on 2012-09-11
I have downloaded an iso file of ubuntu 12.04 and installed it using the option "install alongside windows". still my both operating systems, win7 and ubuntu are on a single drive. 
what does it mean then? does it mean that i've used wubi??

---

### Post by oldfred on 2012-09-11
No, you have separate partitioned install.

From terminal in Ubuntu

sudo fdisk -lu

Should show several partitions.

Windows has always confused drives & partitions. Windows calls everything a drive. Or c: drive d: drive. But c: and d:  can be either one partition each on one physical drive or two physical drives.

In Linux sda, sdb, sdc are physical drives, and sda1, sda2, sda3 etc are partitions on the first physical drive.

---

### Post by KRITI DUDHIYA on 2012-09-12
okay...


but what if i want to install ubuntu on win d: drive, not using wubi? is it possible then??
bcoz during installation it was showing only sda in the drop down list...

---

### Post by oldfred on 2012-09-12
In Linux there is no D: drive, that is Windows. And it will be NTFS formated which does not support Linux ownership and permissions. 
You have to have a Linux formatted partition to install any Linux system. Usually Ubuntu uses ext4 as its format.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

Basics of partitions:
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by KRITI DUDHIYA on 2012-09-23
Sorry, i am late.

I have gone through all the links u have sent..but i am still confused.

The  thing i'm not getting is where ubuntu is installed in my laptop and how  can i say it in windows lang. for ex. if i want to uninstall ubuntu,  then where i have to see for it..?? 

the command u have given shows:

aneki@aneki-Lenovo-B560:~$ sudo fdisk -lu
[sudo] password for aneki: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009e5fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   192892454    96446196    7  HPFS/NTFS/exFAT
/dev/sda2       192892516   976751999   391929742    f  W95 Ext'd (LBA)
/dev/sda5       192892518   329228642    68168062+   7  HPFS/NTFS/exFAT
/dev/sda6       385784973   578677364    96446196    7  HPFS/NTFS/exFAT
/dev/sda7       578677428   771569819    96446196    7  HPFS/NTFS/exFAT
/dev/sda8       771569883   868024079    48227098+   7  HPFS/NTFS/exFAT
/dev/sda9       868024143   976751999    54363928+   7  HPFS/NTFS/exFAT
/dev/sda10      329230336   382005247    26387456   83  Linux
/dev/sda11      382007296   385783807     1888256   82  Linux swap / Solaris



The questions might seem silly to you... but for me its a big question!

---

### Post by netgooroo on 2012-09-23
Hey guys,
Sorry I am late on the reply to this thread but, I thought I had some good experience with this. 

I have been running windowz with Ubuntu along side for a long time now and, the easiest way I have found is to use a partitioner to sperate the partitions on the disk for Ubuntu so, It will have space away from windwoz. 

The best one I have found, in my experiences, has been parted magic. Its very simple to use and, a snap to set your partitions up. 

I have also played around a bit with triple boot options in the past and, did not have the best of experiences with this. I did get it to work but, my system was not happy. :P

Anyway, you can do a search for parted magic and, find it pretty easy. 

Hope that helps,
netgooroo

---

### Post by oldfred on 2012-09-23
You show sda10 as a LInux partition. So that will be your Ubuntu install. And sda11 is the swap. 

From Windows you cannot see the Linux partitions as Windows does not see them. But Linux will see the NTFS partitions or in Windows they are called "drives". 

Your sda1 which is drive sda and partition number 1 is probably your c: drive in Windows. Then each additional "drive" in windows is another partition. 

In Linux we only call drives physical drives. And then we have partitions on the drives. Windows will call a second partition or a second drive as the d: drive, so it can be confusing in Windows.

---

### Post by black veils on 2012-09-24
lets see if i can over-simplify some basics.

harddrives:
that is the hardware. Windows can access these, if they are in Windows formats.

partitions:
harddrives can be split into parts, which are separate from one another, these can be like the equivalent of separate harddrives. you can have entire operating systems running in these different parts, like Windows in one, then a Linux system in another.

the reason Windows can see other partitions sometimes (which are referred to as drives) is because they are in a Windows format, eg. an ntfs data partition. but Windows **cant** access partitions which have Linux formats.

from the Linux operating system perspective, it **can** access Windows partitions (drives).

wubi:
is a weird one. its like installing an application/program on your Windows system, you then remove like an application.

---

### Post by KRITI DUDHIYA on 2012-09-24
ohkay i got this concept.

now my doubt is how can i uninstall ubuntu from my system, if i want to...

---

### Post by joco1500 on 2012-09-24
you must use wubi if you want it on the same partion as windows.

you can make more than u partions on one hdd

---

### Post by oldfred on 2012-09-24
If you want to uninstall Ubuntu, you first have to convert the MBR back to a Windows boot loader, so you can directly boot Windows without grub2's boot loader. 
You can do that from a Windows repairCD to get the Windows boot loader, or use Linux to install a Windows style boot loader that will work just like the Windows boot loader.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

Or if you prefer a gui.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)

You can use gparted from Ubuntu liveCD to delete Linux partitions and then use Windows partition tools to resize the Windows partition.

---

### Post by KRITI DUDHIYA on 2012-09-24
okay..i will try this.

all the info was very helpful..thanx @oldfred & black veils.

---

### Post by YannBuntu on 2012-09-25
There is also a graphical tool to uninstall Ubuntu: 
[https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

[IMG]http://pix.toile-libre.org/upload/original/1340275988.png[/IMG]

---

