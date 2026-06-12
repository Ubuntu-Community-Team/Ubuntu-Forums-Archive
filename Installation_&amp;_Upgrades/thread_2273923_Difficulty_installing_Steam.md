---
title: "Difficulty installing Steam"
date: 2015-04-16
forum: Installation &amp; Upgrades
---

### Post by wally8 on 2015-04-16
I'm new to Ubuntu and recently i have been trying to install steam on it . It installs but when i try running it this crap appears 

```

Steam needs to install these additional packages: 
    libgl1-mesa-dri:i386, libgl1-mesa-glx:i386, libc6:i386
[sudo] password for wally: 
.............................................
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libc6:i386 : Depends: libgcc1:i386 but it is not going to be installed
 libgl1-mesa-dri:i386 : Depends: libdrm-intel1:i386 (>= 2.4.48) but it is not going to be installed
                        Depends: libdrm-nouveau2:i386 (>= 2.4.38) but it is not going to be installed
                        Depends: libdrm-radeon1:i386 (>= 2.4.31) but it is not going to be installed
                        Depends: libdrm2:i386 (>= 2.4.38) but it is not going to be installed
                        Depends: libelf1:i386 (>= 0.142) but it is not going to be installed
                        Depends: libexpat1:i386 (>= 2.0.1) but it is not going to be installed
                        Depends: libgcc1:i386 (>= 1:4.1.1) but it is not going to be installed
                        Depends: libllvm3.4:i386 but it is not going to be installed
                        Depends: libstdc++6:i386 (>= 4.6) but it is not going to be installed
                        Recommends: libtxc-dxtn-s2tc0:i386 but it is not going to be installed or
                                    libtxc-dxtn0:i386
 libgl1-mesa-glx:i386 : Depends: libdrm2:i386 (>= 2.3.1) but it is not going to be installed
                        Depends: libx11-6:i386 (>= 2:1.4.99.1) but it is not going to be installed
                        Depends: libxcb-dri2-0:i386 (>= 1.8) but it is not going to be installed
                        Depends: libxcb-dri3-0:i386 but it is not going to be installed
                        Depends: libxcb-glx0:i386 (>= 1.8) but it is not going to be installed
                        Depends: libxcb-present0:i386 but it is not going to be installed
                        Depends: libxcb-sync1:i386 but it is not going to be installed
                        Depends: libxcb1:i386 (>= 1.9.2) but it is not going to be installed
                        Depends: libxdamage1:i386 (>= 1:1.1) but it is not going to be installed
                        Depends: libxext6:i386 but it is not going to be installed
                        Depends: libxfixes3:i386 but it is not going to be installed
                        Depends: libxxf86vm1:i386 but it is not going to be installed
                        Depends: libudev1:i386 but it is not going to be installed or
                                 libudev0:i386 but it is not installable
E: Unable to correct problems, you have held broken packages.
Press return to continue: 
```

---

### Post by oldos2er on 2015-04-16
Ubuntu version? Did you run ```
sudo apt-get update
``` first?

---

### Post by wally8 on 2015-04-16
yes buddy i tried everything i saw online . I'm running Ubuntu 14.04 LTS..... i have a radeon graphic card . Steam worked like a charm when i had windows on this system ...

---

### Post by wally8 on 2015-04-16
yes buddy i tried everything i saw online . I'm running Ubuntu 14.04 LTS..... i have a radeon graphic card . Steam worked like a charm when i had windows on this system ...

---

### Post by wally8 on 2015-04-17
Please help !

---

