---
title: "Can you slipstream/kickstart ubunut?"
date: 2007-01-10
forum: Installation &amp; Upgrades
---

### Post by bone2006 on 2007-01-10
I have a copy of ubuntu running on a machine that's connected to a television via s-video.  The video drivers that come with ubuntu won't allow me to use my s-video monitor.  
So when I want to reinstall/format my computer and install ubuntu, I'm forced to bring out a monitor then install ubuntu and then install the linux nvidia drivers as well.  Then I'm able to connect my computer to my television. 
Well there's been times I wanted to use the liveCD for a thing or two or when I reformat and it's a pain dragging the monitor back and forth.

So my question is there any possible way to integrating video drivers into ubuntu slipstream or kickstart way with ubuntu?

I tried the newest alpha release and disapointing no s-video with that either without dragging out a CRT monitor and then installing the drivers :(

---

### Post by jbus on 2007-01-10
I'm not sure if it will work for you, but you might want to look at reconstructor [http://reconstructor.aperantis.com/](http://reconstructor.aperantis.com/)

---

### Post by bone2006 on 2007-01-11
thanks for the link, I went through the screenshot at least and read them all and seem you can reconstruct the ubuntu installation, which is nice, but nothing about drivers.

I've used super grub, which when it boots up, it at leasts asks you which video drivers do you want to install, so I'm able to use super grub's liveCD and perform operations, too bad I can't do it with ubuntu.

---

### Post by jbus on 2007-01-11
You can also chroot to make other changes before creating the live cd, so you should be able to install whatever drivers you want... just skip over all the other stuff, chroot & install your drivers and you'll have a live ubuntu cd with the drivers you need.

---

