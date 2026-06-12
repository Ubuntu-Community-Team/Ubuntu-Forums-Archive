---
title: "upgrade to 14.10 incomplete errors"
date: 2015-07-17
forum: Installation &amp; Upgrades
---

### Post by friendlyfrank on 2015-07-17
Hi,
The upgrade from 14.04 failed and softwareupdater fails authentication.

Have tried apt-get result below,  Any suggestion on fixing this?

```
frank@frank-Satellite-M200:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  account-plugin-aim account-plugin-jabber account-plugin-salut
  account-plugin-yahoo acpid alsa-utils anacron apparmor appmenu-qt5 apport at
  avahi-daemon bamfdaemon blender blender-data bluez cheese cheese-common
  colord compiz compiz-core compiz-gnome compiz-plugins compiz-plugins-default
  console-setup cpp cron cups cups-browsed cups-bsd cups-client
  cups-core-drivers cups-daemon cups-filters cups-filters-core-drivers dbus
  dictionaries-common empathy empathy-common eog evince evince-common
  evolution evolution-common evolution-data-server
  evolution-data-server-common evolution-data-server-online-accounts
  evolution-indicator evolution-plugins exiv2 fonts-thai-tlwg freecad
  friendly-recovery g++ gcc gdb gdm gir1.2-clutter-1.0 gir1.2-cogl-1.0
  gir1.2-coglpango-1.0 gir1.2-ebook-1.2 gir1.2-ebookcontacts-1.2
  gir1.2-edataserver-1.2 gir1.2-gdata-0.0 gir1.2-gdm-1.0
  gir1.2-gnomedesktop-3.0 gir1.2-goa-1.0 gir1.2-gtk-3.0 gir1.2-gtksource-3.0
  gir1.2-mutter-3.0 gir1.2-rb-3.0 gir1.2-totem-1.0 glib-networking
  glib-networking-common glib-networking-services gnome-contacts
  gnome-control-center gnome-control-center-data gnome-font-viewer
  gnome-nettool gnome-screensaver gnome-session gnome-session-bin
  gnome-session-common gnome-settings-daemon gnome-settings-daemon-schemas
  gnome-shell gnome-shell-common gnome-system-monitor gnucash gnucash-common
  gpsd gstreamer0.10-plugins-bad gstreamer1.0-clutter gstreamer1.0-libav
  gstreamer1.0-plugins-bad gstreamer1.0-plugins-bad-faad
  gstreamer1.0-plugins-bad-videoparsers hud ifupdown indicator-datetime
  indicator-keyboard initscripts inkscape irqbalance jftp
  keyboard-configuration kmod lftp libaccount-plugin-1.0-0 libaccounts-qt5-1
  libalgorithm-diff-xs-perl libapparmor-perl libapt-pkg-perl libaqbanking34
  libaqbanking34-plugins libaqebics0 libaqhbci22 libaqofxconnect7 libbamf3-2
  libcairo-perl libcheese-gtk23 libcheese7 libchromaprint0 libclone-perl
  libclutter-1.0-0 libclutter-gst-2.0-0 libclutter-gtk-1.0-0 libcmis-0.4-4
  libcompizconfig0 libcrypt-ssleay-perl libcups2 libcupscgi1 libcupsimage2
  libcupsmime1 libcupsppdc1 libcurl3 libcurl3-gnutls libdatetime-perl
  libdatetime-timezone-perl libdecoration0 libebackend-1.2-7 libebook-1.2-14
  libedata-book-1.2-20 libedata-cal-1.2-23 libedataserver-1.2-18 libegl1-mesa
  libegl1-mesa-drivers libevdocument3-4 libevolution libevview3-3
  libfile-fcntllock-perl libfinance-quote-perl libfreeimage3 libgadu3
  libgail-3-0 libgbm1 libgdal1h libgdm1 libgexiv2-2 libgksu2-0 libgl1-mesa-dri
  libgl1-mesa-glx libglapi-mesa libgles2-mesa libglib-perl libgnomevfs2-0
  libgnutls-openssl27 libgnutls26 libgoa-1.0-0b libgoa-1.0-common
  libgoa-backend-1.0-1 libgpod-common libgpod4 libgstreamer-plugins-bad0.10-0
  libgstreamer-plugins-bad1.0-0 libgtk-3-0 libgtk-3-bin libgtk2-perl
  libgtkhtml-4.0-0 libgtkhtml-4.0-common libgtkhtml-editor-4.0-0
  libgtkmm-3.0-1 libgtksourceview-3.0-1 libgvnc-1.0-0 libgwenhywfar60
  libhtml-parser-perl libhud2 libimobiledevice4 libio-pty-perl libldap-2.4-2
  libldb1 liblist-moreutils-perl liblocale-gettext-perl
  liblog-message-simple-perl libmm-glib0 libneon27-gnutls libnet-dbus-perl
  libnet-dns-perl libnet-ssleay-perl libnetaddr-ip-perl libopencv-calib3d2.4
  libopencv-contrib2.4 libopencv-core2.4 libopencv-features2d2.4
  libopencv-flann2.4 libopencv-highgui2.4 libopencv-imgproc2.4
  libopencv-legacy2.4 libopencv-ml2.4 libopencv-objdetect2.4
  libopencv-video2.4 libopenimageio1.3 liboxideqt-qmlplugin liboxideqtcore0
  liboxideqtquick0 libpackage-stash-xs-perl libpam-systemd libpango-perl
  libparams-classify-perl libparams-util-perl libparams-validate-perl
  libperlio-gzip-perl libpoppler-glib8 libpulse0 libpurple0 libqt5core5a
  libqt5dbus5 libqt5gui5 libqt5multimedia5 libqt5network5 libqt5opengl5
  libqt5organizer5 libqt5positioning5 libqt5printsupport5
  libqt5qml-graphicaleffects libqt5qml5 libqt5quick5 libqt5sensors5 libqt5sql5
  libqt5sql5-sqlite libqt5svg5 libqt5test5 libqt5webkit5
  libqt5webkit5-qmlwebkitplugin libqt5widgets5 libqt5xml5
  libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core
  libreoffice-draw libreoffice-gnome libreoffice-gtk libreoffice-help-en-us
  libreoffice-impress libreoffice-math libreoffice-pdfimport
  libreoffice-style-human libreoffice-style-tango libreoffice-writer
  librhythmbox-core8 libsignon-extension1 libsmbclient libsnmp30
  libsocket6-perl libssh2-1 libsub-identify-perl libsub-name-perl
  libsystemd-daemon0 libterm-readkey-perl libtext-charwidth-perl
  libtext-iconv-perl libtext-soundex-perl libtimezonemap1 libtotem-plparser18
  libtotem0 libudev1 libunity-core-6.0-9 libusbmuxd2 libuuid-perl libva1
  libvlc5 libvncserver0 libwayland-egl1-mesa libxatracker2 libxml-parser-perl
  lightdm linux-generic linux-headers-generic linux-image-generic lsb-base
  lsb-core lsb-security mcp-account-manager-uoa metacity metacity-common
  modemmanager mount mountall mutter-common nautilus network-manager nmap
  ntfs-3g oxideqt-codecs-extra parted perl perl-base perl-modules perlmagick
  plymouth plymouth-label plymouth-theme-ubuntu-text poppler-utils
  printer-driver-foo2zjs printer-driver-foo2zjs-common procps pulseaudio
  puppet puppet-common python-aptdaemon python-aptdaemon.gtk3widgets
  python-ldb python-matplotlib python-pycurl python-rdflib python-samba
  python-tk python-twisted-core python-twisted-names python-twisted-web
  python3-uno qlandkartegt qtdeclarative5-dialogs-plugin
  qtdeclarative5-localstorage-plugin qtdeclarative5-privatewidgets-plugin
  qtdeclarative5-qtquick2-plugin
  qtdeclarative5-ubuntu-ui-extras-browser-plugin
  qtdeclarative5-ubuntu-ui-toolkit-plugin qtdeclarative5-window-plugin remmina
  remmina-common remmina-plugin-rdp remmina-plugin-vnc resolvconf rhythmbox
  rhythmbox-data rhythmbox-mozilla rhythmbox-plugin-cdrecorder
  rhythmbox-plugin-magnatune rhythmbox-plugins rsyslog ruby ruby-augeas
  ruby-hiera ruby-json ruby-shadow samba-common samba-common-bin samba-libs
  scribus shotwell shotwell-common signon-ui signond simple-scan smbclient
  system-config-printer-common system-config-printer-udev systemd-shim
  sysvinit-utils telepathy-gabble telepathy-salut totem totem-common
  totem-mozilla totem-plugins ubuntu-session ubuntu-wallpapers udev udisks ufw
  unity unity-control-center unity-control-center-signon unity-services
  unity-settings-daemon unity-webapps-qml uno-libs3 upower upstart ure usbmuxd
  util-linux vinagre vino vlc vlc-data vlc-nox vlc-plugin-notify
  vlc-plugin-pulse wammu webapp-container webbrowser-app xdiagnose
  xserver-xephyr xserver-xorg-core xserver-xorg-input-evdev
  xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-ati
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-geode
  xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-modesetting xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome
  xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon
  xserver-xorg-video-s3 xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sisusb
  xserver-xorg-video-tdfx xserver-xorg-video-trident xserver-xorg-video-vesa
  xserver-xorg-video-vmware
0 upgraded, 0 newly installed, 0 to remove and 435 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up brltty (5.0-2ubuntu3) ...
update-initramfs: deferring update (trigger activated)
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
insserv: Service mountkernfs has to be enabled to start service brltty
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package brltty (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of brltty-x11:
 brltty-x11 depends on brltty (= 5.0-2ubuntu3); however:
  Package brltty is not configured yet.

dpkg: error processing package brltty-x11 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Processing triggers for initramfs-tools (0.103ubuntu8) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-57-generic
Errors were encountered while processing:
 brltty
 brltty-x11
E: Sub-process /usr/bin/dpkg returned an error code (1)
frank@frank-Satellite-M200:~$
```

---

### Post by Shaarika_Lal on 2015-07-17
"Package brltty is not configured yet."
Try reinstalling / configuring this package. 

When I upgraded my system to 14.04, the installations terminated somewhere in the middle.
I followed with the steps below:

apt-get installl -f
apt-get update
apt-get autoclean
apt-get clean


All done as many times as it takes to get apt-get update to execute without failure. 
Then try 
apt-get upgrade

It might work.

---

### Post by tokyobadger on 2015-07-17
@friendlyfrank: how did you prepare for the upgrade and what method did you use?

---

### Post by Bucky Ball on 2015-07-17
Welcome. Unsure why you are upgrading what was probably a fully functional 14.04 LTS (long-term support) release to a release that runs out of support next week.

Forget 14.10. Either clean install 14.04 LTS (supported til 2019) or 15.04 (January 2016).

PS: ALWAYS 'sudo apt-get update' before upgrade or anything else, and please use code tags for terminal output (see last link in my signature). 

PPS: Please post this file:

```
nano /etc/apt/sources.list
```

---

### Post by friendlyfrank on 2015-07-20
frank@frank-Satellite-M200:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) utopic main restricted
deb-src [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) utopic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) utopic-updates main restricted
deb-src [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) utopic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) utopic universe
deb-src [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) utopic universe
deb [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) utopic-updates universe
deb-src [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) utopic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) utopic multiverse
deb-src [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) utopic multiverse
deb [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) utopic-updates multiverse
deb-src [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) utopic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) utopic-security main restricted
deb-src [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) utopic-security main restricted
deb [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) utopic-security universe
deb-src [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) utopic-security universe
deb [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) utopic-security multiverse
deb-src [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) utopic-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) utopic main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) utopic main

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
# deb [http://www.openprinting.org/download/printdriver/debian/](http://www.openprinting.org/download/printdriver/debian/) lsb3.1 gutenprint # disabled on upgrade to saucy
## developers who want to ship their latest software.
frank@frank-Satellite-M200:~$ cat /etc/apt/sources.list
sources.list              sources.list.distUpgrade  
sources.list.d/           sources.list.save         
frank@frank-Satellite-M200:~$ cat /etc/apt/sources.list.distUpgrade 
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) trusty main restricted
deb-src [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) trusty-updates main restricted
deb-src [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) trusty universe
deb-src [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) trusty universe
deb [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) trusty-updates universe
deb-src [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) trusty multiverse
deb-src [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) trusty multiverse
deb [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) trusty-updates multiverse
deb-src [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) trusty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) trusty-security main restricted
deb-src [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) trusty-security main restricted
deb [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) trusty-security universe
deb-src [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) trusty-security universe
deb [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) trusty-security multiverse
deb-src [http://mirror.aarnet.edu.au/pub/ubuntu/archive/](http://mirror.aarnet.edu.au/pub/ubuntu/archive/) trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
# deb [http://www.openprinting.org/download/printdriver/debian/](http://www.openprinting.org/download/printdriver/debian/) lsb3.1 gutenprint # disabled on upgrade to saucy
## developers who want to ship their latest software.
frank@frank-Satellite-M200:~$ 
epare for the upgrade and what method did you use?[/QUOTE]

regards

The upgrade was attempted on line, the 11.04 was fine and up to date
```


```

---

### Post by friendlyfrank on 2015-07-20
just the usual update/upgrade then disupgrade

---

### Post by Bucky Ball on 2015-07-20
Please slap code tags around your output, thanks. :)

Replace [/quote] in the last with [/code] and stick ```
 at the beginning.

You now have a dog's breakfast of Utopic and Trusty repos in your sources.list. 

Even if 14.10 is working it is dead in three days.

What entries do you have on your grub list at boot? One for the 14.10 kernel and one for the 14.04 LTS? After a reboot, choose the first kernel on the list and please post the output of these:

[code]uname -a
lsb_release -a
```

---

