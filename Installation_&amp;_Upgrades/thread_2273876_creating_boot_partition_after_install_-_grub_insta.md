---
title: "creating boot partition after install - grub install fails"
date: 2015-04-16
forum: Installation &amp; Upgrades
---

### Post by brendand2 on 2015-04-16
Mint 17.1(Ubuntu 14.04) I have been following the instructions here ( [https://help.ubuntu.com/community/CreateBootPartitionAfterInstall](https://help.ubuntu.com/community/CreateBootPartitionAfterInstall) ) to create a boot partition after install with the intent of chainloading.  I tried the boot repair tool first but it hung while purging linux kernels. I rebooted into live and saw that boot repair had created the fstab entry for my parition and made a backup of the boot directory. I proceded to follow the Manual Way described, but ran into a problem when I tried to install grub onto my boot partition. Since I do not want to overwrite the MBR I am installing to /dev/sda7 (boot partition), not /dev/sda.
```
$ sudo grub-install --force --root-directory=/mnt/main /dev/sda7
grub-probe: error: failed to get canonical path of `/cow'.
Installing for i386-pc platform.
grub-install.real: warning: File system `ext2' doesn't support embedding.
grub-install.real: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
Installation finished. No error reported.
```
I thought this was the standard warning from a non-MBR install. I then tried to chainload but all I get is the grub menu. It was successfully chainloading prior to moving boot to its own partition.

---

### Post by brendand2 on 2015-04-16
Nevermind. Needed to chroot, update grub and then install grub. All good. Wish there was a way to delete posts....

---

### Post by ajgreeny on 2015-04-16
No need (nor wish) for anyone to delete posts where an answer has been found and mentioned as it can be very useful to another person searching the same problem, which is exactly what this forum is for.

---

