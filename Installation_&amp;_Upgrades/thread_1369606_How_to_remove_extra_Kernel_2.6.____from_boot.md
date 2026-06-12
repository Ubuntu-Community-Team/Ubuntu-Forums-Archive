---
title: "How to remove extra Kernel 2.6._ _ from boot"
date: 2010-01-01
forum: Installation &amp; Upgrades
---

### Post by F8M on 2010-01-01
How do I remove the _extra_ Kernels from my boot menu as listed below?
 
Ubuntu 9.10, Kernel 2.6.31 16 generic
Ubuntu 9.10, Kernel 2.6.31 16 generic (recovery mode)
Ubuntu 9.10, Kernel 2.6.31 15 generic
Ubuntu 9.10, Kernel 2.6.31 15 generic (recovery mode)
Ubuntu 9.10, Kernel 2.6.31 14 generic
Ubuntu 9.10, Kernel 2.6.31 14 generic (recovery mode)
Ubuntu 9.10, Kernel 2.6.28 16 generic
Ubuntu 9.10, Kernel 2.6.28 16 generic (recovery mode)
Ubuntu 9.10, memtest86+
Other operating systems:
Window Vista (loader)

---

### Post by ajgreeny on 2010-01-01
The best, though not the only way is to search for them in synaptic and uninstall them.  I advise you first to check which you are actually booting to by default with the command ```
uname -a
```and to make sure that you keep that and the previous one, in your case keeping 2.6.31-15 and 2.6.31-16 is probably the way to go.

I assume you have updated from 9.04 to 9.10 as you still have a 9.04 kernel in the list, so I wonder if you are still using legacy grub.  If so you can simply edit the /boot/grub/menu.lst file, but if you are using grub2, you can not edit the /boot/grub/grub.cfg in the same way, and I have not yet quite figured how to stop all the kernels showing in grub2's menu.

---

### Post by lidex on 2010-01-01
Go ahead and remove as advised by ajgreeny, then run the ```
sudo update-grub
``` command.

Text from grub 2 ubuntu community documentation:
> grub.cfg is overwritten anytime there is a update, a kernel is added/removed, or the user runs update-grub

More here:
[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

---

### Post by ajgreeny on 2010-01-01
If kernels are uninstalled by synaptic, update-grub is run by the system automatically during the changes, so no need to run it again.

---

