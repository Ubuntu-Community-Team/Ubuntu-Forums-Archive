---
title: "Meerkat won't boot with external monitor connected"
date: 2010-10-30
forum: Installation &amp; Upgrades
---

### Post by mixmastamyk on 2010-10-30
Hi All,

Wondering if anyone could help with this situation.  

Have a Dell Studio XPS with 64 bit Meerkat on it.  Whenever I connect my Samsung external monitor by displayport/dvi ubuntu no longer boots.  Machine unresponsive and have to cut power and disconnect it.  :/

Sounds exactly like this bug, no?  [https://bugs.launchpad.net/bugs/655795](https://bugs.launchpad.net/bugs/655795)

Except for the fact I have ATI video card and the restricted drivers (with Catalyst control center, although it is useless).  See for yourself:

```
02:00.0 VGA compatible controller: ATI Technologies Inc Madison [Mobility Radeon HD 5000 Series]

```

Win7 install works fine ... sigh.  Would turning off acceleration/effects help?  I'm about to try that next then going to bed.  ;)

-Mike

---

### Post by mixmastamyk on 2010-10-31
Looks like I can bypass the problem for now by disconnecting the monitor at boot time, then plugging it in and configuring it afterward.  :/

---

### Post by mixmastamyk on 2011-01-17
Good news (for me), looks like a recent kernel update fixed the problem.  ;)

---

