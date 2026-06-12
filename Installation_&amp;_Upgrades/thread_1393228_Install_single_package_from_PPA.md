---
title: "Install single package from PPA"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by hotfigs on 2010-01-29
Is it possible to cherry pick packages from a PPA? The problem I'm having is that I'm getting thunderbird 3 from the ubuntu-mozilla-daily PPA, but by adding that to my sources, it is also upgrading firefox.

Is there a way to get thunderbird 3 only and stop it upgrading firefox?

Thanks!

---

### Post by loell on 2010-01-29
That really depends on thunder bird 3 dependencies, if  it could live without firefox's newer version, one way to find out (trial and error way) is to download the thunder bird package at 
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)

---

### Post by kansasnoob on 2010-01-29
You could use Ubuntuzilla:

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

The package names are:

firefox-mozilla-build
thunderbird-mozilla-build
seamonkey-mozilla-build

---

### Post by hotfigs on 2010-01-29
Looks like ubuntuzilla doesn't provide 64 binaries. So there's not some way to filter out packages in a PPA?

---

### Post by mc4man on 2010-01-29
> So there's not some way to filter out packages in a PPA?
Well you can go directly to the ppa package list page, expand the package you're interested in and see what add. packages are listed there that may be deps.
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa/+packages](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa/+packages)

Or just d.click on the package you wish and see what gdebi reports.

Otherwise add the repo, search the package in synaptic and mark for install.
If all is acceptable then install andafter the install disable the ppa so other packages available in the ppa aren't upgraded thru the update manager.

In the case of your thunderbird it appears you can just install it, and then the gnome support package if you wish.

> Package: thunderbird-3.0
Version: 3.0.2~hg20100128r4659+nobinonly-0ubuntu1~umd1~karmic
Architecture: i386
Maintainer: Ubuntu Mozilla Team <ubuntu-mozillateam@lists.ubuntu.com>
Installed-Size: 28776
Depends: fontconfig, psmisc, debianutils (>= 1.16), libasound2 (>> 1.0.18), libatk1.0-0 (>= 1.20.0), libc6 (>= 2.4), libcairo2 (>= 1.6.0), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.78), libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.2.1), libgcc1 (>= 1:4.1.1), libglib2.0-0 (>= 2.16.0), libgtk2.0-0 (>= 2.18.0), libhunspell-1.2-0 (>= 1.2.8), libjpeg62, libnspr4-0d (>= 4.7.3-0ubuntu1~), libnss3-1d (>= 3.12.3), libpango1.0-0 (>= 1.14.0), libstartup-notification0 (>= 0.10), libstdc++6 (>= 4.1.1), libx11-6, libxrender1, libxt6, zlib1g (>= 1:1.1.4)
Recommends: myspell-en-us | hunspell-dictionary | myspell-dictionary
Suggests: thunderbird-3.0-gnome-support (= 3.0.2~hg20100128r4659+nobinonly-0ubuntu1~umd1~karmic), latex-xft-fonts, libthai0

---

