---
title: "Installation stalls on Asus A6R laptop (Celeron M, ATI 200m)"
date: 2006-08-11
forum: Installation &amp; Upgrades
---

### Post by kessler on 2006-08-11
I have some trouble installing kubuntu 6.06 on a Asus A6R laptop. It doesnt seem to matter if i select normal installation, or safe graphics mode, it stalls the same place : "Uncompressing linux... Ok, booting the kernel"

I tried removing 'quiet splash' from boot options, and adding 'noacpi' which resulted in the installation stalling at :

Using HPET for base-timer
Using HPET for gettimeofday
Detected 1600.312 MHz processor.
Using hpet for high-res timesource

Anyone know what could be causing this?
Thanks in advance.

---

### Post by kessler on 2006-08-11
Apparently (k)ubuntu uses the boot option 'acpi=off' and not 'noacpi' to disable acpi. The installation has now finished booting up, i'll now proceed to install the system.

---

### Post by mario_7 on 2006-09-10
You have to configure kernel by yourself to have acpi with your laptop and Ubuntu :) I know something about that :P

---

