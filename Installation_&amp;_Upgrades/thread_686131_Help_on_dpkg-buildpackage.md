---
title: "Help on dpkg-buildpackage"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by Paris Heng on 2008-02-02
Problems: What is the fakeroot? It is spell wrongly? Why I can't run the command? 
> root@heng:/etc/hostapd-0.5.5# dpkg-buildpackage -rfakeroot -uc -b
dpkg-buildpackage: source package is hostapd
dpkg-buildpackage: source version is 1:0.5.5-3.1
dpkg-buildpackage: source changed by Matt Brown <mattb@debian.org>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 0.5.5-3.1
fakeroot debian/rules clean
[COLOR="Red"]/usr/bin/dpkg-buildpackage: 212: fakeroot: not found[/COLOR]

Did I need to upgrade the **dpkg-buildpackage** or anythings?

Please assist

---

### Post by Partyboi2 on 2008-02-02
Have you got fakeroot installed?

---

### Post by Paris Heng on 2008-02-02
> **Partyboi2 said:**
> Have you got fakeroot installed?

I think most probably no. Why i need fakeroot? I already in root when i building the package.

---

### Post by Partyboi2 on 2008-02-02
here is a little on fakeroot
>  fakeroot runs a command in an environment wherein it  appears  to  have
       root  privileges  for  file  manipulation.  This is useful for allowing
       users to create archives (tar, ar, .deb etc.) with files in  them  with
       root  permissions/ownership.   Without  fakeroot one would need to have
       root privileges to create the constituent files of  the  archives  with
       the  correct  permissions  and ownership, and then pack them up, or one
       would have to  construct  the  archives  directly,  without  using  the
       archiver.you can read more by opening a terminal and typing
```
man fakeroot
```

---

### Post by zvacet on 2008-02-03
If you want to build your own packages read [this](http://doc.ubuntu.com/ubuntu/packagingguide/C/) and [this](http://www.debian.org/doc/devel-manuals#maint-guide).

---

### Post by Paris Heng on 2008-02-03
Thank you for your informative guide.

I actually having problems is this dpkg, can you help in looking for my error below? Please assist.

***[COLOR="Blue"]Problems:[/COLOR] Error,***

> root@heng:/etc/hostapd-0.5.5# dpkg-buildpackage -rfakeroot -uc -b
dpkg-buildpackage: source package is hostapd
dpkg-buildpackage: source version is 1:0.5.5-3.1
dpkg-buildpackage: source changed by Matt Brown <mattb@debian.org>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 0.5.5-3.1
fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp
/usr/bin/make clean
make[1]: Entering directory `/etc/hostapd-0.5.5'
rm -f core *~ *.o hostapd hostapd_cli nt_password_hash hlr_auc_gw
rm -f *.d driver_conf.c
make[1]: Leaving directory `/etc/hostapd-0.5.5'
dh_clean
dpatch deapply-all
[COLOR="Red"]22_madwifi_plaintext not applied to ./ .
21_madwifi_includes not applied to ./ .
20_madwifi_headers not applied to ./ .
12_conf_etc_hostapd not applied to ./ .
attempting to revert failed patch 10_config from ./:
md5sums match, proceeding ... done (neither success nor failure guaranteed)
rm -rf patch-stamp patch-stampT debian/patched
debian/rules build
test -d debian/patched || install -d debian/patched
dpatch apply-all
applying patch 10_config to ./ ... failed.
make: *** [patch-stamp] Error 1[/COLOR]

Original post:
***hostapd+madwifi - need a clear howto***
[http://ubuntuforums.org/showthread.php?t=353715](http://ubuntuforums.org/showthread.php?t=353715)

-----------------------------
[Paris Heng @ Wifi-Linux]("http://parisheng.110mb.com/")

---

