---
title: "Ubuntu 11.10 + Windows 7 + Shared Partition"
date: 2012-02-03
forum: Installation &amp; Upgrades
---

### Post by majeedk1981 on 2012-02-03
Good Afternoon All
 I want to install Ubuntu 11.10 64bit to dual boot with Windows 7 64bit. I want to use it for 

[LIST=1]
[*]  **Android development using JDK + Android SDK + IntelliJ IDEA 11**
[*]** For FUN..**
[/LIST]
 
 My Current System is

 ```
C Drive: 50GB - Windows 7 - NTFS
D Drive: 150GB - Data Disk - NTFS
```I will repartition D Drive into 50 + 100GB so that my new system looks like

 ```
C Drive: 50GB - Windows 7 - NTFS
D Drive: 50GB - Ubuntu 11.10 - ext4 or whatever 
E Drive: 100GB - Data Disk - NTFS
```**My Questions are:**
 
[LIST=1]
[*]Can I repartition D drive from Windows 7 and then install Ubuntu on the new D drive?
[*]I want to be able to share the Data partition (NTFS) between two OS..  *Is it possible?*
[/LIST]

---

### Post by WasMeHere on 2012-02-03
> **majeedk1981 said:**
> Good Afternoon All
 I want to install Ubuntu 11.10 64bit to dual boot with Windows 7 64bit ...

[*]Can I repartition D drive from Windows 7 and then install Ubuntu on the new D drive?
[*]I want to be able to share the Data partition (NTFS) between two OS..  *Is it possible?*
[/LIST]
Hi majeedk1981,

Welcome to the Ubuntu Forums :-)

Yes and yes, you can. The NTFS file system can be mounted for read and write by linux.

0. Backup the whole hard disk drive to another drive (for example a USB drive). Editing partitions is risky!!!

1. I would suggest that you start by defragmenting the drive before shrinking it.

2. Then you can either install Ubuntu into the free space or do something a little more advanced, but not really difficult. I suggest that you boot a live session from the Ubuntu install drive, use Gparted to create

- an extended partition, and inside that create
- one logical partition to install the linux file system and
- one logical swap partition with size = size of RAM.

3. Finally install Ubuntu!

It is good to ask before you try, so you are welcome to ask more questions whenever you need.

Have fun finding out about Ubuntu
Olle

---

### Post by nipunshakya on 2012-02-03
> **majeedk1981 said:**
> Good Afternoon All
 I want to install Ubuntu 11.10 64bit to dual boot with Windows 7 64bit. I want to use it for 

[LIST=1]
[*]  **Android development using JDK + Android SDK + IntelliJ IDEA 11**
[*]** For FUN..**
[/LIST]
 
 My Current System is

 ```
C Drive: 50GB - Windows 7 - NTFS
D Drive: 150GB - Data Disk - NTFS
```I will repartition D Drive into 50 + 100GB so that my new system looks like

 ```
C Drive: 50GB - Windows 7 - NTFS
D Drive: 50GB - Ubuntu 11.10 - ext4 or whatever 
E Drive: 100GB - Data Disk - NTFS
```**My Questions are:**
 
[LIST=1]
[*]Can I repartition D drive from Windows 7 and then install Ubuntu on the new D drive?
[*]I want to be able to share the Data partition (NTFS) between two OS..  *Is it possible?*
[/LIST]


Olle had nice piece of advice...just wanna add one more thing....
After you partition your drives in windows, make sure you restart time and again to windows itself...
this makes sure that your windows will adapt to the new partition and so you will have no problem after installing ubuntu and with the shared partition...

Regards,WinuxUser

---

### Post by oldfred on 2012-02-03
Windows may have a hidden partition or two and have used all four primary partitions. If you use Windows to create new partitions it may try to convert to dynamic from basic and dynamic is a one way conversion and does not work with Linux.

Best to use Windows tools to shrink Windows partitions, but use gparted to create Linux partitions. Windows cannot create ext3, ext4 or swap partitions anyway.

---

