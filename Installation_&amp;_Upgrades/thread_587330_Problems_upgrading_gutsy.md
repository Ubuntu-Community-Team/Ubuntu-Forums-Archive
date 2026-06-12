---
title: "Problems upgrading gutsy"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by Cubedude04 on 2007-10-22
Popup 1:
Can't install 'ubuntu-desktop'

It was impossible to install a required package. Please report this as a bug. 


Popup 2:
Could not calculate the upgrade

A unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.

> Starting
Starting 2
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
Investigating python-gtk2
Package python-gtk2 has broken dep on python2.4-gtk2
  Considering python2.4-gtk2 6 as a solution to python-gtk2 58
  Added python2.4-gtk2 to the remove list
  Fixing python-gtk2 via remove of python2.4-gtk2
Investigating python-glade2
Package python-glade2 has broken dep on python2.4-glade2
  Considering python2.4-glade2 0 as a solution to python-glade2 30
  Added python2.4-glade2 to the remove list
  Fixing python-glade2 via remove of python2.4-glade2
Investigating upstart
Package upstart has broken dep on sysvinit
  Considering sysvinit 5100 as a solution to upstart 25
  Holding Back upstart rather than change sysvinit
Investigating python-numeric
Package python-numeric has broken dep on python2.4-numeric
  Considering python2.4-numeric 5 as a solution to python-numeric 23
  Added python2.4-numeric to the remove list
  Fixing python-numeric via remove of python2.4-numeric
Investigating python-cairo
Package python-cairo has broken dep on python2.4-cairo
  Considering python2.4-cairo 5 as a solution to python-cairo 21
  Added python2.4-cairo to the remove list
  Fixing python-cairo via remove of python2.4-cairo
Investigating python-gobject
Package python-gobject has broken dep on python2.4-gobject
  Considering python2.4-gobject 5 as a solution to python-gobject 21
  Added python2.4-gobject to the remove list
  Fixing python-gobject via remove of python2.4-gobject
Investigating libgl1-mesa-glx
Package libgl1-mesa-glx has broken dep on libgl1
  Considering libgl1-mesa 3 as a solution to libgl1-mesa-glx 19
  Added libgl1-mesa to the remove list
  Considering libgl1-mesa-swx11 0 as a solution to libgl1-mesa-glx 19
Package libgl1-mesa-glx has broken dep on libgl1-mesa
  Considering libgl1-mesa 3 as a solution to libgl1-mesa-glx 19
  Added libgl1-mesa to the remove list
  Fixing libgl1-mesa-glx via remove of libgl1-mesa
  Fixing libgl1-mesa-glx via remove of libgl1-mesa
Investigating python-pyorbit
Package python-pyorbit has broken dep on python2.4-pyorbit
  Considering python2.4-pyorbit 5 as a solution to python-pyorbit 18
  Added python2.4-pyorbit to the remove list
  Fixing python-pyorbit via remove of python2.4-pyorbit
Investigating python-apt
Package python-apt has broken dep on python2.4-apt
  Considering python2.4-apt 0 as a solution to python-apt 15
  Added python2.4-apt to the remove list
  Fixing python-apt via remove of python2.4-apt
Investigating libnewt0.52
Package libnewt0.52 has broken dep on libnewt0.51
  Considering libnewt0.51 3 as a solution to libnewt0.52 13
  Added libnewt0.51 to the remove list
  Fixing libnewt0.52 via remove of libnewt0.51
Investigating upstart-compat-sysv
Package upstart-compat-sysv has broken dep on upstart
  Considering upstart 25 as a solution to upstart-compat-sysv 12
  Holding Back upstart-compat-sysv rather than change upstart
Investigating python-gnome2
Package python-gnome2 has broken dep on python2.4-gnome2
  Considering python2.4-gnome2 3 as a solution to python-gnome2 11
  Added python2.4-gnome2 to the remove list
  Fixing python-gnome2 via remove of python2.4-gnome2
Investigating python-gnome2-desktop
Package python-gnome2-desktop has broken dep on python2.4-gnome2-desktop
  Considering python2.4-gnome2-desktop 0 as a solution to python-gnome2-desktop 10
  Added python2.4-gnome2-desktop to the remove list
  Fixing python-gnome2-desktop via remove of python2.4-gnome2-desktop
Investigating python-libxml2
Package python-libxml2 has broken dep on python2.4-libxml2
  Considering python2.4-libxml2 2 as a solution to python-libxml2 8
  Added python2.4-libxml2 to the remove list
  Fixing python-libxml2 via remove of python2.4-libxml2
Investigating startup-tasks
Package startup-tasks has broken dep on upstart
  Considering upstart 25 as a solution to startup-tasks 8
  Holding Back startup-tasks rather than change upstart
Investigating python-dbus
Package python-dbus has broken dep on python2.4-dbus
  Considering python2.4-dbus 0 as a solution to python-dbus 8
  Added python2.4-dbus to the remove list
  Fixing python-dbus via remove of python2.4-dbus
Investigating system-services
Package system-services has broken dep on upstart
  Considering upstart 25 as a solution to system-services 8
  Holding Back system-services rather than change upstart
Investigating upstart-logd
Package upstart-logd has broken dep on upstart
  Considering upstart 25 as a solution to upstart-logd 8
  Holding Back upstart-logd rather than change upstart
Investigating libxklavier11
Package libxklavier11 has broken dep on libxklavier10
  Considering libxklavier10 0 as a solution to libxklavier11 7
  Added libxklavier10 to the remove list
  Fixing libxklavier11 via remove of libxklavier10
Investigating python-gnome2-extras
Package python-gnome2-extras has broken dep on python2.4-gnome2-extras
  Considering python2.4-gnome2-extras 0 as a solution to python-gnome2-extras 6
  Added python2.4-gnome2-extras to the remove list
  Fixing python-gnome2-extras via remove of python2.4-gnome2-extras
Investigating xutils-dev
Package xutils-dev has broken dep on imake
  Considering imake 0 as a solution to xutils-dev 6
  Added imake to the remove list
Package xutils-dev has broken dep on makedepend
  Considering makedepend 1 as a solution to xutils-dev 6
  Added makedepend to the remove list
  Fixing xutils-dev via remove of imake
  Fixing xutils-dev via remove of makedepend
Investigating libgcj7-0
Package libgcj7-0 has broken dep on libgcj7
  Considering libgcj7 0 as a solution to libgcj7-0 5
  Added libgcj7 to the remove list
  Fixing libgcj7-0 via remove of libgcj7
Investigating ubuntu-minimal
Package ubuntu-minimal has broken dep on startup-tasks
  Considering startup-tasks 8 as a solution to ubuntu-minimal 5
  Holding Back ubuntu-minimal rather than change startup-tasks
Investigating python-xml
Package python-xml has broken dep on python2.4-xml
  Considering python2.4-xml 3 as a solution to python-xml 4
  Added python2.4-xml to the remove list
  Fixing python-xml via remove of python2.4-xml
Investigating python-egenix-mxtools
Package python-egenix-mxtools has broken dep on python2.4-egenix-mxtools
  Considering python2.4-egenix-mxtools 5 as a solution to python-egenix-mxtools 4
  Holding Back python-egenix-mxtools rather than change python2.4-egenix-mxtools
Investigating gtk2-engines
Package gtk2-engines has broken dep on gtk2-engines-clearlooks
  Considering gtk2-engines-clearlooks 0 as a solution to gtk2-engines 3
  Added gtk2-engines-clearlooks to the remove list
Package gtk2-engines has broken dep on gtk2-engines-crux
  Considering gtk2-engines-crux 0 as a solution to gtk2-engines 3
  Added gtk2-engines-crux to the remove list
Package gtk2-engines has broken dep on gtk2-engines-highcontrast
  Considering gtk2-engines-highcontrast 0 as a solution to gtk2-engines 3
  Added gtk2-engines-highcontrast to the remove list
Package gtk2-engines has broken dep on gtk2-engines-lighthouseblue
  Considering gtk2-engines-lighthouseblue 0 as a solution to gtk2-engines 3
  Added gtk2-engines-lighthouseblue to the remove list
Package gtk2-engines has broken dep on gtk2-engines-mist
  Considering gtk2-engines-mist 0 as a solution to gtk2-engines 3
  Added gtk2-engines-mist to the remove list
Package gtk2-engines has broken dep on gtk2-engines-redmond95
  Considering gtk2-engines-redmond95 0 as a solution to gtk2-engines 3
  Added gtk2-engines-redmond95 to the remove list
Package gtk2-engines has broken dep on gtk2-engines-smooth
  Considering gtk2-engines-smooth 0 as a solution to gtk2-engines 3
  Added gtk2-engines-smooth to the remove list
Package gtk2-engines has broken dep on gtk2-engines-thinice
  Considering gtk2-engines-thinice 0 as a solution to gtk2-engines 3
  Added gtk2-engines-thinice to the remove list
Package gtk2-engines has broken dep on gtk2-engines-industrial
  Considering gtk2-engines-industrial 0 as a solution to gtk2-engines 3
  Added gtk2-engines-industrial to the remove list
  Fixing gtk2-engines via remove of gtk2-engines-clearlooks
  Fixing gtk2-engines via remove of gtk2-engines-crux
  Fixing gtk2-engines via remove of gtk2-engines-highcontrast
  Fixing gtk2-engines via remove of gtk2-engines-lighthouseblue
  Fixing gtk2-engines via remove of gtk2-engines-mist
  Fixing gtk2-engines via remove of gtk2-engines-redmond95
  Fixing gtk2-engines via remove of gtk2-engines-smooth
  Fixing gtk2-engines via remove of gtk2-engines-thinice
  Fixing gtk2-engines via remove of gtk2-engines-industrial
Investigating xserver-xorg-video-rendition
Package xserver-xorg-video-rendition has broken dep on xserver-xorg-driver-rendition
  Considering xserver-xorg-driver-rendition 0 as a solution to xserver-xorg-video-rendition 2
  Added xserver-xorg-driver-rendition to the remove list
  Fixing xserver-xorg-video-rendition via remove of xserver-xorg-driver-rendition
Investigating xserver-xorg-video-newport
Package xserver-xorg-video-newport has broken dep on xserver-xorg-driver-newport
  Considering xserver-xorg-driver-newport 0 as a solution to xserver-xorg-video-newport 2
  Added xserver-xorg-driver-newport to the remove list
  Fixing xserver-xorg-video-newport via remove of xserver-xorg-driver-newport
Investigating xserver-xorg-video-s3virge
Package xserver-xorg-video-s3virge has broken dep on xserver-xorg-driver-s3virge
  Considering xserver-xorg-driver-s3virge 0 as a solution to xserver-xorg-video-s3virge 2
  Added xserver-xorg-driver-s3virge to the remove list
  Fixing xserver-xorg-video-s3virge via remove of xserver-xorg-driver-s3virge
Investigating xserver-xorg-video-apm
Package xserver-xorg-video-apm has broken dep on xserver-xorg-driver-apm
  Considering xserver-xorg-driver-apm 0 as a solution to xserver-xorg-video-apm 2
  Added xserver-xorg-driver-apm to the remove list
  Fixing xserver-xorg-video-apm via remove of xserver-xorg-driver-apm
Investigating xserver-xorg-video-ark
Package xserver-xorg-video-ark has broken dep on xserver-xorg-driver-ark
  Considering xserver-xorg-driver-ark 0 as a solution to xserver-xorg-video-ark 2
  Added xserver-xorg-driver-ark to the remove list
  Fixing xserver-xorg-video-ark via remove of xserver-xorg-driver-ark
Investigating xserver-xorg-video-ati
Package xserver-xorg-video-ati has broken dep on xserver-xorg-driver-r128
  Considering xserver-xorg-driver-ati 0 as a solution to xserver-xorg-video-ati 2
  Added xserver-xorg-driver-ati to the remove list
Package xserver-xorg-video-ati has broken dep on xserver-xorg-driver-radeon
  Considering xserver-xorg-driver-ati 0 as a solution to xserver-xorg-video-ati 2
  Added xserver-xorg-driver-ati to the remove list
Package xserver-xorg-video-ati has broken dep on xserver-xorg-driver-atimisc
  Considering xserver-xorg-driver-ati 0 as a solution to xserver-xorg-video-ati 2
  Added xserver-xorg-driver-ati to the remove list
Package xserver-xorg-video-ati has broken dep on xserver-xorg-driver-ati
  Considering xserver-xorg-driver-ati 0 as a solution to xserver-xorg-video-ati 2
  Added xserver-xorg-driver-ati to the remove list
  Fixing xserver-xorg-video-ati via remove of xserver-xorg-driver-ati
  Fixing xserver-xorg-video-ati via remove of xserver-xorg-driver-ati
  Fixing xserver-xorg-video-ati via remove of xserver-xorg-driver-ati
  Fixing xserver-xorg-video-ati via remove of xserver-xorg-driver-ati
Investigating xserver-xorg-video-tdfx
Package xserver-xorg-video-tdfx has broken dep on xserver-xorg-driver-tdfx
  Considering xserver-xorg-driver-tdfx 0 as a solution to xserver-xorg-video-tdfx 2
  Added xserver-xorg-driver-tdfx to the remove list
  Fixing xserver-xorg-video-tdfx via remove of xserver-xorg-driver-tdfx
Investigating xserver-xorg-video-trident
Package xserver-xorg-video-trident has broken dep on xserver-xorg-driver-trident
  Considering xserver-xorg-driver-trident 0 as a solution to xserver-xorg-video-trident 2
  Added xserver-xorg-driver-trident to the remove list
  Fixing xserver-xorg-video-trident via remove of xserver-xorg-driver-trident
Investigating xserver-xorg-video-glint
Package xserver-xorg-video-glint has broken dep on xserver-xorg-driver-glint
  Considering xserver-xorg-driver-glint 0 as a solution to xserver-xorg-video-glint 2
  Added xserver-xorg-driver-glint to the remove list
  Fixing xserver-xorg-video-glint via remove of xserver-xorg-driver-glint
Investigating xserver-xorg-video-fbdev
Package xserver-xorg-video-fbdev has broken dep on xserver-xorg-driver-fbdev
  Considering xserver-xorg-driver-fbdev 0 as a solution to xserver-xorg-video-fbdev 2
  Added xserver-xorg-driver-fbdev to the remove list
  Fixing xserver-xorg-video-fbdev via remove of xserver-xorg-driver-fbdev
Investigating python2.4-tk
Package python2.4-tk has broken dep on python2.4
  Considering python2.4 293 as a solution to python2.4-tk 2
  Removing python2.4-tk rather than change python2.4
Investigating xserver-xorg-video-v4l
Package xserver-xorg-video-v4l has broken dep on xserver-xorg-driver-v4l
  Considering xserver-xorg-driver-v4l 0 as a solution to xserver-xorg-video-v4l 2
  Added xserver-xorg-driver-v4l to the remove list
  Fixing xserver-xorg-video-v4l via remove of xserver-xorg-driver-v4l
Investigating xserver-xorg-video-mga
Package xserver-xorg-video-mga has broken dep on xserver-xorg-driver-mga
  Considering xserver-xorg-driver-mga 0 as a solution to xserver-xorg-video-mga 2
  Added xserver-xorg-driver-mga to the remove list
  Fixing xserver-xorg-video-mga via remove of xserver-xorg-driver-mga
Investigating hpijs
Package hpijs has broken dep on hplip-ppds
  Considering hplip-ppds 2 as a solution to hpijs 2
  Holding Back hpijs rather than change hplip-ppds
Investigating xserver-xorg-video-nsc
Package xserver-xorg-video-nsc has broken dep on xserver-xorg-driver-nsc
  Considering xserver-xorg-driver-nsc 0 as a solution to xserver-xorg-video-nsc 2
  Added xserver-xorg-driver-nsc to the remove list
  Fixing xserver-xorg-video-nsc via remove of xserver-xorg-driver-nsc
Investigating xserver-xorg-video-vesa
Package xserver-xorg-video-vesa has broken dep on xserver-xorg-driver-vesa
  Considering xserver-xorg-driver-vesa 0 as a solution to xserver-xorg-video-vesa 2
  Added xserver-xorg-driver-vesa to the remove list
  Fixing xserver-xorg-video-vesa via remove of xserver-xorg-driver-vesa
Investigating xserver-xorg-video-siliconmotion
Package xserver-xorg-video-siliconmotion has broken dep on xserver-xorg-driver-siliconmotion
  Considering xserver-xorg-driver-siliconmotion 0 as a solution to xserver-xorg-video-siliconmotion 2
  Added xserver-xorg-driver-siliconmotion to the remove list
  Fixing xserver-xorg-video-siliconmotion via remove of xserver-xorg-driver-siliconmotion
Investigating xserver-xorg-video-tga
Package xserver-xorg-video-tga has broken dep on xserver-xorg-driver-tga
  Considering xserver-xorg-driver-tga 0 as a solution to xserver-xorg-video-tga 2
  Added xserver-xorg-driver-tga to the remove list
  Fixing xserver-xorg-video-tga via remove of xserver-xorg-driver-tga
Investigating xserver-xorg-video-sis
Package xserver-xorg-video-sis has broken dep on xserver-xorg-driver-sis
  Considering xserver-xorg-driver-sis 0 as a solution to xserver-xorg-video-sis 2
  Added xserver-xorg-driver-sis to the remove list
  Fixing xserver-xorg-video-sis via remove of xserver-xorg-driver-sis
Investigating xserver-xorg-video-vga
Package xserver-xorg-video-vga has broken dep on xserver-xorg-driver-vga
  Considering xserver-xorg-driver-vga 0 as a solution to xserver-xorg-video-vga 2
  Added xserver-xorg-driver-vga to the remove list
  Fixing xserver-xorg-video-vga via remove of xserver-xorg-driver-vga
Investigating xserver-xorg-video-via
Package xserver-xorg-video-via has broken dep on xserver-xorg-driver-via
  Considering xserver-xorg-driver-via 0 as a solution to xserver-xorg-video-via 2
  Added xserver-xorg-driver-via to the remove list
  Fixing xserver-xorg-video-via via remove of xserver-xorg-driver-via
Investigating xserver-xorg-video-s3
Package xserver-xorg-video-s3 has broken dep on xserver-xorg-driver-s3
  Considering xserver-xorg-driver-s3 0 as a solution to xserver-xorg-video-s3 2
  Added xserver-xorg-driver-s3 to the remove list
  Fixing xserver-xorg-video-s3 via remove of xserver-xorg-driver-s3
Investigating xserver-xorg-video-nv
Package xserver-xorg-video-nv has broken dep on xserver-xorg-driver-riva128
  Considering xserver-xorg-driver-nv 0 as a solution to xserver-xorg-video-nv 2
  Added xserver-xorg-driver-nv to the remove list
Package xserver-xorg-video-nv has broken dep on xserver-xorg-driver-nv
  Considering xserver-xorg-driver-nv 0 as a solution to xserver-xorg-video-nv 2
  Added xserver-xorg-driver-nv to the remove list
  Fixing xserver-xorg-video-nv via remove of xserver-xorg-driver-nv
  Fixing xserver-xorg-video-nv via remove of xserver-xorg-driver-nv
Investigating xserver-xorg-video-tseng
Package xserver-xorg-video-tseng has broken dep on xserver-xorg-driver-tseng
  Considering xserver-xorg-driver-tseng 0 as a solution to xserver-xorg-video-tseng 2
  Added xserver-xorg-driver-tseng to the remove list
  Fixing xserver-xorg-video-tseng via remove of xserver-xorg-driver-tseng
Investigating xserver-xorg-video-savage
Package xserver-xorg-video-savage has broken dep on xserver-xorg-driver-savage
  Considering xserver-xorg-driver-savage 0 as a solution to xserver-xorg-video-savage 2
  Added xserver-xorg-driver-savage to the remove list
  Fixing xserver-xorg-video-savage via remove of xserver-xorg-driver-savage
Investigating xserver-xorg-video-vmware
Package xserver-xorg-video-vmware has broken dep on xserver-xorg-driver-vmware
  Considering xserver-xorg-driver-vmware 0 as a solution to xserver-xorg-video-vmware 2
  Added xserver-xorg-driver-vmware to the remove list
  Fixing xserver-xorg-video-vmware via remove of xserver-xorg-driver-vmware
Investigating xserver-xorg-video-i128
Package xserver-xorg-video-i128 has broken dep on xserver-xorg-driver-i128
  Considering xserver-xorg-driver-i128 0 as a solution to xserver-xorg-video-i128 2
  Added xserver-xorg-driver-i128 to the remove list
  Fixing xserver-xorg-video-i128 via remove of xserver-xorg-driver-i128
Investigating xserver-xorg-video-neomagic
Package xserver-xorg-video-neomagic has broken dep on xserver-xorg-driver-neomagic
  Considering xserver-xorg-driver-neomagic 0 as a solution to xserver-xorg-video-neomagic 2
  Added xserver-xorg-driver-neomagic to the remove list
  Fixing xserver-xorg-video-neomagic via remove of xserver-xorg-driver-neomagic
Investigating xserver-xorg-video-chips
Package xserver-xorg-video-chips has broken dep on xserver-xorg-driver-chips
  Considering xserver-xorg-driver-chips 0 as a solution to xserver-xorg-video-chips 2
  Added xserver-xorg-driver-chips to the remove list
  Fixing xserver-xorg-video-chips via remove of xserver-xorg-driver-chips
Investigating xserver-xorg-video-voodoo
Package xserver-xorg-video-voodoo has broken dep on xserver-xorg-driver-voodoo
  Considering xserver-xorg-driver-voodoo 0 as a solution to xserver-xorg-video-voodoo 2
  Added xserver-xorg-driver-voodoo to the remove list
  Fixing xserver-xorg-video-voodoo via remove of xserver-xorg-driver-voodoo
Investigating python-gdbm
Package python-gdbm has broken dep on python2.4-gdbm
  Considering python2.4-gdbm 0 as a solution to python-gdbm 2
  Added python2.4-gdbm to the remove list
  Fixing python-gdbm via remove of python2.4-gdbm
Investigating xserver-xorg-video-i740
Package xserver-xorg-video-i740 has broken dep on xserver-xorg-driver-i740
  Considering xserver-xorg-driver-i740 0 as a solution to xserver-xorg-video-i740 2
  Added xserver-xorg-driver-i740 to the remove list
  Fixing xserver-xorg-video-i740 via remove of xserver-xorg-driver-i740
Investigating xserver-xorg-video-i810
Package xserver-xorg-video-i810 has broken dep on xserver-xorg-driver-i810
  Considering xserver-xorg-driver-i810 0 as a solution to xserver-xorg-video-i810 2
  Added xserver-xorg-driver-i810 to the remove list
  Fixing xserver-xorg-video-i810 via remove of xserver-xorg-driver-i810
Investigating xserver-xorg-video-cyrix
Package xserver-xorg-video-cyrix has broken dep on xserver-xorg-driver-cyrix
  Considering xserver-xorg-driver-cyrix 0 as a solution to xserver-xorg-video-cyrix 2
  Added xserver-xorg-driver-cyrix to the remove list
  Fixing xserver-xorg-video-cyrix via remove of xserver-xorg-driver-cyrix
Investigating xserver-xorg-video-dummy
Package xserver-xorg-video-dummy has broken dep on xserver-xorg-driver-dummy
  Considering xserver-xorg-driver-dummy 0 as a solution to xserver-xorg-video-dummy 2
  Added xserver-xorg-driver-dummy to the remove list
  Fixing xserver-xorg-video-dummy via remove of xserver-xorg-driver-dummy
Investigating xserver-xorg-video-sisusb
Package xserver-xorg-video-sisusb has broken dep on xserver-xorg-driver-sisusb
  Considering xserver-xorg-driver-sisusb 0 as a solution to xserver-xorg-video-sisusb 2
  Added xserver-xorg-driver-sisusb to the remove list
  Fixing xserver-xorg-video-sisusb via remove of xserver-xorg-driver-sisusb
Investigating xserver-xorg-video-imstt
Package xserver-xorg-video-imstt has broken dep on xserver-xorg-driver-imstt
  Considering xserver-xorg-driver-imstt 0 as a solution to xserver-xorg-video-imstt 2
  Added xserver-xorg-driver-imstt to the remove list
  Fixing xserver-xorg-video-imstt via remove of xserver-xorg-driver-imstt
Investigating xserver-xorg-video-cirrus
Package xserver-xorg-video-cirrus has broken dep on xserver-xorg-driver-cirrus
  Considering xserver-xorg-driver-cirrus 0 as a solution to xserver-xorg-video-cirrus 2
  Added xserver-xorg-driver-cirrus to the remove list
  Fixing xserver-xorg-video-cirrus via remove of xserver-xorg-driver-cirrus
Investigating python-imaging
Package python-imaging has broken dep on python2.4-imaging
  Considering python2.4-imaging 1 as a solution to python-imaging 1
  Holding Back python-imaging rather than change python2.4-imaging
Investigating python-crypto
Package python-crypto has broken dep on python2.4-crypto
  Considering python2.4-crypto 0 as a solution to python-crypto 0
  Holding Back python-crypto rather than change python2.4-crypto
Investigating python-egenix-mxtexttools
Package python-egenix-mxtexttools has broken dep on python2.4-egenix-mxtexttools
  Considering python2.4-egenix-mxtexttools 0 as a solution to python-egenix-mxtexttools 0
  Holding Back python-egenix-mxtexttools rather than change python2.4-egenix-mxtexttools
Investigating python-ldap
Package python-ldap has broken dep on python2.4-ldap
  Considering python2.4-ldap 0 as a solution to python-ldap 0
  Holding Back python-ldap rather than change python2.4-ldap
Investigating python-pexpect
Package python-pexpect has broken dep on python2.4-pexpect
  Considering python2.4-pexpect 0 as a solution to python-pexpect 0
  Holding Back python-pexpect rather than change python2.4-pexpect
Investigating python-imaging-sane
Package python-imaging-sane has broken dep on python-imaging
  Considering python-imaging 1 as a solution to python-imaging-sane 0
  Holding Back python-imaging-sane rather than change python-imaging
Investigating python2.4-libxslt1
Package python2.4-libxslt1 has broken dep on python2.4-libxml2
  Considering python2.4-libxml2 2 as a solution to python2.4-libxslt1 0
  Removing python2.4-libxslt1 rather than change python2.4-libxml2
Investigating python-mysqldb
Package python-mysqldb has broken dep on mysql-server
  Considering mysql-server 0 as a solution to python-mysqldb 0
  Holding Back python-mysqldb rather than change mysql-server
Investigating python-pyxattr
Package python-pyxattr has broken dep on python2.4-pyxattr
  Considering python2.4-pyxattr 0 as a solution to python-pyxattr 0
  Holding Back python-pyxattr rather than change python2.4-pyxattr
Investigating python-htmlgen
Package python-htmlgen has broken dep on python2.4-htmlgen
  Considering python2.4-htmlgen 0 as a solution to python-htmlgen 0
  Holding Back python-htmlgen rather than change python2.4-htmlgen
Investigating python-clientcookie
Package python-clientcookie has broken dep on python2.4-clientcookie
  Considering python2.4-clientcookie 0 as a solution to python-clientcookie 0
  Holding Back python-clientcookie rather than change python2.4-clientcookie
Investigating python-adns
Package python-adns has broken dep on python2.4-adns
  Considering python2.4-adns 0 as a solution to python-adns 0
  Holding Back python-adns rather than change python2.4-adns
Investigating python-pam
Package python-pam has broken dep on python2.4-pam
  Considering python2.4-pam 0 as a solution to python-pam 0
  Holding Back python-pam rather than change python2.4-pam
Investigating libvte4
Package libvte4 has broken dep on libvte-common
  Considering libvte-common 4 as a solution to libvte4 0
  Removing libvte4 rather than change libvte-common
Investigating python-pyopenssl
Package python-pyopenssl has broken dep on python2.4-pyopenssl
  Considering python2.4-pyopenssl 0 as a solution to python-pyopenssl 0
  Holding Back python-pyopenssl rather than change python2.4-pyopenssl
Investigating python-egenix-mxstack
Package python-egenix-mxstack has broken dep on python2.4-egenix-mxstack
  Considering python2.4-egenix-mxstack 0 as a solution to python-egenix-mxstack 0
  Holding Back python-egenix-mxstack rather than change python2.4-egenix-mxstack
Investigating python-sqlite
Package python-sqlite has broken dep on python2.4-sqlite
  Considering python2.4-sqlite 0 as a solution to python-sqlite 0
  Holding Back python-sqlite rather than change python2.4-sqlite
Investigating python-pylibacl
Package python-pylibacl has broken dep on python2.4-pylibacl
  Considering python2.4-pylibacl 0 as a solution to python-pylibacl 0
  Holding Back python-pylibacl rather than change python2.4-pylibacl
Investigating python-jabber
Package python-jabber has broken dep on python2.4-jabber
  Considering python2.4-jabber 0 as a solution to python-jabber 0
  Holding Back python-jabber rather than change python2.4-jabber
Investigating python-egenix-mxproxy
Package python-egenix-mxproxy has broken dep on python2.4-egenix-mxproxy
  Considering python2.4-egenix-mxproxy 0 as a solution to python-egenix-mxproxy 0
  Holding Back python-egenix-mxproxy rather than change python2.4-egenix-mxproxy
Investigating python-xmpp
Package python-xmpp has broken dep on python2.4-xmpp
  Considering python2.4-xmpp 0 as a solution to python-xmpp 0
  Holding Back python-xmpp rather than change python2.4-xmpp
Investigating python-reportlab
Package python-reportlab has broken dep on python2.4-reportlab
  Considering python2.4-reportlab 0 as a solution to python-reportlab 0
  Holding Back python-reportlab rather than change python2.4-reportlab
Investigating python-simpletal
Package python-simpletal has broken dep on python2.4-simpletal
  Considering python2.4-simpletal 0 as a solution to python-simpletal 0
  Holding Back python-simpletal rather than change python2.4-simpletal
Investigating bluez-pcmcia-support
Package bluez-pcmcia-support has broken dep on bluez-utils
  Considering bluez-utils 2 as a solution to bluez-pcmcia-support -1
  Removing bluez-pcmcia-support rather than change bluez-utils
 Try to Re-Instate ubuntu-minimal
 Try to Re-Instate python-egenix-mxtools
 Try to Re-Instate hpijs
 Try to Re-Instate python-imaging
 Try to Re-Instate python-crypto
 Try to Re-Instate python-egenix-mxtexttools
 Try to Re-Instate python-ldap
 Try to Re-Instate python-pexpect
 Try to Re-Instate python-imaging-sane
 Try to Re-Instate python-mysqldb
 Try to Re-Instate python-pyxattr
 Try to Re-Instate python-htmlgen
 Try to Re-Instate python-clientcookie
 Try to Re-Instate python-adns
 Try to Re-Instate python-pam
 Try to Re-Instate python-pyopenssl
 Try to Re-Instate python-egenix-mxstack
 Try to Re-Instate python-sqlite
 Try to Re-Instate python-pylibacl
 Try to Re-Instate python-jabber
 Try to Re-Instate python-egenix-mxproxy
 Try to Re-Instate python-xmpp
 Try to Re-Instate python-reportlab
 Try to Re-Instate python-simpletal
Done
Starting
Starting 2
Investigating python-imaging-sane
Package python-imaging-sane has broken dep on python2.4-imaging-sane
  Considering python2.4-imaging-sane 0 as a solution to python-imaging-sane 0
  Re-Instated python-imaging-sane
Investigating python2.4-imaging-sane
Package python2.4-imaging-sane has broken dep on python2.4-imaging
  Considering python2.4-imaging 1 as a solution to python2.4-imaging-sane 0
  Removing python2.4-imaging-sane rather than change python2.4-imaging
Done
Starting
Starting 2
Investigating python2.4-pgsql
Package python2.4-pgsql has broken dep on python2.4-egenix-mxdatetime
  Considering python2.4-egenix-mxdatetime 1 as a solution to python2.4-pgsql 1
  Removing python2.4-pgsql rather than change python2.4-egenix-mxdatetime
Investigating python-pgsql
Package python-pgsql has broken dep on python2.4-pgsql
  Considering python2.4-pgsql 1 as a solution to python-pgsql 0
  Removing python-pgsql rather than change python2.4-pgsql
Done
Starting
Starting 2
Investigating foomatic-filters-ppds
Package foomatic-filters-ppds has broken dep on hplip-ppds
  Considering hplip-ppds 1 as a solution to foomatic-filters-ppds -1
    Reinst Failed because of hplip-ppds
  Removing foomatic-filters-ppds rather than change hplip-ppds
Done
Starting
Starting 2
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
Investigating python-gtk2
Package python-gtk2 has broken dep on python2.4-gtk2
  Considering python2.4-gtk2 6 as a solution to python-gtk2 58
  Added python2.4-gtk2 to the remove list
  Fixing python-gtk2 via remove of python2.4-gtk2
Investigating python-glade2
Package python-glade2 has broken dep on python2.4-glade2
  Considering python2.4-glade2 0 as a solution to python-glade2 30
  Added python2.4-glade2 to the remove list
  Fixing python-glade2 via remove of python2.4-glade2
Investigating upstart
Package upstart has broken dep on sysvinit
  Considering sysvinit 5100 as a solution to upstart 25
  Holding Back upstart rather than change sysvinit
Investigating python-numeric
Package python-numeric has broken dep on python2.4-numeric
  Considering python2.4-numeric 5 as a solution to python-numeric 23
  Added python2.4-numeric to the remove list
  Fixing python-numeric via remove of python2.4-numeric
Investigating python-cairo
Package python-cairo has broken dep on python2.4-cairo
  Considering python2.4-cairo 5 as a solution to python-cairo 21
  Added python2.4-cairo to the remove list
  Fixing python-cairo via remove of python2.4-cairo
Investigating python-gobject
Package python-gobject has broken dep on python2.4-gobject
  Considering python2.4-gobject 5 as a solution to python-gobject 21
  Added python2.4-gobject to the remove list
  Fixing python-gobject via remove of python2.4-gobject
Investigating libgl1-mesa-glx
Package libgl1-mesa-glx has broken dep on libgl1
  Considering libgl1-mesa 3 as a solution to libgl1-mesa-glx 19
  Added libgl1-mesa to the remove list
  Considering libgl1-mesa-swx11 0 as a solution to libgl1-mesa-glx 19
Package libgl1-mesa-glx has broken dep on libgl1-mesa
  Considering libgl1-mesa 3 as a solution to libgl1-mesa-glx 19
  Added libgl1-mesa to the remove list
  Fixing libgl1-mesa-glx via remove of libgl1-mesa
  Fixing libgl1-mesa-glx via remove of libgl1-mesa
Investigating python-pyorbit
Package python-pyorbit has broken dep on python2.4-pyorbit
  Considering python2.4-pyorbit 5 as a solution to python-pyorbit 18
  Added python2.4-pyorbit to the remove list
  Fixing python-pyorbit via remove of python2.4-pyorbit
Investigating python-apt
Package python-apt has broken dep on python2.4-apt
  Considering python2.4-apt 0 as a solution to python-apt 15
  Added python2.4-apt to the remove list
  Fixing python-apt via remove of python2.4-apt
Investigating libnewt0.52
Package libnewt0.52 has broken dep on libnewt0.51
  Considering libnewt0.51 3 as a solution to libnewt0.52 13
  Added libnewt0.51 to the remove list
  Fixing libnewt0.52 via remove of libnewt0.51
Investigating upstart-compat-sysv
Package upstart-compat-sysv has broken dep on upstart
  Considering upstart 25 as a solution to upstart-compat-sysv 12
  Holding Back upstart-compat-sysv rather than change upstart
Investigating python-gnome2
Package python-gnome2 has broken dep on python2.4-gnome2
  Considering python2.4-gnome2 3 as a solution to python-gnome2 11
  Added python2.4-gnome2 to the remove list
  Fixing python-gnome2 via remove of python2.4-gnome2
Investigating python-gnome2-desktop
Package python-gnome2-desktop has broken dep on python2.4-gnome2-desktop
  Considering python2.4-gnome2-desktop 0 as a solution to python-gnome2-desktop 10
  Added python2.4-gnome2-desktop to the remove list
  Fixing python-gnome2-desktop via remove of python2.4-gnome2-desktop
Investigating python-libxml2
Package python-libxml2 has broken dep on python2.4-libxml2
  Considering python2.4-libxml2 2 as a solution to python-libxml2 8
  Added python2.4-libxml2 to the remove list
  Fixing python-libxml2 via remove of python2.4-libxml2
Investigating startup-tasks
Package startup-tasks has broken dep on upstart
  Considering upstart 25 as a solution to startup-tasks 8
  Holding Back startup-tasks rather than change upstart
Investigating python-dbus
Package python-dbus has broken dep on python2.4-dbus
  Considering python2.4-dbus 0 as a solution to python-dbus 8
  Added python2.4-dbus to the remove list
  Fixing python-dbus via remove of python2.4-dbus
Investigating system-services
Package system-services has broken dep on upstart
  Considering upstart 25 as a solution to system-services 8
  Holding Back system-services rather than change upstart
Investigating upstart-logd
Package upstart-logd has broken dep on upstart
  Considering upstart 25 as a solution to upstart-logd 8
  Holding Back upstart-logd rather than change upstart
Investigating libxklavier11
Package libxklavier11 has broken dep on libxklavier10
  Considering libxklavier10 0 as a solution to libxklavier11 7
  Added libxklavier10 to the remove list
  Fixing libxklavier11 via remove of libxklavier10
Investigating python-gnome2-extras
Package python-gnome2-extras has broken dep on python2.4-gnome2-extras
  Considering python2.4-gnome2-extras 0 as a solution to python-gnome2-extras 6
  Added python2.4-gnome2-extras to the remove list
  Fixing python-gnome2-extras via remove of python2.4-gnome2-extras
Investigating xutils-dev
Package xutils-dev has broken dep on imake
  Considering imake 0 as a solution to xutils-dev 6
  Added imake to the remove list
Package xutils-dev has broken dep on makedepend
  Considering makedepend 1 as a solution to xutils-dev 6
  Added makedepend to the remove list
  Fixing xutils-dev via remove of imake
  Fixing xutils-dev via remove of makedepend
Investigating libgcj7-0
Package libgcj7-0 has broken dep on libgcj7
  Considering libgcj7 0 as a solution to libgcj7-0 5
  Added libgcj7 to the remove list
  Fixing libgcj7-0 via remove of libgcj7
Investigating ubuntu-minimal
Package ubuntu-minimal has broken dep on startup-tasks
  Considering startup-tasks 8 as a solution to ubuntu-minimal 5
  Holding Back ubuntu-minimal rather than change startup-tasks
Investigating python-xml
Package python-xml has broken dep on python2.4-xml
  Considering python2.4-xml 3 as a solution to python-xml 4
  Added python2.4-xml to the remove list
  Fixing python-xml via remove of python2.4-xml
Investigating python-egenix-mxtools
Package python-egenix-mxtools has broken dep on python2.4-egenix-mxtools
  Considering python2.4-egenix-mxtools 5 as a solution to python-egenix-mxtools 4
  Holding Back python-egenix-mxtools rather than change python2.4-egenix-mxtools
Investigating gtk2-engines
Package gtk2-engines has broken dep on gtk2-engines-clearlooks
  Considering gtk2-engines-clearlooks 0 as a solution to gtk2-engines 3
  Added gtk2-engines-clearlooks to the remove list
Package gtk2-engines has broken dep on gtk2-engines-crux
  Considering gtk2-engines-crux 0 as a solution to gtk2-engines 3
  Added gtk2-engines-crux to the remove list
Package gtk2-engines has broken dep on gtk2-engines-highcontrast
  Considering gtk2-engines-highcontrast 0 as a solution to gtk2-engines 3
  Added gtk2-engines-highcontrast to the remove list
Package gtk2-engines has broken dep on gtk2-engines-lighthouseblue
  Considering gtk2-engines-lighthouseblue 0 as a solution to gtk2-engines 3
  Added gtk2-engines-lighthouseblue to the remove list
Package gtk2-engines has broken dep on gtk2-engines-mist
  Considering gtk2-engines-mist 0 as a solution to gtk2-engines 3
  Added gtk2-engines-mist to the remove list
Package gtk2-engines has broken dep on gtk2-engines-redmond95
  Considering gtk2-engines-redmond95 0 as a solution to gtk2-engines 3
  Added gtk2-engines-redmond95 to the remove list
Package gtk2-engines has broken dep on gtk2-engines-smooth
  Considering gtk2-engines-smooth 0 as a solution to gtk2-engines 3
  Added gtk2-engines-smooth to the remove list
Package gtk2-engines has broken dep on gtk2-engines-thinice
  Considering gtk2-engines-thinice 0 as a solution to gtk2-engines 3
  Added gtk2-engines-thinice to the remove list
Package gtk2-engines has broken dep on gtk2-engines-industrial
  Considering gtk2-engines-industrial 0 as a solution to gtk2-engines 3
  Added gtk2-engines-industrial to the remove list
  Fixing gtk2-engines via remove of gtk2-engines-clearlooks
  Fixing gtk2-engines via remove of gtk2-engines-crux
  Fixing gtk2-engines via remove of gtk2-engines-highcontrast
  Fixing gtk2-engines via remove of gtk2-engines-lighthouseblue
  Fixing gtk2-engines via remove of gtk2-engines-mist
  Fixing gtk2-engines via remove of gtk2-engines-redmond95
  Fixing gtk2-engines via remove of gtk2-engines-smooth
  Fixing gtk2-engines via remove of gtk2-engines-thinice
  Fixing gtk2-engines via remove of gtk2-engines-industrial
Investigating xserver-xorg-video-rendition
Package xserver-xorg-video-rendition has broken dep on xserver-xorg-driver-rendition
  Considering xserver-xorg-driver-rendition 0 as a solution to xserver-xorg-video-rendition 2
  Added xserver-xorg-driver-rendition to the remove list
  Fixing xserver-xorg-video-rendition via remove of xserver-xorg-driver-rendition
Investigating xserver-xorg-video-newport
Package xserver-xorg-video-newport has broken dep on xserver-xorg-driver-newport
  Considering xserver-xorg-driver-newport 0 as a solution to xserver-xorg-video-newport 2
  Added xserver-xorg-driver-newport to the remove list
  Fixing xserver-xorg-video-newport via remove of xserver-xorg-driver-newport
Investigating xserver-xorg-video-s3virge
Package xserver-xorg-video-s3virge has broken dep on xserver-xorg-driver-s3virge
  Considering xserver-xorg-driver-s3virge 0 as a solution to xserver-xorg-video-s3virge 2
  Added xserver-xorg-driver-s3virge to the remove list
  Fixing xserver-xorg-video-s3virge via remove of xserver-xorg-driver-s3virge
Investigating xserver-xorg-video-apm
Package xserver-xorg-video-apm has broken dep on xserver-xorg-driver-apm
  Considering xserver-xorg-driver-apm 0 as a solution to xserver-xorg-video-apm 2
  Added xserver-xorg-driver-apm to the remove list
  Fixing xserver-xorg-video-apm via remove of xserver-xorg-driver-apm
Investigating xserver-xorg-video-ark
Package xserver-xorg-video-ark has broken dep on xserver-xorg-driver-ark
  Considering xserver-xorg-driver-ark 0 as a solution to xserver-xorg-video-ark 2
  Added xserver-xorg-driver-ark to the remove list
  Fixing xserver-xorg-video-ark via remove of xserver-xorg-driver-ark
Investigating xserver-xorg-video-ati
Package xserver-xorg-video-ati has broken dep on xserver-xorg-driver-r128
  Considering xserver-xorg-driver-ati 0 as a solution to xserver-xorg-video-ati 2
  Added xserver-xorg-driver-ati to the remove list
Package xserver-xorg-video-ati has broken dep on xserver-xorg-driver-radeon
  Considering xserver-xorg-driver-ati 0 as a solution to xserver-xorg-video-ati 2
  Added xserver-xorg-driver-ati to the remove list
Package xserver-xorg-video-ati has broken dep on xserver-xorg-driver-atimisc
  Considering xserver-xorg-driver-ati 0 as a solution to xserver-xorg-video-ati 2
  Added xserver-xorg-driver-ati to the remove list
Package xserver-xorg-video-ati has broken dep on xserver-xorg-driver-ati
  Considering xserver-xorg-driver-ati 0 as a solution to xserver-xorg-video-ati 2
  Added xserver-xorg-driver-ati to the remove list
  Fixing xserver-xorg-video-ati via remove of xserver-xorg-driver-ati
  Fixing xserver-xorg-video-ati via remove of xserver-xorg-driver-ati
  Fixing xserver-xorg-video-ati via remove of xserver-xorg-driver-ati
  Fixing xserver-xorg-video-ati via remove of xserver-xorg-driver-ati
Investigating xserver-xorg-video-tdfx
Package xserver-xorg-video-tdfx has broken dep on xserver-xorg-driver-tdfx
  Considering xserver-xorg-driver-tdfx 0 as a solution to xserver-xorg-video-tdfx 2
  Added xserver-xorg-driver-tdfx to the remove list
  Fixing xserver-xorg-video-tdfx via remove of xserver-xorg-driver-tdfx
Investigating xserver-xorg-video-trident
Package xserver-xorg-video-trident has broken dep on xserver-xorg-driver-trident
  Considering xserver-xorg-driver-trident 0 as a solution to xserver-xorg-video-trident 2
  Added xserver-xorg-driver-trident to the remove list
  Fixing xserver-xorg-video-trident via remove of xserver-xorg-driver-trident
Investigating xserver-xorg-video-glint
Package xserver-xorg-video-glint has broken dep on xserver-xorg-driver-glint
  Considering xserver-xorg-driver-glint 0 as a solution to xserver-xorg-video-glint 2
  Added xserver-xorg-driver-glint to the remove list
  Fixing xserver-xorg-video-glint via remove of xserver-xorg-driver-glint
Investigating xserver-xorg-video-fbdev
Package xserver-xorg-video-fbdev has broken dep on xserver-xorg-driver-fbdev
  Considering xserver-xorg-driver-fbdev 0 as a solution to xserver-xorg-video-fbdev 2
  Added xserver-xorg-driver-fbdev to the remove list
  Fixing xserver-xorg-video-fbdev via remove of xserver-xorg-driver-fbdev
Investigating python2.4-tk
Package python2.4-tk has broken dep on python2.4
  Considering python2.4 293 as a solution to python2.4-tk 2
  Removing python2.4-tk rather than change python2.4
Investigating xserver-xorg-video-v4l
Package xserver-xorg-video-v4l has broken dep on xserver-xorg-driver-v4l
  Considering xserver-xorg-driver-v4l 0 as a solution to xserver-xorg-video-v4l 2
  Added xserver-xorg-driver-v4l to the remove list
  Fixing xserver-xorg-video-v4l via remove of xserver-xorg-driver-v4l
Investigating xserver-xorg-video-mga
Package xserver-xorg-video-mga has broken dep on xserver-xorg-driver-mga
  Considering xserver-xorg-driver-mga 0 as a solution to xserver-xorg-video-mga 2
  Added xserver-xorg-driver-mga to the remove list
  Fixing xserver-xorg-video-mga via remove of xserver-xorg-driver-mga
Investigating hpijs
Package hpijs has broken dep on hplip-ppds
  Considering hplip-ppds 2 as a solution to hpijs 2
  Holding Back hpijs rather than change hplip-ppds
Investigating xserver-xorg-video-nsc
Package xserver-xorg-video-nsc has broken dep on xserver-xorg-driver-nsc
  Considering xserver-xorg-driver-nsc 0 as a solution to xserver-xorg-video-nsc 2
  Added xserver-xorg-driver-nsc to the remove list
  Fixing xserver-xorg-video-nsc via remove of xserver-xorg-driver-nsc
Investigating xserver-xorg-video-vesa
Package xserver-xorg-video-vesa has broken dep on xserver-xorg-driver-vesa
  Considering xserver-xorg-driver-vesa 0 as a solution to xserver-xorg-video-vesa 2
  Added xserver-xorg-driver-vesa to the remove list
  Fixing xserver-xorg-video-vesa via remove of xserver-xorg-driver-vesa
Investigating xserver-xorg-video-siliconmotion
Package xserver-xorg-video-siliconmotion has broken dep on xserver-xorg-driver-siliconmotion
  Considering xserver-xorg-driver-siliconmotion 0 as a solution to xserver-xorg-video-siliconmotion 2
  Added xserver-xorg-driver-siliconmotion to the remove list
  Fixing xserver-xorg-video-siliconmotion via remove of xserver-xorg-driver-siliconmotion
Investigating xserver-xorg-video-tga
Package xserver-xorg-video-tga has broken dep on xserver-xorg-driver-tga
  Considering xserver-xorg-driver-tga 0 as a solution to xserver-xorg-video-tga 2
  Added xserver-xorg-driver-tga to the remove list
  Fixing xserver-xorg-video-tga via remove of xserver-xorg-driver-tga
Investigating xserver-xorg-video-sis
Package xserver-xorg-video-sis has broken dep on xserver-xorg-driver-sis
  Considering xserver-xorg-driver-sis 0 as a solution to xserver-xorg-video-sis 2
  Added xserver-xorg-driver-sis to the remove list
  Fixing xserver-xorg-video-sis via remove of xserver-xorg-driver-sis
Investigating xserver-xorg-video-vga
Package xserver-xorg-video-vga has broken dep on xserver-xorg-driver-vga
  Considering xserver-xorg-driver-vga 0 as a solution to xserver-xorg-video-vga 2
  Added xserver-xorg-driver-vga to the remove list
  Fixing xserver-xorg-video-vga via remove of xserver-xorg-driver-vga
Investigating xserver-xorg-video-via
Package xserver-xorg-video-via has broken dep on xserver-xorg-driver-via
  Considering xserver-xorg-driver-via 0 as a solution to xserver-xorg-video-via 2
  Added xserver-xorg-driver-via to the remove list
  Fixing xserver-xorg-video-via via remove of xserver-xorg-driver-via
Investigating xserver-xorg-video-s3
Package xserver-xorg-video-s3 has broken dep on xserver-xorg-driver-s3
  Considering xserver-xorg-driver-s3 0 as a solution to xserver-xorg-video-s3 2
  Added xserver-xorg-driver-s3 to the remove list
  Fixing xserver-xorg-video-s3 via remove of xserver-xorg-driver-s3
Investigating xserver-xorg-video-nv
Package xserver-xorg-video-nv has broken dep on xserver-xorg-driver-riva128
  Considering xserver-xorg-driver-nv 0 as a solution to xserver-xorg-video-nv 2
  Added xserver-xorg-driver-nv to the remove list
Package xserver-xorg-video-nv has broken dep on xserver-xorg-driver-nv
  Considering xserver-xorg-driver-nv 0 as a solution to xserver-xorg-video-nv 2
  Added xserver-xorg-driver-nv to the remove list
  Fixing xserver-xorg-video-nv via remove of xserver-xorg-driver-nv
  Fixing xserver-xorg-video-nv via remove of xserver-xorg-driver-nv
Investigating xserver-xorg-video-tseng
Package xserver-xorg-video-tseng has broken dep on xserver-xorg-driver-tseng
  Considering xserver-xorg-driver-tseng 0 as a solution to xserver-xorg-video-tseng 2
  Added xserver-xorg-driver-tseng to the remove list
  Fixing xserver-xorg-video-tseng via remove of xserver-xorg-driver-tseng
Investigating xserver-xorg-video-savage
Package xserver-xorg-video-savage has broken dep on xserver-xorg-driver-savage
  Considering xserver-xorg-driver-savage 0 as a solution to xserver-xorg-video-savage 2
  Added xserver-xorg-driver-savage to the remove list
  Fixing xserver-xorg-video-savage via remove of xserver-xorg-driver-savage
Investigating xserver-xorg-video-vmware
Package xserver-xorg-video-vmware has broken dep on xserver-xorg-driver-vmware
  Considering xserver-xorg-driver-vmware 0 as a solution to xserver-xorg-video-vmware 2
  Added xserver-xorg-driver-vmware to the remove list
  Fixing xserver-xorg-video-vmware via remove of xserver-xorg-driver-vmware
Investigating xserver-xorg-video-i128
Package xserver-xorg-video-i128 has broken dep on xserver-xorg-driver-i128
  Considering xserver-xorg-driver-i128 0 as a solution to xserver-xorg-video-i128 2
  Added xserver-xorg-driver-i128 to the remove list
  Fixing xserver-xorg-video-i128 via remove of xserver-xorg-driver-i128
Investigating xserver-xorg-video-neomagic
Package xserver-xorg-video-neomagic has broken dep on xserver-xorg-driver-neomagic
  Considering xserver-xorg-driver-neomagic 0 as a solution to xserver-xorg-video-neomagic 2
  Added xserver-xorg-driver-neomagic to the remove list
  Fixing xserver-xorg-video-neomagic via remove of xserver-xorg-driver-neomagic
Investigating xserver-xorg-video-chips
Package xserver-xorg-video-chips has broken dep on xserver-xorg-driver-chips
  Considering xserver-xorg-driver-chips 0 as a solution to xserver-xorg-video-chips 2
  Added xserver-xorg-driver-chips to the remove list
  Fixing xserver-xorg-video-chips via remove of xserver-xorg-driver-chips
Investigating xserver-xorg-video-voodoo
Package xserver-xorg-video-voodoo has broken dep on xserver-xorg-driver-voodoo
  Considering xserver-xorg-driver-voodoo 0 as a solution to xserver-xorg-video-voodoo 2
  Added xserver-xorg-driver-voodoo to the remove list
  Fixing xserver-xorg-video-voodoo via remove of xserver-xorg-driver-voodoo
Investigating python-gdbm
Package python-gdbm has broken dep on python2.4-gdbm
  Considering python2.4-gdbm 0 as a solution to python-gdbm 2
  Added python2.4-gdbm to the remove list
  Fixing python-gdbm via remove of python2.4-gdbm
Investigating xserver-xorg-video-i740
Package xserver-xorg-video-i740 has broken dep on xserver-xorg-driver-i740
  Considering xserver-xorg-driver-i740 0 as a solution to xserver-xorg-video-i740 2
  Added xserver-xorg-driver-i740 to the remove list
  Fixing xserver-xorg-video-i740 via remove of xserver-xorg-driver-i740
Investigating xserver-xorg-video-i810
Package xserver-xorg-video-i810 has broken dep on xserver-xorg-driver-i810
  Considering xserver-xorg-driver-i810 0 as a solution to xserver-xorg-video-i810 2
  Added xserver-xorg-driver-i810 to the remove list
  Fixing xserver-xorg-video-i810 via remove of xserver-xorg-driver-i810
Investigating xserver-xorg-video-cyrix
Package xserver-xorg-video-cyrix has broken dep on xserver-xorg-driver-cyrix
  Considering xserver-xorg-driver-cyrix 0 as a solution to xserver-xorg-video-cyrix 2
  Added xserver-xorg-driver-cyrix to the remove list
  Fixing xserver-xorg-video-cyrix via remove of xserver-xorg-driver-cyrix
Investigating xserver-xorg-video-dummy
Package xserver-xorg-video-dummy has broken dep on xserver-xorg-driver-dummy
  Considering xserver-xorg-driver-dummy 0 as a solution to xserver-xorg-video-dummy 2
  Added xserver-xorg-driver-dummy to the remove list
  Fixing xserver-xorg-video-dummy via remove of xserver-xorg-driver-dummy
Investigating xserver-xorg-video-sisusb
Package xserver-xorg-video-sisusb has broken dep on xserver-xorg-driver-sisusb
  Considering xserver-xorg-driver-sisusb 0 as a solution to xserver-xorg-video-sisusb 2
  Added xserver-xorg-driver-sisusb to the remove list
  Fixing xserver-xorg-video-sisusb via remove of xserver-xorg-driver-sisusb
Investigating xserver-xorg-video-imstt
Package xserver-xorg-video-imstt has broken dep on xserver-xorg-driver-imstt
  Considering xserver-xorg-driver-imstt 0 as a solution to xserver-xorg-video-imstt 2
  Added xserver-xorg-driver-imstt to the remove list
  Fixing xserver-xorg-video-imstt via remove of xserver-xorg-driver-imstt
Investigating xserver-xorg-video-cirrus
Package xserver-xorg-video-cirrus has broken dep on xserver-xorg-driver-cirrus
  Considering xserver-xorg-driver-cirrus 0 as a solution to xserver-xorg-video-cirrus 2
  Added xserver-xorg-driver-cirrus to the remove list
  Fixing xserver-xorg-video-cirrus via remove of xserver-xorg-driver-cirrus
Investigating python-imaging
Package python-imaging has broken dep on python2.4-imaging
  Considering python2.4-imaging 1 as a solution to python-imaging 1
  Holding Back python-imaging rather than change python2.4-imaging
Investigating python-crypto
Package python-crypto has broken dep on python2.4-crypto
  Considering python2.4-crypto 0 as a solution to python-crypto 0
  Holding Back python-crypto rather than change python2.4-crypto
Investigating python-egenix-mxtexttools
Package python-egenix-mxtexttools has broken dep on python2.4-egenix-mxtexttools
  Considering python2.4-egenix-mxtexttools 0 as a solution to python-egenix-mxtexttools 0
  Holding Back python-egenix-mxtexttools rather than change python2.4-egenix-mxtexttools
Investigating python-ldap
Package python-ldap has broken dep on python2.4-ldap
  Considering python2.4-ldap 0 as a solution to python-ldap 0
  Holding Back python-ldap rather than change python2.4-ldap
Investigating python-pexpect
Package python-pexpect has broken dep on python2.4-pexpect
  Considering python2.4-pexpect 0 as a solution to python-pexpect 0
  Holding Back python-pexpect rather than change python2.4-pexpect
Investigating python-imaging-sane
Package python-imaging-sane has broken dep on python-imaging
  Considering python-imaging 1 as a solution to python-imaging-sane 0
  Holding Back python-imaging-sane rather than change python-imaging
Investigating python2.4-libxslt1
Package python2.4-libxslt1 has broken dep on python2.4-libxml2
  Considering python2.4-libxml2 2 as a solution to python2.4-libxslt1 0
  Removing python2.4-libxslt1 rather than change python2.4-libxml2
Investigating python-mysqldb
Package python-mysqldb has broken dep on mysql-server
  Considering mysql-server 0 as a solution to python-mysqldb 0
  Holding Back python-mysqldb rather than change mysql-server
Investigating python-pyxattr
Package python-pyxattr has broken dep on python2.4-pyxattr
  Considering python2.4-pyxattr 0 as a solution to python-pyxattr 0
  Holding Back python-pyxattr rather than change python2.4-pyxattr
Investigating python-htmlgen
Package python-htmlgen has broken dep on python2.4-htmlgen
  Considering python2.4-htmlgen 0 as a solution to python-htmlgen 0
  Holding Back python-htmlgen rather than change python2.4-htmlgen
Investigating python-clientcookie
Package python-clientcookie has broken dep on python2.4-clientcookie
  Considering python2.4-clientcookie 0 as a solution to python-clientcookie 0
  Holding Back python-clientcookie rather than change python2.4-clientcookie
Investigating python-adns
Package python-adns has broken dep on python2.4-adns
  Considering python2.4-adns 0 as a solution to python-adns 0
  Holding Back python-adns rather than change python2.4-adns
Investigating python-pam
Package python-pam has broken dep on python2.4-pam
  Considering python2.4-pam 0 as a solution to python-pam 0
  Holding Back python-pam rather than change python2.4-pam
Investigating libvte4
Package libvte4 has broken dep on libvte-common
  Considering libvte-common 4 as a solution to libvte4 0
  Removing libvte4 rather than change libvte-common
Investigating python-pyopenssl
Package python-pyopenssl has broken dep on python2.4-pyopenssl
  Considering python2.4-pyopenssl 0 as a solution to python-pyopenssl 0
  Holding Back python-pyopenssl rather than change python2.4-pyopenssl
Investigating python-egenix-mxstack
Package python-egenix-mxstack has broken dep on python2.4-egenix-mxstack
  Considering python2.4-egenix-mxstack 0 as a solution to python-egenix-mxstack 0
  Holding Back python-egenix-mxstack rather than change python2.4-egenix-mxstack
Investigating python-sqlite
Package python-sqlite has broken dep on python2.4-sqlite
  Considering python2.4-sqlite 0 as a solution to python-sqlite 0
  Holding Back python-sqlite rather than change python2.4-sqlite
Investigating python-pylibacl
Package python-pylibacl has broken dep on python2.4-pylibacl
  Considering python2.4-pylibacl 0 as a solution to python-pylibacl 0
  Holding Back python-pylibacl rather than change python2.4-pylibacl
Investigating python-jabber
Package python-jabber has broken dep on python2.4-jabber
  Considering python2.4-jabber 0 as a solution to python-jabber 0
  Holding Back python-jabber rather than change python2.4-jabber
Investigating python-egenix-mxproxy
Package python-egenix-mxproxy has broken dep on python2.4-egenix-mxproxy
  Considering python2.4-egenix-mxproxy 0 as a solution to python-egenix-mxproxy 0
  Holding Back python-egenix-mxproxy rather than change python2.4-egenix-mxproxy
Investigating python-xmpp
Package python-xmpp has broken dep on python2.4-xmpp
  Considering python2.4-xmpp 0 as a solution to python-xmpp 0
  Holding Back python-xmpp rather than change python2.4-xmpp
Investigating python-reportlab
Package python-reportlab has broken dep on python2.4-reportlab
  Considering python2.4-reportlab 0 as a solution to python-reportlab 0
  Holding Back python-reportlab rather than change python2.4-reportlab
Investigating python-simpletal
Package python-simpletal has broken dep on python2.4-simpletal
  Considering python2.4-simpletal 0 as a solution to python-simpletal 0
  Holding Back python-simpletal rather than change python2.4-simpletal
Investigating bluez-pcmcia-support
Package bluez-pcmcia-support has broken dep on bluez-utils
  Considering bluez-utils 2 as a solution to bluez-pcmcia-support -1
  Removing bluez-pcmcia-support rather than change bluez-utils
 Try to Re-Instate ubuntu-minimal
 Try to Re-Instate python-egenix-mxtools
 Try to Re-Instate hpijs
 Try to Re-Instate python-imaging
 Try to Re-Instate python-crypto
 Try to Re-Instate python-egenix-mxtexttools
 Try to Re-Instate python-ldap
 Try to Re-Instate python-pexpect
 Try to Re-Instate python-imaging-sane
 Try to Re-Instate python-mysqldb
 Try to Re-Instate python-pyxattr
 Try to Re-Instate python-htmlgen
 Try to Re-Instate python-clientcookie
 Try to Re-Instate python-adns
 Try to Re-Instate python-pam
 Try to Re-Instate python-pyopenssl
 Try to Re-Instate python-egenix-mxstack
 Try to Re-Instate python-sqlite
 Try to Re-Instate python-pylibacl
 Try to Re-Instate python-jabber
 Try to Re-Instate python-egenix-mxproxy
 Try to Re-Instate python-xmpp
 Try to Re-Instate python-reportlab
 Try to Re-Instate python-simpletal
Done
Starting
Starting 2
Investigating python-imaging-sane
Package python-imaging-sane has broken dep on python2.4-imaging-sane
  Considering python2.4-imaging-sane 0 as a solution to python-imaging-sane 0
  Re-Instated python-imaging-sane
Investigating python2.4-imaging-sane
Package python2.4-imaging-sane has broken dep on python2.4-imaging
  Considering python2.4-imaging 1 as a solution to python2.4-imaging-sane 0
  Removing python2.4-imaging-sane rather than change python2.4-imaging
Done
Starting
Starting 2
Investigating python2.4-pgsql
Package python2.4-pgsql has broken dep on python2.4-egenix-mxdatetime
  Considering python2.4-egenix-mxdatetime 1 as a solution to python2.4-pgsql 1
  Removing python2.4-pgsql rather than change python2.4-egenix-mxdatetime
Investigating python-pgsql
Package python-pgsql has broken dep on python2.4-pgsql
  Considering python2.4-pgsql 1 as a solution to python-pgsql 0
  Removing python-pgsql rather than change python2.4-pgsql
Done
Starting
Starting 2
Investigating foomatic-filters-ppds
Package foomatic-filters-ppds has broken dep on hplip-ppds
  Considering hplip-ppds 1 as a solution to foomatic-filters-ppds -1
    Reinst Failed because of hplip-ppds
  Removing foomatic-filters-ppds rather than change hplip-ppds
Done
Starting
Starting 2
Investigating libbtctl2
Package libbtctl2 has broken dep on libbluetooth1
  Considering libbluetooth1 10001 as a solution to libbtctl2 0
  Removing libbtctl2 rather than change libbluetooth1
Done
Starting
Starting 2
Investigating python-kjbuckets
Package python-kjbuckets has broken dep on python2.4-kjbuckets
  Considering python2.4-kjbuckets 10001 as a solution to python-kjbuckets 0
  Removing python-kjbuckets rather than change python2.4-kjbuckets
Done
Starting
Starting 2
Investigating libnautilus-burn3
Package libnautilus-burn3 has broken dep on libdbus-1-2
  Considering libdbus-1-2 10001 as a solution to libnautilus-burn3 0
  Removing libnautilus-burn3 rather than change libdbus-1-2
Done
Starting
Starting 2
Investigating linux-restricted-modules-2.6.15-26-386
Package linux-restricted-modules-2.6.15-26-386 has broken dep on linux-image-2.6.15-26-386
  Considering linux-image-2.6.15-26-386 10001 as a solution to linux-restricted-modules-2.6.15-26-386 0
  Removing linux-restricted-modules-2.6.15-26-386 rather than change linux-image-2.6.15-26-386
Done
Starting
Starting 2
Investigating python-htmltmpl
Package python-htmltmpl has broken dep on python2.4-htmltmpl
  Considering python2.4-htmltmpl 10001 as a solution to python-htmltmpl 0
  Removing python-htmltmpl rather than change python2.4-htmltmpl
Done
Starting
Starting 2
Investigating linux-restricted-modules-2.6.15-28-386
Package linux-restricted-modules-2.6.15-28-386 has broken dep on linux-image-2.6.15-28-386
  Considering linux-image-2.6.15-28-386 10001 as a solution to linux-restricted-modules-2.6.15-28-386 0
  Removing linux-restricted-modules-2.6.15-28-386 rather than change linux-image-2.6.15-28-386
Done
Starting
Starting 2
Investigating python-htmltmpl
Package python-htmltmpl has broken dep on python2.4-htmltmpl
  Considering python2.4-htmltmpl 10001 as a solution to python-htmltmpl 0
  Removing python-htmltmpl rather than change python2.4-htmltmpl
Done
Starting
Starting 2
Investigating libexchange-storage1.2-1
Package libexchange-storage1.2-1 has broken dep on libgnutls12
  Considering libgnutls12 10002 as a solution to libexchange-storage1.2-1 0
  Removing libexchange-storage1.2-1 rather than change libgnutls12
Investigating libegroupwise1.2-9
Package libegroupwise1.2-9 has broken dep on libgnutls12
  Considering libgnutls12 10002 as a solution to libegroupwise1.2-9 0
  Removing libegroupwise1.2-9 rather than change libgnutls12
Done
Starting
Starting 2
Investigating python-soappy
Package python-soappy has broken dep on python2.4-soappy
  Considering python2.4-soappy 10001 as a solution to python-soappy 0
  Removing python-soappy rather than change python2.4-soappy
Done
Starting
Starting 2
Investigating python-htmltmpl
Package python-htmltmpl has broken dep on python2.4-htmltmpl
  Considering python2.4-htmltmpl 10001 as a solution to python-htmltmpl 0
  Removing python-htmltmpl rather than change python2.4-htmltmpl
Done
Starting
Starting 2
Investigating python-soappy
Package python-soappy has broken dep on python2.4-soappy
  Considering python2.4-soappy 10001 as a solution to python-soappy 0
  Removing python-soappy rather than change python2.4-soappy
Done
Starting
Starting 2
Investigating libedataserverui1.2-6
Package libedataserverui1.2-6 has broken dep on libebook1.2-5
  Considering libebook1.2-5 10001 as a solution to libedataserverui1.2-6 0
  Removing libedataserverui1.2-6 rather than change libebook1.2-5
Done
Starting
Starting 2
Investigating libedata-cal1.2-1
Package libedata-cal1.2-1 has broken dep on libecal1.2-3
  Considering libecal1.2-3 10001 as a solution to libedata-cal1.2-1 0
  Removing libedata-cal1.2-1 rather than change libecal1.2-3
Done
Starting
Starting 2
Investigating python-gadfly
Package python-gadfly has broken dep on python2.4-gadfly
  Considering python2.4-gadfly 10001 as a solution to python-gadfly 0
  Removing python-gadfly rather than change python2.4-gadfly
Done
Starting
Starting 2
Investigating python-htmltmpl
Package python-htmltmpl has broken dep on python2.4-htmltmpl
  Considering python2.4-htmltmpl 10001 as a solution to python-htmltmpl 0
  Removing python-htmltmpl rather than change python2.4-htmltmpl
Done
Starting
Starting 2
Investigating python-soappy
Package python-soappy has broken dep on python2.4-soappy
  Considering python2.4-soappy 10001 as a solution to python-soappy 0
  Removing python-soappy rather than change python2.4-soappy
Done
Starting
Starting 2
Investigating libedataserverui1.2-6
Package libedataserverui1.2-6 has broken dep on libebook1.2-5
  Considering libebook1.2-5 10001 as a solution to libedataserverui1.2-6 0
  Removing libedataserverui1.2-6 rather than change libebook1.2-5
Done
Starting
Starting 2
Investigating python-netcdf
Package python-netcdf has broken dep on libnetcdf3
  Considering libnetcdf3 10001 as a solution to python-netcdf 0
  Removing python-netcdf rather than change libnetcdf3
Done
Installing python-central as dep of python-crypto
Installing libc6 as dep of mcpp
Installing libatk1.0-0 as dep of gnome-keyring
Installing libglib2.0-0 as dep of libatk1.0-0
Installing libcairo2 as dep of gnome-keyring
Installing libfontconfig1 as dep of libcairo2
Installing fontconfig-config as dep of libfontconfig1
Installing libpng12-0 as dep of libcairo2
Installing libdbus-1-3 as dep of gnome-keyring
Installing libpango1.0-0 as dep of gnome-keyring
Installing libpango1.0-common as dep of libpango1.0-0
Installing libdatrie0 as dep of libpango1.0-0
Installing libthai0 as dep of libpango1.0-0
Installing libthai-data as dep of libthai0
Installing libxrandr2 as dep of gnome-keyring
Installing libgnome-keyring0 as dep of f-spot
Installing libgnomeui-0 as dep of f-spot
Installing libgnomevfs2-0 as dep of libgnomeui-0
Installing libdbus-glib-1-2 as dep of libgnomevfs2-0
Installing libselinux1 as dep of libgnomevfs2-0
Installing libsepol1 as dep of libselinux1
Installing libxml2 as dep of libgnomevfs2-0
Installing libgnomevfs2-common as dep of libgnomevfs2-0
Installing libgnomeui-common as dep of libgnomeui-0
Installing libmono0 as dep of f-spot
Installing libgphoto2-2 as dep of f-spot
Installing libgphoto2-port0 as dep of libgphoto2-2
Installing libmono-corlib2.0-cil as dep of f-spot
Installing mono-jit as dep of libmono-corlib2.0-cil
Installing mono-common as dep of mono-jit
Installing libmono-sharpzip2.84-cil as dep of f-spot
Installing libmono-system2.0-cil as dep of libmono-sharpzip2.84-cil
Installing libmono-security2.0-cil as dep of libmono-system2.0-cil
Installing libmono-sqlite2.0-cil as dep of f-spot
Installing libmono-system-data2.0-cil as dep of libmono-sqlite2.0-cil
Installing libmono-data-tds2.0-cil as dep of libmono-system-data2.0-cil
Installing libsqlite3-0 as dep of libmono-sqlite2.0-cil
Installing libmono-system-web2.0-cil as dep of f-spot
Installing libmono2.0-cil as dep of f-spot
Installing libndesk-dbus-glib1.0-cil as dep of f-spot
Installing libndesk-dbus1.0-cil as dep of libndesk-dbus-glib1.0-cil
Installing libcupsys2 as dep of libgnomecupsui1.0-1c2a
Installing libgcc1 as dep of libgnomecupsui1.0-1c2a
Installing gcc-4.1-base as dep of libgcc1
Installing libstdc++6 as dep of libgnomecupsui1.0-1c2a
Installing volumeid as dep of udev
Installing libvolume-id0 as dep of volumeid
Installing libasound2 as dep of gstreamer0.10-alsa
Installing libgstreamer0.10-0 as dep of gstreamer0.10-alsa
Installing libnautilus-extension1 as dep of totem-gstreamer
Installing libtotem-plparser1 as dep of totem-gstreamer
Installing gstreamer0.10-plugins-base as dep of totem-gstreamer
Installing linux-image-386 as dep of linux-386
Installing linux-image-2.6.20-16-386 as dep of linux-image-386
Installing linux-restricted-modules-386 as dep of linux-386
Installing linux-restricted-modules-2.6.20-16-386 as dep of linux-restricted-modules-386
Installing linux-restricted-modules-common as dep of linux-restricted-modules-2.6.20-16-386
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing libdirectfb-0.9-25 as dep of libsdl1.2debian-alsa
Installing gcj-4.1-base as dep of libgcj7-jar
Installing libgcj7-0 as dep of libgcj7-jar
Installing libgcj-common as dep of libgcj7-0
Installing xserver-xorg-core as dep of xserver-xorg-video-rendition
Installing libdrm2 as dep of xserver-xorg-core
Installing libxslt1.1 as dep of libxmlsec1
Installing libgpg-error0 as dep of libxslt1.1
Installing gcc-3.3-base as dep of libstdc++5
Installing libpanel-applet2-0 as dep of tomboy
Installing libgnomeprint2.2-0 as dep of tomboy
Installing libgnomeprint2.2-data as dep of libgnomeprint2.2-0
Installing libgnomeprintui2.2-0 as dep of tomboy
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Installing perl as dep of libglib-perl
Installing perl-base as dep of perl
Installing perl-modules as dep of perl
Installing libbz2-1.0 as dep of bzip2
Installing libecal1.2-7 as dep of evolution-webcal
Installing libedataserver1.2-9 as dep of libecal1.2-7
Installing libsoup2.2-8 as dep of evolution-webcal
Installing libebook1.2-9 as dep of ekiga
Installing libcamel1.2-10 as dep of libebook1.2-9
Installing libopal-2.2.0 as dep of ekiga
Installing libpt-1.10.0 as dep of libopal-2.2.0
Installing libsasl2-2 as dep of libpt-1.10.0
Installing libdb4.2 as dep of libsasl2-2
Installing libsasl2-modules as dep of libsasl2-2
Installing libssl0.9.8 as dep of libsasl2-modules
Installing python as dep of python-examples
Installing python2.5 as dep of python
Installing python2.5-minimal as dep of python2.5
Installing libreadline5 as dep of python2.5
Installing python-minimal as dep of python
Installing python2.5-examples as dep of python-examples
Installing openoffice.org-core as dep of openoffice.org-gnome
Installing openoffice.org-common as dep of openoffice.org-core
Installing openoffice.org-style-human as dep of openoffice.org-common
Installing openoffice.org-hyphenation as dep of openoffice.org-core
Installing libcurl3 as dep of openoffice.org-core
Installing libhunspell-1.1-0 as dep of openoffice.org-core
Installing libicu36 as dep of openoffice.org-core
Installing libstlport5.1 as dep of openoffice.org-core
Installing libgutenprint2 as dep of gimp-print
Installing libgutenprintui2-1 as dep of gimp-print
Installing update-manager-core as dep of update-manager
Installing libwps-0.1-1 as dep of openoffice.org-writer
Installing python-uno as dep of openoffice.org-writer
Installing libgs-esp8 as dep of gs-esp
Installing libcupsimage2 as dep of libgs-esp8
Installing libgail-common as dep of gnome-media
Installing gnome-media-common as dep of gnome-media
Installing openoffice.org-style-andromeda as dep of openoffice.org-style-default
Installing metacity-common as dep of metacity
Installing libbeagle0 as dep of nautilus
Installing libeel2-2 as dep of nautilus
Installing libeel2-data as dep of libeel2-2
Installing nautilus-data as dep of nautilus
Installing python2.4 as dep of python2.4-examples
Installing python2.4-minimal as dep of python2.4
Installing libgnome2-common as dep of libgnome2-0
Installing libdns22 as dep of bind9-host
Installing libatspi1.0-0 as dep of libgail-gnome-module
Installing openoffice.org-draw as dep of openoffice.org-impress
Installing language-pack-en as dep of language-pack-en-base
Installing libgamin0 as dep of gamin
Installing python-imaging as dep of python-imaging-sane
Installing python-numarray as dep of python-imaging-sane
Installing lapack3 as dep of python-numarray
Installing refblas3 as dep of lapack3
Installing libg2c0 as dep of lapack3
Installing gcc-3.4-base as dep of libg2c0
Installing gnome-user-guide as dep of ubuntu-docs
Installing dhcp3-common as dep of dhcp3-client
Installing libpq5 as dep of librdf0
Installing libraptor1 as dep of librdf0
Installing librasqal0 as dep of librdf0
Installing samba-common as dep of smbclient
Installing libslang2 as dep of whiptail
new important dependency: command-not-found
Installing command-not-found as dep of ubuntu-standard
Installing command-not-found-data as dep of command-not-found
Installing libgucharmap6 as dep of gucharmap
Installing brltty as dep of brltty-x11
Installing libbluetooth2 as dep of libbtctl4
Installing libopenobex1 as dep of libbtctl4
Installing libavahi-core5 as dep of avahi-daemon
Installing gnome-games-data as dep of gnome-games
Installing gnome-cards-data as dep of gnome-games-data
Installing python-gnome2-desktop as dep of gnome-games
Installing wodim as dep of cdrecord
Installing hwdb-client-common as dep of hwdb-client-gnome
Installing gdebi-core as dep of gdebi
Installing python-apt as dep of gdebi-core
Installing apt as dep of python-apt
Installing gksu as dep of gdebi
Installing evolution as dep of evolution-exchange
Installing libedataserverui1.2-8 as dep of evolution
Installing libegroupwise1.2-13 as dep of evolution
Installing libexchange-storage1.2-3 as dep of evolution
Installing libgnome-pilot2 as dep of evolution
Installing libgtkhtml3.14-19 as dep of evolution
Installing libnm-glib0 as dep of evolution
Installing evolution-common as dep of evolution
Installing evolution-data-server as dep of evolution
Installing libedata-book1.2-2 as dep of evolution-data-server
Installing libedata-cal1.2-6 as dep of evolution-data-server
Installing evolution-data-server-common as dep of evolution-data-server
Installing gtkhtml3.14 as dep of evolution
Installing libmysqlclient15off as dep of python-mysqldb
Installing mysql-common as dep of libmysqlclient15off
Installing esound-common as dep of esound
Installing libcurl3-gnutls as dep of python-pycurl
Installing libgnomekbd1 as dep of gnome-screensaver
Installing libgnomekbd-common as dep of libgnomekbd1
Installing libgnomekbdui1 as dep of gnome-screensaver
Installing libxcomposite1 as dep of gnome-mag
Installing libgpod1 as dep of rhythmbox
Installing libmusicbrainz4c2a as dep of rhythmbox
Installing gedit-common as dep of gedit
Installing python-gmenu as dep of gnome-menus
Installing gnome-panel-data as dep of gnome-panel
Installing libnewt0.52 as dep of python-newt
Installing libsnmp9 as dep of hpijs
Installing libsnmp-base as dep of libsnmp9
Installing genisoimage as dep of dvd+rw-tools
Installing feisty-gdm-themes as dep of ubuntu-artwork
Installing feisty-session-splashes as dep of ubuntu-artwork
Installing feisty-wallpapers as dep of ubuntu-artwork
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
Installing libslab0 as dep of gnome-control-center
Installing capplets-data as dep of gnome-control-center
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing hplip-data as dep of hplip
Installing gconf2-common as dep of gconf2
Installing avahi-autoipd as dep of ubuntu-desktop
Installing dcraw as dep of ubuntu-desktop
Installing desktop-effects as dep of ubuntu-desktop
Installing compiz as dep of desktop-effects
Installing compiz-core as dep of compiz
Installing compiz-plugins as dep of compiz
Installing libdecoration0 as dep of compiz-plugins
Installing compiz-gtk as dep of compiz
Installing compiz-gnome as dep of compiz
Installing gs-esp-x as dep of ubuntu-desktop
Installing gtk2-engines-pixbuf as dep of ubuntu-desktop
Installing libnss-mdns as dep of ubuntu-desktop
Installing openprinting-ppds as dep of ubuntu-desktop
new important dependency: espeak
Installing espeak as dep of ubuntu-desktop
Installing libespeak1 as dep of espeak
Installing espeak-data as dep of libespeak1
new important dependency: gcc
Installing gcc as dep of ubuntu-desktop
Installing cpp as dep of gcc
Installing cpp-4.1 as dep of cpp
Installing gcc-4.1 as dep of gcc
Installing binutils as dep of gcc-4.1
new important dependency: gnome-orca
Installing gnome-orca as dep of ubuntu-desktop
Installing python-orca-brlapi as dep of gnome-orca
Installing python-at-spi as dep of gnome-orca
new important dependency: linux-headers-generic
Installing linux-headers-generic as dep of ubuntu-desktop
Installing linux-headers-2.6.20-16-generic as dep of linux-headers-generic
Installing linux-headers-2.6.20-16 as dep of linux-headers-2.6.20-16-generic
new important dependency: make
Installing make as dep of ubuntu-desktop
new important dependency: network-manager-gnome
Installing network-manager-gnome as dep of ubuntu-desktop
Installing libnm-util0 as dep of network-manager-gnome
Installing network-manager as dep of network-manager-gnome
Installing libnl1-pre6 as dep of network-manager
Installing dhcdbd as dep of network-manager
new important dependency: onboard
Installing onboard as dep of ubuntu-desktop
Installing python-virtkey as dep of onboard
new important dependency: restricted-manager
Installing restricted-manager as dep of ubuntu-desktop
Installing python-notify as dep of restricted-manager
new important dependency: scim-tables-additional
Installing scim-tables-additional as dep of ubuntu-desktop
Installing scim-modules-table as dep of scim-tables-additional
Installing cupsys-client as dep of cupsys-bsd
Installing update-inetd as dep of cupsys-bsd
Installing python-apport as dep of apport
Installing python-problem-report as dep of python-apport
Installing python-launchpad-bugs as dep of python-apport
Installing libcaca0 as dep of gstreamer0.10-plugins-good
Installing libcucul0 as dep of libcaca0
Installing libvte9 as dep of gnome-terminal
Installing libvte-common as dep of libvte9
Installing gnome-terminal-data as dep of gnome-terminal
Installing myspell-en-za as dep of language-support-en
Installing e2fslibs as dep of e2fsprogs
Installing upstart as dep of upstart-compat-sysv
Installing libpoppler1 as dep of libpoppler1-glib
Installing libgtkhtml2-0 as dep of python-gtkhtml2
Installing libx86-1 as dep of vbetool
Installing libgd2-xpm as dep of python-gd
Installing libxml-twig-perl as dep of libnet-dbus-perl
Installing gnome-mount as dep of gnome-volume-manager
Installing libgdiplus as dep of libmono-system1.0-cil
Installing libungif4g as dep of libgdiplus
Installing libgnomecanvas2-common as dep of libgnomecanvas2-0
Installing python-gtk2 as dep of python-glade2
Installing python-bittorrent as dep of bittorrent
Installing language-selector-common as dep of language-selector
Installing openoffice.org-filter-mobiledev as dep of openoffice.org
Installing cupsys as dep of cupsys-driver-gutenprint
Installing libjaxp1.3-java as dep of libxerces2-java
Installing libbonobo2-common as dep of libbonobo2-0
Installing libmagic1 as dep of file
Installing software-properties-gtk as dep of gnome-app-install
Installing python-software-properties as dep of software-properties-gtk
Installing debconf as dep of tasksel
Installing gimp-data as dep of gimp
Installing vim-runtime as dep of vim
Installing mscompress as dep of foo2zjs
Installing libgl1-mesa-glx as dep of libgl1-mesa-dri
Installing libgda2-common as dep of libgda2-3
Installing liboobs-1-3 as dep of gnome-applets
Installing gnome-applets-data as dep of gnome-applets
Installing libusplash0 as dep of usplash
Installing gpgv as dep of gnupg
Starting
Starting 2
WARNING: Failed to read mirror file
Investigating libvolume-id0
Package libvolume-id0 has broken dep on libvolumeid0
  Considering libvolumeid0 4 as a solution to libvolume-id0 20
  Added libvolumeid0 to the remove list
  Fixing libvolume-id0 via remove of libvolumeid0
Investigating libsasl2
Package libsasl2 has broken dep on libsasl2-modules
  Considering libsasl2-modules 22 as a solution to libsasl2 4
Package libsasl2 has broken dep on libsasl2-modules-sql
Package libsasl2 has broken dep on libsasl2-modules-gssapi-heimdal
Package libsasl2 has broken dep on libsasl2-modules-kerberos-heimdal
  Or group remove for libsasl2
Investigating xserver-xorg-video-all
Package xserver-xorg-video-all has broken dep on xserver-xorg-driver-all
  Considering xserver-xorg-driver-all 0 as a solution to xserver-xorg-video-all 3
  Added xserver-xorg-driver-all to the remove list
  Fixing xserver-xorg-video-all via remove of xserver-xorg-driver-all
Investigating libgd2-noxpm
Package libgd2-noxpm has broken dep on libgd2-xpm
  Considering libgd2-xpm 2 as a solution to libgd2-noxpm 2
  Removing libgd2-noxpm rather than change libgd2-xpm
Investigating human-theme
Package human-theme has broken dep on human-gtk-theme
  Considering human-gtk-theme 0 as a solution to human-theme 2
  Added human-gtk-theme to the remove list
  Fixing human-theme via remove of human-gtk-theme
Investigating python-apport
Package python-apport has broken dep on python-apport-utils
  Considering python-apport-utils 0 as a solution to python-apport 2
  Added python-apport-utils to the remove list
  Fixing python-apport via remove of python-apport-utils
Investigating feisty-wallpapers
Package feisty-wallpapers has broken dep on edgy-wallpapers
  Considering edgy-wallpapers 0 as a solution to feisty-wallpapers 1
  Added edgy-wallpapers to the remove list
  Fixing feisty-wallpapers via remove of edgy-wallpapers
Investigating feisty-session-splashes
Package feisty-session-splashes has broken dep on edgy-session-splashes
  Considering edgy-session-splashes 0 as a solution to feisty-session-splashes 1
  Added edgy-session-splashes to the remove list
  Fixing feisty-session-splashes via remove of edgy-session-splashes
Investigating feisty-gdm-themes
Package feisty-gdm-themes has broken dep on edgy-gdm-themes
  Considering edgy-gdm-themes 0 as a solution to feisty-gdm-themes 1
  Added edgy-gdm-themes to the remove list
  Fixing feisty-gdm-themes via remove of edgy-gdm-themes
Investigating python-eunuchs
Package python-eunuchs has broken dep on python
  Considering python 653 as a solution to python-eunuchs 0
  Removing python-eunuchs rather than change python
Investigating python-id3lib
Package python-id3lib has broken dep on python
  Considering python 653 as a solution to python-id3lib 0
  Removing python-id3lib rather than change python
Done
Installing xserver-xorg-core as dep of xserver-xorg
Installing libc6 as dep of xserver-xorg-core
Installing libgcc1 as dep of xserver-xorg-core
Installing gcc-4.2-base as dep of libgcc1
Installing kdelibs4c2a as dep of kpdf
Installing libart-2.0-2 as dep of kdelibs4c2a
Installing libasound2 as dep of kdelibs4c2a
Installing libcupsys2 as dep of kdelibs4c2a
Installing libgnutls13 as dep of libcupsys2
Installing liblzo2-2 as dep of libgnutls13
Installing libopencdk8 as dep of libgnutls13
Installing zlib1g as dep of libgnutls13
Installing libkrb53 as dep of libcupsys2
Installing libkeyutils1 as dep of libkrb53
Installing libfreetype6 as dep of kdelibs4c2a
Installing libjasper1 as dep of kdelibs4c2a
Installing libstdc++6 as dep of kdelibs4c2a
Installing libxml2 as dep of kdelibs4c2a
Installing kdelibs-data as dep of kdelibs4c2a
Installing libpoppler2 as dep of kpdf
Installing xkb-data as dep of xkeyboard-config
Installing libdbus-1-3 as dep of gnome-keyring
Installing libglib2.0-0 as dep of gnome-keyring
Installing libgtk2.0-0 as dep of gnome-keyring
Installing libgtk2.0-common as dep of libgtk2.0-0
Installing libpango1.0-0 as dep of libgtk2.0-0
Installing libpango1.0-common as dep of libpango1.0-0
Installing libxdamage1 as dep of libgtk2.0-0
Installing libhal-storage1 as dep of gnome-keyring
Installing libhal1 as dep of gnome-keyring
Installing libgnomeui-0 as dep of f-spot
Installing libglade2-0 as dep of libgnomeui-0
Installing libgnome-keyring0 as dep of libgnomeui-0
Installing liborbit2 as dep of libgnomeui-0
Installing libgnomeui-common as dep of libgnomeui-0
Installing libmono0 as dep of f-spot
Installing libglade2.0-cil as dep of f-spot
Installing libglib2.0-cil as dep of libglade2.0-cil
Installing libgtk2.0-cil as dep of libglade2.0-cil
Installing libgnome-vfs2.0-cil as dep of f-spot
Installing libgphoto2-2 as dep of f-spot
Installing libgphoto2-port0 as dep of libgphoto2-2
Installing libgtkhtml2.0-cil as dep of f-spot
Installing libmono-corlib2.0-cil as dep of f-spot
Installing mono-jit as dep of libmono-corlib2.0-cil
Installing mono-common as dep of mono-jit
Installing libmono-system2.0-cil as dep of f-spot
Installing libmono2.0-cil as dep of f-spot
Installing libdevmapper1.02.1 as dep of dmsetup
Installing libselinux1 as dep of libdevmapper1.02.1
Installing libsepol1 as dep of libselinux1
Installing volumeid as dep of udev
Installing libvolume-id0 as dep of volumeid
Installing libgstreamer0.10-0 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing ghostscript-x as dep of gs-esp-x
Installing ghostscript as dep of ghostscript-x
Installing libgs8 as dep of ghostscript
Installing libcupsimage2 as dep of libgs8
Installing linux-image-386 as dep of linux-386
Installing linux-image-2.6.22-14-386 as dep of linux-image-386
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing linux-ubuntu-modules-2.6.22-14-386 as dep of linux-image-386
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing linux-restricted-modules-386 as dep of linux-386
Installing linux-restricted-modules-2.6.22-14-386 as dep of linux-restricted-modules-386
Installing linux-restricted-modules-common as dep of linux-restricted-modules-2.6.22-14-386
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing gcj-4.1-base as dep of libgcj7-jar
Installing libgcj7-1 as dep of libgcj7-jar
Installing libdbus-glib-1-2 as dep of libgnomekbd1
Installing libgnomekbd-common as dep of libgnomekbd1
Installing libsm6 as dep of libsm-dev
Installing gnome-specimen as dep of ubuntustudio-graphics
Installing libvorbisfile3 as dep of libarts1c2a
Installing gcc-3.3-base as dep of libstdc++5
Installing libgmime2.2-cil as dep of tomboy
Installing python-twisted-bin as dep of python-twisted-core
Installing perl as dep of libglib-perl
Installing perl-base as dep of perl
Installing perl-modules as dep of perl
Installing libbz2-1.0 as dep of bzip2
Installing libecal1.2-7 as dep of evolution-webcal
Installing libedataserver1.2-9 as dep of libecal1.2-7
Installing libnspr4-0d as dep of libedataserver1.2-9
Installing libebook1.2-9 as dep of ekiga
Installing libcamel1.2-10 as dep of libebook1.2-9
Installing libnss3-0d as dep of libcamel1.2-10
Installing libopal-2.2 as dep of ekiga
Installing libpt-1.10.0 as dep of libopal-2.2
Installing libssl0.9.8 as dep of libpt-1.10.0
Installing python as dep of python-examples
Installing python-minimal as dep of python
Installing libgtk2.0-dev as dep of libgnomeui-dev
Installing libglib2.0-dev as dep of libgnomeui-dev
Installing openoffice.org-core as dep of openoffice.org-gnome
Installing openoffice.org-common as dep of openoffice.org-core
Installing libcurl3-gnutls as dep of openoffice.org-core
Installing libdb4.5 as dep of openoffice.org-core
Installing libhunspell-1.1-0 as dep of openoffice.org-core
Installing libgimp2.0 as dep of gimp-print
Installing libgutenprint2 as dep of gimp-print
Installing libgutenprintui2-1 as dep of gimp-print
Installing libwnck22 as dep of notification-daemon
Installing libwnck-common as dep of libwnck22
Installing libgnomevfs2-common as dep of libgnomevfs2-0
Installing libquicktime1 as dep of dvgrab
Installing libavcodec1d as dep of libquicktime1
Installing libavutil1d as dep of libavcodec1d
Installing libgnomecanvas2-0 as dep of gthumb
Installing libgnomecanvas2-common as dep of libgnomecanvas2-0
Installing libjack0 as dep of sooperlooper
Installing libice6 as dep of libice-dev
Installing update-manager-core as dep of update-manager
Installing python-uno as dep of openoffice.org-writer
Installing libscim8c2a as dep of scim-modules-table
Installing gnome-media-common as dep of gnome-media
Installing openoffice.org-style-andromeda as dep of openoffice.org-style-default
Installing libmetacity0 as dep of metacity
Installing metacity-common as dep of libmetacity0
Installing libbeagle0 as dep of nautilus
Installing librsvg2-2 as dep of nautilus
Installing libgsf-1-114 as dep of librsvg2-2
Installing libgsf-1-common as dep of libgsf-1-114
Installing libtrackerclient0 as dep of nautilus
Installing nautilus-data as dep of nautilus
Installing python2.4 as dep of python2.4-examples
Installing python2.4-minimal as dep of python2.4
Installing libncursesw5 as dep of python2.4
Installing libtasn1-3 as dep of libtasn1-3-dev
Installing libgnome2-common as dep of libgnome2-0
Installing libbind9-30 as dep of bind9-host
Installing libdns32 as dep of libbind9-30
Installing libisc32 as dep of libdns32
Installing libisccfg30 as dep of libbind9-30
Installing libisccc30 as dep of libisccfg30
Installing liblwres30 as dep of bind9-host
Installing libnotify1 as dep of python-notify
Installing libatspi1.0-0 as dep of libgail-gnome-module
Installing openoffice.org-draw as dep of openoffice.org-impress
Installing libsvg1 as dep of openoffice.org-draw
Installing libwpg-0.1-1 as dep of openoffice.org-draw
Installing language-pack-en as dep of language-pack-en-base
Installing libgamin0 as dep of gamin
Installing python-imaging as dep of python-imaging-sane
Installing libglew1.4 as dep of enblend
Installing linux-headers-2.6.22-14-generic as dep of linux-headers-generic
Installing linux-headers-2.6.22-14 as dep of linux-headers-2.6.22-14-generic
Installing libaspell15 as dep of aspell
Installing dhcp3-common as dep of dhcp3-client
Installing libuniconf4.3 as dep of wvdial
Installing libwvstreams4.3-base as dep of libuniconf4.3
Installing libwvstreams4.3-extras as dep of libuniconf4.3
Installing xserver-xorg-video-amd as dep of xserver-xorg-video-all
Installing xserver-xorg-video-intel as dep of xserver-xorg-video-all
Installing xserver-xorg-video-psb as dep of xserver-xorg-video-all
Installing libdrm2 as dep of xserver-xorg-video-psb
Installing liboil0.3 as dep of gstreamer0.10-plugins-ugly
Installing xsane-common as dep of xsane
Installing ttf-indic-fonts-core as dep of ttf-indic-fonts
Installing ttf-bengali-fonts as dep of ttf-indic-fonts
Installing ttf-gujarati-fonts as dep of ttf-indic-fonts
Installing ttf-kannada-fonts as dep of ttf-indic-fonts
Installing ttf-malayalam-fonts as dep of ttf-indic-fonts
Installing ttf-oriya-fonts as dep of ttf-indic-fonts
Installing ttf-tamil-fonts as dep of ttf-indic-fonts
Installing ttf-telugu-fonts as dep of ttf-indic-fonts
Installing openoffice.org-java-common as dep of openoffice.org-filter-mobiledev
Installing xdg-utils as dep of libdjvulibre15
Installing libao2 as dep of vorbis-tools
Installing libflac8 as dep of vorbis-tools
Installing libiw29 as dep of wireless-tools
Installing initramfs-tools as dep of lvm2
Installing libraptor1 as dep of librdf0
Installing libcurl3 as dep of libraptor1
Installing librasqal0 as dep of librdf0
Installing libsqlite3-0 as dep of librdf0
Installing samba-common as dep of smbclient
Installing libslang2 as dep of whiptail
Installing libgpg-error0 as dep of libgpg-error-dev
new important dependency: apparmor-utils
Installing apparmor-utils as dep of ubuntu-standard
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apparmor as dep of apparmor-utils
Installing libterm-readkey-perl as dep of apparmor-utils
Installing librpc-xml-perl as dep of apparmor-utils
Installing libgda3-3 as dep of python-gnome2-extras
Installing libgda3-common as dep of libgda3-3
Installing libgdl-gnome-1-0 as dep of python-gnome2-extras
Installing libgdl-1-common as dep of libgdl-gnome-1-0
Installing libgucharmap6 as dep of gucharmap
Installing brltty as dep of brltty-x11
Installing libbluetooth2 as dep of libbtctl4
Installing libxv1 as dep of libxv-dev
Installing libwxbase2.6-0 as dep of freqtweak
Installing libwxgtk2.6-0 as dep of freqtweak
Installing libdaemon0 as dep of avahi-daemon
Installing gnome-games-data as dep of gnome-games
Installing gnome-cards-data as dep of gnome-games-data
Installing libgconf11 as dep of libgconf-dev
Installing gconf as dep of libgconf-dev
Installing gdebi-core as dep of gdebi
Installing python-apt as dep of gdebi-core
Installing apt-utils as dep of python-apt
Installing apt as dep of apt-utils
Installing python-central as dep of python-apt
Installing dpkg as dep of python-central
Installing evolution as dep of evolution-exchange
Installing libedataserverui1.2-8 as dep of evolution
Installing libegroupwise1.2-13 as dep of evolution
Installing libexchange-storage1.2-3 as dep of evolution
Installing libgtkhtml3.14-19 as dep of evolution
Installing evolution-data-server as dep of evolution
Installing libedata-book1.2-2 as dep of evolution-data-server
Installing libedata-cal1.2-6 as dep of evolution-data-server
Installing evolution-data-server-common as dep of evolution-data-server
Installing libgnome-desktop-2 as dep of libgnome-desktop-dev
Installing gcc-4.1 as dep of g++-4.1
Installing cpp-4.1 as dep of gcc-4.1
Installing libstdc++6-4.1-dev as dep of g++-4.1
Installing esound-common as dep of esound
Installing libgpod2 as dep of rhythmbox
Installing libmtp6 as dep of rhythmbox
Installing libmusicbrainz4c2a as dep of rhythmbox
Installing libtotem-plparser7 as dep of rhythmbox
Installing libgcrypt11 as dep of libgcrypt11-dev
Installing jackd as dep of ardour
Installing libgtksourceview2.0-0 as dep of gedit
Installing libgtksourceview2.0-common as dep of libgtksourceview2.0-0
Installing gedit-common as dep of gedit
Installing python-pygtksourceview as dep of gedit
Installing python-gmenu as dep of gnome-menus
Installing libnewt0.52 as dep of python-newt
Installing libsnmp10 as dep of hpijs
Installing libsnmp-base as dep of libsnmp10
Installing aeolus as dep of ubuntustudio-audio-plugins
Installing libclalsadrv1 as dep of aeolus
Installing libclthreads2 as dep of aeolus
Installing libclxclient3 as dep of aeolus
Installing stops as dep of aeolus
Installing fluidsynth-dssi as dep of ubuntustudio-audio-plugins
Installing hexter as dep of ubuntustudio-audio-plugins
Installing vcf as dep of ubuntustudio-audio-plugins
Installing xsynth-dssi as dep of ubuntustudio-audio-plugins
Installing gutsy-wallpapers as dep of ubuntu-artwork
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
Installing capplets-data as dep of gnome-control-center
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing libsasl2-2 as dep of libsasl2-modules
Installing libxi6 as dep of libxi-dev
Installing hplip-data as dep of hplip
Installing gconf2-common as dep of gconf2
Installing libxrender1 as dep of libxrender-dev
Installing cupsys-client as dep of cupsys-bsd
Installing libcairo2 as dep of libcairo2-dev
Installing libfreetype6-dev as dep of libcairo2-dev
Installing libhal-storage-dev as dep of libgnome-keyring-dev
Installing libhal-dev as dep of libhal-storage-dev
Installing fontconfig-config as dep of libfontconfig1
Installing libx264-54 as dep of gstreamer0.10-plugins-bad-multiverse
Installing libswt3.2-gtk-jni as dep of libswt3.2-gtk-java
Installing libsvn1 as dep of subversion
Installing libgnome-speech7 as dep of gnopernicus
Installing libespeak1 as dep of libgnome-speech7
Installing espeak-data as dep of libespeak1
Installing scim-gtk2-immodule as dep of scim
Installing update-notifier-common as dep of update-notifier
Installing restricted-manager-core as dep of restricted-manager
Installing guidance-backends as dep of restricted-manager-core
Installing libxdmcp6 as dep of libxdmcp-dev
Installing cpp as dep of g++
Installing gcc as dep of g++
Installing libavahi-client3 as dep of libavahi-client-dev
Installing python2.5-minimal as dep of python2.5
Installing libcinepaint0 as dep of cinepaint
Installing cinepaint-data as dep of cinepaint
Installing e2fslibs as dep of e2fsprogs
Installing libglib-jni as dep of libgtk-jni
Installing libpng12-0 as dep of libpng12-dev
Installing upstart as dep of upstart-compat-sysv
Installing libart2.0-cil as dep of libgnome2.0-cil
Installing librsvg2.0-cil as dep of libgnome2.0-cil
Installing libgtkhtml2-0 as dep of python-gtkhtml2
Installing libruby1.8 as dep of ruby1.8
Installing texlive as dep of tetex-bin
Installing texlive-fonts-recommended as dep of texlive
Installing texlive-base as dep of texlive-fonts-recommended
Installing texlive-doc-base as dep of texlive-base
Installing texlive-common as dep of texlive-doc-base
Installing tex-common as dep of texlive-common
Installing texlive-base-bin as dep of texlive-base
Installing libkpathsea4 as dep of texlive-base-bin
Installing texlive-latex-recommended as dep of texlive
Installing texlive-latex-base as dep of texlive-latex-recommended
Installing libgtop2-7 as dep of gnome-utils
Installing libcairo-jni as dep of libcairo-java
Installing libglib-java as dep of libcairo-java
Installing dmz-cursor-theme as dep of human-theme
Installing libxcursor1 as dep of libxcursor-dev
Installing python-orca-brlapi as dep of gnome-orca
Installing python-problem-report as dep of python-apport
Installing python-sip4 as dep of python-qt3
Installing libsynfig0 as dep of libsynfigapp0
Installing libavformat1d as dep of libsynfig0
Installing belocs-locales-bin as dep of locales
Installing libbonobo2-0 as dep of libbonobo2-dev
Installing libbonobo2-common as dep of libbonobo2-0
Installing libpostproc1d as dep of libxine1-ffmpeg
Installing libxine1 as dep of libxine1-ffmpeg
Installing libxcb-shape0 as dep of libxine1
Installing libxcb1 as dep of libxcb-shape0
Installing libxcb-shm0 as dep of libxine1
Installing libxcb-xv0 as dep of libxine1
Installing libswscale1d as dep of ffmpeg2theora
Installing libebml0 as dep of vlc-nox
Installing libmatroska0 as dep of vlc-nox
Installing hugin-bin as dep of hugin
Installing libboost-thread1.34.1 as dep of hugin-bin
Installing libwxbase2.8-0 as dep of hugin-bin
Installing libwxgtk2.8-0 as dep of hugin-bin
Installing hugin-data as dep of hugin-bin
Installing hugin-tools as dep of hugin
Installing libpano12-bin as dep of hugin
Installing autopano-sift as dep of hugin
Installing libgnutlsxx13 as dep of libgnutls-dev
Installing liblzo2-dev as dep of libgnutls-dev
Installing hal-info as dep of hal
Installing python-gtk2 as dep of python-glade2
Installing mixxx-data as dep of mixxx
Installing amarok as dep of amarok-xine
Installing libvte9 as dep of python-vte
Installing libvte-common as dep of libvte9
Installing language-selector-common as dep of language-selector
Installing libxext6 as dep of libxext-dev
Installing libjpeg62 as dep of libjpeg62-dev
Installing pidgin as dep of gaim
Installing pidgin-data as dep of pidgin
Installing libpurple0 as dep of pidgin
Installing libzephyr3 as dep of libpurple0
Installing libhesiod0 as dep of libzephyr3
Installing libpcrecpp0 as dep of gnome-system-monitor
Installing libimlib2 as dep of ffmpeg
Installing libgd2-xpm as dep of libusplash-dev
Installing libpoppler-glib2 as dep of evince
Installing recordmydesktop as dep of gtk-recordmydesktop
Installing libmagic1 as dep of file
Installing python-sexy as dep of gnome-app-install
Installing gij-4.2 as dep of java-gcj-compat
Installing gcj-4.2-base as dep of gij-4.2
Installing libgcj8-1 as dep of gij-4.2
Installing libgcj-bc as dep of java-gcj-compat
Installing libgcj8-jar as dep of java-gcj-compat
Installing libmx4j-java as dep of java-gcj-compat
Installing libbcel-java as dep of libmx4j-java
Installing libregexp-java as dep of libbcel-java
Installing libgail-dev as dep of libgnomecanvas2-dev
Installing libflac++6 as dep of hydrogen
Installing libmms0 as dep of gstreamer0.10-plugins-bad
Installing libopenspc0 as dep of gstreamer0.10-plugins-bad
Installing gimp-data as dep of gimp
Installing vim-runtime as dep of vim
Installing ttf-dejavu-core as dep of ttf-dejavu
Installing ttf-dejavu-extra as dep of ttf-dejavu
Installing librarian0 as dep of yelp
Installing dmidecode as dep of laptop-detect
Installing libxrandr2 as dep of libxrandr-dev
Installing libgl1-mesa-glx as dep of libgl1-mesa-dri
Installing audacious as dep of ubuntustudio-audio
Installing libaudacious5 as dep of audacious
Installing libmcs1 as dep of libaudacious5
Installing audacious-plugins as dep of audacious
Installing audacious-plugins-extra as dep of ubuntustudio-audio
Installing libbinio1c2 as dep of audacious-plugins-extra
Installing libresid-builder0c2a as dep of audacious-plugins-extra
Installing libsidplay2 as dep of audacious-plugins-extra
Installing qsampler as dep of ubuntustudio-audio
Installing libgig6 as dep of qsampler
Installing liblscp as dep of qsampler
Installing gnome-applets-data as dep of gnome-applets
Installing libservlet2.4-java as dep of libhsqldb-java
Installing gnome-panel-data as dep of gnome-panel
Installing libavahi-compat-libdnssd1 as dep of cupsys
Installing libavahi-common3 as dep of libavahi-common-dev
Installing libexiv2-0 as dep of gimp-ufraw
Installing libxinerama1 as dep of libxinerama-dev
Installing libntfs-3g12 as dep of ntfs-3g
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Installing rosegarden as dep of rosegarden4
Installing sndfile-programs as dep of rosegarden
Installing libopenal-dev as dep of libalut-dev
Starting
Starting 2
Investigating dbus
Package dbus has broken dep on dbus-1-utils
  Considering dbus-1-utils -1 as a solution to dbus 124
  Added dbus-1-utils to the remove list
  Fixing dbus via remove of dbus-1-utils
Investigating gimp
Package gimp has broken dep on gimp-svg
  Considering gimp-svg -1 as a solution to gimp 11
  Added gimp-svg to the remove list
  Fixing gimp via remove of gimp-svg
Investigating firefox
Package firefox has broken dep on libnss3
  Considering libnss3 1 as a solution to firefox 7
  Added libnss3 to the remove list
  Fixing firefox via remove of libnss3
Investigating libwnck18
Package libwnck18 has broken dep on libwnck-common
  Considering libwnck-common 20 as a solution to libwnck18 5
  Removing libwnck18 rather than change libwnck-common
Investigating libmtp6
Package libmtp6 has broken dep on libmtp5
  Considering libmtp5 -1 as a solution to libmtp6 3
  Added libmtp5 to the remove list
  Fixing libmtp6 via remove of libmtp5
Investigating ubuntustudio-look
Package ubuntustudio-look has broken dep on ubuntustudio-artwork
  Considering ubuntustudio-artwork -1 as a solution to ubuntustudio-look 3
  Added ubuntustudio-artwork to the remove list
  Fixing ubuntustudio-look via remove of ubuntustudio-artwork
Investigating emerald
Package emerald has broken dep on libwnck18
  Considering libwnck18 5 as a solution to emerald 3
  Removing emerald rather than change libwnck18
Investigating libglew1.4
Package libglew1.4 has broken dep on libglew1
  Considering libglew1 -1 as a solution to libglew1.4 2
  Added libglew1 to the remove list
  Fixing libglew1.4 via remove of libglew1
Investigating libemeraldengine0
Package libemeraldengine0 has broken dep on libwnck18
  Considering libwnck18 5 as a solution to libemeraldengine0 2
  Removing libemeraldengine0 rather than change libwnck18
Investigating libexiv2-0
Package libexiv2-0 has broken dep on libexiv2-0.12
  Considering libexiv2-0.12 -1 as a solution to libexiv2-0 1
  Added libexiv2-0.12 to the remove list
  Fixing libexiv2-0 via remove of libexiv2-0.12
Investigating human-theme
Package human-theme has broken dep on human-cursors-theme
  Considering human-cursors-theme 2 as a solution to human-theme 1
  Holding Back human-theme rather than change human-cursors-theme
Investigating libgnome-speech7
Package libgnome-speech7 has broken dep on libgnome-speech3
  Considering libgnome-speech3 -1 as a solution to libgnome-speech7 1
  Added libgnome-speech3 to the remove list
  Fixing libgnome-speech7 via remove of libgnome-speech3
Investigating hexter
Package hexter has broken dep on dssi-plugin-hexter
  Considering dssi-plugin-hexter -1 as a solution to hexter 0
  Added dssi-plugin-hexter to the remove list
  Fixing hexter via remove of dssi-plugin-hexter
Investigating lvm2
Package lvm2 has broken dep on lvm-common
  Considering lvm-common -1 as a solution to lvm2 0
  Added lvm-common to the remove list
  Fixing lvm2 via remove of lvm-common
Investigating fluidsynth-dssi
Package fluidsynth-dssi has broken dep on dssi-plugin-fluidsynth
  Considering dssi-plugin-fluidsynth -1 as a solution to fluidsynth-dssi 0
  Added dssi-plugin-fluidsynth to the remove list
  Fixing fluidsynth-dssi via remove of dssi-plugin-fluidsynth
Investigating libopal-2.2
Package libopal-2.2 has broken dep on libopal-2.2.0
  Considering libopal-2.2.0 -1 as a solution to libopal-2.2 0
  Added libopal-2.2.0 to the remove list
  Fixing libopal-2.2 via remove of libopal-2.2.0
Investigating vcf
Package vcf has broken dep on vcf-plugins
  Considering vcf-plugins -1 as a solution to vcf 0
  Added vcf-plugins to the remove list
  Fixing vcf via remove of vcf-plugins
Investigating libuniconf4.3
Package libuniconf4.3 has broken dep on libuniconf4.2
  Considering libuniconf4.2 -1 as a solution to libuniconf4.3 0
  Added libuniconf4.2 to the remove list
  Fixing libuniconf4.3 via remove of libuniconf4.2
Investigating beryl
Package beryl has broken dep on emerald
  Considering emerald 3 as a solution to beryl 0
Package beryl has broken dep on aquamarine
Package beryl has broken dep on heliodor
Package beryl has broken dep on yawd
Package beryl has broken dep on compiz-gnome
  Considering compiz-gnome 1 as a solution to beryl 0
  Or group remove for beryl
Investigating xsynth-dssi
Package xsynth-dssi has broken dep on dssi-plugin-xsynth
  Considering dssi-plugin-xsynth -1 as a solution to xsynth-dssi 0
  Added dssi-plugin-xsynth to the remove list
  Fixing xsynth-dssi via remove of dssi-plugin-xsynth
Investigating libcamel1.2-8
Package libcamel1.2-8 has broken dep on libnss3
  Considering libnss3 1 as a solution to libcamel1.2-8 -1
  Removing libcamel1.2-8 rather than change libnss3
Investigating emerald-themes
Package emerald-themes has broken dep on emerald
  Considering emerald 3 as a solution to emerald-themes -1
  Removing emerald-themes rather than change emerald
Investigating libawn-svn
Package libawn-svn has broken dep on libwnck18
  Considering libwnck18 5 as a solution to libawn-svn -1
  Removing libawn-svn rather than change libwnck18
 Try to Re-Instate human-theme
Investigating beryl-manager
Package beryl-manager has broken dep on beryl
  Considering beryl 0 as a solution to beryl-manager 0
  Removing beryl-manager rather than change beryl
Done
Installing consolekit as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing fast-user-switch-applet as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing system-config-printer as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing python-cups as dep of system-config-printer
Installing ubuntu-sounds as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xdg-user-dirs as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xdg-user-dirs-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xvnc4viewer as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing bluez-gnome as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing bogofilter as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing bogofilter-bdb as dep of bogofilter
Installing libgsl0 as dep of bogofilter-bdb
Installing bogofilter-common as dep of bogofilter-bdb
Installing compiz as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing compiz-core as dep of compiz
Installing compiz-plugins as dep of compiz
Installing compiz-gnome as dep of compiz
Installing libcompizconfig-backend-gconf as dep of compiz-gnome
Installing libcompizconfig0 as dep of libcompizconfig-backend-gconf
Installing compiz-fusion-plugins-main as dep of compiz
Installing compiz-fusion-plugins-extra as dep of compiz
Installing cups-pdf as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libpaper-utils as dep of cups-pdf
Installing displayconfig-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing hal-cups-utils as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libdeskbar-tracker as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing tracker as dep of libdeskbar-tracker
Installing o3read as dep of tracker
Installing libpam-gnome-keyring as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing pxljr as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing splix as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing tracker-search-tool as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libtracker-gtk0 as dep of tracker-search-tool
Installing ttf-unfonts-core as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing ubufox as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apturl as dep of ubufox
Starting
Starting 2
Investigating ubuntustudio-sounds
Package ubuntustudio-sounds has broken dep on ubuntu-sounds
  Considering ubuntu-sounds 1 as a solution to ubuntustudio-sounds 2
  Added ubuntu-sounds to the remove list
  Fixing ubuntustudio-sounds via keep of ubuntu-sounds
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on ubuntu-sounds
  Considering ubuntu-sounds 1 as a solution to ubuntu-desktop 9999
  Re-Instated ubuntu-sounds
Investigating ubuntustudio-sounds
Package ubuntustudio-sounds has broken dep on ubuntu-sounds
  Considering ubuntu-sounds 1 as a solution to ubuntustudio-sounds 2
  Added ubuntu-sounds to the remove list
  Fixing ubuntustudio-sounds via keep of ubuntu-sounds
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on ubuntu-sounds
  Considering ubuntu-sounds 1 as a solution to ubuntu-desktop 9999
Done


A quick glance through the list looks like Ubuntu Studio is causing some problem with the upgrade

What should i do

Thanks in advance

---

### Post by Cubedude04 on 2007-10-23
Bump please =/

---

### Post by Anicka on 2007-10-23
What happens if you run "sudo apt-get install -f"? And also post your source-list.

---

### Post by Cubedude04 on 2007-10-23
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libawn-svn
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


and my sources.list is


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main

deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main
deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) feisty avant-window-navigator

# Treviño's Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
# Many eyecandy 3D apps like Beryl, Compiz, Fusion and kiba-dock snapshots
# built using latest available (working) sources from git/svn/cvs.
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

I also just tried to upgrade again and got


Authentication failed

Authenticating the upgrade failed. There may be a problem with the network or with the server.  my internet is working fine =(

---

### Post by Anicka on 2007-10-23
From which distro did you start before updating? Seems you're in feisty now, which would indicate that you started from edgy. In that case your update was successful. Can you run apt-get update and apt-get upgrade and see if anything happens?

---

### Post by Cubedude04 on 2007-10-23
I installed dapper about 3 months ago and immediatly after installing i upgraded to Edgy then to Feisty.  this was about 4 months ago after running feisty for a month i download Ubuntustudio which seems to be causing the problems 

i ran sudo apt-get update
sudo apt-get upgrade and it seems to be downloading quite alot of files which surprises me as i ran those commands a few weeks ago

Should i try and upgrade to gutsy now?

---

### Post by Anicka on 2007-10-23
Upgraded packages a few weeks ago? In ubuntu there are new updates nearly every day.

Before you upgrade to Gutsy, I suggest that you edit your source-list by putting a # in front of any non-ubuntu/ubuntustudio repos. Also it might be a good idea to uninstall beryl (many people have problems with that). Thereafter you can try to upgrade to Gutsy.

---

