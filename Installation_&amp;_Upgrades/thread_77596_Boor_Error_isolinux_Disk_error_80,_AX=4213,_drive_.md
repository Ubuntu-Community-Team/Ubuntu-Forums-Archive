---
title: "Boor Error: isolinux: Disk error 80, AX=4213, drive 9F"
date: 2005-10-17
forum: Installation &amp; Upgrades
---

### Post by carl999 on 2005-10-17
Here's my problem. When I first boot my machine from the Install CD of Ubuntu 5.10, it boots up fine.  What I want to do is wipe out the 40GB hard drive of a previous linux install and put on a clean install of Ubuntu. When it gets to the partitioning stage though, it screws up my partitions somehow and it won't let me continue on. I get a red screen with an error about writing the partitions (sorry that I don't remember the details). I was trying to do an LVM partition.

Anyways, I figured that I'd reboot and start over. Only now the CD won't even boot!! It stops at this point:

Loading /install/vmlinuz.......
Loading /install/initrd.gz..........isolinux: Disk error 80, AX=4213, drive 9F
Boot failed: press a key to retry...

This occurs every time I try to boot on the Install or Live CD now.
I know that I don't have a bad copy of the CD either, and it worked earlier before it screwed with the partitions.

I read somewhere that when it boots it looks for a swap partition on the hard drive and uses that if its available. I think that's the problem, since it previously screwed up the partition tables and the swap partition. All I wanted to do is go in and run fdisk (if possible, I don't know if that's available on the Live CD) and erase the screwed up partitions.  You would think that a Live CD wouldn't need to use the hard drive, and that I could boot with that.

Anyways, I don't know what do do now. I don't have a floppy drive in the computer anymore either, and it's an older PC that won't boot from USB.
Can I type something at the boot prompt to turn off using the swap drive?

Also, this isn't the first instance that I've been annoyed at the partitioning part of the installation. The other day I was trying to install Ubuntu on a rack server with 2 SATA and no IDE hard drives, and the partion program won't even recognize the SATA drives! When I do what someone suggested and change the BIOS settings for legacy SATA suport, then the CDROM isn't detected anymore! I figured that I'd put the install CD iso onto a USB flash drive and boot from that. I've seen instructions on how to get that working.
It's just been a real hassle for me so far...

All I can say is that the partitioning program REALLY needs some work done to get the bugs worked out! If any developers out there see this, could you PLEASE include an alternative (fdisk?) option in the install program? And of course fix the bugs!

Thanks

---

