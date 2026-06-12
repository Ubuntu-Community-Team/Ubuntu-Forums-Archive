---
title: "apt-get upgrade: `libgmpxx4ldbl' contains empty filename"
date: 2011-09-02
forum: Installation &amp; Upgrades
---

### Post by qzjul on 2011-09-02
Hi! For the first time today I ran into a problem with APT that I can't figure out...

I'm running ubuntu 8.04 on a server, but the packages relate to apache, so should still be supported

The packages I'm trying to upgrade are:
```

The following packages will be upgraded:
  apache2 apache2-mpm-prefork apache2-prefork-dev apache2-utils apache2.2-common
```


and what happens is this:

```

Fetched 1469kB in 2s (731kB/s)
(Reading database ... dpkg: error processing /var/cache/apt/archives/apache2-prefork-dev_2.2.8-1ubuntu0.21_amd64.deb (--unpack):
 files list file for package `libgmpxx4ldbl' contains empty filename
Errors were encountered while processing:
 /var/cache/apt/archives/apache2-prefork-dev_2.2.8-1ubuntu0.21_amd64.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```



I've tried apt-get clean, apt-get autoremove, apt-get autoclean; rm'ing the packages in /var/cache/apt/archives; but every fresh download of apache2-prefork-dev seems to have the same problem...




I'm thinking this isn't something to do with my setup, but if it is, what should I be looking for?

---

### Post by qzjul on 2011-10-12
I ran into this problem again for a different installation (mediatomb) and through a different file, (libmozjs0d); i followed the directions [http://finkproject.org/faq/usage-fink.php](http://finkproject.org/faq/usage-fink.php) here, which didn't seem to help, but when doing a dpkg -i of the file itself (libmozjs0d) it told me once again:

files list file for package `libgmpxx4ldbl' contains empty filename


I finally opened and edited the .list file for libgmpxx4ldbl which read:


```

ptional
Section: editors
Package: libmono-corlib2.0-cil
Status: install ok installed

Priority: optional
Section: libs
Installed-Size: 2516
Maintainer: Ubuntu Mono Team <ubuntu-mono@lists.ubuntu.com>
Architecture: all
Source: mono
Version: 1.2.6+dfsg-6

```

which i changed to...

```

Optional
Section: editors
Package: libmono-corlib2.0-cil
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 2516
Maintainer: Ubuntu Mono Team <ubuntu-mono@lists.ubuntu.com>
Architecture: all
Source: mono
Version: 1.2.6+dfsg-6

```

And then everything started working (added the O for Optional and removed new line) :)


So maybe this will help somebody some time.

---

