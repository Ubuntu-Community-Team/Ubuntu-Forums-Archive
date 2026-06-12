---
title: "[SOLVED] Installing ubuntu-restricted-extras removes packages"
date: 2008-10-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ace214 on 2008-10-15
Soooo I tried to install ubuntu-restricted-extras and it removed a library which seemed to cause a few problems. Any ideas why it did this?

```
$ sudo apt-get install ubuntu-restricted-extras 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gsfonts-x11 gstreamer0.10-pitfdll gstreamer0.10-plugins-ugly-multiverse
  java-common libavcodec-unstripped-51 msttcorefonts odbcinst1debian1
  sun-java6-bin sun-java6-jre sun-java6-plugin unixodbc unrar
Suggested packages:
  equivs ttf-liberation sun-java6-fonts libmyodbc odbc-postgresql libct1
[B]The following packages will be REMOVED:
  libavcodec51 openmovieeditor ubuntustudio-video[/B]
The following NEW packages will be installed:
  gsfonts-x11 gstreamer0.10-pitfdll gstreamer0.10-plugins-ugly-multiverse
  java-common libavcodec-unstripped-51 msttcorefonts odbcinst1debian1
  sun-java6-bin sun-java6-jre sun-java6-plugin ubuntu-restricted-extras
  unixodbc unrar
0 upgraded, 13 newly installed, 3 to remove and 1 not upgraded.
Need to get 37.8MB of archives.
After this operation, 98.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com intrepid/main java-common 0.30ubuntu3 [80.3kB]
Get:2 http://us.archive.ubuntu.com intrepid/multiverse sun-java6-jre 6-07-4ubuntu2 [6326kB]
Get:3 http://us.archive.ubuntu.com intrepid/main odbcinst1debian1 2.2.11-16build2 [66.3kB]
Get:4 http://us.archive.ubuntu.com intrepid/main unixodbc 2.2.11-16build2 [295kB]
Get:5 http://us.archive.ubuntu.com intrepid/multiverse sun-java6-bin 6-07-4ubuntu2 [27.3MB]
Get:6 http://us.archive.ubuntu.com intrepid/main gsfonts-x11 0.20ubuntu1 [10.8kB]
Get:7 http://us.archive.ubuntu.com intrepid/universe gstreamer0.10-pitfdll 0.9.1.1+cvs20080215-1 [77.4kB]
Get:8 http://us.archive.ubuntu.com intrepid/multiverse gstreamer0.10-plugins-ugly-multiverse 0.10.7-2 [42.2kB]
Get:9 http://us.archive.ubuntu.com intrepid/multiverse libavcodec-unstripped-51 3:0.svn20080206-12ubuntu3+unstripped4 [3515kB]
Get:10 http://us.archive.ubuntu.com intrepid/multiverse msttcorefonts 2.5 [31.7kB]
Get:11 http://us.archive.ubuntu.com intrepid/multiverse sun-java6-plugin 6-07-4ubuntu2 [1964B]
Get:12 http://us.archive.ubuntu.com intrepid/multiverse ubuntu-restricted-extras 22 [4226B]
Get:13 http://us.archive.ubuntu.com intrepid/multiverse unrar 1:3.8.2-1 [99.0kB]
Fetched 37.8MB in 2min34s (244kB/s)                                            
Preconfiguring packages ...
(Reading database ... 181229 files and directories currently installed.)
Removing ubuntustudio-video ...
Removing openmovieeditor ...
[B]dpkg: libavcodec51: dependency problems, but removing anyway as you request:
 libavformat52 depends on libavcodec51 (>= 3:0.svn20080206-8) | libavcodec-unstripped-51 (>= 3:0.svn20080206-8); however:
  Package libavcodec51 is to be removed.
  Package libavcodec-unstripped-51 is not installed.
 vlc-nox depends on libavcodec51 (>= 3:0.svn20080206-8) | libavcodec-unstripped-51 (>= 3:0.svn20080206-8); however:
  Package libavcodec51 is to be removed.
  Package libavcodec-unstripped-51 is not installed.
 blender depends on libavcodec51 (>= 3:0.svn20080206-8) | libavcodec-unstripped-51 (>= 3:0.svn20080206-8); however:
  Package libavcodec51 is to be removed.
  Package libavcodec-unstripped-51 is not installed.
 libavdevice52 depends on libavcodec51 (>= 3:0.svn20080206-8) | libavcodec-unstripped-51 (>= 3:0.svn20080206-8); however:
  Package libavcodec51 is to be removed.
  Package libavcodec-unstripped-51 is not installed.
 gstreamer0.10-ffmpeg depends on libavcodec51 (>= 3:0.svn20080206-8) | libavcodec-unstripped-51 (>= 3:0.svn20080206-8); however:
  Package libavcodec51 is to be removed.
  Package libavcodec-unstripped-51 is not installed.
 libsynfig0 depends on libavcodec51 (>= 3:0.svn20080206-8) | libavcodec-unstripped-51 (>= 3:0.svn20080206-8); however:
  Package libavcodec51 is to be removed.
  Package libavcodec-unstripped-51 is not installed.
 ffmpeg depends on libavcodec51 (>= 3:0.svn20080206-8) | libavcodec-unstripped-51 (>= 3:0.svn20080206-8); however:
  Package libavcodec51 is to be removed.
  Package libavcodec-unstripped-51 is not installed.
 libhighgui1 depends on libavcodec51 (>= 3:0.svn20080206-8) | libavcodec-unstripped-51 (>= 3:0.svn20080206-8); however:
  Package libavcodec51 is to be removed.
  Package libavcodec-unstripped-51 is not installed.
 libquicktime1 depends on libavcodec51 (>= 3:0.svn20080206-8) | libavcodec-unstripped-51 (>= 3:0.svn20080206-8); however:
  Package libavcodec51 is to be removed.
  Package libavcodec-unstripped-51 is not installed.
 ffmpeg2theora depends on libavcodec51 (>= 3:0.svn20080206-8) | libavcodec-unstripped-51 (>= 3:0.svn20080206-8); however:
  Package libavcodec51 is to be removed.
  Package libavcodec-unstripped-51 is not installed.
Removing libavcodec51 ...[/B]

```

ADD: Nevermind- didn't read output enough about the alternative being installed... Someone can delete this...

---

