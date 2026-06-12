---
title: "Install php5 from source on ubuntu desktop 7.10"
date: 2007-11-26
forum: Installation &amp; Upgrades
---

### Post by rob_b on 2007-11-26
Hi everyone,
I'm new to ubuntu (I come from windows).
I'm trying to set up my LAMP machine and everything worked fine until it came to php.
I'm installing everything from source because I feel I've got better control of what's happening on my computer.
I'm using ubuntu desktop 7.10, apache2.2, mysql5, php5.2.5.
These are my command for the php installation.

sudo ./configure --prefix=/usr/local/php5 \
 --with-mysql=/usr/local/mysql \
 --with-apxs2=/usr/local/apache2/bin/apxs

sudo make

sudo make test

which outputs: Bug #16069 (ICONV transliteration failure) ....

sudo make install

here's what i find in /usr/local/php5:
bin, etc, include, lib, man. NO sign of the php.ini files.


in apache's httpd.conf file I can see that 'LoadModule php5_module  modules/libphp5.so'
has been added, but if I run (once restarted apache) ./httpd -l I can't see the php module.

php files don't work in apache, but ./php -v outputs Zend Engine v2.2.0 ... therefore I assume php is install but doesn't work on apache. 

Can anyone help me please. Where are the php.ini files?

Thanks 

Rob

---

