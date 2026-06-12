---
title: "Compiling Apache2 in Ubuntu 12.04: OpenSSL version too old?"
date: 2013-04-09
forum: Installation &amp; Upgrades
---

### Post by JumpZero on 2013-04-09
I am trying to compile Apache 2.4.4 with proxy and SSL modules, but when I run configure:

./configure --enable-so --enable-mods-shared="proxy cache ssl all" --prefix="/etc/apache2" --with-included-apr --with-pcre=/usr/local/pcre

I get the error below:

```
checking whether to enable mod_ssl... checking dependencies
checking for OpenSSL... checking for user-provided OpenSSL base directory... none
checking for OpenSSL version >= 0.9.7... FAILED
configure: WARNING: OpenSSL version is too old
no
checking whether to enable mod_ssl... configure: error: mod_ssl has been requested but can not be built due to prerequisite failures
```

But when I run "openssl version" I see that I have 1.0.1, clearly higher than 0.9.7:
OpenSSL 1.0.1 14 Mar 2012

Nevertheless, I tried downloading the most recent OpenSSL, configuring it as follows:

./config --prefix=/usr zlib-dynamic --openssldir=/etc/ssl shared

But when I run make this too errors out with the following:

```
make[3]: Entering directory `/home/ryan/Downloads/openssl-1.0.1e'
make[4]: Entering directory `/home/ryan/Downloads/openssl-1.0.1e'
libcrypto.a(c_enc.o): In function `CAST_encrypt':
c_enc.c:(.text+0x0): multiple definition of `CAST_encrypt'
libcrypto.a(cast-586.o):cast-586.s:(.text+0x0): first defined here
libcrypto.a(c_enc.o): In function `CAST_decrypt':
c_enc.c:(.text+0x590): multiple definition of `CAST_decrypt'
libcrypto.a(cast-586.o):cast-586.s:(.text+0x4b0): first defined here
libcrypto.a(c_enc.o): In function `CAST_cbc_encrypt':
c_enc.c:(.text+0xaf0): multiple definition of `CAST_cbc_encrypt'
libcrypto.a(cast-586.o):cast-586.s:(.text+0x950): first defined here
collect2: ld returned 1 exit status
make[4]: *** [link_a.gnu] Error 1
make[4]: Leaving directory `/home/ryan/Downloads/openssl-1.0.1e'
make[3]: *** [do_linux-shared] Error 2
make[3]: Leaving directory `/home/ryan/Downloads/openssl-1.0.1e'
make[2]: *** [libcrypto.so.1.0.0] Error 2
make[2]: Leaving directory `/home/ryan/Downloads/openssl-1.0.1e'
make[1]: *** [shared] Error 2
make[1]: Leaving directory `/home/ryan/Downloads/openssl-1.0.1e/crypto'
make: *** [build_crypto] Error 1

```

All installed packages on my system are up to date, and I have run "apt-get build-dep openssl" just to be sure.

I have reached a point where I can't seem to find any more applicable leads on google, so any insight would be greatly appreciated!

---

### Post by MAFoElffen on 2013-04-09
You installed the openssl deb package that provides opensll services... but, not possitive, but isn't this error looking for the openssl source packages? Or a symlink to those?
[https://launchpad.net/ubuntu/precise/+source/openssl](https://launchpad.net/ubuntu/precise/+source/openssl)

---

### Post by JumpZero on 2013-04-09
Unfortunately I don't believe so.  From Apache's documentation:

[COLOR=#003366][FONT=Courier New]**--with-ssl=**[/FONT][/COLOR]DIR
[COLOR=#003366][FONT=Arial]If [/FONT][/COLOR][mod_ssl]("http://httpd.apache.org/docs/2.2/mod/mod_ssl.html")[COLOR=#003366][FONT=Arial] has been enabled [/FONT][/COLOR]configure[COLOR=#003366][FONT=Arial] searches for an installed OpenSSL. You can set the directory path to the SSL/TLS toolkit instead.[/FONT][/COLOR]


I did give it a shot, specifying the openssl source directory, but it was a no-go.

---

### Post by JumpZero on 2013-04-09
Problem solved.

I had to run "make clean" to get openssl to compile, and once that was done apache installed with no further issues.

---

