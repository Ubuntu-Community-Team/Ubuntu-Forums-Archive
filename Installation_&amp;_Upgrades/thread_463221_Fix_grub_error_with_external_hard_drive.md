---
title: "Fix grub error with external hard drive?"
date: 2007-06-03
forum: Installation &amp; Upgrades
---

### Post by miggols99 on 2007-06-03
I've been installing various linux distos, and I installed them succesfully onto an external hard drive. But if I turn the external hard drive off, grub produces an error (22?) which I guess means it can't find the grub. Can I remove the grub on the external hard drive (by deleting the grub folder?) and make my computer use the grub on the internal hard drive?

---

### Post by miggols99 on 2007-06-04
Anyone?

---

### Post by confused57 on 2007-06-04
Boot into Ubuntu(your install or a live cd), open a terminal, post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

This info is needed  before someone can offer a solution...have your external drive connected when you run the command.

---

### Post by miggols99 on 2007-06-04
Ok, here's the output of sudo fdisk -l
```
Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17340   139282173+   7  HPFS/NTFS
/dev/sda3           17341       30394   104856255    5  Extended
/dev/sda5           17341       20509    25454929+  83  Linux
/dev/sda6           20510       30235    78124063+  83  Linux
/dev/sda7           30236       30394     1277136   82  Linux swap / Solaris

Disk /dev/sdg: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       30401   244196001    5  Extended
/dev/sdg5               1        1912    15358077   83  Linux
/dev/sdg6            1913       30401   228837861   83  Linux

```I've got three partitions for each, one for /, one for /home and one for swap, but no swap for the second (external).

---

### Post by confused57 on 2007-06-04
I believe what you need to do is use the live cd & install your internal hard drive Linux distro's grub to the internal drive mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

"find /boot/grub/stage1" should return several root partitions, you'd use something like:
root (hd0,4)
setup (hd0)

the link explains it pretty well...you can add configfile entries to your menu.lst to boot the OS on your external drive:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

---

### Post by miggols99 on 2007-06-04
Thanks! That looks like it will work ok. :D

---

