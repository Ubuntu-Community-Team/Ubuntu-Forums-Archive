---
title: "What is this message at boot?"
date: 2010-03-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by foxmulder881 on 2010-03-02
Well I fixed my login prompt bug on the server this morning.

But I still have a weird message that appears upon boot. It's quick to appear and disappear so I can only post what I've been able to read.

```
inotify-add-watch udev ~ /dev/sda3 deviofailed <some text> missing <some text>
```

Now on /dev/sda3 I have Fedora 11 root system which is in a LVM. From what I can gather from the message, it's a simple warning stating that it can't read the drive location data. Probably because it's in LVM.

Am I correct? Should I be worried? :shock:

---

### Post by VMC on 2010-03-02
> **foxmulder881 said:**
> Well I fixed my login prompt bug on the server this morning.

But I still have a weird message that appears upon boot. It's quick to appear and disappear so I can only post what I've been able to read.

```
inotify-add-watch udev ~ /dev/sda3 deviofailed <some text> missing <some text>
```

Now on /dev/sda3 I have Fedora 11 root system which is in a LVM. From what I can gather from the message, it's a simple warning stating that it can't read the drive location data. Probably because it's in LVM.

Am I correct? Should I be worried? :shock:

Have you tried fsck'ing the LVM drive:
 fsck.ext3(or ext4) /dev/LV/lvol0

---

### Post by foxmulder881 on 2010-03-03
You mean run it from within Ubuntu or boot into Fedora and run it?

---

### Post by foxmulder881 on 2010-03-03
I tried running from within Fedora but got the "cannot check a mounted disk blah blah" message. Stupid me, I should have realized this beforehand,

So I run fsck in Ubuntu Server and got the message

```
fsck.LVM2_member: not found
```

The dumb thing is, it does exist. It's well and truly there because I boot into it. :)

---

### Post by VMC on 2010-03-03
> **foxmulder881 said:**
> I tried running from within Fedora but got the "cannot check a mounted disk blah blah" message. Stupid me, I should have realized this beforehand,

So I run fsck in Ubuntu Server and got the message

```
fsck.LVM2_member: not found
```

The dumb thing is, it does exist. It's well and truly there because I boot into it. :)

Output your drive listings:

```
sudo fdisk -l
```

---

### Post by foxmulder881 on 2010-03-03
It's not from fdisk but I hope this helps.

[IMG]http://img51.imageshack.us/img51/31/screenshot342010113509a.jpg[/IMG]

---

### Post by VMC on 2010-03-03
I'm not sure what that printout is, but if its gparted, then let it do a check you LVM partitions.

I don't have LVM. Haven't installed it in years. I'm not sure how fsck works on LVM either.

---

### Post by foxmulder881 on 2010-03-04
Here's the fdisk printout:

```
[root@localhost chris]# fdisk -l /dev/sda

Disk /dev/sda: 163.9 GB, 163927522816 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x70855789

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9964    80035798+   7  HPFS/NTFS
/dev/sda2   *        9965        9990      204800   83  Linux
/dev/sda3            9990       19929    79839062+  8e  Linux LVM
[root@localhost chris]# fdisk -l /dev/sdb

Disk /dev/sdb: 80.0 GB, 80025280000 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1c789987

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9557    76766571   83  Linux
/dev/sdb2            9558        9729     1381590    5  Extended
/dev/sdb5            9558        9729     1381558+  82  Linux swap / Solaris
[root@localhost chris]# fdisk -l /dev/sdc

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002f925

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38913   312568641    7  HPFS/NTFS
```

---

### Post by VMC on 2010-03-04
Have you tried the simple 'sudo fsck /dev/sda3' to see if its clean?

---

### Post by foxmulder881 on 2010-03-04
> **VMC said:**
> Have you tried the simple 'sudo fsck /dev/sda3' to see if its clean?

Yep, it's clean.

---

