---
title: "any idea how to fix this broken package: sdl2.0-0"
date: 2014-04-03
forum: Installation &amp; Upgrades
---

### Post by FenrirXIII on 2014-04-03
hi, running 12.04LTS here... you guys know how to fix this issue?

[TABLE="width: 500"]
[TR]
[TD]The following packages have unmet dependencies:

liblove: Depends: libc6 (>= 2.15) but 2.15-0ubuntu10.5 is installed
         Depends: libfreetype6 (>= 2.2.1) but 2.4.8-1ubuntu2.1 is installed
         Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is installed
         Depends: libgl1-mesa-glx but it is not installed
         Depends: libmpg123-0 (>= 1.6.2) but 1.12.1-3.2ubuntu1 is installed
         Depends: libopenal1 (>= 1:1.13) but 1:1.13-4ubuntu3 is installed
         Depends: libphysfs1 (>= 1.1.1) but 2.0.2-5 is installed
         Depends: libsdl2-2.0-0 (>= 2.0.0) but it is not installed
         Depends: libstdc++6 (>= 4.6) but 4.6.3-1ubuntu5 is installed
         Depends: libvorbisfile3 (>= 1.1.2) but 1.3.2-1ubuntu3 is installed
         Depends: libphysfs-1.0-0 but it is a virtual package
libsdl2-dev: Depends: libsdl2-2.0-0 (= 2.0.3ppa3precise1) but it is not installed

[/TD]
[/TR]
[/TABLE]


see image in attachement


i know its probably easy but im working on a few stuff at the moment: you can even say its not big of a deal (if it really isnt)... i thinking its has something to do with LOVE 2D game engine



anyhow, thanks in advance community!! :D

---

### Post by carl4926 on 2014-04-03
Did you do as it suggests?

```
sudo apt-get install -f
```

---

### Post by FenrirXIII on 2014-04-03
yea i did... i thought it would have fixed it but i guess it had some error

[TABLE="width: 500"]
[TR]
[TD]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  ttf-dejavu-extra gir1.2-ubuntuoneui-3.0 linux-headers-3.2.0-51 libsdl2
  lib32gcc1 lib32asound2 lib32nss-mdns gir1.2-unique-3.0 tzdata-java
  linux-headers-3.5.0-23-generic linux-headers-3.5.0-23 libubuntuoneui-3.0-1
  thunderbird-globalmenu linux-headers-3.2.0-51-generic libcmis-0.2-0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libsdl2-2.0-0
The following NEW packages will be installed:
  libsdl2-2.0-0
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0 B/377 kB of archives.
After this operation, 1,089 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 956047 files and directories currently installed.)
Unpacking libsdl2-2.0-0 (from .../libsdl2-2.0-0_2.0.3ppa3precise1_amd64.deb) ...
[COLOR=#ff0000]dpkg: error processing /var/cache/apt/archives/libsdl2-2.0-0_2.0.3ppa3precise1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libSDL2-2.0.so.0', which is also in package libsdl2 2.0.1ppa1precise1
Errors were encountered while processing:
 /var/cache/apt/archives/libsdl2-2.0-0_2.0.3ppa3precise1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR]

[/TD]
[/TR]
[/TABLE]

---

### Post by FenrirXIII on 2014-04-03
nevermind fixed the problem by using Synaptic package manager... i uninstalled Love2d and liblove that came along with it... (i would probably just get the newer version on site) then i was able to uninstall the libsdl2 2.0 that came with THAT dependency and install the libsdl2 that prompt me to... so, i would mark this as SOLVE

---

