---
title: "ATI X1950XT + 6.10 = not working?"
date: 2006-12-27
forum: Installation &amp; Upgrades
---

### Post by ModemMisuser on 2006-12-27
I just upgraded my video card to an ATI X1950XT card (Sapphire brand) so I thought I should also upgrade my Ubuntu installation from 6.06 to 6.10.  Downloaded + burned the 6.10 AMD64 CD and booted it.  

When it flips over to graphics mode, the graphics are ... garbled.  Very hard to describe, but definitely not readable and not working.  Is this a known issue?  Is there a fix?  Search provided no answers.

I also tried "Safe Graphics Mode" --> same result.

---

### Post by pay on 2006-12-28
I've always had problems with my x800pro and xorg7.1. Basically if you have an ati card and want to use Linux be prepared for disappointments (been waiting for aiglx support for awhile....).

---

### Post by ModemMisuser on 2006-12-28
So... No way to get this working?  The 1950 cards are getting pretty popular, there must be a solution! :(

---

### Post by wpshooter on 2006-12-28
Is there an ALTERNATE (text based) CD version for your machine type ?

If so, have you tried it ?

---

### Post by ModemMisuser on 2006-12-28
> **wpshooter said:**
> Is there an ALTERNATE (text based) CD version for your machine type ?

If so, have you tried it ?


Hmmm, there might be.  I can try that, but what would be the point?  I don't really have a use for the OS without X. :P

---

### Post by bulldog on 2006-12-28
> **ModemMisuser said:**
> Hmmm, there might be.  I can try that, but what would be the point?  I don't really have a use for the OS without X. :P


After the install you can install drivers for your graphics,something you can't do running the live cd.

---

### Post by commonplace on 2006-12-29
> **ModemMisuser said:**
> Hmmm, there might be.  I can try that, but what would be the point?  I don't really have a use for the OS without X. :P

Just the installation itself is text-based, not the final result. The text-based installation still installs whatever you want, including X/Gnome.

You'll probably find out, though, that the problem is with ATI's Linux support (or, rather, the lack thereof). I have an ATI x700 card and really, really wish I had an nVidia card.

/Kevin

---

### Post by ModemMisuser on 2006-12-29
Actually, I just ended up booting my existing 6.06 installation, letting the X server die, then installing the ATI drivers and all is well. :p

---

### Post by jcushing on 2007-02-23
what drivers did you install?  i have a 1950xt also and there didnt appear to be any drivers avalible at all for any 1950 series cards on ati's site.

---

