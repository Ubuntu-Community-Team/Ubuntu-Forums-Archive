---
title: "cannot boot from USB just blank screen and no GRUB"
date: 2014-11-13
forum: Installation &amp; Upgrades
---

### Post by beavermml on 2014-11-13
i have acer TM8473T and i want to install fresh ubuntu on it..

but i cannot even get any display ( no GRUB etc ) after booting from USB.. i know it did boot from USB because the "Booting in insecure mode" shows up.. but after that, just blank screen.. 

i suspect after that is the GRUB menu because if i press enter, the laptop seems to be booting the ubuntu ( fans begin faster, cannot shutdown immediatly by pressing on button ) but no drum sound.
 
i have tested the USB with other PC and the USB work fine..


this is not the first time i used ubuntu but i never face this kind of problem before, usually problems came after booting it ( weird display, drivers etc )

---

### Post by grahammechanical on 2014-11-13
Grub is not used on a Ubuntu live session. What other operating system is there installed on this machine and what version of Ubuntu have you burnt to the USB memory stick?

Regards.

---

### Post by beavermml on 2014-11-13
i have installed win8.1 on this laptop.. and i have use 14.10 ISO.. i use the rufus program to make a bootable USB..

the USB works with my PC but with this laptop.. it just blank screen after "Booting in insecure mode"..

---

### Post by beavermml on 2014-11-13
i guess there is something wrong with syslinux/isolinux..

---

### Post by ubfan1 on 2014-11-13
Rufus has lots of options, which can be incompatible with UEFI booting.  I have no experience with it myself, but it does more than you'd need for creating a bootable USB from an ISO.  A UEFI boot will actually use grub (a BIOS boot will use syslinux), and the minimum setup for the USB should be a FAT32 filesystem, a /EFI/Boot directory containing bootx64.efi.  Without that, the USB won't boot UEFI.  Is your pc UEFI too?  Probably not if the stick boots.

---

### Post by beavermml on 2014-11-13
i know that.. i can boot the USB drive both using UEFI and BIOS mode in my PC.. ( my PC will detect 2 USB drive, UEFI: and just USB: ) but my laptop only detect one.. so i think it just boot BIOS mode.

i have tried to boot other distro and they get stuck at "initializing gfx code" in syslinux..

---

### Post by beavermml on 2014-11-13
just tested the elementaryOS 0.2 Luna and it boots just fine  albeit with gfx glitch at the syslinux menu ( try / install etc )..

---

### Post by beavermml on 2014-11-14
i still cant install eOS 0.2 through the live cd.. freeze at "grub-install dummy".. i guess this is the UEFI part..

---

### Post by beavermml on 2014-11-14
i have managed to boot GRUB from the ubuntu 14.10 usb.. 

but i cant boot ubuntu even with "nomodeset, nolapic, etc " mode.
i have tried the "no splash" option
and the last line is
EFI variables facility ..

---

### Post by ubfan1 on 2014-11-14
Here's some more options to try:
For UEFI machines (with a black screen grub (grub-efi)  without any
function key options, like the older grub-pc, edit the grub menu and add
the below options on the "linux" line, then boot with F10 or ctrl-X.


Options for Video problems:

nomodeset
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic

Older Intel video card:
i915.modeset=1 or i915.modeset=0
newer:
i915.i915_enable_rc6=1

video=1280x1024-24@60
video=VGA-1:1280x1024-24@60

To allow Nvidia hybrid machines to boot.
nouveau.blacklist=1

To slow SSDs to allow them to boot:
libata.force=noncq

---

### Post by beavermml on 2014-11-14
ok.. i have managed to "fool" my laptop..

it turns out that this laptop UEFI implementation is so buggy.. i even have difficulties in installing win8.1 in UEFI mode.. ( i never thought that before this, i used the legacy mode to install win8.1 )..

my solution is, after creating the liveCD USB, i just delete the EFI folder in the USB.. this force my laptop to boot ISOlinux instead of grub.. and after that, i can install elementary OS without any problem ( no more grub-install failed )..

---

