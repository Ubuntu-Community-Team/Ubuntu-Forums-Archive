---
title: "More Customized / Optimized Install"
date: 2008-08-09
forum: Installation &amp; Upgrades
---

### Post by dethredic on 2008-08-09
So about six months ago I started duel booting Ubuntu and Vista. I have been using Ubuntu as my default OS and Vista for gaming and benching.

Six months ago was my first experience and I have enjoyed it immensely (Compiz, Synaptic Package Manager and Amarok mainly). I would say I have done experimenting with it, but nothing major.

So lately some of my messing around and the upgrade from 7.1 to 8.4 have given me some troubles, so I have decided to reinstall.

First off, I have a Intel E6420, 8800GTS and an Asus P5N32-E, and 4gigs for ram. Because I have the 4 gigs of ram I am not sure wither I should go 64bit or not. I remember people were having problems with flash before, I am not sure if that is still the case. Are there any other major problems I might run into, or should I just play it safe and go 32bit, as I am more worried about stability than speed.

Also, are there ways to optimize the kernel for my specific hardware to improve boot times and stability?

Anything else I can do to improve this install?

EDIT: Are any of [these ]("http://news.softpedia.com/news/Optimize-Ubuntu-Feisty-Fawn-for-Speed-53836.shtml")tweaks worth doing?

---

### Post by kerry_s on 2008-08-09
> Also, are there ways to optimize the kernel for my specific hardware to improve boot times and stability?

use the right kernel, not generic. you can try building a custom kernel.

> Anything else I can do to improve this install?

try a faster distro, ubuntu is not really built for speed. i recommend debian or arch, if you want top of the line control, then gentoo.


try debian, you can install the 32bit, but after install, grab the big-mem kernel.(see pic, i'm only using etch, but there's one in lenny to)

etch net install:
[http://cdimage.debian.org/debian-cd/4.0_r4a/i386/iso-cd/debian-40r4a-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r4a/i386/iso-cd/debian-40r4a-i386-businesscard.iso)

lenny net install:
[http://cdimage.debian.org/cdimage/lenny_di_beta2/i386/iso-cd/debian-LennyBeta2-i386-businesscard.iso](http://cdimage.debian.org/cdimage/lenny_di_beta2/i386/iso-cd/debian-LennyBeta2-i386-businesscard.iso)


i've had a few problems going with straight lenny, i prefer to go etch, then add the lenny repos and upgrade, the choice is yours. i'm running a etch install on the desktop, cause i don't use it that much so i want it to be stable.

---

### Post by dethredic on 2008-08-09
Ok, well I still like lots of the Ubuntu features, and if you see my specs, it shouldn't run slow. Maybe on the fresh install it will run better. It is just like right now after I log in, it takes 10 seconds for it to load the GUI and in that mean time I get to see the beige background and that is it.

One of the main reasons I wanted to attempt a custom kernal or optimized kernal is cause I usually learn by attempting projects. I will say, I wanna do this, then I do lotsa reasearch, ask questions, then attempt it. Things usually go worng and I learn even more fixing it.

---

### Post by |Eric| on 2008-08-09
you might be interested in Xubuntu a minimalistic version of Ubuntu
(less crap) 

& compiling a kernel is a good step towards performance 
also note that you may be running sevral usless processes 
(services) you could try disabling a few

with the smallest distros you can get down to a kernel that takes less than a Mb of space & even have a graphical interface under 10Mb 


so there is latitude as to what phat you whant to cut down.

---

### Post by dethredic on 2008-08-09
Does anyone know of a good tutorial on making a custom kernel? I have found some stuff, but everything is really outdated.

EDIT: Ok, I figured out how to edit it, now I just need to know what some good options to change are.

---

