---
title: "How to update to linux image 2.6.31-19.56 in Synaptic?"
date: 2010-02-12
forum: Installation &amp; Upgrades
---

### Post by maryjo on 2010-02-12
I installed the 2.6.31-19.56 kernel update, booted into it and installed the ATI drivers for my Acer Aspire 7540-1284 laptop. Since it didn't work, I deleted everything to do with 2.6.31-19.56 that was showing as installed in Synaptic.  This successfully removed it from grub.

Later someone pointed out to me that I needed to update again after installing the drivers.

Now I would like to try it again but would like to be sure what packages I need from Synaptic to duplicate the original update to add Ubuntu with 2.6.31-19.56 to grub.  I think I need the meta package?  How would I find out this information?  

:confused:

---

### Post by Jive Turkey on 2010-02-12
Well when you install the non-free driver from ATI it creates a module for the kernel you have installed currently, and when you upgrade the kernel it is usually necessary to build the new module.  Ubuntu makes this a little easier with the restricted driver manager but you end up with slightly older drivers.

Upgrading the kernel can usually be done with the command:```
sudo apt-get update && sudo apt-get dist-upgrade
``` 
GRUB2 is really good at magically updating itself when a new kernel is present with the command:```
sudo update-grub
```
Keep in mind that you will still need to install that proprietary driver yourself (if you downloaded the newest one from ati), if you only have the ubuntu restricted driver module version it should be good to go.

---

### Post by ajgreeny on 2010-02-12
Run synaptic and go to File ->History.  There you will find all the packages you both installed and uninstalled by date listing.  You can then try again, installing the kernel packages you removed.

---

### Post by maryjo on 2010-02-12
I think I will try the command line approach as there are quite a few packages that were removed according to my history in synaptic.

Thank you so much.

---

