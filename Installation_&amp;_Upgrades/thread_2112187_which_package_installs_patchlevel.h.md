---
title: "which package installs patchlevel.h?"
date: 2013-02-04
forum: Installation &amp; Upgrades
---

### Post by jiapei100 on 2013-02-04
Hi, all:

I'm using Ubuntu 12.10, and I'm just wondering which package installs patchlevel.h? 


Cheers
Pei

---

### Post by schragge on 2013-02-04
> **jiapei100 said:**
> which package installs patchlevel.h?
There are many of them. Which one do you need?
Disclaimer: this was run on Debian wheezy, but I guess on Ubuntu 12.10 you'll get similar results.
```

$ apt-file search /patchlevel.h
bash-builtins: /usr/include/bash/patchlevel.h
hybrid-dev: /usr/include/ircd-hybrid-7/patchlevel.h
libxbae-dev: /usr/include/Xbae/patchlevel.h
perl: /usr/lib/perl/5.14.2/CORE/patchlevel.h
ppp-dev: /usr/include/pppd/patchlevel.h
python2.6-dbg: /usr/include/python2.6_d/patchlevel.h
python2.6-dev: /usr/include/python2.6/patchlevel.h
python2.7-dbg: /usr/include/python2.7_d/patchlevel.h
python2.7-dev: /usr/include/python2.7/patchlevel.h
python3.2-dbg: /usr/include/python3.2dmu/patchlevel.h
python3.2-dev: /usr/include/python3.2mu/patchlevel.h
screen: /usr/share/doc/screen/patchlevel.h.gz
xpaint: /usr/share/xpaint/include/patchlevel.h

```To answer such questions yourself, install 'apt-file'.

---

