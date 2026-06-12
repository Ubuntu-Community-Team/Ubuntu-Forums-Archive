---
title: "Trashed my Perl install"
date: 2008-03-08
forum: Installation &amp; Upgrades
---

### Post by pcsso566 on 2008-03-08
I was following instructions on installing a package on my amd64 ubuntu 7.10 install and toasted my perl install. Here were the instructions (from [http://www.zimbra.com/forums/installation/10306-howto-ubuntu-64bit-install.html):](http://www.zimbra.com/forums/installation/10306-howto-ubuntu-64bit-install.html):)

```
dpkg --force-architecture -i ActivePerl-5.8.8.......blah.blah....deb

mv /usr/bin/perl /usr/bin/perl.ubuntu
ln -s /opt/ActivePerl-5.8/bin/perl /usr/bin/perl.activestate
ln -s /usr/bin/perl.activestate /usr/bin/perl

#INSTALL THE PROGRAM HERE
perl -pi -e 's#/usr/bin/perl#/opt/ActivePerl-5.8/bin/perl#' `find /opt/zimbra -type f -exec grep -l '/usr/bin/perl' {} \;`



# put ubuntu perl back
rm /usr/bin/perl
ln -s /usr/bin/perl.ubuntu /usr/bin/perl

```

Later I was having issues with installing other packages (cause it was still using ActivePerl). I did a unlink on the perl and perl.ubuntu links and now my perl install is messed up.

Isnt there some way to get the installer from the CD to just install perl again like it was? Or am I hosed?


Thanks

Paul

---

