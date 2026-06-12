---
title: "can I use Easy Bcd for Xp and ubuntu Dual Boot?"
date: 2011-07-19
forum: Installation &amp; Upgrades
---

### Post by rahulkale on 2011-07-19
Hey hi guys,  I planning to re-install Ubuntu 11.04, but I prefer to do it using "/boot" loader only , so that it doesn't interact with Windows Xp Boot Files..

When Ubuntu is installed , it doesnt boot as I know , I got how to solve it too... 

[http://ubuntuforums.org/showthread.php?t=1806831]("http://ubuntuforums.org/showthread.php?t=1806831")

But Can I use EasyBcd to add Ubuntu entry to Boot Options?

Is there any other way to do it???

:confused:

---

### Post by sanderd17 on 2011-07-19
EasyBcd has nothing to do with this. You can
[LIST]
[*]not edit the xp boot files and only be able to boot XP
[*]edit the boot files and be able to choose between xp and Ubuntu
[/LIST]

There are really no other options, but you have a few choices in what way you edit those files. The easiest was explained in the post you mentionned.

If you are re-installing it, just let the installer do its work, it will go nicely along xp.

---

### Post by rahulkale on 2011-07-19
Sir please tell me one more thing... 

Should I create /boot ??? 

iF not then where should I install the bootloader??
I dont want to install it in /sda   since it mixs up with Xp, I had to format my drive for that..

I am planning to install it in         / (root)       will Ubuntu Boot from it??

---

### Post by sanderd17 on 2011-07-19
Maybe you need some explanation on the booting proces and what is mounting etc...

When you press the power button, than the BIOS loads. The BIOS is fixed on your mother board. As a last step, the BIOS looks at the first record of the first (or only) harddisk. That record is called the mbr (master boot record).

The computer starts executing what is on the mbr.

If you have only XP installed, than it will execute some code that will start XP. If you have Ubuntu and XP, than it will run some code that will start GRUB (GRand Unified Bootloader).

Grub is an application that lets you choose between different OS. So Grub is started from the mbr, but it's too big to fit on the mbr.

To get around that, the settings of Grub have to be stored somewhere else. That somewhere else is in a directory on a Linux partition.

You can put those settings on a separate partition (used for servers), than it is called the /boot partition. Or you can put the settings inside another partition. But it is very common for desktop computers to put the settings in the "boot" directory of the root (/) partition.

So than Grub loads and you can choose your OS.

I now talked about partitions.

A partition is just a part of your harddisk. In windows, partitions get drive letters (like A:, C:, D: ...) just like separate disks. But in Linux, separate disks get names like sda, sdb ... or hda, hdb ... (for "solid disk" or "hard disk"). Your HDD will get such a name, but your USB stick will also get such kind of name. Other devices that are not hard disks (like CDs) are called names like cd0 or dvd0 or cdrom.

When you have a partition on your harddisk (say on your sda), than the partitions are numbered. The first partition is sda1, the second is sda2 ...

Now, and this is very special for Linux, you can mount a partition to a directory. In Windows, you have partitions C: and D:, but they always sit on the same place.

In Linux, you can for example make a partition to store all your data and settings. Say you do this on sda1. And another partition to store the OS and the applications. Say this is sda2.

Than you have sda2 as your root partition. Grub will boot your OS from that partition and the files on that partition will be directly in the root directory, noted with a single slash /.

Now, your data is on sda1. But it's a PITA to access it every time by going to /dev/sda1/.... So you mount the partition to /home. That way, all the files in sda1 appear to you under the directory called /home.

You can do this trick for any partition. So this is also the way to put the Grub settings on a separate partition. You just make that partition appear like it were the /boot directory.

So creating a separate boot partition has the advantage that you don't have to edit it when you do something drastical to your OS, but in general, the more partitions you have, the more chance you have to select the wrong one and get serious trouble.

That's why the normal installation doens't create any separate partitions. Some prefer a separate /home partition (so that their files aren't touched when the OS is changed) and mission critical servers also have other separate partitions (like a /boot, a /usr, a /blablabla ...) but this is not needed on normal desktop computers.

I hope you understand how Linux works. You have a lot of choices, but the default one is normally the one that gives you as less problems as possible.

---

### Post by Mark Phelps on 2011-07-19
> **rahulkale said:**
> But Can I use EasyBcd to add Ubuntu entry to Boot Options?

EasyBCD only works with Vista and Win7 because it modifies the BCD.  XP has no BCD, so it doesn't work with XP.

---

