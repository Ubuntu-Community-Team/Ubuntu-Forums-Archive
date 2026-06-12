---
title: "Can't install Wine on a reasonably fresh install of Ubuntu 12.04.3 amd64"
date: 2014-02-26
forum: Installation &amp; Upgrades
---

### Post by desconocido on 2014-02-26
These are the actions I took before trying to install Wine:

```
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get install gnome-session-fallback
sudo apt-get remove unity unity-2d
sudo apt-get install libglew1.5 libimlib2 libmotif4 libnspr4-0d
sudo dpkg -i libmozjs2d_1.9.1.16-20_amd64.deb 
sudo apt-get install openjdk-7-jre
[I]The following packages have unmet dependencies.
 openjdk-7-jre : Depends: openjdk-7-jre-headless (= 7u51-2.4.4-0ubuntu0.12.04.2) but it is not going to be installed
                 Depends: libatk-wrapper-java-jni (>= 0.30.4-0ubuntu2) but it is not going to be installed[/I]
sudo apt-get -f install
[I]The following NEW packages will be installed
  ca-certificates-java default-jre default-jre-headless icedtea-6-jre-cacao icedtea-6-jre-jamvm icedtea-netx
  icedtea-netx-common java-common libatk-wrapper-java libatk-wrapper-java-jni libjpeg62 libnss3-1d openjdk-6-jre
  openjdk-6-jre-headless openjdk-6-jre-lib ttf-dejavu-extra tzdata-java
The following packages will be upgraded:
  libnss3[/I]
sudo apt-get install libjpeg62
sudo dpkg -i freewrl_1.22.10-1_amd64.deb
*Install epson-inkjet-printer-nx420_1.0.0-1lsb3.2_amd64.deb 		(using ubuntu software center)*

```

Then I used ubuntu software center to install Wine. This gave me an error. So I went back to apt-get:

```
$ sudo apt-get install wine
[sudo] password for bob: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 wine : Depends: wine1.4 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

```
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  indicator-printers python-cupshelpers gir1.2-ubuntuoneui-3.0 system-config-printer-gnome unity-lens-video
  unity-scope-video-remote unity-scope-musicstores unity-common python-gnomekeyring libunity-misc4 unity-lens-music
  avahi-utils unity-2d-spread rhythmbox-ubuntuone unity-lens-files python-smbc system-config-printer-udev
  unity-2d-shell libubuntuoneui-3.0-1 unity-asset-pool nux-tools system-config-printer-common unity-lens-applications
  python-gconf
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 126 not upgraded.
```

```
$ sudo apt-get install wine1.4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 wine1.4 : Depends: wine1.4-i386 (= 1.4-0ubuntu4)
           Recommends: ttf-mscorefonts-installer but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

```
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  indicator-printers python-cupshelpers gir1.2-ubuntuoneui-3.0 system-config-printer-gnome unity-lens-video
  unity-scope-video-remote unity-scope-musicstores unity-common python-gnomekeyring libunity-misc4 unity-lens-music
  avahi-utils unity-2d-spread rhythmbox-ubuntuone unity-lens-files python-smbc system-config-printer-udev
  unity-2d-shell libubuntuoneui-3.0-1 unity-asset-pool nux-tools system-config-printer-common unity-lens-applications
  python-gconf
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 126 not upgraded.
```

```

sudo add-apt-repository ppa:ubuntu-wine/ppa
You are about to add the following PPA to your system:
 Welcome to the Wine Team PPA.  Here you can get the latest available Wine betas for every supported version of Ubuntu.  This PPA is managed by Scott Ritchie and Maarten Lankhorst.
 More info: https://launchpad.net/~ubuntu-wine/+archive/ppa
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpy5f45b/secring.gpg' created
gpg: keyring `/tmp/tmpy5f45b/pubring.gpg' created
gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpy5f45b/trustdb.gpg: trustdb created
gpg: key F9CB8DB0: public key "Launchpad PPA for Ubuntu Wine Team" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
```


```
$ sudo apt-get update

$ sudo apt-get install wine1.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 wine : Depends: wine1.4 but it is not going to be installed
 wine1.6 : Depends: wine1.6-amd64 (= 1:1.6.1-0ubuntu1~ppa1~precise1)
           Depends: binfmt-support (>= 1.1.2)
           Depends: wine1.6-i386 (= 1:1.6.1-0ubuntu1~ppa1~precise1)
           Recommends: gnome-exe-thumbnailer but it is not going to be installed or
                       kde-runtime but it is not going to be installed
           Recommends: fonts-droid but it is not going to be installed
           Recommends: ttf-mscorefonts-installer but it is not going to be installed
           Recommends: fonts-horai-umefont but it is not going to be installed
           Recommends: fonts-unfonts-core but it is not going to be installed
           Recommends: winbind
           Recommends: winetricks but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```


```
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gir1.2-notify-0.7 libopencc1 syslinux indicator-printers libmtp9 gedit-common gir1.2-rb-3.0 gir1.2-gstreamer-0.10
  libgtksourceview-3.0-0 libdmapsharing-3.0-2 rhythmbox-data gir1.2-gmenu-3.0 intel-gpu-tools libraw5 libdiscid0
  libmtp-runtime gir1.2-indicate-0.7 libgpod-common ibus-gtk3 gir1.2-gnomekeyring-1.0 liblouis-data syslinux-legacy
  libcrypt-passwdmd5-perl ibus-gtk unity-common ubuntu-extras-keyring libgexiv2-1 syslinux-common libunity-misc4
  librhythmbox-core5 libgpod4 unity-lens-music avahi-utils unity-2d-spread gir1.2-totem-1.0 gir1.2-appindicator3-0.1
  libindicator7 command-not-found-data unity-lens-files gir1.2-totem-plparser-1.0 liblouis2 gir1.2-gtksource-3.0
  libgtksourceview-3.0-common gir1.2-gst-plugins-base-0.10 libgtkspell-3-0 gir1.2-atspi-2.0 ibus-pinyin-db-android
  im-switch unity-2d-shell gir1.2-gudev-1.0 libappindicator1 libexiv2-11 gir1.2-wnck-3.0 libmtp-common python-gdbm
  app-install-data thunderbird-globalmenu media-player-info unity-asset-pool gir1.2-launchpad-integration-3.0
  protobuf-compiler libmusicbrainz3-6 nux-tools unity-lens-applications libprotoc7 librsync1
  activity-log-manager-common libmusicbrainz5-0 librhythmbox-core6
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  binfmt-support fonts-unfonts-core gir1.2-totem-1.0 imagemagick imagemagick-common libcdt4 libclutter-1.0-0
  libclutter-gst-1.0-0 libclutter-gtk-1.0-0 libclutter-imcontext-0.1-0 libcluttergesture-0.0.2-0 libcogl-pango0
  libcogl9 libdrm-nouveau2 libdrm-radeon1 libdrm2 libgl1-mesa-glx-lts-raring libglapi-mesa-lts-raring libgraph4
  libgvc5 libhpmud0 libilmbase6 libjpeg-turbo8 liblqr-1-0 libmagickcore4 libmagickcore4-extra libmagickwand4
  libmusicbrainz5-0 libmx-1.0-2 libnetpbm10 libopenexr6 libpathplan4 libpython2.7 librhythmbox-core6 libssl1.0.0
  libtotem0 libwbclient0 netpbm printer-driver-hpijs python2.7 python2.7-minimal samba-common smbclient thunderbird
  thunderbird-globalmenu thunderbird-gnome-support totem totem-common totem-mozilla unrar
Suggested packages:
  imagemagick-doc autotrace curl enscript ffmpeg gimp gnuplot grads hp2xx html2ps libwmf-bin mplayer povray radiance
  texlive-base-bin transfig ufraw-batch hpijs-ppds hplip-doc python2.7-doc cifs-utils ttf-lyx
  gstreamer0.10-plugins-ugly gstreamer0.10-plugins-bad gstreamer0.10-ffmpeg
Recommended packages:
  libclutter-1.0-common libcogl-common
The following packages will be REMOVED
  activity-log-manager-control-center alacarte apport apport-gtk apt-xapian-index aptdaemon apturl apturl-common bluez
  bluez-alsa bluez-gstreamer checkbox checkbox-qt command-not-found deja-dup duplicity epson-inkjet-printer-nx420
  firefox firefox-gnome-support gdb gedit gir1.2-ubuntuoneui-3.0 gnome-bluetooth gnome-control-center gnome-orca
  gnome-sudoku gnome-user-share gwibber gwibber-service gwibber-service-facebook gwibber-service-identica
  gwibber-service-twitter hplip ibus ibus-pinyin ibus-table indicator-datetime indicator-power jockey-common
  jockey-gtk landscape-client-ui-install language-selector-common language-selector-gnome launchpad-integration
  libgwibber-gtk2 libgwibber2 libpurple-bin libpurple0 libreoffice-emailmerge libsasl2-modules libsyncdaemon-1.0-1
  libubuntuoneui-3.0-1 lsb lsb-core lsb-cxx lsb-desktop lsb-graphics lsb-printing lsb-release nautilus-share
  nvidia-common onboard oneconf printer-driver-postscript-hp python-appindicator python-apport python-apt
  python-aptdaemon python-aptdaemon.gtk3widgets python-aptdaemon.pkcompat python-brlapi python-cairo python-chardet
  python-configglue python-crypto python-cups python-cupshelpers python-dateutil python-dbus python-debian
  python-debtagshw python-defer python-dirspec python-egenix-mxdatetime python-egenix-mxtools python-gconf python-gi
  python-gi-cairo python-gmenu python-gnomekeyring python-gnupginterface python-gobject python-gobject-2
  python-gst0.10 python-gtk2 python-httplib2 python-ibus python-imaging python-keyring python-launchpadlib
  python-lazr.restfulclient python-lazr.uri python-libproxy python-libxml2 python-louis python-mako python-markupsafe
  python-notify python-oauth python-openssl python-packagekit python-pam python-pexpect python-piston-mini-client
  python-problem-report python-protobuf python-pyatspi2 python-pycurl python-pyinotify python-renderpm
  python-reportlab python-reportlab-accel python-serial python-simplejson python-smbc python-software-properties
  python-speechd python-twisted-bin python-twisted-core python-twisted-names python-twisted-web
  python-ubuntu-sso-client python-ubuntuone-client python-ubuntuone-control-panel python-ubuntuone-storageprotocol
  python-uno python-virtkey python-wadllib python-xapian python-xdg python-xkit python-zeitgeist python-zope.interface
  rhythmbox rhythmbox-mozilla rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist
  rhythmbox-plugins rhythmbox-ubuntuone sessioninstaller shotwell software-center software-center-aptdaemon-plugins
  software-properties-common software-properties-gtk system-config-printer-common system-config-printer-gnome
  system-config-printer-udev telepathy-haze totem-plugins ubuntu-minimal ubuntu-sso-client ubuntu-sso-client-gtk
  ubuntu-standard ubuntu-system-service ubuntuone-client ubuntuone-client-gnome ubuntuone-control-panel
  ubuntuone-couch ubuntuone-installer ufw unattended-upgrades unity-lens-video unity-scope-musicstores
  unity-scope-video-remote update-manager update-manager-core update-notifier update-notifier-common
  usb-creator-common usb-creator-gtk wine xdiagnose xul-ext-ubufox zeitgeist zeitgeist-core zeitgeist-datahub
The following NEW packages will be installed
  binfmt-support fonts-unfonts-core imagemagick imagemagick-common libcdt4 libclutter-1.0-0 libclutter-gst-1.0-0
  libclutter-gtk-1.0-0 libclutter-imcontext-0.1-0 libcluttergesture-0.0.2-0 libcogl-pango0 libcogl9 libgraph4 libgvc5
  libilmbase6 liblqr-1-0 libmagickcore4 libmagickcore4-extra libmagickwand4 libmusicbrainz5-0 libmx-1.0-2 libnetpbm10
  libopenexr6 libpathplan4 librhythmbox-core6 netpbm unrar
The following packages will be upgraded:
  gir1.2-totem-1.0 libdrm-nouveau2 libdrm-radeon1 libdrm2 libgl1-mesa-glx-lts-raring libglapi-mesa-lts-raring
  libhpmud0 libjpeg-turbo8 libpython2.7 libssl1.0.0 libtotem0 libwbclient0 printer-driver-hpijs python2.7
  python2.7-minimal samba-common smbclient thunderbird thunderbird-globalmenu thunderbird-gnome-support totem
  totem-common totem-mozilla
23 upgraded, 27 newly installed, 188 to remove and 75 not upgraded.
1 not fully installed or removed.
Need to get 83.4 MB of archives.
After this operation, 114 MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

```

```
$ sudo apt-get install wine1.5 wine1.5-i386:i386 wine1.5-amd64

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 wine : Depends: wine1.4 but it is not going to be installed
 wine1.5 : Depends: wine1.6 but it is not going to be installed
 wine1.5-amd64 : Depends: wine1.6-amd64
 wine1.5-i386:i386 : Depends: wine1.6-i386:i386
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

```
$ sudo apt-get install wine1.6 wine1.6-i386:i386 wine1.6-amd64
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 wine : Depends: wine1.4 but it is not going to be installed
 wine1.6 : Depends: binfmt-support (>= 1.1.2)
           Recommends: gnome-exe-thumbnailer but it is not going to be installed or
                       kde-runtime but it is not going to be installed
           Recommends: fonts-droid but it is not going to be installed
           Recommends: ttf-mscorefonts-installer but it is not going to be installed
           Recommends: fonts-horai-umefont but it is not going to be installed
           Recommends: fonts-unfonts-core but it is not going to be installed
           Recommends: winbind
           Recommends: winetricks but it is not going to be installed
 wine1.6-amd64 : Depends: libmpg123-0 (>= 1.6.2) but it is not going to be installed
                 Depends: libopenal1 (>= 1:1.13) but it is not going to be installed
                 Recommends: libcapi20-3 but it is not going to be installed
                 Recommends: libosmesa6 but it is not going to be installed
                 Recommends: unixodbc
                 Recommends: wine-gecko2.21 but it is not going to be installed
                 Recommends: wine-mono0.0.8 but it is not going to be installed
 wine1.6-i386:i386 : Depends: libasound2:i386 (>= 1.0.23) but it is not going to be installed
                     Depends: libc6:i386 (>= 2.12) but it is not going to be installed
                     Depends: libgl1-mesa-glx:i386 or
                              libgl1:i386
                     Depends: libglib2.0-0:i386 (>= 2.12.0) but it is not going to be installed
                     Depends: libglu1-mesa:i386 but it is not going to be installed or
                              libglu1:i386
                     Depends: libgphoto2-2:i386 (>= 2.4.10.1) but it is not going to be installed
                     Depends: libgphoto2-port0:i386 (>= 2.4.10.1) but it is not going to be installed
                     Depends: libgstreamer-plugins-base0.10-0:i386 (>= 0.10.22) but it is not going to be installed
                     Depends: libgstreamer0.10-0:i386 (>= 0.10.26) but it is not going to be installed
                     Depends: liblcms1:i386 (>= 1.15-1) but it is not going to be installed
                     Depends: libldap-2.4-2:i386 (>= 2.4.7) but it is not going to be installed
                     Depends: libmpg123-0:i386 (>= 1.6.2) but it is not going to be installed
                     Depends: libopenal1:i386 (>= 1:1.13) but it is not going to be installed
                     Depends: libpulse0:i386 (>= 1:0.99.1) but it is not going to be installed
                     Depends: libx11-6:i386 but it is not going to be installed
                     Depends: libxext6:i386 but it is not going to be installed
                     Depends: libxml2:i386 (>= 2.7.4) but it is not going to be installed
                     Depends: zlib1g:i386 (>= 1:1.1.4) but it is not going to be installed
                     Depends: libncurses5:i386 but it is not going to be installed
                     Recommends: libasound2-plugins:i386 but it is not going to be installed
                     Recommends: libcapi20-3:i386 but it is not going to be installed
                     Recommends: libcups2:i386 but it is not going to be installed
                     Recommends: libdbus-1-3:i386 but it is not going to be installed
                     Recommends: libfontconfig1:i386 but it is not going to be installed or
                                 libfontconfig:i386
                     Recommends: libfreetype6:i386 but it is not going to be installed
                     Recommends: libgif4:i386 but it is not going to be installed
                     Recommends: libgnutls26:i386 but it is not going to be installed
                     Recommends: libjpeg8:i386 but it is not going to be installed
                     Recommends: libosmesa6:i386 but it is not going to be installed
                     Recommends: libpng12-0:i386 but it is not going to be installed
                     Recommends: libsane:i386 but it is not going to be installed
                     Recommends: libtiff4:i386 but it is not going to be installed
                     Recommends: libv4l-0:i386 but it is not going to be installed
                     Recommends: libxcomposite1:i386 but it is not going to be installed
                     Recommends: libxcursor1:i386 but it is not going to be installed
                     Recommends: libxi6:i386 but it is not going to be installed
                     Recommends: libxinerama1:i386 but it is not going to be installed
                     Recommends: libxrandr2:i386 but it is not going to be installed
                     Recommends: libxrender1:i386 but it is not going to be installed
                     Recommends: libxslt1.1:i386 but it is not going to be installed
                     Recommends: libxt6:i386 but it is not going to be installed
                     Recommends: libxxf86vm1:i386 but it is not going to be installed
                     Recommends: unixodbc:i386
                     Recommends: wine-gecko2.21:i386 but it is not going to be installed
                     Recommends: wine-mono0.0.8:i386
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```
```
$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 wine : Depends: wine1.6 but it is not going to be installed or
                 wine1.7 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

Not keen to delete 188 packages - it didn't work for me before. Any ideas? Thanks in advance.

When apt-get says it has "held broken packages", is there any way to tell it to forget about them?

---

### Post by phidia on 2014-03-03
See if the steps [within this thread]("http://askubuntu.com/questions/204840/dependency-error-while-installing-wine") will work for you.

---

### Post by desconocido on 2014-03-04
> **phidia said:**
> See if the steps [within this thread]("http://askubuntu.com/questions/204840/dependency-error-while-installing-wine") will work for you.

Thanks, but I have finally managed to solve it a different way - see my post at [http://ubuntuforums.org/showthread.php?t=2208261&page=2&p=12946625#post12946625]("http://ubuntuforums.org/showthread.php?t=2208261&page=2&p=12946625#post12946625")

---

