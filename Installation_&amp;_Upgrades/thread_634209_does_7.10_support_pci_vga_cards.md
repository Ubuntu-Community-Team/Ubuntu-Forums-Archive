---
title: "does 7.10 support pci vga cards?"
date: 2007-12-07
forum: Installation &amp; Upgrades
---

### Post by Twig E. Pottox on 2007-12-07
I have tried two different pci vga cards and 7.10 hangs on startup with both of them. This happens with the live disk also. it goes to the ubuntu start up screen and gets to about 3 out of 20 spaces on the statup scale then stops. Happens with gforce and ati cards. No agp on this mobo  (A Open MXGVR(E) ) 1gb ram 80 GB hdd  The on board vga works well but is slow. Is pci not supported and or is there a work around? thanks in advance..

---

### Post by njparton on 2007-12-07
Is that quite an old motherboard?  What chipset does it have?

---

### Post by Twig E. Pottox on 2007-12-07
> **njparton said:**
> Is that quite an old motherboard?  What chipset does it have?

Chipset + Intel 845GV, 

it has what is called a ADD slot where you would expect the AGP slot. Iit looks the same as a AGP and agp cards fit but don't work

---

### Post by Twig E. Pottox on 2007-12-07
Bump --- with more info

Originally Posted by njparton  View Post
Is that quite an old motherboard? What chipset does it have?


The  Chipset is a:  Intel 845GV,  The Board is about 4 years old

it has what is called a ADD slot where you would expect the AGP slot. It looks the same as a AGP and agp cards fit but don't work in it therefore I tried the PCI cards but the hung on startup.

other info celeron 2.6 ghz, 1 ghz ram, soundblaster live5.1, 
__________________

---

### Post by baugen on 2007-12-07
you have to know what graphics chip you have. If linux can't detect it use windows to find out
if you cant identify it otherwise

then after X fails do dpkg-reconfigure xserver-xorg

btw you should get it working by choosing vesa driver but that driver may not suit your needs

---

### Post by Twig E. Pottox on 2007-12-07
> **baugen said:**
> you have to know what graphics chip you have. If linux can't detect it use windows to find out
if you cant identify it otherwise

then after X fails do dpkg-reconfigure xserver-xorg

btw you should get it working by choosing vesa driver but that driver may not suit your needs

Thanks do you mean I have toidentify the actual chip or is the following enough:

I have tried a ATI radeon 9250 256mb pci card and a nvidia GF2MX40064 64mb pci card. With either card 7.10 freezes on boot up at 3 out of 20 on the scale that shows boot progress. I don't know how I could run any command if it doesn't boot up.

---

### Post by Twig E. Pottox on 2007-12-08
El Bumpo

---

### Post by njparton on 2007-12-08
Never heard of an AAD slot so I'm out of ideas.

I've not used a PCI graphics card for years. What's wrong with using the onboard GPU with the VESA driver?

---

### Post by Twig E. Pottox on 2007-12-09
> **njparton said:**
> Never heard of an AAD slot so I'm out of ideas.

I've not used a PCI graphics card for years. What's wrong with using the onboard GPU with the VESA driver?


thanks for your input anyway

This is the only board where I have come across ADD. and I cant find any info on it, most likely a attempt by AOPen to get a proprietary format going.  

I got into this because this particular system  seems a bit slow on the boot up so I blamed the onboard video and dug out the PCI cards I had inherited and gave them a try. A exercise in futility.  No great loss as this is intended to be a part of a  audio system (record and Playback) and not for graphics intensive use. Thanks again for responding I going to leave well enough alone for now.

---

