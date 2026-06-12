---
title: "Bare ubuntu install"
date: 2006-07-22
forum: Installation &amp; Upgrades
---

### Post by X_X_X on 2006-07-22
Hello all,

I was wondering is there anyway to install ubuntu without any of the added software.

---

### Post by ajgreeny on 2006-07-22
Depends what you mean by added software.  You can do the server install which gives you just a bare bones linux kernel more or less with no GUI (Gnome or KDE or xfce).  If you want a gui with low demand  then just install xubuntu; it is much lower in it's requirements than Gnome or KDE.

---

### Post by X_X_X on 2006-07-22
Sry I should have been a bit more specific.

I just dont want evolution, and most of the other software thats there after instalation thats all.

When i try to remove it a lot of it has dependencies to the ubuntu desk top.

Is there a like a guide of which software is safe to remove from ubuntu. I i had a reinstall it like twice after uninstalling things.

---

### Post by ajgreeny on 2006-07-22
I don't think it is disastrous to remove the ubuntu-desktop, si it is probably worth a try.  If you find that some things don't work properly without it you can always reinstall it anyway.  You will still have a lot of gnome desktop packages installed (assuming you don't mean to remove them all).

---

### Post by K.Mandla on 2006-07-22
You can remove ubuntu-desktop without harming anything. The package is a kind of marker, as I understand it, telling the system that an entire series of sub-packages are installed. 

Removing Evolution simply removes that marker, since ubuntu-desktop is *supposed* to have Evolution as well. Don't worry: Nothing is going to break; I've done it any number of times.

---

### Post by X_X_X on 2006-07-23
Thanks for the info,

I had a bit of a poke arround the net, and i think that if i do this

udo apt-get remove alacarte app-install-data-commercial at-spi avahi-daemon bittorrent bluez-pin brltty-x11 bug-buddy capplets-data contact-lookup-applet dbus-1-utils deskbar-applet desktop-base desktop-file-utils ekiga eog esound evince evolution evolution-data-server evolution-exchange evolution-plugins evolution-webcal festival festlex-cmu festlex-poslex festvox-kallpc16k file-roller firefox firefox-gnome-support fping gaim gaim-data gcalctool gconf-editor gconf2 gconf2-common gdb gdebi gdm gedit gedit-common gimp gimp-data gimp-print gimp-python gksu gnome-about gnome-accessibility-themes gnome-app-install gnome-applets gnome-applets-data gnome-btdownload gnome-control-center gnome-cups-manager gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-icon-theme gnome-keyring gnome-mag gnome-media gnome-menus gnome-mime-data gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes gnome-utils gnome-volume-manager gnome2-user-guide gnopernicus gok gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-tools gstreamer0.10-x gthumb gtk2-engines-clearlooks gtk2-engines-crux gtk2-engines-highcontrast gtk2-engines-industrial gtk2-engines-lighthouseblue gtk2-engines-mist gtk2-engines-pixbuf gtk2-engines-redmond95 gtk2-engines-smooth gtk2-engines-thinice gtk2-engines-ubuntulooks gtkhtml3.8 gucharmap guile-1.6-libs hal-device-manager hwdb-client im-switch language-selector launchpad-integration libaa1 libatk1.0-0 libatspi1.0-0 libavahi-core4 libavahi-glib1 libavc1394-0 libbeagle0 libbeecrypt6 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libbtctl2 libcamel1.2-8 libcdio6 libcompfaceg1 libcroco3 libdaemon0 libdjvulibre15 libdv4 libebook1.2-5 libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1 libedataserver1.2-7 libedataserverui1.2-6 libeel2-2 libeel2-data libegroupwise1.2-9 libestools1.2 libexchange-storage1.2-1 libgail-common libgail-gnome-module libgail17 libgconf2-4 libgda2-3 libgda2-common libgdl-1-0 libgdl-1-common libgimp2.0 libgksu1.2-1 libgksuui1.0-1 libglade2-0 libglew1 libglib-perl libglib2.0-data libgnome-desktop-2 libgnome-keyring0 libgnome-mag2 libgnome-menu2 libgnome-pilot2 libgnome-speech3 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnomebt0 libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1 libgnomecupsui1.0-1c2a libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgpod0 libgsf-1-113 libgsf-1-common libgtk2-perl libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtkhtml2-0 libgtkhtml3.8-15 libgtksourceview-common libgtksourceview1.0-0 libgtkspell0 libgtop2-7 libgucharmap4 libguile-ltdl-1 libgutenprintui2-1 libkpathsea4 liblaunchpad-integration0 liblircclient0 liblpint-bonobo0 libmetacity0 libnautilus-burn3 libnautilus-extension1 libnotify1 liboil0.3 libopal-2.2.0 libpanel-applet2-0 libpango1.0-0 libpango1.0-common libpisync0 libpoppler1-glib libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 libqthreads-12 librpm4 librsvg2-2 librsvg2-common libsdl1.2debian libsdl1.2debian-alsa libsexy2 libshout3 libsoup2.2-8 libtotem-plparser1 libvte-common libvte4 libwmf0.2-7 libwnck-common libwnck18 libxklavier10 libxml2-utils libxres1 metacity nautilus nautilus-cd-burner nautilus-data nautilus-sendto notification-daemon openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk pkg-config python-glade2 python-gmenu python-gnome2 python-gnome2-desktop python-gnome2-extras python-gst0.10 python-gtk2 python-launchpad-integration python-libxml2 python-vte python2.4-cairo python2.4-glade2 python2.4-gnome2 python2.4-gnome2-desktop python2.4-gnome2-extras python2.4-gobject python2.4-gtk2 rdesktop rhythmbox rpm rss-glx scim scim-gtk2-immodule scim-modules-socket screensaver-default-images serpentine shared-mime-info sharutils sound-juicer ssh-askpass-gnome synaptic system-tools-backends tangerine-icon-theme tango-icon-theme tango-icon-theme-common totem totem-gstreamer tsclient ttf-arphic-ukai ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-sounds unattended-upgrades update-manager update-notifier vino vnc-common whois xsane xsane-common xscreensaver xscreensaver-data xscreensaver-gl xsltproc xvncviewer yelp zenity

It will remove everything includeing gnome.

Than i think that i should do this to reinstall gnome core

sudo aptitude install gnome-core

I will see what happens. Hopefully it will work.

---

### Post by X_X_X on 2006-07-23
Or maybe

sudo aptitude install ubuntu-minimal 

instead of gnome-core

---

### Post by lefty.crupps on 2007-01-29
I am wondering how well that worked; I too am looking for the barest install available.  I don't want the LAMP stack, don't want GNOME or anything in this install, until I add it..

Any news on your progress of mass removal?  What version of Ubuntu are you starting with, Ubuntu 6.06, 6.10, 7.04?

Does anyone know of a barebones installation image available already?

---

### Post by Hanzerik on 2007-01-29
The basic server install is about it for Ubuntu as far as I know. When you boot with the cd, just do a server install and not the LAMP install.

Or you can get the Debian net install disk (137meg) and deselect all software install options when you reach that screen. This base install is reall small.

---

