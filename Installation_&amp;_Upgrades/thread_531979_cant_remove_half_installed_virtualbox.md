---
title: "cant remove half installed virtualbox"
date: 2007-08-22
forum: Installation &amp; Upgrades
---

### Post by pdc124 on 2007-08-22
SOLVED

tried installing virtualbox and it failed.
now I cant remove it 
 

aptitude tells me its half installed 

msc@goldthorpe:~$ sudo dpkg -i  virtualbox
dpkg: error processing virtualbox (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 virtualbox
msc@goldthorpe:~$
msc@goldthorpe:~$ sudo apt-get remove --purge virtualbox
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
msc@goldthorpe:~$     

PS im new to this - just spent a few years playing around with gentoo .



??

---

### Post by forestpixie on 2007-08-22
sudo dpkg --remove --force-remove-reinstreq virtualbox

worked for me :)

---

