---
title: "Install ubuntu on machine with pre-installed Vista ?"
date: 2007-02-17
forum: Installation &amp; Upgrades
---

### Post by erland on 2007-02-17
I have seen a lot of threads about people having problems with dual-boot and Windows Vista. The situation is that I have just got a new work laptop and it has Windows Vista Business pre-installed as a large partition covering the whole disk.

I have tried to boot with a LiveCD and everything seems to work, so I would now like to install Ubuntu on the hard disk.

I have understand that it is a bad idea to do any partition resizing on the Linux side, since this seems to cause problems with the Vista installation.

I don't want to reinstall Windows Vista since there is a lot of programs already installed and configured, so I would like to shrink the Vista partition to make some room for the Ubuntu partitions. I know about coLinux and VMWare solutions, but I would prefer a solution where I didn't have to run linux from inside Windows.

So, is there a safe way to do this that won't leave me with a non bootable Vista installation ?

I'm thinking something like:
1. Shrink Vista partition from inside Vista with its partitioning tools
2. Reboot with Ubuntu Edgy Installation CD and install Ubuntu and create the ext3/swap Ubuntu partitions during the installation. Install GRUB on the MBR.

Is this a safe way to do this or is there any risk that this will leave me with a non working Vista ?

---

### Post by Sqwishy on 2007-02-17
I'm pretty sure installing ubuntu with vista installed is the same with installing ubuntu when xp is installed. You could repartition it within vista or from the cd, i've never had any data loss when repartitioning my windows partitions from the ubuntu live cd (unless it was intentional).
Safest thing is to back everything up and repartiion it within vista. Then install ubuntu after and make a...
ext2 boot partition (100 or so mb mounted at /boot)
linux swap (size of your ram)
ext3 linux happy (size of your linux mounted at / )
:) hope taht helps

---

### Post by erland on 2007-02-18
Just for information, I decided to try as I described in my initial post and it seems to work. Both Ubuntu and Vista is now booting in a dual-boot configuration.

---

