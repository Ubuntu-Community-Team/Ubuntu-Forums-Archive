---
title: "Dual boot working (Windows 10/Ubuntu 16) but failing after upgrade to 18"
date: 2019-04-10
forum: Installation &amp; Upgrades
---

### Post by nicklyarse on 2019-04-10
Hi very new to Ubuntu. After much searching through the forums I found the Boot-Repair tool and it is suggested I post the resultant fix.

I had issues starting Ubuntu 18, but could successfully use an older kernel from the boot menu, but this also failed hence the Boot-Repair.

[http://paste.ubuntu.com/p/xtbF8XY5VB/](http://paste.ubuntu.com/p/xtbF8XY5VB/)

Thank you for any help or advice.

The PC is a Z-Book 17 with SSD and Graphics card, both of which appear with issues in the forum here and on HP's forum

---

### Post by nicklyarse on 2019-04-10
Update
 - Windows 10 is still working, great, but there are now two boot entries for windows in the boot menu.
- Ubuntu will not boot regardless of the choice made in the boot menu - it just hangs

---

### Post by oldfred on 2019-04-10
Many with HP historically have had issues. Main one is HP violated UEFI standard that said NOT to use description as part of UEFI boot.
Only valid description was "Windows Boot Manager". Multiple work arounds is that is your issue.
But some with newer HP or UEFI updated on HP, do not seem to have issue. have you updated UEFI to latest from HP.
And if SSD updated firmware?

You are showing both Windows & Ubuntu in BIOS with MBR partitioning. 

You seem to have added a lot of boot parameters. Are all these valid or have been suggested for your model system?
       quiet splash pcie_port_pm=off acpi_osi=Linux acpi_rev_override=5 panic=5 $vt_handoff 
I might try replacing all of above with just nomodeset parameter. Without quiet splash you also may see boot process and where it stops. Last message is often not issue, but several lines above may be.

Generally you do need nomodeset to boot installer & first boot or until you install nVidia driver from Ubuntu repository.
Some systems do need additional parameters.

Older post, now Boot-Repair does the copy of shimx64.efi to /EFI/Boot/bootx64.efi for fallback or hard drive boot in UEFI. So manual copy like this user did is not required:
[https://ubuntuforums.org/showthread.php?t=2335223](https://ubuntuforums.org/showthread.php?t=2335223)

Is Windows fast start up off? It must be now, as grub only boots working Windows. Be sure to make a Windows repair disk for current version of Windows. When Windows updates turn fast start up back on, you may not notice & then grub will not boot Windows. And then you need to temporarily restore the Windows boot loader to MBR to boot Windows & then restore grub to MBR. 
Windows 8 & 10 are not dual boot friendly in the old BIOS boot mode. With UEFI, you can just directly boot from UEFI boot menu, if grub does not boot Windows.

Boot-Repair finds .efi boot files in ESP. And then adds additional boot entries for all those files into 25_custom in grub. Most or all can be deleted, if desired.

---

