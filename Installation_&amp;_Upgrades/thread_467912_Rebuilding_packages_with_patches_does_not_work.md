---
title: "Rebuilding packages with patches does not work"
date: 2007-06-08
forum: Installation &amp; Upgrades
---

### Post by sup on 2007-06-08
Hello, I was trying to apply a patch to network-manager-openvpn from [Lanuchpad bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/88069") and it fails. I do the steps that are recommended there, i.e:```
1. $ sudo apt-get build-dep network-manager-openvpn
2. $ apt-get source network-manager-openvpn
3. place the patch file in debian/patches
4. $ sudo debuild -us -uc
```
but none of the patches (either original or added by me) is applied:
```
tom@bill:~/Sources/network-manager-openvpn-0.3.2svn2342$ sudo debuild -us -uc debian/rules clean
test -x debian/rules
test "`id -u`" = 0
/usr/bin/make -f debian/rules reverse-config
make[1]: Entering directory `/home/tom/Sources/network-manager-openvpn-0.3.2svn2342'
make[1]: Nothing to be done for `reverse-config'.
make[1]: Leaving directory `/home/tom/Sources/network-manager-openvpn-0.3.2svn2342'
if [ "reverse-patches" = "reverse-patches" ]; then rm -f debian/stamp-patched; fi
patches: debian/patches/01_fix_dbus_signal_name.diff debian/patches/02_fix_wrong_awk_path.diff debian/patches/03_routers.diff
Patch debian/patches/03_routers.diff is not applied.
Patch debian/patches/02_fix_wrong_awk_path.diff is not applied.
Patch debian/patches/01_fix_dbus_signal_name.diff is not applied.
if [ "reverse-patches" != "reverse-patches" ]; then touch debian/stamp-patched; fi
if [ "reverse-patches" != "reverse-patches" ] ; then \
                /usr/bin/make -f debian/rules update-config ; \
        fi
for dir in debian/patches ; do \
            rm -f $dir/*.log ; \
        done
/usr/bin/make -C . -k distclean
make[1]: Entering directory `/home/tom/Sources/network-manager-openvpn-0.3.2svn2342'
make[1]: *** No rule to make target `distclean'.
make[1]: Leaving directory `/home/tom/Sources/network-manager-openvpn-0.3.2svn2342'
make: [makefile-clean] Error 2 (ignored)
rm -f debian/stamp-makefile-build
dh_clean 
rm -f debian/stamp-autotools-files
rm -f aclocal.m4 auth-dialog/Makefile.in compile config.guess \
           config.h.in config.sub configure depcomp install-sh \
           intltool-extract.in intltool-merge.in intltool-update.in \
           ltmain.sh Makefile.in missing mkinstalldirs po/Makefile.in.in \
           properties/Makefile.in src/Makefile.in
 dpkg-source -b network-manager-openvpn-0.3.2svn2342
dpkg-source: warning: Version number suggests Ubuntu changes, but there is no XSBC-Original-Maintainer field
dpkg-source: building network-manager-openvpn using existing network-manager-openvpn_0.3.2svn2342.orig.tar.gz
dpkg-source: building network-manager-openvpn in network-manager-openvpn_0.3.2svn2342-0ubuntu3.diff.gz
dpkg-source: building network-manager-openvpn in network-manager-openvpn_0.3.2svn2342-0ubuntu3.dsc
 debian/rules build
test -x debian/rules
NOCONFIGURE=1 ./autogen.sh
/usr/bin/gnome-autogen.sh

```
It worked before with other packages (but it does not work with thme now either), any ideas what went wrong?

---

### Post by sup on 2007-06-09
hum, I do not know how to solve this, but I retreted to applying pathces manually, which works...

---

### Post by sup on 2007-06-09
Anyway it started to work now anyway, do not know why...:-/

---

