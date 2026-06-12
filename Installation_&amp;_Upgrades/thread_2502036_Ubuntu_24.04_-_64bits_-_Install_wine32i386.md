---
title: "Ubuntu 24.04 - 64bits - Install wine32:i386"
date: 2024-10-30
forum: Installation &amp; Upgrades
---

### Post by agonzalesc on 2024-10-30
Hi.

These commands was executed previously

```
sudo apt autoclean
sudo apt autoremove
sudo apt -f install
sudo apt --fix-broken install
sudo dpkg --add-architecture i386

```


Now, Wine recommends me to install wine32:i386 so I proceed to install it, but it shows me all this message. I proceed to install it, but it shows me all this message.

```
gonzalesc@puccohp:~/Descargas$ LC_ALL=C sudo apt-get install wine32:i386
[sudo] password for gonzalesc: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  accountsservice-ubuntu-schemas activity-log-manager aha apg apt-config-icons-large apt-config-icons-large-hidpi bamfdaemon breeze-cursor-theme
  breeze-gtk-theme bup bup-doc ca-certificates-java catdoc cheese-common clinfo colord-data cryfs default-jdk-headless default-jre-headless docbook-xml
  docbook-xsl doomsday-data endeavour-common evemu-tools evince-common evolution-data-server-common evtest fluid-soundfont-gm folks-common
  fonts-dejavu-extra fonts-hack fonts-noto-hinted fonts-noto-ui-core fonts-noto-unhinted gir1.2-accountsservice-1.0 gir1.2-atspi-2.0 gir1.2-camel-1.2
  gir1.2-ebookcontacts-1.2 gir1.2-edataserver-1.2 gir1.2-folks-0.7 gir1.2-gck-2 gir1.2-gcr-4 gir1.2-gdata-0.0 gir1.2-gdm-1.0 gir1.2-gee-0.8
  gir1.2-geoclue-2.0 gir1.2-gnomeautoar-0.1 gir1.2-gnomebg-4.0 gir1.2-gnomebluetooth-3.0 gir1.2-gnomedesktop-3.0 gir1.2-goa-1.0 gir1.2-gpaste-2
  gir1.2-gsound-1.0 gir1.2-gstreamer-1.0 gir1.2-gtop-2.0 gir1.2-gweather-4.0 gir1.2-javascriptcoregtk-4.1 gir1.2-javascriptcoregtk-6.0 gir1.2-json-1.0
  gir1.2-nautilus-4.0 gir1.2-nm-1.0 gir1.2-nma4-1.0 gir1.2-snapd-2 gir1.2-soup-2.4 gir1.2-soup-3.0 gir1.2-telepathyglib-0.12 gir1.2-totemplparser-1.0
  gir1.2-upowerglib-1.0 gkbd-capplet gnome-control-center-faces gnome-online-accounts gnome-screensaver gnome-session-common gpaste-2 grilo-plugins-0.3-base
  heif-gdk-pixbuf heif-thumbnailer hplip-data indicator-applet indicator-application indicator-appmenu indicator-common indicator-datetime
  indicator-keyboard indicator-messages indicator-power indicator-printers indicator-session indicator-sound java-common jayatana kactivities-bin
  kde-cli-tools-data kdoctools5 khotkeys-data kio-extras-data kirigami-addons-data kpackagetool5 ktexteditor-data kuserfeedback-doc kwayland-data kwin-data
  liba52-0.7.4 libaa1 libaacs0 libabsl20210324 libabw-0.1-1 libaccounts-glib0 libaccounts-qt5-1 libappimage0 libappimage1.0abi1t64 libappstreamqt5-3
  libaribb24-0t64 libass9 libassimp5 libatk-bridge2.0-dev libatk1.0-dev libatkmm-1.6-dev libatspi2.0-dev libavc1394-0 libavif13 libavtp0 libbamf3-2t64
  libbdplus0 libblas3 libbluray2 libboost-chrono1.83.0t64 libboost-filesystem1.83.0 libboost-program-options1.83.0 libbs2b0 libcaca0 libcairomm-1.0-dev
  libcamel-1.2-64t64 libcamera0.2 libcapi20-3t64 libcddb2 libcdio-cdda2t64 libcdio-paranoia2t64 libcdio19t64 libcdparanoia0 libcdr-0.1-1 libchromaprint1
  libcjson1 libcld2-0 libclutter-1.0-common libcodec2-1.2 libcogl-common libcolamd3 libcolord-gtk4-1t64 libcolorhug2 libcpprest2.10 libcue2 libdatrie-dev
  libdav1d5 libdav1d7 libdbus-1-dev libdc1394-25 libdca0 libdecor-0-0 libdecor-0-plugin-1-cairo libdeflate-dev libdmtx0t64 libdouble-conversion3 libdraco8
  libdv4t64 libdvbpsi10 libdvdnav4 libdvdread8t64 libe-book-0.1-1 libebackend-1.2-11t64 libebml5 libebook-1.2-21t64 libebook-contacts-1.2-4t64 libecal-2.0-3
  libedata-book-1.2-27t64 libedata-cal-2.0-2t64 libedataserver-1.2-27t64 libei1 libeis1 libepub0 libepubgen-0.1-1 libetonyek-0.1-1 libevdocument3-4t64
  libevemu3t64 libexiv2-27 libfaad2 libfakekey0 libfcitx-config4 libfcitx-gclient1 libfcitx-utils0 libflite1 libfmt9 libfolks26 libfontconfig1-dev
  libfreehand-0.1-1 libfreerdp-server3-3 libfribidi-dev libfuse2t64 libgav1-0 libgdata-common libgdata22 libgdk-pixbuf-2.0-dev libgdk-pixbuf-xlib-2.0-0
  libgdk-pixbuf2.0-0 libgdm1 libgeonames-common libgeonames0 libgexiv2-2 libgfortran5 libgit2-1.7 libgles1 libgles2 libglibmm-2.4-dev libglu1-mesa
  libglvnd-core-dev libglvnd0 libgme0 libgnome-autoar-0-0 libgnome-bluetooth-ui-3.0-13 libgnome-panel3 libgnome-rr-4-2t64 libgnomekbd-common libgnomekbd8
  libgoa-1.0-0b libgoa-1.0-common libgoa-backend-1.0-2 libgom-1.0-0t64 libgpaste-2-common libgpaste-2t64 libgphoto2-port12t64 libgpod-common libgpod4t64
  libgps30t64 libgrantlee-templates5 libgraphite2-dev libgrilo-0.3-0 libgsettings-qt1 libgsf-1-114 libgsf-1-common libgsm1 libgsound0t64 libgssdp-1.6-0
  libgtkspell3-3-0 libgupnp-1.6-0 libgupnp-av-1.0-3 libgupnp-igd-1.6-0 libgxps2t64 libharfbuzz-cairo0 libharfbuzz-dev libharfbuzz-subset0 libhfstospell11
  libhpmud0 libhttp-parser2.9 libido3-0.1-0 libiec61883-0 libieee1284-3 libimagequant0 libindicator3-7 libinstpatch-1.0-2 libixml11t64 libjack-jackd2-0
  libjavascriptcoregtk-4.1-0 libjavascriptcoregtk-6.0-1 libjbig-dev libkate1 libkdsoap1 libkeybinder-3.0-0 libkf5activities5 libkf5activitiesstats1
  libkf5archive-data libkf5archive5 libkf5attica5 libkf5auth-data libkf5balooengine5 libkf5bluezqt-data libkf5bluezqt6 libkf5bookmarks-data
  libkf5calendarevents5 libkf5codecs-data libkf5codecs5 libkf5completion-data libkf5config-bin libkf5config-data libkf5configcore5 libkf5configqml5
  libkf5configwidgets-data libkf5contacts-data libkf5coreaddons-data libkf5coreaddons5 libkf5dbusaddons-bin libkf5dbusaddons-data libkf5declarative-data
  libkf5dnssd-data libkf5dnssd5 libkf5doctools5 libkf5filemetadata-data libkf5filemetadata3 libkf5globalaccel-data libkf5guiaddons-data libkf5holidays-data
  libkf5holidays5 libkf5i18n-data libkf5i18n5 libkf5i18nlocaledata5 libkf5iconthemes-data libkf5itemmodels5 libkf5itemviews-data libkf5jobwidgets-data
  libkf5js5t64 libkf5kcmutils-data libkf5kdelibs4support-data libkf5khtml-data libkf5kiontlm5 libkf5modemmanagerqt6 libkf5networkmanagerqt6
  libkf5newstuff-data libkf5notifications-data libkf5notifyconfig-data libkf5package-data libkf5package5 libkf5parts-data libkf5people-data
  libkf5peoplebackend5 libkf5pty-data libkf5pty5 libkf5screen-data libkf5service-data libkf5solid5-data libkf5sonnet5-data libkf5sonnetcore5 libkf5su-bin
  libkf5su-data libkf5su5 libkf5syndication5abi1 libkf5syntaxhighlighting-data libkf5sysguard-data libkf5textwidgets-data libkf5threadweaver5
  libkf5wallet-data libkf5widgetsaddons-data libkf5windowsystem-data libkf5xmlgui-bin libkf5xmlgui-data libkfontinst5 libkpathsea6 libksgrd9
  libksysguardsystemstats1 libkuserfeedback-l10n liblapack3 liblerc-dev liblightdm-gobject-1-0 liblilv-0-0 liblirc-client0t64 liblrdf0 libltc11
  liblttng-ust-common1t64 liblttng-ust-ctl5t64 liblttng-ust1t64 liblua5.2-0 liblucene++0t64 liblzma-dev libmad0 libmanette-0.2-0 libmarkdown2 libmatroska7
  libmbedcrypto7t64 libmd4c0 libmediaart-2.0-0 libmessaging-menu0 libminizip1t64 libmjpegutils-2.1-0t64 libmodplug1 libmpcdec6 libmpeg2-4
  libmpeg2encpp-2.1-0t64 libmplex2-2.1-0t64 libmsgraph-0-1 libmspub-0.1-1 libmtp-common libmtp-runtime libmtp9t64 libmwaw-0.3-3 libmysofa1 libneon27t64
  libnice10 libnorm1t64 libodbc2 libodfgen-0.1-1 libopenal-data libopenal1 libopenconnect5 libopencore-amrnb0 libopencore-amrwb0 libopengl-dev libopengl0
  libopenh264-7 libopenmpt-modplug1 libopenmpt0t64 libopenni2-0 libopusfile0 liborc-0.4-0t64 liborcus-0.18-0 liborcus-parser-0.18-0 libpackagekitqt5-1
  libpagemaker-0.0-0 libpam-kwallet-common libpam-kwallet5 libpango1.0-dev libpangomm-1.4-dev libpciaccess-dev libpciaccess0 libpgm-5.3-0 libphonenumber8
  libphonon-l10n libplacebo338 libplasma-geolocation-interface5 libplymouth5 libpocketsphinx3 libpoppler-glib8t64 libpoppler118 libportal-gtk3-1
  libportal-gtk4-1 libportal1 libpowerdevilui5 libprotobuf-lite32t64 libprotobuf32t64 libproxy-tools libpskc0t64 libqalculate-data libqalculate22t64
  libqca-qt5-2 libqca-qt5-2-plugins libqt5concurrent5t64 libqt5core5t64 libqt5dbus5t64 libqt5network5t64 libqt5positioning5 libqt5qml5 libqt5qmlmodels5
  libqt5qmlworkerscript5 libqt5sensors5 libqt5sql5-sqlite libqt5sql5t64 libqt5test5t64 libqt5texttospeech5 libqt5webchannel5 libqt5webengine-data
  libqt5xml5t64 librabbitmq4 libraqm0 librav1e0 libraw1394-11 libreoffice-base-core libreoffice-uiconfig-calc libreoffice-uiconfig-draw
  libreoffice-uiconfig-impress libreoffice-uiconfig-math libreoffice-uiconfig-writer libresid-builder0c2a librest-1.0-0 librist4 librubberband2
  librygel-core-2.8-0 librygel-db-2.8-0 librygel-renderer-2.8-0 librygel-server-2.8-0 libsane-common libsane-hpaio libscim8v5 libserd-0-0 libsgutils2-1.46-2
  libsharpyuv-dev libshine3 libshout3 libsidplay1v5 libsidplay2 libsigc++-2.0-dev libsignon-plugins-common1 libsignon-qt5-1 libsnapd-qt-2-1 libsnappy1v5
  libsndio7.0 libsnmp-base libsnmp40t64 libsord-0-0 libsoundtouch1 libsoup-2.4-1 libsoup-gnome-2.4-1 libsoup2.4-common libsoxr0 libspandsp2t64
  libspatialaudio0t64 libspdlog1.12 libspeex1 libsphinxbase3t64 libsquashfuse0 libsratom-0-0 libsrt1.5-gnutls libsrtp2-1 libssh-gcrypt-4 libssh2-1t64
  libstoken1t64 libsuitesparseconfig7 libsvtav1enc1d1 libsynctex2 libsysmetrics1 libtag1v5 libtag1v5-vanilla libtelepathy-glib0t64 libtext-engine-0.1-0
  libthai-dev libtheora0 libtiff-dev libtiffxx6 libtimezonemap-data libtimezonemap1 libtomcrypt1 libtommath1 libtotem-plparser-common libtotem-plparser18
  libtracker-sparql-3.0-0 libtss2-tcti-libtpms0t64 libtss2-tcti-spi-helper0t64 libtss2-tctildr0t64 libtwolame0 libudfread0 libunibreak5
  libunity-control-center1 libunity-gtk2-parser0 libunity-gtk3-parser0 libunity-settings-daemon1 libupnp17t64 libv4l-0t64 libv4lconvert0t64 libvdpau1
  libvidstab1.1 libvisio-0.1-1 libvisual-0.4-0 libvlc-bin libvlc5 libvlccore9 libvo-aacenc0 libvo-amrwbenc0 libvoikko1 libvpx9 libwavpack1 libwebp-dev
  libwebpdecoder3 libwildmidi2 libwoff1 libwpd-0.10-10 libwpg-0.3-3 libwps-0.4-4 libwrap0 libx264-164 libx265-199 libxapian30 libxcb-cursor0 libxcb-damage0
  libxcb-dpms0 libxcb-dri2-0 libxcb-dri3-0 libxcb-glx0 libxcb-icccm4 libxcb-image0 libxcb-keysyms1 libxcb-present0 libxcb-randr0 libxcb-record0
  libxcb-render-util0 libxcb-res0 libxcb-sync1 libxcb-xinerama0 libxcb-xkb1 libxcb-xv0 libxcomposite-dev libxcursor-dev libxcvt0 libxdamage-dev
  libxdgutilsbasedir1.0.1 libxdgutilsdesktopentry1.0.1 libxfixes-dev libxfont2 libxft-dev libxi-dev libxinerama-dev libxkbcommon-x11-0 libxklavier16
  libxmlsec1t64-openssl libxrandr-dev libxshmfence1 libxt-dev libxtst-dev libxv1 libxvidcore4 libxvmc1 libxxf86dga1 libyuv0 libzbar0t64 libzeitgeist-2.0-0
  libzimg2 libzix-0-0 libzlcore-data libzlcore0.13t64 libzltext-data libzltext0.13t64 libzmq5 libzstd-dev libzvbi0t64 libzxing3 lp-solve media-player-info
  mobile-broadband-provider-info mutter-common-bin nautilus-data network-manager-gnome openjdk-11-jre-headless openjdk-21-jdk-headless
  openjdk-21-jre-headless oxygen-sounds pango1.0-tools phonon-backend-vlc-common plasma-desktop-data plasma-discover-common plasma-workspace-data
  pocketsphinx-en-us poedit-common policykit-1-gnome power-profiles-daemon powerdevil-data printer-driver-hpcups printer-driver-postscript-hp python3-brlapi
  python3-click python3-colorama python3-dateutil python3-freetype python3-fuse python3-louis python3-nautilus python3-olefile python3-pil python3-pylibacl
  python3-pyqt5.sip python3-pyxattr python3-reportlab python3-rlpycairo python3-speechd python3-tornado python3-xkit qdbus-qt5 qml-module-gsettings1.0
  qml-module-org-kde-bluezqt qml-module-org-kde-kholidays qml-module-org-kde-kitemmodels qml-module-qt-labs-folderlistmodel qml-module-qt-labs-qmlmodels
  qml-module-qt-labs-settings qml-module-qtqml qml-module-qtqml-models2 qtchooser qtspeech5-speechd-plugin qttranslations5-l10n rhythmbox-data sane-airscan
  sgml-data shotwell-common signon-plugin-oauth2 smartmontools socat sonnet-plugins sshfs switcheroo-control tecla timgm6mb-soundfont totem-common tracker
  ubuntu-advantage-desktop-daemon ubuntu-touch-sounds unity-gtk-module-common unity-gtk2-module unity-gtk3-module unity-settings-daemon-schemas vlc-data
  vulkan-tools wayland-protocols x11-apps x11-session-utils x11-xkb-utils xbitmaps xbrlapi xcvt xdg-dbus-proxy xfonts-base xfonts-scalable xinit xinput
  xserver-common xserver-xorg-legacy xsettingsd yelp-xsl zeitgeist-core
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  glib-networking:i386 gstreamer1.0-plugins-base:i386 gstreamer1.0-plugins-good:i386 gstreamer1.0-x:i386 i965-va-driver:i386 intel-media-va-driver:i386
  libaa1:i386 libaom3:i386 libapparmor1:i386 libaribb24-0t64:i386 libasound2-plugins:i386 libasound2t64:i386 libasyncns0:i386 libatk-bridge2.0-0t64:i386
  libatk1.0-0t64:i386 libatomic1:i386 libatspi2.0-0t64:i386 libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386 libavc1394-0:i386
  libavcodec-extra60:i386 libavutil58:i386 libbrotli1:i386 libbsd0:i386 libcaca0:i386 libcairo-gobject2:i386 libcairo2:i386 libcapi20-3t64:i386
  libcdparanoia0:i386 libcodec2-1.2:i386 libcolord2:i386 libcups2t64:i386 libcurl3t64-gnutls:i386 libcurl4t64:i386 libdatrie1:i386 libdav1d7:i386
  libdb5.3t64:i386 libdbus-1-3:i386 libde265-0:i386 libdecor-0-0:i386 libdecor-0-plugin-1-gtk:i386 libdeflate0:i386 libdrm-amdgpu1:i386 libdrm-intel1:i386
  libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386 libduktape207:i386 libdv4t64:i386 libdw1t64:i386 libedit2:i386 libelf1t64:i386 libepoxy0:i386
  libexif12:i386 libexpat1:i386 libffi8:i386 libflac12t64:i386 libfontconfig1:i386 libfreetype6:i386 libfribidi0:i386 libgbm1:i386 libgd3:i386
  libgdk-pixbuf-2.0-0:i386 libgl1:i386 libgl1-mesa-dri:i386 libglapi-mesa:i386 libglib2.0-0t64:i386 libglvnd0:i386 libglx-mesa0:i386 libglx0:i386
  libgnutls30t64:i386 libgomp1:i386 libgphoto2-6t64:i386 libgphoto2-port12t64:i386 libgraphite2-3:i386 libgsm1:i386 libgstreamer-plugins-base1.0-0:i386
  libgstreamer-plugins-good1.0-0:i386 libgstreamer1.0-0:i386 libgtk-3-0t64:i386 libgudev-1.0-0:i386 libharfbuzz0b:i386 libheif-plugin-aomdec:i386
  libheif-plugin-aomenc:i386 libheif-plugin-libde265:i386 libheif1:i386 libhogweed6t64:i386 libicu74:i386 libiec61883-0:i386 libigdgmm12:i386
  libjack-jackd2-0:i386 libjbig0:i386 libjpeg-turbo8:i386 libjpeg8:i386 liblcms2-2:i386 libldap2:i386 libllvm17t64:i386 libltdl7:i386 libmp3lame0:i386
  libmpg123-0t64:i386 libncurses6:i386 libnettle8t64:i386 libnghttp2-14:i386 libnuma1:i386 libodbc2:i386 libogg0:i386 libopencore-amrnb0:i386
  libopencore-amrwb0:i386 libopenjp2-7:i386 libopus0:i386 liborc-0.4-0t64:i386 libosmesa6:i386 libp11-kit0:i386 libpango-1.0-0:i386 libpangocairo-1.0-0:i386
  libpangoft2-1.0-0:i386 libpcap0.8t64:i386 libpciaccess0:i386 libpcsclite1:i386 libpixman-1-0:i386 libpng16-16t64:i386 libproxy1v5:i386 libpsl5t64:i386
  libpulse0:i386 libraw1394-11:i386 libreoffice-core-nogui librsvg2-2:i386 librsvg2-common:i386 librtmp1:i386 libsamplerate0:i386 libsasl2-2:i386
  libsasl2-modules:i386 libsasl2-modules-db:i386 libsdl2-2.0-0:i386 libsensors5:i386 libsharpyuv0:i386 libshine3:i386 libshout3:i386 libslang2:i386
  libsnappy1v5:i386 libsndfile1:i386 libsoup-3.0-0:i386 libsoxr0:i386 libspeex1:i386 libspeexdsp1:i386 libsqlite3-0:i386 libssh-4:i386 libstdc++6:i386
  libsvtav1enc1d1:i386 libswresample4:i386 libtag1v5:i386 libtag1v5-vanilla:i386 libtasn1-6:i386 libthai0:i386 libtheora0:i386 libtiff6:i386
  libtwolame0:i386 libunwind8:i386 libusb-1.0-0:i386 libv4l-0t64:i386 libv4lconvert0t64:i386 libva-drm2:i386 libva-x11-2:i386 libva2:i386 libvdpau1:i386
  libvisual-0.4-0:i386 libvo-amrwbenc0:i386 libvorbis0a:i386 libvorbisenc2:i386 libvpx9:i386 libvulkan1:i386 libwavpack1:i386 libwayland-client0:i386
  libwayland-cursor0:i386 libwayland-egl1:i386 libwayland-server0:i386 libwebp7:i386 libwebpmux3:i386 libwine:i386 libx11-6:i386 libx11-xcb1:i386
  libx264-164:i386 libx265-199:i386 libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386 libxcb-present0:i386 libxcb-randr0:i386
  libxcb-render0:i386 libxcb-shm0:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 libxcb1:i386 libxcomposite1:i386 libxcursor1:i386 libxdamage1:i386
  libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxi6:i386 libxinerama1:i386 libxkbcommon0:i386 libxkbregistry0:i386 libxml2:i386 libxpm4:i386
  libxrandr2:i386 libxrender1:i386 libxshmfence1:i386 libxss1:i386 libxtst6:i386 libxv1:i386 libxvidcore4:i386 libxxf86vm1:i386 libzvbi0t64:i386
  mesa-va-drivers:i386 mesa-vulkan-drivers:i386 ocl-icd-libopencl1:i386 pipewire-alsa pipewire-audio python3-distupgrade ubuntu-release-upgrader-core
  va-driver-all:i386 xserver-common
Suggested packages:
  gvfs:i386 i965-va-driver-shaders:i386 libcuda1:i386 libnvcuvid1:i386 libnvidia-encode1:i386 colord:i386 libdv-bin:i386 oss-compat:i386 libgd-tools:i386
  low-memory-monitor:i386 gnutls-bin:i386 gphoto2:i386 libvisual-0.4-plugins:i386 gstreamer1.0-tools:i386 libheif-plugin-x265:i386
  libheif-plugin-ffmpegdec:i386 libheif-plugin-jpegdec:i386 libheif-plugin-jpegenc:i386 libheif-plugin-j2kdec:i386 libheif-plugin-j2kenc:i386
  libheif-plugin-rav1e:i386 libheif-plugin-svtenc:i386 jackd2:i386 odbc-postgresql:i386 tdsodbc:i386 opus-tools:i386 pcscd:i386 pulseaudio:i386
  libraw1394-doc:i386 librsvg2-bin:i386 libsasl2-modules-gssapi-mit:i386 | libsasl2-modules-gssapi-heimdal:i386 libsasl2-modules-ldap:i386
  libsasl2-modules-otp:i386 libsasl2-modules-sql:i386 lm-sensors:i386 speex:i386 gstreamer1.0-libav:i386 gstreamer1.0-plugins-bad:i386
  gstreamer1.0-plugins-ugly:i386 opencl-icd:i386 wine32-preloader:i386
Recommended packages:
  libgl1-amber-dri:i386 vdpau-driver-all:i386 | vdpau-driver:i386
The following packages will be REMOVED:
  appimagelauncher bluedevil breeze cheese chrome-gnome-shell code colord default-jdk default-jre doomsday doomsday-common drkonqi endeavour evince
  evolution-data-server fbreader ffmpeg frameworkintegration freedoom gdm3 gir1.2-gst-plugins-base-1.0 gir1.2-mutter-14 gir1.2-rb-3.0 gir1.2-totem-1.0
  gir1.2-webkit-6.0 gir1.2-webkit2-4.1 gitkraken gnome-browser-connector gnome-calendar gnome-color-manager gnome-control-center gnome-initial-setup
  gnome-remote-desktop gnome-session-bin gnome-shell gnome-shell-extension-appindicator gnome-shell-extension-desktop-icons-ng gnome-shell-extension-gpaste
  gnome-shell-extension-gsconnect gnome-shell-extension-gsconnect-browsers gnome-shell-extension-manager gnome-shell-extension-prefs
  gnome-shell-extension-ubuntu-dock gnome-shell-extension-ubuntu-tiling-assistant gnome-shell-extensions gnome-snapshot gnome-startup-applications
  gnome-todo gnome-user-docs gnome-user-docs-es gnome-video-effects google-chrome-stable gstreamer1.0-alsa gstreamer1.0-clutter-3.0 gstreamer1.0-gl
  gstreamer1.0-gtk3 gstreamer1.0-libav gstreamer1.0-libcamera gstreamer1.0-pipewire gstreamer1.0-plugins-bad gstreamer1.0-plugins-base
  gstreamer1.0-plugins-base-apps gstreamer1.0-plugins-good gstreamer1.0-plugins-ugly gstreamer1.0-pulseaudio gstreamer1.0-vaapi gstreamer1.0-x gvfs-backends
  hplip i965-va-driver-shaders indicator-bluetooth joystick kaccounts-providers kactivitymanagerd kde-cli-tools kde-config-gtk-style kde-config-screenlocker
  kde-config-sddm kde-config-updates kde-style-breeze kde-style-oxygen-qt5 kdeconnect kded5 keditbookmarks kgamma5 khelpcenter khotkeys kinfocenter kinit
  kio kio-extras kio-fuse kmenuedit kpackagelauncherqml kpeople-vcard kscreen ksshaskpass ksystemstats ktexteditor-katepart kup-backup kwayland-integration
  kwin-common kwin-style-breeze kwin-x11 kwrited layer-shell-qt libasound2-plugins libatk-wrapper-java libatk-wrapper-java-jni libavcodec-extra
  libavcodec-extra60 libavdevice60 libavfilter9 libavformat60 libavutil58 libcheese-gtk25 libcheese8 libclutter-1.0-0 libclutter-gst-3.0-0
  libclutter-gtk-1.0-0 libcogl-pango20 libcogl-path20 libcogl20 libcolorcorrect5 libdbusmenu-qt5-2 libdirectfb-1.7-7t64 libdmapsharing-4.0-3t64
  libdrm-amdgpu1 libdrm-dev libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdrm2 libedataserverui-1.2-4t64 libedataserverui4-1.0-0t64 libegl-dev
  libegl-mesa0 libegl1 libegl1-mesa-dev libepoxy-dev libevview3-3t64 libfluidsynth3 libfolks-eds26 libgbm-dev libgbm1 libgd3 libgl-dev libgl1
  libgl1-amber-dri libgl1-mesa-dri libglapi-mesa libgles-dev libgles2-mesa-dev libglvnd-dev libglx-dev libglx-mesa0 libglx0 libgphoto2-6t64
  libgstreamer-gl1.0-0 libgstreamer-plugins-bad1.0-0 libgstreamer-plugins-base1.0-0 libgstreamer-plugins-good1.0-0 libgtk-3-dev libgtk-4-media-gstreamer
  libgtkmm-3.0-dev libgupnp-dlna-2.0-4 libkaccounts2 libkdecorations2-5v5 libkdecorations2private10 libkf5auth5 libkf5authcore5 libkf5baloo5
  libkf5bookmarks5 libkf5completion5 libkf5configgui5 libkf5configwidgets5 libkf5contacts5 libkf5crash5 libkf5dbusaddons5 libkf5declarative5
  libkf5filemetadata-bin libkf5globalaccel-bin libkf5globalaccel5 libkf5globalaccelprivate5 libkf5guiaddons-bin libkf5guiaddons5 libkf5iconthemes-bin
  libkf5iconthemes5 libkf5idletime5 libkf5itemviews5 libkf5jobwidgets5 libkf5kcmutils5 libkf5kcmutilscore5 libkf5kdelibs4support5 libkf5kdelibs4support5-bin
  libkf5kexiv2-15.0.0 libkf5khtml-bin libkf5khtml5 libkf5kiocore5 libkf5kiofilewidgets5 libkf5kiogui5 libkf5kiowidgets5 libkf5kirigami2-5 libkf5newstuff5
  libkf5newstuffcore5 libkf5newstuffwidgets5 libkf5notifications5 libkf5notifyconfig5 libkf5parts-plugins libkf5parts5 libkf5people5 libkf5peoplewidgets5
  libkf5plasma5 libkf5plasmaquick5 libkf5prison5 libkf5pulseaudioqt3 libkf5purpose-bin libkf5purpose5 libkf5quickaddons5 libkf5runner5 libkf5screen-bin
  libkf5screen8 libkf5screendpms8 libkf5service-bin libkf5service5 libkf5solid5 libkf5sonnetui5 libkf5style5 libkf5syntaxhighlighting5 libkf5sysguard-bin
  libkf5texteditor-bin libkf5texteditor5 libkf5textwidgets5 libkf5wallet-bin libkf5wallet5 libkf5waylandclient5 libkf5widgetsaddons5 libkf5windowsystem5
  libkf5xmlgui5 libkfontinstui5 libkpipewire5 libkpipewiredmabuf5 libkpipewirerecord5 libkpmcore12 libkscreenlocker5 libksysguardformatter1
  libksysguardsensorfaces1 libksysguardsensors1 libkuserfeedbackcore1 libkwalletbackend5-5 libkwineffects14 libkwinglutils14 libkworkspace5-5
  liblayershellqtinterface5 libmutter-14-0 libnotificationmanager1 libosmesa6 liboxygenstyle5-5 liboxygenstyleconfig5-5 libphonon4qt5-4t64 libpolkit-qt5-1-1
  libpoppler-qt5-1 libpostproc57 libpowerdevilcore2 libprocesscore9 libprocessui9 libqaccessibilityclient-qt5-0 libqmobipocket2 libqt5designer5
  libqt5gui5t64 libqt5help5 libqt5hunspellinputmethod5 libqt5multimedia5 libqt5multimedia5-plugins libqt5multimediagsttools5 libqt5multimediaquick5
  libqt5multimediawidgets5 libqt5printsupport5t64 libqt5quick5 libqt5quickcontrols2-5 libqt5quickparticles5 libqt5quickshapes5 libqt5quicktemplates2-5
  libqt5quickwidgets5 libqt5svg5 libqt5virtualkeyboard5 libqt5waylandclient5 libqt5waylandcompositor5 libqt5webengine5 libqt5webenginecore5
  libqt5webenginewidgets5 libqt5webview5 libqt5widgets5t64 libqt5x11extras5 libreoffice-calc libreoffice-core libreoffice-draw libreoffice-gnome
  libreoffice-gtk3 libreoffice-impress libreoffice-math libreoffice-ogltrans libreoffice-pdfimport libreoffice-writer librhythmbox-core10 libsane1
  libsdl2-2.0-0 libsdl2-mixer-2.0-0 libspice-server1 libswresample4 libswscale7 libtaskmanager6 libtotem0 libva-drm2 libva-wayland2 libva-x11-2
  libvirglrenderer1 libvpl2 libweather-ion7 libwebkit2gtk-4.1-0 libwebkitgtk-6.0-4 libwine libwxgtk-webview3.2-1t64 libxatracker2 libyelp0 lightdm
  mesa-utils mesa-utils-bin mesa-va-drivers mesa-vdpau-drivers mesa-vulkan-drivers milou minecraft-launcher nautilus nautilus-share openjdk-11-jre
  openjdk-21-jdk openjdk-21-jre orca partitionmanager peek phonon4qt5 phonon4qt5-backend-vlc php8.2-gd plasma-browser-integration plasma-desktop
  plasma-discover plasma-discover-backend-fwupd plasma-discover-backend-snap plasma-discover-notifier plasma-disks plasma-firewall plasma-framework
  plasma-integration plasma-nm plasma-pa plasma-systemmonitor plasma-thunderbolt plasma-vault plasma-workspace plymouth plymouth-label
  plymouth-theme-spinner plymouth-theme-ubuntu-text poedit polkit-kde-agent-1 powerdevil pulseaudio pulseaudio-module-bluetooth pulseaudio-module-gsettings
  python3-pyqt5 qemu-system-gui qemu-system-modules-opengl qemu-system-modules-spice qml-module-org-kde-activities qml-module-org-kde-draganddrop
  qml-module-org-kde-kcm qml-module-org-kde-kcmutils qml-module-org-kde-kconfig qml-module-org-kde-kcoreaddons qml-module-org-kde-kio
  qml-module-org-kde-kirigami-addons-labs-mobileform qml-module-org-kde-kirigami2 qml-module-org-kde-kquickcontrols qml-module-org-kde-kquickcontrolsaddons
  qml-module-org-kde-ksysguard qml-module-org-kde-kwindowsystem qml-module-org-kde-newstuff qml-module-org-kde-people qml-module-org-kde-pipewire
  qml-module-org-kde-prison qml-module-org-kde-purpose qml-module-org-kde-qqc2desktopstyle qml-module-org-kde-quickcharts qml-module-org-kde-runnermodel
  qml-module-org-kde-solid qml-module-org-kde-sonnet qml-module-org-kde-syntaxhighlighting qml-module-org-kde-userfeedback qml-module-qt-labs-platform
  qml-module-qtgraphicaleffects qml-module-qtmultimedia qml-module-qtquick-controls qml-module-qtquick-controls2 qml-module-qtquick-dialogs
  qml-module-qtquick-layouts qml-module-qtquick-particles2 qml-module-qtquick-privatewidgets qml-module-qtquick-shapes qml-module-qtquick-templates2
  qml-module-qtquick-virtualkeyboard qml-module-qtquick-window2 qml-module-qtquick2 qml-module-qtwebengine qml-module-sso-onlineaccounts
  qml-module-ubuntu-onlineaccounts qt5-gtk-platformtheme qtvirtualkeyboard-plugin qtwayland5 redshift rhythmbox rhythmbox-plugin-alternative-toolbar
  rhythmbox-plugins rygel sane-utils shotwell simple-scan software-properties-gtk spice-vdagent systemsettings totem totem-plugins tracker-extract
  tracker-miner-fs ubuntu-desktop ubuntu-desktop-minimal ubuntu-docs ubuntu-drivers-common ubuntu-release-upgrader-gtk ubuntu-session unity-control-center
  unity-greeter unity-settings-daemon update-manager update-notifier vdpau-driver-all vlc-plugin-base vlc-plugin-video-output wayland-utils wine64 x11-utils
  xdg-desktop-portal-kde xorg xserver-xorg xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-libinput xserver-xorg-input-wacom
  xserver-xorg-video-all xserver-xorg-video-amdgpu xserver-xorg-video-ati xserver-xorg-video-fbdev xserver-xorg-video-intel xserver-xorg-video-nouveau
  xserver-xorg-video-qxl xserver-xorg-video-radeon xserver-xorg-video-vesa xserver-xorg-video-vmware xwayland yelp
The following NEW packages will be installed:
  glib-networking:i386 gstreamer1.0-plugins-base:i386 gstreamer1.0-plugins-good:i386 gstreamer1.0-x:i386 i965-va-driver:i386 intel-media-va-driver:i386
  libaa1:i386 libaom3:i386 libapparmor1:i386 libaribb24-0t64:i386 libasound2-plugins:i386 libasound2t64:i386 libasyncns0:i386 libatk-bridge2.0-0t64:i386
  libatk1.0-0t64:i386 libatomic1:i386 libatspi2.0-0t64:i386 libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386 libavc1394-0:i386
  libavcodec-extra60:i386 libavutil58:i386 libbrotli1:i386 libbsd0:i386 libcaca0:i386 libcairo-gobject2:i386 libcairo2:i386 libcapi20-3t64:i386
  libcdparanoia0:i386 libcodec2-1.2:i386 libcolord2:i386 libcups2t64:i386 libcurl3t64-gnutls:i386 libcurl4t64:i386 libdatrie1:i386 libdav1d7:i386
  libdb5.3t64:i386 libdbus-1-3:i386 libde265-0:i386 libdecor-0-0:i386 libdecor-0-plugin-1-gtk:i386 libdeflate0:i386 libdrm-amdgpu1:i386 libdrm-intel1:i386
  libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386 libduktape207:i386 libdv4t64:i386 libdw1t64:i386 libedit2:i386 libelf1t64:i386 libepoxy0:i386
  libexif12:i386 libexpat1:i386 libffi8:i386 libflac12t64:i386 libfontconfig1:i386 libfreetype6:i386 libfribidi0:i386 libgbm1:i386 libgd3:i386
  libgdk-pixbuf-2.0-0:i386 libgl1:i386 libgl1-mesa-dri:i386 libglapi-mesa:i386 libglib2.0-0t64:i386 libglvnd0:i386 libglx-mesa0:i386 libglx0:i386
  libgnutls30t64:i386 libgomp1:i386 libgphoto2-6t64:i386 libgphoto2-port12t64:i386 libgraphite2-3:i386 libgsm1:i386 libgstreamer-plugins-base1.0-0:i386
  libgstreamer-plugins-good1.0-0:i386 libgstreamer1.0-0:i386 libgtk-3-0t64:i386 libgudev-1.0-0:i386 libharfbuzz0b:i386 libheif-plugin-aomdec:i386
  libheif-plugin-aomenc:i386 libheif-plugin-libde265:i386 libheif1:i386 libhogweed6t64:i386 libicu74:i386 libiec61883-0:i386 libigdgmm12:i386
  libjack-jackd2-0:i386 libjbig0:i386 libjpeg-turbo8:i386 libjpeg8:i386 liblcms2-2:i386 libldap2:i386 libllvm17t64:i386 libltdl7:i386 libmp3lame0:i386
  libmpg123-0t64:i386 libncurses6:i386 libnettle8t64:i386 libnghttp2-14:i386 libnuma1:i386 libodbc2:i386 libogg0:i386 libopencore-amrnb0:i386
  libopencore-amrwb0:i386 libopenjp2-7:i386 libopus0:i386 liborc-0.4-0t64:i386 libosmesa6:i386 libp11-kit0:i386 libpango-1.0-0:i386 libpangocairo-1.0-0:i386
  libpangoft2-1.0-0:i386 libpcap0.8t64:i386 libpciaccess0:i386 libpcsclite1:i386 libpixman-1-0:i386 libpng16-16t64:i386 libproxy1v5:i386 libpsl5t64:i386
  libpulse0:i386 libraw1394-11:i386 libreoffice-core-nogui librsvg2-2:i386 librsvg2-common:i386 librtmp1:i386 libsamplerate0:i386 libsasl2-2:i386
  libsasl2-modules:i386 libsasl2-modules-db:i386 libsdl2-2.0-0:i386 libsensors5:i386 libsharpyuv0:i386 libshine3:i386 libshout3:i386 libslang2:i386
  libsnappy1v5:i386 libsndfile1:i386 libsoup-3.0-0:i386 libsoxr0:i386 libspeex1:i386 libspeexdsp1:i386 libsqlite3-0:i386 libssh-4:i386 libstdc++6:i386
  libsvtav1enc1d1:i386 libswresample4:i386 libtag1v5:i386 libtag1v5-vanilla:i386 libtasn1-6:i386 libthai0:i386 libtheora0:i386 libtiff6:i386
  libtwolame0:i386 libunwind8:i386 libusb-1.0-0:i386 libv4l-0t64:i386 libv4lconvert0t64:i386 libva-drm2:i386 libva-x11-2:i386 libva2:i386 libvdpau1:i386
  libvisual-0.4-0:i386 libvo-amrwbenc0:i386 libvorbis0a:i386 libvorbisenc2:i386 libvpx9:i386 libvulkan1:i386 libwavpack1:i386 libwayland-client0:i386
  libwayland-cursor0:i386 libwayland-egl1:i386 libwayland-server0:i386 libwebp7:i386 libwebpmux3:i386 libwine:i386 libx11-6:i386 libx11-xcb1:i386
  libx264-164:i386 libx265-199:i386 libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386 libxcb-glx0:i386 libxcb-present0:i386 libxcb-randr0:i386
  libxcb-render0:i386 libxcb-shm0:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 libxcb1:i386 libxcomposite1:i386 libxcursor1:i386 libxdamage1:i386
  libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxi6:i386 libxinerama1:i386 libxkbcommon0:i386 libxkbregistry0:i386 libxml2:i386 libxpm4:i386
  libxrandr2:i386 libxrender1:i386 libxshmfence1:i386 libxss1:i386 libxtst6:i386 libxv1:i386 libxvidcore4:i386 libxxf86vm1:i386 libzvbi0t64:i386
  mesa-va-drivers:i386 mesa-vulkan-drivers:i386 ocl-icd-libopencl1:i386 pipewire-alsa pipewire-audio va-driver-all:i386 wine32:i386
The following packages will be upgraded:
  python3-distupgrade ubuntu-release-upgrader-core xserver-common
3 upgraded, 223 newly installed, 470 to remove and 5 not upgraded.
Need to get 272 MB of archives.
After this operation, 2361 MB disk space will be freed.
Do you want to continue? [Y/n]
```

It asks me to remove some packages that I usually use like "gitkraken, chrome, and others". How can I install wine32 but not delete the packages I need?

Thanks

---

### Post by 1fallen on 2024-10-30
I see no mention for this:
```
sudo dpkg --add-architecture i386
```
Did you install it first?

---

### Post by agonzalesc on 2024-10-30
Yes. I edited the original post.

---

### Post by 1fallen on 2024-10-30
I'm not sure what version or pack you installed mine is just fine, and it won't complain about wine-32.

I use the stable wine:
```
 apt policy wine-stable
wine-stable:
  Installed: 3.0.1ubuntu1
  Candidate: 3.0.1ubuntu1
  Version table:
 *** 3.0.1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu plucky/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu plucky/universe i386 Packages
        100 /var/lib/dpkg/status

```

---

### Post by agonzalesc on 2024-10-30
Hi.
Thanks for reply.

I have installed wine-stable but the result is the same:


```
gonzalesc@puccohp:~/Descargas$ LC_ALL=C sudo apt policy wine-stable
wine-stable:
  Installed: 3.0.1ubuntu1
  Candidate: 3.0.1ubuntu1
  Version table:
 *** 3.0.1ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu noble/universe amd64 Packages
        500 http://archive.ubuntu.com/ubuntu noble/universe i386 Packages
        100 /var/lib/dpkg/status

gonzalesc@puccohp:~/Descargas$ LC_ALL=C wine-stable filmora_setup_full7598.exe 
it looks like wine32 is missing, you should install it.
as root, please execute "apt-get install wine32:i386"
0110:err:environ:init_peb starting L"Z:\\home\\gonzalesc\\Descargas\\filmora_setup_full7598.exe" in experimental wow64 mode
wine: failed to load L"\\??\\C:\\windows\\syswow64\\ntdll.dll" error c0000135
Application could not be started, or no application associated with the specified file.
ShellExecuteEx failed: Internal error.
```


This is an example but it happens to me with all the .exe files I have.

I understand that what I am running is 64-bit Wine and it is in the experimental phase, so Wine itself recommends me to use Wine32.

Thanks

---

### Post by 1fallen on 2024-10-30
Can you provide the link for that or any other .exe's that don't work for you, I need to touch and see for myself, to add any other advice or suggestions. ;)

---

### Post by deadflowr on 2024-10-30
With the rather large glut of packages marked for removal I'd say something's rotten in the state of Denmark.

Please post the following outputs
```
sudo apt update
sudo apt upgrade
```
press N to abort it so it doesn't actually run the upgrade part.

wine32 is a dependency of wine and wine-stable.
wine32 is only 32-bit.(i386)
Should already be installed if either wine or wine-stable is installed.

---

### Post by 1fallen on 2024-10-30
> **deadflowr said:**
> With the rather large glut of packages marked for removal I'd say something's rotten in the state of Denmark.

Please post the following outputs
```
sudo apt update
sudo apt upgrade
```
press N to abort it so it doesn't actually run the upgrade part.

wine32 is a dependency of wine and wine-stable.
wine32 is only 32-bit.(i386)
Should already be installed if either wine or wine-stable is installed.

That output was from "sudo apt-get install wine32:i386"
it won't show that again deadflowr.

```
sudo apt-get install wine32:i386
[sudo] password for me: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
wine32:i386 is already the newest version (9.0~repack-4build3).
wine32:i386 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
```

---

### Post by deadflowr on 2024-10-30
i'm not asking to see that.
I'm confused why half the system is set to be autoremoved.

---

### Post by agonzalesc on 2024-10-30
@1fallen2 here a .exe  : [https://download.wondershare.net/inst/filmora_setup_full7598.exe](https://download.wondershare.net/inst/filmora_setup_full7598.exe)

@deadflowr here the output:

```
gonzalesc@puccohp:~/Descargas$ LC_ALL=C sudo apt update
Hit:1 http://archive.ubuntu.com/ubuntu noble InRelease
Hit:2 http://security.ubuntu.com/ubuntu noble-security InRelease
Hit:3 https://download.docker.com/linux/ubuntu focal InRelease
Hit:4 https://download.docker.com/linux/ubuntu noble InRelease
Hit:5 https://download.docker.com/linux/ubuntu jammy InRelease
Hit:6 http://archive.ubuntu.com/ubuntu noble-updates InRelease
Hit:7 http://archive.ubuntu.com/ubuntu noble-backports InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
All packages are up to date.
W: https://download.docker.com/linux/ubuntu/dists/noble/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
N: Skipping acquire of configured file 'stable/binary-i386/Packages' as repository 'https://download.docker.com/linux/ubuntu noble InRelease' doesn't support architecture 'i386'

```



```
gonzalesc@puccohp:~/Descargas$ LC_ALL=C sudo apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
Get more security updates through Ubuntu Pro with 'esm-apps' enabled:
  libmagickwand-6.q16-6 libmagickcore-6.q16-6
Learn more about Ubuntu Pro at https://ubuntu.com/pro
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```



And when I want to install wine32, this is the output:

```
gonzalesc@puccohp:~/Descargas$ LC_ALL=C sudo apt-get install wine32:i386
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages were automatically installed and are no longer required:
  accountsservice-ubuntu-schemas activity-log-manager aha apg apt-config-icons-large apt-config-icons-large-hidpi bamfdaemon breeze-cursor-theme
  breeze-gtk-theme bup bup-doc ca-certificates-java catdoc cheese-common clinfo colord-data cryfs default-jdk-headless default-jre-headless docbook-xml
  docbook-xsl doomsday-data endeavour-common evemu-tools evince-common evolution-data-server-common evtest fluid-soundfont-gm folks-common
  fonts-dejavu-extra fonts-hack fonts-noto-hinted fonts-noto-ui-core fonts-noto-unhinted gir1.2-accountsservice-1.0 gir1.2-atspi-2.0 gir1.2-camel-1.2
  gir1.2-ebookcontacts-1.2 gir1.2-edataserver-1.2 gir1.2-folks-0.7 gir1.2-gck-2 gir1.2-gcr-4 gir1.2-gdata-0.0 gir1.2-gdm-1.0 gir1.2-gee-0.8
  gir1.2-geoclue-2.0 gir1.2-gnomeautoar-0.1 gir1.2-gnomebg-4.0 gir1.2-gnomebluetooth-3.0 gir1.2-gnomedesktop-3.0 gir1.2-goa-1.0 gir1.2-gpaste-2
  gir1.2-gsound-1.0 gir1.2-gstreamer-1.0 gir1.2-gtop-2.0 gir1.2-gweather-4.0 gir1.2-javascriptcoregtk-4.1 gir1.2-javascriptcoregtk-6.0 gir1.2-json-1.0
  gir1.2-nautilus-4.0 gir1.2-nm-1.0 gir1.2-nma4-1.0 gir1.2-snapd-2 gir1.2-soup-2.4 gir1.2-soup-3.0 gir1.2-telepathyglib-0.12 gir1.2-totemplparser-1.0
  gir1.2-upowerglib-1.0 gkbd-capplet gnome-control-center-faces gnome-online-accounts gnome-screensaver gnome-session-common gpaste-2 grilo-plugins-0.3-base
  heif-gdk-pixbuf heif-thumbnailer hplip-data indicator-applet indicator-application indicator-appmenu indicator-common indicator-datetime
  indicator-keyboard indicator-messages indicator-power indicator-printers indicator-session indicator-sound java-common jayatana kactivities-bin
  kde-cli-tools-data kdoctools5 khotkeys-data kio-extras-data kirigami-addons-data kpackagetool5 ktexteditor-data kuserfeedback-doc kwayland-data kwin-data
  liba52-0.7.4 libaa1 libaacs0 libabsl20210324 libabw-0.1-1 libaccounts-glib0 libaccounts-qt5-1 libappimage0 libappimage1.0abi1t64 libappstreamqt5-3
  libaribb24-0t64 libass9 libassimp5 libatk-bridge2.0-dev libatk1.0-dev libatkmm-1.6-dev libatspi2.0-dev libavc1394-0 libavif13 libavtp0 libbamf3-2t64
  libbdplus0 libblas3 libbluray2 libboost-chrono1.83.0t64 libboost-filesystem1.83.0 libboost-program-options1.83.0 libbs2b0 libcaca0 libcairomm-1.0-dev
  libcamel-1.2-64t64 libcamera0.2 libcapi20-3t64 libcddb2 libcdio-cdda2t64 libcdio-paranoia2t64 libcdio19t64 libcdparanoia0 libcdr-0.1-1 libchromaprint1
  libcjson1 libcld2-0 libclutter-1.0-common libcodec2-1.2 libcogl-common libcolamd3 libcolord-gtk4-1t64 libcolorhug2 libcpprest2.10 libcue2 libdatrie-dev
  libdav1d5 libdav1d7 libdbus-1-dev libdc1394-25 libdca0 libdecor-0-0 libdecor-0-plugin-1-cairo libdeflate-dev libdmtx0t64 libdouble-conversion3 libdraco8
  libdv4t64 libdvbpsi10 libdvdnav4 libdvdread8t64 libe-book-0.1-1 libebackend-1.2-11t64 libebml5 libebook-1.2-21t64 libebook-contacts-1.2-4t64 libecal-2.0-3
  libedata-book-1.2-27t64 libedata-cal-2.0-2t64 libedataserver-1.2-27t64 libei1 libeis1 libepub0 libepubgen-0.1-1 libetonyek-0.1-1 libevdocument3-4t64
  libevemu3t64 libexiv2-27 libfaad2 libfakekey0 libfcitx-config4 libfcitx-gclient1 libfcitx-utils0 libflite1 libfmt9 libfolks26 libfontconfig1-dev
  libfreehand-0.1-1 libfreerdp-server3-3 libfribidi-dev libgav1-0 libgdata-common libgdata22 libgdk-pixbuf-2.0-dev libgdk-pixbuf-xlib-2.0-0
  libgdk-pixbuf2.0-0 libgdm1 libgeonames-common libgeonames0 libgexiv2-2 libgfortran5 libgit2-1.7 libgles1 libgles2 libglibmm-2.4-dev libglu1-mesa
  libglvnd-core-dev libglvnd0 libgme0 libgnome-autoar-0-0 libgnome-bluetooth-ui-3.0-13 libgnome-panel3 libgnome-rr-4-2t64 libgnomekbd-common libgnomekbd8
  libgoa-1.0-0b libgoa-1.0-common libgoa-backend-1.0-2 libgom-1.0-0t64 libgpaste-2-common libgpaste-2t64 libgphoto2-port12t64 libgpod-common libgpod4t64
  libgps30t64 libgrantlee-templates5 libgraphite2-dev libgrilo-0.3-0 libgsettings-qt1 libgsf-1-114 libgsf-1-common libgsm1 libgsound0t64 libgssdp-1.6-0
  libgtkspell3-3-0 libgupnp-1.6-0 libgupnp-av-1.0-3 libgupnp-igd-1.6-0 libgxps2t64 libharfbuzz-cairo0 libharfbuzz-dev libharfbuzz-subset0 libhfstospell11
  libhpmud0 libhttp-parser2.9 libido3-0.1-0 libiec61883-0 libieee1284-3 libimagequant0 libindicator3-7 libinstpatch-1.0-2 libixml11t64 libjack-jackd2-0
  libjavascriptcoregtk-4.1-0 libjavascriptcoregtk-6.0-1 libjbig-dev libkate1 libkdsoap1 libkeybinder-3.0-0 libkf5activities5 libkf5activitiesstats1
  libkf5archive-data libkf5archive5 libkf5attica5 libkf5auth-data libkf5balooengine5 libkf5bluezqt-data libkf5bluezqt6 libkf5bookmarks-data
  libkf5calendarevents5 libkf5codecs-data libkf5codecs5 libkf5completion-data libkf5config-bin libkf5config-data libkf5configcore5 libkf5configqml5
  libkf5configwidgets-data libkf5contacts-data libkf5coreaddons-data libkf5coreaddons5 libkf5dbusaddons-bin libkf5dbusaddons-data libkf5declarative-data
  libkf5dnssd-data libkf5dnssd5 libkf5doctools5 libkf5filemetadata-data libkf5filemetadata3 libkf5globalaccel-data libkf5guiaddons-data libkf5holidays-data
  libkf5holidays5 libkf5i18n-data libkf5i18n5 libkf5i18nlocaledata5 libkf5iconthemes-data libkf5itemmodels5 libkf5itemviews-data libkf5jobwidgets-data
  libkf5js5t64 libkf5kcmutils-data libkf5kdelibs4support-data libkf5khtml-data libkf5kiontlm5 libkf5modemmanagerqt6 libkf5networkmanagerqt6
  libkf5newstuff-data libkf5notifications-data libkf5notifyconfig-data libkf5package-data libkf5package5 libkf5parts-data libkf5people-data
  libkf5peoplebackend5 libkf5pty-data libkf5pty5 libkf5screen-data libkf5service-data libkf5solid5-data libkf5sonnet5-data libkf5sonnetcore5 libkf5su-bin
  libkf5su-data libkf5su5 libkf5syndication5abi1 libkf5syntaxhighlighting-data libkf5sysguard-data libkf5textwidgets-data libkf5threadweaver5
  libkf5wallet-data libkf5widgetsaddons-data libkf5windowsystem-data libkf5xmlgui-bin libkf5xmlgui-data libkfontinst5 libkpathsea6 libksgrd9
  libksysguardsystemstats1 libkuserfeedback-l10n liblapack3 liblerc-dev liblightdm-gobject-1-0 liblilv-0-0 liblirc-client0t64 liblrdf0 libltc11
  liblttng-ust-common1t64 liblttng-ust-ctl5t64 liblttng-ust1t64 liblua5.2-0 liblucene++0t64 liblzma-dev libmad0 libmanette-0.2-0 libmarkdown2 libmatroska7
  libmbedcrypto7t64 libmd4c0 libmediaart-2.0-0 libmessaging-menu0 libminizip1t64 libmjpegutils-2.1-0t64 libmodplug1 libmpcdec6 libmpeg2-4
  libmpeg2encpp-2.1-0t64 libmplex2-2.1-0t64 libmsgraph-0-1 libmspub-0.1-1 libmtp-common libmtp-runtime libmtp9t64 libmwaw-0.3-3 libmysofa1 libneon27t64
  libnice10 libnorm1t64 libodbc2 libodfgen-0.1-1 libopenal-data libopenal1 libopenconnect5 libopencore-amrnb0 libopencore-amrwb0 libopengl-dev libopengl0
  libopenh264-7 libopenmpt-modplug1 libopenmpt0t64 libopenni2-0 libopusfile0 liborc-0.4-0t64 liborcus-0.18-0 liborcus-parser-0.18-0 libpackagekitqt5-1
  libpagemaker-0.0-0 libpam-kwallet-common libpam-kwallet5 libpango1.0-dev libpangomm-1.4-dev libpciaccess-dev libpciaccess0 libpgm-5.3-0 libphonenumber8
  libphonon-l10n libplacebo338 libplasma-geolocation-interface5 libplymouth5 libpocketsphinx3 libpoppler-glib8t64 libpoppler118 libportal-gtk3-1
  libportal-gtk4-1 libportal1 libpowerdevilui5 libprotobuf-lite32t64 libprotobuf32t64 libproxy-tools libpskc0t64 libqalculate-data libqalculate22t64
  libqca-qt5-2 libqca-qt5-2-plugins libqt5concurrent5t64 libqt5core5t64 libqt5dbus5t64 libqt5network5t64 libqt5positioning5 libqt5qml5 libqt5qmlmodels5
  libqt5qmlworkerscript5 libqt5sensors5 libqt5sql5-sqlite libqt5sql5t64 libqt5test5t64 libqt5texttospeech5 libqt5webchannel5 libqt5webengine-data
  libqt5xml5t64 librabbitmq4 libraqm0 librav1e0 libraw1394-11 libreoffice-base-core libreoffice-uiconfig-calc libreoffice-uiconfig-draw
  libreoffice-uiconfig-impress libreoffice-uiconfig-math libreoffice-uiconfig-writer libresid-builder0c2a librest-1.0-0 librist4 librubberband2
  librygel-core-2.8-0 librygel-db-2.8-0 librygel-renderer-2.8-0 librygel-server-2.8-0 libsane-common libsane-hpaio libscim8v5 libserd-0-0 libsgutils2-1.46-2
  libsharpyuv-dev libshine3 libshout3 libsidplay1v5 libsidplay2 libsigc++-2.0-dev libsignon-plugins-common1 libsignon-qt5-1 libsnapd-qt-2-1 libsnappy1v5
  libsndio7.0 libsnmp-base libsnmp40t64 libsord-0-0 libsoundtouch1 libsoup-2.4-1 libsoup-gnome-2.4-1 libsoup2.4-common libsoxr0 libspandsp2t64
  libspatialaudio0t64 libspdlog1.12 libspeex1 libsphinxbase3t64 libsquashfuse0 libsratom-0-0 libsrt1.5-gnutls libsrtp2-1 libssh-gcrypt-4 libssh2-1t64
  libstoken1t64 libsuitesparseconfig7 libsvtav1enc1d1 libsynctex2 libsysmetrics1 libtag1v5 libtag1v5-vanilla libtelepathy-glib0t64 libtext-engine-0.1-0
  libthai-dev libtheora0 libtiff-dev libtiffxx6 libtimezonemap-data libtimezonemap1 libtomcrypt1 libtommath1 libtotem-plparser-common libtotem-plparser18
  libtracker-sparql-3.0-0 libtss2-tcti-libtpms0t64 libtss2-tcti-spi-helper0t64 libtss2-tctildr0t64 libtwolame0 libudfread0 libunibreak5
  libunity-control-center1 libunity-gtk2-parser0 libunity-gtk3-parser0 libunity-settings-daemon1 libupnp17t64 libv4l-0t64 libv4lconvert0t64 libvdpau1
  libvidstab1.1 libvisio-0.1-1 libvisual-0.4-0 libvlc-bin libvlc5 libvlccore9 libvo-aacenc0 libvo-amrwbenc0 libvoikko1 libvpx9 libwavpack1 libwebp-dev
  libwebpdecoder3 libwildmidi2 libwoff1 libwpd-0.10-10 libwpg-0.3-3 libwps-0.4-4 libwrap0 libx264-164 libx265-199 libxapian30 libxcb-cursor0 libxcb-damage0
  libxcb-dpms0 libxcb-dri2-0 libxcb-dri3-0 libxcb-glx0 libxcb-icccm4 libxcb-image0 libxcb-keysyms1 libxcb-present0 libxcb-randr0 libxcb-record0
  libxcb-render-util0 libxcb-res0 libxcb-sync1 libxcb-xinerama0 libxcb-xkb1 libxcb-xv0 libxcomposite-dev libxcursor-dev libxcvt0 libxdamage-dev
  libxdgutilsbasedir1.0.1 libxdgutilsdesktopentry1.0.1 libxfixes-dev libxfont2 libxft-dev libxi-dev libxinerama-dev libxkbcommon-x11-0 libxklavier16
  libxmlsec1t64-openssl libxrandr-dev libxshmfence1 libxt-dev libxtst-dev libxv1 libxvidcore4 libxvmc1 libxxf86dga1 libyuv0 libzbar0t64 libzeitgeist-2.0-0
  libzimg2 libzix-0-0 libzlcore-data libzlcore0.13t64 libzltext-data libzltext0.13t64 libzmq5 libzstd-dev libzvbi0t64 libzxing3 lp-solve media-player-info
  mobile-broadband-provider-info mutter-common-bin nautilus-data network-manager-gnome openjdk-11-jre-headless openjdk-21-jdk-headless
  openjdk-21-jre-headless oxygen-sounds pango1.0-tools phonon-backend-vlc-common plasma-desktop-data plasma-discover-common plasma-workspace-data
  pocketsphinx-en-us poedit-common policykit-1-gnome power-profiles-daemon powerdevil-data printer-driver-hpcups printer-driver-postscript-hp python3-brlapi
  python3-click python3-colorama python3-dateutil python3-freetype python3-fuse python3-louis python3-nautilus python3-olefile python3-pil python3-pylibacl
  python3-pyqt5.sip python3-pyxattr python3-reportlab python3-rlpycairo python3-speechd python3-tornado python3-xkit qdbus-qt5 qml-module-gsettings1.0
  qml-module-org-kde-bluezqt qml-module-org-kde-kholidays qml-module-org-kde-kitemmodels qml-module-qt-labs-folderlistmodel qml-module-qt-labs-qmlmodels
  qml-module-qt-labs-settings qml-module-qtqml qml-module-qtqml-models2 qtchooser qtspeech5-speechd-plugin qttranslations5-l10n rhythmbox-data sane-airscan
  sgml-data signon-plugin-oauth2 smartmontools socat sonnet-plugins sshfs switcheroo-control tecla timgm6mb-soundfont totem-common tracker
  ubuntu-advantage-desktop-daemon ubuntu-touch-sounds unity-gtk-module-common unity-gtk2-module unity-gtk3-module unity-settings-daemon-schemas vlc-data
  vulkan-tools wayland-protocols x11-apps x11-session-utils x11-xkb-utils xbitmaps xbrlapi xcvt xdg-dbus-proxy xfonts-base xfonts-scalable xinit xinput
  xserver-common xserver-xorg-legacy xsettingsd yelp-xsl zeitgeist-core
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  glib-networking:i386 gstreamer1.0-plugins-base:i386 gstreamer1.0-plugins-good:i386 gstreamer1.0-x:i386 i965-va-driver:i386 intel-media-va-driver:i386
  libaa1:i386 libaom3:i386 libapparmor1:i386 libaribb24-0t64:i386 libasound2-plugins:i386 libasound2t64:i386 libasyncns0:i386 libatomic1:i386
  libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386 libavc1394-0:i386 libavcodec-extra60:i386 libavutil58:i386 libbrotli1:i386
  libbsd0:i386 libcaca0:i386 libcairo-gobject2:i386 libcairo2:i386 libcapi20-3t64:i386 libcdparanoia0:i386 libcodec2-1.2:i386 libcups2t64:i386
  libcurl3t64-gnutls:i386 libcurl4t64:i386 libdatrie1:i386 libdav1d7:i386 libdb5.3t64:i386 libdbus-1-3:i386 libde265-0:i386 libdeflate0:i386
  libdrm-amdgpu1:i386 libdrm-intel1:i386 libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386 libduktape207:i386 libdv4t64:i386 libdw1t64:i386
  libedit2:i386 libelf1t64:i386 libexif12:i386 libexpat1:i386 libffi8:i386 libflac12t64:i386 libfontconfig1:i386 libfreetype6:i386 libfribidi0:i386
  libgd3:i386 libgdk-pixbuf-2.0-0:i386 libgl1:i386 libgl1-mesa-dri:i386 libglapi-mesa:i386 libglib2.0-0t64:i386 libglvnd0:i386 libglx-mesa0:i386
  libglx0:i386 libgnutls30t64:i386 libgomp1:i386 libgphoto2-6t64:i386 libgphoto2-port12t64:i386 libgraphite2-3:i386 libgsm1:i386
  libgstreamer-plugins-base1.0-0:i386 libgstreamer-plugins-good1.0-0:i386 libgstreamer1.0-0:i386 libgudev-1.0-0:i386 libharfbuzz0b:i386
  libheif-plugin-aomdec:i386 libheif-plugin-aomenc:i386 libheif-plugin-libde265:i386 libheif1:i386 libhogweed6t64:i386 libicu74:i386 libiec61883-0:i386
  libigdgmm12:i386 libjack-jackd2-0:i386 libjbig0:i386 libjpeg-turbo8:i386 libjpeg8:i386 libldap2:i386 libllvm17t64:i386 libltdl7:i386 libmp3lame0:i386
  libmpg123-0t64:i386 libncurses6:i386 libnettle8t64:i386 libnghttp2-14:i386 libnuma1:i386 libodbc2:i386 libogg0:i386 libopencore-amrnb0:i386
  libopencore-amrwb0:i386 libopenjp2-7:i386 libopus0:i386 liborc-0.4-0t64:i386 libosmesa6:i386 libp11-kit0:i386 libpango-1.0-0:i386 libpangocairo-1.0-0:i386
  libpangoft2-1.0-0:i386 libpcap0.8t64:i386 libpciaccess0:i386 libpcsclite1:i386 libpixman-1-0:i386 libpng16-16t64:i386 libproxy1v5:i386 libpsl5t64:i386
  libpulse0:i386 libraw1394-11:i386 libreoffice-core-nogui librsvg2-2:i386 librsvg2-common:i386 librtmp1:i386 libsamplerate0:i386 libsasl2-2:i386
  libsasl2-modules:i386 libsasl2-modules-db:i386 libsensors5:i386 libsharpyuv0:i386 libshine3:i386 libshout3:i386 libslang2:i386 libsnappy1v5:i386
  libsndfile1:i386 libsoup-3.0-0:i386 libsoxr0:i386 libspeex1:i386 libspeexdsp1:i386 libsqlite3-0:i386 libssh-4:i386 libstdc++6:i386 libsvtav1enc1d1:i386
  libswresample4:i386 libtag1v5:i386 libtag1v5-vanilla:i386 libtasn1-6:i386 libthai0:i386 libtheora0:i386 libtiff6:i386 libtwolame0:i386 libunwind8:i386
  libusb-1.0-0:i386 libv4l-0t64:i386 libv4lconvert0t64:i386 libva-drm2:i386 libva-x11-2:i386 libva2:i386 libvdpau1:i386 libvisual-0.4-0:i386
  libvo-amrwbenc0:i386 libvorbis0a:i386 libvorbisenc2:i386 libvpx9:i386 libvulkan1:i386 libwavpack1:i386 libwayland-client0:i386 libwebp7:i386
  libwebpmux3:i386 libwine:i386 libx11-6:i386 libx11-xcb1:i386 libx264-164:i386 libx265-199:i386 libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386
  libxcb-glx0:i386 libxcb-present0:i386 libxcb-randr0:i386 libxcb-render0:i386 libxcb-shm0:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 libxcb1:i386
  libxcomposite1:i386 libxcursor1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxi6:i386 libxinerama1:i386 libxkbcommon0:i386
  libxkbregistry0:i386 libxml2:i386 libxpm4:i386 libxrandr2:i386 libxrender1:i386 libxshmfence1:i386 libxtst6:i386 libxv1:i386 libxvidcore4:i386
  libxxf86vm1:i386 libzvbi0t64:i386 mesa-va-drivers:i386 mesa-vdpau-drivers:i386 mesa-vulkan-drivers:i386 ocl-icd-libopencl1:i386 pipewire-alsa
  pipewire-audio va-driver-all:i386 vdpau-driver-all:i386
Suggested packages:
  gvfs:i386 i965-va-driver-shaders:i386 libcuda1:i386 libnvcuvid1:i386 libnvidia-encode1:i386 libdv-bin:i386 oss-compat:i386 libgd-tools:i386
  low-memory-monitor:i386 gnutls-bin:i386 gphoto2:i386 libvisual-0.4-plugins:i386 gstreamer1.0-tools:i386 libheif-plugin-x265:i386
  libheif-plugin-ffmpegdec:i386 libheif-plugin-jpegdec:i386 libheif-plugin-jpegenc:i386 libheif-plugin-j2kdec:i386 libheif-plugin-j2kenc:i386
  libheif-plugin-rav1e:i386 libheif-plugin-svtenc:i386 jackd2:i386 odbc-postgresql:i386 tdsodbc:i386 opus-tools:i386 pcscd:i386 pulseaudio:i386
  libraw1394-doc:i386 librsvg2-bin:i386 libsasl2-modules-gssapi-mit:i386 | libsasl2-modules-gssapi-heimdal:i386 libsasl2-modules-ldap:i386
  libsasl2-modules-otp:i386 libsasl2-modules-sql:i386 lm-sensors:i386 speex:i386 gstreamer1.0-libav:i386 gstreamer1.0-plugins-bad:i386
  gstreamer1.0-plugins-ugly:i386 opencl-icd:i386 libvdpau-va-gl1:i386 wine32-preloader:i386
Recommended packages:
  libgl1-amber-dri:i386 libsdl2-2.0-0:i386
The following packages will be REMOVED:
  appimagelauncher bluedevil breeze cheese chrome-gnome-shell code colord default-jdk default-jre doomsday doomsday-common drkonqi endeavour evince
  evolution-data-server fbreader ffmpeg frameworkintegration freedoom gdm3 gir1.2-gst-plugins-base-1.0 gir1.2-mutter-14 gir1.2-rb-3.0 gir1.2-totem-1.0
  gir1.2-webkit-6.0 gir1.2-webkit2-4.1 gitkraken gnome-browser-connector gnome-calendar gnome-color-manager gnome-control-center gnome-initial-setup
  gnome-remote-desktop gnome-session-bin gnome-shell gnome-shell-extension-appindicator gnome-shell-extension-desktop-icons-ng gnome-shell-extension-gpaste
  gnome-shell-extension-gsconnect gnome-shell-extension-gsconnect-browsers gnome-shell-extension-manager gnome-shell-extension-prefs
  gnome-shell-extension-ubuntu-dock gnome-shell-extension-ubuntu-tiling-assistant gnome-shell-extensions gnome-snapshot gnome-startup-applications
  gnome-todo gnome-user-docs gnome-user-docs-es gnome-video-effects google-chrome-stable gstreamer1.0-alsa gstreamer1.0-clutter-3.0 gstreamer1.0-gl
  gstreamer1.0-gtk3 gstreamer1.0-libav gstreamer1.0-libcamera gstreamer1.0-pipewire gstreamer1.0-plugins-bad gstreamer1.0-plugins-base
  gstreamer1.0-plugins-base-apps gstreamer1.0-plugins-good gstreamer1.0-plugins-ugly gstreamer1.0-pulseaudio gstreamer1.0-vaapi gstreamer1.0-x gvfs-backends
  hplip i965-va-driver-shaders indicator-bluetooth joystick kaccounts-providers kactivitymanagerd kde-cli-tools kde-config-gtk-style kde-config-screenlocker
  kde-config-sddm kde-config-updates kde-style-breeze kde-style-oxygen-qt5 kdeconnect kded5 keditbookmarks kgamma5 khelpcenter khotkeys kinfocenter kinit
  kio kio-extras kio-fuse kmenuedit kpackagelauncherqml kpeople-vcard kscreen ksshaskpass ksystemstats ktexteditor-katepart kup-backup kwayland-integration
  kwin-common kwin-style-breeze kwin-x11 kwrited layer-shell-qt libasound2-plugins libatk-wrapper-java libatk-wrapper-java-jni libavcodec-extra
  libavcodec-extra60 libavdevice60 libavfilter9 libavformat60 libavutil58 libcheese-gtk25 libcheese8 libclutter-1.0-0 libclutter-gst-3.0-0
  libclutter-gtk-1.0-0 libcogl-pango20 libcogl-path20 libcogl20 libcolorcorrect5 libdbusmenu-qt5-2 libdirectfb-1.7-7t64 libdmapsharing-4.0-3t64
  libdrm-amdgpu1 libdrm-dev libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdrm2 libedataserverui-1.2-4t64 libedataserverui4-1.0-0t64 libegl-dev
  libegl-mesa0 libegl1 libegl1-mesa-dev libepoxy-dev libevview3-3t64 libfluidsynth3 libfolks-eds26 libgbm-dev libgbm1 libgd3 libgl-dev libgl1
  libgl1-amber-dri libgl1-mesa-dri libglapi-mesa libgles-dev libgles2-mesa-dev libglvnd-dev libglx-dev libglx-mesa0 libglx0 libgphoto2-6t64
  libgstreamer-gl1.0-0 libgstreamer-plugins-bad1.0-0 libgstreamer-plugins-base1.0-0 libgstreamer-plugins-good1.0-0 libgtk-3-dev libgtk-4-media-gstreamer
  libgtkmm-3.0-dev libgupnp-dlna-2.0-4 libkaccounts2 libkdecorations2-5v5 libkdecorations2private10 libkf5auth5 libkf5authcore5 libkf5baloo5
  libkf5bookmarks5 libkf5completion5 libkf5configgui5 libkf5configwidgets5 libkf5contacts5 libkf5crash5 libkf5dbusaddons5 libkf5declarative5
  libkf5filemetadata-bin libkf5globalaccel-bin libkf5globalaccel5 libkf5globalaccelprivate5 libkf5guiaddons-bin libkf5guiaddons5 libkf5iconthemes-bin
  libkf5iconthemes5 libkf5idletime5 libkf5itemviews5 libkf5jobwidgets5 libkf5kcmutils5 libkf5kcmutilscore5 libkf5kdelibs4support5 libkf5kdelibs4support5-bin
  libkf5kexiv2-15.0.0 libkf5khtml-bin libkf5khtml5 libkf5kiocore5 libkf5kiofilewidgets5 libkf5kiogui5 libkf5kiowidgets5 libkf5kirigami2-5 libkf5newstuff5
  libkf5newstuffcore5 libkf5newstuffwidgets5 libkf5notifications5 libkf5notifyconfig5 libkf5parts-plugins libkf5parts5 libkf5people5 libkf5peoplewidgets5
  libkf5plasma5 libkf5plasmaquick5 libkf5prison5 libkf5pulseaudioqt3 libkf5purpose-bin libkf5purpose5 libkf5quickaddons5 libkf5runner5 libkf5screen-bin
  libkf5screen8 libkf5screendpms8 libkf5service-bin libkf5service5 libkf5solid5 libkf5sonnetui5 libkf5style5 libkf5syntaxhighlighting5 libkf5sysguard-bin
  libkf5texteditor-bin libkf5texteditor5 libkf5textwidgets5 libkf5wallet-bin libkf5wallet5 libkf5waylandclient5 libkf5widgetsaddons5 libkf5windowsystem5
  libkf5xmlgui5 libkfontinstui5 libkpipewire5 libkpipewiredmabuf5 libkpipewirerecord5 libkpmcore12 libkscreenlocker5 libksysguardformatter1
  libksysguardsensorfaces1 libksysguardsensors1 libkuserfeedbackcore1 libkwalletbackend5-5 libkwineffects14 libkwinglutils14 libkworkspace5-5
  liblayershellqtinterface5 libmutter-14-0 libnotificationmanager1 libosmesa6 liboxygenstyle5-5 liboxygenstyleconfig5-5 libphonon4qt5-4t64 libpolkit-qt5-1-1
  libpoppler-qt5-1 libpostproc57 libpowerdevilcore2 libprocesscore9 libprocessui9 libqaccessibilityclient-qt5-0 libqmobipocket2 libqt5designer5
  libqt5gui5t64 libqt5help5 libqt5hunspellinputmethod5 libqt5multimedia5 libqt5multimedia5-plugins libqt5multimediagsttools5 libqt5multimediaquick5
  libqt5multimediawidgets5 libqt5printsupport5t64 libqt5quick5 libqt5quickcontrols2-5 libqt5quickparticles5 libqt5quickshapes5 libqt5quicktemplates2-5
  libqt5quickwidgets5 libqt5svg5 libqt5virtualkeyboard5 libqt5waylandclient5 libqt5waylandcompositor5 libqt5webengine5 libqt5webenginecore5
  libqt5webenginewidgets5 libqt5webview5 libqt5widgets5t64 libqt5x11extras5 libreoffice-calc libreoffice-core libreoffice-draw libreoffice-gnome
  libreoffice-gtk3 libreoffice-impress libreoffice-math libreoffice-ogltrans libreoffice-pdfimport libreoffice-writer librhythmbox-core10 libsane1
  libsdl2-2.0-0 libsdl2-mixer-2.0-0 libspice-server1 libswresample4 libswscale7 libtaskmanager6 libtotem0 libva-drm2 libva-wayland2 libva-x11-2
  libvirglrenderer1 libvpl2 libweather-ion7 libwebkit2gtk-4.1-0 libwebkitgtk-6.0-4 libwine libwxgtk-webview3.2-1t64 libxatracker2 libyelp0 lightdm
  mesa-utils mesa-utils-bin mesa-va-drivers mesa-vdpau-drivers mesa-vulkan-drivers milou minecraft-launcher nautilus nautilus-share openjdk-11-jre
  openjdk-21-jdk openjdk-21-jre orca partitionmanager peek phonon4qt5 phonon4qt5-backend-vlc php8.2-gd plasma-browser-integration plasma-desktop
  plasma-discover plasma-discover-backend-fwupd plasma-discover-backend-snap plasma-discover-notifier plasma-disks plasma-firewall plasma-framework
  plasma-integration plasma-nm plasma-pa plasma-systemmonitor plasma-thunderbolt plasma-vault plasma-workspace plymouth plymouth-label
  plymouth-theme-spinner plymouth-theme-ubuntu-text poedit polkit-kde-agent-1 powerdevil pulseaudio pulseaudio-module-bluetooth pulseaudio-module-gsettings
  python3-pyqt5 qemu-system-gui qemu-system-modules-opengl qemu-system-modules-spice qml-module-org-kde-activities qml-module-org-kde-draganddrop
  qml-module-org-kde-kcm qml-module-org-kde-kcmutils qml-module-org-kde-kconfig qml-module-org-kde-kcoreaddons qml-module-org-kde-kio
  qml-module-org-kde-kirigami-addons-labs-mobileform qml-module-org-kde-kirigami2 qml-module-org-kde-kquickcontrols qml-module-org-kde-kquickcontrolsaddons
  qml-module-org-kde-ksysguard qml-module-org-kde-kwindowsystem qml-module-org-kde-newstuff qml-module-org-kde-people qml-module-org-kde-pipewire
  qml-module-org-kde-prison qml-module-org-kde-purpose qml-module-org-kde-qqc2desktopstyle qml-module-org-kde-quickcharts qml-module-org-kde-runnermodel
  qml-module-org-kde-solid qml-module-org-kde-sonnet qml-module-org-kde-syntaxhighlighting qml-module-org-kde-userfeedback qml-module-qt-labs-platform
  qml-module-qtgraphicaleffects qml-module-qtmultimedia qml-module-qtquick-controls qml-module-qtquick-controls2 qml-module-qtquick-dialogs
  qml-module-qtquick-layouts qml-module-qtquick-particles2 qml-module-qtquick-privatewidgets qml-module-qtquick-shapes qml-module-qtquick-templates2
  qml-module-qtquick-virtualkeyboard qml-module-qtquick-window2 qml-module-qtquick2 qml-module-qtwebengine qml-module-sso-onlineaccounts
  qml-module-ubuntu-onlineaccounts qt5-gtk-platformtheme qtvirtualkeyboard-plugin qtwayland5 redshift rhythmbox rhythmbox-plugin-alternative-toolbar
  rhythmbox-plugins rygel sane-utils shotwell simple-scan software-properties-gtk spice-vdagent systemsettings totem totem-plugins tracker-extract
  tracker-miner-fs ubuntu-desktop ubuntu-desktop-minimal ubuntu-docs ubuntu-drivers-common ubuntu-release-upgrader-gtk ubuntu-session unity-control-center
  unity-greeter unity-settings-daemon update-manager update-notifier vdpau-driver-all vlc-plugin-base vlc-plugin-video-output wayland-utils wine64 x11-utils
  xdg-desktop-portal-kde xorg xserver-xorg xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-libinput xserver-xorg-input-wacom
  xserver-xorg-video-all xserver-xorg-video-amdgpu xserver-xorg-video-ati xserver-xorg-video-fbdev xserver-xorg-video-intel xserver-xorg-video-nouveau
  xserver-xorg-video-qxl xserver-xorg-video-radeon xserver-xorg-video-vesa xserver-xorg-video-vmware xwayland yelp
The following NEW packages will be installed:
  glib-networking:i386 gstreamer1.0-plugins-base:i386 gstreamer1.0-plugins-good:i386 gstreamer1.0-x:i386 i965-va-driver:i386 intel-media-va-driver:i386
  libaa1:i386 libaom3:i386 libapparmor1:i386 libaribb24-0t64:i386 libasound2-plugins:i386 libasound2t64:i386 libasyncns0:i386 libatomic1:i386
  libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386 libavc1394-0:i386 libavcodec-extra60:i386 libavutil58:i386 libbrotli1:i386
  libbsd0:i386 libcaca0:i386 libcairo-gobject2:i386 libcairo2:i386 libcapi20-3t64:i386 libcdparanoia0:i386 libcodec2-1.2:i386 libcups2t64:i386
  libcurl3t64-gnutls:i386 libcurl4t64:i386 libdatrie1:i386 libdav1d7:i386 libdb5.3t64:i386 libdbus-1-3:i386 libde265-0:i386 libdeflate0:i386
  libdrm-amdgpu1:i386 libdrm-intel1:i386 libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386 libduktape207:i386 libdv4t64:i386 libdw1t64:i386
  libedit2:i386 libelf1t64:i386 libexif12:i386 libexpat1:i386 libffi8:i386 libflac12t64:i386 libfontconfig1:i386 libfreetype6:i386 libfribidi0:i386
  libgd3:i386 libgdk-pixbuf-2.0-0:i386 libgl1:i386 libgl1-mesa-dri:i386 libglapi-mesa:i386 libglib2.0-0t64:i386 libglvnd0:i386 libglx-mesa0:i386
  libglx0:i386 libgnutls30t64:i386 libgomp1:i386 libgphoto2-6t64:i386 libgphoto2-port12t64:i386 libgraphite2-3:i386 libgsm1:i386
  libgstreamer-plugins-base1.0-0:i386 libgstreamer-plugins-good1.0-0:i386 libgstreamer1.0-0:i386 libgudev-1.0-0:i386 libharfbuzz0b:i386
  libheif-plugin-aomdec:i386 libheif-plugin-aomenc:i386 libheif-plugin-libde265:i386 libheif1:i386 libhogweed6t64:i386 libicu74:i386 libiec61883-0:i386
  libigdgmm12:i386 libjack-jackd2-0:i386 libjbig0:i386 libjpeg-turbo8:i386 libjpeg8:i386 libldap2:i386 libllvm17t64:i386 libltdl7:i386 libmp3lame0:i386
  libmpg123-0t64:i386 libncurses6:i386 libnettle8t64:i386 libnghttp2-14:i386 libnuma1:i386 libodbc2:i386 libogg0:i386 libopencore-amrnb0:i386
  libopencore-amrwb0:i386 libopenjp2-7:i386 libopus0:i386 liborc-0.4-0t64:i386 libosmesa6:i386 libp11-kit0:i386 libpango-1.0-0:i386 libpangocairo-1.0-0:i386
  libpangoft2-1.0-0:i386 libpcap0.8t64:i386 libpciaccess0:i386 libpcsclite1:i386 libpixman-1-0:i386 libpng16-16t64:i386 libproxy1v5:i386 libpsl5t64:i386
  libpulse0:i386 libraw1394-11:i386 libreoffice-core-nogui librsvg2-2:i386 librsvg2-common:i386 librtmp1:i386 libsamplerate0:i386 libsasl2-2:i386
  libsasl2-modules:i386 libsasl2-modules-db:i386 libsensors5:i386 libsharpyuv0:i386 libshine3:i386 libshout3:i386 libslang2:i386 libsnappy1v5:i386
  libsndfile1:i386 libsoup-3.0-0:i386 libsoxr0:i386 libspeex1:i386 libspeexdsp1:i386 libsqlite3-0:i386 libssh-4:i386 libstdc++6:i386 libsvtav1enc1d1:i386
  libswresample4:i386 libtag1v5:i386 libtag1v5-vanilla:i386 libtasn1-6:i386 libthai0:i386 libtheora0:i386 libtiff6:i386 libtwolame0:i386 libunwind8:i386
  libusb-1.0-0:i386 libv4l-0t64:i386 libv4lconvert0t64:i386 libva-drm2:i386 libva-x11-2:i386 libva2:i386 libvdpau1:i386 libvisual-0.4-0:i386
  libvo-amrwbenc0:i386 libvorbis0a:i386 libvorbisenc2:i386 libvpx9:i386 libvulkan1:i386 libwavpack1:i386 libwayland-client0:i386 libwebp7:i386
  libwebpmux3:i386 libwine:i386 libx11-6:i386 libx11-xcb1:i386 libx264-164:i386 libx265-199:i386 libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386
  libxcb-glx0:i386 libxcb-present0:i386 libxcb-randr0:i386 libxcb-render0:i386 libxcb-shm0:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 libxcb1:i386
  libxcomposite1:i386 libxcursor1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxi6:i386 libxinerama1:i386 libxkbcommon0:i386
  libxkbregistry0:i386 libxml2:i386 libxpm4:i386 libxrandr2:i386 libxrender1:i386 libxshmfence1:i386 libxtst6:i386 libxv1:i386 libxvidcore4:i386
  libxxf86vm1:i386 libzvbi0t64:i386 mesa-va-drivers:i386 mesa-vdpau-drivers:i386 mesa-vulkan-drivers:i386 ocl-icd-libopencl1:i386 pipewire-alsa
  pipewire-audio va-driver-all:i386 vdpau-driver-all:i386 wine32:i386
0 upgraded, 210 newly installed, 470 to remove and 0 not upgraded.
Need to get 272 MB of archives.
After this operation, 2362 MB disk space will be freed.
Do you want to continue? [Y/n]
```

Regards

---

### Post by 1fallen on 2024-10-30
> **agonzalesc said:**
> @1fallen2 here a .exe  : [https://download.wondershare.net/inst/filmora_setup_full7598.exe](https://download.wondershare.net/inst/filmora_setup_full7598.exe)



See attachment in my last post.

Also I'm surprised to see all that it wants to remove, and do not do it.
Please now run 
```
sudo apt clean
sudo apt update
### and now without this " LC_ALL=C " 
sudo apt install wine32:i386
```
You really don't need it though

---

### Post by agonzalesc on 2024-10-30
Hi.

The result was the same.

```
gonzalesc@puccohp:~/Descargas$ sudo apt clean
gonzalesc@puccohp:~/Descargas$ sudo apt update
Obj:1 https://download.docker.com/linux/ubuntu focal InRelease
Obj:2 https://download.docker.com/linux/ubuntu noble InRelease                                       
Obj:3 https://download.docker.com/linux/ubuntu jammy InRelease                                       
Obj:4 http://archive.ubuntu.com/ubuntu noble InRelease                       
Obj:5 http://security.ubuntu.com/ubuntu noble-security InRelease
Obj:6 http://archive.ubuntu.com/ubuntu noble-updates InRelease
Obj:7 http://archive.ubuntu.com/ubuntu noble-backports InRelease
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
Leyendo la información de estado... Hecho
Todos los paquetes están actualizados.
W: https://download.docker.com/linux/ubuntu/dists/noble/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
N: Omitiendo el uso del fichero configurado «stable/binary-i386/Packages» ya que el repositorio «https://download.docker.com/linux/ubuntu noble InRelease» no admite la arquitectura «i386»
gonzalesc@puccohp:~/Descargas$ sudo apt install wine32:i386
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
Leyendo la información de estado... Hecho
Los paquetes indicados a continuación se instalaron de forma automática y ya no son necesarios.
  accountsservice-ubuntu-schemas activity-log-manager aha apg apt-config-icons-large apt-config-icons-large-hidpi bamfdaemon breeze-cursor-theme
  breeze-gtk-theme bup bup-doc ca-certificates-java catdoc cheese-common clinfo colord-data cryfs default-jdk-headless default-jre-headless docbook-xml
  docbook-xsl doomsday-data endeavour-common evemu-tools evince-common evolution-data-server-common evtest fluid-soundfont-gm folks-common
  fonts-dejavu-extra fonts-hack fonts-noto-hinted fonts-noto-ui-core fonts-noto-unhinted gir1.2-accountsservice-1.0 gir1.2-atspi-2.0 gir1.2-camel-1.2
  gir1.2-ebookcontacts-1.2 gir1.2-edataserver-1.2 gir1.2-folks-0.7 gir1.2-gck-2 gir1.2-gcr-4 gir1.2-gdata-0.0 gir1.2-gdm-1.0 gir1.2-gee-0.8
  gir1.2-geoclue-2.0 gir1.2-gnomeautoar-0.1 gir1.2-gnomebg-4.0 gir1.2-gnomebluetooth-3.0 gir1.2-gnomedesktop-3.0 gir1.2-goa-1.0 gir1.2-gpaste-2
  gir1.2-gsound-1.0 gir1.2-gstreamer-1.0 gir1.2-gtop-2.0 gir1.2-gweather-4.0 gir1.2-javascriptcoregtk-4.1 gir1.2-javascriptcoregtk-6.0 gir1.2-json-1.0
  gir1.2-nautilus-4.0 gir1.2-nm-1.0 gir1.2-nma4-1.0 gir1.2-snapd-2 gir1.2-soup-2.4 gir1.2-soup-3.0 gir1.2-telepathyglib-0.12 gir1.2-totemplparser-1.0
  gir1.2-upowerglib-1.0 gkbd-capplet gnome-control-center-faces gnome-online-accounts gnome-screensaver gnome-session-common gpaste-2 grilo-plugins-0.3-base
  heif-gdk-pixbuf heif-thumbnailer hplip-data indicator-applet indicator-application indicator-appmenu indicator-common indicator-datetime
  indicator-keyboard indicator-messages indicator-power indicator-printers indicator-session indicator-sound java-common jayatana kactivities-bin
  kde-cli-tools-data kdoctools5 khotkeys-data kio-extras-data kirigami-addons-data kpackagetool5 ktexteditor-data kuserfeedback-doc kwayland-data kwin-data
  liba52-0.7.4 libaa1 libaacs0 libabsl20210324 libabw-0.1-1 libaccounts-glib0 libaccounts-qt5-1 libappimage0 libappimage1.0abi1t64 libappstreamqt5-3
  libaribb24-0t64 libass9 libassimp5 libatk-bridge2.0-dev libatk1.0-dev libatkmm-1.6-dev libatspi2.0-dev libavc1394-0 libavif13 libavtp0 libbamf3-2t64
  libbdplus0 libblas3 libbluray2 libboost-chrono1.83.0t64 libboost-filesystem1.83.0 libboost-program-options1.83.0 libbs2b0 libcaca0 libcairomm-1.0-dev
  libcamel-1.2-64t64 libcamera0.2 libcapi20-3t64 libcddb2 libcdio-cdda2t64 libcdio-paranoia2t64 libcdio19t64 libcdparanoia0 libcdr-0.1-1 libchromaprint1
  libcjson1 libcld2-0 libclutter-1.0-common libcodec2-1.2 libcogl-common libcolamd3 libcolord-gtk4-1t64 libcolorhug2 libcpprest2.10 libcue2 libdatrie-dev
  libdav1d5 libdav1d7 libdbus-1-dev libdc1394-25 libdca0 libdecor-0-0 libdecor-0-plugin-1-cairo libdeflate-dev libdmtx0t64 libdouble-conversion3 libdraco8
  libdv4t64 libdvbpsi10 libdvdnav4 libdvdread8t64 libe-book-0.1-1 libebackend-1.2-11t64 libebml5 libebook-1.2-21t64 libebook-contacts-1.2-4t64 libecal-2.0-3
  libedata-book-1.2-27t64 libedata-cal-2.0-2t64 libedataserver-1.2-27t64 libei1 libeis1 libepub0 libepubgen-0.1-1 libetonyek-0.1-1 libevdocument3-4t64
  libevemu3t64 libexiv2-27 libfaad2 libfakekey0 libfcitx-config4 libfcitx-gclient1 libfcitx-utils0 libflite1 libfmt9 libfolks26 libfontconfig1-dev
  libfreehand-0.1-1 libfreerdp-server3-3 libfribidi-dev libgav1-0 libgdata-common libgdata22 libgdk-pixbuf-2.0-dev libgdk-pixbuf-xlib-2.0-0
  libgdk-pixbuf2.0-0 libgdm1 libgeonames-common libgeonames0 libgexiv2-2 libgfortran5 libgit2-1.7 libgles1 libgles2 libglibmm-2.4-dev libglu1-mesa
  libglvnd-core-dev libglvnd0 libgme0 libgnome-autoar-0-0 libgnome-bluetooth-ui-3.0-13 libgnome-panel3 libgnome-rr-4-2t64 libgnomekbd-common libgnomekbd8
  libgoa-1.0-0b libgoa-1.0-common libgoa-backend-1.0-2 libgom-1.0-0t64 libgpaste-2-common libgpaste-2t64 libgphoto2-port12t64 libgpod-common libgpod4t64
  libgps30t64 libgrantlee-templates5 libgraphite2-dev libgrilo-0.3-0 libgsettings-qt1 libgsf-1-114 libgsf-1-common libgsm1 libgsound0t64 libgssdp-1.6-0
  libgtkspell3-3-0 libgupnp-1.6-0 libgupnp-av-1.0-3 libgupnp-igd-1.6-0 libgxps2t64 libharfbuzz-cairo0 libharfbuzz-dev libharfbuzz-subset0 libhfstospell11
  libhpmud0 libhttp-parser2.9 libido3-0.1-0 libiec61883-0 libieee1284-3 libimagequant0 libindicator3-7 libinstpatch-1.0-2 libixml11t64 libjack-jackd2-0
  libjavascriptcoregtk-4.1-0 libjavascriptcoregtk-6.0-1 libjbig-dev libkate1 libkdsoap1 libkeybinder-3.0-0 libkf5activities5 libkf5activitiesstats1
  libkf5archive-data libkf5archive5 libkf5attica5 libkf5auth-data libkf5balooengine5 libkf5bluezqt-data libkf5bluezqt6 libkf5bookmarks-data
  libkf5calendarevents5 libkf5codecs-data libkf5codecs5 libkf5completion-data libkf5config-bin libkf5config-data libkf5configcore5 libkf5configqml5
  libkf5configwidgets-data libkf5contacts-data libkf5coreaddons-data libkf5coreaddons5 libkf5dbusaddons-bin libkf5dbusaddons-data libkf5declarative-data
  libkf5dnssd-data libkf5dnssd5 libkf5doctools5 libkf5filemetadata-data libkf5filemetadata3 libkf5globalaccel-data libkf5guiaddons-data libkf5holidays-data
  libkf5holidays5 libkf5i18n-data libkf5i18n5 libkf5i18nlocaledata5 libkf5iconthemes-data libkf5itemmodels5 libkf5itemviews-data libkf5jobwidgets-data
  libkf5js5t64 libkf5kcmutils-data libkf5kdelibs4support-data libkf5khtml-data libkf5kiontlm5 libkf5modemmanagerqt6 libkf5networkmanagerqt6
  libkf5newstuff-data libkf5notifications-data libkf5notifyconfig-data libkf5package-data libkf5package5 libkf5parts-data libkf5people-data
  libkf5peoplebackend5 libkf5pty-data libkf5pty5 libkf5screen-data libkf5service-data libkf5solid5-data libkf5sonnet5-data libkf5sonnetcore5 libkf5su-bin
  libkf5su-data libkf5su5 libkf5syndication5abi1 libkf5syntaxhighlighting-data libkf5sysguard-data libkf5textwidgets-data libkf5threadweaver5
  libkf5wallet-data libkf5widgetsaddons-data libkf5windowsystem-data libkf5xmlgui-bin libkf5xmlgui-data libkfontinst5 libkpathsea6 libksgrd9
  libksysguardsystemstats1 libkuserfeedback-l10n liblapack3 liblerc-dev liblightdm-gobject-1-0 liblilv-0-0 liblirc-client0t64 liblrdf0 libltc11
  liblttng-ust-common1t64 liblttng-ust-ctl5t64 liblttng-ust1t64 liblua5.2-0 liblucene++0t64 liblzma-dev libmad0 libmanette-0.2-0 libmarkdown2 libmatroska7
  libmbedcrypto7t64 libmd4c0 libmediaart-2.0-0 libmessaging-menu0 libminizip1t64 libmjpegutils-2.1-0t64 libmodplug1 libmpcdec6 libmpeg2-4
  libmpeg2encpp-2.1-0t64 libmplex2-2.1-0t64 libmsgraph-0-1 libmspub-0.1-1 libmtp-common libmtp-runtime libmtp9t64 libmwaw-0.3-3 libmysofa1 libneon27t64
  libnice10 libnorm1t64 libodbc2 libodfgen-0.1-1 libopenal-data libopenal1 libopenconnect5 libopencore-amrnb0 libopencore-amrwb0 libopengl-dev libopengl0
  libopenh264-7 libopenmpt-modplug1 libopenmpt0t64 libopenni2-0 libopusfile0 liborc-0.4-0t64 liborcus-0.18-0 liborcus-parser-0.18-0 libpackagekitqt5-1
  libpagemaker-0.0-0 libpam-kwallet-common libpam-kwallet5 libpango1.0-dev libpangomm-1.4-dev libpciaccess-dev libpciaccess0 libpgm-5.3-0 libphonenumber8
  libphonon-l10n libplacebo338 libplasma-geolocation-interface5 libplymouth5 libpocketsphinx3 libpoppler-glib8t64 libpoppler118 libportal-gtk3-1
  libportal-gtk4-1 libportal1 libpowerdevilui5 libprotobuf-lite32t64 libprotobuf32t64 libproxy-tools libpskc0t64 libqalculate-data libqalculate22t64
  libqca-qt5-2 libqca-qt5-2-plugins libqt5concurrent5t64 libqt5core5t64 libqt5dbus5t64 libqt5network5t64 libqt5positioning5 libqt5qml5 libqt5qmlmodels5
  libqt5qmlworkerscript5 libqt5sensors5 libqt5sql5-sqlite libqt5sql5t64 libqt5test5t64 libqt5texttospeech5 libqt5webchannel5 libqt5webengine-data
  libqt5xml5t64 librabbitmq4 libraqm0 librav1e0 libraw1394-11 libreoffice-base-core libreoffice-uiconfig-calc libreoffice-uiconfig-draw
  libreoffice-uiconfig-impress libreoffice-uiconfig-math libreoffice-uiconfig-writer libresid-builder0c2a librest-1.0-0 librist4 librubberband2
  librygel-core-2.8-0 librygel-db-2.8-0 librygel-renderer-2.8-0 librygel-server-2.8-0 libsane-common libsane-hpaio libscim8v5 libserd-0-0 libsgutils2-1.46-2
  libsharpyuv-dev libshine3 libshout3 libsidplay1v5 libsidplay2 libsigc++-2.0-dev libsignon-plugins-common1 libsignon-qt5-1 libsnapd-qt-2-1 libsnappy1v5
  libsndio7.0 libsnmp-base libsnmp40t64 libsord-0-0 libsoundtouch1 libsoup-2.4-1 libsoup-gnome-2.4-1 libsoup2.4-common libsoxr0 libspandsp2t64
  libspatialaudio0t64 libspdlog1.12 libspeex1 libsphinxbase3t64 libsquashfuse0 libsratom-0-0 libsrt1.5-gnutls libsrtp2-1 libssh-gcrypt-4 libssh2-1t64
  libstoken1t64 libsuitesparseconfig7 libsvtav1enc1d1 libsynctex2 libsysmetrics1 libtag1v5 libtag1v5-vanilla libtelepathy-glib0t64 libtext-engine-0.1-0
  libthai-dev libtheora0 libtiff-dev libtiffxx6 libtimezonemap-data libtimezonemap1 libtomcrypt1 libtommath1 libtotem-plparser-common libtotem-plparser18
  libtracker-sparql-3.0-0 libtss2-tcti-libtpms0t64 libtss2-tcti-spi-helper0t64 libtss2-tctildr0t64 libtwolame0 libudfread0 libunibreak5
  libunity-control-center1 libunity-gtk2-parser0 libunity-gtk3-parser0 libunity-settings-daemon1 libupnp17t64 libv4l-0t64 libv4lconvert0t64 libvdpau1
  libvidstab1.1 libvisio-0.1-1 libvisual-0.4-0 libvlc-bin libvlc5 libvlccore9 libvo-aacenc0 libvo-amrwbenc0 libvoikko1 libvpx9 libwavpack1 libwebp-dev
  libwebpdecoder3 libwildmidi2 libwoff1 libwpd-0.10-10 libwpg-0.3-3 libwps-0.4-4 libwrap0 libx264-164 libx265-199 libxapian30 libxcb-cursor0 libxcb-damage0
  libxcb-dpms0 libxcb-dri2-0 libxcb-dri3-0 libxcb-glx0 libxcb-icccm4 libxcb-image0 libxcb-keysyms1 libxcb-present0 libxcb-randr0 libxcb-record0
  libxcb-render-util0 libxcb-res0 libxcb-sync1 libxcb-xinerama0 libxcb-xkb1 libxcb-xv0 libxcomposite-dev libxcursor-dev libxcvt0 libxdamage-dev
  libxdgutilsbasedir1.0.1 libxdgutilsdesktopentry1.0.1 libxfixes-dev libxfont2 libxft-dev libxi-dev libxinerama-dev libxkbcommon-x11-0 libxklavier16
  libxmlsec1t64-openssl libxrandr-dev libxshmfence1 libxt-dev libxtst-dev libxv1 libxvidcore4 libxvmc1 libxxf86dga1 libyuv0 libzbar0t64 libzeitgeist-2.0-0
  libzimg2 libzix-0-0 libzlcore-data libzlcore0.13t64 libzltext-data libzltext0.13t64 libzmq5 libzstd-dev libzvbi0t64 libzxing3 lp-solve media-player-info
  mobile-broadband-provider-info mutter-common-bin nautilus-data network-manager-gnome openjdk-11-jre-headless openjdk-21-jdk-headless
  openjdk-21-jre-headless oxygen-sounds pango1.0-tools phonon-backend-vlc-common plasma-desktop-data plasma-discover-common plasma-workspace-data
  pocketsphinx-en-us poedit-common policykit-1-gnome power-profiles-daemon powerdevil-data printer-driver-hpcups printer-driver-postscript-hp python3-brlapi
  python3-click python3-colorama python3-dateutil python3-freetype python3-fuse python3-louis python3-nautilus python3-olefile python3-pil python3-pylibacl
  python3-pyqt5.sip python3-pyxattr python3-reportlab python3-rlpycairo python3-speechd python3-tornado python3-xkit qdbus-qt5 qml-module-gsettings1.0
  qml-module-org-kde-bluezqt qml-module-org-kde-kholidays qml-module-org-kde-kitemmodels qml-module-qt-labs-folderlistmodel qml-module-qt-labs-qmlmodels
  qml-module-qt-labs-settings qml-module-qtqml qml-module-qtqml-models2 qtchooser qtspeech5-speechd-plugin qttranslations5-l10n rhythmbox-data sane-airscan
  sgml-data signon-plugin-oauth2 smartmontools socat sonnet-plugins sshfs switcheroo-control tecla timgm6mb-soundfont totem-common tracker
  ubuntu-advantage-desktop-daemon ubuntu-touch-sounds unity-gtk-module-common unity-gtk2-module unity-gtk3-module unity-settings-daemon-schemas vlc-data
  vulkan-tools wayland-protocols x11-apps x11-session-utils x11-xkb-utils xbitmaps xbrlapi xcvt xdg-dbus-proxy xfonts-base xfonts-scalable xinit xinput
  xserver-common xserver-xorg-legacy xsettingsd yelp-xsl zeitgeist-core
Utilice «sudo apt autoremove» para eliminarlos.
Se instalarán los siguientes paquetes adicionales:
  glib-networking:i386 gstreamer1.0-plugins-base:i386 gstreamer1.0-plugins-good:i386 gstreamer1.0-x:i386 i965-va-driver:i386 intel-media-va-driver:i386
  libaa1:i386 libaom3:i386 libapparmor1:i386 libaribb24-0t64:i386 libasound2-plugins:i386 libasound2t64:i386 libasyncns0:i386 libatomic1:i386
  libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386 libavc1394-0:i386 libavcodec-extra60:i386 libavutil58:i386 libbrotli1:i386
  libbsd0:i386 libcaca0:i386 libcairo-gobject2:i386 libcairo2:i386 libcapi20-3t64:i386 libcdparanoia0:i386 libcodec2-1.2:i386 libcups2t64:i386
  libcurl3t64-gnutls:i386 libcurl4t64:i386 libdatrie1:i386 libdav1d7:i386 libdb5.3t64:i386 libdbus-1-3:i386 libde265-0:i386 libdeflate0:i386
  libdrm-amdgpu1:i386 libdrm-intel1:i386 libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386 libduktape207:i386 libdv4t64:i386 libdw1t64:i386
  libedit2:i386 libelf1t64:i386 libexif12:i386 libexpat1:i386 libffi8:i386 libflac12t64:i386 libfontconfig1:i386 libfreetype6:i386 libfribidi0:i386
  libgd3:i386 libgdk-pixbuf-2.0-0:i386 libgl1:i386 libgl1-mesa-dri:i386 libglapi-mesa:i386 libglib2.0-0t64:i386 libglvnd0:i386 libglx-mesa0:i386
  libglx0:i386 libgnutls30t64:i386 libgomp1:i386 libgphoto2-6t64:i386 libgphoto2-port12t64:i386 libgraphite2-3:i386 libgsm1:i386
  libgstreamer-plugins-base1.0-0:i386 libgstreamer-plugins-good1.0-0:i386 libgstreamer1.0-0:i386 libgudev-1.0-0:i386 libharfbuzz0b:i386
  libheif-plugin-aomdec:i386 libheif-plugin-aomenc:i386 libheif-plugin-libde265:i386 libheif1:i386 libhogweed6t64:i386 libicu74:i386 libiec61883-0:i386
  libigdgmm12:i386 libjack-jackd2-0:i386 libjbig0:i386 libjpeg-turbo8:i386 libjpeg8:i386 libldap2:i386 libllvm17t64:i386 libltdl7:i386 libmp3lame0:i386
  libmpg123-0t64:i386 libncurses6:i386 libnettle8t64:i386 libnghttp2-14:i386 libnuma1:i386 libodbc2:i386 libogg0:i386 libopencore-amrnb0:i386
  libopencore-amrwb0:i386 libopenjp2-7:i386 libopus0:i386 liborc-0.4-0t64:i386 libosmesa6:i386 libp11-kit0:i386 libpango-1.0-0:i386 libpangocairo-1.0-0:i386
  libpangoft2-1.0-0:i386 libpcap0.8t64:i386 libpciaccess0:i386 libpcsclite1:i386 libpixman-1-0:i386 libpng16-16t64:i386 libproxy1v5:i386 libpsl5t64:i386
  libpulse0:i386 libraw1394-11:i386 libreoffice-core-nogui librsvg2-2:i386 librsvg2-common:i386 librtmp1:i386 libsamplerate0:i386 libsasl2-2:i386
  libsasl2-modules:i386 libsasl2-modules-db:i386 libsensors5:i386 libsharpyuv0:i386 libshine3:i386 libshout3:i386 libslang2:i386 libsnappy1v5:i386
  libsndfile1:i386 libsoup-3.0-0:i386 libsoxr0:i386 libspeex1:i386 libspeexdsp1:i386 libsqlite3-0:i386 libssh-4:i386 libstdc++6:i386 libsvtav1enc1d1:i386
  libswresample4:i386 libtag1v5:i386 libtag1v5-vanilla:i386 libtasn1-6:i386 libthai0:i386 libtheora0:i386 libtiff6:i386 libtwolame0:i386 libunwind8:i386
  libusb-1.0-0:i386 libv4l-0t64:i386 libv4lconvert0t64:i386 libva-drm2:i386 libva-x11-2:i386 libva2:i386 libvdpau1:i386 libvisual-0.4-0:i386
  libvo-amrwbenc0:i386 libvorbis0a:i386 libvorbisenc2:i386 libvpx9:i386 libvulkan1:i386 libwavpack1:i386 libwayland-client0:i386 libwebp7:i386
  libwebpmux3:i386 libwine:i386 libx11-6:i386 libx11-xcb1:i386 libx264-164:i386 libx265-199:i386 libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386
  libxcb-glx0:i386 libxcb-present0:i386 libxcb-randr0:i386 libxcb-render0:i386 libxcb-shm0:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 libxcb1:i386
  libxcomposite1:i386 libxcursor1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxi6:i386 libxinerama1:i386 libxkbcommon0:i386
  libxkbregistry0:i386 libxml2:i386 libxpm4:i386 libxrandr2:i386 libxrender1:i386 libxshmfence1:i386 libxtst6:i386 libxv1:i386 libxvidcore4:i386
  libxxf86vm1:i386 libzvbi0t64:i386 mesa-va-drivers:i386 mesa-vdpau-drivers:i386 mesa-vulkan-drivers:i386 ocl-icd-libopencl1:i386 pipewire-alsa
  pipewire-audio va-driver-all:i386 vdpau-driver-all:i386
Paquetes sugeridos:
  gvfs:i386 i965-va-driver-shaders:i386 libcuda1:i386 libnvcuvid1:i386 libnvidia-encode1:i386 libdv-bin:i386 oss-compat:i386 libgd-tools:i386
  low-memory-monitor:i386 gnutls-bin:i386 gphoto2:i386 libvisual-0.4-plugins:i386 gstreamer1.0-tools:i386 libheif-plugin-x265:i386
  libheif-plugin-ffmpegdec:i386 libheif-plugin-jpegdec:i386 libheif-plugin-jpegenc:i386 libheif-plugin-j2kdec:i386 libheif-plugin-j2kenc:i386
  libheif-plugin-rav1e:i386 libheif-plugin-svtenc:i386 jackd2:i386 odbc-postgresql:i386 tdsodbc:i386 opus-tools:i386 pcscd:i386 pulseaudio:i386
  libraw1394-doc:i386 librsvg2-bin:i386 libsasl2-modules-gssapi-mit:i386 | libsasl2-modules-gssapi-heimdal:i386 libsasl2-modules-ldap:i386
  libsasl2-modules-otp:i386 libsasl2-modules-sql:i386 lm-sensors:i386 speex:i386 gstreamer1.0-libav:i386 gstreamer1.0-plugins-bad:i386
  gstreamer1.0-plugins-ugly:i386 opencl-icd:i386 libvdpau-va-gl1:i386 wine32-preloader:i386
Paquetes recomendados:
  libgl1-amber-dri:i386 libsdl2-2.0-0:i386
Los siguientes paquetes se ELIMINARÁN:
  appimagelauncher bluedevil breeze cheese chrome-gnome-shell code colord default-jdk default-jre doomsday doomsday-common drkonqi endeavour evince
  evolution-data-server fbreader ffmpeg frameworkintegration freedoom gdm3 gir1.2-gst-plugins-base-1.0 gir1.2-mutter-14 gir1.2-rb-3.0 gir1.2-totem-1.0
  gir1.2-webkit-6.0 gir1.2-webkit2-4.1 gitkraken gnome-browser-connector gnome-calendar gnome-color-manager gnome-control-center gnome-initial-setup
  gnome-remote-desktop gnome-session-bin gnome-shell gnome-shell-extension-appindicator gnome-shell-extension-desktop-icons-ng gnome-shell-extension-gpaste
  gnome-shell-extension-gsconnect gnome-shell-extension-gsconnect-browsers gnome-shell-extension-manager gnome-shell-extension-prefs
  gnome-shell-extension-ubuntu-dock gnome-shell-extension-ubuntu-tiling-assistant gnome-shell-extensions gnome-snapshot gnome-startup-applications
  gnome-todo gnome-user-docs gnome-user-docs-es gnome-video-effects google-chrome-stable gstreamer1.0-alsa gstreamer1.0-clutter-3.0 gstreamer1.0-gl
  gstreamer1.0-gtk3 gstreamer1.0-libav gstreamer1.0-libcamera gstreamer1.0-pipewire gstreamer1.0-plugins-bad gstreamer1.0-plugins-base
  gstreamer1.0-plugins-base-apps gstreamer1.0-plugins-good gstreamer1.0-plugins-ugly gstreamer1.0-pulseaudio gstreamer1.0-vaapi gstreamer1.0-x gvfs-backends
  hplip i965-va-driver-shaders indicator-bluetooth joystick kaccounts-providers kactivitymanagerd kde-cli-tools kde-config-gtk-style kde-config-screenlocker
  kde-config-sddm kde-config-updates kde-style-breeze kde-style-oxygen-qt5 kdeconnect kded5 keditbookmarks kgamma5 khelpcenter khotkeys kinfocenter kinit
  kio kio-extras kio-fuse kmenuedit kpackagelauncherqml kpeople-vcard kscreen ksshaskpass ksystemstats ktexteditor-katepart kup-backup kwayland-integration
  kwin-common kwin-style-breeze kwin-x11 kwrited layer-shell-qt libasound2-plugins libatk-wrapper-java libatk-wrapper-java-jni libavcodec-extra
  libavcodec-extra60 libavdevice60 libavfilter9 libavformat60 libavutil58 libcheese-gtk25 libcheese8 libclutter-1.0-0 libclutter-gst-3.0-0
  libclutter-gtk-1.0-0 libcogl-pango20 libcogl-path20 libcogl20 libcolorcorrect5 libdbusmenu-qt5-2 libdirectfb-1.7-7t64 libdmapsharing-4.0-3t64
  libdrm-amdgpu1 libdrm-dev libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdrm2 libedataserverui-1.2-4t64 libedataserverui4-1.0-0t64 libegl-dev
  libegl-mesa0 libegl1 libegl1-mesa-dev libepoxy-dev libevview3-3t64 libfluidsynth3 libfolks-eds26 libgbm-dev libgbm1 libgd3 libgl-dev libgl1
  libgl1-amber-dri libgl1-mesa-dri libglapi-mesa libgles-dev libgles2-mesa-dev libglvnd-dev libglx-dev libglx-mesa0 libglx0 libgphoto2-6t64
  libgstreamer-gl1.0-0 libgstreamer-plugins-bad1.0-0 libgstreamer-plugins-base1.0-0 libgstreamer-plugins-good1.0-0 libgtk-3-dev libgtk-4-media-gstreamer
  libgtkmm-3.0-dev libgupnp-dlna-2.0-4 libkaccounts2 libkdecorations2-5v5 libkdecorations2private10 libkf5auth5 libkf5authcore5 libkf5baloo5
  libkf5bookmarks5 libkf5completion5 libkf5configgui5 libkf5configwidgets5 libkf5contacts5 libkf5crash5 libkf5dbusaddons5 libkf5declarative5
  libkf5filemetadata-bin libkf5globalaccel-bin libkf5globalaccel5 libkf5globalaccelprivate5 libkf5guiaddons-bin libkf5guiaddons5 libkf5iconthemes-bin
  libkf5iconthemes5 libkf5idletime5 libkf5itemviews5 libkf5jobwidgets5 libkf5kcmutils5 libkf5kcmutilscore5 libkf5kdelibs4support5 libkf5kdelibs4support5-bin
  libkf5kexiv2-15.0.0 libkf5khtml-bin libkf5khtml5 libkf5kiocore5 libkf5kiofilewidgets5 libkf5kiogui5 libkf5kiowidgets5 libkf5kirigami2-5 libkf5newstuff5
  libkf5newstuffcore5 libkf5newstuffwidgets5 libkf5notifications5 libkf5notifyconfig5 libkf5parts-plugins libkf5parts5 libkf5people5 libkf5peoplewidgets5
  libkf5plasma5 libkf5plasmaquick5 libkf5prison5 libkf5pulseaudioqt3 libkf5purpose-bin libkf5purpose5 libkf5quickaddons5 libkf5runner5 libkf5screen-bin
  libkf5screen8 libkf5screendpms8 libkf5service-bin libkf5service5 libkf5solid5 libkf5sonnetui5 libkf5style5 libkf5syntaxhighlighting5 libkf5sysguard-bin
  libkf5texteditor-bin libkf5texteditor5 libkf5textwidgets5 libkf5wallet-bin libkf5wallet5 libkf5waylandclient5 libkf5widgetsaddons5 libkf5windowsystem5
  libkf5xmlgui5 libkfontinstui5 libkpipewire5 libkpipewiredmabuf5 libkpipewirerecord5 libkpmcore12 libkscreenlocker5 libksysguardformatter1
  libksysguardsensorfaces1 libksysguardsensors1 libkuserfeedbackcore1 libkwalletbackend5-5 libkwineffects14 libkwinglutils14 libkworkspace5-5
  liblayershellqtinterface5 libmutter-14-0 libnotificationmanager1 libosmesa6 liboxygenstyle5-5 liboxygenstyleconfig5-5 libphonon4qt5-4t64 libpolkit-qt5-1-1
  libpoppler-qt5-1 libpostproc57 libpowerdevilcore2 libprocesscore9 libprocessui9 libqaccessibilityclient-qt5-0 libqmobipocket2 libqt5designer5
  libqt5gui5t64 libqt5help5 libqt5hunspellinputmethod5 libqt5multimedia5 libqt5multimedia5-plugins libqt5multimediagsttools5 libqt5multimediaquick5
  libqt5multimediawidgets5 libqt5printsupport5t64 libqt5quick5 libqt5quickcontrols2-5 libqt5quickparticles5 libqt5quickshapes5 libqt5quicktemplates2-5
  libqt5quickwidgets5 libqt5svg5 libqt5virtualkeyboard5 libqt5waylandclient5 libqt5waylandcompositor5 libqt5webengine5 libqt5webenginecore5
  libqt5webenginewidgets5 libqt5webview5 libqt5widgets5t64 libqt5x11extras5 libreoffice-calc libreoffice-core libreoffice-draw libreoffice-gnome
  libreoffice-gtk3 libreoffice-impress libreoffice-math libreoffice-ogltrans libreoffice-pdfimport libreoffice-writer librhythmbox-core10 libsane1
  libsdl2-2.0-0 libsdl2-mixer-2.0-0 libspice-server1 libswresample4 libswscale7 libtaskmanager6 libtotem0 libva-drm2 libva-wayland2 libva-x11-2
  libvirglrenderer1 libvpl2 libweather-ion7 libwebkit2gtk-4.1-0 libwebkitgtk-6.0-4 libwine libwxgtk-webview3.2-1t64 libxatracker2 libyelp0 lightdm
  mesa-utils mesa-utils-bin mesa-va-drivers mesa-vdpau-drivers mesa-vulkan-drivers milou minecraft-launcher nautilus nautilus-share openjdk-11-jre
  openjdk-21-jdk openjdk-21-jre orca partitionmanager peek phonon4qt5 phonon4qt5-backend-vlc php8.2-gd plasma-browser-integration plasma-desktop
  plasma-discover plasma-discover-backend-fwupd plasma-discover-backend-snap plasma-discover-notifier plasma-disks plasma-firewall plasma-framework
  plasma-integration plasma-nm plasma-pa plasma-systemmonitor plasma-thunderbolt plasma-vault plasma-workspace plymouth plymouth-label
  plymouth-theme-spinner plymouth-theme-ubuntu-text poedit polkit-kde-agent-1 powerdevil pulseaudio pulseaudio-module-bluetooth pulseaudio-module-gsettings
  python3-pyqt5 qemu-system-gui qemu-system-modules-opengl qemu-system-modules-spice qml-module-org-kde-activities qml-module-org-kde-draganddrop
  qml-module-org-kde-kcm qml-module-org-kde-kcmutils qml-module-org-kde-kconfig qml-module-org-kde-kcoreaddons qml-module-org-kde-kio
  qml-module-org-kde-kirigami-addons-labs-mobileform qml-module-org-kde-kirigami2 qml-module-org-kde-kquickcontrols qml-module-org-kde-kquickcontrolsaddons
  qml-module-org-kde-ksysguard qml-module-org-kde-kwindowsystem qml-module-org-kde-newstuff qml-module-org-kde-people qml-module-org-kde-pipewire
  qml-module-org-kde-prison qml-module-org-kde-purpose qml-module-org-kde-qqc2desktopstyle qml-module-org-kde-quickcharts qml-module-org-kde-runnermodel
  qml-module-org-kde-solid qml-module-org-kde-sonnet qml-module-org-kde-syntaxhighlighting qml-module-org-kde-userfeedback qml-module-qt-labs-platform
  qml-module-qtgraphicaleffects qml-module-qtmultimedia qml-module-qtquick-controls qml-module-qtquick-controls2 qml-module-qtquick-dialogs
  qml-module-qtquick-layouts qml-module-qtquick-particles2 qml-module-qtquick-privatewidgets qml-module-qtquick-shapes qml-module-qtquick-templates2
  qml-module-qtquick-virtualkeyboard qml-module-qtquick-window2 qml-module-qtquick2 qml-module-qtwebengine qml-module-sso-onlineaccounts
  qml-module-ubuntu-onlineaccounts qt5-gtk-platformtheme qtvirtualkeyboard-plugin qtwayland5 redshift rhythmbox rhythmbox-plugin-alternative-toolbar
  rhythmbox-plugins rygel sane-utils shotwell simple-scan software-properties-gtk spice-vdagent systemsettings totem totem-plugins tracker-extract
  tracker-miner-fs ubuntu-desktop ubuntu-desktop-minimal ubuntu-docs ubuntu-drivers-common ubuntu-release-upgrader-gtk ubuntu-session unity-control-center
  unity-greeter unity-settings-daemon update-manager update-notifier vdpau-driver-all vlc-plugin-base vlc-plugin-video-output wayland-utils wine64 x11-utils
  xdg-desktop-portal-kde xorg xserver-xorg xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-libinput xserver-xorg-input-wacom
  xserver-xorg-video-all xserver-xorg-video-amdgpu xserver-xorg-video-ati xserver-xorg-video-fbdev xserver-xorg-video-intel xserver-xorg-video-nouveau
  xserver-xorg-video-qxl xserver-xorg-video-radeon xserver-xorg-video-vesa xserver-xorg-video-vmware xwayland yelp
Se instalarán los siguientes paquetes NUEVOS:
  glib-networking:i386 gstreamer1.0-plugins-base:i386 gstreamer1.0-plugins-good:i386 gstreamer1.0-x:i386 i965-va-driver:i386 intel-media-va-driver:i386
  libaa1:i386 libaom3:i386 libapparmor1:i386 libaribb24-0t64:i386 libasound2-plugins:i386 libasound2t64:i386 libasyncns0:i386 libatomic1:i386
  libavahi-client3:i386 libavahi-common-data:i386 libavahi-common3:i386 libavc1394-0:i386 libavcodec-extra60:i386 libavutil58:i386 libbrotli1:i386
  libbsd0:i386 libcaca0:i386 libcairo-gobject2:i386 libcairo2:i386 libcapi20-3t64:i386 libcdparanoia0:i386 libcodec2-1.2:i386 libcups2t64:i386
  libcurl3t64-gnutls:i386 libcurl4t64:i386 libdatrie1:i386 libdav1d7:i386 libdb5.3t64:i386 libdbus-1-3:i386 libde265-0:i386 libdeflate0:i386
  libdrm-amdgpu1:i386 libdrm-intel1:i386 libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386 libduktape207:i386 libdv4t64:i386 libdw1t64:i386
  libedit2:i386 libelf1t64:i386 libexif12:i386 libexpat1:i386 libffi8:i386 libflac12t64:i386 libfontconfig1:i386 libfreetype6:i386 libfribidi0:i386
  libgd3:i386 libgdk-pixbuf-2.0-0:i386 libgl1:i386 libgl1-mesa-dri:i386 libglapi-mesa:i386 libglib2.0-0t64:i386 libglvnd0:i386 libglx-mesa0:i386
  libglx0:i386 libgnutls30t64:i386 libgomp1:i386 libgphoto2-6t64:i386 libgphoto2-port12t64:i386 libgraphite2-3:i386 libgsm1:i386
  libgstreamer-plugins-base1.0-0:i386 libgstreamer-plugins-good1.0-0:i386 libgstreamer1.0-0:i386 libgudev-1.0-0:i386 libharfbuzz0b:i386
  libheif-plugin-aomdec:i386 libheif-plugin-aomenc:i386 libheif-plugin-libde265:i386 libheif1:i386 libhogweed6t64:i386 libicu74:i386 libiec61883-0:i386
  libigdgmm12:i386 libjack-jackd2-0:i386 libjbig0:i386 libjpeg-turbo8:i386 libjpeg8:i386 libldap2:i386 libllvm17t64:i386 libltdl7:i386 libmp3lame0:i386
  libmpg123-0t64:i386 libncurses6:i386 libnettle8t64:i386 libnghttp2-14:i386 libnuma1:i386 libodbc2:i386 libogg0:i386 libopencore-amrnb0:i386
  libopencore-amrwb0:i386 libopenjp2-7:i386 libopus0:i386 liborc-0.4-0t64:i386 libosmesa6:i386 libp11-kit0:i386 libpango-1.0-0:i386 libpangocairo-1.0-0:i386
  libpangoft2-1.0-0:i386 libpcap0.8t64:i386 libpciaccess0:i386 libpcsclite1:i386 libpixman-1-0:i386 libpng16-16t64:i386 libproxy1v5:i386 libpsl5t64:i386
  libpulse0:i386 libraw1394-11:i386 libreoffice-core-nogui librsvg2-2:i386 librsvg2-common:i386 librtmp1:i386 libsamplerate0:i386 libsasl2-2:i386
  libsasl2-modules:i386 libsasl2-modules-db:i386 libsensors5:i386 libsharpyuv0:i386 libshine3:i386 libshout3:i386 libslang2:i386 libsnappy1v5:i386
  libsndfile1:i386 libsoup-3.0-0:i386 libsoxr0:i386 libspeex1:i386 libspeexdsp1:i386 libsqlite3-0:i386 libssh-4:i386 libstdc++6:i386 libsvtav1enc1d1:i386
  libswresample4:i386 libtag1v5:i386 libtag1v5-vanilla:i386 libtasn1-6:i386 libthai0:i386 libtheora0:i386 libtiff6:i386 libtwolame0:i386 libunwind8:i386
  libusb-1.0-0:i386 libv4l-0t64:i386 libv4lconvert0t64:i386 libva-drm2:i386 libva-x11-2:i386 libva2:i386 libvdpau1:i386 libvisual-0.4-0:i386
  libvo-amrwbenc0:i386 libvorbis0a:i386 libvorbisenc2:i386 libvpx9:i386 libvulkan1:i386 libwavpack1:i386 libwayland-client0:i386 libwebp7:i386
  libwebpmux3:i386 libwine:i386 libx11-6:i386 libx11-xcb1:i386 libx264-164:i386 libx265-199:i386 libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386
  libxcb-glx0:i386 libxcb-present0:i386 libxcb-randr0:i386 libxcb-render0:i386 libxcb-shm0:i386 libxcb-sync1:i386 libxcb-xfixes0:i386 libxcb1:i386
  libxcomposite1:i386 libxcursor1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxi6:i386 libxinerama1:i386 libxkbcommon0:i386
  libxkbregistry0:i386 libxml2:i386 libxpm4:i386 libxrandr2:i386 libxrender1:i386 libxshmfence1:i386 libxtst6:i386 libxv1:i386 libxvidcore4:i386
  libxxf86vm1:i386 libzvbi0t64:i386 mesa-va-drivers:i386 mesa-vdpau-drivers:i386 mesa-vulkan-drivers:i386 ocl-icd-libopencl1:i386 pipewire-alsa
  pipewire-audio va-driver-all:i386 vdpau-driver-all:i386 wine32:i386
0 actualizados, 210 nuevos se instalarán, 470 para eliminar y 0 no actualizados.
Se necesita descargar 272 MB de archivos.
Se liberarán 2.362 MB después de esta operación.
¿Desea continuar? [S/n] n
```


I want to comment that I upgraded to Ubuntu 24, 2 days ago.

Regards

---

### Post by 1fallen on 2024-10-30
One more suggestion here:
```
sudo apt install winetricks
``` 

It maybe that what you see now is leftover cruft from the Upgrade to 24.04 IJDK, that is puzzling....
What shows with this please:
```
sudo apt autoremove -s
```
That is a dry run only I just want too see what it will do.

---

### Post by agonzalesc on 2024-10-30
Hi
Thanks for the reply.

Here the output

```
gonzalesc@puccohp:~/Descargas$ sudo apt autoremove -s
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
Leyendo la información de estado... Hecho
0 actualizados, 0 nuevos se instalarán, 0 para eliminar y 0 no actualizados.
```


Winetricks is installed but it doesnt work.


```
gonzalesc@puccohp:~/Descargas$ winetricks 
Executing cd /usr/bin
------------------------------------------------------
warning: Unknown file arch of /usr/bin/wine.
------------------------------------------------------
```

But this binary exists.

```
gonzalesc@puccohp:~/Descargas$ ls -all /usr/bin/wine
lrwxrwxrwx 1 root root 22 abr  1  2024 /usr/bin/wine -> /etc/alternatives/wine
gonzalesc@puccohp:~/Descargas$ ls /etc/alternatives/wine -all
lrwxrwxrwx 1 root root 20 abr  1  2024 /etc/alternatives/wine -> /usr/bin/wine-stable
gonzalesc@puccohp:~/Descargas$ ls /usr/bin/wine-stable -all
-rwxr-xr-x 1 root root 1029 abr  1  2024 /usr/bin/wine-stable
```



Regards

---

### Post by 1fallen on 2024-10-30
I do see this when starting winetricks
> You are using a 64-bit WINEPREFIX. Note that many verbs only install 32-bit versions of packages.
 If you encounter problems, please retest in a clean 32-bit WINEPREFIX before reporting a bug.

But that is just a headsup or warning
```
 winetricks
Executing cd /usr/bin
------------------------------------------------------
warning: You are using a 64-bit WINEPREFIX. Note that many verbs only install 32-bit versions of packages. If you encounter problems, please retest in a clean 32-bit WINEPREFIX before reporting a bug.
------------------------------------------------------
Using winetricks 20240105 - sha256sum: dd9a0453769c7ca7198812373ecab6d1d2c561416eafba00026a487007f3039f with wine-9.0 (Ubuntu 9.0~repack-4build3) and WINEARCH=win64
winetricks GUI enabled, using zenity 4.0.2

```

I've not seen a problem like what you show though....I'm stumped

EDIT: I never did ask about this though:
```
 sudo apt list --installed|grep wine 

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

fonts-wine/plucky,plucky,now 9.0~repack-4build3 all [installed,automatic]
libwine/plucky,now 9.0~repack-4build3 amd64 [installed,automatic]
libwine/plucky,now 9.0~repack-4build3 i386 [installed,automatic]
wine-stable/plucky,plucky,now 3.0.1ubuntu1 all [installed]
wine32/plucky,now 9.0~repack-4build3 i386 [installed]
wine64/plucky,now 9.0~repack-4build3 amd64 [installed,automatic]
wine/plucky,plucky,now 9.0~repack-4build3 all [installed,automatic]
winetricks/plucky,plucky,now 20240105-3 all [installed]

```

---

### Post by agonzalesc on 2024-10-30
Hi
Thanks..

This is my output:

```
gonzalesc@puccohp:~/Descargas$ sudo apt list --installed|grep wine
[sudo] contraseña para gonzalesc: 

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

fonts-wine/noble,noble,now 9.0~repack-4build3 all [instalado, automático]
libkwineffects14/noble,now 4:5.27.11-0ubuntu3 amd64 [instalado, automático]
libwine/noble,now 9.0~repack-4build3 amd64 [instalado, automático]
wine-stable/noble,noble,now 3.0.1ubuntu1 all [instalado]
wine64/noble,now 9.0~repack-4build3 amd64 [instalado]
wine/noble,noble,now 9.0~repack-4build3 all [instalado, automático]
winetricks/noble,noble,now 20240105-2 all [instalado]
```


Regards

---

### Post by 1fallen on 2024-10-31
It looks to me that you not have enabled universe repo:
```
apt show wine32
Package: wine32:i386
Version: 9.0~repack-4build3
Priority: optional
Section: universe/otherosfs
Source: wine
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Wine Party <debian-wine@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 752 kB
Depends: libc6 (>= 2.38), libwine (= 9.0~repack-4build3)
Recommends: wine (= 9.0~repack-4build3)
Suggests: wine32-preloader (= 9.0~repack-4build3)
Homepage: https://www.winehq.org
Download-Size: 272 kB
APT-Manual-Installed: yes
APT-Sources: http://us.archive.ubuntu.com/ubuntu plucky/universe i386 Packages
Description: Windows API implementation - 32-bit binary loader
 Wine is a free MS-Windows API implementation.
 .
 This package provides the binary loader for 32-bit Windows applications.
```
[]/code]
```
sudo add-apt-repository universe
```
next run
```
sudo apt update
sudo apt upgrade
```
any better?

---

### Post by agonzalesc on 2024-11-01
Hi.
Thanks for the reply

Here mi output: 

```
gonzalesc@puccohp:~$ sudo add-apt-repository universe 
Añadiendo componente(s) «universe» a todos los repositorios.
Oprima [INTRO] para continuar o Ctrl+c para cancelar.
Obj:1 https://download.docker.com/linux/ubuntu focal InRelease
Obj:2 https://download.docker.com/linux/ubuntu jammy InRelease                                         
Obj:3 http://archive.ubuntu.com/ubuntu noble InRelease                                                 
Obj:4 http://security.ubuntu.com/ubuntu noble-security InRelease
Obj:5 http://archive.ubuntu.com/ubuntu noble-updates InRelease
Obj:6 http://archive.ubuntu.com/ubuntu noble-backports InRelease
Leyendo lista de paquetes... Hecho
```

After, I did the **update** and **upgrade** , and when I do **wine32** is the same result:

```
gonzalesc@puccohp:~$ sudo apt show wine32
Package: wine32:i386
Version: 9.0~repack-4build3
Priority: optional
Section: universe/otherosfs
Source: wine
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Wine Party <debian-wine@lists.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 752 kB
Depends: libc6 (>= 2.38), libwine (= 9.0~repack-4build3)
Recommends: wine (= 9.0~repack-4build3)
Suggests: wine32-preloader (= 9.0~repack-4build3)
Homepage: https://www.winehq.org
Download-Size: 272 kB
APT-Sources: http://archive.ubuntu.com/ubuntu noble/universe i386 Packages
Description: Windows API implementation - 32-bit binary loader
 Wine is a free MS-Windows API implementation.
 .
 This package provides the binary loader for 32-bit Windows applications.

gonzalesc@puccohp:~$ wine32
wine32: no se encontró la orden
```




```
gonzalesc@puccohp:~$ sudo apt install wine32:i386
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
Leyendo la información de estado... Hecho
Los paquetes indicados a continuación se instalaron de forma automática y ya no son necesarios.
  accountsservice-ubuntu-schemas activity-log-manager aha apg apt-config-icons-large apt-config-icons-large-hidpi bamfdaemon
  breeze-cursor-theme breeze-gtk-theme bup bup-doc ca-certificates-java catdoc cheese-common clinfo colord-data cryfs
  default-jdk-headless default-jre-headless docbook-xml docbook-xsl doomsday-data endeavour-common evemu-tools evince-common
  evolution-data-server-common evtest fluid-soundfont-gm folks-common fonts-dejavu-extra fonts-hack fonts-noto-hinted fonts-noto-ui-core
  fonts-noto-unhinted fuseiso gir1.2-accountsservice-1.0 gir1.2-atspi-2.0 gir1.2-camel-1.2 gir1.2-ebookcontacts-1.2
  gir1.2-edataserver-1.2 gir1.2-folks-0.7 gir1.2-gck-2 gir1.2-gcr-4 gir1.2-gdata-0.0 gir1.2-gdm-1.0 gir1.2-gee-0.8 gir1.2-geoclue-2.0
  gir1.2-gnomeautoar-0.1 gir1.2-gnomebg-4.0 gir1.2-gnomebluetooth-3.0 gir1.2-gnomedesktop-3.0 gir1.2-goa-1.0 gir1.2-gpaste-2
  gir1.2-gsound-1.0 gir1.2-gstreamer-1.0 gir1.2-gtop-2.0 gir1.2-gweather-4.0 gir1.2-javascriptcoregtk-4.1 gir1.2-javascriptcoregtk-6.0
  gir1.2-json-1.0 gir1.2-nautilus-4.0 gir1.2-nm-1.0 gir1.2-nma4-1.0 gir1.2-snapd-2 gir1.2-soup-2.4 gir1.2-soup-3.0
  gir1.2-telepathyglib-0.12 gir1.2-totemplparser-1.0 gir1.2-upowerglib-1.0 gkbd-capplet gnome-control-center-faces gnome-online-accounts
  gnome-screensaver gnome-session-common gpaste-2 grilo-plugins-0.3-base heif-gdk-pixbuf heif-thumbnailer hplip-data indicator-applet
  indicator-application indicator-appmenu indicator-common indicator-datetime indicator-keyboard indicator-messages indicator-power
  indicator-printers indicator-session indicator-sound java-common jayatana kactivities-bin kde-cli-tools-data kdoctools5 khotkeys-data
  kio-extras-data kirigami-addons-data kpackagetool5 ktexteditor-data kuserfeedback-doc kwayland-data kwin-data liba52-0.7.4 libaa1
  libaacs0 libabsl20210324 libabw-0.1-1 libaccounts-glib0 libaccounts-qt5-1 libappimage0 libappimage1.0abi1t64 libappstreamqt5-3
  libaribb24-0t64 libass9 libassimp5 libatk-bridge2.0-dev libatk1.0-dev libatkmm-1.6-dev libatspi2.0-dev libavc1394-0 libavif13 libavtp0
  libbamf3-2t64 libbdplus0 libblas3 libbluray2 libboost-chrono1.83.0t64 libboost-filesystem1.83.0 libboost-program-options1.83.0 libbs2b0
  libcaca0 libcairomm-1.0-dev libcamel-1.2-64t64 libcamera0.2 libcapi20-3t64 libcddb2 libcdio-cdda2t64 libcdio-paranoia2t64 libcdio19t64
  libcdparanoia0 libcdr-0.1-1 libchromaprint1 libcjson1 libcld2-0 libclutter-1.0-common libcodec2-1.2 libcogl-common libcolamd3
  libcolord-gtk4-1t64 libcolorhug2 libcpprest2.10 libcue2 libdatrie-dev libdav1d5 libdav1d7 libdbus-1-dev libdc1394-25 libdca0
  libdecor-0-0 libdecor-0-plugin-1-cairo libdeflate-dev libdmtx0t64 libdouble-conversion3 libdraco8 libdv4t64 libdvbpsi10 libdvdnav4
  libdvdread8t64 libe-book-0.1-1 libebackend-1.2-11t64 libebml5 libebook-1.2-21t64 libebook-contacts-1.2-4t64 libecal-2.0-3
  libedata-book-1.2-27t64 libedata-cal-2.0-2t64 libedataserver-1.2-27t64 libei1 libeis1 libepub0 libepubgen-0.1-1 libetonyek-0.1-1
  libevdocument3-4t64 libevemu3t64 libexiv2-27 libfaad2 libfakekey0 libfcitx-config4 libfcitx-gclient1 libfcitx-utils0 libflite1 libfmt9
  libfolks26 libfontconfig1-dev libfreehand-0.1-1 libfreerdp-server3-3 libfribidi-dev libfuse2t64 libgav1-0 libgdata-common libgdata22
  libgdk-pixbuf-2.0-dev libgdk-pixbuf-xlib-2.0-0 libgdk-pixbuf2.0-0 libgdm1 libgeonames-common libgeonames0 libgexiv2-2 libgfortran5
  libgit2-1.7 libgles1 libgles2 libglibmm-2.4-dev libglu1-mesa libglvnd-core-dev libglvnd0 libgme0 libgnome-autoar-0-0
  libgnome-bluetooth-ui-3.0-13 libgnome-panel3 libgnome-rr-4-2t64 libgnomekbd-common libgnomekbd8 libgoa-1.0-0b libgoa-1.0-common
  libgoa-backend-1.0-2 libgom-1.0-0t64 libgpaste-2-common libgpaste-2t64 libgphoto2-port12t64 libgpod-common libgpod4t64 libgps30t64
  libgrantlee-templates5 libgraphite2-dev libgrilo-0.3-0 libgsettings-qt1 libgsf-1-114 libgsf-1-common libgsm1 libgsound0t64
  libgssdp-1.6-0 libgtkspell3-3-0 libgupnp-1.6-0 libgupnp-av-1.0-3 libgupnp-igd-1.6-0 libgxps2t64 libharfbuzz-cairo0 libharfbuzz-dev
  libharfbuzz-subset0 libhfstospell11 libhpmud0 libhttp-parser2.9 libido3-0.1-0 libiec61883-0 libieee1284-3 libimagequant0
  libindicator3-7 libinstpatch-1.0-2 libixml11t64 libjack-jackd2-0 libjavascriptcoregtk-4.1-0 libjavascriptcoregtk-6.0-1 libjbig-dev
  libkate1 libkdsoap1 libkeybinder-3.0-0 libkf5activities5 libkf5activitiesstats1 libkf5archive-data libkf5archive5 libkf5attica5
  libkf5auth-data libkf5balooengine5 libkf5bluezqt-data libkf5bluezqt6 libkf5bookmarks-data libkf5calendarevents5 libkf5codecs-data
  libkf5codecs5 libkf5completion-data libkf5config-bin libkf5config-data libkf5configcore5 libkf5configqml5 libkf5configwidgets-data
  libkf5contacts-data libkf5coreaddons-data libkf5coreaddons5 libkf5dbusaddons-bin libkf5dbusaddons-data libkf5declarative-data
  libkf5dnssd-data libkf5dnssd5 libkf5doctools5 libkf5filemetadata-data libkf5filemetadata3 libkf5globalaccel-data libkf5guiaddons-data
  libkf5holidays-data libkf5holidays5 libkf5i18n-data libkf5i18n5 libkf5i18nlocaledata5 libkf5iconthemes-data libkf5itemmodels5
  libkf5itemviews-data libkf5jobwidgets-data libkf5js5t64 libkf5kcmutils-data libkf5kdelibs4support-data libkf5khtml-data libkf5kiontlm5
  libkf5modemmanagerqt6 libkf5networkmanagerqt6 libkf5newstuff-data libkf5notifications-data libkf5notifyconfig-data libkf5package-data
  libkf5package5 libkf5parts-data libkf5people-data libkf5peoplebackend5 libkf5pty-data libkf5pty5 libkf5screen-data libkf5service-data
  libkf5solid5-data libkf5sonnet5-data libkf5sonnetcore5 libkf5su-bin libkf5su-data libkf5su5 libkf5syndication5abi1
  libkf5syntaxhighlighting-data libkf5sysguard-data libkf5textwidgets-data libkf5threadweaver5 libkf5wallet-data libkf5widgetsaddons-data
  libkf5windowsystem-data libkf5xmlgui-bin libkf5xmlgui-data libkfontinst5 libkpathsea6 libksgrd9 libksysguardsystemstats1
  libkuserfeedback-l10n liblapack3 liblerc-dev liblightdm-gobject-1-0 liblilv-0-0 liblirc-client0t64 liblrdf0 libltc11
  liblttng-ust-common1t64 liblttng-ust-ctl5t64 liblttng-ust1t64 liblua5.2-0 liblucene++0t64 liblzma-dev libmad0 libmanette-0.2-0
  libmarkdown2 libmatroska7 libmbedcrypto7t64 libmd4c0 libmediaart-2.0-0 libmessaging-menu0 libminizip1t64 libmjpegutils-2.1-0t64
  libmodplug1 libmpcdec6 libmpeg2-4 libmpeg2encpp-2.1-0t64 libmplex2-2.1-0t64 libmsgraph-0-1 libmspub-0.1-1 libmtp-common libmtp-runtime
  libmtp9t64 libmwaw-0.3-3 libmysofa1 libneon27t64 libnice10 libnorm1t64 libodbc2 libodfgen-0.1-1 libopenal-data libopenal1
  libopenconnect5 libopencore-amrnb0 libopencore-amrwb0 libopengl-dev libopengl0 libopenh264-7 libopenmpt-modplug1 libopenmpt0t64
  libopenni2-0 libopusfile0 liborc-0.4-0t64 liborcus-0.18-0 liborcus-parser-0.18-0 libpackagekitqt5-1 libpagemaker-0.0-0
  libpam-kwallet-common libpam-kwallet5 libpango1.0-dev libpangomm-1.4-dev libpciaccess-dev libpciaccess0 libpgm-5.3-0 libphonenumber8
  libphonon-l10n libplacebo338 libplasma-geolocation-interface5 libplymouth5 libpocketsphinx3 libpoppler-glib8t64 libpoppler118
  libportal-gtk3-1 libportal-gtk4-1 libportal1 libpowerdevilui5 libprotobuf-lite32t64 libprotobuf32t64 libproxy-tools libpskc0t64
  libqalculate-data libqalculate22t64 libqca-qt5-2 libqca-qt5-2-plugins libqt5concurrent5t64 libqt5core5t64 libqt5dbus5t64
  libqt5network5t64 libqt5positioning5 libqt5qml5 libqt5qmlmodels5 libqt5qmlworkerscript5 libqt5sensors5 libqt5sql5-sqlite libqt5sql5t64
  libqt5test5t64 libqt5texttospeech5 libqt5webchannel5 libqt5webengine-data libqt5xml5t64 librabbitmq4 libraqm0 librav1e0 libraw1394-11
  libreoffice-base-core libreoffice-uiconfig-calc libreoffice-uiconfig-draw libreoffice-uiconfig-impress libreoffice-uiconfig-math
  libreoffice-uiconfig-writer libresid-builder0c2a librest-1.0-0 librist4 librubberband2 librygel-core-2.8-0 librygel-db-2.8-0
  librygel-renderer-2.8-0 librygel-server-2.8-0 libsane-common libsane-hpaio libscim8v5 libserd-0-0 libsgutils2-1.46-2 libsharpyuv-dev
  libshine3 libshout3 libsidplay1v5 libsidplay2 libsigc++-2.0-dev libsignon-plugins-common1 libsignon-qt5-1 libsnapd-qt-2-1 libsnappy1v5
  libsndio7.0 libsnmp-base libsnmp40t64 libsord-0-0 libsoundtouch1 libsoup-2.4-1 libsoup-gnome-2.4-1 libsoup2.4-common libsoxr0
  libspandsp2t64 libspatialaudio0t64 libspdlog1.12 libspeex1 libsphinxbase3t64 libsquashfuse0 libsratom-0-0 libsrt1.5-gnutls libsrtp2-1
  libssh-gcrypt-4 libssh2-1t64 libstoken1t64 libsuitesparseconfig7 libsvtav1enc1d1 libsynctex2 libsysmetrics1 libtag1v5 libtag1v5-vanilla
  libtelepathy-glib0t64 libtext-engine-0.1-0 libthai-dev libtheora0 libtiff-dev libtiffxx6 libtimezonemap-data libtimezonemap1
  libtomcrypt1 libtommath1 libtotem-plparser-common libtotem-plparser18 libtracker-sparql-3.0-0 libtss2-tcti-libtpms0t64
  libtss2-tcti-spi-helper0t64 libtss2-tctildr0t64 libtwolame0 libudfread0 libunibreak5 libunity-control-center1 libunity-gtk2-parser0
  libunity-gtk3-parser0 libunity-settings-daemon1 libupnp17t64 libv4l-0t64 libv4lconvert0t64 libvdpau1 libvidstab1.1 libvisio-0.1-1
  libvisual-0.4-0 libvlc-bin libvlc5 libvlccore9 libvo-aacenc0 libvo-amrwbenc0 libvoikko1 libvpx9 libwavpack1 libwebp-dev libwebpdecoder3
  libwildmidi2 libwoff1 libwpd-0.10-10 libwpg-0.3-3 libwps-0.4-4 libwrap0 libx264-164 libx265-199 libxapian30 libxcb-cursor0
  libxcb-damage0 libxcb-dpms0 libxcb-dri2-0 libxcb-dri3-0 libxcb-glx0 libxcb-icccm4 libxcb-image0 libxcb-keysyms1 libxcb-present0
  libxcb-randr0 libxcb-record0 libxcb-render-util0 libxcb-res0 libxcb-sync1 libxcb-xinerama0 libxcb-xkb1 libxcb-xv0 libxcomposite-dev
  libxcursor-dev libxcvt0 libxdamage-dev libxdgutilsbasedir1.0.1 libxdgutilsdesktopentry1.0.1 libxfixes-dev libxfont2 libxft-dev
  libxi-dev libxinerama-dev libxkbcommon-x11-0 libxklavier16 libxmlsec1t64-openssl libxrandr-dev libxshmfence1 libxt-dev libxtst-dev
  libxv1 libxvidcore4 libxvmc1 libxxf86dga1 libyuv0 libzbar0t64 libzeitgeist-2.0-0 libzimg2 libzix-0-0 libzlcore-data libzlcore0.13t64
  libzltext-data libzltext0.13t64 libzmq5 libzstd-dev libzvbi0t64 libzxing3 lp-solve media-player-info mobile-broadband-provider-info
  mutter-common-bin nautilus-data network-manager-gnome openjdk-11-jre-headless openjdk-21-jdk-headless openjdk-21-jre-headless
  oxygen-sounds pango1.0-tools phonon-backend-vlc-common plasma-desktop-data plasma-discover-common plasma-workspace-data
  pocketsphinx-en-us poedit-common policykit-1-gnome power-profiles-daemon powerdevil-data printer-driver-hpcups
  printer-driver-postscript-hp python3-brlapi python3-click python3-colorama python3-dateutil python3-freetype python3-fuse python3-louis
  python3-nautilus python3-olefile python3-pil python3-pylibacl python3-pyqt5.sip python3-pyxattr python3-reportlab python3-rlpycairo
  python3-speechd python3-tornado python3-xkit qdbus-qt5 qml-module-gsettings1.0 qml-module-org-kde-bluezqt qml-module-org-kde-kholidays
  qml-module-org-kde-kitemmodels qml-module-qt-labs-folderlistmodel qml-module-qt-labs-qmlmodels qml-module-qt-labs-settings
  qml-module-qtqml qml-module-qtqml-models2 qtchooser qtspeech5-speechd-plugin qttranslations5-l10n rhythmbox-data sane-airscan sgml-data
  signon-plugin-oauth2 smartmontools socat sonnet-plugins sshfs switcheroo-control tecla timgm6mb-soundfont totem-common tracker
  ubuntu-advantage-desktop-daemon ubuntu-touch-sounds unity-gtk-module-common unity-gtk2-module unity-gtk3-module
  unity-settings-daemon-schemas vlc-data vulkan-tools wayland-protocols x11-apps x11-session-utils x11-xkb-utils xbitmaps xbrlapi xcvt
  xdg-dbus-proxy xfonts-base xfonts-scalable xinit xinput xserver-common xserver-xorg-legacy xsettingsd yelp-xsl zeitgeist-core
Utilice «sudo apt autoremove» para eliminarlos.
Se instalarán los siguientes paquetes adicionales:
  glib-networking:i386 gstreamer1.0-plugins-base:i386 gstreamer1.0-plugins-good:i386 gstreamer1.0-x:i386 i965-va-driver:i386
  intel-media-va-driver:i386 libaa1:i386 libaom3:i386 libapparmor1:i386 libaribb24-0t64:i386 libasound2-plugins:i386 libasound2t64:i386
  libasyncns0:i386 libatk-bridge2.0-0t64:i386 libatk1.0-0t64:i386 libatomic1:i386 libatspi2.0-0t64:i386 libavahi-client3:i386
  libavahi-common-data:i386 libavahi-common3:i386 libavc1394-0:i386 libavcodec-extra60:i386 libavutil58:i386 libbrotli1:i386 libbsd0:i386
  libcaca0:i386 libcairo-gobject2:i386 libcairo2:i386 libcapi20-3t64:i386 libcdparanoia0:i386 libcodec2-1.2:i386 libcolord2:i386
  libcups2t64:i386 libcurl3t64-gnutls:i386 libcurl4t64:i386 libdatrie1:i386 libdav1d7:i386 libdb5.3t64:i386 libdbus-1-3:i386
  libde265-0:i386 libdecor-0-0:i386 libdecor-0-plugin-1-gtk:i386 libdeflate0:i386 libdrm-amdgpu1:i386 libdrm-intel1:i386
  libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386 libduktape207:i386 libdv4t64:i386 libdw1t64:i386 libedit2:i386 libelf1t64:i386
  libepoxy0:i386 libexif12:i386 libexpat1:i386 libffi8:i386 libflac12t64:i386 libfontconfig1:i386 libfreetype6:i386 libfribidi0:i386
  libgbm1:i386 libgd3:i386 libgdk-pixbuf-2.0-0:i386 libgl1:i386 libgl1-mesa-dri:i386 libglapi-mesa:i386 libglib2.0-0t64:i386
  libglvnd0:i386 libglx-mesa0:i386 libglx0:i386 libgnutls30t64:i386 libgomp1:i386 libgphoto2-6t64:i386 libgphoto2-port12t64:i386
  libgraphite2-3:i386 libgsm1:i386 libgstreamer-plugins-base1.0-0:i386 libgstreamer-plugins-good1.0-0:i386 libgstreamer1.0-0:i386
  libgtk-3-0t64:i386 libgudev-1.0-0:i386 libharfbuzz0b:i386 libheif-plugin-aomdec:i386 libheif-plugin-aomenc:i386
  libheif-plugin-libde265:i386 libheif1:i386 libhogweed6t64:i386 libicu74:i386 libiec61883-0:i386 libigdgmm12:i386 libjack-jackd2-0:i386
  libjbig0:i386 libjpeg-turbo8:i386 libjpeg8:i386 liblcms2-2:i386 libldap2:i386 libllvm17t64:i386 libltdl7:i386 libmp3lame0:i386
  libmpg123-0t64:i386 libncurses6:i386 libnettle8t64:i386 libnghttp2-14:i386 libnuma1:i386 libodbc2:i386 libogg0:i386
  libopencore-amrnb0:i386 libopencore-amrwb0:i386 libopenjp2-7:i386 libopus0:i386 liborc-0.4-0t64:i386 libosmesa6:i386 libp11-kit0:i386
  libpango-1.0-0:i386 libpangocairo-1.0-0:i386 libpangoft2-1.0-0:i386 libpcap0.8t64:i386 libpciaccess0:i386 libpcsclite1:i386
  libpixman-1-0:i386 libpng16-16t64:i386 libproxy1v5:i386 libpsl5t64:i386 libpulse0:i386 libraw1394-11:i386 libreoffice-core-nogui
  librsvg2-2:i386 librsvg2-common:i386 librtmp1:i386 libsamplerate0:i386 libsasl2-2:i386 libsasl2-modules:i386 libsasl2-modules-db:i386
  libsdl2-2.0-0:i386 libsensors5:i386 libsharpyuv0:i386 libshine3:i386 libshout3:i386 libslang2:i386 libsnappy1v5:i386 libsndfile1:i386
  libsoup-3.0-0:i386 libsoxr0:i386 libspeex1:i386 libspeexdsp1:i386 libsqlite3-0:i386 libssh-4:i386 libstdc++6:i386 libsvtav1enc1d1:i386
  libswresample4:i386 libtag1v5:i386 libtag1v5-vanilla:i386 libtasn1-6:i386 libthai0:i386 libtheora0:i386 libtiff6:i386 libtwolame0:i386
  libunwind8:i386 libusb-1.0-0:i386 libv4l-0t64:i386 libv4lconvert0t64:i386 libva-drm2:i386 libva-x11-2:i386 libva2:i386 libvdpau1:i386
  libvisual-0.4-0:i386 libvo-amrwbenc0:i386 libvorbis0a:i386 libvorbisenc2:i386 libvpx9:i386 libvulkan1:i386 libwavpack1:i386
  libwayland-client0:i386 libwayland-cursor0:i386 libwayland-egl1:i386 libwayland-server0:i386 libwebp7:i386 libwebpmux3:i386
  libwine:i386 libx11-6:i386 libx11-xcb1:i386 libx264-164:i386 libx265-199:i386 libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386
  libxcb-glx0:i386 libxcb-present0:i386 libxcb-randr0:i386 libxcb-render0:i386 libxcb-shm0:i386 libxcb-sync1:i386 libxcb-xfixes0:i386
  libxcb1:i386 libxcomposite1:i386 libxcursor1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxi6:i386
  libxinerama1:i386 libxkbcommon0:i386 libxkbregistry0:i386 libxml2:i386 libxpm4:i386 libxrandr2:i386 libxrender1:i386 libxshmfence1:i386
  libxss1:i386 libxtst6:i386 libxv1:i386 libxvidcore4:i386 libxxf86vm1:i386 libzvbi0t64:i386 mesa-va-drivers:i386
  mesa-vulkan-drivers:i386 ocl-icd-libopencl1:i386 pipewire-alsa pipewire-audio va-driver-all:i386
Paquetes sugeridos:
  gvfs:i386 i965-va-driver-shaders:i386 libcuda1:i386 libnvcuvid1:i386 libnvidia-encode1:i386 colord:i386 libdv-bin:i386 oss-compat:i386
  libgd-tools:i386 low-memory-monitor:i386 gnutls-bin:i386 gphoto2:i386 libvisual-0.4-plugins:i386 gstreamer1.0-tools:i386
  libheif-plugin-x265:i386 libheif-plugin-ffmpegdec:i386 libheif-plugin-jpegdec:i386 libheif-plugin-jpegenc:i386
  libheif-plugin-j2kdec:i386 libheif-plugin-j2kenc:i386 libheif-plugin-rav1e:i386 libheif-plugin-svtenc:i386 jackd2:i386
  odbc-postgresql:i386 tdsodbc:i386 opus-tools:i386 pcscd:i386 pulseaudio:i386 libraw1394-doc:i386 librsvg2-bin:i386
  libsasl2-modules-gssapi-mit:i386 | libsasl2-modules-gssapi-heimdal:i386 libsasl2-modules-ldap:i386 libsasl2-modules-otp:i386
  libsasl2-modules-sql:i386 lm-sensors:i386 speex:i386 gstreamer1.0-libav:i386 gstreamer1.0-plugins-bad:i386
  gstreamer1.0-plugins-ugly:i386 opencl-icd:i386 wine32-preloader:i386
Paquetes recomendados:
  libgl1-amber-dri:i386 vdpau-driver-all:i386 | vdpau-driver:i386
Los siguientes paquetes se ELIMINARÁN:
  appimagelauncher bluedevil breeze cheese chrome-gnome-shell code colord default-jdk default-jre doomsday doomsday-common drkonqi
  endeavour evince evolution-data-server fbreader ffmpeg frameworkintegration freedoom gdm3 gir1.2-gst-plugins-base-1.0 gir1.2-mutter-14
  gir1.2-rb-3.0 gir1.2-totem-1.0 gir1.2-webkit-6.0 gir1.2-webkit2-4.1 gitkraken gnome-browser-connector gnome-calendar
  gnome-color-manager gnome-control-center gnome-initial-setup gnome-remote-desktop gnome-session-bin gnome-shell
  gnome-shell-extension-appindicator gnome-shell-extension-desktop-icons-ng gnome-shell-extension-gpaste gnome-shell-extension-gsconnect
  gnome-shell-extension-gsconnect-browsers gnome-shell-extension-manager gnome-shell-extension-prefs gnome-shell-extension-ubuntu-dock
  gnome-shell-extension-ubuntu-tiling-assistant gnome-shell-extensions gnome-snapshot gnome-startup-applications gnome-todo
  gnome-user-docs gnome-user-docs-es gnome-video-effects google-chrome-stable gstreamer1.0-alsa gstreamer1.0-clutter-3.0 gstreamer1.0-gl
  gstreamer1.0-gtk3 gstreamer1.0-libav gstreamer1.0-libcamera gstreamer1.0-pipewire gstreamer1.0-plugins-bad gstreamer1.0-plugins-base
  gstreamer1.0-plugins-base-apps gstreamer1.0-plugins-good gstreamer1.0-plugins-ugly gstreamer1.0-pulseaudio gstreamer1.0-vaapi
  gstreamer1.0-x gvfs-backends hplip i965-va-driver-shaders indicator-bluetooth joystick kaccounts-providers kactivitymanagerd
  kde-cli-tools kde-config-gtk-style kde-config-screenlocker kde-config-sddm kde-config-updates kde-style-breeze kde-style-oxygen-qt5
  kdeconnect kded5 keditbookmarks kgamma5 khelpcenter khotkeys kinfocenter kinit kio kio-extras kio-fuse kmenuedit kpackagelauncherqml
  kpeople-vcard kscreen ksshaskpass ksystemstats ktexteditor-katepart kup-backup kwayland-integration kwin-common kwin-style-breeze
  kwin-x11 kwrited layer-shell-qt libasound2-plugins libatk-wrapper-java libatk-wrapper-java-jni libavcodec-extra libavcodec-extra60
  libavdevice60 libavfilter9 libavformat60 libavutil58 libcheese-gtk25 libcheese8 libclutter-1.0-0 libclutter-gst-3.0-0
  libclutter-gtk-1.0-0 libcogl-pango20 libcogl-path20 libcogl20 libcolorcorrect5 libdbusmenu-qt5-2 libdirectfb-1.7-7t64
  libdmapsharing-4.0-3t64 libdrm-amdgpu1 libdrm-dev libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdrm2 libedataserverui-1.2-4t64
  libedataserverui4-1.0-0t64 libegl-dev libegl-mesa0 libegl1 libegl1-mesa-dev libepoxy-dev libevview3-3t64 libfluidsynth3 libfolks-eds26
  libgbm-dev libgbm1 libgd3 libgl-dev libgl1 libgl1-amber-dri libgl1-mesa-dri libglapi-mesa libgles-dev libgles2-mesa-dev libglvnd-dev
  libglx-dev libglx-mesa0 libglx0 libgphoto2-6t64 libgstreamer-gl1.0-0 libgstreamer-plugins-bad1.0-0 libgstreamer-plugins-base1.0-0
  libgstreamer-plugins-good1.0-0 libgtk-3-dev libgtk-4-media-gstreamer libgtkmm-3.0-dev libgupnp-dlna-2.0-4 libkaccounts2
  libkdecorations2-5v5 libkdecorations2private10 libkf5auth5 libkf5authcore5 libkf5baloo5 libkf5bookmarks5 libkf5completion5
  libkf5configgui5 libkf5configwidgets5 libkf5contacts5 libkf5crash5 libkf5dbusaddons5 libkf5declarative5 libkf5filemetadata-bin
  libkf5globalaccel-bin libkf5globalaccel5 libkf5globalaccelprivate5 libkf5guiaddons-bin libkf5guiaddons5 libkf5iconthemes-bin
  libkf5iconthemes5 libkf5idletime5 libkf5itemviews5 libkf5jobwidgets5 libkf5kcmutils5 libkf5kcmutilscore5 libkf5kdelibs4support5
  libkf5kdelibs4support5-bin libkf5kexiv2-15.0.0 libkf5khtml-bin libkf5khtml5 libkf5kiocore5 libkf5kiofilewidgets5 libkf5kiogui5
  libkf5kiowidgets5 libkf5kirigami2-5 libkf5newstuff5 libkf5newstuffcore5 libkf5newstuffwidgets5 libkf5notifications5 libkf5notifyconfig5
  libkf5parts-plugins libkf5parts5 libkf5people5 libkf5peoplewidgets5 libkf5plasma5 libkf5plasmaquick5 libkf5prison5 libkf5pulseaudioqt3
  libkf5purpose-bin libkf5purpose5 libkf5quickaddons5 libkf5runner5 libkf5screen-bin libkf5screen8 libkf5screendpms8 libkf5service-bin
  libkf5service5 libkf5solid5 libkf5sonnetui5 libkf5style5 libkf5syntaxhighlighting5 libkf5sysguard-bin libkf5texteditor-bin
  libkf5texteditor5 libkf5textwidgets5 libkf5wallet-bin libkf5wallet5 libkf5waylandclient5 libkf5widgetsaddons5 libkf5windowsystem5
  libkf5xmlgui5 libkfontinstui5 libkpipewire5 libkpipewiredmabuf5 libkpipewirerecord5 libkpmcore12 libkscreenlocker5
  libksysguardformatter1 libksysguardsensorfaces1 libksysguardsensors1 libkuserfeedbackcore1 libkwalletbackend5-5 libkwineffects14
  libkwinglutils14 libkworkspace5-5 liblayershellqtinterface5 libmutter-14-0 libnotificationmanager1 libosmesa6 liboxygenstyle5-5
  liboxygenstyleconfig5-5 libphonon4qt5-4t64 libpolkit-qt5-1-1 libpoppler-qt5-1 libpostproc57 libpowerdevilcore2 libprocesscore9
  libprocessui9 libqaccessibilityclient-qt5-0 libqmobipocket2 libqt5designer5 libqt5gui5t64 libqt5help5 libqt5hunspellinputmethod5
  libqt5multimedia5 libqt5multimedia5-plugins libqt5multimediagsttools5 libqt5multimediaquick5 libqt5multimediawidgets5
  libqt5printsupport5t64 libqt5quick5 libqt5quickcontrols2-5 libqt5quickparticles5 libqt5quickshapes5 libqt5quicktemplates2-5
  libqt5quickwidgets5 libqt5svg5 libqt5virtualkeyboard5 libqt5waylandclient5 libqt5waylandcompositor5 libqt5webengine5
  libqt5webenginecore5 libqt5webenginewidgets5 libqt5webview5 libqt5widgets5t64 libqt5x11extras5 libreoffice-calc libreoffice-core
  libreoffice-draw libreoffice-gnome libreoffice-gtk3 libreoffice-impress libreoffice-math libreoffice-ogltrans libreoffice-pdfimport
  libreoffice-writer librhythmbox-core10 libsane1 libsdl2-2.0-0 libsdl2-mixer-2.0-0 libspice-server1 libswresample4 libswscale7
  libtaskmanager6 libtotem0 libva-drm2 libva-wayland2 libva-x11-2 libvirglrenderer1 libvpl2 libweather-ion7 libwebkit2gtk-4.1-0
  libwebkitgtk-6.0-4 libwine libwxgtk-webview3.2-1t64 libxatracker2 libyelp0 lightdm mesa-utils mesa-utils-bin mesa-va-drivers
  mesa-vdpau-drivers mesa-vulkan-drivers milou minecraft-launcher nautilus nautilus-share openjdk-11-jre openjdk-21-jdk openjdk-21-jre
  orca partitionmanager peek phonon4qt5 phonon4qt5-backend-vlc php8.2-gd plasma-browser-integration plasma-desktop plasma-discover
  plasma-discover-backend-fwupd plasma-discover-backend-snap plasma-discover-notifier plasma-disks plasma-firewall plasma-framework
  plasma-integration plasma-nm plasma-pa plasma-systemmonitor plasma-thunderbolt plasma-vault plasma-workspace plymouth plymouth-label
  plymouth-theme-spinner plymouth-theme-ubuntu-text poedit polkit-kde-agent-1 powerdevil pulseaudio pulseaudio-module-bluetooth
  pulseaudio-module-gsettings python3-pyqt5 qemu-system-gui qemu-system-modules-opengl qemu-system-modules-spice
  qml-module-org-kde-activities qml-module-org-kde-draganddrop qml-module-org-kde-kcm qml-module-org-kde-kcmutils
  qml-module-org-kde-kconfig qml-module-org-kde-kcoreaddons qml-module-org-kde-kio qml-module-org-kde-kirigami-addons-labs-mobileform
  qml-module-org-kde-kirigami2 qml-module-org-kde-kquickcontrols qml-module-org-kde-kquickcontrolsaddons qml-module-org-kde-ksysguard
  qml-module-org-kde-kwindowsystem qml-module-org-kde-newstuff qml-module-org-kde-people qml-module-org-kde-pipewire
  qml-module-org-kde-prison qml-module-org-kde-purpose qml-module-org-kde-qqc2desktopstyle qml-module-org-kde-quickcharts
  qml-module-org-kde-runnermodel qml-module-org-kde-solid qml-module-org-kde-sonnet qml-module-org-kde-syntaxhighlighting
  qml-module-org-kde-userfeedback qml-module-qt-labs-platform qml-module-qtgraphicaleffects qml-module-qtmultimedia
  qml-module-qtquick-controls qml-module-qtquick-controls2 qml-module-qtquick-dialogs qml-module-qtquick-layouts
  qml-module-qtquick-particles2 qml-module-qtquick-privatewidgets qml-module-qtquick-shapes qml-module-qtquick-templates2
  qml-module-qtquick-virtualkeyboard qml-module-qtquick-window2 qml-module-qtquick2 qml-module-qtwebengine qml-module-sso-onlineaccounts
  qml-module-ubuntu-onlineaccounts qt5-gtk-platformtheme qtvirtualkeyboard-plugin qtwayland5 redshift rhythmbox
  rhythmbox-plugin-alternative-toolbar rhythmbox-plugins rygel sane-utils shotwell simple-scan software-properties-gtk spice-vdagent
  systemsettings totem totem-plugins tracker-extract tracker-miner-fs ubuntu-desktop ubuntu-desktop-minimal ubuntu-docs
  ubuntu-drivers-common ubuntu-release-upgrader-gtk ubuntu-session unity-control-center unity-greeter unity-settings-daemon
  update-manager update-notifier vdpau-driver-all vlc-plugin-base vlc-plugin-video-output wayland-utils wine64 x11-utils
  xdg-desktop-portal-kde xorg xserver-xorg xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-libinput xserver-xorg-input-wacom
  xserver-xorg-video-all xserver-xorg-video-amdgpu xserver-xorg-video-ati xserver-xorg-video-fbdev xserver-xorg-video-intel
  xserver-xorg-video-nouveau xserver-xorg-video-qxl xserver-xorg-video-radeon xserver-xorg-video-vesa xserver-xorg-video-vmware xwayland
  yelp
Se instalarán los siguientes paquetes NUEVOS:
  glib-networking:i386 gstreamer1.0-plugins-base:i386 gstreamer1.0-plugins-good:i386 gstreamer1.0-x:i386 i965-va-driver:i386
  intel-media-va-driver:i386 libaa1:i386 libaom3:i386 libapparmor1:i386 libaribb24-0t64:i386 libasound2-plugins:i386 libasound2t64:i386
  libasyncns0:i386 libatk-bridge2.0-0t64:i386 libatk1.0-0t64:i386 libatomic1:i386 libatspi2.0-0t64:i386 libavahi-client3:i386
  libavahi-common-data:i386 libavahi-common3:i386 libavc1394-0:i386 libavcodec-extra60:i386 libavutil58:i386 libbrotli1:i386 libbsd0:i386
  libcaca0:i386 libcairo-gobject2:i386 libcairo2:i386 libcapi20-3t64:i386 libcdparanoia0:i386 libcodec2-1.2:i386 libcolord2:i386
  libcups2t64:i386 libcurl3t64-gnutls:i386 libcurl4t64:i386 libdatrie1:i386 libdav1d7:i386 libdb5.3t64:i386 libdbus-1-3:i386
  libde265-0:i386 libdecor-0-0:i386 libdecor-0-plugin-1-gtk:i386 libdeflate0:i386 libdrm-amdgpu1:i386 libdrm-intel1:i386
  libdrm-nouveau2:i386 libdrm-radeon1:i386 libdrm2:i386 libduktape207:i386 libdv4t64:i386 libdw1t64:i386 libedit2:i386 libelf1t64:i386
  libepoxy0:i386 libexif12:i386 libexpat1:i386 libffi8:i386 libflac12t64:i386 libfontconfig1:i386 libfreetype6:i386 libfribidi0:i386
  libgbm1:i386 libgd3:i386 libgdk-pixbuf-2.0-0:i386 libgl1:i386 libgl1-mesa-dri:i386 libglapi-mesa:i386 libglib2.0-0t64:i386
  libglvnd0:i386 libglx-mesa0:i386 libglx0:i386 libgnutls30t64:i386 libgomp1:i386 libgphoto2-6t64:i386 libgphoto2-port12t64:i386
  libgraphite2-3:i386 libgsm1:i386 libgstreamer-plugins-base1.0-0:i386 libgstreamer-plugins-good1.0-0:i386 libgstreamer1.0-0:i386
  libgtk-3-0t64:i386 libgudev-1.0-0:i386 libharfbuzz0b:i386 libheif-plugin-aomdec:i386 libheif-plugin-aomenc:i386
  libheif-plugin-libde265:i386 libheif1:i386 libhogweed6t64:i386 libicu74:i386 libiec61883-0:i386 libigdgmm12:i386 libjack-jackd2-0:i386
  libjbig0:i386 libjpeg-turbo8:i386 libjpeg8:i386 liblcms2-2:i386 libldap2:i386 libllvm17t64:i386 libltdl7:i386 libmp3lame0:i386
  libmpg123-0t64:i386 libncurses6:i386 libnettle8t64:i386 libnghttp2-14:i386 libnuma1:i386 libodbc2:i386 libogg0:i386
  libopencore-amrnb0:i386 libopencore-amrwb0:i386 libopenjp2-7:i386 libopus0:i386 liborc-0.4-0t64:i386 libosmesa6:i386 libp11-kit0:i386
  libpango-1.0-0:i386 libpangocairo-1.0-0:i386 libpangoft2-1.0-0:i386 libpcap0.8t64:i386 libpciaccess0:i386 libpcsclite1:i386
  libpixman-1-0:i386 libpng16-16t64:i386 libproxy1v5:i386 libpsl5t64:i386 libpulse0:i386 libraw1394-11:i386 libreoffice-core-nogui
  librsvg2-2:i386 librsvg2-common:i386 librtmp1:i386 libsamplerate0:i386 libsasl2-2:i386 libsasl2-modules:i386 libsasl2-modules-db:i386
  libsdl2-2.0-0:i386 libsensors5:i386 libsharpyuv0:i386 libshine3:i386 libshout3:i386 libslang2:i386 libsnappy1v5:i386 libsndfile1:i386
  libsoup-3.0-0:i386 libsoxr0:i386 libspeex1:i386 libspeexdsp1:i386 libsqlite3-0:i386 libssh-4:i386 libstdc++6:i386 libsvtav1enc1d1:i386
  libswresample4:i386 libtag1v5:i386 libtag1v5-vanilla:i386 libtasn1-6:i386 libthai0:i386 libtheora0:i386 libtiff6:i386 libtwolame0:i386
  libunwind8:i386 libusb-1.0-0:i386 libv4l-0t64:i386 libv4lconvert0t64:i386 libva-drm2:i386 libva-x11-2:i386 libva2:i386 libvdpau1:i386
  libvisual-0.4-0:i386 libvo-amrwbenc0:i386 libvorbis0a:i386 libvorbisenc2:i386 libvpx9:i386 libvulkan1:i386 libwavpack1:i386
  libwayland-client0:i386 libwayland-cursor0:i386 libwayland-egl1:i386 libwayland-server0:i386 libwebp7:i386 libwebpmux3:i386
  libwine:i386 libx11-6:i386 libx11-xcb1:i386 libx264-164:i386 libx265-199:i386 libxau6:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386
  libxcb-glx0:i386 libxcb-present0:i386 libxcb-randr0:i386 libxcb-render0:i386 libxcb-shm0:i386 libxcb-sync1:i386 libxcb-xfixes0:i386
  libxcb1:i386 libxcomposite1:i386 libxcursor1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxi6:i386
  libxinerama1:i386 libxkbcommon0:i386 libxkbregistry0:i386 libxml2:i386 libxpm4:i386 libxrandr2:i386 libxrender1:i386 libxshmfence1:i386
  libxss1:i386 libxtst6:i386 libxv1:i386 libxvidcore4:i386 libxxf86vm1:i386 libzvbi0t64:i386 mesa-va-drivers:i386
  mesa-vulkan-drivers:i386 ocl-icd-libopencl1:i386 pipewire-alsa pipewire-audio va-driver-all:i386 wine32:i386
0 actualizados, 223 nuevos se instalarán, 470 para eliminar y 0 no actualizados.
Se necesita descargar 272 MB de archivos.
Se liberarán 2.361 MB después de esta operación.
¿Desea continuar? [S/n]
```


Regards

---

### Post by 1fallen on 2024-11-01
There no need to install " wine32:i38" it comes in with winetricks.
Your sources are interesting though, when the last time you cleaned them up and out?
ie: you have two for Docker:
```
https://download.docker.com/linux/ubuntu focal InReleaseObj:
2 https://download.docker.com/linux/ubuntu jammy InRelease          
```
Did you ever install "winetricks"?

---

### Post by Tadaen_Sylvermane on 2024-11-01
I'd like to see your entire sources.list + whatever is in /etc/apt/sources.list.d. This type of thing tends to happen when people add random repos quite often from what I've seen. You could have created a Frankenbuntu where you are hopelessly stuck in a mess of wrong packages.

---

### Post by agonzalesc on 2024-11-03
@1fallen2 I removed the docker repositories because I didn't need then anymore.

Yes I installed winetrciks but the result is the same

```

gonzalesc@puccohp:~/Descargas$ winetricks 
Executing cd /usr/bin
------------------------------------------------------
warning: Unknown file arch of /usr/bin/wine.
------------------------------------------------------
```



@tadaen_sylvermane here mi sourcelist

```
gonzalesc@puccohp:~/Descargas$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 22.04 LTS _Jammy Jellyfish_ - Release amd64 (20220419)]/ jammy main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu noble main restricted
# deb-src http://ar.archive.ubuntu.com/ubuntu/ jammy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu noble-updates main restricted
# deb-src http://ar.archive.ubuntu.com/ubuntu/ jammy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu noble universe
# deb-src http://ar.archive.ubuntu.com/ubuntu/ jammy universe
deb http://archive.ubuntu.com/ubuntu noble-updates universe
# deb-src http://ar.archive.ubuntu.com/ubuntu/ jammy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu noble multiverse
# deb-src http://ar.archive.ubuntu.com/ubuntu/ jammy multiverse
deb http://archive.ubuntu.com/ubuntu noble-updates multiverse
# deb-src http://ar.archive.ubuntu.com/ubuntu/ jammy-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu noble-backports main restricted universe multiverse
# deb-src http://ar.archive.ubuntu.com/ubuntu/ jammy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu noble-security main restricted
# deb-src http://security.ubuntu.com/ubuntu jammy-security main restricted
deb http://security.ubuntu.com/ubuntu noble-security universe
# deb-src http://security.ubuntu.com/ubuntu jammy-security universe
deb http://security.ubuntu.com/ubuntu noble-security multiverse
# deb-src http://security.ubuntu.com/ubuntu jammy-security multiverse

# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end of the installation process.
# For information about how to configure apt package sources,
# see the sources.list(5) manual.
```


Regards

---

### Post by 1fallen on 2024-11-03
I was able to reproduce everything you have shown in your thread, but was fixed following this: [https://idroot.us/install-wine-ubuntu-24-04/](https://idroot.us/install-wine-ubuntu-24-04/)

NOTE: Please remove all wine installs first.
```
sudo apt list --installed|grep wine 

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

fonts-wine/noble,noble,now 9.0~repack-4build3 all [installed,automatic]
libwine/noble,now 9.0~repack-4build3 amd64 [installed]
libwine/noble,now 9.0~repack-4build3 i386 [installed,automatic]
q4wine/noble,now 1.3.13-1build2 amd64 [installed]
wine32/noble,now 9.0~repack-4build3 i386 [installed,automatic]
wine64/noble,now 9.0~repack-4build3 amd64 [installed,automatic]
wine/noble,noble,now 9.0~repack-4build3 all [installed,automatic]
winetricks/noble,noble,now 20240105-2 all [installed]
```

Following that link you will or might see "invalid key" just ignore and install fresh. (Stay within the Stable install)
EDIT: This is my installed packages just to help:
```
apt list --installed | grep wine

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

fonts-wine/noble,noble,now 9.0~repack-4build3 all [installed,automatic]
libwine/noble,now 9.0~repack-4build3 amd64 [installed]
libwine/noble,now 9.0~repack-4build3 i386 [installed,automatic]
q4wine/noble,now 1.3.13-1build2 amd64 [installed]
wine-stable/noble,noble,now 3.0.1ubuntu1 all [installed]
wine32/noble,now 9.0~repack-4build3 i386 [installed,automatic]
wine64/noble,now 9.0~repack-4build3 amd64 [installed,automatic]
wine/noble,noble,now 9.0~repack-4build3 all [installed,automatic]
winetricks/noble,noble,now 20240105-2 all [installed]

```
After a good install that PPA can now be removed:
```
sudo rm -rf /etc/apt/sources.list.d/winehq-jammy.sources /etc/apt/sources.list.d/winehq-noble.sources

```
If you changed it to "noble" change the command accordingly.

---

### Post by agonzalesc on 2024-11-03
Hi.
Thanks for the help. I removed all the wine packages, but, after when I try install wine, this is the output:

```
gonzalesc@puccohp:~/Descargas$ sudo apt list --installed|grep wine 
WARNING: apt does not have a stable CLI interface. Use with caution in scripts.
```


```
gonzalesc@puccohp:~/Descargas$ sudo apt install wine
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias... Hecho
Leyendo la información de estado... Hecho
Los paquetes indicados a continuación se instalaron de forma automática y ya no son necesarios.
  libgdk-pixbuf-xlib-2.0-0 libgdk-pixbuf2.0-0 libpciaccess-dev
Utilice «sudo apt autoremove» para eliminarlos.
Se instalarán los siguientes paquetes adicionales:
  fonts-wine libcapi20-3t64 libodbc2 libwine libz-mingw-w64 wine64
Paquetes sugeridos:
  odbc-postgresql tdsodbc q4wine winbind winetricks playonlinux wine-binfmt dosbox exe-thumbnailer | kio-extras wine64-preloader
Paquetes recomendados:
  libosmesa6 wine32
Los siguientes paquetes se ELIMINARÁN:
  code gitkraken google-chrome-stable libdrm-dev libgbm-dev libgl1-amber-dri mesa-va-drivers mesa-vulkan-drivers minecraft-launcher
  php8.2-gd redshift
Se instalarán los siguientes paquetes NUEVOS:
  fonts-wine libcapi20-3t64 libodbc2 libwine libz-mingw-w64 wine wine64
0 actualizados, 7 nuevos se instalarán, 11 para eliminar y 0 no actualizados.
Se necesita descargar 106 MB de archivos.
Se liberarán 828 MB después de esta operación.
¿Desea continuar? [S/n] n
```


it says that some package will be remove like "gitkraken, Google, extension GD of PHP", and I always use those packages.

PD : Yes, I ran the **update** and **upgrade** previously

Regards

---

### Post by 1fallen on 2024-11-04
@agonzalesc have you ever used Wondershare in wine before?
Winehq folks tell me this won't run in wine, I showed them that I installed, but it is total crap on my machine.

I can help to install wine though, They are not happy with Canonical with changes made in 24.04 Noble....LOL
They have not updated any PPA's officially yet. And No time was given for that to happen....

Wonder Share was a bust for me, and my system is good as far as requirements needed.

I'm using a hackish method for the wine Install and I'm pleased with that much and runs most everything I throw at it, except Wondershare.
Just let me know if you want to proceed.
My install now looks like this:
```
apt list --installed | grep wine

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

fonts-wine/noble,noble,now 9.0~repack-4build3 all [installed]
libwine/noble,now 9.0~repack-4build3 amd64 [installed]
libwine/noble,now 9.0~repack-4build3 i386 [installed,auto-removable]
q4wine/noble,now 1.3.13-1build2 amd64 [installed]
wine-stable-amd64/jammy,now 9.0.0.0~jammy-1 amd64 [installed,automatic]
wine-stable-i386/jammy,now 9.0.0.0~jammy-1 i386 [installed,automatic]
wine-stable/jammy,now 9.0.0.0~jammy-1 amd64 [installed]
[COLOR=#FF0000]wine32/noble[/COLOR],now 9.0~repack-4build3 i386 [installed,auto-removable]
[COLOR=#FF0000]wine64/noble[/COLOR],now 9.0~repack-4build3 amd64 [installed,auto-removable]
[COLOR=#FF0000]winehq-stable/jammy[/COLOR],now 9.0.0.0~jammy-1 amd64 [installed]
[COLOR=#FF0000]winetricks/noble[/COLOR],noble,now 20240105-2 all [installed]

```

---

### Post by agonzalesc on 2024-11-04
Hi.

Yes, last year I was using Filmora on Ubuntu (not  Noble version), but I also needed to install other .exe packages.
Yes, I want to install Wine, it's strange everything that is happening in my package system.

Thank you for your time

---

### Post by 1fallen on 2024-11-04
> **agonzalesc said:**
> Hi.

Yes, last year I was using Filmora on Ubuntu (not  Noble version), but I also needed to install other .exe packages.
yes i found it needed to install a lot of them to install Filmora

You might need to go back to the previous version then, I'm guessing 22.04
> **agonzalesc said:**
> Yes, I want to install Wine, it's strange everything that is happening in my package system.

Thank you for your time
Strange Indeed, but I suggest then as I said is to revert to the Last know working Ubuntu install.

Or we can waste some time to see what I already know on 24.04. (Not what I would do though)
Your Choice. :)

---

### Post by 1fallen on 2024-11-04
I had to check, so I Booted to my trusty Arch system, and it works very nicely on that system.

This is definitionally a Noble Flaw/Bug

Nice little program.....;)

---

### Post by agonzalesc on 2024-11-25
Hi @1fallen thanks for the help

I finally managed to downgrade to Ubuntu 22.04 but I couldn't install Filmora because it gives me some errors and I understand that this is already another thread, so I have created a new one.
[https://ubuntuforums.org/showthread.php?t=2502692&p=14213745](https://ubuntuforums.org/showthread.php?t=2502692&p=14213745)


I thank you again for the help in this thread. I'm going to close this thread


Regards

---

### Post by 1fallen on 2024-11-25
I'll take a look in a bit, I need to finish something first.

Always happy to help.

---

