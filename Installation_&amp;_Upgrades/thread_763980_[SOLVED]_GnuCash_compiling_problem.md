---
title: "[SOLVED] GnuCash compiling problem"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by borobudur on 2008-04-23
I'm trying to compile GnuCash with some special options. I'm following this wiki:

[http://wiki.gnucash.org/wiki/Debian](http://wiki.gnucash.org/wiki/Debian)

When I run this: 
```
moi@ubuntu:~/gnucash/gnucash-2.2.1$ dpkg-buildpackage -b -us -uc -rfakeroot
```I get this error:
```
dpkg-buildpackage: source package is gnucash
dpkg-buildpackage: source version is 2.2.1-1ubuntu4.1
dpkg-buildpackage: source changed by moi <moi@ubuntu>
dpkg-buildpackage: host architecture amd64
dpkg-buildpackage: source version without epoch 2.2.1-1ubuntu4.1
dpkg-checkbuilddeps: Unmet build dependencies: libltdl3-dev ofx (>= 1:0.8.0-8) guile-1.6-dev m4 zlib1g-dev libjpeg62-dev liborbit-dev libungif4-dev libglib2.0-dev (>= 2.4.7) libxml2-dev (>= 2.4.16) libbonobo2-dev (>= 2.0.0) libgnomevfs2-dev (>= 2.2.0) libgtk2.0-dev (>= 2.4.13) libglade2-dev (>= 2.3.6) libgnomeprint2.2-dev (>= 2.8.0) libart-2.0-dev (>= 2.3.11) libgconf2-dev libgnomeui-dev (>= 2.0.0) libgsf-gnome-1-dev (>= 1.12.2) libpango1.0-dev (>= 1.6.0) libgtkhtml3.8-dev libgoffice-0-dev imagemagick swig quilt
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)

```Then I add the -d flag:
```
moi@ubuntu:~/gnucash/gnucash-2.2.1$ dpkg-buildpackage -b -us -uc -rfakeroot -d
```and get this:
```
dpkg-buildpackage: source package is gnucash
dpkg-buildpackage: source version is 2.2.1-1ubuntu4.1
dpkg-buildpackage: source changed by moi <moi@ubuntu>
dpkg-buildpackage: host architecture amd64
dpkg-buildpackage: source version without epoch 2.2.1-1ubuntu4.1
 fakeroot debian/rules clean
debian/rules:7: /usr/share/quilt/quilt.make: No such file or directory
make: *** No rule to make target `/usr/share/quilt/quilt.make'.  Stop.
s

```Has anyone an idea what to do?

---

### Post by Ayuthia on 2008-04-23
> dpkg-checkbuilddeps: Unmet build dependencies: libltdl3-dev ofx (>= 1:0.8.0-8) guile-1.6-dev m4 zlib1g-dev libjpeg62-dev liborbit-dev libungif4-dev libglib2.0-dev (>= 2.4.7) libxml2-dev (>= 2.4.16) libbonobo2-dev (>= 2.0.0) libgnomevfs2-dev (>= 2.2.0) libgtk2.0-dev (>= 2.4.13) libglade2-dev (>= 2.3.6) libgnomeprint2.2-dev (>= 2.8.0) libart-2.0-dev (>= 2.3.11) libgconf2-dev libgnomeui-dev (>= 2.0.0) libgsf-gnome-1-dev (>= 1.12.2) libpango1.0-dev (>= 1.6.0) libgtkhtml3.8-dev libgoffice-0-dev imagemagick swig quilt
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
Are you sure that you downloaded all the prerequisites?  It looks like you might have missed this step:
```
# sudo apt-get build-dep gnucash libaqbanking
```

---

### Post by borobudur on 2008-04-25
I had to do this:

```
sudo apt-get update
sudo apt-get upgrade
```Thanks for your help!

---

