---
title: "Problem with package tzdata"
date: 2017-02-22
forum: Installation &amp; Upgrades
---

### Post by andreas-mk on 2017-02-22
Hello,

I post this for a friend of me, how works with Lubuntu 14.04 LTS

It has a problem with the package tzdata and we tried this:


```
23 aktualisiert, 4 neu installiert, 0 zu entfernen und 444 nicht aktualisiert.
20 nicht vollständig installiert oder entfernt.
Es müssen noch 0 B von 100 MB an Archiven heruntergeladen werden.
Nach dieser Operation werden 295 MB Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren? [J/n] J
Segmentation fault (core dumped)
tzdata (2016j-0ubuntu0.14.04) wird eingerichtet ...
dpkg: Fehler beim Bearbeiten des Paketes tzdata (--configure):
 Unterprozess installiertes post-installation-Skript wurde durch Signal (Speicherzugriffsfehler), Speicherabbild erzeugt getötet
Fehler traten auf beim Bearbeiten von:
 tzdata
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

To solve it, we tried this:

[FONT=Arial]1. sudo apt-get purge tzdata
                
                2. sudo apt-get clean
                
                3. sudo apt-get autoclean
                
                4. sudo apt-get autoremove
                
                5. sudo apt-get update
                
                6. sudo apt-get install --reinstall lubuntu-desktop
                
                7. sudo dpkg-reconfigure -phigh -a
[/FONT]
And this is the command output:

```

sudo apt-get purge tzdata



Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.      
Statusinformationen werden eingelesen.... Fertig
Die folgenden Pakete wurden automatisch installiert und werden nicht mehr benötigt:
  brasero-cdrkit brasero-common compiz-core compiz-plugins-default crda
  dvd+rw-tools fonts-sil-gentium fonts-sil-gentium-basic genisoimage
  gir1.2-gconf-2.0 gir1.2-gnomekeyring-1.0 gir1.2-gst-plugins-base-1.0
  gir1.2-peas-1.0 gir1.2-rb-3.0 growisofs gstreamer0.10-pulseaudio
  gstreamer1.0-pulseaudio libbrasero-media3-1 libcdr-0.0-0 libcmis-0.4-4
  libcompizconfig0 libdecoration0 libdmapsharing-3.0-2 libfs6 libfso-glib2
  libfsobasics3 libfsoframework3 libfsoresource3 libgee2 libgmime-2.6-0
  libmspub-0.0-0 libnl-genl-3-200 liborcus-0.6-0 libpeas-1.0-0 libpeas-common
  libprotobuf8 libreadline5 libreoffice-avmedia-backend-gstreamer
  libreoffice-calc libreoffice-draw libreoffice-gnome libreoffice-gtk
  libreoffice-gtk2 libreoffice-impress libreoffice-l10n-zu
  libreoffice-pdfimport libreoffice-report-builder-bin librhythmbox-core8
  libtotem-plparser18 libvisio-0.0-0 libzeitgeist-2.0-0 lubuntu-icon-theme
  policykit-desktop-privileges python-compizconfig python3-mako
  python3-markupsafe rhythmbox-data ttf-ubuntu-font-family wireless-regdb
  wodim wpasupplicant x11-apps x11-session-utils x11-xfs-utils xfonts-mathml
  xinit zeitgeist-core
Verwenden Sie »apt-get autoremove«, um sie zu entfernen.
Die folgenden zusätzlichen Pakete werden installiert: sudo apt-get clean
  gstreamer0.10-plugins-good gstreamer0.10-pulseaudio initramfs-tools-bin
  libboost-filesystem1.54.0 libboost-iostreams1.54.0 libharfbuzz-icu0
  libharfbuzz0b libnm-gtk-common libnm-gtk0 libqt5core5a libqt5dbus5
  libqt5gui5 libqt5network5 libqt5widgets5 libreoffice-base
  libreoffice-base-core libreoffice-base-drivers libreoffice-calc
  libreoffice-common libreoffice-core libreoffice-draw libreoffice-gnome
  libreoffice-gtk libreoffice-gtk2 libreoffice-help-de libreoffice-help-en-gb
  libreoffice-impress libreoffice-java-common libreoffice-l10n-de
  libreoffice-l10n-en-gb libreoffice-math libreoffice-style-galaxy
  libreoffice-style-human libreoffice-writer libsystemd-daemon0 libudev1
  libxcb-icccm4 libxcb-image0 libxcb-render-util0 libxcb-xkb1
  libxkbcommon-x11-0 python3-distupgrade python3-software-properties
  python3-update-manager software-properties-common transmission-qt
  ubuntu-release-upgrader-core uno-libs3 update-manager-core
  update-notifier-common ure
Vorgeschlagene Pakete:
  libreoffice-gcj libreoffice-report-builder libjtds-java
  libreoffice-mysql-connector libmyodbc libmysql-java
  libreoffice-sdbc-postgresql odbc-postgresql libpg-java libsqliteodbc tdsodbc
  mdbtools libreoffice-style-breeze libreoffice-style-hicontrast
  libreoffice-style-oxygen libreoffice-style-sifr libreoffice-style-tango
  libreoffice-evolution libreoffice-grammarcheck-de hunspell-dictionary-en-gb
  myspell-dictionary-en-gb hyphen-en-gb libreoffice-grammarcheck-en-gb
  fonts-crosextra-caladea fonts-crosextra-carlito
Die folgenden Pakete werden ENTFERNT:
  abiword* accountsservice* alsa-base* apparmor* aptdaemon* apturl* audacious*
  avahi-daemon* blueman* bluez* brasero* ca-certificates-java* console-setup* sudo apt-get clean
  consolekit* cron* dbus* dbus-x11* default-jre* default-jre-headless*
  dmsetup* e2fsprogs* eject* exim4* exim4-base* exim4-daemon-light* freecad*
  friendly-recovery* fso-deviced* fso-deviced-player-gstreamer* gconf2* gcr*
  gdebi* gksu* gnome-disk-utility* gnome-keyring* gnome-system-tools*
  gnome-time-admin* grub-common* grub-gfxpayload-lists* grub-pc* grub-pc-bin*
  grub2-common* gstreamer0.10-gconf* gstreamer0.10-gnomevfs*
  gstreamer0.10-plugins-good-dbg* gvfs* gvfs-backends* gvfs-daemons*
  gvfs-fuse* hplip* hplip-gui* icedtea-7-jre-jamvm* initramfs-tools* kbd*
  language-selector-common* language-selector-gnome* libabiword-3.0*
  libatk-wrapper-java* libatk-wrapper-java-jni* libdevmapper-event1.02.1*
  libdevmapper1.02.1* libexo-1-0* libgksu2-0* libgnome2-0* libgnome2-bin*
  libgnome2-common* libgnomevfs2-0* libgnomevfs2-common* libgnomevfs2-extra*
  libical1* libnss-mdns* liboobs-1-5* libpam-systemd* libparted0debian1*
  libreoffice* libreoffice-l10n-en-za* libtcl8.6* libtk8.6* libxfce4ui-1-0*
  libxfconf-0-2* lightdm* linux-generic* linux-image-3.13.0-32-generic* sudo apt-get clean
  linux-image-3.13.0-34-generic* linux-image-3.13.0-35-generic*
  linux-image-3.13.0-36-generic* linux-image-3.13.0-37-generic*
  linux-image-3.13.0-39-generic* linux-image-3.13.0-40-generic*
  linux-image-3.13.0-41-generic* linux-image-3.13.0-44-generic*
  linux-image-3.13.0-45-generic* linux-image-3.13.0-46-generic*
  linux-image-3.13.0-48-generic* linux-image-3.13.0-49-generic*
  linux-image-3.13.0-51-generic* linux-image-3.13.0-52-generic*
  linux-image-3.13.0-53-generic* linux-image-3.13.0-55-generic*
  linux-image-3.13.0-57-generic* linux-image-3.13.0-58-generic* sudo apt-get clean
  linux-image-3.13.0-59-generic* linux-image-3.13.0-61-generic*
  linux-image-3.13.0-62-generic linux-image-3.13.0-63-generic
  linux-image-extra-3.13.0-32-generic* linux-image-extra-3.13.0-34-generic*
  linux-image-extra-3.13.0-35-generic* linux-image-extra-3.13.0-36-generic*
  linux-image-extra-3.13.0-37-generic* linux-image-extra-3.13.0-39-generic*
  linux-image-extra-3.13.0-40-generic* linux-image-extra-3.13.0-41-generic*
  linux-image-extra-3.13.0-44-generic* linux-image-extra-3.13.0-45-generic*
  linux-image-extra-3.13.0-46-generic* linux-image-extra-3.13.0-48-generic*
  linux-image-extra-3.13.0-49-generic* linux-image-extra-3.13.0-51-generic*
  linux-image-extra-3.13.0-52-generic* linux-image-extra-3.13.0-53-generic*


  sudo apt-get clean
 
  linux-image-extra-3.13.0-57-generic*
  linux-image-extra-3.13.0-58-generic* linux-image-extra-3.13.0-59-generic*
  linux-image-extra-3.13.0-61-generic* linux-image-extra-3.13.0-62-generic*
  linux-image-extra-3.13.0-63-generic* linux-image-generic* lubuntu-core*
  lubuntu-default-session* lubuntu-default-settings* lubuntu-desktop* lxinput*
  lxsession* lxsession-logout* media-player-info* mountall* network-manager*
  network-manager-gnome* openjdk-7-jre* openjdk-7-jre-headless* packagekit*
  parted* pidgin* plymouth* plymouth-label* plymouth-theme-lubuntu-logo*
  plymouth-theme-lubuntu-text* plymouth-theme-ubuntu-text* policykit-1*
  policykit-1-gnome* printer-driver-postscript-hp* python-collada*
  python-dateutil* python-matplotlib* python-tk* python-tz* python3-uno*
  rhythmbox* rhythmbox-mozilla* rhythmbox-plugin-cdrecorder*
  rhythmbox-plugin-zeitgeist* rhythmbox-plugins* software-properties-gtk*
  sxid* system-config-printer-gnome* system-tools-backends* systemd-services*
  transmission-gtk* tzdata* tzdata-java* ubuntu-drivers-common*
  ubuntu-minimal* ubuntu-release-upgrader-gtk* ubuntu-standard* ubuntu-tweak*
  udev* udisks2* update-manager* update-notifier* upower* upstart* ureadahead*
  usb-creator-common* usb-creator-gtk* util-linux xfburn* xfce4-notifyd*
  xfce4-power-manager* xfconf* xorg* xserver-xorg* xserver-xorg-core*
  xserver-xorg-input-all* xserver-xorg-input-evdev* xserver-xorg-input-mouse*
  xserver-xorg-input-synaptics* xserver-xorg-input-vmmouse*
  xserver-xorg-input-wacom* xserver-xorg-video-all* xserver-xorg-video-ati*
  xserver-xorg-video-cirrus* xserver-xorg-video-fbdev*
  xserver-xorg-video-glamoregl* xserver-xorg-video-intel*
  xserver-xorg-video-mach64* xserver-xorg-video-mga*
  xserver-xorg-video-modesetting* xserver-xorg-video-neomagic*
  xserver-xorg-video-nouveau* xserver-xorg-video-openchrome*
  xserver-xorg-video-qxl* xserver-xorg-video-r128* xserver-xorg-video-radeon*
  xserver-xorg-video-s3* xserver-xorg-video-savage*
  xserver-xorg-video-siliconmotion* xserver-xorg-video-sis*
  xserver-xorg-video-sisusb* xserver-xorg-video-tdfx*
  xserver-xorg-video-trident* xserver-xorg-video-vesa*
  xserver-xorg-video-vmware*
Die folgenden NEUEN Pakete werden installiert:
  libboost-filesystem1.54.0 libboost-iostreams1.54.0 libqt5core5a libqt5dbus5
  libqt5gui5 libqt5network5 libqt5widgets5 libreoffice-gtk2 libxcb-icccm4
  libxcb-image0 libxcb-render-util0 libxcb-xkb1 libxkbcommon-x11-0
  transmission-qt
Die folgenden Pakete werden aktualisiert (Upgrade):
  gstreamer0.10-plugins-good gstreamer0.10-pulseaudio initramfs-tools-bin
  libharfbuzz-icu0 libharfbuzz0b libnm-gtk-common libnm-gtk0 libreoffice-base
  libreoffice-base-core libreoffice-base-drivers libreoffice-calc
  libreoffice-common libreoffice-core libreoffice-draw libreoffice-gnome
  libreoffice-gtk libreoffice-help-de libreoffice-help-en-gb sudo apt-get clean
  libreoffice-impress libreoffice-java-common libreoffice-l10n-de
  libreoffice-l10n-en-gb libreoffice-math libreoffice-style-galaxy
  libreoffice-style-human libreoffice-writer libsystemd-daemon0 libudev1
  python3-distupgrade python3-software-properties python3-update-manager
  software-properties-common ubuntu-release-upgrader-core uno-libs3
  update-manager-core update-notifier-common ure
WARNUNG: Die folgenden essentiellen Pakete werden entfernt.
Dies sollte NICHT geschehen, außer Sie wissen genau, was Sie tun!
  e2fsprogs util-linux (wegen e2fsprogs) tzdata (wegen util-linux)
37 aktualisiert, 14 neu installiert, 224 zu entfernen und 387 nicht aktualisiert.
20 nicht vollständig installiert oder entfernt.
Es müssen 98,8 MB an Archiven heruntergeladen werden.
Nach dieser Operation werden 3.552 MB Plattenplatz freigegeben.
Sie sind im Begriff, etwas potentiell Schädliches zu tun.
Zum Fortfahren geben Sie bitte »Ja, tue was ich sage!« ein.
 ?]








Punkt 3
sudo apt-get autoclean


Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.      
Statusinformationen werden eingelesen.... Fertig
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Probieren Sie »apt-get update«, um diese Probleme zu korrigieren.








 
Punkt 4                  
Ign http://extras.ubuntu.com trusty InRelease                                 
OK   http://archive.canonical.com trusty Release.gpg                          
Ign http://de.archive.ubuntu.com trusty InRelease                             
OK   http://extras.ubuntu.com trusty Release.gpg                              
OK   http://archive.canonical.com trusty Release                              
Holen: 1 http://de.archive.ubuntu.com trusty-updates InRelease [65,9 kB]      
OK   http://de.archive.ubuntu.com trusty-backports InRelease                  
Holen: 2 http://security.ubuntu.com trusty-security InRelease [65,9 kB]       
OK   http://extras.ubuntu.com trusty Release                                  
OK   http://de.archive.ubuntu.com trusty Release.gpg                          
OK   http://de.archive.ubuntu.com trusty Release                              
OK   http://ppa.launchpad.net trusty InRelease               
Ign http://ppa.launchpad.net trusty InRelease        
OK   http://archive.canonical.com trusty/partner Sources
OK   http://ppa.launchpad.net trusty InRelease
OK   http://archive.canonical.com trusty/partner i386 Packages                
OK   http://ppa.launchpad.net trusty Release.gpg                              
Holen: 3 http://de.archive.ubuntu.com trusty-updates/main Sources [392 kB]    
OK   http://archive.canonical.com trusty/partner Translation-en               
OK   http://ppa.launchpad.net trusty Release                                  
OK   http://extras.ubuntu.com trusty/main Sources                             
Holen: 4 http://de.archive.ubuntu.com trusty-updates/restricted Sources [5.911 B]
OK   http://extras.ubuntu.com trusty/main i386 Packages                       
Holen: 5 http://de.archive.ubuntu.com trusty-updates/universe Sources [174 kB]
Holen: 6 http://security.ubuntu.com trusty-security/main Sources [126 kB]     
OK   http://ppa.launchpad.net trusty/main i386 Packages                       
Holen: 7 http://de.archive.ubuntu.com trusty-updates/multiverse Sources [7.510 B]
OK   http://ppa.launchpad.net trusty/main Translation-en                      
Holen: 8 http://de.archive.ubuntu.com trusty-updates/main i386 Packages [912 kB]
OK   http://ppa.launchpad.net trusty/main i386 Packages                       
OK   http://ppa.launchpad.net trusty/main Translation-en                      
OK   http://ppa.launchpad.net trusty/main i386 Packages                       
Holen: 9 http://security.ubuntu.com trusty-security/restricted Sources [4.637 B]
Ign http://extras.ubuntu.com trusty/main Translation-de_DE                    
Holen: 10 http://security.ubuntu.com trusty-security/universe Sources [49,6 kB]
Ign http://extras.ubuntu.com trusty/main Translation-de                       
Ign http://extras.ubuntu.com trusty/main Translation-en                       
Holen: 11 http://security.ubuntu.com trusty-security/multiverse Sources [3.194 B]
Holen: 12 http://security.ubuntu.com trusty-security/main i386 Packages [544 kB]
Holen: 13 http://de.archive.ubuntu.com trusty-updates/restricted i386 Packages [16,2 kB]
Holen: 14 http://de.archive.ubuntu.com trusty-updates/universe i386 Packages [400 kB]
Ign http://ppa.launchpad.net trusty/main Translation-de_DE                    
Ign http://ppa.launchpad.net trusty/main Translation-de                       
Holen: 15 http://de.archive.ubuntu.com trusty-updates/multiverse i386 Packages [14,4 kB]
Ign http://ppa.launchpad.net trusty/main Translation-en                       
Holen: 16 http://de.archive.ubuntu.com trusty-updates/main Translation-en [471 kB]
Holen: 17 http://de.archive.ubuntu.com trusty-updates/multiverse Translation-en [7.340 B]
Holen: 18 http://de.archive.ubuntu.com trusty-updates/restricted Translation-en [3.847 B]
Holen: 19 http://de.archive.ubuntu.com trusty-updates/universe Translation-en [211 kB]
Holen: 20 http://security.ubuntu.com trusty-security/restricted i386 Packages [13,1 kB]
OK   http://de.archive.ubuntu.com trusty-backports/main Sources               
Holen: 21 http://security.ubuntu.com trusty-security/universe i386 Packages [153 kB]
OK   http://de.archive.ubuntu.com trusty-backports/restricted Sources         
OK   http://de.archive.ubuntu.com trusty-backports/universe Sources           
OK   http://de.archive.ubuntu.com trusty-backports/multiverse Sources         
OK   http://de.archive.ubuntu.com trusty-backports/main i386 Packages         
OK   http://de.archive.ubuntu.com trusty-backports/restricted i386 Packages   
OK   http://de.archive.ubuntu.com trusty-backports/universe i386 Packages     
OK   http://de.archive.ubuntu.com trusty-backports/multiverse i386 Packages   
OK   http://de.archive.ubuntu.com trusty-backports/main Translation-en        
OK   http://de.archive.ubuntu.com trusty-backports/multiverse Translation-en  
OK   http://de.archive.ubuntu.com trusty-backports/restricted Translation-en  
OK   http://de.archive.ubuntu.com trusty-backports/universe Translation-en    
OK   http://de.archive.ubuntu.com trusty/main Sources                         
OK   http://de.archive.ubuntu.com trusty/restricted Sources                   
Holen: 22 http://security.ubuntu.com trusty-security/multiverse i386 Packages [4.278 B]
OK   http://security.ubuntu.com trusty-security/main Translation-en           
OK   http://security.ubuntu.com trusty-security/multiverse Translation-en     
OK   http://security.ubuntu.com trusty-security/restricted Translation-en     
OK   http://de.archive.ubuntu.com trusty/universe Sources                     
OK   http://de.archive.ubuntu.com trusty/multiverse Sources                   
OK   http://security.ubuntu.com trusty-security/universe Translation-en       
OK   http://de.archive.ubuntu.com trusty/main i386 Packages                   
OK   http://de.archive.ubuntu.com trusty/restricted i386 Packages   
OK   http://de.archive.ubuntu.com trusty/universe i386 Packages     
OK   http://de.archive.ubuntu.com trusty/multiverse i386 Packages             
OK   http://de.archive.ubuntu.com trusty/main Translation-de                  
OK   http://de.archive.ubuntu.com trusty/main Translation-en         
OK   http://de.archive.ubuntu.com trusty/multiverse Translation-de   
OK   http://de.archive.ubuntu.com trusty/multiverse Translation-en   
OK   http://de.archive.ubuntu.com trusty/restricted Translation-de   
OK   http://de.archive.ubuntu.com trusty/restricted Translation-en   
OK   http://de.archive.ubuntu.com trusty/universe Translation-de     
OK   http://de.archive.ubuntu.com trusty/universe Translation-en     
Ign http://de.archive.ubuntu.com trusty/main Translation-de_DE       
Ign http://de.archive.ubuntu.com trusty/multiverse Translation-de_DE 
Ign http://de.archive.ubuntu.com trusty/restricted Translation-de_DE 
Ign http://de.archive.ubuntu.com trusty/universe Translation-de_DE   
Es wurden 3.644 kB in 23 s geholt (155 kB/s).                                 
Paketlisten werden gelesen... Fertig




Punkt 5
sudo apt-get update


Ign http://extras.ubuntu.com trusty InRelease
Ign http://archive.canonical.com trusty InRelease                             
OK   http://archive.canonical.com trusty Release.gpg                          
OK   http://extras.ubuntu.com trusty Release.gpg                              
Ign http://de.archive.ubuntu.com trusty InRelease                             
OK   http://archive.canonical.com trusty Release                              
OK   http://extras.ubuntu.com trusty Release                                  
OK   http://security.ubuntu.com trusty-security InRelease                     
OK   http://de.archive.ubuntu.com trusty-updates InRelease                    
OK   http://archive.canonical.com trusty/partner Sources                      
OK   http://de.archive.ubuntu.com trusty-backports InRelease                  
OK   http://de.archive.ubuntu.com trusty Release.gpg                          
OK   http://archive.canonical.com trusty/partner i386 Packages                
OK   http://extras.ubuntu.com trusty/main Sources                             
OK   http://de.archive.ubuntu.com trusty Release                              
OK   http://archive.canonical.com trusty/partner Translation-en               
OK   http://extras.ubuntu.com trusty/main i386 Packages                       
OK   http://security.ubuntu.com trusty-security/main Sources                  
OK   http://de.archive.ubuntu.com trusty-updates/main Sources                 
OK   http://de.archive.ubuntu.com trusty-updates/restricted Sources           
OK   http://de.archive.ubuntu.com trusty-updates/universe Sources             
OK   http://security.ubuntu.com trusty-security/restricted Sources            
OK   http://ppa.launchpad.net trusty InRelease                                
OK   http://de.archive.ubuntu.com trusty-updates/multiverse Sources           
Ign http://ppa.launchpad.net trusty InRelease                                 
OK   http://de.archive.ubuntu.com trusty-updates/main i386 Packages           
OK   http://ppa.launchpad.net trusty InRelease                                
Ign http://extras.ubuntu.com trusty/main Translation-de_DE                    
OK   http://ppa.launchpad.net trusty Release.gpg                              
Ign http://extras.ubuntu.com trusty/main Translation-de                       
OK   http://security.ubuntu.com trusty-security/universe Sources              
OK   http://ppa.launchpad.net trusty Release                                  
Ign http://extras.ubuntu.com trusty/main Translation-en                       
OK   http://ppa.launchpad.net trusty/main i386 Packages                       
OK   http://de.archive.ubuntu.com trusty-updates/restricted i386 Packages     
OK   http://ppa.launchpad.net trusty/main Translation-en                      
OK   http://de.archive.ubuntu.com trusty-updates/universe i386 Packages       
OK   http://security.ubuntu.com trusty-security/multiverse Sources            
OK   http://ppa.launchpad.net trusty/main i386 Packages                       
OK   http://de.archive.ubuntu.com trusty-updates/multiverse i386 Packages     
OK   http://ppa.launchpad.net trusty/main Translation-en                      
OK   http://ppa.launchpad.net trusty/main i386 Packages                       
OK   http://de.archive.ubuntu.com trusty-updates/main Translation-en          
OK   http://security.ubuntu.com trusty-security/main i386 Packages            
OK   http://de.archive.ubuntu.com trusty-updates/multiverse Translation-en    
OK   http://de.archive.ubuntu.com trusty-updates/restricted Translation-en    
OK   http://security.ubuntu.com trusty-security/restricted i386 Packages      
OK   http://de.archive.ubuntu.com trusty-updates/universe Translation-en      
OK   http://de.archive.ubuntu.com trusty-backports/main Sources               
OK   http://security.ubuntu.com trusty-security/universe i386 Packages        
OK   http://de.archive.ubuntu.com trusty-backports/restricted Sources         
OK   http://de.archive.ubuntu.com trusty-backports/universe Sources           
OK   http://security.ubuntu.com trusty-security/multiverse i386 Packages      
OK   http://de.archive.ubuntu.com trusty-backports/multiverse Sources         
OK   http://de.archive.ubuntu.com trusty-backports/main i386 Packages         
Ign http://ppa.launchpad.net trusty/main Translation-de_DE                    
OK   http://de.archive.ubuntu.com trusty-backports/restricted i386 Packages   
OK   http://security.ubuntu.com trusty-security/main Translation-en           
Ign http://ppa.launchpad.net trusty/main Translation-de                       
OK   http://de.archive.ubuntu.com trusty-backports/universe i386 Packages     
Ign http://ppa.launchpad.net trusty/main Translation-en                       
OK   http://de.archive.ubuntu.com trusty-backports/multiverse i386 Packages   
OK   http://de.archive.ubuntu.com trusty-backports/main Translation-en
OK   http://security.ubuntu.com trusty-security/multiverse Translation-en
OK   http://de.archive.ubuntu.com trusty-backports/multiverse Translation-en
OK   http://de.archive.ubuntu.com trusty-backports/restricted Translation-en
OK   http://de.archive.ubuntu.com trusty-backports/universe Translation-en
OK   http://security.ubuntu.com trusty-security/restricted Translation-en
OK   http://de.archive.ubuntu.com trusty/main Sources               
OK   http://de.archive.ubuntu.com trusty/restricted Sources         
OK   http://de.archive.ubuntu.com trusty/universe Sources           
OK   http://security.ubuntu.com trusty-security/universe Translation-en
OK   http://de.archive.ubuntu.com trusty/multiverse Sources         
OK   http://de.archive.ubuntu.com trusty/main i386 Packages
OK   http://de.archive.ubuntu.com trusty/restricted i386 Packages
OK   http://de.archive.ubuntu.com trusty/universe i386 Packages
OK   http://de.archive.ubuntu.com trusty/multiverse i386 Packages
OK   http://de.archive.ubuntu.com trusty/main Translation-de
OK   http://de.archive.ubuntu.com trusty/main Translation-en
OK   http://de.archive.ubuntu.com trusty/multiverse Translation-de
OK   http://de.archive.ubuntu.com trusty/multiverse Translation-en
OK   http://de.archive.ubuntu.com trusty/restricted Translation-de
OK   http://de.archive.ubuntu.com trusty/restricted Translation-en
OK   http://de.archive.ubuntu.com trusty/universe Translation-de
OK   http://de.archive.ubuntu.com trusty/universe Translation-en
Ign http://de.archive.ubuntu.com trusty/main Translation-de_DE
Ign http://de.archive.karl-heinz@karlheinz-SCENIC-P-SCENICO-P:~$ sudo apt-get install --reinstall lubuntu-desktop
ubuntu.com trusty/multiverse Translation-de_DE
Ign http://de.archive.ubuntu.com trusty/restricted Translation-de_DE
Ign http://de.archive.ubuntu.com trusty/universe Translation-de_DE
Paketlisten werden gelesen... Fertig                                          
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n
W: Ignoring Provides line with DepCompareOp for package libreoffice-l10n


Punkt 6
sudo apt-get install --reinstall lubuntu-desktop


Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.      
Statusinformationen werden eingelesen.... Fertig
Die folgenden zusätzlichen Pakete werden installiert:
  linux-image-3.13.0-62-generic linux-image-3.13.0-63-generic util-linux
Vorgeschlagene Pakete:
  fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools util-linux-locales
Die folgenden Pakete werden aktualisiert (Upgrade):
  linux-image-3.13.0-62-generic linux-image-3.13.0-63-generic util-linux
3 aktualisiert, 0 neu installiert, 1 erneut installiert, 0 zu entfernen und 464 nicht aktualisiert.
20 nicht vollständig installiert oder entfernt.
Es müssen 29,9 MB an Archiven heruntergeladen werden.
Nach dieser Operation werden 65,8 MB Plattenplatz zusätzlich benutzt.
Möchten Sie fortfahren? [J/n]







```

What can I do? Thanks

----------------------------------------------------------------------------------------------------------

---

### Post by Impavidus on 2017-02-22
> **andreas-mk said:**
> 
3 aktualisiert, 0 neu installiert, 1 erneut installiert, 0 zu entfernen und 464 nicht aktualisiert.
20 nicht vollständig installiert oder entfernt.

464 outdated packages and 20 partially installed packages, so this system is in a pretty bad condition. A crash in a post install script can be difficult to fix and Lubuntu 14.04 is only 2 months away from end of life. So maybe a fresh install of Lubuntu 16.04 is the best way out. But if you wish, we can try to fix this problem.

---

