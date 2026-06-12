---
title: "Running 10.10 but at startup says 11.04"
date: 2012-02-19
forum: Installation &amp; Upgrades
---

### Post by carpetmanleo on 2012-02-19
I tried an update awhile back and it failed because i have so much stuff installed; that  is what it said anyway. ever since the failed update my blue tooth receiver  has to be unplugged and plugged back in to work. computer doesnt recognize my hds other than  the file system, or my dvd drives. does any know how I would go about fixing these errors. dont want to start over runs fine other than not using dvd drives.

---

### Post by darkod on 2012-02-19
I guess you mean upgrade to a newer version, not just an update.

I don't do upgrades, but as far as I know, if it stops midway or fails out of any reason, you need to continue it with:
sudo dpkg --configure -a

That will continue configuring all packages that were not.

---

### Post by carpetmanleo on 2012-02-19
> **darkod said:**
> I guess you mean upgrade to a newer version, not just an update.

I don't do upgrades, but as far as I know, if it stops midway or fails out of any reason, you need to continue it with:
sudo dpkg --configure -a

That will continue configuring all packages that were not.

Yes I did mean upgrade.

---

### Post by 2F4U on 2012-02-19
Sounds to me as if you are left with a partial upgrade. If you are not able to finish the upgrade, you will most likely have ongoing problems. I would suggest you do a fresh installation, since that would give you a clean system.

---

### Post by carpetmanleo on 2012-02-19
I really don't want to do a clean install. I would rather address my issues one at a time. The upgrade was an accident, hit the wrong button whlle sleepy.  Thanks

---

### Post by darkod on 2012-02-19
> **carpetmanleo said:**
> I really don't want to do a clean install. I would rather address my issues one at a time. The upgrade was an accident, hit the wrong button whlle sleepy.  Thanks

You don't want to try to finish it with the command I provided in my previous post?

It might be the best thing to do, because I don't think you can roll it back and solving any issues will be difficult with half executed upgrade since it is not a normal behaviour.

---

### Post by carpetmanleo on 2012-02-19
> **darkod said:**
> You don't want to try to finish it with the command I provided in my previous post?

It might be the best thing to do, because I don't think you can roll it back and solving any issues will be difficult with half executed upgrade since it is not a normal behaviour.

 I did try what you suggested it did not work.

---

