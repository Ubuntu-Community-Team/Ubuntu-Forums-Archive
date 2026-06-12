---
title: "Unmet dependencies not fixable for Gstreamer"
date: 2018-07-24
forum: Installation &amp; Upgrades
---

### Post by Mark_in_Hollywood on 2018-07-24
I tried to play a recording (.amr) and Video looked for plugins. The plugin window shows an exclamation point in red letter that would be installed. I closed that without installation of plugins. In a terminal, after the "update", I ran: apt-get install ubuntu-restricted-extras. That returned a host of errors. This is a clean install of 16.04, yesterday. I then ran apt-get install -f, but that fails to fix the unmet dependencies. What went wrong at 16.04 install time? Can it be fixed?

```
mark@Lexington:~$ sudo aptitude install ubuntu-restricted-extras
The following NEW packages will be installed:
  cabextract{a} chromium-codecs-ffmpeg-extra{a} flashplugin-installer{a} 
  freepats{a} gstreamer1.0-fluendo-mp3{a} gstreamer1.0-libav{a} 
  gstreamer1.0-plugins-bad{a} gstreamer1.0-plugins-bad-faad{a} 
  gstreamer1.0-plugins-bad-videoparsers{a} gstreamer1.0-plugins-ugly{a} 
  gstreamer1.0-plugins-ugly-amr{a} i965-va-driver{a} liba52-0.7.4{a} 
  libaacs0{a} libass5{a} libavcodec-extra{a} libavcodec-ffmpeg-extra56{ab} 
  libavcodec-ffmpeg56{a} libavfilter-ffmpeg5{a} libavformat-ffmpeg56{a} 
  libavresample-ffmpeg2{a} libavutil-ffmpeg54{a} libbdplus0{a} 
  libbluray1{a} libbs2b0{a} libchromaprint0{a} libcrystalhd3{a} 
  libdc1394-22{a} libdca0{a} libde265-0{a} libdvdnav4{a} libdvdread4{a} 
  libfaad2{a} libflite1{a} libfluidsynth1{a} libgme0{a} libgsm1{a} 
  libgstreamer-plugins-bad1.0-0{a} libgtkglext1{a} libkate1{a} libmad0{a} 
  libmimic0{a} libmjpegutils-2.1-0{a} libmms0{a} libmodplug1{a} 
  libmp3lame0{a} libmpeg2-4{a} libmpeg2encpp-2.1-0{a} libmpg123-0{a} 
  libmplex2-2.1-0{a} libmspack0{a} libofa0{a} libopenal-data{a} 
  libopenal1{a} libopencore-amrnb0{a} libopencore-amrwb0{a} 
  libopencv-calib3d2.4v5{a} libopencv-contrib2.4v5{a} 
  libopencv-core2.4v5{a} libopencv-features2d2.4v5{a} 
  libopencv-flann2.4v5{a} libopencv-highgui2.4v5{a} 
  libopencv-imgproc2.4v5{a} libopencv-legacy2.4v5{a} libopencv-ml2.4v5{a} 
  libopencv-objdetect2.4v5{a} libopencv-video2.4v5{a} libopenjpeg5{a} 
  libpostproc-ffmpeg53{a} libschroedinger-1.0-0{a} libshine3{a} 
  libsidplay1v5{a} libsnappy1v5{a} libsodium18{a} libsoundtouch1{a} 
  libsoxr0{a} libspandsp2{a} libsrtp0{a} libssh-gcrypt-4{a} 
  libswresample-ffmpeg1{a} libswscale-ffmpeg3{a} libtbb2{a} libtwolame0{a} 
  libva1{a} libvo-aacenc0{a} libvo-amrwbenc0{a} libwildmidi-config{a} 
  libwildmidi1{a} libx264-148{a} libx265-79{a} libxvidcore4{a} libzbar0{a} 
  libzmq5{a} libzvbi-common{a} libzvbi0{a} mesa-va-drivers{a} 
  oxideqt-codecs-extra{ab} ttf-mscorefonts-installer{a} 
  ubuntu-restricted-addons{a} ubuntu-restricted-extras unrar{a} 
  va-driver-all{a} 
0 packages upgraded, 102 newly installed, 0 to remove and 0 not upgraded.
Need to get 5,356 kB/68.1 MB of archives. After unpacking 167 MB will be used.
The following packages have unmet dependencies:
 oxideqt-codecs : Conflicts: oxideqt-codecs-extra but 1.21.5-0ubuntu0.16.04.1 is to be installed.
 oxideqt-codecs-extra : Conflicts: oxideqt-codecs but 1.21.5-0ubuntu0.16.04.1 is installed.
 libavcodec-ffmpeg-extra56 : Conflicts: libavcodec-ffmpeg56 but 7:2.8.14-0ubuntu0.16.04.1 is to be installed.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:     
1)     libavcodec-ffmpeg56 [Not Installed]                     
2)     oxideqt-codecs-extra [Not Installed]                    

     Leave the following dependencies unresolved:              
3)     ubuntu-restricted-addons recommends oxideqt-codecs-extra


Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.
mark@Lexington:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```[ATTACH=CONFIG]280501[/ATTACH]

---

### Post by #&amp;thj^% on 2018-07-24
I have never seen this before "ubuntu-restricted-addons recommends oxideqt-codecs-extra" :confused:
See if it is installed:
```
apt policy oxideqt-codecs-extra
```

---

### Post by Mark_in_Hollywood on 2018-07-24
```
mark@Lexington:~$ apt policy oxideqt-codecs-extra
oxideqt-codecs-extra:
  Installed: (none)
  Candidate: 1.21.5-0ubuntu0.16.04.1
  Version table:
     1.21.5-0ubuntu0.16.04.1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 Packages
     1.13.6-0ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
```

---

### Post by Mark_in_Hollywood on 2018-07-25
Although a warning came with trying to install ubuntu-restricted-extras, I installed it (them?). No problems seem to have arisen as a result of that.

---

