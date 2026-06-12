---
title: "lost xp"
date: 2005-05-18
forum: Installation &amp; Upgrades
---

### Post by smb2004 on 2005-05-18
i know a question like this has been asked before, but im stuck.  i reinstalled ubuntu from 64bit to 32 cause of several problems and figured i would redo windows at the same time.  i did xp first, then ubuntu and now i can't boot to xp under grub.  my xp ntfs is hdb1 and my ext2 is hda2. 

**fdisk -l is:**

```

Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes


   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        6374    51199123+   6  FAT16
/dev/hda2   *        6375       24462   145291860   83  Linux
/dev/hda3           24463       24792     2650725    5  Extended
/dev/hda5           24463       24792     2650693+  82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        4864    39070048+   7  HPFS/NTFS


```
**and /boot/grub/menu/lst for xp is :**


```
title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
makeactive
chainloader	
```



when i try and go to doze i get an error saying partition not reconized or something similar.  any ideas?

---

### Post by testingubuntu on 2005-05-19
> **and /boot/grub/menu/lst for xp is :**


```
title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
makeactive
chainloader	
```


 Try adding this to your file 
> 
title	Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify	(hd1,0)
makeactive
chainloader +1

---

### Post by smb2004 on 2005-05-19
yup, that did it.  mind explaining what 'map' does?

---

### Post by davidmigl on 2005-05-28
Wow, that worked for me too!  Thanks so much! Mind explaining what "map" does?

---

### Post by wallijonn on 2005-05-29
[QUOTE=davidmigl]Mind explaining what "map" does?[/QUOTE]

[http://www.linux-mag.com/content/view/1518/2214/](http://www.linux-mag.com/content/view/1518/2214/) :

> Changing the Boot Disk

Some operating systems, such as DOS and Windows, must boot from the first physical disk in the computer. (Windows can actually store most of its files on another disk, but the C: partition on the first physical disk must still hold certain critical boot files.) Although this requirement isn't a problem for a single-OS installation or even for most installations with two or three OSs, as the number of OSs rise, the difficulty increases. This is particularly true when you want to boot multiple versions of DOS or Windows, because you'll soon run out of primary partitions on the first physical disk. Some boot managers allow you to store multiple versions of DOS or Windows on a single C: drive, but GRUB doesn't support this option.

One way around this problem is to make the computer believe the second or subsequent physical disk is in fact the first physical disk. You can pull off this trick using the map option.

The map command accepts two GRUB drive identifiers as parameters: the to-drive and the from-drive. Typically, you'll use this parameter to swap the first two physical disks, so you'll use two map commands, one to map the first physical disk as the second physical disk and the second to map the second physical disk to the first physical disk.

For instance, the following menu.lst or grub.conf entry boots Windows stored on the second partition on the second physical disk:

title Windows
  map (hd0) (hd1)
  map (hd1) (hd0)
  rootnoverify (hd1,1)
  makeactive
  chainloader +1
  boot

Note that the map command doesn't remap GRUB's own drive identifiers; the rootnoverify command still refers to the second physical disk as (hd1,1), not (hd0,1). You'd use the hd1 notation for other commands referring to this disk, too, such as hide or unhide.

Of course, to use this approach, you must first install the OS on the second physical disk. One way to do this is to physically reconfigure the drives for the installation process. That is, change the jumpers on your second drive so that it becomes the first drive, and either remove the first drive entirely or change its jumpers so that it becomes the second drive. After installing, you must then reverse your changes and set up GRUB to boot from the second physical disk. Another way to handle this problem is to create a special GRUB menu item to boot your OS installation medium while swapping drives.

For instance, to boot from an installation floppy disk, you might use the following entry:

title Floppy boot with drive swapping
  map (hd0) (hd1)
  map (hd1) (hd0)
  rootnoverify (fd0)
  chainloader +1
  boot

When you select this option from the GRUB menu, it redirects the boot process to the floppy disk, but the first and second drives will be swapped, at least from the BIOS's point of view. This should be enough to install OSs that rely upon the BIOS for drive access.

One limitation of drive swapping as implemented by GRUB is that it only affects the BIOS's view of drives. If an OS uses non-BIOS access methods, as all modern operating systems do, that operating system won't be affected by the GRUB-specified drive mapping.

Nonetheless, this technique can be useful in starting the boot process. In particular, the early stages of booting Windows rely upon the BIOS, so the mapping options can be useful in overcoming the first-drive requirements of Windows. Later in the boot process, when the more advanced Windows drivers take over disk access, you must rely on other techniques to ensure that drive letters are mapped appropriately. For instance, you can use the hide option to hide primary partitions from the true first physical disk that might be inappropriately mapped as the C: drive in Windows. (Logical partitions from the first physical disk should be mapped with drive letters of D: or above.)

Some older operating systems, such as DOS, rely exclusively upon the BIOS for handling drive access. Thus, the GRUB map options alone can be a handy way to install these OSs.

For instance, suppose you install three versions of Windows on three primary partitions on the first physical disk, but you also want to install DOS. The GRUB map option alone will allow you to install DOS on the second physical disk.

---

