---
title: "Fishy upgrade"
date: 2012-09-20
forum: Installation &amp; Upgrades
---

### Post by dargaud on 2012-09-20
Hello all,
for the last few days, on several of my systems, I have the following upgrade ready but it looks fishy to me. Those are x64 systems, so why does it want to install all those i386 packages ? Is there something wrong or should I go ahead ?
```
$ sudo aptitude full-upgrade 
The following NEW packages will be installed:
  linux-headers-3.2.0-30{a} linux-headers-3.2.0-30-generic{a} linux-image-3.2.0-30-generic 
The following packages will be upgraded:
  akregator amor apport apport-kde ark bind9-host build-essential dhcp3-client dhcp3-common dnsutils dolphin dragonplayer firefox 
  firefox-branding firefox-globalmenu firefox-locale-en firefox-locale-fr firefox-locale-it freespacenotifier gimp gimp-data 
[...]
  python-netcdf python-problem-report python-scientific resolvconf system-config-printer-kde systemsettings tasks-icons 
  xserver-xorg-input-synaptics 
287 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.                                                                    
Need to get 560 MB of archives. After unpacking 220 MB will be used.                                                                         
The following packages have unmet dependencies:                                                                                              
 libkexiv2-data : Breaks: libkexiv2-8 but 4:4.5.5-0ubuntu2 is installed.                                                                     
 libkipi-data : Breaks: libkipi7 but 4:4.5.5-0ubuntu2 is installed.                                                                          
 libkdcraw-data : Breaks: libkdcraw8 but 4:4.5.5-0ubuntu2 is installed.                                                                      
open: 130; closed: 446; defer: 100; conflict: 352                                                                                           .Internal error: the solver Install(qdbus:amd64 4:4.8.1-0ubuntu4.2 <libqt4-dbus:i386 4:4.8.1-0ubuntu4.2 -S> {qdbus:amd64 4:4.8.1-0ubuntu4.2 qdbus:i386 4:4.8.1-0ubuntu4.2}>) of a supposedly unresolved dependency is already installed in step 578                                        
The following actions will resolve these dependencies:                                                                                       
                                                                                                                                             
       Remove the following packages:                                                                                                        
1)       bluez-alsa:i386                                                                                                                     
2)       glib-networking:i386                                                                                                                
3)       googleearth                                                                                                                         
4)       gstreamer0.10-plugins-base:i386                                                                                                     
5)       gstreamer0.10-plugins-good:i386                                                                                                     
6)       gstreamer0.10-x:i386                                                                                                                
7)       gtk2-engines:i386                                                                                                                   
[...]
247)     xaw3dg:i386                                                             
248)     zlib1g:i386                                                             

       Leave the following dependencies unresolved:                              
249)     libcanberra-gtk0:i386 recommends libcanberra-gtk-module:i386            
250)     libncurses5:i386 recommends libgpm2:i386                                
251)     libncursesw5:i386 recommends libgpm2:i386                               
252)     libslang2:i386 recommends libpng12-0:i386                               
253)     libqt4-dbus recommends qdbus (= 4:4.8.1-0ubuntu4.2)                     
254)     plasma-desktop recommends kde-workspace                                 
255)     plasma-netbook recommends kde-workspace                                 
256)     kscreensaver-xsavers recommends kscreensaver (= 4:4.8.5-0ubuntu0.1)     
257)     libgl1-mesa-glx:i386 recommends libgl1-mesa-dri:i386 (>= 7.2)           
258)     libgphoto2-2:i386 recommends udev:i386 (>= 0.175)                       
259)     libgphoto2-2:i386 recommends libgphoto2-l10n:i386 (>= 2.4.13-1ubuntu1.2)
260)     libqtgui4:i386 recommends libcups2:i386                                 
261)     ia32-libs-multiarch:i386 recommends libgl1-mesa-glx:i386                
262)     ia32-libs-multiarch:i386 recommends libgl1-mesa-dri:i386                
263)     skype-bin:i386 recommends sni-qt:i386                                   
264)     skype-bin:i386 recommends libasound2-plugins:i386                       

```

---

### Post by dargaud on 2012-09-23
Bump.
I want an answer to that question before I press [Y].

---

### Post by jerrrys on 2012-09-23
Whats **sudo apt-get dist-upgrade** got to say?

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by oldfred on 2012-09-23
I went thru some of the same issue. I manually uninstalled all the i386 related packages and my wine stopped working. When I reinstalled wine it reinstalled all the i386 packages. There may be other applications also that need them.

I thought I had installed all the i386 packages as I use the dpkg to list all apps in an old install and reinstall in my new install. I assumed incorrectly that they were not needed.

---

### Post by dargaud on 2012-09-24
```
$ sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  libkdcraw8 libkexiv2-8 libkipi7
The following NEW packages will be installed:
  linux-headers-3.2.0-31 linux-headers-3.2.0-31-generic linux-image-3.2.0-31-generic
The following packages will be upgraded:
  akregator amor apport apport-kde ark bind9-host build-essential dbus dbus-x11 dhcp3-client dhcp3-common dnsutils dolphin dragonplayer
  firefox firefox-branding firefox-globalmenu firefox-locale-en firefox-locale-fr firefox-locale-it freespacenotifier ghostscript
  ghostscript-cups ghostscript-x gimp gimp-data glib-networking glib-networking:i386 glib-networking-common glib-networking-services gnupg
  gnupg-agent gnupg-curl gnupg2 gpgsm gpgv gwenview icedtea-6-jre-cacao icedtea-6-jre-jamvm isc-dhcp-client isc-dhcp-common juk
  kaddressbook kalarm kamera kate kate-data katepart kde-baseapps-bin kde-baseapps-data kde-config-cddb kde-l10n-engb kde-l10n-fr
  kde-l10n-it kde-runtime kde-runtime-data kde-style-oxygen kde-window-manager kde-window-manager-common kde-workspace kde-workspace-bin
  kde-workspace-data kde-workspace-kgreet-plugins kde-zeroconf kdebase-bin kdebase-runtime kdebase-workspace kdegames-card-data
  kdegames-card-data-extra kdegraphics kdegraphics-libs-data kdegraphics-mobipocket kdelibs-bin kdelibs5 kdelibs5-data kdelibs5-dbg
  kdelibs5-plugins kdemultimedia kdemultimedia-kio-plugins kdenetwork-filesharing kdepasswd kdepim-dbg kdepim-kresources kdepim-runtime
  kdepim-strigi-plugins kdepimlibs-dbg kdepimlibs-kio-plugins kdepimlibs5 kdetoys kdm kdoctools kfind kgamma kget khelpcenter4 kinfocenter
  klipper kmail kmenuedit kmix knode knotes kompare konqueror konqueror-nsplugins konsole kontact kopete korganizer kpat kppp kscd
  kscreensaver kscreensaver-xsavers ksysguard ksysguardd ksystemlog kteatime ktux libakonadi-calendar4 libakonadi-contact4 libakonadi-kabc4
  libakonadi-kcal4 libakonadi-kde4 libakonadi-kmime4 libakonadi-notes4 libapache2-mod-php5 libart-2.0-2 libbind9-80 libcalendarsupport4
  libdbus-1-3 libdbus-1-3:i386 libdbus-1-dev libdns81 libeventviews4 libgimp2.0 libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra
  libgpgme++2 libgs9 libgs9-common libincidenceeditorsng4 libisc83 libisccc80 libisccfg82 libkabc4 libkactivities-bin libkactivities6
  libkalarmcal2 libkateinterfaces4 libkatepartinterfaces4 libkblog4 libkcal4 libkcalcore4 libkcalutils4 libkcddb4 libkcmutils4
  libkdcraw-data libkdcraw20 libkde3support4 libkdeclarative5 libkdecorations4 libkdecore5 libkdegames5a libkdepim4
  libkdepimdbusinterfaces4 libkdesu5 libkdeui5 libkdewebkit5 libkdgantt2 libkdnssd4 libkemoticons4 libkephal4abi1 libkexiv2-10
  libkexiv2-data libkfile4 libkholidays4 libkhtml5 libkidletime4 libkimap4 libkimproxy4 libkio5 libkipi-data libkipi8 libkjsapi4
  libkjsembed4 libkldap4 libkleo4 libkmanagesieve4 libkmbox4 libkmediaplayer4 libkmime4 libknewstuff2-4 libknewstuff3-4 libknotifyconfig4
  libkntlm4 libkonq-common libkonq5-templates libkonq5abi1 libkonqsidebarplugin4a libkontactinterface4 libkopete4 libkparts4 libkpgp4
  libkpimidentities4 libkpimtextedit4 libkpimutils4 libkprintutils4 libkpty4 libkresources4 libkrosscore4 libkrossui4 libksane-data
  libksane0 libkscreensaver5 libksgrd4 libksieve4 libksieveui4 libksignalplotter4 libktexteditor4 libktnef4 libkunitconversion4 libkutils4
  libkwineffects1abi3 libkwinglutils1 libkwinnvidiahack4 libkworkspace4abi1 libkxmlrpcclient4 liblwres80 libmailcommon4 libmailtransport4
  libmarblewidget13 libmessagecomposer4 libmessagecore4 libmessagelist4 libmessageviewer4 libmicroblog4 libnepomuk4
  libnepomukdatamanagement4 libnepomukquery4a libnepomuksync4 libnepomukutils4 libokularcore1abi1 libplasma-geolocation-interface4
  libplasma3 libplasmaclock4abi3 libplasmagenericshell4 libprocesscore4abi1 libprocessui4a libqgpgme1 libsolid4 libsolidcontrol4abi2
  libsolidcontrolifaces4abi2 libsyndication4 libtaskmanager4abi3 libtemplateparser4 libthreadweaver4 libweather-ion6 linux-firmware
  linux-generic linux-headers-generic linux-image-generic linux-libc-dev linux-source linux-source-3.2.0 marble marble-data marble-plugins
  okular okular-extra-backends openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib php5 php5-cli php5-common php5-gd php5-mysql
  plasma-dataengines-addons plasma-dataengines-workspace plasma-desktop plasma-netbook plasma-scriptengine-javascript
  plasma-scriptengine-python plasma-widget-folderview plasma-widget-kimpanel plasma-widgets-addons plasma-widgets-workspace
  policykit-1-gnome postfix python-apport python-netcdf python-problem-report python-scientific resolvconf system-config-printer-kde
  systemsettings tasks-icons tzdata tzdata-java xserver-xorg-input-synaptics
302 upgraded, 3 newly installed, 3 to remove and 0 not upgraded.
Need to get 568 MB of archives.
After this operation, 219 MB of additional disk space will be used.

```

I don't use Wine, but how do I find out which package(s) causes all those i386 packages to be installed ?

---

### Post by jerrrys on 2012-09-24
Maybe your just looking at the [ia32-libs]("http://packages.ubuntu.com/precise-updates/ia32-libs-multiarch") upgrades

---

### Post by grahammechanical on 2012-09-24
Ubuntu contains certain i386 libraries so that applications coded for a 32bit (i386) operating system will work even on a 64bit OS. This is my understanding.

During the development of 12.04 there was a serious attempt to replace those libraries with what is called multi-arch libraries. In other words Libraries that can be used on the 32bit Ubuntu as well as the 64bit Ubuntu and maybe even on non-intel architectures.

How much of this change Kubuntu picked up I cannot say.

Regards.

---

### Post by dargaud on 2012-10-01
Well, it appears the problem has simply gone away. If I initiate an upgrade, it doesn't mention i386 anymore... That's weird.

---

