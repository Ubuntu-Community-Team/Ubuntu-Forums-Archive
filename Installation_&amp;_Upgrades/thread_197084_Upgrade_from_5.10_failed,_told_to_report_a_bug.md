---
title: "Upgrade from 5.10 failed, told to report a bug"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by knapper on 2006-06-15
Hello all,

Last night I decieded to upgrade a test server I use for web development from 5.10 to 6.06. All seemed to be going well untill quite a way into the installation I hit a fatal error, which told me to report it as a bug and including with the report 2 files. I thought it better to post here first rather than rushing off to report a bug incase someone can spot the problem. I'll put the first file below and post the second, dist-upgrade-apt.log, in a second post to make them easier to read.

Thanks for any information,

knapper 

dist-upgrade.log:

2006-06-14 21:53:51,546 DEBUG Foreign: 
2006-06-14 21:53:51,561 DEBUG Obsolete: opera
2006-06-14 21:53:51,567 DEBUG updateSourcesList()
2006-06-14 21:53:51,597 DEBUG rewriteSourcesList()
2006-06-14 21:53:51,627 DEBUG examining: 'deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted'
2006-06-14 21:53:51,629 DEBUG entry 'deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper main restricted' updated to new dist
2006-06-14 21:53:51,630 DEBUG examining: 'deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted'
2006-06-14 21:53:51,632 DEBUG entry 'deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper main restricted' updated to new dist
2006-06-14 21:53:51,633 DEBUG examining: 'deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted'
2006-06-14 21:53:51,635 DEBUG entry 'deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper-updates main restricted' updated to new dist
2006-06-14 21:53:51,636 DEBUG examining: 'deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted'
2006-06-14 21:53:51,638 DEBUG entry 'deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) dapper-updates main restricted' updated to new dist
2006-06-14 21:53:51,639 DEBUG examining: 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted'
2006-06-14 21:53:51,640 DEBUG entry 'deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted' updated to new dist
2006-06-14 21:53:51,642 DEBUG examining: 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted'
2006-06-14 21:53:51,643 DEBUG entry 'deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted' updated to new dist
2006-06-14 21:54:00,255 DEBUG Marking 'ubuntu-desktop' for upgrade
2006-06-14 21:54:00,331 DEBUG Removing 'xchat' (ubuntu-desktop PostUpgradeRemove rule)
2006-06-14 21:54:00,422 DEBUG Removing 'xscreensaver' (ubuntu-desktop PostUpgradeRemove rule)
2006-06-14 21:54:00,426 DEBUG Purging 'xorg-common' (Distro PostUpgradePurge rule)
2006-06-14 21:54:00,428 DEBUG running dapperQuirks handler
2006-06-14 21:54:01,517 DEBUG About to apply the following changes
2006-06-14 21:54:01,691 DEBUG Remove: libid3-3.8.3c2 libreadline4 libglibmm-2.4-1c2 xmkmf xchat-common xscreensaver libgksuui1.0-0 openoffice.org2 smeg libgksu1.2-0 libnotify0 libgnomecupsui1.0-1 libnautilus-burn2 x-common busybox-cvs-initramfs openoffice.org2-base hotplug xorg-driver-synaptics libgcj6 libopenh323-1.15.3c2 libgtkmm-2.4-1c2 gparted libwpd8c2 libpt-1.8.3c2 base-config gnomemeeting openoffice.org2-draw netcdfg3 openoffice.org2-writer openoffice.org-debian-files libdbus-glib-1-1 xorg-common libgcj6-common openoffice.org2-help-en-us openoffice.org2-common libcamel1.2-6 gij-4.0 ifrename libsigc++-2.0-0c2 cupsys-driver-gimpprint-data hplip-base libdbus-1-1 openoffice.org2-math openoffice.org2-java-common openoffice.org2-impress openoffice.org2-core openoffice.org2-gnome xchat openoffice.org2-l10n-en-us xserver-common libmusicbrainz4c2 openoffice.org2-evolution openoffice.org2-calc
2006-06-14 21:54:01,693 DEBUG Install: scim-gtk2-immodule gtk2-engines-ubuntulooks openoffice.org-writer gnome-power-manager libgdl-1-0 festlex-cmu libxfont1 brltty-x11 libcupsys2 x11-common intltool-debian gstreamer0.10-plugins-base libsnmp9 scim-modules-socket festlex-poslex radeontool deskbar-applet openoffice.org-l10n-en-za festival libpam-foreground libopenobex-1.0-0 smartdimmer laptop-mode-tools libscim8c2a gstreamer0.10-gnomevfs iso-codes gstreamer0.10-plugins-base-apps openoffice.org-help-en-us hplip libbtctl2 openoffice.org-common linux-image-2.6.15-23-386 libavahi-common-data openoffice.org-thesaurus-en-us libgksuui1.0-1 liblwres9 libgnomecupsui1.0-1c2a libbeagle0 libgdl-1-common libsysfs2 libisc11 python2.4-soappy mdetect python-gnome2-desktop libgksu1.2-1 libavahi-common3 libnotify1 gstreamer0.10-x libxmlsec1-nss libxplc0.3.13 libnautilus-burn3 gnome-mag xcursor-themes libneon25 min12xxw ttf-lao readline-common openoffice.org-gtk python-gst0.10 xserver-xorg-driver-voodoo brltty libxmlsec1-openssl libwpd8c2a openoffice.org-gnome ekiga libgmp3c2 libgcj7 linux-restricted-modules-2.6.15-23-386 libedataserver1.2-7 xserver-xorg-driver-all libdevmapper1.02 cupsys-driver-gutenprint libdns21 libestools1.2 libsepol1 libwvstreams4.2-base libegroupwise1.2-9 libatspi1.0-0 libicu34 libopal-2.2.0 libgnome-speech3 pcmciautils gtk2-engines-highcontrast irssi screensaver-default-images libxmlsec1 openoffice.org-base ttf-arphic-ukai poppler-utils libmysqlclient15off at-spi libwvstreams4.2-extras libjline-java language-selector-common libtag1c2a libtotem-plparser1 libexchange-storage1.2-1 openoffice.org-l10n-common libgcj7-jar libgpod0 openoffice.org-math libdmx1 xserver-xorg-input-all libkpathsea4 python2.4-gobject ttf-dejavu openoffice.org-l10n-en-us libdbus-glib-1-2 ttf-thai-tlwg gstreamer0.10-tools unattended-upgrades openoffice.org-l10n-en-gb xserver-xorg-input-evdev gstreamer0.10-plugins-good alacarte openoffice.org-java-common libmusicbrainz4c2a libgutenprintui2-1 ttf-arphic-uming libgnomevfs2-bin gimp-print ubuntu-base python-libxml2 vim-runtime libgnutls12 inputattach xserver-xorg-input-synaptics mysql-client-5.0 gnome-accessibility-themes openoffice.org-draw libcamel1.2-8 libgsf-1-common openoffice.org-core tango-icon-theme-common libgnome-mag2 libpt-1.10.0 libgsf-1-113 ca-certificates gok busybox-initramfs openoffice.org-impress landscape-client libgail-gnome-module festvox-kallpc16k po-debconf tangerine-icon-theme cdrdao gnopernicus gconf2-common libglew1 openoffice.org-calc libssl0.9.8 libid3-3.8.3c2a gstreamer0.10-esd libcdio6 mysql-server-5.0 belocs-locales-bin libdbus-1-2 app-install-data-commercial wpasupplicant libgtop2-7 openoffice.org libgnomevfs2-extra libmagick9 gij-4.1 libgstreamer0.10-0 openoffice.org-evolution foomatic-db-gutenprint python2.4-gnome2-desktop gdebi libuniconf4.2 libgutenprint2 libgnomebt0 ttf-gentium gcj-4.1-base xserver-xorg-driver-sisusb app-install-data tango-icon-theme libsexy2 thunderbird-locale-en-gb libnetcdf3 libbrlapi1 libavahi-glib1 libsigc++-2.0-0c2a example-content ijsgutenprint libgstreamer-plugins-base0.10-0 gstreamer0.10-alsa gettext libparted1.6-13 libpoppler1 libcurl3-gnutls libavahi-client3 mcpp libpoppler1-glib foo2zjs scim libdrm2 gnome-screensaver
2006-06-14 21:54:01,695 DEBUG Upgrade: gtk2-engines-lighthouseblue esound-common xset libpng12-0 libjpeg62 parted libbonobo2-common libtext-wrapi18n-perl acpi-support python2.4-reportlab bittorrent libsasl2 xfonts-75dpi xfd apache2-doc gtk2-engines-clearlooks libxt-java libflac7 language-pack-gnome-en python-launchpad-integration libapr0 xserver-xorg-driver-sis dictionaries-common tsclient xwud libaspell15 appres xload libgnomeprintui2.2-0 xwd python-pexpect gnome-desktop-data libcurl3 less python-simpletal libsdl1.2debian-oss python2.4-clientcookie python-xml libxft2 xserver-xorg-driver-via python2.4-imaging libcupsimage2 wvdial python-sqlite libusb-0.1-4 mysql-server xserver-xorg-driver-i128 libacl1 libpam0g python2.4-minimal xdpyinfo xserver-xorg-driver-newport libgimp2.0 libqthreads-12 ttf-arphic-bkai00mp python2.4-dbus xgc console-tools python-kjbuckets libedit2 libbz2-1.0 gnome-media python-egenix-mxproxy openssl libklibc libc6 ntpdate python-unit librdf0 python2.4-pexpect iputils-ping ubuntu-docs libxp6 libstartup-notification0 libsane gnupg ttf-mgopen xfsprogs x11perf libfreetype6 libhsqldb-java python-pgsql bsh libguile-ltdl-1 libvte-common console-common cupsys-driver-gimpprint libgeoip1 gnome-system-monitor mysql-common linux-restricted-modules-common libwrap0 apache2-common iptables python-glade2 gnome-games-data dc ttf-indic-fonts powermanagement-interface e2fslibs python-apt dselect launchpad-integration python2.4-libxslt1 apache2-utils libidn11 sessreg python2.4-libxml2 installation-report libapache2-mod-php5 hwdata finger libgnome-keyring0 gnome-terminal libattr1 discover1 login zlib1g-dev xkeyboard-config ijsgimpprint diff libxdamage1 netbase libpq4 memtest86+ libgamin0 reiser4progs ttf-oriya-fonts libfontenc1 libgucharmap4 python2.4-glade2 xserver-xorg-driver-i740 python2.4-cairo libxkbfile1 rdesktop python-adns zlib1g pmount gnome-utils xvidtune linux-sound-base python2.4-xml module-init-tools gzip python2.4-tk gnome-doc-utils libgnome2-0 usplash libdbi-perl language-selector hotkey-setup libmyspell3c2 python2.4-librdf foomatic-filters python2.4-pycurl foomatic-db-gimp-print linux-image-386 vim libidl0 makedepend python2.4-pyxattr xserver-xorg-driver-tga totem-gstreamer xserver-xorg-driver-vga liblpint-bonobo0 python-gnome2-extras sysklogd openssh-client libsnmp-base evolution-webcal libgnome2-canvas-perl libmagic1 libaa1 libcomerr2 evolution-data-server xfonts-base foomatic-db-hpijs listres ppp libgtksourceview1.0-0 gtk2-engines-redmond95 linux-restricted-modules-386 libxpm4 tcpdump gij xeyes libjessie-java python2.4-unit libpanel-applet2-0 gcc-4.0-base python-gnome2 libxxf86dga1 libxinerama1 libgnomevfs2-common gimp-python libgtk2-perl ttf-freefont debconf-i18n libqt3-mt libxss1 ifupdown mailx fortunes-min python2.4-htmltmpl hpijs libxres1 ttf-tamil-fonts ssh-askpass-gnome ttf-malayalam-fonts wbritish ico librsvg2-2 libdbd-mysql-perl libscrollkeeper0 libldap2 libdb4.3 libdb4.2 base-passwd libgcc1 gtk2-engines-pixbuf python-egenix-mxtexttools libfribidi0 xlsatoms gnome-about gtkhtml3.8 bogofilter-common gnome-control-center update-manager fstobdf alsa-base libpam-runtime xfonts-scalable fastjar dbus-1-utils contact-lookup-applet xserver-xorg-driver-chips libpango1.0-common xbase-clients python2.4-egenix-mxproxy libsmbclient sysv-rc perl libgnomecanvas2-0 bug-buddy libkrb53 librasqal0 libtasn1-2 gs-common gcc-3.3-base libltdl3 gs-esp logrotate libopencdk8 base-files linux-386 python2.4-pam libgda2-common libpisync0 gconf2 gnome-btdownload python2.4-pyorbit libpango1.0-0 gaim-data libwmf0.2-7 bicyclerepair libgcj-common grepmap libsndfile1 python2.4-eunuchs gnome-icon-theme dmsetup bluez-pin libxtrap6 libfontconfig1 cupsys-bsd libxerces2-java libglu1-mesa evms-ncurses beforelight libconsole libxrandr2 ubuntu-standard libpcre3 linux-kernel-headers xmodmap gnome-applets-data python2.4-gdbm python-reportlab laptop-detect xtrap libgtk2.0-bin python-parted libnss3 xclock language-pack-en-base ttf-arabeyes libportaudio0 xstdcmap xserver-xorg-driver-ati xprop ftp liborbit2 libvte4 hicolor-icon-theme python2.4-imaging-sane libgnome-menu2 dash libaudiofile0 python2.4-gtk2 hplip-data system-tools-backends x-ttcidfont-conf libgtkspell0 evolution-plugins libxrender1 iproute python-ldap libnautilus-extension1 libdjvulibre15 python2.4-sqlite ethtool libvorbis0a gnome-panel-data cpio xfonts-utils libncurses5 util-linux xman python2.4-gd libisccc0 xmag python-examples lvm-common xserver-xorg-driver-trident python-pyxattr language-support-en libgnomeui-common libgnomeprint2.2-data libxklavier10 python2.4-jabber bsdmainutils xscreensaver-gl smbclient ssl-cert ttf-opensymbol screen nvidia-kernel-common libbind9-0 gnome-pilot xserver-xorg-driver-tseng libxt6 xserver-xorg-driver-cyrix python-htmltmpl libpt-plugins-v4l2 liblockfile1 gnome-keyring libreadline5 mount libxslt1.1 procps libslp1 powernowd libice6 zenity rhythmbox initramfs-tools whois hostname libstdc++5 libstdc++6 ttf-punjabi-fonts cupsys-client libebook1.2-5 toshset manpages libxmu6 python2.4-pylibacl libcairo2 libpt-plugins-alsa vsftpd gdb libxxf86misc1 gdm librsvg2-common libbonobo2-0 apache2 lsb-release gnome-session libgtk2.0-0 ucf libgnome2-vfs-perl libservlet2.3-java xserver-xorg-driver-tdfx smproxy gettext-base udev xsetmode xserver-xorg-driver-cirrus rsync libselinux1 libsqlite3-0 libgnomeprintui2.2-common libgphoto2-port0 libgnujaxp-jni libgconf2-4 libxtst6 hplip-ppds python2.4-pgsql libedata-book1.2-2 hal python-syck libxi6 notification-daemon debianutils gedit-common apache2-mpm-prefork libeel2-data at samba-common liblircclient0 xresprobe perl-modules xserver-xorg-driver-siliconmotion python-eunuchs libogg0 libxaw7 libgnujaxp-java usbutils e2fsprogs vnc-common perl-base cpp java-common xgamma hwdb-client xserver-xorg ttf-bengali-fonts python2.4-egenix-mxtexttools ttf-gujarati-fonts foomatic-filters-ppds makedev libgtkhtml3.8-15 xfonts-100dpi totem libunicode-string-perl libgda2-3 xserver-xorg-driver-s3 libslang2 python-imaging-sane x-window-system-core dosfstools libtiff4 nano klogd fping dnsutils capplets-data gnome-menus libgnome2-common fortune-mod libxmuu1 aptitude xrdb libgl1-mesa gnome-spell update-notifier python-gd xdriinfo xsane dhcp3-common libglade2-0 libcroco3 wamerican xmessage bluez-pcmcia-support nautilus python-xdg libtext-iconv-perl librecode0 xauth libpt-plugins-v4l xfontsel mkisofs language-pack-gnome-en-base pppconfig libiw28 postfix python-crypto python-egenix-mxstack lsb-base xserver-xorg-driver-rendition python2.4-ldap readahead java-gcj-compat evolution-exchange python-gdbm libdb3 libgail-common xbiff libgtksourceview-common discover1-data libreiserfs0.3-0 libxalan2-java python-imaging xkbutils ubuntu-minimal irssi-text iceauth bash rss-glx xserver-xorg-driver-s3virge lvm2 gnome-applets libraw1394-5 python-geoip xutils guile-1.6-libs xserver-xorg-input-wacom bitmap net-tools binutils-static dpkg gamin grep lshw-common xserver-xorg-driver-mga python2.4-examples reportbug firefox-gnome-support gedit tk8.4 powermgmt-base wireless-tools passwd libc6-dev python2.4-apt desktop-file-utils libgnomeui-0 python2.4-pyopenssl libblkid1 libvorbisfile3 libuuid1 bogofilter-bdb python-pyorbit imake fontconfig libshout3 libedataserverui1.2-6 python2.4-gnome2-extras libadns1 libgnomeprint2.2-0 xserver-xorg-input-elographics libavc1394-0 gnome-pilot-conduits xev xmore vino libnspr4 python-htmlgen sed xserver-xorg-driver-v4l libgnome-desktop-2 libaudio2 viewres python-pyopenssl libeel2-2 mime-support libraptor1 liboil0.3 foomatic-db-engine libpcap0.8 lsof xlsclients xserver-xorg-driver-neomagic fdutils ttf-devanagari-fonts libwnck18 libxau6 metacity eject pciutils libmetacity0 xpmutils bluez-cups gimp python2.4-numeric coreutils xrefresh popularity-contest serpentine python2.4-kjbuckets vbetool gtk2-engines-industrial xwininfo ubuntu-desktop libijs-0.35 xterm python2.4-epydoc iputils-tracepath bind9-host python-jabber pkg-config lftp xhost xvncviewer xserver-xorg-driver-nsc libvorbisenc2 libss2 bc xkill gnome-panel wget dhcp3-client xsm python2.4-mysqldb tcpd libgnome-pilot2 gnome-volume-manager xlsfonts grub libspeex1 ttf-kannada-fonts file-roller libelfg0 info xserver-xorg-driver-nv gthumb libglib2.0-0 libncursesw5 xsane-common libtheora0 python2.4-adns python-epydoc iputils-arping libecal1.2-3 xinit xserver-xorg-driver-glint cpp-4.0 python2.4-htmlgen python2.4-syck libfs6 python-gmenu console-data gnome-cups-manager libisccfg1 gnome-netstatus-applet gtk2-engines-thinice gnome2-user-guide oclock xlogo unzip xditview libxml2-utils python2.4-id3lib editres python-id3lib python2.4-egenix-mxtools libxcursor1 findutils fetchmail cron libc6-i686 evms python2.4-egenix-mxstack gtk2-engines-smooth xserver-xorg-input-kbd foomatic-db python2.4 bogofilter xsltproc python-minimal libao2 nautilus-data scrollkeeper libdv4 libtext-charwidth-perl firefox libxext6 apt gcalctool libbonoboui2-common libdvdread3 libwnck-common xserver-xorg-input-mouse sudo libbonoboui2-0 python-uno libgsl0 gnome-nettool ttf-telugu-fonts python2.4-simpletal dmidecode python-gadfly alsa-utils tar gnome-themes libasound2 xcalc libgphoto2-2 hal-device-manager libgtk2.0-common python-vte netcat klibc-utils libsqlite0 python2.4-egenix-mxdatetime liblzo1 acpid libbluetooth1 libgnomevfs2-0 xsetpointer xsetroot xserver-xorg-driver-ark gimp-data libxfixes3 python-pam gtk2-engines-crux synaptic aspell dbus libgd2-noxpm libgcrypt11 libperl5.8 libgail17 ncurses-bin pcmcia-cs adduser slocate libglib2.0-data w3m mawk lshw libgpg-error0 freeglut3 python-mysqldb odbcinst1debian1 gtk2-engines-mist groff-base hdparm bsdutils ubuntu-artwork ncurses-base xscreensaver-data sound-juicer apt-utils nautilus-sendto libsdl1.2debian mdadm python-clientcookie libsasl2-modules xserver-xorg-driver-vmware xrandr libartsc0 python-gtk2 libgnomecups1.0-1 libxxf86vm1 bluez-utils python2.4-crypto libevms-2.5 sysvinit libglib-perl xrgb nautilus-cd-burner libmdbtools evolution xserver-xorg-driver-dummy debconf libdiscover1 initscripts mozilla-firefox-locale-en-gb libesd-alsa0 xserver-xorg-driver-i810 cdrecord python-pisock libxdmcp6 python-cddb python2.4-gadfly libhal1 esound xclipboard locales xserver-xorg-driver-vesa doc-debian file libxml2 myspell-en-us python xf86dga xserver-xorg-driver-savage libmpcdec3 libedata-cal1.2-1 php5-common python-egenix-mxtools myspell-en-gb vim-common evince gnome-system-tools xserver-xorg-driver-apm libpam-modules gconf-editor libcupsys2-gnutls10 libhal-storage1 python-netcdf gucharmap tcl8.4 libgnucrypto-java xcursorgen xserver-xorg-driver-fbdev shared-mime-info psmisc language-pack-en dvd+rw-tools xserver-xorg-core libsoup2.2-8 gnome-games python2.4-geoip libgnomecanvas2-common python-soappy libxv1 libgpmg1 xserver-xorg-driver-imstt python-tk libgc1c2 xvinfo libgtkhtml2-0 python-pylibacl gnome-terminal-data libgl1-mesa-dri gksu python2.4-gnome2 gaim cupsys yelp liblaunchpad-integration0 libatk1.0-0 gnome-app-install libsm6 libpisock8 bzip2 python-numeric php5 libx11-6 mysql-client telnet xconsole eog
2006-06-14 21:54:06,147 DEBUG required download: 579484516.0 
2006-06-14 21:54:06,149 DEBUG free on /var/cache/apt/archives/: 6686388224 
2006-06-14 21:54:07,662 DEBUG need additional space: 490225664.0
2006-06-14 21:54:09,205 DEBUG /usr on same fs as /var/cache/apt/archives/, taking dl-size into account, new free: 6106903708.0
2006-06-14 21:54:09,207 DEBUG using safety buffer: 78643200
2006-06-14 22:39:45,770 DEBUG got a conffile-prompt from dpkg for file: '/etc/login.defs'
2006-06-15 00:11:54,404 WARNING no activity on terminal for 240 seconds (Preparing to configure login)
2006-06-15 00:24:32,888 WARNING no activity on terminal for 240 seconds (Preparing to configure libpanel-applet2-0)
2006-06-15 01:27:04,473 WARNING no activity on terminal for 240 seconds (Preparing to configure guile-1.6-libs)
2006-06-15 01:58:19,444 WARNING no activity on terminal for 240 seconds (Configuring scrollkeeper)
2006-06-15 02:59:15,272 DEBUG got a conffile-prompt from dpkg for file: '/etc/vsftpd.conf'
2006-06-15 10:14:36,944 WARNING no activity on terminal for 240 seconds (Installed ttf-arphic-bkai00mp)
2006-06-15 10:52:50,797 DEBUG Obsolete: gstreamer0.8-vorbis xserver-xorg-input-penmount xserver-xorg-input-mutouch libgd1-noxpm python2.4-musicbrainz libparted1.6-12 libdevmapper1.01 libgstreamer-gconf0.8-0 xserver-xorg-input-digitaledge libpoppler0c2-glib gstreamer0.8-dv python-musicbrainz libssl0.9.7 gstreamer0.8-x gstreamer0.8-theora libtotem-plparser0 libdb1-compat gstreamer0.8-misc libwvstreams4.0c2-extras xserver-xorg-input-hyperpen opera xserver-xorg-input-dynapro libsigc++-1.2-5c2 liblwres1 gstreamer0.8-musepack libmusicbrainz2c2 libisc9 gstreamer0.8-alsa libmysqlclient12 xserver-xorg-input-void libmysqlclient14 gstreamer0.8-sdl gstreamer0.8-flac libmysqlclient12-dev libopenal0 xserver-xorg-input-fpit xserver-xorg-input-aiptek libgdchart-gd1-noxpm libdns20 libexchange-storage1.2-0 xserver-xorg-input-dmc python-gst libsmpeg0c2 xserver-xorg-input-magellan gstreamer0.8-cdparanoia laptop-mode xserver-xorg-input-summa libgsf-1 gstreamer0.8-gnomevfs python-osd linux-image-2.6.12-10-386 libgnutls11 gstreamer0.8-dvd linux-image-2.6.12-9-386 xlibs gstreamer0.8-hermes libedataserver1.2-4 xserver-xorg-input-acecad xserver-xorg-input-citron xserver-xorg-input-palmax python2.4-osd hermes1 python-gdchart libwvstreams4.0c2-base xserver-xorg-input-spaceorb libpoppler0c2 sane-utils libgstreamer0.8-0 libxplc0.3.11c2 xserver-xorg-input-microtouch gstreamer0.8-jpeg xserver-xorg-input-tek4957 xserver-xorg-input-calcomp linux-restricted-modules-2.6.12-9-386 libgstreamer-plugins0.8-0 libneon24 gstreamer0.8-oss libgtop2-5 libsysfs1 libkpathsea3 linux-restricted-modules-2.6.12-10-386 libglide2 libdrm1 gstreamer0.8-speex libmagick6 gstreamer0.8-tools libsnmp5 gstreamer0.8-gsm gstreamer0.8-esd libgimpprint1 libegroupwise1.2-8 libxosd2 gstreamer0.8-audiofile xserver-xorg-driver-glide gstreamer0.8-plugin-apps
2006-06-15 10:52:51,045 DEBUG Foreign: 
2006-06-15 10:52:51,067 DEBUG forced_obsoletes: []
2006-06-15 10:52:51,225 DEBUG demoted: 'gstreamer0.8-theora libmysqlclient12-dev gstreamer0.8-alsa xserver-xorg-input-calcomp gstreamer0.8-oss gstreamer0.8-tools python-osd libdb1-compat gstreamer0.8-hermes xserver-xorg-input-citron hermes1 xserver-xorg-input-palmax gstreamer0.8-plugin-apps libopenal0 xserver-xorg-input-spaceorb xserver-xorg-input-void libmysqlclient12 python-gst gstreamer0.8-x gstreamer0.8-vorbis xserver-xorg-input-acecad libgstreamer-plugins0.8-0 libneon24 xserver-xorg-input-summa gstreamer0.8-gnomevfs gstreamer0.8-dvd gstreamer0.8-musepack gstreamer0.8-dv python2.4-osd gstreamer0.8-misc xserver-xorg-input-hyperpen gstreamer0.8-sdl xserver-xorg-input-tek4957 gstreamer0.8-esd xserver-xorg-input-penmount gstreamer0.8-gsm xserver-xorg-input-magellan libgstreamer0.8-0 libssl0.9.7 xserver-xorg-input-mutouch libgnutls11 libmysqlclient14 xserver-xorg-input-dynapro gstreamer0.8-flac python-gdchart libgd1-noxpm libgdchart-gd1-noxpm gstreamer0.8-jpeg xserver-xorg-input-microtouch sane-utils xserver-xorg-input-fpit libgstreamer-gconf0.8-0 xserver-xorg-input-dmc laptop-mode libkpathsea3 gstreamer0.8-audiofile xserver-xorg-input-digitaledge libxosd2 libsigc++-1.2-5c2 xserver-xorg-input-aiptek gstreamer0.8-cdparanoia libglide2 gstreamer0.8-speex'
2006-06-15 11:12:18,825 DEBUG remove_candidates: 'set(['gstreamer0.8-vorbis', 'xserver-xorg-input-penmount', 'xserver-xorg-input-mutouch', 'libgd1-noxpm', 'python2.4-musicbrainz', 'libparted1.6-12', 'libdevmapper1.01', 'libgnutls11', 'xserver-xorg-input-digitaledge', 'libpoppler0c2-glib', 'gstreamer0.8-dv', 'python-musicbrainz', 'libssl0.9.7', 'gstreamer0.8-x', 'gstreamer0.8-theora', 'libtotem-plparser0', 'libdb1-compat', 'gstreamer0.8-misc', 'libmysqlclient12-dev', 'xserver-xorg-input-hyperpen', 'xserver-xorg-input-dynapro', 'xserver-xorg-input-aiptek', 'liblwres1', 'gstreamer0.8-musepack', 'libmusicbrainz2c2', 'libisc9', 'linux-image-2.6.12-10-386', 'libmysqlclient12', 'xserver-xorg-input-void', 'libmysqlclient14', 'gstreamer0.8-hermes', 'gstreamer0.8-flac', 'libopenal0', 'xserver-xorg-input-fpit', 'libsigc++-1.2-5c2', 'libgdchart-gd1-noxpm', 'libdns20', 'libexchange-storage1.2-0', 'xserver-xorg-input-dmc', 'python-gst', 'libsmpeg0c2', 'libgimpprint1', 'xserver-xorg-input-magellan', 'gstreamer0.8-cdparanoia', 'laptop-mode', 'libsysfs1', 'libgsf-1', 'gstreamer0.8-gnomevfs', 'python-osd', 'gstreamer0.8-alsa', 'libgstreamer-gconf0.8-0', 'gstreamer0.8-dvd', 'linux-image-2.6.12-9-386', 'xlibs', 'gstreamer0.8-sdl', 'libedataserver1.2-4', 'xserver-xorg-input-acecad', 'xserver-xorg-input-citron', 'xserver-xorg-input-palmax', 'python2.4-osd', 'hermes1', 'python-gdchart', 'libwvstreams4.0c2-base', 'xserver-xorg-input-spaceorb', 'libglide2', 'sane-utils', 'libgstreamer0.8-0', 'libxplc0.3.11c2', 'xserver-xorg-input-microtouch', 'gstreamer0.8-jpeg', 'xserver-xorg-input-tek4957', 'xserver-xorg-input-calcomp', 'linux-restricted-modules-2.6.12-9-386', 'libgstreamer-plugins0.8-0', 'libneon24', 'gstreamer0.8-oss', 'libgtop2-5', 'xserver-xorg-input-summa', 'libkpathsea3', 'linux-restricted-modules-2.6.12-10-386', 'libpoppler0c2', 'libdrm1', 'gstreamer0.8-speex', 'libmagick6', 'gstreamer0.8-tools', 'libsnmp5', 'gstreamer0.8-gsm', 'gstreamer0.8-esd', 'libwvstreams4.0c2-extras', 'libegroupwise1.2-8', 'libxosd2', 'gstreamer0.8-audiofile', 'xserver-xorg-driver-glide', 'gstreamer0.8-plugin-apps'])'
2006-06-15 11:12:18,847 DEBUG Start checking for obsolete pkgs
2006-06-15 11:12:35,729 DEBUG 'linux-image-2.6.12-10-386' scheduled for remove but not in remove_candiates, skipping
2006-06-15 11:12:51,292 DEBUG 'linux-image-2.6.12-9-386' scheduled for remove but not in remove_candiates, skipping
2006-06-15 11:12:51,953 ERROR not handled expection:
Traceback (most recent call last):

  File "/tmp/tmp4tO9W9/dapper", line 28, in ?
    app.run()

  File "/tmp/tmp4tO9W9/DistUpgradeControler.py", line 513, in run
    self.dapperUpgrade()

  File "/tmp/tmp4tO9W9/DistUpgradeControler.py", line 503, in dapperUpgrade
    self.doPostUpgrade()

  File "/tmp/tmp4tO9W9/DistUpgradeControler.py", line 409, in doPostUpgrade
    if not self.cache._tryMarkObsoleteForRemoval(pkgname, remove_candidates, self.foreign_pkgs):

  File "/tmp/tmp4tO9W9/DistUpgradeCache.py", line 277, in _tryMarkObsoleteForRemoval
    self[pkgname].markDelete()

  File "/usr/lib/python2.4/site-packages/apt/package.py", line 288, in markDelete
    if autoFix and self._depcache.BrokenCount > 0:

SystemError: E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

---

### Post by knapper on 2006-06-15
dist-upgrade-apt.log:

Starting
Starting 2
Investigating x11-common
Package x11-common has broken dep on xfree86-common
  Considering xorg-common 1 as a solution to x11-common 1745
  Added xorg-common to the remove list
Package x11-common has broken dep on xorg-common
  Considering xorg-common 1 as a solution to x11-common 1745
  Added xorg-common to the remove list
Package x11-common has broken dep on xserver-common
  Considering xserver-common 0 as a solution to x11-common 1745
  Added xserver-common to the remove list
Package x11-common has broken dep on x-common
  Considering x-common 0 as a solution to x11-common 1745
  Added x-common to the remove list
  Fixing x11-common via remove of xorg-common
  Fixing x11-common via remove of xorg-common
  Fixing x11-common via remove of xserver-common
  Fixing x11-common via remove of x-common
Investigating locales
Package locales has broken dep on base-config
  Considering base-config 4 as a solution to locales 914
  Added base-config to the remove list
  Fixing locales via remove of base-config
Investigating openoffice.org-l10n-en-us
Package openoffice.org-l10n-en-us has broken dep on myspell-dictionary-en-us
Investigating openoffice.org-core
Package openoffice.org-core has broken dep on openoffice.org2-l10n-1.9.129
  Considering openoffice.org2-l10n-en-us 19 as a solution to openoffice.org-core 39
  Added openoffice.org2-l10n-en-us to the remove list
Package openoffice.org-core has broken dep on openoffice.org-help-1.9.129
  Considering openoffice.org2-help-en-us 13 as a solution to openoffice.org-core 39
  Added openoffice.org2-help-en-us to the remove list
Package openoffice.org-core has broken dep on openoffice.org2-core
  Considering openoffice.org2-core 10 as a solution to openoffice.org-core 39
  Added openoffice.org2-core to the remove list
  Fixing openoffice.org-core via remove of openoffice.org2-l10n-en-us
  Fixing openoffice.org-core via remove of openoffice.org2-help-en-us
  Fixing openoffice.org-core via remove of openoffice.org2-core
Investigating openoffice.org-common
Package openoffice.org-common has broken dep on openoffice.org-l10n-en-us
  Considering openoffice.org-l10n-en-us 50 as a solution to openoffice.org-common 28
  Holding Back openoffice.org-common rather than change openoffice.org-l10n-en-us
Investigating readline-common
Package readline-common has broken dep on libreadline4
  Considering libreadline4 2 as a solution to readline-common 27
  Added libreadline4 to the remove list
  Fixing readline-common via remove of libreadline4
Investigating udev
Package udev has broken dep on hotplug
  Considering hotplug 2 as a solution to udev 26
  Added hotplug to the remove list
Package udev has broken dep on ifrename
  Considering ifrename -1 as a solution to udev 26
  Added ifrename to the remove list
  Fixing udev via remove of hotplug
  Fixing udev via remove of ifrename
Investigating imake
Package imake has broken dep on xmkmf
  Considering xmkmf 12 as a solution to imake 25
  Added xmkmf to the remove list
  Fixing imake via remove of xmkmf
Investigating libcamel1.2-8
Package libcamel1.2-8 has broken dep on libcamel1.2-6
  Considering libcamel1.2-6 0 as a solution to libcamel1.2-8 24
  Added libcamel1.2-6 to the remove list
  Fixing libcamel1.2-8 via remove of libcamel1.2-6
Investigating language-support-en
Package language-support-en has broken dep on openoffice.org-l10n-en-us
  Considering openoffice.org-l10n-en-us 50 as a solution to language-support-en 23
Package language-support-en has broken dep on openoffice.org2-l10n-en-us
  Considering openoffice.org2-l10n-en-us 19 as a solution to language-support-en 23
  Added openoffice.org2-l10n-en-us to the remove list
  Fixing language-support-en via keep of openoffice.org2-l10n-en-us
Investigating libnotify1
Package libnotify1 has broken dep on libnotify0
  Considering libnotify0 0 as a solution to libnotify1 16
  Added libnotify0 to the remove list
  Fixing libnotify1 via remove of libnotify0
Investigating busybox-initramfs
Package busybox-initramfs has broken dep on busybox-cvs-initramfs
  Considering busybox-cvs-initramfs 0 as a solution to busybox-initramfs 14
  Added busybox-cvs-initramfs to the remove list
  Fixing busybox-initramfs via remove of busybox-cvs-initramfs
Investigating libsigc++-2.0-0c2a
Package libsigc++-2.0-0c2a has broken dep on libsigc++-2.0-0c2
  Considering libsigc++-2.0-0c2 3 as a solution to libsigc++-2.0-0c2a 13
  Added libsigc++-2.0-0c2 to the remove list
  Fixing libsigc++-2.0-0c2a via remove of libsigc++-2.0-0c2
Investigating dbus
Package dbus has broken dep on libdbus-1-1
  Considering libdbus-1-1 4 as a solution to dbus 12
  Added libdbus-1-1 to the remove list
  Fixing dbus via remove of libdbus-1-1
Investigating libgksuui1.0-1
Package libgksuui1.0-1 has broken dep on libgksuui1.0-0
  Considering libgksuui1.0-0 0 as a solution to libgksuui1.0-1 11
  Added libgksuui1.0-0 to the remove list
  Fixing libgksuui1.0-1 via remove of libgksuui1.0-0
Investigating libpt-1.10.0
Package libpt-1.10.0 has broken dep on libpt-1.8.3c2
  Considering libpt-1.8.3c2 3 as a solution to libpt-1.10.0 11
  Added libpt-1.8.3c2 to the remove list
  Fixing libpt-1.10.0 via remove of libpt-1.8.3c2
Investigating libgksu1.2-1
Package libgksu1.2-1 has broken dep on libgksu1.2-0
  Considering libgksu1.2-0 0 as a solution to libgksu1.2-1 7
  Added libgksu1.2-0 to the remove list
  Fixing libgksu1.2-1 via remove of libgksu1.2-0
Investigating openoffice.org-java-common
Package openoffice.org-java-common has broken dep on openoffice.org-common
  Considering openoffice.org-common 28 as a solution to openoffice.org-java-common 7
  Holding Back openoffice.org-java-common rather than change openoffice.org-common
Investigating openoffice.org-draw
Package openoffice.org-draw has broken dep on openoffice.org-debian-files
  Considering openoffice.org-debian-files 4 as a solution to openoffice.org-draw 4
  Holding Back openoffice.org-draw rather than change openoffice.org-debian-files
Investigating openoffice.org2-common
Package openoffice.org2-common has broken dep on openoffice.org2-core
  Considering openoffice.org2-core 10 as a solution to openoffice.org2-common 4
  Removing openoffice.org2-common rather than change openoffice.org2-core
Investigating openoffice.org-base
Package openoffice.org-base has broken dep on openoffice.org-java-common
  Considering openoffice.org-java-common 7 as a solution to openoffice.org-base 4
  Holding Back openoffice.org-base rather than change openoffice.org-java-common
Investigating libmusicbrainz4c2a
Package libmusicbrainz4c2a has broken dep on libmusicbrainz4c2
  Considering libmusicbrainz4c2 0 as a solution to libmusicbrainz4c2a 3
  Added libmusicbrainz4c2 to the remove list
  Fixing libmusicbrainz4c2a via remove of libmusicbrainz4c2
Investigating openoffice.org-writer
Package openoffice.org-writer has broken dep on openoffice.org-debian-files
  Considering openoffice.org-debian-files 4 as a solution to openoffice.org-writer 2
  Holding Back openoffice.org-writer rather than change openoffice.org-debian-files
Investigating openoffice.org-impress
Package openoffice.org-impress has broken dep on openoffice.org-draw
  Considering openoffice.org-draw 4 as a solution to openoffice.org-impress 2
  Holding Back openoffice.org-impress rather than change openoffice.org-draw
Investigating libgcj6
Package libgcj6 has broken dep on gcc-4.0-base
  Considering gcc-4.0-base 203 as a solution to libgcj6 2
  Removing libgcj6 rather than change gcc-4.0-base
Investigating openoffice.org-math
Package openoffice.org-math has broken dep on openoffice.org-debian-files
  Considering openoffice.org-debian-files 4 as a solution to openoffice.org-math 2
  Holding Back openoffice.org-math rather than change openoffice.org-debian-files
Investigating openoffice.org-calc
Package openoffice.org-calc has broken dep on openoffice.org-debian-files
  Considering openoffice.org-debian-files 4 as a solution to openoffice.org-calc 2
  Holding Back openoffice.org-calc rather than change openoffice.org-debian-files
Investigating libgnomecupsui1.0-1c2a
Package libgnomecupsui1.0-1c2a has broken dep on libgnomecupsui1.0-1
  Considering libgnomecupsui1.0-1 0 as a solution to libgnomecupsui1.0-1c2a 1
  Added libgnomecupsui1.0-1 to the remove list
  Fixing libgnomecupsui1.0-1c2a via remove of libgnomecupsui1.0-1
Investigating libwpd8c2a
Package libwpd8c2a has broken dep on libwpd8c2
  Considering libwpd8c2 0 as a solution to libwpd8c2a 1
  Added libwpd8c2 to the remove list
  Fixing libwpd8c2a via remove of libwpd8c2
Investigating libdbus-glib-1-1
Package libdbus-glib-1-1 has broken dep on libdbus-1-1
  Considering libdbus-1-1 4 as a solution to libdbus-glib-1-1 1
  Removing libdbus-glib-1-1 rather than change libdbus-1-1
Investigating libopenh323-1.15.3c2
Package libopenh323-1.15.3c2 has broken dep on libpt-1.8.3c2
  Considering libpt-1.8.3c2 3 as a solution to libopenh323-1.15.3c2 1
  Removing libopenh323-1.15.3c2 rather than change libpt-1.8.3c2
Investigating libglibmm-2.4-1c2a
Package libglibmm-2.4-1c2a has broken dep on libglibmm-2.4-1c2
  Considering libglibmm-2.4-1c2 1 as a solution to libglibmm-2.4-1c2a 1
  Holding Back libglibmm-2.4-1c2a rather than change libglibmm-2.4-1c2
Investigating openoffice.org-evolution
Package openoffice.org-evolution has broken dep on openoffice.org-base
  Considering openoffice.org-base 4 as a solution to openoffice.org-evolution 1
  Holding Back openoffice.org-evolution rather than change openoffice.org-base
Investigating openoffice.org
Package openoffice.org has broken dep on openoffice.org-writer
  Considering openoffice.org-writer 2 as a solution to openoffice.org 1
  Holding Back openoffice.org rather than change openoffice.org-writer
Investigating libglibmm-2.4-1c2
Package libglibmm-2.4-1c2 has broken dep on libsigc++-2.0-0c2
  Considering libsigc++-2.0-0c2 3 as a solution to libglibmm-2.4-1c2 1
  Removing libglibmm-2.4-1c2 rather than change libsigc++-2.0-0c2
Investigating libid3-3.8.3c2a
Package libid3-3.8.3c2a has broken dep on libid3-3.8.3c2
  Considering libid3-3.8.3c2 0 as a solution to libid3-3.8.3c2a 1
  Added libid3-3.8.3c2 to the remove list
  Fixing libid3-3.8.3c2a via remove of libid3-3.8.3c2
Investigating libnetcdf3
Package libnetcdf3 has broken dep on netcdfg3
  Considering netcdfg3 0 as a solution to libnetcdf3 1
  Added netcdfg3 to the remove list
  Fixing libnetcdf3 via remove of netcdfg3
Investigating openoffice.org2-math
Package openoffice.org2-math has broken dep on openoffice.org-math
  Considering openoffice.org-math 2 as a solution to openoffice.org2-math 0
  Removing openoffice.org2-math rather than change openoffice.org-math
Investigating xorg-driver-synaptics
Package xorg-driver-synaptics has broken dep on xfree86-driver-synaptics
  Considering xserver-xorg-input-synaptics 0 as a solution to xorg-driver-synaptics 0
  Removing xorg-driver-synaptics rather than change xfree86-driver-synaptics
Investigating gparted
Package gparted has broken dep on libglibmm-2.4-1c2a
  Considering libglibmm-2.4-1c2a 1 as a solution to gparted 0
  Removing gparted rather than change libglibmm-2.4-1c2a
Investigating openoffice.org2-impress
Package openoffice.org2-impress has broken dep on openoffice.org-impress
  Considering openoffice.org-impress 2 as a solution to openoffice.org2-impress 0
  Removing openoffice.org2-impress rather than change openoffice.org-impress
Investigating alacarte
Package alacarte has broken dep on smeg
  Considering smeg 0 as a solution to alacarte 0
  Holding Back alacarte rather than change smeg
Investigating openoffice.org2
Package openoffice.org2 has broken dep on openoffice.org
  Considering openoffice.org 1 as a solution to openoffice.org2 0
  Removing openoffice.org2 rather than change openoffice.org
Investigating cupsys-driver-gimpprint-data
Package cupsys-driver-gimpprint-data has broken dep on cupsys-driver-gimpprint
  Considering cupsys-driver-gimpprint 1 as a solution to cupsys-driver-gimpprint-data 0
  Removing cupsys-driver-gimpprint-data rather than change cupsys-driver-gimpprint
Investigating hplip
Package hplip has broken dep on gtklp
Investigating ubuntu-desktop
Package ubuntu-desktop has broken dep on alacarte
  Considering alacarte 0 as a solution to ubuntu-desktop 0
  Removing ubuntu-desktop rather than change alacarte
Investigating openoffice.org2-writer
Package openoffice.org2-writer has broken dep on openoffice.org-writer
  Considering openoffice.org-writer 2 as a solution to openoffice.org2-writer 0
  Removing openoffice.org2-writer rather than change openoffice.org-writer
Investigating openoffice.org2-base
Package openoffice.org2-base has broken dep on openoffice.org-base
  Considering openoffice.org-base 4 as a solution to openoffice.org2-base 0
  Removing openoffice.org2-base rather than change openoffice.org-base
Investigating openoffice.org2-calc
Package openoffice.org2-calc has broken dep on openoffice.org-calc
  Considering openoffice.org-calc 2 as a solution to openoffice.org2-calc 0
  Removing openoffice.org2-calc rather than change openoffice.org-calc
Investigating gij-4.0
Package gij-4.0 has broken dep on gcc-4.0-base
  Considering gcc-4.0-base 203 as a solution to gij-4.0 0
  Removing gij-4.0 rather than change gcc-4.0-base
Investigating libgcj6-common
Package libgcj6-common has broken dep on libgcj6
  Considering libgcj6 2 as a solution to libgcj6-common 0
  Removing libgcj6-common rather than change libgcj6
Investigating openoffice.org2-evolution
Package openoffice.org2-evolution has broken dep on openoffice.org-evolution
  Considering openoffice.org-evolution 1 as a solution to openoffice.org2-evolution 0
  Removing openoffice.org2-evolution rather than change openoffice.org-evolution
Investigating libgtkmm-2.4-1c2
Package libgtkmm-2.4-1c2 has broken dep on libglibmm-2.4-1c2
  Considering libglibmm-2.4-1c2 1 as a solution to libgtkmm-2.4-1c2 0
  Removing libgtkmm-2.4-1c2 rather than change libglibmm-2.4-1c2
Investigating libgtkmm-2.4-1c2a
Package libgtkmm-2.4-1c2a has broken dep on libglibmm-2.4-1c2a
  Considering libglibmm-2.4-1c2a 1 as a solution to libgtkmm-2.4-1c2a 0
  Holding Back libgtkmm-2.4-1c2a rather than change libglibmm-2.4-1c2a
Investigating openoffice.org2-draw
Package openoffice.org2-draw has broken dep on openoffice.org-draw
  Considering openoffice.org-draw 4 as a solution to openoffice.org2-draw 0
  Removing openoffice.org2-draw rather than change openoffice.org-draw
Investigating hplip-base
Package hplip-base has broken dep on hplip-data
  Considering hplip-data 3 as a solution to hplip-base 0
  Removing hplip-base rather than change hplip-data
Investigating libnautilus-burn2
Package libnautilus-burn2 has broken dep on libdbus-1-1
  Considering libdbus-1-1 4 as a solution to libnautilus-burn2 0
  Removing libnautilus-burn2 rather than change libdbus-1-1
Investigating gnomemeeting
Package gnomemeeting has broken dep on libopenh323-1.15.3c2
  Considering libopenh323-1.15.3c2 1 as a solution to gnomemeeting 0
  Removing gnomemeeting rather than change libopenh323-1.15.3c2
Investigating openoffice.org-core
Package openoffice.org-core has broken dep on openoffice.org-common
  Considering openoffice.org-common 28 as a solution to openoffice.org-core 39
  Holding Back openoffice.org-core rather than change openoffice.org-common
 Try to Re-Instate language-support-en
Re-Instated language-support-en (4 vs 3)
Investigating python-uno
Package python-uno has broken dep on openoffice.org-core
  Considering openoffice.org-core 39 as a solution to python-uno 2
  Removing python-uno rather than change openoffice.org-core
Investigating openoffice.org-gnome
Package openoffice.org-gnome has broken dep on openoffice.org-core
  Considering openoffice.org-core 39 as a solution to openoffice.org-gnome 1
  Holding Back openoffice.org-gnome rather than change openoffice.org-core
Investigating openoffice.org-gtk
Package openoffice.org-gtk has broken dep on openoffice.org-core
  Considering openoffice.org-core 39 as a solution to openoffice.org-gtk 1
  Holding Back openoffice.org-gtk rather than change openoffice.org-core
Investigating openoffice.org2-gnome
Package openoffice.org2-gnome has broken dep on openoffice.org-gnome
  Considering openoffice.org-gnome 1 as a solution to openoffice.org2-gnome 0
  Removing openoffice.org2-gnome rather than change openoffice.org-gnome
Done
Starting
Starting 2
Investigating xchat-common
Package xchat-common has broken dep on xchat
  Considering xchat 10001 as a solution to xchat-common 0
Package xchat-common has broken dep on xchat-text
  Or group remove for xchat-common
Done
Starting
Starting 2
Investigating libgdchart-gd1-noxpm
Package libgdchart-gd1-noxpm has broken dep on libgd1-noxpm
  Considering libgd1-noxpm 10002 as a solution to libgdchart-gd1-noxpm 1
Package libgdchart-gd1-noxpm has broken dep on libgd1-xpm
  Or group remove for libgdchart-gd1-noxpm
Investigating python-gdchart
Package python-gdchart has broken dep on libgd1-noxpm
  Considering libgd1-noxpm 10002 as a solution to python-gdchart 0
Package python-gdchart has broken dep on libgd1-xpm
  Or group remove for python-gdchart
Package python-gdchart has broken dep on libgdchart-gd1-noxpm
  Considering libgdchart-gd1-noxpm 1 as a solution to python-gdchart 0
Package python-gdchart has broken dep on libgdchart-gd1-xpm
  Or group remove for python-gdchart
Done
Starting
Starting 2
Investigating python-musicbrainz
Package python-musicbrainz has broken dep on python2.4-musicbrainz
  Considering python2.4-musicbrainz 10001 as a solution to python-musicbrainz 0
  Removing python-musicbrainz rather than change python2.4-musicbrainz
Done
Starting
Starting 2
Investigating libexchange-storage1.2-0
Package libexchange-storage1.2-0 has broken dep on libgnutls11
  Considering libgnutls11 10002 as a solution to libexchange-storage1.2-0 0
  Removing libexchange-storage1.2-0 rather than change libgnutls11
Investigating libegroupwise1.2-8
Package libegroupwise1.2-8 has broken dep on libgnutls11
  Considering libgnutls11 10002 as a solution to libegroupwise1.2-8 0
  Removing libegroupwise1.2-8 rather than change libgnutls11
Done
Starting
Starting 2
Investigating libdns20
Package libdns20 has broken dep on libssl0.9.7
  Considering libssl0.9.7 10004 as a solution to libdns20 2
  Removing libdns20 rather than change libssl0.9.7
Investigating libneon24
Package libneon24 has broken dep on libssl0.9.7
  Considering libssl0.9.7 10004 as a solution to libneon24 0
  Removing libneon24 rather than change libssl0.9.7
Investigating libwvstreams4.0c2-extras
Package libwvstreams4.0c2-extras has broken dep on libssl0.9.7
  Considering libssl0.9.7 10004 as a solution to libwvstreams4.0c2-extras 0
  Removing libwvstreams4.0c2-extras rather than change libssl0.9.7
Investigating libsnmp5
Package libsnmp5 has broken dep on libssl0.9.7
  Considering libssl0.9.7 10004 as a solution to libsnmp5 0
  Removing libsnmp5 rather than change libssl0.9.7
Done
Starting
Starting 2
Investigating linux-restricted-modules-2.6.12-10-386
Package linux-restricted-modules-2.6.12-10-386 has broken dep on linux-image-2.6.12-10-386
  Considering linux-image-2.6.12-10-386 10001 as a solution to linux-restricted-modules-2.6.12-10-386 0
  Removing linux-restricted-modules-2.6.12-10-386 rather than change linux-image-2.6.12-10-386
Done
Starting
Starting 2
Investigating python2.4-musicbrainz
Package python2.4-musicbrainz has broken dep on libmusicbrainz2c2
  Considering libmusicbrainz2c2 10001 as a solution to python2.4-musicbrainz 1
  Removing python2.4-musicbrainz rather than change libmusicbrainz2c2
Investigating python-musicbrainz
Package python-musicbrainz has broken dep on python2.4-musicbrainz
  Considering python2.4-musicbrainz 1 as a solution to python-musicbrainz 0
  Removing python-musicbrainz rather than change python2.4-musicbrainz
Done
Starting
Starting 2
Investigating libwvstreams4.0c2-extras
Package libwvstreams4.0c2-extras has broken dep on libssl0.9.7
  Considering libssl0.9.7 10001 as a solution to libwvstreams4.0c2-extras 0
  Removing libwvstreams4.0c2-extras rather than change libssl0.9.7
Done
Starting
Starting 2
Investigating libgdchart-gd1-noxpm
Package libgdchart-gd1-noxpm has broken dep on libgd1-noxpm
  Considering libgd1-noxpm 10001 as a solution to libgdchart-gd1-noxpm 0
Package libgdchart-gd1-noxpm has broken dep on libgd1-xpm
  Or group remove for libgdchart-gd1-noxpm
Done
Starting
Starting 2
Investigating linux-restricted-modules-2.6.12-9-386
Package linux-restricted-modules-2.6.12-9-386 has broken dep on linux-image-2.6.12-9-386
  Considering linux-image-2.6.12-9-386 10001 as a solution to linux-restricted-modules-2.6.12-9-386 0
  Removing linux-restricted-modules-2.6.12-9-386 rather than change linux-image-2.6.12-9-386
Done
Starting
Starting 2
Investigating python2.4-musicbrainz
Package python2.4-musicbrainz has broken dep on libmusicbrainz2c2
  Considering libmusicbrainz2c2 10001 as a solution to python2.4-musicbrainz 1
  Removing python2.4-musicbrainz rather than change libmusicbrainz2c2
Investigating python-musicbrainz
Package python-musicbrainz has broken dep on python2.4-musicbrainz
  Considering python2.4-musicbrainz 1 as a solution to python-musicbrainz 0
  Removing python-musicbrainz rather than change python2.4-musicbrainz
Done
Starting
Starting 2
Investigating libwvstreams4.0c2-extras
Package libwvstreams4.0c2-extras has broken dep on libssl0.9.7
  Considering libssl0.9.7 10001 as a solution to libwvstreams4.0c2-extras 0
  Removing libwvstreams4.0c2-extras rather than change libssl0.9.7
Done
Starting
Starting 2
Investigating libgdchart-gd1-noxpm
Package libgdchart-gd1-noxpm has broken dep on libgd1-noxpm
  Considering libgd1-noxpm 10001 as a solution to libgdchart-gd1-noxpm 0
Package libgdchart-gd1-noxpm has broken dep on libgd1-xpm
  Or group remove for libgdchart-gd1-noxpm
Done
Starting
Starting 2
Investigating opera
Package opera has broken dep on xlib6g
Package opera has broken dep on xlibs
  Considering xlibs 10002 as a solution to opera 0
  Or group remove for opera
Package opera has broken dep on lesstif2
Investigating opera
Package opera has broken dep on xlib6g
Package opera has broken dep on xlibs
  Considering xlibs 10002 as a solution to opera 0
  Or group remove for opera
Package opera has broken dep on lesstif2
Investigating opera
Package opera has broken dep on xlib6g
Package opera has broken dep on xlibs
  Considering xlibs 10002 as a solution to opera 0
  Or group remove for opera
Package opera has broken dep on lesstif2
Investigating opera
Package opera has broken dep on xlib6g
Package opera has broken dep on xlibs
  Considering xlibs 10002 as a solution to opera 0
  Or group remove for opera
Package opera has broken dep on lesstif2
Investigating opera
Package opera has broken dep on xlib6g
Package opera has broken dep on xlibs
  Considering xlibs 10002 as a solution to opera 0
  Or group remove for opera
Package opera has broken dep on lesstif2
Investigating opera
Package opera has broken dep on xlib6g
Package opera has broken dep on xlibs
  Considering xlibs 10002 as a solution to opera 0
  Or group remove for opera
Package opera has broken dep on lesstif2
Investigating opera
Package opera has broken dep on xlib6g
Package opera has broken dep on xlibs
  Considering xlibs 10002 as a solution to opera 0
  Or group remove for opera
Package opera has broken dep on lesstif2
Investigating opera
Package opera has broken dep on xlib6g
Package opera has broken dep on xlibs
  Considering xlibs 10002 as a solution to opera 0
  Or group remove for opera
Package opera has broken dep on lesstif2
Investigating opera
Package opera has broken dep on xlib6g
Package opera has broken dep on xlibs
  Considering xlibs 10002 as a solution to opera 0
  Or group remove for opera
Package opera has broken dep on lesstif2
Investigating opera
Package opera has broken dep on xlib6g
Package opera has broken dep on xlibs
  Considering xlibs 10002 as a solution to opera 0
  Or group remove for opera
Package opera has broken dep on lesstif2
Done

---

### Post by starpause on 2006-07-06
same experience here: was doing an upgrade from 5.10 to 6.06 LTS and hit the "A fatal error occured" dialog with instructions to report a bug, but no instructions on where to report the bug to :roll: 

```
Traceback (most recent call last):

  File "/tmp/tmpDl6ZDd/dapper", line 28, in ?
    app.run()

  File "/tmp/tmpDl6ZDd/DistUpgradeControler.py", line 513, in run
    self.dapperUpgrade()

  File "/tmp/tmpDl6ZDd/DistUpgradeControler.py", line 503, in dapperUpgrade
    self.doPostUpgrade()

  File "/tmp/tmpDl6ZDd/DistUpgradeControler.py", line 409, in doPostUpgrade
    if not self.cache._tryMarkObsoleteForRemoval(pkgname, remove_candidates, self.foreign_pkgs):

  File "/tmp/tmpDl6ZDd/DistUpgradeCache.py", line 277, in _tryMarkObsoleteForRemoval
    self[pkgname].markDelete()

  File "/usr/lib/python2.4/site-packages/apt/package.py", line 288, in markDelete
    if autoFix and self._depcache.BrokenCount > 0:

SystemError: E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```

and the two files i was told to include with my report:

[http://mp3death.us/hor/dist-upgrade-apt.log](http://mp3death.us/hor/dist-upgrade-apt.log)
[http://mp3death.us/hor/dist-upgrade.log](http://mp3death.us/hor/dist-upgrade.log)

if anyone has next steps to suggest OR knows where to properly report this error, i am all ears :KS

---

