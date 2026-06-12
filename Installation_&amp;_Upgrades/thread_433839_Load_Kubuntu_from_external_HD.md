---
title: "Load Kubuntu from external HD"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by ThaDoctor99 on 2007-05-05
Hi


I would like to know there is any guys in here who have successfully loaded kubuntu or ubuntu from within vista.
This is really bugging me.


Greetings from Denmark

---

### Post by ThaDoctor99 on 2007-05-05
of course from the external harddisk and preferably at boot, I wouldn't like to need to install a partition with grub or something similiar that is the last case scenario

PS: I am not fooling around with my own computer.

---

### Post by bulldog on 2007-05-05
Hmmm,not sure what you mean.
You want ubuntu on a external hdd and vista on the internal hdd?
You want to be able to boot them both?

If this is what you want,I have a question.
Is this computer able to boot from an USB device? can you select such a thing at boot  time?

---

### Post by ThaDoctor99 on 2007-05-05
The computer can't really find the external, does this mean that I have to install the grub variation ?

---

### Post by bulldog on 2007-05-05
If you can't boot from an USB device you can install GRUB but it won't do any good.

The problem is,your USB device is only recognized when there's an OS loaded,otherwise your external disk is unknown.
So at boot time,with or without GRUB,your disk is non existing.

When you have an option at boot time or in the BIOS,to boot from an USB device,things are different.
Then you can just install GRUB and Ubuntu on the external hdd and choose at boot time to boot the internal [windows] or the external [GRUB --> ubuntu] hdd.

---

### Post by ThaDoctor99 on 2007-05-14
in theory this could be done by clabbing the hd inside the as an internal hd ?
then all of these things would not be as bad.

---

### Post by bulldog on 2007-05-14
If you build the hdd inside the computer,you can use it as a second hdd,if this is what you mean.
Than you can use it for ubuntu for sure.

---

