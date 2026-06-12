---
title: "Will not install HAD A PREVIOUS POST"
date: 2011-04-21
forum: Installation &amp; Upgrades
---

### Post by silvesj on 2011-04-21
Hello,

I had a post a few days ago which got pushed far back I see. I was having trouble installing Ubuntu because from what I understand it is the graphics card. One responder said that Nvidia does not support certain drivers now. I have a nVidia Cuda 360. Is that not one of the supported cards? I really want to be able to install this on my laptop. Please let me know if there is any solution.

---

### Post by Hedgehog1 on 2011-04-21
> **silvesj said:**
> Hello,

I had a post a few days ago which got pushed far back I see. I was having trouble installing Ubuntu because from what I understand it is the graphics card. One responder said that Nvidia does not support certain drivers now. I have a nVidia Cuda 360. Is that not one of the supported cards? I really want to be able to install this on my laptop. Please let me know if there is any solution.

Just check our previous post for hardware specs.  Just so you know, this is a 'family' site (lots of young folks here) and once you use bad words, folks tend to avoid you.

As to your specific NVidia issue - right now the best support for NVidia cards in the newest daily build of 11.04 Natty beta2.  It got an updated NVidia drive yesterday (at least to made it to my NVidia based laptop and NVidia based desktop yesterday).

You best hope to operate Ubuntu is to either:

Try the very latest 11.04 Natty beta2 daily build.  Login using the 'Classic no effects' desktop, load the 'NVidia restricted drivers', reboot when told and see if it works.

Your only other option is to run the generic video drivers.  You will not get Compiz effects, but you **may** be able to run.

***The Hedge***

:KS

---

### Post by silvesj on 2011-04-21
Apologize for the language. This has just become very stressful for me. I will download the latest .iso, that should have the drivers right? Also, if not. How do I go about loading into limited graphics? Or I guess run the install and connect to the network for updates first. Thanks.

---

### Post by Hedgehog1 on 2011-04-21
> **silvesj said:**
> Apologize for the language. This has just become very stressful for me. I will download the latest .iso, that should have the drivers right? Also, if not. How do I go about loading into limited graphics? Or I guess run the install and connect to the network for updates first. Thanks.

This install carries a program with a little video card as an icon - it figures out if there are drivers for you video card 'above and beyond' the basic video support carried with the kernel.  It is called  **EDIT:** '**Additional** Drivers'.

By not allowing it to run and install the NVidia drivers at all (assuming the newest NVidia driver still does not work with your video card), you will run in generic video mode.  This will be fine for surfing and work processing.  With your card you will not fancy effects in generic, and you will not be able to use Unity (Unity requires 3d capable card/drivers combo)

Hope this helps...

***The Hedge***

:KS

---

### Post by Quackers on 2011-04-21
Have you seen this thread? Plenty others with similar details
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

