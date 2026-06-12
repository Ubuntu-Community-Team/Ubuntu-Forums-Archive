---
title: "Ubuntu is DUMB  error loop ! help !!!"
date: 2007-09-18
forum: Installation &amp; Upgrades
---

### Post by syborfical on 2007-09-18
i tried to install vitrual box but it just sat there so i closed the installer.
then when i tried to reinstlal it just comes up with is msg 

 “E: The package virtualbox needs to be reinstalled, but I can't find an archive for it”
it wont let me run synaptic.

how do i fix this? 
i have tired dpkg --configure -a donst do a thing.
can i fix this with out formating?

ive also tried to use apt-get remove and pointed it to the package it still comes up with the same error :S ...

---

### Post by Pumalite on 2007-09-18
Try this:

sudo apt-get remove --purge virtualbox

---

### Post by syborfical on 2007-09-18
tried that still comes up with the same error msg

---

### Post by Pumalite on 2007-09-18
Try this:

sudo dpkg --remove --force-remove-virtualbox

---

### Post by syborfical on 2007-09-18
fixed it 
 dpkg --install then pointed it to the virtualbox.deb

---

### Post by Pumalite on 2007-09-18
No problema.

---

