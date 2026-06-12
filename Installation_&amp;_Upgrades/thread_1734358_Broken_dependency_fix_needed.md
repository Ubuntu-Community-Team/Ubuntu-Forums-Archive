---
title: "Broken dependency fix needed"
date: 2011-04-20
forum: Installation &amp; Upgrades
---

### Post by azenz on 2011-04-20
I foolishly tried to install a newer version of VLC from .deb files from a more decent distro on my Ubuntu 10.04. Now I got dependency issues...learning the hard way here. But I got the necessary files to fix it, just not sure how. 

sudo apt-get install libschroedinger-dev gives this:


The following packages have unmet dependencies:
  libschroedinger-dev: Depends: libschroedinger-1.0-0 (= 1.0.9.is.1.0.8-0ubuntu1) but 1.0.10-2 is to be installed
E: Broken packages

So, I went online and downloaded libschroedinger-1.0-0 version 1.0.9.is.1.0.8-0ubuntu1. When wanting to install this .deb file, I of course got the error that a more recent version is already installed. Now, removing libschroedinger-1.0-0 means to remove a huge glut of programs, including ubuntu-desktop. This I find very daunting. Can't I simply force-remove the libschroedinger-1.0-0 1.0.10-2 version, then install the 1.0.9..., without disturbing any dependencies, on the fly so to speak? 

Thanks for your help!!!

---

### Post by bapoumba on 2011-04-20
How exactly did you install vlc ?

---

### Post by azenz on 2011-04-21
> **bapoumba said:**
> How exactly did you install vlc ?

From more recent .deb packages at packages.debian.org, I think I opted for squeeze packages or so. I did manage to fix this in the meantime through massive uninstalling and then re-installing, but the question of on-the-fly package 'exchange' is still very relevant for me and others!

---

### Post by dino99 on 2011-04-21
use this ppa: [https://launchpad.net/~n-muench/+archive/vlc](https://launchpad.net/~n-muench/+archive/vlc)

---

