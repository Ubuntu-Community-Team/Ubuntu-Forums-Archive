---
title: "Fatal error:  unable to install grub in dev sda"
date: 2011-12-22
forum: Installation &amp; Upgrades
---

### Post by arstickman on 2011-12-22
I'm trying to install Ubuntu and I am getting an error message of unable to install grub in dev sda.  Then a dialogue box popped up that reads:

Sorry, an error occurred and it is not possible to install the bootloader at the specified location.

How would you like to proceed?

Choose a different device to install the bootloader on:

Continue without a boot loader.

Cancel the installation.


Ubuntu works off the disk but I keep getting the same error when I try to install it. Does anyone know how to solve this?

Thank you

---

### Post by Rubi1200 on 2011-12-24
Hi and welcome to the forums :-)

From the LiveCD post the results of the following command:

```
sudo fdisk -l
```

(Lowercase L not 1)

Thanks.

---

### Post by james2b on 2011-12-24
See this site; [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) , also what are your other operating systems on that PC, and which version of the Ubuntu, the new 11.10 ? And try to give more information about the computer with this issue, hardware, how old, etc. thanks. You can choose to install the grub2 onto your Ubuntu's root partition, so say like this if it is # 2 of drive sda partition; /dev/sda2, then you can latter chain load to that Ubuntu boot loader from say a another Linux flavor install.

---

### Post by echo6 on 2011-12-24
Are you installing to lvm, crypto devices or raid?

[https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bugs?field.status:list=NEW](https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bugs?field.status:list=NEW)

---

