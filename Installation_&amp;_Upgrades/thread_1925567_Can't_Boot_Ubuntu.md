---
title: "Can't Boot Ubuntu"
date: 2012-02-14
forum: Installation &amp; Upgrades
---

### Post by CJxD on 2012-02-14
It appears I can't boot into Ubuntu from either LiveCD or LiveUSB with any version of Ubuntu that I tried (11.04 and 11.10).
I can boot into a previously installed 11.04 version, but I wish to scrap that and start again.

The problem I get is during the first part of Ubuntu's boot (where it shows the Kernel status at time-marked intervals), it freezes at about 6 seconds, just after showing something along the lines of 'USB Root Hub' and '4 Ports detected'.

I can't exactly remember what, I'll give more details if you need them. Basically, I started getting this error since I upgraded my PC. I tried removing all USB devices, but I have a feeling it's an unsupported South Bridge or something.

PC:
Core i7 2600K Processor
Gigabyte GA-Z68X-UD5 (B3) Motherboard
4x 2GB Corsair PC3-12800 RAM

Only USB device I left in:
Logitech G510 Keyboard

Help?

---

### Post by varunendra on 2012-02-16
Did you try various [boot options]("https://help.ubuntu.com/community/BootOptions") available on the Live CD? Is it the same Live CD that you used to install 11.04 earlier? If so, I doubt a BIOS change or a broken/loose add-on card or a problem with HDD (the process stopping at USB detection maybe a red herring, but also try disabling USB3 in BIOS anyway).

If none of the boot options help, try booting with live cd with minimum hardware attached (i.e., no HDD, no add-on cards, and single RAM module in DIMM1). This is obviously not a solution, but may help pin-pointing the cause.

---

### Post by CJxD on 2012-02-17
I just tried these extra boot options. None of them made much of a difference. It still freezes.

You were right about USB being a red herring, this time it froze just after mounting a USB stick as sdc.

If I can't install Ubuntu on my computer, I'll actually put Windows on our remote server and program the scripts in Batch instead. =[

---

### Post by oldfred on 2012-02-17
There are several threads on Sandy Bridge issues. I prefer to search forum with google.

using google is often better than the forums search function.
Just append site:ubuntuforums.org to your search terms.
or
[http://www.googlubuntu.com/](http://www.googlubuntu.com/)

Are you in BIOS/MBR or UEFI/gpt modes? I think in either case it is better to partition in advance. If not using Windows I prefer gpt with BIOS also. My older system boots with BIOS from gpt formated drives without issue.

Not Gigabyte but other Sandy Bridge systems.
dual boot efi windows and efi linux 
[http://ubuntuforums.org/showthread.php?t=1890048](http://ubuntuforums.org/showthread.php?t=1890048)
[SOLVED] UEFI Boot Problems 
quiet splash vt.handoff=7 rootdelay=90 reboot=a,w
[http://ubuntuforums.org/showthread.php?t=1857639](http://ubuntuforums.org/showthread.php?t=1857639)
MSI UEFI bug work around A75MA-G55 UEFI boot entries disappear 
[http://forum-en.msi.com/index.php?topic=153411.0](http://forum-en.msi.com/index.php?topic=153411.0)
[SOLVED] Win 7, Natty dual boot on UEFI sort of working 
[http://ubuntuforums.org/showthread.php?t=1753717](http://ubuntuforums.org/showthread.php?t=1753717)

Grub2 efi info ArchLinux - Arch but grub2 is grub2 with maybe minor differences by distribution
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

---

### Post by CJxD on 2012-02-25
Okay, eventually I tried again. I turned off EFI boot for removable media, and it still freezes. Most of the information the links provide is not applicable as it deals with booting Ubuntu once it's already installed.

I can boot a pre-installed Ubuntu, I just can't boot any installation media.

---

