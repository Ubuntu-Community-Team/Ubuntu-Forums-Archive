---
title: "dpkg error during upgrade"
date: 2018-01-23
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2018-01-23
When attempting to run an upgrade I get the following error;

```
dpkg: warning: files list file for package 'gnome-session-flashback' missing; assuming package has no files currently installed
dpkg: unrecoverable fatal error, aborting:
 files list file for package 'gstreamer1.0-plugins-base:amd64' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

Attempting to reinstall either package also generates an error. attempting to remove either of them generates a long list of packages to be removed and a long list of packages to be installed.

I'd like to fix this the easiest way possible.

---

### Post by rsteinmetz70112 on 2018-01-24
Looking through older posts I found one which said to:

```
apt-get -f install
apt-get autoremove
apt-get purge
apt-get clean

```
That resolved one issue;

When I go to upgrade I was able to download the new packages but I'm still getting the same errors:
```

Preconfiguring packages ...
dpkg: warning: files list file for package 'gnome-session-flashback' missing; assuming package has no files currently installed
dpkg: unrecoverable fatal error, aborting:
 files list file for package 'gstreamer1.0-plugins-base:amd64' is missing final newline
```

I have 13 packages which are not upgraded.

Several posts recommend

```
apt-get install --reinstall  gnome-session-flashback  gstreamer1.0-plugins-base amd64
```

However that creates the same error.

---

### Post by rsteinmetz70112 on 2018-01-28
OK I downloaded copies of both packages and ran dpkc -c on them and don't see a files list in either. 

```
# dpkg -c gnome-session-flashback_1%3a3.18.2-1ubuntu1_all.deb
drwxr-xr-x root/root         0 2016-02-18 01:53 ./
drwxr-xr-x root/root         0 2016-02-18 01:53 ./etc/
drwxr-xr-x root/root         0 2016-02-18 01:53 ./etc/xdg/
drwxr-xr-x root/root         0 2016-02-18 01:53 ./etc/xdg/autostart/
-rw-r--r-- root/root       790 2016-02-18 01:53 ./etc/xdg/autostart/gnome-flashback-screensaver.desktop
drwxr-xr-x root/root         0 2016-02-18 01:53 ./usr/
drwxr-xr-x root/root         0 2016-02-18 01:53 ./usr/lib/
drwxr-xr-x root/root         0 2016-02-18 01:53 ./usr/lib/gnome-flashback/
-rwxr-xr-x root/root       162 2016-02-18 01:53 ./usr/lib/gnome-flashback/gnome-flashback-compiz
-rwxr-xr-x root/root       193 2016-02-18 01:53 ./usr/lib/gnome-flashback/gnome-flashback-metacity
drwxr-xr-x root/root         0 2016-02-18 01:53 ./usr/share/
drwxr-xr-x root/root         0 2016-02-18 01:53 ./usr/share/applications/
-rw-r--r-- root/root       256 2016-02-18 01:53 ./usr/share/applications/gnome-flashback-services.desktop
drwxr-xr-x root/root         0 2016-02-18 01:53 ./usr/share/gnome-session/
drwxr-xr-x root/root         0 2016-02-18 01:53 ./usr/share/gnome-session/sessions/
-rw-r--r-- root/root       169 2016-02-18 01:53 ./usr/share/gnome-session/sessions/gnome-flashback-compiz.session
-rw-r--r-- root/root       173 2016-02-18 01:53 ./usr/share/gnome-session/sessions/gnome-flashback-metacity.session
drwxr-xr-x root/root         0 2016-02-18 01:53 ./usr/share/xsessions/
-rw-r--r-- root/root       270 2016-02-18 01:53 ./usr/share/xsessions/gnome-flashback-compiz.desktop
-rw-r--r-- root/root       278 2016-02-18 01:53 ./usr/share/xsessions/gnome-flashback-metacity.desktop
drwxr-xr-x root/root         0 2016-02-18 01:53 ./usr/share/doc/
drwxr-xr-x root/root         0 2016-02-18 01:53 ./usr/share/doc/gnome-session-flashback/
-rw-r--r-- root/root      4511 2016-02-17 10:59 ./usr/share/doc/gnome-session-flashback/copyright
-rw-r--r-- root/root      1679 2016-02-18 01:53 ./usr/share/doc/gnome-session-flashback/changelog.Debian.gz
```

```
# dpkg -c gstreamer1.0-plugins-base_1.8.3-1ubuntu0.2_amd64.deb
drwxr-xr-x root/root         0 2017-03-24 08:53 ./
drwxr-xr-x root/root         0 2017-03-24 08:53 ./usr/
drwxr-xr-x root/root         0 2017-03-24 08:53 ./usr/lib/
drwxr-xr-x root/root         0 2017-03-24 08:53 ./usr/lib/x86_64-linux-gnu/
drwxr-xr-x root/root         0 2017-03-24 08:53 ./usr/lib/x86_64-linux-gnu/gstreamer-1.0/
-rw-r--r-- root/root    234768 2017-03-24 08:53 ./usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstogg.so
-rw-r--r-- root/root     23264 2017-03-24 08:53 ./usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstaudiorate.so
-rw-r--r-- root/root     57048 2017-03-24 08:53 ./usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstopus.so
-rw-r--r-- root/root     23360 2017-03-24 08:53 ./usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstvideoconvert.so
-rw-r--r-- root/root      6320 2017-03-24 08:53 ./usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstapp.so
-rw-r--r-- root/root     23408 2017-03-24 08:53 ./usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstaudioconvert.so
-rw-r--r-- root/root    376000 2017-03-24 08:53 ./usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstplayback.so
-rw-r--r-- root/root     61520 2017-03-24 08:53 ./usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgsttheora.so
-rw-r--r-- root/root     15088 2017-03-24 08:53 ./usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstlibvisual.so
-rw-r--r-- root/root     77040 2017-03-24 08:53 ./usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstaudioresample.so
-rw-r--r-- root/root     31712 2017-03-24 08:53 ./usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstvideoscale.so
-rw-r--r-- root/root     35872 2017-03-24 08:53 ./usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstvideorate.so
-rw-r--r-- root/root     48224 2017-03-24 08:53 ./usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstgio.so
-rw-r--r-- root/root     81920 2017-03-24 08:53 ./usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstsubparse.so
-rw-r--r-- root/root     43984 2017-03-24 08:53 ./usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstaudiotestsrc.so
-rw-r--r-- root/root     56736 2017-03-24 08:53 ./usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstadder.so
-rw-r--r-- root/root     98112 2017-03-24 08:53 ./usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgsttypefindfunctions.so
-rw-r--r-- root/root     52464 2017-03-24 08:53 ./usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstvideotestsrc.so
-rw-r--r-- root/root     70032 2017-03-24 08:53 ./usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstencodebin.so
-rw-r--r-- root/root     31312 2017-03-24 08:53 ./usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstvolume.so
-rw-r--r-- root/root     23232 2017-03-24 08:53 ./usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstcdparanoia.so
-rw-r--r-- root/root     52928 2017-03-24 08:53 ./usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgstvorbis.so
-rw-r--r-- root/root    114800 2017-03-24 08:53 ./usr/lib/x86_64-linux-gnu/gstreamer-1.0/libgsttcp.so
drwxr-xr-x root/root         0 2017-03-24 08:53 ./usr/share/
drwxr-xr-x root/root         0 2017-03-24 08:53 ./usr/share/doc/
drwxr-xr-x root/root         0 2017-03-24 08:54 ./usr/share/doc/gstreamer1.0-plugins-base/
-rw-r--r-- root/root     36363 2016-09-02 07:09 ./usr/share/doc/gstreamer1.0-plugins-base/copyright
lrwxrwxrwx root/root         0 2017-03-24 08:54 ./usr/share/doc/gstreamer1.0-plugins-base/changelog.Debian.gz -> ../libgstreamer-plugins-base1.0-0/changelog.Debian.gz
lrwxrwxrwx root/root         0 2017-03-24 08:54 ./usr/share/doc/gstreamer1.0-plugins-base/README.gz -> ../libgstreamer-plugins-base1.0-0/README.gz
lrwxrwxrwx root/root         0 2017-03-24 08:54 ./usr/share/doc/gstreamer1.0-plugins-base/AUTHORS -> ../libgstreamer-plugins-base1.0-0/AUTHORS
lrwxrwxrwx root/root         0 2017-03-24 08:54 ./usr/share/doc/gstreamer1.0-plugins-base/README.Debian -> ../libgstreamer-plugins-base1.0-0/README.Debian
lrwxrwxrwx root/root         0 2017-03-24 08:54 ./usr/share/doc/gstreamer1.0-plugins-base/NEWS.gz -> ../libgstreamer-plugins-base1.0-0/NEWS.gz
```

Attempting to remove the package creates this list of changes:

```
# apt-get remove gstreamer1.0-plugins-base:amd64
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  apg argyll argyll-ref bijiben brasero-cdrkit brasero-common caribou-antler cheese-common cups-pk-helper dconf-editor dconf-tools
  dleyna-renderer dleyna-server dvd+rw-tools empathy-common evince-common fairymax finger five-or-more folks-common fonts-cantarell
  four-in-a-row freepats geoclue-2.0 gir1.2-champlain-0.12 gir1.2-clutter-gst-3.0 gir1.2-geocodeglib-1.0 gir1.2-gfbgraph-0.2 gir1.2-grilo-0.2
  gir1.2-gtkchamplain-0.12 gir1.2-gtkclutter-1.0 gir1.2-mediaart-2.0 gir1.2-rb-3.0 gir1.2-rest-0.7 gir1.2-secret-1 gir1.2-totem-1.0
  gir1.2-totem-plparser-1.0 gir1.2-tracker-1.0 gir1.2-zpj-0.0 gnome-chess gnome-clocks gnome-color-manager gnome-control-center-data
  gnome-dictionary gnome-games gnome-getting-started-docs gnome-klotski gnome-logs gnome-maps gnome-music gnome-nettool gnome-nibbles
  gnome-online-accounts gnome-online-miners gnome-photos gnome-robots gnome-shell-extension-weather gnome-shell-extensions gnome-tetravex
  gnome-themes-standard gnome-tweak-tool grilo-plugins-0.2-base grilo-plugins-0.2-extra growisofs gstreamer1.0-clutter-3.0 gstreamer1.0-libav
  gstreamer1.0-nice gstreamer1.0-plugins-ugly gstreamer1.0-plugins-ugly-amr gstreamer1.0-x hamster-applet hamster-indicator hitori hoichess
  i965-va-driver iagno javascript-common liba52-0.7.4 libaacs0 libass5 libavc1394-0 libavcodec-ffmpeg56 libavfilter-ffmpeg5
  libavformat-ffmpeg56 libavresample-ffmpeg2 libavutil-ffmpeg54 libbdplus0 libbluray1 libbrasero-media3-1 libbs2b0 libburn4
  libcaribou-gtk-module libcaribou-gtk3-module libchromaprint0 libclutter-gst-2.0-0 libclutter-gst-3.0-0 libcolord-gtk1 libcoverart1
  libcoverartcc1v5 libcrystalhd3 libdc1394-22 libdca0 libde265-0 libdiscid0 libdleyna-connector-dbus-1.0-1 libdleyna-core-1.0-3
  libdmapsharing-3.0-2 libdv4 libdvdnav4 libdvdread4 libevdocument3-4 libfaad2 libflite1 libfluidsynth1 libfolks-eds25 libfolks-telepathy25
  libfolks25 libgdict-1.0-9 libgdict-common libgeoclue-2-0 libgeonames0 libgfbgraph-0.2-0 libgme0 libgoa-backend-1.0-1 libgom-1.0-0
  libgom-1.0-common libgpod-common libgpod4 libgrilo-0.2-1 libgsf-bin libgsm1 libgsound0 libgssdp-1.0-3 libgstreamer-plugins-bad1.0-0
  libgstreamer-plugins-good1.0-0 libgtkglext1 libgupnp-1.0-4 libgupnp-av-1.0-2 libgupnp-dlna-2.0-3 libgupnp-igd-1.0-4 libiec61883-0 libisofs6
  libjs-jquery libjs-jquery-ui libjte1 libkate1 libkpathsea6 liblircclient0 liblua5.3-0 libmad0 libmeanwhile1 libmimic0 libmjpegutils-2.1-0
  libmms0 libmodplug1 libmp3lame0 libmpeg2-4 libmpeg2encpp-2.1-0 libmpg123-0 libmplex2-2.1-0 libmusicbrainz5-2 libmusicbrainz5cc2v5 libnice10
  libofa0 libopenal-data libopenal1 libopencore-amrnb0 libopencore-amrwb0 libopencv-calib3d2.4v5 libopencv-contrib2.4v5 libopencv-core2.4v5
  libopencv-features2d2.4v5 libopencv-flann2.4v5 libopencv-highgui2.4v5 libopencv-imgproc2.4v5 libopencv-legacy2.4v5 libopencv-ml2.4v5
  libopencv-objdetect2.4v5 libopencv-video2.4v5 libopenjpeg5 libpangox-1.0-0 libpostproc-ffmpeg53 libraw1394-11 librhythmbox-core9
  librygel-core-2.6-2 librygel-db-2.6-2 librygel-renderer-2.6-2 librygel-renderer-gst-2.6-2 librygel-server-2.6-2 libschroedinger-1.0-0
  libsgutils2-2 libshine3 libshout3 libsidplay1v5 libsnappy1v5 libsodium18 libsofia-sip-ua-glib3 libsofia-sip-ua0 libsoundtouch1 libsoxr0
  libspandsp2 libspectre1 libspeex1 libsrtp0 libssh-gcrypt-4 libswresample-ffmpeg1 libswscale-ffmpeg3 libtbb2 libtimezonemap-data
  libtimezonemap1 libtotem0 libtwolame0 libv4l-0 libv4lconvert0 libva1 libvo-aacenc0 libvo-amrwbenc0 libwavpack1 libwildmidi-config
  libwildmidi1 libwnck-common libwnck22 libx264-148 libx265-79 libxvidcore4 libzapojit-0.0-0 libzbar0 libzephyr4 libzmq5 libzvbi-common
  libzvbi0 lightsoff media-player-info pidgin-data polari python-matplotlib-data python-wnck python3-cycler python3-dateutil python3-gst-1.0
  python3-mako python3-matplotlib python3-numpy python3-tk python3-tz realmd rhythmbox-data rygel rygel-tracker signon-keyring-extension
  swell-foop tali telepathy-gabble telepathy-logger telepathy-rakia telepathy-salut totem-common ubuntu-system-service
  unity-control-center-faces unoconv va-driver-all vdpau-va-driver xboard
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  apparmor-easyprof apparmor-easyprof-ubuntu click click-apparmor gir1.2-click-0.4 gir1.2-gee-0.8 libboost-log1.58.0 libboost-regex1.58.0
  libboost-thread1.58.0 libclick-0.4-0 libcontent-hub0 libgflags2v5 libgoogle-glog0v5 liblibertine1 liblttng-ust-ctl2 liblttng-ust0
  libubuntu-app-launch2 libubuntu-download-manager-client1 libubuntu-download-manager-common1 libudm-common1 liburcu4 python3-apparmor-click
  python3-click-package qtdeclarative5-ubuntu-content1
Suggested packages:
  click-reviewers-tools ubuntu-app-launch-tools | upstart-app-launch-tools content-hub
The following packages will be REMOVED:
  account-plugin-aim account-plugin-jabber account-plugin-salut account-plugin-yahoo brasero cheese empathy evince gir1.2-evince-3.0
  gir1.2-ges-1.0 gnome gnome-contacts gnome-control-center gnome-core gnome-documents gnome-sound-recorder gnome-sushi gnome-video-effects
  goobox gstreamer1.0-plugins-bad gstreamer1.0-plugins-bad-faad gstreamer1.0-plugins-bad-videoparsers gstreamer1.0-plugins-base
  gstreamer1.0-plugins-good indicator-bluetooth libcheese-gtk25 libcheese8 libevview3-3 libfarstream-0.2-5 libges-1.0-0 libpurple0
  libtelepathy-farstream3 mcp-account-manager-uoa pidgin pidgin-libnotify pitivi rhythmbox rhythmbox-plugin-cdrecorder
  rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist rhythmbox-plugins rygel-playbin telepathy-haze totem totem-plugins ubuntu-desktop
  unity-control-center unity-control-center-signon webaccounts-extension-common xul-ext-webaccounts
The following NEW packages will be installed:
  apparmor-easyprof apparmor-easyprof-ubuntu click click-apparmor gir1.2-click-0.4 gir1.2-gee-0.8 libboost-log1.58.0 libboost-regex1.58.0
  libboost-thread1.58.0 libclick-0.4-0 libcontent-hub0 libgflags2v5 libgoogle-glog0v5 liblibertine1 liblttng-ust-ctl2 liblttng-ust0
  libubuntu-app-launch2 libubuntu-download-manager-client1 libubuntu-download-manager-common1 libudm-common1 liburcu4 python3-apparmor-click
  python3-click-package qtdeclarative5-ubuntu-content1
0 upgraded, 24 newly installed, 50 to remove and 24 not upgraded.
Need to get 1,719 kB of archives.
After this operation, 60.6 MB disk space will be freed.
Do you want to continue? [Y/n]
```

Which seems extreme. 

I moved all of the files in /var/lib/dpkg/info/ related to the two packages but an upgrade of package install failed, so I moved them back.

---

### Post by rsteinmetz70112 on 2018-01-29
OK I've solved one of my problems. The thread below has a script for fixing new lines:

[https://ubuntuforums.org/showthread.php?t=1319791&highlight=newline_fixer.py](https://ubuntuforums.org/showthread.php?t=1319791&highlight=newline_fixer.py)

It works great for  that. After thet I was able to run and update and upgrade whihc sot of worked now I seem to have some unmet dependencies.

```
# dpkg --configure -a
dpkg: dependency problems prevent configuration of fwupdate-signed:
 fwupdate-signed depends on fwupdate (= 0.5-2ubuntu7); however:
  Version of fwupdate on system is 0.5-2ubuntu5.

dpkg: error processing package fwupdate-signed (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of thunderbird-gnome-support:
 thunderbird-gnome-support depends on thunderbird (= 1:52.6.0+build1-0ubuntu0.16.04.1); however:
  Version of thunderbird on system is 1:52.5.0+build1-0ubuntu0.16.04.1.

dpkg: error processing package thunderbird-gnome-support (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fwupdate-signed
 thunderbird-gnome-support
```


```
# sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  fwupdate thunderbird
Suggested packages:
  ttf-lyx
The following packages will be upgraded:
  fwupdate thunderbird
2 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
2 not fully installed or removed.
Need to get 42.3 MB of archives.
After this operation, 71.7 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 [http://archive.linux.duke.edu/ubuntu](http://archive.linux.duke.edu/ubuntu) xenial-updates/main amd64 fwupdate amd64 0.5-2ubuntu7 [34.3 kB]
Get:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 thunderbird amd64 1:52.6.0+build1-0ubuntu0.16.04.1 [42.2 MB]
Fetched 42.3 MB in 24s (1,742 kB/s)
dpkg: warning: files list file for package 'unity-control-center-signon' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnux-4.0-0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ubuntu-sounds' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libfontenc1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsensors4:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libbind9-140:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libbabeltrace-ctf1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'nautilus' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libbrlapi0.6:amd64' missing; assuming package has no files currently installed
(Reading database ... 302932 files and directories currently installed.)
Preparing to unpack .../fwupdate_0.5-2ubuntu7_amd64.deb ...
Unpacking fwupdate (0.5-2ubuntu7) over (0.5-2ubuntu5) ...
dpkg: error processing archive /var/cache/apt/archives/fwupdate_0.5-2ubuntu7_amd64.deb (--unpack):
 unable to make backup symlink for './usr/share/man/man3/fwup_clear_status.3.gz': No such file or directory
No apport report written because the error message indicates an issue on the local system
                                                                                         Preparing to unpack .../thunderbird_1%3a52.6.0+build1-0ubuntu0.16.04.1_amd64.deb ...
Unpacking thunderbird (1:52.6.0+build1-0ubuntu0.16.04.1) over (1:52.5.0+build1-0ubuntu0.16.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/thunderbird_1%3a52.6.0+build1-0ubuntu0.16.04.1_amd64.deb (--unpack):
 unable to make backup symlink for './usr/lib/thunderbird/defaults/pref/syspref.js': No such file or directory
No apport report written because the error message indicates an issue on the local system
                                                                                         Processing triggers for man-db (2.7.5-1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/fwupdate_0.5-2ubuntu7_amd64.deb
 /var/cache/apt/archives/thunderbird_1%3a52.6.0+build1-0ubuntu0.16.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by rsteinmetz70112 on 2018-01-29
After screwing a round with this for a long time the solution was actually pretty easy. While apt and apt-get refused to remove or reinstall the packages, it turns our Synaptic was able to simply reinstall most of them and the couple it couldn't reinstall (thunderbird and fwupdate) it could completely remove and then install them again.

---

