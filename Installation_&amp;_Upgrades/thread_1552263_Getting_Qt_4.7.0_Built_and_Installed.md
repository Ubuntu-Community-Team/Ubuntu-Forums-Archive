---
title: "Getting Qt 4.7.0 Built and Installed"
date: 2010-08-13
forum: Installation &amp; Upgrades
---

### Post by patsissons on 2010-08-13
I wanted to develop using some of the bleeding edge features of the new Qt framework, but there is no easy way to get 4.7.0 installed on lucid.  The build is relatively easy with a few minor annoyances.  So I am just going to detail those annoyances so you don't have to be so annoyed :)

```

# first grab some general require packages
sudo apt-get install build-essential

# now grab the build deps for the current qt (mostly the same as for 4.7.0)
sudo apt-get build-dep qt4-x11

# need to grab some extra libs that are not build deps
sudo apt-get install libphonon-dev libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev

# grab the source package from http://qt.nokia.com/developer/qt-qtcreator-prerelease/ 
wget http://get.qt.nokia.com/qt/source/qt-everywhere-opensource-src-4.7.0-beta2.tar.gz

# now configure qt 4.7.0 with declarative support
# the annoyances here are all the extra includes that are required
# i am installing to $HOME/qt/qt-4.7.0 but feel free to change that
./configure -prefix $HOME/qt/qt-4.7.0 -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2 -opensource -declarative -confirm-license -v 2>&1 | tee config.log

# build (takes a while)
make

# install
make install

```

If anyone out there knows of a PPA that is building Qt 4.7.0, please let me know.  I would be interested to abandon building it manually.

---

### Post by somethingkindawierd on 2010-09-13
Thank you! Worked great :)

I would like to point out that now there is a release-candidate to use instead of the beta:

```
# grab the source package from http://qt.nokia.com/developer/qt-qtcreator-prerelease/ 
wget http://get.qt.nokia.com/qt/source/qt-everywhere-opensource-src-4.7.0-rc1.tar.gz

```

---

### Post by dnc2rt on 2010-09-30
Thank you!

And as Qt 4.7 is released :

```

# grab the source package from http://qt.nokia.com/developer/qt-qtcreator-prerelease/
wget http://get.qt.nokia.com/qt/source/qt-everywhere-opensource-src-4.7.0.tar.gz

```

---

### Post by L_V on 2010-10-03
> **patsissons said:**
> If anyone out there knows of a PPA that is building Qt 4.7.0, please let me know.

```
## kubuntu-ppa backports 
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu lucid main
```

[_27-Sep-2010 - Index of /kubuntu-ppa/backports/ubuntu/pool/main/q/qt4-x11_](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/pool/main/q/qt4-x11/)

---

