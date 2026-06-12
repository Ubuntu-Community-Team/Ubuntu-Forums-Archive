---
title: "Installed Ubuntu and cannot boot to WinXP"
date: 2008-04-21
forum: Installation &amp; Upgrades
---

### Post by jakev383 on 2008-04-21
Never had this happen before....
I wanted 3D acceleration for a Win game, so I backed up my system (debs, home) and wiped the drive clean. I installed WinXP Pro and had that all working fine. I then installed Ubuntu on the remainder of the drive and can boot into Ubuntu just fine.  I cannot boot into Windows though.  Here's my partitions:
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ea456

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          19      152586   83  Linux
/dev/sda2              20        6393    51199155    f  W95 Ext'd (LBA)
/dev/sda3            6394       19457   104936580   83  Linux
/dev/sda5              20        6393    51199123+   7  HPFS/NTFS

```

/dev/sda5 is the Windows partition.  Windows does not show up in the grub menu at all, even after running update-grub.
Anyone see why?

---

### Post by mikewhatever on 2008-04-21
Open grub menu for editing with <gksudo gedit /boot/grub/menu.lst> and add the following to the bottom of the file:
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda4
title           Microsoft Windows XP
root            (hd0,4)
savedefault
makeactive
chainloader     +1


---

### Post by jakev383 on 2008-04-21
I had tried that shooting in the dark. I get a 
```

Error 12: Invalid device Requested

```

I did have a 150M partition at the start of the drive that I was going to use to put grub on when I initially installed WinXP, and I think it may have installed it's boot stuff there. That'll mean reinstalling WinXP again to only use it's single partition right?
Thanks for the help!

---

### Post by mikewhatever on 2008-04-21
How did you partition the HDD after wiping it clean? It seems strange for Windows to end up on the 4-th partition, especially after having been installed on a clean HDD. If I understand correctly, Ubuntu is on sda3. What's on sda1 now?

---

### Post by louieb on 2008-04-21
I've heard its a pain in the butt to get windows  to boot when its installed  on a logical partition.   If you want XP,  think your going to wind up  installing it in a primary partition. 

If you do get it running in sda5 please post back and let us know how you did it. It would be interesting to see how its done.

---

### Post by jakev383 on 2008-04-21
> **mikewhatever said:**
> How did you partition the HDD after wiping it clean? It seems strange for Windows to end up on the 4-th partition, especially after having been installed on a clean HDD. If I understand correctly, Ubuntu is on sda3. What's on sda1 now?

I used the grub boot disk to delete all partitions. I booted XP and created 2 partitions, sda1 which was the 150M partition I intended for grub once WinXP was done installing, and then I created a partition for Win itself. I left the rest of the drive open, and used that when I reinstalled Ubuntu.
sda1 now has grub on it, Maybe I outsmarted myself when creating the 150M part?
At least I saved that damn service pack as a network install. I have another drive in the machine I can move it to if I need to reinstall.

---

### Post by sandysandy on 2008-04-21
some links to dual boot

[http://apcmag.com/how_to_dual_boot_w...lled_first.htm](http://apcmag.com/how_to_dual_boot_w...lled_first.htm)

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

[http://www.linux.com/feature/114157](http://www.linux.com/feature/114157)

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

regards

---

### Post by jakev383 on 2008-04-22
Just so everyone know, I ended up deleting ALL the partitions on the system, installing XP and then putting Ubuntu back in. I fought with it for several hours on the extended partition before I finally gave up and started over.
I think I outsmarted myself by creating the 150M /boot partition. It was initially formatted with FAT32 by XP and since it was the first partition on the drive I think XP used it for it's bootloader. When I installed grub over it I had no Win bootloader to chain to.  Or I'm totally off-base.  Either way I have it working and can play the game now.
Thanks all!

---

