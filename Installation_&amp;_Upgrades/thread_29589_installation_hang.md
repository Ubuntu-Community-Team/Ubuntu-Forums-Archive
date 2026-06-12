---
title: "installation hang"
date: 2005-04-25
forum: Installation &amp; Upgrades
---

### Post by pablo.aimar on 2005-04-25
i try to install hoary, when it comes to first boot, it hang when entering hotplug subsystem.

system : p4 2,2 Ghz, intel 810 chipset, intel vga onboard (disabled), nVidia GeForce 440 MX.

looking into /var/log/messages .. i found APM : bios not found

is that the problem ??
what is that ?

---

### Post by poofyhairguy on 2005-04-25
[QUOTE=pablo.aimar]i try to install hoary, when it comes to first boot, it hang when entering hotplug subsystem.

system : p4 2,2 Ghz, intel 810 chipset, intel vga onboard (disabled), nVidia GeForce 440 MX.

looking into /var/log/messages .. i found APM : bios not found

is that the problem ??
what is that ?[/QUOTE]


Seems like the power profiles are messing you up. I would try reinstalling with this command:

linux acpi=off apm=off

When the first screen comes up when you boot of the install CD, type that then hit enter instead of just hitting enter.

---

### Post by pablo.aimar on 2005-04-25
i've tried reinstalling with that command

linux acpi=off apm=off

then ... it stuck when entering USB section (not even entering installation system yet) :(
so i disabled USB (in BIOS)

it works, passing first phase of installation.
but when it comes to second phase (first boot), the old desease comes again ...

it freeze (again !) when entering hotplug subsytem.

so .. i tried another way, i enabled internal VGA so the nVidia card is disabled (of course)
i enable all MB features .. USB, etc ..

an then ... it works ... perfectly.

but i want to use that nVidia card, cause the internal intel VGA just sucks, eats my memory with no 3D features :( , but i can't .. it always stuck when entering hotplug subsytem :( (always) .. acpi=off, apm=off, usb disabled, not works at all.

please .. anyone can help me ? i'm so desperate to get my ubuntu on !

thx in advance

---

