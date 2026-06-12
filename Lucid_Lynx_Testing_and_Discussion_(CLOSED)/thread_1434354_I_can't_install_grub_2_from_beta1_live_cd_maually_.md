---
title: "I can't install grub 2 from beta1 live cd maually why not?"
date: 2010-03-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-03-20
first of all i thought that beta 1 would finaly solve my problem with grub 2 and automatilcy install it on sda and sdb but she did not when i try this command:

sudo grub-install /dev/sda

i get:
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

it never happen before the same goes with sdb what can i do now?

sudo grub-install /dev/sdb
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

thanks in advance.

p.s before i did those two commands i did this as usual:

sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo chroot /mnt

for some reason ubuiquty identified it as sda 5 and not as sda2 as it should xubuntu ubiqity detected it properly but it's not suppose to be a problem.

---

### Post by ankspo71 on 2010-03-20
Here is the guide that I used to repair grub.
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
scroll down to "Recover Grub2 via Live CD"
I noticed it looks close to the last string of commands you posted...
Hope this does the trick.

---

### Post by aviramof on 2010-03-20
i fixed the problem by changing the boot sequnce in bios and then installed grub 2 on sda and sdb but i'm really hopping that final version would not have such problems in the end.

---

