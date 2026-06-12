---
title: "Mirroring/backing up an installation?"
date: 2006-06-20
forum: Installation &amp; Upgrades
---

### Post by johann_p on 2006-06-20
Is there a way in Ubuntu to automatically install a machine just like another one? Is this possible at least for the set of installed packages? 

This would be extremely important if an admin has to keep many machines installed with identical packages or other configuration stuff. 

It would also help immensely to re-install the system after some serious problem or if moving to a different/new computer.

What are the options here?

---

### Post by johann_p on 2006-06-22
Hmm ... no way to do this except for repeating everything manually?
How are other people doing this??

---

### Post by johann_p on 2006-06-25
I assume that means nothing of this is possible then and Ubuntu only allows manually redoing everything on every machine :(

---

### Post by sickdude on 2006-06-25
maybe write a litte bash script?

but i just made a post sounding just like yours, and im waiting for a reply to :(

---

### Post by aysiu on 2006-06-25
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html) will allow you to do bulk mirrored installs, but it won't keep the computers mirrored thereafter.

---

### Post by johann_p on 2006-06-26
[quote=aysiu][http://www.psychocats.net/ubuntu/partimage.html]("http://www.psychocats.net/ubuntu/partimage.html") will allow you to do bulk mirrored installs, but it won't keep the computers mirrored thereafter.[/quote] 
Yes ... I was looking for a solution that would only backup up the "metainformation", i.e. the list of packages and maybe configuration files, not all the data itself. The difference is probably several orders of magnitude of data space. Backing up the partition would need several GB -- backing up the list of packages and a few configuration files probably just a few kB. Which is even more relevant especially when you want to keep a history of installations.

Personally I think that is a rather natural idea -- it would be really odd that such a thing does not exist yet.

---

### Post by aysiu on 2006-06-26
Well, at this point, for me and a lot of other people, hard drive space is a lot "cheaper" than time.

I'd rather have a full partition image backup (which is about 3.2 GB) that can be restored in a matter of minutes than have to wait for the entire operating system to be reinstalled and then all the packages to be downloaded and reinstalled.

---

### Post by johann_p on 2006-06-26
[quote=aysiu]Well, at this point, for me and a lot of other people, hard drive space is a lot "cheaper" than time.

I'd rather have a full partition image backup (which is about 3.2 GB) that can be restored in a matter of minutes than have to wait for the entire operating system to be reinstalled and then all the packages to be downloaded and reinstalled.[/quote]

Glad if that is what you need or want, but it is not what I was looking for.

---

### Post by aysiu on 2006-06-26
[QUOTE=johann_p]Glad if that is what you need or want, but it is not what I was looking for.[/QUOTE]
Well, if you have one installation the way you want it, you could do this: ```
dpkg -l installed.txt
``` That will get what packages you have installed into a text file (along with the descriptions).

Then, from OpenOffice Calc, you can open the text file as text CSV and isolate only the names of the packages (not the descriptions).

Do a little find/replace in OpenOffice Writer to get rid of the carriage returns and make them spaces instead.

Then change the text file into a bash script that looks something like this: ```
#!/bin/bash
sudo aptitude update
sudo aptitude install abiword abiword-common abiword-plugins acpi acpi-support acpid acroread acroread-plugins adduser adept akregator alacarte alsa-base alsa-oss alsa-utils amarok amarok-xine anacron anthy apmd app-install-data app-install-data-commercial appres apt apt-utils aptitude ark arts artsbuilder aspell aspell-en at at-spi avahi-daemon avifile-win32-plugin banshee banshee-daap base-files base-passwd bash bc beforelight belocs-locales-bin bicyclerepair bind9-host binfmt-support binutils binutils-static bitmap bittorrent blt bluez-cups bluez-pcmcia-support bluez-pin bluez-utils bochsbios bogofilter bogofilter-bdb bogofilter-common brltty brltty-x11 bsdmainutils bsdutils bsh bug-buddy build-essential bum busybox-initramfs bzip2 ca-certificates cabextract capplets-data cdparanoia cdrdao cdrecord console-common console-data console-tools contact-lookup-applet coreutils cpio cpp cpp-4.0 cron cupsys cupsys-bsd cupsys-client cupsys-driver-gutenprint dbus dbus-1-utils dc debconf debconf-i18n debconf-utils debhelper debianutils debootstrap deborphan debtags defoma deskbar-applet desktop-file-utils dhcp3-client dhcp3-common dia dia-common dia-libs dialog dictionaries-common diff discover1 discover1-data diveintopython dmidecode dmsetup dnsutils doc-base doc-debian docbook-xml dosfstools dpkg dpkg-dev dselect dvd+rw-tools e2fslibs e2fsprogs easytag ed editres eject ekiga enscript eog epiphany-browser epiphany-extensions esound esound-common ethtool evince evms evms-ncurses evolution evolution-data-server evolution-exchange evolution-plugins evolution-webcal example-content fastjar fdutils festival festlex-cmu festlex-poslex festvox-kallpc16k file file-roller findutils finger firefox firefox-gnome-support flashplugin-nonfree fontconfig foo2zjs foomatic-db foomatic-db-engine foomatic-db-gutenprint foomatic-db-hpijs foomatic-filters foomatic-filters-ppds fortune-mod fortunes-min fping freeglut3 fstobdf ftp g++ g++-4.0 gaim gaim-data gamin gcalctool gcc gcc-3.3-base gcc-4.0 gcc-4.0-base gcj-4.0-base gcj-4.1-base gconf gconf-editor gconf2 gconf2-common gcursor gda2-postgres gdb gdebi gdk-imlib11 gdm gedit gedit-common gettext gettext-base gij-4.1 gimp gimp-data gimp-print gimp-python gksu gnome-about gnome-accessibility-themes gnome-app-install gnome-applets gnome-applets-data gnome-bin gnome-btdownload gnome-control-center gnome-cups-manager gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-icon-theme gnome-keyring gnome-libs-data gnome-mag gnome-media gnome-menus gnome-mime-data gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-spell gnome-splashscreen-manager gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes gnome-utils gnome-volume-manager gnome2-user-guide gnopernicus gnumeric-common gnumeric-gtk gnupg gok gqview grep grepmap groff-base grub gs-common gs-esp gsfonts gsfonts-x11 gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-tools gstreamer0.10-x gthumb gtk2-engines-clearlooks gtk2-engines-crux gtk2-engines-gtk-qt gtk2-engines-highcontrast gtk2-engines-industrial gtk2-engines-lighthouseblue gtk2-engines-mist gtk2-engines-pixbuf gtk2-engines-redmond95 gtk2-engines-smooth gtk2-engines-thinice gtk2-engines-ubuntulooks gtk2-engines-xfce gtkhtml3.8 gtkorphan gucharmap guile-1.6 guile-1.6-libs gwenview gzip hal hal-device-manager hdparm hfsplus hfsutils hicolor-icon-theme hostname hotkey-setup hpijs hplip hplip-data hplip-ppds html2text hwdata hwdb-client iceauth ico ifupdown ijsgutenprint imagemagick imake imlib-base info initramfs-tools initscripts inkscape inputattach intltool-debian iproute iptables iputils-arping iputils-ping iputils-tracepath irssi iso-codes java-common java-gcj-compat jfsutils juk k3b kaddressbook kaffeine kaffeine-xine kamera karm katalog katapult kate kaudiocreator kcontrol kcron kde-guidance kde-style-lipstik kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-bin kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdm kdnssd keep kfind kghostview khelpcenter kicker kid3 kio-apt kio-locate klaptopdaemon klibc-utils klipper klogd kmail kmailcvt kmenuedit kmilo kmix kmplayer-base kmplayer-konq-plugins knetworkconf knotes koffice-data koffice-libs kolourpaint konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krename krfb krita krita-data kscd kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin kspread ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kvpnc kwalletmanager kwin kwin-baghira kwin-style-crystal kword kword-data lame landscape-client language-pack-en language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base language-selector language-selector-common language-selector-qt language-support-en laptop-detect laptop-mode-tools launchpad-integration less lftp liba52-0.7.4 libaa1 libacl1 libadns1 libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libakode2 libakode2-mpeg libanthy0 libao2 libapm1 libart-2.0-2 libart2 libarts1-akode libarts1c2a libartsc0 libasound2 libaspell15 libatk1-ruby libatk1.0-0 libatm1 libatspi1.0-0 libattr1 libaudio2 libaudiofile0 libavahi-cil libavahi-client3 libavahi-common-data libavahi-common3 libavahi-core4 libavahi-glib1 libavahi-qt3-1 libavc1394-0 libavifile-0.7c2 libbakery-2.4-1 libbeagle0 libbind9-0 libblkid1 libbluetooth1 libbonobo2 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libbrlapi1 libbtctl2 libbz2-1.0 libc6 libc6-dev libc6-i686 libcairo-ruby libcairo2 libcamel1.2-8 libcap1 libcdio6 libcdparanoia0 libchewing-data libchewing2 libcomerr2 libcompfaceg1 libcompress-zlib-perl libconsole libcroco3 libcupsimage2 libcupsys2 libcurl3 libcurl3-gnutls libdaemon0 libdb4.3 libdbus-1-2 libdbus-1-cil libdbus-glib-1-2 libdbus-qt-1-1c2 libdevmapper1.02 libdiscover1 libdjvulibre15 libdmx1 libdns21 libdrm2 libdv4 libdvdread3 libebook1.2-5 libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1 libedataserver1.2-7 libedataserverui1.2-6 libedit2 libeel2-2 libeel2-data libegroupwise1.2-9 libelfg0 libenchant1c2a libesd-alsa0 libestools1.2 libevms-2.5 libexchange-storage1.2-1 libexif12 libexo-0.3-0 libexpat1 libfaac0 libflac++5c2 libflac7 libfontconfig1 libfontenc1 libfreetype6 libfribidi0 libfs6 libgadu3 libgail-common libgail-gnome-module libgail17 libgal23 libgamin0 libgc1c2 libgcc1 libgcj-common libgcj6 libgcj7 libgcj7-jar libgconf11 libgconf2-4 libgconf2-ruby libgconf2.0-cil libgcrypt11 libgd2-noxpm libgda2-3 libgda2-common libgdamm1.3-8 libgdbm3 libgdk-pixbuf-gnome2 libgdk-pixbuf2 libgdk-pixbuf2-ruby libgdl-1-0 libgdl-1-common libgdome2-0 libgdome2-cpp-smart0c2a libgeoip1 libggi-target-x libggi2 libghttp1 libgii0 libgii0-target-x libgimp2.0 libgksu1.2-1 libgksuui1.0-1 libgl1-mesa libgl1-mesa-dri libglade-gnome0 libglade0 libglade2-0 libglade2-ruby libglade2.0-cil libglademm-2.4-1c2a libglew1 libglib-perl libglib1.2 libglib2-ruby libglib2.0-0 libglib2.0-cil libglib2.0-data libglibmm-2.4-1c2a libglu1-mesa libgmp3c2 libgnome-desktop-2 libgnome-keyring0 libgnome-mag2 libgnome-menu2 libgnome-pilot2 libgnome-speech3 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome2.0-cil libgnome32 libgnomebt0 libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1 libgnomecupsui1.0-1c2a libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomesupport0 libgnomeui-0 libgnomeui-common libgnomeui32 libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgnorba27 libgnorbagtk0 libgnucrypto-java libgnutls12 libgoffice-1-common libgoffice-gtk-1-2 libgpg-error0 libgpgme11 libgphoto2-2 libgphoto2-port0 libgpmg1 libgpod0 libgsf-1-113 libgsf-1-common libgsl0 libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libgtk1.2 libgtk1.2-common libgtk2-gladexml-perl libgtk2-perl libgtk2-ruby libgtk2.0-0 libgtk2.0-bin libgtk2.0-cil libgtk2.0-common libgtkhtml1.1-3 libgtkhtml2-0 libgtkhtml3.8-15 libgtkmathview0c2a libgtkmm-2.4-1c2a libgtksourceview-common libgtksourceview1.0-0 libgtkspell0 libgtop2-7 libgucharmap4 libguile-ltdl-1 libguppi16 libgutenprint2 libgutenprintui2-1 libgwrapguile1 libhal-storage1 libhal1 libhfsp0 libhsqldb-java libice6 libicu34 libid3-3.8.3c2a libid3tag0 libidl0 libidn11 libieee1284-3 libijs-0.35 libimlib2 libipoddevice0 libisc11 libisccc0 libisccfg1 libiso9660-4 libiw28 libjasper-1.701-1 libjaxp1.2-java libjessie-java libjline-java libjpeg-progs libjpeg62 libk3b2 libkcal2b libkcddb1 libkdepim1a libkipi0 libkleopatra1 libklibc libkmime2 libkonq4 libkpathsea4 libkpimexchange1 libkpimidentities1 libkrb53 libkscan1 libksieve0 libktnef1 liblame0 liblaunchpad-integration0 liblcms1 libldap2 liblircclient0 liblocale-gettext-perl liblockdev1 liblpint-bonobo0 libltdl3 liblwres9 liblzo1 libmad0 libmagic1 ttf-bitstream-vera ttf-dejavu ttf-devanagari-fonts ttf-freefont ttf-gentium ttf-gujarati-fonts ttf-indic-fonts ttf-kannada-fonts ttf-kochi-gothic ttf-kochi-mincho ttf-lao ttf-malayalam-fonts ttf-mgopen ttf-opensymbol ttf-oriya-fonts ttf-punjabi-fonts ttf-tamil-fonts ttf-telugu-fonts ttf-thai-tlwg ubuntu-artwork ubuntu-base ubuntu-desktop ubuntu-docs ubuntu-keyring ubuntu-minimal ubuntu-sounds ubuntu-standard ucf udev unattended-upgrades unzip update-manager update-notifier usbutils usplash util-linux vbetool vcdimager vgabios viewres vim vim-common vim-runtime vino vmware-player vmware-player-kernel-modules vmware-player-kernel-modules-2.6.15-23 vmware-player-kernel-modules-2.6.15-25 vmware-player-kernel-source vnc-common vorbis-tools vpnc w3c-dtd-xhtml w3m wamerican wbritish wget whiptail whois wireless-tools wlassistant wpasupplicant wvdial x-ttcidfont-conf x-window-system-core x11-common x11perf xarchiver xauth xbase-clients xbiff xcalc xclipboard xclock xconsole xcursor-themes xcursorgen xditview xdpyinfo xdriinfo xev xeyes xf86dga xfburn xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-fsguard-plugin xfce4-icon-theme xfce4-mailwatch-plugin xfce4-mcs-manager xfce4-mcs-plugins xfce4-mixer xfce4-mixer-alsa xfce4-mount-plugin xfce4-netload-plugin xfce4-panel xfce4-quicklauncher-plugin xfce4-screenshooter-plugin xfce4-session xfce4-systemload-plugin xfce4-taskmanager xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfd xfdesktop4 xfmedia xfonts-100dpi xfonts-75dpi xfonts-base xfonts-scalable xfonts-utils xfontsel xfprint4 xfsprogs xfwm4 xfwm4-themes xgamma xgc xhost xinit xkbutils xkeyboard-config xkill xload xlogo xlsatoms xlsclients xlsfonts xmag xman xmessage xml-core xmodmap xmore xnest xpmutils xprop xrandr xrdb xrefresh xresprobe xrgb xsane xsane-common xscreensaver xscreensaver-data xscreensaver-gl xserver-xorg xserver-xorg-core xserver-xorg-driver-all xserver-xorg-driver-apm xserver-xorg-driver-ark xserver-xorg-driver-ati xserver-xorg-driver-chips xserver-xorg-driver-cirrus xserver-xorg-driver-cyrix xserver-xorg-driver-dummy xserver-xorg-driver-fbdev xserver-xorg-driver-glint xserver-xorg-driver-i128 xserver-xorg-driver-i740 xserver-xorg-driver-i810 xserver-xorg-driver-imstt xserver-xorg-driver-mga xserver-xorg-driver-neomagic xserver-xorg-driver-newport xserver-xorg-driver-nsc xserver-xorg-driver-nv xserver-xorg-driver-rendition xserver-xorg-driver-s3 xserver-xorg-driver-s3virge xserver-xorg-driver-savage xserver-xorg-driver-siliconmotion xserver-xorg-driver-sis xserver-xorg-driver-sisusb xserver-xorg-driver-tdfx xserver-xorg-driver-tga xserver-xorg-driver-trident xserver-xorg-driver-tseng xserver-xorg-driver-v4l xserver-xorg-driver-vesa xserver-xorg-driver-vga xserver-xorg-driver-via xserver-xorg-driver-vmware xserver-xorg-driver-voodoo xserver-xorg-input-all xserver-xorg-input-elographics xserver-xorg-input-evdev xserver-xorg-input-kbd xserver-xorg-input-mouse xserver-xorg-input-synaptics xserver-xorg-input-wacom xset xsetmode xsetpointer xsetroot xsltproc xsm xstdcmap xterm xtrap xubuntu-artwork-usplash xubuntu-default-settings xubuntu-desktop xubuntu-docs xutils xvidtune xvinfo xvncviewer xwd xwininfo xwud yelp zenity zip zlib1g
``` Or if you haven't even installed Ubuntu yet, even better.

Install one and configure it the way you want it. As you're configuring it, make sure every configuration is done by command-line commands and copy and paste each command into a text file and make that text file a shell script.

---

### Post by johann_p on 2006-06-28
Somebody has pointed out kickstart to me: this seems to indeed do more or less what I want.

It is available from an Ubuntu repository as system-config-kickstart

Unfortunately, it does not work: entering "systgem-config-kickstart --generate filename" results in an error message:
Traceback (most recent call last):
  File "/usr/share/system-config-kickstart/system-config-kickstart.py", line 58, in ?
    useCliMode(value)
  File "/usr/share/system-config-kickstart/system-config-kickstart.py", line 41, in useCliMode
    import profileSystem
  File "/usr/share/system-config-kickstart/profileSystem.py", line 23, in ?
    import language_backend
ImportError: No module named language_backend

Looks like the package is just broken :(

---

### Post by johann_p on 2006-12-06
It seems system-config-kickstart is still broken in Edgy and there is still no way to do this.

It is quite easy to save the installation information in OpenSuse and do an automatic installation with this information on a different system -- or many different systems. Or, on the same system if there is a hardware failure.

---

### Post by passonno on 2007-09-20
Actually the code is as follows(you forgot the '>')

dpkg -l > installed.txt

---

