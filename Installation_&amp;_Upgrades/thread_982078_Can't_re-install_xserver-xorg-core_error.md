---
title: "Can't re-install xserver-xorg-core: error"
date: 2008-11-14
forum: Installation &amp; Upgrades
---

### Post by jyavenard on 2008-11-14
Hi

I wanted to experiment with an ATI card (to check the new driver) ; previously was running my machine with a nvidia card.

After manually installing the ati drivers; realised on how bad it was so I re-installed the nvidia card ...

Unfortunately, things do go smoothly. Trying to re=install the nvidia drivers always gave me an error about a directory not existing.

So I tried to reinstall xserver-xorg-core ; which gave me the same error.

So I uninstalled xserver-xorg-core and all the xorg packages thinking that it would get easier to re-install after.

Well, I was wrong.

When I try to install manually this package (it also fails via synaptic or apt-get) or fix the packages I get the following error:

avenardj@pcliving:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  xorg-driver-fglrx fglrx-kernel-source fglrx-amdcccle
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  xorg-driver-fglrx xserver-xorg-core
Suggested packages:
  libamdxvba1 xfonts-100dpi xfonts-75dpi xfonts-scalable
The following NEW packages will be installed:
  xorg-driver-fglrx xserver-xorg-core
0 upgraded, 2 newly installed, 0 to remove and 2 not upgraded.
39 not fully installed or removed.
Need to get 0B/19.9MB of archives.
After this operation, 61.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 106100 files and directories currently installed.)
Unpacking xserver-xorg-core (from .../xserver-xorg-core_2%3a1.5.2-2ubuntu3_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/xserver-xorg-core_2%3a1.5.2-2ubuntu3_amd64.deb (--unpack):
 unable to create `./usr/lib/xorg/modules/extensions/libglx.so': No such file or directory
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking xorg-driver-fglrx (from .../xorg-driver-fglrx_2%3a8.543-0ubuntu4_amd64.deb) ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/lib/libGL.so.1 by xorg-driver-fglrx'
  found `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-177'
dpkg: error processing /var/cache/apt/archives/xorg-driver-fglrx_2%3a8.543-0ubuntu4_amd64.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/xserver-xorg-core_2%3a1.5.2-2ubuntu3_amd64.deb
 /var/cache/apt/archives/xorg-driver-fglrx_2%3a8.543-0ubuntu4_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

No matter how I try to install a xorg package, I always get this error:
 unable to create `./usr/lib/xorg/modules/extensions/libglx.so': No such file or directory

Any ideas?

I'm close to re-installing the whole system, which will take me several hours to reconfigure :(

Thanks in advance
JY

---

### Post by cdtech on 2008-11-14
What do you get with:
```
sudo dpkg --audit
```

---

### Post by jyavenard on 2008-11-14
root@pcliving:/usr/lib/xorg/modules/drivers# sudo dpkg --audit
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 xserver-xorg-input-vmmouse X.Org X server -- VMMouse input driver to use with 
 xserver-xorg-video-v4l X.Org X server -- Video 4 Linux display driver
 xserver-xorg-video-sis X.Org X server -- SiS display driver
 xserver-xorg-video-apm X.Org X server -- APM display driver
 xserver-xorg-video-voodoo X.Org X server -- Voodoo display driver
 xserver-xorg-video-s3virge X.Org X server -- S3 ViRGE display driver
 xserver-xorg-video-openchrome X.Org X server -- VIA display driver
 xserver-xorg-video-vmware X.Org X server -- VMware display driver
 xserver-xorg-input-wacom X.Org X server -- Wacom input driver
 xserver-xorg-video-radeon X.Org X server -- ATI Radeon display driver
 xserver-xorg-video-savage X.Org X server -- Savage display driver
 xserver-xorg-video-fbdev X.Org X server -- fbdev display driver
 xserver-xorg-input-evdev X.Org X server -- evdev input driver
 xserver-xorg         the X.Org X server
 xserver-xorg-video-all the X.Org X server -- output driver metapackage
 xserver-xorg-input-synaptics Synaptics TouchPad driver for X.Org/XFree86 serve
 xserver-xorg-video-vesa X.Org X server -- VESA display driver
 xserver-xorg-video-rendition X.Org X server -- Rendition display driver
 xserver-xorg-video-sisusb X.Org X server -- SiS USB display driver
 xserver-xorg-video-tdfx X.Org X server -- tdfx display driver
 xserver-xorg-video-ark X.Org X server -- ark display driver
 xserver-xorg-video-cirrus X.Org X server -- Cirrus display driver
 xserver-xorg-video-r128 X.Org X server -- ATI r128 display driver
 xserver-xorg-video-neomagic X.Org X server -- Neomagic display driver
 xserver-xorg-video-mga X.Org X server -- MGA display driver
 xserver-xorg-video-i128 X.Org X server -- i128 display driver
 xserver-xorg-video-s3 X.Org X server -- legacy S3 display driver
 xserver-xorg-video-trident X.Org X server -- Trident display driver
 xserver-xorg-video-chips X.Org X server -- Chips display driver
 xserver-xorg-video-intel X.Org X server -- Intel i8xx, i9xx display driver
 xserver-xorg-video-mach64 X.Org X server -- ATI Mach64 display driver
 xserver-xorg-input-all the X.Org X server -- input driver metapackage
 xserver-xorg-input-mouse X.Org X server -- mouse input driver
 xserver-xorg-video-nv X.Org X server -- NV display driver
 xserver-xorg-input-kbd X.Org X server -- keyboard input driver
 xserver-xorg-video-ati X.Org X server -- ATI display driver wrapper
 xserver-xorg-video-siliconmotion X.Org X server -- SiliconMotion display drive
 xserver-xorg-video-tseng X.Org X server -- Tseng display driver

---

### Post by cdtech on 2008-11-14
Try running:
```
sudo dpkg --configure -a && sudo apt-get -f install
```

---

### Post by jyavenard on 2008-11-14
Thanks for taking the time to helping me out:

No much luck still ( I had tried this earlier)

```

root@pcliving:~# dpkg --configure -a
dpkg: dependency problems prevent configuration of xserver-xorg-input-vmmouse:
 xserver-xorg-input-vmmouse depends on xserver-xorg-core (>= 2:1.5.1-1ubuntu3); however:
  Package xserver-xorg-core is not installed.
dpkg: error processing xserver-xorg-input-vmmouse (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-v4l:
 xserver-xorg-video-v4l depends on xserver-xorg-core (>= 2:1.4.99.906-2ubuntu2); however:
  Package xserver-xorg-core is not installed.
dpkg: error processing xserver-xorg-video-v4l (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-sis:
 xserver-xorg-video-sis depends on xserver-xorg-core (>= 2:1.4.99.906-2ubuntu2); however:
  Package xserver-xorg-core is not installed.
dpkg: error processing xserver-xorg-video-sis (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-apm:
 xserver-xorg-video-apm depends on xserver-xorg-core (>= 2:1.4.99.906-2ubuntu2); however:
  Package xserver-xorg-core is not installed.
dpkg: error processing xserver-xorg-video-apm (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-voodoo:
 xserver-xorg-video-voodoo depends on xserver-xorg-core (>= 2:1.4.99.906-2ubuntu2); however:
  Package xserver-xorg-core is not installed.
dpkg: error processing xserver-xorg-video-voodoo (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-s3virge:
 xserver-xorg-video-s3virge depends on xserver-xorg-core (>= 2:1.4.99.906-2ubuntu2); however:
  Package xserver-xorg-core is not installed.
dpkg: error processing xserver-xorg-video-s3virge (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-openchrome:
 xserver-xorg-video-openchrome depends on xserver-xorg-core (>= 2:1.5.1-1ubuntu3); however:
  Package xserver-xorg-core is not installed.
dpkg: error processing xserver-xorg-video-openchrome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-vmware:
 xserver-xorg-video-vmware depends on xserver-xorg-core (>= 2:1.4.99.906-2ubuntu2); however:
  Package xserver-xorg-core is not installed.
dpkg: error processing xserver-xorg-video-vmware (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-input-wacom:
 xserver-xorg-input-wacom depends on xserver-xorg-core (>= 2:1.5.1-1ubuntu3); however:
  Package xserver-xorg-core is not installed.
dpkg: error processing xserver-xorg-input-wacom (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-radeon:
 xserver-xorg-video-radeon depends on xserver-xorg-core (>= 2:1.4.99.906-2ubuntu2); however:
  Package xserver-xorg-core is not installed.
dpkg: error processing xserver-xorg-video-radeon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-savage:
 xserver-xorg-video-savage depends on xserver-xorg-core (>= 2:1.4.99.906-2ubuntu2); however:
  Package xserver-xorg-core is not installed.
dpkg: error processing xserver-xorg-video-savage (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-fbdev:
 xserver-xorg-video-fbdev depends on xserver-xorg-core (>= 2:1.4.99.906-2ubuntu2); however:
  Package xserver-xorg-core is not installed.
dpkg: error processing xserver-xorg-video-fbdev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-input-evdev:
 xserver-xorg-input-evdev depends on xserver-xorg-core (>= 2:1.5.1-1ubuntu3); however:
  Package xserver-xorg-core is not installed.
dpkg: error processing xserver-xorg-input-evdev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg:
 xserver-xorg depends on xserver-xorg-core (>= 2:1.5); however:
  Package xserver-xorg-core is not installed.
 xserver-xorg depends on xserver-xorg-input-evdev; however:
  Package xserver-xorg-input-evdev is not configured yet.
dpkg: error processing xserver-xorg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-all:
 xserver-xorg-video-all depends on xserver-xorg-video-apm; however:
  Package xserver-xorg-video-apm is not configured yet.
 xserver-xorg-video-all depends on xserver-xorg-video-fbdev; however:
  Package xserver-xorg-video-fbdev is not configured yet.
 xserver-xorg-video-all depends on xserver-xorg-video-s3virge; however:
  Package xserver-xorg-video-s3virge is not configured yet.
 xserver-xorg-video-all depends on xserver-xorg-video-savage; however:
  Package xserver-xorg-video-savage is not configured yet.
 xserver-xorg-video-all depends on xserver-xorg-video-sis; however:
  Package xserver-xorg-video-sis is not configured yet.
 xserver-xorg-video-all depends on xserver-xorg-video-openchrome; however:
  Package xserver-xorg-video-openchrome is not configured yet.
 xserver-xorg-video-all depends on xserver-xorg-video-voodoo; however:
  Package xserver-xorg-video-voodoo is not configured yet.
 xserver-xorg-video-all depends on xserver-xorg-video-v4l; however:
  Package xserver-xorg-video-v4l is not configured yet.
 xserver-xorg-video-all depends on xserver-xorg-video-vmware; however:
  Package xserver-xorg-video-vmware is not configured yet.
dpkg: error processing xserver-xorg-video-all (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-input-synaptics:
 xserver-xorg-input-synaptics depends on xserver-xorg-core (>= 2:1.5.1-1ubuntu3); however:
  Package xserver-xorg-core is not installed.
dpkg: error processing xserver-xorg-input-synaptics (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-vesa:
 xserver-xorg-video-vesa depends on xserver-xorg-core (>= 2:1.4.99.906-2ubuntu2); however:
  Package xserver-xorg-core is not installed.
dpkg: error processing xserver-xorg-video-vesa (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-rendition:
 xserver-xorg-video-rendition depends on xserver-xorg-core (>= 2:1.4.99.906-2ubuntu2); however:
  Package xserver-xorg-core is not installed.
dpkg: error processing xserver-xorg-video-rendition (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-sisusb:
 xserver-xorg-video-sisusb depends on xserver-xorg-core (>= 2:1.4.99.906-2ubuntu2); however:
  Package xserver-xorg-core is not installed.
dpkg: error processing xserver-xorg-video-sisusb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-tdfx:
 xserver-xorg-video-tdfx depends on xserver-xorg-core (>= 2:1.4.99.906-2ubuntu2); however:
  Package xserver-xorg-core is not installed.
dpkg: error processing xserver-xorg-video-tdfx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-ark:
 xserver-xorg-video-ark depends on xserver-xorg-core (>= 2:1.4.99.906-2ubuntu2); however:
  Package xserver-xorg-core is not installed.
dpkg: error processing xserver-xorg-video-ark (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-cirrus:
 xserver-xorg-video-cirrus depends on xserver-xorg-core (>= 2:1.4.99.906-2ubuntu2); however:
  Package xserver-xorg-core is not installed.
dpkg: error processing xserver-xorg-video-cirrus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-r128:
 xserver-xorg-video-r128 depends on xserver-xorg-core (>= 2:1.4.99.906-2ubuntu2); however:
  Package xserver-xorg-core is not installed.
dpkg: error processing xserver-xorg-video-r128 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-neomagic:
 xserver-xorg-video-neomagic depends on xserver-xorg-core (>= 2:1.4.99.906-2ubuntu2); however:
  Package xserver-xorg-core is not installed.
dpkg: error processing xserver-xorg-video-neomagic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-mga:
 xserver-xorg-video-mga depends on xserver-xorg-core (>= 2:1.4.99.906-2ubuntu2); however:
  Package xserver-xorg-core is not installed.
dpkg: error processing xserver-xorg-video-mga (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-i128:
 xserver-xorg-video-i128 depends on xserver-xorg-core (>= 2:1.4.99.906-2ubuntu2); however:
  Package xserver-xorg-core is not installed.
dpkg: error processing xserver-xorg-video-i128 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-s3:
 xserver-xorg-video-s3 depends on xserver-xorg-core (>= 2:1.4.99.906-2ubuntu2); however:
  Package xserver-xorg-core is not installed.
dpkg: error processing xserver-xorg-video-s3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-trident:
 xserver-xorg-video-trident depends on xserver-xorg-core (>= 2:1.4.99.906-2ubuntu2); however:
  Package xserver-xorg-core is not installed.
dpkg: error processing xserver-xorg-video-trident (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-chips:
 xserver-xorg-video-chips depends on xserver-xorg-core (>= 2:1.4.99.906-2ubuntu2); however:
  Package xserver-xorg-core is not installed.
dpkg: error processing xserver-xorg-video-chips (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-intel:
 xserver-xorg-video-intel depends on xserver-xorg-core (>= 2:1.5.1-1ubuntu3); however:
  Package xserver-xorg-core is not installed.
dpkg: error processing xserver-xorg-video-intel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-mach64:
 xserver-xorg-video-mach64 depends on xserver-xorg-core (>= 2:1.4.99.906-2ubuntu2); however:
  Package xserver-xorg-core is not installed.
dpkg: error processing xserver-xorg-video-mach64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-input-all:
 xserver-xorg-input-all depends on xserver-xorg-input-evdev; however:
  Package xserver-xorg-input-evdev is not configured yet.
 xserver-xorg-input-all depends on xserver-xorg-input-synaptics; however:
  Package xserver-xorg-input-synaptics is not configured yet.
 xserver-xorg-input-all depends on xserver-xorg-input-vmmouse; however:
  Package xserver-xorg-input-vmmouse is not configured yet.
 xserver-xorg-input-all depends on xserver-xorg-input-wacom; however:
  Package xserver-xorg-input-wacom is not configured yet.
dpkg: error processing xserver-xorg-input-all (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-input-mouse:
 xserver-xorg-input-mouse depends on xserver-xorg-core (>= 2:1.4.99.905); however:
  Package xserver-xorg-core is not installed.
dpkg: error processing xserver-xorg-input-mouse (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-nv:
 xserver-xorg-video-nv depends on xserver-xorg-core (>= 2:1.4.99.906-2ubuntu2); however:
  Package xserver-xorg-core is not installed.
dpkg: error processing xserver-xorg-video-nv (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-input-kbd:
 xserver-xorg-input-kbd depends on xserver-xorg-core (>= 2:1.4.99.905); however:
  Package xserver-xorg-core is not installed.
dpkg: error processing xserver-xorg-input-kbd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-ati:
 xserver-xorg-video-ati depends on xserver-xorg-core (>= 2:1.4.99.906-2ubuntu2); however:
  Package xserver-xorg-core is not installed.
 xserver-xorg-video-ati depends on xserver-xorg-video-r128; however:
  Package xserver-xorg-video-r128 is not configured yet.
 xserver-xorg-video-ati depends on xserver-xorg-video-mach64; however:
  Package xserver-xorg-video-mach64 is not configured yet.
 xserver-xorg-video-ati depends on xserver-xorg-video-radeon; however:
  Package xserver-xorg-video-radeon is not configured yet.
dpkg: error processing xserver-xorg-video-ati (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-siliconmotion:
 xserver-xorg-video-siliconmotion depends on xserver-xorg-core (>= 2:1.4.99.906-2ubuntu2); however:
  Package xserver-xorg-core is not installed.
dpkg: error processing xserver-xorg-video-siliconmotion (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-tseng:
 xserver-xorg-video-tseng depends on xserver-xorg-core (>= 2:1.4.99.906-2ubuntu2); however:
  Package xserver-xorg-core is not installed.
dpkg: error processing xserver-xorg-video-tseng (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xserver-xorg-input-vmmouse
 xserver-xorg-video-v4l
 xserver-xorg-video-sis
 xserver-xorg-video-apm
 xserver-xorg-video-voodoo
 xserver-xorg-video-s3virge
 xserver-xorg-video-openchrome
 xserver-xorg-video-vmware
 xserver-xorg-input-wacom
 xserver-xorg-video-radeon
 xserver-xorg-video-savage
 xserver-xorg-video-fbdev
 xserver-xorg-input-evdev
 xserver-xorg
[snip]
root@pcliving:~# 

```

and:
```

root@pcliving:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  x11-apps libavahi-qt3-1 libarts1c2a xserver-xorg-video-all
  nvidia-177-kernel-source xserver-xorg-video-apm xserver-xorg-video-ark
  xserver-xorg-video-ati xfonts-scalable xserver-xorg-video-openchrome fvwm1
  xserver-xorg-video-s3virge xserver-xorg-video-v4l mdetect
  xserver-xorg-video-mga xserver-xorg-video-chips xserver-xorg-core
  xserver-xorg-video-mach64 libgl1-mesa-dri xserver-xorg-video-trident
  ubuntu-sounds xserver-xorg-video-sis mythbuntu-gdm-theme liblualib50
  xfdesktop4-data xserver-xorg-video-siliconmotion xserver-xorg-input-vmmouse
  xserver-xorg-video-savage xserver-xorg-video-tdfx x11-session-utils toshset
  xserver-xorg-video-intel libdmx1 xserver-xorg-input-all acpid finger
  xserver-xorg-video-vmware xserver-xorg-video-r128 xfonts-base
  xserver-xorg-input-evdev xserver-xorg-video-vesa x11-xfs-utils
  xserver-xorg-input-kbd alsa-utils xserver-xorg-video-s3 ubuntu-gdm-themes
  xserver-xorg libxtrap6 xserver-xorg-video-nv xfonts-100dpi
  xserver-xorg-video-voodoo xserver-xorg-video-fbdev xserver-xorg-input-wacom
  xinit laptop-mode-tools libfs6 xserver-xorg-video-neomagic
  xserver-xorg-input-mouse smartdimmer alsa-base xserver-xorg-video-sisusb
  kdelibs-data xserver-xorg-video-tseng xserver-xorg-video-radeon liblua50
  xserver-xorg-video-cirrus xserver-xorg-input-synaptics linux-sound-base
  xserver-xorg-video-rendition xserver-xorg-video-i128
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  xserver-xorg-core
The following NEW packages will be installed:
  xserver-xorg-core
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
38 not fully installed or removed.
Need to get 0B/2641kB of archives.
After this operation, 5915kB of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 105882 files and directories currently installed.)
Unpacking xserver-xorg-core (from .../xserver-xorg-core_2%3a1.5.2-2ubuntu3_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/xserver-xorg-core_2%3a1.5.2-2ubuntu3_amd64.deb (--unpack):
 unable to create `./usr/lib/xorg/modules/extensions/libglx.so': No such file or directory
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/xserver-xorg-core_2%3a1.5.2-2ubuntu3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by cdtech on 2008-11-14
Ok, one more:
```
dpkg-divert --list
```

---

### Post by jyavenard on 2008-11-14
Ok, I've manually remove all the xserver-xorg-* module
sudo dpkg --audit
now returns nothing..

```

root@pcliving:~# dpkg-divert --list
diversion of /bin/sh to /bin/sh.distrib by dash
diversion of /usr/share/man/man1/sh.1.gz to /usr/share/man/man1/sh.distrib.1.gz by dash
diversion of /usr/share/dict/words to /usr/share/dict/words.pre-dictionaries-common by dictionaries-common
diversion of /usr/share/mythtv/util_menu.xml to /usr/share/mythtv/util_menu.xml.diverted by mythbuntu-log-grabber
diversion of /usr/share/mythtv/main_settings.xml to /usr/share/mythtv/main_settings.xml.diverted by mythbuntu-control-centre
diversion of /usr/share/mythtv/info_menu.xml to /usr/share/mythtv/info_menu.xml.diverted by mythbuntu-apple-trailers
diversion of /usr/lib/xorg/modules/extensions/libglx.so to /usr/lib/fglrx/libglx.so.xlibmesa by xorg-driver-fglrx
diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-177
diversion of /usr/lib/libGL.so.1.2 to /usr/lib/nvidia/libGL.so.1.2.xlibmesa by nvidia-glx-177
diversion of /usr/lib32/libGL.so to /usr/lib32/nvidia/libGL.so.xlibmesa by nvidia-glx-177
diversion of /usr/lib32/libGL.so.1 to /usr/lib32/nvidia/libGL.so.1.xlibmesa by nvidia-glx-177
diversion of /usr/lib32/libGL.so.1.2 to /usr/lib32/nvidia/libGL.so.1.2.xlibmesa by nvidia-glx-177
diversion of /usr/lib/xorg/modules/extensions/libGLcore.so to /usr/lib/nvidia/libGLcore.so.xlibmesa by nvidia-glx-177

```

---

### Post by jyavenard on 2008-11-14
Ah Ah!
You showed me what was wrong here:
after reading the man page I did:
dpkg-divert --remove /usr/lib/xorg/modules/extensions/libglx.so 

And now xserver-xorg-core properly installed !

Thanks

I'm very new to ubuntu and deb stuff, a redhat user of 10 years here ...

---

### Post by cdtech on 2008-11-14
Ok, now try running this command on one line:
```
sudo dpkg --configure -a && sudo apt-get -f install
```

Lets see what you get now. You may need to manually remove the divert, we'll see.

---

### Post by cdtech on 2008-11-14
congrats..........:guitar:

---

### Post by jyavenard on 2008-11-14
Thanks again.

I have pretty much re-installed everything now...

However, the fonts are now incredible tiny ; all the menus etc are completely unreadable :(

---

### Post by cdtech on 2008-11-14
Have you looked in the System > Preferences > Appearance and select the tab "fonts"

---

### Post by jyavenard on 2008-11-14
> **cdtech said:**
> Have you looked in the System > Preferences > Appearance and select the tab "fonts"

That's provided I could actually read the label of the menus :)

Edit: Restored gdm configuration I had saved earlier today, all good...

---

### Post by impert on 2009-08-18
Just want to say thanks to both of you - you solved a problem for me. I had a couple of diversions left on my machine after removing - completely as I thought - fglrx. They stopped me from upgrading mesa.

No thanks to fglrx, though.

---

