---
title: "Work-around for broken gnome-core-devel build-essential"
date: 2013-01-18
forum: Installation &amp; Upgrades
---

### Post by mthornton on 2013-01-18
Hello! I am trying to install[ [COLOR=Blue]CisGenome Browser[/COLOR]]("http://http://www-personal.umich.edu/~jianghui/browser/getting_started/index.html") in Ubuntu 12.10. I am having a problem installing GTK, using apt-get. I have seen that there is a_[COLOR=Blue] [COLOR=Blue][bug]("http://https://bugs.launchpad.net/ubuntu/+source/meta-gnome3/+bug/1063660")[/COLOR][/COLOR]_ - and a possible fix, but I don't know how to implement it - or it is still not working.

```

gserver@gserver: sudo aptitude install gnome-core-devel build-essential
The following NEW packages will be installed:
  autopoint{a} devhelp{a} devhelp-common{a} docbook{a} docbook-dsssl{a} docbook-to-man{a} 
  evolution-data-server-dev{a} gir1.2-brasero-3.0{a} gir1.2-ebook-1.2{a} gir1.2-ecalendar-1.2{a} 
  gir1.2-edataserver-1.2{a} gir1.2-evince-3.0{a} gir1.2-gladeui-2.0{a} gir1.2-gtkclutter-1.0{a} git{a} 
  git-man{a} gnome-api-docs{a} gnome-common{a} gnome-core-devel{b} gnome-devel-docs{a} gnome-platform-devel{a} 
  gobject-introspection{a} gsettings-desktop-schemas-dev{a} gstreamer0.10-doc{a} 
  gstreamer0.10-plugins-base-doc{a} gstreamer0.10-plugins-good-doc{a} gstreamer0.10-plugins-ugly-doc{a} 
  gtk-doc-tools{a} gtkmm-documentation{a} jade{a} libatk-bridge2.0-dev{a} libatk1.0-dev{a} libatk1.0-doc{a} 
  libatkmm-1.6-doc{a} libbrasero-media3-dev{a} libcairo2-doc{a} libcamel1.2-dev{a} libcanberra-doc{a} 
  libclutter-1.0-dev{a} libclutter-1.0-doc{a} libclutter-gtk-1.0-dev{a} libclutter-gtk-1.0-doc{a} libcogl-dev{a} 
  libcogl-pango-dev{a} libdbus-1-dev{a} libdbus-glib-1-dev{a} libdconf-dev{a} libdconf-doc{a} libdevhelp-3-1{a} 
  libebackend1.2-dev{a} libebook1.2-dev{a} libecal1.2-dev{a} libedata-book1.2-dev{a} libedata-cal1.2-dev{a} 
  libedataserver1.2-dev{a} libedataserverui-3.0-4{a} libedataserverui-3.0-dev{a} libevince-dev{a} 
  libgail-3-dev{a} libgail-3-doc{a} libgail-dev{a} libgail-doc{a} libgconf2-dev{a} libgconf2-doc{a} 
  libgdk-pixbuf2.0-doc{a} libgirepository1.0-dev{a} libgirepository1.0-doc{a} libgjs-dev{a} libgladeui-2-4{a} 
  libgladeui-common{a} libgladeui-dev{a} libglib2.0-doc{a} libglibmm-2.4-dev{a} libglibmm-2.4-doc{a} 
  libgnome-bluetooth-dev{a} libgnome-desktop-3-dev{a} libgnome-keyring-dev{a} 
  libgstreamer-plugins-base0.10-dev{a} libgstreamer0.10-dev{a} libgtk-3-dev{a} libgtk-3-doc{a} libgtk2.0-dev{a} 
  libgtk2.0-doc{a} libgtkmm-3.0-doc{a} libgtksourceview-3.0-dev{a} libgtksourceview-3.0-doc{a} libgtop2-doc{a} 
  libical-dev{a} libjson-glib-dev{a} libmozjs185-dev{a} libnm-util-dev{a} libnotify-dev{a} libnotify-doc{a} 
  libnspr4-dev{a} libnss3-dev{a} libpanel-applet-4-doc{a} libpango1.0-doc{a} libpangomm-1.4-doc{a} 
  libpeas-dev{a} libpeas-doc{a} libsigc++-2.0-dev{a} libsoup2.4-dev{a} libsoup2.4-doc{a} libsp1c2{a} 
  libsqlite3-dev{a} libtelepathy-glib-doc{a} libvte-doc{a} libxcomposite-dev{a} libxcursor-dev{a} libxi-dev{a} 
  libxinerama-dev{a} libxkbfile-dev{a} libxml2-doc{a} libxrandr-dev{a} policykit-1-doc{a} sp{a} 
  x11proto-composite-dev{a} x11proto-randr-dev{a} x11proto-xinerama-dev{a} xsltproc{a} 
0 packages upgraded, 120 newly installed, 0 to remove and 0 not upgraded.
Need to get 83.8 MB of archives. After unpacking 433 MB will be used.
The following packages have unmet dependencies:
 gnome-core-devel : Depends: libudisks2-dev (>= 3.0) but it is not going to be installed.
                    Depends: gnome-doc-utils (>= 0.20.6) but it is not going to be installed.
                    Depends: libgck-1-dev (>= 3.2) but it is not going to be installed.
                    Depends: libgcr-3-dev (>= 3.0) but it is not going to be installed.
                    Depends: libgnome-menu-3-dev (>= 3.0) but it is not going to be installed.
                    Depends: libpanel-applet-4-dev (>= 3.0) but it is not going to be installed.
                    Depends: libgtkhtml-4.0-dev (>= 4.0) but it is not going to be installed.
                    Depends: libgtkmm-3.0-dev (>= 3.0) but it is not going to be installed.
                    Depends: libgucharmap-2-90-dev (>= 3.0) but it is not going to be installed.
                    Depends: libgnomekbd-dev (>= 3.0) but it is not going to be installed.
                    Depends: libgtop2-dev (>= 2.28.3) but it is not going to be installed.
                    Depends: libgweather-3-dev (>= 3.0) but it is not going to be installed.
                    Depends: libsoup-gnome2.4-dev (>= 2.34) but it is not going to be installed.
                    Depends: libwnck-3-dev (>= 3.0) but it is not going to be installed.
                    Depends: mm-common (>= 0.9.5) but it is not going to be installed.
                    Depends: libmutter-dev (>= 3.0) but it is not going to be installed.
                    Depends: libnautilus-extension-dev (>= 3.0) but it is not going to be installed.
                    Depends: libpangomm-1.4-dev (>= 2.28) but it is not going to be installed.
                    Depends: python-gobject-dev (>= 2.28) but it is not going to be installed.
                    Depends: libtelepathy-glib-dev (>= 0.15) but it is not going to be installed.
                    Depends: libtelepathy-farstream-dev (>= 0.2.1) but it is not going to be installed.
                    Depends: libtotem-plparser-dev (>= 2.32) but it is not going to be installed.
                    Depends: libvte-2.90-dev (>= 0.28) but it is not going to be installed.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     gnome-core-devel [Not Installed]                   



Accept this solution? [Y/n/q/?] 

```Any ideas?

---

