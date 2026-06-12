---
title: "[SOLVED] How do I install latest XOrg ATI Drivers ?"
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by jbt on 2007-12-04
Hi,

I have just installed Gutsy.

I'm running dual screens using an ATI Radeon 7000, so I have to use the Xorg driver.
I have 2 analog monitors, one running off the analog port, and one running off the DVI port with a DVI<->Analog Converter.

My problem is that my screen on the DVI port is very washed out, making it unusable.

I have now discovered that this is a bug in the ati driver:
[https://bugs.freedesktop.org/show_bug.cgi?id=1082](https://bugs.freedesktop.org/show_bug.cgi?id=1082)

Can someone please explain how I get hold of the latest ati driver with this fix, and install it ?

Thanks
JohnT


[Already posted problem to Desktop forum, before I discovered I needed to install new driver]

---

### Post by viking777 on 2007-12-04
You could try looking here:

[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

---

### Post by jbt on 2007-12-04
> **viking777 said:**
> You could try looking here:

[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

Nope.
I need to use the XOrg drivers - the ATI ones don't support my card (radeon 7000)


Regards
JohnT

---

### Post by jbt on 2007-12-06
> **jbt said:**
> Nope.
I need to use the XOrg drivers - the ATI ones don't support my card (radeon 7000)


Regards
JohnT

Found the answer myself now:

Lots of useful X related stuff here:
[https://wiki.ubuntu.com/X](https://wiki.ubuntu.com/X)

Which pointed me to these pages with the latest ATI driver details:

[https://wiki.ubuntu.com/XorgOnTheEdge](https://wiki.ubuntu.com/XorgOnTheEdge)

[https://launchpad.net/~tormodvolden/+archive](https://launchpad.net/~tormodvolden/+archive)

Regards
JohnT

---

