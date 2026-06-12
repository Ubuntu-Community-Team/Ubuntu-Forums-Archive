---
title: "Google Earth is not installed"
date: 2010-08-09
forum: Installation &amp; Upgrades
---

### Post by gpdas on 2010-08-09
I installed googleearth-package from synaptic package manager and version is 0.5.7 .
The googleearth icon is not coming in Applications--> Internet menu.

---

### Post by jocko on 2010-08-09
The package "googleearth-package" does not contain google earth itself, it just installs the necessary files and scripts to download the latest google earth and make a debian package from it.
To install googleearth once googleearth-package is installed, type these commands in a terminal (the first one will take some time):
```
make-googleearth-package --force
sudo dpkg -i googleearth*.deb
```

---

### Post by gpdas on 2010-08-09
[COLOR=Red]**I followed exactly the code given by you. But getting the errors like this. It have shown some sample lines. Finally it failed.**[/COLOR]

dpkg-shlibdeps: warning: Can't extract name and version from library name `libcomponentframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libmoduleframework.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libapiloader.so'
dpkg-shlibdeps: warning: Can't extract name and version from library name `libge_net.so'
Checking shlib deps: libGLU.so.1
Package: googleearth
Version: 5.2.1.1329+0.5.7-1
Section: non-free/science
Priority: optional
Maintainer:  <gpdas@gpdas-desktop>
Architecture: i386
Depends: ttf-dejavu | ttf-bitstream-vera | msttcorefonts, libc6 (>= 2.0), libc6 (>= 2.1.3), libc6 (>= 2.3), libc6 (>= 2.3.2), libc6 (>= 2.3.6-6~), libc6 (>= 2.4), libexpat1 (>= 1.95.8), libgcc1 (>= 1:4.1.1), libgl1-mesa-glx | libgl1, libstdc++6 (>= 4.1.1), libstdc++6 (>= 4.2.1), libx11-6, libx11-6 (>= 0), libxext6, libxext6 (>= 0), libxrender1, zlib1g (>= 1:1.1.4), zlib1g (>= 1:1.2.0) 
Description: Google Earth, a 3D map/planet viewer
 Package built with googleearth-package.
dpkg-deb: building package `googleearth' in `./googleearth_5.2.1.1329+0.5.7-1_i386.deb'.
Success!
You can now install the package with e.g. sudo dpkg -i <package>.deb
gpdas@gpdas-desktop:~$ sudo dpkg -i googleearth*.deb
Selecting previously deselected package googleearth.
(Reading database ... 124861 files and directories currently installed.)
Unpacking googleearth (from googleearth_5.2.1.1329+0.5.7-1_i386.deb) ...
dpkg: dependency problems prevent configuration of googleearth:
 googleearth depends on ttf-dejavu | ttf-bitstream-vera | msttcorefonts; however:
  Package ttf-dejavu is not installed.
  Package ttf-bitstream-vera is not installed.
  Package msttcorefonts is not installed.
dpkg: error processing googleearth (--install):
 dependency problems - leaving unconfigured
Processing triggers for shared-mime-info ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_IN.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 googleearth

---

### Post by jcolyn on 2010-08-09
You need to setup Medibuntu in the repositories and download their version after uninstalling the version you installed.

Go to the below link and scroll part way down to adding the repository and enter the code into your terminal. Then type sudo apt-get update then go to synaptics package manager and type googleearth in the search box. Select the medibuntu package.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by gpdas on 2010-08-09
Thank you Colyn. Now Google Earth is working fine. Thanks again.:D

---

### Post by jocko on 2010-08-10
You could just have installed the missing dependencies it was complaining about:
```
gpdas@gpdas-desktop:~$ sudo dpkg -i googleearth*.deb
Selecting previously deselected package googleearth.
(Reading database ... 124861 files and directories currently installed.)
Unpacking googleearth (from googleearth_5.2.1.1329+0.5.7-1_i386.deb) ...
[COLOR=Red]dpkg: dependency problems prevent configuration of googleearth:
 googleearth depends on ttf-dejavu | ttf-bitstream-vera | msttcorefonts; however:[/COLOR]
  [COLOR=Red]Package ttf-dejavu is not installed.
  Package ttf-bitstream-vera is not installed.
  Package msttcorefonts is not installed.[/COLOR]
dpkg: error processing googleearth (--install):
 dependency problems - leaving unconfigured
Processing triggers for shared-mime-info ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_IN.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 googleearth
```

---

