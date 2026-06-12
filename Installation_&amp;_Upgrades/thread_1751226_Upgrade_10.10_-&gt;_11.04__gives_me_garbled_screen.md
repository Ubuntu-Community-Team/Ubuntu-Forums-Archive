---
title: "Upgrade 10.10 -&gt; 11.04  gives me garbled screen in X, and can't find old xorg.conf!"
date: 2011-05-06
forum: Installation &amp; Upgrades
---

### Post by rothloup on 2011-05-06
I just upgraded from 10.10 to 11.04. 

When I originally installed 10.10, everything worked fine, but I had to twiddle with xorg.conf to get my graphics card to use 2D accel (I stayed away from Compiz and 3D accel after a number of sudden freezes while I was working).  I slogged through many internet posts to figure out the right combination of accel options to use, and after many hours, I had a working xorg.conf file.

BUT, when I upgraded to 11.04, the screen was a garbled mess whenever I entered Xwindows.  My first instinct was to check xorg.conf and Xorg.0.log.  the install had replaced my xorg.conf with a new one, but my old one was nowhere to be found!  I figured out that this new KMS was having trouble setting things properly, so I disabled it.  Now I'm back to trying to figure out what accel options I need to put in my xorg.conf.   Not my idea of fun or time well spent (not anymore...it was fun in my younger days!)

So, I'm hoping that someone can help me answer some of the following questions:
[LIST]
[*]Is it possible for me to find my old xorg.conf somewhere?  I saw some xorg.confs in /etc/X11/ labeled as distro upgrade backups, but they were not my old ones...they were actually identical to the newly installed xorg.conf.  Perhaps it stuck the file somewhere else?
[*]I have an emachines m6809 with an ATI Radeon 9600 (RV350) graphics cards.  Can someone help me get KMS working properly so I don't even have to worry about an xorg.conf?  Note that these laptops have had ACPI issues, which I think KMS is dependent on.  (In fact, that's probably the root of my original problem)
[*]Can someone help me figure out what Accel options work best with this card?  Does someone have the same card (or even the same laptop!) with a working xorg.conf that they can share?
[/LIST]

Thanks for any help!  I am not at my computer right now, but I can post cmd line outputs (i.e. lspci) in a subsequent post.

---

