---
title: "blank desktop after installing ubuntu on the same SSD as windows 10"
date: 2016-06-26
forum: Installation &amp; Upgrades
---

### Post by jose_santiago on 2016-06-26
SOOOO, i just installed Ubuntu on the same drive that my windows ten is on. It boots fine, but when i get to the desk top i either just have a blank desktop with nothing happening, or i get flashes of icons or a box with a bunch of folders, but they are just flashing in and out then just go away. i installed it off of a thumb drive. Could it have been corrupt?

---

### Post by yancek on 2016-06-26
The Ubuntu iso could have become corrupted during the download as it is a rather large file.  You should always do an md5 checksum to verify the download.  What software did you use to put Ubuntu on the bootable flash drive?  It also might just be a graphics driver and you may need to install a proprietary driver.  What graphics card do you have?

---

### Post by jose_santiago on 2016-06-26
I honestly can't remember what i used the first time. I downloaded the file then used a program to make sure it was bootable, then installed it. I just used rufus to redo the usb i had the files on and installed it again. the only difference this time is that i would get the screen to put my password in, but at the desk top it would just be a pinkish background, with the occasional box flickering in and out. My graphics card is  Nvidia GeForce gtx980

---

### Post by ubfan1 on 2016-06-27
Probably a video problem, the 980 is pretty new.  Starting with nomodeset,... at the grub menu screen, (instructions at bottom) type "e" to edit the boot command line for the linux kernel and add the options, one at a time to test what's needed:
Options for Video problems:

nomodeset
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic


i915.i915_enable_rc6=1

video=1280x1024-24@60
video=VGA-1:1280x1024-24@60

To allow Nvidia hybrid machines to boot.
nouveau.blacklist=1

Skylake needs this (15.04...):
i915.preliminary_hw_support=1
noveau.blacklist=1 edd=on nolapic pcie_aspm=force tpm_tis.interrupts=0 
Maybe
intel_idle.max_cstate=1 nouveau.modeset=0

---

