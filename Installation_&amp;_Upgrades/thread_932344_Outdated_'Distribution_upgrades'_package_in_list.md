---
title: "Outdated 'Distribution upgrades' package in list"
date: 2008-09-28
forum: Installation &amp; Upgrades
---

### Post by linuxNewb on 2008-09-28
I was on Ubuntu 7.10 (gutsy), but was unable to upgrade using the Update Manager, because for some reason the 'New Distribution release is available' message along with the 'upgrade' button would not appear.

So I upgraded by manually changing the word 'gutsy' to the word 'hardy' in my sources.list file, then simply updated all my packages. It worked great, and I am now running Ubuntu 8.04 (hardy) with no problems. I just have one minor annoyance...

In my Update Manager, in the actual list of packages, it keeps displaying an outdated GIMP update under a section-title called 'Distribution updates'. It is grayed out, and I'm unable to do anything with it (like remove it). It must have been released between the last time I updated 7.10, and the time I 'updated' to hardy after changing my sources.list file.

How can I remove this outdated package from my list in the Update Manager?

---

### Post by WWSmith36 on 2008-09-28
To fully check and upgrade your system using terminal using command line, open a Terminal from the menu Applications->Accessories->Terminal and type:

```
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install
sudo apt-get clean all
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get clean all
sudo apt-get autoremove
```

then please reboot your system

hope this help

---

