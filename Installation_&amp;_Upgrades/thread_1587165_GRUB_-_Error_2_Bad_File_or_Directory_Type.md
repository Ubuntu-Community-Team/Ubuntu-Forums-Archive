---
title: "GRUB - Error 2: Bad File or Directory Type"
date: 2010-10-03
forum: Installation &amp; Upgrades
---

### Post by vadimk on 2010-10-03
After updating to new kernel 2.6.32-25 I can't load it from GRUB. Got "Error2: Bad file or Directory type". Old kernel (i.e. .32-24) loads normally. All kernels and initrd.img files are in the same folder: /boot. The root folder has symlinks vmlinuz-> and vmlinuz.old-> to kernels 25- and 24-. 

I have tried to setup grub from the scratch and re-build the initial ramdisk - but had no luck. Also executed update-grub utility manually, but only one kernel (from the list) loads normally. Please, help - have no ideas where to look for an error. 

Grub - version 0.97
menu.lst file is below:
------------------------------------------------------------------------------------------
title        Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.32-25-generic root=/dev/mapper/isw_dhicfadcee_RigelRAID1 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-25-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-25-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.32-25-generic root=/dev/mapper/isw_dhicfadcee_RigelRAID1 ro  single
initrd        /boot/initrd.img-2.6.32-25-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.32-24-generic root=/dev/mapper/isw_dhicfadcee_RigelRAID1 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-24-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.32-24-generic root=/dev/mapper/isw_dhicfadcee_RigelRAID1 ro  single
initrd        /boot/initrd.img-2.6.32-24-generic

title        Ubuntu 10.04.1 LTS, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin

---

### Post by dino99 on 2010-10-03
dont use " Grub - version 0.97" its outdated and not the ubuntu default installation choice now.

So, boot on 32.24, as it work, and with nautilus search for:

- menu.lst: delete it

then with synaptic:

- search for "grub" and remove/purge (right click) ALL the related grub installed packages

- install grub-pc and grub-common

now reboot, all your installed kernel might works.

---

### Post by vadimk on 2010-10-04
Unfortunately Grub2 does not recognize my "fakeRAID". And new kernel does not want to work with old Grub. I am thinking of "reinstall". :confused:

---

### Post by dino99 on 2010-10-04
on launchpad there is a report against gparted, and a workaround in the latest posts

[https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/600729](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/600729)

---

