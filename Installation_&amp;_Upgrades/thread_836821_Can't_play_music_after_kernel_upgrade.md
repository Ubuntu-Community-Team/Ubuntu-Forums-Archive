---
title: "Can't play music after kernel upgrade"
date: 2008-06-21
forum: Installation &amp; Upgrades
---

### Post by vik.vaughn on 2008-06-21
I just performed the latest automatic kernel upgrade (with some other suff that was automaticallyupdated too) and now I can't play music anymore. Amarok either freezes up or says "Audio output unavailable, the device is busy. Xine parameters:"

I can't play audio with any other media players either. I'm sure some kind of error log or debug info would be useful in diagnosing what's happened, but I don't know where to start. Basically everything is saying something else is using my sound card or the device is busy.

---

### Post by vik.vaughn on 2008-06-21
Fixed it by moving xine-config to xine-config.old in the amarok directory.

---

