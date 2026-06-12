---
title: "Advice before installing Ubuntu 16.10"
date: 2017-01-04
forum: Installation &amp; Upgrades
---

### Post by mrnoob82 on 2017-01-04
Hi all, I need some advice before I go ahead and install Ubuntu.

I am running an Acer Aspire E-17 with an Intel i5 6200U with Intel Skylake graphics.
I have burned the iso to DVD and tried Ubuntu, it seems to work fine from the installer. However I am using a UEFI bios, and here is where things get difficult.
If I disable UEFI, my Windows 8.1 system will not boot. If I leave it set to on, Ubuntu does not give me the option to install alongside Windows, just the option to delete everything and install Ubuntu only.

I need to keep my Windows partition up and running. In addition, when I attempt to shrink the main HDD partition in Windows using disk management, it reports that there is not enough disk space to shrink the partition to 500GB (there is more than enough space for this) so I wonder if using Gparted is the way to go about creating a 500GB blank unallocated partition and then installing Ubuntu in to there....then hoping that the GRUB will allow the dual boot with UEFI on.

Thoughts and advice welcome.

PS I have some Linux experience, have previously run a dual boot Windows 10/Linux Mint 18 system on a different laptop.

---

### Post by howefield on 2017-01-04
Moved to the "*Installation & Upgrades*" forum for a better fit.

---

### Post by ubfan1 on 2017-01-04
Probably a good read is [http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)

Use Windows to shrink its partitions, which must be basic, not dynamic for things to work with the installer.  Make sure the Windows power option for "fast startup" is off, to prevent hibernation when you shut  Windows down.  Run chkdsk a few times to let Windows clean up its newly shrunken disk.  
Now ensure UEFI mode is set in the BIOS/UEFI settings.  Grub has no problems with UEFI, and the installer will handle secure boot too -- all problems booting are vendor specific.  Acer likes to make you set a supervisor password and "trust" the shimx64.efi and grubx64.efi Ubuntu boot files.  The install should see the Windows partitions, and let you install "alongside", but you should always be able to choose "something else" and see the Windows par;titions, make new ones for root and swap at a minimum, and install to them.

---

### Post by mrnoob82 on 2017-01-04
Thanks for that, I'd forgotten about the fast startup option. I unselected the option to install 3rd party drivers option and the option to install alongside Windows appeared. However after the install the GRUB bootloader didn't appear and Windows booted straight up. The Windows partition has been shrunk as requested but the GRUB isn't appearing even with several reboots. Any suggestions would be welcome!

My BIOS boot order has been set to:

DVD drive
Windows Boot Manager
HDD 
USB HDD
USB FDD

Or:

Windows Boot Manager
DVD drive
HDD
USB HDD
USB FDD

And:

HDD
Windows Boot Manager
DVD Drive
USB HDD
USB FDD

But on each set up the machine boots directly to Windows.

---

### Post by ubfan1 on 2017-01-05
Now try setting "trust" on ubuntu in the BIOS/UEFI settings.  Then it should be a boot optiion.  You can select it from the EFI boot menu (some   function key at power up) if it's not first in the boot order, or change the boot order to put it before the Windows Boot manager.  The HDD option will boot whatever is in /EFI/Boot/bootx64.efi, which probably defaults to the Windows boot manager, but you can replace it with a renamed shimx64.efi (and a copy of grubx64.efi needs to be present too).

---

### Post by mrnoob82 on 2017-01-06
My BIOS sucks in way I hadn't even imagined. It's beyond hard work. I had to set three passwords just to get to the trusted BIOS settings to then enable the .efi files. Took ten times longer than on my old laptop (different make and model) but I FINALLY got it to work how I want. The Ubuntu layout and software repository is vastly different to Mint, but Ubuntu will at least load how it's meant to!

Many thanks to those who replied. Got there in the end.

---

