---
title: "Ubuntu has been blocked by the current security policy"
date: 2015-04-20
forum: Installation &amp; Upgrades
---

### Post by Anidro on 2015-04-20
After the last upgrade at the start appears the message:
Ubuntu has been blocked by the current security policy


 
 
 After clicking ok the O.S. starts normally. However, why this message appears? Previously I do not have this issue. Can I fix the problem?

---

### Post by dino99 on 2015-04-20
which ubuntu is it ? have you some non trusted packages sources installed ?
what the logs are showing ?

---

### Post by Anidro on 2015-04-20
Ubuntu 14.04 LTS 
My source list is:

```
# deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140417)]/ trusty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) trusty main restricted
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) trusty universe
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) trusty universe
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) trusty-updates universe
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) trusty multiverse
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) trusty multiverse
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) trusty-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
deb-src [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) trusty-proposed universe multiverse main restricted
deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free
```
Which logs are required?

---

### Post by oldfred on 2015-04-21
Is system UEFI.
And is Ubuntu installed in UEFI with secure boot, UEFI (without secure boot), or in CSM boot mode.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

CSM also is without secure boot.
But if you have secure boot on, system should only boot with secure boot, but if not it may give you a warning message saying system is not in secure boot mode which you just ignore. You then could be in either UEFI or CSM. And if setting always both, but one is default it has to switch and may give messages.

Some brands (Acer for one) require you to set an UEFI password to specifically allow any other system than Windows to boot.

Check what UEFI settings you have.

---

### Post by Anidro on 2015-04-21
The BIOS boot options are:

```

BOOT MODE: LEGACY SUPPORT
BOOT PRIORITY: UEFI FIRST
USB BOOT: ENABLED

EFI
UBUNTU (LITEONIT LCS-256M6S)
UBUNTU (LITEONIT LCS-256M6S)

LEGACY
SATA HDD: LITEONIT LCS-256M6S
SATA ODD: MATSHITA DVD-RAM UJ8DB
NETWORK BOOT: ATHEROS BOOT AGENT

```

I want to point out that before the last O.S. update I did not have any kind of problem.

---

### Post by flaymond on 2015-04-21
[QUOTE=Anidro]## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.[/QUOTE]

Do you think this log might telling about software you installed before the update? Thanks.

---

### Post by Anidro on 2015-04-21
The apt history log is:
```

Start-Date: 2015-04-20  16:56:42
Commandline: apt-get upgrade
Upgrade: python3-problem-report:amd64 (2.14.1-0ubuntu3.9, 2.14.1-0ubuntu3.10), veusz:amd64 (1.22-0~ppa1~trusty1, 1.23-0~ppa1~trusty1), veusz-helpers:amd64 (1.22-0~ppa1~trusty1, 1.23-0~ppa1~trusty1), ubuntu-drivers-common:amd64 (0.2.91.8, 0.2.91.9), tzdata-java:amd64 (2015b-0ubuntu0.14.04, 2015c-0ubuntu0.14.04), winetricks:amd64 (0.0+201504152316~ubuntu14.04.1, 0.0+201504162317~ubuntu14.04.1), xserver-xorg-video-intel:amd64 (2.99.910-0ubuntu1.4, 2.99.910-0ubuntu1.6), wine-staging-i386:i386 (1.7.40~ubuntu14.04.1, 1.7.41~ubuntu14.04.1), wine-staging:amd64 (1.7.40~ubuntu14.04.1, 1.7.41~ubuntu14.04.1), wine-staging-amd64:amd64 (1.7.40~ubuntu14.04.1, 1.7.41~ubuntu14.04.1), apport-gtk:amd64 (2.14.1-0ubuntu3.9, 2.14.1-0ubuntu3.10), apport:amd64 (2.14.1-0ubuntu3.9, 2.14.1-0ubuntu3.10), python3-apport:amd64 (2.14.1-0ubuntu3.9, 2.14.1-0ubuntu3.10), tzdata:amd64 (2015b-0ubuntu0.14.04, 2015c-0ubuntu0.14.04), linux-libc-dev:amd64 (3.13.0-49.83, 3.13.0-51.84)
End-Date: 2015-04-20  16:56:57

Start-Date: 2015-04-20  16:57:46
Commandline: apt-get dist-upgrade
Install: linux-signed-image-3.13.0-51-generic:amd64 (3.13.0-51.84, automatic), linux-image-extra-3.13.0-51-generic:amd64 (3.13.0-51.84, automatic), linux-image-3.13.0-51-generic:amd64 (3.13.0-51.84, automatic)
Upgrade: grub-efi-amd64-bin:amd64 (2.02~beta2-9ubuntu1, 2.02~beta2-9ubuntu1.1), grub-efi-amd64:amd64 (2.02~beta2-9ubuntu1, 2.02~beta2-9ubuntu1.1), grub-common:amd64 (2.02~beta2-9ubuntu1, 2.02~beta2-9ubuntu1.1), grub2-common:amd64 (2.02~beta2-9ubuntu1, 2.02~beta2-9ubuntu1.1), linux-signed-image-generic:amd64 (3.13.0.49.56, 3.13.0.51.58)
Remove: grub-efi-amd64-signed:amd64 (1.34.1+2.02~beta2-9ubuntu1)
End-Date: 2015-04-20  16:58:22

Start-Date: 2015-04-20  17:44:52
Commandline: apt-get install linux-headers-3.13.0-51-generic
Install: linux-headers-3.13.0-51:amd64 (3.13.0-51.84, automatic), linux-headers-3.13.0-51-generic:amd64 (3.13.0-51.84)
End-Date: 2015-04-20  17:45:27

```

After these update the problem arose.

---

### Post by Anidro on 2015-04-21
I solved the issue. 
I report below the commands used:
```

sudo apt-get clean 
sudo apt-get autoclean 
sudo apt-get autoremove 
sudo apt-get -f install 
sudo apt-get install grub-efi-amd64-signed

```

Thank you all for the support

---

### Post by flaymond on 2015-04-21
Good job, for solving your own issue and sharing the solution. :D

---

