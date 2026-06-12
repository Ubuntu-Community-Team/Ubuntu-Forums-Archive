---
title: "Lucid+Thinkpad X100e hangs on switch to battery"
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Andy Armstrong on 2010-03-23
I've just installed x86_64 Lucid on a Lenovo Thinkpad X100e. On mains power it works fine but when I either switch to battery or attempt to boot on battery it hangs.

I understand the general principle of ACPI but I'm unsure how to go about diagnosing the problem.

I guess the starting point would be to completely disable everything that happens when the power state changes and verify that it doesn't then hang.

I'm not going to file a bug until I've characterized the problem - but some help with how to get started with an investigation would be greatly appreciated.

---

### Post by mariomm on 2010-03-23
Hi,

have the same issue on HP 6735b - cant figure out wat is causing the crash - 

also tried nolapic noapic noacpi and nosmp - does not change anything

i have seen some errors on gnome power management in launchpad - where they say that the battery isn't detectet - but i dont thinkt that the machine wont to suspend - and cat /proc/acpi/battery/BAT0 is recognized correctly

i have no idea how to find out what is causing the problem - maybe anyone can help here

iam using 10.04 beta 1 latest kernel (Linux map-noapple 2.6.32-17-generic #26-Ubuntu SMP Sat Mar 20 02:23:45 UTC 2010 x86_64 GNU/Linux)

by the way - this also effects the "recovery" Bootmode...

greetings from vienna,AT

Mario

---

### Post by mariomm on 2010-03-24
tried to post a bug on launchpad - maybe we will find some help

[https://bugs.launchpad.net/ubuntu/+bug/545508](https://bugs.launchpad.net/ubuntu/+bug/545508)

---

### Post by Andy Armstrong on 2010-03-24
Another data point: if I stop acpid before switching to battery the machine still hangs when I do.

Would I be correct to assume that this means it's not a userspace problem?

---

### Post by mariomm on 2010-03-24
i guess that this issue is not a userspace problem but maybe you can post some more informations

is your 10.04 a clean install or an upgrade from 9.10 ?
maybe you can post your "lspci" output here - or directly on [https://bugs.launchpad.net/ubuntu/+bug/545508](https://bugs.launchpad.net/ubuntu/+bug/545508)

mine is an upgrade - and iam updating abaout 3 times a day , hopefully expecting a silent fix *g*

---

### Post by morsel on 2010-03-30
ehlo

having the same problem on my x100e. disabling acpi on boot time doesn't help.
changing the display brightness freezes my system as well.

didn't go through all the launchpad posts, but figured something's wrong with the thinkpad-acpi module (not yet supported thinkpad detected ...)

I'm hoping for an update on thinkpad-acpi module as seen here:
[http://sourceforge.net/mailarchive/forum.php?thread_name=20100316230950.GA30415%40khazad-dum.debian.net&forum_name=ibm-acpi-devel](http://sourceforge.net/mailarchive/forum.php?thread_name=20100316230950.GA30415%40khazad-dum.debian.net&forum_name=ibm-acpi-devel)

don't know if this fixes the battery bug though, but should help with enabling the bluetooth adapter and possibly the integrated wwan and camera...

---

### Post by zobbo on 2010-04-22
Last night, having upgraded to the latest X100E bios and using the fglrx drivers for display, I was able to overcome this issue, using the Lucid Beta 2 release. Both 32bit and 64 bit working

Everything seems to be working well and I am not tied to the power supply any more!

See also last comments at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/535653?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/535653?comments=all)

---

