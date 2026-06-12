---
title: "Pure KDE from Ubuntu gone awry"
date: 2007-03-20
forum: Installation &amp; Upgrades
---

### Post by MasterOfMuppets on 2007-03-20
I installed Ubuntu, and then Kubuntu on it using aptitude install kubuntu-desktop. I then removed Ubuntu using aysiu's guide [http://www.psychocats.net/ubuntu/purekde]("http://www.psychocats.net/ubuntu/purekde"), not doing aptitude uninstall (sadly) and now I have alot of weird problems like not being able to update things.

I got this:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

For no apparent reason.

---

### Post by Dr. Nick on 2007-03-20
you can only use aptitude to remove the program and all deps if you used it to install origionally.
 
Your problem seems that something is simply tying up the apt/dpkg process. First make sure adept is not running ( I assume your in KDE?) if its not then launch a console and type
 
sudo killalll apt-get
 
or open the process viewer and look for any running instance of apt,adept,dpkg

---

### Post by MasterOfMuppets on 2007-03-20
I manually killed the aptitude and apt-get tasks using sudo kill.
Now I get this:```

The following packages were automatically installed and are no longer required:
  kpdf libpopt-dev ksystemlog libsm-dev krdc krfb kscd kppp konversation
  krita-data libattr1-dev kubuntu-default-settings python2.4-dev kregexpeditor
  libice-dev ktip kdeprint cervisia libaspell-dev adept-manager knode
  kmplayer-konq-plugins kdesdk-kio-plugins ksvg kscreensaver libtasn1-3-dev
  kwin kaffeine-xine libnss3 libaudiofile-dev libaudio-dev
  libavahi-compat-libdnssd1 kio-locate libk3b2 libpythonize0 vorbis-tools
  libglib2.0-dev ncompress libgpg-error-dev ksnapshot liblockdev1
  libgnomeui-common kdebluetooth libkipi0 wlassistant libflac++5c2 kdebase
  x11proto-xinerama-dev comerr-dev openoffice.org-kde libmagick++9c2a
  libpcre3-dev adept-installer libkexif1 libopencdk8-dev
  kdegraphics-kfile-plugins x11proto-render-dev konqueror-nsplugins
  libgcrypt11-dev kpager gwenview libsmokeqt1 libpoppler1-qt libtdb1
  kapptemplate adept-updater liblualib50-dev kprof libqt4-qt3support kde-core
  latex-xft-fonts umbrello hwdb-client-kde krita libxi-dev qca-tls libapr0
  klipper libxmu-headers libxrender-dev kubuntu-artwork-usplash libqt4-core
  kontact libsqlite0 mesa-common-dev kdeadmin-kfile-plugins ksmserver
  subversion ksysguard adept-batch koffice-data libkrb5-dev qt3-dev-tools
  libsasl2-dev libavahi-client-dev libogg-dev libjasper-1.701-dev
  kde-icons-mono libcurl3-gnutls dcraw libpng12-dev libqt-perl kmenuedit
  pykdeextensions libfontconfig1-dev adept libpcrecpp0 ksplash-engine-moodin
  kubuntu-konqueror-shortcuts libsvn0 ksplash kaffeine p7zip skim korganizer
  kdesdk-kfile-plugins k3b kdenetwork-kfile-plugins kbstate akregator kio-apt
  kwin-style-crystal liblua50-dev libxcursor-dev arts python-qt4 ark firefox
  libexif-dev libgphoto2-2-dev kcron lua50 libjasper-runtime libavahi-qt3-dev
  adept-common libgmp3c2 libqt4-gui libacl1-dev qt3-designer libglu1-mesa-dev
  libgnutls-dev libqt3-mt-dev x11proto-randr-dev hspell libdbus-1-dev
  libxslt1-dev libssl-dev libxt-dev kdm libxmu-dev speedcrunch libjpeg62-dev
  libskim0 kpf kbugbuster bogofilter-bdb kdnssd kdemultimedia-kfile-plugins
  katapult poster kdenetwork-filesharing kubuntu-docs knotes bogofilter
  zlib1g-dev kcachegrind ocrad kde-guidance libxml2-dev libtiff4-dev
  libqt4-sql libfreetype6-dev flac debtags libart-2.0-dev libesd0-dev
  x11proto-fixes-dev libnspr4 libgsl0 khelpcenter apt-index-watcher
  libkpimexchange1 gtk2-engines-gtk-qt kmailcvt liblzo-dev rdiff-backup
  libqt3-headers libasound2-dev knetworkconf ksysguardd libtiffxx0c2
  libgl1-mesa-dev liblcms1-dev konq-plugins psutils libxrandr-dev
  kpersonalizer libkadm55 language-selector-qt poxml libexpat1-dev zoo qobex
  ktorrent kompare libmyspell3c2 scim-qtimm kwalletmanager imagemagick
  libxft-dev kopete kdelibs kunittest kappfinder python-elementtree kdbg
  libartsc0-dev libopenexr-dev kdesdk-misc karm kate libxfixes-dev keep
  koffice-libs libmng-dev adept-notifier bogofilter-common libavahi-common-dev
  libimlib2 kde-guidance-powermanager libjpeg-progs libxinerama-dev
  kdesdk-scripts libcupsys2-dev p7zip-full kde-systemsettings libvorbis-dev
  libmpcdec3 librsync1 kmousetool kitchensync gettext-kde kuiviewer kmag
  libidn11-dev kdepim-kresources kdepim-wizards kmilo kmplayer-base libbz2-dev
  kaudiocreator python-kde3 qt4-qtconfig libarts1-dev kdepasswd kmix kmtrace
  kbabel libungif4g

```
when I try to install something.
It seems the system doesn't understand it's not GNOME anymore...
How do I configure the system to make the KDE apps default?
Are there any configuration files to change/delete?

---

### Post by Dr. Nick on 2007-03-20
That problem I have no idea about, never seen something like that before.
 
Does it do that same thing if you type
 
sudo aptitude install kubuntu-desktop ?

---

### Post by zvacet on 2007-03-20
[http://www.psychocats.net/ubuntu/kde]("http://www.psychocats.net/ubuntu/kde")

---

### Post by MasterOfMuppets on 2007-03-21
I used that guide to INSTALL ubuntu, now I have Kubuntu installed and Ubuntu un-installed.

I'll try aptitude install kubuntu-desktop again, although that's the way I originally installed kubuntu.

---

### Post by Dr. Nick on 2007-03-21
the reason i suggested aptitude install kubuntu-desktop was that it appears its trying to remove it when you do anything, thought maybe reinstalling it would make it not mark them as  un-needed, not sure that will work, just a idea

---

### Post by MasterOfMuppets on 2007-03-22
Seems to have worked, should have thought of that... I'll keep u guys posted on this!
Thanks nick!

---

### Post by MasterOfMuppets on 2007-03-30
I've reached the conclusion it has something to do with me removing gwenview. Is it possible that by removing a component of kubuntu-desktop I've cause a situation where the package manager doesn't recognize kubuntu-desktop as being installed?

---

### Post by zvacet on 2007-03-31
I never been in that situation but it sounds logicaly if kubuntu desktop is incomplete it is not recognized as installed.

---

### Post by louieb on 2007-03-31
> **MasterOfMuppets said:**
> I manually killed the aptitude and apt-get tasks using sudo kill.
Now I get this:```

The following packages were automatically installed and are no longer required:  
```
when I try to install something.
It seems the system doesn't understand it's not GNOME anymore...
How do I configure the system to make the KDE apps default?
Are there any configuration files to change/delete?
Its a bug. I've been bitten by it also, apt-get and aptitude don't always play nice together. Don't have the link but saw the bug report on the Debian website.

---

