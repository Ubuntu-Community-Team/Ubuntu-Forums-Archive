---
title: "aticonfig for openSUSE users - evil amdpcsdb!"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by sobranko on 2008-10-31
This concerns openSUSE users migrating to Ubuntu (like me) and probably users of other distros:
**always use -f option with aticonfig --initial **

aticonfig utillity stores its configuration in 
```
/etc/X11/xorg.conf
```
like in opneSUSE, but on Ubuntu it stores additional configuration in
```
/etc/ati/amdpcsdb
```

If you use aticonfig without -f option you will break something because only xorg.conf will be updated.

Ati driver version: **8.47.3**
Gfx card: **X850XT**

---

