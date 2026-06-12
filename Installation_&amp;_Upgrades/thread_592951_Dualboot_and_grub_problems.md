---
title: "Dualboot and grub problems"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by FnTm on 2007-10-26
HI all! I finally got through my Problems, formated my HDD and istalled Gutsy.

So now I have:  2x40gb HDDs with Windows on them (installed first) and a 250gb HDD with ubuntu on it.

So now when I installed ubuntu, I cant seem to boot to windows any more. Its just not showing in grub menu. 

Maybe this is fairly common, but I couldnt seem to find answers anywhere.

Thanks
FnTm

---

### Post by Pumalite on 2007-10-26
You have to edit your menu.lst and add the 2 Windows to it, after memtest.

---

### Post by billrad1 on 2007-10-26
title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1 (hd1) (hd0)

### END DEBIAN AUTOMAGIC KERNELS LIST

this is what works for me

Bill

---

### Post by Pumalite on 2007-10-26
[http://www.linuxforums.org/forum/installation/56461-grub-menu-lst-chainloader-help-needed.html](http://www.linuxforums.org/forum/installation/56461-grub-menu-lst-chainloader-help-needed.html)

---

### Post by FnTm on 2007-10-26
Did as billrad1 said, but when I tried to boot to it, it showed: Wrong file type, or invalid file. Something like that. So still stuck. Going to sleep... maybe will be wiser in the morning.

---

### Post by Pumalite on 2007-10-26
Your Windows is probably (hd0,0)

---

### Post by FnTm on 2007-10-30
Uhm... it still isnt working.  Heres my setup:

title Windows XP
root (hd0,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 


Maybe ive got some mistakes in there?

---

### Post by harvey186 on 2007-10-30
Hi, I'm using the following lines and it works. I have 2 IDE drives and one sata raid. my Windows is on the raid. In the bios the raif is the second drive.

title Windows Loader
rootnoverify (hd0,0)
makeactive
chainloader +1
map (hd0) (hd1)
map (hd1) (hd0)

---

### Post by FnTm on 2007-10-30
How long is it supposed to take, before it starts to boot? Because nothing happens for like 5 minutes, and then i just reboot it... kinda confused here. Would really like to get to my Win files too.

---

### Post by meierfra on 2007-10-31
Post your menu.lst and the output of "sudo fdisk -l" .

---

### Post by NJC on 2007-10-31
> **FnTm said:**
> Uhm... it still isnt working.  Heres my setup:

title Windows XP
root (hd0,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 



Have you tried "rootnoverify" instead of "root"?

> Use the command 'root' if you are booting a Windows version with the FAT32 filesystem such as Windows 95, Windows 98, Windows ME, or Windows XP Home Edition. 

Use the command 'rootnoverify if you aren't sure, or if you are booting a Windows system that has the NTFS filesystem. Windows XP Home Edition, Windows XP Professional, WIndows NT and Windows 2000. 


[http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_the_simple_way](http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_the_simple_way)

---

### Post by FnTm on 2007-10-31
Fdisk:
```

Disk /dev/sda: 40.0 GB, 40018599936 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xee29ee29

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40018599936 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe5a91019

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       29645   238123431   83  Linux
/dev/sdc2           29646       30401     6072570    5  Extended
/dev/sdc5           29646       30401     6072538+  82  Linux swap / Solaris

Disk /dev/dm-0: 80.0 GB, 80031776768 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xee29ee29

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-0p1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/dm-1: 80.0 GB, 80015491584 bytes
255 heads, 63 sectors/track, 9727 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69205244

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/dm-1p1   ?       13578      119522   850995205   72  Unknown
Partition 1 does not end on cylinder boundary.
/dev/dm-1p2   ?       45382       79243   271987362   74  Unknown
Partition 2 does not end on cylinder boundary.
/dev/dm-1p3   ?       10499       10499           0   65  Novell Netware 386
Partition 3 does not end on cylinder boundary.
/dev/dm-1p4          167628      167631       25817+   0  Empty
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
```

Menu.lst
```
## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f0bcb067-d22f-4a3d-9370-f6dcbe9ce213 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f0bcb067-d22f-4a3d-9370-f6dcbe9ce213 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet

title Windows Loader
rootnoverify (hd0,0)
makeactive
chainloader +1
map (hd0) (hd1)
map (hd1) (hd0)


### END DEBIAN AUTOMAGIC KERNELS LIST
```

ive got a question.

Could it be because, i have not mounted my partition, so that linux could access it? Because curently I cant do that.

---

### Post by uidb4056 on 2007-10-31
I've a dual boot with XP on hd0,0 formatted as NTFS and Gutsy on hd1,3. My config in menu.lst is for Windows:

title                Microsoft Windows XP Professional
root               (hd0,0)
savedefault
makeactive
chainloader    +1

I thing you can have problems with the map you put at the end and/or rootnoverify

---

### Post by Pumalite on 2007-10-31
Check your UUID's
Compare the output of
blkid
with:
cat /etc/fstab
Make the changes necessary if any.

---

### Post by FnTm on 2007-10-31
Is this right?
```
/dev/sdc1: UUID="f0bcb067-d22f-4a3d-9370-f6dcbe9ce213" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc5: UUID="9e467345-150d-4eab-96e6-ba826cf69006" TYPE="swap" 
fntm@fntm-ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdc1
UUID=f0bcb067-d22f-4a3d-9370-f6dcbe9ce213 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdc5
UUID=9e467345-150d-4eab-96e6-ba826cf69006 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

---

