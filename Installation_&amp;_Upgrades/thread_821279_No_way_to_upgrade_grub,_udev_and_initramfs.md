---
title: "No way to upgrade grub, udev and initramfs"
date: 2008-06-07
forum: Installation &amp; Upgrades
---

### Post by skotos on 2008-06-07
After upgrading from Gutsy to Hardy, I realized that some core applications had not been updated and - worst of all - are not upgradable at all because Synaptic would simply :( remove Ubuntu itself.

The following list shows the current applications levels that I cannot change and/or update.
[LIST]
[*]initramfs-tools 0.85eubuntu20 (now)
[*]grub 0.97-29ubuntu4 (now)
[*]volumeid 093-0ubuntu18 (now)
[*]udev 093-0ubuntu18 (now)
[/LIST]

Official and proposed updates for them are available in the repositories. 
[LIST]
[*]initramfs-tools 0.85eubuntu36 (hardy)
[*]grub 0.97-29ubuntu21 (hardy)
[*]udev 117-8 (hardy)
[/LIST]
[LIST]
[*]initramfs-tools 0.85eubuntu39.1 (hardy-proposed)
[/LIST]

And these are some of the applications that would be removed by Synaptic:
[LIST]
[*]...
[*]gnome-mount
[*]gnome-power-manager
[*]gnome-session
[*]gnome-volume-manager
[*]grub
[*]...
[*]linux-generic
[*]linux-image-2.6.22-14-generic
[*]linux-image-2.6.22-18-generic
[*]linux-image-2.6.22-19-generic
[*]linux-image-generic
[*]linux-restricted-modules-2.6.22-14-generic
[*]linux-restricted-modules-2.6.22-18-generic
[*]linux-restricted-modules-2.6.22-19-generic
[*]linux-restricted-modules-generic
[*]linux-ubuntu-modules-2.6.22-14-generic
[*]linux-ubuntu-modules-2.6.22-18-generic
[*]linux-ubuntu-modules-2.6.22-19-generic
[*]...
[*]ubuntu-desktop
[*]ubuntu-minimal
[*]...
[/LIST]
The involved packages are core ones (boot sequence and devices management).
I am looking for a way not to loose my production environment (update) and have them definitely patched.

---

### Post by dstew on 2008-06-07
How did you originally install those packages? If you installed them by compiling from source, then Synaptic will not be able to un-install them. You will have to uninstall them by hand.

---

### Post by skotos on 2008-06-07
No, I did not compile them. They should be the binaries downloaded from the repositories.

The question might be changed this way: **is it possible and *safe*** (if yes) **to force the installation of the latest versions without removing the dependent files, since we are sure the dependent files will be there later?**

---

### Post by dstew on 2008-06-07
Usually it is not safe to force dpkg to do things. It is trying to protect the integrity of the system. That is, it cannot be certain that the proposed updates will not delete some file that is currently being used to run the computer, so it refuses to update.

The best way to solve a problem like this is to understand it first. Once the problem is understood, you might find that forcing is OK. To do that, do```
sudo apt-get update
sudo apt-get upgrade
```and post the output to the forum.

Also, [this HowTo]("http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html") has some information on how to proceed when you have update problems like this.

---

### Post by skotos on 2008-06-14
> **dstew said:**
> Usually it is not safe to force dpkg to do things...
Yes, dstew. I know. :(
> **dstew said:**
> 
The best way to solve a problem like this is to understand it first... To do that, do```
sudo apt-get update
sudo apt-get upgrade
```and post the output to the forum.
Thanks, your right and I missed them.
This is a great point that has not to be missed.
I did
```
sudo apt-get udate > apt-get_update_output.txt
sudo apt-get upgrade > apt-get_upgrade_output.txt
```
And the output I got is this:
```

Hit http://na.mirror.garr.it hardy Release.gpg
Ign http://na.mirror.garr.it hardy/main Translation-en_US
Hit http://va.archive.ubuntu.com gutsy-backports Release.gpg
Ign http://va.archive.ubuntu.com gutsy-backports/main Translation-en_US
Ign http://na.mirror.garr.it hardy/restricted Translation-en_US
Ign http://va.archive.ubuntu.com gutsy-backports/restricted Translation-en_US
Ign http://va.archive.ubuntu.com gutsy-backports/universe Translation-en_US
Ign http://va.archive.ubuntu.com gutsy-backports/multiverse Translation-en_US
Ign http://na.mirror.garr.it hardy/universe Translation-en_US
Ign http://ppa.launchpad.net hardy Release.gpg
Ign http://ppa.launchpad.net hardy/main Translation-en_US
Ign http://ppa.launchpad.net hardy Release.gpg
Hit http://va.archive.ubuntu.com gutsy-backports Release
Hit http://wine.budgetdedicated.com hardy Release.gpg
Ign http://wine.budgetdedicated.com hardy/main Translation-en_US
Ign http://na.mirror.garr.it hardy/multiverse Translation-en_US
Ign http://ppa.launchpad.net hardy/main Translation-en_US
Ign http://ppa.launchpad.net hardy/universe Translation-en_US
Ign http://ppa.launchpad.net hardy Release.gpg
Ign http://ppa.launchpad.net hardy/main Translation-en_US
Ign http://ppa.launchpad.net gutsy Release.gpg
Ign http://ppa.launchpad.net gutsy/main Translation-en_US
Ign http://ppa.launchpad.net gutsy/universe Translation-en_US
Hit http://wine.budgetdedicated.com hardy Release
Ign http://ppa.launchpad.net hardy Release.gpg
Hit http://va.archive.ubuntu.com gutsy-backports/main Packages
Hit http://na.mirror.garr.it hardy-updates Release.gpg
Hit http://va.archive.ubuntu.com gutsy-backports/restricted Packages
Hit http://va.archive.ubuntu.com gutsy-backports/universe Packages
Hit http://va.archive.ubuntu.com gutsy-backports/multiverse Packages
Ign http://na.mirror.garr.it hardy-updates/main Translation-en_US
Ign http://ppa.launchpad.net hardy/main Translation-en_US
Get:1 http://ppa.launchpad.net hardy Release [27.6kB]
Ign http://wine.budgetdedicated.com hardy/main Packages
Hit http://va.archive.ubuntu.com gutsy-backports/main Sources
Hit http://va.archive.ubuntu.com gutsy-backports/restricted Sources
Hit http://va.archive.ubuntu.com gutsy-backports/universe Sources
Hit http://va.archive.ubuntu.com gutsy-backports/multiverse Sources
Ign http://na.mirror.garr.it hardy-updates/restricted Translation-en_US
Hit http://www.vollstreckernet.de testing Release.gpg
Hit http://wine.budgetdedicated.com hardy/main Packages
Get:2 http://ppa.launchpad.net hardy Release [27.6kB]
Get:3 http://ppa.launchpad.net hardy Release [27.6kB]
Get:4 http://ppa.launchpad.net gutsy Release [27.6kB]
Ign http://na.mirror.garr.it hardy-updates/multiverse Translation-en_US
Hit http://apt.last.fm debian Release.gpg
Ign http://apt.last.fm debian/stable Translation-en_US
Ign http://na.mirror.garr.it hardy-updates/universe Translation-en_US
Hit http://apt.last.fm debian Release
Get:5 http://ppa.launchpad.net hardy Release [27.6kB]
Hit http://packages.medibuntu.org hardy Release.gpg
Ign http://packages.medibuntu.org hardy/free Translation-en_US
Hit http://na.mirror.garr.it hardy-security Release.gpg
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US
Hit http://packages.medibuntu.org hardy Release
Ign http://apt.last.fm debian/stable Packages
Ign http://ppa.launchpad.net hardy/main Packages
Ign http://ppa.launchpad.net hardy/main Sources
Ign http://ppa.launchpad.net hardy/main Packages
Ign http://ppa.launchpad.net hardy/universe Packages
Ign http://ppa.launchpad.net hardy/main Packages
Ign http://ppa.launchpad.net hardy/main Sources
Hit http://debian.vakevainen.fi unstable Release.gpg
Ign http://debian.vakevainen.fi unstable/main Translation-en_US
Ign http://na.mirror.garr.it hardy-security/main Translation-en_US
Ign http://www.vollstreckernet.de testing/amule Translation-en_US
Hit http://apt.last.fm debian/stable Packages
Hit http://packages.medibuntu.org hardy/free Packages
Ign http://na.mirror.garr.it hardy-security/restricted Translation-en_US
Ign http://ppa.launchpad.net gutsy/main Packages
Ign http://ppa.launchpad.net gutsy/universe Packages
Ign http://ppa.launchpad.net hardy/main Packages
Ign http://ppa.launchpad.net hardy/main Sources
Hit http://ppa.launchpad.net hardy/main Packages
Hit http://ppa.launchpad.net hardy/main Sources
Hit http://ppa.launchpad.net hardy/main Packages
Hit http://packages.medibuntu.org hardy/non-free Packages
Hit http://packages.medibuntu.org hardy/free Sources
Hit http://packages.medibuntu.org hardy/non-free Sources
Ign http://na.mirror.garr.it hardy-security/universe Translation-en_US
Hit http://debian.vakevainen.fi unstable Release
Hit http://ppa.launchpad.net hardy/universe Packages
Hit http://ppa.launchpad.net hardy/main Packages
Ign http://na.mirror.garr.it hardy-security/multiverse Translation-en_US
Hit http://na.mirror.garr.it hardy-backports Release.gpg
Hit http://www.vollstreckernet.de testing Release
Hit http://ppa.launchpad.net hardy/main Sources
Hit http://ppa.launchpad.net gutsy/main Packages
Hit http://ppa.launchpad.net gutsy/universe Packages
Hit http://ppa.launchpad.net hardy/main Packages
Hit http://ppa.launchpad.net hardy/main Sources
Ign http://na.mirror.garr.it hardy-backports/restricted Translation-en_US
Hit http://debian.vakevainen.fi unstable/main Packages
Ign http://na.mirror.garr.it hardy-backports/main Translation-en_US
Hit http://moblock-deb.sourceforge.net hardy Release.gpg
Ign http://apt.wicd.net hardy Release.gpg
Ign http://apt.wicd.net hardy/extras Translation-en_US
Ign http://na.mirror.garr.it hardy-backports/multiverse Translation-en_US
Ign http://www.vollstreckernet.de testing/amule Packages
Ign http://na.mirror.garr.it hardy-backports/universe Translation-en_US
Hit http://na.mirror.garr.it hardy-proposed Release.gpg
Ign http://na.mirror.garr.it hardy-proposed/restricted Translation-en_US
Ign http://na.mirror.garr.it hardy-proposed/main Translation-en_US
Hit http://www.vollstreckernet.de testing/amule Packages
Ign http://na.mirror.garr.it hardy-proposed/multiverse Translation-en_US
Get:6 http://apt.wicd.net hardy Release [29.1kB]
Ign http://na.mirror.garr.it hardy-proposed/universe Translation-en_US
Hit http://na.mirror.garr.it hardy Release
Hit http://au.ubuntu.cafuego.net hardy-cafuego Release.gpg
Ign http://au.ubuntu.cafuego.net hardy-cafuego/all Translation-en_US
Hit http://na.mirror.garr.it hardy-updates Release
Hit http://na.mirror.garr.it hardy-security Release
Hit http://na.mirror.garr.it hardy-backports Release
Hit http://na.mirror.garr.it hardy-proposed Release
Hit http://apt.wicd.net hardy/extras Packages
Hit http://na.mirror.garr.it hardy/main Packages
Hit http://na.mirror.garr.it hardy/restricted Packages
Hit http://na.mirror.garr.it hardy/restricted Sources
Ign http://moblock-deb.sourceforge.net hardy/main Translation-en_US
Hit http://na.mirror.garr.it hardy/main Sources
Hit http://na.mirror.garr.it hardy/multiverse Sources
Hit http://na.mirror.garr.it hardy/universe Sources
Hit http://na.mirror.garr.it hardy/universe Packages
Hit http://na.mirror.garr.it hardy/multiverse Packages
Hit http://na.mirror.garr.it hardy-updates/main Packages
Hit http://au.ubuntu.cafuego.net hardy-cafuego Release
Hit http://na.mirror.garr.it hardy-updates/restricted Packages
Hit http://na.mirror.garr.it hardy-updates/multiverse Packages
Hit http://na.mirror.garr.it hardy-updates/universe Packages
Hit http://na.mirror.garr.it hardy-updates/main Sources
Hit http://na.mirror.garr.it hardy-updates/restricted Sources
Hit http://na.mirror.garr.it hardy-updates/multiverse Sources
Hit http://na.mirror.garr.it hardy-updates/universe Sources
Hit http://moblock-deb.sourceforge.net hardy Release
Hit http://au.ubuntu.cafuego.net hardy-cafuego/all Packages
Hit http://na.mirror.garr.it hardy-security/main Packages
Hit http://na.mirror.garr.it hardy-security/restricted Packages
Hit http://na.mirror.garr.it hardy-security/restricted Sources
Hit http://na.mirror.garr.it hardy-security/main Sources
Hit http://na.mirror.garr.it hardy-security/multiverse Sources
Hit http://na.mirror.garr.it hardy-security/universe Sources
Hit http://na.mirror.garr.it hardy-security/universe Packages
Hit http://na.mirror.garr.it hardy-security/multiverse Packages
Hit http://na.mirror.garr.it hardy-backports/restricted Packages
Hit http://na.mirror.garr.it hardy-backports/main Packages
Hit http://moblock-deb.sourceforge.net hardy/main Packages
Hit http://na.mirror.garr.it hardy-backports/multiverse Packages
Hit http://na.mirror.garr.it hardy-backports/universe Packages
Hit http://au.ubuntu.cafuego.net hardy-cafuego/all Sources
Hit http://na.mirror.garr.it hardy-backports/restricted Sources
Hit http://na.mirror.garr.it hardy-backports/main Sources
Hit http://na.mirror.garr.it hardy-backports/multiverse Sources
Hit http://na.mirror.garr.it hardy-backports/universe Sources
Hit http://na.mirror.garr.it hardy-proposed/restricted Packages
Hit http://na.mirror.garr.it hardy-proposed/main Packages
Hit http://na.mirror.garr.it hardy-proposed/multiverse Packages
Hit http://na.mirror.garr.it hardy-proposed/universe Packages
Hit http://na.mirror.garr.it hardy-proposed/restricted Sources
Hit http://na.mirror.garr.it hardy-proposed/main Sources
Hit http://na.mirror.garr.it hardy-proposed/multiverse Sources
Hit http://na.mirror.garr.it hardy-proposed/universe Sources
Hit http://moblock-deb.sourceforge.net hardy/main Sources
Fetched 6B in 3s (2B/s)
Reading package lists...

```
```

Reading package lists...
Building dependency tree...
Reading state information...
The following packages have been kept back:
  grub initramfs-tools udev volumeid
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
```
> **dstew said:**
> 
Also, [this HowTo]("http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html") has some information on how to proceed when you have update problems like this.
Yes, it's truly interesting. Now that I have successfully solved the NVIDIA (btw: envyng-gtk was GREAT!) and the NO SOUND AFTER UPGRADE (thx to posts # 205449 and 5131958 )  issues, I am going to dump the dpkg output too

---

