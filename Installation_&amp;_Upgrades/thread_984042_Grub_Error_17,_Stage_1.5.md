---
title: "Grub Error 17, Stage 1.5"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by loonyjuice on 2008-11-15
I too am having the same problem, and so far nothing I have done, even re-installing from the live cd will make my error 17 go away! Please can someone help?

I suspect it's to do with the drive order or something, but I don't know, and I'm a noob.

fdisk -l gives:
[I]
fdisk ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001e7cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xecebeceb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36483   293049666    7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00006144

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       18705   150247881   83  Linux
/dev/sdc2           18706       19457     6040440    5  Extended
/dev/sdc5           18706       19457     6040408+  82  Linux swap / Solaris

Disk /dev/sdd: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001a79d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       36483   293049666   83  Linux

Disk /dev/sde: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa711ef95

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       10011    80413326   83  Linux[/I]

Ubuntu is/should be installed on my 160 GB drive /dev/sdc1

/boot/grub/menu.lst gives

[I]title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ac73d324-9fe5-48e2-b62d-1ff1da62e7a4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ac73d324-9fe5-48e2-b62d-1ff1da62e7a4 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd2,0)
kernel		/boot/memtest86+.bin
quiet[/I]

and device.map gives:
[I]ubuntu@ubuntu:/media/disk/boot/grub$ cat device.map 
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
(hd3)	/dev/sdd
(hd4)	/dev/sde[/I]

This all came about from upgrading to intrepid. When I restarted it came up with grub error 17! If I re-install it makes no difference. However, if i remove all the other drives, other than my 160GB disk, and then install ubuntu it will work. How can I over come this problem?

Many thanks in advance,

M.

---

### Post by caljohnsmith on 2008-11-15
> **loonyjuice said:**
> 

This all came about from upgrading to intrepid. When I restarted it came up with grub error 17! If I re-install it makes no difference. However, if i remove all the other drives, other than my 160GB disk, and then install ubuntu it will work. How can I over come this problem?

Many thanks in advance,

M.
Do you get the Grub error 17 before you see the Grub menu on start up, or after you get the Grub menu and select to boot Ubuntu? Do you know which drive you are booting on start up? It looks like you might be booting the sda drive. And if you are not all ready booting your Ubuntu sdc drive, can you set your BIOS to boot the sdc drive on start up? 

How about also posting:
```
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdc count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
sudo dd if=/dev/sdc bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
```
And we can work from there.

---

### Post by loonyjuice on 2008-11-15
Hi, thanks for your reply. 

I get the error before any grub menu. I don't think i can change the drive order in the bios, besides this was working before. I suspect the boot sector is in /dev/sda1, but it should be set to point to /dev/sdc1. I have tried setting grub to do this manually, by setting root (hd2,0), i think!

Printouts from the commands you mentioned are as follows:

ubuntu@ubuntu:/media/disk/boot/grub$ sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB 
ubuntu@ubuntu:/media/disk/boot/grub$ sudo dd if=/dev/sdc count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB 
ubuntu@ubuntu:/media/disk/boot/grub$ sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
8200

ubuntu@ubuntu:/media/disk/boot/grub$ sudo dd if=/dev/sdc bs=1 skip=1049 count=2 2>/dev/null | hexdump | awk '{print $2}'
ff00

means little to me.

Thanks,

M.

---

### Post by caljohnsmith on 2008-11-15
OK, according to those commands, Grub is installed to the MBR of both sda and sdc, and the sda drive points to the 3rd BIOS boot drive for Grub's boot files, which might be the problem since we don't know which drive sdc is in the BIOS boot order. How about doing:
```
sudo grub
grub> device (hd1) /dev/sdc
grub> device (hd0) /dev/sda
grub> root (hd1,0)
grub> setup (hd0)
```
That will point the Grub in the MBR of sda to the 2nd drive in the BIOS boot order, rather than the 3rd. Give that a shot and let me know if it works. If it doesn't, there are two more possibilities to try, because as I mentioned, we don't know where sdc is in the BIOS boot order.

---

### Post by loonyjuice on 2008-11-15
Ok, I entered the commands you mention, and I think I understand what you're saying, but I now get error 15, which I believe is file not found?

Back in the live cd, the /boot/grub/device.map still has /dev/sdc1 as hd2, though. Did it not work or do I misunderstand?

Thanks,

M.

---

### Post by caljohnsmith on 2008-11-15
> **loonyjuice said:**
> Ok, I entered the commands you mention, and I think I understand what you're saying, but I now get error 15, which I believe is file not found?

Back in the live cd, the /boot/grub/device.map still has /dev/sdc1 as hd2, though. Did it not work or do I misunderstand?

Thanks,

M.
Fortunately you don't have to worry about the device.map file at this point, because that is only used on start up if the menu.lst has references to /dev/sdX drives; if you aren't even getting a Grub menu yet, it won't help to change that file. But that Grub error 15 most likely means that the sdc drive must not be 2nd in the BIOS boot order, so next try:
```
sudo grub
grub> device (hd3) /dev/sdc
grub> device (hd0) /dev/sda
grub> root (hd3,0)
grub> setup (hd0)
```
And let me know how that goes.

---

### Post by loonyjuice on 2008-11-15
Thanks for your help so far, but I"m gonna call it a day and head out to the pub for a bit, to de-stress and reflect.

I'll continue this tomorrow.

Thanks,

M.

---

### Post by bapoumba on 2008-11-16
Moved this particular issue to its own thread.

---

