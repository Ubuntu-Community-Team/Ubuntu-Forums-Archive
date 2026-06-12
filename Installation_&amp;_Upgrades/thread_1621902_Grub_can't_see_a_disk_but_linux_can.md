---
title: "Grub can't see a disk but linux can"
date: 2010-11-14
forum: Installation &amp; Upgrades
---

### Post by gsiliceo on 2010-11-14
Hello, i recently installed ubuntu 8.04.1(i dislike a few things about 10.04) in a HP proliant server, all went well in installation as expected the problem is this.
This is is how i configured my partitions on the installer(manually=

scsi disk partition1 ext3 /boot
ide disk partition1 ext3 /
ide disk partition2 swap

I did it this way because the scsi is failing, so i figured the less i use it the better and since i'll only be using it for booting up i should be ok.
**The problem is** grub can't see the IDE and doing some research i discovered that Proliant servers are designed to only boot their scsi disks, and i comfirmed this looking around the BIOS.
The setup did see the IDE and it mapped it to hda and the scsi mapped it to hdb but when i do the first boot grub comes up but it tries to boot the scsi! that of course only contains /boot and if i manually change the grub entries it fails to see the IDE.
Is there anyway i can load the linux kernel in /boot and then tell it to load the kernel in the IDE? because grub can't see the IDE but the linux kernel can.
Any help appreciated

---

