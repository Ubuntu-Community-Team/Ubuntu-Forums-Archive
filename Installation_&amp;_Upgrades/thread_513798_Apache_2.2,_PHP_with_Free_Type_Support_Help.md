---
title: "Apache 2.2, PHP with Free Type Support Help"
date: 2007-07-30
forum: Installation &amp; Upgrades
---

### Post by jugend on 2007-07-30
I've been having a hard time to install PHP GD with Freetype support, hope you guys can help me  out of this.

Envrionment: Apache 2.2, PHP 5.1.6, Ubuntu 6,06 LTS

I used the following configuration command:

'./configure' '--prefix=/usr/local/apache2/php' '--with-zlib' '--with-xml' '--with-ldap=/usr' '--enable-cli' '--with-zlib-dir=/usr' '--enable-exif' '--enable-ftp' '--enable-mbstring' '--enable-mbregex' '--enable-dbx' '--enable-sockets' '--with-curl=/usr' '--with-mysql' '--with-gd' '--with-freetype-dir' '--with-t1lib' '--enable-gd-native-ttf' '--with-jpeg-dir' '--with-png-dir' '--with-apxs2=/usr/local/apache2/bin/apxs' '--with-config-file-path=/usr/local/apache2/php'

Shown the following log:

checking OpenSSL dir for FTP... no
checking for GD support... yes
checking for the location of libjpeg... yes
checking for the location of libpng... yes
checking for the location of libXpm... no
checking for FreeType 1.x support... no
checking for FreeType 2... yes
checking for T1lib support... yes
checking whether to enable truetype string function in GD... yes
checking whether to enable JIS-mapped Japanese font support in GD... no

And this is shown in PHP info, the Freetype was never enabled:
GD Support 	enabled
GD Version 	bundled (2.0.28 compatible)
GIF Read Support 	enabled
GIF Create Support 	enabled
JPG Support 	enabled
PNG Support 	enabled
WBMP Support 	enabled
XBM Support 	enabled

I've probably missed out something, wil be grateful for any help. Thanks!

---

