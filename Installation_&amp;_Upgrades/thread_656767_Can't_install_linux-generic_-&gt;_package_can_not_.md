---
title: "Can't install linux-generic -&gt; package can not be authenticated"
date: 2008-01-02
forum: Installation &amp; Upgrades
---

### Post by alonsoa on 2008-01-02
I've been using the PXE installation method during December without any problems.

Today I get an error while the base system is getting installed showing that the
kernel packages can not be authenticated.

All other posts related to this seem to be post-installation. As this is during the
install I can't fix it via the CLI. Is there any boot options that can be used to force
the install?

Thanks,

Alberto

---

### Post by zvacet on 2008-01-03
Maybe you just need to refresh your source list

```
sudo apt-get update
```

and see does it work after that.

---

### Post by alonsoa on 2008-01-03
This is during the base-install. At this point the servers are bricks that can not be booted into.

So, unfortunately I can only use the servers to where ubuntu was installed in December, the rest are unusable.

Any other ideas?

Thanks,

Alberto

---

