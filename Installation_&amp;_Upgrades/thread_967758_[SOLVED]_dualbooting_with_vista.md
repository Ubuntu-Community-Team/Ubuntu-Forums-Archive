---
title: "[SOLVED] dualbooting with vista"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by laney_1 on 2008-11-02
i am hoping to dual boot ubuntu 8.04 "hardy" with windows vista home premium.

i have a 160gb hard drive (internal) and a external 160gb hard drive which i am going to format fat32.

i was wondering how much space i should use for ubuntu i plan to use apps like wine and openoffice. all my games for wine i am going to put on the external hard drive.:)

laney_1

---

### Post by Pumalite on 2008-11-02
First; you have to allocate space for Ubuntu with the Vista partitioner.
Then get Gparted Live CD:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it.
In the 'free space' make 3 'New' partitions:
20 GB for '/'
The rest minus your RAM for /home
Your RAM for /swap
I'd give 30 to 50 GB to Ubuntu.

---

### Post by laney_1 on 2008-11-02
thanks that helps a lot:D

laney_1

---

