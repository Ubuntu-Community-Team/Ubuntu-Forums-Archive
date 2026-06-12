---
title: "Kcontrol, system config problems"
date: 2007-01-30
forum: Installation &amp; Upgrades
---

### Post by freund on 2007-01-30
I recently had a problem with modules (Monitor & Display or Data or Filesystems) not loading in kcontrol or the systemconfig menu.

I looked through the Menu Editor and discovered the command line that ran kcmshell. 

I did a kcmshell --list and the modules where not listed. I looked in the directory /usr/lib/kde3 kcm_displayconfig.* were out of date.

I did a search on google to find the package that it belongs to and discover it was kde-guidance.

I uninstall and then installed and the problem was solved. The modules could be loaded again.
One might have to run sudo apt-get clean all to get rid of old packages first before reinstalling.

al

---

