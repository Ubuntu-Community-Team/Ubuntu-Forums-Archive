---
title: "Extending existing Windows partition and reinstalling Windows"
date: 2018-11-23
forum: Installation &amp; Upgrades
---

### Post by rcrdo on 2018-11-23
Hi there.

I have a 500 GB hard drive in my laptop in which I have a 100 GB  partition for my Windows 7 and the rest for my Ubuntu 18.04 The problem is that my Windows is running terribly slowly and I'd like  to reinstall it and do it in a larger partition (150 or 200 GB). But I have a question. Some time ago, when I first installed Ubuntu in dual boot with Windows  (four o five years ago), I read that if you install Windows in an  computer with an already existing Ubuntu OS, Windows could overwrite the  boot loader and you wouldn't be able to boot the Ubuntu system without  doing some tweaks in the Windows boot loader. Is that still true? Because I could run into this problem if I finally format my partition  and reinstall Windows.

  
From what I've gathered, I will have to use an Ubuntu Live CD with gparted to extend the partition, then install Windows, and finally run the Live CD again to run boot-repair, which should reinstall GRUB and fix things again.
Is this right?


  Thanks.

---

### Post by oldfred on 2018-11-23
You also are probably running BIOS/MBR and Windows has a bug (Windows feature?) that deletes Linux logical partitions when it does major updates or reinstalls. Partition is still there, it just is not written back into partition table. Best after resizing partitions, to back up partition table. Then you can easily restore. Otherwise it is testdisk or parted rescue.

 Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[https://www.gnu.org/software/parted/manual/parted.html#rescue](https://www.gnu.org/software/parted/manual/parted.html#rescue)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[https://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition](https://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition) 


NTFS runs slow if you have less than 30% free space. Many housecleaning or moving some data to another NTFS shared data partition would be an alternative?

---

### Post by yancek on 2018-11-23
Best to boot GParted and get an image of the drive and post it here.  It may or may not be possible to resize/extend the windows partition.  You would need to have unallocated space contiguous to your windows partition to do that.

And yes, re-installing windows will overwrite your Grub bootloader.  You won't be asked or informed that it is happening.  YOu can repair with your Ubuntu Live CD.

---

### Post by rcrdo on 2018-11-24
Thanks for your answer.

I got a snapshot from gparted (I hope that's what you were asking for), that is attached to this message.

What I'd like to do is to extend the sda2 (Windows partition) to at least 150 GB, and I could shrink my home partition (sda5) to 200 GB, for example.
I think I might as well extend my root partition to 100 GB.

Would that be possible?

---

### Post by rcrdo on 2018-11-24
> **oldfred said:**
> 
NTFS runs slow if you have less than 30% free space. Many housecleaning or moving some data to another NTFS shared data partition would be an alternative?

Sure that's what's happening.
It runs terribly slow, and I'd never had this problem before with a Windows machine.
Besides, I'd like to install MATLAB, which takes a lot of space (20-30 GB), and that'd make things even worse...

---

### Post by yancek on 2018-11-24
Your windows installation is a Legacy/MBR install which means you have a limit of 4 primary partitions.  Windows is on sda2, a primary partition while your /home partition is on a logical partition which is inside the Extended partition, the Extended partition is a primary partition also.  To resize and extend/expand, you need the partitions (sda2 and sda5) to be contiguous which they are not.  You can tell this if you run the command:  sudo fdisk -l(Lower Case Letter L in the command) and look at the beginning/ending Sectors for sda2 and sda3.

In order to shrink or extend a Linux partition, it cannot be mounted so that means you would need to use another system or Live DVD/usb.  If you move the Ubuntu / (root filesystem) partition, you would also need to move all the data to the right which would also mean moving the boot files which would in all likelihood, render the machine unbootable. It might be possible to use a Live DVD to do this and chroot to update grub but that is a complicated process, particlularly for a new user and moving all the data on a partition makes this process a lot riskier.

Your GParted output shows your windows system has 44% free space so you might look for another reason for your problem with windows.

---

### Post by Impavidus on 2018-11-24
> **rcrdo said:**
> 
What I'd like to do is to extend the sda2 (Windows partition) to at least 150 GB, and I could shrink my home partition (sda5) to 200 GB, for example.
I think I might as well extend my root partition to 100 GB.
What would be the purpose of extending the root partition? You've got a separate /home partition, which is where all ordinary documents go. With a separate /home partition, and assuming this is not a server or such a system where a lot of stuff goes into /var, there's no need for the root partition to be any larger than about 25GB. Currently, you use just 11GB of your root partition and that's not very likely to grow much larger in the future.

The easiest way to make your Windows partition larger is to shrink your root partition. Boot a live disk, make a backup of your /home partition (and, if you wish, your root partition) and use gparted to shrink sda4 from the left. Then boot Windows and use Windows tools to expand the Windows partition. Then hope that Windows doesn't damage the Linux partitions. If it does, you're ready to recover your documents from backup.

> **yancek said:**
> If you move the Ubuntu / (root filesystem) partition, you would also need to move all the data to the right which would also mean moving the boot files which would in all likelihood, render the machine unbootable.
Actually, it's supposed to work, although I'm not sure I ever tried. I don't partition my hard drive very often. core.img (grub stage 1.5) is loaded by physical address, so that's a problem if you want to move the bios_grub partition on gpt drives with bios, but there's no such problem here. Here, core.img is at a fixed location before the start of the first partition. Loading core.img makes grub smart enough to find its remaining data by file path, independent of physical location.

Having said that, there is of course a risk with shrinking the root partition. A lot of data has to be moved on disk and if anything goes wrong (power failure, hitting the wrong button), you probably have to reinstall.

---

