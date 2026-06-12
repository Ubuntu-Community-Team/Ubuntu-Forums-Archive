---
title: "How do i upgrade from  2.6.22-14-generic #1 SMP to 2.6.23.1 kernel"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by jaffa_nz on 2007-11-05
Kia Ora

While attempting to troubleshoot this damnable Gutsy freeze problem someone mentioned moving to kernel 2.6.23.1.  [[http://ubuntuforums.org/showthread.php?t=587905&page=8]](http://ubuntuforums.org/showthread.php?t=587905&page=8]) 

Can anyone tell me how to do this?

i did an upgrade from feisty to gutsy so thought i was on the latest, at 2.6.22-14 generic smp.  am more than happy to move to a development kernel if i could get some peace from these machine freezes. lords!

all help appreciated.  thanks

---

### Post by scrooge_74 on 2007-11-05
go into synaptic and find the linux-image-2.6.xx-x-xxx  kernel you want to use.

After you install it reboot.

Rinse and repeat

If the kernel gives you problesm at next reboot go into GRUB and pick the one you were using before

---

### Post by jaffa_nz on 2007-11-06
Kia Ora

i think what i'm after is the repository lines to add so that when i search for "linux-image" in synaptic, it lists 2.6.23.1.  Mine currently only displays 2.6.22-14.46 which i have installed.

cheers

---

### Post by scrooge_74 on 2007-11-06
I am not currently using Ubuntu so I am not so sure which image is the latest one, but if you do a update of the repositories and it appears in the list then you can use. If not there then it is not ready to be use and then you would have to get it yourself from kernel.org and download the source code and compile.

As I am writting the Etch kernel is 2.6.18-xxx, but I went to the backports to get 2.6.22-2

You can also try changing from generic to another kernel image, usually generic will get you the latest one once they update the repositories

---

