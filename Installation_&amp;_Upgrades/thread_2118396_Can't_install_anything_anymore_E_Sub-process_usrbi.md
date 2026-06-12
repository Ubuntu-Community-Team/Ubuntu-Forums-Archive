---
title: "Can't install anything anymore: E: Sub-process /usr/bin/dpkg returned an error code"
date: 2013-02-21
forum: Installation &amp; Upgrades
---

### Post by djibi on 2013-02-21
Hello,

I've a problem for a few weeks, I can't install anything anymore, I always have dependencies errors with LibreOffice, I think.
I created a bug report [here]("https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1045294"), but I do not get any answer, I'm then trying on Ubuntu Forums.
When I try to upgrade, I got the following terminal output:
```
$ sudo apt-get upgrade -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages have been kept back:
  ginn hplip hplip-data libgrip0 libhpmud0 libsane-hpaio libunity-2d-private0
  libunity-core-5.0-5 linux-generic-pae linux-headers-generic-pae
  linux-image-generic-pae printer-driver-hpcups printer-driver-hpijs unity
  unity-2d-common unity-2d-panel unity-2d-shell unity-2d-spread unity-common
  unity-services
The following packages will be upgraded:
  accountsservice activity-log-manager-common
  activity-log-manager-control-center apparmor appmenu-gtk appmenu-gtk3 apport
  apport-gtk apport-symptoms apt apt-transport-https apt-utils aptdaemon
  aptdaemon-data bamfdaemon bind9-host brasero brasero-cdrkit brasero-common
  build-essential busybox-static checkbox checkbox-qt colord compiz
  compiz-core compiz-gnome compiz-plugins-default cups cups-bsd cups-client
  cups-common cups-ppdc dbus dbus-x11 dconf-gsettings-backend dconf-service
  deja-dup dh-apparmor dnsutils dpkg-dev duplicity eog evince evince-common
  firefox firefox-globalmenu firefox-gnome-support firefox-locale-en
  fonts-opensymbol gcalctool gdb ghostscript ghostscript-cups ghostscript-x
  gir1.2-gtk-3.0 gir1.2-gudev-1.0 gir1.2-javascriptcoregtk-3.0
  gir1.2-launchpad-integration-3.0 gir1.2-rb-3.0 gir1.2-totem-1.0
  gir1.2-webkit-3.0 glib-networking glib-networking-common
  glib-networking-services gnome-accessibility-themes gnome-control-center
  gnome-control-center-data gnome-games-data gnome-media gnome-power-manager
  gnome-settings-daemon gnome-sudoku gnomine gnupg gpgv grub-common grub-pc
  grub-pc-bin grub2-common gstreamer0.10-gconf gstreamer0.10-plugins-good
  gstreamer0.10-pulseaudio gvfs gvfs-backends gvfs-bin gvfs-common
  gvfs-daemons gvfs-fuse gvfs-libs gwibber gwibber-service
  gwibber-service-facebook gwibber-service-identica gwibber-service-twitter
  im-switch indicator-messages indicator-sound indicator-status-provider-mc5
  isc-dhcp-client isc-dhcp-common jockey-common jockey-gtk
  landscape-client-ui-install language-pack-en language-pack-en-base
  language-pack-gnome-en language-pack-gnome-en-base language-selector-common
  language-selector-gnome launchpad-integration libaccountsservice0
  libapt-inst1.4 libapt-pkg4.12 libart-2.0-2 libbamf0 libbamf3-0 libbind9-80
  libbrasero-media3-1 libcolord1 libcups2 libcupscgi1 libcupsdriver1
  libcupsimage2 libcupsmime1 libcupsppdc1 libdconf-dbus-1-0 libdconf0
  libdecoration0 libdevmapper-event1.02.1 libdns81 libdpkg-perl
  libedataserverui-3.0-1 libevince3-3 libfreerdp-plugins-standard libfreerdp1
  libgail-3-0 libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libglu1-mesa
  libgnome-control-center1 libgnome2-common libgs9 libgs9-common libgtk-3-0
  libgtk-3-bin libgtk-3-common libgudev-1.0-0 libgwibber-gtk2 libgwibber2
  libindicator-messages-status-provider1 libisc83 libisccc80 libisccfg82
  libjavascriptcoregtk-3.0-0 liblaunchpad-integration-3.0-1
  liblaunchpad-integration-common libldap-2.4-2 liblightdm-gobject-1-0
  liblvm2app2.2 liblwres80 libmission-control-plugins0 libnautilus-extension1a
  libnm-glib-vpn1 libnm-glib4 libnm-util2 libnspr4 libnss3 libnux-2.0-0
  libnux-2.0-common liboverlay-scrollbar-0.2-0 liboverlay-scrollbar3-0.2-0
  libparted0debian1 libperl5.14 libpoppler-glib8 libpoppler19 libproxy1
  libproxy1-plugin-gsettings libproxy1-plugin-networkmanager
  libpulse-mainloop-glib0 libpulse0 libpulsedsp libpurple-bin libpurple0
  libqt4-dbus libqt4-declarative libqt4-network libqt4-opengl libqt4-script
  libqt4-sql libqt4-sql-sqlite libqt4-svg libqt4-xml libqt4-xmlpatterns
  libqtbamf1 libqtcore4 libqtgui4 libreoffice-base-core libreoffice-calc
  libreoffice-common libreoffice-core libreoffice-draw libreoffice-emailmerge
  libreoffice-gnome libreoffice-gtk libreoffice-help-en-us libreoffice-impress
  libreoffice-math libreoffice-style-human libreoffice-writer
  librhythmbox-core5 libsnmp-base libsnmp15 libssh-4 libtelepathy-glib0
  libtiff4 libtotem0 libwebkitgtk-3.0-0 libwebkitgtk-3.0-common libxatracker1
  libxcb-dri2-0 libxcb-glx0 libxcb-render0 libxcb-shape0 libxcb-shm0 libxcb1
  libxcb1-dev libxslt1.1 light-themes lightdm linux-firmware lsb-base
  lsb-release mahjongg make man-db multiarch-support nautilus nautilus-data
  network-manager ntfs-3g nux-tools nvidia-common onboard oneconf openssl
  overlay-scrollbar parted passwd perl perl-base perl-modules
  plymouth-theme-ubuntu-logo plymouth-theme-ubuntu-text policykit-1-gnome
  poppler-utils printer-driver-gutenprint printer-driver-ptouch pulseaudio
  pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-x11
  pulseaudio-utils python-apport python-aptdaemon python-aptdaemon.gtk3widgets
  python-aptdaemon.pkcompat python-crypto python-cupshelpers python-debtagshw
  python-gst0.10 python-keyring python-libproxy python-libxml2
  python-piston-mini-client python-problem-report python-software-properties
  python-ubuntu-sso-client python-ubuntuone-control-panel python-uno qdbus
  remmina remmina-common remmina-plugin-rdp remmina-plugin-vnc resolvconf
  rhythmbox rhythmbox-data rhythmbox-mozilla rhythmbox-plugin-cdrecorder
  rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist rhythmbox-plugins
  samba-common samba-common-bin seahorse sessioninstaller shotwell simple-scan
  smbclient software-center software-properties-common software-properties-gtk
  system-config-printer-common system-config-printer-gnome
  system-config-printer-udev telepathy-gabble telepathy-mission-control-5
  thunderbird thunderbird-globalmenu thunderbird-gnome-support totem
  totem-common totem-mozilla totem-plugins transmission-common
  transmission-gtk ubuntu-desktop ubuntu-docs ubuntu-keyring ubuntu-minimal
  ubuntu-sso-client ubuntu-sso-client-gtk ubuntu-standard
  ubuntuone-control-panel ubuntuone-installer udisks unattended-upgrades
  unity-2d unity-greeter unity-lens-applications unity-lens-music
  unity-lens-video unity-scope-musicstores unity-scope-video-remote uno-libs3
  update-manager update-manager-core update-notifier update-notifier-common
  ure vino wpasupplicant x11-common x11-utils xdiagnose xorg xserver-common
  xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all
  xserver-xorg-video-intel xserver-xorg-video-qxl xserver-xorg-video-vmware
  xterm xul-ext-ubufox xvfb zeitgeist zenity zenity-common
366 upgraded, 0 newly installed, 0 to remove and 20 not upgraded.
54 not fully installed or removed.
Need to get 0 B/297 MB of archives.
After this operation, 19.4 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: regarding .../libreoffice-core_1%3a3.5.7-0ubuntu4_i386.deb containing libreoffice-core:
 libreoffice-core conflicts with libreoffice-calc (<< 1:3.5.7-0ubuntu4)
  libreoffice-calc (version 1:3.5.4-0ubuntu1) is present and unpacked but not configured.
dpkg: error processing /var/cache/apt/archives/libreoffice-core_1%3a3.5.7-0ubuntu4_i386.deb (--unpack):
 conflicting packages - not installing libreoffice-core
No apport report written because MaxReports is reached already
                                                              (Reading database (Reading database ... 171098 files and directories currently installed.)
Preparing to replace perl 5.14.2-6ubuntu2 (using .../perl_5.14.2-6ubuntu2.2_i386.deb) ...
Unpacking replacement perl ...
Preparing to replace libperl5.14 5.14.2-6ubuntu2 (using .../libperl5.14_5.14.2-6ubuntu2.2_i386.deb) ...
Unpacking replacement libperl5.14 ...
Preparing to replace perl-base 5.14.2-6ubuntu2 (using .../perl-base_5.14.2-6ubuntu2.2_i386.deb) ...
Unpacking replacement perl-base ...
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-core_1%3a3.5.7-0ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Thank you for your help!
Best regards,
J-B

---

### Post by jdthood on 2013-02-21
First try ```
apt-get -f install
```.

---

### Post by djibi on 2013-02-22
I already tried a lot of such command and I do not think it will be solved without some dark magic I am asking here :)
Here is the result:
```
$ sudo apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core
  libreoffice-draw libreoffice-gnome libreoffice-gtk libreoffice-impress
  libreoffice-math libreoffice-writer perl-modules python-uno uno-libs3 ure
Suggested packages:
  libreoffice-base libreoffice-style-hicontrast libreoffice-style-tango
  libreoffice-style-crystal libreoffice-style-oxygen libreoffice-evolution
  libreoffice-gcj libreoffice-filter-binfilter default-jre gcj-jre
  java-gcj-compat openjdk-6-jre openjdk-7-jre sun-java5-jre sun-java6-jre
  java5-runtime jre libreoffice-java-common libpod-plainer-perl
The following packages will be upgraded:
  libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core
  libreoffice-draw libreoffice-gnome libreoffice-gtk libreoffice-impress
  libreoffice-math libreoffice-writer perl-modules python-uno uno-libs3 ure
14 upgraded, 0 newly installed, 0 to remove and 369 not upgraded.
57 not fully installed or removed.
Need to get 0 B/84.2 MB of archives.
After this operation, 164 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Setting up perl-base (5.14.2-6ubuntu2.2) ...
dpkg: regarding .../libreoffice-core_1%3a3.5.7-0ubuntu4_i386.deb containing libreoffice-core:
 libreoffice-core conflicts with libreoffice-calc (<< 1:3.5.7-0ubuntu4)
  libreoffice-calc (version 1:3.5.4-0ubuntu1) is present and unpacked but not configured.
dpkg: error processing /var/cache/apt/archives/libreoffice-core_1%3a3.5.7-0ubuntu4_i386.deb (--unpack):
 conflicting packages - not installing libreoffice-core
(Reading database ... 171098 files and directories currently installed.)
Preparing to replace perl-modules 5.14.2-6ubuntu2 (using .../perl-modules_5.14.2-6ubuntu2.2_all.deb) ...
Unpacking replacement perl-modules ...
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-core_1%3a3.5.7-0ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by djibi on 2013-02-25
Up!

---

### Post by matt_symes on 2013-02-25
Hi

Do you have any special ppas installed ?

Can you post the output of

```
grep -v ^# /etc/apt/sources.list /etc/apt/sources.list.d/*
```

Kind regards

---

### Post by malish on 2013-02-25
Hi,

The problem is a conflict between two different modules of libreoffice, maybe because of some version conflicts. So, remove all libreoffice packages 
```
sudo apt-get remove libreoffice*
```
or
```
sudo apt-get purge libreoffice*
```
and then try
```
sudo apt-get install -f
```
again.

Bests,
[m.a.sharpasand.com]("http://m.a.sharpasand.com/")

---

### Post by matt_symes on 2013-02-25
Hi

> The problem is a conflict between two different modules of libreoffice, maybe because of some version conflicts.

That is why it is best to check the sources before doing anything else though :)

Kind regards

---

### Post by malish on 2013-02-25
Yeah ;) you're right!

---

### Post by djibi on 2013-02-25
Hello,
First of all, thank you for your answers.
@matt_symes:
```
$ grep -v ^# /etc/apt/sources.list /etc/apt/sources.list.d/*
/etc/apt/sources.list:
/etc/apt/sources.list:deb http://fr.archive.ubuntu.com/ubuntu/ precise main restricted
/etc/apt/sources.list:deb-src http://fr.archive.ubuntu.com/ubuntu/ precise main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:deb http://fr.archive.ubuntu.com/ubuntu/ precise-updates main restricted
/etc/apt/sources.list:deb-src http://fr.archive.ubuntu.com/ubuntu/ precise-updates main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:deb http://fr.archive.ubuntu.com/ubuntu/ precise universe
/etc/apt/sources.list:deb-src http://fr.archive.ubuntu.com/ubuntu/ precise universe
/etc/apt/sources.list:deb http://fr.archive.ubuntu.com/ubuntu/ precise-updates universe
/etc/apt/sources.list:deb-src http://fr.archive.ubuntu.com/ubuntu/ precise-updates universe
/etc/apt/sources.list:
/etc/apt/sources.list:deb http://fr.archive.ubuntu.com/ubuntu/ precise multiverse
/etc/apt/sources.list:deb-src http://fr.archive.ubuntu.com/ubuntu/ precise multiverse
/etc/apt/sources.list:deb http://fr.archive.ubuntu.com/ubuntu/ precise-updates multiverse
/etc/apt/sources.list:deb-src http://fr.archive.ubuntu.com/ubuntu/ precise-updates multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:deb http://fr.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
/etc/apt/sources.list:deb-src http://fr.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu precise-security main restricted
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu precise-security universe
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu precise-security universe
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu precise-security multiverse
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu precise-security multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:
/etc/apt/sources.list:deb http://extras.ubuntu.com/ubuntu precise main
/etc/apt/sources.list:deb-src http://extras.ubuntu.com/ubuntu precise main
grep: /etc/apt/sources.list.d/*: No such file or directory

```

@malish
```
$ sudo apt-get purge libreoffice*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libreoffice-bundled' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-3.5' for regex 'libreoffice*'
Note, selecting 'libreoffice-presenter-console' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-pt-br' for regex 'libreoffice*'
Note, selecting 'libreoffice-presentation-minimizer' for regex 'libreoffice*'
Note, selecting 'libreoffice-spellcheck-fi' for regex 'libreoffice*'
Note, selecting 'libreoffice-dmaths' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-pt-br' for regex 'libreoffice*'
Note, selecting 'libreoffice-base' for regex 'libreoffice*'
Note, selecting 'libreoffice-spellcheck-tr' for regex 'libreoffice*'
Note, selecting 'libreoffice-dev-doc' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-andromeda' for regex 'libreoffice*'
Note, selecting 'libreoffice-zemberek' for regex 'libreoffice*'
Note, selecting 'libreoffice-calc' for regex 'libreoffice*'
Note, selecting 'libreoffice.org-writer' for regex 'libreoffice*'
Note, selecting 'mozilla-libreoffice' for regex 'libreoffice*'
Note, selecting 'libreoffice-gnome' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-af' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-be' for regex 'libreoffice*'
Note, selecting 'libreoffice-style' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ca' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-bg' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-da' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ar' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-bn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-as' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-de' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-br' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-bs' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-fa' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-cs' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ga' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-el' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-fi' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-eo' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-cy' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-es' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-he' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-et' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-eu' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-dz' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-gl' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-fr' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-id' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-hi' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ja' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ka' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-gu' for regex 'libreoffice*'
Note, selecting 'docvert-libreoffice' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-hr' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-hu' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-is' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-it' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-km' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ko' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-nb' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ne' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-mk' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ku' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ml' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-oc' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-mn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-lt' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-lv' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-nl' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-mr' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-nn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-nr' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-om' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-pl' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-or' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-pt' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ta' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-si' for regex 'libreoffice*'
Note, selecting 'libreoffice-script-provider-bsh' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-te' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ro' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-sk' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-tg' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-sl' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-th' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ru' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ug' for regex 'libreoffice*'
Note, selecting 'libreoffice-officebean' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-sr' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-rw' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-tn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ss' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ve' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-st' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-uk' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-sv' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-tr' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-vi' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ts' for regex 'libreoffice*'
Note, selecting 'libreoffice-emailmerge' for regex 'libreoffice*'
Note, selecting 'libreoffice-gtk-gnome' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-xh' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-zh-cn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-uz' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-zu' for regex 'libreoffice*'
Note, selecting 'libreoffice.org-calc' for regex 'libreoffice*'
Note, selecting 'libreoffice-core' for regex 'libreoffice*'
Note, selecting 'libreoffice-evolution' for regex 'libreoffice*'
Note, selecting 'libreoffice-pdfimport' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-zh-tw' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-zh-cn' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-ast' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-hicontrast' for regex 'libreoffice*'
Note, selecting 'libreoffice-writer' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-oxygen' for regex 'libreoffice*'
Note, selecting 'libreoffice-filter-mobiledev' for regex 'libreoffice*'
Note, selecting 'libreoffice-draw' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-zh-tw' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-en-gb' for regex 'libreoffice*'
Note, selecting 'libreoffice-filter-binfilter' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-en-us' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-en-za' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-en-gb' for regex 'libreoffice*'
Note, selecting 'libreoffice-base-core' for regex 'libreoffice*'
Note, selecting 'libreoffice-ogltrans' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-en-us' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-en-za' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-nso' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-af' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-be' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ca' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-bg' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-da' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ar' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-human' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-bn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-as' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-de' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-br' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-bs' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-fa' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-cs' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ga' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-el' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-industrial' for regex 'libreoffice*'
Note, selecting 'libreoffice-hyphenation-fi' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-fi' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-eo' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-cy' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-es' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-he' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-et' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-eu' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-dz' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-gl' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-fr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-id' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-hi' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ja' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ka' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-gu' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-hr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-in' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-hu' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-is' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-it' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-km' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ko' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-nb' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ne' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-mk' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ku' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ml' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-oc' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-mn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-lt' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-lv' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-nl' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-mr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-nn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-nr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-om' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-pl' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-or' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-pt' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ta' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-si' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ro' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-te' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-sk' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-tg' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-sl' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-th' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ru' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ug' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-sr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-rw' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-tn' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ss' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ve' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-st' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-uk' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-sv' for regex 'libreoffice*'
Note, selecting 'libreoffice-hyphenation-tr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-tr' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-vi' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ts' for regex 'libreoffice*'
Note, selecting 'libreoffice-gtk3' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-xh' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-za' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-uz' for regex 'libreoffice*'
Note, selecting 'libreoffice-filter-so52' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-zu' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-crystal' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-3.5' for regex 'libreoffice*'
Note, selecting 'libreoffice-writer2latex' for regex 'libreoffice*'
Note, selecting 'libreoffice-script-provider-python' for regex 'libreoffice*'
Note, selecting 'libreoffice-writer2xhtml' for regex 'libreoffice*'
Note, selecting 'libreoffice-impress' for regex 'libreoffice*'
Note, selecting 'libreoffice-nlpsolver' for regex 'libreoffice*'
Note, selecting 'libreoffice-dtd-officedocument1.0' for regex 'libreoffice*'
Note, selecting 'libreoffice-java-common' for regex 'libreoffice*'
Note, selecting 'libreoffice-mysql-connector' for regex 'libreoffice*'
Note, selecting 'openclipart-libreoffice' for regex 'libreoffice*'
Note, selecting 'libreoffice-math' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-ast' for regex 'libreoffice*'
Note, selecting 'libreoffice' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-galaxy' for regex 'libreoffice*'
Note, selecting 'libreoffice-sdbc-postgresql' for regex 'libreoffice*'
Note, selecting 'libreoffice-script-provider-js' for regex 'libreoffice*'
Note, selecting 'libreoffice-common' for regex 'libreoffice*'
Note, selecting 'libreoffice-dbg' for regex 'libreoffice*'
Note, selecting 'libreoffice-dev' for regex 'libreoffice*'
Note, selecting 'libreoffice-voikko' for regex 'libreoffice*'
Note, selecting 'libreoffice-gcj' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-nso' for regex 'libreoffice*'
Note, selecting 'libreoffice-l10n-pa-in' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-tango' for regex 'libreoffice*'
Note, selecting 'libreoffice-kab' for regex 'libreoffice*'
Note, selecting 'libreoffice-gtk' for regex 'libreoffice*'
Note, selecting 'libreoffice-wiki-publisher' for regex 'libreoffice*'
Note, selecting 'libreoffice-kde' for regex 'libreoffice*'
Note, selecting 'libreoffice-help-pa-in' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-default' for regex 'libreoffice*'
Note, selecting 'libreoffice-style-human' instead of 'libreoffice-style-default'
Note, selecting 'libreoffice-common' instead of 'libreoffice-l10n-en-us'
Note, selecting 'libreoffice-core' instead of 'libreoffice-bundled'
Note, selecting 'openoffice.org-dtd-officedocument1.0' instead of 'libreoffice-dtd-officedocument1.0'
Note, selecting 'libreoffice-gnome' instead of 'libreoffice-gtk-gnome'
Note, selecting 'libreoffice-voikko' instead of 'libreoffice-spellcheck-fi'
Note, selecting 'libreoffice-zemberek' instead of 'libreoffice-spellcheck-tr'
Note, selecting 'libreoffice-voikko' instead of 'libreoffice-hyphenation-fi'
Note, selecting 'libreoffice-zemberek' instead of 'libreoffice-hyphenation-tr'
Package libreoffice-nlpsolver is not installed, so not removed
Package libreoffice-voikko is not installed, so not removed
Package docvert-libreoffice is not installed, so not removed
Package libreoffice-dmaths is not installed, so not removed
Package libreoffice-writer2latex is not installed, so not removed
Package libreoffice-writer2xhtml is not installed, so not removed
Package libreoffice-zemberek is not installed, so not removed
Package openclipart-libreoffice is not installed, so not removed
Package libreoffice is not installed, so not removed
Package libreoffice-base is not installed, so not removed
Package libreoffice-dbg is not installed, so not removed
Package libreoffice-dev is not installed, so not removed
Package libreoffice-dev-doc is not installed, so not removed
Package libreoffice-evolution is not installed, so not removed
Package libreoffice-filter-binfilter is not installed, so not removed
Package libreoffice-filter-mobiledev is not installed, so not removed
Package libreoffice-help-ca is not installed, so not removed
Package libreoffice-help-cs is not installed, so not removed
Package libreoffice-help-da is not installed, so not removed
Package libreoffice-help-de is not installed, so not removed
Package libreoffice-help-dz is not installed, so not removed
Package libreoffice-help-el is not installed, so not removed
Package libreoffice-help-en-gb is not installed, so not removed
Package libreoffice-help-es is not installed, so not removed
Package libreoffice-help-et is not installed, so not removed
Package libreoffice-help-eu is not installed, so not removed
Package libreoffice-help-fi is not installed, so not removed
Package libreoffice-help-fr is not installed, so not removed
Package libreoffice-help-gl is not installed, so not removed
Package libreoffice-help-hi is not installed, so not removed
Package libreoffice-help-hu is not installed, so not removed
Package libreoffice-help-it is not installed, so not removed
Package libreoffice-help-ja is not installed, so not removed
Package libreoffice-help-km is not installed, so not removed
Package libreoffice-help-ko is not installed, so not removed
Package libreoffice-help-nl is not installed, so not removed
Package libreoffice-help-om is not installed, so not removed
Package libreoffice-help-pl is not installed, so not removed
Package libreoffice-help-pt is not installed, so not removed
Package libreoffice-help-pt-br is not installed, so not removed
Package libreoffice-help-ru is not installed, so not removed
Package libreoffice-help-sk is not installed, so not removed
Package libreoffice-help-sl is not installed, so not removed
Package libreoffice-help-sv is not installed, so not removed
Package libreoffice-help-zh-cn is not installed, so not removed
Package libreoffice-help-zh-tw is not installed, so not removed
Package libreoffice-java-common is not installed, so not removed
Package libreoffice-kde is not installed, so not removed
Package libreoffice-l10n-af is not installed, so not removed
Package libreoffice-l10n-ar is not installed, so not removed
Package libreoffice-l10n-as is not installed, so not removed
Package libreoffice-l10n-ast is not installed, so not removed
Package libreoffice-l10n-be is not installed, so not removed
Package libreoffice-l10n-bg is not installed, so not removed
Package libreoffice-l10n-bn is not installed, so not removed
Package libreoffice-l10n-br is not installed, so not removed
Package libreoffice-l10n-bs is not installed, so not removed
Package libreoffice-l10n-ca is not installed, so not removed
Package libreoffice-l10n-cs is not installed, so not removed
Package libreoffice-l10n-cy is not installed, so not removed
Package libreoffice-l10n-da is not installed, so not removed
Package libreoffice-l10n-de is not installed, so not removed
Package libreoffice-l10n-dz is not installed, so not removed
Package libreoffice-l10n-el is not installed, so not removed
Package libreoffice-l10n-en-gb is not installed, so not removed
Package libreoffice-l10n-en-za is not installed, so not removed
Package libreoffice-l10n-eo is not installed, so not removed
Package libreoffice-l10n-es is not installed, so not removed
Package libreoffice-l10n-et is not installed, so not removed
Package libreoffice-l10n-eu is not installed, so not removed
Package libreoffice-l10n-fa is not installed, so not removed
Package libreoffice-l10n-fi is not installed, so not removed
Package libreoffice-l10n-fr is not installed, so not removed
Package libreoffice-l10n-ga is not installed, so not removed
Package libreoffice-l10n-gl is not installed, so not removed
Package libreoffice-l10n-gu is not installed, so not removed
Package libreoffice-l10n-he is not installed, so not removed
Package libreoffice-l10n-hi is not installed, so not removed
Package libreoffice-l10n-hr is not installed, so not removed
Package libreoffice-l10n-hu is not installed, so not removed
Package libreoffice-l10n-id is not installed, so not removed
Package libreoffice-l10n-in is not installed, so not removed
Package libreoffice-l10n-is is not installed, so not removed
Package libreoffice-l10n-it is not installed, so not removed
Package libreoffice-l10n-ja is not installed, so not removed
Package libreoffice-l10n-ka is not installed, so not removed
Package libreoffice-l10n-km is not installed, so not removed
Package libreoffice-l10n-ko is not installed, so not removed
Package libreoffice-l10n-ku is not installed, so not removed
Package libreoffice-l10n-lt is not installed, so not removed
Package libreoffice-l10n-lv is not installed, so not removed
Package libreoffice-l10n-mk is not installed, so not removed
Package libreoffice-l10n-ml is not installed, so not removed
Package libreoffice-l10n-mn is not installed, so not removed
Package libreoffice-l10n-mr is not installed, so not removed
Package libreoffice-l10n-nb is not installed, so not removed
Package libreoffice-l10n-ne is not installed, so not removed
Package libreoffice-l10n-nl is not installed, so not removed
Package libreoffice-l10n-nn is not installed, so not removed
Package libreoffice-l10n-nr is not installed, so not removed
Package libreoffice-l10n-nso is not installed, so not removed
Package libreoffice-l10n-oc is not installed, so not removed
Package libreoffice-l10n-om is not installed, so not removed
Package libreoffice-l10n-or is not installed, so not removed
Package libreoffice-l10n-pa-in is not installed, so not removed
Package libreoffice-l10n-pl is not installed, so not removed
Package libreoffice-l10n-pt is not installed, so not removed
Package libreoffice-l10n-pt-br is not installed, so not removed
Package libreoffice-l10n-ro is not installed, so not removed
Package libreoffice-l10n-ru is not installed, so not removed
Package libreoffice-l10n-rw is not installed, so not removed
Package libreoffice-l10n-si is not installed, so not removed
Package libreoffice-l10n-sk is not installed, so not removed
Package libreoffice-l10n-sl is not installed, so not removed
Package libreoffice-l10n-sr is not installed, so not removed
Package libreoffice-l10n-ss is not installed, so not removed
Package libreoffice-l10n-st is not installed, so not removed
Package libreoffice-l10n-sv is not installed, so not removed
Package libreoffice-l10n-ta is not installed, so not removed
Package libreoffice-l10n-te is not installed, so not removed
Package libreoffice-l10n-tg is not installed, so not removed
Package libreoffice-l10n-th is not installed, so not removed
Package libreoffice-l10n-tn is not installed, so not removed
Package libreoffice-l10n-tr is not installed, so not removed
Package libreoffice-l10n-ts is not installed, so not removed
Package libreoffice-l10n-ug is not installed, so not removed
Package libreoffice-l10n-uk is not installed, so not removed
Package libreoffice-l10n-uz is not installed, so not removed
Package libreoffice-l10n-ve is not installed, so not removed
Package libreoffice-l10n-vi is not installed, so not removed
Package libreoffice-l10n-xh is not installed, so not removed
Package libreoffice-l10n-za is not installed, so not removed
Package libreoffice-l10n-zh-cn is not installed, so not removed
Package libreoffice-l10n-zh-tw is not installed, so not removed
Package libreoffice-l10n-zu is not installed, so not removed
Package libreoffice-officebean is not installed, so not removed
Package libreoffice-style-oxygen is not installed, so not removed
Package libreoffice-style-tango is not installed, so not removed
Package libreoffice-gtk3 is not installed, so not removed
Package libreoffice-mysql-connector is not installed, so not removed
Package libreoffice-ogltrans is not installed, so not removed
Package libreoffice-pdfimport is not installed, so not removed
Package libreoffice-presentation-minimizer is not installed, so not removed
Package libreoffice-presenter-console is not installed, so not removed
Package libreoffice-script-provider-bsh is not installed, so not removed
Package libreoffice-script-provider-js is not installed, so not removed
Package libreoffice-sdbc-postgresql is not installed, so not removed
Package libreoffice-style-crystal is not installed, so not removed
Package libreoffice-style-galaxy is not installed, so not removed
Package libreoffice-style-hicontrast is not installed, so not removed
Package libreoffice-wiki-publisher is not installed, so not removed
Package mozilla-libreoffice is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 python-uno : Depends: libreoffice-core (= 1:3.5.4-0ubuntu1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```
FYI, I think I broke my system by using [APT-Offline]("http://apt-offline.alioth.debian.org/") because I didn't have internet connexion to update my system...

---

### Post by matt_symes on 2013-02-25
Hi

APT-Offline may have done it. Your sources are fine and they are where most version issues come from.

Can you post the output of

```
dpkg -l libreoffice-calc
```

and after try 

```
sudo apt-get install -f
```

If the apt-get command fails then post its output.

Kind regards

---

### Post by djibi on 2013-02-25
```
$ dpkg -l libreoffice-calc
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
iU  libreoffice-ca 1:3.5.4-0ubunt office productivity suite -- spreadsheet

```

```
$ sudo apt-get install -f
[sudo] password for feronjb: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core
  libreoffice-draw libreoffice-gnome libreoffice-gtk libreoffice-impress
  libreoffice-math libreoffice-writer python-uno uno-libs3 ure
Suggested packages:
  libreoffice-base libreoffice-style-hicontrast libreoffice-style-tango
  libreoffice-style-crystal libreoffice-style-oxygen libreoffice-evolution
  libreoffice-gcj libreoffice-filter-binfilter default-jre gcj-jre
  java-gcj-compat openjdk-6-jre openjdk-7-jre sun-java5-jre sun-java6-jre
  java5-runtime jre libreoffice-java-common
The following packages will be upgraded:
  libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core
  libreoffice-draw libreoffice-gnome libreoffice-gtk libreoffice-impress
  libreoffice-math libreoffice-writer python-uno uno-libs3 ure
13 upgraded, 0 newly installed, 0 to remove and 373 not upgraded.
57 not fully installed or removed.
Need to get 0 B/80.8 MB of archives.
After this operation, 163 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
dpkg: regarding .../libreoffice-core_1%3a3.5.7-0ubuntu4_i386.deb containing libreoffice-core:
 libreoffice-core conflicts with libreoffice-calc (<< 1:3.5.7-0ubuntu4)
  libreoffice-calc (version 1:3.5.4-0ubuntu1) is present and unpacked but not configured.
dpkg: error processing /var/cache/apt/archives/libreoffice-core_1%3a3.5.7-0ubuntu4_i386.deb (--unpack):
 conflicting packages - not installing libreoffice-core
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-core_1%3a3.5.7-0ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by matt_symes on 2013-02-25
Hi

This is the problem package.

```
sudo dpkg -P libreoffice-calc
``````
sudo apt-get install -f
```

If either fail post back output

Kind regards

---

### Post by djibi on 2013-02-25
First the results which are not OK:
```
$ sudo dpkg -P libreoffice-calc
(Reading database ... 171097 files and directories currently installed.)
Removing libreoffice-calc ...
Purging configuration files for libreoffice-calc ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
```

```
$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libreoffice-base-core libreoffice-common libreoffice-core libreoffice-draw
  libreoffice-gnome libreoffice-gtk libreoffice-impress libreoffice-math
  libreoffice-writer python-uno uno-libs3 ure
Suggested packages:
  libreoffice-base libreoffice-style-hicontrast libreoffice-style-tango
  libreoffice-style-crystal libreoffice-style-oxygen libreoffice-evolution
  libreoffice-gcj libreoffice-filter-binfilter default-jre gcj-jre
  java-gcj-compat openjdk-6-jre openjdk-7-jre sun-java5-jre sun-java6-jre
  java5-runtime jre libreoffice-java-common
The following packages will be upgraded:
  libreoffice-base-core libreoffice-common libreoffice-core libreoffice-draw
  libreoffice-gnome libreoffice-gtk libreoffice-impress libreoffice-math
  libreoffice-writer python-uno uno-libs3 ure
12 upgraded, 0 newly installed, 0 to remove and 373 not upgraded.
56 not fully installed or removed.
Need to get 0 B/74.5 MB of archives.
After this operation, 153 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
dpkg: regarding .../libreoffice-core_1%3a3.5.7-0ubuntu4_i386.deb containing libreoffice-core:
 libreoffice-core conflicts with libreoffice-draw (<< 1:3.5.7-0ubuntu4)
  libreoffice-draw (version 1:3.5.4-0ubuntu1) is present and unpacked but not configured.
dpkg: error processing /var/cache/apt/archives/libreoffice-core_1%3a3.5.7-0ubuntu4_i386.deb (--unpack):
 conflicting packages - not installing libreoffice-core
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-core_1%3a3.5.7-0ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Next, I have a question to understand how you are proceeding:
How do you know that the libreoffice-calc package is the problem?

Thanks for your help!

---

### Post by matt_symes on 2013-02-25
Hi

```
sudo dpkg -P libreoffice-core
```

```
sudo apt-get remove --purge libreoffice
```
> 
Next, I have a question to understand how you are proceeding:
How do you know that the libreoffice-calc package is the problem?

It was one of the conflicting packages. I'm going through all the conflicting packages for you :D

I really hoping it's just libreoffice that this has happened to.

Kind regards

---

### Post by djibi on 2013-02-25
```
$ sudo dpkg -P libreoffice-core
dpkg: dependency problems prevent removal of libreoffice-core:
 libreoffice-emailmerge depends on libreoffice-core; however:
  Package libreoffice-core is to be removed.
dpkg: error processing libreoffice-core (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 libreoffice-core
```

```
$sudo apt-get remove --purge libreoffice
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libreoffice is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libreoffice-base-core : Depends: libreoffice-core (= 1:3.5.4-0ubuntu1) but 1:3.5.2-2ubuntu1 is to be installed
 libreoffice-draw : Depends: libreoffice-core (= 1:3.5.4-0ubuntu1) but 1:3.5.2-2ubuntu1 is to be installed
 libreoffice-gnome : Depends: libreoffice-core (= 1:3.5.4-0ubuntu1) but 1:3.5.2-2ubuntu1 is to be installed
 libreoffice-gtk : Depends: libreoffice-core (= 1:3.5.4-0ubuntu1) but 1:3.5.2-2ubuntu1 is to be installed
                   Recommends: libreoffice-style-tango but it is not going to be installed
 libreoffice-impress : Depends: libreoffice-core (= 1:3.5.4-0ubuntu1) but 1:3.5.2-2ubuntu1 is to be installed
 libreoffice-math : Depends: libreoffice-core (= 1:3.5.4-0ubuntu1) but 1:3.5.2-2ubuntu1 is to be installed
 libreoffice-writer : Depends: libreoffice-core (= 1:3.5.4-0ubuntu1) but 1:3.5.2-2ubuntu1 is to be installed
 python-uno : Depends: libreoffice-core (= 1:3.5.4-0ubuntu1) but 1:3.5.2-2ubuntu1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

```
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libreoffice-base-core libreoffice-common libreoffice-core libreoffice-draw
  libreoffice-gnome libreoffice-gtk libreoffice-impress libreoffice-math
  libreoffice-writer python-uno uno-libs3 ure
Suggested packages:
  libreoffice-base libreoffice-style-hicontrast libreoffice-style-tango
  libreoffice-style-crystal libreoffice-style-oxygen libreoffice-evolution
  libreoffice-gcj libreoffice-filter-binfilter default-jre gcj-jre
  java-gcj-compat openjdk-6-jre openjdk-7-jre sun-java5-jre sun-java6-jre
  java5-runtime jre libreoffice-java-common
The following packages will be upgraded:
  libreoffice-base-core libreoffice-common libreoffice-core libreoffice-draw
  libreoffice-gnome libreoffice-gtk libreoffice-impress libreoffice-math
  libreoffice-writer python-uno uno-libs3 ure
12 upgraded, 0 newly installed, 0 to remove and 373 not upgraded.
56 not fully installed or removed.
Need to get 0 B/74.5 MB of archives.
After this operation, 153 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Selecting previously unselected package libreoffice-core.
dpkg: regarding .../libreoffice-core_1%3a3.5.7-0ubuntu4_i386.deb containing libreoffice-core:
 libreoffice-core conflicts with libreoffice-draw (<< 1:3.5.7-0ubuntu4)
  libreoffice-draw (version 1:3.5.4-0ubuntu1) is present and unpacked but not configured.
dpkg: error processing /var/cache/apt/archives/libreoffice-core_1%3a3.5.7-0ubuntu4_i386.deb (--unpack):
 conflicting packages - not installing libreoffice-core
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-core_1%3a3.5.7-0ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
:confused::confused::confused:

---

### Post by schragge on 2013-02-25
Hmm, I wonder wouldn't *sudo apt-get dist-upgrade* help here? *apt-get upgrade* tries hard not to remove any packages, *apt-get dist-upgrade* doesn't have this restriction.

---

### Post by djibi on 2013-02-25
```
$ sudo apt-get -f dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  libframe6 libgeis1 libgrail5 linux-headers-3.2.0-38
  linux-headers-3.2.0-38-generic-pae linux-image-3.2.0-38-generic-pae
  printer-driver-postscript-hp
The following packages will be upgraded:
  accountsservice activity-log-manager-common
  activity-log-manager-control-center apparmor appmenu-gtk appmenu-gtk3 apport
  apport-gtk apport-symptoms apt apt-transport-https apt-utils aptdaemon
  aptdaemon-data bamfdaemon bind9-host brasero brasero-cdrkit brasero-common
  build-essential busybox-static checkbox checkbox-qt colord compiz
  compiz-core compiz-gnome compiz-plugins-default cups cups-bsd cups-client
  cups-common cups-ppdc dbus dbus-x11 dconf-gsettings-backend dconf-service
  deja-dup dh-apparmor dnsutils dpkg-dev duplicity eog evince evince-common
  firefox firefox-globalmenu firefox-gnome-support firefox-locale-en
  fonts-opensymbol gcalctool gdb ghostscript ghostscript-cups ghostscript-x
  ginn gir1.2-gtk-3.0 gir1.2-gudev-1.0 gir1.2-javascriptcoregtk-3.0
  gir1.2-launchpad-integration-3.0 gir1.2-rb-3.0 gir1.2-totem-1.0
  gir1.2-webkit-3.0 glib-networking glib-networking-common
  glib-networking-services gnome-accessibility-themes gnome-control-center
  gnome-control-center-data gnome-games-data gnome-media gnome-power-manager
  gnome-settings-daemon gnome-sudoku gnomine gnupg gpgv grub-common grub-pc
  grub-pc-bin grub2-common gstreamer0.10-gconf gstreamer0.10-plugins-good
  gstreamer0.10-pulseaudio gvfs gvfs-backends gvfs-bin gvfs-common
  gvfs-daemons gvfs-fuse gvfs-libs gwibber gwibber-service
  gwibber-service-facebook gwibber-service-identica gwibber-service-twitter
  hplip hplip-data im-switch indicator-messages indicator-sound
  indicator-status-provider-mc5 isc-dhcp-client isc-dhcp-common jockey-common
  jockey-gtk landscape-client-ui-install language-pack-en
  language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base
  language-selector-common language-selector-gnome launchpad-integration
  libaccountsservice0 libapt-inst1.4 libapt-pkg4.12 libart-2.0-2 libbamf0
  libbamf3-0 libbind9-80 libbrasero-media3-1 libcolord1 libcups2 libcupscgi1
  libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1 libdconf-dbus-1-0
  libdconf0 libdecoration0 libdevmapper-event1.02.1 libdns81 libdpkg-perl
  libedataserverui-3.0-1 libevince3-3 libfreerdp-plugins-standard libfreerdp1
  libgail-3-0 libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libglu1-mesa
  libgnome-control-center1 libgnome2-common libgrip0 libgs9 libgs9-common
  libgtk-3-0 libgtk-3-bin libgtk-3-common libgudev-1.0-0 libgwibber-gtk2
  libgwibber2 libhpmud0 libindicator-messages-status-provider1 libisc83
  libisccc80 libisccfg82 libjavascriptcoregtk-3.0-0
  liblaunchpad-integration-3.0-1 liblaunchpad-integration-common libldap-2.4-2
  liblightdm-gobject-1-0 liblvm2app2.2 liblwres80 libmission-control-plugins0
  libnautilus-extension1a libnm-glib-vpn1 libnm-glib4 libnm-util2 libnspr4
  libnss3 libnux-2.0-0 libnux-2.0-common liboverlay-scrollbar-0.2-0
  liboverlay-scrollbar3-0.2-0 libparted0debian1 libpoppler-glib8 libpoppler19
  libproxy1 libproxy1-plugin-gsettings libproxy1-plugin-networkmanager
  libpulse-mainloop-glib0 libpulse0 libpulsedsp libpurple-bin libpurple0
  libqt4-dbus libqt4-declarative libqt4-network libqt4-opengl libqt4-script
  libqt4-sql libqt4-sql-sqlite libqt4-svg libqt4-xml libqt4-xmlpatterns
  libqtbamf1 libqtcore4 libqtgui4 libreoffice-base-core libreoffice-common
  libreoffice-core libreoffice-draw libreoffice-emailmerge libreoffice-gnome
  libreoffice-gtk libreoffice-help-en-us libreoffice-impress libreoffice-math
  libreoffice-style-human libreoffice-writer librhythmbox-core5 libsane-hpaio
  libsnmp-base libsnmp15 libssh-4 libssl-dev libssl-doc libssl1.0.0
  libtelepathy-glib0 libtiff4 libtotem0 libunity-2d-private0
  libunity-core-5.0-5 libwebkitgtk-3.0-0 libwebkitgtk-3.0-common libxatracker1
  libxcb-dri2-0 libxcb-glx0 libxcb-render0 libxcb-shape0 libxcb-shm0 libxcb1
  libxcb1-dev libxslt1.1 light-themes lightdm linux-firmware linux-generic-pae
  linux-headers-generic-pae linux-image-generic-pae linux-libc-dev lsb-base
  lsb-release mahjongg make man-db multiarch-support nautilus nautilus-data
  network-manager ntfs-3g nux-tools nvidia-common onboard oneconf openssl
  overlay-scrollbar parted passwd plymouth-theme-ubuntu-logo
  plymouth-theme-ubuntu-text policykit-1-gnome poppler-utils
  printer-driver-gutenprint printer-driver-hpcups printer-driver-hpijs
  printer-driver-ptouch pulseaudio pulseaudio-module-bluetooth
  pulseaudio-module-gconf pulseaudio-module-x11 pulseaudio-utils python-apport
  python-aptdaemon python-aptdaemon.gtk3widgets python-aptdaemon.pkcompat
  python-crypto python-cupshelpers python-debtagshw python-gst0.10
  python-keyring python-libproxy python-libxml2 python-piston-mini-client
  python-problem-report python-software-properties python-ubuntu-sso-client
  python-ubuntuone-control-panel python-uno qdbus remmina remmina-common
  remmina-plugin-rdp remmina-plugin-vnc resolvconf rhythmbox rhythmbox-data
  rhythmbox-mozilla rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune
  rhythmbox-plugin-zeitgeist rhythmbox-plugins samba-common samba-common-bin
  seahorse sessioninstaller shotwell simple-scan smbclient software-center
  software-properties-common software-properties-gtk
  system-config-printer-common system-config-printer-gnome
  system-config-printer-udev telepathy-gabble telepathy-mission-control-5
  thunderbird thunderbird-globalmenu thunderbird-gnome-support totem
  totem-common totem-mozilla totem-plugins transmission-common
  transmission-gtk ubuntu-desktop ubuntu-docs ubuntu-keyring ubuntu-minimal
  ubuntu-sso-client ubuntu-sso-client-gtk ubuntu-standard
  ubuntuone-control-panel ubuntuone-installer udisks unattended-upgrades unity
  unity-2d unity-2d-common unity-2d-panel unity-2d-shell unity-2d-spread
  unity-common unity-greeter unity-lens-applications unity-lens-music
  unity-lens-video unity-scope-musicstores unity-scope-video-remote
  unity-services uno-libs3 update-manager update-manager-core update-notifier
  update-notifier-common ure vino wpasupplicant x11-common x11-utils xdiagnose
  xorg xserver-common xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all
  xserver-xorg-video-intel xserver-xorg-video-qxl xserver-xorg-video-vmware
  xterm xul-ext-ubufox xvfb zeitgeist zenity zenity-common
385 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
56 not fully installed or removed.
Need to get 67.0 MB/348 MB of archives.
After this operation, 202 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main libssl-doc all 1.0.1-4ubuntu5.6 [1,036 kB]
Get:2 http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main libssl-dev i386 1.0.1-4ubuntu5.6 [1,422 kB]
Get:3 http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main libssl1.0.0 i386 1.0.1-4ubuntu5.6 [1,009 kB]
Get:4 http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main linux-libc-dev i386 3.2.0-38.61 [862 kB]
Get:5 http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main libframe6 i386 2.2.4-0ubuntu0.12.04.1 [41.9 kB]
Get:6 http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main libgrail5 i386 3.0.6-0ubuntu0.12.04.01 [64.1 kB]
Get:7 http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main linux-image-3.2.0-38-generic-pae i386 3.2.0-38.61 [38.2 MB]
Get:8 http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main libgeis1 i386 2.2.9.2-0ubuntu1 [66.3 kB]
Get:9 http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main openssl i386 1.0.1-4ubuntu5.6 [520 kB]
Get:10 http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main unity i386 5.18.0-0ubuntu2 [1,293 kB]
Get:11 http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main libunity-core-5.0-5 i386 5.18.0-0ubuntu2 [235 kB]
Get:12 http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main unity-services i386 5.18.0-0ubuntu2 [34.8 kB]
Get:13 http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main unity-common all 5.18.0-0ubuntu2 [146 kB]
Get:14 http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main libgrip0 i386 0.3.5-0ubuntu1~12.04.1 [16.0 kB]
Get:15 http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main printer-driver-hpijs i386 3.12.2-1ubuntu3.1 [361 kB]
Get:16 http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main libsane-hpaio i386 3.12.2-1ubuntu3.1 [130 kB]
Get:17 http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main hplip i386 3.12.2-1ubuntu3.1 [86.8 kB]
Get:18 http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main libhpmud0 i386 3.12.2-1ubuntu3.1 [117 kB]
Get:19 http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main hplip-data all 3.12.2-1ubuntu3.1 [6,667 kB]
Get:20 http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main printer-driver-hpcups i386 3.12.2-1ubuntu3.1 [303 kB]
Get:21 http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main unity-2d-shell i386 5.12.0-0ubuntu1.2 [277 kB]
Get:22 http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main unity-2d-panel i386 5.12.0-0ubuntu1.2 [130 kB]
Get:23 http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main unity-2d-spread i386 5.12.0-0ubuntu1.2 [33.0 kB]
Get:24 http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main unity-2d-common all 5.12.0-0ubuntu1.2 [11.2 kB]
Get:25 http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main libunity-2d-private0 i386 5.12.0-0ubuntu1.2 [477 kB]
Get:26 http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main linux-generic-pae i386 3.2.0.38.46 [1,728 B]
Get:27 http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main linux-image-generic-pae i386 3.2.0.38.46 [2,616 B]
Get:28 http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.2.0-38 all 3.2.0-38.61 [11.7 MB]
Get:29 http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.2.0-38-generic-pae i386 3.2.0-38.61 [981 kB]
Get:30 http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-generic-pae i386 3.2.0.38.46 [2,602 B]
Get:31 http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main printer-driver-postscript-hp all 3.12.2-1ubuntu3.1 [785 kB]
Get:32 http://fr.archive.ubuntu.com/ubuntu/ precise-updates/main ginn i386 0.2.4.1-0ubuntu1 [15.5 kB]
Fetched 67.0 MB in 9min 1s (124 kB/s)                                          
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 171073 files and directories currently installed.)
Preparing to replace libssl1.0.0 1.0.1-4ubuntu5.5 (using .../libssl1.0.0_1.0.1-4ubuntu5.6_i386.deb) ...
Unpacking replacement libssl1.0.0 ...
Setting up libssl1.0.0 (1.0.1-4ubuntu5.6) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
dpkg: regarding .../libreoffice-core_1%3a3.5.7-0ubuntu4_i386.deb containing libreoffice-core:
 libreoffice-core conflicts with libreoffice-draw (<< 1:3.5.7-0ubuntu4)
  libreoffice-draw (version 1:3.5.4-0ubuntu1) is present and unpacked but not configured.
dpkg: error processing /var/cache/apt/archives/libreoffice-core_1%3a3.5.7-0ubuntu4_i386.deb (--unpack):
 conflicting packages - not installing libreoffice-core
(Reading database ... 171073 files and directories currently installed.)
Preparing to replace libapt-pkg4.12 0.8.16~exp12ubuntu10.2 (using .../libapt-pkg4.12_0.8.16~exp12ubuntu10.7_i386.deb) ...
Unpacking replacement libapt-pkg4.12 ...
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-core_1%3a3.5.7-0ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by matt_symes on 2013-02-25
Hi

Let's try a slightly different approach. There many be milege in the dist-upgrade approach especially as your sources are fine. If your sources were mixed i would not want to try it.

Your package system is a bit shot.

Let's clean out the cache as that is causing problems now.
```
sudo apt-get clean
```

.. And then pull all new packages down and see where it takes us.
```
sudo apt-get dist-upgrade
```Kind regards

---

### Post by djibi on 2013-02-25
```
$ sudo apt-get clean
$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libreoffice-base-core : Depends: libreoffice-core (= 1:3.5.4-0ubuntu1) but 1:3.5.2-2ubuntu1 is installed
 libreoffice-draw : Depends: libreoffice-core (= 1:3.5.4-0ubuntu1) but 1:3.5.2-2ubuntu1 is installed
 libreoffice-gnome : Depends: libreoffice-core (= 1:3.5.4-0ubuntu1) but 1:3.5.2-2ubuntu1 is installed
 libreoffice-gtk : Depends: libreoffice-core (= 1:3.5.4-0ubuntu1) but 1:3.5.2-2ubuntu1 is installed
                   Recommends: libreoffice-style-tango but it is not installed
 libreoffice-impress : Depends: libreoffice-core (= 1:3.5.4-0ubuntu1) but 1:3.5.2-2ubuntu1 is installed
 libreoffice-math : Depends: libreoffice-core (= 1:3.5.4-0ubuntu1) but 1:3.5.2-2ubuntu1 is installed
 libreoffice-writer : Depends: libreoffice-core (= 1:3.5.4-0ubuntu1) but 1:3.5.2-2ubuntu1 is installed
 libssl-dev : Depends: libssl1.0.0 (= 1.0.1-4ubuntu5.5) but 1.0.1-4ubuntu5.6 is installed
 python-uno : Depends: libreoffice-core (= 1:3.5.4-0ubuntu1) but 1:3.5.2-2ubuntu1 is installed
E: Unmet dependencies. Try using -f.
```
I tried ```
sudo apt-get -f dist-upgrade
``` It is now downloading the packages avor a 3G connexion, I come back to you it finishes, in a few hours or tomorrow ;-)

---

### Post by matt_symes on 2013-02-25
Hi

 ```
3G connexion
```

Hence APTCache :D

Kind reagsrd

---

### Post by djibi on 2013-02-25
```
$ sudo apt-get -f dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  libframe6 libgeis1 libgrail5 linux-headers-3.2.0-38
  linux-headers-3.2.0-38-generic-pae linux-image-3.2.0-38-generic-pae
  printer-driver-postscript-hp
The following packages will be upgraded:
  accountsservice activity-log-manager-common
  activity-log-manager-control-center apparmor appmenu-gtk appmenu-gtk3 apport
  apport-gtk apport-symptoms apt apt-transport-https apt-utils aptdaemon
  aptdaemon-data bamfdaemon bind9-host brasero brasero-cdrkit brasero-common
  build-essential busybox-static checkbox checkbox-qt colord compiz
  compiz-core compiz-gnome compiz-plugins-default cups cups-bsd cups-client
  cups-common cups-ppdc dbus dbus-x11 dconf-gsettings-backend dconf-service
  deja-dup dh-apparmor dnsutils dpkg-dev duplicity eog evince evince-common
  firefox firefox-globalmenu firefox-gnome-support firefox-locale-en
  fonts-opensymbol gcalctool gdb ghostscript ghostscript-cups ghostscript-x
  ginn gir1.2-gtk-3.0 gir1.2-gudev-1.0 gir1.2-javascriptcoregtk-3.0
  gir1.2-launchpad-integration-3.0 gir1.2-rb-3.0 gir1.2-totem-1.0
  gir1.2-webkit-3.0 glib-networking glib-networking-common
  glib-networking-services gnome-accessibility-themes gnome-control-center
  gnome-control-center-data gnome-games-data gnome-media gnome-power-manager
  gnome-settings-daemon gnome-sudoku gnomine gnupg gpgv grub-common grub-pc
  grub-pc-bin grub2-common gstreamer0.10-gconf gstreamer0.10-plugins-good
  gstreamer0.10-pulseaudio gvfs gvfs-backends gvfs-bin gvfs-common
  gvfs-daemons gvfs-fuse gvfs-libs gwibber gwibber-service
  gwibber-service-facebook gwibber-service-identica gwibber-service-twitter
  hplip hplip-data im-switch indicator-messages indicator-sound
  indicator-status-provider-mc5 isc-dhcp-client isc-dhcp-common jockey-common
  jockey-gtk landscape-client-ui-install language-pack-en
  language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base
  language-selector-common language-selector-gnome launchpad-integration
  libaccountsservice0 libapt-inst1.4 libart-2.0-2 libbamf0 libbamf3-0
  libbind9-80 libbrasero-media3-1 libcolord1 libcups2 libcupscgi1
  libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1 libdconf-dbus-1-0
  libdconf0 libdecoration0 libdevmapper-event1.02.1 libdns81 libdpkg-perl
  libedataserverui-3.0-1 libevince3-3 libfreerdp-plugins-standard libfreerdp1
  libgail-3-0 libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libglu1-mesa
  libgnome-control-center1 libgnome2-common libgrip0 libgs9 libgs9-common
  libgtk-3-0 libgtk-3-bin libgtk-3-common libgudev-1.0-0 libgwibber-gtk2
  libgwibber2 libhpmud0 libindicator-messages-status-provider1 libisc83
  libisccc80 libisccfg82 libjavascriptcoregtk-3.0-0
  liblaunchpad-integration-3.0-1 liblaunchpad-integration-common libldap-2.4-2
  liblightdm-gobject-1-0 liblvm2app2.2 liblwres80 libmission-control-plugins0
  libnautilus-extension1a libnm-glib-vpn1 libnm-glib4 libnm-util2 libnspr4
  libnss3 libnux-2.0-0 libnux-2.0-common liboverlay-scrollbar-0.2-0
  liboverlay-scrollbar3-0.2-0 libparted0debian1 libpoppler-glib8 libpoppler19
  libproxy1 libproxy1-plugin-gsettings libproxy1-plugin-networkmanager
  libpulse-mainloop-glib0 libpulse0 libpulsedsp libpurple-bin libpurple0
  libqt4-dbus libqt4-declarative libqt4-network libqt4-opengl libqt4-script
  libqt4-sql libqt4-sql-sqlite libqt4-svg libqt4-xml libqt4-xmlpatterns
  libqtbamf1 libqtcore4 libqtgui4 libreoffice-base-core libreoffice-common
  libreoffice-core libreoffice-draw libreoffice-emailmerge libreoffice-gnome
  libreoffice-gtk libreoffice-help-en-us libreoffice-impress libreoffice-math
  libreoffice-style-human libreoffice-writer librhythmbox-core5 libsane-hpaio
  libsnmp-base libsnmp15 libssh-4 libssl-dev libssl-doc libtelepathy-glib0
  libtiff4 libtotem0 libunity-2d-private0 libunity-core-5.0-5
  libwebkitgtk-3.0-0 libwebkitgtk-3.0-common libxatracker1 libxcb-dri2-0
  libxcb-glx0 libxcb-render0 libxcb-shape0 libxcb-shm0 libxcb1 libxcb1-dev
  libxslt1.1 light-themes lightdm linux-firmware linux-generic-pae
  linux-headers-generic-pae linux-image-generic-pae linux-libc-dev lsb-base
  lsb-release mahjongg make man-db multiarch-support nautilus nautilus-data
  network-manager ntfs-3g nux-tools nvidia-common onboard oneconf openssl
  overlay-scrollbar parted passwd plymouth-theme-ubuntu-logo
  plymouth-theme-ubuntu-text policykit-1-gnome poppler-utils
  printer-driver-gutenprint printer-driver-hpcups printer-driver-hpijs
  printer-driver-ptouch pulseaudio pulseaudio-module-bluetooth
  pulseaudio-module-gconf pulseaudio-module-x11 pulseaudio-utils python-apport
  python-aptdaemon python-aptdaemon.gtk3widgets python-aptdaemon.pkcompat
  python-crypto python-cupshelpers python-debtagshw python-gst0.10
  python-keyring python-libproxy python-libxml2 python-piston-mini-client
  python-problem-report python-software-properties python-ubuntu-sso-client
  python-ubuntuone-control-panel python-uno qdbus remmina remmina-common
  remmina-plugin-rdp remmina-plugin-vnc resolvconf rhythmbox rhythmbox-data
  rhythmbox-mozilla rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune
  rhythmbox-plugin-zeitgeist rhythmbox-plugins samba-common samba-common-bin
  seahorse sessioninstaller shotwell simple-scan smbclient software-center
  software-properties-common software-properties-gtk
  system-config-printer-common system-config-printer-gnome
  system-config-printer-udev telepathy-gabble telepathy-mission-control-5
  thunderbird thunderbird-globalmenu thunderbird-gnome-support totem
  totem-common totem-mozilla totem-plugins transmission-common
  transmission-gtk ubuntu-desktop ubuntu-docs ubuntu-keyring ubuntu-minimal
  ubuntu-sso-client ubuntu-sso-client-gtk ubuntu-standard
  ubuntuone-control-panel ubuntuone-installer udisks unattended-upgrades unity
  unity-2d unity-2d-common unity-2d-panel unity-2d-shell unity-2d-spread
  unity-common unity-greeter unity-lens-applications unity-lens-music
  unity-lens-video unity-scope-musicstores unity-scope-video-remote
  unity-services uno-libs3 update-manager update-manager-core update-notifier
  update-notifier-common ure vino wpasupplicant x11-common x11-utils xdiagnose
  xorg xserver-common xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all
  xserver-xorg-video-intel xserver-xorg-video-qxl xserver-xorg-video-vmware
  xterm xul-ext-ubufox xvfb zeitgeist zenity zenity-common
383 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
57 not fully installed or removed.
Need to get 0 B/346 MB of archives.
After this operation, 202 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
E: Internal Error, No file name for libapt-pkg4.12
```
The error message changed:
```
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libreoffice-base-core libreoffice-common libreoffice-core libreoffice-draw
  libreoffice-gnome libreoffice-gtk libreoffice-impress libreoffice-math
  libreoffice-writer libssl-dev python-uno uno-libs3 ure
Suggested packages:
  libreoffice-base libreoffice-style-hicontrast libreoffice-style-tango
  libreoffice-style-crystal libreoffice-style-oxygen libreoffice-evolution
  libreoffice-gcj libreoffice-filter-binfilter default-jre gcj-jre
  java-gcj-compat openjdk-6-jre openjdk-7-jre sun-java5-jre sun-java6-jre
  java5-runtime jre libreoffice-java-common
The following packages will be upgraded:
  libreoffice-base-core libreoffice-common libreoffice-core libreoffice-draw
  libreoffice-gnome libreoffice-gtk libreoffice-impress libreoffice-math
  libreoffice-writer libssl-dev python-uno uno-libs3 ure
13 upgraded, 0 newly installed, 0 to remove and 370 not upgraded.
57 not fully installed or removed.
Need to get 0 B/75.9 MB of archives.
After this operation, 162 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
E: Internal Error, No file name for libapt-pkg4.12
```

---

### Post by matt_symes on 2013-02-25
Hi

Can you post the output from

```
dpkg --audit
```

Kind regards

---

### Post by schragge on 2013-02-25
Yeah, this error usually means you need to
```

sudo dpkg --configure -a

```
before anything else

---

### Post by djibi on 2013-02-25
```
$ sudo dpkg --audit 
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 libreoffice-style-human office productivity suite -- Human symbol style
 ure                  LibreOffice UNO runtime environment
 libfreetype6         FreeType 2 font engine, shared library files
 initramfs-tools      tools for generating an initramfs
 libxml2              GNOME XML library
 libdbus-1-3          simple interprocess messaging system (library)
 libperl5.14          shared Perl library
 fontconfig           generic font configuration library - support binaries
 libreoffice-math     office productivity suite -- equation editor
 libreoffice-impress  office productivity suite -- presentation
 libpython2.7         Shared Python runtime library (version 2.7)
 perl-modules         Core Perl modules
 libexpat1-dev        XML parsing C library - development kit
 libc6-dev            Embedded GNU C Library: Development Libraries and Header 
 libxslt1.1           XSLT 1.0 processing library - runtime library
 libdrm2              Userspace interface to kernel DRM services -- runtime
 libdrm-nouveau1a     Userspace interface to nouveau-specific kernel DRM servic
 libudev0             udev library
 libfontconfig1       generic font configuration library - runtime
 mountall             filesystem mounting tool
 libc-dev-bin         Embedded GNU C Library: Development binaries
 libapt-pkg4.12       package managment runtime library
 linux-libc-dev       Linux Kernel Headers for development
 libreoffice-writer   office productivity suite -- word processor
 libdrm-radeon1       Userspace interface to radeon-specific kernel DRM service
 libfontconfig1-dev   generic font configuration library - development
 python2.7            Interactive high-level object-oriented language (version 
 libreoffice-base-core office productivity suite -- shared library
 libreoffice-gnome    office productivity suite -- GNOME integration
 libsqlite3-0         SQLite 3 shared library
 libplymouth2         graphical boot animation and logger - shared libraries
 libnspr4             NetScape Portable Runtime Library
 libexpat1            XML parsing C library - runtime library
 initramfs-tools-bin  binaries used by initramfs-tools
 libreoffice-common   office productivity suite -- arch-independent files
 uno-libs3            LibreOffice UNO runtime environment -- public shared libr
 plymouth-label       graphical boot animation and logger - label control
 plymouth             graphical boot animation and logger - main package
 upstart              event-based init daemon
 python2.7-dev        Header files and a static library for Python (v2.7)
 libnih1              NIH Utility Library
 libssl-doc           SSL development documentation documentation
 libssl-dev           SSL development libraries, header files and documentation
 busybox-initramfs    Standalone shell setup for initramfs
 fonts-opensymbol     OpenSymbol TrueType font
 perl                 Larry Wall's Practical Extraction and Report Language
 libdrm-intel1        Userspace interface to intel-specific kernel DRM services
 libpciaccess0        Generic PCI access library for X
 libnss3              Network Security Service libraries
 fontconfig-config    generic font configuration library - configuration
 libreoffice-gtk      office productivity suite -- GTK+ integration
 libnih-dbus1         NIH D-Bus Bindings Library
 udev                 rule-based device node and kernel event manager
 python-uno           Python-UNO bridge
 libreoffice-draw     office productivity suite -- drawing
 libsqlite3-dev       SQLite 3 development files
 libfreetype6-dev     FreeType 2 font engine, development files
```

```
$ sudo dpkg --configure -a
Setting up libreoffice-style-human (1:3.5.4-0ubuntu1.1) ...
Setting up libfreetype6 (2.4.8-1ubuntu2.1) ...
Setting up libxml2 (2.7.8.dfsg-5.1ubuntu4.3) ...
Setting up libdbus-1-3 (1.4.18-1ubuntu1.3) ...
Setting up libperl5.14 (5.14.2-6ubuntu2.2) ...
dpkg: dependency problems prevent configuration of libreoffice-math:
 libreoffice-math depends on libreoffice-core (= 1:3.5.4-0ubuntu1); however:
  Version of libreoffice-core on system is 1:3.5.2-2ubuntu1.
dpkg: error processing libreoffice-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-impress:
 libreoffice-impress depends on libreoffice-core (= 1:3.5.4-0ubuntu1); however:
  Version of libreoffice-core on system is 1:3.5.2-2ubuntu1.
dpkg: error processing libreoffice-impress (--configure):
 dependency problems - leaving unconfigured
Setting up libxslt1.1 (1.1.26-8ubuntu1.1) ...
Setting up libdrm2 (2.4.39-0ubuntu0.1) ...
Setting up libdrm-nouveau1a (2.4.39-0ubuntu0.1) ...
Setting up libudev0 (175-0ubuntu9.2) ...
Setting up libc-dev-bin (2.15-0ubuntu10.3) ...
Setting up libapt-pkg4.12 (0.8.16~exp12ubuntu10.7) ...
Setting up linux-libc-dev (3.2.0-38.60) ...
dpkg: dependency problems prevent configuration of libreoffice-writer:
 libreoffice-writer depends on libreoffice-core (= 1:3.5.4-0ubuntu1); however:
  Version of libreoffice-core on system is 1:3.5.2-2ubuntu1.
dpkg: error processing libreoffice-writer (--configure):
 dependency problems - leaving unconfigured
Setting up libdrm-radeon1 (2.4.39-0ubuntu0.1) ...
dpkg: dependency problems prevent configuration of libreoffice-base-core:
 libreoffice-base-core depends on libreoffice-core (= 1:3.5.4-0ubuntu1); however:
  Version of libreoffice-core on system is 1:3.5.2-2ubuntu1.
dpkg: error processing libreoffice-base-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on libreoffice-core (= 1:3.5.4-0ubuntu1); however:
  Version of libreoffice-core on system is 1:3.5.2-2ubuntu1.
dpkg: error processing libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
Setting up libsqlite3-0 (3.7.9-2ubuntu1.1) ...
Setting up libplymouth2 (0.8.2-2ubuntu31) ...
Setting up libnspr4 (4.8.9-1ubuntu2.3) ...
Setting up libexpat1 (2.0.1-7.2ubuntu1.1) ...
Setting up initramfs-tools-bin (0.99ubuntu13.1) ...
Setting up libnih1 (1.0.3-4ubuntu9.1) ...
Setting up libssl-doc (1.0.1-4ubuntu5.5) ...
dpkg: dependency problems prevent configuration of libssl-dev:
 libssl-dev depends on libssl1.0.0 (= 1.0.1-4ubuntu5.5); however:
  Version of libssl1.0.0 on system is 1.0.1-4ubuntu5.6.
dpkg: error processing libssl-dev (--configure):
 dependency problems - leaving unconfigured
Setting up busybox-initramfs (1:1.18.5-1ubuntu4.1) ...
Setting up fonts-opensymbol (2:102.2+LibO3.5.4-0ubuntu1.1) ...
Setting up libpciaccess0 (0.12.902-1ubuntu0.1) ...
Setting up libnss3 (3.13.1.with.ckbi.1.88-1ubuntu6.1) ...
Setting up fontconfig-config (2.8.0-3ubuntu9.1) ...
dpkg: dependency problems prevent configuration of libreoffice-gtk:
 libreoffice-gtk depends on libreoffice-core (= 1:3.5.4-0ubuntu1); however:
  Version of libreoffice-core on system is 1:3.5.2-2ubuntu1.
dpkg: error processing libreoffice-gtk (--configure):
 dependency problems - leaving unconfigured
Setting up libnih-dbus1 (1.0.3-4ubuntu9.1) ...
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on libreoffice-core (= 1:3.5.4-0ubuntu1); however:
  Version of libreoffice-core on system is 1:3.5.2-2ubuntu1.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-draw:
 libreoffice-draw depends on libreoffice-core (= 1:3.5.4-0ubuntu1); however:
  Version of libreoffice-core on system is 1:3.5.2-2ubuntu1.
dpkg: error processing libreoffice-draw (--configure):
 dependency problems - leaving unconfigured
Setting up libc6-dev (2.15-0ubuntu10.3) ...
Setting up libfontconfig1 (2.8.0-3ubuntu9.1) ...
Setting up python2.7 (2.7.3-0ubuntu3.1) ...
dpkg: dependency problems prevent configuration of python2.7-dev:
 python2.7-dev depends on libssl-dev; however:
  Package libssl-dev is not configured yet.
dpkg: error processing python2.7-dev (--configure):
 dependency problems - leaving unconfigured
Setting up libdrm-intel1 (2.4.39-0ubuntu0.1) ...
Setting up libsqlite3-dev (3.7.9-2ubuntu1.1) ...
Setting up libfreetype6-dev (2.4.8-1ubuntu2.1) ...
Setting up fontconfig (2.8.0-3ubuntu9.1) ...
Regenerating fonts cache... done.
Setting up libpython2.7 (2.7.3-0ubuntu3.1) ...
Setting up libexpat1-dev (2.0.1-7.2ubuntu1.1) ...
Setting up libfontconfig1-dev (2.8.0-3ubuntu9.1) ...
Setting up ure (3.5.4-0ubuntu1.1) ...
Setting up perl-modules (5.14.2-6ubuntu2.2) ...
Setting up libreoffice-common (1:3.5.4-0ubuntu1.1) ...
Setting up uno-libs3 (3.5.4-0ubuntu1.1) ...
Setting up perl (5.14.2-6ubuntu2.2) ...
Setting up initramfs-tools (0.99ubuntu13.1) ...
update-initramfs: deferring update (trigger activated)
Setting up mountall (2.36.4) ...
Setting up plymouth (0.8.2-2ubuntu31) ...
update-initramfs: deferring update (trigger activated)
Setting up upstart (1.5-0ubuntu7.2) ...
Setting up udev (175-0ubuntu9.2) ...
udev stop/waiting
udev start/running, process 4061
Removing 'diversion of /sbin/udevadm to /sbin/udevadm.upgrade by fake-udev'
update-initramfs: deferring update (trigger activated)
Setting up plymouth-label (0.8.2-2ubuntu31) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-23-generic-pae
Errors were encountered while processing:
 libreoffice-math
 libreoffice-impress
 libreoffice-writer
 libreoffice-base-core
 libreoffice-gnome
 libssl-dev
 libreoffice-gtk
 python-uno
 libreoffice-draw
 python2.7-dev
```

I could install some package:
```
$ sudo apt-get -f dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  libframe6 libgeis1 libgrail5 linux-headers-3.2.0-38
  linux-headers-3.2.0-38-generic-pae linux-image-3.2.0-38-generic-pae
  printer-driver-postscript-hp
The following packages will be upgraded:
  accountsservice activity-log-manager-common
  activity-log-manager-control-center apparmor appmenu-gtk appmenu-gtk3 apport
  apport-gtk apport-symptoms apt apt-transport-https apt-utils aptdaemon
  aptdaemon-data bamfdaemon bind9-host brasero brasero-cdrkit brasero-common
  build-essential busybox-static checkbox checkbox-qt colord compiz
  compiz-core compiz-gnome compiz-plugins-default cups cups-bsd cups-client
  cups-common cups-ppdc dbus dbus-x11 dconf-gsettings-backend dconf-service
  deja-dup dh-apparmor dnsutils dpkg-dev duplicity eog evince evince-common
  firefox firefox-globalmenu firefox-gnome-support firefox-locale-en
  fonts-opensymbol gcalctool gdb ghostscript ghostscript-cups ghostscript-x
  ginn gir1.2-gtk-3.0 gir1.2-gudev-1.0 gir1.2-javascriptcoregtk-3.0
  gir1.2-launchpad-integration-3.0 gir1.2-rb-3.0 gir1.2-totem-1.0
  gir1.2-webkit-3.0 glib-networking glib-networking-common
  glib-networking-services gnome-accessibility-themes gnome-control-center
  gnome-control-center-data gnome-games-data gnome-media gnome-power-manager
  gnome-settings-daemon gnome-sudoku gnomine gnupg gpgv grub-common grub-pc
  grub-pc-bin grub2-common gstreamer0.10-gconf gstreamer0.10-plugins-good
  gstreamer0.10-pulseaudio gvfs gvfs-backends gvfs-bin gvfs-common
  gvfs-daemons gvfs-fuse gvfs-libs gwibber gwibber-service
  gwibber-service-facebook gwibber-service-identica gwibber-service-twitter
  hplip hplip-data im-switch indicator-messages indicator-sound
  indicator-status-provider-mc5 isc-dhcp-client isc-dhcp-common jockey-common
  jockey-gtk landscape-client-ui-install language-pack-en
  language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base
  language-selector-common language-selector-gnome launchpad-integration
  libaccountsservice0 libapt-inst1.4 libart-2.0-2 libbamf0 libbamf3-0
  libbind9-80 libbrasero-media3-1 libcolord1 libcups2 libcupscgi1
  libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1 libdconf-dbus-1-0
  libdconf0 libdecoration0 libdevmapper-event1.02.1 libdns81 libdpkg-perl
  libedataserverui-3.0-1 libevince3-3 libfreerdp-plugins-standard libfreerdp1
  libgail-3-0 libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libglu1-mesa
  libgnome-control-center1 libgnome2-common libgrip0 libgs9 libgs9-common
  libgtk-3-0 libgtk-3-bin libgtk-3-common libgudev-1.0-0 libgwibber-gtk2
  libgwibber2 libhpmud0 libindicator-messages-status-provider1 libisc83
  libisccc80 libisccfg82 libjavascriptcoregtk-3.0-0
  liblaunchpad-integration-3.0-1 liblaunchpad-integration-common libldap-2.4-2
  liblightdm-gobject-1-0 liblvm2app2.2 liblwres80 libmission-control-plugins0
  libnautilus-extension1a libnm-glib-vpn1 libnm-glib4 libnm-util2 libnspr4
  libnss3 libnux-2.0-0 libnux-2.0-common liboverlay-scrollbar-0.2-0
  liboverlay-scrollbar3-0.2-0 libparted0debian1 libpoppler-glib8 libpoppler19
  libproxy1 libproxy1-plugin-gsettings libproxy1-plugin-networkmanager
  libpulse-mainloop-glib0 libpulse0 libpulsedsp libpurple-bin libpurple0
  libqt4-dbus libqt4-declarative libqt4-network libqt4-opengl libqt4-script
  libqt4-sql libqt4-sql-sqlite libqt4-svg libqt4-xml libqt4-xmlpatterns
  libqtbamf1 libqtcore4 libqtgui4 libreoffice-base-core libreoffice-common
  libreoffice-core libreoffice-draw libreoffice-emailmerge libreoffice-gnome
  libreoffice-gtk libreoffice-help-en-us libreoffice-impress libreoffice-math
  libreoffice-style-human libreoffice-writer librhythmbox-core5 libsane-hpaio
  libsnmp-base libsnmp15 libssh-4 libssl-dev libssl-doc libtelepathy-glib0
  libtiff4 libtotem0 libunity-2d-private0 libunity-core-5.0-5
  libwebkitgtk-3.0-0 libwebkitgtk-3.0-common libxatracker1 libxcb-dri2-0
  libxcb-glx0 libxcb-render0 libxcb-shape0 libxcb-shm0 libxcb1 libxcb1-dev
  libxslt1.1 light-themes lightdm linux-firmware linux-generic-pae
  linux-headers-generic-pae linux-image-generic-pae linux-libc-dev lsb-base
  lsb-release mahjongg make man-db multiarch-support nautilus nautilus-data
  network-manager ntfs-3g nux-tools nvidia-common onboard oneconf openssl
  overlay-scrollbar parted passwd plymouth-theme-ubuntu-logo
  plymouth-theme-ubuntu-text policykit-1-gnome poppler-utils
  printer-driver-gutenprint printer-driver-hpcups printer-driver-hpijs
  printer-driver-ptouch pulseaudio pulseaudio-module-bluetooth
  pulseaudio-module-gconf pulseaudio-module-x11 pulseaudio-utils python-apport
  python-aptdaemon python-aptdaemon.gtk3widgets python-aptdaemon.pkcompat
  python-crypto python-cupshelpers python-debtagshw python-gst0.10
  python-keyring python-libproxy python-libxml2 python-piston-mini-client
  python-problem-report python-software-properties python-ubuntu-sso-client
  python-ubuntuone-control-panel python-uno qdbus remmina remmina-common
  remmina-plugin-rdp remmina-plugin-vnc resolvconf rhythmbox rhythmbox-data
  rhythmbox-mozilla rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune
  rhythmbox-plugin-zeitgeist rhythmbox-plugins samba-common samba-common-bin
  seahorse sessioninstaller shotwell simple-scan smbclient software-center
  software-properties-common software-properties-gtk
  system-config-printer-common system-config-printer-gnome
  system-config-printer-udev telepathy-gabble telepathy-mission-control-5
  thunderbird thunderbird-globalmenu thunderbird-gnome-support totem
  totem-common totem-mozilla totem-plugins transmission-common
  transmission-gtk ubuntu-desktop ubuntu-docs ubuntu-keyring ubuntu-minimal
  ubuntu-sso-client ubuntu-sso-client-gtk ubuntu-standard
  ubuntuone-control-panel ubuntuone-installer udisks unattended-upgrades unity
  unity-2d unity-2d-common unity-2d-panel unity-2d-shell unity-2d-spread
  unity-common unity-greeter unity-lens-applications unity-lens-music
  unity-lens-video unity-scope-musicstores unity-scope-video-remote
  unity-services uno-libs3 update-manager update-manager-core update-notifier
  update-notifier-common ure vino wpasupplicant x11-common x11-utils xdiagnose
  xorg xserver-common xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all
  xserver-xorg-video-intel xserver-xorg-video-qxl xserver-xorg-video-vmware
  xterm xul-ext-ubufox xvfb zeitgeist zenity zenity-common
383 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
10 not fully installed or removed.
Need to get 0 B/346 MB of archives.
After this operation, 202 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 171072 files and directories currently installed.)
Preparing to replace ure 3.5.4-0ubuntu1.1 (using .../ure_3.5.7-0ubuntu4_i386.deb) ...
Unpacking replacement ure ...
Preparing to replace uno-libs3 3.5.4-0ubuntu1.1 (using .../uno-libs3_3.5.7-0ubuntu4_i386.deb) ...
Unpacking replacement uno-libs3 ...
Preparing to replace libreoffice-common 1:3.5.4-0ubuntu1.1 (using .../libreoffice-common_1%3a3.5.7-0ubuntu4_all.deb) ...
Unpacking replacement libreoffice-common ...
dpkg: regarding .../libreoffice-core_1%3a3.5.7-0ubuntu4_i386.deb containing libreoffice-core:
 libreoffice-core conflicts with libreoffice-draw (<< 1:3.5.7-0ubuntu4)
  libreoffice-draw (version 1:3.5.4-0ubuntu1) is present and unpacked but not configured.
dpkg: error processing /var/cache/apt/archives/libreoffice-core_1%3a3.5.7-0ubuntu4_i386.deb (--unpack):
 conflicting packages - not installing libreoffice-core
No apport report written because MaxReports is reached already
                                                              Preparing to replace fonts-opensymbol 2:102.2+LibO3.5.4-0ubuntu1.1 (using .../fonts-opensymbol_2%3a102.2+LibO3.5.7-0ubuntu4_all.deb) ...
Unpacking replacement fonts-opensymbol ...
Preparing to replace libreoffice-style-human 1:3.5.4-0ubuntu1.1 (using .../libreoffice-style-human_1%3a3.5.7-0ubuntu4_all.deb) ...
Unpacking replacement libreoffice-style-human ...
Preparing to replace libnspr4 4.8.9-1ubuntu2.3 (using .../libnspr4_4.9.4-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement libnspr4 ...
Preparing to replace libnss3 3.13.1.with.ckbi.1.88-1ubuntu6.1 (using .../libnss3_3.14.1-0ckbi1.93ubuntu.0.12.04.1_i386.deb) ...
Unpacking replacement libnss3 ...
Preparing to replace libxslt1.1 1.1.26-8ubuntu1.1 (using .../libxslt1.1_1.1.26-8ubuntu1.2_i386.deb) ...
Unpacking replacement libxslt1.1 ...
Preparing to replace libssl-doc 1.0.1-4ubuntu5.5 (using .../libssl-doc_1.0.1-4ubuntu5.6_all.deb) ...
Unpacking replacement libssl-doc ...
Preparing to replace ubuntu-keyring 2011.11.21 (using .../ubuntu-keyring_2011.11.21.1_all.deb) ...
Unpacking replacement ubuntu-keyring ...
Processing triggers for shared-mime-info ...
Processing triggers for man-db ...
Processing triggers for gnome-icon-theme ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for fontconfig ...
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-core_1%3a3.5.7-0ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Thank you for your help!

---

### Post by schragge on 2013-02-25
Well, lather, rinse, repeat :), i.e. what packages are still not configured?
```

sudo dpkg --audit

```

---

### Post by matt_symes on 2013-02-25
Hi 

Have you pinned any packages ?

What version of ubuntu are you using ?

> libreoffice-math depends on libreoffice-core (= 1:3.5.4-0ubuntu1); however:   Version of libreoffice-core on system is 1:3.5.2-2ubuntu1.It wants version of libreoffice-core = 1:3.5.4-0ubuntu1.

can you install the version ?

```
sudo apt-get remove libreoffice-core=1:3.5.2-2ubuntu1
```

```
sudo apt-get  install libreoffice-core=1:3.5.4-0ubuntu1
```Kind regards

---

### Post by djibi on 2013-02-26
Hello!
I am using Ubuntu 12.04.
Here are the different commands results:
```
$ sudo dpkg --audit 
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 libreoffice-style-human office productivity suite -- Human symbol style
 ure                  LibreOffice UNO runtime environment
 libreoffice-math     office productivity suite -- equation editor
 libreoffice-impress  office productivity suite -- presentation
 libxslt1.1           XSLT 1.0 processing library - runtime library
 libreoffice-writer   office productivity suite -- word processor
 libreoffice-base-core office productivity suite -- shared library
 libreoffice-gnome    office productivity suite -- GNOME integration
 libnspr4             NetScape Portable Runtime Library
 libreoffice-common   office productivity suite -- arch-independent files
 uno-libs3            LibreOffice UNO runtime environment -- public shared libr
 python2.7-dev        Header files and a static library for Python (v2.7)
 libssl-doc           SSL development documentation documentation
 ubuntu-keyring       GnuPG keys of the Ubuntu archive
 libssl-dev           SSL development libraries, header files and documentation
 fonts-opensymbol     OpenSymbol TrueType font
 libnss3              Network Security Service libraries
 libreoffice-gtk      office productivity suite -- GTK+ integration
 python-uno           Python-UNO bridge
 libreoffice-draw     office productivity suite -- drawing
```

```
$ sudo apt-get remove libreoffice-core=1:3.5.2-2ubuntu1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libreoffice-base-core : Depends: libreoffice-core (= 1:3.5.4-0ubuntu1) but it is not going to be installed
 libreoffice-draw : Depends: libreoffice-core (= 1:3.5.4-0ubuntu1) but it is not going to be installed
 libreoffice-emailmerge : Depends: libreoffice-core but it is not going to be installed
 libreoffice-gnome : Depends: libreoffice-core (= 1:3.5.4-0ubuntu1) but it is not going to be installed
 libreoffice-gtk : Depends: libreoffice-core (= 1:3.5.4-0ubuntu1) but it is not going to be installed
                   Recommends: libreoffice-style-tango but it is not going to be installed
 libreoffice-impress : Depends: libreoffice-core (= 1:3.5.4-0ubuntu1) but it is not going to be installed
 libreoffice-math : Depends: libreoffice-core (= 1:3.5.4-0ubuntu1) but it is not going to be installed
 libreoffice-style-human : Depends: libreoffice-core but it is not going to be installed
 libreoffice-writer : Depends: libreoffice-core (= 1:3.5.4-0ubuntu1) but it is not going to be installed
 libssl-dev : Depends: libssl1.0.0 (= 1.0.1-4ubuntu5.5) but 1.0.1-4ubuntu5.6 is to be installed
 python-uno : Depends: libreoffice-core (= 1:3.5.4-0ubuntu1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

And if I try to install the new libreoffice-core package:
```
$ sudo apt-get install libreoffice-core=1:3.5.4-0ubuntu1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Version '1:3.5.4-0ubuntu1' for 'libreoffice-core' was not found
```
I tried version 1:3.5.7 and it was not found too.

---

### Post by schragge on 2013-02-26
Current versions are:
precise: **1:3.5.4-0ubuntu1.1**
precise-updates:  **1:3.5.7-0ubuntu4**

But at this point, I'd first force-remove all libreoffice-related packages:
```

sudo dpkg --force-remove-reinstreq -r ^libreoffice
sudo apt-get clean
sudo apt-get dist-upgrade
sudo apt-get install libreoffice

```

---

### Post by djibi on 2013-02-26
YEAH!
We finally got it!
```
sudo dpkg --force-remove-reinstreq ^libreoffice
```
was a part of the solution.

Here was the solution for future use:
```
sudo dpkg --remove --force-remove-reinstreq libreoffice*
sudo apt-get -f dist-upgrade
sudo dpkg --remove --force-remove-reinstreq libssl-dev
sudo dpkg --remove --force-remove-reinstreq python*
sudo apt-get install python2.7
sudo apt-get -f install
sudo apt-get dist-upgrade
sudo apt-get install libreoffice
sudo apt-get upgrade
```

Thanks to the involved Ubuntuers for their time, patience and involvement!

Regards,
J-B

---

### Post by matt_symes on 2013-02-26
Hi

That's great news. Sometimes you have to work on the packages themselves and not reply on apt-get.

Can you mark this thread as solved.

Kind regards

---

### Post by srimchandra on 2014-01-27
Thanks it worked for me.

sudo dpkg --force-remove-reinstreq -r libreoffice*

---

### Post by WinEunuchs2Unix on 2014-08-10
> **matt_symes said:**
> Hi

```
sudo dpkg -P libreoffice-core
```

```
sudo apt-get remove --purge libreoffice
```


It was one of the conflicting packages. I'm going through all the conflicting packages for you :D

I really hoping it's just libreoffice that this has happened to.

Kind regards

Installing Unity-Desktop overtop of Apache OpenOffice drove me crazy for hours last night due to broken dependencies and nuclear meltdown of apt-get and Ubuntu Software Centre.  After hours of google and dozens of suggestions executed this code finally got rid of the problems.

PS I didn't have to reinstall Unity-Desktop to get back network-manager and system-settings applets but "it seemed like a good idea at the time..."

---

### Post by nigelhinton on 2014-08-16
I've spent hours trying to find a solution to broken package for Libreoffice-common which stops me from loading fileZilla and mono which are essential for my REAL WORk.

i've been through all relevant postings and it appears that this is a bug resulting from some crappy Ubuntu design whereby Libreoffice is coupled with Ubuntu.

I attach what I've done which is the about the 3rd time I've tried to purge and then re-install Libreoffice so that I can load some more software.

This is the final straw with Ubuntu and I would not advise anyone who needs to rely on their computer for work to go anywhere near Ubuntu in any form or variety - what a heap of crap!

The following packages have unmet dependencies:
 libobasis4.1-core01 : Depends: libreoffice4.1-ure but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
nigel@c1:~/folderAnalyst/reports$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libreoffice-common
Suggested packages:
  libreoffice-style-hicontrast libreoffice-style-tango
  libreoffice-style-crystal libreoffice-style-oxygen
The following NEW packages will be installed:
  libreoffice-common
0 upgraded, 1 newly installed, 0 to remove and 147 not upgraded.
3 not fully installed or removed.
Need to get 21.0 MB of archives.
After this operation, 52.7 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libreoffice-common all 1:3.5.7-0ubuntu6.1 [21.0 MB]
Fetched 21.0 MB in 5min 50s (60.0 kB/s)                                        
(Reading database ... 152787 files and directories currently installed.)
Unpacking libreoffice-common (from .../libreoffice-common_1%3a3.5.7-0ubuntu6.1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libreoffice-common_1%3a3.5.7-0ubuntu6.1_all.deb (--unpack):
 trying to overwrite '/usr/share/applications/libreoffice-startcenter.desktop', which is also in package libreoffice 1:4.1.0bodhi1
rmdir: failed to remove `/var/lib/libreoffice/share/prereg/': No such file or directory
rmdir: failed to remove `/var/lib/libreoffice/share/': Directory not empty
rmdir: failed to remove `/var/lib/libreoffice/program/': No such file or directory
rmdir: failed to remove `/var/lib/libreoffice': Directory not empty
rmdir: failed to remove `/var/lib/libreoffice': Directory not empty
Processing triggers for man-db ...
Processing triggers for gnome-icon-theme ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for desktop-file-utils ...
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-common_1%3a3.5.7-0ubuntu6.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

This was after remove,autoremove,purge and so on and so on.

If I try to load any new software it will say there is a dependency for Libreoffice-common and so on, and so on.

When I've gathered my strength, I'm going to download a non-Ubuntu distribution and start from scratch.  The only saving grace about my association with Ubuntu systems is that I'm now so adept at getting my data off systems and back onto new ones because that's what you do if you use Ubuntu.

How the hell Ubuntu manages to maintain a high profile in the Linux community is beyond me.

Ubuntu gives Linux a very bad name.

---

