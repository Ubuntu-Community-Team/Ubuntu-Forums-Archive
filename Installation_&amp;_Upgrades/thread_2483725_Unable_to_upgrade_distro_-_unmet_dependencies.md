---
title: "Unable to upgrade distro - unmet dependencies"
date: 2023-02-07
forum: Installation &amp; Upgrades
---

### Post by leopheard on 2023-02-07
[SIZE=3]Hi all,

I'm running Ubuntu 20.04.5 LTS and trying to upgrade to the latest stable version, but I get the following message:

```
sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  gdb gir1.2-peas-1.0 libpeas-1.0-0 libsmbclient libwbclient0 samba-libs
0 to upgrade, 0 to newly install, 0 to remove and 6 not to upgrade.

```

I'm guessing it's something to do with the software sources?:

```
$ cat /etc/apt/sources.list# deb cdrom:[Ubuntu 18.04.1 LTS _Bionic Beaver_ - Release amd64 (20180725)]/ bionic main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ focal main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ focal main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ focal-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ focal universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic universe
deb http://gb.archive.ubuntu.com/ubuntu/ focal-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ focal multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ focal-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ focal-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu bionic partner
deb-src http://archive.canonical.com/ubuntu focal partner

deb http://gb.archive.ubuntu.com/ubuntu/ focal-security main restricted
# deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
deb http://gb.archive.ubuntu.com/ubuntu/ focal-security universe
# deb-src http://security.ubuntu.com/ubuntu bionic-security universe
deb http://gb.archive.ubuntu.com/ubuntu/ focal-security multiverse
# deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse
# deb https://dl.winehq.org/wine-builds/ubuntu/ focal main # disabled on upgrade to focal
# deb-src https://dl.winehq.org/wine-builds/ubuntu/ bionic main
# deb https://dl.bintray.com/resin-io/debian stable etcher # disabled on upgrade to focal
# deb-src https://dl.bintray.com/resin-io/debian stable etcher
# deb-src https://dl.winehq.org/wine-builds/ubuntu/ bionic main
```

Any help would be appreciated, as the only help I can find is quite a few releases ago and I'm not sure if it would apply to 2022 releases.[/SIZE]

---

### Post by kc1di on 2023-02-07
It shows that there are no upgrades available and 6 packages are being kept back, most likely cause the break something else.  This is normal.  
You can try changing your mirror in software services and see if there is any change.

---

### Post by BBQdave on 2023-02-07
You could also simply install the six packages held back:
$ sudo apt install package package2 package3

This will resolve any missing dependencies for the six packages held back.

---

### Post by ian-weisser on 2023-02-07
Seems a likely case of plain old Phased Updates to me.

Run "apt-cache policy <package_name>" on any of the kept-back packages listed to know for sure.

---

### Post by leopheard on 2023-02-07
Thanks for the reply, I did that with a few, not fully sure what it means though:

```
$ sudo apt-cache policy gdb
gdb:
  Installed: 8.1.1-0ubuntu1
  Candidate: 9.2-0ubuntu1~20.04.1
  Version table:
     9.2-0ubuntu1~20.04.1 500
        500 https://mirror.webworld.ie/ubuntu focal-updates/main amd64 Packages
     9.1-0ubuntu1 500
        500 https://mirror.webworld.ie/ubuntu focal/main amd64 Packages
 *** 8.1.1-0ubuntu1 100
        100 /var/lib/dpkg/status


```

```
$ sudo apt-cache policy samba-libs
samba-libs:
  Installed: 2:4.7.6+dfsg~ubuntu-0ubuntu2.29
  Candidate: 2:4.13.17~dfsg-0ubuntu1.20.04.5
  Version table:
     2:4.13.17~dfsg-0ubuntu1.20.04.5 500
        500 https://mirror.webworld.ie/ubuntu focal-updates/main amd64 Packages
        500 https://mirror.webworld.ie/ubuntu focal-security/main amd64 Packages
     2:4.11.6+dfsg-0ubuntu1 500
        500 https://mirror.webworld.ie/ubuntu focal/main amd64 Packages
 *** 2:4.7.6+dfsg~ubuntu-0ubuntu2.29 100
        100 /var/lib/dpkg/status

```
```
$ sudo apt-cache policy libsmbclient
libsmbclient:
  Installed: 2:4.7.6+dfsg~ubuntu-0ubuntu2.29
  Candidate: 2:4.13.17~dfsg-0ubuntu1.20.04.5
  Version table:
     2:4.13.17~dfsg-0ubuntu1.20.04.5 500
        500 https://mirror.webworld.ie/ubuntu focal-updates/main amd64 Packages
        500 https://mirror.webworld.ie/ubuntu focal-security/main amd64 Packages
     2:4.11.6+dfsg-0ubuntu1 500
        500 https://mirror.webworld.ie/ubuntu focal/main amd64 Packages
 *** 2:4.7.6+dfsg~ubuntu-0ubuntu2.29 100
        100 /var/lib/dpkg/status

```

---

### Post by lucant on 2023-02-07
This happened to me too... Manually install each package... That's what I did...

---

### Post by deadflowr on 2023-02-07
From whatever reason you've had this problem the whole time you've been on 20.04.
Those packages are all from 18.04.
Have you, at some point in time, apt marked anything to be held?
Look at
```
apt-mark showhold
```

---

### Post by leopheard on 2023-02-08
```
apt-mark showhold
``` just gives a new line in the CLI and produces nothing, I assume meaning there are no held packages?

EDIT: I have tried 'fix broken packages' using Synaptic, it says it fixes them but does so instantly, as if it's not done anything at all.

---

### Post by ian-weisser on 2023-02-08
> **deadflowr said:**
> From whatever reason you've had this problem the whole time you've been on 20.04.
Those packages are all from 18.04.

Quite right. Seems not Phased Updates after all. Worse.

I will be eating my hat on this one, just as soon at it marinates a little longer.

Packages left over from 18.04 suggest an incomplete or broken release-upgrade.

---

### Post by oldos2er on 2023-02-08
No need for "sudo" with apt-cache policy or apt policy.

---

### Post by leopheard on 2023-02-09
So, I got it figured.

I didn't have the latest 22.04 repos in my /etc/apt/sources.lst - so I added the latest ones from [Github]("https://gist.githubusercontent.com/hakerdefo/9c99e140f543b5089e32176fe8721f5f/raw/7ac6ccf882bb0d39297962f0baedce5721c9be65/sources.list"): 

```
deb http://archive.ubuntu.com/ubuntu/ jammy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jammy main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ jammy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jammy-updates main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ jammy-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jammy-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu/ jammy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jammy-backports main restricted universe multiverse

deb http://archive.canonical.com/ubuntu/ jammy partner
deb-src http://archive.canonical.com/ubuntu/ jammy partner
```

I then ran ```
sudo apt-get update && sudo apt-get dist-upgrade
```
Unfortunately, my system went into suspend during the long upgrade process, so I got locked out of the screensaver screen in Ubuntu and then had to reboot after a long while. Got a kernel panic screen during bootup. The GRUB screen didn't work when I tried a backup. So I hit Ctrl + Alt + F3 to force the bootup to give a CLI.

It realized that the upgrade was messed up, so I ran:

```
sudo dpkg --configure -a && sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

Then ```
sudo reboot now
``` made the system reboot fine and now I'm running 22.04 LTS. Thanks for your help!

---

