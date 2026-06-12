---
title: "Synaptic, apt-* and dpkg, and repositories"
date: 2005-06-07
forum: Installation &amp; Upgrades
---

### Post by pkoufalas on 2005-06-07
G'day all, I have a few basic questions regarding my new Ubuntu 5.04 installation.

For my Knoppix installation, I typically download packages to usb stick and install them via dpkg; I resolve dependencies and conflicts as they crop up. I do this as I don't have broadband and get around this by downloading packages to usb stick when away from my home PC. I'll need to do the same for Ubuntu. I'd much rather use Synaptic or apt-get but my understanding is that repositories are more than just directories with *.deb files in them, correct?  Secondly, I download packages for my Knoppix installation from packages.debian.org. I download packages for my Ubuntu installation from packages.ubuntu.org, correct? That is, I shouldn't install packages from debian.org, right? Given that Ubuntu is based on debian, I'm not sure how sigificantly the binary (or source) packages differ.

---

### Post by adwait on 2005-06-07
I think (not sure) repositories is a collection of deb files and apt-get automatically checks their dependencies and downloads those which are necesary and installs them as well. So I am not really sure whether you can do this on another pc on a USB stick and then transfer to your pc. You can directly download the files from debian.org and download the listed dependencies as well. The packages downloaded from there, almost always work on Ubuntu barring a few.

---

### Post by pkoufalas on 2005-06-07
Yes, synaptic (GUI) and apt-get resolve dependencies and conflicts in real-time. Bit hard when all you've got is 56k dialup and it wants to download lots of packages to meet dependencies or resolve conflicts.

So I'm left with manually browsing through packages.ubuntu.org, looking for hoary packages of interest and downloading them (away from home) onto usb stick.

In this scenario, I suppose apt-get and synaptic are basically useless to me and I'm stuck with using dpkg?

The other thing is I still don't understand how deb packages differ between ubuntu and debian (ie from debs at packages.ubuntu.org and packages.debian.org respectively). I guess Ubuntu developers are making changes to shared libraries and kernel source? Modified file system organisation? C/C++ complier/linker version control? ...?

I'm trying to keep a neat and clean Ubuntu installation, well it's worth a try anyway!

---

### Post by pkoufalas on 2005-06-08
Someone else asked a similar question:

[http://ubuntuforums.org/showthread.php?t=40381](http://ubuntuforums.org/showthread.php?t=40381)

---

