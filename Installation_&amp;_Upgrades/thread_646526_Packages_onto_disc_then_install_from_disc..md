---
title: "Packages onto disc then install from disc."
date: 2007-12-21
forum: Installation &amp; Upgrades
---

### Post by m_pachol on 2007-12-21
Haven't seen a topic like this yet, if there is one sorry.  

At work I cannot use my network bandwidth to install packages I want.  I want xubunt-desktop or ubuntu-desktop for Ubuntu 7.10 server 64bit.  

I can't take the system home with me either, so I was wondering if there is a way to download the packages onto a disc and then install them from there?

I am fimiliar with adding cdrom's to the sources.list file.  But where do I get the packages from?

Thanks

Mike :confused:

---

### Post by DrMega on 2007-12-21
I think you can download the .deb packages without installing them, and then install them later using dpkg.

Have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=103462]("http://ubuntuforums.org/showthread.php?t=103462")

---

### Post by ajgreeny on 2007-12-21
Get **aptoncd** ```
sudo apt-get install aptoncd
``` and you can sort out all this easily.  It lets you burn a CD with all the packages on and then use that on another machine as the source of packages.  If you can install **aptoncd** at work (it is only a small install) you can then use the archive on the CD of downloaded packages.  You can use synaptic to download but not install, or you can simply see what is already in your **/var/cache/apt/archives** folder and use what you already have there; if you've already installed those packages at home they should be in the archive still.

---

