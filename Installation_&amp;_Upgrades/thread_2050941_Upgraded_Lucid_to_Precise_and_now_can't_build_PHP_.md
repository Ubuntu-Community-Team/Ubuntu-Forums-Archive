---
title: "Upgraded Lucid to Precise and now can't build PHP from source"
date: 2012-08-31
forum: Installation &amp; Upgrades
---

### Post by specialcase on 2012-08-31
After downloading and extracting PHP and doing a 'cd' into the directory, I've done the following without incident for the past six months or so:

```
./configure --with-curl --with-pear --with-gd --with-jpeg-dir --with-png-dir --with-zlib --with-xpm-dir --with-freetype-dir --with-t1lib --with-mcrypt --with-mhash --with-mysql --with-mysqli --with-pdo-mysql --with-openssl --with-xmlrpc --with-xsl --with-bz2 --with-gettext --enable-exif --enable-wddx --enable-zip --enable-bcmath --enable-calendar --enable-ftp --enable-mbstring --enable-soap --enable-sockets --enable-sqlite-utf8 --enable-shmop --enable-dba --enable-sysvmsg --enable-sysvsem --enable-sysvshm --with-fpm-user=www-data --with-fpm-group=www-data --enable-fpm

```Which today output this lovely error:

```
checking for the location of libXpm... yes
checking for FreeType 2... yes
checking for T1lib support... yes
checking whether to enable truetype string function in GD... no
checking whether to enable JIS-mapped Japanese font support in GD... no
checking for fabsf... yes
checking for floorf... yes
checking for jpeg_read_header in -ljpeg... yes
checking for png_write_image in -lpng... yes
configure: error: libXpm.(a|so) not found.

```It said "yes" to finding the location of libXpm and then failed to find it.

I just upgraded yesterday from Lucid (10.04 LTS) to Precise (12.04.1 LTS) on my server and I'm working through the fallout of that upgrade.  I think I was using a 32-bit version and upgrading to Precise seems to have moved to a 64-bit version.  I'm crossing my fingers that my server isn't hosed but it has already survived two reboot cycles without issue after the upgrade.  Upgrading PHP is something I do once a month, so the 'configure' command hasn't changed but libXpm apparently can no longer be found.  So, I tried:

```
sudo apt-get install libxpm-dev
```And got:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
libxpm-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```So then I tried removing and installing libxpm-dev again (apt-get remove then apt-get install).  Nothing changed.  Searching the system for libXpm* using 'find', I found the relevant files in:

/usr/lib/x86_64-linux-gnu/

```
/usr/lib/x86_64-linux-gnu$ ls -la libXpm*
-rw-r--r-- 1 root root 122804 Nov 11  2011 libXpm.a
lrwxrwxrwx 1 root root     16 Nov 11  2011 libXpm.so -> libXpm.so.4.11.0
lrwxrwxrwx 1 root root     16 Nov 11  2011 libXpm.so.4 -> libXpm.so.4.11.0
-rw-r--r-- 1 root root  68288 Nov 11  2011 libXpm.so.4.11.0

```These are the only binaries on the system, so I assume they are the correct ones.  Based on some Google searches, I tried adding "--with-libdir=/usr/lib/x86_64-linux-gnu" and got the same error.  I'm at a loss at this point.

Oh yeah, 'uname -a':

```
Linux [redacted] 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```And 'lsb_release -a':

```
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.1 LTS
Release:        12.04
Codename:       precise

```Hopefully someone knows what to do here.

---

### Post by specialcase on 2012-09-01
I solved the issue:

```
--with-libdir=/lib/x86_64-linux-gnu
```

Without it, I had errors.  With it, everything built cleanly.

---

