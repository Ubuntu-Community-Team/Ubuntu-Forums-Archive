---
title: "problem at installing gazebo in ubuntu!"
date: 2008-10-17
forum: Installation &amp; Upgrades
---

### Post by swelin on 2008-10-17
I had made these stages.
export PATH=/usr/local/bin:$PATH
export CPATH=/usr/local/include:$CPATH
export LIBRARY_PATH=/usr/local/lib:$LIBRARY_PATH
export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig:$PKG_CONFIG_PATH
cd /usr/local
$ tar xvzf gazebo-0.8-pre3.tar.gz
$ cd gazebo-0.8-pre3
$ scons

But output come like that

scons: Reading SConscript files ...
detected CPU atributes: -mmmx -msse -msse2 -msse3 
Checking for [pkg-config --cflags --libs OGRE]
Package OGRE was not found in the pkg-config search path.
Perhaps you should add the directory containing `OGRE.pc'
to the PKG_CONFIG_PATH environment variable
No package 'OGRE' found
Unable to parse config [pkg-config --cflags --libs OGRE]
Ogre3d and development files are required, but not found.
  [http://www.ogre3d.org/](http://www.ogre3d.org/)
swelin@swelin-laptop:/usr/local/gazebo-0.8-pre3$ ./configure
bash: ./configure: No such file or directory

pls advice me!

---

### Post by Cruz on 2008-11-03
See "Package OGRE was not found", obviously you didn't install OGRE yet. Search for "libogre" in synaptic, most likely you will find libogre14. Install libogre14-dev too.

---

### Post by gauravsc on 2010-01-05
I am trying to install gazebo-0.9.0 on ubuntu 9.04 and getting the following error...
I have installed ODE 0.11.1 in default location..

thanks in advance if anyone can help...

Linking CXX shared library libgazebo_av.so
[ 84%] Built target gazebo_av-shared
[ 85%] Building CXX object server/CMakeFiles/gazebo-exec.dir/main.o
Linking CXX executable gazebo
libgazebo_server.so.0.9.0: undefined reference to `boost::signals::detail::signal_base::signal_base(boost::function2<bool, boost::signals::detail::stored_group, boost::signals::detail::stored_group> const&, boost::any const&)'
libgazebo_server.so.0.9.0: undefined reference to `dMassSetTrimesh'
libgazebo_server.so.0.9.0: undefined reference to `dInitODE'
libgazebo_server.so.0.9.0: undefined reference to `dGeomTriMeshSetLastTransform'
libgazebo_server.so.0.9.0: undefined reference to `dBodySetAngularDamping'
libgazebo_server.so.0.9.0: undefined reference to `dBodySetLinearDamping'
collect2: ld returned 1 exit status
make[2]: *** [server/gazebo] Error 1
make[1]: *** [server/CMakeFiles/gazebo-exec.dir/all] Error 2
make: *** [all] Error 2

---

