---
title: "how to downgrade evolution ? 2.30 to any older and stable version"
date: 2010-05-27
forum: Installation &amp; Upgrades
---

### Post by gabak on 2010-05-27
evolution crash or shuts down by itself 
version 2.28 and 2.30 has the same problem.

[http://ubuntuforums.org/showthread.php?t=1473440&page=4](http://ubuntuforums.org/showthread.php?t=1473440&page=4)

i was thinking maybe and older version will be better.

thxs in advance

---

### Post by dino99 on 2010-05-27
try to repair: 
sudo apt-get install -f
sudo dpkg --configure -a
sudo dpkg-reconfigure evolution

if repairing dont work, into /home, unhide with menu the files, you will find a folder .evolution: save your data (mails, passwords) then delete this folder.

then goto synaptic and remove/purge (right click) then reinstall evolution

---

### Post by gabak on 2010-05-27
thxs pal
but i tried everything you told me and it still crash !!
i want to try with an older version and see what happen.
do u know where can i get older versions?

cuz newer is nt always better

---

