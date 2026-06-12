---
title: "triple boot"
date: 2011-07-02
forum: Installation &amp; Upgrades
---

### Post by malakar.subhendu on 2011-07-02
Is it safe to use 3 O/S on a machine.
I want to use ubuntu 10.10, fedora 13 and windows7.
I have windows 7 and fedora 13 installed already, now i want to install ubuntu. i have unpartitioned space already in the system. 
thanks.

---

### Post by dino99 on 2011-07-02
some of us have much more :) :)

---

### Post by Rubi1200 on 2011-07-02
Sounds okay to me. If you install Ubuntu last it will put GRUB in the MBR and you can control booting from there (it should pick up and recognize your other installs and add them to the menu).

Good luck!

---

### Post by YesWeCan on 2011-07-02
I'd suggest you use one primary partition and convert it to "extended" (if there isn't already one) and then put all your new OS partitions inside it. This way you are not limited to just 4 partitions. Windows OS's have to be in a primary partition, tho.

---

### Post by shrakmoose on 2011-07-03
Will windows still work if the partition isn't first?

---

