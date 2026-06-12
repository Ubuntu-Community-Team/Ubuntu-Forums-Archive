---
title: "Upgrade to 11.10 Failed: Resolve generated breaks...."
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by LWhitson2 on 2011-10-13
Just tried to update from 11.04 to 11.10 and I got a message stating that the upgrade failed due to "Resolve generated breaks, this may be caused by held packages." Below are my log files:

main.log
```
2011-10-13 15:44:57,476 INFO Using config files '['./DistUpgrade.cfg']'
2011-10-13 15:44:57,477 INFO uname information: 'Linux Simon 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:17:25 UTC 2011 x86_64'
2011-10-13 15:44:57,477 INFO release-upgrader version '0.152.25' started
2011-10-13 15:44:57,561 DEBUG WARNING: can not get name for '<gtk.TreeSelection object at 0x177a140 (GtkTreeSelection at 0x164d640)>'
2011-10-13 15:44:57,561 DEBUG WARNING: can not get name for '<gtk.TreeSelection object at 0x177a190 (GtkTreeSelection at 0x1724900)>'
2011-10-13 15:44:57,610 DEBUG svg pixbuf loader failed (Error displaying image)
2011-10-13 15:44:57,679 DEBUG Using 'DistUpgradeViewGtk' view
2011-10-13 15:44:57,713 DEBUG aufsOptionsAndEnvironmentSetup()
2011-10-13 15:44:57,714 DEBUG using '/tmp/upgrade-rw-vMGwH3' as aufs_rw_dir
2011-10-13 15:44:57,714 DEBUG using '/tmp/upgrade-chroot-7yPJaM' as aufs chroot dir
2011-10-13 15:44:57,715 DEBUG enable dpkg --force-overwrite
2011-10-13 15:44:57,736 DEBUG creating statefile: '/var/log/dist-upgrade/apt-clone_system_state.tar.gz'
2011-10-13 15:44:59,140 DEBUG lsb-release: 'natty'
2011-10-13 15:44:59,141 DEBUG _pythonSymlinkCheck run
2011-10-13 15:44:59,141 DEBUG openCache()
2011-10-13 15:44:59,142 DEBUG Plugin modules in ./plugins: kdelibs4to5_plugin.py deb_plugin.py dpkg_status_plugin.py remove_lilo_plugin.py langpack_manual_plugin.py
2011-10-13 15:44:59,142 DEBUG Loading module ./plugins/kdelibs4to5_plugin.py
2011-10-13 15:44:59,143 DEBUG Plugins in <module 'kdelibs4to5_plugin' from './plugins/kdelibs4to5_plugin.py'>: <class 'kdelibs4to5_plugin.Kdelibs4devToKdelibs5devPlugin'>
2011-10-13 15:44:59,143 DEBUG Loading module ./plugins/deb_plugin.py
2011-10-13 15:44:59,144 DEBUG Plugins in <module 'deb_plugin' from './plugins/deb_plugin.py'>: <class 'deb_plugin.DebPlugin'>
2011-10-13 15:44:59,144 DEBUG Loading module ./plugins/dpkg_status_plugin.py
2011-10-13 15:44:59,146 DEBUG Plugins in <module 'dpkg_status_plugin' from './plugins/dpkg_status_plugin.py'>: <class 'dpkg_status_plugin.DpkgStatusPlugin'>
2011-10-13 15:44:59,146 DEBUG Loading module ./plugins/remove_lilo_plugin.py
2011-10-13 15:44:59,147 DEBUG Plugins in <module 'remove_lilo_plugin' from './plugins/remove_lilo_plugin.py'>: <class 'remove_lilo_plugin.RemoveLiloPlugin'>
2011-10-13 15:44:59,148 DEBUG Loading module ./plugins/langpack_manual_plugin.py
2011-10-13 15:44:59,149 DEBUG Plugins in <module 'langpack_manual_plugin' from './plugins/langpack_manual_plugin.py'>: <class 'langpack_manual_plugin.MarkLangpacksManuallyInstalledPlugin'>
2011-10-13 15:44:59,149 DEBUG plugins for condition 'PreCacheOpen' are '[]'
2011-10-13 15:44:59,149 DEBUG plugins for condition 'oneiricPreCacheOpen' are '[]'
2011-10-13 15:44:59,150 DEBUG plugins for condition 'from_nattyPreCacheOpen' are '[]'
2011-10-13 15:44:59,150 DEBUG quirks: running PreCacheOpen
2011-10-13 15:44:59,150 DEBUG running Quirks.PreCacheOpen
2011-10-13 15:44:59,150 DEBUG quirks: running oneiricPreCacheOpen
2011-10-13 15:44:59,150 DEBUG running Quirks.oneiricPreCacheOpen
2011-10-13 15:44:59,150 DEBUG multiarch: enabling i386 as a additional architecture
2011-10-13 15:44:59,419 DEBUG /openCache(), new cache size 33565
2011-10-13 15:44:59,419 DEBUG needServerMode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
2011-10-13 15:44:59,419 DEBUG checkViewDepends()
2011-10-13 15:44:59,419 DEBUG running doUpdate() (showErrors=False)
2011-10-13 15:46:00,408 DEBUG openCache()
2011-10-13 15:46:03,256 DEBUG /openCache(), new cache size 52696
2011-10-13 15:46:03,256 DEBUG doPostInitialUpdate
2011-10-13 15:46:03,256 DEBUG plugins for condition 'PostInitialUpdate' are '[]'
2011-10-13 15:46:03,256 DEBUG plugins for condition 'oneiricPostInitialUpdate' are '[]'
2011-10-13 15:46:03,256 DEBUG plugins for condition 'from_nattyPostInitialUpdate' are '[]'
2011-10-13 15:46:03,257 DEBUG quirks: running oneiricPostInitialUpdate
2011-10-13 15:46:07,653 DEBUG Foreign: google-chrome-beta nautilus-dropbox
2011-10-13 15:46:07,653 DEBUG Obsolete: cnijfilter-mx880series libffi6 ia32-crossover-pro libglapi-mesa flashplugin64-installer libllvm2.9 cnijfilter-common ia32-crossover-games-demo
2011-10-13 15:46:07,654 DEBUG updateSourcesList()
2011-10-13 15:46:07,713 DEBUG rewriteSourcesList()
2011-10-13 15:46:07,716 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ natty main restricted'
2011-10-13 15:46:07,716 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted' updated to new dist
2011-10-13 15:46:07,716 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ natty main restricted'
2011-10-13 15:46:07,716 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted' updated to new dist
2011-10-13 15:46:07,716 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted'
2011-10-13 15:46:07,717 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted' updated to new dist
2011-10-13 15:46:07,717 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted'
2011-10-13 15:46:07,717 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted' updated to new dist
2011-10-13 15:46:07,717 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ natty universe'
2011-10-13 15:46:07,717 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ oneiric universe' updated to new dist
2011-10-13 15:46:07,717 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ natty universe'
2011-10-13 15:46:07,717 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric universe' updated to new dist
2011-10-13 15:46:07,717 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ natty-updates universe'
2011-10-13 15:46:07,717 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe' updated to new dist
2011-10-13 15:46:07,717 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates universe'
2011-10-13 15:46:07,717 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe' updated to new dist
2011-10-13 15:46:07,718 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ natty multiverse'
2011-10-13 15:46:07,718 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse' updated to new dist
2011-10-13 15:46:07,718 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ natty multiverse'
2011-10-13 15:46:07,718 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse' updated to new dist
2011-10-13 15:46:07,718 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse'
2011-10-13 15:46:07,718 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse' updated to new dist
2011-10-13 15:46:07,718 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse'
2011-10-13 15:46:07,718 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse' updated to new dist
2011-10-13 15:46:07,718 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu natty-security main restricted'
2011-10-13 15:46:07,718 DEBUG entry 'deb http://security.ubuntu.com/ubuntu oneiric-security main restricted' updated to new dist
2011-10-13 15:46:07,719 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu natty-security main restricted'
2011-10-13 15:46:07,719 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted' updated to new dist
2011-10-13 15:46:07,719 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu natty-security universe'
2011-10-13 15:46:07,719 DEBUG entry 'deb http://security.ubuntu.com/ubuntu oneiric-security universe' updated to new dist
2011-10-13 15:46:07,719 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu natty-security universe'
2011-10-13 15:46:07,719 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu oneiric-security universe' updated to new dist
2011-10-13 15:46:07,719 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu natty-security multiverse'
2011-10-13 15:46:07,719 DEBUG entry 'deb http://security.ubuntu.com/ubuntu oneiric-security multiverse' updated to new dist
2011-10-13 15:46:07,719 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu natty-security multiverse'
2011-10-13 15:46:07,719 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse' updated to new dist
2011-10-13 15:46:07,720 DEBUG examining: 'deb http://archive.canonical.com/ubuntu natty partner'
2011-10-13 15:46:07,720 DEBUG entry 'deb http://archive.canonical.com/ubuntu oneiric partner' updated to new dist
2011-10-13 15:46:07,720 DEBUG examining: 'deb http://extras.ubuntu.com/ubuntu natty main'
2011-10-13 15:46:07,720 DEBUG entry 'deb http://extras.ubuntu.com/ubuntu oneiric main' updated to new dist
2011-10-13 15:46:07,720 DEBUG examining: 'deb http://ppa.launchpad.net/sevenmachines/flash/ubuntu natty main'
2011-10-13 15:46:07,722 DEBUG entry '# deb http://ppa.launchpad.net/sevenmachines/flash/ubuntu oneiric main # disabled on upgrade to oneiric' was disabled (unknown mirror)
2011-10-13 15:46:07,722 DEBUG examining: 'deb http://dl.google.com/linux/chrome/deb/ stable main'
2011-10-13 15:46:07,725 DEBUG entry '# deb http://dl.google.com/linux/chrome/deb/ stable main # disabled on upgrade to oneiric' was disabled (unknown mirror)
2011-10-13 15:46:07,725 DEBUG examining: 'deb http://linux.dropbox.com/ubuntu natty main'
2011-10-13 15:46:07,727 DEBUG entry '# deb http://linux.dropbox.com/ubuntu oneiric main # disabled on upgrade to oneiric' was disabled (unknown mirror)
2011-10-13 15:46:12,730 DEBUG running doUpdate() (showErrors=True)
2011-10-13 15:48:17,464 DEBUG openCache()
2011-10-13 15:48:17,464 DEBUG failed to SystemUnLock() (E:Not locked) 
2011-10-13 15:48:20,386 DEBUG /openCache(), new cache size 55774
2011-10-13 15:48:20,386 DEBUG needServerMode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
2011-10-13 15:50:11,406 ERROR Dist-upgrade failed: 'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'
2011-10-13 15:50:11,407 DEBUG abort called
2011-10-13 15:50:11,409 DEBUG openCache()
2011-10-13 15:50:11,410 DEBUG failed to SystemUnLock() (E:Not locked) 
2011-10-13 15:50:13,969 DEBUG /openCache(), new cache size 52696
2011-10-13 15:50:13,970 DEBUG enabling apt cron job
```

apt.log
```
Log time: 2011-10-13 15:44:59.419351
Log time: 2011-10-13 15:46:03.239488
Log time: 2011-10-13 15:48:20.125451
  Installing kde-runtime as Depends of kubuntu-debug-installer
    Installing kde-runtime-data as Depends of kde-runtime
  Installing dconf-gsettings-backend as Depends of gnome-session-canberra
  Installing libperl5.12 as Depends of libpurple0
  Installing libapt-pkg4.11 as Depends of apt-transport-https
  Installing at-spi2-core as Depends of ubuntu-desktop
  Setting NOT as auto-installed (direct Depends of pkg in APT::Never-MarkAuto-Sections)
    Installing libatspi2.0-0 as Depends of at-spi2-core
  Installing gnome-font-viewer as Depends of ubuntu-desktop
  Setting NOT as auto-installed (direct Depends of pkg in APT::Never-MarkAuto-Sections)
    Installing libgtk-3-0 as Depends of gnome-font-viewer
      Installing libgtk-3-common as Depends of libgtk-3-0
      Installing libgtk-3-bin as Recommends of libgtk-3-0
  Installing libatk-adaptor as Depends of ubuntu-desktop
  Setting NOT as auto-installed (direct Depends of pkg in APT::Never-MarkAuto-Sections)
  Installing libnotify-bin as Depends of ubuntu-desktop
  Setting NOT as auto-installed (direct Depends of pkg in APT::Never-MarkAuto-Sections)
  Installing lightdm as Depends of ubuntu-desktop
  Setting NOT as auto-installed (direct Depends of pkg in APT::Never-MarkAuto-Sections)
    Installing unity-greeter as Recommends of lightdm
      Installing libindicator3-6 as Depends of unity-greeter
      Installing liblightdm-gobject-1-0 as Depends of unity-greeter
        Installing accountsservice as Recommends of liblightdm-gobject-1-0
          Installing libaccountsservice0 as Depends of accountsservice
  Installing unity-2d as Depends of ubuntu-desktop
  Setting NOT as auto-installed (direct Depends of pkg in APT::Never-MarkAuto-Sections)
    Installing unity-2d-launcher as Depends of unity-2d
      Installing libdconf-qt0 as Depends of unity-2d-launcher
        Installing libdconf-dbus-1-0 as Depends of libdconf-qt0
      Installing libunity-2d-private0 as Depends of unity-2d-launcher
        Installing libnux-1.0-0 as Depends of libunity-2d-private0
          Installing libnux-1.0-common as Depends of libnux-1.0-0
        Installing libqtbamf1 as Depends of libunity-2d-private0
        Installing libqtdee2 as Depends of libunity-2d-private0
        Installing libunity-core-4.0-4 as Depends of libunity-2d-private0
          Installing unity-services as Depends of libunity-core-4.0-4
        Installing libwnck-3-0 as Depends of libunity-2d-private0
          Installing libwnck-3-common as Depends of libwnck-3-0
      Installing unity-lens-files as Recommends of unity-2d-launcher
        Installing libunity6 as Depends of unity-lens-files
          Installing libdbusmenu-glib4 as Depends of libunity6
      Installing unity-lens-applications as Recommends of unity-2d-launcher
      Installing unity-lens-music as Recommends of unity-2d-launcher
        Installing unity-scope-musicstores as Recommends of unity-lens-music
    Installing unity-2d-panel as Depends of unity-2d
      Installing libqtgconf1 as Depends of unity-2d-panel
      Installing indicator-messages as Recommends of unity-2d-panel
        Installing libdbusmenu-gtk3-4 as Depends of indicator-messages
        Installing libindicator-messages-status-provider1 as Depends of indicator-messages
        Installing indicator-status-provider-mc5 as Recommends of indicator-messages
    Installing unity-2d-places as Depends of unity-2d
    Installing unity-2d-spread as Depends of unity-2d
  Installing xdiagnose as Depends of ubuntu-desktop
  Setting NOT as auto-installed (direct Depends of pkg in APT::Never-MarkAuto-Sections)
    Installing gir1.2-gtk-3.0 as Depends of xdiagnose
  new important dependency: c2esp
  Installing c2esp as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
  new important dependency: deja-dup
  Installing deja-dup as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
    Installing libgnome-control-center1 as Depends of deja-dup
    Installing duplicity as Depends of deja-dup
      Installing librsync1 as Depends of duplicity
    Installing ubuntuone-couch as Recommends of deja-dup
  new important dependency: ibus-gtk3
  Installing ibus-gtk3 as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
    Installing libibus-1.0-0 as Depends of ibus-gtk3
  new important dependency: libgail-3-common
  Installing libgail-3-common as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
    Installing libgail-3-0 as Depends of libgail-3-common
  new important dependency: ptouch-driver
  Installing ptouch-driver as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
  new important dependency: qt-at-spi
  Installing qt-at-spi as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
  new important dependency: rastertosag-gdi
  Installing rastertosag-gdi as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
  new important dependency: sni-qt
  Installing sni-qt as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
  new important dependency: thunderbird
  Installing thunderbird as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
    Installing thunderbird-globalmenu as Recommends of thunderbird
      Installing libdbusmenu-gtk4 as Depends of thunderbird-globalmenu
  new important dependency: thunderbird-gnome-support
  Installing thunderbird-gnome-support as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
    Installing libebook1.2-12 as Depends of thunderbird-gnome-support
      Installing libcamel-1.2-29 as Depends of libebook1.2-12
        Installing libedataserver1.2-15 as Depends of libcamel-1.2-29
  Installing libbamf3-0 as Depends of unity
  Installing libgnome-desktop-3-2 as Depends of unity
    Installing gnome-desktop3-data as Depends of libgnome-desktop-3-2
  Installing libunity-misc4 as Depends of unity
  Installing compiz-plugins-main-default as Depends of unity
    Installing libboost-serialization1.46.1 as Depends of compiz-plugins-main-default
  new important dependency: indicator-power
  Installing indicator-power as Recommends of unity
  Installing gcc-4.6-base as Depends of libstdc++6
  Installing libdbus-glib1.0-cil as Depends of tomboy
    Installing libdbus1.0-cil as Depends of libdbus-glib1.0-cil
      Installing libmono-corlib4.0-cil as Depends of libdbus1.0-cil
        Installing libmono-i18n-west4.0-cil as Recommends of libmono-corlib4.0-cil
          Installing libmono-i18n4.0-cil as Depends of libmono-i18n-west4.0-cil
      Installing libmono-system-core4.0-cil as Depends of libdbus1.0-cil
        Installing libmono-posix4.0-cil as Depends of libmono-system-core4.0-cil
          Installing libmono-system4.0-cil as Depends of libmono-posix4.0-cil
            Installing libmono-security4.0-cil as Depends of libmono-system4.0-cil
            Installing libmono-system-configuration4.0-cil as Depends of libmono-system4.0-cil
              Installing libmono-system-security4.0-cil as Depends of libmono-system-configuration4.0-cil
                Installing libmono-system-xml4.0-cil as Depends of libmono-system-security4.0-cil
  Installing libmono-cairo4.0-cil as Depends of tomboy
  Installing libcanberra-gtk3-0 as Depends of libevolution
    Installing libcanberra-gtk3-module as Recommends of libcanberra-gtk3-0
  Installing libecal1.2-10 as Depends of libevolution
  Installing libedataserverui-3.0-1 as Depends of libevolution
  Installing libgoa-1.0-0 as Depends of libevolution
    Installing librest-0.7-0 as Depends of libgoa-1.0-0
    Installing libwebkitgtk-3.0-0 as Depends of libgoa-1.0-0
      Installing libwebkitgtk-3.0-common as Depends of libwebkitgtk-3.0-0
  Installing libgtkhtml-4.0-0 as Depends of libevolution
    Installing libgtkhtml-4.0-common as Depends of libgtkhtml-4.0-0
  Installing libgtkhtml-editor-4.0-0 as Depends of libevolution
  Installing liblaunchpad-integration-3.0-1 as Depends of libevolution
  Installing libtinfo5 as Depends of libncurses5
  Installing libdb5.1 as Depends of iproute
  Installing libgmp10 as Depends of libmpfr4
  Installing libgnome-media-profiles-3.0-0 as Depends of gnome-media
  Installing gstreamer0.10-gconf as Depends of gnome-media
  Installing libjpeg8 as Depends of libv4l-0
  Installing libprotobuf7 as Depends of libcompizconfig0
  Installing libappindicator3-1 as Depends of update-notifier
  Installing libdbi1 as Depends of gnucash
  Installing guile-1.8 as Depends of gnucash
  Installing ubuntuone-installer as Depends of ubuntuone-control-panel-gtk
  Installing libgvnc-1.0-0 as Depends of libgtk-vnc-1.0-0
  Installing lib32tinfo5 as Depends of lib32ncurses5
  Installing libgucharmap-2-90-7 as Depends of gnome-applets
  Installing libgweather-3-0 as Depends of gnome-applets
  Installing libpanel-applet-4-0 as Depends of gnome-applets
  Installing gir1.2-panelapplet-4.0 as Depends of gnome-applets
  new important dependency: gir1.2-unity-4.0
  Installing gir1.2-unity-4.0 as Recommends of ubuntuone-client
  Installing libssl1.0.0 as Depends of libsnmp15
  Installing libnm-glib4 as Depends of network-manager-gnome
    Installing libnm-util2 as Depends of libnm-glib4
  Installing libnm-gtk0 as Depends of network-manager-gnome
    Installing libnm-gtk-common as Depends of libnm-gtk0
  Installing libraptor2-0 as Depends of librdf0
    Installing libyajl1 as Depends of libraptor2-0
  Installing librasqal3 as Depends of librdf0
    Installing libmhash2 as Depends of librasqal3
  Installing libyaml-tiny-perl as Depends of doc-base
  Installing zenity-common as Depends of zenity
  Installing libgdata13 as Depends of totem-plugins
    Installing liboauth0 as Depends of libgdata13
  Installing libtotem0 as Depends of totem-plugins
    Installing libpeas-1.0-0 as Depends of libtotem0
      Installing libpeas-common as Depends of libpeas-1.0-0
  Installing gir1.2-totem-1.0 as Depends of totem-plugins
    Installing gir1.2-totem-plparser-1.0 as Depends of gir1.2-totem-1.0
  Installing gir1.2-peas-1.0 as Depends of totem-plugins
  Installing lib32ffi6 as Depends of ia32-libs
  new important dependency: ia32-libs-multiarch
  Installing ia32-libs-multiarch as Recommends of ia32-libs
    Installing libqtcore4 as Depends of ia32-libs-multiarch
      Installing libc6 as Depends of libqtcore4
        Installing libgcc1 as Depends of libc6
          Installing gcc-4.6-base as Depends of libgcc1
      Installing libglib2.0-0 as Depends of libqtcore4
        Installing libffi6 as Depends of libglib2.0-0
        Installing libpcre3 as Depends of libglib2.0-0
        Installing libselinux1 as Depends of libglib2.0-0
        Installing zlib1g as Depends of libglib2.0-0
      Installing libstdc++6 as Depends of libqtcore4
    Installing libqtgui4 as Depends of ia32-libs-multiarch
      Installing libaudio2 as Depends of libqtgui4
        Installing libxau6 as Depends of libaudio2
        Installing libxt6 as Depends of libaudio2
          Installing libice6 as Depends of libxt6
          Installing libsm6 as Depends of libxt6
            Installing libuuid1 as Depends of libsm6
          Installing libx11-6 as Depends of libxt6
            Installing libxcb1 as Depends of libx11-6
              Installing libxdmcp6 as Depends of libxcb1
      Installing libfontconfig1 as Depends of libqtgui4
        Installing libexpat1 as Depends of libfontconfig1
        Installing libfreetype6 as Depends of libfontconfig1
      Installing libjpeg62 as Depends of libqtgui4
      Installing libmng1 as Depends of libqtgui4
        Installing liblcms1 as Depends of libmng1
      Installing libpng12-0 as Depends of libqtgui4
      Installing libqt4-declarative as Depends of libqtgui4
        Installing libqt4-network as Depends of libqt4-declarative
          Installing libqt4-dbus as Depends of libqt4-network
            Installing libdbus-1-3 as Depends of libqt4-dbus
            Installing libqt4-xml as Depends of libqt4-dbus
            Installing qdbus as Depends of libqt4-dbus
        Installing libqt4-script as Depends of libqt4-declarative
        Installing libqt4-sql as Depends of libqt4-declarative
          Installing libqt4-sql-mysql as Recommends of libqt4-sql
            Installing libmysqlclient16 as Depends of libqt4-sql-mysql
        Installing libqt4-xmlpatterns as Depends of libqt4-declarative
      Installing libtiff4 as Depends of libqtgui4
      Installing libxext6 as Depends of libqtgui4
      Installing libxi6 as Depends of libqtgui4
      Installing libxrender1 as Depends of libqtgui4
      Installing libcups2 as Recommends of libqtgui4
        Installing libavahi-client3 as Depends of libcups2
          Installing libavahi-common3 as Depends of libavahi-client3
            Installing libavahi-common-data as Depends of libavahi-common3
        Installing libgnutls26 as Depends of libcups2
          Installing libgcrypt11 as Depends of libgnutls26
            Installing libgpg-error0 as Depends of libgcrypt11
          Installing libtasn1-3 as Depends of libgnutls26
        Installing libgssapi-krb5-2 as Depends of libcups2
          Installing libcomerr2 as Depends of libgssapi-krb5-2
          Installing libk5crypto3 as Depends of libgssapi-krb5-2
            Installing libkrb5support0 as Depends of libk5crypto3
          Installing libkrb5-3 as Depends of libgssapi-krb5-2
            Installing libkeyutils1 as Depends of libkrb5-3
    Installing libqt4-opengl as Depends of ia32-libs-multiarch
      Installing libgl1-mesa-glx as Depends of libqt4-opengl
        Installing libdrm2 as Depends of libgl1-mesa-glx
        Installing libglapi-mesa as Depends of libgl1-mesa-glx
        Installing libxdamage1 as Depends of libgl1-mesa-glx
        Installing libxfixes3 as Depends of libgl1-mesa-glx
        Installing libxxf86vm1 as Depends of libgl1-mesa-glx
        Installing libgl1-mesa-dri as Recommends of libgl1-mesa-glx
          Installing libdrm-intel1 as Depends of libgl1-mesa-dri
            Installing libpciaccess0 as Depends of libdrm-intel1
          Installing libdrm-nouveau1a as Depends of libgl1-mesa-dri
          Installing libdrm-radeon1 as Depends of libgl1-mesa-dri
          Installing libllvm2.9 as Depends of libgl1-mesa-dri
    Installing libqt4-qt3support as Depends of ia32-libs-multiarch
      Installing libqt4-designer as Depends of libqt4-qt3support
    Installing libqt4-scripttools as Depends of ia32-libs-multiarch
    Installing libqt4-svg as Depends of ia32-libs-multiarch
    Installing libqt4-test as Depends of ia32-libs-multiarch
    Installing libacl1 as Depends of ia32-libs-multiarch
      Installing libattr1 as Depends of libacl1
    Installing libcupsimage2 as Depends of ia32-libs-multiarch
    Installing libcurl3 as Depends of ia32-libs-multiarch
      Installing libidn11 as Depends of libcurl3
      Installing libldap-2.4-2 as Depends of libcurl3
        Installing libsasl2-2 as Depends of libldap-2.4-2
          Installing libdb5.1 as Depends of libsasl2-2
          Installing libsasl2-modules as Recommends of libsasl2-2
            Installing libssl1.0.0 as Depends of libsasl2-modules
      Installing librtmp0 as Depends of libcurl3
    Installing libgdbm3 as Depends of ia32-libs-multiarch
    Installing libnss3 as Depends of ia32-libs-multiarch
      Installing libnspr4 as Depends of libnss3
      Installing libsqlite3-0 as Depends of libnss3
    Installing libxss1 as Depends of ia32-libs-multiarch
  Installing gir1.2-vte-2.90 as Depends of language-selector-gnome
    Installing libvte-2.90-9 as Depends of gir1.2-vte-2.90
  Installing libunique-3.0-0 as Depends of gnome-disk-utility
  Installing libcolord1 as Depends of gnome-settings-daemon
    Installing colord as Recommends of libcolord1
      Installing liblcms2-2 as Depends of colord
      Installing acl as Depends of colord
      Installing icc-profiles-free as Recommends of colord
  Installing libgnomekbd7 as Depends of gnome-settings-daemon
  Installing libgtksourceview-3.0-0 as Depends of gedit
    Installing libgtksourceview-3.0-common as Depends of libgtksourceview-3.0-0
  new important dependency: gir1.2-gtksource-3.0
  Installing gir1.2-gtksource-3.0 as Recommends of gedit
  Installing libgtkmm-3.0-1 as Depends of gnome-system-monitor
  Installing libdlrestrictions1 as Depends of libkdecore5
  Installing libebackend-1.2-1 as Depends of evolution-exchange
  Installing libedata-book-1.2-11 as Depends of evolution-exchange
  Installing libedata-cal-1.2-13 as Depends of evolution-exchange
  Installing gir1.2-launchpad-integration-3.0 as Depends of gnome-sudoku
  Installing libindicate-gtk3 as Depends of python-indicate
  Installing python-gobject-2 as Depends of python-indicate
  Installing libevent-2.0-5 as Depends of transmission-gtk
  Installing libminiupnpc5 as Depends of transmission-gtk
  Installing libnatpmp1 as Depends of transmission-gtk
  Installing libmono-csharp4.0-cil as Depends of gbrainy
  Installing libgck-1-0 as Depends of seahorse
    Installing libp11-kit0 as Depends of libgck-1-0
  Installing libgcr-3-1 as Depends of seahorse
  Installing libboost-iostreams1.46.1 as Depends of aptitude
  Installing libfolks-telepathy25 as Depends of empathy
    Installing libfolks25 as Depends of libfolks-telepathy25
  Installing libido3-0.1-0 as Depends of empathy
  new important dependency: telepathy-indicator
  Installing telepathy-indicator as Recommends of empathy
  Installing libapt-inst1.3 as Depends of python-apt
  Installing liboverlay-scrollbar-0.2-0 as Depends of overlay-scrollbar
  Installing liboverlay-scrollbar3-0.2-0 as Depends of overlay-scrollbar
  Installing libxcb-util0 as Depends of libstartup-notification0
  new important dependency: python-dateutil
  Installing python-dateutil as Recommends of checkbox
  new important dependency: libswitch-perl
  Installing libswitch-perl as Recommends of perl-modules
  new important dependency: libpod-plainer-perl
  Installing libpod-plainer-perl as Recommends of perl-modules
  new important dependency: libclass-isa-perl
  Installing libclass-isa-perl as Recommends of perl-modules
  Installing libavahi-ui-gtk3-0 as Depends of vinagre
  Installing libgtk-vnc-2.0-0 as Depends of vinagre
  Installing libcap2-bin as Depends of gnome-keyring
  Installing gir1.2-gmenu-3.0 as Depends of software-center
    Installing libgnome-menu-3-0 as Depends of gir1.2-gmenu-3.0
  Installing gir1.2-webkit-3.0 as Depends of software-center
  Installing oneconf as Depends of software-center
  Installing g++-4.6 as Depends of g++
    Installing gcc-4.6 as Depends of g++-4.6
      Installing cpp-4.6 as Depends of gcc-4.6
      Installing libquadmath0 as Depends of gcc-4.6
    Installing libstdc++6-4.6-dev as Depends of g++-4.6
  Installing sound-theme-freedesktop as Depends of libcanberra0
  Installing libmono-sharpzip4.84-cil as Depends of libmono-addins0.2-cil
  Installing libmtp9 as Depends of banshee
    Installing libmtp-common as Depends of libmtp9
    Installing libmtp-runtime as Recommends of libmtp9
  Installing grub2-common as Depends of grub-pc
  Installing grub-pc-bin as Depends of grub-pc
  Installing libmono-management4.0-cil as Depends of mono-csharp-shell
  new important dependency: gir1.2-dbusmenu-gtk-0.4
  Installing gir1.2-dbusmenu-gtk-0.4 as Recommends of update-manager
  Installing python-pyatspi2 as Depends of gnome-orca
    Installing gir1.2-atspi-2.0 as Depends of python-pyatspi2
  Installing gir1.2-wnck-3.0 as Depends of gnome-orca
  Installing libnl3 as Depends of network-manager
  Installing librtmp0 as Depends of libcurl3
  Installing libgrip0 as Depends of eog
  Installing mono-4.0-gac as Depends of mono-gac
  Installing gir1.2-gnomebluetooth-1.0 as Depends of gnome-bluetooth
  Installing software-properties-common as Depends of software-properties-gtk
  Installing compiz-plugins-default as Depends of compiz-gnome
  Installing linux-headers-3.0.0-12-generic as Depends of linux-headers-generic
    Installing linux-headers-3.0.0-12 as Depends of linux-headers-3.0.0-12-generic
  Installing linux-image-3.0.0-12-generic as Depends of linux-image-generic
  Setting NOT as auto-installed (direct Depends of pkg in APT::Never-MarkAuto-Sections)
  Installing libevince3-3 as Depends of evince
  Installing libppl-c4 as Depends of libcloog-ppl0
    Installing libppl9 as Depends of libppl-c4
    Installing libpwl5 as Depends of libppl-c4
  new important dependency: appmenu-gtk3
  Installing appmenu-gtk3 as Recommends of indicator-appmenu
  Installing tcl8.5 as Depends of tcl
  Installing gir1.2-indicate-0.6 as Depends of gwibber-service
  Installing libindicator6 as Depends of libappindicator1
  Installing libyelp0 as Depends of yelp
  Installing libbrasero-media3-1 as Depends of brasero-cdrkit
  Installing libaqhbci20 as Depends of libaqbanking33-plugins
  Installing gir1.2-appindicator3-0.1 as Depends of jockey-gtk
  Installing libprotoc7 as Depends of protobuf-compiler
  Installing gnome-control-center-data as Depends of gnome-control-center
  new important dependency: apg
  Installing apg as Recommends of gnome-control-center
  new important dependency: gnome-icon-theme-symbolic
  Installing gnome-icon-theme-symbolic as Recommends of gnome-control-center
  new important dependency: gnome-online-accounts
  Installing gnome-online-accounts as Recommends of gnome-control-center
  Installing libmount1 as PreDepends of mount
  Installing libasyncns0 as Depends of libpulse0
  Installing libjson0 as Depends of libpulse0
  Installing libhttp-daemon-perl as Depends of librpc-xml-perl
    Installing libhttp-message-perl as Depends of libhttp-daemon-perl
      Installing libhttp-date-perl as Depends of libhttp-message-perl
      Installing libencode-locale-perl as Depends of libhttp-message-perl
      Installing liblwp-mediatypes-perl as Depends of libhttp-message-perl
  new important dependency: gvfs-bin
  Installing gvfs-bin as Recommends of gvfs
  new important dependency: gnome-session-fallback
  Installing gnome-session-fallback as Recommends of gnome-panel
  Installing libfile-listing-perl as Depends of libwww-perl
  Installing libhttp-cookies-perl as Depends of libwww-perl
  Installing libhttp-negotiate-perl as Depends of libwww-perl
  Installing liblwp-protocol-https-perl as Depends of libwww-perl
    Installing libnet-http-perl as Depends of liblwp-protocol-https-perl
      Installing libio-socket-ssl-perl as Recommends of libnet-http-perl
        Installing libnet-ssleay-perl as Depends of libio-socket-ssl-perl
  Installing libwww-robotrules-perl as Depends of libwww-perl
  new important dependency: libhtml-form-perl
  Installing libhtml-form-perl as Recommends of libwww-perl
  Installing libjte1 as Depends of libisofs6
  Installing libgwibber-gtk2 as Depends of gwibber
    Installing libgtkspell3-0 as Depends of libgwibber-gtk2
    Installing libgwibber2 as Depends of libgwibber-gtk2
  Installing libmono-system-drawing4.0-cil as Depends of libgtk2.0-cil
    Installing libgdiplus as Depends of libmono-system-drawing4.0-cil
  Installing patchutils as Depends of lintian
  Installing libpanel-applet-3-0 as Depends of gir1.2-panelapplet-3.0
  Installing libkde3support4 as Depends of kdelibs5-plugins
    Installing libqt4-qt3support as Depends of libkde3support4
      Installing libqt4-designer as Depends of libqt4-qt3support
  Installing katepart as Depends of kdelibs5-plugins
    Installing kate-data as Depends of katepart
  Installing gtk3-engines-unico as Depends of light-themes
  new important dependency: libgphoto2-l10n
  Installing libgphoto2-l10n as Recommends of libgphoto2-2
Starting
Starting 2
Investigating (0) libdbusmenu-glib4 [ amd64 ] < none -> 0.5.0-0ubuntu3 > ( libs )
Broken libdbusmenu-glib4:amd64 Breaks on gir1.2-unity-3.0 [ amd64 ] < 3.8.4-0ubuntu1 > ( libs ) (< 3.8.4-0ubuntu2)
  Considering gir1.2-unity-3.0:amd64 5 as a solution to libdbusmenu-glib4:amd64 82
  Added gir1.2-unity-3.0:amd64 to the remove list
  Fixing libdbusmenu-glib4:amd64 via remove of gir1.2-unity-3.0:amd64
Investigating (0) libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2 -> 7.11-0ubuntu3 > ( libs )
Broken libgl1-mesa-glx:amd64 Depends on libglapi-mesa [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs ) (= 7.11-0ubuntu3)
  Considering libglapi-mesa:amd64 19 as a solution to libgl1-mesa-glx:amd64 68
  Removing libgl1-mesa-glx:amd64 rather than change libglapi-mesa:amd64
Investigating (0) gvfs [ amd64 ] < 1.8.0-0ubuntu3 -> 1.10.0-0ubuntu1 > ( libs )
Broken gvfs:amd64 Conflicts on libgvfscommon0 [ amd64 ] < 1.8.0-0ubuntu3 > ( libs )
  Considering libgvfscommon0:amd64 -1 as a solution to gvfs:amd64 54
  Added libgvfscommon0:amd64 to the remove list
  Fixing gvfs:amd64 via remove of libgvfscommon0:amd64
Investigating (0) libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.0-0ubuntu4 > ( libs )
Broken libgnome-desktop-3-2:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2 -> 7.11-0ubuntu3 > ( libs )
  Considering libgl1-mesa-glx:amd64 68 as a solution to libgnome-desktop-3-2:amd64 48
  Holding Back libgnome-desktop-3-2:amd64 rather than change libgl1-mesa-glx:amd64
Broken libgnome-desktop-3-2:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 68 as a solution to libgnome-desktop-3-2:amd64 48
  Holding Back libgnome-desktop-3-2:amd64 rather than change libgl1:amd64
  Or group keep for libgnome-desktop-3-2:amd64
Investigating (0) gnome-settings-daemon [ amd64 ] < 2.32.1-0ubuntu13.1 -> 3.2.0-0ubuntu5 > ( gnome )
Broken gnome-settings-daemon:amd64 Depends on libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.0-0ubuntu4 > ( libs ) (>= 3.1.5)
  Considering libgnome-desktop-3-2:amd64 48 as a solution to gnome-settings-daemon:amd64 36
  Holding Back gnome-settings-daemon:amd64 rather than change libgnome-desktop-3-2:amd64
Investigating (0) x11-utils [ amd64 ] < 7.6+1 -> 7.6+3 > ( x11 )
Broken x11-utils:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2 -> 7.11-0ubuntu3 > ( libs )
  Considering libgl1-mesa-glx:amd64 68 as a solution to x11-utils:amd64 35
Broken x11-utils:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 68 as a solution to x11-utils:amd64 35
  Or group remove for x11-utils:amd64
Investigating (0) gnome-session [ amd64 ] < 2.32.1-0ubuntu20 -> 3.2.0-0ubuntu3 > ( gnome )
Broken gnome-session:amd64 Depends on gnome-settings-daemon [ amd64 ] < 2.32.1-0ubuntu13.1 -> 3.2.0-0ubuntu5 > ( gnome ) (>= 3.0)
  Considering gnome-settings-daemon:amd64 36 as a solution to gnome-session:amd64 24
  Removing gnome-session:amd64 rather than change gnome-settings-daemon:amd64
Investigating (0) gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.0-0ubuntu6 > ( gnome )
Broken gnome-control-center:amd64 Depends on libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.0-0ubuntu4 > ( libs ) (>= 3.1.2)
  Considering libgnome-desktop-3-2:amd64 48 as a solution to gnome-control-center:amd64 23
  Holding Back gnome-control-center:amd64 rather than change libgnome-desktop-3-2:amd64
Investigating (0) console-setup [ amd64 ] < 1.57ubuntu20 -> 1.57ubuntu27 > ( utils )
Broken console-setup:amd64 Conflicts on console-terminus [ amd64 ] < 4.30-2 > ( fonts )
  Considering console-terminus:amd64 -1 as a solution to console-setup:amd64 19
  Added console-terminus:amd64 to the remove list
  Fixing console-setup:amd64 via remove of console-terminus:amd64
Investigating (0) gnome-control-center-data [ amd64 ] < none -> 1:3.2.0-0ubuntu6 > ( gnome )
Broken gnome-control-center-data:amd64 Conflicts on capplets-data [ amd64 ] < 1:2.32.1-0ubuntu15 > ( gnome )
  Considering capplets-data:amd64 -1 as a solution to gnome-control-center-data:amd64 19
  Added capplets-data:amd64 to the remove list
Broken gnome-control-center-data:amd64 Breaks on gnome-settings-daemon [ amd64 ] < 2.32.1-0ubuntu13.1 -> 3.2.0-0ubuntu5 > ( gnome ) (< 3.0~)
  Considering gnome-settings-daemon:amd64 36 as a solution to gnome-control-center-data:amd64 19
  Holding Back gnome-control-center-data:amd64 rather than change gnome-settings-daemon:amd64
Investigating (0) libglapi-mesa [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
Broken libglapi-mesa:amd64 Breaks on libglapi-mesa [ i386 ] < none -> 7.11-0ubuntu3 > ( libs ) (!= 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty)
  Considering libglapi-mesa:i386 1 as a solution to libglapi-mesa:amd64 19
  Added libglapi-mesa:i386 to the remove list
  Fixing libglapi-mesa:amd64 via keep of libglapi-mesa:i386
Investigating (0) gnome-panel [ amd64 ] < 1:2.32.1-0ubuntu6.5 -> 1:3.2.0-0ubuntu1 > ( universe/gnome )
Broken gnome-panel:amd64 Depends on libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.0-0ubuntu4 > ( libs ) (>= 2.91.5)
  Considering libgnome-desktop-3-2:amd64 48 as a solution to gnome-panel:amd64 19
  Removing gnome-panel:amd64 rather than change libgnome-desktop-3-2:amd64
Investigating (0) ntfs-3g [ amd64 ] < 1:2010.8.8-0ubuntu1 -> 1:2011.4.12AR.4-2ubuntu3 > ( otherosfs )
Broken ntfs-3g:amd64 Conflicts on ntfsprogs [ amd64 ] < 2.0.0-1ubuntu4 > ( universe/otherosfs )
  Considering ntfsprogs:amd64 7 as a solution to ntfs-3g:amd64 18
  Added ntfsprogs:amd64 to the remove list
  Fixing ntfs-3g:amd64 via remove of ntfsprogs:amd64
Investigating (0) libevolution [ amd64 ] < 2.32.2-0ubuntu7 -> 3.2.0-0ubuntu2 > ( gnome )
Broken libevolution:amd64 Depends on libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.0-0ubuntu4 > ( libs ) (>= 2.91.5)
  Considering libgnome-desktop-3-2:amd64 48 as a solution to libevolution:amd64 16
  Holding Back libevolution:amd64 rather than change libgnome-desktop-3-2:amd64
Investigating (0) gnome-session-bin [ amd64 ] < 2.32.1-0ubuntu20 -> 3.2.0-0ubuntu3 > ( gnome )
Broken gnome-session-bin:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2 -> 7.11-0ubuntu3 > ( libs )
  Considering libgl1-mesa-glx:amd64 68 as a solution to gnome-session-bin:amd64 16
Broken gnome-session-bin:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 68 as a solution to gnome-session-bin:amd64 16
  Or group remove for gnome-session-bin:amd64
Investigating (0) nautilus [ amd64 ] < 1:2.32.2.1-0ubuntu13 -> 1:3.2.0-0ubuntu5 > ( gnome )
Broken nautilus:amd64 Depends on libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.0-0ubuntu4 > ( libs ) (>= 3.0.0)
  Considering libgnome-desktop-3-2:amd64 48 as a solution to nautilus:amd64 13
  Removing nautilus:amd64 rather than change libgnome-desktop-3-2:amd64
Investigating (0) compiz-plugins-default [ amd64 ] < none -> 1:0.9.6+bzr20110929-0ubuntu3 > ( x11 )
Broken compiz-plugins-default:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2 -> 7.11-0ubuntu3 > ( libs )
  Considering libgl1-mesa-glx:amd64 68 as a solution to compiz-plugins-default:amd64 12
  Holding Back compiz-plugins-default:amd64 rather than change libgl1-mesa-glx:amd64
Broken compiz-plugins-default:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 68 as a solution to compiz-plugins-default:amd64 12
  Holding Back compiz-plugins-default:amd64 rather than change libgl1:amd64
  Or group keep for compiz-plugins-default:amd64
Investigating (0) libglu1-mesa [ amd64 ] < 7.10.2-0ubuntu2 -> 7.11-0ubuntu3 > ( libs )
Broken libglu1-mesa:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2 -> 7.11-0ubuntu3 > ( libs )
  Considering libgl1-mesa-glx:amd64 68 as a solution to libglu1-mesa:amd64 12
Broken libglu1-mesa:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 68 as a solution to libglu1-mesa:amd64 12
  Or group remove for libglu1-mesa:amd64
Investigating (0) libqt4-opengl [ amd64 ] < 4:4.7.2-0ubuntu6.3 -> 4:4.7.4-0ubuntu8 > ( libs )
Broken libqt4-opengl:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2 -> 7.11-0ubuntu3 > ( libs )
  Considering libgl1-mesa-glx:amd64 68 as a solution to libqt4-opengl:amd64 11
Broken libqt4-opengl:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 68 as a solution to libqt4-opengl:amd64 11
  Or group remove for libqt4-opengl:amd64
Investigating (0) libplasma3 [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu3 > ( libs )
Broken libplasma3:amd64 Depends on libqt4-opengl [ amd64 ] < 4:4.7.2-0ubuntu6.3 -> 4:4.7.4-0ubuntu8 > ( libs ) (>= 4:4.7.0)
  Considering libqt4-opengl:amd64 11 as a solution to libplasma3:amd64 10
  Removing libplasma3:amd64 rather than change libqt4-opengl:amd64
Investigating (0) phonon-backend-gstreamer [ amd64 ] < 4:4.7.0really4.5.0-0ubuntu2.1 -> 4:4.7.0really4.5.1-1ubuntu3 > ( sound )
Broken phonon-backend-gstreamer:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2 -> 7.11-0ubuntu3 > ( libs )
  Considering libgl1-mesa-glx:amd64 68 as a solution to phonon-backend-gstreamer:amd64 10
Broken phonon-backend-gstreamer:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 68 as a solution to phonon-backend-gstreamer:amd64 10
  Or group remove for phonon-backend-gstreamer:amd64
Broken phonon-backend-gstreamer:amd64 Depends on libqt4-opengl [ amd64 ] < 4:4.7.2-0ubuntu6.3 -> 4:4.7.4-0ubuntu8 > ( libs ) (>= 4:4.5.3)
  Considering libqt4-opengl:amd64 11 as a solution to phonon-backend-gstreamer:amd64 10
  Removing phonon-backend-gstreamer:amd64 rather than change libqt4-opengl:amd64
Investigating (0) kde-runtime [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
Broken kde-runtime:amd64 Depends on libplasma3 [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu3 > ( libs ) (>= 4:4.6.80)
  Considering libplasma3:amd64 10 as a solution to kde-runtime:amd64 10
  Holding Back kde-runtime:amd64 rather than change libplasma3:amd64
Investigating (0) gnome-applets [ amd64 ] < 2.32.1.1-0ubuntu5 -> 3.2.0-0ubuntu1 > ( universe/gnome )
Broken gnome-applets:amd64 Depends on gnome-panel [ amd64 ] < 1:2.32.1-0ubuntu6.5 -> 1:3.2.0-0ubuntu1 > ( universe/gnome ) (>= 2.91.91)
  Considering gnome-panel:amd64 19 as a solution to gnome-applets:amd64 9
  Removing gnome-applets:amd64 rather than change gnome-panel:amd64
Investigating (0) phonon [ amd64 ] < 4:4.7.0really4.5.0-0ubuntu3 -> 4:4.7.0really4.5.0-3ubuntu4 > ( sound )
Broken phonon:amd64 Depends on phonon-backend-gstreamer [ amd64 ] < 4:4.7.0really4.5.0-0ubuntu2.1 -> 4:4.7.0really4.5.1-1ubuntu3 > ( sound )
  Considering phonon-backend-gstreamer:amd64 10 as a solution to phonon:amd64 9
Broken phonon:amd64 Depends on phonon-backend [ amd64 ] < none > ( none )
  Considering phonon-backend-gstreamer:amd64 10 as a solution to phonon:amd64 9
  Or group remove for phonon:amd64
Investigating (0) libnux-1.0-0 [ amd64 ] < none -> 1.14.0-0ubuntu1 > ( libs )
Broken libnux-1.0-0:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2 -> 7.11-0ubuntu3 > ( libs )
  Considering libgl1-mesa-glx:amd64 68 as a solution to libnux-1.0-0:amd64 9
  Holding Back libnux-1.0-0:amd64 rather than change libgl1-mesa-glx:amd64
Broken libnux-1.0-0:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 68 as a solution to libnux-1.0-0:amd64 9
  Holding Back libnux-1.0-0:amd64 rather than change libgl1:amd64
  Or group keep for libnux-1.0-0:amd64
Broken libnux-1.0-0:amd64 Depends on libglu1-mesa [ amd64 ] < 7.10.2-0ubuntu2 -> 7.11-0ubuntu3 > ( libs )
  Considering libglu1-mesa:amd64 12 as a solution to libnux-1.0-0:amd64 9
  Holding Back libnux-1.0-0:amd64 rather than change libglu1-mesa:amd64
Broken libnux-1.0-0:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 12 as a solution to libnux-1.0-0:amd64 9
  Holding Back libnux-1.0-0:amd64 rather than change libglu1:amd64
  Or group keep for libnux-1.0-0:amd64
Investigating (0) libglew1.5 [ amd64 ] < 1.5.7.is.1.5.2-1ubuntu2 -> 1.5.7.is.1.5.2-1ubuntu4 > ( libs )
Broken libglew1.5:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2 -> 7.11-0ubuntu3 > ( libs )
  Considering libgl1-mesa-glx:amd64 68 as a solution to libglew1.5:amd64 8
Broken libglew1.5:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 68 as a solution to libglew1.5:amd64 8
  Or group remove for libglew1.5:amd64
Investigating (0) gnome-session-fallback [ amd64 ] < none -> 3.2.0-0ubuntu3 > ( universe/gnome )
Broken gnome-session-fallback:amd64 Depends on gnome-settings-daemon [ amd64 ] < 2.32.1-0ubuntu13.1 -> 3.2.0-0ubuntu5 > ( gnome ) (>= 3.0)
  Considering gnome-settings-daemon:amd64 36 as a solution to gnome-session-fallback:amd64 8
  Holding Back gnome-session-fallback:amd64 rather than change gnome-settings-daemon:amd64
Investigating (0) libunity-core-4.0-4 [ amd64 ] < none -> 4.22.0-0ubuntu3 > ( libs )
Broken libunity-core-4.0-4:amd64 Depends on libnux-1.0-0 [ amd64 ] < none -> 1.14.0-0ubuntu1 > ( libs ) (>= 1.8.0-0)
  Considering libnux-1.0-0:amd64 9 as a solution to libunity-core-4.0-4:amd64 7
  Holding Back libunity-core-4.0-4:amd64 rather than change libnux-1.0-0:amd64
Investigating (0) kubuntu-debug-installer [ amd64 ] < 11.04ubuntu1 -> 11.10ubuntu1 > ( kde )
Broken kubuntu-debug-installer:amd64 Depends on kde-runtime [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
  Considering kde-runtime:amd64 10 as a solution to kubuntu-debug-installer:amd64 6
  Holding Back kubuntu-debug-installer:amd64 rather than change kde-runtime:amd64
Investigating (0) unity [ amd64 ] < 3.8.16-0ubuntu1~natty2 -> 4.22.0-0ubuntu3 > ( gnome )
Broken unity:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2 -> 7.11-0ubuntu3 > ( libs )
  Considering libgl1-mesa-glx:amd64 68 as a solution to unity:amd64 6
Broken unity:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 68 as a solution to unity:amd64 6
  Or group remove for unity:amd64
Broken unity:amd64 Depends on libglew1.5 [ amd64 ] < 1.5.7.is.1.5.2-1ubuntu2 -> 1.5.7.is.1.5.2-1ubuntu4 > ( libs ) (>= 1.5.7.is.1.5.2)
  Considering libglew1.5:amd64 8 as a solution to unity:amd64 6
  Removing unity:amd64 rather than change libglew1.5:amd64
Investigating (0) evolution [ amd64 ] < 2.32.2-0ubuntu7 -> 3.2.0-0ubuntu2 > ( gnome )
Broken evolution:amd64 Depends on libevolution [ amd64 ] < 2.32.2-0ubuntu7 -> 3.2.0-0ubuntu2 > ( gnome ) (>= 3.2)
  Considering libevolution:amd64 16 as a solution to evolution:amd64 6
  Removing evolution:amd64 rather than change libevolution:amd64
Investigating (0) plasma-scriptengine-javascript [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu5 > ( kde )
Broken plasma-scriptengine-javascript:amd64 Depends on libplasma3 [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu3 > ( libs ) (>= 4:4.6.80)
  Considering libplasma3:amd64 10 as a solution to plasma-scriptengine-javascript:amd64 6
  Removing plasma-scriptengine-javascript:amd64 rather than change libplasma3:amd64
Investigating (0) gnome-media [ amd64 ] < 2.32.0-0ubuntu7 -> 2.91.2-2ubuntu2 > ( gnome )
Broken gnome-media:amd64 Depends on x11-utils [ amd64 ] < 7.6+1 -> 7.6+3 > ( x11 )
  Considering x11-utils:amd64 35 as a solution to gnome-media:amd64 5
  Removing gnome-media:amd64 rather than change x11-utils:amd64
Investigating (0) evolution-plugins [ amd64 ] < 2.32.2-0ubuntu7 -> 3.2.0-0ubuntu2 > ( gnome )
Broken evolution-plugins:amd64 Depends on libevolution [ amd64 ] < 2.32.2-0ubuntu7 -> 3.2.0-0ubuntu2 > ( gnome ) (>= 3.2)
  Considering libevolution:amd64 16 as a solution to evolution-plugins:amd64 5
  Holding Back evolution-plugins:amd64 rather than change libevolution:amd64
Investigating (0) kde-runtime-data [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
Broken kde-runtime-data:amd64 Breaks on kdebase-runtime-data [ amd64 ] < 4:4.6.5-0ubuntu1 > ( kde )
  Considering kdebase-runtime-data:amd64 -1 as a solution to kde-runtime-data:amd64 5
  Added kdebase-runtime-data:amd64 to the remove list
Broken kde-runtime-data:amd64 Breaks on plasma-scriptengine-declarative [ amd64 ] < 4:4.6.5-0ubuntu1 > ( kde )
  Considering plasma-scriptengine-declarative:amd64 -1 as a solution to kde-runtime-data:amd64 5
  Added plasma-scriptengine-declarative:amd64 to the remove list
  Fixing kde-runtime-data:amd64 via remove of kdebase-runtime-data:amd64
  Fixing kde-runtime-data:amd64 via remove of plasma-scriptengine-declarative:amd64
Investigating (0) compiz-plugins-main-default [ amd64 ] < none -> 1:0.9.6-0ubuntu2 > ( x11 )
Broken compiz-plugins-main-default:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2 -> 7.11-0ubuntu3 > ( libs )
  Considering libgl1-mesa-glx:amd64 68 as a solution to compiz-plugins-main-default:amd64 5
  Holding Back compiz-plugins-main-default:amd64 rather than change libgl1-mesa-glx:amd64
Broken compiz-plugins-main-default:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 68 as a solution to compiz-plugins-main-default:amd64 5
  Holding Back compiz-plugins-main-default:amd64 rather than change libgl1:amd64
  Or group keep for compiz-plugins-main-default:amd64
Broken compiz-plugins-main-default:amd64 Depends on libglu1-mesa [ amd64 ] < 7.10.2-0ubuntu2 -> 7.11-0ubuntu3 > ( libs )
  Considering libglu1-mesa:amd64 12 as a solution to compiz-plugins-main-default:amd64 5
  Holding Back compiz-plugins-main-default:amd64 rather than change libglu1-mesa:amd64
Broken compiz-plugins-main-default:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 12 as a solution to compiz-plugins-main-default:amd64 5
  Holding Back compiz-plugins-main-default:amd64 rather than change libglu1:amd64
  Or group keep for compiz-plugins-main-default:amd64
Investigating (0) libglewmx1.5 [ amd64 ] < 1.5.7.is.1.5.2-1ubuntu2 -> 1.5.7.is.1.5.2-1ubuntu4 > ( libs )
Broken libglewmx1.5:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2 -> 7.11-0ubuntu3 > ( libs )
  Considering libgl1-mesa-glx:amd64 68 as a solution to libglewmx1.5:amd64 5
Broken libglewmx1.5:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 68 as a solution to libglewmx1.5:amd64 5
  Or group remove for libglewmx1.5:amd64
Investigating (0) kdebase-runtime [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu5 > ( kde )
Broken kdebase-runtime:amd64 Depends on kde-runtime [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
  Considering kde-runtime:amd64 10 as a solution to kdebase-runtime:amd64 4
  Removing kdebase-runtime:amd64 rather than change kde-runtime:amd64
Investigating (0) xbase-clients [ amd64 ] < 1:7.6+4ubuntu3.1 -> 1:7.6+7ubuntu7 > ( x11 )
Broken xbase-clients:amd64 Depends on x11-utils [ amd64 ] < 7.6+1 -> 7.6+3 > ( x11 )
  Considering x11-utils:amd64 35 as a solution to xbase-clients:amd64 3
  Removing xbase-clients:amd64 rather than change x11-utils:amd64
Investigating (0) libunity-2d-private0 [ amd64 ] < none -> 4.12.0-0ubuntu1 > ( libs )
Broken libunity-2d-private0:amd64 Depends on libnux-1.0-0 [ amd64 ] < none -> 1.14.0-0ubuntu1 > ( libs ) (>= 1.8.0-0)
  Considering libnux-1.0-0:amd64 9 as a solution to libunity-2d-private0:amd64 3
  Holding Back libunity-2d-private0:amd64 rather than change libnux-1.0-0:amd64
Investigating (0) libgl1-mesa-glx [ i386 ] < none -> 7.11-0ubuntu3 > ( libs )
Broken libgl1-mesa-glx:i386 Depends on libglapi-mesa [ i386 ] < none -> 7.11-0ubuntu3 > ( libs ) (= 7.11-0ubuntu3)
  Considering libglapi-mesa:i386 1 as a solution to libgl1-mesa-glx:i386 3
  Holding Back libgl1-mesa-glx:i386 rather than change libglapi-mesa:i386
Investigating (0) nautilus-sendto [ amd64 ] < 2.32.0-0ubuntu1.1 -> 3.0.1-0ubuntu1 > ( gnome )
Broken nautilus-sendto:amd64 Depends on nautilus [ amd64 ] < 1:2.32.2.1-0ubuntu13 -> 1:3.2.0-0ubuntu5 > ( gnome ) (>= 1:2.91)
  Considering nautilus:amd64 13 as a solution to nautilus-sendto:amd64 3
  Holding Back nautilus-sendto:amd64 rather than change nautilus:amd64
Investigating (0) libvisual-0.4-plugins [ amd64 ] < 0.4.0.dfsg.1-2ubuntu5 -> 0.4.0.dfsg.1-2ubuntu6 > ( sound )
Broken libvisual-0.4-plugins:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2 -> 7.11-0ubuntu3 > ( libs )
  Considering libgl1-mesa-glx:amd64 68 as a solution to libvisual-0.4-plugins:amd64 3
Broken libvisual-0.4-plugins:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 68 as a solution to libvisual-0.4-plugins:amd64 3
  Or group remove for libvisual-0.4-plugins:amd64
Broken libvisual-0.4-plugins:amd64 Depends on libglu1-mesa [ amd64 ] < 7.10.2-0ubuntu2 -> 7.11-0ubuntu3 > ( libs )
  Considering libglu1-mesa:amd64 12 as a solution to libvisual-0.4-plugins:amd64 3
Broken libvisual-0.4-plugins:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 12 as a solution to libvisual-0.4-plugins:amd64 3
  Or group remove for libvisual-0.4-plugins:amd64
Investigating (0) nux-tools [ amd64 ] < 0.9.48-0ubuntu1.1 -> 1.14.0-0ubuntu1 > ( x11 )
Broken nux-tools:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2 -> 7.11-0ubuntu3 > ( libs )
  Considering libgl1-mesa-glx:amd64 68 as a solution to nux-tools:amd64 3
Broken nux-tools:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 68 as a solution to nux-tools:amd64 3
  Or group remove for nux-tools:amd64
Investigating (0) compiz [ amd64 ] < 1:0.9.4+bzr20110606-0ubuntu1~natty2 -> 1:0.9.6+bzr20110929-0ubuntu3 > ( x11 )
Broken compiz:amd64 Depends on compiz-plugins-default [ amd64 ] < none -> 1:0.9.6+bzr20110929-0ubuntu3 > ( x11 ) (>= 1:0.9.6+bzr20110929-0ubuntu3)
  Considering compiz-plugins-default:amd64 12 as a solution to compiz:amd64 3
  Holding Back compiz:amd64 rather than change compiz-plugins-default:amd64
Investigating (0) libqt4-sql-mysql [ i386 ] < none -> 4:4.7.4-0ubuntu8 > ( libs )
Broken libqt4-sql-mysql:i386 Depends on libmysqlclient16 [ i386 ] < none -> 5.1.58-1ubuntu1 > ( libs ) (>= 5.1.50-1)
  Considering libmysqlclient16:i386 1 as a solution to libqt4-sql-mysql:i386 3
  Holding Back libqt4-sql-mysql:i386 rather than change libmysqlclient16:i386
Investigating (0) qapt-batch [ amd64 ] < 1.1.2-0ubuntu1 -> 1.2.1-0ubuntu2 > ( kde )
Broken qapt-batch:amd64 Depends on kde-runtime [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
  Considering kde-runtime:amd64 10 as a solution to qapt-batch:amd64 2
  Removing qapt-batch:amd64 rather than change kde-runtime:amd64
Investigating (0) libqt4-opengl [ i386 ] < none -> 4:4.7.4-0ubuntu8 > ( libs )
Broken libqt4-opengl:i386 Depends on libgl1-mesa-glx [ i386 ] < none -> 7.11-0ubuntu3 > ( libs )
  Considering libgl1-mesa-glx:i386 3 as a solution to libqt4-opengl:i386 2
  Holding Back libqt4-opengl:i386 rather than change libgl1-mesa-glx:i386
Broken libqt4-opengl:i386 Depends on libgl1 [ i386 ] < none > ( none )
  Considering libgl1-mesa-swx11:i386 0 as a solution to libqt4-opengl:i386 2
  Holding Back libqt4-opengl:i386 rather than change libgl1:i386
  Or group keep for libqt4-opengl:i386
Investigating (0) compiz-gnome [ amd64 ] < 1:0.9.4+bzr20110606-0ubuntu1~natty2 -> 1:0.9.6+bzr20110929-0ubuntu3 > ( x11 )
Broken compiz-gnome:amd64 Depends on compiz-plugins-default [ amd64 ] < none -> 1:0.9.6+bzr20110929-0ubuntu3 > ( x11 ) (= 1:0.9.6+bzr20110929-0ubuntu3)
  Considering compiz-plugins-default:amd64 12 as a solution to compiz-gnome:amd64 2
  Removing compiz-gnome:amd64 rather than change compiz-plugins-default:amd64
Investigating (0) libmtp-common [ amd64 ] < none -> 1.1.0-3ubuntu1 > ( libs )
Broken libmtp-common:amd64 Breaks on libmtp8 [ amd64 ] < 1.0.6-2 > ( libs ) (<= 1.0.6-6)
  Considering libmtp8:amd64 -1 as a solution to libmtp-common:amd64 2
  Added libmtp8:amd64 to the remove list
  Fixing libmtp-common:amd64 via remove of libmtp8:amd64
Investigating (0) python-gnome2 [ amd64 ] < 2.28.1-1ubuntu3 -> 2.28.1-3 > ( python )
Broken python-gnome2:amd64 Conflicts on python-gnomecanvas [ amd64 ] < 2.28.1-1ubuntu3 > ( python )
  Considering python-gnomecanvas:amd64 -1 as a solution to python-gnome2:amd64 1
  Added python-gnomecanvas:amd64 to the remove list
  Fixing python-gnome2:amd64 via remove of python-gnomecanvas:amd64
Investigating (0) python-pyatspi2 [ amd64 ] < none -> 2.2.0-0ubuntu1 > ( python )
Broken python-pyatspi2:amd64 Conflicts on python-pyatspi [ amd64 ] < 1.32.0-0ubuntu2 -> 1.32.0-0ubuntu3 > ( universe/libs )
  Considering python-pyatspi:amd64 0 as a solution to python-pyatspi2:amd64 1
  Added python-pyatspi:amd64 to the remove list
  Conflicts//Breaks against version 1.32.0-0ubuntu2 for python-pyatspi but that is not InstVer, ignoring
  Fixing python-pyatspi2:amd64 via remove of python-pyatspi:amd64
Investigating (0) nautilus-share [ amd64 ] < 0.7.2-14ubuntu1 -> 0.7.3-1ubuntu1 > ( gnome )
Broken nautilus-share:amd64 Depends on nautilus [ amd64 ] < 1:2.32.2.1-0ubuntu13 -> 1:3.2.0-0ubuntu5 > ( gnome ) (>= 2.10)
  Considering nautilus:amd64 13 as a solution to nautilus-share:amd64 1
  Removing nautilus-share:amd64 rather than change nautilus:amd64
Investigating (0) libevince3-3 [ amd64 ] < none -> 3.2.0-0ubuntu1 > ( libs )
Broken libevince3-3:amd64 Breaks on libevdocument3 [ amd64 ] < 2.32.0-0ubuntu12.3 > ( libs )
  Considering libevdocument3:amd64 1 as a solution to libevince3-3:amd64 1
  Holding Back libevince3-3:amd64 rather than change libevdocument3:amd64
Investigating (0) libokularcore1 [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu2 > ( libs )
Broken libokularcore1:amd64 Depends on phonon [ amd64 ] < 4:4.7.0really4.5.0-0ubuntu3 -> 4:4.7.0really4.5.0-3ubuntu4 > ( sound )
  Considering phonon:amd64 9 as a solution to libokularcore1:amd64 1
  Removing libokularcore1:amd64 rather than change phonon:amd64
Investigating (0) unity-2d-spread [ amd64 ] < none -> 4.12.0-0ubuntu1 > ( x11 )
Broken unity-2d-spread:amd64 Depends on libunity-2d-private0 [ amd64 ] < none -> 4.12.0-0ubuntu1 > ( libs ) (= 4.12.0-0ubuntu1)
  Considering libunity-2d-private0:amd64 3 as a solution to unity-2d-spread:amd64 1
  Holding Back unity-2d-spread:amd64 rather than change libunity-2d-private0:amd64
Investigating (0) konsole [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu2 > ( kde )
Broken konsole:amd64 Depends on kde-runtime [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
  Considering kde-runtime:amd64 10 as a solution to konsole:amd64 1
  Removing konsole:amd64 rather than change kde-runtime:amd64
Investigating (0) unity-2d-panel [ amd64 ] < none -> 4.12.0-0ubuntu1 > ( x11 )
Broken unity-2d-panel:amd64 Depends on libunity-2d-private0 [ amd64 ] < none -> 4.12.0-0ubuntu1 > ( libs ) (= 4.12.0-0ubuntu1)
  Considering libunity-2d-private0:amd64 3 as a solution to unity-2d-panel:amd64 1
  Holding Back unity-2d-panel:amd64 rather than change libunity-2d-private0:amd64
Investigating (0) eog [ amd64 ] < 2.32.1-0ubuntu2 -> 3.2.0-0ubuntu1 > ( gnome )
Broken eog:amd64 Depends on libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.0-0ubuntu4 > ( libs ) (>= 2.91.5)
  Considering libgnome-desktop-3-2:amd64 48 as a solution to eog:amd64 1
  Holding Back eog:amd64 rather than change libgnome-desktop-3-2:amd64
Investigating (0) gdm [ amd64 ] < 2.32.1-0ubuntu3.2 -> 3.0.4-0ubuntu11 > ( universe/gnome )
Broken gdm:amd64 Depends on gnome-session-bin [ amd64 ] < 2.32.1-0ubuntu20 -> 3.2.0-0ubuntu3 > ( gnome )
  Considering gnome-session-bin:amd64 16 as a solution to gdm:amd64 1
  Removing gdm:amd64 rather than change gnome-session-bin:amd64
Investigating (0) evince [ amd64 ] < 2.32.0-0ubuntu12.3 -> 3.2.0-0ubuntu1 > ( gnome )
Broken evince:amd64 Depends on libevince3-3 [ amd64 ] < none -> 3.2.0-0ubuntu1 > ( libs ) (= 3.2.0-0ubuntu1)
  Considering libevince3-3:amd64 1 as a solution to evince:amd64 1
  Removing evince:amd64 rather than change libevince3-3:amd64
Investigating (0) unity-2d-places [ amd64 ] < none -> 4.12.0-0ubuntu1 > ( x11 )
Broken unity-2d-places:amd64 Depends on libunity-2d-private0 [ amd64 ] < none -> 4.12.0-0ubuntu1 > ( libs ) (= 4.12.0-0ubuntu1)
  Considering libunity-2d-private0:amd64 3 as a solution to unity-2d-places:amd64 1
  Holding Back unity-2d-places:amd64 rather than change libunity-2d-private0:amd64
Investigating (0) gnome-screensaver [ amd64 ] < 2.30.2-0ubuntu2 -> 3.2.0-0ubuntu1 > ( gnome )
Broken gnome-screensaver:amd64 Depends on libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.0-0ubuntu4 > ( libs ) (>= 3.1.91)
  Considering libgnome-desktop-3-2:amd64 48 as a solution to gnome-screensaver:amd64 1
  Removing gnome-screensaver:amd64 rather than change libgnome-desktop-3-2:amd64
Investigating (0) xorg [ amd64 ] < 1:7.6+4ubuntu3.1 -> 1:7.6+7ubuntu7 > ( x11 )
Broken xorg:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2 -> 7.11-0ubuntu3 > ( libs )
  Considering libgl1-mesa-glx:amd64 68 as a solution to xorg:amd64 1
Broken xorg:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 68 as a solution to xorg:amd64 1
  Or group remove for xorg:amd64
Broken xorg:amd64 Depends on libglu1-mesa [ amd64 ] < 7.10.2-0ubuntu2 -> 7.11-0ubuntu3 > ( libs )
  Considering libglu1-mesa:amd64 12 as a solution to xorg:amd64 1
  Removing xorg:amd64 rather than change libglu1-mesa:amd64
Investigating (0) unity-2d-launcher [ amd64 ] < none -> 4.12.0-0ubuntu1 > ( x11 )
Broken unity-2d-launcher:amd64 Depends on libunity-2d-private0 [ amd64 ] < none -> 4.12.0-0ubuntu1 > ( libs ) (= 4.12.0-0ubuntu1)
  Considering libunity-2d-private0:amd64 3 as a solution to unity-2d-launcher:amd64 1
  Holding Back unity-2d-launcher:amd64 rather than change libunity-2d-private0:amd64
Investigating (0) xscreensaver-gl [ amd64 ] < 5.12-0ubuntu3 -> 5.14-1ubuntu1 > ( x11 )
Broken xscreensaver-gl:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2 -> 7.11-0ubuntu3 > ( libs )
  Considering libgl1-mesa-glx:amd64 68 as a solution to xscreensaver-gl:amd64 0
Broken xscreensaver-gl:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 68 as a solution to xscreensaver-gl:amd64 0
  Or group remove for xscreensaver-gl:amd64
Broken xscreensaver-gl:amd64 Depends on libglu1-mesa [ amd64 ] < 7.10.2-0ubuntu2 -> 7.11-0ubuntu3 > ( libs )
  Considering libglu1-mesa:amd64 12 as a solution to xscreensaver-gl:amd64 0
Broken xscreensaver-gl:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 12 as a solution to xscreensaver-gl:amd64 0
  Or group remove for xscreensaver-gl:amd64
Investigating (0) ubuntu-desktop [ amd64 ] < 1.220 -> 1.245 > ( metapackages )
Broken ubuntu-desktop:amd64 Depends on evince [ amd64 ] < 2.32.0-0ubuntu12.3 -> 3.2.0-0ubuntu1 > ( gnome )
  Considering evince:amd64 1 as a solution to ubuntu-desktop:amd64 0
  Removing ubuntu-desktop:amd64 rather than change evince:amd64
Investigating (0) gdm-guest-session [ amd64 ] < 0.24 -> 0.27 > ( universe/gnome )
Broken gdm-guest-session:amd64 Depends on gdm [ amd64 ] < 2.32.1-0ubuntu3.2 -> 3.0.4-0ubuntu11 > ( universe/gnome ) (>= 2.30.0-0ubuntu5)
  Considering gdm:amd64 1 as a solution to gdm-guest-session:amd64 0
  Removing gdm-guest-session:amd64 rather than change gdm:amd64
Investigating (0) evolution-exchange [ amd64 ] < 2.32.2-0ubuntu3 -> 3.2.0-0ubuntu2 > ( gnome )
Broken evolution-exchange:amd64 Depends on libevolution [ amd64 ] < 2.32.2-0ubuntu7 -> 3.2.0-0ubuntu2 > ( gnome ) (>= 3.2)
  Considering libevolution:amd64 16 as a solution to evolution-exchange:amd64 0
  Removing evolution-exchange:amd64 rather than change libevolution:amd64
Investigating (0) nautilus-open-terminal [ amd64 ] < 0.18-1 -> 0.19-1build1 > ( universe/gnome )
Broken nautilus-open-terminal:amd64 Depends on libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.0-0ubuntu4 > ( libs ) (>= 2.91.90)
  Considering libgnome-desktop-3-2:amd64 48 as a solution to nautilus-open-terminal:amd64 0
  Holding Back nautilus-open-terminal:amd64 rather than change libgnome-desktop-3-2:amd64
Investigating (0) driconf [ amd64 ] < 0.9.1-2ubuntu1 > ( universe/x11 )
Broken driconf:amd64 Depends on xdriinfo [ amd64 ] < none > ( none )
Broken driconf:amd64 Depends on xbase-clients [ amd64 ] < 1:7.6+4ubuntu3.1 -> 1:7.6+7ubuntu7 > ( x11 ) (> 6.8.0)
  Considering xbase-clients:amd64 3 as a solution to driconf:amd64 0
  Or group remove for driconf:amd64
Investigating (0) compiz-plugins [ amd64 ] < 1:0.9.4+bzr20110606-0ubuntu1~natty2 -> 1:0.9.6+bzr20110929-0ubuntu3 > ( x11 )
Broken compiz-plugins:amd64 Depends on compiz-plugins-default [ amd64 ] < none -> 1:0.9.6+bzr20110929-0ubuntu3 > ( x11 ) (= 1:0.9.6+bzr20110929-0ubuntu3)
  Considering compiz-plugins-default:amd64 12 as a solution to compiz-plugins:amd64 0
  Removing compiz-plugins:amd64 rather than change compiz-plugins-default:amd64
Investigating (0) gnome-font-viewer [ amd64 ] < none -> 3.2.0-0ubuntu1 > ( gnome )
Broken gnome-font-viewer:amd64 Breaks on capplets-data [ amd64 ] < 1:2.32.1-0ubuntu15 > ( gnome ) (< 1:3.0.0)
  Considering capplets-data:amd64 -1 as a solution to gnome-font-viewer:amd64 0
  Added capplets-data:amd64 to the remove list
Broken gnome-font-viewer:amd64 Breaks on gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.0-0ubuntu6 > ( gnome ) (< 1:3.0.0)
  Considering gnome-control-center:amd64 23 as a solution to gnome-font-viewer:amd64 0
  Holding Back gnome-font-viewer:amd64 rather than change gnome-control-center:amd64
Investigating (0) kile [ amd64 ] < 1:2.1.0~svn1112278beta4-2ubuntu2 -> 1:2.1.0-1ubuntu1 > ( universe/tex )
Broken kile:amd64 Depends on konsole [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu2 > ( kde )
  Considering konsole:amd64 1 as a solution to kile:amd64 0
  Removing kile:amd64 rather than change konsole:amd64
Investigating (0) libbrasero-media1 [ amd64 ] < 2.32.1-0ubuntu2 > ( libs )
Broken libbrasero-media1:amd64 Depends on brasero-common [ amd64 ] < 2.32.1-0ubuntu2 -> 3.2.0-0ubuntu1 > ( gnome ) (< 2.33)
  Considering brasero-common:amd64 14 as a solution to libbrasero-media1:amd64 -1
  Removing libbrasero-media1:amd64 rather than change brasero-common:amd64
Investigating (0) indicator-applet-complete [ amd64 ] < 0.4.12-0ubuntu1 > ( gnome )
Broken indicator-applet-complete:amd64 Depends on gnome-panel [ amd64 ] < 1:2.32.1-0ubuntu6.5 -> 1:3.2.0-0ubuntu1 > ( universe/gnome )
  Considering gnome-panel:amd64 19 as a solution to indicator-applet-complete:amd64 -1
  Removing indicator-applet-complete:amd64 rather than change gnome-panel:amd64
Investigating (0) compiz-plugins-main [ amd64 ] < 0.9.4+bzr20110527-0ubuntu1~natty1 -> 1:0.9.6-0ubuntu2 > ( x11 )
Broken compiz-plugins-main:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2 -> 7.11-0ubuntu3 > ( libs )
  Considering libgl1-mesa-glx:amd64 68 as a solution to compiz-plugins-main:amd64 -1
Broken compiz-plugins-main:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 68 as a solution to compiz-plugins-main:amd64 -1
  Or group remove for compiz-plugins-main:amd64
Broken compiz-plugins-main:amd64 Depends on compiz-plugins-main-default [ amd64 ] < none -> 1:0.9.6-0ubuntu2 > ( x11 ) (= 1:0.9.6-0ubuntu2)
  Considering compiz-plugins-main-default:amd64 5 as a solution to compiz-plugins-main:amd64 -1
  Removing compiz-plugins-main:amd64 rather than change compiz-plugins-main-default:amd64
Investigating (0) indicator-applet-appmenu [ amd64 ] < 0.4.12-0ubuntu1 > ( gnome )
Broken indicator-applet-appmenu:amd64 Depends on gnome-panel [ amd64 ] < 1:2.32.1-0ubuntu6.5 -> 1:3.2.0-0ubuntu1 > ( universe/gnome )
  Considering gnome-panel:amd64 19 as a solution to indicator-applet-appmenu:amd64 -1
  Removing indicator-applet-appmenu:amd64 rather than change gnome-panel:amd64
Investigating (0) libpulse-browse0 [ amd64 ] < 1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1 > ( sound )
Broken libpulse-browse0:amd64 Depends on libpulse0 [ amd64 ] < 1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1 -> 1:1.0-0ubuntu3 > ( libs ) (= 1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1)
  Considering libpulse0:amd64 85 as a solution to libpulse-browse0:amd64 -1
  Removing libpulse-browse0:amd64 rather than change libpulse0:amd64
Investigating (0) indicator-applet-session [ amd64 ] < 0.4.12-0ubuntu1 > ( gnome )
Broken indicator-applet-session:amd64 Depends on gnome-panel [ amd64 ] < 1:2.32.1-0ubuntu6.5 -> 1:3.2.0-0ubuntu1 > ( universe/gnome )
  Considering gnome-panel:amd64 19 as a solution to indicator-applet-session:amd64 -1
  Removing indicator-applet-session:amd64 rather than change gnome-panel:amd64
Investigating (0) libnux-0.9-0 [ amd64 ] < 0.9.48-0ubuntu1.1 > ( libs )
Broken libnux-0.9-0:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2 -> 7.11-0ubuntu3 > ( libs )
  Considering libgl1-mesa-glx:amd64 68 as a solution to libnux-0.9-0:amd64 -1
Broken libnux-0.9-0:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 68 as a solution to libnux-0.9-0:amd64 -1
  Or group remove for libnux-0.9-0:amd64
Broken libnux-0.9-0:amd64 Depends on libglew1.5 [ amd64 ] < 1.5.7.is.1.5.2-1ubuntu2 -> 1.5.7.is.1.5.2-1ubuntu4 > ( libs ) (>= 1.5.7.is.1.5.2)
  Considering libglew1.5:amd64 8 as a solution to libnux-0.9-0:amd64 -1
  Removing libnux-0.9-0:amd64 rather than change libglew1.5:amd64
Investigating (0) libperl5.10 [ amd64 ] < 5.10.1-17ubuntu4.1 > ( libs )
Broken libperl5.10:amd64 Depends on perl-base [ amd64 ] < 5.10.1-17ubuntu4.1 -> 5.12.4-4 > ( perl ) (= 5.10.1-17ubuntu4.1)
  Considering perl-base:amd64 5322 as a solution to libperl5.10:amd64 -1
  Removing libperl5.10:amd64 rather than change perl-base:amd64
Investigating (0) lib32v4l-0 [ amd64 ] < 0.8.3-1 > ( libs )
Broken lib32v4l-0:amd64 Depends on libv4l-0 [ amd64 ] < 0.8.3-1 -> 0.8.5-3ubuntu1 > ( libs ) (= 0.8.3-1)
  Considering libv4l-0:amd64 16 as a solution to lib32v4l-0:amd64 -1
  Removing lib32v4l-0:amd64 rather than change libv4l-0:amd64
Investigating (0) okular [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu2 > ( graphics )
Broken okular:amd64 Depends on kde-runtime [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
  Considering kde-runtime:amd64 10 as a solution to okular:amd64 -1
  Removing okular:amd64 rather than change kde-runtime:amd64
Investigating (0) ia32-libs-multiarch [ i386 ] < none -> 20090808ubuntu26 > ( universe/libs )
Broken ia32-libs-multiarch:i386 Depends on libqt4-opengl [ i386 ] < none -> 4:4.7.4-0ubuntu8 > ( libs )
  Considering libqt4-opengl:i386 2 as a solution to ia32-libs-multiarch:i386 -2
  Holding Back ia32-libs-multiarch:i386 rather than change libqt4-opengl:i386
Investigating (1) libglib2.0-0 [ amd64 ] < 2.28.6-0ubuntu1 -> 2.30.0-0ubuntu4 > ( libs )
Broken libglib2.0-0:amd64 Breaks on gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.0-0ubuntu6 > ( gnome ) (< 1:3)
  Considering gnome-control-center:amd64 23 as a solution to libglib2.0-0:amd64 3027
  Upgrading gnome-control-center:amd64 due to Breaks field in libglib2.0-0:amd64
Investigating (1) gvfs [ amd64 ] < 1.8.0-0ubuntu3 -> 1.10.0-0ubuntu1 > ( libs )
Broken gvfs:amd64 Depends on x11-utils [ amd64 ] < 7.6+1 -> 7.6+3 > ( x11 )
  Considering x11-utils:amd64 35 as a solution to gvfs:amd64 54
  Added x11-utils:amd64 to the remove list
  Fixing gvfs:amd64 via keep of x11-utils:amd64
 Try to Re-Instate (1) gnome-settings-daemon:amd64
 Try to Re-Instate (1) x11-utils:amd64
Investigating (1) x11-utils [ amd64 ] < 7.6+1 -> 7.6+3 > ( x11 )
Broken x11-utils:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2 -> 7.11-0ubuntu3 > ( libs )
  Considering libgl1-mesa-glx:amd64 68 as a solution to x11-utils:amd64 35
Broken x11-utils:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 68 as a solution to x11-utils:amd64 35
  Or group remove for x11-utils:amd64
Investigating (1) gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.0-0ubuntu6 > ( gnome )
Broken gnome-control-center:amd64 Depends on libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.0-0ubuntu4 > ( libs ) (>= 3.1.2)
  Considering libgnome-desktop-3-2:amd64 48 as a solution to gnome-control-center:amd64 23
  Holding Back gnome-control-center:amd64 rather than change libgnome-desktop-3-2:amd64
Investigating (1) indicator-applet [ amd64 ] < 0.4.12-0ubuntu1 > ( gnome )
Broken indicator-applet:amd64 Depends on gnome-panel [ amd64 ] < 1:2.32.1-0ubuntu6.5 -> 1:3.2.0-0ubuntu1 > ( universe/gnome )
  Considering gnome-panel:amd64 19 as a solution to indicator-applet:amd64 19
  Removing indicator-applet:amd64 rather than change gnome-panel:amd64
 Try to Re-Instate (1) libevolution:amd64
 Try to Re-Instate (1) kubuntu-debug-installer:amd64
Investigating (1) kubuntu-debug-installer [ amd64 ] < 11.04ubuntu1 -> 11.10ubuntu1 > ( kde )
Broken kubuntu-debug-installer:amd64 Depends on kdebase-runtime [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu5 > ( kde )
  Considering kdebase-runtime:amd64 4 as a solution to kubuntu-debug-installer:amd64 6
  Added kdebase-runtime:amd64 to the remove list
Broken kubuntu-debug-installer:amd64 Depends on qapt-batch [ amd64 ] < 1.1.2-0ubuntu1 -> 1.2.1-0ubuntu2 > ( kde )
  Considering qapt-batch:amd64 2 as a solution to kubuntu-debug-installer:amd64 6
  Added qapt-batch:amd64 to the remove list
  Fixing kubuntu-debug-installer:amd64 via keep of kdebase-runtime:amd64
  Fixing kubuntu-debug-installer:amd64 via keep of qapt-batch:amd64
Investigating (1) unity-2d [ amd64 ] < none -> 4.12.0-0ubuntu1 > ( x11 )
Broken unity-2d:amd64 Depends on unity-2d-launcher [ amd64 ] < none -> 4.12.0-0ubuntu1 > ( x11 )
  Considering unity-2d-launcher:amd64 1 as a solution to unity-2d:amd64 5
  Holding Back unity-2d:amd64 rather than change unity-2d-launcher:amd64
 Try to Re-Instate (1) evolution-plugins:amd64
Investigating (1) kde-runtime-data [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
Broken kde-runtime-data:amd64 Breaks on kdebase-runtime [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu5 > ( kde ) (< 4:4.6.80)
  Considering kdebase-runtime:amd64 4 as a solution to kde-runtime-data:amd64 5
  Upgrading kdebase-runtime:amd64 due to Breaks field in kde-runtime-data:amd64
Investigating (1) kdebase-runtime [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu5 > ( kde )
Broken kdebase-runtime:amd64 Depends on kde-runtime [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
  Considering kde-runtime:amd64 10 as a solution to kdebase-runtime:amd64 4
  Removing kdebase-runtime:amd64 rather than change kde-runtime:amd64
 Try to Re-Instate (1) nautilus-sendto:amd64
 Try to Re-Instate (1) compiz:amd64
Investigating (1) compiz [ amd64 ] < 1:0.9.4+bzr20110606-0ubuntu1~natty2 -> 1:0.9.6+bzr20110929-0ubuntu3 > ( x11 )
Broken compiz:amd64 Depends on compiz-plugins [ amd64 ] < 1:0.9.4+bzr20110606-0ubuntu1~natty2 -> 1:0.9.6+bzr20110929-0ubuntu3 > ( x11 ) (>= 1:0.9.4+bzr20110606-0ubuntu1~natty2)
  Considering compiz-plugins:amd64 0 as a solution to compiz:amd64 3
  Added compiz-plugins:amd64 to the remove list
Broken compiz:amd64 Depends on compiz-gnome [ amd64 ] < 1:0.9.4+bzr20110606-0ubuntu1~natty2 -> 1:0.9.6+bzr20110929-0ubuntu3 > ( x11 )
  Considering compiz-gnome:amd64 2 as a solution to compiz:amd64 3
  Added compiz-gnome:amd64 to the remove list
Broken compiz:amd64 Depends on compiz-kde [ amd64 ] < none -> 1:0.9.6+bzr20110929-0ubuntu3 > ( universe/x11 )
  Considering compiz-kde:amd64 1 as a solution to compiz:amd64 3
  Try Installing compiz-kde [ amd64 ] < none -> 1:0.9.6+bzr20110929-0ubuntu3 > ( universe/x11 ) before changing compiz:amd64
    Installing kde-runtime as Depends of compiz-kde
      Installing libplasma3 as Depends of kde-runtime
        Installing libqt4-opengl as Depends of libplasma3
          Installing libgl1-mesa-glx as Depends of libqt4-opengl
      Installing phonon as Depends of kde-runtime
        Installing phonon-backend-gstreamer as Depends of phonon
      Installing plasma-scriptengine-javascript as Depends of kde-runtime
    Installing libkdecorations4 as Depends of compiz-kde
    Installing compiz-plugins-default as Depends of compiz-kde
    Installing compizconfig-backend-kconfig as Depends of compiz-kde
Broken compiz:amd64 Depends on compiz-plugins-main [ amd64 ] < 0.9.4+bzr20110527-0ubuntu1~natty1 -> 1:0.9.6-0ubuntu2 > ( x11 ) (>= 0.9)
  Considering compiz-plugins-main:amd64 -1 as a solution to compiz:amd64 3
  Added compiz-plugins-main:amd64 to the remove list
  Fixing compiz:amd64 via keep of compiz-plugins:amd64
  Fixing compiz:amd64 via keep of compiz-gnome:amd64
  Fixing compiz:amd64 via keep of compiz-plugins-main:amd64
 Try to Re-Instate (1) qapt-batch:amd64
Re-Instated qapt-batch:amd64 (8 vs 7)
 Try to Re-Instate (1) compiz-gnome:amd64
Re-Instated compiz-gnome:amd64 (7 vs 7)
 Try to Re-Instate (1) eog:amd64
 Try to Re-Instate (1) nautilus-open-terminal:amd64
 Try to Re-Instate (1) compiz-plugins:amd64
Investigating (1) compiz-plugins [ amd64 ] < 1:0.9.4+bzr20110606-0ubuntu1~natty2 -> 1:0.9.6+bzr20110929-0ubuntu3 > ( x11 )
Broken compiz-plugins:amd64 Depends on compiz-core [ amd64 ] < 1:0.9.4+bzr20110606-0ubuntu1~natty2 -> 1:0.9.6+bzr20110929-0ubuntu3 > ( x11 ) (= 1:0.9.4+bzr20110606-0ubuntu1~natty2)
  Considering compiz-core:amd64 16 as a solution to compiz-plugins:amd64 0
  Removing compiz-plugins:amd64 rather than change compiz-core:amd64
 Try to Re-Instate (1) compiz-plugins-main:amd64
Investigating (1) compiz-plugins-main [ amd64 ] < 0.9.4+bzr20110527-0ubuntu1~natty1 -> 1:0.9.6-0ubuntu2 > ( x11 )
Broken compiz-plugins-main:amd64 Depends on libglu1-mesa [ amd64 ] < 7.10.2-0ubuntu2 -> 7.11-0ubuntu3 > ( libs )
  Considering libglu1-mesa:amd64 12 as a solution to compiz-plugins-main:amd64 -1
Broken compiz-plugins-main:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 12 as a solution to compiz-plugins-main:amd64 -1
  Or group remove for compiz-plugins-main:amd64
Broken compiz-plugins-main:amd64 Depends on compiz-core-abiversion-20110322 [ amd64 ] < none > ( none )
  Considering compiz-core:amd64 16 as a solution to compiz-plugins-main:amd64 -1
  Removing compiz-plugins-main:amd64 rather than change compiz-core-abiversion-20110322:amd64
Investigating (2) libglib2.0-0 [ amd64 ] < 2.28.6-0ubuntu1 -> 2.30.0-0ubuntu4 > ( libs )
Broken libglib2.0-0:amd64 Breaks on gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.0-0ubuntu6 > ( gnome ) (< 1:3)
  Considering gnome-control-center:amd64 23 as a solution to libglib2.0-0:amd64 3027
  Upgrading gnome-control-center:amd64 due to Breaks field in libglib2.0-0:amd64
Investigating (2) libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2 -> 7.11-0ubuntu3 > ( libs )
Broken libgl1-mesa-glx:amd64 Depends on libglapi-mesa [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs ) (= 7.11-0ubuntu3)
  Considering libglapi-mesa:amd64 19 as a solution to libgl1-mesa-glx:amd64 68
  Holding Back libgl1-mesa-glx:amd64 rather than change libglapi-mesa:amd64
Investigating (2) libgl1-mesa-dri [ amd64 ] < 7.10.2-0ubuntu2 -> 7.11-0ubuntu3 > ( libs )
Broken libgl1-mesa-dri:amd64 Breaks on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2 -> 7.11-0ubuntu3 > ( libs ) (< 7.10.3-0ubuntu1)
  Considering libgl1-mesa-glx:amd64 68 as a solution to libgl1-mesa-dri:amd64 65
  Removing libgl1-mesa-dri:amd64 rather than change libgl1-mesa-glx:amd64
Investigating (2) gvfs [ amd64 ] < 1.8.0-0ubuntu3 -> 1.10.0-0ubuntu1 > ( libs )
Broken gvfs:amd64 Depends on x11-utils [ amd64 ] < 7.6+1 -> 7.6+3 > ( x11 )
  Considering x11-utils:amd64 35 as a solution to gvfs:amd64 54
  Added x11-utils:amd64 to the remove list
  Fixing gvfs:amd64 via keep of x11-utils:amd64
Investigating (2) gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.0-0ubuntu6 > ( gnome )
Broken gnome-control-center:amd64 Depends on libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.0-0ubuntu4 > ( libs ) (>= 3.1.2)
  Considering libgnome-desktop-3-2:amd64 48 as a solution to gnome-control-center:amd64 23
  Holding Back gnome-control-center:amd64 rather than change libgnome-desktop-3-2:amd64
Investigating (2) kubuntu-debug-installer [ amd64 ] < 11.04ubuntu1 -> 11.10ubuntu1 > ( kde )
Broken kubuntu-debug-installer:amd64 Depends on kdebase-runtime [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu5 > ( kde )
  Considering kdebase-runtime:amd64 4 as a solution to kubuntu-debug-installer:amd64 6
  Added kdebase-runtime:amd64 to the remove list
  Fixing kubuntu-debug-installer:amd64 via keep of kdebase-runtime:amd64
Investigating (2) kde-runtime-data [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
Broken kde-runtime-data:amd64 Breaks on kdebase-runtime [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu5 > ( kde ) (< 4:4.6.80)
  Considering kdebase-runtime:amd64 6 as a solution to kde-runtime-data:amd64 5
  Holding Back kde-runtime-data:amd64 rather than change kdebase-runtime:amd64
Investigating (2) libgl1-mesa-dri [ i386 ] < none -> 7.11-0ubuntu3 > ( libs )
Broken libgl1-mesa-dri:i386 Breaks on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2 -> 7.11-0ubuntu3 > ( libs ) (< 7.10.3-0ubuntu1)
  Considering libgl1-mesa-glx:amd64 68 as a solution to libgl1-mesa-dri:i386 4
  Holding Back libgl1-mesa-dri:i386 rather than change libgl1-mesa-glx:amd64
 Try to Re-Instate (2) kdebase-runtime:amd64
Re-Instated kdebase-runtime:amd64 (5 vs 4)
Investigating (2) compiz [ amd64 ] < 1:0.9.4+bzr20110606-0ubuntu1~natty2 -> 1:0.9.6+bzr20110929-0ubuntu3 > ( x11 )
Broken compiz:amd64 Depends on compiz-plugins [ amd64 ] < 1:0.9.4+bzr20110606-0ubuntu1~natty2 -> 1:0.9.6+bzr20110929-0ubuntu3 > ( x11 ) (>= 1:0.9.4+bzr20110606-0ubuntu1~natty2)
  Considering compiz-plugins:amd64 0 as a solution to compiz:amd64 3
  Added compiz-plugins:amd64 to the remove list
Broken compiz:amd64 Depends on compiz-plugins-main [ amd64 ] < 0.9.4+bzr20110527-0ubuntu1~natty1 -> 1:0.9.6-0ubuntu2 > ( x11 ) (>= 0.9)
  Considering compiz-plugins-main:amd64 -1 as a solution to compiz:amd64 3
  Added compiz-plugins-main:amd64 to the remove list
  Fixing compiz:amd64 via keep of compiz-plugins:amd64
  Fixing compiz:amd64 via keep of compiz-plugins-main:amd64
Investigating (2) compiz-plugins [ amd64 ] < 1:0.9.4+bzr20110606-0ubuntu1~natty2 -> 1:0.9.6+bzr20110929-0ubuntu3 > ( x11 )
Broken compiz-plugins:amd64 Depends on compiz-core [ amd64 ] < 1:0.9.4+bzr20110606-0ubuntu1~natty2 -> 1:0.9.6+bzr20110929-0ubuntu3 > ( x11 ) (= 1:0.9.4+bzr20110606-0ubuntu1~natty2)
  Considering compiz-core:amd64 16 as a solution to compiz-plugins:amd64 3
  Removing compiz-plugins:amd64 rather than change compiz-core:amd64
Investigating (2) compiz-plugins-main [ amd64 ] < 0.9.4+bzr20110527-0ubuntu1~natty1 -> 1:0.9.6-0ubuntu2 > ( x11 )
Broken compiz-plugins-main:amd64 Depends on libglu1-mesa [ amd64 ] < 7.10.2-0ubuntu2 -> 7.11-0ubuntu3 > ( libs )
  Considering libglu1-mesa:amd64 12 as a solution to compiz-plugins-main:amd64 3
Broken compiz-plugins-main:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 12 as a solution to compiz-plugins-main:amd64 3
  Or group remove for compiz-plugins-main:amd64
Broken compiz-plugins-main:amd64 Depends on compiz-core-abiversion-20110322 [ amd64 ] < none > ( none )
  Considering compiz-core:amd64 16 as a solution to compiz-plugins-main:amd64 3
  Removing compiz-plugins-main:amd64 rather than change compiz-core-abiversion-20110322:amd64
Investigating (3) libglib2.0-0 [ amd64 ] < 2.28.6-0ubuntu1 -> 2.30.0-0ubuntu4 > ( libs )
Broken libglib2.0-0:amd64 Breaks on gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.0-0ubuntu6 > ( gnome ) (< 1:3)
  Considering gnome-control-center:amd64 23 as a solution to libglib2.0-0:amd64 3027
  Upgrading gnome-control-center:amd64 due to Breaks field in libglib2.0-0:amd64
 Try to Re-Instate (3) libgl1-mesa-glx:amd64
Investigating (3) gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.0-0ubuntu6 > ( gnome )
Broken gnome-control-center:amd64 Depends on libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.0-0ubuntu4 > ( libs ) (>= 3.1.2)
  Considering libgnome-desktop-3-2:amd64 48 as a solution to gnome-control-center:amd64 23
  Holding Back gnome-control-center:amd64 rather than change libgnome-desktop-3-2:amd64
Investigating (3) kde-runtime [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
Broken kde-runtime:amd64 Depends on kde-runtime-data [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde ) (>= 4:4.7.1-0ubuntu5)
  Considering kde-runtime-data:amd64 5 as a solution to kde-runtime:amd64 10
  Holding Back kde-runtime:amd64 rather than change kde-runtime-data:amd64
Investigating (3) kdebase-runtime [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu5 > ( kde )
Broken kdebase-runtime:amd64 Depends on kde-runtime [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
  Considering kde-runtime:amd64 10 as a solution to kdebase-runtime:amd64 6
  Removing kdebase-runtime:amd64 rather than change kde-runtime:amd64
Investigating (3) compiz [ amd64 ] < 1:0.9.4+bzr20110606-0ubuntu1~natty2 -> 1:0.9.6+bzr20110929-0ubuntu3 > ( x11 )
Broken compiz:amd64 Depends on compiz-plugins [ amd64 ] < 1:0.9.4+bzr20110606-0ubuntu1~natty2 -> 1:0.9.6+bzr20110929-0ubuntu3 > ( x11 ) (>= 1:0.9.4+bzr20110606-0ubuntu1~natty2)
  Considering compiz-plugins:amd64 16 as a solution to compiz:amd64 3
  Removing compiz:amd64 rather than change compiz-plugins:amd64
Investigating (3) qapt-batch [ amd64 ] < 1.1.2-0ubuntu1 -> 1.2.1-0ubuntu2 > ( kde )
Broken qapt-batch:amd64 Depends on kde-runtime [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
  Considering kde-runtime:amd64 10 as a solution to qapt-batch:amd64 2
  Removing qapt-batch:amd64 rather than change kde-runtime:amd64
Investigating (4) libglib2.0-0 [ amd64 ] < 2.28.6-0ubuntu1 -> 2.30.0-0ubuntu4 > ( libs )
Broken libglib2.0-0:amd64 Breaks on gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.0-0ubuntu6 > ( gnome ) (< 1:3)
  Considering gnome-control-center:amd64 23 as a solution to libglib2.0-0:amd64 3027
  Upgrading gnome-control-center:amd64 due to Breaks field in libglib2.0-0:amd64
Investigating (4) gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.0-0ubuntu6 > ( gnome )
Broken gnome-control-center:amd64 Depends on libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.0-0ubuntu4 > ( libs ) (>= 3.1.2)
  Considering libgnome-desktop-3-2:amd64 48 as a solution to gnome-control-center:amd64 23
  Holding Back gnome-control-center:amd64 rather than change libgnome-desktop-3-2:amd64
Investigating (4) kubuntu-debug-installer [ amd64 ] < 11.04ubuntu1 -> 11.10ubuntu1 > ( kde )
Broken kubuntu-debug-installer:amd64 Depends on kdebase-runtime [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu5 > ( kde )
  Considering kdebase-runtime:amd64 10 as a solution to kubuntu-debug-installer:amd64 6
  Removing kubuntu-debug-installer:amd64 rather than change kdebase-runtime:amd64
Investigating (5) libglib2.0-0 [ amd64 ] < 2.28.6-0ubuntu1 -> 2.30.0-0ubuntu4 > ( libs )
Broken libglib2.0-0:amd64 Breaks on gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.0-0ubuntu6 > ( gnome ) (< 1:3)
  Considering gnome-control-center:amd64 23 as a solution to libglib2.0-0:amd64 3027
  Upgrading gnome-control-center:amd64 due to Breaks field in libglib2.0-0:amd64
Investigating (5) gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.0-0ubuntu6 > ( gnome )
Broken gnome-control-center:amd64 Depends on libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.0-0ubuntu4 > ( libs ) (>= 3.1.2)
  Considering libgnome-desktop-3-2:amd64 48 as a solution to gnome-control-center:amd64 23
  Holding Back gnome-control-center:amd64 rather than change libgnome-desktop-3-2:amd64
Investigating (6) libglib2.0-0 [ amd64 ] < 2.28.6-0ubuntu1 -> 2.30.0-0ubuntu4 > ( libs )
Broken libglib2.0-0:amd64 Breaks on gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.0-0ubuntu6 > ( gnome ) (< 1:3)
  Considering gnome-control-center:amd64 23 as a solution to libglib2.0-0:amd64 3027
  Upgrading gnome-control-center:amd64 due to Breaks field in libglib2.0-0:amd64
Investigating (6) gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.0-0ubuntu6 > ( gnome )
Broken gnome-control-center:amd64 Depends on libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.0-0ubuntu4 > ( libs ) (>= 3.1.2)
  Considering libgnome-desktop-3-2:amd64 48 as a solution to gnome-control-center:amd64 23
  Holding Back gnome-control-center:amd64 rather than change libgnome-desktop-3-2:amd64
Investigating (7) libglib2.0-0 [ amd64 ] < 2.28.6-0ubuntu1 -> 2.30.0-0ubuntu4 > ( libs )
Broken libglib2.0-0:amd64 Breaks on gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.0-0ubuntu6 > ( gnome ) (< 1:3)
  Considering gnome-control-center:amd64 23 as a solution to libglib2.0-0:amd64 3027
  Upgrading gnome-control-center:amd64 due to Breaks field in libglib2.0-0:amd64
Investigating (7) gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.0-0ubuntu6 > ( gnome )
Broken gnome-control-center:amd64 Depends on libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.0-0ubuntu4 > ( libs ) (>= 3.1.2)
  Considering libgnome-desktop-3-2:amd64 48 as a solution to gnome-control-center:amd64 23
  Holding Back gnome-control-center:amd64 rather than change libgnome-desktop-3-2:amd64
Investigating (8) libglib2.0-0 [ amd64 ] < 2.28.6-0ubuntu1 -> 2.30.0-0ubuntu4 > ( libs )
Broken libglib2.0-0:amd64 Breaks on gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.0-0ubuntu6 > ( gnome ) (< 1:3)
  Considering gnome-control-center:amd64 23 as a solution to libglib2.0-0:amd64 3027
  Upgrading gnome-control-center:amd64 due to Breaks field in libglib2.0-0:amd64
Investigating (8) gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.0-0ubuntu6 > ( gnome )
Broken gnome-control-center:amd64 Depends on libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.0-0ubuntu4 > ( libs ) (>= 3.1.2)
  Considering libgnome-desktop-3-2:amd64 48 as a solution to gnome-control-center:amd64 23
  Holding Back gnome-control-center:amd64 rather than change libgnome-desktop-3-2:amd64
Investigating (9) libglib2.0-0 [ amd64 ] < 2.28.6-0ubuntu1 -> 2.30.0-0ubuntu4 > ( libs )
Broken libglib2.0-0:amd64 Breaks on gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.0-0ubuntu6 > ( gnome ) (< 1:3)
  Considering gnome-control-center:amd64 23 as a solution to libglib2.0-0:amd64 3027
  Upgrading gnome-control-center:amd64 due to Breaks field in libglib2.0-0:amd64
Investigating (9) gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.0-0ubuntu6 > ( gnome )
Broken gnome-control-center:amd64 Depends on libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.0-0ubuntu4 > ( libs ) (>= 3.1.2)
  Considering libgnome-desktop-3-2:amd64 48 as a solution to gnome-control-center:amd64 23
  Holding Back gnome-control-center:amd64 rather than change libgnome-desktop-3-2:amd64
Done
Log time: 2011-10-13 15:50:13.950214
```

---

### Post by zvacet on 2011-10-13
```
sudo apt-get update && sudo apt-get dist-upgrade
```

Maybe that will solve your problem.

---

### Post by LWhitson2 on 2011-10-14
Nope, that does nothing for me. When I run dist-upgrade instead of using update manager, I get the following output:

```
lunitsond@Simon:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by zvacet on 2011-10-14
```
sudo apt-get -f install
```

---

### Post by komsas on 2011-10-15
Hey, I have same problem. In the apt.log last line is "Holding Back gnome-control-center:amd64 rather than change libgnome-desktop-3-2:amd64", so I consider that it is related with gnome-control-center package. Any h elp?

---

### Post by sogood007 on 2011-10-15
I have the same problem. I wonder it is because I am using server kernel with desktop install on top of it, which seems the message indicate.

---

### Post by rajwarrior on 2011-10-15
[QUOTE=LWhitson2;11339184]Just tried to update from 11.04 to 11.10 and I got a message stating that the upgrade failed due to "Resolve generated breaks, this may be caused by held packages." Below are my log files:

Hi, I have just done an upgrade last night and was faced with a break and got almost similar situation with 300 odd held back packages.

Solved it by running sudo apt-get dist-upgrade

This throws up a sequence of errors showing 'unable to early remove' some packages.

Removed named packages one by one with sudo apt-get remove (and package name)

run sudo apt-get dist-upgrade after each package is removed. It will show some other problem.

One package gave greater problem - liblcms1. This needed me to remove the named java package when trying to remove it. Once done then all went well.

A good indicator is to see whether linux kernel 3.0.0 is being added to the boot list. Once that is done then restart should work.

BTW first boot does seem very slow. Rebooting after that works fine. 

Cheers

---

### Post by LWhitson2 on 2011-10-15
Alright, I have tried "sudo apt-get -f install" and still did not get anywhere with this installation. I am very frustrated about now. I don't completely understand RajWarriors idea because when I run "apt-get dist-upgrade" I get no output as seen above.

---

### Post by rockorequin on 2011-10-16
I had the same error message and it turned out to be a problem upgrading to the new multiarch architecture in 11.10. 

I managed to fix it by removing ia32-libs with:

```
sudo apt-get remove ia32-libs
```

Afterwards update-manager no longer gave the error ([https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/834261](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/834261)).

Note that removing ia32-libs will also remove any 32 bit apps from the system that depend on it (eg skype, wine) so you'll need to reinstall them after the upgrade (eg for skype it will probably be 'sudo apt-get install skype:i386').


Btw, 'apt-get dist-upgrade' doesn't upgrade to a new distribution release - it upgrades the current release with a 'substantial' change, such as removing a package that used to be required. And update-manager knows when and how to do this anyway. The command line to upgrade to a new distro release is 'sudo do-release-upgrade'.

---

### Post by brimble2010 on 2011-11-22
This worked for me,

I removed ia32-libs and then did an ```
apt-get autoremove
``` just to clean things up a bit.

> **rockorequin said:**
> I had the same error message and it turned out to be a problem upgrading to the new multiarch architecture in 11.10. 

I managed to fix it by removing ia32-libs with:

```
sudo apt-get remove ia32-libs
```

Afterwards update-manager no longer gave the error ([https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/834261](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/834261)).

Note that removing ia32-libs will also remove any 32 bit apps from the system that depend on it (eg skype, wine) so you'll need to reinstall them after the upgrade (eg for skype it will probably be 'sudo apt-get install skype:i386').


Btw, 'apt-get dist-upgrade' doesn't upgrade to a new distribution release - it upgrades the current release with a 'substantial' change, such as removing a package that used to be required. And update-manager knows when and how to do this anyway. The command line to upgrade to a new distro release is 'sudo do-release-upgrade'.

---

### Post by ObsessiveMathsFreak on 2013-04-03
I am getting the same errors. This is incredibly frustrating. Is there no way to simply reset apt or the like?

main.log
```

2013-04-03 23:58:31,120 INFO Using config files '['./DistUpgrade.cfg']'
2013-04-03 23:58:31,120 INFO uname information: 'Linux wutai 2.6.38-16-generic #67-Ubuntu SMP Thu Sep 6 17:58:38 UTC 2012 x86_64'
2013-04-03 23:58:31,120 INFO release-upgrader version '0.152.25.4' started
2013-04-03 23:58:31,193 DEBUG WARNING: can not get name for '<gtk.TreeSelection object at 0x23e40f0 (GtkTreeSelection at 0x2458240)>'
2013-04-03 23:58:31,193 DEBUG WARNING: can not get name for '<gtk.TreeSelection object at 0x23e4140 (GtkTreeSelection at 0x2511780)>'
2013-04-03 23:58:31,212 DEBUG svg pixbuf loader failed (Error displaying image)
2013-04-03 23:58:31,247 DEBUG Using 'DistUpgradeViewGtk' view
2013-04-03 23:58:31,272 DEBUG aufsOptionsAndEnvironmentSetup()
2013-04-03 23:58:31,272 DEBUG using '/tmp/upgrade-rw-JqIO2M' as aufs_rw_dir
2013-04-03 23:58:31,273 DEBUG using '/tmp/upgrade-chroot-YnRsUy' as aufs chroot dir
2013-04-03 23:58:31,273 DEBUG enable dpkg --force-overwrite
2013-04-03 23:58:31,288 DEBUG creating statefile: '/var/log/dist-upgrade/apt-clone_system_state.tar.gz'
2013-04-03 23:58:32,071 DEBUG lsb-release: 'natty'
2013-04-03 23:58:32,072 DEBUG _pythonSymlinkCheck run
2013-04-03 23:58:32,073 DEBUG openCache()
2013-04-03 23:58:32,073 DEBUG Plugin modules in ./plugins: kdelibs4to5_plugin.py langpack_manual_plugin.py remove_lilo_plugin.py deb_plugin.py dpkg_status_plugin.py
2013-04-03 23:58:32,073 DEBUG Loading module ./plugins/kdelibs4to5_plugin.py
2013-04-03 23:58:32,074 DEBUG Plugins in <module 'kdelibs4to5_plugin' from './plugins/kdelibs4to5_plugin.py'>: <class 'kdelibs4to5_plugin.Kdelibs4devToKdelibs5devPlugin'>
2013-04-03 23:58:32,074 DEBUG Loading module ./plugins/langpack_manual_plugin.py
2013-04-03 23:58:32,075 DEBUG Plugins in <module 'langpack_manual_plugin' from './plugins/langpack_manual_plugin.py'>: <class 'langpack_manual_plugin.MarkLangpacksManuallyInstalledPlugin'>
2013-04-03 23:58:32,076 DEBUG Loading module ./plugins/remove_lilo_plugin.py
2013-04-03 23:58:32,077 DEBUG Plugins in <module 'remove_lilo_plugin' from './plugins/remove_lilo_plugin.py'>: <class 'remove_lilo_plugin.RemoveLiloPlugin'>
2013-04-03 23:58:32,077 DEBUG Loading module ./plugins/deb_plugin.py
2013-04-03 23:58:32,077 DEBUG Plugins in <module 'deb_plugin' from './plugins/deb_plugin.py'>: <class 'deb_plugin.DebPlugin'>
2013-04-03 23:58:32,077 DEBUG Loading module ./plugins/dpkg_status_plugin.py
2013-04-03 23:58:32,079 DEBUG Plugins in <module 'dpkg_status_plugin' from './plugins/dpkg_status_plugin.py'>: <class 'dpkg_status_plugin.DpkgStatusPlugin'>
2013-04-03 23:58:32,079 DEBUG plugins for condition 'PreCacheOpen' are '[]'
2013-04-03 23:58:32,079 DEBUG plugins for condition 'oneiricPreCacheOpen' are '[]'
2013-04-03 23:58:32,079 DEBUG plugins for condition 'from_nattyPreCacheOpen' are '[]'
2013-04-03 23:58:32,079 DEBUG quirks: running PreCacheOpen
2013-04-03 23:58:32,079 DEBUG running Quirks.PreCacheOpen
2013-04-03 23:58:32,079 DEBUG quirks: running oneiricPreCacheOpen
2013-04-03 23:58:32,079 DEBUG running Quirks.oneiricPreCacheOpen
2013-04-03 23:58:32,079 DEBUG multiarch: enabling i386 as a additional architecture
2013-04-03 23:58:32,155 DEBUG /openCache(), new cache size 8595
2013-04-03 23:58:32,155 DEBUG needServerMode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
2013-04-03 23:58:32,155 DEBUG checkViewDepends()
2013-04-03 23:58:32,155 DEBUG running doUpdate() (showErrors=False)
2013-04-03 23:58:33,567 DEBUG openCache()
2013-04-03 23:58:34,215 DEBUG /openCache(), new cache size 13010
2013-04-03 23:58:34,215 DEBUG doPostInitialUpdate
2013-04-03 23:58:34,215 DEBUG plugins for condition 'PostInitialUpdate' are '[]'
2013-04-03 23:58:34,216 DEBUG plugins for condition 'oneiricPostInitialUpdate' are '[]'
2013-04-03 23:58:34,216 DEBUG plugins for condition 'from_nattyPostInitialUpdate' are '[]'
2013-04-03 23:58:34,216 DEBUG quirks: running oneiricPostInitialUpdate
2013-04-03 23:58:34,973 DEBUG Foreign: 
2013-04-03 23:58:34,973 DEBUG Obsolete: fancontrol gv nvidia-180-libvdpau-dev octave-nnet xserver-xorg-video-v4l libglc0 libopenmpi-dev libqt4-webkit python-scipy octave-fpl octave-plot libi18n-ruby1.8 ktoon paprefs module-assistant libiso9660-dev tuxtype libsynfig0 mpg123 libwxgtk2.8-0 speedbar libwsutil0 dhcp3-common octave-octcdf libsdl-gfx1.2-4 xfonts-100dpi nvidia-185-libvdpau-dev vlc monodevelop liblua5.1-expat0 libglapi-mesa libsdl1.2debian-pulseaudio-dummy libgnomepanel2.24-cil octave-io wipe libtcd0 libnfs0 libncurses-ruby1.8 python-pip mercurial transmission-cli dia cnee libtcnative-1 bcmwl-modaliases a2ps python-wicd python-wxgtk2.8 liblapack-test uswsusp libgavl1 libkate1 x264 libfaac0 libboost-date-time-dev libgnome2-canvas-perl autokey-gtk python-traitsbackendwx ruby1.9.1 libjpfcodegen-java libgeos-dev libqrupdate1 octave-optiminterp icedax octave-irsa libqt4-assistant melt octave-parallel sensors-applet xsensors vlc-nox libsox-fmt-alsa alsa-tools-gui wireshark supertux-data xnee autotrace xfonts-75dpi libgraphicsmagick++3 network-manager-openvpn libpngwriter0-dev python-aeidon texlive-latex3 libactionpack-ruby1.8 mercurial-common libslv2-9 libpnglite-dev dosbox liblockdev1 liblua5.1-socket2 gens:i386 xpdf liblualib50-dev jabref libgdata-google1.2-1 libboost-signals-dev libhdf4-0 libfolks0 octave-ann phonon-backend-xine ipe libdevkit-power-gobject1 ruby1.9.1-examples libx264-106 libmpeg2-4-dev supertux-data-stable filezilla libruby1.9.1-dbg libxvidcore4 libpango1.0-common libpdfbox-java apg libmlt3 libx264-98 libmpg123-dev frei0r-plugins libsdl-net1.2 zim flashplugin-installer octave-ident avidemux-plugins-gtk advi libggimisc2 openoffice.org-math pgplot5 gifsicle recordmydesktop libpng3 libjempbox-java gstreamer0.10-ffmpeg octave-ocs libdvdread-dev libgtksourceview-3.0-0 libportmidi0 virtualbox-ose octave-bioinfo lincity-ng-data cl-asdf sun-java6-bin libicu42 libgtkglextmm-x11-1.2-0 timidity-daemon libflickrnet2.2-cil asymptote-doc libglpk0 libsoundtouch0 html-helper-mode p7zip libiso9660-7 weechat mpi-default-bin nvidia-glx-180-dev pavumeter links libebml3 libebml2 whizzytex libsox1b octave-miscellaneous libcsiro0 libgnomevfs2-extra libsigsegv0 lame gcc-3.4 padevchooser libnice0 octave-nurbs libtext-format-ruby1.8 smartdimmer alsa-oss audacity-data libboost-program-options-dev python-enthoughtbase libvlccore4 libplplot9 python-envisageplugins elyxer libqhull5 avidemux libgtksourceview-3.0-common octave-splines libhal-storage1 libwerken.xpath-java octave-specfun libggi-target-x gstreamer0.10-plugins-bad libopencascade-foundation-6.3.0 apcalc-common docbook-xsl-doc-html openoffice.org-gtk libtcd-dev libgii1-target-x checkinstall giblib1 libtorque2 scrot nvidia-current-dev libsensors-applet-plugin0 libsdl-ttf2.0-0 octave-symbolic weechat-core prelink chromium-bsu-data enigmail ubuntu-restricted-addons libgme0 eukleides dgen octave-time cabextract octave-informationtheory gnuplot-x11 schroot liblua50-dev libcdaudio1 octave-econometrics apcalc common-lisp-controller virtualbox-ose-guest-utils gnote rake nethogs libcapi20-3 ttf-lyx gnuplot-nox libvtk5.4 libscotch-5.1 libboost-regex-dev p7zip-rar ri1.9.1 libtzinfo-ruby1.8 transmission chromium-browser-l10n libcr0 nvidia-glx-185 libmpeg2-4 cpp-3.4 nvidia-185-libvdpau libsmpeg0 virtualbox-ose-qt octave-communications-common lincity-ng alsa-firmware-loaders libwiretap0 libann0 glutg3 libwxbase2.6-0 lua50 octave-simp python-envisagecore gaupol libboost-thread-dev libvcdinfo-dev tcsh libcec libarpack2 wondershaper libboost-system-dev libgtkdatabox-0.9.1-1 lm-sensors python-opengl maxima-share asymptote id3v2 libactionmailer-ruby1.8 octave-optim libzbar0 texmaker wwwconfig-common python-visual libcddb2 libisc60 libass4 sam2p golly libsqlite3-ruby1.8 virtualbox-ose-dkms libmemcache-client-ruby1.8 libmatroska3 libmatroska2 mesa-utils audacity xulrunner-2.0 liblua5.1-rings0 libwireshark0 libwv-1.2-3 ekiga comix libopencore-amrwb-dev librack-ruby liblivemedia-dev libdvdread-dbg css-mode libdv-bin octave-control libiptcdata0 libpoppler-glib5 libgeos-c1 libdca-dev libmms0 libwxbase2.6-dev libpanelappletmm-2.6-1c2 libhal-dev rails widelands lyx-common icedtea6-plugin fxload python-pygame libtcltk-ruby octave-symband libpt2.6.7 nvidia-current libpng-sixlegs-java pybliographer nvidia-glx-173-dev hddtemp libfaad-dev sun-java6-plugin python-matplotlib-data octave-pdb paman libggi2-dev octave-combinatorics libtar git-cola libavutil-extra-50 gnome-js-common djvulibre-desktop rednotebook libalut0 libweed0 libopenal1 octave-secs2d libtar-dev libisccfg60 libshairport1 python-apptools winff ruby1.9.1-full libtheora-bin octave-xraylib octave-outliers wavpack epstool libwxbase2.8-0 libdirac-encoder0 texlive-generic-extra libautotrace3 libhal-storage-dev libmicroba-java liblapack-pic openuniverse octave-physicalconstants libdevice-modem-perl python-mpmath libeggdbus-1-0 ruby1.9.1-dev librack-ruby1.8 synfig celestia-common octave-signal libdvdnav4 ubuntu-restricted-extras mplayer libglut3 octave-linear-algebra achilles libopencore-amrwb0 sun-java6-jdk libgeos-3.2.0 libupnp3-dev octave-struct libindicate4 libdvbpsi5 sagemath-upstream-binary octave-audio libtwolame-dev libdx4 libsdl-image1.2 liboil0.3-dev octave-zenity pdfedit octave-image maxima-doc libgl2ps-dev python-matplotlib libavcodec-extra-52 blcr-util libexiv2-6 libgii1-dev nvidia-96-modaliases octave-missing-functions psfontmgr libebml-dev ttf-mscorefonts-installer xulrunner-2.0-mozjs python-fstab libcvaux2.1 mame libglazedlists-java libmjpegtools-1.9 linux-headers-2.6.35-22 lsyncd libmpeg4ip-dev vlc-plugin-notify whitedune libdevice-cdio-perl snes9x-gtk sun-java6-jre dx fceux plymouth-x11 libsmi2ldbl libhdf5-serial-dev octave3.2-headers filezilla-common libpng-sixlegs-java-doc xserver-xorg-video-nv libatlas3gf-base f-spot libginac1.5 octave-pkg-dev chromium-bsu octave-nan octave-vrml libgdata7 libwps-0.1-1 libjs-prototype libwildmidi0 libwildmidi1 nvidia-173 matchbox-keyboard-im libopencore-amrnb-dev libbreakpoint-ruby1.8 octave-financial wx2.6-headers dvdauthor openoffice.org-draw libaften0 libdvbpsi6 libebook1.2-9 python-bibtex libipe7.0.10 chromium-browser clisp libpngwriter0c2 wx2.8-headers mjpegtools lives-data octave-bim cmatrix nautilus-open-terminal libboost-regex1.40.0 python-mlt3 wv ttf-sil-doulos weechat-curses nvidia-kernel-common libgdata1.2-1 gnome-exe-thumbnailer libplib1 winff-doc libxapian15 libgnome-keyring1.0-cil asunder liblua50 maxima-emacs supertux liboil0.3 libopencore-amrnb0 avidemux-plugins-common libnetcdf6 ibus-pinyin-db-open-phrase libnspr4-0d octave3.2-common oss4-dev ppa-purge libtclap-dev lesstif2 octave-integration iotop libvcdinfo0 octave-sp fglrx-modaliases mame-common libphysfs1 libnuma1 ogmtools libhal1 mencoder libdevice-serialport-perl avidemux-common libgl2ps0 libjgoodies-looks-java linux-headers-2.6.35-28 libbluray0 openoffice.org-l10n-common libcddb2-dev libmp3lame-dev libcv2.1 gnee libpackagekit-qt-14 nvidia-180-libvdpau libopencascade-modeling-6.3.0 libtcmalloc-minimal0-dbg octave-secs1d libboost-program-options1.40.0 kdenlive lives libgtkglext1 transcode-doc octave-tsa pinyin-database libfaad2 libsidplay1 libdbusmenu-gtk1 octave-plplot libcgns2 python-matplotlib-doc nvidia-180-kernel-source libwpd8c2a kdenlive-data fceu libavidemux0 epiphany-browser-data octave-odepkg octave-statistics libsdl-sound1.2 libwxbase2.8-dev joy2key alsa-tools xulrunner-1.9.2-dev luasocket-dev libactiverecord-ruby1.8 libtelepathy-logger1 libopenjpeg2 libglpng wireshark-common openoffice.org-common php5-imagick chromium-codecs-ffmpeg pdftk octave-benchmark dx-doc rails-ruby1.8 vlc-data libx264-dev libboost-wave-dev libvlc5 twolame units epiphany-data octave-multicore libtcltk-ruby1.9.1 openmpi-bin libcelt0-0 googleearth-package openshot octave-ga libhdf4-0-alt libredcloth-ruby1.8 ttf-uralic shapelib celestia-gnome javascript-common python-traitsgui istanbul libmlt++3 ttf-sil-andika libffcall1 libedata-cal1.2-7 gnome-alsamixer libcapi20-dev maxima mimms octave-gsl p7zip-full openmpi-common mkvtoolnix nvidia-cg-toolkit slime libedataserverui1.2-8 libgnome2-vfs-perl yabasic libwpg-0.1-1 libvala-0.10-0 kile libsvga1 ftplib3 libactiveresource-ruby1.8 hal libboost-math-dev octave-mapping git-gui gtk-recordmydesktop libopal3.6.8 libafpclient0 klavaro libdns66 sysbench rubygems ttf-umefont libmlt-data libboost-filesystem-dev pychecker gstreamer0.10-plugins-ugly octave-ad libjgoodies-forms-java octave-general widelands-dbg libpoppler7 openmpi-checkpoint libmp4v2-0 nvidia-173-kernel-source libtcl-chiark-1 liblog4r-ruby1.8 freepats libwxbase2.8-dbg gstreamer0.10-plugins-bad-multiverse xxdiff libportsmf0 libpgplot-perl libfolks-telepathy0 php-elisp djview4 vlc-plugin-pulse octave-data-smoothing octave-communications libmpg123-0 libdca0 blcr-dkms openshot-doc dchroot openuniverse-common linux-headers-2.6.35-32 libtwolame0 alsa-source gnupg-curl libggimisc2-dev octave-fixed libmpfr1ldbl libsdl-mixer1.2 libdbusmenu-glib1 unrar dumphd timidity cl-swank libdevil-dev liblualib50 schroot-common pavucontrol libjpf-java preload network-manager-openvpn-gnome libsoundtouch1c2 libdvdcss2 linux-headers-2.6.35-30 lib32nss-mdns dvgrab vdpau-va-driver libquicktime1 libmpeg4ip-0 octave-sockets octave-pfstools libdvdread4 python-pyparsing octave-ftp lbzip2 libfakekey0 libfaac-dev dhcp3-client libwxbase2.6-dbg swh-plugins nvidia-glx-180 wacom-utility epiphany libopenal-dev libxvidcore-dev autokey-common libgs8 libmmap-ruby1.8 libedataserver1.2-13 tuxtype-data libhdf5-serial-1.8.4 librtmp0 python-wxversion libgnome-pilot2 xournal libspin-java octave-octgpr libgii1 sox lightyears gmsh libedata-book1.2-2 libmikmod2 libruby1.8-extras gfceu xmacro libvamp-hostsdk3 octave-msh xulrunner-1.9.2 libtcltk-ruby1.8 libhighgui2.1 supertux-stable gfortran-4.4 nvidia-173-dev libgnome2-perl libtmail-ruby1.8 libdvbpsi5-dev libcap2-bin mpi-default-dev libdvdnav-dev gtypist libruby1.9.1 python-xlib nvidia-185-kernel-source libwireshark-data dxsamples libmocha-ruby1.8 libsrtp0 libsox-fmt-base xutils faac libmp3lame0 python-tz virtualbox-ose-guest-x11 libcamel1.2-14 libboost-graph-dev libdevil1c2 octave-strings libopenmpi1.3 libggi2 lyx libmimic0 liba52-0.7.4 gstreamer0.10-plugins-ugly-multiverse nvidia-glx-173 cedet-common wmctrl nvidia-glx-185-dev python-traits gstreamer0.10-fluendo-mp3 gnuplot gcc-3.4-base libsvga1-dev octave3.2 gstreamer0.10-gconf matchbox-keyboard transcode octave-nlwing2 libsdl-pango1 python-mode rubygems1.8 libbuilder-ruby1.8 octave-epstk xpdf-reader libmatroska-dev libcmdparse2-ruby1.8 libftgl2 libgraphicsmagick3 libass-dev chromium-browser-inspector velocity libecal1.2-7 libtcmalloc-minimal0 aconnectgui libsensors3 libupnp3 libdaemons-ruby1.8 libxnee0 hal-info libactivesupport-ruby1.8 widelands-data libdb4.7 ttf-droid liba52-0.7.4-dev epdfview
2013-04-03 23:58:34,973 DEBUG updateSourcesList()
2013-04-03 23:58:35,007 DEBUG rewriteSourcesList()
2013-04-03 23:58:35,008 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu natty main'
2013-04-03 23:58:35,008 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu oneiric main' updated to new dist
2013-04-03 23:58:35,008 DEBUG examining: 'deb-src http://archive.ubuntu.com/ubuntu natty main'
2013-04-03 23:58:35,008 DEBUG entry 'deb-src http://archive.ubuntu.com/ubuntu oneiric main' updated to new dist
2013-04-03 23:58:35,008 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu natty-security main'
2013-04-03 23:58:35,008 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu oneiric-security main' updated to new dist
2013-04-03 23:58:35,008 DEBUG examining: 'deb-src http://archive.ubuntu.com/ubuntu natty-security main'
2013-04-03 23:58:35,008 DEBUG entry 'deb-src http://archive.ubuntu.com/ubuntu oneiric-security main' updated to new dist
2013-04-03 23:58:35,008 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu natty-updates main'
2013-04-03 23:58:35,008 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu oneiric-updates main' updated to new dist
2013-04-03 23:58:35,008 DEBUG examining: 'deb-src http://archive.ubuntu.com/ubuntu natty-updates main'
2013-04-03 23:58:35,008 DEBUG entry 'deb-src http://archive.ubuntu.com/ubuntu oneiric-updates main' updated to new dist
2013-04-03 23:58:35,012 DEBUG running doUpdate() (showErrors=True)
2013-04-03 23:58:46,016 DEBUG openCache()
2013-04-03 23:58:46,016 DEBUG failed to SystemUnLock() (E:Not locked) 
2013-04-03 23:58:46,722 DEBUG /openCache(), new cache size 14032
2013-04-03 23:58:46,722 DEBUG needServerMode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
2013-04-03 23:59:35,833 ERROR Dist-upgrade failed: 'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'
2013-04-03 23:59:35,833 DEBUG abort called
2013-04-03 23:59:35,835 DEBUG openCache()
2013-04-03 23:59:35,835 DEBUG failed to SystemUnLock() (E:Not locked) 
2013-04-03 23:59:36,525 DEBUG /openCache(), new cache size 13010
2013-04-03 23:59:36,525 DEBUG enabling apt cron job

```

apt.log (This file is completely unhelpful)
```

Log time: 2013-04-03 23:58:32.155259
Log time: 2013-04-03 23:58:34.213523
Log time: 2013-04-03 23:58:46.717324
  Installing kde-runtime as Depends of kubuntu-debug-installer
    Installing kde-runtime-data as Depends of kde-runtime
    Installing libcanberra-pulse as Recommends of kde-runtime
  Installing dconf-gsettings-backend as Depends of gnome-session-canberra
  Installing libperl5.12 as Depends of libpurple0
  Installing libapt-pkg4.11 as Depends of apt-transport-https
  Installing libssl1.0.0 as Depends of openssh-server
  Installing at-spi2-core as Depends of ubuntu-desktop
  Setting NOT as auto-installed (direct Depends of pkg in APT::Never-MarkAuto-Sections)
    Installing libatspi2.0-0 as Depends of at-spi2-core
  Installing gnome-font-viewer as Depends of ubuntu-desktop
  Setting NOT as auto-installed (direct Depends of pkg in APT::Never-MarkAuto-Sections)
  Installing libatk-adaptor as Depends of ubuntu-desktop
  Setting NOT as auto-installed (direct Depends of pkg in APT::Never-MarkAuto-Sections)
  Installing libnotify-bin as Depends of ubuntu-desktop
  Setting NOT as auto-installed (direct Depends of pkg in APT::Never-MarkAuto-Sections)
  Installing lightdm as Depends of ubuntu-desktop
  Setting NOT as auto-installed (direct Depends of pkg in APT::Never-MarkAuto-Sections)
    Installing unity-greeter as Recommends of lightdm
      Installing libindicator3-6 as Depends of unity-greeter
      Installing liblightdm-gobject-1-0 as Depends of unity-greeter
        Installing accountsservice as Recommends of liblightdm-gobject-1-0
          Installing libaccountsservice0 as Depends of accountsservice
  Installing unity-2d as Depends of ubuntu-desktop
  Setting NOT as auto-installed (direct Depends of pkg in APT::Never-MarkAuto-Sections)
    Installing unity-2d-launcher as Depends of unity-2d
      Installing libdconf-qt0 as Depends of unity-2d-launcher
        Installing libdconf-dbus-1-0 as Depends of libdconf-qt0
      Installing libgeis1 as Depends of unity-2d-launcher
        Installing libgrail1 as Depends of libgeis1
          Installing libevemu1 as Depends of libgrail1
          Installing libframe1 as Depends of libgrail1
      Installing libunity-2d-private0 as Depends of unity-2d-launcher
        Installing libnux-1.0-0 as Depends of libunity-2d-private0
          Installing libnux-1.0-common as Depends of libnux-1.0-0
        Installing libqtbamf1 as Depends of libunity-2d-private0
        Installing libqtdee2 as Depends of libunity-2d-private0
        Installing libunity-core-4.0-4 as Depends of libunity-2d-private0
          Installing unity-services as Depends of libunity-core-4.0-4
        Installing libwnck-3-0 as Depends of libunity-2d-private0
          Installing libwnck-3-common as Depends of libwnck-3-0
      Installing unity-lens-files as Recommends of unity-2d-launcher
        Installing libunity6 as Depends of unity-lens-files
          Installing libdbusmenu-glib4 as Depends of libunity6
      Installing unity-lens-applications as Recommends of unity-2d-launcher
      Installing unity-lens-music as Recommends of unity-2d-launcher
        Installing unity-scope-musicstores as Recommends of unity-lens-music
    Installing unity-2d-panel as Depends of unity-2d
      Installing libqtgconf1 as Depends of unity-2d-panel
    Installing unity-2d-places as Depends of unity-2d
    Installing unity-2d-spread as Depends of unity-2d
  Installing xdiagnose as Depends of ubuntu-desktop
  Setting NOT as auto-installed (direct Depends of pkg in APT::Never-MarkAuto-Sections)
    Installing gir1.2-gtk-3.0 as Depends of xdiagnose
  new important dependency: c2esp
  Installing c2esp as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
  new important dependency: deja-dup
  Installing deja-dup as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
    Installing libdbusmenu-gtk3-4 as Depends of deja-dup
    Installing libgnome-control-center1 as Depends of deja-dup
    Installing duplicity as Depends of deja-dup
      Installing librsync1 as Depends of duplicity
    Installing ubuntuone-couch as Recommends of deja-dup
  new important dependency: ibus-gtk3
  Installing ibus-gtk3 as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
    Installing libibus-1.0-0 as Depends of ibus-gtk3
  new important dependency: libgail-3-common
  Installing libgail-3-common as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
    Installing libgail-3-0 as Depends of libgail-3-common
  new important dependency: ptouch-driver
  Installing ptouch-driver as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
  new important dependency: qt-at-spi
  Installing qt-at-spi as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
  new important dependency: rastertosag-gdi
  Installing rastertosag-gdi as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
  new important dependency: sni-qt
  Installing sni-qt as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
  new important dependency: thunderbird-gnome-support
  Installing thunderbird-gnome-support as Recommends of ubuntu-desktop
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
    Installing libdbusmenu-gtk4 as Depends of thunderbird-gnome-support
    Installing libebook1.2-12 as Depends of thunderbird-gnome-support
      Installing libcamel-1.2-29 as Depends of libebook1.2-12
        Installing libedataserver1.2-15 as Depends of libcamel-1.2-29
  Installing libbamf3-0 as Depends of unity
  Installing libgnome-desktop-3-2 as Depends of unity
    Installing gnome-desktop3-data as Depends of libgnome-desktop-3-2
  Installing libunity-misc4 as Depends of unity
  Installing compiz-plugins-main-default as Depends of unity
    Installing libboost-serialization1.46.1 as Depends of compiz-plugins-main-default
  new important dependency: indicator-power
  Installing indicator-power as Recommends of unity
  Installing gcc-4.6-base as Depends of libstdc++6
  Installing libdbus-glib1.0-cil as Depends of tomboy
    Installing libdbus1.0-cil as Depends of libdbus-glib1.0-cil
      Installing libmono-corlib4.0-cil as Depends of libdbus1.0-cil
        Installing libmono-i18n-west4.0-cil as Recommends of libmono-corlib4.0-cil
          Installing libmono-i18n4.0-cil as Depends of libmono-i18n-west4.0-cil
      Installing libmono-system-core4.0-cil as Depends of libdbus1.0-cil
        Installing libmono-posix4.0-cil as Depends of libmono-system-core4.0-cil
          Installing libmono-system4.0-cil as Depends of libmono-posix4.0-cil
            Installing libmono-security4.0-cil as Depends of libmono-system4.0-cil
            Installing libmono-system-configuration4.0-cil as Depends of libmono-system4.0-cil
              Installing libmono-system-security4.0-cil as Depends of libmono-system-configuration4.0-cil
                Installing libmono-system-xml4.0-cil as Depends of libmono-system-security4.0-cil
  Installing libmono-cairo4.0-cil as Depends of tomboy
  Installing libavformat53 as Depends of libavformat-dev
    Installing libavcodec53 as Depends of libavformat53
      Installing libavutil51 as Depends of libavcodec53
  Installing libcanberra-gtk3-0 as Depends of libevolution
    Installing libcanberra-gtk3-module as Recommends of libcanberra-gtk3-0
  Installing libecal1.2-10 as Depends of libevolution
  Installing libedataserverui-3.0-1 as Depends of libevolution
  Installing libgoa-1.0-0 as Depends of libevolution
    Installing librest-0.7-0 as Depends of libgoa-1.0-0
    Installing libwebkitgtk-3.0-0 as Depends of libgoa-1.0-0
      Installing libwebkitgtk-3.0-common as Depends of libwebkitgtk-3.0-0
  Installing libgtkhtml-4.0-0 as Depends of libevolution
    Installing libgtkhtml-4.0-common as Depends of libgtkhtml-4.0-0
  Installing libgtkhtml-editor-4.0-0 as Depends of libevolution
  Installing liblaunchpad-integration-3.0-1 as Depends of libevolution
  Installing libtinfo5 as Depends of libncurses5
  Installing libindicate-gtk3 as Depends of pidgin-libnotify
  new important dependency: indicator-status-provider-pidgin
  Installing indicator-status-provider-pidgin as Recommends of pidgin-libnotify
    Installing libindicator-messages-status-provider1 as Depends of indicator-status-provider-pidgin
  Installing libdb5.1 as Depends of iproute
  Installing libgmp10 as Depends of libmpfr4
  Installing libgnome-media-profiles-3.0-0 as Depends of gnome-media
  Installing libprotobuf7 as Depends of libcompizconfig0
  Installing libappindicator3-1 as Depends of update-notifier
  Installing ubuntuone-installer as Depends of ubuntuone-control-panel-gtk
  Installing libgvnc-1.0-0 as Depends of libgtk-vnc-1.0-0
  Installing lib32tinfo5 as Depends of lib32ncurses5
  Installing libgcj12 as Depends of libgcj-bc
    Installing gcj-4.6-base as Depends of libgcj12
    Installing gcj-4.6-jre-lib as Recommends of libgcj12
  new important dependency: gir1.2-unity-4.0
  Installing gir1.2-unity-4.0 as Recommends of ubuntuone-client
  Installing libnm-glib4 as Depends of network-manager-gnome
    Installing libnm-util2 as Depends of libnm-glib4
  Installing libnm-gtk0 as Depends of network-manager-gnome
    Installing libnm-gtk-common as Depends of libnm-gtk0
  Installing libraptor2-0 as Depends of librdf0
    Installing libyajl1 as Depends of libraptor2-0
  Installing librasqal3 as Depends of librdf0
    Installing libmhash2 as Depends of librasqal3
  Installing libyaml-tiny-perl as Depends of doc-base
  Installing libgucharmap-2-90-7 as Depends of gucharmap
  Installing zenity-common as Depends of zenity
  Installing libgdata13 as Depends of totem-plugins
    Installing liboauth0 as Depends of libgdata13
  Installing libtotem0 as Depends of totem-plugins
    Installing libpeas-1.0-0 as Depends of libtotem0
      Installing libpeas-common as Depends of libpeas-1.0-0
  Installing gir1.2-totem-1.0 as Depends of totem-plugins
    Installing gir1.2-totem-plparser-1.0 as Depends of gir1.2-totem-1.0
  Installing gir1.2-peas-1.0 as Depends of totem-plugins
  Installing libgweather-3-0 as Depends of evolution
  Installing gir1.2-vte-2.90 as Depends of language-selector-gnome
    Installing libvte-2.90-9 as Depends of gir1.2-vte-2.90
  Installing libunique-3.0-0 as Depends of gnome-disk-utility
  Installing libcolord1 as Depends of gnome-settings-daemon
    Installing colord as Recommends of libcolord1
      Installing liblcms2-2 as Depends of colord
      Installing acl as Depends of colord
      Installing icc-profiles-free as Recommends of colord
  Installing libgnomekbd7 as Depends of gnome-settings-daemon
  Installing libevent-2.0-5 as Depends of transmission-cli
  Installing libminiupnpc5 as Depends of transmission-cli
  Installing libnatpmp1 as Depends of transmission-cli
  Installing qdbus as Depends of libqt4-dbus
  Installing librhythmbox-core4 as Depends of rhythmbox
  new important dependency: gir1.2-gtksource-3.0
  Installing gir1.2-gtksource-3.0 as Recommends of gedit
  Installing libllvm2.9 as Depends of libgl1-mesa-dri
    Installing libffi6 as Depends of libllvm2.9
  Installing libgtkmm-3.0-1 as Depends of gnome-system-monitor
  Installing libdlrestrictions1 as Depends of libkdecore5
  Installing libtinfo-dev as Depends of libncurses5-dev
  Installing libebackend-1.2-1 as Depends of evolution-exchange
  Installing libedata-book-1.2-11 as Depends of evolution-exchange
  Installing libedata-cal-1.2-13 as Depends of evolution-exchange
  Installing gir1.2-launchpad-integration-3.0 as Depends of gnome-sudoku
  Installing lib32tinfo-dev as Depends of lib32ncursesw5-dev
  Installing python-gobject-2 as Depends of python-indicate
  Installing libmono-csharp4.0-cil as Depends of gbrainy
  Installing libgck-1-0 as Depends of seahorse
    Installing libp11-kit0 as Depends of libgck-1-0
  Installing libgcr-3-1 as Depends of seahorse
  Installing libboost-iostreams1.46.1 as Depends of aptitude
  Installing libfolks-telepathy25 as Depends of empathy
    Installing libfolks25 as Depends of libfolks-telepathy25
  Installing libido3-0.1-0 as Depends of empathy
  new important dependency: telepathy-indicator
  Installing telepathy-indicator as Recommends of empathy
  Installing libapt-inst1.3 as Depends of python-apt
  Installing liboverlay-scrollbar-0.2-0 as Depends of overlay-scrollbar
  Installing liboverlay-scrollbar3-0.2-0 as Depends of overlay-scrollbar
  Installing gcc-4.6-multilib as Depends of gcc-multilib
    Installing gcc-4.6 as Depends of gcc-4.6-multilib
      Installing cpp-4.6 as Depends of gcc-4.6
      Installing libquadmath0 as Depends of gcc-4.6
    Installing lib32quadmath0 as Depends of gcc-4.6-multilib
  Installing libxcb-util0 as Depends of libstartup-notification0
  new important dependency: libswitch-perl
  Installing libswitch-perl as Recommends of perl-modules
  new important dependency: libpod-plainer-perl
  Installing libpod-plainer-perl as Recommends of perl-modules
  new important dependency: libclass-isa-perl
  Installing libclass-isa-perl as Recommends of perl-modules
  Installing libavahi-ui-gtk3-0 as Depends of vinagre
  Installing libgtk-vnc-2.0-0 as Depends of vinagre
  Installing gir1.2-gmenu-3.0 as Depends of software-center
    Installing libgnome-menu-3-0 as Depends of gir1.2-gmenu-3.0
  Installing gir1.2-webkit-3.0 as Depends of software-center
  Installing oneconf as Depends of software-center
  Installing g++-4.6 as Depends of g++
    Installing libstdc++6-4.6-dev as Depends of g++-4.6
  Installing nvidia-current as Depends of nvidia-185-libvdpau
  Installing sound-theme-freedesktop as Depends of libcanberra0
  Installing libmono-sharpzip4.84-cil as Depends of libmono-addins0.2-cil
  Installing libmtp9 as Depends of banshee
    Installing libmtp-common as Depends of libmtp9
    Installing libmtp-runtime as Recommends of libmtp9
  Installing grub2-common as Depends of grub-pc
  Installing grub-pc-bin as Depends of grub-pc
  Installing dh-translations as Depends of cdbs
  Installing libkonq5abi1 as Depends of dolphin
    Installing libkonq-common as Depends of libkonq5abi1
  new important dependency: anthy
  Installing anthy as Recommends of m17n-db
    Installing anthy-common as Depends of anthy
  new important dependency: ispell
  Installing ispell as Recommends of m17n-db
    Installing iamerican as Recommends of ispell
      Installing ienglish-common as Depends of iamerican
  Installing libboost-test1.46-dev as Depends of libboost-test-dev
    Installing libboost1.46-dev as Depends of libboost-test1.46-dev
    Installing libboost-test1.46.1 as Depends of libboost-test1.46-dev
  Installing libmono-management4.0-cil as Depends of mono-csharp-shell
  new important dependency: gir1.2-dbusmenu-gtk-0.4
  Installing gir1.2-dbusmenu-gtk-0.4 as Recommends of update-manager
  Installing libswscale2 as Depends of libswscale-dev
  Installing qt4-linguist-tools as Depends of libqt4-dev
  Installing libboost1.42-dev as Depends of libboost-math1.42-dev
  Installing python-pyatspi2 as Depends of gnome-orca
    Installing gir1.2-atspi-2.0 as Depends of python-pyatspi2
  Installing gir1.2-wnck-3.0 as Depends of gnome-orca
  Installing libboost-serialization1.46-dev as Depends of libboost-serialization-dev
  Installing nvidia-173 as Depends of nvidia-173-kernel-source
  Installing libnl3 as Depends of network-manager
  Installing libmaa3 as Depends of dict
  Installing libmtp8 as Depends of vlc-nox
  Installing libgrip0 as Depends of eog
  Installing libmono-system-data4.0-cil as Depends of libmono-db2-1.0-cil
    Installing libmono-data-tds4.0-cil as Depends of libmono-system-data4.0-cil
    Installing libmono-system-enterpriseservices4.0-cil as Depends of libmono-system-data4.0-cil
      Installing libmono-system-transactions4.0-cil as Depends of libmono-system-enterpriseservices4.0-cil
  new important dependency: libssl-doc
  Installing libssl-doc as Recommends of libssl-dev
  Installing mono-4.0-gac as Depends of mono-gac
  new important dependency: indicator-status-provider-mc5
  Installing indicator-status-provider-mc5 as Recommends of indicator-messages
  Installing gir1.2-gnomebluetooth-1.0 as Depends of gnome-bluetooth
  previously satisfied important dependency on indicator-me
  Installing indicator-me as Recommends of indicator-applet-session
  Installing gfortran-4.6 as Depends of gfortran
  Installing software-properties-common as Depends of software-properties-gtk
  Installing libcogl5 as Depends of libclutter-1.0-0
    Installing libcogl-common as Recommends of libcogl5
  Installing compiz-plugins-default as Depends of compiz-gnome
  Installing libgladeui-2-0 as Depends of glade
    Installing libgladeui-common as Depends of libgladeui-2-0
  new important dependency: libgtk-3-dev
  Installing libgtk-3-dev as Recommends of glade
  Installing linux-headers-3.0.0-32-generic as Depends of linux-headers-generic
    Installing linux-headers-3.0.0-32 as Depends of linux-headers-3.0.0-32-generic
  Installing libavdevice53 as Depends of ffmpeg
  Installing libavfilter2 as Depends of ffmpeg
  Installing libpostproc52 as Depends of ffmpeg
  Installing linux-image-3.0.0-32-generic as Depends of linux-image-generic
  Setting NOT as auto-installed (direct Depends of pkg in APT::Never-MarkAuto-Sections)
  Installing libevince3-3 as Depends of evince
  Installing libsigsegv2 as PreDepends of gawk
  Installing libppl-c4 as Depends of libcloog-ppl0
    Installing libppl9 as Depends of libppl-c4
    Installing libpwl5 as Depends of libppl-c4
  Installing libc6 as Depends of gens
    Installing libgcc1 as Depends of libc6
      Installing gcc-4.6-base as Depends of libgcc1
  Installing libgl1-mesa-glx as Depends of gens
    Installing libdrm2 as Depends of libgl1-mesa-glx
    Installing libglapi-mesa as Depends of libgl1-mesa-glx
    Installing libx11-6 as Depends of libgl1-mesa-glx
      Installing libxcb1 as Depends of libx11-6
        Installing libxau6 as Depends of libxcb1
        Installing libxdmcp6 as Depends of libxcb1
    Installing libxdamage1 as Depends of libgl1-mesa-glx
    Installing libxext6 as Depends of libgl1-mesa-glx
    Installing libxfixes3 as Depends of libgl1-mesa-glx
    Installing libxxf86vm1 as Depends of libgl1-mesa-glx
    Installing libgl1-mesa-dri as Recommends of libgl1-mesa-glx
      Installing libdrm-intel1 as Depends of libgl1-mesa-dri
        Installing libpciaccess0 as Depends of libdrm-intel1
          Installing zlib1g as Depends of libpciaccess0
      Installing libdrm-nouveau1a as Depends of libgl1-mesa-dri
      Installing libdrm-radeon1 as Depends of libgl1-mesa-dri
      Installing libexpat1 as Depends of libgl1-mesa-dri
      Installing libllvm2.9 as Depends of libgl1-mesa-dri
        Installing libffi6 as Depends of libllvm2.9
        Installing libstdc++6 as Depends of libllvm2.9
  Installing libglib2.0-0 as Depends of gens
    Installing libpcre3 as Depends of libglib2.0-0
    Installing libselinux1 as Depends of libglib2.0-0
  Installing libgtk2.0-0 as Depends of gens
    Installing libatk1.0-0 as Depends of libgtk2.0-0
    Installing libcairo2 as Depends of libgtk2.0-0
      Installing libfontconfig1 as Depends of libcairo2
        Installing libfreetype6 as Depends of libfontconfig1
      Installing libpixman-1-0 as Depends of libcairo2
      Installing libpng12-0 as Depends of libcairo2
      Installing libxcb-render0 as Depends of libcairo2
      Installing libxcb-shm0 as Depends of libcairo2
      Installing libxrender1 as Depends of libcairo2
    Installing libcups2 as Depends of libgtk2.0-0
      Installing libavahi-client3 as Depends of libcups2
        Installing libavahi-common3 as Depends of libavahi-client3
          Installing libavahi-common-data as Depends of libavahi-common3
        Installing libdbus-1-3 as Depends of libavahi-client3
      Installing libgnutls26 as Depends of libcups2
        Installing libgcrypt11 as Depends of libgnutls26
          Installing libgpg-error0 as Depends of libgcrypt11
        Installing libtasn1-3 as Depends of libgnutls26
      Installing libgssapi-krb5-2 as Depends of libcups2
        Installing libcomerr2 as Depends of libgssapi-krb5-2
        Installing libk5crypto3 as Depends of libgssapi-krb5-2
          Installing libkrb5support0 as Depends of libk5crypto3
        Installing libkrb5-3 as Depends of libgssapi-krb5-2
          Installing libkeyutils1 as Depends of libkrb5-3
    Installing libgdk-pixbuf2.0-0 as Depends of libgtk2.0-0
      Installing libjasper1 as Depends of libgdk-pixbuf2.0-0
        Installing libjpeg62 as Depends of libjasper1
      Installing libtiff4 as Depends of libgdk-pixbuf2.0-0
    Installing libpango1.0-0 as Depends of libgtk2.0-0
      Installing libthai0 as Depends of libpango1.0-0
        Installing libdatrie1 as Depends of libthai0
      Installing libxft2 as Depends of libpango1.0-0
    Installing libxcomposite1 as Depends of libgtk2.0-0
    Installing libxcursor1 as Depends of libgtk2.0-0
    Installing libxi6 as Depends of libgtk2.0-0
    Installing libxinerama1 as Depends of libgtk2.0-0
    Installing libxrandr2 as Depends of libgtk2.0-0
  Installing libsdl1.2debian as Depends of gens
    Installing libsdl1.2debian-alsa as Depends of libsdl1.2debian
      Installing libasound2 as Depends of libsdl1.2debian-alsa
  new important dependency: appmenu-gtk3
  Installing appmenu-gtk3 as Recommends of indicator-appmenu
  new important dependency: appmenu-qt
  Installing appmenu-qt as Recommends of indicator-appmenu
  Installing gir1.2-indicate-0.6 as Depends of gwibber-service
  Installing libsdl1.2debian as Depends of chromium-bsu
    Installing libsdl1.2debian-alsa as Depends of libsdl1.2debian
  Installing libindicator6 as Depends of libappindicator1
  Installing libyelp0 as Depends of yelp
  Installing libbrasero-media3-1 as Depends of brasero-cdrkit
  new important dependency: keyutils
  Installing keyutils as Recommends of cifs-utils
  new important dependency: gir1.2-appindicator3-0.1
  Installing gir1.2-appindicator3-0.1 as Recommends of onboard
  Installing libprotoc7 as Depends of protobuf-compiler
  Installing gnome-control-center-data as Depends of gnome-control-center
  new important dependency: gnome-icon-theme-symbolic
  Installing gnome-icon-theme-symbolic as Recommends of gnome-control-center
  new important dependency: gnome-online-accounts
  Installing gnome-online-accounts as Recommends of gnome-control-center
  Installing libmount1 as PreDepends of mount
  Installing libjson0 as Depends of libpulse0
  Installing libhttp-daemon-perl as Depends of librpc-xml-perl
    Installing libhttp-message-perl as Depends of libhttp-daemon-perl
      Installing libhttp-date-perl as Depends of libhttp-message-perl
      Installing libencode-locale-perl as Depends of libhttp-message-perl
      Installing liblwp-mediatypes-perl as Depends of libhttp-message-perl
  Installing libgnutlsxx26 as Depends of libgnutls-dev
  previously satisfied important dependency on alacarte
  Installing alacarte as Recommends of gnome-panel
  Installing libmono-codecontracts4.0-cil as Depends of mono-devel
  Installing libmono-compilerservices-symbolwriter4.0-cil as Depends of mono-devel
  Installing libmono-peapi4.0-cil as Depends of mono-devel
  Installing libmono-relaxng4.0-cil as Depends of mono-devel
  Installing libmono-system-configuration-install4.0-cil as Depends of mono-devel
  Installing libmono-system-data-linq4.0-cil as Depends of mono-devel
    Installing libmono-system-runtime-serialization4.0-cil as Depends of libmono-system-data-linq4.0-cil
  Installing libmono-system-runtime4.0-cil as Depends of mono-devel
    Installing libmono-system-runtime-serialization-formatters-soap4.0-cil as Depends of libmono-system-runtime4.0-cil
    Installing libmono-system-web4.0-cil as Depends of libmono-system-runtime4.0-cil
      Installing libmono-sqlite4.0-cil as Depends of libmono-system-web4.0-cil
      Installing libmono-system-drawing4.0-cil as Depends of libmono-system-web4.0-cil
      Installing libmono-system-web-applicationservices4.0-cil as Depends of libmono-system-web4.0-cil
      Installing libmono-system-web-services4.0-cil as Depends of libmono-system-web4.0-cil
      Installing libmono-web4.0-cil as Depends of libmono-system-web4.0-cil
  Installing libmono-system-servicemodel4.0-cil as Depends of mono-devel
    Installing libmono-system-identitymodel-selectors4.0-cil as Depends of libmono-system-servicemodel4.0-cil
      Installing libmono-system-identitymodel4.0-cil as Depends of libmono-system-identitymodel-selectors4.0-cil
    Installing libmono-system-messaging4.0-cil as Depends of libmono-system-servicemodel4.0-cil
      Installing libmono-messaging4.0-cil as Depends of libmono-system-messaging4.0-cil
      Installing libmono-system-windows-forms4.0-cil as Depends of libmono-system-messaging4.0-cil
        Installing libmono-accessibility4.0-cil as Depends of libmono-system-windows-forms4.0-cil
        Installing libmono-webbrowser4.0-cil as Depends of libmono-system-windows-forms4.0-cil
  Installing mono-dmcs as Depends of mono-devel
    Installing libmono-microsoft-csharp4.0-cil as Depends of mono-dmcs
  Installing mono-xbuild as Depends of mono-devel
    Installing libmono-microsoft-build-engine4.0-cil as Depends of mono-xbuild
      Installing libmono-microsoft-build-framework4.0-cil as Depends of libmono-microsoft-build-engine4.0-cil
      Installing libmono-microsoft-build-utilities-v4.0-4.0-cil as Depends of libmono-microsoft-build-engine4.0-cil
    Installing libmono-microsoft-build-tasks-v4.0-4.0-cil as Depends of mono-xbuild
  Installing libmono-2.0-dev as Depends of mono-devel
    Installing libmono-2.0-1 as Depends of libmono-2.0-dev
  Installing libfile-listing-perl as Depends of libwww-perl
  Installing libhttp-cookies-perl as Depends of libwww-perl
  Installing libhttp-negotiate-perl as Depends of libwww-perl
  Installing liblwp-protocol-https-perl as Depends of libwww-perl
    Installing libnet-http-perl as Depends of liblwp-protocol-https-perl
      Installing libio-socket-ssl-perl as Recommends of libnet-http-perl
        Installing libnet-ssleay-perl as Depends of libio-socket-ssl-perl
  Installing libwww-robotrules-perl as Depends of libwww-perl
  new important dependency: libhtml-form-perl
  Installing libhtml-form-perl as Recommends of libwww-perl
  Installing libjte1 as Depends of libisofs6
  Installing mythes-en-au as Depends of openoffice.org-thesaurus-en-au
  Setting NOT as auto-installed (direct Depends of pkg in APT::Never-MarkAuto-Sections)
  Installing libkadm5srv-mit8 as Depends of krb5-multidev
    Installing libkdb5-5 as Depends of libkadm5srv-mit8
  Installing libkadm5clnt-mit8 as Depends of krb5-multidev
  Installing libgwibber-gtk2 as Depends of gwibber
    Installing libgtkspell3-0 as Depends of libgwibber-gtk2
    Installing libgwibber2 as Depends of libgwibber-gtk2
  Installing nvidia-current as Depends of nvidia-current-dev
  Installing libdmapsharing-3.0-2 as Depends of rhythmbox-plugins
  Installing gir1.2-rb-3.0 as Depends of rhythmbox-plugins
    Installing gir1.2-gstreamer-0.10 as Depends of gir1.2-rb-3.0
  Installing libboost-iostreams1.46-dev as Depends of libboost-iostreams-dev
    Installing libboost-regex1.46-dev as Depends of libboost-iostreams1.46-dev
      Installing libboost-regex1.46.1 as Depends of libboost-regex1.46-dev
  Installing katepart as Depends of kdelibs5-plugins
    Installing kate-data as Depends of katepart
  Installing libkdegames5a as Depends of konquest
  Installing gtk3-engines-unico as Depends of light-themes
  Installing g++-4.6-multilib as Depends of g++-multilib
  Installing libdevhelp-3-0 as Depends of devhelp
  new important dependency: libgtk-3-doc
  Installing libgtk-3-doc as Recommends of devhelp
  Installing libnunit2.5-cil as Depends of libnunit-cil-dev
  Installing libmono-webbrowser2.0-cil as Depends of libmono-winforms2.0-cil
  Installing libmono-custommarshalers4.0-cil as Depends of libmono-cil-dev
  Installing libmono-debugger-soft2.0-cil as Depends of libmono-cil-dev
  Installing libmono-debugger-soft4.0-cil as Depends of libmono-cil-dev
  Installing libmono-http4.0-cil as Depends of libmono-cil-dev
  Installing libmono-i18n4.0-all as Depends of libmono-cil-dev
    Installing libmono-i18n-cjk4.0-cil as Depends of libmono-i18n4.0-all
    Installing libmono-i18n-mideast4.0-cil as Depends of libmono-i18n4.0-all
    Installing libmono-i18n-other4.0-cil as Depends of libmono-i18n4.0-all
    Installing libmono-i18n-rare4.0-cil as Depends of libmono-i18n4.0-all
  Installing libmono-ldap4.0-cil as Depends of libmono-cil-dev
  Installing libmono-messaging-rabbitmq4.0-cil as Depends of libmono-cil-dev
    Installing libmono-rabbitmq4.0-cil as Depends of libmono-messaging-rabbitmq4.0-cil
  Installing libmono-microsoft-visualc10.0-cil as Depends of libmono-cil-dev
  Installing libmono-microsoft-web-infrastructure1.0-cil as Depends of libmono-cil-dev
  Installing libmono-npgsql4.0-cil as Depends of libmono-cil-dev
  Installing libmono-opensystem-c4.0-cil as Depends of libmono-cil-dev
  Installing libmono-oracle4.0-cil as Depends of libmono-cil-dev
  Installing libmono-simd4.0-cil as Depends of libmono-cil-dev
  Installing libmono-system-componentmodel-composition4.0-cil as Depends of libmono-cil-dev
  Installing libmono-system-componentmodel-dataannotations4.0-cil as Depends of libmono-cil-dev
  Installing libmono-system-data-datasetextensions4.0-cil as Depends of libmono-cil-dev
  Installing libmono-system-data-services4.0-cil as Depends of libmono-cil-dev
    Installing libmono-system-servicemodel-web4.0-cil as Depends of libmono-system-data-services4.0-cil
      Installing libmono-system-web-extensions4.0-cil as Depends of libmono-system-servicemodel-web4.0-cil
  Installing libmono-system-data-services-client4.0-cil as Depends of libmono-cil-dev
    Installing libmono-system-xml-linq4.0-cil as Depends of libmono-system-data-services-client4.0-cil
  Installing libmono-system-design4.0-cil as Depends of libmono-cil-dev
    Installing libmono-system-drawing-design4.0-cil as Depends of libmono-system-design4.0-cil
  Installing libmono-system-dynamic4.0-cil as Depends of libmono-cil-dev
  Installing libmono-system-ldap4.0-cil as Depends of libmono-cil-dev
  Installing libmono-system-management4.0-cil as Depends of libmono-cil-dev
  Installing libmono-system-net4.0-cil as Depends of libmono-cil-dev
  Installing libmono-system-numerics4.0-cil as Depends of libmono-cil-dev
  Installing libmono-system-runtime-caching4.0-cil as Depends of libmono-cil-dev
  Installing libmono-system-runtime-durableinstancing4.0-cil as Depends of libmono-cil-dev
  Installing libmono-system-servicemodel-discovery4.0-cil as Depends of libmono-cil-dev
  Installing libmono-system-servicemodel-routing4.0-cil as Depends of libmono-cil-dev
  Installing libmono-system-serviceprocess4.0-cil as Depends of libmono-cil-dev
  Installing libmono-system-web-abstractions4.0-cil as Depends of libmono-cil-dev
  Installing libmono-system-web-dynamicdata4.0-cil as Depends of libmono-cil-dev
  Installing libmono-system-web-extensions-design4.0-cil as Depends of libmono-cil-dev
  Installing libmono-system-web-routing4.0-cil as Depends of libmono-cil-dev
  Installing libmono-system-windows-forms-datavisualization4.0-cil as Depends of libmono-cil-dev
  Installing libmono-system-xaml4.0-cil as Depends of libmono-cil-dev
  Installing libmono-tasklets4.0-cil as Depends of libmono-cil-dev
  Installing libmono-webmatrix-data4.0-cil as Depends of libmono-cil-dev
  Installing libmono-windowsbase4.0-cil as Depends of libmono-cil-dev
  new important dependency: libgphoto2-l10n
  Installing libgphoto2-l10n as Recommends of libgphoto2-2
Starting
Starting 2
Investigating (0) libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
Broken libgl1-mesa-glx:amd64 Depends on libglapi-mesa [ amd64 ] < 7.11.0+git20110222.7aeb610f-0ubuntu0sarvatt~maverick > ( libs ) (= 7.11-0ubuntu3.2)
  Considering libglapi-mesa:amd64 57 as a solution to libgl1-mesa-glx:amd64 238
  Removing libgl1-mesa-glx:amd64 rather than change libglapi-mesa:amd64
Investigating (0) libc6-dev [ amd64 ] < 2.13-0ubuntu13.2 -> 2.13-20ubuntu5.3 > ( libdevel )
Broken libc6-dev:amd64 Breaks on gcj-4.5-base [ amd64 ] < 4.5.2-8ubuntu1 > ( libs ) (< 4.5.3-1ubuntu2)
  Considering gcj-4.5-base:amd64 2 as a solution to libc6-dev:amd64 147
  Added gcj-4.5-base:amd64 to the remove list
  Fixing libc6-dev:amd64 via remove of gcj-4.5-base:amd64
Investigating (0) octave3.2 [ amd64 ] < 3.2.4-8 > ( math )
Broken octave3.2:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to octave3.2:amd64 126
Broken octave3.2:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to octave3.2:amd64 126
  Or group remove for octave3.2:amd64
Investigating (0) libglu1-mesa [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
Broken libglu1-mesa:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to libglu1-mesa:amd64 121
Broken libglu1-mesa:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to libglu1-mesa:amd64 121
  Or group remove for libglu1-mesa:amd64
Investigating (0) libdbusmenu-glib4 [ amd64 ] < none -> 0.5.0-0ubuntu3 > ( libs )
Broken libdbusmenu-glib4:amd64 Breaks on gir1.2-unity-3.0 [ amd64 ] < 3.8.4-0ubuntu1 > ( libs ) (< 3.8.4-0ubuntu2)
  Considering gir1.2-unity-3.0:amd64 5 as a solution to libdbusmenu-glib4:amd64 85
  Added gir1.2-unity-3.0:amd64 to the remove list
  Fixing libdbusmenu-glib4:amd64 via remove of gir1.2-unity-3.0:amd64
Investigating (0) libmono-corlib1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono )
Broken libmono-corlib1.0-cil:amd64 Depends on mono-runtime [ amd64 ] < 2.6.7-5ubuntu3.1 -> 2.10.5-1ubuntu0.1 > ( interpreters ) (< 2.6.8)
  Considering mono-runtime:amd64 923 as a solution to libmono-corlib1.0-cil:amd64 81
  Removing libmono-corlib1.0-cil:amd64 rather than change mono-runtime:amd64
Investigating (0) libfltk1.1 [ amd64 ] < 1.1.10-3 -> 1.1.10-7 > ( libs )
Broken libfltk1.1:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to libfltk1.1:amd64 74
Broken libfltk1.1:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to libfltk1.1:amd64 74
  Or group remove for libfltk1.1:amd64
Investigating (0) libftgl2 [ amd64 ] < 2.1.3~rc5-3 > ( libs )
Broken libftgl2:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to libftgl2:amd64 66
Broken libftgl2:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to libftgl2:amd64 66
  Or group remove for libftgl2:amd64
Broken libftgl2:amd64 Depends on libglu1-mesa [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libglu1-mesa:amd64 121 as a solution to libftgl2:amd64 66
Broken libftgl2:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 121 as a solution to libftgl2:amd64 66
  Or group remove for libftgl2:amd64
Investigating (0) gvfs [ amd64 ] < 1.8.0-0ubuntu4 -> 1.10.0-0ubuntu1.1 > ( libs )
Broken gvfs:amd64 Conflicts on libgvfscommon0 [ amd64 ] < 1.8.0-0ubuntu4 > ( libs )
  Considering libgvfscommon0:amd64 -1 as a solution to gvfs:amd64 62
  Added libgvfscommon0:amd64 to the remove list
  Fixing gvfs:amd64 via remove of libgvfscommon0:amd64
Investigating (0) libglapi-mesa [ amd64 ] < 7.11.0+git20110222.7aeb610f-0ubuntu0sarvatt~maverick > ( libs )
Broken libglapi-mesa:amd64 Conflicts on libglapi-mesa [ i386 ] < none -> 7.11-0ubuntu3.2 > ( libs )
  Considering libglapi-mesa:i386 0 as a solution to libglapi-mesa:amd64 57
  Added libglapi-mesa:i386 to the remove list
  Conflicts//Breaks against version 7.11-0ubuntu3 for libglapi-mesa but that is not InstVer, ignoring
  Fixing libglapi-mesa:amd64 via keep of libglapi-mesa:i386
Investigating (0) x11-utils [ amd64 ] < 7.6+1 -> 7.6+3 > ( x11 )
Broken x11-utils:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to x11-utils:amd64 49
Broken x11-utils:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to x11-utils:amd64 49
  Or group remove for x11-utils:amd64
Investigating (0) libmono-system1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono )
Broken libmono-system1.0-cil:amd64 Depends on libmono-corlib1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono ) (>= 1.2.2.1)
  Considering libmono-corlib1.0-cil:amd64 81 as a solution to libmono-system1.0-cil:amd64 47
  Removing libmono-system1.0-cil:amd64 rather than change libmono-corlib1.0-cil:amd64
Investigating (0) libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.1-0ubuntu1.1 > ( libs )
Broken libgnome-desktop-3-2:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to libgnome-desktop-3-2:amd64 36
  Holding Back libgnome-desktop-3-2:amd64 rather than change libgl1-mesa-glx:amd64
Broken libgnome-desktop-3-2:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to libgnome-desktop-3-2:amd64 36
  Holding Back libgnome-desktop-3-2:amd64 rather than change libgl1:amd64
  Or group keep for libgnome-desktop-3-2:amd64
Investigating (0) gstreamer0.10-plugins-good [ amd64 ] < 0.10.29-1~maverick1 -> 0.10.30-1ubuntu7.1 > ( libs )
Broken gstreamer0.10-plugins-good:amd64 Breaks on gstreamer0.10-plugins-bad [ amd64 ] < 0.10.22-1~maverick2 > ( libs ) (< 0.10.22-2ubuntu4)
  Considering gstreamer0.10-plugins-bad:amd64 -1 as a solution to gstreamer0.10-plugins-good:amd64 32
  Added gstreamer0.10-plugins-bad:amd64 to the remove list
  Fixing gstreamer0.10-plugins-good:amd64 via remove of gstreamer0.10-plugins-bad:amd64
Investigating (0) gnome-settings-daemon [ amd64 ] < 2.32.1-0ubuntu14~audiohacks1 -> 3.2.2-0ubuntu2.3 > ( gnome )
Broken gnome-settings-daemon:amd64 Depends on libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.1-0ubuntu1.1 > ( libs ) (>= 3.1.5)
  Considering libgnome-desktop-3-2:amd64 36 as a solution to gnome-settings-daemon:amd64 31
  Holding Back gnome-settings-daemon:amd64 rather than change libgnome-desktop-3-2:amd64
Investigating (0) libmono-i18n-west1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono )
Broken libmono-i18n-west1.0-cil:amd64 Depends on libmono-corlib1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono ) (>= 1.2.2.1)
  Considering libmono-corlib1.0-cil:amd64 81 as a solution to libmono-i18n-west1.0-cil:amd64 30
  Removing libmono-i18n-west1.0-cil:amd64 rather than change libmono-corlib1.0-cil:amd64
Investigating (0) plymouth [ amd64 ] < 0.8.2-2ubuntu23 -> 0.8.2-2ubuntu28 > ( x11 )
Broken plymouth:amd64 Breaks on gdm [ amd64 ] < 2.32.1-0ubuntu3.2 > ( gnome ) (< 3.0.4-0ubuntu11)
  Considering gdm:amd64 1 as a solution to plymouth:amd64 24
  Added gdm:amd64 to the remove list
  Fixing plymouth:amd64 via remove of gdm:amd64
Investigating (0) console-setup [ amd64 ] < 1.57ubuntu20 -> 1.57ubuntu27 > ( utils )
Broken console-setup:amd64 Conflicts on console-terminus [ amd64 ] < 4.30-2 > ( fonts )
  Considering console-terminus:amd64 -1 as a solution to console-setup:amd64 20
  Added console-terminus:amd64 to the remove list
  Fixing console-setup:amd64 via remove of console-terminus:amd64
Investigating (0) gnome-session [ amd64 ] < 2.32.1-0ubuntu20 -> 3.2.1-0ubuntu1.1 > ( gnome )
Broken gnome-session:amd64 Depends on gnome-settings-daemon [ amd64 ] < 2.32.1-0ubuntu14~audiohacks1 -> 3.2.2-0ubuntu2.3 > ( gnome ) (>= 3.0)
  Considering gnome-settings-daemon:amd64 31 as a solution to gnome-session:amd64 20
  Removing gnome-session:amd64 rather than change gnome-settings-daemon:amd64
Investigating (0) gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.2-0ubuntu1 > ( gnome )
Broken gnome-control-center:amd64 Depends on libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.1-0ubuntu1.1 > ( libs ) (>= 3.1.2)
  Considering libgnome-desktop-3-2:amd64 36 as a solution to gnome-control-center:amd64 20
  Holding Back gnome-control-center:amd64 rather than change libgnome-desktop-3-2:amd64
Investigating (0) gnome-menus [ amd64 ] < 2.30.5-0ubuntu3 -> 3.2.0-0ubuntu2 > ( gnome )
Broken gnome-menus:amd64 Breaks on alacarte [ amd64 ] < 0.13.2-1ubuntu2 > ( utils ) (< 0.13.2-2)
  Considering alacarte:amd64 6 as a solution to gnome-menus:amd64 18
  Added alacarte:amd64 to the remove list
  Fixing gnome-menus:amd64 via remove of alacarte:amd64
Investigating (0) ntfs-3g [ amd64 ] < 1:2010.8.8-0ubuntu1 -> 1:2011.4.12AR.4-2ubuntu3 > ( otherosfs )
Broken ntfs-3g:amd64 Conflicts on ntfsprogs [ amd64 ] < 2.0.0-1ubuntu4 > ( otherosfs )
  Considering ntfsprogs:amd64 6 as a solution to ntfs-3g:amd64 18
  Added ntfsprogs:amd64 to the remove list
  Fixing ntfs-3g:amd64 via remove of ntfsprogs:amd64
Investigating (0) gnome-control-center-data [ amd64 ] < none -> 1:3.2.2-0ubuntu1 > ( gnome )
Broken gnome-control-center-data:amd64 Conflicts on capplets-data [ amd64 ] < 1:2.32.1-0ubuntu15 > ( gnome )
  Considering capplets-data:amd64 -1 as a solution to gnome-control-center-data:amd64 17
  Added capplets-data:amd64 to the remove list
Broken gnome-control-center-data:amd64 Breaks on gnome-settings-daemon [ amd64 ] < 2.32.1-0ubuntu14~audiohacks1 -> 3.2.2-0ubuntu2.3 > ( gnome ) (< 3.0~)
  Considering gnome-settings-daemon:amd64 31 as a solution to gnome-control-center-data:amd64 17
  Holding Back gnome-control-center-data:amd64 rather than change gnome-settings-daemon:amd64
Investigating (0) kde-runtime [ amd64 ] < none -> 4:4.7.4-0ubuntu0.1 > ( kde )
Broken kde-runtime:amd64 Breaks on plasma-scriptengine-declarative [ amd64 ] < 4:4.6.5-0ubuntu1 > ( kde )
  Considering plasma-scriptengine-declarative:amd64 -1 as a solution to kde-runtime:amd64 17
  Added plasma-scriptengine-declarative:amd64 to the remove list
  Fixing kde-runtime:amd64 via remove of plasma-scriptengine-declarative:amd64
Investigating (0) libevolution [ amd64 ] < 2.32.2-0ubuntu7 -> 3.2.2-0ubuntu0.1 > ( gnome )
Broken libevolution:amd64 Depends on libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.1-0ubuntu1.1 > ( libs ) (>= 2.91.5)
  Considering libgnome-desktop-3-2:amd64 36 as a solution to libevolution:amd64 16
  Holding Back libevolution:amd64 rather than change libgnome-desktop-3-2:amd64
Investigating (0) nautilus [ amd64 ] < 1:2.32.2.1-0ubuntu13 -> 1:3.2.1-0ubuntu4.2 > ( gnome )
Broken nautilus:amd64 Depends on libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.1-0ubuntu1.1 > ( libs ) (>= 3.0.0)
  Considering libgnome-desktop-3-2:amd64 36 as a solution to nautilus:amd64 15
  Removing nautilus:amd64 rather than change libgnome-desktop-3-2:amd64
Investigating (0) libmono-system-data1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono )
Broken libmono-system-data1.0-cil:amd64 Depends on libmono-corlib1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono ) (>= 1.2.2.1)
  Considering libmono-corlib1.0-cil:amd64 81 as a solution to libmono-system-data1.0-cil:amd64 14
  Removing libmono-system-data1.0-cil:amd64 rather than change libmono-corlib1.0-cil:amd64
Investigating (0) gnome-session-bin [ amd64 ] < 2.32.1-0ubuntu20 -> 3.2.1-0ubuntu1.1 > ( gnome )
Broken gnome-session-bin:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to gnome-session-bin:amd64 13
Broken gnome-session-bin:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to gnome-session-bin:amd64 13
  Or group remove for gnome-session-bin:amd64
Investigating (0) indicator-messages [ amd64 ] < 0.4.0-0ubuntu1 -> 0.5.0-0ubuntu1 > ( gnome )
Broken indicator-messages:amd64 Conflicts on indicator-me [ amd64 ] < 0.2.19-0ubuntu1 > ( gnome )
  Considering indicator-me:amd64 1 as a solution to indicator-messages:amd64 13
  Added indicator-me:amd64 to the remove list
  Fixing indicator-messages:amd64 via remove of indicator-me:amd64
Investigating (0) compiz-plugins-default [ amd64 ] < none -> 1:0.9.6+bzr20110929-0ubuntu6.1 > ( x11 )
Broken compiz-plugins-default:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to compiz-plugins-default:amd64 12
  Holding Back compiz-plugins-default:amd64 rather than change libgl1-mesa-glx:amd64
Broken compiz-plugins-default:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to compiz-plugins-default:amd64 12
  Holding Back compiz-plugins-default:amd64 rather than change libgl1:amd64
  Or group keep for compiz-plugins-default:amd64
Investigating (0) libqt4-opengl [ amd64 ] < 4:4.7.2-0ubuntu6.4 -> 4:4.7.4-0ubuntu8.3 > ( libs )
Broken libqt4-opengl:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to libqt4-opengl:amd64 12
Broken libqt4-opengl:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to libqt4-opengl:amd64 12
  Or group remove for libqt4-opengl:amd64
Investigating (0) synaptic [ amd64 ] < 0.75.1ubuntu2 > ( admin )
Broken synaptic:amd64 Depends on libapt-inst1.2 [ amd64 ] < none > ( none )
  Considering apt-utils:amd64 99 as a solution to synaptic:amd64 12
  Removing synaptic:amd64 rather than change libapt-inst1.2:amd64
Investigating (0) freeglut3 [ amd64 ] < 2.6.0-1ubuntu2 > ( libs )
Broken freeglut3:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to freeglut3:amd64 11
Broken freeglut3:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to freeglut3:amd64 11
  Or group remove for freeglut3:amd64
Investigating (0) python-gnome2 [ amd64 ] < 2.28.1-1ubuntu3 -> 2.28.1-3 > ( python )
Broken python-gnome2:amd64 Conflicts on python-gnomecanvas [ amd64 ] < 2.28.1-1ubuntu3 > ( python )
  Considering python-gnomecanvas:amd64 -1 as a solution to python-gnome2:amd64 10
  Added python-gnomecanvas:amd64 to the remove list
  Fixing python-gnome2:amd64 via remove of python-gnomecanvas:amd64
Investigating (0) libglew1.5 [ amd64 ] < 1.5.7.is.1.5.2-1ubuntu2 -> 1.5.7.is.1.5.2-1ubuntu4 > ( libs )
Broken libglew1.5:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to libglew1.5:amd64 10
Broken libglew1.5:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to libglew1.5:amd64 10
  Or group remove for libglew1.5:amd64
Investigating (0) kde-runtime-data [ amd64 ] < none -> 4:4.7.4-0ubuntu0.1 > ( kde )
Broken kde-runtime-data:amd64 Breaks on kdebase-runtime-data [ amd64 ] < 4:4.6.5-0ubuntu1 > ( kde )
  Considering kdebase-runtime-data:amd64 -1 as a solution to kde-runtime-data:amd64 10
  Added kdebase-runtime-data:amd64 to the remove list
  Fixing kde-runtime-data:amd64 via remove of kdebase-runtime-data:amd64
Investigating (0) libglib2.0-0 [ i386 ] < none -> 2.30.0-0ubuntu4 > ( libs )
Broken libglib2.0-0:i386 Breaks on gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.2-0ubuntu1 > ( gnome ) (< 1:3)
  Considering gnome-control-center:amd64 20 as a solution to libglib2.0-0:i386 9
  Holding Back libglib2.0-0:i386 rather than change gnome-control-center:amd64
Investigating (0) libwxgtk2.8-0 [ amd64 ] < 2.8.11.0-0ubuntu8.1 > ( libs )
Broken libwxgtk2.8-0:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to libwxgtk2.8-0:amd64 9
Broken libwxgtk2.8-0:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to libwxgtk2.8-0:amd64 9
  Or group remove for libwxgtk2.8-0:amd64
Broken libwxgtk2.8-0:amd64 Depends on libglu1-mesa [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libglu1-mesa:amd64 121 as a solution to libwxgtk2.8-0:amd64 9
Broken libwxgtk2.8-0:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 121 as a solution to libwxgtk2.8-0:amd64 9
  Or group remove for libwxgtk2.8-0:amd64
Investigating (0) libnux-1.0-0 [ amd64 ] < none -> 1.16.0-0ubuntu1.1 > ( libs )
Broken libnux-1.0-0:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to libnux-1.0-0:amd64 9
  Holding Back libnux-1.0-0:amd64 rather than change libgl1-mesa-glx:amd64
Broken libnux-1.0-0:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to libnux-1.0-0:amd64 9
  Holding Back libnux-1.0-0:amd64 rather than change libgl1:amd64
  Or group keep for libnux-1.0-0:amd64
Broken libnux-1.0-0:amd64 Depends on libglew1.5 [ amd64 ] < 1.5.7.is.1.5.2-1ubuntu2 -> 1.5.7.is.1.5.2-1ubuntu4 > ( libs ) (>= 1.5.7.is.1.5.2)
  Considering libglew1.5:amd64 10 as a solution to libnux-1.0-0:amd64 9
  Holding Back libnux-1.0-0:amd64 rather than change libglew1.5:amd64
Investigating (0) libnspr4-0d [ amd64 ] < 4.8.7-0ubuntu1 > ( libs )
Broken libnspr4-0d:amd64 Depends on libnspr4 [ amd64 ] < 4.8.7-0ubuntu1 -> 4.9.5-0ubuntu0.11.10.1 > ( libs ) (= 4.8.7-0ubuntu1)
  Considering libnspr4:amd64 121 as a solution to libnspr4-0d:amd64 8
  Removing libnspr4-0d:amd64 rather than change libnspr4:amd64
Investigating (0) libmono-data-tds1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono )
Broken libmono-data-tds1.0-cil:amd64 Depends on libmono-corlib1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono ) (>= 1.2.2.1)
  Considering libmono-corlib1.0-cil:amd64 81 as a solution to libmono-data-tds1.0-cil:amd64 8
  Removing libmono-data-tds1.0-cil:amd64 rather than change libmono-corlib1.0-cil:amd64
Investigating (0) libunity-core-4.0-4 [ amd64 ] < none -> 4.30.0-0ubuntu1 > ( libs )
Broken libunity-core-4.0-4:amd64 Depends on libnux-1.0-0 [ amd64 ] < none -> 1.16.0-0ubuntu1.1 > ( libs ) (>= 1.8.0-0)
  Considering libnux-1.0-0:amd64 9 as a solution to libunity-core-4.0-4:amd64 7
  Holding Back libunity-core-4.0-4:amd64 rather than change libnux-1.0-0:amd64
Investigating (0) octave-miscellaneous [ amd64 ] < 1.0.9-1build2 > ( math )
Broken octave-miscellaneous:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-miscellaneous:amd64 7
  Removing octave-miscellaneous:amd64 rather than change octave3.2:amd64
Investigating (0) libmono-webbrowser4.0-cil [ amd64 ] < none -> 2.10.5-1ubuntu0.1 > ( cli-mono )
Broken libmono-webbrowser4.0-cil:amd64 Conflicts on libmono-webbrowser0.5-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono )
  Considering libmono-webbrowser0.5-cil:amd64 -1 as a solution to libmono-webbrowser4.0-cil:amd64 7
  Added libmono-webbrowser0.5-cil:amd64 to the remove list
  Fixing libmono-webbrowser4.0-cil:amd64 via remove of libmono-webbrowser0.5-cil:amd64
Investigating (0) unity [ amd64 ] < 3.8.16-0ubuntu1~natty3 -> 4.30.0-0ubuntu1 > ( gnome )
Broken unity:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to unity:amd64 6
Broken unity:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to unity:amd64 6
  Or group remove for unity:amd64
Broken unity:amd64 Depends on libglew1.5 [ amd64 ] < 1.5.7.is.1.5.2-1ubuntu2 -> 1.5.7.is.1.5.2-1ubuntu4 > ( libs ) (>= 1.5.7.is.1.5.2)
  Considering libglew1.5:amd64 10 as a solution to unity:amd64 6
  Removing unity:amd64 rather than change libglew1.5:amd64
Investigating (0) evolution [ amd64 ] < 2.32.2-0ubuntu7 -> 3.2.2-0ubuntu0.1 > ( gnome )
Broken evolution:amd64 Depends on libevolution [ amd64 ] < 2.32.2-0ubuntu7 -> 3.2.2-0ubuntu0.1 > ( gnome ) (>= 3.2)
  Considering libevolution:amd64 16 as a solution to evolution:amd64 6
  Removing evolution:amd64 rather than change libevolution:amd64
Investigating (0) libglewmx1.5 [ amd64 ] < 1.5.7.is.1.5.2-1ubuntu2 -> 1.5.7.is.1.5.2-1ubuntu4 > ( libs )
Broken libglewmx1.5:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to libglewmx1.5:amd64 6
Broken libglewmx1.5:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to libglewmx1.5:amd64 6
  Or group remove for libglewmx1.5:amd64
Investigating (0) evolution-plugins [ amd64 ] < 2.32.2-0ubuntu7 -> 3.2.2-0ubuntu0.1 > ( gnome )
Broken evolution-plugins:amd64 Depends on libevolution [ amd64 ] < 2.32.2-0ubuntu7 -> 3.2.2-0ubuntu0.1 > ( gnome ) (>= 3.2)
  Considering libevolution:amd64 16 as a solution to evolution-plugins:amd64 5
  Holding Back evolution-plugins:amd64 rather than change libevolution:amd64
Investigating (0) libmono-system-web1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono )
Broken libmono-system-web1.0-cil:amd64 Depends on libmono-corlib1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono ) (>= 1.2.2.1)
  Considering libmono-corlib1.0-cil:amd64 81 as a solution to libmono-system-web1.0-cil:amd64 5
  Removing libmono-system-web1.0-cil:amd64 rather than change libmono-corlib1.0-cil:amd64
Investigating (0) dia [ amd64 ] < 0.97.1-7build1 > ( graphics )
Broken dia:amd64 Depends on dia-common [ amd64 ] < 0.97.1-7build1 -> 0.97.1-9 > ( graphics ) (= 0.97.1-7build1)
  Considering dia-common:amd64 5 as a solution to dia:amd64 5
  Removing dia:amd64 rather than change dia-common:amd64
Investigating (0) network-manager [ amd64 ] < 0.8.4~git.20110319t175609.d14809b-0ubuntu3.1 -> 0.9.1.90-0ubuntu5.2 > ( net )
Broken network-manager:amd64 Breaks on network-manager-openvpn [ amd64 ] < 0.8.1+git.20100810t173015.1711d04-0ubuntu2 > ( universe/net ) (< 0.8.99)
  Considering network-manager-openvpn:amd64 0 as a solution to network-manager:amd64 5
  Added network-manager-openvpn:amd64 to the remove list
  Fixing network-manager:amd64 via remove of network-manager-openvpn:amd64
Investigating (0) libmono-security1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono )
Broken libmono-security1.0-cil:amd64 Depends on libmono-corlib1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono ) (>= 1.2.2.1)
  Considering libmono-corlib1.0-cil:amd64 81 as a solution to libmono-security1.0-cil:amd64 5
  Removing libmono-security1.0-cil:amd64 rather than change libmono-corlib1.0-cil:amd64
Investigating (0) nautilus-sendto [ amd64 ] < 2.32.0-0ubuntu1.1 -> 3.0.1-0ubuntu1 > ( gnome )
Broken nautilus-sendto:amd64 Depends on nautilus [ amd64 ] < 1:2.32.2.1-0ubuntu13 -> 1:3.2.1-0ubuntu4.2 > ( gnome ) (>= 1:2.91)
  Considering nautilus:amd64 15 as a solution to nautilus-sendto:amd64 5
  Holding Back nautilus-sendto:amd64 rather than change nautilus:amd64
Investigating (0) gnome-media [ amd64 ] < 2.32.0-0ubuntu8~audiohacks1 -> 2.91.2-2ubuntu2 > ( gnome )
Broken gnome-media:amd64 Depends on x11-utils [ amd64 ] < 7.6+1 -> 7.6+3 > ( x11 )
  Considering x11-utils:amd64 49 as a solution to gnome-media:amd64 4
  Removing gnome-media:amd64 rather than change x11-utils:amd64
Investigating (0) libxine1-x [ amd64 ] < 1.1.19-2ubuntu5 -> 1.1.19-2ubuntu6 > ( libs )
Broken libxine1-x:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to libxine1-x:amd64 4
Broken libxine1-x:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to libxine1-x:amd64 4
  Or group remove for libxine1-x:amd64
Broken libxine1-x:amd64 Depends on libglu1-mesa [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libglu1-mesa:amd64 121 as a solution to libxine1-x:amd64 4
Broken libxine1-x:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 121 as a solution to libxine1-x:amd64 4
  Or group remove for libxine1-x:amd64
Investigating (0) libboost1.46-dev [ amd64 ] < none -> 1.46.1-5ubuntu2 > ( libdevel )
Broken libboost1.46-dev:amd64 Conflicts on libboost1.42-dev [ amd64 ] < 1.42.0-4ubuntu2 > ( libdevel )
  Considering libboost1.42-dev:amd64 19 as a solution to libboost1.46-dev:amd64 4
  Holding Back libboost1.46-dev:amd64 rather than change libboost1.42-dev:amd64
Investigating (0) octave-optim [ amd64 ] < 1.0.12-1 > ( math )
Broken octave-optim:amd64 Depends on octave-miscellaneous [ amd64 ] < 1.0.9-1build2 > ( math ) (>= 1.0.0)
  Considering octave-miscellaneous:amd64 7 as a solution to octave-optim:amd64 4
  Removing octave-optim:amd64 rather than change octave-miscellaneous:amd64
Investigating (0) compiz-plugins-main-default [ amd64 ] < none -> 1:0.9.6-0ubuntu4.2 > ( x11 )
Broken compiz-plugins-main-default:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to compiz-plugins-main-default:amd64 4
  Holding Back compiz-plugins-main-default:amd64 rather than change libgl1-mesa-glx:amd64
Broken compiz-plugins-main-default:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to compiz-plugins-main-default:amd64 4
  Holding Back compiz-plugins-main-default:amd64 rather than change libgl1:amd64
  Or group keep for compiz-plugins-main-default:amd64
Broken compiz-plugins-main-default:amd64 Depends on libglu1-mesa [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libglu1-mesa:amd64 121 as a solution to compiz-plugins-main-default:amd64 4
  Holding Back compiz-plugins-main-default:amd64 rather than change libglu1-mesa:amd64
Broken compiz-plugins-main-default:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 121 as a solution to compiz-plugins-main-default:amd64 4
  Holding Back compiz-plugins-main-default:amd64 rather than change libglu1:amd64
  Or group keep for compiz-plugins-main-default:amd64
Investigating (0) octave-fpl [ amd64 ] < 1.0.0-1 > ( math )
Broken octave-fpl:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-fpl:amd64 3
  Removing octave-fpl:amd64 rather than change octave3.2:amd64
Investigating (0) octave-msh [ amd64 ] < 1.0.1-1 > ( math )
Broken octave-msh:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-msh:amd64 3
  Removing octave-msh:amd64 rather than change octave3.2:amd64
Investigating (0) libmono-sharpzip0.84-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono )
Broken libmono-sharpzip0.84-cil:amd64 Depends on libmono-corlib1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono ) (>= 1.2.2.1)
  Considering libmono-corlib1.0-cil:amd64 81 as a solution to libmono-sharpzip0.84-cil:amd64 3
  Removing libmono-sharpzip0.84-cil:amd64 rather than change libmono-corlib1.0-cil:amd64
Investigating (0) python-wxgtk2.8 [ amd64 ] < 2.8.11.0-0ubuntu8.1 > ( python )
Broken python-wxgtk2.8:amd64 Depends on libwxgtk2.8-0 [ amd64 ] < 2.8.11.0-0ubuntu8.1 > ( libs ) (>= 2.8.11.0)
  Considering libwxgtk2.8-0:amd64 9 as a solution to python-wxgtk2.8:amd64 3
  Removing python-wxgtk2.8:amd64 rather than change libwxgtk2.8-0:amd64
Investigating (0) libunity-2d-private0 [ amd64 ] < none -> 4.12.0-0ubuntu1.4 > ( libs )
Broken libunity-2d-private0:amd64 Depends on libnux-1.0-0 [ amd64 ] < none -> 1.16.0-0ubuntu1.1 > ( libs ) (>= 1.8.0-0)
  Considering libnux-1.0-0:amd64 9 as a solution to libunity-2d-private0:amd64 3
  Holding Back libunity-2d-private0:amd64 rather than change libnux-1.0-0:amd64
Investigating (0) mplayer [ amd64 ] < 2:1.0~rc4.dfsg1-1ubuntu3 > ( video )
Broken mplayer:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to mplayer:amd64 3
Broken mplayer:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to mplayer:amd64 3
  Or group remove for mplayer:amd64
Investigating (0) unity-lens-files [ amd64 ] < none -> 0.6.12-0ubuntu1 > ( gnome )
Broken unity-lens-files:amd64 Breaks on unity-place-files [ amd64 ] < 0.5.46-0ubuntu5.1 > ( gnome ) (< 0.6.0~)
  Considering unity-place-files:amd64 -1 as a solution to unity-lens-files:amd64 3
  Added unity-place-files:amd64 to the remove list
  Fixing unity-lens-files:amd64 via remove of unity-place-files:amd64
Investigating (0) libgtkglext1 [ amd64 ] < 1.2.0-1.1ubuntu1 > ( libs )
Broken libgtkglext1:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to libgtkglext1:amd64 3
Broken libgtkglext1:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to libgtkglext1:amd64 3
  Or group remove for libgtkglext1:amd64
Broken libgtkglext1:amd64 Depends on libglu1-mesa [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libglu1-mesa:amd64 121 as a solution to libgtkglext1:amd64 3
Broken libgtkglext1:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 121 as a solution to libgtkglext1:amd64 3
  Or group remove for libgtkglext1:amd64
Investigating (0) libvisual-0.4-plugins [ amd64 ] < 0.4.0.dfsg.1-2ubuntu5 -> 0.4.0.dfsg.1-2ubuntu6 > ( sound )
Broken libvisual-0.4-plugins:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to libvisual-0.4-plugins:amd64 3
Broken libvisual-0.4-plugins:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to libvisual-0.4-plugins:amd64 3
  Or group remove for libvisual-0.4-plugins:amd64
Broken libvisual-0.4-plugins:amd64 Depends on libglu1-mesa [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libglu1-mesa:amd64 121 as a solution to libvisual-0.4-plugins:amd64 3
Broken libvisual-0.4-plugins:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 121 as a solution to libvisual-0.4-plugins:amd64 3
  Or group remove for libvisual-0.4-plugins:amd64
Investigating (0) libmtp-common [ amd64 ] < none -> 1.1.0-3ubuntu1 > ( libs )
Broken libmtp-common:amd64 Breaks on libmtp8 [ amd64 ] < 1.0.6-2 > ( libs ) (<= 1.0.6-6)
  Considering libmtp8:amd64 2 as a solution to libmtp-common:amd64 3
  Added libmtp8:amd64 to the remove list
  Fixing libmtp-common:amd64 via remove of libmtp8:amd64
Investigating (0) gtk2-engines-pixbuf [ amd64 ] < 2.24.4-0ubuntu2 > ( graphics )
Broken gtk2-engines-pixbuf:amd64 Depends on libgtk2.0-0 [ amd64 ] < 2.24.4-0ubuntu2 -> 2.24.6-0ubuntu5 > ( libs ) (= 2.24.4-0ubuntu2)
  Considering libgtk2.0-0:amd64 628 as a solution to gtk2-engines-pixbuf:amd64 3
  Removing gtk2-engines-pixbuf:amd64 rather than change libgtk2.0-0:amd64
Investigating (0) libcamel1.2-14 [ amd64 ] < 2.30.3-2ubuntu2.1 > ( libs )
Broken libcamel1.2-14:amd64 Depends on libnspr4-0d [ amd64 ] < 4.8.7-0ubuntu1 > ( libs ) (>= 4.7.3-0ubuntu1~)
  Considering libnspr4-0d:amd64 8 as a solution to libcamel1.2-14:amd64 3
  Removing libcamel1.2-14:amd64 rather than change libnspr4-0d:amd64
Investigating (0) nux-tools [ amd64 ] < 0.9.48-0ubuntu1.1 -> 1.16.0-0ubuntu1.1 > ( x11 )
Broken nux-tools:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to nux-tools:amd64 3
Broken nux-tools:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to nux-tools:amd64 3
  Or group remove for nux-tools:amd64
Investigating (0) compiz [ amd64 ] < 1:0.9.4+bzr20110606-0ubuntu1~natty2 -> 1:0.9.6+bzr20110929-0ubuntu6.1 > ( x11 )
Broken compiz:amd64 Depends on compiz-plugins-default [ amd64 ] < none -> 1:0.9.6+bzr20110929-0ubuntu6.1 > ( x11 ) (>= 1:0.9.6+bzr20110929-0ubuntu6.1)
  Considering compiz-plugins-default:amd64 12 as a solution to compiz:amd64 3
  Holding Back compiz:amd64 rather than change compiz-plugins-default:amd64
Investigating (0) unity-lens-applications [ amd64 ] < none -> 0.4.12-0ubuntu2.1 > ( gnome )
Broken unity-lens-applications:amd64 Breaks on unity-place-applications [ amd64 ] < 0.2.46-0ubuntu3.1 > ( gnome ) (< 0.4.0~)
  Considering unity-place-applications:amd64 -1 as a solution to unity-lens-applications:amd64 3
  Added unity-place-applications:amd64 to the remove list
  Fixing unity-lens-applications:amd64 via remove of unity-place-applications:amd64
Investigating (0) libmono-posix1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono )
Broken libmono-posix1.0-cil:amd64 Depends on libmono-corlib1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono ) (>= 1.2.2.1)
  Considering libmono-corlib1.0-cil:amd64 81 as a solution to libmono-posix1.0-cil:amd64 3
  Removing libmono-posix1.0-cil:amd64 rather than change libmono-corlib1.0-cil:amd64
Investigating (0) libebook1.2-9 [ amd64 ] < 2.30.3-2ubuntu2.1 > ( libs )
Broken libebook1.2-9:amd64 Depends on libcamel1.2-14 [ amd64 ] < 2.30.3-2ubuntu2.1 > ( libs ) (>= 2.30.3)
  Considering libcamel1.2-14:amd64 3 as a solution to libebook1.2-9:amd64 3
  Removing libebook1.2-9:amd64 rather than change libcamel1.2-14:amd64
Investigating (0) libgl1-mesa-dev [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libdevel )
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs ) (= 7.11-0ubuntu3.2)
  Considering libgl1-mesa-glx:amd64 238 as a solution to libgl1-mesa-dev:amd64 2
  Removing libgl1-mesa-dev:amd64 rather than change libgl1-mesa-glx:amd64
Investigating (0) libkonq-common [ amd64 ] < none -> 4:4.7.4-0ubuntu0.1 > ( libs )
Broken libkonq-common:amd64 Breaks on libkonq5a [ amd64 ] < 4:4.6.5-0ubuntu1 > ( libs )
  Considering libkonq5a:amd64 -1 as a solution to libkonq-common:amd64 2
  Added libkonq5a:amd64 to the remove list
  Fixing libkonq-common:amd64 via remove of libkonq5a:amd64
Investigating (0) libgl1-mesa-glx [ i386 ] < none -> 7.11-0ubuntu3.2 > ( libs )
Broken libgl1-mesa-glx:i386 Depends on libglapi-mesa [ i386 ] < none -> 7.11-0ubuntu3.2 > ( libs ) (= 7.11-0ubuntu3.2)
  Considering libglapi-mesa:i386 0 as a solution to libgl1-mesa-glx:i386 2
  Holding Back libgl1-mesa-glx:i386 rather than change libglapi-mesa:i386
Investigating (0) dx [ amd64 ] < 1:4.4.4-3build3 > ( science )
Broken dx:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to dx:amd64 2
Broken dx:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to dx:amd64 2
  Or group remove for dx:amd64
Broken dx:amd64 Depends on libglu1-mesa [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libglu1-mesa:amd64 121 as a solution to dx:amd64 2
Broken dx:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 121 as a solution to dx:amd64 2
  Or group remove for dx:amd64
Investigating (0) octave-control [ amd64 ] < 1.0.11-2 > ( math )
Broken octave-control:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-control:amd64 2
  Removing octave-control:amd64 rather than change octave3.2:amd64
Investigating (0) libgcj11 [ amd64 ] < 4.5.2-8ubuntu1 > ( libs )
Broken libgcj11:amd64 Depends on gcj-4.5-base [ amd64 ] < 4.5.2-8ubuntu1 > ( libs ) (>= 4.5.2-8ubuntu1)
  Considering gcj-4.5-base:amd64 2 as a solution to libgcj11:amd64 2
  Removing libgcj11:amd64 rather than change gcj-4.5-base:amd64
Investigating (0) gnuplot-x11 [ amd64 ] < 4.4.2-0ubuntu1 > ( math )
Broken gnuplot-x11:amd64 Depends on libwxgtk2.8-0 [ amd64 ] < 2.8.11.0-0ubuntu8.1 > ( libs ) (>= 2.8.11.0)
  Considering libwxgtk2.8-0:amd64 9 as a solution to gnuplot-x11:amd64 2
  Removing gnuplot-x11:amd64 rather than change libwxgtk2.8-0:amd64
Investigating (0) compiz-gnome [ amd64 ] < 1:0.9.4+bzr20110606-0ubuntu1~natty2 -> 1:0.9.6+bzr20110929-0ubuntu6.1 > ( x11 )
Broken compiz-gnome:amd64 Depends on compiz-plugins-default [ amd64 ] < none -> 1:0.9.6+bzr20110929-0ubuntu6.1 > ( x11 ) (= 1:0.9.6+bzr20110929-0ubuntu6.1)
  Considering compiz-plugins-default:amd64 12 as a solution to compiz-gnome:amd64 2
  Removing compiz-gnome:amd64 rather than change compiz-plugins-default:amd64
Investigating (0) libgtk2.0-0 [ i386 ] < none -> 2.24.6-0ubuntu5 > ( libs )
Broken libgtk2.0-0:i386 Depends on libglib2.0-0 [ i386 ] < none -> 2.30.0-0ubuntu4 > ( libs ) (>= 2.29.6)
  Considering libglib2.0-0:i386 9 as a solution to libgtk2.0-0:i386 2
  Holding Back libgtk2.0-0:i386 rather than change libglib2.0-0:i386
Investigating (0) libmono-cil-dev [ amd64 ] < 2.6.7-5ubuntu3.1 -> 2.10.5-1ubuntu0.1 > ( cli-mono )
Broken libmono-cil-dev:amd64 Breaks on libmono-dev [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono ) (< 2.10~)
  Considering libmono-dev:amd64 1 as a solution to libmono-cil-dev:amd64 2
  Added libmono-dev:amd64 to the remove list
  Fixing libmono-cil-dev:amd64 via remove of libmono-dev:amd64
Investigating (0) python-wxversion [ amd64 ] < 2.8.11.0-0ubuntu8.1 > ( python )
Broken python-wxversion:amd64 Depends on python-wxgtk2.8 [ amd64 ] < 2.8.11.0-0ubuntu8.1 > ( python ) (>= 2.8.6.1-0ubuntu2)
  Considering python-wxgtk2.8:amd64 3 as a solution to python-wxversion:amd64 2
Broken python-wxversion:amd64 Depends on python-wxgtk2.6 [ amd64 ] < none > ( none ) (>= 2.6.3.2.2-1ubuntu2)
  Or group remove for python-wxversion:amd64
Investigating (0) libxine1 [ amd64 ] < 1.1.19-2ubuntu5 -> 1.1.19-2ubuntu6 > ( libs )
Broken libxine1:amd64 Depends on libxine1-x [ amd64 ] < 1.1.19-2ubuntu5 -> 1.1.19-2ubuntu6 > ( libs ) (= 1.1.19-2ubuntu6)
  Considering libxine1-x:amd64 4 as a solution to libxine1:amd64 2
  Removing libxine1:amd64 rather than change libxine1-x:amd64
Investigating (0) octave-struct [ amd64 ] < 1.0.7-2 > ( math )
Broken octave-struct:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-struct:amd64 1
  Removing octave-struct:amd64 rather than change octave3.2:amd64
Investigating (0) python-traitsbackendwx [ amd64 ] < 3.4.0-1 > ( python )
Broken python-traitsbackendwx:amd64 Depends on python-wxgtk2.8 [ amd64 ] < 2.8.11.0-0ubuntu8.1 > ( python )
  Considering python-wxgtk2.8:amd64 3 as a solution to python-traitsbackendwx:amd64 1
  Removing python-traitsbackendwx:amd64 rather than change python-wxgtk2.8:amd64
Investigating (0) libgnome2-vfs-perl [ amd64 ] < 1.081-1build1 > ( perl )
Broken libgnome2-vfs-perl:amd64 Depends on perlapi-5.10.1 [ amd64 ] < none > ( none )
  Considering perl-base:amd64 5396 as a solution to libgnome2-vfs-perl:amd64 1
  Removing libgnome2-vfs-perl:amd64 rather than change perlapi-5.10.1:amd64
Investigating (0) python-pyatspi2 [ amd64 ] < none -> 2.2.1-0ubuntu1 > ( python )
Broken python-pyatspi2:amd64 Conflicts on python-pyatspi [ amd64 ] < 1.32.0-0ubuntu2 > ( python )
  Considering python-pyatspi:amd64 -1 as a solution to python-pyatspi2:amd64 1
  Added python-pyatspi:amd64 to the remove list
  Fixing python-pyatspi2:amd64 via remove of python-pyatspi:amd64
Investigating (0) octave-nan [ amd64 ] < 2.3.1-2 > ( math )
Broken octave-nan:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-nan:amd64 1
  Removing octave-nan:amd64 rather than change octave3.2:amd64
Investigating (0) libnet-dbus-perl [ amd64 ] < 0.33.6-2 > ( perl )
Broken libnet-dbus-perl:amd64 Depends on perlapi-5.10.1 [ amd64 ] < none > ( none )
  Considering perl-base:amd64 5396 as a solution to libnet-dbus-perl:amd64 1
  Removing libnet-dbus-perl:amd64 rather than change perlapi-5.10.1:amd64
Investigating (0) libmono-ldap1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono )
Broken libmono-ldap1.0-cil:amd64 Depends on libmono-corlib1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono ) (>= 1.2.2.1)
  Considering libmono-corlib1.0-cil:amd64 81 as a solution to libmono-ldap1.0-cil:amd64 1
  Removing libmono-ldap1.0-cil:amd64 rather than change libmono-corlib1.0-cil:amd64
Investigating (0) nautilus-share [ amd64 ] < 0.7.2-14ubuntu1 -> 0.7.3-1ubuntu1 > ( gnome )
Broken nautilus-share:amd64 Depends on nautilus [ amd64 ] < 1:2.32.2.1-0ubuntu13 -> 1:3.2.1-0ubuntu4.2 > ( gnome ) (>= 2.10)
  Considering nautilus:amd64 15 as a solution to nautilus-share:amd64 1
  Removing nautilus-share:amd64 rather than change nautilus:amd64
Investigating (0) octave3.2-headers [ amd64 ] < 3.2.4-8 > ( math )
Broken octave3.2-headers:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (= 3.2.4-8)
  Considering octave3.2:amd64 126 as a solution to octave3.2-headers:amd64 1
  Removing octave3.2-headers:amd64 rather than change octave3.2:amd64
Investigating (0) libevince3-3 [ amd64 ] < none -> 3.2.1-0ubuntu2.3 > ( libs )
Broken libevince3-3:amd64 Breaks on libevdocument3 [ amd64 ] < 2.32.0-0ubuntu12.4 > ( libs )
  Considering libevdocument3:amd64 1 as a solution to libevince3-3:amd64 1
  Holding Back libevince3-3:amd64 rather than change libevdocument3:amd64
Investigating (0) libmono-debugger-soft2.0-cil [ amd64 ] < none -> 2.10.5-1ubuntu0.1 > ( cli-mono )
Broken libmono-debugger-soft2.0-cil:amd64 Conflicts on libmono-debugger-soft0.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono )
  Considering libmono-debugger-soft0.0-cil:amd64 -1 as a solution to libmono-debugger-soft2.0-cil:amd64 1
  Added libmono-debugger-soft0.0-cil:amd64 to the remove list
  Fixing libmono-debugger-soft2.0-cil:amd64 via remove of libmono-debugger-soft0.0-cil:amd64
Investigating (0) python-gtksourceview2 [ amd64 ] < 2.10.1-1build1 > ( python )
Broken python-gtksourceview2:amd64 Depends on python2.6-gtk2 [ amd64 ] < none > ( none )
  Considering python-gtk2:amd64 90 as a solution to python-gtksourceview2:amd64 1
  Removing python-gtksourceview2:amd64 rather than change python2.6-gtk2:amd64
Investigating (0) libmono-accessibility1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono )
Broken libmono-accessibility1.0-cil:amd64 Depends on libmono-corlib1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono ) (>= 1.2.2.1)
  Considering libmono-corlib1.0-cil:amd64 81 as a solution to libmono-accessibility1.0-cil:amd64 1
  Removing libmono-accessibility1.0-cil:amd64 rather than change libmono-corlib1.0-cil:amd64
Investigating (0) unity-2d-spread [ amd64 ] < none -> 4.12.0-0ubuntu1.4 > ( x11 )
Broken unity-2d-spread:amd64 Depends on libunity-2d-private0 [ amd64 ] < none -> 4.12.0-0ubuntu1.4 > ( libs ) (= 4.12.0-0ubuntu1.4)
  Considering libunity-2d-private0:amd64 3 as a solution to unity-2d-spread:amd64 1
  Holding Back unity-2d-spread:amd64 rather than change libunity-2d-private0:amd64
Investigating (0) compiz-plugins-main [ amd64 ] < 0.9.4+bzr20110527-0ubuntu1~natty1 -> 1:0.9.6-0ubuntu4.2 > ( x11 )
Broken compiz-plugins-main:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to compiz-plugins-main:amd64 1
Broken compiz-plugins-main:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to compiz-plugins-main:amd64 1
  Or group remove for compiz-plugins-main:amd64
Broken compiz-plugins-main:amd64 Depends on compiz-plugins-main-default [ amd64 ] < none -> 1:0.9.6-0ubuntu4.2 > ( x11 ) (= 1:0.9.6-0ubuntu4.2)
  Considering compiz-plugins-main-default:amd64 4 as a solution to compiz-plugins-main:amd64 1
  Removing compiz-plugins-main:amd64 rather than change compiz-plugins-main-default:amd64
Investigating (0) unity-2d-panel [ amd64 ] < none -> 4.12.0-0ubuntu1.4 > ( x11 )
Broken unity-2d-panel:amd64 Depends on libunity-2d-private0 [ amd64 ] < none -> 4.12.0-0ubuntu1.4 > ( libs ) (= 4.12.0-0ubuntu1.4)
  Considering libunity-2d-private0:amd64 3 as a solution to unity-2d-panel:amd64 1
  Holding Back unity-2d-panel:amd64 rather than change libunity-2d-private0:amd64
Investigating (0) octave-odepkg [ amd64 ] < 0.6.10-1 > ( math )
Broken octave-odepkg:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-odepkg:amd64 1
  Removing octave-odepkg:amd64 rather than change octave3.2:amd64
Investigating (0) libpulse-browse0 [ amd64 ] < 1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1 > ( sound )
Broken libpulse-browse0:amd64 Depends on libpulse0 [ amd64 ] < 1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1 -> 1:1.0-0ubuntu3.1 > ( libs ) (= 1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1)
  Considering libpulse0:amd64 133 as a solution to libpulse-browse0:amd64 1
  Removing libpulse-browse0:amd64 rather than change libpulse0:amd64
Investigating (0) eog [ amd64 ] < 2.32.1-0ubuntu2 -> 3.2.1-0ubuntu1.1 > ( gnome )
Broken eog:amd64 Depends on libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.1-0ubuntu1.1 > ( libs ) (>= 2.91.5)
  Considering libgnome-desktop-3-2:amd64 36 as a solution to eog:amd64 1
  Holding Back eog:amd64 rather than change libgnome-desktop-3-2:amd64
Investigating (0) libglu1-mesa-dev [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libdevel )
Broken libglu1-mesa-dev:amd64 Depends on libglu1-mesa [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs ) (= 7.11-0ubuntu3.2)
  Considering libglu1-mesa:amd64 121 as a solution to libglu1-mesa-dev:amd64 1
  Removing libglu1-mesa-dev:amd64 rather than change libglu1-mesa:amd64
Investigating (0) libglc0 [ amd64 ] < 0.7.2-4build1 > ( libs )
Broken libglc0:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to libglc0:amd64 1
Broken libglc0:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to libglc0:amd64 1
  Or group remove for libglc0:amd64
Broken libglc0:amd64 Depends on libglewmx1.5 [ amd64 ] < 1.5.7.is.1.5.2-1ubuntu2 -> 1.5.7.is.1.5.2-1ubuntu4 > ( libs ) (>= 1.5.7.is.1.5.2)
  Considering libglewmx1.5:amd64 6 as a solution to libglc0:amd64 1
  Removing libglc0:amd64 rather than change libglewmx1.5:amd64
Investigating (0) whitedune [ amd64 ] < 0.28.14-1.1 > ( graphics )
Broken whitedune:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to whitedune:amd64 1
Broken whitedune:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to whitedune:amd64 1
  Or group remove for whitedune:amd64
Broken whitedune:amd64 Depends on libglu1-mesa [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libglu1-mesa:amd64 121 as a solution to whitedune:amd64 1
Broken whitedune:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 121 as a solution to whitedune:amd64 1
  Or group remove for whitedune:amd64
Investigating (0) gconf-defaults-service [ amd64 ] < 2.32.2-0ubuntu2 > ( libs )
Broken gconf-defaults-service:amd64 Depends on gconf2-common [ amd64 ] < 2.32.2-0ubuntu2 -> 3.2.3-0ubuntu0.1 > ( libs ) (< 2.33)
  Considering gconf2-common:amd64 322 as a solution to gconf-defaults-service:amd64 1
  Removing gconf-defaults-service:amd64 rather than change gconf2-common:amd64
Investigating (0) libgnome2-canvas-perl [ amd64 ] < 1.002-2build1 > ( perl )
Broken libgnome2-canvas-perl:amd64 Depends on perlapi-5.10.1 [ amd64 ] < none > ( none )
  Considering perl-base:amd64 5396 as a solution to libgnome2-canvas-perl:amd64 1
  Removing libgnome2-canvas-perl:amd64 rather than change perlapi-5.10.1:amd64
Investigating (0) evince [ amd64 ] < 2.32.0-0ubuntu12.4 -> 3.2.1-0ubuntu2.3 > ( gnome )
Broken evince:amd64 Depends on libevince3-3 [ amd64 ] < none -> 3.2.1-0ubuntu2.3 > ( libs ) (= 3.2.1-0ubuntu2.3)
  Considering libevince3-3:amd64 1 as a solution to evince:amd64 1
  Removing evince:amd64 rather than change libevince3-3:amd64
Investigating (0) octave-communications [ amd64 ] < 1.0.10-2 > ( math )
Broken octave-communications:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-communications:amd64 1
  Removing octave-communications:amd64 rather than change octave3.2:amd64
Investigating (0) gcj-4.5-jre-lib [ amd64 ] < 4.5.2-8ubuntu1 > ( java )
Broken gcj-4.5-jre-lib:amd64 Depends on gcj-4.5-base [ amd64 ] < 4.5.2-8ubuntu1 > ( libs ) (>= 4.5.1-1~)
  Considering gcj-4.5-base:amd64 2 as a solution to gcj-4.5-jre-lib:amd64 1
  Removing gcj-4.5-jre-lib:amd64 rather than change gcj-4.5-base:amd64
Investigating (0) libdx4 [ amd64 ] < 1:4.4.4-3build3 > ( libs )
Broken libdx4:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to libdx4:amd64 1
Broken libdx4:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to libdx4:amd64 1
  Or group remove for libdx4:amd64
Broken libdx4:amd64 Depends on libglu1-mesa [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libglu1-mesa:amd64 121 as a solution to libdx4:amd64 1
Broken libdx4:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 121 as a solution to libdx4:amd64 1
  Or group remove for libdx4:amd64
Investigating (0) gnome-dictionary [ amd64 ] < 2.32.0-0ubuntu5 > ( gnome )
Broken gnome-dictionary:amd64 Depends on gnome-utils-common [ amd64 ] < 2.32.0-0ubuntu5 -> 3.2.1-0ubuntu1 > ( libs ) (< 2.33)
  Considering gnome-utils-common:amd64 32 as a solution to gnome-dictionary:amd64 1
  Removing gnome-dictionary:amd64 rather than change gnome-utils-common:amd64
Investigating (0) unity-2d-places [ amd64 ] < none -> 4.12.0-0ubuntu1.4 > ( x11 )
Broken unity-2d-places:amd64 Depends on libunity-2d-private0 [ amd64 ] < none -> 4.12.0-0ubuntu1.4 > ( libs ) (= 4.12.0-0ubuntu1.4)
  Considering libunity-2d-private0:amd64 3 as a solution to unity-2d-places:amd64 1
  Holding Back unity-2d-places:amd64 rather than change libunity-2d-private0:amd64
Investigating (0) gnome-screensaver [ amd64 ] < 2.30.2-0ubuntu2 -> 3.2.0-0ubuntu1 > ( gnome )
Broken gnome-screensaver:amd64 Depends on libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.1-0ubuntu1.1 > ( libs ) (>= 3.1.91)
  Considering libgnome-desktop-3-2:amd64 36 as a solution to gnome-screensaver:amd64 1
  Removing gnome-screensaver:amd64 rather than change libgnome-desktop-3-2:amd64
Investigating (0) gmsh [ amd64 ] < 2.5.0.dfsg-2 > ( math )
Broken gmsh:amd64 Depends on libfltk1.1 [ amd64 ] < 1.1.10-3 -> 1.1.10-7 > ( libs ) (>= 1.1.8~rc1)
  Considering libfltk1.1:amd64 74 as a solution to gmsh:amd64 1
  Removing gmsh:amd64 rather than change libfltk1.1:amd64
Investigating (0) octave-splines [ amd64 ] < 1.0.7-2 > ( math )
Broken octave-splines:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-splines:amd64 1
  Removing octave-splines:amd64 rather than change octave3.2:amd64
Investigating (0) xorg [ amd64 ] < 1:7.6+4ubuntu3.2 -> 1:7.6+7ubuntu7.1 > ( x11 )
Broken xorg:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to xorg:amd64 1
Broken xorg:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to xorg:amd64 1
  Or group remove for xorg:amd64
Broken xorg:amd64 Depends on libglu1-mesa [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libglu1-mesa:amd64 121 as a solution to xorg:amd64 1
  Removing xorg:amd64 rather than change libglu1-mesa:amd64
Investigating (0) lib32v4l-0 [ amd64 ] < 0.8.3-1 > ( libs )
Broken lib32v4l-0:amd64 Depends on libv4l-0 [ amd64 ] < 0.8.3-1 -> 0.8.5-3ubuntu2 > ( libs ) (= 0.8.3-1)
  Considering libv4l-0:amd64 34 as a solution to lib32v4l-0:amd64 1
  Removing lib32v4l-0:amd64 rather than change libv4l-0:amd64
Investigating (0) octave-statistics [ amd64 ] < 1.0.10-1 > ( math )
Broken octave-statistics:amd64 Depends on octave-miscellaneous [ amd64 ] < 1.0.9-1build2 > ( math )
  Considering octave-miscellaneous:amd64 7 as a solution to octave-statistics:amd64 1
  Removing octave-statistics:amd64 rather than change octave-miscellaneous:amd64
Investigating (0) octave-time [ amd64 ] < 1.0.9-2 > ( math )
Broken octave-time:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-time:amd64 1
  Removing octave-time:amd64 rather than change octave3.2:amd64
Investigating (0) unity-2d-launcher [ amd64 ] < none -> 4.12.0-0ubuntu1.4 > ( x11 )
Broken unity-2d-launcher:amd64 Depends on libunity-2d-private0 [ amd64 ] < none -> 4.12.0-0ubuntu1.4 > ( libs ) (= 4.12.0-0ubuntu1.4)
  Considering libunity-2d-private0:amd64 3 as a solution to unity-2d-launcher:amd64 1
  Holding Back unity-2d-launcher:amd64 rather than change libunity-2d-private0:amd64
Investigating (0) libdevil1c2 [ amd64 ] < 1.7.8-6build1 > ( libs )
Broken libdevil1c2:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to libdevil1c2:amd64 1
Broken libdevil1c2:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to libdevil1c2:amd64 1
  Or group remove for libdevil1c2:amd64
Broken libdevil1c2:amd64 Depends on libglu1-mesa [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libglu1-mesa:amd64 121 as a solution to libdevil1c2:amd64 1
Broken libdevil1c2:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 121 as a solution to libdevil1c2:amd64 1
  Or group remove for libdevil1c2:amd64
Investigating (0) xscreensaver-gl [ amd64 ] < 5.12-0ubuntu3 -> 5.14-1ubuntu1 > ( x11 )
Broken xscreensaver-gl:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to xscreensaver-gl:amd64 0
Broken xscreensaver-gl:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to xscreensaver-gl:amd64 0
  Or group remove for xscreensaver-gl:amd64
Broken xscreensaver-gl:amd64 Depends on libglu1-mesa [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libglu1-mesa:amd64 121 as a solution to xscreensaver-gl:amd64 0
Broken xscreensaver-gl:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 121 as a solution to xscreensaver-gl:amd64 0
  Or group remove for xscreensaver-gl:amd64
Investigating (0) libatk1.0-0 [ i386 ] < none -> 2.2.0-0ubuntu1 > ( libs )
Broken libatk1.0-0:i386 Depends on libglib2.0-0 [ i386 ] < none -> 2.30.0-0ubuntu4 > ( libs ) (>= 2.16.0)
  Considering libglib2.0-0:i386 9 as a solution to libatk1.0-0:i386 0
  Holding Back libatk1.0-0:i386 rather than change libglib2.0-0:i386
Investigating (0) ubuntu-desktop [ amd64 ] < 1.220 -> 1.245.1 > ( metapackages )
Broken ubuntu-desktop:amd64 Depends on evince [ amd64 ] < 2.32.0-0ubuntu12.4 -> 3.2.1-0ubuntu2.3 > ( gnome )
  Considering evince:amd64 1 as a solution to ubuntu-desktop:amd64 0
  Removing ubuntu-desktop:amd64 rather than change evince:amd64
Investigating (0) octave-gsl [ amd64 ] < 1.0.8-2build1 > ( math )
Broken octave-gsl:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-gsl:amd64 0
  Removing octave-gsl:amd64 rather than change octave3.2:amd64
Investigating (0) libboost-regex1.46-dev [ amd64 ] < none -> 1.46.1-5ubuntu2 > ( libdevel )
Broken libboost-regex1.46-dev:amd64 Depends on libboost1.46-dev [ amd64 ] < none -> 1.46.1-5ubuntu2 > ( libdevel ) (= 1.46.1-5ubuntu2)
  Considering libboost1.46-dev:amd64 4 as a solution to libboost-regex1.46-dev:amd64 0
  Holding Back libboost-regex1.46-dev:amd64 rather than change libboost1.46-dev:amd64
Investigating (0) audacity [ amd64 ] < 1.3.13-3ubuntu1 > ( sound )
Broken audacity:amd64 Depends on libwxgtk2.8-0 [ amd64 ] < 2.8.11.0-0ubuntu8.1 > ( libs ) (>= 2.8.11.0)
  Considering libwxgtk2.8-0:amd64 9 as a solution to audacity:amd64 0
  Removing audacity:amd64 rather than change libwxgtk2.8-0:amd64
Investigating (0) octave-specfun [ amd64 ] < 1.0.9-1 > ( math )
Broken octave-specfun:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-specfun:amd64 0
  Removing octave-specfun:amd64 rather than change octave3.2:amd64
Investigating (0) evolution-exchange [ amd64 ] < 2.32.2-0ubuntu3 -> 3.2.1-0ubuntu1 > ( gnome )
Broken evolution-exchange:amd64 Depends on libevolution [ amd64 ] < 2.32.2-0ubuntu7 -> 3.2.2-0ubuntu0.1 > ( gnome ) (>= 3.2)
  Considering libevolution:amd64 16 as a solution to evolution-exchange:amd64 0
  Removing evolution-exchange:amd64 rather than change libevolution:amd64
Investigating (0) libkdegames5a [ amd64 ] < none -> 4:4.7.4-0ubuntu0.1 > ( libs )
Broken libkdegames5a:amd64 Breaks on libkdegames5 [ amd64 ] < 4:4.6.5-0ubuntu1 > ( libs )
  Considering libkdegames5:amd64 -1 as a solution to libkdegames5a:amd64 0
  Added libkdegames5:amd64 to the remove list
  Fixing libkdegames5a:amd64 via remove of libkdegames5:amd64
Investigating (0) libsdl1.2-dev [ amd64 ] < 1.2.14-6.1ubuntu3 -> 1.2.14-6.1ubuntu4 > ( libdevel )
Broken libsdl1.2-dev:amd64 Depends on libglu1-mesa-dev [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libdevel )
  Considering libglu1-mesa-dev:amd64 1 as a solution to libsdl1.2-dev:amd64 0
  Removing libsdl1.2-dev:amd64 rather than change libglu1-mesa-dev:amd64
Investigating (0) libgdk-pixbuf2.0-0 [ i386 ] < none -> 2.24.0-1ubuntu1 > ( libs )
Broken libgdk-pixbuf2.0-0:i386 Depends on libglib2.0-0 [ i386 ] < none -> 2.30.0-0ubuntu4 > ( libs ) (>= 2.28.0)
  Considering libglib2.0-0:i386 9 as a solution to libgdk-pixbuf2.0-0:i386 0
  Holding Back libgdk-pixbuf2.0-0:i386 rather than change libglib2.0-0:i386
Investigating (0) virtualbox-ose-qt [ amd64 ] < 4.0.4-dfsg-1ubuntu4.1 > ( misc )
Broken virtualbox-ose-qt:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to virtualbox-ose-qt:amd64 0
Broken virtualbox-ose-qt:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to virtualbox-ose-qt:amd64 0
  Or group remove for virtualbox-ose-qt:amd64
Broken virtualbox-ose-qt:amd64 Depends on libqt4-opengl [ amd64 ] < 4:4.7.2-0ubuntu6.4 -> 4:4.7.4-0ubuntu8.3 > ( libs ) (>= 4:4.7.0~rc1)
  Considering libqt4-opengl:amd64 12 as a solution to virtualbox-ose-qt:amd64 0
  Removing virtualbox-ose-qt:amd64 rather than change libqt4-opengl:amd64
Investigating (0) asymptote [ amd64 ] < 2.02-2 > ( tex )
Broken asymptote:amd64 Depends on freeglut3 [ amd64 ] < 2.6.0-1ubuntu2 > ( libs )
  Considering freeglut3:amd64 11 as a solution to asymptote:amd64 0
  Removing asymptote:amd64 rather than change freeglut3:amd64
Investigating (0) libboost-iostreams1.46-dev [ amd64 ] < none -> 1.46.1-5ubuntu2 > ( libdevel )
Broken libboost-iostreams1.46-dev:amd64 Depends on libboost1.46-dev [ amd64 ] < none -> 1.46.1-5ubuntu2 > ( libdevel ) (= 1.46.1-5ubuntu2)
  Considering libboost1.46-dev:amd64 4 as a solution to libboost-iostreams1.46-dev:amd64 0
  Holding Back libboost-iostreams1.46-dev:amd64 rather than change libboost1.46-dev:amd64
Investigating (0) flashplugin-installer [ amd64 ] < 11.2.202.243ubuntu0.11.04.1 > ( contrib/web )
Broken flashplugin-installer:amd64 Depends on libnspr4-0d [ amd64 ] < 4.8.7-0ubuntu1 > ( libs ) (>= 4.7.1~beta2)
  Considering libnspr4-0d:amd64 8 as a solution to flashplugin-installer:amd64 0
  Removing flashplugin-installer:amd64 rather than change libnspr4-0d:amd64
Investigating (0) network-manager-openvpn-gnome [ amd64 ] < 0.8.1+git.20100810t173015.1711d04-0ubuntu2 > ( universe/net )
Broken network-manager-openvpn-gnome:amd64 Depends on network-manager-openvpn [ amd64 ] < 0.8.1+git.20100810t173015.1711d04-0ubuntu2 > ( universe/net )
  Considering network-manager-openvpn:amd64 0 as a solution to network-manager-openvpn-gnome:amd64 0
  Removing network-manager-openvpn-gnome:amd64 rather than change network-manager-openvpn:amd64
Investigating (0) compiz-plugins [ amd64 ] < 1:0.9.4+bzr20110606-0ubuntu1~natty2 -> 1:0.9.6+bzr20110929-0ubuntu6.1 > ( x11 )
Broken compiz-plugins:amd64 Depends on compiz-plugins-default [ amd64 ] < none -> 1:0.9.6+bzr20110929-0ubuntu6.1 > ( x11 ) (= 1:0.9.6+bzr20110929-0ubuntu6.1)
  Considering compiz-plugins-default:amd64 12 as a solution to compiz-plugins:amd64 0
  Removing compiz-plugins:amd64 rather than change compiz-plugins-default:amd64
Investigating (0) libplib1 [ amd64 ] < 1.8.5-5+squeeze1build0.11.04.1 > ( libs )
Broken libplib1:amd64 Depends on freeglut3 [ amd64 ] < 2.6.0-1ubuntu2 > ( libs )
  Considering freeglut3:amd64 11 as a solution to libplib1:amd64 0
  Removing libplib1:amd64 rather than change freeglut3:amd64
Investigating (0) libfltk1.1-dev [ amd64 ] < 1.1.10-3 -> 1.1.10-7 > ( libdevel )
Broken libfltk1.1-dev:amd64 Depends on libfltk1.1 [ amd64 ] < 1.1.10-3 -> 1.1.10-7 > ( libs ) (= 1.1.10-7)
  Considering libfltk1.1:amd64 74 as a solution to libfltk1.1-dev:amd64 0
  Removing libfltk1.1-dev:amd64 rather than change libfltk1.1:amd64
Investigating (0) libboost-serialization1.46-dev [ amd64 ] < none -> 1.46.1-5ubuntu2 > ( libdevel )
Broken libboost-serialization1.46-dev:amd64 Depends on libboost1.46-dev [ amd64 ] < none -> 1.46.1-5ubuntu2 > ( libdevel ) (= 1.46.1-5ubuntu2)
  Considering libboost1.46-dev:amd64 4 as a solution to libboost-serialization1.46-dev:amd64 0
  Holding Back libboost-serialization1.46-dev:amd64 rather than change libboost1.46-dev:amd64
Investigating (0) libpango1.0-0 [ i386 ] < none -> 1.29.3+git20110916-0ubuntu1 > ( libs )
Broken libpango1.0-0:i386 Depends on libglib2.0-0 [ i386 ] < none -> 2.30.0-0ubuntu4 > ( libs ) (>= 2.27.0)
  Considering libglib2.0-0:i386 9 as a solution to libpango1.0-0:i386 0
  Holding Back libpango1.0-0:i386 rather than change libglib2.0-0:i386
Investigating (0) libboost-dev [ amd64 ] < 1.42.0.1ubuntu1 -> 1.46.1.1 > ( libdevel )
Broken libboost-dev:amd64 Depends on libboost1.46-dev [ amd64 ] < none -> 1.46.1-5ubuntu2 > ( libdevel )
  Considering libboost1.46-dev:amd64 4 as a solution to libboost-dev:amd64 0
  Holding Back libboost-dev:amd64 rather than change libboost1.46-dev:amd64
Investigating (0) libdevice-serialport-perl [ amd64 ] < 1.04-2 > ( perl )
Broken libdevice-serialport-perl:amd64 Depends on perlapi-5.10.0 [ amd64 ] < none > ( none )
  Considering perl-base:amd64 5396 as a solution to libdevice-serialport-perl:amd64 0
  Removing libdevice-serialport-perl:amd64 rather than change perlapi-5.10.0:amd64
Investigating (0) libgtkglextmm-x11-1.2-0 [ amd64 ] < 1.2.0-4ubuntu3 > ( libs )
Broken libgtkglextmm-x11-1.2-0:amd64 Depends on libgtkglext1 [ amd64 ] < 1.2.0-1.1ubuntu1 > ( libs )
  Considering libgtkglext1:amd64 3 as a solution to libgtkglextmm-x11-1.2-0:amd64 0
  Removing libgtkglextmm-x11-1.2-0:amd64 rather than change libgtkglext1:amd64
Investigating (0) gnome-font-viewer [ amd64 ] < none -> 3.2.1-0ubuntu1 > ( gnome )
Broken gnome-font-viewer:amd64 Breaks on capplets-data [ amd64 ] < 1:2.32.1-0ubuntu15 > ( gnome ) (< 1:3.0.0)
  Considering capplets-data:amd64 -1 as a solution to gnome-font-viewer:amd64 0
  Added capplets-data:amd64 to the remove list
Broken gnome-font-viewer:amd64 Breaks on gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.2-0ubuntu1 > ( gnome ) (< 1:3.0.0)
  Considering gnome-control-center:amd64 20 as a solution to gnome-font-viewer:amd64 0
  Holding Back gnome-font-viewer:amd64 rather than change gnome-control-center:amd64
Investigating (0) libboost-iostreams-dev [ amd64 ] < 1.42.0.1ubuntu1 -> 1.46.1.1 > ( libdevel )
Broken libboost-iostreams-dev:amd64 Depends on libboost-iostreams1.46-dev [ amd64 ] < none -> 1.46.1-5ubuntu2 > ( libdevel )
  Considering libboost-iostreams1.46-dev:amd64 0 as a solution to libboost-iostreams-dev:amd64 0
  Holding Back libboost-iostreams-dev:amd64 rather than change libboost-iostreams1.46-dev:amd64
Investigating (0) libboost-test1.46-dev [ amd64 ] < none -> 1.46.1-5ubuntu2 > ( libdevel )
Broken libboost-test1.46-dev:amd64 Depends on libboost1.46-dev [ amd64 ] < none -> 1.46.1-5ubuntu2 > ( libdevel ) (= 1.46.1-5ubuntu2)
  Considering libboost1.46-dev:amd64 4 as a solution to libboost-test1.46-dev:amd64 0
  Holding Back libboost-test1.46-dev:amd64 rather than change libboost1.46-dev:amd64
Investigating (0) octave-signal [ amd64 ] < 1.0.11-2 > ( math )
Broken octave-signal:amd64 Depends on octave-optim [ amd64 ] < 1.0.12-1 > ( math ) (>= 1.0.5)
  Considering octave-optim:amd64 4 as a solution to octave-signal:amd64 0
  Removing octave-signal:amd64 rather than change octave-optim:amd64
Investigating (0) mesa-utils [ amd64 ] < 8.0.1+git20110129+d8f7d6b-0ubuntu2 > ( x11 )
Broken mesa-utils:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to mesa-utils:amd64 -1
Broken mesa-utils:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to mesa-utils:amd64 -1
  Or group remove for mesa-utils:amd64
Investigating (0) octave-ftp [ amd64 ] < 1.0.2-4build1 > ( math )
Broken octave-ftp:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-ftp:amd64 -1
  Removing octave-ftp:amd64 rather than change octave3.2:amd64
Investigating (0) filezilla [ amd64 ] < 3.3.5.1-1ubuntu1 > ( net )
Broken filezilla:amd64 Depends on libwxgtk2.8-0 [ amd64 ] < 2.8.11.0-0ubuntu8.1 > ( libs ) (>= 2.8.11.0)
  Considering libwxgtk2.8-0:amd64 9 as a solution to filezilla:amd64 -1
  Removing filezilla:amd64 rather than change libwxgtk2.8-0:amd64
Investigating (0) octave-combinatorics [ amd64 ] < 1.0.9-2build1 > ( math )
Broken octave-combinatorics:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-combinatorics:amd64 -1
  Removing octave-combinatorics:amd64 rather than change octave3.2:amd64
Investigating (0) libmono1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono )
Broken libmono1.0-cil:amd64 Depends on libmono-corlib1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono ) (>= 1.2.2.1)
  Considering libmono-corlib1.0-cil:amd64 81 as a solution to libmono1.0-cil:amd64 -1
  Removing libmono1.0-cil:amd64 rather than change libmono-corlib1.0-cil:amd64
Investigating (0) octave-ident [ amd64 ] < 1.0.7-2 > ( math )
Broken octave-ident:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-ident:amd64 -1
  Removing octave-ident:amd64 rather than change octave3.2:amd64
Investigating (0) libmono-system-ldap1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono )
Broken libmono-system-ldap1.0-cil:amd64 Depends on libmono-corlib1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono ) (>= 1.2.2.1)
  Considering libmono-corlib1.0-cil:amd64 81 as a solution to libmono-system-ldap1.0-cil:amd64 -1
  Removing libmono-system-ldap1.0-cil:amd64 rather than change libmono-corlib1.0-cil:amd64
Investigating (0) octave-ocs [ amd64 ] < 0.1.0-2 > ( math )
Broken octave-ocs:amd64 Depends on octave-odepkg [ amd64 ] < 0.6.10-1 > ( math )
  Considering octave-odepkg:amd64 1 as a solution to octave-ocs:amd64 -1
  Removing octave-ocs:amd64 rather than change octave-odepkg:amd64
Investigating (0) libbrasero-media1 [ amd64 ] < 2.32.1-0ubuntu2 > ( libs )
Broken libbrasero-media1:amd64 Depends on brasero-common [ amd64 ] < 2.32.1-0ubuntu2 -> 3.2.0-0ubuntu1.1 > ( gnome ) (< 2.33)
  Considering brasero-common:amd64 16 as a solution to libbrasero-media1:amd64 -1
  Removing libbrasero-media1:amd64 rather than change brasero-common:amd64
Investigating (0) octave-pdb [ amd64 ] < 1.0.7-2build1 > ( math )
Broken octave-pdb:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-pdb:amd64 -1
  Removing octave-pdb:amd64 rather than change octave3.2:amd64
Investigating (0) libmono-getoptions1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono )
Broken libmono-getoptions1.0-cil:amd64 Depends on libmono-corlib1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono ) (>= 1.2.2.1)
  Considering libmono-corlib1.0-cil:amd64 81 as a solution to libmono-getoptions1.0-cil:amd64 -1
  Removing libmono-getoptions1.0-cil:amd64 rather than change libmono-corlib1.0-cil:amd64
Investigating (0) gfortran-4.4 [ amd64 ] < 4.4.5-15ubuntu1 > ( devel )
Broken gfortran-4.4:amd64 Depends on gcc-4.4-base [ amd64 ] < 4.4.5-15ubuntu1 -> 4.4.6-11ubuntu2 > ( libs ) (= 4.4.5-15ubuntu1)
  Considering gcc-4.4-base:amd64 16 as a solution to gfortran-4.4:amd64 -1
  Removing gfortran-4.4:amd64 rather than change gcc-4.4-base:amd64
Investigating (0) libmono-data1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono )
Broken libmono-data1.0-cil:amd64 Depends on libmono-corlib1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono ) (>= 1.2.2.1)
  Considering libmono-corlib1.0-cil:amd64 81 as a solution to libmono-data1.0-cil:amd64 -1
  Removing libmono-data1.0-cil:amd64 rather than change libmono-corlib1.0-cil:amd64
Investigating (0) gfortran-4.5 [ amd64 ] < 4.5.2-8ubuntu4 > ( devel )
Broken gfortran-4.5:amd64 Depends on gcc-4.5-base [ amd64 ] < 4.5.2-8ubuntu4 -> 4.5.3-9ubuntu1 > ( libs ) (= 4.5.2-8ubuntu4)
  Considering gcc-4.5-base:amd64 16 as a solution to gfortran-4.5:amd64 -1
  Removing gfortran-4.5:amd64 rather than change gcc-4.5-base:amd64
Investigating (0) esound-clients [ amd64 ] < 0.2.41-8 > ( sound )
Broken esound-clients:amd64 Depends on esound-common [ amd64 ] < 0.2.41-8 -> 0.2.41-9 > ( sound ) (= 0.2.41-8)
  Considering esound-common:amd64 12 as a solution to esound-clients:amd64 -1
  Removing esound-clients:amd64 rather than change esound-common:amd64
Investigating (0) octave-vrml [ amd64 ] < 1.0.11-1 > ( math )
Broken octave-vrml:amd64 Depends on octave-miscellaneous [ amd64 ] < 1.0.9-1build2 > ( math )
  Considering octave-miscellaneous:amd64 7 as a solution to octave-vrml:amd64 -1
  Removing octave-vrml:amd64 rather than change octave-miscellaneous:amd64
Investigating (0) lives [ amd64 ] < 1.4.1-1ubuntu1 > ( video )
Broken lives:amd64 Depends on mplayer [ amd64 ] < 2:1.0~rc4.dfsg1-1ubuntu3 > ( video )
  Considering mplayer:amd64 3 as a solution to lives:amd64 -1
  Removing lives:amd64 rather than change mplayer:amd64
Investigating (0) octave-ad [ amd64 ] < 1.0.6-3build1 > ( math )
Broken octave-ad:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-ad:amd64 -1
  Removing octave-ad:amd64 rather than change octave3.2:amd64
Investigating (0) libglpng [ amd64 ] < 1.45-6 > ( libs )
Broken libglpng:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to libglpng:amd64 -1
Broken libglpng:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to libglpng:amd64 -1
  Or group remove for libglpng:amd64
Investigating (0) octave-missing-functions [ amd64 ] < 1.0.2-2 > ( math )
Broken octave-missing-functions:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-missing-functions:amd64 -1
  Removing octave-missing-functions:amd64 rather than change octave3.2:amd64
Investigating (0) octave-ga [ amd64 ] < 0.9.8-1 > ( math )
Broken octave-ga:amd64 Depends on octave-communications [ amd64 ] < 1.0.10-2 > ( math ) (>= 1.0.0)
  Considering octave-communications:amd64 1 as a solution to octave-ga:amd64 -1
  Removing octave-ga:amd64 rather than change octave-communications:amd64
Investigating (0) gdm-guest-session [ amd64 ] < 0.24ubuntu0.1 > ( gnome )
Broken gdm-guest-session:amd64 Depends on gdm [ amd64 ] < 2.32.1-0ubuntu3.2 > ( gnome ) (>= 2.30.0-0ubuntu5)
  Considering gdm:amd64 1 as a solution to gdm-guest-session:amd64 -1
  Removing gdm-guest-session:amd64 rather than change gdm:amd64
Investigating (0) octave-tsa [ amd64 ] < 4.0.1-2 > ( math )
Broken octave-tsa:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-tsa:amd64 -1
  Removing octave-tsa:amd64 rather than change octave3.2:amd64
Investigating (0) octave-io [ amd64 ] < 1.0.12-1 > ( math )
Broken octave-io:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-io:amd64 -1
  Removing octave-io:amd64 rather than change octave3.2:amd64
Investigating (0) git-gui [ amd64 ] < 1:1.7.4.1-3 > ( vcs )
Broken git-gui:amd64 Depends on git [ amd64 ] < 1:1.7.4.1-3 -> 1:1.7.5.4-1 > ( vcs ) (< 1:1.7.4.1-.)
  Considering git:amd64 13 as a solution to git-gui:amd64 -1
  Removing git-gui:amd64 rather than change git:amd64
Investigating (0) snes9x-gtk [ amd64 ] < 1:1.52-1 > ( non-free/games )
Broken snes9x-gtk:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to snes9x-gtk:amd64 -1
Broken snes9x-gtk:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to snes9x-gtk:amd64 -1
  Or group remove for snes9x-gtk:amd64
Investigating (0) octave-sp [ amd64 ] < 1:2003-10 > ( math )
Broken octave-sp:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.3)
  Considering octave3.2:amd64 126 as a solution to octave-sp:amd64 -1
  Removing octave-sp:amd64 rather than change octave3.2:amd64
Investigating (0) libglut3 [ amd64 ] < 3.7-25 > ( libs )
Broken libglut3:amd64 Depends on freeglut3 [ amd64 ] < 2.6.0-1ubuntu2 > ( libs )
  Considering freeglut3:amd64 11 as a solution to libglut3:amd64 -1
  Removing libglut3:amd64 rather than change freeglut3:amd64
Investigating (0) libmono-relaxng1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono )
Broken libmono-relaxng1.0-cil:amd64 Depends on libmono-corlib1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono ) (>= 1.2.2.1)
  Considering libmono-corlib1.0-cil:amd64 81 as a solution to libmono-relaxng1.0-cil:amd64 -1
  Removing libmono-relaxng1.0-cil:amd64 rather than change libmono-corlib1.0-cil:amd64
Investigating (0) python-traitsgui [ amd64 ] < 3.4.0-1 > ( python )
Broken python-traitsgui:amd64 Depends on python-traitsbackendwx [ amd64 ] < 3.4.0-1 > ( python )
  Considering python-traitsbackendwx:amd64 1 as a solution to python-traitsgui:amd64 -1
Broken python-traitsgui:amd64 Depends on python-traitsbackendqt [ amd64 ] < none > ( none )
  Or group remove for python-traitsgui:amd64
Broken python-traitsgui:amd64 Depends on python-wxgtk2.8 [ amd64 ] < 2.8.11.0-0ubuntu8.1 > ( python )
  Considering python-wxgtk2.8:amd64 3 as a solution to python-traitsgui:amd64 -1
  Removing python-traitsgui:amd64 rather than change python-wxgtk2.8:amd64
Investigating (0) python-visual [ amd64 ] < 1:5.12-1.1build2 > ( python )
Broken python-visual:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to python-visual:amd64 -1
Broken python-visual:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to python-visual:amd64 -1
  Or group remove for python-visual:amd64
Broken python-visual:amd64 Depends on libglu1-mesa [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libglu1-mesa:amd64 121 as a solution to python-visual:amd64 -1
Broken python-visual:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 121 as a solution to python-visual:amd64 -1
  Or group remove for python-visual:amd64
Broken python-visual:amd64 Depends on libgtkglextmm-x11-1.2-0 [ amd64 ] < 1.2.0-4ubuntu3 > ( libs )
  Considering libgtkglextmm-x11-1.2-0:amd64 0 as a solution to python-visual:amd64 -1
  Removing python-visual:amd64 rather than change libgtkglextmm-x11-1.2-0:amd64
Investigating (0) octave-mapping [ amd64 ] < 1.0.7-2 > ( math )
Broken octave-mapping:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-mapping:amd64 -1
  Removing octave-mapping:amd64 rather than change octave3.2:amd64
Investigating (0) supertux [ amd64 ] < 0.3.3-2 > ( games )
Broken supertux:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to supertux:amd64 -1
Broken supertux:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to supertux:amd64 -1
  Or group remove for supertux:amd64
Broken supertux:amd64 Depends on libglew1.5 [ amd64 ] < 1.5.7.is.1.5.2-1ubuntu2 -> 1.5.7.is.1.5.2-1ubuntu4 > ( libs ) (>= 1.5.2)
  Considering libglew1.5:amd64 10 as a solution to supertux:amd64 -1
  Removing supertux:amd64 rather than change libglew1.5:amd64
Investigating (0) xutils [ amd64 ] < 1:7.6+4ubuntu3.2 > ( x11 )
Broken xutils:amd64 Depends on x11-utils [ amd64 ] < 7.6+1 -> 7.6+3 > ( x11 )
  Considering x11-utils:amd64 49 as a solution to xutils:amd64 -1
  Removing xutils:amd64 rather than change x11-utils:amd64
Investigating (0) supertux-stable [ amd64 ] < 0.1.3-1.1ubuntu3 > ( games )
Broken supertux-stable:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to supertux-stable:amd64 -1
Broken supertux-stable:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to supertux-stable:amd64 -1
  Or group remove for supertux-stable:amd64
Investigating (0) octave-general [ amd64 ] < 1.2.2-1 > ( math )
Broken octave-general:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-general:amd64 -1
  Removing octave-general:amd64 rather than change octave3.2:amd64
Investigating (0) libmono-microsoft7.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono )
Broken libmono-microsoft7.0-cil:amd64 Depends on libmono-corlib1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono ) (>= 1.2.2.1)
  Considering libmono-corlib1.0-cil:amd64 81 as a solution to libmono-microsoft7.0-cil:amd64 -1
  Removing libmono-microsoft7.0-cil:amd64 rather than change libmono-corlib1.0-cil:amd64
Investigating (0) mencoder [ amd64 ] < 2:1.0~rc4.dfsg1-1ubuntu3 > ( video )
Broken mencoder:amd64 Depends on mplayer [ amd64 ] < 2:1.0~rc4.dfsg1-1ubuntu3 > ( video )
  Considering mplayer:amd64 3 as a solution to mencoder:amd64 -1
  Removing mencoder:amd64 rather than change mplayer:amd64
Investigating (0) octave-informationtheory [ amd64 ] < 0.1.8-1 > ( math )
Broken octave-informationtheory:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-informationtheory:amd64 -1
  Removing octave-informationtheory:amd64 rather than change octave3.2:amd64
Investigating (0) mono-2.0-devel [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono )
Broken mono-2.0-devel:amd64 Depends on libmono-corlib1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono ) (>= 1.2.2.1)
  Considering libmono-corlib1.0-cil:amd64 81 as a solution to mono-2.0-devel:amd64 -1
  Removing mono-2.0-devel:amd64 rather than change libmono-corlib1.0-cil:amd64
Investigating (0) octave-irsa [ amd64 ] < 1.0.7-2 > ( math )
Broken octave-irsa:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-irsa:amd64 -1
  Removing octave-irsa:amd64 rather than change octave3.2:amd64
Investigating (0) glutg3 [ amd64 ] < 3.7-25 > ( oldlibs )
Broken glutg3:amd64 Depends on freeglut3 [ amd64 ] < 2.6.0-1ubuntu2 > ( libs )
  Considering freeglut3:amd64 11 as a solution to glutg3:amd64 -1
  Removing glutg3:amd64 rather than change freeglut3:amd64
Investigating (0) libdevice-cdio-perl [ amd64 ] < 0.2.4-5build1 > ( perl )
Broken libdevice-cdio-perl:amd64 Depends on perlapi-5.10.1 [ amd64 ] < none > ( none )
  Considering perl-base:amd64 5396 as a solution to libdevice-cdio-perl:amd64 -1
  Removing libdevice-cdio-perl:amd64 rather than change perlapi-5.10.1:amd64
Investigating (0) gnome-utils [ amd64 ] < 2.32.0-0ubuntu5 > ( gnome )
Broken gnome-utils:amd64 Depends on gnome-dictionary [ amd64 ] < 2.32.0-0ubuntu5 > ( gnome )
  Considering gnome-dictionary:amd64 1 as a solution to gnome-utils:amd64 -1
  Removing gnome-utils:amd64 rather than change gnome-dictionary:amd64
Investigating (0) gconf-editor [ amd64 ] < 2.32.0-0ubuntu2 > ( utils )
Broken gconf-editor:amd64 Depends on gconf-defaults-service [ amd64 ] < 2.32.2-0ubuntu2 > ( libs ) (>= 2.28)
  Considering gconf-defaults-service:amd64 1 as a solution to gconf-editor:amd64 -1
  Removing gconf-editor:amd64 rather than change gconf-defaults-service:amd64
Investigating (0) octave-pfstools [ amd64 ] < 1.8.1-2ubuntu1 > ( math )
Broken octave-pfstools:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.4)
  Considering octave3.2:amd64 126 as a solution to octave-pfstools:amd64 -1
  Removing octave-pfstools:amd64 rather than change octave3.2:amd64
Investigating (0) octave-optiminterp [ amd64 ] < 0.3.2-2build1 > ( math )
Broken octave-optiminterp:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-optiminterp:amd64 -1
  Removing octave-optiminterp:amd64 rather than change octave3.2:amd64
Investigating (0) ktoon [ amd64 ] < 0.8.1-4.1ubuntu2 > ( graphics )
Broken ktoon:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to ktoon:amd64 -1
Broken ktoon:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to ktoon:amd64 -1
  Or group remove for ktoon:amd64
Broken ktoon:amd64 Depends on libqt4-opengl [ amd64 ] < 4:4.7.2-0ubuntu6.4 -> 4:4.7.4-0ubuntu8.3 > ( libs ) (>= 4:4.5.3)
  Considering libqt4-opengl:amd64 12 as a solution to ktoon:amd64 -1
  Removing ktoon:amd64 rather than change libqt4-opengl:amd64
Investigating (0) libmono-i18n1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono )
Broken libmono-i18n1.0-cil:amd64 Depends on libmono-corlib1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono ) (>= 1.2.2.1)
  Considering libmono-corlib1.0-cil:amd64 81 as a solution to libmono-i18n1.0-cil:amd64 -1
  Removing libmono-i18n1.0-cil:amd64 rather than change libmono-corlib1.0-cil:amd64
Investigating (0) libmono-oracle1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono )
Broken libmono-oracle1.0-cil:amd64 Depends on libmono-corlib1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono ) (>= 1.2.2.1)
  Considering libmono-corlib1.0-cil:amd64 81 as a solution to libmono-oracle1.0-cil:amd64 -1
  Removing libmono-oracle1.0-cil:amd64 rather than change libmono-corlib1.0-cil:amd64
Investigating (0) dgen [ amd64 ] < 1.23-11 > ( non-free/otherosfs )
Broken dgen:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to dgen:amd64 -1
Broken dgen:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to dgen:amd64 -1
  Or group remove for dgen:amd64
Investigating (0) libdevice-modem-perl [ amd64 ] < 1.47-2.1 > ( perl )
Broken libdevice-modem-perl:amd64 Depends on libdevice-serialport-perl [ amd64 ] < 1.04-2 > ( perl )
  Considering libdevice-serialport-perl:amd64 0 as a solution to libdevice-modem-perl:amd64 -1
  Removing libdevice-modem-perl:amd64 rather than change libdevice-serialport-perl:amd64
Investigating (0) octave-secs1d [ amd64 ] < 0.0.8-2build1 > ( math )
Broken octave-secs1d:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-secs1d:amd64 -1
  Removing octave-secs1d:amd64 rather than change octave3.2:amd64
Investigating (0) octave-secs2d [ amd64 ] < 0.0.8-2build1 > ( math )
Broken octave-secs2d:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-secs2d:amd64 -1
  Removing octave-secs2d:amd64 rather than change octave3.2:amd64
Investigating (0) octave-bioinfo [ amd64 ] < 0.1.2-2 > ( math )
Broken octave-bioinfo:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-bioinfo:amd64 -1
  Removing octave-bioinfo:amd64 rather than change octave3.2:amd64
Investigating (0) libedataserverui1.2-8 [ amd64 ] < 2.30.3-2ubuntu2.1 > ( libs )
Broken libedataserverui1.2-8:amd64 Depends on libebook1.2-9 [ amd64 ] < 2.30.3-2ubuntu2.1 > ( libs ) (>= 2.30.3)
  Considering libebook1.2-9:amd64 3 as a solution to libedataserverui1.2-8:amd64 -1
  Removing libedataserverui1.2-8:amd64 rather than change libebook1.2-9:amd64
Investigating (0) octave-integration [ amd64 ] < 1.0.7-2 > ( math )
Broken octave-integration:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-integration:amd64 -1
  Removing octave-integration:amd64 rather than change octave3.2:amd64
Investigating (0) libmono-winforms1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono )
Broken libmono-winforms1.0-cil:amd64 Depends on libmono-accessibility1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono ) (>= 1.0)
  Considering libmono-accessibility1.0-cil:amd64 1 as a solution to libmono-winforms1.0-cil:amd64 -1
  Removing libmono-winforms1.0-cil:amd64 rather than change libmono-accessibility1.0-cil:amd64
Investigating (0) octave-strings [ amd64 ] < 1.0.7-2 > ( math )
Broken octave-strings:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-strings:amd64 -1
  Removing octave-strings:amd64 rather than change octave3.2:amd64
Investigating (0) libedata-book1.2-2 [ amd64 ] < 2.30.3-2ubuntu2.1 > ( libs )
Broken libedata-book1.2-2:amd64 Depends on libebook1.2-9 [ amd64 ] < 2.30.3-2ubuntu2.1 > ( libs ) (>= 2.30.3)
  Considering libebook1.2-9:amd64 3 as a solution to libedata-book1.2-2:amd64 -1
  Removing libedata-book1.2-2:amd64 rather than change libebook1.2-9:amd64
Investigating (0) dosbox [ amd64 ] < 0.74-1 > ( otherosfs )
Broken dosbox:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to dosbox:amd64 -1
Broken dosbox:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to dosbox:amd64 -1
  Or group remove for dosbox:amd64
Investigating (0) gnome-themes-selected [ amd64 ] < 2.32.1-0ubuntu1 > ( gnome )
Broken gnome-themes-selected:amd64 Depends on gtk2-engines-pixbuf [ amd64 ] < 2.24.4-0ubuntu2 > ( graphics )
  Considering gtk2-engines-pixbuf:amd64 3 as a solution to gnome-themes-selected:amd64 -1
  Removing gnome-themes-selected:amd64 rather than change gtk2-engines-pixbuf:amd64
Investigating (0) phonon-backend-xine [ amd64 ] < 4:4.7.0really4.4.4-0ubuntu3 > ( sound )
Broken phonon-backend-xine:amd64 Depends on libxine1 [ amd64 ] < 1.1.19-2ubuntu5 -> 1.1.19-2ubuntu6 > ( libs ) (>= 1.1.8-1)
  Considering libxine1:amd64 2 as a solution to phonon-backend-xine:amd64 -1
  Removing phonon-backend-xine:amd64 rather than change libxine1:amd64
Investigating (0) libpgplot-perl [ amd64 ] < 1:2.20-1 > ( contrib/perl )
Broken libpgplot-perl:amd64 Depends on perlapi-5.10.0 [ amd64 ] < none > ( none )
  Considering perl-base:amd64 5396 as a solution to libpgplot-perl:amd64 -1
  Removing libpgplot-perl:amd64 rather than change perlapi-5.10.0:amd64
Investigating (0) gcc-4.4-multilib [ amd64 ] < 4.4.5-15ubuntu1 > ( devel )
Broken gcc-4.4-multilib:amd64 Depends on gcc-4.4-base [ amd64 ] < 4.4.5-15ubuntu1 -> 4.4.6-11ubuntu2 > ( libs ) (= 4.4.5-15ubuntu1)
  Considering gcc-4.4-base:amd64 16 as a solution to gcc-4.4-multilib:amd64 -1
  Removing gcc-4.4-multilib:amd64 rather than change gcc-4.4-base:amd64
Investigating (0) octave-symbolic [ amd64 ] < 1.0.9-1build1 > ( math )
Broken octave-symbolic:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-symbolic:amd64 -1
  Removing octave-symbolic:amd64 rather than change octave3.2:amd64
Investigating (0) libmono-bytefx0.7.6.1-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono )
Broken libmono-bytefx0.7.6.1-cil:amd64 Depends on libmono-corlib1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono ) (>= 1.2.2.1)
  Considering libmono-corlib1.0-cil:amd64 81 as a solution to libmono-bytefx0.7.6.1-cil:amd64 -1
  Removing libmono-bytefx0.7.6.1-cil:amd64 rather than change libmono-corlib1.0-cil:amd64
Investigating (0) libvtk5.4 [ amd64 ] < 5.4.2-8ubuntu4 > ( libs )
Broken libvtk5.4:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to libvtk5.4:amd64 -1
Broken libvtk5.4:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to libvtk5.4:amd64 -1
  Or group remove for libvtk5.4:amd64
Investigating (0) octave-image [ amd64 ] < 1.0.12-1 > ( math )
Broken octave-image:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-image:amd64 -1
  Removing octave-image:amd64 rather than change octave3.2:amd64
Investigating (0) libmono-npgsql1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono )
Broken libmono-npgsql1.0-cil:amd64 Depends on libmono-corlib1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono ) (>= 1.2.2.1)
  Considering libmono-corlib1.0-cil:amd64 81 as a solution to libmono-npgsql1.0-cil:amd64 -1
  Removing libmono-npgsql1.0-cil:amd64 rather than change libmono-corlib1.0-cil:amd64
Investigating (0) liblapack-pic [ amd64 ] < 3.3.0-3 > ( libdevel )
Broken liblapack-pic:amd64 Depends on liblapack3gf [ amd64 ] < 3.3.0-3 -> 3.3.1-1 > ( libs ) (= 3.3.0-3)
  Considering liblapack3gf:amd64 133 as a solution to liblapack-pic:amd64 -1
  Removing liblapack-pic:amd64 rather than change liblapack3gf:amd64
Investigating (0) libmono-peapi1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono )
Broken libmono-peapi1.0-cil:amd64 Depends on libmono-corlib1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono ) (>= 1.2.2.1)
  Considering libmono-corlib1.0-cil:amd64 81 as a solution to libmono-peapi1.0-cil:amd64 -1
  Removing libmono-peapi1.0-cil:amd64 rather than change libmono-corlib1.0-cil:amd64
Investigating (0) gnome-themes-ubuntu [ amd64 ] < 0.6.1 > ( gnome )
Broken gnome-themes-ubuntu:amd64 Depends on gtk2-engines-pixbuf [ amd64 ] < 2.24.4-0ubuntu2 > ( graphics )
  Considering gtk2-engines-pixbuf:amd64 3 as a solution to gnome-themes-ubuntu:amd64 -1
  Removing gnome-themes-ubuntu:amd64 rather than change gtk2-engines-pixbuf:amd64
Investigating (0) libdevhelp-2-1 [ amd64 ] < 2.32.0-0ubuntu2 > ( libs )
Broken libdevhelp-2-1:amd64 Depends on devhelp-common [ amd64 ] < 2.32.0-0ubuntu2 -> 3.2.0-1 > ( devel ) (= 2.32.0-0ubuntu2)
  Considering devhelp-common:amd64 3 as a solution to libdevhelp-2-1:amd64 -1
  Removing libdevhelp-2-1:amd64 rather than change devhelp-common:amd64
Investigating (0) octave-nnet [ amd64 ] < 0.1.12-1 > ( math )
Broken octave-nnet:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-nnet:amd64 -1
  Removing octave-nnet:amd64 rather than change octave3.2:amd64
Investigating (0) octave-outliers [ amd64 ] < 0.13.9-2 > ( math )
Broken octave-outliers:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-outliers:amd64 -1
  Removing octave-outliers:amd64 rather than change octave3.2:amd64
Investigating (0) octave-zenity [ amd64 ] < 0.5.7-2 > ( math )
Broken octave-zenity:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-zenity:amd64 -1
  Removing octave-zenity:amd64 rather than change octave3.2:amd64
Investigating (0) octave-sockets [ amd64 ] < 1.0.6-1build1 > ( math )
Broken octave-sockets:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-sockets:amd64 -1
  Removing octave-sockets:amd64 rather than change octave3.2:amd64
Investigating (0) octave-linear-algebra [ amd64 ] < 2.0.0-1 > ( math )
Broken octave-linear-algebra:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-linear-algebra:amd64 -1
  Removing octave-linear-algebra:amd64 rather than change octave3.2:amd64
Investigating (0) octave-multicore [ amd64 ] < 0.2.15-1build1 > ( math )
Broken octave-multicore:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-multicore:amd64 -1
  Removing octave-multicore:amd64 rather than change octave3.2:amd64
Investigating (0) libmono-sharpzip0.6-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono )
Broken libmono-sharpzip0.6-cil:amd64 Depends on libmono-corlib1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono ) (>= 1.2.2.1)
  Considering libmono-corlib1.0-cil:amd64 81 as a solution to libmono-sharpzip0.6-cil:amd64 -1
  Removing libmono-sharpzip0.6-cil:amd64 rather than change libmono-corlib1.0-cil:amd64
Investigating (0) libmono-cscompmgd7.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono )
Broken libmono-cscompmgd7.0-cil:amd64 Depends on libmono-corlib1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono ) (>= 1.2.2.1)
  Considering libmono-corlib1.0-cil:amd64 81 as a solution to libmono-cscompmgd7.0-cil:amd64 -1
  Removing libmono-cscompmgd7.0-cil:amd64 rather than change libmono-corlib1.0-cil:amd64
Investigating (0) googleearth-package [ amd64 ] < 0.6.1 > ( contrib/misc )
Broken googleearth-package:amd64 Depends on x11-utils [ amd64 ] < 7.6+1 -> 7.6+3 > ( x11 )
  Considering x11-utils:amd64 49 as a solution to googleearth-package:amd64 -1
  Removing googleearth-package:amd64 rather than change x11-utils:amd64
Investigating (0) libmono-sqlite1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono )
Broken libmono-sqlite1.0-cil:amd64 Depends on libmono-corlib1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono ) (>= 1.2.2.1)
  Considering libmono-corlib1.0-cil:amd64 81 as a solution to libmono-sqlite1.0-cil:amd64 -1
  Removing libmono-sqlite1.0-cil:amd64 rather than change libmono-corlib1.0-cil:amd64
Investigating (0) chromium-bsu [ amd64 ] < 0.9.15-1 > ( games )
Broken chromium-bsu:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to chromium-bsu:amd64 -1
Broken chromium-bsu:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to chromium-bsu:amd64 -1
  Or group remove for chromium-bsu:amd64
Broken chromium-bsu:amd64 Depends on libglc0 [ amd64 ] < 0.7.2-4build1 > ( libs ) (>= 0.7.1)
  Considering libglc0:amd64 1 as a solution to chromium-bsu:amd64 -1
  Removing chromium-bsu:amd64 rather than change libglc0:amd64
Investigating (0) octave-xraylib [ amd64 ] < 1.0.8-2build1 > ( math )
Broken octave-xraylib:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-xraylib:amd64 -1
  Removing octave-xraylib:amd64 rather than change octave3.2:amd64
Investigating (0) octave-fixed [ amd64 ] < 0.7.10-2build1 > ( math )
Broken octave-fixed:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-fixed:amd64 -1
  Removing octave-fixed:amd64 rather than change octave3.2:amd64
Investigating (0) octave-audio [ amd64 ] < 1.1.4-2build1 > ( math )
Broken octave-audio:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-audio:amd64 -1
  Removing octave-audio:amd64 rather than change octave3.2:amd64
Investigating (0) aconnectgui [ amd64 ] < 0.9.0rc2-1-9 > ( sound )
Broken aconnectgui:amd64 Depends on libfltk1.1 [ amd64 ] < 1.1.10-3 -> 1.1.10-7 > ( libs ) (>= 1.1.6)
  Considering libfltk1.1:amd64 74 as a solution to aconnectgui:amd64 -1
  Removing aconnectgui:amd64 rather than change libfltk1.1:amd64
Investigating (0) vlc [ amd64 ] < 1.1.9-1ubuntu1.3 > ( video )
Broken vlc:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to vlc:amd64 -1
Broken vlc:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to vlc:amd64 -1
  Or group remove for vlc:amd64
Investigating (0) octave-nurbs [ amd64 ] < 1.0.3-1 > ( math )
Broken octave-nurbs:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-nurbs:amd64 -1
  Removing octave-nurbs:amd64 rather than change octave3.2:amd64
Investigating (0) libnux-0.9-0 [ amd64 ] < 0.9.48-0ubuntu1.1 > ( libs )
Broken libnux-0.9-0:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to libnux-0.9-0:amd64 -1
Broken libnux-0.9-0:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to libnux-0.9-0:amd64 -1
  Or group remove for libnux-0.9-0:amd64
Broken libnux-0.9-0:amd64 Depends on libglew1.5 [ amd64 ] < 1.5.7.is.1.5.2-1ubuntu2 -> 1.5.7.is.1.5.2-1ubuntu4 > ( libs ) (>= 1.5.7.is.1.5.2)
  Considering libglew1.5:amd64 10 as a solution to libnux-0.9-0:amd64 -1
  Removing libnux-0.9-0:amd64 rather than change libglew1.5:amd64
Investigating (0) libperl5.10 [ amd64 ] < 5.10.1-17ubuntu4.1 > ( libs )
Broken libperl5.10:amd64 Depends on perl-base [ amd64 ] < 5.10.1-17ubuntu4.1 -> 5.12.4-4ubuntu0.2 > ( perl ) (= 5.10.1-17ubuntu4.1)
  Considering perl-base:amd64 5396 as a solution to libperl5.10:amd64 -1
  Removing libperl5.10:amd64 rather than change perl-base:amd64
Investigating (0) libdevil-dev [ amd64 ] < 1.7.8-6build1 > ( libdevel )
Broken libdevil-dev:amd64 Depends on libdevil1c2 [ amd64 ] < 1.7.8-6build1 > ( libs ) (= 1.7.8-6build1)
  Considering libdevil1c2:amd64 1 as a solution to libdevil-dev:amd64 -1
  Removing libdevil-dev:amd64 rather than change libdevil1c2:amd64
Investigating (0) octave-econometrics [ amd64 ] < 1:1.0.8-2build1 > ( math )
Broken octave-econometrics:amd64 Depends on octave-optim [ amd64 ] < 1.0.12-1 > ( math )
  Considering octave-optim:amd64 4 as a solution to octave-econometrics:amd64 -1
  Removing octave-econometrics:amd64 rather than change octave-optim:amd64
Investigating (0) octave-plot [ amd64 ] < 1.0.8-1 > ( math )
Broken octave-plot:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-plot:amd64 -1
  Removing octave-plot:amd64 rather than change octave3.2:amd64
Investigating (0) plymouth-x11 [ amd64 ] < 0.8.2-2ubuntu23 > ( x11 )
Broken plymouth-x11:amd64 Depends on libplymouth2 [ amd64 ] < 0.8.2-2ubuntu23 -> 0.8.2-2ubuntu28 > ( libs ) (= 0.8.2-2ubuntu23)
  Considering libplymouth2:amd64 29 as a solution to plymouth-x11:amd64 -1
  Removing plymouth-x11:amd64 rather than change libplymouth2:amd64
Investigating (0) octave-pkg-dev [ amd64 ] < 0.7.3 > ( devel )
Broken octave-pkg-dev:amd64 Depends on octave3.2-headers [ amd64 ] < 3.2.4-8 > ( math )
  Considering octave3.2-headers:amd64 1 as a solution to octave-pkg-dev:amd64 -1
  Removing octave-pkg-dev:amd64 rather than change octave3.2-headers:amd64
Investigating (0) octave-financial [ amd64 ] < 0.3.2-1 > ( math )
Broken octave-financial:amd64 Depends on octave-miscellaneous [ amd64 ] < 1.0.9-1build2 > ( math ) (>= 1.0.9-1)
  Considering octave-miscellaneous:amd64 7 as a solution to octave-financial:amd64 -1
  Removing octave-financial:amd64 rather than change octave-miscellaneous:amd64
Investigating (0) libmono-cairo1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono )
Broken libmono-cairo1.0-cil:amd64 Depends on libmono-corlib1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono ) (>= 1.2.2.1)
  Considering libmono-corlib1.0-cil:amd64 81 as a solution to libmono-cairo1.0-cil:amd64 -1
  Removing libmono-cairo1.0-cil:amd64 rather than change libmono-corlib1.0-cil:amd64
Investigating (0) computer-janitor-gtk [ amd64 ] < 2.1.0-0ubuntu4 > ( admin )
Broken computer-janitor-gtk:amd64 Depends on computer-janitor [ amd64 ] < 2.1.0-0ubuntu4 -> 2.1.0-0ubuntu6 > ( admin ) (= 2.1.0-0ubuntu4)
  Considering computer-janitor:amd64 2 as a solution to computer-janitor-gtk:amd64 -1
  Removing computer-janitor-gtk:amd64 rather than change computer-janitor:amd64
Investigating (0) octave-parallel [ amd64 ] < 2.0.4-1 > ( math )
Broken octave-parallel:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-parallel:amd64 -1
  Removing octave-parallel:amd64 rather than change octave3.2:amd64
Investigating (0) octave-epstk [ amd64 ] < 2.3-1 > ( math )
Broken octave-epstk:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.4)
  Considering octave3.2:amd64 126 as a solution to octave-epstk:amd64 -1
  Removing octave-epstk:amd64 rather than change octave3.2:amd64
Investigating (0) octave-nlwing2 [ amd64 ] < 1.1.1-3build1 > ( math )
Broken octave-nlwing2:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-nlwing2:amd64 -1
  Removing octave-nlwing2:amd64 rather than change octave3.2:amd64
Investigating (0) libgnome2-perl [ amd64 ] < 1.042-2build1 > ( perl )
Broken libgnome2-perl:amd64 Depends on perlapi-5.10.1 [ amd64 ] < none > ( none )
  Considering perl-base:amd64 5396 as a solution to libgnome2-perl:amd64 -1
  Removing libgnome2-perl:amd64 rather than change perlapi-5.10.1:amd64
Investigating (0) autokey-gtk [ amd64 ] < 0.71.2-1 > ( gnome )
Broken autokey-gtk:amd64 Depends on python-gtksourceview2 [ amd64 ] < 2.10.1-1build1 > ( python )
  Considering python-gtksourceview2:amd64 1 as a solution to autokey-gtk:amd64 -1
  Removing autokey-gtk:amd64 rather than change python-gtksourceview2:amd64
Investigating (0) lib32v4l-dev [ amd64 ] < 0.8.3-1 > ( libdevel )
Broken lib32v4l-dev:amd64 Depends on libv4l-0 [ amd64 ] < 0.8.3-1 -> 0.8.5-3ubuntu2 > ( libs ) (= 0.8.3-1)
  Considering libv4l-0:amd64 34 as a solution to lib32v4l-dev:amd64 -1
  Removing lib32v4l-dev:amd64 rather than change libv4l-0:amd64
Investigating (0) fceux [ amd64 ] < 2.1.4a+repack-0ubuntu1 > ( otherosfs )
Broken fceux:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to fceux:amd64 -1
Broken fceux:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to fceux:amd64 -1
  Or group remove for fceux:amd64
Investigating (0) compiz-fusion-plugins-main [ amd64 ] < 0.9.4+bzr20110527-0ubuntu1~natty1 -> 1:0.9.6-0ubuntu4.2 > ( x11 )
Broken compiz-fusion-plugins-main:amd64 Depends on compiz-plugins-main [ amd64 ] < 0.9.4+bzr20110527-0ubuntu1~natty1 -> 1:0.9.6-0ubuntu4.2 > ( x11 )
  Considering compiz-plugins-main:amd64 1 as a solution to compiz-fusion-plugins-main:amd64 -1
  Removing compiz-fusion-plugins-main:amd64 rather than change compiz-plugins-main:amd64
Investigating (0) libmono-system-messaging1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono )
Broken libmono-system-messaging1.0-cil:amd64 Depends on libmono-corlib1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono ) (>= 1.2.2.1)
  Considering libmono-corlib1.0-cil:amd64 81 as a solution to libmono-system-messaging1.0-cil:amd64 -1
  Removing libmono-system-messaging1.0-cil:amd64 rather than change libmono-corlib1.0-cil:amd64
Investigating (0) octave-simp [ amd64 ] < 1.1.0-2 > ( math )
Broken octave-simp:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-simp:amd64 -1
  Removing octave-simp:amd64 rather than change octave3.2:amd64
Investigating (0) octave-octcdf [ amd64 ] < 1.0.13-2 > ( math )
Broken octave-octcdf:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-octcdf:amd64 -1
  Removing octave-octcdf:amd64 rather than change octave3.2:amd64
Investigating (0) octave-data-smoothing [ amd64 ] < 1.2.0-2 > ( math )
Broken octave-data-smoothing:amd64 Depends on octave-optim [ amd64 ] < 1.0.12-1 > ( math ) (>= 1.0.3)
  Considering octave-optim:amd64 4 as a solution to octave-data-smoothing:amd64 -1
  Removing octave-data-smoothing:amd64 rather than change octave-optim:amd64
Investigating (0) pdftk [ amd64 ] < 1.44-1 > ( text )
Broken pdftk:amd64 Depends on libgcj11 [ amd64 ] < 4.5.2-8ubuntu1 > ( libs ) (>= 4.4)
  Considering libgcj11:amd64 2 as a solution to pdftk:amd64 -1
  Removing pdftk:amd64 rather than change libgcj11:amd64
Investigating (0) achilles [ amd64 ] < 2-8 > ( science )
Broken achilles:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to achilles:amd64 -1
Broken achilles:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to achilles:amd64 -1
  Or group remove for achilles:amd64
Broken achilles:amd64 Depends on libglu1-mesa [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libglu1-mesa:amd64 121 as a solution to achilles:amd64 -1
Broken achilles:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 121 as a solution to achilles:amd64 -1
  Or group remove for achilles:amd64
Investigating (0) lincity-ng [ amd64 ] < 2.0-2build1 > ( games )
Broken lincity-ng:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to lincity-ng:amd64 -1
Broken lincity-ng:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to lincity-ng:amd64 -1
  Or group remove for lincity-ng:amd64
Investigating (0) octave-symband [ amd64 ] < 1.0.10-1build1 > ( math )
Broken octave-symband:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-symband:amd64 -1
  Removing octave-symband:amd64 rather than change octave3.2:amd64
Investigating (0) golly [ amd64 ] < 2.2-1 > ( games )
Broken golly:amd64 Depends on libwxgtk2.8-0 [ amd64 ] < 2.8.11.0-0ubuntu8.1 > ( libs ) (>= 2.8.11.0)
  Considering libwxgtk2.8-0:amd64 9 as a solution to golly:amd64 -1
  Removing golly:amd64 rather than change libwxgtk2.8-0:amd64
Investigating (0) libmono-system-runtime1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono )
Broken libmono-system-runtime1.0-cil:amd64 Depends on libmono-corlib1.0-cil [ amd64 ] < 2.6.7-5ubuntu3.1 > ( cli-mono ) (>= 1.2.2.1)
  Considering libmono-corlib1.0-cil:amd64 81 as a solution to libmono-system-runtime1.0-cil:amd64 -1
  Removing libmono-system-runtime1.0-cil:amd64 rather than change libmono-corlib1.0-cil:amd64
Investigating (0) octave-physicalconstants [ amd64 ] < 0.1.7-2 > ( math )
Broken octave-physicalconstants:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-physicalconstants:amd64 -1
  Removing octave-physicalconstants:amd64 rather than change octave3.2:amd64
Investigating (0) octave-benchmark [ amd64 ] < 1.1.1-2 > ( math )
Broken octave-benchmark:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-benchmark:amd64 -1
  Removing octave-benchmark:amd64 rather than change octave3.2:amd64
Investigating (0) openuniverse [ amd64 ] < 1.0beta3.1+dfsg-1build1 > ( science )
Broken openuniverse:amd64 Depends on freeglut3 [ amd64 ] < 2.6.0-1ubuntu2 > ( libs )
  Considering freeglut3:amd64 11 as a solution to openuniverse:amd64 -1
  Removing openuniverse:amd64 rather than change freeglut3:amd64
Investigating (0) octave-bim [ amd64 ] < 1.0.0-1 > ( math )
Broken octave-bim:amd64 Depends on octave-fpl [ amd64 ] < 1.0.0-1 > ( math )
  Considering octave-fpl:amd64 3 as a solution to octave-bim:amd64 -1
  Removing octave-bim:amd64 rather than change octave-fpl:amd64
Investigating (0) octave-ann [ amd64 ] < 1.0.2+dfsg-2build1 > ( math )
Broken octave-ann:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-ann:amd64 -1
  Removing octave-ann:amd64 rather than change octave3.2:amd64
Investigating (0) octave-octgpr [ amd64 ] < 1.2.0-1 > ( math )
Broken octave-octgpr:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.0-1)
  Considering octave3.2:amd64 126 as a solution to octave-octgpr:amd64 -1
  Removing octave-octgpr:amd64 rather than change octave3.2:amd64
Investigating (0) python-opengl [ amd64 ] < 3.0.1~b2-1 > ( python )
Broken python-opengl:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to python-opengl:amd64 -1
Broken python-opengl:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to python-opengl:amd64 -1
  Or group remove for python-opengl:amd64
Broken python-opengl:amd64 Depends on libglu1-mesa [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libglu1-mesa:amd64 121 as a solution to python-opengl:amd64 -1
Broken python-opengl:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 121 as a solution to python-opengl:amd64 -1
  Or group remove for python-opengl:amd64
Broken python-opengl:amd64 Depends on freeglut3 [ amd64 ] < 2.6.0-1ubuntu2 > ( libs )
  Considering freeglut3:amd64 11 as a solution to python-opengl:amd64 -1
  Removing python-opengl:amd64 rather than change freeglut3:amd64
Investigating (0) celestia-gnome [ amd64 ] < 1.6.0+dfsg-2 > ( gnome )
Broken celestia-gnome:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to celestia-gnome:amd64 -1
Broken celestia-gnome:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to celestia-gnome:amd64 -1
  Or group remove for celestia-gnome:amd64
Broken celestia-gnome:amd64 Depends on libglu1-mesa [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libglu1-mesa:amd64 121 as a solution to celestia-gnome:amd64 -1
Broken celestia-gnome:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 121 as a solution to celestia-gnome:amd64 -1
  Or group remove for celestia-gnome:amd64
Broken celestia-gnome:amd64 Depends on libgtkglext1 [ amd64 ] < 1.2.0-1.1ubuntu1 > ( libs )
  Considering libgtkglext1:amd64 3 as a solution to celestia-gnome:amd64 -1
  Removing celestia-gnome:amd64 rather than change libgtkglext1:amd64
Investigating (0) libpackagekit-qt-14 [ amd64 ] < 0.6.8-0ubuntu3.2 > ( libs )
Broken libpackagekit-qt-14:amd64 Depends on libapt-pkg4.10 [ amd64 ] < none > ( none )
  Considering apt:amd64 30 as a solution to libpackagekit-qt-14:amd64 -2
  Removing libpackagekit-qt-14:amd64 rather than change libapt-pkg4.10:amd64
Investigating (0) brltty-x11 [ amd64 ] < 4.2-8ubuntu2 > ( admin )
Broken brltty-x11:amd64 Depends on brltty [ amd64 ] < 4.2-8ubuntu2 -> 4.2-8ubuntu5.1 > ( admin ) (= 4.2-8ubuntu2)
  Considering brltty:amd64 3 as a solution to brltty-x11:amd64 -2
  Removing brltty-x11:amd64 rather than change brltty:amd64
Investigating (0) nvidia-cg-toolkit [ amd64 ] < 3.0.0007-0ubuntu1 > ( non-free/libs )
Broken nvidia-cg-toolkit:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to nvidia-cg-toolkit:amd64 -2
Broken nvidia-cg-toolkit:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to nvidia-cg-toolkit:amd64 -2
  Or group remove for nvidia-cg-toolkit:amd64
Broken nvidia-cg-toolkit:amd64 Depends on libglu1-mesa [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libglu1-mesa:amd64 121 as a solution to nvidia-cg-toolkit:amd64 -2
Broken nvidia-cg-toolkit:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 121 as a solution to nvidia-cg-toolkit:amd64 -2
  Or group remove for nvidia-cg-toolkit:amd64
Investigating (0) alsa-tools-gui [ amd64 ] < 1.0.24.1-0ubuntu1 > ( sound )
Broken alsa-tools-gui:amd64 Depends on libfltk1.1 [ amd64 ] < 1.1.10-3 -> 1.1.10-7 > ( libs ) (>= 1.1.6)
  Considering libfltk1.1:amd64 74 as a solution to alsa-tools-gui:amd64 -2
  Removing alsa-tools-gui:amd64 rather than change libfltk1.1:amd64
Investigating (0) gens [ i386 ] < 2.16.7 > ( games )
Broken gens:i386 Depends on libgl1-mesa-glx [ i386 ] < none -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:i386 2 as a solution to gens:i386 -2
  Try Installing libgl1-mesa-glx [ i386 ] < none -> 7.11-0ubuntu3.2 > ( libs ) before changing gens:i386
    Installing libglapi-mesa as Depends of libgl1-mesa-glx
Broken gens:i386 Depends on libgl1 [ i386 ] < none > ( none )
  Considering libgl1-mesa-swx11:i386 0 as a solution to gens:i386 -2
  Or group remove for gens:i386
Broken gens:i386 Depends on libglib2.0-0 [ i386 ] < none -> 2.30.0-0ubuntu4 > ( libs ) (>= 2.4.0)
  Considering libglib2.0-0:i386 9 as a solution to gens:i386 -2
  Removing gens:i386 rather than change libglib2.0-0:i386
Investigating (0) octave-plplot [ amd64 ] < 5.9.5-4ubuntu3 > ( math )
Broken octave-plplot:amd64 Depends on octave3.2 [ amd64 ] < 3.2.4-8 > ( math ) (>= 3.2.4)
  Considering octave3.2:amd64 126 as a solution to octave-plplot:amd64 -2
  Removing octave-plplot:amd64 rather than change octave3.2:amd64
Investigating (1) libglib2.0-0 [ amd64 ] < 2.28.6-0ubuntu1 -> 2.30.0-0ubuntu4 > ( libs )
Broken libglib2.0-0:amd64 Breaks on gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.2-0ubuntu1 > ( gnome ) (< 1:3)
  Considering gnome-control-center:amd64 20 as a solution to libglib2.0-0:amd64 4044
  Upgrading gnome-control-center:amd64 due to Breaks field in libglib2.0-0:amd64
Investigating (1) gnuplot [ amd64 ] < 4.4.2-0ubuntu1 > ( math )
Broken gnuplot:amd64 Depends on gnuplot-x11 [ amd64 ] < 4.4.2-0ubuntu1 > ( math ) (>= 4.4.2-0ubuntu1)
  Considering gnuplot-x11:amd64 2 as a solution to gnuplot:amd64 66
  Added gnuplot-x11:amd64 to the remove list
  Fixing gnuplot:amd64 via keep of gnuplot-x11:amd64
Investigating (1) gvfs [ amd64 ] < 1.8.0-0ubuntu4 -> 1.10.0-0ubuntu1.1 > ( libs )
Broken gvfs:amd64 Depends on x11-utils [ amd64 ] < 7.6+1 -> 7.6+3 > ( x11 )
  Considering x11-utils:amd64 49 as a solution to gvfs:amd64 62
  Added x11-utils:amd64 to the remove list
  Fixing gvfs:amd64 via keep of x11-utils:amd64
 Try to Re-Instate (1) x11-utils:amd64
Investigating (1) x11-utils [ amd64 ] < 7.6+1 -> 7.6+3 > ( x11 )
Broken x11-utils:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libgl1-mesa-glx:amd64 238 as a solution to x11-utils:amd64 49
Broken x11-utils:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 238 as a solution to x11-utils:amd64 49
  Or group remove for x11-utils:amd64
 Try to Re-Instate (1) gnome-settings-daemon:amd64
Investigating (1) gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.2-0ubuntu1 > ( gnome )
Broken gnome-control-center:amd64 Depends on libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.1-0ubuntu1.1 > ( libs ) (>= 3.1.2)
  Considering libgnome-desktop-3-2:amd64 36 as a solution to gnome-control-center:amd64 20
  Holding Back gnome-control-center:amd64 rather than change libgnome-desktop-3-2:amd64
Investigating (1) phonon [ amd64 ] < 4:4.7.0really4.5.0-0ubuntu3 -> 4:4.7.0really4.5.0-3ubuntu4 > ( sound )
Broken phonon:amd64 Depends on phonon-backend-gstreamer [ amd64 ] < none -> 4:4.7.0really4.5.1-1ubuntu3 > ( sound )
  Considering phonon-backend-gstreamer:amd64 2 as a solution to phonon:amd64 19
  Try Installing phonon-backend-gstreamer [ amd64 ] < none -> 4:4.7.0really4.5.1-1ubuntu3 > ( sound ) before changing phonon:amd64
    Installing libgl1-mesa-glx as Depends of phonon-backend-gstreamer
    Installing libqt4-opengl as Depends of phonon-backend-gstreamer
 Try to Re-Instate (1) libevolution:amd64
Investigating (1) libedataserver1.2-13 [ amd64 ] < 2.30.3-2ubuntu2.1 > ( libs )
Broken libedataserver1.2-13:amd64 Depends on libnspr4-0d [ amd64 ] < 4.8.7-0ubuntu1 > ( libs ) (>= 4.7.3-0ubuntu1~)
  Considering libnspr4-0d:amd64 8 as a solution to libedataserver1.2-13:amd64 10
  Added libnspr4-0d:amd64 to the remove list
  Fixing libedataserver1.2-13:amd64 via keep of libnspr4-0d:amd64
Investigating (1) libnspr4-0d [ amd64 ] < 4.8.7-0ubuntu1 > ( libs )
Broken libnspr4-0d:amd64 Depends on libnspr4 [ amd64 ] < 4.8.7-0ubuntu1 -> 4.9.5-0ubuntu0.11.10.1 > ( libs ) (= 4.8.7-0ubuntu1)
  Considering libnspr4:amd64 121 as a solution to libnspr4-0d:amd64 8
  Removing libnspr4-0d:amd64 rather than change libnspr4:amd64
Investigating (1) unity-2d [ amd64 ] < none -> 4.12.0-0ubuntu1.4 > ( x11 )
Broken unity-2d:amd64 Depends on unity-2d-launcher [ amd64 ] < none -> 4.12.0-0ubuntu1.4 > ( x11 )
  Considering unity-2d-launcher:amd64 1 as a solution to unity-2d:amd64 5
  Holding Back unity-2d:amd64 rather than change unity-2d-launcher:amd64
 Try to Re-Instate (1) evolution-plugins:amd64
 Try to Re-Instate (1) nautilus-sendto:amd64
Investigating (1) nvidia-185-libvdpau [ amd64 ] < 270.41.06-0ubuntu1.2 > ( restricted/misc )
Broken nvidia-185-libvdpau:amd64 Depends on nvidia-current [ amd64 ] < 270.41.06-0ubuntu1.2 > ( restricted/misc )
  Considering nvidia-current:amd64 5 as a solution to nvidia-185-libvdpau:amd64 3
  Removing nvidia-185-libvdpau:amd64 rather than change nvidia-current:amd64
Investigating (1) padevchooser [ amd64 ] < 0.9.3-2ubuntu4 > ( sound )
Broken padevchooser:amd64 Depends on libpulse-browse0 [ amd64 ] < 1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1 > ( sound ) (>= 0.9.8)
  Considering libpulse-browse0:amd64 1 as a solution to padevchooser:amd64 3
  Added libpulse-browse0:amd64 to the remove list
  Fixing padevchooser:amd64 via keep of libpulse-browse0:amd64
Investigating (1) vlc-nox [ amd64 ] < 1.1.9-1ubuntu1.3 > ( video )
Broken vlc-nox:amd64 Depends on libmtp8 [ amd64 ] < 1.0.6-2 > ( libs ) (>= 0.3.1)
  Considering libmtp8:amd64 2 as a solution to vlc-nox:amd64 3
  Added libmtp8:amd64 to the remove list
  Fixing vlc-nox:amd64 via keep of libmtp8:amd64
Investigating (1) libmtp-common [ amd64 ] < none -> 1.1.0-3ubuntu1 > ( libs )
Broken libmtp-common:amd64 Breaks on libmtp8 [ amd64 ] < 1.0.6-2 > ( libs ) (<= 1.0.6-6)
  Considering libmtp8:amd64 2 as a solution to libmtp-common:amd64 3
  Added libmtp8:amd64 to the remove list
  Fixing libmtp-common:amd64 via remove of libmtp8:amd64
 Try to Re-Instate (1) compiz:amd64
Investigating (1) compiz [ amd64 ] < 1:0.9.4+bzr20110606-0ubuntu1~natty2 -> 1:0.9.6+bzr20110929-0ubuntu6.1 > ( x11 )
Broken compiz:amd64 Depends on compiz-plugins [ amd64 ] < 1:0.9.4+bzr20110606-0ubuntu1~natty2 -> 1:0.9.6+bzr20110929-0ubuntu6.1 > ( x11 ) (>= 1:0.9.4+bzr20110606-0ubuntu1~natty2)
  Considering compiz-plugins:amd64 0 as a solution to compiz:amd64 3
  Added compiz-plugins:amd64 to the remove list
Broken compiz:amd64 Depends on compiz-gnome [ amd64 ] < 1:0.9.4+bzr20110606-0ubuntu1~natty2 -> 1:0.9.6+bzr20110929-0ubuntu6.1 > ( x11 )
  Considering compiz-gnome:amd64 2 as a solution to compiz:amd64 3
  Added compiz-gnome:amd64 to the remove list
Broken compiz:amd64 Depends on compiz-kde [ amd64 ] < none > ( none )
Broken compiz:amd64 Depends on compiz-plugins-main [ amd64 ] < 0.9.4+bzr20110527-0ubuntu1~natty1 -> 1:0.9.6-0ubuntu4.2 > ( x11 ) (>= 0.9)
  Considering compiz-plugins-main:amd64 1 as a solution to compiz:amd64 3
  Added compiz-plugins-main:amd64 to the remove list
  Fixing compiz:amd64 via keep of compiz-plugins:amd64
  Fixing compiz:amd64 via keep of compiz-gnome:amd64
  Fixing compiz:amd64 via keep of compiz-plugins-main:amd64
Investigating (1) gnuplot-x11 [ amd64 ] < 4.4.2-0ubuntu1 > ( math )
Broken gnuplot-x11:amd64 Depends on libwxgtk2.8-0 [ amd64 ] < 2.8.11.0-0ubuntu8.1 > ( libs ) (>= 2.8.11.0)
  Considering libwxgtk2.8-0:amd64 9 as a solution to gnuplot-x11:amd64 2
  Removing gnuplot-x11:amd64 rather than change libwxgtk2.8-0:amd64
 Try to Re-Instate (1) compiz-gnome:amd64
Investigating (1) system-tools-backends [ amd64 ] < 2.10.1-2ubuntu1 > ( admin )
Broken system-tools-backends:amd64 Depends on libnet-dbus-perl [ amd64 ] < 0.33.6-2 > ( perl )
  Considering libnet-dbus-perl:amd64 1 as a solution to system-tools-backends:amd64 2
  Added libnet-dbus-perl:amd64 to the remove list
  Fixing system-tools-backends:amd64 via keep of libnet-dbus-perl:amd64
Investigating (1) nvidia-current-dev [ amd64 ] < 270.41.06-0ubuntu1.2 > ( restricted/misc )
Broken nvidia-current-dev:amd64 Depends on nvidia-current [ amd64 ] < 270.41.06-0ubuntu1.2 > ( restricted/misc ) (>= 270.41.06)
  Considering nvidia-current:amd64 5 as a solution to nvidia-current-dev:amd64 2
  Removing nvidia-current-dev:amd64 rather than change nvidia-current:amd64
Investigating (1) nvidia-185-kernel-source [ amd64 ] < 270.41.06-0ubuntu1.2 > ( restricted/misc )
Broken nvidia-185-kernel-source:amd64 Depends on nvidia-current [ amd64 ] < 270.41.06-0ubuntu1.2 > ( restricted/misc )
  Considering nvidia-current:amd64 5 as a solution to nvidia-185-kernel-source:amd64 1
  Removing nvidia-185-kernel-source:amd64 rather than change nvidia-current:amd64
Investigating (1) nvidia-173-dev [ amd64 ] < 173.14.30-0ubuntu1.2 > ( restricted/misc )
Broken nvidia-173-dev:amd64 Depends on nvidia-173 [ amd64 ] < 173.14.30-0ubuntu1.2 > ( restricted/misc ) (>= 173.14.30)
  Considering nvidia-173:amd64 4 as a solution to nvidia-173-dev:amd64 1
  Removing nvidia-173-dev:amd64 rather than change nvidia-173:amd64
Investigating (1) libnet-dbus-perl [ amd64 ] < 0.33.6-2 > ( perl )
Broken libnet-dbus-perl:amd64 Depends on perlapi-5.10.1 [ amd64 ] < none > ( none )
  Considering perl-base:amd64 5396 as a solution to libnet-dbus-perl:amd64 1
  Removing libnet-dbus-perl:amd64 rather than change perlapi-5.10.1:amd64
 Try to Re-Instate (1) compiz-plugins-main:amd64
Investigating (1) compiz-plugins-main [ amd64 ] < 0.9.4+bzr20110527-0ubuntu1~natty1 -> 1:0.9.6-0ubuntu4.2 > ( x11 )
Broken compiz-plugins-main:amd64 Depends on libglu1-mesa [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libglu1-mesa:amd64 121 as a solution to compiz-plugins-main:amd64 1
Broken compiz-plugins-main:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 121 as a solution to compiz-plugins-main:amd64 1
  Or group remove for compiz-plugins-main:amd64
Broken compiz-plugins-main:amd64 Depends on compiz-core-abiversion-20110322 [ amd64 ] < none > ( none )
  Considering compiz-core:amd64 15 as a solution to compiz-plugins-main:amd64 1
  Removing compiz-plugins-main:amd64 rather than change compiz-core-abiversion-20110322:amd64
Investigating (1) nvidia-glx-185-dev [ amd64 ] < 270.41.06-0ubuntu1.2 > ( restricted/misc )
Broken nvidia-glx-185-dev:amd64 Depends on nvidia-current-dev [ amd64 ] < 270.41.06-0ubuntu1.2 > ( restricted/misc )
  Considering nvidia-current-dev:amd64 2 as a solution to nvidia-glx-185-dev:amd64 1
  Removing nvidia-glx-185-dev:amd64 rather than change nvidia-current-dev:amd64
Investigating (1) libpulse-browse0 [ amd64 ] < 1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1 > ( sound )
Broken libpulse-browse0:amd64 Depends on libpulse0 [ amd64 ] < 1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1 -> 1:1.0-0ubuntu3.1 > ( libs ) (= 1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1)
  Considering libpulse0:amd64 133 as a solution to libpulse-browse0:amd64 1
  Removing libpulse-browse0:amd64 rather than change libpulse0:amd64
Investigating (1) nvidia-glx-185 [ amd64 ] < 270.41.06-0ubuntu1.2 > ( restricted/misc )
Broken nvidia-glx-185:amd64 Depends on nvidia-current [ amd64 ] < 270.41.06-0ubuntu1.2 > ( restricted/misc )
  Considering nvidia-current:amd64 5 as a solution to nvidia-glx-185:amd64 1
  Removing nvidia-glx-185:amd64 rather than change nvidia-current:amd64
 Try to Re-Instate (1) eog:amd64
Investigating (1) libboost-test-dev [ amd64 ] < 1.42.0.1ubuntu1 -> 1.46.1.1 > ( libdevel )
Broken libboost-test-dev:amd64 Depends on libboost-test1.46-dev [ amd64 ] < none -> 1.46.1-5ubuntu2 > ( libdevel )
  Considering libboost-test1.46-dev:amd64 0 as a solution to libboost-test-dev:amd64 0
  Holding Back libboost-test-dev:amd64 rather than change libboost-test1.46-dev:amd64
Investigating (1) libboost-serialization-dev [ amd64 ] < 1.42.0.1ubuntu1 -> 1.46.1.1 > ( libdevel )
Broken libboost-serialization-dev:amd64 Depends on libboost-serialization1.46-dev [ amd64 ] < none -> 1.46.1-5ubuntu2 > ( libdevel )
  Considering libboost-serialization1.46-dev:amd64 0 as a solution to libboost-serialization-dev:amd64 0
  Holding Back libboost-serialization-dev:amd64 rather than change libboost-serialization1.46-dev:amd64
 Try to Re-Instate (1) compiz-plugins:amd64
Investigating (1) compiz-plugins [ amd64 ] < 1:0.9.4+bzr20110606-0ubuntu1~natty2 -> 1:0.9.6+bzr20110929-0ubuntu6.1 > ( x11 )
Broken compiz-plugins:amd64 Depends on compiz-core [ amd64 ] < 1:0.9.4+bzr20110606-0ubuntu1~natty2 -> 1:0.9.6+bzr20110929-0ubuntu6.1 > ( x11 ) (= 1:0.9.4+bzr20110606-0ubuntu1~natty2)
  Considering compiz-core:amd64 15 as a solution to compiz-plugins:amd64 0
  Removing compiz-plugins:amd64 rather than change compiz-core:amd64
 Try to Re-Instate (1) libboost-dev:amd64
 Try to Re-Instate (1) libboost-iostreams-dev:amd64
Investigating (1) nvidia-180-libvdpau [ amd64 ] < 185.18.36-0ubuntu9 > ( restricted/misc )
Broken nvidia-180-libvdpau:amd64 Depends on nvidia-185-libvdpau [ amd64 ] < 270.41.06-0ubuntu1.2 > ( restricted/misc )
  Considering nvidia-185-libvdpau:amd64 3 as a solution to nvidia-180-libvdpau:amd64 -1
  Removing nvidia-180-libvdpau:amd64 rather than change nvidia-185-libvdpau:amd64
Investigating (1) nvidia-185-libvdpau-dev [ amd64 ] < 270.41.06-0ubuntu1.2 > ( restricted/misc )
Broken nvidia-185-libvdpau-dev:amd64 Depends on nvidia-current-dev [ amd64 ] < 270.41.06-0ubuntu1.2 > ( restricted/misc )
  Considering nvidia-current-dev:amd64 2 as a solution to nvidia-185-libvdpau-dev:amd64 -1
  Removing nvidia-185-libvdpau-dev:amd64 rather than change nvidia-current-dev:amd64
Investigating (1) nvidia-glx-173-dev [ amd64 ] < 173.14.30-0ubuntu1.2 > ( restricted/misc )
Broken nvidia-glx-173-dev:amd64 Depends on nvidia-173-dev [ amd64 ] < 173.14.30-0ubuntu1.2 > ( restricted/misc )
  Considering nvidia-173-dev:amd64 1 as a solution to nvidia-glx-173-dev:amd64 -1
  Removing nvidia-glx-173-dev:amd64 rather than change nvidia-173-dev:amd64
Investigating (1) nvidia-173-kernel-source [ amd64 ] < 173.14.30-0ubuntu1.2 > ( restricted/misc )
Broken nvidia-173-kernel-source:amd64 Depends on nvidia-173 [ amd64 ] < 173.14.30-0ubuntu1.2 > ( restricted/misc )
  Considering nvidia-173:amd64 4 as a solution to nvidia-173-kernel-source:amd64 -1
  Removing nvidia-173-kernel-source:amd64 rather than change nvidia-173:amd64
Investigating (1) nvidia-glx-173 [ amd64 ] < 173.14.30-0ubuntu1.2 > ( restricted/misc )
Broken nvidia-glx-173:amd64 Depends on nvidia-173 [ amd64 ] < 173.14.30-0ubuntu1.2 > ( restricted/misc )
  Considering nvidia-173:amd64 4 as a solution to nvidia-glx-173:amd64 -1
  Removing nvidia-glx-173:amd64 rather than change nvidia-173:amd64
Investigating (1) nvidia-glx-180 [ amd64 ] < 185.18.36-0ubuntu9 > ( restricted/misc )
Broken nvidia-glx-180:amd64 Depends on nvidia-glx-185 [ amd64 ] < 270.41.06-0ubuntu1.2 > ( restricted/misc )
  Considering nvidia-glx-185:amd64 1 as a solution to nvidia-glx-180:amd64 -1
  Removing nvidia-glx-180:amd64 rather than change nvidia-glx-185:amd64
Investigating (1) nvidia-180-libvdpau-dev [ amd64 ] < 185.18.36-0ubuntu9 > ( restricted/misc )
Broken nvidia-180-libvdpau-dev:amd64 Depends on nvidia-185-libvdpau [ amd64 ] < 270.41.06-0ubuntu1.2 > ( restricted/misc )
  Considering nvidia-185-libvdpau:amd64 3 as a solution to nvidia-180-libvdpau-dev:amd64 -1
  Removing nvidia-180-libvdpau-dev:amd64 rather than change nvidia-185-libvdpau:amd64
Investigating (1) nvidia-180-kernel-source [ amd64 ] < 185.18.36-0ubuntu9 > ( restricted/misc )
Broken nvidia-180-kernel-source:amd64 Depends on nvidia-185-kernel-source [ amd64 ] < 270.41.06-0ubuntu1.2 > ( restricted/misc )
  Considering nvidia-185-kernel-source:amd64 1 as a solution to nvidia-180-kernel-source:amd64 -1
  Removing nvidia-180-kernel-source:amd64 rather than change nvidia-185-kernel-source:amd64
Investigating (1) nvidia-glx-180-dev [ amd64 ] < 185.18.36-0ubuntu9 > ( restricted/misc )
Broken nvidia-glx-180-dev:amd64 Depends on nvidia-glx-185-dev [ amd64 ] < 270.41.06-0ubuntu1.2 > ( restricted/misc )
  Considering nvidia-glx-185-dev:amd64 1 as a solution to nvidia-glx-180-dev:amd64 -1
  Removing nvidia-glx-180-dev:amd64 rather than change nvidia-glx-185-dev:amd64
Investigating (2) libglib2.0-0 [ amd64 ] < 2.28.6-0ubuntu1 -> 2.30.0-0ubuntu4 > ( libs )
Broken libglib2.0-0:amd64 Breaks on gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.2-0ubuntu1 > ( gnome ) (< 1:3)
  Considering gnome-control-center:amd64 20 as a solution to libglib2.0-0:amd64 4044
  Upgrading gnome-control-center:amd64 due to Breaks field in libglib2.0-0:amd64
Investigating (2) libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
Broken libgl1-mesa-glx:amd64 Depends on libglapi-mesa [ amd64 ] < 7.11.0+git20110222.7aeb610f-0ubuntu0sarvatt~maverick > ( libs ) (= 7.11-0ubuntu3.2)
  Considering libglapi-mesa:amd64 57 as a solution to libgl1-mesa-glx:amd64 238
  Holding Back libgl1-mesa-glx:amd64 rather than change libglapi-mesa:amd64
Investigating (2) libgl1-mesa-dri [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
Broken libgl1-mesa-dri:amd64 Breaks on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs ) (< 7.10.3-0ubuntu1)
  Considering libgl1-mesa-glx:amd64 238 as a solution to libgl1-mesa-dri:amd64 105
  Removing libgl1-mesa-dri:amd64 rather than change libgl1-mesa-glx:amd64
Investigating (2) gnuplot [ amd64 ] < 4.4.2-0ubuntu1 > ( math )
Broken gnuplot:amd64 Depends on gnuplot-x11 [ amd64 ] < 4.4.2-0ubuntu1 > ( math ) (>= 4.4.2-0ubuntu1)
  Considering gnuplot-x11:amd64 2 as a solution to gnuplot:amd64 66
  Added gnuplot-x11:amd64 to the remove list
  Fixing gnuplot:amd64 via keep of gnuplot-x11:amd64
Investigating (2) gvfs [ amd64 ] < 1.8.0-0ubuntu4 -> 1.10.0-0ubuntu1.1 > ( libs )
Broken gvfs:amd64 Depends on x11-utils [ amd64 ] < 7.6+1 -> 7.6+3 > ( x11 )
  Considering x11-utils:amd64 49 as a solution to gvfs:amd64 62
  Added x11-utils:amd64 to the remove list
  Fixing gvfs:amd64 via keep of x11-utils:amd64
Investigating (2) gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.2-0ubuntu1 > ( gnome )
Broken gnome-control-center:amd64 Depends on libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.1-0ubuntu1.1 > ( libs ) (>= 3.1.2)
  Considering libgnome-desktop-3-2:amd64 36 as a solution to gnome-control-center:amd64 20
  Holding Back gnome-control-center:amd64 rather than change libgnome-desktop-3-2:amd64
 Try to Re-Instate (2) phonon:amd64
Re-Instated phonon:amd64 (9 vs 9)
Investigating (2) libedataserver1.2-13 [ amd64 ] < 2.30.3-2ubuntu2.1 > ( libs )
Broken libedataserver1.2-13:amd64 Depends on libnspr4-0d [ amd64 ] < 4.8.7-0ubuntu1 > ( libs ) (>= 4.7.3-0ubuntu1~)
  Considering libnspr4-0d:amd64 8 as a solution to libedataserver1.2-13:amd64 10
  Added libnspr4-0d:amd64 to the remove list
  Fixing libedataserver1.2-13:amd64 via keep of libnspr4-0d:amd64
Investigating (2) libnspr4-0d [ amd64 ] < 4.8.7-0ubuntu1 > ( libs )
Broken libnspr4-0d:amd64 Depends on libnspr4 [ amd64 ] < 4.8.7-0ubuntu1 -> 4.9.5-0ubuntu0.11.10.1 > ( libs ) (= 4.8.7-0ubuntu1)
  Considering libnspr4:amd64 121 as a solution to libnspr4-0d:amd64 10
  Removing libnspr4-0d:amd64 rather than change libnspr4:amd64
Investigating (2) padevchooser [ amd64 ] < 0.9.3-2ubuntu4 > ( sound )
Broken padevchooser:amd64 Depends on libpulse-browse0 [ amd64 ] < 1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1 > ( sound ) (>= 0.9.8)
  Considering libpulse-browse0:amd64 1 as a solution to padevchooser:amd64 3
  Added libpulse-browse0:amd64 to the remove list
  Fixing padevchooser:amd64 via keep of libpulse-browse0:amd64
Investigating (2) vlc-nox [ amd64 ] < 1.1.9-1ubuntu1.3 > ( video )
Broken vlc-nox:amd64 Depends on libmtp8 [ amd64 ] < 1.0.6-2 > ( libs ) (>= 0.3.1)
  Considering libmtp8:amd64 2 as a solution to vlc-nox:amd64 3
  Added libmtp8:amd64 to the remove list
  Fixing vlc-nox:amd64 via keep of libmtp8:amd64
Investigating (2) libmtp-common [ amd64 ] < none -> 1.1.0-3ubuntu1 > ( libs )
Broken libmtp-common:amd64 Breaks on libmtp8 [ amd64 ] < 1.0.6-2 > ( libs ) (<= 1.0.6-6)
  Considering libmtp8:amd64 3 as a solution to libmtp-common:amd64 3
  Holding Back libmtp-common:amd64 rather than change libmtp8:amd64
Investigating (2) compiz [ amd64 ] < 1:0.9.4+bzr20110606-0ubuntu1~natty2 -> 1:0.9.6+bzr20110929-0ubuntu6.1 > ( x11 )
Broken compiz:amd64 Depends on compiz-plugins [ amd64 ] < 1:0.9.4+bzr20110606-0ubuntu1~natty2 -> 1:0.9.6+bzr20110929-0ubuntu6.1 > ( x11 ) (>= 1:0.9.4+bzr20110606-0ubuntu1~natty2)
  Considering compiz-plugins:amd64 0 as a solution to compiz:amd64 3
  Added compiz-plugins:amd64 to the remove list
Broken compiz:amd64 Depends on compiz-plugins-main [ amd64 ] < 0.9.4+bzr20110527-0ubuntu1~natty1 -> 1:0.9.6-0ubuntu4.2 > ( x11 ) (>= 0.9)
  Considering compiz-plugins-main:amd64 1 as a solution to compiz:amd64 3
  Added compiz-plugins-main:amd64 to the remove list
  Fixing compiz:amd64 via keep of compiz-plugins:amd64
  Fixing compiz:amd64 via keep of compiz-plugins-main:amd64
Investigating (2) libmtp-runtime [ amd64 ] < none -> 1.1.0-3ubuntu1 > ( libs )
Broken libmtp-runtime:amd64 Depends on libmtp-common [ amd64 ] < none -> 1.1.0-3ubuntu1 > ( libs )
  Considering libmtp-common:amd64 3 as a solution to libmtp-runtime:amd64 2
  Holding Back libmtp-runtime:amd64 rather than change libmtp-common:amd64
Investigating (2) gnuplot-x11 [ amd64 ] < 4.4.2-0ubuntu1 > ( math )
Broken gnuplot-x11:amd64 Depends on libwxgtk2.8-0 [ amd64 ] < 2.8.11.0-0ubuntu8.1 > ( libs ) (>= 2.8.11.0)
  Considering libwxgtk2.8-0:amd64 9 as a solution to gnuplot-x11:amd64 66
  Added libwxgtk2.8-0:amd64 to the remove list
  Fixing gnuplot-x11:amd64 via keep of libwxgtk2.8-0:amd64
Investigating (2) system-tools-backends [ amd64 ] < 2.10.1-2ubuntu1 > ( admin )
Broken system-tools-backends:amd64 Depends on libnet-dbus-perl [ amd64 ] < 0.33.6-2 > ( perl )
  Considering libnet-dbus-perl:amd64 1 as a solution to system-tools-backends:amd64 2
  Added libnet-dbus-perl:amd64 to the remove list
  Fixing system-tools-backends:amd64 via keep of libnet-dbus-perl:amd64
Investigating (2) libnet-dbus-perl [ amd64 ] < 0.33.6-2 > ( perl )
Broken libnet-dbus-perl:amd64 Depends on perlapi-5.10.1 [ amd64 ] < none > ( none )
  Considering perl-base:amd64 5396 as a solution to libnet-dbus-perl:amd64 2
  Removing libnet-dbus-perl:amd64 rather than change perlapi-5.10.1:amd64
Investigating (2) compiz-plugins-main [ amd64 ] < 0.9.4+bzr20110527-0ubuntu1~natty1 -> 1:0.9.6-0ubuntu4.2 > ( x11 )
Broken compiz-plugins-main:amd64 Depends on libglu1-mesa [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libglu1-mesa:amd64 121 as a solution to compiz-plugins-main:amd64 3
Broken compiz-plugins-main:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 121 as a solution to compiz-plugins-main:amd64 3
  Or group remove for compiz-plugins-main:amd64
Broken compiz-plugins-main:amd64 Depends on compiz-core-abiversion-20110322 [ amd64 ] < none > ( none )
  Considering compiz-core:amd64 15 as a solution to compiz-plugins-main:amd64 3
  Removing compiz-plugins-main:amd64 rather than change compiz-core-abiversion-20110322:amd64
Investigating (2) libpulse-browse0 [ amd64 ] < 1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1 > ( sound )
Broken libpulse-browse0:amd64 Depends on libpulse0 [ amd64 ] < 1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1 -> 1:1.0-0ubuntu3.1 > ( libs ) (= 1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1)
  Considering libpulse0:amd64 133 as a solution to libpulse-browse0:amd64 3
  Removing libpulse-browse0:amd64 rather than change libpulse0:amd64
Investigating (2) libgl1-mesa-dri [ i386 ] < none -> 7.11-0ubuntu3.2 > ( libs )
Broken libgl1-mesa-dri:i386 Breaks on libgl1-mesa-glx [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs ) (< 7.10.3-0ubuntu1)
  Considering libgl1-mesa-glx:amd64 238 as a solution to libgl1-mesa-dri:i386 0
  Holding Back libgl1-mesa-dri:i386 rather than change libgl1-mesa-glx:amd64
 Try to Re-Instate (2) libboost-test-dev:amd64
 Try to Re-Instate (2) libboost-serialization-dev:amd64
Investigating (2) compiz-plugins [ amd64 ] < 1:0.9.4+bzr20110606-0ubuntu1~natty2 -> 1:0.9.6+bzr20110929-0ubuntu6.1 > ( x11 )
Broken compiz-plugins:amd64 Depends on compiz-core [ amd64 ] < 1:0.9.4+bzr20110606-0ubuntu1~natty2 -> 1:0.9.6+bzr20110929-0ubuntu6.1 > ( x11 ) (= 1:0.9.4+bzr20110606-0ubuntu1~natty2)
  Considering compiz-core:amd64 15 as a solution to compiz-plugins:amd64 3
  Removing compiz-plugins:amd64 rather than change compiz-core:amd64
Investigating (3) libglib2.0-0 [ amd64 ] < 2.28.6-0ubuntu1 -> 2.30.0-0ubuntu4 > ( libs )
Broken libglib2.0-0:amd64 Breaks on gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.2-0ubuntu1 > ( gnome ) (< 1:3)
  Considering gnome-control-center:amd64 20 as a solution to libglib2.0-0:amd64 4044
  Upgrading gnome-control-center:amd64 due to Breaks field in libglib2.0-0:amd64
 Try to Re-Instate (3) libgl1-mesa-glx:amd64
Investigating (3) gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.2-0ubuntu1 > ( gnome )
Broken gnome-control-center:amd64 Depends on libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.1-0ubuntu1.1 > ( libs ) (>= 3.1.2)
  Considering libgnome-desktop-3-2:amd64 36 as a solution to gnome-control-center:amd64 20
  Holding Back gnome-control-center:amd64 rather than change libgnome-desktop-3-2:amd64
Investigating (3) libedataserver1.2-13 [ amd64 ] < 2.30.3-2ubuntu2.1 > ( libs )
Broken libedataserver1.2-13:amd64 Depends on libnspr4-0d [ amd64 ] < 4.8.7-0ubuntu1 > ( libs ) (>= 4.7.3-0ubuntu1~)
  Considering libnspr4-0d:amd64 121 as a solution to libedataserver1.2-13:amd64 10
  Removing libedataserver1.2-13:amd64 rather than change libnspr4-0d:amd64
Investigating (3) libwxgtk2.8-0 [ amd64 ] < 2.8.11.0-0ubuntu8.1 > ( libs )
Broken libwxgtk2.8-0:amd64 Depends on libglu1-mesa [ amd64 ] < 7.10.2-0ubuntu2.1 -> 7.11-0ubuntu3.2 > ( libs )
  Considering libglu1-mesa:amd64 121 as a solution to libwxgtk2.8-0:amd64 66
Broken libwxgtk2.8-0:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 121 as a solution to libwxgtk2.8-0:amd64 66
  Or group remove for libwxgtk2.8-0:amd64
Investigating (3) libmtp9 [ amd64 ] < none -> 1.1.0-3ubuntu1 > ( libs )
Broken libmtp9:amd64 Depends on libmtp-common [ amd64 ] < none -> 1.1.0-3ubuntu1 > ( libs )
  Considering libmtp-common:amd64 3 as a solution to libmtp9:amd64 7
  Holding Back libmtp9:amd64 rather than change libmtp-common:amd64
Investigating (3) padevchooser [ amd64 ] < 0.9.3-2ubuntu4 > ( sound )
Broken padevchooser:amd64 Depends on libpulse-browse0 [ amd64 ] < 1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1 > ( sound ) (>= 0.9.8)
  Considering libpulse-browse0:amd64 133 as a solution to padevchooser:amd64 3
  Removing padevchooser:amd64 rather than change libpulse-browse0:amd64
Investigating (3) compiz [ amd64 ] < 1:0.9.4+bzr20110606-0ubuntu1~natty2 -> 1:0.9.6+bzr20110929-0ubuntu6.1 > ( x11 )
Broken compiz:amd64 Depends on compiz-plugins [ amd64 ] < 1:0.9.4+bzr20110606-0ubuntu1~natty2 -> 1:0.9.6+bzr20110929-0ubuntu6.1 > ( x11 ) (>= 1:0.9.4+bzr20110606-0ubuntu1~natty2)
  Considering compiz-plugins:amd64 15 as a solution to compiz:amd64 3
  Removing compiz:amd64 rather than change compiz-plugins:amd64
Investigating (3) rhythmbox-plugins [ amd64 ] < 0.13.3-0ubuntu6 -> 2.90.1~20110908-0ubuntu1.4 > ( gnome )
Broken rhythmbox-plugins:amd64 Depends on libmtp9 [ amd64 ] < none -> 1.1.0-3ubuntu1 > ( libs ) (>= 1.1.0)
  Considering libmtp9:amd64 7 as a solution to rhythmbox-plugins:amd64 3
  Removing rhythmbox-plugins:amd64 rather than change libmtp9:amd64
Investigating (3) gnuplot-x11 [ amd64 ] < 4.4.2-0ubuntu1 > ( math )
Broken gnuplot-x11:amd64 Depends on libwxgtk2.8-0 [ amd64 ] < 2.8.11.0-0ubuntu8.1 > ( libs ) (>= 2.8.11.0)
  Considering libwxgtk2.8-0:amd64 66 as a solution to gnuplot-x11:amd64 66
  Removing gnuplot-x11:amd64 rather than change libwxgtk2.8-0:amd64
Investigating (3) compiz-gnome [ amd64 ] < 1:0.9.4+bzr20110606-0ubuntu1~natty2 -> 1:0.9.6+bzr20110929-0ubuntu6.1 > ( x11 )
Broken compiz-gnome:amd64 Depends on compiz-plugins [ amd64 ] < 1:0.9.4+bzr20110606-0ubuntu1~natty2 -> 1:0.9.6+bzr20110929-0ubuntu6.1 > ( x11 ) (= 1:0.9.4+bzr20110606-0ubuntu1~natty2)
  Considering compiz-plugins:amd64 15 as a solution to compiz-gnome:amd64 2
  Removing compiz-gnome:amd64 rather than change compiz-plugins:amd64
Investigating (3) system-tools-backends [ amd64 ] < 2.10.1-2ubuntu1 > ( admin )
Broken system-tools-backends:amd64 Depends on libnet-dbus-perl [ amd64 ] < 0.33.6-2 > ( perl )
  Considering libnet-dbus-perl:amd64 5396 as a solution to system-tools-backends:amd64 2
  Removing system-tools-backends:amd64 rather than change libnet-dbus-perl:amd64
Investigating (3) libecal1.2-7 [ amd64 ] < 2.30.3-2ubuntu2.1 > ( libs )
Broken libecal1.2-7:amd64 Depends on libedataserver1.2-13 [ amd64 ] < 2.30.3-2ubuntu2.1 > ( libs ) (>= 2.30.3)
  Considering libedataserver1.2-13:amd64 121 as a solution to libecal1.2-7:amd64 1
  Removing libecal1.2-7:amd64 rather than change libedataserver1.2-13:amd64
Investigating (3) liboobs-1-5 [ amd64 ] < 2.32.0-0ubuntu1 > ( libs )
Broken liboobs-1-5:amd64 Depends on system-tools-backends [ amd64 ] < 2.10.1-2ubuntu1 > ( admin ) (>= 2.9.2)
  Considering system-tools-backends:amd64 5396 as a solution to liboobs-1-5:amd64 1
  Removing liboobs-1-5:amd64 rather than change system-tools-backends:amd64
Investigating (3) libedata-cal1.2-7 [ amd64 ] < 2.30.3-2ubuntu2.1 > ( libs )
Broken libedata-cal1.2-7:amd64 Depends on libecal1.2-7 [ amd64 ] < 2.30.3-2ubuntu2.1 > ( libs ) (>= 2.30.3)
  Considering libecal1.2-7:amd64 121 as a solution to libedata-cal1.2-7:amd64 -1
  Removing libedata-cal1.2-7:amd64 rather than change libecal1.2-7:amd64
Investigating (3) gnome-system-tools [ amd64 ] < 2.32.0-0ubuntu7 > ( gnome )
Broken gnome-system-tools:amd64 Depends on liboobs-1-5 [ amd64 ] < 2.32.0-0ubuntu1 > ( libs ) (>= 2.31.91)
  Considering liboobs-1-5:amd64 5396 as a solution to gnome-system-tools:amd64 -1
  Removing gnome-system-tools:amd64 rather than change liboobs-1-5:amd64
Investigating (4) libglib2.0-0 [ amd64 ] < 2.28.6-0ubuntu1 -> 2.30.0-0ubuntu4 > ( libs )
Broken libglib2.0-0:amd64 Breaks on gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.2-0ubuntu1 > ( gnome ) (< 1:3)
  Considering gnome-control-center:amd64 20 as a solution to libglib2.0-0:amd64 4044
  Upgrading gnome-control-center:amd64 due to Breaks field in libglib2.0-0:amd64
Investigating (4) gnuplot [ amd64 ] < 4.4.2-0ubuntu1 > ( math )
Broken gnuplot:amd64 Depends on gnuplot-x11 [ amd64 ] < 4.4.2-0ubuntu1 > ( math ) (>= 4.4.2-0ubuntu1)
  Considering gnuplot-x11:amd64 66 as a solution to gnuplot:amd64 66
  Removing gnuplot:amd64 rather than change gnuplot-x11:amd64
Investigating (4) gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.2-0ubuntu1 > ( gnome )
Broken gnome-control-center:amd64 Depends on libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.1-0ubuntu1.1 > ( libs ) (>= 3.1.2)
  Considering libgnome-desktop-3-2:amd64 36 as a solution to gnome-control-center:amd64 20
  Holding Back gnome-control-center:amd64 rather than change libgnome-desktop-3-2:amd64
Investigating (4) banshee [ amd64 ] < 2.0.1-1ubuntu1~natty2 -> 2.2.1-1ubuntu3 > ( sound )
Broken banshee:amd64 Depends on libmtp9 [ amd64 ] < none -> 1.1.0-3ubuntu1 > ( libs )
  Considering libmtp9:amd64 7 as a solution to banshee:amd64 8
  Holding Back banshee:amd64 rather than change libmtp9:amd64
Investigating (4) banshee-extension-soundmenu [ amd64 ] < 2.0.1-1ubuntu1~natty2 -> 2.2.1-1ubuntu3 > ( gnome )
Broken banshee-extension-soundmenu:amd64 Depends on banshee [ amd64 ] < 2.0.1-1ubuntu1~natty2 -> 2.2.1-1ubuntu3 > ( sound ) (>= 2.2.1)
  Considering banshee:amd64 8 as a solution to banshee-extension-soundmenu:amd64 5
  Holding Back banshee-extension-soundmenu:amd64 rather than change banshee:amd64
Investigating (4) maxima [ amd64 ] < 5.22.1-9 > ( math )
Broken maxima:amd64 Depends on gnuplot-x11 [ amd64 ] < 4.4.2-0ubuntu1 > ( math )
  Considering gnuplot-x11:amd64 66 as a solution to maxima:amd64 2
  Removing maxima:amd64 rather than change gnuplot-x11:amd64
Investigating (4) maxima-share [ amd64 ] < 5.22.1-9 > ( math )
Broken maxima-share:amd64 Depends on maxima [ amd64 ] < 5.22.1-9 > ( math ) (>= 5.22.1-9)
  Considering maxima:amd64 66 as a solution to maxima-share:amd64 1
  Removing maxima-share:amd64 rather than change maxima:amd64
Investigating (4) banshee-extension-ubuntuonemusicstore [ amd64 ] < 2.0.1-1ubuntu1~natty2 -> 2.2.1-1ubuntu3 > ( gnome )
Broken banshee-extension-ubuntuonemusicstore:amd64 Depends on banshee [ amd64 ] < 2.0.1-1ubuntu1~natty2 -> 2.2.1-1ubuntu3 > ( sound ) (>= 2.2.1)
  Considering banshee:amd64 8 as a solution to banshee-extension-ubuntuonemusicstore:amd64 1
  Holding Back banshee-extension-ubuntuonemusicstore:amd64 rather than change banshee:amd64
Investigating (4) maxima-emacs [ amd64 ] < 5.22.1-9 > ( math )
Broken maxima-emacs:amd64 Depends on maxima [ amd64 ] < 5.22.1-9 > ( math ) (>= 5.22.1-9)
  Considering maxima:amd64 66 as a solution to maxima-emacs:amd64 -1
  Removing maxima-emacs:amd64 rather than change maxima:amd64
Investigating (5) libglib2.0-0 [ amd64 ] < 2.28.6-0ubuntu1 -> 2.30.0-0ubuntu4 > ( libs )
Broken libglib2.0-0:amd64 Breaks on gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.2-0ubuntu1 > ( gnome ) (< 1:3)
  Considering gnome-control-center:amd64 20 as a solution to libglib2.0-0:amd64 4044
  Upgrading gnome-control-center:amd64 due to Breaks field in libglib2.0-0:amd64
Investigating (5) gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.2-0ubuntu1 > ( gnome )
Broken gnome-control-center:amd64 Depends on libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.1-0ubuntu1.1 > ( libs ) (>= 3.1.2)
  Considering libgnome-desktop-3-2:amd64 36 as a solution to gnome-control-center:amd64 20
  Holding Back gnome-control-center:amd64 rather than change libgnome-desktop-3-2:amd64
 Try to Re-Instate (5) banshee:amd64
 Try to Re-Instate (5) banshee-extension-soundmenu:amd64
 Try to Re-Instate (5) banshee-extension-ubuntuonemusicstore:amd64
Investigating (6) libglib2.0-0 [ amd64 ] < 2.28.6-0ubuntu1 -> 2.30.0-0ubuntu4 > ( libs )
Broken libglib2.0-0:amd64 Breaks on gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.2-0ubuntu1 > ( gnome ) (< 1:3)
  Considering gnome-control-center:amd64 20 as a solution to libglib2.0-0:amd64 4044
  Upgrading gnome-control-center:amd64 due to Breaks field in libglib2.0-0:amd64
Investigating (6) gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.2-0ubuntu1 > ( gnome )
Broken gnome-control-center:amd64 Depends on libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.1-0ubuntu1.1 > ( libs ) (>= 3.1.2)
  Considering libgnome-desktop-3-2:amd64 36 as a solution to gnome-control-center:amd64 20
  Holding Back gnome-control-center:amd64 rather than change libgnome-desktop-3-2:amd64
Investigating (7) libglib2.0-0 [ amd64 ] < 2.28.6-0ubuntu1 -> 2.30.0-0ubuntu4 > ( libs )
Broken libglib2.0-0:amd64 Breaks on gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.2-0ubuntu1 > ( gnome ) (< 1:3)
  Considering gnome-control-center:amd64 20 as a solution to libglib2.0-0:amd64 4044
  Upgrading gnome-control-center:amd64 due to Breaks field in libglib2.0-0:amd64
Investigating (7) gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.2-0ubuntu1 > ( gnome )
Broken gnome-control-center:amd64 Depends on libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.1-0ubuntu1.1 > ( libs ) (>= 3.1.2)
  Considering libgnome-desktop-3-2:amd64 36 as a solution to gnome-control-center:amd64 20
  Holding Back gnome-control-center:amd64 rather than change libgnome-desktop-3-2:amd64
Investigating (8) libglib2.0-0 [ amd64 ] < 2.28.6-0ubuntu1 -> 2.30.0-0ubuntu4 > ( libs )
Broken libglib2.0-0:amd64 Breaks on gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.2-0ubuntu1 > ( gnome ) (< 1:3)
  Considering gnome-control-center:amd64 20 as a solution to libglib2.0-0:amd64 4044
  Upgrading gnome-control-center:amd64 due to Breaks field in libglib2.0-0:amd64
Investigating (8) gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.2-0ubuntu1 > ( gnome )
Broken gnome-control-center:amd64 Depends on libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.1-0ubuntu1.1 > ( libs ) (>= 3.1.2)
  Considering libgnome-desktop-3-2:amd64 36 as a solution to gnome-control-center:amd64 20
  Holding Back gnome-control-center:amd64 rather than change libgnome-desktop-3-2:amd64
Investigating (9) libglib2.0-0 [ amd64 ] < 2.28.6-0ubuntu1 -> 2.30.0-0ubuntu4 > ( libs )
Broken libglib2.0-0:amd64 Breaks on gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.2-0ubuntu1 > ( gnome ) (< 1:3)
  Considering gnome-control-center:amd64 20 as a solution to libglib2.0-0:amd64 4044
  Upgrading gnome-control-center:amd64 due to Breaks field in libglib2.0-0:amd64
Investigating (9) gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.2-0ubuntu1 > ( gnome )
Broken gnome-control-center:amd64 Depends on libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.1-0ubuntu1.1 > ( libs ) (>= 3.1.2)
  Considering libgnome-desktop-3-2:amd64 36 as a solution to gnome-control-center:amd64 20
  Holding Back gnome-control-center:amd64 rather than change libgnome-desktop-3-2:amd64
Done
Log time: 2013-04-03 23:59:36.521098

```
These logs don't even say why the upgrade is failing. Is there no other file that shows preciely where the problem actually is?

---

### Post by ObsessiveMathsFreak on 2013-04-03
Is there no way to actually upgrade 11.04 anymore? Is this a dead distribution?

---

### Post by oldos2er on 2013-04-04
Old thread closed, if you have questions please start a new thread.

11.04 reached its end of life last October.

---

