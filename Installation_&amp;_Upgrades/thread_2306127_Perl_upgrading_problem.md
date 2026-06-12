---
title: "Perl upgrading problem"
date: 2015-12-12
forum: Installation &amp; Upgrades
---

### Post by Gran_Bostrm on 2015-12-12
Hi!

I have upgraded my perl program and forgot to upgrade the perl-modules package (don't know how I mananged to do that).

I tried to uninstall the perl-package and then upgrade the perl-modules without success.

```
Reading package lists...Building dependency tree...
Reading state information...
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  consolekit diffstat fcitx-config-common fcitx-config-gtk2 genisoimage
  gettext gir1.2-gnomekeyring-1.0 laptop-detect libapt-pkg-perl
  libasprintf-dev libaudcore2 libck-connector0 libgettextpo-dev libglade2-0
  libjpeg-progs libjpeg-turbo-progs linux-headers-3.19.0-15
  linux-headers-3.19.0-15-generic linux-image-3.19.0-15-generic
  linux-image-extra-3.19.0-15-generic lubuntu-icon-theme lxsession-data
  lxsession-logout pcmanfm policykit-desktop-privileges t1utils
  ttf-ancient-fonts xbacklight
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  perl-modules
Suggested packages:
  libb-lint-perl libcpanplus-dist-build-perl libcpanplus-perl
  libfile-checktree-perl liblog-message-simple-perl liblog-message-perl
  libobject-accessor-perl
Recommended packages:
  libarchive-extract-perl libmodule-pluggable-perl libpod-latex-perl
  libterm-ui-perl libtext-soundex-perl libcgi-pm-perl libmodule-build-perl
  libpackage-constants-perl
The following packages will be upgraded:
  perl-modules
1 upgraded, 0 newly installed, 0 to remove and 709 not upgraded.
2 not fully installed or removed.
Need to get 0 B/2 501 kB of archives.
After this operation, 1 024 B of additional disk space will be used.
Do you want to continue? [Y/n] (Reading database ... 
(Reading database ... 181630 files and directories currently installed.)
Preparing to unpack .../perl-modules_5.20.2-6_all.deb ...
Unpacking perl-modules (5.20.2-6) over (5.20.2-2) ...
dpkg-deb (subprocess): decompressing archive member: lzma error: compressed data is corrupt
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing archive /var/cache/apt/archives/perl-modules_5.20.2-6_all.deb (--unpack):
 cannot copy extracted data for './usr/share/perl/5.20.2/ExtUtils/Constant/ProxySubs.pm' to '/usr/share/perl/5.20.2/ExtUtils/Constant/ProxySubs.pm.dpkg-new': unexpected end of file or stream
Errors were encountered while processing:
 /var/cache/apt/archives/perl-modules_5.20.2-6_all.deb

```

How should I proceed to upgrade the perl-modules package as well?

// Göran

---

### Post by ian-weisser on 2015-12-12
Try:
```
sudo apt-get clean perl-modules   // Delete the corrupt version
sudo apt-get upgrade              // Upgrade what can be upgraded, including perl-modules

sudo apt-get autoremove           // Remove all those orphans
```
How did you manage to orphan consolekit?

---

