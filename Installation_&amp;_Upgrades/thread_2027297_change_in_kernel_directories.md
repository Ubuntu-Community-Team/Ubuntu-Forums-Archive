---
title: "change in kernel directories"
date: 2012-07-16
forum: Installation &amp; Upgrades
---

### Post by AbhijitG on 2012-07-16
Hi,
I have upgraded from ubuntu 10.10 to 11.04.
& had uame -r > 2.6.38-15-generic-pae
Now the problem is when i want to build kernel modules it doesnt have build directory in location /lib/modules/2.6.38-15-generic-pae/ 
I can not compile the modules without those and with the previous kernel files :(
Plz Can anybody tell me what is happening?

---

### Post by dino99 on 2012-07-16
/lib/modules/ is only cleaned when a kernel is purged. So you might have the kernel(s) subfolder(s) actually installed. Update the system and reinstall the missing kernel, then /lib/modules/ will have it.

[https://launchpad.net/ubuntu/+source/linux](https://launchpad.net/ubuntu/+source/linux)

---

### Post by AbhijitG on 2012-07-17
Thnx dino99

Dont wanna know why that happened but installed new kernel 3.3.4
and back to normal routine

---

