---
title: "Ubuntu 14.04,  software updater hangs, then says &quot;not all updates can be installed&quot;"
date: 2016-04-09
forum: Installation &amp; Upgrades
---

### Post by richterbg on 2016-04-09
Software updater downloads the information, then turns dark for a while, and after some time says "not all updates can be installed". 

Someone somewhere suggested to run:
> sudo apt-get install -f

The output is:
```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded. 
```   

Now, if I try to run:
> sudo apt-get dist-upgrade 


Then things start to look kinda ugly:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  avidemux-common bluefish-data bluefish-plugins bluegriffon-data
  deluge-common deluge-gtk filezilla-common fonts-horai-umefont fonts-mathjax
  gambas3-gb-gtk gambas3-gb-image gambas3-gb-settings gambas3-runtime
  gnome-exe-thumbnailer lame libaften0 libao-common libao4
  libasn1-8-heimdal:i386 libaudio2:i386 libcapi20-3 libcapi20-3:i386 libchm1
  libdrm-intel1:i386 libdrm-nouveau2:i386 libdrm-radeon1:i386 libelf1:i386
  libevdev2 libexif12:i386 libfaac0 libgd3:i386 libgif4:i386
  libgl1-mesa-glx:i386 libglapi-mesa:i386 libgphoto2-6:i386
  libgphoto2-port10:i386 libgsl0ldbl libgssapi3-heimdal:i386
  libgstreamer-plugins-base0.10-0:i386 libgstreamer-plugins-base1.0-0:i386
  libgstreamer0.10-0:i386 libgstreamer1.0-0:i386 libhcrypto4-heimdal:i386
  libheimbase1-heimdal:i386 libheimntlm0-heimdal:i386 libhttrack2
  libhx509-5-heimdal:i386 libieee1284-3:i386 libjs-jquery libjs-mathjax
  libjs-sphinxdoc libjs-underscore libkrb5-26-heimdal:i386 liblavfile-2.1-0
  liblavjpeg-2.1-0 liblavplay-2.1-0 liblcms2-2:i386 libldap-2.4-2:i386
  libltdl7:i386 libmikmod2 libmjpegutils-2.1-0 libmpg123-0:i386
  libmysqlclient18:i386 libodbc1 libopenal1:i386 liborc-0.4-0:i386
  libp11-kit-gnome-keyring:i386 libpciaccess0:i386 libportmidi0 libquicktime2
  libroken18-heimdal:i386 libsane:i386 libsasl2-2:i386 libsasl2-modules:i386
  libsasl2-modules-db:i386 libsdl-ttf2.0-0 libsmltk0 libsmpeg0 libsoil1
  libsqlite3-0:i386 libssl1.0.0:i386 libtidy-0.99-0 libunwind8
  libusb-1.0-0:i386 libv4l-0:i386 libv4lconvert0:i386 libvpx1:i386
  libwind0-heimdal:i386 libx11-xcb1:i386 libxcb-dri2-0:i386 libxcb-dri3-0:i386
  libxcb-glx0:i386 libxcb-present0:i386 libxcb-sync1:i386 libxml2:i386
  libxpm4:i386 libxshmfence1:i386 libxslt1.1:i386 libxss1:i386 libxt6:i386
  libxv1:i386 libxxf86vm1:i386 linux-headers-3.13.0-79
  linux-headers-3.13.0-79-generic linux-headers-3.13.0-83
  linux-headers-3.13.0-83-generic ocl-icd-libopencl1:i386 p11-kit-modules:i386
  perlmagick pidgin-data python-apsw python-beautifulsoup python-cherrypy3
  python-cssselect python-cssutils python-dateutil python-feedparser
  python-markdown python-mechanize python-netifaces python-pygments
  python-pyparsing python-repoze.lru python-routes python-utidylib
  python-webob qtdeclarative5-ubuntu-settings-components-assets twolame
  unixodbc webhttrack-common wine-gecko2.21 wine-gecko2.21:i386 wine-mono0.0.8
  xchat-common
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  account-plugin-aim account-plugin-facebook account-plugin-flickr
  account-plugin-google account-plugin-jabber account-plugin-salut
  account-plugin-twitter account-plugin-windows-live account-plugin-yahoo
  activity-log-manager activity-log-manager-control-center appmenu-qt
  appmenu-qt5 apport apport-gtk apt-transport-https apt-utils apt-xapian-index
  aptdaemon apturl apturl-common avidemux avidemux-plugins-common
  avidemux-plugins-gtk bbswitch-dkms bluefish bluegriffon brltty
  build-essential ca-certificates-java calibre calibre-bin checkbox-gui cheese
  click click-apparmor command-not-found compiz compiz-core compiz-gnome
  compiz-plugins compiz-plugins-default compizconfig-settings-manager cups
  cups-core-drivers cups-filters cups-filters-core-drivers cups-ppdc
  default-jre default-jre-headless deluge dkms dolphin-emu empathy enchant eog
  evince filezilla firefox flashplugin-installer friends-facebook
  friends-twitter g++ g++-4.8 gambas3-gb-form gambas3-gb-gui gambas3-gb-qt4
  gcc gcc-4.8 gdisk gedit gettext gimp gimp-help-en gir1.2-rb-3.0
  gir1.2-totem-1.0 gir1.2-webkit-3.0 gnome-contacts gnome-control-center
  gnome-media gnome-session-flashback gnome-system-monitor gnome-user-guide
  gnome-video-effects google-chrome-stable gparted groff-base
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-good
  gstreamer0.10-plugins-ugly gstreamer1.0-clutter gstreamer1.0-plugins-bad
  gstreamer1.0-plugins-bad-faad gstreamer1.0-plugins-bad-videoparsers
  gstreamer1.0-plugins-good gstreamer1.0-plugins-ugly hud ibus-pinyin
  icedtea-7-jre-jamvm indicator-bluetooth indicator-datetime inkscape
  intltool-debian kismet kismet-plugins landscape-client-ui-install
  language-selector-common language-selector-gnome libaccount-plugin-1.0-0
  libaccount-plugin-generic-oauth libaccount-plugin-google libaccounts-qt5-1
  libapt-inst1.5 libapt-pkg-perl libasan0 libasound2-plugins:i386
  libatk-wrapper-java libatk-wrapper-java-jni libatkmm-1.6-1 libatomic1
  libavidemux0 libbasicusageenvironment0 libboost-date-time1.54.0
  libboost-iostreams1.54.0 libboost-program-options1.54.0
  libboost-python1.54.0 libboost-serialization1.54.0 libboost-system1.54.0
  libcairomm-1.0-1 libcapnp-0.4.0 libcdr-0.0-0 libcheese-gtk23 libcheese7
  libcholmod2.1.2 libchromaprint0 libclucene-contribs1 libclucene-core1
  libclutter-1.0-0 libclutter-gst-2.0-0 libclutter-gtk-1.0-0 libcmis-0.4-4
  libcogl-pango15 libcogl15 libcolumbus1 libcompizconfig0 libcontent-hub0
  libcupsppdc1 libcurl4-gnutls-dev libdbus-cpp2 libdbusmenu-qt2
  libdbusmenu-qt2:i386 libdbusmenu-qt5 libde265 libdirac-encoder0
  libdjvulibre21 libebml4 libegl1-mesa-drivers libenchant1c2a libept1.4.12
  libespeak1 libevdocument3-4 libevview3-3 libexempi3 libexiv2-12
  libfarstream-0.1-0 libfarstream-0.2-2 libfluidsynth1 libframe6
  libgcc-4.8-dev libgdbussyncevo0 libgegl-0.2-0 libgeis1 libgexiv2-2
  libgflags2 libgfortran3 libgl1-mesa-dri:i386 libglibmm-2.4-1c2a libglu1-mesa
  libglu1-mesa:i386 libgme0 libgnutls-dev libgnutlsxx27 libgoa-backend-1.0-1
  libgoogle-glog0 libgrail6 libgrip0 libgroupsock1
  libgstreamer-plugins-bad1.0-0 libgtkglext1 libgtkmm-2.4-1c2a libgtkmm-3.0-1
  libgtkspell0 libharfbuzz-icu0 libhunspell-1.3-0 libilmbase6 libitm1
  libjack-jackd2-0:i386 libjavascriptcoregtk-1.0-0 libjavascriptcoregtk-3.0-0
  liblapack3 liblivemedia23 libllvm3.4:i386 libmagick++5 libmagickcore5-extra
  libmatroska6 libmirclient7 libmirclientplatform-mesa libmirplatform
  libmirplatformgraphics-mesa libmirprotobuf0 libmirserver18
  libmpeg2encpp-2.1-0 libmplex2-2.1-0 libmspub-0.0-0 libmythes-1.2-0
  libnux-4.0-0 libofa0 libopencv-calib3d2.4 libopencv-contrib2.4
  libopencv-core2.4 libopencv-features2d2.4 libopencv-flann2.4
  libopencv-highgui2.4 libopencv-imgproc2.4 libopencv-legacy2.4
  libopencv-ml2.4 libopencv-objdetect2.4 libopencv-video2.4 libopenexr6
  liborcus-0.6-0 libosmesa6 libosmesa6:i386 liboxideqt-qmlplugin
  liboxideqtcore0 liboxideqtquick0 libpangomm-1.4-1 libpcrecpp0 libpodofo0.9.0
  libportaudio2 libprocess-cpp1 libprotobuf8 libproxy-tools
  libproxy1-plugin-gsettings libproxy1-plugin-networkmanager libpurple0
  libpyzy-1.0-0 libqdjango-db0 libqgsttools-p1 libqpdf13 libqt4-dbus
  libqt4-dbus:i386 libqt4-declarative libqt4-declarative:i386 libqt4-designer
  libqt4-help libqt4-network libqt4-network:i386 libqt4-opengl
  libqt4-opengl:i386 libqt4-qt3support libqt4-script libqt4-script:i386
  libqt4-scripttools libqt4-sql libqt4-sql:i386 libqt4-sql-mysql:i386
  libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml libqt4-xml:i386
  libqt4-xmlpatterns libqt4-xmlpatterns:i386 libqt5feedback5 libqt5multimedia5
  libqt5multimedia5-plugins libqt5multimediaquick-p5 libqt5multimediawidgets5
  libqt5opengl5 libqt5organizer5 libqt5positioning5 libqt5printsupport5
  libqt5qml-graphicaleffects libqt5sensors5 libqt5sql5 libqt5sql5-sqlite
  libqt5svg5 libqt5systeminfo5 libqt5test5 libqt5webkit5
  libqt5webkit5-qmlwebkitplugin libqt5widgets5 libqt5xml5 libqt5xmlpatterns5
  libqtassistantclient4 libqtcore4 libqtcore4:i386 libqtdbus4 libqtdbus4:i386
  libqtgui4 libqtgui4:i386 libqtwebkit4 libqtwebkit4:i386 libquadmath0
  librarian0 libraw9 libreoffice-avmedia-backend-gstreamer
  libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core
  libreoffice-draw libreoffice-gnome libreoffice-gtk libreoffice-help-en-us
  libreoffice-impress libreoffice-math libreoffice-ogltrans
  libreoffice-pdfimport libreoffice-presentation-minimizer libreoffice-writer
  libresid-builder0c2a librhythmbox-core8 librtmp-dev libsdl-mixer1.2 libsexy2
  libsfml-network2 libsfml-system2 libsidplay1 libsidplay2 libsigc++-2.0-0c2a
  libsignon-extension1 libsignon-plugins-common1 libsoundtouch0
  libstdc++-4.8-dev libstdc++6:i386 libsyncevolution0 libsynthesis0
  libtag1-vanilla libtag1c2a libtbb2 libtelepathy-farstream3 libthumbnailer0
  libtinyxml2.6.2 libtorrent-rasterbar7 libtotem0 libtracker-extract-0.16-0
  libtsan0 libtxc-dxtn-s2tc0:i386 libubuntu-application-api-mirserver1
  libubuntu-download-manager-priv0 libubuntu-location-service0
  libubuntu-platform-hardware-api1 libumfpack5.6.2 libunity-action-qt1
  libunity-core-6.0-9 libunity-mir1 libunity-scopes1 libunity-webapps0
  libunityvoice1 libusermetricsoutput1 libvisio-0.0-0 libvisual-0.4-plugins
  libvlc5 libvlccore7 libwayland-egl1-mesa libwebkitgtk-1.0-0
  libwebkitgtk-3.0-0 libwpd-0.9-9 libwpg-0.2-2 libwps-0.2-2 libwxbase2.8-0
  libwxgtk-media2.8-0 libwxgtk2.8-0 libxapian22 libxatracker2 libyelp0 libzmq3
  libzmqpp3 lintian lshw man-db mcp-account-manager-uoa mediascanner2.0
  metacity mjpegtools mjpegtools-gtk mythes-en-us nautilus nautilus-sendto
  nautilus-sendto-empathy nautilus-share nvidia-331 nvidia-340 nvidia-prime
  onboard onboard-data oneconf oneconf-common openjdk-7-jre
  openjdk-7-jre-headless opera-beta opera-developer opera-stable p7zip pidgin
  pidgin-libnotify printer-driver-gutenprint printer-driver-pxljr python-apt
  python-aptdaemon python-aptdaemon.gtk3widgets python-commandnotfound
  python-compizconfig python-libtorrent python-numpy python-oneconf
  python-pygame python-qt4 python-qt4-dbus python-wxgtk2.8 python-xapian
  python3-apport python3-apt python3-aptdaemon python3-aptdaemon.gtk3widgets
  python3-aptdaemon.pkcompat python3-click python3-commandnotfound
  python3-distupgrade python3-oneconf python3-software-properties python3-uno
  python3-update-manager qdbus qpdf qt-at-spi qtchooser
  qtdeclarative5-accounts-plugin qtdeclarative5-dialogs-plugin
  qtdeclarative5-localstorage-plugin qtdeclarative5-privatewidgets-plugin
  qtdeclarative5-qtfeedback-plugin qtdeclarative5-qtmultimedia-plugin
  qtdeclarative5-qtquick2-plugin qtdeclarative5-systeminfo-plugin
  qtdeclarative5-ubuntu-content0.1 qtdeclarative5-ubuntu-settings-components
  qtdeclarative5-ubuntu-thumbnailer0.1
  qtdeclarative5-ubuntu-ui-extras-browser-plugin
  qtdeclarative5-ubuntu-ui-toolkit-plugin qtdeclarative5-unity-action-plugin
  qtdeclarative5-window-plugin qtdeclarative5-xmllistmodel-plugin
  rarian-compat rhythmbox rhythmbox-mozilla rhythmbox-plugin-cdrecorder
  rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist rhythmbox-plugins
  sessioninstaller shotwell signon-keyring-extension signon-plugin-oauth2
  signon-plugin-password signon-ui signond skype:i386 sni-qt sni-qt:i386
  software-center software-properties-common software-properties-gtk
  speech-dispatcher synaptic syncevolution syncevolution-common
  syncevolution-libs syncevolution-libs-gnome system-config-printer-gnome
  system-image-common system-image-dbus telepathy-haze thumbnailer-service
  thunderbird thunderbird-gnome-support thunderbird-locale-en
  thunderbird-locale-en-us toshset totem totem-mozilla totem-plugins tracker
  tracker-extract tracker-miner-fs tracker-utils ttf-mscorefonts-installer
  ubuntu-desktop ubuntu-docs ubuntu-download-manager ubuntu-drivers-common
  ubuntu-keyboard-data ubuntu-minimal ubuntu-release-upgrader-core
  ubuntu-release-upgrader-gtk ubuntu-sso-client-qt ubuntu-standard
  ubuntu-system-service ubuntu-tweak unattended-upgrades unity
  unity-control-center unity-control-center-signon unity-lens-applications
  unity-plugin-scopes unity-scope-gdrive unity-scope-manpages
  unity-scope-scopes unity-tweak-tool unity-voice-service unity-webapps-common
  unity-webapps-qml unity-webapps-service uno-libs3 unrar update-manager
  update-manager-core update-notifier update-notifier-common
  upstart-app-launch upstart-app-launch-tools ure usermetricsservice
  virtualbox-4.3 vlc vlc-nox vlc-plugin-libde265 vlc-plugin-notify
  vlc-plugin-pulse webaccounts-extension-common webapp-container
  webbrowser-app webhttrack wine1.6 wine1.6-amd64 wine1.6-i386:i386 winetricks
  xaralx xaralx-svg xchat xchat-indicator xdiagnose xorg
  xserver-xorg-video-all xserver-xorg-video-ati xserver-xorg-video-glamoregl
  xserver-xorg-video-vmware xul-ext-unity xul-ext-webaccounts
  xul-ext-websites-integration yelp yumi zeitgeist zeitgeist-core
  zeitgeist-datahub zenity
The following NEW packages will be installed:
  foomatic-filters
The following packages have been kept back:
  gcc-4.9-base gcc-4.9-base:i386 lib32gcc1 libgcc1 libgcc1:i386
0 upgraded, 1 newly installed, 567 to remove and 5 not upgraded.
Need to get 98,6 kB of archives.
After this operation, 3425 MB disk space will be freed.
Do you want to continue? [Y/n] n
Abort.



```

This definitely doesn't look OK. Any ideas how to fix it?

Thank you.

---

### Post by grahammechanical on 2016-04-09
That is one reason for not using dist-upgrade. It brings in packages that have been held back for some reason. And unlike apt-get upgrade it will use what is called "smart conflict resolution" to resolve package conflicts. I put "smart" in inverted commas because the so-called smart conflict resolution is to remove packages. I had one occasion where it removed Ubuntu desktop and broke the OS. I would not use dist-upgrade on a production install. I do use it on the development version that I run. I am willing to accept breakage on a development version installation.

It is safe to run apt-get autoremove. I have just run it on 16.04 & it removed all the old kernels except 2. As for the original message about not being able to install all updates. Were you given a reason. The reasons given when I get that message are,

This can be can be caused by:

1) A previous upgrade which did not complete
2) Problems with some installed software
3) Unofficial software packages not provided by Ubuntu
4) Normal changes of a pre-release version of Ubuntu

In my case it is #4. I am running the pre-release version of 16.04. I normally click Continue and the usual update/upgrade proceeds. If you accept the offer of a Partial upgrade then it most likely remove all those packages that dist-upgrade was going to remove.

A lot will depend on why you are getting that message.

Regards.

---

### Post by richterbg on 2016-04-09
Thank you very much for taking the time to post a reply to my question. 

It does return the very same reasons that you've pasted. However, it does take about 5-10 minutes to display the message. During this time the process bar stays grayed. 

If I click continue, then standard user programs do get updated (firefox, thunderbird, etc.). However kernel upgrades do not get processed. 

I'm afraid that I don't know how to troubleshoot this...

---

### Post by kansasnoob on 2016-04-09
It's clearly not going to be OK to remove everything it wants to remove :o

I wonder about this:

> [B][COLOR="#FF0000"]The following NEW packages will be installed:
  foomatic-filters[/COLOR][/B]
The following packages have been kept back:
  gcc-4.9-base gcc-4.9-base:i386 lib32gcc1 libgcc1 libgcc1:i386

Had you recently been trying to set up a new printer?

Not sure why gcc updates would be held back. I just checked mine and the most recent updates were last September.

What was the last thing you attempted to do before things got messed up?

---

### Post by grahammechanical on 2016-04-09
You are not running a pre-release version of Ubuntu. So, you can discount reason #4 but what about the other 3 reasons? What about, Unofficial software packages not provided by Ubuntu?

Have you installed any PPAs (Personal Package Archives). PPAs can be useful for installing software but it is sometimes best to disable the PPA afterwards and then the package manager will not try to access the PPA every time it tries to update the OS. System Settings>Software & Updates>Other Software tab. Untick any PPAs.

Are there any other software repositories (software sources) that you have added. What do you get when you run?

```
sudo apt-get update
```

Any errors regarding connections to URLs could be an interesting bit of information.

Have you run sudo apt-get autoremove? That command will only remove those packages first listed as no longer required. It will not remove those packages listed afterwards. It is dist-upgrade that will remove the packages listed afterwards to avoid conflict with something that dist-upgrade is upgrading.

Regards.

---

### Post by richterbg on 2016-04-10
I run an ancient Brother HL-2030 printer, which was operating without any issues. At some point it did stop. The [http://127.0.0.1:631](http://127.0.0.1:631) address was not running for some reason. I did install something from the Ubuntu software center, which enabled it, but I really do not remember what was it. 

The problem did start about 2-3 months ago. I did receive one such partial upgrade possible message. I believe I clicked "Continue" and it installed a bunch of stuff. Don't know if Ubuntu holds logs for such past events. 

When the "software updated" started to show such behavior, I did read that I can manually use "**sudo apt update**" and "**sudo apt upgrad**e" (not apt-get) to perform updates. It does seem to work, but it turned out that the kernel doesn't get updated. "apt" seems to download the kernel and install it. However, after I ran "**uname -r**" yesterday, I saw that the current kernel is:

 3.13.0-74-generic

while apt did download 3.13.0-85-generic yesterday. That's why I started this thread. 

I also tried to update grub with "**sudo update-grub2**", but a new kernel would not show...

The output of "sudo apt-get update" does not show any particular errors:

```
Hit http://deb.opera.com stable InReleaseHit http://ppa.launchpad.net trusty InRelease                                  
Hit http://deb.opera.com stable InRelease                                      
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://deb.opera.com stable InRelease                                      
Hit http://ppa.launchpad.net trusty InRelease                                  
Hit http://deb.opera.com stable InRelease                                      
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://deb.opera.com stable/non-free amd64 Packages                        
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://deb.opera.com stable/non-free i386 Packages                         
Ign http://archive.ubuntu.com trusty InRelease                                 
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:1 http://archive.getdeb.net trusty-getdeb InRelease [8143 B]               
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Get:2 http://extras.ubuntu.com trusty Release.gpg [72 B]                       
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://deb.opera.com stable/non-free amd64 Packages                        
Get:3 http://archive.ubuntu.com trusty-updates InRelease [65,9 kB]             
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://deb.opera.com stable/non-free i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://extras.ubuntu.com trusty Release                                    
Get:4 http://archive.getdeb.net trusty-getdeb/apps amd64 Packages [72,0 kB]    
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://deb.opera.com stable/non-free amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://deb.opera.com stable/non-free i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://deb.opera.com stable/non-free amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://deb.opera.com stable/non-free i386 Packages                         
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:5 http://archive.getdeb.net trusty-getdeb/apps i386 Packages [72,7 kB]     
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Get:6 http://archive.ubuntu.com trusty-backports InRelease [65,9 kB]           
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Get:7 http://archive.ubuntu.com trusty-security InRelease [65,9 kB]            
Hit http://archive.ubuntu.com trusty Release.gpg                               
Get:8 http://archive.ubuntu.com trusty-updates/main Sources [270 kB]           
Ign http://archive.getdeb.net trusty-getdeb/apps Translation-en_US             
Ign http://archive.getdeb.net trusty-getdeb/apps Translation-en                
Get:9 http://archive.ubuntu.com trusty-updates/restricted Sources [5352 B]     
Ign http://deb.opera.com stable/non-free Translation-en_US                     
Ign http://deb.opera.com stable/non-free Translation-en                        
Ign http://deb.opera.com stable/non-free Translation-en_US            
Ign http://extras.ubuntu.com trusty/main Translation-en_US
Ign http://deb.opera.com stable/non-free Translation-en
Get:10 http://archive.ubuntu.com trusty-updates/universe Sources [152 kB]
Ign http://deb.opera.com stable/non-free Translation-en_US                   
Ign http://extras.ubuntu.com trusty/main Translation-en                      
Ign http://deb.opera.com stable/non-free Translation-en 
Ign http://deb.opera.com stable/non-free Translation-en_US             
Ign http://deb.opera.com stable/non-free Translation-en                
Get:11 http://archive.ubuntu.com trusty-updates/multiverse Sources [5928 B]
Get:12 http://archive.ubuntu.com trusty-updates/main amd64 Packages [750 kB]
Get:13 http://archive.ubuntu.com trusty-updates/restricted amd64 Packages [15,9 kB]
Get:14 http://archive.ubuntu.com trusty-updates/universe amd64 Packages [358 kB]
Get:15 http://archive.ubuntu.com trusty-updates/multiverse amd64 Packages [13,2 kB]
Get:16 http://archive.ubuntu.com trusty-updates/main i386 Packages [716 kB]
Get:17 http://archive.ubuntu.com trusty-updates/restricted i386 Packages [15,6 kB]
Get:18 http://archive.ubuntu.com trusty-updates/universe i386 Packages [359 kB]
Get:19 http://archive.ubuntu.com trusty-updates/multiverse i386 Packages [13,6 kB]
Get:20 http://archive.ubuntu.com trusty-updates/main Translation-en [374 kB]
Get:21 http://archive.ubuntu.com trusty-updates/multiverse Translation-en [7227 B]
Get:22 http://archive.ubuntu.com trusty-updates/restricted Translation-en [3699 B]
Get:23 http://archive.ubuntu.com trusty-updates/universe Translation-en [187 kB]
Get:24 http://archive.ubuntu.com trusty-backports/main Sources [8904 B]        
Get:25 http://archive.ubuntu.com trusty-backports/restricted Sources [28 B]    
Get:26 http://archive.ubuntu.com trusty-backports/universe Sources [34,5 kB]   
Get:27 http://archive.ubuntu.com trusty-backports/multiverse Sources [1898 B]  
Get:28 http://archive.ubuntu.com trusty-backports/main amd64 Packages [9967 B] 
Get:29 http://archive.ubuntu.com trusty-backports/restricted amd64 Packages [28 B]
Get:30 http://archive.ubuntu.com trusty-backports/universe amd64 Packages [41,5 kB]
Get:31 http://archive.ubuntu.com trusty-backports/multiverse amd64 Packages [1571 B]
Get:32 http://archive.ubuntu.com trusty-backports/main i386 Packages [9986 B]  
Get:33 http://archive.ubuntu.com trusty-backports/restricted i386 Packages [28 B]
Get:34 http://archive.ubuntu.com trusty-backports/universe i386 Packages [41,5 kB]
Get:35 http://archive.ubuntu.com trusty-backports/multiverse i386 Packages [1552 B]
Hit http://archive.ubuntu.com trusty-backports/main Translation-en             
Hit http://archive.ubuntu.com trusty-backports/multiverse Translation-en       
Hit http://archive.ubuntu.com trusty-backports/restricted Translation-en       
Hit http://archive.ubuntu.com trusty-backports/universe Translation-en         
Get:36 http://archive.ubuntu.com trusty-security/main Sources [110 kB]         
Get:37 http://archive.ubuntu.com trusty-security/restricted Sources [4035 B]   
Get:38 http://archive.ubuntu.com trusty-security/universe Sources [35,2 kB]    
Get:39 http://archive.ubuntu.com trusty-security/multiverse Sources [2764 B]   
Get:40 http://archive.ubuntu.com trusty-security/main amd64 Packages [454 kB]  
Get:41 http://archive.ubuntu.com trusty-security/restricted amd64 Packages [13,0 kB]
Get:42 http://archive.ubuntu.com trusty-security/universe amd64 Packages [126 kB]
Get:43 http://archive.ubuntu.com trusty-security/multiverse amd64 Packages [4982 B]
Get:44 http://archive.ubuntu.com trusty-security/main i386 Packages [427 kB]   
Get:45 http://archive.ubuntu.com trusty-security/restricted i386 Packages [12,7 kB]
Get:46 http://archive.ubuntu.com trusty-security/universe i386 Packages [126 kB]
Get:47 http://archive.ubuntu.com trusty-security/multiverse i386 Packages [5172 B]
Hit http://archive.ubuntu.com trusty-security/main Translation-en              
Hit http://archive.ubuntu.com trusty-security/multiverse Translation-en        
Hit http://archive.ubuntu.com trusty-security/restricted Translation-en        
Hit http://archive.ubuntu.com trusty-security/universe Translation-en          
Hit http://archive.ubuntu.com trusty Release                                   
Hit http://archive.ubuntu.com trusty/main Sources                              
Hit http://archive.ubuntu.com trusty/restricted Sources                        
Hit http://archive.ubuntu.com trusty/universe Sources                          
Hit http://archive.ubuntu.com trusty/multiverse Sources                        
Hit http://archive.ubuntu.com trusty/main amd64 Packages                       
Hit http://archive.ubuntu.com trusty/restricted amd64 Packages                 
Hit http://archive.ubuntu.com trusty/universe amd64 Packages                   
Hit http://archive.ubuntu.com trusty/multiverse amd64 Packages                 
Hit http://archive.ubuntu.com trusty/main i386 Packages                        
Hit http://archive.ubuntu.com trusty/restricted i386 Packages                  
Hit http://archive.ubuntu.com trusty/universe i386 Packages                    
Hit http://archive.ubuntu.com trusty/multiverse i386 Packages                  
Hit http://archive.ubuntu.com trusty/main Translation-en                       
Hit http://archive.ubuntu.com trusty/multiverse Translation-en                 
Hit http://archive.ubuntu.com trusty/restricted Translation-en                 
Hit http://archive.ubuntu.com trusty/universe Translation-en                   
Ign http://archive.ubuntu.com trusty/main Translation-en_US                    
Ign http://archive.ubuntu.com trusty/multiverse Translation-en_US              
Ign http://archive.ubuntu.com trusty/restricted Translation-en_US              
Ign http://archive.ubuntu.com trusty/universe Translation-en_US                
Fetched 5070 kB in 19s (261 kB/s)                                              
Reading package lists... Done



```

"**sudo apt-get autoremove**" also doesn't return anything interesting:

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
```

---

### Post by kansasnoob on 2016-04-10
The logs are in /var/log/apt:

```
lance@lance-desktop:~$ ls /var/log/apt
history.log        history.log.4.gz  term.log.10.gz  term.log.5.gz
history.log.10.gz  history.log.5.gz  term.log.11.gz  term.log.6.gz
history.log.11.gz  history.log.6.gz  term.log.12.gz  term.log.7.gz
history.log.12.gz  history.log.7.gz  term.log.1.gz   term.log.8.gz
history.log.1.gz   history.log.8.gz  term.log.2.gz   term.log.9.gz
history.log.2.gz   history.log.9.gz  term.log.3.gz
history.log.3.gz   term.log          term.log.4.gz

```

After they reach a certain size they get archived. Then the latest archived logs become .1.gz. Typically the history.log is easier to read and may provide enough info to get started.

For now I'd avoid using just apt and stick with using apt-get in Trusty.

I'd like to see the full output of this command:

```
sudo apt-get install -s foomatic-filters
```

The -s simulates what would happen.

---

### Post by richterbg on 2016-04-10
The output of **sudo apt-get install -s foomatic-filters **is as follows: 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  cups cups-filters printer-driver-gutenprint
The following NEW packages will be installed:
  foomatic-filters
0 upgraded, 1 newly installed, 3 to remove and 5 not upgraded.
Remv printer-driver-gutenprint [5.2.10~pre2-0ubuntu2]
Remv cups [1.7.2-0ubuntu1.7]
Remv cups-filters [1.0.52-0ubuntu1.7] [printer-driver-pxljr:amd64 printer-driver-foo2zjs:amd64 ]
Inst foomatic-filters (4.0.17-1ubuntu1 Ubuntu:14.04/trusty [amd64])
Conf foomatic-filters (4.0.17-1ubuntu1 Ubuntu:14.04/trusty [amd64])
```

The history log from January seemed bigger. I believe the problematic update occurred then. The log looks as follows:

```
Start-Date: 2016-01-06  18:00:48
Commandline: aptdaemon role='role-commit-packages' sender=':1.115'
Upgrade: libquadmath0:amd64 (4.8.4-2ubuntu1~14.04, 4.9.2-0ubuntu1~14.04), python-samba:amd64 (4.1.6+dfsg-1ubuntu2.14.04.9, 4.1.6+dfsg-1ubuntu2.14.04.11), winbind:amd64 (4.1.6+dfsg-1ubuntu2.14.04.9, 4.1.6+dfsg-1ubuntu2.14.04.11), libgomp1:amd64 (4.8.4-2ubuntu1~14.04, 4.9.2-0ubuntu1~14.04), libtsan0:amd64 (4.8.4-2ubuntu1~14.04, 4.9.2-0ubuntu1~14.04), samba:amd64 (4.1.6+dfsg-1ubuntu2.14.04.9, 4.1.6+dfsg-1ubuntu2.14.04.11), samba-dsdb-modules:amd64 (4.1.6+dfsg-1ubuntu2.14.04.9, 4.1.6+dfsg-1ubuntu2.14.04.11), libnss-winbind:amd64 (4.1.6+dfsg-1ubuntu2.14.04.9, 4.1.6+dfsg-1ubuntu2.14.04.11), libatomic1:amd64 (4.8.4-2ubuntu1~14.04, 4.9.2-0ubuntu1~14.04), samba-common-bin:amd64 (4.1.6+dfsg-1ubuntu2.14.04.9, 4.1.6+dfsg-1ubuntu2.14.04.11), libldb1:amd64 (1.1.16-1, 1.1.16-1ubuntu0.1), samba-libs:amd64 (4.1.6+dfsg-1ubuntu2.14.04.9, 4.1.6+dfsg-1ubuntu2.14.04.11), smbclient:amd64 (4.1.6+dfsg-1ubuntu2.14.04.9, 4.1.6+dfsg-1ubuntu2.14.04.11), libgfortran3:amd64 (4.8.4-2ubuntu1~14.04, 4.9.2-0ubuntu1~14.04), libpam-winbind:amd64 (4.1.6+dfsg-1ubuntu2.14.04.9, 4.1.6+dfsg-1ubuntu2.14.04.11), libwbclient0:amd64 (4.1.6+dfsg-1ubuntu2.14.04.9, 4.1.6+dfsg-1ubuntu2.14.04.11), samba-vfs-modules:amd64 (4.1.6+dfsg-1ubuntu2.14.04.9, 4.1.6+dfsg-1ubuntu2.14.04.11), python-ldb:amd64 (1.1.16-1, 1.1.16-1ubuntu0.1), samba-common:amd64 (4.1.6+dfsg-1ubuntu2.14.04.9, 4.1.6+dfsg-1ubuntu2.14.04.11), libitm1:amd64 (4.8.4-2ubuntu1~14.04, 4.9.2-0ubuntu1~14.04), libsmbclient:amd64 (4.1.6+dfsg-1ubuntu2.14.04.9, 4.1.6+dfsg-1ubuntu2.14.04.11)
End-Date: 2016-01-06  18:00:56


Start-Date: 2016-01-07  09:22:00
Commandline: aptdaemon role='role-commit-packages' sender=':1.110'
Upgrade: libpng12-0:amd64 (1.2.50-1ubuntu2.14.04.1, 1.2.50-1ubuntu2.14.04.2), libpng12-0:i386 (1.2.50-1ubuntu2.14.04.1, 1.2.50-1ubuntu2.14.04.2)
End-Date: 2016-01-07  09:22:02


Start-Date: 2016-01-08  12:05:52
Commandline: aptdaemon role='role-commit-packages' sender=':1.110'
Upgrade: libnss3-1d:amd64 (3.19.2.1-0ubuntu0.14.04.1, 3.19.2.1-0ubuntu0.14.04.2), libnss3-nssdb:amd64 (3.19.2.1-0ubuntu0.14.04.1, 3.19.2.1-0ubuntu0.14.04.2), libnss3:amd64 (3.19.2.1-0ubuntu0.14.04.1, 3.19.2.1-0ubuntu0.14.04.2), python-pygments:amd64 (1.6+dfsg-1ubuntu1, 1.6+dfsg-1ubuntu1.1)
End-Date: 2016-01-08  12:05:55


Start-Date: 2016-01-09  12:01:19
Commandline: aptdaemon role='role-commit-packages' sender=':1.116'
Upgrade: libgnutls-openssl27:amd64 (2.12.23-12ubuntu2.3, 2.12.23-12ubuntu2.4), firefox-locale-en:amd64 (43.0+build1-0ubuntu0.14.04.1, 43.0.4+build3-0ubuntu0.14.04.1), firefox:amd64 (43.0+build1-0ubuntu0.14.04.1, 43.0.4+build3-0ubuntu0.14.04.1), grub-common:amd64 (2.02~beta2-9ubuntu1.6, 2.02~beta2-9ubuntu1.7), grub2-common:amd64 (2.02~beta2-9ubuntu1.6, 2.02~beta2-9ubuntu1.7), grub-pc-bin:amd64 (2.02~beta2-9ubuntu1.6, 2.02~beta2-9ubuntu1.7), libgnutls26:amd64 (2.12.23-12ubuntu2.3, 2.12.23-12ubuntu2.4), libgnutls26:i386 (2.12.23-12ubuntu2.3, 2.12.23-12ubuntu2.4), grub-pc:amd64 (2.02~beta2-9ubuntu1.6, 2.02~beta2-9ubuntu1.7), libgnutls-dev:amd64 (2.12.23-12ubuntu2.3, 2.12.23-12ubuntu2.4), libgnutlsxx27:amd64 (2.12.23-12ubuntu2.3, 2.12.23-12ubuntu2.4)
End-Date: 2016-01-09  12:01:36


Start-Date: 2016-01-12  14:23:05
Commandline: aptdaemon role='role-commit-packages' sender=':1.113'
Upgrade: oxideqt-codecs-extra:amd64 (1.11.3-0ubuntu0.14.04.1, 1.11.4-0ubuntu0.14.04.1), chromium-codecs-ffmpeg-extra:amd64 (47.0.2526.73-0ubuntu0.14.04.1.1106, 47.0.2526.106-0ubuntu0.14.04.1.1107), liboxideqtcore0:amd64 (1.11.3-0ubuntu0.14.04.1, 1.11.4-0ubuntu0.14.04.1), liboxideqtquick0:amd64 (1.11.3-0ubuntu0.14.04.1, 1.11.4-0ubuntu0.14.04.1), liboxideqt-qmlplugin:amd64 (1.11.3-0ubuntu0.14.04.1, 1.11.4-0ubuntu0.14.04.1), opera-stable:amd64 (34.0.2036.25, 34.0.2036.47)
End-Date: 2016-01-12  14:23:16


Start-Date: 2016-01-12  14:32:27
Commandline: aptdaemon role='role-commit-packages' sender=':1.149'
Install: libunique-3.0-0:amd64 (3.0.2-2ubuntu1, automatic), diodon:amd64 (1.0.2-0ubuntu2), libdiodon0:amd64 (1.0.2-0ubuntu2, automatic)
End-Date: 2016-01-12  14:32:30


Start-Date: 2016-01-13  13:12:49
Commandline: aptdaemon role='role-commit-packages' sender=':1.134'
Install: accountsservice-ubuntu-schemas:amd64 (0.0.1+14.04.20140401-0ubuntu1), qtdeclarative5-folderlistmodel-plugin:amd64 (5.2.1-3ubuntu15.1), ntrack-module-libnl-0:amd64 (016-1.2ubuntu2, automatic), oxygen-icon-theme:amd64 (4.13.0-0ubuntu1), libubuntu-download-manager-common0:amd64 (0.3+14.04.20140321-0ubuntu1, automatic), kdelibs5-data:amd64 (4.13.3-0ubuntu0.2), ubuntuone-credentials-common:amd64 (14.04+14.04.20140415), libubuntu-platform-hardware-api1:amd64 (0.20+14.04.20140411-0ubuntu1, automatic), python3-apparmor:amd64 (2.8.95~2430-0ubuntu5.3, automatic), libqdjango-db0:amd64 (0.4.0-1ubuntu2), libunwind8:amd64 (1.1-2.2ubuntu3, automatic), apparmor-easyprof:amd64 (2.8.95~2430-0ubuntu5.3), mysql-server-core-5.5:amd64 (5.5.46-0ubuntu0.14.04.2), libgflags2:amd64 (2.0-1.1ubuntu1), libqmenumodel0:amd64 (0.2.7+14.04.20140305-0ubuntu2), liblttng-ust-ctl2:amd64 (2.4.0-4ubuntu1, automatic), default-jre:amd64 (1.7-51), mysql-client-core-5.5:amd64 (5.5.46-0ubuntu0.14.04.2), qtdeclarative5-ubuntu-content0.1:amd64 (0.0+14.04.20140415-0ubuntu1), libqrencode3:amd64 (3.4.2-1), nepomuk-core-data:amd64 (4.13.3-0ubuntu0.2), libubuntu-download-manager-priv0:amd64 (0.3+14.04.20140321-0ubuntu1), libntrack0:amd64 (016-1.2ubuntu2), kde-runtime-data:amd64 (4.13.3-0ubuntu0.2), click:amd64 (0.4.21.1ubuntu0.2), libandroid-properties1:amd64 (0.1.0+git20131207+e452e83-0ubuntu12), system-image-dbus:amd64 (2.2-0ubuntu1), libmirplatform:amd64 (0.1.8+14.04.20140411-0ubuntu1), gir1.2-click-0.4:amd64 (0.4.21.1ubuntu0.2, automatic), system-image-common:amd64 (2.2-0ubuntu1), ubuntu-touch-sounds:amd64 (13.10.1), libzip2:amd64 (0.10.1-1.2, automatic), default-jre-headless:amd64 (1.7-51, automatic), mediascanner2.0:amd64 (0.100+14.04.20140403-0ubuntu1, automatic), libdee-qt5-3:amd64 (3.3+14.04.20140317-0ubuntu1), ubuntu-download-manager:amd64 (0.3+14.04.20140321-0ubuntu1, automatic), libpgm-5.1-0:amd64 (5.1.118-1~dfsg-0.1ubuntu3), gir1.2-json-1.0:amd64 (0.16.2-1ubuntu1, automatic), python3-gnupg:amd64 (0.3.6-1), libunity-api0:amd64 (7.80.6+14.04.20140402-0ubuntu1), libubuntu-application-api-mirserver1:amd64 (0.20+14.04.20140411-0ubuntu1), consolekit:amd64 (0.4.5-3.1ubuntu2), libdbus-cpp2:amd64 (2.0.0+14.04.20140326-0ubuntu1), libcontent-hub0:amd64 (0.0+14.04.20140415-0ubuntu1), libvirtodbc0:amd64 (6.1.6+repack-0ubuntu3), gir1.2-gee-0.8:amd64 (0.10.5-1ubuntu1, automatic), liburcu1:amd64 (0.7.12-0ubuntu2, automatic), liblttng-ust0:amd64 (2.4.0-4ubuntu1, automatic), phonon-backend-gstreamer-common:amd64 (4.7.80-0ubuntu2~ubuntu14.04), libmediascanner-2.0-0:amd64 (0.100+14.04.20140403-0ubuntu1), libupstart-app-launch2:amd64 (0.3+14.04.20140411-0ubuntu1, automatic), libmirclient7:amd64 (0.1.8+14.04.20140411-0ubuntu1), libunity-mir1:amd64 (0.3+14.04.20140417-0ubuntu1), virtuoso-opensource-6.1-common:amd64 (6.1.6+repack-0ubuntu3, automatic), virtuoso-opensource-6.1-bin:amd64 (6.1.6+repack-0ubuntu3, automatic), libzmq3:amd64 (4.0.4+dfsg-2, automatic), virtuoso-minimal:amd64 (6.1.6+repack-0ubuntu3), usermetricsservice:amd64 (1.1.1+14.04.20140305-0ubuntu2, automatic), upstart-app-launch:amd64 (0.3+14.04.20140411-0ubuntu1, automatic), qtdeclarative5-unity-notifications-plugin:amd64 (0.1.1+14.04.20140402-0ubuntu1), libonline-accounts-client1:amd64 (0.3+14.04.20140328-0ubuntu3), libcapnp-0.4.0:amd64 (0.4.0-1ubuntu2), ubuntu-keyboard-data:amd64 (0.99.trunk.phablet2+14.04.20140415-0ubuntu1), libqt5xmlpatterns5:amd64 (5.2.1-3), libprocess-cpp1:amd64 (1.0.0+14.04.20140328-0ubuntu1, automatic), sgml-data:amd64 (2.0.9-1, automatic), ttf-dejavu-core:amd64 (2.34-1ubuntu1), libunity-scopes1:amd64 (0.4.2+14.04.20140408-0ubuntu1), libpam-ck-connector:amd64 (0.4.5-3.1ubuntu2, automatic), qtdeclarative5-xmllistmodel-plugin:amd64 (5.2.1-3ubuntu15.1), accountsservice-ubuntu-touch-schemas:amd64 (0.0.1+14.04.20140401-0ubuntu1), libmirserver18:amd64 (0.1.8+14.04.20140411-0ubuntu1), libboost-iostreams1.54.0:amd64 (1.54.0-4ubuntu3.1), libmirclientplatform-mesa:amd64 (0.1.8+14.04.20140411-0ubuntu1, automatic), libgoogle-glog0:amd64 (0.3.3-1), kde-l10n-engb:amd64 (4.13.0-0ubuntu1, automatic), libubuntu-location-service0:amd64 (0.0.2+14.04.20140307-0ubuntu1, automatic), libmirplatformgraphics-mesa:amd64 (0.1.8+14.04.20140411-0ubuntu1), libmirprotobuf0:amd64 (0.1.8+14.04.20140411-0ubuntu1, automatic), libqt5multimediawidgets5:amd64 (5.2.1-0ubuntu5, automatic), qtdeclarative5-qtmultimedia-plugin:amd64 (5.2.1-0ubuntu5), libqt5multimediaquick-p5:amd64 (5.2.1-0ubuntu5), libboost-program-options1.54.0:amd64 (1.54.0-4ubuntu3.1), libboost-serialization1.54.0:amd64 (1.54.0-4ubuntu3.1), qtdeclarative5-gsettings1.0:amd64 (0.1+14.04.20140408-0ubuntu1), libmysqlclient18:amd64 (5.5.46-0ubuntu0.14.04.2), libdlrestrictions1:amd64 (0.15.12ubuntu1), docbook-xml:amd64 (4.5-7.2), foomatic-filters:amd64 (4.0.17-1ubuntu1), libclick-0.4-0:amd64 (0.4.21.1ubuntu0.2, automatic), unity-scope-scopes:amd64 (0.1+14.04.20140404-0ubuntu1), upstart-app-launch-tools:amd64 (0.3+14.04.20140411-0ubuntu1, automatic), libsystemsettings1:amd64 (0.1+14.04.20140411-0ubuntu2), gsettings-ubuntu-touch-schemas:amd64 (0.0.1+14.04.20140401-0ubuntu1), libkdecore5:amd64 (4.13.3-0ubuntu0.2, automatic), qtdeclarative5-ubuntu-settings-components:amd64 (0.1+14.04.20140306-0ubuntu1), libdmtx0a:amd64 (0.7.4-2), click-apparmor:amd64 (0.2ubuntu1, automatic), apparmor-easyprof-ubuntu:amd64 (1.1.16), libusermetricsoutput1:amd64 (1.1.1+14.04.20140305-0ubuntu2), libhud-client2:amd64 (14.04+14.04.20140604-0ubuntu1), docbook-xsl:amd64 (1.78.1+dfsg-1), libhybris-common1:amd64 (0.1.0+git20131207+e452e83-0ubuntu12), libzmqpp3:amd64 (3.2.0-0ubuntu3, automatic), libkfbapi1:amd64 (1.0-0ubuntu4), kde-l10n-bg:amd64 (4.13.0-0ubuntu1, automatic), qmenumodel-qml:amd64 (0.2.7+14.04.20140305-0ubuntu2), suru-icon-theme:amd64 (14.04+14.04.20140410-0ubuntu1), thumbnailer-service:amd64 (1.1+14.04.20150205-0ubuntu1, automatic), libqt5multimedia5-plugins:amd64 (5.2.1-0ubuntu5), libjsoncpp0:amd64 (0.6.0~rc2-3ubuntu1), libepub0:amd64 (0.2.2-2ubuntu1), libubuntu-download-manager-client0:amd64 (0.3+14.04.20140321-0ubuntu1), qtdeclarative5-dee-plugin:amd64 (3.3+14.04.20140317-0ubuntu1), python3-click:amd64 (0.4.21.1ubuntu0.2, automatic), python3-libapparmor:amd64 (2.8.95~2430-0ubuntu5.3, automatic), libqgsttools-p1:amd64 (5.2.1-0ubuntu5), ubuntu-mobile-icons:amd64 (14.04+14.04.20140410-0ubuntu1, automatic), libck-connector0:amd64 (0.4.5-3.1ubuntu2, automatic), libkgapi2-2:amd64 (2.1.0-0ubuntu1), libqt5systeminfo5:amd64 (5.0~git20130712-0ubuntu4), python3-apparmor-click:amd64 (0.2ubuntu1, automatic), libxml2-utils:amd64 (2.9.1+dfsg1-3ubuntu4.6), qtdeclarative5-systeminfo-plugin:amd64 (5.0~git20130712-0ubuntu4), kate-data:amd64 (4.13.3-0ubuntu0.1), libakonadi-kabc4:amd64 (4.13.3-0ubuntu0.2), unity-plugin-scopes:amd64 (0.4.0+14.04.20140408-0ubuntu2), shared-desktop-ontologies:amd64 (0.11.0-1), qtdeclarative5-ubuntu-settings-components-assets:amd64 (0.1+14.04.20140306-0ubuntu1, automatic), qtdeclarative5-ubuntu-thumbnailer0.1:amd64 (1.1+14.04.20150205-0ubuntu1), libofono-qt1:amd64 (1.5+git20120419+bcf0c04-0ubuntu6)
Upgrade: libnautilus-extension1a:amd64 (3.10.1-0ubuntu9.10, 3.10.1-0ubuntu9.11), libmm-glib0:amd64 (1.0.0-2ubuntu1, 1.0.0-2ubuntu1.1), modemmanager:amd64 (1.0.0-2ubuntu1, 1.0.0-2ubuntu1.1), nautilus-data:amd64 (3.10.1-0ubuntu9.10, 3.10.1-0ubuntu9.11)
Remove: hplip:amd64 (3.14.3-0ubuntu3.4), cups:amd64 (1.7.2-0ubuntu1.7), bluez-cups:amd64 (4.101-0ubuntu13.1), printer-driver-postscript-hp:amd64 (3.14.3-0ubuntu3.4), printer-driver-gutenprint:amd64 (5.2.10~pre2-0ubuntu2), cups-filters:amd64 (1.0.52-0ubuntu1.7), printer-driver-splix:amd64 (2.0.0+svn315-2fakesync1), printer-driver-hpcups:amd64 (3.14.3-0ubuntu3.4), indicator-printers:amd64 (0.1.7+14.04.20140527-0ubuntu1)
End-Date: 2016-01-13  13:13:40


Start-Date: 2016-01-16  09:03:13
Commandline: apt-get upgrade
Upgrade: oneconf:amd64 (0.3.7, 0.3.7.14.04.1), isc-dhcp-common:amd64 (4.2.4-7ubuntu12.3, 4.2.4-7ubuntu12.4), google-chrome-stable:amd64 (47.0.2526.106-1, 47.0.2526.111-1), thunderbird-locale-en-us:amd64 (38.4.0+build3-0ubuntu0.14.04.1, 38.5.1+build2-0ubuntu0.14.04.1), opera-beta:amd64 (35.0.2066.10, 35.0.2066.23), thunderbird:amd64 (38.4.0+build3-0ubuntu0.14.04.1, 38.5.1+build2-0ubuntu0.14.04.1), python3-software-properties:amd64 (0.92.37.6, 0.92.37.7), python3-oneconf:amd64 (0.3.7, 0.3.7.14.04.1), opera-developer:amd64 (36.0.2079.0, 36.0.2106.0), ssh-askpass-gnome:amd64 (6.6p1-2ubuntu2.3, 6.6p1-2ubuntu2.4), thunderbird-locale-en:amd64 (38.4.0+build3-0ubuntu0.14.04.1, 38.5.1+build2-0ubuntu0.14.04.1), nautilus:amd64 (3.10.1-0ubuntu9.10, 3.10.1-0ubuntu9.11), openssh-client:amd64 (6.6p1-2ubuntu2.3, 6.6p1-2ubuntu2.4), oneconf-common:amd64 (0.3.7, 0.3.7.14.04.1), thunderbird-gnome-support:amd64 (38.4.0+build3-0ubuntu0.14.04.1, 38.5.1+build2-0ubuntu0.14.04.1), isc-dhcp-client:amd64 (4.2.4-7ubuntu12.3, 4.2.4-7ubuntu12.4), software-properties-common:amd64 (0.92.37.6, 0.92.37.7), python-oneconf:amd64 (0.3.7, 0.3.7.14.04.1), software-properties-gtk:amd64 (0.92.37.6, 0.92.37.7)
End-Date: 2016-01-16  09:03:40


Start-Date: 2016-01-16  09:55:13
Commandline: aptdaemon role='role-commit-packages' sender=':1.110'
Install: cups:amd64 (1.7.2-0ubuntu1.7), printer-driver-gutenprint:amd64 (5.2.10~pre2-0ubuntu2, automatic), cups-filters:amd64 (1.0.52-0ubuntu1.7, automatic)
Remove: foomatic-filters:amd64 (4.0.17-1ubuntu1)
End-Date: 2016-01-16  09:55:19

```

---

### Post by kansasnoob on 2016-04-10
I wonder what action brought this about:

```
Start-Date: 2016-01-13  13:12:49
Commandline: aptdaemon role='role-commit-packages' sender=':1.134'
**[COLOR="#FF0000"]Install[/COLOR]**: accountsservice-ubuntu-schemas:amd64 (0.0.1+14.04.20140401-0ubuntu1), qtdeclarative5-folderlistmodel-plugin:amd64 (5.2.1-3ubuntu15.1), ntrack-module-libnl-0:amd64 (016-1.2ubuntu2, automatic), oxygen-icon-theme:amd64 (4.13.0-0ubuntu1), libubuntu-download-manager-common0:amd64 (0.3+14.04.20140321-0ubuntu1, automatic), kdelibs5-data:amd64 (4.13.3-0ubuntu0.2), ubuntuone-credentials-common:amd64 (14.04+14.04.20140415), libubuntu-platform-hardware-api1:amd64 (0.20+14.04.20140411-0ubuntu1, automatic), python3-apparmor:amd64 (2.8.95~2430-0ubuntu5.3, automatic), libqdjango-db0:amd64 (0.4.0-1ubuntu2), libunwind8:amd64 (1.1-2.2ubuntu3, automatic), apparmor-easyprof:amd64 (2.8.95~2430-0ubuntu5.3), mysql-server-core-5.5:amd64 (5.5.46-0ubuntu0.14.04.2), libgflags2:amd64 (2.0-1.1ubuntu1), libqmenumodel0:amd64 (0.2.7+14.04.20140305-0ubuntu2), liblttng-ust-ctl2:amd64 (2.4.0-4ubuntu1, automatic), default-jre:amd64 (1.7-51), mysql-client-core-5.5:amd64 (5.5.46-0ubuntu0.14.04.2), qtdeclarative5-ubuntu-content0.1:amd64 (0.0+14.04.20140415-0ubuntu1), libqrencode3:amd64 (3.4.2-1), nepomuk-core-data:amd64 (4.13.3-0ubuntu0.2), libubuntu-download-manager-priv0:amd64 (0.3+14.04.20140321-0ubuntu1), libntrack0:amd64 (016-1.2ubuntu2), kde-runtime-data:amd64 (4.13.3-0ubuntu0.2), click:amd64 (0.4.21.1ubuntu0.2), libandroid-properties1:amd64 (0.1.0+git20131207+e452e83-0ubuntu12), system-image-dbus:amd64 (2.2-0ubuntu1), libmirplatform:amd64 (0.1.8+14.04.20140411-0ubuntu1), gir1.2-click-0.4:amd64 (0.4.21.1ubuntu0.2, automatic), system-image-common:amd64 (2.2-0ubuntu1), ubuntu-touch-sounds:amd64 (13.10.1), libzip2:amd64 (0.10.1-1.2, automatic), default-jre-headless:amd64 (1.7-51, automatic), mediascanner2.0:amd64 (0.100+14.04.20140403-0ubuntu1, automatic), libdee-qt5-3:amd64 (3.3+14.04.20140317-0ubuntu1), ubuntu-download-manager:amd64 (0.3+14.04.20140321-0ubuntu1, automatic), libpgm-5.1-0:amd64 (5.1.118-1~dfsg-0.1ubuntu3), gir1.2-json-1.0:amd64 (0.16.2-1ubuntu1, automatic), python3-gnupg:amd64 (0.3.6-1), libunity-api0:amd64 (7.80.6+14.04.20140402-0ubuntu1), libubuntu-application-api-mirserver1:amd64 (0.20+14.04.20140411-0ubuntu1), consolekit:amd64 (0.4.5-3.1ubuntu2), libdbus-cpp2:amd64 (2.0.0+14.04.20140326-0ubuntu1), libcontent-hub0:amd64 (0.0+14.04.20140415-0ubuntu1), libvirtodbc0:amd64 (6.1.6+repack-0ubuntu3), gir1.2-gee-0.8:amd64 (0.10.5-1ubuntu1, automatic), liburcu1:amd64 (0.7.12-0ubuntu2, automatic), liblttng-ust0:amd64 (2.4.0-4ubuntu1, automatic), phonon-backend-gstreamer-common:amd64 (4.7.80-0ubuntu2~ubuntu14.04), libmediascanner-2.0-0:amd64 (0.100+14.04.20140403-0ubuntu1), libupstart-app-launch2:amd64 (0.3+14.04.20140411-0ubuntu1, automatic), libmirclient7:amd64 (0.1.8+14.04.20140411-0ubuntu1), libunity-mir1:amd64 (0.3+14.04.20140417-0ubuntu1), virtuoso-opensource-6.1-common:amd64 (6.1.6+repack-0ubuntu3, automatic), virtuoso-opensource-6.1-bin:amd64 (6.1.6+repack-0ubuntu3, automatic), libzmq3:amd64 (4.0.4+dfsg-2, automatic), virtuoso-minimal:amd64 (6.1.6+repack-0ubuntu3), usermetricsservice:amd64 (1.1.1+14.04.20140305-0ubuntu2, automatic), upstart-app-launch:amd64 (0.3+14.04.20140411-0ubuntu1, automatic), qtdeclarative5-unity-notifications-plugin:amd64 (0.1.1+14.04.20140402-0ubuntu1), libonline-accounts-client1:amd64 (0.3+14.04.20140328-0ubuntu3), libcapnp-0.4.0:amd64 (0.4.0-1ubuntu2), ubuntu-keyboard-data:amd64 (0.99.trunk.phablet2+14.04.20140415-0ubuntu1), libqt5xmlpatterns5:amd64 (5.2.1-3), libprocess-cpp1:amd64 (1.0.0+14.04.20140328-0ubuntu1, automatic), sgml-data:amd64 (2.0.9-1, automatic), ttf-dejavu-core:amd64 (2.34-1ubuntu1), libunity-scopes1:amd64 (0.4.2+14.04.20140408-0ubuntu1), libpam-ck-connector:amd64 (0.4.5-3.1ubuntu2, automatic), qtdeclarative5-xmllistmodel-plugin:amd64 (5.2.1-3ubuntu15.1), accountsservice-ubuntu-touch-schemas:amd64 (0.0.1+14.04.20140401-0ubuntu1), libmirserver18:amd64 (0.1.8+14.04.20140411-0ubuntu1), libboost-iostreams1.54.0:amd64 (1.54.0-4ubuntu3.1), libmirclientplatform-mesa:amd64 (0.1.8+14.04.20140411-0ubuntu1, automatic), libgoogle-glog0:amd64 (0.3.3-1), kde-l10n-engb:amd64 (4.13.0-0ubuntu1, automatic), libubuntu-location-service0:amd64 (0.0.2+14.04.20140307-0ubuntu1, automatic), libmirplatformgraphics-mesa:amd64 (0.1.8+14.04.20140411-0ubuntu1), libmirprotobuf0:amd64 (0.1.8+14.04.20140411-0ubuntu1, automatic), libqt5multimediawidgets5:amd64 (5.2.1-0ubuntu5, automatic), qtdeclarative5-qtmultimedia-plugin:amd64 (5.2.1-0ubuntu5), libqt5multimediaquick-p5:amd64 (5.2.1-0ubuntu5), libboost-program-options1.54.0:amd64 (1.54.0-4ubuntu3.1), libboost-serialization1.54.0:amd64 (1.54.0-4ubuntu3.1), qtdeclarative5-gsettings1.0:amd64 (0.1+14.04.20140408-0ubuntu1), libmysqlclient18:amd64 (5.5.46-0ubuntu0.14.04.2), libdlrestrictions1:amd64 (0.15.12ubuntu1), docbook-xml:amd64 (4.5-7.2), foomatic-filters:amd64 (4.0.17-1ubuntu1), libclick-0.4-0:amd64 (0.4.21.1ubuntu0.2, automatic), unity-scope-scopes:amd64 (0.1+14.04.20140404-0ubuntu1), upstart-app-launch-tools:amd64 (0.3+14.04.20140411-0ubuntu1, automatic), libsystemsettings1:amd64 (0.1+14.04.20140411-0ubuntu2), gsettings-ubuntu-touch-schemas:amd64 (0.0.1+14.04.20140401-0ubuntu1), libkdecore5:amd64 (4.13.3-0ubuntu0.2, automatic), qtdeclarative5-ubuntu-settings-components:amd64 (0.1+14.04.20140306-0ubuntu1), libdmtx0a:amd64 (0.7.4-2), click-apparmor:amd64 (0.2ubuntu1, automatic), apparmor-easyprof-ubuntu:amd64 (1.1.16), libusermetricsoutput1:amd64 (1.1.1+14.04.20140305-0ubuntu2), libhud-client2:amd64 (14.04+14.04.20140604-0ubuntu1), docbook-xsl:amd64 (1.78.1+dfsg-1), libhybris-common1:amd64 (0.1.0+git20131207+e452e83-0ubuntu12), libzmqpp3:amd64 (3.2.0-0ubuntu3, automatic), libkfbapi1:amd64 (1.0-0ubuntu4), kde-l10n-bg:amd64 (4.13.0-0ubuntu1, automatic), qmenumodel-qml:amd64 (0.2.7+14.04.20140305-0ubuntu2), suru-icon-theme:amd64 (14.04+14.04.20140410-0ubuntu1), thumbnailer-service:amd64 (1.1+14.04.20150205-0ubuntu1, automatic), libqt5multimedia5-plugins:amd64 (5.2.1-0ubuntu5), libjsoncpp0:amd64 (0.6.0~rc2-3ubuntu1), libepub0:amd64 (0.2.2-2ubuntu1), libubuntu-download-manager-client0:amd64 (0.3+14.04.20140321-0ubuntu1), qtdeclarative5-dee-plugin:amd64 (3.3+14.04.20140317-0ubuntu1), python3-click:amd64 (0.4.21.1ubuntu0.2, automatic), python3-libapparmor:amd64 (2.8.95~2430-0ubuntu5.3, automatic), libqgsttools-p1:amd64 (5.2.1-0ubuntu5), ubuntu-mobile-icons:amd64 (14.04+14.04.20140410-0ubuntu1, automatic), libck-connector0:amd64 (0.4.5-3.1ubuntu2, automatic), libkgapi2-2:amd64 (2.1.0-0ubuntu1), libqt5systeminfo5:amd64 (5.0~git20130712-0ubuntu4), python3-apparmor-click:amd64 (0.2ubuntu1, automatic), libxml2-utils:amd64 (2.9.1+dfsg1-3ubuntu4.6), qtdeclarative5-systeminfo-plugin:amd64 (5.0~git20130712-0ubuntu4), kate-data:amd64 (4.13.3-0ubuntu0.1), libakonadi-kabc4:amd64 (4.13.3-0ubuntu0.2), unity-plugin-scopes:amd64 (0.4.0+14.04.20140408-0ubuntu2), shared-desktop-ontologies:amd64 (0.11.0-1), qtdeclarative5-ubuntu-settings-components-assets:amd64 (0.1+14.04.20140306-0ubuntu1, automatic), qtdeclarative5-ubuntu-thumbnailer0.1:amd64 (1.1+14.04.20150205-0ubuntu1), libofono-qt1:amd64 (1.5+git20120419+bcf0c04-0ubuntu6)
**[COLOR="#FF0000"]Upgrade[/COLOR]**: libnautilus-extension1a:amd64 (3.10.1-0ubuntu9.10, 3.10.1-0ubuntu9.11), libmm-glib0:amd64 (1.0.0-2ubuntu1, 1.0.0-2ubuntu1.1), modemmanager:amd64 (1.0.0-2ubuntu1, 1.0.0-2ubuntu1.1), nautilus-data:amd64 (3.10.1-0ubuntu9.10, 3.10.1-0ubuntu9.11)
**[COLOR="#FF0000"]Remove[/COLOR]**: hplip:amd64 (3.14.3-0ubuntu3.4), cups:amd64 (1.7.2-0ubuntu1.7), bluez-cups:amd64 (4.101-0ubuntu13.1), printer-driver-postscript-hp:amd64 (3.14.3-0ubuntu3.4), printer-driver-gutenprint:amd64 (5.2.10~pre2-0ubuntu2), cups-filters:amd64 (1.0.52-0ubuntu1.7), printer-driver-splix:amd64 (2.0.0+svn315-2fakesync1), printer-driver-hpcups:amd64 (3.14.3-0ubuntu3.4), indicator-printers:amd64 (0.1.7+14.04.20140527-0ubuntu1)
End-Date: 2016-01-13  13:13:40
```

Lots & lots of packages installed :confused:

---

### Post by richterbg on 2016-04-10
Well, I guess, it was the first time I saw that message that not all updates can be installed:

[IMG]http://i.imgur.com/yoMpIeW.png[/IMG]

However, for the love of the Almighty, I can't remember if I clicked Continue, or Partial upgrade...

---

### Post by kansasnoob on 2016-04-10
If this is standard Ubuntu and not one of the other flavors it might be worth trying:

```
sudo apt-get install -s ubuntu-desktop^
```

The ^ is intentional to be sure all required dependencies are properly installed and defined as true dependencies. If the outcome listed at the end does NOT scare the hell out of you it would probably be safe to run without the -s so it can actually do its thing, but** if in doubt show us what that command displays at the end**.

And maybe we should see if dpkg is hung up (**I can NOT 100% guarantee that won't break things but commonly it won't**):

```
sudo dpkg --configure -a
```

I have to be AFK for a bit but I'll check back when I return.

---

### Post by kansasnoob on 2016-04-10
Just thinking out loud before I run out of here ............................. it might be worth investigating whether or not some arch mismatched packages have been installed :confused: I think this looks like a 64 bit install, eh? If so maybe a 32 bit specific package was installed from an external source? I'm not even sure how or where to begin looking but it's just a silly thought :-k

---

### Post by richterbg on 2016-04-11
I'm in Europe, so most likely I won't be able to read your input right after you submit it anyway. In other words, we are not in a hurry. This is not an emergency. The Ubuntu installation works. I managed to update the kernel through Synaptic, so I guess the OS is pretty much up to date. 

I really do appreciate that you take your time to troubleshoot this. 

The **[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install -s ubuntu-desktop^ command[/FONT][/COLOR]**[COLOR=#000000][FONT=Ubuntu Mono] did not return something scary:

[/FONT][/COLOR]```
Reading package lists...Building dependency tree...
Reading state information...
acl is already the newest version.
acpi-support is already the newest version.
acpid is already the newest version.
adium-theme-ubuntu is already the newest version.
aisleriot is already the newest version.
alsa-base is already the newest version.
alsa-utils is already the newest version.
anacron is already the newest version.
apg is already the newest version.
app-install-data-partner is already the newest version.
appmenu-qt is already the newest version.
appmenu-qt5 is already the newest version.
apport-symptoms is already the newest version.
apt-xapian-index is already the newest version.
apturl is already the newest version.
apturl-common is already the newest version.
aspell is already the newest version.
aspell-en is already the newest version.
at-spi2-core is already the newest version.
avahi-autoipd is already the newest version.
avahi-daemon is already the newest version.
avahi-utils is already the newest version.
bamfdaemon is already the newest version.
baobab is already the newest version.
bc is already the newest version.
branding-ubuntu is already the newest version.
brasero is already the newest version.
brasero-cdrkit is already the newest version.
brasero-common is already the newest version.
brltty is already the newest version.
checkbox-gui is already the newest version.
checkbox-ng is already the newest version.
checkbox-ng-service is already the newest version.
cheese is already the newest version.
cheese-common is already the newest version.
colord is already the newest version.
cpp is already the newest version.
cracklib-runtime is already the newest version.
crda is already the newest version.
cups-pk-helper is already the newest version.
dc is already the newest version.
dconf-cli is already the newest version.
dconf-gsettings-backend is already the newest version.
dconf-service is already the newest version.
deja-dup is already the newest version.
deja-dup-backend-gvfs is already the newest version.
desktop-file-utils is already the newest version.
dialog is already the newest version.
dictionaries-common is already the newest version.
diffstat is already the newest version.
dmz-cursor-theme is already the newest version.
doc-base is already the newest version.
dvd+rw-tools is already the newest version.
enchant is already the newest version.
espeak-data is already the newest version.
ethtool is already the newest version.
example-content is already the newest version.
folks-common is already the newest version.
fonts-dejavu-core is already the newest version.
fonts-freefont-ttf is already the newest version.
fonts-kacst is already the newest version.
fonts-kacst-one is already the newest version.
fonts-khmeros-core is already the newest version.
fonts-lao is already the newest version.
fonts-liberation is already the newest version.
fonts-lklug-sinhala is already the newest version.
fonts-nanum is already the newest version.
fonts-sil-abyssinica is already the newest version.
fonts-sil-padauk is already the newest version.
fonts-takao-pgothic is already the newest version.
fonts-thai-tlwg is already the newest version.
fonts-tibetan-machine is already the newest version.
fonts-tlwg-garuda is already the newest version.
fonts-tlwg-kinnari is already the newest version.
fonts-tlwg-loma is already the newest version.
fonts-tlwg-mono is already the newest version.
fonts-tlwg-norasi is already the newest version.
fonts-tlwg-purisa is already the newest version.
fonts-tlwg-sawasdee is already the newest version.
fonts-tlwg-typewriter is already the newest version.
fonts-tlwg-typist is already the newest version.
fonts-tlwg-typo is already the newest version.
fonts-tlwg-umpush is already the newest version.
fonts-tlwg-waree is already the newest version.
foomatic-db-compressed-ppds is already the newest version.
friends is already the newest version.
friends-dispatcher is already the newest version.
friends-facebook is already the newest version.
friends-twitter is already the newest version.
gcc is already the newest version.
gconf-service is already the newest version.
gconf-service-backend is already the newest version.
gconf2 is already the newest version.
gconf2-common is already the newest version.
gcr is already the newest version.
gedit is already the newest version.
gedit-common is already the newest version.
genisoimage is already the newest version.
geoclue is already the newest version.
geoclue-ubuntu-geoip is already the newest version.
gir1.2-accounts-1.0 is already the newest version.
gir1.2-atk-1.0 is already the newest version.
gir1.2-atspi-2.0 is already the newest version.
gir1.2-dee-1.0 is already the newest version.
gir1.2-gdata-0.0 is already the newest version.
gir1.2-gmenu-3.0 is already the newest version.
gir1.2-gnomekeyring-1.0 is already the newest version.
gir1.2-goa-1.0 is already the newest version.
gir1.2-gtksource-3.0 is already the newest version.
gir1.2-messagingmenu-1.0 is already the newest version.
gir1.2-notify-0.7 is already the newest version.
gir1.2-packagekitglib-1.0 is already the newest version.
gir1.2-peas-1.0 is already the newest version.
gir1.2-secret-1 is already the newest version.
gir1.2-signon-1.0 is already the newest version.
gir1.2-soup-2.4 is already the newest version.
gir1.2-totem-1.0 is already the newest version.
gir1.2-totem-plparser-1.0 is already the newest version.
gir1.2-unity-5.0 is already the newest version.
gkbd-capplet is already the newest version.
gnome-accessibility-themes is already the newest version.
gnome-contacts is already the newest version.
gnome-disk-utility is already the newest version.
gnome-font-viewer is already the newest version.
gnome-icon-theme is already the newest version.
gnome-icon-theme-symbolic is already the newest version.
gnome-mahjongg is already the newest version.
gnome-menus is already the newest version.
gnome-mines is already the newest version.
gnome-orca is already the newest version.
gnome-power-manager is already the newest version.
gnome-screensaver is already the newest version.
gnome-screenshot is already the newest version.
gnome-session-canberra is already the newest version.
gnome-system-log is already the newest version.
gnome-system-monitor is already the newest version.
gnome-terminal is already the newest version.
gnome-terminal-data is already the newest version.
gnome-user-guide is already the newest version.
gnome-user-share is already the newest version.
gnome-video-effects is already the newest version.
gnomine is already the newest version.
growisofs is already the newest version.
gsettings-desktop-schemas is already the newest version.
gsettings-ubuntu-schemas is already the newest version.
gsfonts is already the newest version.
gstreamer0.10-alsa is already the newest version.
gstreamer0.10-nice is already the newest version.
gstreamer0.10-plugins-base is already the newest version.
gstreamer0.10-plugins-base-apps is already the newest version.
gstreamer0.10-plugins-good is already the newest version.
gstreamer0.10-pulseaudio is already the newest version.
gstreamer0.10-tools is already the newest version.
gstreamer0.10-x is already the newest version.
gstreamer1.0-clutter is already the newest version.
gstreamer1.0-nice is already the newest version.
gtk2-engines-murrine is already the newest version.
gtk3-engines-unico is already the newest version.
gucharmap is already the newest version.
guile-2.0-libs is already the newest version.
hicolor-icon-theme is already the newest version.
humanity-icon-theme is already the newest version.
hunspell-en-us is already the newest version.
hwdata is already the newest version.
ibus-pinyin is already the newest version.
ibus-table is already the newest version.
indicator-application is already the newest version.
indicator-appmenu is already the newest version.
indicator-bluetooth is already the newest version.
indicator-datetime is already the newest version.
indicator-keyboard is already the newest version.
indicator-messages is already the newest version.
indicator-power is already the newest version.
indicator-sound is already the newest version.
inputattach is already the newest version.
intltool-debian is already the newest version.
iw is already the newest version.
kerneloops-daemon is already the newest version.
laptop-detect is already the newest version.
libaa1 is already the newest version.
libaccount-plugin-1.0-0 is already the newest version.
libaccounts-glib0 is already the newest version.
libaccounts-qt5-1 is already the newest version.
libapt-pkg-perl is already the newest version.
libarchive-zip-perl is already the newest version.
libart-2.0-2 is already the newest version.
libasound2 is already the newest version.
libasound2-data is already the newest version.
libasound2-plugins is already the newest version.
libaspell15 is already the newest version.
libassuan0 is already the newest version.
libasyncns0 is already the newest version.
libatasmart4 is already the newest version.
libatk-adaptor is already the newest version.
libatk-bridge2.0-0 is already the newest version.
libatk1.0-0 is already the newest version.
libatk1.0-data is already the newest version.
libatkmm-1.6-1 is already the newest version.
libatspi2.0-0 is already the newest version.
libaudio2 is already the newest version.
libauthen-sasl-perl is already the newest version.
libautodie-perl is already the newest version.
libavahi-client3 is already the newest version.
libavahi-common-data is already the newest version.
libavahi-common3 is already the newest version.
libavahi-core7 is already the newest version.
libavahi-glib1 is already the newest version.
libavahi-gobject0 is already the newest version.
libavc1394-0 is already the newest version.
libbamf3-2 is already the newest version.
libbrasero-media3-1 is already the newest version.
libbrlapi0.6 is already the newest version.
libburn4 is already the newest version.
libcaca0 is already the newest version.
libcairomm-1.0-1 is already the newest version.
libcanberra-gtk-module is already the newest version.
libcanberra-gtk0 is already the newest version.
libcanberra-gtk3-0 is already the newest version.
libcanberra-gtk3-module is already the newest version.
libcanberra-pulse is already the newest version.
libcanberra0 is already the newest version.
libcdio-cdda1 is already the newest version.
libcdio-paranoia1 is already the newest version.
libcdio13 is already the newest version.
libcdparanoia0 is already the newest version.
libcdr-0.0-0 is already the newest version.
libcheese-gtk23 is already the newest version.
libcheese7 is already the newest version.
libclass-accessor-perl is already the newest version.
libclone-perl is already the newest version.
libcloog-isl4 is already the newest version.
libclucene-contribs1 is already the newest version.
libclucene-core1 is already the newest version.
libclutter-1.0-0 is already the newest version.
libclutter-1.0-common is already the newest version.
libclutter-gst-2.0-0 is already the newest version.
libcmis-0.4-4 is already the newest version.
libcogl-common is already the newest version.
libcogl-pango15 is already the newest version.
libcogl15 is already the newest version.
libcolamd2.8.0 is already the newest version.
libcolord1 is already the newest version.
libcolorhug1 is already the newest version.
libcolumbus1 is already the newest version.
libcolumbus1-common is already the newest version.
libcrack2 is already the newest version.
libcroco3 is already the newest version.
libcrypt-passwdmd5-perl is already the newest version.
libdaemon0 is already the newest version.
libdatrie1 is already the newest version.
libdbusmenu-qt2 is already the newest version.
libdbusmenu-qt5 is already the newest version.
libdconf1 is already the newest version.
libdee-1.0-4 is already the newest version.
libdigest-hmac-perl is already the newest version.
libdjvulibre-text is already the newest version.
libdjvulibre21 is already the newest version.
libdmapsharing-3.0-2 is already the newest version.
libdotconf0 is already the newest version.
libdv4 is already the newest version.
libelfg0 is already the newest version.
libemail-valid-perl is already the newest version.
libenchant1c2a is already the newest version.
libespeak1 is already the newest version.
libexempi3 is already the newest version.
libexif12 is already the newest version.
libexiv2-12 is already the newest version.
libexttextcat-2.0-0 is already the newest version.
libexttextcat-data is already the newest version.
libfarstream-0.1-0 is already the newest version.
libfarstream-0.2-2 is already the newest version.
libfftw3-single3 is already the newest version.
libfile-basedir-perl is already the newest version.
libfile-copy-recursive-perl is already the newest version.
libfile-desktopentry-perl is already the newest version.
libfile-fcntllock-perl is already the newest version.
libfile-mimeinfo-perl is already the newest version.
libfolks-eds25 is already the newest version.
libfolks-telepathy25 is already the newest version.
libfolks25 is already the newest version.
libfontenc1 is already the newest version.
libframe6 is already the newest version.
libfreerdp-plugins-standard is already the newest version.
libfreerdp1 is already the newest version.
libfriends0 is already the newest version.
libfs6 is already the newest version.
libgc1c2 is already the newest version.
libgconf-2-4 is already the newest version.
libgcr-ui-3-1 is already the newest version.
libgd3 is already the newest version.
libgdata-common is already the newest version.
libgdata13 is already the newest version.
libgee-0.8-2 is already the newest version.
libgee2 is already the newest version.
libgeis1 is already the newest version.
libgeoclue0 is already the newest version.
libglamor0 is already the newest version.
libglew1.10 is already the newest version.
libglewmx1.10 is already the newest version.
libglibmm-2.4-1c2a is already the newest version.
libglu1-mesa is already the newest version.
libgmime-2.6-0 is already the newest version.
libgmp10 is already the newest version.
libgnome-keyring-common is already the newest version.
libgnome-keyring0 is already the newest version.
libgnome-menu-3-0 is already the newest version.
libgnomekbd-common is already the newest version.
libgnomekbd8 is already the newest version.
libgoa-1.0-0b is already the newest version.
libgoa-1.0-common is already the newest version.
libgpm2 is already the newest version.
libgpod-common is already the newest version.
libgpod4 is already the newest version.
libgrail6 is already the newest version.
libgrip0 is already the newest version.
libgsettings-qt1 is already the newest version.
libgssdp-1.0-3 is already the newest version.
libgstreamer-plugins-base0.10-0 is already the newest version.
libgstreamer0.10-0 is already the newest version.
libgtkmm-3.0-1 is already the newest version.
libgtksourceview-3.0-1 is already the newest version.
libgtksourceview-3.0-common is already the newest version.
libgtop2-7 is already the newest version.
libgtop2-common is already the newest version.
libgucharmap-2-90-7 is already the newest version.
libgupnp-1.0-4 is already the newest version.
libgupnp-igd-1.0-4 is already the newest version.
libgusb2 is already the newest version.
libgutenprint2 is already the newest version.
libgxps2 is already the newest version.
libhyphen0 is already the newest version.
libical1 is already the newest version.
libice6 is already the newest version.
libiec61883-0 is already the newest version.
libieee1284-3 is already the newest version.
libijs-0.35 is already the newest version.
libimobiledevice4 is already the newest version.
libio-pty-perl is already the newest version.
libio-socket-inet6-perl is already the newest version.
libio-socket-ssl-perl is already the newest version.
libio-string-perl is already the newest version.
libipc-run-perl is already the newest version.
libipc-system-simple-perl is already the newest version.
libisl10 is already the newest version.
libisofs6 is already the newest version.
libiw30 is already the newest version.
libjack-jackd2-0 is already the newest version.
libjbig2dec0 is already the newest version.
libjpeg-turbo8 is already the newest version.
libjpeg8 is already the newest version.
libjson-glib-1.0-0 is already the newest version.
libjson-glib-1.0-common is already the newest version.
libjte1 is already the newest version.
libkpathsea6 is already the newest version.
liblangtag-common is already the newest version.
liblangtag1 is already the newest version.
liblcms2-2 is already the newest version.
liblircclient0 is already the newest version.
liblist-moreutils-perl is already the newest version.
libllvm3.4 is already the newest version.
liblouis-data is already the newest version.
liblouis2 is already the newest version.
libltdl7 is already the newest version.
liblua5.2-0 is already the newest version.
libmailtools-perl is already the newest version.
libmeanwhile1 is already the newest version.
libmessaging-menu0 is already the newest version.
libmhash2 is already the newest version.
libmission-control-plugins0 is already the newest version.
libmnl0 is already the newest version.
libmpc3 is already the newest version.
libmpfr4 is already the newest version.
libmspub-0.0-0 is already the newest version.
libmtdev1 is already the newest version.
libmythes-1.2-0 is already the newest version.
libnatpmp1 is already the newest version.
libneon27-gnutls is already the newest version.
libnet-dns-perl is already the newest version.
libnet-domain-tld-perl is already the newest version.
libnet-ip-perl is already the newest version.
libnet-libidn-perl is already the newest version.
libnet-smtp-ssl-perl is already the newest version.
libnet-ssleay-perl is already the newest version.
libnetfilter-conntrack3 is already the newest version.
libnice10 is already the newest version.
libnl-3-200 is already the newest version.
libnl-genl-3-200 is already the newest version.
libnl-route-3-200 is already the newest version.
libnotify-bin is already the newest version.
libnotify4 is already the newest version.
libnss-mdns is already the newest version.
libntdb1 is already the newest version.
liboauth0 is already the newest version.
libogg0 is already the newest version.
libopencc1 is already the newest version.
libopenobex1 is already the newest version.
liborc-0.4-0 is already the newest version.
liborcus-0.6-0 is already the newest version.
libpackagekit-glib2-16 is already the newest version.
libpangomm-1.4-1 is already the newest version.
libpangox-1.0-0 is already the newest version.
libpaper-utils is already the newest version.
libpaper1 is already the newest version.
libparse-debianchangelog-perl is already the newest version.
libpciaccess0 is already the newest version.
libpcsclite1 is already the newest version.
libpeas-1.0-0 is already the newest version.
libpeas-common is already the newest version.
libperlio-gzip-perl is already the newest version.
libplist1 is already the newest version.
libpocketsphinx1 is already the newest version.
libportaudio2 is already the newest version.
libprotobuf8 is already the newest version.
libproxy1 is already the newest version.
libproxy1-plugin-gsettings is already the newest version.
libproxy1-plugin-networkmanager is already the newest version.
libpython-stdlib is already the newest version.
libpyzy-1.0-0 is already the newest version.
libqmi-glib0 is already the newest version.
libqpdf13 is already the newest version.
libqt5feedback5 is already the newest version.
libqt5multimedia5 is already the newest version.
libqt5organizer5 is already the newest version.
libqt5positioning5 is already the newest version.
libqt5qml-graphicaleffects is already the newest version.
libqt5sensors5 is already the newest version.
libqt5svg5 is already the newest version.
libqt5webkit5 is already the newest version.
libqt5webkit5-qmlwebkitplugin is already the newest version.
libqtassistantclient4 is already the newest version.
libqtwebkit4 is already the newest version.
libraptor2-0 is already the newest version.
librasqal3 is already the newest version.
libraw1394-11 is already the newest version.
libraw9 is already the newest version.
librdf0 is already the newest version.
libreadline5 is already the newest version.
librest-0.7-0 is already the newest version.
librsvg2-2 is already the newest version.
librsvg2-common is already the newest version.
librsync1 is already the newest version.
libsamplerate0 is already the newest version.
libsbc1 is already the newest version.
libsecret-1-0 is already the newest version.
libsecret-common is already the newest version.
libsensors4 is already the newest version.
libsgutils2-2 is already the newest version.
libshout3 is already the newest version.
libsigc++-2.0-0c2a is already the newest version.
libsignon-extension1 is already the newest version.
libsignon-glib1 is already the newest version.
libsignon-plugins-common1 is already the newest version.
libsignon-qt5-1 is already the newest version.
libsm6 is already the newest version.
libsocket6-perl is already the newest version.
libsonic0 is already the newest version.
libsoup-gnome2.4-1 is already the newest version.
libsoup2.4-1 is already the newest version.
libspeechd2 is already the newest version.
libspeex1 is already the newest version.
libspeexdsp1 is already the newest version.
libsphinxbase1 is already the newest version.
libstartup-notification0 is already the newest version.
libsub-identify-perl is already the newest version.
libsub-name-perl is already the newest version.
libt1-5 is already the newest version.
libtag1-vanilla is already the newest version.
libtag1c2a is already the newest version.
libtalloc2 is already the newest version.
libtcl8.6 is already the newest version.
libtdb1 is already the newest version.
libtelepathy-farstream3 is already the newest version.
libtelepathy-glib0 is already the newest version.
libtelepathy-logger3 is already the newest version.
libtevent0 is already the newest version.
libtext-levenshtein-perl is already the newest version.
libthai-data is already the newest version.
libthai0 is already the newest version.
libtheora0 is already the newest version.
libtimedate-perl is already the newest version.
libtimezonemap1 is already the newest version.
libtk8.6 is already the newest version.
libtotem-plparser18 is already the newest version.
libtotem0 is already the newest version.
libtxc-dxtn-s2tc0 is already the newest version.
libunistring0 is already the newest version.
libunity-action-qt1 is already the newest version.
libunity-misc4 is already the newest version.
libunity-protocol-private0 is already the newest version.
libunity-scopes-json-def-desktop is already the newest version.
libunity-webapps0 is already the newest version.
libunity9 is already the newest version.
libunityvoice1 is already the newest version.
libupower-glib1 is already the newest version.
liburi-perl is already the newest version.
liburl-dispatcher1 is already the newest version.
libusbmuxd2 is already the newest version.
libutempter0 is already the newest version.
libuuid-perl is already the newest version.
libv4l-0 is already the newest version.
libv4lconvert0 is already the newest version.
libvisio-0.0-0 is already the newest version.
libvisual-0.4-0 is already the newest version.
libvisual-0.4-plugins is already the newest version.
libvorbis0a is already the newest version.
libvorbisenc2 is already the newest version.
libvorbisfile3 is already the newest version.
libvpx1 is already the newest version.
libwacom-common is already the newest version.
libwacom2 is already the newest version.
libwavpack1 is already the newest version.
libwayland-client0 is already the newest version.
libwayland-cursor0 is already the newest version.
libwayland-server0 is already the newest version.
libwebp5 is already the newest version.
libwebpmux1 is already the newest version.
libwhoopsie-preferences0 is already the newest version.
libwnck-common is already the newest version.
libwnck22 is already the newest version.
libwpd-0.9-9 is already the newest version.
libwpg-0.2-2 is already the newest version.
libwps-0.2-2 is already the newest version.
libwrap0 is already the newest version.
libx11-xcb1 is already the newest version.
libx86-1 is already the newest version.
libxapian22 is already the newest version.
libxaw7 is already the newest version.
libxcb-dri2-0 is already the newest version.
libxcb-dri3-0 is already the newest version.
libxcb-glx0 is already the newest version.
libxcb-icccm4 is already the newest version.
libxcb-image0 is already the newest version.
libxcb-present0 is already the newest version.
libxcb-randr0 is already the newest version.
libxcb-render-util0 is already the newest version.
libxcb-render0 is already the newest version.
libxcb-shape0 is already the newest version.
libxcb-shm0 is already the newest version.
libxcb-sync1 is already the newest version.
libxcb-util0 is already the newest version.
libxcb-xfixes0 is already the newest version.
libxcb-xkb1 is already the newest version.
libxcomposite1 is already the newest version.
libxcursor1 is already the newest version.
libxdamage1 is already the newest version.
libxft2 is already the newest version.
libxinerama1 is already the newest version.
libxkbcommon0 is already the newest version.
libxkbfile1 is already the newest version.
libxklavier16 is already the newest version.
libxmu6 is already the newest version.
libxp6 is already the newest version.
libxpm4 is already the newest version.
libxrandr2 is already the newest version.
libxres1 is already the newest version.
libxshmfence1 is already the newest version.
libxslt1.1 is already the newest version.
libxss1 is already the newest version.
libxt6 is already the newest version.
libxtst6 is already the newest version.
libxv1 is already the newest version.
libxvmc1 is already the newest version.
libxxf86dga1 is already the newest version.
libxxf86vm1 is already the newest version.
libyajl2 is already the newest version.
libyaml-tiny-perl is already the newest version.
libyelp0 is already the newest version.
libzeitgeist-1.0-1 is already the newest version.
libzephyr4 is already the newest version.
light-themes is already the newest version.
lintian is already the newest version.
linux-sound-base is already the newest version.
lp-solve is already the newest version.
make is already the newest version.
manpages-dev is already the newest version.
media-player-info is already the newest version.
memtest86+ is already the newest version.
mobile-broadband-provider-info is already the newest version.
mousetweaks is already the newest version.
mscompress is already the newest version.
mtools is already the newest version.
nautilus-sendto is already the newest version.
nautilus-share is already the newest version.
network-manager-pptp is already the newest version.
network-manager-pptp-gnome is already the newest version.
notify-osd is already the newest version.
obex-data-server is already the newest version.
obexd-client is already the newest version.
openprinting-ppds is already the newest version.
overlay-scrollbar is already the newest version.
overlay-scrollbar-gtk2 is already the newest version.
overlay-scrollbar-gtk3 is already the newest version.
p11-kit is already the newest version.
p11-kit-modules is already the newest version.
patchutils is already the newest version.
pcmciautils is already the newest version.
pkg-config is already the newest version.
plainbox-provider-checkbox is already the newest version.
plainbox-provider-resource-generic is already the newest version.
plainbox-secure-policy is already the newest version.
policykit-1-gnome is already the newest version.
policykit-desktop-privileges is already the newest version.
poppler-data is already the newest version.
pptp-linux is already the newest version.
printer-driver-c2esp is already the newest version.
printer-driver-foo2zjs is already the newest version.
printer-driver-foo2zjs-common is already the newest version.
printer-driver-gutenprint is already the newest version.
printer-driver-gutenprint set to manually installed.
printer-driver-min12xxw is already the newest version.
printer-driver-pnm2ppa is already the newest version.
printer-driver-ptouch is already the newest version.
printer-driver-pxljr is already the newest version.
printer-driver-sag-gdi is already the newest version.
python is already the newest version.
python-cairo is already the newest version.
python-chardet is already the newest version.
python-commandnotfound is already the newest version.
python-crypto is already the newest version.
python-cups is already the newest version.
python-dbus is already the newest version.
python-dbus-dev is already the newest version.
python-debian is already the newest version.
python-debtagshw is already the newest version.
python-defer is already the newest version.
python-dirspec is already the newest version.
python-gconf is already the newest version.
python-gdbm is already the newest version.
python-gnomekeyring is already the newest version.
python-gobject-2 is already the newest version.
python-gtk2 is already the newest version.
python-httplib2 is already the newest version.
python-imaging is already the newest version.
python-lockfile is already the newest version.
python-minimal is already the newest version.
python-notify is already the newest version.
python-ntdb is already the newest version.
python-oauthlib is already the newest version.
python-openssl is already the newest version.
python-pam is already the newest version.
python-pil is already the newest version.
python-piston-mini-client is already the newest version.
python-pycurl is already the newest version.
python-qt4 is already the newest version.
python-qt4-dbus is already the newest version.
python-renderpm is already the newest version.
python-reportlab is already the newest version.
python-reportlab-accel is already the newest version.
python-serial is already the newest version.
python-sip is already the newest version.
python-smbc is already the newest version.
python-talloc is already the newest version.
python-tdb is already the newest version.
python-twisted-bin is already the newest version.
python-twisted-core is already the newest version.
python-twisted-web is already the newest version.
python-ubuntu-sso-client is already the newest version.
python-xapian is already the newest version.
python-xdg is already the newest version.
python-zope.interface is already the newest version.
python3-brlapi is already the newest version.
python3-cairo is already the newest version.
python3-checkbox-ng is already the newest version.
python3-checkbox-support is already the newest version.
python3-crypto is already the newest version.
python3-debian is already the newest version.
python3-defer is already the newest version.
python3-feedparser is already the newest version.
python3-httplib2 is already the newest version.
python3-louis is already the newest version.
python3-mako is already the newest version.
python3-markupsafe is already the newest version.
python3-oauthlib is already the newest version.
python3-piston-mini-client is already the newest version.
python3-plainbox is already the newest version.
python3-pyatspi is already the newest version.
python3-pycurl is already the newest version.
python3-pyparsing is already the newest version.
python3-speechd is already the newest version.
python3-xdg is already the newest version.
python3-xkit is already the newest version.
qpdf is already the newest version.
qt-at-spi is already the newest version.
qtchooser is already the newest version.
qtdeclarative5-accounts-plugin is already the newest version.
qtdeclarative5-qtfeedback-plugin is already the newest version.
qtdeclarative5-ubuntu-ui-toolkit-plugin is already the newest version.
qtdeclarative5-unity-action-plugin is already the newest version.
remmina is already the newest version.
remmina-common is already the newest version.
remmina-plugin-rdp is already the newest version.
remmina-plugin-vnc is already the newest version.
rfkill is already the newest version.
rtkit is already the newest version.
seahorse is already the newest version.
session-migration is already the newest version.
sessioninstaller is already the newest version.
signon-keyring-extension is already the newest version.
signon-plugin-oauth2 is already the newest version.
signon-plugin-password is already the newest version.
signon-ui is already the newest version.
signond is already the newest version.
sni-qt is already the newest version.
software-center-aptdaemon-plugins is already the newest version.
sound-theme-freedesktop is already the newest version.
speech-dispatcher is already the newest version.
speech-dispatcher-audio-plugins is already the newest version.
sphinx-voxforge-hmm-en is already the newest version.
sphinx-voxforge-lm-en is already the newest version.
ssl-cert is already the newest version.
syslinux is already the newest version.
syslinux-common is already the newest version.
syslinux-legacy is already the newest version.
tcl is already the newest version.
tcl8.6 is already the newest version.
tcpd is already the newest version.
telepathy-haze is already the newest version.
telepathy-idle is already the newest version.
telepathy-indicator is already the newest version.
telepathy-logger is already the newest version.
telepathy-mission-control-5 is already the newest version.
telepathy-salut is already the newest version.
tk is already the newest version.
tk8.6 is already the newest version.
toshset is already the newest version.
totem is already the newest version.
totem-common is already the newest version.
totem-mozilla is already the newest version.
totem-plugins is already the newest version.
ttf-indic-fonts-core is already the newest version.
ttf-punjabi-fonts is already the newest version.
ttf-ubuntu-font-family is already the newest version.
ubuntu-artwork is already the newest version.
ubuntu-desktop is already the newest version.
ubuntu-extras-keyring is already the newest version.
ubuntu-mono is already the newest version.
ubuntu-settings is already the newest version.
ubuntu-sounds is already the newest version.
ubuntu-sso-client is already the newest version.
ubuntu-sso-client-qt is already the newest version.
ubuntu-system-service is already the newest version.
ubuntu-ui-toolkit-theme is already the newest version.
ubuntu-wallpapers is already the newest version.
ubuntu-wallpapers-trusty is already the newest version.
ubuntuone-client-data is already the newest version.
unity-asset-pool is already the newest version.
unity-control-center-signon is already the newest version.
unity-lens-applications is already the newest version.
unity-lens-files is already the newest version.
unity-lens-friends is already the newest version.
unity-lens-photos is already the newest version.
unity-lens-video is already the newest version.
unity-scope-audacious is already the newest version.
unity-scope-calculator is already the newest version.
unity-scope-chromiumbookmarks is already the newest version.
unity-scope-clementine is already the newest version.
unity-scope-colourlovers is already the newest version.
unity-scope-devhelp is already the newest version.
unity-scope-firefoxbookmarks is already the newest version.
unity-scope-gdrive is already the newest version.
unity-scope-gmusicbrowser is already the newest version.
unity-scope-gourmet is already the newest version.
unity-scope-guayadeque is already the newest version.
unity-scope-home is already the newest version.
unity-scope-manpages is already the newest version.
unity-scope-musique is already the newest version.
unity-scope-openclipart is already the newest version.
unity-scope-texdoc is already the newest version.
unity-scope-tomboy is already the newest version.
unity-scope-video-remote is already the newest version.
unity-scope-virtualbox is already the newest version.
unity-scope-yelp is already the newest version.
unity-scope-zotero is already the newest version.
unity-scopes-master-default is already the newest version.
unity-scopes-runner is already the newest version.
unity-voice-service is already the newest version.
unity-webapps-common is already the newest version.
unity-webapps-qml is already the newest version.
unity-webapps-service is already the newest version.
update-inetd is already the newest version.
upower is already the newest version.
usb-modeswitch is already the newest version.
usb-modeswitch-data is already the newest version.
usbmuxd is already the newest version.
vbetool is already the newest version.
vino is already the newest version.
wamerican is already the newest version.
whoopsie-preferences is already the newest version.
wireless-regdb is already the newest version.
wireless-tools is already the newest version.
wodim is already the newest version.
x11-apps is already the newest version.
x11-session-utils is already the newest version.
x11-utils is already the newest version.
x11-xfs-utils is already the newest version.
x11-xkb-utils is already the newest version.
x11-xserver-utils is already the newest version.
xbitmaps is already the newest version.
xcursor-themes is already the newest version.
xdg-user-dirs is already the newest version.
xdg-user-dirs-gtk is already the newest version.
xdiagnose is already the newest version.
xfonts-base is already the newest version.
xfonts-encodings is already the newest version.
xfonts-mathml is already the newest version.
xfonts-scalable is already the newest version.
xfonts-utils is already the newest version.
xinit is already the newest version.
xinput is already the newest version.
xorg-docs-core is already the newest version.
xserver-xorg-input-evdev is already the newest version.
xserver-xorg-input-mouse is already the newest version.
xserver-xorg-input-synaptics is already the newest version.
xserver-xorg-input-vmmouse is already the newest version.
xserver-xorg-input-wacom is already the newest version.
xserver-xorg-video-cirrus is already the newest version.
xserver-xorg-video-fbdev is already the newest version.
xserver-xorg-video-glamoregl is already the newest version.
xserver-xorg-video-mach64 is already the newest version.
xserver-xorg-video-mga is already the newest version.
xserver-xorg-video-modesetting is already the newest version.
xserver-xorg-video-neomagic is already the newest version.
xserver-xorg-video-nouveau is already the newest version.
xserver-xorg-video-qxl is already the newest version.
xserver-xorg-video-r128 is already the newest version.
xserver-xorg-video-s3 is already the newest version.
xserver-xorg-video-savage is already the newest version.
xserver-xorg-video-siliconmotion is already the newest version.
xserver-xorg-video-sis is already the newest version.
xserver-xorg-video-sisusb is already the newest version.
xserver-xorg-video-tdfx is already the newest version.
xserver-xorg-video-trident is already the newest version.
xserver-xorg-video-vesa is already the newest version.
xserver-xorg-video-vmware is already the newest version.
xterm is already the newest version.
xz-utils is already the newest version.
yelp is already the newest version.
yelp-xsl is already the newest version.
zenity is already the newest version.
zenity-common is already the newest version.
zip is already the newest version.
account-plugin-aim is already the newest version.
account-plugin-facebook is already the newest version.
account-plugin-flickr is already the newest version.
account-plugin-google is already the newest version.
account-plugin-jabber is already the newest version.
account-plugin-salut is already the newest version.
account-plugin-twitter is already the newest version.
account-plugin-windows-live is already the newest version.
account-plugin-yahoo is already the newest version.
activity-log-manager is already the newest version.
activity-log-manager-control-center is already the newest version.
app-install-data is already the newest version.
apport is already the newest version.
apport-gtk is already the newest version.
aptdaemon is already the newest version.
aptdaemon-data is already the newest version.
binutils is already the newest version.
bluez is already the newest version.
bluez-alsa is already the newest version.
compiz is already the newest version.
compiz-core is already the newest version.
compiz-gnome is already the newest version.
compiz-plugins-default is already the newest version.
cpp-4.8 is already the newest version.
cups is already the newest version.
cups-browsed is already the newest version.
cups-bsd is already the newest version.
cups-client is already the newest version.
cups-common is already the newest version.
cups-core-drivers is already the newest version.
cups-daemon is already the newest version.
cups-filters is already the newest version.
cups-filters set to manually installed.
cups-filters-core-drivers is already the newest version.
cups-ppdc is already the newest version.
cups-server-common is already the newest version.
dbus-x11 is already the newest version.
dnsmasq-base is already the newest version.
duplicity is already the newest version.
empathy is already the newest version.
empathy-common is already the newest version.
eog is already the newest version.
evince is already the newest version.
evince-common is already the newest version.
evolution-data-server is already the newest version.
evolution-data-server-common is already the newest version.
evolution-data-server-online-accounts is already the newest version.
file-roller is already the newest version.
firefox is already the newest version.
fontconfig is already the newest version.
fontconfig-config is already the newest version.
fonts-droid is already the newest version.
fonts-opensymbol is already the newest version.
gcc-4.8 is already the newest version.
gdb is already the newest version.
gdisk is already the newest version.
gettext is already the newest version.
ghostscript is already the newest version.
ghostscript-x is already the newest version.
gir1.2-appindicator3-0.1 is already the newest version.
gir1.2-dbusmenu-glib-0.4 is already the newest version.
gir1.2-ebook-1.2 is already the newest version.
gir1.2-ebookcontacts-1.2 is already the newest version.
gir1.2-edataserver-1.2 is already the newest version.
gir1.2-freedesktop is already the newest version.
gir1.2-gdkpixbuf-2.0 is already the newest version.
gir1.2-gnomebluetooth-1.0 is already the newest version.
gir1.2-gst-plugins-base-1.0 is already the newest version.
gir1.2-gstreamer-1.0 is already the newest version.
gir1.2-gtk-3.0 is already the newest version.
gir1.2-gudev-1.0 is already the newest version.
gir1.2-ibus-1.0 is already the newest version.
gir1.2-javascriptcoregtk-3.0 is already the newest version.
gir1.2-networkmanager-1.0 is already the newest version.
gir1.2-pango-1.0 is already the newest version.
gir1.2-rb-3.0 is already the newest version.
gir1.2-udisks-2.0 is already the newest version.
gir1.2-vte-2.90 is already the newest version.
gir1.2-webkit-3.0 is already the newest version.
gir1.2-wnck-3.0 is already the newest version.
glib-networking is already the newest version.
glib-networking-common is already the newest version.
glib-networking-services is already the newest version.
gnome-bluetooth is already the newest version.
gnome-calculator is already the newest version.
gnome-control-center-shared-data is already the newest version.
gnome-desktop3-data is already the newest version.
gnome-keyring is already the newest version.
gnome-session-bin is already the newest version.
gnome-session-common is already the newest version.
gnome-settings-daemon-schemas is already the newest version.
gnome-sudoku is already the newest version.
gstreamer1.0-alsa is already the newest version.
gstreamer1.0-plugins-base is already the newest version.
gstreamer1.0-plugins-base-apps is already the newest version.
gstreamer1.0-plugins-good is already the newest version.
gstreamer1.0-pulseaudio is already the newest version.
gstreamer1.0-tools is already the newest version.
gstreamer1.0-x is already the newest version.
gvfs is already the newest version.
gvfs-backends is already the newest version.
gvfs-bin is already the newest version.
gvfs-common is already the newest version.
gvfs-daemons is already the newest version.
gvfs-fuse is already the newest version.
gvfs-libs is already the newest version.
hardening-includes is already the newest version.
hplip-data is already the newest version.
hud is already the newest version.
ibus is already the newest version.
ibus-gtk is already the newest version.
ibus-gtk3 is already the newest version.
im-config is already the newest version.
indicator-session is already the newest version.
intel-gpu-tools is already the newest version.
iproute is already the newest version.
iputils-arping is already the newest version.
landscape-client-ui-install is already the newest version.
language-selector-gnome is already the newest version.
libaccount-plugin-generic-oauth is already the newest version.
libaccount-plugin-google is already the newest version.
libappindicator3-1 is already the newest version.
libarchive13 is already the newest version.
libasan0 is already the newest version.
libasprintf-dev is already the newest version.
libbluetooth3 is already the newest version.
libboost-date-time1.54.0 is already the newest version.
libboost-system1.54.0 is already the newest version.
libc-dev-bin is already the newest version.
libc6-dbg is already the newest version.
libc6-dev is already the newest version.
libcairo-gobject2 is already the newest version.
libcairo2 is already the newest version.
libcamel-1.2-45 is already the newest version.
libclutter-gtk-1.0-0 is already the newest version.
libcompizconfig0 is already the newest version.
libcups2 is already the newest version.
libcupscgi1 is already the newest version.
libcupsfilters1 is already the newest version.
libcupsimage2 is already the newest version.
libcupsmime1 is already the newest version.
libcupsppdc1 is already the newest version.
libcurl3 is already the newest version.
libdbusmenu-glib4 is already the newest version.
libdbusmenu-gtk3-4 is already the newest version.
libdbusmenu-gtk4 is already the newest version.
libdecoration0 is already the newest version.
libdpkg-perl is already the newest version.
libdrm-intel1 is already the newest version.
libdrm-nouveau2 is already the newest version.
libdrm-radeon1 is already the newest version.
libebackend-1.2-7 is already the newest version.
libebook-1.2-14 is already the newest version.
libebook-contacts-1.2-0 is already the newest version.
libecal-1.2-16 is already the newest version.
libedata-book-1.2-20 is already the newest version.
libedata-cal-1.2-23 is already the newest version.
libedataserver-1.2-18 is already the newest version.
libegl1-mesa is already the newest version.
libegl1-mesa-drivers is already the newest version.
libevdocument3-4 is already the newest version.
libevent-2.0-5 is already the newest version.
libevview3-3 is already the newest version.
libflac8 is already the newest version.
libfontconfig1 is already the newest version.
libfontembed1 is already the newest version.
libfreetype6 is already the newest version.
libgail-3-0 is already the newest version.
libgail-common is already the newest version.
libgail18 is already the newest version.
libgbm1 is already the newest version.
libgcc-4.8-dev is already the newest version.
libgdk-pixbuf2.0-0 is already the newest version.
libgdk-pixbuf2.0-common is already the newest version.
libgettextpo-dev is already the newest version.
libgettextpo0 is already the newest version.
libgexiv2-2 is already the newest version.
libgl1-mesa-dri is already the newest version.
libgl1-mesa-glx is already the newest version.
libglapi-mesa is already the newest version.
libgles2-mesa is already the newest version.
libglib2.0-bin is already the newest version.
libgnome-bluetooth11 is already the newest version.
libgnome-control-center1 is already the newest version.
libgnome-desktop-3-7 is already the newest version.
libgpgme11 is already the newest version.
libgphoto2-6 is already the newest version.
libgphoto2-l10n is already the newest version.
libgphoto2-port10 is already the newest version.
libgraphite2-3 is already the newest version.
libgs9 is already the newest version.
libgs9-common is already the newest version.
libgstreamer-plugins-base1.0-0 is already the newest version.
libgstreamer-plugins-good1.0-0 is already the newest version.
libgstreamer1.0-0 is already the newest version.
libgtk-3-0 is already the newest version.
libgtk-3-bin is already the newest version.
libgtk-3-common is already the newest version.
libgtk2.0-0 is already the newest version.
libgtk2.0-bin is already the newest version.
libgtk2.0-common is already the newest version.
libgudev-1.0-0 is already the newest version.
libgweather-3-6 is already the newest version.
libgweather-common is already the newest version.
libharfbuzz-icu0 is already the newest version.
libharfbuzz0b is already the newest version.
libhpmud0 is already the newest version.
libhud2 is already the newest version.
libhunspell-1.3-0 is already the newest version.
libibus-1.0-5 is already the newest version.
libicu52 is already the newest version.
libido3-0.1-0 is already the newest version.
libindicator3-7 is already the newest version.
libjasper1 is already the newest version.
libjavascriptcoregtk-3.0-0 is already the newest version.
libjbig0 is already the newest version.
libldb1 is already the newest version.
liblightdm-gobject-1-0 is already the newest version.
liblzo2-2 is already the newest version.
libmbim-glib0 is already the newest version.
libmetacity-private0a is already the newest version.
libminiupnpc8 is already the newest version.
libmm-glib0 is already the newest version.
libmtp-common is already the newest version.
libmtp-runtime is already the newest version.
libmtp9 is already the newest version.
libnautilus-extension1a is already the newest version.
libnettle4 is already the newest version.
libnm-glib-vpn1 is already the newest version.
libnm-glib4 is already the newest version.
libnm-gtk-common is already the newest version.
libnm-gtk0 is already the newest version.
libnm-util2 is already the newest version.
libnspr4 is already the newest version.
libnss3 is already the newest version.
libnss3-nssdb is already the newest version.
libnux-4.0-0 is already the newest version.
libnux-4.0-common is already the newest version.
libopenvg1-mesa is already the newest version.
liboxideqt-qmlplugin is already the newest version.
liboxideqtcore0 is already the newest version.
libp11-kit-gnome-keyring is already the newest version.
libpam-gnome-keyring is already the newest version.
libpango-1.0-0 is already the newest version.
libpango1.0-0 is already the newest version.
libpangocairo-1.0-0 is already the newest version.
libpangoft2-1.0-0 is already the newest version.
libpangoxft-1.0-0 is already the newest version.
libperl5.18 is already the newest version.
libpixman-1-0 is already the newest version.
libpolkit-agent-1-0 is already the newest version.
libpolkit-backend-1-0 is already the newest version.
libpoppler-glib8 is already the newest version.
libpoppler44 is already the newest version.
libpulse-mainloop-glib0 is already the newest version.
libpulse0 is already the newest version.
libpulsedsp is already the newest version.
libpurple-bin is already the newest version.
libpurple0 is already the newest version.
libpwquality-common is already the newest version.
libpwquality1 is already the newest version.
libpython2.7 is already the newest version.
libpython2.7-minimal is already the newest version.
libpython2.7-stdlib is already the newest version.
libpython3.4 is already the newest version.
libqt4-dbus is already the newest version.
libqt4-declarative is already the newest version.
libqt4-designer is already the newest version.
libqt4-help is already the newest version.
libqt4-network is already the newest version.
libqt4-opengl is already the newest version.
libqt4-script is already the newest version.
libqt4-scripttools is already the newest version.
libqt4-sql is already the newest version.
libqt4-sql-sqlite is already the newest version.
libqt4-svg is already the newest version.
libqt4-test is already the newest version.
libqt4-xml is already the newest version.
libqt4-xmlpatterns is already the newest version.
libqt5core5a is already the newest version.
libqt5dbus5 is already the newest version.
libqt5gui5 is already the newest version.
libqt5network5 is already the newest version.
libqt5opengl5 is already the newest version.
libqt5printsupport5 is already the newest version.
libqt5qml5 is already the newest version.
libqt5quick5 is already the newest version.
libqt5sql5 is already the newest version.
libqt5sql5-sqlite is already the newest version.
libqt5test5 is already the newest version.
libqt5widgets5 is already the newest version.
libqt5xml5 is already the newest version.
libqtcore4 is already the newest version.
libqtdbus4 is already the newest version.
libqtgui4 is already the newest version.
libreoffice-avmedia-backend-gstreamer is already the newest version.
libreoffice-base-core is already the newest version.
libreoffice-calc is already the newest version.
libreoffice-common is already the newest version.
libreoffice-core is already the newest version.
libreoffice-draw is already the newest version.
libreoffice-gnome is already the newest version.
libreoffice-gtk is already the newest version.
libreoffice-impress is already the newest version.
libreoffice-math is already the newest version.
libreoffice-ogltrans is already the newest version.
libreoffice-pdfimport is already the newest version.
libreoffice-presentation-minimizer is already the newest version.
libreoffice-style-human is already the newest version.
libreoffice-writer is already the newest version.
librhythmbox-core8 is already the newest version.
libsane is already the newest version.
libsane-common is already the newest version.
libsane-hpaio is already the newest version.
libsmbclient is already the newest version.
libsndfile1 is already the newest version.
libsnmp-base is already the newest version.
libsnmp30 is already the newest version.
libspectre1 is already the newest version.
libspice-server1 is already the newest version.
libssh-4 is already the newest version.
libsystemd-journal0 is already the newest version.
libthumbnailer0 is already the newest version.
libtiff5 is already the newest version.
libudisks2-0 is already the newest version.
libufe-xidgetter0 is already the newest version.
libunity-control-center1 is already the newest version.
libunity-core-6.0-9 is already the newest version.
libunity-gtk2-parser0 is already the newest version.
libunity-gtk3-parser0 is already the newest version.
libupstart1 is already the newest version.
libvncserver0 is already the newest version.
libvte-2.90-9 is already the newest version.
libvte-2.90-common is already the newest version.
libwayland-egl1-mesa is already the newest version.
libwbclient0 is already the newest version.
libwebkitgtk-3.0-0 is already the newest version.
libwebkitgtk-3.0-common is already the newest version.
libwhoopsie0 is already the newest version.
libwmf0.2-7 is already the newest version.
libwmf0.2-7-gtk is already the newest version.
libwnck-3-0 is already the newest version.
libwnck-3-common is already the newest version.
libxatracker2 is already the newest version.
libxfixes3 is already the newest version.
libxfont1 is already the newest version.
libxi6 is already the newest version.
libxrender1 is already the newest version.
libzeitgeist-2.0-0 is already the newest version.
lightdm is already the newest version.
linux-libc-dev is already the newest version.
mcp-account-manager-uoa is already the newest version.
metacity-common is already the newest version.
modemmanager is already the newest version.
nautilus is already the newest version.
nautilus-data is already the newest version.
nautilus-sendto-empathy is already the newest version.
network-manager is already the newest version.
network-manager-gnome is already the newest version.
notify-osd-icons is already the newest version.
nux-tools is already the newest version.
onboard is already the newest version.
onboard-data is already the newest version.
oneconf is already the newest version.
oneconf-common is already the newest version.
patch is already the newest version.
plymouth-label is already the newest version.
plymouth-theme-ubuntu-logo is already the newest version.
pm-utils is already the newest version.
policykit-1 is already the newest version.
poppler-utils is already the newest version.
pulseaudio is already the newest version.
pulseaudio-module-bluetooth is already the newest version.
pulseaudio-module-x11 is already the newest version.
pulseaudio-utils is already the newest version.
python-apt is already the newest version.
python-aptdaemon is already the newest version.
python-aptdaemon.gtk3widgets is already the newest version.
python-cupshelpers is already the newest version.
python-gi is already the newest version.
python-gi-cairo is already the newest version.
python-gobject is already the newest version.
python-ibus is already the newest version.
python-ldb is already the newest version.
python-libxml2 is already the newest version.
python-lxml is already the newest version.
python-oneconf is already the newest version.
python-pexpect is already the newest version.
python-pkg-resources is already the newest version.
python-samba is already the newest version.
python-six is already the newest version.
python-zeitgeist is already the newest version.
python2.7 is already the newest version.
python2.7-minimal is already the newest version.
python3-apport is already the newest version.
python3-aptdaemon is already the newest version.
python3-aptdaemon.gtk3widgets is already the newest version.
python3-aptdaemon.pkcompat is already the newest version.
python3-chardet is already the newest version.
python3-gi-cairo is already the newest version.
python3-lxml is already the newest version.
python3-oneconf is already the newest version.
python3-pkg-resources is already the newest version.
python3-problem-report is already the newest version.
python3-requests is already the newest version.
python3-six is already the newest version.
python3-software-properties is already the newest version.
python3-uno is already the newest version.
python3-urllib3 is already the newest version.
qdbus is already the newest version.
qtcore4-l10n is already the newest version.
qtdeclarative5-dialogs-plugin is already the newest version.
qtdeclarative5-localstorage-plugin is already the newest version.
qtdeclarative5-privatewidgets-plugin is already the newest version.
qtdeclarative5-qtquick2-plugin is already the newest version.
qtdeclarative5-ubuntu-ui-extras-browser-plugin is already the newest version.
qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets is already the newest version.
qtdeclarative5-window-plugin is already the newest version.
rhythmbox is already the newest version.
rhythmbox-data is already the newest version.
rhythmbox-mozilla is already the newest version.
rhythmbox-plugin-cdrecorder is already the newest version.
rhythmbox-plugin-magnatune is already the newest version.
rhythmbox-plugin-zeitgeist is already the newest version.
rhythmbox-plugins is already the newest version.
samba-common is already the newest version.
samba-common-bin is already the newest version.
samba-libs is already the newest version.
sane-utils is already the newest version.
shotwell is already the newest version.
shotwell-common is already the newest version.
simple-scan is already the newest version.
smbclient is already the newest version.
software-center is already the newest version.
software-properties-common is already the newest version.
software-properties-gtk is already the newest version.
ssh-askpass-gnome is already the newest version.
system-config-printer-common is already the newest version.
system-config-printer-gnome is already the newest version.
system-config-printer-udev is already the newest version.
t1utils is already the newest version.
telepathy-gabble is already the newest version.
thunderbird is already the newest version.
thunderbird-gnome-support is already the newest version.
transmission-common is already the newest version.
transmission-gtk is already the newest version.
ubuntu-docs is already the newest version.
ubuntu-drivers-common is already the newest version.
ubuntu-release-upgrader-gtk is already the newest version.
ubuntu-session is already the newest version.
udisks2 is already the newest version.
unattended-upgrades is already the newest version.
unity is already the newest version.
unity-control-center is already the newest version.
unity-greeter is already the newest version.
unity-gtk-module-common is already the newest version.
unity-gtk2-module is already the newest version.
unity-gtk3-module is already the newest version.
unity-lens-music is already the newest version.
unity-scope-musicstores is already the newest version.
unity-services is already the newest version.
unity-settings-daemon is already the newest version.
uno-libs3 is already the newest version.
unzip is already the newest version.
update-manager is already the newest version.
update-notifier is already the newest version.
update-notifier-common is already the newest version.
ure is already the newest version.
usb-creator-common is already the newest version.
usb-creator-gtk is already the newest version.
webaccounts-extension-common is already the newest version.
webapp-container is already the newest version.
webbrowser-app is already the newest version.
whoopsie is already the newest version.
wpasupplicant is already the newest version.
x11-common is already the newest version.
xdg-utils is already the newest version.
xorg is already the newest version.
xserver-common is already the newest version.
xserver-xorg is already the newest version.
xserver-xorg-core is already the newest version.
xserver-xorg-input-all is already the newest version.
xserver-xorg-video-all is already the newest version.
xserver-xorg-video-ati is already the newest version.
xserver-xorg-video-intel is already the newest version.
xserver-xorg-video-openchrome is already the newest version.
xserver-xorg-video-radeon is already the newest version.
xul-ext-ubufox is already the newest version.
xul-ext-unity is already the newest version.
xul-ext-webaccounts is already the newest version.
xul-ext-websites-integration is already the newest version.
zeitgeist is already the newest version.
zeitgeist-core is already the newest version.
zeitgeist-datahub is already the newest version.
Suggested packages:
  hplip-gui hplip-doc system-config-printer
The following packages will be REMOVED:
  oxideqt-codecs-extra
The following NEW packages will be installed:
  bluez-cups hplip indicator-printers oxideqt-codecs printer-driver-hpcups
  printer-driver-postscript-hp printer-driver-splix
0 upgraded, 7 newly installed, 1 to remove and 5 not upgraded.
Remv oxideqt-codecs-extra [1.13.6-0ubuntu0.14.04.1] [liboxideqtcore0:amd64 liboxideqtquick0:amd64 ]
Inst oxideqt-codecs (1.13.6-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Inst bluez-cups (4.101-0ubuntu13.1 Ubuntu:14.04/trusty-updates [amd64])
Inst printer-driver-hpcups (3.14.3-0ubuntu3.4 Ubuntu:14.04/trusty-updates [amd64])
Inst hplip (3.14.3-0ubuntu3.4 Ubuntu:14.04/trusty-updates [amd64])
Inst printer-driver-postscript-hp (3.14.3-0ubuntu3.4 Ubuntu:14.04/trusty-updates [all])
Inst printer-driver-splix (2.0.0+svn315-2fakesync1 Ubuntu:14.04/trusty [amd64])
Inst indicator-printers (0.1.7+14.04.20140527-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
Conf oxideqt-codecs (1.13.6-0ubuntu0.14.04.1 Ubuntu:14.04/trusty-updates [amd64])
Conf bluez-cups (4.101-0ubuntu13.1 Ubuntu:14.04/trusty-updates [amd64])
Conf printer-driver-hpcups (3.14.3-0ubuntu3.4 Ubuntu:14.04/trusty-updates [amd64])
Conf hplip (3.14.3-0ubuntu3.4 Ubuntu:14.04/trusty-updates [amd64])
Conf printer-driver-postscript-hp (3.14.3-0ubuntu3.4 Ubuntu:14.04/trusty-updates [all])
Conf printer-driver-splix (2.0.0+svn315-2fakesync1 Ubuntu:14.04/trusty [amd64])

Conf indicator-printers (0.1.7+14.04.20140527-0ubuntu1 Ubuntu:14.04/trusty-updates [amd64])
```[COLOR=#000000][FONT=Ubuntu Mono]

[/FONT][/COLOR]It seems to want to install mostly printer related stuff. I executed the command without the -s and it did complete successfully. 

The other command (**[COLOR=#000000][FONT=Ubuntu Mono]sudo dpkg --configure -a[/FONT][/COLOR]**) did not return any output. I rebooted the computer for sure, but the software-updated still hangs, unfortunately. 

Indeed, I do run a 64-bit OS. However, I don't know how to identify a rogue 32-bit package either, I'm afraid...

---

### Post by richterbg on 2016-04-11
Phew, I fixed it. It seems that the problem was related to a Dolphin Emulator installation. The 32-bit gcc stuff seemed to be related to this installation. I did run:

```
 history | grep add-apt-repository  369  sudo add-apt-repository ppa:nilarimogard/webupd8
  886  sudo add-apt-repository ppa:dolphin-emu/ppa
  890  sudo add-apt-repository ppa:dolphin-emu/gcc-for-dolphin
 1228  history | grep add-apt-repository

```

then ppa-purge for the two dolphin-emu ppa-s.

now the software updater runs normally. 

Frankly, I wouldn't have made it without your guidance and thoughts!

---

### Post by kansasnoob on 2016-04-11
> **richterbg said:**
> Phew, I fixed it. It seems that the problem was related to a Dolphin Emulator installation. The 32-bit gcc stuff seemed to be related to this installation. I did run:

```
 history | grep add-apt-repository  369  sudo add-apt-repository ppa:nilarimogard/webupd8
  886  sudo add-apt-repository ppa:dolphin-emu/ppa
  890  sudo add-apt-repository ppa:dolphin-emu/gcc-for-dolphin
 1228  history | grep add-apt-repository

```

then ppa-purge for the two dolphin-emu ppa-s.

now the software updater runs normally. 

Frankly, I wouldn't have made it without your guidance and thoughts!

Far out :guitar:

I hope we didn't break your print driver.

---

### Post by richterbg on 2016-04-11
Nah, the printer is working normally. This thought crossed my mind too, but I managed to print some stuff after the printer driver update. It was fun :)

---

