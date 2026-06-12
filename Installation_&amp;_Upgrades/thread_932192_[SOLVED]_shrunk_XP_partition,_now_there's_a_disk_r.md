---
title: "[SOLVED] shrunk XP partition, now there's a disk read error"
date: 2008-09-28
forum: Installation &amp; Upgrades
---

### Post by xchronox on 2008-09-28
I used the ubuntu live cd and gparted to shrink my XP partition... I knew it was risky, but I didn't think it would end this badly...
Basically, after I shrunk the partition, XP lost its boot capabilities. I don't think it has anything to do with grub since grub is pointing towards (hd0,0) where the XP partition is...
I think it's boot.ini but i have not for the life of me been able to find a solution that doesn't involve reinstalling windows. 

The exact process I go through to boot is:
I turn on the computer
Grub comes up
I select XP
is goes to a new screen saying "starting up..."
which is immediately followed by:
     A disk read error occurred
     Press Ctrl+Alt+Del to restart

If anyone has a solution to this that doesn't involve formating I would be forever in their debt.

---

### Post by Partyboi2 on 2008-09-28
If you have a windows xp disk boot that and go into recovery and try checking the disk.
```
chkdsk /r
```
Another one to try is
```
fixboot
```

---

### Post by xchronox on 2008-09-28
thanks for replying so quick :)
I've searched and I can't find a working XP disc. I tried my vista one for my laptop but it didn't have fixboot. I might be able to get one in a few weeks but if there's any other way to fix this...
Maybe if I could somehow get the parameters for the XP boot sector and manually input them into boot.ini, after all my Ubuntu OS is working perfectly at the moment.

---

### Post by caljohnsmith on 2008-09-28
Since you have a Vista install/recovery CD, just use that to run "chkdsk /r" on your Windows XP partition. First try that and report what happens when you boot Windows again, and also post the output of:
```
sudo fdisk -lu
```
If the chkdsk is not enough to get Windows going, it is possible to use "testdisk" in linux to fix the Windows partition boot sector similar to "fixboot", assuming a backup one is available in your Windows file system (usually there is one). But try the chkdsk first, let me know what happens, and we can go from there.

---

### Post by Pumalite on 2008-09-28
Try to boot/fix XP with Super Grub:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by xchronox on 2008-09-28
hm, when I use the Vista CD "repair this computer" option, it doesn't detect the XP partition as being a windows installation... I can however browse to it with the "load drivers" feature. 
if I ignore that and continue onto the command prompt, typing chkdsk /r gives me:
```
The type of the file system is NTFS.
Cannot lock current drive.
Windows Cannot run disk checking on this volume because it is write protected.
```

So here's the output to fdisk:

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   133130654    66565296    7  HPFS/NTFS
/dev/sda2       268414020   388564154    60075067+  83  Linux
/dev/sda3       388564155   390716864     1076355   82  Linux swap / Solaris
/dev/sda4       133130655   268414019    67641682+   b  W95 FAT32

Partition table entries are not in disk order

```
I ran testdisk after this and it seemed to have kinda fixed the bootsector but killed grub, so i ran the SGD and got grub back. Tried to boot windows and it gets stuck on the disk check at:

```
Deleting an index entry from index $0 of file 25.
```

I hard booted from that, skipped the diskcheck and now I've gotten into my windows XP OS without any apparent issues. 
For the record I use it once in a blue moon for school projects when it calls for specialty software such as the adobe suite...

anyway, it's up and running for now. Thanks for everything. You're all my hero's :)

SOLVED... for now.

---

