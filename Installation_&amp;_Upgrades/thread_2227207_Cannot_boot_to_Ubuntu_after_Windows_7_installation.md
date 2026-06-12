---
title: "Cannot boot to Ubuntu after Windows 7 installation and “boot-repair” does not work"
date: 2014-05-31
forum: Installation &amp; Upgrades
---

### Post by mercury1981 on 2014-05-31
I hope someone here can help me:
I re-installed my Windows 7 partition and now I cannot boot to Ubuntu  14.04 any more - no grub boot-menu is display instead directly the  "Loading windows" screen is shown

 If I go to the boot menu in BIOS I can select my Ubuntu - drive and boot from it (which is quite cumbersome).


  So I tried to use "boot-repair" as described at at the help pages but the program exits with an error.


  This is the link I get from "boot-repair": [http://paste.ubuntu.com/7558812/](http://paste.ubuntu.com/7558812/)

---

### Post by mercury1981 on 2014-05-31
Fix for the problem:

1. Start via Live-CD
2. mount Linux partition
3. "ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/ubuntu/e2eec732-eb12-47e4-8c4d-5f50d4ad5986/ /dev/sdb"
4. restart
5. in BIOS change boot priority of devices - prio 1 is Linux
6. fixed - grub is loaded first and the Windows can be selected

---

