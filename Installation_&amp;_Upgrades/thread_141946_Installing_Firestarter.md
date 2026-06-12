---
title: "Installing Firestarter"
date: 2006-03-09
forum: Installation &amp; Upgrades
---

### Post by cantrj on 2006-03-09
Community

I am trying to install firestarter onto my BB 5.10 distro but am having no luck. I apparently have this application (version 1.0.7) on my Linux Magazine DVD but can not for the life of me find it. The install directions that are provided with the 1.0.3 tarball did not provide me with any success. Lastly I tryed from the sudo apt-get install firestarter command but recived the following error.

cantrj@FPD014147:~/Desktop$ sudo apt-get install firestarter
Password:
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package firestarter
cantrj@FPD014147:~/Desktop$
  
I am not sure which of theys three install sources I sould proceed with and were to go from there...Please help.

---

### Post by heimo on 2006-03-09
Try:
```
sudo apt-get update
sudo apt-get install firestarter

```

---

