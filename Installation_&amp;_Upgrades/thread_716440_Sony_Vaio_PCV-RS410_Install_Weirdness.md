---
title: "Sony Vaio PCV-RS410 Install Weirdness"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by rahnen on 2008-03-05
I just installed 7.10 w/ a ISO image from December in a dual boot config on my sisters Sony Vaio PCV-RS 410.  The install went fine, 7.10 came up beautifully but when I installed the long list of upgrades(since it was a December image) and then rebooted, I completely lost the video!!! Just squiggly lines and bars now.  I used Grub to boot into XP(gasp) and that still runs just fine.  Can anybody out there give some pointers as to what I should do from this point?:mad:

---

### Post by zvacet on 2008-03-06
Boot in recovery mode and after login type

```
dpkg-reconfigure -phigh xserver-xorg
```

Select **vesa** driver and that will give you basic graphic.After you can go and search for your video card driver.

---

