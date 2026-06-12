---
title: "Booting with Boot It NG"
date: 2006-09-02
forum: Installation &amp; Upgrades
---

### Post by JWells on 2006-09-02
I use Boot It NG (BING) as my boot manager.  On my hard drive I have two installs of XP and one of Xandros.  When I install Ubuntu, it wipes out BING and installs GRUB.  I can boot fine to all OS's, including Ubuntu, using GRUB.  But when I re-install BING, I can no longer boot to Ubuntu.  BING says its not a bootable item.  With Xandros, it gives you an option to not load its default boot loader, which I don't.  After installing Xandros, BING boots to it without problem.  I like Ubuntu much better, look and feel wise.  How do I install Ubuntu without involving GRUB?  I'm installing Ubuntu from the live CD, which places an "install" icon on the desktop.  I looked closely for an option to not install GRUB, but didn't see one.  BTW, BING is installed in its own primary partition as the first partition on the hard drive.

---

### Post by JWells on 2006-09-03
OK, I half solved my problem.  I downloaded the "alternate" image and imagaged to a CD.  So, now what....how do I avoid installing GRUB?  What do I choose.....OEM install?

---

### Post by cotcot on 2006-09-03
No not OEM.

Choose the first option (install in text mode)
With F6 you can choose between normal or expert. Normal should do.

---

### Post by confused57 on 2006-09-03
You can choose to install grub to the partition that you're installing Ubuntu on using the alternate cd..
You might be able to use the live cd and install grub to the Ubuntu partition, using your current installation:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)
If you can do this you wouldn't need to install with the alternate cd.

---

### Post by JWells on 2006-09-03
Thanks all for your help. Well, I used "text" install, and installed GRUB on the root partition of ubuntu, which works.  I guess ubuntu does't have its own boot sector and needs GRUB to boot.  Now, when I use BING to boot ubuntu, it brings up GRUB, which displays all the OS's in the my system, and I then choose Ubuntu.  Interestingly, when I use BING to boot to Xandros, it boots directly into the OS. Is there anyway to get Ubuntu to boot directly into the OS from BING, without the added step of GRUB?  Not a deal breaker, but would be nice to "cut out the middle man".

---

