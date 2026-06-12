---
title: "Upgrade by HAND"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by morequarky on 2006-06-05
1. Ok, I have a 4+gig backup file. Hope it works. Tar through no errors.
2. I have backed up my source.list
3. I have copied and pasted the new source.list ubuntu supplied.
4. I ran "update"
5. I ran "dist-upgrade" BUT I PRESSED NO.

I am worried about space. On my messed up partitions.

Need to get 684MB of archives.
After unpacking 354MB of additional disk space will be used.

What does that mean space wise?  684MB in '/var'?  354MB in '/'?

Where is this stored to?  Can I change the directory where packages are downloaded to?  

I have 61 packages to UNINSTALL.  That should help a lot.

I have LAMP on Breezy.  Will it be destroyed?

---

### Post by llamakc on 2006-06-05
dist-upgrade is what you wanted to do.

---

### Post by morequarky on 2006-06-05
I ran dist-upgrade because I wanted to see what was going to be installed and what was going to be removed and the like.

I now have run dist-upgrade hoping not to run out of space.

I have run into an error.  Maybe others have seen this.

dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on pcmciautils; however:
  Package pcmciautils is not installed.
 ubuntu-minimal depends on wpasupplicant; however:
  Package wpasupplicant is not installed.
dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ubuntu-minimal

---

### Post by morequarky on 2006-06-05
I am still running Breezy.. I have not and will not reboot.  Ubuntu-minimal is vital.

HELP!!!

---

### Post by morequarky on 2006-06-05
Here is exactly what I did.

After downloaded all required packages it started removing unneeded packages. And configuring.

At one point it asked if I wanted to change some ???/login???  It gave me four options.  I pressed D to look at the changes.

I scrolled down by pressing enter and space.  After reaching the bottom I didn't know how to get out of the program.

I pressed ctrl-z which just suspended it.

I used fg or something to get back in it.

I pressed ctrl-c to get out.  I then had to run 

sudo dpkg --configure -a to get it back working.

It promply put me at the same four options for /???/login???
I pressed N to NOT CHANGE the file.

The VERY NEXT THING IT DID was 

dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on pcmciautils; however:
  Package pcmciautils is not installed.
 ubuntu-minimal depends on wpasupplicant; however:
  Package wpasupplicant is not installed.
dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ubuntu-minimal

and kicked me out.

---

### Post by morequarky on 2006-06-05
Should I try the following?  

sudo apt-get -f remove

I guess it wouldn't be a good idea, but I don't know.

---

### Post by pellgarlic on 2006-06-05
[QUOTE=llamakc]dist-upgrade is what you wanted to do.[/QUOTE]

i believe morequarky pressed "no" because of concerns about lack of hard drive space, not because the dist-upgrade was unwanted.

@morequarky, have you read this sticky: [http://ubuntuforums.org/showthread.php?t=186672](http://ubuntuforums.org/showthread.php?t=186672)

it seems to concern problems with borken dependencies, and ubuntu_demon seems to have done a thorough job of covering a lot of different possible problems. don't know how relevant it is to your problem, but it might be worth reading. 

the other thing you could try, is to take note of the "missing dependencies" (i.e. pcmciautils and wpasupplicant) and install them first, then retry the dist-upgrade.

---

### Post by morequarky on 2006-06-05
PellGarlic:

I read that thread a few times.  My case isn't listed.  I can't remove "ubuntu-minimal as the thread says and I can't remove any of my dependancies because my system doesn't have them either.

I tried apt-get "missing dependency" but they don't existe.

So ubuntu-minimal requires no-existing packages to run?  That doesn't make sense.  How do I download non-existing packages?  Do I need to include mulitverse or some other repository?  Well, probably not, because the basic ubuntu-minimal should have all its dependencies in "main"

That is why I can't get an answer from anyone.  Dapper gets to a point in installation where it desides to act stupid and ask for something not there.

---

### Post by morequarky on 2006-06-05
From this thread I got an idea.  [http://ubuntuforums.org/showthread.php?t=189050](http://ubuntuforums.org/showthread.php?t=189050)

I will run "apt-get dist-upgrade" again to see what happends.

It tell me:

>sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  ubuntu-minimal: Depends: pcmciautils but it is not installed
                  Depends: wpasupplicant but it is not installed
E: Unmet dependencies. Try using -f.

>sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libssl0.9.8 libsysfs2 lsb-base module-init-tools pcmciautils
The following packages will be REMOVED:
  ubuntu-minimal
The following NEW packages will be installed:
  libssl0.9.8 libsysfs2 pcmciautils
The following packages will be upgraded:
  lsb-base module-init-tools
2 upgraded, 3 newly installed, 1 to remove and 1057 not upgraded.
1 not fully installed or removed.
Need to get 0B/2740kB of archives.
After unpacking 6586kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.


Should I say yes?  Yes seems nuts.  I can't remove ubuntu-minimal.  Ubuntu-minimal is required.

HELP!!!!

---

### Post by morequarky on 2006-06-05
How do I force linux to install a dowloaded package!!!

You can see from the above list that I HAVE the files to install but stupid apt-get refuses to install anything.

Thanks

---

### Post by morequarky on 2006-06-05
ah shot, I ran 

"apt-get clean"

Now I have to download stuff again.  apt-get won't listen to me.  I want it to install a package and it wants to lolly gag around with broken stuff.  Apt-get won't let me do what I want to fix the issues.  Apt-get needs to SHUT UP and download the files I SAY.  does dselect work?

How do I download packages manually?  How do I install them manually?  APT-GET is STUPID

---

### Post by morequarky on 2006-06-05
I have been trying to upgrade this computer now for over 12 hours.  The computer insists on removing ubuntu-minumal.

Linux claims to be so much about control, but I CANT CONTROL APT-GET or SYNOPTIC with my CD, why?  I DON'T KNOW. 

WHAT is wrong?  Why can't I CONTROL the computer like so many linux people claim?

This is extremely frustrating. 

Is anyone out there who can give me some advice?

---

### Post by llamakc on 2006-06-05
Which package do you want to install? You can download packages from packages.ubuntu.com. You can install them at the commandline with:

dpkg -i /path/to/nameof.db

And if we need to force or overwrite there are ways to do that also. In the meanwhile lets refocus your frustration to the problems. 

In your first post you said you did NOT run dist-upgrade. When you pressed "NO" did it do a regular package upgrade at that point? I believe I misunderstood you when I replied earlier.

Have you ran out of space yet?

What does `df -h` report?

---

### Post by morequarky on 2006-06-05
I believe space is not a problem now.

>df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             449M  195M  231M  46% /
tmpfs                 237M     0  237M   0% /dev/shm
tmpfs                 237M   13M  225M   6% /lib/modules/2.6.12-10-386/volatile
/dev/hda9              54G  9.8G   41G  20% /home
/dev/hda1             5.9G  5.7G  174M  98% /media/hda1
/dev/hda6             361M  8.1M  334M   3% /srv
/dev/hda8             2.8G  2.1G  576M  79% /usr
/dev/hda5             897M  108M  742M  13% /var
/dev/hda10            8.7G  717M  8.0G   9% /media/fat32
/dev/hdc              693M  693M     0 100% /media/cdrom0

My problem stems from ubuntu-minimal.  apt-get wants to uninstall it.  But the forum says not to.  apt-get wants to install a few other things.

I want to force apt-get to install what it wants to install and upgrade what it wants to upgrade, but NOT remove ubuntu-minimal....now I don't even know if that is what I should do.

I have one "broken" package it seems.  ubuntu-minimal.  Why I don't know?

Please read the whole thread.  You'll understand my situation and processes the fastest that way.

---

### Post by morequarky on 2006-06-05
>>sudo apt-get dist-upgrade

Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  ubuntu-minimal: Depends: [COLOR="Blue"]pcmciautils[/COLOR] but it is not installed
                  Depends: wpasupplicant but it is not installed
E: Unmet dependencies. Try using -f.

>>sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libssl0.9.8 libsysfs2 lsb-base module-init-tools [COLOR="Blue"]pcmciautils[/COLOR]
[COLOR="Red"]The following packages will be REMOVED:
  ubuntu-minimal[/COLOR]
The following NEW packages will be installed:
  libssl0.9.8 libsysfs2 pcmciautils
The following packages will be upgraded:
  lsb-base module-init-tools
2 upgraded, 3 newly installed, 1 to remove and 1057 not upgraded.
1 not fully installed or removed.
Need to get 2740kB of archives.
After unpacking 6586kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

What should I do?

---

### Post by llamakc on 2006-06-05
IF X is currently running, start a terminal.

do:

sudo aptitude dist-upgrade

When in Aptitude you can press F-10 and right-arrow over to OPTIONS | DEPENDENCY HANDLING and report back what is and is not check-marked.

Has this been tried yet?

---

### Post by llamakc on 2006-06-05
At this point I would back up my data elsewhere just in case something ends up hosed.

---

### Post by morequarky on 2006-06-05
I don't have the program aptitude installed it seems.
```

>>sudo aptitude dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
The following NEW packages will be automatically installed:
  alacarte amule-common app-install-data app-install-data-commercial at-spi
  brltty brltty-x11 busybox-initramfs ca-certificates
  cupsys-driver-gutenprint dcraw deskbar-applet ekiga example-content
  festival festlex-cmu festlex-poslex festvox-kallpc16k foo2zjs
  foomatic-db-gutenprint gcj-4.0-base gcj-4.1-base gconf2-common gdebi
  gij-4.1 gimp-print gnome-accessibility-themes gnome-mag
  gnome-power-manager gnome-screensaver gnopernicus gok gstreamer0.10-alsa
  gstreamer0.10-esd gstreamer0.10-gnomevfs gstreamer0.10-plugins-base
  gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good
  gstreamer0.10-tools gstreamer0.10-x gtk2-engines-highcontrast
  gtk2-engines-ubuntulooks gutenprint-locales hplip ijsgutenprint im-switch
  inputattach irssi iso-codes kdelibs4c2a landscape-client
  language-selector-common laptop-mode-tools libalut0 libapt-pkg-perl
  libarts1c2a libatspi1.0-0 libavahi-client3 libavahi-common-data
  libavahi-common3 libavahi-glib1 libavahi-qt3-1 libavifile-0.7c2
  libbakery-2.4-1 libbakery-2.4-common libbeagle0 libbrlapi1 libbtctl2
  libcal3d11c2a libcamel1.2-8 libcdio6 libcrypto++5.2c2a libcupsys2
  libcurl3-gnutls libdbus-1-2 libdbus-glib-1-2 libdevmapper1.02 libdmx1
  libdns21 libdrm2 libedataserver1.2-7 libegroupwise1.2-9 libenchant1c2a
  libestools1.2 libexchange-storage1.2-1 libgail-gnome-module libgcj7
  libgcj7-jar libgdl-1-0 libgdl-1-common libgksu1.2-1 libgksuui1.0-1
  libglademm-2.4-1c2a libglibmm-2.4-1c2a libgmp3c2 libgnome-mag2
  libgnome-speech3 libgnome-vfsmm-2.6-1c2a libgnomebt0
  libgnomecupsui1.0-1c2a libgnomevfs2-bin libgnomevfs2-extra libgnutls12
  libgpod-common libgpod0 libgsf-1-113 libgsf-1-common
  libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libgtkmm-2.4-1c2a
  libgtop2-7 libgutenprint2 libgutenprintui2-1 libicu34 libid3-3.8.3c2a
  libisc11 libiso9660-4 libjack0.100.0-0 libjline-java libkpathsea4
  liblwres9 libmagick9 libmjpegtools0c2a libmusicbrainz4c2a
  libmysqlclient15off libnautilus-burn3 libneon25 libnetcdf3 libnotify1
  libopal-2.2.0 libopenal0a libopenexr2c2a libopenobex-1.0-0
  libparted1.6-13 libpoppler1 libpoppler1-glib libpt-1.10.0
  libpt-plugins-avc libpt-plugins-dc libpt-plugins-oss libqscintilla6
  libquicktime0 libscim8c2a libsexy2 libsigc++-2.0-0c2a libsmpeg0 libsnmp9
  libssl0.9.8 libsysfs2 libtag1c2a libtidy-0.99-0 libtotem-plparser1
  libuniconf4.2 libwavpack0 libwpd8c2a libwvstreams4.2-base
  libwvstreams4.2-extras libxfont1 libxine-extracodecs libxine-main1
  libxml++2.6c2a libxmlsec1 libxmlsec1-nss libxmlsec1-openssl libxplc0.3.13
  libxvmc1 linux-image-2.6.15-23-386 linux-restricted-modules-2.6.15-23-386
  mcpp mdetect min12xxw mplayer mplayer-skins mysql-client-5.0
  mysql-server-5.0 openoffice.org openoffice.org-base openoffice.org-calc
  openoffice.org-common openoffice.org-core openoffice.org-draw
  openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk
  openoffice.org-help-en-us openoffice.org-impress
  openoffice.org-java-common openoffice.org-l10n-common
  openoffice.org-l10n-en-gb openoffice.org-l10n-en-us
  openoffice.org-l10n-en-za openoffice.org-math
  openoffice.org-thesaurus-en-us openoffice.org-writer pcmciautils
  poppler-utils python-beagle python-gnome2-desktop python-gst0.10
  python-libxml2 python2.4-gnome2-desktop python2.4-gobject
  python2.4-soappy radeontool readline-common scim scim-gtk2-immodule
  scim-modules-socket screensaver-default-images smartdimmer
  tangerine-icon-theme tango-icon-theme tango-icon-theme-common
  thunderbird-locale-en-gb ttf-arphic-ukai ttf-arphic-uming ttf-dejavu
  ttf-gentium ttf-lao ttf-thai-tlwg unattended-upgrades vim-runtime
  wpasupplicant x11-common xcursor-themes xserver-xorg-input-synaptics
The following packages will be automatically REMOVED:
  busybox-cvs-initramfs cupsys-driver-gimpprint-data gnomemeeting hotplug
  hplip-base ifrename libbakery-2.3-15 libbakery-2.3-common libcal3d10c2
  libcamel1.2-6 libdbus-1-1 libdbus-glib-1-1 libgksu1.2-0 libgksuui1.0-0
  libgnomecupsui1.0-1 libid3-3.8.3c2 libmusicbrainz4c2 libnautilus-burn2
  libnotify0 libopenal0 libopenh323-1.15.3c2 libpt-1.8.3c2 libsmpeg0c2
  libwpd8c2 libxml++2.6c2 netcdfg3 openoffice.org-debian-files
  openoffice.org2-common openoffice.org2-core openoffice.org2-help-en-us
  openoffice.org2-java-common openoffice.org2-l10n-en-us smeg x-common
  xmkmf xorg-common xorg-driver-synaptics xserver-common
The following NEW packages will be installed:
  alacarte amule-common app-install-data app-install-data-commercial at-spi
  brltty brltty-x11 busybox-initramfs ca-certificates
  cupsys-driver-gutenprint dcraw deskbar-applet ekiga example-content
  festival festlex-cmu festlex-poslex festvox-kallpc16k foo2zjs
  foomatic-db-gutenprint gcj-4.0-base gcj-4.1-base gconf2-common gdebi
  gij-4.1 gimp-print gnome-accessibility-themes gnome-mag
  gnome-power-manager gnome-screensaver gnopernicus gok gstreamer0.10-alsa
  gstreamer0.10-esd gstreamer0.10-gnomevfs gstreamer0.10-plugins-base
  gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good
  gstreamer0.10-tools gstreamer0.10-x gtk2-engines-highcontrast
  gtk2-engines-ubuntulooks gutenprint-locales hplip ijsgutenprint im-switch
  inputattach irssi iso-codes kdelibs4c2a landscape-client
  language-selector-common laptop-mode-tools libalut0 libapt-pkg-perl
  libarts1c2a libatspi1.0-0 libavahi-client3 libavahi-common-data
  libavahi-common3 libavahi-glib1 libavahi-qt3-1 libavifile-0.7c2
  libbakery-2.4-1 libbakery-2.4-common libbeagle0 libbrlapi1 libbtctl2
  libcal3d11c2a libcamel1.2-8 libcdio6 libcrypto++5.2c2a libcupsys2
  libcurl3-gnutls libdbus-1-2 libdbus-glib-1-2 libdevmapper1.02 libdmx1
  libdns21 libdrm2 libedataserver1.2-7 libegroupwise1.2-9 libenchant1c2a
  libestools1.2 libexchange-storage1.2-1 libgail-gnome-module libgcj7
  libgcj7-jar libgdl-1-0 libgdl-1-common libgksu1.2-1 libgksuui1.0-1
  libglademm-2.4-1c2a libglibmm-2.4-1c2a libgmp3c2 libgnome-mag2
  libgnome-speech3 libgnome-vfsmm-2.6-1c2a libgnomebt0
  libgnomecupsui1.0-1c2a libgnomevfs2-bin libgnomevfs2-extra libgnutls12
  libgpod-common libgpod0 libgsf-1-113 libgsf-1-common
  libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libgtkmm-2.4-1c2a
  libgtop2-7 libgutenprint2 libgutenprintui2-1 libicu34 libid3-3.8.3c2a
  libisc11 libiso9660-4 libjack0.100.0-0 libjline-java libkpathsea4
  liblwres9 libmagick9 libmjpegtools0c2a libmusicbrainz4c2a
  libmysqlclient15off libnautilus-burn3 libneon25 libnetcdf3 libnotify1
  libopal-2.2.0 libopenal0a libopenexr2c2a libopenobex-1.0-0
  libparted1.6-13 libpoppler1 libpoppler1-glib libpt-1.10.0
  libpt-plugins-avc libpt-plugins-dc libpt-plugins-oss libqscintilla6
  libquicktime0 libscim8c2a libsexy2 libsigc++-2.0-0c2a libsmpeg0 libsnmp9
  libssl0.9.8 libsysfs2 libtag1c2a libtidy-0.99-0 libtotem-plparser1
  libuniconf4.2 libwavpack0 libwpd8c2a libwvstreams4.2-base
  libwvstreams4.2-extras libxfont1 libxine-extracodecs libxine-main1
  libxml++2.6c2a libxmlsec1 libxmlsec1-nss libxmlsec1-openssl libxplc0.3.13
  libxvmc1 linux-image-2.6.15-23-386 linux-restricted-modules-2.6.15-23-386
  mcpp mdetect min12xxw mplayer mplayer-skins mysql-client-5.0
  mysql-server-5.0 openoffice.org openoffice.org-base openoffice.org-calc
  openoffice.org-common openoffice.org-core openoffice.org-draw
  openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk
  openoffice.org-help-en-us openoffice.org-impress
  openoffice.org-java-common openoffice.org-l10n-common
  openoffice.org-l10n-en-gb openoffice.org-l10n-en-us
  openoffice.org-l10n-en-za openoffice.org-math
  openoffice.org-thesaurus-en-us openoffice.org-writer pcmciautils
  poppler-utils python-beagle python-gnome2-desktop python-gst0.10
  python-libxml2 python2.4-gnome2-desktop python2.4-gobject
  python2.4-soappy radeontool readline-common scim scim-gtk2-immodule
  scim-modules-socket screensaver-default-images smartdimmer
  tangerine-icon-theme tango-icon-theme tango-icon-theme-common
  thunderbird-locale-en-gb ttf-arphic-ukai ttf-arphic-uming ttf-dejavu
  ttf-gentium ttf-lao ttf-thai-tlwg unattended-upgrades vim-runtime
  wpasupplicant x11-common xcursor-themes xserver-xorg-input-synaptics
The following packages will be REMOVED:
  busybox-cvs-initramfs cupsys-driver-gimpprint-data gnomemeeting
  gstreamer0.8-jack hotplug hplip-base ifrename kdelibs4c2 libarts1c2
  libbakery-2.3-15 libbakery-2.3-common libcal3d10c2 libcamel1.2-6
  libdbus-1-1 libdbus-glib-1-1 libenchant1c2 libgksu1.2-0 libgksuui1.0-0
  libglademm-2.4-1c2 libglibmm-2.4-1c2 libgnome-vfsmm-2.6-1c2
  libgnomecupsui1.0-1 libgtkmm-2.4-1c2 libid3-3.8.3c2 libjack0.80.0-0
  libmusicbrainz4c2 libnautilus-burn2 libnotify0 libopenal0 libopenexr2c2
  libopenh323-1.15.3c2 libpt-1.8.3c2 libqscintilla5c2 libsigc++-2.0-0c2
  libsmpeg0c2 libtag1c2 libtidy0 libtunepimp2c2 libwpd8c2 libxml++2.6c2
  netcdfg3 openoffice.org-debian-files openoffice.org2-common
  openoffice.org2-core openoffice.org2-help-en-us
  openoffice.org2-java-common openoffice.org2-l10n-en-us smeg x-common
  xmkmf xorg-common xorg-driver-synaptics xserver-common
The following packages will be upgraded:
  acpi-support acpid adduser albumshaper alsa-base alsa-utils amule anjuta
  anjuta-common apache-doc apache2 apache2-common apache2-mpm-prefork
  apache2-utils appres apt apt-utils aptitude aspell at base-files
  base-passwd bash bc beforelight bicyclerepair bind9-host binutils
  binutils-static bitmap bittornado bittornado-gui bittorrent blender
  bluefish bluez-cups bluez-pcmcia-support bluez-pin bluez-utils bogofilter
  bogofilter-bdb bogofilter-common bsdmainutils bsdutils bsh bug-buddy bum
  bzip2 capplets-data cdda2wav cdrdao cdrecord console-common console-data
  console-tools contact-lookup-applet coreutils cpio cpp cpp-4.0 cracklib2
  cron cupsys cupsys-bsd cupsys-client cupsys-driver-gimpprint dash dbus
  dbus-1-utils dc debconf debconf-i18n debconf-utils debhelper
  desktop-file-utils dhcp3-client dhcp3-common dictionaries-common diff
  digikam discover1 discover1-data dmidecode dmsetup dnsutils doc-debian
  docker dosfstools dpkg dpkg-dev dselect dvd+rw-tools e2fslibs e2fsprogs
  editres eject eog eric esound esound-common ethtool evince evms
  evms-ncurses evolution evolution-data-server evolution-exchange
  evolution-plugins evolution-webcal fakeroot fastjar fdutils fetchmail
  ffmpeg file file-roller findutils finger firefox firefox-gnome-support
  fontconfig foomatic-db foomatic-db-engine foomatic-db-gimp-print
  foomatic-db-hpijs foomatic-filters foomatic-filters-ppds fortune-mod
  fortunes-min fping freeciv-client-gtk freeciv-data freeciv-server
  freeglut3 fstobdf ftp gaim gaim-data gamin gawk gcalctool gcc-3.3-base
  gcc-3.4-base gcc-4.0-base gconf-editor gconf2 gdb gdm gedit gedit-common
  gettext gettext-base gij gij-4.0 gimp gimp-data gimp-python gksu
  gnome-about gnome-app-install gnome-applets gnome-applets-data
  gnome-btdownload gnome-control-center gnome-cups-manager
  gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data
  gnome-icon-theme gnome-keyring gnome-media gnome-menus
  gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data
  gnome-pilot gnome-pilot-conduits gnome-session gnome-spell
  gnome-system-monitor gnome-system-tools gnome-terminal
  gnome-terminal-data gnome-themes gnome-utils gnome-volume-manager
  gnome2-user-guide gnomebaker gnupg gparted grep grepmap groff-base grub
  gs-common gs-esp gstreamer0.8-a52dec gstreamer0.8-aa gstreamer0.8-alsa
  gstreamer0.8-artsd gstreamer0.8-audiofile gstreamer0.8-caca
  gstreamer0.8-cdio gstreamer0.8-cdparanoia gstreamer0.8-dv
  gstreamer0.8-dvd gstreamer0.8-esd gstreamer0.8-faac gstreamer0.8-faad
  gstreamer0.8-festival gstreamer0.8-ffmpeg gstreamer0.8-flac
  gstreamer0.8-gnomevfs gstreamer0.8-gsm gstreamer0.8-gtk
  gstreamer0.8-hermes gstreamer0.8-jpeg gstreamer0.8-lame gstreamer0.8-mad
  gstreamer0.8-mikmod gstreamer0.8-misc gstreamer0.8-mms
  gstreamer0.8-mpeg2dec gstreamer0.8-musepack gstreamer0.8-oss
  gstreamer0.8-plugin-apps gstreamer0.8-plugins gstreamer0.8-sdl
  gstreamer0.8-sid gstreamer0.8-speex gstreamer0.8-swfdec
  gstreamer0.8-theora gstreamer0.8-tools gstreamer0.8-vorbis gstreamer0.8-x
  gthumb gtk2-engines-clearlooks gtk2-engines-crux gtk2-engines-industrial
  gtk2-engines-lighthouseblue gtk2-engines-mist gtk2-engines-pixbuf
  gtk2-engines-redmond95 gtk2-engines-smooth gtk2-engines-thinice
  gtkhtml3.8 gucharmap guile-1.6-libs gzip hal hal-device-manager hdparm
  hermes1 hicolor-icon-theme hostname hotkey-setup hpijs hplip-data
  hplip-ppds html2text hwdata hwdb-client iceauth ico ifupdown ijsgimpprint
  imagemagick imake imlib-base imlib11 info initramfs-tools initscripts
  installation-report intltool-debian iproute iptables iputils-arping
  iputils-ping iputils-tracepath irssi-text jackd java-common
  java-gcj-compat java-package kdelibs-bin kdelibs-data kfilereplace
  klibc-utils klinkstatus klogd kommander language-pack-en
  language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base
  language-selector language-support-en laptop-detect launchpad-integration
  less lftp libaa1 libacl1 libadns1 libao2 libapache2-mod-auth-mysql
  libapache2-mod-php4 libapr0 libarchive-tar-perl libarchive-zip-perl
  libartsc0 libasound2 libaspell15 libatk1.0-0 libattr1 libaudio2
  libaudiofile0 libavc1394-0 libbind9-0 libblkid1 libbluetooth1
  libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common
  libbz2-1.0 libcairo2 libcomerr2 libcompress-zlib-perl libconsole
  libcroco3 libcupsimage2 libcupsys2-gnutls10 libcurl3 libdb1-compat libdb3
  libdb4.2 libdbd-mysql-perl libdbi-perl libdc1394-13 libdirectfb-0.9-22
  libdiscover1 libdjvulibre15 libdv4 libdvdread3 libebook1.2-5 libecal1.2-3
  libedata-book1.2-2 libedata-cal1.2-1 libedataserverui1.2-6 libedit2
  libeel2-2 libeel2-data libelfg0 libesd-alsa0 libevent-perl libevms-2.5
  libfaac0 libfaad2-0 libflac7 libfontconfig1 libfontenc1 libfreetype6
  libfribidi0 libfs6 libg2c0 libgail-common libgail17 libgamin0 libgc1c2
  libgcc1 libgcj-common libgcj6 libgconf2-4 libgconfmm-2.6-1c2 libgcrypt11
  libgd2-noxpm libgda2-3 libgda2-common libgdk-pixbuf2 libgeoip1 libggi2
  libgii0 libgii0-target-x libgimp2.0 libgl1-mesa libgl1-mesa-dri libglade0
  libglade2-0 libglew1 libglib-perl libglib1.2 libglib2.0-0 libglib2.0-data
  libglu1-mesa libgnome-desktop-2 libgnome-keyring0 libgnome-menu2
  libgnome-pilot2 libgnome2-0 libgnome2-canvas-perl libgnome2-common
  libgnome2-vfs-perl libgnomecanvas2-0 libgnomecanvas2-common
  libgnomecups1.0-1 libgnomeprint2.2-0 libgnomeprint2.2-data
  libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeui-0
  libgnomeui-common libgnomevfs2-0 libgnomevfs2-common libgnucrypto-java
  libgnujaxp-java libgnujaxp-jni libgnutls11 libgpg-error0 libgphoto2-2
  libgphoto2-port0 libgpmg1 libgsl0 libgstreamer-gconf0.8-0
  libgstreamer-plugins0.8-0 libgstreamer0.8-0 libgtk-perl
  libgtk-pixbuf-perl libgtk1.2 libgtk1.2-common libgtk2-gladexml-perl
  libgtk2-perl libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtkhtml2-0
  libgtkhtml3.8-15 libgtksourceview-common libgtksourceview1.0-0
  libgtkspell0 libgucharmap4 libguile-ltdl-1 libhal-storage1 libhal1
  libhsqldb-java libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl
  libice6 libid3tag0 libidl0 libidn11 libijs-0.35 libimlib2 libintl-perl
  libisccc0 libisccfg1 libiw28 libjessie-java libjpeg62 libkexif1 libkipi0
  libklibc libkpathsea3 libkrb53 liblaunchpad-integration0 libldap2
  liblircclient0 liblockfile1 liblpint-bonobo0 libltdl3 liblzo1 libmagic1
  libmdbtools libmetacity0 libmms0 libmodplug0c2 libmp4v2-0 libmpcdec3
  libmpeg2-4 libmyspell3c2 libmysqlclient14 libnautilus-extension1
  libncurses5 libncursesw5 libneon24 libnetpbm10 libnetpbm9 libnspr4
  libnss3 libogg0 liboggflac3 liboil0.3 libopencdk8 liborbit2
  libpanel-applet2-0 libpango1.0-0 libpango1.0-common libpcap0.8 libpcre3
  libpisock8 libpisync0 libpng12-0 libportaudio0 libpq4 libpt-plugins-alsa
  libpt-plugins-v4l libpt-plugins-v4l2 libpvm3 libqt3-mt libqthreads-12
  libraptor1 librasqal0 libraw1394-5 librdf0 libreadline4 libreadline5
  librecode0 libreiserfs0.3-0 librsvg2-2 librsvg2-common libsane libsasl2
  libsasl2-modules libscrollkeeper0 libsdl-net1.2 libsdl-ttf2.0-0
  libsdl1.2debian libsdl1.2debian-oss libservlet2.3-java libshout3
  libsidplay1 libslang2 libslp1 libsm6 libsmbclient libsmjs1 libsndfile1
  libsnmp-base libsoup2.2-8 libspeex1 libsqlite0 libsqlite3-0 libss2
  libssl0.9.7 libstartup-notification0 libstdc++5 libstdc++6 libswfdec0.3
  libtasn1-2 libtext-charwidth-perl libtext-iconv-perl
  libtext-wrapi18n-perl libtheora0 libtiff4 libungif4g
  libunicode-string-perl libusb-0.1-4 libuuid1 libvcdinfo0 libvorbis0a
  libvorbisenc2 libvorbisfile3 libvte-common libvte4 libwmf0.2-7
  libwnck-common libwnck18 libwrap0 libwxgtk2.4-1 libwxgtk2.6-0 libx11-6
  libxalan2-java libxau6 libxaw7 libxcursor1 libxdamage1 libxdmcp6
  libxerces2-java libxext6 libxfixes3 libxft2 libxi6 libxine1c2
  libxinerama1 libxkbfile1 libxklavier10 libxml1 libxml2 libxml2-utils
  libxmu6 libxmuu1 libxosd2 libxp6 libxpm4 libxrandr2 libxrender1 libxres1
  libxslt1.1 libxss1 libxt-java libxt6 libxtrap6 libxtst6 libxv1
  libxvidcore4 libxxf86dga1 libxxf86misc1 libxxf86vm1 linux-386
  linux-image-386 linux-restricted-modules-386
  linux-restricted-modules-common linux-sound-base listres localepurge
  logrotate lsb-base lsb-release lshw lshw-common lsof lvm-common lvm2
  mailx make makedepend makedev manpages mawk mdadm memtest86+ menu
  menu-xdg metacity mime-support mjpegtools mkisofs module-init-tools mount
  mozilla-firefox-locale-en-gb mplayer-586 msttcorefonts myspell-en-gb
  myspell-en-us mysql-client mysql-common mysql-server nano nautilus
  nautilus-cd-burner nautilus-data nautilus-sendto ncurses-base ncurses-bin
  net-tools netbase netcat netpbm nfs-common nfs-kernel-server
  notification-daemon ntpdate numlockx nvidia-kernel-common oclock
  odbcinst1debian1 openoffice.org2 openoffice.org2-base
  openoffice.org2-calc openoffice.org2-draw openoffice.org2-evolution
  openoffice.org2-gnome openoffice.org2-impress openoffice.org2-math
  openoffice.org2-writer openssh-client openssl parted passwd pciutils
  pcmcia-cs pdmenu php4 php4-common php4-mysql phpmyadmin pkg-config
  planetpenguin-racer-data planner pmount po-debconf popularity-contest
  portmap postfix powermanagement-interface powermgmt-base powernowd ppp
  pppconfig prefixsuffix procps psmisc python python-adns python-apt
  python-cddb python-clientcookie python-crypto python-egenix-mxproxy
  python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools
  python-epydoc python-eunuchs python-examples python-gadfly python-gd
  python-gdbm python-geoip python-glade2 python-gmenu python-gnome2
  python-gnome2-extras python-gst python-gtk2 python-htmlgen
  python-htmltmpl python-id3lib python-imaging python-imaging-sane
  python-imaging-tk python-jabber python-kjbuckets
  python-launchpad-integration python-ldap python-minimal python-mysqldb
  python-netcdf python-numeric python-openal python-opengl python-osd
  python-pam python-parted python-pexpect python-pgsql python-pisock
  python-pygame python-pylibacl python-pyopenssl python-pyorbit
  python-pyxattr python-qt3 python-qtext python-reportlab python-simpletal
  python-soappy python-soya python-sqlite python-syck python-tk python-unit
  python-uno python-vte python-wxgtk2.6 python-wxversion python-xdg
  python-xml python2.4 python2.4-adns python2.4-apt python2.4-cairo
  python2.4-clientcookie python2.4-crypto python2.4-dbus
  python2.4-egenix-mxdatetime python2.4-egenix-mxproxy
  python2.4-egenix-mxstack python2.4-egenix-mxtexttools
  python2.4-egenix-mxtools python2.4-epydoc python2.4-eunuchs
  python2.4-examples python2.4-gadfly python2.4-gd python2.4-gdbm
  python2.4-geoip python2.4-glade2 python2.4-gnome2 python2.4-gnome2-extras
  python2.4-gtk2 python2.4-htmlgen python2.4-htmltmpl python2.4-id3lib
  python2.4-imaging python2.4-imaging-sane python2.4-imaging-tk
  python2.4-jabber python2.4-kjbuckets python2.4-ldap python2.4-librdf
  python2.4-libxml2 python2.4-libxslt1 python2.4-minimal python2.4-mysqldb
  python2.4-numeric python2.4-numeric-ext python2.4-opengl python2.4-osd
  python2.4-pam python2.4-pexpect python2.4-pgsql python2.4-pycurl
  python2.4-pygame python2.4-pylibacl python2.4-pyopenssl python2.4-pyorbit
  python2.4-pyxattr python2.4-qt3 python2.4-qtext python2.4-reportlab
  python2.4-simpletal python2.4-sip4-qt3 python2.4-sqlite python2.4-syck
  python2.4-tk python2.4-unit python2.4-xml qtparted quanta-data rdesktop
  readahead regionset reiser4progs reportbug revelation rhythmbox rss-glx
  rsync samba samba-common sane-utils scorched3d-data screem screen
  scrollkeeper sed serpentine sessreg shared-mime-info slocate smbclient
  smbfs smproxy sound-juicer sox ssh-askpass-gnome ssl-cert sudo synaptic
  sysklogd system-tools-backends sysv-rc sysvinit tar tcl8.4 tcpd tcpdump
  telnet tidy tk8.4 toshset totem totem-xine transcode tsclient
  ttf-arabeyes ttf-arphic-bkai00mp ttf-bengali-fonts ttf-devanagari-fonts
  ttf-freefont ttf-gujarati-fonts ttf-indic-fonts ttf-kannada-fonts
  ttf-malayalam-fonts ttf-mgopen ttf-opensymbol ttf-oriya-fonts
  ttf-punjabi-fonts ttf-tamil-fonts ttf-telugu-fonts ubuntu-artwork
  ubuntu-desktop ubuntu-docs ubuntu-standard ucf udev unzip update-manager
  update-notifier usbutils usplash util-linux vbetool vcdimager viewres vim
  vim-common vino vnc-common vorbis-tools w3m wamerican wbritish wget whois
  wireless-tools wvdial x-ttcidfont-conf x-window-system-core x11perf xauth
  xbase-clients xbiff xcalc xcdroast xchat xchat-common xclipboard xclock
  xconsole xcursorgen xditview xdpyinfo xdriinfo xev xeyes xf86dga xfd
  xfonts-100dpi xfonts-75dpi xfonts-base xfonts-scalable xfonts-utils
  xfontsel xfsprogs xgamma xgc xhost xinit xkbutils xkeyboard-config xkill
  xload xlogo xlsatoms xlsclients xlsfonts xmag xman xmessage xmms xmodmap
  xmore xpmutils xprop xrandr xrdb xrefresh xresprobe xrgb xsane
  xsane-common xscreensaver xscreensaver-data xscreensaver-gl xserver-xorg
  xserver-xorg-core xserver-xorg-driver-apm xserver-xorg-driver-ark
  xserver-xorg-driver-ati xserver-xorg-driver-chips
  xserver-xorg-driver-cirrus xserver-xorg-driver-cyrix
  xserver-xorg-driver-dummy xserver-xorg-driver-fbdev
  xserver-xorg-driver-glint xserver-xorg-driver-i128
  xserver-xorg-driver-i740 xserver-xorg-driver-i810
  xserver-xorg-driver-imstt xserver-xorg-driver-mga
  xserver-xorg-driver-neomagic xserver-xorg-driver-newport
  xserver-xorg-driver-nsc xserver-xorg-driver-nv
  xserver-xorg-driver-rendition xserver-xorg-driver-s3
  xserver-xorg-driver-s3virge xserver-xorg-driver-savage
  xserver-xorg-driver-siliconmotion xserver-xorg-driver-sis
  xserver-xorg-driver-tdfx xserver-xorg-driver-tga
  xserver-xorg-driver-trident xserver-xorg-driver-tseng
  xserver-xorg-driver-v4l xserver-xorg-driver-vesa xserver-xorg-driver-vga
  xserver-xorg-driver-via xserver-xorg-driver-vmware
  xserver-xorg-input-acecad xserver-xorg-input-aiptek
  xserver-xorg-input-calcomp xserver-xorg-input-citron
  xserver-xorg-input-digitaledge xserver-xorg-input-dmc
  xserver-xorg-input-dynapro xserver-xorg-input-elographics
  xserver-xorg-input-fpit xserver-xorg-input-hyperpen
  xserver-xorg-input-kbd xserver-xorg-input-magellan
  xserver-xorg-input-microtouch xserver-xorg-input-mouse
  xserver-xorg-input-mutouch xserver-xorg-input-palmax
  xserver-xorg-input-penmount xserver-xorg-input-spaceorb
  xserver-xorg-input-summa xserver-xorg-input-tek4957
  xserver-xorg-input-void xserver-xorg-input-wacom xset xsetmode
  xsetpointer xsetroot xsltproc xsm xstdcmap xterm xtrap xutils xvidtune
  xvinfo xvncviewer xwd xwininfo xwud yelp zenity zlib1g
1056 packages upgraded, 226 newly installed, 53 to remove and 0 not upgraded.
Need to get 745MB of archives. After unpacking 570MB will be used.
Do you want to continue? [Y/n/?] n
Abort.

```

That is all I get with "sudo aptitude dist-upgrade"

No "F10" option

---

### Post by morequarky on 2006-06-05
Why do you say that?

I already said in the first few post that I backup up my Breezy install.  4+gig tar file.

Also, do you think I should press "y" and remove "ubuntu-minimal"?

I have done everything I have been told and followed the "upgrade by hand" directions perfectly.  Why does it want to remove ubuntu-minimal?  How do I make it keep it?  What is ubuntu-minimal anyways?  Is it breezy which is currently running?  I need information and answers so I know what to do.

---

### Post by llamakc on 2006-06-05
My error. if you run:

sudo aptitude 

You'll then be able to get the menu. BTW, do you see ubuntu-minimal in that list of stuff to remove? I didn't.

---

### Post by morequarky on 2006-06-05
Check out the screenshot.

f10 didn't work, but my mouse worked, just had to click on it.

---

### Post by morequarky on 2006-06-05
llamakc THANKS SOOOOOOOO MUCH FOR YOUR EFFORTS

If anyone else ends up like this, this thread will be useful.

---

### Post by morequarky on 2006-06-05
Do you think I should run "sudo aptitude dist-upgrade" and press yes, and see if it works?  I think I have already installed much of that stuff with "apt-get dist-upgrade"?

---

### Post by morequarky on 2006-06-05
When the HOWTO says:
1. backup date
2. change repos to dapper
3. update
4. upgrade

maybe the problem is apt-get
maybe upgrading should use aptitude instead.  Maybe aptitude is smarter.

I really don't know.

---

### Post by llamakc on 2006-06-05
Well most of those packages aren't fully configured yet because you've ran into the snag, so they are not fully installed yet. Aptitude, Synaptic, DSelect, and apt-get from the commandline are interoperable. I suggest you run aptitude dist-upgrade only and ONLY after you have certainly backed up your LAMP files for your webserver and have done a dump of your databases.

---

### Post by morequarky on 2006-06-05
I have a 4gig back up of Breezy.

How do I do a mysql dump?  I need this BEFORE running aptitude dist-upgrade.

Thanks for your help.

---

### Post by llamakc on 2006-06-05
Somebody smarter will come along and possibly give you a better answer but I do:

# mysqldump command
mysqldump --all-databases --add-drop-table -u root -psome_password > db.dump

# then readd db

mysql -u root -psomepassword < db.dump

---

### Post by pellgarlic on 2006-06-06
[QUOTE=pellgarlic]the other thing you could try, is to take note of the "missing dependencies" (i.e. pcmciautils and wpasupplicant) and install them first, then retry the dist-upgrade.[/QUOTE]

have you tried this yet? might be worth a shot...

[edit]: sorry, my email notification only informed me of the last two posts directly after my own last post - didn't realize so much progress had been made in the interim, and i posted this without realizing pages 2 and 3 existed! glad you're getting somewhere, and have someone more knowledgeable than myself to help you :)

---

### Post by morequarky on 2006-06-06
Actually, Pellgarlic, I wanted to try that.

IIamakc has been a great help.  I am thinking of using aptitude soon, but I would like to try to install the missing dependencies first.  How would I go about forcing apt-get or aptitude to install only the packages I want.  namely psmciautils and wpasupplicat and their dependence.

Thanks.

---

### Post by ubuntu_demon on 2006-06-06
> 
I read that thread a few times. My case isn't listed. I can't remove "ubuntu-minimal as the thread says and I can't remove any of my dependancies because my system doesn't have them either.


It isn't possible to list all possible cases.

From [http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672) :
> 
I'm posting this as a forum user and not as a staff member. First read and understand the entire post before doing anything. This is all on your own risk. Please be very careful


I've written the howto with apt-get in mind because I'm experienced with it. If you want to use aptitude the general idea probably remains the same.

First make sure you are using a clean sources.list :
[http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2)
in this specific case : After changing the sources.list don't dist-upgrade but only do :
$sudo apt-get update 

If apt-get wants to remove crucial packages like ubuntu-minimal you should definitely make sure this is what you want to do before pressing 'Y'. In this case removing the meta-package ubuntu-minimal doesn't remove any other packages so it's definetely safe but the next command should be to install it again. So :

$sudo apt-get remove -f
remove ONLY ubuntu-minimal ? YES
$sudo apt-get install ubuntu-minimal -f
$sudo apt-get dist-upgrade

and continue with the guide. Let's start at the top of the guide (right after changing the sources.list).

---

### Post by morequarky on 2006-06-06
Ahhhh I get it.  remove then re-install it quick like without dist-upgrade knowing it.  

Great.  I'll try that.

Thanks SOOOOOOOOOOO much, (even if it doesn't work)

---

### Post by pellgarlic on 2006-06-06
cool - ubuntu-demon's on the case! you should follow those instructions. if ubuntu_demon hadn't posted, i would have said to do 

$sudo apt-get install pcmciautils 
$sudo apt-get install wpasupplicant

but i'm taking pot-shots in the dark here - ubuntu_demon is speaking from experience. good luck ;)

---

### Post by morequarky on 2006-06-06
I read your thread a couple of times.

Couldn't quit grasp what to do.  Also, your thread says be careful with stuff like ubuntu-minimal.  So that made me use even more caution.

---

### Post by ubuntu_demon on 2006-06-06
I've updated my guide to make it a bit more clear. Please ask any questions you have.

ubuntu-minimal is a meta-package. This package has no contents of it's own. But it makes sure important packages are kept installed. So it's safe to remove it **if no packages belonging to ubuntu-minimal get removed and if you make sure it gets installed again** as soon as possible to make sure apt-get doesn't want to remove packages belonging to ubuntu-minimal especially **apt**.

---

### Post by ubuntu_demon on 2006-06-06
[QUOTE=pellgarlic]cool - ubuntu-demon's on the case! you should follow those instructions. if ubuntu_demon hadn't posted, i would have said to do 

$sudo apt-get install pcmciautils 
$sudo apt-get install wpasupplicant

but i'm taking pot-shots in the dark here - ubuntu_demon is speaking from experience. good luck ;)[/QUOTE]

thnx for the compliment :-D 

I'm not the "upgrade god" :p but I have some experience with these types of problems.

Let's all stick together and help eachother out with our upgrading and installing problems!

I probably won't be back here until tomorrow.

---

### Post by morequarky on 2006-06-06
OOOOOO
KKKKKKKK

Dapper up and running.

I did have a message about "HAL" but that was because I relogged using the Breezy X session.

I have now rebooted.  LAMP seems to be working great.  Upgrading by hand was a piece of cake really.  I just needed to know that I could remove and then reinstall ubuntu-minimal.

THANKS SOOOOOOOOOOOO MUCH

---

### Post by morequarky on 2006-06-06
Ok, as I said, Dapper is up and running. =D> 8-) 

Thanks for all the help.

Now I have noticed two software issues that are probably easy to fix.

1. OpenOffice is not listed in my menus and add/remove programs won't let me add it due to some problem.  Synoptic doesn't say there is a problem.  CLUELESS

2. mplayer is not working.  I am guessing I have to uninstall automatix and reinstall it.  UNSURE

3. I have the debian menu installed from automatix.  I would like that uninstalled.  I never use it.

Dapper is fast.8)

---

### Post by pellgarlic on 2006-06-06
1. can you quote any error messages or warnings you get when trying to do so? does OOo run ok otherwise? try uninstalling and reinstalling?

2. try just reinstalling mplayer using apt-get or synaptic?

3. this page: [http://ubuntuforums.org/showthread.php?t=90797](http://ubuntuforums.org/showthread.php?t=90797) is a thread for "Removal of softwares installed by automatix"

[edit: ok, maybe not a good idea to use apt-get or synaptic if you're using automatix, found this in the faq on automatix's website: 

"Q7) Can I run synaptic, apt-get and other software installations alongside Automatix while it's running?
A: NO. Please do not attempt to install any other software or run updates while running Automatix. If you try to do so, Automatix will throw an error and exit."]

---

### Post by pellgarlic on 2006-06-06
by the way, have you tried this: [http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/)

seems to me a much better proposition than automatix, as it strives to achieve the same thing, but seems to be more user-freindly and more successful. when reading about automatix, it didn't sound like a well implemented idea, but easyubuntu does. although i am not speaking from experience here... but easyubuntu sounds good enough that i am going to try it myself, whereas automatix didn't appeal to me at all.

---

### Post by ubuntu_demon on 2006-06-07
openoffice is installed by default so you are probably missing ubuntu-desktop.

So you haven't read my post here very good :
Like I said here : [http://www.ubuntuforums.org/showpost.php?p=1101297&postcount=30](http://www.ubuntuforums.org/showpost.php?p=1101297&postcount=30)

You should follow the guide from top :
[http://www.ubuntuforums.org/showthread.php?t=187656](http://www.ubuntuforums.org/showthread.php?t=187656)

I also say this in my guide :
> 
**Make sure you have done all steps even if you think some step in the middle has solved your problems.**


So only **after**r you have followed it and made sure there are **no problems left** then you go adding other software and/or repositories. (you have to do a bit of work before multimedia works)

If you don't understand something please ask.

good luck! :)

This is my recommended sources.list **after** everything is solved :
[http://www.ubuntuforums.org/showthread.php?t=185758](http://www.ubuntuforums.org/showthread.php?t=185758)
This is my favorite way to install multimedia **after** everything is solved :
[http://www.ubuntuforums.org/showthread.php?t=186792](http://www.ubuntuforums.org/showthread.php?t=186792)

---

### Post by morequarky on 2006-06-07
>>>sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  python-soya tidy
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

I finished everything.

I uninstalled mplayer and it's stuff(got it from automatix for breezy)  re-installed it(without the help of automatix), works great now.

Openoffice2 has like two thinks installed from what synoptic says.  But it wasn't in the menues.  I went though synoptic and found the openoffice2 packages I wanted.  It uninstalled something if I remember and installed some new transitional packages.  Anyways, it works now and is located in my office menu tap in the Applications menu.

I also burned a CDRW without any trouble.

I think everything is set.  Done and Done.

I don't think I have any more customizing or errors.

---

### Post by ubuntu_demon on 2006-06-07
Don't use automatix (which edits your sources.list) before having maked sure everything was correctly installed and dist-upgraded.

Try which one of these gives you the best result :
$sudo apt-get install python-soya 
$sudo apt-get remove python-soya 

Try which one of these gives you the best result :
$sudo apt-get install tidy
$sudo apt-get remove tidy

Try dist-upgrading again :
$sudo apt-get dist-upgrade

install ubuntu-desktop :
$sudo apt-get install ubuntu-desktop

do a reboot :
$sudo reboot

Now everything is probably fixed and now is the time to install codecs and everything else you want.

good luck ! :)

---

