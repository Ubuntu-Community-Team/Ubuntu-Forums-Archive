---
title: "Can't login - a new variation on the same old theme?"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by sirmrmatt on 2007-04-28
Dead upgrade?

I ran the synaptic dist-upgrade on both of my edgy computers to upgrade to fiesty. One went fine, the other one, I keep getting these "your session lasted only ten seconds" errors, and "couldn't find sessreg" errors (when you view the error file).

I was able to rsh in using the command line on my other computer and ran

sudo apt-get install -f

and 

sudo dpkg --configure -a

I finally did a 

sudo su

after a bunch of "Permission denied" error messages (I though "Permission denied" was impossible when using sudo?)

Anyhow, here is the (lengthy) output of the command line as it finally gives up:

```
root@pinguin1:/home/austin# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  kpdf ksystemlog kscreensaver-xsavers krdc krfb kscd kppp konversation
  krita-data kubuntu-default-settings libkscan1 python2.4-dev kregexpeditor
  kdeprint adept-manager knode kmplayer-konq-plugins ksvg kscreensaver
  libnfsidmap1 kaffeine-xine libavahi-compat-libdnssd1 kio-locate libk3b2
  libpythonize0 python-software-properties ksnapshot liblockdev1 kdebluetooth
  kooka libkipi0 wlassistant desktop-effects openoffice.org-kde
  libmagick++9c2a adept-installer libkexif1 kdegraphics-kfile-plugins libburn2
  konqueror-nsplugins gwenview gtk2-engines-pixbuf libsmokeqt1 libpoppler1-qt
  libtdb1 adept-updater libqt4-qt3support guile-g-wrap hwdb-client-kde krita
  qca-tls libapr0 klipper libevent1 ubuntu-desktop kubuntu-artwork-usplash
  libqt4-core kontact libsqlite0 kdeadmin-kfile-plugins libktoblzcheck1-dev
  ksmserver libgnet2.0-0 ksysguard adept-batch koffice-data kde-icons-mono
  kubuntu-desktop libqt-perl kmenuedit pykdeextensions libgssapi2 adept
  ksplash-engine-moodin kubuntu-konqueror-shortcuts ksplash kaffeine
  kipi-plugins korganizer k3b kdenetwork-kfile-plugins kbstate
  libgwenhywfar38-dev akregator kio-apt kwin-style-crystal arts python-qt4
  libexif-dev libgphoto2-2-dev libusb-dev kcron librpcsecgss2
  libjasper-runtime adept-common libgmp3c2 libqt4-gui digikam kdm speedcrunch
  avahi-autoipd kpf bogofilter-bdb kdnssd kdemultimedia-kfile-plugins katapult
  poster kde-style-polyester kdenetwork-filesharing kubuntu-docs knotes
  bogofilter kde-guidance libqt4-sql flac debtags libgsl0 apt-index-watcher
  libdbus-glib-1-dev libkpimexchange1 gtk2-engines-gtk-qt kmailcvt
  rdiff-backup knetworkconf software-properties-kde ksysguardd konq-plugins
  digikamimageplugins kpersonalizer language-selector-qt qobex xorg ktorrent
  scim-qtimm kwalletmanager kopete compiz libisofs2 karm kate keep
  koffice-libs adept-notifier bogofilter-common kde-guidance-powermanager
  kde-systemsettings nfs-common librsync1 kmousetool kitchensync kmag
  kdepim-kresources kdepim-wizards kmilo kmplayer-base libaqbanking++0
  kaudiocreator python-kde3 qt4-qtconfig kdepasswd kmix
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  avahi-autoipd cdrecord compiz compiz-core compiz-gnome compiz-gtk
  compiz-plugins desktop-effects genisoimage gs-esp gs-esp-x
  gtk2-engines-pixbuf kde-style-polyester kdelibs-data kwin libcupsimage2
  libdecoration0 libgnomeui-0 libgnomeui-common libgnomeui-dev libgnomevfs2-0
  libgnomevfs2-common libgnomevfs2-dev libgnomevfs2-extra libgs-esp8
  libxcomposite-dev libxcomposite1 libxcomposite1-dbg mkisofs
  openprinting-ppds python-software-properties software-properties-kde wodim
  xcdroast xkb-data xserver-xorg-core
Suggested packages:
  cdrkit-doc gs-cjk-resource gtk-engines-pixmap kpager libgnomeui-doc
  foomatic-filters-ppds hpijs-ppds openprinting-ppds-extra
Recommended packages:
  restricted-manager
The following packages will be REMOVED:
  kubuntu-desktop ubuntu-desktop xorg
The following NEW packages will be installed:
  avahi-autoipd compiz compiz-core compiz-gnome compiz-gtk compiz-plugins
  desktop-effects genisoimage gs-esp-x gtk2-engines-pixbuf kde-style-polyester
  libdecoration0 libgs-esp8 openprinting-ppds python-software-properties
  software-properties-kde wodim
The following packages will be upgraded:
  cdrecord gs-esp kdelibs-data kwin libcupsimage2 libgnomeui-0
  libgnomeui-common libgnomeui-dev libgnomevfs2-0 libgnomevfs2-common
  libgnomevfs2-dev libgnomevfs2-extra libxcomposite-dev libxcomposite1
  libxcomposite1-dbg mkisofs xcdroast xkb-data xserver-xorg-core
19 upgraded, 17 newly installed, 3 to remove and 1350 not upgraded.
167 not fully installed or removed.
Need to get 0B/26.4MB of archives.
After unpacking 11.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 75, <> line 36.)
debconf: falling back to frontend: Readline
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 242033 files and directories currently installed.)
Preparing to replace xkb-data 0.8-7ubuntu2 (using .../xkb-data_0.9-4ubuntu1_all.deb) ...
/var/lib/dpkg/tmp.ci/preinst: 56: xargs: not found
dpkg: error processing /var/cache/apt/archives/xkb-data_0.9-4ubuntu1_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 127
dpkg: regarding .../xserver-xorg-core_2%3a1.2.0-3ubuntu8_i386.deb containing xserver-xorg-core:
 xserver-xorg-core conflicts with xkb-data (<< 0.9)
  xkb-data (version 0.8-7ubuntu2) is installed.
dpkg: error processing /var/cache/apt/archives/xserver-xorg-core_2%3a1.2.0-3ubuntu8_i386.deb (--unpack):
 conflicting packages - not installing xserver-xorg-core
Preparing to replace kdelibs-data 4:3.5.5-0ubuntu3.4 (using .../kdelibs-data_4%3a3.5.6-0ubuntu14_all.deb) ...
/var/lib/dpkg/tmp.ci/preinst: 31: awk: Permission denied
dpkg: error processing /var/cache/apt/archives/kdelibs-data_4%3a3.5.6-0ubuntu14_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 126
Errors were encountered while processing:
 /var/cache/apt/archives/xkb-data_0.9-4ubuntu1_all.deb
 /var/cache/apt/archives/xserver-xorg-core_2%3a1.2.0-3ubuntu8_i386.deb
 /var/cache/apt/archives/kdelibs-data_4%3a3.5.6-0ubuntu14_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@pinguin1:/home/austin# dpkg --configure -a
dpkg: dependency problems prevent configuration of kdelibs4c2a:
 kdelibs4c2a depends on kdelibs-data (>> 4:3.5.6); however:
  Version of kdelibs-data on system is 4:3.5.5-0ubuntu3.4.
dpkg: error processing kdelibs4c2a (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-sis:
 xserver-xorg-video-sis depends on xserver-xorg-core (>= 2:1.1.1); however:
  Version of xserver-xorg-core on system is 1:1.1.1-0ubuntu12.2.
dpkg: error processing xserver-xorg-video-sis (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-apm:
 xserver-xorg-video-apm depends on xserver-xorg-core (>= 2:1.1.1-1); however:
  Version of xserver-xorg-core on system is 1:1.1.1-0ubuntu12.2.
dpkg: error processing xserver-xorg-video-apm (--configure):
 dependency problems - leaving unconfigured
Setting up libsdl-sound1.2 (1.0.1-12build1) ...

dpkg: dependency problems prevent configuration of xserver-xorg-video-s3virge:
 xserver-xorg-video-s3virge depends on xserver-xorg-core (>= 2:1.1.1); however:
  Version of xserver-xorg-core on system is 1:1.1.1-0ubuntu12.2.
dpkg: error processing xserver-xorg-video-s3virge (--configure):
 dependency problems - leaving unconfigured
Setting up libssl0.9.8 (0.9.8c-4build1) ...
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 75.)
debconf: falling back to frontend: Readline
Checking for services that may need to be restarted.../var/lib/dpkg/info/libssl0.9.8.postinst: line 75: /usr/bin/awk: Permission denied
dpkg: error processing libssl0.9.8 (--configure):
 subprocess post-installation script returned error exit status 126
Setting up python2.5-minimal (2.5.1~rc1-0ubuntu3) ...
Linking and byte-compiling packages for runtime python2.5...
/var/lib/dpkg/info/python2.5-minimal.postinst: 39: awk: Permission denied
dpkg: error processing python2.5-minimal (--configure):
 subprocess post-installation script returned error exit status 126
dpkg: dependency problems prevent configuration of xserver-xorg-video-vmware:
 xserver-xorg-video-vmware depends on xserver-xorg-core (>= 2:1.1.1); however:
  Version of xserver-xorg-core on system is 1:1.1.1-0ubuntu12.2.
dpkg: error processing xserver-xorg-video-vmware (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-savage:
 xserver-xorg-video-savage depends on xserver-xorg-core (>= 2:1.1.1); however:
  Version of xserver-xorg-core on system is 1:1.1.1-0ubuntu12.2.
dpkg: error processing xserver-xorg-video-savage (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-fbdev:
 xserver-xorg-video-fbdev depends on xserver-xorg-core (>= 2:1.1.1-11); however:
  Version of xserver-xorg-core on system is 1:1.1.1-0ubuntu12.2.
dpkg: error processing xserver-xorg-video-fbdev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-input-evdev:
 xserver-xorg-input-evdev depends on xserver-xorg-core (>= 2:1.1.1-1); however:
  Version of xserver-xorg-core on system is 1:1.1.1-0ubuntu12.2.
dpkg: error processing xserver-xorg-input-evdev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-glint:
 xserver-xorg-video-glint depends on xserver-xorg-core (>= 2:1.1.1); however:
  Version of xserver-xorg-core on system is 1:1.1.1-0ubuntu12.2.
dpkg: error processing xserver-xorg-video-glint (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-all:
 xserver-xorg-video-all depends on xserver-xorg-video-apm; however:
  Package xserver-xorg-video-apm is not configured yet.
 xserver-xorg-video-all depends on xserver-xorg-video-fbdev; however:
  Package xserver-xorg-video-fbdev is not configured yet.
 xserver-xorg-video-all depends on xserver-xorg-video-glint; however:
  Package xserver-xorg-video-glint is not configured yet.
 xserver-xorg-video-all depends on xserver-xorg-video-s3virge; however:
  Package xserver-xorg-video-s3virge is not configured yet.
 xserver-xorg-video-all depends on xserver-xorg-video-savage; however:
  Package xserver-xorg-video-savage is not configured yet.
 xserver-xorg-video-all depends on xserver-xorg-video-sis; however:
  Package xserver-xorg-video-sis is not configured yet.
 xserver-xorg-video-all depends on xserver-xorg-video-vmware; however:
  Package xserver-xorg-video-vmware is not configured yet.
dpkg: error processing xserver-xorg-video-all (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python2.5:
 python2.5 depends on python2.5-minimal (= 2.5.1~rc1-0ubuntu3); however:
  Package python2.5-minimal is not configured yet.
 python2.5 depends on libssl0.9.8 (>= 0.9.8c-1); however:
  Package libssl0.9.8 is not configured yet.
dpkg: error processing python2.5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-imstt:
 xserver-xorg-video-imstt depends on xserver-xorg-core (>= 2:1.1.1); however:
  Version of xserver-xorg-core on system is 1:1.1.1-0ubuntu12.2.
dpkg: error processing xserver-xorg-video-imstt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-cyrix:
 xserver-xorg-video-cyrix depends on xserver-xorg-core (>= 2:1.1.1); however:
  Version of xserver-xorg-core on system is 1:1.1.1-0ubuntu12.2.
dpkg: error processing xserver-xorg-video-cyrix (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-vesa:
 xserver-xorg-video-vesa depends on xserver-xorg-core (>= 2:1.1.1-11); however:
  Version of xserver-xorg-core on system is 1:1.1.1-0ubuntu12.2.
dpkg: error processing xserver-xorg-video-vesa (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of postfix:
 postfix depends on libssl0.9.8 (>= 0.9.8c-1); however:
  Package libssl0.9.8 is not configured yet.
dpkg: error processing postfix (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-rendition:
 xserver-xorg-video-rendition depends on xserver-xorg-core (>= 2:1.1.1); however:
  Version of xserver-xorg-core on system is 1:1.1.1-0ubuntu12.2.
dpkg: error processing xserver-xorg-video-rendition (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-dummy:
 xserver-xorg-video-dummy depends on xserver-xorg-core (>= 2:1.1.1); however:
  Version of xserver-xorg-core on system is 1:1.1.1-0ubuntu12.2.
dpkg: error processing xserver-xorg-video-dummy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-sisusb:
 xserver-xorg-video-sisusb depends on xserver-xorg-core (>= 2:1.1.1); however:
  Version of xserver-xorg-core on system is 1:1.1.1-0ubuntu12.2.
dpkg: error processing xserver-xorg-video-sisusb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-input-elographics:
 xserver-xorg-input-elographics depends on xserver-xorg-core (>= 2:1.1.1-1); however:
  Version of xserver-xorg-core on system is 1:1.1.1-0ubuntu12.2.
dpkg: error processing xserver-xorg-input-elographics (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-tdfx:
 xserver-xorg-video-tdfx depends on xserver-xorg-core (>= 2:1.1.1-11); however:
  Version of xserver-xorg-core on system is 1:1.1.1-0ubuntu12.2.
dpkg: error processing xserver-xorg-video-tdfx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-ark:
 xserver-xorg-video-ark depends on xserver-xorg-core (>= 2:1.1.1-1); however:
  Version of xserver-xorg-core on system is 1:1.1.1-0ubuntu12.2.
dpkg: error processing xserver-xorg-video-ark (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-cirrus:
 xserver-xorg-video-cirrus depends on xserver-xorg-core (>= 2:1.1.1); however:
  Version of xserver-xorg-core on system is 1:1.1.1-0ubuntu12.2.
dpkg: error processing xserver-xorg-video-cirrus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-neomagic:
 xserver-xorg-video-neomagic depends on xserver-xorg-core (>= 2:1.1.1-11); however:
  Version of xserver-xorg-core on system is 1:1.1.1-0ubuntu12.2.
dpkg: error processing xserver-xorg-video-neomagic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-newport:
 xserver-xorg-video-newport depends on xserver-xorg-core (>= 2:1.1.1); however:
  Version of xserver-xorg-core on system is 1:1.1.1-0ubuntu12.2.
dpkg: error processing xserver-xorg-video-newport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsasl2-modules:
 libsasl2-modules depends on libssl0.9.8 (>= 0.9.8c-1); however:
  Package libssl0.9.8 is not configured yet.
dpkg: error processing libsasl2-modules (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsasl2-2:
 libsasl2-2 depends on libsasl2-modules (= 2.1.22.dfsg1-8ubuntu2) | libsasl2-modules-sql (= 2.1.22.dfsg1-8ubuntu2) | libsasl2-modules-gssapi-heimdal (= 2.1.22.dfsg1-8ubuntu2) | libsasl2-modules-kerberos-heimdal (= 2.1.22.dfsg1-8ubuntu2); however:
  Package libsasl2-modules is not configured yet.
  Package libsasl2-modules-sql is not installed.
  Package libsasl2-modules-gssapi-heimdal is not installed.
  Package libsasl2-modules-kerberos-heimdal is not installed.
dpkg: error processing libsasl2-2 (--configure):
 dependency problems - leaving unconfigured
Setting up libsdl-mixer1.2 (1.2.6-1.1build1) ...

dpkg: dependency problems prevent configuration of xserver-xorg-video-nsc:
 xserver-xorg-video-nsc depends on xserver-xorg-core (>= 2:1.1.1); however:
  Version of xserver-xorg-core on system is 1:1.1.1-0ubuntu12.2.
dpkg: error processing xserver-xorg-video-nsc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apache2-utils:
 apache2-utils depends on libssl0.9.8 (>= 0.9.8c-1); however:
  Package libssl0.9.8 is not configured yet.
dpkg: error processing apache2-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-mga:
 xserver-xorg-video-mga depends on xserver-xorg-core (>= 2:1.1.1-11); however:
  Version of xserver-xorg-core on system is 1:1.1.1-0ubuntu12.2.
dpkg: error processing xserver-xorg-video-mga (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-i128:
 xserver-xorg-video-i128 depends on xserver-xorg-core (>= 2:1.1.1); however:
  Version of xserver-xorg-core on system is 1:1.1.1-0ubuntu12.2.
dpkg: error processing xserver-xorg-video-i128 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-vga:
 xserver-xorg-video-vga depends on xserver-xorg-core (>= 2:1.1.1); however:
  Version of xserver-xorg-core on system is 1:1.1.1-0ubuntu12.2.
dpkg: error processing xserver-xorg-video-vga (--configure):
 dependency problems - leaving unconfigured
Setting up phpmyadmin (2.9.1.1-2ubuntu1) ...
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 75.)
debconf: falling back to frontend: Readline
/usr/bin/ucf: line 556: /usr/bin/awk: Permission denied
dpkg: error processing phpmyadmin (--configure):
 subprocess post-installation script returned error exit status 126
dpkg: dependency problems prevent configuration of libssl-dev:
 libssl-dev depends on libssl0.9.8 (= 0.9.8c-4build1); however:
  Package libssl0.9.8 is not configured yet.
dpkg: error processing libssl-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-s3:
 xserver-xorg-video-s3 depends on xserver-xorg-core (>= 2:1.1.1-11); however:
  Version of xserver-xorg-core on system is 1:1.1.1-0ubuntu12.2.
dpkg: error processing xserver-xorg-video-s3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-trident:
 xserver-xorg-video-trident depends on xserver-xorg-core (>= 2:1.1.1-11); however:
  Version of xserver-xorg-core on system is 1:1.1.1-0ubuntu12.2.
dpkg: error processing xserver-xorg-video-trident (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-tga:
 xserver-xorg-video-tga depends on xserver-xorg-core (>= 2:1.1.1); however:
  Version of xserver-xorg-core on system is 1:1.1.1-0ubuntu12.2.
dpkg: error processing xserver-xorg-video-tga (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-chips:
 xserver-xorg-video-chips depends on xserver-xorg-core (>= 2:1.1.1); however:
  Version of xserver-xorg-core on system is 1:1.1.1-0ubuntu12.2.
dpkg: error processing xserver-xorg-video-chips (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-i810:
 xserver-xorg-video-i810 depends on xserver-xorg-core (>= 2:1.1.1-11); however:
  Version of xserver-xorg-core on system is 1:1.1.1-0ubuntu12.2.
dpkg: error processing xserver-xorg-video-i810 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apache2.2-common:
 apache2.2-common depends on apache2-utils; however:
  Package apache2-utils is not configured yet.
dpkg: error processing apache2.2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libapache2-mod-php5:
 libapache2-mod-php5 depends on libssl0.9.8 (>= 0.9.8c-1); however:
  Package libssl0.9.8 is not configured yet.
 libapache2-mod-php5 depends on apache2.2-common; however:
  Package apache2.2-common is not configured yet.
dpkg: error processing libapache2-mod-php5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-input-all:
 xserver-xorg-input-all depends on xserver-xorg-input-evdev; however:
  Package xserver-xorg-input-evdev is not configured yet.
 xserver-xorg-input-all depends on xserver-xorg-input-elographics; however:
  Package xserver-xorg-input-elographics is not configured yet.
dpkg: error processing xserver-xorg-input-all (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsasl2:
 libsasl2 depends on libsasl2-2 (= 2.1.22.dfsg1-8ubuntu2); however:
  Package libsasl2-2 is not configured yet.
dpkg: error processing libsasl2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-input-mouse:
 xserver-xorg-input-mouse depends on xserver-xorg-core (>= 2:1.1.1-1); however:
  Version of xserver-xorg-core on system is 1:1.1.1-0ubuntu12.2.
dpkg: error processing xserver-xorg-input-mouse (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-nv:
 xserver-xorg-video-nv depends on xserver-xorg-core (>= 2:1.1.1); however:
  Version of xserver-xorg-core on system is 1:1.1.1-0ubuntu12.2.
dpkg: error processing xserver-xorg-video-nv (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php5:
 php5 depends on libapache2-mod-php5 (>= 5.2.1-0ubuntu1) | php5-cgi (>= 5.2.1-0ubuntu1); however:
  Package libapache2-mod-php5 is not configured yet.
  Package php5-cgi is not installed.
dpkg: error processing php5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-via:
 xserver-xorg-video-via depends on xserver-xorg-core (>= 2:1.1.1-11); however:
  Version of xserver-xorg-core on system is 1:1.1.1-0ubuntu12.2.
dpkg: error processing xserver-xorg-video-via (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdelibs4-dev:
 kdelibs4-dev depends on kdelibs4c2a (= 4:3.5.6-0ubuntu14); however:
  Package kdelibs4c2a is not configured yet.
 kdelibs4-dev depends on libssl-dev; however:
  Package libssl-dev is not configured yet.
dpkg: error processing kdelibs4-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libsasl2-dev:
 libsasl2-dev depends on libsasl2-modules (= 2.1.22.dfsg1-8ubuntu2); however:
  Package libsasl2-modules is not configured yet.
dpkg: error processing libsasl2-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-input-kbd:
 xserver-xorg-input-kbd depends on xserver-xorg-core (>= 2:1.1.1-4); however:
  Version of xserver-xorg-core on system is 1:1.1.1-0ubuntu12.2.
dpkg: error processing xserver-xorg-input-kbd (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Errors were encountered while processing:
 kdelibs4c2a
 xserver-xorg-video-sis
 xserver-xorg-video-apm
 xserver-xorg-video-s3virge
 libssl0.9.8
 python2.5-minimal
 xserver-xorg-video-vmware
 xserver-xorg-video-savage
 xserver-xorg-video-fbdev
 xserver-xorg-input-evdev
 xserver-xorg-video-glint
 xserver-xorg-video-all
 python2.5
 xserver-xorg-video-imstt
 xserver-xorg-video-cyrix
 xserver-xorg-video-vesa
 postfix
 xserver-xorg-video-rendition
 xserver-xorg-video-dummy
 xserver-xorg-video-sisusb
 xserver-xorg-input-elographics
 xserver-xorg-video-tdfx
 xserver-xorg-video-ark
 xserver-xorg-video-cirrus
 xserver-xorg-video-neomagic
 xserver-xorg-video-newport
 libsasl2-modules
 libsasl2-2
 xserver-xorg-video-nsc
 apache2-utils
 xserver-xorg-video-mga
 xserver-xorg-video-i128
 xserver-xorg-video-vga
 phpmyadmin
 libssl-dev
 xserver-xorg-video-s3
 xserver-xorg-video-trident
 xserver-xorg-video-tga
 xserver-xorg-video-chips
 xserver-xorg-video-i810
 apache2.2-common
 libapache2-mod-php5
 xserver-xorg-input-all
 libsasl2
 xserver-xorg-input-mouse
 xserver-xorg-video-nv
 php5
 xserver-xorg-video-via
 kdelibs4-dev
 libsasl2-dev
 xserver-xorg-input-kbd
Processing was halted because there were too many errors.

```

Any ideas what to do next? 

Please advise. 

Regards,
Matt

---

### Post by sirmrmatt on 2007-04-28
In response to the above messages advice to "run apt-get autoremove," I did and got the following:


```
root@pinguin1:/home/austin# apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  kdelibs4c2a: Depends: kdelibs-data (> 4:3.5.6) but 4:3.5.5-0ubuntu3.4 is installed
  xserver-xorg-input-elographics: Depends: xserver-xorg-core (>= 2:1.1.1-1) but 1:1.1.1-0ubuntu12.2 is installed
  xserver-xorg-input-evdev: Depends: xserver-xorg-core (>= 2:1.1.1-1) but 1:1.1.1-0ubuntu12.2 is installed
  xserver-xorg-input-kbd: Depends: xserver-xorg-core (>= 2:1.1.1-4) but 1:1.1.1-0ubuntu12.2 is installed
  xserver-xorg-input-mouse: Depends: xserver-xorg-core (>= 2:1.1.1-1) but 1:1.1.1-0ubuntu12.2 is installed
  xserver-xorg-video-apm: Depends: xserver-xorg-core (>= 2:1.1.1-1) but 1:1.1.1-0ubuntu12.2 is installed
  xserver-xorg-video-ark: Depends: xserver-xorg-core (>= 2:1.1.1-1) but 1:1.1.1-0ubuntu12.2 is installed
  xserver-xorg-video-ati: Depends: xserver-xorg-core (>= 2:1.1.1-1) but 1:1.1.1-0ubuntu12.2 is installed
  xserver-xorg-video-chips: Depends: xserver-xorg-core (>= 2:1.1.1) but 1:1.1.1-0ubuntu12.2 is installed
  xserver-xorg-video-cirrus: Depends: xserver-xorg-core (>= 2:1.1.1) but 1:1.1.1-0ubuntu12.2 is installed
  xserver-xorg-video-cyrix: Depends: xserver-xorg-core (>= 2:1.1.1) but 1:1.1.1-0ubuntu12.2 is installed
  xserver-xorg-video-dummy: Depends: xserver-xorg-core (>= 2:1.1.1) but 1:1.1.1-0ubuntu12.2 is installed
  xserver-xorg-video-fbdev: Depends: xserver-xorg-core (>= 2:1.1.1-11) but 1:1.1.1-0ubuntu12.2 is installed
  xserver-xorg-video-glint: Depends: xserver-xorg-core (>= 2:1.1.1) but 1:1.1.1-0ubuntu12.2 is installed
  xserver-xorg-video-i128: Depends: xserver-xorg-core (>= 2:1.1.1) but 1:1.1.1-0ubuntu12.2 is installed
  xserver-xorg-video-i740: Depends: xserver-xorg-core (>= 2:1.1.1) but 1:1.1.1-0ubuntu12.2 is installed
  xserver-xorg-video-i810: Depends: xserver-xorg-core (>= 2:1.1.1-11) but 1:1.1.1-0ubuntu12.2 is installed
  xserver-xorg-video-imstt: Depends: xserver-xorg-core (>= 2:1.1.1) but 1:1.1.1-0ubuntu12.2 is installed
  xserver-xorg-video-mga: Depends: xserver-xorg-core (>= 2:1.1.1-11) but 1:1.1.1-0ubuntu12.2 is installed
  xserver-xorg-video-neomagic: Depends: xserver-xorg-core (>= 2:1.1.1-11) but 1:1.1.1-0ubuntu12.2 is installed
  xserver-xorg-video-newport: Depends: xserver-xorg-core (>= 2:1.1.1) but 1:1.1.1-0ubuntu12.2 is installed
  xserver-xorg-video-nsc: Depends: xserver-xorg-core (>= 2:1.1.1) but 1:1.1.1-0ubuntu12.2 is installed
  xserver-xorg-video-nv: Depends: xserver-xorg-core (>= 2:1.1.1) but 1:1.1.1-0ubuntu12.2 is installed
  xserver-xorg-video-rendition: Depends: xserver-xorg-core (>= 2:1.1.1) but 1:1.1.1-0ubuntu12.2 is installed
  xserver-xorg-video-s3: Depends: xserver-xorg-core (>= 2:1.1.1-11) but 1:1.1.1-0ubuntu12.2 is installed
  xserver-xorg-video-s3virge: Depends: xserver-xorg-core (>= 2:1.1.1) but 1:1.1.1-0ubuntu12.2 is installed
  xserver-xorg-video-savage: Depends: xserver-xorg-core (>= 2:1.1.1) but 1:1.1.1-0ubuntu12.2 is installed
  xserver-xorg-video-siliconmotion: Depends: xserver-xorg-core (>= 2:1.1.1) but 1:1.1.1-0ubuntu12.2 is installed
  xserver-xorg-video-sis: Depends: xserver-xorg-core (>= 2:1.1.1) but 1:1.1.1-0ubuntu12.2 is installed
  xserver-xorg-video-sisusb: Depends: xserver-xorg-core (>= 2:1.1.1) but 1:1.1.1-0ubuntu12.2 is installed
  xserver-xorg-video-tdfx: Depends: xserver-xorg-core (>= 2:1.1.1-11) but 1:1.1.1-0ubuntu12.2 is installed
  xserver-xorg-video-tga: Depends: xserver-xorg-core (>= 2:1.1.1) but 1:1.1.1-0ubuntu12.2 is installed
  xserver-xorg-video-trident: Depends: xserver-xorg-core (>= 2:1.1.1-11) but 1:1.1.1-0ubuntu12.2 is installed
  xserver-xorg-video-tseng: Depends: xserver-xorg-core (>= 2:1.1.1) but 1:1.1.1-0ubuntu12.2 is installed
  xserver-xorg-video-vesa: Depends: xserver-xorg-core (>= 2:1.1.1-11) but 1:1.1.1-0ubuntu12.2 is installed
  xserver-xorg-video-vga: Depends: xserver-xorg-core (>= 2:1.1.1) but 1:1.1.1-0ubuntu12.2 is installed
  xserver-xorg-video-via: Depends: xserver-xorg-core (>= 2:1.1.1-11) but 1:1.1.1-0ubuntu12.2 is installed
  xserver-xorg-video-vmware: Depends: xserver-xorg-core (>= 2:1.1.1) but 1:1.1.1-0ubuntu12.2 is installed
E: Unmet dependencies. Try using -f.

```

Does this help? Seems like I was getting xserver-xorg errors in previous command "episode" above?

Regards,
Matt

---

