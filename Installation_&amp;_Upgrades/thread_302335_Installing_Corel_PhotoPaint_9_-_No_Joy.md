---
title: "Installing Corel PhotoPaint 9 - No Joy"
date: 2006-11-18
forum: Installation &amp; Upgrades
---

### Post by Kerry Lange on 2006-11-18
Hi there:

I'm trying to install Corel PhotoPaint 9 but without success so far.  I'm a Linux / Ubuntu newbie, which makes it worse.

Anyway, I've got the files burnt to a CD and am trying to install from there.  Supposedly, one way to install is to simply double-click on the "install" file on the CD.  Doing so brings up a window where I'm asked to type in my password.  I type in my password, the window disappears and nothing happens.

An alternate method tells me to do the following:

1. Log in as root, and make sure that the CD-ROM is a source in your "/etc/apt/sources.list" file.
2. Type the following commands at a shell prompt:
apt-get clean
apt-get update
apt-get install <package name>, where <package name> is graphics9-paint for Corel PHOTO-PAINT 9 for LINUX installation

When I do all the above and installing, I get the following error message:

E: Couldn't find package

Which isn't very helpful.

I've also tried opening the deb file with the package installer but am told "Error:  Dependency is not satisfiable: libaps."

Any suggestions?

---

### Post by 9000 on 2008-05-09
Did you ever resolve this? I'm trying in Hardy (just for kicks, I doubt I'll actually use it) with the same results.

---

