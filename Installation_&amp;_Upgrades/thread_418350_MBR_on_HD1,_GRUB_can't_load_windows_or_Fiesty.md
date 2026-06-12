---
title: "MBR on HD1, GRUB can't load windows or Fiesty"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by Trifid on 2007-04-22
To some everything up, I didn't forward plan building my PC and put my main hdd in SATA3 and my data on SATA1. This means that the MBR is on HD1 and this confuses GRUB and gives error 22: can't find partition. 

I am unsure on how to proceed with this. I have replaced GRUB with the windows boot loader as a temporary solution but I want to have fun with linux which using a live CD can't allow. Has anyone here got any ideas?

Thanks, Trif.

---

### Post by pepsi_max2k on 2007-04-22
Edit /boot/grub/menu.lst in your feisty partition to correct the partition setup. Could be a number of things need changing, but as a guide I had to add the following to get windows to boot when it's on my first sata drive and grub is on my firsd ide drive...

```
title Windows XP
    map (hd0) (hd1)
    map (hd1) (hd0)
    rootnoverify (hd1,0)
    chainloader +1
    makeactive
```

---

