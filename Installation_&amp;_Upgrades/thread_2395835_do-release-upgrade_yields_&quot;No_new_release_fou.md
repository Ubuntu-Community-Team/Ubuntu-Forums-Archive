---
title: "do-release-upgrade yields &quot;No new release found&quot; in GNOME 16.04 LTS"
date: 2018-07-07
forum: Installation &amp; Upgrades
---

### Post by 98cwitr on 2018-07-07
[https://ubuntugnome.org/download/](https://ubuntugnome.org/download/)

Since 18.04 went back to gnome, is this project dead? I guess I need to do a fresh install.

---

### Post by #&amp;thj^% on 2018-07-07
They have been waiting until the first point release, since 14.04 and up.
I always check with:
```
do-release-upgrade -d -c
Checking for a new Ubuntu release
Upgrades to the development release are only 
available from the latest supported release.

```
But I'm already on 
```
lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 18.04 LTS
Release:	18.04
Codename:	bionic

```
> Since 18.04 went back to gnome, is this project dead? I guess I need to do **_a fresh install_**. 
For a better user experience I would.

---

### Post by 98cwitr on 2018-07-07
-d -c did the trick. But yes, I've make me a boot USB for 18.04 and doing a fresh install now. Thanks!

---

