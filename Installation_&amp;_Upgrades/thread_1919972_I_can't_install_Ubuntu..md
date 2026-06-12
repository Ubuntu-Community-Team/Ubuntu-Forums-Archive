---
title: "I can't install Ubuntu."
date: 2012-02-03
forum: Installation &amp; Upgrades
---

### Post by Acutical on 2012-02-03
When i try and boot from a USB, i get a black screen with white text on it. I've let it set 10 mins and it still doesn't boot. I've tried Wubi just to see if it fixes the issue and i still have the problem.

If it matters, my specs are:

Motherboard: Asus Sabertooth X58
Graphics: Nvidia GTX 560 Ti
RAM: 4 Gb
and Intel Core i7

---

### Post by wolfen69 on 2012-02-03
Maybe it didn't write correctly to the usb drive. Can you make a cd and try that? How did you make the usb drive?

---

### Post by Acutical on 2012-02-03
With unetbootin. I can't install it with a CD because its over 700MB.

---

### Post by TheFu on 2012-02-03
Not all USB devices support being booted from. Some are just flaky with certain USB controllers.

The workaround for this is either
a) to burn a DVD and boot from that
or
b) get a different flash drive and try your steps again.

You may need to tweak the BIOS settings for USB too.  I've had issues with some systems refusing to boot from USB, but those are generally older - pre-Core2 Duo machines. I doubt that's an issue for your Core i7.

---

### Post by wolfen69 on 2012-02-03
> **Acutical said:**
> With unetbootin. I can't install it with a CD because its over 700MB.

Ubuntu has never been over 700mb for the standard image. Check [here]("http://releases.ubuntu.com/oneiric/").

It *will* be, starting with 12.04, but not yet.

---

### Post by Acutical on 2012-02-08
Ok. I tried using a CD. Still doesn't work. My USB can be booted from, because i installed ubuntu on another computer with it with no problem at all.

---

