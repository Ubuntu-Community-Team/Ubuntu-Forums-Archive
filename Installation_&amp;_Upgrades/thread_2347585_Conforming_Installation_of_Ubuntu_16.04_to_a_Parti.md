---
title: "Conforming Installation of Ubuntu 16.04 to a Particular Situation"
date: 2016-12-27
forum: Installation &amp; Upgrades
---

### Post by arashk on 2016-12-27
Hello there,
I want to install Ubuntu 16.04 on a machine that already has Windows 7, 1GB RAM. I have attached a picture of the current situation of the partitions. Drive D is empty. The tutorials I have seen on the internet are general and I could not conform them to my particular situation. Some questions are as follows:
1. According to the attached picture, is Ubuntu to be installed on drive D?
2. Should I change some parameters of D from inside Windows (Disk Management), e.g. "unallocate" it, and then begin the installation process?
3. Should I make "root", "swap", and "home" partitions in the drive D? At which stage? via "Something else" option?
And ...

Good luck
Arashk

---

### Post by oldos2er on 2016-12-27
If your computer only has 1GB RAM, I would install Lubuntu, because Ubuntu would struggle with that.

You can do everything you want to do with the 'Something else' installation option, no need to do anything in Windows ahead of time except to backup any sensitive data.

---

### Post by slickymaster on 2016-12-27
*Thread moved to **Installation & Upgrades**.*

---

### Post by oldfred on 2016-12-27
Drive D is not a drive but  a partition. And as an extended partition it can hold any number of logical partitions. Since only 33GB I would suggest 30GB for / (root) and 2GB for swap. 

Do not use Windows for Linux partitions. Only use Windows tools to shrink NTFS partitions and after any shrink you must reboot immediately so it can run chkdsk.

Ubuntu cannot install to NTFS, so you will have to delete that. If you delete in Windows, you could use auto install and it will create whatever size it thinks you need. Usually better to use gparted to partition in advance and then use Something Else to choose(change) ext4 formatted partition to / (root) and if you have swap it finds that automatically.

       Also links to more info
[http://gparted.org/documentation.php](http://gparted.org/documentation.php)
GParted partitioning software - Full tutorial 
[URL="http://www.dedoimedo.com/computers/gparted.html"]http://www.dedoimedo.com/computers/gparted.html

      [/URL]
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing) 
    [URL="http://www.dedoimedo.com/computers/gparted.html"]
[/URL]

---

### Post by Impavidus on 2016-12-28
> **oldfred said:**
> Ubuntu cannot install to NTFS, so you will have to delete that. If you delete in Windows, you could use auto install and it will create whatever size it thinks you need. Usually better to use gparted to partition in advance and then use Something Else to choose(change) ext4 formatted partition to / (root) and if you have swap it finds that automatically.

+1 to that.

The easy way is deleting the D partition in Windows, then booting from the live disk. When you install Ubuntu, you can choose "install alongside" and the installer will create a root partition and a swap partition in the unallocated space. If you wish, you can choose "something else" and partition manually. But don't choose "use entire disk" as that will wipe your C, E and F partitions. And make sure you have backups of the important stuff in C, E and F partitions anyway.

33GB disk space is enough, but not a lot. Best to have only root and swap partitions. 1GB memory is not a lot. A lighter flavour like Xubuntu or Lubuntu may be better than Ubuntu.

---

