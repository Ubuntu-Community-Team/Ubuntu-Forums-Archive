---
title: "This is certainly not NORMAL."
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by atentik on 2011-10-18
After several efforts to get my system back and running, I am able to boot but on the desktop, I have nothing. No option to select internet, not sidebar, no terminal at the top, no program file. Absolutely nothing. This is not normal.

Please see the attached picture.

---

### Post by 2F4U on 2011-10-18
Am I right in guessing that this is an upgraded system? Have you already tried to create a new user and see if this user has the same problems?

---

### Post by decoherence on 2011-10-18
that looks like the gnome-shell background.

well, i guess try resetting your gnome stuff.

```
mv .gnome .gnome.BAK
mv .gnome2 .gnome2.BAK
mv .gconf .gconf.BAK
mv .gconfd .gconfd.BAK
mv .metacity .metacity.BAK
```

this might not work exactly right with GNOME3... you might need to rename a '.gnome3' folder as well, you might not have a '.metacity' folder.... i haven't got a machine to test on right now.

If you find things break even more, you can reverse the commands to restore things (ie 'mv .gnome2.BAK .gnome2') -- some people will direct you to run 'rm -rf' on these files instead of 'mv' but this will prevent you from restoring anything.

---

### Post by collisionystm on 2011-10-18
I had that. It was my video card driver. Apparently gnome-shells video card requirements are different than Unity.

---

### Post by atentik on 2011-10-18
Thanks everyone. collisionystm, how did you solve the problem. should I remove gnome-shell?

---

### Post by collisionystm on 2011-10-18
> **atentik said:**
> Thanks everyone. collisionystm, how did you solve the problem. should I remove gnome-shell?

I tried to update my video card drivers. Still failed. 

I actually ended up using CrunchBang with xfce and it worked really well. I had all effects and it was so smooth..almost unbelievable.

---

