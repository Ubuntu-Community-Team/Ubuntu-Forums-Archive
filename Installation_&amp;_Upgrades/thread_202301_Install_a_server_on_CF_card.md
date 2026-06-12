---
title: "Install a server on CF card"
date: 2006-06-23
forum: Installation &amp; Upgrades
---

### Post by rklauco on 2006-06-23
I am using CF to IDE adaptor for 2.5" HDD (PC Engines CFDISK.2G).
I installed the 6.06 on a 1GB CF card.
The installation claimed about nonexisting swap, but worked OK.
I replaced the 1GB card with 2GB and tried the sasme installation.
During the installation process I found that it is working very slow and on the fourth screen I can see the error message ```
hda: lost interrupt
```
The card works fine in USB reader and I can see no reason why it should not to work in the adaptor.
The only difference I can see is the installation process - on the !gb card the ```
hdparm /dev/hda
``` states about not using DMA, on the 2GB it is using the DMA mode.
I switched it of during the first stages (where the system asks about language etc), but it didn't helped...
Any ideas what am I doing wrong?
Thanks in advance.

---

### Post by txmail on 2006-06-23
I dont have a reply for you; but have always wanted to do something like this. The only thing that I worry about is the limited writes to the disk. Have you tried a microdrive?

---

### Post by rklauco on 2006-06-23
[QUOTE=txmail]I dont have a reply for you; but have always wanted to do something like this. The only thing that I worry about is the limited writes to the disk. Have you tried a microdrive?[/QUOTE]
Well, the limited number of writes is not a problem for me.
The tmp and var folder will be mounted from ramdisk and the rest of the system does not require some intensive writing.
And, the low power and quiet system is a big advantage for me.

---

### Post by rklauco on 2006-06-26
No hints, really?

---

