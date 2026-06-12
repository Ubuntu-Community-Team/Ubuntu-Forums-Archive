---
title: "How do you downgrade?"
date: 2013-05-30
forum: Installation &amp; Upgrades
---

### Post by cryken on 2013-05-30
I am currently running Ubuntu 13.04 Raring Ringtail and I found out my graphics driver is not supported on it. So I found out it's supported on Ubuntu 12.04 LTS but the problem is I don't know how to downgrade to it.

---

### Post by lykwydchykyn on 2013-05-30
There is no way to downgrade; you have to reinstall fresh.

---

### Post by Cheesemill on 2013-05-30
If your card is an ATI 2/3/4xxx series then make sure you install Ubuntu from the 12.04.1 CD ***not*** the 12.04.2 CD as the later version of 12.04 doesnt support these cards either.

Downloads for 12.04.1 can be found here...
[http://old-releases.ubuntu.com/releases/precise/](http://old-releases.ubuntu.com/releases/precise/)

---

### Post by alan9800 on 2013-05-30
> **Cheesemill said:**
> If your card is an ATI 2/3/4xxx series then make sure you install Ubuntu from the 12.04.1 CD ***not*** the 12.04.2 CD as the later version of 12.04 doesnt support these cards either.

Downloads for 12.04.1 can be found here...
[http://old-releases.ubuntu.com/releases/precise/](http://old-releases.ubuntu.com/releases/precise/)regarding to this: my video card is an ATI 2400XT; I've installed Kubuntu 12.04.02 64bit and I've noticed that, differently from Ubuntu 12.04.02, the kernel version is 3.20.44 (on Ubuntu 12.04.02 is 3.5.<something>; I don't remember now the rest of numbers, but it's the lts-quantalized version). Is perhaps because of this different kernel version that Kubuntu runs better than Ubuntu on my PC?

---

### Post by Mark Phelps on 2013-05-30
AMD (the successor to ATI) dropped restricted driver support for that card YEARS ago.  The cards that were dropped last summer were the "HD" series -- which are newer than yours. The only driver that works in recent history is the default Radeon driver, and it that case, it really doesn't matter what version of Ubuntu you use that is newer than 9.10.

---

