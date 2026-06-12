---
title: "Can't install any software on ubuntu 10.04"
date: 2010-09-06
forum: Installation &amp; Upgrades
---

### Post by zicoe on 2010-09-06
Hi everyone, I'm new to linux, trying to migrate form ms windows to ubuntu. I have already installed ubuntu 10.04 32-bit on my hp compaq presario cq60 laptop, and it is running side-by-side with win vista.
My problems is i cannot instal anything on my ubuntu, the software centre does not have "Install" button next to each software as it is supposed to be, instead there is a "more info" button and when i click on it, it says "the software catalog needs updating"
On the notification area there is a triangle with an exclamation mark inside and hovering the mouse pointer over the tri, it says "software packages are out of date, click to manually update" but on clicking and checking for updates it ends at 105 of 147 then it fails and says that E: 407 Proxy authentication required.
One other thing it seems like i can't ping anything outside my  wan, the prompt just hangs in there, but surprisingly i have Internet.

Somebody please help, this is stressing  me, really.

---

### Post by azertyh on 2010-09-06
hi,
try [synaptic]("http://ubuntuforums.org/showthread.php?t=781352") to install software.

---

### Post by 73ckn797 on 2010-09-06
Have you gone to System/Software Sources/Ubuntu Software and checked all options? Do the same for the Other Software tab also

---

### Post by zicoe on 2010-09-09
I have checked all options yes but now when i try to update, it says "Down loading package 141 of 184" then it stops and says "Could not download all repository indexes". Then it shows this:

Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/lucid/partner/binary-i386/Packages.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/partner/source/Sources.gz](http://archive.canonical.com/ubuntu/dists/lucid/partner/source/Sources.gz)  407  Proxy Authentication Required
Failed to fetch [http://ppa.launchpad.net/example/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/example/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  407  Proxy Authentication Required
Failed to fetch [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-backports/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-backports/main/binary-i386/Packages.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-backports/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-backports/restricted/binary-i386/Packages.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-backports/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-backports/universe/binary-i386/Packages.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-backports/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-backports/multiverse/binary-i386/Packages.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-backports/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-backports/main/source/Sources.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-backports/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-backports/restricted/source/Sources.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-backports/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-backports/universe/source/Sources.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-backports/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-backports/multiverse/source/Sources.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/restricted/binary-i386/Packages.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/main/binary-i386/Packages.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/multiverse/binary-i386/Packages.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/universe/binary-i386/Packages.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/restricted/source/Sources.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/main/source/Sources.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/multiverse/source/Sources.gz)  407  Proxy Authentication Required
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/universe/source/Sources.gz)  407  Proxy Authentication Required
Some index files failed to download, they have been ignored, or old ones used instead. 


When i try to use Synaptic S/w Manager to install, this is what i get:

An error occurred
The following details are provided

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/abrowser_3.6.8+build1+nobinonly-0ubuntu0.10.04.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/abrowser_3.6.8+build1+nobinonly-0ubuntu0.10.04.1_all.deb)
  407  Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/postfix/postfix_2.7.0-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/postfix/postfix_2.7.0-1_i386.deb)
  407  Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/bsd-mailx/bsd-mailx_8.1.2-0.20090911cvs-2ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/bsd-mailx/bsd-mailx_8.1.2-0.20090911cvs-2ubuntu1_i386.deb)
  407  Proxy Authentication Required

---

### Post by zicoe on 2010-09-09
Thanks guys at last I managed to do it.

---

### Post by phoenix1/4 on 2010-09-30
Hey there, may I ask what you did to fix this? Im having a similar problem, except mine is giving a connection failed error (I'm using a proxy).

---

