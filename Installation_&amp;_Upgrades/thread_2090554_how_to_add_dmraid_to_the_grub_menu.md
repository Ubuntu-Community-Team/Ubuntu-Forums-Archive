---
title: "how to add dmraid to the grub menu?"
date: 2012-12-02
forum: Installation &amp; Upgrades
---

### Post by bardminz on 2012-12-02
Hi All,


I have a AMD-mobo-supported RAID 1+0 array with 4x 1TB disks. Linux mint 14 is installed. But it failed to enter the grub menu or the os because the array is not recognized (there is an error message in the end saying '/dev/mapper/<raid_id>' is missing). I managed to add a line "dmraid -ay" to the beginning of /boot/grub/grub.cfg and now the grub menu is there. Unfortunately, after selecting the menu item, I still can't enter the os. A busybox 'initramfs' was shown. Does anyone know how to let the system call "dmraid -ay" before the startup?


UPDATE:

I bumped into this bug report : [https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/941874](https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/941874)
 I was able to type "dmraid -ay" in the busybox shell and exit the shell. It then ran normally to the system.

Does anyone know how to automate it so that I don't have to type every time it boots?

Thanks in advance,
-Shawn

---

### Post by bardminz on 2012-12-03
bump with updates. thanks for looking.

---

### Post by darkod on 2012-12-03
If I understand it correctly, you can boot it manually. Do that once and then try updating the initramfs in terminal:
```
sudo update-initramfs -u -k all
sudo update-grub
```

I guess something is missing, maybe during the installation you didn't tell it to detect and use the fakeraid array. That's why it's better to use the array during the install and create a mount point for it even if the OS is not on the array. I'm not sure if something is missing that should have been included during the installation.

---

### Post by bardminz on 2012-12-03
Thanks Darko! I will give a try when I get back home. 

I did install the OS on the array and instructed the installer to install the bootloader on the array too. Somehow, it just missed it.

---

### Post by darkod on 2012-12-03
In that case it might be a bug, so even the update-initramfs might not help, but you can at least try.

---

### Post by bardminz on 2012-12-04
> **darkod said:**
> If I understand it correctly, you can boot it manually. Do that once and then try updating the initramfs in terminal:
```
sudo update-initramfs -u -k all
sudo update-grub
```

I guess something is missing, maybe during the installation you didn't tell it to detect and use the fakeraid array. That's why it's better to use the array during the install and create a mount point for it even if the OS is not on the array. I'm not sure if something is missing that should have been included during the installation.
It works. Now it automatically goes to the login menu although I still need to include "dmraid -ay"  in /boot/grub/grub.cfg 

Thanks Darko. I'm marking this as solved.

---

