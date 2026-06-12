---
title: "boot"
date: 2015-12-18
forum: Installation &amp; Upgrades
---

### Post by guesmi on 2015-12-18
bonjour c'est la premiere fois que j'installe linux 
 je peut pas booter sur windows 7 apres que j'installe ubunto 15.04
au cours de l'installation j'ai fait  deux partitions swap et  / seulement
qui peut m'aider svp

---

### Post by slickymaster on 2015-12-18
Hi guesmi, welcome to the forums

Please take in consideration that this an English spoken forum, so you'll have to write your posts in English unless you are participating in a Loco Forum, where you are permitted to use another language if it is in common use in that Loco Forum and understood by the Loco Forum staff. We have many users from many different countries, and English is the common language of these forums.

Alternatively you can post your issues at [https://forum.ubuntu-fr.org/](https://forum.ubuntu-fr.org/)

---

### Post by guesmi on 2015-12-18
good morning
it is my first time that I install linux
I'cant boot to windows7 after I install ubunto 15,04
during the installation of ubunto I make  just two partitions swap and /
can you help me please

---

### Post by yancek on 2015-12-18
Boot Ubuntu, open a terminal and run this command and watch the output to see if there is any reference to windows:  sudo update-grub
If you don't see any windows output run this command from a terminal and post the output here:  sudo fdisk -l(Lower Case Letter L in the command)

---

### Post by grahammechanical on 2015-12-18
When we install Ubuntu we get these options:

1) Install Ubuntu alongside them [that is other operating systems]
2) Erase disk & install Ubuntu
3) Encrypt the new Ubuntu installation for security
4) Use LVM with the new Ubuntu installation
5) Something else [create, resize partitions yourself or choose multiple partitions for Ubuntu]

Which option did you choose?

Regards.

---

