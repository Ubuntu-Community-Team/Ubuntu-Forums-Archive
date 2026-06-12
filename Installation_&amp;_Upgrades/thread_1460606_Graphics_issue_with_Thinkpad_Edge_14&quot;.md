---
title: "Graphics issue with Thinkpad Edge 14&quot;"
date: 2010-04-23
forum: Installation &amp; Upgrades
---

### Post by ugodiggi on 2010-04-23
Hi,
I'm trying to get 9.10 to work nicely on a Thinkpad Edge 14".

Everything is working fine, except that I have issues with the intel graphics drivers.
The monitor's native resolution is 1366x768 and I have Intel HD graphics card on it.
I have changed my xorg.conf to use driver = "vesa", but now I get only a resolution of 1024x768.
I tried to use xrandr to fix this, by adding a new mode etcetera, but this does not work - I believe because the driver is the issue.

Also, doing Ctrl+Alt+F[1-6] gives me a blank screen rather than a console.

How do I find out the details about my graphics chip? I see this:
```

$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Arrandale Integrated Graphics Controller (rev 12)
```

Maybe I should go more bleeding edge for my drivers? How do I do that?

Thank you!

Ugo

---

### Post by Mark Phelps on 2010-04-23
> **ugodiggi said:**
> Maybe I should go more bleeding edge for my drivers? How do I do that?

You could download the 10.04 RC that was just posted, burn that to CD, and try that in LiveCD mode -- but it may not work because according to the Release Notes, Intel is still investigating their 8xxx-series display drivers problems and the fixes are not in 10.04 as yet.

---

### Post by ugodiggi on 2010-04-24
Thanks for the suggestion, Mark.

I'm downloading 10.4RC CD right now, will ping back with what I find.

---

### Post by thinkbrowner on 2010-04-25
Any Luck on this? I just got a Dell with the Arrandale Chipset, and I'm curious what your experience with 10.04 is.

---

### Post by ugodiggi on 2010-04-27
I finally got to this, and it does work!

I used 10.4 beta 2 for amd64.

I get full resolution with the default installation and the consoles are working again.
The driver that is used in the new xorg.conf is:
  Driver = "fbdev"
rather than the intel one, or vesa like I was using before.

---

