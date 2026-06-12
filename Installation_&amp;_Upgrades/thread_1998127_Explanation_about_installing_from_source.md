---
title: "Explanation about installing from source"
date: 2012-06-06
forum: Installation &amp; Upgrades
---

### Post by M@htte0 on 2012-06-06
Good morning,
I am writing because of a behavior I do not understand. It surely is my fault, but please help.

I manage two Ubuntu servers, a virtual one, which I use for testing, and a physical one, whose space I sell to my clients.

They both run 8.04 on i686 architecture, but I needed latest version of proFTPd because of its features, so I decided to try and install it from source. After testing on the virtual machine, I found the following command, issued in the decompressed source tarball folder, to work:
```
dh_make -n -m
```
```
./configure --prefix=/usr \
--sysconfdir=/etc/proftpd \
--localstatedir=/var/run \
--libexecdir=/usr/lib/proftpd \
--disable-auth-file \
--enable-ctrls \
--enable-dso \
--enable-nls \
--enable-facl \
--with-modules=mod_facl:mod_ctrls_admin \
--with-shared=mod_ban:mod_quotatab:mod_quotatab_sql:mod_rewrite:mod_sql:mod_sql_mysql:mod_ifsession:mod_site_misc \
--with-includes=/usr/include/mysql
```
```
sudo debuild binary
```
```
sudo apt-get remove proftpd proftpd-doc proftpd-mysql
```
```
sudo dpkg -i ../*package_name*
```

The thing I do not understand is that, when I run those exact command on the physical machine, they did not work. Installing the package actually deleted the installed binaries, and I solved by removing the packages installed from the repos and running ```
debuild binary
``` again. That installed the program without the need of dpkg-ing the debs.

Is that expected? How come it did not work that way on the virtual machine?

Thank you for your help.

---

