---
title: "Basic Custom kernel compilation"
date: 2008-07-22
forum: Installation &amp; Upgrades
---

### Post by Riverdale on 2008-07-22
Hi
I am a newbie to custom kernel compilation and have recently switched over to ubuntu hardy.

I have compiled my custom kernel successfully (2.6.26 with sound card exception) using some of the excellent guides listed by community. But, I need to know, everytime I make an alteration to menuconfig, do I have to recompile the kernel for changes to take effect (the time taken by compilation is really a pain).

Cheers,
Riverdale

---

### Post by sdennie on 2008-07-22
Yes, you generally have to recompile every time you make a change to the config.  However, some things like sound/wifi drivers can be built as modules against a specific kernel (so, you just compile the specific modules and not the entire kernel).  You should first see if that's possible before doing a full recompile.  

For example, the latest sound drivers can be downloaded from [here]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.17.tar.bz2") and can you usually build them for the running kernel without having to recompile everything.

---

### Post by Riverdale on 2008-07-22
Hi
I finally got my sound card working. I had recompiled the code to get it done. Had to turn Intel HD in menuconfig to get it working, although it is not installed (read somewhere while googling).

Rd

---

