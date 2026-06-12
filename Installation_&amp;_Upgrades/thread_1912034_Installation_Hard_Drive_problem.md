---
title: "Installation Hard Drive problem"
date: 2012-01-19
forum: Installation &amp; Upgrades
---

### Post by SharkIsDangerous on 2012-01-19
Hi, I need a little help setting up Ubuntu on my PC.

I have 2 identical 750 GB HDs one of which is currently running Windows Vista. I don't want anything changed with that one. I am currently trying to put Ubuntu 11.10 on the other hard drive. I am currently running this version off of my USB drive. When I try to install it, I run into some problems.

First of all, instead of 'Install Ubuntu alongside Windows Vista' or 'Replace Windows Vista with Ubuntu' I choose 'Something else' as it makes the most logical sense. I then get a view as follows:

/dev/sda/
  /dev/sda1/  ntfs                           750xxx MB        170xxxMB
/dev/sdb

From what I can tell, /dev/sdb is my clean hard drive correct? When I double click the drive, it then brings up a new line under /dev/sdb/ entitled 'free space' (with 750154MB). I double click this and it brings up several options including type, size, location, use as, and mount point. No matter what I do, I end up getting 'no root file system is defined'. I think part of the problem may be because it won't let me choose NTFS under my hard drive, instead giving me other options including Extension 4, Fat 16, etc. 

If anyone can help me get this installed I would greatly appreciate it.

---

### Post by raja.genupula on 2012-01-20
Hi 

no root file system means , you have to select the mount point as "/" at the partition where you have to install the Ubuntu .
Type-EXT4 
Size Give what evr you want
 Mount point  as /

you did these things ?

---

### Post by oldfred on 2012-01-22
You cannot use NTFS for Ubuntu unless you install wubi inside Windows NTFS partition.

You also need to be careful to install the grub2 boot loader to the MBR of sdb.

Install to external drive 11.04.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

I prefer to partition in advance, but you can do it as part of the install.
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

