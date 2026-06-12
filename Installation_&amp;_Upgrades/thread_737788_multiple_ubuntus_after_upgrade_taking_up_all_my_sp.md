---
title: "multiple ubuntus after upgrade taking up all my space"
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by Ralph Boland on 2008-03-27
I just upgraded from ubuntu 6.10 to 7.10 via 7.04 
using the 7.04 and 7.10 ubuntu disks.
Could someone please help get me out of the corner I am in.
I now have 4 versions of ubuntu, one is 6.10, one is 7.04,
one is 7.10 and I didn't check what the 4th one is.

I only wanted one version (7.10).

Could someone tell me:  (especially 1 and 2)

   1) What I did wrong.

   2) How to end up with only 7.10.

      The current 7.10 is only using 5G of my 40G drive.
      I want my 40G.

   3) How to not lose my original /home directory.
      It's gone from the current 7.10 version but is still in the 6.10 version.
      I have a backup but it would be nice not to have to use it.

   4) How to create a /boot and /home partitions while I am
      at it or afterwords.  I could solve this another day
      of course but it would be nice to fix it at the same time.

Note that in general I would like be be able to upgrade from disk
without loosing my home directory.

Thanks  Ralph Boland
~                                                                                 
~

---

### Post by zvacet on 2008-03-28
You can do upgrade only from alternate Cd.If you didn´t use it then you didn´t upgrade.Probably you installed all versions.Type in terminal

```
cat /etc/fstab
```

Post it here.

---

### Post by Ralph Boland on 2008-03-30
In the end I just gave up and installed 7.10 from scratch and then reloaded my home
directory from backup.

Hopefully, I learned enough to avoid getting myself into this mess again.

Ralph

---

