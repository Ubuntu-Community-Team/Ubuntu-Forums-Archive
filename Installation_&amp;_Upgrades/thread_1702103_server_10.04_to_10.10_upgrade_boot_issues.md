---
title: "server 10.04 to 10.10 upgrade boot issues"
date: 2011-03-07
forum: Installation &amp; Upgrades
---

### Post by doulos564 on 2011-03-07
I have an old PC that I use as a LAMP development environment:
HP Pavillion
AMD Athlon 850
RAM 370 Mb
Vanta/Vanta LT Graphis

I did a network upgrade from 10.04 to 10.10.

I can boot into the Linux 2.6.32-28-generic kernel, and everything appears to work.

When I boot into Linux 2.6.35-25-generic or
                 Linus 2.6.35-27-generic

I get a blank screen with a blinking cursor in the upper left corner, and nothing else.

I've tried changing the boot parameters to remove quiet and splash.
I've also tried adding:
acpi=off, nomodeset, and i915.modeset=0

However, these have no effect on the 2.6.35 kernels.

I see nothing in /var/log/messages or /var/log/dmesg files except for those that appear related to the 2.6.28 kernel.

I do remember a previous version needed an option to disable a memory check on boot, but I can't find the documentation to try this again.

---

### Post by whiteman on 2011-03-07
> **doulos564 said:**
> I have an old PC that I use as a LAMP development environment:
HP Pavillion
AMD Athlon 850
RAM 370 Mb
Vanta/Vanta LT Graphis

I did a network upgrade from 10.04 to 10.10.

I can boot into the Linux 2.6.32-28-generic kernel, and everything appears to work.

When I boot into Linux 2.6.35-25-generic or
                 Linus 2.6.35-27-generic

I get a blank screen with a blinking cursor in the upper left corner, and nothing else.

I've tried changing the boot parameters to remove quiet and splash.
I've also tried adding:
acpi=off, nomodeset, and i915.modeset=0

However, these have no effect on the 2.6.35 kernels.

I see nothing in /var/log/messages or /var/log/dmesg files except for those that appear related to the 2.6.28 kernel.

I do remember a previous version needed an option to disable a memory check on boot, but I can't find the documentation to try this again.


I got the same thing when I installed 10.04. Nothing but  big blank screen. HAd to reinstall Jaunty. Id love to use ext4, but cant get it to recognize my printers.

---

