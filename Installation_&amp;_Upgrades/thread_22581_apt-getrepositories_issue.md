---
title: "apt-get/repositories issue"
date: 2005-03-28
forum: Installation &amp; Upgrades
---

### Post by chili on 2005-03-28
Goal is to get apt-get running error free and I see to have nothing but errors.

[COLOR=Red]Here is my sources.list:[/COLOR]

deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview amd64 Binary-1 (20041020)]/ unstable main restricted

## Main sources - Ubuntu Warty
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted

## Main sources - Ubuntu Warty security updates
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted

## Universe sources - Ubuntu Warty
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe

## Multiverse sources - Ubuntu Warty
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse

## Java sources - Ubuntu Warty
deb [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) warty java

## Backport sources - Ubuntu Warty
deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) warty-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) warty-extras main universe multiverse restricted

## Marillat's Sources (MPlayer, w32 video codecs, etc.)
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main

---------------------------------------------------------------------------------------------------------------

[COLOR=Red]Here is an example when I run apt-get update[/COLOR]

Ign [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Release
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable/main Packages
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable/main Release
Fetched 932B in 4s (224B/s)
Failed to fetch [http://ubuntu.tower-net.de/ubuntu/dists/warty/java/binary-amd64/Packages.gz](http://ubuntu.tower-net.de/ubuntu/dists/warty/java/binary-amd64/Packages.gz)  404 Not Found
Failed to fetch [ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-amd64/Packages.gz](ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-amd64/Packages.gz)  Unable to fetch file, server said '/debian-marillat/dists/stable/main/binary-amd64/Packages.gz: No such file or directory  '
Failed to fetch [ftp://ftp.nerim.net/debian-marillat/dists/testing/main/binary-amd64/Packages.gz](ftp://ftp.nerim.net/debian-marillat/dists/testing/main/binary-amd64/Packages.gz)  Unable to fetch file, server said '/debian-marillat/dists/testing/main/binary-amd64/Packages.gz: No such file or directory  '
Reading Package Lists... Done
W: Couldn't stat source package list [http://ubuntu.tower-net.de](http://ubuntu.tower-net.de) warty/java Packages (/var/lib/apt/lists/ubuntu.tower-net.de_ubuntu_dists_warty_java_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu.tower-net.de](http://ubuntu.tower-net.de) warty/java Packages (/var/lib/apt/lists/ubuntu.tower-net.de_ubuntu_dists_warty_java_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

Am I getting these error because of my AMD64 proc??  Are there different repositories for AMD64?

At a loss.  Any help would be greatly appreciated.  And if I forgot to post something that would be helpful please let me know.

Chili

---

### Post by PMO6022 on 2005-03-28
Maybe try running 

sudo apt-get update first.

---

### Post by chili on 2005-03-28
I did run apt-get as root.

---

### Post by PMO6022 on 2005-03-28
Since the problem seems to be limited to some non-supported repo's (java sources and marillat) try commenting out the problematic sources in /etc/apt/sources.list and apt-get update again.  If it works, then the problem is probably with those sources.  Just try them periodically.  I don't have either of those enabled, myself, so I don't know if they are currently working or not.

---

### Post by seasidebaz on 2005-03-29
my problem with apt is that the marillat repo will not load... i installed his pgp key as per instructions on website but it still says key unavailable!

---

