---
title: "symbol not found grub_os_area_addr"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by Dabaizki on 2011-05-01
My ubuntu 10.10 cannot boot from disk .
only can boot from >grub rescue
and I type these
>grub set root=(hd0,1)
>grub set prefix=(hd0,1)/boot/rub
>grub  insmod normal
>grub normal
enter
 
Boot menu is back,but it dosnot work.
So i press C to command line 
and type these
>grub root (hd0,1)
>grub linux (hdo,1)/boot/vmlinuz-2.***
&#12304;Symbol not found: 'grub_OS_area_addr'&#12305; 
>grub initrd (hd0,1)/boot/initrd-2.*** 
&#12304;Symbol not found: 'grub_OS_area_addr'&#12305; 
>boot
 
It dosnot work at all.
how to solve it?
 
Thanks.

---

### Post by Quackers on 2011-05-01
Welcome to UF.
It may be beneficial to purge and re-install grub to your system. Full details are given in the guide below.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by Dabaizki on 2011-05-01
> **Quackers said:**
> Welcome to UF.
It may be beneficial to purge and re-install grub to your system. Full details are given in the guide below.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Thank you , for that quick reply. It‘s useful for me.

and I just make a USB Ubuntu livecd to reinstall ubuntu to my backup partition sda4.

when it restart , "Ubuntu 10.10 on sda1 "is aviable on boot menu.

thanks.

But i still confused by the grub  location.sda? sda1?

---

### Post by Dabaizki on 2011-05-02
> **dabaizki said:**
> thank you , for that quick reply. It‘s useful for me.

And i just make a usb ubuntu livecd to reinstall ubuntu to my backup partition sda4.

When it restart , "ubuntu 10.10 on sda1 "is aviable on boot menu.

Thanks.

But i still confused by the grub  location.sda? Sda1?

got it~ :d

---

