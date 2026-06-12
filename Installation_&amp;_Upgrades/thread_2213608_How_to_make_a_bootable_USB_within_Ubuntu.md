---
title: "How to make a bootable USB within Ubuntu"
date: 2014-03-27
forum: Installation &amp; Upgrades
---

### Post by georgeward520-c on 2014-03-27
I'm trying to make a bootable USB for Xubuntu 13.10 in Ubuntu, but I dont know how. Unetbootin never picks up my USB when its connected, so thats out of the question. Any tips?

---

### Post by sudodus on 2014-03-27
Unetbootin should pick it up, if the drive is recognized by the system as a mass storage device **/dev/sdx**, where **x** is the device letter (a, b, ...)

Are you familiar with the command line? In that case, please post the output of the following command (when the USB drive is connected)

```
sudo parted -l     # 'space' 'minus' 'ell' at the end of the command line
```

Otherwise, try to identify the USB drive with the file browser.

---

### Post by georgeward520-c on 2014-03-27
Heres what the command line returns: Model: TDKMedia Trans-It Drive (scsi)
Disk /dev/sdb: 3997MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      31.7kB  3994MB  3994MB  primary  fat32        boot, lba

---

### Post by sudodus on 2014-03-27
That is good. The pendrive is recognized as **/dev/sdb**

```

Model: TDKMedia Trans-It Drive (scsi)
Disk /dev/sdb: 3997MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      31.7kB  3994MB  3994MB  primary  fat32        boot, lba

```

(The next time, please put such output (and commands too) within code tags. 'Go Advanced', mark the text and click on the # icon above the editng window.)

Anyway, Unetbootin should find the USB pendrive. At the bottom of the Unetbootin window, you should see

**Drive: /dev/sdb1**

at least if you start Unetbootin after inserting the pendrive.

---

### Post by sudodus on 2014-03-27
If you still have problems, I suggest that you use ***gparted*** to re-partition and re-format the pendrive.

---

### Post by georgeward520-c on 2014-03-27
What format should I use for the USB stick?
Edit: All sorted, now using Unetbootin to extract the .iso :) Thanks for the help!

---

### Post by sudodus on 2014-03-27
FAT32 (as it is now should be good).

But if you remove the partition and create a new one, it will start at another point (1 MB from the head of the drive instead of 31.7 kB).

---

