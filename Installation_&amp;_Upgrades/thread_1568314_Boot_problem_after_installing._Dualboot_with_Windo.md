---
title: "Boot problem after installing. Dualboot with Windows 7."
date: 2010-09-05
forum: Installation &amp; Upgrades
---

### Post by fn00dle on 2010-09-05
Hi all. :)

I bought a new laptop yesterday and after installing and configging Windows 7 I wanted to install Ubuntu on it as dualboot. First I tried the regular 10.04 Live CD, but with that one it wouldn't load into the menu. Then I tried the 10.10 beta CD, with which I was able to use and install Ubuntu. Only this live CD appeared to not install grub so I went straight into Windows again. I booted into windows, cleared the Ubuntu partition and downloaded the 10.04 alternate CD and successfully installed Ubuntu from there, GRUB also successfully installed. When trying to boot the normal ubuntu I get to the _ thingy flashing at the top right, and then nothing happens. When I try to boot in recovery mode it get's stuck after two seconds saying: 
[1.3964512] atkbd.c: Spurious ACK on isa0060/serio0, Some program might be trying access hardware directly.

I can't boot in Ubuntu in any way. I googled the error and I turned up with some people having the same error message after booting and having problems with their touchpad, though none of the solutions worked for me. :(

Hardware:
Medion Akoya E5217 (MD 97531)
4GB DDR2 RAM
Intel Pentium Processor T4500 2.2Ghz
640GB Sata hdd

Hoping to have a reaction! :)

---

### Post by dino99 on 2010-09-05
when you see the grub menu, select the ubuntu boot line and edit it (E), then:

- remove quiet splash, to see all the comments when booting, that way you can know about the issues

- add one or few of these keywords on the boot line: irqpoll, nomodeset, noacpi, nolapic, noapic

then boot ( ctrl+x )

is it a 32 or 64 bits installation ? ( less issue with 32 bits, then install with synaptic the pae-kernel to use all your ram like 64 bits do)

---

### Post by fn00dle on 2010-09-05
I removed quiete splash and tried with 'nomodeset' and the whole set of options, but both tries resulted in the laptop booting till after the point of error last time, but resulted in a screen with some white stripes and colored blocks. I'll add a screenshot below for the error shown without quite splash and without any further options.

[http://junk.centravi.org/laptop_trouble/error.jpg](http://junk.centravi.org/laptop_trouble/error.jpg)

---

### Post by Rubi1200 on 2010-09-05
What graphics card do you have installed?

---

