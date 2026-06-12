---
title: "Unmet dependencies errors updating kubuntu"
date: 2019-08-20
forum: Installation &amp; Upgrades
---

### Post by petrogromovo on 2019-08-20
Hello,

I made silly error of installing Opera [COLOR=#333333]386 version[/COLOR] in my kubuntu 18.04(64bit) and next I got errors:

```
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 opera-stable:i386 : PreDepends: apt-transport-https:i386
                     Recommends: pepperflashplugin-nonfree:i386 but it is not installable
                     Recommends: chromium-codecs-ffmpeg-extra:i386 but it is not installed
 slimjet : Depends: libcurl3 but it is not installed or
                    libcurl4 but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

```

I tried to remove this package by :

```
# sudo apt-get remove  opera-stable:i386
Reading package lists... Done                                                                                                                                                                                                                
Building dependency tree                                                                                                                                                                                                                     
Reading state information... Done                                                                                                                                                                                                            
You might want to run 'apt --fix-broken install' to correct these.                                                                                                                                                                           
The following packages have unmet dependencies:                                                                                                                                                                                              
 slimjet : Depends: libcurl3 but it is not going to be installed or                                                                                                                                                                          
                    libcurl4 but it is not going to be installed                                                                                                                                                                             
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

```
I am not sure if 
```
apt --fix-broken install

```is a  safe way to fix it... How to fix these errors correctly ?

```

$ lsb_release -d; uname -r; uname -i
Description:    Ubuntu 18.04.3 LTS
4.15.0-58-generic
x86_64
```

Thanks!

---

### Post by guiverc on 2019-08-20
I just looked up one missing package ([https://packages.ubuntu.com/search?suite=all&searchon=names&keywords=pepperflashplugin-nonfree](https://packages.ubuntu.com/search?suite=all&searchon=names&keywords=pepperflashplugin-nonfree)) so it's available and in 'multiverse' so do you have it enabled?  and as it's a x86/i386 package you need, do you have it enabled for that architecture.

Also note I have `opera` installed, but the x86_64 (64bit) version, so I wonder why you have i386/x86 release of opera installed?

`libcurl3` is found in 'universe' ([https://packages.ubuntu.com/search?suite=all&section=all&arch=any&keywords=libcurl3&searchon=names](https://packages.ubuntu.com/search?suite=all&section=all&arch=any&keywords=libcurl3&searchon=names)), so do you have that enabled?  

If you need help with repositories; [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by westie457 on 2019-08-20
Try these commands ```
sudo dpkg --add-architecture i386
sudo apt update
sudo apt install -f
sudo dpkg --configure -a
```
All being well you should be able to run Opera

---

### Post by petrogromovo on 2019-08-20
Actually I prefer to remove opera i386 and all related i386 libs but not to use it more. Is it possible?

---

### Post by westie457 on 2019-08-20
Because it has partly installed you have to run those commands I posted earlier to (hopefully) finish the installation, then you can uninstall opera followed by removing the i386 libraries and then finally remove the architecture files.

---

### Post by petrogromovo on 2019-08-20
Last 2 commands outputted errors :
```
 qml-module-qtquick-controls:amd64 depends on dpkg (>= 1.15.6~); however:
  Package dpkg is to be removed.
 fonts-sil-abyssinica depends on dpkg (>= 1.15.6~).

Removing dpkg (1.19.0.5ubuntu2.1) ...
 libreoffice-core: dependency problems, but removing anyway as you requested:
 python3-uno depends on libreoffice-core (= 1:6.0.7-0ubuntu0.18.04.8).
 libreoffice-calc depends on libreoffice-core (= 1:6.0.7-0ubuntu0.18.04.8).
 libreoffice-sdbc-hsqldb depends on libreoffice-core (= 1:6.0.7-0ubuntu0.18.04.8).
 libreoffice-base-core depends on libreoffice-core (= 1:6.0.7-0ubuntu0.18.04.8).
 libreoffice-math depends on libreoffice-core (= 1:6.0.7-0ubuntu0.18.04.8).
 libreoffice-impress depends on libreoffice-core (= 1:6.0.7-0ubuntu0.18.04.8).
 libreoffice-kde4 depends on libreoffice-core (= 1:6.0.7-0ubuntu0.18.04.8).
 libreoffice-writer depends on libreoffice-core (= 1:6.0.7-0ubuntu0.18.04.8).
 libreoffice-avmedia-backend-gstreamer depends on libreoffice-core (= 1:6.0.7-0ubuntu0.18.04.8).
 libreoffice-draw depends on libreoffice-core (= 1:6.0.7-0ubuntu0.18.04.8).

Removing libreoffice-core (1:6.0.7-0ubuntu0.18.04.8) ...
 dpkg: fontconfig: dependency problems, but removing anyway as you requested:
 libpango-1.0-0:i386 depends on fontconfig (>= 2.1.91).
 libpango-1.0-0:amd64 depends on fontconfig (>= 2.1.91).
 libqt5gui5:amd64 depends on fontconfig.
 libqtgui4:amd64 depends on fontconfig.

Removing fontconfig (2.12.6-0ubuntu2) ...
Could not exec dpkg!
E: Sub-process /usr/bin/dpkg returned an error code (100)
E: Sub-process dpkg --set-selections returned an error code (100)
E: Couldn't revert dpkg selection for approved remove/purge after an error was encountered!

# sudo dpkg --configure -a
sudo: dpkg: command not found


```

?

---

### Post by westie457 on 2019-08-20
What commands did you use because none of those I posted were to remove anything.
Could you post the commands you used please. We might have an awkward situation here with a lot of work to fix.

---

