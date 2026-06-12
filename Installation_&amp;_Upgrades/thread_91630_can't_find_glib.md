---
title: "can't find glib"
date: 2005-11-17
forum: Installation &amp; Upgrades
---

### Post by ralph4100 on 2005-11-17
Every time I try to install something, the configure file can't find glib. First I installed the latest glib (2.8.0) and still it could not find it. Then, upon finding some info on a similar problem, I installed a previous version (1.4?) and the error message changed slightly:

```
checking for glib-config... /usr/local/bin/glib-config
checking for GLIB - version >= 1.2.0... no
*** Could not run GLIB test program, checking why...
*** The test program compiled, but did not run. This usually means
*** that the run-time linker is not finding GLIB or finding the wrong
*** version of GLIB. If it is not finding GLIB, you'll need to set your
*** LD_LIBRARY_PATH environment variable, or edit /etc/ld.so.conf to point
*** to the installed location  Also, make sure you have run ldconfig if that
*** is required on your system
***
*** If you have an old version installed, it is best to remove it, although
*** you may also be able to get things to work by modifying LD_LIBRARY_PATH
***
*** If you have a RedHat 5.0 system, you should remove the GTK package that
*** came with the system with the command
***
***    rpm --erase --nodeps gtk gtk-devel
configure: error: glib >= 1.2.0 not found

```

I am trying to install dpsftp, but the problem has been the same for cftp and gftp. 

thx

---

### Post by ralph4100 on 2005-11-17
I think I may have made some progress--I enabled apt-get to download files...

But when I try to update, I get this message:

```
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

```

What does it mean?

---

### Post by ralph4100 on 2005-11-17
btw gftp is working now...

---

### Post by dcstar on 2005-11-17
[QUOTE=ralph4100]I think I may have made some progress--I enabled apt-get to download files...

But when I try to update, I get this message:

```
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

```

What does it mean?[/QUOTE]
Bad repository, try:

[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main universe multiverse restricted

---

### Post by ralph4100 on 2005-11-17
that one didn't work either...

---

### Post by ralph4100 on 2005-11-17
does someone just have a sources.list file I could use?

---

### Post by timfrost on 2005-11-17
Ralph,

The glib library is a standard part of the distribution.  In fact, my breezy system has libglib1.2 and libglib2.0-0.

However, you will also need to install the development package before you can compile any program that needs it.  That package is libglib2.0-dev.

If you are compiling programs, you will need to install the development versions of all libraries that the application uses, so that the compiler can get the symbol lists and other information.

I suspect that your error with the repository may be that there isn't (yet) a breezy-backports section in the repository.

---

