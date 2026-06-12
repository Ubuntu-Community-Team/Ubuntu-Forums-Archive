---
title: "pkgProblemResolver:Resolve generated breaks, this may be caused by held packages"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by chteuchteu on 2010-10-10
Hello !

I'm trying to update my Ubuntu 10.04 to 10.10... But I get this error message:[INDENT]pkgProblemResolver:Resolve generated breaks, this may be caused by held packages
[/INDENT]I tried to disable all the repositories, and also "sudo apt-get -f"... But still having this error message...

What can I do ??

---

### Post by Anal on 2010-11-22
I have the very same issue. 

Please help :)

Thanks!

---

### Post by letharion on 2010-12-29
Bumping, because it's high on google and I have the same problem.

---

### Post by couzin2000 on 2011-01-02
So do I, here's the complete error:

> Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.

Here's the contents of /var/log/dist-upgrade/main.log:

```
2011-01-02 13:03:12,800 INFO Using config files '['./DistUpgrade.cfg']'
2011-01-02 13:03:12,800 INFO uname information: 'Linux sebastien-laptop 2.6.32-27-generic #49-Ubuntu SMP Wed Dec 1 23:52:12 UTC 2010 i686'
2011-01-02 13:03:12,801 INFO creating state file with '['tar', '-z', '-c', '-f', '/var/log/dist-upgrade/system_state.tar.gz', '/etc/apt/preferences.d/', '/etc/apt/sources.list', '/etc/apt/sources.list.d/', '/var/lib/dpkg/status']'
2011-01-02 13:03:12,993 INFO release-upgrader version '0.142.20' started
2011-01-02 13:03:13,228 DEBUG svg pixbuf loader failed (Error displaying image)
2011-01-02 13:03:13,317 DEBUG Using 'DistUpgradeViewGtk' view
2011-01-02 13:03:13,367 DEBUG aufsOptionsAndEnvironmentSetup()
2011-01-02 13:03:13,368 DEBUG using '/tmp/upgrade-rw-KdWg3R' as aufs_rw_dir
2011-01-02 13:03:13,369 DEBUG using '/tmp/upgrade-chroot-xw2nql' as aufs chroot dir
2011-01-02 13:03:13,369 DEBUG enable dpkg --force-overwrite
2011-01-02 13:03:13,444 DEBUG lsb-release: 'lucid'
2011-01-02 13:03:13,452 DEBUG who -m --ips: ''
2011-01-02 13:03:13,453 DEBUG _pythonSymlinkCheck run
2011-01-02 13:03:13,453 DEBUG openCache()
2011-01-02 13:03:14,206 DEBUG /openCache(), new cache size 30361
2011-01-02 13:03:14,207 DEBUG needServerMode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
2011-01-02 13:03:14,207 DEBUG checkViewDepends()
2011-01-02 13:03:14,207 DEBUG running doUpdate() (showErrors=False)
2011-01-02 13:03:15,207 DEBUG openCache()
2011-01-02 13:03:15,720 DEBUG /openCache(), new cache size 30361
2011-01-02 13:03:15,720 DEBUG doPostInitialUpdate
2011-01-02 13:03:15,721 DEBUG Plugin modules in ./plugins: dpkg_status_plugin.py langpack_manual_plugin.py deb_plugin.py remove_lilo_plugin.py kdelibs4to5_plugin.py
2011-01-02 13:03:15,721 DEBUG Loading module ./plugins/dpkg_status_plugin.py
2011-01-02 13:03:15,724 DEBUG Plugins in <module 'dpkg_status_plugin' from './plugins/dpkg_status_plugin.py'>: <class 'dpkg_status_plugin.DpkgStatusPlugin'>
2011-01-02 13:03:15,724 DEBUG Loading module ./plugins/langpack_manual_plugin.py
2011-01-02 13:03:15,726 DEBUG Plugins in <module 'langpack_manual_plugin' from './plugins/langpack_manual_plugin.py'>: <class 'langpack_manual_plugin.MarkLangpacksManuallyInstalledPlugin'>
2011-01-02 13:03:15,726 DEBUG Loading module ./plugins/deb_plugin.py
2011-01-02 13:03:15,727 DEBUG Plugins in <module 'deb_plugin' from './plugins/deb_plugin.py'>: <class 'deb_plugin.DebPlugin'>
2011-01-02 13:03:15,727 DEBUG Loading module ./plugins/remove_lilo_plugin.py
2011-01-02 13:03:15,728 DEBUG Plugins in <module 'remove_lilo_plugin' from './plugins/remove_lilo_plugin.py'>: <class 'remove_lilo_plugin.RemoveLiloPlugin'>
2011-01-02 13:03:15,728 DEBUG Loading module ./plugins/kdelibs4to5_plugin.py
2011-01-02 13:03:15,730 DEBUG Plugins in <module 'kdelibs4to5_plugin' from './plugins/kdelibs4to5_plugin.py'>: <class 'kdelibs4to5_plugin.Kdelibs4devToKdelibs5devPlugin'>
2011-01-02 13:03:15,730 DEBUG plugins for condition 'PostInitialUpdate' are '[]'
2011-01-02 13:03:15,730 DEBUG plugins for condition 'maverickPostInitialUpdate' are '[]'
2011-01-02 13:03:15,730 DEBUG plugins for condition 'from_lucidPostInitialUpdate' are '[]'
2011-01-02 13:03:20,079 DEBUG Foreign: xserver-xorg-video-intel xserver-xorg-video-ati virtualbox-3.2 deluge-common nvidia-173-modaliases acroread nvidia-current-modaliases adobe-flashplugin nvidia-current xserver-xorg-video-radeon libtorrent-rasterbar5 fglrx-modaliases nvidia-96-modaliases nvidia-settings nvidia-173 intel-gpu-tools deluge-gtk python-libtorrent
2011-01-02 13:03:20,080 DEBUG Obsolete: 
2011-01-02 13:03:20,081 DEBUG updateSourcesList()
2011-01-02 13:03:20,163 DEBUG rewriteSourcesList()
2011-01-02 13:03:20,167 DEBUG examining: 'deb http://ca.archive.ubuntu.com/ubuntu/ lucid main restricted'
2011-01-02 13:03:20,167 DEBUG entry 'deb http://ca.archive.ubuntu.com/ubuntu/ maverick main restricted' updated to new dist
2011-01-02 13:03:20,167 DEBUG examining: 'deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid main restricted'
2011-01-02 13:03:20,167 DEBUG entry 'deb-src http://ca.archive.ubuntu.com/ubuntu/ maverick main restricted' updated to new dist
2011-01-02 13:03:20,167 DEBUG examining: 'deb http://ca.archive.ubuntu.com/ubuntu/ lucid-updates main restricted'
2011-01-02 13:03:20,167 DEBUG entry 'deb http://ca.archive.ubuntu.com/ubuntu/ maverick-updates main restricted' updated to new dist
2011-01-02 13:03:20,167 DEBUG examining: 'deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid-updates main restricted'
2011-01-02 13:03:20,168 DEBUG entry 'deb-src http://ca.archive.ubuntu.com/ubuntu/ maverick-updates main restricted' updated to new dist
2011-01-02 13:03:20,168 DEBUG examining: 'deb http://ca.archive.ubuntu.com/ubuntu/ lucid universe'
2011-01-02 13:03:20,168 DEBUG entry 'deb http://ca.archive.ubuntu.com/ubuntu/ maverick universe' updated to new dist
2011-01-02 13:03:20,168 DEBUG examining: 'deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid universe'
2011-01-02 13:03:20,168 DEBUG entry 'deb-src http://ca.archive.ubuntu.com/ubuntu/ maverick universe' updated to new dist
2011-01-02 13:03:20,168 DEBUG examining: 'deb http://ca.archive.ubuntu.com/ubuntu/ lucid-updates universe'
2011-01-02 13:03:20,168 DEBUG entry 'deb http://ca.archive.ubuntu.com/ubuntu/ maverick-updates universe' updated to new dist
2011-01-02 13:03:20,168 DEBUG examining: 'deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid-updates universe'
2011-01-02 13:03:20,169 DEBUG entry 'deb-src http://ca.archive.ubuntu.com/ubuntu/ maverick-updates universe' updated to new dist
2011-01-02 13:03:20,169 DEBUG examining: 'deb http://ca.archive.ubuntu.com/ubuntu/ lucid multiverse'
2011-01-02 13:03:20,169 DEBUG entry 'deb http://ca.archive.ubuntu.com/ubuntu/ maverick multiverse' updated to new dist
2011-01-02 13:03:20,169 DEBUG examining: 'deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid multiverse'
2011-01-02 13:03:20,169 DEBUG entry 'deb-src http://ca.archive.ubuntu.com/ubuntu/ maverick multiverse' updated to new dist
2011-01-02 13:03:20,169 DEBUG examining: 'deb http://ca.archive.ubuntu.com/ubuntu/ lucid-updates multiverse'
2011-01-02 13:03:20,169 DEBUG entry 'deb http://ca.archive.ubuntu.com/ubuntu/ maverick-updates multiverse' updated to new dist
2011-01-02 13:03:20,169 DEBUG examining: 'deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid-updates multiverse'
2011-01-02 13:03:20,170 DEBUG entry 'deb-src http://ca.archive.ubuntu.com/ubuntu/ maverick-updates multiverse' updated to new dist
2011-01-02 13:03:20,170 DEBUG examining: 'deb http://archive.canonical.com/ubuntu lucid partner'
2011-01-02 13:03:20,170 DEBUG entry 'deb http://archive.canonical.com/ubuntu maverick partner' updated to new dist
2011-01-02 13:03:20,170 DEBUG examining: 'deb-src http://archive.canonical.com/ubuntu lucid partner'
2011-01-02 13:03:20,170 DEBUG entry 'deb-src http://archive.canonical.com/ubuntu maverick partner' updated to new dist
2011-01-02 13:03:20,170 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu lucid-security main restricted'
2011-01-02 13:03:20,170 DEBUG entry 'deb http://security.ubuntu.com/ubuntu maverick-security main restricted' updated to new dist
2011-01-02 13:03:20,171 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted'
2011-01-02 13:03:20,171 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted' updated to new dist
2011-01-02 13:03:20,171 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu lucid-security universe'
2011-01-02 13:03:20,171 DEBUG entry 'deb http://security.ubuntu.com/ubuntu maverick-security universe' updated to new dist
2011-01-02 13:03:20,171 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu lucid-security universe'
2011-01-02 13:03:20,171 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu maverick-security universe' updated to new dist
2011-01-02 13:03:20,171 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu lucid-security multiverse'
2011-01-02 13:03:20,171 DEBUG entry 'deb http://security.ubuntu.com/ubuntu maverick-security multiverse' updated to new dist
2011-01-02 13:03:20,172 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse'
2011-01-02 13:03:20,172 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse' updated to new dist
2011-01-02 13:03:20,172 DEBUG examining: 'deb http://download.virtualbox.org/virtualbox/debian lucid non-free'
2011-01-02 13:03:20,177 DEBUG entry '# deb http://download.virtualbox.org/virtualbox/debian maverick non-free # disabled on upgrade to maverick' was disabled (unknown mirror)
2011-01-02 13:03:20,177 DEBUG examining: 'deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu lucid main'
2011-01-02 13:03:20,182 DEBUG entry '# deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu maverick main # disabled on upgrade to maverick' was disabled (unknown mirror)
2011-01-02 13:03:20,182 DEBUG examining: 'deb-src http://ppa.launchpad.net/deluge-team/ppa/ubuntu lucid main'
2011-01-02 13:03:20,187 DEBUG entry '# deb-src http://ppa.launchpad.net/deluge-team/ppa/ubuntu maverick main # disabled on upgrade to maverick' was disabled (unknown mirror)
2011-01-02 13:03:20,187 DEBUG examining: 'deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu lucid main'
2011-01-02 13:03:20,192 DEBUG entry '# deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu maverick main # disabled on upgrade to maverick' was disabled (unknown mirror)
2011-01-02 13:03:20,192 DEBUG examining: 'deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu lucid main'
2011-01-02 13:03:20,197 DEBUG entry '# deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu maverick main # disabled on upgrade to maverick' was disabled (unknown mirror)
2011-01-02 13:03:22,949 DEBUG running doUpdate() (showErrors=True)
2011-01-02 13:03:58,127 DEBUG openCache()
2011-01-02 13:03:58,128 DEBUG failed to SystemUnLock() (E:Not locked) 
2011-01-02 13:04:01,330 DEBUG /openCache(), new cache size 32318
2011-01-02 13:04:01,330 DEBUG needServerMode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
```

Here's also the contents of /var/log/dist-upgrade/apt.log:

```
Log time: 2011-01-02 13:03:13.977003
Log time: 2011-01-02 13:03:15.712456
Log time: 2011-01-02 13:04:01.316633
  Installing xserver-xorg-core as Depends of xserver-xorg
    Installing xserver-common as Depends of xserver-xorg-core
    Installing libxfont1 as Depends of xserver-xorg-core
      Installing libdrm-intel1 as Depends of xserver-xorg-video-intel
      Installing libdrm-nouveau1 as Depends of xserver-xorg-video-nouveau
  Installing gconf2 as Depends of ubuntuone-client
    Installing libgconf2-4 as Depends of gconf2
      Installing libglib2.0-0 as Depends of libgconf2-4
        new important dependency: libdconf0
        Installing libdconf0 as Recommends of libglib2.0-0
      Installing gconf2-common as Depends of libgconf2-4
  Installing python-ubuntuone-client as Depends of ubuntuone-client
    Installing python-ubuntuone-storageprotocol as Depends of python-ubuntuone-client
    Installing python-libproxy as Depends of python-ubuntuone-client
  Installing ubuntu-sso-client as Depends of ubuntuone-client
    Installing dpkg as PreDepends of ubuntu-sso-client
  Installing libappindicator1 as Depends of policykit-1-gnome
    Installing libdbus-glib-1-2 as Depends of libappindicator1
    Installing libdbusmenu-glib1 as Depends of libappindicator1
    Installing libdbusmenu-gtk1 as Depends of libappindicator1
      Installing libgdk-pixbuf2.0-0 as Depends of libdbusmenu-gtk1
    Installing libindicator1 as Depends of libappindicator1
    Installing indicator-application as Recommends of libappindicator1
  Installing libc6 as Depends of mono-2.0-gac
    Installing libc-bin as Depends of libc6
  Installing libmono-corlib2.0-cil as Depends of mono-2.0-gac
    Installing mono-runtime as Depends of libmono-corlib2.0-cil
      Installing mono-gac as Depends of mono-runtime
  Installing libmono-security2.0-cil as Depends of mono-2.0-gac
    Installing libmono-system2.0-cil as Depends of libmono-security2.0-cil
  Installing libcairo2 as Depends of f-spot
    Installing libpixman-1-0 as Depends of libcairo2
  Installing libgtk2.0-0 as Depends of f-spot
  Installing libglib2.0-cil as Depends of f-spot
  Installing libgtk2.0-cil as Depends of f-spot
  Installing libmono-simd2.0-cil as Depends of f-spot
  Installing libmono-system-data2.0-cil as Depends of f-spot
    Installing libmono-data-tds2.0-cil as Depends of libmono-system-data2.0-cil
    Installing libmono-wcf3.0-cil as Depends of libmono-system-data2.0-cil
      Installing libmono-system-messaging2.0-cil as Depends of libmono-wcf3.0-cil
        Installing libmono-messaging2.0-cil as Depends of libmono-system-messaging2.0-cil
  Installing libsqlite3-0 as Depends of f-spot
  Installing libgstreamer0.10-0 as Depends of gstreamer0.10-alsa
  Installing libgstreamer-plugins-base0.10-0 as Depends of gstreamer0.10-alsa
  Installing libsdl1.2debian-alsa as Depends of libsdl1.2debian
  Installing libkrb5support0 as Depends of libkrb5-3
  Installing libgnomekbd-common as Depends of libgnomekbd4
  Installing perl as Depends of libpurple0
    Installing perl-base as Depends of perl
    Installing perl-modules as Depends of perl
  Installing python as Depends of python-twisted-names
    Installing python2.6 as Depends of python
      Installing python2.6-minimal as Depends of python2.6
        Installing libssl0.9.8 as Depends of python2.6-minimal
      Installing libncursesw5 as Depends of python2.6
    Installing python-minimal as Depends of python
  Installing python-twisted-core as Depends of python-twisted-names
    Installing python-twisted-bin as Depends of python-twisted-core
  Installing syslinux-common as Depends of syslinux
    Installing libcrypt-passwdmd5-perl as Recommends of syslinux-common
    Installing libdigest-sha1-perl as Recommends of syslinux-common
  Installing libavutil-extra-50 as Depends of libpostproc-extra-51
  Installing gcc-4.5-base as Depends of libstdc++6
  Installing libkdecore5 as Depends of kubuntu-debug-installer
    Installing liblzma2 as Depends of libkdecore5
    Installing libqt4-dbus as Depends of libkdecore5
      Installing libqt4-xml as Depends of libqt4-dbus
        Installing libqtcore4 as Depends of libqt4-xml
    Installing libqt4-network as Depends of libkdecore5
  Installing libkdeui5 as Depends of kubuntu-debug-installer
    Installing libdbusmenu-qt2 as Depends of libkdeui5
      Installing libqtgui4 as Depends of libdbusmenu-qt2
        Installing libmng1 as Depends of libqtgui4
    Installing libqt4-svg as Depends of libkdeui5
    Installing kdelibs5-data as Recommends of libkdeui5
  Installing libqapt1 as Depends of kubuntu-debug-installer
    Installing apt as Depends of libqapt1
      new important dependency: gpg
  Installing qapt-batch as Depends of kubuntu-debug-installer
    Installing libqapt-runtime as Depends of qapt-batch
  Installing libappindicator0.1-cil as Depends of tomboy
  Installing libbz2-1.0 as Depends of bzip2
  Installing libedataserver1.2-13 as Depends of evolution-webcal
  Installing libespeak1 as Depends of espeak
    Installing libportaudio2 as Depends of libespeak1
      Installing libjack-jackd2-0 as Depends of libportaudio2
    Installing espeak-data as Depends of libespeak1
  Installing libnih1 as Depends of libnih-dbus1
  Installing computer-janitor as Depends of computer-janitor-gtk
    Installing python-argparse as Depends of computer-janitor
  Installing openoffice.org-core as Depends of openoffice.org-gnome
    Installing openoffice.org-common as Depends of openoffice.org-core
    Installing libhunspell-1.2-0 as Depends of openoffice.org-core
    Installing libneon27-gnutls as Depends of openoffice.org-core
    Installing ure as Depends of openoffice.org-core
      Installing uno-libs3 as Depends of ure
  Installing libutouch-grail1 as Depends of xserver-xorg-input-evdev
    Installing libmtdev1 as Depends of libutouch-grail1
  Installing libprotobuf6 as Depends of libcompizconfig0
  Installing compiz-core as Depends of libcompizconfig0
    previously satisfied important dependency on compiz-plugins
    Installing compiz-plugins as Recommends of compiz-core
  Installing update-manager-core as Depends of update-manager
  Installing openoffice.org-base-core as Depends of openoffice.org-writer
  Installing libqtassistantclient4 as Depends of libqt4-assistant
  Installing python-gconf as Depends of python-gnome2
  Installing python-libtorrent as Depends of miro
    Installing libboost-filesystem1.42.0 as Depends of python-libtorrent
      Installing libboost-system1.42.0 as Depends of libboost-filesystem1.42.0
    Installing libboost-python1.42.0 as Depends of python-libtorrent
    Installing libtorrent-rasterbar6 as Depends of python-libtorrent
      Installing libboost-thread1.42.0 as Depends of libtorrent-rasterbar6
      Installing libgeoip1 as Depends of libtorrent-rasterbar6
  Installing miro-data as Depends of miro
  Installing gnome-media-common as Depends of gnome-media
  Installing nautilus-data as Depends of nautilus
  Installing gnome-games-common as Depends of aisleriot
  Installing libgnome2-common as Depends of libgnome2-0
  Installing libusb-1.0-0 as Depends of libdc1394-22
  Installing libbind9-60 as Depends of bind9-host
    Installing libdns66 as Depends of libbind9-60
  Installing libisc60 as Depends of bind9-host
  Installing libisccfg60 as Depends of bind9-host
  Installing liblwres60 as Depends of bind9-host
  Installing openoffice.org-draw as Depends of openoffice.org-impress
  Installing librasqal2 as Depends of slv2-jack
  Installing language-pack-en as Depends of language-pack-en-base
  Installing gvfs as Depends of gvfs-fuse
  Installing erlang-base as Depends of erlang-inets
    previously satisfied important dependency on erlang-crypto
    Installing erlang-crypto as Recommends of erlang-base
    previously satisfied important dependency on erlang-syntax-tools
    Installing erlang-syntax-tools as Recommends of erlang-base
  Installing erlang-mnesia as Depends of erlang-inets
  Installing erlang-runtime-tools as Depends of erlang-inets
  Installing erlang-ssl as Depends of erlang-inets
    Installing erlang-public-key as Depends of erlang-ssl
  Installing python-markupsafe as Depends of python-mako
  Installing linux-headers-2.6.35-24-generic as Depends of linux-headers-generic
    Installing linux-headers-2.6.35-24 as Depends of linux-headers-2.6.35-24-generic
  Installing libaspell15 as Depends of aspell
  Installing dhcp3-common as Depends of dhcp3-client
  Installing libdirectfb-1.2-9 as Depends of libxine1-x
  Installing libxine1-bin as Depends of libxine1-x
  Installing libsnmp-base as Depends of libsnmp15
  Installing libkde3support4 as Depends of libk3b6
    Installing libkfile4 as Depends of libkde3support4
      Installing libkio5 as Depends of libkfile4
        Installing libnepomuk4 as Depends of libkio5
          Installing libsoprano4 as Depends of libnepomuk4
            Installing soprano-daemon as Depends of libsoprano4
        Installing libsolid4 as Depends of libkio5
        Installing kdelibs5-plugins as Recommends of libkio5
          Installing libkatepartinterfaces4 as Depends of kdelibs5-plugins
            Installing libkparts4 as Depends of libkatepartinterfaces4
            Installing libktexteditor4 as Depends of libkatepartinterfaces4
            Installing libkutils4 as Depends of libkatepartinterfaces4
            Installing libqt4-script as Depends of libkatepartinterfaces4
          Installing libkhtml5 as Depends of kdelibs5-plugins
            Installing libkjsapi4 as Depends of libkhtml5
            Installing libphonon4 as Depends of libkhtml5
          Installing libkjsembed4 as Depends of kdelibs5-plugins
          Installing libkntlm4 as Depends of kdelibs5-plugins
          Installing libkrosscore4 as Depends of kdelibs5-plugins
          Installing libkrossui4 as Depends of kdelibs5-plugins
          Installing kdoctools as Depends of kdelibs5-plugins
          Installing kdelibs-bin as Depends of kdelibs5-plugins
    Installing libkpty4 as Depends of libkde3support4
      Installing libutempter0 as Depends of libkpty4
    Installing libqt4-qt3support as Depends of libkde3support4
      Installing libqt4-designer as Depends of libqt4-qt3support
      Installing libqt4-sql as Depends of libqt4-qt3support
  Installing libmpcdec6 as Depends of libk3b6
  Installing libdjvulibre-text as Depends of libdjvulibre21
  Installing libnotify1 as Depends of gnome-settings-daemon
  Installing libmagickcore3 as Depends of obex-data-server
    Installing liblqr-1-0 as Depends of libmagickcore3
  Installing libmagickwand3 as Depends of obex-data-server
  Installing libdebconf-kde0 as Depends of kpackagekit
  Installing libpackagekit-qt-14 as Depends of kpackagekit
  Installing libao4 as Depends of vorbis-tools
    Installing libao-common as Depends of libao4
  Installing libglib2.0-bin as Depends of libglib2.0-dev
  Installing libcamel1.2-14 as Depends of evolution-indicator
  Installing libevolution as Depends of evolution-indicator
    Installing libebackend1.2-0 as Depends of libevolution
    Installing libebook1.2-9 as Depends of libevolution
    Installing libecal1.2-7 as Depends of libevolution
    Installing libedataserverui1.2-8 as Depends of libevolution
    Installing libgdata-google1.2-1 as Depends of libevolution
      Installing libgdata1.2-1 as Depends of libgdata-google1.2-1
    Installing libgtkhtml-editor0 as Depends of libevolution
      Installing libgtkhtml3.14-19 as Depends of libgtkhtml-editor0
      Installing libgtkhtml-editor-common as Depends of libgtkhtml-editor0
  Installing samba-common as Depends of smbclient
  Installing libnewt0.52 as Depends of whiptail
  Installing libvorbis0a as Depends of libvorbisfile3
  Installing plymouth as Depends of plymouth-x11
  Installing libgucharmap7 as Depends of gucharmap
  Installing libatspi1.0-0 as Depends of brltty-x11
  Installing brltty as Depends of brltty-x11
  Installing libnm-glib2 as Depends of network-manager
  Installing libnm-util1 as Depends of network-manager
  Installing libavahi-core7 as Depends of avahi-daemon
  Installing gdebi-core as Depends of gdebi
    Installing python-apt as Depends of gdebi-core
      Installing apt-utils as Depends of python-apt
  Installing libimobiledevice1 as Depends of upower
  Installing libupower-glib1 as Depends of upower
  Installing libedata-book1.2-2 as Depends of evolution-exchange
  Installing libedata-cal1.2-7 as Depends of evolution-exchange
  Installing libegroupwise1.2-13 as Depends of evolution-exchange
  Installing evolution as Depends of evolution-exchange
    Installing evolution-data-server as Depends of evolution
      Installing evolution-data-server-common as Depends of evolution-data-server
  Installing libclutter-1.0-0 as Depends of quadrapassel
  Installing libpulse0 as Depends of libpulse-dev
  Installing libpulse-mainloop-glib0 as Depends of libpulse-dev
  Installing libpulse-browse0 as Depends of libpulse-dev
  Installing xul-ext-ubufox as Depends of ubufox
  Installing libgnome-bluetooth8 as Depends of gnome-bluetooth
  Installing python-aptdaemon as Depends of python-aptdaemon-gtk
  Installing gtkpod-data as Depends of gtkpod
  Installing libgladeui-1-9 as Depends of libgnome-media0
  Installing libavidemux0 as Depends of avidemux
  Installing gcc-4.4-base as Depends of g++-4.4
  Installing gcc-4.4 as Depends of g++-4.4
    Installing cpp-4.4 as Depends of gcc-4.4
      Installing libmpfr4 as Depends of cpp-4.4
    Installing binutils as Depends of gcc-4.4
    Installing libgcc1 as Depends of gcc-4.4
    Installing libgomp1 as Depends of gcc-4.4
  Installing libstdc++6-4.4-dev as Depends of g++-4.4
  Installing libjack0 as Depends of mplayer-gui
  Installing libwxbase2.8-0 as Depends of libwxgtk2.8-0
  Installing libglibmm-2.4-1c2a as Depends of gparted
  Installing totem as Depends of totem-plugins
    Installing libtotem-plparser17 as Depends of totem
    Installing gstreamer0.10-plugins-base as Depends of totem
    Installing totem-common as Depends of totem
    previously satisfied important dependency on totem-mozilla
    Installing totem-mozilla as Recommends of totem
  Installing libgdata7 as Depends of totem-plugins
  Installing libattica0 as Depends of kdebase-runtime
  Installing libkdesu5 as Depends of kdebase-runtime
  Installing libkdnssd4 as Depends of kdebase-runtime
  Installing libkmediaplayer4 as Depends of kdebase-runtime
  Installing libknewstuff3-4 as Depends of kdebase-runtime
  Installing libknotifyconfig4 as Depends of kdebase-runtime
  Installing libnepomukquery4a as Depends of kdebase-runtime
  Installing libplasma3 as Depends of kdebase-runtime
    Installing libkdewebkit5 as Depends of libplasma3
      Installing libqtwebkit4 as Depends of libkdewebkit5
    Installing libthreadweaver4 as Depends of libplasma3
  Installing kdebase-runtime-data as Depends of kdebase-runtime
  Installing plasma-scriptengine-javascript as Depends of kdebase-runtime
  new important dependency: virtuoso-minimal
  Installing virtuoso-minimal as Recommends of kdebase-runtime
    Installing virtuoso-opensource-6.1-bin as Depends of virtuoso-minimal
    Installing libvirtodbc0 as Depends of virtuoso-minimal
      Installing virtuoso-opensource-6.1-common as Depends of libvirtodbc0
      Installing odbcinst as Depends of libvirtodbc0
        Installing odbcinst1debian2 as Depends of odbcinst
  Installing linux-image-2.6.35-24-generic as Depends of linux-image-generic
  Setting NOT as auto-installed (direct Depends of pkg in APT::Never-MarkAuto-Sections)
  Installing audacity-data as Depends of audacity
  previously satisfied important dependency on libavcodec52
  Installing libavcodec52 as Recommends of audacity
    Installing libva1 as Depends of libavcodec52
    Installing libvpx0 as Depends of libavcodec52
  previously satisfied important dependency on libavformat52
  Installing libavformat52 as Recommends of audacity
  Installing libgssdp-1.0-2 as Depends of libgstfarsight0.10-0
  Installing libgupnp-1.0-3 as Depends of libgstfarsight0.10-0
  Installing libgupnp-igd-1.0-3 as Depends of libgstfarsight0.10-0
  Installing libmodplug1 as Depends of libxine1-misc-plugins
  Installing ncurses-bin as Depends of libncursesw5-dev
  Installing libibus2 as Depends of ibus-gtk
  Installing smplayer as Depends of smplayer-translations
  Installing libkimproxy4 as Depends of kdelibs5
  Installing libknewstuff2-4 as Depends of kdelibs5
  Installing python-gmenu as Depends of gnome-menus
  Installing libhpmud0 as Depends of hpijs
  Installing libprotoc6 as Depends of protobuf-compiler
  Installing cups-common as Depends of cups-client
  Installing libx264-98 as Depends of avidemux-plugins-common
  Installing libswscale0 as Depends of mplayer
  Installing libvdpau1 as Depends of mplayer
  Installing language-pack-gnome-en as Depends of language-pack-gnome-en-base
  Installing libgnome-window-settings1 as Depends of gnome-control-center
  Installing capplets-data as Depends of gnome-control-center
  Installing libsasl2-2 as Depends of libsasl2-modules
  Installing libsane-hpaio as Depends of hplip
  Installing hplip-data as Depends of hplip
  Installing mono-csharp-shell as Depends of gbrainy
    Installing libmono-management2.0-cil as Depends of mono-csharp-shell
    Installing mono-gmcs as Depends of mono-csharp-shell
  Installing foomatic-db-compressed-ppds as Depends of ubuntu-desktop
  Setting NOT as auto-installed (direct Depends of pkg in APT::Never-MarkAuto-Sections)
  Installing ubuntu-extras-keyring as Depends of ubuntu-desktop
  Setting NOT as auto-installed (direct Depends of pkg in APT::Never-MarkAuto-Sections)
  new important dependency: ibus-pinyin
  Installing ibus-pinyin as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
    Installing ibus-pinyin-db-open-phrase as Depends of ibus-pinyin
      Installing pinyin-database as Depends of ibus-pinyin-db-open-phrase
    Installing libopencc1 as Depends of ibus-pinyin
    Installing ibus as Depends of ibus-pinyin
      Installing python-ibus as Depends of ibus
  new important dependency: ibus-pinyin-db-android
  Installing ibus-pinyin-db-android as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
  new important dependency: shotwell
  Installing shotwell as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
    Installing libgee2 as Depends of shotwell
    Installing libgexiv2-0 as Depends of shotwell
  new important dependency: ttf-ubuntu-font-family
  Installing ttf-ubuntu-font-family as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
  Installing libboost-iostreams1.42.0 as Depends of aptitude
  Installing libept1 as Depends of aptitude
  Installing libfolks-telepathy0 as Depends of empathy
    Installing libfolks0 as Depends of libfolks-telepathy0
  Installing libtelepathy-logger1 as Depends of empathy
  Installing empathy-common as Depends of empathy
  Installing gnome-icon-theme as Depends of empathy
  Installing telepathy-logger as Depends of empathy
  Installing python2.6-dev as Depends of python-dev
    Installing libpython2.6 as Depends of python2.6-dev
    Installing libssl-dev as Depends of python2.6-dev
  Installing gtk2-engines-murrine as Depends of light-themes
  Installing libvte9 as Depends of vinagre
  Installing libxdmcp6 as Depends of libxdmcp-dev
  Installing libsysfs2 as Depends of libsysfs-dev
  Installing cpp as Depends of g++
  Installing gcc as Depends of g++
  Installing libavahi-client3 as Depends of libavahi-client-dev
  Installing libparted0debian1 as Depends of libparted0
  Installing libbluetooth3 as Depends of bluez
  Installing libmpeg4ip-0 as Depends of libmpeg4ip-dev
  Installing libsyncdaemon-1.0-1 as Depends of ubuntuone-client-gnome
  Installing libgutenprint2 as Depends of cups-driver-gutenprint
  Installing gnome-terminal-data as Depends of gnome-terminal
  Installing e2fslibs as PreDepends of e2fsprogs
  Installing grub-common as Depends of grub-pc
  Installing baobab as Depends of gnome-utils
    Installing gnome-utils-common as Depends of baobab
  Installing gnome-dictionary as Depends of gnome-utils
  Installing gnome-screenshot as Depends of gnome-utils
  Installing gnome-search-tool as Depends of gnome-utils
  Installing gnome-system-log as Depends of gnome-utils
  Installing libboost-program-options1.42.0 as Depends of libakonadiprivate1
  Installing aptdaemon as Depends of software-center
  new important dependency: sessioninstaller
  Installing sessioninstaller as Recommends of software-center
  Installing libunistring0 as Depends of gettext
  Installing python-sip as Depends of python-qt4
  Installing at-spi as Depends of python-pyatspi
  new important dependency: gpg
  Installing libbrasero-media1 as Depends of rhythmbox-plugin-cdrecorder
    Installing libburn4 as Depends of libbrasero-media1
    Installing libisofs6 as Depends of libbrasero-media1
    Installing libpoppler7 as Depends of cups
    Installing cups-ppdc as Depends of cups
  Installing libdvbpsi6 as Depends of vlc-nox
  Installing libebml2 as Depends of vlc-nox
  Installing libmatroska2 as Depends of vlc-nox
  Installing libvlc5 as Depends of vlc-nox
    Installing libvlccore4 as Depends of libvlc5
      Installing vlc-data as Depends of libvlccore4
  Installing speech-dispatcher as Depends of python-speechd
  Installing python-gtk2 as Depends of python-glade2
  Installing libdrm-radeon1 as Depends of libdrm-dev
  Installing libkms1 as Depends of libdrm-dev
  Installing usb-creator-common as Depends of usb-creator-gtk
  Installing language-selector-common as Depends of language-selector
  Installing libavcodec-dev as Depends of libavformat-dev
    Installing libavutil-dev as Depends of libavcodec-dev
  Installing libgwibber0 as Depends of indicator-me
  Installing libxapian15 as Depends of python-xapian
  Installing liblouis2 as Depends of python-louis
  Installing python-cups as Depends of system-config-printer-common
  Installing librtmp0 as Depends of libavformat-extra-52
  Installing libavdevice52 as Depends of ffmpeg
  Installing libavfilter1 as Depends of ffmpeg
  Installing libbonobo2-common as Depends of libbonobo2-0
  Installing libevdocument3 as Depends of evince
    Installing libpoppler-glib5 as Depends of libevdocument3
    Installing libt1-5 as Depends of libevdocument3
  Installing libevview3 as Depends of evince
  Installing evince-common as Depends of evince
  Installing zlib1g as Depends of zlib1g-dev
  Installing libmission-control-plugins0 as Depends of telepathy-mission-control-5
  Installing libnetpbm10 as Depends of netpbm
  Installing libnice0 as Depends of telepathy-gabble
  Installing libdpkg-perl as Depends of dpkg-dev
  new important dependency: libalgorithm-merge-perl
  Installing libalgorithm-merge-perl as Recommends of dpkg-dev
    Installing libalgorithm-diff-perl as Depends of libalgorithm-merge-perl
  Installing libstreams0 as Depends of libstreamanalyzer0
  Installing libzbar0 as Depends of gstreamer0.10-plugins-bad
  Installing libsox1b as Depends of libsox-fmt-base
  Installing libdmapsharing2 as Depends of rhythmbox-plugins
  Installing libvala-0.10-0 as Depends of rhythmbox-plugins
  Installing libpackagekit-glib2-14 as Depends of packagekit
  Installing packagekit-backend-aptcc as Depends of packagekit
  previously satisfied important dependency on indicator-application
  Installing libgimp2.0 as Depends of gimp
    previously satisfied important dependency on gimp-data
    Installing gimp-data as Recommends of libgimp2.0
  Installing libva-x11-1 as Depends of vlc
  Installing libxcb-randr0 as Depends of vlc
  new important dependency: vlc-plugin-notify
  Installing vlc-plugin-notify as Recommends of vlc
  previously satisfied important dependency on vlc-plugin-pulse
  Installing vlc-plugin-pulse as Recommends of vlc
  Installing liba52-0.7.4 as Depends of liba52-0.7.4-dev
  Installing libakonadi-kabc4 as Depends of kdepimlibs5
  Installing libakonadi-kde4 as Depends of kdepimlibs5
  Installing libakonadi-kmime4 as Depends of kdepimlibs5
    Installing libkmime4 as Depends of libakonadi-kmime4
  Installing libgpgme++2 as Depends of kdepimlibs5
  Installing libkabc4 as Depends of kdepimlibs5
    Installing libkldap4 as Depends of libkabc4
    Installing libkresources4 as Depends of libkabc4
  Installing libkblog4 as Depends of kdepimlibs5
    Installing libkcal4 as Depends of libkblog4
      Installing libkpimutils4 as Depends of libkcal4
    Installing libkxmlrpcclient4 as Depends of libkblog4
    Installing libsyndication4 as Depends of libkblog4
  Installing libkholidays4 as Depends of kdepimlibs5
  Installing libkimap4 as Depends of kdepimlibs5
  Installing libkpimidentities4 as Depends of kdepimlibs5
    Installing libkpimtextedit4 as Depends of libkpimidentities4
  Installing libktnef4 as Depends of kdepimlibs5
  Installing libmailtransport4 as Depends of kdepimlibs5
  Installing libmicroblog4 as Depends of kdepimlibs5
  Installing libqgpgme1 as Depends of kdepimlibs5
  Installing kdepimlibs-kio-plugins as Depends of kdepimlibs5
  Installing libgl1-mesa-glx as Depends of libgl1-mesa-dev
  Installing gsfonts as Depends of ghostscript
  new important dependency: libmagickcore3-extra
  Installing libmagickcore3-extra as Recommends of imagemagick
    Installing libcdt4 as Depends of libmagickcore3-extra
    Installing libgraph4 as Depends of libmagickcore3-extra
    Installing libgvc5 as Depends of libmagickcore3-extra
      Installing libpathplan4 as Depends of libgvc5
      Installing libxdot4 as Depends of libgvc5
  Installing liboobs-1-5 as Depends of gnome-system-tools
  new important dependency: brasero-cdrkit
  Installing brasero-cdrkit as Recommends of brasero
  Installing python-papyon as Depends of telepathy-butterfly
  new important dependency: hwdata
  Installing hwdata as Recommends of libgnome-desktop-2-17
  Installing jackd2 as Depends of jackd
    Installing libjack-jackd2-0 as Depends of jackd2
    Installing jackd2-firewire as Recommends of jackd2
  Installing libavahi-common3 as Depends of libavahi-common-dev
  Installing libjpeg8 as Depends of libjpeg-progs
  Installing gnome-session-common as Depends of gnome-session
  Installing libntfs-3g79 as Depends of ntfs-3g
  new important dependency: usb-modeswitch
  Installing usb-modeswitch as Recommends of modemmanager
    Installing usb-modeswitch-data as Depends of usb-modeswitch
  Installing kdepim-runtime as Depends of python-kde4
    Installing libakonadi-kcal4 as Depends of kdepim-runtime
    Installing akonadi-server as Depends of kdepim-runtime
      Installing mysql-server-core-5.1 as Depends of akonadi-server
      Installing mysql-client-core-5.1 as Depends of akonadi-server
  Installing libmusicbrainz3-6 as Depends of sound-juicer
    Installing libdiscid0 as Depends of libmusicbrainz3-6
  Installing libgirepository1.0-1 as Depends of python-gobject
  Installing gir1.0-glib-2.0 as Depends of python-gobject
  new important dependency: python-gobject-cairo
  Installing python-gobject-cairo as Recommends of python-gobject
Starting
Starting 2
Investigating libc6
Package libc6 has broken Conflicts on libc6-i686
  Considering libc6-i686 -2 as a solution to libc6 13580
  Added libc6-i686 to the remove list
  Fixing libc6 via remove of libc6-i686
Investigating xserver-xorg-core
Package xserver-xorg-core has broken Breaks on xserver-xorg-video-6
  Considering xserver-xorg-video-tseng 2 as a solution to xserver-xorg-core 79
  Added xserver-xorg-video-tseng to the remove list
  Fixing xserver-xorg-core via remove of xserver-xorg-video-tseng
Investigating libjack-jackd2-0
Package libjack-jackd2-0 has broken Conflicts on libjack-0.116
  Considering libjack0 2 as a solution to libjack-jackd2-0 24
  Added libjack0 to the remove list
Package libjack-jackd2-0 has broken Conflicts on libjack0
  Considering libjack0 2 as a solution to libjack-jackd2-0 24
  Added libjack0 to the remove list
  Considering libjack0 2 as a solution to libjack-jackd2-0 24
  Fixing libjack-jackd2-0 via keep of libjack0
  Fixing libjack-jackd2-0 via remove of libjack0
Investigating libakonadi-kde4
Package libakonadi-kde4 has broken Conflicts on kdepimlibs-data
  Considering kdepimlibs-data -1 as a solution to libakonadi-kde4 12
  Added kdepimlibs-data to the remove list
  Fixing libakonadi-kde4 via remove of kdepimlibs-data
Investigating pm-utils
Package pm-utils has broken Conflicts on pm-utils-powersave-policy
  Considering pm-utils-powersave-policy -1 as a solution to pm-utils 10
  Added pm-utils-powersave-policy to the remove list
  Fixing pm-utils via remove of pm-utils-powersave-policy
Investigating xserver-xorg-video-all
Package xserver-xorg-video-all has broken Depends on xserver-xorg-video-tseng
  Considering xserver-xorg-video-tseng 2 as a solution to xserver-xorg-video-all 5
  Added xserver-xorg-video-tseng to the remove list
  Fixing xserver-xorg-video-all via keep of xserver-xorg-video-tseng
Investigating foomatic-db-compressed-ppds
Package foomatic-db-compressed-ppds has broken Conflicts on foomatic-db
  Considering foomatic-db 3 as a solution to foomatic-db-compressed-ppds 4
  Added foomatic-db to the remove list
  Considering foomatic-db 3 as a solution to foomatic-db-compressed-ppds 4
Package foomatic-db-compressed-ppds has broken Conflicts on foomatic-db-hpijs
  Considering foomatic-db 3 as a solution to foomatic-db-compressed-ppds 4
  Considering foomatic-db 3 as a solution to foomatic-db-compressed-ppds 4
  Added foomatic-db to the remove list
  Fixing foomatic-db-compressed-ppds via remove of foomatic-db
  Fixing foomatic-db-compressed-ppds via remove of foomatic-db
Investigating libcdt4
Package libcdt4 has broken Conflicts on libgraphviz4
  Considering libgraphviz4 1 as a solution to libcdt4 3
  Added libgraphviz4 to the remove list
  Fixing libcdt4 via remove of libgraphviz4
Investigating libept0
Package libept0 has broken Depends on libapt-pkg-libc6.10-6-4.8
  Considering apt 31 as a solution to libept0 3
  Removing libept0 rather than change libapt-pkg-libc6.10-6-4.8
 Try to Re-Instate xserver-xorg-video-tseng
Re-Instated xserver-xorg-video-tseng (11 vs 11)
Investigating fceux
Package fceux has broken Conflicts on gfceux
  Considering gfceux -1 as a solution to fceux 2
  Added gfceux to the remove list
  Fixing fceux via remove of gfceux
Investigating jackd2-firewire
Package jackd2-firewire has broken Conflicts on jackd-firewire
  Considering jackd-firewire -1 as a solution to jackd2-firewire 1
  Added jackd-firewire to the remove list
  Considering jackd1-firewire 0 as a solution to jackd2-firewire 1
  Fixing jackd2-firewire via remove of jackd-firewire
Investigating libvlccore2
Package libvlccore2 has broken Depends on vlc-data
  Considering vlc-data 6 as a solution to libvlccore2 1
  Removing libvlccore2 rather than change vlc-data
Investigating libbrasero-media0
Package libbrasero-media0 has broken Depends on brasero-common
  Considering brasero-common 16 as a solution to libbrasero-media0 -1
  Removing libbrasero-media0 rather than change brasero-common
Investigating mplayer-gui
Package mplayer-gui has broken Depends on libjack0
  Considering libjack0 2 as a solution to mplayer-gui -1
  Removing mplayer-gui rather than change libjack0
Investigating libmagickcore2-extra
Package libmagickcore2-extra has broken Depends on libgraphviz4
  Considering libgraphviz4 1 as a solution to libmagickcore2-extra -1
  Removing libmagickcore2-extra rather than change libgraphviz4
Investigating libvlc2
Package libvlc2 has broken Depends on libvlccore2
  Considering libvlccore2 1 as a solution to libvlc2 -1
  Removing libvlc2 rather than change libvlccore2
Investigating libavfilter0
Package libavfilter0 has broken Depends on libavcodec52
  Considering libavcodec52 20 as a solution to libavfilter0 -1
Package libavfilter0 has broken Depends on libavcodec-extra-52
  Considering libavcodec-extra-52 79 as a solution to libavfilter0 -1
  Or group remove for libavfilter0
Investigating libpackagekit-glib2-12
Package libpackagekit-glib2-12 has broken Depends on libapt-pkg-libc6.10-6-4.8
  Considering apt 31 as a solution to libpackagekit-glib2-12 -2
  Removing libpackagekit-glib2-12 rather than change libapt-pkg-libc6.10-6-4.8
Investigating libpackagekit-qt-12
Package libpackagekit-qt-12 has broken Depends on libapt-pkg-libc6.10-6-4.8
  Considering apt 31 as a solution to libpackagekit-qt-12 -2
  Removing libpackagekit-qt-12 rather than change libapt-pkg-libc6.10-6-4.8
Investigating xserver-xorg-core
Package xserver-xorg-core has broken Breaks on xserver-xorg-video-6
  Considering xserver-xorg-video-tseng 2 as a solution to xserver-xorg-core 79
  Added xserver-xorg-video-tseng to the remove list
  Fixing xserver-xorg-core via remove of xserver-xorg-video-tseng
Investigating xserver-xorg-video-all
Package xserver-xorg-video-all has broken Depends on xserver-xorg-video-tseng
  Considering xserver-xorg-video-tseng 2 as a solution to xserver-xorg-video-all 5
  Added xserver-xorg-video-tseng to the remove list
  Fixing xserver-xorg-video-all via keep of xserver-xorg-video-tseng
Investigating xserver-xorg-core
Package xserver-xorg-core has broken Breaks on xserver-xorg-video-6
  Considering xserver-xorg-video-tseng 2 as a solution to xserver-xorg-core 79
  Added xserver-xorg-video-tseng to the remove list
  Fixing xserver-xorg-core via remove of xserver-xorg-video-tseng
Investigating xserver-xorg-video-all
Package xserver-xorg-video-all has broken Depends on xserver-xorg-video-tseng
  Considering xserver-xorg-video-tseng 79 as a solution to xserver-xorg-video-all 5
  Removing xserver-xorg-video-all rather than change xserver-xorg-video-tseng
Investigating xserver-xorg-core
Package xserver-xorg-core has broken Breaks on xserver-xorg-video-6
  Considering xserver-xorg-video-tseng 79 as a solution to xserver-xorg-core 79
  Holding Back xserver-xorg-core rather than change xserver-xorg-video-6
Investigating xserver-xorg
Package xserver-xorg has broken Depends on xserver-xorg-core
  Considering xserver-xorg-core 79 as a solution to xserver-xorg 46
  Holding Back xserver-xorg rather than change xserver-xorg-core
Investigating xserver-xorg-input-evdev
Package xserver-xorg-input-evdev has broken Depends on xorg-input-abi-11.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-input-evdev 7
  Holding Back xserver-xorg-input-evdev rather than change xorg-input-abi-11.0
Investigating xserver-xorg-video-rendition
Package xserver-xorg-video-rendition has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-rendition 2
  Holding Back xserver-xorg-video-rendition rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-s3virge
Package xserver-xorg-video-s3virge has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-s3virge 2
  Holding Back xserver-xorg-video-s3virge rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-apm
Package xserver-xorg-video-apm has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-apm 2
  Holding Back xserver-xorg-video-apm rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-ark
Package xserver-xorg-video-ark has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-ark 2
  Holding Back xserver-xorg-video-ark rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-ati
Package xserver-xorg-video-ati has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-ati 2
  Holding Back xserver-xorg-video-ati rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-tdfx
Package xserver-xorg-video-tdfx has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-tdfx 2
  Holding Back xserver-xorg-video-tdfx rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-trident
Package xserver-xorg-video-trident has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-trident 2
  Holding Back xserver-xorg-video-trident rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-fbdev
Package xserver-xorg-video-fbdev has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-fbdev 2
  Holding Back xserver-xorg-video-fbdev rather than change xorg-video-abi-8.0
Investigating xserver-xorg-input-wacom
Package xserver-xorg-input-wacom has broken Depends on xorg-input-abi-11.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-input-wacom 2
  Holding Back xserver-xorg-input-wacom rather than change xorg-input-abi-11.0
Investigating xserver-xorg-video-mga
Package xserver-xorg-video-mga has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-mga 2
  Holding Back xserver-xorg-video-mga rather than change xorg-video-abi-8.0
Investigating xserver-xorg-input-vmmouse
Package xserver-xorg-input-vmmouse has broken Depends on xorg-input-abi-11.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-input-vmmouse 2
  Holding Back xserver-xorg-input-vmmouse rather than change xorg-input-abi-11.0
Investigating xserver-xorg-input-mouse
Package xserver-xorg-input-mouse has broken Depends on xorg-input-abi-11.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-input-mouse 2
  Holding Back xserver-xorg-input-mouse rather than change xorg-input-abi-11.0
Investigating xserver-xorg-video-r128
Package xserver-xorg-video-r128 has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-r128 2
  Holding Back xserver-xorg-video-r128 rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-openchrome
Package xserver-xorg-video-openchrome has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-openchrome 2
  Holding Back xserver-xorg-video-openchrome rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-vesa
Package xserver-xorg-video-vesa has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-vesa 2
  Holding Back xserver-xorg-video-vesa rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-siliconmotion
Package xserver-xorg-video-siliconmotion has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-siliconmotion 2
  Holding Back xserver-xorg-video-siliconmotion rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-mach64
Package xserver-xorg-video-mach64 has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-mach64 2
  Holding Back xserver-xorg-video-mach64 rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-sis
Package xserver-xorg-video-sis has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-sis 2
  Holding Back xserver-xorg-video-sis rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-s3
Package xserver-xorg-video-s3 has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-s3 2
  Holding Back xserver-xorg-video-s3 rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-nv
Package xserver-xorg-video-nv has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-nv 2
  Holding Back xserver-xorg-video-nv rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-savage
Package xserver-xorg-video-savage has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-savage 2
  Holding Back xserver-xorg-video-savage rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-vmware
Package xserver-xorg-video-vmware has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-vmware 2
  Holding Back xserver-xorg-video-vmware rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-i128
Package xserver-xorg-video-i128 has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-i128 2
  Holding Back xserver-xorg-video-i128 rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-neomagic
Package xserver-xorg-video-neomagic has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-neomagic 2
  Holding Back xserver-xorg-video-neomagic rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-chips
Package xserver-xorg-video-chips has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-chips 2
  Holding Back xserver-xorg-video-chips rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-voodoo
Package xserver-xorg-video-voodoo has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-voodoo 2
  Holding Back xserver-xorg-video-voodoo rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-geode
Package xserver-xorg-video-geode has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-geode 2
  Holding Back xserver-xorg-video-geode rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-i740
Package xserver-xorg-video-i740 has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-i740 2
  Holding Back xserver-xorg-video-i740 rather than change xorg-video-abi-8.0
Investigating xserver-xorg-input-synaptics
Package xserver-xorg-input-synaptics has broken Depends on xorg-input-abi-11.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-input-synaptics 2
  Holding Back xserver-xorg-input-synaptics rather than change xorg-input-abi-11.0
Investigating xserver-xorg-video-sisusb
Package xserver-xorg-video-sisusb has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-sisusb 2
  Holding Back xserver-xorg-video-sisusb rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-radeon
Package xserver-xorg-video-radeon has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-radeon 2
  Holding Back xserver-xorg-video-radeon rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-cirrus
Package xserver-xorg-video-cirrus has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-cirrus 2
  Holding Back xserver-xorg-video-cirrus rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-intel
Package xserver-xorg-video-intel has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-intel 2
  Holding Back xserver-xorg-video-intel rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-v4l
Package xserver-xorg-video-v4l has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-v4l 0
  Holding Back xserver-xorg-video-v4l rather than change xorg-video-abi-8.0
 Try to Re-Instate xserver-xorg-core
 Try to Re-Instate xserver-xorg
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 17
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
 Try to Re-Instate xserver-xorg-input-evdev
 Try to Re-Instate xserver-xorg-video-rendition
 Try to Re-Instate xserver-xorg-video-s3virge
 Try to Re-Instate xserver-xorg-video-apm
 Try to Re-Instate xserver-xorg-video-ark
 Try to Re-Instate xserver-xorg-video-ati
 Try to Re-Instate xserver-xorg-video-tdfx
 Try to Re-Instate xserver-xorg-video-trident
 Try to Re-Instate xserver-xorg-video-fbdev
 Try to Re-Instate xserver-xorg-input-wacom
 Try to Re-Instate xserver-xorg-video-mga
 Try to Re-Instate xserver-xorg-input-vmmouse
 Try to Re-Instate xserver-xorg-input-mouse
 Try to Re-Instate xserver-xorg-video-r128
 Try to Re-Instate xserver-xorg-video-openchrome
 Try to Re-Instate xserver-xorg-video-vesa
 Try to Re-Instate xserver-xorg-video-siliconmotion
 Try to Re-Instate xserver-xorg-video-mach64
 Try to Re-Instate xserver-xorg-video-sis
 Try to Re-Instate xserver-xorg-video-s3
 Try to Re-Instate xserver-xorg-video-nv
 Try to Re-Instate xserver-xorg-video-savage
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
 Try to Re-Instate xserver-xorg-video-vmware
 Try to Re-Instate xserver-xorg-video-i128
 Try to Re-Instate xserver-xorg-video-neomagic
 Try to Re-Instate xserver-xorg-video-chips
 Try to Re-Instate xserver-xorg-video-voodoo
 Try to Re-Instate xserver-xorg-video-geode
 Try to Re-Instate xserver-xorg-video-i740
 Try to Re-Instate xserver-xorg-input-synaptics
 Try to Re-Instate xserver-xorg-video-sisusb
 Try to Re-Instate xserver-xorg-video-radeon
 Try to Re-Instate xserver-xorg-video-cirrus
 Try to Re-Instate xserver-xorg-video-intel
 Try to Re-Instate xserver-xorg-video-v4l
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 17
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 17
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 17
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 17
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 17
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Done
```

And finally, contents of /var/log/dist-upgrade/lspci.txt:

```
00:00.0 RAM memory [0500]: nVidia Corporation MCP78S [GeForce 8200] Memory Controller [10de:0754] (rev a2)
00:01.0 ISA bridge [0601]: nVidia Corporation Device [10de:075e] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP78S [GeForce 8200] SMBus [10de:0752] (rev a1)
00:01.3 Co-processor [0b40]: nVidia Corporation MCP78S [GeForce 8200] Co-Processor [10de:0753] (rev a2)
00:01.4 RAM memory [0500]: nVidia Corporation MCP78S [GeForce 8200] Memory Controller [10de:0568] (rev a1)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller [10de:077b] (rev a1)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller [10de:077c] (rev a1)
00:04.0 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller [10de:077d] (rev a1)
00:04.1 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller [10de:077e] (rev a1)
00:06.0 IDE interface [0101]: nVidia Corporation MCP78S [GeForce 8200] IDE [10de:0759] (rev a1)
00:07.0 Audio device [0403]: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio [10de:0774] (rev a1)
00:08.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge [10de:075a] (rev a1)
00:09.0 IDE interface [0101]: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) [10de:0ad0] (rev a2)
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP77 Ethernet [10de:0760] (rev a2)
00:0b.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge [10de:0569] (rev a1)
00:14.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge [10de:077a] (rev a1)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration [1022:1300] (rev 40)
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map [1022:1301]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller [1022:1302]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control [1022:1303]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control [1022:1304]
02:00.0 VGA compatible controller [0300]: nVidia Corporation C77 [GeForce 8200M G] [10de:0845] (rev a2)
07:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
```
BUMPED

---

### Post by kslays on 2011-01-04
I also have the same problem.  I suspect it may be due to any one of the following:
* I installed libusb 1.0.8 from the 10.10 repository because 10.04 is only at libusb 1.0.6 and a cellphone app I have needs 10.0.8 (Heimdall, for flashing Samsung Android software).
* Adobe Software like Air, Flash, or Reader
* A Google package like Google Earth, Chrome, Talk, Picasa etc.
* System76 packages
* Dropbox
* Nvidia drivers
* Skype
* Tor (though I uninstalled it mostly I think)

I'll check back here after a while, and if there's no solution I'll try uninstalling them all one at a time.

---

### Post by Saptrans on 2011-01-05
> **couzin2000 said:**
> So do I, here's the complete error:



Here's the contents of /var/log/dist-upgrade/main.log:

```
2011-01-02 13:03:12,800 INFO Using config files '['./DistUpgrade.cfg']'
2011-01-02 13:03:12,800 INFO uname information: 'Linux sebastien-laptop 2.6.32-27-generic #49-Ubuntu SMP Wed Dec 1 23:52:12 UTC 2010 i686'
2011-01-02 13:03:12,801 INFO creating state file with '['tar', '-z', '-c', '-f', '/var/log/dist-upgrade/system_state.tar.gz', '/etc/apt/preferences.d/', '/etc/apt/sources.list', '/etc/apt/sources.list.d/', '/var/lib/dpkg/status']'
2011-01-02 13:03:12,993 INFO release-upgrader version '0.142.20' started
2011-01-02 13:03:13,228 DEBUG svg pixbuf loader failed (Error displaying image)
2011-01-02 13:03:13,317 DEBUG Using 'DistUpgradeViewGtk' view
2011-01-02 13:03:13,367 DEBUG aufsOptionsAndEnvironmentSetup()
2011-01-02 13:03:13,368 DEBUG using '/tmp/upgrade-rw-KdWg3R' as aufs_rw_dir
2011-01-02 13:03:13,369 DEBUG using '/tmp/upgrade-chroot-xw2nql' as aufs chroot dir
2011-01-02 13:03:13,369 DEBUG enable dpkg --force-overwrite
2011-01-02 13:03:13,444 DEBUG lsb-release: 'lucid'
2011-01-02 13:03:13,452 DEBUG who -m --ips: ''
2011-01-02 13:03:13,453 DEBUG _pythonSymlinkCheck run
2011-01-02 13:03:13,453 DEBUG openCache()
2011-01-02 13:03:14,206 DEBUG /openCache(), new cache size 30361
2011-01-02 13:03:14,207 DEBUG needServerMode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
2011-01-02 13:03:14,207 DEBUG checkViewDepends()
2011-01-02 13:03:14,207 DEBUG running doUpdate() (showErrors=False)
2011-01-02 13:03:15,207 DEBUG openCache()
2011-01-02 13:03:15,720 DEBUG /openCache(), new cache size 30361
2011-01-02 13:03:15,720 DEBUG doPostInitialUpdate
2011-01-02 13:03:15,721 DEBUG Plugin modules in ./plugins: dpkg_status_plugin.py langpack_manual_plugin.py deb_plugin.py remove_lilo_plugin.py kdelibs4to5_plugin.py
2011-01-02 13:03:15,721 DEBUG Loading module ./plugins/dpkg_status_plugin.py
2011-01-02 13:03:15,724 DEBUG Plugins in <module 'dpkg_status_plugin' from './plugins/dpkg_status_plugin.py'>: <class 'dpkg_status_plugin.DpkgStatusPlugin'>
2011-01-02 13:03:15,724 DEBUG Loading module ./plugins/langpack_manual_plugin.py
2011-01-02 13:03:15,726 DEBUG Plugins in <module 'langpack_manual_plugin' from './plugins/langpack_manual_plugin.py'>: <class 'langpack_manual_plugin.MarkLangpacksManuallyInstalledPlugin'>
2011-01-02 13:03:15,726 DEBUG Loading module ./plugins/deb_plugin.py
2011-01-02 13:03:15,727 DEBUG Plugins in <module 'deb_plugin' from './plugins/deb_plugin.py'>: <class 'deb_plugin.DebPlugin'>
2011-01-02 13:03:15,727 DEBUG Loading module ./plugins/remove_lilo_plugin.py
2011-01-02 13:03:15,728 DEBUG Plugins in <module 'remove_lilo_plugin' from './plugins/remove_lilo_plugin.py'>: <class 'remove_lilo_plugin.RemoveLiloPlugin'>
2011-01-02 13:03:15,728 DEBUG Loading module ./plugins/kdelibs4to5_plugin.py
2011-01-02 13:03:15,730 DEBUG Plugins in <module 'kdelibs4to5_plugin' from './plugins/kdelibs4to5_plugin.py'>: <class 'kdelibs4to5_plugin.Kdelibs4devToKdelibs5devPlugin'>
2011-01-02 13:03:15,730 DEBUG plugins for condition 'PostInitialUpdate' are '[]'
2011-01-02 13:03:15,730 DEBUG plugins for condition 'maverickPostInitialUpdate' are '[]'
2011-01-02 13:03:15,730 DEBUG plugins for condition 'from_lucidPostInitialUpdate' are '[]'
2011-01-02 13:03:20,079 DEBUG Foreign: xserver-xorg-video-intel xserver-xorg-video-ati virtualbox-3.2 deluge-common nvidia-173-modaliases acroread nvidia-current-modaliases adobe-flashplugin nvidia-current xserver-xorg-video-radeon libtorrent-rasterbar5 fglrx-modaliases nvidia-96-modaliases nvidia-settings nvidia-173 intel-gpu-tools deluge-gtk python-libtorrent
2011-01-02 13:03:20,080 DEBUG Obsolete: 
2011-01-02 13:03:20,081 DEBUG updateSourcesList()
2011-01-02 13:03:20,163 DEBUG rewriteSourcesList()
2011-01-02 13:03:20,167 DEBUG examining: 'deb http://ca.archive.ubuntu.com/ubuntu/ lucid main restricted'
2011-01-02 13:03:20,167 DEBUG entry 'deb http://ca.archive.ubuntu.com/ubuntu/ maverick main restricted' updated to new dist
2011-01-02 13:03:20,167 DEBUG examining: 'deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid main restricted'
2011-01-02 13:03:20,167 DEBUG entry 'deb-src http://ca.archive.ubuntu.com/ubuntu/ maverick main restricted' updated to new dist
2011-01-02 13:03:20,167 DEBUG examining: 'deb http://ca.archive.ubuntu.com/ubuntu/ lucid-updates main restricted'
2011-01-02 13:03:20,167 DEBUG entry 'deb http://ca.archive.ubuntu.com/ubuntu/ maverick-updates main restricted' updated to new dist
2011-01-02 13:03:20,167 DEBUG examining: 'deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid-updates main restricted'
2011-01-02 13:03:20,168 DEBUG entry 'deb-src http://ca.archive.ubuntu.com/ubuntu/ maverick-updates main restricted' updated to new dist
2011-01-02 13:03:20,168 DEBUG examining: 'deb http://ca.archive.ubuntu.com/ubuntu/ lucid universe'
2011-01-02 13:03:20,168 DEBUG entry 'deb http://ca.archive.ubuntu.com/ubuntu/ maverick universe' updated to new dist
2011-01-02 13:03:20,168 DEBUG examining: 'deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid universe'
2011-01-02 13:03:20,168 DEBUG entry 'deb-src http://ca.archive.ubuntu.com/ubuntu/ maverick universe' updated to new dist
2011-01-02 13:03:20,168 DEBUG examining: 'deb http://ca.archive.ubuntu.com/ubuntu/ lucid-updates universe'
2011-01-02 13:03:20,168 DEBUG entry 'deb http://ca.archive.ubuntu.com/ubuntu/ maverick-updates universe' updated to new dist
2011-01-02 13:03:20,168 DEBUG examining: 'deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid-updates universe'
2011-01-02 13:03:20,169 DEBUG entry 'deb-src http://ca.archive.ubuntu.com/ubuntu/ maverick-updates universe' updated to new dist
2011-01-02 13:03:20,169 DEBUG examining: 'deb http://ca.archive.ubuntu.com/ubuntu/ lucid multiverse'
2011-01-02 13:03:20,169 DEBUG entry 'deb http://ca.archive.ubuntu.com/ubuntu/ maverick multiverse' updated to new dist
2011-01-02 13:03:20,169 DEBUG examining: 'deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid multiverse'
2011-01-02 13:03:20,169 DEBUG entry 'deb-src http://ca.archive.ubuntu.com/ubuntu/ maverick multiverse' updated to new dist
2011-01-02 13:03:20,169 DEBUG examining: 'deb http://ca.archive.ubuntu.com/ubuntu/ lucid-updates multiverse'
2011-01-02 13:03:20,169 DEBUG entry 'deb http://ca.archive.ubuntu.com/ubuntu/ maverick-updates multiverse' updated to new dist
2011-01-02 13:03:20,169 DEBUG examining: 'deb-src http://ca.archive.ubuntu.com/ubuntu/ lucid-updates multiverse'
2011-01-02 13:03:20,170 DEBUG entry 'deb-src http://ca.archive.ubuntu.com/ubuntu/ maverick-updates multiverse' updated to new dist
2011-01-02 13:03:20,170 DEBUG examining: 'deb http://archive.canonical.com/ubuntu lucid partner'
2011-01-02 13:03:20,170 DEBUG entry 'deb http://archive.canonical.com/ubuntu maverick partner' updated to new dist
2011-01-02 13:03:20,170 DEBUG examining: 'deb-src http://archive.canonical.com/ubuntu lucid partner'
2011-01-02 13:03:20,170 DEBUG entry 'deb-src http://archive.canonical.com/ubuntu maverick partner' updated to new dist
2011-01-02 13:03:20,170 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu lucid-security main restricted'
2011-01-02 13:03:20,170 DEBUG entry 'deb http://security.ubuntu.com/ubuntu maverick-security main restricted' updated to new dist
2011-01-02 13:03:20,171 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted'
2011-01-02 13:03:20,171 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted' updated to new dist
2011-01-02 13:03:20,171 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu lucid-security universe'
2011-01-02 13:03:20,171 DEBUG entry 'deb http://security.ubuntu.com/ubuntu maverick-security universe' updated to new dist
2011-01-02 13:03:20,171 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu lucid-security universe'
2011-01-02 13:03:20,171 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu maverick-security universe' updated to new dist
2011-01-02 13:03:20,171 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu lucid-security multiverse'
2011-01-02 13:03:20,171 DEBUG entry 'deb http://security.ubuntu.com/ubuntu maverick-security multiverse' updated to new dist
2011-01-02 13:03:20,172 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse'
2011-01-02 13:03:20,172 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse' updated to new dist
2011-01-02 13:03:20,172 DEBUG examining: 'deb http://download.virtualbox.org/virtualbox/debian lucid non-free'
2011-01-02 13:03:20,177 DEBUG entry '# deb http://download.virtualbox.org/virtualbox/debian maverick non-free # disabled on upgrade to maverick' was disabled (unknown mirror)
2011-01-02 13:03:20,177 DEBUG examining: 'deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu lucid main'
2011-01-02 13:03:20,182 DEBUG entry '# deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu maverick main # disabled on upgrade to maverick' was disabled (unknown mirror)
2011-01-02 13:03:20,182 DEBUG examining: 'deb-src http://ppa.launchpad.net/deluge-team/ppa/ubuntu lucid main'
2011-01-02 13:03:20,187 DEBUG entry '# deb-src http://ppa.launchpad.net/deluge-team/ppa/ubuntu maverick main # disabled on upgrade to maverick' was disabled (unknown mirror)
2011-01-02 13:03:20,187 DEBUG examining: 'deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu lucid main'
2011-01-02 13:03:20,192 DEBUG entry '# deb http://ppa.launchpad.net/deluge-team/ppa/ubuntu maverick main # disabled on upgrade to maverick' was disabled (unknown mirror)
2011-01-02 13:03:20,192 DEBUG examining: 'deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu lucid main'
2011-01-02 13:03:20,197 DEBUG entry '# deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu maverick main # disabled on upgrade to maverick' was disabled (unknown mirror)
2011-01-02 13:03:22,949 DEBUG running doUpdate() (showErrors=True)
2011-01-02 13:03:58,127 DEBUG openCache()
2011-01-02 13:03:58,128 DEBUG failed to SystemUnLock() (E:Not locked) 
2011-01-02 13:04:01,330 DEBUG /openCache(), new cache size 32318
2011-01-02 13:04:01,330 DEBUG needServerMode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
```

Here's also the contents of /var/log/dist-upgrade/apt.log:

```
Log time: 2011-01-02 13:03:13.977003
Log time: 2011-01-02 13:03:15.712456
Log time: 2011-01-02 13:04:01.316633
  Installing xserver-xorg-core as Depends of xserver-xorg
    Installing xserver-common as Depends of xserver-xorg-core
    Installing libxfont1 as Depends of xserver-xorg-core
      Installing libdrm-intel1 as Depends of xserver-xorg-video-intel
      Installing libdrm-nouveau1 as Depends of xserver-xorg-video-nouveau
  Installing gconf2 as Depends of ubuntuone-client
    Installing libgconf2-4 as Depends of gconf2
      Installing libglib2.0-0 as Depends of libgconf2-4
        new important dependency: libdconf0
        Installing libdconf0 as Recommends of libglib2.0-0
      Installing gconf2-common as Depends of libgconf2-4
  Installing python-ubuntuone-client as Depends of ubuntuone-client
    Installing python-ubuntuone-storageprotocol as Depends of python-ubuntuone-client
    Installing python-libproxy as Depends of python-ubuntuone-client
  Installing ubuntu-sso-client as Depends of ubuntuone-client
    Installing dpkg as PreDepends of ubuntu-sso-client
  Installing libappindicator1 as Depends of policykit-1-gnome
    Installing libdbus-glib-1-2 as Depends of libappindicator1
    Installing libdbusmenu-glib1 as Depends of libappindicator1
    Installing libdbusmenu-gtk1 as Depends of libappindicator1
      Installing libgdk-pixbuf2.0-0 as Depends of libdbusmenu-gtk1
    Installing libindicator1 as Depends of libappindicator1
    Installing indicator-application as Recommends of libappindicator1
  Installing libc6 as Depends of mono-2.0-gac
    Installing libc-bin as Depends of libc6
  Installing libmono-corlib2.0-cil as Depends of mono-2.0-gac
    Installing mono-runtime as Depends of libmono-corlib2.0-cil
      Installing mono-gac as Depends of mono-runtime
  Installing libmono-security2.0-cil as Depends of mono-2.0-gac
    Installing libmono-system2.0-cil as Depends of libmono-security2.0-cil
  Installing libcairo2 as Depends of f-spot
    Installing libpixman-1-0 as Depends of libcairo2
  Installing libgtk2.0-0 as Depends of f-spot
  Installing libglib2.0-cil as Depends of f-spot
  Installing libgtk2.0-cil as Depends of f-spot
  Installing libmono-simd2.0-cil as Depends of f-spot
  Installing libmono-system-data2.0-cil as Depends of f-spot
    Installing libmono-data-tds2.0-cil as Depends of libmono-system-data2.0-cil
    Installing libmono-wcf3.0-cil as Depends of libmono-system-data2.0-cil
      Installing libmono-system-messaging2.0-cil as Depends of libmono-wcf3.0-cil
        Installing libmono-messaging2.0-cil as Depends of libmono-system-messaging2.0-cil
  Installing libsqlite3-0 as Depends of f-spot
  Installing libgstreamer0.10-0 as Depends of gstreamer0.10-alsa
  Installing libgstreamer-plugins-base0.10-0 as Depends of gstreamer0.10-alsa
  Installing libsdl1.2debian-alsa as Depends of libsdl1.2debian
  Installing libkrb5support0 as Depends of libkrb5-3
  Installing libgnomekbd-common as Depends of libgnomekbd4
  Installing perl as Depends of libpurple0
    Installing perl-base as Depends of perl
    Installing perl-modules as Depends of perl
  Installing python as Depends of python-twisted-names
    Installing python2.6 as Depends of python
      Installing python2.6-minimal as Depends of python2.6
        Installing libssl0.9.8 as Depends of python2.6-minimal
      Installing libncursesw5 as Depends of python2.6
    Installing python-minimal as Depends of python
  Installing python-twisted-core as Depends of python-twisted-names
    Installing python-twisted-bin as Depends of python-twisted-core
  Installing syslinux-common as Depends of syslinux
    Installing libcrypt-passwdmd5-perl as Recommends of syslinux-common
    Installing libdigest-sha1-perl as Recommends of syslinux-common
  Installing libavutil-extra-50 as Depends of libpostproc-extra-51
  Installing gcc-4.5-base as Depends of libstdc++6
  Installing libkdecore5 as Depends of kubuntu-debug-installer
    Installing liblzma2 as Depends of libkdecore5
    Installing libqt4-dbus as Depends of libkdecore5
      Installing libqt4-xml as Depends of libqt4-dbus
        Installing libqtcore4 as Depends of libqt4-xml
    Installing libqt4-network as Depends of libkdecore5
  Installing libkdeui5 as Depends of kubuntu-debug-installer
    Installing libdbusmenu-qt2 as Depends of libkdeui5
      Installing libqtgui4 as Depends of libdbusmenu-qt2
        Installing libmng1 as Depends of libqtgui4
    Installing libqt4-svg as Depends of libkdeui5
    Installing kdelibs5-data as Recommends of libkdeui5
  Installing libqapt1 as Depends of kubuntu-debug-installer
    Installing apt as Depends of libqapt1
      new important dependency: gpg
  Installing qapt-batch as Depends of kubuntu-debug-installer
    Installing libqapt-runtime as Depends of qapt-batch
  Installing libappindicator0.1-cil as Depends of tomboy
  Installing libbz2-1.0 as Depends of bzip2
  Installing libedataserver1.2-13 as Depends of evolution-webcal
  Installing libespeak1 as Depends of espeak
    Installing libportaudio2 as Depends of libespeak1
      Installing libjack-jackd2-0 as Depends of libportaudio2
    Installing espeak-data as Depends of libespeak1
  Installing libnih1 as Depends of libnih-dbus1
  Installing computer-janitor as Depends of computer-janitor-gtk
    Installing python-argparse as Depends of computer-janitor
  Installing openoffice.org-core as Depends of openoffice.org-gnome
    Installing openoffice.org-common as Depends of openoffice.org-core
    Installing libhunspell-1.2-0 as Depends of openoffice.org-core
    Installing libneon27-gnutls as Depends of openoffice.org-core
    Installing ure as Depends of openoffice.org-core
      Installing uno-libs3 as Depends of ure
  Installing libutouch-grail1 as Depends of xserver-xorg-input-evdev
    Installing libmtdev1 as Depends of libutouch-grail1
  Installing libprotobuf6 as Depends of libcompizconfig0
  Installing compiz-core as Depends of libcompizconfig0
    previously satisfied important dependency on compiz-plugins
    Installing compiz-plugins as Recommends of compiz-core
  Installing update-manager-core as Depends of update-manager
  Installing openoffice.org-base-core as Depends of openoffice.org-writer
  Installing libqtassistantclient4 as Depends of libqt4-assistant
  Installing python-gconf as Depends of python-gnome2
  Installing python-libtorrent as Depends of miro
    Installing libboost-filesystem1.42.0 as Depends of python-libtorrent
      Installing libboost-system1.42.0 as Depends of libboost-filesystem1.42.0
    Installing libboost-python1.42.0 as Depends of python-libtorrent
    Installing libtorrent-rasterbar6 as Depends of python-libtorrent
      Installing libboost-thread1.42.0 as Depends of libtorrent-rasterbar6
      Installing libgeoip1 as Depends of libtorrent-rasterbar6
  Installing miro-data as Depends of miro
  Installing gnome-media-common as Depends of gnome-media
  Installing nautilus-data as Depends of nautilus
  Installing gnome-games-common as Depends of aisleriot
  Installing libgnome2-common as Depends of libgnome2-0
  Installing libusb-1.0-0 as Depends of libdc1394-22
  Installing libbind9-60 as Depends of bind9-host
    Installing libdns66 as Depends of libbind9-60
  Installing libisc60 as Depends of bind9-host
  Installing libisccfg60 as Depends of bind9-host
  Installing liblwres60 as Depends of bind9-host
  Installing openoffice.org-draw as Depends of openoffice.org-impress
  Installing librasqal2 as Depends of slv2-jack
  Installing language-pack-en as Depends of language-pack-en-base
  Installing gvfs as Depends of gvfs-fuse
  Installing erlang-base as Depends of erlang-inets
    previously satisfied important dependency on erlang-crypto
    Installing erlang-crypto as Recommends of erlang-base
    previously satisfied important dependency on erlang-syntax-tools
    Installing erlang-syntax-tools as Recommends of erlang-base
  Installing erlang-mnesia as Depends of erlang-inets
  Installing erlang-runtime-tools as Depends of erlang-inets
  Installing erlang-ssl as Depends of erlang-inets
    Installing erlang-public-key as Depends of erlang-ssl
  Installing python-markupsafe as Depends of python-mako
  Installing linux-headers-2.6.35-24-generic as Depends of linux-headers-generic
    Installing linux-headers-2.6.35-24 as Depends of linux-headers-2.6.35-24-generic
  Installing libaspell15 as Depends of aspell
  Installing dhcp3-common as Depends of dhcp3-client
  Installing libdirectfb-1.2-9 as Depends of libxine1-x
  Installing libxine1-bin as Depends of libxine1-x
  Installing libsnmp-base as Depends of libsnmp15
  Installing libkde3support4 as Depends of libk3b6
    Installing libkfile4 as Depends of libkde3support4
      Installing libkio5 as Depends of libkfile4
        Installing libnepomuk4 as Depends of libkio5
          Installing libsoprano4 as Depends of libnepomuk4
            Installing soprano-daemon as Depends of libsoprano4
        Installing libsolid4 as Depends of libkio5
        Installing kdelibs5-plugins as Recommends of libkio5
          Installing libkatepartinterfaces4 as Depends of kdelibs5-plugins
            Installing libkparts4 as Depends of libkatepartinterfaces4
            Installing libktexteditor4 as Depends of libkatepartinterfaces4
            Installing libkutils4 as Depends of libkatepartinterfaces4
            Installing libqt4-script as Depends of libkatepartinterfaces4
          Installing libkhtml5 as Depends of kdelibs5-plugins
            Installing libkjsapi4 as Depends of libkhtml5
            Installing libphonon4 as Depends of libkhtml5
          Installing libkjsembed4 as Depends of kdelibs5-plugins
          Installing libkntlm4 as Depends of kdelibs5-plugins
          Installing libkrosscore4 as Depends of kdelibs5-plugins
          Installing libkrossui4 as Depends of kdelibs5-plugins
          Installing kdoctools as Depends of kdelibs5-plugins
          Installing kdelibs-bin as Depends of kdelibs5-plugins
    Installing libkpty4 as Depends of libkde3support4
      Installing libutempter0 as Depends of libkpty4
    Installing libqt4-qt3support as Depends of libkde3support4
      Installing libqt4-designer as Depends of libqt4-qt3support
      Installing libqt4-sql as Depends of libqt4-qt3support
  Installing libmpcdec6 as Depends of libk3b6
  Installing libdjvulibre-text as Depends of libdjvulibre21
  Installing libnotify1 as Depends of gnome-settings-daemon
  Installing libmagickcore3 as Depends of obex-data-server
    Installing liblqr-1-0 as Depends of libmagickcore3
  Installing libmagickwand3 as Depends of obex-data-server
  Installing libdebconf-kde0 as Depends of kpackagekit
  Installing libpackagekit-qt-14 as Depends of kpackagekit
  Installing libao4 as Depends of vorbis-tools
    Installing libao-common as Depends of libao4
  Installing libglib2.0-bin as Depends of libglib2.0-dev
  Installing libcamel1.2-14 as Depends of evolution-indicator
  Installing libevolution as Depends of evolution-indicator
    Installing libebackend1.2-0 as Depends of libevolution
    Installing libebook1.2-9 as Depends of libevolution
    Installing libecal1.2-7 as Depends of libevolution
    Installing libedataserverui1.2-8 as Depends of libevolution
    Installing libgdata-google1.2-1 as Depends of libevolution
      Installing libgdata1.2-1 as Depends of libgdata-google1.2-1
    Installing libgtkhtml-editor0 as Depends of libevolution
      Installing libgtkhtml3.14-19 as Depends of libgtkhtml-editor0
      Installing libgtkhtml-editor-common as Depends of libgtkhtml-editor0
  Installing samba-common as Depends of smbclient
  Installing libnewt0.52 as Depends of whiptail
  Installing libvorbis0a as Depends of libvorbisfile3
  Installing plymouth as Depends of plymouth-x11
  Installing libgucharmap7 as Depends of gucharmap
  Installing libatspi1.0-0 as Depends of brltty-x11
  Installing brltty as Depends of brltty-x11
  Installing libnm-glib2 as Depends of network-manager
  Installing libnm-util1 as Depends of network-manager
  Installing libavahi-core7 as Depends of avahi-daemon
  Installing gdebi-core as Depends of gdebi
    Installing python-apt as Depends of gdebi-core
      Installing apt-utils as Depends of python-apt
  Installing libimobiledevice1 as Depends of upower
  Installing libupower-glib1 as Depends of upower
  Installing libedata-book1.2-2 as Depends of evolution-exchange
  Installing libedata-cal1.2-7 as Depends of evolution-exchange
  Installing libegroupwise1.2-13 as Depends of evolution-exchange
  Installing evolution as Depends of evolution-exchange
    Installing evolution-data-server as Depends of evolution
      Installing evolution-data-server-common as Depends of evolution-data-server
  Installing libclutter-1.0-0 as Depends of quadrapassel
  Installing libpulse0 as Depends of libpulse-dev
  Installing libpulse-mainloop-glib0 as Depends of libpulse-dev
  Installing libpulse-browse0 as Depends of libpulse-dev
  Installing xul-ext-ubufox as Depends of ubufox
  Installing libgnome-bluetooth8 as Depends of gnome-bluetooth
  Installing python-aptdaemon as Depends of python-aptdaemon-gtk
  Installing gtkpod-data as Depends of gtkpod
  Installing libgladeui-1-9 as Depends of libgnome-media0
  Installing libavidemux0 as Depends of avidemux
  Installing gcc-4.4-base as Depends of g++-4.4
  Installing gcc-4.4 as Depends of g++-4.4
    Installing cpp-4.4 as Depends of gcc-4.4
      Installing libmpfr4 as Depends of cpp-4.4
    Installing binutils as Depends of gcc-4.4
    Installing libgcc1 as Depends of gcc-4.4
    Installing libgomp1 as Depends of gcc-4.4
  Installing libstdc++6-4.4-dev as Depends of g++-4.4
  Installing libjack0 as Depends of mplayer-gui
  Installing libwxbase2.8-0 as Depends of libwxgtk2.8-0
  Installing libglibmm-2.4-1c2a as Depends of gparted
  Installing totem as Depends of totem-plugins
    Installing libtotem-plparser17 as Depends of totem
    Installing gstreamer0.10-plugins-base as Depends of totem
    Installing totem-common as Depends of totem
    previously satisfied important dependency on totem-mozilla
    Installing totem-mozilla as Recommends of totem
  Installing libgdata7 as Depends of totem-plugins
  Installing libattica0 as Depends of kdebase-runtime
  Installing libkdesu5 as Depends of kdebase-runtime
  Installing libkdnssd4 as Depends of kdebase-runtime
  Installing libkmediaplayer4 as Depends of kdebase-runtime
  Installing libknewstuff3-4 as Depends of kdebase-runtime
  Installing libknotifyconfig4 as Depends of kdebase-runtime
  Installing libnepomukquery4a as Depends of kdebase-runtime
  Installing libplasma3 as Depends of kdebase-runtime
    Installing libkdewebkit5 as Depends of libplasma3
      Installing libqtwebkit4 as Depends of libkdewebkit5
    Installing libthreadweaver4 as Depends of libplasma3
  Installing kdebase-runtime-data as Depends of kdebase-runtime
  Installing plasma-scriptengine-javascript as Depends of kdebase-runtime
  new important dependency: virtuoso-minimal
  Installing virtuoso-minimal as Recommends of kdebase-runtime
    Installing virtuoso-opensource-6.1-bin as Depends of virtuoso-minimal
    Installing libvirtodbc0 as Depends of virtuoso-minimal
      Installing virtuoso-opensource-6.1-common as Depends of libvirtodbc0
      Installing odbcinst as Depends of libvirtodbc0
        Installing odbcinst1debian2 as Depends of odbcinst
  Installing linux-image-2.6.35-24-generic as Depends of linux-image-generic
  Setting NOT as auto-installed (direct Depends of pkg in APT::Never-MarkAuto-Sections)
  Installing audacity-data as Depends of audacity
  previously satisfied important dependency on libavcodec52
  Installing libavcodec52 as Recommends of audacity
    Installing libva1 as Depends of libavcodec52
    Installing libvpx0 as Depends of libavcodec52
  previously satisfied important dependency on libavformat52
  Installing libavformat52 as Recommends of audacity
  Installing libgssdp-1.0-2 as Depends of libgstfarsight0.10-0
  Installing libgupnp-1.0-3 as Depends of libgstfarsight0.10-0
  Installing libgupnp-igd-1.0-3 as Depends of libgstfarsight0.10-0
  Installing libmodplug1 as Depends of libxine1-misc-plugins
  Installing ncurses-bin as Depends of libncursesw5-dev
  Installing libibus2 as Depends of ibus-gtk
  Installing smplayer as Depends of smplayer-translations
  Installing libkimproxy4 as Depends of kdelibs5
  Installing libknewstuff2-4 as Depends of kdelibs5
  Installing python-gmenu as Depends of gnome-menus
  Installing libhpmud0 as Depends of hpijs
  Installing libprotoc6 as Depends of protobuf-compiler
  Installing cups-common as Depends of cups-client
  Installing libx264-98 as Depends of avidemux-plugins-common
  Installing libswscale0 as Depends of mplayer
  Installing libvdpau1 as Depends of mplayer
  Installing language-pack-gnome-en as Depends of language-pack-gnome-en-base
  Installing libgnome-window-settings1 as Depends of gnome-control-center
  Installing capplets-data as Depends of gnome-control-center
  Installing libsasl2-2 as Depends of libsasl2-modules
  Installing libsane-hpaio as Depends of hplip
  Installing hplip-data as Depends of hplip
  Installing mono-csharp-shell as Depends of gbrainy
    Installing libmono-management2.0-cil as Depends of mono-csharp-shell
    Installing mono-gmcs as Depends of mono-csharp-shell
  Installing foomatic-db-compressed-ppds as Depends of ubuntu-desktop
  Setting NOT as auto-installed (direct Depends of pkg in APT::Never-MarkAuto-Sections)
  Installing ubuntu-extras-keyring as Depends of ubuntu-desktop
  Setting NOT as auto-installed (direct Depends of pkg in APT::Never-MarkAuto-Sections)
  new important dependency: ibus-pinyin
  Installing ibus-pinyin as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
    Installing ibus-pinyin-db-open-phrase as Depends of ibus-pinyin
      Installing pinyin-database as Depends of ibus-pinyin-db-open-phrase
    Installing libopencc1 as Depends of ibus-pinyin
    Installing ibus as Depends of ibus-pinyin
      Installing python-ibus as Depends of ibus
  new important dependency: ibus-pinyin-db-android
  Installing ibus-pinyin-db-android as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
  new important dependency: shotwell
  Installing shotwell as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
    Installing libgee2 as Depends of shotwell
    Installing libgexiv2-0 as Depends of shotwell
  new important dependency: ttf-ubuntu-font-family
  Installing ttf-ubuntu-font-family as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
  Installing libboost-iostreams1.42.0 as Depends of aptitude
  Installing libept1 as Depends of aptitude
  Installing libfolks-telepathy0 as Depends of empathy
    Installing libfolks0 as Depends of libfolks-telepathy0
  Installing libtelepathy-logger1 as Depends of empathy
  Installing empathy-common as Depends of empathy
  Installing gnome-icon-theme as Depends of empathy
  Installing telepathy-logger as Depends of empathy
  Installing python2.6-dev as Depends of python-dev
    Installing libpython2.6 as Depends of python2.6-dev
    Installing libssl-dev as Depends of python2.6-dev
  Installing gtk2-engines-murrine as Depends of light-themes
  Installing libvte9 as Depends of vinagre
  Installing libxdmcp6 as Depends of libxdmcp-dev
  Installing libsysfs2 as Depends of libsysfs-dev
  Installing cpp as Depends of g++
  Installing gcc as Depends of g++
  Installing libavahi-client3 as Depends of libavahi-client-dev
  Installing libparted0debian1 as Depends of libparted0
  Installing libbluetooth3 as Depends of bluez
  Installing libmpeg4ip-0 as Depends of libmpeg4ip-dev
  Installing libsyncdaemon-1.0-1 as Depends of ubuntuone-client-gnome
  Installing libgutenprint2 as Depends of cups-driver-gutenprint
  Installing gnome-terminal-data as Depends of gnome-terminal
  Installing e2fslibs as PreDepends of e2fsprogs
  Installing grub-common as Depends of grub-pc
  Installing baobab as Depends of gnome-utils
    Installing gnome-utils-common as Depends of baobab
  Installing gnome-dictionary as Depends of gnome-utils
  Installing gnome-screenshot as Depends of gnome-utils
  Installing gnome-search-tool as Depends of gnome-utils
  Installing gnome-system-log as Depends of gnome-utils
  Installing libboost-program-options1.42.0 as Depends of libakonadiprivate1
  Installing aptdaemon as Depends of software-center
  new important dependency: sessioninstaller
  Installing sessioninstaller as Recommends of software-center
  Installing libunistring0 as Depends of gettext
  Installing python-sip as Depends of python-qt4
  Installing at-spi as Depends of python-pyatspi
  new important dependency: gpg
  Installing libbrasero-media1 as Depends of rhythmbox-plugin-cdrecorder
    Installing libburn4 as Depends of libbrasero-media1
    Installing libisofs6 as Depends of libbrasero-media1
    Installing libpoppler7 as Depends of cups
    Installing cups-ppdc as Depends of cups
  Installing libdvbpsi6 as Depends of vlc-nox
  Installing libebml2 as Depends of vlc-nox
  Installing libmatroska2 as Depends of vlc-nox
  Installing libvlc5 as Depends of vlc-nox
    Installing libvlccore4 as Depends of libvlc5
      Installing vlc-data as Depends of libvlccore4
  Installing speech-dispatcher as Depends of python-speechd
  Installing python-gtk2 as Depends of python-glade2
  Installing libdrm-radeon1 as Depends of libdrm-dev
  Installing libkms1 as Depends of libdrm-dev
  Installing usb-creator-common as Depends of usb-creator-gtk
  Installing language-selector-common as Depends of language-selector
  Installing libavcodec-dev as Depends of libavformat-dev
    Installing libavutil-dev as Depends of libavcodec-dev
  Installing libgwibber0 as Depends of indicator-me
  Installing libxapian15 as Depends of python-xapian
  Installing liblouis2 as Depends of python-louis
  Installing python-cups as Depends of system-config-printer-common
  Installing librtmp0 as Depends of libavformat-extra-52
  Installing libavdevice52 as Depends of ffmpeg
  Installing libavfilter1 as Depends of ffmpeg
  Installing libbonobo2-common as Depends of libbonobo2-0
  Installing libevdocument3 as Depends of evince
    Installing libpoppler-glib5 as Depends of libevdocument3
    Installing libt1-5 as Depends of libevdocument3
  Installing libevview3 as Depends of evince
  Installing evince-common as Depends of evince
  Installing zlib1g as Depends of zlib1g-dev
  Installing libmission-control-plugins0 as Depends of telepathy-mission-control-5
  Installing libnetpbm10 as Depends of netpbm
  Installing libnice0 as Depends of telepathy-gabble
  Installing libdpkg-perl as Depends of dpkg-dev
  new important dependency: libalgorithm-merge-perl
  Installing libalgorithm-merge-perl as Recommends of dpkg-dev
    Installing libalgorithm-diff-perl as Depends of libalgorithm-merge-perl
  Installing libstreams0 as Depends of libstreamanalyzer0
  Installing libzbar0 as Depends of gstreamer0.10-plugins-bad
  Installing libsox1b as Depends of libsox-fmt-base
  Installing libdmapsharing2 as Depends of rhythmbox-plugins
  Installing libvala-0.10-0 as Depends of rhythmbox-plugins
  Installing libpackagekit-glib2-14 as Depends of packagekit
  Installing packagekit-backend-aptcc as Depends of packagekit
  previously satisfied important dependency on indicator-application
  Installing libgimp2.0 as Depends of gimp
    previously satisfied important dependency on gimp-data
    Installing gimp-data as Recommends of libgimp2.0
  Installing libva-x11-1 as Depends of vlc
  Installing libxcb-randr0 as Depends of vlc
  new important dependency: vlc-plugin-notify
  Installing vlc-plugin-notify as Recommends of vlc
  previously satisfied important dependency on vlc-plugin-pulse
  Installing vlc-plugin-pulse as Recommends of vlc
  Installing liba52-0.7.4 as Depends of liba52-0.7.4-dev
  Installing libakonadi-kabc4 as Depends of kdepimlibs5
  Installing libakonadi-kde4 as Depends of kdepimlibs5
  Installing libakonadi-kmime4 as Depends of kdepimlibs5
    Installing libkmime4 as Depends of libakonadi-kmime4
  Installing libgpgme++2 as Depends of kdepimlibs5
  Installing libkabc4 as Depends of kdepimlibs5
    Installing libkldap4 as Depends of libkabc4
    Installing libkresources4 as Depends of libkabc4
  Installing libkblog4 as Depends of kdepimlibs5
    Installing libkcal4 as Depends of libkblog4
      Installing libkpimutils4 as Depends of libkcal4
    Installing libkxmlrpcclient4 as Depends of libkblog4
    Installing libsyndication4 as Depends of libkblog4
  Installing libkholidays4 as Depends of kdepimlibs5
  Installing libkimap4 as Depends of kdepimlibs5
  Installing libkpimidentities4 as Depends of kdepimlibs5
    Installing libkpimtextedit4 as Depends of libkpimidentities4
  Installing libktnef4 as Depends of kdepimlibs5
  Installing libmailtransport4 as Depends of kdepimlibs5
  Installing libmicroblog4 as Depends of kdepimlibs5
  Installing libqgpgme1 as Depends of kdepimlibs5
  Installing kdepimlibs-kio-plugins as Depends of kdepimlibs5
  Installing libgl1-mesa-glx as Depends of libgl1-mesa-dev
  Installing gsfonts as Depends of ghostscript
  new important dependency: libmagickcore3-extra
  Installing libmagickcore3-extra as Recommends of imagemagick
    Installing libcdt4 as Depends of libmagickcore3-extra
    Installing libgraph4 as Depends of libmagickcore3-extra
    Installing libgvc5 as Depends of libmagickcore3-extra
      Installing libpathplan4 as Depends of libgvc5
      Installing libxdot4 as Depends of libgvc5
  Installing liboobs-1-5 as Depends of gnome-system-tools
  new important dependency: brasero-cdrkit
  Installing brasero-cdrkit as Recommends of brasero
  Installing python-papyon as Depends of telepathy-butterfly
  new important dependency: hwdata
  Installing hwdata as Recommends of libgnome-desktop-2-17
  Installing jackd2 as Depends of jackd
    Installing libjack-jackd2-0 as Depends of jackd2
    Installing jackd2-firewire as Recommends of jackd2
  Installing libavahi-common3 as Depends of libavahi-common-dev
  Installing libjpeg8 as Depends of libjpeg-progs
  Installing gnome-session-common as Depends of gnome-session
  Installing libntfs-3g79 as Depends of ntfs-3g
  new important dependency: usb-modeswitch
  Installing usb-modeswitch as Recommends of modemmanager
    Installing usb-modeswitch-data as Depends of usb-modeswitch
  Installing kdepim-runtime as Depends of python-kde4
    Installing libakonadi-kcal4 as Depends of kdepim-runtime
    Installing akonadi-server as Depends of kdepim-runtime
      Installing mysql-server-core-5.1 as Depends of akonadi-server
      Installing mysql-client-core-5.1 as Depends of akonadi-server
  Installing libmusicbrainz3-6 as Depends of sound-juicer
    Installing libdiscid0 as Depends of libmusicbrainz3-6
  Installing libgirepository1.0-1 as Depends of python-gobject
  Installing gir1.0-glib-2.0 as Depends of python-gobject
  new important dependency: python-gobject-cairo
  Installing python-gobject-cairo as Recommends of python-gobject
Starting
Starting 2
Investigating libc6
Package libc6 has broken Conflicts on libc6-i686
  Considering libc6-i686 -2 as a solution to libc6 13580
  Added libc6-i686 to the remove list
  Fixing libc6 via remove of libc6-i686
Investigating xserver-xorg-core
Package xserver-xorg-core has broken Breaks on xserver-xorg-video-6
  Considering xserver-xorg-video-tseng 2 as a solution to xserver-xorg-core 79
  Added xserver-xorg-video-tseng to the remove list
  Fixing xserver-xorg-core via remove of xserver-xorg-video-tseng
Investigating libjack-jackd2-0
Package libjack-jackd2-0 has broken Conflicts on libjack-0.116
  Considering libjack0 2 as a solution to libjack-jackd2-0 24
  Added libjack0 to the remove list
Package libjack-jackd2-0 has broken Conflicts on libjack0
  Considering libjack0 2 as a solution to libjack-jackd2-0 24
  Added libjack0 to the remove list
  Considering libjack0 2 as a solution to libjack-jackd2-0 24
  Fixing libjack-jackd2-0 via keep of libjack0
  Fixing libjack-jackd2-0 via remove of libjack0
Investigating libakonadi-kde4
Package libakonadi-kde4 has broken Conflicts on kdepimlibs-data
  Considering kdepimlibs-data -1 as a solution to libakonadi-kde4 12
  Added kdepimlibs-data to the remove list
  Fixing libakonadi-kde4 via remove of kdepimlibs-data
Investigating pm-utils
Package pm-utils has broken Conflicts on pm-utils-powersave-policy
  Considering pm-utils-powersave-policy -1 as a solution to pm-utils 10
  Added pm-utils-powersave-policy to the remove list
  Fixing pm-utils via remove of pm-utils-powersave-policy
Investigating xserver-xorg-video-all
Package xserver-xorg-video-all has broken Depends on xserver-xorg-video-tseng
  Considering xserver-xorg-video-tseng 2 as a solution to xserver-xorg-video-all 5
  Added xserver-xorg-video-tseng to the remove list
  Fixing xserver-xorg-video-all via keep of xserver-xorg-video-tseng
Investigating foomatic-db-compressed-ppds
Package foomatic-db-compressed-ppds has broken Conflicts on foomatic-db
  Considering foomatic-db 3 as a solution to foomatic-db-compressed-ppds 4
  Added foomatic-db to the remove list
  Considering foomatic-db 3 as a solution to foomatic-db-compressed-ppds 4
Package foomatic-db-compressed-ppds has broken Conflicts on foomatic-db-hpijs
  Considering foomatic-db 3 as a solution to foomatic-db-compressed-ppds 4
  Considering foomatic-db 3 as a solution to foomatic-db-compressed-ppds 4
  Added foomatic-db to the remove list
  Fixing foomatic-db-compressed-ppds via remove of foomatic-db
  Fixing foomatic-db-compressed-ppds via remove of foomatic-db
Investigating libcdt4
Package libcdt4 has broken Conflicts on libgraphviz4
  Considering libgraphviz4 1 as a solution to libcdt4 3
  Added libgraphviz4 to the remove list
  Fixing libcdt4 via remove of libgraphviz4
Investigating libept0
Package libept0 has broken Depends on libapt-pkg-libc6.10-6-4.8
  Considering apt 31 as a solution to libept0 3
  Removing libept0 rather than change libapt-pkg-libc6.10-6-4.8
 Try to Re-Instate xserver-xorg-video-tseng
Re-Instated xserver-xorg-video-tseng (11 vs 11)
Investigating fceux
Package fceux has broken Conflicts on gfceux
  Considering gfceux -1 as a solution to fceux 2
  Added gfceux to the remove list
  Fixing fceux via remove of gfceux
Investigating jackd2-firewire
Package jackd2-firewire has broken Conflicts on jackd-firewire
  Considering jackd-firewire -1 as a solution to jackd2-firewire 1
  Added jackd-firewire to the remove list
  Considering jackd1-firewire 0 as a solution to jackd2-firewire 1
  Fixing jackd2-firewire via remove of jackd-firewire
Investigating libvlccore2
Package libvlccore2 has broken Depends on vlc-data
  Considering vlc-data 6 as a solution to libvlccore2 1
  Removing libvlccore2 rather than change vlc-data
Investigating libbrasero-media0
Package libbrasero-media0 has broken Depends on brasero-common
  Considering brasero-common 16 as a solution to libbrasero-media0 -1
  Removing libbrasero-media0 rather than change brasero-common
Investigating mplayer-gui
Package mplayer-gui has broken Depends on libjack0
  Considering libjack0 2 as a solution to mplayer-gui -1
  Removing mplayer-gui rather than change libjack0
Investigating libmagickcore2-extra
Package libmagickcore2-extra has broken Depends on libgraphviz4
  Considering libgraphviz4 1 as a solution to libmagickcore2-extra -1
  Removing libmagickcore2-extra rather than change libgraphviz4
Investigating libvlc2
Package libvlc2 has broken Depends on libvlccore2
  Considering libvlccore2 1 as a solution to libvlc2 -1
  Removing libvlc2 rather than change libvlccore2
Investigating libavfilter0
Package libavfilter0 has broken Depends on libavcodec52
  Considering libavcodec52 20 as a solution to libavfilter0 -1
Package libavfilter0 has broken Depends on libavcodec-extra-52
  Considering libavcodec-extra-52 79 as a solution to libavfilter0 -1
  Or group remove for libavfilter0
Investigating libpackagekit-glib2-12
Package libpackagekit-glib2-12 has broken Depends on libapt-pkg-libc6.10-6-4.8
  Considering apt 31 as a solution to libpackagekit-glib2-12 -2
  Removing libpackagekit-glib2-12 rather than change libapt-pkg-libc6.10-6-4.8
Investigating libpackagekit-qt-12
Package libpackagekit-qt-12 has broken Depends on libapt-pkg-libc6.10-6-4.8
  Considering apt 31 as a solution to libpackagekit-qt-12 -2
  Removing libpackagekit-qt-12 rather than change libapt-pkg-libc6.10-6-4.8
Investigating xserver-xorg-core
Package xserver-xorg-core has broken Breaks on xserver-xorg-video-6
  Considering xserver-xorg-video-tseng 2 as a solution to xserver-xorg-core 79
  Added xserver-xorg-video-tseng to the remove list
  Fixing xserver-xorg-core via remove of xserver-xorg-video-tseng
Investigating xserver-xorg-video-all
Package xserver-xorg-video-all has broken Depends on xserver-xorg-video-tseng
  Considering xserver-xorg-video-tseng 2 as a solution to xserver-xorg-video-all 5
  Added xserver-xorg-video-tseng to the remove list
  Fixing xserver-xorg-video-all via keep of xserver-xorg-video-tseng
Investigating xserver-xorg-core
Package xserver-xorg-core has broken Breaks on xserver-xorg-video-6
  Considering xserver-xorg-video-tseng 2 as a solution to xserver-xorg-core 79
  Added xserver-xorg-video-tseng to the remove list
  Fixing xserver-xorg-core via remove of xserver-xorg-video-tseng
Investigating xserver-xorg-video-all
Package xserver-xorg-video-all has broken Depends on xserver-xorg-video-tseng
  Considering xserver-xorg-video-tseng 79 as a solution to xserver-xorg-video-all 5
  Removing xserver-xorg-video-all rather than change xserver-xorg-video-tseng
Investigating xserver-xorg-core
Package xserver-xorg-core has broken Breaks on xserver-xorg-video-6
  Considering xserver-xorg-video-tseng 79 as a solution to xserver-xorg-core 79
  Holding Back xserver-xorg-core rather than change xserver-xorg-video-6
Investigating xserver-xorg
Package xserver-xorg has broken Depends on xserver-xorg-core
  Considering xserver-xorg-core 79 as a solution to xserver-xorg 46
  Holding Back xserver-xorg rather than change xserver-xorg-core
Investigating xserver-xorg-input-evdev
Package xserver-xorg-input-evdev has broken Depends on xorg-input-abi-11.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-input-evdev 7
  Holding Back xserver-xorg-input-evdev rather than change xorg-input-abi-11.0
Investigating xserver-xorg-video-rendition
Package xserver-xorg-video-rendition has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-rendition 2
  Holding Back xserver-xorg-video-rendition rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-s3virge
Package xserver-xorg-video-s3virge has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-s3virge 2
  Holding Back xserver-xorg-video-s3virge rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-apm
Package xserver-xorg-video-apm has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-apm 2
  Holding Back xserver-xorg-video-apm rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-ark
Package xserver-xorg-video-ark has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-ark 2
  Holding Back xserver-xorg-video-ark rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-ati
Package xserver-xorg-video-ati has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-ati 2
  Holding Back xserver-xorg-video-ati rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-tdfx
Package xserver-xorg-video-tdfx has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-tdfx 2
  Holding Back xserver-xorg-video-tdfx rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-trident
Package xserver-xorg-video-trident has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-trident 2
  Holding Back xserver-xorg-video-trident rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-fbdev
Package xserver-xorg-video-fbdev has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-fbdev 2
  Holding Back xserver-xorg-video-fbdev rather than change xorg-video-abi-8.0
Investigating xserver-xorg-input-wacom
Package xserver-xorg-input-wacom has broken Depends on xorg-input-abi-11.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-input-wacom 2
  Holding Back xserver-xorg-input-wacom rather than change xorg-input-abi-11.0
Investigating xserver-xorg-video-mga
Package xserver-xorg-video-mga has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-mga 2
  Holding Back xserver-xorg-video-mga rather than change xorg-video-abi-8.0
Investigating xserver-xorg-input-vmmouse
Package xserver-xorg-input-vmmouse has broken Depends on xorg-input-abi-11.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-input-vmmouse 2
  Holding Back xserver-xorg-input-vmmouse rather than change xorg-input-abi-11.0
Investigating xserver-xorg-input-mouse
Package xserver-xorg-input-mouse has broken Depends on xorg-input-abi-11.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-input-mouse 2
  Holding Back xserver-xorg-input-mouse rather than change xorg-input-abi-11.0
Investigating xserver-xorg-video-r128
Package xserver-xorg-video-r128 has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-r128 2
  Holding Back xserver-xorg-video-r128 rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-openchrome
Package xserver-xorg-video-openchrome has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-openchrome 2
  Holding Back xserver-xorg-video-openchrome rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-vesa
Package xserver-xorg-video-vesa has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-vesa 2
  Holding Back xserver-xorg-video-vesa rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-siliconmotion
Package xserver-xorg-video-siliconmotion has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-siliconmotion 2
  Holding Back xserver-xorg-video-siliconmotion rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-mach64
Package xserver-xorg-video-mach64 has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-mach64 2
  Holding Back xserver-xorg-video-mach64 rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-sis
Package xserver-xorg-video-sis has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-sis 2
  Holding Back xserver-xorg-video-sis rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-s3
Package xserver-xorg-video-s3 has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-s3 2
  Holding Back xserver-xorg-video-s3 rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-nv
Package xserver-xorg-video-nv has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-nv 2
  Holding Back xserver-xorg-video-nv rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-savage
Package xserver-xorg-video-savage has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-savage 2
  Holding Back xserver-xorg-video-savage rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-vmware
Package xserver-xorg-video-vmware has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-vmware 2
  Holding Back xserver-xorg-video-vmware rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-i128
Package xserver-xorg-video-i128 has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-i128 2
  Holding Back xserver-xorg-video-i128 rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-neomagic
Package xserver-xorg-video-neomagic has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-neomagic 2
  Holding Back xserver-xorg-video-neomagic rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-chips
Package xserver-xorg-video-chips has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-chips 2
  Holding Back xserver-xorg-video-chips rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-voodoo
Package xserver-xorg-video-voodoo has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-voodoo 2
  Holding Back xserver-xorg-video-voodoo rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-geode
Package xserver-xorg-video-geode has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-geode 2
  Holding Back xserver-xorg-video-geode rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-i740
Package xserver-xorg-video-i740 has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-i740 2
  Holding Back xserver-xorg-video-i740 rather than change xorg-video-abi-8.0
Investigating xserver-xorg-input-synaptics
Package xserver-xorg-input-synaptics has broken Depends on xorg-input-abi-11.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-input-synaptics 2
  Holding Back xserver-xorg-input-synaptics rather than change xorg-input-abi-11.0
Investigating xserver-xorg-video-sisusb
Package xserver-xorg-video-sisusb has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-sisusb 2
  Holding Back xserver-xorg-video-sisusb rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-radeon
Package xserver-xorg-video-radeon has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-radeon 2
  Holding Back xserver-xorg-video-radeon rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-cirrus
Package xserver-xorg-video-cirrus has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-cirrus 2
  Holding Back xserver-xorg-video-cirrus rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-intel
Package xserver-xorg-video-intel has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-intel 2
  Holding Back xserver-xorg-video-intel rather than change xorg-video-abi-8.0
Investigating xserver-xorg-video-v4l
Package xserver-xorg-video-v4l has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-v4l 0
  Holding Back xserver-xorg-video-v4l rather than change xorg-video-abi-8.0
 Try to Re-Instate xserver-xorg-core
 Try to Re-Instate xserver-xorg
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 17
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
 Try to Re-Instate xserver-xorg-input-evdev
 Try to Re-Instate xserver-xorg-video-rendition
 Try to Re-Instate xserver-xorg-video-s3virge
 Try to Re-Instate xserver-xorg-video-apm
 Try to Re-Instate xserver-xorg-video-ark
 Try to Re-Instate xserver-xorg-video-ati
 Try to Re-Instate xserver-xorg-video-tdfx
 Try to Re-Instate xserver-xorg-video-trident
 Try to Re-Instate xserver-xorg-video-fbdev
 Try to Re-Instate xserver-xorg-input-wacom
 Try to Re-Instate xserver-xorg-video-mga
 Try to Re-Instate xserver-xorg-input-vmmouse
 Try to Re-Instate xserver-xorg-input-mouse
 Try to Re-Instate xserver-xorg-video-r128
 Try to Re-Instate xserver-xorg-video-openchrome
 Try to Re-Instate xserver-xorg-video-vesa
 Try to Re-Instate xserver-xorg-video-siliconmotion
 Try to Re-Instate xserver-xorg-video-mach64
 Try to Re-Instate xserver-xorg-video-sis
 Try to Re-Instate xserver-xorg-video-s3
 Try to Re-Instate xserver-xorg-video-nv
 Try to Re-Instate xserver-xorg-video-savage
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
 Try to Re-Instate xserver-xorg-video-vmware
 Try to Re-Instate xserver-xorg-video-i128
 Try to Re-Instate xserver-xorg-video-neomagic
 Try to Re-Instate xserver-xorg-video-chips
 Try to Re-Instate xserver-xorg-video-voodoo
 Try to Re-Instate xserver-xorg-video-geode
 Try to Re-Instate xserver-xorg-video-i740
 Try to Re-Instate xserver-xorg-input-synaptics
 Try to Re-Instate xserver-xorg-video-sisusb
 Try to Re-Instate xserver-xorg-video-radeon
 Try to Re-Instate xserver-xorg-video-cirrus
 Try to Re-Instate xserver-xorg-video-intel
 Try to Re-Instate xserver-xorg-video-v4l
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 17
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 17
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 17
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 17
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 17
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 79 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Done
```

And finally, contents of /var/log/dist-upgrade/lspci.txt:

```
00:00.0 RAM memory [0500]: nVidia Corporation MCP78S [GeForce 8200] Memory Controller [10de:0754] (rev a2)
00:01.0 ISA bridge [0601]: nVidia Corporation Device [10de:075e] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP78S [GeForce 8200] SMBus [10de:0752] (rev a1)
00:01.3 Co-processor [0b40]: nVidia Corporation MCP78S [GeForce 8200] Co-Processor [10de:0753] (rev a2)
00:01.4 RAM memory [0500]: nVidia Corporation MCP78S [GeForce 8200] Memory Controller [10de:0568] (rev a1)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller [10de:077b] (rev a1)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller [10de:077c] (rev a1)
00:04.0 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller [10de:077d] (rev a1)
00:04.1 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller [10de:077e] (rev a1)
00:06.0 IDE interface [0101]: nVidia Corporation MCP78S [GeForce 8200] IDE [10de:0759] (rev a1)
00:07.0 Audio device [0403]: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio [10de:0774] (rev a1)
00:08.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge [10de:075a] (rev a1)
00:09.0 IDE interface [0101]: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) [10de:0ad0] (rev a2)
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP77 Ethernet [10de:0760] (rev a2)
00:0b.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge [10de:0569] (rev a1)
00:14.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge [10de:077a] (rev a1)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration [1022:1300] (rev 40)
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map [1022:1301]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller [1022:1302]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control [1022:1303]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control [1022:1304]
02:00.0 VGA compatible controller [0300]: nVidia Corporation C77 [GeForce 8200M G] [10de:0845] (rev a2)
07:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
```
BUMPED

It seems that culprit is X-Swat-x-updates ppa in your case. You have to downgrade all packages installed from this ppa to official lucid versions first.

---

### Post by juanskarlos on 2011-02-13
I got my upgrade fix it if you look in the main log it appears that xserver-xorg-video-nouveau has some trouble or there is trouble with it, I just remove it with

**sudo apt-get remove xserver-xorg-video-nouveau**

I got this info from: [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/606652](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/606652) post #24.

After that in one of my laps I couldn't start Ubuntu, don't even in the login screen, so I start in safe mode with network, start ok and use cable network connection because I can't figure it out how to connect to my Wireless wpa2 network and install o reinstall, any way you want to understand it, **ubuntu-desktop** and reboot and that was all.

In the others computer was fine with removing **xserver-xorg-video-nouveau** and the upgrade was installed and reboot just fine. hope this works for anyone. this was done from Ubuntu 10.04 to Ubuntu 10.10.

---

### Post by Knapweed on 2011-02-25
> **juanskarlos said:**
> I got my upgrade fix it if you look in the main log it appears that xserver-xorg-video-nouveau has some trouble or there is trouble with it, I just remove it with

**sudo apt-get remove xserver-xorg-video-nouveau**



This worked for me. Thanks, Juan!

---

### Post by jonbwilson on 2011-03-01
> **Knapweed said:**
> This worked for me. Thanks, Juan!

Worked for me, too. Thank god. I Really didn't want to do a fresh install.

---

### Post by pawel k on 2012-01-23
I have had the same problem with upgrade from 11.04 to 11.10:
```
E:Error, pkgProblemResolver::Resolve generated breaks, this may be  caused by held packages.
```
But, the solution was to uninstall the nspluginwrapper package.:P

```
 sudo apt-get remove nspluginwrapper 
```

---

### Post by ksallee on 2012-06-24
I had the same exact problem.  This worked for me as well:

```
sudo apt-get remove nspluginwrapper
```

---

