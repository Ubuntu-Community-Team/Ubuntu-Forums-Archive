---
title: "FreeSpire and UBUNTU manual grub"
date: 2008-03-12
forum: Installation &amp; Upgrades
---

### Post by n2stc on 2008-03-12
Hello all & thanks for reading.  

I recently put FreeSpire on a machine where UBUNTU and XP already exist, just to try it.  I like the interface (maybe i should try KUBUNTU).  Any way I forgot to uncheck the write MBR box, so after I couldn't start anything but FreeSpire. I reinstalled grub and editied the menu.lst file so I can BOOT XP or UBUNTU, but don't know how to enter FreeSpire in there.  Does any one know what the manual entries would be?  I've looked a several posts but don't see it.  I tried to look at the files FS generated for an example, but can't open them.  Any help is appreciated: THANKS!

Stan

---

### Post by dstew on 2008-03-12
Your freespire partition is probably not bootable at the moment because it put the grub stage1 into the MBR. When you restored your previous grub to the MBR, it over-wrote the freespire grub.

The way to fix this is to install grub to the freespire *_partition_*, then change your /boot/grub/menu.lst file in your Ubuntu system to boot the freespire partition. Note: when you install grub into the freespire partition, it might show you a new menu, from freespire, that you made before. That's OK, if you select freespire it will probably boot.

To install grub into the freespire partition you need to know its name in grub-speak. From your Ubuntu boot, open a terminal and enter```
sudo fdisk -l
```That will show us what your partitions look like. If your freespire partition is, say, /dev/hdb1, then the correct grub root for installing it there should be (hd1,0). Then you give that same partition name to the setup command. To install grub this way, from your Ubuntu terminal enter ```
sudo grub
```This gets you the grub command line with the grub> prompt. At the grub prompt, enter these commands:```
root (hd1,0)
setup (hd1,0)
quit
```This will put a grub stage1 into the boot sector of that partition, and it should be pointing to the root directory of that same partition to get the rest of its boot code and the freespire grub menu.

To finish, you need to put a statement in your Ubuntu /boot/grub/menu.lst file to boot the (hd1,0) partition. You do it by chainloading, same as for Windows. You don't need map statements though. Try this in your menu.lst file:```
title Freespire
root (hd1,0)
chainloader +1
```The main problem you are likely to have is being sure of the proper grub-name for the freespire partition. Grub counts from 0, so disk hda is (hd0), hdb is (hd1). Same for partitions. So, sda1 is (hd0,0), sdb2 is (hd1,1)...

---

