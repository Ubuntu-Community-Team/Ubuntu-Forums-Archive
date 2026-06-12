---
title: "Edgy ATI 3D Acceleration Success (fglrx)"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by pauljwells on 2006-10-28
I don't claim the kudos for this, I found this article: it's simple and easy and it worked for me.

[http://felipe-alfaro.org/blog/2006/09/06/ubuntu-edgy-ati-fglrx-dri-3d-acceleration-and-xorg-composite-extension/](http://felipe-alfaro.org/blog/2006/09/06/ubuntu-edgy-ati-fglrx-dri-3d-acceleration-and-xorg-composite-extension/)

At the end of your xorg.conf add the following:

Section Extensions
Option "Composite" "disable"
EndSection

and reboot...

edit: this works for cards that use the fglrx driver.

---

### Post by nbx909 on 2006-10-28
what cards?

---

### Post by pauljwells on 2006-10-28
any card that can use fglrx

---

### Post by jimbonnet on 2006-10-28
I got mine working as well with the latest ATI driver under edgy..

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X300/X550 Series Generic
OpenGL version string: 2.0.6065 (8.29.6)

01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]

using sources from ati

---

### Post by moeFinley on 2006-10-28
Working for me too.  But I wanted to try Beryl on Edgy anyone know about the open source driver?

---

### Post by abahgat on 2006-10-29
> **pauljwells said:**
> I don't claim the kudos for this, I found this article: it's simple and easy and it worked for me.

[http://felipe-alfaro.org/blog/2006/09/06/ubuntu-edgy-ati-fglrx-dri-3d-acceleration-and-xorg-composite-extension/](http://felipe-alfaro.org/blog/2006/09/06/ubuntu-edgy-ati-fglrx-dri-3d-acceleration-and-xorg-composite-extension/)

At the end of your xorg.conf add the following:

Section Extensions
Option "Composite" "disable"
EndSection

and reboot...

edit: this works for cards that use the fglrx driver.
Well, I may be wrong, but doesn't disabling the composite extension prevent you from being able to run compiz?

---

### Post by pony-tail on 2006-10-29
Yes it does - this "work around" causes as much trouble as it fixes .
From my (extensive) googling I have found that the issue is related to the inclusion of aiglx / xorg7.1 in edgy - maybe ATI will fix their drivers so as they work with this combo but do not hold your breath - I have 4 machines with Radeon Cards none is supported by the open source driver (X700 , X800 , 9800XT , and a PCI-e X850XT-PE on  64bit) The x700 and x800 are on Dapper and working fine - the other two are on edgy the 9800XT is working but without compositing and the X850 is just barely working at all(64bit edgy).

---

### Post by happy-and-lost on 2006-10-29
Completely broke X server for me, nano to the rescue!

---

### Post by pauljwells on 2006-10-30
pony-tail is correct. Edgy includes compositing by default, but the fglrx driver doesn't work with this.

I've never felt the need to try the compositing desktops so this isn't a concern for me. Sorry if anyone was misled.

I recall seeing a post that you can get beryl/xgl to work on edgy with the fglrx driver.

---

