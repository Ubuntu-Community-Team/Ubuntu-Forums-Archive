---
title: "CD boot failure... I/O error on hdc?"
date: 2006-11-07
forum: Installation &amp; Upgrades
---

### Post by ncc386 on 2006-11-07
I'm trying to boot from the x64 ISO and besides the graphics being a little corrupted (which might be expected as I have a newer video card and no drivers yet), the Ubuntu logo appears and after a few minutes, I can see a line saying there was an I/O error on hda (or hdc depending upon which computer I try to boot it on).

The hda error appear on a computer that is using the ATI RD580/ULi chipset, SATA drives, and an X1900XT PCI-E video card.

The hdc error appears on a computer using an NVIDIA nForce4 chipset, IDE drive, and X850XT PCI-E video card.

The error notification begins with a [ 123.435784745] number (randomized for example) that continuously counts upward as every 10 seconds or so, the same error line appears under the last.

These computers are quite operational with other operating systems. So, maybe there is something I am overlooking? Maybe a switch I can pass off during CD boot?

It stays on a black (console I'm assuming) screen with regular errors for hours. I usually lose patience and give up.

I'm downloading the regular x86 distro right now to give it a shot. I am using an Athlon64 X2 4800+, by the way.

Thanks for any help you can give!

---

### Post by Darksky on 2006-11-07
Same problem for me, same error.
I'm a ubuntu newbie and i donwloaded the x64 desktop iso.
I tried to install it on my laptop, an acer aspire 5024 ( turion 64bit, 1Gb ram, ATI x700 128 MB, HD seagate 4200rpm 80Gb-->60gb for win xp and 20 gb for Suse 9.3 ).

---

### Post by ncc386 on 2006-11-08
Sounds like I'm Ubuntu'd! hehe

---

### Post by loclei on 2006-11-09
[1719705.296000]hdd:timeout waiting for DMA
[1719705.300000]hdd:drive not ready for command

this is my error
i don't know how to get past this and install ubuntu
i've waited some minutes and the error would repeat itself

and there was another error in between these that was something like can'd read sector ******

---

### Post by SkyNet2029 on 2006-11-09
I was receiving the same errors on install, so I got tired and did the logical thing.. replaced hdc with a known good (but older and more common model than my newer dvd drive).. and problem solved.

---

### Post by Darksky on 2006-11-09
Solved installing X64 _alternate_, burned at 4X speed.

---

