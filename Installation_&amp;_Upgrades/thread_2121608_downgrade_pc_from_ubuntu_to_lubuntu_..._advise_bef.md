---
title: "downgrade pc from ubuntu to lubuntu ... advise before i proceed"
date: 2013-03-02
forum: Installation &amp; Upgrades
---

### Post by Dodeca on 2013-03-02
Hello all

I have an old laptop pc with winXP and ubuntu 12.04 LTS ... lt's a dual boot.

I need to remove ubuntu and install LUBUNTU.

My plan is to use a gparted live cd and just delete ubuntu and then just stick in lubuntu cd and reboot and install.

Is this a good idea?

Thanks !

---

### Post by sudodus on 2013-03-02
You need not wipe Ubuntu. Just re-use its partition, when you install Lubuntu. At the partitioning page of the installer, select '***Something else***', and select the former Ubuntu partition as your root partition /, and set it to be (re)formatted to ext4.

*Edit*: by the way, you will be **up**grading the performance ;-)

---

### Post by QIII on 2013-03-02
Hello!

You realy needn't reinstall at all.

You can just install the Lubuntu desktop and select it at login.  

That's what I would do.

(+1 to performance... and it's not a downgrade at all anyway.)

---

### Post by mörgæs on 2013-03-02
The command for QIII's idea is

```
sudo apt-get install lubuntu-desktop
```

---

### Post by Dodeca on 2013-03-02
That was quick and easy ....

Thanks ...


Now ... how to "mark solved" ... seems to have changed ... will check back later !

---

