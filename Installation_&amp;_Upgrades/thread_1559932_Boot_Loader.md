---
title: "Boot Loader"
date: 2010-08-24
forum: Installation &amp; Upgrades
---

### Post by gavinjb on 2010-08-24
Hi,

I am looking at installing Ubuntu on my Sony NW20ZF/S Laptop, but prior to switching completly to Ubuntu on this machine I am looking at installing it on an external disk and installing the boot loader on the external disk and then when I want to use Ubuntu set the boot priority to this disk (need to check bios still supports this).

Is this possible and if I do get the boot loader installed on the external disk I want to make sure that the installer wont make any changes to my main disk.

Once I have everything up and working on the external disk I will then simply swap the disks.

Thanks,


Gavin,

---

### Post by lechien73 on 2010-08-24
Yes, that will work fine. Often modern BIOSes allow you to press a function key on startup, which will present you with a boot device selection.

When you install Ubuntu, you will need to click the Advanced button on the partitioning screen, and make sure that Grub will be installed to the external disk.

If you're feeling particularly adventurous, then I've made instructions (here: [http://uri.tl/t](http://uri.tl/t)) for adding an Ubuntu option to your Windows Boot Manager menu - so you wouldn't have to change boot priority. This doesn't affect the boot loader of your primary disk at all.

---

### Post by gavinjb on 2010-08-24
Thanks for the help, I now have it installed with boot loader on external hd.

---

