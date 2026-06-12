---
title: "Will nvidia users get KMS in karmic?"
date: 2009-06-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tgpraveen on 2009-06-22
as far as i know the proprietary nvidia drivers are not going (and cant due to legal reasons??) to support KMS and the foss drivers of nvidia novoue drivers wont support KMS until kernel 2.6.32 or 2.6.33 which definitely wont be in karmic.

SO what happens to nvidia card users like me? how ill our experience in karmic be?

will it be just like jaunty ie without KMS (which is ok imho)?
will it be very buggy (like jaunty was for intel users)?

---

### Post by Swarms on 2009-06-22
Most people are still going to use the propriatary driver until then.

---

### Post by RAOF on 2009-06-22
The binary driver certainly won't.  The nouveau drivers might; I haven't checked yet.

---

### Post by tgpraveen on 2009-06-22
nouveau drivers with KMS certainly wont be ready in time for karmic.
SO my question is where does that leave us nvidia users.

Also why "binary driver certainly won't"?

also problem with Nouveau is that although it is good at 2d and maybe one day KMS, people who need 3D support will need the proprietary drivers.

SO users will have to give up one thing or the other for quite a long period of time till Nouveau catches up.

---

### Post by 23meg on 2009-06-22
Nouveau will do KMS eventually, but most likely will miss the Karmic time frame.

---

### Post by gnomeuser on 2009-06-22
> **23meg said:**
> Nouveau will do KMS eventually, but most likely will miss the Karmic time frame.

Eventually.. that is an understatement, Ben Skeggs had that working for the Geforce8 series cards in F11. It works today, just not for every card. 

[http://fedoraproject.org/wiki/Features/NouveauModesetting](http://fedoraproject.org/wiki/Features/NouveauModesetting)

---

### Post by 23meg on 2009-06-22
[QUOTE=tgpraveen]Also why "binary driver certainly won't"?[/QUOTE]

My understanding, based on some dated semi-official reportage, has been that the kernel interfaces needed for KMS work are exposed to GPL modules only, meaning that either NVIDIA will have to open at least part of their X module source (they obviously have been unwilling to), or the relevant kernel code will have to be adapted to fit (the kernel people are perhaps understandably reluctant to bend their code around an uncontrollable proprietary module that may change at any moment).

---

### Post by gnomeuser on 2009-06-22
> **tgpraveen said:**
> 
Also why "binary driver certainly won't"?


Supporting KMS would make their code derived from the kernel and thus subject to the terms of the GPL. Something nvidia wants to avoid like the plague, they are already on legally some what thin ice with their approach today.

---

### Post by 23meg on 2009-06-22
> **gnomeuser said:**
> Eventually.. that is an understatement, Ben Skeggs had that working for the Geforce8 series cards in F11. It works today, just not for every card. 

[http://fedoraproject.org/wiki/Features/NouveauModesetting](http://fedoraproject.org/wiki/Features/NouveauModesetting)

I know, but as per [the kernel KMS plans for Karmic]("https://blueprints.launchpad.net/ubuntu/+spec/kernel-karmic-kms"), KMS will be enabled for the drivers that can work with a broad range of hardware and deemed stable enough around Alpha 6, and if I recall correctly, at the UDS session the possibility of Nouveau making it was pretty much ruled out in that regard by people who have the call, and have been following up the progress much more closely than I have.

---

### Post by froggyswamp on 2009-06-22
> **gnomeuser said:**
> ...they are already on legally some what thin ice with their approach today.
I'm just curious, can I have a link/hint to what legal issues they're facing please?

---

### Post by plun on 2009-06-22
> **tgpraveen said:**
> as far as i know the proprietary nvidia drivers are not going (and cant due to legal reasons??) to support KMS and the foss drivers of nvidia novoue drivers wont support KMS until kernel 2.6.32 or 2.6.33 which definitely wont be in karmic.

SO what happens to nvidia card users like me? how ill our experience in karmic be?

will it be just like jaunty ie without KMS (which is ok imho)?
will it be very buggy (like jaunty was for intel users)?

KMS is a nVidia hater "hype" with minimal use.........
> 
With KMS, a simple default policy is loaded into the kernel for initial output setup, which means connected displays should go to their native resolution as early as possible. Graphical display services, like the X server and the new Plymouth boot manager, simply reuse the existing display settings if they match what is desired. This allows for a seamless transition between bootup and login screen. Fast user switching can also take advantage of this; if both users have the same screen resolutions, then there's no need to blink to transition, and even if they're different, the kernel can make the switch exactly once (instead of twice like before).

Finally, since the kernel is aware of which regions of video memory are being displayed, it can print panic messages to the display, which will assist with troubleshooting.


Just "crap" for a normal user.........:D

---

### Post by tgpraveen on 2009-06-22
well for me the most intresting thing with KMS is super fast and stable suspend resume feature.

the flicker free boot will help improve linux's image but the huge impprovements to suspend-resume that kms brings is what i am intrested in.
And so it is not just "hype".

---

### Post by plun on 2009-06-22
Well... maybe there are more important issues...?

KMS gives minimal of benefits and Gnome is overfilled with "crap"...

---

### Post by tgpraveen on 2009-06-22
KMS and gnome have nothing to do with one another really.
and suspend resume is a important feature for laptop users.

also fast boot up times in which it helps impresses users.

and yes gnome does have a lot of problems which must be dealt with too i dont disagree.
but the people doing the 2 things are different

---

### Post by PRGUY85 on 2009-06-22
Nouveau doesn't support 3D effect yet right?

---

### Post by ghindo on 2009-06-22
> **PRGUY85 said:**
> Nouveau doesn't support 3D effect yet right?AFAIK it doesn't, no.

---

### Post by cb951303 on 2009-06-22
I emailed Nvidia about KMS support in binary driver and they told me they don't plan to support it.

---

### Post by MacUntu on 2009-06-22
> **PRGUY85 said:**
> Nouveau doesn't support 3D effect yet right?

Standby/resume being another issue. :(

---

### Post by inportb on 2009-06-22
> **cb951303 said:**
> I emailed Nvidia about KMS support in binary driver and they told me they don't plan to support it.

They also posted this on some popular forum... I forgot where it was...

---

### Post by plun on 2009-06-22
> **MacUntu said:**
> Standby/resume being another issue. :(

Well.... what is the worst "bugger"...a terrible Gnome session mess or KMS..??:)

---

### Post by inportb on 2009-06-22
> **plun said:**
> Well.... what is the worst "bugger"...a terrible Gnome session mess or KMS..??:)

Definitely KMS, because it's easy to switch to KDE :) (j/p)
Hmm... now to get KMS working for *radeon*...

---

### Post by plun on 2009-06-22
> **inportb said:**
> Definitely KMS, because it's easy to switch to KDE :) (j/p)
Hmm... now to get KMS working for *radeon*...

But what does KMS give you....???  or for a normal user ???

Gnomes session management is a mess, IMHO !

---

### Post by inportb on 2009-06-22
> **plun said:**
> But what does KMS give you....???  or for a normal user ???

Hm... nothing much, actually. I don't sit around idly as my laptop boots :o

> **plun said:**
> Gnomes session management is a mess, IMHO !

Ah, I wouldn't know... but it does seem to be of higher priority -- after all, you boot your computer not for the sake of booting it, but to use it.

---

### Post by plun on 2009-06-22
> **inportb said:**
> Hm... nothing much, actually. I don't sit around idly as my laptop boots :o

Ah, I wouldn't know... but it does seem to be of higher priority -- after all, you boot your computer not for the sake of booting it, but to use it.

Yup, If we manage to boot to the login screen within 10s and a Gnome start takes 20 seconds its a disaster.....

With KMS... maybe one or 2 seconds better...


But its forbidden to criticise "the holy Gnome Cathedral"... :)

"Fedora-boys" maybe can see great benefits...:D

---

### Post by MacUntu on 2009-06-22
That's why they stop bootchart at GDM start by default. :D

If you have a SSD just change readahead's profile behavior to not stop at GDM start, let it load the session, then stop readahead. Now you have a "complete" boot file in /etc/readahead - should be a lot faster.

But this thread was about nVidia and KMS, right? :D

---

### Post by plun on 2009-06-22
> **MacUntu said:**
> 
But this thread was about nVidia and KMS, right? :D

OK... we blame nVidia for everything...:D

Compiz, gnome-panel and applets, pulseaudio,,, everything is nVidias fault...

---

### Post by RAOF on 2009-06-23
Nouveau KMS update: with an updated nouveau-kernel-source, libdrm, and xserver-xorg-video-nouveau I have KMS on my laptop's nv4B chipset.  Unfortunately, trying to start X hardlocks the system, so it's not yet particularly useful :)

---

### Post by MacUntu on 2009-06-24
Great! Do you think it will be ready for 2.6.32?

---

### Post by cb951303 on 2009-06-24
> **inportb said:**
> Hm... nothing much, actually. I don't sit around idly as my laptop boots :o

KMS allows non-root X server which is a big security enhancement.
Also it will eventually improve suspend/resume functionality in laptop.
Flicker-free boot process/terminal changing etc. are just perks for me.

---

### Post by antiloop on 2009-07-06
Maybe it's time to convert to ATI again. Those 4890 cards just got a hefty price drop. :)

---

### Post by lithorus on 2009-07-06
> **antiloop said:**
> Maybe it's time to convert to ATI again. Those 4890 cards just got a hefty price drop. :)
Just for KMS? You have got to be kidding...

---

