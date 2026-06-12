---
title: "grub segmentation fault after upgrade to 13.10"
date: 2014-03-04
forum: Installation &amp; Upgrades
---

### Post by David_Witham on 2014-03-04
After upgrading from 13.04 to 13.10 grub now segmentation faults when I tried to write the new config:

# grub-install /dev/sda
Segmentation fault (core dumped)
Segmentation fault (core dumped)
Path `/boot/grub' is not readable by GRUB on boot. Installation is impossible. Aborting.

This is an EFI system if that makes a difference.

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2       909G   20G  844G   3% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            3.9G   12K  3.9G   1% /dev
tmpfs           790M  1.4M  788M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G  544K  3.9G   1% /run/shm
none            100M   44K  100M   1% /run/user
/dev/sda1        95M  487K   95M   1% /boot/efi

I ran boot_repair and it removed and reinstalled a heap of grub related packages but it didn't fix the problem.

I can manually boot the new kernel from the grub advanced options (the old kernel is incompatible with some newer drivers) so I don't think its the kernel thats the issue.

Any ideas?

thanks,
David

---

### Post by fantab on 2014-03-05
> **David_Witham said:**
> After upgrading from 13.04 to 13.10 grub now segmentation faults when I tried to write the new config:

# grub-install /dev/sda
Segmentation fault (core dumped)
Segmentation fault (core dumped)
Path `/boot/grub' is not readable by GRUB on boot. Installation is impossible. Aborting.

This is an EFI system if that makes a difference.

I ran boot_repair and it removed and reinstalled a heap of grub related packages but it didn't fix the problem.


If you ran Boot-Repair [BR], then didn't you note/save the Bootinfo Summary? If you did then post it here.
But if you didn't then run BR again and only 'create a Bootinfo Summary'.... note the web url where the bootinfo is located and post it here.

Since you have an EFI System Partition [EFI] then Grub should be installed there (ESP) and not on /dev/sda, which by the way, is the default location for MBR systems.
And I think it is this which is causing 'segmentation fault'. 

However, BR should have fixed this by re-installing grub-efi... let's see that Bootinfo.

---

