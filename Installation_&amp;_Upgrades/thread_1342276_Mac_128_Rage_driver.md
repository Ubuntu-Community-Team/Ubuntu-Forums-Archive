---
title: "Mac 128 Rage driver?"
date: 2009-11-30
forum: Installation &amp; Upgrades
---

### Post by Smale on 2009-11-30
Hi, I'm new to Ubuntu... like, I *just* started using it, and it turns out my graphics card is *pretty* bad. So, my brother told me to ask on the forums about a 'driver' for my Mac 128 rage card. Not that I really know what this means, but hopefully someone can help. Thanks in advance :)

---

### Post by Smale on 2009-11-30
> **Smale said:**
> Hi, I'm new to Ubuntu... like, I *just* started using it, and it turns out my graphics card is *pretty* bad. So, my brother told me to ask on the forums about a 'driver' for my Mac 128 rage card. Not that I really know what this means, but hopefully someone can help. Thanks in advance :)

no one?

---

### Post by jacobs444 on 2009-11-30
This is an ati driver, thus if you have that card and need the driver, then you will need to get it from ati.

---

### Post by jacobs444 on 2009-11-30
type sudo lshw (that is a lowercase L not a 1, for the command means list hardware) look for the part near the top of the output about display, it should list your card, it may be under pci though.

If you are using the latest ubuntu, your card will not be supported by ati though. That is an old card.

---

