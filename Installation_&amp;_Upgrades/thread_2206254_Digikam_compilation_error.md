---
title: "Digikam compilation error"
date: 2014-02-18
forum: Installation &amp; Upgrades
---

### Post by michal-urban on 2014-02-18
Hi! Im trying to compile DigiKAM from GIT, following the digikam webpage guide:

```

git clone git://anongit.kde.org/digikam-software-compilation dk
cd dk 
./download-repos
./bootstrap.linux 
cd build 
make 

```

I managed to get all the dependencies (or at least it looked that way) - but when I run debootstrap.linux there is a strange (at least for myself) error which I dont really understand ... Im running Ubuntu 12.04.4 amd64 btw.


```

michal@mironet:~/Build/Dikikam/dk$ ./bootstrap.linux 
-- Found Qt-Version 4.8.1 (using /usr/bin/qmake)
-- Found X11: /usr/lib/x86_64-linux-gnu/libX11.so
-- Found KDE 4.8 include dir: /usr/include
-- Found KDE 4.8 library dir: /usr/lib
-- Found the KDE4 kconfig_compiler preprocessor: /usr/bin/kconfig_compiler
-- Found automoc4: /usr/bin/automoc4
-- /home/michal/Build/Dikikam/dk/po/ dir do not exists. Translations compilation disabled...
-- You can use DIGIKAMSC_CHECKOUT_PO option to extract po files from KDE repositories.
-- Local kdegraphics libraries will be compiled... YES
-- Handbooks will be compiled..................... YES
-- Extract translations files..................... NO
-- Translations will be compiled.................. NO
-- ----------------------------------------------------------------------------------
-- Starting CMake configuration for: libksane


-----------------------------------------------------------------------------
-- The following external packages were located on your system.
-- This installation will have the extra features provided by these packages.
-----------------------------------------------------------------------------
   * SANE development toolkit - Scanner Access Now Easy (SANE) development package


-----------------------------------------------------------------------------
-- Congratulations! All external packages have been found.
-----------------------------------------------------------------------------


-- ----------------------------------------------------------------------------------
-- Starting CMake configuration for: libkipi
-- ----------------------------------------------------------------------------------
-- Starting CMake configuration for: libkexiv2
CMake Error at extra/libkexiv2/CMakeLists.txt:111 (INCLUDE):
  include could not find load file:


    CMakePackageConfigHelpers




CMake Error at extra/libkexiv2/CMakeLists.txt:112 (CONFIGURE_PACKAGE_CONFIG_FILE):
  Unknown CMake command "CONFIGURE_PACKAGE_CONFIG_FILE".




-- Configuring incomplete, errors occurred!

```

Help, please!!! :)

---

### Post by mörgæs on 2014-02-19
Hi, welcome to the fora.

Why do you compile Digikam? You can just install from the repositories.

---

### Post by monkeybrain20122 on 2014-02-19
If you are configuring out of source (i.e in build) the command is 
```
cmake ..
```
Notice the two dots, which means one level up the directory tree.

---

### Post by monkeybrain20122 on 2014-02-19
Instead of compiling you can get more up to date versions from ppa,
Check 
[https://launchpad.net/ubuntu/+source/digikam](https://launchpad.net/ubuntu/+source/digikam)

> **mörgæs said:**
> Hi, welcome to the fora.

Why do you compile Digikam? You can just install from the repositories.

Because Precise's repo is very outdated?  :)

---

### Post by mörgæs on 2014-02-19
If that's the problem installing 13.10 is an easy solution.

---

### Post by monkeybrain20122 on 2014-02-19
> **mörgæs said:**
> If that's the problem installing 13.10 is an easy solution.

Well some people prefer LTS and I do think it is kind of silly to upgrade the whole OS because of one or a few programs. that's why ppas are useful. :)

---

