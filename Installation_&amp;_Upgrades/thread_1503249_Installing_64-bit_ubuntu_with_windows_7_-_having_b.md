---
title: "Installing 64-bit ubuntu with windows 7 - having bcd errors"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by bsm1th on 2010-06-06
Like a fool, I deleted the BCD entry for ubuntu before uninstalling. Now I am trying to do a reinstall, but now can do nothing. Can anyone tell me what the name shown on the boot menu for Ubuntu 10.04 for the 64 bit alpha is? I am trying to put the entry back with EasyBCD, but the sum is off by a bit with 'Ubuntu-10.04 64amd', so I am close, but not there. Please help.

Bob <bsm2th@gmail.com>

---

### Post by linuxman94 on 2010-06-06
This a wubi install, correct? You should be able to completely remove the install using Programs in the control panel.

---

### Post by bsm1th on 2010-06-06
In Programs, it shows up as Ubuntu, and the uninstall fails because the script tries to remove the BCD entry as part of the uninstall. That's why I wanted to make an entry with the same name, even if it didn't go anywhere..

Bob <bsm2th@gmail.com>:confused:

---

### Post by drdos2006 on 2010-06-06
I found with a new install that Windows needed to be installed first in its own artition as it takes over control of the HDDs and boot sector. Ubuntu loads over the top of Windows and allows the menu to choose from Ubuntu or Windows. 

regards

---

### Post by Mark Phelps on 2010-06-07
> **bsm1th said:**
> ...I am trying to put the entry back with EasyBCD, 

Then go to the EasyBCD support forum at the NeoSmart Technology forums.  It's their product; they are the ones that know how it works.

---

