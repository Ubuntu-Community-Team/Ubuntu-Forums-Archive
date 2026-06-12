---
title: "wine issues. missing some development files and headers"
date: 2008-04-09
forum: Installation &amp; Upgrades
---

### Post by yiddski on 2008-04-09
i'm trying to install the newest wine, but this happens at the end of configure

```
configure: libxcursor development files not found, the Xcursor extension won't be supported.
configure: libxi development files not found, the Xinput extension won't be supported.
configure: libXxf86vm development files not found, XFree86 Vidmode won't be supported.
configure: libxrender development files not found, XRender won't be supported.
configure: libxrandr development files not found, XRandr won't be supported.
configure: libxinerama development files not found, multi-monitor setups won't be supported.
configure: libxml2 development files not found, XML won't be supported.
configure: libxslt development files not found, xslt won't be supported.
configure: libhal development files not found, no dynamic device support.
configure: lib(n)curses development files not found, curses won't be supported.
configure: libsane development files not found, scanners won't be supported.
configure: libgphoto2 development files not found, digital cameras won't be supported.
configure: liblcms development files not found, Color Management won't be supported.
configure: libldap (OpenLDAP) development files not found, LDAP won't be supported.
configure: libcapi20 development files not found, ISDN won't be supported.
configure: libcups development files not found, CUPS won't be supported.
configure: fontconfig development files not found, fontconfig won't be supported.
configure: OpenSSL development files not found, SSL won't be supported.
configure: libjpeg development files not found, JPEG won't be supported.
configure: libpng development files not found, PNG won't be supported.

configure: WARNING: OpenGL development headers not found.
OpenGL and Direct3D won't be supported.

configure: WARNING: FreeType development files not found.
Fonts will not be built. Dialog text may be invisible or unaligned.

```

google has been unhelpful 

halp?

---

### Post by Partyboi2 on 2008-04-09
You probably need some more packages installed you could try adding the wine repo and then installing build-dep wine. In a terminal
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```then```

 sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list
```then update
```
sudo apt-get update
```then
```
sudo  apt-get build-dep wine
```then try wine install again
```
./tools/wineinstall
```

---

### Post by yiddski on 2008-04-10
> **Partyboi2 said:**
> You probably need some more packages installed you could try adding the wine repo and then installing build-dep wine. In a terminal
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```then```

 sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list
```then update
```
sudo apt-get update
```then
```
sudo  apt-get build-dep wine
```then try wine install again
```
./tools/wineinstall
```

i get this now after running sudo apt-get build-dep wine

E: Could not open file /var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_breezy_free_source_Sources - open (2 No such file or directory)

---

### Post by Partyboi2 on 2008-04-10
What version of ubuntu are you running? Gusty?

---

