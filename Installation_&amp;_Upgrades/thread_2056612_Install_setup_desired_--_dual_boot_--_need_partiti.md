---
title: "Install setup desired -- dual boot -- need partition help"
date: 2012-09-11
forum: Installation &amp; Upgrades
---

### Post by butsam on 2012-09-11
My computer is a new HP Pavilion HPE h8-1360t (64-bit) w/ 3rd gen quad-core i7 processor, 12 GB RAM, and 2 separate 1 TiB hard drives.

I want to keep hard disk #1 as Windows 7, and hard disk #2 I want kubuntu.

When I went through the kubuntu setup, it seemed more unintuitive than with old versions of Ubuntu to set up this scenario.

In Windows, I used the default Partition Editor to free up the 2nd HDD, so it now shows as unpartitioned space.

Is there an easy way to have kubuntu use all of a single hard drive, but keep the main Windows hard drive untouched? I thought there used to be a "use all unpartitioned space" option or something like that...but now I can't find it in kubuntu 12.04.1 x64's install.

Please help me! What should I do to get this desired setup?

Thanks!

Sam

---

### Post by zvacet on 2012-09-15
Read [this]("http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/").I hope it will be helpful.

---

### Post by oldfred on 2012-09-15
zvacet's link is good for BIOS/MBR.

But, with a new system you may have UEFI and gpt? 

Whichever way Windows is installed is the way you need to install Ubuntu. And whichever way you boot install media CD or USB is the way it will install. Only the 64bit version offers the choice of UEFI or BIOS/AHCI/legacy or whatever.

---

