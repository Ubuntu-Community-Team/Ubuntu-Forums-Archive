---
title: "Hardy / XP Dual Boot - Partition Question"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by maroonandwhite on 2008-04-26
I attempted to resurrect my bloated Dell XPS M1710 with a clean OS install.  My goal was to set up a dual boot configuration with Hardy and Windows XP.  While I thought the installs went well, I have concerns regarding the hard drive partitioning, and I'd really appreciate some expert advice at this point in case I need to start over completely.

First, I installed a fresh copy of XP.  When I did, there were four existing partitions.  I wanted to install XP in one partition, and then use the file partitioning tool in Ubuntu to do the more complicated divisions when it came time for that install.  However, I could only delete two of them, leaving me with a ~4 gig NTFS partition, and a ~93 gig NTFS partition (3 gig was untouchable, which I've read is a hidden Dell recovery partition). I tried to install XP onto the larger partition, but it wouldn't allow me, saying that there was already an OS installed there.  So, I pointed it at the small partition assuming I could rearrange things later.  XP installed perfectly, and ran well.

Next, I installed Ubuntu.  My ultimate goal, based on my research, was to have a 10 gig NTFS partition on which XP was Installed, a 10 gig ext3 partition on which Ubuntu was installed, a 2 gig swap file, with the remainder being a large ext3 /home partition for Ubuntu settings as well as shared space that XP could also read and write to (using FS-Drive).  I wanted to be able to boot to either  OS using Grub.  

Playing with the Ubuntu partition tool during the install, I thought I had achieved my goal.  However, I was unable to enlarge my NTFS partition.  This means all of my Windows programs will have to be installed in the ext3 partition-- will this work?

Also, Grub only recognizes Ubuntu as bootable, so I have not been able to boot into XP.  I've tried to flag the NTFT portion as boot using gparted, but that causes the boot flag to be removed from the Ubuntu section.  Also, the boot flag is on the large ext3 partition I wanted to use for settings and shared files, not the small partition I wanted to house the OS.  

If any of you experts can point me in the right direction, I would really appreciate it.  I've been very impressed with Ubuntu so far, so I'm anxious to get this set up correctly.  BTW, I'm a technically oriented long time Windows user (although I was familiar with command line DOS operation prior to Windows 3.x), but a complete Linux newbie. Help!

A summary of my current partitioning is shown below:

Partition     Filesystem   Mountpoint   Size    Used   Unused   Flags 
/dev/sda1     ext3         /home        74.5GB   1GB   73.5GB   boot
/dev/sda2     extended                  17.3GB                  lba
  /dev/sda6   ext3         /            11.2GB   2.2GB   9GB
  /dev/sda7   linux-swap                3GB      
  /dev/sda5   ntfs                      3.11GB

---

### Post by Pumalite on 2008-04-26
Post a screen shot of Gparted.

---

### Post by maroonandwhite on 2008-04-26
Sure-- here's a GPARTED screenshot:

---

### Post by Pumalite on 2008-04-26
It seems you have XP installed in a logical partition, which causes Grub to give you an error 12. ntfs seems to be beyond /swap, maybe deleting /swap would allow you to enlarge it. But besides all that it seems an exercise in futility. You should have XP in sda1 in a primary partition and install Ubuntu in the second or 3rd partition. preferably logical inside of an extended partition.

---

### Post by maroonandwhite on 2008-04-26
Gotcha-- it seems like a big "do-over" is in order.  Any suggestions as to the best way to approach that at this point?  Should I make some changes via gparted prior to beginning the XP install again?

Thanks!

---

### Post by Pumalite on 2008-04-26
You are going to need a first partition (sda1) formatted ntfs. The rest, I'd make an extended partition an stick as many logicals as I want inside. Windows needs a primary, but Ubuntu is happy in any.

---

