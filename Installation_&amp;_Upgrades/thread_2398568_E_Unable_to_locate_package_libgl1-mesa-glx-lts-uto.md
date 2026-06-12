---
title: "E: Unable to locate package libgl1-mesa-glx-lts-utopic:i386"
date: 2018-08-14
forum: Installation &amp; Upgrades
---

### Post by mehmtee10 on 2018-08-14
Hello i installed steam but error :


```
Steam needs to install these additional packages: 
	libgl1-mesa-dri:i386, libgl1-mesa-glx:i386, libc6:i386
[sudo] password for root1: 
.....W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/openjdk-r-ubuntu-ppa-bionic.list:2 and /etc/apt/sources.list.d/openjdk-r-ubuntu-ppa-bionic.list:3
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/openjdk-r-ubuntu-ppa-bionic.list:2 and /etc/apt/sources.list.d/openjdk-r-ubuntu-ppa-bionic.list:4
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/openjdk-r-ubuntu-ppa-bionic.list:2 and /etc/apt/sources.list.d/openjdk-r-ubuntu-ppa-bionic.list:3
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/openjdk-r-ubuntu-ppa-bionic.list:2 and /etc/apt/sources.list.d/openjdk-r-ubuntu-ppa-bionic.list:4


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 libgl1-mesa-dri:i386 : Depends: libglapi-mesa:i386 but it is not going to be installed
                        Depends: libllvm6.0:i386 (>= 1:6.0~svn298832-1~) but it is not going to be installed
 libgl1-mesa-glx:i386 : Depends: libgl1:i386 but it is not going to be installed
                        Depends: libglx-mesa0:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
Press return to continue: 
```

and i trying :

```

sudo apt-get install libc6:i386 libgl1-mesa-dri-lts-utopic:i386 libgl1-mesa-glx-lts-utopic:i386

```

but error:

```

E: Unable to locate package libgl1-mesa-dri-lts-utopic:i386
E: Unable to locate package libgl1-mesa-glx-lts-utopic:i386

```

System: i3 5200  Ubuntu 18.04

---

### Post by deadflowr on 2018-08-14
You definitely don't want anything utopic, as those are all ancient and what you would get from the normal packages in 18.04 are newer and, most likely, better.

But you'll need to fix your warnings and error issues.
Firstly
You need to fix those warnings
Post back the output from
```
cat /etc/apt/sources.list.d/openjdk-r-ubuntu-ppa-bionic.list
```
to see how many duplicate entries there are.

This would be first things first.
Everything else can wait.
(Meaning next step would be to run and post the output for the update and upgrade commands. But I would consider running and posting those moot until the warning are dealt with)

---

