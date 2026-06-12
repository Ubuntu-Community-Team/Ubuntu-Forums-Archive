---
title: "multi partitions/disks/Operating Systems - Grub Problem"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by darbid on 2008-07-10
I am an informed beginner.  (that means I have learnt enought to get me into this much trouble)

Problem - When I have an USB turned on at boot I get at Grub 1.5 an error 25.

here is a fdisk -l with the USB turned on at boot using the Ubuntu live up DVD.

```
 Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4334    34812823+   7  HPFS/NTFS
/dev/sda2            4335       19457   121475497+   5  Extended
/dev/sda3   *        6247        8621    19077187+  af  Unknown
/dev/sda5   *        4335        6246    15358108+  af  Unknown
/dev/sda6            8622       19457    87040138+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2eb3ee57

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        1276       36957   286615665    7  HPFS/NTFS
/dev/sdb2           36958       38913    15711570   af  Unknown
/dev/sdb3            1047        1275     1839442+   5  Extended
/dev/sdb4               1        1046     8401963+  83  Linux
/dev/sdb5            1047        1275     1839411   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d801451

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       16971   136319525+   7  HPFS/NTFS
/dev/sdc2           16972       18282    10530607+  af  Unknown
/dev/sdc3           18283       19457     9438187+   5  Extended
/dev/sdc5   *       18283       19457     9438156   af  Unknown
```

I have no idea how I got so many partitions.  Only with fdisk do i see all these.  Even in Acronis I do not see all these.

Basically 

sda1 is Vista
sda3 is OSX (one version)
sdb4 is Ubuntu
sdb2 is OSX

And I am not sure yet but 
sdc5 is most likely another OSX :-)

Other than I played around with a boot manager program in Vista which now starts after Grub if no USB is plugged in then it works.

here is the menu.1st bit

```
title		Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		OSX
root		(hd0,2)
savedefault
makeactive
chainloader	+1

title		Ubuntu
root		(hd1,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=10278edc-b934-4249-aa3f-fcc402f80380 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		OSX
root		(hd1,1)
savedefault
makeactive
chainloader	+1

title		LEO
root		(hd2,1)
savedefault
makeactive
chainloader	+1
```

The last LEO here does not work cause that would be an USB but as I cannot have it in at boot I cannot boot into it.

I have done a bit of reading and think that the problem is that Linux and thus grub is on the second disk.

I have tried the following;

from Ubuntu i did grub-install /dev/sda

from the Ubuntu live I tried
linux-rescue
chroot /mnt/sysimage 
grub-install /dev/sda
exit

but i got a message at the beginning that linux rescue was not installed

I did try the fake ubuntu install but only install grub, but I got scared and got to the install button and could not find the install grub bit.

What I think I want is to have a boot flag next to VISTA to keep it happy.  And to install GRUB again into the MBR overwriting what is there.

Could anyone please sort me out please.

---

### Post by matthewbpt on 2008-07-10
I dont know what the problem is but according to the Grub Manual ([http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors](http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors)) error 25 means:

> 25 : Disk read error
    This error is returned if there is a disk read error when trying to probe or read data from a particular disk. 

Maybe reading some more of the manual can give you an idea of what is causing the problem.

---

### Post by darbid on 2008-07-10
Yep thanks been there and know this 

22 : No such partition
    This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk. 

But why.  The only thing that I have read is that when an USB is present then it becomes HD0/sda1 but from the Ubuntu Live boot that does not appear to be the case.

Since my first post I have been able to remove the boot flags from the USB but that has not helped.

---

### Post by darbid on 2008-07-11
There are not many options in this BIOS but i have noticed something strange

With no USB plugged in the bios information lists my two internal drives (i am on a laptop) but in the boot list section it only lists the CD/DVD and then the first hard drive.

WITH THE USB PLUGGED IN

The information section is the same.
But in the boot list it now lists as a possibility the USB drive.

---

### Post by darbid on 2008-07-15
Ok final go - then I will just open my favourite email client and send myself an email.

So I have worked out that when a USB is connected at BIOS stage it takes over as HD1.  

So in Grub is there another way of naming the partitions.

---

