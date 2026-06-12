---
title: "Can I create a new partition in front of a Windows partition without trouble?"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by Mortesins93 on 2010-10-25
Hello,
This is my partition table:
/dev/sda1               1        4255    34178256   83  Linux
/dev/sda2            4256        4437     1461915    5  Extended
/dev/sda3   *        4438        9964    44395627+   7  HPFS/NTFS
/dev/sda5            4256        4437     1461883+  82  Linux swap / Solaris

I would like to create a new partition to install Ubuntu 10.04 without touching Windows. Can I resize the first partition and create a new one? Should I move the first partition and the extended too? Is it risky? I don't want to do a clean install because I want to keep the Ubuntu which is in the first partition.
Hope you can help me.
Thanks in advance

---

### Post by srs5694 on 2010-10-25
If you resize /dev/sda1, you should be able to create a new primary /dev/sda4 without affecting Windows. Alternatively, you can resize /dev/sda1, expand the extended /dev/sda2 into the newly-freed space, and create a new logical /dev/sda6 on which to install the new Ubuntu. Both approaches should work, and in theory Windows shouldn't be bothered by this; however, Windows is sometimes touchy about disks. There's a chance you'll need to run a Windows recovery tool from CD/DVD to get it to boot again after such a change. If you don't resize the Windows partition, though, the odds of your needing to do this are low.

---

### Post by kansasnoob on 2010-10-25
I'd generally never move the beginning (left side in Gparted) of a Windows OS partition! It can mangle things boot wise.

Why have two threads about the same issue:

[http://ubuntuforums.org/showthread.php?t=1605485](http://ubuntuforums.org/showthread.php?t=1605485)

---

### Post by Mortesins93 on 2010-10-26
Sorry I tried deleting the other one but I guess it didn't work

---

### Post by Mortesins93 on 2010-10-26
This is the output of:
```
sudo parted /dev/sda print
```
```
Model: ATA Maxtor 6Y080L0 (scsi)
Disco /dev/sda: 82,0GB
Dimensione del settore (logica/fisica): 512B/512B
Tabella delle partizioni: msdos

Numero  Inizio  Fine    Dimensione  Tipo      File System  Flag 
 1      32,3kB  35,0GB  35,0GB      primary   ext3              
 2      35,0GB  36,5GB  1497MB      extended                    
 5      35,0GB  36,5GB  1497MB      logical   linux-swap        
 3      36,5GB  82,0GB  45,5GB      primary   ntfs         avvio

```

It is in Italian but I think you'll understand anyways.

---

