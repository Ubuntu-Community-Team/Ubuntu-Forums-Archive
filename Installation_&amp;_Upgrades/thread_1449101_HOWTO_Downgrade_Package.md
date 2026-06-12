---
title: "HOWTO: Downgrade Package"
date: 2010-04-07
forum: Installation &amp; Upgrades
---

### Post by johnathanamber on 2010-04-07
Hello everyone!

So i've found this article on how to downgrade a package to an earlier version:
[http://www.skorks.com/2009/07/downgrading-a-ubuntu-package/](http://www.skorks.com/2009/07/downgrading-a-ubuntu-package/)

I've updated libgtk2.0-0 to a later version (2.19.7-polslinux2). And now I am having issue with my mouse. "Can not grab mouse" errors.

Here is my output when I try to downgrade to an earlier version of libgtk2.0-0:
> 
$ sudo apt-get install libgtk2.0-0=2.18.3-1ubuntu2.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dvdrip-doc python-beaker libxml-sax-perl kdebase-runtime-data-common
  libnautilus-burn4 python-mako libxml-sax-expat-perl libxine1-x lives-data
  twolame libsox-fmt-base libgtk2-imageview-perl libknotificationitem1
  kdelibs5 libsox-fmt-alsa libglademm-2.4-1c2a transcode-doc
  gtk2-ex-formfactory-perl libx11-protocol-perl libxml-namespacesupport-perl
  libhttp-server-simple-perl liblzma0 backintime-common libsoprano4
  libevent-execflow-perl libextutils-depends-perl transcode-utils
  kde-icons-oxygen libgnome2-gconf-perl libxml-simple-perl libqt4-gui
  libwww-mechanize-perl libgtkimageview0 vamps gnome-web-photo
  libxine1-console soprano-daemon fping sox cdrdao fuseiso libplasma3
  libgnome2-wnck-perl kdelibs-bin libstreams0 liferea-data kdelibs5-data
  libintl-perl libsox1a libxcb-shape0 libextutils-pkgconfig-perl
  kdebase-runtime-data libhttp-response-encoding-perl libgoo-canvas-perl
  libxine1-bin libgtk2-trayicon-perl libxine1-ffmpeg libstreamanalyzer0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  acetoneiso awn-applets-c-extras-trunk backintime-gnome dvd95 dvdauthor
  dvdrip empathy empathy-megaphone-applet evolution evolution-couchdb
  evolution-exchange evolution-indicator evolution-plugins f-spot gdm
  gdm-guest-session gimp gnome-about gnome-applets gnome-color-chooser
  gnome-orca gnome-panel gnome-pilot gnome-pilot-conduits gnome-power-manager
  gnome-session gnome-themes gnome-themes-more gnome-themes-selected
  gnome-themes-ubuntu gnome-utils gtk2-engines-pixbuf handbrake-gtk
  imagemagick indicator-applet indicator-applet-session indicator-messages
  indicator-session k9copy kdebase-runtime kdebase-runtime-bin-kde4
  khelpcenter4 libbonoboui2-0 libdvd0 libempathy-gtk28 libgail-common
  libgail-gnome-module libgail18 libgnome-pilot2 libgnome2-canvas-perl
  libgnome2-perl libgnome2.24-cil libgnomecanvas2-0 libgnomepanel2.24-cil
  libgnomeui-0 libgraphviz4 libgtkhtml-editor0 libgtkhtml2-0 libgtkhtml3.14-19
  liblpint-bonobo0 libmagickcore2 libmagickwand2 libpanel-applet2-0
  libwebkit-1.0-2 libxine1 libxine1-misc-plugins liferea lives mousetweaks
  nautilus nautilus-share obex-data-server perlmagick phonon-backend-xine
  python-empathy python-gnome2 python-gnomeapplet python-gnomecanvas
  python-gtkhtml2 python-pyatspi python-webkit rhythmbox
  rhythmbox-plugin-cdrecorder rhythmbox-plugins shrinkta shutter
  software-center stardict-gnome stardict-plugin stardict-plugin-espeak
  stardict-plugin-festival stardict-plugin-gucharmap subtitleripper
  system-config-printer-gnome tomboy transcode ubuntu-desktop usb-creator-gtk
  vinagre xine-ui xiphos
The following packages will be DOWNGRADED:
  libgtk2.0-0
0 upgraded, 0 newly installed, 1 downgraded, 101 to remove and 0 not upgraded.
Need to get 0B/2,553kB of archives.
After this operation, 278MB disk space will be freed.
Do you want to continue [Y/n]? 


Of course I hit 'n'. Is there a way to downgrade this WITHOUT removing all of those packages that I regularly use?

I was able to follow the above link to downgrade the following without issue:
libgtk2.0-bin
libgtk2.0-common

Issue still persists.

Thank you and God bless,
Johanthan

---

### Post by johnathanamber on 2010-06-08
Ended up reinstalling.

---

