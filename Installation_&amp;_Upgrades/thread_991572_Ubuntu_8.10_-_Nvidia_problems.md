---
title: "Ubuntu 8.10 - Nvidia problems"
date: 2008-11-23
forum: Installation &amp; Upgrades
---

### Post by waylow on 2008-11-23
Hey Guys,

I can't get the nvidia drivers to work with 8.10 - can use the generic driver but it has no 3d acceleration

can somebody tell me if they have had success or if it is possible with my hardware
and what is the correct driver to try


**CPU**: AMD Athelon(tm) 64 processor 3200+

**Video Card**: nVidia Corporation NV43GL [Quadro FX 540] (rev a2)

**Monitor**: ViewSonic VA1912wb

Any help would be greatly appreciated 

Thanks in advance

---

### Post by Giggity on 2008-11-24
I can confirm an issue with this.  I have an nVidia 7900 GTS and I've tried activating the nVidia 177 driver through the hardware driver manager.  It says it's "downloading and installing" but then it never indicates that it's been activated.

Attempting to enable Desktop effects thus fails.  Boo-hoo!  It worked on Hardy!

---

### Post by waylow on 2008-11-24
that's pretty much as far as I have got too
(I don't use Desktop effects as I had to always turn it off when I wanted to use blender - this is why I need the 3d acceleration though) 

I have tried the 96, 173, and 177 driver as well as stopping x and installing in from the command line

Has anyone had any success?

---

### Post by Giggity on 2008-11-24
Never mind, I'm kinda dumb... I had tried to activate the driver right after a fresh install of the system, but I forgot to do the big post-installation update beforehand.

Since the software wasn't up to date, apparently there was some kind of error.

So, have you done all the major updates?

---

### Post by waylow on 2008-11-24
> **Giggity said:**
> 
So, have you done all the major updates?

Yes

So you have been successful - that gives me hope

---

### Post by Giggity on 2008-11-25
That's too bad... my computer is "middle aged," so I guess there's not too many issues to be had with hardware.

You could try using one of the older drivers.  I'm actually using version 173 with no issues, but you may have more advanced acceleration needs.  Folks around here have been talking about glitches in the newest nVidia (177), so even if you can install it, you may still have problems.

Did the drivers work with 8.04 ?  If so, I'd just go back to Hardy.  That was probably the most stable release I've had the privilege to use.

---

### Post by TunaCanTommy on 2008-11-26
Take a look at the post by ryukent . .

[http://ubuntuforums.org/showthread.php?t=993368]("http://ubuntuforums.org/showthread.php?t=993368")

It describes a very quick and easy way to upgrade you nVIDIA driver to ver 180.08.

It solved some of my nNVIDA problems - #-o#

---

### Post by waylow on 2008-11-26
thanks TunaCanTommy

I did try the 180.06 version 
and also now the 180.08 but it still doesn't work

It looks like something is stopping the drivers from loading correctly not the actual drivers themselves

---

### Post by waylow on 2008-12-05
Just incase anyone else is still having the same problem
and they too have tried everything to get 3d acceleration working

I didn't fix it but I just rolled back to an older kernel

I had to roll back to  22.6.22-14 so that everything works properly again including all the other problems I was having (wireless WPA2, unclean shutdown and sound issues)

So it's not fixed but I gave up on 8.10 for the moment

---

