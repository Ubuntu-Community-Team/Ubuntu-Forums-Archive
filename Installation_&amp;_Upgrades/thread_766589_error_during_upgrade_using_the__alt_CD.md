---
title: "error during upgrade using the  alt CD"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by aum11 on 2008-04-25
Have had the same problem on 2 computers using 2 copies of the 8.04 alt CD.

Am successfully updating using the CD until the following message appears:

E: /media/Ubuntu 8.04 i386//pool/main/h/human-theme/human-theme_0.18_all.deb: trying to overwrite `/usr/share/applications/screensavers/ubuntu_theme.desktop', which is also in package gnome-screensaver

Anybody know what is going on?

Thanks.

---

### Post by Pumalite on 2008-04-25
You have mixed dependencies and the installer is warning you that it cannot proceed because of them.

---

### Post by aum11 on 2008-04-25
Thanks, and how to fix it please?

This is just an upgrade of a standard install...on 2 separate machines.  I see someone else has the same problem...suspiciously like a bug.  Happy to discover if it is not so.

---

### Post by Pumalite on 2008-04-25
No assurances, but we can try. Run:
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade

---

### Post by aum11 on 2008-04-25
Thanks Pumalite,

I just responded to You under another thread, so maybe it is best ti deal with my problem under this thread.

Results of step 1:

~$ sudo dpkg --configure -a
[sudo] password for ari:
dpkg: dependency problems prevent configuration of ubuntu-artwork:
 ubuntu-artwork depends on human-theme (>= 0.10); however:
  Version of human-theme on system is 0.9.
 ubuntu-artwork depends on ubuntu-gdm-themes; however:
  Package ubuntu-gdm-themes is not installed.
 ubuntu-artwork depends on ubuntu-wallpapers; however:
  Package ubuntu-wallpapers is not installed.
dpkg: error processing ubuntu-artwork (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ubuntu-artwork

---

