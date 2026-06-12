---
title: "linidn11 i386 or equivalent not present in 22.04"
date: 2022-05-04
forum: Installation &amp; Upgrades
---

### Post by jrcj38 on 2022-05-04
Just, like a few hours ago, updated to 22.04. HUGE mistake. I run Firestorm for Second Life (based on the Second Life viewer). Unfortunately they use a 32 helper app for second life voice, SLVoice, made by a 3rd party. it needs a number of i386 libraries all of which exist EXCEPT libidn11. I could still get this from Ubuntu 21.10 off the ubuntu site. Can't find it anywhere for 22.04. I have mentioned this phase out problem on multiple forms for years. Now I need to get this working but can't find a libidn11. Any help GREATLY appreciated.

---

### Post by QIII on 2022-05-04
It looks like there is a 32bit dev package for Jammy:  [https://packages.ubuntu.com/jammy/libidn11-dev](https://packages.ubuntu.com/jammy/libidn11-dev)

I would highly recommend moving away from 32 bit applications and libraries as those things are becoming harder and harder to find.

---

### Post by jrcj38 on 2022-05-04
Oh, I'm well aware and have been telling others. Thank you. I'll try it.

---

### Post by jrcj38 on 2022-05-04
Rats. No go. It's looking for a libidn.so.11. Even after installing the above (successfully) the library still isn't there.

---

### Post by jrcj38 on 2022-05-04
Turns out there is a work around for this, see [https://wiki.firestormviewer.org/getting_help](https://wiki.firestormviewer.org/getting_help).  Thanks to the Firestorm support group in Second Life.

---

