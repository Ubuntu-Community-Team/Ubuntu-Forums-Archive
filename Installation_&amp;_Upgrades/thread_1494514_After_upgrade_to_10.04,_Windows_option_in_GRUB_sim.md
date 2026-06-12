---
title: "After upgrade to 10.04, Windows option in GRUB simply reloads GRUB"
date: 2010-05-27
forum: Installation &amp; Upgrades
---

### Post by conway.federico on 2010-05-27
After I upgraded to lucid, I noticed that my GRUB loader finds my windows partition and lists it correctly (dev/sda1)... however when selected... grub is just reloaded.  Ubuntu boots fine.  Perhaps GRUB got installed inside the windows partition??? I don´t know, I am a linux newbie.  Any ideas?  

Please submit any ideas to me with the command present... otherwise I might not know what you are talking about.  

not sure if its useful but... fdisk -l reads out as follows 

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4ac64ac6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4899    39351186    7  HPFS/NTFS
/dev/sda2            4900        9729    38796975    5  Extended
/dev/sda5            4900        9525    37158313+  83  Linux
/dev/sda6            9526        9729     1638598+  82  Linux swap / Solaris
```

---

### Post by pmlxuser on 2010-05-27
i also faced the same roblem, it got solved by doing the package upgrade.. i think it upgraded grub and then it reconfigured correctly..

>system> Admin> Update manager

update..

---

### Post by conway.federico on 2010-05-27
Thank you for the quick reply.. and I really hoped for a minute that it might be that easy.  But no, I am up to date and I still have my redundant little GRUB loader. Any other ideas?

---

### Post by kansasnoob on 2010-05-27
You are quite likely effected by this:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

I can only be sure if you post the output of The Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

I filed a bug report regarding this:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

So, if that ends up being the problem please add a comment there and select "this bug effects me". I sure wish they'd fix that.

---

### Post by conway.federico on 2010-05-27
> **kansasnoob said:**
> You are quite likely effected by this:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

I can only be sure if you post the output of The Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

I filed a bug report regarding this:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

So, if that ends up being the problem please add a comment there and select "this bug effects me". I sure wish they'd fix that.

Fixed!!! Thank you so much.  I will list my bug report for sure.

---

