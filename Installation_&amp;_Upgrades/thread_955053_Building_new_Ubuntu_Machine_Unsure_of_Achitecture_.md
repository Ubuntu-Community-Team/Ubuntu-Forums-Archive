---
title: "Building new Ubuntu Machine Unsure of Achitecture Type"
date: 2008-10-21
forum: Installation &amp; Upgrades
---

### Post by webbed on 2008-10-21
Hi Guys,

I am looking at building a new machine based around the Intel Core 2 Duo. I've seen a lot of information on a lot of different forums but this has just confused me (my post probably looks that way too).

With the machine I am looking at doing a fair bit of web design/programming work currently I use the following programs in Ubuntu 8.04 (i386 - my old machine).

[LIST]
[*]Aptana (Java based programming IDE)
[*]Photoshop CS2 (Currently running on Wine 1.1.5)
[/LIST]

I also play World of Warcraft on my machine and want to be able to do the following with it.

[LIST]
[*]5.1 Surround Sound (via Pulseaudio)
[*]Record sound (currently been unable to set with my SoundBlaster Audigy Value card)
[/LIST]

What I would like to know is?

[LIST=1]
[*]Which version of Ubuntu is best for an Intel Core 2 Duo processor (i386 or x64)?
[*]Is the Intel Core 2 Duo a 32bit or 64bit processor?
[*]Would the x64 version have any issues running 32 bit apps like World of Warcraft, Photoshop, Aptana, etc?
[*]Are there any recommendations for sound cards to use under Linux to achieve 5.1 surround, with sound recording support (want to use Pulseaudio as well so that multiple programs can access the sound card at once.)?
[/LIST]

---

### Post by pytheas22 on 2008-10-21
The Core 2 Duo is a 64-bit chip.  Based on the information you give, I'd definitely recommend using 64-bit Ubuntu.  Processing time is a bit faster on 64-bit, and more importantly you can use more RAM, which is probably important to you if you're doing heavy-duty sound processing and gaming.

32-bit Windows programs in wine will work fine on 64-bit Ubuntu without any special effort on your part.

That said, 32-bit Ubuntu will work fine on a Core 2 Duo as well, just a bit slower and capped at four gigabytes of memory.  But 64-bit is probably better for you.  The only reason that I'd ever tell anyone not to use 64-bit is if they have to use ndiswrapper to drive a wireless card (few people still need ndiswrapper these days) and no 64-bit Windows driver is available.  If you don't use ndiswrapper, don't worry about this.

Unfortunately, I don't know much about sound (I'm using a card that's 10+ years old in my year-old Core 2 Duo machine, because it still works and I didn't want to buy a new card for no reason), but others will surely be able to make suggestions.  The people in the multimedia subforum would be particularly knowledgeable.

---

