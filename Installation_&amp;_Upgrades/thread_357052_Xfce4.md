---
title: "Xfce4"
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by dmsn on 2007-02-09
Hi, i have ubuntu with gnome but i want to test xfce4. Must in install new ubuntu or how should i do ? Thanks

---

### Post by bapoumba on 2007-02-09
Hello,
just install xubuntu-desktop. On login with GDM, click "session", you can start an xfce session, and make it your default one (or not).
I just did that a couple days ago, and had not much time to check it out or customize it. 
```
~ $ aptitude show xfce4
Package: xfce4
State: not installed
Version: 4.3.90.2
Priority: optional
Section: universe/x11
Maintainer: Debian Xfce Maintainers <pkg-xfce-devel@lists.alioth.debian.org>
Uncompressed Size: 49.2k
Depends: xfwm4 (>= 4.3.90.1-1), xfwm4-themes (>= 4.3.90.1-1), xfce4-mcs-plugins
         (>= 4.3.90.1-1), xfce4-panel (>= 4.3.90.1-1), xfce4-icon-theme (>=
         4.3.90.1-1), xfdesktop4 (>= 4.3.90.1-1), thunar, xfce4-utils (>=
         4.3.90.1-1), gtk2-engines-xfce, xfce4-session (>= 4.3.90.1-1)
Recommends: xfce4-mixer, xfprint4, orage, xfce4-terminal, xfmedia
Suggests: x-window-system-core
Replaces: xfce4-themes (<= 4.0.0+cvs.20030301-1), xfce4-dev (<
          4.0.0+cvs.20030421)
Description: meta-package for xfce4 dependencies
 This package is a meta-package;  it depends on the core packages of the Xfce4
 desktop environment and recommends some extra Xfce4 packages.  If you intend to
 use Xfce4 and want the full experience then installing this package and the
 packages it Recommends is a great place to start. If you just want to pick and
 choose the core components then feel free to remove this package.

```

As you can see, I have not tested xfce4 yet ;)

---

