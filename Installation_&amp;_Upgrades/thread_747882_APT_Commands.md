---
title: "APT Commands"
date: 2008-04-07
forum: Installation &amp; Upgrades
---

### Post by fxars on 2008-04-07
I'm new to the ubuntu/debian distro, I'm more of a RedHat / CentOS guy.

Anyway, if I want to send a query to whatever the default APT repository is for ubuntu, how do I?

Specifically, there doesn't seem to be a full set of man pages for perl.
   man perl
works fine, but there's no
   man perlop
or
   man perlre

Perhaps there's an APT package that includes that.  How could I use an APT command to find that out?

   === Al

---

### Post by tamoneya on 2008-04-07
```
sudo apt-get perl-doc
```
This should work

---

### Post by zvacet on 2008-04-07
[Apt-how to](http://www.debian.org/doc/manuals/apt-howto/)

---

### Post by schiznik on 2008-04-07
apt-cache search pkgname or aptitude search pkgname.

some useful addons to apt that you might want to install are:
apt-listbugs, that queries the bugtracker as you install/update things
apt-file, that shows you which files are installed by what package and vice versa
apt-spy, which will run bandwidth tests to select the most appropriate mirror to use for your location.

---

### Post by fxars on 2008-04-07
Thanks.  That should do me.
  === Al

---

