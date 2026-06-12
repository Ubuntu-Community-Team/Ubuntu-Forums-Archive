---
title: "Unable to boot: A2811201: ACPI: Unable to load system description"
date: 2008-10-12
forum: Installation &amp; Upgrades
---

### Post by Kevin Jones on 2008-10-12
Hello all,

I recently tried to upgrade to I.I. 8.10. I have an oldish HP pavillion pc
After installing the 8.10 I tried to reboot. I got an error:
A2811201 ACPI: Unable to load system description tables.
I have tried to re-install 8.04, as well as burning a knoppix dvd to see if  that would  work
I now have 8.04 installed with  no  other operating system. After the grub loads I get the:
A 02811201 ACPI: unable to load system description tables.
Then a blank 'greenish' ubuntu like screen.
I have checked about...
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=715344](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=715344)
[http://www.undergroundsystems.org/forums/showthread.php?t=3720](http://www.undergroundsystems.org/forums/showthread.php?t=3720)
seem to have simialar issues, but I don't think the solutions will work. I looked at the bios menu and I can't see any power management settings, other than 'do you want to restart automatically after power failure? This is set to  NO

Any   help would really be appreciated

Kevin Jones

---

### Post by jonathanmotes on 2008-11-02
Try "live acpi=off noacpi" (minus the quotes) if you are using a live disc, "linux acpi=off noacpi" if it is already installed. (it worked for me on an older Compaq Presario for 8.04 - doesn't seem to work for 8.10 though). 

If that doesn't work you can try a cd with a text-based installer (the alternate disc). 

Hope this helps!

---

