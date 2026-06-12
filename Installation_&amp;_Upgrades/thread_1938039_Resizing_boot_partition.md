---
title: "Resizing /boot partition"
date: 2012-03-09
forum: Installation &amp; Upgrades
---

### Post by Jiawen on 2012-03-09
When I installed Ubuntu on this machine, I made the /boot partition only 100 MB. That has proven woefully inadequate, because every time a new linux-headers package comes down the pipe, I have to go uninstalling previous kernels to make enough space. I'd like to resize the /boot partition.

It's located at /dev/sdc5, which is right next to the / partition at /dev/sdc6. Is it possible to add space to /dev/sdc5 without screwing up the / partition?

---

### Post by WthIteh on 2012-03-09
If you used LVM, it was very easy.
However, you have some options for now.

[LIST=1]
[*]If there is enough free space after /dev/sdc6 partition, create a new partition there and mount it as new /boot,
[*]If the total available free space (/dev/sdc5 plus free space after /dev/sdc6) is enough, you can move /dev/sdc6 forward and then resize /dev/sdc5,
[*]Otherwise, and if there is enough space in the /dev/sdc6, you can forget about a separate partition and let your /boot to be placed in the / partition.
[/LIST]

---

### Post by Adrian98 on 2012-03-09
Thanks for the ways to fix this problem of Kernel, I wish i could have got this solution few days ago so that I wouldn't have re installed my Ubuntu!!!

---

### Post by pavi_elex on 2012-03-09
:(

---

### Post by Jiawen on 2012-03-10
> **WthIteh said:**
> If you used LVM, it was very easy.? I used the Ubuntu installer. Now, Gparted is the main tool available. 
> If there is enough free space after /dev/sdc6 partition, create a new partition there and mount it as new /boot,How do I do that? Is the boot partition only used when the system is booting up?
> If the total available free space (/dev/sdc5 plus free space after /dev/sdc6) is enough, you can move /dev/sdc6 forward and then resize /dev/sdc5,Really? It's safe to move the root partition?
> Otherwise, and if there is enough space in the /dev/sdc6, you can forget about a separate partition and let your /boot to be placed in the / partition.
[/LIST]How would that work? How do I put it there?

---

### Post by oldfred on 2012-03-10
It is just like a move of /home. You create a partition, move files to new partition and edit fstab with the new UUID. You probably have to reinstall grub also which you would not have to do with a move of /home.
Or just copy/move files back into / and remove entry for /boot from fstab. Reinstall grub. Then if not boot issues you can delete the /boot partition.

What is before sda5? You might be able to shrink that a little, move extended left and move sda5 left and expand to the right. Since it is small it will move quick and have less risk (backups always a good idea). But be prepared to reinstall grub from a liveCD. Moving should not change UUID but you never know.

For most desktops now, you do not need a separate /boot partition. Only server type installs with RAID or LVM or old systems than can only boot from the first 137GB may need a separate /boot partition.

---

### Post by WthIteh on 2012-03-10
> **Jiawen said:**
> 
How do I do that? Is the boot partition only used when the system is booting up?

If you want to use first option and there is enough free space after /dev/sdc6 partition:

[LIST=1]
[*]Open gparted,
[*]Select free space after /dev/sdc6 and create a new partition for /boot (probably named /dev/sdc7),
[*]Apply changes,
[*]Mount /dev/sdc7 anywhere you want (for example /mnt) and then copy all files from /boot to it,
[*]Open gparted again,
[*]Delete /dev/sdc5 (old /boot which you copied all of its files to new partition),
[*]Modify /dev/sdc7 (new partition) and set /boot as its mount point,
[*]Take a look at /etc/fstab to be sure it's information are about new /boot partition,
[*]NOTE: after removing the old /boot partition, all partition numbers (sdc5, sdc6, ...) will be shifted!! You can also let that partition remains there undeleted and just select nothing as its mount point in gparted.
[/LIST]
You can do all of above items in your normal system (it's not required to boot a live CD).
> **Jiawen said:**
> 
Really? It's safe to move the root partition?
Yes, but you need to boot a live CD and open gparted there. Then simply select the root partition and drag and drop to move it to its new location and apply changes.
> **Jiawen said:**
> 
How would that work? How do I put it there?
If you want to forget about a separate /boot partition, you can:

[LIST=1]
[*]Copy /boot completely to somewhere else (like /mnt),
[*]Unmount /boot partition and change /etc/fstab and remove anything related to /boot from there too,
[*]Now the /boot partition will not be used anymore and the /boot can be used like other normal folders in the / partition,
[*]Copy all of /boot contents (for example from /mnt) to /boot (which is now an empty folder) again.
[/LIST]
NOTE: After using anyone of above options, if you can not boot normally (which should not be the case), simply select "recovery mode" from grub menu and then reinstall grub and then reboot. It fixes any possible issue which moving root partition, etc. may cause (of course backing up important files can be useful if you want).
For reinstalling grub use:
```
sudo grub-install --boot-directory=<path-to-/boot-if-you-mounted-it-somewhere-else> /dev/sdc
```

---

