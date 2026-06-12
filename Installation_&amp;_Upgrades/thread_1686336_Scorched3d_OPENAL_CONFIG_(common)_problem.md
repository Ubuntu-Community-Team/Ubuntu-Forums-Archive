---
title: "Scorched3d OPENAL_CONFIG (common) problem"
date: 2011-02-12
forum: Installation &amp; Upgrades
---

### Post by irfan_s on 2011-02-12
Hi Ubuntu community. I'm the new guy, and this is my first post here :) 
I am trying to install Scorched 3D, version: 43.2a, but the Synaptic gives 42.1, so i deleted the old version and tried manually to install from 

[http://www.playdeb.net/install/scorched3d/43.2a%7Edfsg-1%7Egetdeb1]("http://www.playdeb.net/install/scorched3d/43.2a%7Edfsg-1%7Egetdeb1")

but in the end all I get is the version I had before (42.1). As you can see the link gives 43.2a, but still, it doesn't seem to work. 
I am not the best guy in Ubuntu, but I am not a noob either, so i downloaded 

[http://sourceforge.net/projects/scorched3d/files/scorched3d/Version%2043.2a/Scorched3D-43.2a-src.tar.gz/download](http://sourceforge.net/projects/scorched3d/files/scorched3d/Version%2043.2a/Scorched3D-43.2a-src.tar.gz/download)

and followed the procedure:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

After installing the missing packages, I was happy cause I thought it will go smooth, but
I seem to have a problem with OPENAL_CONFIG, and I searched the net before I posted, but still was unable to find anything related. Everyone posts the problem, and gets no answer, so I hope you guys, the experienced ones, can help. This is my "first" log:

```
user@user-comp:/usr/local/src/Scorched3D-43.2a-src/scorched$ ./configure

...

We highly suggest that you rectify this situation immediately.
checking for OpenGL support... yes
checking for OpenAL support... checking for openal-config... no
*** The openal-config script installed by OpenAL could not be found
*** Make sure openal-config is in your path, or set the OPENAL_CONFIG
*** environment variable to the full path to openal-config.
configure: error: *** Can't find the openal library. Try: http://www.openal.org/
```I did the following thing: 

```
user@user-comp:/usr/local/src/Scorched3D-43.2a-src/scorched$ ./configure ac_cv_path_OPENAL_CONFIG="usr/local/src/Scorched3D-43.2a-src/scorched-dep-osx/config/openal-config" ac_cv_path_FREEALUT_CONFIG="usr/local/src/Scorched3D-43.2a-src/scorched-dep-osx/config/freealut-config"
```

and now I get:

```


...

We highly suggest that you rectify this situation immediately.
checking for OpenGL support... yes
checking for OpenAL support... checking for openal-config... (cached) usr/local/src/Scorched3D-43.2a-src/scorched-dep-osx/config/openal-config
./configure: line 4679: usr/local/src/Scorched3D-43.2a-src/scorched-dep-osx/config/openal-config: No such file or directory
./configure: line 4682: usr/local/src/Scorched3D-43.2a-src/scorched-dep-osx/config/openal-config: No such file or directory
yes
checking for Freealut support... checking for freealut-config... (cached) usr/local/src/Scorched3D-43.2a-src/scorched-dep-osx/config/freealut-config
./configure: line 4739: usr/local/src/Scorched3D-43.2a-src/scorched-dep-osx/config/freealut-config: No such file or directory
./configure: line 4740: usr/local/src/Scorched3D-43.2a-src/scorched-dep-osx/config/freealut-config: No such file or directory
yes
checking for OpenAL compilation... *** Failed to compile using the OpenAL library.
*** CFLAGS =  
configure: error: *** Check the OpenAL library is correctly installed.

```

**I cant understand what to do, since I am not really experienced with these kinds of errors.**

Both the openal-config and freealut-config are in

```
/usr/local/src/Scorched3D-43.2a-src/scorched-dep-osx/config/
```and 

configure is in 

```
/usr/local/src/Scorched3D-43.2a-src/scorched/
```Thank you in advance.

---

### Post by irfan_s on 2011-02-12
OK, it seems I solved the problem. For others who may encounter this same problem:

open the terminal and type:

```
sudo gedit /etc/apt/sources.list
```

add this:

```
deb [http://mirrors.dotsrc.org/getdeb/ubuntu](http://mirrors.dotsrc.org/getdeb/ubuntu) lucid-getdeb apps
deb-src [http://mirrors.dotsrc.org/getdeb/ubuntu](http://mirrors.dotsrc.org/getdeb/ubuntu) lucid-getdeb apps
deb [http://mirrors.dotsrc.org/getdeb/ubuntu](http://mirrors.dotsrc.org/getdeb/ubuntu) lucid-getdeb games
deb-src [http://mirrors.dotsrc.org/getdeb/ubuntu](http://mirrors.dotsrc.org/getdeb/ubuntu) lucid-getdeb games
```

than do 

```
sudo apt-get update

sudo apt-get upgrade
```

Enjoy :)

---

