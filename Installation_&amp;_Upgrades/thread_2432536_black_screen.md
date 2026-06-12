---
title: "black screen"
date: 2019-12-04
forum: Installation &amp; Upgrades
---

### Post by gabyarcade on 2019-12-04
Hello, I am new to all this and I have tried to install ubuntu version 16, and it has installed everything to the point of the warning that tells me to restart the system, I press the button and at the time of rebooting then this black screen comes out and there is no option no problem. I do not know what to do,
I add that I have done it through a USB.
Thank you for your help and I hope you have a solution

---

### Post by mörgæs on 2019-12-04
Hi, welcome to the fora.
Which hardware are you using?

---

### Post by gabyarcade on 2019-12-04
[FONT=arial]it is a celeron 430 1.8ghz processor, 4 gb of ram, 80gb hardisk ide[/FONT]
[FONT=arial]it is a celeron 430 1.8ghz processor, 4 gb of ram, 80gb hardisk ide[/FONT]

---

### Post by Impavidus on 2019-12-05
The important thing to know is the graphics hardware.

BTW, any particular reason to install 16.04 LTS (I assume that's the one you installed)? Because 18.04 LTS is solid too, more up to date and has longer support left. In the Linux world, if you've got old hardware, you don't use an old release, but use a light flavour.

---

### Post by gabyarcade on 2019-12-05
[FONT=arial]I tried with 16 for the requirements of my pc they allowed me to have only a graphic board, on the motherboard[/FONT]

---

### Post by gabyarcade on 2019-12-05
Minimum system requirements for Ubuntu 18.04 LTS (desktop)
2 GB of RAM
Dual Core Processor (2 GH)
25 GB of free hard disk space. my pc is only 1.8gh

---

### Post by guiverc on 2019-12-06
I tested Lubuntu (and Xubuntu) up to 19.04 using pentium M laptops & pentium 4 desktops (mostly single core, ~2003 with ram as little as 1GB).  As @Impavadis said, a lighter flavor (or really lighter desktop on same base) and still use Lubuntu 18.04 LTS on a thinkpad t43 (1.5gb ram)).

I don't see how *onboard* graphics has any bearing on release of Ubuntu, as most systems I test with also use onboard graphics. Your celeron 430 (2007) is a number of years later than some of the systems I test Ubuntu (x86) and flavors with, and maybe ~two years older than the system I'm using to type this.

Boot the 'live' (your install media) and `sudo lshw -C video` (which means *list hardware of class=video*) may provide some clues.

---

