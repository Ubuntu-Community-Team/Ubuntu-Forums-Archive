---
title: "ATI driver installation, dual monitors"
date: 2005-07-26
forum: Installation &amp; Upgrades
---

### Post by neylitalo on 2005-07-26
I have a ATI Radeon 9800 video card, and I need to set it up to use dual monitors. I read somewhere on this forum not to use the drivers provided by ATI, but to use the ones in linux-restricted-modules. However, after getting my kernel all set up and linux-restricted-modules, I have no clue where to go from here. Any and all help is appreciated.

---

### Post by autocrosser on 2005-07-26
First--do you have dual monitors working right now?? There are two ways to do it if you don't--(well-three)

1. FBMerged with one card--has a slightly higher frame rate than the other option--downside is that apps sometimes place themselves in the center of the two screens (read games here).

2. Xinerama with two cards--slightly slower, but much more accurate. Everything goes where it should--but at a hit of about 50/100fps (depends on your system).

The other thing--Xorg has no DRI support for any cards newer than 9200 as of this release (6.8.2)--so, your fps won't be blazing--at least until Breezy is out (at least that is what I hear, based on the version of Xorg it will be using)--So, you will not have acceleration in any case unless you want to gamble on the ATI drivers (I've heard both pro & con--I want a stable system & would reboot to my "other" OS for my games anyway)--either FBMerged or Xinerama will work well--& FBMerged will have acceleration within the next couple of revisions of Xorg....

I can post both of the .conf files--but I have posted them elsewhere on the site--just look back thru my prior posts--I'm using Xinerama right now, the wife likes some of the games i've downloaded & that gets her "liking" Linux :wink--but I'm going to look at FBMerged again when Xorg version 7 is out--

Hope this answers your question---

Cheers!!
Dean

---

