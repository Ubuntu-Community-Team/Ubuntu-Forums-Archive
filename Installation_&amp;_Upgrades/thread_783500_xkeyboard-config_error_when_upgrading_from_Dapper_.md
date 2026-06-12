---
title: "xkeyboard-config error when upgrading from Dapper to Hardy"
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by ilmw on 2008-05-05
Unfortunately, I encountered the following problem when upgrading from Dapper LTS to Hardy LTS:

E: /var/cache/apt/archives/xkb-data_1.1~cvs.20080104.1-1ubuntu6_all.deb: trying to overwrite `/etc/X11/xkb/types.dir', which is also in package xkeyboard-config

I found the solution from [https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/213566/comments/5:](https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/213566/comments/5:)

This bug was fixed in the package xkeyboard-config - 1.1~cvs.20080104.1-1ubuntu5

---------------
xkeyboard-config (1.1~cvs.20080104.1-1ubuntu5) hardy; urgency=low

  * preinst:
    - when upgrading from hardy, check the conffiles against
      xkeyboard-config not xkb-data (was not available back then)
  * debian/control:
    - add conflicts against old xkeyboard-config to ensure the
      upgrade happens in the right order (LP: #213566)

Can someone helps me to solve this? I understand the above statement but don't know how to to it.

THANKS!

---

### Post by ilmw on 2008-05-06
No one had this problem? :-(

---

