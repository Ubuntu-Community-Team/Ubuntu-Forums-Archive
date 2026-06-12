---
title: "glitches trying to install Ubuntu MATE on old IBM ThinkPad T43"
date: 2015-07-19
forum: Installation &amp; Upgrades
---

### Post by Buntu Bunny on 2015-07-19
I was given an IBM ThinkPad T43 and thought it would be a good way to try out Ubuntu MATE 15.04. The gal who gave it to me had Xubuntu 12.04 installed but couldn't remember her password, so I figured I would set BIOS to load the DVD first and install from there. I direct downloaded ubuntu-mate-15.04-desktop-i386.iso, checked the MD5 hashes, and burned it to a DVD. When I attempted to load the disc, I got a screen that said

> ISOLINUX 6.03 2010358 ETCD Copyright (C) 1994-2014 H. Peter Anvin et al

and a blinking cursor which was not responsive to the keyboard. I removed the DVD and got 

> Failed to load Idlinux.c32
Boot failed: press any key to retry...

I removed the DVD, closed the DVD drive and GRUB popped up, but I couldn't get anything to load.

Crtl-alt-del reboots to blank screen.

So, I have done something wrong, am doing something wrong, or attempting the impossible. Suggestions?

---

### Post by v3.xx on 2015-07-19
If it was me, I would try 14.04.1

That release will keep you on a older kernel and you just may get lucky :)

I have not seen this "Failed to load Idlinux.c32" error, but a lot of talk about it on google.

Good luck

---

### Post by Buntu Bunny on 2015-07-19
> **v3.xx said:**
> If it was me, I would try 14.04.1. That release will keep you on a older kernel and you just may get lucky :)

Well, that's an idea. I doubt which one matters a whole lot. I would just like to get *something* on that machine. 

> **v3.xx said:**
> I have not seen this "Failed to load Idlinux.c32" error, but a lot of talk about it on google.

Hmm, then that's something I should research. Thanks v3.xx!

---

### Post by v3.xx on 2015-07-19
Maybe better

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Failed+to+load+Ldlinux.c32&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Failed+to+load+Ldlinux.c32&sa=Search&cof=FORID:9)

---

### Post by Buntu Bunny on 2015-07-19
Success! I ended up installing 14.04.2, but it was quick and painless. I like what I see. 

I'm glad there was a workaround to the "Failed to load Idlinux.c32" error. Thanks for your help v3.xx

---

