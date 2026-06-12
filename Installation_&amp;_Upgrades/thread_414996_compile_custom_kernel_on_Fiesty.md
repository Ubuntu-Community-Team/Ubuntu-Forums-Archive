---
title: "compile custom kernel on Fiesty?"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by SundaY82 on 2007-04-20
Hi,

I just did a fresh install of Fiesty and wanted to add support for raid5 and dmcrypt to the kernel so i compiled my own kernel using this guide (have followed this guide several times before with perfect result) [http://www.howtoforge.com/kernel_compilation_ubuntu]("http://www.howtoforge.com/kernel_compilation_ubuntu").

But now i get this when trying to install my newly compiled kernel:

```
root@mysystem:/usr/src# dpkg -i linux-image-2.6.20.7-custom_2.6.20.7-custom-10.00.Custom_i386.deb
Selecting previously deselected package linux-image-2.6.20.7-custom.
(Reading database ... 17286 files and directories currently installed.)
Unpacking linux-image-2.6.20.7-custom (from linux-image-2.6.20.7-custom_2.6.20.7-custom-10.00.Custom_i386.deb) ...
Done.
Setting up linux-image-2.6.20.7-custom (2.6.20.7-custom-10.00.Custom) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.20.7-custom
find: /lib/firmware/2.6.20.7-custom: No such file or directory
find: /lib/firmware/2.6.20.7-custom: No such file or directory
find: /lib/firmware/2.6.20.7-custom: No such file or directory
find: /lib/firmware/2.6.20.7-custom: No such file or directory
find: /lib/firmware/2.6.20.7-custom: No such file or directory
find: /lib/firmware/2.6.20.7-custom: No such file or directory
```
and then it just stops there.

Any suggestions on how i can fix this i would greatly appreciate it?

Thanks in advance
Ola Ahlman

---

### Post by SundaY82 on 2007-04-20
i see now that Fiesty comes with 2.6.20.15 ... this one aint available through kernel.org what i can see

is there any other way to activate raid5 and dmcrypt except compiling new kernel?

some are marked as M in the kernel config but some isnt marked at all like AES and so, so that must mean that i cant activate the ones that isnt marked as M as a module, right?

Anyone with some advice?

---

