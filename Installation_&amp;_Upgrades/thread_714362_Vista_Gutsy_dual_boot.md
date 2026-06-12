---
title: "Vista Gutsy dual boot"
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by mpfriar84 on 2008-03-03
Ok so I have searched this forum repeatedly and tried everything that was suggested for similar problems. I was dual booting vista and XP; I decided to install Gutsy on the partition that was previously XP, Gutsy works fine but now booting Vista is no longer an option. I can view the partition through Gutsy, but I really need to be able to use vista as well. Here is my info:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+  83  Linux
/dev/sda2            2551        9430    55263232    7  HPFS/NTFS
/dev/sda3            9431        9729     2401717+   5  Extended
/dev/sda5            9431        9729     2401686   82  Linux swap / Solaris


and menu.lst:

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=98a4d8d6-3447-4c66-89fa-a5732124010c ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=98a4d8d6-3447-4c66-89fa-a5732124010c ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by dstew on 2008-03-04
You need to add the Vista boot option to the menu.lst file. From Ubuntu, do ```
gksudo gedit /boot/grub/menu.lst
```At the end of the file, below the ### END DEBIAN AUTOMAGIC KERNELS LIST separator, enter```
title Windows Vista
root (hd0,1)
savedefault
makeactive
chainloader +1
```Save the file, then reboot, and you should be able to boot Vista.

---

### Post by mpfriar84 on 2008-03-04
Fist off, thanks dstew for responding to me, it was looking like I wasn't going to find any help fixing this. I edited the menu.lst file exactly as you said. Unfortunately I got an error while Vista was trying to start up that said BOOTMGR is missing. From there my only option was to Ctrl+Alt+Del and restart. Any thoughts?

---

### Post by froy02 on 2008-03-04
You have to restore the Vista boot record with your Vi$ta installation disk using bootrec.exe.  Here's a website for instructions:  [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392).

You may or may not have to re-install grub.  If you re-install a boot record on the partition you may not need to re-install grub.  However if you re-install the MBR also then you have to re-install grub.

---

### Post by dstew on 2008-03-04
See [this page]("http://www.howtogeek.com/howto/windows-vista/fixing-bootmgr-is-missing-error-while-trying-to-boot-windows-vista/"). What you need to do is enter the Windows Recovery Environment using the Vista CD, and get to the command line, as shown. There, issue the fixboot command. Then try it again. If you do the complete startup repair, grub will be replaced. But if you only do fixboot, only the partition boot loader will be replaced. That is what you want.

If you lose grub, no worries, we can install it again.

---

### Post by Pumalite on 2008-03-04
You can also use Super Grub to restore your MBR: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Then use this to reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Windows should ideally be installed first in sda1

---

