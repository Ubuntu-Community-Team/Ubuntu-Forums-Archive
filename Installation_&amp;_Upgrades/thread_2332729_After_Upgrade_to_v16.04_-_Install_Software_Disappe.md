---
title: "After Upgrade to v16.04 - Install Software Disappeared?"
date: 2016-08-03
forum: Installation &amp; Upgrades
---

### Post by Rick St. George on 2016-08-03
On two machines, upgraded to UbuntuStudio v16.04 and Xubuntu v16.04 and Software Center disappeared. Since the Upgrade REMOVED Office and other Apps such as PulseAudio, How do we get back ability to INSTALL Software?

Thanks!
Rick

---

### Post by Rick St. George on 2016-08-03
Found this - "Ubuntu Software Centre has been replaced by Gnome Software (re-branded Ubuntu software) and its software catalogue is still under construction. And we do need the partner repositories enabled."
Here; [https://ubuntuforums.org/showthread.php?t=2321818&highlight=install+software+installer](https://ubuntuforums.org/showthread.php?t=2321818&highlight=install+software+installer)

But we don't have this either.

---

### Post by QDR06VV9 on 2016-08-03
What dose it say after running these
```
sudo apt-get install -f 
sudo apt-get update 
sudo apt-get install software-center 
```
And Do not forget about synaptic.
```
sudo apt install synaptic
```

---

### Post by Rick St. George on 2016-08-03
```

stephen@stephen-evo-5723:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libcuda1-352-updates nvidia-libopencl1-352-updates vcdimager
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
stephen@stephen-evo-5723:~$ sudo apt-get update
Get:1 http://download.virtualbox.org/virtualbox/debian xenial InRelease [7,894 B]
Ign:2 http://download.bitdefender.com/repos/deb bitdefender InRelease          
Hit:3 http://download.bitdefender.com/repos/deb bitdefender Release            
Ign:1 http://download.virtualbox.org/virtualbox/debian xenial InRelease  
Hit:4 http://archive.ubuntu.com/ubuntu xenial InRelease                  
Hit:5 http://ppa.launchpad.net/jfi/ppa/ubuntu xenial InRelease           
Hit:7 http://archive.ubuntu.com/ubuntu xenial-updates InRelease         
Hit:8 http://ppa.launchpad.net/pipelight/stable/ubuntu xenial InRelease 
Get:9 http://archive.ubuntu.com/ubuntu xenial-security InRelease [94.5 kB]
Hit:10 http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu xenial InRelease 
Hit:11 http://ppa.launchpad.net/ubuntu-sdk-team/ppa/ubuntu xenial InRelease    
Hit:12 http://ppa.launchpad.net/webupd8team/java/ubuntu xenial InRelease       
Hit:13 https://deb.opera.com/opera-stable stable InRelease
Fetched 102 kB in 1s (80.3 kB/s)
Reading package lists... Done
W: GPG error: http://download.virtualbox.org/virtualbox/debian xenial InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A2F683C52980AECF
W: The repository 'http://download.virtualbox.org/virtualbox/debian xenial InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: http://download.bitdefender.com/repos/deb/dists/bitdefender/Release.gpg: Signature by key 639ADD458616BD06A1B55F9CA373FB480EC4FE05 uses weak digest algorithm (SHA1)
stephen@stephen-evo-5723:~$ sudo apt autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libcuda1-352-updates nvidia-libopencl1-352-updates vcdimager
0 upgraded, 0 newly installed, 3 to remove and 11 not upgraded.
After this operation, 29.6 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 257396 files and directories currently installed.)
Removing libcuda1-352-updates (352.63-0ubuntu0.14.04.1) ...
Removing nvidia-libopencl1-352-updates (352.63-0ubuntu0.14.04.1) ...
Removing vcdimager (0.7.24+dfsg-0.1ubuntu2) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Processing triggers for man-db (2.7.5-1) ...
stephen@stephen-evo-5723:~$ sudo apt-get install software-center
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package software-center is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'software-center' has no installation candidate

```

---

### Post by QDR06VV9 on 2016-08-03
Well the only thing I can offer right now is 
  Do not forget about synaptic.
          ```
sudo apt install synaptic gdebi
```
I was under the impression that the package manager was fixed..but I guess not.

---

### Post by Rick St. George on 2016-08-03
```

stephen@stephen-evo-5723:~$ sudo apt install synaptic gdebi
[sudo] password for stephen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package gdebi is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'synaptic' has no installation candidate
E: Package 'gdebi' has no installation candidate


```

---

### Post by QDR06VV9 on 2016-08-03
I am sure you have updated...lets see what your repo list is like
```
mousepad /etc/apt/sources.list
```
Or use the native text editor

---

### Post by Rick St. George on 2016-08-03
Don't have Mousepad, used SCITE. Here is the output!

```

# deb cdrom:[Ubuntu-Studio 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.1)]/ trusty main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu xenial main restricted
deb-src http://archive.ubuntu.com/ubuntu xenial main restricted #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb-src http://archive.ubuntu.com/ubuntu xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://archive.ubuntu.com/ubuntu xenial-security main restricted
deb-src http://archive.ubuntu.com/ubuntu xenial-security main restricted #Added by software-properties

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
## deb http://archive.canonical.com/ubuntu trusty partner
## deb-src http://archive.canonical.com/ubuntu trusty partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
deb http://archive.ubuntu.com/ubuntu xenial-updates main restricted


```


Also changed in Repository from "trusty" to "xenial", but it did not fully work. See above output in Post #4.

---

### Post by QDR06VV9 on 2016-08-03
Just to be clear...this is supposed to be 16.04 Xenial Right?

---

### Post by howefield on 2016-08-03
Have a look at the Software and Updates application, and check that the relevant repositories are selected.

---

### Post by QDR06VV9 on 2016-08-03
Must have of had a hicup in the upgrade.
Here is a new list you can just copy and paste in removing the old one as root.
```
#------------------------------------------------------------------------------#
#                            OFFICIAL UBUNTU REPOS                             #
#------------------------------------------------------------------------------#


###### Ubuntu Main Repos
deb http://....archive.ubuntu.com/ubuntu/ xenial main restricted universe multiverse 
deb-src http://....archive.ubuntu.com/ubuntu/ xenial main restricted universe multiverse 

###### Ubuntu Update Repos
deb http://....archive.ubuntu.com/ubuntu/ xenial-security main restricted universe multiverse 
deb http://....archive.ubuntu.com/ubuntu/ xenial-updates main restricted universe multiverse 
deb http://....archive.ubuntu.com/ubuntu/ xenial-proposed main restricted universe multiverse 
deb http://....archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse 
deb-src http://....archive.ubuntu.com/ubuntu/ xenial-security main restricted universe multiverse 
deb-src http://....archive.ubuntu.com/ubuntu/ xenial-updates main restricted universe multiverse 
# deb-src http://....archive.ubuntu.com/ubuntu/ xenial-proposed main restricted universe multiverse 
deb-src http://....archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse 

###### Ubuntu Partner Repo
# deb http://archive.canonical.com/ubuntu xenial partner
# deb-src http://archive.canonical.com/ubuntu xenial partner


```
If you go with this you will have to run
```
sudo apt-get update && sudo apt-get upgrade -y && sudo apt-get dist-upgrade -y
```
And if any errors paste them back here.

---

### Post by Rick St. George on 2016-08-03
Right 'runrickus', ... upgraded to v16.04 LTS Xenial.

'howefield', Why would I open access to untrusted sources?

---

### Post by QDR06VV9 on 2016-08-03
See Post #11

---

### Post by Rick St. George on 2016-08-03
Seemed to work, except what was reported at the bottom. See Below;

```

stephen@stephen-evo-5723:~$ sudo apt-get update && sudo apt-get upgrade -y && sudo apt-get dist-upgrade -y
Get:1 http://download.virtualbox.org/virtualbox/debian xenial InRelease [7,894 B]
Ign:2 http://download.bitdefender.com/repos/deb bitdefender InRelease          
Hit:3 http://download.bitdefender.com/repos/deb bitdefender Release            
Hit:4 http://ppa.launchpad.net/jfi/ppa/ubuntu xenial InRelease           
Hit:5 http://archive.ubuntu.com/ubuntu xenial InRelease                  
Ign:1 http://download.virtualbox.org/virtualbox/debian xenial InRelease
Get:7 http://archive.ubuntu.com/ubuntu xenial-security InRelease [94.5 kB]
Hit:8 http://ppa.launchpad.net/pipelight/stable/ubuntu xenial InRelease        
Hit:9 http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu xenial InRelease  
Hit:10 http://ppa.launchpad.net/ubuntu-sdk-team/ppa/ubuntu xenial InRelease    
Hit:11 http://ppa.launchpad.net/webupd8team/java/ubuntu xenial InRelease       
Get:12 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [95.7 kB]
Get:13 http://archive.ubuntu.com/ubuntu xenial-proposed InRelease [247 kB]
Get:14 http://archive.ubuntu.com/ubuntu xenial-backports InRelease [92.2 kB]
Get:15 http://archive.ubuntu.com/ubuntu xenial/universe Sources [7,728 kB]
Get:16 http://archive.ubuntu.com/ubuntu xenial/multiverse Sources [179 kB]     
Get:17 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages [7,532 kB]
Get:18 http://archive.ubuntu.com/ubuntu xenial/universe i386 Packages [7,512 kB]
Get:19 http://archive.ubuntu.com/ubuntu xenial/universe Translation-en [4,354 kB]
Get:20 http://archive.ubuntu.com/ubuntu xenial/multiverse amd64 Packages [144 kB]
Get:21 http://archive.ubuntu.com/ubuntu xenial/multiverse i386 Packages [140 kB]
Get:22 http://archive.ubuntu.com/ubuntu xenial/multiverse Translation-en [106 kB]
Get:23 http://archive.ubuntu.com/ubuntu xenial-security/universe Sources [8,948 B]
Get:24 http://archive.ubuntu.com/ubuntu xenial-security/multiverse Sources [728 B]
Get:25 http://archive.ubuntu.com/ubuntu xenial-security/universe amd64 Packages [36.5 kB]
Hit:26 https://deb.opera.com/opera-stable stable InRelease                     
Get:27 http://archive.ubuntu.com/ubuntu xenial-security/universe i386 Packages [36.5 kB]
Get:28 http://archive.ubuntu.com/ubuntu xenial-security/universe Translation-en [22.0 kB]
Get:29 http://archive.ubuntu.com/ubuntu xenial-security/multiverse amd64 Packages [1,176 B]
Get:30 http://archive.ubuntu.com/ubuntu xenial-security/multiverse i386 Packages [1,344 B]
Get:31 http://archive.ubuntu.com/ubuntu xenial-security/multiverse Translation-en [628 B]
Get:32 http://archive.ubuntu.com/ubuntu xenial-updates/universe Sources [85.2 kB]
Get:33 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse Sources [3,220 B]
Get:34 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [300 kB]
Get:35 http://archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [297 kB]
Get:36 http://archive.ubuntu.com/ubuntu xenial-updates/universe Translation-en [101 kB]
Get:37 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 Packages [5,488 B]
Get:38 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse i386 Packages [4,280 B]
Get:39 http://archive.ubuntu.com/ubuntu xenial-updates/multiverse Translation-en [2,428 B]
Get:40 http://archive.ubuntu.com/ubuntu xenial-proposed/main amd64 Packages [91.8 kB]
Get:41 http://archive.ubuntu.com/ubuntu xenial-proposed/main i386 Packages [89.0 kB]
Get:42 http://archive.ubuntu.com/ubuntu xenial-proposed/main Translation-en [34.2 kB]
Get:43 http://archive.ubuntu.com/ubuntu xenial-proposed/universe amd64 Packages [43.6 kB]
Get:44 http://archive.ubuntu.com/ubuntu xenial-proposed/universe i386 Packages [43.6 kB]
Get:45 http://archive.ubuntu.com/ubuntu xenial-proposed/universe Translation-en [22.5 kB]
Get:46 http://archive.ubuntu.com/ubuntu xenial-proposed/multiverse amd64 Packages [1,460 B]
Get:47 http://archive.ubuntu.com/ubuntu xenial-proposed/multiverse i386 Packages [1,460 B]
Get:48 http://archive.ubuntu.com/ubuntu xenial-proposed/multiverse Translation-en [752 B]
Get:49 http://archive.ubuntu.com/ubuntu xenial-backports/main Sources [1,400 B]
Get:50 http://archive.ubuntu.com/ubuntu xenial-backports/universe Sources [800 B]
Get:51 http://archive.ubuntu.com/ubuntu xenial-backports/main amd64 Packages [1,540 B]
Get:52 http://archive.ubuntu.com/ubuntu xenial-backports/main i386 Packages [1,544 B]
Get:53 http://archive.ubuntu.com/ubuntu xenial-backports/main Translation-en [1,484 B]
Get:54 http://archive.ubuntu.com/ubuntu xenial-backports/universe amd64 Packages [1,000 B]
Get:55 http://archive.ubuntu.com/ubuntu xenial-backports/universe i386 Packages [1,000 B]
Get:56 http://archive.ubuntu.com/ubuntu xenial-backports/universe Translation-en [584 B]
Fetched 29.5 MB in 21s (1,367 kB/s)                                            
Reading package lists... Done
W: GPG error: http://download.virtualbox.org/virtualbox/debian xenial InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A2F683C52980AECF
W: The repository 'http://download.virtualbox.org/virtualbox/debian xenial InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: http://download.bitdefender.com/repos/deb/dists/bitdefender/Release.gpg: Signature by key 639ADD458616BD06A1B55F9CA373FB480EC4FE05 uses weak digest algorithm (SHA1)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  gstreamer0.10-plugins-bad-multiverse libfaac0 libintl-perl
  libpod-plainer-perl lsb-cxx lsb-desktop lsb-graphics lsb-languages
  lsb-multimedia
Use 'sudo apt autoremove' to remove them.
The following packages have been kept back:
  argyll audacious-plugins audacity audacity-data cabextract codeblocks
  codeblocks-common csladspa csound darktable debugedit exo-utils
  ffmpeg2theora ffmpegthumbnailer filezilla filezilla-common gem gem-extra
  gem-plugin-gmerlin gem-plugin-lqt gem-plugin-magick gem-plugin-v4l2 gimp
  gimp-data gimp-plugin-registry gnome-icon-theme gnome-icon-theme-symbolic
  gstreamer1.0-libav gstreamer1.0-plugins-ugly hydrogen libaacs0 libastro1
  libaubio4 libav-tools libavcodec-extra libcodeblocks0 libcsound64-6.0
  libepub0 libexo-1-0 libgarcon-1-0 libgimp2.0 libgksu2-0 libgmerlin-avdec1
  libjpeg-progs libjpeg-turbo-progs libmlt++3 libmlt6 libqca2
  libqca2-plugin-ossl libquicktime2 librpm3 librpmbuild3 libthunarx-2-0 libva1
  libxfce4ui-1-0 libxfce4ui-2-0 libxfce4ui-utils libxfce4util-bin
  libxfcegui4-4 libxine2 libxine2-bin libxine2-ffmpeg libxine2-misc-plugins
  libxine2-plugins libxine2-x linux-headers-lowlatency linux-image-lowlatency
  linux-lowlatency lmms marble-plugins melt mencoder mplayer musescore
  musescore-soundfont-gm mypaint oxygen-icon-theme phatch phatch-cli psensor
  psensor-common python-debianbts python-enum python-matplotlib python-mlt
  python-pyexiv2 python-reportbug python-soappy qsynth reportbug ristretto rpm
  rpm-common rpm2cpio scribus smplayer sooperlooper stk thunar thunar-data
  thunar-volman transcode ttf-alee ttf-ancient-fonts ttf-georgewilliams
  ttf-radisnoir ubuntu-dev-tools ubuntustudio-audio ubuntustudio-controls
  ubuntustudio-default-settings ubuntustudio-font-meta ubuntustudio-video
  vinagre xfce4-appfinder xfce4-cpugraph-plugin xfce4-dict
  xfce4-fsguard-plugin xfce4-indicator-plugin xfce4-mailwatch-plugin
  xfce4-mount-plugin xfce4-netload-plugin xfce4-notes xfce4-notes-plugin
  xfce4-notifyd xfce4-panel xfce4-places-plugin xfce4-power-manager
  xfce4-power-manager-data xfce4-quicklauncher-plugin xfce4-screenshooter
  xfce4-session xfce4-settings xfce4-smartbookmark-plugin
  xfce4-systemload-plugin xfce4-terminal xfce4-verve-plugin
  xfce4-weather-plugin xfconf xfdesktop4 xfdesktop4-data xfwm4 xjadeo
  xserver-xephyr yoshimi
The following packages will be upgraded:
  a2jmidid aeolus alacarte alien alsa-tools alsa-tools-gui amb-plugins
  android-tools-adb android-tools-fastboot apparmor apparmor-easyprof asunder
  audacious-plugins-data autotalent bleachbit blender-data bluefish
  bluefish-data bluefish-plugins calf-plugins calligra-data caps catfish
  chromium-codecs-ffmpeg-extra click-reviewers-tools csound-data csound-utils
  cyclist dcraw debian-archive-keyring debian-keyring desktop-base drumkv1
  dssi-host-jack dssi-utils dvd+rw-tools dvdauthor elementary-icon-theme
  entangle exiftran exiv2 fil-plugins fluidsynth fonts-beteckna fonts-lyx
  fonts-sil-andika fonts-sil-charis fonts-sil-doulos fonts-sil-gentium
  fonts-tuffy foo-yc20 fslint gcalctool geany geany-common gem-doc ghostess
  gimp-data-extras gimp-gmic gimp-ufraw gir1.2-javascriptcoregtk-3.0
  gir1.2-unity-5.0 gir1.2-webkit-3.0 gksu gmidimonitor gnome-color-manager
  gnome-system-tools gnome-time-admin growisofs grub-common grub-pc
  grub-pc-bin grub2-common gstreamer0.10-plugins-base gstreamer1.0-fluendo-mp3
  gufw guile-1.8 guile-1.8-libs hydrogen-drumkits icoutils
  invada-studio-plugins-ladspa invada-studio-plugins-lv2 ir.lv2 jack-capture
  jconvolver jconvolver-config-files k3b-extrathemes kate-data
  kde-runtime-data kdenlive-data krita-data lame language-selector-common
  language-selector-gnome less liba52-0.7.4 libakonadiprotocolinternals1
  libapparmor-perl libapparmor1 libattica0.4 libaudclient2 libaudiofile1
  libbabl-0.1-0 libbaloocore4 libbluray1 libbs2b0 libcdaudio1 libcddb2
  libclxclient3 libcolord-gtk1 libcwiid1 libdc1394-22 libdca0
  libdirectfb-1.2-9 libdlrestrictions1 libdv-bin libdvdnav4 libdvdread4
  libegl1-mesa libenca0 libexo-common libexo-helpers libfaac0 libfaad2
  libflickcurl0 libflite1 libfltk1.1 libfluidsynth1 libgarcon-common libgavl1
  libgbm1 libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libgles2-mesa libgme0
  libgoocanvas-common libgoocanvas3 libgstreamer-plugins-base0.10-0
  libgstreamer0.10-0 libgtk-vnc-2.0-0 libgtkglext1 libgtkimageview0 libguess1
  libgvnc-1.0-0 libid3tag0 libimage-exiftool-perl libimlib2 libintl-perl
  libiptcdata0 libiso9660-8 libjavascriptcoregtk-1.0-0
  libjavascriptcoregtk-3.0-0 libjpeg62 libkactivities6 libkate1 libkdcraw-data
  libkdecore5 libkdeui5 libkeybinder0 libkldap4 libkresources4
  liblavfile-2.1-0 liblavjpeg-2.1-0 liblavplay-2.1-0 liblensfun-data
  liblensfun0 liblightdm-gobject-1-0 liblilv-0-0 liblo7 liblrdf0 libltc11
  libmimic0 libmjpegutils-2.1-0 libmlt-data libmms0 libmodplug1 libmowgli2
  libmp3lame0 libmpcdec6 libmpeg2-4 libmpeg2encpp-2.1-0 libmpg123-0
  libmplex2-2.1-0 libmxml1 libnm-gtk-common libnm-gtk0 libnma-common libnma0
  libntrack-qt4-1 libntrack0 libofa0 liboggkate1 liboobs-1-5 libopenal-data
  libopenal1 libopencore-amrnb0 libopencore-amrwb0 libphonon4
  libpod-plainer-perl libqmobipocket1 libqtwebkit4 libraptor1 librarian0
  librpmio3 libsbsms10 libschroedinger-1.0-0 libserd-0-0 libslv2-9 libsoprano4
  libsord-0-0 libsox-fmt-alsa libsox-fmt-base libsox2 libsoxr0 libspandsp2
  libspnav0 libsqlite0 libsratom-0-0 libsuil-0-0 libtbb2 libtcl8.5
  libtext-unidecode-perl libtiff-tools libtk8.5 libtumbler-1-0 libtwolame0
  libunique-1.0-0 libunity-protocol-private0 libunity-scopes-json-def-desktop
  libunity9 libupnp6 libva-glx1 libva-x11-1 libvcdinfo0 libvirtodbc0
  libvte-common libvte9 libwayland-egl1-mesa libwebkitgtk-1.0-0
  libwebkitgtk-1.0-common libwebkitgtk-3.0-0 libwebkitgtk-3.0-common
  libwildmidi-config libwildmidi1 libwnck-common libwnck22 libxatracker2
  libxfce4ui-common libxfce4util-common libxfconf-0-2 libxine2-doc
  libxvidcore4 libzbar0 libzvbi-common libzvbi0 lightdm lightdm-gtk-greeter
  lilypond lilypond-data lilypond-doc lilypond-doc-html lilypond-doc-pdf
  linux-firmware linux-libc-dev lm-sensors lmms-common lsb lsb-core
  lsb-invalid-mta lsb-printing lsb-security marble-data mcp-plugins mda-lv2
  menu mesa-utils mjpegtools mjpegtools-gtk mudita24 musescore-common
  mypaint-data network-manager-gnome normalize-audio ntpdate
  ntrack-module-libnl-0 openshot-doc openssh-client osspd osspd-pulseaudio
  pd-chaos pd-csound pd-cyclone pd-ggee pd-iemambi pd-iemnet pd-osc
  pd-unauthorized pd-zexy phablet-tools phasex phonon phonon-backend-gstreamer
  phonon-backend-gstreamer-common puredata puredata-core puredata-dev
  puredata-doc puredata-extra puredata-gui puredata-utils pybootchartgui
  python-debian python-distro-info python-editobj python-fpconst
  python-gobject python-gst-1.0 python-hachoir-core python-hachoir-metadata
  python-hachoir-parser python-imaging python-lzma python-matplotlib-data
  python-notify python-pyexiv2-doc python-pygoocanvas python-sqlite
  python-wxversion python3-apparmor python3-distupgrade python3-libapparmor
  python3-software-properties qasconfig qashctl qasmixer qastools-common
  qemu-user-static qmidiarp qmidiroute rarian-compat rawtherapee-data
  recordmydesktop rev-plugins rtirq-init rubberband-cli rubberband-ladspa
  samplv1 scite slv2-doc smplayer-themes software-properties-common
  software-properties-gtk songwrite soprano-daemon sox swh-lv2 swh-plugins
  synfig-examples synthv1 system-tools-backends t1-xfree86-nonfree tap-plugins
  tcl8.5 texinfo thunar-archive-plugin timidity timidity-daemon tk8.5
  transcode-doc ttf-lyx ttf-mscorefonts-installer ttf-summersby
  ttf-xfree86-nonfree ttf-xfree86-nonfree-syriac tumbler tumbler-common
  twolame ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk
  ubuntu-restricted-addons ubuntu-restricted-extras ubuntustudio-audio-plugins
  ubuntustudio-graphics ubuntustudio-icon-theme ubuntustudio-lightdm-theme
  ubuntustudio-look ubuntustudio-menu ubuntustudio-photography
  ubuntustudio-publishing ubuntustudio-wallpapers unrar vco-plugins
  virtualbox-5.0 virtuoso-minimal virtuoso-opensource-6.1-bin
  virtuoso-opensource-6.1-common vorbis-tools wah-plugins wavpack xcftools
  xfce4-taskmanager xfce4-volumed xscreensaver xscreensaver-data
  xscreensaver-gl xserver-common xserver-xorg-core xubuntu-icon-theme
  yoshimi-data zita-ajbridge zita-at1 zita-lrx zita-mu1 zita-rev1
415 upgraded, 0 newly installed, 0 to remove and 144 not upgraded.
Need to get 562 MB of archives.
After this operation, 129 MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  virtualbox-5.0
E: There were unauthenticated packages and -y was used without --allow-unauthenticated


```

Is this anything to be concerned about?

Thanks! 'runrickus'

---

### Post by QDR06VV9 on 2016-08-03
Nothing to be worried about just a key signing Warning is all.
You can try to add the keys by way of
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 639ADD458616BD06A1B55F9CA373FB480EC4FE05
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A2F683C52980AECF
```
And after you still may see uses weak digest algorithm (SHA1) warnings Ubuntu has a new policy on this and it looks like the responsible Maintainers have not yet conformed.

---

### Post by Rick St. George on 2016-08-03
Rec'd the following in Software Updater - "Failed to Download Repository Information"

```

W:GPG error: http://download.virtualbox.org/virtualbox/debian xenial InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A2F683C52980AECF, W:The repository 'http://download.virtualbox.org/virtualbox/debian xenial InRelease' is not signed., W:Data from such a repository can't be authenticated and is therefore potentially dangerous to use., W:See apt-secure(8) manpage for repository creation and user configuration details., W:The repository 'http://download.bitdefender.com/repos/deb BitDefender Release' does not have a Release file., W:Data from such a repository can't be authenticated and is therefore potentially dangerous to use., W:See apt-secure(8) manpage for repository creation and user configuration details., E:Failed to fetch http://download.bitdefender.com/repos/deb/dists/BitDefender/non-free/binary-amd64/Packages  404  Not Found, E:Some index files failed to download. They have been ignored, or old ones used instead.

```


Any suggestion? Or is this one you were referring to at the bottom of Post #15?
Thanks!

---

### Post by QDR06VV9 on 2016-08-03
> **Rick St. George said:**
> Rec'd the following in Software Updater - "Failed to Download Repository Information"

```

W:GPG error: http://download.virtualbox.org/virtualbox/debian xenial InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A2F683C52980AECF, W:The repository 'http://download.virtualbox.org/virtualbox/debian xenial InRelease' is not signed., W:Data from such a repository can't be authenticated and is therefore potentially dangerous to use., W:See apt-secure(8) manpage for repository creation and user configuration details., W:The repository 'http://download.bitdefender.com/repos/deb BitDefender Release' does not have a Release file., W:Data from such a repository can't be authenticated and is therefore potentially dangerous to use., W:See apt-secure(8) manpage for repository creation and user configuration details., E:Failed to fetch http://download.bitdefender.com/repos/deb/dists/BitDefender/non-free/binary-amd64/Packages  404  Not Found, E:Some index files failed to download. They have been ignored, or old ones used instead.

```


Any suggestion? _**Or is this one you were referring to at the bottom of Post #15?**_
Thanks!
Yep! You will have to disable those 2 PPA's for now..But there is a Virtualbox in the Xenial Repo's.
If I remember correctly they have had close to a year now to comply....To the New (SHA2) singing policy, So now they will be disabled by default.
Don't kill the messenger.:)
EDIT just found this for Bitdefender PPA but I do not know if the same will happen with the Key, Have a look and you decide: [https://ubuntuforums.org/showthread.php?t=2319219](https://ubuntuforums.org/showthread.php?t=2319219)

---

### Post by Rick St. George on 2016-08-03
Did that ..Now I get "Requires Installation of Untrusted Packages".

And Software Updater just closes! I did see a number of updates ... over 150 MB. Undoubtably because of the recent upgrade. 
But how do I get around, or fix this?

---

### Post by QDR06VV9 on 2016-08-03
> **Rick St. George said:**
> Did that ..Now I get "Requires Installation of Untrusted Packages".

And Software Updater just closes! I did see a number of updates ... over 150 MB. Undoubtably because of the recent upgrade. 
But how do I get around, or fix this?

I need to see the Error please.

---

### Post by Rick St. George on 2016-08-03
Went back into Sources.List and REMOVED those lines, as well as in Software Updater / Settings.
Then the Update ran and finished. Rebooting Now.

One Last Question - Can I install LibreOffice via the Terminal? Software Center and Synaptic Pkg. Mgr. is installed but apparently not working with this new OS v16.04.

---

### Post by QDR06VV9 on 2016-08-03
Synaptic works fine here..
Check again after rebooting.

---

### Post by Rick St. George on 2016-08-03
Error in Synaptic Pkg. Mgr.:
E: The value 'trusty' is invalid for APT::Default-Release as such a release is not available in the sources
E: _cache->open() failed, please report.

The E drive should not be registered?!?!?

---

### Post by QDR06VV9 on 2016-08-03
He he he Nothing is easy here is it..
Lets get rough with then.
```
 sudo sed -i 's/trusty/xenial/g' /etc/apt/sources.list
```
Now update and dist-upgrade
```
sudo apt-get update && sudo apt-get dist-upgrade
```
Tell me how this goes.

---

### Post by Rick St. George on 2016-08-03
This is how it goes ...

```

stephen@stephen-evo-5723:~$ sudo sed -i 's/trusty/xenial/g' /etc/apt/sources.list
stephen@stephen-evo-5723:~$ sudo apt-get update && sudo apt-get dist-upgrade
Hit:1 http://archive.canonical.com/ubuntu xenial InRelease
Hit:2 http://archive.ubuntu.com/ubuntu xenial InRelease
Hit:3 http://ppa.launchpad.net/jfi/ppa/ubuntu xenial InRelease           
Get:4 http://archive.ubuntu.com/ubuntu xenial-security InRelease [94.5 kB]
Hit:5 http://ppa.launchpad.net/pipelight/stable/ubuntu xenial InRelease        
Hit:6 http://ppa.launchpad.net/sunab/kdenlive-release/ubuntu xenial InRelease  
Hit:7 http://ppa.launchpad.net/ubuntu-sdk-team/ppa/ubuntu xenial InRelease     
Get:8 http://archive.ubuntu.com/ubuntu xenial-updates InRelease [95.7 kB]
Hit:9 http://ppa.launchpad.net/webupd8team/java/ubuntu xenial InRelease        
Hit:10 https://deb.opera.com/opera-stable stable InRelease                     
Get:11 http://archive.ubuntu.com/ubuntu xenial-proposed InRelease [247 kB]
Fetched 437 kB in 1s (219 kB/s)                               
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  gstreamer0.10-plugins-bad-multiverse libfaac0
Use 'sudo apt autoremove' to remove them.
The following packages have been kept back:
  libmlt++3 melt
The following packages will be upgraded:
  gir1.2-unity-5.0 libnm-gtk-common libnm-gtk0 libnma-common libnma0
  libunity-protocol-private0 libunity-scopes-json-def-desktop libunity9
  network-manager-gnome openssh-client
10 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 1,324 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 openssh-client amd64 1:7.2p2-4ubuntu1 [586 kB]
Get:2 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libunity9 amd64 7.1.4+16.04.20160701-0ubuntu1 [199 kB]
Get:3 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libunity-protocol-private0 amd64 7.1.4+16.04.20160701-0ubuntu1 [78.1 kB]
Get:4 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libunity-scopes-json-def-desktop all 7.1.4+16.04.20160701-0ubuntu1 [3,544 B]
Get:5 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 gir1.2-unity-5.0 amd64 7.1.4+16.04.20160701-0ubuntu1 [20.2 kB]
Get:6 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libnm-gtk0 amd64 1.2.0-0ubuntu0.16.04.3 [70.0 kB]
Get:7 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libnm-gtk-common all 1.2.0-0ubuntu0.16.04.3 [5,344 B]
Get:8 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 network-manager-gnome amd64 1.2.0-0ubuntu0.16.04.3 [290 kB]
Get:9 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libnma0 amd64 1.2.0-0ubuntu0.16.04.3 [66.0 kB]
Get:10 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libnma-common all 1.2.0-0ubuntu0.16.04.3 [5,328 B]
Fetched 1,324 kB in 2s (569 kB/s)         
(Reading database ... 291229 files and directories currently installed.)
Preparing to unpack .../openssh-client_1%3a7.2p2-4ubuntu1_amd64.deb ...
Unpacking openssh-client (1:7.2p2-4ubuntu1) over (1:7.2p2-4) ...
Preparing to unpack .../libunity9_7.1.4+16.04.20160701-0ubuntu1_amd64.deb ...
Unpacking libunity9:amd64 (7.1.4+16.04.20160701-0ubuntu1) over (7.1.4+15.10.20151002-0ubuntu2) ...
Preparing to unpack .../libunity-protocol-private0_7.1.4+16.04.20160701-0ubuntu1_amd64.deb ...
Unpacking libunity-protocol-private0:amd64 (7.1.4+16.04.20160701-0ubuntu1) over (7.1.4+15.10.20151002-0ubuntu2) ...
Preparing to unpack .../libunity-scopes-json-def-desktop_7.1.4+16.04.20160701-0ubuntu1_all.deb ...
Unpacking libunity-scopes-json-def-desktop (7.1.4+16.04.20160701-0ubuntu1) over (7.1.4+15.10.20151002-0ubuntu2) ...
Preparing to unpack .../gir1.2-unity-5.0_7.1.4+16.04.20160701-0ubuntu1_amd64.deb ...
Unpacking gir1.2-unity-5.0:amd64 (7.1.4+16.04.20160701-0ubuntu1) over (7.1.4+15.10.20151002-0ubuntu2) ...
Preparing to unpack .../libnm-gtk0_1.2.0-0ubuntu0.16.04.3_amd64.deb ...
Unpacking libnm-gtk0:amd64 (1.2.0-0ubuntu0.16.04.3) over (1.1.93-1ubuntu1) ...
Preparing to unpack .../libnm-gtk-common_1.2.0-0ubuntu0.16.04.3_all.deb ...
Unpacking libnm-gtk-common (1.2.0-0ubuntu0.16.04.3) over (1.1.93-1ubuntu1) ...
Preparing to unpack .../network-manager-gnome_1.2.0-0ubuntu0.16.04.3_amd64.deb ...
Unpacking network-manager-gnome (1.2.0-0ubuntu0.16.04.3) over (1.1.93-1ubuntu1) ...
Preparing to unpack .../libnma0_1.2.0-0ubuntu0.16.04.3_amd64.deb ...
Unpacking libnma0:amd64 (1.2.0-0ubuntu0.16.04.3) over (1.1.93-1ubuntu1) ...
Preparing to unpack .../libnma-common_1.2.0-0ubuntu0.16.04.3_all.deb ...
Unpacking libnma-common (1.2.0-0ubuntu0.16.04.3) over (1.1.93-1ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...
Processing triggers for libglib2.0-0:amd64 (2.48.1-1~ubuntu16.04.1) ...
No such key 'show-notify-osd-on-scroll' in schema 'com.canonical.indicator.sound' as specified in override file '/usr/share/glib-2.0/schemas/20_ubuntustudio-default-settings.gschema.override'; ignoring override for this key.
No such key 'auto-launch' in schema 'com.ubuntu.update-notifier' as specified in override file '/usr/share/glib-2.0/schemas/20_ubuntustudio-default-settings.gschema.override'; ignoring override for this key.
Processing triggers for gconf2 (3.2.6-3ubuntu6) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Setting up openssh-client (1:7.2p2-4ubuntu1) ...
Setting up libunity-protocol-private0:amd64 (7.1.4+16.04.20160701-0ubuntu1) ...
Setting up libunity-scopes-json-def-desktop (7.1.4+16.04.20160701-0ubuntu1) ...
Setting up libunity9:amd64 (7.1.4+16.04.20160701-0ubuntu1) ...
Setting up gir1.2-unity-5.0:amd64 (7.1.4+16.04.20160701-0ubuntu1) ...
Setting up libnm-gtk-common (1.2.0-0ubuntu0.16.04.3) ...
Setting up libnm-gtk0:amd64 (1.2.0-0ubuntu0.16.04.3) ...
Setting up libnma-common (1.2.0-0ubuntu0.16.04.3) ...
Setting up libnma0:amd64 (1.2.0-0ubuntu0.16.04.3) ...
Setting up network-manager-gnome (1.2.0-0ubuntu0.16.04.3) ...
Processing triggers for libc-bin (2.23-0ubuntu3) ...

```

Almost all went OK - Notice the "No Such Key" items above. Should this be a concern, as it has to do with sound?

---

### Post by QDR06VV9 on 2016-08-03
Huumm? Might have to do with VB.
```
sudo adduser $USER vboxusers
```
But yes that looks better, and what about synaptic..is it now in a good state?

---

### Post by Rick St. George on 2016-08-03
I am already a member of 'vboxusers'. Rec'd this again with Synaptic Pkg. Mgr.

```

E: The value 'trusty' is invalid for APT::Default-Release as such a release is not available in the sources
E: _cache->open() failed, please report.

```

Performed the following;

```

  	 	 	 	   sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade  
```

Almost like it did the Upgrade All over again!  .. 100's of MB download & installed.
It Ended with this ....

```

Registering documents with scrollkeeper...
Processing triggers for dbus (1.10.6-1ubuntu3) ...
Processing triggers for python-support (1.0.15) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libxfce4panel-2.0-4_4.12.0-3ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```


But a window popped up and Reported a BUG.

---

### Post by QDR06VV9 on 2016-08-03
I'm sure this will not be of any use... but we try
```
sudo apt-get -f install
```
I'm wondering if a clean install would not improve things...just to many missing packages at this point.
I mean we can pursue this if you want to...it will be a long frustrating path but I will assist you if you want this. 
There were a lot of others Upgrading from Ubuntu Studio (14.04) to Ubuntu Studio (16.04) that still have no solutions to the error you have just shown [B]"/var/cache/apt/archives/libxfce4panel-2.0-4_4.12.0-3ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)"
EDIT: [/B]This might be because we installed synaptic when the trusty repos were still showing**..**So maybe we can get lucky and remove synaptic and re-install it[B].
[/B]```
sudo apt-get remove synaptic*
```

---

### Post by Rick St. George on 2016-08-03
That removed Synaptic Pkg Mgr. I'll wait for the Bugs to be fixed before downloading and installing it. 
Thanks 'runrickus' for all the help. I am afraid of losing too many files and my Virtual Machine will Trading Software etc. if I do a clean install. Right now battling with why my fairly new machine can't see the 2nd Hard Drive (#1 is a SSD). It has all my files on it. 

Catch ya later!
Peace.

---

### Post by Rick St. George on 2016-11-10
I believe this is related to another post I made here [https://ubuntuforums.org/showthread.php?t=2337677](https://ubuntuforums.org/showthread.php?t=2337677)

So I will mark this Thread as Solved.

Thanks all  ! ! ! 

:popcorn:

---

