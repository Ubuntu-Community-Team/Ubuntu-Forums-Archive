---
title: "apt-get build-dep error"
date: 2010-12-29
forum: Installation &amp; Upgrades
---

### Post by bradhaack on 2010-12-29
Running this give me an error

desktop:sudo apt-get build-dep gnucash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have unmet dependencies:
  libglib2.0-dev: Depends: libglib2.0-0 (= 2.24.0-0ubuntu4) but 2.24.1-0ubuntu1 is to be installed
  libgnomeui-dev: Depends: libgnomecanvas2-dev (>= 2.6.0) but it is not going to be installed
                  Depends: libgnome-keyring-dev (>= 0.4) but it is not going to be installed
                  Depends: libbonoboui2-dev (>= 2.13.1) but it is not going to be installed
  libgtk2.0-dev: Depends: libgtk2.0-0 (= 2.20.0-0ubuntu4) but 2.20.1-0ubuntu2 is to be installed
                 Depends: libatk1.0-dev (>= 1.13.0) but it is not going to be installed
E: Build-dependencies for gnucash could not be satisfied.

Someone on the gnucash list suggested that I enable backports, so I did that & now I get:

desktop:sudo apt-get build-dep gnucash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_lucid-backports_main_source_Sources - open (2: No such file or directory)

How do I debug this?

---

### Post by sikander3786 on 2010-12-29
After you make any change to the repos/sources.list, you need to update your repos information which you didn't I guess. Try this and post the output in ```
 tags. Click the # icon in post menu and paste your text in between the generated code tags.

[code]sudo apt-get update && sudo apt-get install gnucash
```

---

### Post by bradhaack on 2010-12-29
Right after i posted I figured out that i needed to run apt-get update after changing the repositories.  Then I got the same error as before.  I'm trying to build the latest release of gnucash from source.  The one available thru install is not the latest.

Here's the output from
sudo apt-get update && sudo apt-get install gnucash

```
Hit http://us.archive.ubuntu.com lucid Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-backports Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-security Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release
Hit http://us.archive.ubuntu.com lucid-backports Release
Hit http://us.archive.ubuntu.com lucid-security Release
Hit http://us.archive.ubuntu.com lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-backports/main Packages
Hit http://us.archive.ubuntu.com lucid-backports/restricted Packages
Hit http://us.archive.ubuntu.com lucid-backports/universe Packages
Hit http://us.archive.ubuntu.com lucid-backports/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-backports/main Sources
Hit http://us.archive.ubuntu.com lucid-backports/restricted Sources
Hit http://us.archive.ubuntu.com lucid-backports/universe Sources
Hit http://us.archive.ubuntu.com lucid-backports/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-security/main Packages
Hit http://us.archive.ubuntu.com lucid-security/restricted Packages
Hit http://us.archive.ubuntu.com lucid-security/main Sources
Hit http://us.archive.ubuntu.com lucid-security/restricted Sources
Hit http://us.archive.ubuntu.com lucid-security/universe Packages
Hit http://us.archive.ubuntu.com lucid-security/universe Sources
Hit http://us.archive.ubuntu.com lucid-security/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-security/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnucash is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by sikander3786 on 2010-12-29
Try,

```
sudo aptitude build-dep gnucash
```

---

### Post by bradhaack on 2010-12-29
```
:sudo apt-get build-dep gnucash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have unmet dependencies:
  libglib2.0-dev: Depends: libglib2.0-0 (= 2.24.0-0ubuntu4) but 2.24.1-0ubuntu1 is to be installed
  libgnomeui-dev: Depends: libgnomecanvas2-dev (>= 2.6.0) but it is not going to be installed
                  Depends: libgnome-keyring-dev (>= 0.4) but it is not going to be installed
                  Depends: libbonoboui2-dev (>= 2.13.1) but it is not going to be installed
  libgtk2.0-dev: Depends: libgtk2.0-0 (= 2.20.0-0ubuntu4) but 2.20.1-0ubuntu2 is to be installed
                 Depends: libatk1.0-dev (>= 1.13.0) but it is not going to be installed
E: Build-dependencies for gnucash could not be satisfied.

```

---

### Post by bradhaack on 2010-12-29
oops, i see you had aptitude.

I get a msg that packages will be downgraded.  Is this safe?

```
:sudo aptitude build-dep gnucash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  libatk1.0-dev libgail-dev libglib2.0-dev libgnome-keyring-dev libgtk2.0-dev 
The following NEW packages will be installed:
  debhelper dpatch guile-1.6-dev gwenhywfar-tools{a} intltool-debian{a} libaqbanking29-dev 
  libart-2.0-dev{a} libaudiofile-dev{a} libavahi-client-dev{a} libavahi-common-dev{a} 
  libavahi-glib-dev{a} libbonobo2-dev{a} libbonoboui2-dev{a} libbz2-dev{a} libcairo2-dev{a} 
  libdbus-1-dev{a} libdirectfb-dev{a} libdirectfb-extra{a} libenchant-dev{a} libesd0-dev{a} 
  libexpat1-dev{a} libfontconfig1-dev{a} libfreetype6-dev{a} libgconf2-dev libgcrypt11-dev{a} 
  libglade2-dev libgnome2-dev{a} libgnomecanvas2-dev{a} libgnomeui-dev libgnomevfs2-dev{a} 
  libgnutls-dev{a} libgoffice-0.8-dev libgpg-error-dev{a} libgsf-1-dev{a} libgsf-gnome-1-114{a} 
  libgsf-gnome-1-dev libgtkhtml3.14-dev libgwenhywfar47-dev{a} libice-dev{a} libidl-dev{a} 
  libjpeg62-dev{a} libktoblzcheck1-dev{a} libmail-sendmail-perl{a} libofx-dev liborbit2-dev{a} 
  libosp-dev{a} libpango1.0-dev libpixman-1-dev{a} libpng12-dev{a} libpopt-dev{a} 
  libpthread-stubs0{a} libpthread-stubs0-dev{a} libselinux1-dev{a} libsepol1-dev{a} libsm-dev{a} 
  libsys-hostname-long-perl{a} libsysfs-dev{a} libtasn1-3-dev{a} libx11-dev{a} libxau-dev{a} 
  libxcb-render-util0-dev{a} libxcb-render0-dev{a} libxcb1-dev{a} libxcomposite-dev{a} 
  libxcursor-dev{a} libxdamage-dev{a} libxdmcp-dev{a} libxext-dev{a} libxfixes-dev{a} libxft-dev{a} 
  libxi-dev{a} libxinerama-dev{a} libxml++1.0c2a{a} libxml2-dev libxrandr-dev{a} libxrender-dev{a} 
  ofx opensp{a} orbit2{a} patchutils{a} po-debconf{a} swig x11proto-composite-dev{a} 
  x11proto-core-dev{a} x11proto-damage-dev{a} x11proto-fixes-dev{a} x11proto-input-dev{a} 
  x11proto-kb-dev{a} x11proto-randr-dev{a} x11proto-render-dev{a} x11proto-xext-dev{a} 
  x11proto-xinerama-dev{a} xtrans-dev{a} zlib1g-dev 
The following packages will be REMOVED:
  guile-1.8 guile-1.8-dev libgmp3-dev{u} libgmpxx4ldbl{u} libltdl-dev{u} libtool{u} 
0 packages upgraded, 99 newly installed, 6 to remove and 0 not upgraded.
Need to get 28.5MB of archives. After unpacking 104MB will be used.
The following packages have unmet dependencies:
  libatk1.0-dev: Depends: libatk1.0-0 (= 1.30.0-0ubuntu2) but 1.30.0-0ubuntu2.1 is installed.
  libglib2.0-dev: Depends: libglib2.0-0 (= 2.24.0-0ubuntu4) but 2.24.1-0ubuntu1 is installed.
  libgnome-keyring-dev: Depends: libgnome-keyring0 (= 2.30.0-0ubuntu4) but 2.30.1-0ubuntu1 is installed.
  libgail-dev: Depends: libgail18 (= 2.20.0-0ubuntu4) but 2.20.1-0ubuntu2 is installed.
               Depends: libgail-common (= 2.20.0-0ubuntu4) but 2.20.1-0ubuntu2 is installed.
  libgtk2.0-dev: Depends: libgtk2.0-0 (= 2.20.0-0ubuntu4) but 2.20.1-0ubuntu2 is installed.
The following actions will resolve these dependencies:

Downgrade the following packages:
gtk2-engines-pixbuf [2.20.1-0ubuntu2 (now) -> 2.20.0-0ubuntu4 (lucid)]
libatk1.0-0 [1.30.0-0ubuntu2.1 (now) -> 1.30.0-0ubuntu2 (lucid)]
libatk1.0-data [1.30.0-0ubuntu2.1 (now) -> 1.30.0-0ubuntu2 (lucid)]
libgail-common [2.20.1-0ubuntu2 (now) -> 2.20.0-0ubuntu4 (lucid)]
libgail18 [2.20.1-0ubuntu2 (now) -> 2.20.0-0ubuntu4 (lucid)]
libglib2.0-0 [2.24.1-0ubuntu1 (now) -> 2.24.0-0ubuntu4 (lucid)]
libglib2.0-data [2.24.1-0ubuntu1 (now) -> 2.24.0-0ubuntu4 (lucid)]
libgnome-keyring0 [2.30.1-0ubuntu1 (now) -> 2.30.0-0ubuntu4 (lucid)]
libgtk2.0-0 [2.20.1-0ubuntu2 (now) -> 2.20.0-0ubuntu4 (lucid)]
libgtk2.0-bin [2.20.1-0ubuntu2 (now) -> 2.20.0-0ubuntu4 (lucid)]

Score is 353

Accept this solution? [Y/n/q/?] 

```

---

### Post by sikander3786 on 2010-12-29
It _should_ be safe. The packages will be downgraded to the standard versions found in Lucid. I think you installed them from some daily build/development PPAs.

---

### Post by bradhaack on 2010-12-29
Thanks, that worked.  It's still building, but past that error anyway.  I'm not sure where the other packages came from.  I installed wine a few days ago (& uninstalled it), maybe that's where they came from.

At a glance apt-get and aptitude are supposed to do the same thing?  When should one use aptitude instead of apt-get?

---

