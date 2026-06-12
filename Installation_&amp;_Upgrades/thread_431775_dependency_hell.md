---
title: "dependency hell ?"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by brazzmonkey on 2007-05-03
today, out of curiosity, i ran sudo aptitude install.
here's what i got :
```
sudo aptitude install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages are BROKEN:
  amarok apache2-mpm-prefork apache2.2-common beagle beryl-settings dazuko-source envy foo2zjs gs-esp juk kdebluetooth koffice kopete kubuntu-desktop
  libapache2-mod-php5 libdevmapper1.02 libfinance-quote-perl libfreebob0 libgphoto2-2-dev libmono-system1.0-cil libpango1.0-0 libpythonize0 libqt4-qt3support
  libqt4-sql libsasl2-2 libsvn1 libxalan2-java libxerces2-java lirc mysql-server-5.0 nvidia-glx nvidia-glx-new openoffice.org openoffice.org-common
  openoffice.org-style-default php5 php5-mysql powersaved prevu skype subversion vmware-server
The following packages are unused and will be REMOVED:
  python-imaging python-imaging-tk
The following NEW packages will be installed:
  automatix2 kde-guidance-powermanager kicker-kblogger libsdl1.2debian-alsa oooqs2-kde openoffice.org-help-en-us openoffice.org-help-fr
  openoffice.org-l10n-en-us openoffice.org-thesaurus-en-us scribus ttf-arabeyes ttf-arphic-ukai ttf-arphic-uming ttf-baekmuk ttf-bengali-fonts
  ttf-devanagari-fonts ttf-gentium ttf-indic-fonts ttf-kannada-fonts ttf-kochi-gothic ttf-kochi-mincho ttf-lao ttf-malayalam-fonts ttf-oriya-fonts
  ttf-punjabi-fonts ttf-tamil-fonts ttf-telugu-fonts ttf-thai-tlwg xinetd
The following packages will be REMOVED:
  3ddesktop apache2-utils apport apport-qt artwiz-cursor avahi-autoipd beryl-kubuntu bum camorama checkinstall clamav{p} clamav-base clamav-freshclam clara
  comixcursors command-not-found command-not-found-data convertall cpufrequtils crystalcursors cups-pdf cvs debootstrap desktop-file-utils devscripts dh-make
  dhcdbd dialog dmsetup dpatch dvb-utils dvdauthor fakeroot festival festlex-cmu festlex-poslex festvox-kallpc16k fftw3 filezilla filezilla-common
  flashplugin-nonfree gawk giblib1 gnome-about gnumeric gnumeric-common gnumeric-plugins-extra gocr gpm gproftpd gqcam gs-esp-x gstreamer0.10-pitfdll guessnet
  hal-device-manager hibernate hpijs-ppds hwdb-client-gnome ifplugd imwheel inkscape k9copy kde-hal-device-manager kde-style-polyester kdewebdev kdocker
  kfilereplace kicker-kickoff kimagemapeditor kio-beagle klamav klinkstatus kmyfirewall kmysqladmin knemo knetload knetworkmanager kommander kompare kplato
  krename ksame ksensors kxdocker kxdocker-data kxsldbg language-pack-gnome-en language-pack-gnome-en-base language-pack-gnome-fr language-pack-gnome-fr-base
  libapache2-mod-auth-mysql libapr1 libaprutil1 libcairo-perl libcairomm-1.0-1 libclamav2 libclucene0 libcpufreq0 libcrypt-ssleay-perl libcurses-perl
  libcurses-ui-perl libcvsservice0 libdb4.2 libdbd-mysql-perl libdbi-perl libdvdplay0 libebml-dev libenchant1c2a libestools1.2 libevent1 libfame-0.9 libgadu3
  libgcj7-awt libgdiplus libglib-perl libglibmm-2.4-1c2a libgoffice-0-3 libgoffice-0-common libgs-esp8 libgsasl7 libgsf-gnome-1-114 libgssapi2 libgtk1.2
  libgtk1.2-common libgtk2-gladexml-perl libgtk2-perl libgtkmm-2.4-1c2a libiec61883-0 libjack0.100.0-0 libjaxp1.3-java libk3b2-mp3 libkpathsea4
  liblaunchpad-integration0 liblockfile1 liblog4cxx9c2a libmatroska-dev libmeanwhile1 libmjpegtools0c2a libmono-corlib2.0-cil libmono-data-tds2.0-cil
  libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-system2.0-cil
  libmono2.0-cil libmysqlclient14 libnet-daemon-perl libnet1 libnetpbm10 libnl1-pre6 libnm-util0 libofa0 libopenobex1 libpcap0.7 libplrpc-perl libpostproc0
  libpq5 libpvm3 libqt-perl libqt3-i18n libquicktime0 librpcsecgss2 librsvg2-common librte1 libsdl1.2debian-all libsmokeqt1 libssl0.9.7 libstrigihtmlgui0
  libsvga1 libt1-5 libterm-readkey-perl libthai0 libtunepimp5 libusb-dev libytnef0 libzvbi-common libzvbi0 links2 linuxprinting.org-ppds lirc-modules-source
  lm-sensors lomoco lsb lsb-core lsb-cxx lsb-desktop lsb-graphics lynx mailx mencoder mercurial module-assistant mpg123-alsa mscompress msmtp mysql-client-5.0
  ncurses-term netkit-inetd network-manager nfs-common ocrad openoffice.org-filter-mobiledev openoffice.org-l10n-en-gb openoffice.org-officebean p7zip
  p7zip-full pax pbuilder pdfedit pdfjam pdftk perlmagick php5-cgi php5-common php5-imagick phpmyadmin pia plib1.8.4c2 portmap postfix preload proftpd pxlib1
  python-apport python-gnupginterface python-launchpad-bugs python-launchpad-integration python-problem-report python-reportlab python-reportlab-accel
  python-software-properties python-xdg python2.5-dev quanta quanta-data regionset resolvconf sane-utils scantv scribus-ng scrot sdparm showimg
  software-properties-kde strigi-applet strigi-daemon synaptic sysv-rc-conf tango-icon-theme-extras tetex-base tetex-bin tetex-extra tex-common transcode
  tuxpuck tvtime unace-nonfree unattended-upgrades update-manager-core v4l-conf vamps vlc-plugin-alsa vlc-plugin-arts vmware-server-kernel-modules
  vmware-server-kernel-modules-2.6.20-15 webcam webcamd wv xarchiver xawtv xawtv-plugins xnest xsane xsane-common xserver-xephyr xserver-xorg-dev ytnef
0 packages upgraded, 31 newly installed, 281 to remove and 0 not upgraded.
Need to get 85.4MB of archives. After unpacking 526MB will be freed.
The following packages have unmet dependencies:
  lirc: PreDepends: dialog but it is not installable
  libfreebob0: Depends: libiec61883-0 (>= 1.1.0) but it is not installable
  gs-esp: Depends: libgs-esp8 but it is not installable
  openoffice.org-style-default: Depends: openoffice.org-style-andromeda (= 2.2.0-1ubuntu3) but it is not installable
  libpythonize0: Depends: python2.5-dev but it is not installable
  kdebluetooth: Depends: libopenobex1 but it is not installable
  koffice: Depends: kplato (>= 1:1.6.2-0ubuntu1) but it is not installable
  php5: Depends: php5-common (>= 5.2.1-0ubuntu1.1) but it is not installable
  nvidia-glx-new: Conflicts: nvidia-glx but 1:1.0.9631+2.6.20.5-15.20 is to be installed.
  libqt4-qt3support: Depends: libpq5 but it is not installable
  mysql-server-5.0: Depends: mysql-client-5.0 (>= 5.0.38-0ubuntu1) but it is not installable
                    Depends: libdbi-perl but it is not installable
  libfinance-quote-perl: Depends: libcrypt-ssleay-perl but it is not installable
  subversion: Depends: libapr1 but it is not installable
  libdevmapper1.02: Depends: dmsetup (>= 2:1.02.08-1ubuntu2) but it is not installable
  apache2-mpm-prefork: Depends: libapr1 but it is not installable
                       Depends: libaprutil1 but it is not installable
                       Depends: libpq5 but it is not installable
  powersaved: Depends: libcpufreq0 but it is not installable
  kubuntu-desktop: Depends: avahi-autoipd but it is not installable
                   Depends: gs-esp-x but it is not installable
                   Depends: kde-style-polyester but it is not installable
                   Depends: libqt-perl but it is not installable
                   Depends: software-properties-kde but it is not installable
  vmware-server: Depends: netkit-inetd but it is not installable or
                          inetd which is a virtual package.
                 Depends: vmware-server-kernel-modules but it is not installable
                 Depends: librsvg2-common (>= 2.9.5) but it is not installable
                 Depends: libssl0.9.7 but it is not installable
                 Conflicts: xinetd but 1:2.3.14-1ubuntu1 is to be installed.
  libsvn1: Depends: libapr1 but it is not installable
           Depends: libaprutil1 but it is not installable
  skype: Depends: librte1 but it is not installable
  libgphoto2-2-dev: Depends: libusb-dev but it is not installable
  apache2.2-common: Depends: apache2-utils but it is not installable
  libpango1.0-0: Depends: libthai0 (>= 0.1.7) but it is not installable
  libmono-system1.0-cil: Depends: libgdiplus (>= 1.1.18) but it is not installable
  beryl-settings: Depends: librsvg2-common but it is not installable
  openoffice.org-common: Depends: desktop-file-utils but it is not installable
  beagle: Depends: libmono-corlib2.0-cil (>= 1.2.3) but it is not installable
          Depends: libmono-sharpzip2.84-cil (>= 1.0) but it is not installable
          Depends: libmono-sqlite2.0-cil (>= 1.0) but it is not installable
          Depends: libmono-system-data2.0-cil (>= 1.0) but it is not installable
          Depends: libmono-system-web2.0-cil (>= 1.0) but it is not installable
          Depends: libmono-system2.0-cil (>= 1.2.3) but it is not installable
          Depends: libmono2.0-cil (>= 1.2.3) but it is not installable
  openoffice.org: Depends: openoffice.org-filter-mobiledev but it is not installable
  amarok: Depends: libpq5 but it is not installable
          Depends: libtunepimp5 but it is not installable
  juk: Depends: libtunepimp5 but it is not installable
  libxerces2-java: Depends: libjaxp1.3-java but it is not installable
  libqt4-sql: Depends: libpq5 but it is not installable
  dazuko-source: Depends: module-assistant but it is not installable
  envy: Depends: xserver-xorg-dev but it is not installable
        Depends: module-assistant but it is not installable
        Depends: fakeroot but it is not installable
        Depends: dh-make but it is not installable
  libxalan2-java: Depends: libjaxp1.3-java but it is not installable
  foo2zjs: Depends: mscompress but it is not installable
  prevu: Depends: pbuilder but it is not installable
         Depends: devscripts but it is not installable
         Depends: debootstrap but it is not installable
         Depends: fakeroot but it is not installable
  libsasl2-2: Depends: libdb4.2 but it is not installable
  php5-mysql: Depends: php5-common (= 5.2.1-0ubuntu1.1) but it is not installable
  kopete: Depends: libgadu3 (>= 1:1.7~rc2) but it is not installable
          Depends: libmeanwhile1 (>= 1.0.2) but it is not installable
  libapache2-mod-php5: Depends: php5-common (= 5.2.1-0ubuntu1.1) but it is not installable
  nvidia-glx: Conflicts: nvidia-glx-new but 1.0.9755+2.6.20.5-15.20 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
kubuntu-desktop
prevu
vmware-server

Keep the following packages at their current version:
apache2-utils [2.2.3-3.2build1 (feisty, now)]
command-not-found [0.2.4 (feisty, now)]
command-not-found-data [0.2.4 (feisty, now)]
cvs [1:1.12.13-5build1 (feisty, now)]
desktop-file-utils [0.12-0ubuntu2 (feisty, now)]
dh-make [0.42 (feisty, now)]
dialog [1.0-20060221-1 (feisty, now)]
dmsetup [2:1.02.08-1ubuntu10 (feisty, now)]
fakeroot [1.5.10ubuntu2 (feisty, now)]
fftw3 [3.1.2-1build1 (feisty, now)]
gawk [1:3.1.5.dfsg-4build1 (feisty, now)]
gs-esp-x [8.15.4.dfsg.1-0ubuntu1 (feisty, now)]
hpijs-ppds [2.7.2+1.7.3-0ubuntu1 (feisty, now)]
knemo [0.4.6-2ubuntu1 (feisty, now)]
knetload [2.3-3build1 (feisty, now)]
kplato [1:1.6.2-0ubuntu1 (feisty, now)]
ksensors [0.7.3-13ubuntu1 (feisty, now)]
libapr1 [1.2.7-8.1 (feisty, now)]
libaprutil1 [1.2.7+dfsg-2build1 (feisty, now)]
libcpufreq0 [002-2 (feisty, now)]
libcrypt-ssleay-perl [0.51-5 (feisty, now)]
libdb4.2 [4.2.52+dfsg-1build1 (feisty, now)]
libdbd-mysql-perl [3.0008-1build1 (feisty, now)]
libdbi-perl [1.53-1build1 (feisty, now)]
libgadu3 [1:1.7~rc2-2 (feisty, now)]
libgcj7-awt [4.1.2-0ubuntu5 (feisty, now)]
libgdiplus [1.2.3-0ubuntu1 (feisty, now)]
libgs-esp8 [8.15.4.dfsg.1-0ubuntu1 (feisty, now)]
libiec61883-0 [1.1.0-2ubuntu2 (feisty, now)]
libjaxp1.3-java [1.3.03-5 (feisty, now)]
liblockfile1 [1.06.1ubuntu1 (feisty, now)]
libmeanwhile1 [1.0.2-2 (feisty, now)]
libmono-corlib2.0-cil [1.2.3.1-1ubuntu1 (feisty, now)]
libmono-data-tds2.0-cil [1.2.3.1-1ubuntu1 (feisty, now)]
libmono-security2.0-cil [1.2.3.1-1ubuntu1 (feisty, now)]
libmono-sharpzip2.84-cil [1.2.3.1-1ubuntu1 (feisty, now)]
libmono-sqlite2.0-cil [1.2.3.1-1ubuntu1 (feisty, now)]
libmono-system-data2.0-cil [1.2.3.1-1ubuntu1 (feisty, now)]
libmono-system-web2.0-cil [1.2.3.1-1ubuntu1 (feisty, now)]
libmono-system2.0-cil [1.2.3.1-1ubuntu1 (feisty, now)]
libmono2.0-cil [1.2.3.1-1ubuntu1 (feisty, now)]
libnet-daemon-perl [0.38-1.1 (feisty, now)]
libofa0 [0.9.3-1 (feisty, now)]
libopenobex1 [1.3-3 (feisty, now)]
libplrpc-perl [0.2017-1.1 (feisty, now)]
libpq5 [8.2.4-0ubuntu0.7.04 (feisty-security, now)]
libqt-perl [3.008-2build1 (feisty, now)]
librsvg2-common [2.16.0-0ubuntu2 (feisty, now)]
librte1 [0.5.1-0.1 (feisty, now)]
libsmokeqt1 [4:3.5.5-1ubuntu4 (feisty, now)]
libstrigihtmlgui0 [0.3.11-1ubuntu1 (feisty, now)]
libthai0 [0.1.8-2 (feisty, now)]
libtunepimp5 [0.5.2-1ubuntu3 (feisty, now)]
libusb-dev [2:0.1.12-2 (feisty, now)]
lm-sensors [1:2.10.1-2ubuntu2 (feisty, now)]
mailx [1:8.1.2-0.20050715cvs-1ubuntu2 (feisty, now)]
module-assistant [0.10.10 (feisty, now)]
mscompress [0.3-2ubuntu1 (feisty, now)]
mysql-client-5.0 [5.0.38-0ubuntu1 (feisty, now)]
nvidia-glx [Not Installed]
ocrad [0.16-1 (feisty, now)]
openoffice.org-filter-mobiledev [2.2.0-1ubuntu3 (feisty, now)]
openoffice.org-style-default [Not Installed]
p7zip-full [4.43~dfsg.1-1 (feisty, now)]
php5-common [5.2.1-0ubuntu1.1 (feisty-security, now)]
postfix [2.3.8-2 (feisty, now)]
python-gnupginterface [0.3.2-9 (feisty, now)]
python-imaging [1.1.6-0ubuntu3 (feisty, now)]
python-reportlab [2.0dfsg-1 (feisty, now)]
python2.5-dev [2.5.1-0ubuntu1 (feisty-proposed, now)]
sane-utils [1.0.18-3ubuntu1 (feisty, now)]
sdparm [0.98-1 (feisty, now)]
showimg [0.9.5-1.1ubuntu1 (feisty, now)]
strigi-applet [0.3.11-1ubuntu1 (feisty, now)]
ttf-arphic-ukai [Not Installed]
ttf-arphic-uming [Not Installed]
update-manager-core [1:0.59.22 (feisty-proposed, now)]
xserver-xorg-dev [2:1.2.0-3ubuntu8 (feisty, now)]

Leave the following dependencies unresolved:
lsb-release recommends lsb
openoffice.org-core recommends nfs-common
kdvi recommends tetex-bin
Score is -5366

Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.

```
wtf ? is it safe to proceed (i suppose it's not...)
please note that my system has been upgraded from edgy to feisty about 2 weeks ago.

oh, and i get something similar using apt-get :
```
$ sudo apt-get install
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgtkhtml3.8-15 libtwolame0 libattr1-dev kdelibs4-dev libenchant1c2a ksim libmono-security1.0-cil kcharselect knewsticker-scripts kdessh libaspell-dev
  libtunepimp-bin kdemultimedia-dev libgksu1.2-1 libnss3 libaudiofile-dev libmono-sharpzip0.84-cil libglib2.0-dev python-gnome2-extras libgksuui1.0-1
  libmono-sqlite1.0-cil libgnome-media0 libmono-system-web1.0-cil libpcre3-dev kfloppy libgtksourceview1.0-0 liblualib50-dev kcalc libapr0 metacity-common
  libfinance-quote-perl libsasl2-dev libavahi-client-dev libogg-dev libjasper-1.701-dev khexedit libsvn0 kedit tango-icon-theme-common tango-icon-theme
  python-gtkhtml2 liblua50-dev lua50 librpcsecgss2 libavahi-qt3-dev libmono-sharpzip0.6-cil libacl1-dev libwv-1.2-1 tango-icon-theme-extras hspell libdbus-1-dev
  libxslt1-dev libhtml-tableextract-perl libssl-dev kdf libmono1.0-cil libgtksourceview-common libmono-data-tds1.0-cil libxml2-dev libtiff4-dev
  libmono-system-data1.0-cil libart-2.0-dev libesd0-dev libgtkhtml2-0 libnspr4 libmetacity0 libasound2-dev libtiffxx0c2 libmysqlclient14 libmyspell3c2
  libmono-system-runtime1.0-cil libtotem-plparser1 liblog4cxx9c2a libsynaptics0 libgtkspell0 libxml2-utils libartsc0-dev libopenexr-dev kdelirc superkaramba kjots
  libavahi-common-dev libnautilus-burn4 python-gnome2-desktop libclucene0 plib1.8.4c2 libgnome-desktop-2 kgpg libvorbis-dev gettext-kde libgdl-1-0 libidn11-dev
  libbz2-dev ktimer strigi-daemon libarts1-dev libnews-nntpclient-perl libgdl-1-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by TheWizzard on 2007-05-03
what are you trying to achieve with this command? 
normally you'd do
sudo aptitude install packagename

---

### Post by brazzmonkey on 2007-05-03
well, i have to admit that it was a typo at first, but it raised my curiosity. man aptitude gives :
```
As a special case, &#8220;install&#8221; with no arguments will act on any stored/pending actions.
```
i'm not sure whether i should worry or not...

---

### Post by zvacet on 2007-05-03
That command means nothing.I don´t know what are you tryin to d o,but I know that is not the way to do it.

```
sudo aptitude update && sudo aptitude upgrade
```


If you want to instal package with aptitude then 

```
sudo aptitude install package_name
```

---

### Post by rsambuca on 2007-05-03
Why don't you just select 'Y' and see what happens?:popcorn: 

Just kidding!

Just so you know, when I type it in, I just get the standard "0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."

---

### Post by mikewhatever on 2007-05-03
No, do not proceed! Are you asking for trouble with that curiosity of yours? 
To learn what aptitude or apt-get does open the terminal and type [COLOR="Sienna"]man aptitude[/COLOR].

I'd also strongly recommend to never enter a command of any kind out of curiosity. It might be like pressing some red button.

---

### Post by brazzmonkey on 2007-05-03
surely i wouldn't install all those crucial packages. i'm just trying to understand what would cause such output, especially since rsambuca doesn't get such weird output.
that makes me think something is wrong on my system, though i haven't encountered any troubles so far, except some usual, known bugs.

---

### Post by mikewhatever on 2007-05-03
Don't know of any 'usual or known bugs', can you update.

---

### Post by brazzmonkey on 2007-05-03
> **mikewhatever said:**
> Don't know of any 'usual or known bugs', can you update.
those ones for instance :
[http://ubuntuforums.org/showthread.php?t=415239](http://ubuntuforums.org/showthread.php?t=415239)
[http://ubuntuforums.org/showthread.php?t=420721](http://ubuntuforums.org/showthread.php?t=420721)
but this is out of topic...

---

### Post by jfinkels on 2007-05-03
If you want to remove unused dependencies, type ```
sudo apt-get autoremove
```
That will clear up a few packages.

Do you want to install a program? I don't understand what you're trying to do.

In general, when you see output like that from aptitude, it means that aptitude is getting confused when there are new upgrades for packages and it thinks that you should downgrade some other ones to fix dependencies.

---

### Post by brazzmonkey on 2007-05-03
i'm not trying to do anything special really. as stated before, i noticed this after a typo (i accidentally hit enter before typing the name of the program i was about to install), and i got the output i wrote in my first post. this scared me out a little bit, so i thought i would ask before further worrying.

now, running this autoremove command also gives me a bunch of unused programs, but i don't feel confident when it comes to uninstalling them.
```
$ sudo apt-get autoremove
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgtkhtml3.8-15 libtwolame0 libattr1-dev kdelibs4-dev libenchant1c2a ksim libmono-security1.0-cil kcharselect knewsticker-scripts kdessh libaspell-dev
  libtunepimp-bin kdemultimedia-dev libgksu1.2-1 libnss3 libaudiofile-dev libmono-sharpzip0.84-cil libglib2.0-dev python-gnome2-extras libgksuui1.0-1
  libmono-sqlite1.0-cil libgnome-media0 libmono-system-web1.0-cil libpcre3-dev kfloppy libgtksourceview1.0-0 liblualib50-dev kcalc libapr0 metacity-common
  libfinance-quote-perl libsasl2-dev libavahi-client-dev libogg-dev libjasper-1.701-dev khexedit libsvn0 kedit tango-icon-theme-common tango-icon-theme
  python-gtkhtml2 liblua50-dev lua50 librpcsecgss2 libavahi-qt3-dev libmono-sharpzip0.6-cil libacl1-dev libwv-1.2-1 tango-icon-theme-extras hspell libdbus-1-dev
  libxslt1-dev libhtml-tableextract-perl libssl-dev kdf libmono1.0-cil libgtksourceview-common libmono-data-tds1.0-cil libxml2-dev libtiff4-dev
  libmono-system-data1.0-cil libart-2.0-dev libesd0-dev libgtkhtml2-0 libnspr4 libmetacity0 libasound2-dev libtiffxx0c2 libmysqlclient14 libmyspell3c2
  libmono-system-runtime1.0-cil libtotem-plparser1 liblog4cxx9c2a libsynaptics0 libgtkspell0 libxml2-utils libartsc0-dev libopenexr-dev kdelirc superkaramba kjots
  libavahi-common-dev libnautilus-burn4 python-gnome2-desktop libclucene0 plib1.8.4c2 libgnome-desktop-2 kgpg libvorbis-dev gettext-kde libgdl-1-0 libidn11-dev
  libbz2-dev ktimer strigi-daemon libarts1-dev libnews-nntpclient-perl libgdl-1-common
The following packages will be REMOVED:
  gettext-kde hspell kcalc kcharselect kdelibs4-dev kdelirc kdemultimedia-dev kdessh kdf kedit kfloppy kgpg khexedit kjots knewsticker-scripts ksim ktimer
  libacl1-dev libapr0 libart-2.0-dev libarts1-dev libartsc0-dev libasound2-dev libaspell-dev libattr1-dev libaudiofile-dev libavahi-client-dev libavahi-common-dev
  libavahi-qt3-dev libbz2-dev libclucene0 libdbus-1-dev libenchant1c2a libesd0-dev libfinance-quote-perl libgdl-1-0 libgdl-1-common libgksu1.2-1 libgksuui1.0-1
  libglib2.0-dev libgnome-desktop-2 libgnome-media0 libgtkhtml2-0 libgtkhtml3.8-15 libgtksourceview-common libgtksourceview1.0-0 libgtkspell0
  libhtml-tableextract-perl libidn11-dev libjasper-1.701-dev liblog4cxx9c2a liblua50-dev liblualib50-dev libmetacity0 libmono-data-tds1.0-cil
  libmono-security1.0-cil libmono-sharpzip0.6-cil libmono-sharpzip0.84-cil libmono-sqlite1.0-cil libmono-system-data1.0-cil libmono-system-runtime1.0-cil
  libmono-system-web1.0-cil libmono1.0-cil libmyspell3c2 libmysqlclient14 libnautilus-burn4 libnews-nntpclient-perl libnspr4 libnss3 libogg-dev libopenexr-dev
  libpcre3-dev librpcsecgss2 libsasl2-dev libssl-dev libsvn0 libsynaptics0 libtiff4-dev libtiffxx0c2 libtotem-plparser1 libtunepimp-bin libtwolame0 libvorbis-dev
  libwv-1.2-1 libxml2-dev libxml2-utils libxslt1-dev lua50 metacity-common plib1.8.4c2 python-gnome2-desktop python-gnome2-extras python-gtkhtml2 strigi-daemon
  superkaramba tango-icon-theme tango-icon-theme-common tango-icon-theme-extras
0 upgraded, 0 newly installed, 98 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 110MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

```
or is it safe to remove all these ?

---

### Post by rsambuca on 2007-05-03
It looks to me like you removed a program at one point that is part of the kubuntu-desktop meta-package, and now it wants to remove everything else.  What happens when you```
sudo apt-get install kubuntu-desktop
```

---

### Post by jfinkels on 2007-05-03
> **rsambuca said:**
> It looks to me like you removed a program at one point that is part of the kubuntu-desktop meta-package, and now it wants to remove everything else.  What happens when you```
sudo apt-get install kubuntu-desktop
```

Yes, it does look like that. Do what he says.

---

### Post by brazzmonkey on 2007-05-04
i get :
```
$ sudo apt-get install kubuntu-desktop
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
kubuntu-desktop is already the newest version.
The following packages were automatically installed and are no longer required:
  libgtkhtml3.8-15 libtwolame0 libattr1-dev kdelibs4-dev libenchant1c2a ksim libmono-security1.0-cil kcharselect knewsticker-scripts kdessh debootstrap
  libaspell-dev libtunepimp-bin kdemultimedia-dev libgksu1.2-1 libnss3 libaudiofile-dev libmono-sharpzip0.84-cil libglib2.0-dev python-gnome2-extras libgksuui1.0-1
  libmono-sqlite1.0-cil libgnome-media0 libmono-system-web1.0-cil libpcre3-dev kfloppy libgtksourceview1.0-0 liblualib50-dev kcalc libapr0 metacity-common
  libfinance-quote-perl libsasl2-dev libavahi-client-dev libogg-dev libjasper-1.701-dev khexedit libsvn0 kedit tango-icon-theme-common tango-icon-theme
  python-gtkhtml2 liblua50-dev lua50 librpcsecgss2 libavahi-qt3-dev libmono-sharpzip0.6-cil libacl1-dev libwv-1.2-1 tango-icon-theme-extras hspell libdbus-1-dev
  libxslt1-dev libhtml-tableextract-perl libssl-dev kdf devscripts libmono1.0-cil libgtksourceview-common libmono-data-tds1.0-cil libxml2-dev libtiff4-dev
  libmono-system-data1.0-cil libart-2.0-dev libesd0-dev libgtkhtml2-0 libnspr4 libmetacity0 libasound2-dev libtiffxx0c2 libmysqlclient14 libmyspell3c2
  libmono-system-runtime1.0-cil libtotem-plparser1 liblog4cxx9c2a libsynaptics0 libgtkspell0 libxml2-utils pbuilder libartsc0-dev libopenexr-dev kdelirc
  superkaramba kjots libavahi-common-dev libnautilus-burn4 python-gnome2-desktop libclucene0 plib1.8.4c2 libgnome-desktop-2 kgpg libvorbis-dev gettext-kde
  libgdl-1-0 libidn11-dev libbz2-dev ktimer strigi-daemon libarts1-dev libnews-nntpclient-perl libgdl-1-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
kubuntu-desktop is already installed and functional, otherwise i suppose aptitude wouldn't propose to remove it (see first post). as far as i can remember, the only things i once uninstalled that were part of kubuntu metapackage are some foreign fonts which i will never use. but they have been reinstalled since.

---

### Post by jfinkels on 2007-05-04
> **brazzmonkey said:**
> i get :
```
$ sudo apt-get install kubuntu-desktop
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
kubuntu-desktop is already the newest version.
The following packages were automatically installed and are no longer required:
  libgtkhtml3.8-15 libtwolame0 libattr1-dev kdelibs4-dev libenchant1c2a ksim libmono-security1.0-cil kcharselect knewsticker-scripts kdessh debootstrap
  libaspell-dev libtunepimp-bin kdemultimedia-dev libgksu1.2-1 libnss3 libaudiofile-dev libmono-sharpzip0.84-cil libglib2.0-dev python-gnome2-extras libgksuui1.0-1
  libmono-sqlite1.0-cil libgnome-media0 libmono-system-web1.0-cil libpcre3-dev kfloppy libgtksourceview1.0-0 liblualib50-dev kcalc libapr0 metacity-common
  libfinance-quote-perl libsasl2-dev libavahi-client-dev libogg-dev libjasper-1.701-dev khexedit libsvn0 kedit tango-icon-theme-common tango-icon-theme
  python-gtkhtml2 liblua50-dev lua50 librpcsecgss2 libavahi-qt3-dev libmono-sharpzip0.6-cil libacl1-dev libwv-1.2-1 tango-icon-theme-extras hspell libdbus-1-dev
  libxslt1-dev libhtml-tableextract-perl libssl-dev kdf devscripts libmono1.0-cil libgtksourceview-common libmono-data-tds1.0-cil libxml2-dev libtiff4-dev
  libmono-system-data1.0-cil libart-2.0-dev libesd0-dev libgtkhtml2-0 libnspr4 libmetacity0 libasound2-dev libtiffxx0c2 libmysqlclient14 libmyspell3c2
  libmono-system-runtime1.0-cil libtotem-plparser1 liblog4cxx9c2a libsynaptics0 libgtkspell0 libxml2-utils pbuilder libartsc0-dev libopenexr-dev kdelirc
  superkaramba kjots libavahi-common-dev libnautilus-burn4 python-gnome2-desktop libclucene0 plib1.8.4c2 libgnome-desktop-2 kgpg libvorbis-dev gettext-kde
  libgdl-1-0 libidn11-dev libbz2-dev ktimer strigi-daemon libarts1-dev libnews-nntpclient-perl libgdl-1-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
kubuntu-desktop is already installed and functional, otherwise i suppose aptitude wouldn't propose to remove it (see first post). as far as i can remember, the only things i once uninstalled that were part of kubuntu metapackage are some foreign fonts which i will never use. but they have been reinstalled since.

I say go for it! If you need anything (ktimer? superkaramba? kdessh?) you can just reinstall them.

But then again, I'm crazy and don't care if I break my system.

---

### Post by rsambuca on 2007-05-04
To be honest, I am not sure what you were doing to have all of these extra packages hanging about, but I think I would also just do what it says and run the old "sudo apt-get autoremove"

---

### Post by brazzmonkey on 2007-05-04
aren't there any critical packages amongst those listed ?
surely enough there are packages which i do not use nor need (some kde stuff you mention for instance), but i'd like to be as sure as possible before i do something...

---

### Post by rsambuca on 2007-05-04
It looks to me like you should be fine.

In any event, if you lose the Kubuntu Desktop (which I don't think will happen), you can just run the following commands from the command line terminal.```
sudo apt-get update
sudo apt-get install kubuntu-desktop
sudo /etc/init.d/kdm restart
```

---

### Post by brazzmonkey on 2007-05-04
alright, i did it. everything seems fine so far, i just cross my fingers...
thanks for your psychological support rsambuca !

---

