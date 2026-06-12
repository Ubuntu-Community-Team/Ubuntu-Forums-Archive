---
title: "Unable to dual boot with Windows 8"
date: 2013-05-30
forum: Installation &amp; Upgrades
---

### Post by samunitions on 2013-05-30
Hello,
I'm a Linux beginner, haven't used it since I graduated in 99.

But I'm a Windows developer with reasonable infrastructure knowledge.

Today I downloaded the latest ubuntu version and attempted to install it.
I created a bootable usb
Freed up 100GB of space on the hd, and left them unallocated

Rebooted , and chose the Install Inside Windows 8 version....

I get a Signal 15 error and the machine reboots.

From reading many related threads it seems to be due to partition configuration.
I've attached a snapshot of my partition configuration.

Would appreciate advice on how to proceed from here, given that I cannot delete this Win 8 installation, and require all the files in C: and F: to remain intact.

Thanks
-Sam Amin

---

### Post by gordintoronto on 2013-05-30
It's always helpful to say what version of Ubuntu you downloaded. The latest version is 13.04, but I think it no longer supports "inside Windows." In any case, if you created a partition for Ubuntu, you don't want "inside Windows." I have not installed Ubuntu in exactly the configuration you have, but I think there might be a "install in free space" option. If not, choose "something else" and manually specify the partitioning. (You might find it useful in the long term to specify three Linux partitions: / (root) of about 20 GB, swap just a bit larger than the computer's memory, and /home for the rest. This simplifies installing new versions when they become available.)

I hope you have multiple full backups of your files, since it is easy to make a mistake which wipes everything from your computer.

Does the hard drive use GPT partitioning?

---

### Post by arpanaut on 2013-05-30
Linux does not recognize dynamic disks.
You will need to find a way out of that before you can install.
Take a look at this post: [http://ubuntuforums.org/showthread.php?t=1705481&p=10552116&viewfull=1#post10552116](http://ubuntuforums.org/showthread.php?t=1705481&p=10552116&viewfull=1#post10552116)

---

### Post by fantab on 2013-05-31
> **samunitions said:**
> ...
I created a bootable usb
Freed up 100GB of space on the hd, and left them unallocated

Rebooted , and chose the Install Inside Windows 8 version....

I get a Signal 15 error and the machine reboots.

You are using legacy 'msdos' partition table and not 'GUID' partition table [GPT] which is, more or less, a norm these days with OEM. 

> **arpanaut said:**
> Linux does not recognize dynamic disks.
You will need to find a way out of that before you can install.
Take a look at this post: [http://ubuntuforums.org/showthread.php?t=1705481&p=10552116&viewfull=1#post10552116](http://ubuntuforums.org/showthread.php?t=1705481&p=10552116&viewfull=1#post10552116)

+1.

'msdos' partition table can only have FOUR Primary Partitions. If you force the FIFTH partition then Windows converts 'Basic' disks to "Dynamic" disks. 'Dynamic' is a Microsoft Proprietory and Linux based OS cannot work with those. That is why you have to convert them back to 'Basic'.
To overcome this 'Four Primary Partition' Limit we use EXTENDED partition, which serves as a Primary Partition but is not exactly a Partition itself. It serves as a 'container' for LOGICAL Partitions within it. You can have more than 100 Logical Partition within an Extended Partition.
Both Windows and Ubuntu recognize Logical Partition and can read and write to it. However, Windows CANNOT boot from Logical partition but Ubuntu can.

My two cents...

---

