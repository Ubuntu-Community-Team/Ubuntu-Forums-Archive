---
title: "403 Forbidden - Ubuntu updates ??"
date: 2021-08-16
forum: Installation &amp; Upgrades
---

### Post by oygle on 2021-08-16
```
$ sudo apt-get update
```

> Hit:1 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal InRelease
Hit:2 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal-updates InRelease
Hit:3 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal-backports InRelease
Hit:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease                                                                
Hit:5 [http://ppa.launchpad.net/audio-recorder/ppa/ubuntu](http://ppa.launchpad.net/audio-recorder/ppa/ubuntu) focal InRelease                                                        
Ign:6 [https://www.scootersoftware.com](https://www.scootersoftware.com) bcompare4 InRelease                                                
Hit:7 [http://ppa.launchpad.net/mkusb/ppa/ubuntu](http://ppa.launchpad.net/mkusb/ppa/ubuntu) focal InRelease                                          
Hit:8 [https://www.scootersoftware.com](https://www.scootersoftware.com) bcompare4 Release
Reading package lists... Done

```
$ sudo apt upgrade
```

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  language-pack-en language-pack-en-base libegl-mesa0 libegl1-mesa libgbm1 libgl1-mesa-dri libgl1-mesa-dri:i386 libgl1-mesa-glx
  libglapi-mesa libglapi-mesa:i386 libglx-mesa0 libglx-mesa0:i386 libxatracker2 mesa-va-drivers mesa-vdpau-drivers
  mesa-vulkan-drivers mesa-vulkan-drivers:i386
17 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
Need to get 123 kB/39.6 MB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Err:1 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal-updates/main amd64 libegl-mesa0 amd64 21.0.3-0ubuntu0.3~20.04.1
  403  Forbidden [IP: 202.158.214.106 80]
Err:2 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal-updates/main i386 libglapi-mesa i386 21.0.3-0ubuntu0.3~20.04.1
  403  Forbidden [IP: 202.158.214.106 80]
E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libegl-mesa0_21.0.3-0ubuntu0.3~20.04.1_amd64.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libegl-mesa0_21.0.3-0ubuntu0.3~20.04.1_amd64.deb)  403  Forbidden [IP: 202.158.214.106 80]
E: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libglapi-mesa_21.0.3-0ubuntu0.3~20.04.1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/m/mesa/libglapi-mesa_21.0.3-0ubuntu0.3~20.04.1_i386.deb)  403  Forbidden [IP: 202.158.214.106 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by MAFoElffen on 2021-08-16
> E: Unable to fetch some archives, [COLOR=#ff0000]maybe run apt-get update or try with --fix-missing?[/COLOR]
And after you followed the advice of
```
sudo apt --fix-missing
```
Then what did it do?

Probably the same right? Most of the time, if someone gets a 403 status code "on an Ubuntu Repo or Mirror" its because the repo was either down for maintenance, or in the middle of a repo sync. No worries. Wait a bit and try again.

---

### Post by oygle on 2021-08-16
> **MAFoElffen said:**
> And after you followed the advice of
```
sudo apt --fix-missing
```
Then what did it do?

Probably the same right? Most of the time, if someone gets a 403 status code "on an Ubuntu Repo or Mirror" its because the repo was either down for maintenance, or in the middle of a repo sync. No worries. Wait a bit and try again.

It downloaded and updating everything _except_ the archives with the "403". I just tried it again now, and it was able to retrieve those as well. So it's all okay now. Maybe next time I just wait for a few hours. Thanks for your help.  :)

---

### Post by MAFoElffen on 2021-08-16
Please remember to go to the thread tools in the upper right of the page to mark this as Solved so others can find find your solution (to help them)...

---

