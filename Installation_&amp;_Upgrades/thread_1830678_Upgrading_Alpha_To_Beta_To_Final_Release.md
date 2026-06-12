---
title: "Upgrading Alpha To Beta To Final Release"
date: 2011-08-22
forum: Installation &amp; Upgrades
---

### Post by MARP1961 on 2011-08-22
Can I convert my 11.10 installation to a Final Release version simply by doing ```
sudo apt-get update
``` then
```
sudo apt-get dist-upgrade
```?

Will doing this turn my Alpha 3 into the Final Release version in October?

---

### Post by nothingspecial on 2011-08-22
If you keep updating a development release then, yes you will end up with the final release.

---

### Post by MARP1961 on 2011-08-22
OK, thanks for that. I wasn't sure.

---

### Post by Mark Phelps on 2011-08-22
In some cases, especially with Alpha versions, you can not simply "upgrade" from one version to another; instead, you have to remove the earlier version and replace it with the newer version.

Alpha versions are limited function releases intended ONLY for testing; they are not intended to be fully-functional, nor are they intended to be easily upgraded to later versions.

The best approach (IMHO) is to have a separate install of the newer pre-released version and only use it for experimentation and testing.  Then, when the Released version comes out, replace the test version with it.

---

