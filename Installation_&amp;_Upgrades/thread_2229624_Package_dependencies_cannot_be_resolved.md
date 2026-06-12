---
title: "Package dependencies cannot be resolved"
date: 2014-06-14
forum: Installation &amp; Upgrades
---

### Post by jaime3 on 2014-06-14
Hi I'm having this issue when installing Audacity. 

Package dependencies cannot be resolved


This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

audacity: Depends: audacity-data (= 2.0.5+svn20140613+r8405+28+29+29~ubuntu12.04.1) but 2.0.5+svn20140613+r8405+28+29+29~ubuntu12.04.1 is to be installed
          Depends: libavcodec-extra-53 (>= 4:0.8-1~) but 4:0.8.12ubuntu0.12.04.1 is to be installed
          Depends: libavformat-extra-53 (>= 4:0.8-1~) but 4:0.8.12ubuntu0.12.04.1 is to be installed
          Depends: libavutil-extra-51 (>= 4:0.8-1~) but 4:0.8.12ubuntu0.12.04.1 is to be installed
          Depends: libc6 (>= 2.15) but 2.15-0ubuntu10.5 is to be installed
          Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
          Depends: libglib2.0-0 (>= 2.12.0) but 2.32.4-0ubuntu1 is to be installed
          Depends: libgtk2.0-0 (>= 2.8.0) but 2.24.10-0ubuntu6.1 is to be installed
          Depends: libid3tag0 (>= 0.15.1b) but it is not going to be installed
          Depends: libportaudio2 (>= 19+svn20101113-2~) but 19+svn20111121-1 is to be installed
          Depends: libstdc++6 (>= 4.4.0) but 4.6.3-1ubuntu5 is to be installed
          Depends: libwxbase2.8-0 (>= 2.8.12.1) but 2.8.12.1-6ubuntu2 is to be installed
          Depends: libwxgtk2.8-0 (>= 2.8.12.1) but 2.8.12.1-6ubuntu2 is to be installed

---

### Post by alexandari on 2014-06-14
Hello! Try this command,it will try to install the missing dependencies
```
 sudo apt-get -f install 
```

---

### Post by bapoumba on 2014-06-14
Please post the outputs to :
```
cat -n /etc/apt/sources.list
ls /etc/apt/sources.list.d
```

And the exact outputs to
```
sudo apt-get update
sudo apt-get upgrade
```

Conflicting packages versions usually mean third party or ppa repositories problems.

---

