---
title: "Why Intrepid is so SLOW compared to Hardy"
date: 2008-09-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by grigio on 2008-09-16
Intrepid: Xorg 1.4.0.90 + fglrx
Hardy:    Xorg 1.4.0.90 + fglrx
[http://global.phoronix-test-suite.com/index.php?k=profile&u=utente-23748-25836-21064](http://global.phoronix-test-suite.com/index.php?k=profile&u=utente-23748-25836-21064)

---

### Post by danniel on 2008-09-16
Maybe because Intrepid is still an **Alpha** version? You should do this test again after a couple of months and then ask questions (if any).

---

### Post by Nullack on 2008-09-16
Hmm I dunno. Debug package compiles arent installed in Ubuntu alphas by default and the most significant upstream projects are at release status or near release status such as where gnome 2.23 is at now.

---

### Post by gnomeuser on 2008-09-16
> **Nullack said:**
> Hmm I dunno. Debug package compiles arent installed in Ubuntu alphas by default and the most significant upstream projects are at release status or near release status such as where gnome 2.23 is at now.

That doesn't mean our kernel e.g. might not have debug stuff enabled to weed out bugs. Every major distribution does this during the development stage I would not be surprised if Ubuntu did as well. The impact of slab debug e.g. is quite significant.

There is also the concern that Intrepid is fast moving, it is e.g. very hard to keep a preload cache updated and effective if packages are updated every day. This has an impact on certain kinds of performance.

All in all it is most fair to compare Hardy to Intrepid at the earliest when it hits RC stage and preferredly after release on a fresh install of both platforms.

---

### Post by Calmatory on 2008-09-16
Test conditions are far from identical. For example OpenGL driver differs. GCC compiler differs(shouldn't make any difference in practice tho) and the worst of all: The test suite differs. Easier to run 100 meters on a solid ground than on a muddy and slippery ground. :)

Edit: Also, tests are ran by an unknown user. It might be that he messed something up intentionally or not. But as it has been said already, the Intrepid is at it's alpha stage yet. Things may change, big time. But I suspect it is the poor and immature driver with Intrepid. ATI's drivers.... :P

---

### Post by Nullack on 2008-09-17
> **gnomeuser said:**
> That doesn't mean our kernel e.g. might not have debug stuff enabled to weed out bugs. Every major distribution does this during the development stage I would not be surprised if Ubuntu did as well. The impact of slab debug e.g. is quite significant..

I have not seen any items in the GIT logs of the kernel team about this and I went onto IRC to ask - the response was there isnt debug stuff in the default kernel builds for Intrepid Alphas.

This requires a more serious look.

---

### Post by RAOF on 2008-09-17
What?  You mean there's an actual benchmark suite available?  Sweet!

---

### Post by grigio on 2008-09-18
> **Calmatory said:**
> 
Edit: Also, tests are ran by an unknown user. It might be that he messed something up intentionally or not. But as it has been said already, the Intrepid is at it's alpha stage yet. Things may change, big time. But I suspect it is the poor and immature driver with Intrepid. ATI's drivers.... :P

The unknown user is **me** and I have no advantage to publish fake results.. If you have a differnt comparison post it!

The Catalyst drivers should be 8.7 and 8.8, but I don't think this is only cause for a so huge difference.

---

### Post by BackwardsDown on 2008-09-18
Too bad it does not run on gutsy (it needs libc6), so I could not test.

---

### Post by Nullack on 2008-09-18
Lots of other people still can betwen Hardy and Gutsy:)

---

