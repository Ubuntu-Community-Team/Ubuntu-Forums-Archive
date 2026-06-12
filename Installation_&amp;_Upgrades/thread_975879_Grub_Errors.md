---
title: "Grub Errors"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by dermy on 2008-11-08
Hey, I use Vista and I heard you could run Umbuntu from a flash drive. I followed the instructions from Pen Linux drive and I installed 8.10 on a 4GB flash drive. I ran it from the flash drive after and played around with Umbuntu a bit. When I went to boot from my hard drive I started to get GRUB errors.

Can anybody help me get vista back? I'm not ready to take Linux all the way. I still want to play the OS field for a bit and I'm starting to panic

---

### Post by tvtech on 2008-11-08
if you want to get rid of the grub problem your going to have to repair your windows mbr to get rid of the grubs.  your should be able to pop your windows disk and have an option to repair your mbr.

---

### Post by 73ckn797 on 2008-11-08
> **dermy said:**
> Hey, I use Vista and I heard you could run Umbuntu from a flash drive. I followed the instructions from Pen Linux drive and I installed 8.10 on a 4GB flash drive. I ran it from the flash drive after and played around with Umbuntu a bit. When I went to boot from my hard drive I started to get GRUB errors.

Can anybody help me get vista back? I'm not ready to take Linux all the way. I still want to play the OS field for a bit and I'm starting to panic

Boot system with Windows disk and choose recovery. Type "fixmbr" or "fixboot". Exit system and reboot.

---

### Post by caljohnsmith on 2008-11-09
Since you are using Vista, if you have your Vista Install CD, just run:
```
bootrec /fixmbr
```
And if you don't have your Vista Install CD, you can download a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). Let us know how it goes.

---

### Post by dermy on 2008-11-09
Wish I wasn't so eager. 
Ended up doing a complete reinstall of Vista, I was only allowed to do a clean install. Had to reinstall a lot of software and now I'm trying to recover my bookmarks and other settings. 

Thanks for the help anyway. I plan to have another attempt at pen drive Linux or see if I can get an old compy and install on that.

---

