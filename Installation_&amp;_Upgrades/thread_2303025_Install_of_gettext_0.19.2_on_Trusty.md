---
title: "Install of gettext 0.19.2 on Trusty"
date: 2015-11-15
forum: Installation &amp; Upgrades
---

### Post by cscj01 on 2015-11-15
I have Ubuntu 14.04.3 x64, and I am trying to use a process from Elle Stone [http://ninedegreesbelow.com/photography/build-gimp-in-prefix-for-artists.html]("http://ninedegreesbelow.com/photography/build-gimp-in-prefix-for-artists.html") to install a git version of Gimp.  When I try to do the steps to install gdk-pixbuf```
cd $SRC_DIR/gdk-pixbuf
./autogen.sh --prefix=$PREFIX
make -j3
make -j3 install
```the ./autogen.sh step gives me an error```
autoreconf: Entering directory `.'
autoreconf: running: autopoint --force
autopoint: *** The AM_GNU_GETTEXT_VERSION declaration in your configure.ac
               file requires the infrastructure from gettext-0.19 but this version
               is older. Please upgrade to gettext-0.19 or newer.
autopoint: *** Stop.
autoreconf: autopoint failed with exit status: 1
```I looked for gettext and found versions at [http://ftp.gnu.org/gnu/gettext/]("http://ftp.gnu.org/gnu/gettext/") as *.tar.gz files.  I have never installed from a *.tar.gz file before.  What I am wondering about is can I install it in the folders I have set up for this git environment, and if so, do I need to modify anything in the tar.gz file to make sure it doesn't overlay my release version?

I checked trusty-backports, but gettext is not in there, so I am a little concerned about overlaying my existing gettext version with one of the newer ones.

---

### Post by Vladlenin5000 on 2015-11-15
[http://packages.ubuntu.com/search?keywords=gettext](http://packages.ubuntu.com/search?keywords=gettext)

---

### Post by cscj01 on 2015-11-15
> **Vladlenin5000 said:**
> [http://packages.ubuntu.com/search?keywords=gettext](http://packages.ubuntu.com/search?keywords=gettext)This link has a package for gettext with the correct version, but it is for Vivid.  If I install it (plus the dependencies such as libgomp1 which Trusty doesn't have at the needed level), I'll be installing over my existing package releases for Trusty.  That would be installing software that may or may not work in Trusty.  So I still have the issue of how to install it in the git structure I built.  Normally trusty-backports would have at least tested the versions included in it on Trusty.  This would be an untested install (if I understand things correctly).

---

### Post by cscj01 on 2015-11-20
I resolved this by installing gettext in the proper folder in my git structure.  I set up my environment variables to point to the correct location, and the install worked perfectly.  I did not install over my system copy.

---

