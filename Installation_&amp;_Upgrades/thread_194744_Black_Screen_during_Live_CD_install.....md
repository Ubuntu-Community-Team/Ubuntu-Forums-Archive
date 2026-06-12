---
title: "Black Screen during Live CD install...."
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by gennipher on 2006-06-11
I am attempting to run Ubuntu's Live CD on my iMac G3 computer, 256RAM, 10Gig HD, 400MHz processor (that sounds about right...).  When I startup from the CD I get the boot prompt, and type live-powerpc to start the install.  The CD then loads to the Ubuntu logo, and starts to run through certain things, each saying OK.  After about 3 minutes of that the screen goes black and I eventually hear the Ubuntu chime.  I can still hear the CD doing stuff but it has been now 45 minutes since the screen went black.  Is this indicative of a video driver issue?  I tried from the boot prompt doing live video=vesa, with the same results.  A point in the right direction would be much appreciative.

---

### Post by cubensis on 2006-06-11
I am also having the same problems, I get to the Ububtu splash screen, I pick the first option, then it gives me a list of things that are loading, then either a screen saying "Loading Kernal, OK, Loading Linux", or this screen.
System is a Dell XPSgen2, 512mb ram/60gb hd, geforce 6800 go. 2ghz Pentium M

---

### Post by gennipher on 2006-06-12
I've switched to my iBook G3 now and have successfully installed Ubuntu without any problems.  I'm sure that it was just a video driver issue, although I would like to know what would have fixed that for my iMac.

On a side note, my iMac is now having a Kernel Panic.  This is going to be a wonderful Monday...

---

### Post by jitesh on 2006-06-12
It could very well be a video card issue, When installing try using the lowest resolution.  This could be done by typing the following command at bootup :

"linux vga=771"

---

