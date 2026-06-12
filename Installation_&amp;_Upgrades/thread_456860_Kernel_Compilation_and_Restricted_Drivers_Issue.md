---
title: "Kernel Compilation and Restricted Drivers Issue"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by sertansenturk on 2007-05-28
Hi there,

I'm using Ubuntu Feisty 7.04 i386 architecture. I also enabled Ubuntu Studio repositories to benefit from music apps.

My computer has a hardware issue to randomly recognize my mainboard soundcard and Creative soundcard. I want my Creative soundcard to be recognized.

My hardware components are:
AMD Athlon 64 3000+ Processor
Creative SB Audigy 2 ZS
Asus A8V Mainboard

I have previously dealt with the problem by compiling my own kernel and removing all the modules except Creative's.

But after compilation I have to install Nvidia restricted modules and now newer kernels need SATA modules manually enabled, which I ,frankly, need some guidance.

I want to compile latest of two kernels: generic and lowlatency (from Ubuntu Studio). I believe 2.6.20.16.28.1's are in the latest in the Ubuntu official repositories. I'm using 2.6.20.15.14-generic (which has the soundcard recognition problem) and the same version of the lowlatency kernel (which is not booting due to Nvidia restricted modules are not manually installed but should have the sound problem if it were to boot)

I would also appreciate help on compilation (a ubuntu patch maybe), a link to a good how-to to remember kernel compilation or any friendly advice on the process.

Thanks in advance,
Sertan

---

