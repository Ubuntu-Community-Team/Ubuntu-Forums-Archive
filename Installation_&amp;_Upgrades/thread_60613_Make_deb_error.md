---
title: "Make deb error"
date: 2005-08-28
forum: Installation &amp; Upgrades
---

### Post by votum on 2005-08-28
```
root@Votum:/ndiswrapper-1.2#  make deb
```

make[1]: Entering directory `/ndiswrapper-1.2'
make -f debian/rules binary-utils
make[2]: Entering directory `/ndiswrapper-1.2'
sed -e 's/-#KVERS#//g' \
-e 's/#NDISVERS#/1.2/g' \
-e 's/#DATE#/'"`date --rfc-822`"'/g' \
        -e 's/#MAINT#/Giridhar Pemmasani <pgiri@users.sourceforge.net>/g' \
        debian/changelog.template > debian/changelog
sed -e 's/#NDISVERS#/1.2/' \
-e 's/#MAINT#/Giridhar Pemmasani <pgiri@users.sourceforge.net>/g' \
debian/control.utils > debian/control
echo "utils/loadndisdriver /sbin" > debian/ndiswrapper-utils.install
echo "utils/ndiswrapper /usr/sbin" >> debian/ndiswrapper-utils.install
echo "utils/ndiswrapper-buginfo /usr/sbin" >> \
        debian/ndiswrapper-utils.install
cp debian/dirs.utils debian/dirs
dh_testdir
dh_testroot
dh_installchangelogs ChangeLog
dh_installdocs
dh_installexamples
dh_installdebconf
export DH_OPTIONS='-i'
dh_installman ndiswrapper.8
make -C utils
make[3]: Entering directory `/ndiswrapper-1.2/utils'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/ndiswrapper-1.2/utils'
dh_install
dh_link
dh_strip
dh_compress
dh_fixperms
dh_perl
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dh_gencontrol
dpkg-gencontrol: warning: unknown substitution variable ${misc:Depends}
dh_md5sums
dh_builddeb --destdir=..
dpkg-deb: building package `ndiswrapper-utils' in `../ndiswrapper-utils_1.2-1_i386.deb'.
dh_clean
make[2]: Leaving directory `/ndiswrapper-1.2'
make -f debian/rules binary-modules
make[2]: Entering directory `/ndiswrapper-1.2'
sed -e 's/#KVERS#/2.6.10-5-k7/g' \
-e 's/#NDISVERS#/1.2/g' \
-e 's/#DATE#/'"`date --rfc-822`"'/g' \
        -e 's/#MAINT#/Giridhar Pemmasani <pgiri@users.sourceforge.net>/g' \
        debian/changelog.template > debian/changelog
sed -e 's/#KVERS#/2.6.10-5-k7/' \
-e 's/#NDISVERS#/1.2/' \
debian/control.modules > debian/control
sed -e 's/#KVERS#/2.6.10-5-k7/' debian/postinst.modules > debian/postinst
if [ 6 == 4 ];then \
        module=ndiswrapper.o; \
else \
        module=ndiswrapper.ko; \
fi; \
echo "driver/$module /lib/modules/2.6.10-5-k7/kernel/drivers/net/ndiswrapper" \
        > debian/ndiswrapper-modules-2.6.10-5-k7.install
dh_testdir
dh_testroot
dh_installchangelogs ChangeLog
dh_installdocs
dh_installexamples
dh_installdebconf
dh_installdirs lib/modules/2.6.10-5-k7/kernel/drivers/net/ndiswrapper
make -C /ndiswrapper-1.2/driver
make[3]: Entering directory `/ndiswrapper-1.2/driver'
[COLOR=Red]Can't find kernel sources in /lib/modules/2.6.10-5-k7/build;
  give the path to kernel sources with KSRC=<path> argument to make[/COLOR]
make[3]: *** [prereq_check] Error 1
make[3]: Leaving directory `/ndiswrapper-1.2/driver'
make[2]: *** [build-modules] Error 2
make[2]: Leaving directory `/ndiswrapper-1.2'
make[1]: *** [binary] Error 2
make[1]: Leaving directory `/ndiswrapper-1.2'
make: *** [deb] Error 2

If someone know where to get started plz let me know ](*,) 
tanks in advance

---

