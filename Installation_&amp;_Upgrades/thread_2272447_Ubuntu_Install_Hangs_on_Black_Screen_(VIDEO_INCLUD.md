---
title: "Ubuntu Install Hangs on Black Screen (VIDEO INCLUDED)"
date: 2015-04-06
forum: Installation &amp; Upgrades
---

### Post by Demsmond on 2015-04-06
I am trying to install Ubuntu on a Republic Of Gamers g20AJ, but every time I try to install my computer will starting to install Ubuntu, but then it simply hangs on a black screen, however the backlights are still on.

VIDEO OF WHATS HAPPENING
[https://youtu.be/abraOHpzKIQ](https://youtu.be/abraOHpzKIQ)


System Specs 

**Graphics Card:** Nvidia GeForce GTX 760 / Intergrated Graphics
**Operating System:** Windows 8.1
**CPU: **Intel(R) Core(TM) i5-4460 CPU @ 3.2ghz

I am connected to a 32 inch 1920x1080p Monitor via HDMI

From what I remember, the computer switches from integrated to NVidia gpu, but you cant switch it from the UEFI, its 100% automatic

I have went through hundreds of threads trying to find the answer, but no luck as of yet. Many of these threads give steps that are supposed to be taken at a "language select" screen, but I only get the grub loader

I have disabled secure boot
I used legacy and UEFI mode and neither worked
I have used CSM settings for Legacy, didn't work
I have used nomodeset in the grub console
I have used the fan off command in the grub console
I have tried switching to a DvD
I have tried switching to a bootable USB

When I try booting with UEFI its even worse, it just immediately goes to the black screen without installing anything.

I have been at this for almost 15 hours straight, any ideas on how I could get Ubuntu to stop hanging at the black screen?

---

### Post by gordintoronto on 2015-04-07
What version of Ubuntu?

My choice would be to leave UEFI and secure boot on, and use nomodeset, with 64-bit Ubuntu 15.04, which is still in beta. (I have been running Xubuntu 15.04 for a month with no problems.) New hardware, old OS, bad combination.

---

