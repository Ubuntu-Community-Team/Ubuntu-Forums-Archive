---
title: "Full-encrypted dualboot system"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by Phantom784 on 2008-05-01
I'm getting a laptop soon.  It will come pre-installed with Vista Home Premium, and I want to keep that in addition to installing Hardy Heron.  I want the Ubuntu install to be fully encrypted, with seperate / and /home partitions.  Also, I want to be able to access my /home partition on the Vista install.  Does anyone have advise on the best way to do this?

(I'm not currently planning on encrypting the Vista partition)

---

### Post by twright on 2008-05-01
if you want to be able to access /home from windows then you might have trouble encrypting it

you should use the liveCD and gparted to resize windows then use the alternative cd to create 2 partition (all logical), 1 about 100 meg and ext3 for /boot and one physical volume for encrypted lvm create 3 lv's in that, one for / one for /home and one for swap (if you want to hibernate) 

see this guide:
[http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html](http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html)

---

