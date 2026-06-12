---
title: "Free Space in &quot;/boot&quot;?"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by zwollner on 2010-04-30
How do I allocate more space to the "/boot" directory?

I'm trying to upgrade from 9.10 to 10.04 and it says the "/boot" directory does not have enough free space, and that I need to free up 5mb more.

I checked my root dir, and I have 65Gb free.

What do I do?

---

### Post by bhaverkamp on 2010-04-30
You should be able to resize the boot partition from a live CD using gparted. If you're not sure about this post the output of gparted so someone can suggest what to do. Of course make sure your system is backed up first.

---

