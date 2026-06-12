---
title: "Possible to install a package with only what it depends on and nothing else?"
date: 2015-07-08
forum: Installation &amp; Upgrades
---

### Post by greg2lapa on 2015-07-08
If I try to install the package "unity" from a minimal ubuntu install (i.e., from a terminal) it includes a lot of scopes and other stuff that aren't dependencies. 

If I run ```
apt-cache depends unity
``` I can see what the dependencies are. Is there a way to install unity with only these dependencies and nothing more?

---

### Post by papibe on 2015-07-08
Hi greg2lapa.

Try using the '--no-install-recommends' options. For example:
```
sudo apt-get --no-install-recommends install unity
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by v3.xx on 2015-07-08
Here's the breakdown

[http://packages.ubuntu.com/trusty/ubuntu-desktop](http://packages.ubuntu.com/trusty/ubuntu-desktop)

---

