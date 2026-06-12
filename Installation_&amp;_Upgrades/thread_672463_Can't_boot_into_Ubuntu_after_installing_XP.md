---
title: "Can't boot into Ubuntu after installing XP"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by Kaphix on 2008-01-19
I did [http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/) and tried replacing the hd0 with everything up to 3, and set sda2 (linux partition) as boot, and set it back to Windows and I can still only boot into windows.

EasyBCD isn't working on Windows. When I did changed my ubuntu partition to have the boot flag, it says "cannot load OS".

[IMG]http://i25.photobucket.com/albums/c69/Kaphix/Screenshot--dev-sda-GParted-1.png[/IMG]

---

### Post by logos34 on 2008-01-19
this is what you want:

> [B]sudo grub

> root (hd0,1) [/B] [--> sda2]
[B]> setup (hd0)
> exit[/B]

EasyBCD requires grub be installed to the bootsector of the linux root partition.  

> [B]sudo grub

> root (hd0,1) [/B]
**> setup (hd0,[B][COLOR="Red"]1[/COLOR]**)
> exit[/B]


---

### Post by erginemr on 2008-01-19
Referring to the same web page, your hard disk where Linux is installed is (hd0) and the corresponding partition (sda2) is (hd0,1). In this respect:
```
sudo grub
 > root (hd0,1)
 > setup (hd0)
 > exit
```

should apply.

---

