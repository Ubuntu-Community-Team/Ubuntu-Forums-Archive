---
title: "New compiled Kenel not in grub-menu"
date: 2010-09-25
forum: Installation &amp; Upgrades
---

### Post by philippjosefrichard on 2010-09-25
After having patched the kernel with an ABI-patch 
I cannot find it in the grub2-Menu
OS: Ubuntu 10.04 LTS



in /boot I can see:
**the original and the new config-file**

> config-2.6.30.1ABI-2.6.29.1_4 
config-2.6.32-21-generic
[B]
The original and new  vmlinuz-file[/B]

> vmlinuz-2.6.32-21-generic 
vmlinuz-2.6.30.1ABI-2.6.29.1_4
[B]
Original and new  System.map:[/B]

> System.map-2.6.32-21-generic 
System.map-2.6.30.1ABI-2.6.29.1_4

**_But only one initrd.img:_** 

> initrd.img-2.6.32-21-generic

/boot/grub/menu.lst contains "> vmlinuz-2.6.30.1ABI-2.6.29.1_4 "

But I cannot find it in  /boot/grub/grub.cfg

Concerning:**menuentry 'Ubuntu, mit Linux 2.6.30.1ABI-2.6.29.1_4'**

```
sudo /usr/sbin/grub-mkconfig
``` displays the following line:>  menuentry 'Ubuntu, mit Linux 2.6.30.1ABI-2.6.29.1_4'


```
sudo update-grub
``` did run afterwards.

Does somone know, what I did wrong?

Thanks
Philipp

---

### Post by philippjosefrichard on 2010-09-27
I got the solution:

I had the old grub still installed. 
Installing Ubuntu 10.04 new, but did the partitioning manually. So obviasly grub remained in the MBR.

Installing grub2 with synaptic, which automatically deinstalled grub
was the solution!

---

