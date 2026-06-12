---
title: "Hello - got a bootloader question - dual boot"
date: 2005-08-09
forum: Installation &amp; Upgrades
---

### Post by muychingon on 2005-08-09
Hello everyone. I'm new here.  I just got Ubuntu installed and I really like what I see so far. I am however having one small issue... 

I can't boot back into my Windows box.  For some reason Grub didn't pick up my previous installation of Windows and keep it as a boot option so now when I start my pc I only get the options to boot Ubuntu default, recovery or memory test. 

I have 2 drives /hda and /hdb  

/hda - has ubuntu (was blank before)
/hdb - has windows (taking the entire drive).

I didnt find a "grub.conf" file to my surprise, but i found menu.1st which seemed to be the file to edit to correct the problem.

I'm not sure how to manually add the windows partition, I tried this:

```
title         Windows XP
rootnoverify  (hd1,0)
makeactive
chainloader   +1
boot
``` 

```

title         Windows XP
root  (hd1,0)
makeactive
chainloader   +1
```

I also tried making the disk (hd1,1) for the first partition and that didnt work either.  The other setups don't work... I'm not sure how to set this up. My Windows install takes up my entire second drive (hdb).

fstab
```
root@ubuntu:~ # cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
``` 

fdisk -l
```
root@ubuntu:~ # fdisk -l

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14263   114567516   83  Linux
/dev/hda2           14264       14593     2650725    5  Extended
/dev/hda5           14264       14593     2650693+  82  Linux swap / Solaris

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14592   117210208+   7  HPFS/NTFS
```

device.map
```
root@ubuntu:/boot/grub # cat device.map
(hd0)   /dev/hda
(hd1)   /dev/hdb
``` 

Any help you can provide will be great.

thanks.

---

### Post by odin on 2005-08-09
title           windows XP
root            (hd1,0)
savedefault
makeactive
chainloader     +1

I have (as you can see) the same situation and everything works fine.The only difference I can see betwen my menu.lst and your is the line after "root(hd1,0)"(the "savedefault")the rest looks like one of the things you tried so,I dont know try that.If it  works I cant tell you why but at least you got what you wanted.  ;-)

---

### Post by muychingon on 2005-08-10
> title windows XP
root (hd1,0)
savedefault
makeactive
chainloader +1 

That didn't do it either. 

Does anybody else have any suggestions? is there more information I can post here to help you help me?

I'd hate to do a fixmbr from the windows recovery mode... I like Ubuntu :)

---

### Post by muychingon on 2005-08-10
Doing some digging around i found this:

> 7.4.1.3. Changing the Hard Disk Sequence

Some operating systems, such as Windows, can only start from the first hard disk. If you have such an operating system installed on a different hard disk, you can implement a logical change for the respective menu entry. However, this only works if the operating system accesses the hard disks by way of the BIOS when booting.

...
title windows
   map (hd0) (hd1)
   map (hd1) (hd0)
   chainloader(hd1,0)+1
...

In this example, Windows is started from the second hard disk. For this purpose, the logical sequence of the hard disks is changed with map. This change does not affect the logic within the GRUB menu file. You still need to specify the second hard disk for chainloader. 

in here: [http://www.novell.com/documentation/suse91/suselinux-adminguide/html/ch07s04.html](http://www.novell.com/documentation/suse91/suselinux-adminguide/html/ch07s04.html)

Can someone explain what this is doing... I'm not sure what that means. And whether you think this will fix the problem I'm having.

---

### Post by al7kz on 2005-08-10
Hi,

Edit menu.lst:

$ sudo gedit /boot/grub/menu.lst

Change windoze entry to:

title windoze
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

---

