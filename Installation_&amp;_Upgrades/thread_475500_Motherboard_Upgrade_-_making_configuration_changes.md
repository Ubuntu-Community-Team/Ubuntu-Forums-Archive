---
title: "Motherboard Upgrade - making configuration changes"
date: 2007-06-16
forum: Installation &amp; Upgrades
---

### Post by w2vy on 2007-06-16
I installed Feisty as dual boot on a second disk on my desktop at work.

I was considering using it full time, but there are a couple of appliations I need that I can't run.
(yes I know about wine; but I am sure my IT guy would really whine about it...)

So he got me a new system and I moved the hard disk into it.

I booted from the install disk and copied xorg.conf to get the display working.

From time to time the system locks up, or hangs.

By hitting power (get shutdown menu) I can get it to come out, or maybe by installed a CD.

The real question buried here is: What files should I look at for the rest of the system configuration when booted in the install cd?

tom

---

### Post by Pumalite on 2007-06-16
> **w2vy said:**
> I installed Feisty as dual boot on a second disk on my desktop at work.

I was considering using it full time, but there are a couple of appliations I need that I can't run.
(yes I know about wine; but I am sure my IT guy would really whine about it...)

So he got me a new system and I moved the hard disk into it.

I booted from the install disk and copied xorg.conf to get the display working.

From time to time the system locks up, or hangs.

By hitting power (get shutdown menu) I can get it to come out, or maybe by installed a CD.

The real question buried here is: What files should I look at for the rest of the system configuration when booted in the install cd?

tom

Hi there,

Look at these:
/etc/fstab
/etc/mtab
/etc/hdparm

Cheers.

---

### Post by wpshooter on 2007-06-16
IMO, you will send much less time and get better results, if you just re-install the O/S.

---

### Post by w2vy on 2007-06-17
I am not surprised...

It there an easy way to generate a list of all the packages I used apt-get to install?

I am sure  can make a list of the ones installed and diff between old and new...

tom

---

