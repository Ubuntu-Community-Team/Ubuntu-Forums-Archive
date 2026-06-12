---
title: "Letting Vista Take Charge"
date: 2010-04-28
forum: Installation &amp; Upgrades
---

### Post by KarmaAmputee on 2010-04-28
G'day All,

For a while now, I have multibooted my Vista installation with Ubuntu.
However, up until now I have been happy with Ubuntu being in charge of my boot options.
I am wanting to change my bootloader so that when my machine boots, and no choices are made at the boot menu, Vista automatically starts after a set amount of time instead of Ubuntu. 

I know the boys over at APC have a guide on how to do this, but it involves copying information from the menu.lst file and using EasyBCD - I was wondering if these steps will still work now that I am running Karmic Koala, which I understand uses a different method of changing GRUB entries (manipulating the menu.lst file is no longer part of this process and is no longer recommended)

If someone could tell me how to put Vista in charge of my boot options so that it will boot automatically instead of Linux, that would be greatness.

Cheers guys :)

---

### Post by ubunterooster on 2010-04-28
Use lilo, not grub :D
[http://en.wikipedia.org/wiki/LILO_%28boot_loader%29](http://en.wikipedia.org/wiki/LILO_%28boot_loader%29)

---

### Post by Doug11 on 2010-04-28
> **KarmaAmputee said:**
> G'day All,

For a while now, I have multibooted my Vista installation with Ubuntu.
However, up until now I have been happy with Ubuntu being in charge of my boot options.
I am wanting to change my bootloader so that when my machine boots, and no choices are made at the boot menu, Vista automatically starts after a set amount of time instead of Ubuntu. 

I know the boys over at APC have a guide on how to do this, but it involves copying information from the menu.lst file and using EasyBCD - I was wondering if these steps will still work now that I am running Karmic Koala, which I understand uses a different method of changing GRUB entries (manipulating the menu.lst file is no longer part of this process and is no longer recommended)

If someone could tell me how to put Vista in charge of my boot options so that it will boot automatically instead of Linux, that would be greatness.

Cheers guys :)

Go to synaptic and install start-up manager. It goes to System>administration. There you can choose which OS will startup automatically.

---

### Post by ubunterooster on 2010-04-28
Cool! I never saw that before!
Easier then setting up LILO.

---

### Post by KarmaAmputee on 2010-04-28
Awesome - thank you Doug11 - I will download, install and use this!

most helpful, well done.

---

### Post by Doug11 on 2010-04-29
no prob,,anytime,,,i just found out about it not to long ago either.

---

