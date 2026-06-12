---
title: "Installation Problem"
date: 2006-07-24
forum: Installation &amp; Upgrades
---

### Post by Tarq on 2006-07-24
Hi,

I've just received my installation CD and put it into an old Windows 98 PC at work, encountering the following problem:

CD Starts

Ubuntu screen appears

Selected Start or Install

Uncompressing Linux... Ok, booting the kernel.
[4294667.296000 ] ACPI: Unable to locate RSDP
[     71.866400 ] isapnp: unexpected or unknown tag type 0xff for logical device 3 (device 1), ignored
[     76.153490 ] isapnp: checksum for device 1 is not valid (0xad)

What should I do?

Many thanks for any replies!
Tarq

---

### Post by zxee on 2006-07-24
Do you have a ISA sound card in that computer? Searching the last two lines of output you provided provided hits about ISA sound cards which weren't compatible/had no linux drivers...[http://www.linuxforums.org/forum/debian-linux-help/48459-als100-isa-sound-card.html](http://www.linuxforums.org/forum/debian-linux-help/48459-als100-isa-sound-card.html)
You might want to provide more of the computer's hardware details-specifications.
If this is a very old machine and also has less than 128MB RAM it probably won't work with the latest version(s) of ubuntu.

---

