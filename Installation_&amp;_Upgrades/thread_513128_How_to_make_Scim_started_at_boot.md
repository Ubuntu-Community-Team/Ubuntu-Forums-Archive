---
title: "How to make Scim started at boot"
date: 2007-07-30
forum: Installation &amp; Upgrades
---

### Post by satimis on 2007-07-30
Hi folks,

Ubuntu 7.04 desktop


Where shall I keep following lines;```

export LC_CTYPE="zh_TW.UTF-8"
export XIM=SCIM
export XIM_PROGRAM=/usr/bin/scim
export XIM_ARGS=”-d”
export GTK_IM_MODULE=xim
export QT_IM_MODULE=xim

```
so that "scim" will start at boot with input method available immediately.

I tested them on;
/etc/gdm/Xsession
~/.bashrc

w/o result


satimis

---

