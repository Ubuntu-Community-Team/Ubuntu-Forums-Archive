---
title: "Upgrades held back for weeks."
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by spongypants23 on 2010-01-29
Hi guys.

On my 8.04 server installation, I've been getting this message from apt-get upgrade for a few weeks:

```
The following packages have been kept back:
  bind9-host dnsutils libbind9-30 libdns35 libisc35 libisccfg30 liblwres30
  linux-image-server linux-server
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
```

I thought this would be fixed with the 8.04.4 release yesterday, but alas, it was not so.

It's bugging me a bit that there are packages that need to be upgraded, but it's not doing it.

Any help?

---

### Post by zvacet on 2010-01-29
```
sudo apt-get dist-upgrade
```

---

### Post by ratcheer on 2010-01-29
Or, full-upgrade

Tim

---

### Post by tgalati4 on 2010-01-30
I get that as well.  It must be a package that was installed that was statically built with those libraries.  I'm not sure what the package is.  I haven't spent the time to track it down yet.

---

### Post by spongypants23 on 2010-01-30
> **zvacet said:**
> ```
sudo apt-get dist-upgrade
```

This seems to have done it.


Apparently it wasn't installing the newer kernel package with just "upgrade".

Thanks!

---

### Post by snowpine on 2010-01-30
That is the correct and normal behavior of "apt-get upgrade" vs. "apt-get dist-upgrade".

---

