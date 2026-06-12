---
title: "installing package when openJDK (headless) is installed"
date: 2012-03-13
forum: Installation &amp; Upgrades
---

### Post by mikeym on 2012-03-13
Hi, 

Can anyone explain to me what's happening with this deb (yacy) that's pulling in all these extra dependencies? I guess it's something to do with having java headless installed but I'm just guessing.

```

yacy
  Depends: <java2-runtime>
    default-jre
    gcj-4.4-jre
    gcj-4.5-jre
    gcj-4.6-jre
    gcj-jre
    openjdk-6-jre
    openjdk-7-jre
  Depends: sudo
    sudo-ldap
  Depends: debconf
Reading package lists...
Building dependency tree...
Reading state information...
The following extra packages will be installed:
  default-jre default-jre-headless icedtea-6-jre-cacao icedtea-6-jre-jamvm
  icedtea-netx libaccess-bridge-java libaccess-bridge-java-jni libasound2
  libasyncns0 libflac8 libgif4 libjson0 liblcms1 libogg0 libpulse0 libsndfile1     
  libvorbis0a libvorbisenc2 libxi6 libxtst6 openjdk-6-jre
  openjdk-6-jre-headless openjdk-6-jre-lib x11-common
Suggested packages:
  libasound2-plugins libasound2-python liblcms-utils pulseaudio icedtea-plugin
  libnss-mdns sun-java6-fonts ttf-baekmuk ttf-unfonts ttf-unfonts-core
  ttf-sazanami-gothic ttf-kochi-gothic ttf-sazanami-mincho ttf-kochi-mincho
  ttf-wqy-microhei ttf-wqy-zenhei ttf-indic-fonts-core ttf-telugu-fonts
  ttf-oriya-fonts ttf-kannada-fonts ttf-bengali-fonts
The following NEW packages will be installed
  default-jre default-jre-headless icedtea-6-jre-cacao icedtea-6-jre-jamvm
  icedtea-netx libaccess-bridge-java libaccess-bridge-java-jni libasound2

  libasyncns0 libflac8 libgif4 libjson0 liblcms1 libogg0 libpulse0 libsndfile1
  libvorbis0a libvorbisenc2 libxi6 libxtst6 openjdk-6-jre
  openjdk-6-jre-headless openjdk-6-jre-lib x11-common yacy
0 upgraded, 25 newly installed, 0 to remove and 0 not upgraded.
Need to get 59.2 MB of archives.
After this operation, 135 MB of additional disk space will be used.
Do you want to continue [Y/n]? Abort.

```

---

### Post by raja.genupula on 2012-03-14
what  java version now you have installed in your Ubuntu . Java 6 or Java 7 . because its giving all the pkg's related to Java6 ,eventhough that Yacy will depends on both java 7 and java 6 .

---

