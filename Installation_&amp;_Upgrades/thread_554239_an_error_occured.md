---
title: "an error occured"
date: 2007-09-18
forum: Installation &amp; Upgrades
---

### Post by shorty28898 on 2007-09-18
up where the date is (uper right) where all the icons are, theres the update icon.  when i hover it is says this. (by the way i was trying to install vdrift):

a error occured, please run package manager from the right-click menu or apt-get on a terminal to see what is wrong.  the error message was: 
unknown error:' <type'exceptions.systemError'> (E: The package vdrift-full needs to be reinstall, but i cant find an archive for it.)'



help?

---

### Post by Pumalite on 2007-09-18
Run in Terminal:
sudo dpkg --configure -a
If not, then:
sudo apt-get remove --purge vdrift-full
If not, then:
sudo dpkg --remove --force-remove-reinstreq vdrift-full

Then re-install.

---

