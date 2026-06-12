---
title: "install to external hard drive grub broken"
date: 2007-07-25
forum: Installation &amp; Upgrades
---

### Post by android6011 on 2007-07-25
I followed [http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)  and changed the menu.lst as directed, but when I try to load ubuntu at the grub menu, I get

Error 17 : Cannot mount selected partition

what is wrong?

---

### Post by confused57 on 2007-07-25
> **android6011 said:**
> I followed [http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)  and changed the menu.lst as directed, but when I try to load ubuntu at the grub menu, I get

Error 17 : Cannot mount selected partition

what is wrong?

You might want to post the output of:
```
sudo fdisk -l
```
-l is a small "L"
you can do this from the Ubuntu live cd

---

### Post by android6011 on 2007-07-25
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5193    41712741    7  HPFS/NTFS
/dev/sda2            5376        9729    34973505   83  Linux
/dev/sda3            5194        5375     1461915   82  Linux swap / 
Solaris

Partition table entries are not in disk order

------menu.lst-------
 ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=abde7e45-5149-4e3d-bb13-3188f7d05e2b ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=abde7e45-5149-4e3d-bb13-3188f7d05e2b ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
chainloader	+1


I tried replacing the UUID with just root=/dev/sda2 but that did not work, i had the same problem, I also cannot load windows. I get an error saying NTLDR is missing, but if i make my internal harddrive boot first, windows is fine.

---

### Post by confused57 on 2007-07-25
It looks like Ubuntu is on the 2nd partition, so root would need to be (hd0,1):
```
title Ubuntu, kernel 2.6.20-15-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=abde7e45-5149-4e3d-bb13-3188f7d05e2b ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
```
it would definitely be better to use UUID in the kernel line

You need map commands in your Windows entry:
```
title Microsoft Windows XP Home Edition
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

---

### Post by android6011 on 2007-07-26
thanks that did it

---

