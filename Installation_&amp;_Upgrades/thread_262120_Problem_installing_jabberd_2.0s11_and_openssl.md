---
title: "Problem installing jabberd 2.0s11 and openssl"
date: 2006-09-21
forum: Installation &amp; Upgrades
---

### Post by pkutter on 2006-09-21
Ubuntu 6.06
jabberd 2.0s11 from source
openssl 0.9.8a-7 from synaptic package manager
mysql-server5.022 from synaptic package manager

I first installed jabberd from the synaptic package manager. After having lots of problems connecting it to mysql I removed it and am now trying to compile jabberd 2.0s11 from source and getting a compile error.

I run
sudo ./configure --enable-mysql --enable-ssl --enable-debug

And I get (snip from compile output)
checking stringprep.h usability... yes
checking stringprep.h presence... yes
checking for stringprep.h... yes
checking for stringprep_check_version in -lidn... yes
checking for Libidn version >= 0.3.0... yes
checking openssl/crypto.h usability... no
checking openssl/crypto.h presence... no
checking for openssl/crypto.h... no
configure: error: OpenSSL >= 0.9.6b not found


It appears that I have the wrong version of openssl. I didn't find an older version in synaptic package manager. Is there a way to make it work with this one, or is there an easy way to get the right one in here?

Sorry, I 'm still kind of new to ubuntu/linux, any help would be much appreciated.

Thanks,
Pete

---

### Post by pkutter on 2006-09-21
I've done a little more research. I found the older version of openssl here
[http://www.openssl.org/source/](http://www.openssl.org/source/)

I went to remove openssl 0.9.8a and it also wanted to remove apache 2, libcurl, openoffice and about 20 other packages. The apache took me a while to configure (for a different service) so I really don't want to break that. Can I have 2 different versions of openssl installed at the same time. If not can anyone tell me how I could get both apache2 and jabberd installed on the same machine?

Thanks,
Pete

---

