---
title: "Installing latest Kernels - missing modules cat /proc/modules ls /dev"
date: 2016-03-10
forum: Installation &amp; Upgrades
---

### Post by ian_frost2 on 2016-03-10
Hi

I need some help!

I want to upgrade my Kernel due to my dumb ass decision to buy a SKylake proc.

Problem is I cant install a KErnel that has any features of Skylake without getting a error where it cant find my drives partition.

I can install up to 4.2.0-27-generic but after that I get "missing modules cat /proc/modules ls /dev"

I can see the drive if I go into grub command line and can set root to point at the partition and load the kernel and the initrd but as soon as I go boot.

It just says it cant find dev/sda2

I have a Samsung nvme m.2 950 drive and it works fine in 4.2.0 so at a loss why it wont work above that version and I have no idea how to fix it.
[ATTACH=CONFIG]267734[/ATTACH]

Can anyone help me please!

Thanks

---

### Post by SeijiSensei on 2016-03-10
Do you actually have a /dev/sda2?  That refers to the second partition on the primary hard drive, which I presume is the Samsung.

---

### Post by ian_frost2 on 2016-03-10
> **SeijiSensei said:**
> Do you actually have a /dev/sda2?  That refers to the second partition on the primary hard drive, which I presume is the Samsung.

If I use the grub command line and "ls" I can see the partition as (hd0,2) and I can list it and in the /boot are all the kernel files.

I can run "linux" and point it to the correct vmlinux file and set root=/dev/disk/by-uuid/#################

and run "initrd" with the correct.img file, no errors but when I type "boot" I just get the same error.

I then get the busybox prompt and can "cd" into /dev but I do not have the disk/ or sda2/ dir.


I imagine I need to mount this from the busybox prompt but I have no idea how to do that as it doesnt know what (hd0,2) is, anyone know how?

---

### Post by ian_frost2 on 2016-03-11
Any advice on a Forum where I might be able to get some help on this?

Or how do I post to the dev team of Linux with this issue?

---

### Post by SeijiSensei on 2016-03-11
Try booting from a distribution ISO and choosing "Try Ubuntu".  Then you can run grub-install against the drive which might cure the problem.  See "man grub-install" for details.

---

### Post by ian_frost2 on 2016-03-11
> **SeijiSensei said:**
> Try booting from a distribution ISO and choosing "Try Ubuntu".  Then you can run grub-install against the drive which might cure the problem.  See "man grub-install" for details.

I can run the Ubunto from a usb but its the Kernel update that is the problem, sorry I should point out im new to linux administration so forgive me if I do not follow what you say.

I have grub at boot up the problem appears to be the drive not mounting under this kernel, again I dont really follow what you mean could you expand on it.

---

### Post by ian_frost2 on 2016-03-11
Bump!

---

### Post by SeijiSensei on 2016-03-13
Suppose your boot device is /dev/sda, the primary hard drive.  Then if you boot from the USB image, choose Try Ubuntu, then open a terminal and run the command
```
sudo grub-install /dev/sda
```
it will scan all the partitions on /dev/sda and rebuild the boot record. That may solve the problem.

---

