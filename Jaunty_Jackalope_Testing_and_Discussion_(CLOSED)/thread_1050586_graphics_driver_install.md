---
title: "graphics driver install"
date: 2009-01-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by fdhealy4 on 2009-01-25
Jaunty Jackalope A3 installed. Previously had 8.10 installed and things worked great.

I did a clean install of Jaunty. After about 15 minutes the "normal video effects" started to work. I assume somehow the proprietary video driver installed. I had to re-install Jaunty and I can't get the visual advanced effects to work. The hardware drivers window has nothing listed. My video card is listed as a nVidia Corporation NV34 (GEForce 5200) (rev al) when I pull it up in terminal. How and where do I go to get and install the proper driver.

---

### Post by autocrosser on 2009-01-25
You need to look thru the prior posts---there is a mod you need to do to make 8xxx, 9xxx & newer nVidia products work & then add a PPA from Launchpad...It's all in the "X-server breakage" thread--Dinxter posted the xorg.conf fix & I posted the PPA.

Looks like there needs to be a Sticky about this....

As for your card, It is not going to work with the nVidia drivers right now........

---

### Post by RAOF on 2009-01-25
> **autocrosser said:**
> You need to look thru the prior posts---there is a mod you need to do to make 8xxx, 9xxx & newer nVidia products work & then add a PPA from Launchpad...It's all in the "X-server breakage" thread--Dinxter posted the xorg.conf fix & I posted the PPA.
...

You don't need a PPA (and haven't for quite some time).  The nvidia-glx-180 packages from the official archives work just fine.

---

### Post by autocrosser on 2009-01-25
Sorry 'bout that--I do think that we need a sticky about this--I see quite a few questions...

---

### Post by gspat on 2009-01-25
The packages themselves work fine from the standard repos now, but you still need to add the IgnoreABI directive to xorg.conf

---

### Post by Gina on 2009-01-26
Go into Synaptic Search for nvidia 180 and install the nvidia 180 driver packages.  You will also need the xorg.conf patch (probably) as detailed in another thread.  I found the same thing.

---

### Post by plun on 2009-01-26
Is it hacked for 5XXX GPUs  ???

Current nVidia releases

[http://www.nvnews.net/vbulletin/showthread.php?t=122606](http://www.nvnews.net/vbulletin/showthread.php?t=122606)


**About the 180 driver**

> Please note: This NVIDIA Linux graphics driver release **supports GeForce 6xxx and newer NVIDIA GPUs**, GeForce4 and older GPUs are supported through the 96.43.xx and 71.86.xx NVIDIA legacy graphics drivers. GeForce FX GPUs are supported through the 173.14.xx NVIDIA legacy graphics drivers.


Driver 173.14.15 and ignoreABI probably works for an 5200 GPU...

---

### Post by RAOF on 2009-01-26
Man, wouldn't it be nice if nouveau was good enough for default, and we had just *one* driver for the nvidia cards, rather than *four*!

---

### Post by autocrosser on 2009-01-26
Yes +3!!!!!!

---

### Post by plun on 2009-01-27
> **RAOF said:**
> Man, wouldn't it be nice if nouveau was good enough for default, and we had just *one* driver for the nvidia cards, rather than *four*!

Yes for sure...:D

But a nVidia GPU chip is maybe a little more advanced then 
crap from Intel....

nVidia will open the driver....100% sure when the timing is right.

---

### Post by RAOF on 2009-01-27
> **plun said:**
> 
But a nVidia GPU chip is maybe a little more advanced then 
crap from Intel....

I present to you... "radeon".  One driver from > r128 - r700.  Although there's also radeonhd for > r500, too; I'm not entirely sure how that's going to end up.

> **plun said:**
> 
nVidia will open the driver....100% sure when the timing is right.

I fail to see what's wrong with the present.  Also, opening the driver?  Not really so useful.  It'd need to be rewritten to be acceptable anyway - friendly drivers don't replace parts of X or the entire Mesa stack.  Documentation, *a la* ATi, would be fine.  Developers paid to hack on nouveau optional (I believe thanks here go to Red Hat).

---

### Post by plun on 2009-01-27
Well... I passes to discuss this... last time I got a infraction. :rolleyes:

Windows 7 says thanks to the open source mess..


----------------------------------------------------

A new driver is also out, **ver 180.25** ;)


Aaron calls it a "pre-release"

[http://www.nvnews.net/vbulletin/showthread.php?t=122606](http://www.nvnews.net/vbulletin/showthread.php?t=122606)

Running fine nevertheless..:D

---

