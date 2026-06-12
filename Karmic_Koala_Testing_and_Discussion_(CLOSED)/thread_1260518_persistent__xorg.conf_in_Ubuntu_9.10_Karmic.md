---
title: "persistent  xorg.conf in Ubuntu 9.10 Karmic"
date: 2009-09-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by redDEADresolve on 2009-09-07
It was a shock to find that there was no /etc/x11/xorg.conf in Ubuntu 9.10

I understand it is created on the fly and the old method was a bit dated, but I need to edit some of my touchpad settings and make them stick.

How can I create/make a persistent xorg file?

---

### Post by glasen on 2009-09-07
Just type in "sudo nano /etc/X11/xorg.conf" and add your modifications.

A existing xorg.conf-file will never be touched or deleted!

---

### Post by jwssr on 2009-09-07
nor used    ???????

---

### Post by autocrosser on 2009-09-07
All the values in mine get used (I run a SLI-Nvidia setup & need to define several values) --so I would say that it is persistent.... ;)

---

### Post by redDEADresolve on 2009-09-07
how am i supposed to define my touchpad settings if the /ect/x11/xorg.conf files isnt used

---

### Post by jithin1987 on 2009-09-07
If the file is present xserver will read from it. If not it will stick with defauts.

---

### Post by dinxter on 2009-09-08
/etc/X11/xorg.conf is used if it exists, it just isnt created by default.
sudo Xorg -configure 
will try to generate an xorg.conf for you if you want it
but if you need to add options you can just create an empty xorg.conf file yourself and add those options to it if you like

---

### Post by eznet on 2009-10-15
It does seem to be operating differently than in the past in my experiences thus far... Ex. I used to be able to make a change in xorg.conf and have that reflected immediately (upon X restart of course), but now I am having the widely documented nVidia/New Kernel issue and changing my driver back to 'nv' doesn't seem to cause X to use nv rather than nVidia - it just ignores the change...

Anyone aware of any good faq/doc/wiki for these changes with how xorg.conf is being handled in 9.10?

Thanks!

-Matt

---

### Post by chrispcall on 2009-10-24
A manual on these changes would be awesome.  I am very much a noob, but how can I back up my settings before installing restricted video drivers if there is no Xorg.conf file?  Is there somewhere else to back up?

Thanks in advance!

---

### Post by Longinus00 on 2009-10-24
> **eznet said:**
> It does seem to be operating differently than in the past in my experiences thus far... Ex. I used to be able to make a change in xorg.conf and have that reflected immediately (upon X restart of course), but now I am having the widely documented nVidia/New Kernel issue and changing my driver back to 'nv' doesn't seem to cause X to use nv rather than nVidia - it just ignores the change...

Anyone aware of any good faq/doc/wiki for these changes with how xorg.conf is being handled in 9.10?

Thanks!

-Matt

Have you tried removing the nvidia driver?

---

