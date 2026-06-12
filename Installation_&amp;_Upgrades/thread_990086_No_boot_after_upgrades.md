---
title: "No boot after upgrades"
date: 2008-11-22
forum: Installation &amp; Upgrades
---

### Post by olihall on 2008-11-22
I am running a dual boot system with Windows XP Home Edition (Version 2002) and Ubuntu 8.04.  After my PC's RAM stopped working I have just repaired it by putting some new RAM in.  All was fine until I updated Ubuntu and Windows installed some updates.  Now both Operating Systems won't boot and when I try to start Ubuntu I get this error message:

[   0.000000] ACPI: no DMI BIOS year, acpi=force is required to enable ACPI

I get the feeling the Windows update had something to do with it as the Ubuntu updates were fine.  When I try to go into Windows all I get is a blank screen.  I've tried the Ubuntu recovery mode and I've tried to repair windows using the CD but the CD doesn't boot up properly.  

Any Ideas?  Have I done something wrong or do I have to format my system and start again?

---

### Post by Partyboi2 on 2008-11-22
Try adding the boot option that is mentioned. When you are at the grub menu where you choose to boot into ubuntu or windows press "e" after you have highlighted the ubuntu kernel. Then select the line starting with "Kernel" and press "e" again then at the end of the line add acpi=force then enter and finally "b" to boot. If this works you will need to make it permanent.

---

### Post by caljohnsmith on 2008-11-23
Were you previously able to boot the Windows CD OK? And can you boot a Ubuntu Live CD? It sounds like you might have a BIOS settings issue, based on that error you got. It might be that in the process of installing your RAM you unintentionally reset your BIOS back to its defaults or something of that nature. If you can boot your Ubuntu Live CD, I think it would also be good to run the "Test Memory" option available from the first main menu to make sure your new memory modules are working OK. Let me know how it goes.

---

### Post by ubix on 2008-11-23
There must be something wrong with dual boot systems in [color=navy]**Hardy**[/color]. However, things point to a hardware and/or driver problems on some HW platforms. When I changed my ASUS motherboard for "FXF nFORXE 610i" motherboard and reinstalling my dual-boot system I started to experience a weird boot problem. After selecting the OS in GRUB I get the following error message:```
Error 18 selected cylinder exceeds maximum supported by BIOS.
``` All these problems seem to be tied into [color=navy]**Hardy's**[/color] disk management system. However there seems to be also a M$ Windows related screwup. Namely, when you install windows onto a system with extended disk partition defined, windows installation blocks with a blank (black) screen. There is a possibility that NTFS/Extended DOS combination causes the problem instead FAT32/Extended DOS may be a better choice (I am testing this right now and do not have the results yet):(

---

### Post by ubix on 2008-11-23
My problem is resolved and described here:  ( [[color=green]**Error18 selected cylinder exceeds BIOS**[/color]]("http://ubuntuforums.org/showthread.php?t=990505") )

---

### Post by olihall on 2008-11-30
I managed to get things working on it.  I left at an hour or two and managed to boot into Windows.  It turns out Windows crashed half way through an update messing with the bios settings (I had no boot image for the motherboard after the crash).  After completing the upgrade all was fine, but I still have an annoying long term problem where I have to shut down my PC and leave it for at least half and hour before I can boot it up again!!

But being the doughnut that I am I decided to remove the Grub using "fixboot" on the Windows recovery console with the intention of installing a fresh copy of Ubuntu.  All this seems to have done is made my PC unusable.  XP doesn't boot, the PC will just restart over and over again and when I try to run the repair from the disk or the recovery console it just shuts down the system!!

Oh well, should've stuck with Linux!

---

