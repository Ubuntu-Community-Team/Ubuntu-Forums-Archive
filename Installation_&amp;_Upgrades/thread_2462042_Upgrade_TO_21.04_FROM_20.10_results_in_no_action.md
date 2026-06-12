---
title: "Upgrade TO 21.04 FROM 20.10 results in no action"
date: 2021-05-12
forum: Installation &amp; Upgrades
---

### Post by carlo-sanguineti on 2021-05-12
Hello, I am currently currently using Ubuntu 20.10 release. in the configuration as in the following pictures:
[ATTACH=CONFIG]288450[/ATTACH][ATTACH=CONFIG]288451[/ATTACH][ATTACH=CONFIG]288452[/ATTACH][ATTACH=CONFIG]288453[/ATTACH][ATTACH=CONFIG]288454[/ATTACH]
When I launch "Software Updater" from "Activities" the system does tell me that there is a new version, 21.04.
When I click on the "Upgrade..." button, nothing happens.
In the same way, if a do, as described:
1.) First of all, make backup of all your important data. (already done usually)
2.) Then disable or remove Ubuntu PPAs, or third-party repositories. To do so, open Software & Updates utility and go to Other Software tab. (cleaned a lot of stuff)
3.) Next navigate to Updates tab, make sure the value of “Notify me a new Ubuntu version” is set to “For any new version“. (it was already so)
4.) If proprietary drivers are in use, it’s recommended to switch to the open-source drivers under Additional Drivers tab. (it was already done)
5.) Press Ctrl+Alt+T on keyboard to open terminal, and run command to install all system updates: ```
sudo apt update && sudo apt upgrade
```
6.) Restart your machine, then open terminal and run command: ```
update-manager -d
```
The Software Updater will pop-up and prompt you that Ubuntu 21.04 is available.
7.) Click on “Upgrade” button and confirm after reading the release note dialog.
Then, again, nothing happens.

Could someone help me?
Thank you in advance,
Carlo

---

### Post by Frogs Hair on 2021-05-12
Can you clarify please. The title indicates an upgrade from 21.04 t0 20.10 which is not possible anyway and the text of your post states you are running 20.04. There is no direct upgrade path from 20.04 to 21.04 without upgrading 20.10 first.

---

### Post by Dennis N on 2021-05-12
The command I used to upgrade 20.10 to 21.04 was:

```
sudo do-release-upgrade -d
```

Try that.

Note: unless I used the -d (development) option, no new version was found. That was on May 1.

---

### Post by carlo-sanguineti on 2021-05-12
Since I am an idiot, I wrote an idiocy: my upgrade was off course from 20.10 to 21.04. And I'm currently using 20.10. And I'm sorry... I have corrected the post and the related title.

---

### Post by carlo-sanguineti on 2021-05-12
Firstly, Thank you. The result of the command was:
```
sudo do-release-upgrade -d[sudo] password for carlos: 
Checking for a new Ubuntu release
Upgrades to the development release are only 
available from the latest supported release.

```

---

### Post by Dennis N on 2021-05-12
Then leave off the -d. What happens?

---

### Post by carlo-sanguineti on 2021-05-12
If I do not use "-d" i have this result:
```
sudo do-release-upgradeChecking for a new Ubuntu release
Please install all available updates for your release before upgrading.
```
But it looks I have no updates to install.
```
sudo apt-get updateHit:1 http://archive.ubuntu.com/ubuntu groovy InRelease
Hit:2 http://archive.ubuntu.com/ubuntu groovy-updates InRelease
Hit:3 http://archive.ubuntu.com/ubuntu groovy-backports InRelease
Hit:4 http://archive.ubuntu.com/ubuntu groovy-security InRelease
Hit:5 http://archive.canonical.com/ubuntu groovy InRelease
Reading package lists... Done
```

```
sudo apt-get upgradeReading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  adobe-flash-properties-gtk libcgi-fast-perl libcgi-pm-perl libfcgi-perl
  libnvidia-cfg1-435 libnvidia-cfg1-455 libnvidia-common-435
  libnvidia-common-455 libnvidia-compute-435 libnvidia-compute-435:i386
  libnvidia-compute-455 libnvidia-compute-455:i386 libnvidia-decode-435
  libnvidia-decode-435:i386 libnvidia-decode-455 libnvidia-decode-455:i386
  libnvidia-encode-435 libnvidia-encode-435:i386 libnvidia-encode-455
  libnvidia-encode-455:i386 libnvidia-extra-455 libnvidia-fbc1-435
  libnvidia-fbc1-435:i386 libnvidia-fbc1-455 libnvidia-fbc1-455:i386
  libnvidia-gl-435 libnvidia-gl-435:i386 libnvidia-gl-455
  libnvidia-gl-455:i386 libnvidia-ifr1-435 libnvidia-ifr1-435:i386
  libnvidia-ifr1-455 libnvidia-ifr1-455:i386 nvidia-compute-utils-435
  nvidia-compute-utils-455 nvidia-dkms-435 nvidia-dkms-455 nvidia-utils-435
  nvidia-utils-455 python-ptyprocess xserver-xorg-video-nvidia-435
  xserver-xorg-video-nvidia-455
Use 'sudo apt autoremove' to remove them.
The following packages have been kept back:
  dh-python
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded
```

I tried the autoremove
```
sudo apt autoremoveReading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  adobe-flash-properties-gtk libcgi-fast-perl libcgi-pm-perl libfcgi-perl
  libnvidia-cfg1-435 libnvidia-cfg1-455 libnvidia-common-435
  libnvidia-common-455 libnvidia-compute-435 libnvidia-compute-435:i386
  libnvidia-compute-455 libnvidia-compute-455:i386 libnvidia-decode-435
  libnvidia-decode-435:i386 libnvidia-decode-455 libnvidia-decode-455:i386
  libnvidia-encode-435 libnvidia-encode-435:i386 libnvidia-encode-455
  libnvidia-encode-455:i386 libnvidia-extra-455 libnvidia-fbc1-435
  libnvidia-fbc1-435:i386 libnvidia-fbc1-455 libnvidia-fbc1-455:i386
  libnvidia-gl-435 libnvidia-gl-435:i386 libnvidia-gl-455
  libnvidia-gl-455:i386 libnvidia-ifr1-435 libnvidia-ifr1-435:i386
  libnvidia-ifr1-455 libnvidia-ifr1-455:i386 nvidia-compute-utils-435
  nvidia-compute-utils-455 nvidia-dkms-435 nvidia-dkms-455 nvidia-utils-435
  nvidia-utils-455 python-ptyprocess xserver-xorg-video-nvidia-435
  xserver-xorg-video-nvidia-455
0 upgraded, 0 newly installed, 42 to remove and 1 not upgraded.
After this operation, 1,377 kB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 336718 files and directories currently installed.)
Removing adobe-flash-properties-gtk (1:20201231.1-0ubuntu0.20.10.1) ...
Removing libcgi-fast-perl (1:2.15-1) ...
Removing libcgi-pm-perl (4.50-1) ...
Removing libfcgi-perl (0.79-1) ...
Removing xserver-xorg-video-nvidia-435:amd64 (455.45.01-0ubuntu0.20.10.1) ...
Removing libnvidia-cfg1-435:amd64 (455.45.01-0ubuntu0.20.10.1) ...
Removing libnvidia-cfg1-455:amd64 (460.73.01-0ubuntu0.20.10.1) ...
Removing libnvidia-ifr1-435:amd64 (455.45.01-0ubuntu0.20.10.1) ...
Removing libnvidia-gl-435:amd64 (455.45.01-0ubuntu0.20.10.1) ...
Removing libnvidia-ifr1-435:i386 (455.45.01-0ubuntu0.20.10.1) ...
Removing libnvidia-gl-435:i386 (455.45.01-0ubuntu0.20.10.1) ...
Removing libnvidia-common-435 (455.45.01-0ubuntu0.20.10.1) ...
Removing libnvidia-common-455 (460.73.01-0ubuntu0.20.10.1) ...
Removing nvidia-utils-435:amd64 (455.45.01-0ubuntu0.20.10.1) ...
Removing nvidia-compute-utils-435:amd64 (455.45.01-0ubuntu0.20.10.1) ...
Removing libnvidia-compute-435:amd64 (455.45.01-0ubuntu0.20.10.1) ...
Removing libnvidia-encode-435:i386 (455.45.01-0ubuntu0.20.10.1) ...
Removing libnvidia-decode-435:i386 (455.45.01-0ubuntu0.20.10.1) ...
Removing libnvidia-compute-435:i386 (455.45.01-0ubuntu0.20.10.1) ...
Removing libnvidia-compute-455:i386 (460.73.01-0ubuntu0.20.10.1) ...
Removing libnvidia-compute-455:amd64 (460.73.01-0ubuntu0.20.10.1) ...
Removing libnvidia-encode-435:amd64 (455.45.01-0ubuntu0.20.10.1) ...
Removing libnvidia-decode-435:amd64 (455.45.01-0ubuntu0.20.10.1) ...
Removing libnvidia-decode-455:amd64 (460.73.01-0ubuntu0.20.10.1) ...
Removing libnvidia-decode-455:i386 (460.73.01-0ubuntu0.20.10.1) ...
Removing libnvidia-encode-455:amd64 (460.73.01-0ubuntu0.20.10.1) ...
Removing libnvidia-encode-455:i386 (460.73.01-0ubuntu0.20.10.1) ...
Removing libnvidia-extra-455:amd64 (460.73.01-0ubuntu0.20.10.1) ...
Removing libnvidia-fbc1-435:amd64 (455.45.01-0ubuntu0.20.10.1) ...
Removing libnvidia-fbc1-435:i386 (455.45.01-0ubuntu0.20.10.1) ...
Removing libnvidia-fbc1-455:i386 (460.73.01-0ubuntu0.20.10.1) ...
Removing libnvidia-fbc1-455:amd64 (460.73.01-0ubuntu0.20.10.1) ...
Removing libnvidia-gl-455:amd64 (460.73.01-0ubuntu0.20.10.1) ...
Removing libnvidia-gl-455:i386 (460.73.01-0ubuntu0.20.10.1) ...
Removing libnvidia-ifr1-455:i386 (460.73.01-0ubuntu0.20.10.1) ...
Removing libnvidia-ifr1-455:amd64 (460.73.01-0ubuntu0.20.10.1) ...
Removing nvidia-compute-utils-455:amd64 (460.73.01-0ubuntu0.20.10.1) ...
Removing nvidia-dkms-435 (455.45.01-0ubuntu0.20.10.1) ...
Removing nvidia-dkms-455 (460.73.01-0ubuntu0.20.10.1) ...
Removing nvidia-utils-455:amd64 (460.73.01-0ubuntu0.20.10.1) ...
Removing python-ptyprocess (0.6.0-1ubuntu1) ...
Removing xserver-xorg-video-nvidia-455:amd64 (460.73.01-0ubuntu0.20.10.1) ...
Processing triggers for man-db (2.9.3-2) ...

```

Then I tried again with no result
```
sudo do-release-upgrade
Checking for a new Ubuntu release
Please install all available updates for your release before upgrading.

```

---

### Post by deadflowr on 2021-05-12
Use full-upgrade
```
 sudo apt full-upgrade
```

---

### Post by grahammechanical on 2021-05-12
This will help you.

[https://www.omgubuntu.co.uk/2021/05/upgrade-to-ubuntu-21-04-from-20-10](https://www.omgubuntu.co.uk/2021/05/upgrade-to-ubuntu-21-04-from-20-10)


Notice the switch is -c not -d. The d switch will upgrade to a development version. From 21.04 to 21.10 development version.

Also keep in mind that the upgrade path from 20.10 to 21.04 has been blocked because of a bug on some machines that stopped the OS from booting. That seems to have been fixed but it may still need a few hours before the upgrade path is available to all.

Regards

---

### Post by carlo-sanguineti on 2021-05-12
As before,
```
sudo apt full-upgrade[sudo] password for carlos: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  dh-python
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```
Thank you anyway

---

### Post by carlo-sanguineti on 2021-05-12
Not a step beyond...
```
update-manager -cChecking for a new Ubuntu release
Please install all available updates for your release before upgrading.
```

But there are no updates to install.

Thank you anyway

---

### Post by Frogs Hair on 2021-05-12
You can try from the terminal. These commands are often used to upgrade to the development version by just by changing the code name.  

Changes sources list.
```
sudo sed -i 's/groovy/hirsute/g' /etc/apt/sources.list     
```          ```
 sudo apt update 
``````
sudo apt full-upgrade
```

---

### Post by Dennis N on 2021-05-12
```
The following packages have been kept back:
  dh-python
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded
```
See this [Ask Ubuntu question]("https://askubuntu.com/questions/601/the-following-packages-have-been-kept-back-why-and-how-do-i-solve-it"). It may help resolve this.
Consider: You also might just remove this package, do the upgrade to 21.04, and after the upgrade install it again. It's in the 21.04 repository.

---

### Post by carlo-sanguineti on 2021-05-13
Well, this morning, after logging in, a popup appeared, warning me that the full upgrade was not possible since in the past there were some issue, as for example, not authorized software applications installed (but I cleaned up some times ago, despite yesterday there were still a lot of strange ppa that I duly deleted), or an update that went wrong. This it could be, since I had to re-route all links to two internal (on the cabinet) HDD that were suddenly no more reachable (5 minutes of work).
This popup had three buttons: "Settings", "Partial Upgrade" and "Continue" My choice was "Continue" After some installation, the same pop-up went up and this time I choose "Partial Upgrade". Everything went well, and it looks I have now a partial upgrade to 21.04 (I don't know what does it means).
Looking forward to an happy ending, I thank in advance Anybody that will explain me what happened and what I need to do.

Carlo

P.S.

I realized that I have a brand new file on the desktop: chrome-bplhnalbmejffflmhmdahnmmiimfepci-Default.desktop I don't know what it is.

---

### Post by ActionParsnip on 2021-05-13
[https://www.omgubuntu.co.uk/2021/05/upgrade-to-ubuntu-21-04-from-20-10](https://www.omgubuntu.co.uk/2021/05/upgrade-to-ubuntu-21-04-from-20-10)

---

### Post by Frogs Hair on 2021-05-13
> looks I have now a partial upgrade to 21.04 This usually means that packages were withheld due to availability or dependency issues caused by 3rd party software such as PPAs. Partial upgrades are most often seen on development versions of Ubuntu and sometimes on normal releases.Continue to update your system daily and report any errors here.

---

### Post by carlo-sanguineti on 2021-05-13
OK, I understood. Thank you. What can I do now?

---

### Post by Frogs Hair on 2021-05-15
Report any errors.
```
sudo apt update && sudo apt upgrade
```

---

