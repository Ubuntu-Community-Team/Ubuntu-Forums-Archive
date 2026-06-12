---
title: "/var/lib/dpkg/info/format is corrupted,"
date: 2012-09-06
forum: Installation &amp; Upgrades
---

### Post by rosstaman on 2012-09-06
I have searched everywhere I know for information on this error and have found nothing.  Help!  This is affesting both updates and upgrades Here's the output from sudo apt-get upgrade (same error as update):

Reading package lists...
Building dependency tree...
Reading state information...
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic vlc vlc-nox
  vlc-plugin-notify vlc-plugin-pulse
The following packages will be upgraded:
  accountsservice apport apport-gtk aptdaemon aptdaemon-data base-files compiz
  compiz-core compiz-gnome compiz-plugins compiz-plugins-default cups cups-bsd
  cups-client cups-common cups-ppdc dconf-gsettings-backend dconf-service
  empathy empathy-common evince evince-common firefox firefox-globalmenu
  firefox-gnome-support firefox-locale-en flashplugin-downloader:i386
  flashplugin-installer fontconfig fontconfig-config fonts-opensymbol
  gcalctool ghostscript ghostscript-cups ghostscript-x
  gir1.2-accountsservice-1.0 gir1.2-gudev-1.0 gir1.2-javascriptcoregtk-3.0
  gir1.2-launchpad-integration-3.0 gir1.2-webkit-3.0 glib-networking
  glib-networking-common glib-networking-services gnome-control-center
  gnome-control-center-data gnome-desktop3-data gnome-games-data
  gnome-settings-daemon gnome-sudoku gnomine google-chrome-stable
  idle-python2.7 imagemagick imagemagick-common initscripts jockey-common
  jockey-gtk krb5-locales language-pack-en language-pack-en-base
  language-pack-gnome-en language-pack-gnome-en-base launchpad-integration
  libaccountsservice0 libbonobo2-0 libbonobo2-common libbonoboui2-0
  libbonoboui2-common libcups2 libcupscgi1 libcupsdriver1 libcupsimage2
  libcupsmime1 libcupsppdc1 libdconf-dbus-1-0 libdconf0 libdecoration0
  libevince3-3 libexpat1 libfontconfig1 libfreerdp-plugins-standard
  libfreerdp1 libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libglu1-mesa
  libgnome-control-center1 libgnome-desktop-3-2 libgphoto2-2 libgphoto2-l10n
  libgphoto2-port0 libgs9 libgs9-common libgssapi-krb5-2 libgudev-1.0-0
  libjavascriptcoregtk-1.0-0 libjavascriptcoregtk-3.0-0 libk5crypto3 libkrb5-3
  libkrb5support0 liblaunchpad-integration-3.0-1
  liblaunchpad-integration-common liblaunchpad-integration1
  liblaunchpad-integration1.0-cil libldap-2.4-2 liblightdm-gobject-1-0
  libmagickcore4 libmagickcore4-extra libmagickwand4
  libmission-control-plugins0 libnautilus-extension1a libnspr4 libnspr4-0d
  libnss3 libnss3-1d libnux-2.0-0 libnux-2.0-common libperl5.14 libpython2.7
  libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core
  libreoffice-draw libreoffice-emailmerge libreoffice-gnome libreoffice-gtk
  libreoffice-help-en-us libreoffice-impress libreoffice-math
  libreoffice-style-human libreoffice-style-tango libreoffice-writer
  libsqlite3-0 libssl1.0.0 libssl1.0.0:i386 libudev0 libunity-core-5.0-5
  libvlc5 libvlccore5 libwebkitgtk-1.0-0 libwebkitgtk-1.0-common
  libwebkitgtk-3.0-0 libwebkitgtk-3.0-common libxatracker1 libxml-sax-perl
  libxslt1.1 light-themes lightdm linux-libc-dev mahjongg nautilus
  nautilus-data nautilus-sendto-empathy nux-tools openssl perl perl-base
  perl-modules policykit-1-gnome python-apport python-aptdaemon
  python-aptdaemon-gtk python-aptdaemon.gtk3widgets
  python-aptdaemon.gtkwidgets python-aptdaemon.pkcompat python-gst0.10
  python-launchpad-integration python-problem-report
  python-software-properties python-ubuntu-sso-client python-uno python2.7
  python2.7-minimal resolvconf sessioninstaller software-center
  software-properties-common software-properties-gtk sysv-rc sysvinit-utils
  telepathy-mission-control-5 thunderbird thunderbird-globalmenu
  thunderbird-gnome-support ttf-opensymbol tzdata ubuntu-docs
  ubuntu-sso-client ubuntu-sso-client-gtk ubuntu-sso-client-qt
  ubuntuone-installer udev unity unity-common unity-greeter unity-services
  uno-libs3 update-manager update-manager-core update-notifier
  update-notifier-common ure vlc-data xserver-common xserver-xorg-core
  xserver-xorg-video-intel xsltproc
208 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
Need to get 0 B/266 MB of archives.
After this operation, 7,985 kB of additional disk space will be used.
Do you want to continue [Y/n]? Preconfiguring packages ...
dpkg: error: /var/lib/dpkg/info/format is corrupted, it should contain a database format version (an integer)

---

