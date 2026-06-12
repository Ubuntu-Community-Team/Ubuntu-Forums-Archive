---
title: "[SOLVED] software sources not appearing?"
date: 2008-11-13
forum: Installation &amp; Upgrades
---

### Post by -Outcast- on 2008-11-13
if I go into system-administration-Software Sources 

Nothing is happening. 

I have upgraded to 8.10 but Uograde manager is giving me the error that I cannot perform updates from ibex to hardy??

So something is wrong here

Any help appreciated!

---

### Post by zvacet on 2008-11-13
Just look in /etc/apt/  and see if you have two sources list( one with hardy repos and other with interpid).If that isthe case elete one with hardy repos and leave one with interpid.Or you can run this in terminal


```
cat /etc/apt/sources.list
```

and post it here.

---

### Post by -Outcast- on 2008-11-13
Thanks for the reply

> deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse


Update manager is giving me the following error 

> Can not upgrade

An upgrade from 'intrepid' to 'hardy' is not supported with this tool.

I've upgrade through apt get, but am still getting the above??

---

### Post by zvacet on 2008-11-13
As far as I can see your source list looks good.Did you looked at /etc/apt to see is that only source list you have,because it can happened that you have two sources list.One with old version and other with new one.That happened to me after upgrade.If that is a case simply delete source list with old repos (Hardy in this case) and after that run 

```
sudo apt-get update && sudo apt-get upgrade
```

You can also try to switch to main server in system>admin>software sources to see if that can make difference.

---

### Post by -Outcast- on 2008-11-13
Thanks, there was something there with Hardy on it so I deleted it. But still no luck. 

> system>admin>software sources

And nothing happens. 

I have > sudo apt-get update && sudo apt-get upgrade

It goes through everything fine

Then I try Update manager and again > Can not upgrade

An upgrade from 'intrepid' to 'hardy' is not supported with this tool. 

> Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_PH
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_PH
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_PH
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_PH
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_PH
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_PH
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_PH
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_PH
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/main Translation-en_PH
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/restricted Translation-en_PH
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/universe Translation-en_PH
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/multiverse Translation-en_PH
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-security/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  apparmor apparmor-utils apt apt-utils aptitude at-spi bind9-host bluez-cups
  bluez-gnome bluez-utils bogofilter-bdb brasero brltty brltty-x11 bug-buddy
  capplets-data clamav clamav-daemon clamav-freshclam clamav-milter conky
  contact-lookup-applet cpp cpp-4.2 cups-pdf cupsddk cupsddk-drivers cupsys
  cupsys-bsd cupsys-client cupsys-common cupsys-driver-gutenprint
  deskbar-applet dnsutils doc-base eog epiphany-browser-data epiphany-gecko
  evince evolution evolution-common evolution-data-server
  evolution-data-server-common f-spot file-roller filezilla filezilla-common
  filezilla-locales firefox firefox-3.0 firefox-3.0-gnome-support
  gappletviewer-4.2 gcalctool gcc gcc-4.2 gcc-4.2-base gcj-4.2-base
  gconf-editor gdesklets gdm gedit gedit-common ghostscript ghostscript-x gij
  gij-4.2 gimp gimp-data gnash gnash-common gnome-applets gnome-applets-data
  gnome-cards-data gnome-control-center gnome-core gnome-games
  gnome-games-data gnome-keyring gnome-mag gnome-main-menu gnome-media
  gnome-media-common gnome-mount gnome-netstatus-applet gnome-nettool
  gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits
  gnome-power-manager gnome-screensaver gnome-session gnome-settings-daemon
  gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal
  gnome-terminal-data gnome-themes gnome-utils gnome-volume-manager gnupg
  gparted gstreamer0.10-ffmpeg gstreamer0.10-plugins-good gtk2-engines
  gtk2-engines-murrine gtk2-engines-pixbuf gucharmap gvfs gvfs-backends hal
  hal-cups-utils hpijs hplip hplip-data human-theme initscripts
  java-gcj-compat java-gcj-compat-headless java-gcj-compat-plugin
  jockey-common jockey-gtk kdebase-runtime kdebase-runtime-bin-kde4 kdelibs5
  landscape-client lftp libaa1 libalut0 libatspi1.0-0 libavahi-ui0
  libbit-vector-perl libbonoboui2-0 libbonoboui2-common libcairo-perl
  libclamav-dev libcupsimage2 libcupsys2 libcurl3-gnutls libdirectfb-1.0-0
  libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6
  libedataserverui1.2-8 libeel2-2 libegroupwise1.2-13 libenchant1c2a
  libexchange-storage1.2-3 libgail-gnome-module libgcc1 libgcj-bc libgcj8-1
  libgcj8-1-awt libgdata-google1.2-1 libgdata1.2-1 libgdl-1-0 libgdl-1-common
  libggz2 libggzcore9 libggzmod4 libgimp2.0 libgksu2-0 libglade2-0
  libglade2.0-cil libglib-perl libgmime2.2-cil libgnome-media0
  libgnome-window-settings1 libgnome2-canvas-perl libgnome2-perl
  libgnome2-vfs-perl libgnome2.0-cil libgnomecanvas2-0 libgnomecups1.0-1
  libgnomekbd-common libgnomeprint2.2-0 libgnomeprint2.2-data
  libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeui-0
  libgnomeui-common libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra
  libgomp1 libgphoto2-2 libgphoto2-port0 libgpod3 libgraphviz4 libgs8
  libgtk-vnc-1.0-0 libgtk2-perl libgtk2.0-0 libgtk2.0-bin libgtk2.0-cil
  libgtkhtml2-0 libgtkhtml3.14-19 libgtkhtml3.16-cil libgtkmm-2.4-1c2a
  libgtksourceview2.0-0 libgtksourceview2.0-common libgweather1
  libhtml-parser-perl libkonq5 liblaunchpad-integration1 libldap-2.4-2
  liblocale-gettext-perl liblpint-bonobo0 libmagick10 libmetacity0
  libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil
  libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil
  libmono-system-data2.0-cil libmono-system-web1.0-cil
  libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil
  libmono2.0-cil libnautilus-burn4 libnautilus-extension1 libnet-dbus-perl
  libnm-glib0 libnm-util0 libopal-2.2 libpam-modules libpanel-applet2-0
  libphonon4 libpisock9 libpolkit-gnome0 libpt-1.10.10-plugins-v4l2
  libpulsecore5 libpurple0 libqt4-core libqt4-gui libqt4-qt3support libqt4-sql
  librsvg2-2 librsvg2-common libslab0 libsmbclient libsnmp15 libsoprano4
  libsoup2.4-1 libstdc++6 libstrigiqtdbusclient0 libswfdec-0.6-90
  libterm-readkey-perl libtext-charwidth-perl libtext-iconv-perl
  libtracker-gtk0 libvte9 libwnck22 libwxgtk2.6-0 libwxgtk2.8-0 libxi6
  libxine1 libxine1-bin libxine1-console libxine1-ffmpeg libxine1-misc-plugins
  libxine1-plugins libxine1-x libxml-parser-perl linux-generic
  linux-headers-generic linux-image-generic linux-restricted-modules-generic
  ltrace metacity metacity-common mono-common mono-gac mono-jit mono-runtime
  mousetweaks mozilla-plugin-gnash nautilus nautilus-cd-burner nautilus-data
  nautilus-image-converter nautilus-sendto nautilus-share network-manager
  network-manager-gnome notification-daemon ntfs-3g obex-data-server
  odbcinst1debian1 parted pciutils perl perl-base perl-modules pidgin
  pidgin-data policykit-gnome poppler-utils pulseaudio
  pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal
  pulseaudio-module-x11 python-apt python-clamav python-cups python-glade2
  python-gnome2 python-gnome2-desktop python-gnome2-extras python-gnomecanvas
  python-gobject python-gtk2 python-gtkhtml2 python-gtksourceview2
  python-pyatspi python-pyexiv2 python-vte python-wxgtk2.8 rhythmbox
  samba-common scim scim-bridge-client-gtk scim-gtk2-immodule
  scim-modules-socket seahorse seamonkey-browser sensors-applet smbclient
  sound-juicer splix ssh-askpass-gnome swfdec-mozilla synaptic
  system-config-printer-common sysvutils thunderbird tomboy toshset totem
  totem-common totem-gstreamer totem-mozilla totem-plugins tracker
  tracker-search-tool transmission-common transmission-gtk tsclient
  ubuntu-minimal unixodbc update-manager update-manager-core update-notifier
  upstart upstart-compat-sysv upstart-logd vbetool vinagre vino vlc vlc-nox
  vlc-plugin-pulse w3m winbind wodim wpasupplicant x11-common
  x11-xserver-utils xdg-user-dirs-gtk xorg xsane xsane-common
  xscreensaver-data xscreensaver-gl xserver-xorg xserver-xorg-core
  xserver-xorg-input-evdev xserver-xorg-input-kbd xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-apm xserver-xorg-video-ark
  xserver-xorg-video-ati xserver-xorg-video-chips xserver-xorg-video-cirrus
  xserver-xorg-video-dummy xserver-xorg-video-fbdev xserver-xorg-video-geode
  xserver-xorg-video-glint xserver-xorg-video-i128 xserver-xorg-video-i740
  xserver-xorg-video-intel xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-nsc xserver-xorg-video-nv xserver-xorg-video-openchrome
  xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-tga
  xserver-xorg-video-trident xserver-xorg-video-tseng xserver-xorg-video-v4l
  xserver-xorg-video-vesa xserver-xorg-video-vga xserver-xorg-video-vmware
  xserver-xorg-video-voodoo xulrunner-1.9 xulrunner-1.9-gnome-support yelp
  zenity
0 upgraded, 0 newly installed, 0 to remove and 425 not upgraded.


I notice 425 not upgraded???

---

### Post by zvacet on 2008-11-13
```
sudo apt-get dist-upgrade
```

---

### Post by -Outcast- on 2008-11-13
Getting closer 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  python-wxgtk2.8 seamonkey-browser thunderbird
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
544 not fully installed or removed.
Need to get 0B/30.8MB of archives.
After this operation, 414kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 171645 files and directories currently installed.)
Preparing to replace python-wxgtk2.8 2.8.7.1-0ubuntu3 (using .../python-wxgtk2.8_2.8.8.0-0ubuntu2_i386.deb) ...
Unpacking replacement python-wxgtk2.8 ...
dpkg: error processing /var/cache/apt/archives/python-wxgtk2.8_2.8.8.0-0ubuntu2_i386.deb (--unpack):
 failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wx/lib/flatnotebook.py': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace seamonkey-browser 1.1.12+nobinonly-0ubuntu0.8.04.1 (using .../seamonkey-browser_1.1.12+nobinonly-0ubuntu1_i386.deb) ...
Unpacking replacement seamonkey-browser ...
dpkg: error processing /var/cache/apt/archives/seamonkey-browser_1.1.12+nobinonly-0ubuntu1_i386.deb (--unpack):
 failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./usr/lib/seamonkey/components/libgklayout.so': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Updating seamonkey chrome registry...done.
Preparing to replace thunderbird 2.0.0.17+nobinonly-0ubuntu0.8.04.1 (using .../thunderbird_2.0.0.17+nobinonly-0ubuntu1_i386.deb) ...
Unpacking replacement thunderbird ...
dpkg: error processing /var/cache/apt/archives/thunderbird_2.0.0.17+nobinonly-0ubuntu1_i386.deb (--unpack):
 failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./usr/lib/thunderbird/components/libgklayout.so': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for man-db ...
/usr/bin/mandb: can't write to /var/cache/man/3087: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/sv/3087: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/gl/3087: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/it/3087: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/zh_TW/3087: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/fr.ISO8859-1/3087: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/es/3087: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/id/3087: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/pl.ISO8859-2/3087: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/it.UTF-8/3087: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/pt_BR/3087: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/ko/3087: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/de.UTF-8/3087: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/ja/3087: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/pl/3087: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/fr/3087: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/tr/3087: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/ru/3087: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/pl.UTF-8/3087: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/cs/3087: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/de/3087: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/it.ISO8859-1/3087: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/zh_CN/3087: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/fr.UTF-8/3087: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/pa/3087: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/fi/3087: No space left on device
/usr/bin/mandb: can't write to /var/cache/man/hu/3087: No space left on device
/usr/bin/mandb: can't create index cache /var/cache/man/oldlocal/3087: No space left on device
/usr/bin/mandb: can't create index cache /var/cache/man/local/3087: No space left on device
Processing triggers for menu ...
Errors were encountered while processing:
 /var/cache/apt/archives/python-wxgtk2.8_2.8.8.0-0ubuntu2_i386.deb
 /var/cache/apt/archives/seamonkey-browser_1.1.12+nobinonly-0ubuntu1_i386.deb
 /var/cache/apt/archives/thunderbird_2.0.0.17+nobinonly-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



Update manager now freezes too

---

### Post by -Outcast- on 2008-11-13
Just ran it again and it kicked in!!

All up and running again. 

Much thanks and appreciation for your help!!

---

### Post by zvacet on 2008-11-14
I´m glad  you are enjoying Ubuntu again.

---

