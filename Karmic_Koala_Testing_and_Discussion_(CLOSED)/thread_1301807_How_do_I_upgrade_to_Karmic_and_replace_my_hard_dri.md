---
title: "How do I upgrade to Karmic and replace my hard drive?"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dalesd on 2009-10-26
I've been using Ubuntu as my main OS since 8.04 and am getting prepared for 9.10.

I want to take advantage of the new features, like EXT4 and encrypted Home, and also replace my old hard drive with a newer, bigger, faster one.

I already have /home on it's own partition, and a large secondary disk for media.

So. what's the best way to do this?  I feel like it should involve doing a fresh install on the new disk, but I'm unclear on the details other than that.

---

### Post by fancypiper on 2009-10-27
Just remember to **not** format your /home and /media partitions during your install

---

### Post by philinux on 2009-10-27
> **dalesd said:**
> I've been using Ubuntu as my main OS since 8.04 and am getting prepared for 9.10.

I want to take advantage of the new features, like EXT4 and encrypted Home, and also replace my old hard drive with a newer, bigger, faster one.

I already have /home on it's own partition, and a large secondary disk for media.

So. what's the best way to do this?  I feel like it should involve doing a fresh install on the new disk, but I'm unclear on the details other than that.

Backup your important stuff from /home to your data drive, install new drive, install karmic to new drive. Copy back stuff from data.

---

