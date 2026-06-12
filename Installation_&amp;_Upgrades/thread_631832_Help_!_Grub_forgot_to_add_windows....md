---
title: "Help ! Grub forgot to add windows..."
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by Amamba on 2007-12-04
Hi, 

I hope somebody can help. I just tried Ubuntu again, almost two years since giving up on 6.06. Well, this time, GRUB install didn't even suggest adding WinXP to the boot list. I hoped to find it in menu.lst but it's not there, either. 

Here's the output of fdisk -l:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4079    32764536    7  HPFS/NTFS
/dev/sda2            4080       19377   122881185    7  HPFS/NTFS
/dev/sda3           19378       23966    36861142+  83  Linux
/dev/sda4           23967       24321     2851537+  82  Linux swap / Solaris

the /dev/sda1 is where XP is installed, how do I add it to the menu.lst (I know the process of editing menu.lst, just need to know how to properly "call" for windows - hda0,0 didn't work).

Thanks !](*,)

---

### Post by raul_ on 2007-12-04
Here's mine.

REMEMBER TO REPLACE WHERE NEEDED.

since you said you know how it works ;)
```

# (1) Windows
title Windows
rootnoverify (hd0,0)
makeactive
chainloader +1

```
and fstab 
```

[raul@osiris ~]$ sudo fdisk -l
Palavra passe: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4fba4fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4212    33832858+   7  HPFS/NTFS
/dev/sda2            4344       14593    82333125    f  W95 Ext'd (LBA)
/dev/sda3            4213        4343     1052257+  82  Linux swap / Solaris
/dev/sda5   *        4344        5873    12289693+  83  Linux
/dev/sda6            5874       14593    70043368+  83  Linux

Partition table entries are not in disk order

```

---

### Post by Amamba on 2007-12-04
Thanks ! That worked, although I could swear I did have hda0,0 before...

Eh, nevermind - your post says hd0,0 ! 

Thanks for help, again ! Now, on to the next problem...

---

