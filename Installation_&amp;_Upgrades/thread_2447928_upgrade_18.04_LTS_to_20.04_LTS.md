---
title: "upgrade 18.04 LTS to 20.04 LTS"
date: 2020-07-29
forum: Installation &amp; Upgrades
---

### Post by ortollj on 2020-07-29
Hi

[https://www.linuxtechi.com/upgrade-ubuntu-18-04-lts-to-ubuntu-20-04-lts/](https://www.linuxtechi.com/upgrade-ubuntu-18-04-lts-to-ubuntu-20-04-lts/)



 1333  sudo apt update
 1334  sudo apt upgrade -y
 1335  sudo reboot
 1336  sudo apt --purge autoremove
 1337  sudo apt install update-manager-core -y
 1338  sudo do-release-upgrade
 1339  sudo do-release-upgrade -d

sudo do-release-upgrade -d
I still got the message:

[B]Checking for a new Ubuntu release
Please install all available updates for your release before upgrading.

I forgot to mention this cmd i also did:
sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  wine-stable winehq-stable
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

 [/B]

---

### Post by grahammechanical on 2020-07-30
I will possibly upgrade from 18.04 to 20.04 in a few days. I have made sure that Software & Updates>Updates>Notify me of a new Ubuntu version is set to For long-term support versions. Then in a few days time when 20.04 is put on general release I will expect the update manager to offer an invitation to upgrade. In fact, it usually nags the user to upgrade.

[https://wiki.ubuntu.com/FocalFossa/ReleaseNotes](https://wiki.ubuntu.com/FocalFossa/ReleaseNotes)

> The -d switch is necessary to upgrade from  Ubuntu 18.04 LTS as upgrades have not yet been enabled and will only be  enabled after the first point release of 20.04 LTS.

The first point release comes 6th August

[https://www.omgubuntu.co.uk/2020/05/ubuntu-20-04-1-coming-july](https://www.omgubuntu.co.uk/2020/05/ubuntu-20-04-1-coming-july)


Regards

---

### Post by guiverc on 2020-07-30
I suspect your issue maybe related to 

```
The following packages have been kept back:
  wine-stable winehq-stable
```

I'd check your sources, are those packages official [Ubuntu] packages? do you have any holds on any packages? (esp. them) or any other 3rd party packages.

If you have 3rd party (PPA etc), it's best if you revert them to standard packages, so the *release-upgrade* can work as intended, then adjust to 3rd party if absolutely necessary post-upgrade.

---

### Post by ortollj on 2020-07-31
ok @guiverc, but how can I delete this PPA or remove its protection ?

```
ortollj@ortollj-SATELLITE-C70-B:~$ sudo apt-get update
[sudo] password for ortollj: 
Hit:1 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic InRelease
Get:2 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates InRelease [88,7 kB]                                                                           
Hit:3 [http://ppa.launchpad.net/alessandro-strada/ppa/ubuntu](http://ppa.launchpad.net/alessandro-strada/ppa/ubuntu) bionic InRelease                                                                                                       
Get:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [88,7 kB]                                                                                                        
Hit:5 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                                                                                         
Get:6 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-backports InRelease [74,6 kB]                                                                       
Hit:7 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) bionic InRelease                                               
Get:8 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/main i386 Packages [723 kB]
Get:9 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main amd64 DEP-11 Metadata [46,0 kB]
Get:10 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe Translation-en [227 kB]                          
Get:11 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe amd64 DEP-11 Metadata [49,2 kB]     
Get:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/multiverse amd64 DEP-11 Metadata [2&#8239;464 B]         
Get:13 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 Packages [1&#8239;032 kB]                 
Get:14 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/main amd64 DEP-11 Metadata [294 kB]
Get:15 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/restricted i386 Packages [11,1 kB]
Get:16 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/restricted amd64 Packages [84,8 kB]
Get:17 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/universe i386 Packages [1&#8239;027 kB]
Get:18 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 Packages [1&#8239;097 kB]
Get:19 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/universe amd64 DEP-11 Metadata [279 kB]
Get:20 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/multiverse amd64 Packages [19,3 kB]
Get:21 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/multiverse i386 Packages [8&#8239;540 B]
Get:22 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/multiverse Translation-en [6&#8239;712 B]
Get:23 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-updates/multiverse amd64 DEP-11 Metadata [2&#8239;464 B]
Get:24 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) bionic-backports/universe amd64 DEP-11 Metadata [9&#8239;288 B]
Fetched 5&#8239;172 kB in 4s (1&#8239;372 kB/s)                                       
Reading package lists... Done
```

[B]ortollj@ortollj-SATELLITE-C70-B:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  wine-stable wine-stable-amd64 wine-stable-i386:i386 winehq-stable
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.[/B]

is this package possibly a malware ?

 may I use deborphan ?:[URL="https://ostechnix.com/how-to-find-and-remove-unused-packages-in-linux/"]https://ostechnix.com/how-to-find-and-remove-unused-packages-in-linux/


[/URL]

---

### Post by ortollj on 2020-07-31
**thank you @** [URL="https://ubuntuforums.org/member.php?u=1087323"][B][COLOR=#000000]grahammechanical
maybe i should wait for august 4

[/COLOR][/B][/URL]

---

### Post by CatKiller on 2020-07-31
> **ortollj said:**
> is this package possibly a malware ? 

No, it's Wine, which you've installed to run Windows software. 

```
https://dl.winehq.org/wine-builds/ubuntu/ bionic main
``` 

This is the repository that you added to get Wine from. Over the course of 18.04's lifecycle the Wine project changed their cryptographic key and added a dependency that isn't provided by the Ubuntu repositories and isn't provided by Wine's repository either. Either of those would cause Wine to not update. You can read about both of those [here](https://wiki.winehq.org/Ubuntu). You can either correct those, or use **ppa-purge** to remove the repository setting and use versions of those packages from the standard repositories instead, or simply remove the Wine packages and remove the PPA entry yourself.

---

### Post by grahammechanical on 2020-07-31
Software & Updates>Other software tab is where we can uncheck certain repositories that may interfere with a distribution upgrade. It is there that we can also remove those repositories. The winehq.org repositories are listed there.

Regards

---

