---
title: "Keep update manager from uninstalling applications"
date: 2013-01-30
forum: Installation &amp; Upgrades
---

### Post by flyingfisch on 2013-01-30
About a month ago update manager uninstalled a bunch of stuff while updating and today it decided that i didn't need x11 anymore... :confused:

Is there a way to get it to simply install stuff and not remove without asking?

---

### Post by ibjsb4 on 2013-01-30
The term stuff and x11 covers a lot of territory.  Could you instead show us whats being installed and removed.

---

### Post by flyingfisch on 2013-01-30
sure.

Today it was all the x drivers, which I reinstalled by running

```

sudo apt-get install xserver-xorg

```

The last time it happened it was a lot of unrelated stuff, including xfce, unity, FlightGear, SuperTuxCart (those two might have been removed because playdeb is down? idk), lxde, firefox, thunderbird, gdebi package installer, I don't remember the rest....

---

### Post by flyingfisch on 2013-01-31
bump.

---

### Post by Cheesehead on 2013-01-31
Insufficient data.

To help you, we need the complete terminal log of a session where this mass-removal occurred. Look in /var/log/apt for the term.log files, and attach one that shows a mass-removal event.

---

### Post by flyingfisch on 2013-01-31
Does this help?

```

Start-Date: 2013-01-29  19:28:09
Commandline: aptdaemon role='role-commit-packages' sender=':1.714'
Upgrade: initramfs-tools-bin:i386 (0.99ubuntu13, 0.99ubuntu13.1), initramfs-tools:i386 (0.99ubuntu13, 0.99ubuntu13.1)
End-Date: 2013-01-29  19:29:26

Start-Date: 2013-01-30  08:22:42
Install: xserver-xorg-video-cirrus-lts-quantal:i386 (1.5.1-0ubuntu2~precise1), xserver-xorg-core-lts-quantal:i386 (1.13.0-0ubuntu6.1~precise2), libdrm-nouveau2:i386 (2.4.39-0ubuntu0.1), xserver-common-lts-quantal:i386 (1.13.0-0ubuntu6.1~precise2)
Remove: xserver-xorg:i386 (7.6+12ubuntu2), xserver-xorg-input-evdev:i386 (2.7.0-0ubuntu1.2), xserver-xorg-video-all:i386 (7.6+12ubuntu2), xserver-xorg-video-ati:i386 (6.14.99~really6.14.6~glasen~ppa4), xserver-xorg-video-tdfx:i386 (1.4.3-4build2), xserver-xorg-video-trident:i386 (1.3.4-2build2), xserver-xorg-video-fbdev:i386 (0.4.2-4ubuntu2), xserver-xorg-input-wacom:i386 (0.14.0-0ubuntu2.1), xserver-xorg-video-mga:i386 (1.4.13.dfsg-4build2), xserver-xorg-input-vmmouse:i386 (12.9.0-0ubuntu0.1), xserver-xorg-input-mouse:i386 (1.7.1-1build3), xserver-xorg-video-r128:i386 (6.8.1-5build2), libxatracker1:i386 (9.0.2~glasen~ppa1), xserver-xorg-video-openchrome:i386 (0.2.904+svn1050-1), ubuntu-desktop:i386 (1.267.1), xserver-xorg-video-vesa:i386 (2.3.0-7build2), xserver-xorg-video-siliconmotion:i386 (1.7.5-1build2), xserver-xorg-video-mach64:i386 (6.9.0-1build2), xserver-xorg-video-sis:i386 (0.10.3-3build2), xserver-xorg-video-qxl:i386 (0.0.16-2), xserver-xorg-video-s3:i386 (0.6.3-4build2), xserver-xorg-core:i386 (1.11.4-0ubuntu10.8), kubuntu-desktop:i386 (1.254), xserver-xorg-video-savage:i386 (2.3.3-1ubuntu1), xserver-xorg-input-all:i386 (7.6+12ubuntu2), xserver-xorg-video-nouveau:i386 (1.1.0~glasen~ppa4.1), xserver-xorg-video-vmware:i386 (12.0.1-1ubuntu1.1), xubuntu-desktop:i386 (2.152), xserver-xorg-video-neomagic:i386 (1.2.5-2build2), libgl1-mesa-dri:i386 (9.0.2~glasen~ppa1), xserver-xorg-video-geode:i386 (2.11.13-2build1), xorg:i386 (7.6+12ubuntu2), xserver-xorg-input-synaptics:i386 (1.6.2-1ubuntu1~precise2), xserver-xorg-video-sisusb:i386 (0.9.4-2build2), xserver-xorg-video-radeon:i386 (6.14.99~really6.14.6~glasen~ppa4), xserver-xorg-video-cirrus:i386 (1.3.2-4build1), xserver-xorg-video-intel:i386 (2.20.19~precise~ppa1.1)
Error: Sub-process /usr/bin/dpkg returned an error code (1)
End-Date: 2013-01-30  08:23:45

```

EDIT:

also found this:

```

Start-Date: 2013-01-03  15:15:21
Commandline: aptdaemon role='role-commit-packages' sender=':1.80'
Upgrade: nautilus:i386 (3.4.2-0ubuntu5, 3.4.2-0ubuntu6), libdecoration0:i386 (0.9.7.8+bzr3121-0ubuntu1, 0.9.7.12-0ubuntu1), nautilus-data:i386 (3.4.2-0ubuntu5, 3.4.2-0ubuntu6), gir1.2-nautilus-3.0:i386 (3.4.2-0ubuntu5, 3.4.2-0ubuntu6), compiz-plugins-default:i386 (0.9.7.8+bzr3121-0ubuntu1, 0.9.7.12-0ubuntu1), compiz-plugins:i386 (0.9.7.8+bzr3121-0ubuntu1, 0.9.7.12-0ubuntu1), unattended-upgrades:i386 (0.76, 0.76ubuntu1), libdecoration0-dev:i386 (0.9.7.8+bzr3121-0ubuntu1, 0.9.7.12-0ubuntu1), libnautilus-extension1a:i386 (3.4.2-0ubuntu5, 3.4.2-0ubuntu6), compiz:i386 (0.9.7.8+bzr3121-0ubuntu1, 0.9.7.12-0ubuntu1), compiz-core:i386 (0.9.7.8+bzr3121-0ubuntu1, 0.9.7.12-0ubuntu1), compiz-gnome:i386 (0.9.7.8+bzr3121-0ubuntu1, 0.9.7.12-0ubuntu1)
End-Date: 2013-01-03  15:17:42

Start-Date: 2013-01-03  19:23:08
Commandline: aptdaemon role='role-remove-packages' sender=':1.174'
Install: plasma-active-imageviewer:i386 (2.0+git2012021101-0ubuntu4~ppa3, automatic), plasma-active-mobilecomponents:i386 (2.0+git2012021101-0ubuntu4~ppa3, automatic), libqt4-declarative-gestures:i386 (4.8.1-0ubuntu4.3, automatic), libqtmultimediakit1:i386 (1.2.0-1ubuntu2, automatic), plasma-widgets-active:i386 (2.0+git2012021101-0ubuntu4~ppa3, automatic), share-like-connect-data:i386 (2.0+git2012021101-0ubuntu1, automatic), kde-artwork-active:i386 (1.0+svn2012022702-0ubuntu1, automatic), startactive-ksplash-theme:i386 (2.0+git2012030201-0ubuntu2, automatic), plasma-active-settings:i386 (2.0+git2012021101-0ubuntu4~ppa3, automatic), libavformat-extra-53:i386 (0.8.4ubuntu0.12.04.1, automatic), share-like-connect:i386 (2.0+git2012021101-0ubuntu1, automatic), libdeclarative-multimedia:i386 (1.2.0-1ubuntu2, automatic), plasma-active-data:i386 (2.0+git2012021101-0ubuntu4~ppa3, automatic), plasma-active-webbrowser:i386 (2.0+git2012021101-0ubuntu4~ppa3, automatic), startactive-data:i386 (2.0+git2012030201-0ubuntu2, automatic)
Remove: menu-xdg:i386 (0.5), plasma-dataengines-workspace:i386 (4.8.5-0ubuntu0.2), mate-applets-common:i386 (1.4.0-1+precise), plexydesk:i386 (0.6.6-1133~201211220850~precise1), plasma-netbook:i386 (4.8.5-0ubuntu0.2), libopencv-highgui2.3:i386 (2.3.1-7), mate-settings-daemon-gstreamer:i386 (1.4.0-2+precise), libmtp9:i386 (1.1.5-1~eugenesan~precise2), mate-panel:i386 (1.4.0-1+precise), mate-desktop-environment:i386 (1.4.0+precise), eom-common:i386 (1.4.0-1+precise), libmatecomponent:i386 (1.4.0-1+precise), engrampa-common:i386 (1.4.1-1+precise), libdc1394-22:i386 (2.2.0-2), mate-system-tools:i386 (1.4.0-1+precise), usbmuxd:i386 (1.0.7-2), bluefish:i386 (2.2.2-1), hedgewars-data:i386 (0.9.18-1~getdeb2), python-mate:i386 (1.4.0-1+precise), ubuntu-standard:i386 (1.267), libmatemenu:i386 (1.4.0-1+precise), mozo:i386 (1.4.0-1+precise), upower:i386 (0.9.15-3git1), gnome-power-manager:i386 (3.4.0-0ubuntu1.1), gecko-mediaplayer:i386 (1.0.4-2ubuntu1), libopencv-imgproc2.3:i386 (2.3.1-7), plasma-widgets-workspace:i386 (4.8.5-0ubuntu0.2), kde-workspace:i386 (4.8.5-0ubuntu0.2), mate-text-editor:i386 (1.4.0-1+precise), bluez-cups:i386 (4.98-2ubuntu7), fgrun:i386 (1.6.2-1~getdeb1), mate-settings-daemon-common:i386 (1.4.0-2+precise), libgmtk0:i386 (1.0.5-1), mate-sensors-applet:i386 (1.2.0-3+precise), libav-tools:i386 (0.8.4-0ubuntu0.12.04.1), printer-driver-postscript-hp:i386 (3.12.2-1ubuntu3.1), hplip:i386 (3.12.2-1ubuntu3.1), libgps20:i386 (3.4-2), mate-media:i386 (1.4.0-1+precise), mate-backgrounds:i386 (1.4.0-1+precise), ubuntu-desktop:i386 (1.267), python-mate-desktop:i386 (1.4.0-1+precise), printer-driver-gutenprint:i386 (5.2.8~pre1-0ubuntu2.1), libmatepanelapplet:i386 (1.4.0-1+precise), libmate-common:i386 (1.4.0-1+precise), libusb-1.0-0:i386 (1.0.9~rc3-2ubuntu1), ffmpegthumbnailer-caja:i386 (1.4.0-1+precise), libgpod4:i386 (0.8.2-4), caja:i386 (1.4.0-1+precise), wallch:i386 (3.01-0ubuntu1), libavformat53:i386 (0.8.4-0ubuntu0.12.04.1), simgear2.8.0:i386 (2.8.0-1~getdeb1), kubuntu-desktop:i386 (1.254), mate-system-monitor:i386 (1.4.0-2+precise), bluefish-plugins:i386 (2.2.2-1), mate-power-manager:i386 (1.4.0-1+precise), mate-panel-common:i386 (1.4.0-1+precise), bluefish-data:i386 (2.2.2-1), mate-media-gstreamer:i386 (1.4.0-1+precise), mate-menus:i386 (1.4.0-1+precise), libopenscenegraph80:i386 (3.0.1-2), libmatedesktop:i386 (1.4.2-1+precise), mate-power-manager-common:i386 (1.4.0-1+precise), hedgewars:i386 (0.9.18-1~getdeb2), mate-desktop-common:i386 (1.4.2-1+precise), libfltk1.1:i386 (1.1.10-10), eom:i386 (1.4.0-1+precise), mate-desktop:i386 (1.4.2-1+precise), flightgear:i386 (2.8.0-1~getdeb1), mate-applets:i386 (1.4.0-1+precise), gnome-session-fallback:i386 (3.2.1-0ubuntu8), gnome-session-bin:i386 (3.2.1-0ubuntu8), engrampa:i386 (1.4.1-1+precise), amarok:i386 (2.5.0-0ubuntu6), libopencv-core2.3:i386 (2.3.1-7), gnome-mplayer:i386 (1.0.5-1), libimobiledevice2:i386 (1.1.1-4), ffmpeg:i386 (0.8.4-0ubuntu0.12.04.1), mate-calc:i386 (1.4.0-1+precise), cups:i386 (1.5.3-0ubuntu6), mate-media-common:i386 (1.4.0-1+precise), mate-settings-daemon:i386 (1.4.0-2+precise), hddtemp:i386 (0.3-beta15-51), mate-utils:i386 (1.4.0-1+precise), libmtp-runtime:i386 (1.1.5-1~eugenesan~precise2), mate-control-center:i386 (1.4.0-1+precise), caja-common:i386 (1.4.0-1+precise), nautilus-share:i386 (0.7.3-1ubuntu2), gstreamer0.10-plugins-bad:i386 (0.10.22.3-2ubuntu2.1), printer-driver-hpcups:i386 (3.12.2-1ubuntu3.1), libgpod-common:i386 (0.8.2-4), rhythmbox-plugins:i386 (2.96-0ubuntu4.2), mate-netspeed:i386 (1.4.0-1+precise), plasma-widgets-addons:i386 (4.8.5-0ubuntu0.1), xfce4-power-manager:i386 (1.0.11-0ubuntu2), libgmtk0-data:i386 (1.0.5-1), mate-user-share:i386 (1.4.1-1+precise), blender:i386 (2.62-1), usbutils:i386 (005-1), libusb-1.0-0-dev:i386 (1.0.9~rc3-2ubuntu1), libmateui:i386 (1.4.0-1+precise), plasma-desktop:i386 (4.8.5-0ubuntu0.2), libmatekbd:i386 (1.4.0-1+precise), libffmpegthumbnailer4:i386 (2.0.7-2), gpsd:i386 (3.4-2), mate-core:i386 (1.4.0+precise), mate-bluetooth:i386 (1.4.0-2+precise), libmatebluetooth:i386 (1.4.0-2+precise), indicator-session:i386 (0.3.96-0ubuntu1), libmatewnck:i386 (1.4.0-2+precise), python-corba:i386 (1.4.0-1+precise), libmate:i386 (1.4.0-1+precise), gvfs-backends:i386 (1.12.1-0ubuntu1.1), libmatewnck-common:i386 (1.4.0-2+precise), libmatecomponentui:i386 (1.4.0-1+precise), python-mate-menu:i386 (1.4.0-1+precise), ffmpegthumbnailer:i386 (2.0.7-2), mate-session-manager:i386 (1.4.0-1+precise), libgmlib0:i386 (1.0.5-1), indicator-power:i386 (2.0-0ubuntu1), gnome-session:i386 (3.2.1-0ubuntu8), mate-themes:i386 (1.4.0-1+precise), libmatesensorsappletplugin:i386 (1.2.0-3+precise), kde-workspace-bin:i386 (4.8.5-0ubuntu0.2), indicator-printers:i386 (0.1.6-0ubuntu1), libmatecanvas:i386 (1.4.0-1+precise), mate-screensaver:i386 (1.4.0-1+precise), hwdata:i386 (0.233-1ubuntu1), libavdevice53:i386 (0.8.4-0ubuntu0.12.04.1)
End-Date: 2013-01-03  19:31:30

Start-Date: 2013-01-03  19:37:15
Commandline: apt-get upgrade
Upgrade: grub2-common:i386 (1.99-21ubuntu3.4, 1.99-21ubuntu3.7), gnome-control-center:i386 (3.4.2-0ubuntu0.7, 3.4.2-0ubuntu0.8), grub-pc:i386 (1.99-21ubuntu3.4, 1.99-21ubuntu3.7), software-center:i386 (5.2.6, 5.2.7), grub-pc-bin:i386 (1.99-21ubuntu3.4, 1.99-21ubuntu3.7), gnome-control-center-data:i386 (3.4.2-0ubuntu0.7, 3.4.2-0ubuntu0.8), grub-common:i386 (1.99-21ubuntu3.4, 1.99-21ubuntu3.7), mountall:i386 (2.36, 2.36.3), libgnome-control-center1:i386 (3.4.2-0ubuntu0.7, 3.4.2-0ubuntu0.8)
End-Date: 2013-01-03  19:41:36

```

---

### Post by flyingfisch on 2013-02-05
bumpity.

---

### Post by furything on 2013-02-05
I note you have 
> Error: Sub-process /usr/bin/dpkg returned an error code (1)Have you tried to do any repairs? Looks like you have something broken

Try
```
sudo dpkg-reconfigure -a
sudo apt-get update && sudo apt-get upgrade
```Post the output here

This may be pertinent to you
[http://ubuntuforums.org/showthread.php?t=2112670](http://ubuntuforums.org/showthread.php?t=2112670)
Looks like 2 versions of something causing package manager to misbehave.

Have a look through to see what you have installed

---

### Post by flyingfisch on 2013-02-05
Hmm... the last time I did *sudo dpkg-reconfigure -a *my system got messed up, so I'm a little leery of doing it again...

---

### Post by snowpine on 2013-02-05
I don't know about the GUI Update Manager, but let's look at the apt-get terminal commands.

This one has the power to add/remove packages:

```
sudo apt-get dist-upgrade
```

This one does not have the power, therefore it should never uninstall applications:

```
sudo apt-get upgrade
```

For more info, see:

```
man apt-get
```

Probably what happened is you uninstalled a metapackage (a "dummy" package such as 'ubuntu-desktop' that is basically just a list of other packages).

---

### Post by flyingfisch on 2013-02-05
ok, so i should use apt-get upgrade instead?

---

### Post by snowpine on 2013-02-05
I personally only ever use 'apt-get dist-upgrade'; however 1) I do not use Ubuntu, 2) I do not have broken packages, 3) I do not remove metapackages. So I am not sure what advice to give you. "Use 'apt-get upgrade'" is my direct response to your specific question implied by the thread title.

---

### Post by flyingfisch on 2013-02-05
OK, then i guess this thread is solved?

---

