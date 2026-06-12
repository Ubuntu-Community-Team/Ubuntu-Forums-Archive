---
title: "Help with first boot: &quot;unknown interrupt or fault at eip XXXXXXXXX XXXXXXXXX&quot;"
date: 2006-11-17
forum: Installation &amp; Upgrades
---

### Post by aNt1X on 2006-11-17
I posted 1 day ago in another forum, but it seems that nobody can help me ](*,) ](*,) ](*,) 

I'm trying to install Ubuntu Server 6.10, standard installation with no LAMP and no DNS, on the following machines

GCT Allwell 3036N (Geode GX1 266 MHz + HD IBM Travelstar 3.25GB)
[http://www.gctglobal.com/Products/Se...1030_3036.html](http://www.gctglobal.com/Products/Se...1030_3036.html)

GCT Allwell STB6386N (VIA Eden X86 733 MHz + HD Samsung SP0802N 80GB)
[http://www.gctglobal.com/Products/Se.../stb6286n.html](http://www.gctglobal.com/Products/Se.../stb6286n.html)

During the installation no problems, all went ok.

After the first reboot, i got the
"Starting up..."
message, followed by a lot of
"unknown interrupt or fault at eip XXXXXXXXX XXXXXXXXX"
messages, followed by a reboot.
The XXXXXXXX codes changes after some second, and differs from the two machines.

I tried also booting with "acpi=off", but still have these reboots.
I tried also removing TV TUNER, but still have the problem.

What can i do? Any idea? How can i investigate the problem?

Thank a lot in advance,
aNt1X

---

### Post by tarvid on 2007-01-16
I am having the same problem with Edgy on an m10000 board. noapic, nolapic, acpi=off didn't work. Hammered all of the not required devices in the bios and a couple of other tweaks and I managed to get my machine to not post at all.](*,)

---

