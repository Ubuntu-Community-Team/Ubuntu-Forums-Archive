---
title: "Installation of Ubuntu alongside Windows 2008 Server and Windows XP"
date: 2011-07-04
forum: Installation &amp; Upgrades
---

### Post by PauliesRhythm on 2011-07-04
Hi, here's my problem:

I have Windows XP Pro and Windows 2008 Server installed. Now I want to install Ubuntu Linux.

I chose "Something else" during installation. My drive table looks as follows:

/dev/sda1, ntfs, (WinXP)
/dev/sda2, ntfs, (just a partition with stuff)
/dev/sda3, ntfs, (Win2k8)
/dev/sda4, empty space. Note: This is actually physically located between sda1 and sda2.

Windows 2008 Server was installed after Windows XP, so Win2k8 has the boot loader with the boot menu to choose between XP/W2k8)

How can I make Ubuntu install to the empty space, and then have a boot loader that lets me choose between XP/Win2k8/Ubuntu?

I tried to proceed by choosing ext2fs as file system, but the installation proggie complained I hadn't chosen a root. ???

Thanks in advance,

Paulie

---

### Post by Mark Phelps on 2011-07-04
You get that message if you haven't designated a partition as "/".  This installer version is probably the most confusing that Canonical has developed to date.

You have to select the space, click CHANGE, and set the partition up to mount to "/".

Only THEN, will it let you continue the installation.

---

### Post by oldfred on 2011-07-04
You want to create an extended partition for all the free space you have. then create / (root) and swap partitions as logical inside the extended. But I suggest a separate /home also.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Windows has literally moved boot files from the first install to the partition with the second install. You may be able to move them back and edit boot.ini to work.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

