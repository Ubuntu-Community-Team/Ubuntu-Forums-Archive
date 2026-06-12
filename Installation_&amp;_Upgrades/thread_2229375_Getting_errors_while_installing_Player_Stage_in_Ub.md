---
title: "Getting errors while installing Player Stage in Ubuntu 14.04 64-bit"
date: 2014-06-12
forum: Installation &amp; Upgrades
---

### Post by sam54 on 2014-06-12
Hi, 

I am trying to install player/stage on my machine but I am getting errors after cmake .. 

I am following the instructions from [http://yorkroboticist.blogspot.ca/2011/10/installing-playerstage-in-ubuntu-natty.html](http://yorkroboticist.blogspot.ca/2011/10/installing-playerstage-in-ubuntu-natty.html)

I am attaching the error log and the output files below. Can anyone please help me with this?

[ATTACH]253918[/ATTACH][ATTACH]253919[/ATTACH]

---

### Post by joekeo on 2014-12-20
Any luck with this? I am also trying to install Player on 14.04.

I followed this instructions   [http://playerstage.sourceforge.net/doc/Player-cvs/player/install.html](http://playerstage.sourceforge.net/doc/Player-cvs/player/install.html]http://playerstage.sourceforge.net/doc/Player-cvs/player/install.html)]([http://playerstage.sourceforge.net/doc/Player-cvs/player/install.html) and installed this packages when possible and when not I used the most recent version for 14.04:

sudo apt-get install autotools-dev 
build-essential 
cmake 
cpp
 libboost-thread1.35.0
 libboost-thread1.35-dev 
libboost-signals1.35.0 
libboost-signals1.35-dev 
libcv1 
libcv-dev 
libgdk-pixbuf2 
libgdk-pixbuf-dev
 libgnomecanvas2-0
 libgnomecanvas2-dev
 libgsl0 
libgsl0-dev 
libjpeg62-dev
 libtool 
libxmu-dev 
swig 
freeglut3 
freeglut3-dev
 libfltk1.1 
libfltk1.1-dev 
libgtk2.0-dev 
libltdl7 
libltdl7-dev 
libpng12-0 
libpng12-0-dev

When I try to make it, thios is the error I get:
[EMAIL="pepe@PPC:~/Player_Stage/src/player-3.0.2"]pepe@PPC:~/Player_Stage/src/player-3.0.2[/EMAIL]/build$ make
[  1%] Built target playercommon
[  1%] Generating functiontable_gen.h
[  1%] Built target functiontable_gen
[  1%] Generating interface_table.h
[  1%] Built target interface_table
[  1%] Generating player_interfaces.h
[  2%] Built target player_interfaces
[  4%] Built target playerinterface
[  4%] Generating playerxdr.?
[  4%] Built target playerxdr_src
[  4%] Built target playerjpeg
Linking C shared library libplayerwkb.so
/usr/bin/ld: cannot find -lgeos
collect2: error: ld returned 1 exit status
make[2]: *** [libplayerwkb/libplayerwkb.so.3.0.2] Error 1
make[1]: *** [libplayerwkb/CMakeFiles/playerwkb.dir/all] Error 2
make: *** [all] Error 2

When I use make VERBOSE=1
.
.
.
Linking C shared library libplayerwkb.so
cd /home/pepe/Player_Stage/src/player-3.0.2/build/libplayerwkb && /usr/bin/cmake -E cmake_link_script CMakeFiles/playerwkb.dir/link.txt --verbose=1
/usr/bin/cc  -fPIC  -Wall   -shared -Wl,-soname,libplayerwkb.so.3.0 -o libplayerwkb.so.3.0.2 CMakeFiles/playerwkb.dir/playerwkb.o ../libplayercommon/libplayercommon.so.3.0.2 -lgeos -lgeos_c -Wl,-rpath,/usr/local/lib64 
/usr/bin/ld: cannot find -lgeos
collect2: error: ld returned 1 exit status
make[2]: *** [libplayerwkb/libplayerwkb.so.3.0.2] Error 1
make[2]: Leaving directory `/home/pepe/Player_Stage/src/player-3.0.2/build'
make[1]: *** [libplayerwkb/CMakeFiles/playerwkb.dir/all] Error 2
make[1]: Leaving directory `/home/pepe/Player_Stage/src/player-3.0.2/build'
make: *** [all] Error 2

any idea?

thanks

---

### Post by swaroop.hangal on 2015-01-11
Check out [http://stackoverflow.com/questions/21557845/geos-installation-in-non-standard-location](http://stackoverflow.com/questions/21557845/geos-installation-in-non-standard-location)
You might also need to visit [http://answers.ros.org/question/58779/fuerte-on-fedora-18-build-error-at-rosbag/](http://answers.ros.org/question/58779/fuerte-on-fedora-18-build-error-at-rosbag/) for boost related error.

---

### Post by SeijiSensei on 2015-01-11
> /usr/bin/ld: cannot find -lgeos

You probably need to install libgeos and libgeos-dev:
 
[http://packages.ubuntu.com/trusty/libgeos-3.4.2](http://packages.ubuntu.com/trusty/libgeos-3.4.2)
[http://packages.ubuntu.com/trusty/libgeos-dev](http://packages.ubuntu.com/trusty/libgeos-dev)

---

### Post by pereira2 on 2015-04-29
In order to build player on Ubuntu 14.04 the files listed bellow (and correspondent mods) had to be modified. Note I used [player-3.0.2]("http://sourceforge.net/projects/playerstage/files/Player/3.0.2/player-3.0.2.tar.gz/download").




diff -r player-3.0.2/client_libs/libplayerc++/CMakeLists.txt player-3.0.2_1404/client_libs/libplayerc++/CMakeLists.txt
27c27
<         IF (CMAKE_MAJOR_VERSION EQUAL 2 AND CMAKE_MINOR_VERSION EQUAL 6)
---
>         IF (CMAKE_MAJOR_VERSION EQUAL 2 AND CMAKE_MINOR_VERSION GREATER 6)
45c45
<             FIND_PACKAGE (Boost COMPONENTS ${BOOST_COMPONENTS})
---
>             FIND_PACKAGE (Boost COMPONENTS ${BOOST_COMPONENTS} system)
81c81
<         ELSE (CMAKE_MAJOR_VERSION EQUAL 2 AND CMAKE_MINOR_VERSION EQUAL 6)
---
>         ELSE (CMAKE_MAJOR_VERSION EQUAL 2 AND CMAKE_MINOR_VERSION GREATER 6)
149c149
<         ENDIF (CMAKE_MAJOR_VERSION EQUAL 2 AND CMAKE_MINOR_VERSION EQUAL 6)
---
>         ENDIF (CMAKE_MAJOR_VERSION EQUAL 2 AND CMAKE_MINOR_VERSION GREATER 6)
diff -r player-3.0.2/client_libs/libplayerc++/playerclient.cc player-3.0.2_1404/client_libs/libplayerc++/playerclient.cc
171c171
<     boost::xtime_get(&xt, boost::TIME_UTC);
---
>     boost::xtime_get(&xt, boost::TIME_UTC_);
Only in player-3.0.2_1404/client_libs/libplayerc++: playerclient.cc~
diff -r player-3.0.2/client_libs/libplayerc++/test/CMakeLists.txt player-3.0.2_1404/client_libs/libplayerc++/test/CMakeLists.txt
43c43
<                                ${PLAYERCC_EXTRA_LINK_LIBRARIES})
---
>                                ${PLAYERCC_EXTRA_LINK_LIBRARIES} boost_system)
diff -r player-3.0.2/cmake/internal/SearchForStuff.cmake player-3.0.2_1404/cmake/internal/SearchForStuff.cmake
38c38
< IF (CMAKE_MAJOR_VERSION EQUAL 2 AND CMAKE_MINOR_VERSION EQUAL 6)
---
> IF (CMAKE_MAJOR_VERSION EQUAL 2 AND CMAKE_MINOR_VERSION GREATER 6)
41c41
< ELSE (CMAKE_MAJOR_VERSION EQUAL 2 AND CMAKE_MINOR_VERSION EQUAL 6)
---
> ELSE (CMAKE_MAJOR_VERSION EQUAL 2 AND CMAKE_MINOR_VERSION GREATER 6)
46c46
< ENDIF (CMAKE_MAJOR_VERSION EQUAL 2 AND CMAKE_MINOR_VERSION EQUAL 6)
---
> ENDIF (CMAKE_MAJOR_VERSION EQUAL 2 AND CMAKE_MINOR_VERSION GREATER 6)
diff -r player-3.0.2/examples/libplayerc++/CMakeLists.txt player-3.0.2_1404/examples/libplayerc++/CMakeLists.txt
21c21
<                                ${PLAYERCC_EXTRA_LINK_LIBRARIES})
---
>                                ${PLAYERCC_EXTRA_LINK_LIBRARIES} boost_system)
Only in player-3.0.2_1404/examples/libplayerc++: Makefile
Only in player-3.0.2_1404/examples/libplayerc++: Makefile~
Only in player-3.0.2_1404/examples/libplayerc++: sonarobstacleavoid
Only in player-3.0.2_1404/examples/libplayerc++: wallfollow
diff -r player-3.0.2/server/drivers/shell/readlog.cc player-3.0.2_1404/server/drivers/shell/readlog.cc
668c668
<         ret = gzseek(this->file,0,SEEK_SET);
---
>         ret = gzseek(this->gzfile,0,SEEK_SET);
714c714
<         ret = (gzgets(this->file, this->line, this->line_size) == NULL);
---
>         ret = (gzgets(this->gzfile, this->line, this->line_size) == NULL);
diff -r player-3.0.2/utils/playerjoy/CMakeLists.txt player-3.0.2_1404/utils/playerjoy/CMakeLists.txt
13c13
<                                    ${PLAYERCC_EXTRA_LINK_LIBRARIES} ${PTHREAD_LIB})
---
>                                    ${PLAYERCC_EXTRA_LINK_LIBRARIES} ${PTHREAD_LIB} boost_system)
diff -r player-3.0.2/utils/playerprint/CMakeLists.txt player-3.0.2_1404/utils/playerprint/CMakeLists.txt
26c26
<                                ${playerreplaceLib} ${PLAYERCC_EXTRA_LINK_LIBRARIES})
---
>                                ${playerreplaceLib} ${PLAYERCC_EXTRA_LINK_LIBRARIES} boost_system)
diff -r player-3.0.2/utils/playerprop/CMakeLists.txt player-3.0.2_1404/utils/playerprop/CMakeLists.txt
17c17
<                                ${PLAYERCC_EXTRA_LINK_LIBRARIES})
---
>                                ${PLAYERCC_EXTRA_LINK_LIBRARIES} boost_system)

---

### Post by schnellbe on 2016-02-06
pereira2;
Many thanks for your post. I am a newbie with Player/Stage/Gazebo. Without your help, I would have been _really_ stuck.  :-)

---

### Post by pinftv on 2016-11-08
If anyone want's to install it in ubuntu 14 or 16 I have modify the files and successfully installed it in both. I have write an easy instruction . Please contact me for get the files.

---

