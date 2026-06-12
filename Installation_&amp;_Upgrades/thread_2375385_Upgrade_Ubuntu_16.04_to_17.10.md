---
title: "Upgrade Ubuntu 16.04 to 17.10"
date: 2017-10-24
forum: Installation &amp; Upgrades
---

### Post by PedroPV on 2017-10-24
How can I upgrade Ubuntu 16.04 to 17.10 without loosing data?

---

### Post by dino99 on 2017-10-24
usually, dist-upgrade is available with:
- LTS -> LTS
- n-1 -> n

if you are aventurous, and experienced enough to deal with possible transitional conflicts/problems, then you can:
- disable external third sources via synaptic
- edit /etc/apt/sources.list and change the desired release name
- then run synaptic, update, and install first: tools (apt, dpkg'...) then language (cpp, python, perl, ...) then the metapackages (ubuntu-desktop, ubuntu-minimal/standard) then apps (evolution, libreoffice, ...) and finaly the DE (gnome-shell, ...)
- and run gtkorphan & bleachbit (as root) to get a cleaned installation.

or better, start installing a fresh mini.iso (netboot install) on a usb key for example if the net link is good enough; this takes mainly the same time  and you get a clean install, then you have some more manual apps to install (dkms, tweaks, localepurge, gtkorphan, bleachbit, ...)

---

### Post by ajgreeny on 2017-10-24
My main question would be, do you really want to move from an LTS version to a short term, intermediate version from which you will have to further update in eight or nine months time to 18.04; why not wait until April 2018 when in theory at least, you can move straight to 18.04.

I am totally unaware of how well the move from unity to the new gnome version is managed in an update from 16.04 to the new gnome DE, and personally I have always clean installed for a new start; I have a separate /home partition so apart from normal backups I do not have to do anything extra when moving my OS version by clean installation.

BY all means try what dino99 suggests but do make sure you have backups of everything important to you before engaging in this operation.

---

