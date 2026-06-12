---
title: "Can't boot Ubuntu/Please assist"
date: 2013-01-31
forum: Installation &amp; Upgrades
---

### Post by lferg on 2013-01-31
Sh here is what happen.  I had 10.4 running great, had to install Windows for something that couldn't be done through through virtual machine.  So, I booted with a Ubuntu Live CD, and used gparted to make a partition for Windows. I just unmounted my HDD and made a 50GB portion for Windows.  I turned off my machine and Ubuntu booted up just fine with all my files intact.  Now, I install Windows on the freshly made partition. Everything goes great except  every boot in now directly to Windows. I used LiveCD to run gparted and changed the boot flag from the windows partition to Ubuntu. When I boot now, It says something to the effect of "No Operating System". So I change the boot flag back to the Windows one and now what do I do?  :(

---

### Post by Bucky Ball on 2013-01-31
Boot Repair:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You can install it while running from the LiveCD. If it doesn't fix will give you all the information needed for us to see what's happening. Post here, please.

Can you boot into Ubuntu at all? If so:

```
sudo update-grub
```

Restart.

---

### Post by lferg on 2013-01-31
> **Bucky Ball said:**
> Boot Repair:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You can install it while running from the LiveCD. If it doesn't fix will give you all the information needed for us to see what's happening. Post here, please.

Can you boot into Ubuntu at all? If so:

```
sudo update-grub
```Restart.

I can not boot into Ubuntu at all.  I will try this tomorrow evening and let you know... Thanks for this.  I was fearing I would have to reinstall and loose everything

---

### Post by Bucky Ball on 2013-02-01
Boot repair is your friend. And as I say, don't forget to post the report Boot Repair outputs if it doesn't fix.

Reinstall last resort and not there yet. ;)

---

### Post by lferg on 2013-02-01
This was the out put.  Had to put it somewhere, about to reboot and I'll let you know how it goes.


Boot successfully repaired.

Please write on a paper the following URL:
[http://paste.ubuntu.com/1599355/](http://paste.ubuntu.com/1599355/)

In case you still experience boot problem, indicate this URL to:
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] or to your favorite support forum.

You can now reboot your computer.



IT WORKED!!! Holy crap thanks guys

---

### Post by Bucky Ball on 2013-02-02
All good and glad it worked. Please mark the thread as Solved from Thread Tools to help others. ;)

---

