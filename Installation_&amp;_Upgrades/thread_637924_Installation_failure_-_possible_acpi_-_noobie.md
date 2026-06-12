---
title: "Installation failure - possible acpi - noobie"
date: 2007-12-11
forum: Installation &amp; Upgrades
---

### Post by High_Yield on 2007-12-11
Hi-

I'm a linux newbie installing the "latest" (7.1?) version of ubuntu desktop.
The machine is:
- Matsonic 7016s motherboard socket 478
- Celeron 400
- AMI bios
- Voodoo 3 graphics card (heh yes - 3dfx)
- ~329 meg of RAM

I've tried to no avail:
-  both the default install and the secondary safe graphics option to no avail.
- turning power options on and off in the bios
- installing another linux called Mepis with similar issues
- removing all devices but the hard disk
- using 2 different hard disks

The first issue of note after kernal load 100% is a note the install gives me stating "[0.0000] No DMI BIOS year.  acpi=force is required to enable acpi"
Unfortunatley, I do not really want ANY power options on - I want to keep this VERY simple.

Then the install simply continues, perhpas forever, but I always interrupt it after many, many error messages.

I see the ubuntu logo with install bars, then a nice pink screen with a mouse cursor that works when I move the mouse.  It then thinks for awhile and the screen goes to black with white text and system logs and errors being reported.
The first error of note I see is something like "Error inserting battery  : Battery.ko : No such device"

From there I get many other errors, like "error reading device sr0" etc...

ANY help is appreciated - thanks - B

---

### Post by djdnc on 2007-12-14
I get the same thing on the battery and on the acpi, maybe someone can help.

---

### Post by rfruth on 2007-12-14
On my mini-tower had to set "S3" not S1 (the default) in the BIOS (under power conservation)

---

