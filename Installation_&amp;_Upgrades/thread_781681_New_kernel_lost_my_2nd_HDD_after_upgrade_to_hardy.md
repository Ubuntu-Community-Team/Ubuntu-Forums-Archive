---
title: "New kernel lost my 2nd HDD after upgrade to hardy"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by dobuntu on 2008-05-04
Hello,

I have a Pentium III 866 with 768MB RAM and 2 IDE HDDs (WD 80 and 320 GB).
I have ran Ubuntu on this machine since version 6.10.

After upgrading from 7.10 to 8.04 the new kernel (2.6.24-16-generic) **doesn't recognize** my 2nd hard disk which hosts my **/home** partition.

The **old kernel** (2.6.22-14-generic) works fine.

No trace of my 2nd HD can be found in **/dev/disk** nor in the output of the command
```
fdisk -l
```
which only lists my first drive's partitions.
```
root@mizar:~# fdisk -l

Disco /dev/sda: 80.0 GB, 80026361856 byte
255 heads, 63 sectors/track, 9729 cylinders
Units = cilindri of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe6cef0bc

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6235    50082606   83  Linux
/dev/sda2            6367        6464      787185   82  Linux swap / Solaris
/dev/sda3            6465        9729    26226112+  83  Linux
/dev/sda4            6236        6366     1052257+  83  Linux

Le voci nella tabella delle partizioni non sono nello stesso ordine del disco

```

With the new kernel I can only log in as root (since the /root partition is on my first HD).

To log in as a **normal user** I must boot the old (gutsy) kernel.

Some weeks ago one of my HD drives (the one with Windows on) got broken so I bought the new 320GB HD, and I definitely got rid of Windows on my PC. **All of my documents are now on my Ubuntu /home directory!**

PLEASE HELP!!!

---

