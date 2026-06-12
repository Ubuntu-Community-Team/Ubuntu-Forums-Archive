---
title: "Installing 64-bit over 32-bit - how to?"
date: 2018-11-03
forum: Installation &amp; Upgrades
---

### Post by vfr750 on 2018-11-03
Presently running 18.04 LTS, 32-bit variety, on my Thinkpad T60 ( T7200 which is 64-bit, I believe). Since 32-bit appears to be likely to be un-upgraded at some future date, I obtained a 64-bit installation stick to convert to 64-bit. Given that 32-bit is already installed, what (if anything) do I need to do to ready my T60 for the installation? This may be a non-issue, but I'd like some confirmation of that. TIA! 

Ed

---

### Post by Autodave on 2018-11-03
From what I found, that machine only has 1 gig RAM.  If that is true, you are better sticking with the 32 bit until it is no longer supported.  

What version are you running: Ubuntu, Xubuntu, Lubuntu, ??

---

### Post by him610 on 2018-11-03
How about showing, between the code tags, the results of ```
free && inxi -F
```

---

### Post by vfr750 on 2018-11-03
Thanks for the quick response, AutoDave.

I'm blessed with 2GB RAM. Is that still insufficient, or marginal, for 64-bit Ubuntu (which is the flavor I'm running)?

---

### Post by vfr750 on 2018-11-03
Ooops! I Misspoke - I'm running 32-bit Ubuntu presently.

---

### Post by vfr750 on 2018-11-03
Thanks, Him610. I'll be back in the morning with the results of your suggesting.

---

### Post by Mark Phelps on 2018-11-03
Your post had a statement about "convert to 64-bit" -- as if you were looking for a way to replace the 32-bit OS components with 64-bit and leave the rest intact.

That would be essentially the same thing as an "in-place upgrade" and that simply is not possible.

You would have to reinstall from scratch with the 64-bit version.

---

### Post by Autodave on 2018-11-03
a 32 bit system running 2 gigs of RAM is goin g to run about the same speed as a 64 bit system with 1 gig of RAM.  You would lose some speed switching to 64 bit.

Having said that, Ubuntu is rather heavy to be running on 2 gig.  Xubuntu would be a better choice since it is much lighter than Ubuntu.  Lubuntu is lighter yet, but with a rather (in my opinion) dull and bland desktop.

---

### Post by oldfred on 2018-11-03
I have run 64 bit Ubuntu on my 2006 Laptop with 1.5GB of RAM. But full Ubuntu was slow and I installed fallback or now gnome-panel. It is the old menu system similar to what Ubuntu had before Unity. But now updated.

With only 1.5GB of RAM, system would start using swap if I loaded more than one larger app and several smaller apps. Or I ran Firefox with just a couple of tabs and terminal & Zim ok. But if I then tried to open something needing LibreOffice, system would turn gray and stall while writing to swap. Laptop also had slow HDD which did not help. But most of my use was ok with just the 1.5GB of RAM.

---

### Post by Impavidus on 2018-11-04
A 64 bit system uses slightly more memory to do the same tasks than a 32 bit system and only has real advantages when you have more than about 4GB of memory. But, as you rightly observed, support for 32 bit is dwindling.

There's no upgrade from 32 bit to 64 bit. You have to use a fresh install, but it may be possible to keep all your user documents and settings. If you have a separate /home partition, you can install using manual partitioning, select /home as the mount point for your current /home partition and make sure you don't format it. If you have no /home partition now, the best way to go is to make a backup of your /home directory on an external drive and restore it after install.

There's no advantage in replacing your current 32 bit system with an 64 bit system of the same release, just to make sure you can later upgrade to the next release. Just install the 64 bit version of the next release when it's released.

With just 2GB of memory you can better use one of the lighter flavours of Ubuntu.

---

### Post by vfr750 on 2018-11-04
Thanks all! The gist of what I'm reading is that I'm better off leaving things as they are (not trying to run 64-bit Ubuntu) with this machine. I had made a copy of the results of " inxi -F " as Him610 suggested, in prep to paste into a reply here, but when I started my browser up, I got a black box (no text or images) which I could close by clicking in the upper right corner where I estimated the "X" would be. Duplicated this a couple of times, doesn't matter what the application is, any attempt to run an additional application results in a black box for it. 

So, I'm diverted from the original question, and after gathering my wits, will start another thread over in "newbies" I guess. This may actually be proof that the RAM even at 2 GB is inadequate. This "black box" thing started with this up-grade (18.04 LTS), I think. The laptop is more a plaything, and not used for much more than browsing and music, so I may wind up going back to an earlier iteration of Unbuntu, or to Lubentu. 

Again, thanks for all the advice and help!

Ed

---

