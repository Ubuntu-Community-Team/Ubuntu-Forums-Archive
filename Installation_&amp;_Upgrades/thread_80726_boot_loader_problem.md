---
title: "boot loader problem"
date: 2005-10-22
forum: Installation &amp; Upgrades
---

### Post by madjid on 2005-10-22
Hi everyone !!

I tried to install ubuntu yesterday on my laptop but i didn t see it requires 2 GB of free disk space. so i just made a new partition using partition magic (size 1.5 GB) and i tried to install it. As you could expect it failed... so now i have two partitions: one with windows (approx 26 GB) and another one with ubuntu not working (1.5 GB). The grub boot loader is installed and i still can boot my windows from there... 
Do you think it is safe to reformat the ubuntu partition and make it bigger using partition magic ... will the boot loader be still working if i do that ? 
If not do u have any ideas on what i could do to restore my windows boot loader ( i don t have install cds of windows xp i only have master cds which don t say anything about boot loader... :(  ) .....
 

Thank you.


madjid

---

### Post by Koybe on 2005-10-23
Partition magic is never 100% save, so take care of your data. Anyway resizing your partitions won't change anything to the boot loader. So it should work properly.
If you want to get rid of the bootloader, just use fdisk /mbr on windows command line or booting a windows cd (you don't have) and using the fixmbr command.

Good luck.

---

### Post by SilentCacophony on 2005-10-23
> Do you think it is safe to reformat the ubuntu partition and make it bigger using partition magic ... will the boot loader be still working if i do that ?

Hi. Since the /boot/grub/menu.lst file, which contains your boot choices, is on the ubuntu partition, you would strand the grub boot loader if you reformat the ubuntu partition.

There is a way to restore it after doing so, though, and also an optional alternative to install grub to a floppy. I would install grub to a floppy first, before doing the above, then do the restore to MBR step. 

See this thread for info on how to do both operations (the boot floppy is described in the comments following the original post.)

[http://ubuntuforums.org/showthread.php?t=76652](http://ubuntuforums.org/showthread.php?t=76652)

> If not do u have any ideas on what i could do to restore my windows boot loader ( i don t have install cds of windows xp i only have master cds which don t say anything about boot loader...  ) .....


That's tricky if you don't have the install disc. As **Koybe** mentioned, *fdisk /mbr *should work.

Assuming that you have a floppy drive, I'd try the boot floppy procedure first, though.

---

