---
title: "Lost Ubuntu boot"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by gilch on 2010-05-01
I'm going from bad to worst.
I installed Ubuntu 10.04. Things seemed to go ok except when it was installing Grub. I couldn,t understand what was going on but I continued anyway.

It concluded and Ubuntu worked fine (after I reinstalled nvidia drivers). It showed the grub options on restart, and if I chose Linux it booted properly. It listed Windows 7 as an option, but when I tried it it didn't do anything.

I followed the best I could some advice on how to reload boot for WIndows 7, using the Win7 DVD. I went to COmmand prompt and ran
bootrec.exe /fixboot (it worked)
then
bootrec.exe /fixmbr (it worked0.

Then I tried reboot.

Now it reboots only Windows 7 and the Grub menu has disappeared. So now, I have regained Win7 but lost Ubuntu. (I have few hairs left).

Gilles

---

