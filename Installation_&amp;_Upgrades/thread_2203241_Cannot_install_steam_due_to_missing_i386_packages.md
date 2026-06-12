---
title: "Cannot install steam due to missing i386 packages"
date: 2014-02-02
forum: Installation &amp; Upgrades
---

### Post by maeries on 2014-02-02
Hi,

I've reinstalled Ubuntu 64bit a few days ago and since then I cannot install steam```
:~$ sudo apt-get install steam
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 libgl1-mesa-dri : Depends: libdrm-intel1 (>= 2.4.48) but it is not going to be installed
                   Depends: libdrm-nouveau2 (>= 2.4.38) but it is not going to be installed
                   Depends: libdrm-radeon1 (>= 2.4.31) but it is not going to be installed
 steam:i386 : Depends: libx11-6:i386 but it is not going to be installed
              Depends: libxcb1:i386 but it is not going to be installed
              Depends: libgl1-mesa-dri:i386 but it is not going to be installed
              Depends: libgl1-mesa-glx:i386 but it is not going to be installed
 ubuntu-system-settings : Depends: indicator-bluetooth (> 0.0.6+13.10.20131010) but it is not going to be installed
                          Depends: indicator-network (>= 0.5.0+13.10.20130918) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```
And apt-get -f install doesn't do anything```
:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Do you have any idea how to solve this?

---

### Post by oldos2er on 2014-02-02
Have you updated your sources since reinstalling? ```
sudo apt-get update && sudo apt-get dist-upgrade
```

Also I think it's best to get the latest steam*deb from Steam's site, [http://store.steampowered.com/about/](http://store.steampowered.com/about/) click 'Install Steam Now'. Let us know if it works or not.

---

### Post by maeries on 2014-02-02
Yes, i ran apt-get update, apt-get (dist-)upgrade, apt-get autoremove and apt-get -f install nearly 100 times.

So, I downloaded steam from steampowered.com and it kinda works. I can start it, but at every start I get this
```
Steam needs to install these additional packages: 
    libgl1-mesa-dri:i386, libgl1-mesa-glx:i386
[sudo] password for user: 
..............................................................................................................................................
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 libgl1-mesa-dri:i386 : Depends: libdrm-intel1:i386 (>= 2.4.38) but it is not going to be installed
                        Depends: libdrm-nouveau2:i386 (>= 2.4.38) but it is not going to be installed
                        Depends: libdrm-radeon1:i386 (>= 2.4.31) but it is not going to be installed
                        Depends: libdrm2:i386 (>= 2.4.38) but it is not going to be installed
                        Depends: libglapi-mesa:i386 but it is not going to be installed
 libgl1-mesa-glx:i386 : Depends: libdrm2:i386 (>= 2.3.1) but it is not going to be installed
                        Depends: libglapi-mesa:i386 (= 9.2.1-1ubuntu3) but it is not going to be installed
                        Depends: libx11-6:i386 (>= 2:1.4.99.1) but it is not going to be installed
                        Depends: libxcb-dri2-0:i386 (>= 1.8) but it is not going to be installed
                        Depends: libxcb-glx0:i386 (>= 1.8) but it is not going to be installed
                        Depends: libxcb1:i386 but it is not going to be installed
                        Depends: libxdamage1:i386 (>= 1:1.1) but it is not going to be installed
                        Depends: libxext6:i386 but it is not going to be installed
                        Depends: libxfixes3:i386 but it is not going to be installed
                        Depends: libxxf86vm1:i386 but it is not going to be installed
 libqt5feedback5 : Depends: libqt5multimedia5 (>= 5.0.2) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```
Also, when I want to install Skype it nearly looks the same ```
:~$ sudo apt-get install skype-bin
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 skype-bin:i386 : Depends: libqtgui4:i386 (>= 4:4.8.0) but it is not going to be installed
                  Depends: libqtwebkit4:i386 (>= 2.2~2011week36) but it is not going to be installed
                  Depends: libgl1-mesa-glx:i386 but it is not going to be installed
                  Recommends: sni-qt:i386 but it is not going to be installed
                  Recommends: libasound2-plugins:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```
Notice that it says here "held broken packages" while steam says only "held packages"

---

### Post by maeries on 2014-02-02
I found something I don't understand. I have to install libdrm2:i386 to get steam working```
:~$ sudo apt-get install libdrm2:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 kmod : Depends: upstart-job
 libqt5feedback5 : Depends: libqt5multimedia5 (>= 5.0.2) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

``` But why does thin not work? I have kmod, upstart, libqt5feedback5 and libqt5multimedia5 installed.

---

### Post by maeries on 2014-02-21
Anyone any idea?

---

