---
title: "Problems installing Ubuntu 8.04 on NX9000"
date: 2008-09-14
forum: Installation &amp; Upgrades
---

### Post by jlaeret on 2008-09-14
Hello, everyone!

I am experiencing problems installing Hardy Heron on my old HP Compaq nx9000 from the Live CD. When I boot from it and choose install it jumps to the loading screen, and when it's done loading it goes to the background picture of the bird. There is nothing else showing on the screen. At this point nothing more happens, except the cd-drives continues to read the drive very erratically. After a while the screen goes black, possibly due to some power saving thing(?)

Anyways, the cursor does not respond to the touchpad either.
Anyone had any similar problems? There is not much info about installing ubuntu on this laptop on the internet, at least that I've been able to find.

Thanks!

---

### Post by overdrank on 2008-09-14
> **jlaeret said:**
> Hello, everyone!

I am experiencing problems installing Hardy Heron on my old HP Compaq nx9000 from the Live CD. When I boot from it and choose install it jumps to the loading screen, and when it's done loading it goes to the background picture of the bird. There is nothing else showing on the screen. At this point nothing more happens, except the cd-drives continues to read the drive very erratically. After a while the screen goes black, possibly due to some power saving thing(?)

Anyways, the cursor does not respond to the touchpad either.
Anyone had any similar problems? There is not much info about installing ubuntu on this laptop on the internet, at least that I've been able to find.

Thanks!

Hi and welcome, could you tell us some system specs like memory? Also have you checked the cd for errors?

---

### Post by zoomy942 on 2008-09-14
> **overdrank said:**
> Hi and welcome, could you tell us some system specs like memory? Also have you checked the cd for errors?


i agree - its probably the cd with errors.

---

### Post by jlaeret on 2008-09-14
Thanks!
I'm pretty sure it's not the cd that has errors, I've tried burning it out many times, both with the 8.04 and the 8.04.1 version. I've also checked the cd's for errors.
I'm trying to look up the specs, not completely sure how to find them all, but looking at My Computer in Windows gives:
HP Compaq nx9000
Mobile Intel(R) Pentium 4 - M CPU 2.00GHz (Actually says both 2.00GHz and 1.20GHz)
ATI RADEON IGP 340M 
Hitachi DK23EA-40 40GB
192MB 266MHz SDRAM PC2100

Let me know if you need any more info. I tried running ubuntu from the live cd without installing it, doesn't work either. It freezes after the loading screen showing a blank beige background (no picture this time) and a white rectangle in the corner (as though there would be a window appearing there, but it froze before it opened). Cursor doesn't move in this mode either.

---

### Post by wpshooter on 2008-09-14
If it only has 192mb RAM, then that is your problem.

You could try the ALTERNATE (text based) CD version of Ubuntu BUT with only 192mb of RAM, I am not sure that even if you can get it to install, if you are going to have even a half way decent experience.

You may try Xubuntu instead but my recommendation would be that you get more RAM or even better a computer that is a little more up-to-date of it's specs.

Good luck.

---

### Post by tangibleorange on 2008-09-14
> **wpshooter said:**
> If it only has 192mb RAM, then that is your problem.

You could try the ALTERNATE (text based) CD version of Ubuntu BUT with only 192mb of RAM, I am not sure that even if you can get it to install, if you are going to have even a half way decent experience.

You may try Xubuntu instead but my recommendation would be that you get more RAM or even better a computer that is a little more up-to-date of it's specs.

Good luck.

yeah that's definitely your problem. had the exact same thing on a computer of similar specs with the Xubuntu live CD, so you've no chance with the Ubuntu CD!
As above, I would recommend simply buying more RAM or try using the Alternate CD of Xubuntu. it will probably install but be very slow.

good luck!

---

### Post by jlaeret on 2008-09-14
Yeah, perhaps. This is just an old computer I had lying around, figured it'd be fun to see if I could get ubuntu on it. I was a bit surprised though that it said 192MB, I was almost certain it had 256MB. Is it possible that the computer is only accessing 192MB for some reason?

---

### Post by tangibleorange on 2008-09-14
> **jlaeret said:**
> Yeah, perhaps. This is just an old computer I had lying around, figured it'd be fun to see if I could get ubuntu on it. I was a bit surprised though that it said 192MB, I was almost certain it had 256MB. Is it possible that the computer is only accessing 192MB for some reason?

possible but unlikely. you can confirm by going into your BIOS at startup and seeing what it reports.

---

### Post by overdrank on 2008-09-14
> **jlaeret said:**
> Yeah, perhaps. This is just an old computer I had lying around, figured it'd be fun to see if I could get ubuntu on it. I was a bit surprised though that it said 192MB, I was almost certain it had 256MB. Is it possible that the computer is only accessing 192MB for some reason?

Hi and yes the graphics are using the rest. You may try and reduce what is shared with the graphics in the bios. This may allow you to run the lived cd and you can try and use the alternate cd for installation but it is recommend to use ubuntu 384mb. You may try puppy or DSL.

---

### Post by jlaeret on 2008-09-14
> **overdrank said:**
> Hi and yes the graphics are using the rest. You may try and reduce what is shared with the graphics in the bios. This may allow you to run the lived cd and you can try and use the alternate cd for installation but it is recommend to use ubuntu 384mb. You may try puppy or DSL.

Of course! Yeah, I remember now reading that the memory on this computer is shared with the graphics card. I'm trying to install xubuntu now, it seems to work, but it's a bit slow. Thanks! :)

---

