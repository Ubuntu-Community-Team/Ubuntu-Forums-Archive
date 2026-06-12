---
title: "Question with a dual boot system - Ubuntu/Win98"
date: 2007-12-14
forum: Installation &amp; Upgrades
---

### Post by dsaint on 2007-12-14
I’m new to Ubuntu - Question with a dual boot system:

I have two separate hard drives; one with Win 98 (secondary drive) and one for Ubuntu (primary drive). I disconnected the secondary drive when I loaded Ubuntu, (which in hindsight, was probably a mistake). Now after re-connecting the 2nd drive grub can’t see Win98. 

I tried editing the menu.lst with the following:

title:		Windows 98
root: 		(hd1,0)
savedefault
makeactive
chainloader	+1

Which has made the selection for windows at least show up on the start menu. However, when I choose it the machine just hangs with “Starting Up ….” At the top of the screen. 

The drive with Win 98 on it does have System Commander on it which may complicate things. I would think that after making the selection in Grub that I would either go to the SC menu or directly into Win 98. I have no idea why it just hangs. Do I need to add to the root line description in the menu.lst?

Any help would be greatly appreciated.

---

### Post by PmDematagoda on 2007-12-14
Could you post the result of:-

```
sudo fdisk -l
```

---

### Post by dsaint on 2007-12-14
dps@dps-desktop:/$ sudo fdisk -l

Disk /dev/hde: 30.7 GB, 30735581184 bytes
255 heads, 63 sectors/track, 3736 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1               1        3581    28764351   83  Linux
/dev/hde2            3582        3736     1245037+   f  W95 Ext'd (LBA)
/dev/hde5            3582        3736     1245006   82  Linux swap / Solaris

Disk /dev/hdf: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdf1   *           1        1275    10241406    c  W95 FAT32 (LBA)
/dev/hdf2            1276        4982    29776477+   f  W95 Ext'd (LBA)
/dev/hdf5            1276        4982    29776446    b  W95 FAT32
dps@dps-desktop:/$ 


Thanks.

---

### Post by dsaint on 2007-12-14
I found the answer on the System Commander website. Apparently all windows versions like to be installed on the primary partition on the first drive.  So I just switched the two drives and re-installed Ubuntu which installed the Grub on the primary partition. It now seems to work fine. 


:)  yea....

---

### Post by Herman on 2007-12-14
> I found the answer on the System Commander website. Apparently all windows versions like to be installed on the primary partition on the first drive. So I just switched the two drives and re-installed Ubuntu which installed the Grub on the primary partition. It now seems to work fine. 
That's one way to fix it, and that's okay if you want to do it that way. Sorry I'm late, but another way to do it would have been to use a pair of GRUB's 'map' commands to trick Windows into thinking it's on the first drive, more information here: [Chainloading Windows on a non-first hard disk]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk")

So you could have just edited your /boot/grub/menu.lst like this,
```
 title 		Windows 98
root  		(hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader	+1

```Sorry I'm late, but it might help someone else looking for a solution if they read this thread.

Regards, Herman :)

---

