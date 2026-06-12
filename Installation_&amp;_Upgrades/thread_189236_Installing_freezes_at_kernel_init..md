---
title: "Installing freezes at kernel init."
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by saskboy on 2006-06-05
I have had no luck installing the [last 3 releases]("http://ubuntuforums.org/showthread.php?t=51909") of Ubuntu to my computer. All times the intall has failed early on, shortly after the boot options are entered; it stops responding after it says it's doing something like unpacking the kernel 

I've tried other linux distributions, and some of them have trouble too, so I know it's a hardware issue, but my machine works fine in Windows XP, so I think it's due to an incompatible part or two. Here are my parts off the top of my head, in case you have an idea which one(s) is causing this hanging.

Asus motherboard A7V8X , AMD 1800+ CPU
512MB RAM
DVD+- drive
3 IDE hard drives
on board sound, and NIC
ATI 8500DV Radeon AllInWonder TV
LCD 17" Daewoo monitor

I managed to enter a boot string last time with 5.10 to get the installation to stop locking up.
Now I don't remember that string, or it is no longer working, because I've tried the following:
noapic nolapic vga=771 debian-installer/framebuffer=false pci=noacpi
and nothing is working. Turrning off framebuffer shows me text instead of a graphical screen that freezes.

My hardware hasn't changed except for a new 160GB IDE drive.

The last line in the error message says:
4294669.993000 Kernel panic notsyncing VFS unable to mount fs ..... (8,1)

Thank you for any suggestions, feel free to email me,
Saskboy

---

### Post by nanotube on 2006-06-05
[QUOTE=saskboy]I have had no luck installing the [last 3 releases]("http://ubuntuforums.org/showthread.php?t=51909") of Ubuntu to my computer. All times the intall has failed early on, shortly after the boot options are entered; it stops responding after it says it's doing something like unpacking the kernel 

I've tried other linux distributions, and some of them have trouble too, so I know it's a hardware issue, but my machine works fine in Windows XP, so I think it's due to an incompatible part or two. Here are my parts off the top of my head, in case you have an idea which one(s) is causing this hanging.

Asus motherboard A7V8X , AMD 1800+ CPU
512MB RAM
DVD+- drive
3 IDE hard drives
on board sound, and NIC
ATI 8500DV Radeon AllInWonder TV
LCD 17" Daewoo monitor

I managed to enter a boot string last time with 5.10 to get the installation to stop locking up.
Now I don't remember that string, or it is no longer working, because I've tried the following:
noapic nolapic vga=771 debian-installer/framebuffer=false pci=noacpi
and nothing is working. Turrning off framebuffer shows me text instead of a graphical screen that freezes.

My hardware hasn't changed except for a new 160GB IDE drive.

The last line in the error message says:
4294669.993000 Kernel panic notsyncing VFS unable to mount fs ..... (8,1)

Thank you for any suggestions, feel free to email me,
Saskboy[/QUOTE]
try adding "acpi=off" to your boot string

---

### Post by saskboy on 2006-06-05
OK Nanotube, I'll try turning ACPI off too and let you know if that did it.

---

### Post by saskboy on 2006-06-06
I tried turning framebuffer, usb , and acpi off in the boot string, and it still hangs. I'll try running the disc check again but that was hanging too, or I didn't give it enough time maybe.

---

### Post by darrenrxm on 2006-06-08
Saskboy,

GRUB hangs if tv is connected.

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards)

---

### Post by saskboy on 2006-06-08
Thanks for the try Darren, but the coax isn't plugged in. I do have the cable block plugged in though...

---

