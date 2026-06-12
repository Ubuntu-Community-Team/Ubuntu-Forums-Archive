---
title: "grub error 21"
date: 2008-04-05
forum: Installation &amp; Upgrades
---

### Post by fbaerkir on 2008-04-05
Hi - one thing I should say right off the bat is I'm a noob, so be gentle!
OK, I tried many, many ways of dual booting Vista and Ubtuntu on the same RAID 5 array, with no luck. I finally slapped in a PCI IDE card, and am trying to install Ubuntu on a separate drive. It seemed to work OK, but when I tried to boot I got the message Grub error 21. Is this because it's trying to install a grub loader on the RAID, which Ubuntu doesn't recognize? Or is the Grub on the IDE drive I installed Ubuntu on? Any ideas?

---

### Post by dstew on 2008-04-05
> I finally slapped in a PCI IDE card, and am trying to install Ubuntu on a separate drive.You are trying to install onto the un-RAIDed IDE drive, correct? How are you installing, with a Live CD or Alternate Install CD? When you tried to boot, did you get the error message with an explanation, like "Selected disk does not exist", or was it just the number? Can you still boot Vista?

As far as I know, if you install from a Live CD, there is no provision to recognize a pre-existing RAID, unless you install some RAID software into the Live CD system. Usually, it sees the RAID as separate disks, not as a single RAID device. When you install grub, it might be put into the MBR of the first RAID disk. This can overwrite whatever was there before, which might be a non-standard partition table that was part of the RAID setup, destroying the RAID (or at least messing it up -- you might have to restore it). If grub was installed onto the MBR of the first disk, it had to be setup to find its stage2 from an un-RAIDed disk, because (I am pretty sure of this) grub cannot see RAID devices. If there was an error in setup, because the RAID was not detected, grub could have been mis-directed to look for its stage2 in one of the RAID disks. It finds a non-standard partition table, and gives the error.

---

### Post by fbaerkir on 2008-04-05
From what I do know that does seem to be the problem. I see all my disks individually rather than as one disk plus a RAID. You're right about my trying to put Ubuntu on the non-RAID disk. It did mess up the MBR, but I was able to restore it. 
So what if I install, but specify not to write to the other disks (that looked to be an option in the install process)? Does grub have to go into Windows' MBR to dual boot, or can it live separately?
If it does need to go into the RAID, can I edit grub to see all the disks, or is there more to it?
Thanks for the help!

---

### Post by dstew on 2008-04-05
> So what if I install, but specify not to write to the other disks (that looked to be an option in the install process)? Does grub have to go into Windows' MBR to dual boot, or can it live separately?Grub does not have to go into the MBR of any particular disk, it can live anywhere, but it does need to be somewhere that BIOS can boot. So, if BIOS can boot your non-RAID IDE disk, you can install grub there, and if you boot that disk, grub will be able to boot an Ubuntu system that is on the non-RAID disk. However, I do not think that grub can boot a RAID of any kind.> If it does need to go into the RAID, can I edit grub to see all the disks, or is there more to it?Reading around, it seems that grub is not a good choice if you want to install to and/or boot a RAID. I don't think you can install grub onto a bootable RAID. It seems that LILO has the ability to be installed to and boot RAID partition: see [this HowTo]("http://tldp.org/HOWTO/Boot+Root+Raid+LILO.html"). Also, this [Ubuntu HowTo]("https://help.ubuntu.com/community/Installation/LVMOnRaid") gives directions for installing on a RAID. This can be done using the Alternate Install CD, it has menu choices to create and install to a RAID. It also can install LILO instead of grub to boot the RAID, I think. I do not know if LILO can dual-boot Windows and Ubuntu on a RAID though. If you want to boot with grub, you have to create at least an un-RAIDed /boot partition that contains grub's stage2, and the linux kernel, and initial ramdisk image. Once the kernel boots, it can handle the RAID. You could access the RAID, but not boot it.

---

