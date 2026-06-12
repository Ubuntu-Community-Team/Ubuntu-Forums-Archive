---
title: "making my old HD my /home HD"
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by zenkoanlife on 2008-12-01
Okay, so upgrade to 8.10 hosed my computer, and after spending a week or two looking for a fix I decided to just reinstall 8.04. Since I was planning on adding another hard drive anyway, I installed fresh ubuntu onto a new drive, and would like to mount my old drive as my /home directory and delete everything that isn't /home from it. So I guess my question is this... Is it as easy as mounting it and deleting all the junk I don't want, then editing /etc/fstab to mount it under /home ?

---

### Post by Pumalite on 2008-12-01
This might help:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by zenkoanlife on 2008-12-02
thanks... that did help. The only thing I had to do was delete files and get my actual home files to the root of the drive.  So instead of /disk/home/username  I just had /disk/username then used the fstab entry from the howto posted above and restart the machine.

---

