---
title: "Partition on which ubuntu installed missing"
date: 2011-06-30
forum: Installation &amp; Upgrades
---

### Post by elpuir on 2011-06-30
I use Windows 7: Home Premium and I have three partitions on my hard disk. Lately I installed Ubuntu NOT on C: (win 7) BUT on D: (size 104 GB). Now, I CAN'T find the drive (D:\) on Ubuntu. However I can still find it on Win 7. Please help.

If a similar problem has already been discussed on some other thread, please direct me to the same. Thank you.

---

### Post by Bucky Ball on 2011-06-30
The confusion could be in the labelling. If you open Gparted (partition editor) the mount point that Ubuntu is mounted on is / and whatever label you have chosen for it (if you have used one). 

The Ubuntu install is in the directory / on sda* probably (where * is a number, sda5 for instance).

---

### Post by elpuir on 2011-06-30
I think not. Because then I should be able to see the drive when I click on Home folder rite? I don't. All the folders which I put in them while using Win 7 are now missing.

P.S: I use Ubuntu **11.04**.

---

### Post by Bucky Ball on 2011-06-30
All the folders you put in them? Windows does not natively see EXT4 partitions, which is what Ubuntu is installed on. It can see NTFS partitions, but Ubuntu won't install on one of them so I'm a bit confused.

You were in Windows and put some files on a Ubuntu partition, booted into Ubuntu and the files aren't there?

Release/version doesn't matter: the Ubuntu operating system is in /. Unless you made a separate /home partition that will be on the same partition as /. Therefore, sda5 might contain both / and /home.

---

### Post by dFlyer on 2011-06-30
> **elpuir said:**
> I think not. Because then I should be able to see the drive when I click on Home folder rite? I don't. All the folders which I put in them while using Win 7 are now missing.

P.S: I use Ubuntu **11.04**.

NTFS can not read ext4 files, so it's not possible to transfer files from windows to ubuntu. Ubuntu can read NTFS and you can access windows from Ubuntu, but not the other way.

---

### Post by elpuir on 2011-06-30
@Bucky Ball:
Yes, all the folders that I had put in them while using windows are now missing. I have attached a screenshot of my Disk Management window. The 'Entertain.. (113 GB)' drive is what I'm talking about. I installed Linux on it (from windows itself. i.e, Didn't use a CD or a bootable USB). Now that drive, even though seen on Disk Management, is not accessible. 'File System' (which is what linux calls it) drive only has linux folders and not the folders that I had on 'D: (Entertain)' before installation. This is the problem as I understand it. I don't know what 'ext4' is. Please help.

---

### Post by georgelab on 2011-06-30
As a matter of fact, ext4  filesystem is a journaling file system for Linux. Windows can't browse ext4 filesystems.

---

### Post by Bucky Ball on 2011-06-30
Sounds like you've installed from wubi. You were running Ubuntu inside Windows but installed, like a program, and then you installed it to the hard drive?

---

### Post by dFlyer on 2011-06-30
Are you using wubi? If so I believe it also creates an ext4 space on it's install and as everyone has been says Windows can not copy, transfer in any way any file to an Ubuntu install.

---

### Post by elpuir on 2011-06-30
@all:
That's right. I ran a file 'wubi.exe' to install Ubuntu 11.04 from Win7. Now, is there a solution to this problem?

Even if I have to re-install, how do I do it? The way I already did install is the only way I know to do it.

---

### Post by dFlyer on 2011-06-30
Install a dual boot system. Uninstall wubi and partition your hard drive correctly and reinstall to a dual boot, with windows in one partition and Ubuntu in another partition. Wubi is just running a windows/linux program within windows.

---

### Post by Bucky Ball on 2011-06-30
Wubi is to try Ubuntu for awhile to see if you like, not a permanent solution. Download the ISO and burn a CD to boot from and then dual-boot, as suggested, if you are intending to keep Windows. There is a lot of help around to get you through it ...

---

### Post by georgelab on 2011-06-30
Make a Ubuntu live CD or bootable USB disk, then run the live test. If you like it, you can install Ubuntu to disk from the live CD... It's quite simple. Ubuntu detects your Windows partition.

---

### Post by bcbc on 2011-06-30
Just look under /host and you'll see your D drive.

If you're on 11.04 with Unity, click on the Home icon, then Computer, then host. (Something like that).
Or from a terminal (Ctrl+Alt+t): nautilus /host

---

