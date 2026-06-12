---
title: "Grub"
date: 2005-03-12
forum: Installation &amp; Upgrades
---

### Post by eraos on 2005-03-12
I have XP installed on hda,0.  I have a second hard drive I'm using to store games.  Then on my third drive, I have FC3 on (hdd, 0), and Ubuntu on (hdd, 1)

I installed XP first, FC3 second and Ubuntu third.  I only installed grub during the Ubuntu installation hoping that it would automatically detect all three OSes.  But it's only detected Ubuntu and XP.

How can I fix this?  

I tried installing the GAG boot manager, but, though it could detect the linux partitions, it would not load up either linux system.  

Thanks

---

### Post by nemin on 2005-03-13
[QUOTE=eraos]I have XP installed on hda,0.  I have a second hard drive I'm using to store games.  Then on my third drive, I have FC3 on (hdd, 0), and Ubuntu on (hdd, 1)

I installed XP first, FC3 second and Ubuntu third.  I only installed grub during the Ubuntu installation hoping that it would automatically detect all three OSes.  But it's only detected Ubuntu and XP.

How can I fix this?  
[/QUOTE]
So you only lack FC3? You have to add the boot info for FC3 to the /boot/grub/menu.lst file.
Example:
```
title FC3[INDENT]root (hdd,0)
kernel /boot/vmlinuz-2.6.9-1.667 root=/dev/hdd0 LABEL=/ ro rhgb quiet
initrd /boot/initrd-2.6.9-1.667.img[/INDENT] 

``` 
You might have to change these filename, you can mount the FC3 partition and have a look at the /boot dir to see the correct ones.

---

