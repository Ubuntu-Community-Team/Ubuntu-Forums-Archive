---
title: "Advantage of using &quot;686&quot; kernel ?"
date: 2006-03-13
forum: Installation &amp; Upgrades
---

### Post by Darkriser on 2006-03-13
The installation CD installs the "386" kernel, by default. As I have P4 (2.4GHz) CPU, I could be using the "686" kernel, instead (either downloading one from repositories or compiling my own one).
But the question is - is there any advantage for me using the "686" kernel over the default "386" one?

Thanx a lot...
Marcel

---

### Post by bjweeks on 2006-03-13
[QUOTE=Darkriser]The installation CD installs the "386" kernel, by default. As I have P4 (2.4GHz) CPU, I could be using the "686" kernel, instead (either downloading one from repositories or compiling my own one).
But the question is - is there any advantage for me using the "686" kernel over the default "386" one?

Thanx a lot...
Marcel[/QUOTE]

It is slightly faster, otherwise no.

---

### Post by lordofkhemenu on 2006-03-13
[quote=bjweeks]It is slightly faster, otherwise no.[/quote]
Also, I think you'd only notice a noticable difference if you used debs that were compiled for 686 as well (AFAIK, all the ubuntu debs are 386 by default).

---

### Post by cotcot on 2006-03-13
I have installed the 686 because it was needed to install the accelerator for my ATI Radeon graphics card. After that I could use flightgear at a good speed.

---

### Post by knalle on 2006-03-13
[QUOTE=bjweeks]It is slightly faster, otherwise no.[/QUOTE]

yeah, i think the main difference between the 386 and 686 build is that it is compiled with MMX and SSL1/SSL2 -o flags

---

