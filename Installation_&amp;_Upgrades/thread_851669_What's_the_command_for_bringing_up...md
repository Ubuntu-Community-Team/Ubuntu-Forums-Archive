---
title: "What's the command for bringing up.."
date: 2008-07-06
forum: Installation &amp; Upgrades
---

### Post by buccaneere on 2008-07-06
... the location of other OS's on other hard disks that I've added to my desktop box?

I plugged in two other HD's to my desktop - one with XP, and another with PCLinuxOS, and I want to import those respective grub loaders from those 2 disks into the Ubuntu Grub loader.

The XP disk is already dual boot w/an older ubuntu version; what difference does that make?




Thanks...

---

### Post by Pumalite on 2008-07-06
sudo fdisk -lu
will give you the location of other drives/partitions/OS's
gksudo /boot/gru/menu.lst
will let incorporate the rest of the OS's

---

### Post by buccaneere on 2008-07-06
> **Pumalite said:**
> sudo fdisk -lu
will give you the location of other drives/partitions/OS's
gksudo /boot/gru/menu.lst
will let incorporate the rest of the OS's

Thanks! 


On it......

---

### Post by buccaneere on 2008-07-10
I've done something wrong... The additions appear in the grub menu, but will not load. They will load if the IDE cable is switched directly to the respective disks.

Help?

---

### Post by SkonesMickLoud on 2008-07-10
> **buccaneere said:**
> I've done something wrong... The additions appear in the grub menu, but will not load. They will load if the IDE cable is switched directly to the respective disks.

Help?

Sounds like you have the

```
root (hdx,x)
```

line messed up somehow.

Grub names disks and partitions starting at zero, meaning that sda1 would be (hd0,0) while sda2 would be (hd0,1) etc.  If you have more than one disk, it could look something like (hd1,0).  That is the first partition on the second disk.

Make sure the entries for your different operating systems point to the disk/partition they are actually installed to.

---

### Post by buccaneere on 2008-07-12
> **SkonesMickLoud said:**
> 

Make sure the entries for your different operating systems point to the disk/partition they are actually installed to.

Sounds great skones!

Now... What's the command for bringing up ... the location of other OS's on other hard disks that I've added to my desktop box?

Specifically - the boot loader/partition for those other OS's? Does that value show as a return for the command that puma gave me?




Wow - we just did a do loop!

---

### Post by SkonesMickLoud on 2008-07-12
> **buccaneere said:**
> Does that value show as a return for the command that puma gave me?

Yes, but it takes a little bit of decoding.

Can you post the output of:

```
sudo fdisk -l
```

(that's a lowercase 'L' by the by)

and:

```
cat /etc/fstab
```

---

### Post by buccaneere on 2008-07-12
> chucknb@chucknb-desktop:~$ sudo fdisk [l
[sudo] password for chucknb: 

Unable to open [l  [COLOR="Red"]***[oops]***[/COLOR]
chucknb@chucknb-desktop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00045b5c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1019     8185086   83  Linux
/dev/sda2            1020        9729    69963075    5  Extended
/dev/sda5            1020        1528     4088511   82  Linux swap / Solaris
/dev/sda6            1529        9729    65874501   83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00022288

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          25      200781   83  Linux
/dev/sdb2              26        4828    38580097+  8e  Linux LVM
/dev/sdb3   *        4829        9522    37704555   83  Linux
/dev/sdb4            9523        9729     1662727+   5  Extended
/dev/sdb5            9523        9729     1662696   82  Linux swap / Solaris

Disk /dev/sdc: 30.7 GB, 30735581184 bytes
255 heads, 63 sectors/track, 3736 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006ca0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        3736    30009388+   7  HPFS/NTFS
chucknb@chucknb-desktop:~$ 
 

Here's the fstab file contents. What does this tell me?

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc3
UUID=601da4e5-6554-48d0-bdc7-c43ddcc5f4d3 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdc5
UUID=8c6fe35a-c295-4fca-a885-c13032ca4d0f none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0



Thanks for gettin' back on that...

---

### Post by Pumalite on 2008-07-13
Post:
sudo blkid

---

### Post by buccaneere on 2008-07-13
return...

> chucknb@chucknb-desktop:~$ sudo blkid
[sudo] password for chucknb: 
/dev/sda1: UUID="33fc5dbf-e701-43c8-be79-1cfe25c90477" SEC_TYPE="ext2" TYPE="ext3" 

/dev/sda5: TYPE="swap" UUID="e69e1ed4-0fe7-40ac-a67e-5c7141d09571" 

/dev/sdb1: LABEL="/boot" UUID="ff30e74c-36d1-417e-8ff1-c7af6e46b93a" TYPE="ext3" SEC_TYPE="ext2" 

/dev/sdb2: UUID="72399921-3d5b-44e0-b4d5-947e04fb9933" SEC_TYPE="ext2" TYPE="ext3" 

/dev/sdb3: UUID="601da4e5-6554-48d0-bdc7-c43ddcc5f4d3" TYPE="ext3" 

/dev/sdb5: TYPE="swap" UUID="8c6fe35a-c295-4fca-a885-c13032ca4d0f" 

/dev/sdc1: UUID="2030A6DF30A6BAE4" TYPE="ntfs" 

/dev/sda6: UUID="782f3117-89cb-4238-a40d-53e994531958" SEC_TYPE="ext2" TYPE="ext3" 

chucknb@chucknb-desktop:~$ 

---

### Post by Pumalite on 2008-07-13
I would try:

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sdb3
UUID=601da4e5-6554-48d0-bdc7-c43ddcc5f4d3 / ext3 defaults,errors=remount-ro 0 1
# /dev/sdb5
UUID=8c6fe35a-c295-4fca-a885-c13032ca4d0f none swap sw 0 0
/dev/hdb /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
/dev/hda /media/cdrom1 udf,iso9660 user,noauto,exec 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0

---

### Post by buccaneere on 2008-07-13
Thanks again there puma..

What am I changin' there? If it doesn't work, will I be able to revert without a meltdown?

I like knowin' what I'm doin' before I do it - that way I might learn a fix to apply to other processes, AND, help others at the same time...

---

### Post by Pumalite on 2008-07-13
You are changing fstab to correspond with menu.lst, fdisk and blkid
The kernel checks fstab at boot. If it doesnt work; you can change it back.

---

### Post by buccaneere on 2008-07-13
Well, something changed...

After GRUB, XP is 'starting up'. And that's as far as that goes. PCLinuxOS option returns 'invalid executable file (or something of the like)'; press any key to continue'.

Any other ideas what I've got wrong?

---

### Post by Pumalite on 2008-07-13
Get Super Grub and see if it can boot your OS's:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)
Burn to disk and boot from it.

---

