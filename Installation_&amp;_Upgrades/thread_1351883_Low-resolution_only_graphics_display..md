---
title: "Low-resolution only graphics display."
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by nssone on 2009-12-11
OK, so I have a Dell Mini 9 and recently upgraded it from Jaunty to Karmic. After upgrading and rewriting my menu.lst to load the latest kernels (because my mouse wouldn't work then otherwise), I got a messed up display. In order to even get any kind of viewable display back I had to do the force BIOS hack for i915resolution, and all that got me is the low-res display I have now. Without that in my kernel line of the GRUB, I don't get any real display on the Min. I tried the whole xorg.conf delete and rewrite and dpkg, but none of that is working for me. I tried rewriting some of the sections in it but I can't seem to figure out what values need to be rewritten.

So, if anybody has any insight into this, it would help me out greatly. Also, so nobody has to look it up, the graphic hardware is Intel 945GME.

Thanks.

---

### Post by mikewhatever on 2009-12-11
Try this howto [http://ubuntuforums.org/showthread.php?t=1346125](http://ubuntuforums.org/showthread.php?t=1346125).

For the record, you shouldn't need kernels outside the repositories.

---

