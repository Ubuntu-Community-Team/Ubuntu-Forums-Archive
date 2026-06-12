---
title: "RSDP prob, followed by blinking keyboard"
date: 2007-09-10
forum: Installation &amp; Upgrades
---

### Post by SunEdison on 2007-09-10
I am a fairly techie user but new to Ubuntu. Just downloaded 7.04 and trying to boot from the ISO image CD on a Pentium 233 MHz MMX machine with 256 MB RAM, Windows 98 SE. Here is what I am seeing when I try to install Ubuntu with dual boot option.

1) Changed BIOS setting to include "boot from CD"
2) Boot the machine
3) Chose "Start or Install Ubuntu" option on the opening screen
4) Got [   0.0000...] ACPI: Unable to locate RSDP. It seemed stuck but after hesitation proceeds with the dancing orange progress bar for a bit.
5) Machine freezes - The Orange Progress bar stops and the keyboard Caps lock and Scroll lock LEDs flash together.
6) Nothing happens.

I have read through some of the RSDP error resolutions on ACPI but did not make any difference in my situation. I am trying to download the "Alternate" CD to see if that makes a difference.

Any suggestions to get past the "blinking keyboard" problem so it boots and I can install Ubuntu in a dual boot mode?

Thanks a lot.

---

### Post by Pumalite on 2007-09-10
Let's see what happens with the Alternate CD first.

---

### Post by SunEdison on 2007-09-10
Hi Pumalite

On the Alternate CD I got the the ACPI: Unable to locate RSDP as well and just like with the regular Ubuntu, the system proceeded to install (past language and keyboard selection) but eventually froze with the blue screen and flashing caps lock and scroll lock LEDs.

Any suggestions? Do you think it is a keyboard problem?

Thanks for your help.

---

### Post by Pumalite on 2007-09-10
Let me research it. I have to go for now but I'll be back.

---

### Post by Pumalite on 2007-09-10
This is the best thread I could come up with. There are several fixes proposed. I hope one of them work for you: [http://ubuntuforums.org/showthread.php?t=189190](http://ubuntuforums.org/showthread.php?t=189190)

---

### Post by SunEdison on 2007-09-11
Thanks Pumalite. 

I tried most of the stuff discussed on the forums but so far no luck. The system freezes while booting from the CD. I think the system is actually able to go past the ACPI:Unable to locate RSDP error because it does not get stuck there but there after.

My machine/bios (Phoenix BIOS 4)  may be too old to support Ubuntu. Oh well. I was so excited about Ubuntu when I got started.

Any one else have any other suggestions?

---

### Post by Pumalite on 2007-09-11
See if you can update your BIOS.

---

### Post by sivadbp on 2007-10-12
I ran into the same blinking capslock and scrollock lights during installation.  

What worked for me was disabling acpi in the bios.

---

### Post by theJagger on 2008-03-18
I had no way to change the power management (acpi) settings in my bios on a hp e800.
when booting the install disk i hit F6  (for more boot options) and removed:
> quiet splash --
and added:
> noacpi nolacpi acpi=off
to the end of the boot command

---

