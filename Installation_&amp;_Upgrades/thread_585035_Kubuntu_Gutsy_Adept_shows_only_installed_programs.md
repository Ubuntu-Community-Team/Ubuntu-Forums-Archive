---
title: "Kubuntu Gutsy: Adept shows only installed programs"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by mibadt on 2007-10-21
Hi,
I'm on a fresh installed Kubuntu Gutsy 7/1 (386). I've created a new sources.list using source-o-matic and placed it in /etc/apt. Yet, when running Adept :
1. It shows only installed programs. It doesn't show ANY program that is not installed.
2. It won't find and additional package I'm looking (Skype, guarddog, Firefox, KOffice etc.).

Please advise!

Thanks
Michael Badt

---------copy of my sources.list----------
# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) gutsy main restricted
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) gutsy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted

deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) gutsy main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) gutsy-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) gutsy universe multiverse
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe multiverse

deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) gutsy universe multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe multiverse

# Ubuntu backports project
# GPG key: 437D05B5
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse

deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse
----------------------end-------------------------------------

---

### Post by hinge on 2007-10-21
Just to check the stupid littel things....
There is a filter function at the top of adept where you can select what you want to see - among these are installed apps and not installed apps - are any of these checked ??

The sources list does not have anything to do with what you presently have installed....

---

### Post by mibadt on 2007-10-21
Solved the problem, although I don't understand why.
I'm behind a router. Initially (when ADept wasn't functioning), my resolv.conf contained only the router's IP address (I had FULL browsing and email functionality). Adding the DNS of my ISP (to resolv.conf) somehow borough  Adept back to full functionality.

Michael Badt

---

### Post by fabusio on 2007-10-25
wow tx a lot for your suggestion. i was crazy for this problem :)

---

