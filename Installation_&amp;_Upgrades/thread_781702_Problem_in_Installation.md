---
title: "Problem in Installation"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by mmad on 2008-05-04
At the moment, im running a 32-bit version of Windows XP on my computer, which has a AMD Athlon 64 X2 processor. Every site says that my processor is compatible with BOTH 32bit and 64bit OS's.

My old computer and my laptop (both using Intel processors) can handle the standard disc (Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM)) but this computer cannot. I was intending to try the 64-bit version but then I came across this post: 

[http://ubuntuforums.org/showthread.php?t=764011](http://ubuntuforums.org/showthread.php?t=764011) which seems to say that, it wont work either.

This is the error message:
```

[     0.480000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[     0.480000] Kernel panic - not syncing: IO-APIC + timer doesn't work! 

Boot with apic=debug and sens a report. Then try booting with the 'noapic' option
```

Video:
[http://www.youtube.com/watch?v=FwgjNGLJ6FQ](http://www.youtube.com/watch?v=FwgjNGLJ6FQ)

EDIT:
By the way, I've tried the other options too

---

### Post by Pumalite on 2008-05-04
I have no idea if it will work or not, but you can knock yourself out with these:
[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1)
[http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html](http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
[http://www.knoppix.net/wiki/Kernel-parameters-2.6.11](http://www.knoppix.net/wiki/Kernel-parameters-2.6.11)
noapic nolapic acpi=off pci=noacpi irqpoll pnpbios=off vga=0x317

---

### Post by mmad on 2008-05-04
> **Pumalite said:**
> I have no idea if it will work or not, but you can knock yourself out with these:
[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1)
[http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html](http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
[http://www.knoppix.net/wiki/Kernel-parameters-2.6.11](http://www.knoppix.net/wiki/Kernel-parameters-2.6.11)
noapic nolapic acpi=off pci=noacpi irqpoll pnpbios=off vga=0x317

Ill look over these, hopefully it'll sort out my problem =)

---

### Post by Pumalite on 2008-05-04
Good luck.

---

