---
title: "Dual boot - Ubuntu and Ubuntu?"
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by spiney_norm on 2007-12-19
I installed ubuntu fine once, but then when I was trying to delete my Windows XP crap I must have accident;y deleted something for Ubuntu, So when I restarted my computer nothing happened, no ubuntu, no xp. I put my Ubuntu disk in and re-installed Ubuntu. After I did this my first installation of Ubuntu started to work again. All I want to know is how to get rid of the second Ubuntu I installed.

---

### Post by logos34 on 2007-12-20
Reinstall grub pointing to the original ubuntu.  Then you can delete the second one.

For example, if your original ubuntu install is sda2/(hd0,1), then you would go

sudo grub

> root (hd0,1)
> setup (hd0)
> quit


Delete second ubuntu with Gparted:

sudo gparted

unmount the second ubuntu, then delete it.

---

### Post by spiney_norm on 2007-12-20
Thanks for the help I think you got me pointed in the right direction.

---

### Post by logos34 on 2007-12-20
Sure thing.  Have fun with 'boon2

---

