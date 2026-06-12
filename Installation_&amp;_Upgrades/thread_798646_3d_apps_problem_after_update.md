---
title: "3d apps problem after update"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by threegremlins on 2008-05-18
I've installed hardy and after installing blender, blender works fine. After installing the updates

libgtk2.0-common        install
evolution-common        install
update-manager        install
libgphoto2-port0        install
gnome-desktop-data        install
nautilus        install
gvfs-fuse        install
lshw        install
gnome-settings-daemon        install
update-manager-core        install
libexchange-storage1.2-3        install
util-linux        install
xulrunner-1.9        install
gtk2-engines-pixbuf        install
gnome-control-center        install
libspeex1        install
libcamel1.2-11        install
openssl-blacklist        install
python-virtkey        install
libedata-cal1.2-6        install
libgvfscommon0        install
apport        install
nautilus-data        install
gstreamer0.10-plugins-good        install
libgphoto2-2        install
friendly-recovery        install
util-linux-locales        install
libpanel-applet2-0        install
openssh-client        install
jockey-common        install
gnome-about        install
libhal1        install
gdm        install
hal        install
capplets-data        install
libegroupwise1.2-13        install
bsdutils        install
libgtk2.0-bin        install
sudo        install
libecal1.2-7        install
libgdata1.2-1        install
ssl-cert        install
libhal-storage1        install
gnome-system-monitor        install
python-problem-report        install
libgdata-google1.2-1        install
libebook1.2-9        install
libedataserverui1.2-8        install
libgnome-window-settings1        install
libedata-book1.2-2        install
evolution-data-server        install
libedataserver1.2-9        install
libldap-2.4-2        install
gksu        install
apparmor        install
libglib2.0-0        install
foomatic-filters        install
libssl0.9.8        install
jockey-gtk        install
openssl        install
mount        install
gvfs        install
apparmor-utils        install
gnome-panel        install
xulrunner-1.9-gnome-support        install
gvfs-backends        install
python-apport        install
libnautilus-extension1        install
evolution-data-server-common        install
compiz-fusion-plugins-main        install
apport-gtk        install
transmission-common        install
libgnome-desktop-2        install
libgtk2.0-0        install
transmission-gtk        install
gnome-panel-data        install
ssh-askpass-gnome        install
xserver-xorg-video-intel        install
(this is from Synaptic not the update manager but I believe they are the same)

blender will fire up then disappear and other 3d editing apps like wings3d will not run. When I try to launch blender in a terminal window the final line reads illegal error. 

my box is a SOny Vaio with 1.6 or 8 gig, 512mb of memory and geforce 5500 Nvidia card(which works fine)

---

### Post by meanerelk on 2008-05-18
could you post more of the output from running in a terminal?

---

### Post by threegremlins on 2008-05-18
dave@sanctuary:~$ blender-bin
guessing 'blender-bin' == '/usr/bin/blender-bin'
Compiled with Python version 2.5.2.
Checking for installed Python... got it!
Illegal instruction

I should have thought of this using -d

dave@sanctuary:~$ blender -d
guessing 'blender-bin' == '/usr/bin/blender-bin'
Blender 2.45 (sub 0) Build
argv[0] = blender-bin
argv[1] = -d
Compiled with Python version 2.5.2.
Checking for installed Python... got it!
Color depth r 8 g 8 b 8
Aux buffers: 4
read file 
  Version 242 sub 4
read file /home/dave/.B.blend
  Version 244 sub 0

ordered
 OBLamp
 OBCamera

Registering scripts in Blender menus ...

Getting menu data for scripts from file:
/home/dave/.blender/Bpymenus
dave@sanctuary:~$ blender
guessing 'blender-bin' == '/usr/bin/blender-bin'
Compiled with Python version 2.5.2.
Checking for installed Python... got it!
Illegal instruction
dave@sanctuary:~$
Unable to load: libtiff.
Try setting the BF_TIFF_LIB environment variable if you want this support.
Example: setenv BF_TIFF_LIB /usr/lib/libtiff.so
Color depth r 8 g 8 b 8
Aux buffers: 4
Color depth r 8 g 8 b 8
Aux buffers: 4
Color depth r 8 g 8 b 8
Aux buffers: 4
Illegal instruction

if it's a setenv problem I'll need help with that, like where and in what

---

### Post by threegremlins on 2008-05-21
Anybody?

---

### Post by threegremlins on 2008-05-21
Wednesday

---

### Post by threegremlins on 2008-05-22
To bad there isn't a way to mark this as dead.
I did a server install and installed fluxbox as a desktop and installed all the updates. Blender is working fine, eh. Not a satisfactory remedy, but until I finish my project it will do and maybe by then the problem will be worked out.

---

