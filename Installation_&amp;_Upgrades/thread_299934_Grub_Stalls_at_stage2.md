---
title: "Grub Stalls at stage2"
date: 2006-11-14
forum: Installation &amp; Upgrades
---

### Post by AbyssNOLF on 2006-11-14
This might not necessarily be a topic concerning Ubuntu, but Ubuntu is the only linux distro I've used. In any case, the problem is this:

I want to boot Ubuntu off a single IDE drive, however...

I have two SATA drives I had in a RAID0 array on an old motherboard. I ended up selling off that entire computer a while back, but I recently got a new motherboard that had SATA RAID support, except its by VIA instead of Sil. In any case, whenever I boot from the LiveCD, I can install dmraid, mount, and access my old RAID array just fine. However, whenever I try to boot into my Ubuntu installation on a separate hard drive, GRUB fails to load, usually hanging at "loading stage2.." This is also the case when I attempt to boot into the Super Grub Disk cd in order to try and repair GRUB. If I turn off my SATA hardware support in BIOS, however, everything works just fine., except I can't access the SATA drives anymore.

I have scoured the internet for many hours and I have attempted to follow various How-To's on setting up RAID and installing Ubuntu to RAID, or tutorials on fixing GRUB installations and so on, but I have not succeeded in anything. It is my goal not to have to reformat my SATA drives, and I do not want to install Ubuntu to them (I have already done that on a separate drive), I just want to be able to mount the drives and access them.

Does anyone have any idea why the problem is occurring or how I could resolve the issue? Why would booting the Ubuntu Live CD allow me access to the SATA RAID when I otherwise could not boot at all? Any help would be appreciated.

BTW, I'm running on the amd64 architecture and therefore am using the amd64 software. The hardware RAID support is by the vt8237 chip, and the raid firmware does not recognize that the two drives are already in a RAID array.

---

### Post by onlyoneskwalla on 2006-11-17
OK from what I understand you have 2 disks from and old raid0 computer. You have a 3rd with ubuntu installed on it. When the 2 raid0 ones are enabled you cant boot ubuntu, but when they aren't you can.   

Likely that they are counting in before your ubuntu drive, meaning Ubuntu equals hd0 when no other drives and equals hd2 when the Raid0 ones are enabled.  Even if your bios knows which to boot first, the order for grub has probably changed.

You'll likely have to edit/fix your /boot/grub/menu.lst.

Boot into a livecd with all drives enabled find out the order ubuntu list your drives /dev/hda or /dev/sda and mount your installed ubuntu partition and open /boot/grub/menu.lst.  Refer to [FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto#head-b40f74375e725eb35189a50fbb6f31b5f840fb6e") or [ubuntuGrubwiki]("https://help.ubuntu.com/community/GrubHowto") for the best info on editing it.

Post your hard drive and partition setup if you get lost.

---

