---
title: "Is Ubuntu leaving synaptic and apt-get ?"
date: 2008-09-18
forum: Installation &amp; Upgrades
---

### Post by TusharG on 2008-09-18
I wrote a new blog on 16th that talks about why I moved to Ubuntu over Fedora. There I received comment that says Ubuntu is moving from apt-get/synaptic to PackageKit that has been developed by Fedora because Ubuntu is not happy with synaptic. Is that true? What is the blocker for Ubuntu in using synaptic/apt-get? 
  My blog is here... [http://tusharg.blogspot.com/](http://tusharg.blogspot.com/)

---

### Post by Partyboi2 on 2008-09-18
From what I have read its not going to replace apt

[https://wiki.ubuntu.com/DesktopTeam/Specs/PackageKit](https://wiki.ubuntu.com/DesktopTeam/Specs/PackageKit)

> PackageKit is a system designed to make installing and updating software on your computer easier. The primary design goal is to unify all the software graphical tools used in different distributions, and use some of the latest technology like PolicyKit to make the process suck less. 

The actual nuts-and-bolts distro tool (yum, apt, conary, etc) is used by PackageKit using compiled and scripted helpers. PackageKit isn't meant to replace these tools, instead providing a common set of abstractions that can be used by standard GUI and text mode package managers. 

PackageKit itself is a system activated daemon called packagekitd. Being system activated means that it's only being run when the user is using a text mode or graphical tool, and quits when it's no longer being used. This means we don't delay the boot sequence or session startup and don't consume memory when not being used.

---

### Post by TusharG on 2008-09-19
It is not going to replace but is ubuntu gonna get one more(?) package manager ?

---

### Post by Partyboi2 on 2008-09-19
Packagekit is already in the ubuntu repo's for hardy and intrepid, its not installed by default, but whether this changes down the track I am unsure.
So in short there is another package manager available.

---

