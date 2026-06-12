---
title: "Upgraded from 6.06 to 6.10 - black screen"
date: 2007-01-19
forum: Installation &amp; Upgrades
---

### Post by kensund on 2007-01-19
Hi!

I have an IBM Thinkpad 2656-E2G (P3 1Ghz, 632 MB RAM) that i installed a Ubuntu 6.06 (cd from Shipit) and it work perfectly..
So i tryed too install 6.10 (edgy) with the official method.. The download worked, but not the first reboot.. the Ubuntu logo loads too 100%, then the screen goes black..

So, what does a Windows guy do now?
Ive not that good in linux, just jused Knoppix for defected hardware..


H.E.L.P.  M.E. :)

---

### Post by pay on 2007-01-19
With my card when I update to xorg 7.1, the standard open source video drivers break compatiability with my ati card so I then need to install the proprietary driver or properly setup the radeon driver to get the x-server running again.

So try installing your video drivers, if you have a problem like mine.

---

### Post by kensund on 2007-01-19
Hmm, i need it in tablespoon format..

How do i install xorg 7.1 from command line?

---

### Post by pay on 2007-01-20
Sorry, I should of been more clear. Xorg 7.1 is automatically installed when you update to edgy. I can't tell you how to install your video card driver unless if you tell me what video card you have;)

---

### Post by kensund on 2007-01-20
Searched on the ibm.com page now, and it looks like it came with a "Trident CyberBlade" card.. never heard about them before..

Thanks for your effort in helping a ubuntu noob =D>

---

### Post by pay on 2007-01-20
Hmmm. You have a more obscure system than I thought so installing a driver is abit more tricky. However, I would imagine that the driver for that card would be compiled into the kernel. 

A search on google found this, but I havent tried it. [http://www.driverskit.com/freedownload/Video_Card/Trident/Blade_3D/11344.html](http://www.driverskit.com/freedownload/Video_Card/Trident/Blade_3D/11344.html)
( I mainly specialize in ati, nvidia and intel cards)

Hopefully someone with more knowledge of your hardware reads this and helps you some more. Goodluck.

---

### Post by kensund on 2007-01-20
How do i compile the driver in the kernel?
And can i do it from the Grub loader?
And will the unix driver work?
..
Maybe i should just go back to the 6.06 build

---

### Post by pay on 2007-01-20
> **kensund said:**
> How do i compile the driver in the kernel?The driver should already have been in the kernel so no compiling should be needed.> **kensund said:**
> Maybe i should just go back to the 6.06 buildMaybe that's best in your situation. Dapper (6.06) has had alot more bug fixing and testing that what edgy has so it is a more stable system.

---

