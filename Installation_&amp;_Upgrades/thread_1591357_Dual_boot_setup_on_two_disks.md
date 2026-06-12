---
title: "Dual boot setup on two disks"
date: 2010-10-09
forum: Installation &amp; Upgrades
---

### Post by alt.dev on 2010-10-09
Hello !

When Ubuntu 10.04 was released I installed it in a partition on my main drive. The configuration was something like this :

||Recovery Partition||WinVista||Ubuntu||Data Partitions ...||

Ubuntu installed GRUB and while it booted the two OSes just fine, it made my laptop's Windows recovery partition inaccessible and despite many attempts at trying to recover the recovery partition it never worked. This, combined with some unresolved sound issues led me to wipe off Ubuntu at the time.

I'm planning to install 10.10 on my desktop. I've salvaged a 120GB SATA drive from an another system that I plan to dedicate to Linux installs. Now this time I want to keep my primary Windows 7 HDD unaffected from the Linux install. Is there some way to make sure that the GRUB install will not overwrite the primary HDD MBR ? The configuration I'm aiming for is this :

Primary Drive :
||Win7||Data Partitions ... ||

Secondary Drive :
||Ubuntu Partitions ||

I want to be able to choose which drive to boot from using the BIOS F12 boot device selection menu.

Is this possible ?

---

### Post by mikewhatever on 2010-10-09
Yes, there is. Look at step 8 of the installation guide:
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

The 'Advanced' button lets you choose where to install grub. The default choice it sda, which is not what you want. The secondary hdd should be designated as sdb or sdc.

---

### Post by cascade9 on 2010-10-09
Or do it the lazy way- just disconnect the windows HDD when you install the 120GB HDD for linux. Install linux, shut down, then reconnect the windows HDD...then change the defualt booting HDD (in BIOS) to whatever OS you want to start normally. 

If you want to start the other OS, just go into BIOS, or hit the 'select what device to boot from' key (normally F12). Easy!

---

### Post by alt.dev on 2010-10-09
Thanks for the suggestions guys. I though of the "lazy" method too but I figured in that case Ubuntu would not get a chance to auto-mount my NTFS partitions during setup. If I do use this trick, would it be easy to reattach the NTFS drive later on and have Ubuntu mount my partitions ?

---

### Post by mikewhatever on 2010-10-09
Making an ntfs partition automount is very easy indeed.
[http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows)

---

### Post by Mark Phelps on 2010-10-09
> **alt.dev said:**
> Thanks for the suggestions guys. I though of the "lazy" method too but I figured in that case Ubuntu would not get a chance to auto-mount my NTFS partitions during setup. If I do use this trick, would it be easy to reattach the NTFS drive later on and have Ubuntu mount my partitions ?

You don't want to automount your Win7 OS partition, at least, not read-write. That's asking for trouble as any filesystem problems brought about by unclean shutdown could render your Win7 OS partition unbootable.

---

