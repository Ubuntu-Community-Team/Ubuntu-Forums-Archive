---
title: "More Ubuntu Kernel Panicking"
date: 2005-10-02
forum: Installation &amp; Upgrades
---

### Post by mohhingman on 2005-10-02
Hi All, 
Ubuntu Hoary is having issues booting after an install. I want to get Ubuntu running on a laptop. Since the laptop didn't have a cdrom, i removed the hdd from the laptop and proceeded to install on my main computer. Installation of  Ubuntu onto a laptop hdd went successfully. The laptop hdd was then removed from the main computer and was placed into the laptop. The laptop was powered up, and the hdd started to boot Ubuntu. It went fine until it stopped as shown below:
VFS: Cannot open root device "hda1" on unknown-block(0,0)
Please append a correct "root=" boot option
Kernel Panic - not syncing : VFS : unable to mount root fs on unknown-block(0,0)
Initially I was not surprised it did this since another computer was used for the installation and would have confused the bootloader. Immediately after, i attempted to correct the grub config files according to some posts on this forum and some others found using google. 
Ubuntu gave the same error message on bootup regardless of whether the grub files were corrected or not.:confused: As far as i can tell, the config files are *should* be working. Has anyone had this problem before? 
Diagnostic info shown below:
----menu.lst----------------------------------------------
default		0
timeout		3
hiddenmenu
title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro 
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot
title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot
title		Ubuntu, kernel memtest86+ 
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot
### END DEBIAN AUTOMAGIC KERNELS LIST
----FSTAB----------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext2    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
----device.map----------------------------------------------
(hd0)	/dev/hda
----fdisk -l ----------------------------------------------
Disk /dev/hda 1083 MB 1083801600 bytes
255 chead/ 63 sectors/track, 131 cylinders
Units = cylinders of 16065 = 512 = 8225280 bytes
Device       boot      Start     End     Blocks     ID      system
/dev/hda1    *           1        121     971901   83      Linux
/dev/hda2                 121     131     80325     5       Extended
/dev/hda5                 122     131     80293+   82      Linux swap  
-----------------------------------------------------------
Thanks in advance :)

---

### Post by mlomker on 2005-10-02
> Since the laptop didn't have a cdrom, i removed the hdd from the laptop and proceeded to install on my main computer. 

If you have a desktop handy and the laptop is capable of network booting, then you might want to look into setting up a PXE (called RIS in Windows) server instead of moving the disk.

Your menu list looks correct for an IDE drive.  It'd be sda1 for SATA or SCSI.  Here's mine:

```

title           Ubuntu, kernel 2.6.10-5-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/sda1 ro quiet splash
initrd          /boot/initrd.img-2.6.10-5-385
savedefault
boot



```

---

### Post by mohhingman on 2005-10-03
> 
If you have a desktop handy and the laptop is capable of network booting, then you might want to look into setting up a PXE (called RIS in Windows) server instead of moving the disk.

Thanks for the reply.

Unfortunately, the laptop i'm using does not support network booting. It is quite old. It would be much better to load Ubuntu from a remote server than have to open the thing up. Is there a way to correct the configuration files on the laptop hard drive to solve the kernel panic error? I'm really confused why ubuntu came up with the error message after fixing the grub files up. 

Is there a program or script which can find the errors?

Cheers,
Mohhingman

---

### Post by mlomker on 2005-10-03
> Is there a program or script which can find the errors?


Not that I know of.  What you are doing really isn't a supported solution, so having some trouble getting it working shouldn't be too surprising.  I can't think of an easy way to troubleshoot this without a bootable network card or a bootable CD.  There are older distros that can boot from floppy and then install over the network, but I'm not familiar with them.

---

