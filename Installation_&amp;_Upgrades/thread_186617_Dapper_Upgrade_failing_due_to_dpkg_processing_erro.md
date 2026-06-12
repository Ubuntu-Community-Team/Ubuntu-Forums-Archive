---
title: "Dapper Upgrade failing due to dpkg processing errors"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by kahuuna on 2006-06-02
Trying to upgrade ubuntu to dapper on my second box. /etc/apt/sources.list is in ok order. After sudo apt-get update, this is produced:
```
kahuuna@lbx:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  imagemagick irssi-text language-selector librpm4 linux-headers-386 linux-image-386
  linux-restricted-modules-386 lsb mysql-client mysql-server nautilus-sendto python-soappy
  python-twisted python2.4-crypto python2.4-pycurl python2.4-twisted rpm rss-glx serpentine wvdial
The following packages will be upgraded:
  gnome-games gnome-games-data hpijs hplip-ppds libdbd-mysql-perl nautilus postgresql proftpd-common
  proftpd-mysql python-mysqldb python2.4-mysqldb yelp
12 upgraded, 0 newly installed, 0 to remove and 20 not upgraded.
167 not fully installed or removed.
Need to get 0B/6782kB of archives.
After unpacking 4272kB disk space will be freed.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 135437 files and directories currently installed.)
Preparing to replace gnome-games 1:2.12.1-0ubuntu1 (using .../gnome-games_1%3a2.14.1-0ubuntu2_i386.deb) ...
gconftool-2: symbol lookup error: /usr/lib/libgconf-2.so.4: undefined symbol: g_slice_alloc0
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
dpkg: error processing /var/cache/apt/archives/gnome-games_1%3a2.14.1-0ubuntu2_i386.deb (--unpack):
 there is no script in the new version of the package - giving up
Preparing to replace gnome-games-data 1:2.12.1-0ubuntu1 (using .../gnome-games-data_1%3a2.14.1-0ubuntu2_all.deb) ...
Unpacking replacement gnome-games-data ...
dpkg: error processing /var/cache/apt/archives/gnome-games-data_1%3a2.14.1-0ubuntu2_all.deb (--unpack):
 trying to overwrite `/usr/share/gconf/schemas/aisleriot.schemas', which is also in package gnome-games
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-games_1%3a2.14.1-0ubuntu2_i386.deb
 /var/cache/apt/archives/gnome-games-data_1%3a2.14.1-0ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


sudo apt-get dist-upgrade
```
kahuuna@lbx:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  irssi language-selector-common libbeecrypt6 libbtctl2 libcurl3-gnutls libglew1 libgmp3c2 libgnomebt0 libmagick9 libopenobex-1.0-0
  libqt3-mt libuniconf4.2 libwvstreams4.2-base libwvstreams4.2-extras libxplc0.3.13 linux-headers-2.6.15-23 linux-headers-2.6.15-23-386
  linux-image-2.6.15-23-386 linux-restricted-modules-2.6.15-23-386 lsb-desktop mysql-client-5.0 mysql-server-5.0 python-gst0.10
  python-twisted-conch python-twisted-core python-twisted-lore python-twisted-mail python-twisted-names python-twisted-news
  python-twisted-runner python-twisted-web python-twisted-words python2.4-soappy python2.4-twisted-conch python2.4-twisted-core
  python2.4-twisted-lore python2.4-twisted-mail python2.4-twisted-names python2.4-twisted-news python2.4-twisted-runner
  python2.4-twisted-web python2.4-twisted-words
The following packages will be upgraded:
  gnome-games gnome-games-data hpijs hplip-ppds imagemagick irssi-text language-selector libdbd-mysql-perl librpm4 linux-headers-386
  linux-image-386 linux-restricted-modules-386 lsb mysql-client mysql-server nautilus nautilus-sendto postgresql proftpd-common
  proftpd-mysql python-mysqldb python-soappy python-twisted python2.4-crypto python2.4-mysqldb python2.4-pycurl python2.4-twisted rpm
  rss-glx serpentine wvdial yelp
32 upgraded, 42 newly installed, 0 to remove and 0 not upgraded.
167 not fully installed or removed.
Need to get 0B/88,4MB of archives.
After unpacking 237MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 135437 files and directories currently installed.)
Preparing to replace gnome-games 1:2.12.1-0ubuntu1 (using .../gnome-games_1%3a2.14.1-0ubuntu2_i386.deb) ...
gconftool-2: symbol lookup error: /usr/lib/libgconf-2.so.4: undefined symbol: g_slice_alloc0
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
dpkg: error processing /var/cache/apt/archives/gnome-games_1%3a2.14.1-0ubuntu2_i386.deb (--unpack):
 there is no script in the new version of the package - giving up
Preparing to replace gnome-games-data 1:2.12.1-0ubuntu1 (using .../gnome-games-data_1%3a2.14.1-0ubuntu2_all.deb) ...
Unpacking replacement gnome-games-data ...
dpkg: error processing /var/cache/apt/archives/gnome-games-data_1%3a2.14.1-0ubuntu2_all.deb (--unpack):
 trying to overwrite `/usr/share/gconf/schemas/aisleriot.schemas', which is also in package gnome-games
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-games_1%3a2.14.1-0ubuntu2_i386.deb
 /var/cache/apt/archives/gnome-games-data_1%3a2.14.1-0ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Help would be greatly appreciated.

---

### Post by kahuuna on 2006-06-02
And here is sudo apt-get install -f

```
kahuuna@lbx:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 32 not upgraded.
167 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up gconf2 (2.14.0-1ubuntu2) ...
gconf-merge-tree: symbol lookup error: /usr/lib/libgconf-2.so.4: undefined symbol: g_slice_alloc0
dpkg: error processing gconf2 (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of libgnomevfs2-common:
 libgnomevfs2-common depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgnomevfs2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-0:
 libgnomevfs2-0 depends on libgnomevfs2-common (= 2.14.1-0ubuntu8); however:
  Package libgnomevfs2-common is not configured yet.
dpkg: error processing libgnomevfs2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome-menu2:
 libgnome-menu2 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome-menu2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-menus:
 gnome-menus depends on libgnome-menu2; however:
  Package libgnome-menu2 is not configured yet.
 gnome-menus depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing gnome-menus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of alacarte:
 alacarte depends on gnome-menus (>= 2.10); however:
  Package gnome-menus is not configured yet.
dpkg: error processing alacarte (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-common:
 libgnome2-common depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgnome2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-0:
 libgnome2-0 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 libgnome2-0 depends on libgnome2-common (= 2.14.1-0ubuntu2); however:
  Package libgnome2-common is not configured yet.
dpkg: error processing libgnome2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libbonoboui2-0:
 libbonoboui2-0 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libbonoboui2-0 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libbonoboui2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomeui-0:
 libgnomeui-0 depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 libgnomeui-0 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libgnomeui-0 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnomeui-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome-desktop-2:
 libgnome-desktop-2 depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 libgnome-desktop-2 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libgnome-desktop-2 depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 libgnome-desktop-2 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome-desktop-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bug-buddy:
 bug-buddy depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
 bug-buddy depends on libgnome-desktop-2 (>= 2.11.1); however:
  Package libgnome-desktop-2 is not configured yet.
 bug-buddy depends on libgnome-menu2; however:
  Package libgnome-menu2 is not configured yet.
 bug-buddy depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 bug-buddy depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 bug-buddy depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing bug-buddy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of capplets-data:
 capplets-data depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing capplets-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libebook1.2-5:
 libebook1.2-5 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libebook1.2-5 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libebook1.2-5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpanel-applet2-0:
 libpanel-applet2-0 depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 libpanel-applet2-0 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libpanel-applet2-0 depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 libpanel-applet2-0 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libpanel-applet2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of contact-lookup-applet:
 contact-lookup-applet depends on libebook1.2-5 (>= 1.6.1); however:
  Package libebook1.2-5 is not configured yet.
 contact-lookup-applet depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 contact-lookup-applet depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 contact-lookup-applet depends on libpanel-applet2-0 (>= 2.14.1); however:
  Package libpanel-applet2-0 is not configured yet.
dpkg: error processing contact-lookup-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gstreamer0.10-plugins-good:
 gstreamer0.10-plugins-good depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing gstreamer0.10-plugins-good (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-media:
 gnome-media depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 gnome-media depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 gnome-media depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 gnome-media depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 gnome-media depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
 gnome-media depends on gstreamer0.10-plugins-good; however:
  Package gstreamer0.10-plugins-good is not configured yet.
dpkg: error processing gnome-media (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libtotem-plparser1:
 libtotem-plparser1 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libtotem-plparser1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.4-gnome2-desktop:
 python2.4-gnome2-desktop depends on gnome-media; however:
  Package gnome-media is not configured yet.
 python2.4-gnome2-desktop depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 python2.4-gnome2-desktop depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 python2.4-gnome2-desktop depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 python2.4-gnome2-desktop depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 python2.4-gnome2-desktop depends on libpanel-applet2-0 (>= 2.14.0); however:
  Package libpanel-applet2-0 is not configured yet.
 python2.4-gnome2-desktop depends on libtotem-plparser1; however:
  Package libtotem-plparser1 is not configured yet.
dpkg: error processing python2.4-gnome2-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2-desktop:
 python-gnome2-desktop depends on python2.4-gnome2-desktop; however:
  Package python2.4-gnome2-desktop is not configured yet.
dpkg: error processing python-gnome2-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of deskbar-applet:
 deskbar-applet depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 deskbar-applet depends on libebook1.2-5 (>= 1.6.1); however:
  Package libebook1.2-5 is not configured yet.
 deskbar-applet depends on libgnome-desktop-2 (>= 2.11.1); however:
  Package libgnome-desktop-2 is not configured yet.
 deskbar-applet depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 deskbar-applet depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 deskbar-applet depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 deskbar-applet depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
 deskbar-applet depends on python-gnome2-desktop; however:
  Package python-gnome2-desktop is not configured yet.
dpkg: error processing deskbar-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eog:
 eog depends on libgnome-desktop-2 (>= 2.11.1); however:
  Package libgnome-desktop-2 is not configured yet.
 eog depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 eog depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 eog depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 eog depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing eog (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnautilus-extension1:
 libnautilus-extension1 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libnautilus-extension1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evince:
 evince depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 evince depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 evince depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 evince depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 evince depends on libnautilus-extension1 (>= 2.13.1); however:
  Package libnautilus-extension1 is not configured yet.
 evince depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing evince (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtkhtml3.8-15:
 libgtkhtml3.8-15 depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 libgtkhtml3.8-15 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libgtkhtml3.8-15 depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 libgtkhtml3.8-15 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgtkhtml3.8-15 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gtkhtml3.8:
 gtkhtml3.8 depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 gtkhtml3.8 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 gtkhtml3.8 depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 gtkhtml3.8 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 gtkhtml3.8 depends on libgtkhtml3.8-15 (>= 3.10.1); however:
  Package libgtkhtml3.8-15 is not configured yet.
dpkg: error processing gtkhtml3.8 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libecal1.2-3:
 libecal1.2-3 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libecal1.2-3 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libecal1.2-3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedataserverui1.2-6:
 libedataserverui1.2-6 depends on libebook1.2-5 (>= 1.6.1); however:
  Package libebook1.2-5 is not configured yet.
 libedataserverui1.2-6 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libedataserverui1.2-6 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libedataserverui1.2-6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of liblpint-bonobo0:
 liblpint-bonobo0 depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 liblpint-bonobo0 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 liblpint-bonobo0 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing liblpint-bonobo0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedata-book1.2-2:
 libedata-book1.2-2 depends on libebook1.2-5 (>= 1.6.1); however:
  Package libebook1.2-5 is not configured yet.
 libedata-book1.2-2 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libedata-book1.2-2 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libedata-book1.2-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedata-cal1.2-1:
 libedata-cal1.2-1 depends on libecal1.2-3 (>= 1.6.1); however:
  Package libecal1.2-3 is not configured yet.
 libedata-cal1.2-1 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libedata-cal1.2-1 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libedata-cal1.2-1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-data-server:
 evolution-data-server depends on libebook1.2-5 (>= 1.6.1); however:
  Package libebook1.2-5 is not configured yet.
 evolution-data-server depends on libecal1.2-3 (>= 1.6.1); however:
  Package libecal1.2-3 is not configured yet.
 evolution-data-server depends on libedata-book1.2-2 (>= 1.6.1); however:
  Package libedata-book1.2-2 is not configured yet.
 evolution-data-server depends on libedata-cal1.2-1 (>= 1.6.1); however:
  Package libedata-cal1.2-1 is not configured yet.
 evolution-data-server depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 evolution-data-server depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing evolution-data-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on gtkhtml3.8 (>= 3.8.0); however:
  Package gtkhtml3.8 is not configured yet.
 evolution depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 evolution depends on libebook1.2-5 (>= 1.6.1); however:
  Package libebook1.2-5 is not configured yet.
 evolution depends on libecal1.2-3 (>= 1.6.1); however:
  Package libecal1.2-3 is not configured yet.
 evolution depends on libedataserverui1.2-6 (>= 1.6.1); however:
  Package libedataserverui1.2-6 is not configured yet.
 evolution depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 evolution depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 evolution depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 evolution depends on libgtkhtml3.8-15 (>= 3.10.1); however:
  Package libgtkhtml3.8-15 is not configured yet.
 evolution depends on liblpint-bonobo0; however:
  Package liblpint-bonobo0 is not configured yet.
 evolution depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
 evolution depends on evolution-data-server (>= 1.5.5); however:
  Package evolution-data-server is not configured yet.
dpkg: error processing evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libexchange-storage1.2-1:
 libexchange-storage1.2-1 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libexchange-storage1.2-1 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libexchange-storage1.2-1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-exchange:
 evolution-exchange depends on evolution (>= 2.6.1); however:
  Package evolution is not configured yet.
 evolution-exchange depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 evolution-exchange depends on libebook1.2-5 (>= 1.6.1); however:
  Package libebook1.2-5 is not configured yet.
 evolution-exchange depends on libecal1.2-3 (>= 1.6.1); however:
  Package libecal1.2-3 is not configured yet.
 evolution-exchange depends on libedata-book1.2-2 (>= 1.6.1); however:
  Package libedata-book1.2-2 is not configured yet.
 evolution-exchange depends on libedata-cal1.2-1 (>= 1.6.1); however:
  Package libedata-cal1.2-1 is not configured yet.
 evolution-exchange depends on libedataserverui1.2-6 (>= 1.6.1); however:
  Package libedataserverui1.2-6 is not configured yet.
 evolution-exchange depends on libexchange-storage1.2-1 (>= 1.6.1); however:
  Package libexchange-storage1.2-1 is not configured yet.
 evolution-exchange depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 evolution-exchange depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 evolution-exchange depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 evolution-exchange depends on libgtkhtml3.8-15 (>= 3.10.1); however:
  Package libgtkhtml3.8-15 is not configured yet.
 evolution-exchange depends on liblpint-bonobo0; however:
  Package liblpint-bonobo0 is not configured yet.
dpkg: error processing evolution-exchange (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-plugins:
 evolution-plugins depends on evolution (= 2.6.1-0ubuntu7); however:
  Package evolution is not configured yet.
 evolution-plugins depends on evolution (>= 2.6.1); however:
  Package evolution is not configured yet.
 evolution-plugins depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 evolution-plugins depends on libebook1.2-5 (>= 1.6.1); however:
  Package libebook1.2-5 is not configured yet.
 evolution-plugins depends on libecal1.2-3 (>= 1.6.1); however:
  Package libecal1.2-3 is not configured yet.
 evolution-plugins depends on libedataserverui1.2-6 (>= 1.6.1); however:
  Package libedataserverui1.2-6 is not configured yet.
 evolution-plugins depends on libexchange-storage1.2-1 (>= 1.6.1); however:
  Package libexchange-storage1.2-1 is not configured yet.
 evolution-plugins depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 evolution-plugins depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 evolution-plugins depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 evolution-plugins depends on libgtkhtml3.8-15 (>= 3.10.1); however:
  Package libgtkhtml3.8-15 is not configured yet.
dpkg: error processing evolution-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-webcal:
 evolution-webcal depends on libecal1.2-3 (>= 1.6.1); however:
  Package libecal1.2-3 is not configured yet.
 evolution-webcal depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 evolution-webcal depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
dpkg: error processing evolution-webcal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of file-roller:
 file-roller depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 file-roller depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 file-roller depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 file-roller depends on libnautilus-extension1 (>= 2.13.1); however:
  Package libnautilus-extension1 is not configured yet.
 file-roller depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing file-roller (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 firefox-gnome-support depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 firefox-gnome-support depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 firefox-gnome-support depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gcalctool:
 gcalctool depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 gcalctool depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 gcalctool depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 gcalctool depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 gcalctool depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing gcalctool (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gconf-editor:
 gconf-editor depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 gconf-editor depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 gconf-editor depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing gconf-editor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 gnome-control-center depends on libebook1.2-5 (>= 1.6.1); however:
  Package libebook1.2-5 is not configured yet.
 gnome-control-center depends on libgnome-desktop-2 (>= 2.11.1); however:
  Package libgnome-desktop-2 is not configured yet.
 gnome-control-center depends on libgnome-menu2; however:
  Package libgnome-menu2 is not configured yet.
 gnome-control-center depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 gnome-control-center depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 gnome-control-center depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 gnome-control-center depends on libnautilus-extension1 (>= 2.13.1); however:
  Package libnautilus-extension1 is not configured yet.
 gnome-control-center depends on capplets-data (= 1:2.14.1-0ubuntu11); 
```

---

### Post by kahuuna on 2006-06-02
continued
```
however:
  Package capplets-data is not configured yet.
 gnome-control-center depends on gnome-menus; however:
  Package gnome-menus is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of notification-daemon:
 notification-daemon depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing notification-daemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-power-manager:
 gnome-power-manager depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 gnome-power-manager depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 gnome-power-manager depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 gnome-power-manager depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 gnome-power-manager depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
 gnome-power-manager depends on notification-daemon; however:
  Package notification-daemon is not configured yet.
dpkg: error processing gnome-power-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session:
 gnome-session depends on libgnome-desktop-2 (>= 2.11.1); however:
  Package libgnome-desktop-2 is not configured yet.
 gnome-session depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 gnome-session depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 gnome-session depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
 gnome-session depends on gnome-control-center (>= 2.6); however:
  Package gnome-control-center is not configured yet.
 gnome-session depends on gnome-power-manager; however:
  Package gnome-power-manager is not configured yet.
dpkg: error processing gnome-session (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of metacity:
 metacity depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing metacity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-terminal-data:
 gnome-terminal-data depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-terminal-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-terminal:
 gnome-terminal depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 gnome-terminal depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 gnome-terminal depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 gnome-terminal depends on gnome-control-center (>= 1:2.8.0); however:
  Package gnome-control-center is not configured yet.
 gnome-terminal depends on gnome-terminal-data (= 2.14.1-0ubuntu1); 

however:
  Package gnome-terminal-data is not configured yet.
dpkg: error processing gnome-terminal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gksu:
 gksu depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing gksu (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gdm:
 gdm depends on gksu (>= 1.0.7); however:
  Package gksu is not configured yet.
dpkg: error processing gdm (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Errors were encountered while processing:
 gconf2
 libgnomevfs2-common
 libgnomevfs2-0
 libgnome-menu2
 gnome-menus
 alacarte
 libgnome2-common
 libgnome2-0
 libbonoboui2-0
 libgnomeui-0
 libgnome-desktop-2
 bug-buddy
 capplets-data
 libebook1.2-5
 libpanel-applet2-0
 contact-lookup-applet
 gstreamer0.10-plugins-good
 gnome-media
 libtotem-plparser1
 python2.4-gnome2-desktop
 python-gnome2-desktop
 deskbar-applet
 eog
 libnautilus-extension1
 evince
 libgtkhtml3.8-15
 gtkhtml3.8
 libecal1.2-3
 libedataserverui1.2-6
 liblpint-bonobo0
 libedata-book1.2-2
 libedata-cal1.2-1
 evolution-data-server
 evolution
 libexchange-storage1.2-1
 evolution-exchange
 evolution-plugins
 evolution-webcal
 file-roller
 firefox-gnome-support
 gcalctool
 gconf-editor
 gnome-control-center
 notification-daemon
 gnome-power-manager
 gnome-session
 metacity
 gnome-terminal-data
 gnome-terminal
 gksu
 gdm
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by barbarian on 2006-06-02
Hi,
try *sudo apt-get -f install*

---

### Post by kahuuna on 2006-06-02
```
kahuuna@lbx:~$ sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 32 not upgraded.
167 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up gconf2 (2.14.0-1ubuntu2) ...
gconf-merge-tree: symbol lookup error: /usr/lib/libgconf-2.so.4: undefined symbol: g_slice_alloc0
dpkg: error processing gconf2 (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of libgnomevfs2-common:
 libgnomevfs2-common depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgnomevfs2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-0:
 libgnomevfs2-0 depends on libgnomevfs2-common (= 2.14.1-0ubuntu8); however:
  Package libgnomevfs2-common is not configured yet.
dpkg: error processing libgnomevfs2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome-menu2:
 libgnome-menu2 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome-menu2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-menus:
 gnome-menus depends on libgnome-menu2; however:
  Package libgnome-menu2 is not configured yet.
 gnome-menus depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing gnome-menus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of alacarte:
 alacarte depends on gnome-menus (>= 2.10); however:
  Package gnome-menus is not configured yet.
dpkg: error processing alacarte (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-common:
 libgnome2-common depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgnome2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-0:
 libgnome2-0 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 libgnome2-0 depends on libgnome2-common (= 2.14.1-0ubuntu2); however:
  Package libgnome2-common is not configured yet.
dpkg: error processing libgnome2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libbonoboui2-0:
 libbonoboui2-0 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libbonoboui2-0 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libbonoboui2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomeui-0:
 libgnomeui-0 depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 libgnomeui-0 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libgnomeui-0 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnomeui-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome-desktop-2:
 libgnome-desktop-2 depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 libgnome-desktop-2 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libgnome-desktop-2 depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 libgnome-desktop-2 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome-desktop-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bug-buddy:
 bug-buddy depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
 bug-buddy depends on libgnome-desktop-2 (>= 2.11.1); however:
  Package libgnome-desktop-2 is not configured yet.
 bug-buddy depends on libgnome-menu2; however:
  Package libgnome-menu2 is not configured yet.
 bug-buddy depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 bug-buddy depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 bug-buddy depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing bug-buddy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of capplets-data:
 capplets-data depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing capplets-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libebook1.2-5:
 libebook1.2-5 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libebook1.2-5 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libebook1.2-5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpanel-applet2-0:
 libpanel-applet2-0 depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 libpanel-applet2-0 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libpanel-applet2-0 depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 libpanel-applet2-0 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libpanel-applet2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of contact-lookup-applet:
 contact-lookup-applet depends on libebook1.2-5 (>= 1.6.1); however:
  Package libebook1.2-5 is not configured yet.
 contact-lookup-applet depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 contact-lookup-applet depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 contact-lookup-applet depends on libpanel-applet2-0 (>= 2.14.1); however:
  Package libpanel-applet2-0 is not configured yet.
dpkg: error processing contact-lookup-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gstreamer0.10-plugins-good:
 gstreamer0.10-plugins-good depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing gstreamer0.10-plugins-good (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-media:
 gnome-media depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 gnome-media depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 gnome-media depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 gnome-media depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 gnome-media depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
 gnome-media depends on gstreamer0.10-plugins-good; however:
  Package gstreamer0.10-plugins-good is not configured yet.
dpkg: error processing gnome-media (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libtotem-plparser1:
 libtotem-plparser1 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libtotem-plparser1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.4-gnome2-desktop:
 python2.4-gnome2-desktop depends on gnome-media; however:
  Package gnome-media is not configured yet.
 python2.4-gnome2-desktop depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 python2.4-gnome2-desktop depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 python2.4-gnome2-desktop depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 python2.4-gnome2-desktop depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 python2.4-gnome2-desktop depends on libpanel-applet2-0 (>= 2.14.0); however:
  Package libpanel-applet2-0 is not configured yet.
 python2.4-gnome2-desktop depends on libtotem-plparser1; however:
  Package libtotem-plparser1 is not configured yet.
dpkg: error processing python2.4-gnome2-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2-desktop:
 python-gnome2-desktop depends on python2.4-gnome2-desktop; however:
  Package python2.4-gnome2-desktop is not configured yet.
dpkg: error processing python-gnome2-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of deskbar-applet:
 deskbar-applet depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 deskbar-applet depends on libebook1.2-5 (>= 1.6.1); however:
  Package libebook1.2-5 is not configured yet.
 deskbar-applet depends on libgnome-desktop-2 (>= 2.11.1); however:
  Package libgnome-desktop-2 is not configured yet.
 deskbar-applet depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 deskbar-applet depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 deskbar-applet depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 deskbar-applet depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
 deskbar-applet depends on python-gnome2-desktop; however:
  Package python-gnome2-desktop is not configured yet.
dpkg: error processing deskbar-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eog:
 eog depends on libgnome-desktop-2 (>= 2.11.1); however:
  Package libgnome-desktop-2 is not configured yet.
 eog depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 eog depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 eog depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 eog depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing eog (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnautilus-extension1:
 libnautilus-extension1 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libnautilus-extension1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evince:
 evince depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 evince depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 evince depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 evince depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 evince depends on libnautilus-extension1 (>= 2.13.1); however:
  Package libnautilus-extension1 is not configured yet.
 evince depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing evince (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtkhtml3.8-15:
 libgtkhtml3.8-15 depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 libgtkhtml3.8-15 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libgtkhtml3.8-15 depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 libgtkhtml3.8-15 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgtkhtml3.8-15 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gtkhtml3.8:
 gtkhtml3.8 depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 gtkhtml3.8 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 gtkhtml3.8 depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 gtkhtml3.8 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 gtkhtml3.8 depends on libgtkhtml3.8-15 (>= 3.10.1); however:
  Package libgtkhtml3.8-15 is not configured yet.
dpkg: error processing gtkhtml3.8 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libecal1.2-3:
 libecal1.2-3 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libecal1.2-3 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libecal1.2-3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedataserverui1.2-6:
 libedataserverui1.2-6 depends on libebook1.2-5 (>= 1.6.1); however:
  Package libebook1.2-5 is not configured yet.
 libedataserverui1.2-6 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libedataserverui1.2-6 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libedataserverui1.2-6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of liblpint-bonobo0:
 liblpint-bonobo0 depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 liblpint-bonobo0 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 liblpint-bonobo0 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing liblpint-bonobo0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedata-book1.2-2:
 libedata-book1.2-2 depends on libebook1.2-5 (>= 1.6.1); however:
  Package libebook1.2-5 is not configured yet.
 libedata-book1.2-2 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libedata-book1.2-2 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libedata-book1.2-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedata-cal1.2-1:
 libedata-cal1.2-1 depends on libecal1.2-3 (>= 1.6.1); however:
  Package libecal1.2-3 is not configured yet.
 libedata-cal1.2-1 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libedata-cal1.2-1 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libedata-cal1.2-1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-data-server:
 evolution-data-server depends on libebook1.2-5 (>= 1.6.1); however:
  Package libebook1.2-5 is not configured yet.
 evolution-data-server depends on libecal1.2-3 (>= 1.6.1); however:
  Package libecal1.2-3 is not configured yet.
 evolution-data-server depends on libedata-book1.2-2 (>= 1.6.1); however:
  Package libedata-book1.2-2 is not configured yet.
 evolution-data-server depends on libedata-cal1.2-1 (>= 1.6.1); however:
  Package libedata-cal1.2-1 is not configured yet.
 evolution-data-server depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 evolution-data-server depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing evolution-data-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on gtkhtml3.8 (>= 3.8.0); however:
  Package gtkhtml3.8 is not configured yet.
 evolution depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 evolution depends on libebook1.2-5 (>= 1.6.1); however:
  Package libebook1.2-5 is not configured yet.
 evolution depends on libecal1.2-3 (>= 1.6.1); however:
  Package libecal1.2-3 is not configured yet.
 evolution depends on libedataserverui1.2-6 (>= 1.6.1); however:
  Package libedataserverui1.2-6 is not configured yet.
 evolution depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 evolution depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 evolution depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 evolution depends on libgtkhtml3.8-15 (>= 3.10.1); however:
  Package libgtkhtml3.8-15 is not configured yet.
 evolution depends on liblpint-bonobo0; however:
  Package liblpint-bonobo0 is not configured yet.
 evolution depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
 evolution depends on evolution-data-server (>= 1.5.5); however:
  Package evolution-data-server is not configured yet.
dpkg: error processing evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libexchange-storage1.2-1:
 libexchange-storage1.2-1 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libexchange-storage1.2-1 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libexchange-storage1.2-1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-exchange:
 evolution-exchange depends on evolution (>= 2.6.1); however:
  Package evolution is not configured yet.
 evolution-exchange depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 evolution-exchange depends on libebook1.2-5 (>= 1.6.1); however:
  Package libebook1.2-5 is not configured yet.
 evolution-exchange depends on libecal1.2-3 (>= 1.6.1); however:
  Package libecal1.2-3 is not configured yet.
 evolution-exchange depends on libedata-book1.2-2 (>= 1.6.1); however:
  Package libedata-book1.2-2 is not configured yet.
 evolution-exchange depends on libedata-cal1.2-1 (>= 1.6.1); however:
  Package libedata-cal1.2-1 is not configured yet.
 evolution-exchange depends on libedataserverui1.2-6 (>= 1.6.1); however:
  Package libedataserverui1.2-6 is not configured yet.
 evolution-exchange depends on libexchange-storage1.2-1 (>= 1.6.1); however:
  Package libexchange-storage1.2-1 is not configured yet.
 evolution-exchange depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 evolution-exchange depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 evolution-exchange depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 evolution-exchange depends on libgtkhtml3.8-15 (>= 3.10.1); however:
  Package libgtkhtml3.8-15 is not configured yet.
 evolution-exchange depends on liblpint-bonobo0; however:
  Package liblpint-bonobo0 is not configured yet.
dpkg: error processing evolution-exchange (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-plugins:
 evolution-plugins depends on evolution (= 2.6.1-0ubuntu7); however:
  Package evolution is not configured yet.
 evolution-plugins depends on evolution (>= 2.6.1); however:
  Package evolution is not configured yet.
 evolution-plugins depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 
```

---

### Post by kahuuna on 2006-06-02
continued
```
evolution-plugins depends on libebook1.2-5 (>= 1.6.1); however:
  Package libebook1.2-5 is not configured yet.
 evolution-plugins depends on libecal1.2-3 (>= 1.6.1); however:
  Package libecal1.2-3 is not configured yet.
 evolution-plugins depends on libedataserverui1.2-6 (>= 1.6.1); however:
  Package libedataserverui1.2-6 is not configured yet.
 evolution-plugins depends on libexchange-storage1.2-1 (>= 1.6.1); however:
  Package libexchange-storage1.2-1 is not configured yet.
 evolution-plugins depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 evolution-plugins depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 evolution-plugins depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 evolution-plugins depends on libgtkhtml3.8-15 (>= 3.10.1); however:
  Package libgtkhtml3.8-15 is not configured yet.
dpkg: error processing evolution-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-webcal:
 evolution-webcal depends on libecal1.2-3 (>= 1.6.1); however:
  Package libecal1.2-3 is not configured yet.
 evolution-webcal depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 evolution-webcal depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
dpkg: error processing evolution-webcal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of file-roller:
 file-roller depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 file-roller depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 file-roller depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 file-roller depends on libnautilus-extension1 (>= 2.13.1); however:
  Package libnautilus-extension1 is not configured yet.
 file-roller depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing file-roller (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 firefox-gnome-support depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 firefox-gnome-support depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 firefox-gnome-support depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gcalctool:
 gcalctool depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 gcalctool depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 gcalctool depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 gcalctool depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 gcalctool depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing gcalctool (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gconf-editor:
 gconf-editor depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 gconf-editor depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 gconf-editor depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing gconf-editor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 gnome-control-center depends on libebook1.2-5 (>= 1.6.1); however:
  Package libebook1.2-5 is not configured yet.
 gnome-control-center depends on libgnome-desktop-2 (>= 2.11.1); however:
  Package libgnome-desktop-2 is not configured yet.
 gnome-control-center depends on libgnome-menu2; however:
  Package libgnome-menu2 is not configured yet.
 gnome-control-center depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 gnome-control-center depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 gnome-control-center depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 gnome-control-center depends on libnautilus-extension1 (>= 2.13.1); however:
  Package libnautilus-extension1 is not configured yet.
 gnome-control-center depends on capplets-data (= 1:2.14.1-0ubuntu11); however:
  Package capplets-data is not configured yet.
 gnome-control-center depends on gnome-menus; however:
  Package gnome-menus is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of notification-daemon:
 notification-daemon depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing notification-daemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-power-manager:
 gnome-power-manager depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 gnome-power-manager depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 gnome-power-manager depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 gnome-power-manager depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 gnome-power-manager depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
 gnome-power-manager depends on notification-daemon; however:
  Package notification-daemon is not configured yet.
dpkg: error processing gnome-power-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session:
 gnome-session depends on libgnome-desktop-2 (>= 2.11.1); however:
  Package libgnome-desktop-2 is not configured yet.
 gnome-session depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 gnome-session depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 gnome-session depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
 gnome-session depends on gnome-control-center (>= 2.6); however:
  Package gnome-control-center is not configured yet.
 gnome-session depends on gnome-power-manager; however:
  Package gnome-power-manager is not configured yet.
dpkg: error processing gnome-session (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of metacity:
 metacity depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing metacity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-terminal-data:
 gnome-terminal-data depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-terminal-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-terminal:
 gnome-terminal depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 gnome-terminal depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 gnome-terminal depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 gnome-terminal depends on gnome-control-center (>= 1:2.8.0); however:
  Package gnome-control-center is not configured yet.
 gnome-terminal depends on gnome-terminal-data (= 2.14.1-0ubuntu1); however:
  Package gnome-terminal-data is not configured yet.
dpkg: error processing gnome-terminal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gksu:
 gksu depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing gksu (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gdm:
 gdm depends on gksu (>= 1.0.7); however:
  Package gksu is not configured yet.
dpkg: error processing gdm (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Errors were encountered while processing:
 gconf2
 libgnomevfs2-common
 libgnomevfs2-0
 libgnome-menu2
 gnome-menus
 alacarte
 libgnome2-common
 libgnome2-0
 libbonoboui2-0
 libgnomeui-0
 libgnome-desktop-2
 bug-buddy
 capplets-data
 libebook1.2-5
 libpanel-applet2-0
 contact-lookup-applet
 gstreamer0.10-plugins-good
 gnome-media
 libtotem-plparser1
 python2.4-gnome2-desktop
 python-gnome2-desktop
 deskbar-applet
 eog
 libnautilus-extension1
 evince
 libgtkhtml3.8-15
 gtkhtml3.8
 libecal1.2-3
 libedataserverui1.2-6
 liblpint-bonobo0
 libedata-book1.2-2
 libedata-cal1.2-1
 evolution-data-server
 evolution
 libexchange-storage1.2-1
 evolution-exchange
 evolution-plugins
 evolution-webcal
 file-roller
 firefox-gnome-support
 gcalctool
 gconf-editor
 gnome-control-center
 notification-daemon
 gnome-power-manager
 gnome-session
 metacity
 gnome-terminal-data
 gnome-terminal
 gksu
 gdm
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by barbarian on 2006-06-02
yee dependencies..

post your sources list please.

---

### Post by kahuuna on 2006-06-02
```
deb http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ca.archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
#deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
#deb http://security.ubuntu.com/ubuntu dapper-security universe
#deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

---

### Post by barbarian on 2006-06-02
Do you have ubuntu-desktop installed?

[I]sudo aptitude update
sudo aptitude install ubuntu-desktop[/I]

---

### Post by kahuuna on 2006-06-02
Was already installed, but here's what happened:
```
kahuuna@lbx:~$ sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 31 not upgraded.
213 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up gconf2 (2.14.0-1ubuntu2) ...
gconf-merge-tree: symbol lookup error: /usr/lib/libgconf-2.so.4: undefined symbol: g_slice_alloc0
dpkg: error processing gconf2 (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of libgnomevfs2-common:
 libgnomevfs2-common depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgnomevfs2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-0:
 libgnomevfs2-0 depends on libgnomevfs2-common (= 2.14.1-0ubuntu8); however:
  Package libgnomevfs2-common is not configured yet.
dpkg: error processing libgnomevfs2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome-menu2:
 libgnome-menu2 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome-menu2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-menus:
 gnome-menus depends on libgnome-menu2; however:
  Package libgnome-menu2 is not configured yet.
 gnome-menus depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing gnome-menus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of alacarte:
 alacarte depends on gnome-menus (>= 2.10); however:
  Package gnome-menus is not configured yet.
dpkg: error processing alacarte (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-common:
 libgnome2-common depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgnome2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-0:
 libgnome2-0 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 libgnome2-0 depends on libgnome2-common (= 2.14.1-0ubuntu2); however:
  Package libgnome2-common is not configured yet.
dpkg: error processing libgnome2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libbonoboui2-0:
 libbonoboui2-0 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libbonoboui2-0 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libbonoboui2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomeui-0:
 libgnomeui-0 depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 libgnomeui-0 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libgnomeui-0 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnomeui-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome-desktop-2:
 libgnome-desktop-2 depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 libgnome-desktop-2 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libgnome-desktop-2 depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 libgnome-desktop-2 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome-desktop-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bug-buddy:
 bug-buddy depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
 bug-buddy depends on libgnome-desktop-2 (>= 2.11.1); however:
  Package libgnome-desktop-2 is not configured yet.
 bug-buddy depends on libgnome-menu2; however:
  Package libgnome-menu2 is not configured yet.
 bug-buddy depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 bug-buddy depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 bug-buddy depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing bug-buddy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of capplets-data:
 capplets-data depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing capplets-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libebook1.2-5:
 libebook1.2-5 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libebook1.2-5 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libebook1.2-5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpanel-applet2-0:
 libpanel-applet2-0 depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 libpanel-applet2-0 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libpanel-applet2-0 depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 libpanel-applet2-0 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libpanel-applet2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of contact-lookup-applet:
 contact-lookup-applet depends on libebook1.2-5 (>= 1.6.1); however:
  Package libebook1.2-5 is not configured yet.
 contact-lookup-applet depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 contact-lookup-applet depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 contact-lookup-applet depends on libpanel-applet2-0 (>= 2.14.1); however:
  Package libpanel-applet2-0 is not configured yet.
dpkg: error processing contact-lookup-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gstreamer0.10-plugins-good:
 gstreamer0.10-plugins-good depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing gstreamer0.10-plugins-good (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-media:
 gnome-media depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 gnome-media depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 gnome-media depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 gnome-media depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 gnome-media depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
 gnome-media depends on gstreamer0.10-plugins-good; however:
  Package gstreamer0.10-plugins-good is not configured yet.
dpkg: error processing gnome-media (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libtotem-plparser1:
 libtotem-plparser1 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libtotem-plparser1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.4-gnome2-desktop:
 python2.4-gnome2-desktop depends on gnome-media; however:
  Package gnome-media is not configured yet.
 python2.4-gnome2-desktop depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 python2.4-gnome2-desktop depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 python2.4-gnome2-desktop depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 python2.4-gnome2-desktop depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 python2.4-gnome2-desktop depends on libpanel-applet2-0 (>= 2.14.0); however:
  Package libpanel-applet2-0 is not configured yet.
 python2.4-gnome2-desktop depends on libtotem-plparser1; however:
  Package libtotem-plparser1 is not configured yet.
dpkg: error processing python2.4-gnome2-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2-desktop:
 python-gnome2-desktop depends on python2.4-gnome2-desktop; however:
  Package python2.4-gnome2-desktop is not configured yet.
dpkg: error processing python-gnome2-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of deskbar-applet:
 deskbar-applet depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 deskbar-applet depends on libebook1.2-5 (>= 1.6.1); however:
  Package libebook1.2-5 is not configured yet.
 deskbar-applet depends on libgnome-desktop-2 (>= 2.11.1); however:
  Package libgnome-desktop-2 is not configured yet.
 deskbar-applet depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 deskbar-applet depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 deskbar-applet depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 deskbar-applet depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
 deskbar-applet depends on python-gnome2-desktop; however:
  Package python-gnome2-desktop is not configured yet.
dpkg: error processing deskbar-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libecal1.2-3:
 libecal1.2-3 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libecal1.2-3 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libecal1.2-3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedata-book1.2-2:
 libedata-book1.2-2 depends on libebook1.2-5 (>= 1.6.1); however:
  Package libebook1.2-5 is not configured yet.
 libedata-book1.2-2 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libedata-book1.2-2 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libedata-book1.2-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedata-cal1.2-1:
 libedata-cal1.2-1 depends on libecal1.2-3 (>= 1.6.1); however:
  Package libecal1.2-3 is not configured yet.
 libedata-cal1.2-1 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libedata-cal1.2-1 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libedata-cal1.2-1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-data-server:
 evolution-data-server depends on libebook1.2-5 (>= 1.6.1); however:
  Package libebook1.2-5 is not configured yet.
 evolution-data-server depends on libecal1.2-3 (>= 1.6.1); however:
  Package libecal1.2-3 is not configured yet.
 evolution-data-server depends on libedata-book1.2-2 (>= 1.6.1); however:
  Package libedata-book1.2-2 is not configured yet.
 evolution-data-server depends on libedata-cal1.2-1 (>= 1.6.1); however:
  Package libedata-cal1.2-1 is not configured yet.
 evolution-data-server depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 evolution-data-server depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing evolution-data-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ekiga:
 ekiga depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 ekiga depends on libebook1.2-5 (>= 1.6.1); however:
  Package libebook1.2-5 is not configured yet.
 ekiga depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 ekiga depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 ekiga depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 ekiga depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
 ekiga depends on evolution-data-server; however:
  Package evolution-data-server is not configured yet.
dpkg: error processing ekiga (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eog:
 eog depends on libgnome-desktop-2 (>= 2.11.1); however:
  Package libgnome-desktop-2 is not configured yet.
 eog depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 eog depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 eog depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 eog depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing eog (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnautilus-extension1:
 libnautilus-extension1 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libnautilus-extension1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evince:
 evince depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 evince depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 evince depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 evince depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 evince depends on libnautilus-extension1 (>= 2.13.1); however:
  Package libnautilus-extension1 is not configured yet.
 evince depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing evince (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtkhtml3.8-15:
 libgtkhtml3.8-15 depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 libgtkhtml3.8-15 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libgtkhtml3.8-15 depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 libgtkhtml3.8-15 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgtkhtml3.8-15 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gtkhtml3.8:
 gtkhtml3.8 depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 gtkhtml3.8 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 gtkhtml3.8 depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 gtkhtml3.8 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 gtkhtml3.8 depends on libgtkhtml3.8-15 (>= 3.10.1); however:
  Package libgtkhtml3.8-15 is not configured yet.
dpkg: error processing gtkhtml3.8 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedataserverui1.2-6:
 libedataserverui1.2-6 depends on libebook1.2-5 (>= 1.6.1); however:
  Package libebook1.2-5 is not configured yet.
 libedataserverui1.2-6 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libedataserverui1.2-6 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libedataserverui1.2-6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of liblpint-bonobo0:
 liblpint-bonobo0 depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 liblpint-bonobo0 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 liblpint-bonobo0 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing liblpint-bonobo0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on gtkhtml3.8 (>= 3.8.0); however:
  Package gtkhtml3.8 is not configured yet.
 evolution depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 evolution depends on libebook1.2-5 (>= 1.6.1); however:
  Package libebook1.2-5 is not configured yet.
 evolution depends on libecal1.2-3 (>= 1.6.1); however:
  Package libecal1.2-3 is not configured yet.
 evolution depends on libedataserverui1.2-6 (>= 1.6.1); however:
  Package libedataserverui1.2-6 is not configured yet.
 evolution depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.

```

---

### Post by kahuuna on 2006-06-02
continued, yet again ](*,) 
```
 evolution depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 evolution depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 evolution depends on libgtkhtml3.8-15 (>= 3.10.1); however:
  Package libgtkhtml3.8-15 is not configured yet.
 evolution depends on liblpint-bonobo0; however:
  Package liblpint-bonobo0 is not configured yet.
 evolution depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
 evolution depends on evolution-data-server (>= 1.5.5); however:
  Package evolution-data-server is not configured yet.
dpkg: error processing evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libexchange-storage1.2-1:
 libexchange-storage1.2-1 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libexchange-storage1.2-1 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libexchange-storage1.2-1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-exchange:
 evolution-exchange depends on evolution (>= 2.6.1); however:
  Package evolution is not configured yet.
 evolution-exchange depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 evolution-exchange depends on libebook1.2-5 (>= 1.6.1); however:
  Package libebook1.2-5 is not configured yet.
 evolution-exchange depends on libecal1.2-3 (>= 1.6.1); however:
  Package libecal1.2-3 is not configured yet.
 evolution-exchange depends on libedata-book1.2-2 (>= 1.6.1); however:
  Package libedata-book1.2-2 is not configured yet.
 evolution-exchange depends on libedata-cal1.2-1 (>= 1.6.1); however:
  Package libedata-cal1.2-1 is not configured yet.
 evolution-exchange depends on libedataserverui1.2-6 (>= 1.6.1); however:
  Package libedataserverui1.2-6 is not configured yet.
 evolution-exchange depends on libexchange-storage1.2-1 (>= 1.6.1); however:
  Package libexchange-storage1.2-1 is not configured yet.
 evolution-exchange depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 evolution-exchange depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 evolution-exchange depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 evolution-exchange depends on libgtkhtml3.8-15 (>= 3.10.1); however:
  Package libgtkhtml3.8-15 is not configured yet.
 evolution-exchange depends on liblpint-bonobo0; however:
  Package liblpint-bonobo0 is not configured yet.
dpkg: error processing evolution-exchange (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-plugins:
 evolution-plugins depends on evolution (= 2.6.1-0ubuntu7); however:
  Package evolution is not configured yet.
 evolution-plugins depends on evolution (>= 2.6.1); however:
  Package evolution is not configured yet.
 evolution-plugins depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 evolution-plugins depends on libebook1.2-5 (>= 1.6.1); however:
  Package libebook1.2-5 is not configured yet.
 evolution-plugins depends on libecal1.2-3 (>= 1.6.1); however:
  Package libecal1.2-3 is not configured yet.
 evolution-plugins depends on libedataserverui1.2-6 (>= 1.6.1); however:
  Package libedataserverui1.2-6 is not configured yet.
 evolution-plugins depends on libexchange-storage1.2-1 (>= 1.6.1); however:
  Package libexchange-storage1.2-1 is not configured yet.
 evolution-plugins depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 evolution-plugins depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 evolution-plugins depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 evolution-plugins depends on libgtkhtml3.8-15 (>= 3.10.1); however:
  Package libgtkhtml3.8-15 is not configured yet.
dpkg: error processing evolution-plugins (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-webcal:
 evolution-webcal depends on libecal1.2-3 (>= 1.6.1); however:
  Package libecal1.2-3 is not configured yet.
 evolution-webcal depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 evolution-webcal depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
dpkg: error processing evolution-webcal (--configure):
 dependency problems - leaving unconfigured
Setting up example-content (21) ...
Setting up libestools1.2 (1.2.3-9.1ubuntu1) ...

dpkg: dependency problems prevent configuration of file-roller:
 file-roller depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 file-roller depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 file-roller depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 file-roller depends on libnautilus-extension1 (>= 2.13.1); however:
  Package libnautilus-extension1 is not configured yet.
 file-roller depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing file-roller (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 firefox-gnome-support depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 firefox-gnome-support depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 firefox-gnome-support depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
Setting up foo2zjs (20051220dfsg-1) ...
dpkg: dependency problems prevent configuration of gcalctool:
 gcalctool depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 gcalctool depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 gcalctool depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 gcalctool depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 gcalctool depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing gcalctool (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gconf-editor:
 gconf-editor depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 gconf-editor depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 gconf-editor depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing gconf-editor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gksu:
 gksu depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing gksu (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gdebi:
 gdebi depends on gksu (>= 1.3.6-1); however:
  Package gksu is not configured yet.
dpkg: error processing gdebi (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 gnome-control-center depends on libebook1.2-5 (>= 1.6.1); however:
  Package libebook1.2-5 is not configured yet.
 gnome-control-center depends on libgnome-desktop-2 (>= 2.11.1); however:
  Package libgnome-desktop-2 is not configured yet.
 gnome-control-center depends on libgnome-menu2; however:
  Package libgnome-menu2 is not configured yet.
 gnome-control-center depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 gnome-control-center depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 gnome-control-center depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 gnome-control-center depends on libnautilus-extension1 (>= 2.13.1); however:
  Package libnautilus-extension1 is not configured yet.
 gnome-control-center depends on capplets-data (= 1:2.14.1-0ubuntu11); however:
  Package capplets-data is not configured yet.
 gnome-control-center depends on gnome-menus; however:
  Package gnome-menus is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of notification-daemon:
 notification-daemon depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing notification-daemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-power-manager:
 gnome-power-manager depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 gnome-power-manager depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 gnome-power-manager depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 gnome-power-manager depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 gnome-power-manager depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
 gnome-power-manager depends on notification-daemon; however:
  Package notification-daemon is not configured yet.
dpkg: error processing gnome-power-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-session:
 gnome-session depends on libgnome-desktop-2 (>= 2.11.1); however:
  Package libgnome-desktop-2 is not configured yet.
 gnome-session depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 gnome-session depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 gnome-session depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
 gnome-session depends on gnome-control-center (>= 2.6); however:
  Package gnome-control-center is not configured yet.
 gnome-session depends on gnome-power-manager; however:
  Package gnome-power-manager is not configured yet.
dpkg: error processing gnome-session (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of metacity:
 metacity depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing metacity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-terminal-data:
 gnome-terminal-data depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing gnome-terminal-data (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Errors were encountered while processing:
 gconf2
 libgnomevfs2-common
 libgnomevfs2-0
 libgnome-menu2
 gnome-menus
 alacarte
 libgnome2-common
 libgnome2-0
 libbonoboui2-0
 libgnomeui-0
 libgnome-desktop-2
 bug-buddy
 capplets-data
 libebook1.2-5
 libpanel-applet2-0
 contact-lookup-applet
 gstreamer0.10-plugins-good
 gnome-media
 libtotem-plparser1
 python2.4-gnome2-desktop
 python-gnome2-desktop
 deskbar-applet
 libecal1.2-3
 libedata-book1.2-2
 libedata-cal1.2-1
 evolution-data-server
 ekiga
 eog
 libnautilus-extension1
 evince
 libgtkhtml3.8-15
 gtkhtml3.8
 libedataserverui1.2-6
 liblpint-bonobo0
 evolution
 libexchange-storage1.2-1
 evolution-exchange
 evolution-plugins
 evolution-webcal
 file-roller
 firefox-gnome-support
 gcalctool
 gconf-editor
 gksu
 gdebi
 gnome-control-center
 notification-daemon
 gnome-power-manager
 gnome-session
 metacity
 gnome-terminal-data
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by jegerjensen on 2006-06-02
have you tried 

sudo dpkg --configure -a

(from  the dapper uppgrade troubleshhooting 
[https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades) )

---

### Post by kahuuna on 2006-06-02
[QUOTE=jegerjensen]have you tried 
sudo dpkg --configure -a[/QUOTE]

Yes, ends up with the same errors:
```
Processing was halted because there were too many errors.
```

---

### Post by ubuntu_demon on 2006-06-02
I just created a guide for you and others :
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

---

### Post by kahuuna on 2006-06-02
Thanks, your advice helped some, but I'm still stuck. Here's the current dependency issue:
```
kahuuna@lbx:~$ sudo apt-get -f remove
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  gnome-games gnome-games-data
Recommended packages:
  gnome-games-extra-data
The following NEW packages will be installed:
  gnome-games-data
The following packages will be upgraded:
  gnome-games
1 upgraded, 1 newly installed, 0 to remove and 27 not upgraded.
17 not fully installed or removed.
Need to get 0B/4182kB of archives.
After unpacking 14,0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package gnome-games.
(Reading database ... 134884 files and directories currently installed.)
Preparing to replace gnome-games 1:2.12.1-0ubuntu1 (using .../gnome-games_1%3a2.14.1-0ubuntu2_i386.deb) ...
gconftool-2: symbol lookup error: /usr/lib/libgconf-2.so.4: undefined symbol: g_slice_alloc0
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
dpkg: error processing /var/cache/apt/archives/gnome-games_1%3a2.14.1-0ubuntu2_i386.deb (--unpack):
 there is no script in the new version of the package - giving up
Unpacking gnome-games-data (from .../gnome-games-data_1%3a2.14.1-0ubuntu2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/gnome-games-data_1%3a2.14.1-0ubuntu2_all.deb (--unpack):
 trying to overwrite `/usr/share/gconf/schemas/aisleriot.schemas', which is also in package gnome-games
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-games_1%3a2.14.1-0ubuntu2_i386.deb
 /var/cache/apt/archives/gnome-games-data_1%3a2.14.1-0ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

```
kahuuna@lbx:~$ sudo apt-get remove -f gconf2
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  capplets-data: Depends: gconf2 (>= 2.12.1-4ubuntu1) but it is not going to be installed
  gnome-games: Depends: gnome-games-data (= 1:2.12.1-0ubuntu1) but it is not going to be installed
  libgnome2-common: Depends: gconf2 (>= 2.12.1-4ubuntu1) but it is not going to be installed
  libgnomevfs2-common: Depends: gconf2 (>= 2.12.1-4ubuntu1) but it is not going to be installed
  libgsf-1: Depends: gconf2 (>= 2.6.2-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

```
kahuuna@lbx:~$ sudo dpkg --configure -a
Setting up libpango1.0-common (1.12.2-0ubuntu3) ...
Updating the modules list for Pango-1.5.0.../usr/bin/pango-querymodules: symbol lookup error: /usr/lib/libpango-1.0.so.0: undefined symbol: g_intern_static_string
dpkg: error processing libpango1.0-common (--configure):
 subprocess post-installation script returned error exit status 127
Setting up gconf2 (2.14.0-1ubuntu2) ...
gconf-merge-tree: symbol lookup error: /usr/lib/libgconf-2.so.4: undefined symbol: g_slice_alloc0
dpkg: error processing gconf2 (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of capplets-data:
 capplets-data depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing capplets-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-common:
 libgnomevfs2-common depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgnomevfs2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-common:
 libgnome2-common depends on gconf2 (>= 2.12.1-4ubuntu1); however:
  Package gconf2 is not configured yet.
dpkg: error processing libgnome2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on capplets-data (= 1:2.14.1-0ubuntu11); however:
  Package capplets-data is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-0:
 libgnomevfs2-0 depends on libgnomevfs2-common (= 2.14.1-0ubuntu8); however:
  Package libgnomevfs2-common is not configured yet.
dpkg: error processing libgnomevfs2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libnautilus-extension1:
 libnautilus-extension1 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libnautilus-extension1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-0:
 libgnome2-0 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
 libgnome2-0 depends on libgnome2-common (= 2.14.1-0ubuntu2); however:
  Package libgnome2-common is not configured yet.
dpkg: error processing libgnome2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libbonoboui2-0:
 libbonoboui2-0 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libbonoboui2-0 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libbonoboui2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomeui-0:
 libgnomeui-0 depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 libgnomeui-0 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libgnomeui-0 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnomeui-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libebook1.2-5:
 libebook1.2-5 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libebook1.2-5 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libebook1.2-5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome-desktop-2:
 libgnome-desktop-2 depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 libgnome-desktop-2 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libgnome-desktop-2 depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 libgnome-desktop-2 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome-desktop-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-menus:
 gnome-menus depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing gnome-menus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome-menu2:
 libgnome-menu2 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome-menu2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libeel2-2:
 libeel2-2 depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 libeel2-2 depends on libgnome-desktop-2 (>= 2.11.1); however:
  Package libgnome-desktop-2 is not configured yet.
 libeel2-2 depends on libgnome-menu2; however:
  Package libgnome-menu2 is not configured yet.
 libeel2-2 depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libeel2-2 depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 libeel2-2 depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libeel2-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gmenu:
 python-gmenu depends on libgnome-menu2; however:
  Package libgnome-menu2 is not configured yet.
dpkg: error processing python-gmenu (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libpango1.0-common
 gconf2
 capplets-data
 libgnomevfs2-common
 libgnome2-common
 gnome-control-center
 libgnomevfs2-0
 libnautilus-extension1
 libgnome2-0
 libbonoboui2-0
 libgnomeui-0
 libebook1.2-5
 libgnome-desktop-2
 gnome-menus
 libgnome-menu2
 libeel2-2
 python-gmenu

```

---

### Post by ubuntu_demon on 2006-06-02
Try removing all packages that give errors. Do it in ctrl-alt-f1.

$sudo apt-get remove -f
$sudo apt-get remove gnome-games gnome-games-data gconf2 libgnome2-common libgsf-1 libpango1.0-common gconf2 capplets-data  libgnomevfs2-common  libgnome2-common  gnome-control-center libgnomevfs2-0  libnautilus-extension1  libgnome2-0  libbonoboui2-0  libgnomeui-0  libebook1.2-5  libgnome-desktop-2  gnome-menus  libgnome-menu2  libeel2-2  python-gmenu
$sudo apt-get remove -f

continue removing stuff until you don't have errors anymore.

then continue in this part of the guide :
> 
Let's now configure all packages that are still unconfigured :
$ sudo dpkg --configure -a

Now there are no more broken dependencies and all packages are configured. Let's install everything :

$ sudo apt-get install ubuntu-minimal
$ sudo apt-get install ubuntu-base
$ sudo apt-get install ubuntu-desktop
(or kubuntu / edubuntu / xubuntu)

And make sure everything is upgraded :
$ sudo apt-get update
$ sudo apt-get dist-upgrade

If everything went well your broken dependencies problem is fixed.

Now do a reboot :
$ sudo reboot


---

### Post by kahuuna on 2006-06-02
[QUOTE=ubuntu_demon]Try removing all packages that give errors. Do it in ctrl-alt-f1.
$sudo apt-get remove -f
$sudo apt-get remove gnome-games gnome-games-data gconf2 libgnome2-common libgsf-1 libpango1.0-common gconf2 capplets-data  libgnomevfs2-common  libgnome2-common  gnome-control-center libgnomevfs2-0  libnautilus-extension1  libgnome2-0  libbonoboui2-0  libgnomeui-0  libebook1.2-5  libgnome-desktop-2  gnome-menus  libgnome-menu2  libeel2-2  python-gmenu
$sudo apt-get remove -f
[/QUOTE]

I had already tried removing all those packages, here is the output:

```
kahuuna@lbx:~$ sudo apt-get remove -f
Password:
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  gnome-games gnome-games-data
Recommended packages:
  gnome-games-extra-data
The following NEW packages will be installed:
  gnome-games-data
The following packages will be upgraded:
  gnome-games
1 upgraded, 1 newly installed, 0 to remove and 27 not upgraded.
17 not fully installed or removed.
Need to get 0B/4182kB of archives.
After unpacking 14,0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 134884 files and directories currently installed.)
Preparing to replace gnome-games 1:2.12.1-0ubuntu1 (using .../gnome-games_1%3a2.14.1-0ubuntu2_i386.deb) ...
gconftool-2: symbol lookup error: /usr/lib/libgconf-2.so.4: undefined symbol: g_slice_alloc0
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
dpkg: error processing /var/cache/apt/archives/gnome-games_1%3a2.14.1-0ubuntu2_i386.deb (--unpack):
 there is no script in the new version of the package - giving up
Unpacking gnome-games-data (from .../gnome-games-data_1%3a2.14.1-0ubuntu2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/gnome-games-data_1%3a2.14.1-0ubuntu2_all.deb (--unpack):
 trying to overwrite `/usr/share/gconf/schemas/aisleriot.schemas', which is also in package gnome-games
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-games_1%3a2.14.1-0ubuntu2_i386.deb
 /var/cache/apt/archives/gnome-games-data_1%3a2.14.1-0ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


kahuuna@lbx:~$ sudo apt-get remove gnome-games gnome-games-data gconf2 libgnome2-common libgsf-1 libpango1.0-common gconf2 capplets-data libgnomevfs2-common libgnome2-common gnome-control-center libgnomevfs2-0 libnautilus-extension1 libgnome2-0 libbonoboui2-0 libgnomeui-0 libebook1.2-5 libgnome-desktop-2 gnome-menus libgnome-menu2 libeel2-2 python-gmenu
Reading package lists... Done
Building dependency tree... Done
Package gnome-games-data is not installed, so not removed
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libpango1.0-0: Depends: libpango1.0-common (>= 1.12.2-0ubuntu3) but it is not going to be installed
  nautilus: Depends: libbonoboui2-0 (>= 2.5.4) but it is not going to be installed
            Depends: libeel2-2 (>= 2.11.90) but it is not going to be installed
            Depends: libgnome-desktop-2 (>= 2.9.91) but it is not going to be installed
            Depends: libgnome2-0 (>= 2.8.0) but it is not going to be installed
            Depends: libgnomeui-0 (>= 2.8.0) but it is not going to be installed
            Depends: libgnomevfs2-0 (>= 2.11.3) but it is not going to be installed
            Depends: libnautilus-extension1 (>= 2.9.1) but it is not going to be installed
            Depends: gnome-control-center (>= 2.6) but it is not going to be installed
  yelp: Depends: libgnome2-0 (>= 2.8.0) but it is not going to be installed
        Depends: libgnomeui-0 (>= 2.8.0) but it is not going to be installed
        Depends: libgnomevfs2-0 (>= 2.11.3) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


kahuuna@lbx:~$ sudo apt-get remove -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  gnome-games gnome-games-data
Recommended packages:
  gnome-games-extra-data
The following NEW packages will be installed:
  gnome-games-data
The following packages will be upgraded:
  gnome-games
1 upgraded, 1 newly installed, 0 to remove and 27 not upgraded.
17 not fully installed or removed.
Need to get 0B/4182kB of archives.
After unpacking 14,0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 134884 files and directories currently installed.)
Preparing to replace gnome-games 1:2.12.1-0ubuntu1 (using .../gnome-games_1%3a2.14.1-0ubuntu2_i386.deb) ...
gconftool-2: symbol lookup error: /usr/lib/libgconf-2.so.4: undefined symbol: g_slice_alloc0
dpkg: warning - old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
dpkg: error processing /var/cache/apt/archives/gnome-games_1%3a2.14.1-0ubuntu2_i386.deb (--unpack):
 there is no script in the new version of the package - giving up
Unpacking gnome-games-data (from .../gnome-games-data_1%3a2.14.1-0ubuntu2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/gnome-games-data_1%3a2.14.1-0ubuntu2_all.deb (--unpack):
 trying to overwrite `/usr/share/gconf/schemas/aisleriot.schemas', which is also in package gnome-games
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-games_1%3a2.14.1-0ubuntu2_i386.deb
 /var/cache/apt/archives/gnome-games-data_1%3a2.14.1-0ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by ubuntu_demon on 2006-06-02
Post your /etc/apt/sources.list in order to make sure no non-official sources are listed there.

Make sure you are doing everything from ctrl-alt-f1 and also remove all new dependencies showing up such as :
nautilus , libeel2-2,yelp

Keep removing stuff until there are no more dependencies problems and things get actually removed. You could add them all to a single big remove command.

After that continue with this part of the guide :

> 
Let's run this command again to make sure it has removed everything that's problematic :
$ sudo apt-get -f remove

Let's now configure all packages that are still unconfigured :
$ sudo dpkg --configure -a

Now there are no more broken dependencies and all packages are configured. Let's install everything :

$ sudo apt-get install ubuntu-minimal
$ sudo apt-get install ubuntu-base
$ sudo apt-get install ubuntu-desktop
(or kubuntu / edubuntu / xubuntu)

And make sure everything is upgraded :
$ sudo apt-get update
$ sudo apt-get dist-upgrade

If everything went well your broken dependencies problem is fixed.

Now do a reboot :
$ sudo reboot


---

### Post by kahuuna on 2006-06-02
[QUOTE=ubuntu_demon]Post your /etc/apt/sources.list in order to make sure no non-official sources are listed there.

Make sure you are doing everything from ctrl-alt-f1 and also remove all new dependencies showing up such as :
nautilus , libeel2-2,yelp

Keep removing stuff until there are no more dependencies problems and things get actually removed. You could add them all to a single big remove command.

After that continue with this part of the guide :[/QUOTE]

After doing a massive and hefty sudo apt-get remove command, these are the leftovers which seem invulnerable:
```
The following packages will be REMOVED:
  gnome-games libgsf-1 nautilus yelp
0 upgraded, 0 newly installed, 4 to remove and 24 not upgraded.
10 not fully installed or removed.
Need to get 0B of archives.
After unpacking 8622kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 118468 files and directories currently installed.)
Removing gnome-games ...
/var/lib/dpkg/info/gnome-games.prerm: line 9: gconftool-2: command not found
/var/lib/dpkg/info/gnome-games.prerm: line 9: gconftool-2: command not found
dpkg: error processing gnome-games (--remove):
 subprocess pre-removal script returned error exit status 127
Removing libgsf-1 ...
/var/lib/dpkg/info/libgsf-1.prerm: line 9: gconftool-2: command not found
/var/lib/dpkg/info/libgsf-1.prerm: line 9: gconftool-2: command not found
dpkg: error processing libgsf-1 (--remove):
 subprocess pre-removal script returned error exit status 127
Removing nautilus ...
/var/lib/dpkg/info/nautilus.prerm: line 9: gconftool-2: command not found
/var/lib/dpkg/info/nautilus.prerm: line 9: gconftool-2: command not found
dpkg: error processing nautilus (--remove):
 subprocess pre-removal script returned error exit status 127
Removing yelp ...
/var/lib/dpkg/info/yelp.prerm: line 9: gconftool-2: command not found
/var/lib/dpkg/info/yelp.prerm: line 9: gconftool-2: command not found
dpkg: error processing yelp (--remove):
 subprocess pre-removal script returned error exit status 127
Errors were encountered while processing:
 gnome-games
 libgsf-1
 nautilus
 yelp
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Note that sudo apt-get remove -f would want me to install them all again:
```
kahuuna@lbx:~$ sudo apt-get remove -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  capplets-data firefox gconf2 gnome-control-center gnome-games gnome-games-data gnome-icon-theme gnome-keyring gnome-menus
  libbonoboui2-0 libebook1.2-5 libeel2-2 libgail-common libgail17 libglade2-0 libgnome-desktop-2 libgnome-keyring0
  libgnome-menu2 libgnome2-0 libgnome2-common libgnomecanvas2-0 libgnomeprint2.2-0 libgnomeprintui2.2-0 libgnomeui-0
  libgnomevfs2-0 libgnomevfs2-common libgtk2.0-0 libgtk2.0-bin libgtk2.0-common liblaunchpad-integration0 libmetacity0
  libnautilus-extension1 libpango1.0-0 libpango1.0-common librsvg2-2 librsvg2-common python-gmenu
Suggested packages:
  firefox-gnome-support latex-xft-fonts libthai0 esound-clients xscreensaver gnome-screensaver gstreamer0.10-alsa desktop-base
  libgnomevfs2-bin ttf-thryomanes librsvg2-bin
Recommended packages:
  gnome-session gnome-games-extra-data libgnomevfs2-extra
The following NEW packages will be installed:
  capplets-data firefox gconf2 gnome-control-center gnome-games-data gnome-icon-theme gnome-keyring gnome-menus libbonoboui2-0
  libebook1.2-5 libeel2-2 libgail-common libgail17 libglade2-0 libgnome-desktop-2 libgnome-keyring0 libgnome-menu2 libgnome2-0
  libgnome2-common libgnomecanvas2-0 libgnomeprint2.2-0 libgnomeprintui2.2-0 libgnomeui-0 libgnomevfs2-0 libgnomevfs2-common
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common liblaunchpad-integration0 libmetacity0 libnautilus-extension1 libpango1.0-0
  libpango1.0-common librsvg2-2 librsvg2-common python-gmenu
The following packages will be upgraded:
  gnome-games
1 upgraded, 36 newly installed, 0 to remove and 26 not upgraded.
10 not fully installed or removed.
Need to get 0B/22,8MB of archives.
After unpacking 98,4MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

```

---

### Post by ubuntu_demon on 2006-06-02
Read this. Make sure you understand it and follow it's suggestions :

What to do when apt-get fails :
[http://www.linux.com/article.pl?sid=05/10/12/1952217](http://www.linux.com/article.pl?sid=05/10/12/1952217)

Another option might be trying debfoster.This is a guide for breezy I wrote. But the principal in Dapper is the same :
[http://www.ubuntuforums.org/showthread.php?t=90675](http://www.ubuntuforums.org/showthread.php?t=90675)

Using debfoster you can easily remove packages including it's "children".

**But be very careful with debfoster**. And **only do it** if you understand what you are doing.

---

### Post by kahuuna on 2006-06-03
:-k ```
kahuuna@lbx:~$ sudo vim /var/lib/debfoster/keepers
kahuuna@lbx:~$ sudo debfoster -f
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gnome-games: Depends: libgnome2-0 (>= 2.8.0) but it is not going to be installed
               Depends: libgnomeui-0 (>= 2.8.0) but it is not going to be installed
               Depends: libgnomevfs2-0 (>= 2.11.3) but it is not going to be installed
               Depends: gnome-games-data (= 1:2.12.1-0ubuntu1) but it is not going to be installed
  libgsf-1: Depends: gconf2 (>= 2.6.2-1) but it is not going to be installed
  nautilus: Depends: libbonoboui2-0 (>= 2.5.4) but it is not going to be installed
            Depends: libeel2-2 (>= 2.11.90) but it is not going to be installed
            Depends: libgnome-desktop-2 (>= 2.9.91) but it is not going to be installed
            Depends: libgnome2-0 (>= 2.8.0) but it is not going to be installed
            Depends: libgnomeui-0 (>= 2.8.0) but it is not going to be installed
            Depends: libgnomevfs2-0 (>= 2.11.3) but it is not going to be installed
            Depends: libnautilus-extension1 (>= 2.9.1) but it is not going to be installed
            Depends: gnome-control-center (>= 2.6) but it is not going to be installed
  ubuntu-base: Depends: ubuntu-minimal but it is not going to be installed
  yelp: Depends: libgnome2-0 (>= 2.8.0) but it is not going to be installed
        Depends: libgnomeui-0 (>= 2.8.0) but it is not going to be installed
        Depends: libgnomevfs2-0 (>= 2.11.3) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by ubuntu_demon on 2006-06-03
I'm sorry I don't have time right now. I'll be back for you I'll promise.

---

### Post by kahuuna on 2006-06-03
[QUOTE=ubuntu_demon]I'm sorry I don't have time right now. I'll be back for you I'll promise.[/QUOTE]

Don't bother. I appreciate and thank you for your help though. I decided to install dapper from cd overwriting the previous installation.

I consider this upgrade process to have failed, and as a self-proclaimed Ubuntu fanboy I'm quite disappointed. Oh well, I shall hope dependency issues shall never plague me again (one can always hope).

Good night and good luck,
kahuuna

---

### Post by ubuntu_demon on 2006-06-03
You should try one more time. First :
$sudo apt-get install -f

Then my guide :
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

If it doesn't work out and you are getting too frustrated you could choose to reinstall. 

In order to prevent future dependencies problems. Here are some pausible causes :
-You started dist-upgrading while not having commented non-official Ubuntu repositories
-Your system became unresponsive while dist-upgrading and you had to reboot after a while waiting.
-You installed too many non-official packages and you have bad luck.

sorry that I don't have more time

good luck! :)

---

### Post by annajilly on 2006-09-08
found a solution, on my system.

I has having similar things going on with Debian.  My laptop battery ran out or got a kernel panic in the middle of an upgrade. When I came back to it I was completely stuck.  I followed all the advice I found everywhere, including in this thread, and nothing worked.  EVERY command failed because of that missing symbol: g_slice_alloc0

Finally, after running ldd on a few executables that seemed to be giving me problems I realized that they were linked to libraries in  /usr/local/lib/ .  libglib, specifically, in my /usr/local was in use and it lacked the symbol that a newer library required.  deleting this from-scratch install removed my symbols problem.

---

