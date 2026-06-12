---
title: "Flash video Noticeable Improvement"
date: 2009-08-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Kai Summers on 2009-08-23
Has anyone else noticed if they're flash video has undergone a major improvement in terms of stability and fluidity of streams in Karmic, compared to other version of ubuntu?

I know some are reporting issues with it but for me It really is a joy now to watch videos in Full Screen!!! Perhaps they have specific driver issues but I'm really happy!

---

### Post by psyke83 on 2009-08-23
What graphics card/adapter and CPU do you use? I don't notice an improvement on my Intel 855GM chipset over Jaunty (after manually fixing MTRR registers).

---

### Post by Kai Summers on 2009-08-23
I've got Karmic on my Laptop which hasn't got the best specs in the world...

**Specs**
Intel Centrino Duo CPU
2GB memory
160GB hdd
Intel Mobile Express 945GT
Current flash version: LNX 10,0,22,87
Browser FF 3.5

So not really anything special...

---

### Post by psyke83 on 2009-08-23
> **Kai Summers said:**
> I've got Karmic on my Laptop which hasn't got the best specs in the world...

**Specs**
Intel Centrino Duo CPU
2GB memory
160GB hdd
Intel Mobile Express 945GT
Current flash version: LNX 10,0,22,87
Browser FF 3.5

So not really anything special...

Ok. Fullscreen Flash video was slower for you in Jaunty due to the MTRR range not being set for your graphics card's memory range (it's explained in the guide in my signature). This is fixed in Karmic's version of the kernel and intel driver.

Karmic's version of Flash is also outdated. If you want, remove your current package (flashplugin-installer/flashplugin-nonfree) and install the deb from: [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

---

### Post by nhasian on 2009-08-24
i've been pretty happy with flash since they came out with that alpha refresh of the 64 bit version of flash at the end of july.  its not in the repos though - you have to get it directly from adobe labs.

---

### Post by gnomeuser on 2009-08-24
On all my machines flash operates strangely, if there is sound (a rarity with it's horrid abuse of the ALSA API) then it's needlessly choppy and loads the CPU 100% - something that just shouldn't happen on a Core 2 Duo or any CPU for that matter.

The same youtube videos downloaded and played back in totem in the very same flash video format are flawless and smooth.

Flash is a painful painful experience and should be taken to the backyard to be put out of it's misery. Years and years of "bugfixes" have failed to improve it.

So no, I haven't noticed any improvement lately or ever.

---

### Post by Seventh Reign on 2009-08-24
Flash is, and always has been 100% flawless for me.  

Its Java that needs improved .. or removed completely ..

---

### Post by caeroe on 2009-08-25
> **Kai Summers said:**
> Has anyone else noticed if they're flash video has undergone a major improvement in terms of stability and fluidity of streams in Karmic, compared to other version of ubuntu?

I know some are reporting issues with it but for me It really is a joy now to watch videos in Full Screen!!! Perhaps they have specific driver issues but I'm really happy!

Flash has been great on my notebook for as long as I can remember, which is still using Jaunty x64.  It's been subpar on my desktop, and only very recently have I been able to watch fullscreen video on Ubuntu Karmic.  It still is choppy at times on my desktop.

It's not a hardware/bandwidth issue as my desktop dual boots with Win7 x64, not to mention being a much nicer system.  I feel it's my Nvidia card (8800GT 512mb), my notebook has an ATI card.  I tried so many different drivers, making sure to do clean installs.

---

