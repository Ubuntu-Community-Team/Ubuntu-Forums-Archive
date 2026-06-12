---
title: "Upgrade errors, scared to reboot"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by rich86 on 2007-10-20
Hi, i started the upgrade this morning and during the install part i had lots of errors i am now scared to reboot, i don;t know if anything will work! Here is my log file:
```
2007-10-20 11:15:57,363 INFO release-upgrader version '0.81' started
2007-10-20 11:16:00,945 DEBUG lsb-release: 'feisty'
2007-10-20 11:16:00,946 DEBUG _pythonSymlinkCheck run
2007-10-20 11:16:02,993 DEBUG checkViewDepends()
2007-10-20 11:16:06,948 DEBUG Foreign: automatix2 realplay acroread virtualbox
2007-10-20 11:16:06,949 DEBUG Obsolete: libdvdcss2 mlt++ kdenlive mlt avg75fld
2007-10-20 11:16:06,950 DEBUG updateSourcesList()
2007-10-20 11:16:07,095 DEBUG rewriteSourcesList()
2007-10-20 11:16:07,109 DEBUG examining: 'deb http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted'
2007-10-20 11:16:07,109 DEBUG entry 'deb http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted' updated to new dist
2007-10-20 11:16:07,110 DEBUG examining: 'deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted'
2007-10-20 11:16:07,110 DEBUG entry 'deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted' updated to new dist
2007-10-20 11:16:07,110 DEBUG examining: 'deb http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted'
2007-10-20 11:16:07,110 DEBUG entry 'deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted' updated to new dist
2007-10-20 11:16:07,110 DEBUG examining: 'deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted'
2007-10-20 11:16:07,111 DEBUG entry 'deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted' updated to new dist
2007-10-20 11:16:07,111 DEBUG examining: 'deb http://gb.archive.ubuntu.com/ubuntu/ feisty universe'
2007-10-20 11:16:07,111 DEBUG entry 'deb http://gb.archive.ubuntu.com/ubuntu/ gutsy universe' updated to new dist
2007-10-20 11:16:07,111 DEBUG examining: 'deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty universe'
2007-10-20 11:16:07,112 DEBUG entry 'deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy universe' updated to new dist
2007-10-20 11:16:07,112 DEBUG examining: 'deb http://gb.archive.ubuntu.com/ubuntu/ feisty multiverse'
2007-10-20 11:16:07,112 DEBUG entry 'deb http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse' updated to new dist
2007-10-20 11:16:07,113 DEBUG examining: 'deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty multiverse'
2007-10-20 11:16:07,113 DEBUG entry 'deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse' updated to new dist
2007-10-20 11:16:07,113 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu feisty-security main restricted'
2007-10-20 11:16:07,113 DEBUG entry 'deb http://security.ubuntu.com/ubuntu gutsy-security main restricted' updated to new dist
2007-10-20 11:16:07,114 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted'
2007-10-20 11:16:07,114 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted' updated to new dist
2007-10-20 11:16:07,114 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu feisty-security universe'
2007-10-20 11:16:07,114 DEBUG entry 'deb http://security.ubuntu.com/ubuntu gutsy-security universe' updated to new dist
2007-10-20 11:16:07,115 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu feisty-security universe'
2007-10-20 11:16:07,115 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu gutsy-security universe' updated to new dist
2007-10-20 11:16:07,115 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu feisty-security multiverse'
2007-10-20 11:16:07,115 DEBUG entry 'deb http://security.ubuntu.com/ubuntu gutsy-security multiverse' updated to new dist
2007-10-20 11:16:07,115 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse'
2007-10-20 11:16:07,116 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse' updated to new dist
2007-10-20 11:16:07,117 DEBUG examining: 'deb http://www.getautomatix.com/apt feisty main'
2007-10-20 11:16:07,121 DEBUG entry '# deb http://www.getautomatix.com/apt feisty main' was disabled (unknown mirror)
2007-10-20 11:16:07,121 DEBUG transitioned commerical to 'deb http://archive.canonical.com/ubuntu gutsy partner' 
2007-10-20 11:16:07,122 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse'
2007-10-20 11:16:07,122 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse' updated to new dist
2007-10-20 11:16:07,122 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse'
2007-10-20 11:16:07,122 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu gutsy-updates universe multiverse' updated to new dist
2007-10-20 11:16:07,123 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse'
2007-10-20 11:16:07,123 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse' updated to new dist
2007-10-20 11:16:54,589 DEBUG demoted: 'binfmt-support feisty-session-splashes gcj-4.1-base gij-4.1 gnome-cups-manager libgda2-3 libgda2-common libglib1.2 libgnomecupsui1.0-1c2a libgtk1.2 libgtk1.2-common liblzo1 libportaudio0 libslab0 libstlport5.1 openoffice.org-filter-mobiledev ttf-baekmuk vnc-common xvncviewer'
2007-10-20 11:17:33,892 DEBUG Removing 'xscreensaver' (ubuntu-desktop PostUpgradeRemove rule)
2007-10-20 11:17:34,068 DEBUG Removing 'gnome-cups-manager' (ubuntu-desktop PostUpgradeRemove rule)
2007-10-20 11:17:34,240 DEBUG Purging 'xorg-common' (Distro PostUpgradePurge rule)
2007-10-20 11:17:34,241 DEBUG Purging 'libgl1-mesa' (Distro PostUpgradePurge rule)
2007-10-20 11:17:34,241 DEBUG Purging 'ltsp-client' (Distro PostUpgradePurge rule)
2007-10-20 11:17:34,413 DEBUG Purging 'ltspfsd' (Distro PostUpgradePurge rule)
2007-10-20 11:17:34,584 DEBUG Purging 'python2.3' (Distro PostUpgradePurge rule)
2007-10-20 11:17:34,585 DEBUG running gutsyQuirks handler
2007-10-20 11:17:34,586 DEBUG found nfs mount in line 'nfsd /proc/fs/nfsd nfsd rw 0 0', marking nfs-common for install 
2007-10-20 11:17:34,757 DEBUG Kernel uname: '2.6.20-16-generic' 
2007-10-20 11:17:35,159 DEBUG Marking 'ubuntu-desktop' for upgrade
2007-10-20 11:17:36,708 DEBUG About to apply the following changes
2007-10-20 11:17:37,058 DEBUG Held-back: 
2007-10-20 11:17:37,058 DEBUG Remove: compiz-gtk libglew1 texlive-chemistry libopal-2.2.0 gnome-cups-manager libwnck18 libgnome-speech3 libmtp5 texlive-context dbus-1-utils libuniconf4.2 human-cursors-theme texlive-pdfetex texlive-full libnss3
2007-10-20 11:17:37,059 DEBUG Install: bluez-gnome splix libcairo-jni fast-user-switch-applet libtotem-plparser7 libgnome-vfs2.0-cil libswscale1d libdevmapper1.02.1 libcal3d12 libavutil1d libgcj7-1 libx264-54 libtrackerclient0 o3read libavformat1d libcompizconfig-backend-gconf liblwres30 linux-restricted-modules-2.6.22-14-generic libgtksourceview2.0-common libwnck22 libjasper1 python-sexy ttf-dejavu-extra libdb4.5 xdg-user-dirs libgda3-common libglew1.4 gcc-4.2-base pidgin-data libwpg-0.1-1 restricted-manager-core libnss3-0d libio-compress-base-perl libpurple0 libplot2c2 librpc-xml-perl libquicktime1 libkpathsea-dev gij-4.2 libode0debian1 linux-image-2.6.22-14-generic libwvstreams4.3-extras libmeanwhile1 lmodern linux-headers-2.6.22-14 hugin-data gutsy-wallpapers libxcb-shm0 texlive-humanities pidgin libatm1 xserver-xorg-video-amd bogofilter libiw29 libgs8 ttf-indic-fonts-core ubufox librsvg2.0-cil libsnmp10 libxcb-shape0 libneon26 libebml0 update-notifier-common autopano-sift tracker libjack0 libgraphviz3 pxljr libisc32 hugin-tools libdeskbar-tracker texlive-science guidance-backends libgd2-xpm linux-headers-2.6.22-14-generic libwvstreams4.3-base python-pygtksourceview libisccfg30 xvnc4viewer libpam-gnome-keyring libkeyutils1 libxcb1 libflac++6 python-zopeinterface bogofilter-bdb apturl libgtkhtml2.0-cil libgnome-speech7 libopenspc0 system-config-printer libpostproc1d libcompress-raw-zlib-perl libcompizconfig0 libgpod2 liblzo2-2 libio-compress-zlib-perl libsvg1 compiz-fusion-plugins-extra texlive-xetex libavahi-compat-libdnssd1 openbsd-inetd libservlet2.4-java python-cups libmtp6 tracker-search-tool libxcb-xv0 libmatroska0 libzephyr3 xdg-utils hugin-bin libgsl0 libpaper-utils libpcrecpp0 python-twisted-bin libterm-readkey-perl xdg-user-dirs-gtk libgcj8-1 libimlib2 xserver-xorg-video-psb libpano12-bin gcj-4.2-base ttf-unfonts-core tcpd librarian0 libart2.0-cil lame compiz-fusion-plugins-main libuniconf4.3 displayconfig-gtk xserver-xorg-video-intel libwxbase2.8-0 libtracker-gtk0 texlive-doc-tr context consolekit apparmor libgda3-3 libntfs-3g12 linux-ubuntu-modules-2.6.22-14-generic python-twisted-core libnspr4-0d libopal-2.2 enblend bogofilter-common libdns32 libisccc30 libgdl-gnome-1-0 ttf-dejavu-core libpoppler2 libwxgtk2.8-0 videotrans ghostscript libboost-thread1.34.1 libavcodec1d hal-cups-utils libpoppler-glib2 apparmor-utils libflac8 libglib-jni libgtksourceview2.0-0 libhesiod0 libbind9-30 ghostscript-x texlive-doc-zh dmz-cursor-theme
2007-10-20 11:17:37,059 DEBUG Upgrade: libbz2-1.0 libsane libarchive1 gnome-terminal hal esound-common wvdial python2.5-minimal libapm1 xserver-xorg-video-rendition base-files libsdl-ttf2.0-0 smartdimmer libglu1-mesa xserver-xorg-video-vesa net-tools libgtk2.0-bin texlive-fonts-extra libcupsimage2 listres texlive-doc-es texlive-doc-el texlive-doc-en xserver-xorg-video-sis gnome-applets-data gparted grub udev libmono-system1.0-cil libfaad2-0 dhcdbd python-launchpad-bugs libevent1 volumeid xauth unixodbc readahead util-linux-locales gnome-applets libegroupwise1.2-13 libk3b2 libc6-dev libuuid1 libgksu2-0 wpasupplicant libungif4g libmono-system-web2.0-cil libmono-system2.0-cil libxtrap6 libss2 libgnomecanvas2-0 libgmp3c2 xsane-common totem libofa0 powermanagement-interface gstreamer0.10-plugins-bad python-gtk2 libmono-system-web1.0-cil libbrlapi1 texlive-lang-norwegian texlive-lang-finnish openoffice.org-evolution libkpathsea4 libsasl2-2 gtk2-engines login compiz-plugins dvd+rw-tools texlive-lang-cyrillic texlive-doc-mn libgmime2.2-cil libgcrypt11 libatk1.0-0 bzip2 libglib2.0-cil libswt3.2-gtk-java libwrap0 cdparanoia hplip-data xclock mysql-server xdpyinfo gnome-media texlive-lang-portuguese libdbi-perl launchpad-integration apache2-utils restricted-manager p7zip-full libxres1 libnotify1 upstart-logd librecode0 brltty mysql-query-browser-common libthai-data docbook-xml hwdb-client-gnome libguile-ltdl-1 sun-java6-jdk libxrender1 python-bibtex texlive-base libice6 libicu36 libsqlite3-0 python-vte liblircclient0 xserver-xorg tzdata openoffice.org-base fftw3 ssh-askpass-gnome libgnome2-common libxine1-ffmpeg libxplc0.3.13 libgnome2-0 libnm-util0 python-gnomecanvas libwnck-common apport-gtk libgphoto2-2 netcat ruby1.8 libexpat1 bluez-utils xf86dga xsm gnome-games openssh-server nautilus-open-terminal python-gtkhtml2 libgucharmap6 scim-modules-socket texlive-metapost libusb-0.1-4 python2.4-minimal wodim libpam-foreground gstreamer0.10-gnomevfs gnome-system-monitor linux-restricted-modules-common e2fslibs gnome-terminal-data xserver-xorg-video-siliconmotion human-theme gnome-doc-utils language-selector kdebase-bin ifupdown hpijs ttf-tamil-fonts libscrollkeeper0 libdb4.3 libdb4.2 libdb4.4 glibc-doc texlive-doc-base xmodmap upstart-compat-sysv texlive-math-extra libncurses5 procps python-central texlive-lang-italian dia-gnome librsvg2-common gettext-base gnome-panel-data notification-daemon perl-modules p7zip python-gdbm cupsys-client gstreamer0.10-plugins-good passwd fontconfig libmetacity0 coreutils libgsf-1-114 ca-certificates iputils-tracepath xhost gnome-volume-manager gconf2-common ndiswrapper-common libxml2-utils texlive-base-bin python-sip4 libgcj-bc xserver-xorg-video-apm dselect libxi6 nautilus-sendto libldap2 libglib-perl bsdmainutils libebook1.2-9 locales gstreamer0.10-alsa texlive-games libpam-modules mplayer-skins libgpmg1 gnome-screensaver libjpeg62 openoffice.org-writer language-pack-gnome-en foomatic-filters python-notify exif libsdl-image1.2 mysql-common python-glade2 python-soya finger discover1 nautilus-share libaspell15 libbeagle0 libgtksourceview1.0-0 gnome-user-guide evolution-common update-manager feynmf libkonq4 smproxy ppp libbluetooth2 cupsys-bsd libxerces2-java texlive-doc-pt libpcre3 dictionaries-common texlive-doc-pl texlive-latex-extra xmore gnome-pilot initramfs-tools iso-codes xrgb apache2-mpm-prefork xresprobe xgamma xserver-xorg-video-savage lha discover1-data xserver-xorg-input-evdev gpgv binutils-static compiz-core mysql-client-5.0 gsfonts liboil0.3 gij-4.1 gnome-netstatus-applet gnome-orca feisty-gdm-themes dhcp3-common libxcursor1 tex4ht libglade2.0-cil xml-core libxext6 apt libgnomevfs2-extra aspell odbcinst1debian1 ktorrent ubuntu-artwork sysv-rc g++ libgnome-media0 libsigc++-2.0-0c2a texlive-lang-danish libsm6 libexif12 x11-common libx11-data xconsole xwud doc-base wine whiptail linux-libc-dev lcdf-typetools netbase gnome-games-data gnome-utils genisoimage gstreamer0.10-plugins-bad-multiverse libxml-twig-perl hwdb-client-common xman xmag libgdiplus libbonobo2-0 libxau6 texlive-bibtex-extra libgutenprint2 debianutils cpp libmono-cairo1.0-cil libmysqlclient15off libjline-java nfs-common texlive-doc-ko gamin libalut0 mysql-server-5.0 libgnutls13 libparted1.7-1 sed openoffice.org-thesaurus-en-us libnewt0.52 linux-image-generic unzip gstreamer0.10-esd gcalctool debconf-i18n libbonoboui2-common libsamplerate0 tex-common python libgtk-jni libsasl2-modules libavahi-core5 libpng12-0 thunderbird-locale-en-gb libesd-alsa0 python-bittorrent ttf-gujarati-fonts gnome-menus texlive-lang-other texlive-lang-armenian libx11-6 libmono-sqlite2.0-cil mono-common libndesk-dbus-glib1.0-cil acpi-support libxfont1 libqt3-mt python-xml libsmpeg0 cpp-4.1 findutils texlive-lang-czechslovak mencoder openoffice.org-l10n-en-gb libdc1394-13 module-init-tools gtk2-engines-pixbuf tcpdump libgcc1 libwxgtk2.6-0 amarok-xine gstreamer0.10-ffmpeg libopencdk8 graphviz ed libcurl3 libgdl-1-common gftp-common ubuntu-standard libedata-book1.2-2 apport dosfstools klogd dnsutils libmp4v2-0 totem-mozilla evolution-exchange libcdaudio1 libraw1394-8 bash ffmpeg gedit python-problem-report libhtml-tree-perl python-gnupginterface xserver-xorg-video-glint liburi-perl freeglut3 libpcap0.8 xkb-data xterm libxml-parser-perl firefox-gnome-support xserver-xorg-input-kbd mysql-admin-common qdvdauthor belocs-locales-bin alsa-utils sudo libasound2 libgstreamer0.10-0 klibc-utils libhal-storage1 acpid libgnome2.0-cil mono-runtime liblog4j1.2-java gcj-4.1-base mplayer eject libmpcdec3 python-apport libgnomekbdui1 libmdbtools evolution libmono-system-data2.0-cil laptop-detect gshare linux-headers-generic mono-gac libxevie1 xserver-xorg-video-voodoo brltty-x11 usplash-theme-ubuntu libgdl-1-0 libgnomekbd-common appres gnupg unace xwininfo dash ttf-oriya-fonts libavahi-common-data libxalan110 libglibmm-2.4-1c2a mysql-admin libcucul0 gnome-control-center libsmbclient libtasn1-3 iamerican python-tk libwpd8c2a texlive-lang-mongolian texlive-doc-fi texlive-doc-fr vorbis-tools libatspi1.0-0 lsb-release libgnomekbd1 whois ttf-punjabi-fonts toshset libxmu6 flashplugin-nonfree gnomebaker libmono-sharpzip2.84-cil cupsys-common ttf-dejavu libdbus-glib-1-2 rss-glx libglib-java inputattach sun-java6-jre ttf-devanagari-fonts texlive-lang-tibetan libemeraldengine0 libid3tag0 gnome-panel libgail-gnome-module cdrdao xsetmode libcamel1.2-10 iputils-arping libtiff4 libssl0.9.8 xditview xfonts-encodings apmd python-minimal liba52-0.7.4 system-services gcc-4.1 acidrip ncurses-base sound-juicer linux-sound-base software-properties-gtk debconf at-spi texlive-doc-nl libgnomeprint2.2-0 gnome-system-tools tcl8.4 libavahi-client3 xserver-xorg-video-ark libstdc++6-4.1-dev libgtkhtml2-0 mysql-client python-launchpad-integration ntfs-3g libmono1.0-cil texlive-lang-vietnamese gkrellm xserver-xorg-video-tga texlive-lang-croatian libhsqldb-java xserver-xorg-video-newport ttf-indic-fonts hplip amarok libxdamage1 apt-utils linux-restricted-modules-generic xlsatoms libmono-system-data1.0-cil texlive-lang-hungarian ico ttf-freefont libusplash0 librsvg2-2 samba-doc texlive-lang-african command-not-found-data libieee1284-3 libgstreamer-plugins-base0.10-0 gstreamer0.10-x libnautilus-burn4 gnome-mag libpango1.0-0 libncursesw5 libmono-sharpzip0.84-cil gnome-session python-dbus libarts1c2a libsepol1 texlive-doc-vi avahi-autoipd unattended-upgrades perl-base command-not-found libavahi-common3 libnfsidmap2 libxrandr2 libexchange-storage1.2-3 libwavpack1 update-notifier ttf-malayalam-fonts ibritish libpaper1 alacarte gnome-accessibility-themes openoffice.org-draw viewres libx86-1 xpmutils libcairomm-1.0-1 libmad0 ndiswrapper-utils-1.9 fuse-utils xlogo mktemp libdecoration0 xsetpointer emerald slocate libmjpegtools0c2a esound myspell-en-gb libdvdread3 libgtk-java libpisock9 php5 scim gnome-cards-data libgtk2.0-cil lm-sensors sun-java6-plugin ubuntu-docs libscim8c2a libfreetype6 memtest86+ wireshark-common xeyes sox fortunes-min xbase-clients ethtool libltdl3 texlive-publishers xvinfo xserver-xorg-video-s3 liborbit2 libnl1-pre6 libcairo-java libxklavier11 screen libnautilus-extension1 libselinux1 texlive-omega libgconf2-4 libgtkhtml3.14-19 texlive-pstricks gedit-common samba-common ssl-cert libxinerama1 libopenal0a xfontsel libxaw7 openoffice.org-java-common xserver-xorg-input-wacom dpkg ttf-arphic-uming libgnomevfs2-bin python-gnome2-desktop libgnome-desktop-2 imagemagick binutils build-essential xlsclients libpulse0 console-terminus texlive-doc-it readline-common libnet-dbus-perl python-cairo texlive-latex-base libdbus-1-3 xcalc libgtk2.0-common alsa-oss libgmime-2.0-2 mesa-utils libcurl3-gnutls unzoo libxpm4 libdirectfb-0.9-25 ucf gdebi-core libdv4 java-common xsltproc ispell gnome-mime-data xgc scim-modules-table myspell-en-za gstreamer0.10-plugins-ugly libidl0 evolution-webcal libmagic1 pfb2t1c2pfb python-gnome2 libcompress-zlib-perl mkisofs gconf2 python-imaging ekiga texlive-doc-uk python-gobject konsole cupsys-driver-gutenprint poppler-utils xserver-xorg-video-via zenity libstlport5.1 libgphoto2-port0 libxtst6 openoffice.org-filter-mobiledev vnc-common mozilla-mplayer nano capplets-data hugin libruby1.8 nautilus libxvmc1 xutils guile-1.6-libs libmusicbrainz4c2a libgsf-1-common librpcsecgss3 libcdparanoia0 texlive-lang-latin openoffice.org-calc gnome-themes libsdl1.2debian alsa-base ubuntu-minimal xserver-xorg-video-i128 libavahi-glib1 feisty-wallpapers libsensors3 gksu evolution-data-server-common compiz libbonobo2-common libswt3.2-gtk-jni gnome-desktop-data libedit2 openoffice.org-style-human vlc-nox xserver-xorg-video-nv libgnome-keyring0 libqthreads-12 zlib1g liboobs-1-3 libcomerr2 evolution-data-server foomatic-db-hpijs libjack0.100.0-0 xwd libxss1 espeak-data acpi plib1.8.4c2 libfontconfig1 python-imaging-tk libart-2.0-2 gphpedit k3b libgcj-common util-linux libgconf2.0-cil dvdauthor libmodplug0c2 libpano12-0 libsdl-mixer1.2 metacity-common gtkhtml3.14 libgnomevfs2-common file texlive-doc-de makedev libgssapi2 openoffice.org-math sun-java6-bin xserver-xorg-video-all python-virtkey pciutils mono-jit libarchive-zip-perl texlive-lang-hebrew desktop-file-utils texlive-lang-dutch nfs-kernel-server openoffice.org-impress gthumb libecal1.2-7 vlc libc6-i686 python2.5 python2.4 linux-generic gnome-nettool libgtop2-7 hal-device-manager gramps libxfixes3 libxt6 dbus libgail18 pgf xutils-dev gnome-icon-theme libgnome-window-settings1 myspell-en-us sysvutils ltrace cupsys mcpp libwxbase2.6-0 python-numeric apache2.2-common compiz-gnome parted latex-beamer xvidtune xserver-xorg-video-ati bsh libvte-common f-spot libaa1 gij libslang2 xserver-xorg-video-nsc xmessage gs-esp texlive-fonts-recommended xorg python-gst0.10 ttf-telugu-fonts psmisc openoffice.org-gnome fontconfig-config xload openoffice.org gstreamer0.10-plugins-base-apps x-ttcidfont-conf libvorbis0a xscreensaver-gl pppconfig libcairo-perl gnome-keyring mount rhythmbox liblcms1 samba apache2 libarchive-tar-perl libgtk2.0-0 libgnomeprintui2.2-common dia-common libreadline5 xlsfonts libxmuu1 xsane language-pack-gnome-en-base console-setup libmono-data-tds2.0-cil libgtop2-common texlive-formats-extra gcc-4.1-base startup-tasks man-db texlive-doc-th python-libxml2 libgtkmm-2.4-1c2a gucharmap texlive-plain-extra pkg-config xvncviewer busybox-initramfs libvorbisenc2 xkill tomboy libgnome-pilot2 tangerine-icon-theme mozilla-firefox-locale-en-gb libespeak1 libxkbfile1 texlive-lang-polish scrollkeeper python-uno gnome-mount libmagick9 libtunepimp5 xrandr libartsc0 vim-tiny gaim texlive-lang-greek libavahi1.0-cil nautilus-cd-burner tango-icon-theme mjpegtools texlive-latex3 initscripts liblaunchpad-integration0 libdrm2 texlive-lang-spanish gnome-power-manager bittorrent libapr1 swat tsclient gstreamer0.10-plugins-base libklibc binfmt-support diff texlive gzip hotkey-setup bind9-host sysklogd openssh-client update-inetd libgtkspell0 php5-mysql time gimp-python libxcomposite1 gnome-about gstreamer0.10-tools libpam-runtime libpango1.0-common libkrb53 tasksel-data libportaudio0 cli-common file-roller iproute libhunspell-1.1-0 libxvidcore4 libstdc++5 libstdc++6 manpages libpt-plugins-alsa gdb gdm libgpg-error0 totem-gstreamer libedataserver1.2-9 e2fsprogs openoffice.org-l10n-common fortune-mod mysql-query-browser libglade2-0 libpt-plugins-v4l system-tools-backends soundconverter liblocale-gettext-perl ftp wireless-tools python-pyorbit human-icon-theme rdesktop libeel2-2 upstart metacity bluez-cups popularity-contest laptop-mode-tools libedataserverui1.2-8 g++-4.1 wget wireshark nautilus-data firefox xserver-xorg-input-mouse app-install-data-commercial libidn11 hdparm hddtemp libdiscover1 libgnome-menu2 libhal1 language-selector-common libxml2 iceauth php5-common vim-common less dmidecode eog gtk2-engines-ubuntulooks python-gconf python-support libavahi-qt3-1 ntp libsdl1.2debian-alsa iputils-ping libmono-corlib1.0-cil iptables onboard libhtml-parser-perl libgnomecanvas2-common openoffice.org-common usplash libgksuui1.0-1 xbitmaps tasksel musixtex texlive-generic-extra gstreamer0.10-plugins-ugly-multiverse bug-buddy gcc-3.3-base openoffice.org-gtk gnome-btdownload dmsetup beforelight python-software-properties libsnmp-base texlive-extra-utils dia-libs libapache2-mod-auth-mysql texinfo libblkid1 bitmap texlive-generic-recommended texlive-lang-german libdbd-mysql-perl libthai0 ndisgtk espeak kdebase-kio-plugins texlive-lang-french libcap1 xrdb portmap xserver-xorg-input-all tex4ht-common libgtksourceview-common libcairo2 libgutenprintui2-1 gs-esp-x xserver-xorg-input-synaptics libgamin0 ttf-kannada-fonts gimp gconf-editor libgnome-mag2 gnome-media-common libelfg0 info texlive-lang-manju hal-info oclock libbonoboui2-0 texlive-latex-recommended gimp-data gdebi lshw kdelibs4c2a kdelibs-data reiserfsprogs unrar shared-mime-info language-pack-en texlive-pictures gnome-app-install editres gftp-gtk ttf-opensymbol texlive-doc-bg libmms0 xserver-xorg-video-i810 nvidia-glx libxine1 ncurses-bin network-manager libpq5 libmono2.0-cil libfontenc1 ubuntu-desktop libmono-corlib2.0-cil libgnomeprintui2.2-0 libpisync0 libapache2-mod-php5 xserver-xorg-video-mga python-gnome2-extras dvd-slideshow mtr-tiny texlive-lang-indic base-passwd update-manager-core avahi-daemon contact-lookup-applet perl gnome-keyring-manager gs-common libwmf0.2-7 kdesktop libconsole libsysfs2 xstdcmap libgnomeui-common libxslt1.1 texlive-music libswfdec0.3 texlive-font-utils ttf-arphic-ukai icedax manpages-dev aptitude libgl1-mesa-glx libgail-common xbiff libfuse2 libxalan2-java python-orca-brlapi tk8.4 libfreebob0 libdvdnav4 gnome-pilot-conduits texlive-doc-ja libwps-0.1-1 vino libnss-mdns libaudio2 xserver-xorg-core openoffice.org-core libvlc0 texlive-doc-cs+sk libc6 preview-latex-style serpentine dhcp3-client language-pack-en-base liblame0 python-gmenu lftp foomatic-db network-manager-gnome libao2 gcc cups-pdf libgnomevfs2-0 libmono0 synaptic xscreensaver-data python-qt3 libvolume-id0 strace libdvbpsi4 xclipboard evince libxv1 texlive-lang-ukenglish foo2zjs pppoeconf yelp libcupsys2 xfd libnm-glib0 libxft2 libpam0g libgimp2.0 adduser openprinting-ppds console-tools openssl libmono-data-tds1.0-cil ntpdate firestarter bsdutils libperl5.8 python-apt sessreg scim-tables-additional libmono-security1.0-cil openoffice.org-help-en-us texlive-doc-ru liblpint-bonobo0 libpanel-applet2-0 evolution-plugins ubuntu-keyring libenchant1c2a libsndfile1 texlive-lang-swedish ttf-arabeyes libvte9 lsb-base libdjvulibre15 cpio libgnomeprint2.2-data smbclient libpt-plugins-v4l2 libgnomeui-0 kile rsync libeel2-data usbutils ttf-bengali-fonts openoffice.org-l10n-en-za libmono-security2.0-cil libcroco3 ttf-thai-tlwg libglib2.0-0 defoma gimp-print libvorbisfile3 libopenexr2c2a arj lsof scim-gtk2-immodule libpt-1.10.0 libtag1c2a deskbar-applet libcaca0 libgsm1 tar xserver-xorg-video-tseng python-at-spi libdaemon0 arabtex app-install-data cdrecord foomatic-db-engine libedata-cal1.2-6 texlive-common libsexy2 xsetroot libgl1-mesa-dri libxdmcp6 dpkg-dev
2007-10-20 11:17:37,062 DEBUG Free space on /: 12212604928
2007-10-20 11:17:37,063 DEBUG Dir /usr mounted on /
2007-10-20 11:17:37,064 DEBUG Dir /var mounted on /
2007-10-20 11:17:37,064 DEBUG Free space on /boot: 155856896
2007-10-20 11:17:37,065 DEBUG Dir /var/cache/apt/archives mounted on /
2007-10-20 11:17:37,066 DEBUG Free space on /home: 10121027584
2007-10-20 11:17:37,067 DEBUG fs_free contains: '{'/var': <DistUpgradeControler.FreeSpace object at 0xa7c15ec>, '/home': <DistUpgradeControler.FreeSpace object at 0xa7c170c>, '/boot': <DistUpgradeControler.FreeSpace object at 0xa7c16cc>, '/usr': <DistUpgradeControler.FreeSpace object at 0xa7c15ec>, '/': <DistUpgradeControler.FreeSpace object at 0xa7c15ec>, '/var/cache/apt/archives': <DistUpgradeControler.FreeSpace object at 0xa7c15ec>}'
2007-10-20 11:17:37,091 DEBUG linux-image-2.6.20-16-generic (upgrade|installed) added with 10485760 to boot space
2007-10-20 11:17:37,147 DEBUG linux-image-2.6.22-14-generic (new-install) added with 10485760 to boot space
2007-10-20 11:17:37,344 DEBUG linux-image-2.6.20-15-generic (upgrade|installed) added with 10485760 to boot space
2007-10-20 11:17:38,211 DEBUG dir '/var/cache/apt/archives' needs '1366625556.0' of '<DistUpgradeControler.FreeSpace object at 0xa7c15ec>' (12212604928.000000)
2007-10-20 11:17:38,211 DEBUG dir '/usr' needs '782180352.0' of '<DistUpgradeControler.FreeSpace object at 0xa7c15ec>' (10845979372.000000)
2007-10-20 11:17:38,212 DEBUG dir '/usr' needs '52428800' of '<DistUpgradeControler.FreeSpace object at 0xa7c15ec>' (10063799020.000000)
2007-10-20 11:17:38,212 DEBUG dir '/boot' needs '31457280' of '<DistUpgradeControler.FreeSpace object at 0xa7c16cc>' (155856896.000000)
2007-10-20 11:17:38,212 DEBUG dir '/' needs '10485760' of '<DistUpgradeControler.FreeSpace object at 0xa7c15ec>' (10011370220.000000)
2007-10-20 11:18:11,971 INFO using backports in '/tmp/tmpGv4rOc/backports' 
2007-10-20 11:18:11,972 DEBUG have: ['/tmp/tmpGv4rOc/backports/release-upgrader-apt_0.6.46.4ubuntu10.3_i386.udeb', '/tmp/tmpGv4rOc/backports/release-upgrader-dpkg_1.14.5ubuntu11.2_i386.udeb']
2007-10-20 11:18:11,973 DEBUG setting MinAge to 10
2007-10-20 11:18:11,975 DEBUG no file '/etc/apt/apt.conf.d/25adept-archive-limits'
2007-10-20 12:51:37,778 INFO cache.commit()
2007-10-20 12:56:51,088 ERROR got an error from dpkg for pkg: 'libpam0g': 'subprocess post-installation script killed by signal (Aborted), core dumped
'
2007-10-20 12:56:51,139 ERROR got an error from dpkg for pkg: 'libpam0g': 'subprocess post-installation script killed by signal (Aborted), core dumped
'
2007-10-20 12:58:53,473 ERROR got an error from dpkg for pkg: 'libpam-modules': 'dependency problems - leaving unconfigured
'
2007-10-20 12:58:53,793 ERROR got an error from dpkg for pkg: 'libpam-modules': 'dependency problems - leaving unconfigured
'
2007-10-20 12:59:31,733 ERROR got an error from dpkg for pkg: 'login': 'dependency problems - leaving unconfigured
'
2007-10-20 12:59:31,753 ERROR got an error from dpkg for pkg: 'login': 'dependency problems - leaving unconfigured
'
2007-10-20 13:14:53,888 ERROR got an error from dpkg for pkg: 'base-files': 'dependency problems - leaving unconfigured
'
2007-10-20 13:14:53,963 ERROR got an error from dpkg for pkg: 'base-files': 'dependency problems - leaving unconfigured
'
2007-10-20 13:45:40,814 WARNING no activity on terminal for 240 seconds (Preparing to configure base-files)
2007-10-20 13:45:40,968 ERROR got an error from dpkg for pkg: 'bash': 'dependency problems - leaving unconfigured
'
2007-10-20 13:45:40,998 ERROR got an error from dpkg for pkg: 'bash': 'dependency problems - leaving unconfigured
'
2007-10-20 13:45:57,912 ERROR got an error from dpkg for pkg: 'passwd': 'dependency problems - leaving unconfigured
'
2007-10-20 13:45:57,928 ERROR got an error from dpkg for pkg: 'passwd': 'dependency problems - leaving unconfigured
'
2007-10-20 13:46:07,584 ERROR got an error from dpkg for pkg: 'adduser': 'dependency problems - leaving unconfigured
'
2007-10-20 13:46:07,600 ERROR got an error from dpkg for pkg: 'adduser': 'dependency problems - leaving unconfigured
'
2007-10-20 13:46:15,148 ERROR got an error from dpkg for pkg: 'fuse-utils': 'dependency problems - leaving unconfigured
'
2007-10-20 13:46:15,164 ERROR got an error from dpkg for pkg: 'fuse-utils': 'dependency problems - leaving unconfigured
'
2007-10-20 13:46:25,308 ERROR got an error from dpkg for pkg: 'ssl-cert': 'dependency problems - leaving unconfigured
'
2007-10-20 13:46:25,322 ERROR got an error from dpkg for pkg: 'ssl-cert': 'dependency problems - leaving unconfigured
'
2007-10-20 13:46:32,892 ERROR got an error from dpkg for pkg: 'cupsys': 'dependency problems - leaving unconfigured
'
2007-10-20 13:46:32,911 ERROR got an error from dpkg for pkg: 'cupsys': 'dependency problems - leaving unconfigured
'
2007-10-20 13:49:26,193 ERROR got an error from dpkg for pkg: 'dbus': 'dependency problems - leaving unconfigured
'
2007-10-20 13:49:26,261 ERROR got an error from dpkg for pkg: 'dbus': 'dependency problems - leaving unconfigured
'
2007-10-20 13:49:44,944 ERROR got an error from dpkg for pkg: 'libgnomevfs2-0': 'dependency problems - leaving unconfigured
'
2007-10-20 13:49:44,960 ERROR got an error from dpkg for pkg: 'libgnomevfs2-0': 'dependency problems - leaving unconfigured
'
2007-10-20 13:49:51,716 ERROR got an error from dpkg for pkg: 'libgnome2-0': 'dependency problems - leaving unconfigured
'
2007-10-20 13:49:51,769 ERROR got an error from dpkg for pkg: 'libgnome2-0': 'dependency problems - leaving unconfigured
'
2007-10-20 13:53:13,690 ERROR got an error from dpkg for pkg: 'libbonoboui2-0': 'dependency problems - leaving unconfigured
'
2007-10-20 13:53:13,780 ERROR got an error from dpkg for pkg: 'libbonoboui2-0': 'dependency problems - leaving unconfigured
'
2007-10-20 13:53:24,945 ERROR got an error from dpkg for pkg: 'libgnomeui-0': 'dependency problems - leaving unconfigured
'
2007-10-20 13:53:24,962 ERROR got an error from dpkg for pkg: 'libgnomeui-0': 'dependency problems - leaving unconfigured
'
2007-10-20 13:53:33,105 ERROR got an error from dpkg for pkg: 'libgnome-desktop-2': 'dependency problems - leaving unconfigured
'
2007-10-20 13:53:33,128 ERROR got an error from dpkg for pkg: 'libgnome-desktop-2': 'dependency problems - leaving unconfigured
'
2007-10-20 13:53:39,904 ERROR got an error from dpkg for pkg: 'libgnome-menu2': 'dependency problems - leaving unconfigured
'
2007-10-20 13:53:39,928 ERROR got an error from dpkg for pkg: 'libgnome-menu2': 'dependency problems - leaving unconfigured
'
2007-10-20 13:53:44,920 ERROR got an error from dpkg for pkg: 'libpanel-applet2-0': 'dependency problems - leaving unconfigured
'
2007-10-20 13:53:45,010 ERROR got an error from dpkg for pkg: 'libpanel-applet2-0': 'dependency problems - leaving unconfigured
'
2007-10-20 13:53:50,071 ERROR got an error from dpkg for pkg: 'libgnome-window-settings1': 'dependency problems - leaving unconfigured
'
2007-10-20 13:53:50,088 ERROR got an error from dpkg for pkg: 'libgnome-window-settings1': 'dependency problems - leaving unconfigured
'
2007-10-20 13:53:55,712 ERROR got an error from dpkg for pkg: 'compiz-gnome': 'dependency problems - leaving unconfigured
'
2007-10-20 13:53:55,761 ERROR got an error from dpkg for pkg: 'compiz-gnome': 'dependency problems - leaving unconfigured
'
2007-10-20 13:53:59,776 ERROR got an error from dpkg for pkg: 'compiz': 'dependency problems - leaving unconfigured
'
2007-10-20 13:53:59,800 ERROR got an error from dpkg for pkg: 'compiz': 'dependency problems - leaving unconfigured
'
2007-10-20 13:56:27,949 ERROR got an error from dpkg for pkg: 'sudo': 'dependency problems - leaving unconfigured
'
2007-10-20 13:56:27,999 ERROR got an error from dpkg for pkg: 'sudo': 'dependency problems - leaving unconfigured
'
2007-10-20 13:56:43,749 ERROR got an error from dpkg for pkg: 'gksu': 'dependency problems - leaving unconfigured
'
2007-10-20 13:56:43,851 ERROR got an error from dpkg for pkg: 'gksu': 'dependency problems - leaving unconfigured
'
2007-10-20 13:56:52,141 ERROR got an error from dpkg for pkg: 'update-manager': 'dependency problems - leaving unconfigured
'
2007-10-20 13:56:52,161 ERROR got an error from dpkg for pkg: 'update-manager': 'dependency problems - leaving unconfigured
'
2007-10-20 13:56:55,815 DEBUG got a conffile-prompt from dpkg for file: '/etc/modprobe.d/blacklist'
2007-10-20 13:57:26,965 ERROR got an error from dpkg for pkg: 'udev': 'dependency problems - leaving unconfigured
'
2007-10-20 13:57:26,993 ERROR got an error from dpkg for pkg: 'udev': 'dependency problems - leaving unconfigured
'
2007-10-20 13:57:32,993 ERROR got an error from dpkg for pkg: 'hal': 'dependency problems - leaving unconfigured
'
2007-10-20 13:57:33,008 ERROR got an error from dpkg for pkg: 'hal': 'dependency problems - leaving unconfigured
'
2007-10-20 13:57:47,676 ERROR got an error from dpkg for pkg: 'update-notifier': 'dependency problems - leaving unconfigured
'
2007-10-20 13:57:47,692 ERROR got an error from dpkg for pkg: 'update-notifier': 'dependency problems - leaving unconfigured
'
2007-10-20 13:57:53,413 ERROR got an error from dpkg for pkg: 'gnome-power-manager': 'dependency problems - leaving unconfigured
'
2007-10-20 13:57:53,428 ERROR got an error from dpkg for pkg: 'gnome-power-manager': 'dependency problems - leaving unconfigured
'
2007-10-20 13:58:01,752 ERROR got an error from dpkg for pkg: 'libgucharmap6': 'dependency problems - leaving unconfigured
'
2007-10-20 13:58:01,772 ERROR got an error from dpkg for pkg: 'libgucharmap6': 'dependency problems - leaving unconfigured
'
2007-10-20 13:58:08,687 ERROR got an error from dpkg for pkg: 'gucharmap': 'dependency problems - leaving unconfigured
'
2007-10-20 13:58:08,708 ERROR got an error from dpkg for pkg: 'gucharmap': 'dependency problems - leaving unconfigured
'
2007-10-20 13:58:12,968 ERROR got an error from dpkg for pkg: 'libcamel1.2-10': 'dependency problems - leaving unconfigured
'
2007-10-20 13:58:12,988 ERROR got an error from dpkg for pkg: 'libcamel1.2-10': 'dependency problems - leaving unconfigured
'
2007-10-20 13:58:19,864 ERROR got an error from dpkg for pkg: 'libebook1.2-9': 'dependency problems - leaving unconfigured
'
2007-10-20 13:58:19,929 ERROR got an error from dpkg for pkg: 'libebook1.2-9': 'dependency problems - leaving unconfigured
'
2007-10-20 13:58:24,200 ERROR got an error from dpkg for pkg: 'libecal1.2-7': 'dependency problems - leaving unconfigured
'
2007-10-20 13:58:24,228 ERROR got an error from dpkg for pkg: 'libecal1.2-7': 'dependency problems - leaving unconfigured
'
2007-10-20 13:58:29,316 ERROR got an error from dpkg for pkg: 'libedataserverui1.2-8': 'dependency problems - leaving unconfigured
'
2007-10-20 13:58:29,331 ERROR got an error from dpkg for pkg: 'libedataserverui1.2-8': 'dependency problems - leaving unconfigured
'
2007-10-20 13:58:36,763 ERROR got an error from dpkg for pkg: 'liblpint-bonobo0': 'dependency problems - leaving unconfigured
'
2007-10-20 13:58:36,801 ERROR got an error from dpkg for pkg: 'liblpint-bonobo0': 'dependency problems - leaving unconfigured
'
2007-10-20 13:58:41,864 ERROR got an error from dpkg for pkg: 'libnautilus-extension1': 'dependency problems - leaving unconfigured
'
2007-10-20 13:58:41,918 ERROR got an error from dpkg for pkg: 'libnautilus-extension1': 'dependency problems - leaving unconfigured
'
2007-10-20 13:58:48,320 ERROR SystemError from cache.commit(): installArchives() failed
```
Its the bottom part that has all the errors but it still seems to be updating various packages still at the moment. Any idea of what to do or anyone had a similar problem??

---

### Post by rich86 on 2007-10-20
OK after running dpkg --configure -a and running apt-get and trying to install sp,e packages that it said didn't install correctly i took the plunge and rebooted. Nowe when i boot it crashes on the new kernal(think 2.16.22?) and if i use an older one it boots but i have no screen. i can use ctrl+atl+F5 to get a terminal. i have changed the Xorg.conf file back to a failsafe one but still no help, and still does a hard crash on boot.
If i run in recovery i get a hard crash on boot as well using the newest kernal, any ideas??

---

### Post by hugmenot on 2007-10-22
If you can boot to a virtual console (black terminal), and have internet at this point, try installing ubuntu-standard, ubuntu-minimal, and ubuntu-desktop again, and see if you have all necessary packages installed.
I couldn't figure out from your log what the actual dependency problems were.

To figure out what the Xorg problem is, inspect the file /var/log/Xorg.0.log
You can read it with "less".

On the bottom it specifies the problem. It&#8217;s likely a problem with the nvidia driver module, or something similar.

---

### Post by rich86 on 2007-10-22
hi thanks for the reply but i needed to do some work to just reinstalled feisty, when i next try i will try your suggestions if i have a problem.
Thanks anyway

---

### Post by hugmenot on 2007-10-22
Shouldn't you have installed Gutsy instead?

---

### Post by rich86 on 2007-10-22
in hindsight maybe but i couldn't download it i need an install to get the wireless working, can't use it from live CD.
Oh well i will try in a few weeks when i have a bit more free time

---

### Post by darkazurka on 2007-10-23
I downloaded the gutsy CD the first thing I did. It helped because my upgrade failed because when I rebooted with the upgraded system (7.10) then it didn't show anything at all, and in recovery mode it worked for 23 seconds, then it stopped. (all while complaining about usb errors)

---

### Post by djaquay on 2007-10-23
I've got the same problem as the first post in this thread.  The libpam0g install dumped core, and a bunch of things after that failed on dependencies.  I have yet to finish the install (47 minutes remaining), and I'm hoping for some help before I try to reboot.  It appears to be doing a 'dpkg --configure -a'; should this take care of things, perhaps?

Is there a way to try again?

Thanks,
Dave

---

### Post by hugmenot on 2007-10-23
dpkg --configure -a is used when a previous apt run was interrupted (as in crash) and unconfigured packages are remaining.You certasinly have to make sure that no conflicts remain when you reboot. Also make sure that the ubuntu-{minimal,standard,desktop} packages are installed.

---

### Post by djaquay on 2007-10-23
Ah, okay, well dpkg finished running, and now I don't seem to have a network.  I'm thinking of rebooting, and if that doesn't work (which seems likely), trying to resuscitate it with a 7.10 live CD.  Sound reasonable?

Thanks very much,
Dave

---

### Post by djaquay on 2007-10-23
Wow.  I'm still nervous, but I rebooted, and all looks well.  update-manager and synaptic both say everything is up to date, and everything seems to be coming back up just fine.

Dave

---

