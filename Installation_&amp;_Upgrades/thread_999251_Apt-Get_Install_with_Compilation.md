---
title: "Apt-Get Install with Compilation"
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by Mr.Macdonald on 2008-12-01
Is it possible to have apt-get install a package by downloading the source and then compiling.

I tried
> sudo apt-get install firefox --compile
but I got errors, heres output
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Need to get 11.3MB of source archives.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main firefox-3.0 3.0.4+nobinonly-0ubuntu0.8.04.1 (dsc) [2073B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main firefox-3.0 3.0.4+nobinonly-0ubuntu0.8.04.1 (tar) [11.2MB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main firefox-3.0 3.0.4+nobinonly-0ubuntu0.8.04.1 (diff) [106kB]
Fetched 11.3MB in 22s (507kB/s)                                                
gpg: new configuration file `/root/.gnupg/gpg.conf' created
gpg: WARNING: options in `/root/.gnupg/gpg.conf' are not yet active during this run
gpg: Signature made Thu 13 Nov 2008 07:38:08 AM PST using DSA key ID 174BF01A
gpg: Can't check signature: public key not found
dpkg-source: extracting firefox-3.0 in firefox-3.0-3.0.4+nobinonly
dpkg-source: unpacking firefox-3.0_3.0.4+nobinonly.orig.tar.gz
dpkg-source: applying ./firefox-3.0_3.0.4+nobinonly-0ubuntu0.8.04.1.diff.gz
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package firefox-3.0
dpkg-buildpackage: source version 3.0.4+nobinonly-0ubuntu0.8.04.1
dpkg-buildpackage: source changed by Alexander Sack <asac@ubuntu.com>
dpkg-buildpackage: host architecture i386
dpkg-checkbuilddeps: Unmet build dependencies: cdbs debhelper (>= 5) sharutils m4 autotools-dev autoconf2.13 quilt patchutils (>= 0.2.25) zlib1g-dev libx11-dev libxt-dev libgtk2.0-dev (>= 2.10) liborbit2-dev libidl-dev (>= 0.8.0) libxft-dev libfreetype6-dev libpng12-dev libjpeg62-dev libxrender-dev libxinerama-dev libcairo2-dev libpixman-1-dev libgnome2-dev libgconf2-dev libgnomevfs2-dev libgnomeui-dev libhunspell-dev libdbus-glib-1-dev (>= 0.60) xulrunner-1.9-dev (>= 1.9.0.1) libnss3-dev mozilla-devscripts (>= 0.06~)
dpkg-buildpackage: warning: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: warning: (Use -d flag to override.)
Build command 'cd firefox-3.0-3.0.4+nobinonly && dpkg-buildpackage -b -uc' failed.
E: Child process failed


why doesn't apt-get fix dependencies

---

### Post by Mr.Macdonald on 2008-12-01
This would be similar to Gentoo's package installing

---

### Post by Partyboi2 on 2008-12-01
try installing the dependencies first 
```
sudo apt-get build-dep firefox
```
```
apt-get source --compile firefox 
```

---

### Post by Mr.Macdonald on 2008-12-01
does build-dep compile the dependencies

---

### Post by Partyboi2 on 2008-12-01
build-dep will install all the dev packages (dependencies)  that are required to compile it.

---

### Post by Mr.Macdonald on 2008-12-01
the build-dep worked, but I am guessing that it doesn't install dependencies by compiling the source, right?

And oh does it take forever to compile!

---

### Post by Partyboi2 on 2008-12-01
correct :)

---

