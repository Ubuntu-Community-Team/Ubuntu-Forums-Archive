---
title: "Help with Install"
date: 2011-07-31
forum: Installation &amp; Upgrades
---

### Post by Prejudice182 on 2011-07-31
While installing Ubuntu, I picked to install the boot record onto the Windows 7(loader) option. Now when I try to boot back into Windows, it just keeps looping back to GRUB. Is there any way I can fix this? Any help without having to reinstall Windows would be appreciated.
[edit] Added sudo fdisk -l output[/edit]
[edit2]Pastebin of Bootinfoscript: [http://pastebin.com/6u6YSLTx](http://pastebin.com/6u6YSLTx)[/edit]

```
Disk /dev/sda: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x03c26d10

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156286976    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8fdec67d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2              13       97275   781250000    7  HPFS/NTFS
/dev/sdb3           97275      121602   195407873    5  Extended
/dev/sdb5           97275      109438    97703936   83  Linux
/dev/sdb6          109438      121602    97702912   82  Linux swap / Solaris
```

---

### Post by jpr0 on 2011-07-31
Did you try these steps? 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Quackers on 2011-08-01
According to the boot script output you have, at some time installed grub to the sdb1 partition. Consequently that partition now has a Boot Sector Type of "Grub2" whereas it should be "Windows Vista/7". Basically Windows can't find what it's looking for, so it will not boot.
The folder called "boot" needs to be removed from that partition BUT BE CAREFUL! as there will be 2 of them and the Windows one must remain untouched.
The "boot" you need to remove from the root of sdb1 has a folder in it called grub. 
The "Boot" that is a Windows folder has a file called "BCD" and BCD.Log and others in it. These must remain untouched.
Once this is removed you can try to boot Windows.

---

### Post by Prejudice182 on 2011-08-01
Thanks for the help, got it sorted with a Windows DVD though.

---

