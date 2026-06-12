---
title: "missing links in /etc/php/8.1/apache2/conf.d/"
date: 2022-12-19
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2022-12-19
Trying retrace what I've done as best as I can, but mat miss a step or two.

I'm using Nextcloud in my Ubuntu server (Ubuntu 20.04.5 LTS) and wanted to change the Apache php version from 7.4 to 8.1.
I diabled the 7.4 mod and enabled the 8.1 mod
I tested the server and everyting worked fine
I then installed bcmath and noticed that I had some obsolete 8.1 packages. Not sure why they were obsolute given that apache was using 8.1; the rest of the server was still on 7.4.
I then did something stupid and removed the obsolete packages

The website then stopped working, because amongst other things the mysql apache mod was removed

Follwoing are the mods for 7.4
```
llist@mail1:/etc/php/8.1/apache2$ ls -lsa /etc/php/7.4/apache2/conf.d/
total 8
4 drwxr-xr-x 2 root root 4096 Dec 11 01:07 .
4 drwxr-xr-x 3 root root 4096 Nov 17 23:32 ..
0 lrwxrwxrwx 1 root root   39 Apr 25  2021 10-mysqlnd.ini -> /etc/php/7.4/mods-available/mysqlnd.ini
0 lrwxrwxrwx 1 root root   39 Apr 25  2021 10-opcache.ini -> /etc/php/7.4/mods-available/opcache.ini
0 lrwxrwxrwx 1 root root   35 Apr 25  2021 10-pdo.ini -> /etc/php/7.4/mods-available/pdo.ini
0 lrwxrwxrwx 1 root root   35 Apr 25  2021 15-xml.ini -> /etc/php/7.4/mods-available/xml.ini
0 lrwxrwxrwx 1 root root   38 Apr 25  2021 20-bcmath.ini -> /etc/php/7.4/mods-available/bcmath.ini
0 lrwxrwxrwx 1 root root   35 Apr 25  2021 20-bz2.ini -> /etc/php/7.4/mods-available/bz2.ini
0 lrwxrwxrwx 1 root root   40 Apr 25  2021 20-calendar.ini -> /etc/php/7.4/mods-available/calendar.ini
0 lrwxrwxrwx 1 root root   37 Apr 25  2021 20-ctype.ini -> /etc/php/7.4/mods-available/ctype.ini
0 lrwxrwxrwx 1 root root   36 Apr 25  2021 20-curl.ini -> /etc/php/7.4/mods-available/curl.ini
0 lrwxrwxrwx 1 root root   35 Apr 25  2021 20-dom.ini -> /etc/php/7.4/mods-available/dom.ini
0 lrwxrwxrwx 1 root root   36 Apr 25  2021 20-exif.ini -> /etc/php/7.4/mods-available/exif.ini
0 lrwxrwxrwx 1 root root   35 Apr 25  2021 20-ffi.ini -> /etc/php/7.4/mods-available/ffi.ini
0 lrwxrwxrwx 1 root root   40 Apr 25  2021 20-fileinfo.ini -> /etc/php/7.4/mods-available/fileinfo.ini
0 lrwxrwxrwx 1 root root   35 Apr 25  2021 20-ftp.ini -> /etc/php/7.4/mods-available/ftp.ini
0 lrwxrwxrwx 1 root root   34 Apr 25  2021 20-gd.ini -> /etc/php/7.4/mods-available/gd.ini
0 lrwxrwxrwx 1 root root   39 Apr 25  2021 20-gettext.ini -> /etc/php/7.4/mods-available/gettext.ini
0 lrwxrwxrwx 1 root root   35 Apr 26  2021 20-gmp.ini -> /etc/php/7.4/mods-available/gmp.ini
0 lrwxrwxrwx 1 root root   37 Apr 25  2021 20-iconv.ini -> /etc/php/7.4/mods-available/iconv.ini
0 lrwxrwxrwx 1 root root   40 Dec 11 01:06 20-igbinary.ini -> /etc/php/7.4/mods-available/igbinary.ini
0 lrwxrwxrwx 1 root root   39 Dec 11 01:06 20-imagick.ini -> /etc/php/7.4/mods-available/imagick.ini
0 lrwxrwxrwx 1 root root   36 Apr 25  2021 20-intl.ini -> /etc/php/7.4/mods-available/intl.ini
0 lrwxrwxrwx 1 root root   36 Apr 25  2021 20-json.ini -> /etc/php/7.4/mods-available/json.ini
0 lrwxrwxrwx 1 root root   40 Apr 25  2021 20-mbstring.ini -> /etc/php/7.4/mods-available/mbstring.ini
0 lrwxrwxrwx 1 root root   38 Apr 25  2021 20-mysqli.ini -> /etc/php/7.4/mods-available/mysqli.ini
0 lrwxrwxrwx 1 root root   41 Apr 25  2021 20-pdo_mysql.ini -> /etc/php/7.4/mods-available/pdo_mysql.ini
0 lrwxrwxrwx 1 root root   36 Apr 25  2021 20-phar.ini -> /etc/php/7.4/mods-available/phar.ini
0 lrwxrwxrwx 1 root root   37 Apr 25  2021 20-posix.ini -> /etc/php/7.4/mods-available/posix.ini
0 lrwxrwxrwx 1 root root   40 Apr 25  2021 20-readline.ini -> /etc/php/7.4/mods-available/readline.ini
0 lrwxrwxrwx 1 root root   37 Dec 11 01:07 20-redis.ini -> /etc/php/7.4/mods-available/redis.ini
0 lrwxrwxrwx 1 root root   37 Apr 25  2021 20-shmop.ini -> /etc/php/7.4/mods-available/shmop.ini
0 lrwxrwxrwx 1 root root   41 Apr 25  2021 20-simplexml.ini -> /etc/php/7.4/mods-available/simplexml.ini
0 lrwxrwxrwx 1 root root   39 Apr 25  2021 20-sockets.ini -> /etc/php/7.4/mods-available/sockets.ini
0 lrwxrwxrwx 1 root root   39 Apr 25  2021 20-sysvmsg.ini -> /etc/php/7.4/mods-available/sysvmsg.ini
0 lrwxrwxrwx 1 root root   39 Apr 25  2021 20-sysvsem.ini -> /etc/php/7.4/mods-available/sysvsem.ini
0 lrwxrwxrwx 1 root root   39 Apr 25  2021 20-sysvshm.ini -> /etc/php/7.4/mods-available/sysvshm.ini
0 lrwxrwxrwx 1 root root   41 Apr 25  2021 20-tokenizer.ini -> /etc/php/7.4/mods-available/tokenizer.ini
0 lrwxrwxrwx 1 root root   41 Apr 25  2021 20-xmlreader.ini -> /etc/php/7.4/mods-available/xmlreader.ini
0 lrwxrwxrwx 1 root root   41 Apr 25  2021 20-xmlwriter.ini -> /etc/php/7.4/mods-available/xmlwriter.ini
0 lrwxrwxrwx 1 root root   35 Apr 25  2021 20-xsl.ini -> /etc/php/7.4/mods-available/xsl.ini
0 lrwxrwxrwx 1 root root   35 Apr 25  2021 20-zip.ini -> /etc/php/7.4/mods-available/zip.ini

```

And this is for 8.1
```
llist@mail1:/etc/php/8.1/apache2$ ls -lsa /etc/php/8.1/apache2/conf.d/
total 8
4 drwxr-xr-x 2 root root 4096 Dec 20 01:46 .
4 drwxr-xr-x 3 root root 4096 Dec 20 01:18 ..
0 lrwxrwxrwx 1 root root   39 Jan 18  2022 10-opcache.ini -> /etc/php/8.1/mods-available/opcache.ini
0 lrwxrwxrwx 1 root root   35 Jan 18  2022 10-pdo.ini -> /etc/php/8.1/mods-available/pdo.ini
0 lrwxrwxrwx 1 root root   35 Jan 18  2022 15-xml.ini -> /etc/php/8.1/mods-available/xml.ini
0 lrwxrwxrwx 1 root root   38 Dec 20 01:44 20-bcmath.ini -> /etc/php/8.1/mods-available/bcmath.ini
0 lrwxrwxrwx 1 root root   40 Jan 18  2022 20-calendar.ini -> /etc/php/8.1/mods-available/calendar.ini
0 lrwxrwxrwx 1 root root   37 Jan 18  2022 20-ctype.ini -> /etc/php/8.1/mods-available/ctype.ini
0 lrwxrwxrwx 1 root root   35 Jan 18  2022 20-dom.ini -> /etc/php/8.1/mods-available/dom.ini
0 lrwxrwxrwx 1 root root   36 Jan 18  2022 20-exif.ini -> /etc/php/8.1/mods-available/exif.ini
0 lrwxrwxrwx 1 root root   35 Jan 18  2022 20-ffi.ini -> /etc/php/8.1/mods-available/ffi.ini
0 lrwxrwxrwx 1 root root   40 Jan 18  2022 20-fileinfo.ini -> /etc/php/8.1/mods-available/fileinfo.ini
0 lrwxrwxrwx 1 root root   35 Jan 18  2022 20-ftp.ini -> /etc/php/8.1/mods-available/ftp.ini
0 lrwxrwxrwx 1 root root   39 Jan 18  2022 20-gettext.ini -> /etc/php/8.1/mods-available/gettext.ini
0 lrwxrwxrwx 1 root root   37 Jan 18  2022 20-iconv.ini -> /etc/php/8.1/mods-available/iconv.ini
0 lrwxrwxrwx 1 root root   40 Dec 11 01:07 20-igbinary.ini -> /etc/php/8.1/mods-available/igbinary.ini
0 lrwxrwxrwx 1 root root   36 Jan 18  2022 20-phar.ini -> /etc/php/8.1/mods-available/phar.ini
0 lrwxrwxrwx 1 root root   37 Jan 18  2022 20-posix.ini -> /etc/php/8.1/mods-available/posix.ini
0 lrwxrwxrwx 1 root root   40 Jan 18  2022 20-readline.ini -> /etc/php/8.1/mods-available/readline.ini
0 lrwxrwxrwx 1 root root   37 Jan 18  2022 20-shmop.ini -> /etc/php/8.1/mods-available/shmop.ini
0 lrwxrwxrwx 1 root root   41 Jan 18  2022 20-simplexml.ini -> /etc/php/8.1/mods-available/simplexml.ini
0 lrwxrwxrwx 1 root root   39 Jan 18  2022 20-sockets.ini -> /etc/php/8.1/mods-available/sockets.ini
0 lrwxrwxrwx 1 root root   39 Jan 18  2022 20-sysvmsg.ini -> /etc/php/8.1/mods-available/sysvmsg.ini
0 lrwxrwxrwx 1 root root   39 Jan 18  2022 20-sysvsem.ini -> /etc/php/8.1/mods-available/sysvsem.ini
0 lrwxrwxrwx 1 root root   39 Jan 18  2022 20-sysvshm.ini -> /etc/php/8.1/mods-available/sysvshm.ini
0 lrwxrwxrwx 1 root root   41 Jan 18  2022 20-tokenizer.ini -> /etc/php/8.1/mods-available/tokenizer.ini
0 lrwxrwxrwx 1 root root   41 Jan 18  2022 20-xmlreader.ini -> /etc/php/8.1/mods-available/xmlreader.ini
0 lrwxrwxrwx 1 root root   41 Jan 18  2022 20-xmlwriter.ini -> /etc/php/8.1/mods-available/xmlwriter.ini
0 lrwxrwxrwx 1 root root   35 Jan 18  2022 20-xsl.ini -> /etc/php/8.1/mods-available/xsl.ini

```

I tried to reinstall 8.1, but that didn't work

---

