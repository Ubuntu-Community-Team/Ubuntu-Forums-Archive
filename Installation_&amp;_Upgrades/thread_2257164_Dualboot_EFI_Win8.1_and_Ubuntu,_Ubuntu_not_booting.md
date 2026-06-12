---
title: "Dualboot EFI Win8.1 and Ubuntu, Ubuntu not booting"
date: 2014-12-17
forum: Installation &amp; Upgrades
---

### Post by Bombolero on 2014-12-17
Hey guys,
I want to install a dualboot on my Dell Inspiron 14z. It has 2 physical drives, one 250 GB SSD I want to use for Windows and a 32 GB mSata I want to use for [COLOR=#000000]Ubuntu 12.04.5 LTS[/COLOR].
It uses an Intel HD 4000 Graphics card and an AMD Radeon HD 7500M Series.
Fast Boot is disabled, Intel RST aswell. I could not find a quickboot option in the settings.  

Here's what I tried to do:
Install Windows on the 250 GB (sda). It created a bunch of partitions here, for efi and stuff. I Also left ~4GB of space for Linux' swap partition.
Install Linux on the 32 GB mSata. Here the problems started: Selecting the bootstick in UEFI mode only resulted in a blackscreen, so I tried to install it in legacy mode in order to convert it later. I also created a 4 megabyte big mbr partition on the mSata.
At this point, booting Linux in legacy mode by directly selecting the drive in the boot menu worked.
I then used a boot-repair stick to convert Ubuntu to EFI. When I now start my laptop, GRUB shows up, and if I select Windows it boots fine. Selecting Linux however results in a purple screen (normal mode) or in a blackscreen (recovery mode). 
Just before GRUB opens there are some errors showing up, but they disappear to fast to read.

I tried everything explained over at [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535), but the purple screen remains.  
When I add an echo line at the end of the Grub editor, The text will be shown and stay on the screen when I try to boot.
Here's the info file Boot-repair generated: [http://paste.ubuntu.com/9552050/](http://paste.ubuntu.com/9552050/) (sda is the sata ssd, sdb ist the msata ssd, and sdc is the boot-repair stick).

If you need more information, I'll gladly give it to you, but as a newcomer to Linux I don't know what else you might need.


regards, Bombolero

---

### Post by oldfred on 2014-12-17
It looks like Boot-Repair did convert Ubuntu to UEFI boot as you now have an Ubuntu folder in the efi partition and added that efi partition into fstab to mount as the efi partition.

I do not know AMD.
Are you able to set which video chip is used when you boot. Some have UEFI settings for that, others automaticlly switch. 
Most do seem to boot with the Intel video and that may need settings. If you were booting with the AMD the recovery mode should have worked as the recovery mode includes a nomodeset boot option.
See boot options by ubfan1, most are for Intel. Add just like the instructions for adding nomodeset as boot parameter and be sure to use your screen size not size shown in examples.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

