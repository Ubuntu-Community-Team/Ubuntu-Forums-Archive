---
title: "howto select another kernel at boot in karmic?"
date: 2010-03-26
forum: Installation &amp; Upgrades
---

### Post by zepita on 2010-03-26
Hi,

In previous versions of ubuntu I was able to select another kernels at boot by pressing esc key.
I have upgraded to 2.6.31-20 and want to get back to 2.6.31.14 but grub boots up without prompting.

Is there an easy way to do this?

Thanks!

edit: (did not mean to put gobuntu)

---

### Post by Cork87 on 2010-03-26
In the file /boot/grub/menu.lst you can set the kernel that your system boot. 

The kernels are listed here. Default it will pick 0 , change this to the kernel you want and it will boot the kernel.

---

### Post by oldfred on 2010-03-27
If it is a new install of Karmic it has grub2 and no menu.lst.

Either grub or grub2 versions can use startup manager to set default.

Startup manager in synaptic will allow you to set boot default and the timeout even in lucid.

---

### Post by r_s on 2010-03-27
If you haven't removed your previous kernels you can still use them, by default grub2 keeps all your kernels listed unless you remove them.

---

### Post by drs305 on 2010-03-27
To just access the menu during boot in Grub 2, hold down the SHIFT key instead of ESC. 

If you want to change the default for every boot, take a look at the SUM or G2-Tasks links in my signature line for making permanent changes.

---

