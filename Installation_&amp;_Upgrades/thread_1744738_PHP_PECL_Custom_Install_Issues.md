---
title: "PHP PECL Custom Install Issues"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by pythod on 2011-04-30
Hello,

I scoured the web trying to find a solution to this problem. If this question has been posted before, please pardon me.

So, basically I custom compiled PHP 5.3.4 with this command on my 64-bit Ubuntu 2.6.32-31-server 10.04.2 Server with the latest updates applied:

```

cd /usr/local/src/; rm * -fR; cd /usr/local/src/;wget http://museum.php.net/php5/php-5.2.11.tar.gz;wget http://download.suhosin.org/suhosin-patch-5.2.11-0.9.7.patch.gz
cd /usr/local/src/; rm php-5.2.11/ -fR; tar -xzf php-5.2.11.tar.gz; gunzip suhosin-patch-5.2.11-0.9.7.patch.gz;
cd php-5.2.11/; patch -p 1 -i ../suhosin-patch-5.2.11-0.9.7.patch ;touch ac* ;./buildconf --force

CFLAGS="-D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64" ./configure --prefix=/usr --with-config-file-path=/etc/php5/cgi --with-config-file-scan-dir=/etc/php5/cgi/conf.d --mandir=/usr/share/man --disable-debug --disable-pdo --disable-rpath --disable-static --enable-bcmath --enable-calendar --enable-ctype --enable-dbx --enable-discard-path --enable-exif --enable-fastcgi --enable-filepro --enable-force-redirect --enable-ftp --enable-gd-native-ttf --enable-inline-optimization --enable-mbregex --enable-mbstring --enable-memcache --enable-memory-limit --enable-pcntl --enable-pic --enable-session --enable-shmop --enable-simplexml --enable-soap --enable-sockets --enable-suhosin --enable-sysvmsg --enable-sysvsem --enable-sysvshm --enable-track-vars --enable-trans-sid --enable-wddx --enable-xslt --enable-zip --with-bz2 --with-curl=shared,/usr --with-curlwrappers --with-exec-dir=/usr/lib/php5/libexec --with-freetype-dir=shared,/usr --with-gd=shared,/usr --with-gettext --with-gmp=shared,/usr --with-iconv --with-jpeg-dir=shared,/usr --with-kerberos=/usr --with-layout=GNU --with-libxml-dir=/usr --with-mcrypt --with-mhash=shared,/usr --with-mime-magic=/usr/share/file/magic.mime --with-mysql=shared,/usr --with-mysqli=shared,/usr/bin/mysql_config --with-openssl=/usr --without-gdbm --without-mm --without-pdo-sqlite --without-sqlite --with-pcre-regex=/usr --with-pear=/usr/share/php --with-pic --with-png-dir=shared,/usr --with-regex=php --with-system-tzdata --with-tidy=shared,/usr --with-ttf=shared,/usr --with-xml --with-xmlrpc=shared --with-xpm-dir=shared --with-xsl=shared,/usr --with-zlib;make; make install

```I then issued this command to install PHP extensions:

```
pear update-channels;pecl uninstall apc;pecl install apc;pear upgrade PEAR; pear install HTTP; pear install HTTP_Download; pear install HTTP_Header; pear install MIME_Type; pecl install pecl_http
```However, I see that "pecl install XXX" doesn't do any good. i.e. does not install or compile the extensions I need. This is the output I got:

> 
root@web1:/usr# pear update-channels;pecl uninstall apc;pecl install apc;pear upgrade PEAR; pear install HTTP; pear install HTTP_Download; pear install HTTP_Header; pear install MIME_Type; pecl install pecl_http
Updating channel "doc.php.net"
Channel "doc.php.net" is up to date
Updating channel "pear.php.net"
Channel "pear.php.net" is up to date
Updating channel "pecl.php.net"
Channel "pecl.php.net" is up to date
pecl/apc not installed
downloading APC-3.1.6.tgz ...
Starting to download APC-3.1.6.tgz (148,835 bytes)
.................................done: 148,835 bytes
downloading PEAR-1.9.2.tgz ...
Starting to download PEAR-1.9.2.tgz (295,120 bytes)
.............................................................done: 295,120 bytes
downloading HTTP-1.4.1.tgz ...
Starting to download HTTP-1.4.1.tgz (8,635 bytes)
.....done: 8,635 bytes
Did not download optional dependencies: pear/Archive_Zip, pear/MIME_Type, use --alldeps to download automatically
pear/HTTP_Download can optionally use package "pear/Archive_Zip"
pear/HTTP_Download can optionally use package "pear/MIME_Type"
pear/HTTP_Download can optionally use PHP extension "mime_magic"
pear/HTTP_Download can optionally use PHP extension "pgsql"
downloading HTTP_Download-1.1.4.tgz ...
Starting to download HTTP_Download-1.1.4.tgz (14,571 bytes)
.....done: 14,571 bytes
downloading HTTP_Header-1.2.1.tgz ...
Starting to download HTTP_Header-1.2.1.tgz (10,682 bytes)
.....done: 10,682 bytes
Did not download optional dependencies: pear/System_Command, use --alldeps to download automatically
pear/MIME_Type can optionally use package "pear/System_Command"
downloading MIME_Type-1.2.1.tgz ...
Starting to download MIME_Type-1.2.1.tgz (11,609 bytes)
.....done: 11,609 bytes
downloading pecl_http-1.7.0.tgz ...
Starting to download pecl_http-1.7.0.tgz (173,979 bytes)
.....................................done: 173,979 bytes
root@web1:/usr#
I checked to make sure that "noexec" is not set on /etc/fstab for /tmp/ folder.

Here's my /etc/fstab:

```

root@web1:/usr# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md0 during installation
UUID=b9e8630e-0ab7-4297-84f6-4a0f86e4b368 /               xfs     defaults        0       1
# /data was on /dev/md2 during installation
UUID=0efb1bcf-3634-460e-bc64-58f1280cdb20 /data           xfs     defaults        0       2
# /data2 was on /dev/md4 during installation
UUID=695384db-cbbb-4d66-b856-6a2bbed3132a /data2          xfs     defaults        0       2
# /www was on /dev/md3 during installation
UUID=f561aba0-5014-4a2e-aad9-06f350c52888 /www            xfs     defaults        0       2
# swap was on /dev/md1 during installation
UUID=cbba8e61-d715-4c75-827e-714b8f615ca3 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


```Please advise as to what is going on here?

Someone else is facing the same problem on the link I am facing and I do not wish to go through the custom compile route. Here's the link:

[http://www.linuxquestions.org/questions/linux-server-73/pecl-install-wont-work-840608/](http://www.linuxquestions.org/questions/linux-server-73/pecl-install-wont-work-840608/)

Thanks so much!

---

