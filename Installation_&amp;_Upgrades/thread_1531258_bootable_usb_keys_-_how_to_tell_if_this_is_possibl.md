---
title: "bootable usb keys - how to tell if this is possible?"
date: 2010-07-14
forum: Installation &amp; Upgrades
---

### Post by poldie on 2010-07-14
I have some USB keys which can be made bootable, and some which can't.  It seems to be random. Admittedly, it's older, smaller ones which can't, in my experience.

I want to buy a USB key which is large enough to install a full, normal version of Ubuntu 10.04 onto, which seems to require about 2.5 gigs.  I can get a 16gb Sandisk Cruzer Blade for about £17, which would leave plenty of space for apps/data, but does anyone know if this is definitely bootable?  What is it about them which makes them bootable?

---

### Post by Darkness Des on 2010-07-14
Most newer USB Keys can be booted from. As long as they have enough space on them, they can be used.

---

### Post by poldie on 2010-07-16
> **Darkness Des said:**
> Most newer USB Keys can be booted from. As long as they have enough space on them, they can be used.

I've just ordered one - guess there's only one way to find out!

Cheers.

---

### Post by jimmers on 2010-07-17
Hi Poldie,
I have Lucid running on a Kingston data Traveller (16Gb), bought from Argos, no trouble at all, runs like a dream, also have Maverick (Testing) on a Kingston Data Traveller (8Gb), also bought from Argos, Kingston is brills.

Tried the SanCruzer type, but now just use them for storage i.e 16 and 8 Gb drives,
if you have'nt already decided on which drive you will use, I reccomend Kingston.

Luck

Jim

---

### Post by efflandt on 2010-07-17
Just make sure that your Cruzer does not have U3, because that includes an embedded pseudo cdrom (sr device) for the U3 encryption, which can greatly extend boot time.  I have heard that there are ways to remove that, so not sure if that helps.

I just know that booting 9.10 iso on a 2 GB mini Cruzer w/U3 took twice as long to boot as other USB sticks, or even SD or microSD on USB.

---

### Post by poldie on 2010-07-17
> **efflandt said:**
> Just make sure that your Cruzer does not have U3, because that includes an embedded pseudo cdrom (sr device) for the U3 encryption, which can greatly extend boot time.  I have heard that there are ways to remove that, so not sure if that helps.

I just know that booting 9.10 iso on a 2 GB mini Cruzer w/U3 took twice as long to boot as other USB sticks, or even SD or microSD on USB.

I've already ordered it - no sign of U3 on the amazon page.  Looks like there is a way to get rid of it if it's on there.  I'm going to check it out the day I get it, install Ubuntu, do some timings etc.  If it's slow, or I can't get rid of U3, or I can't boot from it then it's going straight back.   I'll update this comment either way.

cheers.

Yeah, this key is bootable.

---

### Post by bumanie on 2010-07-17
The U3 uninstaller works fine and once U3 is gone, the usb stick works as it should - that U3 was a terrible idea, imo.

---

