---
title: "Please help, Resizing Ubuntu"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by kbm3 on 2008-11-08
Ok I am new here to the Ubuntu forums, and the linux community for that matter.  Now when I first installed Ubuntu on my hp laptop I did not partition enough space for linux.  So now I have tried shrinking my vista down to leave more room for Ubuntu.  I used a live CD to grow my existing partition on my linux box.  When it completed it said that it failed but it showed that the drive actually added the space.  Now when I start my ubuntu machine though I have no actual space left on the machine.  I grew it 20 gb more however.  I will say though that before I did all this i accidentally removed myself from the admin account and had to reenable through grub.  But I am receiving permission denied on many things however.  I do not know if this affected the grow.  Will somebody please help me to get my box running properly.

---

### Post by taurus on 2008-11-08
1.  Can you post a picture of gparted of your partition table from either LiveCD or from Ubuntu.  However, if you want to resize it, you have to do it from LiveCD.

2.  To see if you have root privilege, post the output of this command from a terminal.

Applications -> Accessories -> Terminal
```
id
```

---

### Post by kbm3 on 2008-11-08
Id contents:
uid=1000(kyle) gid=1000(kyle) groups=0(root),3(sys),4(adm),6(disk),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),27(sudo),29(audio),30(dip),44(video),46(plugdev),100(users),105(scanner),107(fuse),109(lpadmin),115(admin),1000(kyle),1002(vboxusers)

and as for the images the first one is my gparted and the second you can note the available space on the bottom left

---

### Post by taurus on 2008-11-08
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by kbm3 on 2008-11-08
```

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x57d857d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13854   111274856    7  HPFS/NTFS
/dev/sda2           22992       24321    10683225    7  HPFS/NTFS
/dev/sda3           13855       22497    69424897+  83  Linux
/dev/sda4           22506       22991     3903795   82  Linux swap / Solaris

Partition table entries are not in disk order

```

I have vista and ubuntu on my machine.

---

