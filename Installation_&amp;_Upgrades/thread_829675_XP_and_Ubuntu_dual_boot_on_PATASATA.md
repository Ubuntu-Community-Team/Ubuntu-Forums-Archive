---
title: "XP and Ubuntu dual boot on PATA/SATA"
date: 2008-06-15
forum: Installation &amp; Upgrades
---

### Post by rvijay17 on 2008-06-15
Hi,

I have installed Ubuntu 8.04 on my PATA disk and XP on my SATA disk. Only after doing this, I got to know that i can't have my PATA disk as the first boot device. I am now stuck as I can't boot Ubuntu.

Is there anyway I can modify boot.sys (or the boot.ini file or some Windows file) such that windows bootloader shows the two OSes.

I do not want to install GRUB on my SATA(Windows) disk.

Regards,
Vijay.

---

### Post by meierfra. on 2008-06-16
Get Supergrub (see my signature) and follow this howto:

[http://www.supergrubdisk.org/wiki/Howto_Boot_Grub_from_windows](http://www.supergrubdisk.org/wiki/Howto_Boot_Grub_from_windows)

Use the classical solution, also when it says:

sudo su
grub

use "sudo grub" instead.


If you need additional help, boot from the Ubuntu Live CD, open a terminal
(Applications->Accessories->Termianl) and post the output of

 ```
sudo fdisk -l
```
( l is a lower case L)

But I would recommend to install Grub  (the Ubuntu boot loader) to the MBR of the SATA drive, and then add Windows to the Grub Menu.

That is easier than adding Ubuntu to boot.ini and also is more reliable.

---

### Post by adrian15 on 2008-06-17
> **meierfra. said:**
> 
Use the classical solution, also when it says:

su
grub

use "sudo grub" instead.


In the wiki it is written **sudo su** instead of **su**.

Any problem about it? How can we improve it?

adrian15

---

### Post by meierfra. on 2008-06-17
> In the wiki it is written sudo su instead of su.

Oops, I edited my post.


> Any problem about it? 
"sudo su"  only works when the root password is enable.  But in Ubuntu the root password is disabled by default. Also Ubuntu strongly discourages from enabling the root password.


> How can we improve it?

One could write:

```
su
grub
(in Ubuntu use "sudo grub" instead)

```

That only works well if only one command requires "sudo".

So maybe in general this is better:

```
su  (use "sudo -i" in Ubuntu)
grub
```

---

