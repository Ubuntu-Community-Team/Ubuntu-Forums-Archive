---
title: "cannot boot"
date: 2011-03-11
forum: Installation &amp; Upgrades
---

### Post by ddavidd on 2011-03-11
I am trying to reinstall my Toshiba Satellite L20 laptop.

I successfully installed W2K from CD, XP from the so-called recovery disc and Ubuntu from a CD I downloaded and burnt. They are in partitions in the order XP-W2K-Ubuntu and all started and Grub worked well. 
Last night, I tried to create the common data partition in XP and it refused with silly errors (i.e. XP has probably damaged something!)
Today, the laptop will not boot at all. The message comes:
error: no such partition.
grub rescue>

This grub rescue prompt does not know the commands fdisk or find or man, not even help

I found several good instructions how to reinstall Grub, which start with booting the live CD, which I did and it worked well, and entering the command:
sudo grub
but this produces the error message 
sudo: grub: command not found

Can anyone help, please?

---

### Post by ddavidd on 2011-03-11
Further information.

according to this link:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

when I boot the live CD and look in the explorer, it should show my Ubuntu installation partition as "18 GB file system"
But it wasn't there, only 20 GB and 6 GB, which are the Windows installation partitions.
The problem seems to be that the partition is somehow lost.
Another sysmptom is that when I try to open gparted to check look at disc, it opens and then disappears without giving any information. 

Looks like I am gong to have to reinstall Ubuntu tomorrow. 
Unless anyone has any better suggestions?

---

### Post by coffeecat on 2011-03-11
I'm sorry to hear of your problems. They probably arise from this:

> **ddavidd said:**
> Last night, I tried to create the common data partition in XP and it refused with silly errors (i.e. XP has probably damaged something!)

I think you are quite right. Windows gets confused by logical partitions with Linux filesystems on them and can do amazingly ridiculous things at times. A good rule of them when you are using both Windows and Ubuntu is never to use Windows XP to create any partitions unless you are doing a fresh installation to a blank drive. To only use Disk Management in Vista and W7 to shrink the C: partition before installing Ubuntu. And to use Ubuntu's Gparted for everything else.

But to your problem. The grub error does suggest that you have lost the Ubuntu root partition, probably a victim of XP's ministrations. Also, it might have corrupted the partition table which *might* explain Gparted crashing on you.

Boot up with the live CD, open a terminal and post the output of this command:

```
sudo fdisk -lu
```That will tell us your partition layout and also if there is any inconsistency in the partition table. At least then you'll have better information for if and when you need to re-install Ubuntu.

I'll have to log off within the hour, but I'll check this thread in the morning (local time).

---

### Post by ddavidd on 2011-03-12
Hello coffeecat, thanks very much for taking the trouble to answer!

The suggested command looks like this:

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x85b05ed6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    40965749    20482843+   7  HPFS/NTFS
/dev/sda2        40965811    94847759    26940974+   f  W95 Ext'd (LBA)
/dev/sda3        94847760   156296384    30724312+   6  FAT16
/dev/sda5        40965813    53255474     6144831    7  HPFS/NTFS
ubuntu@ubuntu:~$ 

Since only Windows partitions are listed and no Ext4, this must indeed mean that Windows has damaged the Linux partition. I will have to reinstall Ubuntu, luckily I had not configured too much yet.
Yesterday I got fed up with Windows not allowing me to remove a stick and just pulled it out, which caused the data on the stick to be wiped. Dangerous operating system, Windows.
Ubuntu unmounts a stick with one click!

In case anyone else is interested in the successful installation process, I will post a list of steps once it has worked.

---

### Post by coffeecat on 2011-03-12
Good luck with that.

If you look at the figures in your fdisk output you'll see that the physical order of your partitions is actually XP, then the sda2 extended partition which would have contained the Ubuntu partitions, and lastly the sda3 FAT16 partition which would be the W2K one, I guess. The logical NTFS partition (sda5) only takes up part of the space inside sda2. It'll be easier to see when you examine it all in Gparted in the live CD.

---

### Post by ddavidd on 2011-03-12
Thanks for the advice, coffeecat, it turned out to be spot on.
If you are involved with Ubutu development, keep up the good work!

The mistake was that I thought it was better to let Windows create its own partition, but as coffeecat suggested, it worked well when I created the data partition in Ubuntu, windows accepted it straight away.

In case it is of any interest to anyone, here is a full list of the steps to install 3 operating systems on this laptop, which does not have a Windows installation CD, only an image, which can only reproduce the original installation of XP complete with Toshiba's horrible adaptations.

General installation order - Windows, oldest first, Linux last.

Run W2K installation. Create a 20 GB partition and a 6 GB partition and installd W2k in the 6 GB (won't be used much)

Run the Toshiba recovery CD and choose expert mode. It is very well hidden, but it is possible to copy the XP installation into the chosen (20 GB) partition instead of the whole disc. 

In XP, edit C:\boot.ini to add a reference to the W2K installation:
[boot loader]

timeout=10

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Professional" /noexecute=optin /fastdetect

multi(0)disk(0)rdisk(0)partition(2)\WINNT="Windows 2000 Professional" /fastdetect

Run the Ubuntu installation CD and create a third partition as swap, a fourth as Linux Ext4 installation partition and install Ubuntu in it.

Grub is installed automatically and should now offer Ubuntu or Windows at the start. If you choose Widows, the boot.ini menu appears.

In Ubuntu, create the common data partition on the rest of the disc. I formatted this with FAT 32, which has following advantages and disadvantages:
- reliable read and write from Windows or Linux (perhaps it works with NTFS as well now?)
- no permissions with the associated advantages and disadvantages
- maximum size of 32 GB

Windows needs to be persuaded to use the common data partition, for example redirect the home folder. To redirect the home folder in Linux is beyond my capabilities! :DThe data is now fully accessible from Windows or Linux.

---

