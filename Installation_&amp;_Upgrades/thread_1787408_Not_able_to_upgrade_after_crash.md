---
title: "Not able to upgrade after crash"
date: 2011-06-21
forum: Installation &amp; Upgrades
---

### Post by fikkaud on 2011-06-21
History: An upgrade went wrong due to lack of space in /boot. So the kernel didn't install.
 
I now have a system that won't run apt-get update or installs due to a mismatch with packages that is not configured with the present kernel.
 
How can i fix this? Aptitude is confused. Should I manually install the kernel that the upgrade attempted? 
 
Any advice is much appreciated.

---

### Post by jerrrys on 2011-06-21
try a 

dpkg --configure -a

you should backup before going further, you could crash

---

