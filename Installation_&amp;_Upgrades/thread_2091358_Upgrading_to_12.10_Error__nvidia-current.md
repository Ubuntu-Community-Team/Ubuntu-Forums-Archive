---
title: "Upgrading to 12.10 Error : nvidia-current"
date: 2012-12-04
forum: Installation &amp; Upgrades
---

### Post by costis on 2012-12-04
Dear community,

I had ubuntu 12.04.01 and did a distribution upgrade to 12.10 through unity, but it stalled somewhere (the machine was frozen), so I continued with # apt-get dist-upgrade after a restart. The problem is that I get:
```

# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 compiz-kde : Depends: compiz-core (= 1:0.9.7.8-0ubuntu1.4) but 1:0.9.8.4+bzr3407-0ubuntu1 is installed
              Depends: compiz-plugins-default (= 1:0.9.7.8-0ubuntu1.4) but 1:0.9.8.4+bzr3407-0ubuntu1 is installed
 libcompizconfig0 : Depends: compiz-core-abiversion-20120305 but it is not installable
 libdecoration0-dev : Depends: libdecoration0 (= 1:0.9.7.8-0ubuntu1.4) but 1:0.9.8.4+bzr3407-0ubuntu1 is installed
 libgnome-desktop-3-2 : Depends: gnome-desktop3-data (= 3.4.2-0ubuntu0.1) but 3.6.0.1-0ubuntu2 is installed
 libunity-core-5.0-5 : Depends: unity-services (= 5.16.0-0ubuntu1) but 6.10.0-0ubuntu2 is installed
 xserver-xorg-video-ati : Depends: xorg-video-abi-13
                          Depends: xserver-xorg-core (>= 2:1.12.99.901) but 2:1.11.4-0ubuntu10.8 is installed
 xserver-xorg-video-intel : Depends: xorg-video-abi-13
                            Depends: xserver-xorg-core (>= 2:1.12.99.901) but 2:1.11.4-0ubuntu10.8 is installed
 xserver-xorg-video-mach64 : Depends: xorg-video-abi-13
                             Depends: xserver-xorg-core (>= 2:1.12.99.901) but 2:1.11.4-0ubuntu10.8 is installed
 xserver-xorg-video-s3 : Depends: xorg-video-abi-13
                         Depends: xserver-xorg-core (>= 2:1.12.99.901) but 2:1.11.4-0ubuntu10.8 is installed
 xserver-xorg-video-siliconmotion : Depends: xorg-video-abi-13
                                    Depends: xserver-xorg-core (>= 2:1.12.99.901) but 2:1.11.4-0ubuntu10.8 is installed
 xserver-xorg-video-trident : Depends: xorg-video-abi-13
                              Depends: xserver-xorg-core (>= 2:1.12.99.901) but 2:1.11.4-0ubuntu10.8 is installed
E: Unmet dependencies. Try using -f.
```

Trying the -f option I get:
```
# apt-get dist-upgrade -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  compiz-kde gnuplot-nox indicator-messages-gtk2 indicator-status-provider-mc5 indicator-status-provider-pidgin language-pack-kde-el-base libatk-adaptor-schemas libboost-all-dev libboost-date-time-dev
  libboost-date-time1.46-dev libboost-filesystem1.46-dev libboost-graph-dev libboost-graph-parallel-dev libboost-graph-parallel1.46-dev libboost-graph1.46-dev libboost-iostreams1.46-dev libboost-math1.46-dev
  libboost-mpi-dev libboost-mpi-python-dev libboost-mpi1.46-dev libboost-program-options1.46-dev libboost-python1.46-dev libboost-regex1.46-dev libboost-serialization-dev libboost-serialization1.46-dev
  libboost-signals1.46-dev libboost-system1.46-dev libboost-test-dev libboost-test1.46-dev libboost-thread-dev libboost-thread1.46-dev libboost-wave-dev libboost-wave1.46-dev libboost1.46-dev libcheese-gtk21
  libcheese3 libevince3-3 libexttextcat0 libgnome-desktop-3-2 libgwibber-gtk2 libgwibber2 libindicator-messages-status-provider1 libkdegames5a libmlt4 liboverlay-scrollbar-0.2-0 liboverlay-scrollbar3-0.2-0
  librpm2 librpmbuild2 librpmsign0 libunity-core-5.0-5 libupnp3 nvidia-current python-mlt3 python-speechd smbfs ubuntu-sso-client-gtk xfce4-utils xserver-xorg-video-apm xserver-xorg-video-ark
  xserver-xorg-video-i128 xserver-xorg-video-rendition xserver-xorg-video-s3virge xserver-xorg-video-voodoo xz-lzma
The following NEW packages will be installed:
  account-plugin-facebook account-plugin-flickr account-plugin-google account-plugin-identica account-plugin-twitter akonadi-facebook antlr3 apper-data aptitude-common aspectj audiocd-kio augeas-lenses
  calligra-data calligra-l10n-el calligra-libs colord-kde cpp-4.7 cracklib-runtime distro-info-data erlang-asn1 erlang-eunit erlang-os-mon erlang-snmp erlang-tools erlang-webtool finger fonts-freefont-otf
  fonts-freefont-ttf fonts-lklug-sinhala fonts-lyx fonts-sil-abyssinica fonts-sil-padauk fonts-tibetan-machine freerdp-x11 g++-4.7 gcc-4.7 gfortran-4.7 gir1.2-accounts-1.0 gir1.2-messagingmenu-1.0
  gir1.2-signon-1.0 gnome-themes-standard gstreamer1.0-plugins-bad gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-x hardening-includes icedtea-7-jre-jamvm icedtea-7-plugin k3b-i18n kamoso
  kde-base-artwork kde-config-gtk-style kde-config-tablet kde-config-telepathy-accounts kde-telepathy kde-telepathy-approver kde-telepathy-auth-handler kde-telepathy-contact-list kde-telepathy-data
  kde-telepathy-filetransfer-handler kde-telepathy-integration-module kde-telepathy-minimal kde-telepathy-send-file kde-telepathy-text-ui kdegames-data kdevelop-l10n kdevelop-php-docs-l10n kdevelop-php-l10n
  kexi krdc krita krita-data libaccounts-qt1 liballegro4.4 liballegro4.4-plugin-alsa libamd2.2.0 libantlr-java libapt-inst1.5 libarchive-zip-perl libaspectj-java libasprintf0c2 libatk-adaptor-data libattica0.4
  libaudiocdplugins4 libaudit0 libaugeas0 libbabl-0.1-0 libblas3 libbobcat3 libboost-chrono-dev libboost-chrono1.49-dev libboost-chrono1.49.0 libboost-date-time1.49.0 libboost-filesystem1.49-dev
  libboost-filesystem1.49.0 libboost-graph-parallel1.49.0 libboost-graph1.49.0 libboost-iostreams1.49-dev libboost-iostreams1.49.0 libboost-locale-dev libboost-locale1.49-dev libboost-locale1.49.0
  libboost-math1.49-dev libboost-math1.49.0 libboost-mpi-python1.49.0 libboost-mpi1.49.0 libboost-program-options1.49-dev libboost-program-options1.49.0 libboost-python1.49-dev libboost-python1.49.0
  libboost-random-dev libboost-random1.49-dev libboost-random1.49.0 libboost-regex1.49-dev libboost-regex1.49.0 libboost-serialization1.49.0 libboost-signals1.49-dev libboost-signals1.49.0
  libboost-system1.49-dev libboost-system1.49.0 libboost-test1.49.0 libboost-thread1.49.0 libboost-timer-dev libboost-timer1.49-dev libboost-timer1.49.0 libboost-wave1.49.0 libboost1.49-dev libcggl
  libcheese-gtk23 libcheese7 libchm1 libclutter-gst-2.0-0 libclutter-imcontext-0.1-bin libcmis-0.2-2 libconfig++9 libcrack2 libdistro-info-perl libevdocument3-4 libevview3-3 libexiv2-12 libexttextcat-1.0-0
  libfile-fcntllock-perl libfontembed1 libfreerdp-plugins-standard libfreerdp1 libgdata2.1-cil libgegl-0.2-0 libgeronimo-jpa-2.0-spec-java libgeronimo-osgi-support-java libgstreamer-plugins-bad1.0-0
  libgstreamer-plugins-base1.0-0 libgstreamer1.0-0 libgtlcore0.8 libgtlfragment0.8 libgusb2 libgwibber-gtk3 libgwibber3 libgxps2 libindi0b libintl-perl libitm1 libjbig-dev libjs-jquery-form libjs-sphinxdoc
  libjs-underscore libkcompactdisc4 libkdcraw21 libkdecorations4abi1 libkdegames6 libkexiv2-11 libkgapi0 libkipi9 libkolab0 libkolabxml0 libktorrent4 libktpchat0 libktpcommoninternalsprivate3
  libkwineffects1abi4 libkwinglutils1abi1 libkworkspace4abi2 liblapack3 liblastfm1 liblightdm-qt-2-0 liblilv-0-0 liblinear-tools liblinear1 libmagick++5 libmagickcore5 libmagickcore5-extra libmagickwand5
  libmailimporter4 libmarblewidget14 libmediastreamer1 libmediawiki1 libmlt5 libmodule-implementation-perl libmono-system-runtime-serialization4.0-cil libmono-system-xml-linq4.0-cil libmx-bin libmx-common
  libnb-org-openide-modules-java libnb-org-openide-util-java libnb-org-openide-util-lookup-java libnb-platform13-java libnepomukcore4abi1 libnetcf1 libnewtonsoft-json4.5-cil libnova-0.14-0 libnss-winbind
  libnunit2.6-cil libopenconnect2 libopenctl0.8 libopenshiva0.8 libopus0 libortp8 libosgi-compendium-java libosgi-core-java libosgi-foundation-ee-java libpam-freerdp libpoppler-qt4-4 libprocps0 libpwquality1
  libqalculate5-data libqoauth1 libqpdf8 libqtgstreamerui-0.10-0 libqtshiva0.1 libreoffice-pdfimport librpm3 librpmbuild3 librpmio3 librpmsign1 libruby1.9.1 libsbsms10 libserd-0-0 libserf1 libservlet3.0-java
  libsord-0-0 libsox2 libspnav0 libsratom-0-0 libsrtp0 libssh2-1 libstdc++6-4.7-dev libstringtemplate-java libtaglib2.1-cil libtbb2 libtelepathy-logger-qt4-1 libtelepathy-qt4-2 libumfpack5.4.0 libupnp6
  libusb-1.0-0:i386 libvncserver0 libwebp2 libwebp2:i386 libx264-123 libxerces-c3.1 libxfce4ui-utils libxfce4util6 libyajl2 libyaml-0-2 lightdm-kde-greeter lightdm-remote-session-freerdp
  lightdm-remote-session-uccsconfigure linux-headers-3.5.0-19 linux-headers-3.5.0-19-generic linux-image-3.5.0-19-generic linux-image-extra-3.5.0-19-generic nepomuk-core nepomuk-core-data nvidia-cg-dev
  openjdk-7-jre openjdk-7-jre-headless openjdk-7-jre-lib overlay-scrollbar-gtk2 overlay-scrollbar-gtk3 packagekit-tools plasma-widget-telepathy-chat plasma-widget-telepathy-presence print-manager
  python-liblarch python-liblarch-gtk python-mlt5 python-six python3-apport python3-apt python3-aptdaemon python3-aptdaemon.gtk3widgets python3-brlapi python3-cairo python3-defer python3-distupgrade
  python3-gdbm python3-gi python3-gi-cairo python3-louis python3-lxml python3-pkg-resources python3-problem-report python3-pyatspi2 python3-pycurl python3-pykde4 python3-pyqt4 python3-sip
  python3-software-properties python3-speechd python3-update-manager python3-virtkey python3-xkit qpdf remote-login-service ruby1.9.1 signon-keyring-extension signon-plugin-oauth2 signon-ui skanlite
  syslinux-themes-debian-wheezy thin-client-config-agent ubuntu-drivers-common ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk ubuntu-release-upgrader-qt ubuntu-wallpapers-quantal unity-lens-gwibber
  vcdimager x11proto-scrnsaver-dev x11proto-xf86dri-dev xbrlapi xserver-xephyr xserver-xorg-video-dummy xserver-xorg-video-modesetting
The following packages have been kept back:
  nvidia-settings nvidia-settings-updates
The following packages will be upgraded:
  abiword abiword-plugin-grammar abiword-plugin-mathview akonadi-backend-mysql akonadi-server akregator amarok amarok-common amarok-dbg amarok-utils apparmor-utils apper apport apport-gtk apport-kde apt-utils
  aptdaemon aptitude apturl apturl-common apturl-kde ardour ark audacity audacity-data audex banshee banshee-extension-alarm banshee-extension-appindicator banshee-extension-awn
  banshee-extension-coverwallpaper banshee-extension-lcd banshee-extension-lirc banshee-extension-liveradio banshee-extension-lyrics banshee-extension-magnatune banshee-extension-mirage
  banshee-extension-openvp banshee-extension-radiostationfetcher banshee-extension-soundmenu banshee-extension-streamrecorder banshee-extension-telepathy banshee-extensions-common baobab brltty brltty-x11
  checkbox checkbox-gtk cheese cheese-common cifs-utils colord command-not-found couchdb-bin cpp cups-filters debhelper deluge deluge-common deluge-gtk devscripts digikam digikam-data dolphin dpkg-dev
  dragonplayer enblend enfuse eog erlang-base erlang-crypto erlang-inets erlang-mnesia erlang-public-key erlang-runtime-tools erlang-ssl erlang-syntax-tools erlang-xmerl evince evince-common exiv2 exo-utils
  ffmpeg foomatic-db-compressed-ppds freespacenotifier g++ gcc gdm gettext gettext-base gfortran gimp gimp-data gimp-gmic gimp-plugin-registry gir1.2-totem-1.0 gir1.2-unity-5.0 gmusicbrowser gnash gnash-common
  gnome-applets gnome-applets-data gnome-disk-utility gnome-nettool gnome-orca gnome-screensaver gnome-session gnome-session-bin gnome-session-common gnome-session-fallback gnome-system-log gnome-user-share
  gnuplot-x11 grub-common grub-pc grub-pc-bin grub2-common gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gtg gwenview gwibber gwibber-service gwibber-service-facebook gwibber-service-identica
  gwibber-service-twitter hugin hugin-data hugin-tools icedtea-plugin imagemagick indicator-appmenu indicator-messages inkscape intel-gpu-tools juk k3b k3b-data kaccessible kaddressbook kamera kate kate-dbg
  katepart kcalc kde-baseapps kde-baseapps-bin kde-baseapps-data kde-plasma-desktop kde-runtime kde-runtime-data kde-runtime-dbg kde-standard kde-style-oxygen kde-window-manager kde-window-manager-common
  kde-workspace kde-workspace-bin kde-workspace-data kde-workspace-kgreet-plugins kde-zeroconf kdeartwork kdeartwork-theme-window kdegraphics-mobipocket kdegraphics-thumbnailers kdelibs-bin kdelibs5-data
  kdelibs5-dbg kdelibs5-dev kdelibs5-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdepasswd kdepim-kresources kdepim-runtime kdepim-strigi-plugins kdepimlibs-kio-plugins kdeplasma-addons kdm
  kdoctools kfind khelpcenter4 kinfocenter kipi-plugins kipi-plugins-common klipper kmag kmail kmenuedit kmix kmousetool knotes kompare konq-plugins konqueror konqueror-nsplugins konsole konsole-dbg kontact
  kopete korganizer kpat kppp krename kscreensaver kscreensaver-xsavers ksnapshot kstars ksysguard ksysguardd ktorrent ktorrent-data ktouch kubuntu-desktop kubuntu-notification-helper kwalletmanager kwrite
  language-pack-kde-el language-selector-common language-selector-gnome language-selector-kde libakonadi-calendar4 libakonadi-contact4 libakonadi-kcal4 libakonadi-kde4 libakonadi-kmime4 libakonadi-notes4
  libakonadiprotocolinternals1 libatk-adaptor libav-tools libavcodec-extra-53 libavdevice53 libavfilter2 libavformat53 libavutil-extra-51 libblas-dev libblas3gf libboost-dev libboost-filesystem-dev
  libboost-iostreams-dev libboost-math-dev libboost-program-options-dev libboost-python-dev libboost-regex-dev libboost-signals-dev libboost-system-dev libcalendarsupport4 libcg libclass-load-perl
  libclutter-imcontext-0.1-0 libcompizconfig0 libdecoration0-dev libdevil1c2 libdpkg-perl libequinox-osgi-java libeventviews4 libexo-1-0 libexttextcat-data libffado2 libgarcon-1-0 libgettextpo0
  libgettextpo0:i386 libgexiv2-1 libgimp2.0 libgpod-common libgstreamer-plugins-bad0.10-0 libgtkmm-3.0-1 libincidenceeditorsng4 libk3b6 libkabc4 libkactivities-bin libkactivities6 libkalarmcal2
  libkateinterfaces4 libkatepartinterfaces4 libkblog4 libkcal4 libkcalcore4 libkcalutils4 libkcddb4 libkcmutils4 libkde3support4 libkdeclarative5 libkdecore5 libkdepim4 libkdepimdbusinterfaces4 libkdesu5
  libkdeui5 libkdewebkit5 libkdgantt2 libkdnssd4 libkemoticons4 libkephal4abi1 libkfile4 libkgeomap1 libkholidays4 libkhtml5 libkidletime4 libkimap4 libkimproxy4 libkio5 libkjsapi4 libkjsembed4 libkldap4
  libkleo4 libkmanagesieve4 libkmbox4 libkmediaplayer4 libkmime4 libknewstuff2-4 libknewstuff3-4 libknotifyconfig4 libkntlm4 libkonq-common libkonq5abi1 libkonqsidebarplugin4a libkontactinterface4
  libkopete-dev libkopete4 libkparts4 libkpgp4 libkpimidentities4 libkpimtextedit4 libkpimutils4 libkprintutils4 libkpty4 libkresources4 libkrosscore4 libkrossui4 libksane0 libkscreensaver5 libksgrd4
  libksieve4 libksieveui4 libksignalplotter4 libktexteditor4 libktnef4 libktorrent-l10n libkunitconversion4 libkutils4 libkwinnvidiahack4 libkxmlrpcclient4 liblapack-dev liblapack3gf libmailcommon4
  libmailtransport4 libmessagecomposer4 libmessagecore4 libmessagelist4 libmessageviewer4 libmicroblog4 libmlt++3 libmuonprivate1 libmutter0 libmx-1.0-2 libnepomuk4 libnepomukquery4a libnepomuksync4
  libnepomukutils4 libokularcore1abi1 libopencv-calib3d2.3 libopencv-core2.3 libopencv-features2d2.3 libopencv-flann2.3 libopencv-highgui2.3 libopencv-imgproc2.3 libopencv-legacy2.3 libopencv-objdetect2.3
  libopencv-video2.3 libpackagekit-glib2-14 libpackagekit-qt2-2 libpam-smbpass libpam-winbind libparams-validate-perl libplasma-geolocation-interface4 libplasma3 libplasmaclock4abi3 libplasmagenericshell4
  libpostproc52 libprocesscore4abi1 libprocessui4a libprojectm2 libqalculate5 libqapt1 libquicktime2 libraptor2-0 libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw
  libreoffice-help-en-gb libreoffice-help-en-us libreoffice-impress libreoffice-kde libreoffice-l10n-el libreoffice-l10n-en-gb libreoffice-l10n-en-za libreoffice-math libreoffice-style-oxygen
  libreoffice-style-tango libreoffice-writer libsane libsane:i386 libsane-common libsdl-image1.2 libsdl-image1.2:i386 libsdl-image1.2-dev libsolid4 libsolidcontrol4abi2 libsolidcontrolifaces4abi2
  libsoprano-dev libsoprano4 libsox-fmt-alsa libsox-fmt-base libstreamanalyzer0 libstreams0 libsvn1 libswscale2 libsyndication4 libtaoframework-sdl1.2-cil libtaskmanager4abi3 libtemplateparser4
  libthreadweaver4 libthunarx-2-0 libtiff4 libtiff4:i386 libtiff4-dev libtiffxx0c2 libtorrent-rasterbar6 libtotem0 libvirt-bin libvirt0 libwbclient0 libweather-ion6 libxatracker1 libxfce4ui-1-0
  libxfce4util-bin libxfcegui4-4 lintian linux-headers-generic linux-image-generic lsb-core lsb-release marble-plugins melt mencoder mousepad muon muon-installer muon-notifier muon-updater mutter mutter-common
  network-manager-gnome nmap nvidia-cg-toolkit nvidia-common nvidia-current-updates okular okular-extra-backends onboard openprinting-ppds orage otf-freefont overlay-scrollbar packagekit
  packagekit-backend-aptcc parole pdfcube perlmagick plasma-containments-addons plasma-dataengines-addons plasma-dataengines-workspace plasma-desktop plasma-netbook plasma-runners-addons
  plasma-scriptengine-javascript plasma-wallpapers-addons plasma-widget-folderview plasma-widget-kimpanel plasma-widget-lancelot plasma-widget-networkmanagement plasma-widgets-addons plasma-widgets-workspace
  printer-driver-foo2zjs printer-driver-postscript-hp printer-driver-ptouch printer-driver-pxljr procps projectm-dbg python-apt python-aptdaemon python-aptdaemon-gtk python-aptdaemon.gtk3widgets
  python-aptdaemon.gtkwidgets python-debian python-kde4 python-libtorrent python-libvirt python-transmissionrpc python-ubuntu-sso-client python-uno python-wimpiggy qapt-deb-installer r-base r-base-core
  r-base-dev r-cran-boot r-cran-class r-cran-foreign r-cran-kernsmooth r-cran-lattice r-cran-mass r-cran-matrix r-cran-mgcv r-cran-nlme r-cran-nnet r-cran-rpart r-cran-spatial r-cran-survival r-mathlib
  r-recommended rekonq ristretto rpm rpm-common rpm2cpio ruby samba samba-common screen-resolution-extra shotwell smbclient software-center software-center-aptdaemon-plugins software-properties-common
  software-properties-gtk software-properties-kde soprano-daemon sox spring spring-common subversion sweeper synaptic syslinux-themes-debian systemsettings telepathy-indicator thunar thunar-data thunar-volman
  totem totem-common totem-mozilla totem-plugins ttf-freefont ttf-lyx ubuntu-minimal ubuntu-sso-client ubuntu-wallpapers ufw unattended-upgrades unity-greeter unity-scope-musicstores unity-scope-video-remote
  update-manager update-manager-core update-manager-kde update-notifier update-notifier-common upower vinagre visualvm vlc vlc-nox vlc-plugin-notify vlc-plugin-pulse winbind xd xfburn xfce4 xfce4-appfinder
  xfce4-cpugraph-plugin xfce4-dict xfce4-fsguard-plugin xfce4-indicator-plugin xfce4-mailwatch-plugin xfce4-mixer xfce4-mount-plugin xfce4-netload-plugin xfce4-notes xfce4-notes-plugin xfce4-notifyd
  xfce4-panel xfce4-power-manager xfce4-power-manager-data xfce4-quicklauncher-plugin xfce4-screenshooter xfce4-session xfce4-settings xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-terminal
  xfce4-verve-plugin xfce4-weather-plugin xfconf xfdesktop4 xfdesktop4-data xfprint4 xfwm4 xfwm4-themes xpra xserver-xorg-core xserver-xorg-dev xserver-xorg-input-evdev xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome xserver-xorg-video-qxl xserver-xorg-video-r128 xserver-xorg-video-radeon xserver-xorg-video-savage xserver-xorg-video-sis xserver-xorg-video-sisusb
  xserver-xorg-video-tdfx xserver-xorg-video-vesa xserver-xorg-video-vmware xz-utils
637 upgraded, 331 newly installed, 64 to remove and 2 not upgraded.
6 not fully installed or removed.
Need to get 0 B/1,063 MB of archives.
After this operation, 464 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 615425 files and directories currently installed.)
Removing nvidia-current ...
Removing all DKMS Modules
Error! There are no instances of module: nvidia-current
295.40 located in the DKMS tree.
Done.
Traceback (most recent call last):
  File "/usr/bin/quirks-handler", line 26, in <module>
    import Quirks.quirkapplier
  File "/usr/lib/python2.7/dist-packages/Quirks/quirkapplier.py", line 26, in <module>
    import XKit.xutils
ImportError: No module named XKit.xutils
dpkg: error processing nvidia-current (--remove):
 subprocess installed pre-removal script returned error exit status 1
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 nvidia-current
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I have also tried ```
# update-alternatives --remove-all x86_64-linux-gnu_gl_conf
```
and ```
 # aptitude safe-upgrade
``` ```
# update-alternatives --remove i386-linux-gnu_gl_conf /usr/share/man/man1/nvidia-settings.1.gz
``` ```
#  update-alternatives --force --remove-all i386-linux-gnu_gl_conf
``` ```
# dpkg --configure -a
```but in vain.


I cannot purge nvidia-current: ```
~# apt-get purge nvidia-current
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 compiz-kde : Depends: compiz-core (= 1:0.9.7.8-0ubuntu1.4) but 1:0.9.8.4+bzr3407-0ubuntu1 is to be installed
              Depends: compiz-plugins-default (= 1:0.9.7.8-0ubuntu1.4) but 1:0.9.8.4+bzr3407-0ubuntu1 is to be installed
 libcompizconfig0 : Depends: compiz-core-abiversion-20120305 but it is not installable
 libdecoration0-dev : Depends: libdecoration0 (= 1:0.9.7.8-0ubuntu1.4) but 1:0.9.8.4+bzr3407-0ubuntu1 is to be installed
 libgnome-desktop-3-2 : Depends: gnome-desktop3-data (= 3.4.2-0ubuntu0.1) but 3.6.0.1-0ubuntu2 is to be installed
 libunity-core-5.0-5 : Depends: unity-services (= 5.16.0-0ubuntu1) but 6.10.0-0ubuntu2 is to be installed
 xserver-xorg-video-ati : Depends: xorg-video-abi-13
                          Depends: xserver-xorg-core (>= 2:1.12.99.901) but 2:1.11.4-0ubuntu10.8 is to be installed
 xserver-xorg-video-intel : Depends: xorg-video-abi-13
                            Depends: xserver-xorg-core (>= 2:1.12.99.901) but 2:1.11.4-0ubuntu10.8 is to be installed
 xserver-xorg-video-mach64 : Depends: xorg-video-abi-13
                             Depends: xserver-xorg-core (>= 2:1.12.99.901) but 2:1.11.4-0ubuntu10.8 is to be installed
 xserver-xorg-video-s3 : Depends: xorg-video-abi-13
                         Depends: xserver-xorg-core (>= 2:1.12.99.901) but 2:1.11.4-0ubuntu10.8 is to be installed
 xserver-xorg-video-siliconmotion : Depends: xorg-video-abi-13
                                    Depends: xserver-xorg-core (>= 2:1.12.99.901) but 2:1.11.4-0ubuntu10.8 is to be installed
 xserver-xorg-video-trident : Depends: xorg-video-abi-13
                              Depends: xserver-xorg-core (>= 2:1.12.99.901) but 2:1.11.4-0ubuntu10.8 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

The other possible solution to my problem was to [edit]("http://www.backtrack-linux.org/forums/showthread.php?t=40978") /usr/src/nvidia-current-*/nv.c --- I *think* I tried it as described on the link for the folders[LIST][*]nvidia-310.19
[*]nvidia-current-295.40
[*]nvidia-current-updates-304.43
[/LIST] that reside in my /usr/src but this didn't work either.

Any more suggestions, please?

---

```
# uname -a
Linux malaga 3.2.0-34-generic #53-Ubuntu SMP Thu Nov 15 10:48:16 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
~# cat /var/log/dmesg.0 |grep NVIDIA
[   19.510280] nvidia: module license 'NVIDIA' taints kernel.
[   19.540706] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  310.19  Thu Nov  8 00:52:03 PST 2012

```

---

