---
title: "dpkg_1.14.5ubuntu11.2_i386.udeb' is NOT trusted"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by Timokl on 2007-10-21
Hi,

I tried to upgrade from Feisty to Gutsy using the graphical update manager several times, and it did not work. 

First, everything seemed fine, and the necessary files got downloaded. After coming back from work several hours later, I expected to have Gutsy set up. But it said that some .debs could not have been downloaded. (Forgot to write down which ones).

When I tried to start upgrade process another time, the process did not get past the first step.

I tried to download from the main server (setting up the sources with Synaptic) instead from the Thai-based server, but to no avail.

Here are my log files from */var/log/dist-upgrade*

**main.log**

```
2007-10-21 18:09:13,681 INFO release-upgrader version '0.81' started
2007-10-21 18:09:47,984 DEBUG lsb-release: 'feisty'
2007-10-21 18:09:48,027 DEBUG _pythonSymlinkCheck run
2007-10-21 18:10:06,983 DEBUG checkViewDepends()
2007-10-21 18:10:06,984 DEBUG getRequiredBackports()
2007-10-21 18:10:33,415 DEBUG marking 'release-upgrader-apt' for install
2007-10-21 18:10:34,004 DEBUG marking 'release-upgrader-dpkg' for install
2007-10-21 18:13:44,999 DEBUG pre-requists item: '<pkgAcquire::ItemIterator object: Status: 2 Complete: 1 Local: 0 IsTrusted: 0 FileSize: 1924684 DestFile:'/tmp/tmpo8ydmK/backports/release-upgrader-dpkg_1.14.5ubuntu11.2_i386.udeb' DescURI: 'http://de.archive.ubuntu.com/ubuntu/pool/main/r/release-upgrader-dpkg/release-upgrader-dpkg_1.14.5ubuntu11.2' 
2007-10-21 18:13:45,040 ERROR pre-requists item 'http://de.archive.ubuntu.com/ubuntu/pool/main/r/release-upgrader-dpkg/release-upgrader-dpkg_1.14.5ubuntu11.2_i386.udeb' is NOT trusted
```

**main_pre_req.log**

```
2007-10-21 17:30:57,616 INFO release-upgrader version '0.81' started
2007-10-21 17:31:01,043 DEBUG lsb-release: 'feisty'
2007-10-21 17:31:01,043 DEBUG _pythonSymlinkCheck run
2007-10-21 17:31:04,664 DEBUG checkViewDepends()
2007-10-21 17:31:04,665 DEBUG getRequiredBackports()
2007-10-21 17:31:39,420 DEBUG marking 'release-upgrader-apt' for install
2007-10-21 17:31:39,556 DEBUG marking 'release-upgrader-dpkg' for install
2007-10-21 17:34:46,085 DEBUG pre-requists item: '<pkgAcquire::ItemIterator object: Status: 2 Complete: 1 Local: 0 IsTrusted: 1 FileSize: 1924684 DestFile:'/tmp/tmpkYxdxK/backports/release-upgrader-dpkg_1.14.5ubuntu11.2_i386.udeb' DescURI: 'http://de.archive.ubuntu.com/ubuntu/pool/main/r/release-upgrader-dpkg/release-upgrader-dpkg_1.14.5ubuntu11.2' 
2007-10-21 17:34:46,086 DEBUG pre-requists item: '<pkgAcquire::ItemIterator object: Status: 2 Complete: 1 Local: 0 IsTrusted: 1 FileSize: 1307096 DestFile:'/tmp/tmpkYxdxK/backports/release-upgrader-apt_0.6.46.4ubuntu10.3_i386.udeb' DescURI: 'http://de.archive.ubuntu.com/ubuntu/pool/main/r/release-upgrader-apt/release-upgrader-apt_0.6.46.4ubuntu10.' 
2007-10-21 17:34:46,087 DEBUG extracting udeb '/tmp/tmpkYxdxK/backports/release-upgrader-dpkg_1.14.5ubuntu11.2_i386.udeb' 
2007-10-21 17:34:46,464 DEBUG extracting udeb '/tmp/tmpkYxdxK/backports/release-upgrader-apt_0.6.46.4ubuntu10.3_i386.udeb' 
```

**apt-autoinst-fixup.log**

```
2007-04-22 08:18:30,011 DEBUG Starting to check for auto-install states that need fixup
2007-04-22 08:18:30,050 DEBUG Found installed meta-pkg: 'ubuntu-standard' 
2007-04-22 08:18:30,050 INFO Removed auto-flag from package 'ed'
2007-04-22 08:18:30,050 INFO Removed auto-flag from package 'command-not-found'
2007-04-22 08:18:30,051 INFO Removed auto-flag from package 'update-manager-core'
2007-04-22 08:18:30,077 DEBUG Found installed meta-pkg: 'ubuntu-minimal' 
2007-04-22 08:18:30,077 INFO Removed auto-flag from package 'apt'
2007-04-22 08:18:30,107 DEBUG Found installed meta-pkg: 'ubuntu-desktop' 
2007-04-22 08:18:30,107 INFO Removed auto-flag from package 'acpi-support'
2007-04-22 08:18:30,108 INFO Removed auto-flag from package 'alacarte'
2007-04-22 08:18:30,108 INFO Removed auto-flag from package 'anacron'
2007-04-22 08:18:30,108 INFO Removed auto-flag from package 'apmd'
2007-04-22 08:18:30,108 INFO Removed auto-flag from package 'avahi-autoipd'
2007-04-22 08:18:30,108 INFO Removed auto-flag from package 'avahi-daemon'
2007-04-22 08:18:30,108 INFO Removed auto-flag from package 'bc'
2007-04-22 08:18:30,108 INFO Removed auto-flag from package 'cdparanoia'
2007-04-22 08:18:30,109 INFO Removed auto-flag from package 'cupsys'
2007-04-22 08:18:30,109 INFO Removed auto-flag from package 'cupsys-bsd'
2007-04-22 08:18:30,109 INFO Removed auto-flag from package 'cupsys-client'
2007-04-22 08:18:30,109 INFO Removed auto-flag from package 'cupsys-driver-gutenprint'
2007-04-22 08:18:30,109 INFO Removed auto-flag from package 'dc'
2007-04-22 08:18:30,109 INFO Removed auto-flag from package 'dcraw'
2007-04-22 08:18:30,109 INFO Removed auto-flag from package 'desktop-effects'
2007-04-22 08:18:30,110 INFO Removed auto-flag from package 'desktop-file-utils'
2007-04-22 08:18:30,110 INFO Removed auto-flag from package 'doc-base'
2007-04-22 08:18:30,110 INFO Removed auto-flag from package 'dvd+rw-tools'
2007-04-22 08:18:30,110 INFO Removed auto-flag from package 'eog'
2007-04-22 08:18:30,110 INFO Removed auto-flag from package 'esound'
2007-04-22 08:18:30,110 INFO Removed auto-flag from package 'evince'
2007-04-22 08:18:30,110 INFO Removed auto-flag from package 'evolution-webcal'
2007-04-22 08:18:30,111 INFO Removed auto-flag from package 'file-roller'
2007-04-22 08:18:30,111 INFO Removed auto-flag from package 'foo2zjs'
2007-04-22 08:18:30,111 INFO Removed auto-flag from package 'foomatic-db'
2007-04-22 08:18:30,111 INFO Removed auto-flag from package 'foomatic-db-engine'
2007-04-22 08:18:30,111 INFO Removed auto-flag from package 'foomatic-db-hpijs'
2007-04-22 08:18:30,111 INFO Removed auto-flag from package 'foomatic-filters'
2007-04-22 08:18:30,111 INFO Removed auto-flag from package 'fortune-mod'
2007-04-22 08:18:30,112 INFO Removed auto-flag from package 'gcalctool'
2007-04-22 08:18:30,112 INFO Removed auto-flag from package 'gconf-editor'
2007-04-22 08:18:30,112 INFO Removed auto-flag from package 'gdebi'
2007-04-22 08:18:30,112 INFO Removed auto-flag from package 'gdm'
2007-04-22 08:18:30,112 INFO Removed auto-flag from package 'gedit'
2007-04-22 08:18:30,112 INFO Removed auto-flag from package 'genisoimage'
2007-04-22 08:18:30,112 INFO Removed auto-flag from package 'gimp-python'
2007-04-22 08:18:30,113 INFO Removed auto-flag from package 'gnome-about'
2007-04-22 08:18:30,113 INFO Removed auto-flag from package 'gnome-app-install'
2007-04-22 08:18:30,113 INFO Removed auto-flag from package 'gnome-applets'
2007-04-22 08:18:30,113 INFO Removed auto-flag from package 'gnome-btdownload'
2007-04-22 08:18:30,113 INFO Removed auto-flag from package 'gnome-control-center'
2007-04-22 08:18:30,113 INFO Removed auto-flag from package 'gnome-cups-manager'
2007-04-22 08:18:30,113 INFO Removed auto-flag from package 'gnome-icon-theme'
2007-04-22 08:18:30,113 INFO Removed auto-flag from package 'gnome-keyring-manager'
2007-04-22 08:18:30,114 INFO Removed auto-flag from package 'gnome-media'
2007-04-22 08:18:30,114 INFO Removed auto-flag from package 'gnome-menus'
2007-04-22 08:18:30,114 INFO Removed auto-flag from package 'gnome-netstatus-applet'
2007-04-22 08:18:30,114 INFO Removed auto-flag from package 'gnome-nettool'
2007-04-22 08:18:30,114 INFO Removed auto-flag from package 'gnome-panel'
2007-04-22 08:18:30,114 INFO Removed auto-flag from package 'gnome-pilot-conduits'
2007-04-22 08:18:30,114 INFO Removed auto-flag from package 'gnome-power-manager'
2007-04-22 08:18:30,115 INFO Removed auto-flag from package 'gnome-session'
2007-04-22 08:18:30,115 INFO Removed auto-flag from package 'gnome-spell'
2007-04-22 08:18:30,115 INFO Removed auto-flag from package 'gnome-system-monitor'
2007-04-22 08:18:30,115 INFO Removed auto-flag from package 'gnome-system-tools'
2007-04-22 08:18:30,115 INFO Removed auto-flag from package 'gnome-terminal'
2007-04-22 08:18:30,115 INFO Removed auto-flag from package 'gnome-themes'
2007-04-22 08:18:30,116 INFO Removed auto-flag from package 'gnome-utils'
2007-04-22 08:18:30,116 INFO Removed auto-flag from package 'gnome-volume-manager'
2007-04-22 08:18:30,116 INFO Removed auto-flag from package 'gs-esp-x'
2007-04-22 08:18:30,116 INFO Removed auto-flag from package 'gstreamer0.10-alsa'
2007-04-22 08:18:30,116 INFO Removed auto-flag from package 'gstreamer0.10-esd'
2007-04-22 08:18:30,116 INFO Removed auto-flag from package 'gstreamer0.10-plugins-base-apps'
2007-04-22 08:18:30,116 INFO Removed auto-flag from package 'gthumb'
2007-04-22 08:18:30,117 INFO Removed auto-flag from package 'gtk2-engines'
2007-04-22 08:18:30,117 INFO Removed auto-flag from package 'gtk2-engines-pixbuf'
2007-04-22 08:18:30,117 INFO Removed auto-flag from package 'gucharmap'
2007-04-22 08:18:30,117 INFO Removed auto-flag from package 'hal'
2007-04-22 08:18:30,117 INFO Removed auto-flag from package 'hal-device-manager'
2007-04-22 08:18:30,117 INFO Removed auto-flag from package 'hotkey-setup'
2007-04-22 08:18:30,117 INFO Removed auto-flag from package 'hwdb-client-gnome'
2007-04-22 08:18:30,117 INFO Removed auto-flag from package 'language-selector'
2007-04-22 08:18:30,118 INFO Removed auto-flag from package 'lftp'
2007-04-22 08:18:30,118 INFO Removed auto-flag from package 'libgl1-mesa-glx'
2007-04-22 08:18:30,118 INFO Removed auto-flag from package 'libgnome2-perl'
2007-04-22 08:18:30,118 INFO Removed auto-flag from package 'libgnomevfs2-bin'
2007-04-22 08:18:30,118 INFO Removed auto-flag from package 'libgnomevfs2-extra'
2007-04-22 08:18:30,118 INFO Removed auto-flag from package 'libnss-mdns'
2007-04-22 08:18:30,118 INFO Removed auto-flag from package 'libpt-plugins-v4l'
2007-04-22 08:18:30,119 INFO Removed auto-flag from package 'libpt-plugins-v4l2'
2007-04-22 08:18:30,119 INFO Removed auto-flag from package 'libstdc++5'
2007-04-22 08:18:30,119 INFO Removed auto-flag from package 'libxp6'
2007-04-22 08:18:30,119 INFO Removed auto-flag from package 'metacity'
2007-04-22 08:18:30,119 INFO Removed auto-flag from package 'min12xxw'
2007-04-22 08:18:30,119 INFO Removed auto-flag from package 'nautilus'
2007-04-22 08:18:30,120 INFO Removed auto-flag from package 'nautilus-cd-burner'
2007-04-22 08:18:30,120 INFO Removed auto-flag from package 'nautilus-sendto'
2007-04-22 08:18:30,120 INFO Removed auto-flag from package 'notification-daemon'
2007-04-22 08:18:30,120 INFO Removed auto-flag from package 'openprinting-ppds'
2007-04-22 08:18:30,120 INFO Removed auto-flag from package 'pnm2ppa'
2007-04-22 08:18:30,120 INFO Removed auto-flag from package 'powermanagement-interface'
2007-04-22 08:18:30,120 INFO Removed auto-flag from package 'readahead'
2007-04-22 08:18:30,121 INFO Removed auto-flag from package 'rss-glx'
2007-04-22 08:18:30,121 INFO Removed auto-flag from package 'screen'
2007-04-22 08:18:30,121 INFO Removed auto-flag from package 'screensaver-default-images'
2007-04-22 08:18:30,121 INFO Removed auto-flag from package 'scrollkeeper'
2007-04-22 08:18:30,121 INFO Removed auto-flag from package 'serpentine'
2007-04-22 08:18:30,121 INFO Removed auto-flag from package 'slocate'
2007-04-22 08:18:30,121 INFO Removed auto-flag from package 'smbclient'
2007-04-22 08:18:30,121 INFO Removed auto-flag from package 'sound-juicer'
2007-04-22 08:18:30,122 INFO Removed auto-flag from package 'ssh-askpass-gnome'
2007-04-22 08:18:30,122 INFO Removed auto-flag from package 'synaptic'
2007-04-22 08:18:30,122 INFO Removed auto-flag from package 'tangerine-icon-theme'
2007-04-22 08:18:30,122 INFO Removed auto-flag from package 'tango-icon-theme'
2007-04-22 08:18:30,122 INFO Removed auto-flag from package 'tango-icon-theme-common'
2007-04-22 08:18:30,122 INFO Removed auto-flag from package 'tsclient'
2007-04-22 08:18:30,122 INFO Removed auto-flag from package 'ttf-bitstream-vera'
2007-04-22 08:18:30,123 INFO Removed auto-flag from package 'ttf-dejavu'
2007-04-22 08:18:30,123 INFO Removed auto-flag from package 'ttf-freefont'
2007-04-22 08:18:30,123 INFO Removed auto-flag from package 'ubuntu-artwork'
2007-04-22 08:18:30,123 INFO Removed auto-flag from package 'ubuntu-sounds'
2007-04-22 08:18:30,123 INFO Removed auto-flag from package 'unzip'
2007-04-22 08:18:30,123 INFO Removed auto-flag from package 'update-notifier'
2007-04-22 08:18:30,124 INFO Removed auto-flag from package 'usplash'
2007-04-22 08:18:30,124 INFO Removed auto-flag from package 'usplash-theme-ubuntu'
2007-04-22 08:18:30,124 INFO Removed auto-flag from package 'vino'
2007-04-22 08:18:30,124 INFO Removed auto-flag from package 'wodim'
2007-04-22 08:18:30,124 INFO Removed auto-flag from package 'wvdial'
2007-04-22 08:18:30,124 INFO Removed auto-flag from package 'x-ttcidfont-conf'
2007-04-22 08:18:30,124 INFO Removed auto-flag from package 'xorg'
2007-04-22 08:18:30,125 INFO Removed auto-flag from package 'xsane'
2007-04-22 08:18:30,125 INFO Removed auto-flag from package 'xscreensaver-data'
2007-04-22 08:18:30,125 INFO Removed auto-flag from package 'xscreensaver-gl'
2007-04-22 08:18:30,125 INFO Removed auto-flag from package 'xterm'
2007-04-22 08:18:30,125 INFO Removed auto-flag from package 'xvncviewer'
2007-04-22 08:18:30,125 INFO Removed auto-flag from package 'yelp'
2007-04-22 08:18:30,125 INFO Removed auto-flag from package 'zenity'
2007-04-22 08:18:30,125 INFO Removed auto-flag from package 'zip'
2007-04-22 08:18:30,126 INFO Removed auto-flag from package 'apport-gtk'
2007-04-22 08:18:30,126 INFO Removed auto-flag from package 'bluez-cups'
2007-04-22 08:18:30,126 INFO Removed auto-flag from package 'bluez-pin'
2007-04-22 08:18:30,126 INFO Removed auto-flag from package 'bluez-utils'
2007-04-22 08:18:30,126 INFO Removed auto-flag from package 'brltty'
2007-04-22 08:18:30,126 INFO Removed auto-flag from package 'brltty-x11'
2007-04-22 08:18:30,126 INFO Removed auto-flag from package 'bug-buddy'
2007-04-22 08:18:30,127 INFO Removed auto-flag from package 'contact-lookup-applet'
2007-04-22 08:18:30,127 INFO Removed auto-flag from package 'deskbar-applet'
2007-04-22 08:18:30,127 INFO Removed auto-flag from package 'diveintopython'
2007-04-22 08:18:30,127 INFO Removed auto-flag from package 'ekiga'
2007-04-22 08:18:30,127 INFO Removed auto-flag from package 'espeak'
2007-04-22 08:18:30,127 INFO Removed auto-flag from package 'evolution'
2007-04-22 08:18:30,128 INFO Removed auto-flag from package 'evolution-exchange'
2007-04-22 08:18:30,128 INFO Removed auto-flag from package 'evolution-plugins'
2007-04-22 08:18:30,128 INFO Removed auto-flag from package 'example-content'
2007-04-22 08:18:30,128 INFO Removed auto-flag from package 'f-spot'
2007-04-22 08:18:30,128 INFO Removed auto-flag from package 'firefox'
2007-04-22 08:18:30,129 INFO Removed auto-flag from package 'firefox-gnome-support'
2007-04-22 08:18:30,129 INFO Removed auto-flag from package 'gaim'
2007-04-22 08:18:30,129 INFO Removed auto-flag from package 'gcc'
2007-04-22 08:18:30,129 INFO Removed auto-flag from package 'gimp'
2007-04-22 08:18:30,129 INFO Removed auto-flag from package 'gimp-print'
2007-04-22 08:18:30,129 INFO Removed auto-flag from package 'gnome-accessibility-themes'
2007-04-22 08:18:30,129 INFO Removed auto-flag from package 'gnome-games'
2007-04-22 08:18:30,130 INFO Removed auto-flag from package 'gnome-mag'
2007-04-22 08:18:30,130 INFO Removed auto-flag from package 'gnome-orca'
2007-04-22 08:18:30,130 INFO Removed auto-flag from package 'gnome-screensaver'
2007-04-22 08:18:30,130 INFO Removed auto-flag from package 'gnome-user-guide'
2007-04-22 08:18:30,130 INFO Removed auto-flag from package 'hplip'
2007-04-22 08:18:30,130 INFO Removed auto-flag from package 'landscape-client'
2007-04-22 08:18:30,130 INFO Removed auto-flag from package 'linux-headers-generic'
2007-04-22 08:18:30,131 INFO Removed auto-flag from package 'make'
2007-04-22 08:18:30,131 INFO Removed auto-flag from package 'onboard'
2007-04-22 08:18:30,131 INFO Removed auto-flag from package 'openoffice.org'
2007-04-22 08:18:30,131 INFO Removed auto-flag from package 'openoffice.org-evolution'
2007-04-22 08:18:30,131 INFO Removed auto-flag from package 'openoffice.org-gnome'
2007-04-22 08:18:30,131 INFO Removed auto-flag from package 'powernowd'
2007-04-22 08:18:30,131 INFO Removed auto-flag from package 'restricted-manager'
2007-04-22 08:18:30,132 INFO Removed auto-flag from package 'rhythmbox'
2007-04-22 08:18:30,132 INFO Removed auto-flag from package 'scim'
2007-04-22 08:18:30,132 INFO Removed auto-flag from package 'scim-gtk2-immodule'
2007-04-22 08:18:30,132 INFO Removed auto-flag from package 'tomboy'
2007-04-22 08:18:30,132 INFO Removed auto-flag from package 'totem'
2007-04-22 08:18:30,132 INFO Removed auto-flag from package 'totem-mozilla'
2007-04-22 08:18:30,132 INFO Removed auto-flag from package 'ttf-arabeyes'
2007-04-22 08:18:30,133 INFO Removed auto-flag from package 'ttf-arphic-ukai'
2007-04-22 08:18:30,133 INFO Removed auto-flag from package 'ttf-arphic-uming'
2007-04-22 08:18:30,133 INFO Removed auto-flag from package 'ttf-baekmuk'
2007-04-22 08:18:30,133 INFO Removed auto-flag from package 'ttf-gentium'
2007-04-22 08:18:30,133 INFO Removed auto-flag from package 'ttf-indic-fonts'
2007-04-22 08:18:30,133 INFO Removed auto-flag from package 'ttf-kochi-gothic'
2007-04-22 08:18:30,133 INFO Removed auto-flag from package 'ttf-kochi-mincho'
2007-04-22 08:18:30,134 INFO Removed auto-flag from package 'ttf-lao'
2007-04-22 08:18:30,134 INFO Removed auto-flag from package 'ttf-malayalam-fonts'
2007-04-22 08:18:30,134 INFO Removed auto-flag from package 'ttf-mgopen'
2007-04-22 08:18:30,134 INFO Removed auto-flag from package 'ttf-thai-tlwg'
2007-04-22 08:18:30,134 INFO Removed auto-flag from package 'ubuntu-docs'
2007-04-22 08:18:30,134 INFO Removed auto-flag from package 'xcursor-themes'
```

**apt.log** This seems to point to some broken packages, I presume.

```
Installing python-central as dep of python-crypto
Installing libc6 as dep of mcpp
Installing xkb-data as dep of xkeyboard-config
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
Installing libpopt0 as dep of libpopt-dev
Installing libcupsys2 as dep of libgnomecupsui1.0-1c2a
Installing libgcc1 as dep of libgnomecupsui1.0-1c2a
Installing gcc-4.1-base as dep of libgcc1
Installing libstdc++6 as dep of libgnomecupsui1.0-1c2a
Installing libasound2 as dep of gstreamer0.10-alsa
Installing libgstreamer0.10-0 as dep of gstreamer0.10-alsa
Installing libnautilus-extension1 as dep of totem-gstreamer
Installing libtotem-plparser1 as dep of totem-gstreamer
Installing gstreamer0.10-plugins-base as dep of totem-gstreamer
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing libdirectfb-0.9-25 as dep of libsdl1.2debian-alsa
Installing xserver-xorg-core as dep of xserver-xorg-video-rendition
Installing libdrm2 as dep of xserver-xorg-core
Installing libsm6 as dep of libsm-dev
Installing libgail-common as dep of libgtkhtml3.8-15
Installing libgail18 as dep of libgail-common
Installing libgnomeprint2.2-0 as dep of libgtkhtml3.8-15
Installing libgnomeprint2.2-data as dep of libgnomeprint2.2-0
Installing libgnomeprintui2.2-0 as dep of libgtkhtml3.8-15
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Installing libwxgtk2.4-1 as dep of libwxgtk2.4-1-contrib
Installing libqt3-mt as dep of libarts1c2a
Installing libxslt1.1 as dep of libxmlsec1
Installing libgpg-error0 as dep of libxslt1.1
Installing gcc-3.3-base as dep of libstdc++5
Installing python2.5 as dep of planner
Installing python2.5-minimal as dep of python2.5
Installing libreadline5 as dep of python2.5
Installing libssl0.9.8 as dep of python2.5
Installing libpanel-applet2-0 as dep of tomboy
Installing python-twisted-bin as dep of python-twisted-core
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
Installing libxcomposite1 as dep of compiz-extra
Installing python2.4 as dep of python2.4-dbg
Installing python2.4-minimal as dep of python2.4
Installing liblua50 as dep of kdelibs4c2a
Installing liblualib50 as dep of kdelibs4c2a
Installing kdelibs-data as dep of kdelibs4c2a
Installing libgsf-1-114 as dep of libgsf-gnome-1-114
Installing libgsf-1-common as dep of libgsf-1-114
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
Installing libice6 as dep of libice-dev
Installing update-manager-core as dep of update-manager
Installing libwps-0.1-1 as dep of openoffice.org-writer
Installing python-uno as dep of openoffice.org-writer
Installing python as dep of python-uno
Installing python-minimal as dep of python
Installing libgs-esp8 as dep of gs-esp
Installing libcupsimage2 as dep of libgs-esp8
Installing gnome-media-common as dep of gnome-media
Installing openoffice.org-style-andromeda as dep of openoffice.org-style-default
Installing metacity-common as dep of metacity
Installing libgucharmap6 as dep of abiword-gnome
Installing libbeagle0 as dep of nautilus
Installing libeel2-2 as dep of nautilus
Installing libeel2-data as dep of libeel2-2
Installing nautilus-data as dep of nautilus
Installing libtasn1-3 as dep of libtasn1-3-dev
Installing libgnome2-common as dep of libgnome2-0
Installing libgfortran1 as dep of octave2.9
Installing libdns22 as dep of bind9-host
Installing openoffice.org-draw as dep of openoffice.org-impress
Installing language-pack-en as dep of language-pack-en-base
Installing libgamin0 as dep of gamin
Installing gnome-user-guide as dep of ubuntu-docs
Installing linux-headers-2.6.20-15-generic as dep of linux-headers-generic
Installing linux-headers-2.6.20-15 as dep of linux-headers-2.6.20-15-generic
Installing dhcp3-common as dep of dhcp3-client
Installing libatspi1.0-0 as dep of python-at-spi
Installing sun-java5-jre as dep of sun-java5-bin
Installing libxine1-ffmpeg as dep of libxine-extracodecs
Installing libxine1 as dep of libxine1-ffmpeg
Installing libpulse0 as dep of libxine1
Installing gftp-common as dep of gftp-gtk
Installing samba-common as dep of smbclient
Installing libslang2 as dep of whiptail
new important dependency: command-not-found
Installing command-not-found as dep of ubuntu-standard
Installing command-not-found-data as dep of command-not-found
Installing language-pack-gnome-th as dep of language-pack-gnome-th-base
Installing brltty as dep of brltty-x11
Installing libbluetooth2 as dep of libbtctl4
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
Installing sun-java6-bin as dep of sun-java6-plugin
Installing sun-java6-jre as dep of sun-java6-bin
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
Installing libwxbase2.6-0 as dep of libwxgtk2.6-0
Installing libmysqlclient15off as dep of python-mysqldb
Installing mysql-common as dep of libmysqlclient15off
Installing gcc-4.1 as dep of g++-4.1
Installing cpp-4.1 as dep of gcc-4.1
Installing binutils as dep of gcc-4.1
Installing libstdc++6-4.1-dev as dep of g++-4.1
Installing esound-common as dep of esound
Installing linux-image-2.6.20-15-generic as dep of linux-image-generic
Installing libjack0.100.0-0 as dep of audacity
Installing libfreebob0 as dep of libjack0.100.0-0
Installing libportaudio2 as dep of audacity
Installing libsamplerate0 as dep of audacity
Installing libsoundtouch1c2 as dep of audacity
Installing libgnomekbd1 as dep of gnome-screensaver
Installing libgnomekbd-common as dep of libgnomekbd1
Installing libgnomekbdui1 as dep of gnome-screensaver
Installing libgpod1 as dep of rhythmbox
Installing libmusicbrainz4c2a as dep of rhythmbox
Installing language-pack-de as dep of language-pack-de-base
Installing libgcrypt11 as dep of libgcrypt11-dev
Installing gedit-common as dep of gedit
Installing python-gmenu as dep of gnome-menus
Installing gnome-panel-data as dep of gnome-panel
Installing icedax as dep of cdda2wav
Installing gnome-core as dep of gnome-office
Installing libsnmp9 as dep of hpijs
Installing libsnmp-base as dep of libsnmp9
Installing genisoimage as dep of dvd+rw-tools
Installing libpq5 as dep of libqt4-qt3support
Installing libqt4-core as dep of libqt4-qt3support
Installing libqt4-gui as dep of libqt4-qt3support
Installing libqt4-sql as dep of libqt4-qt3support
Installing libcaca0 as dep of mplayer
Installing libcucul0 as dep of libcaca0
Installing feisty-gdm-themes as dep of ubuntu-artwork
Installing feisty-session-splashes as dep of ubuntu-artwork
Installing feisty-wallpapers as dep of ubuntu-artwork
Installing libgtkhtml2-0 as dep of screem
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
Installing libslab0 as dep of gnome-control-center
Installing capplets-data as dep of gnome-control-center
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing libxi6 as dep of libxi-dev
Installing hplip-data as dep of hplip
Installing gconf2-common as dep of gconf2
Installing libxrender1 as dep of libxrender-dev
Installing avahi-autoipd as dep of ubuntu-desktop
Installing dcraw as dep of ubuntu-desktop
Installing desktop-effects as dep of ubuntu-desktop
Installing gs-esp-x as dep of ubuntu-desktop
Installing gtk2-engines-pixbuf as dep of ubuntu-desktop
Installing libnss-mdns as dep of ubuntu-desktop
Installing openprinting-ppds as dep of ubuntu-desktop
new important dependency: espeak
Installing espeak as dep of ubuntu-desktop
Installing libespeak1 as dep of espeak
Installing espeak-data as dep of libespeak1
new important dependency: restricted-manager
Installing restricted-manager as dep of ubuntu-desktop
Installing python-notify as dep of restricted-manager
Installing cupsys-client as dep of cupsys-bsd
Installing update-inetd as dep of cupsys-bsd
Installing python2.5-dev as dep of python-dev
Installing libswt3.2-gtk-jni as dep of libswt3.2-gtk-java
Installing language-pack-km as dep of language-pack-km-base
Installing dmsetup as dep of libdevmapper1.02
Installing volumeid as dep of udev
Installing libvolume-id0 as dep of volumeid
Installing libxdmcp6 as dep of libxdmcp-dev
Installing python-apport as dep of apport
Installing python-problem-report as dep of python-apport
Installing python-launchpad-bugs as dep of python-apport
Installing cpp as dep of g++
Installing gcc as dep of g++
Installing libvte9 as dep of gnome-terminal
Installing libvte-common as dep of libvte9
Installing gnome-terminal-data as dep of gnome-terminal
Installing libcinepaint0 as dep of cinepaint
Installing cinepaint-data as dep of cinepaint
Installing e2fslibs as dep of e2fsprogs
Installing gcc-3.4-base as dep of gcc-3.4
Installing cpp-3.4 as dep of gcc-3.4
Installing language-pack-gnome-de as dep of language-pack-gnome-de-base
Installing upstart as dep of upstart-compat-sysv
Installing vlc-nox as dep of mozilla-plugin-vlc
Installing libdvdnav4 as dep of vlc-nox
Installing libpoppler1 as dep of libpoppler1-glib
Installing libruby1.8 as dep of ruby1.8
Installing libx86-1 as dep of vbetool
Installing compiz-core as dep of compiz-plugins
Installing libdecoration0 as dep of compiz-plugins
Installing libgd2-xpm as dep of python-gd
Installing libxcursor1 as dep of libxcursor-dev
Installing python-orca-brlapi as dep of gnome-orca
Installing libgail-gnome-module as dep of gnome-orca
Installing libxml-twig-perl as dep of libnet-dbus-perl
Installing gnome-mount as dep of gnome-volume-manager
Installing dia-common as dep of dia-gnome
Installing libgdiplus as dep of libmono-system1.0-cil
Installing language-pack-gnome-km as dep of language-pack-gnome-km-base
Installing mysql-admin-common as dep of mysql-admin
Installing libqt3-headers as dep of libqt3-mt-dev
Installing libgnomecanvas2-common as dep of libgnomecanvas2-0
Installing python-gtk2 as dep of python-glade2
Installing libgii1-target-x as dep of libgii1
Installing libwv-1.2-3 as dep of beagle
Installing python-bittorrent as dep of bittorrent
Installing libxt6 as dep of libxt-dev
Installing language-selector-common as dep of language-selector
Installing libxmu6 as dep of libxmu-dev
Installing openoffice.org-filter-mobiledev as dep of openoffice.org
Installing libxext6 as dep of libxext-dev
Installing cupsys as dep of cupsys-driver-gutenprint
Installing libjaxp1.3-java as dep of libxerces2-java
Installing libbonobo2-common as dep of libbonobo2-0
Installing zlib1g as dep of zlib1g-dev
Installing libmagic1 as dep of file
Installing software-properties-gtk as dep of gnome-app-install
Installing python-software-properties as dep of software-properties-gtk
Installing libnetpbm10 as dep of netpbm
Installing libcdaudio1 as dep of gstreamer0.10-plugins-bad
Installing libwavpack1 as dep of gstreamer0.10-plugins-bad
Installing dpatch as dep of fglrx-kernel-source
Installing debconf as dep of tasksel
Installing gimp-data as dep of gimp
Installing mscompress as dep of foo2zjs
Installing libgl1-mesa-glx as dep of libgl1-mesa-dev
Installing libgl1-mesa-dri as dep of libgl1-mesa-dev
Installing libgda2-common as dep of libgda2-3
Installing liboobs-1-3 as dep of gnome-applets
Installing gnome-applets-data as dep of gnome-applets
Installing libcurl3-gnutls as dep of xine-ui
Installing linux-restricted-modules-2.6.20-15-generic as dep of linux-restricted-modules-generic
Installing compiz-gtk as dep of compiz
Installing libgnome-compiz-manager0 as dep of gnome-compiz-manager
Installing ogmtools as dep of dvdrip
Installing libusplash0 as dep of usplash
Installing gpgv as dep of gnupg
Starting
Starting 2
WARNING: Failed to read mirror file
Investigating libpango1.0-0
Package libpango1.0-0 has broken dep on pango-libthai
  Considering pango-libthai 0 as a solution to libpango1.0-0 1179
  Added pango-libthai to the remove list
  Fixing libpango1.0-0 via remove of pango-libthai
Investigating libvolume-id0
Package libvolume-id0 has broken dep on libvolumeid0
  Considering libvolumeid0 4 as a solution to libvolume-id0 20
  Added libvolumeid0 to the remove list
  Fixing libvolume-id0 via remove of libvolumeid0
Investigating python2.4-schoolbell
Package python2.4-schoolbell has broken dep on python
  Considering python 690 as a solution to python2.4-schoolbell 3
  Removing python2.4-schoolbell rather than change python
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
Investigating gwget
Package gwget has broken dep on epiphany-extension-gwget
  Considering epiphany-extension-gwget 0 as a solution to gwget 1
  Added epiphany-extension-gwget to the remove list
  Fixing gwget via remove of epiphany-extension-gwget
Investigating python-orbit
Package python-orbit has broken dep on python
  Considering python 690 as a solution to python-orbit 0
  Removing python-orbit rather than change python
Investigating python2.4-schooltool
Package python2.4-schooltool has broken dep on python
  Considering python 690 as a solution to python2.4-schooltool -1
  Removing python2.4-schooltool rather than change python
Done
Starting
Starting 2
Investigating python2.4-tunepimp
Package python2.4-tunepimp has broken dep on libtunepimp3
  Considering libtunepimp3 10001 as a solution to python2.4-tunepimp 0
  Removing python2.4-tunepimp rather than change libtunepimp3
Done
Starting
Starting 2
Investigating libcamel1.2-8
Package libcamel1.2-8 has broken dep on libedataserver1.2-7
  Considering libedataserver1.2-7 10002 as a solution to libcamel1.2-8 0
  Removing libcamel1.2-8 rather than change libedataserver1.2-7
Investigating libexchange-storage1.2-2
Package libexchange-storage1.2-2 has broken dep on libedataserver1.2-7
  Considering libedataserver1.2-7 10002 as a solution to libexchange-storage1.2-2 0
  Removing libexchange-storage1.2-2 rather than change libedataserver1.2-7
Done
Starting
Starting 2
Investigating util-linux
Package util-linux has broken dep on tzdata
  Considering tzdata 10004 as a solution to util-linux 5120
  Removing util-linux rather than change tzdata
Investigating locales
Package locales has broken dep on tzdata
  Considering tzdata 10004 as a solution to locales 1108
  Removing locales rather than change tzdata
Investigating util-linux-locales
Package util-linux-locales has broken dep on util-linux
  Considering util-linux 5120 as a solution to util-linux-locales 9
  Removing util-linux-locales rather than change util-linux
Investigating sun-java6-jre
Package sun-java6-jre has broken dep on locales
  Considering locales 1108 as a solution to sun-java6-jre 4
  Removing sun-java6-jre rather than change locales
Investigating ubuntu-minimal
Package ubuntu-minimal has broken dep on locales
  Considering locales 1108 as a solution to ubuntu-minimal 4
  Removing ubuntu-minimal rather than change locales
Investigating sun-java5-jre
Package sun-java5-jre has broken dep on locales
  Considering locales 1108 as a solution to sun-java5-jre 3
  Removing sun-java5-jre rather than change locales
Investigating libhsqldb-java
Package libhsqldb-java has broken dep on gij
  Considering gij 8 as a solution to libhsqldb-java 3
Package libhsqldb-java has broken dep on java-gcj-compat
  Considering java-gcj-compat 10 as a solution to libhsqldb-java 3
Package libhsqldb-java has broken dep on java2-runtime
  Considering gij-4.1 0 as a solution to libhsqldb-java 3
  Added gij-4.1 to the remove list
  Fixing libhsqldb-java via keep of gij-4.1
Investigating language-pack-en-base
Package language-pack-en-base has broken dep on locales
  Considering locales 1108 as a solution to language-pack-en-base 2
  Removing language-pack-en-base rather than change locales
Investigating language-pack-gnome-th-base
Package language-pack-gnome-th-base has broken dep on locales
  Considering locales 1108 as a solution to language-pack-gnome-th-base 2
  Removing language-pack-gnome-th-base rather than change locales
Investigating language-pack-de-base
Package language-pack-de-base has broken dep on locales
  Considering locales 1108 as a solution to language-pack-de-base 2
  Removing language-pack-de-base rather than change locales
Investigating language-pack-gnome-en-base
Package language-pack-gnome-en-base has broken dep on locales
  Considering locales 1108 as a solution to language-pack-gnome-en-base 2
  Removing language-pack-gnome-en-base rather than change locales
Investigating language-pack-km-base
Package language-pack-km-base has broken dep on locales
  Considering locales 1108 as a solution to language-pack-km-base 2
  Removing language-pack-km-base rather than change locales
Investigating language-pack-gnome-de-base
Package language-pack-gnome-de-base has broken dep on locales
  Considering locales 1108 as a solution to language-pack-gnome-de-base 2
  Removing language-pack-gnome-de-base rather than change locales
Investigating language-pack-gnome-km-base
Package language-pack-gnome-km-base has broken dep on locales
  Considering locales 1108 as a solution to language-pack-gnome-km-base 2
  Removing language-pack-gnome-km-base rather than change locales
Investigating libjline-java
Package libjline-java has broken dep on java-gcj-compat
  Considering java-gcj-compat 10 as a solution to libjline-java 2
Package libjline-java has broken dep on java2-runtime
  Considering gij-4.1 0 as a solution to libjline-java 2
  Added gij-4.1 to the remove list
Package libjline-java has broken dep on java1-runtime
  Considering gij-4.1 0 as a solution to libjline-java 2
  Added gij-4.1 to the remove list
Package libjline-java has broken dep on java-virtual-machine
  Considering gij-4.1 0 as a solution to libjline-java 2
  Added gij-4.1 to the remove list
  Fixing libjline-java via keep of gij-4.1
  Fixing libjline-java via keep of gij-4.1
  Fixing libjline-java via keep of gij-4.1
Investigating libservlet2.3-java
Package libservlet2.3-java has broken dep on java-gcj-compat
  Considering java-gcj-compat 10 as a solution to libservlet2.3-java 2
Package libservlet2.3-java has broken dep on java1-runtime
  Considering gij-4.1 0 as a solution to libservlet2.3-java 2
  Added gij-4.1 to the remove list
Package libservlet2.3-java has broken dep on java2-runtime
  Considering gij-4.1 0 as a solution to libservlet2.3-java 2
  Added gij-4.1 to the remove list
  Fixing libservlet2.3-java via keep of gij-4.1
  Fixing libservlet2.3-java via keep of gij-4.1
Investigating openoffice.org-base
Package openoffice.org-base has broken dep on gij
  Considering gij 8 as a solution to openoffice.org-base 2
Package openoffice.org-base has broken dep on java-gcj-compat
  Considering java-gcj-compat 10 as a solution to openoffice.org-base 2
Package openoffice.org-base has broken dep on j2re1.4
  Considering j2re1.4 2 as a solution to openoffice.org-base 2
Package openoffice.org-base has broken dep on java2-runtime
  Considering gij-4.1 0 as a solution to openoffice.org-base 2
  Added gij-4.1 to the remove list
  Fixing openoffice.org-base via keep of gij-4.1
Investigating language-pack-de
Package language-pack-de has broken dep on language-pack-de-base
  Considering language-pack-de-base 2 as a solution to language-pack-de 2
  Removing language-pack-de rather than change language-pack-de-base
Investigating language-pack-en
Package language-pack-en has broken dep on language-pack-en-base
  Considering language-pack-en-base 2 as a solution to language-pack-en 2
  Removing language-pack-en rather than change language-pack-en-base
Investigating language-pack-km
Package language-pack-km has broken dep on language-pack-km-base
  Considering language-pack-km-base 2 as a solution to language-pack-km 2
  Removing language-pack-km rather than change language-pack-km-base
Investigating language-pack-gnome-de
Package language-pack-gnome-de has broken dep on language-pack-gnome-de-base
  Considering language-pack-gnome-de-base 2 as a solution to language-pack-gnome-de 2
  Removing language-pack-gnome-de rather than change language-pack-gnome-de-base
Investigating language-pack-gnome-en
Package language-pack-gnome-en has broken dep on language-pack-gnome-en-base
  Considering language-pack-gnome-en-base 2 as a solution to language-pack-gnome-en 2
  Removing language-pack-gnome-en rather than change language-pack-gnome-en-base
Investigating language-pack-gnome-km
Package language-pack-gnome-km has broken dep on language-pack-gnome-km-base
  Considering language-pack-gnome-km-base 2 as a solution to language-pack-gnome-km 2
  Removing language-pack-gnome-km rather than change language-pack-gnome-km-base
Investigating language-pack-th-base
Package language-pack-th-base has broken dep on locales
  Considering locales 1108 as a solution to language-pack-th-base 2
  Removing language-pack-th-base rather than change locales
Investigating language-pack-gnome-th
Package language-pack-gnome-th has broken dep on language-pack-gnome-th-base
  Considering language-pack-gnome-th-base 2 as a solution to language-pack-gnome-th 2
  Removing language-pack-gnome-th rather than change language-pack-gnome-th-base
Investigating openoffice.org-filter-mobiledev
Package openoffice.org-filter-mobiledev has broken dep on gij
  Considering gij 8 as a solution to openoffice.org-filter-mobiledev 1
Package openoffice.org-filter-mobiledev has broken dep on java-gcj-compat
  Considering java-gcj-compat 10 as a solution to openoffice.org-filter-mobiledev 1
Package openoffice.org-filter-mobiledev has broken dep on j2re1.4
  Considering j2re1.4 2 as a solution to openoffice.org-filter-mobiledev 1
Package openoffice.org-filter-mobiledev has broken dep on java2-runtime
  Considering gij-4.1 0 as a solution to openoffice.org-filter-mobiledev 1
  Added gij-4.1 to the remove list
  Fixing openoffice.org-filter-mobiledev via keep of gij-4.1
Investigating libjaxp1.2-java
Package libjaxp1.2-java has broken dep on gij
  Considering gij 8 as a solution to libjaxp1.2-java 0
Package libjaxp1.2-java has broken dep on java-gcj-compat
  Considering java-gcj-compat 10 as a solution to libjaxp1.2-java 0
Package libjaxp1.2-java has broken dep on java1-runtime
  Considering gij-4.1 0 as a solution to libjaxp1.2-java 0
Package libjaxp1.2-java has broken dep on java2-runtime
  Considering gij-4.1 0 as a solution to libjaxp1.2-java 0
  Or group remove for libjaxp1.2-java
Investigating libxt-java
Package libxt-java has broken dep on gij
  Considering gij 8 as a solution to libxt-java 0
Package libxt-java has broken dep on java-gcj-compat
  Considering java-gcj-compat 10 as a solution to libxt-java 0
Package libxt-java has broken dep on java1-runtime
  Considering gij-4.1 0 as a solution to libxt-java 0
Package libxt-java has broken dep on java2-runtime
  Considering gij-4.1 0 as a solution to libxt-java 0
  Or group remove for libxt-java
Investigating sun-java6-fonts
Package sun-java6-fonts has broken dep on sun-java6-jre
  Considering sun-java6-jre 4 as a solution to sun-java6-fonts 0
  Removing sun-java6-fonts rather than change sun-java6-jre
Investigating libmysql-java
Package libmysql-java has broken dep on java-gcj-compat-dev
  Considering java-gcj-compat-dev 1 as a solution to libmysql-java 0
Package libmysql-java has broken dep on java2-runtime
  Considering gij-4.1 0 as a solution to libmysql-java 0
  Or group remove for libmysql-java
Investigating python-tz
Package python-tz has broken dep on tzdata
  Considering tzdata 10004 as a solution to python-tz 0
  Removing python-tz rather than change tzdata
Investigating zope3
Package zope3 has broken dep on python-tz
  Considering python-tz 0 as a solution to zope3 0
  Removing zope3 rather than change python-tz
Investigating libc6
Package libc6 has broken dep on locales
  Considering locales 1108 as a solution to libc6 12623
  Added locales to the remove list
  Fixing libc6 via keep of locales
Investigating locales
Package locales has broken dep on tzdata
  Considering tzdata 10004 as a solution to locales 1108
  Removing locales rather than change tzdata
Investigating libxerces2-java
Package libxerces2-java has broken dep on gij
  Considering gij 8 as a solution to libxerces2-java 6
Package libxerces2-java has broken dep on java-gcj-compat
  Considering java-gcj-compat 10 as a solution to libxerces2-java 6
Package libxerces2-java has broken dep on java1-runtime
  Considering gij-4.1 0 as a solution to libxerces2-java 6
  Added gij-4.1 to the remove list
Package libxerces2-java has broken dep on java2-runtime
  Considering gij-4.1 0 as a solution to libxerces2-java 6
  Added gij-4.1 to the remove list
  Fixing libxerces2-java via keep of gij-4.1
  Fixing libxerces2-java via keep of gij-4.1
Investigating libjaxp1.3-java
Package libjaxp1.3-java has broken dep on gij
  Considering gij 8 as a solution to libjaxp1.3-java 5
Package libjaxp1.3-java has broken dep on java-gcj-compat
  Considering java-gcj-compat 10 as a solution to libjaxp1.3-java 5
Package libjaxp1.3-java has broken dep on java1-runtime
  Considering gij-4.1 0 as a solution to libjaxp1.3-java 5
  Added gij-4.1 to the remove list
Package libjaxp1.3-java has broken dep on java2-runtime
  Considering gij-4.1 0 as a solution to libjaxp1.3-java 5
  Added gij-4.1 to the remove list
  Fixing libjaxp1.3-java via keep of gij-4.1
  Fixing libjaxp1.3-java via keep of gij-4.1
Investigating sun-java6-bin
Package sun-java6-bin has broken dep on sun-java6-jre
  Considering sun-java6-jre 4 as a solution to sun-java6-bin 4
  Removing sun-java6-bin rather than change sun-java6-jre
Investigating bsh
Package bsh has broken dep on gij
  Considering gij 8 as a solution to bsh 4
Package bsh has broken dep on java-gcj-compat
  Considering java-gcj-compat 10 as a solution to bsh 4
Package bsh has broken dep on java1-runtime
  Considering gij-4.1 0 as a solution to bsh 4
  Added gij-4.1 to the remove list
Package bsh has broken dep on java2-runtime
  Considering gij-4.1 0 as a solution to bsh 4
  Added gij-4.1 to the remove list
  Fixing bsh via keep of gij-4.1
  Fixing bsh via keep of gij-4.1
Investigating sun-java5-bin
Package sun-java5-bin has broken dep on sun-java5-jre
  Considering sun-java5-jre 3 as a solution to sun-java5-bin 3
  Removing sun-java5-bin rather than change sun-java5-jre
Investigating libhsqldb-java
Package libhsqldb-java has broken dep on gij
  Considering gij 8 as a solution to libhsqldb-java 3
Package libhsqldb-java has broken dep on java-gcj-compat
  Considering java-gcj-compat 10 as a solution to libhsqldb-java 3
Package libhsqldb-java has broken dep on java2-runtime
  Considering gij-4.1 0 as a solution to libhsqldb-java 3
  Added gij-4.1 to the remove list
  Fixing libhsqldb-java via keep of gij-4.1
Investigating libjline-java
Package libjline-java has broken dep on java-gcj-compat
  Considering java-gcj-compat 10 as a solution to libjline-java 2
Package libjline-java has broken dep on java2-runtime
  Considering gij-4.1 0 as a solution to libjline-java 2
  Added gij-4.1 to the remove list
Package libjline-java has broken dep on java1-runtime
  Considering gij-4.1 0 as a solution to libjline-java 2
  Added gij-4.1 to the remove list
Package libjline-java has broken dep on java-virtual-machine
  Considering gij-4.1 0 as a solution to libjline-java 2
  Added gij-4.1 to the remove list
  Fixing libjline-java via keep of gij-4.1
  Fixing libjline-java via keep of gij-4.1
  Fixing libjline-java via keep of gij-4.1
Investigating libservlet2.3-java
Package libservlet2.3-java has broken dep on java-gcj-compat
  Considering java-gcj-compat 10 as a solution to libservlet2.3-java 2
Package libservlet2.3-java has broken dep on java1-runtime
  Considering gij-4.1 0 as a solution to libservlet2.3-java 2
  Added gij-4.1 to the remove list
Package libservlet2.3-java has broken dep on java2-runtime
  Considering gij-4.1 0 as a solution to libservlet2.3-java 2
  Added gij-4.1 to the remove list
  Fixing libservlet2.3-java via keep of gij-4.1
  Fixing libservlet2.3-java via keep of gij-4.1
Investigating openoffice.org-base
Package openoffice.org-base has broken dep on gij
  Considering gij 8 as a solution to openoffice.org-base 2
Package openoffice.org-base has broken dep on java-gcj-compat
  Considering java-gcj-compat 10 as a solution to openoffice.org-base 2
Package openoffice.org-base has broken dep on j2re1.4
  Considering j2re1.4 2 as a solution to openoffice.org-base 2
Package openoffice.org-base has broken dep on java2-runtime
  Considering gij-4.1 0 as a solution to openoffice.org-base 2
  Added gij-4.1 to the remove list
Package openoffice.org-base has broken dep on libpg-java
  Considering libpg-java 0 as a solution to openoffice.org-base 2
  Removing openoffice.org-base rather than change libpg-java
Investigating language-pack-th
Package language-pack-th has broken dep on language-pack-th-base
  Considering language-pack-th-base 2 as a solution to language-pack-th 2
  Removing language-pack-th rather than change language-pack-th-base
Investigating openoffice.org-filter-mobiledev
Package openoffice.org-filter-mobiledev has broken dep on gij
  Considering gij 8 as a solution to openoffice.org-filter-mobiledev 1
Package openoffice.org-filter-mobiledev has broken dep on java-gcj-compat
  Considering java-gcj-compat 10 as a solution to openoffice.org-filter-mobiledev 1
Package openoffice.org-filter-mobiledev has broken dep on j2re1.4
  Considering j2re1.4 2 as a solution to openoffice.org-filter-mobiledev 1
Package openoffice.org-filter-mobiledev has broken dep on java2-runtime
  Considering gij-4.1 0 as a solution to openoffice.org-filter-mobiledev 1
  Added gij-4.1 to the remove list
  Fixing openoffice.org-filter-mobiledev via keep of gij-4.1
Investigating sun-java6-plugin
Package sun-java6-plugin has broken dep on sun-java6-bin
  Considering sun-java6-bin 4 as a solution to sun-java6-plugin 0
  Removing sun-java6-plugin rather than change sun-java6-bin
Investigating openoffice.org-evolution
Package openoffice.org-evolution has broken dep on openoffice.org-base
  Considering openoffice.org-base 2 as a solution to openoffice.org-evolution 0
  Removing openoffice.org-evolution rather than change openoffice.org-base
Investigating openoffice.org
Package openoffice.org has broken dep on openoffice.org-base
  Considering openoffice.org-base 2 as a solution to openoffice.org 0
  Removing openoffice.org rather than change openoffice.org-base
Investigating sun-java5-plugin
Package sun-java5-plugin has broken dep on sun-java5-bin
  Considering sun-java5-bin 3 as a solution to sun-java5-plugin 0
  Removing sun-java5-plugin rather than change sun-java5-bin
Investigating libc6
Package libc6 has broken dep on locales
  Considering locales 1108 as a solution to libc6 12623
  Added locales to the remove list
  Fixing libc6 via keep of locales
Investigating locales
Package locales has broken dep on tzdata
  Considering tzdata 10004 as a solution to locales 12623
  Considering tzdata 10004 as a solution to locales 12623
Investigating libxerces2-java
Package libxerces2-java has broken dep on gij
  Considering gij 8 as a solution to libxerces2-java 6
Package libxerces2-java has broken dep on java-gcj-compat
  Considering java-gcj-compat 10 as a solution to libxerces2-java 6
Package libxerces2-java has broken dep on java1-runtime
  Considering gij-4.1 0 as a solution to libxerces2-java 6
  Added gij-4.1 to the remove list
Package libxerces2-java has broken dep on java2-runtime
  Considering gij-4.1 0 as a solution to libxerces2-java 6
  Added gij-4.1 to the remove list
  Fixing libxerces2-java via keep of gij-4.1
  Fixing libxerces2-java via keep of gij-4.1
Investigating libjaxp1.3-java
Package libjaxp1.3-java has broken dep on gij
  Considering gij 8 as a solution to libjaxp1.3-java 5
Package libjaxp1.3-java has broken dep on java-gcj-compat
  Considering java-gcj-compat 10 as a solution to libjaxp1.3-java 5
Package libjaxp1.3-java has broken dep on java1-runtime
  Considering gij-4.1 6 as a solution to libjaxp1.3-java 5
Package libjaxp1.3-java has broken dep on java2-runtime
  Considering gij-4.1 6 as a solution to libjaxp1.3-java 5
  Or group remove for libjaxp1.3-java
Investigating bsh
Package bsh has broken dep on gij
  Considering gij 8 as a solution to bsh 4
Package bsh has broken dep on java-gcj-compat
  Considering java-gcj-compat 10 as a solution to bsh 4
Package bsh has broken dep on java1-runtime
  Considering gij-4.1 6 as a solution to bsh 4
Package bsh has broken dep on java2-runtime
  Considering gij-4.1 6 as a solution to bsh 4
  Or group remove for bsh
Investigating libxalan2-java
Package libxalan2-java has broken dep on libjaxp1.3-java
  Considering libjaxp1.3-java 5 as a solution to libxalan2-java 4
  Removing libxalan2-java rather than change libjaxp1.3-java
Investigating libhsqldb-java
Package libhsqldb-java has broken dep on gij
  Considering gij 8 as a solution to libhsqldb-java 3
Package libhsqldb-java has broken dep on java-gcj-compat
  Considering java-gcj-compat 10 as a solution to libhsqldb-java 3
Package libhsqldb-java has broken dep on java2-runtime
  Considering gij-4.1 6 as a solution to libhsqldb-java 3
  Or group remove for libhsqldb-java
Investigating libjline-java
Package libjline-java has broken dep on java-gcj-compat
  Considering java-gcj-compat 10 as a solution to libjline-java 2
Package libjline-java has broken dep on java2-runtime
  Considering gij-4.1 6 as a solution to libjline-java 2
Package libjline-java has broken dep on java1-runtime
  Considering gij-4.1 6 as a solution to libjline-java 2
  Or group remove for libjline-java
Package libjline-java has broken dep on java-virtual-machine
  Considering gij-4.1 6 as a solution to libjline-java 2
  Removing libjline-java rather than change java-virtual-machine
Investigating libservlet2.3-java
Package libservlet2.3-java has broken dep on java-gcj-compat
  Considering java-gcj-compat 10 as a solution to libservlet2.3-java 2
Package libservlet2.3-java has broken dep on java1-runtime
  Considering gij-4.1 6 as a solution to libservlet2.3-java 2
Package libservlet2.3-java has broken dep on java2-runtime
  Considering gij-4.1 6 as a solution to libservlet2.3-java 2
  Or group remove for libservlet2.3-java
Investigating openoffice.org-filter-mobiledev
Package openoffice.org-filter-mobiledev has broken dep on gij
  Considering gij 8 as a solution to openoffice.org-filter-mobiledev 1
Package openoffice.org-filter-mobiledev has broken dep on java-gcj-compat
  Considering java-gcj-compat 10 as a solution to openoffice.org-filter-mobiledev 1
Package openoffice.org-filter-mobiledev has broken dep on j2re1.4
  Considering j2re1.4 2 as a solution to openoffice.org-filter-mobiledev 1
Package openoffice.org-filter-mobiledev has broken dep on java2-runtime
  Considering gij-4.1 6 as a solution to openoffice.org-filter-mobiledev 1
  Or group remove for openoffice.org-filter-mobiledev
Investigating locales
Package locales has broken dep on tzdata
  Considering tzdata 10004 as a solution to locales 12623
  Considering tzdata 10004 as a solution to locales 12623
Investigating openoffice.org-java-common
Package openoffice.org-java-common has broken dep on libxalan2-java
  Considering libxalan2-java 5 as a solution to openoffice.org-java-common 6
  Added libxalan2-java to the remove list
Package openoffice.org-java-common has broken dep on bsh
  Considering bsh 4 as a solution to openoffice.org-java-common 6
  Added bsh to the remove list
  Fixing openoffice.org-java-common via keep of libxalan2-java
  Fixing openoffice.org-java-common via keep of bsh
Investigating libxerces2-java
Package libxerces2-java has broken dep on gij
  Considering gij 8 as a solution to libxerces2-java 6
Package libxerces2-java has broken dep on java-gcj-compat
  Considering java-gcj-compat 10 as a solution to libxerces2-java 6
Package libxerces2-java has broken dep on java1-runtime
  Considering gij-4.1 6 as a solution to libxerces2-java 6
Package libxerces2-java has broken dep on java2-runtime
  Considering gij-4.1 6 as a solution to libxerces2-java 6
  Or group remove for libxerces2-java
Package libxerces2-java has broken dep on libjaxp1.3-java
  Considering libjaxp1.3-java 5 as a solution to libxerces2-java 6
  Added libjaxp1.3-java to the remove list
Investigating bsh
Package bsh has broken dep on gij
  Considering gij 8 as a solution to bsh 6
Package bsh has broken dep on java-gcj-compat
  Considering java-gcj-compat 10 as a solution to bsh 6
Package bsh has broken dep on java1-runtime
  Considering gij-4.1 6 as a solution to bsh 6
Package bsh has broken dep on java2-runtime
  Considering gij-4.1 6 as a solution to bsh 6
  Or group remove for bsh
Package bsh has broken dep on libjline-java
  Considering libjline-java 6 as a solution to bsh 6
  Removing bsh rather than change libjline-java
Investigating libxalan2-java
Package libxalan2-java has broken dep on libjaxp1.3-java
  Considering libjaxp1.3-java 5 as a solution to libxalan2-java 6
  Added libjaxp1.3-java to the remove list
Package libxalan2-java has broken dep on libxerces2-java
  Considering libxerces2-java 6 as a solution to libxalan2-java 6
  Removing libxalan2-java rather than change libxerces2-java
Investigating locales
Package locales has broken dep on tzdata
  Considering tzdata 10004 as a solution to locales 12623
  Considering tzdata 10004 as a solution to locales 12623
Investigating openoffice.org-java-common
Package openoffice.org-java-common has broken dep on libxerces2-java
  Considering libxerces2-java 6 as a solution to openoffice.org-java-common 6
  Removing openoffice.org-java-common rather than change libxerces2-java
Investigating locales
Package locales has broken dep on tzdata
  Considering tzdata 10004 as a solution to locales 12623
  Considering tzdata 10004 as a solution to locales 12623
Done
Starting
Starting 2
Investigating libexchange-storage1.2-2
Package libexchange-storage1.2-2 has broken dep on libedataserver1.2-7
  Considering libedataserver1.2-7 10001 as a solution to libexchange-storage1.2-2 0
  Removing libexchange-storage1.2-2 rather than change libedataserver1.2-7
Done
Starting
Starting 2
Investigating libexchange-storage1.2-2
Package libexchange-storage1.2-2 has broken dep on libedataserver1.2-7
  Considering libedataserver1.2-7 10001 as a solution to libexchange-storage1.2-2 0
  Removing libexchange-storage1.2-2 rather than change libedataserver1.2-7
Done
Starting
Starting 2
Investigating linux-restricted-modules-2.6.17-11-generic
Package linux-restricted-modules-2.6.17-11-generic has broken dep on linux-image-2.6.17-11-generic
  Considering linux-image-2.6.17-11-generic 10001 as a solution to linux-restricted-modules-2.6.17-11-generic 0
  Removing linux-restricted-modules-2.6.17-11-generic rather than change linux-image-2.6.17-11-generic
Done
Starting
Starting 2
Investigating libexchange-storage1.2-2
Package libexchange-storage1.2-2 has broken dep on libedataserver1.2-7
  Considering libedataserver1.2-7 10001 as a solution to libexchange-storage1.2-2 0
  Removing libexchange-storage1.2-2 rather than change libedataserver1.2-7
Done
Starting
Starting 2
Investigating libexchange-storage1.2-2
Package libexchange-storage1.2-2 has broken dep on libedataserver1.2-7
  Considering libedataserver1.2-7 10001 as a solution to libexchange-storage1.2-2 0
  Removing libexchange-storage1.2-2 rather than change libedataserver1.2-7
Done
Starting
Starting 2
Investigating linux-restricted-modules-2.6.17-10-generic
Package linux-restricted-modules-2.6.17-10-generic has broken dep on linux-image-2.6.17-10-generic
  Considering linux-image-2.6.17-10-generic 10001 as a solution to linux-restricted-modules-2.6.17-10-generic 0
  Removing linux-restricted-modules-2.6.17-10-generic rather than change linux-image-2.6.17-10-generic
Done
Starting
Starting 2
Investigating libexchange-storage1.2-2
Package libexchange-storage1.2-2 has broken dep on libedataserver1.2-7
  Considering libedataserver1.2-7 10001 as a solution to libexchange-storage1.2-2 0
  Removing libexchange-storage1.2-2 rather than change libedataserver1.2-7
Done
Starting
Starting 2
Investigating qtpfsgui
Package qtpfsgui has broken dep on libexiv2-0.10
  Considering libexiv2-0.10 10001 as a solution to qtpfsgui 0
  Removing qtpfsgui rather than change libexiv2-0.10
Done
Starting
Starting 2
Investigating libexchange-storage1.2-2
Package libexchange-storage1.2-2 has broken dep on libedataserver1.2-7
  Considering libedataserver1.2-7 10001 as a solution to libexchange-storage1.2-2 0
  Removing libexchange-storage1.2-2 rather than change libedataserver1.2-7
Done
Installing xserver-xorg-core as dep of xserver-xorg
Installing libc6 as dep of xserver-xorg-core
Installing libgcc1 as dep of xserver-xorg-core
Installing gcc-4.2-base as dep of libgcc1
Installing libdbus-1-3 as dep of gnome-keyring
Installing libglib2.0-0 as dep of gnome-keyring
Installing libgtk2.0-0 as dep of gnome-keyring
Installing libgtk2.0-common as dep of libgtk2.0-0
Installing libcupsys2 as dep of libgtk2.0-0
Installing libgnutls13 as dep of libcupsys2
Installing liblzo2-2 as dep of libgnutls13
Installing libopencdk8 as dep of libgnutls13
Installing zlib1g as dep of libgnutls13
Installing libkrb53 as dep of libcupsys2
Installing libkeyutils1 as dep of libkrb53
Installing libpango1.0-0 as dep of libgtk2.0-0
Installing libpango1.0-common as dep of libpango1.0-0
Installing libfreetype6 as dep of libpango1.0-0
Installing libxdamage1 as dep of libgtk2.0-0
Installing libart-2.0-2 as dep of f-spot
Installing libgnomeui-0 as dep of f-spot
Installing libglade2-0 as dep of libgnomeui-0
Installing libxml2 as dep of libglade2-0
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
Installing libgtkhtml3.8-15 as dep of libgtkhtml2.0-cil
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
Installing librsvg2-2 as dep of libgnome-compiz-manager0
Installing libgsf-1-114 as dep of librsvg2-2
Installing libgsf-1-common as dep of libgsf-1-114
Installing libwnck22 as dep of libgnome-compiz-manager0
Installing libwnck-common as dep of libwnck22
Installing libstdc++6 as dep of libopenexr2c2a
Installing libasound2 as dep of gstreamer0.10-alsa
Installing libgstreamer0.10-0 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing ghostscript-x as dep of gs-esp-x
Installing ghostscript as dep of ghostscript-x
Installing libgs8 as dep of ghostscript
Installing libcupsimage2 as dep of libgs8
Installing openoffice.org-l10n-common as dep of openoffice.org-l10n-th
Installing openoffice.org-common as dep of openoffice.org-l10n-th
Installing openoffice.org-core as dep of openoffice.org-common
Installing libcurl3-gnutls as dep of openoffice.org-core
Installing libdb4.5 as dep of openoffice.org-core
Installing libhunspell-1.1-0 as dep of openoffice.org-core
Installing libneon26 as dep of openoffice.org-core
Installing libnss3-0d as dep of openoffice.org-core
Installing libpam0g as dep of openoffice.org-core
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing libdbus-glib-1-2 as dep of libgnomekbd1
Installing libgnomekbd-common as dep of libgnomekbd1
Installing libsm6 as dep of libsm-dev
Installing libvorbisfile3 as dep of libarts1c2a
Installing gcc-3.3-base as dep of libstdc++5
Installing libgmime2.2-cil as dep of tomboy
Installing libgnomecanvas2-0 as dep of camorama
Installing libgnomecanvas2-common as dep of libgnomecanvas2-0
Installing perl as dep of libglib-perl
Installing perl-base as dep of perl
Installing perl-modules as dep of perl
Installing libbz2-1.0 as dep of bzip2
Installing libecal1.2-7 as dep of evolution-webcal
Installing libedataserver1.2-9 as dep of libecal1.2-7
Installing libebook1.2-9 as dep of ekiga
Installing libcamel1.2-10 as dep of libebook1.2-9
Installing libopal-2.2 as dep of ekiga
Installing libpt-1.10.0 as dep of libopal-2.2
Installing libssl0.9.8 as dep of libpt-1.10.0
Installing python2.4 as dep of python2.4-dbg
Installing python2.4-minimal as dep of python2.4
Installing libncursesw5 as dep of python2.4
Installing libjasper1 as dep of kdelibs4c2a
Installing kdelibs-data as dep of kdelibs4c2a
Installing libgimp2.0 as dep of gimp-print
Installing libgutenprint2 as dep of gimp-print
Installing libgutenprintui2-1 as dep of gimp-print
Installing libgnomevfs2-common as dep of libgnomevfs2-0
Installing libice6 as dep of libice-dev
Installing update-manager-core as dep of update-manager
Installing python-uno as dep of openoffice.org-writer
Installing gnome-media-common as dep of gnome-media
Installing libmetacity0 as dep of metacity
Installing metacity-common as dep of libmetacity0
Installing libbeagle0 as dep of nautilus
Installing libtrackerclient0 as dep of nautilus
Installing nautilus-data as dep of nautilus
Installing libtasn1-3 as dep of libtasn1-3-dev
Installing libgnome2-common as dep of libgnome2-0
Installing gimp-help-common as dep of gimp-help-de
Installing libglpk0 as dep of octave2.9
Installing libsuitesparse as dep of octave2.9
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
Installing sun-java5-jre as dep of sun-java5-bin
Installing ttf-indic-fonts-core as dep of ttf-indic-fonts
Installing ttf-bengali-fonts as dep of ttf-indic-fonts
Installing ttf-gujarati-fonts as dep of ttf-indic-fonts
Installing ttf-kannada-fonts as dep of ttf-indic-fonts
Installing ttf-malayalam-fonts as dep of ttf-indic-fonts
Installing ttf-oriya-fonts as dep of ttf-indic-fonts
Installing ttf-tamil-fonts as dep of ttf-indic-fonts
Installing ttf-telugu-fonts as dep of ttf-indic-fonts
Installing openoffice.org-java-common as dep of openoffice.org-filter-mobiledev
Installing gftp-common as dep of gftp-gtk
Installing libflac++6 as dep of libk3b2
Installing libflac8 as dep of libflac++6
Installing xdg-utils as dep of libdjvulibre15
Installing libgconf2-ruby1.8 as dep of libgconf2-ruby
Installing libruby1.8 as dep of libgconf2-ruby1.8
Installing libglib2-ruby1.8 as dep of libgconf2-ruby1.8
Installing libao2 as dep of vorbis-tools
Installing libclamav2 as dep of avscan
Installing libiw29 as dep of wireless-tools
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
Installing language-pack-gnome-th as dep of language-pack-gnome-th-base
Installing libgucharmap6 as dep of gucharmap
Installing brltty as dep of brltty-x11
Installing libatk1-ruby1.8 as dep of libatk1-ruby
Installing libbluetooth2 as dep of libbtctl4
Installing libdaemon0 as dep of avahi-daemon
Installing gnome-games-data as dep of gnome-games
Installing gnome-cards-data as dep of gnome-games-data
Installing gdebi-core as dep of gdebi
Installing python-apt as dep of gdebi-core
Installing apt-utils as dep of python-apt
Installing apt as dep of apt-utils
Installing python-central as dep of python-apt
Installing dpkg as dep of python-central
Installing sun-java6-bin as dep of sun-java6-plugin
Installing sun-java6-jre as dep of sun-java6-bin
Installing evolution as dep of evolution-exchange
Installing libedataserverui1.2-8 as dep of evolution
Installing libegroupwise1.2-13 as dep of evolution
Installing libexchange-storage1.2-3 as dep of evolution
Installing libgtkhtml3.14-19 as dep of evolution
Installing evolution-data-server as dep of evolution
Installing libedata-book1.2-2 as dep of evolution-data-server
Installing libedata-cal1.2-6 as dep of evolution-data-server
Installing evolution-data-server-common as dep of evolution-data-server
Installing libwxbase2.6-0 as dep of libwxgtk2.6-0
Installing gcc-4.1 as dep of g++-4.1
Installing cpp-4.1 as dep of gcc-4.1
Installing libstdc++6-4.1-dev as dep of g++-4.1
Installing esound-common as dep of esound
Installing linux-image-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing linux-ubuntu-modules-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing clamav-base as dep of clamav-freshclam
Installing libjack0 as dep of audacity
Installing libgpod2 as dep of rhythmbox
Installing libmtp6 as dep of rhythmbox
Installing libmusicbrainz4c2a as dep of rhythmbox
Installing libtotem-plparser7 as dep of rhythmbox
Installing language-pack-de as dep of language-pack-de-base
Installing liblame0 as dep of gstreamer0.10-plugins-ugly-multiverse
Installing libgcrypt11 as dep of libgcrypt11-dev
Installing libgtksourceview2.0-0 as dep of gedit
Installing libgtksourceview2.0-common as dep of libgtksourceview2.0-0
Installing gedit-common as dep of gedit
Installing python-pygtksourceview as dep of gedit
Installing python-gmenu as dep of gnome-menus
Installing gnome-core as dep of gnome-office
Installing eog as dep of gnome-core
Installing gnome-session as dep of gnome-core
Installing gnome-control-center as dep of gnome-session
Installing capplets-data as dep of gnome-control-center
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing libsnmp10 as dep of hpijs
Installing libsnmp-base as dep of libsnmp10
Installing libx264-54 as dep of mplayer
Installing gutsy-wallpapers as dep of ubuntu-artwork
Installing libgtkhtml2-0 as dep of screem
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
Installing libsasl2-2 as dep of libsasl2-modules
Installing libpoppler-qt2 as dep of krita
Installing libpoppler2 as dep of libpoppler-qt2
Installing libxi6 as dep of libxi-dev
Installing hplip-data as dep of hplip
Installing gconf2-common as dep of gconf2
Installing libxrender1 as dep of libxrender-dev
Installing libglade2-ruby1.8 as dep of libglade2-ruby
Installing libgtk2-ruby1.8 as dep of libglade2-ruby1.8
Installing libpango1-ruby1.8 as dep of libgtk2-ruby1.8
Installing libgdk-pixbuf2-ruby1.8 as dep of libgtk2-ruby1.8
Installing cupsys-client as dep of cupsys-bsd
Installing mysql-common as dep of mysql-client-5.0
Installing libmysqlclient15off as dep of mysql-client-5.0
Installing fontconfig-config as dep of libfontconfig1
Installing libvlc0 as dep of vlc-plugin-sdl
Installing libswt3.2-gtk-jni as dep of libswt3.2-gtk-java
Installing language-pack-km as dep of language-pack-km-base
Installing update-notifier-common as dep of update-notifier
Installing restricted-manager-core as dep of restricted-manager
Installing guidance-backends as dep of restricted-manager-core
Installing libxdmcp6 as dep of libxdmcp-dev
Installing cpp as dep of g++
Installing gcc as dep of g++
Installing python2.5-minimal as dep of python2.5
Installing e2fslibs as dep of e2fsprogs
Installing libpng12-0 as dep of libpng12-dev
Installing gcc-3.4-base as dep of gcc-3.4
Installing cpp-3.4 as dep of gcc-3.4
Installing language-pack-gnome-de as dep of language-pack-gnome-de-base
Installing upstart as dep of upstart-compat-sysv
Installing vlc-nox as dep of mozilla-plugin-vlc
Installing libavcodec1d as dep of vlc-nox
Installing libavutil1d as dep of libavcodec1d
Installing libavformat1d as dep of vlc-nox
Installing libebml0 as dep of vlc-nox
Installing libmatroska0 as dep of vlc-nox
Installing libpostproc1d as dep of vlc-nox
Installing libart2.0-cil as dep of libgnome2.0-cil
Installing librsvg2.0-cil as dep of libgnome2.0-cil
Installing libjinglexmpp0.3-0 as dep of libjinglep2p0.3-0
Installing libmozjs0d as dep of gxine
Installing libgtop2-7 as dep of gnome-utils
Installing compiz-core as dep of compiz-plugins
Installing libexiv2-0 as dep of qtpfsgui
Installing libqt4-gui as dep of qtpfsgui
Installing qtpfsgui-data as dep of qtpfsgui
Installing dmz-cursor-theme as dep of human-theme
Installing libxcursor1 as dep of libxcursor-dev
Installing libgnome-speech7 as dep of gnome-orca
Installing libespeak1 as dep of libgnome-speech7
Installing espeak-data as dep of libespeak1
Installing python-orca-brlapi as dep of gnome-orca
Installing python-problem-report as dep of python-apport
Installing gimp as dep of gimp-helpbrowser
Installing gimp-data as dep of gimp
Installing libpoppler-glib2 as dep of gimp
Installing belocs-locales-bin as dep of locales
Installing dia-common as dep of dia-gnome
Installing libxine1 as dep of libxine1-ffmpeg
Installing libxcb-shape0 as dep of libxine1
Installing libxcb1 as dep of libxcb-shape0
Installing libxcb-shm0 as dep of libxine1
Installing libxcb-xv0 as dep of libxine1
Installing libswscale1d as dep of ffmpeg2theora
Installing language-pack-gnome-km as dep of language-pack-gnome-km-base
Installing mysql-admin-common as dep of mysql-admin
Installing mysql-query-browser as dep of mysql-admin
Installing mysql-query-browser-common as dep of mysql-query-browser
Installing libgnutlsxx13 as dep of libgnutls-dev
Installing liblzo2-dev as dep of libgnutls-dev
Installing libqt3-mt as dep of libqt3-mt-dev
Installing libqt3-headers as dep of libqt3-mt-dev
Installing python-gtk2 as dep of python-glade2
Installing freeglut3 as dep of freeglut3-dev
Installing libvte9 as dep of python-vte
Installing libvte-common as dep of libvte9
Installing libxt6 as dep of libxt-dev
Installing language-selector-common as dep of language-selector
Installing libxmu6 as dep of libxmu-dev
Installing libxext6 as dep of libxext-dev
Installing libjpeg62 as dep of libjpeg62-dev
Installing pidgin as dep of gaim
Installing pidgin-data as dep of pidgin
Installing libpurple0 as dep of pidgin
Installing libmeanwhile1 as dep of libpurple0
Installing libzephyr3 as dep of libpurple0
Installing libhesiod0 as dep of libzephyr3
Installing libpcrecpp0 as dep of gnome-system-monitor
Installing libquicktime1 as dep of libmjpegtools0c2a
Installing libbonobo2-common as dep of libbonobo2-0
Installing libmagic1 as dep of file
Installing python-sexy as dep of gnome-app-install
Installing libmms0 as dep of gstreamer0.10-plugins-bad
Installing libopenspc0 as dep of gstreamer0.10-plugins-bad
Installing ttf-dejavu-core as dep of ttf-dejavu
Installing ttf-dejavu-extra as dep of ttf-dejavu
Installing librarian0 as dep of yelp
Installing libgl1-mesa-glx as dep of libgl1-mesa-dev
Installing dmidecode as dep of laptop-detect
Installing libxrandr2 as dep of libxrandr-dev
Installing gnome-applets-data as dep of gnome-applets
Installing libgoffice-0-4 as dep of gnumeric
Installing libalut0 as dep of rss-glx
Installing libopenal0a as dep of libalut0
Installing libglew1.4 as dep of rss-glx
Installing libservlet2.4-java as dep of libhsqldb-java
Installing linux-restricted-modules-2.6.22-14-generic as dep of linux-restricted-modules-generic
Installing libpaper-utils as dep of cups-pdf
Installing compiz-fusion-plugins-main as dep of compiz
Installing compiz-fusion-plugins-extra as dep of compiz
Installing libcompizconfig0 as dep of compiz
Installing gnome-panel-data as dep of gnome-panel
Installing liblink-grammar4 as dep of abiword-plugins
Installing link-grammar-dictionaries-en as dep of liblink-grammar4
Installing libavahi-compat-libdnssd1 as dep of cupsys
Installing libxinerama1 as dep of libxinerama-dev
Installing libkrb5-dev as dep of libcupsys2-dev
Installing libkadm55 as dep of libkrb5-dev
Installing comerr-dev as dep of libkrb5-dev
Installing libntfs-3g12 as dep of ntfs-3g
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Installing libcompizconfig-backend-gconf as dep of compiz-gnome
Starting
Starting 2
Investigating dbus
Package dbus has broken dep on dbus-1-utils
  Considering dbus-1-utils 0 as a solution to dbus 135
  Added dbus-1-utils to the remove list
  Fixing dbus via remove of dbus-1-utils
Investigating firefox
Package firefox has broken dep on libnss3
  Considering libnss3 -1 as a solution to firefox 22
  Added libnss3 to the remove list
  Fixing firefox via remove of libnss3
Investigating compiz-core
Package compiz-core has broken dep on compiz-extra
  Considering compiz-extra -2 as a solution to compiz-core 21
  Will not break compiz-extra as stated in Breaks field in compiz-core
Investigating compiz-plugins
Package compiz-plugins has broken dep on compiz-core
  Considering compiz-core 21 as a solution to compiz-plugins 9
  Holding Back compiz-plugins rather than change compiz-core
Investigating compiz-gnome
Package compiz-gnome has broken dep on compiz-core
  Considering compiz-core 21 as a solution to compiz-gnome 4
  Holding Back compiz-gnome rather than change compiz-core
Investigating libsasl2
Package libsasl2 has broken dep on libsasl2-2
  Considering libsasl2-2 46 as a solution to libsasl2 3
  Removing libsasl2 rather than change libsasl2-2
Investigating ttf-thai-tlwg
Package ttf-thai-tlwg has broken dep on xfonts-thai-ttf
  Considering xfonts-thai-ttf -1 as a solution to ttf-thai-tlwg 2
  Added xfonts-thai-ttf to the remove list
  Fixing ttf-thai-tlwg via remove of xfonts-thai-ttf
Investigating libexiv2-0
Package libexiv2-0 has broken dep on libexiv2-0.12
  Considering libexiv2-0.12 -1 as a solution to libexiv2-0 1
  Added libexiv2-0.12 to the remove list
  Fixing libexiv2-0 via remove of libexiv2-0.12
Investigating libwnck18
Package libwnck18 has broken dep on libwnck-common
  Considering libwnck-common 20 as a solution to libwnck18 1
  Removing libwnck18 rather than change libwnck-common
Investigating human-theme
Package human-theme has broken dep on human-cursors-theme
  Considering human-cursors-theme 0 as a solution to human-theme 1
  Added human-cursors-theme to the remove list
  Fixing human-theme via remove of human-cursors-theme
Investigating libsuitesparse
Package libsuitesparse has broken dep on libufsparse
  Considering libufsparse 0 as a solution to libsuitesparse 0
  Holding Back libsuitesparse rather than change libufsparse
Investigating octave2.9
Package octave2.9 has broken dep on libsuitesparse
  Considering libsuitesparse 0 as a solution to octave2.9 0
  Holding Back octave2.9 rather than change libsuitesparse
Investigating libglew1.4
Package libglew1.4 has broken dep on libglew1
  Considering libglew1 -1 as a solution to libglew1.4 0
  Added libglew1 to the remove list
  Fixing libglew1.4 via remove of libglew1
Investigating libopal-2.2
Package libopal-2.2 has broken dep on libopal-2.2.0
  Considering libopal-2.2.0 -1 as a solution to libopal-2.2 0
  Added libopal-2.2.0 to the remove list
  Fixing libopal-2.2 via remove of libopal-2.2.0
Investigating libgnome-speech7
Package libgnome-speech7 has broken dep on libgnome-speech3
  Considering libgnome-speech3 -1 as a solution to libgnome-speech7 0
  Added libgnome-speech3 to the remove list
  Fixing libgnome-speech7 via remove of libgnome-speech3
Investigating liferea
Package liferea has broken dep on liferea-mozilla
  Considering liferea-mozilla -1 as a solution to liferea 0
  Added liferea-mozilla to the remove list
  Fixing liferea via remove of liferea-mozilla
Investigating libuniconf4.3
Package libuniconf4.3 has broken dep on libuniconf4.2
  Considering libuniconf4.2 -1 as a solution to libuniconf4.3 0
  Added libuniconf4.2 to the remove list
  Fixing libuniconf4.3 via remove of libuniconf4.2
Investigating compiz-gtk
Package compiz-gtk has broken dep on libwnck18
  Considering libwnck18 1 as a solution to compiz-gtk -1
  Removing compiz-gtk rather than change libwnck18
 Try to Re-Instate compiz-core
 Try to Re-Instate compiz-plugins
 Try to Re-Instate compiz-gnome
Investigating compiz-gnome
Package compiz-gnome has broken dep on compiz-gtk
  Considering compiz-gtk -1 as a solution to compiz-gnome 4
  Added compiz-gtk to the remove list
  Fixing compiz-gnome via keep of compiz-gtk
 Try to Re-Instate octave2.9
Investigating compiz-gtk
Package compiz-gtk has broken dep on libwnck18
  Considering libwnck18 1 as a solution to compiz-gtk -1
  Removing compiz-gtk rather than change libwnck18
Investigating compiz-gnome
Package compiz-gnome has broken dep on compiz-gtk
  Considering compiz-gtk -1 as a solution to compiz-gnome 4
  Added compiz-gtk to the remove list
  Fixing compiz-gnome via keep of compiz-gtk
Investigating compiz-gtk
Package compiz-gtk has broken dep on libwnck18
  Considering libwnck18 1 as a solution to compiz-gtk 4
  Added libwnck18 to the remove list
  Fixing compiz-gtk via keep of libwnck18
Investigating libwnck18
Package libwnck18 has broken dep on libwnck-common
  Considering libwnck-common 20 as a solution to libwnck18 4
  Removing libwnck18 rather than change libwnck-common
Investigating compiz-gtk
Package compiz-gtk has broken dep on libwnck18
  Considering libwnck18 20 as a solution to compiz-gtk 4
  Removing compiz-gtk rather than change libwnck18
Investigating compiz-gnome
Package compiz-gnome has broken dep on compiz-gtk
  Considering compiz-gtk 20 as a solution to compiz-gnome 4
  Removing compiz-gnome rather than change compiz-gtk
Investigating compiz
Package compiz has broken dep on compiz-gnome
  Considering compiz-gnome 20 as a solution to compiz 3
  Removing compiz rather than change compiz-gnome
Investigating gnome-compiz-manager
Package gnome-compiz-manager has broken dep on compiz
  Considering compiz 20 as a solution to gnome-compiz-manager 0
  Removing gnome-compiz-manager rather than change compiz
Investigating desktop-effects
Package desktop-effects has broken dep on compiz
  Considering compiz 20 as a solution to desktop-effects -1
  Removing desktop-effects rather than change compiz
Done
Installing consolekit as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing fast-user-switch-applet as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing system-config-printer as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing python-cups as dep of system-config-printer
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
Installing compiz-gnome as dep of compiz
Installing compiz-core as dep of compiz-gnome
Installing compiz-plugins as dep of compiz-gnome
Installing discover1 as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libdiscover1 as dep of discover1
Installing discover1-data as dep of libdiscover1
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
Installing scim as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libscim8c2a as dep of scim
Installing scim-gtk2-immodule as dep of scim
Installing scim-modules-socket as dep of scim-gtk2-immodule
Installing scim-tables-additional as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing scim-modules-table as dep of scim-tables-additional
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
Installing xresprobe as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Starting
Starting 2
Investigating compiz-core
Package compiz-core has broken dep on compiz-extra
  Considering compiz-extra -2 as a solution to compiz-core 16
  Will not break compiz-extra as stated in Breaks field in compiz-core
Investigating compiz-plugins
Package compiz-plugins has broken dep on compiz-core
  Considering compiz-core 16 as a solution to compiz-plugins 6
  Holding Back compiz-plugins rather than change compiz-core
Investigating compiz-gnome
Package compiz-gnome has broken dep on compiz-core
  Considering compiz-core 16 as a solution to compiz-gnome 1
  Re-Instated compiz-core
  Re-Instated compiz-plugins
  Re-Instated compiz-gnome
Investigating compiz-core
Package compiz-core has broken dep on compiz-extra
  Considering compiz-extra -2 as a solution to compiz-core 16
  Will not break compiz-extra as stated in Breaks field in compiz-core
Investigating compiz-plugins
Package compiz-plugins has broken dep on compiz-core
  Considering compiz-core 16 as a solution to compiz-plugins 6
  Holding Back compiz-plugins rather than change compiz-core
Investigating compiz-gnome
Package compiz-gnome has broken dep on compiz-core
  Considering compiz-core 16 as a solution to compiz-gnome 1
  Removing compiz-gnome rather than change compiz-core
Investigating compiz
Package compiz has broken dep on compiz-gnome
  Considering compiz-gnome 1 as a solution to compiz 0
    Reinst Failed because of compiz-gnome
  Removing compiz rather than change compiz-gnome
 Try to Re-Instate compiz-core
 Try to Re-Instate compiz-plugins
Done

bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.


bzip2: Data integrity error when decompressing.
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.
```

---

### Post by Timokl on 2007-10-21
It seems to me that I should remove compiz from my actual distribution. Could this help? (That's the way I interpret the log files.)

---

### Post by Timokl on 2007-10-21
I forgot - here's my /etc/apt/sources.list

```
# 
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release Candidate i386 (20061017.1)]/ edgy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty main #Added by software-properties


# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release Candidate i386 (20061017.1)]/ edgy restricted

deb http://archive.ubuntu.com/ubuntu/ feisty main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty universe multiverse #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ feisty-updates main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty-updates main universe multiverse #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://th.archive.ubuntu.com/ubuntu/ edgy

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ feisty-backports main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty-backports main multiverse universe #Added by software-properties


deb http://archive.ubuntu.com/ubuntu/ feisty-security main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty-security main universe multiverse #Added by software-properties
# deb http://security.ubuntu.com/ubuntu edgy-security universe
deb http://archive.ubuntu.com/ubuntu/ feisty-proposed main multiverse universe restricted
deb-src http://archive.ubuntu.com/ubuntu/ feisty-proposed main multiverse universe #Added by software-properties
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
# deb http://wine.budgetdedicated.com/apt edgy main
# deb http://debian.scribus.net/debian dapper main restricted
# deb-src http://debian.scribus.net/debian dapper main restricted
# deb http://debian.tagancha.org/debian dapper main restricted
# deb-src http://debian.tagancha.org/debian dapper main restricted

# Webcam
# deb http://blognux.free.fr/debian unstable main

# Compiz
# deb http://gandalfn.club.fr/ubuntu edgy dev
# deb http://ubuntu.davromaniak.eu edgy-depomaniak all
# deb http://www.telemail.fi/mlind/ubuntu edgy fonts
# deb-src http://www.telemail.fi/mlind/ubuntu edgy fonts

# Bibus
# deb http://switch.dl.sourceforge.net/sourceforge/bibus-biblio ./
# deb-src http://switch.dl.sourceforge.net/sourceforge/bibus-biblio ./

## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
# deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
# deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free
# deb http://download.skype.com/linux/repos/debian/ stable non-free
```

---

