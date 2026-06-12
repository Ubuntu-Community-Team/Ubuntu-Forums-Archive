---
title: "[SOLVED] Dapper to Edgy upgrade failed W. apt.log"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by jrlii on 2007-04-21
Since Feisty is out I figured Edgy was safe enough to upgrade to.

No joy.

Please forgive me 'cause I haven't a clue, and I've included the logs from the last try below.
I'm still pretty new to Linux, though I've been programming minis and mainframes since the early '70s. Not much system-level stuff, though.

Dapper had all the patches.

I downloaded the Edgy ISO from the Argonne mirror at work, brought it home on a thumb drive and burnt it to CD.

I first tryied the standard upgrade: 

gksu "update-manager -c"

This ran for a while, hitting the modem hard and eventually failed, after saying it would take over 27 hours.

I eventually found the recomendation for updating from CD:

gksu sh /cdrom/cdromupgrade

IIRC This made it a tad further: The first method failed (or at least threw errors) during the "Modifying software channels" stage. 

This failed at (or near) `the beginning of the "Fetching and installing the upgrades."

The errors listed were: --------------------------------------------------------------------------------------------

Traceback (most recent call last):

  File "/tmp/tmp.0zwt9T/edgy", line 40, in ?
    app.run()

  File "/tmp/tmp.0zwt9T/DistUpgradeControler.py", line 765, in run
    self.edgyUpgrade()

  File "/tmp/tmp.0zwt9T/DistUpgradeControler.py", line 744, in edgyUpgrade
    if not self.askDistUpgrade():

  File "/tmp/tmp.0zwt9T/DistUpgradeControler.py", line 438, in askDistUpgrade
    if not self.cache.distUpgrade(self._view):

  File "/tmp/tmp.0zwt9T/DistUpgradeCache.py", line 237, in distUpgrade
    if not self._installMetaPkgs(view):

  File "/tmp/tmp.0zwt9T/DistUpgradeCache.py", line 343, in _installMetaPkgs
    self[key].markInstall()

  File "/usr/lib/python2.4/site-packages/apt/cache.py", line 78, in __getitem__
    return self._dict[key]

KeyError: 'ubuntu-desktop'

-----------------------------------------------------------------------------------------------------------------------

It said to include /var/distupgrade/apt.log in the report,so here it is:-----------------------


gzip: stdin: not in gzip format

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format

gzip: stdin: not in gzip format
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
gpgv: Signature made Wed 25 Oct 2006 09:10:29 AM CDT using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Starting
Starting 2
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
Investigating python-gtk2
Package python-gtk2 has broken dep on python2.4-gtk2
  Considering python2.4-gtk2 6 as a solution to python-gtk2 47
  Added python2.4-gtk2 to the remove list
  Fixing python-gtk2 via remove of python2.4-gtk2
Investigating upstart
Package upstart has broken dep on sysvinit
  Considering sysvinit 5100 as a solution to upstart 25
  Holding Back upstart rather than change sysvinit
Investigating python-numeric
Package python-numeric has broken dep on python2.4-numeric
  Considering python2.4-numeric 5 as a solution to python-numeric 23
  Added python2.4-numeric to the remove list
  Fixing python-numeric via remove of python2.4-numeric
Investigating libgl1-mesa-glx
Package libgl1-mesa-glx has broken dep on libgl1
  Considering libgl1-mesa 5 as a solution to libgl1-mesa-glx 20
  Added libgl1-mesa to the remove list
  Considering libgl1-mesa-swx11 0 as a solution to libgl1-mesa-glx 20
  Considering libgl1-mesa-glide3 0 as a solution to libgl1-mesa-glx 20
Package libgl1-mesa-glx has broken dep on libgl1-mesa
  Considering libgl1-mesa 5 as a solution to libgl1-mesa-glx 20
  Added libgl1-mesa to the remove list
  Fixing libgl1-mesa-glx via remove of libgl1-mesa
  Fixing libgl1-mesa-glx via remove of libgl1-mesa
Investigating python-cairo
Package python-cairo has broken dep on python2.4-cairo
  Considering python2.4-cairo 5 as a solution to python-cairo 20
  Added python2.4-cairo to the remove list
  Fixing python-cairo via remove of python2.4-cairo
Investigating python-gobject
Package python-gobject has broken dep on python2.4-gobject
  Considering python2.4-gobject 5 as a solution to python-gobject 20
  Added python2.4-gobject to the remove list
  Fixing python-gobject via remove of python2.4-gobject
Investigating python-pyorbit
Package python-pyorbit has broken dep on python2.4-pyorbit
  Considering python2.4-pyorbit 5 as a solution to python-pyorbit 18
  Added python2.4-pyorbit to the remove list
  Fixing python-pyorbit via remove of python2.4-pyorbit
Investigating python-glade2
Package python-glade2 has broken dep on python2.4-glade2
  Considering python2.4-glade2 0 as a solution to python-glade2 18
  Added python2.4-glade2 to the remove list
  Fixing python-glade2 via remove of python2.4-glade2
Investigating libnewt0.52
Package libnewt0.52 has broken dep on libnewt0.51
  Considering libnewt0.51 3 as a solution to libnewt0.52 13
  Added libnewt0.51 to the remove list
  Fixing libnewt0.52 via remove of libnewt0.51
Investigating upstart-compat-sysv
Package upstart-compat-sysv has broken dep on upstart
  Considering upstart 25 as a solution to upstart-compat-sysv 12
  Holding Back upstart-compat-sysv rather than change upstart
Investigating python-apt
Package python-apt has broken dep on python2.4-apt
  Considering python2.4-apt 0 as a solution to python-apt 9
  Added python2.4-apt to the remove list
  Fixing python-apt via remove of python2.4-apt
Investigating startup-tasks
Package startup-tasks has broken dep on upstart
  Considering upstart 25 as a solution to startup-tasks 8
  Holding Back startup-tasks rather than change upstart
Investigating system-services
Package system-services has broken dep on upstart
  Considering upstart 25 as a solution to system-services 8
  Holding Back system-services rather than change upstart
Investigating upstart-logd
Package upstart-logd has broken dep on upstart
  Considering upstart 25 as a solution to upstart-logd 8
  Holding Back upstart-logd rather than change upstart
Investigating python-libxml2
Package python-libxml2 has broken dep on python2.4-libxml2
  Considering python2.4-libxml2 2 as a solution to python-libxml2 7
  Added python2.4-libxml2 to the remove list
  Fixing python-libxml2 via remove of python2.4-libxml2
Investigating python-gnome2-desktop
Package python-gnome2-desktop has broken dep on python2.4-gnome2-desktop
  Considering python2.4-gnome2-desktop 0 as a solution to python-gnome2-desktop 7
  Added python2.4-gnome2-desktop to the remove list
  Fixing python-gnome2-desktop via remove of python2.4-gnome2-desktop
Investigating python-gnome2
Package python-gnome2 has broken dep on python2.4-gnome2
  Considering python2.4-gnome2 2 as a solution to python-gnome2 5
  Added python2.4-gnome2 to the remove list
  Fixing python-gnome2 via remove of python2.4-gnome2
Investigating libgcj7-0
Package libgcj7-0 has broken dep on libgcj7
  Considering libgcj7 0 as a solution to libgcj7-0 5
  Added libgcj7 to the remove list
  Fixing libgcj7-0 via remove of libgcj7
Investigating python-dbus
Package python-dbus has broken dep on python2.4-dbus
  Considering python2.4-dbus 0 as a solution to python-dbus 5
  Added python2.4-dbus to the remove list
  Fixing python-dbus via remove of python2.4-dbus
Investigating ubuntu-minimal
Package ubuntu-minimal has broken dep on startup-tasks
  Considering startup-tasks 8 as a solution to ubuntu-minimal 5
  Holding Back ubuntu-minimal rather than change startup-tasks
Investigating libxklavier11
Package libxklavier11 has broken dep on libxklavier10
  Considering libxklavier10 0 as a solution to libxklavier11 5
  Added libxklavier10 to the remove list
  Fixing libxklavier11 via remove of libxklavier10
Investigating python-egenix-mxtools
Package python-egenix-mxtools has broken dep on python2.4-egenix-mxtools
  Considering python2.4-egenix-mxtools 5 as a solution to python-egenix-mxtools 5
  Holding Back python-egenix-mxtools rather than change python2.4-egenix-mxtools
Investigating xutils-dev
Package xutils-dev has broken dep on imake
  Considering imake 0 as a solution to xutils-dev 5
  Added imake to the remove list
Package xutils-dev has broken dep on makedepend
  Considering makedepend 1 as a solution to xutils-dev 5
  Added makedepend to the remove list
  Fixing xutils-dev via remove of imake
  Fixing xutils-dev via remove of makedepend
Investigating python-gnome2-extras
Package python-gnome2-extras has broken dep on python2.4-gnome2-extras
  Considering python2.4-gnome2-extras 0 as a solution to python-gnome2-extras 3
  Added python2.4-gnome2-extras to the remove list
  Fixing python-gnome2-extras via remove of python2.4-gnome2-extras
Investigating python-xml
Package python-xml has broken dep on python2.4-xml
  Considering python2.4-xml 2 as a solution to python-xml 3
  Added python2.4-xml to the remove list
  Fixing python-xml via remove of python2.4-xml
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
  Considering python2.4 284 as a solution to python2.4-tk 2
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
Investigating linux-libc-dev
Package linux-libc-dev has broken dep on linux-kernel-headers
  Considering linux-kernel-headers 2 as a solution to linux-libc-dev 2
  Holding Back linux-libc-dev rather than change linux-kernel-headers
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
Investigating hpijs
Package hpijs has broken dep on hplip-ppds
  Considering hplip-ppds 2 as a solution to hpijs 1
  Holding Back hpijs rather than change hplip-ppds
Investigating python-imaging
Package python-imaging has broken dep on python2.4-imaging
  Considering python2.4-imaging 1 as a solution to python-imaging 1
  Holding Back python-imaging rather than change python2.4-imaging
Investigating python-gdbm
Package python-gdbm has broken dep on python2.4-gdbm
  Considering python2.4-gdbm 0 as a solution to python-gdbm 1
  Added python2.4-gdbm to the remove list
  Fixing python-gdbm via remove of python2.4-gdbm
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
Investigating python-kjbuckets
Package python-kjbuckets has broken dep on python2.4-kjbuckets
  Considering python2.4-kjbuckets 0 as a solution to python-kjbuckets 0
  Holding Back python-kjbuckets rather than change python2.4-kjbuckets
Investigating python-pgsql
Package python-pgsql has broken dep on python2.4-pgsql
  Considering python2.4-pgsql 0 as a solution to python-pgsql 0
  Holding Back python-pgsql rather than change python2.4-pgsql
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
Investigating python-gadfly
Package python-gadfly has broken dep on python2.4-gadfly
  Considering python2.4-gadfly 0 as a solution to python-gadfly 0
  Holding Back python-gadfly rather than change python2.4-gadfly
Investigating python-soappy
Package python-soappy has broken dep on python2.4-soappy
  Considering python2.4-soappy 0 as a solution to python-soappy 0
  Holding Back python-soappy rather than change python2.4-soappy
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
Investigating python-syck
Package python-syck has broken dep on python2.4-syck
  Considering python2.4-syck 0 as a solution to python-syck 0
  Holding Back python-syck rather than change python2.4-syck
Investigating python-egenix-mxdatetime
Package python-egenix-mxdatetime has broken dep on python2.4-egenix-mxdatetime
  Considering python2.4-egenix-mxdatetime 1 as a solution to python-egenix-mxdatetime 0
  Holding Back python-egenix-mxdatetime rather than change python2.4-egenix-mxdatetime
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
Investigating python-htmltmpl
Package python-htmltmpl has broken dep on python2.4-htmltmpl
  Considering python2.4-htmltmpl 0 as a solution to python-htmltmpl 0
  Holding Back python-htmltmpl rather than change python2.4-htmltmpl
Investigating python-reportlab
Package python-reportlab has broken dep on python2.4-reportlab
  Considering python2.4-reportlab 0 as a solution to python-reportlab 0
  Holding Back python-reportlab rather than change python2.4-reportlab
Investigating python-simpletal
Package python-simpletal has broken dep on python2.4-simpletal
  Considering python2.4-simpletal 0 as a solution to python-simpletal 0
  Holding Back python-simpletal rather than change python2.4-simpletal
 Try to Re-Instate ubuntu-minimal
 Try to Re-Instate python-egenix-mxtools
Investigating libc6-dev
Package libc6-dev has broken dep on linux-libc-dev
  Considering linux-libc-dev 2 as a solution to libc6-dev 3
  Removing libc6-dev rather than change linux-libc-dev
Investigating libstdc++6-4.0-dev
Package libstdc++6-4.0-dev has broken dep on libc6-dev
  Considering libc6-dev 3 as a solution to libstdc++6-4.0-dev 2
  Removing libstdc++6-4.0-dev rather than change libc6-dev
Investigating g++-4.0
Package g++-4.0 has broken dep on libstdc++6-4.0-dev
  Considering libstdc++6-4.0-dev 2 as a solution to g++-4.0 2
  Removing g++-4.0 rather than change libstdc++6-4.0-dev
 Try to Re-Instate hpijs
Investigating libstdc++6-4.1-dev
Package libstdc++6-4.1-dev has broken dep on libc6-dev
  Considering libc6-dev 3 as a solution to libstdc++6-4.1-dev 1
  Holding Back libstdc++6-4.1-dev rather than change libc6-dev
 Try to Re-Instate python-imaging
 Try to Re-Instate python-crypto
 Try to Re-Instate python-egenix-mxtexttools
 Try to Re-Instate python-ldap
 Try to Re-Instate python-pexpect
 Try to Re-Instate python-imaging-sane
 Try to Re-Instate python-mysqldb
 Try to Re-Instate python-pyxattr
 Try to Re-Instate python-kjbuckets
 Try to Re-Instate python-pgsql
 Try to Re-Instate python-htmlgen
 Try to Re-Instate python-clientcookie
 Try to Re-Instate python-adns
 Try to Re-Instate python-pam
 Try to Re-Instate python-gadfly
 Try to Re-Instate python-soappy
 Try to Re-Instate python-pyopenssl
 Try to Re-Instate python-egenix-mxstack
 Try to Re-Instate python-sqlite
 Try to Re-Instate python-syck
 Try to Re-Instate python-pylibacl
 Try to Re-Instate python-jabber
 Try to Re-Instate python-egenix-mxproxy
 Try to Re-Instate python-xmpp
 Try to Re-Instate python-htmltmpl
 Try to Re-Instate python-reportlab
 Try to Re-Instate python-simpletal
Investigating g++-4.1
Package g++-4.1 has broken dep on libstdc++6-4.1-dev
  Considering libstdc++6-4.1-dev 1 as a solution to g++-4.1 1
  Holding Back g++-4.1 rather than change libstdc++6-4.1-dev
Investigating g++
Package g++ has broken dep on g++-4.1
  Considering g++-4.1 1 as a solution to g++ 0
  Removing g++ rather than change g++-4.1
Done
Starting
Starting 2
Investigating foomatic-filters-ppds
Package foomatic-filters-ppds has broken dep on hplip-ppds
  Considering hplip-ppds 1 as a solution to foomatic-filters-ppds -1
    Reinst Failed because of hplip-ppds
  Removing foomatic-filters-ppds rather than change hplip-ppds
Done
gpgv: Signature made Wed 25 Oct 2006 09:10:29 AM CDT using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Starting
Starting 2
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
Investigating libc6-dev
Package libc6-dev has broken dep on libc6
Investigating dpkg-dev
Package dpkg-dev has broken dep on dpkg
Investigating linux-libc-dev
Package linux-libc-dev has broken dep on linux-kernel-headers
  Considering linux-kernel-headers 2 as a solution to linux-libc-dev 2
  Holding Back linux-libc-dev rather than change linux-kernel-headers
Investigating g++-4.1
Package g++-4.1 has broken dep on gcc-4.1-base
Investigating libstdc++6-4.1-dev
Package libstdc++6-4.1-dev has broken dep on gcc-4.1-base
Investigating g++
Package g++ has broken dep on cpp
 Try to Re-Instate libc6-dev
 Try to Re-Instate dpkg-dev
 Try to Re-Instate g++
Done
Starting
Starting 2
Investigating libglu1-mesa
Package libglu1-mesa has broken dep on libgl1-mesa
  Considering libgl1-mesa 11 as a solution to libglu1-mesa 15
  Added libgl1-mesa to the remove list
Package libglu1-mesa has broken dep on libgl1
  Considering libgl1-mesa 11 as a solution to libglu1-mesa 15
  Added libgl1-mesa to the remove list
  Fixing libglu1-mesa via keep of libgl1-mesa
  Fixing libglu1-mesa via keep of libgl1-mesa
Done
gpgv: Signature made Wed 25 Oct 2006 09:10:29 AM CDT using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Starting
Starting 2
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
Investigating libc6-dev
Package libc6-dev has broken dep on libc6
Investigating dpkg-dev
Package dpkg-dev has broken dep on dpkg
Investigating linux-libc-dev
Package linux-libc-dev has broken dep on linux-kernel-headers
  Considering linux-kernel-headers 2 as a solution to linux-libc-dev 2
  Holding Back linux-libc-dev rather than change linux-kernel-headers
Investigating g++-4.1
Package g++-4.1 has broken dep on gcc-4.1-base
Investigating libstdc++6-4.1-dev
Package libstdc++6-4.1-dev has broken dep on gcc-4.1-base
Investigating g++
Package g++ has broken dep on cpp
 Try to Re-Instate libc6-dev
 Try to Re-Instate dpkg-dev
 Try to Re-Instate g++
Done
Starting
Starting 2
Investigating libglu1-mesa
Package libglu1-mesa has broken dep on libgl1-mesa
  Considering libgl1-mesa 11 as a solution to libglu1-mesa 15
  Added libgl1-mesa to the remove list
Package libglu1-mesa has broken dep on libgl1
  Considering libgl1-mesa 11 as a solution to libglu1-mesa 15
  Added libgl1-mesa to the remove list
  Fixing libglu1-mesa via keep of libgl1-mesa
  Fixing libglu1-mesa via keep of libgl1-mesa
Done
gpgv: Signature made Wed 25 Oct 2006 09:10:29 AM CDT using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Starting
Starting 2
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
Investigating libc6-dev
Package libc6-dev has broken dep on libc6
Investigating dpkg-dev
Package dpkg-dev has broken dep on dpkg
Investigating linux-libc-dev
Package linux-libc-dev has broken dep on linux-kernel-headers
  Considering linux-kernel-headers 2 as a solution to linux-libc-dev 2
  Holding Back linux-libc-dev rather than change linux-kernel-headers
Investigating g++-4.1
Package g++-4.1 has broken dep on gcc-4.1-base
Investigating libstdc++6-4.1-dev
Package libstdc++6-4.1-dev has broken dep on gcc-4.1-base
Investigating g++
Package g++ has broken dep on cpp
 Try to Re-Instate libc6-dev
 Try to Re-Instate dpkg-dev
 Try to Re-Instate g++
Done
Starting
Starting 2
Investigating libglu1-mesa
Package libglu1-mesa has broken dep on libgl1-mesa
  Considering libgl1-mesa 11 as a solution to libglu1-mesa 15
  Added libgl1-mesa to the remove list
Package libglu1-mesa has broken dep on libgl1
  Considering libgl1-mesa 11 as a solution to libglu1-mesa 15
  Added libgl1-mesa to the remove list
  Fixing libglu1-mesa via keep of libgl1-mesa
  Fixing libglu1-mesa via keep of libgl1-mesa
Done
gpgv: Signature made Wed 25 Oct 2006 09:10:29 AM CDT using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Starting
Starting 2
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
WARNING: can't read '/usr/share/update-manager/mirrors.cfg'
Investigating libc6-dev
Package libc6-dev has broken dep on libc6
Investigating dpkg-dev
Package dpkg-dev has broken dep on dpkg
Investigating linux-libc-dev
Package linux-libc-dev has broken dep on linux-kernel-headers
  Considering linux-kernel-headers 2 as a solution to linux-libc-dev 2
  Holding Back linux-libc-dev rather than change linux-kernel-headers
Investigating g++-4.1
Package g++-4.1 has broken dep on gcc-4.1-base
Investigating libstdc++6-4.1-dev
Package libstdc++6-4.1-dev has broken dep on gcc-4.1-base
Investigating g++
Package g++ has broken dep on cpp
 Try to Re-Instate libc6-dev
 Try to Re-Instate dpkg-dev
 Try to Re-Instate g++
Done
Starting
Starting 2
Investigating libglu1-mesa
Package libglu1-mesa has broken dep on libgl1-mesa
  Considering libgl1-mesa 11 as a solution to libglu1-mesa 15
  Added libgl1-mesa to the remove list
Package libglu1-mesa has broken dep on libgl1
  Considering libgl1-mesa 11 as a solution to libglu1-mesa 15
  Added libgl1-mesa to the remove list
  Fixing libglu1-mesa via keep of libgl1-mesa
  Fixing libglu1-mesa via keep of libgl1-mesa
Done
---------------------------------------------------------------------------------------------------------------------------

Thanks in advance.

---

### Post by jrlii on 2007-04-21
It also said to include /var/distupgrade/main.log: -----------------------------------------------------

2007-04-21 11:46:59,934 DEBUG useNetwork: 'False' (selected by user)
2007-04-21 11:46:59,934 DEBUG doUpdate() will not use the network because self.useNetwork==false
2007-04-21 11:47:01,003 DEBUG Foreign: 
2007-04-21 11:47:01,004 DEBUG Obsolete: vim-common libdvdcss2 opera vim flash-plugin fp-linux-ws vim-runtime
2007-04-21 11:47:01,005 DEBUG updateSourcesList()
2007-04-21 11:47:01,051 DEBUG rewriteSourcesList()
2007-04-21 11:47:01,633 DEBUG examining: 'deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted'
2007-04-21 11:47:01,633 DEBUG entry 'deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted' updated to new dist
2007-04-21 11:47:01,633 DEBUG examining: 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted'
2007-04-21 11:47:01,634 DEBUG entry 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted' updated to new dist
2007-04-21 11:47:01,634 DEBUG examining: 'deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted'
2007-04-21 11:47:01,634 DEBUG entry 'deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted' updated to new dist
2007-04-21 11:47:01,634 DEBUG examining: 'deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse'
2007-04-21 11:47:01,634 DEBUG entry 'deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe main restricted multiverse' updated to new dist
2007-04-21 11:47:01,635 DEBUG examining: 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse'
2007-04-21 11:47:01,635 DEBUG entry 'deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse' updated to new dist
2007-04-21 11:47:01,635 DEBUG examining: 'deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse'
2007-04-21 11:47:01,635 DEBUG entry 'deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse' updated to new dist
2007-04-21 11:47:01,635 DEBUG examining: 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted'
2007-04-21 11:47:01,636 DEBUG entry 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted' updated to new dist
2007-04-21 11:47:01,636 DEBUG examining: 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted'
2007-04-21 11:47:01,636 DEBUG entry 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted' updated to new dist
2007-04-21 11:47:01,636 DEBUG examining: 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe'
2007-04-21 11:47:01,636 DEBUG entry 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe' updated to new dist
2007-04-21 11:47:01,645 DEBUG AptCdrom.add() called with '/cdrom'
2007-04-21 11:47:02,012 DEBUG AptCdrom.add() returned: 1
2007-04-21 11:47:02,013 DEBUG doUpdate() will not use the network because self.useNetwork==false
2007-04-21 11:47:02,334 DEBUG Purging 'xorg-common' (Distro PostUpgradePurge rule)
2007-04-21 11:47:02,334 DEBUG Purging 'libgl1-mesa' (Distro PostUpgradePurge rule)
2007-04-21 11:47:02,334 DEBUG running edgyQuirks handler
2007-04-21 11:47:02,335 DEBUG Installing 'python-egenix-mxtexttools' (python2.4->python upgrade rule)
2007-04-21 11:47:02,344 DEBUG Installing 'python-id3lib' (python2.4->python upgrade rule)
2007-04-21 11:47:02,344 DEBUG Installing 'python-imaging' (python2.4->python upgrade rule)
2007-04-21 11:47:02,345 DEBUG Installing 'python-egenix-mxstack' (python2.4->python upgrade rule)
2007-04-21 11:47:02,346 DEBUG Installing 'python-egenix-mxproxy' (python2.4->python upgrade rule)
2007-04-21 11:47:02,346 DEBUG Installing 'python-geoip' (python2.4->python upgrade rule)
2007-04-21 11:47:02,346 DEBUG Installing 'xserver-xorg-input-mouse' (xserver-xorg-input fixup rule)
2007-04-21 11:47:02,347 DEBUG Installing 'python-pam' (python2.4->python upgrade rule)
2007-04-21 11:47:02,347 DEBUG Installing 'python-clientcookie' (python2.4->python upgrade rule)
2007-04-21 11:47:02,348 DEBUG Installing 'xserver-xorg-input-synaptics' (xserver-xorg-input fixup rule)
2007-04-21 11:47:02,348 DEBUG Installing 'python-pyorbit' (python2.4->python upgrade rule)
2007-04-21 11:47:02,349 DEBUG Installing 'python-htmltmpl' (python2.4->python upgrade rule)
2007-04-21 11:47:02,349 DEBUG Installing 'xserver-xorg-input-kbd' (xserver-xorg-input fixup rule)
2007-04-21 11:47:02,349 DEBUG Installing 'python-eunuchs' (python2.4->python upgrade rule)
2007-04-21 11:47:02,349 DEBUG Installing 'python-minimal' (python2.4->python upgrade rule)
2007-04-21 11:47:02,350 DEBUG Installing 'python-gnome2-desktop' (python2.4->python upgrade rule)
2007-04-21 11:47:02,350 DEBUG Installing 'python-egenix-mxtools' (python2.4->python upgrade rule)
2007-04-21 11:47:02,350 DEBUG Installing 'python-simpletal' (python2.4->python upgrade rule)
2007-04-21 11:47:02,351 DEBUG Installing 'xserver-xorg-input-evdev' (xserver-xorg-input fixup rule)
2007-04-21 11:47:02,351 DEBUG Installing 'python-gdbm' (python2.4->python upgrade rule)
2007-04-21 11:47:02,351 DEBUG Installing 'python-mysqldb' (python2.4->python upgrade rule)
2007-04-21 11:47:02,352 DEBUG Installing 'xserver-xorg-input-wacom' (xserver-xorg-input fixup rule)
2007-04-21 11:47:02,352 DEBUG Installing 'python-xml' (python2.4->python upgrade rule)
2007-04-21 11:47:02,353 DEBUG Installing 'python-pexpect' (python2.4->python upgrade rule)
2007-04-21 11:47:02,353 DEBUG Installing 'python-examples' (python2.4->python upgrade rule)
2007-04-21 11:47:02,353 DEBUG Installing 'python-jabber' (python2.4->python upgrade rule)
2007-04-21 11:47:02,353 DEBUG Installing 'python-sqlite' (python2.4->python upgrade rule)
2007-04-21 11:47:02,354 DEBUG Installing 'python-gtk2' (python2.4->python upgrade rule)
2007-04-21 11:47:02,354 DEBUG Installing 'python-apt' (python2.4->python upgrade rule)
2007-04-21 11:47:02,354 DEBUG Installing 'python-pyopenssl' (python2.4->python upgrade rule)
2007-04-21 11:47:02,355 DEBUG Installing 'xserver-xorg-input-all' (xserver-xorg-input fixup rule)
2007-04-21 11:47:02,355 DEBUG Installing 'python-xmpp' (python2.4->python upgrade rule)
2007-04-21 11:47:02,355 DEBUG Installing 'python-gnome2-extras' (python2.4->python upgrade rule)
2007-04-21 11:47:02,356 DEBUG Installing 'xserver-xorg-input-elographics' (xserver-xorg-input fixup rule)
2007-04-21 11:47:02,356 DEBUG Installing 'python-gd' (python2.4->python upgrade rule)
2007-04-21 11:47:02,357 DEBUG Installing 'python-libxml2' (python2.4->python upgrade rule)
2007-04-21 11:47:02,357 DEBUG Installing 'python-gadfly' (python2.4->python upgrade rule)
2007-04-21 11:47:02,358 DEBUG Installing 'python-imaging-sane' (python2.4->python upgrade rule)
2007-04-21 11:47:02,359 DEBUG Installing 'python-numeric' (python2.4->python upgrade rule)
2007-04-21 11:47:02,359 DEBUG Installing 'python-pylibacl' (python2.4->python upgrade rule)
2007-04-21 11:47:02,359 DEBUG Installing 'python-tk' (python2.4->python upgrade rule)
2007-04-21 11:47:02,360 DEBUG Installing 'python-kjbuckets' (python2.4->python upgrade rule)
2007-04-21 11:47:02,360 DEBUG Installing 'python-reportlab' (python2.4->python upgrade rule)
2007-04-21 11:47:02,361 DEBUG Installing 'python-glade2' (python2.4->python upgrade rule)
2007-04-21 11:47:02,361 DEBUG Installing 'python-epydoc' (python2.4->python upgrade rule)
2007-04-21 11:47:02,361 DEBUG Installing 'python-pyxattr' (python2.4->python upgrade rule)
2007-04-21 11:47:02,362 DEBUG Installing 'python-syck' (python2.4->python upgrade rule)
2007-04-21 11:47:02,362 DEBUG Installing 'python-ldap' (python2.4->python upgrade rule)
2007-04-21 11:47:02,363 DEBUG Installing 'python-pgsql' (python2.4->python upgrade rule)
2007-04-21 11:47:02,363 DEBUG Installing 'python-unit' (python2.4->python upgrade rule)
2007-04-21 11:47:02,363 DEBUG Installing 'python-gnome2' (python2.4->python upgrade rule)
2007-04-21 11:47:02,364 DEBUG Installing 'python-soappy' (python2.4->python upgrade rule)
2007-04-21 11:47:02,364 DEBUG Installing 'python-adns' (python2.4->python upgrade rule)
2007-04-21 11:47:02,365 DEBUG Installing 'python-crypto' (python2.4->python upgrade rule)
2007-04-21 11:47:02,365 DEBUG Installing 'python-htmlgen' (python2.4->python upgrade rule)
2007-04-21 11:47:02,365 DEBUG Installing 'hpijs' (hpijs quirk upgrade rule)
2007-04-21 11:47:02,366 DEBUG no {ubuntu,edubuntu,kubuntu}-desktop pkg installed
2007-04-21 11:47:02,366 DEBUG guessing 'ubuntu-desktop' as missing meta-pkg
2007-04-21 11:47:02,368 ERROR not handled expection:
Traceback (most recent call last):

  File "/tmp/tmp.0zwt9T/edgy", line 40, in ?
    app.run()

  File "/tmp/tmp.0zwt9T/DistUpgradeControler.py", line 765, in run
    self.edgyUpgrade()

  File "/tmp/tmp.0zwt9T/DistUpgradeControler.py", line 744, in edgyUpgrade
    if not self.askDistUpgrade():

  File "/tmp/tmp.0zwt9T/DistUpgradeControler.py", line 438, in askDistUpgrade
    if not self.cache.distUpgrade(self._view):

  File "/tmp/tmp.0zwt9T/DistUpgradeCache.py", line 237, in distUpgrade
    if not self._installMetaPkgs(view):

  File "/tmp/tmp.0zwt9T/DistUpgradeCache.py", line 343, in _installMetaPkgs
    self[key].markInstall()

  File "/usr/lib/python2.4/site-packages/apt/cache.py", line 78, in __getitem__
    return self._dict[key]

KeyError: 'ubuntu-desktop'

---

### Post by jrlii on 2007-04-21
Any notions as to what I did wrong? Or were there incompatibilities with the updated packages in Dapper? The last update was yesterday.

Thanks in advance!

---

### Post by jrlii on 2007-04-29
After much poking around and several more tries, I found out you can't upgrade with the desktop disk. You have use the Alternate disk.

---

### Post by zvacet on 2007-04-29
Sorry,just came to the forum.Now you have alternate Cd but I seen that you tryed to use command for upgrade from Cd without qoute.Right command is

```
gksu "sh /cdrom/cdromupgrade" 
```

---

