---
title: "Ubuntu 15.04 can't install steam after update"
date: 2015-04-10
forum: Installation &amp; Upgrades
---

### Post by thanhvt1609 on 2015-04-10
I just update ubuntu and autoremove yesterday, steam disappear, I can not install it again.
```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 steam:i386 : Depends: libgl1-mesa-glx:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```
I try install libgl1-mesa-glx:i386 but no luck.
```

Some packages could not be installed. This may mean that you haverequested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 liboxideqt-qmlplugin : Depends: liboxideqtcore0 (= 1.5.5-0ubuntu1) but it is not going to be installed
                        Depends: liboxideqtquick0 (= 1.5.5-0ubuntu1) but it is not going to be installed
 libqt5gui5-gles : Depends: libgles2-mesa (>= 7.8.1) but it is not going to be installed or
                            libgles2
 libqt5quick5-gles : Depends: libgles2-mesa (>= 7.8.1) but it is not going to be installed or
                              libgles2
 xserver-xorg-core : Depends: libgl1-mesa-glx but it is not going to be installed or
                              libgl1
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```

---

