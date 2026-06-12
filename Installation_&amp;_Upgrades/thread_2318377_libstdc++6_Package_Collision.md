---
title: "libstdc++6 Package Collision"
date: 2016-03-25
forum: Installation &amp; Upgrades
---

### Post by bbatten on 2016-03-25
I'm running Ubuntu 14.04 on a 64 bit x86 system.

After installing Silicon Labs SimplicityStudio for Ubuntu, I tried to upgrade my packages using "apt-get -dist-upgrade" and got a message about packages with unmet dependencies along with a suggestion to try "apt-get -f install", which produced a set of messages including the following errors:
```
...
dpkg: error processing archive /var/cache/apt/archives/libstdc++6-armhf-cross_4.8.4-2ubuntu1~14.04.1cross0.11.1_all.deb (--unpack):
 trying to overwrite '/usr/share/gcc-4.8/python/libstdcxx/__init__.py', which is also in package libstdc++6:amd64 4.8.4-2ubuntu1~14.04.1
...
dpkg: error processing archive /var/cache/apt/archives/libstdc++6-powerpc-cross_4.8.4-2ubuntu1~14.04.1cross0.11.1_all.deb (--unpack):
 trying to overwrite '/usr/share/gcc-4.8/python/libstdcxx/__init__.py', which is also in package libstdc++6:amd64 4.8.4-2ubuntu1~14.04.1
... 
```
This command shows __init__.py is indeed shared between two different packages, one 64 bit, and one 32 bit:

```
[3] bryan: dpkg -S /usr/share/gcc-4.8/python/libstdcxx/__init__.py
libstdc++6:amd64, libstdc++6:i386: /usr/share/gcc-4.8/python/libstdcxx/__init__.py
```

libstdc++6:i386 was installed by the SimplicityStudio installer. It was not previously present on my system. This would make that product a suspect, but its install script just does a bunch of apt-get installs of packages from the standard Ubuntu sources.list.

dpkg -L shows both packages share the /usr/share/gcc-4.8/python directory, but I'm not sure why that would be a problem. In the meantime, I'm stuck alternating between trying to upgrade and failing apt-get -f.

Any help would be appreciated. Thanks,

---

### Post by bbatten on 2016-03-27
Looks like the problem is also discussed in Ubuntu questions. See here:

[https://answers.launchpad.net/ubuntu/+source/gcc-4.8-armhf-cross/+question/289204](https://answers.launchpad.net/ubuntu/+source/gcc-4.8-armhf-cross/+question/289204)

for a workaround which worked for me.

---

