---
title: "fglrx copiz lag"
date: 2009-03-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by screaminj3sus on 2009-03-25
In 9.04 on my card (hd2600, fglrx from repo) compiz has a ridiculously slow lag when you unminimize a window, it was fine in previous versions of ubuntu and using the same 0.8.x version of compiz in fedora 10. the metacity compositer is even worse and suffers a massive performance hit in 9.04.

---

### Post by hcooh on 2009-03-29
Hello,

I encounter the same problem !
I have an ATI HD2600 Mobility and since jaunty I have some trouble unminimizing a window when desktop effects are on... it takes at least 2 sec !
And this appears on gnome AND kde !

Is there any fix ?

---

### Post by screaminj3sus on 2009-03-29
I have tried tweaking the hell out of my xorg.conf but nothing really helped. I think these beta drivers are just crappy and don't work very well at all with the  new xorg.

---

### Post by hcooh on 2009-03-30
Actually,
the same bug appears for me with openSUSE 11.1 with both fglrx and the free driver !
So it does not come from the fglrx.
(the bug only appears when desktop effects are enabled)

---

### Post by Marcham89 on 2009-04-09
Same problem here. I also have an ATI mobile card.

---

### Post by carrozza on 2009-04-09
Same card here (ATI Mobility Radeon HD 2600), same old story.

Many users complains about ATI performances in Jaunty but the simple answer is that _FGLRX drivers version 9.03 are NOT updated for the new X.org server in Jaunty_.

When FGLRX will make to 9.04 we will have back our good ATI speed.

---

