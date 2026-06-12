---
title: "After upgrade to 8.10 can't boot 2.6.27 kernel"
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by rage9 on 2008-11-04
The upgrade went fine, but apon trying to boot into the new kernel I don't get to payday.  I can luckily still boot into 2.6.24-21, and like many other I chose the option to clean up all the junk, which I saw in another thread was causing problems.  However kernel 2.6.27-7 is giving me a headache.

Looks like X tries to start but then quickly drops out and:

```
..udev_rules_apply_format: Unknown format variable... something about my laptops chassis

u splash: no usable theme found for 1024x768
screen init failed
gave up waiting for root device.
...some other crap...
Alert /dev/disk/by-uuid/..some number and letters.. does not exist. Dropping to shell!!

...
ata2: SRST failed (errno=-16)
ata2: SRST failed (errno=-16)
ata2: reset fialed, giving up
```

Anyone get spunked by anything similar?:confused:

Edit: Oh yes I did already try and re-install the kernel from 2.6.24.

---

### Post by findus on 2008-12-06
I am having the exact same error- any ideas?

---

### Post by henrik65 on 2008-12-07
I have same problem but no" sata/ata failed", the sata disk just isn't shown. I'm getting help over in
[http://ubuntuforums.org/showthread.php?p=6325225](http://ubuntuforums.org/showthread.php?p=6325225)

---

