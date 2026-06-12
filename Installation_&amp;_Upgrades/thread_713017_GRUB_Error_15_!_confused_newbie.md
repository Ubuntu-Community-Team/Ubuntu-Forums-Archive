---
title: "GRUB Error 15 ! confused newbie"
date: 2008-03-02
forum: Installation &amp; Upgrades
---

### Post by Sig88 on 2008-03-02
Well I have been trying to install ubuntu since friday and its not working, first I get error 17 but when I add /boot and previously had root and swap. So I resolved error 17 but now I get error 15 for some reason that I do not know.

And another thing can I do guided install to scsi1 not scsi4, because when I do guided install it just shows scsi4 and that doesnt work because its not the first hd and grub doesnt load on it.

hope this will be resolved, thanks.

---

### Post by Pumalite on 2008-03-02
If you can boot a Live CD, post:
sudo fdisk -lu
cat /boot/grub/menu.lst
[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)

---

### Post by Sig88 on 2008-03-02
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x08880888

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   476295119   238147528+  83  Linux
/dev/sda2       476295120   488392064     6048472+   5  Extended
/dev/sda5       476311185   479235014     1461915   82  Linux swap / Solaris
/dev/sda6       479235078   488392064     4578493+  83  Linux


Disk /dev/sdd (SGI disk label): 255 heads, 63 sectors, 30401 cylinders
Units = sectors of 1 * 512 bytes

----- partitions -----
Pt#    Device  Info     Start       End   Sectors  Id  System
 1: /dev/sdd1            4096 488396674 488392579   3  SGI raw
 9: /dev/sdd2               0      4095      4096   0  SGI volhdr
11: /dev/sdd3               0 488397167 488397168   6  SGI volume
----- Bootinfo -----
Bootfile: 
----- Directory Entries -----

Disk /dev/sdd9 (SGI disk label): 255 heads, 63 sectors, 0 cylinders
Units = sectors of 1 * 512 bytes

----- partitions -----
Pt#     Device  Info     Start       End   Sectors  Id  System
 1: /dev/sdd9p1            4096 488396674 488392579   3  SGI raw
 9: /dev/sdd9p2               0      4095      4096   0  SGI volhdr
11: /dev/sdd9p3               0 488397167 488397168   6  SGI volume
----- Bootinfo -----
Bootfile: 
----- Directory Entries -----

Disk /dev/sdd11 (SGI disk label): 255 heads, 63 sectors, 30401 cylinders
Units = sectors of 1 * 512 bytes

----- partitions -----
Pt#      Device  Info     Start       End   Sectors  Id  System
 1: /dev/sdd11p1            4096 488396674 488392579   3  SGI raw
 9: /dev/sdd11p2               0      4095      4096   0  SGI volhdr
11: /dev/sdd11p3               0 488397167 488397168   6  SGI volume
----- Bootinfo -----
Bootfile: 
----- Directory Entries -----

was i suppose to post this.
And I cant acces the /boot/grub/menu.lst

---

### Post by Pumalite on 2008-03-02
sudo mkdir /media/sda1
sudo mount -t ext3 /dev/sda1 /media/sda1
cat /media/sda1/boot/grub/menu.lst

---

### Post by Sig88 on 2008-03-02
cat mubuntu@ubuntu:~$ cat /media/sda1/boot/grub/menu.lst
cat: /media/sda1/boot/grub/menu.lst: No such file or directory

I just get this, man this sucks.

---

### Post by Pumalite on 2008-03-02
Did you make the directory? Did you mount the partition? Respect the spaces. Copy and paste the commands to your Terminal.

---

### Post by Sig88 on 2008-03-02
yeah the /media/sda1 file exists, but when I try to get to the grub menu it wont just says it doesnt exist so it probably didn't install correctly. 
You think I can fix this with that supergrub cd.

---

### Post by Pumalite on 2008-03-02
If menu.lst doesn't exist you didn't install right in the first place. You could try to boot Ubuntu with Super Grub just in case.

---

### Post by Sig88 on 2008-03-02
Where do I get SuperGrub. Cant seem to find it.

---

### Post by Pumalite on 2008-03-02
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

