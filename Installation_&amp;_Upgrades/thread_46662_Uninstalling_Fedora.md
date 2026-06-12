---
title: "Uninstalling Fedora"
date: 2005-07-05
forum: Installation &amp; Upgrades
---

### Post by burnhamd on 2005-07-05
I installed ubuntu on my computer that already had windows on it and then I installed fedora after that to test it out.  Now I want to take fedora off and restore Ubuntu's Grub.  How do I go about doing this.  Anyway here is the setup as reported by fdisk

```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3264    26218048+   c  W95 FAT32 (LBA)
/dev/sda2            3265        5209    15623212+  83  Linux
/dev/sda3            5210        5222      104422+  83  Linux
/dev/sda4            5223        9729    36202477+   5  Extended
/dev/sda5            5223        9728    36194413+  8e  Linux LVM
``` 

Windows is of (as you may guess) sda,1 and Ubuntu is sda3
Now fedora took three partions and I think sda4 and sda5 are in fact two logical groups.

can you give me directions on taking off everyting but windows and ubuntu and still with my dual boot intact.

---

### Post by Xian on 2005-07-05
[QUOTE=burnhamd]I installed ubuntu on my computer that already had windows on it and then I installed fedora after that to test it out.  Now I want to take fedora off and restore Ubuntu's Grub.  How do I go about doing this.  Anyway here is the setup as reported by fdisk

```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3264    26218048+   c  W95 FAT32 (LBA)
/dev/sda2            3265        5209    15623212+  83  Linux
/dev/sda3            5210        5222      104422+  83  Linux
/dev/sda4            5223        9729    36202477+   5  Extended
/dev/sda5            5223        9728    36194413+  8e  Linux LVM
``` 

Windows is of (as you may guess) sda,1 and Ubuntu is sda3
Now fedora took three partions and I think sda4 and sda5 are in fact two logical groups.

can you give me directions on taking off everyting but windows and ubuntu and still with my dual boot intact.[/QUOTE]
Ubuntu can not be on sda3 as that partition is way too small.
Perhaps you have it on sda2.

You should be using a swap partition but generally if it was sda2 it would have the 'Linux swap' notation, but even then it does not look large enough to serve this purpose. You may want to look more closely at this scheme.

Anyway, once you get all the mount points sorted all you need is to either use a parted GUI (gparted, qtparted, etc), the install CD, or a windows tool to remove or reformat the Fedora partitions, and then to reinstall grub with Ubuntu you would just issue the 'sudo grub-install /dev/sda' command if this is a single HD from a terminal. Make sure you don't get any errors before rebooting, and also double-check your /boot/grub/menu.lst file before resetting grub to see that it is properly configured. In addition, you will need to verify your /etc/fstab to ascertain that when you reboot the system will only be mounting valid partitions. You certainly don't want it attempting to access those old Fedora paths (if any are present) as that will result in a failed boot.

---

