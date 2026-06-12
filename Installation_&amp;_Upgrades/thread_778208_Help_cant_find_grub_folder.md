---
title: "Help cant find grub folder"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by Venom_Man on 2008-05-01
help, i just installed hardy and i need to change the grub to disable my splash screen and i cant find my gub folder. it is not any of my hda partitions in the boot folder where it should be. any idea what is going on?

---

### Post by Patb on 2008-05-02
VenomMan, try 
```
sudo updatedb
```then
```
locate menu.lst
```
If that doesn't help, please post the output of the last command, and the output of:
```
sudo fdisk -l
```  

Cheers, Pat.

---

