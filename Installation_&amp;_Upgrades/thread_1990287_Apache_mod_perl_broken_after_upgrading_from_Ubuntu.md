---
title: "Apache mod_perl broken after upgrading from Ubuntu 11.10 to 12.04"
date: 2012-05-29
forum: Installation &amp; Upgrades
---

### Post by Bobbis2000 on 2012-05-29
Kind of a newb at this..
When I upgrade our webserver from Ubuntu to 12.04, I get the following when I start apache:
"apache2: Syntax error on line 214 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/httpd.conf: Cannot load /usr/lib/apache2/modules/mod_perl.so into server: libperl.so.5.12: cannot open shared object file: No such file or directory"

Basically, line 214 of apache2.conf points to the httpd.conf file which has one line in it:
LoadModule perl_module /usr/lib/apache2/modules/mod_perl.so

I checked and there is a mod_perl.so file in /usr/lib/apache2/modules/
I think that file is trying to evoke /usr/lib/liberperl.so.5.12 but that file is no longer there after the upgrade and has been replaced by libperl.so.5.14

This is where I get dumb and don't know what to do from here.  Any ideas how to get it working again?

Thanks,
Rob

---

