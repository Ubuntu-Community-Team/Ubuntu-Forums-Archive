---
title: "Failed update due to python2.6-minimal"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jandante on 2009-10-25
Hi,

I'm getting an error trying to upgrade. I have Karmic installed and want to install a new package (inkscape) and I checked all updates. But I get the error you can read here:
```
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
Setting up python2.6-minimal (2.6.4~rc2-0ubuntu1) ...
update-binfmts: /var/lib/binfmts/wine corrupt: out of binfmt data reading
package 
dpkg: error processing python2.6-minimal (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 python2.6-minimal
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I've found [https://bugs.launchpad.net/ubuntu/+source/python2.6/+bug/354228](https://bugs.launchpad.net/ubuntu/+source/python2.6/+bug/354228).

But I can't find a solution there. Can anybody help me?

---

