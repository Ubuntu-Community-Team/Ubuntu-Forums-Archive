---
title: "remove kernel and gnome"
date: 2005-02-20
forum: Installation &amp; Upgrades
---

### Post by pfefferkeks on 2005-02-20
Hi,

1)
I have installed Ubuntu. Than I have updatet to hoary, now I habe istalld three kernels.
2.6.10-3-386, 2.6.8.1-3-386 and 2.6.8.1-5-386 (ls /lib/modules/), but I only nead 2.6.10-3-386. Now I would remove the other tow kernels but ther isen't any removing bosebilitiy with apt-get. I have looked with dpkg -l *kernel*||/ Name           Version        Beschreibung
+++-==============-==============-============================================
un  kernel-image-2 <keine>        (keine Beschreibung vorhanden)
un  kernel-patch-2 <keine>        (keine Beschreibung vorhanden)
un  kernel-patch-b <keine>        (keine Beschreibung vorhanden)
un  kernel-patch-e <keine>        (keine Beschreibung vorhanden)
ii  linux-kernel-h 2.5.999-test7- Linux Kernel Headers for development
un  linux-kernel-l <keine>        (keine Beschreibung vorhanden)
un  nvidia-kernel  <keine>        (keine Beschreibung vorhanden)
un  nvidia-kernel- <keine>        (keine Beschreibung vorhanden)
un  nvidia-kernel- <keine>        (keine Beschreibung vorhanden)
ii  nvidia-kernel- 1.0.6629+1     NVIDIA binary kernel module common files
un  nvidia-kernel- <keine>        (keine Beschreibung vorhanden)

There isn't any installatiob from any kernel? I dont't understand this i thing I have installed the tree kernels. But dpkg tells me no. ???? 
Can some one help me?

2)
I alway use fluxbox, what are the packets to remove GNOME compleatly?

thangs pfefferjejs

---

### Post by fordp on 2005-02-20
I had three kernels installed. I use a K7 one now. I just removed the old ones from Synaptic and it worked fine editing the Grub configuratin correctly too!

---

### Post by pfefferkeks on 2005-02-20
Hi,

my problem is that I don't find the installed kernels. Only the vmlinuz file and the modules in the /lib/moduls. 
So I can't remove the kernel ;)

thangs for your help pfefferkeks

---

### Post by az on 2005-02-20
The package names are linux-image
as in linux-image-2.6.8.1-3-386

Remove those.

---

### Post by pfefferkeks on 2005-02-20
thats it thangs. ;)

---

