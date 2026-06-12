---
title: "whats new in lucid?"
date: 2010-01-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Dayofswords on 2010-01-21
today i was bored and i download the lucid iso, ran in virtualbox and well.

i hardly noticed a difference from 9.10, the shutdown was just a little different, but that about i saw, plus gimp was there.

what exactly is new in lucid?

---

### Post by exploder on 2010-01-21
So far most of the changes are under the hood. Newer kernel, gnome, device kit, Plymouth takes the place of XSplash, hal removed,etc. Pitivi Video Editor was added and application updates will come before the final release. The Ubuntu Software Center is getting more refined. So far the LTS is looking very good.

---

### Post by Yofel on 2010-01-21
See [https://wiki.ubuntu.com/LucidLynx](https://wiki.ubuntu.com/LucidLynx)
especially the links to the blueprints and the technical overview.

---

### Post by philinux on 2010-01-21
> **Dayofswords said:**
> today i was bored and i download the lucid iso, ran in virtualbox and well.

i hardly noticed a difference from 9.10, the shutdown was just a little different, but that about i saw, plus gimp was there.

what exactly is new in lucid?

One major thing is I'm booting in a about 35 seconds. Thats nearly twice as fast Karmic.
Have a read.
[http://www.ubuntu.com/testing/lucid/alpha2](http://www.ubuntu.com/testing/lucid/alpha2)

---

### Post by xir_ on 2010-01-22
> **philinux said:**
> One major thing is I'm booting in a about 35 seconds. Thats nearly twice as fast Karmic.
Have a read.
[http://www.ubuntu.com/testing/lucid/alpha2](http://www.ubuntu.com/testing/lucid/alpha2)

with or without the 45 second delay added to bootchart on karmic?


For me the biggest feature is going to be opensource 3D graphics drivers for ati and nvidia chip-sets.


There is meant to be something to do with social from the start, goodness only knows what that means, but we just gained 50 megs on the live CD's and that's a whole load of social.


Also there may be a new gtk with some cool alpha blur features enabled.

---

### Post by uBeer on 2010-01-22
> **xir_ said:**
> with or without the 45 second delay added to bootchart on karmic?

Ehm, he said 35 seconds, so probably without the 45 second delay... :popcorn:

---

### Post by 3rdalbum on 2010-01-22
My netbook is booting very fast too.

I've also noticed that the fsck visual has changed too. Instead of getting a textual representation of the progress of fsck, you get an orange progress bar with no text at all. If your system needs to reboot afterwards, it just does it.

Surprised the heck out of me the first time it happened, and then I realised what was going on. Well, I assume it's fsck.

---

### Post by xir_ on 2010-01-22
> **uBeer said:**
> Ehm, he said 35 seconds, so probably without the 45 second delay... :popcorn:

could be... or alternatively not, that's why i asked

---

### Post by VMC on 2010-01-22
> **3rdalbum said:**
> My netbook is booting very fast too.

I've also noticed that the fsck visual has changed too. Instead of getting a textual representation of the progress of fsck, you get an orange progress bar with no text at all. If your system needs to reboot afterwards, it just does it.

Surprised the heck out of me the first time it happened, and then I realised what was going on. Well, I assume it's fsck.

I wondered what that orange progress bar was that I only see once in awhile. How did you figure out it came from fsck?

I saw it once on Kubuntu and yesterday from Ubuntu.

---

### Post by jmmL on 2010-01-22
> **xir_ said:**
> could be... or alternatively not, that's why i asked

You can't have a 35 second boot that includes a 45 second wait.
Anyway, the version of bootchart in lucid is now much cleverer and stops itself once a particular desktop process has been started (gnome-panel, perhaps?). So now the times reported in bootchart are an accurate representation of the time taken to go from grub to a usable desktop.

---

### Post by philinux on 2010-01-22
Just got 25.81 seconds. Thats with plymouth too.

---

### Post by inportb on 2010-01-22
I don't really care for Plymouth (and I haven't seen Plymouth on this system yet to tell the truth), but KMS/flickerfreeboot for Radeon is amazing. The VT-switching experience is pretty impressive.

---

### Post by UbuWu on 2010-01-23
> **3rdalbum said:**
> My netbook is booting very fast too.

I've also noticed that the fsck visual has changed too. Instead of getting a textual representation of the progress of fsck, you get an orange progress bar with no text at all. If your system needs to reboot afterwards, it just does it.

Surprised the heck out of me the first time it happened, and then I realised what was going on. Well, I assume it's fsck.

It is probably ureadahead reprofiling.

---

