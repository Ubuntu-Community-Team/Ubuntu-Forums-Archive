---
title: "mbr repair on Dell Inspiron with Windows 8 and EFI"
date: 2013-03-27
forum: Installation &amp; Upgrades
---

### Post by gemichael on 2013-03-27
I try to install ubuntu 12.10 64bit alongside pre installed efi Windows 8 on a Dell Inspiron laptop following instructions [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
When I run the the boot repair utility and reboot the laptop just hangs at the DELL logo as if it can't find anything to boot.
I tried the boot repair twice. These are the URLs it gave me.
[http://paste.ubuntu.com/5652942](http://paste.ubuntu.com/5652942)
[http://paste.ubuntu.com/5653033](http://paste.ubuntu.com/5653033)

Google says that Dell has a custom MBR. Otherwise I might try bootrec.exe /fixmbr.
I don't have windows 8 installation media.
Any ideas on how to fix this?

---

### Post by oldfred on 2013-03-28
With UEFI and Windows 8 pre-installed do not follow any of the old instructioins for BIOS and MBR(msdos) formatted drives. It is totally different.

You can only have one efi partition per drive, you have two. Remove boot flag from sda5 with gparted.

It looks like you have booted Boot-repair in BIOS mode not UEFI mode. It installed a Windows type boot loader (syslinux) to the protective MBR. The protective MBR is primarily to let old partition tools know the drive is fully partitioned with gpt, so old tools do not damage the new gpt. You can use the MBR for boot code with Ubuntu, but Windows only boots from gpt drives with UEFI.

       You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

Use Windows Disk tools to shrink the Windows partition. But do not create partitions with Windows. Reboot Windows as it has to do repairs on its new size and run chkdsk.

Other Dells that seem to have worked.

 Installing Ubuntu 12.10 x64 on Dell XPS 13 Alongside Windows from USB New user with Details post 10
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)
Dell Inspiron 17R SE -  12.04.2 but otherwise similar to XPS13 above
[http://ubuntuforums.org/showthread.php?t=2125701](http://ubuntuforums.org/showthread.php?t=2125701)
Dell XPS 14 Ultrabook what works
[http://ubuntuforums.org/showthread.php?t=2116597](http://ubuntuforums.org/showthread.php?t=2116597)
Dell 14z used Dell Recovery and Refind
[http://ubuntuforums.org/showthread.php?t=2125397](http://ubuntuforums.org/showthread.php?t=2125397)
 HOWTO Ubuntu 12.10 x64 Dell XPS 14 (UEFI + Intel Rapid Start Technology + Flashcache), bumblebee - Details
[http://ubuntuforums.org/showthread.php?t=2117166](http://ubuntuforums.org/showthread.php?t=2117166)
Dell XPS13 general info mega-thread
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Dell XPS 8500, desktop. Win 8 eventually worked (Ignore sidetrack to EasyBCD)
[http://ubuntuforums.org/showthread.php?t=2086383](http://ubuntuforums.org/showthread.php?t=2086383)
No EFI boot on Dell Inspiron One 2330 UEFI/BIOS update solved issues:
[http://ubuntuforums.org/showthread.php?t=2086631](http://ubuntuforums.org/showthread.php?t=2086631)

---

