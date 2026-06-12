---
title: "GIMP fails to load after upgrade to 19.04"
date: 2019-05-24
forum: Installation &amp; Upgrades
---

### Post by pablosquared on 2019-05-24
Hi folks. After upgrading to 19.04, I find that GIMP now fails to load. On running it from CLI, I see the following error, and nothing further happens.

```

gimp: symbol lookup error: /usr/lib/libgimpcolor-2.0.so.0: undefined symbol: gegl_scratch_alloc

```

GEGL is installed. I tried both the distro version of GIMP, and a newer version from PPA, same issue with both.

Any ideas, anyone?

---

### Post by SeijiSensei on 2019-05-24
Did you try updating gegl and babl manually as well?

---

### Post by brysq on 2019-05-25
Solved as seen in:

[https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/1820088](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/1820088)

```
sudo apt purge gimp
sudo apt purge libgegl-0.4-0
sudo apt install gimp
```

---

### Post by pablosquared on 2019-05-27
Thank you! This indeed did the trick. Greatly appreciate the help.

pablosquared


> **brysq said:**
> Solved as seen in:

[https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/1820088](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/1820088)

```
sudo apt purge gimp
sudo apt purge libgegl-0.4-0
sudo apt install gimp
```

---

