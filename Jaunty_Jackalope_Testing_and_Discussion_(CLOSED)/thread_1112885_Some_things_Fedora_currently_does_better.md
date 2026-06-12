---
title: "Some things Fedora currently does better"
date: 2009-04-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Yashiro on 2009-04-01
After a spin with the latest F11 beta here's what I though were some immediately obvious areas for Ubuntu improvement.

_Video performance._
No idea how this is possible but on an ati 4850, both running the latest free driver, F11 beta is noticeably better than Jaunty. Faster at basic things like scrolling and with less artifacts generally. Don't quite understand why.
	
_Better user switching applet._
I just prefer it. It fits with the system, doesn't look out of place and doesn't mess with the gnome dialogs.
It's just more consistent than the ubuntu fusa.


I only meant to post about the video issue to be honest.

---

### Post by Tirk on 2009-04-01
And all of this is nothing for me since somehow fonts in Fedora look so ugly for me I cannot look at it, I don't know why, tried many things.
Dangerous thread you have opened. Perhaps it should be closed immediately;)

---

### Post by Yashiro on 2009-04-01
Yes, Fedora default font rendering is nasty. You can patch it I heard. You shouldn't have to do this though, really.
I was curious about the slight speed difference in the radeon driver mainly. I've trimmed my post so it's more obvious.

---

### Post by gnomeuser on 2009-04-01
> **Yashiro said:**
> After a spin with the latest F11 beta here's what I though were some immediately obvious areas for Ubuntu improvement.

_Video performance._
No idea how this is possible but on an ati 4850, both running the latest free driver, F11 beta is noticeably better than Jaunty. Faster at basic things like scrolling and with less artifacts generally. Don't quite understand why.



Fedora consistently has a newer X stack and set of drivers than Ubuntu. Additionally the lead Radeon developer works for Red Hat so we have a very short loop between bug filing and bug fixes being available.

F11 has KMS, DRI2 and improved 3D support for ATI cards, it all pays off.

---

### Post by gnomeuser on 2009-04-01
> **Yashiro said:**
> Yes, Fedora default font rendering is nasty. You can patch it I heard. You shouldn't have to do this though, really.
I was curious about the slight speed difference in the radeon driver mainly. I've trimmed my post so it's more obvious.

I never really had problems with fonts in Fedora. However if you want to get the very best, and sadly patent encumbered, freetype has to offer in Fedora.

first go to rpmfusion.org and enable the repos for the relevant platform. Then install freetype-freeworld and go to the look and feel entry in the System->Preferences menu, select the fonts tab and set it to using subpixel hinting (works on any modern flat screen monitor and many modern CRTs as well).

---

### Post by Tirk on 2009-04-01
> **gnomeuser said:**
> 
first go to rpmfusion.org and enable the repos for the relevant platform. Then install freetype-freeworld and go to the look and feel entry in the System->Preferences menu, select the fonts tab and set it to using subpixel hinting (works on any modern flat screen monitor and many modern CRTs as well).

I did it exactly as you said and I installed corefonts. Still in my case F10 fonts are no match to Ubuntu look. Believe me I tried different settings and so on. Still Ubuntu had clearer and better fonts no matter what.

---

### Post by kj74 on 2009-04-01
> **gnomeuser said:**
> I never really had problems with fonts in Fedora. However if you want to get the very best, and sadly patent encumbered, freetype has to offer in Fedora.

first go to rpmfusion.org and enable the repos for the relevant platform. Then install freetype-freeworld and go to the look and feel entry in the System->Preferences menu, select the fonts tab and set it to using subpixel hinting (works on any modern flat screen monitor and many modern CRTs as well).

That package is useless, it has absoluntely no effect in font rendering.

---

### Post by FuturePilot on 2009-04-01
> **gnomeuser said:**
> I never really had problems with fonts in Fedora. However if you want to get the very best, and sadly patent encumbered, freetype has to offer in Fedora.

first go to rpmfusion.org and enable the repos for the relevant platform. Then install freetype-freeworld and go to the look and feel entry in the System->Preferences menu, select the fonts tab and set it to using subpixel hinting (works on any modern flat screen monitor and many modern CRTs as well).

> **Tirk said:**
> I did it exactly as you said and I installed corefonts. Still in my case F10 fonts are no match to Ubuntu look. Believe me I tried different settings and so on. Still Ubuntu had clearer and better fonts no matter what.

> **kj74 said:**
> That package is useless, it has absoluntely no effect in font rendering.

This is because Cairo and Xft both have to be compiled with the patches for the subpixel rendering. If they aren't it doesn't matter what fonts you install they will never be antialiased.

I've seen the same problem with Suse and it's because they simply don't compile cairo and xft with the necessary patches for the subpixel rendering. This is one of the things that has been a turn off for me on other distros. Yeah it may sound silly, pfft font rendering, but after using Ubuntu's beautiful subpixel font rendering I simply can't use anything else.

---

### Post by kj74 on 2009-04-01
> **FuturePilot said:**
> This is because Cairo and Xft both have to be compiled with the patches for the subpixel rendering. If they aren't it doesn't matter what fonts you install they will never be antialiased.

I've seen the same problem with Suse and it's because they simply don't compile cairo and xft with the necessary patches for the subpixel rendering. This is one of the things that has been a turn off for me on other distros. Yeah it may sound silly, pfft font rendering, but after using Ubuntu's beautiful subpixel font rendering I simply can't use anything else.

Yes i know that and agree with you.

---

