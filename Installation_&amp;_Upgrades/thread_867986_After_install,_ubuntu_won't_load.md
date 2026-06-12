---
title: "After install, ubuntu won't load"
date: 2008-07-23
forum: Installation &amp; Upgrades
---

### Post by Berethend on 2008-07-23
After I installed the 64 bit version of Ubuntu 8.04 it tells me to remove the CD and restart, which I do. Upon startup, because I'm dual booting, it asks me to choose which OS I'd like to start. I choose Ubuntu (something else here) -generic, and it begins to boot. It stays on the Ubuntu loading screen for about 3 minutes or so and then goes to a screen that says (or what I remember) Bushybox v1.1.1.3 (some other text here) and under all of that it says "initramfs." It stays on this screen indefinitely and I can't get passed it. Please pardon my ignorance with Linux, I hope to learn. 

I read somewhere else that I should remove the line "quiet" from the bootup options, which I tried, but the same problem still occurred. I have reinstalled and still to no avail.

---

### Post by LeevS on 2008-07-23
I have the same problem, the only way i can get it to load is to press escape to go to the menu and use the recovery mode. then chose to resume normal boot.

---

### Post by Berethend on 2008-07-23
I tried booting into recovery mode but I still get the same problem. Maybe someone can shed some light on this problem?

---

### Post by LeevS on 2008-07-23
did u repair broken packages?

---

### Post by Berethend on 2008-07-23
How would I do that?

---

### Post by LeevS on 2008-07-23
it was one of the options on the recovery mode for me, fist one i think

---

### Post by Berethend on 2008-07-23
Ahh well I can't even boot to the recovery. I get the same message of "initramfs" and then it stops right there.

---

### Post by avtolle on 2008-07-23
Take a look at [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) and try the boot options given, first individually and then combining them. One boot option not listed is all_generic_ide, which may or may not help, but give it a try, too. Good luck.

---

### Post by R.C. on 2008-07-23
This Busybox prompt problem is an ongoing issue. I don't know whether Canonical, or whomever, has yet declared it to be a "known" issue or assigned a time for fixing it, but it is certainly something that lots of people are experiencing.

In my case, it happens when I try to use the Live CD. I've tried several combinations of startup options, to no avail.

I just wish someone would work out a diagnostic process that would allow us to know WHAT exactly is causing the boot process to "fail out" and land at the Busybox prompt.

If we knew WHERE in the process the error was happening, we might be able to figure out exactly which set of startup options will fix it.

WITHOUT that, people are just suggesting random collections of startup options for no apparent reason.

I've seen them suggest:

vga=791
vga=789
vga=788
vga=0x317
pnpbios=off
pci=nomsi
pci=noacpi
acpi=off
noapic
nolapic
floppy=off
irqpoll
all_generic_ide

...and hitting the F4 key to do some kind of compatibility something or other.

Sometimes they say, "try two or three of these options in combination." Well, gee. If I try two in combination until I try all the possible combinations, that's forty-five or so combinations, with each one taking 5 minutes or so: FOUR HOURS of nothing but rebooting and trying another combination.

Fellas, is there no way to diagnostically narrow down the number of options we should try?!

---

