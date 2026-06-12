---
title: "Automatically installed/autoremove/too many packages"
date: 2009-03-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2009-03-02
I do not think that all these packages need to be removed. Will all this eventually sort out, or do I need to go through each one individually and see what is up with each?
```
The following packages were automatically installed and are no longer required:
  libclucene0ldbl menu-xdg desktop-base planner libgsf-gnome-1-114 libqt4-opengl gthumb
  gnome-desktop-environment python-psyco linux-headers-2.6.28-6-generic gnome-games-extra-data python-renderpm
  libxine1-x librdf0 linux-headers-2.6.28-6 libdiscid0 cheese libots0 gnome-network-admin hardinfo libqt4-test
  gthumb-data gparted libqt4-sql-mysql libqt4-dbus libxine1-misc-plugins libxcb-xv0 gnome-office phonon
  libaiksaurusgtk-1.2-0c2a abiword-common abiword libqt4-qt3support abiword-plugin-mathview latex-xft-fonts
  libaiksaurus-1.2-0c2a liblualib50 libboost-thread1.34.1 python-lxml swfdec-gnome python-reportlab-accel
  gnumeric-common libxine1-bin libexiv2-4 libsoup2.2-8 gnumeric-doc libboost-date-time1.34.1 librasqal1 dasher
  libloudmouth1-0 link-grammar-dictionaries-en libqt4-dbg p7zip gnome-themes-extras libgoffice-0-6-common
  libsoprano4 redland-utils gdm-themes abiword-help arj gnome-volume-manager libqt4-webkit libxine1-ffmpeg
  libt1-5 libaiksaurus-1.2-data libqtcore4 libavahi-qt3-1 libwv-1.2-3 python-4suite-doc gnome-backgrounds
  dasher-data gok libgdome2-0 libxcb-shape0 abiword-plugin-grammar libwmf-bin libtunepimp5 libqt4-sql libifp4
  libqt4-svg libswfdec-0.8-0 libgoffice-0-6 libstreamanalyzer0 libphonon4 libdvdread3 libqt4-xml
  python-uniconvertor libqt4-network imagemagick-doc phonon-backend-xine libqt4-designer libxine1-plugins
  liferea libgdome2-cpp-smart0c2a swfdec-mozilla gnome-core libqtgui4 gnumeric libpq5 libboost-filesystem1.34.1
  libstreams0 libraptor1 imagemagick libmodplug0c2 liblink-grammar4 exiv2 libgtkmathview0c2a libqt3-mt
  gnome-accessibility liblua50 libqt4-script miro-data perlmagick libxcb-shm0 soprano-daemon portmap inkscape
  raptor-utils python-reportlab libboost-python1.34.1 libnjb5 sound-juicer qt4-qtconfig libxine1-console
  libmusicbrainz3-6 gnome-vfs-obexftp libxine1

```

---

### Post by DougieFresh4U on 2009-03-08
Still seeing this when I do
```
sudo apt-get -f install
```
I think it's actually adding more every day!! I was hoping that python issue would get resolved and then maybe some of the list would go down. any thoughts on how I should handle this? I do believe doing an 'autoremove' will leave me a 'borked' sytem.
```
dougie@DougiesLeanMachine:~$ sudo apt-get -f install
[sudo] password for dougie: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libclucene0ldbl menu-xdg python-alsaaudio desktop-base planner libmono-posix1.0-cil libgsf-gnome-1-114 libqt4-opengl
  libmono-security1.0-cil gthumb gnome-desktop-environment python-psyco linux-headers-2.6.28-6-generic
  gnome-games-extra-data python-renderpm libmono-sharpzip0.84-cil librdf0 linux-headers-2.6.28-6 libdiscid0 cheese libots0
  gnome-network-admin hardinfo libmono-system-web1.0-cil libqt4-test gthumb-data gparted libqt4-sql-mysql libqt4-dbus
  gnome-office phonon libaiksaurusgtk-1.2-0c2a abiword-common abiword libqt4-qt3support abiword-plugin-mathview
  latex-xft-fonts libmono-data1.0-cil acpi python-sqlalchemy libaiksaurus-1.2-0c2a libboost-thread1.34.1 python-lxml
  swfdec-gnome python-reportlab-accel gnumeric-common libexiv2-4 libsoup2.2-8 gnumeric-doc libboost-date-time1.34.1
  librasqal1 python-utidylib dasher libloudmouth1-0 link-grammar-dictionaries-en libqt4-dbg p7zip gnome-themes-extras
  libgoffice-0-6-common libsoprano4 redland-utils libtidy-0.99-0 gdm-themes abiword-help arj gnome-volume-manager
  libqt4-webkit libt1-5 libaiksaurus-1.2-data libqtcore4 libwv-1.2-3 python-4suite-doc gnome-backgrounds dasher-data gok
  libgdome2-0 abiword-plugin-grammar libmono-getoptions1.0-cil libmono1.0-cil python-feedparser libmono-data-tds1.0-cil
  libwmf-bin libqt4-sql libmono-system-data1.0-cil libqt4-svg libswfdec-0.8-0 libgoffice-0-6 libstreamanalyzer0 libphonon4
  libdvdread3 libqt4-xml python-uniconvertor libqt4-network imagemagick-doc phonon-backend-xine libqt4-designer liferea
  libgdome2-cpp-smart0c2a swfdec-mozilla gnome-core libqtgui4 gnumeric libboost-filesystem1.34.1 libstreams0 libraptor1
  imagemagick liblink-grammar4 exiv2 libgtkmathview0c2a gnome-accessibility libqt4-script miro-data perlmagick
  python-chardet soprano-daemon portmap inkscape raptor-utils python-reportlab libboost-python1.34.1 sound-juicer
  qt4-qtconfig libmusicbrainz3-6 gnome-vfs-obexftp
Use 'apt-get autoremove' to remove them.

```

---

