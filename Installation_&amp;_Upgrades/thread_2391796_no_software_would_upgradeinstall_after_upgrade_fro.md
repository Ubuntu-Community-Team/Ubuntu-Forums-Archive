---
title: "no software would upgrade/install after upgrade from 17.04"
date: 2018-05-13
forum: Installation &amp; Upgrades
---

### Post by Amgad elsaiegh on 2018-05-13
since the upgrade, the software center can't make any new installs or updates
even when i try this manually,tried to install akregator for example and here is the result:
```

sudo apt install akregator
Reading package lists... Done
Building dependency tree       
Reading state information... Done
akregator is already the newest version (4:17.04.3-0ubuntu1).
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
libvtk6.3 : Depends: gdal-abi-2-2-3 but it is not installable
           Depends: libgl2ps1.4 but it is not installable
           Depends: libnetcdf13 (>= 4.0.1) but it is not installable
libwxgtk3.0-0v5 : Depends: libwxbase3.0-0v5 (>= 3.0.4+dfsg) but 3.0.3.1+dfsg2-1 is to be installed
mplayer : Depends: libcdio-cdda2 (>= 10.2+0.94+2) but it is not installable
         Depends: libcdio-paranoia2 (>= 10.2+0.94+2) but it is not installable
openjdk-8-jre : Depends: openjdk-8-jre-headless (= 8u162-b12-1) but 8u162-b12-0ubuntu0.17.10.2 is to be installed
xorg : Depends: xserver-xorg (>= 1:7.7+19ubuntu7) but 1:7.7+19ubuntu3 is to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).


```

when i tried apt-fix-broken install,this was the result:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
apg bmon byobu ccze cmatrix fonts-roboto-hinted htop jp2a kodi-bin kodi-data kodi-visualization-spectrum libbonobo2-0
libbonobo2-common libbonoboui2-0 libbonoboui2-common libcdio15 libcec4 libcrossguid0 libdirectfb-1.7-7 libenca0
libfabric1 libgirara-gtk3-2 libgl2ps1 libgnome-2-0 libgnome-keyring-common libgnome-keyring0 libgnome2-common
libgnomecanvas2-0 libgnomecanvas2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-common
libhdf5-openmpi-100 libhwloc-plugins libhwloc5 libibverbs1 libjpeg-turbo-progs libjs-iscroll libjsoncpp1 liblept5
libmicrohttpd12 libnetcdf-c++4 libopencv-shape3.1 libopenmpi2 liborbit-2-0 libp8-platform2 libpcrecpp0v5
libprotobuf10 libpsm-infinipath1 librdmacm1 libsrtp0 libsynctex1 libtesseract-data libtesseract3 libtgvoip1.0
libtinyxml2.6.2v5 libva-wayland1 libvorbisidec1 libwxbase3.0-0v5 linux-headers-4.13.0-16
linux-headers-4.13.0-16-generic linux-headers-4.13.0-25 linux-headers-4.13.0-25-generic linux-headers-4.13.0-32
linux-headers-4.13.0-32-generic linux-headers-4.13.0-37 linux-headers-4.13.0-37-generic linux-image-4.13.0-16-generic
linux-image-4.13.0-25-generic linux-image-4.13.0-32-generic linux-image-4.13.0-37-generic
linux-image-extra-4.13.0-16-generic linux-image-extra-4.13.0-25-generic linux-image-extra-4.13.0-32-generic
linux-image-extra-4.13.0-37-generic moreutils net-tools ocl-icd-libopencl1 openmpi-bin openmpi-common pastebinit
python-imaging python-olefile python-pil python-urwid python-wxversion python3-newt run-one speedometer tmux tree
xscreensaver-data
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
default-jre displaycal hollywood libopencv-contrib3.1 libopencv-viz3.1 libvtk6.3 libwxgtk3.0-0v5 mplayer
openjdk-8-jre python-wxgtk3.0 xorg
0 upgraded, 0 newly installed, 11 to remove and 1 not upgraded.
6 not fully installed or removed.
After this operation, 232 MB disk space will be freed.
Do you want to continue? [Y/n] y
Setting up dash (0.5.8-2.10) ...
No diversion 'diversion of /bin/sh by dash', none removed.
This should never be reached
dpkg: error processing package dash (--configure):
installed dash package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
dash
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

when trying to do anything from muon package manager, the following error message appears:
> 
dash
installed dash package post-installation script subprocess returned error exit status 1

what do you suggest?

---

### Post by dino99 on 2018-05-13
i'm seeing conflicts: maybe you need to downgrade some ppa's packages ;)

---

### Post by Amgad elsaiegh on 2018-05-14
can you show me how to do it?

---

### Post by Amgad elsaiegh on 2018-05-18
problem solved by following these steps

-open muon package manager
-open software sources from settings menu
- press the reset button in the bottom left corner and let it proceed
-open the konsole & excute these commands
sudo apt clean
and
sudo apt -f install
sudo dpkg --configure -a

---

### Post by mörgæs on 2018-05-19
Thanks for posting the solution. Please mark the thread solved using Thread Tools.

---

