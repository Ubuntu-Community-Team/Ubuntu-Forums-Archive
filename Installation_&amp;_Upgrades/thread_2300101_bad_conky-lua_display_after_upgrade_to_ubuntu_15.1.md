---
title: "bad conky-lua display after upgrade to ubuntu 15.10"
date: 2015-10-23
forum: Installation &amp; Upgrades
---

### Post by rodride on 2015-10-23
Hi,

I have a bad conky-lua display (no more rings...) after upgrading to 15.10.

It works fine on 15.04 before upgrade.

Thanks for help.

---

### Post by scooter3 on 2015-10-23
Same with me.  conky/lua scripts that work on 12.04 through 15.04, but not 15.10.  Tried removing conky, conky-all, reinstalling, etc.  Conky works by itself, but not with lua.

Update 27 Oct - I purged conky and loaded conky-all from 15.04 and everything is working again.  This is conky v 1.09 and lua50.  Has there been a change to running lua scripts in the new conky?

---

### Post by rodride on 2015-11-06
I just found the solution.

I downgrade conky-all package to version 1.9 and all woks fine from now on.

---

