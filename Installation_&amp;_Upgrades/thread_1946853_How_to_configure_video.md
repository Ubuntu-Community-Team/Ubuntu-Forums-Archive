---
title: "How to configure video"
date: 2012-03-25
forum: Installation &amp; Upgrades
---

### Post by davedaveh on 2012-03-25
Have installed Ubuntu 11.04 next to XP.  Video is balky - system is slow. Mouse conflicts too?

How to configure card and monitor?  Don't even know how to decipher chipset.
Using Acer flat screen monitor.

My install says I can't use Unity, so am using Classic. Video testing hangs....
Thank you for pointing me to a way to configure.

---

### Post by AlexDudko on 2012-03-25
> **davedaveh said:**
> Have installed Ubuntu 11.04 next to XP.  Video is balky - system is slow. Mouse conflicts too?

How to configure card and monitor?  Don't even know how to decipher chipset.
Using Acer flat screen monitor.

My install says I can't use Unity, so am using Classic. Video testing hangs....
Thank you for pointing me to a way to configure.

Provide us with the output of this commant:
> sudo lspci | grep VGA

---

### Post by davedaveh on 2012-03-25
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a2)

BTW, I have another card if that helps. The nVidia has cooling fins. The other one does not (Cardex)

---

### Post by AlexDudko on 2012-03-25
> **davedaveh said:**
> 01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a2)

BTW, I have another card if that helps. The nVidia has cooling fins. The other one does not (Cardex)

It's an old video card and I can't give you a working solution. I doubt whether it supports gnome3.
Have a look at this thread also [http://ubuntuforums.org/showthread.php?t=1487976](http://ubuntuforums.org/showthread.php?t=1487976)

---

### Post by davedaveh on 2012-03-25
I thought Linux could run on old stuff.

Can this card work?:

01:00.0 VGA compatible controller: S3 Inc. ViRGE/GX2 (rev 04)

(It actually is more unstable!!)

Thanks for your help.

---

### Post by AlexDudko on 2012-03-26
> **davedaveh said:**
> I thought Linux could run on old stuff.

Can this card work?:

01:00.0 VGA compatible controller: S3 Inc. ViRGE/GX2 (rev 04)

(It actually is more unstable!!)

Thanks for your help.

It's also a very old one. You won't be able to run gnome3 on it. I can say only that Ubuntu-10.04 worked fine with it. 
You can also try some more  lightweight DE (xfce, lxde).

---

### Post by davedaveh on 2012-03-26
OK you have some good ideas.  I'm wondering if I can even get a video card for a regular PCI slot - I've seen some high powered ones that may outpower my MB.  They've got HDMI and stuff. (Just need a card!)

I will try Lubuntu - hopefully I can install ntsf-3g/Disk Manager on it so I can see my old unbootable XP partition.
Yeah -- Linux can see my bad XP partiton files when all other boot disks cannot.
Thanks for the tips, AlexDudko

---

### Post by Mark Phelps on 2012-03-27
> **davedaveh said:**
> ...I'm wondering if I can even get a video card for a regular PCI slot ...

Yeah, that could be a real challenge.  You might have to go online to find some place that still stocks the "old" PCI cards.

---

