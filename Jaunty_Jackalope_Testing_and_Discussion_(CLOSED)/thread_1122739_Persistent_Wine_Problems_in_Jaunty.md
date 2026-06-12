---
title: "Persistent Wine Problems in Jaunty"
date: 2009-04-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by scradock on 2009-04-11
Is anyone else having problems with screen redraws in Wine on Jaunty? It happens with compiz enbled OR with metacity plus compositing. Without compositing, screen redraws are fine, if perhaps a bit slow. I'm using the opensource ati/radeon drivers (ATI Radeon Xpress 200M 5955 chipset).

The symptoms are slow and jerky redraws, then blue patches start to appear instead of the correct contents, then Wine crashes.

Identical operations in Intrepid are perfectly fine; it's not the hardware.

I've reported the bug - #314205 (back in January). No sign of any action, just the comment that "Wine has always had problems with compiz", as if neither was important enough to bother about.

I left it, thinking it would surely be fixed by Beta - but here we are and it's still there.

Any ideas?

---

### Post by dino99 on 2009-04-11
> **scradock said:**
> Is anyone else having problems with screen redraws in Wine on Jaunty? It happens with compiz enbled OR with metacity plus compositing. Without compositing, screen redraws are fine, if perhaps a bit slow. I'm using the opensource ati/radeon drivers (ATI Radeon Xpress 200M 5955 chipset).

The symptoms are slow and jerky redraws, then blue patches start to appear instead of the correct contents, then Wine crashes.

Identical operations in Intrepid are perfectly fine; it's not the hardware.

I've reported the bug - #314205 (back in January). No sign of any action, just the comment that "Wine has always had problems with compiz", as if neither was important enough to bother about.

I left it, thinking it would surely be fixed by Beta - but here we are and it's still there.

Any ideas?

Have you the last version .19 ?

---

### Post by scradock on 2009-04-11
last version of what? I'm using the ubuntu-supplied Wine 1.0.1-0ubuntu6, Jaunty up-to-date. If there's a newer version of Wine that works with Jaunty I'd like to know about it......

---

### Post by forcecore on 2009-04-11
easy to get wine from here:
[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

---

### Post by scradock on 2009-04-11
Thanks. I just did that, and can confirm that the same symptoms persist with the 1.1.19 beta version. Without compositing it's OK, with compositing it fails to redraw correctly, and eventually crashes.

---

### Post by amano on 2009-04-11
It is probably related to the ATI driver that you are using. It seems that you have to turn off compositing when using Wine. The graphics drivers have been updated to work with the new x.org release and this might have been a regression.

I am on nvidia here, so I can't test this on my machine.

---

### Post by novafluxx on 2009-04-11
Just want to throw in my vote for using the latest Wine, instead of the 1.0.1 'stable' one included with Ubuntu

---

### Post by scradock on 2009-04-12
Thanks, everyone! It seems that this is a small facet of a much bigger problem due to the switch to xserver-xorg 1.6. In my case the open-source x-x-video-ati drivers are not handling OpenGL calls properly with the compositing window managers. So it's linked to the ongoing problems with Googleearth, for instance. At least there isn't a binary blob (fglrx) or a proprietary app (Googleearth) in my case, so maybe the situation will improve.

I'm assured that this is not a Wine problem - the Wine team will not be fixing anything. It's not a compiz problem - and it's not an ATI (fglrx) problem. This is something the OS developers can fix. 

What bothers me is why Ubuntu takes these lurches into the future before all the bits are in place. Pulseaudio (again????) - xserver-xorg 1.6 - ext4 - with progress like this we shall have a version that won't do any of the basic stuff that Hardy was doing well last year.   /rant

---

### Post by Locke_99GS on 2009-04-12
I don't have ATI, and have been using Jaunty only in a VM, but my buddy has a laptop with ATI and Intrepid. He is using fglrx, latest Wine from WineHQ, and has the exact same problems you mention. Never having these sorts of problems myself, I had never even thought to disable compositing. So the problem exists even in Intrepid.

I only hope disabling compositing will fix his flickering Wine apps. He can live with that.

> **scradock said:**
> What bothers me is why Ubuntu takes these lurches into the future before all the bits are in place. Pulseaudio (again????) - xserver-xorg 1.6 - ext4 - with progress like this we shall have a version that won't do any of the basic stuff that Hardy was doing well last year.   /rant

Ahh, I have been complaining to myself about it for some time as well.

---

