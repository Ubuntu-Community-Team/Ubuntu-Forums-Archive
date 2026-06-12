---
title: "Apt wants to remove whole system"
date: 2014-02-23
forum: Installation &amp; Upgrades
---

### Post by promotox on 2014-02-23
I had dependeces issue so i run ```
sudo apt-get -f install 
```

and this is what i get ```
 $ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  aglfn apper-data avogadro-data firefox-locale-pl flare-data fontforge-common freeciv-data
  gcc-4.8-base:i386 gir1.2-gdesktopenums-3.0 gnustep-common libakonadi-kabc4 libavahi-common-data:i386
  libbcmail-java libbcpkix-java libcolumbus1-common libgdata-common libgnomeprint2.2-data
  libgnomeprintui2.2-common libgnuinet-java libgnujaf-java libgnumail-java libgtksourceview2.0-common
  libkonq5-templates liblouis-data libnux-4.0-common libpthread-stubs0 libpthread-stubs0-dev libx11-doc
  octave-common octave-htmldoc pidgin-data psensor-common qastools-common sphinx-voxforge-hmm-en
  sphinx-voxforge-lm-en ubuntu-mobile-icons ubuntu-touch-sounds unetbootin-translations
  unity-scopes-master-default unity-scopes-runner x11proto-composite-dev x11proto-core-dev
  x11proto-damage-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev
  x11proto-render-dev x11proto-xext-dev x11proto-xinerama-dev xcrysden-data xorg-sgml-doctools xtrans-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gcc-4.8-base gcc-4.8-base:i386
The following packages will be REMOVED:
  a2jmidid abgate account-plugin-facebook account-plugin-flickr account-plugin-google
  account-plugin-twitter accountsservice acl acpi-support acpid adduser aeolus agave akonadi-backend-mysql
  akonadi-server alacarte alsa-base alsa-tools alsa-tools-gui alsa-utils amb-plugins anacron apg apparmor
  apparmor-easyprof apper apport apport-gtk appstream-index apt apt-transport-https apt-utils
  apt-xapian-index aptdaemon arandr ardour ardour3 argyll ark aspell aspell-en at-spi2-core audacious
  audacious-plugins audacity autotalent avahi-autoipd avahi-daemon avahi-utils avogadro bamfdaemon
  banish404 base-files base-passwd bash bash-completion batmon.app bc bcmwl-kernel-source bind9-host
  binfmt-support binutils bleachbit blender blop blt blueman bluetooth bluewho bluez bluez-alsa bluez-audio
  bluez-btsco bluez-compat bluez-cups bluez-dbg bluez-gstreamer bluez-hcidump bluez-pcmcia-support
  bluez-tools bluez-utils bonnie++ bootchart brasero brasero-cdrkit brasero-common brltty bsdmainutils
  bsdutils build-essential bum busybox-initramfs bwidget bzip2 bzr ca-certificates ca-certificates-java
  cabextract calf-plugins calligra-libs caps catfish cdrdao cheese cheese-common
  chromium-codecs-ffmpeg-extra cifs-utils cli-common cm-super-minimal cm-super-x11 cmt colord
  command-not-found console-setup consolekit content-hub coreutils cpio cpp cpp-4.7 cpp-4.8 cpu-g
  cracklib-runtime crda cron cryptsetup-bin cups cups-browsed cups-bsd cups-client cups-daemon
  cups-driver-gutenprint cups-filters cups-pk-helper cups-ppdc curl darktable dash dbus dbus-x11 dc
  dconf-cli dconf-gsettings-backend dconf-service dcraw debconf debconf-i18n debhelper debianutils
  debugedit default-jre default-jre-headless desktop-file-utils dh-apparmor dh-python dialog
  dictionaries-common diffstat diffutils dkms dmidecode dmsetup dnsmasq-base dnsutils doc-base docbook-xml
  docbook-xsl dosbox dosfstools dpkg dpkg-dev dssi-dev dssi-host-jack dssi-utils dvd+rw-tools dvdauthor
  dvdisaster dvdstyler dvgrab dvipng e2fslibs e2fsprogs ed eject elementary-icon-theme elyxer enchant eq10q
  ethtool evince evince-common evolution-data-server-common exiftran exiv2 exo-utils extlinux fakeroot
  ffado-dbus-server ffado-mixer-qt4 ffado-tools ffmpeg ffmpeg2theora ffmpegthumbnailer file file-roller
  findutils firefox firefox-globalmenu flare flashplugin-installer fluidsynth fluidsynth-dssi fluxgui
  font-manager fontconfig fontconfig-config fontforge fonts-beteckna fonts-bpg-georgian fonts-breip
  fonts-droid fonts-f500 fonts-horai-umefont fonts-junicode fonts-kacst fonts-kacst-one fonts-lmodern
  fonts-manchufont fonts-ocr-a fonts-sil-abyssinica fonts-sil-andika fonts-takao-pgothic fonts-texgyre
  fonts-tomsontalks foo-yc20 foomatic-db-compressed-ppds foomatic-filters freeciv-client-gtk freeciv-server
  frei0r-plugins friendly-recovery friends friends-dispatcher friends-facebook friends-twitter ftp
  furiusisomount fuse fuseiso fuseiso9660 g++ g++-4.8 gambas3 gambas3-dev gambas3-examples gambas3-gb-args
  gambas3-gb-cairo gambas3-gb-chart gambas3-gb-clipper gambas3-gb-complex gambas3-gb-compress
  gambas3-gb-compress-bzlib2 gambas3-gb-compress-zlib gambas3-gb-crypt gambas3-gb-data gambas3-gb-db
  gambas3-gb-db-form gambas3-gb-db-mysql gambas3-gb-db-odbc gambas3-gb-db-postgresql gambas3-gb-db-sqlite3
  gambas3-gb-dbus gambas3-gb-desktop gambas3-gb-eval-highlight gambas3-gb-form gambas3-gb-form-dialog
  gambas3-gb-form-mdi gambas3-gb-form-stock gambas3-gb-gmp gambas3-gb-gsl gambas3-gb-gtk
  gambas3-gb-gtk-opengl gambas3-gb-gui gambas3-gb-gui-opengl gambas3-gb-httpd gambas3-gb-image
  gambas3-gb-image-effect gambas3-gb-image-imlib gambas3-gb-image-io gambas3-gb-jit gambas3-gb-libxml
  gambas3-gb-map gambas3-gb-memcached gambas3-gb-mime gambas3-gb-mysql gambas3-gb-ncurses gambas3-gb-net
  gambas3-gb-net-curl gambas3-gb-net-pop3 gambas3-gb-net-smtp gambas3-gb-openal gambas3-gb-opengl
  gambas3-gb-opengl-glsl gambas3-gb-opengl-glu gambas3-gb-opengl-sge gambas3-gb-openssl gambas3-gb-option
  gambas3-gb-pcre gambas3-gb-pdf gambas3-gb-qt4 gambas3-gb-qt4-ext gambas3-gb-qt4-opengl
  gambas3-gb-qt4-webkit gambas3-gb-report gambas3-gb-sdl gambas3-gb-sdl-sound gambas3-gb-settings
  gambas3-gb-v4l gambas3-gb-vb gambas3-gb-web gambas3-gb-xml gambas3-gb-xml-html gambas3-gb-xml-rpc
  gambas3-gb-xml-xslt gambas3-ide gambas3-runtime gawk gcalctool gcc-4.7 gcj-4.8-jre-lib gconf-service
  gconf-service-backend gconf2 gconf2-common gcr gdb gdebi-core gedit gedit-common gelemental gem gem-extra
  gem-plugin-gmerlin gem-plugin-lqt gem-plugin-magick gem-plugin-v4l2 genisoimage geoclue
  geoclue-ubuntu-geoip geoip-database gettext gettext-base ghostscript ghostscript-x gigolo gimp gimp-gap
  gimp-gmic gimp-help-en gimp-help-pl gimp-plugin-registry gimp-resynthesizer gimp-ufraw
  gir1.2-accounts-1.0 gir1.2-appindicator3-0.1 gir1.2-atk-1.0 gir1.2-atspi-2.0 gir1.2-dbusmenu-glib-0.4
  gir1.2-dee-1.0 gir1.2-ebook-1.2 gir1.2-ebookcontacts-1.2 gir1.2-edataserver-1.2 gir1.2-freedesktop
  gir1.2-gdata-0.0 gir1.2-gdkpixbuf-2.0 gir1.2-glib-2.0 gir1.2-gmenu-3.0 gir1.2-gnomebluetooth-1.0
  gir1.2-gnomedesktop-3.0 gir1.2-goa-1.0 gir1.2-gstreamer-1.0 gir1.2-gtk-2.0 gir1.2-gtk-3.0
  gir1.2-gtksource-3.0 gir1.2-gudev-1.0 gir1.2-ibus-1.0 gir1.2-messagingmenu-1.0 gir1.2-networkmanager-1.0
  gir1.2-notify-0.7 gir1.2-packagekitglib-1.0 gir1.2-pango-1.0 gir1.2-peas-1.0 gir1.2-signon-1.0
  gir1.2-soup-2.4 gir1.2-totem-1.0 gir1.2-totem-plparser-1.0 gir1.2-unity-5.0 gir1.2-vte-2.90
  gir1.2-webkit-3.0 gir1.2-wnck-3.0 gkbd-capplet gksu gladish glib-networking glib-networking-services
  globs gmidimonitor gmountiso gnome-bluetooth gnome-calculator gnome-color-manager gnome-control-center
  gnome-control-center-signon gnome-disk-utility gnome-icon-theme gnome-icon-theme-full
  gnome-icon-theme-symbolic gnome-keyring gnome-menus gnome-orca gnome-session-bin gnome-settings-daemon
  gnome-shell-common gnome-system-monitor gnome-system-tools gnome-time-admin gnome-tweak-tool
  gnome-user-guide gnome-user-share gnome-video-effects gnupg gnuplot-x11 gnustep-back-common
  gnustep-back0.22 gnustep-back0.22-art gnustep-base-common gnustep-base-runtime gnustep-gpbs
  gnustep-gui-common gnustep-gui-runtime gparted gpgv gpointing-device-settings grep groff-base growisofs
  grub-common grub-gfxpayload-lists grub-pc grub-pc-bin grub2-common gsettings-desktop-schemas
  gsettings-ubuntu-touch-schemas gstreamer0.10-alsa gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3
  gstreamer0.10-nice gstreamer0.10-plugins-bad gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps
  gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-pulseaudio gstreamer0.10-tools
  gstreamer0.10-x gstreamer1.0-clutter gstreamer1.0-fluendo-mp3 gstreamer1.0-libav gstreamer1.0-plugins-bad
  gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-plugins-ugly gstreamer1.0-pulseaudio
  gstreamer1.0-x gtk-recordmydesktop gtk-redshift gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf
  gucharmap guitarix gvfs gvfs-backends gvfs-bin gvfs-common gvfs-daemons gvfs-fuse gvfs-libs gwyddion
  gwyddion-common gzip hardening-includes hardinfo hddtemp hdparm heirloom-mailx hexter hostname hplip
  hplip-data hplip-gui hud humanity-icon-theme hunspell-en-ca hunspell-en-us hwdata hydrogen i-nex
  i965-va-driver ibus ibus-gtk ibus-gtk3 ibus-m17n ibus-table icedtea-7-jre-jamvm icedtea-7-plugin
  icedtea-netx icedtea-plugin icoutils idjc ifupdown im-config imagemagick imagemagick-common
  indicator-application indicator-application-gtk2 indicator-bluetooth indicator-cpufreq
  indicator-multiload indicator-network indicator-sound indicator-sound-gtk2 info init-system-helpers
  initramfs-tools initramfs-tools-bin initscripts inkscape inputattach insserv install-info intel-gpu-tools
  intel-linux-graphics-installer intltool-debian invada-studio-plugins-lv2 iproute iproute2 iptables
  iputils-arping iputils-ping iputils-tracepath ir.lv2 irqbalance isc-dhcp-client isc-dhcp-common iw
  jack-capture jack-keyboard jack-rack jackd jackd2 jackd2-firewire jamin jockey-common katepart kbd
  kde-l10n-pl kde-runtime kde-runtime-data kdelibs-bin kdelibs5-data kdelibs5-plugins kdenlive
  kdenlive-data kdepim-runtime kdepimlibs-kio-plugins kdoctools kerneloops-daemon keyboard-configuration
  keyutils khelpcenter4 kmod krita kubuntu-debug-installer ladish laditools ladspa-sdk lame
  language-pack-en language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base
  language-pack-gnome-pl language-pack-gnome-pl-base language-pack-pl language-pack-pl-base
  language-selector-common language-selector-gnome laptop-detect laptop-mode-tools latex-beamer
  latex-xcolor leafpad less lib32bz2-1.0 liba52-0.7.4 libaa1 libaacs0 libaccount-plugin-1.0-0
  libaccount-plugin-generic-oauth libaccount-plugin-google libaccounts-glib0 libaccounts-qt1
  libaccounts-qt5-1 libaccountsservice0 libacl1 libaio1 libakonadi-calendar4 libakonadi-contact4
  libakonadi-kcal4 libakonadi-kde4 libakonadi-kmime4 libakonadi-notes4 libakonadi-socialutils4
  libakonadiprotocolinternals1 libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl
  libalure1 libamd2.2.0 libandroid-properties1 libao4 libapparmor-perl libapparmor1 libappindicator1
  libappindicator3-1 libappstream0 libapt-inst1.5 libapt-pkg-perl libapt-pkg4.12 libarchive-zip-perl
  libarchive13 libarpack2 libart-2.0-2 libasan0 libasn1-8-heimdal libasn1-8-heimdal:i386 libasound2
  libasound2:i386 libasound2-dev libasound2-plugins libasound2-plugins:i386 libaspell15 libasprintf-dev
  libasprintf0c2 libass4 libassuan0 libasyncns0 libasyncns0:i386 libatasmart4 libatk-adaptor
  libatk-bridge2.0-0 libatk-wrapper-java libatk-wrapper-java-jni libatk1.0-0 libatk1.0-0:i386 libatk1.0-dev
  libatkmm-1.6-1 libatlas3-base libatm1 libatomic1 libatspi2.0-0 libattica0.4 libattr1 libaubio2
  libaudclient2 libaudcore1 libaudio-scrobbler-perl libaudio2 libaudio2:i386 libaudiofile1 libaudit1
  libauthen-sasl-perl libautodie-perl libav-tools libavahi-client3 libavahi-client3:i386 libavahi-common3
  libavahi-common3:i386 libavahi-core7 libavahi-glib1 libavahi-gobject0 libavahi-ui-gtk3-0 libavc1394-0
  libavcodec-extra-53 libavdevice-extra-53 libavfilter-extra-2 libavformat-extra-53 libavogadro1
  libavutil-extra-51 libbabl-0.1-0 libbamf3-2 libbcprov-java libbfb0 libbind9-90 libbinio1ldbl libblas3
  libblkid1 libbluetooth-dev libbluetooth3 libbluetooth3-dbg libbluray1 libbonobo2-0 libbonoboui2-0
  libboost-date-time1.53.0 libboost-filesystem1.49.0 libboost-filesystem1.53.0 libboost-locale1.49.0
  libboost-locale1.53.0 libboost-program-options1.53.0 libboost-python1.49.0 libboost-python1.53.0
  libboost-regex1.49.0 libboost-regex1.53.0 libboost-signals1.53.0 libboost-system1.49.0
  libboost-system1.53.0 libboost-thread1.49.0 libboost-thread1.53.0 libbrasero-media3-1 libbrlapi0.6
  libbs2b0 libbsd0 libburn4 libbz2-1.0 libc-bin libc-dev-bin libc6 libc6:i386 libc6-dbg libc6-dev
  libc6-i386 libcaca0 libcairo-gobject2 libcairo-perl libcairo-script-interpreter2 libcairo2 libcairo2:i386
  libcairo2-dev libcairomm-1.0-1 libcamel-1.2-43 libcanberra-gtk-module libcanberra-gtk0 libcanberra-gtk3-0
  libcanberra-gtk3-module libcanberra-pulse libcanberra0 libcap-ng0 libcap2 libcap2-bin libcapi20-3
  libcapi20-3:i386 libccolamd2.7.1 libcdaudio1 libcddb2 libcdio-cdda1 libcdio-paranoia1 libcdio13
  libcdparanoia0 libcdr-0.0-0 libcdt4 libcheese-gtk23 libcheese7 libcholmod1.7.1 libchromaprint0
  libck-connector0 libclalsadrv2 libclass-accessor-perl libclone-perl libcloog-isl4 libcloog-ppl1
  libclthreads2 libclucene-contribs1 libclucene-core1 libclutter-1.0-0 libclutter-gst-2.0-0
  libclutter-gtk-1.0-0 libclxclient3 libcogl-pango12 libcogl12 libcolamd2.7.1 libcolord-gtk1 libcolord1
  libcolorhug1 libcolumbus1 libcomerr2 libcomerr2:i386 libconfig++9 libconfig-inifiles-perl libcontent-hub0
  libcpufreq0 libcrack2 libcroco3 libcrypt-passwdmd5-perl libcryptsetup4 libcrystalhd3 libcue1 libcups2
  libcups2:i386 libcupscgi1 libcupsfilters1 libcupsimage2 libcupsmime1 libcupsppdc1 libcurl3
  libcurl3-gnutls libcxsparse2.2.3 libdaemon0 libdatrie1 libdatrie1:i386 libdb5.1 libdb5.1:i386 libdbus-1-3
  libdbus-1-3:i386 libdbus-1-dev libdbus-c++-1-0 libdbus-glib-1-2 libdbusmenu-glib4 libdbusmenu-gtk3-4
  libdbusmenu-gtk4 libdbusmenu-qt2 libdc1394-22 libdca0 libdconf1 libdebconf-kde0 libdee-1.0-4 libdee-qt5-3
  libdevmapper-event1.02.1 libdevmapper1.02.1 libdigest-hmac-perl libdirac-encoder0 libdirectfb-1.2-9
  libdjvulibre21 libdlrestrictions1 libdmtx0a libdns99 libdpkg-perl libdrm-intel1 libdrm-intel1:i386
  libdrm-nouveau2 libdrm-nouveau2:i386 libdrm-radeon1 libdrm-radeon1:i386 libdrm2 libdrm2:i386 libdumb1
  libdv-bin libdv4 libdvbpsi8 libdvdnav4 libdvdread4 libebackend-1.2-6 libebml3 libebook-1.2-14
  libebook-contacts-1.2-0 libedata-book-1.2-17 libedataserver-1.2-17 libedit2 libegl1-mesa
  libegl1-mesa-drivers libelemental0 libelf1 libelf1:i386 libelfg0 libemail-valid-perl libenca0
  libenchant1c2a libencode-locale-perl libept1.4.12 libepub0 libesd0 libevdocument3-4 libevent-2.0-5
  libevview3-3 libexempi3 libexif12 libexif12:i386 libexiv2-12 libexo-1-0 libexo-common libexpat1
  libexpat1:i386 libexpat1-dev libexttextcat-2.0-0 libfaad2 libfarstream-0.1-0 libffado2 libffi6
  libffi6:i386 libffmpegthumbnailer4 libfftw3-3 libfftw3-double3 libfftw3-single3 libfile-basedir-perl
  libfile-copy-recursive-perl libfile-desktopentry-perl libfile-fcntllock-perl libfile-listing-perl
  libfile-mimeinfo-perl libflac++6 libflac8 libflac8:i386 libflickcurl0 libflite1 libflowcanvas5
  libfltk-gl1.3 libfltk1.1 libfltk1.3 libfluidsynth1 libfont-afm-perl libfontconfig1 libfontconfig1:i386
  libfontconfig1-dev libfontembed1 libfontenc1 libfontforge1 libframe6 libfreetype6 libfreetype6:i386
  libfreetype6-dev libfribidi0 libfriends0 libfs6 libftgl2 libfuse2 libgail-3-0 libgail-common libgail18
  libgarcon-1-0 libgavl1 libgbm1 libgc1c2 libgcc-4.7-dev libgcc-4.8-dev libgcc1 libgcc1:i386 libgcj-common
  libgcj14 libgck-1-0 libgconf-2-4 libgconf2-4 libgconfmm-2.6-1c2 libgcr-3-1 libgcr-base-3-1 libgcr-ui-3-1
  libgcrypt11 libgcrypt11:i386 libgd3 libgd3:i386 libgdata13 libgdbm3 libgdiplus libgdk-pixbuf2.0-0
  libgdk-pixbuf2.0-0:i386 libgdk-pixbuf2.0-dev libgdraw4 libgee-0.8-2 libgee2 libgegl-0.2-0 libgeis1
  libgeoclue0 libgeoip1 libgettextpo-dev libgettextpo0 libgexiv2-2 libgflags2 libgfortran3 libgif4
  libgif4:i386 libgimp2.0 libgirepository-1.0-1 libgksu2-0 libgl1-mesa-dri libgl1-mesa-dri:i386
  libgl1-mesa-glx libgl1-mesa-glx:i386 libgl2ps0 libglade2-0 libglademm-2.4-1c2a libglamor0 libglapi-mesa
  libglapi-mesa:i386 libgles2-mesa libglew1.10 libglew1.8 libglewmx1.8 libglib-perl libglib2.0-0
  libglib2.0-0:i386 libglib2.0-bin libglib2.0-cil libglib2.0-dev libglibmm-2.4-1c2a libglpk0 libglu1-mesa
  libglu1-mesa:i386 libgme0 libgmerlin-avdec1 libgmime-2.6-0 libgmp10 libgmpxx4ldbl libgnome-bluetooth11
  libgnome-control-center1 libgnome-desktop-3-7 libgnome-keyring0 libgnome-menu-3-0 libgnome-menu2
  libgnome2-0 libgnome2-bin libgnome2-common libgnomecanvas2-0 libgnomecanvasmm-2.6-1c2a libgnomecups1.0-1
  libgnomekbd-common libgnomekbd8 libgnomeprint2.2-0 libgnomeprintui2.2-0 libgnomeui-0 libgnomevfs2-0
  libgnomevfs2-common libgnomevfs2-extra libgnustep-base1.24 libgnustep-gui0.22 libgnutls-openssl27
  libgnutls26 libgnutls26:i386 libgoa-1.0-0 libgomp1 libgoocanvas3 libgoogle-glog0 libgpds0 libgpg-error0
  libgpg-error0:i386 libgpgme11 libgphoto2-6 libgphoto2-6:i386 libgphoto2-port10 libgphoto2-port10:i386
  libgpm2 libgpm2:i386 libgrail6 libgraph4 libgraphicsmagick++3 libgraphicsmagick3 libgraphite2-3
  libgraphite2-3:i386 libgraphite3 libgringotts2 libgrip0 libgs9 libgsettings-qt1 libgsl0ldbl libgsm1
  libgsoap3 libgssapi-krb5-2 libgssapi-krb5-2:i386 libgssapi3-heimdal libgssapi3-heimdal:i386
  libgssdp-1.0-3 libgstreamer-plugins-bad0.10-0 libgstreamer-plugins-bad1.0-0
  libgstreamer-plugins-base0.10-0 libgstreamer-plugins-base0.10-0:i386 libgstreamer-plugins-base1.0-0
  libgstreamer-plugins-good1.0-0 libgstreamer0.10-0 libgstreamer0.10-0:i386 libgstreamer1.0-0
  libgstreamermm-0.10-2 libgtk-3-0 libgtk-3-bin libgtk-3-common libgtk-vnc-2.0-0 libgtk2-perl libgtk2.0-0
  libgtk2.0-0:i386 libgtk2.0-0-dbg libgtk2.0-bin libgtk2.0-cil libgtk2.0-dev libgtkglext1 libgtkimageview0
  libgtkmm-2.4-1c2a libgtkmm-3.0-1 libgtksourceview-3.0-1 libgtksourceview2.0-0 libgtkspell0 libgtlcore0.8
  libgtlfragment0.8 libgtop2-7 libgucharmap-2-90-7 libgudev-1.0-0 libguess1 libgupnp-1.0-4
  libgupnp-igd-1.0-4 libgusb2 libgutenprint2 libgvc5 libgvnc-1.0-0 libgwyddion2-0 libgxps2 libharfbuzz-dev
  libharfbuzz-icu0 libharfbuzz0a libharfbuzz0a:i386 libhcrypto4-heimdal libhcrypto4-heimdal:i386 libhdf5-7
  libheimbase1-heimdal libheimbase1-heimdal:i386 libheimntlm0-heimdal libheimntlm0-heimdal:i386 libhpmud0
  libhtml-form-perl libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl
  libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl libhttp-message-perl libhttp-negotiate-perl
  libhud-client2 libhud2 libhunspell-1.3-0 libhx509-5-heimdal libhx509-5-heimdal:i386 libhybris-common1
  libhyphen0 libibus-1.0-5 libical1 libicc2 libice-dev libice6 libice6:i386 libicu48 libid3tag0
  libidl-common libidl0 libidn11 libido-0.1-0 libido3-0.1-0 libiec61883-0 libieee1284-3 libieee1284-3:i386
  libijs-0.35 libilmbase6 libimage-exiftool-perl libimdi0 libimlib2 libimobiledevice4 libindicator3-7
  libindicator7 libintl-perl libio-html-perl libio-pty-perl libio-socket-inet6-perl libio-socket-ssl-perl
  libio-string-perl libipc-run-perl libipc-system-simple-perl libiptcdata0 libisc95 libisccc90 libisccfg90
  libisl10 libiso9660-8 libisofs6 libitext-java libitm1 libiw30 libjack-jackd2-0 libjack-jackd2-0:i386
  libjack-jackd2-dev libjasper1 libjasper1:i386 libjavascriptcoregtk-1.0-0 libjavascriptcoregtk-3.0-0
  libjbig0 libjbig0:i386 libjbig2dec0 libjpeg-progs libjpeg-turbo-progs libjpeg-turbo8 libjpeg-turbo8:i386
  libjpeg8 libjpeg8:i386 libjson-c2 libjson-c2:i386 libjson-glib-1.0-0 libjson0 libjte1 libk5crypto3
  libk5crypto3:i386 libkabc4 libkactivities-bin libkactivities-models1 libkactivities6 libkalarmcal2
  libkate1 libkatepartinterfaces4 libkcal4 libkcalcore4 libkcalutils4 libkcmutils4 libkdcraw22
  libkde3support4 libkdeclarative5 libkdecore5 libkdesu5 libkdeui5 libkdewebkit5 libkdnssd4 libkemoticons4
  libkeybinder0 libkeyutils1 libkeyutils1:i386 libkfbapi1 libkfile4 libkgapi2-2 libkholidays4 libkhtml5
  libkidletime4 libkimap4 libkio5 libkjsapi4 libkjsembed4 libkldap4 libkmbox4 libkmediaplayer4 libkmime4
  libkmod2 libknewstuff2-4 libknewstuff3-4 libknotifyconfig4 libkntlm4 libkolab0 libkolabxml0
  libkonq-common libkonq5abi1 libkparts4 libkpathsea6 libkpimidentities4 libkpimtextedit4 libkpimutils4
  libkprintutils4 libkpty4 libkrb5-26-heimdal libkrb5-26-heimdal:i386 libkrb5-3 libkrb5-3:i386
  libkrb5support0 libkrb5support0:i386 libkresources4 libkrosscore4 libkrossui4 libktexteditor4
  libkworkspace4abi2 libkxmlrpcclient4 liblangtag1 liblapack3 liblcms1 liblcms1:i386 liblcms2-2
  libldap-2.4-2 libldap-2.4-2:i386 liblensfun0 liblightdm-gobject-1-0 liblilv-0-0 liblircclient0
  liblist-moreutils-perl liblistaller-glib0 libllvm3.0 libllvm3.2 libllvm3.3 libllvm3.4 libllvm3.4:i386
  liblo7 liblocale-gettext-perl liblockfile-bin liblockfile1 liblouis2 liblqr-1-0 liblrdf0 libltc11
  libltcsmpte1 libltdl7 libltdl7:i386 liblua5.1-0 liblua5.2-0 liblv2dynparamhost1-1 liblvm2app2.2
  liblwp-mediatypes-perl liblwp-protocol-https-perl liblwres90 liblzma5 liblzma5:i386 liblzo2-2 libm17n-0
  libmad0 libmagic1 libmagick++5 libmagickcore5 libmagickcore5-extra libmagickwand5 libmail-sendmail-perl
  libmailtools-perl libmailtransport4 libmatroska5 libmcrypt4 libmeanwhile1 libmessaging-menu0 libmhash2
  libmicroblog4 libmikmod2 libmimic0 libminiupnpc8 libmirclient3 libmirplatform libmirprotobuf0
  libmirserver7 libmjpegutils-2.0-0 libmlt++3 libmlt-data libmlt5 libmms0 libmng1 libmng1:i386 libmnl0
  libmodplug1 libmono-cairo4.0-cil libmono-corlib4.0-cil libmono-i18n-west4.0-cil libmono-i18n4.0-cil
  libmono-security4.0-cil libmono-system-configuration4.0-cil libmono-system-drawing4.0-cil
  libmono-system-security4.0-cil libmono-system-xml4.0-cil libmono-system4.0-cil libmount1 libmowgli2
  libmp3lame0 libmpc2 libmpc3 libmpcdec6 libmpeg2-4 libmpfr4 libmpg123-0 libmpg123-0:i386 libmspub-0.0-0
  libmtdev1 libmtp-runtime libmtp9 libmulticobex1 libmuparser2 libmxml1 libmysqlclient18
  libmysqlclient18:i386 libmythes-1.2-0 libnatpmp1 libnautilus-extension1a libncurses5 libncurses5:i386
  libncursesw5 libneon27-gnutls libnepomuk4 libnepomukcleaner4 libnepomukcore4abi1 libnepomukquery4a
  libnepomukutils4 libnet-dbus-perl libnet-dns-perl libnet-domain-tld-perl libnet-http-perl libnet-ip-perl
  libnet-smtp-ssl-perl libnet-ssleay-perl libnetfilter-conntrack3 libnetpbm10 libnettle4 libnewt0.52
  libnfnetlink0 libnice10 libnih-dbus1 libnih1 libnl-3-200 libnl-genl-3-200 libnl-route-3-200
  libnm-glib-vpn1 libnm-glib4 libnm-gtk0 libnm-util2 libnotify-bin libnotify4 libnspr4 libnspr4:i386
  libnspr4-0d libnss-cache libnss-mdns libnss3 libnss3:i386 libnss3-1d libntrack-qt4-1 libntrack0 libnuma1
  libnux-4.0-0 liboauth0 libobexftp0 libobjc4 liboctave1 libodbc1 libofa0 libofono-qt1 libogg0 libogg0:i386
  liboggkate1 liboil0.3 liboobs-1-5 libopenal1 libopenal1:i386 libopenbabel4 libopencolorio1
  libopencore-amrnb0 libopencore-amrwb0 libopencv-core2.4 libopencv-highgui2.4 libopencv-imgproc2.4
  libopenexr6 libopenimageio1.1 libopenjpeg2 libopenobex1 libopenshiva0.8 libopenvg1-mesa libopus0
  liborbit2 liborc-0.4-0 liborc-0.4-0:i386 liborcus-0.6-0 libotf0 libp11-kit-gnome-keyring
  libp11-kit-gnome-keyring:i386 libp11-kit0 libp11-kit0:i386 libpackagekit-glib2-16 libpackagekit-qt2-6
  libpam-cap libpam-ck-connector libpam-gnome-keyring libpam-modules libpam-modules-bin libpam-runtime
  libpam-systemd libpam0g libpango-1.0-0 libpango-1.0-0:i386 libpango-perl libpango1.0-0 libpango1.0-dev
  libpangocairo-1.0-0 libpangocairo-1.0-0:i386 libpangoft2-1.0-0 libpangoft2-1.0-0:i386 libpangomm-1.4-1
  libpangox-1.0-0 libpangoxft-1.0-0 libpaper-utils libpaper1 libparse-debianchangelog-perl
  libparted0debian1 libpathplan4 libpcap0.8 libpci3 libpciaccess0 libpciaccess0:i386 libpcre3 libpcre3:i386
  libpcre3-dev libpcrecpp0 libpcsclite1 libpeas-1.0-0 libperl5.14 libperlio-gzip-perl libphat0 libphonon4
  libphononexperimental4 libpipeline1 libpixman-1-0 libpixman-1-0:i386 libpixman-1-dev libplasma3 libplist1
  libplot2c2 libplotmm0 libplymouth2 libpng12-0 libpng12-0:i386 libpng12-dev libpocketsphinx1
  libpodofo0.9.0 libpolkit-agent-1-0 libpolkit-backend-1-0 libpolkit-gobject-1-0 libpolkit-qt-1-1
  libpoppler-glib8 libpoppler-qt4-4 libpoppler37 libpoppler43 libpopt0 libportaudio2 libportmidi0
  libportsmf0 libpostproc-extra-52 libppl-c4 libppl12 libpq5 libprison0 libprocps0 libprotobuf7 libproxy1
  libpstoedit0c2a libptexenc1 libpth20 libpulse-mainloop-glib0 libpulse0 libpulse0:i386 libpulsedsp
  libpurple-bin libpurple0 libpwquality1 libpython-stdlib libpython2.7 libpython2.7-stdlib
  libpython3-stdlib libpython3.3 libpython3.3-minimal libpython3.3-stdlib libqapt2 libqapt2-runtime libqca2
  libqca2-plugin-ossl libqdjango-db0 libqhull5 libqjson0 libqmenumodel0 libqpdf10 libqrencode3 libqrupdate1
  libqt4-dbus libqt4-dbus:i386 libqt4-declarative libqt4-declarative:i386 libqt4-designer libqt4-help
  libqt4-network libqt4-network:i386 libqt4-opengl libqt4-opengl:i386 libqt4-qt3support libqt4-script
  libqt4-script:i386 libqt4-scripttools libqt4-sql libqt4-sql:i386 libqt4-sql-mysql libqt4-sql-mysql:i386
  libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml libqt4-xml:i386 libqt4-xmlpatterns
  libqt4-xmlpatterns:i386 libqt53d5 libqt5core5 libqt5dbus5 libqt5feedback5 libqt5gui5 libqt5location5
  libqt5multimedia5 libqt5multimediaquick-p5 libqt5network5 libqt5opengl5 libqt5organizer5
  libqt5printsupport5 libqt5qml-graphicaleffects libqt5qml5 libqt5quick5 libqt5sensors5 libqt5sql5
  libqt5sql5-sqlite libqt5svg5 libqt5systeminfo5 libqt5test5 libqt5v8-5 libqt5webkit5 libqt5widgets5
  libqt5xml5 libqt5xmlpatterns5 libqtassistantclient4 libqtcore4 libqtcore4:i386 libqtgui4 libqtgui4:i386
  libqtscript4-core libqtscript4-gui libqtscript4-network libqtscript4-opengl libqtscript4-phonon
  libqtscript4-qtbindings libqtscript4-sql libqtscript4-svg libqtscript4-uitools libqtscript4-webkit
  libqtscript4-xml libqtscript4-xmlpatterns libqtshiva0.1 libqtwebkit4 libqtwebkit4:i386 libquadmath0
  libquicktime2 libquvi7 libqwt5-qt4 libqwtplot3d-qt4-0 libraptor1 libraptor2-0 librarian0 librasqal3
  libraul10 libraw1394-11 libraw9 librdf0 libreadline5 libreadline6 libreoffice
  libreoffice-avmedia-backend-gstreamer libreoffice-base libreoffice-base-core libreoffice-base-drivers
  libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw libreoffice-gnome libreoffice-gtk
  libreoffice-impress libreoffice-java-common libreoffice-math libreoffice-pdfimport
  libreoffice-report-builder-bin libreoffice-sdbc-firebird libreoffice-sdbc-hsqldb libreoffice-writer
  libresid-builder0c2a librest-0.7-0 libroken18-heimdal libroken18-heimdal:i386 librpm3 librpmbuild3
  librpmio3 librpmsign1 librsvg2-2 librsvg2-bin librsvg2-common librtaudio4 librtmidi1 librtmp0
  librubberband2 libruby1.9.1 libsamplerate0 libsamplerate0:i386 libsane libsane:i386 libsane-hpaio
  libsasl2-2 libsasl2-2:i386 libsasl2-modules libsasl2-modules:i386 libsasl2-modules-db
  libsasl2-modules-db:i386 libsbc1 libsbsms10 libschroedinger-1.0-0 libsdl-image1.2 libsdl-mixer1.2
  libsdl-net1.2 libsdl-sound1.2 libsdl-ttf2.0-0 libsdl1.2debian libsecret-1-0 libselinux1 libselinux1:i386
  libsemanage1 libsensors4 libsepol1 libserd-0-0 libsexy2 libsgutils2-2 libshout-idjc3 libshout3
  libsidplay1 libsidplay2 libsigc++-1.2-5c2 libsigc++-2.0-0c2a libsignon-extension1 libsignon-glib1
  libsignon-plugins-common1 libsignon-qt1 libsignon-qt5-1 libsigsegv2 libslang2 libslv2-9 libsm-dev libsm6
  libsm6:i386 libsmbclient libsndfile1 libsndfile1:i386 libsnmp30 libsocket6-perl libsolid4 libsoprano4
  libsord-0-0 libsoundtouch0 libsoup-gnome2.4-1 libsoup2.4-1 libsox-fmt-alsa libsox-fmt-base libsox2
  libsoxr0 libspandsp2 libspectre1 libspeex1 libspeexdsp1 libspeexdsp1:i386 libsphinxbase1 libspiro0
  libspnav0 libsqlite0 libsqlite3-0 libsqlite3-0:i386 libsratom-0-0 libsrtp0 libss2 libssh-4 libssh2-1
  libssl1.0.0 libssl1.0.0:i386 libstartup-notification0 libstdc++-4.8-dev libstdc++6 libstdc++6:i386
  libstk0c2a libstreamanalyzer0 libstreams0 libsub-identify-perl libsub-name-perl libsubtitleeditor0
  libsuil-0-0 libsvga1 libswitch-perl libswscale-extra-2 libswt-cairo-gtk-3-jni libswt-gtk-3-java
  libswt-gtk-3-jni libswt-webkit-gtk-3-jni libsynfig0 libsys-hostname-long-perl libsysfs2
  libsystemd-daemon0 libsystemd-journal0 libsystemd-login0 libsystemsettings1 libt1-5 libtag1-vanilla
  libtag1c2a libtagc0 libtalloc2 libtar0 libtasn1-3 libtasn1-3:i386 libtbb2 libtdb1 libtelepathy-glib0
  libtevent0 libtext-charwidth-perl libtext-iconv-perl libtext-levenshtein-perl libtext-unidecode-perl
  libtext-wrapi18n-perl libthai0 libthai0:i386 libtheora0 libthreadweaver4 libthumbnailer0 libthunarx-2-0
  libtidy-0.99-0 libtie-ixhash-perl libtiff-tools libtiff4 libtiff5 libtiff5:i386 libtimedate-perl
  libtimezonemap1 libtinfo5 libtinfo5:i386 libtinyxml2.6.2 libtotem-plparser17 libtotem0 libts-0.0-0
  libtsan0 libtumbler-1-0 libtwolame0 libtxc-dxtn-s2tc0 libtxc-dxtn-s2tc0:i386
  libubuntu-application-api-mirserver1 libubuntu-location-service0 libubuntu-platform-hardware-api1
  libubuntudownloadmanager1 libudev1 libudev1:i386 libudisks2-0 libumfpack5.4.0 libuninameslist0
  libunique-1.0-0 libunistring0 libunity-action-qt1 libunity-core-6.0-8 libunity-mir1
  libunity-protocol-private0 libunity-webapps0 libunity9 libunwind8 libupnp6 libupower-glib1
  libupstart-app-launch1 libupstart1 liburi-perl liburl-dispatcher1 libusb-0.1-4 libusb-1.0-0
  libusb-1.0-0:i386 libusbmuxd2 libuser1 libusermetricsoutput1 libustr-1.0-1 libutempter0 libuuid-perl
  libuuid1 libuuid1:i386 libv4l-0 libv4l-0:i386 libv4lconvert0 libv4lconvert0:i386 libva-drm1 libva-egl1
  libva-glx1 libva-intel-vaapi-driver libva-tpi1 libva-x11-1 libva1 libvamp-hostsdk3 libvamp-sdk2
  libvcdinfo0 libvdpau1 libvirtodbc0 libvisio-0.0-0 libvisual-0.4-0 libvisual-0.4-plugins libvlc5
  libvlccore5 libvncserver0 libvo-aacenc0 libvo-amrwbenc0 libvorbis0a libvorbis0a:i386 libvorbisenc2
  libvorbisenc2:i386 libvorbisfile3 libvpx1 libvpx1:i386 libvte-2.90-9 libvte9 libwacom2 libwavpack1
  libwayland-client0 libwayland-cursor0 libwayland-server0 libwbclient0 libwebkitgtk-1.0-0
  libwebkitgtk-3.0-0 libwebp4 libwhoopsie-preferences0 libwhoopsie0 libwildmidi1 libwind0-heimdal
  libwind0-heimdal:i386 libwmf-bin libwmf0.2-7 libwnck-3-0 libwnck22 libwpd-0.9-9 libwpg-0.2-2 libwps-0.2-2
  libwrap0 libwrap0:i386 libwww-perl libwww-robotrules-perl libwxbase2.8-0 libwxgtk-media2.8-0
  libwxgtk2.8-0 libwxsvg0 libx11-6 libx11-6:i386 libx11-dev libx11-xcb1 libx11-xcb1:i386 libx264-123
  libx86-1 libxapian22 libxatracker1 libxau-dev libxau6 libxau6:i386 libxaw7 libxcb-composite0
  libxcb-dri2-0 libxcb-dri2-0:i386 libxcb-glx0 libxcb-glx0:i386 libxcb-icccm4 libxcb-image0 libxcb-keysyms1
  libxcb-randr0 libxcb-render-util0 libxcb-render0 libxcb-render0:i386 libxcb-render0-dev libxcb-shape0
  libxcb-shm0 libxcb-shm0:i386 libxcb-shm0-dev libxcb-sync0 libxcb-util0 libxcb-xfixes0 libxcb-xv0 libxcb1
  libxcb1:i386 libxcb1-dev libxcomposite-dev libxcomposite1 libxcomposite1:i386 libxcursor-dev libxcursor1
  libxcursor1:i386 libxdamage-dev libxdamage1 libxdamage1:i386 libxdmcp-dev libxdmcp6 libxdmcp6:i386
  libxerces-c3.1 libxext-dev libxext6 libxext6:i386 libxfce4ui-1-0 libxfce4ui-utils libxfce4util-bin
  libxfce4util6 libxfcegui4-4 libxfconf-0-2 libxfixes-dev libxfixes3 libxfixes3:i386 libxfont1 libxft-dev
  libxft2 libxi-dev libxi6 libxi6:i386 libxine2 libxine2-bin libxine2-ffmpeg libxine2-misc-plugins
  libxine2-plugins libxine2-x libxinerama-dev libxinerama1 libxinerama1:i386 libxkbcommon0 libxkbfile1
  libxklavier16 libxml++2.6-2 libxml-libxml-perl libxml-namespacesupport-perl libxml-parser-perl
  libxml-sax-base-perl libxml-sax-expat-perl libxml-sax-perl libxml-twig-perl libxml-xpath-perl libxml2
  libxml2:i386 libxml2-utils libxmu6 libxmuu1 libxp6 libxpm4 libxpm4:i386 libxrandr-dev libxrandr2
  libxrandr2:i386 libxrender-dev libxrender1 libxrender1:i386 libxres1 libxslt1.1 libxslt1.1:i386 libxss1
  libxss1:i386 libxt6 libxt6:i386 libxtables10 libxtst6 libxtst6:i386 libxv1 libxv1:i386 libxvidcore4
  libxvmc1 libxxf86dga1 libxxf86vm1 libxxf86vm1:i386 libyajl2 libyaml-0-2 libyaml-cpp0.3 libyaml-tiny-perl
  libyelp0 libzbar0 libzeitgeist-1.0-1 libzeitgeist-2.0-0 libzephyr4 libzip2 libzita-alsa-pcmi0
  libzita-convolver3 libzita-resampler1 libzvbi0 lightdm lightdm-gtk-greeter lintian linux-disk-cleaner
  linux-headers-3.11.0-15-lowlatency linux-headers-3.11.0-17-lowlatency linux-headers-lowlatency
  linux-image-3.11.0-15-lowlatency linux-image-3.11.0-17-lowlatency linux-image-lowlatency linux-lowlatency
  linux-lowlatency-headers-3.11.0-15 linux-lowlatency-headers-3.11.0-17 linux-sound-base linuxdcpp
  listaller lm-sensors lmms lmodern locate lockfile-progs login logrotate lp-solve lsb-release lshw lsof
  lsscsi ltrace luatex lv2fil lv2vocoder lyx lyx-common make makedev man-db mawk maxima maxima-doc
  maxima-share mcp-plugins mda-lv2 melt memtest86+ mencoder menu meterbridge mknfonts.tool mlocate
  modemmanager module-init-tools mono-4.0-gac mono-gac mono-runtime mount mountall mousetweaks mpg321
  mplayer mscompress mtools mtr-tiny mudita24 multiarch-support murrine-themes musescore mypaint
  myspell-en-au myspell-en-gb myspell-en-za myspell-pl mysql-client-core-5.5 mysql-server-core-5.5 nano
  nautilus nautilus-data nautilus-dropbox nautilus-sendto ncurses-bin nepomuk-core nepomuk-core-runtime
  net-tools netcat-openbsd netpbm network-manager network-manager-gnome network-manager-pptp
  network-manager-pptp-gnome nsscache ntfs-3g ntfs-config ntpdate ntrack-module-libnl-0 nvidia-common
  obex-data-server obexd-client obexftp octave octave-info odbcinst odbcinst1debian2 omins oneconf
  oneconf-common openbabel openjdk-7-jre openjdk-7-jre-headless openprinting-ppds openshot openshot-doc
  openssh-client openssl orage os-prober osmo osspd p11-kit p7zip-full packagekit packagekit-backend-aptcc
  packagekit-tools parole parted passwd patch patchage patchutils pavucontrol pciutils pcmciautils
  pd-plugin pdftk perl perl-base perl-modules perlmagick pgf phasex phatch phatch-cli phonon
  phonon-backend-gstreamer pidgin pidgin-libnotify pkg-config plasma-scriptengine-javascript plymouth
  plymouth-label plymouth-theme-ubuntu-text plymouth-theme-ubuntustudio pm-utils po-debconf policykit-1
  policykit-1-gnome poppler-data poppler-utils popularity-contest powermgmt-base powerstat powertop ppp
  pppconfig pppoeconf pptp-linux preload preview-latex-style printer-driver-c2esp printer-driver-foo2zjs
  printer-driver-gutenprint printer-driver-hpcups printer-driver-min12xxw printer-driver-pnm2ppa
  printer-driver-postscript-hp printer-driver-ptouch printer-driver-pxljr printer-driver-sag-gdi
  printer-driver-splix procps prosper ps2eps psensor psmisc pstoedit psutils pulseaudio
  pulseaudio-module-gconf pulseaudio-module-jack pulseaudio-module-x11 pulseaudio-utils puredata
  puredata-core puredata-extra puredata-gui puredata-utils pybootchartgui python python-appindicator
  python-apt python-apt-common python-aptdaemon python-aptdaemon.gtk3widgets python-avogadro
  python-beautifulsoup python-bluez python-bzrlib python-cairo python-central python-chardet
  python-commandnotfound python-configobj python-crypto python-cups python-cupshelpers python-dateutil
  python-dbus python-debian python-debtagshw python-defer python-dirspec python-enum python-eyed3
  python-feedparser python-gconf python-gdbm python-gi python-gi-cairo python-glade2 python-gmenu
  python-gnome2 python-gnomekeyring python-gobject python-gobject-2 python-gpgme python-gst0.10 python-gtk2
  python-hachoir-core python-hachoir-metadata python-hachoir-parser python-httplib2 python-ibus
  python-imaging python-imaging-compat python-kaa-base python-kaa-metadata python-keyring python-laditools
  python-launchpadlib python-lazr.restfulclient python-lazr.uri python-ldap python-libuser python-libxml2
  python-lxml python-minimal python-mlt5 python-mutagen python-notify python-numpy python-oauth
  python-oauthlib python-oneconf python-openssl python-pam python-paramiko python-pexpect
  python-piston-mini-client python-pkg-resources python-pyasn1 python-pycurl python-pyexiv2
  python-pygoocanvas python-pyorbit python-qt4 python-qt4-dbus python-renderpm python-reportlab
  python-reportlab-accel python-rsvg python-secretstorage python-serial python-simplejson python-sip
  python-six python-smartpm python-smbc python-sqlite python-support python-tk python-twisted
  python-twisted-bin python-twisted-conch python-twisted-core python-twisted-lore python-twisted-mail
  python-twisted-names python-twisted-news python-twisted-runner python-twisted-web python-twisted-words
  python-tz python-ubuntu-sso-client python-uniconvertor python-utidylib python-wadllib python-webkit
  python-wnck python-wxgtk2.8 python-wxversion python-xapian python-xdg python-xkit python-zeitgeist
  python-zope.interface python2.7 python2.7-minimal python3 python3-apport python3-apt python3-aptdaemon
  python3-aptdaemon.gtk3widgets python3-brlapi python3-chardet python3-commandnotfound python3-crypto
  python3-dbus python3-debian python3-defer python3-distupgrade python3-gdbm python3-gi python3-gnupg
  python3-httplib2 python3-louis python3-minimal python3-oauthlib python3-oneconf python3-packagekit
  python3-piston-mini-client python3-pkg-resources python3-problem-report python3-pyatspi python3-pykde4
  python3-pyqt4 python3-sip python3-six python3-software-properties python3-speechd python3-uno
  python3-update-manager python3-xdg python3-xkit python3.3 python3.3-minimal qapt-batch qasconfig qashctl
  qasmixer qdbus qjackctl qmenumodel-qml qmidiarp qmidinet qmidiroute qpdf qsynth qt-assistant-compat
  qtchooser qtdeclarative5-accounts-plugin qtdeclarative5-dee-plugin qtdeclarative5-folderlistmodel-plugin
  qtdeclarative5-gsettings1.0 qtdeclarative5-qtfeedback-plugin qtdeclarative5-qtmultimedia-plugin
  qtdeclarative5-qtquick2-plugin qtdeclarative5-systeminfo-plugin qtdeclarative5-ubuntu-content0.1
  qtdeclarative5-ubuntu-ui-toolkit-plugin qtdeclarative5-unity-action-plugin
  qtdeclarative5-unity-notifications-plugin qtdeclarative5-window-plugin qtdeclarative5-xmllistmodel-plugin
  qtoctave qtractor radeontool rakarrack rapid-photo-downloader rarian-compat rawtherapee rdesktop
  readline-common recordmydesktop redshift resolvconf rfkill ristretto rpm rpm-common rpm2cpio rsync
  rsyslog rtkit rubberband-cli rubberband-ladspa ruby ruby1.9.1 samba samba-common samba-common-bin
  sane-utils scidavis screenlets screenlets-pack-basic screensaver-default-images scribus sdparm sed
  session-migration sessioninstaller setserial sgml-base sgml-data shared-mime-info shimmer-themes shotwell
  shotwell-common signon-keyring-extension signon-plugin-oauth2 signon-ui signond simple-scan skype:i386
  smartmontools smartpm smartpm-core smb4k smbclient software-center software-center-aptdaemon-plugins
  software-properties-common software-properties-gtk software-properties-kde sooperlooper soprano-daemon
  sox spacetheremin specimen sqlite3 ssh-askpass-gnome ssl-cert steam-launcher stk strace subtitleeditor
  sudo swh-lv2 swh-plugins synaptic synfigstudio syslinux syslinux-legacy syslinux-themes-debian
  syslinux-themes-debian-wheezy system-config-printer-common system-config-printer-gnome
  system-config-printer-udev system-config-samba system-image-common system-image-dbus
  system-tools-backends systemd-services systemd-shim sysv-rc sysvinit-utils t1-cyrillic t1-oldslavic
  t1-teams t1-xfree86-nonfree t1utils tap-plugins tar tcl tcl-lib tcl8.4 tcl8.5 tcl8.5-lib tcpd tcpdump
  tdb-tools telnet tex-common tex-gyre texinfo texlive-base texlive-binaries texlive-extra-utils
  texlive-font-utils texlive-fonts-recommended texlive-fonts-recommended-doc texlive-generic-extra
  texlive-generic-recommended texlive-latex-base texlive-latex-base-doc texlive-latex-extra
  texlive-latex-extra-doc texlive-latex-recommended texlive-latex-recommended-doc texlive-luatex
  texlive-pictures texlive-pictures-doc texlive-pstricks texlive-pstricks-doc texlive-science
  texlive-science-doc thunar thunar-archive-plugin thunar-media-tags-plugin thunar-volman thunderbird time
  tipa tk tk-lib tk8.4 tk8.5 tk8.5-lib toshset totem totem-common totem-mozilla totem-plugins transcode
  transmission-gtk transmission-qt ttf-atarismall ttf-georgewilliams ttf-goudybookletter ttf-isabella
  ttf-lyx ttf-mscorefonts-installer ttf-radisnoir ttf-sjfonts ttf-staypuft ttf-tiresias ttf-tomsontalks
  ttf-xfree86-nonfree ttf-xfree86-nonfree-syriac tumbler tuxguitar tuxguitar-alsa tuxguitar-jack
  tuxguitar-oss twolame tzdata tzdata-java ubuntu-download-manager ubuntu-drivers-common
  ubuntu-extras-keyring ubuntu-keyboard-data ubuntu-minimal ubuntu-release-upgrader-core
  ubuntu-release-upgrader-gtk ubuntu-settings ubuntu-sso-client ubuntu-standard ubuntu-system-service
  ubuntu-system-settings ubuntu-system-settings-online-accounts ubuntu-ui-toolkit-theme ubuntustudio-audio
  ubuntustudio-audio-plugins ubuntustudio-default-settings ubuntustudio-desktop ubuntustudio-font-meta
  ubuntustudio-graphics ubuntustudio-installer ubuntustudio-lightdm-theme ubuntustudio-look
  ubuntustudio-menu ubuntustudio-photography ubuntustudio-publishing ubuntustudio-video ucf udev udisks
  udisks2 ufw unattended-upgrades unetbootin unity-asset-pool unity-lens-applications unity-lens-friends
  unity-scope-gdrive unity-scope-home unity-scope-musicstores unity-scope-video-remote unity-services
  unity-webapps-service unity8 unity8-fake-env unity8-private unixodbc uno-libs3 unrar unzip update-inetd
  update-java update-manager update-manager-core update-notifier update-notifier-common upower upstart ure
  ureadahead usb-creator-common usb-creator-gtk usb-modeswitch usb-modeswitch-data usbmuxd usbutils
  usermetricsservice util-linux uuid-runtime vainfo vbetool vendetta-online vim-common vim-tiny vinagre
  virtualbox virtualbox-dkms virtualbox-qt virtuoso-minimal virtuoso-opensource-6.1-bin
  virtuoso-opensource-6.1-common vkeybd vlc vlc-data vlc-nox vlc-plugin-notify vlc-plugin-pulse vocproc
  vorbis-tools wah-plugins wallch wamerican wbritish wget whiptail whoopsie-preferences whysynth wifi-radar
  winbind wine-gecko1.4 wine-gecko1.4:i386 wine1.4 wine1.4-amd64 wine1.4-i386:i386 winetricks winusb
  wireless-tools wodim wpasupplicant wpolish wxmaxima x11-apps x11-common x11-session-utils x11-utils
  x11-xfs-utils x11-xkb-utils x11-xserver-utils xauth xcftools xchat xchat-common xchat-indicator xcrysden
  xdg-user-dirs xfce4-appfinder xfce4-cpugraph-plugin xfce4-dict xfce4-fsguard-plugin
  xfce4-indicator-plugin xfce4-mailwatch-plugin xfce4-mixer xfce4-mount-plugin xfce4-netload-plugin
  xfce4-notes xfce4-notes-plugin xfce4-notifyd xfce4-panel xfce4-places-plugin xfce4-power-manager
  xfce4-quicklauncher-plugin xfce4-screenshooter xfce4-session xfce4-settings xfce4-smartbookmark-plugin
  xfce4-systemload-plugin xfce4-taskmanager xfce4-terminal xfce4-verve-plugin xfce4-volumed
  xfce4-weather-plugin xfconf xfdesktop4 xfonts-base xfonts-encodings xfonts-mathml xfonts-scalable
  xfonts-utils xfwm4 xine-ui xinit xinput xjadeo xml-core xorg xscreensaver xscreensaver-data
  xscreensaver-gl xserver-common xserver-xorg xserver-xorg-core xserver-xorg-glamoregl
  xserver-xorg-input-all xserver-xorg-input-evdev xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-ati
  xserver-xorg-video-cirrus xserver-xorg-video-fbdev xserver-xorg-video-intel xserver-xorg-video-mach64
  xserver-xorg-video-mga xserver-xorg-video-modesetting xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-openchrome xserver-xorg-video-qxl xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-s3 xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis xserver-xorg-video-sisusb xserver-xorg-video-tdfx
  xserver-xorg-video-trident xserver-xorg-video-vesa xserver-xorg-video-vmware xsynth-dssi xterm
  xul-ext-ubufox xz-utils yelp yoshimi zeitgeist zeitgeist-core zeitgeist-datahub zenity zip zita-ajbridge
  zita-at1 zlib1g zlib1g:i386 zlib1g-dev zynjacku
The following NEW packages will be installed:
  gcc-4.8-base gcc-4.8-base:i386
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  apt libapt-pkg4.12 (due to apt) libc6 (due to apt) libgcc1 (due to apt) libstdc++6 (due to apt) gnupg
  (due to apt) base-files base-passwd bash debianutils (due to bash) dash (due to bash) libtinfo5 (due to
  bash) bsdutils coreutils libacl1 (due to coreutils) libattr1 (due to coreutils) libselinux1 (due to
  coreutils) dpkg (due to dash) diffutils libbz2-1.0 (due to dpkg) liblzma5 (due to dpkg) zlib1g (due to
  dpkg) tar (due to dpkg) e2fsprogs e2fslibs (due to e2fsprogs) libblkid1 (due to e2fsprogs) libcomerr2
  (due to e2fsprogs) libss2 (due to e2fsprogs) libuuid1 (due to e2fsprogs) util-linux (due to e2fsprogs)
  findutils grep install-info (due to grep) gzip hostname sysv-rc (due to hostname) libc-bin libcap2 (due
  to libc-bin) login libpam0g (due to login) libpam-runtime (due to login) libpam-modules (due to login)
  mount libmount1 (due to mount) ncurses-bin perl-base sed tzdata (due to util-linux) debconf (due to
  util-linux) libncurses5 (due to util-linux) libslang2 (due to util-linux)
0 upgraded, 2 newly installed, 2830 to remove and 3 not upgraded.
Need to get 33.4 kB of archives.
After this operation, 6951 MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
```

How can i repair this ?

---

### Post by westie457 on 2014-02-23
What were you trying to install to cause this and can you post the original errors please.

ps Welcome to the Forum

---

