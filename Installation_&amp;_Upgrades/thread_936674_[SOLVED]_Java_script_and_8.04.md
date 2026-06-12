---
title: "[SOLVED] Java script and 8.04"
date: 2008-10-03
forum: Installation &amp; Upgrades
---

### Post by NewNerd99 on 2008-10-03
Hi guys was following a previously closed thread 

[http://ubuntuforums.org/showthread.php?t=936470&highlight=java+script](http://ubuntuforums.org/showthread.php?t=936470&highlight=java+script)   
   
and I had a problem executing the cmd     

sudo apt-get install ubuntu-restricted-extras
 
this is what came up:
I'm sure its something basic I'm missing. I'm just in the process of a rebuilding after wiping and reinstalling 8.04

I'm not sure why it is looking at E: (my disc drive I think) as I have not checked the box 'software sources'

Cheers
Chris


chris@chris-laptop:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  cabextract flashplugin-nonfree gstreamer0.10-pitfdll
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
  gstreamer0.10-plugins-ugly-multiverse java-common libcdaudio1 libfaac0
  libfaad0 libfreebob0 libgmyth0 libiptcdata0 libjack0 liblame0
  libmjpegtools0c2a libmms0 libmpcdec3 libmysqlclient15off libopenspc0
  libquicktime1 libsoundtouch1c2 libwildmidi0 libx264-57 libxvidcore4
  msttcorefonts mysql-common odbcinst1debian1 sun-java6-bin sun-java6-jre
  sun-java6-plugin unixodbc unrar
Suggested packages:
  konqueror-nsplugins libflashsupport ttf-xfree86-nonfree xfs equivs jackd
  binfmt-support sun-java6-fonts ttf-wqy-zenhei libct1 libmyodbc
  odbc-postgresql
Recommended packages:
  w32codecs freepats gsfonts-x11
The following NEW packages will be installed:
  cabextract flashplugin-nonfree gstreamer0.10-pitfdll
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
  gstreamer0.10-plugins-ugly-multiverse java-common libcdaudio1 libfaac0
  libfaad0 libfreebob0 libgmyth0 libiptcdata0 libjack0 liblame0
  libmjpegtools0c2a libmms0 libmpcdec3 libmysqlclient15off libopenspc0
  libquicktime1 libsoundtouch1c2 libwildmidi0 libx264-57 libxvidcore4
  msttcorefonts mysql-common odbcinst1debian1 sun-java6-bin sun-java6-jre
  sun-java6-plugin ubuntu-restricted-extras unixodbc unrar
0 upgraded, 34 newly installed, 0 to remove and 87 not upgraded.
1 not fully installed or removed.
Need to get 39.3MB of archives.
After this operation, 112MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main java-common 0.28ubuntu3
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main odbcinst1debian1 2.2.11-16build1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main unixodbc 2.2.11-16build1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse sun-java6-bin 6-06-0ubuntu1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse sun-java6-jre 6-06-0ubuntu1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe cabextract 1.2-2
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse flashplugin-nonfree 9.0.124.0ubuntu2
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe gstreamer0.10-pitfdll 0.9.1.1+cvs20080215-1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe libcdaudio1 0.99.12p2-3
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe libfaad0 2.6.1-2
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main mysql-common 5.0.51a-3ubuntu5.1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main libmysqlclient15off 5.0.51a-3ubuntu5.1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main libgmyth0 0.7.debian1-1~hardy1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe libiptcdata0 1.0.2-2
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe libfreebob0 1.0.7-1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe libjack0 0.109.2-1ubuntu1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe libmms0 0.3-6
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main libmpcdec3 1.2.2-1build1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe libopenspc0 0.3.99a-2
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/universe libsoundtouch1c2 1.3.0-2.2ubuntu0.1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe libwildmidi0 0.2.2-2
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe gstreamer0.10-plugins-bad 0.10.6-5
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse libfaac0 1.26-0.1ubuntu1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe libquicktime1 2:1.0.0+debian-5
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse libmjpegtools0c2a 1:1.8.0-0.2ubuntu5
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse libx264-57 1:0.svn20071224-0.0ubuntu1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse libxvidcore4 2:1.1.2-0.1ubuntu3
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse gstreamer0.10-plugins-bad-multiverse 0.10.6-1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse liblame0 3.97-0.0
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse gstreamer0.10-plugins-ugly-multiverse 0.10.7-1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse msttcorefonts 2.4
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse sun-java6-plugin 6-06-0ubuntu1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/multiverse ubuntu-restricted-extras 15.2
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse unrar 1:3.7.8-1
  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/j/java-common/java-common_0.28ubuntu3_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/j/java-common/java-common_0.28ubuntu3_all.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/u/unixodbc/odbcinst1debian1_2.2.11-16build1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/u/unixodbc/odbcinst1debian1_2.2.11-16build1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/u/unixodbc/unixodbc_2.2.11-16build1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/u/unixodbc/unixodbc_2.2.11-16build1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-bin_6-06-0ubuntu1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-bin_6-06-0ubuntu1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-jre_6-06-0ubuntu1_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-jre_6-06-0ubuntu1_all.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/c/cabextract/cabextract_1.2-2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/c/cabextract/cabextract_1.2-2_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.124.0ubuntu2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.124.0ubuntu2_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gstreamer0.10-pitfdll/gstreamer0.10-pitfdll_0.9.1.1+cvs20080215-1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gstreamer0.10-pitfdll/gstreamer0.10-pitfdll_0.9.1.1+cvs20080215-1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/libc/libcdaudio/libcdaudio1_0.99.12p2-3_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/libc/libcdaudio/libcdaudio1_0.99.12p2-3_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/f/faad2/libfaad0_2.6.1-2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/f/faad2/libfaad0_2.6.1-2_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-common_5.0.51a-3ubuntu5.1_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-common_5.0.51a-3ubuntu5.1_all.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/libmysqlclient15off_5.0.51a-3ubuntu5.1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/libmysqlclient15off_5.0.51a-3ubuntu5.1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/gmyth/libgmyth0_0.7.debian1-1~hardy1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/gmyth/libgmyth0_0.7.debian1-1~hardy1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/libi/libiptcdata/libiptcdata0_1.0.2-2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/libi/libiptcdata/libiptcdata0_1.0.2-2_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/libf/libfreebob/libfreebob0_1.0.7-1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/libf/libfreebob/libfreebob0_1.0.7-1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/j/jack-audio-connection-kit/libjack0_0.109.2-1ubuntu1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/j/jack-audio-connection-kit/libjack0_0.109.2-1ubuntu1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/libm/libmms/libmms0_0.3-6_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/libm/libmms/libmms0_0.3-6_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/libm/libmpcdec/libmpcdec3_1.2.2-1build1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/libm/libmpcdec/libmpcdec3_1.2.2-1build1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/libo/libopenspc/libopenspc0_0.3.99a-2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/libo/libopenspc/libopenspc0_0.3.99a-2_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/s/soundtouch/libsoundtouch1c2_1.3.0-2.2ubuntu0.1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/s/soundtouch/libsoundtouch1c2_1.3.0-2.2ubuntu0.1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/w/wildmidi/libwildmidi0_0.2.2-2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/w/wildmidi/libwildmidi0_0.2.2-2_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-bad0.10/gstreamer0.10-plugins-bad_0.10.6-5_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-bad0.10/gstreamer0.10-plugins-bad_0.10.6-5_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/multiverse/f/faac/libfaac0_1.26-0.1ubuntu1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/multiverse/f/faac/libfaac0_1.26-0.1ubuntu1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/libq/libquicktime/libquicktime1_1.0.0+debian-5_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/libq/libquicktime/libquicktime1_1.0.0+debian-5_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/multiverse/m/mjpegtools/libmjpegtools0c2a_1.8.0-0.2ubuntu5_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/multiverse/m/mjpegtools/libmjpegtools0c2a_1.8.0-0.2ubuntu5_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/multiverse/x/x264/libx264-57_0.svn20071224-0.0ubuntu1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/multiverse/x/x264/libx264-57_0.svn20071224-0.0ubuntu1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/multiverse/x/xvidcore/libxvidcore4_1.1.2-0.1ubuntu3_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/multiverse/x/xvidcore/libxvidcore4_1.1.2-0.1ubuntu3_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/multiverse/g/gst-plugins-bad-multiverse0.10/gstreamer0.10-plugins-bad-multiverse_0.10.6-1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/multiverse/g/gst-plugins-bad-multiverse0.10/gstreamer0.10-plugins-bad-multiverse_0.10.6-1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/multiverse/l/lame/liblame0_3.97-0.0_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/multiverse/l/lame/liblame0_3.97-0.0_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/multiverse/g/gst-plugins-ugly-multiverse0.10/gstreamer0.10-plugins-ugly-multiverse_0.10.7-1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/multiverse/g/gst-plugins-ugly-multiverse0.10/gstreamer0.10-plugins-ugly-multiverse_0.10.7-1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/multiverse/m/msttcorefonts/msttcorefonts_2.4_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/multiverse/m/msttcorefonts/msttcorefonts_2.4_all.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-plugin_6-06-0ubuntu1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-plugin_6-06-0ubuntu1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/multiverse/u/ubuntu-restricted-extras/ubuntu-restricted-extras_15.2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/multiverse/u/ubuntu-restricted-extras/ubuntu-restricted-extras_15.2_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/multiverse/u/unrar-nonfree/unrar_3.7.8-1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/multiverse/u/unrar-nonfree/unrar_3.7.8-1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
chris@chris-laptop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
chris@chris-laptop:~$

---

### Post by Elfy on 2008-10-03
It looks like you were trying to run apt-get while either add/remove/sysnaptic or another terminal running apt-get or aptitude was running.

You can only have one running at a time or it gets locked, if that is not the case sometimes you can unlock it with a reboot.

---

### Post by NewNerd99 on 2008-10-03
I didn't have anything else running at the time, and just to be sure I re booted and tried again with the same result :(

I am going through a proxy server, however 'add/remove' and the synaptics package manager have no problems getting through (I have put in the IP address/port # and authentication for the package manager to get through)

is it something to do with the E: lock file line?

Chris

---

### Post by Elfy on 2008-10-03
Remove the file and do an update 
```
sudo rm /var/lib/apt/lists/lock
sudo apt-get update
```

If ok run the install again

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by NewNerd99 on 2008-10-03
hmm
still no joy...

chris@chris-laptop:~$ sudo rm /var/lib/apt/lists/lock
[sudo] password for chris: 
chris@chris-laptop:~$ sudo apt-get update
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_AU               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_AU           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_AU     
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy Release.gpg                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_AU
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_AU
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main Translation-en_AU                  
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/restricted Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe Translation-en_AU
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                   
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse Translation-en_AU           
Err [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages
  404 Not Found
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/restricted Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/universe Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/multiverse Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy Release
Err [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources
  404 Not Found
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates Release
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
  404 Not Found
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main Packages                        
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                    
  404 Not Found
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/restricted Packages                    
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources              
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages                
  404 Not Found
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main Sources                            
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources                
  404 Not Found
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/restricted Sources                     
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages           
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources               
  404 Not Found
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe Packages                       
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe Sources 
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/restricted Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/restricted Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/universe Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/universe Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/multiverse Packages
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/multiverse Sources
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main Packages    
  404 Not Found [IP: 91.189.88.31 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/restricted Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main Sources     
  404 Not Found [IP: 91.189.88.31 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/restricted Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe Sources 
  404 Not Found [IP: 91.189.88.31 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/restricted Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/restricted Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/universe Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/universe Sources
  404 Not Found [IP: 91.189.88.31 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/multiverse Packages
  404 Not Found [IP: 91.189.88.31 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/multiverse Sources
  404 Not Found [IP: 91.189.88.31 80]
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/hardy/partner/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/hardy/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/hardy/partner/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/source/Sources.gz)  404 Not Found

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/hardy/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz](http://au.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.31 80]

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.31 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
chris@chris-laptop:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  cabextract flashplugin-nonfree gstreamer0.10-pitfdll
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
  gstreamer0.10-plugins-ugly-multiverse java-common libcdaudio1 libfaac0
  libfaad0 libfreebob0 libgmyth0 libiptcdata0 libjack0 liblame0
  libmjpegtools0c2a libmms0 libmpcdec3 libmysqlclient15off libopenspc0
  libquicktime1 libsoundtouch1c2 libwildmidi0 libx264-57 libxvidcore4
  msttcorefonts mysql-common odbcinst1debian1 sun-java6-bin sun-java6-jre
  sun-java6-plugin unixodbc unrar
Suggested packages:
  konqueror-nsplugins libflashsupport ttf-xfree86-nonfree xfs equivs jackd
  binfmt-support sun-java6-fonts ttf-wqy-zenhei libct1 libmyodbc
  odbc-postgresql
Recommended packages:
  w32codecs freepats gsfonts-x11
The following NEW packages will be installed:
  cabextract flashplugin-nonfree gstreamer0.10-pitfdll
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse
  gstreamer0.10-plugins-ugly-multiverse java-common libcdaudio1 libfaac0
  libfaad0 libfreebob0 libgmyth0 libiptcdata0 libjack0 liblame0
  libmjpegtools0c2a libmms0 libmpcdec3 libmysqlclient15off libopenspc0
  libquicktime1 libsoundtouch1c2 libwildmidi0 libx264-57 libxvidcore4
  msttcorefonts mysql-common odbcinst1debian1 sun-java6-bin sun-java6-jre
  sun-java6-plugin ubuntu-restricted-extras unixodbc unrar
0 upgraded, 34 newly installed, 0 to remove and 87 not upgraded.
1 not fully installed or removed.
Need to get 39.3MB of archives.
After this operation, 112MB of additional disk space will be used.
Do you want to continue [Y/n]? y    
WARNING: The following packages cannot be authenticated!
  java-common odbcinst1debian1 unixodbc sun-java6-bin sun-java6-jre cabextract
  flashplugin-nonfree gstreamer0.10-pitfdll libcdaudio1 libfaad0 mysql-common
  libmysqlclient15off libgmyth0 libiptcdata0 libfreebob0 libjack0 libmms0
  libmpcdec3 libopenspc0 libsoundtouch1c2 libwildmidi0
  gstreamer0.10-plugins-bad libfaac0 libquicktime1 libmjpegtools0c2a
  libx264-57 libxvidcore4 gstreamer0.10-plugins-bad-multiverse liblame0
  gstreamer0.10-plugins-ugly-multiverse msttcorefonts sun-java6-plugin
  ubuntu-restricted-extras unrar
Install these packages without verification [y/N]? y
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main java-common 0.28ubuntu3
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main odbcinst1debian1 2.2.11-16build1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main unixodbc 2.2.11-16build1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse sun-java6-bin 6-06-0ubuntu1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse sun-java6-jre 6-06-0ubuntu1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe cabextract 1.2-2
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse flashplugin-nonfree 9.0.124.0ubuntu2
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe gstreamer0.10-pitfdll 0.9.1.1+cvs20080215-1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe libcdaudio1 0.99.12p2-3
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe libfaad0 2.6.1-2
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main mysql-common 5.0.51a-3ubuntu5.1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/main libmysqlclient15off 5.0.51a-3ubuntu5.1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main libgmyth0 0.7.debian1-1~hardy1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe libiptcdata0 1.0.2-2
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe libfreebob0 1.0.7-1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe libjack0 0.109.2-1ubuntu1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe libmms0 0.3-6
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main libmpcdec3 1.2.2-1build1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe libopenspc0 0.3.99a-2
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/universe libsoundtouch1c2 1.3.0-2.2ubuntu0.1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe libwildmidi0 0.2.2-2
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe gstreamer0.10-plugins-bad 0.10.6-5
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse libfaac0 1.26-0.1ubuntu1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe libquicktime1 2:1.0.0+debian-5
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse libmjpegtools0c2a 1:1.8.0-0.2ubuntu5
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse libx264-57 1:0.svn20071224-0.0ubuntu1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse libxvidcore4 2:1.1.2-0.1ubuntu3
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse gstreamer0.10-plugins-bad-multiverse 0.10.6-1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse liblame0 3.97-0.0
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse gstreamer0.10-plugins-ugly-multiverse 0.10.7-1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse msttcorefonts 2.4
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse sun-java6-plugin 6-06-0ubuntu1
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy-updates/multiverse ubuntu-restricted-extras 15.2
  404 Not Found [IP: 91.189.88.46 80]
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/multiverse unrar 1:3.7.8-1
  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/j/java-common/java-common_0.28ubuntu3_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/j/java-common/java-common_0.28ubuntu3_all.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/u/unixodbc/odbcinst1debian1_2.2.11-16build1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/u/unixodbc/odbcinst1debian1_2.2.11-16build1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/u/unixodbc/unixodbc_2.2.11-16build1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/u/unixodbc/unixodbc_2.2.11-16build1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-bin_6-06-0ubuntu1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-bin_6-06-0ubuntu1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-jre_6-06-0ubuntu1_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-jre_6-06-0ubuntu1_all.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/c/cabextract/cabextract_1.2-2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/c/cabextract/cabextract_1.2-2_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.124.0ubuntu2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.124.0ubuntu2_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gstreamer0.10-pitfdll/gstreamer0.10-pitfdll_0.9.1.1+cvs20080215-1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gstreamer0.10-pitfdll/gstreamer0.10-pitfdll_0.9.1.1+cvs20080215-1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/libc/libcdaudio/libcdaudio1_0.99.12p2-3_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/libc/libcdaudio/libcdaudio1_0.99.12p2-3_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/f/faad2/libfaad0_2.6.1-2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/f/faad2/libfaad0_2.6.1-2_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-common_5.0.51a-3ubuntu5.1_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/mysql-common_5.0.51a-3ubuntu5.1_all.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/libmysqlclient15off_5.0.51a-3ubuntu5.1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/m/mysql-dfsg-5.0/libmysqlclient15off_5.0.51a-3ubuntu5.1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/gmyth/libgmyth0_0.7.debian1-1~hardy1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/gmyth/libgmyth0_0.7.debian1-1~hardy1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/libi/libiptcdata/libiptcdata0_1.0.2-2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/libi/libiptcdata/libiptcdata0_1.0.2-2_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/libf/libfreebob/libfreebob0_1.0.7-1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/libf/libfreebob/libfreebob0_1.0.7-1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/j/jack-audio-connection-kit/libjack0_0.109.2-1ubuntu1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/j/jack-audio-connection-kit/libjack0_0.109.2-1ubuntu1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/libm/libmms/libmms0_0.3-6_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/libm/libmms/libmms0_0.3-6_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/libm/libmpcdec/libmpcdec3_1.2.2-1build1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/libm/libmpcdec/libmpcdec3_1.2.2-1build1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/libo/libopenspc/libopenspc0_0.3.99a-2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/libo/libopenspc/libopenspc0_0.3.99a-2_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/s/soundtouch/libsoundtouch1c2_1.3.0-2.2ubuntu0.1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/s/soundtouch/libsoundtouch1c2_1.3.0-2.2ubuntu0.1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/w/wildmidi/libwildmidi0_0.2.2-2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/w/wildmidi/libwildmidi0_0.2.2-2_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-bad0.10/gstreamer0.10-plugins-bad_0.10.6-5_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/g/gst-plugins-bad0.10/gstreamer0.10-plugins-bad_0.10.6-5_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/multiverse/f/faac/libfaac0_1.26-0.1ubuntu1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/multiverse/f/faac/libfaac0_1.26-0.1ubuntu1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/universe/libq/libquicktime/libquicktime1_1.0.0+debian-5_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/universe/libq/libquicktime/libquicktime1_1.0.0+debian-5_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/multiverse/m/mjpegtools/libmjpegtools0c2a_1.8.0-0.2ubuntu5_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/multiverse/m/mjpegtools/libmjpegtools0c2a_1.8.0-0.2ubuntu5_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/multiverse/x/x264/libx264-57_0.svn20071224-0.0ubuntu1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/multiverse/x/x264/libx264-57_0.svn20071224-0.0ubuntu1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/multiverse/x/xvidcore/libxvidcore4_1.1.2-0.1ubuntu3_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/multiverse/x/xvidcore/libxvidcore4_1.1.2-0.1ubuntu3_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/multiverse/g/gst-plugins-bad-multiverse0.10/gstreamer0.10-plugins-bad-multiverse_0.10.6-1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/multiverse/g/gst-plugins-bad-multiverse0.10/gstreamer0.10-plugins-bad-multiverse_0.10.6-1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/multiverse/l/lame/liblame0_3.97-0.0_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/multiverse/l/lame/liblame0_3.97-0.0_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/multiverse/g/gst-plugins-ugly-multiverse0.10/gstreamer0.10-plugins-ugly-multiverse_0.10.7-1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/multiverse/g/gst-plugins-ugly-multiverse0.10/gstreamer0.10-plugins-ugly-multiverse_0.10.7-1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/multiverse/m/msttcorefonts/msttcorefonts_2.4_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/multiverse/m/msttcorefonts/msttcorefonts_2.4_all.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-plugin_6-06-0ubuntu1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/sun-java6-plugin_6-06-0ubuntu1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/multiverse/u/ubuntu-restricted-extras/ubuntu-restricted-extras_15.2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/multiverse/u/ubuntu-restricted-extras/ubuntu-restricted-extras_15.2_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/multiverse/u/unrar-nonfree/unrar_3.7.8-1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/multiverse/u/unrar-nonfree/unrar_3.7.8-1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
chris@chris-laptop:~$

---

### Post by Elfy on 2008-10-03
Ok that's a different problem - do you have the repos set in your sources properly.

Software sources - System > Admin menu - make sure that universe, multiverse, main and restricted are enable and that cdrom is disabled. You can alos enable the partners if you wish on the 3rd party tab.

If they are all ok check your server in the same - if it's set to a local server try the main server, if main try local or use the program to find the best server for you. The files you are getting a 404 for are all reachable here. Are you behind a proxy at all?

---

### Post by NewNerd99 on 2008-10-03
main, universe, restricted and multiverse are all checked.
CD ROM is unchecked.
I changed to main server and got the same results.

Thanks for the suggestions .... am ready for the next lot!!

Chris

---

### Post by DrMega on 2008-10-03
I know you've probably considered this, but I have to ask, is your internet connection working ok? (if you posted your thread from the same machine then obviously the answer is yes).

It seems to me that your machine is failing to connect to the repositories. (hence the 404 messages, 404 is page not found in http terms).

---

### Post by NewNerd99 on 2008-10-03
yep posting on the same machine.
"add/remove" works fine and I am able to download and install packages through the synaptics package manager.

At this point I haven't downloaded all available updates (due download restrictions) would there be something I need to have downloaded before trying those commands or it shouldn't matter?

Once again, thanks for your time.

Cheers
Chris

---

### Post by Elfy on 2008-10-03
You obviously missed the question on proxies - do you have any proxies set up?

Is apt-get the only problem you get - you say add/remove and synaptic work ok - how about aptitude?

---

### Post by NewNerd99 on 2008-10-03
Problem solved???

sort of.....

I went to a site requiring the Java plug in (runescape) and said yes to install it.

It installed and I now have Java 6.

So yes I have Java, but I am concerned that the commands in terminal were unable to produce a result.....

I would like to hear if anyone has any more ideas then will mark the thread as closed tomorrow.

Thanks guys for the suggestions thus far.

Chris

---

### Post by NewNerd99 on 2008-10-03
Forest,
Thanks, I have a proxy set up and (I think) is working fine.

I have just typed in 'Aptitude' in Terminal and a screen has come up. I've never used this screen before. 

Is there a cmd I can use to see if I'm able to access the repositories that have previously given me the 404 errors?

Chris

---

