---
title: "Karmic apt-get ia32 package snafu"
date: 2009-07-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by RandomMatt on 2009-07-10
Hi,

I know I shouldn't be using karmic yet, but I decided foolishly that I wanted bleeding-edge, and so far it has cost me KDE4 and apt-get.

Trying to install PHP has caused libgd2-noxpm to randomly break in such a way that it won't unbreak, and so many packages depend on it (indirectly, seemingly the entirity of KDE4) that I am loath to remove it. Trying to fix it causes these lovely messages from our favourite package manager:

```
Unpacking ia32-libgd2-noxpm (from .../libgd2-noxpm_2.0.36~rc1~dfsg-3ubuntu1_amd64.deb) ...
dch warning: new version (2.0.36~rc1~dfsg-3ubuntu1~14) is less than
the current version number (2.0.36~rc1~dfsg-3ubuntu1).
dpkg: error processing libgd2-noxpm (--configure):
 no package named `libgd2-noxpm' is installed, cannot configure
Errors were encountered while processing:
 libgd2-noxpm

```

I have no idea how to fix this; every time I try to install libgd2-noxpm, it tries to install the ia32-prefixed version, complains about versions, and then tries to configure the non-prefixed version, realises there is no such thing, and breaks.

In addition, the ia32 library is refusing to play ball because the ia32-prefixed versions of everything it needs don't exist either, whereas the normal libraries do! I'm sure that this is just a package handling issue, as everything using these libraries works fine.

Could anyone help, please?

---

