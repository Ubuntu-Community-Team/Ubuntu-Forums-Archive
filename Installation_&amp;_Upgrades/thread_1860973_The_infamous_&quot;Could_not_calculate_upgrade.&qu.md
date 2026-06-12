---
title: "The infamous &quot;Could not calculate upgrade.&quot;"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by SoylentSteak on 2011-10-15
I removed all the repositories that weren't Canonical, but I still have no luck. At first, I got a couple of messages about Nvidia x.org packages being held back, but they went away after I disabled repositories. Could that perhaps still be the problem? Also, Is there a command I can use to find all currently installed unofficial packages?

---

### Post by SoylentSteak on 2011-10-16
Bump.

---

### Post by Old_Grey_Wolf on 2011-10-16
Enter these commands in the terminal and post the output. We need to see the errors so we can determine how to help you.
```
sudo apt-get update
``````
sudo apt-get dist-upgrade
```

---

### Post by SoylentSteak on 2011-10-16
```
chris@chris-desktop:~$ sudo apt-get update
[sudo] password for chris: 
Ign http://archive.ubuntu.com natty InRelease
Ign http://archive.ubuntu.com natty-updates InRelease
Ign http://archive.ubuntu.com natty-security InRelease
Hit http://archive.ubuntu.com natty Release.gpg
Hit http://archive.ubuntu.com natty-updates Release.gpg
Hit http://archive.ubuntu.com natty-security Release.gpg
Hit http://archive.ubuntu.com natty Release
Hit http://archive.ubuntu.com natty-updates Release
Hit http://archive.ubuntu.com natty-security Release
Hit http://archive.ubuntu.com natty/restricted Sources
Hit http://archive.ubuntu.com natty/main Sources
Hit http://archive.ubuntu.com natty/multiverse Sources
Hit http://archive.ubuntu.com natty/universe Sources
Hit http://archive.ubuntu.com natty/main amd64 Packages
Hit http://archive.ubuntu.com natty/restricted amd64 Packages
Hit http://archive.ubuntu.com natty/universe amd64 Packages
Hit http://archive.ubuntu.com natty/multiverse amd64 Packages
Ign http://archive.ubuntu.com natty/main TranslationIndex
Ign http://archive.ubuntu.com natty/multiverse TranslationIndex
Ign http://archive.ubuntu.com natty/restricted TranslationIndex
Ign http://archive.ubuntu.com natty/universe TranslationIndex
Hit http://archive.ubuntu.com natty-updates/restricted Sources
Hit http://archive.ubuntu.com natty-updates/main Sources
Hit http://archive.ubuntu.com natty-updates/multiverse Sources
Hit http://archive.ubuntu.com natty-updates/universe Sources
Hit http://archive.ubuntu.com natty-updates/main amd64 Packages
Hit http://archive.ubuntu.com natty-updates/restricted amd64 Packages
Hit http://archive.ubuntu.com natty-updates/universe amd64 Packages
Hit http://archive.ubuntu.com natty-updates/multiverse amd64 Packages
Ign http://archive.ubuntu.com natty-updates/main TranslationIndex
Ign http://archive.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://archive.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://archive.ubuntu.com natty-updates/universe TranslationIndex
Hit http://archive.ubuntu.com natty-security/restricted Sources
Hit http://archive.ubuntu.com natty-security/main Sources
Hit http://archive.ubuntu.com natty-security/multiverse Sources
Hit http://archive.ubuntu.com natty-security/universe Sources
Hit http://archive.ubuntu.com natty-security/main amd64 Packages
Hit http://archive.ubuntu.com natty-security/restricted amd64 Packages
Hit http://archive.ubuntu.com natty-security/universe amd64 Packages
Hit http://archive.ubuntu.com natty-security/multiverse amd64 Packages
Ign http://archive.ubuntu.com natty-security/main TranslationIndex
Ign http://archive.ubuntu.com natty-security/multiverse TranslationIndex
Ign http://archive.ubuntu.com natty-security/restricted TranslationIndex
Ign http://archive.ubuntu.com natty-security/universe TranslationIndex
Ign http://archive.ubuntu.com natty/main Translation-en_US
Ign http://archive.ubuntu.com natty/main Translation-en
Ign http://archive.ubuntu.com natty/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty/multiverse Translation-en
Ign http://archive.ubuntu.com natty/restricted Translation-en_US
Ign http://archive.ubuntu.com natty/restricted Translation-en
Ign http://archive.ubuntu.com natty/universe Translation-en_US
Ign http://archive.ubuntu.com natty/universe Translation-en
Ign http://archive.ubuntu.com natty-updates/main Translation-en_US
Ign http://archive.ubuntu.com natty-updates/main Translation-en
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://archive.ubuntu.com natty-updates/universe Translation-en_US
Ign http://archive.ubuntu.com natty-updates/universe Translation-en
Ign http://archive.ubuntu.com natty-security/main Translation-en_US
Ign http://archive.ubuntu.com natty-security/main Translation-en
Ign http://archive.ubuntu.com natty-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty-security/multiverse Translation-en
Ign http://archive.ubuntu.com natty-security/restricted Translation-en_US
Ign http://archive.ubuntu.com natty-security/restricted Translation-en
Ign http://archive.ubuntu.com natty-security/universe Translation-en_US
Ign http://archive.ubuntu.com natty-security/universe Translation-en
Reading package lists... Done
chris@chris-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
chris@chris-desktop:~$ 

```

Nothing jumps out at me....

---

### Post by Old_Grey_Wolf on 2011-10-16
That looks like a successful update. You may want to enable some of the repositories that you where having problems with and try the commands again.

---

### Post by SoylentSteak on 2011-10-16
Just so there's no confusion, I was trying to upgrade to 11.10. I'm going to try the repositories again, but I think the problem may be unofficial packages. The thing is, I don't remember all the stuff I've installed since upgrading to 11.04, and I don't know how to find what they may be. Is there a command or script to pinpoint them?

---

### Post by Old_Grey_Wolf on 2011-10-17
to get a list of all installed packages ```
dpkg -l
```

---

### Post by Old_Grey_Wolf on 2011-10-17
you can upgrade to 11.10 using ```
sudo do-release-upgrade
```
if it can't upgrade, hopefully it will give you errors to explain why

---

### Post by SoylentSteak on 2011-10-17
```
Could not calculate the upgrade 

An unresolvable problem occurred while calculating the upgrade: 
E:Error, pkgProblemResolver::Resolve generated breaks, this may be 
caused by held packages. 

This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 

If none of this applies, then please report this bug using the 
command 'ubuntu-bug update-manager' in a terminal. 

```

---

### Post by SoylentSteak on 2011-10-17
Here's the log:

```
Log time: 2011-10-17 18:34:19.111532
Log time: 2011-10-17 18:34:30.416544
Log time: 2011-10-17 18:34:57.342433
  Installing kde-runtime as Depends of kubuntu-debug-installer
    Installing kde-runtime-data as Depends of kde-runtime
  Installing libmono-cairo4.0-cil as Depends of f-spot
    Installing libmono-corlib4.0-cil as Depends of libmono-cairo4.0-cil
      Installing libmono-i18n-west4.0-cil as Recommends of libmono-corlib4.0-cil
        Installing libmono-i18n4.0-cil as Depends of libmono-i18n-west4.0-cil
  Installing libmono-posix4.0-cil as Depends of f-spot
    Installing libmono-system4.0-cil as Depends of libmono-posix4.0-cil
      Installing libmono-security4.0-cil as Depends of libmono-system4.0-cil
      Installing libmono-system-configuration4.0-cil as Depends of libmono-system4.0-cil
        Installing libmono-system-security4.0-cil as Depends of libmono-system-configuration4.0-cil
          Installing libmono-system-xml4.0-cil as Depends of libmono-system-security4.0-cil
  Installing libmono-sharpzip4.84-cil as Depends of f-spot
  Installing libmono-simd4.0-cil as Depends of f-spot
    Installing libmono-system-core4.0-cil as Depends of libmono-simd4.0-cil
  Installing libmono-system-web4.0-cil as Depends of f-spot
    Installing libmono-sqlite4.0-cil as Depends of libmono-system-web4.0-cil
      Installing libmono-system-data4.0-cil as Depends of libmono-sqlite4.0-cil
        Installing libmono-data-tds4.0-cil as Depends of libmono-system-data4.0-cil
        Installing libmono-system-enterpriseservices4.0-cil as Depends of libmono-system-data4.0-cil
          Installing libmono-system-transactions4.0-cil as Depends of libmono-system-enterpriseservices4.0-cil
    Installing libmono-system-drawing4.0-cil as Depends of libmono-system-web4.0-cil
    Installing libmono-system-web-applicationservices4.0-cil as Depends of libmono-system-web4.0-cil
    Installing libmono-system-web-services4.0-cil as Depends of libmono-system-web4.0-cil
    Installing libmono-web4.0-cil as Depends of libmono-system-web4.0-cil
  Installing libmlt4 as Depends of melt
    Installing libavcodec53 as Depends of libmlt4
      Installing libavutil51 as Depends of libavcodec53
    Installing libavdevice53 as Depends of libmlt4
      Installing libavformat53 as Depends of libavdevice53
    Installing libquicktime2 as Depends of libmlt4
      Installing libjpeg8 as Depends of libquicktime2
      Installing libswscale2 as Depends of libquicktime2
      Installing libx264-116 as Depends of libquicktime2
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
  Installing libecal1.2-10 as Depends of python-evolution
  Installing libboost-signals1.46.1 as Depends of ekiga
  Installing libopal3.10.2 as Depends of ekiga
    Installing libcapi20-3 as Depends of libopal3.10.2
    Installing libpt2.10.2 as Depends of libopal3.10.2
      Installing libssl1.0.0 as Depends of libpt2.10.2
    Installing libspandsp2 as Depends of libopal3.10.2
  Installing libcanberra-gtk3-0 as Depends of libevolution
    Installing libcanberra-gtk3-module as Recommends of libcanberra-gtk3-0
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
  Installing libkdcraw20 as Depends of kipi-plugins
    Installing libkdcraw-data as Depends of libkdcraw20
  Installing libkexiv2-10 as Depends of kipi-plugins
    Installing libkexiv2-data as Depends of libkexiv2-10
  Installing libkgeomap1 as Depends of kipi-plugins
    Installing libmarblewidget12 as Depends of libkgeomap1
    Installing libkgeomap-data as Depends of libkgeomap1
  Installing libkvkontakte1 as Depends of kipi-plugins
    Installing libkvkontakte-data as Depends of libkvkontakte1
  Installing libdb5.1 as Depends of iproute
  Installing libksane-data as Depends of libksane0
  Installing libgmp10 as Depends of libmpfr4
  Installing libgnome-media-profiles-3.0-0 as Depends of gnome-media
  Installing gstreamer0.10-gconf as Depends of gnome-media
  Installing libprotobuf7 as Depends of libcompizconfig0
  Installing libappindicator3-1 as Depends of update-notifier
  Installing thunderbird-locale-en as Depends of thunderbird-locale-en-gb
  Installing ubuntuone-installer as Depends of ubuntuone-control-panel-gtk
  Installing libslv2-9 as Depends of gstreamer0.10-plugins-bad
    Installing libraptor2-0 as Depends of libslv2-9
      Installing libyajl1 as Depends of libraptor2-0
  Installing libgvnc-1.0-0 as Depends of libgtk-vnc-1.0-0
  Installing lib32tinfo5 as Depends of lib32ncurses5
  Installing nspluginviewer as Depends of nspluginwrapper
    Installing libc6 as Depends of nspluginviewer
      Installing libgcc1 as Depends of libc6
        Installing gcc-4.6-base as Depends of libgcc1
    Installing libglib2.0-0 as Depends of nspluginviewer
      Installing libffi6 as Depends of libglib2.0-0
      Installing libpcre3 as Depends of libglib2.0-0
      Installing libselinux1 as Depends of libglib2.0-0
      Installing zlib1g as Depends of libglib2.0-0
    Installing libgtk2.0-0 as Depends of nspluginviewer
      Installing libatk1.0-0 as Depends of libgtk2.0-0
      Installing libcairo2 as Depends of libgtk2.0-0
        Installing libfontconfig1 as Depends of libcairo2
          Installing libexpat1 as Depends of libfontconfig1
          Installing libfreetype6 as Depends of libfontconfig1
        Installing libpixman-1-0 as Depends of libcairo2
        Installing libpng12-0 as Depends of libcairo2
        Installing libx11-6 as Depends of libcairo2
          Installing libxcb1 as Depends of libx11-6
            Installing libxau6 as Depends of libxcb1
            Installing libxdmcp6 as Depends of libxcb1
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
        Installing libxfixes3 as Depends of libxcursor1
      Installing libxdamage1 as Depends of libgtk2.0-0
      Installing libxext6 as Depends of libgtk2.0-0
      Installing libxi6 as Depends of libgtk2.0-0
      Installing libxinerama1 as Depends of libgtk2.0-0
      Installing libxrandr2 as Depends of libgtk2.0-0
    Installing libxt6 as Depends of nspluginviewer
      Installing libice6 as Depends of libxt6
      Installing libsm6 as Depends of libxt6
        Installing libuuid1 as Depends of libsm6
  Installing libpodofo0.9.0 as Depends of calibre-bin
  Installing libgucharmap-2-90-7 as Depends of gnome-applets
  Installing libgweather-3-0 as Depends of gnome-applets
  Installing libpanel-applet-4-0 as Depends of gnome-applets
  Installing gir1.2-panelapplet-4.0 as Depends of gnome-applets
  new important dependency: gir1.2-unity-4.0
  Installing gir1.2-unity-4.0 as Recommends of ubuntuone-client
  Installing libnm-glib4 as Depends of network-manager-gnome
    Installing libnm-util2 as Depends of libnm-glib4
  Installing libnm-gtk0 as Depends of network-manager-gnome
    Installing libnm-gtk-common as Depends of libnm-gtk0
  Installing librasqal3 as Depends of librdf0
    Installing libmhash2 as Depends of librasqal3
  Installing libyaml-tiny-perl as Depends of doc-base
  Installing zenity-common as Depends of zenity
  Installing libkipi-data as Depends of libkipi8
  Installing libgdata13 as Depends of totem-plugins
    Installing liboauth0 as Depends of libgdata13
  Installing libtotem0 as Depends of totem-plugins
    Installing libpeas-1.0-0 as Depends of libtotem0
      Installing libpeas-common as Depends of libpeas-1.0-0
  Installing gir1.2-totem-1.0 as Depends of totem-plugins
    Installing gir1.2-totem-plparser-1.0 as Depends of gir1.2-totem-1.0
  Installing gir1.2-peas-1.0 as Depends of totem-plugins
  Installing gir1.2-vte-2.90 as Depends of gdebi
    Installing libvte-2.90-9 as Depends of gir1.2-vte-2.90
  Installing lib32ffi6 as Depends of ia32-libs
  new important dependency: ia32-libs-multiarch
  Installing ia32-libs-multiarch as Recommends of ia32-libs
    Installing libqtcore4 as Depends of ia32-libs-multiarch
      Installing libstdc++6 as Depends of libqtcore4
    Installing libqtgui4 as Depends of ia32-libs-multiarch
      Installing libaudio2 as Depends of libqtgui4
      Installing libmng1 as Depends of libqtgui4
        Installing liblcms1 as Depends of libmng1
      Installing libqt4-declarative as Depends of libqtgui4
        Installing libqt4-network as Depends of libqt4-declarative
          Installing libqt4-dbus as Depends of libqt4-network
            Installing libqt4-xml as Depends of libqt4-dbus
            Installing qdbus as Depends of libqt4-dbus
        Installing libqt4-script as Depends of libqt4-declarative
        Installing libqt4-sql as Depends of libqt4-declarative
          Installing libqt4-sql-mysql as Recommends of libqt4-sql
            Installing libmysqlclient16 as Depends of libqt4-sql-mysql
        Installing libqt4-xmlpatterns as Depends of libqt4-declarative
    Installing libqt4-opengl as Depends of ia32-libs-multiarch
      Installing libgl1-mesa-glx as Depends of libqt4-opengl
        Installing libdrm2 as Depends of libgl1-mesa-glx
        Installing libglapi-mesa as Depends of libgl1-mesa-glx
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
  Installing libgl1-mesa-glx as Depends of libcegui-mk2-1
  Installing libunique-3.0-0 as Depends of gnome-disk-utility
  Installing libcolord1 as Depends of gnome-settings-daemon
    Installing colord as Recommends of libcolord1
      Installing liblcms2-2 as Depends of colord
      Installing icc-profiles-free as Recommends of colord
  Installing libgnomekbd7 as Depends of gnome-settings-daemon
  Installing libdrm2 as Depends of xserver-xorg-core
  Installing libpciaccess0 as Depends of xserver-xorg-core
  previously satisfied important dependency on libgl1-mesa-dri
  Installing libgl1-mesa-dri as Recommends of xserver-xorg-core
  Installing librhythmbox-core4 as Depends of rhythmbox
  Installing libgtksourceview-3.0-0 as Depends of gedit
    Installing libgtksourceview-3.0-common as Depends of libgtksourceview-3.0-0
  new important dependency: gir1.2-gtksource-3.0
  Installing gir1.2-gtksource-3.0 as Recommends of gedit
  previously satisfied important dependency on marble-plugins
  Installing libdrm-intel1 as Depends of libgl1-mesa-dri
  Installing libdrm-nouveau1a as Depends of libgl1-mesa-dri
  Installing libgtkmm-3.0-1 as Depends of gnome-system-monitor
  Installing libdlrestrictions1 as Depends of libkdecore5
  new important dependency: libavcodec-extra-53
  Installing libavcodec-extra-53 as Recommends of ubuntu-restricted-extras
  Setting NOT as auto-installed (direct Recommends of pkg in APT::Never-MarkAuto-Sections)
    Installing libavutil-extra-51 as Depends of libavcodec-extra-53
    Installing libvo-aacenc0 as Depends of libavcodec-extra-53
    Installing libvo-amrwbenc0 as Depends of libavcodec-extra-53
  Installing libasound2 as Depends of guitarpro6
  Installing libxml2 as Depends of guitarpro6
  Installing libxslt1.1 as Depends of guitarpro6
  Installing libportaudio0 as Depends of guitarpro6
  Installing libportaudio2 as Depends of guitarpro6
    Installing libjack-jackd2-0 as Depends of libportaudio2
  Installing libglu1-mesa as Depends of guitarpro6
  Installing gksu as Depends of guitarpro6
    Installing libgksu2-0 as Depends of gksu
      Installing libgconf2-4 as Depends of libgksu2-0
        Installing libdbus-glib-1-2 as Depends of libgconf2-4
      Installing libgnome-keyring0 as Depends of libgksu2-0
      Installing libgtop2-7 as Depends of libgksu2-0
      Installing libstartup-notification0 as Depends of libgksu2-0
        Installing libx11-xcb1 as Depends of libstartup-notification0
        Installing libxcb-util0 as Depends of libstartup-notification0
      Installing gconf2 as Depends of libgksu2-0
        Installing psmisc as Depends of gconf2
          Installing libncurses5 as Depends of psmisc
            Installing libtinfo5 as Depends of libncurses5
            Installing libgpm2 as Recommends of libncurses5
        Installing libgtk-3-0 as Recommends of gconf2
          Installing libcairo-gobject2 as Depends of libgtk-3-0
      Installing xauth as Depends of libgksu2-0
        Installing libxmuu1 as Depends of xauth
      Installing sudo as Recommends of libgksu2-0
        Installing libpam0g as Depends of sudo
        Installing libpam-modules as Depends of sudo
    Installing gnome-keyring as Recommends of gksu
      Installing dconf-gsettings-backend as Depends of gnome-keyring
      Installing libcap-ng0 as Depends of gnome-keyring
      Installing libgck-1-0 as Depends of gnome-keyring
        Installing libp11-kit0 as Depends of libgck-1-0
      Installing libgcr-3-1 as Depends of gnome-keyring
      Installing libcap2-bin as Depends of gnome-keyring
        Installing libcap2 as Depends of libcap2-bin
      Installing libpam-gnome-keyring as Recommends of gnome-keyring
  Installing libncurses5 as Depends of bsdmainutils
    Installing libtinfo5 as Depends of libncurses5
    previously satisfied important dependency on libgpm2
    Installing libgpm2 as Recommends of libncurses5
  Installing libglapi-mesa as Depends of libgl1-mesa-glx
  Installing libpostproc52 as Depends of mplayer
  Installing libtinfo-dev as Depends of libncurses5-dev
  Installing libebackend-1.2-1 as Depends of evolution-exchange
    Installing libgconf2-4 as Depends of libebackend-1.2-1
      Installing libxml2 as Depends of libgconf2-4
  Installing libedata-book-1.2-11 as Depends of evolution-exchange
  Installing libedata-cal-1.2-13 as Depends of evolution-exchange
  Installing libgtk-3-0 as Depends of evolution-exchange
  Installing gconf2 as Depends of evolution-exchange
    Installing psmisc as Depends of gconf2
  Installing gir1.2-launchpad-integration-3.0 as Depends of gnome-sudoku
  Installing python-gobject-2 as Depends of python-indicate
  Installing libevent-2.0-5 as Depends of transmission-gtk
  Installing libminiupnpc5 as Depends of transmission-gtk
  Installing libnatpmp1 as Depends of transmission-gtk
  Installing libxmuu1 as Depends of xauth
  Installing libmono-csharp4.0-cil as Depends of gbrainy
  Installing libgck-1-0 as Depends of seahorse
    Installing libp11-kit0 as Depends of libgck-1-0
  Installing libgcr-3-1 as Depends of seahorse
  Installing libgnome-keyring0 as Depends of seahorse
  Installing dconf-gsettings-backend as Depends of seahorse
  Installing gnome-keyring as Depends of seahorse
    Installing libcap-ng0 as Depends of gnome-keyring
    Installing libcap2-bin as Depends of gnome-keyring
      Installing libcap2 as Depends of libcap2-bin
    previously satisfied important dependency on libpam-gnome-keyring
    Installing libpam-gnome-keyring as Recommends of gnome-keyring
  Installing libboost-iostreams1.46.1 as Depends of aptitude
  Installing libfolks-telepathy25 as Depends of empathy
    Installing libfolks25 as Depends of libfolks-telepathy25
  Installing libido3-0.1-0 as Depends of empathy
  new important dependency: telepathy-indicator
  Installing telepathy-indicator as Recommends of empathy
  Installing libapt-inst1.3 as Depends of python-apt
  Installing liboverlay-scrollbar-0.2-0 as Depends of overlay-scrollbar
  Installing liboverlay-scrollbar3-0.2-0 as Depends of overlay-scrollbar
  Installing gcj-4.6-jre as Depends of gcj-jre
    Installing gcj-4.6-base as Depends of gcj-4.6-jre
    Installing gcj-4.6-jre-headless as Depends of gcj-4.6-jre
      Installing libgcj12 as Depends of gcj-4.6-jre-headless
        Installing gcj-4.6-jre-lib as Recommends of libgcj12
    Installing libgcj12-awt as Depends of gcj-4.6-jre
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
  Installing libmysqlclient16 as Depends of mysql-server-core-5.1
  Installing libseed-gtk3-0 as Depends of seed
  Installing g++-4.6 as Depends of g++
    Installing gcc-4.6 as Depends of g++-4.6
      Installing cpp-4.6 as Depends of gcc-4.6
      Installing libquadmath0 as Depends of gcc-4.6
    Installing libstdc++6-4.6-dev as Depends of g++-4.6
  Installing sudo as Depends of ubuntu-minimal
  Setting NOT as auto-installed (direct Depends of pkg in APT::Never-MarkAuto-Sections)
  Installing sound-theme-freedesktop as Depends of libcanberra0
  Installing libmtp9 as Depends of banshee
    Installing libmtp-common as Depends of libmtp9
    Installing libmtp-runtime as Recommends of libmtp9
  Installing libclutter-gtk-1.0-0 as Depends of gnibbles
  Installing libkonq5abi1 as Depends of dolphin
    Installing libkonq-common as Depends of libkonq5abi1
  new important dependency: anthy
  Installing anthy as Recommends of m17n-db
    Installing anthy-common as Depends of anthy
  new important dependency: ispell
  Installing ispell as Recommends of m17n-db
    Installing iamerican as Recommends of ispell
      Installing ienglish-common as Depends of iamerican
  Installing libgtop2-7 as Depends of gnome-nettool
  Installing gksu as Depends of gnome-codec-install
  Installing libmono-management4.0-cil as Depends of mono-csharp-shell
  new important dependency: gir1.2-dbusmenu-gtk-0.4
  Installing gir1.2-dbusmenu-gtk-0.4 as Recommends of update-manager
  Installing libglu1-mesa as Depends of mupen64plus
  Installing qt4-linguist-tools as Depends of libqt4-dev
  Installing evolution-couchdb-backend as Depends of evolution-couchdb
  Installing libboost-program-options1.46.1 as Depends of akonadi-server
  Installing akonadi-backend-mysql as Depends of akonadi-server
  Installing fonts-arabeyes as Depends of ttf-arabeyes
  Installing python-pyatspi2 as Depends of gnome-orca
    Installing gir1.2-atspi-2.0 as Depends of python-pyatspi2
  Installing gir1.2-wnck-3.0 as Depends of gnome-orca
  Installing libboost-python1.46.1 as Depends of python-pythonmagick
  Installing kde-workspace-bin as Depends of kde-window-manager
    Installing libkephal4abi1 as Depends of kde-workspace-bin
    Installing libprocesscore4abi1 as Depends of kde-workspace-bin
    Installing libsolidcontrol4abi2 as Depends of kde-workspace-bin
    Installing libsolidcontrolifaces4abi2 as Depends of kde-workspace-bin
    Installing plasma-desktop as Depends of kde-workspace-bin
      Installing libtaskmanager4abi2 as Depends of plasma-desktop
      Installing plasma-widgets-workspace as Depends of plasma-desktop
        Installing libkunitconversion4 as Depends of plasma-widgets-workspace
        Installing libplasmaclock4abi2 as Depends of plasma-widgets-workspace
          Installing libkholidays4 as Depends of libplasmaclock4abi2
        Installing plasma-dataengines-workspace as Depends of plasma-widgets-workspace
          Installing libkcalcore4 as Depends of plasma-dataengines-workspace
          Installing libkcalutils4 as Depends of plasma-dataengines-workspace
          Installing libksgrd4 as Depends of plasma-dataengines-workspace
          Installing libplasma-geolocation-interface4 as Depends of plasma-dataengines-workspace
          Installing libsyndication4 as Depends of plasma-dataengines-workspace
          Installing libweather-ion6 as Depends of plasma-dataengines-workspace
          Installing ksysguardd as Recommends of plasma-dataengines-workspace
      Installing kde-workspace as Recommends of plasma-desktop
        Installing klipper as Depends of kde-workspace
          Installing libprison0 as Depends of klipper
            Installing libdmtx0a as Depends of libprison0
            Installing libqrencode3 as Depends of libprison0
        Installing ksysguard as Depends of kde-workspace
          Installing libksignalplotter4 as Depends of ksysguard
        Installing systemsettings as Depends of kde-workspace
        Installing freespacenotifier as Depends of kde-workspace
        Installing kdm as Recommends of kde-workspace
          Installing kde-workspace-kgreet-plugins as Depends of kdm
        Installing kinfocenter as Recommends of kde-workspace
    Installing kde-workspace-data as Depends of kde-workspace-bin
      Installing kde-wallpapers-default as Depends of kde-workspace-data
  Installing libkwineffects1abi2 as Depends of kde-window-manager
  Installing libswt-gtk-3-java as Depends of tuxguitar
    Installing libswt-gtk-3-jni as Depends of libswt-gtk-3-java
  Installing libswt-cairo-gtk-3-jni as Depends of tuxguitar
  Installing libswt-webkit-gtk-3-jni as Depends of tuxguitar
  Installing libnl3 as Depends of network-manager
  Installing libdvbpsi7 as Depends of vlc-nox
  Installing libmatroska4 as Depends of vlc-nox
  Installing libgrip0 as Depends of eog
  Installing libkface1 as Depends of digikam
    Installing libkface-data as Depends of libkface1
  Installing kde-baseapps-bin as Depends of kdebase-bin
    Installing kde-baseapps-data as Depends of kde-baseapps-bin
  Installing mono-4.0-gac as Depends of mono-gac
  new important dependency: indicator-status-provider-mc5
  Installing indicator-status-provider-mc5 as Recommends of indicator-messages
  Installing gir1.2-gnomebluetooth-1.0 as Depends of gnome-bluetooth
  previously satisfied important dependency on indicator-me
  Installing indicator-me as Recommends of indicator-applet-session
  Installing software-properties-common as Depends of software-properties-gtk
  Installing libcogl5 as Depends of libclutter-1.0-0
    Installing libcogl-common as Recommends of libcogl5
  Installing compiz-plugins-default as Depends of compiz-gnome
  Installing linux-headers-3.0.0-12-generic as Depends of linux-headers-generic
    Installing linux-headers-3.0.0-12 as Depends of linux-headers-3.0.0-12-generic
  Installing libavfilter2 as Depends of ffmpeg
  Installing linux-image-3.0.0-12-generic as Depends of linux-image-generic
  Setting NOT as auto-installed (direct Depends of pkg in APT::Never-MarkAuto-Sections)
  Installing libevince3-3 as Depends of evince
  Installing libsigsegv2 as PreDepends of gawk
  Installing flashplugin-downloader as Depends of flashplugin-installer
    Installing libnss3-1d as Depends of flashplugin-downloader
    Installing libnspr4-0d as Depends of flashplugin-downloader
    Installing libasound2-plugins as Recommends of flashplugin-downloader
      Installing libpulse0 as Depends of libasound2-plugins
        Installing libasyncns0 as Depends of libpulse0
        Installing libjson0 as Depends of libpulse0
        Installing libsndfile1 as Depends of libpulse0
          Installing libflac8 as Depends of libsndfile1
            Installing libogg0 as Depends of libflac8
          Installing libvorbis0a as Depends of libsndfile1
          Installing libvorbisenc2 as Depends of libsndfile1
        Installing libwrap0 as Depends of libpulse0
      Installing libsamplerate0 as Depends of libasound2-plugins
      Installing libspeexdsp1 as Depends of libasound2-plugins
  Installing libppl-c4 as Depends of libcloog-ppl0
    Installing libppl9 as Depends of libppl-c4
    Installing libpwl5 as Depends of libppl-c4
  Installing wine1.3 as Depends of wine
    Installing wine1.3-gecko as Recommends of wine1.3
    Installing winetricks as Recommends of wine1.3
  Installing libgl1-mesa-glx as Depends of gens
    Installing libdrm2 as Depends of libgl1-mesa-glx
    Installing libglapi-mesa as Depends of libgl1-mesa-glx
    Installing libgl1-mesa-dri as Recommends of libgl1-mesa-glx
      Installing libdrm-intel1 as Depends of libgl1-mesa-dri
      Installing libdrm-nouveau1a as Depends of libgl1-mesa-dri
  Installing libsdl1.2debian as Depends of gens
    Installing libsdl1.2debian-alsa as Depends of libsdl1.2debian
  new important dependency: appmenu-gtk3
  Installing appmenu-gtk3 as Recommends of indicator-appmenu
  Installing libdrm-nouveau1a as Depends of xserver-xorg-video-nouveau
  Installing libboost-filesystem1.46.1 as Depends of smc
    Installing libboost-system1.46.1 as Depends of libboost-filesystem1.46.1
  Installing libgl1-mesa-glx as Depends of smc
  Installing libsdl1.2debian as Depends of smc
    Installing libsdl1.2debian-alsa as Depends of libsdl1.2debian
  Installing gir1.2-indicate-0.6 as Depends of gwibber-service
  Installing libtar0 as Depends of vlc
  Installing libindicator6 as Depends of libappindicator1
  Installing libyelp0 as Depends of yelp
  Installing libgksu2-0 as Depends of gksu
  Installing libbrasero-media3-1 as Depends of brasero-cdrkit
  Installing gir1.2-appindicator3-0.1 as Depends of jockey-gtk
  Installing libgl1-mesa-dri as Depends of xorg
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
  new important dependency: gnome-session-fallback
  Installing gnome-session-fallback as Recommends of gnome-panel
  Installing libdrm2 as Depends of libkms1
  new important dependency: extlinux
  Installing extlinux as Recommends of unetbootin
    Installing syslinux-themes-debian as Recommends of extlinux
      Installing syslinux-themes-debian-squeeze as Depends of syslinux-themes-debian
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
  Installing libgwibber-gtk2 as Depends of gwibber
    Installing libgtkspell3-0 as Depends of libgwibber-gtk2
    Installing libgwibber2 as Depends of libgwibber-gtk2
  Installing libpanel-applet-3-0 as Depends of gir1.2-panelapplet-3.0
  Installing libdmapsharing-3.0-2 as Depends of rhythmbox-plugins
  Installing gir1.2-rb-3.0 as Depends of rhythmbox-plugins
  Installing katepart as Depends of kdelibs5-plugins
    Installing kate-data as Depends of katepart
  Installing libakonadi-contact4 as Depends of kdepim-runtime
  Installing libkmbox4 as Depends of kdepim-runtime
  Installing libkpimidentities4 as Depends of kdepim-runtime
    Installing libkpimtextedit4 as Depends of libkpimidentities4
  Installing gtk3-engines-unico as Depends of light-themes
  new important dependency: python-cssutils-doc
  Installing python-cssutils-doc as Recommends of python-cssutils
  Installing libdrm-intel1 as Depends of plymouth
  Installing gir1.2-cogl-1.0 as Depends of gir1.2-clutter-1.0
  Installing gir1.2-json-1.0 as Depends of gir1.2-clutter-1.0
  new important dependency: libgphoto2-l10n
  Installing libgphoto2-l10n as Recommends of libgphoto2-2
Starting
Starting 2
Investigating (0) libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
Broken libgl1-mesa-glx:amd64 Breaks on libgl1-mesa-glx [ i386 ] < none -> 7.11-0ubuntu3 > ( libs ) (!= 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty)
  Considering libgl1-mesa-glx:i386 6 as a solution to libgl1-mesa-glx:amd64 174
  Added libgl1-mesa-glx:i386 to the remove list
  Fixing libgl1-mesa-glx:amd64 via keep of libgl1-mesa-glx:i386
Investigating (0) libdrm2 [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libs )
Broken libdrm2:amd64 Breaks on libdrm2 [ i386 ] < none -> 2.4.26-1ubuntu1 > ( libs ) (!= 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty)
  Considering libdrm2:i386 19 as a solution to libdrm2:amd64 136
  Added libdrm2:i386 to the remove list
  Fixing libdrm2:amd64 via keep of libdrm2:i386
Investigating (0) libgl1-mesa-dri [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
Broken libgl1-mesa-dri:amd64 Breaks on libgl1-mesa-dri [ i386 ] < none -> 7.11-0ubuntu3 > ( libs ) (!= 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty)
  Considering libgl1-mesa-dri:i386 5 as a solution to libgl1-mesa-dri:amd64 105
  Added libgl1-mesa-dri:i386 to the remove list
  Fixing libgl1-mesa-dri:amd64 via keep of libgl1-mesa-dri:i386
Investigating (0) libdbusmenu-glib4 [ amd64 ] < none -> 0.5.0-0ubuntu3 > ( libs )
Broken libdbusmenu-glib4:amd64 Breaks on gir1.2-unity-3.0 [ amd64 ] < 3.8.4-0ubuntu1 > ( libs ) (< 3.8.4-0ubuntu2)
  Considering gir1.2-unity-3.0:amd64 5 as a solution to libdbusmenu-glib4:amd64 85
  Added gir1.2-unity-3.0:amd64 to the remove list
  Fixing libdbusmenu-glib4:amd64 via remove of gir1.2-unity-3.0:amd64
Investigating (0) gvfs [ amd64 ] < 1.8.0-0ubuntu3 -> 1.10.0-0ubuntu1 > ( libs )
Broken gvfs:amd64 Conflicts on libgvfscommon0 [ amd64 ] < 1.8.0-0ubuntu3 > ( libs )
  Considering libgvfscommon0:amd64 -1 as a solution to gvfs:amd64 73
  Added libgvfscommon0:amd64 to the remove list
  Fixing gvfs:amd64 via remove of libgvfscommon0:amd64
Investigating (0) libglapi-mesa [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
Broken libglapi-mesa:amd64 Breaks on libglapi-mesa [ i386 ] < none -> 7.11-0ubuntu3 > ( libs ) (!= 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty)
  Considering libglapi-mesa:i386 2 as a solution to libglapi-mesa:amd64 56
  Added libglapi-mesa:i386 to the remove list
  Fixing libglapi-mesa:amd64 via keep of libglapi-mesa:i386
Investigating (0) kde-runtime [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
Broken kde-runtime:amd64 Breaks on plasma-scriptengine-declarative [ amd64 ] < 4:4.6.5-0ubuntu1 > ( kde )
  Considering plasma-scriptengine-declarative:amd64 -1 as a solution to kde-runtime:amd64 49
  Added plasma-scriptengine-declarative:amd64 to the remove list
  Fixing kde-runtime:amd64 via remove of plasma-scriptengine-declarative:amd64
Investigating (0) libsdl1.2debian-pulseaudio [ amd64 ] < 1.2.14-6.1ubuntu3 -> 1.2.14-6.1ubuntu4 > ( libs )
Broken libsdl1.2debian-pulseaudio:amd64 Conflicts on libsdl1.2debian-alsa [ amd64 ] < none -> 1.2.14-6.1ubuntu4 > ( libs )
  Considering libsdl1.2debian-alsa:amd64 39 as a solution to libsdl1.2debian-pulseaudio:amd64 41
  Added libsdl1.2debian-alsa:amd64 to the remove list
  Conflicts//Breaks against version 1.2.13-4ubuntu4 for libsdl1.2debian-alsa but that is not InstVer, ignoring
  Fixing libsdl1.2debian-pulseaudio:amd64 via keep of libsdl1.2debian-alsa:amd64
Investigating (0) gnome-keyring [ amd64 ] < 2.92.92.is.2.32.1-0ubuntu2.1 -> 3.2.0-0ubuntu1 > ( gnome )
Broken gnome-keyring:amd64 Breaks on seahorse-plugins [ amd64 ] < 2.30.1-3ubuntu2 > ( gnome ) (< 3.0)
  Considering seahorse-plugins:amd64 -1 as a solution to gnome-keyring:amd64 25
  Added seahorse-plugins:amd64 to the remove list
  Fixing gnome-keyring:amd64 via remove of seahorse-plugins:amd64
Investigating (0) language-support-translations-en [ amd64 ] < 1:9.04+20090401 > ( translations )
Broken language-support-translations-en:amd64 Depends on evolution-documentation-en [ amd64 ] < none > ( none )
  Considering evolution-common:amd64 6 as a solution to language-support-translations-en:amd64 24
  Added evolution-common:amd64 to the remove list
  Fixing language-support-translations-en:amd64 via keep of evolution-common:amd64
Investigating (0) kde-runtime-data [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
Broken kde-runtime-data:amd64 Breaks on kdebase-runtime-data [ amd64 ] < 4:4.6.5-0ubuntu1 > ( kde )
  Considering kdebase-runtime-data:amd64 -1 as a solution to kde-runtime-data:amd64 22
  Added kdebase-runtime-data:amd64 to the remove list
  Fixing kde-runtime-data:amd64 via remove of kdebase-runtime-data:amd64
Investigating (0) ntfs-3g [ amd64 ] < 1:2010.8.8-0ubuntu1 -> 1:2011.4.12AR.4-2ubuntu3 > ( otherosfs )
Broken ntfs-3g:amd64 Conflicts on ntfsprogs [ amd64 ] < 2.0.0-1ubuntu4 > ( universe/otherosfs )
  Considering ntfsprogs:amd64 9 as a solution to ntfs-3g:amd64 22
  Added ntfsprogs:amd64 to the remove list
  Fixing ntfs-3g:amd64 via remove of ntfsprogs:amd64
Investigating (0) console-setup [ amd64 ] < 1.57ubuntu20 -> 1.57ubuntu27 > ( utils )
Broken console-setup:amd64 Conflicts on console-terminus [ amd64 ] < 4.30-2 > ( fonts )
  Considering console-terminus:amd64 -1 as a solution to console-setup:amd64 19
  Added console-terminus:amd64 to the remove list
  Fixing console-setup:amd64 via remove of console-terminus:amd64
Investigating (0) libdrm-intel1 [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libs )
Broken libdrm-intel1:amd64 Breaks on libdrm-intel1 [ i386 ] < none -> 2.4.26-1ubuntu1 > ( libs ) (!= 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty)
  Considering libdrm-intel1:i386 4 as a solution to libdrm-intel1:amd64 18
  Added libdrm-intel1:i386 to the remove list
  Fixing libdrm-intel1:amd64 via keep of libdrm-intel1:i386
Investigating (0) gnome-panel [ amd64 ] < 1:2.32.1-0ubuntu6.5 -> 1:3.2.0-0ubuntu1 > ( universe/gnome )
Broken gnome-panel:amd64 Breaks on libpanel-applet-3-0 [ amd64 ] < 1:2.32.1-0ubuntu6.5 > ( libs )
  Considering libpanel-applet-3-0:amd64 12 as a solution to gnome-panel:amd64 18
  Added libpanel-applet-3-0:amd64 to the remove list
Broken gnome-panel:amd64 Breaks on libpanel-applet2-0 [ amd64 ] < 1:2.32.1-0ubuntu6.5 > ( libs )
  Considering libpanel-applet2-0:amd64 11 as a solution to gnome-panel:amd64 18
  Added libpanel-applet2-0:amd64 to the remove list
  Fixing gnome-panel:amd64 via remove of libpanel-applet-3-0:amd64
  Fixing gnome-panel:amd64 via remove of libpanel-applet2-0:amd64
Investigating (0) libdrm-radeon1 [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libs )
Broken libdrm-radeon1:amd64 Breaks on libdrm-radeon1 [ i386 ] < none -> 2.4.26-1ubuntu1 > ( libs ) (!= 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty)
  Considering libdrm-radeon1:i386 4 as a solution to libdrm-radeon1:amd64 17
  Added libdrm-radeon1:i386 to the remove list
  Fixing libdrm-radeon1:amd64 via keep of libdrm-radeon1:i386
Investigating (0) gnome-control-center-data [ amd64 ] < none -> 1:3.2.0-0ubuntu6 > ( gnome )
Broken gnome-control-center-data:amd64 Conflicts on capplets-data [ amd64 ] < 1:2.32.1-0ubuntu15 > ( gnome )
  Considering capplets-data:amd64 -1 as a solution to gnome-control-center-data:amd64 17
  Added capplets-data:amd64 to the remove list
  Fixing gnome-control-center-data:amd64 via remove of capplets-data:amd64
Investigating (0) libdrm-nouveau1a [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libs )
Broken libdrm-nouveau1a:amd64 Breaks on libdrm-nouveau1a [ i386 ] < none -> 2.4.26-1ubuntu1 > ( libs ) (!= 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty)
  Considering libdrm-nouveau1a:i386 4 as a solution to libdrm-nouveau1a:amd64 17
  Added libdrm-nouveau1a:i386 to the remove list
  Fixing libdrm-nouveau1a:amd64 via keep of libdrm-nouveau1a:i386
Investigating (0) indicator-messages [ amd64 ] < 0.4.0-0ubuntu1 -> 0.5.0-0ubuntu1 > ( gnome )
Broken indicator-messages:amd64 Conflicts on indicator-me [ amd64 ] < 0.2.19-0ubuntu1 > ( gnome )
  Considering indicator-me:amd64 2 as a solution to indicator-messages:amd64 14
  Added indicator-me:amd64 to the remove list
  Fixing indicator-messages:amd64 via remove of indicator-me:amd64
Investigating (0) evolution [ amd64 ] < 2.32.2-0ubuntu7 -> 3.2.0-0ubuntu2 > ( gnome )
Broken evolution:amd64 Depends on evolution-common [ amd64 ] < 2.32.2-0ubuntu7 -> 3.2.0-0ubuntu2 > ( gnome ) (= 3.2.0-0ubuntu2)
  Considering evolution-common:amd64 6 as a solution to evolution:amd64 7
  Removing evolution:amd64 rather than change evolution-common:amd64
Investigating (0) gir1.2-json-1.0 [ amd64 ] < none -> 0.14.0-1 > ( libs )
Broken gir1.2-json-1.0:amd64 Conflicts on gir1.2-json-glib-1.0 [ amd64 ] < 0.12.2-0ubuntu1 > ( libs )
  Considering gir1.2-json-glib-1.0:amd64 2 as a solution to gir1.2-json-1.0:amd64 7
  Added gir1.2-json-glib-1.0:amd64 to the remove list
  Fixing gir1.2-json-1.0:amd64 via remove of gir1.2-json-glib-1.0:amd64
Investigating (0) evolution-plugins [ amd64 ] < 2.32.2-0ubuntu7 -> 3.2.0-0ubuntu2 > ( gnome )
Broken evolution-plugins:amd64 Depends on evolution [ amd64 ] < 2.32.2-0ubuntu7 -> 3.2.0-0ubuntu2 > ( gnome ) (= 3.2.0-0ubuntu2)
  Considering evolution:amd64 7 as a solution to evolution-plugins:amd64 6
  Holding Back evolution-plugins:amd64 rather than change evolution:amd64
 Try to Re-Instate (0) evolution-common:amd64
Investigating (0) rhythmbox [ amd64 ] < 0.13.3-0ubuntu6 -> 2.90.1~20110908-0ubuntu1 > ( gnome )
Broken rhythmbox:amd64 Breaks on rhythmbox-ubuntuone-music-store [ amd64 ] < 0.2.0-0ubuntu1 > ( gnome ) (<= 0.2.0-0ubuntu1)
  Considering rhythmbox-ubuntuone-music-store:amd64 -2 as a solution to rhythmbox:amd64 5
  Added rhythmbox-ubuntuone-music-store:amd64 to the remove list
  Fixing rhythmbox:amd64 via remove of rhythmbox-ubuntuone-music-store:amd64
Investigating (0) libmlt4 [ amd64 ] < none -> 0.7.4-3 > ( universe/libs )
Broken libmlt4:amd64 Conflicts on libmlt3 [ amd64 ] < 0.6.2-2 > ( libs )
  Considering libmlt3:amd64 -1 as a solution to libmlt4:amd64 5
  Added libmlt3:amd64 to the remove list
  Fixing libmlt4:amd64 via remove of libmlt3:amd64
Investigating (0) wine1.2 [ amd64 ] < 1.2.2-0ubuntu6 -> 1.2.3-0ubuntu1 > ( universe/otherosfs )
Broken wine1.2:amd64 Breaks on ttf-symbol-replacement [ amd64 ] < 1.2.2-0ubuntu6 > ( fonts )
  Considering ttf-symbol-replacement:amd64 -1 as a solution to wine1.2:amd64 4
  Added ttf-symbol-replacement:amd64 to the remove list
  Fixing wine1.2:amd64 via remove of ttf-symbol-replacement:amd64
Investigating (0) kde-baseapps-data [ amd64 ] < none -> 4:4.7.1-0ubuntu3 > ( kde )
Broken kde-baseapps-data:amd64 Breaks on kdebase-data [ amd64 ] < 4:4.6.5-0ubuntu1 > ( kde )
  Considering kdebase-data:amd64 -1 as a solution to kde-baseapps-data:amd64 4
  Added kdebase-data:amd64 to the remove list
  Fixing kde-baseapps-data:amd64 via remove of kdebase-data:amd64
Investigating (0) libmtp-common [ amd64 ] < none -> 1.1.0-3ubuntu1 > ( libs )
Broken libmtp-common:amd64 Breaks on libmtp8 [ amd64 ] < 1.0.6-2 > ( libs ) (<= 1.0.6-6)
  Considering libmtp8:amd64 -1 as a solution to libmtp-common:amd64 4
  Added libmtp8:amd64 to the remove list
  Fixing libmtp-common:amd64 via remove of libmtp8:amd64
Investigating (0) gstreamer0.10-plugins-ugly [ amd64 ] < 0.10.17-1ubuntu2 -> 0.10.18-3ubuntu1 > ( universe/libs )
Broken gstreamer0.10-plugins-ugly:amd64 Conflicts on gstreamer0.10-lame [ amd64 ] < none > ( none )
  Considering gstreamer0.10-plugins-ugly-multiverse:amd64 -1 as a solution to gstreamer0.10-plugins-ugly:amd64 3
  Added gstreamer0.10-plugins-ugly-multiverse:amd64 to the remove list
  Fixing gstreamer0.10-plugins-ugly:amd64 via remove of gstreamer0.10-plugins-ugly-multiverse:amd64
Investigating (0) wine1.3 [ amd64 ] < none -> 1.3.28-0ubuntu1 > ( universe/otherosfs )
Broken wine1.3:amd64 Conflicts on wine1.2 [ amd64 ] < 1.2.2-0ubuntu6 -> 1.2.3-0ubuntu1 > ( universe/otherosfs )
  Considering wine1.2:amd64 4 as a solution to wine1.3:amd64 3
  Holding Back wine1.3:amd64 rather than change wine1.2:amd64
Investigating (0) libqt4-sql-mysql [ i386 ] < none -> 4:4.7.4-0ubuntu8 > ( libs )
Broken libqt4-sql-mysql:i386 Depends on libmysqlclient16 [ i386 ] < none -> 5.1.58-1ubuntu1 > ( libs ) (>= 5.1.50-1)
  Considering libmysqlclient16:i386 1 as a solution to libqt4-sql-mysql:i386 3
  Holding Back libqt4-sql-mysql:i386 rather than change libmysqlclient16:i386
Investigating (0) python-gnome2 [ amd64 ] < 2.28.1-1ubuntu3 -> 2.28.1-3 > ( python )
Broken python-gnome2:amd64 Conflicts on python-gnomecanvas [ amd64 ] < 2.28.1-1ubuntu3 > ( python )
  Considering python-gnomecanvas:amd64 -1 as a solution to python-gnome2:amd64 2
  Added python-gnomecanvas:amd64 to the remove list
  Fixing python-gnome2:amd64 via remove of python-gnomecanvas:amd64
Investigating (0) kde-workspace-bin [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
Broken kde-workspace-bin:amd64 Breaks on kdebase-workspace-bin [ amd64 ] < 4:4.6.5-0ubuntu1 > ( kde ) (< 4:4.6.90)
  Considering kdebase-workspace-bin:amd64 -1 as a solution to kde-workspace-bin:amd64 2
  Added kdebase-workspace-bin:amd64 to the remove list
Broken kde-workspace-bin:amd64 Breaks on kdebase-workspace-data [ amd64 ] < 4:4.6.5-0ubuntu1 > ( kde ) (< 4:4.6.80)
  Considering kdebase-workspace-data:amd64 1 as a solution to kde-workspace-bin:amd64 2
  Added kdebase-workspace-data:amd64 to the remove list
Broken kde-workspace-bin:amd64 Breaks on libpowerdevilcore0 [ amd64 ] < 4:4.6.5-0ubuntu1 > ( libs )
  Considering libpowerdevilcore0:amd64 1 as a solution to kde-workspace-bin:amd64 2
  Added libpowerdevilcore0:amd64 to the remove list
  Fixing kde-workspace-bin:amd64 via remove of kdebase-workspace-bin:amd64
  Fixing kde-workspace-bin:amd64 via remove of kdebase-workspace-data:amd64
  Fixing kde-workspace-bin:amd64 via remove of libpowerdevilcore0:amd64
Investigating (0) libkonq-common [ amd64 ] < none -> 4:4.7.1-0ubuntu3 > ( libs )
Broken libkonq-common:amd64 Breaks on libkonq5a [ amd64 ] < 4:4.6.5-0ubuntu1 > ( libs )
  Considering libkonq5a:amd64 -1 as a solution to libkonq-common:amd64 2
  Added libkonq5a:amd64 to the remove list
  Fixing libkonq-common:amd64 via remove of libkonq5a:amd64
Investigating (0) libqt4-opengl [ i386 ] < none -> 4:4.7.4-0ubuntu8 > ( libs )
Broken libqt4-opengl:i386 Depends on libgl1-mesa-glx [ i386 ] < none -> 7.11-0ubuntu3 > ( libs )
  Considering libgl1-mesa-glx:i386 6 as a solution to libqt4-opengl:i386 2
  Holding Back libqt4-opengl:i386 rather than change libgl1-mesa-glx:i386
Broken libqt4-opengl:i386 Depends on libgl1 [ i386 ] < none > ( none )
  Considering libgl1-mesa-swx11:i386 0 as a solution to libqt4-opengl:i386 2
  Holding Back libqt4-opengl:i386 rather than change libgl1:i386
  Or group keep for libqt4-opengl:i386
Investigating (0) kde-workspace-kgreet-plugins [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( libs )
Broken kde-workspace-kgreet-plugins:amd64 Breaks on kdebase-workspace-kgreet-plugins [ amd64 ] < 4:4.6.5-0ubuntu1 > ( libs ) (< 4:4.6.90)
  Considering kdebase-workspace-kgreet-plugins:amd64 1 as a solution to kde-workspace-kgreet-plugins:amd64 2
  Added kdebase-workspace-kgreet-plugins:amd64 to the remove list
  Fixing kde-workspace-kgreet-plugins:amd64 via remove of kdebase-workspace-kgreet-plugins:amd64
Investigating (0) python-pyatspi2 [ amd64 ] < none -> 2.2.0-0ubuntu1 > ( python )
Broken python-pyatspi2:amd64 Conflicts on python-pyatspi [ amd64 ] < 1.32.0-0ubuntu2 -> 1.32.0-0ubuntu3 > ( universe/libs )
  Considering python-pyatspi:amd64 0 as a solution to python-pyatspi2:amd64 1
  Added python-pyatspi:amd64 to the remove list
  Conflicts//Breaks against version 1.32.0-0ubuntu2 for python-pyatspi but that is not InstVer, ignoring
  Fixing python-pyatspi2:amd64 via remove of python-pyatspi:amd64
Investigating (0) libevince3-3 [ amd64 ] < none -> 3.2.0-0ubuntu1 > ( libs )
Broken libevince3-3:amd64 Breaks on libevdocument3 [ amd64 ] < 2.32.0-0ubuntu12.3 > ( libs )
  Considering libevdocument3:amd64 2 as a solution to libevince3-3:amd64 1
  Holding Back libevince3-3:amd64 rather than change libevdocument3:amd64
Investigating (0) indicator-applet-session [ amd64 ] < 0.4.12-0ubuntu1 > ( gnome )
Broken indicator-applet-session:amd64 Depends on libpanel-applet-3-0 [ amd64 ] < 1:2.32.1-0ubuntu6.5 > ( libs )
  Considering libpanel-applet-3-0:amd64 12 as a solution to indicator-applet-session:amd64 1
  Removing indicator-applet-session:amd64 rather than change libpanel-applet-3-0:amd64
Investigating (0) evince [ amd64 ] < 2.32.0-0ubuntu12.3 -> 3.2.0-0ubuntu1 > ( gnome )
Broken evince:amd64 Depends on libevince3-3 [ amd64 ] < none -> 3.2.0-0ubuntu1 > ( libs ) (= 3.2.0-0ubuntu1)
  Considering libevince3-3:amd64 1 as a solution to evince:amd64 1
  Removing evince:amd64 rather than change libevince3-3:amd64
Investigating (0) ubuntu-desktop [ amd64 ] < 1.220 -> 1.245 > ( metapackages )
Broken ubuntu-desktop:amd64 Depends on evince [ amd64 ] < 2.32.0-0ubuntu12.3 -> 3.2.0-0ubuntu1 > ( gnome )
  Considering evince:amd64 1 as a solution to ubuntu-desktop:amd64 0
  Removing ubuntu-desktop:amd64 rather than change evince:amd64
Investigating (0) esound-clients [ amd64 ] < 0.2.41-8 > ( sound )
Broken esound-clients:amd64 Depends on esound-common [ amd64 ] < 0.2.41-8 -> 0.2.41-9 > ( sound ) (= 0.2.41-8)
  Considering esound-common:amd64 10 as a solution to esound-clients:amd64 0
  Removing esound-clients:amd64 rather than change esound-common:amd64
Investigating (0) libtar0 [ amd64 ] < none -> 1.2.11-8 > ( universe/libs )
Broken libtar0:amd64 Breaks on libtar [ amd64 ] < 1.2.11-6 > ( libs )
  Considering libtar:amd64 -1 as a solution to libtar0:amd64 0
  Added libtar:amd64 to the remove list
  Fixing libtar0:amd64 via remove of libtar:amd64
Investigating (0) evolution-exchange [ amd64 ] < 2.32.2-0ubuntu3 -> 3.2.0-0ubuntu2 > ( gnome )
Broken evolution-exchange:amd64 Depends on evolution [ amd64 ] < 2.32.2-0ubuntu7 -> 3.2.0-0ubuntu2 > ( gnome ) (>= 3.1.91)
  Considering evolution:amd64 7 as a solution to evolution-exchange:amd64 0
  Removing evolution-exchange:amd64 rather than change evolution:amd64
Investigating (0) gnome-pilot [ amd64 ] < 2.32.0-0ubuntu1 > ( gnome )
Broken gnome-pilot:amd64 Depends on libpanel-applet2-0 [ amd64 ] < 1:2.32.1-0ubuntu6.5 > ( libs ) (>= 2.26.0)
  Considering libpanel-applet2-0:amd64 11 as a solution to gnome-pilot:amd64 0
  Removing gnome-pilot:amd64 rather than change libpanel-applet2-0:amd64
Investigating (0) evolution-couchdb [ amd64 ] < 0.5.3-0ubuntu2 -> 0.5.91-0ubuntu6 > ( gnome )
Broken evolution-couchdb:amd64 Depends on evolution [ amd64 ] < 2.32.2-0ubuntu7 -> 3.2.0-0ubuntu2 > ( gnome ) (>= 2.27.0)
  Considering evolution:amd64 7 as a solution to evolution-couchdb:amd64 0
  Removing evolution-couchdb:amd64 rather than change evolution:amd64
Investigating (0) wine [ amd64 ] < 1.2.2-0ubuntu6 -> 1.2.3-0ubuntu1 > ( universe/otherosfs )
Broken wine:amd64 Depends on wine1.3 [ amd64 ] < none -> 1.3.28-0ubuntu1 > ( universe/otherosfs )
  Considering wine1.3:amd64 3 as a solution to wine:amd64 0
  Holding Back wine:amd64 rather than change wine1.3:amd64
Investigating (0) gnome-pilot-conduits [ amd64 ] < 2.32.1-0ubuntu1 > ( gnome )
Broken gnome-pilot-conduits:amd64 Depends on gnome-pilot [ amd64 ] < 2.32.0-0ubuntu1 > ( gnome ) (>= 2.32.0)
  Considering gnome-pilot:amd64 0 as a solution to gnome-pilot-conduits:amd64 0
  Removing gnome-pilot-conduits:amd64 rather than change gnome-pilot:amd64
Investigating (0) florence [ amd64 ] < 0.5.0-2 > ( web )
Broken florence:amd64 Depends on libpanel-applet2-0 [ amd64 ] < 1:2.32.1-0ubuntu6.5 > ( libs ) (>= 2.26.0)
  Considering libpanel-applet2-0:amd64 11 as a solution to florence:amd64 -1
  Removing florence:amd64 rather than change libpanel-applet2-0:amd64
Investigating (0) libbrasero-media1 [ amd64 ] < 2.32.1-0ubuntu2 > ( libs )
Broken libbrasero-media1:amd64 Depends on brasero-common [ amd64 ] < 2.32.1-0ubuntu2 -> 3.2.0-0ubuntu1 > ( gnome ) (< 2.33)
  Considering brasero-common:amd64 16 as a solution to libbrasero-media1:amd64 -1
  Removing libbrasero-media1:amd64 rather than change brasero-common:amd64
Investigating (0) libgnomepanel2.24-cil [ amd64 ] < 2.26.0-3build1 > ( cli-mono )
Broken libgnomepanel2.24-cil:amd64 Depends on libpanel-applet2-0 [ amd64 ] < 1:2.32.1-0ubuntu6.5 > ( libs ) (>= 2.26.0)
  Considering libpanel-applet2-0:amd64 11 as a solution to libgnomepanel2.24-cil:amd64 -1
  Removing libgnomepanel2.24-cil:amd64 rather than change libpanel-applet2-0:amd64
Investigating (0) guitarpro6 [ i386 ] < 6.0.2 > ( non-free/audio )
Broken guitarpro6:i386 Depends on libxml2 [ i386 ] < none -> 2.7.8.dfsg-4 > ( libs )
  Considering libxml2:i386 1 as a solution to guitarpro6:i386 -1
  Removing guitarpro6:i386 rather than change libxml2:i386
Investigating (0) indicator-applet-complete [ amd64 ] < 0.4.12-0ubuntu1 > ( gnome )
Broken indicator-applet-complete:amd64 Depends on libpanel-applet-3-0 [ amd64 ] < 1:2.32.1-0ubuntu6.5 > ( libs )
  Considering libpanel-applet-3-0:amd64 12 as a solution to indicator-applet-complete:amd64 -1
  Removing indicator-applet-complete:amd64 rather than change libpanel-applet-3-0:amd64
Investigating (0) flashplugin-downloader [ i386 ] < none -> 11.0.1.152ubuntu1 > ( multiverse/web )
Broken flashplugin-downloader:i386 Conflicts on flashplugin-nonfree [ amd64 ] < 11.0.1.152ubuntu0.11.04.1 > ( contrib/web ) (< 11.0.1.152ubuntu1)
  Considering flashplugin-nonfree:amd64 -1 as a solution to flashplugin-downloader:i386 -1
  Holding Back flashplugin-downloader:i386 rather than change flashplugin-nonfree:amd64
Investigating (0) libgail-gnome-module [ amd64 ] < 1.20.3-1 > ( libs )
Broken libgail-gnome-module:amd64 Depends on libpanel-applet2-0 [ amd64 ] < 1:2.32.1-0ubuntu6.5 > ( libs ) (>= 2.26.0)
  Considering libpanel-applet2-0:amd64 11 as a solution to libgail-gnome-module:amd64 -1
  Removing libgail-gnome-module:amd64 rather than change libpanel-applet2-0:amd64
Investigating (0) indicator-applet-appmenu [ amd64 ] < 0.4.12-0ubuntu1 > ( gnome )
Broken indicator-applet-appmenu:amd64 Depends on libpanel-applet-3-0 [ amd64 ] < 1:2.32.1-0ubuntu6.5 > ( libs )
  Considering libpanel-applet-3-0:amd64 12 as a solution to indicator-applet-appmenu:amd64 -1
  Removing indicator-applet-appmenu:amd64 rather than change libpanel-applet-3-0:amd64
Investigating (0) libpulse-browse0 [ amd64 ] < 1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1 > ( sound )
Broken libpulse-browse0:amd64 Depends on libpulse0 [ amd64 ] < 1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1 -> 1:1.0-0ubuntu3 > ( libs ) (= 1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1)
  Considering libpulse0:amd64 129 as a solution to libpulse-browse0:amd64 -1
  Removing libpulse-browse0:amd64 rather than change libpulse0:amd64
Investigating (0) tsclient [ amd64 ] < 0.150-4ubuntu2 > ( gnome )
Broken tsclient:amd64 Depends on libpanel-applet2-0 [ amd64 ] < 1:2.32.1-0ubuntu6.5 > ( libs ) (>= 2.26.0)
  Considering libpanel-applet2-0:amd64 11 as a solution to tsclient:amd64 -1
  Removing tsclient:amd64 rather than change libpanel-applet2-0:amd64
Investigating (0) libperl5.10 [ amd64 ] < 5.10.1-17ubuntu4.1 > ( libs )
Broken libperl5.10:amd64 Depends on perl-base [ amd64 ] < 5.10.1-17ubuntu4.1 -> 5.12.4-4 > ( perl ) (= 5.10.1-17ubuntu4.1)
  Considering perl-base:amd64 5362 as a solution to libperl5.10:amd64 -1
  Removing libperl5.10:amd64 rather than change perl-base:amd64
Investigating (0) lib32v4l-0 [ amd64 ] < 0.8.3-1 > ( libs )
Broken lib32v4l-0:amd64 Depends on libv4l-0 [ amd64 ] < 0.8.3-1 -> 0.8.5-3ubuntu1 > ( libs ) (= 0.8.3-1)
  Considering libv4l-0:amd64 37 as a solution to lib32v4l-0:amd64 -1
  Removing lib32v4l-0:amd64 rather than change libv4l-0:amd64
Investigating (0) gir1.2-panelapplet-3.0 [ amd64 ] < 1:2.32.1-0ubuntu6.5 > ( gnome )
Broken gir1.2-panelapplet-3.0:amd64 Depends on libpanel-applet-3-0 [ amd64 ] < 1:2.32.1-0ubuntu6.5 > ( libs )
  Considering libpanel-applet-3-0:amd64 12 as a solution to gir1.2-panelapplet-3.0:amd64 -1
  Removing gir1.2-panelapplet-3.0:amd64 rather than change libpanel-applet-3-0:amd64
Investigating (0) ia32-libs-multiarch [ i386 ] < none -> 20090808ubuntu26 > ( universe/libs )
Broken ia32-libs-multiarch:i386 Depends on libqt4-opengl [ i386 ] < none -> 4:4.7.4-0ubuntu8 > ( libs )
  Considering libqt4-opengl:i386 2 as a solution to ia32-libs-multiarch:i386 -2
  Holding Back ia32-libs-multiarch:i386 rather than change libqt4-opengl:i386
Investigating (0) libreadline5-dev [ amd64 ] < 5.2-7build1 > ( libdevel )
Broken libreadline5-dev:amd64 Depends on libreadline5 [ amd64 ] < 5.2-7build1 -> 5.2-9ubuntu1 > ( libs ) (= 5.2-7build1)
  Considering libreadline5:amd64 3 as a solution to libreadline5-dev:amd64 -2
  Removing libreadline5-dev:amd64 rather than change libreadline5:amd64
Investigating (0) gens [ i386 ] < 2.15.5 > ( unknown )
Broken gens:i386 Depends on libgl1-mesa [ i386 ] < none > ( none )
  Removing gens:i386 because I can't find libgl1-mesa:i386
Broken gens:i386 Depends on libgl1 [ i386 ] < none > ( none )
  Considering libgl1-mesa-swx11:i386 0 as a solution to gens:i386 -2
  Or group remove for gens:i386
Broken gens:i386 Depends on libgl1-mesa-glx [ i386 ] < none -> 7.11-0ubuntu3 > ( libs )
  Considering libgl1-mesa-glx:i386 6 as a solution to gens:i386 -2
  Try Installing libgl1-mesa-glx [ i386 ] < none -> 7.11-0ubuntu3 > ( libs ) before changing gens:i386
    Installing libdrm2 as Depends of libgl1-mesa-glx
    Installing libglapi-mesa as Depends of libgl1-mesa-glx
    Installing libgl1-mesa-dri as Recommends of libgl1-mesa-glx
      Installing libdrm-intel1 as Depends of libgl1-mesa-dri
        Installing libpciaccess0 as Depends of libdrm-intel1
      Installing libdrm-nouveau1a as Depends of libgl1-mesa-dri
      Installing libdrm-radeon1 as Depends of libgl1-mesa-dri
Broken gens:i386 Depends on libgl1 [ i386 ] < none > ( none )
  Considering libgl1-mesa-swx11:i386 0 as a solution to gens:i386 -2
  Or group remove for gens:i386
Broken gens:i386 Depends on libsdl1.2debian [ i386 ] < none -> 1.2.14-6.1ubuntu4 > ( libs ) (>= 1.2.10-1)
  Considering libsdl1.2debian:i386 1 as a solution to gens:i386 -2
  Removing gens:i386 rather than change libsdl1.2debian:i386
Investigating (0) andyetitmoves [ amd64 ] < 1.2.0 > ( games )
Broken andyetitmoves:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to andyetitmoves:amd64 -2
Broken andyetitmoves:amd64 Depends on nvidia-glx [ amd64 ] < none > ( none )
Broken andyetitmoves:amd64 Depends on fglrx-glx [ amd64 ] < none > ( none )
  Or group remove for andyetitmoves:amd64
Investigating (1) xserver-xorg-core [ amd64 ] < 2:1.10.3.902+git20110815+server-1.10-branch.4597f201-0ubuntu0sarvatt~natty -> 2:1.10.4-1ubuntu4 > ( x11 )
Broken xserver-xorg-core:amd64 Depends on libdrm2 [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libs ) (>= 2.3.1)
  Considering libdrm2:amd64 136 as a solution to xserver-xorg-core:amd64 59
  Removing xserver-xorg-core:amd64 rather than change libdrm2:amd64
Investigating (1) x11-utils [ amd64 ] < 7.6+1 -> 7.6+3 > ( x11 )
Broken x11-utils:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to x11-utils:amd64 50
Broken x11-utils:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to x11-utils:amd64 50
  Or group remove for x11-utils:amd64
Investigating (1) libglu1-mesa [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
Broken libglu1-mesa:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to libglu1-mesa:amd64 50
Broken libglu1-mesa:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to libglu1-mesa:amd64 50
  Or group remove for libglu1-mesa:amd64
Investigating (1) libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.0-0ubuntu4.1 > ( libs )
Broken libgnome-desktop-3-2:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to libgnome-desktop-3-2:amd64 46
  Holding Back libgnome-desktop-3-2:amd64 rather than change libgl1-mesa-glx:amd64
Broken libgnome-desktop-3-2:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to libgnome-desktop-3-2:amd64 46
  Holding Back libgnome-desktop-3-2:amd64 rather than change libgl1:amd64
  Or group keep for libgnome-desktop-3-2:amd64
Investigating (1) gnome-settings-daemon [ amd64 ] < 2.32.1-0ubuntu13.1 -> 3.2.0-0ubuntu5 > ( gnome )
Broken gnome-settings-daemon:amd64 Depends on libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.0-0ubuntu4.1 > ( libs ) (>= 3.1.5)
  Considering libgnome-desktop-3-2:amd64 46 as a solution to gnome-settings-daemon:amd64 35
  Holding Back gnome-settings-daemon:amd64 rather than change libgnome-desktop-3-2:amd64
Investigating (1) libqt4-opengl [ amd64 ] < 4:4.7.2-0ubuntu6.3 -> 4:4.7.4-0ubuntu8 > ( libs )
Broken libqt4-opengl:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to libqt4-opengl:amd64 30
Broken libqt4-opengl:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to libqt4-opengl:amd64 30
  Or group remove for libqt4-opengl:amd64
Investigating (1) gnome-session [ amd64 ] < 2.32.1-0ubuntu20 -> 3.2.0-0ubuntu3 > ( gnome )
Broken gnome-session:amd64 Depends on gnome-settings-daemon [ amd64 ] < 2.32.1-0ubuntu13.1 -> 3.2.0-0ubuntu5 > ( gnome ) (>= 3.0)
  Considering gnome-settings-daemon:amd64 35 as a solution to gnome-session:amd64 23
  Removing gnome-session:amd64 rather than change gnome-settings-daemon:amd64
Investigating (1) plymouth [ amd64 ] < 0.8.2-2ubuntu23 -> 0.8.2-2ubuntu28 > ( x11 )
Broken plymouth:amd64 Depends on libdrm-intel1 [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libs ) (>= 2.4.9)
  Considering libdrm-intel1:amd64 18 as a solution to plymouth:amd64 23
  Added libdrm-intel1:amd64 to the remove list
Broken plymouth:amd64 Depends on libdrm-nouveau1a [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libs ) (>= 2.4.23)
  Considering libdrm-nouveau1a:amd64 17 as a solution to plymouth:amd64 23
  Added libdrm-nouveau1a:amd64 to the remove list
Broken plymouth:amd64 Depends on libdrm-radeon1 [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libs ) (>= 2.4.17)
  Considering libdrm-radeon1:amd64 17 as a solution to plymouth:amd64 23
  Added libdrm-radeon1:amd64 to the remove list
Broken plymouth:amd64 Depends on libdrm2 [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libs ) (>= 2.4.3)
  Considering libdrm2:amd64 136 as a solution to plymouth:amd64 23
  Removing plymouth:amd64 rather than change libdrm2:amd64
Investigating (1) gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.0-0ubuntu6 > ( gnome )
Broken gnome-control-center:amd64 Depends on libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.0-0ubuntu4.1 > ( libs ) (>= 3.1.2)
  Considering libgnome-desktop-3-2:amd64 46 as a solution to gnome-control-center:amd64 22
  Removing gnome-control-center:amd64 rather than change libgnome-desktop-3-2:amd64
Investigating (1) indicator-applet [ amd64 ] < 0.4.12-0ubuntu1 > ( gnome )
Broken indicator-applet:amd64 Depends on libpanel-applet-3-0 [ amd64 ] < 1:2.32.1-0ubuntu6.5 > ( libs )
  Considering libpanel-applet-3-0:amd64 12 as a solution to indicator-applet:amd64 20
  Added libpanel-applet-3-0:amd64 to the remove list
  Fixing indicator-applet:amd64 via keep of libpanel-applet-3-0:amd64
Investigating (1) libevolution [ amd64 ] < 2.32.2-0ubuntu7 -> 3.2.0-0ubuntu2 > ( gnome )
Broken libevolution:amd64 Depends on libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.0-0ubuntu4.1 > ( libs ) (>= 2.91.5)
  Considering libgnome-desktop-3-2:amd64 46 as a solution to libevolution:amd64 18
  Holding Back libevolution:amd64 rather than change libgnome-desktop-3-2:amd64
Investigating (1) gnome-panel [ amd64 ] < 1:2.32.1-0ubuntu6.5 -> 1:3.2.0-0ubuntu1 > ( universe/gnome )
Broken gnome-panel:amd64 Depends on libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.0-0ubuntu4.1 > ( libs ) (>= 2.91.5)
  Considering libgnome-desktop-3-2:amd64 46 as a solution to gnome-panel:amd64 18
  Removing gnome-panel:amd64 rather than change libgnome-desktop-3-2:amd64
Investigating (1) gnome-control-center-data [ amd64 ] < none -> 1:3.2.0-0ubuntu6 > ( gnome )
Broken gnome-control-center-data:amd64 Breaks on gnome-settings-daemon [ amd64 ] < 2.32.1-0ubuntu13.1 -> 3.2.0-0ubuntu5 > ( gnome ) (< 3.0~)
  Considering gnome-settings-daemon:amd64 35 as a solution to gnome-control-center-data:amd64 17
  Holding Back gnome-control-center-data:amd64 rather than change gnome-settings-daemon:amd64
Investigating (1) gnome-session-bin [ amd64 ] < 2.32.1-0ubuntu20 -> 3.2.0-0ubuntu3 > ( gnome )
Broken gnome-session-bin:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to gnome-session-bin:amd64 16
Broken gnome-session-bin:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to gnome-session-bin:amd64 16
  Or group remove for gnome-session-bin:amd64
Investigating (1) nautilus [ amd64 ] < 1:2.32.2.1-0ubuntu13 -> 1:3.2.0-0ubuntu5 > ( gnome )
Broken nautilus:amd64 Depends on libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.0-0ubuntu4.1 > ( libs ) (>= 3.0.0)
  Considering libgnome-desktop-3-2:amd64 46 as a solution to nautilus:amd64 15
  Removing nautilus:amd64 rather than change libgnome-desktop-3-2:amd64
Investigating (1) plymouth-theme-ubuntu-text [ amd64 ] < 0.8.2-2ubuntu23 -> 0.8.2-2ubuntu28 > ( x11 )
Broken plymouth-theme-ubuntu-text:amd64 Depends on plymouth [ amd64 ] < 0.8.2-2ubuntu23 -> 0.8.2-2ubuntu28 > ( x11 )
  Considering plymouth:amd64 23 as a solution to plymouth-theme-ubuntu-text:amd64 15
  Removing plymouth-theme-ubuntu-text:amd64 rather than change plymouth:amd64
Investigating (1) compiz-plugins-default [ amd64 ] < none -> 1:0.9.6+bzr20110929-0ubuntu3 > ( x11 )
Broken compiz-plugins-default:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to compiz-plugins-default:amd64 14
  Holding Back compiz-plugins-default:amd64 rather than change libgl1-mesa-glx:amd64
Broken compiz-plugins-default:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to compiz-plugins-default:amd64 14
  Holding Back compiz-plugins-default:amd64 rather than change libgl1:amd64
  Or group keep for compiz-plugins-default:amd64
Investigating (1) xserver-xorg [ amd64 ] < 1:7.6+4ubuntu3.1 -> 1:7.6+7ubuntu7 > ( x11 )
Broken xserver-xorg:amd64 Depends on xserver-xorg-core [ amd64 ] < 2:1.10.3.902+git20110815+server-1.10-branch.4597f201-0ubuntu0sarvatt~natty -> 2:1.10.4-1ubuntu4 > ( x11 ) (>= 2:1.9.99.901+git20110131)
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg:amd64 11
  Removing xserver-xorg:amd64 rather than change xserver-xorg-core:amd64
Investigating (1) libglew1.5 [ amd64 ] < 1.5.7.is.1.5.2-1ubuntu2 -> 1.5.7.is.1.5.2-1ubuntu4 > ( libs )
Broken libglew1.5:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to libglew1.5:amd64 10
Broken libglew1.5:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to libglew1.5:amd64 10
  Or group remove for libglew1.5:amd64
Investigating (1) gnome-applets [ amd64 ] < 2.32.1.1-0ubuntu5 -> 3.2.0-0ubuntu1 > ( universe/gnome )
Broken gnome-applets:amd64 Depends on gnome-panel [ amd64 ] < 1:2.32.1-0ubuntu6.5 -> 1:3.2.0-0ubuntu1 > ( universe/gnome ) (>= 2.91.91)
  Considering gnome-panel:amd64 18 as a solution to gnome-applets:amd64 9
  Removing gnome-applets:amd64 rather than change gnome-panel:amd64
Investigating (1) libnux-1.0-0 [ amd64 ] < none -> 1.14.0-0ubuntu1 > ( libs )
Broken libnux-1.0-0:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to libnux-1.0-0:amd64 9
  Holding Back libnux-1.0-0:amd64 rather than change libgl1-mesa-glx:amd64
Broken libnux-1.0-0:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to libnux-1.0-0:amd64 9
  Holding Back libnux-1.0-0:amd64 rather than change libgl1:amd64
  Or group keep for libnux-1.0-0:amd64
Broken libnux-1.0-0:amd64 Depends on libglew1.5 [ amd64 ] < 1.5.7.is.1.5.2-1ubuntu2 -> 1.5.7.is.1.5.2-1ubuntu4 > ( libs ) (>= 1.5.7.is.1.5.2)
  Considering libglew1.5:amd64 10 as a solution to libnux-1.0-0:amd64 9
  Holding Back libnux-1.0-0:amd64 rather than change libglew1.5:amd64
Investigating (1) freeglut3 [ amd64 ] < 2.6.0-1ubuntu2 > ( libs )
Broken freeglut3:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to freeglut3:amd64 9
Broken freeglut3:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to freeglut3:amd64 9
  Or group remove for freeglut3:amd64
Investigating (1) gnome-session-fallback [ amd64 ] < none -> 3.2.0-0ubuntu3 > ( universe/gnome )
Broken gnome-session-fallback:amd64 Depends on gnome-settings-daemon [ amd64 ] < 2.32.1-0ubuntu13.1 -> 3.2.0-0ubuntu5 > ( gnome ) (>= 3.0)
  Considering gnome-settings-daemon:amd64 35 as a solution to gnome-session-fallback:amd64 8
  Holding Back gnome-session-fallback:amd64 rather than change gnome-settings-daemon:amd64
Investigating (1) libunity-core-4.0-4 [ amd64 ] < none -> 4.22.0-0ubuntu3 > ( libs )
Broken libunity-core-4.0-4:amd64 Depends on libnux-1.0-0 [ amd64 ] < none -> 1.14.0-0ubuntu1 > ( libs ) (>= 1.8.0-0)
  Considering libnux-1.0-0:amd64 9 as a solution to libunity-core-4.0-4:amd64 7
  Holding Back libunity-core-4.0-4:amd64 rather than change libnux-1.0-0:amd64
Investigating (1) xserver-xorg-input-evdev [ amd64 ] < 1:2.6.0+git20110408.68a6a18f-0ubuntu0sarvatt > ( x11 )
Broken xserver-xorg-input-evdev:amd64 Depends on xorg-input-abi-12 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-input-evdev:amd64 7
  Removing xserver-xorg-input-evdev:amd64 rather than change xorg-input-abi-12:amd64
Investigating (1) libglewmx1.5 [ amd64 ] < 1.5.7.is.1.5.2-1ubuntu2 -> 1.5.7.is.1.5.2-1ubuntu4 > ( libs )
Broken libglewmx1.5:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to libglewmx1.5:amd64 7
Broken libglewmx1.5:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to libglewmx1.5:amd64 7
  Or group remove for libglewmx1.5:amd64
Investigating (1) unity [ amd64 ] < 3.8.16-0ubuntu1~natty2 -> 4.22.0-0ubuntu3 > ( gnome )
Broken unity:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to unity:amd64 6
Broken unity:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to unity:amd64 6
  Or group remove for unity:amd64
Broken unity:amd64 Depends on libglew1.5 [ amd64 ] < 1.5.7.is.1.5.2-1ubuntu2 -> 1.5.7.is.1.5.2-1ubuntu4 > ( libs ) (>= 1.5.7.is.1.5.2)
  Considering libglew1.5:amd64 10 as a solution to unity:amd64 6
  Removing unity:amd64 rather than change libglew1.5:amd64
 Try to Re-Instate (1) evolution-plugins:amd64
Investigating (1) xserver-xorg-input-all [ amd64 ] < 1:7.6+4ubuntu3.1 -> 1:7.6+7ubuntu7 > ( x11 )
Broken xserver-xorg-input-all:amd64 Depends on xserver-xorg-input-evdev [ amd64 ] < 1:2.6.0+git20110408.68a6a18f-0ubuntu0sarvatt > ( x11 )
  Considering xserver-xorg-input-evdev:amd64 7 as a solution to xserver-xorg-input-all:amd64 6
  Removing xserver-xorg-input-all:amd64 rather than change xserver-xorg-input-evdev:amd64
Investigating (1) nautilus-sendto [ amd64 ] < 2.32.0-0ubuntu1.1 -> 3.0.1-0ubuntu1 > ( gnome )
Broken nautilus-sendto:amd64 Depends on nautilus [ amd64 ] < 1:2.32.2.1-0ubuntu13 -> 1:3.2.0-0ubuntu5 > ( gnome ) (>= 1:2.91)
  Considering nautilus:amd64 15 as a solution to nautilus-sendto:amd64 6
  Holding Back nautilus-sendto:amd64 rather than change nautilus:amd64
Investigating (1) gnome-media [ amd64 ] < 2.32.0-0ubuntu7 -> 2.91.2-2ubuntu2 > ( gnome )
Broken gnome-media:amd64 Depends on x11-utils [ amd64 ] < 7.6+1 -> 7.6+3 > ( x11 )
  Considering x11-utils:amd64 50 as a solution to gnome-media:amd64 5
  Removing gnome-media:amd64 rather than change x11-utils:amd64
Investigating (1) libqt4-opengl-dev [ amd64 ] < 4:4.7.2-0ubuntu6.3 -> 4:4.7.4-0ubuntu8 > ( libdevel )
Broken libqt4-opengl-dev:amd64 Depends on libqt4-opengl [ amd64 ] < 4:4.7.2-0ubuntu6.3 -> 4:4.7.4-0ubuntu8 > ( libs ) (= 4:4.7.4-0ubuntu8)
  Considering libqt4-opengl:amd64 30 as a solution to libqt4-opengl-dev:amd64 5
  Removing libqt4-opengl-dev:amd64 rather than change libqt4-opengl:amd64
Investigating (1) libgl1-mesa-dev [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libdevel )
Broken libgl1-mesa-dev:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs ) (= 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty)
  Considering libgl1-mesa-glx:amd64 174 as a solution to libgl1-mesa-dev:amd64 5
  Removing libgl1-mesa-dev:amd64 rather than change libgl1-mesa-glx:amd64
Investigating (1) libfltk1.1 [ amd64 ] < 1.1.10-3 -> 1.1.10-7 > ( libs )
Broken libfltk1.1:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to libfltk1.1:amd64 5
Broken libfltk1.1:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to libfltk1.1:amd64 5
  Or group remove for libfltk1.1:amd64
Investigating (1) compiz-plugins-main-default [ amd64 ] < none -> 1:0.9.6-0ubuntu2 > ( x11 )
Broken compiz-plugins-main-default:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to compiz-plugins-main-default:amd64 5
  Holding Back compiz-plugins-main-default:amd64 rather than change libgl1-mesa-glx:amd64
Broken compiz-plugins-main-default:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to compiz-plugins-main-default:amd64 5
  Holding Back compiz-plugins-main-default:amd64 rather than change libgl1:amd64
  Or group keep for compiz-plugins-main-default:amd64
Broken compiz-plugins-main-default:amd64 Depends on libglu1-mesa [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libglu1-mesa:amd64 50 as a solution to compiz-plugins-main-default:amd64 5
  Holding Back compiz-plugins-main-default:amd64 rather than change libglu1-mesa:amd64
Broken compiz-plugins-main-default:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 50 as a solution to compiz-plugins-main-default:amd64 5
  Holding Back compiz-plugins-main-default:amd64 rather than change libglu1:amd64
  Or group keep for compiz-plugins-main-default:amd64
Investigating (1) libxine1-x [ amd64 ] < 1.1.19-2ubuntu5 -> 1.1.19-2ubuntu6 > ( libs )
Broken libxine1-x:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to libxine1-x:amd64 4
Broken libxine1-x:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to libxine1-x:amd64 4
  Or group remove for libxine1-x:amd64
Broken libxine1-x:amd64 Depends on libglu1-mesa [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libglu1-mesa:amd64 50 as a solution to libxine1-x:amd64 4
Broken libxine1-x:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 50 as a solution to libxine1-x:amd64 4
  Or group remove for libxine1-x:amd64
Investigating (1) flashplugin-installer [ amd64 ] < 11.0.1.152ubuntu0.11.04.1 -> 11.0.1.152ubuntu1 > ( multiverse/web )
Broken flashplugin-installer:amd64 Depends on flashplugin-downloader [ amd64 ] < none > ( none ) (>= 11.0.1.152ubuntu1)
  Considering flashplugin-downloader:i386 -1 as a solution to flashplugin-installer:amd64 4
  Holding Back flashplugin-installer:amd64 rather than change flashplugin-downloader:amd64
Investigating (1) indicator-datetime [ amd64 ] < 0.2.3-0ubuntu3 -> 0.3.0-0ubuntu3 > ( misc )
Broken indicator-datetime:amd64 Depends on gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.0-0ubuntu6 > ( gnome )
  Considering gnome-control-center:amd64 22 as a solution to indicator-datetime:amd64 4
  Holding Back indicator-datetime:amd64 rather than change gnome-control-center:amd64
Investigating (1) torcs [ amd64 ] < 1.3.1-5 -> 1.3.1-6 > ( universe/games )
Broken torcs:amd64 Depends on freeglut3 [ amd64 ] < 2.6.0-1ubuntu2 > ( libs )
  Considering freeglut3:amd64 9 as a solution to torcs:amd64 4
  Removing torcs:amd64 rather than change freeglut3:amd64
Investigating (1) xbase-clients [ amd64 ] < 1:7.6+4ubuntu3.1 -> 1:7.6+7ubuntu7 > ( x11 )
Broken xbase-clients:amd64 Depends on x11-utils [ amd64 ] < 7.6+1 -> 7.6+3 > ( x11 )
  Considering x11-utils:amd64 50 as a solution to xbase-clients:amd64 3
  Removing xbase-clients:amd64 rather than change x11-utils:amd64
Investigating (1) nvidia-cg-toolkit [ amd64 ] < 3.0.0007-0ubuntu1 > ( multiverse/libs )
Broken nvidia-cg-toolkit:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to nvidia-cg-toolkit:amd64 3
Broken nvidia-cg-toolkit:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to nvidia-cg-toolkit:amd64 3
  Or group remove for nvidia-cg-toolkit:amd64
Broken nvidia-cg-toolkit:amd64 Depends on libglu1-mesa [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libglu1-mesa:amd64 50 as a solution to nvidia-cg-toolkit:amd64 3
Broken nvidia-cg-toolkit:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 50 as a solution to nvidia-cg-toolkit:amd64 3
  Or group remove for nvidia-cg-toolkit:amd64
Investigating (1) libunity-2d-private0 [ amd64 ] < none -> 4.12.0-0ubuntu1 > ( libs )
Broken libunity-2d-private0:amd64 Depends on libnux-1.0-0 [ amd64 ] < none -> 1.14.0-0ubuntu1 > ( libs ) (>= 1.8.0-0)
  Considering libnux-1.0-0:amd64 9 as a solution to libunity-2d-private0:amd64 3
  Holding Back libunity-2d-private0:amd64 rather than change libnux-1.0-0:amd64
Investigating (1) compiz-plugins-main [ amd64 ] < 0.9.4+bzr20110527-0ubuntu1~natty1 -> 1:0.9.6-0ubuntu2 > ( x11 )
Broken compiz-plugins-main:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to compiz-plugins-main:amd64 3
Broken compiz-plugins-main:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to compiz-plugins-main:amd64 3
  Or group remove for compiz-plugins-main:amd64
Broken compiz-plugins-main:amd64 Depends on compiz-plugins-main-default [ amd64 ] < none -> 1:0.9.6-0ubuntu2 > ( x11 ) (= 1:0.9.6-0ubuntu2)
  Considering compiz-plugins-main-default:amd64 5 as a solution to compiz-plugins-main:amd64 3
  Removing compiz-plugins-main:amd64 rather than change compiz-plugins-main-default:amd64
Investigating (1) libwxgtk2.8-0 [ amd64 ] < 2.8.11.0-0ubuntu8.1 -> 2.8.11.0-0ubuntu10 > ( universe/libs )
Broken libwxgtk2.8-0:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to libwxgtk2.8-0:amd64 3
Broken libwxgtk2.8-0:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to libwxgtk2.8-0:amd64 3
  Or group remove for libwxgtk2.8-0:amd64
Investigating (1) libglu1-mesa-dev [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libdevel )
Broken libglu1-mesa-dev:amd64 Depends on libglu1-mesa [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs ) (= 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty)
  Considering libglu1-mesa:amd64 50 as a solution to libglu1-mesa-dev:amd64 3
  Removing libglu1-mesa-dev:amd64 rather than change libglu1-mesa:amd64
Investigating (1) libplib1 [ amd64 ] < 1.8.5-5 > ( universe/libs )
Broken libplib1:amd64 Depends on freeglut3 [ amd64 ] < 2.6.0-1ubuntu2 > ( libs )
  Considering freeglut3:amd64 9 as a solution to libplib1:amd64 3
  Removing libplib1:amd64 rather than change freeglut3:amd64
Investigating (1) libvisual-0.4-plugins [ amd64 ] < 0.4.0.dfsg.1-2ubuntu5 -> 0.4.0.dfsg.1-2ubuntu6 > ( sound )
Broken libvisual-0.4-plugins:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to libvisual-0.4-plugins:amd64 3
Broken libvisual-0.4-plugins:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to libvisual-0.4-plugins:amd64 3
  Or group remove for libvisual-0.4-plugins:amd64
Broken libvisual-0.4-plugins:amd64 Depends on libglu1-mesa [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libglu1-mesa:amd64 50 as a solution to libvisual-0.4-plugins:amd64 3
Broken libvisual-0.4-plugins:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 50 as a solution to libvisual-0.4-plugins:amd64 3
  Or group remove for libvisual-0.4-plugins:amd64
Investigating (1) nux-tools [ amd64 ] < 0.9.48-0ubuntu1.1 -> 1.14.0-0ubuntu1 > ( x11 )
Broken nux-tools:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to nux-tools:amd64 3
Broken nux-tools:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to nux-tools:amd64 3
  Or group remove for nux-tools:amd64
Investigating (1) compiz [ amd64 ] < 1:0.9.4+bzr20110606-0ubuntu1~natty2 -> 1:0.9.6+bzr20110929-0ubuntu3 > ( x11 )
Broken compiz:amd64 Depends on compiz-plugins-default [ amd64 ] < none -> 1:0.9.6+bzr20110929-0ubuntu3 > ( x11 ) (>= 1:0.9.6+bzr20110929-0ubuntu3)
  Considering compiz-plugins-default:amd64 14 as a solution to compiz:amd64 3
  Removing compiz:amd64 rather than change compiz-plugins-default:amd64
Investigating (1) yabause-qt [ amd64 ] < 0.9.10-1 -> 0.9.10-2 > ( universe/utils )
Broken yabause-qt:amd64 Depends on freeglut3 [ amd64 ] < 2.6.0-1ubuntu2 > ( libs )
  Considering freeglut3:amd64 9 as a solution to yabause-qt:amd64 2
  Removing yabause-qt:amd64 rather than change freeglut3:amd64
Investigating (1) xserver-xorg-video-openchrome [ amd64 ] < 1:0.2.904+svn916-1ubuntu0sarvatt -> 1:0.2.904+svn920-1 > ( x11 )
Broken xserver-xorg-video-openchrome:amd64 Depends on libdrm2 [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libs ) (>= 2.3.1)
  Considering libdrm2:amd64 136 as a solution to xserver-xorg-video-openchrome:amd64 2
  Removing xserver-xorg-video-openchrome:amd64 rather than change libdrm2:amd64
Investigating (1) kdenlive [ amd64 ] < 0.7.8-2 -> 0.8-4build1 > ( universe/graphics )
Broken kdenlive:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to kdenlive:amd64 2
Broken kdenlive:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to kdenlive:amd64 2
  Or group remove for kdenlive:amd64
Broken kdenlive:amd64 Depends on libglu1-mesa [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libglu1-mesa:amd64 50 as a solution to kdenlive:amd64 2
Broken kdenlive:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 50 as a solution to kdenlive:amd64 2
  Or group remove for kdenlive:amd64
Broken kdenlive:amd64 Depends on libqt4-opengl [ amd64 ] < 4:4.7.2-0ubuntu6.3 -> 4:4.7.4-0ubuntu8 > ( libs ) (>= 4:4.5.3)
  Considering libqt4-opengl:amd64 30 as a solution to kdenlive:amd64 2
  Removing kdenlive:amd64 rather than change libqt4-opengl:amd64
Investigating (1) libcegui-mk2-1 [ amd64 ] < 0.6.2-5ubuntu3 -> 0.6.2-5.1 > ( universe/libs )
Broken libcegui-mk2-1:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to libcegui-mk2-1:amd64 2
Broken libcegui-mk2-1:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to libcegui-mk2-1:amd64 2
  Or group remove for libcegui-mk2-1:amd64
Broken libcegui-mk2-1:amd64 Depends on libglu1-mesa [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libglu1-mesa:amd64 50 as a solution to libcegui-mk2-1:amd64 2
Broken libcegui-mk2-1:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 50 as a solution to libcegui-mk2-1:amd64 2
  Or group remove for libcegui-mk2-1:amd64
Investigating (1) kde-workspace-bin [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
Broken kde-workspace-bin:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to kde-workspace-bin:amd64 2
  Holding Back kde-workspace-bin:amd64 rather than change libgl1-mesa-glx:amd64
Broken kde-workspace-bin:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to kde-workspace-bin:amd64 2
  Holding Back kde-workspace-bin:amd64 rather than change libgl1:amd64
  Or group keep for kde-workspace-bin:amd64
Broken kde-workspace-bin:amd64 Depends on x11-utils [ amd64 ] < 7.6+1 -> 7.6+3 > ( x11 )
  Considering x11-utils:amd64 50 as a solution to kde-workspace-bin:amd64 2
  Holding Back kde-workspace-bin:amd64 rather than change x11-utils:amd64
Investigating (1) audacity [ amd64 ] < 1.3.13-3ubuntu1 -> 1.3.13-5 > ( universe/sound )
Broken audacity:amd64 Depends on libwxgtk2.8-0 [ amd64 ] < 2.8.11.0-0ubuntu8.1 -> 2.8.11.0-0ubuntu10 > ( universe/libs ) (>= 2.8.11.0)
  Considering libwxgtk2.8-0:amd64 3 as a solution to audacity:amd64 2
  Removing audacity:amd64 rather than change libwxgtk2.8-0:amd64
Investigating (1) xserver-xorg-video-qxl [ amd64 ] < 0.0.12-1ubuntu4 -> 0.0.14-1 > ( x11 )
Broken xserver-xorg-video-qxl:amd64 Depends on xorg-video-abi-10 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-video-qxl:amd64 2
  Removing xserver-xorg-video-qxl:amd64 rather than change xorg-video-abi-10:amd64
Investigating (1) plymouth-label [ amd64 ] < 0.8.2-2ubuntu23 -> 0.8.2-2ubuntu28 > ( x11 )
Broken plymouth-label:amd64 Depends on plymouth [ amd64 ] < 0.8.2-2ubuntu23 -> 0.8.2-2ubuntu28 > ( x11 ) (= 0.8.2-2ubuntu28)
  Considering plymouth:amd64 23 as a solution to plymouth-label:amd64 2
  Removing plymouth-label:amd64 rather than change plymouth:amd64
Investigating (1) libqt4-gui [ amd64 ] < 4:4.7.2-0ubuntu6.3 -> 4:4.7.4-0ubuntu8 > ( libs )
Broken libqt4-gui:amd64 Depends on libqt4-opengl [ amd64 ] < 4:4.7.2-0ubuntu6.3 -> 4:4.7.4-0ubuntu8 > ( libs ) (= 4:4.7.4-0ubuntu8)
  Considering libqt4-opengl:amd64 30 as a solution to libqt4-gui:amd64 2
  Removing libqt4-gui:amd64 rather than change libqt4-opengl:amd64
Investigating (1) indicator-power [ amd64 ] < none -> 0.9-0ubuntu2 > ( gnome )
Broken indicator-power:amd64 Depends on gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.0-0ubuntu6 > ( gnome ) (>= 3.1)
  Considering gnome-control-center:amd64 22 as a solution to indicator-power:amd64 2
  Holding Back indicator-power:amd64 rather than change gnome-control-center:amd64
Investigating (1) libgtkglext1 [ amd64 ] < 1.2.0-1.1ubuntu1 -> 1.2.0-1.2fakesync1 > ( universe/libs )
Broken libgtkglext1:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to libgtkglext1:amd64 2
Broken libgtkglext1:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to libgtkglext1:amd64 2
  Or group remove for libgtkglext1:amd64
Broken libgtkglext1:amd64 Depends on libglu1-mesa [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libglu1-mesa:amd64 50 as a solution to libgtkglext1:amd64 2
Broken libgtkglext1:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 50 as a solution to libgtkglext1:amd64 2
  Or group remove for libgtkglext1:amd64
Investigating (1) compiz-gnome [ amd64 ] < 1:0.9.4+bzr20110606-0ubuntu1~natty2 -> 1:0.9.6+bzr20110929-0ubuntu3 > ( x11 )
Broken compiz-gnome:amd64 Depends on compiz-plugins-default [ amd64 ] < none -> 1:0.9.6+bzr20110929-0ubuntu3 > ( x11 ) (= 1:0.9.6+bzr20110929-0ubuntu3)
  Considering compiz-plugins-default:amd64 14 as a solution to compiz-gnome:amd64 2
  Removing compiz-gnome:amd64 rather than change compiz-plugins-default:amd64
Investigating (1) xserver-xorg-input-wacom [ amd64 ] < 1:0.10.11-0ubuntu4 -> 1:0.11.0-0ubuntu2 > ( x11 )
Broken xserver-xorg-input-wacom:amd64 Depends on xorg-input-abi-12 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-input-wacom:amd64 2
  Removing xserver-xorg-input-wacom:amd64 rather than change xorg-input-abi-12:amd64
Investigating (1) compiz-plugins [ amd64 ] < 1:0.9.4+bzr20110606-0ubuntu1~natty2 -> 1:0.9.6+bzr20110929-0ubuntu3 > ( x11 )
Broken compiz-plugins:amd64 Depends on compiz-plugins-default [ amd64 ] < none -> 1:0.9.6+bzr20110929-0ubuntu3 > ( x11 ) (= 1:0.9.6+bzr20110929-0ubuntu3)
  Considering compiz-plugins-default:amd64 14 as a solution to compiz-plugins:amd64 2
  Removing compiz-plugins:amd64 rather than change compiz-plugins-default:amd64
Investigating (1) radeontool [ amd64 ] < 1.6.1-1 > ( utils )
Broken radeontool:amd64 Depends on libpciaccess0 [ amd64 ] < 0.12.1+git20110826.7bfc4f80-0ubuntu0sarvatt~natty2 > ( libs )
  Considering libpciaccess0:amd64 51 as a solution to radeontool:amd64 2
  Removing radeontool:amd64 rather than change libpciaccess0:amd64
Investigating (1) xserver-xorg-input-synaptics [ amd64 ] < 1.3.99+git20110116.0e27ce3a-0ubuntu12.1 -> 1.4.1-1ubuntu2 > ( x11 )
Broken xserver-xorg-input-synaptics:amd64 Depends on xorg-input-abi-12 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-input-synaptics:amd64 2
  Removing xserver-xorg-input-synaptics:amd64 rather than change xorg-input-abi-12:amd64
Investigating (1) libdevil1c2 [ amd64 ] < 1.7.8-6build1 -> 1.7.8-6build2 > ( universe/libs )
Broken libdevil1c2:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to libdevil1c2:amd64 2
Broken libdevil1c2:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to libdevil1c2:amd64 2
  Or group remove for libdevil1c2:amd64
Broken libdevil1c2:amd64 Depends on libglu1-mesa [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libglu1-mesa:amd64 50 as a solution to libdevil1c2:amd64 2
Broken libdevil1c2:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 50 as a solution to libdevil1c2:amd64 2
  Or group remove for libdevil1c2:amd64
Investigating (1) python-opengl [ amd64 ] < 3.0.1~b2-1 > ( universe/python )
Broken python-opengl:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to python-opengl:amd64 2
Broken python-opengl:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to python-opengl:amd64 2
  Or group remove for python-opengl:amd64
Broken python-opengl:amd64 Depends on libglu1-mesa [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libglu1-mesa:amd64 50 as a solution to python-opengl:amd64 2
Broken python-opengl:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 50 as a solution to python-opengl:amd64 2
  Or group remove for python-opengl:amd64
Broken python-opengl:amd64 Depends on freeglut3 [ amd64 ] < 2.6.0-1ubuntu2 > ( libs )
  Considering freeglut3:amd64 9 as a solution to python-opengl:amd64 2
  Removing python-opengl:amd64 rather than change freeglut3:amd64
Investigating (1) libxine1 [ amd64 ] < 1.1.19-2ubuntu5 -> 1.1.19-2ubuntu6 > ( libs )
Broken libxine1:amd64 Depends on libxine1-x [ amd64 ] < 1.1.19-2ubuntu5 -> 1.1.19-2ubuntu6 > ( libs ) (= 1.1.19-2ubuntu6)
  Considering libxine1-x:amd64 4 as a solution to libxine1:amd64 2
  Removing libxine1:amd64 rather than change libxine1-x:amd64
Investigating (1) libva-x11-1 [ amd64 ] < 1.0.12-1~xorgedgers -> 1.0.12-2 > ( libs )
Broken libva-x11-1:amd64 Depends on libdrm2 [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libs ) (>= 2.3.1)
  Considering libdrm2:amd64 136 as a solution to libva-x11-1:amd64 1
  Removing libva-x11-1:amd64 rather than change libdrm2:amd64
Investigating (1) kipi-plugins [ amd64 ] < 1.9.0-1ubuntu2 -> 2:2.1.1-0ubuntu1 > ( universe/kde )
Broken kipi-plugins:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to kipi-plugins:amd64 1
Broken kipi-plugins:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to kipi-plugins:amd64 1
  Or group remove for kipi-plugins:amd64
Broken kipi-plugins:amd64 Depends on libqt4-opengl [ amd64 ] < 4:4.7.2-0ubuntu6.3 -> 4:4.7.4-0ubuntu8 > ( libs ) (>= 4:4.5.3)
  Considering libqt4-opengl:amd64 30 as a solution to kipi-plugins:amd64 1
  Removing kipi-plugins:amd64 rather than change libqt4-opengl:amd64
Investigating (1) xserver-xorg-video-ati [ amd64 ] < 1:6.14.99+git20110922.a6b2bd2d-0ubuntu0sarvatt~natty > ( x11 )
Broken xserver-xorg-video-ati:amd64 Depends on libpciaccess0 [ amd64 ] < 0.12.1+git20110826.7bfc4f80-0ubuntu0sarvatt~natty2 > ( libs )
  Considering libpciaccess0:amd64 51 as a solution to xserver-xorg-video-ati:amd64 1
  Removing xserver-xorg-video-ati:amd64 rather than change libpciaccess0:amd64
Investigating (1) glchess [ amd64 ] < 1:2.32.1-0ubuntu5 -> 1:3.2.0-0ubuntu1 > ( universe/games )
Broken glchess:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to glchess:amd64 1
  Holding Back glchess:amd64 rather than change libgl1-mesa-glx:amd64
Broken glchess:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to glchess:amd64 1
  Holding Back glchess:amd64 rather than change libgl1:amd64
  Or group keep for glchess:amd64
Broken glchess:amd64 Depends on libglu1-mesa [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libglu1-mesa:amd64 50 as a solution to glchess:amd64 1
  Holding Back glchess:amd64 rather than change libglu1-mesa:amd64
Broken glchess:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 50 as a solution to glchess:amd64 1
  Holding Back glchess:amd64 rather than change libglu1:amd64
  Or group keep for glchess:amd64
Investigating (1) nautilus-share [ amd64 ] < 0.7.2-14ubuntu1 -> 0.7.3-1ubuntu1 > ( gnome )
Broken nautilus-share:amd64 Depends on nautilus [ amd64 ] < 1:2.32.2.1-0ubuntu13 -> 1:3.2.0-0ubuntu5 > ( gnome ) (>= 2.10)
  Considering nautilus:amd64 15 as a solution to nautilus-share:amd64 1
  Removing nautilus-share:amd64 rather than change nautilus:amd64
Investigating (1) xserver-xorg-video-mga [ amd64 ] < 1:1.4.13.dsfg+git20110928.07792ef4-0ubuntu0sarvatt~natty > ( x11 )
Broken xserver-xorg-video-mga:amd64 Depends on xorg-video-abi-10 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-video-mga:amd64 1
  Removing xserver-xorg-video-mga:amd64 rather than change xorg-video-abi-10:amd64
Investigating (1) xserver-xorg-video-trident [ amd64 ] < 1:1.3.4+git20110526.de79bbea-0ubuntu0sarvatt~natty > ( x11 )
Broken xserver-xorg-video-trident:amd64 Depends on xorg-video-abi-10 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-video-trident:amd64 1
  Removing xserver-xorg-video-trident:amd64 rather than change xorg-video-abi-10:amd64
Investigating (1) compiz-plugins-extra [ amd64 ] < 0.9.4-0ubuntu3 -> 0.9.5.94-0ubuntu1 > ( universe/x11 )
Broken compiz-plugins-extra:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to compiz-plugins-extra:amd64 1
Broken compiz-plugins-extra:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to compiz-plugins-extra:amd64 1
  Or group remove for compiz-plugins-extra:amd64
Broken compiz-plugins-extra:amd64 Depends on libglu1-mesa [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libglu1-mesa:amd64 50 as a solution to compiz-plugins-extra:amd64 1
Broken compiz-plugins-extra:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 50 as a solution to compiz-plugins-extra:amd64 1
  Or group remove for compiz-plugins-extra:amd64
Investigating (1) xserver-xorg-video-sis [ amd64 ] < 1:0.10.3+git20110608.94f23a56-0ubuntu0sarvatt~natty > ( x11 )
Broken xserver-xorg-video-sis:amd64 Depends on xorg-video-abi-10 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-video-sis:amd64 1
  Removing xserver-xorg-video-sis:amd64 rather than change xorg-video-abi-10:amd64
Investigating (1) xserver-xorg-video-siliconmotion [ amd64 ] < 1:1.7.5+git20110526.087226bf-0ubuntu0sarvatt~natty > ( x11 )
Broken xserver-xorg-video-siliconmotion:amd64 Depends on xorg-video-abi-10 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-video-siliconmotion:amd64 1
  Removing xserver-xorg-video-siliconmotion:amd64 rather than change xorg-video-abi-10:amd64
Investigating (1) xserver-xorg-input-vmmouse [ amd64 ] < 1:12.7.0+git20110624.fd140bfb-0ubuntu0sarvatt~natty > ( x11 )
Broken xserver-xorg-input-vmmouse:amd64 Depends on xorg-input-abi-12 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-input-vmmouse:amd64 1
  Removing xserver-xorg-input-vmmouse:amd64 rather than change xorg-input-abi-12:amd64
Investigating (1) xserver-xorg-video-savage [ amd64 ] < 1:2.3.2+git20110928.f7516fd3-0ubuntu0sarvatt~natty > ( x11 )
Broken xserver-xorg-video-savage:amd64 Depends on xorg-video-abi-10 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-video-savage:amd64 1
  Removing xserver-xorg-video-savage:amd64 rather than change xorg-video-abi-10:amd64
Investigating (1) libkwineffects1abi2 [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( libs )
Broken libkwineffects1abi2:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to libkwineffects1abi2:amd64 1
  Holding Back libkwineffects1abi2:amd64 rather than change libgl1-mesa-glx:amd64
Broken libkwineffects1abi2:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to libkwineffects1abi2:amd64 1
  Holding Back libkwineffects1abi2:amd64 rather than change libgl1:amd64
  Or group keep for libkwineffects1abi2:amd64
Investigating (1) plymouth-theme-ubuntu-logo [ amd64 ] < 0.8.2-2ubuntu23 -> 0.8.2-2ubuntu28 > ( x11 )
Broken plymouth-theme-ubuntu-logo:amd64 Depends on plymouth [ amd64 ] < 0.8.2-2ubuntu23 -> 0.8.2-2ubuntu28 > ( x11 )
  Considering plymouth:amd64 23 as a solution to plymouth-theme-ubuntu-logo:amd64 1
  Removing plymouth-theme-ubuntu-logo:amd64 rather than change plymouth:amd64
Investigating (1) xserver-xorg-video-tdfx [ amd64 ] < 1:1.4.3+git20110526.0c4ffbec-0ubuntu0sarvatt~natty > ( x11 )
Broken xserver-xorg-video-tdfx:amd64 Depends on xorg-video-abi-10 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-video-tdfx:amd64 1
  Removing xserver-xorg-video-tdfx:amd64 rather than change xorg-video-abi-10:amd64
Investigating (1) unity-2d-spread [ amd64 ] < none -> 4.12.0-0ubuntu1 > ( x11 )
Broken unity-2d-spread:amd64 Depends on libunity-2d-private0 [ amd64 ] < none -> 4.12.0-0ubuntu1 > ( libs ) (= 4.12.0-0ubuntu1)
  Considering libunity-2d-private0:amd64 3 as a solution to unity-2d-spread:amd64 1
  Holding Back unity-2d-spread:amd64 rather than change libunity-2d-private0:amd64
Investigating (1) unity-2d-panel [ amd64 ] < none -> 4.12.0-0ubuntu1 > ( x11 )
Broken unity-2d-panel:amd64 Depends on libunity-2d-private0 [ amd64 ] < none -> 4.12.0-0ubuntu1 > ( libs ) (= 4.12.0-0ubuntu1)
  Considering libunity-2d-private0:amd64 3 as a solution to unity-2d-panel:amd64 1
  Holding Back unity-2d-panel:amd64 rather than change libunity-2d-private0:amd64
Investigating (1) xserver-xorg-video-intel [ amd64 ] < 2:2.16.0+git20111011.823a4272-0ubuntu0sarvatt~natty > ( x11 )
Broken xserver-xorg-video-intel:amd64 Depends on libdrm-intel1 [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libs ) (>= 2.4.23-3~)
  Considering libdrm-intel1:amd64 18 as a solution to xserver-xorg-video-intel:amd64 1
  Removing xserver-xorg-video-intel:amd64 rather than change libdrm-intel1:amd64
Investigating (1) kde-window-manager [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu5 > ( x11 )
Broken kde-window-manager:amd64 Depends on kde-workspace-bin [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
  Considering kde-workspace-bin:amd64 2 as a solution to kde-window-manager:amd64 1
  Removing kde-window-manager:amd64 rather than change kde-workspace-bin:amd64
Investigating (1) xserver-xorg-video-vmware [ amd64 ] < 1:11.0.99.901+git20111005.de70a1d0-0ubuntu0sarvatt~natty > ( x11 )
Broken xserver-xorg-video-vmware:amd64 Depends on libdrm2 [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libs ) (>= 2.3.1)
  Considering libdrm2:amd64 136 as a solution to xserver-xorg-video-vmware:amd64 1
  Removing xserver-xorg-video-vmware:amd64 rather than change libdrm2:amd64
Investigating (1) eog [ amd64 ] < 2.32.1-0ubuntu2 -> 3.2.0-0ubuntu1 > ( gnome )
Broken eog:amd64 Depends on libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.0-0ubuntu4.1 > ( libs ) (>= 2.91.5)
  Considering libgnome-desktop-3-2:amd64 46 as a solution to eog:amd64 1
  Holding Back eog:amd64 rather than change libgnome-desktop-3-2:amd64
Investigating (1) gdm [ amd64 ] < 2.32.1-0ubuntu3.2 -> 3.0.4-0ubuntu11 > ( universe/gnome )
Broken gdm:amd64 Depends on gnome-session-bin [ amd64 ] < 2.32.1-0ubuntu20 -> 3.2.0-0ubuntu3 > ( gnome )
  Considering gnome-session-bin:amd64 16 as a solution to gdm:amd64 1
  Removing gdm:amd64 rather than change gnome-session-bin:amd64
Investigating (1) xserver-xorg-video-vesa [ amd64 ] < 1:2.3.0+git20110526.0b02c685-0ubuntu0sarvatt~natty > ( x11 )
Broken xserver-xorg-video-vesa:amd64 Depends on xorg-video-abi-10 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-video-vesa:amd64 1
  Removing xserver-xorg-video-vesa:amd64 rather than change xorg-video-abi-10:amd64
Investigating (1) libglc0 [ amd64 ] < 0.7.2-4build1 > ( universe/libs )
Broken libglc0:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to libglc0:amd64 1
Broken libglc0:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to libglc0:amd64 1
  Or group remove for libglc0:amd64
Broken libglc0:amd64 Depends on libglewmx1.5 [ amd64 ] < 1.5.7.is.1.5.2-1ubuntu2 -> 1.5.7.is.1.5.2-1ubuntu4 > ( libs ) (>= 1.5.7.is.1.5.2)
  Considering libglewmx1.5:amd64 7 as a solution to libglc0:amd64 1
  Removing libglc0:amd64 rather than change libglewmx1.5:amd64
Investigating (1) xserver-xorg-video-s3 [ amd64 ] < 1:0.6.3+git20110526.381ace93-0ubuntu0sarvatt~natty > ( x11 )
Broken xserver-xorg-video-s3:amd64 Depends on xorg-video-abi-10 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-video-s3:amd64 1
  Removing xserver-xorg-video-s3:amd64 rather than change xorg-video-abi-10:amd64
Investigating (1) xserver-xorg-video-fbdev [ amd64 ] < 1:0.4.2+git20110526.a8721393-0ubuntu0sarvatt~natty > ( x11 )
Broken xserver-xorg-video-fbdev:amd64 Depends on xorg-video-abi-10 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-video-fbdev:amd64 1
  Removing xserver-xorg-video-fbdev:amd64 rather than change xorg-video-abi-10:amd64
Investigating (1) xserver-xorg-video-nouveau [ amd64 ] < 1:0.0.16+git20111011.d575a28a-0ubuntu0sarvatt~natty > ( x11 )
Broken xserver-xorg-video-nouveau:amd64 Depends on libdrm-nouveau1a [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libs ) (>= 2.4.23)
  Considering libdrm-nouveau1a:amd64 17 as a solution to xserver-xorg-video-nouveau:amd64 1
  Removing xserver-xorg-video-nouveau:amd64 rather than change libdrm-nouveau1a:amd64
Investigating (1) smc [ amd64 ] < 1.9-3ubuntu1 -> 1.9-4ubuntu1 > ( universe/games )
Broken smc:amd64 Depends on libcegui-mk2-1 [ amd64 ] < 0.6.2-5ubuntu3 -> 0.6.2-5.1 > ( universe/libs )
  Considering libcegui-mk2-1:amd64 2 as a solution to smc:amd64 1
  Removing smc:amd64 rather than change libcegui-mk2-1:amd64
Investigating (1) xserver-xorg-video-neomagic [ amd64 ] < 1:1.2.5+git20110526.a9d69f6d-0ubuntu0sarvatt~natty > ( x11 )
Broken xserver-xorg-video-neomagic:amd64 Depends on xorg-video-abi-10 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-video-neomagic:amd64 1
  Removing xserver-xorg-video-neomagic:amd64 rather than change xorg-video-abi-10:amd64
Investigating (1) unity-2d-places [ amd64 ] < none -> 4.12.0-0ubuntu1 > ( x11 )
Broken unity-2d-places:amd64 Depends on libunity-2d-private0 [ amd64 ] < none -> 4.12.0-0ubuntu1 > ( libs ) (= 4.12.0-0ubuntu1)
  Considering libunity-2d-private0:amd64 3 as a solution to unity-2d-places:amd64 1
  Holding Back unity-2d-places:amd64 rather than change libunity-2d-private0:amd64
Investigating (1) gnome-screensaver [ amd64 ] < 2.30.2-0ubuntu2 -> 3.2.0-0ubuntu1 > ( gnome )
Broken gnome-screensaver:amd64 Depends on libgnome-desktop-3-2 [ amd64 ] < none -> 3.2.0-0ubuntu4.1 > ( libs ) (>= 3.1.91)
  Considering libgnome-desktop-3-2:amd64 46 as a solution to gnome-screensaver:amd64 1
  Removing gnome-screensaver:amd64 rather than change libgnome-desktop-3-2:amd64
Investigating (1) xorg [ amd64 ] < 1:7.6+4ubuntu3.1 -> 1:7.6+7ubuntu7 > ( x11 )
Broken xorg:amd64 Depends on xserver-xorg [ amd64 ] < 1:7.6+4ubuntu3.1 -> 1:7.6+7ubuntu7 > ( x11 ) (>= 1:7.6+7ubuntu7)
  Considering xserver-xorg:amd64 11 as a solution to xorg:amd64 1
  Removing xorg:amd64 rather than change xserver-xorg:amd64
Investigating (1) xserver-xorg-video-sisusb [ amd64 ] < 1:0.9.4+git20110928.3dc05f64-0ubuntu0sarvatt~natty > ( x11 )
Broken xserver-xorg-video-sisusb:amd64 Depends on xorg-video-abi-10 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-video-sisusb:amd64 1
  Removing xserver-xorg-video-sisusb:amd64 rather than change xorg-video-abi-10:amd64
Investigating (1) xserver-xorg-video-cirrus [ amd64 ] < 1:1.3.2+git20110526.e4f80ffd-0ubuntu0sarvatt~natty > ( x11 )
Broken xserver-xorg-video-cirrus:amd64 Depends on xorg-video-abi-10 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-video-cirrus:amd64 1
  Removing xserver-xorg-video-cirrus:amd64 rather than change xorg-video-abi-10:amd64
Investigating (1) unity-2d-launcher [ amd64 ] < none -> 4.12.0-0ubuntu1 > ( x11 )
Broken unity-2d-launcher:amd64 Depends on libunity-2d-private0 [ amd64 ] < none -> 4.12.0-0ubuntu1 > ( libs ) (= 4.12.0-0ubuntu1)
  Considering libunity-2d-private0:amd64 3 as a solution to unity-2d-launcher:amd64 1
  Holding Back unity-2d-launcher:amd64 rather than change libunity-2d-private0:amd64
Investigating (1) xscreensaver-gl [ amd64 ] < 5.12-0ubuntu3 -> 5.14-1ubuntu1 > ( x11 )
Broken xscreensaver-gl:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to xscreensaver-gl:amd64 0
Broken xscreensaver-gl:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to xscreensaver-gl:amd64 0
  Or group remove for xscreensaver-gl:amd64
Broken xscreensaver-gl:amd64 Depends on libglu1-mesa [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libglu1-mesa:amd64 50 as a solution to xscreensaver-gl:amd64 0
Broken xscreensaver-gl:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 50 as a solution to xscreensaver-gl:amd64 0
  Or group remove for xscreensaver-gl:amd64
Investigating (1) intel-gpu-tools [ amd64 ] < 1.0.2+git20110729+3b10b7b-0ubuntu1~edgers~natty > ( x11 )
Broken intel-gpu-tools:amd64 Depends on libdrm-intel1 [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libs ) (>= 2.4.23-3~)
  Considering libdrm-intel1:amd64 18 as a solution to intel-gpu-tools:amd64 0
  Removing intel-gpu-tools:amd64 rather than change libdrm-intel1:amd64
Investigating (1) gnome-games [ amd64 ] < 1:2.32.1-0ubuntu5 -> 1:3.2.0-0ubuntu1 > ( universe/gnome )
Broken gnome-games:amd64 Depends on glchess [ amd64 ] < 1:2.32.1-0ubuntu5 -> 1:3.2.0-0ubuntu1 > ( universe/games ) (>= 1:3.2.0-0ubuntu1)
  Considering glchess:amd64 1 as a solution to gnome-games:amd64 0
  Holding Back gnome-games:amd64 rather than change glchess:amd64
Investigating (1) gdm-guest-session [ amd64 ] < 0.24 -> 0.27 > ( universe/gnome )
Broken gdm-guest-session:amd64 Depends on gdm [ amd64 ] < 2.32.1-0ubuntu3.2 -> 3.0.4-0ubuntu11 > ( universe/gnome ) (>= 2.30.0-0ubuntu5)
  Considering gdm:amd64 1 as a solution to gdm-guest-session:amd64 0
  Removing gdm-guest-session:amd64 rather than change gdm:amd64
Investigating (1) xserver-xorg-video-mach64 [ amd64 ] < 6.9.0+git20110526.ef55d1f1-0ubuntu0sarvatt~natty > ( x11 )
Broken xserver-xorg-video-mach64:amd64 Depends on xorg-video-abi-10 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-video-mach64:amd64 0
  Removing xserver-xorg-video-mach64:amd64 rather than change xorg-video-abi-10:amd64
Investigating (1) smc-music [ amd64 ] < 1.9-3ubuntu1 -> 1.9-4ubuntu1 > ( universe/games )
Broken smc-music:amd64 Depends on smc [ amd64 ] < 1.9-3ubuntu1 -> 1.9-4ubuntu1 > ( universe/games ) (>= 1.9-4ubuntu1)
  Considering smc:amd64 1 as a solution to smc-music:amd64 0
  Removing smc-music:amd64 rather than change smc:amd64
Investigating (1) driconf [ amd64 ] < 0.9.1-2ubuntu1 > ( universe/x11 )
Broken driconf:amd64 Depends on xdriinfo [ amd64 ] < none > ( none )
Broken driconf:amd64 Depends on xbase-clients [ amd64 ] < 1:7.6+4ubuntu3.1 -> 1:7.6+7ubuntu7 > ( x11 ) (> 6.8.0)
  Considering xbase-clients:amd64 3 as a solution to driconf:amd64 0
  Or group remove for driconf:amd64
Investigating (1) libwxgtk2.8-dev [ amd64 ] < 2.8.11.0-0ubuntu8.1 -> 2.8.11.0-0ubuntu10 > ( universe/libdevel )
Broken libwxgtk2.8-dev:amd64 Depends on libwxgtk2.8-0 [ amd64 ] < 2.8.11.0-0ubuntu8.1 -> 2.8.11.0-0ubuntu10 > ( universe/libs ) (= 2.8.11.0-0ubuntu10)
  Considering libwxgtk2.8-0:amd64 3 as a solution to libwxgtk2.8-dev:amd64 0
  Removing libwxgtk2.8-dev:amd64 rather than change libwxgtk2.8-0:amd64
Investigating (1) mupen64plus [ amd64 ] < 1.5+dfsg1-13 -> 1.5+dfsg1-16 > ( universe/games )
Broken mupen64plus:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to mupen64plus:amd64 0
Broken mupen64plus:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to mupen64plus:amd64 0
  Or group remove for mupen64plus:amd64
Broken mupen64plus:amd64 Depends on libglu1-mesa [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libglu1-mesa:amd64 50 as a solution to mupen64plus:amd64 0
Broken mupen64plus:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 50 as a solution to mupen64plus:amd64 0
  Or group remove for mupen64plus:amd64
Investigating (1) libsdl1.2-dev [ amd64 ] < 1.2.14-6.1ubuntu3 -> 1.2.14-6.1ubuntu4 > ( libdevel )
Broken libsdl1.2-dev:amd64 Depends on libglu1-mesa-dev [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libdevel )
  Considering libglu1-mesa-dev:amd64 3 as a solution to libsdl1.2-dev:amd64 0
  Removing libsdl1.2-dev:amd64 rather than change libglu1-mesa-dev:amd64
Investigating (1) dgen [ amd64 ] < 1.23-11 > ( multiverse/otherosfs )
Broken dgen:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to dgen:amd64 0
Broken dgen:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to dgen:amd64 0
  Or group remove for dgen:amd64
Investigating (1) vbaexpress [ amd64 ] < 1.2-0ubuntu3 > ( universe/games )
Broken vbaexpress:amd64 Depends on libfltk1.1 [ amd64 ] < 1.1.10-3 -> 1.1.10-7 > ( libs ) (>= 1.1.7-2)
  Considering libfltk1.1:amd64 5 as a solution to vbaexpress:amd64 0
  Removing vbaexpress:amd64 rather than change libfltk1.1:amd64
Investigating (1) xserver-xorg-video-r128 [ amd64 ] < 6.8.1+git20110526.3de85360-0ubuntu0sarvatt~natty > ( x11 )
Broken xserver-xorg-video-r128:amd64 Depends on xorg-video-abi-10 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-video-r128:amd64 0
  Removing xserver-xorg-video-r128:amd64 rather than change xorg-video-abi-10:amd64
Investigating (1) libdrm-dev [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libdevel )
Broken libdrm-dev:amd64 Depends on libdrm2 [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libs ) (= 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty)
  Considering libdrm2:amd64 136 as a solution to libdrm-dev:amd64 0
  Removing libdrm-dev:amd64 rather than change libdrm2:amd64
Investigating (1) digikam [ amd64 ] < 2:1.9.0-1ubuntu1 -> 2:2.1.1-0ubuntu1 > ( universe/graphics )
Broken digikam:amd64 Depends on kipi-plugins [ amd64 ] < 1.9.0-1ubuntu2 -> 2:2.1.1-0ubuntu1 > ( universe/kde )
  Considering kipi-plugins:amd64 1 as a solution to digikam:amd64 0
  Removing digikam:amd64 rather than change kipi-plugins:amd64
Investigating (1) kde-workspace [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
Broken kde-workspace:amd64 Depends on kde-workspace-bin [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde ) (>= 4:4.7.1-0ubuntu5)
  Considering kde-workspace-bin:amd64 2 as a solution to kde-workspace:amd64 0
  Holding Back kde-workspace:amd64 rather than change kde-workspace-bin:amd64
Investigating (1) xdiagnose [ amd64 ] < none -> 1.6 > ( python )
Broken xdiagnose:amd64 Depends on intel-gpu-tools [ amd64 ] < 1.0.2+git20110729+3b10b7b-0ubuntu1~edgers~natty > ( x11 )
  Considering intel-gpu-tools:amd64 0 as a solution to xdiagnose:amd64 0
  Holding Back xdiagnose:amd64 rather than change intel-gpu-tools:amd64
 Try to Re-Instate (1) wine:amd64
Investigating (1) vlc [ amd64 ] < 1.1.9-1ubuntu1.3 -> 1.1.11-2build2 > ( universe/graphics )
Broken vlc:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to vlc:amd64 0
Broken vlc:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to vlc:amd64 0
  Or group remove for vlc:amd64
Broken vlc:amd64 Depends on libva-x11-1 [ amd64 ] < 1.0.12-1~xorgedgers -> 1.0.12-2 > ( libs ) (> 1.0.12~)
  Considering libva-x11-1:amd64 1 as a solution to vlc:amd64 0
  Removing vlc:amd64 rather than change libva-x11-1:amd64
Investigating (1) kinfocenter [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( utils )
Broken kinfocenter:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to kinfocenter:amd64 0
  Holding Back kinfocenter:amd64 rather than change libgl1-mesa-glx:amd64
Broken kinfocenter:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to kinfocenter:amd64 0
  Holding Back kinfocenter:amd64 rather than change libgl1:amd64
  Or group keep for kinfocenter:amd64
Broken kinfocenter:amd64 Depends on libglu1-mesa [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libglu1-mesa:amd64 50 as a solution to kinfocenter:amd64 0
  Holding Back kinfocenter:amd64 rather than change libglu1-mesa:amd64
Broken kinfocenter:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 50 as a solution to kinfocenter:amd64 0
  Holding Back kinfocenter:amd64 rather than change libglu1:amd64
  Or group keep for kinfocenter:amd64
Investigating (1) xserver-xorg-input-mouse [ amd64 ] < 1:1.7.1+git20110725.93ebeecd-0ubuntu0sarvatt~natty > ( x11 )
Broken xserver-xorg-input-mouse:amd64 Depends on xorg-input-abi-12 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-input-mouse:amd64 0
  Removing xserver-xorg-input-mouse:amd64 rather than change xorg-input-abi-12:amd64
Investigating (1) dreamchess [ amd64 ] < 0.2.0-2ubuntu1 -> 0.2.0-3 > ( universe/games )
Broken dreamchess:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to dreamchess:amd64 0
Broken dreamchess:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to dreamchess:amd64 0
  Or group remove for dreamchess:amd64
Broken dreamchess:amd64 Depends on libglu1-mesa [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libglu1-mesa:amd64 50 as a solution to dreamchess:amd64 0
Broken dreamchess:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 50 as a solution to dreamchess:amd64 0
  Or group remove for dreamchess:amd64
Investigating (1) plymouth-x11 [ amd64 ] < 0.8.2-2ubuntu23 -> 0.8.2-2ubuntu28 > ( universe/x11 )
Broken plymouth-x11:amd64 Depends on plymouth [ amd64 ] < 0.8.2-2ubuntu23 -> 0.8.2-2ubuntu28 > ( x11 ) (= 0.8.2-2ubuntu28)
  Considering plymouth:amd64 23 as a solution to plymouth-x11:amd64 0
  Removing plymouth-x11:amd64 rather than change plymouth:amd64
Investigating (1) rss-glx [ amd64 ] < 0.9.1-3ubuntu1 -> 0.9.1-5ubuntu1 > ( universe/x11 )
Broken rss-glx:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to rss-glx:amd64 0
Broken rss-glx:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to rss-glx:amd64 0
  Or group remove for rss-glx:amd64
Broken rss-glx:amd64 Depends on libglc0 [ amd64 ] < 0.7.2-4build1 > ( universe/libs ) (>= 0.7.1)
  Considering libglc0:amd64 1 as a solution to rss-glx:amd64 0
  Removing rss-glx:amd64 rather than change libglc0:amd64
Investigating (1) libkms1 [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libs )
Broken libkms1:amd64 Depends on libdrm2 [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libs ) (>= 2.4.25)
  Considering libdrm2:amd64 136 as a solution to libkms1:amd64 0
  Removing libkms1:amd64 rather than change libdrm2:amd64
Investigating (1) xserver-xorg-video-radeon [ amd64 ] < 1:6.14.99+git20110922.a6b2bd2d-0ubuntu0sarvatt~natty > ( x11 )
Broken xserver-xorg-video-radeon:amd64 Depends on libdrm-radeon1 [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libs ) (>= 2.4.17)
  Considering libdrm-radeon1:amd64 17 as a solution to xserver-xorg-video-radeon:amd64 0
  Removing xserver-xorg-video-radeon:amd64 rather than change libdrm-radeon1:amd64
Investigating (1) libglew1.5-dev [ amd64 ] < 1.5.7.is.1.5.2-1ubuntu2 -> 1.5.7.is.1.5.2-1ubuntu4 > ( libdevel )
Broken libglew1.5-dev:amd64 Depends on libglew1.5 [ amd64 ] < 1.5.7.is.1.5.2-1ubuntu2 -> 1.5.7.is.1.5.2-1ubuntu4 > ( libs ) (= 1.5.7.is.1.5.2-1ubuntu4)
  Considering libglew1.5:amd64 10 as a solution to libglew1.5-dev:amd64 0
  Removing libglew1.5-dev:amd64 rather than change libglew1.5:amd64
Investigating (1) mesa-utils [ amd64 ] < 8.0.1+git20110129+d8f7d6b-0ubuntu2 > ( universe/graphics )
Broken mesa-utils:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to mesa-utils:amd64 -1
Broken mesa-utils:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to mesa-utils:amd64 -1
  Or group remove for mesa-utils:amd64
Investigating (1) xserver-xorg-video-apm [ amd64 ] < 1:1.2.3+git20110526.6f8a776f-0ubuntu0sarvatt~natty > ( universe/x11 )
Broken xserver-xorg-video-apm:amd64 Depends on xorg-video-abi-10 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-video-apm:amd64 -1
  Removing xserver-xorg-video-apm:amd64 rather than change xorg-video-abi-10:amd64
Investigating (1) xserver-xorg-video-ark [ amd64 ] < 1:0.7.3+git20110526.9d3769be-0ubuntu0sarvatt~natty > ( universe/x11 )
Broken xserver-xorg-video-ark:amd64 Depends on xorg-video-abi-10 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-video-ark:amd64 -1
  Removing xserver-xorg-video-ark:amd64 rather than change xorg-video-abi-10:amd64
Investigating (1) zynaddsubfx [ amd64 ] < 2.4.0-1build3 -> 2.4.0-1.2 > ( universe/sound )
Broken zynaddsubfx:amd64 Depends on libfltk1.1 [ amd64 ] < 1.1.10-3 -> 1.1.10-7 > ( libs ) (>= 1.1.6)
  Considering libfltk1.1:amd64 5 as a solution to zynaddsubfx:amd64 -1
  Removing zynaddsubfx:amd64 rather than change libfltk1.1:amd64
Investigating (1) libkwineffects1a [ amd64 ] < 4:4.6.5-0ubuntu1 > ( libs )
Broken libkwineffects1a:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to libkwineffects1a:amd64 -1
Broken libkwineffects1a:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to libkwineffects1a:amd64 -1
  Or group remove for libkwineffects1a:amd64
Investigating (1) xserver-xorg-video-s3virge [ amd64 ] < 1:1.10.4+git20110526.a568407e-0ubuntu0sarvatt~natty > ( universe/x11 )
Broken xserver-xorg-video-s3virge:amd64 Depends on xorg-video-abi-10 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-video-s3virge:amd64 -1
  Removing xserver-xorg-video-s3virge:amd64 rather than change xorg-video-abi-10:amd64
Investigating (1) xserver-xorg-video-v4l [ amd64 ] < 1:0.2.0-5build2 > ( x11 )
Broken xserver-xorg-video-v4l:amd64 Depends on xorg-video-abi-10 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-video-v4l:amd64 -1
  Removing xserver-xorg-video-v4l:amd64 rather than change xorg-video-abi-10:amd64
Investigating (1) xserver-xorg-video-chips [ amd64 ] < 1:1.2.4+git20111005.5f8a7320-0ubuntu0sarvatt~natty > ( universe/x11 )
Broken xserver-xorg-video-chips:amd64 Depends on xorg-video-abi-10 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-video-chips:amd64 -1
  Removing xserver-xorg-video-chips:amd64 rather than change xorg-video-abi-10:amd64
Investigating (1) openmovieeditor [ amd64 ] < 0.0.20080102-3ubuntu1 > ( graphics )
Broken openmovieeditor:amd64 Depends on libfltk1.1 [ amd64 ] < 1.1.10-3 -> 1.1.10-7 > ( libs ) (>= 1.1.8~rc1)
  Considering libfltk1.1:amd64 5 as a solution to openmovieeditor:amd64 -1
  Removing openmovieeditor:amd64 rather than change libfltk1.1:amd64
Investigating (1) snes9x-gtk [ amd64 ] < 1:1.52-1 > ( non-free/games )
Broken snes9x-gtk:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to snes9x-gtk:amd64 -1
Broken snes9x-gtk:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to snes9x-gtk:amd64 -1
  Or group remove for snes9x-gtk:amd64
Investigating (1) mplayer [ amd64 ] < 2:1.0~rc4.dfsg1-1ubuntu3 -> 2:1.0~rc4.dfsg1+svn33713-1 > ( universe/graphics )
Broken mplayer:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to mplayer:amd64 -1
Broken mplayer:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to mplayer:amd64 -1
  Or group remove for mplayer:amd64
Investigating (1) imageshack-uploader [ amd64 ] < 2.2.0 > ( universe/utils )
Broken imageshack-uploader:amd64 Depends on libqt4-gui [ amd64 ] < 4:4.7.2-0ubuntu6.3 -> 4:4.7.4-0ubuntu8 > ( libs )
  Considering libqt4-gui:amd64 2 as a solution to imageshack-uploader:amd64 -1
  Removing imageshack-uploader:amd64 rather than change libqt4-gui:amd64
Investigating (1) compiz-fusion-plugins-extra [ amd64 ] < 0.9.4-0ubuntu3 -> 0.9.5.94-0ubuntu1 > ( universe/x11 )
Broken compiz-fusion-plugins-extra:amd64 Depends on compiz-plugins-extra [ amd64 ] < 0.9.4-0ubuntu3 -> 0.9.5.94-0ubuntu1 > ( universe/x11 )
  Considering compiz-plugins-extra:amd64 1 as a solution to compiz-fusion-plugins-extra:amd64 -1
  Removing compiz-fusion-plugins-extra:amd64 rather than change compiz-plugins-extra:amd64
Investigating (1) python-gtkglext1 [ amd64 ] < 1.1.0-6build1 -> 1.1.0-7 > ( universe/python )
Broken python-gtkglext1:amd64 Depends on libgtkglext1 [ amd64 ] < 1.2.0-1.1ubuntu1 -> 1.2.0-1.2fakesync1 > ( universe/libs )
  Considering libgtkglext1:amd64 2 as a solution to python-gtkglext1:amd64 -1
  Removing python-gtkglext1:amd64 rather than change libgtkglext1:amd64
Investigating (1) phonon-backend-xine [ amd64 ] < 4:4.7.0really4.4.4-0ubuntu3 > ( sound )
Broken phonon-backend-xine:amd64 Depends on libxine1 [ amd64 ] < 1.1.19-2ubuntu5 -> 1.1.19-2ubuntu6 > ( libs ) (>= 1.1.8-1)
  Considering libxine1:amd64 2 as a solution to phonon-backend-xine:amd64 -1
  Removing phonon-backend-xine:amd64 rather than change libxine1:amd64
Investigating (1) desmume [ amd64 ] < 0.9.6-1-1 -> 0.9.7-2 > ( universe/games )
Broken desmume:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to desmume:amd64 -1
Broken desmume:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to desmume:amd64 -1
  Or group remove for desmume:amd64
Broken desmume:amd64 Depends on libglu1-mesa [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libglu1-mesa:amd64 50 as a solution to desmume:amd64 -1
Broken desmume:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 50 as a solution to desmume:amd64 -1
  Or group remove for desmume:amd64
Investigating (1) xserver-xorg-video-nv [ amd64 ] < 1:2.1.17-3ubuntu7 > ( x11 )
Broken xserver-xorg-video-nv:amd64 Depends on libdrm2 [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libs ) (>= 2.4.3)
  Considering libdrm2:amd64 136 as a solution to xserver-xorg-video-nv:amd64 -1
  Removing xserver-xorg-video-nv:amd64 rather than change libdrm2:amd64
Investigating (1) xserver-xorg-video-voodoo [ amd64 ] < 1:1.2.4+git20110526.614ccdf6-0ubuntu0sarvatt~natty > ( universe/x11 )
Broken xserver-xorg-video-voodoo:amd64 Depends on xorg-video-abi-10 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-video-voodoo:amd64 -1
  Removing xserver-xorg-video-voodoo:amd64 rather than change xorg-video-abi-10:amd64
Investigating (1) libnux-0.9-0 [ amd64 ] < 0.9.48-0ubuntu1.1 > ( libs )
Broken libnux-0.9-0:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to libnux-0.9-0:amd64 -1
Broken libnux-0.9-0:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to libnux-0.9-0:amd64 -1
  Or group remove for libnux-0.9-0:amd64
Broken libnux-0.9-0:amd64 Depends on libglew1.5 [ amd64 ] < 1.5.7.is.1.5.2-1ubuntu2 -> 1.5.7.is.1.5.2-1ubuntu4 > ( libs ) (>= 1.5.7.is.1.5.2)
  Considering libglew1.5:amd64 10 as a solution to libnux-0.9-0:amd64 -1
  Removing libnux-0.9-0:amd64 rather than change libglew1.5:amd64
Investigating (1) libsoil1 [ amd64 ] < 1.07~20080707.dfsg-2 > ( universe/libs )
Broken libsoil1:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to libsoil1:amd64 -1
Broken libsoil1:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to libsoil1:amd64 -1
  Or group remove for libsoil1:amd64
Investigating (1) xserver-xorg-video-tseng [ amd64 ] < 1:1.2.4+git20110613.542e65de-0ubuntu0sarvatt~natty > ( universe/x11 )
Broken xserver-xorg-video-tseng:amd64 Depends on xorg-video-abi-10 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-video-tseng:amd64 -1
  Removing xserver-xorg-video-tseng:amd64 rather than change xorg-video-abi-10:amd64
Investigating (1) compiz-fusion-plugins-main [ amd64 ] < 0.9.4+bzr20110527-0ubuntu1~natty1 -> 1:0.9.6-0ubuntu2 > ( x11 )
Broken compiz-fusion-plugins-main:amd64 Depends on compiz-plugins-main [ amd64 ] < 0.9.4+bzr20110527-0ubuntu1~natty1 -> 1:0.9.6-0ubuntu2 > ( x11 )
  Considering compiz-plugins-main:amd64 3 as a solution to compiz-fusion-plugins-main:amd64 -1
  Removing compiz-fusion-plugins-main:amd64 rather than change compiz-plugins-main:amd64
Investigating (1) xserver-xorg-input-joystick [ amd64 ] < 1:1.6.0+git20110725.204dcb86-0ubuntu0sarvatt~natty > ( universe/x11 )
Broken xserver-xorg-input-joystick:amd64 Depends on xorg-input-abi-12 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-input-joystick:amd64 -1
  Removing xserver-xorg-input-joystick:amd64 rather than change xorg-input-abi-12:amd64
Investigating (1) xserver-xorg-video-rendition [ amd64 ] < 1:4.2.4+git20110526.541d1193-0ubuntu0sarvatt~natty > ( universe/x11 )
Broken xserver-xorg-video-rendition:amd64 Depends on xorg-video-abi-10 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-video-rendition:amd64 -1
  Removing xserver-xorg-video-rendition:amd64 rather than change xorg-video-abi-10:amd64
Investigating (1) xserver-xorg-video-i128 [ amd64 ] < 1:1.3.4+git20110526.b9e0edbd-0ubuntu0sarvatt~natty > ( universe/x11 )
Broken xserver-xorg-video-i128:amd64 Depends on xorg-video-abi-10 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-video-i128:amd64 -1
  Removing xserver-xorg-video-i128:amd64 rather than change xorg-video-abi-10:amd64
Investigating (1) braid [ amd64 ] < 1.0.0-0ubuntu2 > ( games )
Broken braid:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to braid:amd64 -2
Broken braid:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to braid:amd64 -2
  Or group remove for braid:amd64
Broken braid:amd64 Depends on nvidia-cg-toolkit [ amd64 ] < 3.0.0007-0ubuntu1 > ( multiverse/libs )
  Considering nvidia-cg-toolkit:amd64 3 as a solution to braid:amd64 -2
  Removing braid:amd64 rather than change nvidia-cg-toolkit:amd64
Investigating (1) worldofgoodemo [ amd64 ] < 1.41 > ( games )
Broken worldofgoodemo:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to worldofgoodemo:amd64 -2
  Removing worldofgoodemo:amd64 rather than change libgl1:amd64
Investigating (2) gvfs [ amd64 ] < 1.8.0-0ubuntu3 -> 1.10.0-0ubuntu1 > ( libs )
Broken gvfs:amd64 Depends on x11-utils [ amd64 ] < 7.6+1 -> 7.6+3 > ( x11 )
  Considering x11-utils:amd64 50 as a solution to gvfs:amd64 73
  Added x11-utils:amd64 to the remove list
  Fixing gvfs:amd64 via keep of x11-utils:amd64
Investigating (2) libplasma3 [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu3 > ( libs )
Broken libplasma3:amd64 Depends on libqt4-opengl [ amd64 ] < 4:4.7.2-0ubuntu6.3 -> 4:4.7.4-0ubuntu8 > ( libs ) (>= 4:4.7.0)
  Considering libqt4-opengl:amd64 30 as a solution to libplasma3:amd64 57
  Added libqt4-opengl:amd64 to the remove list
  Fixing libplasma3:amd64 via keep of libqt4-opengl:amd64
 Try to Re-Instate (2) x11-utils:amd64
Investigating (2) x11-utils [ amd64 ] < 7.6+1 -> 7.6+3 > ( x11 )
Broken x11-utils:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to x11-utils:amd64 73
Broken x11-utils:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to x11-utils:amd64 73
  Or group remove for x11-utils:amd64
Investigating (2) kde-runtime [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
Broken kde-runtime:amd64 Depends on phonon-backend-gstreamer [ amd64 ] < none -> 4:4.7.0really4.5.1-1ubuntu3 > ( sound )
  Considering phonon-backend-gstreamer:amd64 2 as a solution to kde-runtime:amd64 49
  Holding Back kde-runtime:amd64 rather than change phonon-backend-gstreamer:amd64
Broken kde-runtime:amd64 Depends on phonon-backend [ amd64 ] < none > ( none )
  Considering phonon-backend-xine:amd64 -1 as a solution to kde-runtime:amd64 49
  Added phonon-backend-xine:amd64 to the remove list
  Fixing kde-runtime:amd64 via keep of phonon-backend-xine:amd64
 Try to Re-Instate (2) gnome-settings-daemon:amd64
Investigating (2) mountall [ amd64 ] < 2.25ubuntu1 -> 2.31 > ( admin )
Broken mountall:amd64 Depends on plymouth [ amd64 ] < 0.8.2-2ubuntu23 -> 0.8.2-2ubuntu28 > ( x11 )
  Considering plymouth:amd64 23 as a solution to mountall:amd64 33
  Added plymouth:amd64 to the remove list
  Fixing mountall:amd64 via keep of plymouth:amd64
 Try to Re-Instate (2) libqt4-opengl:amd64
Investigating (2) libqt4-opengl [ amd64 ] < 4:4.7.2-0ubuntu6.3 -> 4:4.7.4-0ubuntu8 > ( libs )
Broken libqt4-opengl:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to libqt4-opengl:amd64 57
Broken libqt4-opengl:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to libqt4-opengl:amd64 57
  Or group remove for libqt4-opengl:amd64
Broken libqt4-opengl:amd64 Depends on libqtcore4 [ amd64 ] < 4:4.7.2-0ubuntu6.3 -> 4:4.7.4-0ubuntu8 > ( libs ) (= 4:4.7.2-0ubuntu6.3)
  Considering libqtcore4:amd64 1354 as a solution to libqt4-opengl:amd64 57
  Removing libqt4-opengl:amd64 rather than change libqtcore4:amd64
 Try to Re-Instate (2) plymouth:amd64
Investigating (2) plymouth [ amd64 ] < 0.8.2-2ubuntu23 -> 0.8.2-2ubuntu28 > ( x11 )
Broken plymouth:amd64 Depends on libdrm-intel1 [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libs ) (>= 2.4.9)
  Considering libdrm-intel1:amd64 18 as a solution to plymouth:amd64 33
  Added libdrm-intel1:amd64 to the remove list
Broken plymouth:amd64 Depends on libdrm-nouveau1a [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libs ) (>= 2.4.23)
  Considering libdrm-nouveau1a:amd64 17 as a solution to plymouth:amd64 33
  Added libdrm-nouveau1a:amd64 to the remove list
Broken plymouth:amd64 Depends on libdrm-radeon1 [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libs ) (>= 2.4.17)
  Considering libdrm-radeon1:amd64 17 as a solution to plymouth:amd64 33
  Added libdrm-radeon1:amd64 to the remove list
Broken plymouth:amd64 Depends on libdrm2 [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libs ) (>= 2.4.3)
  Considering libdrm2:amd64 136 as a solution to plymouth:amd64 33
  Removing plymouth:amd64 rather than change libdrm2:amd64
Investigating (2) indicator-applet [ amd64 ] < 0.4.12-0ubuntu1 > ( gnome )
Broken indicator-applet:amd64 Depends on gnome-panel [ amd64 ] < 1:2.32.1-0ubuntu6.5 -> 1:3.2.0-0ubuntu1 > ( universe/gnome )
  Considering gnome-panel:amd64 18 as a solution to indicator-applet:amd64 20
  Added gnome-panel:amd64 to the remove list
  Fixing indicator-applet:amd64 via keep of gnome-panel:amd64
 Try to Re-Instate (2) libevolution:amd64
 Try to Re-Instate (2) gnome-panel:amd64
Investigating (2) gnome-panel [ amd64 ] < 1:2.32.1-0ubuntu6.5 -> 1:3.2.0-0ubuntu1 > ( universe/gnome )
Broken gnome-panel:amd64 Depends on gnome-panel-data [ amd64 ] < 1:2.32.1-0ubuntu6.5 -> 1:3.2.0-0ubuntu1 > ( universe/gnome ) (< 1:2.33)
  Considering gnome-panel-data:amd64 9 as a solution to gnome-panel:amd64 20
  Added gnome-panel-data:amd64 to the remove list
Broken gnome-panel:amd64 Depends on gnome-control-center [ amd64 ] < 1:2.32.1-0ubuntu15 -> 1:3.2.0-0ubuntu6 > ( gnome ) (>= 1:2.8.2-3)
  Considering gnome-control-center:amd64 22 as a solution to gnome-panel:amd64 20
  Removing gnome-panel:amd64 rather than change gnome-control-center:amd64
Investigating (2) xserver-xorg-video-all [ amd64 ] < 1:7.6+4ubuntu3.1 -> 1:7.6+7ubuntu7 > ( x11 )
Broken xserver-xorg-video-all:amd64 Depends on xserver-xorg-video-ati [ amd64 ] < 1:6.14.99+git20110922.a6b2bd2d-0ubuntu0sarvatt~natty > ( x11 )
  Considering xserver-xorg-video-ati:amd64 1 as a solution to xserver-xorg-video-all:amd64 6
  Added xserver-xorg-video-ati:amd64 to the remove list
Broken xserver-xorg-video-all:amd64 Depends on xserver-xorg-video-cirrus [ amd64 ] < 1:1.3.2+git20110526.e4f80ffd-0ubuntu0sarvatt~natty > ( x11 )
  Considering xserver-xorg-video-cirrus:amd64 1 as a solution to xserver-xorg-video-all:amd64 6
  Added xserver-xorg-video-cirrus:amd64 to the remove list
Broken xserver-xorg-video-all:amd64 Depends on xserver-xorg-video-fbdev [ amd64 ] < 1:0.4.2+git20110526.a8721393-0ubuntu0sarvatt~natty > ( x11 )
  Considering xserver-xorg-video-fbdev:amd64 1 as a solution to xserver-xorg-video-all:amd64 6
  Added xserver-xorg-video-fbdev:amd64 to the remove list
Broken xserver-xorg-video-all:amd64 Depends on xserver-xorg-video-intel [ amd64 ] < 2:2.16.0+git20111011.823a4272-0ubuntu0sarvatt~natty > ( x11 )
  Considering xserver-xorg-video-intel:amd64 1 as a solution to xserver-xorg-video-all:amd64 6
  Added xserver-xorg-video-intel:amd64 to the remove list
Broken xserver-xorg-video-all:amd64 Depends on xserver-xorg-video-mga [ amd64 ] < 1:1.4.13.dsfg+git20110928.07792ef4-0ubuntu0sarvatt~natty > ( x11 )
  Considering xserver-xorg-video-mga:amd64 1 as a solution to xserver-xorg-video-all:amd64 6
  Added xserver-xorg-video-mga:amd64 to the remove list
Broken xserver-xorg-video-all:amd64 Depends on xserver-xorg-video-neomagic [ amd64 ] < 1:1.2.5+git20110526.a9d69f6d-0ubuntu0sarvatt~natty > ( x11 )
  Considering xserver-xorg-video-neomagic:amd64 1 as a solution to xserver-xorg-video-all:amd64 6
  Added xserver-xorg-video-neomagic:amd64 to the remove list
Broken xserver-xorg-video-all:amd64 Depends on xserver-xorg-video-nouveau [ amd64 ] < 1:0.0.16+git20111011.d575a28a-0ubuntu0sarvatt~natty > ( x11 )
  Considering xserver-xorg-video-nouveau:amd64 1 as a solution to xserver-xorg-video-all:amd64 6
  Added xserver-xorg-video-nouveau:amd64 to the remove list
Broken xserver-xorg-video-all:amd64 Depends on xserver-xorg-video-openchrome [ amd64 ] < 1:0.2.904+svn916-1ubuntu0sarvatt -> 1:0.2.904+svn920-1 > ( x11 )
  Considering xserver-xorg-video-openchrome:amd64 2 as a solution to xserver-xorg-video-all:amd64 6
  Added xserver-xorg-video-openchrome:amd64 to the remove list
Broken xserver-xorg-video-all:amd64 Depends on xserver-xorg-video-qxl [ amd64 ] < 0.0.12-1ubuntu4 -> 0.0.14-1 > ( x11 )
  Considering xserver-xorg-video-qxl:amd64 2 as a solution to xserver-xorg-video-all:amd64 6
  Added xserver-xorg-video-qxl:amd64 to the remove list
Broken xserver-xorg-video-all:amd64 Depends on xserver-xorg-video-s3 [ amd64 ] < 1:0.6.3+git20110526.381ace93-0ubuntu0sarvatt~natty > ( x11 )
  Considering xserver-xorg-video-s3:amd64 1 as a solution to xserver-xorg-video-all:amd64 6
  Added xserver-xorg-video-s3:amd64 to the remove list
Broken xserver-xorg-video-all:amd64 Depends on xserver-xorg-video-savage [ amd64 ] < 1:2.3.2+git20110928.f7516fd3-0ubuntu0sarvatt~natty > ( x11 )
  Considering xserver-xorg-video-savage:amd64 1 as a solution to xserver-xorg-video-all:amd64 6
  Added xserver-xorg-video-savage:amd64 to the remove list
Broken xserver-xorg-video-all:amd64 Depends on xserver-xorg-video-siliconmotion [ amd64 ] < 1:1.7.5+git20110526.087226bf-0ubuntu0sarvatt~natty > ( x11 )
  Considering xserver-xorg-video-siliconmotion:amd64 1 as a solution to xserver-xorg-video-all:amd64 6
  Added xserver-xorg-video-siliconmotion:amd64 to the remove list
Broken xserver-xorg-video-all:amd64 Depends on xserver-xorg-video-sis [ amd64 ] < 1:0.10.3+git20110608.94f23a56-0ubuntu0sarvatt~natty > ( x11 )
  Considering xserver-xorg-video-sis:amd64 1 as a solution to xserver-xorg-video-all:amd64 6
  Added xserver-xorg-video-sis:amd64 to the remove list
Broken xserver-xorg-video-all:amd64 Depends on xserver-xorg-video-sisusb [ amd64 ] < 1:0.9.4+git20110928.3dc05f64-0ubuntu0sarvatt~natty > ( x11 )
  Considering xserver-xorg-video-sisusb:amd64 1 as a solution to xserver-xorg-video-all:amd64 6
  Added xserver-xorg-video-sisusb:amd64 to the remove list
Broken xserver-xorg-video-all:amd64 Depends on xserver-xorg-video-tdfx [ amd64 ] < 1:1.4.3+git20110526.0c4ffbec-0ubuntu0sarvatt~natty > ( x11 )
  Considering xserver-xorg-video-tdfx:amd64 1 as a solution to xserver-xorg-video-all:amd64 6
  Added xserver-xorg-video-tdfx:amd64 to the remove list
Broken xserver-xorg-video-all:amd64 Depends on xserver-xorg-video-trident [ amd64 ] < 1:1.3.4+git20110526.de79bbea-0ubuntu0sarvatt~natty > ( x11 )
  Considering xserver-xorg-video-trident:amd64 1 as a solution to xserver-xorg-video-all:amd64 6
  Added xserver-xorg-video-trident:amd64 to the remove list
Broken xserver-xorg-video-all:amd64 Depends on xserver-xorg-video-vesa [ amd64 ] < 1:2.3.0+git20110526.0b02c685-0ubuntu0sarvatt~natty > ( x11 )
  Considering xserver-xorg-video-vesa:amd64 1 as a solution to xserver-xorg-video-all:amd64 6
  Added xserver-xorg-video-vesa:amd64 to the remove list
Broken xserver-xorg-video-all:amd64 Depends on xserver-xorg-video-vmware [ amd64 ] < 1:11.0.99.901+git20111005.de70a1d0-0ubuntu0sarvatt~natty > ( x11 )
  Considering xserver-xorg-video-vmware:amd64 1 as a solution to xserver-xorg-video-all:amd64 6
  Added xserver-xorg-video-vmware:amd64 to the remove list
  Fixing xserver-xorg-video-all:amd64 via keep of xserver-xorg-video-ati:amd64
  Fixing xserver-xorg-video-all:amd64 via keep of xserver-xorg-video-cirrus:amd64
  Fixing xserver-xorg-video-all:amd64 via keep of xserver-xorg-video-fbdev:amd64
  Fixing xserver-xorg-video-all:amd64 via keep of xserver-xorg-video-intel:amd64
  Fixing xserver-xorg-video-all:amd64 via keep of xserver-xorg-video-mga:amd64
  Fixing xserver-xorg-video-all:amd64 via keep of xserver-xorg-video-neomagic:amd64
  Fixing xserver-xorg-video-all:amd64 via keep of xserver-xorg-video-nouveau:amd64
  Fixing xserver-xorg-video-all:amd64 via keep of xserver-xorg-video-openchrome:amd64
  Fixing xserver-xorg-video-all:amd64 via keep of xserver-xorg-video-qxl:amd64
  Fixing xserver-xorg-video-all:amd64 via keep of xserver-xorg-video-s3:amd64
  Fixing xserver-xorg-video-all:amd64 via keep of xserver-xorg-video-savage:amd64
  Fixing xserver-xorg-video-all:amd64 via keep of xserver-xorg-video-siliconmotion:amd64
  Fixing xserver-xorg-video-all:amd64 via keep of xserver-xorg-video-sis:amd64
  Fixing xserver-xorg-video-all:amd64 via keep of xserver-xorg-video-sisusb:amd64
  Fixing xserver-xorg-video-all:amd64 via keep of xserver-xorg-video-tdfx:amd64
  Fixing xserver-xorg-video-all:amd64 via keep of xserver-xorg-video-trident:amd64
  Fixing xserver-xorg-video-all:amd64 via keep of xserver-xorg-video-vesa:amd64
  Fixing xserver-xorg-video-all:amd64 via keep of xserver-xorg-video-vmware:amd64
 Try to Re-Instate (2) nautilus-sendto:amd64
Investigating (2) unity-2d [ amd64 ] < none -> 4.12.0-0ubuntu1 > ( x11 )
Broken unity-2d:amd64 Depends on unity-2d-launcher [ amd64 ] < none -> 4.12.0-0ubuntu1 > ( x11 )
  Considering unity-2d-launcher:amd64 1 as a solution to unity-2d:amd64 5
  Holding Back unity-2d:amd64 rather than change unity-2d-launcher:amd64
 Try to Re-Instate (2) flashplugin-installer:amd64
 Try to Re-Instate (2) indicator-datetime:amd64
Investigating (2) aisleriot [ amd64 ] < 1:2.32.1-0ubuntu5 -> 1:3.2.0-0ubuntu1 > ( games )
Broken aisleriot:amd64 Conflicts on gnome-games [ amd64 ] < 1:2.32.1-0ubuntu5 -> 1:3.2.0-0ubuntu1 > ( universe/gnome ) (< 1:3.1.0)
  Considering gnome-games:amd64 0 as a solution to aisleriot:amd64 2
  Added gnome-games:amd64 to the remove list
  Fixing aisleriot:amd64 via remove of gnome-games:amd64
 Try to Re-Instate (2) xserver-xorg-video-openchrome:amd64
Investigating (2) xserver-xorg-video-openchrome [ amd64 ] < 1:0.2.904+svn916-1ubuntu0sarvatt -> 1:0.2.904+svn920-1 > ( x11 )
Broken xserver-xorg-video-openchrome:amd64 Depends on libdrm2 [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libs ) (>= 2.3.1)
  Considering libdrm2:amd64 136 as a solution to xserver-xorg-video-openchrome:amd64 6
  Removing xserver-xorg-video-openchrome:amd64 rather than change libdrm2:amd64
 Try to Re-Instate (2) xserver-xorg-video-qxl:amd64
Investigating (2) xserver-xorg-video-qxl [ amd64 ] < 0.0.12-1ubuntu4 -> 0.0.14-1 > ( x11 )
Broken xserver-xorg-video-qxl:amd64 Depends on xorg-video-abi-10 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-video-qxl:amd64 6
  Removing xserver-xorg-video-qxl:amd64 rather than change xorg-video-abi-10:amd64
Investigating (2) mesa-common-dev [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( devel )
Broken mesa-common-dev:amd64 Depends on libdrm-dev [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libdevel )
  Considering libdrm-dev:amd64 0 as a solution to mesa-common-dev:amd64 2
  Added libdrm-dev:amd64 to the remove list
  Fixing mesa-common-dev:amd64 via keep of libdrm-dev:amd64
Investigating (2) xserver-xorg-video-ati [ amd64 ] < 1:6.14.99+git20110922.a6b2bd2d-0ubuntu0sarvatt~natty > ( x11 )
Broken xserver-xorg-video-ati:amd64 Depends on libpciaccess0 [ amd64 ] < 0.12.1+git20110826.7bfc4f80-0ubuntu0sarvatt~natty2 > ( libs )
  Considering libpciaccess0:amd64 51 as a solution to xserver-xorg-video-ati:amd64 6
  Removing xserver-xorg-video-ati:amd64 rather than change libpciaccess0:amd64
 Try to Re-Instate (2) glchess:amd64
Investigating (2) xserver-xorg-video-mga [ amd64 ] < 1:1.4.13.dsfg+git20110928.07792ef4-0ubuntu0sarvatt~natty > ( x11 )
Broken xserver-xorg-video-mga:amd64 Depends on xorg-video-abi-10 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-video-mga:amd64 6
  Removing xserver-xorg-video-mga:amd64 rather than change xorg-video-abi-10:amd64
Investigating (2) xserver-xorg-video-trident [ amd64 ] < 1:1.3.4+git20110526.de79bbea-0ubuntu0sarvatt~natty > ( x11 )
Broken xserver-xorg-video-trident:amd64 Depends on xorg-video-abi-10 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-video-trident:amd64 6
  Removing xserver-xorg-video-trident:amd64 rather than change xorg-video-abi-10:amd64
Investigating (2) xserver-xorg-video-sis [ amd64 ] < 1:0.10.3+git20110608.94f23a56-0ubuntu0sarvatt~natty > ( x11 )
Broken xserver-xorg-video-sis:amd64 Depends on xorg-video-abi-10 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-video-sis:amd64 6
  Removing xserver-xorg-video-sis:amd64 rather than change xorg-video-abi-10:amd64
Investigating (2) xserver-xorg-video-siliconmotion [ amd64 ] < 1:1.7.5+git20110526.087226bf-0ubuntu0sarvatt~natty > ( x11 )
Broken xserver-xorg-video-siliconmotion:amd64 Depends on xorg-video-abi-10 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-video-siliconmotion:amd64 6
  Removing xserver-xorg-video-siliconmotion:amd64 rather than change xorg-video-abi-10:amd64
Investigating (2) xserver-xorg-video-savage [ amd64 ] < 1:2.3.2+git20110928.f7516fd3-0ubuntu0sarvatt~natty > ( x11 )
Broken xserver-xorg-video-savage:amd64 Depends on xorg-video-abi-10 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-video-savage:amd64 6
  Removing xserver-xorg-video-savage:amd64 rather than change xorg-video-abi-10:amd64
Investigating (2) xserver-xorg-video-tdfx [ amd64 ] < 1:1.4.3+git20110526.0c4ffbec-0ubuntu0sarvatt~natty > ( x11 )
Broken xserver-xorg-video-tdfx:amd64 Depends on xorg-video-abi-10 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-video-tdfx:amd64 6
  Removing xserver-xorg-video-tdfx:amd64 rather than change xorg-video-abi-10:amd64
Investigating (2) xserver-xorg-video-intel [ amd64 ] < 2:2.16.0+git20111011.823a4272-0ubuntu0sarvatt~natty > ( x11 )
Broken xserver-xorg-video-intel:amd64 Depends on libdrm-intel1 [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libs ) (>= 2.4.23-3~)
  Considering libdrm-intel1:amd64 18 as a solution to xserver-xorg-video-intel:amd64 6
  Removing xserver-xorg-video-intel:amd64 rather than change libdrm-intel1:amd64
Investigating (2) xserver-xorg-video-vmware [ amd64 ] < 1:11.0.99.901+git20111005.de70a1d0-0ubuntu0sarvatt~natty > ( x11 )
Broken xserver-xorg-video-vmware:amd64 Depends on libdrm2 [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libs ) (>= 2.3.1)
  Considering libdrm2:amd64 136 as a solution to xserver-xorg-video-vmware:amd64 6
  Removing xserver-xorg-video-vmware:amd64 rather than change libdrm2:amd64
 Try to Re-Instate (2) eog:amd64
Investigating (2) xserver-xorg-video-vesa [ amd64 ] < 1:2.3.0+git20110526.0b02c685-0ubuntu0sarvatt~natty > ( x11 )
Broken xserver-xorg-video-vesa:amd64 Depends on xorg-video-abi-10 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-video-vesa:amd64 6
  Removing xserver-xorg-video-vesa:amd64 rather than change xorg-video-abi-10:amd64
Investigating (2) xserver-xorg-video-s3 [ amd64 ] < 1:0.6.3+git20110526.381ace93-0ubuntu0sarvatt~natty > ( x11 )
Broken xserver-xorg-video-s3:amd64 Depends on xorg-video-abi-10 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-video-s3:amd64 6
  Removing xserver-xorg-video-s3:amd64 rather than change xorg-video-abi-10:amd64
Investigating (2) xserver-xorg-video-fbdev [ amd64 ] < 1:0.4.2+git20110526.a8721393-0ubuntu0sarvatt~natty > ( x11 )
Broken xserver-xorg-video-fbdev:amd64 Depends on xorg-video-abi-10 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-video-fbdev:amd64 6
  Removing xserver-xorg-video-fbdev:amd64 rather than change xorg-video-abi-10:amd64
Investigating (2) xserver-xorg-video-nouveau [ amd64 ] < 1:0.0.16+git20111011.d575a28a-0ubuntu0sarvatt~natty > ( x11 )
Broken xserver-xorg-video-nouveau:amd64 Depends on libdrm-nouveau1a [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libs ) (>= 2.4.23)
  Considering libdrm-nouveau1a:amd64 17 as a solution to xserver-xorg-video-nouveau:amd64 6
  Removing xserver-xorg-video-nouveau:amd64 rather than change libdrm-nouveau1a:amd64
Investigating (2) xserver-xorg-video-neomagic [ amd64 ] < 1:1.2.5+git20110526.a9d69f6d-0ubuntu0sarvatt~natty > ( x11 )
Broken xserver-xorg-video-neomagic:amd64 Depends on xorg-video-abi-10 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-video-neomagic:amd64 6
  Removing xserver-xorg-video-neomagic:amd64 rather than change xorg-video-abi-10:amd64
Investigating (2) xserver-xorg-video-sisusb [ amd64 ] < 1:0.9.4+git20110928.3dc05f64-0ubuntu0sarvatt~natty > ( x11 )
Broken xserver-xorg-video-sisusb:amd64 Depends on xorg-video-abi-10 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-video-sisusb:amd64 6
  Removing xserver-xorg-video-sisusb:amd64 rather than change xorg-video-abi-10:amd64
Investigating (2) xserver-xorg-video-cirrus [ amd64 ] < 1:1.3.2+git20110526.e4f80ffd-0ubuntu0sarvatt~natty > ( x11 )
Broken xserver-xorg-video-cirrus:amd64 Depends on xorg-video-abi-10 [ amd64 ] < none > ( none )
  Considering xserver-xorg-core:amd64 59 as a solution to xserver-xorg-video-cirrus:amd64 6
  Removing xserver-xorg-video-cirrus:amd64 rather than change xorg-video-abi-10:amd64
Investigating (2) libdrm-dev [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libdevel )
Broken libdrm-dev:amd64 Depends on libdrm2 [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libs ) (= 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty)
  Considering libdrm2:amd64 136 as a solution to libdrm-dev:amd64 2
  Removing libdrm-dev:amd64 rather than change libdrm2:amd64
Investigating (2) phonon-backend-xine [ amd64 ] < 4:4.7.0really4.4.4-0ubuntu3 > ( sound )
Broken phonon-backend-xine:amd64 Depends on libxine1 [ amd64 ] < 1.1.19-2ubuntu5 -> 1.1.19-2ubuntu6 > ( libs ) (>= 1.1.8-1)
  Considering libxine1:amd64 2 as a solution to phonon-backend-xine:amd64 49
  Added libxine1:amd64 to the remove list
Broken phonon-backend-xine:amd64 Depends on libxine1-x [ amd64 ] < 1.1.19-2ubuntu5 -> 1.1.19-2ubuntu6 > ( libs )
  Considering libxine1-x:amd64 4 as a solution to phonon-backend-xine:amd64 49
  Added libxine1-x:amd64 to the remove list
  Fixing phonon-backend-xine:amd64 via keep of libxine1:amd64
  Fixing phonon-backend-xine:amd64 via keep of libxine1-x:amd64
Investigating (3) gvfs [ amd64 ] < 1.8.0-0ubuntu3 -> 1.10.0-0ubuntu1 > ( libs )
Broken gvfs:amd64 Depends on x11-utils [ amd64 ] < 7.6+1 -> 7.6+3 > ( x11 )
  Considering x11-utils:amd64 73 as a solution to gvfs:amd64 73
  Removing gvfs:amd64 rather than change x11-utils:amd64
Investigating (3) libplasma3 [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu3 > ( libs )
Broken libplasma3:amd64 Depends on libqt4-opengl [ amd64 ] < 4:4.7.2-0ubuntu6.3 -> 4:4.7.4-0ubuntu8 > ( libs ) (>= 4:4.7.0)
  Considering libqt4-opengl:amd64 1354 as a solution to libplasma3:amd64 57
  Removing libplasma3:amd64 rather than change libqt4-opengl:amd64
Investigating (3) kde-runtime [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
Broken kde-runtime:amd64 Depends on libplasma3 [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu3 > ( libs ) (>= 4:4.6.80)
  Considering libplasma3:amd64 1354 as a solution to kde-runtime:amd64 49
  Holding Back kde-runtime:amd64 rather than change libplasma3:amd64
Investigating (3) mountall [ amd64 ] < 2.25ubuntu1 -> 2.31 > ( admin )
Broken mountall:amd64 Depends on plymouth [ amd64 ] < 0.8.2-2ubuntu23 -> 0.8.2-2ubuntu28 > ( x11 )
  Considering plymouth:amd64 136 as a solution to mountall:amd64 33
  Removing mountall:amd64 rather than change plymouth:amd64
Investigating (3) kubuntu-debug-installer [ amd64 ] < 11.04ubuntu1 -> 11.10ubuntu1 > ( kde )
Broken kubuntu-debug-installer:amd64 Depends on kde-runtime [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
  Considering kde-runtime:amd64 49 as a solution to kubuntu-debug-installer:amd64 23
  Holding Back kubuntu-debug-installer:amd64 rather than change kde-runtime:amd64
Investigating (3) plasma-scriptengine-javascript [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu5 > ( kde )
Broken plasma-scriptengine-javascript:amd64 Depends on libplasma3 [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu3 > ( libs ) (>= 4:4.6.80)
  Considering libplasma3:amd64 1354 as a solution to plasma-scriptengine-javascript:amd64 23
  Removing plasma-scriptengine-javascript:amd64 rather than change libplasma3:amd64
Investigating (3) indicator-applet [ amd64 ] < 0.4.12-0ubuntu1 > ( gnome )
Broken indicator-applet:amd64 Depends on gnome-panel [ amd64 ] < 1:2.32.1-0ubuntu6.5 -> 1:3.2.0-0ubuntu1 > ( universe/gnome )
  Considering gnome-panel:amd64 22 as a solution to indicator-applet:amd64 20
  Removing indicator-applet:amd64 rather than change gnome-panel:amd64
Investigating (3) gvfs-bin [ amd64 ] < 1.8.0-0ubuntu3 -> 1.10.0-0ubuntu1 > ( libs )
Broken gvfs-bin:amd64 Depends on gvfs [ amd64 ] < 1.8.0-0ubuntu3 -> 1.10.0-0ubuntu1 > ( libs ) (= 1.10.0-0ubuntu1)
  Considering gvfs:amd64 73 as a solution to gvfs-bin:amd64 18
  Removing gvfs-bin:amd64 rather than change gvfs:amd64
Investigating (3) libkworkspace4 [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu5 > ( libs )
Broken libkworkspace4:amd64 Depends on libplasma3 [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu3 > ( libs ) (>= 4:4.6.80)
  Considering libplasma3:amd64 1354 as a solution to libkworkspace4:amd64 16
  Removing libkworkspace4:amd64 rather than change libplasma3:amd64
Investigating (3) kdebase-runtime [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu5 > ( kde )
Broken kdebase-runtime:amd64 Depends on kde-runtime [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
  Considering kde-runtime:amd64 49 as a solution to kdebase-runtime:amd64 15
  Removing kdebase-runtime:amd64 rather than change kde-runtime:amd64
Investigating (3) gvfs-backends [ amd64 ] < 1.8.0-0ubuntu3 -> 1.10.0-0ubuntu1 > ( libs )
Broken gvfs-backends:amd64 Depends on gvfs [ amd64 ] < 1.8.0-0ubuntu3 -> 1.10.0-0ubuntu1 > ( libs ) (= 1.10.0-0ubuntu1)
  Considering gvfs:amd64 73 as a solution to gvfs-backends:amd64 14
  Removing gvfs-backends:amd64 rather than change gvfs:amd64
Investigating (3) kdepim-runtime [ amd64 ] < 4:4.4.10-0ubuntu2 -> 4:4.7.2+git111007-0ubuntu1 > ( kde )
Broken kdepim-runtime:amd64 Depends on kde-runtime [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
  Considering kde-runtime:amd64 49 as a solution to kdepim-runtime:amd64 7
  Removing kdepim-runtime:amd64 rather than change kde-runtime:amd64
Investigating (3) xserver-xorg-video-all [ amd64 ] < 1:7.6+4ubuntu3.1 -> 1:7.6+7ubuntu7 > ( x11 )
Broken xserver-xorg-video-all:amd64 Depends on xserver-xorg-video-ati [ amd64 ] < 1:6.14.99+git20110922.a6b2bd2d-0ubuntu0sarvatt~natty > ( x11 )
  Considering xserver-xorg-video-ati:amd64 51 as a solution to xserver-xorg-video-all:amd64 6
  Removing xserver-xorg-video-all:amd64 rather than change xserver-xorg-video-ati:amd64
Investigating (3) polkit-kde-1 [ amd64 ] < 0.99.0-0ubuntu3 -> 0.99.0-3ubuntu1 > ( libs )
Broken polkit-kde-1:amd64 Depends on kde-runtime [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
  Considering kde-runtime:amd64 49 as a solution to polkit-kde-1:amd64 6
  Removing polkit-kde-1:amd64 rather than change kde-runtime:amd64
Investigating (3) brasero [ amd64 ] < 2.32.1-0ubuntu2 -> 3.2.0-0ubuntu1 > ( gnome )
Broken brasero:amd64 Depends on gvfs [ amd64 ] < 1.8.0-0ubuntu3 -> 1.10.0-0ubuntu1 > ( libs )
  Considering gvfs:amd64 73 as a solution to brasero:amd64 6
  Removing brasero:amd64 rather than change gvfs:amd64
Investigating (3) libplasmagenericshell4 [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu5 > ( libs )
Broken libplasmagenericshell4:amd64 Depends on libkworkspace4 [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu5 > ( libs ) (= 4:4.7.1-0ubuntu5)
  Considering libkworkspace4:amd64 1354 as a solution to libplasmagenericshell4:amd64 5
  Removing libplasmagenericshell4:amd64 rather than change libkworkspace4:amd64
Investigating (3) kde-baseapps-bin [ amd64 ] < none -> 4:4.7.1-0ubuntu3 > ( kde )
Broken kde-baseapps-bin:amd64 Depends on kde-runtime [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
  Considering kde-runtime:amd64 49 as a solution to kde-baseapps-bin:amd64 4
  Holding Back kde-baseapps-bin:amd64 rather than change kde-runtime:amd64
 Try to Re-Instate (3) libxine1-x:amd64
Investigating (3) libxine1-x [ amd64 ] < 1.1.19-2ubuntu5 -> 1.1.19-2ubuntu6 > ( libs )
Broken libxine1-x:amd64 Depends on libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libgl1-mesa-glx:amd64 174 as a solution to libxine1-x:amd64 49
Broken libxine1-x:amd64 Depends on libgl1 [ amd64 ] < none > ( none )
  Considering libgl1-mesa-glx:amd64 174 as a solution to libxine1-x:amd64 49
  Or group remove for libxine1-x:amd64
Broken libxine1-x:amd64 Depends on libglu1-mesa [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
  Considering libglu1-mesa:amd64 50 as a solution to libxine1-x:amd64 49
Broken libxine1-x:amd64 Depends on libglu1 [ amd64 ] < none > ( none )
  Considering libglu1-mesa:amd64 50 as a solution to libxine1-x:amd64 49
  Or group remove for libxine1-x:amd64
Broken libxine1-x:amd64 Depends on libxine1-bin [ amd64 ] < 1.1.19-2ubuntu5 -> 1.1.19-2ubuntu6 > ( libs ) (= 1.1.19-2ubuntu5)
  Considering libxine1-bin:amd64 6 as a solution to libxine1-x:amd64 49
  Added libxine1-bin:amd64 to the remove list
Investigating (3) konqueror [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu3 > ( web )
Broken konqueror:amd64 Depends on kde-baseapps-bin [ amd64 ] < none -> 4:4.7.1-0ubuntu3 > ( kde ) (= 4:4.7.1-0ubuntu3)
  Considering kde-baseapps-bin:amd64 4 as a solution to konqueror:amd64 4
  Removing konqueror:amd64 rather than change kde-baseapps-bin:amd64
Investigating (3) konqueror-nsplugins [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu3 > ( utils )
Broken konqueror-nsplugins:amd64 Depends on kde-runtime [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
  Considering kde-runtime:amd64 49 as a solution to konqueror-nsplugins:amd64 3
  Removing konqueror-nsplugins:amd64 rather than change kde-runtime:amd64
Investigating (3) dolphin [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu3 > ( kde )
Broken dolphin:amd64 Depends on kde-runtime [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
  Considering kde-runtime:amd64 49 as a solution to dolphin:amd64 3
  Removing dolphin:amd64 rather than change kde-runtime:amd64
Investigating (3) qapt-batch [ amd64 ] < 1.1.2-0ubuntu1 -> 1.2.1-0ubuntu2 > ( kde )
Broken qapt-batch:amd64 Depends on kde-runtime [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
  Considering kde-runtime:amd64 49 as a solution to qapt-batch:amd64 2
  Removing qapt-batch:amd64 rather than change kde-runtime:amd64
Investigating (3) mesa-common-dev [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( devel )
Broken mesa-common-dev:amd64 Depends on libdrm-dev [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libdevel )
  Considering libdrm-dev:amd64 136 as a solution to mesa-common-dev:amd64 2
  Removing mesa-common-dev:amd64 rather than change libdrm-dev:amd64
Investigating (3) kfind [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu3 > ( utils )
Broken kfind:amd64 Depends on kde-runtime [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
  Considering kde-runtime:amd64 49 as a solution to kfind:amd64 2
  Removing kfind:amd64 rather than change kde-runtime:amd64
Investigating (3) kdebase-bin [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu3 > ( universe/kde )
Broken kdebase-bin:amd64 Depends on kde-baseapps-bin [ amd64 ] < none -> 4:4.7.1-0ubuntu3 > ( kde )
  Considering kde-baseapps-bin:amd64 4 as a solution to kdebase-bin:amd64 2
  Removing kdebase-bin:amd64 rather than change kde-baseapps-bin:amd64
Investigating (3) python-kde4 [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu1 > ( python )
Broken python-kde4:amd64 Depends on kde-runtime [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
  Considering kde-runtime:amd64 49 as a solution to python-kde4:amd64 2
  Removing python-kde4:amd64 rather than change kde-runtime:amd64
 Try to Re-Instate (3) libxine1:amd64
Investigating (3) libxine1 [ amd64 ] < 1.1.19-2ubuntu5 -> 1.1.19-2ubuntu6 > ( libs )
Broken libxine1:amd64 Depends on libxine1-misc-plugins [ amd64 ] < 1.1.19-2ubuntu5 -> 1.1.19-2ubuntu6 > ( libs ) (= 1.1.19-2ubuntu5)
  Considering libxine1-misc-plugins:amd64 2 as a solution to libxine1:amd64 49
  Added libxine1-misc-plugins:amd64 to the remove list
Broken libxine1:amd64 Depends on libxine1-plugins [ amd64 ] < none -> 1.1.19-2ubuntu6 > ( universe/libs ) (= 1.1.19-2ubuntu5)
Broken libxine1:amd64 Depends on libxine1-x [ amd64 ] < 1.1.19-2ubuntu5 -> 1.1.19-2ubuntu6 > ( libs ) (= 1.1.19-2ubuntu5)
  Considering libxine1-x:amd64 49 as a solution to libxine1:amd64 49
  Removing libxine1:amd64 rather than change libxine1-x:amd64
Investigating (3) gvfs-fuse [ amd64 ] < 1.8.0-0ubuntu3 -> 1.10.0-0ubuntu1 > ( libs )
Broken gvfs-fuse:amd64 Depends on gvfs [ amd64 ] < 1.8.0-0ubuntu3 -> 1.10.0-0ubuntu1 > ( libs ) (= 1.10.0-0ubuntu1)
  Considering gvfs:amd64 73 as a solution to gvfs-fuse:amd64 1
  Removing gvfs-fuse:amd64 rather than change gvfs:amd64
Investigating (3) kdesudo [ amd64 ] < 3.4.2.3-2ubuntu3 > ( kde )
Broken kdesudo:amd64 Depends on kdebase-runtime [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu5 > ( kde )
  Considering kdebase-runtime:amd64 49 as a solution to kdesudo:amd64 1
  Removing kdesudo:amd64 rather than change kdebase-runtime:amd64
Investigating (3) libtaskmanager4abi2 [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( libs )
Broken libtaskmanager4abi2:amd64 Depends on libkworkspace4 [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu5 > ( libs ) (= 4:4.7.1-0ubuntu5)
  Considering libkworkspace4:amd64 1354 as a solution to libtaskmanager4abi2:amd64 1
  Holding Back libtaskmanager4abi2:amd64 rather than change libkworkspace4:amd64
Investigating (3) plasma-desktop [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
Broken plasma-desktop:amd64 Depends on kde-runtime [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
  Considering kde-runtime:amd64 49 as a solution to plasma-desktop:amd64 1
  Holding Back plasma-desktop:amd64 rather than change kde-runtime:amd64
Investigating (3) f-spot [ amd64 ] < 0.8.2-1 -> 0.8.2-4 > ( universe/gnome )
Broken f-spot:amd64 Depends on gvfs-bin [ amd64 ] < 1.8.0-0ubuntu3 -> 1.10.0-0ubuntu1 > ( libs )
  Considering gvfs-bin:amd64 73 as a solution to f-spot:amd64 0
  Removing f-spot:amd64 rather than change gvfs-bin:amd64
Investigating (3) libweather-ion6 [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( libs )
Broken libweather-ion6:amd64 Depends on libplasma3 [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu3 > ( libs ) (>= 4:4.6.80)
  Considering libplasma3:amd64 1354 as a solution to libweather-ion6:amd64 0
  Holding Back libweather-ion6:amd64 rather than change libplasma3:amd64
Investigating (3) klipper [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
Broken klipper:amd64 Depends on kde-runtime [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
  Considering kde-runtime:amd64 49 as a solution to klipper:amd64 0
  Holding Back klipper:amd64 rather than change kde-runtime:amd64
Investigating (3) libplasmaclock4abi2 [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( libs )
Broken libplasmaclock4abi2:amd64 Depends on libplasma3 [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu3 > ( libs ) (>= 4:4.6.80)
  Considering libplasma3:amd64 1354 as a solution to libplasmaclock4abi2:amd64 0
  Holding Back libplasmaclock4abi2:amd64 rather than change libplasma3:amd64
Investigating (3) ksysguard [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( utils )
Broken ksysguard:amd64 Depends on kde-runtime [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
  Considering kde-runtime:amd64 49 as a solution to ksysguard:amd64 0
  Holding Back ksysguard:amd64 rather than change kde-runtime:amd64
Investigating (3) k3b [ amd64 ] < 2.0.2-0ubuntu1 -> 2.0.2-0ubuntu4 > ( otherosfs )
Broken k3b:amd64 Depends on kde-runtime [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
  Considering kde-runtime:amd64 49 as a solution to k3b:amd64 0
  Removing k3b:amd64 rather than change kde-runtime:amd64
Investigating (3) kdm [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
Broken kdm:amd64 Depends on kde-runtime [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
  Considering kde-runtime:amd64 49 as a solution to kdm:amd64 0
  Holding Back kdm:amd64 rather than change kde-runtime:amd64
Investigating (3) plasma-dataengines-workspace [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
Broken plasma-dataengines-workspace:amd64 Depends on kdepim-runtime [ amd64 ] < 4:4.4.10-0ubuntu2 -> 4:4.7.2+git111007-0ubuntu1 > ( kde )
  Considering kdepim-runtime:amd64 49 as a solution to plasma-dataengines-workspace:amd64 0
  Holding Back plasma-dataengines-workspace:amd64 rather than change kdepim-runtime:amd64
Investigating (3) update-manager-kde [ amd64 ] < 1:0.150.3 -> 1:0.152.25 > ( gnome )
Broken update-manager-kde:amd64 Depends on python-kde4 [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu1 > ( python )
  Considering python-kde4:amd64 49 as a solution to update-manager-kde:amd64 0
  Removing update-manager-kde:amd64 rather than change python-kde4:amd64
Investigating (3) jockey-kde [ amd64 ] < 0.9.2-0ubuntu5 -> 0.9.4-0ubuntu10 > ( admin )
Broken jockey-kde:amd64 Depends on python-kde4 [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu1 > ( python )
  Considering python-kde4:amd64 49 as a solution to jockey-kde:amd64 0
  Removing jockey-kde:amd64 rather than change python-kde4:amd64
Investigating (3) systemsettings [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
Broken systemsettings:amd64 Depends on kde-runtime [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
  Considering kde-runtime:amd64 49 as a solution to systemsettings:amd64 0
  Holding Back systemsettings:amd64 rather than change kde-runtime:amd64
Investigating (3) plasma-widgets-workspace [ amd64 ] < none -> 4:4.7.1-0ubuntu5 > ( kde )
Broken plasma-widgets-workspace:amd64 Depends on libkworkspace4 [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu5 > ( libs ) (= 4:4.7.1-0ubuntu5)
  Considering libkworkspace4:amd64 1354 as a solution to plasma-widgets-workspace:amd64 0
  Holding Back plasma-widgets-workspace:amd64 rather than change libkworkspace4:amd64
Investigating (3) phonon-backend-xine [ amd64 ] < 4:4.7.0really4.4.4-0ubuntu3 > ( sound )
Broken phonon-backend-xine:amd64 Depends on libxine1 [ amd64 ] < 1.1.19-2ubuntu5 -> 1.1.19-2ubuntu6 > ( libs ) (>= 1.1.8-1)
  Considering libxine1:amd64 49 as a solution to phonon-backend-xine:amd64 49
  Removing phonon-backend-xine:amd64 rather than change libxine1:amd64
Investigating (4) upstart [ amd64 ] < 0.9.7-1 -> 1.3-0ubuntu10 > ( admin )
Broken upstart:amd64 Depends on mountall [ amd64 ] < 2.25ubuntu1 -> 2.31 > ( admin )
  Considering mountall:amd64 136 as a solution to upstart:amd64 72
  Removing upstart:amd64 rather than change mountall:amd64
Investigating (4) initscripts [ amd64 ] < 2.87dsf-4ubuntu23 -> 2.88dsf-13.10ubuntu4 > ( admin )
Broken initscripts:amd64 Depends on upstart [ amd64 ] < 0.9.7-1 -> 1.3-0ubuntu10 > ( admin )
  Considering upstart:amd64 136 as a solution to initscripts:amd64 56
  Removing initscripts:amd64 rather than change upstart:amd64
Investigating (4) keyboard-configuration [ amd64 ] < 1.57ubuntu20 -> 1.57ubuntu27 > ( utils )
Broken keyboard-configuration:amd64 Depends on upstart-job [ amd64 ] < none > ( none )
  Considering upstart:amd64 136 as a solution to keyboard-configuration:amd64 50
  Removing keyboard-configuration:amd64 rather than change upstart-job:amd64
Investigating (4) cups [ amd64 ] < 1.4.6-5ubuntu1.4 -> 1.5.0-8ubuntu1 > ( net )
Broken cups:amd64 Depends on upstart-job [ amd64 ] < none > ( none )
  Considering upstart:amd64 136 as a solution to cups:amd64 49
  Removing cups:amd64 rather than change upstart-job:amd64
Investigating (4) phonon [ amd64 ] < 4:4.7.0really4.5.0-0ubuntu3 -> 4:4.7.0really4.5.0-3ubuntu4 > ( sound )
Broken phonon:amd64 Depends on phonon-backend-gstreamer [ amd64 ] < none -> 4:4.7.0really4.5.1-1ubuntu3 > ( sound )
  Considering phonon-backend-gstreamer:amd64 2 as a solution to phonon:amd64 45
  Try Installing phonon-backend-gstreamer [ amd64 ] < none -> 4:4.7.0really4.5.1-1ubuntu3 > ( sound ) before changing phonon:amd64
    Installing libgl1-mesa-glx as Depends of phonon-backend-gstreamer
    Installing libqt4-opengl as Depends of phonon-backend-gstreamer
Investigating (4) avahi-daemon [ amd64 ] < 0.6.30-0ubuntu2 -> 0.6.30-4ubuntu1 > ( net )
Broken avahi-daemon:amd64 Depends on upstart-job [ amd64 ] < none > ( none )
  Considering upstart:amd64 136 as a solution to avahi-daemon:amd64 45
  Removing avahi-daemon:amd64 rather than change upstart-job:amd64
Investigating (4) ecryptfs-utils [ amd64 ] < 87-0ubuntu1.2 -> 92-0ubuntu1 > ( misc )
Broken ecryptfs-utils:amd64 Depends on upstart-job [ amd64 ] < none > ( none )
  Considering upstart:amd64 136 as a solution to ecryptfs-utils:amd64 37
  Removing ecryptfs-utils:amd64 rather than change upstart-job:amd64
Investigating (4) binfmt-support [ amd64 ] < 2.0.3 -> 2.0.7 > ( admin )
Broken binfmt-support:amd64 Depends on upstart-job [ amd64 ] < none > ( none )
  Considering upstart:amd64 136 as a solution to binfmt-support:amd64 34
  Holding Back binfmt-support:amd64 rather than change upstart-job:amd64
Investigating (4) ifupdown [ amd64 ] < 0.6.10ubuntu4 -> 0.7~alpha5.1ubuntu5 > ( admin )
Broken ifupdown:amd64 Depends on upstart-job [ amd64 ] < none > ( none )
  Considering upstart:amd64 136 as a solution to ifupdown:amd64 34
  Removing ifupdown:amd64 rather than change upstart-job:amd64
Investigating (4) cron [ amd64 ] < 3.0pl1-116ubuntu1 -> 3.0pl1-116ubuntu3 > ( admin )
Broken cron:amd64 Depends on upstart-job [ amd64 ] < none > ( none )
  Considering upstart:amd64 136 as a solution to cron:amd64 25
  Removing cron:amd64 rather than change upstart-job:amd64
 Try to Re-Instate (4) kubuntu-debug-installer:amd64
Investigating (4) kubuntu-debug-installer [ amd64 ] < 11.04ubuntu1 -> 11.10ubuntu1 > ( kde )
Broken kubuntu-debug-installer:amd64 Depends on kdebase-runtime [ amd64 ] < 4:4.6.5-0ubuntu1 -> 4:4.7.1-0ubuntu5 > ( kde )
  Considering kdebase-runtime:amd64 49 as a solution to kubuntu-debug-installer:amd64 23
  Removing kubuntu-debug-installer:amd64 rather than change kdebase-runtime:amd64
Investigating (4) ntfs-3g [ amd64 ] < 1:2010.8.8-0ubuntu1 -> 1:2011.4.12AR.4-2ubuntu3 > ( otherosfs )
Broken ntfs-3g:amd64 Depends on initscripts [ amd64 ] < 2.87dsf-4ubuntu23 -> 2.88dsf-13.10ubuntu4 > ( admin ) (>= 2.88dsf-13.3)
  Considering initscripts:amd64 136 as a solution to ntfs-3g:amd64 22
  Holding Back ntfs-3g:amd64 rather than change initscripts:amd64
Investigating (4) console-setup [ amd64 ] < 1.57ubuntu20 -> 1.57ubuntu27 > ( utils )
Broken console-setup:amd64 Depends on keyboard-configuration [ amd64 ] < 1.57ubuntu20 -> 1.57ubuntu27 > ( utils )
  Considering keyboard-configuration:amd64 136 as a solution to console-setup:amd64 19
  Removing console-setup:amd64 rather than change keyboard-configuration:amd64
Investigating (4) cups-driver-gutenprint [ amd64 ] < 5.2.6-1ubuntu1 -> 5.2.7-2ubuntu4 > ( graphics )
Broken cups-driver-gutenprint:amd64 Depends on cups [ amd64 ] < 1.4.6-5ubuntu1.4 -> 1.5.0-8ubuntu1 > ( net ) (>= 1.3.0)
  Considering cups:amd64 136 as a solution to cups-driver-gutenprint:amd64 18
  Removing cups-driver-gutenprint:amd64 rather than change cups:amd64
Investigating (4) libnss-mdns [ amd64 ] < 0.10-3.1ubuntu1 > ( admin )
Broken libnss-mdns:amd64 Depends on avahi-daemon [ amd64 ] < 0.6.30-0ubuntu2 -> 0.6.30-4ubuntu1 > ( net ) (>= 0.6.16-1)
  Considering avahi-daemon:amd64 136 as a solution to libnss-mdns:amd64 16
  Removing libnss-mdns:amd64 rather than change avahi-daemon:amd64
Investigating (4) anacron [ amd64 ] < 2.3-14ubuntu1 > ( admin )
Broken anacron:amd64 Depends on upstart-job [ amd64 ] < none > ( none )
  Considering upstart:amd64 136 as a solution to anacron:amd64 16
  Removing anacron:amd64 rather than change upstart-job:amd64
Investigating (4) rsyslog [ amd64 ] < 4.6.4-2ubuntu4.1 -> 5.8.1-1ubuntu2 > ( admin )
Broken rsyslog:amd64 Depends on upstart-job [ amd64 ] < none > ( none )
  Considering upstart:amd64 136 as a solution to rsyslog:amd64 13
  Removing rsyslog:amd64 rather than change upstart-job:amd64
Investigating (4) ureadahead [ amd64 ] < 0.100.0-11 > ( admin )
Broken ureadahead:amd64 Depends on upstart [ amd64 ] < 0.9.7-1 -> 1.3-0ubuntu10 > ( admin ) (>= 0.6.0)
  Considering upstart:amd64 136 as a solution to ureadahead:amd64 9
  Removing ureadahead:amd64 rather than change upstart:amd64
Investigating (4) apport [ amd64 ] < 1.20.1-0ubuntu5.1 -> 1.23-0ubuntu3 > ( utils )
Broken apport:amd64 Depends on upstart-job [ amd64 ] < none > ( none )
  Considering upstart:amd64 136 as a solution to apport:amd64 8
  Removing apport:amd64 rather than change upstart-job:amd64
Investigating (4) lib32nss-mdns [ amd64 ] < 0.10-3.1ubuntu1 > ( universe/admin )
Broken lib32nss-mdns:amd64 Depends on avahi-daemon [ amd64 ] < 0.6.30-0ubuntu2 -> 0.6.30-4ubuntu1 > ( net ) (>= 0.6.16-1)
  Considering avahi-daemon:amd64 136 as a solution to lib32nss-mdns:amd64 7
  Removing lib32nss-mdns:amd64 rather than change avahi-daemon:amd64
Investigating (4) apport-gtk [ amd64 ] < 1.20.1-0ubuntu5.1 -> 1.23-0ubuntu3 > ( gnome )
Broken apport-gtk:amd64 Depends on apport [ amd64 ] < 1.20.1-0ubuntu5.1 -> 1.23-0ubuntu3 > ( utils ) (>= 0.41)
  Considering apport:amd64 136 as a solution to apport-gtk:amd64 6
  Removing apport-gtk:amd64 rather than change apport:amd64
Investigating (4) irqbalance [ amd64 ] < 0.56-1ubuntu3 > ( utils )
Broken irqbalance:amd64 Depends on upstart-job [ amd64 ] < none > ( none )
  Considering upstart:amd64 136 as a solution to irqbalance:amd64 5
  Removing irqbalance:amd64 rather than change upstart-job:amd64
Investigating (4) at [ amd64 ] < 3.1.12-1ubuntu2 -> 3.1.12-1ubuntu3 > ( admin )
Broken at:amd64 Depends on upstart-job [ amd64 ] < none > ( none )
  Considering upstart:amd64 136 as a solution to at:amd64 5
  Removing at:amd64 rather than change upstart-job:amd64
Investigating (4) friendly-recovery [ amd64 ] < 0.2.11 -> 0.2.18 > ( admin )
Broken friendly-recovery:amd64 Depends on upstart-job [ amd64 ] < none > ( none )
  Considering upstart:amd64 136 as a solution to friendly-recovery:amd64 5
  Removing friendly-recovery:amd64 rather than change upstart-job:amd64
Investigating (4) network-manager [ amd64 ] < 0.8.4~git.20110319t175609.d14809b-0ubuntu3 -> 0.9.1.90-0ubuntu3 > ( net )
Broken network-manager:amd64 Depends on upstart-job [ amd64 ] < none > ( none )
  Considering upstart:amd64 136 as a solution to network-manager:amd64 5
  Removing network-manager:amd64 rather than change upstart-job:amd64
Investigating (4) alsa-utils [ amd64 ] < 1.0.24.2-0ubuntu6 -> 1.0.24.2-0ubuntu8.1 > ( sound )
Broken alsa-utils:amd64 Depends on upstart-job [ amd64 ] < none > ( none )
  Considering upstart:amd64 136 as a solution to alsa-utils:amd64 5
  Removing alsa-utils:amd64 rather than change upstart-job:amd64
Investigating (4) ufw [ amd64 ] < 0.30.1-1ubuntu1 -> 0.30.1-2ubuntu1 > ( admin )
Broken ufw:amd64 Depends on upstart-job [ amd64 ] < none > ( none )
  Considering upstart:amd64 136 as a solution to ufw:amd64 5
  Removing ufw:amd64 rather than change upstart-job:amd64
Investigating (4) network-manager-gnome [ amd64 ] < 0.8.4~git.20110318t152954.9c4c9a0-0ubuntu1 -> 0.9.1.90-0ubuntu6 > ( net )
Broken network-manager-gnome:amd64 Depends on network-manager [ amd64 ] < 0.8.4~git.20110319t175609.d14809b-0ubuntu3 -> 0.9.1.90-0ubuntu3 > ( net ) (>= 0.8.998)
  Considering network-manager:amd64 136 as a solution to network-manager-gnome:amd64 4
  Removing network-manager-gnome:amd64 rather than change network-manager:amd64
Investigating (4) wine1.2 [ amd64 ] < 1.2.2-0ubuntu6 -> 1.2.3-0ubuntu1 > ( universe/otherosfs )
Broken wine1.2:amd64 Depends on lib32nss-mdns [ amd64 ] < 0.10-3.1ubuntu1 > ( universe/admin ) (>= 0.10-3)
  Considering lib32nss-mdns:amd64 136 as a solution to wine1.2:amd64 4
  Removing wine1.2:amd64 rather than change lib32nss-mdns:amd64
Investigating (4) ubuntu-minimal [ amd64 ] < 1.220 -> 1.245 > ( metapackages )
Broken ubuntu-minimal:amd64 Depends on console-setup [ amd64 ] < 1.57ubuntu20 -> 1.57ubuntu27 > ( utils )
  Considering console-setup:amd64 136 as a solution to ubuntu-minimal:amd64 4
  Removing ubuntu-minimal:amd64 rather than change console-setup:amd64
Investigating (4) hplip-cups [ amd64 ] < 3.11.1-2ubuntu2 -> 3.11.7-1ubuntu3 > ( text )
Broken hplip-cups:amd64 Depends on cups [ amd64 ] < 1.4.6-5ubuntu1.4 -> 1.5.0-8ubuntu1 > ( net )
  Considering cups:amd64 136 as a solution to hplip-cups:amd64 3
  Removing hplip-cups:amd64 rather than change cups:amd64
Investigating (4) bluez-cups [ amd64 ] < 4.91-0ubuntu1 -> 4.96-0ubuntu4 > ( admin )
Broken bluez-cups:amd64 Depends on cups [ amd64 ] < 1.4.6-5ubuntu1.4 -> 1.5.0-8ubuntu1 > ( net )
  Considering cups:amd64 136 as a solution to bluez-cups:amd64 3
  Removing bluez-cups:amd64 rather than change cups:amd64
Investigating (4) hplip [ amd64 ] < 3.11.1-2ubuntu2 -> 3.11.7-1ubuntu3 > ( utils )
Broken hplip:amd64 Depends on hplip-cups [ amd64 ] < 3.11.1-2ubuntu2 -> 3.11.7-1ubuntu3 > ( text ) (= 3.11.7-1ubuntu3)
  Considering hplip-cups:amd64 136 as a solution to hplip:amd64 3
  Removing hplip:amd64 rather than change hplip-cups:amd64
Investigating (4) modemmanager [ amd64 ] < 0.4+git.20110124t203624.00b6cce-2ubuntu1 -> 0.5-1ubuntu1 > ( net )
Broken modemmanager:amd64 Depends on upstart-job [ amd64 ] < none > ( none )
  Considering upstart:amd64 136 as a solution to modemmanager:amd64 3
  Holding Back modemmanager:amd64 rather than change upstart-job:amd64
Investigating (4) ubuntu-standard [ amd64 ] < 1.220 -> 1.245 > ( metapackages )
Broken ubuntu-standard:amd64 Depends on at [ amd64 ] < 3.1.12-1ubuntu2 -> 3.1.12-1ubuntu3 > ( admin )
  Considering at:amd64 136 as a solution to ubuntu-standard:amd64 2
  Removing ubuntu-standard:amd64 rather than change at:amd64
Investigating (4) lightdm [ amd64 ] < none -> 1.0.1-0ubuntu6 > ( x11 )
Broken lightdm:amd64 Depends on upstart-job [ amd64 ] < none > ( none )
  Considering upstart:amd64 136 as a solution to lightdm:amd64 2
  Holding Back lightdm:amd64 rather than change upstart-job:amd64
Investigating (4) telepathy-salut [ amd64 ] < 0.4.0-1 -> 0.5.0-3ubuntu1 > ( net )
Broken telepathy-salut:amd64 Depends on avahi-daemon [ amd64 ] < 0.6.30-0ubuntu2 -> 0.6.30-4ubuntu1 > ( net )
  Considering avahi-daemon:amd64 136 as a solution to telepathy-salut:amd64 2
  Removing telepathy-salut:amd64 rather than change avahi-daemon:amd64
Investigating (4) avahi-utils [ amd64 ] < 0.6.30-0ubuntu2 -> 0.6.30-4ubuntu1 > ( net )
Broken avahi-utils:amd64 Depends on avahi-daemon [ amd64 ] < 0.6.30-0ubuntu2 -> 0.6.30-4ubuntu1 > ( net )
  Considering avahi-daemon:amd64 136 as a solution to avahi-utils:amd64 2
  Removing avahi-utils:amd64 rather than change avahi-daemon:amd64
Investigating (4) acpid [ amd64 ] < 1:2.0.7-1ubuntu2 -> 1:2.0.10-1ubuntu2 > ( admin )
Broken acpid:amd64 Depends on upstart-job [ amd64 ] < none > ( none )
  Considering upstart:amd64 136 as a solution to acpid:amd64 2
  Removing acpid:amd64 rather than change upstart-job:amd64
Investigating (4) acpi-support [ amd64 ] < 0.138 > ( admin )
Broken acpi-support:amd64 Depends on acpid [ amd64 ] < 1:2.0.7-1ubuntu2 -> 1:2.0.10-1ubuntu2 > ( admin ) (>= 1.0.4-1ubuntu4)
  Considering acpid:amd64 136 as a solution to acpi-support:amd64 1
  Removing acpi-support:amd64 rather than change acpid:amd64
Investigating (4) screen [ amd64 ] < 4.0.3-14ubuntu7 -> 4.0.3-14ubuntu8 > ( misc )
Broken screen:amd64 Depends on upstart-job [ amd64 ] < none > ( none )
  Considering upstart:amd64 136 as a solution to screen:amd64 0
  Removing screen:amd64 rather than change upstart-job:amd64
Investigating (4) wine [ amd64 ] < 1.2.2-0ubuntu6 -> 1.2.3-0ubuntu1 > ( universe/otherosfs )
Broken wine:amd64 Depends on wine1.2 [ amd64 ] < 1.2.2-0ubuntu6 -> 1.2.3-0ubuntu1 > ( universe/otherosfs )
  Considering wine1.2:amd64 136 as a solution to wine:amd64 0
  Removing wine:amd64 rather than change wine1.2:amd64
Investigating (5) util-linux [ amd64 ] < 2.17.2-9.1ubuntu4 -> 2.19.1-2ubuntu3 > ( utils )
Broken util-linux:amd64 Depends on upstart-job [ amd64 ] < none > ( none )
  Considering upstart:amd64 136 as a solution to util-linux:amd64 5282
  Added upstart:amd64 to the remove list
  Fixing util-linux:amd64 via keep of upstart:amd64
Investigating (5) libgl1-mesa-glx [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
Broken libgl1-mesa-glx:amd64 Depends on libdrm2 [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libs ) (>= 2.3.1)
  Considering libdrm2:amd64 136 as a solution to libgl1-mesa-glx:amd64 174
  Added libdrm2:amd64 to the remove list
Broken libgl1-mesa-glx:amd64 Depends on libglapi-mesa [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs ) (= 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty)
  Considering libglapi-mesa:amd64 56 as a solution to libgl1-mesa-glx:amd64 174
  Added libglapi-mesa:amd64 to the remove list
  Fixing libgl1-mesa-glx:amd64 via keep of libdrm2:amd64
  Fixing libgl1-mesa-glx:amd64 via keep of libglapi-mesa:amd64
Investigating (5) netbase [ amd64 ] < 4.45ubuntu1 -> 4.45ubuntu3 > ( admin )
Broken netbase:amd64 Depends on initscripts [ amd64 ] < 2.87dsf-4ubuntu23 -> 2.88dsf-13.10ubuntu4 > ( admin )
  Considering initscripts:amd64 136 as a solution to netbase:amd64 161
  Added initscripts:amd64 to the remove list
  Fixing netbase:amd64 via keep of initscripts:amd64
Investigating (5) libdrm2 [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libs )
Broken libdrm2:amd64 Breaks on libdrm2 [ i386 ] < none -> 2.4.26-1ubuntu1 > ( libs ) (!= 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty)
  Considering libdrm2:i386 19 as a solution to libdrm2:amd64 174
  Added libdrm2:i386 to the remove list
  Fixing libdrm2:amd64 via keep of libdrm2:i386
 Try to Re-Instate (5) upstart:amd64
Investigating (5) upstart [ amd64 ] < 0.9.7-1 -> 1.3-0ubuntu10 > ( admin )
Broken upstart:amd64 Depends on mountall [ amd64 ] < 2.25ubuntu1 -> 2.31 > ( admin )
  Considering mountall:amd64 136 as a solution to upstart:amd64 5282
  Added mountall:amd64 to the remove list
Broken upstart:amd64 Depends on ifupdown [ amd64 ] < 0.6.10ubuntu4 -> 0.7~alpha5.1ubuntu5 > ( admin ) (>= 0.6.8ubuntu29)
  Considering ifupdown:amd64 136 as a solution to upstart:amd64 5282
  Added ifupdown:amd64 to the remove list
  Fixing upstart:amd64 via keep of mountall:amd64
  Fixing upstart:amd64 via keep of ifupdown:amd64
Investigating (5) libglapi-mesa [ amd64 ] < 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty > ( libs )
Broken libglapi-mesa:amd64 Breaks on libglapi-mesa [ i386 ] < none -> 7.11-0ubuntu3 > ( libs ) (!= 7.12.0~git20111012.ae1153c4-0ubuntu0sarvatt~natty)
  Considering libglapi-mesa:i386 2 as a solution to libglapi-mesa:amd64 174
  Added libglapi-mesa:i386 to the remove list
  Fixing libglapi-mesa:amd64 via keep of libglapi-mesa:i386
 Try to Re-Instate (5) initscripts:amd64
 Try to Re-Instate (5) phonon:amd64
Re-Instated phonon:amd64 (8 vs 8)
 Try to Re-Instate (5) binfmt-support:amd64
Re-Instated binfmt-support:amd64 (8 vs 8)
 Try to Re-Instate (5) ifupdown:amd64
 Try to Re-Instate (5) mountall:amd64
Investigating (5) mountall [ amd64 ] < 2.25ubuntu1 -> 2.31 > ( admin )
Broken mountall:amd64 Depends on plymouth [ amd64 ] < 0.8.2-2ubuntu23 -> 0.8.2-2ubuntu28 > ( x11 )
  Considering plymouth:amd64 136 as a solution to mountall:amd64 5282
  Added plymouth:amd64 to the remove list
  Fixing mountall:amd64 via keep of plymouth:amd64
Investigating (5) kbd [ amd64 ] < 1.15-1ubuntu5 -> 1.15.2-3ubuntu1 > ( utils )
Broken kbd:amd64 Depends on console-setup [ amd64 ] < 1.57ubuntu20 -> 1.57ubuntu27 > ( utils )
  Considering console-setup:amd64 136 as a solution to kbd:amd64 25
  Removing kbd:amd64 rather than change console-setup:amd64
Investigating (5) plymouth [ amd64 ] < 0.8.2-2ubuntu23 -> 0.8.2-2ubuntu28 > ( x11 )
Broken plymouth:amd64 Depends on libdrm-intel1 [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libs ) (>= 2.4.9)
  Considering libdrm-intel1:amd64 18 as a solution to plymouth:amd64 5282
  Added libdrm-intel1:amd64 to the remove list
Broken plymouth:amd64 Depends on libdrm-nouveau1a [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libs ) (>= 2.4.23)
  Considering libdrm-nouveau1a:amd64 17 as a solution to plymouth:amd64 5282
  Added libdrm-nouveau1a:amd64 to the remove list
Broken plymouth:amd64 Depends on libdrm-radeon1 [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libs ) (>= 2.4.17)
  Considering libdrm-radeon1:amd64 17 as a solution to plymouth:amd64 5282
  Added libdrm-radeon1:amd64 to the remove list
Broken plymouth:amd64 Depends on libplymouth2 [ amd64 ] < 0.8.2-2ubuntu23 -> 0.8.2-2ubuntu28 > ( libs ) (= 0.8.2-2ubuntu23)
  Considering libplymouth2:amd64 28 as a solution to plymouth:amd64 5282
  Added libplymouth2:amd64 to the remove list
  Fixing plymouth:amd64 via keep of libdrm-intel1:amd64
  Fixing plymouth:amd64 via keep of libdrm-nouveau1a:amd64
  Fixing plymouth:amd64 via keep of libdrm-radeon1:amd64
  Fixing plymouth:amd64 via keep of libplymouth2:amd64
 Try to Re-Instate (5) ntfs-3g:amd64
Investigating (5) logrotate [ amd64 ] < 3.7.8-6ubuntu3.1 -> 3.7.8-6ubuntu5 > ( admin )
Broken logrotate:amd64 Depends on cron [ amd64 ] < 3.0pl1-116ubuntu1 -> 3.0pl1-116ubuntu3 > ( admin )
  Considering cron:amd64 136 as a solution to logrotate:amd64 20
Broken logrotate:amd64 Depends on anacron [ amd64 ] < 2.3-14ubuntu1 > ( admin )
  Considering anacron:amd64 136 as a solution to logrotate:amd64 20
Broken logrotate:amd64 Depends on fcron [ amd64 ] < none > ( none )
  Or group remove for logrotate:amd64
Investigating (5) libdrm-intel1 [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libs )
Broken libdrm-intel1:amd64 Depends on libpciaccess0 [ amd64 ] < 0.12.1+git20110826.7bfc4f80-0ubuntu0sarvatt~natty2 > ( libs )
  Considering libpciaccess0:amd64 51 as a solution to libdrm-intel1:amd64 5282
  Added libpciaccess0:amd64 to the remove list
Broken libdrm-intel1:amd64 Breaks on libdrm-intel1 [ i386 ] < none -> 2.4.26-1ubuntu1 > ( libs ) (!= 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty)
  Considering libdrm-intel1:i386 4 as a solution to libdrm-intel1:amd64 5282
  Added libdrm-intel1:i386 to the remove list
  Fixing libdrm-intel1:amd64 via keep of libpciaccess0:amd64
  Fixing libdrm-intel1:amd64 via keep of libdrm-intel1:i386
Investigating (5) libdrm-radeon1 [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libs )
Broken libdrm-radeon1:amd64 Breaks on libdrm-radeon1 [ i386 ] < none -> 2.4.26-1ubuntu1 > ( libs ) (!= 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty)
  Considering libdrm-radeon1:i386 4 as a solution to libdrm-radeon1:amd64 5282
  Added libdrm-radeon1:i386 to the remove list
  Fixing libdrm-radeon1:amd64 via keep of libdrm-radeon1:i386
Investigating (5) libdrm-nouveau1a [ amd64 ] < 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty > ( libs )
Broken libdrm-nouveau1a:amd64 Breaks on libdrm-nouveau1a [ i386 ] < none -> 2.4.26-1ubuntu1 > ( libs ) (!= 2.4.26+git20110921.1459cb92-0ubuntu0sarvatt~natty)
  Considering libdrm-nouveau1a:i386 4 as a solution to libdrm-nouveau1a:amd64 5282
  Added libdrm-nouveau1a:i386 to the remove list
  Fixing libdrm-nouveau1a:amd64 via keep of libdrm-nouveau1a:i386
Investigating (5) libgl1-mesa-dri [ i386 ] < none -> 7.11-0ubuntu3 > ( libs )
Broken libgl1-mesa-dri:i386 Depends on libdrm-intel1 [ i386 ] < none -> 2.4.26-1ubuntu1 > ( libs ) (>= 2.4.23-3~)
  Considering libdrm-intel1:i386 5282 as a solution to libgl1-mesa-dri:i386 5
  Holding Back libgl1-mesa-dri:i386 rather than change libdrm-intel1:i386
Investigating (5) clamav-base [ amd64 ] < 0.97.2+dfsg-1ubuntu1.11.04 -> 0.97.2+dfsg-1ubuntu2 > ( utils )
Broken clamav-base:amd64 Depends on logrotate [ amd64 ] < 3.7.8-6ubuntu3.1 -> 3.7.8-6ubuntu5 > ( admin )
  Considering logrotate:amd64 20 as a solution to clamav-base:amd64 4
  Removing clamav-base:amd64 rather than change logrotate:amd64
 Try to Re-Instate (5) modemmanager:amd64
Re-Instated modemmanager:amd64 (4 vs 4)
Investigating (5) clamav-freshclam [ amd64 ] < 0.97.2+dfsg-1ubuntu1.11.04 -> 0.97.2+dfsg-1ubuntu2 > ( utils )
Broken clamav-freshclam:amd64 Depends on clamav-base [ amd64 ] < 0.97.2+dfsg-1ubuntu1.11.04 -> 0.97.2+dfsg-1ubuntu2 > ( utils ) (>= 0.97.2+dfsg-1ubuntu2)
  Considering clamav-base:amd64 20 as a solution to clamav-freshclam:amd64 2
  Removing clamav-freshclam:amd64 rather than change clamav-base:amd64
Investigating (5) libpciaccess0 [ i386 ] < none -> 0.12.1-2 > ( libs )
Broken libpciaccess0:i386 Breaks on libpciaccess0 [ amd64 ] < 0.12.1+git20110826.7bfc4f80-0ubuntu0sarvatt~natty2 > ( libs ) (!= 0.12.1-2)
  Considering libpciaccess0:amd64 5282 as a solution to libpciaccess0:i386 1
  Holding Back libpciaccess0:i386 rather than change libpciaccess0:amd64
Investigating (6) base-files [ amd64 ] < 5.0.0ubuntu28 -> 6.4ubuntu5 > ( admin )
Broken base-files:amd64 Breaks on initscripts [ amd64 ] < 2.87dsf-4ubuntu23 -> 2.88dsf-13.10ubuntu4 > ( admin ) (< 2.88dsf-13.3)
  Considering initscripts:amd64 161 as a solution to base-files:amd64 5229
  Upgrading initscripts:amd64 due to Breaks field in base-files:amd64
Investigating (6) initscripts [ amd64 ] < 2.87dsf-4ubuntu23 -> 2.88dsf-13.10ubuntu4 > ( admin )
Broken initscripts:amd64 Depends on mountall [ amd64 ] < 2.25ubuntu1 -> 2.31 > ( admin ) (>= 2.28)
  Considering mountall:amd64 5282 as a solution to initscripts:amd64 161
  Holding Back initscripts:amd64 rather than change mountall:amd64
 Try to Re-Instate (6) libplymouth2:amd64
Investigating (6) clamav [ amd64 ] < 0.97.2+dfsg-1ubuntu1.11.04 -> 0.97.2+dfsg-1ubuntu2 > ( utils )
Broken clamav:amd64 Depends on clamav-freshclam [ amd64 ] < 0.97.2+dfsg-1ubuntu1.11.04 -> 0.97.2+dfsg-1ubuntu2 > ( utils )
  Considering clamav-freshclam:amd64 20 as a solution to clamav:amd64 3
Broken clamav:amd64 Depends on clamav-data [ amd64 ] < none > ( none )
  Considering clamav-freshclam:amd64 20 as a solution to clamav:amd64 3
  Or group remove for clamav:amd64
Investigating (7) base-files [ amd64 ] < 5.0.0ubuntu28 -> 6.4ubuntu5 > ( admin )
Broken base-files:amd64 Breaks on initscripts [ amd64 ] < 2.87dsf-4ubuntu23 -> 2.88dsf-13.10ubuntu4 > ( admin ) (< 2.88dsf-13.3)
  Considering initscripts:amd64 161 as a solution to base-files:amd64 5229
  Upgrading initscripts:amd64 due to Breaks field in base-files:amd64
Investigating (7) initscripts [ amd64 ] < 2.87dsf-4ubuntu23 -> 2.88dsf-13.10ubuntu4 > ( admin )
Broken initscripts:amd64 Depends on mountall [ amd64 ] < 2.25ubuntu1 -> 2.31 > ( admin ) (>= 2.28)
  Considering mountall:amd64 5282 as a solution to initscripts:amd64 161
  Holding Back initscripts:amd64 rather than change mountall:amd64
Investigating (8) base-files [ amd64 ] < 5.0.0ubuntu28 -> 6.4ubuntu5 > ( admin )
Broken base-files:amd64 Breaks on initscripts [ amd64 ] < 2.87dsf-4ubuntu23 -> 2.88dsf-13.10ubuntu4 > ( admin ) (< 2.88dsf-13.3)
  Considering initscripts:amd64 161 as a solution to base-files:amd64 5229
  Upgrading initscripts:amd64 due to Breaks field in base-files:amd64
Investigating (8) initscripts [ amd64 ] < 2.87dsf-4ubuntu23 -> 2.88dsf-13.10ubuntu4 > ( admin )
Broken initscripts:amd64 Depends on mountall [ amd64 ] < 2.25ubuntu1 -> 2.31 > ( admin ) (>= 2.28)
  Considering mountall:amd64 5282 as a solution to initscripts:amd64 161
  Holding Back initscripts:amd64 rather than change mountall:amd64
Investigating (9) base-files [ amd64 ] < 5.0.0ubuntu28 -> 6.4ubuntu5 > ( admin )
Broken base-files:amd64 Breaks on initscripts [ amd64 ] < 2.87dsf-4ubuntu23 -> 2.88dsf-13.10ubuntu4 > ( admin ) (< 2.88dsf-13.3)
  Considering initscripts:amd64 161 as a solution to base-files:amd64 5229
  Upgrading initscripts:amd64 due to Breaks field in base-files:amd64
Investigating (9) initscripts [ amd64 ] < 2.87dsf-4ubuntu23 -> 2.88dsf-13.10ubuntu4 > ( admin )
Broken initscripts:amd64 Depends on mountall [ amd64 ] < 2.25ubuntu1 -> 2.31 > ( admin ) (>= 2.28)
  Considering mountall:amd64 5282 as a solution to initscripts:amd64 161
  Holding Back initscripts:amd64 rather than change mountall:amd64
Done
Log time: 2011-10-17 18:35:19.998583
```

Ctrl+F shows some instances of "holding back".

---

### Post by 23dornot23d on 2011-10-17
Can you show us the 

**/etc/apt/souces.list**

please

copy and paste it between code tags ....

---

### Post by SoylentSteak on 2011-10-17
```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu natty main restricted
deb-src http://archive.ubuntu.com/ubuntu natty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu natty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu natty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu natty universe
deb http://archive.ubuntu.com/ubuntu natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu natty multiverse
deb http://archive.ubuntu.com/ubuntu natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.

deb http://archive.ubuntu.com/ubuntu natty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu natty-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu natty-security universe
deb http://archive.ubuntu.com/ubuntu natty-security multiverse
```

---

### Post by 23dornot23d on 2011-10-17
[I]Try these ..... in a terminal ...... they are the way I upgraded ...... early on ...
( it may solve the problem .... or it may give us something to work with .... )

sudo sed -i 's/natty/oneiric/g' /etc/apt/sources.list

sudo apt-get update
sudo apt-get install aptitude

sudo aptitude update
sudo aptitude dist-upgrade[/I]

---

### Post by SoylentSteak on 2011-10-17
That seems to be working...so far.

---

### Post by 23dornot23d on 2011-10-17
Good to hear .... give me a copy of the output from the very last command if you can ....

before saying yes to it ...... ( if you haven't already done so )

it may show some dependency problems (it may not .... if not just carry on ...)

---

### Post by SoylentSteak on 2011-10-17
The terminal is currently too busy scrolling out lines, but if something goes wrong, I'll keep you informed. I hope it continues to go smoothly.

And I typed "yes" before you edited your post. :?:

---

### Post by 23dornot23d on 2011-10-17
me too ........ reading some of the problems earlier on in the upgrading
the flash-installer was causing a problem .... but that should be fixed by now ....

so unless there is something else amiss .... it should go ok ;)

No problem .... to the answering yes .... we will see after it finishes if the main things are there
to run a session up .....

---

### Post by SoylentSteak on 2011-10-17
It should be completed within an hour, so we'll see then. I've got my important stuff backed up.

---

### Post by 23dornot23d on 2011-10-17
Ok good to know ...... and the graphics card is what type on it .... ?

---

### Post by SoylentSteak on 2011-10-17
Integrated ATI Radeon Xpress 200.

---

### Post by 23dornot23d on 2011-10-17
ok the ATI radeons - fglx is causing some problems .... we will have to see how
well it picks it up .....

[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide)

---

### Post by SoylentSteak on 2011-10-17
Before upgrading, some nvidia x.org packages were held back, so I'm thinking that might have had something to do with it. After I removed some repositories, that stuff disappeared.

---

### Post by 23dornot23d on 2011-10-17
have all the packages downloaded yet and are they unpacking or setting up now .....

---

### Post by SoylentSteak on 2011-10-17
An estimated 5 minutes to complete downloading.

---

### Post by 23dornot23d on 2011-10-17
ok it usually takes as long to unpack and set-up ....

but [COLOR=Red]**do not reboot**[/COLOR] ...... after the download and setting up ...

**We need to check some thing out ...... certain packages and things ....**

---

### Post by SoylentSteak on 2011-10-17
Okie dokie.

---

### Post by SoylentSteak on 2011-10-17
"Configuring gdm" has popped up. I can go to gdm, kdm, or lightdm.

---

### Post by 23dornot23d on 2011-10-17
You seem to be running kubuntu .... kdm is the one for that .....

or are you running something else ?

---

### Post by SoylentSteak on 2011-10-17
It's just normal Ubuntu.

---

### Post by 23dornot23d on 2011-10-17
ok lightdm then



I was reading the beginning of your log where it stated this  ..... thats why I asked ...
> 
Log time: 2011-10-17 18:34:57.342433   Installing kde-runtime as Depends of kubuntu-debug-installer     Installing kde-runtime-data as Depends of kde-runtime   Installing libmono-cairo4.0-cil as Depends of f-spot



You spotted any errors yet .... or is it all ok ..... watch carefully when it sets the kernel and the graphics driver

---

### Post by SoylentSteak on 2011-10-17
Unpacking stuff now.

BTW, thanks for the detailed help. :)

---

### Post by 23dornot23d on 2011-10-17
Ok your welcome 

Watch for any errors .... especially as it sets the kernel and the graphics drivers up .....

sometime you can tell here ..... there will be a red [COLOR=Red]**FAIL**[/COLOR] ..in the text... if it does not work properly

---

### Post by SoylentSteak on 2011-10-17
"Configuring libpam0g: amd64"

"Services to restart for PAM library upgrade:

cups cron atd

Asking me if it's okay.

---

### Post by 23dornot23d on 2011-10-17
yes ....  its ok .... as long as its not asking to restart the desktop manager ....

cups is printing - cron is a job shdeduler .... and atd runs jobs

we need the desktop to work from ..... its easier .....

---

### Post by SoylentSteak on 2011-10-17
Unpacking, and going smoothly.

---

### Post by 23dornot23d on 2011-10-17
ok nice ... it tends to go in batches .... until it reaches any problems ....

then it may drop out and say had problem with certain packages .....

best to note them down if it happens ....

---

### Post by 23dornot23d on 2011-10-17
Are things ok or is there a problem - seems a awful long time .... passed ...... 

40 mins ... since your last response

and

2 hours ... since we started ....

---

### Post by SoylentSteak on 2011-10-17
Fine so far. But yes, it has been taking a long time.

---

### Post by 23dornot23d on 2011-10-17
Ok good to know ..... what packages is it installing at present .....

it may give me an idea where your at  ..... as its 3:26 am here

---

### Post by SoylentSteak on 2011-10-17
Just finished! No failures, but it said there were 2 broken packages. It doesn't specify what they were.

---

### Post by 23dornot23d on 2011-10-17
ok copy the bottom 20 or so lines and post them if you would please ....

will just give me some idea of what you can see there

---

### Post by SoylentSteak on 2011-10-17
```
Setting up kinfocenter (4:4.7.1-0ubuntu5) ...
Setting up konqueror-nsplugins (4:4.7.1-0ubuntu3) ...
Setting up kubuntu-debug-installer (11.10ubuntu1) ...
Setting up libappindicator0.1-cil (0.4.1-0ubuntu2) ...
* Installing 3 assemblies from libappindicator0.1-cil into Mono
Setting up libgmime2.4-cil (2.4.26-0ubuntu2) ...
* Installing 1 assembly from libgmime2.4-cil into Mono
Setting up libndesk-dbus-glib1.0-cil (0.4.1-3build1) ...
* Installing 1 assembly from libndesk-dbus-glib1.0-cil into Mono
Setting up mono-2.0-gac (2.10.5-1) ...
Setting up sysinfo (0.7-6) ...
Setting up tomboy (1.8.0-1ubuntu1) ...
Setting up ubuntu-artwork (54) ...
Setting up update-manager-kde (1:0.152.25) ...
Setting up libmono-system-web4.0-cil (2.10.5-1) ...
Setting up libflickrnet2.2-cil (1:2.2.0-3build1) ...
* Installing 1 assembly from libflickrnet2.2-cil into Mono
Setting up f-spot (0.8.2-4) ...
Processing triggers for libreoffice-common ...
Updating services.rdb...
done.
Setting up openoffice.org-common (1:3.3.0-7ubuntu4) ...
Setting up libreoffice-l10n-en-za (1:3.4.3-1ubuntu1) ...
Setting up openoffice.org-l10n-en-za (1:3.3.0-7ubuntu4) ...
Processing triggers for tex-common ...
Running mktexlsr. This may take some time... done.
Running updmap-sys. This may take some time... done.
Running mktexlsr /var/lib/texmf ... done.
Building e-tex based formats --byhyphen /var/lib/texmf/tex/generic/config/language.def.
	This may take some time... done.
Setting up texlive-latex-base (2009-13) ...
Running mktexlsr. This may take some time... done.
Building format(s) --all --cnffile /etc/texmf/fmt.d/10texlive-latex-base.cnf.
	This may take some time... done.
Setting up texlive-luatex (2009-13) ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up language-pack-gnome-en (1:11.10+20111006) ...
Setting up language-pack-kde-en (1:11.10+20111006) ...
Setting up kde-l10n-engb (4:4.7.1-0ubuntu1) ...
Setting up language-pack-gnome-en-base (1:11.10+20111006) ...
Setting up language-pack-kde-en-base (1:11.10+20111006) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-12-generic
Processing triggers for python-support ...
Processing triggers for menu ...
Processing triggers for python-central ...
Processing triggers for tex-common ...
Running mktexlsr. This may take some time... done.
Running updmap-sys. This may take some time... done.
Running mktexlsr /var/lib/texmf ... done.
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
                                         
Current status: 2 broken [+2], 0 updates [-1721], 3 new [+3].
There are 3 newly obsolete packages: gens, guitarpro6, rejoystick
chris@chris-desktop:~$ 

```

---

### Post by 23dornot23d on 2011-10-17
Ok looks pretty good ....

sudo aptitude install lightdm

I just want to make sure the display manger loaded ..... it will probably come back with
  its already installed .....

but I would rather check first

let me see the output ..... too .... if you would please

It is 4:00 am here now and I have been going for 16 solid ... today ....
so if you could let me know what is happening I would appreciate it .... ty

---

### Post by SoylentSteak on 2011-10-17
The system went haywire and crashed. Upon reboot, it can't load the file system. I appreciate all your help, but now it looks as though it will be easier to do a clean install. :(

---

### Post by 23dornot23d on 2011-10-17
ok sorry to hear that ...... what happened for it to go haywire ....

can you get to the logs - to see where it failed

cd /var/log/

check syslog and kern.log

the last command should just have checked that lightdm was installed...

ok hope you get the system back as you want it .... you can always choose the older

kernel in the grub menu ... see if that makes any difference to it starting

The other thing is the ATI graphics  ..... different drivers have been tried as it can lock up at boot.

---

### Post by SoylentSteak on 2011-10-17
The update manager popped up, and didn't accept my valid password. Then,everything disappeard, except for the bare desktop. I had no control over anything and had to do a hard reboot. I'm going to bed now. I think I'll just do a clean install when I can borrow a live cd from my uncle. It may be a few days from now, but I'll let you know when it happens. Good night.

---

### Post by 23dornot23d on 2011-10-17
We can always try some more things tomorrow .... the system upgraded and there were no errors .... the update manager popping up ...... just unfortunate ....

But all the files are on the disk now for 11.10 ......  

I rarely fail to get a system going 

Upto you tomorrow is another day ....

Night ... have a good rest and I will think of possibilities .... 

_________________________________________________________________

had a kip ... for 30 mins ..

Leave me a message tomorrow if you can get to the terminal in safe-mode
we can look at the logs to see what problems there are .....

If it works in safe-mode ..... we should be able to get the graphics working .... ;)

and see if there are any other problems ..... ( we can rescue this system )

check the bottom link in my footer if its a password problem stopping you still ..... Xauthority was the cause

---

### Post by LordNodens on 2011-10-20
I also had the same problem with the upgrade from 11.04 x64 and this is what I need:

[LIST=1]
[*]Checked the apt.log in /var/log/dist-upgrade
[*]Found the lines that were saying "Holding Back nameofthepackeage..."
[*]There were a lot of them, so I decided to remove at first the package that appeared the most which was "nspluginwrapper"
[*]Run again the upgrade and the message disappeared.
[/LIST]

PS. After rebooting I encountered the kernel panic error. I found the solution and posted it in the forum.

---

