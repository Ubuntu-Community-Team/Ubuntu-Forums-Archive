---
title: "TV card not working anymore"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Devport on 2009-10-23
My tv card is not working under Karmic anymore.

I booted back into 9.04 and added the exact data to /etc/modprobe.d/saa7134.conf :

options saa7134 card=49 tuner=5

but Karmic wont detect the tuner correctly ?!

Instead of

[   11.750077] tuner 1-0060: chip found @ 0xc0 (saa7134[0])

the message should mention that it is the Philips PAL (MI...) tuner...

It works fine under Jaunty without any options !

---

### Post by Devport on 2009-10-25
[http://bugzilla.kernel.org/show_bug.cgi?id=14114](http://bugzilla.kernel.org/show_bug.cgi?id=14114)

---

