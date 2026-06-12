---
title: "Installing 12.10 on Dell XPS 13 (1080p) model with UEFI"
date: 2013-04-04
forum: Installation &amp; Upgrades
---

### Post by karnka on 2013-04-04
I've just gotten my shiny new XPS 13 and I want to dual boot Win 8 with 12.10. It's being rather a nightmare however.

Windows is booting from UEFI so I want to install Ubuntu as UEFI as well and have been looking at many threads on issues around this.

The most relevant seems to be this one:
[http://ubuntuforums.org/showthread.php?t=2116137](http://ubuntuforums.org/showthread.php?t=2116137)

Where someone else is (like me) having problems trying to boot from a USB disk at all (without enabling legacy boot and defeating the purpose).

I've added a UEFI boot entry as the other post suggests, pointing at  /efi/boot/bootx64.efi on the usb disk however selecting it from the boot menu I still end up in windows, every time.

Smart connect and fast boot are disabled and I've tried variations of the boot entry for both USB ports.

If anyone has any advice it would be hugely appreciated.

---

### Post by oldfred on 2013-04-04
I do not have a Dell, but a few others that seem to have made it work.

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

### Post by karnka on 2013-04-04
Thanks for that.

I've been using the first thread as a reference (without much luck!) but had seen a few useful things from yourself in there.

I hadn't thought of looking at similar situations with other laptops but that might prove very helpful. Thanks for the idea.

---

### Post by oldfred on 2013-04-04
This user with an HP just got his system working, but even with grub'2 secure boot files, he could not chain load to Windows from grub with secure boot on. It worked with secure boot off.

Bug report seems to show several brands including Dell.
 Windows will not chain load from grub -
file path: /ACPI(a0341d0,0)/PCI(2,1f)/UnknownMessaging(12)/HD(2,96800,32000,7c043777b8608641,87,f6)/File(\EFI\Microsoft\Boot)/File(bootmgfw.efi
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464)

---

