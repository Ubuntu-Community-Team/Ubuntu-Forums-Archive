---
title: "Problem with alternate CD partitioner"
date: 2008-08-21
forum: Installation &amp; Upgrades
---

### Post by Brownedwg89 on 2008-08-21
I am trying to install ubuntu on my aunt's fairly old gateway pc.
The live cd will not run on it, so I an installing with the alternate cd. The install proceeds normally until the partitioning step. It then shows:
> [!!] Partition disks
??? ???
<Go Back> <Continue>

Choosing either option sends me to a blank (empty blue) screen and nothing happens.

Could anybody help with this? Thanks :)

---

### Post by Pumalite on 2008-08-21
Try editing your boot line and adding all_generic_ide at the end of the line.
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by Brownedwg89 on 2008-08-22
> **Pumalite said:**
> Try editing your boot line and adding all_generic_ide at the end of the line.
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

i tried that and it didn't work

---

### Post by sandysandy on 2008-08-22
what r the computer specs - RAM , speed etc

---

### Post by DavidTangye on 2008-08-22
> **Brownedwg89 said:**
> i tried that and it didn't work
How much RAM does it have? If 256mB you are best using xubuntu and you need to install no gui first, ie command line only, and using the 'lowmem' option. After installing and rebooting, log in and run ```
sudo apt-get install xubuntu-desktop
```I have standard xubuntu running nicely on someone's old 256mB RAM PC.

---

### Post by Pumalite on 2008-08-22
256 MB of RAM or less>Xubuntu Alternate CD.
[http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/](http://cdimage.ubuntu.com/xubuntu/releases/8.04.1/release/)

---

