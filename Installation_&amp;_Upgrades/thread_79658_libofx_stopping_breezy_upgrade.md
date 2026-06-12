---
title: "libofx stopping breezy upgrade"
date: 2005-10-20
forum: Installation &amp; Upgrades
---

### Post by domstyledesign on 2005-10-20
i tried to dist-upgrade from apt-get, but it failed, so i thought i try w/ synaptic.

here's what i got:

```
E: /var/cache/apt/archives/libofx2_10x1.998900000005dp-8900.8.0-3ubuntu8_i386.deb:  trying to overwrite `/usr/share/libofx/dtd/opensp.dcl', which is also in package libofx0c102

4
```

the upgrade stops after that.  i tried marking the libofx that's already installed for removal, but it didn't help

---

### Post by kimsay on 2005-10-20
I'ved this problem too. I find out that the programs gnucash and mplayer are the problems on my computer. They used libofx. After I've removed both, it works.

---

