---
title: "Problem with BIOS"
date: 2017-03-19
forum: Installation &amp; Upgrades
---

### Post by chiefchacka on 2017-03-19
I was trying to get xubuntu on my hp chromebook 11 g4 through a bootable flash drive, but I need to change my BIOS to SeaBIOS, and to do that I need to disable Write Protection, but every time I try to disable it I get this message: 

flashrom v0.9.4 : 65be03a : Nov 08 2016 10:51:57 UTC on Linux 3.10.18 (x86_64)
 flashrom v0.9.4 : 65be03a : Nov 08 2016 10:51:57 UTC on Linux 3.10.18 (x86_64)
 Mapping BYT IBASE at 0xfed08000, unaligned size 0x200.
 Mapping BYT SBASE at 0xfed01000, unaligned size 0x200.
 w25q_disable_writeprotect(): error=1.
 FAILED


Please help.

---

### Post by mörgæs on 2017-03-19
Hi, welcome to the fora.

Are you sure that you need a new Bios?

If you do and if you want to use Flashrom for the process then I suggest release 0.9.9

---

### Post by chiefchacka on 2017-03-19
How exactly would I get flashrom 0.9.9 on my chromebook and how would I use it?

---

### Post by RobGoss on 2017-03-20
Not sure if this is what you're looking for have a look here [https://www.flashrom.org/Downloads#Installation_from_source](https://www.flashrom.org/Downloads#Installation_from_source)

---

