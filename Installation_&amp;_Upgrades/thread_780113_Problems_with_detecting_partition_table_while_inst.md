---
title: "Problems with detecting partition table while installation (8.04)"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by Andity on 2008-05-03
Hi all!

I have ubuntu 8.04 32-bit DVD.

After loading in LiveCD-mode for installation ubuntu, in install manager (and, also, in gparted) I can't see partitions table.
It's displayed only "/dev/sda". But partitions mount and work!

Configuration: notebook Dell Vostro 1400 with installed WinVista. Earlier, I installed mandriva 2008.1, but very soon, I deleted it (in vista recovery console recover loader and format partitions).
"Dell Media Direct" - special partition with something like crippled version of windows for watching dvd - was removed in vista's "Disk managment".

---

### Post by Pumalite on 2008-05-03
Post:
sudo fdisk -l

---

### Post by Andity on 2008-05-03
```
&#1044;&#1080;&#1089;&#1082; /dev/sda: 160.0 &#1043;&#1041;, 160041885696 &#1073;&#1072;&#1081;&#1090;
255 heads, 63 sectors/track, 19457 cylinders
Units = &#1094;&#1080;&#1083;&#1080;&#1085;&#1076;&#1088;&#1099; of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8000000

&#1059;&#1089;&#1090;&#1088;-&#1074;&#1086; &#1047;&#1072;&#1075;&#1088;     &#1053;&#1072;&#1095;&#1072;&#1083;&#1086;       &#1050;&#1086;&#1085;&#1077;&#1094;       &#1041;&#1083;&#1086;&#1082;&#1080;   Id  &#1057;&#1080;&#1089;&#1090;&#1077;&#1084;&#1072;
/dev/sda1               1          14      112423+  de  Dell Utility
/dev/sda2              15       19458   156176569    f  W95 &#1088;&#1072;&#1089;&#1096;&#1080;&#1088;. (LBA)
/dev/sda3   *        1320       19131   143069184    7  HPFS/NTFS
/dev/sda5              15        1320    10484736    7  HPFS/NTFS
```

---

### Post by Pumalite on 2008-05-03
If you are using Vista; you have to provide 'unallocatted' free space for Ubuntu with Vista partitioner first.

---

### Post by Andity on 2008-05-03
> **Pumalite said:**
> If you are using Vista; you have to provide 'unallocatted' free space for Ubuntu with Vista partitioner first.
done. but, same results(

---

### Post by Pumalite on 2008-05-03
People have done it:
[http://ubuntuforums.org/showthread.php?t=765097](http://ubuntuforums.org/showthread.php?t=765097)
Check your hardware.

---

### Post by PachmanP on 2008-05-03
gparted shows a blank drive?  
I had what sounds like a similar problem and I traced it back to overlapping partitions.  There is some similar bug reports for gparted.  
I fixed it by installing partition magic in windows (xp not vista though) and that did some error correction but then confused itself.  I was then able to go in with gparted and see the partitions and change things around/delete old non-NTFS partitions.  
Certainly not a sol'n for the faint of heart and I would suggest back up everything you want to save and a printout of the results of fdisk -l in case you need to rebuild the partitoin table.

---

### Post by Pumalite on 2008-05-03
> **Andity said:**
> done. but, same results(

Check your drive/Partition Table with TestDisk> 
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

### Post by scb147 on 2008-05-03
> **Pumalite said:**
> Check your drive/Partition Table with TestDisk> 
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)
Thank you very much! I was having this exact problem and TestDisk corrected it for me!

---

### Post by Pumalite on 2008-05-03
You are welcome. Good luck.

---

### Post by Andity on 2008-05-04
> Check your drive/Partition Table with TestDisk>
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

Problem was solved, but without this program - I'm reformat hdd already:)
Ubuntu installed successfully!

**Pumalite**, **scb147**,
thanks a lot for your help!

---

### Post by Pumalite on 2008-05-04
You are welcome. Good luck.

---

