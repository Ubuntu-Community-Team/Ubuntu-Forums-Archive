---
title: "Upgrade problem"
date: 2015-11-17
forum: Installation &amp; Upgrades
---

### Post by erictherev on 2015-11-17
I was recently in the process of upgrading to 15.10 when my system lost power. I do about 99% of my work with my linux systems in putty. (I know, upgrading via ssh is never a good idea. It just has never been an issue... until now.)

After booting the system back up, the upgrade will not continue. Here is what I am dealing with:

root@Tython:/home/nomad# do-release-upgrade
```
Checking for a new Ubuntu release
No new release found
```
root@Tython:/home/nomad# apt-get upgrade
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 kde-l10n-engb : Breaks: kde-config-telepathy-accounts (< 15.04) but 0.9.0-0ubuntu1 is installed
 kde-telepathy : Depends: kde-telepathy-minimal (= 15.04.20ubuntu1) but 0.9.0ubuntu1 is installed
 kde-telepathy-text-ui : Depends: libktpotr9 (>= 15.03.80) but it is not installed
E: Unmet dependencies. Try using -f.
```
root@Tython:/home/nomad# apt-get dist-upgrade
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 kde-l10n-engb : Breaks: kde-config-telepathy-accounts (< 15.04) but 0.9.0-0ubuntu1 is installed
 kde-telepathy : Depends: kde-telepathy-minimal (= 15.04.20ubuntu1) but 0.9.0ubuntu1 is installed
 kde-telepathy-text-ui : Depends: libktpotr9 (>= 15.03.80) but it is not installed
E: Unmet dependencies. Try using -f.
```
root@Tython:/home/nomad# apt-get -f install
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gir1.2-gtop-2.0 libaccounts-qt1 libavdevice55 libbaloopim4
  libboost-filesystem1.55.0 libboost-locale1.55.0 libboost-regex1.55.0
  libboost-system1.55.0 libboost-thread1.55.0 libcompress-raw-lzma-perl
  libedata-cal-1.2-23 libfollowupreminder4 libgtkhtml-4.0-0
  libgtkhtml-4.0-common libgtkhtml-editor-4.0-0 libinput7
  libio-compress-lzma-perl libkdgantt2-0 libkf5dbusaddons-bin
  libkf5iconthemes-bin libkf5sysguard5 libkf5sysguard5-data libkf5xmlgui-bin
  libkf5xmlrpcclientprivate5 libkgapi2-2 libmirclient8 libmircommon3
  libmirprotobuf0 liboath0 libprotobuf9 librhythmbox-core8 libsendlater4
  libsignon-qt1 libwps-0.3-3 mir-client-platform-mesa2 rhythmbox-mozilla
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  kde-config-telepathy-accounts kde-telepathy-minimal libktpotr9
The following packages will be REMOVED:
  libktpotrprivate8
The following NEW packages will be installed:
  libktpotr9
The following packages will be upgraded:
  kde-config-telepathy-accounts kde-telepathy-minimal
2 upgraded, 1 newly installed, 1 to remove and 1419 not upgraded.
3 not fully installed or removed.
Need to get 0 B/285 kB of archives.
After this operation, 1,766 kB disk space will be freed.
Do you want to continue? [Y/n] y
Setting up zlib1g:i386 (1:1.2.8.dfsg-2ubuntu4) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
(Reading database ... 261640 files and directories currently installed.)
Preparing to unpack .../kde-config-telepathy-accounts_4%3a15.08.2-0ubuntu1_i386.deb ...
Unpacking kde-config-telepathy-accounts (4:15.08.2-0ubuntu1) over (0.9.0-0ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.08.2-0ubuntu1_i386.deb (--unpack):
 trying to overwrite '/usr/share/accounts/services/google-im.service', which is also in package account-plugin-google 0.12+15.04.20150415.1-0ubuntu2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.08.2-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
root@Tython:/home/nomad# dpkg --configure -a
```
dpkg: dependency problems prevent configuration of kde-telepathy:
 kde-telepathy depends on kde-telepathy-minimal (= 15.04.20ubuntu1); however:
  Version of kde-telepathy-minimal on system is 0.9.0ubuntu1.

dpkg: error processing package kde-telepathy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kde-telepathy-text-ui:
 kde-telepathy-text-ui depends on libktpotr9 (>= 15.03.80); however:
  Package libktpotr9 is not installed.

dpkg: error processing package kde-telepathy-text-ui (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 kde-telepathy
 kde-telepathy-text-ui
```
root@Tython:/home/nomad# cat -n /etc/apt/sources.list
```
     1  # deb cdrom:[Kubuntu 13.04 _Raring Ringtail_ - Release i386 (20130424)]/ raring main multiverse restricted universe
     2
     3  # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4  # newer versions of the distribution.
     5  deb http://us.archive.ubuntu.com/ubuntu/ wily main restricted
     6  deb-src http://us.archive.ubuntu.com/ubuntu/ wily main restricted
     7
     8  ## Major bug fix updates produced after the final release of the
     9  ## distribution.
    10  deb http://us.archive.ubuntu.com/ubuntu/ wily-updates main restricted
    11  deb-src http://us.archive.ubuntu.com/ubuntu/ wily-updates main restricted
    12
    13  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14  ## team. Also, please note that software in universe WILL NOT receive any
    15  ## review or updates from the Ubuntu security team.
    16  deb http://us.archive.ubuntu.com/ubuntu/ wily universe
    17  deb-src http://us.archive.ubuntu.com/ubuntu/ wily universe
    18  deb http://us.archive.ubuntu.com/ubuntu/ wily-updates universe
    19  deb-src http://us.archive.ubuntu.com/ubuntu/ wily-updates universe
    20
    21  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    22  ## team, and may not be under a free licence. Please satisfy yourself as to
    23  ## your rights to use the software. Also, please note that software in
    24  ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25  ## security team.
    26  deb http://us.archive.ubuntu.com/ubuntu/ wily multiverse
    27  deb-src http://us.archive.ubuntu.com/ubuntu/ wily multiverse
    28  deb http://us.archive.ubuntu.com/ubuntu/ wily-updates multiverse
    29  deb-src http://us.archive.ubuntu.com/ubuntu/ wily-updates multiverse
    30
    31  ## N.B. software from this repository may not have been tested as
    32  ## extensively as that contained in the main release, although it includes
    33  ## newer versions of some applications which may provide useful features.
    34  ## Also, please note that software in backports WILL NOT receive any review
    35  ## or updates from the Ubuntu security team.
    36  deb http://us.archive.ubuntu.com/ubuntu/ wily-backports main restricted universe multiverse
    37  deb-src http://us.archive.ubuntu.com/ubuntu/ wily-backports main restricted universe multiverse
    38
    39  deb http://security.ubuntu.com/ubuntu wily-security main restricted
    40  deb-src http://security.ubuntu.com/ubuntu wily-security main restricted
    41  deb http://security.ubuntu.com/ubuntu wily-security universe
    42  deb-src http://security.ubuntu.com/ubuntu wily-security universe
    43  deb http://security.ubuntu.com/ubuntu wily-security multiverse
    44  deb-src http://security.ubuntu.com/ubuntu wily-security multiverse
    45
    46  ## Uncomment the following two lines to add software from Canonical's
    47  ## 'partner' repository.
    48  ## This software is not part of Ubuntu, but is offered by Canonical and the
    49  ## respective vendors as a service to Ubuntu users.
    50  # deb http://archive.canonical.com/ubuntu raring partner
    51  # deb-src http://archive.canonical.com/ubuntu raring partner
    52
```
root@Tython:/home/nomad# ls -la /etc/apt/sources.list.d
```
total 16
drwxr-xr-x 2 root root 4096 Nov 15 07:35 .
drwxr-xr-x 6 root root 4096 Nov 14 16:36 ..
-rw-r--r-- 1 root root  176 Nov 15 07:35 google-chrome.list
-rw-r--r-- 1 root root  209 Nov 14 16:44 google-chrome.list.distUpgrade

```
root@Tython:/home/nomad# tail -v -n +1 /etc/apt/sources.list.d/*
```
==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main

==> /etc/apt/sources.list.d/google-chrome.list.distUpgrade <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb http://dl.google.com/linux/chrome/deb/ stable main # disabled on upgrade to vivid
```

In addition to what is posted above, I have unsuccessfully attempted to boot from a USB drive. Booting from installation media is not my preferred method for repair due to my inability to remember the architecture of my build (x86 or x64).

The system runs and I can still connect via ssh, but I would like to have the system fully functional.

Any help would be greatly appreciated.

---

### Post by QIII on 2015-11-17
Yes you were and please don't.

Moved to its own thread from [here]("http://ubuntuforums.org/showthread.php?t=2301084").

---

### Post by erictherev on 2015-11-17
After a little more looking around online, I tried this:

root@Tython:/home/nomad# apt-get upgrade --fix-broken
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
Calculating upgrade... The following packages were automatically installed and are no longer required:
  gir1.2-gtop-2.0 gir1.2-vte-2.90 kde-config-touchpad libaccounts-qt1
  libavdevice55 libbaloopim4 libboost-filesystem1.55.0 libboost-locale1.55.0
  libboost-regex1.55.0 libboost-system1.55.0 libboost-thread1.55.0
  libdirac-encoder0 libebackend-1.2-7 libebook-1.2-14 libebook-contacts-1.2-0
  libecal-1.2-16 libedata-book-1.2-20 libedata-cal-1.2-23 libexiv2-13
  libfollowupreminder4 libgnome-bluetooth11 libgphoto2-port10 libgtkhtml-4.0-0
  libgtkhtml-4.0-common libgtkhtml-editor-4.0-0 libhogweed2 libinput7 libisl10
  libkdgantt2-0 libkf5su-bin libkf5sysguard5 libkf5sysguard5-data
  libkf5xmlrpcclientprivate5 libkgapi2-2 libmirclient8 libmircommon3
  libmirprotobuf0 liboath0 libplist2 libprotobuf9 librhythmbox-core8
  libsendlater4 libsignon-qt1 libvte-2.90-9 libvte-2.90-common libwps-0.3-3
  mir-client-platform-mesa2 rhythmbox-mozilla
Use 'apt-get autoremove' to remove them.
Done
The following packages will be REMOVED:
  libktpotrprivate8
The following NEW packages will be installed:
  libktpotr9
The following packages have been kept back:
  account-plugin-aim account-plugin-jabber account-plugin-salut
  account-plugin-yahoo breeze breeze-cursor-theme breeze-icon-theme
  browser-plugin-gnash clamfs cpp cups-filters cups-filters-core-drivers
  dolphin empathy empathy-common gcc gdb gettext-base gimp gir1.2-totem-1.0
  gir1.2-tracker-1.0 gnash gnash-common gnome-contacts gnome-dictionary
  gnome-documents gnome-sudoku gnome-sushi gramps grilo-plugins-0.2-base
  gstreamer0.10-plugins-ugly gstreamer1.0-plugins-ugly
  gstreamer1.0-plugins-ugly-amr icedtea-7-jre-jamvm kactivities
  kde-style-breeze kde-style-breeze-qt4 kdeplasma-addons-data khelpcenter kpat
  krdc ktexteditor-data kwin kwin-addons kwin-data kwin-style-breeze
  libasprintf-dev libastro1 libclamav6 libenchant1c2a libepub0 libjson-xs-perl
  libkcddb4 libkf5sonnet5-data libkf5sonnetcore5 libkf5su5 libkf5texteditor5
  liblist-moreutils-perl libpod-readme-perl libpurple0 libqgpgme1
  libstartup-notification0 libtelepathy-farstream3 libtotem-plparser18
  libtotem0 libtracker-control-1.0-0 libtracker-miner-1.0-0
  libtracker-sparql-1.0-0 libwireshark-data libwireshark5 libwpg-0.3-3
  libxcb-image0 linux-generic linux-headers-generic linux-image-generic
  marble-plugins mcp-account-manager-uoa metacity metacity-common
  openjdk-7-jre openjdk-7-jre-headless pam-kwallet plasma-dataengines-addons
  plasma-runners-addons plasma-wallpapers-addons plasma-widget-kimpanel
  plasma-widgets-addons powerdevil powerdevil-data python-oauthlib
  python-openssl python3-pykde4 qml-module-org-kde-extensionplugin
  qml-module-qtquick-controls-styles-breeze qpdf rygel rygel-playbin
  rygel-preferences sessioninstaller sonnet-plugins sound-juicer supertux
  supertux-data totem totem-common totem-plugins tracker tracker-extract
  tracker-gui tracker-miner-fs wireshark wireshark-common xdg-utils
  xserver-xephyr xserver-xorg-video-intel
The following packages will be upgraded:
  about-distro account-plugin-google adduser aisleriot alsa-base alsa-utils
  app-install-data apport apport-kde apt-transport-https apt-utils aptdaemon
  aptdaemon-data apturl-common apturl-kde argyll argyll-ref ark aspell
  at-spi2-core baobab bind9-host binutils bluez-cups brasero brasero-cdrkit
  brasero-common busybox-initramfs busybox-static ca-certificates caribou
  caribou-antler cgmanager cheese cheese-common chromium-codecs-ffmpeg-extra
  clamav clamav-base clamav-daemon clamav-freshclam clamdscan clamtk colord
  colord-data command-not-found command-not-found-data conky-all console-setup
  console-setup-linux cpp-4.7 cpp-4.8 cpp-4.9 cracklib-runtime cryptsetup
  cryptsetup-bin cups cups-browsed cups-bsd cups-client cups-common
  cups-core-drivers cups-daemon cups-ppdc cups-server-common dbus-x11
  dconf-editor dconf-tools debconf-i18n debconf-kde-data dh-python dialog
  dictionaries-common diffstat dmidecode dmsetup dnsmasq-base dnsutils
  docbook-xml dosfstools dragonplayer enchant eog etherape evince
  evince-common file file-roller firefox firefox-locale-en
  flashplugin-installer folks-common fonts-dejavu-core fonts-dejavu-extra
  fonts-lyx fonts-opensymbol foomatic-db-compressed-ppds four-in-a-row
  freerdp-x11 friendly-recovery frozen-bubble frozen-bubble-data ftp fuse
  gcc-4.7-base gcc-4.8 gcc-4.8-base gcc-4.9 gcc-4.9-base gconf-service
  gconf-service-backend gconf2 gconf2-common gcr gdbserver gdebi gdebi-core
  gdisk gedit gedit-common geoip-database gettext ghostscript ghostscript-x
  gimp-data gir1.2-accountsservice-1.0 gir1.2-atk-1.0 gir1.2-atspi-2.0
  gir1.2-caribou-1.0 gir1.2-clutter-gst-2.0 gir1.2-cogl-1.0
  gir1.2-coglpango-1.0 gir1.2-evince-3.0 gir1.2-gck-1 gir1.2-gcr-3
  gir1.2-gdata-0.0 gir1.2-gdesktopenums-3.0 gir1.2-gdkpixbuf-2.0
  gir1.2-gexiv2-0.10 gir1.2-gmenu-3.0 gir1.2-gst-plugins-base-1.0
  gir1.2-gstreamer-1.0 gir1.2-gtkclutter-1.0 gir1.2-gtksource-3.0
  gir1.2-gucharmap-2.90 gir1.2-ibus-1.0 gir1.2-javascriptcoregtk-3.0
  gir1.2-json-1.0 gir1.2-networkmanager-1.0 gir1.2-nmgtk-1.0
  gir1.2-osmgpsmap-1.0 gir1.2-packagekitglib-1.0 gir1.2-panelapplet-5.0
  gir1.2-polkit-1.0 gir1.2-rest-0.7 gir1.2-secret-1 gir1.2-soup-2.4
  gir1.2-totem-plparser-1.0 gir1.2-udisks-2.0 gir1.2-upowerglib-1.0
  gir1.2-vte-2.91 gir1.2-webkit-3.0 gir1.2-wnck-3.0 gir1.2-zeitgeist-2.0 gjs
  gnome-applets gnome-applets-data gnome-backgrounds gnome-calculator
  gnome-cards-data gnome-chess gnome-color-manager
  gnome-control-center-shared-data gnome-desktop3-data gnome-disk-utility
  gnome-keyring gnome-klotski gnome-mahjongg gnome-nibbles gnome-online-miners
  gnome-orca gnome-packagekit gnome-packagekit-data gnome-packagekit-session
  gnome-panel gnome-panel-data gnome-robots gnome-screensaver gnome-screenshot
  gnome-session-flashback gnome-system-log gnome-terminal gnome-terminal-data
  gnome-tetravex gnome-tweak-tool gnome-user-guide gnome-user-share gnuchess
  gnupg-agent gnupg2 gpgsm graphviz grilo-plugins-0.2 grilo-plugins-0.2-extra
  grub-common grub-pc grub-pc-bin grub2-common gsettings-ubuntu-schemas
  gstreamer-qapt gstreamer0.10-nice gstreamer0.10-plugins-bad
  gstreamer0.10-pulseaudio gstreamer0.10-qapt gstreamer1.0-clutter
  gstreamer1.0-libav gstreamer1.0-nice gstreamer1.0-plugins-base
  gstreamer1.0-pulseaudio gstreamer1.0-x gtk2-engines-pixbuf gucharmap
  gwenview hicolor-icon-theme hplip hplip-data humanity-icon-theme
  i965-va-driver ibus ibus-qt4 ifupdown im-config imagemagick
  imagemagick-6.q16 indicator-datetime indicator-keyboard indicator-messages
  indicator-power indicator-session indicator-sound info initramfs-tools
  initramfs-tools-bin inputattach intltool-debian iproute iproute2 irqbalance
  isc-dhcp-client isc-dhcp-common iso-codes k3b-i18n kaccessible kamera kate
  kate5-data kbd kcalc kde-base-artwork kde-baseapps-bin kde-baseapps-data
  kde-cli-tools kde-cli-tools-data kde-config-gtk-style
  kde-config-gtk-style-preview kde-config-sddm kde-config-telepathy-accounts
  kde-config-whoopsie kde-style-oxygen-qt5 kde-telepathy-minimal
  kde-wallpapers kde-wallpapers-default kde-zeroconf kdebase-runtime kded5
  kdemultimedia-kio-plugins kdenetwork-filesharing kdepasswd
  keyboard-configuration khelpcenter4 khotkeys khotkeys-data
  kimageformat-plugins kinfocenter kinit kio-audiocd kio-mtp kmag kmenuedit
  kmix kmod kmousetool konsole konsole-kpart kpackagelauncherqml kpartx
  kpartx-boot kppp krb5-locales kross kscreen ksshaskpass ksystemlog
  ktexteditor-katepart kubuntu-debug-installer kubuntu-desktop
  kubuntu-driver-manager kubuntu-notification-helper kwalletmanager kwrited
  language-pack-en language-pack-en-base language-selector-common liba52-0.7.4
  libaccount-plugin-generic-oauth libaccount-plugin-google libaccounts-qt1
  libakonadi-kabc4 libalien-sdl-perl libapparmor-perl libapparmor1
  libarchive-extract-perl libarchive-zip-perl libarchive13 libasan0 libasan1
  libasn1-8-heimdal libasound2 libasound2-data libasound2-plugins libaspell15
  libass5 libassuan0 libatk-adaptor libatk-bridge2.0-0 libatk-wrapper-java
  libatk-wrapper-java-jni libatomic1 libatspi2.0-0 libattica0.4
  libaudit-common libaudit1 libautodie-perl libbabl-0.1-0 libbaloocore4
  libbalooqueryparser4 libbind9-90 libblkid1 libbluetooth3 libbonoboui2-0
  libbonoboui2-common libbrasero-media3-1 libbrlapi0.6 libburn4 libcaca0
  libcairo-gobject2 libcairo-perl libcairo2 libcap-ng0 libcap2 libcap2-bin
  libcapture-tiny-perl libcaribou-common libcaribou-gtk-module
  libcaribou-gtk3-module libcaribou0 libcdt5 libcgi-fast-perl libcgi-pm-perl
  libcgmanager0 libcgraph6 libcheese-gtk23 libcheese7 libchromaprint0
  libcilkrts5 libclass-c3-perl libclone-perl libcloog-isl4
  libclutter-1.0-common libclutter-gst-2.0-0 libclutter-gtk-1.0-0
  libcogl-common libcogl-pango20 libcogl-path20 libcolord2 libcolorhug2
  libcommon-sense-perl libcompress-bzip2-perl libcompress-raw-lzma-perl
  libcrack2 libcryptsetup4 libcups2 libcupscgi1 libcupsfilters1 libcupsimage2
  libcupsmime1 libcupsppdc1 libcurl3 libcurl3-gnutls libdatrie1 libdb5.3
  libdbusmenu-qt2 libdbusmenu-qt5 libdebconf-kde1 libdee-1.0-4
  libdevmapper-event1.02.1 libdevmapper1.02.1 libdiscid0 libdjvulibre-text
  libdjvulibre21 libdlrestrictions1 libdmapsharing-3.0-2 libdns-export100
  libdns100 libdpkg-perl libdrm-intel1 libdrm-nouveau2 libdrm-radeon1 libdrm2
  libdvdnav4 libe-book-0.1-1 libedit2 libegl1-mesa-drivers libelf1
  libemail-valid-perl libestr0 libetonyek-0.1-1 libevdev2 libevdocument3-4
  libevview3-3 libexempi3 libexpat1 libfaad2 libfcitx-config4
  libfcitx-gclient0 libfcitx-utils0 libffi6 libfile-basedir-perl
  libfile-desktopentry-perl libfile-fcntllock-perl libfile-mimeinfo-perl
  libfile-which-perl libflac8 libfluidsynth1 libfolks-eds25
  libfolks-telepathy25 libfolks25 libfontembed1 libfontenc1 libfreehand-0.1-1
  libfreerdp-cache1.1 libfreerdp-client1.1 libfreerdp-codec1.1
  libfreerdp-common1.1.0 libfreerdp-core1.1 libfreerdp-crypto1.1
  libfreerdp-gdi1.1 libfreerdp-locale1.1 libfreerdp-plugins-standard
  libfreerdp-primitives1.1 libfreerdp-rail1.1 libfreerdp-utils1.1 libfreetype6
  libfribidi0 libfs6 libfuse2 libgail-common libgail18 libgcc-4.8-dev
  libgcc-4.9-dev libgck-1-0 libgconf-2-4 libgconf2-4 libgcr-3-common
  libgcr-base-3-1 libgcr-ui-3-1 libgd3 libgdata-common libgdict-common
  libgdk-pixbuf2.0-0 libgdk-pixbuf2.0-common libgee-0.8-2 libgee2
  libgeocode-glib0 libgeoip1 libgettextpo-dev libgettextpo0 libgexiv2-2
  libgfbgraph-0.2-0 libgfortran3 libgimp2.0 libgit2-22 libgl1-mesa-glx
  libglapi-mesa libgles2-mesa libglib-perl libglib2.0-data libgme0 libgmp10
  libgmpxx4ldbl libgnome-desktop-3-10 libgnome-menu-3-0 libgnomevfs2-0
  libgnomevfs2-common libgnomevfs2-extra libgomp1 libgpgme11 libgphoto2-6
  libgphoto2-l10n libgpod-common libgpod4 libgrilo-0.2-1 libgs9 libgs9-common
  libgsf-1-114 libgsf-1-common libgsl0ldbl libgssapi-krb5-2 libgssapi3-heimdal
  libgssdp-1.0-3 libgstreamer-plugins-bad0.10-0 libgstreamer0.10-0
  libgtk-3-bin libgtk2-perl libgtk2.0-0 libgtk2.0-bin libgtk2.0-common
  libgtksourceview-3.0-1 libgtksourceview-3.0-common libgtkspell3-3-0
  libgucharmap-2-90-7 libgudev-1.0-0 libgupnp-1.0-4 libgupnp-av-1.0-2
  libgupnp-dlna-2.0-3 libgusb2 libgutenprint2 libgvc6 libgvpr2
  libgweather-common libgxps2 libharfbuzz-icu0 libharfbuzz0b
  libhcrypto4-heimdal libhdb9-heimdal libheimbase1-heimdal
  libheimntlm0-heimdal libhpmud0 libhtml-format-perl libhtml-parser-perl
  libhtml-tree-perl libhunspell-1.3-0 libhx509-5-heimdal libibus-1.0-5
  libibus-qt1 libical1a libido3-0.1-0 libijs-0.35 libimage-magick-perl
  libimage-magick-q16-perl libimlib2 libimobiledevice4
  libio-compress-lzma-perl libio-socket-inet6-perl libio-socket-ssl-perl
  libipc-run-perl libirs-export91 libisc-export95 libisc95 libisccc90
  libisccfg-export90 libisccfg90 libisl13 libisofs6 libitm1 libjack-jackd2-0
  libjavascriptcoregtk-3.0-0 libjbig2dec0 libjson-glib-1.0-0
  libjson-glib-1.0-common libjson-perl libk5crypto3 libkactivities6
  libkcompactdisc4 libkdc2-heimdal libkdcraw-data libkdcraw23
  libkf5activities5 libkf5archive5 libkf5bookmarks-data libkf5bookmarks5
  libkf5crash5 libkf5dbusaddons-bin libkf5dnssd-data libkf5dnssd5
  libkf5emoticons-bin libkf5emoticons-data libkf5emoticons5
  libkf5iconthemes-bin libkf5itemmodels5 libkf5js5 libkf5jsembed-data
  libkf5jsembed5 libkf5kdelibs4support-data libkf5kdelibs4support5
  libkf5kdelibs4support5-bin libkf5khtml-bin libkf5khtml-data libkf5khtml5
  libkf5kiofilewidgets5 libkf5kiontlm5 libkf5krosscore5 libkf5krossui5
  libkf5modemmanagerqt6 libkf5networkmanagerqt6 libkf5newstuff-data
  libkf5newstuff5 libkf5parts-data libkf5parts-plugins libkf5parts5
  libkf5plasma5 libkf5pty-data libkf5pty5 libkf5runner5 libkf5screen6
  libkf5service-bin libkf5solid5 libkf5solid5-data libkf5style5 libkf5su-bin
  libkf5threadweaver5 libkf5unitconversion-data libkf5unitconversion5
  libkf5waylandserver5 libkf5webkit5 libkf5xmlgui-bin libkfbapi1 libkfontinst5
  libkfontinstui5 libkipi-data libkipi11 libkmod2 libkonq-common
  libkonq5-templates libkonq5abi1 libkpathsea6 libkrb5-26-heimdal libkrb5-3
  libkrb5support0 libksane-data libksane0 libksba8 libktorrent-l10n
  libkwin4-effect-builtins1 libkwineffects6 libkwinglutils6
  libkwinxrenderutils6 libkworkspace5-5 liblastfm1 libldap-2.4-2 libldb1
  liblightdm-gobject-1-0 liblightdm-qt-3-0 liblinear-tools liblinear1
  liblocale-gettext-perl libloudmouth1-0 liblouis-data liblouis2 liblua5.1-0
  liblua5.2-0 liblvm2app2.2 liblwres90 libmagic1 libmagickcore-6.q16-2-extra
  libmail-spf-perl libmessaging-menu0 libminiupnpc10
  libmission-control-plugins0 libmm-glib0 libmodule-pluggable-perl
  libmodule-signature-perl libmotif-common libmount1 libmp3lame0 libmpeg2-4
  libmpfr4 libmpg123-0 libmspub-0.1-1 libmtp-common libmtp-runtime libmtp9
  libmuon libmysqlclient18 libmythes-1.2-0 libncurses5 libncursesw5
  libnet-domain-tld-perl libnet-http-perl libnet-ssleay-perl libnewt0.52
  libnice10 libnm-glib-vpn1 libnm-glib4 libnm-util2 libnspr4 libnspr4-0d
  libnss3 libnss3-1d libnss3-nssdb libntdb1 libnuma1 liboath0 libofa0
  libopenal-data libopenal1 libopenjpeg5 libopenobex1 liborbit-2-0 liborbit2
  libosmgpsmap-1.0-0 liboxygenstyle5-5 liboxygenstyleconfig5-5
  libp11-kit-gnome-keyring libp11-kit0 libpackagekit-glib2-16 libpam-cap
  libpam-gnome-keyring libpanel-applet0 libparse-debianchangelog-perl
  libpathplan4 libpcap0.8 libpci3 libpciaccess0 libpcre3 libpcsclite1
  libperl4-corelibs-perl libphysfs1 libpipeline1
  libplasma-geolocation-interface5 libpod-latex-perl libpolkit-backend-1-0
  libpolkit-qt-1-1 libpoppler-glib8 libpoppler-qt4-4 libpoppler-qt5-1
  libportaudio2 libpowerdevilcore2 libpowerdevilui5 libpulse-mainloop-glib0
  libpulse0 libpulsedsp libpurple-bin libpython2.7 libpython2.7-minimal
  libpython2.7-stdlib libpython3-stdlib libpython3.4 libpython3.4-minimal
  libpython3.4-stdlib libqalculate5-data libqca-qt5-2 libqca-qt5-2-plugins
  libqca2-plugin-ossl libqgsttools-p1 libqmobipocket1 libqt4-dbus
  libqt4-declarative libqt4-designer libqt4-help libqt4-network libqt4-opengl
  libqt4-qt3support libqt4-script libqt4-scripttools libqt4-sql
  libqt4-sql-mysql libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml
  libqt4-xmlpatterns libqt5clucene5 libqt5designercomponents5 libqt5help5
  libqt5multimediaquick-p5 libqt5multimediawidgets5 libqt5test5
  libqtassistantclient4 libqtcore4 libqtdbus4 libqtglib-2.0-0
  libqtgstreamer-1.0-0 libqtgstreamerui-1.0-0 libqtgui4 libqtwebkit4
  libquadmath0 libraw10 libraw1394-11 libreadline5
  libreoffice-avmedia-backend-gstreamer libreoffice-help-en-us
  libreoffice-java-common libreoffice-sdbc-firebird libreoffice-sdbc-hsqldb
  librest-0.7-0 librevenge-0.0-0 libroken18-heimdal librsvg2-2 librsvg2-common
  librtmp1 libruby2.1 libsane libsane-common libsane-hpaio libsasl2-2
  libsasl2-modules libsasl2-modules-db libsbc1 libsdl-perl libsdl1.2debian
  libsecret-1-0 libsecret-common libselinux1 libsemanage-common libsemanage1
  libsensors4 libservlet3.0-java libsgutils2-2 libshp2 libsignon-glib1
  libsignon-qt1 libslv2-9 libsmartcols1 libsmbclient libsnmp-base libsnmp30
  libsoftware-license-perl libsoundtouch0 libsoup-gnome2.4-1 libsoup2.4-1
  libspeechd2 libspeex1 libspeexdsp1 libspice-client-glib-2.0-8
  libspice-client-gtk-3.0-4 libspnav0 libsqlite3-0 libssh2-1 libssl1.0.0
  libstoken1 libsub-identify-perl libsub-name-perl libsys-hostname-long-perl
  libtalloc2 libtbb2 libtcl8.6 libtdb1 libtevent0 libtext-csv-perl
  libtext-csv-xs-perl libtext-levenshtein-perl libthai-data libthai0
  libtheora0 libtinfo5 libtk8.6 libtomcrypt0 libtommath0 libtwolame0 libubsan0
  libudisks2-0 libunity-control-center1 libunity-protocol-private0
  libunity-scopes-json-def-desktop libunity-settings-daemon1 libunity9
  libupower-glib3 liburi-perl liburl-dispatcher1 libusb-0.1-4 libusbmuxd2
  libustr-1.0-1 libutempter0 libuuid1 libv4l-0 libv4lconvert0 libva1 libvdpau1
  libvisio-0.1-1 libvte-2.91-0 libvte-2.91-common libwacom-bin libwacom-common
  libwacom2 libwavpack1 libwayland-client0 libwayland-cursor0
  libwayland-server0 libwbclient0 libweather-ion7 libwebkitgtk-3.0-0
  libwebkitgtk-3.0-common libwebpmux1 libwebrtc-audio-processing-0
  libwhoopsie-preferences0 libwhoopsie0 libwildmidi-config libwildmidi1
  libwind0-heimdal libwinpr-crt0.1 libwinpr-dsparse0.1 libwinpr-environment0.1
  libwinpr-file0.1 libwinpr-handle0.1 libwinpr-heap0.1 libwinpr-input0.1
  libwinpr-interlocked0.1 libwinpr-library0.1 libwinpr-path0.1
  libwinpr-pool0.1 libwinpr-registry0.1 libwinpr-rpc0.1 libwinpr-sspi0.1
  libwinpr-synch0.1 libwinpr-sysinfo0.1 libwinpr-thread0.1 libwinpr-utils0.1
  libwiretap4 libwmf-bin libwmf0.2-7 libwnck-3-0 libwnck-3-common
  libwpd-0.10-10 libwsutil4 libwww-perl libxaw7 libxcb-composite0
  libxcb-damage0 libxcb-dri2-0 libxcb-dri3-0 libxcb-glx0 libxcb-present0
  libxcb-randr0 libxcb-record0 libxcb-render0 libxcb-shape0 libxcb-shm0
  libxcb-xf86dri0 libxcb-xfixes0 libxcb-xkb1 libxcb-xtest0 libxcb-xv0
  libxerces-c3.1 libxfont1 libxfreerdp-client1.1 libxkbfile1 libxm4 libxml2
  libxml2-utils libxmmsclient6 libxmu6 libxmuu1 libxnvctrl0 libxrandr2
  libxrender1 libxshmfence1 libxt6 libxvidcore4 libxvmc1 libxxf86vm1 libyelp0
  libzeitgeist-2.0-0 libzvbi-common libzvbi0 lightdm lightsoff lintian
  linux-firmware linux-libc-dev linux-sound-base locales logrotate lshw make
  man-db marble-data memtest86+ milou module-init-tools muon-common
  muon-discover muon-notifier muon-updater mysql-client-core-5.6 mysql-common
  mysql-server-core-5.6 nano nautilus-data ncurses-term ndiff nmap
  notification-daemon ntfs-3g ntpdate nvidia-common okular-extra-backends
  openprinting-ppds openssh-client openssh-server openssh-sftp-server openssl
  orion-gtk-theme os-prober oxideqt-codecs-extra oxygen-icon-theme
  oxygen-sounds p11-kit p11-kit-modules p7zip-full passwd patchutils pciutils
  perlmagick pidgin pidgin-data pinentry-qt4 plasma-framework
  plasma-widget-folderview plymouth-theme-kubuntu-logo
  plymouth-theme-kubuntu-text policykit-1 polkit-kde-1 polkit-kde-agent-1
  poppler-data poppler-utils pppconfig pptp-linux print-manager
  printer-driver-gutenprint printer-driver-hpcups printer-driver-postscript-hp
  pulseaudio pulseaudio-module-bluetooth pulseaudio-module-x11
  pulseaudio-utils python-aptdaemon python-aptdaemon.gtk3widgets python-bs4
  python-characteristic python-chardet python-commandnotfound python-configobj
  python-crypto python-cups python-dbus python-dbus-dev python-debian
  python-dirspec python-gi python-gi-cairo python-glade2 python-gobject
  python-gtk2 python-html5lib python-idna python-imaging python-kde4
  python-ldb python-lxml python-ntdb python-numpy python-pam python-pil
  python-pil.imagetk python-pkg-resources python-pyasn1 python-pyasn1-modules
  python-pyatspi python-pycurl python-pyudev python-qt4 python-qt4-dbus
  python-renderpm python-reportlab python-reportlab-accel python-samba
  python-serial python-service-identity python-sip python-six python-talloc
  python-tdb python-twisted-bin python-twisted-core python-twisted-web
  python-ubuntu-sso-client python-zope.interface python2.7 python2.7-minimal
  python3 python3-apport python3-aptdaemon python3-aptdaemon.pkcompat
  python3-brlapi python3-bs4 python3-bsddb3 python3-cairo python3-chardet
  python3-commandnotfound python3-cups python3-cupshelpers python3-dbus
  python3-dbus.mainloop.pyqt5 python3-dbus.mainloop.qt python3-debian
  python3-distupgrade python3-gdbm python3-gi python3-gi-cairo
  python3-html5lib python3-icu python3-louis python3-lxml python3-mako
  python3-markupsafe python3-minimal python3-pil python3-pkg-resources
  python3-problem-report python3-pyatspi python3-pycurl python3-renderpm
  python3-reportlab python3-reportlab-accel python3-requests python3-six
  python3-smbc python3-software-properties python3-speechd
  python3-update-manager python3-urllib3 python3.4 python3.4-minimal
  qapt-batch qdbus qdbus-qt5 qml-module-org-kde-draganddrop
  qml-module-org-kde-kcoreaddons qml-module-org-kde-kio
  qml-module-org-kde-kquickcontrols qml-module-org-kde-kquickcontrolsaddons
  qml-module-org-kde-runnermodel qml-module-org-kde-solid
  qml-module-qtgraphicaleffects qml-module-qtmultimedia
  qml-module-qtquick-window2 qml-module-qtquick2 qml-module-qtwebkit qt-at-spi
  qt5-image-formats-plugins qtchooser qtcore4-l10n
  qtdeclarative5-kf5declarative qtdeclarative5-kf5solid
  qtgstreamer-declarative qttranslations5-l10n quadrapassel quassel
  quassel-data realmd rename resolvconf rsyslog ruby ruby2.1
  rubygems-integration sa-compile samba samba-common samba-common-bin
  samba-dsdb-modules samba-libs samba-vfs-modules sane-utils scdaemon sddm
  seahorse session-migration shotwell shotwell-common signon-ui
  signon-ui-service simple-scan smbclient sni-qt socat
  software-properties-common software-properties-kde spamc speech-dispatcher
  speech-dispatcher-audio-plugins spice-client-glib-usb-acl-helper sqlite3 ssh
  ssh-import-id ssl-cert sudo swell-foop syslinux syslinux-common
  syslinux-legacy system-config-printer-common system-config-printer-gnome
  system-config-printer-udev systemd-sysv systemsettings tali tcl8.6 tcpdump
  tdb-tools telepathy-mission-control-5 telnet thermald time tk8.6
  transmission-common transmission-gtk ttf-dejavu-core ttf-ubuntu-font-family
  tzdata tzdata-java ubuntu-drivers-common ubuntu-minimal ubuntu-mono
  ubuntu-release-upgrader-core ubuntu-release-upgrader-qt ubuntu-sso-client
  ubuntu-standard ubuntu-touch-sounds udisks2 ufw unattended-upgrades unoconv
  unzip update-manager-core update-notifier-common upower upstart
  usb-creator-common usb-creator-kde usb-modeswitch usb-modeswitch-data
  usbmuxd usbutils user-manager uuid-runtime va-driver-all vdpau-va-driver
  vim-common vim-tiny vinagre whiptail whois whoopsie whoopsie-preferences
  wireless-regdb wpasupplicant x11-apps x11-session-utils x11-utils
  x11-xfs-utils x11-xkb-utils x11-xserver-utils xbrlapi xdg-user-dirs
  xfonts-100dpi xfonts-base xfonts-scalable xfonts-utils xorg-docs-core
  xserver-xorg-input-evdev xserver-xorg-input-vmmouse xserver-xorg-input-wacom
  xserver-xorg-video-ati xserver-xorg-video-cirrus xserver-xorg-video-mach64
  xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-nouveau xserver-xorg-video-qxl xserver-xorg-video-r128
  xserver-xorg-video-radeon xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-tdfx
  xserver-xorg-video-trident xserver-xorg-video-vesa xserver-xorg-video-vmware
  xul-ext-ubufox yelp yelp-xsl zeitgeist zeitgeist-datahub zenity
  zenity-common zip
1306 upgraded, 1 newly installed, 1 to remove and 115 not upgraded.
2 not fully installed or removed.
Need to get 0 B/644 MB of archives.
After this operation, 59.3 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 261640 files and directories currently installed.)
Preparing to unpack .../kde-config-telepathy-accounts_4%3a15.08.2-0ubuntu1_i386.deb ...
Unpacking kde-config-telepathy-accounts (4:15.08.2-0ubuntu1) over (0.9.0-0ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.08.2-0ubuntu1_i386.deb (--unpack):
 trying to overwrite '/usr/share/accounts/services/google-im.service', which is also in package account-plugin-google 0.12+15.04.20150415.1-0ubuntu2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to unpack .../libkf5archive5_5.15.0-0ubuntu1_i386.deb ...
Unpacking libkf5archive5:i386 (5.15.0-0ubuntu1) over (5.9.0-0ubuntu1) ...
Preparing to unpack .../libkf5emoticons-bin_5.15.0-0ubuntu1_i386.deb ...
Unpacking libkf5emoticons-bin (5.15.0-0ubuntu1) over (5.9.0-0ubuntu1) ...
Preparing to unpack .../libkf5emoticons5_5.15.0-0ubuntu1_i386.deb ...
Unpacking libkf5emoticons5:i386 (5.15.0-0ubuntu1) over (5.9.0-0ubuntu1) ...
Preparing to unpack .../libkf5emoticons-data_5.15.0-0ubuntu1_all.deb ...
Unpacking libkf5emoticons-data (5.15.0-0ubuntu1) over (5.9.0-0ubuntu1) ...
Preparing to unpack .../libkf5parts5_5.15.0-0ubuntu1_i386.deb ...
Unpacking libkf5parts5:i386 (5.15.0-0ubuntu1) over (5.9.0-0ubuntu1) ...
Preparing to unpack .../libkf5parts-data_5.15.0-0ubuntu1_all.deb ...
Unpacking libkf5parts-data (5.15.0-0ubuntu1) over (5.9.0-0ubuntu1) ...
Preparing to unpack .../libkf5webkit5_5.15.0-0ubuntu1_i386.deb ...
Unpacking libkf5webkit5:i386 (5.15.0-0ubuntu1) over (5.9.0-0ubuntu1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/kde-config-telepathy-accounts_4%3a15.08.2-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by erictherev on 2015-11-17
> **QIII said:**
> Yes you were and please don't.

Moved to its own thread from [here]("http://ubuntuforums.org/showthread.php?t=2301084").

Thanks for relocating this to the correct place.

---

