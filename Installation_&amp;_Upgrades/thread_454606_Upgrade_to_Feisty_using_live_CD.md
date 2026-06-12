---
title: "Upgrade to Feisty using live CD"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by Striatum on 2007-05-25
Hi!

I have a PC here with ISDN connection running 6.10 and a live CD with 7.04. Is there a way to upgrade using that live CD - there can't be that many differences between the packages on live and alternate CD? Or do I have to get alternate CD from somewhere (which could be difficult for me at the moment) ?.

Thanks a lot!
Striatum

---

### Post by BobbyBionic on 2007-05-25
Hi

It's possible to upgrade with live cd (or alternate, same packages), put it on your drive and add the cdrom as a repository.

Nevertheless, it's possible (quite sure) that you will have some problems of dependencies, so I suggest you to change repositories to feisty and to be connected on the internet at the same time.

---

### Post by Striatum on 2007-05-26
How do I change the repositories to Feisty?

---

### Post by BobbyBionic on 2007-05-26
If you are using Ubuntu 6.10 (Edgy Eft), edit your /etc/apt/sources.list and replace edgy by feisty (you must use sudo/gksudo to edit it).

---

