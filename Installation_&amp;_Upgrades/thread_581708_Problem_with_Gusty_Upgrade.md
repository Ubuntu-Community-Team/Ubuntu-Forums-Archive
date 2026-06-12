---
title: "Problem with Gusty Upgrade"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by Austin17 on 2007-10-19
Hi, I'm new to Ubuntu, and fairly new to Linux as a whole. I have two computers that were each running 7.04, one is an older computer that I use as a spair/server computer and the other is a newer one that is the one I normally use. I have a lot of the same software running on both of the computers, so I thought I would try the 7.04 to 7.10 upgrade on the computer I don't care as much about to test it out. It took most of the day to download the files, and I didn't have any problem there; but about 3/4 through the installation it gave me some error's about programs it had trouble updating, and one of them was the update manager. After I got the error message about the update manager, the whole update quit out. At that point I just rebooted and after I got back in I noticed things looked different like they should in Gusty. Grub even said I had 7.10, but I'm still not sure what happened, and at this point I'm too paranoid to try the update on my main computer. I did do all the updates before I installed Gusty, so I'm not sure what could be the problem, or what I can do to fix it. Thanks.

---

### Post by quark_77 on 2007-10-19
I'll give you a quick run-down of the upgrade process as I understand it.

The script basically changes your sources (/etc/apt/sources.list) from feisty to gutsy and then works out what needs changing i.e. what is new in the package list, what replaces what and then goes ahead and does it.

If you crashed and burned during the install, you will have everything installed up to that point. Try booting the system. If you can get to the gui you may be able to continue the update with the remaining packages using the update manager (usually appears top right). If you can't, post back to us and we'll see what we can do.

A few questions for when you come back to help anyone trying to help you:
[LIST]
[*]Which package caused the install to break? If it also breaks again on the partial upgrade, which package is causing all the headache?
[*]How far can you load the system normally i.e. is the desktop OK?
[/LIST]

Finally, I'd advise leaving your second PC well alone if it is configured similarly until you understand where the problems are. I'm just trying to rescue my own setup!

Note: I'm a great fan of downloading the alternative CD for updates...

I hope this helps, please post back with whatever results you get and someone will have the answer.

Quark_77

---

### Post by Austin17 on 2007-10-19
Thanks for the reply. I can boot to the system and the GUI seems to work. I tried checking for updates and it only came up with this one small update so I installed it and checked again, but nothing else appeared. I am actually on the system now typing this, so a lot of stuff works. The only thing I remember was that it said something about the update manager system not being able to update and then it gave me some message saying my system was probably in an unstable state. Here is one of the weird things that I've noticed: While I still have the new Appearance tab with all the new settings in it, I still have the old Desktop Effects button in my System-->Preferences list. This tells me that my system does not seem to have cleaned out all the stuff for the upgrade, so I'm also wondering how much more might still be out there. Is there a place where I can get some log of the upgrade so that I can see if I can point out some specific package?

---

### Post by Tris2006 on 2007-10-19
You dont happen to know what packages were having problems? The names of them I mean. 

Well it sounds like everything else was updated, but the removal process was not able to complete. I am not sure if there is a way to resume it, but you may have to remove the old packages one by one... Thats gota be a pain. Some one correct me if im wrong.

Oh, and Hi Austin! :KS

---

### Post by Austin17 on 2007-10-19
I can't remember the exact packages, but if there were a log I might be able to find it. Is a log taken for the upgrade, and if so where can I find it?

Hi Tris! :KS

---

### Post by Austin17 on 2007-10-19
Sorry for the double post, but I think I got my log. Here is is from /var/log/dist-upgrade/main.log



```
2007-10-18 09:28:41,284 INFO release-upgrader version '0.81' started
2007-10-18 09:28:51,881 DEBUG lsb-release: 'feisty'
2007-10-18 09:28:51,883 DEBUG _pythonSymlinkCheck run
2007-10-18 09:29:02,643 DEBUG checkViewDepends()
2007-10-18 09:29:16,088 DEBUG Foreign: automatix2 wine
2007-10-18 09:29:16,090 DEBUG Obsolete: gaim-xfire python-coherence libpigment0 python-lirc libdecoration0 python-louie elisa
2007-10-18 09:29:16,095 DEBUG updateSourcesList()
2007-10-18 09:29:16,511 DEBUG rewriteSourcesList()
2007-10-18 09:29:16,541 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted'
2007-10-18 09:29:16,542 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted' updated to new dist
2007-10-18 09:29:16,544 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted'
2007-10-18 09:29:16,545 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted' updated to new dist
2007-10-18 09:29:16,546 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted'
2007-10-18 09:29:16,548 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted' updated to new dist
2007-10-18 09:29:16,549 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted'
2007-10-18 09:29:16,550 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted' updated to new dist
2007-10-18 09:29:16,551 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ feisty universe'
2007-10-18 09:29:16,553 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe' updated to new dist
2007-10-18 09:29:16,554 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe'
2007-10-18 09:29:16,555 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe' updated to new dist
2007-10-18 09:29:16,557 DEBUG examining: 'deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse'
2007-10-18 09:29:16,558 DEBUG entry 'deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse' updated to new dist
2007-10-18 09:29:16,559 DEBUG examining: 'deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse'
2007-10-18 09:29:16,561 DEBUG entry 'deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse' updated to new dist
2007-10-18 09:29:16,562 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu feisty-security main restricted'
2007-10-18 09:29:16,564 DEBUG entry 'deb http://security.ubuntu.com/ubuntu gutsy-security main restricted' updated to new dist
2007-10-18 09:29:16,565 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted'
2007-10-18 09:29:16,566 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted' updated to new dist
2007-10-18 09:29:16,567 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu feisty-security universe'
2007-10-18 09:29:16,569 DEBUG entry 'deb http://security.ubuntu.com/ubuntu gutsy-security universe' updated to new dist
2007-10-18 09:29:16,570 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu feisty-security universe'
2007-10-18 09:29:16,571 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu gutsy-security universe' updated to new dist
2007-10-18 09:29:16,573 DEBUG examining: 'deb http://security.ubuntu.com/ubuntu feisty-security multiverse'
2007-10-18 09:29:16,574 DEBUG entry 'deb http://security.ubuntu.com/ubuntu gutsy-security multiverse' updated to new dist
2007-10-18 09:29:16,575 DEBUG examining: 'deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse'
2007-10-18 09:29:16,577 DEBUG entry 'deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse' updated to new dist
2007-10-18 09:29:16,578 DEBUG examining: 'deb http://www.getautomatix.com/apt feisty main'
2007-10-18 09:29:16,588 DEBUG entry '# deb http://www.getautomatix.com/apt feisty main' was disabled (unknown mirror)
2007-10-18 09:29:16,590 DEBUG transitioned commerical to 'deb http://archive.canonical.com/ubuntu gutsy partner' 
2007-10-18 09:29:16,591 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse'
2007-10-18 09:29:16,593 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse' updated to new dist
2007-10-18 09:29:16,594 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse'
2007-10-18 09:29:16,595 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu gutsy-updates universe multiverse' updated to new dist
2007-10-18 09:29:16,597 DEBUG examining: 'deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse'
2007-10-18 09:29:16,598 DEBUG entry 'deb http://archive.ubuntu.com/ubuntu gutsy-security main restricted universe multiverse' updated to new dist
2007-10-18 09:29:16,599 DEBUG examining: 'deb http://wine.budgetdedicated.com/apt feisty main #WineHQ - Ubuntu 7.04 "Feisty Fawn"'
2007-10-18 09:29:16,609 DEBUG entry '# deb http://wine.budgetdedicated.com/apt feisty main #WineHQ - Ubuntu 7.04 "Feisty Fawn"' was disabled (unknown mirror)
2007-10-18 09:29:16,611 DEBUG examining: 'deb-src http://wine.budgetdedicated.com/apt feisty main #WineHQ - Ubuntu 7.04 "Feisty Fawn"'
2007-10-18 09:29:16,621 DEBUG entry '# deb-src http://wine.budgetdedicated.com/apt feisty main #WineHQ - Ubuntu 7.04 "Feisty Fawn"' was disabled (unknown mirror)
2007-10-18 09:32:42,423 DEBUG demoted: 'binfmt-support emacs21 emacs21-bin-common emacs21-common feisty-session-splashes gcj-4.1-base gij-4.1 gnome-cups-manager libgda2-3 libgda2-common libglib1.2 libgnomecupsui1.0-1c2a libgtk1.2 libgtk1.2-common liblzo1 libportaudio0 libslab0 libstlport5.1 openoffice.org-filter-mobiledev ttf-baekmuk vnc-common xvncviewer'
2007-10-18 09:34:11,245 DEBUG Removing 'xscreensaver' (ubuntu-desktop PostUpgradeRemove rule)
2007-10-18 09:34:11,627 DEBUG Removing 'gnome-cups-manager' (ubuntu-desktop PostUpgradeRemove rule)
2007-10-18 09:34:12,017 DEBUG Purging 'xorg-common' (Distro PostUpgradePurge rule)
2007-10-18 09:34:12,018 DEBUG Purging 'libgl1-mesa' (Distro PostUpgradePurge rule)
2007-10-18 09:34:12,019 DEBUG Purging 'ltsp-client' (Distro PostUpgradePurge rule)
2007-10-18 09:34:12,398 DEBUG Purging 'ltspfsd' (Distro PostUpgradePurge rule)
2007-10-18 09:34:12,774 DEBUG Purging 'python2.3' (Distro PostUpgradePurge rule)
2007-10-18 09:34:12,776 DEBUG running gutsyQuirks handler
2007-10-18 09:34:12,778 DEBUG found nfs mount in line 'nfsd /proc/fs/nfsd nfsd rw 0 0', marking nfs-common for install 
2007-10-18 09:34:13,153 DEBUG Kernel uname: '2.6.20-16-generic' 
2007-10-18 09:34:13,997 DEBUG Marking 'ubuntu-desktop' for upgrade
2007-10-18 09:34:18,342 DEBUG About to apply the following changes
2007-10-18 09:34:19,252 DEBUG Held-back: 
2007-10-18 09:34:19,254 DEBUG Remove: compiz-gtk libglew1 libopal-2.2.0 gnome-cups-manager libwnck18 libgnome-speech3 dbus-1-utils libuniconf4.2 human-cursors-theme libnss3 gaim-dev
2007-10-18 09:34:19,255 DEBUG Install: bluez-gnome splix fast-user-switch-applet libtotem-plparser7 libpigment0.3-1 libgnome-vfs2.0-cil libdevmapper1.02.1 libavutil1d libgcj7-1 libx264-54 libtrackerclient0 o3read libavformat1d libcompizconfig-backend-gconf liblwres30 linux-restricted-modules-2.6.22-14-generic libgtksourceview2.0-common libwnck22 libjasper1 python-sexy ttf-dejavu-extra libdb4.5 xdg-user-dirs libgda3-common libglew1.4 gcc-4.2-base pidgin-data libwpg-0.1-1 restricted-manager-core libnss3-0d libpurple0 discover1 librpc-xml-perl xresprobe discover1-data gij-4.2 linux-image-2.6.22-14-generic libwvstreams4.3-extras libmeanwhile1 linux-headers-2.6.22-14 gutsy-wallpapers pidgin libatm1 libalut0 xserver-xorg-video-amd bogofilter libiw29 libgs8 ttf-indic-fonts-core ubufox librsvg2.0-cil libsnmp10 libneon26 libebml0 update-notifier-common tracker libjack0 pxljr libisc32 python-pigment libdeskbar-tracker guidance-backends linux-headers-2.6.22-14-generic libwvstreams4.3-base python-pygtksourceview libisccfg30 xvnc4viewer ntfs-3g libpam-gnome-keyring libkeyutils1 libgtkhtml3.8-15 bogofilter-bdb fuse-utils apturl libgtkhtml2.0-cil libgnome-speech7 libopenspc0 libltdl3 system-config-printer libffi4 libpostproc1d libcompizconfig0 libopenal0a libgpod2 liblzo2-2 libsvg1 compiz-fusion-plugins-extra libavahi-compat-libdnssd1 libservlet2.4-java python-cups libmtp6 tracker-search-tool libmatroska0 libzephyr3 xdg-utils libgsl0 libpaper-utils libpcrecpp0 libterm-readkey-perl xdg-user-dirs-gtk libgcj8-1 xserver-xorg-video-psb gcj-4.2-base ttf-unfonts-core tcpd librarian0 libart2.0-cil compiz-fusion-plugins-main libuniconf4.3 displayconfig-gtk xserver-xorg-video-intel libtracker-gtk0 consolekit apparmor libgda3-3 libntfs-3g12 linux-ubuntu-modules-2.6.22-14-generic libnspr4-0d libopal-2.2 libdiscover1 bogofilter-common libdns32 libisccc30 libgdl-gnome-1-0 ttf-dejavu-core libpoppler2 ghostscript libavcodec1d libfuse2 hal-cups-utils cups-pdf libpoppler-glib2 apparmor-utils libflac8 libgtksourceview2.0-0 libhesiod0 libbind9-30 ghostscript-x dmz-cursor-theme
2007-10-18 09:34:19,262 DEBUG Upgrade: libbz2-1.0 libsane python-twisted-web gnome-terminal hal esound-common wvdial python2.5-minimal libapm1 xserver-xorg-video-rendition base-files libsdl-ttf2.0-0 smartdimmer libglu1-mesa xserver-xorg-video-vesa net-tools libgtk2.0-bin libcupsimage2 listres xserver-xorg-video-sis gnome-applets-data gparted grub udev libmono-system1.0-cil dhcdbd python-launchpad-bugs libevent1 volumeid xauth devhelp readahead util-linux-locales gnome-applets libegroupwise1.2-13 libc6-dev libuuid1 libgksu2-0 wpasupplicant libungif4g libmono-system-web2.0-cil libmono-system2.0-cil libxtrap6 libss2 libgnomecanvas2-0 xsane-common totem powermanagement-interface info gstreamer0.10-plugins-bad python-gtk2 libbrlapi1 cvs openoffice.org-evolution libkpathsea4 libsasl2-2 gtk2-engines login compiz-plugins dvd+rw-tools libgmime2.2-cil libgcrypt11 libatk1.0-0 bzip2 libglib2.0-cil libwrap0 cdparanoia hplip-data xclock mysql-server xdpyinfo gnome-media libdbi-perl launchpad-integration apache2-utils restricted-manager libxres1 libnotify1 upstart-logd librecode0 brltty libthai-data docbook-xml hwdb-client-gnome libguile-ltdl-1 libxrender1 xaw3dg libice6 libicu36 libsqlite3-0 python-vte liblircclient0 xserver-xorg tzdata openoffice.org-base ssh-askpass-gnome libgnome2-common libxplc0.3.13 libgnome2-0 libnm-util0 python-gnomecanvas libwnck-common apport-gtk libgphoto2-2 netcat libexpat1 bluez-utils kommander xf86dga xsm gnome-games openssh-server python-gtkhtml2 libgucharmap6 scim-modules-socket libusb-0.1-4 python2.4-minimal wodim libpam-foreground mplayer-doc gstreamer0.10-gnomevfs vncserver gnome-system-monitor linux-restricted-modules-common e2fslibs libdevhelp-1-0 gnome-terminal-data xserver-xorg-video-siliconmotion human-theme gnome-doc-utils language-selector ifupdown hpijs ttf-tamil-fonts libscrollkeeper0 libdb4.3 libdb4.2 libdb4.4 python-setuptools xmodmap upstart-compat-sysv libncurses5 procps python-central librsvg2-common gettext-base gnome-panel-data notification-daemon perl-modules python-gdbm cupsys-client gstreamer0.10-plugins-good passwd fontconfig libmetacity0 coreutils libgsf-1-114 ca-certificates iputils-tracepath xhost gnome-volume-manager gconf2-common libxml2-utils elisa libgcj-bc xserver-xorg-video-apm dselect libxi6 nautilus-sendto libldap2 libglib-perl bsdmainutils libebook1.2-9 locales gstreamer0.10-alsa libpam-modules mplayer-skins libgpmg1 gnome-screensaver libjpeg62 openoffice.org-writer language-pack-gnome-en foomatic-filters python-notify libsdl-image1.2 mysql-common python-glade2 finger fceu libaspell15 libbeagle0 libgtksourceview1.0-0 gnome-user-guide evolution-common update-manager smproxy ktron ppp libbluetooth2 cupsys-bsd libxerces2-java libpcre3 dictionaries-common xmore gnome-pilot initramfs-tools iso-codes xrgb apache2-mpm-prefork gettext xgamma xserver-xorg-video-savage python-elementtree xserver-xorg-input-evdev gpgv binutils-static compiz-core mysql-client-5.0 gsfonts liboil0.3 gij-4.1 gnome-netstatus-applet konquest gnome-orca feisty-gdm-themes dhcp3-common libxcursor1 libglade2.0-cil xml-core libxext6 apt libgnomevfs2-extra aspell ubuntu-artwork sysv-rc g++ libgnome-media0 libsigc++-2.0-0c2a libsm6 libexif12 x11-common libx11-data xconsole xwud doc-base whiptail linux-libc-dev netbase kmines librsync1 gnome-games-data ksirtet gnome-utils genisoimage libxml-twig-perl kspaceduel hwdb-client-common atlantik xman xmag libgdiplus libbonobo2-0 libxau6 libgutenprint2 debianutils cpp libmono-cairo1.0-cil libmysqlclient15off libjline-java nfs-common libglib2.0-dev gamin mysql-server-5.0 libgnutls13 libparted1.7-1 sed openoffice.org-thesaurus-en-us libnewt0.52 linux-image-generic unzip gstreamer0.10-esd gcalctool debconf-i18n libbonoboui2-common python libsasl2-modules libavahi-core5 libpng12-0 thunderbird-locale-en-gb libesd-alsa0 python-bittorrent ttf-gujarati-fonts gnome-menus libx11-6 libmono-sqlite2.0-cil mono-common libndesk-dbus-glib1.0-cil acpi-support libxfont1 libqt3-mt python-xml libsmpeg0 cpp-4.1 putty findutils mencoder openoffice.org-l10n-en-gb libdc1394-13 module-init-tools gtk2-engines-pixbuf tcpdump libgcc1 libwxgtk2.6-0 gstreamer0.10-ffmpeg libopencdk8 kasteroids ed libcurl3 libgdl-1-common kfilereplace ubuntu-standard libedata-book1.2-2 apport dosfstools klogd dnsutils libmp4v2-0 python-avahi evolution-exchange libcdaudio1 libraw1394-8 bash gedit python-problem-report libhtml-tree-perl python-gnupginterface xserver-xorg-video-glint liburi-perl freeglut3 libpcap0.8 xkb-data xterm libxml-parser-perl firefox-gnome-support xserver-xorg-input-kbd belocs-locales-bin alsa-utils sudo libasound2 libgstreamer0.10-0 klibc-utils libhal-storage1 acpid libgnome2.0-cil mono-runtime keep gcj-4.1-base mplayer eject libmpcdec3 python-apport libgnomekbdui1 libmdbtools evolution libmono-system-data2.0-cil laptop-detect linux-headers-generic mono-gac libxevie1 xserver-xorg-video-voodoo brltty-x11 usplash-theme-ubuntu libgdl-1-0 klinkstatus libgnomekbd-common appres gnupg xwininfo dash ttf-oriya-fonts libavahi-common-data libglibmm-2.4-1c2a libcucul0 gnome-control-center libsmbclient libtasn1-3 libwpd8c2a vorbis-tools libatspi1.0-0 lsb-release libgnomekbd1 whois ttf-punjabi-fonts toshset libxmu6 libmono-sharpzip2.84-cil cupsys-common ttf-dejavu libdbus-glib-1-2 rss-glx inputattach ttf-devanagari-fonts libid3tag0 gnome-panel libgail-gnome-module cdrdao xsetmode libcamel1.2-10 iputils-arping libtiff4 libssl0.9.8 xditview xfonts-encodings apmd python-minimal liba52-0.7.4 system-services gcc-4.1 ncurses-base sound-juicer tidy linux-sound-base software-properties-gtk debconf at-spi libgnomeprint2.2-0 gnome-system-tools libavahi-client3 xserver-xorg-video-ark libstdc++6-4.1-dev libgtkhtml2-0 python-launchpad-integration xserver-xorg-video-tga libhsqldb-java xserver-xorg-video-newport ttf-indic-fonts filezilla-common hplip libxdamage1 kftpgrabber apt-utils linux-restricted-modules-generic xlsatoms ico ttf-freefont libusplash0 librsvg2-2 command-not-found-data libieee1284-3 libgstreamer-plugins-base0.10-0 gstreamer0.10-x proftpd libnautilus-burn4 gnome-mag libpango1.0-0 libncursesw5 gnome-session python-dbus libarts1c2a libsepol1 avahi-autoipd unattended-upgrades perl-base command-not-found libavahi-common3 libnfsidmap2 libxrandr2 libexchange-storage1.2-3 libwavpack1 update-notifier ttf-malayalam-fonts python-zopeinterface checkinstall libpaper1 alacarte artsbuilder gnome-accessibility-themes openoffice.org-draw viewres libx86-1 xpmutils libcairomm-1.0-1 libmad0 xlogo mktemp libdecoration0 xsetpointer slocate esound myspell-en-gb libdvdread3 libpisock9 php5 scim gnome-cards-data libgtk2.0-cil ubuntu-docs libscim8c2a libfreetype6 memtest86+ xeyes fortunes-min xbase-clients ethtool xvinfo xserver-xorg-video-s3 liborbit2 libnl1-pre6 libxklavier11 screem screen libnautilus-extension1 kolf libselinux1 libgconf2-4 libgtkhtml3.14-19 gedit-common samba-common putty-tools gproftpd ssl-cert libxinerama1 xfontsel libxaw7 openoffice.org-java-common xserver-xorg-input-wacom dpkg ttf-arphic-uming libgnomevfs2-bin python-gnome2-desktop libgnome-desktop-2 binutils build-essential xlsclients libpulse0 console-terminus readline-common libnet-dbus-perl python-cairo kwin4 libdbus-1-3 xcalc libgtk2.0-common alsa-oss libgmime-2.0-2 mesa-utils libcurl3-gnutls libxpm4 libdirectfb-0.9-25 ucf gdebi-core rdiff-backup libdv4 xsltproc gnome-mime-data xgc scim-modules-table myspell-en-za gstreamer0.10-plugins-ugly libidl0 evolution-webcal libmagic1 python-gnome2 mkisofs filezilla gconf2 python-imaging ekiga python-gobject cupsys-driver-gutenprint poppler-utils xserver-xorg-video-via zenity libstlport5.1 libgphoto2-port0 libxtst6 openoffice.org-filter-mobiledev vnc-common mozilla-mplayer nano capplets-data nautilus libxvmc1 xutils guile-1.6-libs libmusicbrainz4c2a libgsf-1-common librpcsecgss3 libcdparanoia0 openoffice.org-calc gnome-themes libsdl1.2debian alsa-base ubuntu-minimal xserver-xorg-video-i128 libavahi-glib1 feisty-wallpapers libsensors3 gksu evolution-data-server-common compiz libbonobo2-common gnome-desktop-data python-twisted-bin libedit2 kbattleship openoffice.org-style-human vlc-nox xserver-xorg-video-nv libgnome-keyring0 libqthreads-12 zlib1g liboobs-1-3 libcomerr2 evolution-data-server foomatic-db-hpijs libjack0.100.0-0 xwd libxss1 espeak-data acpi atlantikdesigner libfontconfig1 libart-2.0-2 libgcj-common util-linux libgconf2.0-cil libmodplug0c2 libsdl-mixer1.2 metacity-common gtkhtml3.14 emacs21-bin-common libgnomevfs2-common file makedev emacs21-common libgssapi2 openoffice.org-math xserver-xorg-video-all python-virtkey pciutils mono-jit ksnake desktop-file-utils libtidy-0.99-0 nfs-kernel-server openoffice.org-impress gthumb libecal1.2-7 vlc libc6-i686 python2.5 python2.4 linux-generic gnome-nettool libgtop2-7 hal-device-manager libxfixes3 libxt6 dbus libgail18 xutils-dev gnome-icon-theme libgnome-window-settings1 myspell-en-us sysvutils liblockfile1 ltrace quanta cupsys mcpp libwxbase2.6-0 python-numeric apache2.2-common compiz-gnome parted python-ctypes xvidtune xserver-xorg-video-ati libwxbase2.8-0 bsh libvte-common f-spot libaa1 python-louie gij libslang2 xserver-xorg-video-nsc xmessage devhelp-common libkdegames1 gs-esp xorg python-gst0.10 ttf-telugu-fonts psmisc openoffice.org-gnome fontconfig-config xload openoffice.org gstreamer0.10-plugins-base-apps x-ttcidfont-conf libvorbis0a xscreensaver-gl pppconfig libcairo-perl gnome-keyring mount rhythmbox liblcms1 samba apache2 libgtk2.0-0 libgnomeprintui2.2-common libreadline5 xlsfonts libxmuu1 xsane language-pack-gnome-en-base console-setup libmono-data-tds2.0-cil libgtop2-common gcc-4.1-base startup-tasks man-db python-libxml2 libgtkmm-2.4-1c2a gucharmap kreversi pkg-config xvncviewer busybox-initramfs libvorbisenc2 xkill tomboy libgnome-pilot2 tangerine-icon-theme mozilla-firefox-locale-en-gb libespeak1 libxkbfile1 scrollkeeper python-uno gnome-mount libmagick9 xrandr libartsc0 vim-tiny gaim nautilus-cd-burner tango-icon-theme initscripts liblaunchpad-integration0 libdrm2 python-pysqlite2 gnome-power-manager bittorrent libapr1 tsclient gstreamer0.10-plugins-base libklibc binfmt-support diff gzip hotkey-setup bind9-host sysklogd openssh-client ksayit update-inetd libgtkspell0 time gimp-python libxcomposite1 gnome-about gstreamer0.10-tools libpam-runtime libpango1.0-common libkrb53 tasksel-data libportaudio0 cli-common file-roller iproute libcvsservice0 libhunspell-1.1-0 libxvidcore4 libstdc++5 libstdc++6 manpages libpt-plugins-alsa gdb gdm libgpg-error0 totem-gstreamer libedataserver1.2-9 e2fsprogs openoffice.org-l10n-common fortune-mod libglade2-0 libpt-plugins-v4l system-tools-backends liblocale-gettext-perl ftp python-twisted-core wireless-tools python-pyorbit human-icon-theme rdesktop libeel2-2 gcompris upstart metacity bluez-cups popularity-contest laptop-mode-tools libedataserverui1.2-8 g++-4.1 wget nautilus-data firefox xserver-xorg-input-mouse app-install-data-commercial libidn11 hdparm libgnome-menu2 libhal1 language-selector-common libxml2 iceauth php5-common vim-common less dmidecode eog gtk2-engines-ubuntulooks python-gconf python-support libavahi-qt3-1 libsdl1.2debian-alsa iputils-ping libmono-corlib1.0-cil iptables onboard libhtml-parser-perl libgnomecanvas2-common openoffice.org-common usplash libgksuui1.0-1 xbitmaps tasksel bug-buddy gcc-3.3-base openoffice.org-gtk gnome-btdownload dmsetup beforelight python-software-properties libsnmp-base libblkid1 bitmap python-celementtree quanta-data libdbd-mysql-perl libthai0 espeak libcap1 xrdb portmap xserver-xorg-input-all libgtksourceview-common libcairo2 libgutenprintui2-1 gs-esp-x xserver-xorg-input-synaptics libgamin0 ttf-kannada-fonts kimagemapeditor gimp gconf-editor libgnome-mag2 gnome-media-common libelfg0 hal-info oclock libbonoboui2-0 gimp-data gdebi lshw kdelibs4c2a kdelibs-data reiserfsprogs shared-mime-info language-pack-en gnome-app-install libwxgtk2.8-0 editres ksmiletris smbfs ttf-opensymbol libmms0 xserver-xorg-video-i810 ncurses-bin network-manager libpq5 libmono2.0-cil libfontenc1 ubuntu-desktop libmono-corlib2.0-cil libgnomeprintui2.2-0 libpisync0 libapache2-mod-php5 xserver-xorg-video-mga python-gnome2-extras mtr-tiny base-passwd update-manager-core avahi-daemon contact-lookup-applet perl gnome-keyring-manager gs-common libwmf0.2-7 libconsole libsysfs2 xstdcmap libgnomeui-common libxslt1.1 emacs21 libswfdec0.3 ttf-arphic-ukai aptitude libgl1-mesa-glx libgail-common xbiff libxalan2-java python-orca-brlapi libfreebob0 libdvdnav4 gnome-pilot-conduits libwps-0.1-1 vino libnss-mdns libaudio2 xserver-xorg-core openoffice.org-core libvlc0 libc6 serpentine dhcp3-client language-pack-en-base liblame0 python-gmenu lftp foomatic-db network-manager-gnome libao2 gcc libgnomevfs2-0 libmono0 synaptic xscreensaver-data libvolume-id0 strace libdvbpsi4 xclipboard evince libxv1 foo2zjs pppoeconf yelp libcupsys2 xfd libnm-glib0 libxft2 libpam0g libgimp2.0 adduser openprinting-ppds console-tools openssl ntpdate bsdutils libperl5.8 python-apt sessreg python-configobj scim-tables-additional openoffice.org-help-en-us liblpint-bonobo0 libpanel-applet2-0 evolution-plugins ubuntu-keyring libenchant1c2a libsndfile1 ttf-arabeyes libvte9 gcompris-data lsb-base libdjvulibre15 cpio ssh libgnomeprint2.2-data smbclient libpt-plugins-v4l2 libgnomeui-0 rsync libeel2-data usbutils ttf-bengali-fonts openoffice.org-l10n-en-za libmono-security2.0-cil libcroco3 ttf-thai-tlwg libglib2.0-0 defoma gimp-print libvorbisfile3 libopenexr2c2a lsof scim-gtk2-immodule libpt-1.10.0 libtag1c2a deskbar-applet libcaca0 libgsm1 tar xserver-xorg-video-tseng python-at-spi libdaemon0 app-install-data cdrecord foomatic-db-engine libedata-cal1.2-6 libsexy2 xsetroot libgl1-mesa-dri libxdmcp6 dpkg-dev
2007-10-18 09:34:19,273 DEBUG Free space on /: 8673021952
2007-10-18 09:34:19,275 DEBUG Dir /usr mounted on /
2007-10-18 09:34:19,278 DEBUG Dir /var mounted on /
2007-10-18 09:34:19,282 DEBUG Dir /boot mounted on /
2007-10-18 09:34:19,285 DEBUG Dir /var/cache/apt/archives mounted on /
2007-10-18 09:34:19,287 DEBUG Dir /home mounted on /
2007-10-18 09:34:19,289 DEBUG fs_free contains: '{'/var': <DistUpgradeControler.FreeSpace object at 0xa73ceac>, '/home': <DistUpgradeControler.FreeSpace object at 0xa73ceac>, '/boot': <DistUpgradeControler.FreeSpace object at 0xa73ceac>, '/usr': <DistUpgradeControler.FreeSpace object at 0xa73ceac>, '/': <DistUpgradeControler.FreeSpace object at 0xa73ceac>, '/var/cache/apt/archives': <DistUpgradeControler.FreeSpace object at 0xa73ceac>}'
2007-10-18 09:34:19,366 DEBUG linux-image-2.6.20-16-generic (upgrade|installed) added with 10485760 to boot space
2007-10-18 09:34:19,559 DEBUG linux-image-2.6.22-14-generic (new-install) added with 10485760 to boot space
2007-10-18 09:34:21,036 DEBUG linux-image-2.6.20-15-generic (upgrade|installed) added with 10485760 to boot space
2007-10-18 09:34:25,595 DEBUG dir '/var/cache/apt/archives' needs '800109454.0' of '<DistUpgradeControler.FreeSpace object at 0xa73ceac>' (8673021952.000000)
2007-10-18 09:34:25,597 DEBUG dir '/usr' needs '482603008.0' of '<DistUpgradeControler.FreeSpace object at 0xa73ceac>' (7872912498.000000)
2007-10-18 09:34:25,599 DEBUG dir '/usr' needs '52428800' of '<DistUpgradeControler.FreeSpace object at 0xa73ceac>' (7390309490.000000)
2007-10-18 09:34:25,600 DEBUG dir '/boot' needs '31457280' of '<DistUpgradeControler.FreeSpace object at 0xa73ceac>' (7337880690.000000)
2007-10-18 09:34:25,602 DEBUG dir '/' needs '10485760' of '<DistUpgradeControler.FreeSpace object at 0xa73ceac>' (7306423410.000000)
2007-10-18 09:35:24,810 INFO using backports in '/tmp/tmpZmlj-O/backports' 
2007-10-18 09:35:24,816 DEBUG have: ['/tmp/tmpZmlj-O/backports/release-upgrader-dpkg_1.14.5ubuntu11.2_i386.udeb', '/tmp/tmpZmlj-O/backports/release-upgrader-apt_0.6.46.4ubuntu10.3_i386.udeb']
2007-10-18 09:35:24,818 DEBUG setting MinAge to 10
2007-10-18 09:35:24,821 DEBUG no file '/etc/apt/apt.conf.d/25adept-archive-limits'
2007-10-18 14:24:20,552 ERROR IOError in cache.commit(): 'Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/libx/libxpm/xpmutils_3.5.6-3_i386.deb Error reading from server - read (104 Connection reset by peer) [IP: 91.189.89.8 80]
'. Retrying (currentTry: 0)
2007-10-18 14:26:28,607 INFO cache.commit()
2007-10-18 14:46:56,254 WARNING no activity on terminal for 240 seconds (Configuring libpam0g)
2007-10-18 15:17:00,727 DEBUG got a conffile-prompt from dpkg for file: '/etc/login.defs'
2007-10-18 15:53:53,305 DEBUG got a conffile-prompt from dpkg for file: '/etc/cups/cupsd.conf'
2007-10-18 16:27:08,247 WARNING no activity on terminal for 240 seconds (Configuring libldap2)
2007-10-18 17:01:50,340 WARNING no activity on terminal for 240 seconds (Configuring scrollkeeper)
2007-10-18 17:31:34,813 ERROR got an error from dpkg for pkg: 'python-pigment': 'subprocess post-installation script returned error exit status 1
'
2007-10-18 17:31:35,103 ERROR got an error from dpkg for pkg: 'python-pigment': 'subprocess post-installation script returned error exit status 1
'
2007-10-18 18:41:21,855 WARNING no activity on terminal for 240 seconds (Configuring python-pigment)
2007-10-18 18:41:22,180 ERROR got an error from dpkg for pkg: 'elisa': 'dependency problems - leaving unconfigured
'
2007-10-18 18:41:22,305 ERROR got an error from dpkg for pkg: 'elisa': 'dependency problems - leaving unconfigured
'
2007-10-18 19:26:40,513 WARNING no activity on terminal for 240 seconds (Installed initramfs-tools)
2007-10-18 21:15:38,318 ERROR SystemError from cache.commit(): installArchives() failed
2007-10-18 21:16:00,031 DEBUG setting MinAge to 2
2007-10-18 21:16:00,033 DEBUG no file '/etc/apt/apt.conf.d/25adept-archive-limits'
```

---

### Post by heldal on 2007-10-19
I think I'm in a similar situation on one PC. The error messages were similar, and the final message was that the system may be in some "undetermined state". 

When rebooting the computer failed to boot the new kernel. It seemed to be missing drivers (at least SATA and RAID-drivers). However, the old kernel hadn't been removed as the cleanup of unused old packages happen at the end of the upgrade process. I was thus able to boot the old 2.6.20-16 kernel in recovery-mode. I suspected that the configuration-part of the install-procedure hadn't been completed for the new kernel and that the init RAMdisk hadn't been built complete with all necessary modules. I re-created the initrd for the 2.6.22-14 kernel with "update-initramfs" and rebooted -- it worked. 

The computer now runs what appear to be a fairly complete system and I've manually (using apt-get) cleaned out the old unused packages that should have been removed at the end of the upgrade. Everything I've checked so far seems to be working. The update process did however indicate that it only was 2/3 completed so something must be missing, or not initialised or configured properly. It's a pity there are no tools to analyse the apt-log and if possible resume the process. Still, the ubuntu-desktop package that maintain all dependencies for a complete desktop install is reported to be installed properly so it may not be so bad after all.

---

### Post by DalaiDakkar on 2007-10-19
sorry, how can I open a new thread????? I can't find a new post button anywhere thank you

---

### Post by csabimeta on 2007-10-20
I started to upgrade kubuntu gusty with the recommended method. After downloading everything (at about 10 hours, with an 1 Mbit/s connection:confused:), started to install. But at a point it posted an error message. I can't remember the output exactly, but that was an issue with ldap. The upgrade tool didn't resume, until 3 hours. So I decided to break the process, and continue tomorrow. When I started up, this uncomplete gusty wasn't able to launch kdm and kde. So I did a dpkg --configure -a. When it finished, still couldn't start kdm.
Tried apt-get --update, --upgrade and --dist-upgrade, but didn't worked. Is it possible to resume the upgrade somehow, without a GUI?
Please help me, I need my kubuntu:(!

---

### Post by Austin17 on 2007-10-20
> **DalaiDakkar said:**
> sorry, how can I open a new thread????? I can't find a new post button anywhere thank you

It's in the top left "Make New Post" is the title of the button. I couldn't find it right away when I wanted to make this post either. lol

Can anyone see what appears to be wrong with my log? Because I can't point out any one thing that might have caused it, but I'm no good at reading the log anyway.

---

### Post by Hoppiesbox on 2007-10-20
This is like the 5th time I'll be doing this but...

My post:
[http://ubuntuforums.org/showthread.php?t=582616](http://ubuntuforums.org/showthread.php?t=582616)

And these peoples:
[http://ubuntuforums.org/showthread.php?p=3579154](http://ubuntuforums.org/showthread.php?p=3579154)
[http://ubuntuforums.org/showthread.php?p=3579236](http://ubuntuforums.org/showthread.php?p=3579236)
[http://ubuntuforums.org/showthread.php?p=3579260](http://ubuntuforums.org/showthread.php?p=3579260)

These might share a similar solution to your problem.

dpkg --configure -a does nothing but return errors.

I'd love to provide some outputs if anyone can suggest what might be useful.
the end of my term.log looks like:

```
gconftool-2: symbol lookup error: /usr/lib/libxml2.so.2: undefined symbol: gzopen64
dpkg: error processing libgnomekbd-common (--configure):
 subprocess post-installation script returned error exit status 127
Setting up bsdmainutils (6.1.6ubuntu1) ...
Setting up util-linux-locales (2.13-8ubuntu1) ...
dpkg: dependency problems prevent configuration of evolution-exchange:
 evolution-exchange depends on libgnomeui-0 (>= 2.19.1); however:
  Package libgnomeui-0 is not configured yet.
dpkg: error processing evolution-exchange (--configure):
 dependency problems - leaving unconfigured
Setting up discover1-data (2.2007.05.11ubuntu4) ...
Setting up dmz-cursor-theme (0.4.1) ...
Setting up libxfce4util4 (4.4.1-1ubuntu1) ...
Setting up screen (4.0.3-0.4ubuntu2) ...
Installing new version of config file /etc/init.d/screen ...
 Removing any system startup links for /etc/init.d/screen-cleanup ...
dpkg: dependency problems prevent configuration of libgdl-gnome-1-0:
 libgdl-gnome-1-0 depends on libgnomeui-0 (>= 2.17.1); however:
dpkg: error processing libgdl-gnome-1-0 (--configure):
dpkg: too many errors, stopping
dpkg: ../../src/packages.c:251: process_queue: Assertion `!queuelen' failed.
```

---

### Post by Lord Landis on 2007-10-20
[QUOTE=Austin17]Can anyone see what appears to be wrong with my log? Because I can't point out any one thing that might have caused it, but I'm no good at reading the log anyway.[/QUOTE]

Look at these lines:

> [SIZE="1"]2007-10-18 17:31:34,813 ERROR got an error from dpkg for pkg: 'python-pigment': 'subprocess post-installation script returned error exit status 1
'
2007-10-18 17:31:35,103 ERROR got an error from dpkg for pkg: 'python-pigment': 'subprocess post-installation script returned error exit status 1
'
2007-10-18 18:41:21,855 WARNING no activity on terminal for 240 seconds (Configuring python-pigment)
2007-10-18 18:41:22,180 ERROR got an error from dpkg for pkg: 'elisa': 'dependency problems - leaving unconfigured
'
2007-10-18 18:41:22,305 ERROR got an error from dpkg for pkg: 'elisa': 'dependency problems - leaving unconfigured
'
2007-10-18 19:26:40,513 WARNING no activity on terminal for 240 seconds (Installed initramfs-tools)
2007-10-18 21:15:38,318 ERROR SystemError from cache.commit(): installArchives() failed[/SIZE]

There is at least one package which is missing dependencies.  These may or may not be what's causing all of your problems.  There are a couple of things you can try from the terminal, though I'm not entirely sure they'll work.  The first is to do
```

sudo apt-get install elisa -f
```

That should force the elisa package to install, along with any dependencies.

Edit your sources by doing the following:
```
sudo nano /etc/apt/sources.list
```
and remove (or comment out) anything that has 'feisty' in it.  Save the file.

Next, use these two commands:
```
sudo apt-get update
sudo apt-get upgrade
```
This will download the headers from the repositories and then update any packages that still haven't been fully updated.

Finally, after all that's done, run this:
```
sudo apt-get autoremove
sudo apt-get clean
```
to purge any leftover packages that are no longer needed and to clean out your arp cache.

---

### Post by Hoppiesbox on 2007-10-20
@Lord Landis:

I've tried autoremove, etc - and just installing a package that is missing...it insists that I can't do anything before dpkg --configure -a which atm doesn't fix anything.

The original posters log shows an exit with status 1 -while my log shows status 127 - any clue where some info can be found on the meaning of these codes?

---

### Post by bturrie on 2007-10-20
I've done several feisty-gutsy upgrades. they were all a little different. my latest one hung up and wouldn't continue until i went into Konsole and ran

sudo apt-get autoclean

that cleared out a bunch of stuff that was not properly installed. I followed that with 

sudo apt-get update
sudo apt-get upgrade

you may need to repeat this pair of instructions several times (i did) , if the upgrade hangs up with a dpkg error try 

sudo dpkg --configure -a

hope this helps

---

### Post by Hoppiesbox on 2007-10-20
But what to do when 'sudo dpkg --configure -a' returns too many errors and stops?

---

### Post by Lord Landis on 2007-10-20
[QUOTE=Hoppiesbox]But what to do when 'sudo dpkg --configure -a' returns too many errors and stops?[/QUOTE]

The best advice I can give on that is to remove the package entirely and then re-install it.
```

sudo dpkg -r *package*
```
If that doesn't work, use the purge option '-P' instead of the remove option '-r'.  After that, you should be able to run the normal 'sudo dpkg -i *package*' command to re-install it.

Unfortunately, I don't know what the error codes themselves mean, and I'm not entirely sure where to start looking (of course, GIYF).

If worse comes to worst, do a clean install to a freshly-squeezed partition and mount your old partition as a device like /media/hdb.  Extract and backup any critical data you need from it, and then just do a completely new install and wipe the whole drive.

I actually had to do this the other night on my 7.04 system after installing a mouse theme broke my desktop.  Yes, it's weird, an X11 mouse theme broke everything.  But in the end it's okay, because I also got to purge around 400 or so Gnome packages that were eating up space on my system (I'm running Kubuntu now).

---

### Post by Austin17 on 2007-10-20
Lord Landis:

Thanks a lot for your help. When I followed the instructions I noticed all of the Feisty stuff was already # out. So I went ahead and did the autoremove and stuff, and it seems to have cleared out a lot. The thing is that I still see some 7.04 stuff like the Desktop Effects thing under System --> Preferences. This tells me that there are probably more stuff out there. Is there anything else I can do? Thanks for all the help so far.

Austin

---

### Post by dsiddens on 2007-10-20
I used the update notification on my Feisty laptop to begin the Gutsy upgrade. After the files were obtained it began replacing to the Gutsy versions. As the files were being written, I noticed quite a few depencencies errors with their messages that a given file (program) would not be installed or might not work properly. This message suggested that I file a bug report. A bit further on into this upgrade process I noticed that there were messages giving me the option to "compare the differences" between the file I had and the new file. So on one of these messages, I don't know which one, I selected "D" and was given a command line screen that described stuff I did not know about and then sat there saying "end".

I figured that hitting enter would return me to the install process. Not so. The machine was sitting at the command prompt waiting for, I don't know what. Eventually I thought if I did a power down/up that the install process would pick up from where it left off. Again, not so. I tried booting from the regular kernal choice and from the recovery mode, neither of which yeilded a working computer.

From the screens that stopped on the boot attempts I wrote down the last screen of each attempt. The significant lines are:

For the kernel 2.6.22-14 (recovery mode)
[10.960197]/build/buildd/linux-source-2.6.22-2.6.22/drivers/ftc/hc.tosys.c: unable to open rtc device(rtc0)
[10.973499] input: AT Translated Set 2 keyboard as /class/input/input1
[11.063970] VFS: Cannot open root device "UUID =adc16267-58e2-4882-9850-9da2e35d482" or unknown-block (0,0)
[11.064022] Please append a correct "root=" boot option; here are the available partitions:
[11.064075] Kernel panic - not sysncing: VFS: Unable to mount root fs on unknown-block (0,0)

For the kernel 2.6.22.14-generic
[16.798468] PCI: Cannot allocate resource region 7 of bridge 0000:00:04.0
[17.014051] Kernal panic-not syncing: VFS: Unable to mount root fs on unknown-block (0,0)

at the bottom of the screen:
Kernel alive
kernel direct mapping tables up to 100000000@8000-d000

I had other boot choices which I went through and tried them all with the result that I was brought to a light blue screen with a cursor that I could move around but no text or sign-in boxes.

The machine in question is a laptop AMD64. It was running fine with the Feisty software.
I'm on our secod laptop hoping that some one can give me a newbie's, detailed instruction to get Gutsy up and running.

Thank you, Doug

---

### Post by Lord Landis on 2007-10-22
**@ Austin17**

No problem!  The things you're seeing in the menus may or may not still be installed.  The best way to check is to pour through Synaptic and see if they're listed as installed.  If they are, you can probably remove them safely (just check to see how many other files it'll yank out with it).  Not knowing the package names can make this a little difficult, but if you search by description, or at least narrow it down to the Gnome-specific section, it should make life a little easier.

If the packages are not installed, you'd need to edit the menus to remove them.  Unfortunately, I'm not quite sure which files you'd need to edit to actually accomplish that. 

**@ dsiddens**

Kernel Panic = very, very, extremely bad.  It's basically the BSoD for Linux.

It sounds like the system is borked and in an un-recoverable state.  The 'D' option you choose probably put you into a debugging mode, though it may have also deleted the file.

As much as it sucks to have to say this, your best bet to get the system up is going to be to download the .iso, burn it to disc, and perform a clean install.

---

### Post by dsiddens on 2007-10-22
quark77,  In my situtation i can only get to the screen that shows the various version of the kernel.  Eventhough I have several to choose from (and I've tried each of them in turn) the result is the same: a soft blue screen with a cursor that I can move but nothing else.
I'm wondering if using this second machine to download and make a disc, then trying  to boot the dead machine  from the disc...  I don't want a repeat of when I upgraded from Dapper to Edgy which was to loose all of the files which had been on the hd.   So if I were to make a bootable disk, what do you Ubuntu wizards think of this idea? 
Thank you, Doug

follow on information:  I was successful in booting from a gutsy cd but the hard drives, hda & hdb, in this laptop still do not show.  The machine appears to be running ok off of the cd.  I'll be looking for how to's to get an identification of the drives as a next step

---

### Post by Lord Landis on 2007-10-22
Here's a solid way to save your data, but you'll have to install twice.

[LIST=1]
[*]On the first install, create a new partition in the unused space for the install, and then mount the existing partition as /media/hdb or something like that.
[*]Boot into the newly-installed system.
[*]Back up your data from /media/hdb to a CD, USB drive, or network drive.
[*]Reboot to the LiveCD again, and perform a clean install that wipes the entire disk.
[*]Boot to the newly-newly-installed system.
[*]Copy the backed-up data to your box.
[*]Profit.
[/LIST]

It's a pain, but it's going to be pretty much the only way you can save that data.  Just booting with the CD isn't necessarily going to allow you to access the data on the hard-drive to save/recover/back it up, as it might not mount the hard-drive.

---

### Post by csabimeta on 2007-10-22
> **csabimeta said:**
> I started to upgrade kubuntu gusty with the recommended method. After downloading everything (at about 10 hours, with an 1 Mbit/s connection:confused:), started to install. But at a point it posted an error message. I can't remember the output exactly, but that was an issue with ldap. The upgrade tool didn't resume, until 3 hours. So I decided to break the process, and continue tomorrow. When I started up, this uncomplete gusty wasn't able to launch kdm and kde. So I did a dpkg --configure -a. When it finished, still couldn't start kdm.
Tried apt-get --update, --upgrade and --dist-upgrade, but didn't worked. Is it possible to resume the upgrade somehow, without a GUI?
Please help me, I need my kubuntu:(!

Finally gusty is running. I've done it with aptitude, installed its recommendations, and reinstalled kernel modules. Everything is fine now, Gusty is Great!!!

---

### Post by eyemou on 2007-10-22
I'm having a similar issue. My Gutsy update hung during the "Install" phase. After it sat on one package, (preparing to configure expat1), with no change in status, I killed it. Stupid, I know.

Anyhow, apt-get update & apt-get upgrade seemed to get things working again, almost. A ton of stuff installed, and it was pretty smooth sailing. However, I seem to be hung up on 1 package (bsdmainutils), and that 1 package is hanging up about 115 more to be upgraded.

I'm not in front of the computer itself, unfortunately (it's at home, I'm at work), but I am unable to install/reinstall or remove the package. I always seem to get error messages along the lines of:

"dpkg error: processing bsdmainutils --configure
 subporcess post-installation script returned an error exit status 2"

and

"update alternatives: internal error: /var/lib/alternatives/write corrupt: manflag"

A couple more notes:

In //var/lib/dpkg/status, the entry for "Package: bsdmainutils" appears to have a status of "deinstall ok half-configured".

As for /var/lib/alternatives/write, it is indeed corrupted... I'm not 100% sure what it's supposed to contain, but it's definitely not correct / complete / may as well be blank (something went buggy at some point, and it appears to contain the output of some other process... This happened to my old /dpkg/status file a while back).

Anyhow, long story short, bsdmainutils looks as if it's going to be removed and replaced with bsdutils. Even if I remove its entry from the 'status' file, it re-appears, flagged for deinstall. Is there a way to just remove the package entirely from the system?

So far apt-get install (to properly install it, so I can properly remove it), apt-get remove, and dpkg -P have not worked.

---

### Post by ikesfreedomworld on 2007-10-22
I am not sure how similar my problem is to any of these previous posts.  I upgraded my Gateway M275 laptop from feisty to gusty the other day (in fact I tried twice).  It seems to upgrade just fine but when rebooting after completing the install, it finishes the grub bootloader, goes through some startup things then gets hung up with a black, blank screen and a blinking cursor.    It will not respond to keystrokes or anything else and seems to just hang up.

Has anyone had this before.  Should I just wait till this upgrade gets some real world use before bothering again.  I am new to Linux and Ubuntu, so I want to hold off before I try installing this on any other computers.

---

### Post by eyemou on 2007-10-22
> **Lord Landis said:**
> Here's a solid way to save your data, but you'll have to install twice.

[LIST=1]
[*]On the first install, create a new partition in the unused space for the install, and then mount the existing partition as /media/hdb or something like that.
[*]Boot into the newly-installed system.
[*]Back up your data from /media/hdb to a CD, USB drive, or network drive.
[*]Reboot to the LiveCD again, and perform a clean install that wipes the entire disk.
[*]Boot to the newly-newly-installed system.
[*]Copy the backed-up data to your box.
[*]Profit.
[/LIST]

It's a pain, but it's going to be pretty much the only way you can save that data.  Just booting with the CD isn't necessarily going to allow you to access the data on the hard-drive to save/recover/back it up, as it might not mount the hard-drive.

I may have to go the re-install route. I posted another thread with my backup idea, looking for a quick sanity check. It's a little different from the one outlined above. Anyone see any glaring issues/stupidity on my part? Here it is:

[http://ubuntuforums.org/showthread.php?p=3601010#post3601010](http://ubuntuforums.org/showthread.php?p=3601010#post3601010)

---

### Post by gannon on 2007-10-22
> **ikesfreedomworld said:**
> I am not sure how similar my problem is to any of these previous posts.  I upgraded my Gateway M275 laptop from feisty to gusty the other day (in fact I tried twice).  It seems to upgrade just fine but when rebooting after completing the install, it finishes the grub bootloader, goes through some startup things then gets hung up with a black, blank screen and a blinking cursor.

Same here, so I'm going to end up reinstalling 7.04 later.

---

### Post by scottmuz on 2007-10-22
Austin17 I had exactly the same problem with my upgrader crashing.
My system seems to be fine.

If you're not getting the upgrade
icon apearing and complaining about anything being out of date you are fine.

You should run
sudo apt-get clean 
to remove all the downloaded packages.

---

### Post by cygnis1 on 2007-10-22
I also am having issues with the upgrade to gutsy.  Can I do a clean install?  My system is a dual boot ubuntu/xp laptop.
Cygnis1

---

### Post by eyemou on 2007-10-23
Well, removing/purging bsdmainutils via aptitude (and not apt-get), and then a reinstall of the package, got me unstuck. After that, it was back to apt-get (update + update), and almost everything worked fine. Oh, and the occasional apt-get -f install.

All in all, everything seems to work... I just had to reinstall gtk-qt-engine (I'm using KDE, so apps like Firefox looked a bit off), as well as play around with my fonts.

---

### Post by Austin17 on 2007-10-23
Well at this point, because for the most part I think I got the issues on my secondary computer sorted out, that I might put Gusty on my main one.

The setup of my main computer is that I have 2 150GB hard drives, with Windows XP taking up all of the first hard drive, and on the second hard drive I have 100GB as NTFS for Windows Games, and 50GB given to Ubuntu. I'm wondering if worst comes to happen, can I rescue my duel-boot and get into Windows at least? And then put Ubuntu back on the old partitions from a clean install? Thanks for all the help so far.

Oh, and by the way, I have Automatix. Could that mess anything up?

---

### Post by Kaptain Chaos on 2007-10-23
Hello Austin,

The general concensus is that you should remove Automatix from your system AND check that the sources do NOT contain any reference to Automatix (delete them if they remain). Automatix is not recommended by Ubuntu for whatever reason (I think mainly because so many people with Automatix installed have reported broken systems after upgrading - whether that's Automatix fault or not).

Two questions:
a) Did your other PC (with Gutsy) have Automatix installed and
b) does it also have two hard drives? 

My main reason for asking is that I (and others) have had problems related to having more than one hard drive, if so, I'd check and see if a live CD runs on your main system before trying to upgrade if that's possible. Heldal's post (#7) would certainly be helpful to try if, on booting up after the upgrade there were problems recognising your two drives with the new kernel.

---

### Post by Austin17 on 2007-10-23
Thanks Kaptain Chaos, I'll follow the directions you gave me.

I just thought of another thing though, how do I find out which packages were supposed to be removed, but weren't because of the computer not getting to the clean up section of the update? I would like to know this so that I can manually clean out the old packages.

---

### Post by Lord Landis on 2007-10-24
> **Kaptain Chaos said:**
> 
My main reason for asking is that I (and others) have had problems related to having more than one hard drive, if so, I'd check and see if a live CD runs on your main system before trying to upgrade if that's possible.

I've done two upgrades, and have two hard-drives in my main system.  I've never encountered a problem because of this.  I guess the question is, do you have multiple hard-drives AND a dual-boot system?

FWIW, I have my second drive mounted as /home, and it's never been a problem.  In fact, it makes life easier because the only real changes occur on the primary drive and pretty much everything else (including Firefox bookmarks & my Thunderbird mail folders) is untouched.

---

### Post by Austin17 on 2007-10-24
Lord Landis:
I do have two hard drives and dual boot. Both drives are 150 GB and on the first drive I have given the whole thing to Windows, and on the second drive 50 GB are given to Ubuntu and 100 GB are given to an NTFS partition for extra space for games in Windows. Could this cause a problem? Thanks for all the help so far.

---

### Post by Lord Landis on 2007-10-24
Austin17:

Possibly.  Any time I've done a dual-boot, I've always installed Ubuntu to the primary/master drive, rather than the secondary/slave.  Still, Grub shouldnt' have any issues with recognizing the install.

---

### Post by Austin17 on 2007-10-24
Ok, thanks for all the help guys. At this point I'm planning on upgrading my main system to Gusty tomorrow. I'll try to post to let you guys know how it goes.

One last thing is, if it doesn't make it to the clean up stage (like my other computer), how do I know what packages to remove?

---

### Post by Austin17 on 2007-10-25
Sorry for the double post, but I upgraded my main computer to gusty this morning. Before doing so I deleted Automatix and disabled my effects. The install asked me if I wanted to replace a configuration file, but thats it. Gusty is running great! Thanks for all the help guys! Even though it doesn't really matter too much anymore, I am wondering how do I know what packages to remove on my spair/older computer because it didn't make it to the clean up stage?

---

### Post by davekenny on 2007-10-27
If this already appears. I'm sorry for the duplication, but I tried to search this thread but couldn't find info I the problems I had. So I thought I post my problem and the solution.

I was running 7.04 - no problems
upgraded to 7.10 - most things worked. apache2 would not start!!!
I might have more problems but haven't found them yet.
anyway back to the apache2 problem. tried many things but found in one of my virtual sites a change for some reason it now think it needed the perl apache::asp module. I never install this under 7.04. since I hadn't planning on running ASP code under apache2 on ubuntu. I suspect the upgrade process found the old .asp files in the virtual sites and added the handler in the virtual site file. It didn't add the necessary supporting files. oops


DaveKenny

---

### Post by Bergen on 2007-12-06
Just installed Gusty and installed all the updated right after. Halfway the updates I get a looooong list of scrollkeeper parsing errors:
```
Uitpakken van vervangende python-bittorrent ...
Voorbereiden om capplets-data 1:2.20.0.1-0ubuntu5 te vervangen (door .../capplets-data_1%3a2.20.1-0ubuntu1_all.deb) ...
Uitpakken van vervangende capplets-data ...
Voorbereiden om libpng12-0 1.2.15~beta5-2build1 te vervangen (door .../libpng12-0_1.2.15~beta5-2ubuntu0.1_i386.deb) ...
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4153: parser error : Extra content at the end of the document
itle>
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4153: parser error : Extra content at the end of the document
itle>
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4153: parser error : Extra content at the end of the document
itle>
^
/var/lib/scrollkeeper/sv/scrollkeeper_cl.xml:793: parser error : Extra content at the end of the document
</ScrollKeeperContentsList>
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4153: parser error : Extra content at the end of the document
itle>
^
/var/lib/scrollkeeper/sv/scrollkeeper_cl.xml:793: parser error : Extra content at the end of the document
</ScrollKeeperContentsList>
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4153: parser error : Extra content at the end of the document
itle>
^
/var/lib/scrollkeeper/sv/scrollkeeper_cl.xml:793: parser error : Extra content at the end of the document
</ScrollKeeperContentsList>
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4153: parser error : Extra content at the end of the document
itle>
^
/var/lib/scrollkeeper/sv/scrollkeeper_cl.xml:793: parser error : Extra content at the end of the document
</ScrollKeeperContentsList>
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4153: parser error : Extra content at the end of the document
itle>
^
/var/lib/scrollkeeper/sv/scrollkeeper_cl.xml:793: parser error : Extra content at the end of the document
</ScrollKeeperContentsList>
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4153: parser error : Extra content at the end of the document
itle>
^
/var/lib/scrollkeeper/sv/scrollkeeper_cl.xml:793: parser error : Extra content at the end of the document
</ScrollKeeperContentsList>
^
/var/lib/scrollkeeper/sv/scrollkeeper_cl.xml:793: parser error : Extra content at the end of the document
</ScrollKeeperContentsList>
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4153: parser error : Extra content at the end of the document
itle>
^
/var/lib/scrollkeeper/sv/scrollkeeper_cl.xml:793: parser error : Extra content at the end of the document
</ScrollKeeperContentsList>
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4153: parser error : Extra content at the end of the document
itle>
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4153: parser error : Extra content at the end of the document
itle>
^
/var/lib/scrollkeeper/sv/scrollkeeper_cl.xml:793: parser error : Extra content at the end of the document
</ScrollKeeperContentsList>
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4153: parser error : Extra content at the end of the document
itle>
^
/var/lib/scrollkeeper/sv/scrollkeeper_cl.xml:793: parser error : Extra content at the end of the document
</ScrollKeeperContentsList>
^
/var/lib/scrollkeeper/sv/scrollkeeper_cl.xml:793: parser error : Extra content at the end of the document
</ScrollKeeperContentsList>
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4153: parser error : Extra content at the end of the document
itle>
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4153: parser error : Extra content at the end of the document
itle>
^
/var/lib/scrollkeeper/sv/scrollkeeper_cl.xml:793: parser error : Extra content at the end of the document
</ScrollKeeperContentsList>
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4153: parser error : Extra content at the end of the document
itle>
^
/var/lib/scrollkeeper/sv/scrollkeeper_cl.xml:793: parser error : Extra content at the end of the document
</ScrollKeeperContentsList>
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4153: parser error : Extra content at the end of the document
itle>
^
/var/lib/scrollkeeper/sv/scrollkeeper_cl.xml:793: parser error : Extra content at the end of the document
</ScrollKeeperContentsList>
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4153: parser error : Extra content at the end of the document
itle>
^
/var/lib/scrollkeeper/sv/scrollkeeper_cl.xml:793: parser error : Extra content at the end of the document
</ScrollKeeperContentsList>
^
/var/lib/scrollkeeper/sv/scrollkeeper_cl.xml:793: parser error : Extra content at the end of the document
</ScrollKeeperContentsList>
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4153: parser error : Extra content at the end of the document
itle>
^
/var/lib/scrollkeeper/sv/scrollkeeper_cl.xml:793: parser error : Extra content at the end of the document
</ScrollKeeperContentsList>
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4153: parser error : Extra content at the end of the document
itle>
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4153: parser error : Extra content at the end of the document
itle>
^
/var/lib/scrollkeeper/sv/scrollkeeper_cl.xml:793: parser error : Extra content at the end of the document
</ScrollKeeperContentsList>
^
/var/lib/scrollkeeper/sv/scrollkeeper_cl.xml:793: parser error : Extra content at the end of the document
</ScrollKeeperContentsList>
^
/var/lib/scrollkeeper/sv/scrollkeeper_cl.xml:793: parser error : Extra content at the end of the document
</ScrollKeeperContentsList>
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4153: parser error : Extra content at the end of the document
itle>
^
/var/lib/scrollkeeper/es/scrollkeeper_extended_cl.xml:4153: parser error : Extra content at the end of the document
itle>
^
Uitpakken van vervangende libpng12-0 ...
Voorbereiden om libcairo2 1.4.10-1ubuntu4 te vervangen (door .../libcairo2_1.4.10-1ubuntu4.1_i386.deb) ...
Uitpakken van vervangende libcairo2 ...
Voorbereiden om libdecoration0 1:0.6.0+git20071008-0ubuntu1 te vervangen (door .../libdecoration0_1%3a0.6.0+git20071008-0ubuntu1.1_i386.deb) ...
Uitpakken van vervangende libdecoration0 ...
Voorbereiden om libpango1.0-common 1.18.2-0ubuntu1 te vervangen (door .../libpango1.0-common_1.18.3-0ubuntu1_all.deb) ...
Cleaning up font configuration of pango...
Cleaning up category xfont..
```
As you can see it continues normally with the rest of the updates, but someone should probably look into these errors.

---

