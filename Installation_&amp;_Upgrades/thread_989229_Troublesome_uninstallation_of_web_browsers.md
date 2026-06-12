---
title: "Troublesome uninstallation of web browsers"
date: 2008-11-21
forum: Installation &amp; Upgrades
---

### Post by liamnixon on 2008-11-21
I can't seem to uninstall Seamonkey or Opera.

I did 'apt-get remove seamonkey', and it seemed to work, but when I opened the network folder, it was still there and it still ran too!  And opera, well, I downloaded that from the web site, so I tried to remove it manually, but I'm apparently not allowed to delete folders, and I'm not sure how to change that.  :mad:

If you can't tell, I'm pretty new to Linux (used for a couple months now), and really new to XFCE, so be gentle, please!

Thanks.

---

### Post by taurus on 2008-11-21
Did you download and install the .deb version of opera?  If so, you can remove it with the dpkg command from a terminal.

```
sudo dpkg remove opera
```

---

### Post by liamnixon on 2008-11-21
Yeah, I did.  Thanks, that worked for Opera.

Not for Seamonkey, though.  I tried it, but it's still there, and still runs.  It even said it's uninstalled when I tried it again with the purge flag.

---

### Post by taurus on 2008-11-21
Maybe reboot?

---

### Post by liamnixon on 2008-11-21
I just did, but it's still there.  :confused:  I'm not sure what other relevant info I could offer.

I downloaded it through command line w/ 'sudo apt-get.'  Perhaps I could remove the files manually, but when I right-click to delete the folder, the delete and cut options are shadowed.  Besides, I don't want to delete anything important.

Hm...

---

### Post by taurus on 2008-11-21
If you installed it with apt-get, you can remove it with apt-get as well.

```
sudo apt-get remove seamonkey
sudo apt-get autoremove
```

---

### Post by liamnixon on 2008-11-21
When I do 'apt-get remove,' it's still there, and I tried auto-remove, but it wants to uninstall 309 MB, which is a lot more than it installed (90.1 KB).  Maybe this will clear something up.

--------------------------------------------------------

kevinfowler@destroyer:~$ sudo apt-get remove seamonkey
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgtkglext1-ruby python-crypto libstrigiqtdbusclient0 libclucene0ldbl
  libglib1.2ldbl python-twisted-names libarts1c2a wavpack libtwolame0
  libwildmidi0 dvdrip-doc kdelibs4c2a libartsc0 libqt4-opengl liblzo1
  libvte-ruby1.8 libdc1394-22 libglade2-ruby1.8 mppenc libgconf2-ruby librdf0
  kdebase-runtime-data-common libbinio1ldbl libgtk1.2 libgnomevfs2-ruby
  libatk1-ruby libnet-ssleay-perl mplayer-skins python-twisted-web
  libpanel-applet2-ruby libfame-0.9 libgtksourceview1-ruby1.8 libsvga1
  libart2-ruby libgtkhtml2-ruby1.8 libresid-builder0c2a libqt4-sql-mysql
  libqt4-dbus seamonkey-mailnews libxine1-misc-plugins libaldmb1 kdelibs-data
  python-twisted-runner libxcb-xv0 toolame phonon libpvm3 libgtk-mozembed-ruby
  libgtk-mozembed-ruby1.8 liblo0ldbl libqt4-qt3support libatk1-ruby1.8 libdca0
  libgnomevfs2-ruby1.8 libopenspc0 amarok-common
  openoffice.org-hyphenation-en-us liblualib50 ruby-gnome2 libglade2-ruby
  libcddb2 mysql-common libgtkglext1-ruby1.8 libgnome2-ruby1.8
  libgtksourceview1-ruby transcode-doc libpanel-applet2-ruby1.8 libpango1-ruby
  libass1 transfig kde-icons-oxygen libgnomecanvas2-ruby mp3gain vorbisgain
  librasqal0 libglide2 libdvbpsi4 python-utidylib libggi-target-x
  guile-1.8-libs libmysqlclient15off libopengl-ruby1.8 libsoprano4
  redland-utils python-twisted-mail libgnomecanvas2-ruby1.8 libvlc2
  libtidy-0.99-0 libgdk-pixbuf2-ruby ruby libenca0 kdelibs5-data faad libggi2
  seamonkey-chatzilla libqtcore4 libavahi-qt3-1 libevent-rpc-perl
  libgnomecanvasmm-2.6-1c2a libgii1 libxcb-shape0 icedax libgnome2-ruby
  python-twisted-lore libgconf2-ruby1.8 python-twisted-conch freepats
  python-twisted-news python-feedparser python-twisted-words libopengl-ruby
  libgnomeprint2-ruby python-twisted libglib2-ruby1.8 libqt4-sql libifp4 flac
  libqt4-svg libgii1-target-x phonon-backend-gstreamer netpbm libvte-ruby
  libcairo-ruby1.8 pvm anyevent-perl libstreamanalyzer0 libgnomeprintui2-ruby
  libphonon4 libiso9660-5 libfluidsynth1 libqt4-xml libgtkhtml2-ruby
  libgdk-pixbuf2-ruby1.8 libqt4-network libgtk1.2-common libqt4-designer
  libdumb1 libsidplay2 libxvmc1 gocr libqtgui4 libgnomeprint2-ruby1.8
  libgnomemm-2.6-1c2 liblua5.1-0 libgucharmap7 libnetpbm10 libart2-ruby1.8
  libfreeimage3 libgtk2-ruby1.8 libpq5 libgnomeprintui2-ruby1.8
  librsvg2-ruby1.8 libboost-filesystem1.34.1 libstreams0 libraptor1 timidity
  libgmyth0 libmodplug0c2 vlc-data liblrdf0 libgconfmm-2.6-1c2 libtar
  libgtk2-ruby libio-socket-ssl-perl libmcs1 libgnome-vfsmm-2.6-1c2a
  librsvg2-ruby liblua50 libgnomeuimm-2.6-1c2a libqt4-script ladcca2
  libjpeg-progs libvlccore0 libxcb-shm0 python-chardet lame soprano-daemon
  libvcdinfo0 kdebase-runtime-data libebml0 libglademm-2.4-1c2a liballegro4.2
  libpango1-ruby1.8 libmatroska0 libnjb5 libmms0 libneon27-gnutls libiptcdata0
  qt4-qtconfig libavdevice52
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  seamonkey
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 90.1kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 123538 files and directories currently installed.)
Removing seamonkey ...

------------------------------------------------------------------------

kevinfowler@destroyer:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgtkglext1-ruby python-crypto libstrigiqtdbusclient0 libclucene0ldbl
  libglib1.2ldbl python-twisted-names libarts1c2a wavpack libtwolame0
  libwildmidi0 dvdrip-doc kdelibs4c2a libartsc0 libqt4-opengl liblzo1
  libvte-ruby1.8 libdc1394-22 libglade2-ruby1.8 mppenc libgconf2-ruby librdf0
  kdebase-runtime-data-common libbinio1ldbl libgtk1.2 libgnomevfs2-ruby
  libatk1-ruby libnet-ssleay-perl mplayer-skins python-twisted-web
  libpanel-applet2-ruby libfame-0.9 libgtksourceview1-ruby1.8 libsvga1
  libart2-ruby libgtkhtml2-ruby1.8 libresid-builder0c2a libqt4-sql-mysql
  libqt4-dbus seamonkey-mailnews libxine1-misc-plugins libaldmb1 kdelibs-data
  python-twisted-runner libxcb-xv0 toolame phonon libpvm3 libgtk-mozembed-ruby
  libgtk-mozembed-ruby1.8 liblo0ldbl libqt4-qt3support libatk1-ruby1.8 libdca0
  libgnomevfs2-ruby1.8 libopenspc0 amarok-common
  openoffice.org-hyphenation-en-us liblualib50 ruby-gnome2 libglade2-ruby
  libcddb2 mysql-common libgtkglext1-ruby1.8 libgnome2-ruby1.8
  libgtksourceview1-ruby transcode-doc libpanel-applet2-ruby1.8 libpango1-ruby
  libass1 transfig kde-icons-oxygen libgnomecanvas2-ruby mp3gain vorbisgain
  librasqal0 libglide2 libdvbpsi4 python-utidylib libggi-target-x
  guile-1.8-libs libmysqlclient15off libopengl-ruby1.8 libsoprano4
  redland-utils python-twisted-mail libgnomecanvas2-ruby1.8 libvlc2
  libtidy-0.99-0 libgdk-pixbuf2-ruby ruby libenca0 kdelibs5-data faad libggi2
  seamonkey-chatzilla libqtcore4 libavahi-qt3-1 libevent-rpc-perl
  libgnomecanvasmm-2.6-1c2a libgii1 libxcb-shape0 icedax libgnome2-ruby
  python-twisted-lore libgconf2-ruby1.8 python-twisted-conch freepats
  python-twisted-news python-feedparser python-twisted-words libopengl-ruby
  libgnomeprint2-ruby python-twisted libglib2-ruby1.8 libqt4-sql libifp4 flac
  libqt4-svg libgii1-target-x phonon-backend-gstreamer netpbm libvte-ruby
  libcairo-ruby1.8 pvm anyevent-perl libstreamanalyzer0 libgnomeprintui2-ruby
  libphonon4 libiso9660-5 libfluidsynth1 libqt4-xml libgtkhtml2-ruby
  libgdk-pixbuf2-ruby1.8 libqt4-network libgtk1.2-common libqt4-designer
  libdumb1 libsidplay2 libxvmc1 gocr libqtgui4 libgnomeprint2-ruby1.8
  libgnomemm-2.6-1c2 liblua5.1-0 libgucharmap7 libnetpbm10 libart2-ruby1.8
  libfreeimage3 libgtk2-ruby1.8 libpq5 libgnomeprintui2-ruby1.8
  librsvg2-ruby1.8 libboost-filesystem1.34.1 libstreams0 libraptor1 timidity
  libgmyth0 libmodplug0c2 vlc-data liblrdf0 libgconfmm-2.6-1c2 libtar
  libgtk2-ruby libio-socket-ssl-perl libmcs1 libgnome-vfsmm-2.6-1c2a
  librsvg2-ruby liblua50 libgnomeuimm-2.6-1c2a libqt4-script ladcca2
  libjpeg-progs libvlccore0 libxcb-shm0 python-chardet lame soprano-daemon
  libvcdinfo0 kdebase-runtime-data libebml0 libglademm-2.4-1c2a liballegro4.2
  libpango1-ruby1.8 libmatroska0 libnjb5 libmms0 libneon27-gnutls libiptcdata0
  qt4-qtconfig libavdevice52
The following packages will be REMOVED:
  amarok-common anyevent-perl dvdrip-doc faad flac freepats gocr
  guile-1.8-libs icedax kde-icons-oxygen kdebase-runtime-data
  kdebase-runtime-data-common kdelibs-data kdelibs4c2a kdelibs5-data ladcca2
  lame libaldmb1 liballegro4.2 libart2-ruby libart2-ruby1.8 libarts1c2a
  libartsc0 libass1 libatk1-ruby libatk1-ruby1.8 libavahi-qt3-1 libavdevice52
  libbinio1ldbl libboost-filesystem1.34.1 libcairo-ruby1.8 libcddb2
  libclucene0ldbl libdc1394-22 libdca0 libdumb1 libdvbpsi4 libebml0 libenca0
  libevent-rpc-perl libfame-0.9 libfluidsynth1 libfreeimage3 libgconf2-ruby
  libgconf2-ruby1.8 libgconfmm-2.6-1c2 libgdk-pixbuf2-ruby
  libgdk-pixbuf2-ruby1.8 libggi-target-x libggi2 libgii1 libgii1-target-x
  libglade2-ruby libglade2-ruby1.8 libglademm-2.4-1c2a libglib1.2ldbl
  libglib2-ruby1.8 libglide2 libgmyth0 libgnome-vfsmm-2.6-1c2a libgnome2-ruby
  libgnome2-ruby1.8 libgnomecanvas2-ruby libgnomecanvas2-ruby1.8
  libgnomecanvasmm-2.6-1c2a libgnomemm-2.6-1c2 libgnomeprint2-ruby
  libgnomeprint2-ruby1.8 libgnomeprintui2-ruby libgnomeprintui2-ruby1.8
  libgnomeuimm-2.6-1c2a libgnomevfs2-ruby libgnomevfs2-ruby1.8
  libgtk-mozembed-ruby libgtk-mozembed-ruby1.8 libgtk1.2 libgtk1.2-common
  libgtk2-ruby libgtk2-ruby1.8 libgtkglext1-ruby libgtkglext1-ruby1.8
  libgtkhtml2-ruby libgtkhtml2-ruby1.8 libgtksourceview1-ruby
  libgtksourceview1-ruby1.8 libgucharmap7 libifp4 libio-socket-ssl-perl
  libiptcdata0 libiso9660-5 libjpeg-progs liblo0ldbl liblrdf0 liblua5.1-0
  liblua50 liblualib50 liblzo1 libmatroska0 libmcs1 libmms0 libmodplug0c2
  libmysqlclient15off libneon27-gnutls libnet-ssleay-perl libnetpbm10 libnjb5
  libopengl-ruby libopengl-ruby1.8 libopenspc0 libpanel-applet2-ruby
  libpanel-applet2-ruby1.8 libpango1-ruby libpango1-ruby1.8 libphonon4 libpq5
  libpvm3 libqt4-dbus libqt4-designer libqt4-network libqt4-opengl
  libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql libqt4-svg
  libqt4-xml libqtcore4 libqtgui4 libraptor1 librasqal0 librdf0
  libresid-builder0c2a librsvg2-ruby librsvg2-ruby1.8 libsidplay2 libsoprano4
  libstreamanalyzer0 libstreams0 libstrigiqtdbusclient0 libsvga1 libtar
  libtidy-0.99-0 libtwolame0 libvcdinfo0 libvlc2 libvlccore0 libvte-ruby
  libvte-ruby1.8 libwildmidi0 libxcb-shape0 libxcb-shm0 libxcb-xv0
  libxine1-misc-plugins libxvmc1 mp3gain mplayer-skins mppenc mysql-common
  netpbm openoffice.org-hyphenation-en-us phonon phonon-backend-gstreamer pvm
  python-chardet python-crypto python-feedparser python-twisted
  python-twisted-conch python-twisted-lore python-twisted-mail
  python-twisted-names python-twisted-news python-twisted-runner
  python-twisted-web python-twisted-words python-utidylib qt4-qtconfig
  redland-utils ruby ruby-gnome2 seamonkey-chatzilla seamonkey-mailnews
  soprano-daemon timidity toolame transcode-doc transfig vlc-data vorbisgain
  wavpack
0 upgraded, 0 newly installed, 190 to remove and 0 not upgraded.
After this operation, 309MB disk space will be freed.
Do you want to continue [Y/n]?

---

