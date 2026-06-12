---
title: "Upgrading without meta-packages"
date: 2006-05-31
forum: Installation &amp; Upgrades
---

### Post by Tachyon1000 on 2006-05-31
When I first installed breezy I had some problems and had to get it up and running by manually installing X and gnome, etc via apt-get, therefore I never installed the ubuntu-desktop metapackage, nor do I want it as there is alot of programs that I simply don't need in the package.  I have seen a thread or two mentioning problems upgrading without these metapackages in place.  Can anyone confirm or deny these problems when upgrading to dapper and if this problem does exist, is there any solution except installing the metapackage before upgrading?  Thanks.

---

### Post by tikal26 on 2006-06-01
I would actually like to know that to since everytime I try to install I am told that there is something broke.

---

### Post by Tachyon1000 on 2006-06-03
Hi, just thought I might bump this.  Of course, people are having much more pressing problems, but if I could get an answer to this, it would be great.

---

### Post by wbmj on 2006-06-03
I've actually done this.  edit your sources.list by replacing breezy with dapper.
sudo apt-get update
sudo apt-get upgrade
this will only upgrade the install packages on your machine
if you want a full upgrade with the metapackages included the type sudo apt-get dist-upgrade

---

