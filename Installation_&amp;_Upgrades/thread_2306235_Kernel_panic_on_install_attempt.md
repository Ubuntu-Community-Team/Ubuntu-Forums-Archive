---
title: "Kernel panic on install attempt"
date: 2015-12-13
forum: Installation &amp; Upgrades
---

### Post by GB_Joe on 2015-12-13
So, I've got a new HP 820 G2 with Win7 Pro 64 and I'm trying to add Ubuntu as dual-boot. I'm using a copy of 15.10 on an external USB drive which I've successfully used to install on a couple of other machines (Lenovo T430 dual boot and a brand new AMD desktop).

Initially I couldn't get the laptop to see the USB drive at all on boot until I changed the boot mode from Legacy to UEFI. There are two options for UEFI, with or without CSM, and either of these got me to the initial Ubuntu installation menu. My excitement was short-lived though; picking any option at this point gets me the following:
```
kernel panic not syncing vfs unable to mount root fs on unknown-block (1,0)
```...and a bunch of other stuff (which I can copy out if it'll help), but the end result is the only thing I can do next is hold down the power button until it shuts down. Windows won't boot until I change back to the Legacy boot mode.

I've seen several posts here with a similar error code, but they all seem to be in different circumstances where Ubuntu has already been installed and working. Does anyone have any ideas? I'm totally out of my depth here...

---

### Post by oldfred on 2015-12-13
Is Windows 7 in UEFI or BIOS/CSM/Legacy boot mode. If partitions are MBR(msdos) then it is BIOS, if gpt then UEFI.
And you need to install Ubuntu in same boot mode as Windows is installed, unless you reinstall Windows first. And how you boot installer UEFI or BIOS, is then how it installs.
New system is UEFI hardware, but Windows 7 could be either UEFI or BIOS.

Are you using 64 bit installer?

What are specs of your system? Particularly what video is it, Intel or something else.
If Intel and newer Intel chip, you may need boot parameter.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

 # Usually nVidia or AMD work with this:
nomodeset
# Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size

---

### Post by GB_Joe on 2015-12-13
I've just had a reply on the HP forum, so I can give you a bit more info.

Win7 is installed in Legacy mode (presumably this means BIOS) because that's the only way to disable Secure Boot, and Win7 won't work with it enabled. So... I guess this puts me back in the original situation where I can't get the laptop to spot the USB drive to boot from (although it's in the boot options menu and I select it).

The hardware is a simple Intel chipset and integrated graphics affair (HP have at one time offered it with Ubuntu pre-installed), i5-5200U.

The only way I can get to see the grub menu is if I put it into UEFI mode. Are you suggesting I do this and change the grub options before going back to Legacy?

---

### Post by oldfred on 2015-12-13
Not true.
Windows 7 can boot in UEFI mode, but it is true that it will not boot with secure boot on.
Some vendor's UEFI call secure boot "Windows" boot, and then for Windows 7 or Ubuntu you have to use the "other" setting but UEFI on and secure boot off. And CSM/BIOS/Legacy off.
        
How to Create a Bootable UEFI USB Flash Drive for Installing Windows 7, Windows 8, or Windows 8.1 - Also command line install of files to efi partition uses rufus
[http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html](http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html)
[http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx](http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx)

    
If Windows is BIOS, then you need to install Ubuntu in BIOS mode. If you attempt to install in UEFI mode, it will probably convert drive to gpt. And that will erase drive. 
And Windows cannot be restored from your back up (you do have a backup?) as it is BIOS/MBR mode. Windows only boots from gpt with UEFI.

Often Windows installed in BIOS boot mode has converted a gpt partitioned drive to MBR but left the backup gpt partition table. The backup gpt partition table is one of gpt's advantages.
And then Linux tools see both gpt & MBR and do not know what you want, so only option is to totally erase drive. You can manually remove backup gpt partition table if that is an issue with fixparts.

---

### Post by GB_Joe on 2015-12-15
Hi oldfred

I've managed to get this one sorted now, thanks for your help. I was able to get hold of a 2GB USB stick to use for the installation; I suspect the partitioning on the external HDD I'd been using was causing problems. I stuck with the Legacy mode in the end, apparently that's likely the only way to disable secure boot on this laptop.

Incidentally, in case anyone else comes up against the same thing, the next problem I had was the error ```
missing parameter in configuration file. Keyword: path 
gfxboot.c32: not a com32R image
boot:
``` which was solved by this thread: [http://ubuntuforums.org/showthread.php?t=2249701](http://ubuntuforums.org/showthread.php?t=2249701)

---

