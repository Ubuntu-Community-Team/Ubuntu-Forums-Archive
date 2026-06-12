---
title: "Partitioning, LVM"
date: 2013-10-25
forum: Installation &amp; Upgrades
---

### Post by mattmc74 on 2013-10-25
Hi there

I am currently trying to create a new partition using GParted Live CD so I can install Win 7 as a dual boot system on my laptop.

My understanding is that I need to resize (shrink) sda2 by 25gb and then create a new 25gb NTFS partition on which to install Windows.

Problem is I cannot resize sda2 or sda5 (the slider won't move) to make any room. I'm new to Linux so I'm sure I'm missing something blindingly obvious, so any help would be appreciated!

Thanks!

[IMG]https://db.tt/it1VBT0P[/IMG]

---

### Post by fdrake on 2013-10-25
using the live cd select the partition you want to resize (right click > unmount partition). Or check in the menu tab I think is tools> unmount partition

---

### Post by VMC on 2013-10-25
Not only is it extended but also under LVM. What prompted you to use LVM? Was this an original Ubuntu install. It looks like the LVM partition is full, or maybe that's how LVM partitions always look. I only installed LVM once and once was enough.

You could backup what OS you have there,and then start from scratch. Unless someone comes along that is LVM literate.

---

### Post by mattmc74 on 2013-10-25
> **fdrake said:**
> using the live cd select the partition you want to resize (right click > unmount partition). Or check in the menu tab I think is tools> unmount partition

There is no option to unmount sda1 or sda2 and Mount is greyed out for both.

---

### Post by mattmc74 on 2013-10-25
> **VMC said:**
> Not only is it extended but also under LVM. What prompted you to use LVM? Was this an original Ubuntu install. It looks like the LVM partition is full, or maybe that's how LVM partitions always look. I only installed LVM once and once was enough.

You could backup what OS you have there,and then start from scratch. Unless someone comes along that is LVM literate.

Thanks for your reply..

I am running Zorin. I may have installed Ubuntu originally and then uninstalled it. To be honest, I just followed the install instructions and have no clue what LVM is!

I have no idea how to backup the OS and start from scratch! 

Are you saying the partition sda2 is full (that is what sda5 shows)?

---

### Post by oldfred on 2013-10-25
I do not know LVM, nor encryption, other than LVM is a logical partition system overlayed over the physical partitions. It advantage is that then you can easily modify sizes of partitions, but it is another layer and adds complications. You cannot use standard partition tools to change lvm but have to use lvm tools.

When you choose full disk encryption you get lvm. That is not a typical standard install.

       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
lvm How-To info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
[http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html)
sudo apt-get install lvm2
sudo vgchange -ay

Linux encryption will not work with Windows. 
If you really want encryption then you may want to look into truecrypt.

---

### Post by mattmc74 on 2013-10-25
Ok, so as I understand it I must have chosen to encrypt my hard drive during installation, hence the LVM partition.

I guess I have 2 options:

1) Search and understand how to resize the LVM partition
2) Unencrypt the hdd

Is this correct? If so, which would you recommend?

Thanks


> **oldfred said:**
> I do not know LVM, nor encryption, other than LVM is a logical partition system overlayed over the physical partitions. It advantage is that then you can easily modify sizes of partitions, but it is another layer and adds complications. You cannot use standard partition tools to change lvm but have to use lvm tools.

When you choose full disk encryption you get lvm. That is not a typical standard install.

       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
lvm How-To info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
[http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html)
sudo apt-get install lvm2
sudo vgchange -ay

Linux encryption will not work with Windows. 
If you really want encryption then you may want to look into truecrypt.

---

### Post by oldfred on 2013-10-25
I do not know lvm well enough to help. The links I posted I think are a start if you want to learn lvm.

You unencrypt your system when you boot and give pass phrase. You then should be able to backup /home to an unencrypted copy on a large flash drive or other drive. 

In fact with encryption you must have really good backup procedures as any of the standard partition recovery tools will not work. And we regularly get users with drive issues and want to recovery data. Once encrypted it is not possible to get to unless it at least loads enough to ask for pass phrase.

---

### Post by Petro Dawg on 2013-10-25
The experts may have a different opinion, but from what I've always heard, it is unwise to install Windows after installing Linux.  I believe the quickest, and least troublesome route is to install Win7 first, allowing it to install on the entire drive, and then shrink the Windows partition size from within Windows using the Disk Management tool.  Afterwards, you can just install Ubuntu beside Windows, and let the Ubuntu installer handle all the partitioning for you.  This what I have done in the past, and it has served me well.

---

### Post by fdrake on 2013-10-25
+1
instruction for resizing encrypted partition : [https://help.ubuntu.com/community/ResizeEncryptedPartitions](https://help.ubuntu.com/community/ResizeEncryptedPartitions)

---

