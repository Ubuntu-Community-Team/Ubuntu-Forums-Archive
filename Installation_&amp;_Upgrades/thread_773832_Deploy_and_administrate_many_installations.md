---
title: "Deploy and administrate many installations?"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by mikkelk on 2008-04-29
Hi

How do I deploy and administrate (install upgrades or new programs etc.) to many computers?

I have about 32 laptops that needs the same configuration. Can I have a "master" computer, that i can install upgrades to, install new programs, setup Firefox to start when booted etc. and all the other computers will get the same configuration?

Thanks in advance

Mikkel Kaas

---

### Post by wkulecz on 2008-04-29
With 6.06 I had a master system and "cloned" the hard drive with rsync and then popped them into the other systems. Normally, only the network name had to be changed, but since I keep each of these systems isolated behind "cable/dsl modem router boxes" they could all have the same system name.

8.04's use of UUID instead of /dev entries to mount disks makes this problematic.  Not insurmountable, but I don't see the upside of partition mounting schemes that are basically untype-able from the command line!

--wally.

---

### Post by mikkelk on 2008-05-09
Bump

---

### Post by prshah on 2008-05-09
> **mikkelk said:**
> Hi
that i can install upgrades to, 

Dont know about the rest, but you can use a utility called apt-cacher to ensure that updates downloaded in your "master" machine do not have to be re-downloaded to the other 31 machines: see [http://ubuntuforums.org/showthread.php?t=564301](http://ubuntuforums.org/showthread.php?t=564301) for more info.

---

