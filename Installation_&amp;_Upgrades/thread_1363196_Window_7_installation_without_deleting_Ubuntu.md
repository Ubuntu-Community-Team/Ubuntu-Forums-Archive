---
title: "Window 7 installation without deleting Ubuntu"
date: 2009-12-24
forum: Installation &amp; Upgrades
---

### Post by jsmanian on 2009-12-24
Dear all,

        I have windows XP and ubuntu 9.1 installed in separate partition. Both are working fine. Now I am going to install windows 7 in the XP partition. I am afraid that it will modify grub boot loader and ubuntu cannot load after this. Really I don't know. So Kindly could anybody give me detailed procedure to follow.

---

### Post by Grenage on 2009-12-24
You are quite correct, it will.  Make sure you have a live cd, then take a look [here]("http://ubuntuforums.org/showthread.php?t=1035999").

---

### Post by jsmanian on 2009-12-24
[COLOR=Black]Hi Grenage,

    Thanks for link. I got the same what I tried to find:P. 

Thanks for your help


[/COLOR]

---

### Post by oldfred on 2009-12-24
With Karmic 9.10 you need to know if you have grub legacy 0.97 from an upgrade or grub2 (1.97) from a new install. The instructions for reinstalling grub are different and if you get them mixed up it is real fun trying to straighten it out.

Grub version:

grub-install -v

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by jsmanian on 2009-12-25
Hi Oldfred,

     Thanks for information. It gives clear procedure to do.

---

