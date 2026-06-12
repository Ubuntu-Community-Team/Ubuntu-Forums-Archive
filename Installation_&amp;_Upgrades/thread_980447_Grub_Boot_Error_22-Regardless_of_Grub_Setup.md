---
title: "Grub Boot Error 22-Regardless of Grub Setup"
date: 2008-11-12
forum: Installation &amp; Upgrades
---

### Post by NoSkill on 2008-11-12
Hi,

          I have recently installed the new version of ubuntu 8.10 on my PC. I have 3 Harddrives , one of the has XP the other is just data and the other has my ubuntu partition. 

Whenever i try to boot, I get the Grub Error 22 message. I tried Fixing grub with


> sudo grub
find /boot/grub/stage1
    >>Returns (hd0,0)
root (hd0,0)
setup (hd0)

But when I boot again, I get the SAME error 22!

My menu.lst is as follows:

> 

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		438c7aec-d252-45a0-8806-7b274a9b16c5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=438c7aec-d252-45a0-8806-7b274a9b16c5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		438c7aec-d252-45a0-8806-7b274a9b16c5
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=438c7aec-d252-45a0-8806-7b274a9b16c5 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		438c7aec-d252-45a0-8806-7b274a9b16c5
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title		Microsoft Windows XP Professional
root		(hd1,1)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1



This looks very incorrect as there is no entry for ubuntu, and yes I copy pasted everything.

fdisk yields the following:

> 
ubuntu@ubuntu:/media/disk/boot/grub$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x35cc9dc6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38297   307620621   83  Linux
/dev/sda2           38298       38913     4948020    5  Extended
/dev/sda5           38298       38913     4947988+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e9aa6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2   *       16713       37810   169469685    7  HPFS/NTFS

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2e6cf85e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2       30515   245103705    f  W95 Ext'd (LBA)
/dev/sdc5               2       30515   245103673+   7  HPFS/NTFS
ubuntu@ubuntu:/media/disk/boot/grub$ 



Any ideas please anyone???

---

### Post by unutbu on 2008-11-12
Perhaps try this:
```
sudo grub
grub> device (hd0) /dev/sda
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```

Reboot, and see if you can at least boot Ubuntu.
If that does not work, please post the output of 
```

blkid
```

---

### Post by NoSkill on 2008-11-12
Same Error 22 Message after I entered the commands.

The output of blkid is:
> ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="438c7aec-d252-45a0-8806-7b274a9b16c5" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="61b3d7f2-2642-4fdb-86ec-cc0db25622a0" TYPE="swap" 
/dev/sdb2: UUID="5468B96468B94590" TYPE="ntfs" 
/dev/sdc5: UUID="126B19963A554391" LABEL="Music" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs"

---

### Post by linux_tech on 2008-11-12
If you can't boot windows, you could fix the mbr first. 

1. Boot up with your Windows XP disc.

2. Select the option Recovery Console.

3. At the prompt, type "fdisk /mbr" (without the quotes of course)

4. Restart your computer.

---

### Post by NoSkill on 2008-11-12
I am not particularly concerned about the Windows partition, I know it's there and available, I would just love for linux to work since I'm sick of windows

---

### Post by linux_tech on 2008-11-12
Boot your Live CD and do the following:
Code:

```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```

---

### Post by NoSkill on 2008-11-12
> **linux_tech said:**
> Boot your Live CD and do the following:
Code:

```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```

tried it already but unfortunately no luck. Thank you

---

### Post by meierfra. on 2008-11-12
Make sure your bios are set to boot from the Ubuntu drive.

---

### Post by NoSkill on 2008-11-12
> **meierfra. said:**
> Make sure your bios are set to boot from the Ubuntu drive.

Oh wow thanks, that did it. Fail on my part !

---

