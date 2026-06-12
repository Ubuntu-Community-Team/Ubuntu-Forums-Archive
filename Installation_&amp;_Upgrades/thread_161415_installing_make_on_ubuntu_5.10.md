---
title: "installing make on ubuntu 5.10"
date: 2006-04-17
forum: Installation &amp; Upgrades
---

### Post by ashimseth on 2006-04-17
hi guys...
i have been tryin to install make on my new ubuntu installation using:
sudo apt-get install make

but this is wat it says:

Reading package lists... Done
Building dependency tree... Done
Package make is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Package make has no installation candidate

i guess make hasnt been installed..

please help

---

### Post by Sef on 2006-04-17
To download, start with this page here:

[http://www.gnu.org/software/make/]("http://www.gnu.org/software/make/")

> Package make is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

The package is either most likely not in the ubuntu repositories or it is a subdirectory in another program.

---

### Post by Sutekh on 2006-04-17
Do you still have your Installation CD?

Use```
sudo apt-cdrom add
sudo apt-get install build-essential
```
to add you cdrom to the repositories and install build-essential, which contains make as well as the gcc/g++ compilers.

---

