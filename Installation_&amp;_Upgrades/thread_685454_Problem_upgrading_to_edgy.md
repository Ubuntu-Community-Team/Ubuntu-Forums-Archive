---
title: "Problem upgrading to edgy"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by mbailey on 2008-02-02
I'm trying to upgrade from 6.06, preferably to gutsy, so as the first step I need to upgrade to edgy. I'm using this:

gksu "update-manager -c"

which throws this warning:
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)

After this it invokes update manager just fine, but there is no upgrade button. Running check doesn't find anything new. The docs don't reccomend editing sources.list directly.

Any advice?

Thanks

---

### Post by Partyboi2 on 2008-02-02
You could try using the apt-get way, its not recommended but the choice is yours
[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)
Another option could be to back up what you need and do a clean install of gusty.

---

### Post by mbailey on 2008-02-02
Thanks - the apt-get seems to have worked, so far: Feisty upgrade in progress :)

---

