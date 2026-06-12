---
title: "How to troubleshoot the 8.04 upgrade"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by dgavenda on 2008-04-24
I am having issues w/ the 8.04 upgrade from 7.10.  Here is the output:

sudo aptitude safe-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  abiword abiword-plugins amarok-xine amule-common apt apt-utils asterisk-config bluez-gnome boo compiz-core compiz-fusion-plugins-extra 
  compiz-fusion-plugins-main compiz-gnome compiz-plugins dbus-x11 debhelper dia-common dia-libs dpkg-dev eclipse eclipse-jdt 
  eclipse-jdt-gcj eclipse-pde eclipse-pde-gcj eclipse-platform eclipse-platform-gcj eclipse-rcp eclipse-rcp-gcj eclipse-source 
  evolution-common g++ gappletviewer-4.2 gcj-4.2 gcj-4.2-base gij-4.2 gnome-cards-data gnome-mount gnucash-common gnumeric-common 
  gnumeric-gtk gqview gstreamer0.10-plugins-bad gtk2-engines-xfce gtkhtml3.14 hal-cups-utils hal-info hpijs-ppds java-gcj-compat-dev 
  kamera kdebase-bin kdebase-kio-plugins kdelibs-data kdelibs4c2a kdemultimedia-kio-plugins kdesktop kghostview koffice-libs 
  libaiksaurusgtk-1.2-0c2a libapache2-mod-php5 libaprutil1 libedataserver1.2-9 libegroupwise1.2-13 libexchange-storage1.2-3 libexo-0.3-0 
  libfaad2-0 libgcj-bc libgcj7-1 libgcj7-1-awt libgcj8-1 libgcj8-1-awt libgcj8-dev libgcj8-jar libgdl-gnome-1-0 libgnome-speech7 
  libgnomekbd-common libgpod-common libgs8 libgtk1.2 libgtkhtml3.14-19 libgtkmathview0c2a libgtkmm-2.4-1c2a libgtksourceview2.0-0 
  libgtksourceview2.0-common libgucharmap6 libimlib2 libjaxp1.3-java-gcj libkcddb1 libkonq4 libmime-lite-perl libmime-perl libnfsidmap2 
  libnss3-0d libofa0 libopal-2.2 libossp-uuid-perl libpoppler-glib2 libpq5 libpri1.2 libpurple0 libquicktime1 librarian0 librpcsecgss3 
  libsasl2-2 libsvn1 libswt3.2-gtk-gcj libswt3.2-gtk-java libswt3.2-gtk-jni libthunar-vfs-1-2 libtunepimp5 libungif4-dev libungif4g 
  libvcdinfo0 libwnck22 libwxgtk2.6-0 libwxgtk2.8-0 libx11-dev libxalan2-java-gcj libxerces2-java-gcj libxfcegui4-4 libxine1-ffmpeg 
  linux-headers-generic mousepad mysql-query-browser network-manager-gnome nfs-common openoffice.org-filter-binfilter 
  openoffice.org-filter-mobiledev openoffice.org-help-en-us openoffice.org-l10n-common openoffice.org-l10n-en-gb openoffice.org-l10n-en-za 
  openoffice.org-style-andromeda openoffice.org-style-human openoffice.org-style-tango openssh-server orage perl-suid php5-common php5-gd 
  pidgin-data python-cups python-exo python-notify python2.5 python2.5-examples python2.5-minimal rpm scim-modules-table 
  scim-tables-additional sendmail-bin sun-java5-bin sun-java5-demo sun-java5-jre thunar thunar-data thunderbird update-manager-core 
  vlc-nox wireshark-common xarchiver xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-fsguard-plugin 
  xfce4-mcs-manager xfce4-mcs-plugins xfce4-mixer xfce4-mixer-alsa xfce4-notes-plugin xfce4-panel xfce4-quicklauncher-plugin xfce4-session 
  xfce4-systemload-plugin xfce4-terminal xfce4-utils xfce4-weather-plugin xfdesktop4 xfdesktop4-data xfprint4 xfwm4 xfwm4-themes 
  xscreensaver xserver-xorg-video-amd xserver-xorg-video-intel 
The following packages have been kept back:
  acpi-support amarok amule aptitude asterisk at-spi avidemux banshee bluefish bluez-pcmcia-support bluez-utils brasero brltty brltty-x11 
  bug-buddy capplets-data cheese compiz cupsys cupsys-bsd cupsys-client cupsys-driver-gutenprint dbus deskbar-applet dia dpkg eclipse-sdk 
  ekiga eog ethereal ethereal-common evolution evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins 
  evolution-webcal f-spot file-roller firefox firefox-gnome-support gcalctool gcj-4.1-base gconf-editor gconf2 gconf2-common gdesklets gdm 
  gedit gedit-common gij-4.1 gimp gimp-data gimp-python gksu gnome-app-install gnome-applets gnome-applets-data gnome-bluetooth 
  gnome-control-center gnome-games gnome-games-data gnome-keyring gnome-mag gnome-media gnome-media-common gnome-nettool gnome-panel 
  gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-session gnome-system-monitor gnome-system-tools 
  gnome-terminal gnome-terminal-data gnome-utils gnome-volume-manager gnucash gnupg gok grub gstreamer0.10-plugins-bad-multiverse 
  gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-x gthumb gtk2-engines gtk2-engines-murrine gtk2-engines-pixbuf 
  gtk2-engines-ubuntulooks gtkhtml3.8 gucharmap hal hpijs hplip hplip-data imagemagick initramfs-tools iproute irssi java-gcj-compat 
  kismet kmymoney2 kplato language-support-en lftp libatspi1.0-0 libbonoboui2-0 libbonoboui2-common libcairo2 libcupsimage2 libcupsys2 
  libcurl3 libcurl3-gnutls libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserverui1.2-8 libeel2-2 libgail-common 
  libgail-gnome-module libgail18 libgconf2-4 libgdl-1-0 libgdl-1-common libgimp2.0 libgksu2-0 libglade2.0-cil libgnome-desktop-2 
  libgnome-media0 libgnome-window-settings1 libgnome2-canvas-perl libgnome2.0-cil libgnomebt0 libgnomecanvas2-0 libgnomecups1.0-1 
  libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 
  libgnomevfs2-common libgnomevfs2-extra libgnutls13 libgtk2.0-0 libgtk2.0-bin libgtk2.0-cil libgtk2.0-common libgtkhtml2-0 
  libgtkhtml3.8-15 libgtkspell0 libgutenprintui2-1 libhsqldb-java libimlib2-dev liblpint-bonobo0 libmetacity0 libpam-modules 
  libpanel-applet2-0 libpango1.0-0 libperl-dev libperl5.8 librdf0 librsvg2-2 librsvg2-common libsasl2-modules libsdl1.2-dev 
  libsdl1.2debian libsdl1.2debian-alsa libsmbclient libsoup2.2-8 libunicode-string-perl libvte-common libvte9 libwnck-common libx11-6 
  libx264-dev libxine1 linux-386 linux-generic linux-image-386 linux-image-generic linux-restricted-modules linux-restricted-modules-386 
  linux-restricted-modules-generic lvm2 mdadm metacity metacity-common mysql-admin nautilus nautilus-cd-burner nautilus-data netcat 
  network-manager ngrep notification-daemon ntfs-3g nvu openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common 
  openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk openoffice.org-impress 
  openoffice.org-java-common openoffice.org-math openoffice.org-style-industrial openoffice.org-writer openssh-client perl perl-base 
  perl-modules php5 php5-mysql pidgin planner python python-apt python-cairo python-epydoc python-examples python-glade2 python-gnome2 
  python-gnome2-desktop python-gnome2-extras python-gnomecanvas python-gobject python-gtk2 python-gtkhtml2 python-launchpad-integration 
  python-ldap python-minimal python-netcdf python-numeric python-numeric-ext python-pyopenssl python-soappy python-uno python-vte 
  python2.4 python2.4-examples python2.4-minimal python2.5-dev rhythmbox rss-glx samba-common scim scim-gtk2-immodule scim-modules-socket 
  scribus serpentine smbclient smbfs sound-juicer splix ssh-askpass-gnome streamripper subversion sun-java5-fonts sun-java5-jdk 
  sun-java5-plugin synaptic system-tools-backends thunar-volman tomboy totem totem-mozilla totem-xine ttf-gentium ttf-opensymbol 
  ubuntu-artwork ubuntu-standard udev update-manager update-notifier vino vlc winbind wireshark wvdial xbase-clients xfce4-places-plugin 
  xorg xsane xsane-common xscreensaver-data xscreensaver-gl xserver-xorg xserver-xorg-core xserver-xorg-input-all 
  xserver-xorg-input-elographics xserver-xorg-input-evdev xserver-xorg-input-kbd xserver-xorg-input-mouse xserver-xorg-input-synaptics 
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-apm xserver-xorg-video-ark xserver-xorg-video-ati 
  xserver-xorg-video-chips xserver-xorg-video-cirrus xserver-xorg-video-cyrix xserver-xorg-video-dummy xserver-xorg-video-fbdev 
  xserver-xorg-video-glint xserver-xorg-video-i128 xserver-xorg-video-i740 xserver-xorg-video-imstt xserver-xorg-video-mga 
  xserver-xorg-video-neomagic xserver-xorg-video-newport xserver-xorg-video-nsc xserver-xorg-video-nv xserver-xorg-video-rendition 
  xserver-xorg-video-s3 xserver-xorg-video-s3virge xserver-xorg-video-savage xserver-xorg-video-siliconmotion xserver-xorg-video-sis 
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-tga xserver-xorg-video-trident xserver-xorg-video-tseng 
  xserver-xorg-video-v4l xserver-xorg-video-vesa xserver-xorg-video-vga xserver-xorg-video-via xserver-xorg-video-vmware 
  xserver-xorg-video-voodoo xubuntu-desktop xutils yelp zenity 
The following partially installed packages will be configured:
  xfce4-dict-plugin xfce4-mount-plugin 
0 packages upgraded, 0 newly installed, 0 to remove and 529 not upgraded.
Need to get 0B/923kB of archives. After unpacking 0B will be used.
(Reading database ... 195347 files and directories currently installed.)
Preparing to replace alacarte 0.11.5-0ubuntu1 (using .../alacarte_0.11.5-0ubuntu1_all.deb) ...
Unpacking replacement alacarte ...
The generated cache was invalid.
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
The generated cache was invalid.
dpkg: error processing /var/cache/apt/archives/alacarte_0.11.5-0ubuntu1_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
The generated cache was invalid.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Preparing to replace apport 0.108 (using .../archives/apport_0.108_all.deb) ...
Unpacking replacement apport ...
The generated cache was invalid.
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
The generated cache was invalid.
dpkg: error processing /var/cache/apt/archives/apport_0.108_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
The generated cache was invalid.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Preparing to replace libdjvulibre15 3.5.20-2 (using .../libdjvulibre15_3.5.20-2_i386.deb) ...
Unpacking replacement libdjvulibre15 ...
The generated cache was invalid.
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
The generated cache was invalid.
dpkg: error processing /var/cache/apt/archives/libdjvulibre15_3.5.20-2_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
The generated cache was invalid.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/alacarte_0.11.5-0ubuntu1_all.deb
 /var/cache/apt/archives/apport_0.108_all.deb
 /var/cache/apt/archives/libdjvulibre15_3.5.20-2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up xfce4-mount-plugin (0.5.4-0ubuntu1) ...
The generated cache was invalid.
dpkg: error processing xfce4-mount-plugin (--configure):
 subprocess post-installation script returned error exit status 1
Setting up xfce4-dict-plugin (0.2.1-1ubuntu1) ...
The generated cache was invalid.
dpkg: error processing xfce4-dict-plugin (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 xfce4-mount-plugin
 xfce4-dict-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done 



The tail end of aptitude log in /var/log is:

[HOLD] xserver-xorg-video-via
[HOLD] xserver-xorg-video-vmware
[HOLD] xserver-xorg-video-voodoo
[HOLD] xubuntu-desktop
[HOLD] xutils
[HOLD] yelp
[HOLD] zenity
[????????] xfce4-dict-plugin
[????????] xfce4-mount-plugin
===============================================================================

Log complete.


Can someone guide me where to look to troubleshoot and fix this issue?

Thx,
Dan

---

### Post by Perfect Storm on 2008-04-24
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

Note, the servers may be very heated at this moment which can cause trouble upgrading.

---

### Post by dgavenda on 2008-04-26
Artificial Intelligence,

Not sure that helps at all.  Are their logs in /var/log or anywhere that will point me to the problems with:

Errors were encountered while processing:
xfce4-mount-plugin
xfce4-dict-plugin



I can't upgrade from cmd line (apt-get/aptitude) or gui (update-manager) due to these errors.  The error in full are in my first post.

Thx,
Dan

---

### Post by Perfect Storm on 2008-04-26
You could try getting them from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and install them manually.

---

### Post by dgavenda on 2008-04-28
No dice.  

dgavenda:~/downloads$ sudo dpkg -i xfce4-mount-plugin_0.5.4-0ubuntu1_i386.deb 
(Reading database ... 195347 files and directories currently installed.)
Preparing to replace xfce4-mount-plugin 0.5.4-0ubuntu1 (using xfce4-mount-plugin_0.5.4-0ubuntu1_i386.deb) ...
Unpacking replacement xfce4-mount-plugin ...
Setting up xfce4-mount-plugin (0.5.4-0ubuntu1) ...
The generated cache was invalid.
dpkg: error processing xfce4-mount-plugin (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 xfce4-mount-plugin
dgavenda:~/downloads$ 
dgavenda:~/downloads$ 
dgavenda:~/downloads$ 
dgavenda:~/downloads$ sudo dpkg -i xfce4-dict-plugin_0.2.1-1ubuntu1_i386.deb 
(Reading database ... 195347 files and directories currently installed.)
Preparing to replace xfce4-dict-plugin 0.2.1-1ubuntu1 (using xfce4-dict-plugin_0.2.1-1ubuntu1_i386.deb) ...
Unpacking replacement xfce4-dict-plugin ...
Setting up xfce4-dict-plugin (0.2.1-1ubuntu1) ...
The generated cache was invalid.
dpkg: error processing xfce4-dict-plugin (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 xfce4-dict-plugin


Where/how do I see logs about these errors?

I am trying to avoid removing xfce but I guess that is an alternative.  

Dan

---

### Post by dgavenda on 2008-04-28
I got it to upgrade by choosing another mirror.  Seems odd to me but it worked and I don't have the slightest idea why.  

Anyway, on to 8.04....

---

