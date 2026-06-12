---
title: "apic=debug and noapic"
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by money2themax on 2007-12-19
what is apic?

i updated using the update thing that shows up when ever an update is needed and i restarted my PC and it tried to start but stoped and told me to start once with apic=debug then to start up using noapic no apic made it start but i have noidea what that for or what it stopped.

---

### Post by Pumalite on 2007-12-19
[http://en.wikipedia.org/wiki/Advanced_Programmable_Interrupt_Controller](http://en.wikipedia.org/wiki/Advanced_Programmable_Interrupt_Controller)

---

### Post by fs3rp4 on 2007-12-20
Why so many problems with Linux and this funcionality.

---

### Post by Pumalite on 2007-12-20
The problem is not Linux. The problem is hardware that does not support Linux and is oriented to Micro&%$ instead.

---

### Post by fs3rp4 on 2007-12-20
Well. I agree wth you If we talk about a wireless, or HD sound  driver. They don't support Linux.  But the apic look like more a BIOS implementation than a driver.

Quote "The Intel APIC Architecture is a system of Advanced Programmable Interrupt Controllers (APICs) designed by Intel for use in Symmetric Multi-Processor (SMP) computer systems. It was originally implemented by the Intel 82093AA and 82489DX, and is found in most x86 SMP motherboards. It is one of several attempts to solve interrupt routing efficiency issues in multiprocessor computer systems."

---

### Post by Pumalite on 2007-12-20
How do you explain that this is a problem in some motherboards only?

---

### Post by igknighted on 2007-12-20
> **fs3rp4 said:**
> Well. I agree wth you If we talk about a wireless, or HD sound  driver. They don't support Linux.  But the apic look like more a BIOS implementation than a driver.

Quote "The Intel APIC Architecture is a system of Advanced Programmable Interrupt Controllers (APICs) designed by Intel for use in Symmetric Multi-Processor (SMP) computer systems. It was originally implemented by the Intel 82093AA and 82489DX, and is found in most x86 SMP motherboards. It is one of several attempts to solve interrupt routing efficiency issues in multiprocessor computer systems."

You still need full disclosure about the implementation in order to interface properly with it in linux.

---

### Post by money2themax on 2007-12-20
i'll give you my specs

[http://h10025.www1.hp.com/ewfrf/wc/genericDocument?docname=c00679523&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN](http://h10025.www1.hp.com/ewfrf/wc/genericDocument?docname=c00679523&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN)

+ a 30GB HDD in addition to the 200GB
+ a 2nd Ethernet PCI card from HP [i think]
+ an old 1.1 USB [2 USB Ports] PCI card

---

### Post by igknighted on 2007-12-20
> **money2themax said:**
> i'll give you my specs

[http://h10025.www1.hp.com/ewfrf/wc/genericDocument?docname=c00679523&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN](http://h10025.www1.hp.com/ewfrf/wc/genericDocument?docname=c00679523&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN)

+ a 30GB HDD in addition to the 200GB
+ a 2nd Ethernet PCI card from HP [i think]
+ an old 1.1 USB [2 USB Ports] PCI card

I boot my Athlon64 system with the noapic command, and it doesn't seem to have disabled anything.  I can still read all the hardware sensors, I can still use CPU frequency throttling, etc.  I would just add it you menu.lst and forget about it.

---

### Post by Pumalite on 2007-12-20
+1

---

### Post by Kembo on 2007-12-20
A way to solve the APIC timer issue with Ubuntu on some motherboards.

Some motherboards have 2 different timers. They apparently do not seam to work well together when both are enabled and trying to run Ubuntu. At least this was the case with my XFX nForce 680i SLI motherboard. In addition to APIC timer it has something called a HPET Function (short for High Precision Event Timer) under the Advanced Chipset Features (Motherboard BIOS), disableing this will let Ubuntu use the APIC timer properly and not end up with a Kernel Panic. 

Hopefully this sollution might help other people experiencing NO APIC timer Kernel Panic.

Best regards
Kembo

---

### Post by money2themax on 2007-12-20
...what? I sorta computer savvy but you just when waaaaaaaaaaaaay over my head both of you and why does that guy keep +1ing?

---

### Post by money2themax on 2008-01-03
Ok everytime i boot up my computer i have to put in that noapic thing how do i make the permanent?

---

### Post by Pumalite on 2008-01-03
Read post # 11 again.

---

### Post by money2themax on 2008-01-03
umm...how do i get to that?

---

### Post by IeU on 2008-01-21
K,

i was running linux the past months without any problem, but then suddenly . . .

[IMG]http://img100.imageshack.us/img100/9018/g1xm9.jpg[/IMG]

why ?

i did not upgrade anything hard/software . . .

how come i start getting this out of nothing ?

Btw, i botted with apic=debug

where do i find the debug file ?

once in Linux, my network card does not work anymore

---

### Post by money2themax on 2008-01-21
i figured it out just go here [http://ubuntuforums.org/showthread.php?t=666072](http://ubuntuforums.org/showthread.php?t=666072)

---

### Post by IeU on 2008-01-24
i think i updated my bios, that is when my problems started :/

i dont want to reinstall everything again ;(

---

### Post by IeU on 2008-01-30
bump

---

