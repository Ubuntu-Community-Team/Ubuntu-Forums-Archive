---
title: "Booting ubuntu 13.04 on live usb: xorg error"
date: 2013-05-28
forum: Installation &amp; Upgrades
---

### Post by jpcarlino on 2013-05-28
Hello,

I've bought a Samsung series 5 (np530u3c) preinstalled with W7. BIOS setup had already all the "new conflictive stuff" disabled (secure boot, uefi, fast boot, etc). I've created an usb bootable disk with Ubuntu 13.04 64-bit and was able to boot, however it crashed when starting xorg. To be more precise, i was able to see desktop for a few moments and then it showed a dialog window telling something went wrong, with the option to use low resolution mode. If i select low resolution mode nothing happens. I can switch to command line fine (CTRL + F1) see the live filesystem, etc.
I've seen ton of problems with this laptop ;) but none yet related with this specific issue.
I've attached an screenshot showing the log contents for xorg.

Any hints on this?

PS: i've also enabled uefi and this time it showed the grub menu to select options (live ubuntu, install, diagnose, etc) but i'm stuck on the same stage, so it doesn't seem to relate with any bios issue.

---

### Post by jpcarlino on 2013-05-29
I had to boot it using "nomodeset" kernel parameter. Although aspect ratio is not correct i can start gdm fine on live instance. I wonder if this is a known issue on kernel 3.8 and if i will be forced to use generic vesa drivers also after installation.

---

### Post by Bashing-om on 2013-05-29
[COLOR=#000000]jpcarlino; Hi ! Welcome to the forum .

You are making good progress. I do not have "unity's" desktop environment installed on my 13.04 so not able to be specific about where/how, but;
Boot your system using the "nomodeset" boot parameter option, get to the desktop and find the utility "Additional Drivers" and then install the recommended driver.

Should fix ya right up.[/COLOR][INDENT=2][COLOR=#000000]
just try'n to help

[/COLOR][/INDENT]

---

