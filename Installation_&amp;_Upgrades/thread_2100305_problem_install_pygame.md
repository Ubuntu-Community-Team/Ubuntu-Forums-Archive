---
title: "problem install pygame"
date: 2013-01-01
forum: Installation &amp; Upgrades
---

### Post by olivalpaulino on 2013-01-01
Good afternoon

i'm trying install pygame in my computer, but this problem appeared. can someone help-me? thank you
______________________________
running install
running build
running build_py
running build_ext
building 'pygame._camera' extension
gcc -pthread -fno-strict-aliasing -g -O2 -DNDEBUG -g -fwrapv -O3 -Wall -Wstrict-prototypes -fPIC -D_REENTRANT -I/usr/X11R6/include -I/usr/local/include/SDL -I/usr/local/include/python2.7 -c src/_camera.c -o build/temp.linux-x86_64-2.7/src/_camera.o
gcc -pthread -fno-strict-aliasing -g -O2 -DNDEBUG -g -fwrapv -O3 -Wall -Wstrict-prototypes -fPIC -D_REENTRANT -I/usr/X11R6/include -I/usr/local/include/SDL -I/usr/local/include/python2.7 -c src/camera_v4l2.c -o build/temp.linux-x86_64-2.7/src/camera_v4l2.o
In file included from src/camera.h:20:0,
                 from src/camera_v4l2.c:22:
src/pygame.h:678:14: warning: ‘PyGAME_C_API’ defined but not used [-Wunused-variable]
gcc -pthread -fno-strict-aliasing -g -O2 -DNDEBUG -g -fwrapv -O3 -Wall -Wstrict-prototypes -fPIC -D_REENTRANT -I/usr/X11R6/include -I/usr/local/include/SDL -I/usr/local/include/python2.7 -c src/camera_v4l.c -o build/temp.linux-x86_64-2.7/src/camera_v4l.o
src/camera_v4l.c: In function ‘v4l_open_device’:
src/camera_v4l.c:29:29: error: storage size of ‘cap’ isn’t known
src/camera_v4l.c:30:23: error: storage size of ‘buf’ isn’t known
src/camera_v4l.c:51:24: error: ‘VIDIOCGCAP’ undeclared (first use in this function)
src/camera_v4l.c:51:24: note: each undeclared identifier is reported only once for each function it appears in
src/camera_v4l.c:63:26: error: ‘VIDIOCGMBUF’ undeclared (first use in this function)
src/camera_v4l.c:30:23: warning: unused variable ‘buf’ [-Wunused-variable]
src/camera_v4l.c:29:29: warning: unused variable ‘cap’ [-Wunused-variable]
In file included from src/camera.h:20:0,
                 from src/camera_v4l.c:20:
src/camera_v4l.c: At top level:
src/pygame.h:678:14: warning: ‘PyGAME_C_API’ defined but not used [-Wunused-variable]
error: command 'gcc' failed with exit status 1
_________________________________________________---
i'm install the python correctly.
I did everything as required on site >>[http://eli.thegreenplace.net/2011/10/10/installing-python-2-7-on-ubuntu/](http://eli.thegreenplace.net/2011/10/10/installing-python-2-7-on-ubuntu/)

installed
Step 1: Prerequisites
sudo apt-get install libreadline-dev
sudo apt-get install libsqlite3-dev
sudo apt-get install libbz2-dev
sudo apt-get install libssl-dev

Step 2: Download and build Python
./configure
make -j

Step 3: Install
sudo make install

Step 4: Install some essential first modules
sudo pip install ipython

The python works correctly.

---

### Post by dino99 on 2013-01-01
sudo apt-get install python-pygame

[https://launchpad.net/ubuntu/+source/pygame](https://launchpad.net/ubuntu/+source/pygame)

---

