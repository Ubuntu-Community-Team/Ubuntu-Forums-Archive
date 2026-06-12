---
title: "No Intrepid daily-live build for Power PC"
date: 2008-09-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jtappin on 2008-09-02
I see that on the port section of cdimage.ubuntu.com, there have not been any daily builds of the Intrepid daily-live cd images since mid-July (and even there only the directories remain).

Is there a technical reason for this or is it simply that there isn't enough manpower/computer power to do them?

---

### Post by stream303 on 2008-09-05
I forget now if a similar situation existed for Hardy since I always favored the "alternate" installer anyway.

I don't know about the live-cd situation, but pretty recent builds of intrepid are there in the plain old "daily" directory.  If you decide to go this route, maybe hang tight for the latest Alpha scheduled to come out on Sep 5th I believe...

---

### Post by jtappin on 2008-09-05
I generally prefer the alternate too, but I upgraded my G3 iBook from Hardy, and now I can only get 800x600 resolution no matter what I try, so I'd like to try from a live-cd to see if there's some "legacy" cruft that's breaking things before I do a full re-install.

As for point releases (e.g. Alpha 5) my recollection is that there are none for ports, only for the main "official" platforms.

---

### Post by ubuntubrian on 2008-09-14
> I'd like to try from a live-cd to see if there's some "legacy" cruft that's breaking things before I do a full re-install.

exactly what I wanted to do but I ended up trying the alternate install cd and it wouldn't complete on my Lombard powerbook.I edited my sources.list to all intrepid and apt upgraded after updatemanager wouldn't complete a dist-upgrade. things sort of worked but now I get an "illegal instruction" error with all gnome apps and they crash. 
KDE apps work fine so maybe it's a gtk thing. I keep running dist-upgrades with apt-get (as synaptic and update manager won't run) and I'm hoping by Beta it may self resolve. A live cd would have been helpful. Luckily it's my play box.

---

### Post by jtappin on 2008-09-15
> **ubuntubrian said:**
> exactly what I wanted to do but I ended up trying the alternate install cd and it wouldn't complete on my Lombard powerbook.

I think Friday's daily alternate (at least) has a bad cdrom driver. It booted from the CD but then the booted system said that there was no CD on the system! 

I'm not sure if this is the Hardy IDE problem again in some form or just a CDROM driver snafu.

---

