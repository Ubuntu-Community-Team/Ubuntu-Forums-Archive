---
title: "Trouble with apt-get"
date: 2007-07-16
forum: Installation &amp; Upgrades
---

### Post by Armetheous on 2007-07-16
I just recently switched from SUSE to Ubuntu. I have Ubuntu server version 7.04 installed, but the problem that I have run into is that I can't seem to get apt-get to work correctly for me. I have tried installing the proftpd and lampp packages and I receive the following error:

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package proftpd

It looks as if its searching for the packages on CDROM. How do I enable it to search online repositories?

Here is what is in my source.list file:

# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty main restricted 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe multiverse

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe multiverse

# Seveas' Ubuntu Packages
# GPG key: 1135D466
deb [http://seveas.imbrandon.com](http://seveas.imbrandon.com) feisty-seveas all 

deb-src [http://mirror2.ubuntulinux.nl/](http://mirror2.ubuntulinux.nl/) feisty-seveas all

# Ubuntu backports project
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse 

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

# Kubuntu.org bleeding edge KDE
# GPG key: DD4D5088
deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) feisty main 

deb-src [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) feisty main

# Kubuntu.org bleeding edge Koffice
# GPG key: DD4D5088
deb [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) feisty main 

deb-src [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) feisty main

# Kubuntu.org bleeding edge amaroK
# GPG key: DD4D5088
deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) feisty main 

deb-src [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) feisty main

# Upstream Wine
# GPG key: 387EE263
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main 

deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main

# Upstream Opera
# GPG key: 6A423791
deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free 

# Upstream Beryl
# GPG key: ed8a569e
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) edgy main-edgy 

deb-src [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) edgy main-edgy

# Medibuntu multimedia packages
# GPG key: 0C5A2783
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free 

deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

# Canonical Commercial packages
# GPG key: 437D05B5
deb [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial main 

deb-src [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial main


Additionally, if someone could tell me how to change my keyboard layout to the standard US keyboard I would really appreciate it.

---

### Post by Armetheous on 2007-07-16
I found the problem.

---

