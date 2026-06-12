---
title: "dist-upgrade fails on openoffice - I'm stuck!"
date: 2005-10-17
forum: Installation &amp; Upgrades
---

### Post by bjtuna on 2005-10-17
Ran my dist-upgrade and got:

```

Selecting previously deselected package openoffice.org2-help-en-us.
Unpacking openoffice.org2-help-en-us (from .../openoffice.org2-help-en-us_1.9.129-0.1ubuntu5_all.deb) ...
dpkg: error processing /var/cache/apt/archives/openoffice.org2-help-en-us_1.9.129-0.1ubuntu5_all.deb (--unpack):
 trying to overwrite `/usr/lib/openoffice2/help/en/scalc.idx/DOCS.TAB', which is also in package openoffice.org2-calc
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org2-help-en-us_1.9.129-0.1ubuntu5_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I get the same error if I try 'apt-get -f install', or if I try to 'apt-get remove openoffice.org2-calc' or really anything else I try.  My system is half-upgraded and so most things don't work and won't work until I can get this resolved so I can complete the dist-upgrade.

Any help would be greatly appreciated! Thanks!

---

### Post by bjtuna on 2005-10-17
Ok I was able to get around this by doing:

```

dpkg -i --force-overwrite /var/cache/apt/archives/openoffice.org2-help-en-us_1.9.129-0.1ubuntu5_all.deb

```

Followed by a very stressful 15 minutes of 'apt-get -f install' and then another turn at 'apt-get dist-upgrade'.  

It should also be known that I got errors on dist-upgrade on postfix, lsb, mutt and friends.. had to 'apt-get remove postfix' to clear all that up.

Bugs!

---

