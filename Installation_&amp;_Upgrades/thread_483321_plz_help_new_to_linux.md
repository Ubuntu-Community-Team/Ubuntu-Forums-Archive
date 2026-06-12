---
title: "plz help new to linux"
date: 2007-06-24
forum: Installation &amp; Upgrades
---

### Post by Greensauce on 2007-06-24
Hey all, after being a long time Mac user i one day decided i should try windows after many years (and much pain) i feel i've become familiar enough with it to move on again to linux. Now here's my situation...

I have 2 HD's 160GB(master) OS is Vista Ultimate, and a 60GB(slave) i am trying to install Ubuntu 7.04 on. After i installed Ubuntu to my 60GB drive I restarted and got what appears to be the notorious Error 17 during start up. I have read through countless posts and tried many fixes to no avail. 

the post i paid most attention to was this one
[http://ubuntuforums.org/showthread.php?t=401531&page=2](http://ubuntuforums.org/showthread.php?t=401531&page=2)

and i tried most of them. But like i said i am new to linux and am not familiar with how everything works.

Any help would be greatly appreciated.

---

### Post by Greensauce on 2007-06-24
also plz keep everything as simple as possible I am just starting to learn codeing languages and am still a noob in that department

---

### Post by Pumalite on 2007-06-24
How did you partition?

---

### Post by Greensauce on 2007-06-24
the entire 60GB drive...the second choice on the install i believe i had the install wipe it clean and install completely to the 60GB drive

---

### Post by Greensauce on 2007-06-24
heres a copy of my fdisk -l if it helps (i have a 160GB external as well)

```
Disk /dev/hdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/hdd: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        6994    56179273+  83  Linux
/dev/hdd2            6995        7297     2433847+   5  Extended
/dev/hdd5            6995        7297     2433816   82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19457   156288321    c  W95 FAT32 (LBA)

```

---

### Post by Pumalite on 2007-06-24
You can try a couple of things:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

If none of that works; report back.

---

### Post by Greensauce on 2007-06-24
wow i went to the first link and tried that once i must've done it wrong it brought up the grub loader right after restart thanks appericiate it, i'm sure it wont be the last you hear from me :-D

---

