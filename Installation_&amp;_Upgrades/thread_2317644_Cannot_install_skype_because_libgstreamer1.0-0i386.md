---
title: "Cannot install skype because libgstreamer1.0-0:i386"
date: 2016-03-18
forum: Installation &amp; Upgrades
---

### Post by Daniyal_Javani on 2016-03-18
When I want to install skype, it depends libgstreamer1.0-0:i386 but when I  want to install this apt-get force me to remove many packages, can you  please help me.
I think my problem is:
```
$ apt-cache policy libgstreamer1.0-0
libgstreamer1.0-0:
  Installed: 1.5.91+git20150921.ebd2748c-0ubuntu1~14.04~ricotz0
  Candidate: 1.5.91+git20150921.ebd2748c-0ubuntu1~14.04~ricotz0
  Version table:
 *** 1.5.91+git20150921.ebd2748c-0ubuntu1~14.04~ricotz0 0
        100 /var/lib/dpkg/status
     1.2.4-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     1.2.3-1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
```

Anyway, this is my try to install skype:
```
$ sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 skype : Depends: skype-bin
E: Unable to correct problems, you have held broken packages.
```
```
$ sudo apt-get install skype-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 skype-bin:i386 : Depends: libqtwebkit4:i386 (>= 2.2~2011week36) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```
```
$ sudo apt-get install libqtwebkit4:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libqtwebkit4:i386 : Depends: libgstreamer-plugins-base1.0-0:i386 (>= 1.0.0) but it is not going to be installed
                     Depends: libgstreamer1.0-0:i386 (>= 1.0.0) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```
```
$ sudo apt-get install libgstreamer-plugins-base1.0-0:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgstreamer-plugins-base1.0-0:i386 : Depends: libgstreamer1.0-0:i386 (>= 1.5.91) but it is not going to be installed
                                       Recommends: gstreamer1.0-plugins-base:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

```
$ sudo apt-get install libgstreamer1.0-0:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  accountsservice-ubuntu-schemas accountsservice-ubuntu-touch-schemas
  gir1.2-gconf-2.0 glade2script gnome-control-center-data
  gsettings-ubuntu-touch-schemas lame launchpad-getkeys libcontent-hub0
  libgtkglext1 libofono-qt1 libonline-accounts-client1 libopencv-core2.4
  libopencv-highgui2.4 libopencv-imgproc2.4 libqgsttools-p1 libqt4-gui
  libqt5multimedia5-plugins libqt5multimediaquick-p5 libqt5multimediawidgets5
  libqt5systeminfo5 libsystemsettings1 libtbb2 libtidy-0.99-0
  libubuntu-download-manager-client0 libubuntu-download-manager-common0
  libubuntu-download-manager-priv0 libubuntuoneauth-2.0-0 pastebinit ppa-purge
  python-keyring python-launchpadlib python-lazr.restfulclient python-lazr.uri
  python-netifaces python-oauth python-psutil python-pyudev
  python-secretstorage python-wadllib python3-gnupg
  qtdeclarative5-folderlistmodel-plugin qtdeclarative5-qtmultimedia-plugin
  qtdeclarative5-systeminfo-plugin qtdeclarative5-ubuntu-content0.1
  suru-icon-theme system-image-common system-image-dbus tidy
  ubuntu-download-manager ubuntu-mobile-icons ubuntu-touch-sounds
  ubuntuone-credentials-common whoopsie-preferences xclip
Use 'apt-get autoremove' to remove them.
Suggested packages:
  gstreamer1.0-tools:i386 gstreamer1.0-plugins-base:i386
The following packages will be REMOVED:
  anki apturl boot-repair boot-sav boot-sav-extra brasero-cdrkit checkbox-gui
  cheese copyq cuttlefish gimp gir1.2-gst-plugins-base-1.0
  gir1.2-gstreamer-1.0 gir1.2-rb-3.0 gir1.2-totem-1.0 gir1.2-webkit-3.0 gitg
  gnome-user-guide gnome-video-effects goldendict gstreamer1.0-alsa
  gstreamer1.0-clutter gstreamer1.0-fluendo-mp3 gstreamer1.0-libav
  gstreamer1.0-nice gstreamer1.0-plugins-bad gstreamer1.0-plugins-base
  gstreamer1.0-plugins-base-apps gstreamer1.0-plugins-good
  gstreamer1.0-plugins-ugly gstreamer1.0-pulseaudio gstreamer1.0-tools
  gstreamer1.0-x gufw indicator-bluetooth kde-runtime kdelibs5-plugins
  kubuntu-debug-installer libaccount-plugin-generic-oauth libbrasero-media3-1
  libcheese-gtk23 libcheese7 libclutter-gst-2.0-0 libdmapsharing-3.0-2
  libfarstream-0.2-2 libgstreamer-plugins-bad1.0-0
  libgstreamer-plugins-base1.0-0 libgstreamer-plugins-good1.0-0
  libgstreamer1.0-0 libkactivities-bin libkdewebkit5 libokularcore4 libplasma3
  libqt5webkit5 libqt5webkit5-qmlwebkitplugin libqtwebkit4
  libreoffice-avmedia-backend-gstreamer librhythmbox-core9
  libtelepathy-farstream3 libthumbnailer0 libtotem0 libwebkit2gtk-4.0-37
  libwebkitgtk-1.0-0 libwebkitgtk-3.0-0 libyelp0 mediascanner2.0
  nautilus-share nixnote2 okular okular-extra-backends phonon
  phonon-backend-gstreamer phonon-backend-gstreamer1.0
  plasma-scriptengine-javascript python-qt4 qapt-batch
  qtdeclarative5-ubuntu-settings-components
  qtdeclarative5-ubuntu-thumbnailer0.1
  qtdeclarative5-ubuntu-ui-extras-browser-plugin
  qtdeclarative5-ubuntu-ui-toolkit-plugin sessioninstaller shotwell
  signon-plugin-oauth2 signon-ui smtube software-center thumbnailer-service
  ubuntu-docs ubuntu-release-upgrader-gtk ubuntu-sso-client-qt ubuntu-tweak
  unity-control-center unity-scope-mediascanner2 unity8 update-manager
  update-notifier y-ppa-manager yad yelp zenity
The following NEW packages will be installed:
  libgstreamer1.0-0:i386
0 upgraded, 1 newly installed, 100 to remove and 257 not upgraded.
Need to get 585 kB of archives.
After this operation, 614 MB disk space will be freed.
Do you want to continue? [Y/n] n
Abort.
```

---

### Post by $yl9pAR%t on 2016-03-18
Download Skype client from Skype website and try to install it using gdebi. I did it this way on Ubuntu 16.04, 14.04, 12.04 and perhaps even 10.04 (not sure). I never had any poblems installing this way.

---

### Post by Daniyal_Javani on 2016-03-19
> **mefisto888 said:**
> Download Skype client from Skype website and try to install it using gdebi. I did it this way on Ubuntu 16.04, 14.04, 12.04 and perhaps even 10.04 (not sure). I never had any poblems installing this way.

Same story!
```
$ sudo gdebi Data/Downloads/aria2/skype-ubuntu-precise_4.3.0.37-1_i386.deb 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Building data structures... Done 
Building data structures... Done 
This package is uninstallable
Cannot install 'libqtwebkit4:i386'
```

---

### Post by tomdkat on 2016-03-19
I'm in the same boat as Daniyal_Javani.  I want to install Skype on my mom's Ubuntu 14.04 (64-bit) system and I keep running into these same dependency issues.   

Peace...

---

### Post by $yl9pAR%t on 2016-03-19
@[COLOR=#000000]tomdkat

I am not sure if you are both in the same boat, perhaps I am wrong, but it seems OP did some experiments with his OS and he uses experimental PPA.
Check in terminal:

```
[/COLOR][COLOR=#000000][FONT=Ubuntu Mono]apt-cache policy libgstreamer1.0-0[/FONT][/COLOR][COLOR=#000000]
```

If you will get different result than OP, try some tips from this link:

[http://askubuntu.com/questions/504689/cant-install-skype-4-3-on-ubuntu-14-04-64-bit](http://askubuntu.com/questions/504689/cant-install-skype-4-3-on-ubuntu-14-04-64-bit)
[/COLOR]

---

### Post by ian-weisser on 2016-03-19
The system is trying to warn you about a version conflict.
Each package specifies a range of versions that it will accept for each dependency. You have instructed your system to install a package that requires a dependency version that is out-of-range for your version of Ubuntu.
Version conflicts are usually caused by (unsupported) packages from PPAs and other non-Ubuntu sources.

Adding *more* non-Ubuntu software is unlikely to solve the problem.

These are usually very easy to fix.
The normal way to resolve a version conflict is to uninstall ALL of the non-Ubuntu packages and disable/delete those sources.
Then install the tested and compatible versions of the software packages from the Ubuntu repositories.
If you still need non-Ubuntu packages, add each source one at a time and test for upgrade errors after each non-Ubunto package install. If you get errors, remove those packages and delete that source.

---

