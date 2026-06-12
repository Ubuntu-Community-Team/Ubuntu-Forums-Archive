---
title: "'apt_get autoremove' wants to delete the whole OS"
date: 2015-03-03
forum: Installation &amp; Upgrades
---

### Post by J_Me on 2015-03-03
I was trying to remove a package that I installed and clean up kubuntu 14.04 and I'm wondering why 'sudo apt-get autoremove' will remove old kernels but 'apt-get autoremove' will remove the whole OS.
```
The following packages were automatically installed and are no longer required:
  audacity-data esound-common fonts-dejavu grhino-data kdegames-data
  libbonoboui2-common libgnomecanvas2-common libgnomeui-common
  libgoocanvas-common libgtop2-common libpthread-stubs0-dev
  libunity-scopes-json-def-desktop libwebkitgtk-3.0-common libx11-doc
  libzvbi-common mariadb-common psensor-common tesseract-ocr-eng
  tesseract-ocr-equ tesseract-ocr-osd tsconf ttf-dejavu ttf-dejavu-extra
  x11proto-composite-dev x11proto-core-dev x11proto-damage-dev
  x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev
  x11proto-render-dev x11proto-xext-dev x11proto-xinerama-dev
  xorg-sgml-doctools xtrans-dev yelp-xsl
Use 'apt-get autoremove' to remove them.
apt-get autoremove



The following packages will be REMOVED
  about-distro* accountsservice* acl* acpi-support* acpid* adduser*
  akonadi-backend-mysql* akonadi-server* akregator* alsa-base* alsa-utils*
  amarok* amarok-common* amarok-utils* anacron* ansible* apparmor* appmenu-qt*
  apport* apport-kde* apt* apt-file* apt-transport-https* apt-utils*
  apt-xapian-index* aptdaemon* apturl-common* apturl-kde* ardour3* ark*
  aspell* aspell-en* at-spi2-core* audacity* audiocd-kio* avahi-autoipd*
  avahi-daemon* baloo* base-files* base-passwd* bash* bash-completion* bc*
  bind9-host* binutils* bison* bluedevil* bluez* bluez-alsa* bluez-cups*
  bootchart* brasero* brasero-cdrkit* brasero-common* brltty*
  browser-plugin-gnash* bsdmainutils* bsdutils* build-essential*
  busybox-initramfs* bzip2* ca-certificates* ca-certificates-java* cabextract*
  cdparanoia* cdrdao* chromium-browser* chromium-browser-l10n*
  chromium-codecs-ffmpeg-extra* colord* colord-kde* command-not-found*
  console-setup* consolekit* coreutils* cpio* cpp* cpp-4.8* cpufreqd*
  cpufrequtils* cracklib-runtime* crda* cron* cryptsetup* cryptsetup-bin*
  cups* cups-browsed* cups-bsd* cups-client* cups-core-drivers* cups-daemon*
  cups-filters* cups-filters-core-drivers* cups-ppdc* curl* dash* dbus*
  dbus-x11* dc* dcfldd* dconf-gsettings-backend* dconf-service* debconf*
  debconf-i18n* debhelper* debianutils* default-jre* default-jre-headless*
  desktop-file-utils* dh-python* dialog* dictionaries-common* diffstat*
  diffutils* dkms* dmidecode* dmsetup* dnsmasq-base* dnsutils* docbook-xml*
  docbook-xsl* dolphin* dosfstools* dpkg* dpkg-dev* dragonplayer*
  dvd+rw-tools* dvdbackup* e2fslibs* e2fsprogs* ed* eject* enchant* ethtool*
  fakeroot* festival* festival-freebsoft-utils* festlex-cmu* festlex-poslex*
  festvox-kallpc16k* file* findutils* firefox* fontconfig* fontconfig-config*
  fonts-droid* fonts-kacst* fonts-kacst-one* fonts-nanum*
  fonts-sil-abyssinica* fonts-takao-pgothic* foomatic-db-compressed-ppds*
  foremost* freerdp-x11* freespacenotifier* friendly-recovery* ftp* fuse* g++*
  g++-4.8* gawk* gcc* gcc-4.8* gcc-4.8-base* gcc-4.9-base* gconf-service*
  gconf-service-backend* gconf2* gconf2-common* gcr* gdb* gddrescue* gdisk*
  genisoimage* gettext* gettext-base* ghostscript* ghostscript-x*
  gir1.2-appindicator3-0.1* gir1.2-atk-1.0* gir1.2-brasero-3.0*
  gir1.2-freedesktop* gir1.2-gdkpixbuf-2.0* gir1.2-glib-2.0* gir1.2-gtk-3.0*
  gir1.2-pango-1.0* gir1.2-soup-2.4* gir1.2-udisks-2.0* glib-networking*
  glib-networking-services* gnash* gnash-common* gnome-icon-theme*
  gnome-keyring* gnome-user-guide* gnuchess* gnuchess-book* gnugo* gnupg*
  gnupg-agent* gnupg2* goldendict* gpgsm* gpgv* grep* grhino* groff-base*
  growisofs* grub-common* grub-gfxpayload-lists* grub-pc* grub-pc-bin*
  grub2-common* gsettings-desktop-schemas* gstreamer0.10-nice*
  gstreamer0.10-plugins-bad* gstreamer0.10-plugins-base*
  gstreamer0.10-plugins-good* gstreamer0.10-pulseaudio* gstreamer0.10-qapt*
  gstreamer0.10-x* gstreamer1.0-libav* gstreamer1.0-plugins-bad*
  gstreamer1.0-plugins-bad-faad* gstreamer1.0-plugins-bad-videoparsers*
  gstreamer1.0-plugins-base* gstreamer1.0-plugins-good*
  gstreamer1.0-plugins-ugly* gstreamer1.0-pulseaudio* gstreamer1.0-x*
  gtk2-engines-oxygen* gtk3-engines-oxygen* gvfs* gvfs-common* gvfs-daemons*
  gvfs-libs* gwenview* gzip* handbrake-cli* hardening-includes* hddtemp*
  hdparm* hostname* hplip* hplip-data* htop* humanity-icon-theme*
  hunspell-en-us* hyphen-en-us* ibus-qt4* icedtea-7-jre-jamvm* icoutils*
  iftop* ifupdown* im-config* indicator-application* indicator-cpufreq* info*
  init-system-helpers* initramfs-tools* initramfs-tools-bin* initscripts*
  inputattach* insserv* install-info* intltool-debian* iotop* iperf* iproute*
  iproute2* iptables* iputils-arping* iputils-ping* iputils-tracepath*
  irqbalance* isc-dhcp-client* isc-dhcp-common* iw* jackd* jackd2*
  jackd2-firewire* jovie* k3b* k3b-i18n* kaccessible* kaddressbook* kamera*
  kate* katepart* kbd* kbreakout* kcalc* kde-baseapps-bin*
  kde-config-gtk-style* kde-config-pimactivity* kde-config-tablet*
  kde-config-telepathy-accounts* kde-config-whoopsie* kde-l10n-engb*
  kde-runtime* kde-runtime-data* kde-style-oxygen* kde-telepathy*
  kde-telepathy-approver* kde-telepathy-auth-handler*
  kde-telepathy-contact-list* kde-telepathy-declarative*
  kde-telepathy-desktop-applets* kde-telepathy-filetransfer-handler*
  kde-telepathy-integration-module* kde-telepathy-minimal*
  kde-telepathy-send-file* kde-telepathy-text-ui* kde-touchpad*
  kde-window-manager* kde-window-manager-common* kde-workspace*
  kde-workspace-bin* kde-workspace-kgreet-plugins* kde-zeroconf*
  kdegraphics-strigi-analyzer* kdelibs-bin* kdelibs5-data* kdelibs5-plugins*
  kdemultimedia-kio-plugins* kdenetwork-filesharing* kdepasswd*
  kdepim-kresources* kdepim-runtime* kdepimlibs-kio-plugins* kdesudo*
  kdoctools* kerneloops-daemon* keyboard-configuration* kfind* khelpcenter4*
  kinfocenter* kio-audiocd* kio-mtp* klipper* kmag* kmail* kmenuedit* kmix*
  kmod* kmousetool* kmouth* knights* knotes* konqueror* konqueror-nsplugins*
  konsole* kontact* korganizer* krdc* kscreen* ksnapshot* ksysguard*
  ksysguardd* ksystemlog* ktorrent* kubuntu-debug-installer* kubuntu-desktop*
  kubuntu-docs* kubuntu-driver-manager* kubuntu-notification-helper*
  kubuntu-settings-desktop* kubuntu-settings-netbook* kwalletmanager* lame*
  language-pack-en* language-pack-en-base* language-pack-gnome-en*
  language-pack-gnome-en-base* language-pack-kde-en* language-selector-common*
  laptop-detect* less* liba52-0.7.4* libaa1* libaacs0* libaccounts-glib0*
  libaccounts-qt1* libaccountsservice0* libacl1* libaio1*
  libakonadi-calendar4* libakonadi-contact4* libakonadi-kcal4*
  libakonadi-kde4* libakonadi-kmime4* libakonadi-notes4*
  libakonadi-socialutils4* libakonadiprotocolinternals1*
  libalgorithm-diff-perl* libalgorithm-diff-xs-perl* libalgorithm-merge-perl*
  libao4* libapparmor-perl* libapparmor1* libappindicator3-1* libapt-inst1.5*
  libapt-pkg-perl* libapt-pkg4.12* libarchive-extract-perl*
  libarchive-zip-perl* libarchive13* libart-2.0-2* libasan0*
  libasn1-8-heimdal* libasound2* libasound2-plugins* libaspell15*
  libasprintf-dev* libasprintf0c2* libass4* libassuan0* libasyncns0*
  libatasmart4* libatk-bridge2.0-0* libatk-bridge2.0-dev* libatk-wrapper-java*
  libatk-wrapper-java-jni* libatk1.0-0* libatk1.0-dev* libatkmm-1.6-1*
  libatomic1* libatspi2.0-0* libattica0.4* libattr1* libaubio4* libaudio2*
  libaudiofile1* libaudit1* libauthen-sasl-perl* libautodie-perl* libav-tools*
  libavahi-client3* libavahi-common3* libavahi-core7* libavahi-glib1*
  libavahi-gobject0* libavc1394-0* libavcodec54* libavdevice53* libavfilter3*
  libavformat54* libavresample1* libavutil52* libbaloocore4* libbaloofiles4*
  libbaloopim4* libbaloowidgets4* libbalooxapian4* libbasicusageenvironment0*
  libbind9-90* libblas3* libblkid1* libbluedevil1* libbluetooth3* libbluray1*
  libbonobo2-0* libbonoboui2-0* libboost-date-time1.54.0*
  libboost-iostreams1.54.0* libboost-program-options1.54.0*
  libboost-system1.54.0* libboost-thread1.54.0* libbrasero-media3-1*
  libbrasero-media3-dev* libbrlapi0.6* libbsd0* libburn4* libbz2-1.0*
  libc-bin* libc-dev-bin* libc6* libc6-dbg* libc6-dev* libcaca0*
  libcairo-gobject2* libcairo-script-interpreter2* libcairo2* libcairo2-dev*
  libcairomm-1.0-1* libcalendarsupport4* libcanberra-gtk3-0*
  libcanberra-gtk3-module* libcanberra-pulse* libcanberra0* libcap-ng0*
  libcap2* libcap2-bin* libcdaudio1* libcddb2* libcdio-cdda1*
  libcdio-paranoia1* libcdio13* libcdparanoia0* libcdr-0.0-0* libcgmanager0*
  libchm1* libchromaprint0* libck-connector0* libclass-accessor-perl* libcln6*
  libclone-perl* libcloog-isl4* libclucene-contribs1* libclucene-core1*
  libcmis-0.4-4* libcolamd2.8.0* libcolord1* libcolorhug1* libcomerr2*
  libconfig++9* libconfig-file-perl* libcpufreq0* libcrack2* libcroco3*
  libcrypt-passwdmd5-perl* libcryptsetup4* libcrystalhd3* libcups2*
  libcupscgi1* libcupsfilters1* libcupsimage2* libcupsmime1* libcupsppdc1*
  libcurl3* libcurl3-gnutls* libcwiid1* libdaemon0* libdatrie1* libdb5.3*
  libdbd-mysql-perl* libdbi-perl* libdbus-1-3* libdbus-glib-1-2*
  libdbusmenu-glib4* libdbusmenu-gtk3-4* libdbusmenu-gtk4* libdbusmenu-qt2*
  libdc1394-22* libdca0* libdconf1* libdebconf-kde0* libdebconfclient0*
  libdebian-installer4* libdee-1.0-4* libdevmapper-event1.02.1*
  libdevmapper1.02.1* libdigest-hmac-perl* libdirac-encoder0*
  libdirectfb-1.2-9* libdjvulibre21* libdlrestrictions1* libdmtx0a* libdns100*
  libdotconf0* libdpkg-perl* libdrm-intel1* libdrm-nouveau2* libdrm-radeon1*
  libdrm2* libdv4* libdvbpsi8* libdvdcss2* libdvdnav-dev* libdvdnav4*
  libdvdread-dev* libdvdread4* libebml4* libedit2* libegl1-mesa*
  libegl1-mesa-drivers* libelf1* libelfg0* libemail-valid-perl* libenca0*
  libenchant1c2a* libencode-locale-perl* libepub0* libesd0* libespeak1*
  libestools2.1* libestr0* libeventviews4* libexif12* libexiv2-12* libexpat1*
  libexpat1-dev* libexttextcat-2.0-0* libfaad2* libfakeroot*
  libfarstream-0.1-0* libffado2* libffi6* libfftw3-double3* libfftw3-single3*
  libfile-basedir-perl* libfile-copy-recursive-perl*
  libfile-desktopentry-perl* libfile-fcntllock-perl* libfile-listing-perl*
  libfile-mimeinfo-perl* libflac++6* libflac8* libflite1* libfluidsynth1*
  libfont-afm-perl* libfontconfig1* libfontconfig1-dev* libfontembed1*
  libfontenc1* libfreerdp-plugins-standard* libfreerdp1* libfreetype6*
  libfreetype6-dev* libfribidi0* libfs6* libfuse2* libgail18* libgbm1*
  libgcc-4.8-dev* libgcc1* libgck-1-0* libgconf-2-4* libgconf2-4*
  libgcr-base-3-1* libgcr-ui-3-1* libgcrypt11* libgd3* libgdbm3*
  libgdk-pixbuf2.0-0* libgdk-pixbuf2.0-dev* libgeoclue0* libgeoip1*
  libgettextpo-dev* libgettextpo0* libgif4* libgirepository-1.0-1*
  libgl1-mesa-dri* libgl1-mesa-glx* libglade2-0* libglamor0* libglapi-mesa*
  libgles2-mesa* libglib2.0-0* libglib2.0-bin* libglib2.0-dev*
  libglibmm-2.4-1c2a* libglu1-mesa* libgme0* libgmime-2.6-0* libgmp10*
  libgnome-keyring0* libgnome2-0* libgnome2-bin* libgnome2-common*
  libgnomecanvas2-0* libgnomecanvasmm-2.6-1c2a* libgnomeui-0* libgnomevfs2-0*
  libgnomevfs2-common* libgnutls-openssl27* libgnutls26* libgnutls28*
  libgomp1* libgoocanvas3* libgpg-error0* libgpgme++2* libgpgme11*
  libgphoto2-6* libgphoto2-port10* libgpm2* libgpod-common* libgpod4*
  libgps20* libgrantlee-core0* libgrantlee-gui0* libgraphite2-3*
  libgroupsock1* libgs9* libgsm1* libgsoap4* libgssapi-krb5-2*
  libgssapi3-heimdal* libgssdp-1.0-3* libgstreamer-plugins-bad0.10-0*
  libgstreamer-plugins-bad1.0-0* libgstreamer-plugins-base0.10-0*
  libgstreamer-plugins-base1.0-0* libgstreamer-plugins-good1.0-0*
  libgstreamer0.10-0* libgstreamer1.0-0* libgtk-3-0* libgtk-3-bin*
  libgtk-3-common* libgtk-3-dev* libgtk2.0-0* libgtk2.0-bin* libgtkglext1*
  libgtkmm-2.4-1c2a* libgtop2-7* libgudev-1.0-0* libgupnp-1.0-4*
  libgupnp-igd-1.0-4* libgusb2* libgutenprint2* libharfbuzz-dev*
  libharfbuzz-gobject0* libharfbuzz-icu0* libharfbuzz0b* libhcrypto4-heimdal*
  libheimbase1-heimdal* libheimntlm0-heimdal* libhogweed2* libhpmud0*
  libhtml-form-perl* libhtml-format-perl* libhtml-parser-perl*
  libhtml-tagset-perl* libhtml-template-perl* libhtml-tree-perl*
  libhttp-cookies-perl* libhttp-daemon-perl* libhttp-date-perl*
  libhttp-message-perl* libhttp-negotiate-perl* libhunspell-1.3-0*
  libhx509-5-heimdal* libhyphen0* libibus-1.0-5* libibus-qt1* libical1*
  libice-dev* libice6* libicu52* libid3tag0* libidl-common* libidl0* libidn11*
  libiec61883-0* libieee1284-3* libijs-0.35* libilmbase6* libimobiledevice4*
  libincidenceeditorsng4* libindicate-qt1* libindicate5* libindicator3-7*
  libio-html-perl* libio-pty-perl* libio-socket-inet6-perl*
  libio-socket-ssl-perl* libio-string-perl* libipc-run-perl*
  libipc-system-simple-perl* libisc95* libisccc90* libisccfg90* libisl10*
  libiso9660-8* libisofs6* libitm1* libiw30* libjack-jackd2-0* libjasper1*
  libjavascriptcoregtk-3.0-0* libjbig0* libjbig2dec0* libjemalloc1*
  libjpeg-turbo8* libjpeg8* libjson-c2* libjson0* libjte1* libk3b-dev*
  libk3b6* libk3b6-extracodecs* libk5crypto3* libkabc4* libkactivities-bin*
  libkactivities-models1* libkactivities6* libkalarmcal2* libkate1*
  libkateinterfaces4* libkatepartinterfaces4* libkblog4* libkcal4*
  libkcalcore4* libkcalutils4* libkcddb4* libkcmutils4* libkcompactdisc4*
  libkdcraw23* libkde3support4* libkdeclarative5* libkdecorations4abi1*
  libkdecore5* libkdegames6* libkdepim4* libkdepimdbusinterfaces4* libkdesu5*
  libkdeui5* libkdewebkit5* libkdgantt2-0* libkdnssd4* libkemoticons4*
  libkephal4abi1* libkexiv2-11* libkeyutils1* libkfile4* libkfilemetadata4*
  libkgapi2-2* libkholidays4* libkhtml5* libkidletime4* libkimap4* libkio5*
  libkipi11* libkjsapi4* libkjsembed4* libkldap4* libkleo4* libkmanagesieve4*
  libkmbox4* libkmediaplayer4* libkmime4* libkmod2* libknewstuff2-4*
  libknewstuff3-4* libknotifyconfig4* libkntlm4* libkolab0* libkolabxml1*
  libkonq-common* libkonq5abi1* libkonqsidebarplugin4a* libkontactinterface4*
  libkparts4* libkpeople3* libkpgp4* libkpimidentities4* libkpimtextedit4*
  libkpimutils4* libkprintutils4* libkpty4* libkrb5-26-heimdal* libkrb5-3*
  libkrb5support0* libkresources4* libkrosscore4* libksane0* libksba8*
  libkscreen1* libkscreensaver5* libksgrd4* libksieve4* libksieveui4*
  libksignalplotter4* libktexteditor4* libktnef4* libktorrent-l10n*
  libktorrent5* libktpcommoninternalsprivate7* libkubuntu0*
  libkunitconversion4* libkwineffects1abi4* libkwinglesutils1*
  libkwinglutils1abi3* libkworkspace4abi2* libkxmlrpcclient4* liblangtag1*
  liblastfm1* liblcms2-2* libldap-2.4-2* libldb1* liblept4*
  liblightdm-gobject-1-0* liblightdm-qt-3-0* liblilv-0-0* liblinear-tools*
  liblinear1* liblircclient0* liblist-moreutils-perl* liblivemedia23*
  libllvm3.4* liblo7* liblocale-gettext-perl* liblockfile-bin* liblockfile1*
  liblog-message-simple-perl* libloudmouth1-0* liblrdf0* libltdl7*
  liblua5.2-0* liblwp-mediatypes-perl* liblwp-protocol-https-perl* liblwres90*
  liblzma5* liblzo2-2* libmad0* libmagic1* libmail-sendmail-perl*
  libmailcommon4* libmailimporter4* libmailtools-perl* libmailtransport4*
  libmatroska6* libmbim-glib0* libmeanwhile1* libmessagecomposer4*
  libmessagecore4* libmessagelist4* libmessageviewer4* libmhash2*
  libmicroblog4* libmimic0* libmission-control-plugins0* libmkv0* libmm-glib0*
  libmms0* libmnl0* libmodemmanagerqt1* libmodplug1* libmodule-pluggable-perl*
  libmount1* libmp3lame0* libmpc3* libmpcdec6* libmpdec2* libmpeg2-4*
  libmpfr4* libmpg123-0* libmspub-0.0-0* libmtdev1* libmtp-runtime* libmtp9*
  libmuonprivate2* libmusicbrainz5-0* libmygpo-qt1* libmysqlclient18*
  libmythes-1.2-0* libnautilus-extension1a* libncurses5* libncursesw5*
  libneon27-gnutls* libnepomuk4* libnepomukcleaner4* libnepomukcore4abi1*
  libnepomukquery4a* libnepomukutils4* libnet-dns-perl*
  libnet-domain-tld-perl* libnet-http-perl* libnet-ip-perl*
  libnet-smtp-ssl-perl* libnet-ssleay-perl* libnetfilter-conntrack3*
  libnettle4* libnetworkmanagerqt1* libnewt0.52* libnfnetlink0* libnice10*
  libnih-dbus1* libnih1* libnl-3-200* libnl-genl-3-200* libnl-route-3-200*
  libnm-glib-vpn1* libnm-glib4* libnm-util2* libnoteshared4* libnotify4*
  libnspr4* libnspr4-0d* libnss-mdns* libnss3* libnss3-1d* libnss3-nssdb*
  libntdb1* libntrack-qt4-1* libntrack0* libnuma1* liboath0* libofa0* libogg0*
  libokularcore4* libopenal1* libopenconnect2* libopencore-amrnb0*
  libopencore-amrwb0* libopencv-calib3d2.4* libopencv-contrib2.4*
  libopencv-core2.4* libopencv-features2d2.4* libopencv-flann2.4*
  libopencv-highgui2.4* libopencv-imgproc2.4* libopencv-legacy2.4*
  libopencv-ml2.4* libopencv-objdetect2.4* libopencv-video2.4* libopenexr6*
  libopenjpeg2* libopenobex1* libopenvg1-mesa* libopus0* liborbit-2-0*
  liborbit2* liborc-0.4-0* liborcus-0.6-0* libp11-kit-gnome-keyring*
  libp11-kit0* libpam-cap* libpam-ck-connector* libpam-gnome-keyring*
  libpam-modules* libpam-modules-bin* libpam-runtime* libpam-systemd*
  libpam0g* libpango-1.0-0* libpango1.0-0* libpango1.0-dev*
  libpangocairo-1.0-0* libpangoft2-1.0-0* libpangomm-1.4-1* libpangox-1.0-0*
  libpangoxft-1.0-0* libpaper-utils* libpaper1* libparse-debianchangelog-perl*
  libparted0debian1* libpcap0.8* libpci3* libpciaccess0* libpcre3*
  libpcre3-dev* libpcrecpp0* libpcsclite1* libperl4-corelibs-perl*
  libperl5.18* libperlio-gzip-perl* libphonon4* libpimactivity4*
  libpimcommon4* libpipeline1* libpixman-1-0* libpixman-1-dev*
  libplasma-geolocation-interface4* libplasma3* libplasmaclock4abi4*
  libplasmagenericshell4* libplist1* libplymouth2* libpng12-0* libpng12-dev*
  libpod-latex-perl* libpolkit-agent-1-0* libpolkit-backend-1-0*
  libpolkit-gobject-1-0* libpolkit-qt-1-1* libpoppler-qt4-4* libpoppler44*
  libpopt0* libportaudio2* libportsmf0* libpostproc52* libpq5* libprison0*
  libprocesscore4abi1* libprocessui4a* libprocps3* libproxy-tools* libproxy1*
  libpth20* libpulse-mainloop-glib0* libpulse0* libpulsedsp* libpurple-bin*
  libpurple0* libpwquality1* libpython-stdlib* libpython2.7*
  libpython2.7-stdlib* libpython3-stdlib* libpython3.4* libpython3.4-minimal*
  libpython3.4-stdlib* libqaccessibilityclient0* libqalculate5* libqapt2*
  libqapt2-runtime* libqca2* libqca2-plugin-ossl* libqgpgme1* libqimageblitz4*
  libqjson0* libqmi-glib0* libqmobipocket1* libqoauth1* libqpdf13*
  libqrencode3* libqt4-dbus* libqt4-declarative* libqt4-designer* libqt4-help*
  libqt4-network* libqt4-opengl* libqt4-qt3support* libqt4-script*
  libqt4-scripttools* libqt4-sql* libqt4-sql-mysql* libqt4-sql-sqlite*
  libqt4-svg* libqt4-test* libqt4-xml* libqt4-xmlpatterns*
  libqtassistantclient4* libqtcore4* libqtdbus4* libqtglib-2.0-0* libqtgui4*
  libqtscript4-core* libqtscript4-gui* libqtscript4-network* libqtscript4-sql*
  libqtscript4-uitools* libqtscript4-xml* libqtwebkit4* libquadmath0*
  libraptor1* libraptor2-0* librasqal3* libraw1394-11* libraw9* librdf0*
  libreadline5* libreadline6* libregexp-assemble-perl* libreoffice-common*
  libreoffice-java-common* libresid-builder0c2a* libroken18-heimdal*
  librsvg2-2* librsvg2-common* librtmp0* libruby1.9.1* libsamplerate0*
  libsane* libsane-hpaio* libsasl2-2* libsasl2-modules* libsasl2-modules-db*
  libsbc1* libsbsms10* libschroedinger-1.0-0* libsdl-image1.2*
  libsdl1.2debian* libsecret-1-0* libselinux1* libsemanage1* libsendlater4*
  libsensors4* libsepol1* libserd-0-0* libsgutils2-2* libshout3* libsidplay1*
  libsidplay2* libsigc++-2.0-0c2a* libsignon-qt1* libsigsegv2* libslang2*
  libslv2-9* libsm-dev* libsm6* libsmbclient* libsndfile1* libsnmp30*
  libsocket6-perl* libsolid4* libsonic0* libsoprano4* libsord-0-0*
  libsoundtouch0* libsoup-gnome2.4-1* libsoup2.4-1* libsox-fmt-alsa*
  libsox-fmt-base* libsox2* libsoxr0* libspandsp2* libspectre1* libspeechd2*
  libspeex1* libspeexdsp1* libsqlite3-0* libsratom-0-0* libsrtp0* libss2*
  libssh-4* libssh2-1* libssl1.0.0* libstartup-notification0*
  libstdc++-4.8-dev* libstdc++6* libstreamanalyzer0* libstreams0*
  libsub-identify-perl* libsub-name-perl* libsuil-0-0* libsvga1* libswscale2*
  libsyndication4* libsys-hostname-long-perl* libsysfs2* libsystemd-daemon0*
  libsystemd-login0* libtag-extras1* libtag1-vanilla* libtag1c2a* libtalloc2*
  libtar0* libtaskmanager4abi5* libtasn1-6* libtbb2* libtcl8.6* libtdb1*
  libtelepathy-glib0* libtelepathy-logger-qt4-1* libtelepathy-logger3*
  libtelepathy-qt4-2* libtemplateparser4* libterm-readkey-perl*
  libterm-ui-perl* libtesseract3* libtevent0* libtext-charwidth-perl*
  libtext-iconv-perl* libtext-levenshtein-perl* libtext-soundex-perl*
  libtext-wrapi18n-perl* libthai0* libtheora0* libthreadweaver4* libtiff5*
  libtimedate-perl* libtinfo5* libtk8.6* libtotem-plparser18* libts-0.0-0*
  libtwolame0* libtxc-dxtn-s2tc0* libudev1* libudisks2-0* libunistring0*
  libunity-protocol-private0* libunity9* libupnp6* libupower-glib1*
  liburi-perl* libusageenvironment1* libusb-0.1-4* libusb-1.0-0* libusbmuxd2*
  libustr-1.0-1* libutempter0* libuuid1* libv4l-0* libv4lconvert0*
  libva-x11-1* libva1* libvamp-hostsdk3* libvcdinfo0* libvdpau1* libvirtodbc0*
  libvisio-0.0-0* libvisual-0.4-0* libvisual-0.4-plugins* libvlc5*
  libvlccore7* libvncserver0* libvo-aacenc0* libvo-amrwbenc0* libvorbis0a*
  libvorbisenc2* libvorbisfile3* libvpx1* libwavpack1* libwayland-client0*
  libwayland-cursor0* libwayland-dev* libwayland-egl1-mesa*
  libwayland-server0* libwbclient0* libweather-ion6* libwebkitgtk-3.0-0*
  libwebp5* libwebpmux1* libwhoopsie-preferences0* libwhoopsie0* libwildmidi1*
  libwind0-heimdal* libwpd-0.9-9* libwpg-0.2-2* libwps-0.2-2* libwrap0*
  libwww-perl* libwww-robotrules-perl* libwxbase2.8-0* libwxgtk2.8-0*
  libx11-6* libx11-dev* libx11-xcb1* libx264-142* libx86-1* libxapian22*
  libxatracker2* libxau-dev* libxau6* libxaw7* libxcb-composite0*
  libxcb-damage0* libxcb-dri2-0* libxcb-dri3-0* libxcb-glx0* libxcb-image0*
  libxcb-keysyms1* libxcb-present0* libxcb-randr0* libxcb-record0*
  libxcb-render0* libxcb-render0-dev* libxcb-shape0* libxcb-shm0*
  libxcb-shm0-dev* libxcb-sync1* libxcb-util0* libxcb-xfixes0* libxcb-xtest0*
  libxcb-xv0* libxcb1* libxcb1-dev* libxcomposite-dev* libxcomposite1*
  libxcursor-dev* libxcursor1* libxdamage-dev* libxdamage1* libxdmcp-dev*
  libxdmcp6* libxerces-c3.1* libxext-dev* libxext6* libxfixes-dev* libxfixes3*
  libxfont1* libxft-dev* libxft2* libxi-dev* libxi6* libxinerama-dev*
  libxinerama1* libxkbcommon-dev* libxkbcommon0* libxkbfile1* libxklavier16*
  libxml++2.6-2* libxml2* libxml2-utils* libxmu6* libxmuu1* libxp6* libxpm4*
  libxrandr-dev* libxrandr2* libxrender-dev* libxrender1* libxshmfence1*
  libxslt1.1* libxss1* libxt6* libxtables10* libxtst6* libxv1* libxvidcore4*
  libxvmc1* libxxf86dga1* libxxf86vm1* libyajl2* libyaml-0-2* libyelp0*
  libzbar0* libzephyr4* libzip2* libzvbi0* lightdm* lightdm-kde-greeter*
  lintian* linux-generic* linux-headers-3.13.0-36*
  linux-headers-3.13.0-36-generic* linux-headers-3.13.0-46*
  linux-headers-3.13.0-46-generic* linux-headers-generic*
  linux-image-3.13.0-24-generic* linux-image-3.13.0-34-generic*
  linux-image-3.13.0-36-generic* linux-image-3.13.0-46-generic*
  linux-image-extra-3.13.0-24-generic* linux-image-extra-3.13.0-34-generic*
  linux-image-extra-3.13.0-36-generic* linux-image-extra-3.13.0-46-generic*
  linux-image-generic* linux-sound-base* lm-sensors* locales* lockfile-progs*
  login* logrotate* lp-solve* lsb-release* lshw* lsof* ltrace* m4* make*
  makedev* man-db* mawk* media-player-info* memtest86+* mlocate* modemmanager*
  module-init-tools* motion* mount* mountall* mplayer* mscompress* mtools*
  mtr-tiny* multiarch-support* muon-discover* muon-notifier* muon-updater*
  myspell-en-au* myspell-en-gb* myspell-en-za* mysql-client* mysql-client-5.5*
  mysql-client-core-5.5* mysql-server-core-5.5* nano* ncurses-bin*
  nepomuk-core-ffmpegextractor* nepomuk-core-runtime* net-tools*
  netcat-openbsd* network-manager* network-manager-pptp* nmap* ntfs-3g*
  ntpdate* ntrack-module-libnl-0* obex-data-server* obexd-client* ocrfeeder*
  odbcinst* odbcinst1debian2* okular* okular-extra-backends* openjdk-7-jre*
  openjdk-7-jre-headless* openoffice.org-hyphenation* openprinting-ppds*
  openssh-client* openssl* os-prober* oxideqt-codecs-extra* p11-kit*
  p11-kit-modules* p7zip-full* pam-kwallet* parted* partitionmanager* passwd*
  patch* patchutils* pciutils* pcmciautils* pepperflashplugin-nonfree* perl*
  perl-base* perl-modules* phonon* phonon-backend-gstreamer* pinentry-qt4*
  pkg-config* plasma-dataengines-addons* plasma-dataengines-workspace*
  plasma-desktop* plasma-netbook* plasma-nm* plasma-runner-telepathy-contact*
  plasma-scriptengine-javascript* plasma-widget-folderview*
  plasma-widget-kimpanel* plasma-widget-menubar* plasma-widgets-addons*
  plasma-widgets-workspace* plymouth* plymouth-label*
  plymouth-theme-kubuntu-logo* plymouth-theme-kubuntu-text*
  plymouth-theme-ubuntu-text* pm-utils* po-debconf* policykit-1*
  policykit-1-gnome* polkit-kde-1* poppler-data* poppler-utils*
  popularity-contest* powermgmt-base* ppp* pppconfig* pppoeconf* pptp-linux*
  print-manager* printer-driver-c2esp* printer-driver-foo2zjs*
  printer-driver-foo2zjs-common* printer-driver-gutenprint*
  printer-driver-hpcups* printer-driver-min12xxw* printer-driver-pnm2ppa*
  printer-driver-postscript-hp* printer-driver-ptouch* printer-driver-pxljr*
  printer-driver-sag-gdi* printer-driver-splix* procps* psensor* psmisc*
  pulseaudio* pulseaudio-module-bluetooth* pulseaudio-module-x11*
  pulseaudio-utils* pybootchartgui* python* python-apt* python-apt-common*
  python-cairo* python-chardet* python-crypto* python-cups*
  python-cupshelpers* python-dbus* python-debian* python-dirspec*
  python-enchant* python-gi* python-gobject* python-gobject-2* python-gtk2*
  python-httplib2* python-imaging* python-imaging-sane* python-jinja2*
  python-ldb* python-lxml* python-markupsafe* python-minimal* python-ntdb*
  python-oauthlib* python-openssl* python-pam* python-pexpect* python-pil*
  python-pkg-resources* python-pycurl* python-pygoocanvas* python-qt4-dbus*
  python-renderpm* python-reportlab* python-reportlab-accel* python-requests*
  python-samba* python-sane* python-serial* python-six* python-support*
  python-talloc* python-tdb* python-tk* python-twisted-bin*
  python-twisted-core* python-twisted-web* python-ubuntu-sso-client*
  python-urllib3* python-xapian* python-yaml* python-zope.interface*
  python2.7* python2.7-minimal* python3* python3-apport* python3-apt*
  python3-aptdaemon* python3-chardet* python3-commandnotfound* python3-dbus*
  python3-dbus.mainloop.qt* python3-debian* python3-defer*
  python3-distupgrade* python3-gdbm* python3-gi* python3-minimal*
  python3-pkg-resources* python3-problem-report* python3-pycurl*
  python3-pykde4* python3-pyqt4* python3-sip* python3-six*
  python3-software-properties* python3-update-manager* python3-xkit*
  python3.4* python3.4-minimal* qapt-batch* qapt-deb-installer* qarecord*
  qdbus* qjackctl* qpdf* qtchooser* qtcore4-l10n* quarry* quassel*
  readline-common* resolvconf* rfkill* rsync* rsyslog* rtkit* ruby* ruby1.9.1*
  samba-common* samba-common-bin* samba-libs* sane-utils* scdaemon* sed*
  sgml-base* sgml-data* shared-mime-info* sjeng* skanlite* smbclient* socat*
  software-properties-common* software-properties-kde* soprano-daemon* sox*
  speech-dispatcher* speech-dispatcher-audio-plugins*
  speech-dispatcher-festival* ssl-cert* stockfish* strace* sudo* syslinux*
  syslinux-legacy* system-config-printer-udev* systemd-services* systemd-shim*
  systemsettings* sysv-rc* sysvinit-utils* t1utils* tar* tcl* tcl8.6* tcpd*
  tcpdump* telepathy-gabble* telepathy-haze* telepathy-logger*
  telepathy-mission-control-5* telepathy-salut* telnet* tesseract-ocr* time*
  tk* tk8.6* toshset* traceroute* ttf-mscorefonts-installer* tzdata*
  tzdata-java* ubuntu-drivers-common* ubuntu-extras-keyring* ubuntu-minimal*
  ubuntu-release-upgrader-core* ubuntu-release-upgrader-qt* ubuntu-sso-client*
  ubuntu-standard* ucf* udev* udisks2* ufw* unattended-upgrades* uno-libs3*
  unpaper* unrar* unzip* update-inetd* update-manager-core*
  update-notifier-common* upower* upstart* ure* ureadahead*
  usb-creator-common* usb-creator-kde* usb-modeswitch* usbmuxd* usbutils*
  user-manager* util-linux* uuid-runtime* vbetool* vcdimager* vim-common*
  vim-tiny* virtualbox* virtualbox-dkms* virtualbox-qt* virtuoso-minimal*
  virtuoso-opensource-6.1-bin* virtuoso-opensource-6.1-common* vlc* vlc-data*
  vlc-nox* vlc-plugin-notify* vlc-plugin-pulse* wamerican* wbritish* wget*
  whiptail* whoopsie* whoopsie-preferences* wireless-tools* wodim*
  wpasupplicant* x11-apps* x11-common* x11-session-utils* x11-utils*
  x11-xfs-utils* x11-xkb-utils* x11-xserver-utils* xauth* xdg-user-dirs*
  xfonts-base* xfonts-encodings* xfonts-mathml* xfonts-scalable* xfonts-utils*
  xinit* xinput* xml-core* xorg* xserver-common* xserver-xorg*
  xserver-xorg-core* xserver-xorg-input-all* xserver-xorg-input-evdev*
  xserver-xorg-input-mouse* xserver-xorg-input-synaptics*
  xserver-xorg-input-vmmouse* xserver-xorg-input-wacom*
  xserver-xorg-video-all* xserver-xorg-video-ati* xserver-xorg-video-cirrus*
  xserver-xorg-video-fbdev* xserver-xorg-video-glamoregl*
  xserver-xorg-video-intel* xserver-xorg-video-mach64* xserver-xorg-video-mga*
  xserver-xorg-video-modesetting* xserver-xorg-video-neomagic*
  xserver-xorg-video-nouveau* xserver-xorg-video-openchrome*
  xserver-xorg-video-qxl* xserver-xorg-video-r128* xserver-xorg-video-radeon*
  xserver-xorg-video-s3* xserver-xorg-video-savage*
  xserver-xorg-video-siliconmotion* xserver-xorg-video-sis*
  xserver-xorg-video-sisusb* xserver-xorg-video-tdfx*
  xserver-xorg-video-trident* xserver-xorg-video-vesa*
  xserver-xorg-video-vmware* xul-ext-ubufox* xz-utils* yelp* zip* zlib1g*
  zlib1g-dev*
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  apt libapt-pkg4.12 (due to apt) libc6 (due to apt) libgcc1 (due to apt)
  libstdc++6 (due to apt) gnupg (due to apt) base-files base-passwd
  libdebconfclient0 (due to base-passwd) bash debianutils (due to bash) dash
  (due to bash) libtinfo5 (due to bash) bsdutils coreutils libacl1 (due to
  coreutils) libattr1 (due to coreutils) libselinux1 (due to coreutils) dpkg
  (due to dash) diffutils libbz2-1.0 (due to dpkg) liblzma5 (due to dpkg)
  zlib1g (due to dpkg) tar (due to dpkg) e2fsprogs e2fslibs (due to e2fsprogs)
  libblkid1 (due to e2fsprogs) libcomerr2 (due to e2fsprogs) libss2 (due to
  e2fsprogs) libuuid1 (due to e2fsprogs) util-linux (due to e2fsprogs)
  findutils grep install-info (due to grep) libpcre3 (due to grep) gzip
  hostname libc-bin libcap2 (due to libc-bin) login libpam0g (due to login)
  libpam-runtime (due to login) libpam-modules (due to login) mount libmount1
  (due to mount) ncurses-bin perl-base sed tzdata (due to util-linux) debconf
  (due to util-linux) sysv-rc (due to util-linux) libncurses5 (due to
  util-linux) libslang2 (due to util-linux)
0 to upgrade, 0 to newly install, 1821 to remove and 0 not to upgrade.
After this operation, 3,104 MB disk space will be freed.
You are about to do something potentially harmful
To continue type in the phrase ‘Yes, do as I say!’
 ?] Abort.
```

---

### Post by dino99 on 2015-03-03
ah ah, you may have some non genuine packages installed (from ppa for example.)
open the file manager, and downgrade these packages first (ppa enabled first, then disabled when the downgrade is done)

---

### Post by oldos2er on 2015-03-03
What package were you originally trying to remove?

---

### Post by kerry_s on 2015-03-03
sudo apt-get reinstall kubuntu-desktop
sudo apt-get update

---

### Post by J_Me on 2015-03-04
Thanks for the replies
> ah ah, you may have some non genuine packages installed (from ppa for example.)
open the file manager, and downgrade these packages first (ppa enabled first, then disabled when the downgrade is done)Is it a straight forward process. The package manager for kubuntu doesn't highlight ppa's also I'm a bit hazy on which ones I installed.
So I did some googling and found.
ppa-purge
y-ppa(I think this is just for Ubuntu not Kubuntu)
> What package were you originally trying to remove?libreOffice,cacti
> sudo apt-get reinstall kubuntu-desktop
sudo apt-get updateAre you suggesting that I run this after running autoremove, won't I lose all the additional packages I installed.
Thanks

---

### Post by ian-weisser on 2015-03-04
> **J_Me said:**
> The package manager for kubuntu doesn't highlight ppa's also I'm a bit hazy on which ones I installed.
Apt (the package manager) doesn't know or care if a source is an Official Ubuntu Repository,or a PPA or something else.
Apt only knows "the human told me to use this source".
You -the human- are responsible choosing safe, appropriate sources for apt to use. That's why Ubuntu includes a full set of Official Repositories that you can trust.

> **J_Me said:**
>  Are you suggesting that I run this after running autoremove, won't I lose all the additional packages I installed.
If you install kubuntu-desktop *after* autoremove, you will indeed lose all those packages first, leaving your system in a sorry state.
The suggestion was to install kubuntu-desktop *before* autoremove, to prevent loss of all those packages.


The system trying to remove lots and lots of packages is rare.The cause is well known and easily fixable.
Apt keeps track of which packages are *manually* specified by you, and which are *automatically* included as dependencies.
Apt will never autoremove a package marked 'manual'
Apt will always autoremove a package marked 'auto' if no installed package depends upon it.
The cause: All those packages are marked 'auto', and are dependencies of the package you want to remove.
The fix: Install something (thereby marking it 'manual') that depends upon many of those packages. Hence the kubuntu-desktop suggestion.

---

### Post by J_Me on 2015-03-05
Thanks for taking the time to give me a detailed explanation, much appreciated.
> The system trying to remove lots and lots of packages is rare.Not with me :) usually I just do a fresh install and move on, but this time I'd like to tackle the issue if I can.
Anyway trying 'sudo apt-get reinstall kubuntu-desktop' I get this error 'E: Invalid operation reinstall'
Just for clarity
```
man apt-get
--reinstall
           Re-install packages that are already installed and at the newest version. Configuration Item:
           APT::Get::ReInstall.
```

---

### Post by ian-weisser on 2015-03-05
Try: sudo apt-get install kubuntu-desktop

If kubuntu-desktop were installed, the system would not be trying to remove dependencies of it.

---

### Post by J_Me on 2015-03-05
Thanks that worked. Marking this thread as solved.

---

