---
title: "General Installation problems"
date: 2007-09-22
forum: Installation &amp; Upgrades
---

### Post by Eagle784 on 2007-09-22
I've been trying to install a ftp server on ubuntu 7.04, but I keep getting install errors.  the gettext package seems to be at the root of all the problems.  This is my output when I try to install:

# apt-get install proftpd
Reading package lists... Done
Building dependency tree
Reading state information... Done
proftpd is already the newest version.
The following packages were automatically installed and are no longer required:
  libgnomecupsui1.0-1c2a gstreamer0.10-alsa gs-esp-x evolution-common
  libsdl1.2debian libgnomekbd1 desktop-base libsdl1.2debian-alsa planner
  libglib-perl ekiga libgsf-gnome-1-114 xsltproc libenchant1c2a
  notification-daemon gcalctool gnome-desktop-environment gstreamer0.10-x
  libgail18 gs-esp python-gnome2 gnome-nettool libgoffice-0-common gnome-media
  gnome-games-extra-data metacity epiphany-browser gnome-desktop-data
  abiword-gnome nautilus dia-libs libgstreamer0.10-0 libnss3 libraw1394-8
  libcaca0 libiec61883-0 genisoimage libdjvulibre15 libwmf0.2-7 libvorbisfile3
  libperl5.8 gucharmap python-gnomecanvas industrial-cursor-theme zenity
  gnome-games libgail-common cdrecord liburi-perl evolution libgnome-media0
  libbeagle0 gnome-power-manager esound libexchange-storage1.2-3 unzip
  gnome-cards-data gnome-screensaver libgtksourceview1.0-0 rhythmbox gedit
  gnome-menus liblircclient0 gtk2-engines-pixbuf gnome-office dvd+rw-tools
  abiword-common libx86-1 libhtml-parser-perl gnome-control-center libspeex1
  libapm1 libpisock9 libcamel1.2-10 libwnck-common gnome-themes
  metacity-common libgnome2-perl libpcre3 libxml-twig-perl whois libnotify1
  libedata-cal1.2-6 gnumeric-common libvorbisenc2 libsoup2.2-8
  gnome-media-common libgpod1 nautilus-data libgnome-menu2
  gstreamer0.10-plugins-good gnome-terminal libxml-parser-perl toshset
  system-tools-backends libcdio6 gtkhtml3.14 libpanel-applet2-0
  libpoppler1-glib libeel2-data libwnck18 guile-1.6-libs libgnomekbd-common
  libsexy2 gedit-common gnome-utils gnome-themes-extras vbetool
  libcairomm-1.0-1 libgnome-pilot2 libxres1 acpid finger libglibmm-2.4-1c2a
  gdm-themes libmusicbrainz4c2a libnet-dbus-perl fast-user-switch-applet
  firefox laptop-mode-tools libhunspell-1.1-0 powermgmt-base gnome-about
  gnome-volume-manager dia-gnome nautilus-cd-burner gtk2-engines
  libgnomeprint2.2-data libkpathsea4 libpt-plugins-v4l gs-common
  libgnomekbdui1 gdb eog gdm libavc1394-0 libslab0 hal capplets-data
  libgnome2-vfs-perl gnome-backgrounds libegroupwise1.2-13 bug-buddy
  libnm-glib0 libgsf-1-common gnome-doc-utils libgtk2-perl libcroco3
  libecal1.2-7 libpoppler1 libtheora0 libaa1 wodim libdirectfb-0.9-25
  libgtksourceview-common vino gnome-keyring-manager gnome-system-monitor
  libgtkmm-2.4-1c2a libao2 evince libqthreads-12 libbluetooth2
  gnome-games-data powermanagement-interface libcdparanoia0 gnome-user-guide
  libflac7 libebook1.2-9 libnspr4 libgoffice-0-3 libshout3 libdv4
  libedataserverui1.2-8 totem-gstreamer libgnome-window-settings1 libmetacity0
  libedata-book1.2-2 evolution-data-server cdrdao libgnomevfs2-bin
  acpi-support gimp liblpint-bonobo0 libedataserver1.2-9 libgimp2.0 yelp gksu
  gnome-icon-theme smartdimmer libeel2-2 zip gnome-core dia-common
  gnome-netstatus-applet libcupsimage2 libpt-plugins-alsa libtag1c2a
  librsvg2-2 libxklavier11 libgda2-3 gnome-terminal-data liboobs-1-3
  libgucharmap6 libgksu2-0 gnome-applets gnumeric python-gmenu libopal-2.2.0
  radeontool libtotem-plparser1 libgs-esp8 gnome-system-tools
  libhtml-tree-perl liboil0.3 hal-info libxdamage1 libxml2-utils gnome-panel
  libcairo-perl libwww-perl libvisual-0.4-0 libgda2-common
  gtk2-engines-spherecrystal mkisofs gstreamer0.10-gnomevfs libvorbis0a totem
  libnautilus-burn4 python-gnome2-desktop libnautilus-extension1
  evolution-data-server-common gimp-data gnome-mount gnome-applets-data
  libgnomeprint2.2-0 gstreamer0.10-plugins-base libhtml-tagset-perl
  desktop-file-utils libpt-1.10.0 inkscape libgstreamer-plugins-base0.10-0
  libguile-ltdl-1 gnome-session libgnome-desktop-2 librsvg2-common
  libgnomeprintui2.2-0 libaspell15 totem-mozilla libmng1 libcucul0
  libgnome2-canvas-perl libgtkhtml3.14-19 libgnomeprintui2.2-common
  libgsf-1-114 gsfonts file-roller libpaper1 gnome-cups-manager
  gnome-panel-data sound-juicer libgnomecups1.0-1 libpisync0 libogg0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Illegal instruction
Setting up gettext (0.16.1-1ubuntu2) ...
Illegal instruction
dpkg: error processing gettext (--configure):
 subprocess post-installation script returned error exit status 132
Setting up proftpd (1.3.0-21ubuntu1) ...
dpkg: error processing proftpd (--configure):
 subprocess post-installation script killed by signal (Illegal instruction)
Errors were encountered while processing:
 gettext
 proftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)

Thanks for your help.

---

### Post by Eagle784 on 2007-09-23
Anyone have any ideas?  I really don't want to have to reinstall everything ...

---

### Post by banewman on 2007-09-23
I would have thought sudo would be needed...

---

### Post by Eagle784 on 2007-09-23
running as root atm

Edit: just to explain why I really prefer not to reinstall this time - I'm accessing a box at a datacenter remotely.  As far as I can tell, reinstalling involves imaging the drive back to 6.06 (the most recent version of ubuntu they have available), once again getting lucky that upgrading works for edgy and feisty (it didn't for me the first two times I tried it, both with apt-get dist-upgrade and update-manager), once again recompiling some of the programs I need, and finally hoping like hell this doesn't happen again, because apparently, there's no way to fix it ...

Been browsing around and tried some other recommended advice: apt-get remove, apt-get remove purge, dpkg --forceall -P without any luck.  I'm about ready to spend the 18 euros a month for a windows license; all those people telling me how simple to use ubuntu had gotten can most charitably be described as liars.

---

### Post by banewman on 2007-09-23
The fifth line says you already have the latest proftpd so what you wanted that for should be available.... I would clean up with autoremove.

---

### Post by Eagle784 on 2007-09-23
Nah, no such luck.  The error when I try to run proftpd:

 - Fatal: unable to read configuration file '/etc/proftpd/proftpd.conf': No such file or directory

---

