---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by danhm on 2005-10-14
I'm following the apt-get instructions on [https://wiki.ubuntu.com/BreezyUpgrade?highlight=%28breezy%29%7C%28upgrade%29](https://wiki.ubuntu.com/BreezyUpgrade?highlight=%28breezy%29%7C%28upgrade%29)

Everything works great until I type "sudo apt-get dist-upgrade" and I get this error:

> dan@ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  libofx2 openoffice.org1-debian-files planetpenguin-racer-extras psfontmgr
  python-zopeinterface python2.4-epydoc python2.4-zopeinterface
  ttf-bengali-fonts ttf-devanagari-fonts ttf-gujarati-fonts ttf-kannada-fonts
  ttf-oriya-fonts ttf-punjabi-fonts ttf-tamil-fonts ttf-telugu-fonts
  xscreensaver-data
The following packages have been kept back:
  mplayer-386 xfce4-mixer
The following packages will be upgraded:
  gnucash gnucash-common openoffice.org openoffice.org-bin
  openoffice.org-gtk-gnome openoffice.org-l10n-en python-epydoc python-twisted
  python2.4-twisted ttf-indic-fonts tuxracer-extras xscreensaver
12 upgraded, 16 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/77.9MB of archives.
After unpacking 10.6MB of additional disk space will be used.
Do you want to continue [Y/n]? Y

Preconfiguring packages ...
(Reading database ... 115615 files and directories currently installed.)
Unpacking libofx2 (from .../libofx2_1%3a0.8.0-3ubuntu8_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libofx2_1%3a0.8.0-3ubuntu8_i386.deb (--unpack):
 trying to overwrite `/usr/share/libofx/dtd/opensp.dcl', which is also in package libofx0c102
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libofx2_1%3a0.8.0-3ubuntu8_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I don't have a clue what it means.


Also, I had to reboot and the only way to get X to start was to boot into recovery mode. In the regular mode, it would start in the CLI and if I typed "startx" or "gdm" I'd just get a black screen.

---

