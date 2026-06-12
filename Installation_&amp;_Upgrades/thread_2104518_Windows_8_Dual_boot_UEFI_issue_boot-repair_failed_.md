---
title: "Windows 8 Dual boot UEFI issue boot-repair failed or user error"
date: 2013-01-13
forum: Installation &amp; Upgrades
---

### Post by switch89 on 2013-01-13
I have an HP ENVY dv4 with windows 8 preinstalled.

To boot the 64-bit ubuntu install disc I had to switch my bios to enable legacy mode.  It installed fine as far as I can tell.  GRUB however has never loaded.  I've switched the BIOS settings back and forth from UEFI (with and without secure boot) to legacy, etc with no luck.  It boots into windows 8 everytime with no GRUB screen ever occurring.  I've run through several tutorials all to no avail.  I've run boot-repair from the live CD a couple times.  The last time I used advanced settings and purged grub before running with otherwise default settings.  The URL I have is: [http://paste.ubuntu.com/1528180](http://paste.ubuntu.com/1528180)

Any ideas?

---

### Post by oldfred on 2013-01-13
It looks like your install is now in UEFI mode. The list of UEFI boot entries shows ubuntu as this in line 923.

Boot0001* ubuntu

If you boot that entry from UEFI does it not boot?

Is secure boot on or off? And fast boot off?

And it looks like Boot-Repair found a bunch of other HP efi boot entries. 
Grub still has the bug that its entry that refers directly to sda4 or sda5 will not work.

---

### Post by switch89 on 2013-01-13
Fast boot is off.

Secure boot is off.

And I have no option to boot ubuntu.  It dumps into Windows 8 with no option to me at any point, everytime.

In the boot options for UEFI in my BIOS, there's nothing but OS boot manager in the UEFI options.  And there's another setting which references my hard drive, but it doesn't point to separate partitions, just the one hard drive so I can't change anything.

---

### Post by switch89 on 2013-01-13
Ok so I found a way to boot ubuntu:

FROM windows 8 I have to choose advanced startup in order to boot from the hard disk where GRUB is installed instead of dropping into Windows boot manager. 

I can't seem to boot directly with any of the BIOS settings, however from a powered down state.

This is slightly annoying, but I'm relatively ok with it.

---

### Post by oldfred on 2013-01-13
I thought that was the quick boot or fast boot setting. With that on, you had to use Windows to get back to the UEFI menu. But with it off, you should get to UEFI menu and be able to set Ubuntu as default.

A few UEFI systems will only boot the Windows boot entry. Some have renamed the Windows entry as a backup, put grub or grub's secure boot file into the Windows file and rename it to the Windows name. Then chain load from grub to the backed up Windows efi file to boot Windows.

I would fully back up efi partition if you want to try any of this:

       Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.

    
       To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply

    
       sony vaio laptop error: symbol not found: `grub_efi_secure_boot'.
[http://ubuntuforums.org/showthread.php?t=2102083](http://ubuntuforums.org/showthread.php?t=2102083)
So this time I installed 12.10, then I booted again from liveCD, made backup of (efi part)/EFI/microsoft/boot and copied all files from /EFI/ubuntu into it. Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi. And it works

---

