---
title: "How do you mount a SCSI in Edgy"
date: 2007-01-06
forum: Installation &amp; Upgrades
---

### Post by lift_test on 2007-01-06
How do you mount a second SCSI hard disk (first is ATA) in Edgy?  Previously mounted the disk in Dapper but after new Edgy install there doesn't seem to be a utility to do this.

I presume it can be done in a console but don't know where to start.

---

### Post by taurus on 2007-01-06
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by lift_test on 2007-01-06
Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2330    18715693+  83  Linux
/dev/hda2            2331        2434      835380    5  Extended
/dev/hda5            2331        2434      835348+  82  Linux swap / Solaris

Disk /dev/sda: 9100 MB, 9100044288 bytes
255 heads, 63 sectors/track, 1106 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1057     8490321   83  Linux
/dev/sda2            1058        1106      393592+   5  Extended
/dev/sda5            1058        1106      393561   82  Linux swap / Solaris
vic@TIME:~$

---

### Post by taurus on 2007-01-06
I assume you have another Linux distro running off /dev/sda!!!  

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
Scroll to the end and add these two lines to it.

```

/dev/sda1   /media/sda1   ext3   defaults   0   1
/dev/sda5   none   swap   sw   0   0

```
Save the changes.  Then, create a new mount point and mount it.

```
sudo mkdir /media/sda1
sudo mount -a
df -h  <--  should see /dev/sda1 on the list...
free <--  see your swap space increased...
```

---

### Post by lift_test on 2007-01-06
Thanks, took a while but got there in the end.  Must try and use the terminal window more, I can do the equivalent in win/dos but am not familiar with Linux command names.

---

### Post by taurus on 2007-01-06
As you can see, I am always a terminal man...  ;)   When I sit in front of a Linux machine (or even Unix), the first thing I look for is where to start a terminal.

---

