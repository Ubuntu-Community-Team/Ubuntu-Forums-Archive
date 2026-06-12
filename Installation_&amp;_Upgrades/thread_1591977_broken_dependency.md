---
title: "broken dependency"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by Matthes on 2010-10-10
Hello. I have a broken dependency. The package is libsdl-image-1.2-dev. When I try to fix it via synaptic, it says E: libsdl-image1.2-dev: cannot remove `/.'  What can I do? Please help me. :)

---

### Post by dino99 on 2010-10-10
two ways:

- synaptic: remove/purge every related packages then reinstall them

- nautilus "search" about this package and delete it

but check that the sources are correctly set and that some ppa (if any) dont conflict (mostly oldish): synaptic repo tab

---

### Post by Matthes on 2010-10-10
When 'completely remove' it I get the same error. There aren't any other change suggested when I mark it for removal. 
 How can I search/remove the package via nautilus? 
 I think that my sources are okay. :)

---

### Post by Matthes on 2010-10-10
dpkg-reconfigure lbsdl-image1.2-dev && sudo apt-get remove --purge libsdl-image1.2-dev
output:
Package `lbsdl-image1.2-dev' is not installed and no info is available. 
Use dpkg --info (= dpkg-deb --info) to examine archive files, 
and dpkg --contents (= dpkg-deb --contents) to list their contents. 
/usr/sbin/dpkg-reconfigure: lbsdl-image1.2-dev is not installed

---

