---
title: "Installing ubuntu on Zotac Zbox with Atom 510 and Next Gen Ion...Suggestions?"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by Doctor_Gonzo on 2010-05-16
So I just ordered the ZOTAC ZBOX HD-ID11 ION2 Atom D510 System, and will be getting it wednesday...As I didn't order an OS I'm gonna throw Linux on it, preferably Ubuntu.

What I'm wondering is which would be the best edition for this system? Ubuntu, Studio, UNE?

I'm going to be using it as a media center connected to my big *** flatscreen, but was considering throwing wine on it as well for occasional light gaming.

Has anyone put set one of these up yet and if so, what was your experience?

I'm open for suggestions!

---

### Post by mistichu on 2010-05-16
go with studio for media or you could just choose ubuntu and install everything needed to do it ,
 
my estimated time on setting that up would be maybe 45 mins cause everything on studio is in the repo and you could search the cache for stuff to add there are some programs /frameworks for media center esque stuff 
 
apt-cache search media 
apt-cache search media center 
 
should show you a bunch of results

---

### Post by Doctor_Gonzo on 2010-05-16
32 or 64 bit?

---

### Post by movieman on 2010-05-16
There's no good reason not to go 64-bit unless perhaps you're only going to install 1GB of RAM.

I have a Zotac Ion-1 board for my MythTV frontend and it runs standard Ubuntu with xbmc as the media player software. If I'd been intending to use the MythTV frontend I'd have installed Mythbuntu to ensure the same versions of MythTV were on both systems.

The Ion-1 plays pretty much all my video files perfectly with VDPAU acceleration, but it does struggle with some of my 1080i MPEG-2 files for some reason. I'd presume the Ion-2 would manage that OK since it's significantly more powerful.

---

### Post by mistichu on 2010-05-16
> **movieman said:**
> There's no good reason not to go 64-bit unless perhaps you're only going to install 1GB of RAM.
 
I have a Zotac Ion-1 board for my MythTV frontend and it runs standard Ubuntu with xbmc as the media player software. If I'd been intending to use the MythTV frontend I'd have installed Mythbuntu to ensure the same versions of MythTV were on both systems.
 
The Ion-1 plays pretty much all my video files perfectly with VDPAU acceleration, but it does struggle with some of my 1080i MPEG-2 files for some reason. I'd presume the Ion-2 would manage that OK since it's significantly more powerful.
how many slots for memory are there ? if theres two i would just pop 2 2gigs in if thats possible if not i would still go with 64 bit just because 64 bit can handle more memory and you can upgrade. that is if your processor is 64 bit other wise youll have to choose 32 bit the only difference is that 64 bit can process more data :)
 
oh and movie man 32 bit can handle 2gigs of ram at a time anything else is ignored

---

### Post by movieman on 2010-05-16
> **mistichu said:**
> oh and movie man 32 bit can handle 2gigs of ram at a time anything else is ignored

32-bit can handle up to 4GB without PAE and I think 128GB with PAE; but 64-bit code does typically use a few percent more memory due to larger pointer sizes, and with only 1GB of RAM you need all the help you can get these days :).

My frontend is running 64-bit, but it has 4GB of RAM (though only about 3.2GB are visible in Linux).

---

### Post by mistichu on 2010-05-16
> **movieman said:**
> 32-bit can handle up to 4GB without PAE and I think 128GB with PAE; but 64-bit code does typically use a few percent more memory due to larger pointer sizes, and with only 1GB of RAM you need all the help you can get these days :).
 
My frontend is running 64-bit, but it has 4GB of RAM (though only about 3.2GB are visible in Linux).
 lol that is weird thx 4 info but srsly is it os limitations then ? xp only recongnizes 2gigs on 32 bit as far as i know and ubi will recongnize more i know but lol it doesnt matter
 
op just do whatever you feels best that your computer will handle:guitar:

---

