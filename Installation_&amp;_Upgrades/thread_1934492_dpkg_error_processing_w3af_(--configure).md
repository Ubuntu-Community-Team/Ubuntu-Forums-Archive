---
title: "dpkg: error processing w3af (--configure)"
date: 2012-03-02
forum: Installation &amp; Upgrades
---

### Post by stueng on 2012-03-02
Hi,

When I try and dist-upgrade I receive error

dpkg: error processing w3af (--configure)
E: sub-process /usr/bin/pkg returned an error code (1)

I am trying to upgrade Backtrack 5 (Ubuntu 10.04) to 5.1

---

### Post by Lasall on 2012-03-02
Hi stueng,

please debug postinst script an set as second line in **/var/lib/dpkg/info/PACKAGE.postinst** "set -x".

Then run **dpkg --configure -a** again. (Please attach postinst script too.)


Kind regards

Lasall

---

