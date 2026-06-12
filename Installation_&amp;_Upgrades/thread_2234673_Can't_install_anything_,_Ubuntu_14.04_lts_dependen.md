---
title: "Can't install anything , Ubuntu 14.04 lts dependencies !"
date: 2014-07-16
forum: Installation &amp; Upgrades
---

### Post by kamhagh on 2014-07-16
hi, i get Dependencies error while i try to install java

i have no idea what to do i haven't used linux for long! seems my fresh install has  lots of problems ! my ubuntu is fresh 14.04 lts

this is the error :

The following packages have unmet dependencies:

openjdk-7-jre: Depends: openjdk-7-jre-headless (= 7u55-2.4.7-1ubuntu1) but 7u55-2.4.7-1ubuntu1 is to be installed
               Depends: libgif4 (>= 4.1.4) but it is not going to be installed
               Depends: libjpeg8 (>= 8c) but 8c-2ubuntu8 is to be installed
               Depends: libpulse0 (>= 1:0.99.1) but 1:4.0-0ubuntu11 is to be installed
               Depends: libatk-wrapper-java-jni (>= 0.30.4-0ubuntu2) but it is not going to be installed

oh god this feels so horrible, i remember i installed the vlc right after installing ubuntu 13.04 long ago, now i get this:

The following packages have unmet dependencies:

vlc: Depends: vlc-nox (= 2.1.4-0ubuntu14.04.1) but 2.1.4-0ubuntu14.04.1 is to be installed
     Depends: libc6 (>= 2.15) but 2.19-0ubuntu6 is to be installed
     Depends: libfreetype6 (>= 2.2.1) but 2.5.2-1ubuntu2 is to be installed
     Depends: libgcc1 (>= 1:4.1.1) but 1:4.9-20140406-0ubuntu1 is to be installed
     Depends: libqtcore4 (>= 4:4.8.0) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 is to be installed
     Depends: libqtgui4 (>= 4:4.8.0) but 4:4.8.5+git192-g085f851+dfsg-2ubuntu4 is to be installed
     Depends: libsdl-image1.2 (>= 1.2.10) but it is not going to be installed
     Depends: libsdl1.2debian (>= 1.2.11) but it is not going to be installed
     Depends: libstdc++6 (>= 4.6) but 4.8.2-19ubuntu1 is to be installed
     Depends: libtar0 but it is not going to be installed
     Depends: libva-x11-1 (> 1.3.0~) but it is not going to be installed
     Depends: libva1 (> 1.3.0~) but it is not going to be installed
     Depends: libxcb-composite0 but it is not going to be installed
     Depends: libxcb-keysyms1 (>= 0.3.9) but it is not going to be installed
     Depends: libxcb-xv0 (>= 1.2) but it is not going to be installed
     Depends: zlib1g (>= 1:1.2.3.3) but 1:1.2.8.dfsg-1ubuntu1 is to be installed
should i do a reinstall?

EDIT: i re installed ubuntu, i could install java and vlc with no problem ONLY in try ubuntu(from usb) but after the re install ,it still gives me the message that it needs dependencies, i ran sudo apt-get update, the size was so bg so i couldn't do it, also it was really slow !

i want to return to ubuntu :( help me !!!! 96 views and no answer, is my thread bad? i can make a few changed to make it look clean!

---

### Post by bapoumba on 2014-07-16
Please post the output to :
```
cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d
```

---

### Post by kamhagh on 2014-07-18
sorry for long delay i had some net problems, i fixed it, i removed google from other software from ubuntu software center :) now i got new problem with wine, im making a thread in gaming and leisure !!! thanks for reply anyway :)

---

