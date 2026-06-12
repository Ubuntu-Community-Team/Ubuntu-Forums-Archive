---
title: "Install a Perl module"
date: 2006-07-14
forum: Installation &amp; Upgrades
---

### Post by Hieronimus on 2006-07-14
Hi all

I'm trying to compile the latest version of xfce and thunar. To do that I need to install a Perl module called URI::file (I think: Perl's not my area of expertise).

The module ./configure and make perfectly, but whenever I try to make install I get the error:
mkdir /usr/local/man: File exists at /usr/share/perl/5.8/ExtUtils/Install.pm line 112
make: *** [pure_site_install] Error 2


I always run make install as root (sudo -s), so I don't understand. Could anyone give me a hand?

---

