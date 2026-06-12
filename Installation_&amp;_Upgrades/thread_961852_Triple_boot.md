---
title: "Triple boot"
date: 2008-10-28
forum: Installation &amp; Upgrades
---

### Post by bmkulw on 2008-10-28
This has to do with setting up an IBM T23 laptop with Ubuntu 8.04. 

Before the hard disk failed, the machine was set up with a dual boot of Windows 2000 Pro and Ubuntu 7.10.

The new hard disk is 80 GB.  I recovered the Windows partition from backup and used Partition Magic to move it over and also set up a DOS partition at the beginning of the hard disk.  The DOS partition is 1.6 GB and the Windows one is 45 GB (details attached).  At the moment I'm not using a boot loader, just switching partitions manually using PM. I have about 30 GB of free space left for Ubuntu.

I have the 8.04 live CD and have been experimenting with it.  

I'd like to install the Linux so that GRUB picks up all three bootable partitions, providing a choice among them when restarting.  I noticed that I can set the boot flag of both existing partitions using gparted.

My question is:  should I do this prior to installing Ubuntu? ...or will the installation routine automatically recognize both existing partitions as bootable?  ... or will I have to configure GRUB after the fact?  If the latter, how do I proceed?

I'm a novice with Linux.  I'd like to avoid having to re-partition and start again from scratch (been there, done that--bummer).

I'll appreciate any help.

B.

---

### Post by caljohnsmith on 2008-10-28
About setting your boot flags, you should have only one partition on the HDD marked as bootable. Grub doesn't care about whether the boot flag is set on a partition in order to boot it; the boot flag is mainly for "brainless" boot loaders in the MBR (Master Boot Record) like a Windows MBR, because all a Windows MBR does is look for whichever partition is marked as bootable, and then it tries to boot the boot sector of that partition. That's the main reason why you should only have one partition marked as bootable. The other reason is because of a BIOS issue, because I know there are some BIOSes that will refuse to boot a drive unless one of the partitions is marked as bootable; but I don't know if those same BIOSes would have a problem if multiple partitions are marked bootable.

It's been so long since I installed Ubuntu from the Live CD that I don't remember how to make Ubuntu automatically detect the Windows installation to put in Grub's menu. I'm sure someone else can help you with that. But it is really easy to add Windows to your Grub menu afterwards if for some reason it isn't automatically done. I'll be glad to help with that if you end up needing a helping hand. :)

---

### Post by bmkulw on 2008-10-28
Appreciate the info.  I'm pretty sure that grub will pick up the W2K partition, but not sure about the DOS one.  I may ask for assistance later, if that turns out to be necessary. Glad to learn that modifying the grub menu is easy.

B.

---

