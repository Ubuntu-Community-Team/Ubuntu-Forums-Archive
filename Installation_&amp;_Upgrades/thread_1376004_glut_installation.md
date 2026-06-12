---
title: "glut installation"
date: 2010-01-08
forum: Installation &amp; Upgrades
---

### Post by amittalkin on 2010-01-08
hello everyone..

i'm just beginner...and recently i had to work with openGL and GLUT libraries

to install glut libraries ...i got some information while surfing net ...and that was not to compile the source code but to install one or the other packages that contain glut.h etc.., files so as to avoid any complications that may arise from compilation process.

so i started with installing the followng packages:

freeglut3 
freeglut3-dbg 
freeglut3-dev 
libglu1-mesa 
libglu1-mesa-dev 
libglui2c2 
libglui-dev 
libglut3 
libglut3-dev

but i receive the following msg:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
freeglut3 is already the newest version.
libglu1-mesa is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libglu1-mesa-dev: Depends: libglu1-mesa (= 7.4-0ubuntu3.2) but 7.6.0-1ubuntu4 is to be installed
E: Broken packages


i even tried installing  libglu1-mesa separately...i succeeded but still no difference.

later i manullly downloaded   libglu1-mesa-dev and used the followng command:

dpkg -i --force-depends-version libglu1-mesa_7.6.0-1ubuntu4_i386.deb

but still no result.....

can any one help me out please............

i have my assignment pending.

thanks in advance  :-)

---

### Post by SkyNet2029 on 2010-01-08
you really should not cross post in the forums. The answer is on your other post.
 
....
 
```
sudo apt-get -f install
```

---

### Post by c03 on 2011-10-24
I have the same problem and the above does not help! Nothing is fixed by executing the command.

```
c03@u36:~/Downloads/freeglut-2.6.0$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
c03@u36:~/Downloads/freeglut-2.6.0$ sudo apt-get install freeglut3-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 freeglut3-dev : Depends: libgl1-mesa-dev but it is not going to be installed or
                          libgl-dev
                 Depends: libglu1-mesa-dev but it is not going to be installed or
                          libglu-dev
E: Unable to correct problems, you have held broken packages.

```

---

