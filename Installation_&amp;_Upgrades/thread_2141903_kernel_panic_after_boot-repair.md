---
title: "kernel panic after boot-repair"
date: 2013-05-04
forum: Installation &amp; Upgrades
---

### Post by oduhart on 2013-05-04
Hello,

I tried a boot-repair after losed my MBR (my entire fault...) 
But when booting in recovery mode I get a kernel panic :

```
VFS : cannot open root device "sda7" or unknown-block(0,0) : error-6
```

my boot-repair log : [http://paste2.org/cxUe84Dv]("http://paste2.org/cxUe84Dv")  

I loked at this log and I think the erro is in the linux section (both normal and recovery) where it says

```
	set root='hd0,msdos2'
```

I guess that it should not be hd0,msdos2 but something like hd0,7 hd0,6 or hd0,8 : I dont exactly now how to translate /dev/sda7 into grub partiytion names

can you help me, please ?

-- edit --

I forgot to say that vista boot correctly ... 
and I looked cautioulisly to the bootrepair log ans saw that I have a remaining burg.cfg  (that how I ****** my MBR :( ). It worked but in fact I dislike it...
at least i know now that the good hd name is hd0,5 :)

I leave the thread opened just in case I am wrong and to know what may be the cause of  this boot-repair error creating grub.cfg

---

### Post by dino99 on 2013-05-04
sudo grub-install /dev/sda
sudo update-grub

---

### Post by oduhart on 2013-05-04
> **dino99 said:**
> sudo grub-install /dev/sda
sudo update-grub

Can you elaborate a bit more, please ?

where and when do I need to enter this commands ? I can only boot using a live usb key, is this possible to use my grub.cfg configuration file (in /dev/sda5 partition) to install / update my MBR ?

I just don't know  all the tricks with grub2 :(

anyway thanksfor your quick help

---

