---
title: "installing Myth TV problem"
date: 2007-10-08
forum: Installation &amp; Upgrades
---

### Post by indereet on 2007-10-08
When i was first installing mythtv it said that i need to install lame mp3 encoder. After i was done installing that it still would not run the file. I tried sudo make install and then install and then ./configure. none of them work. Could someone please tell me why it is not working. Thanks a lot for your help.


inder@inder-desktop:~/Desktop/mythtv-0.20.2$ ./configure
cat: /etc/ld.so.conf.d/*.conf: No such file or directory
cat: /etc/ld.so.conf.d/*.conf: No such file or directory
cat: /etc/ld.so.conf.d/*.conf: No such file or directory
cat: /etc/ld.so.conf.d/*.conf: No such file or directory
cat: /etc/ld.so.conf.d/*.conf: No such file or directory
cat: /etc/ld.so.conf.d/*.conf: No such file or directory
cat: /etc/ld.so.conf.d/*.conf: No such file or directory
cat: /etc/ld.so.conf.d/*.conf: No such file or directory
cat: /etc/ld.so.conf.d/*.conf: No such file or directory
# Basic Settings
Compile type     release
Compiler cache   no
DistCC           no
Install prefix   /usr/local
CPU              x86 (model name        : Pentium III (Coppermine))
Big Endian       no
MMX enabled      yes

# Input Support
Joystick menu    yes
lirc support     no
Apple Remote     no
Video4Linux sup. yes
ivtv support     yes
FireWire support no
DVB support      no [/usr/include]
DBox2 support    yes
HDHomeRun sup.   yes
CRC Ip Rec sup.  yes
FreeBox support  yes

# Sound Output Support
OSS support      yes
ALSA support     yes
aRts support     no
JACK support     no
DTS passthrough  no

# Video Output Support
x11 support      yes
xrandr support   yes
xv support       yes
XvMC support     no
XvMC VLD support no
XvMC pro support no
XvMC OpenGL sup. no
Mac accel.       no
OpenGL vsync     no
DirectFB         no

# Misc Features
Frontend         yes
Backend          yes

# Bindings
bindings_perl    no
Creating libs/libmyth/mythconfig.h and libs/libmyth/mythconfig.mak

./configure: 3510: qmake: not found
inder@inder-desktop:~/Desktop/mythtv-0.20.2$ sudo make install
make: *** No rule to make target `install'.  Stop.

---

### Post by oled on 2007-10-08
Why compile your own when myth packages is in the repositories????

[https://help.ubuntu.com/community/MythTV]("https://help.ubuntu.com/community/MythTV")

---

### Post by indereet on 2007-10-08
Well i am new to linux and so i think this would probebly be the best way to learn ubuntu.

---

### Post by superm1 on 2007-10-08
I would hardly agree that compiling is the best way to start to learn things in linux.  Install the packages, only compile if you really have a reason that they are needed to be compiled by hand.

---

