---
title: "where can i find linux-restricted-modules-2.6.23.8"
date: 2007-12-21
forum: Installation &amp; Upgrades
---

### Post by lime4x4 on 2007-12-21
i need this module for the latest kernel update

---

### Post by igknighted on 2007-12-21
> **lime4x4 said:**
> i need this module for the latest kernel update

What module from that package do you need?  And where did you get kernel 2.6.23.8?  Is this on Hardy?

---

### Post by lime4x4 on 2007-12-21
Running gusty. I updated to the latest kernel on the 19th. I lost my ethernet cards, sound and video cards which are nvidia based. When i try to enable the restricted drivers i get an error about the following linux-restricted-modules-2.6.23.8 is required for this program to run

---

### Post by igknighted on 2007-12-21
> **lime4x4 said:**
> Running gusty. I updated to the latest kernel on the 19th. I lost my ethernet cards, sound and video cards which are nvidia based. When i try to enable the restricted drivers i get an error about the following linux-restricted-modules-2.6.23.8 is required for this program to run

Can you post your /etc/apt/sources.list file please?  As well as the result of the command 'uname -r'.  You should be running the 2.6.22-14 kernel if you have stock gutsy.

EDIT: Did you compile the kernel from source yourself?  If so you likely left out drivers for you sound and ethernet, and you have to manually install the Nvidia drivers for you graphics card.  Try compiling again, but look through all the options when you run 'make menuconfig' to ensure that support is added for all your devices.  Restricted-manager only installs the version from the repo's, which is specifically built for the default gutsy kernel.

---

### Post by lime4x4 on 2007-12-21
i didn't build a new kernel. the software update button was on and when i selected it it showed a new kernel .
I had to revert back to my last working kernel which is 
john@john-feisty:~$ uname -r
2.6.22-14-generic

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) gutsy non-free

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed restricted main multiverse universe

deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free
# gOS Repositories
deb [http://packages.thinkgos.com/gos/](http://packages.thinkgos.com/gos/) painful main
deb-src [http://packages.thinkgos.com/gos/](http://packages.thinkgos.com/gos/) painful main

## Wine, Ubuntu Gutsy (7.10):
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) gutsy main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) gutsy main

---

### Post by lime4x4 on 2007-12-21
On the 19th i took the kernel update which put this in my grub menu

title           Ubuntu 7.10, kernel 2.6.23.8
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.23.8 root=UUID=4f8517f6-634e-43f1-b764-64fd6b4e35ed ro quiet splash
initrd          /boot/initrd.img-2.6.23.8
quiet

title           Ubuntu 7.10, kernel 2.6.23.8 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.23.8 root=UUID=4f8517f6-634e-43f1-b764-64fd6b4e35ed ro single
initrd          /boot/initrd.img-2.6.23.8

---

