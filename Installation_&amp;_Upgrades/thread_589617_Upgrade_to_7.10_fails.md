---
title: "Upgrade to 7.10 fails"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by vasiliymeshko on 2007-10-24
When I try to upgrade to 7.10 the process fails and I get the following error saying that upgrade has terminated unexpectedly:

"Please report this as a bug (if you haven't already) and include the files /var/log/dist-upgrade/main.log and /var/log/dist-upgrade/apt.log in your report. The upgrade aborts now.
Your original sources.list was saved in /etc/apt/sources.list.distUpgrade."

Here are the file contents of /var/log/dist-upgrade/main.log

```

2007-10-24 08:10:27,061 INFO release-upgrader version '0.81' started
2007-10-24 08:10:29,897 DEBUG lsb-release: 'feisty'
2007-10-24 08:10:29,898 DEBUG _pythonSymlinkCheck run
2007-10-24 08:10:30,834 DEBUG checkViewDepends()
2007-10-24 08:10:33,104 DEBUG Foreign: 
2007-10-24 08:10:33,104 DEBUG Obsolete: kaffeine-xine libdvdcss2 libk3b2 libavcodec0d libavformat0d amarok w32codecs frostwire kaffeine libpostproc0d k3b libk3b2-mp3 amarok-xine
2007-10-24 08:10:33,106 DEBUG updateSourcesList()
2007-10-24 08:10:33,246 DEBUG rewriteSourcesList()
2007-10-24 08:10:33,250 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted'
2007-10-24 08:10:33,250 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted' updated to new dist
2007-10-24 08:10:33,250 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted'
2007-10-24 08:10:33,251 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted' updated to new dist
2007-10-24 08:10:33,251 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted'
2007-10-24 08:10:33,251 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted' updated to new dist
2007-10-24 08:10:33,251 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted'
2007-10-24 08:10:33,251 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted' updated to new dist
2007-10-24 08:10:33,251 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ feisty universe'
2007-10-24 08:10:33,252 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe' updated to new dist
2007-10-24 08:10:33,252 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe'
2007-10-24 08:10:33,252 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe' updated to new dist
2007-10-24 08:10:33,252 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse'
2007-10-24 08:10:33,252 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse' updated to new dist
2007-10-24 08:10:33,252 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse'
2007-10-24 08:10:33,253 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse' updated to new dist
2007-10-24 08:10:33,253 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu feisty-security main restricted'
2007-10-24 08:10:33,253 DEBUG entry 'deb http://security.ubuntu.com/ubuntu gutsy-security main restricted' updated to new dist
2007-10-24 08:10:33,253 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted'
2007-10-24 08:10:33,253 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted' updated to new dist
2007-10-24 08:10:33,253 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu feisty-security universe'
2007-10-24 08:10:33,253 DEBUG entry 'deb http://security.ubuntu.com/ubuntu gutsy-security universe' updated to new dist
2007-10-24 08:10:33,254 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu feisty-security universe'
2007-10-24 08:10:33,254 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu gutsy-security universe' updated to new dist
2007-10-24 08:10:33,254 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu feisty-security multiverse'
2007-10-24 08:10:33,254 DEBUG entry 'deb http://security.ubuntu.com/ubuntu gutsy-security multiverse' updated to new dist
2007-10-24 08:10:33,254 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse'
2007-10-24 08:10:33,254 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse' updated to new dist
2007-10-24 08:11:00,974 DEBUG demoted: 'binfmt-support feisty-session-splashes gcj-4.1-base gij-4.1 gnome-cups-manager gxine kitchensync libgcj7-jar libgda2-3 libgda2-common libglib1.2 libgnomecupsui1.0-1c2a libgtk1.2 libgtk1.2-common libjasper-runtime liblzo1 libportaudio0 libslab0 libstlport5.1 openoffice.org-filter-mobiledev pmount ttf-baekmuk vnc-common xarchiver xfce4-taskmanager xvncviewer'
2007-10-24 08:11:54,634 DEBUG Removing 'xscreensaver' (ubuntu-desktop PostUpgradeRemove rule)
2007-10-24 08:11:54,766 DEBUG Removing 'gnome-cups-manager' (ubuntu-desktop PostUpgradeRemove rule)
2007-10-24 08:11:54,899 DEBUG Purging 'xorg-common' (Distro PostUpgradePurge rule)
2007-10-24 08:11:54,899 DEBUG Purging 'libgl1-mesa' (Distro PostUpgradePurge rule)
2007-10-24 08:11:54,900 DEBUG Purging 'ltsp-client' (Distro PostUpgradePurge rule)
2007-10-24 08:11:55,030 DEBUG Purging 'ltspfsd' (Distro PostUpgradePurge rule)
2007-10-24 08:11:55,159 DEBUG Purging 'python2.3' (Distro PostUpgradePurge rule)
2007-10-24 08:11:55,159 DEBUG running gutsyQuirks handler
2007-10-24 08:11:55,160 DEBUG Kernel uname: '2.6.20-16-generic' 
2007-10-24 08:11:55,429 DEBUG Marking 'ubuntu-desktop' for upgrade
2007-10-24 08:11:55,558 DEBUG Marking 'kubuntu-desktop' for upgrade
2007-10-24 08:11:55,687 DEBUG Marking 'xubuntu-desktop' for upgrade
2007-10-24 08:11:56,730 DEBUG About to apply the following changes
2007-10-24 08:11:56,935 DEBUG Held-back: 
2007-10-24 08:11:56,935 DEBUG Remove: compiz-gtk libglew1 libgmpxx4 libopal-2.2.0 thunar-volman-plugin gnome-cups-manager libwnck18 libgnome-speech3 libmtp5 dbus-1-utils libuniconf4.2 xscreensaver digikamimageplugins human-cursors-theme totem-gstreamer libnss3 thunar-doc libkexiv2-0 libexiv2-0.12 libgcj7-awt qobex
2007-10-24 08:11:56,936 DEBUG Install: bluez-gnome libsidplay2 splix gtkhtml3.8 libsdl-ttf2.0-0 fast-user-switch-applet libtotem-plparser7 libgnome-vfs2.0-cil libgconf2-ruby1.8 xfce4-places-plugin libdevmapper1.02.1 libavutil1d libgcj7-1 libpth20 libx264-54 libtrackerclient0 o3read thunderbird libavformat1d libcompizconfig-backend-gconf network-manager-kde liblwres30 linux-restricted-modules-2.6.22-14-generic libgtksourceview2.0-common libwnck22 libjasper1 python-sexy ttf-dejavu-extra python-qt4-dbus libdb4.5 xdg-user-dirs libgda3-common libglew1.4 libgcj7-1-awt gcc-4.2-base pidgin-data libwpg-0.1-1 restricted-manager-core libnss3-0d dolphin libpurple0 discover1 totem-xine gcj-4.2 librpc-xml-perl libquicktime1 libgdk-pixbuf2-ruby1.8 xresprobe discover1-data gij-4.2 libatk1-ruby1.8 libode0debian1 libcluceneindex0 linux-image-2.6.22-14-generic gnupg-agent liblink-grammar4 libecj-java-gcj libwvstreams4.3-extras linux-headers-2.6.22-14 gutsy-wallpapers libxcb-shm0 libgoffice-gtk-0-4 pidgin libatm1 libalut0 xserver-xorg-video-amd libsidutils0 foomatic-db-gutenprint libiw29 libgs8 ttf-indic-fonts-core ubufox librsvg2.0-cil libsnmp10 libxcb-shape0 libneon26 libebml0 update-notifier-common kdesudo tracker libpqxx-2.6.9 libjack0 pxljr libisc32 libdeskbar-tracker libglib2-ruby1.8 dbus-x11 guidance-backends gcc-4.2 linux-headers-2.6.22-14-generic libxapian15 libwvstreams4.3-base python-pygtksourceview libisccfg30 xvnc4viewer libpam-gnome-keyring libpango1-ruby1.8 hplip-gui libkeyutils1 libxcb1 libboost-signals1.34.1 libflac++6 libresid-builder0c2a apturl libaprutil1 libgtkhtml2.0-cil libgnome-speech7 libopenspc0 libexiv2-0 libpostproc1d libcompizconfig0 libgpod2 libgsf-gnome-1-114 liblzo2-2 libsvg1 compiz-fusion-plugins-extra libstreams0 cpp-4.2 kio-umountwrapper libservlet2.4-java libkdcraw1 libmtp6 tracker-search-tool thunar-volman libxcb-xv0 libmatroska0 libzephyr3 xdg-utils libmozjs0d libpaper-utils libpcrecpp0 libterm-readkey-perl xdg-user-dirs-gtk kvkbd gdebi-kde brasero libgcj8-1 thunar-data strigi-daemon xserver-xorg-video-psb libgmpxx4ldbl gcj-4.2-base ttf-unfonts-core tcpd librarian0 libart2.0-cil compiz-fusion-plugins-main libuniconf4.3 strigi-applet displayconfig-gtk xserver-xorg-video-intel libtracker-gtk0 libkbluetooth0 pinentry-qt libgcj8-1-awt libstrigihtmlgui0 consolekit apparmor libapr1 libgda3-3 libntfs-3g12 link-grammar-dictionaries-en linux-ubuntu-modules-2.6.22-14-generic libnspr4-0d libijs-0.35 libgcj8-dev libopal-2.2 libdiscover1 libopensync0 libksba8 libglade2-ruby1.8 libept0 libgomp1 libdns32 libpoppler-qt2 gtk2-engines-murrine hal-info libgtk2-ruby1.8 libisccc30 libstreamanalyzer0 libgdl-gnome-1-0 libkexiv2-1 ttf-dejavu-core libpoppler2 restricted-manager-kde ghostscript libgcj8-jar libavcodec1d cups-pdf libpoppler-glib2 ijsgutenprint xfdesktop4-data apparmor-utils libflac8 libsvn1 libgtksourceview2.0-0 libhesiod0 libsearchclient0 gpgsm libbind9-30 ghostscript-x libecj-java dmz-cursor-theme
2007-10-24 08:11:56,936 DEBUG Upgrade: libbz2-1.0 libsane gnome-terminal hal libcairo-ruby1.8 esound-common planetpenguin-racer-data kwalletmanager wvdial iukrainian python2.5-minimal libqt4-sql kivio konqueror-nsplugins libapm1 xserver-xorg-video-rendition kmailcvt base-files kdeprint smartdimmer libglu1-mesa xserver-xorg-video-vesa net-tools msttcorefonts libclan2c2a-gui libgtk2.0-bin libcupsimage2 listres xserver-xorg-video-sis gnome-applets-data gparted libjasper-runtime grub udev libmono-system1.0-cil libfaad2-0 dhcdbd python-launchpad-bugs kdemultimedia-kio-plugins volumeid xauth libatk1-ruby unixodbc readahead util-linux-locales gnome-applets libegroupwise1.2-13 libk3b2 libc6-dev libuuid1 python-all-dev libgksu2-0 wpasupplicant libgcj7-dev libungif4g libmono-system-web2.0-cil libmono-system2.0-cil libxtrap6 gqview libgnatprj4.1 libss2 libgnomecanvas2-0 libgmp3c2 jackd xsane-common totem libgmp3-dev libofa0 libxfce4mcs-client3 powermanagement-interface kpdf info gstreamer0.10-plugins-bad python-gtk2 libktnef1 libbrlapi1 cvs openoffice.org-evolution libkpathsea4 libsasl2-2 gtk2-engines login compiz-plugins dvd+rw-tools libgmime2.2-cil libgcrypt11 kmag libatk1.0-0 bzip2 libglib2.0-cil libwrap0 koshell libkcal2b cdparanoia hplip-data xclock xdpyinfo gnome-media qt4-qtconfig launchpad-integration python-kde3 restricted-manager p7zip-full xfce4-weather-plugin sword-text-arasvd libxres1 libkpimidentities1 libnotify1 kmplayer-base upstart-logd librecode0 brltty libthai-data docbook-xml hwdb-client-gnome libguile-ltdl-1 libxrender1 kdenetwork-kfile-plugins libice6 libicu36 libltdl3-dev libsqlite3-0 python-vte liblircclient0 xserver-xorg mozilla-thunderbird tzdata im-switch language-pack-kde-uk-base openoffice.org-base libmimelib1c2a fftw3 ssh-askpass-gnome libgnome2-common kdepim-wizards libxine1-ffmpeg libxplc0.3.13 libgnome2-0 libnm-util0 ubuntu-restricted-extras python-gnomecanvas kubuntu-konqueror-shortcuts gtk2-engines-xfce libwnck-common apport-gtk libgphoto2-2 gobjc netcat kcontrol kaffeine ruby1.8 libkcddb1 libexpat1 bluez-utils language-pack-gnome-uk kubuntu-default-settings exiv2 libwv2-1c2 libgdome2-0 xf86dga xsm gnome-games nautilus-open-terminal python-gtkhtml2 koffice-data kbstate libgucharmap6 kde-systemsettings xfwm4-themes scim-modules-socket libusb-0.1-4 python2.4-minimal wodim libpam-foreground gstreamer0.10-gnomevfs gnome-system-monitor linux-restricted-modules-common e2fslibs kpresenter gnome-terminal-data khelpcenter xserver-xorg-video-siliconmotion human-theme gnome-doc-utils zoo libqt4-qt3support language-selector kdebase-bin xfce4-mount-plugin ifupdown hpijs ttf-tamil-fonts libscrollkeeper0 libdb4.3 libdb4.2 libdb4.4 xubuntu-desktop xmodmap upstart-compat-sysv kdevelop-doc kspread libncurses5 anthy procps python-central libclan2c2a-png librsvg2-common gettext-base gnome-panel-data notification-daemon perl-modules libxfcegui4-4 g77-3.4 libtagc0 xfce4-clipman-plugin p7zip python-gdbm cupsys-client gstreamer0.10-plugins-good kword passwd fontconfig kopete libmetacity0 coreutils libclanlib2c2a libgsf-1-114 ca-certificates iputils-tracepath xhost gnome-volume-manager gconf2-common kugar libxml2-utils python-sip4 libgcj-bc xfce4-session xserver-xorg-video-apm libsmokeqt1 dselect libxi6 nautilus-sendto libxfce4util4 elinks libldap2 libglib-perl bsdmainutils libebook1.2-9 locales xfwm4 xfprint4 gstreamer0.10-alsa libclan2c2a-vorbis libpam-modules libgpmg1 gnome-screensaver libjpeg62 openoffice.org-writer language-pack-gnome-en foomatic-filters libaiksaurusgtk-1.2-0c2a libwpd-stream8c2a python-notify libsdl-image1.2 mysql-common python-glade2 finger python2.5-dev libaspell15 kpresenter-data libbeagle0 libgtksourceview1.0-0 gnome-user-guide evolution-common autoconf update-manager libkonq4 gobjc++-4.1 smproxy scim-hangul ppp libbluetooth2 cupsys-bsd libxerces2-java kdenetwork-filesharing libpcre3 dictionaries-common gcj-4.1 ksmserver xmore gnome-pilot initramfs-tools iso-codes gpc-2.1-3.4 xrgb xgamma lisa xserver-xorg-video-savage kde-guidance postfix python-elementtree xserver-xorg-input-evdev gpgv gpc binutils-static compiz-core gsfonts liboil0.3 gij-4.1 gnome-netstatus-applet gnome-orca gnome-splashscreen-manager feisty-gdm-themes dhcp3-common libxcursor1 libglade2.0-cil xml-core libxext6 apt libgnomevfs2-extra abiword-common aspell scim-qtimm odbcinst1debian1 ktorrent ubuntu-artwork sysv-rc g++ libmeanwhile1 libgnome-media0 rpm libsigc++-2.0-0c2a libsm6 libthunar-vfs-1-2 libclucene0 libexif12 x11-common libx11-data xconsole xwud doc-base kscreensaver whiptail konq-plugins linux-libc-dev netbase librsync1 kdebase-data gnome-games-data thunar-media-tags-plugin zlib1g-dev gnome-utils genisoimage gstreamer0.10-plugins-bad-multiverse libxml-twig-perl ksystemlog gnome-art hwdb-client-common kubuntu-docs libpvm3 libpythonize0 xman xmag libgdiplus libbonobo2-0 libxau6 knode libgutenprint2 debianutils cpp libmono-cairo1.0-cil libmysqlclient15off libjline-java koffice kexi latex-xft-fonts gamin vim-runtime libgnutls13 libparted1.7-1 sed openoffice.org-thesaurus-en-us libnewt0.52 linux-image-generic kaddressbook libkmime2 unzip gstreamer0.10-esd bogofilter gcalctool debconf-i18n libbonoboui2-common libsamplerate0 python kpf libsasl2-modules libavahi-core5 libpng12-0 thunderbird-locale-en-gb libesd-alsa0 python-bittorrent ttf-gujarati-fonts gnome-menus konqueror abiword-help libx11-6 libmono-sqlite2.0-cil mono-common libndesk-dbus-glib1.0-cil acpi-support libxfont1 libqt3-mt gcc-3.4 python-xml libsmpeg0 cpp-4.1 findutils openoffice.org-l10n-en-gb libdc1394-13 module-init-tools gtk2-engines-pixbuf tcpdump libclan2c2a-sound libgcc1 libwxgtk2.6-0 amarok-xine gstreamer0.10-ffmpeg libopencdk8 ed libcurl3 libgdl-1-common libaiksaurus-1.2-data kchart ubuntu-standard libedata-book1.2-2 apport dosfstools klogd dnsutils kontact libmp4v2-0 adept-manager totem-mozilla cmus evolution-exchange libcdaudio1 libraw1394-8 bash libgnatvsn4.1 gedit karm python-problem-report libhtml-tree-perl python-gnupginterface xserver-xorg-video-glint liburi-perl libgdome2-cpp-smart0c2a freeglut3 libpcap0.8 xkb-data xterm libxml-parser-perl libchm1 firefox-gnome-support fastjar xserver-xorg-input-kbd belocs-locales-bin alsa-utils sudo libasound2 libgstreamer0.10-0 klibc-utils libhal-storage1 acpid libgnome2.0-cil mono-runtime ecj keep gcj-4.1-base eject libmpcdec3 python-apport libgnomekbdui1 libmdbtools evolution libmono-system-data2.0-cil kivio-data myspell-uk laptop-detect gnat-4.1 linux-headers-generic mono-gac libxevie1 xserver-xorg-video-voodoo kipi-plugins brltty-x11 usplash-theme-ubuntu libgdl-1-0 libgnomekbd-common appres gnupg knotes xwininfo dash ttf-oriya-fonts gnomesword libavahi-common-data libglibmm-2.4-1c2a libcucul0 skim gnome-control-center perl-suid libsmbclient libtasn1-3 kubuntu-artwork-usplash libots0 python-tk libwpd8c2a vorbis-tools libatspi1.0-0 xfce4-utils lsb-release libgnomekbd1 whois xfce4-battery-plugin ttf-punjabi-fonts toshset libxmu6 flashplugin-nonfree xfce4-appfinder arts kdevelop libmono-sharpzip2.84-cil cupsys-common ttf-dejavu libdbus-glib-1-2 xfce4-mixer-alsa audacity rss-glx xfce4-fsguard-plugin inputattach sun-java6-jre language-pack-uk-base ttf-devanagari-fonts libid3tag0 debtags gnome-panel libgail-gnome-module cdrdao xsetmode libcamel1.2-10 iputils-arping libtiff4 libssl0.9.8 xditview xfonts-encodings apmd python-minimal liba52-0.7.4 system-services gcc-4.1 ncurses-base sound-juicer linux-sound-base libt1-5 software-properties-gtk debconf at-spi libgnomeprint2.2-0 adept-installer gnome-system-tools tcl8.4 libavahi-client3 xserver-xorg-video-ark libstdc++6-4.1-dev libgtkhtml2-0 gcc-3.4-base ksysguardd python-launchpad-integration ntfs-3g m4 mc libexo-0.3-0 kscreensaver-xsavers xserver-xorg-video-tga libhsqldb-java xserver-xorg-video-newport libgtk2-ruby ttf-indic-fonts knetworkmanager hplip amarok libxdamage1 apt-utils linux-restricted-modules-generic xlsatoms ico ttf-freefont libusplash0 librsvg2-2 command-not-found-data libieee1284-3 libgstreamer-plugins-base0.10-0 gstreamer0.10-x libnautilus-burn4 gnome-mag libpango1.0-0 libncursesw5 psfontmgr gnome-session python-dbus kdepasswd libarts1c2a libsepol1 python-all kppp libobjc1 karbon scribus avahi-autoipd koffice-doc-html unattended-upgrades perl-base command-not-found libavahi-common3 libxrandr2 libexchange-storage1.2-3 libwavpack1 update-notifier ttf-malayalam-fonts xmoto kmenuedit libpaper1 alacarte bogofilter-bdb kmilo gnome-accessibility-themes openoffice.org-draw viewres libx86-1 xpmutils libcairomm-1.0-1 libmad0 libkpimexchange1 libgoffice-0-common fuse-utils xlogo wukrainian mktemp libdecoration0 xsetpointer slocate kcron libmjpegtools0c2a console-cyrillic esound python-exo myspell-en-gb libdvdread3 libpisock9 krusader scim gnome-cards-data pmount scim-pinyin libgtk2.0-cil bloboats sun-java6-plugin ubuntu-docs libscim8c2a libfreetype6 memtest86+ xeyes language-selector-qt sox fortunes-min xbase-clients ethtool libltdl3 system-config-printer xvinfo xserver-xorg-video-s3 liborbit2 libnl1-pre6 libxklavier11 screen libnautilus-extension1 libselinux1 libgconf2-4 libgtkhtml3.14-19 gedit-common samba-common ssl-cert libxinerama1 libopenal0a xfontsel libkleopatra1 libxaw7 openoffice.org-java-common xserver-xorg-input-wacom dpkg kdepim-kresources ttf-arphic-uming libgnomevfs2-bin python-gnome2-desktop libgnome-desktop-2 imagemagick adept-notifier binutils build-essential xlsclients libpulse0 console-terminus readline-common libnet-dbus-perl python-dev python-cairo libdbus-1-3 xcalc libgtk2.0-common libgmime-2.0-2 xfce4-icon-theme kword-data mesa-utils libncurses5-dev kfind libcurl3-gnutls libxpm4 libdirectfb-0.9-25 ucf libavahi-compat-libdnssd1 xfce4-notes-plugin xfce4-terminal gdebi-core kooka rdiff-backup libdv4 java-common xsltproc libopenobex1 katapult ispell kde-icons-mono libjpeg-progs gnome-mime-data language-pack-kde-uk xgc scim-modules-table gstreamer0.10-pitfdll myspell-en-za gstreamer0.10-plugins-ugly libidl0 evolution-webcal libmagic1 python-gnome2 kmix mousepad ksvg libg2c0 mkisofs gconf2 libsword6 ekiga librpm4 python-gobject konsole cupsys-driver-gutenprint poppler-utils xserver-xorg-video-via zenity libstlport5.1 libgphoto2-port0 python-cups libxtst6 openoffice.org-filter-mobiledev vnc-common scim-chewing nano capplets-data libruby1.8 nautilus libxvmc1 openoffice.org-l10n-en-us xfce4-cpugraph-plugin kde-guidance-powermanager xutils guile-1.6-libs libskim0 apport-qt libmusicbrainz4c2a libgsf-1-common korganizer gs-gpl kdepim-kio-plugins libcdparanoia0 kate openoffice.org-calc libgsl0 gnome-themes kio-apt gstreamer0.10-gl xubuntu-docs libsdl1.2debian libaiksaurus-1.2-0c2a xfdesktop4 kde-i18n-uk alsa-base ubuntu-minimal xmoto-data xserver-xorg-video-i128 g77 libavahi-glib1 kformula libgpgme11 feisty-wallpapers libsensors3 gksu evolution-data-server-common compiz software-properties-kde libbonobo2-common pingus gnome-desktop-data libedit2 gwenview openoffice.org-style-human vlc-nox xserver-xorg-video-nv libgnome-keyring0 libqthreads-12 zlib1g liboobs-1-3 hwdb-client-kde kdevelop-data libcomerr2 evolution-data-server foomatic-db-hpijs libjack0.100.0-0 xwd libxss1 espeak-data acpi xfce4-verve-plugin libkscan1 libfontconfig1 libart-2.0-2 k3b libgcj-common util-linux libgconf2.0-cil kaffeine-xine libmodplug0c2 libsdl-mixer1.2 metacity-common gtkhtml3.14 xfce4-netload-plugin libgnomevfs2-common file konversation makedev openoffice.org-math kitchensync sun-java6-bin xserver-xorg-video-all python-virtkey pciutils kdeadmin-kfile-plugins mono-jit libarts1-akode desktop-file-utils aspell-uk libksieve0 krdc openoffice.org-impress libakode2 language-pack-gnome-uk-base gthumb libecal1.2-7 cpp-3.4 vlc libc6-i686 python2.5 python2.4 linux-generic gnome-nettool moc-ffmpeg-plugin libgtop2-7 hal-device-manager libsqlite0 kghostview libxfixes3 libxt6 dbus krita xfburn libgail18 xfce4-mcs-plugins sane-utils xutils-dev ksnapshot gnome-icon-theme libgnome-window-settings1 xchm myspell-en-us kplato sysvutils gobjc++ ltrace cupsys mcpp libwxbase2.6-0 python-numeric compiz-gnome adept-updater parted xvidtune ksysguard kmail xserver-xorg-video-ati bsh libvte-common f-spot transcode-doc openoffice.org-l10n-uk libxfce4mcs-manager3 gnumeric-common libgtkmathview0c2a libaa1 gij libslang2 xserver-xorg-video-nsc libkdepim1a xmessage gs-esp xorg python-gst0.10 ttf-telugu-fonts psmisc abiword-plugins openoffice.org-gnome fontconfig-config xload openoffice.org gstreamer0.10-plugins-base-apps x-ttcidfont-conf libvorbis0a xscreensaver-gl pppconfig krita-data libcairo-perl gnome-keyring mount rhythmbox liblcms1 libgtk2.0-0 libgnomeprintui2.2-common kamera libreadline5 xlsfonts akregator libxmuu1 xsane language-pack-gnome-en-base console-setup libmono-data-tds2.0-cil libgtop2-common gcc-4.1-base xfce4-mailwatch-plugin startup-tasks man-db python-libxml2 libgtkmm-2.4-1c2a gucharmap xfce4-screenshooter-plugin pkg-config xvncviewer busybox-initramfs libvorbisenc2 xkill tomboy libgnome-pilot2 tangerine-icon-theme mozilla-firefox-locale-en-gb libespeak1 libxkbfile1 scrollkeeper python-uno gnome-mount libmagick9 xfce4-mcs-manager thunar libtunepimp5 libgnat-4.1 networkstatus xrandr libartsc0 vim-tiny gaim nautilus-cd-burner tango-icon-theme mjpegtools kdm xubuntu-artwork-usplash initscripts liblaunchpad-integration0 libdrm2 xubuntu-default-settings libcairo-ruby gnome-power-manager bittorrent tsclient gstreamer0.10-plugins-base libgconf2-ruby libklibc libtdb1 binfmt-support diff gxine openoffice.org-help-en-gb libanthy0 gzip xfce4-quicklauncher-plugin hotkey-setup bind9-host sysklogd openssh-client libkipi0 update-inetd libgtkspell0 time gimp-python libxcomposite1 gnome-about gstreamer0.10-tools libpam-runtime libpango1.0-common libkrb53 gnumeric-gtk tasksel-data libportaudio2 libportaudio0 cli-common file-roller iproute python-eyed3 libg2c0-dev adept libcvsservice0 libhunspell-1.1-0 libxvidcore4 openoffice.org-kde libstdc++5 libstdc++6 manpages libpt-plugins-alsa gdb libqt4-gui gdm klipper libgpg-error0 kdnssd libedataserver1.2-9 e2fsprogs openoffice.org-l10n-common fortune-mod libglade2-0 libpt-plugins-v4l system-tools-backends kdegraphics-kfile-plugins liblocale-gettext-perl ftp orage wireless-tools python-pyorbit human-icon-theme rdesktop libeel2-2 upstart metacity bluez-cups popularity-contest laptop-mode-tools libedataserverui1.2-8 g++-4.1 wget kdebluetooth pykdeextensions nautilus-data firefox xserver-xorg-input-mouse app-install-data-commercial scim-anthy language-pack-uk libidn11 hdparm libgnome-menu2 libhal1 language-selector-common libxml2 iceauth vim-common less dmidecode libclan2c2a-mikmod kubuntu-desktop eog gtk2-engines-ubuntulooks python-gconf libglib2.0-data python-support libavahi-qt3-1 libglib2-ruby ntp libsdl1.2debian-alsa iputils-ping libmono-corlib1.0-cil libqt4-core iptables onboard libhtml-parser-perl libgnomecanvas2-common openoffice.org-common qca-tls toolame kmousetool usplash libgksuui1.0-1 xbitmaps tasksel gstreamer0.10-plugins-ugly-multiverse bogofilter-common gawk bug-buddy gcc-3.3-base openoffice.org-gtk gnome-btdownload dmsetup beforelight python-software-properties libpango1-ruby xfce4-mixer libsnmp-base xfce4-xkb-plugin kpersonalizer libblkid1 bitmap libthai0 espeak kdebase-kio-plugins libcap1 autotools-dev xrdb xserver-xorg-input-all libgtksourceview-common kthesaurus libcairo2 libgutenprintui2-1 gs-esp-x xserver-xorg-input-synaptics libgamin0 ttf-kannada-fonts gimp gconf-editor libgnome-mag2 libkjsembed1 gnome-media-common libelfg0 oclock libbonoboui2-0 xfce4-panel thunar-archive-plugin gimp-data gdebi lshw kdelibs4c2a kdelibs-data reiserfsprogs transcode shared-mime-info language-pack-en gnome-app-install planetpenguin-racer koffice-i18n-uk editres digikam ttf-opensymbol kregexpeditor libmms0 xarchiver xserver-xorg-video-i810 libxine1 ncurses-bin python2.4-dev network-manager libpq5 libmono2.0-cil libfontenc1 ubuntu-desktop libmono-corlib2.0-cil libgnomeprintui2.2-0 libpisync0 xserver-xorg-video-mga python-gnome2-extras speedcrunch xfce4-systemload-plugin kde-style-polyester mtr-tiny kwin libglade2-ruby base-passwd update-manager-core avahi-daemon contact-lookup-applet perl gnome-keyring-manager gs-common kmplayer-konq-plugins libwmf0.2-7 kdesktop libconsole libsysfs2 xstdcmap libgnomeui-common libxslt1.1 koffice-libs moc libswfdec0.3 libk3b2-mp3 ttf-arphic-ukai libgcj7-jar aptitude libgl1-mesa-glx libgdk-pixbuf2-ruby libgail-common xbiff libfuse2 libxalan2-java python-orca-brlapi tk8.4 libfreebob0 libdvdnav4 gnome-pilot-conduits libwps-0.1-1 vino libnss-mdns libaudio2 xserver-xorg-core openoffice.org-core libvlc0 openoffice.org-style-crystal libc6 serpentine adept-common dhcp3-client language-pack-en-base liblame0 libtool python-gmenu lftp foomatic-db hal-cups-utils network-manager-gnome libao2 gcc gcj pingus-data libgnomevfs2-0 libmono0 scribus-doc synaptic krfb xscreensaver-data python-qt3 python-qt4 libvolume-id0 strace gtk-qt-engine libdvbpsi4 xclipboard evince ksplash-engine-moodin libxv1 adept-batch foo2zjs pppoeconf yelp libcupsys2 xfd kicker libnm-glib0 libxft2 libpam0g libgimp2.0 adduser openprinting-ppds console-tools openssl ntpdate bsdutils libperl5.8 python-apt sessreg scim-tables-additional openoffice.org-help-en-us libclan2c2a-jpeg liblpint-bonobo0 libpanel-applet2-0 evolution-plugins ubuntu-keyring gnat-4.1-base libenchant1c2a libsndfile1 ttf-arabeyes libvte9 lsb-base libdjvulibre15 cpio libgnomeprint2.2-data smbclient libpt-plugins-v4l2 libgnomeui-0 rsync libeel2-data usbutils ttf-bengali-fonts openoffice.org-l10n-en-za libmono-security2.0-cil libcroco3 knetworkconf ttf-thai-tlwg libglib2.0-0 defoma ecj-gcj gimp-print ksplash libvorbisfile3 libopenexr2c2a arj ark pvm lsof scim-gtk2-immodule libpt-1.10.0 libtag1c2a deskbar-applet libcaca0 libgsm1 tar xserver-xorg-video-tseng kdemultimedia-kfile-plugins python-at-spi gobjc-4.1 libdaemon0 app-install-data cdrecord abiword foomatic-db-engine libedata-cal1.2-6 libsexy2 xsetroot libgl1-mesa-dri libxdmcp6 dpkg-dev
2007-10-24 08:11:56,939 DEBUG Free space on /: 52362493952
2007-10-24 08:11:56,939 DEBUG Dir /usr mounted on /
2007-10-24 08:11:56,939 DEBUG Dir /var mounted on /
2007-10-24 08:11:56,940 DEBUG Dir /boot mounted on /
2007-10-24 08:11:56,940 DEBUG Dir /var/cache/apt/archives mounted on /
2007-10-24 08:11:56,940 DEBUG Dir /home mounted on /
2007-10-24 08:11:56,940 DEBUG fs_free contains: '{'/var': <DistUpgradeControler.FreeSpace object at 0xa6562cc>, '/home': <DistUpgradeControler.FreeSpace object at 0xa6562cc>, '/boot': <DistUpgradeControler.FreeSpace object at 0xa6562cc>, '/usr': <DistUpgradeControler.FreeSpace object at 0xa6562cc>, '/': <DistUpgradeControler.FreeSpace object at 0xa6562cc>, '/var/cache/apt/archives': <DistUpgradeControler.FreeSpace object at 0xa6562cc>}'
2007-10-24 08:11:56,953 DEBUG linux-image-2.6.20-16-generic (upgrade|installed) added with 10485760 to boot space
2007-10-24 08:11:56,985 DEBUG linux-image-2.6.22-14-generic (new-install) added with 10485760 to boot space
2007-10-24 08:11:57,100 DEBUG linux-image-2.6.20-15-generic (upgrade|installed) added with 10485760 to boot space
2007-10-24 08:11:57,603 DEBUG dir '/var/cache/apt/archives' needs '1149969808.0' of '<DistUpgradeControler.FreeSpace object at 0xa6562cc>' (52362493952.000000)
2007-10-24 08:11:57,603 DEBUG dir '/usr' needs '657588224.0' of '<DistUpgradeControler.FreeSpace object at 0xa6562cc>' (51212524144.000000)
2007-10-24 08:11:57,603 DEBUG dir '/usr' needs '52428800' of '<DistUpgradeControler.FreeSpace object at 0xa6562cc>' (50554935920.000000)
2007-10-24 08:11:57,603 DEBUG dir '/boot' needs '31457280' of '<DistUpgradeControler.FreeSpace object at 0xa6562cc>' (50502507120.000000)
2007-10-24 08:11:57,604 DEBUG dir '/' needs '10485760' of '<DistUpgradeControler.FreeSpace object at 0xa6562cc>' (50471049840.000000)
2007-10-24 08:11:58,097 ERROR not handled expection:
Traceback (most recent call last):

  File "/tmp/tmpLTCxrc/gutsy", line 59, in <module>
    app.run()

  File "/tmp/tmpLTCxrc/DistUpgradeControler.py", line 1346, in run
    self.fullUpgrade()

  File "/tmp/tmpLTCxrc/DistUpgradeControler.py", line 1312, in fullUpgrade
    if not self.askDistUpgrade():

  File "/tmp/tmpLTCxrc/DistUpgradeControler.py", line 725, in askDistUpgrade
    self.cache.requiredDownload)

  File "/tmp/tmpLTCxrc/DistUpgradeViewGtk.py", line 550, in confirmChanges
    pkgs_remove) % pkgs_remove

TypeError: not all arguments converted during string formatting

2007-10-24 08:11:58,394 ERROR failed to import apport python module, can't report bug: No module named python_hook

```

..and here is /var/log/dist-upgrade/apt.log

```

gpgv: Signature made &#1087;&#1085;, 15-&#1078;&#1086;&#1074;-2007 19:24:30 -0400 EDT using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
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
Installing libhal-storage1 as dep of gnome-keyring
Installing libhal1 as dep of gnome-keyring
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
Installing libasound2 as dep of gstreamer0.10-alsa
Installing libgstreamer0.10-0 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing libdbus-glib-1-2 as dep of libgnomekbd1
Installing libgnomekbd-common as dep of libgnomekbd1
Installing libstdc++6 as dep of libwpd8c2a
Installing gcc-3.3-base as dep of libstdc++5
Installing libgmime2.2-cil as dep of tomboy
Installing perl as dep of libglib-perl
Installing perl-base as dep of perl
Installing perl-modules as dep of perl
Installing libbz2-1.0 as dep of bzip2
Installing libecal1.2-7 as dep of evolution-webcal
Installing libedataserver1.2-9 as dep of libecal1.2-7
Installing libnspr4-0d as dep of libedataserver1.2-9
Installing libebook1.2-9 as dep of ekiga
Installing libcamel1.2-10 as dep of libebook1.2-9
Installing libnss3-0d as dep of libcamel1.2-10
Installing libopal-2.2 as dep of ekiga
Installing libpt-1.10.0 as dep of libopal-2.2
Installing libssl0.9.8 as dep of libpt-1.10.0
Installing openoffice.org-core as dep of openoffice.org-gnome
Installing openoffice.org-common as dep of openoffice.org-core
Installing libcurl3-gnutls as dep of openoffice.org-core
Installing libdb4.5 as dep of openoffice.org-core
Installing libhunspell-1.1-0 as dep of openoffice.org-core
Installing libneon26 as dep of openoffice.org-core
Installing libgimp2.0 as dep of gimp-print
Installing libgutenprint2 as dep of gimp-print
Installing libgutenprintui2-1 as dep of gimp-print
Installing libjasper1 as dep of libmagick9
Installing libwnck22 as dep of notification-daemon
Installing libwnck-common as dep of libwnck22
Installing libgnomevfs2-common as dep of libgnomevfs2-0
Installing libatm1 as dep of iproute
Installing libgnomecanvas2-0 as dep of gthumb
Installing libgnomecanvas2-common as dep of libgnomecanvas2-0
Installing update-manager-core as dep of update-manager
Installing python-uno as dep of openoffice.org-writer
Installing libscim8c2a as dep of scim-modules-table
Installing gnome-media-common as dep of gnome-media
Installing libmetacity0 as dep of metacity
Installing metacity-common as dep of libmetacity0
Installing libbeagle0 as dep of nautilus
Installing librsvg2-2 as dep of nautilus
Installing libgsf-1-114 as dep of librsvg2-2
Installing libgsf-1-common as dep of libgsf-1-114
Installing libtrackerclient0 as dep of nautilus
Installing nautilus-data as dep of nautilus
Installing libgnome2-common as dep of libgnome2-0
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
Installing libncursesw5 as dep of aspell
Installing libaspell15 as dep of aspell
Installing dhcp3-common as dep of dhcp3-client
Installing libuniconf4.3 as dep of wvdial
Installing libwvstreams4.3-base as dep of libuniconf4.3
Installing libwvstreams4.3-extras as dep of libuniconf4.3
Installing xserver-xorg-video-amd as dep of xserver-xorg-video-all
Installing xserver-xorg-video-intel as dep of xserver-xorg-video-all
Installing xserver-xorg-video-psb as dep of xserver-xorg-video-all
Installing libdrm2 as dep of xserver-xorg-video-psb
Installing xsane-common as dep of xsane
Installing libgcj-common as dep of libgcj-bc
Installing libgcj8-1 as dep of libgcj-bc
Installing gcj-4.2-base as dep of libgcj8-1
Installing xdg-utils as dep of libdjvulibre15
Installing libiw29 as dep of wireless-tools
Installing samba-common as dep of smbclient
Installing libslang2 as dep of whiptail
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
Installing libgucharmap6 as dep of gucharmap
Installing brltty as dep of brltty-x11
Installing libdaemon0 as dep of avahi-daemon
Installing gnome-games-data as dep of gnome-games
Installing gnome-cards-data as dep of gnome-games-data
Installing gdebi-core as dep of gdebi
Installing python-apt as dep of gdebi-core
Installing apt-utils as dep of python-apt
Installing apt as dep of apt-utils
Installing python-central as dep of python-apt
Installing dpkg as dep of python-central
Installing evolution as dep of evolution-exchange
Installing libedataserverui1.2-8 as dep of evolution
Installing libegroupwise1.2-13 as dep of evolution
Installing libexchange-storage1.2-3 as dep of evolution
Installing libgtkhtml3.14-19 as dep of evolution
Installing evolution-data-server as dep of evolution
Installing libedata-book1.2-2 as dep of evolution-data-server
Installing libedata-cal1.2-6 as dep of evolution-data-server
Installing evolution-data-server-common as dep of evolution-data-server
Installing gcc-4.1 as dep of g++-4.1
Installing cpp-4.1 as dep of gcc-4.1
Installing libstdc++6-4.1-dev as dep of g++-4.1
Installing linux-image-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing linux-ubuntu-modules-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libgpod2 as dep of rhythmbox
Installing libmtp6 as dep of rhythmbox
Installing libmusicbrainz4c2a as dep of rhythmbox
Installing libtotem-plparser7 as dep of rhythmbox
Installing libgtksourceview2.0-0 as dep of gedit
Installing libgtksourceview2.0-common as dep of libgtksourceview2.0-0
Installing gedit-common as dep of gedit
Installing python-pygtksourceview as dep of gedit
Installing python-gmenu as dep of gnome-menus
Installing libbluetooth2 as dep of bluez-cups
Installing python-cups as dep of system-config-printer
Installing libsnmp10 as dep of hpijs
Installing libsnmp-base as dep of libsnmp10
Installing gutsy-wallpapers as dep of ubuntu-artwork
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
Installing capplets-data as dep of gnome-control-center
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing libsasl2-2 as dep of libsasl2-modules
Installing hplip-data as dep of hplip
Installing gconf2-common as dep of gconf2
Installing esound-common as dep of libesd-alsa0
Installing consolekit as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing fast-user-switch-applet as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing ghostscript-x as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing ghostscript as dep of ghostscript-x
Installing libgs8 as dep of ghostscript
Installing libcupsimage2 as dep of libgs8
Installing ttf-dejavu-core as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xdg-user-dirs as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xdg-user-dirs-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xvnc4viewer as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: bluez-gnome
Installing bluez-gnome as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: cups-pdf
Installing cups-pdf as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libpaper-utils as dep of cups-pdf
new important dependency: discover1
Installing discover1 as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libdiscover1 as dep of discover1
Installing discover1-data as dep of libdiscover1
new important dependency: displayconfig-gtk
Installing displayconfig-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing guidance-backends as dep of displayconfig-gtk
new important dependency: libdeskbar-tracker
Installing libdeskbar-tracker as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing tracker as dep of libdeskbar-tracker
Installing libpoppler-glib2 as dep of tracker
Installing libpoppler2 as dep of libpoppler-glib2
Installing libsqlite3-0 as dep of tracker
Installing o3read as dep of tracker
new important dependency: libpam-gnome-keyring
Installing libpam-gnome-keyring as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: pidgin
Installing pidgin as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing pidgin-data as dep of pidgin
Installing libpurple0 as dep of pidgin
Installing libzephyr3 as dep of libpurple0
Installing libhesiod0 as dep of libzephyr3
new important dependency: pxljr
Installing pxljr as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: splix
Installing splix as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: tracker-search-tool
Installing tracker-search-tool as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libtracker-gtk0 as dep of tracker-search-tool
new important dependency: ttf-indic-fonts-core
Installing ttf-indic-fonts-core as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: ttf-unfonts-core
Installing ttf-unfonts-core as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: ubufox
Installing ubufox as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apturl as dep of ubufox
new important dependency: xresprobe
Installing xresprobe as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing cupsys-client as dep of cupsys-bsd
Installing fontconfig-config as dep of libfontconfig1
Installing scim-gtk2-immodule as dep of scim
Installing update-notifier-common as dep of update-notifier
Installing restricted-manager-core as dep of restricted-manager
Installing cpp as dep of g++
Installing gcc as dep of g++
Installing python2.5-minimal as dep of python2.5
Installing libflac8 as dep of gstreamer0.10-plugins-good
Installing liboil0.3 as dep of gstreamer0.10-plugins-good
Installing e2fslibs as dep of e2fsprogs
Installing kde-guidance as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing ttf-dejavu as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing upstart as dep of upstart-compat-sysv
Installing libart2.0-cil as dep of libgnome2.0-cil
Installing librsvg2.0-cil as dep of libgnome2.0-cil
Installing libgtkhtml2-0 as dep of python-gtkhtml2
Installing libgtop2-7 as dep of gnome-utils
Installing compiz-core as dep of compiz-plugins
Installing dmz-cursor-theme as dep of human-theme
Installing libgnome-speech7 as dep of gnome-orca
Installing libespeak1 as dep of libgnome-speech7
Installing espeak-data as dep of libespeak1
Installing python-orca-brlapi as dep of gnome-orca
Installing python-problem-report as dep of python-apport
Installing belocs-locales-bin as dep of locales
Installing tcpd as dep of netbase
Installing hal-info as dep of hal
Installing gij-4.2 as dep of gij
Installing python-gtk2 as dep of python-glade2
Installing libvte9 as dep of python-vte
Installing libvte-common as dep of libvte9
Installing language-selector-common as dep of language-selector
Installing libmtp5 as dep of amarok
Installing libpcrecpp0 as dep of gnome-system-monitor
Installing libbonobo2-common as dep of libbonobo2-0
Installing libmagic1 as dep of file
Installing gtk2-engines-xfce as dep of xubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing vim-runtime as dep of xubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing python-sexy as dep of gnome-app-install
Installing gs-gpl as dep of scribus
Installing gimp-data as dep of gimp
Installing librarian0 as dep of yelp
Installing dmidecode as dep of laptop-detect
Installing libgl1-mesa-glx as dep of libgl1-mesa-dri
Installing gnome-applets-data as dep of gnome-applets
Installing libalut0 as dep of rss-glx
Installing libglew1.4 as dep of rss-glx
Installing libservlet2.4-java as dep of libhsqldb-java
Installing linux-restricted-modules-2.6.22-14-generic as dep of linux-restricted-modules-generic
Installing compiz-fusion-plugins-main as dep of compiz
Installing compiz-fusion-plugins-extra as dep of compiz
Installing libcompizconfig0 as dep of compiz
Installing gnome-panel-data as dep of gnome-panel
Installing libntfs-3g12 as dep of ntfs-3g
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Installing libcompizconfig-backend-gconf as dep of compiz-gnome
Starting
Starting 2
Investigating libgtk2.0-0
Package libgtk2.0-0 has broken dep on gtk2-engines-xfce
  Considering gtk2-engines-xfce 1 as a solution to libgtk2.0-0 1037
  Added gtk2-engines-xfce to the remove list
Package libgtk2.0-0 has broken dep on gtk-qt-engine
  Considering gtk-qt-engine -1 as a solution to libgtk2.0-0 1037
  Added gtk-qt-engine to the remove list
  Fixing libgtk2.0-0 via remove of gtk2-engines-xfce
  Fixing libgtk2.0-0 via remove of gtk-qt-engine
Investigating dbus
Package dbus has broken dep on dbus-1-utils
  Considering dbus-1-utils 1 as a solution to dbus 125
  Added dbus-1-utils to the remove list
  Fixing dbus via remove of dbus-1-utils
Investigating openoffice.org-core
Package openoffice.org-core has broken dep on openoffice.org-kde
  Considering openoffice.org-kde -1 as a solution to openoffice.org-core 40
  Added openoffice.org-kde to the remove list
  Fixing openoffice.org-core via remove of openoffice.org-kde
Investigating ghostscript
Package ghostscript has broken dep on gs-esp
  Considering gs-esp 9 as a solution to ghostscript 29
  Added gs-esp to the remove list
Package ghostscript has broken dep on gs-gpl
  Considering gs-gpl 5 as a solution to ghostscript 29
  Added gs-gpl to the remove list
Package ghostscript has broken dep on gs-common
  Considering gs-common 7 as a solution to ghostscript 29
  Added gs-common to the remove list
  Fixing ghostscript via remove of gs-esp
  Fixing ghostscript via remove of gs-gpl
  Fixing ghostscript via remove of gs-common
Investigating openoffice.org-style-crystal
Package openoffice.org-style-crystal has broken dep on openoffice.org-common
  Considering openoffice.org-common 49 as a solution to openoffice.org-style-crystal 14
  Removing openoffice.org-style-crystal rather than change openoffice.org-common
Investigating vim-tiny
Package vim-tiny has broken dep on vim-runtime
  Considering vim-runtime 1 as a solution to vim-tiny 9
  Added vim-runtime to the remove list
  Fixing vim-tiny via remove of vim-runtime
Investigating openoffice.org-java-common
Package openoffice.org-java-common has broken dep on openoffice.org-filter-mobiledev
  Considering openoffice.org-filter-mobiledev -1 as a solution to openoffice.org-java-common 6
  Added openoffice.org-filter-mobiledev to the remove list
  Fixing openoffice.org-java-common via remove of openoffice.org-filter-mobiledev
Investigating ghostscript-x
Package ghostscript-x has broken dep on gs-esp-x
  Considering gs-esp-x 3 as a solution to ghostscript-x 4
  Added gs-esp-x to the remove list
  Fixing ghostscript-x via remove of gs-esp-x
Investigating python2.5-dev
Package python2.5-dev has broken dep on python2.5
  Considering python2.5 218 as a solution to python2.5-dev 3
  Removing python2.5-dev rather than change python2.5
Investigating human-theme
Package human-theme has broken dep on human-cursors-theme
  Considering human-cursors-theme -1 as a solution to human-theme 3
  Added human-cursors-theme to the remove list
  Fixing human-theme via remove of human-cursors-theme
Investigating adept-manager
Package adept-manager has broken dep on libapt-pkg-libc6.4-6-3.53
  Considering apt 18 as a solution to adept-manager 2
  Removing adept-manager rather than change libapt-pkg-libc6.4-6-3.53
Investigating guidance-backends
Package guidance-backends has broken dep on kde-guidance
  Considering kde-guidance 3 as a solution to guidance-backends 2
  Holding Back guidance-backends rather than change kde-guidance
Investigating adept-updater
Package adept-updater has broken dep on libapt-pkg-libc6.4-6-3.53
  Considering apt 18 as a solution to adept-updater 2
  Removing adept-updater rather than change libapt-pkg-libc6.4-6-3.53
Investigating adept
Package adept has broken dep on adept-manager
  Considering adept-manager 2 as a solution to adept 2
  Removing adept rather than change adept-manager
Investigating gutsy-wallpapers
Package gutsy-wallpapers has broken dep on feisty-wallpapers
  Considering feisty-wallpapers -1 as a solution to gutsy-wallpapers 2
  Added feisty-wallpapers to the remove list
  Fixing gutsy-wallpapers via remove of feisty-wallpapers
Investigating debtags
Package debtags has broken dep on libapt-pkg-libc6.4-6-3.53
  Considering apt 18 as a solution to debtags 2
  Removing debtags rather than change libapt-pkg-libc6.4-6-3.53
Investigating gobjc-4.1
Package gobjc-4.1 has broken dep on gcc-4.1-base
  Considering gcc-4.1-base 21 as a solution to gobjc-4.1 2
  Removing gobjc-4.1 rather than change gcc-4.1-base
Investigating libuniconf4.3
Package libuniconf4.3 has broken dep on libuniconf4.2
  Considering libuniconf4.2 -1 as a solution to libuniconf4.3 2
  Added libuniconf4.2 to the remove list
  Fixing libuniconf4.3 via remove of libuniconf4.2
Investigating libobjc1
Package libobjc1 has broken dep on gcc-4.1-base
  Considering gcc-4.1-base 21 as a solution to libobjc1 2
  Removing libobjc1 rather than change gcc-4.1-base
Investigating compiz-gnome
Package compiz-gnome has broken dep on compiz-gtk
  Considering compiz-gtk -1 as a solution to compiz-gnome 2
  Added compiz-gtk to the remove list
  Fixing compiz-gnome via remove of compiz-gtk
Investigating openoffice.org-l10n-uk
Package openoffice.org-l10n-uk has broken dep on openoffice.org-core
  Considering openoffice.org-core 40 as a solution to openoffice.org-l10n-uk 1
  Removing openoffice.org-l10n-uk rather than change openoffice.org-core
Investigating libpythonize0
Package libpythonize0 has broken dep on python2.5-dev
  Considering python2.5-dev 3 as a solution to libpythonize0 1
  Removing libpythonize0 rather than change python2.5-dev
Investigating adept-installer
Package adept-installer has broken dep on libapt-pkg-libc6.4-6-3.53
  Considering apt 18 as a solution to adept-installer 1
  Removing adept-installer rather than change libapt-pkg-libc6.4-6-3.53
Investigating libglew1.4
Package libglew1.4 has broken dep on libglew1
  Considering libglew1 -1 as a solution to libglew1.4 1
  Added libglew1 to the remove list
  Fixing libglew1.4 via remove of libglew1
Investigating python-all
Package python-all has broken dep on python
  Considering python 657 as a solution to python-all 1
  Removing python-all rather than change python
Investigating python-dev
Package python-dev has broken dep on python
  Considering python 657 as a solution to python-dev 1
  Removing python-dev rather than change python
Investigating adept-batch
Package adept-batch has broken dep on libapt-pkg-libc6.4-6-3.53
  Considering apt 18 as a solution to adept-batch 1
  Removing adept-batch rather than change libapt-pkg-libc6.4-6-3.53
Investigating language-support-uk
Package language-support-uk has broken dep on openoffice.org-l10n-uk
  Considering openoffice.org-l10n-uk 1 as a solution to language-support-uk 1
  Removing language-support-uk rather than change openoffice.org-l10n-uk
Investigating libwnck18
Package libwnck18 has broken dep on libwnck-common
  Considering libwnck-common 16 as a solution to libwnck18 1
  Removing libwnck18 rather than change libwnck-common
Investigating gobjc++-4.1
Package gobjc++-4.1 has broken dep on gcc-4.1-base
  Considering gcc-4.1-base 21 as a solution to gobjc++-4.1 1
  Removing gobjc++-4.1 rather than change gcc-4.1-base
Investigating language-selector-qt
Package language-selector-qt has broken dep on language-selector-common
  Considering language-selector-common 4 as a solution to language-selector-qt 1
  Removing language-selector-qt rather than change language-selector-common
Investigating adept-notifier
Package adept-notifier has broken dep on libapt-pkg-libc6.4-6-3.53
  Considering apt 18 as a solution to adept-notifier 1
  Removing adept-notifier rather than change libapt-pkg-libc6.4-6-3.53
Investigating ttf-dejavu-core
Package ttf-dejavu-core has broken dep on ttf-dejavu
  Considering ttf-dejavu 8 as a solution to ttf-dejavu-core 0
  Holding Back ttf-dejavu-core rather than change ttf-dejavu
Investigating libmtp6
Package libmtp6 has broken dep on libmtp5
  Considering libmtp5 2 as a solution to libmtp6 0
  Holding Back libmtp6 rather than change libmtp5
Investigating rhythmbox
Package rhythmbox has broken dep on libmtp6
  Considering libmtp6 0 as a solution to rhythmbox 0
  Holding Back rhythmbox rather than change libmtp6
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on ttf-dejavu-core
  Considering ttf-dejavu-core 0 as a solution to ubuntu-desktop 0
  Holding Back ubuntu-desktop rather than change ttf-dejavu-core
Investigating restricted-manager-core
Package restricted-manager-core has broken dep on guidance-backends
  Considering guidance-backends 2 as a solution to restricted-manager-core 0
  Holding Back restricted-manager-core rather than change guidance-backends
Investigating perl-suid
Package perl-suid has broken dep on perl
  Considering perl 321 as a solution to perl-suid 0
  Removing perl-suid rather than change perl
Investigating zlib1g-dev
Package zlib1g-dev has broken dep on zlib1g
  Considering zlib1g 2860 as a solution to zlib1g-dev 0
  Removing zlib1g-dev rather than change zlib1g
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
Investigating python-all-dev
Package python-all-dev has broken dep on python-all
  Considering python-all 1 as a solution to python-all-dev -1
  Removing python-all-dev rather than change python-all
Investigating gobjc++
Package gobjc++ has broken dep on gobjc++-4.1
  Considering gobjc++-4.1 1 as a solution to gobjc++ -1
  Removing gobjc++ rather than change gobjc++-4.1
Investigating kubuntu-desktop
Package kubuntu-desktop has broken dep on adept
  Considering adept 2 as a solution to kubuntu-desktop -1
  Removing kubuntu-desktop rather than change adept
Investigating libltdl3-dev
Package libltdl3-dev has broken dep on libltdl3
  Considering libltdl3 21 as a solution to libltdl3-dev -1
  Removing libltdl3-dev rather than change libltdl3
Investigating xubuntu-desktop
Package xubuntu-desktop has broken dep on gtk2-engines-xfce
  Considering gtk2-engines-xfce 1 as a solution to xubuntu-desktop -1
  Removing xubuntu-desktop rather than change gtk2-engines-xfce
Investigating scribus
Package scribus has broken dep on gs-gpl
  Considering gs-gpl 5 as a solution to scribus -1
Package scribus has broken dep on gs-afpl
Package scribus has broken dep on gs-esp
  Considering gs-esp 9 as a solution to scribus -1
  Or group remove for scribus
Investigating pidgin
Package pidgin has broken dep on gaim
  Considering gaim -1 as a solution to pidgin -1
  Holding Back pidgin rather than change gaim
Investigating libncurses5-dev
Package libncurses5-dev has broken dep on libncurses5
  Considering libncurses5 722 as a solution to libncurses5-dev -1
  Removing libncurses5-dev rather than change libncurses5
Investigating gobjc
Package gobjc has broken dep on gobjc-4.1
  Considering gobjc-4.1 2 as a solution to gobjc -1
  Removing gobjc rather than change gobjc-4.1
Investigating displayconfig-gtk
Package displayconfig-gtk has broken dep on guidance-backends
  Considering guidance-backends 2 as a solution to displayconfig-gtk -1
  Holding Back displayconfig-gtk rather than change guidance-backends
Investigating adept-common
Package adept-common has broken dep on debtags
  Considering debtags 2 as a solution to adept-common 4
  Added debtags to the remove list
  Fixing adept-common via keep of debtags
Investigating kde-guidance
Package kde-guidance has broken dep on libpythonize0
  Considering libpythonize0 1 as a solution to kde-guidance 3
  Added libpythonize0 to the remove list
  Fixing kde-guidance via keep of libpythonize0
Investigating debtags
Package debtags has broken dep on libapt-pkg-libc6.4-6-3.53
  Considering apt 18 as a solution to debtags 2
  Removing debtags rather than change libapt-pkg-libc6.4-6-3.53
Investigating libpythonize0
Package libpythonize0 has broken dep on python2.5-dev
  Considering python2.5-dev 3 as a solution to libpythonize0 1
  Removing libpythonize0 rather than change python2.5-dev
Investigating kdenetwork-filesharing
Package kdenetwork-filesharing has broken dep on perl-suid
  Considering perl-suid 0 as a solution to kdenetwork-filesharing 1
  Added perl-suid to the remove list
  Fixing kdenetwork-filesharing via keep of perl-suid
Investigating libgcj7-dev
Package libgcj7-dev has broken dep on zlib1g-dev
  Considering zlib1g-dev 0 as a solution to libgcj7-dev 1
  Added zlib1g-dev to the remove list
  Fixing libgcj7-dev via keep of zlib1g-dev
 Try to Re-Instate rhythmbox
 Try to Re-Instate ubuntu-desktop
Investigating restricted-manager
Package restricted-manager has broken dep on restricted-manager-core
  Considering restricted-manager-core 0 as a solution to restricted-manager 0
  Holding Back restricted-manager rather than change restricted-manager-core
Investigating perl-suid
Package perl-suid has broken dep on perl
  Considering perl 321 as a solution to perl-suid 0
  Removing perl-suid rather than change perl
Investigating zlib1g-dev
Package zlib1g-dev has broken dep on zlib1g
  Considering zlib1g 2860 as a solution to zlib1g-dev 0
  Removing zlib1g-dev rather than change zlib1g
Investigating adept-common
Package adept-common has broken dep on debtags
  Considering debtags 2 as a solution to adept-common 4
  Added debtags to the remove list
  Fixing adept-common via keep of debtags
Investigating kde-guidance
Package kde-guidance has broken dep on libpythonize0
  Considering libpythonize0 1 as a solution to kde-guidance 3
  Added libpythonize0 to the remove list
  Fixing kde-guidance via keep of libpythonize0
Investigating debtags
Package debtags has broken dep on libapt-pkg-libc6.4-6-3.53
  Considering apt 18 as a solution to debtags 4
  Removing debtags rather than change libapt-pkg-libc6.4-6-3.53
Investigating libpythonize0
Package libpythonize0 has broken dep on python2.5-dev
  Considering python2.5-dev 3 as a solution to libpythonize0 3
  Removing libpythonize0 rather than change python2.5-dev
Investigating kdenetwork-filesharing
Package kdenetwork-filesharing has broken dep on perl-suid
  Considering perl-suid 0 as a solution to kdenetwork-filesharing 1
  Added perl-suid to the remove list
  Fixing kdenetwork-filesharing via keep of perl-suid
Investigating libgcj7-dev
Package libgcj7-dev has broken dep on zlib1g-dev
  Considering zlib1g-dev 0 as a solution to libgcj7-dev 1
  Added zlib1g-dev to the remove list
  Fixing libgcj7-dev via keep of zlib1g-dev
 Try to Re-Instate restricted-manager
Investigating perl-suid
Package perl-suid has broken dep on perl
  Considering perl 321 as a solution to perl-suid 1
  Removing perl-suid rather than change perl
Investigating zlib1g-dev
Package zlib1g-dev has broken dep on zlib1g
  Considering zlib1g 2860 as a solution to zlib1g-dev 1
  Removing zlib1g-dev rather than change zlib1g
Investigating adept-common
Package adept-common has broken dep on debtags
  Considering debtags 18 as a solution to adept-common 4
  Removing adept-common rather than change debtags
Investigating kde-guidance
Package kde-guidance has broken dep on libpythonize0
  Considering libpythonize0 3 as a solution to kde-guidance 3
  Removing kde-guidance rather than change libpythonize0
Investigating kdenetwork-filesharing
Package kdenetwork-filesharing has broken dep on perl-suid
  Considering perl-suid 321 as a solution to kdenetwork-filesharing 1
  Removing kdenetwork-filesharing rather than change perl-suid
Investigating libgcj7-dev
Package libgcj7-dev has broken dep on zlib1g-dev
  Considering zlib1g-dev 2860 as a solution to libgcj7-dev 1
  Removing libgcj7-dev rather than change zlib1g-dev
Investigating kde-guidance-powermanager
Package kde-guidance-powermanager has broken dep on kde-guidance
  Considering kde-guidance 3 as a solution to kde-guidance-powermanager -1
  Removing kde-guidance-powermanager rather than change kde-guidance
Investigating gcj-4.1
Package gcj-4.1 has broken dep on libgcj7-dev
  Considering libgcj7-dev 2860 as a solution to gcj-4.1 2
  Removing gcj-4.1 rather than change libgcj7-dev
Investigating gcj
Package gcj has broken dep on gcj-4.1
  Considering gcj-4.1 2860 as a solution to gcj -1
  Removing gcj rather than change gcj-4.1
Done
Starting
Starting 2
Investigating language-support-uk
Package language-support-uk has broken dep on openoffice.org-l10n-uk
  Considering openoffice.org-l10n-uk 1 as a solution to language-support-uk 9999
  Added openoffice.org-l10n-uk to the remove list
  Fixing language-support-uk via keep of openoffice.org-l10n-uk
Investigating openoffice.org-l10n-uk
Package openoffice.org-l10n-uk has broken dep on openoffice.org-core
  Considering openoffice.org-core 35 as a solution to openoffice.org-l10n-uk 1
  Removing openoffice.org-l10n-uk rather than change openoffice.org-core
Investigating language-support-uk
Package language-support-uk has broken dep on openoffice.org-l10n-uk
  Considering openoffice.org-l10n-uk 1 as a solution to language-support-uk 9999
  Added openoffice.org-l10n-uk to the remove list
  Fixing language-support-uk via keep of openoffice.org-l10n-uk
Investigating openoffice.org-l10n-uk
Package openoffice.org-l10n-uk has broken dep on openoffice.org-core
  Considering openoffice.org-core 35 as a solution to openoffice.org-l10n-uk 1
  Removing openoffice.org-l10n-uk rather than change openoffice.org-core
Investigating language-support-uk
Package language-support-uk has broken dep on openoffice.org-l10n-uk
  Considering openoffice.org-l10n-uk 1 as a solution to language-support-uk 9999
  Added openoffice.org-l10n-uk to the remove list
  Fixing language-support-uk via keep of openoffice.org-l10n-uk
Investigating openoffice.org-l10n-uk
Package openoffice.org-l10n-uk has broken dep on openoffice.org-core
  Considering openoffice.org-core 35 as a solution to openoffice.org-l10n-uk 9999
  Added openoffice.org-core to the remove list
  Fixing openoffice.org-l10n-uk via keep of openoffice.org-core
Investigating openoffice.org-impress
Package openoffice.org-impress has broken dep on openoffice.org-core
  Considering openoffice.org-core 9999 as a solution to openoffice.org-impress 1
  Re-Instated openoffice.org-core
  Re-Instated openoffice.org-impress
Investigating openoffice.org-l10n-uk
Package openoffice.org-l10n-uk has broken dep on openoffice.org-core
  Considering openoffice.org-core 9999 as a solution to openoffice.org-l10n-uk 9999
  Removing openoffice.org-l10n-uk rather than change openoffice.org-core
Investigating language-support-uk
Package language-support-uk has broken dep on openoffice.org-l10n-uk
  Considering openoffice.org-l10n-uk 9999 as a solution to language-support-uk 9999
Done
Installing xserver-xorg-core as dep of xserver-xorg
Installing libc6 as dep of xserver-xorg-core
Installing libgcc1 as dep of xserver-xorg-core
Installing gcc-4.2-base as dep of libgcc1
Installing kdelibs4c2a as dep of kpdf
Installing libart-2.0-2 as dep of kdelibs4c2a
Installing libasound2 as dep of kdelibs4c2a
Installing libcupsys2 as dep of kdelibs4c2a
Installing libgnutls13 as dep of libcupsys2
Installing liblzo2-2 as dep of libgnutls13
Installing libopencdk8 as dep of libgnutls13
Installing zlib1g as dep of libgnutls13
Installing libkrb53 as dep of libcupsys2
Installing libkeyutils1 as dep of libkrb53
Installing libfreetype6 as dep of kdelibs4c2a
Installing libjasper1 as dep of kdelibs4c2a
Installing libstdc++6 as dep of kdelibs4c2a
Installing libxml2 as dep of kdelibs4c2a
Installing kdelibs-data as dep of kdelibs4c2a
Installing libpoppler2 as dep of kpdf
Installing libdbus-1-3 as dep of gnome-keyring
Installing libglib2.0-0 as dep of gnome-keyring
Installing libgtk2.0-0 as dep of gnome-keyring
Installing libgtk2.0-common as dep of libgtk2.0-0
Installing libpango1.0-0 as dep of libgtk2.0-0
Installing libpango1.0-common as dep of libpango1.0-0
Installing libxdamage1 as dep of libgtk2.0-0
Installing libhal-storage1 as dep of gnome-keyring
Installing libhal1 as dep of gnome-keyring
Installing libgnomeui-0 as dep of f-spot
Installing libglade2-0 as dep of libgnomeui-0
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
Installing libxfce4util4 as dep of libxfcegui4-4
Installing libgstreamer0.10-0 as dep of gstreamer0.10-alsa
Installing libgstreamer-plugins-base0.10-0 as dep of gstreamer0.10-alsa
Installing ghostscript-x as dep of gs-esp-x
Installing ghostscript as dep of ghostscript-x
Installing libgs8 as dep of ghostscript
Installing libcupsimage2 as dep of libgs8
Installing libsdl1.2debian-alsa as dep of libsdl1.2debian
Installing gcj-4.1-base as dep of libgcj7-jar
Installing libgcj7-1 as dep of libgcj7-jar
Installing openoffice.org-l10n-common as dep of openoffice.org-l10n-uk
Installing libdbus-glib-1-2 as dep of libgnomekbd1
Installing libgnomekbd-common as dep of libgnomekbd1
Installing libxfce4mcs-client3 as dep of xfce4-mcs-plugins
Installing libxfce4mcs-manager3 as dep of xfce4-mcs-plugins
Installing libvorbisfile3 as dep of libarts1c2a
Installing gcc-3.3-base as dep of libstdc++5
Installing libgmime2.2-cil as dep of tomboy
Installing perl as dep of libglib-perl
Installing perl-base as dep of perl
Installing perl-modules as dep of perl
Installing libbz2-1.0 as dep of bzip2
Installing libecal1.2-7 as dep of evolution-webcal
Installing libedataserver1.2-9 as dep of libecal1.2-7
Installing libnspr4-0d as dep of libedataserver1.2-9
Installing libebook1.2-9 as dep of ekiga
Installing libcamel1.2-10 as dep of libebook1.2-9
Installing libnss3-0d as dep of libcamel1.2-10
Installing libopal-2.2 as dep of ekiga
Installing libpt-1.10.0 as dep of libopal-2.2
Installing libssl0.9.8 as dep of libpt-1.10.0
Installing dmz-cursor-theme as dep of kubuntu-default-settings
Installing openoffice.org-core as dep of openoffice.org-gnome
Installing openoffice.org-common as dep of openoffice.org-core
Installing libcurl3-gnutls as dep of openoffice.org-core
Installing libdb4.5 as dep of openoffice.org-core
Installing libhunspell-1.1-0 as dep of openoffice.org-core
Installing libneon26 as dep of openoffice.org-core
Installing libgimp2.0 as dep of gimp-print
Installing libgutenprint2 as dep of gimp-print
Installing libgutenprintui2-1 as dep of gimp-print
Installing libwnck22 as dep of notification-daemon
Installing libwnck-common as dep of libwnck22
Installing libgnomevfs2-common as dep of libgnomevfs2-0
Installing network-manager-kde as dep of knetworkmanager
Installing networkstatus as dep of network-manager-kde
Installing libatm1 as dep of iproute
Installing python2.4 as dep of python2.4-dev
Installing python2.4-minimal as dep of python2.4
Installing libncursesw5 as dep of python2.4
Installing libgnomecanvas2-0 as dep of gthumb
Installing libgnomecanvas2-common as dep of libgnomecanvas2-0
Installing update-manager-core as dep of update-manager
Installing python-uno as dep of openoffice.org-writer
Installing apt as dep of adept-manager
Installing libept0 as dep of adept-manager
Installing libxapian15 as dep of libept0
Installing language-pack-gnome-uk as dep of language-pack-gnome-uk-base
Installing libkcal2b as dep of knode
Installing libkdepim1a as dep of libkcal2b
Installing libkleopatra1 as dep of knode
Installing libkmime2 as dep of knode
Installing kmplayer-base as dep of kmplayer-konq-plugins
Installing libscim8c2a as dep of scim-modules-table
Installing gnome-media-common as dep of gnome-media
Installing libmetacity0 as dep of metacity
Installing metacity-common as dep of libmetacity0
Installing libkjsembed1 as dep of krusader
Installing libkonq4 as dep of krusader
Installing libbeagle0 as dep of nautilus
Installing librsvg2-2 as dep of nautilus
Installing libgsf-1-114 as dep of librsvg2-2
Installing libgsf-1-common as dep of libgsf-1-114
Installing libtrackerclient0 as dep of nautilus
Installing nautilus-data as dep of nautilus
Installing libgnome2-common as dep of libgnome2-0
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
Installing gnat-4.1-base as dep of libgnatvsn4.1
Installing libgnat-4.1 as dep of libgnatvsn4.1
Installing linux-headers-2.6.22-14-generic as dep of linux-headers-generic
Installing linux-headers-2.6.22-14 as dep of linux-headers-2.6.22-14-generic
Installing libaspell15 as dep of aspell
Installing libxcb1 as dep of kaffeine-xine
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
Installing libgcj-common as dep of libgcj-bc
Installing libgcj8-1 as dep of libgcj-bc
Installing gcj-4.2-base as dep of libgcj8-1
Installing ttf-indic-fonts-core as dep of ttf-indic-fonts
Installing ttf-bengali-fonts as dep of ttf-indic-fonts
Installing ttf-gujarati-fonts as dep of ttf-indic-fonts
Installing ttf-kannada-fonts as dep of ttf-indic-fonts
Installing ttf-malayalam-fonts as dep of ttf-indic-fonts
Installing ttf-oriya-fonts as dep of ttf-indic-fonts
Installing ttf-tamil-fonts as dep of ttf-indic-fonts
Installing ttf-telugu-fonts as dep of ttf-indic-fonts
Installing libapr1 as dep of kdevelop
Installing libaprutil1 as dep of kdevelop
Installing libsvn1 as dep of kdevelop
Installing kdevelop-data as dep of kdevelop
Installing openoffice.org-java-common as dep of openoffice.org-filter-mobiledev
Installing libflac++6 as dep of libk3b2
Installing libflac8 as dep of libflac++6
Installing python-all as dep of python-all-dev
Installing python as dep of python-all
Installing python-minimal as dep of python
Installing python-dev as dep of python-all-dev
Installing xdg-utils as dep of libdjvulibre15
Installing libgconf2-ruby1.8 as dep of libgconf2-ruby
Installing libruby1.8 as dep of libgconf2-ruby1.8
Installing libglib2-ruby1.8 as dep of libgconf2-ruby1.8
Installing libao2 as dep of vorbis-tools
Installing libiw29 as dep of wireless-tools
Installing samba-common as dep of smbclient
Installing libslang2 as dep of whiptail
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
Installing language-pack-kde-uk as dep of language-pack-kde-uk-base
Installing libbluetooth2 as dep of kdebluetooth
Installing libkbluetooth0 as dep of kdebluetooth
Installing python-qt4-dbus as dep of kdebluetooth
Installing libqt4-core as dep of python-qt4-dbus
Installing koffice-libs as dep of koshell
Installing koffice-data as dep of koffice-libs
Installing kicker as dep of kcontrol
Installing kdebase-data as dep of kicker
Installing libgucharmap6 as dep of gucharmap
Installing brltty as dep of brltty-x11
Installing gcc-3.4-base as dep of libg2c0-dev
Installing libg2c0 as dep of libg2c0-dev
Installing libatk1-ruby1.8 as dep of libatk1-ruby
Installing libdaemon0 as dep of avahi-daemon
Installing gnome-games-data as dep of gnome-games
Installing gnome-cards-data as dep of gnome-games-data
Installing gdebi-core as dep of gdebi
Installing python-apt as dep of gdebi-core
Installing apt-utils as dep of python-apt
Installing python-central as dep of python-apt
Installing dpkg as dep of python-central
Installing sun-java6-bin as dep of sun-java6-plugin
Installing sun-java6-jre as dep of sun-java6-bin
Installing cpp as dep of gobjc++
Installing cpp-4.1 as dep of cpp
Installing gcc-4.1-base as dep of cpp-4.1
Installing gcc as dep of gobjc++
Installing gcc-4.1 as dep of gcc
Installing gobjc++-4.1 as dep of gobjc++
Installing gobjc-4.1 as dep of gobjc++-4.1
Installing libobjc1 as dep of gobjc-4.1
Installing g++-4.1 as dep of gobjc++-4.1
Installing libstdc++6-4.1-dev as dep of g++-4.1
Installing libanthy0 as dep of anthy
Installing evolution as dep of evolution-exchange
Installing libedataserverui1.2-8 as dep of evolution
Installing libegroupwise1.2-13 as dep of evolution
Installing libexchange-storage1.2-3 as dep of evolution
Installing libgtkhtml3.14-19 as dep of evolution
Installing evolution-data-server as dep of evolution
Installing libedata-book1.2-2 as dep of evolution-data-server
Installing libedata-cal1.2-6 as dep of evolution-data-server
Installing evolution-data-server-common as dep of evolution-data-server
Installing gcc-3.4 as dep of gpc-2.1-3.4
Installing cpp-3.4 as dep of gcc-3.4
Installing karbon as dep of koffice
Installing kchart as dep of koffice
Installing kexi as dep of koffice
Installing libpqxx-2.6.9 as dep of kexi
Installing kformula as dep of koffice
Installing kivio as dep of koffice
Installing kplato as dep of koffice
Installing kpresenter as dep of koffice
Installing kpresenter-data as dep of kpresenter
Installing krita as dep of koffice
Installing libpoppler-qt2 as dep of krita
Installing kspread as dep of koffice
Installing kugar as dep of koffice
Installing kword as dep of koffice
Installing kthesaurus as dep of koffice
Installing libwxbase2.6-0 as dep of libwxgtk2.6-0
Installing xfce4-panel as dep of xfce4-xkb-plugin
Installing esound-common as dep of esound
Installing linux-image-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing linux-ubuntu-modules-2.6.22-14-generic as dep of linux-image-generic
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libjack0 as dep of audacity
Installing libgpod2 as dep of rhythmbox
Installing libmtp6 as dep of rhythmbox
Installing libmusicbrainz4c2a as dep of rhythmbox
Installing libtotem-plparser7 as dep of rhythmbox
Installing liblame0 as dep of gstreamer0.10-plugins-ugly-multiverse
Installing libexo-0.3-0 as dep of xfce4-verve-plugin
Installing libgtksourceview2.0-0 as dep of gedit
Installing libgtksourceview2.0-common as dep of libgtksourceview2.0-0
Installing gedit-common as dep of gedit
Installing python-pygtksourceview as dep of gedit
Installing libexiv2-0 as dep of gwenview
Installing python-gmenu as dep of gnome-menus
Installing python-cups as dep of system-config-printer
Installing libsnmp10 as dep of hpijs
Installing libsnmp-base as dep of libsnmp10
Installing libgmp3c2 as dep of libgmp3-dev
Installing libgmpxx4ldbl as dep of libgmp3-dev
Installing kdepim-kresources as dep of kdepim-kio-plugins
Installing kaddressbook as dep of kdepim-kresources
Installing libqt4-gui as dep of libqt4-qt3support
Installing libqt4-sql as dep of libqt4-qt3support
Installing libsqlite3-0 as dep of libqt4-sql
Installing gutsy-wallpapers as dep of ubuntu-artwork
Installing language-pack-gnome-en as dep of language-pack-gnome-en-base
Installing capplets-data as dep of gnome-control-center
Installing libgnome-window-settings1 as dep of gnome-control-center
Installing libsasl2-2 as dep of libsasl2-modules
Installing hplip-data as dep of hplip
Installing gconf2-common as dep of gconf2
Installing libkcddb1 as dep of kdemultimedia-kio-plugins
Installing consolekit as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing fast-user-switch-applet as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing ttf-dejavu-core as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xdg-user-dirs as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xdg-user-dirs-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing xvnc4viewer as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: bluez-gnome
Installing bluez-gnome as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: cups-pdf
Installing cups-pdf as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libpaper-utils as dep of cups-pdf
new important dependency: discover1
Installing discover1 as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libdiscover1 as dep of discover1
Installing discover1-data as dep of libdiscover1
new important dependency: displayconfig-gtk
Installing displayconfig-gtk as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing guidance-backends as dep of displayconfig-gtk
new important dependency: libdeskbar-tracker
Installing libdeskbar-tracker as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing tracker as dep of libdeskbar-tracker
Installing libpoppler-glib2 as dep of tracker
Installing o3read as dep of tracker
new important dependency: libpam-gnome-keyring
Installing libpam-gnome-keyring as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: pidgin
Installing pidgin as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing pidgin-data as dep of pidgin
Installing libpurple0 as dep of pidgin
Installing libzephyr3 as dep of libpurple0
Installing libhesiod0 as dep of libzephyr3
new important dependency: pxljr
Installing pxljr as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: splix
Installing splix as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: tracker-search-tool
Installing tracker-search-tool as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libtracker-gtk0 as dep of tracker-search-tool
new important dependency: ttf-unfonts-core
Installing ttf-unfonts-core as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: ubufox
Installing ubufox as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing apturl as dep of ubufox
new important dependency: xresprobe
Installing xresprobe as dep of ubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libkpimidentities1 as dep of kontact
Installing libglade2-ruby1.8 as dep of libglade2-ruby
Installing libgtk2-ruby1.8 as dep of libglade2-ruby1.8
Installing libpango1-ruby1.8 as dep of libgtk2-ruby1.8
Installing libgdk-pixbuf2-ruby1.8 as dep of libgtk2-ruby1.8
Installing cupsys-client as dep of cupsys-bsd
Installing fontconfig-config as dep of libfontconfig1
Installing ecj as dep of ecj-gcj
Installing libecj-java as dep of ecj
Installing gij-4.2 as dep of ecj
Installing libgcj8-jar as dep of ecj
Installing libecj-java-gcj as dep of ecj-gcj
Installing libx264-54 as dep of gstreamer0.10-plugins-bad-multiverse
Installing libexiv2-0.12 as dep of libkexiv2-0
Installing ksysguardd as dep of ksysguard
Installing scim-gtk2-immodule as dep of scim
Installing update-notifier-common as dep of update-notifier
Installing restricted-manager-core as dep of restricted-manager
Installing python2.5 as dep of python2.5-dev
Installing python2.5-minimal as dep of python2.5
Installing e2fslibs as dep of e2fsprogs
new important dependency: dolphin
Installing dolphin as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: foomatic-db-gutenprint
Installing foomatic-db-gutenprint as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing ijsgutenprint as dep of foomatic-db-gutenprint
Installing libijs-0.35 as dep of ijsgutenprint
new important dependency: gdebi-kde
Installing gdebi-kde as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: hplip-gui
Installing hplip-gui as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: kdesudo
Installing kdesudo as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: kio-umountwrapper
Installing kio-umountwrapper as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: kvkbd
Installing kvkbd as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: pinentry-qt
Installing pinentry-qt as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: restricted-manager-kde
Installing restricted-manager-kde as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: strigi-applet
Installing strigi-applet as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libsearchclient0 as dep of strigi-applet
Installing libstreams0 as dep of strigi-applet
Installing libstrigihtmlgui0 as dep of strigi-applet
Installing libstreamanalyzer0 as dep of libstrigihtmlgui0
new important dependency: strigi-daemon
Installing strigi-daemon as dep of kubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing libcluceneindex0 as dep of strigi-daemon
Installing python-apport as dep of apport-qt
Installing python-problem-report as dep of python-apport
Installing python-launchpad-bugs as dep of python-apport
Installing libgoffice-0-4 as dep of gnumeric-gtk
Installing libgsf-gnome-1-114 as dep of libgoffice-0-4
Installing upstart as dep of upstart-compat-sysv
Installing pingus-data as dep of pingus
Installing libboost-signals1.34.1 as dep of pingus
Installing ksplash as dep of ksplash-engine-moodin
Installing libart2.0-cil as dep of libgnome2.0-cil
Installing librsvg2.0-cil as dep of libgnome2.0-cil
Installing libgtkhtml2-0 as dep of python-gtkhtml2
Installing libmozjs0d as dep of gxine
Installing libgtop2-7 as dep of gnome-utils
Installing libkdcraw1 as dep of kipi-plugins
Installing libkexiv2-1 as dep of kipi-plugins
Installing libkpimexchange1 as dep of korganizer
Installing compiz-core as dep of compiz-plugins
Installing libltdl3 as dep of libltdl3-dev
Installing libgnome-speech7 as dep of gnome-orca
Installing libespeak1 as dep of libgnome-speech7
Installing espeak-data as dep of libespeak1
Installing python-orca-brlapi as dep of gnome-orca
Installing python-sip4 as dep of python-qt3
Installing libgcj7-dev as dep of gcj-4.1
Installing libgcj7-1-awt as dep of libgcj7-dev
Installing belocs-locales-bin as dep of locales
Installing libavcodec1d as dep of libxine1-ffmpeg
Installing libavutil1d as dep of libavcodec1d
Installing libpostproc1d as dep of libxine1-ffmpeg
Installing libxine1 as dep of libxine1-ffmpeg
Installing libxcb-shape0 as dep of libxine1
Installing libxcb-shm0 as dep of libxine1
Installing libxcb-xv0 as dep of libxine1
Installing libavformat1d as dep of vlc-nox
Installing libebml0 as dep of vlc-nox
Installing libmatroska0 as dep of vlc-nox
Installing tcpd as dep of netbase
Installing gij as dep of gcj
Installing gcj-4.2 as dep of gcj
Installing gcc-4.2 as dep of gcj-4.2
Installing cpp-4.2 as dep of gcc-4.2
Installing libgomp1 as dep of gcc-4.2
Installing libgcj8-dev as dep of gcj-4.2
Installing libgcj8-1-awt as dep of libgcj8-dev
Installing hal-info as dep of hal
Installing thunar-data as dep of thunar
Installing dbus-x11 as dep of thunar
Installing python-gtk2 as dep of python-glade2
Installing amarok as dep of amarok-xine
Installing libvte9 as dep of python-vte
Installing libvte-common as dep of libvte9
Installing language-selector-common as dep of language-selector
Installing libpcrecpp0 as dep of gnome-system-monitor
Installing libresid-builder0c2a as dep of moc
Installing libsidplay2 as dep of moc
Installing libsidutils0 as dep of moc
Installing libquicktime1 as dep of libmjpegtools0c2a
Installing libbonobo2-common as dep of libbonobo2-0
Installing thunderbird as dep of mozilla-thunderbird
Installing libmagic1 as dep of file
Installing gtk2-engines-murrine as dep of xubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing thunar-volman as dep of xubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: brasero
Installing brasero as dep of xubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: libgoffice-gtk-0-4
Installing libgoffice-gtk-0-4 as dep of xubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: totem-xine
Installing totem-xine as dep of xubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
new important dependency: xfce4-places-plugin
Installing xfce4-places-plugin as dep of xubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Installing python-sexy as dep of gnome-app-install
Installing planetpenguin-racer-data as dep of planetpenguin-racer
Installing libmms0 as dep of gstreamer0.10-plugins-bad
Installing libopenspc0 as dep of gstreamer0.10-plugins-bad
Installing gimp-data as dep of gimp
Installing xfdesktop4-data as dep of xfdesktop4
Installing ttf-dejavu-extra as dep of ttf-dejavu
Installing librarian0 as dep of yelp
Installing dmidecode as dep of laptop-detect
Installing libgl1-mesa-glx as dep of libgl1-mesa-dri
Installing gnome-applets-data as dep of gnome-applets
Installing libalut0 as dep of rss-glx
Installing libglew1.4 as dep of rss-glx
Installing libpth20 as dep of libgpgme11
Installing gnupg as dep of libgpgme11
Installing libservlet2.4-java as dep of libhsqldb-java
Installing gtkhtml3.8 as dep of gnomesword
Installing linux-restricted-modules-2.6.22-14-generic as dep of linux-restricted-modules-generic
Installing compiz-fusion-plugins-main as dep of compiz
Installing compiz-fusion-plugins-extra as dep of compiz
Installing libcompizconfig0 as dep of compiz
Installing gnome-panel-data as dep of gnome-panel
Installing gpgsm as dep of kmail
Installing libksba8 as dep of gpgsm
Installing gnupg-agent as dep of kmail
Installing liblink-grammar4 as dep of abiword-plugins
Installing link-grammar-dictionaries-en as dep of liblink-grammar4
Installing libode0debian1 as dep of xmoto
Installing libsdl-ttf2.0-0 as dep of xmoto
Installing libntfs-3g12 as dep of ntfs-3g
Installing libgnomeprintui2.2-common as dep of libgnomeprintui2.2-0
Installing libopensync0 as dep of kitchensync
Installing libcompizconfig-backend-gconf as dep of compiz-gnome
Starting
Starting 2
Investigating dbus
Package dbus has broken dep on dbus-1-utils
  Considering dbus-1-utils -1 as a solution to dbus 132
  Added dbus-1-utils to the remove list
  Fixing dbus via remove of dbus-1-utils
Investigating firefox
Package firefox has broken dep on libnss3
  Considering libnss3 -1 as a solution to firefox 10
  Added libnss3 to the remove list
  Fixing firefox via remove of libnss3
Investigating libexiv2-0
Package libexiv2-0 has broken dep on libexiv2-0.12
  Considering libexiv2-0.12 2 as a solution to libexiv2-0 6
  Added libexiv2-0.12 to the remove list
  Fixing libexiv2-0 via remove of libexiv2-0.12
Investigating digikam
Package digikam has broken dep on digikamimageplugins
  Considering digikamimageplugins -1 as a solution to digikam 4
  Added digikamimageplugins to the remove list
Package digikam has broken dep on libkexiv2-0
  Considering libkexiv2-0 1 as a solution to digikam 4
  Added libkexiv2-0 to the remove list
  Fixing digikam via remove of digikamimageplugins
  Fixing digikam via remove of libkexiv2-0
Investigating thunar-data
Package thunar-data has broken dep on thunar-doc
  Considering thunar-doc -1 as a solution to thunar-data 4
  Added thunar-doc to the remove list
  Fixing thunar-data via remove of thunar-doc
Investigating libmtp6
Package libmtp6 has broken dep on libmtp5
  Considering libmtp5 -1 as a solution to libmtp6 3
  Added libmtp5 to the remove list
  Fixing libmtp6 via remove of libmtp5
Investigating human-theme
Package human-theme has broken dep on human-cursors-theme
  Considering human-cursors-theme 0 as a solution to human-theme 3
  Added human-cursors-theme to the remove list
  Fixing human-theme via remove of human-cursors-theme
Investigating compiz-gnome
Package compiz-gnome has broken dep on compiz-gtk
  Considering compiz-gtk -1 as a solution to compiz-gnome 2
  Added compiz-gtk to the remove list
  Fixing compiz-gnome via remove of compiz-gtk
Investigating libglew1.4
Package libglew1.4 has broken dep on libglew1
  Considering libglew1 -1 as a solution to libglew1.4 1
  Added libglew1 to the remove list
  Fixing libglew1.4 via remove of libglew1
Investigating libwnck18
Package libwnck18 has broken dep on libwnck-common
  Considering libwnck-common 16 as a solution to libwnck18 1
  Removing libwnck18 rather than change libwnck-common
Investigating libkbluetooth0
Package libkbluetooth0 has broken dep on qobex
  Considering qobex -1 as a solution to libkbluetooth0 0
  Added qobex to the remove list
  Fixing libkbluetooth0 via remove of qobex
Investigating thunar-volman
Package thunar-volman has broken dep on thunar-volman-plugin
  Considering thunar-volman-plugin -1 as a solution to thunar-volman 0
  Added thunar-volman-plugin to the remove list
  Fixing thunar-volman via remove of thunar-volman-plugin
Investigating libgmpxx4ldbl
Package libgmpxx4ldbl has broken dep on libgmpxx4
  Considering libgmpxx4 -1 as a solution to libgmpxx4ldbl 0
  Added libgmpxx4 to the remove list
  Fixing libgmpxx4ldbl via remove of libgmpxx4
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
Investigating libuniconf4.3
Package libuniconf4.3 has broken dep on libuniconf4.2
  Considering libuniconf4.2 -1 as a solution to libuniconf4.3 0
  Added libuniconf4.2 to the remove list
  Fixing libuniconf4.3 via remove of libuniconf4.2
Investigating libgcj7-awt
Package libgcj7-awt has broken dep on gcj-4.1-base
  Considering gcj-4.1-base 19 as a solution to libgcj7-awt -1
  Removing libgcj7-awt rather than change gcj-4.1-base
Done
new important dependency: totem-xine
Installing totem-xine as dep of xubuntu-desktop
Setting NOT as auto-installed because its a direct dep of a package in section metapackages
Traceback (most recent call last):
  File "/usr/share/apport/apport-gtk", line 247, in <module>
    app.run_argv()
  File "/var/lib/python-support/python2.5/apport/ui.py", line 252, in run_argv
    self.run_crashes()
  File "/var/lib/python-support/python2.5/apport/ui.py", line 116, in run_crashes
    self.run_crash(f)
  File "/var/lib/python-support/python2.5/apport/ui.py", line 125, in run_crash
    apport.fileutils.mark_report_seen(report_file)
  File "/var/lib/python-support/python2.5/apport/fileutils.py", line 75, in mark_report_seen
    st = os.stat(report)
OSError: [Errno 2] No such file or directory: '/var/crash/_usr_lib_xfce4-fsguard-plugin_xfce4_panel-plugins_xfce4-fsguard-plugin.1000.crash'

```

---

### Post by vasiliymeshko on 2007-10-24
Right now attempting to upgrade by changing all lines in sources.list from 'feisty' to 'gutsy' and doing dist-upgrade. I'm still curious as to why wouldn't it upgrade in the first try. Anyone else with similar issues?

---

### Post by Steve1961 on 2007-10-24
Run apt-get -f install a few times then apt-get dist-upgrade.  I got a lot of errors with my first upgrade (using the beta) and the updater crashed.  However, I was then able to finish the upgrade manually once I'd run apt-get -f install.

---

### Post by vasiliymeshko on 2007-10-24
Right now I'm at a point where it downloaded 83% of packages it needs. Hopefully it finishes successfully.

---

### Post by pierrot on 2007-10-24
Hello!

I`m with Toshiba Satellite L30 , install 7.10 and have no video - download movie, start the Totem and fault - mix of colors.

Typing "apt-get -f install" will it be a solution of my problem? With 7.04 has no problem...:confused:

---

### Post by Steve1961 on 2007-10-24
> **pierrot said:**
> Hello!

I`m with Toshiba Satellite L30 , install 7.10 and have no video - download movie, start the Totem and fault - mix of colors.

Typing "apt-get -f install" will it be a solution of my problem? With 7.04 has no problem...:confused:


No apt-get -f install will not solve this problem.  I suggest you create a separate post about these issues, and don't forget to include details of your hardware, especially your graphics card

---

