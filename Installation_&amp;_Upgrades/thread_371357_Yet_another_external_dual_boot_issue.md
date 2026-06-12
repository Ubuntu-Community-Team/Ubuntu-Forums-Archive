---
title: "Yet another external dual boot issue"
date: 2007-02-26
forum: Installation &amp; Upgrades
---

### Post by shawn524 on 2007-02-26
First off, sorry. 
This most likely has probably been answered, but for the life of me I can not find the proper documentation. I have scowered these forums searching for my answer but to no avail.

So here it gos:
I have a 160g internal HDD on my laptop that has vista installed on it. I thought to myself that it would be nice to have good 'ol ubuntu back, so I installed it to a 50g partition on an external 300g HDD.
Here comes the problem, GRUB wont boot anything anymore, all I can do is Live CD it. When I boot with the external HDD on and plugged in, i get error 21, and same when its off. When I try to boot straight from the external, i get error 17.

As always, any help at all is greatly appreciated.

---

### Post by confused57 on 2007-02-26
> **shawn524 said:**
> First off, sorry. 
This most likely has probably been answered, but for the life of me I can not find the proper documentation. I have scowered these forums searching for my answer but to no avail.

So here it gos:
I have a 160g internal HDD on my laptop that has vista installed on it. I thought to myself that it would be nice to have good 'ol ubuntu back, so I installed it to a 50g partition on an external 300g HDD.
Here comes the problem, GRUB wont boot anything anymore, all I can do is Live CD it. When I boot with the external HDD on and plugged in, i get error 21, and same when its off. When I try to boot straight from the external, i get error 17.

As always, any help at all is greatly appreciated.

Please post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

Did your errors occur immediately after installing Ubuntu or were you once able to boot after installing Ubuntu to your external drive?

---

### Post by shawn524 on 2007-02-26
Yea, the errors were immediate, i never got into ubuntu or vista.

Output of sudo fdisk -l:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       18557   149010907+   7  HPFS/NTFS
/dev/sda3           18558       18818     2096482+   f  W95 Ext'd (LBA)
/dev/sda4           18819       19457     5132767+  db  CP/M / CTOS / ...
/dev/sda5           18558       18818     2096451   dd  Unknown

Disk /dev/sdb: 300.0 GB, 300090727936 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30109   241849666    7  HPFS/NTFS
/dev/sdb2           30110       36356    50179027+  83  Linux
/dev/sdb3           36357       36483     1020127+  82  Linux swap / Solaris

---

### Post by confused57 on 2007-02-26
> **shawn524 said:**
> Yea, the errors were immediate, i never got into ubuntu or vista.

Output of sudo fdisk -l:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       18557   149010907+   7  HPFS/NTFS
/dev/sda3           18558       18818     2096482+   f  W95 Ext'd (LBA)
/dev/sda4           18819       19457     5132767+  db  CP/M / CTOS / ...
/dev/sda5           18558       18818     2096451   dd  Unknown

Disk /dev/sdb: 300.0 GB, 300090727936 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30109   241849666    7  HPFS/NTFS
/dev/sdb2           30110       36356    50179027+  83  Linux
/dev/sdb3           36357       36483     1020127+  82  Linux swap / Solaris

Here's some instructions I gave someone else who was having problems booting after installing Ubuntu to an external drive:
[http://www.ubuntuforums.org/showpost.php?p=2167867&postcount=49](http://www.ubuntuforums.org/showpost.php?p=2167867&postcount=49)

Basically, you'd need to install grub to your external hard drive mbr(using the live cd, set your bios to boot first to the internal hd), reboot,  then set bios to boot first to the external drive, highlight your Ubuntu entry in the grub menu, press "e" to edit, change the line with root to (hd0,1), then press "b" to boot...this change is temporary, but you can find out if it'll work.
You'd also need to repair your Vista mbr, so that you can boot Vista without the external drive connected...I don't know how this is done for Vista, I've read you can boot up the Vista install DVD & select a repair option, that allows you to restore the mbr.

If I'm reading your post correctly, you already have grub installed to the external drive mbr...can you boot Vista with the external drive disconnected?

---

### Post by shawn524 on 2007-02-26
Nope, cant boot when its doscinnected either.
Also, I havent been able to figure out how to do the fixmbr by booting up from vista. Its only an upgrade cd if that matters. The only think I could see remotely resembling the recovery console is the option to run a command prompt window, but fixmbr or /fixmbr does nothing there. 

Also, is my external HD hd0? Because when i install ubuntu, thats where it says to put it.

---

### Post by confused57 on 2007-02-26
> **shawn524 said:**
> Nope, cant boot when its doscinnected either.
Also, I havent been able to figure out how to do the fixmbr by booting up from vista. Its only an upgrade cd if that matters. The only think I could see remotely resembling the recovery console is the option to run a command prompt window, but fixmbr or /fixmbr does nothing there. 

Also, is my external HD hd0? Because when i install ubuntu, thats where it says to put it.
It looks like grub was installed to your Vista mbr, I'm not sure about repairing your mbr with the upgrade disk...if you want to boot into your OS, read back over my previous reply...this should get you where you "should" be able to boot, but you'd need to have your external drive connected to do so.

Installing grub from the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

If you're able to boot Ubuntu, you can add an entry to your /boot/grub/menu.lst to boot Windows, see this thread:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

Something like this:

title              Windows Vista
rootnoverify     (hd1,1)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

---

