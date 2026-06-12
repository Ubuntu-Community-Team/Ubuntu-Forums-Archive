---
title: "Dual boot windows 2000 and ubuntu same drive"
date: 2006-12-25
forum: Installation &amp; Upgrades
---

### Post by djur on 2006-12-25
I'm trying to dual boot both windows and ubuntu from the same drive.  I installed ubuntu first, for no real reason, that installation is working fine, it is on the second partition on my serial ATA drive. I then installed windows on the first partition of that drive expecting it to overwrite the master boot record.  To my surprise when I rebooted the system, I got grub, so I selected the Windows Chainloader option from the menu and it booted fine, awesome.. everything worked...  I then rebooted and removed the windows boot CD, and did exactly the same thing...

It didn't work.  It said "invalid partition" I believe was the error.  Interestingly  enough when it booted it booted with the command (hd1,0), where ubuntu is booting with the command (hd0,1), which would indicate it is on another drive?  I'm thinking (hd1,0) in this instance might have been the boot CD.

I have entered about every drive/partition combination conceivable, and none will boot windows.  Since this is the first partition of the first drive, mapping should not be required, it should just boot...  I cannot understand whey windows did not write its MBR...

I also have a scsi drive and an IDE drive with stray / abandoned windows installations, which I'm hoping aren't causing any of the current confusion.

Anyone have any ideas?

---

### Post by Unc0 on 2006-12-25
try installing windows first and then install ubuntu. that's what i just did and it works fine. GRUB is the boot loader and i can access my windows installations from it.

---

### Post by bulldog on 2006-12-25
We can take a look at your partitions,can you give me the output of```
sudo fdisk -l ( l as in like)
```


Maybe you can give the menu.lst as well to see how it's configured your installs.
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by djur on 2006-12-25
I have no idea why my swap drive has the boot flag, I'm off to experiment with this now, but let me know what you think.

```
Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100       10199    40965750   83  Linux
/dev/sda3   *       10200       10454     2048287+  82  Linux swap / Solaris
/dev/sda4           10455       24792   115169985    5  Extended
/dev/sda5           10455       24792   115169953+   b  W95 FAT32

Disk /dev/hda: 6498 MB, 6498680832 bytes
255 heads, 63 sectors/track, 790 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         790     6345643+   b  W95 FAT32
Disk /dev/sdb: 18.3 GB, 18360785920 bytes
255 heads, 63 sectors/track, 2232 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2232    17928508+   b  W95 FAT32
```

I'm not sure how much good this will do you since I had to manually edit this file to get Ubuntu to boot. (it set the drives up at (hd1,1) by default....


```
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by bulldog on 2006-12-25
```
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1** <------this one**
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```
It seems you have a boot able windows on your hda1 partition which is listed in your menu.lst.
We have to change that one to the right partition,which is (hd0,0) but not on /hda1 but sda1.

Another question would be on which disk is GRUB located?
In other words which one is the disk where you boot from?
This could make a difference because the first disk is (hd0) and the second disk is (hd1) and they are both listed as (hd0) which can not be.

But if your ubuntu boots well I presume this entry's are right so you should be booting from the Sata disk.

**EDIT**
I read you had to make some changes to the menu.lst in order to get ubuntu to boot,this can be essential.
Because if GRUB is on the IDE disk your menu.lst should be modified,just check in the BIOS which drive is set to boot by default.
Or type in your terminal```
cat /boot/grub/device.map
``` and copy the output to the forum please.

---

### Post by djur on 2006-12-25
The device map seems to be wrong.  I checked my bios, which has my SATA drive booting first, then my SCSI (adapted by a PCI card), and then my IDE drive.   Yet this is what grub generated as the device map..

```
(hd0)   /dev/hda
(hd1)   /dev/sda
(hd2)   /dev/sdb
```

When I try to boot (hd1,0) it gives me an error that it isn't a suitable boot disk...  maybe because it thinks the partition is the second drive?

I formatted both my scsi drive and ide drive to fat32 since my first post, so neither of them have a working installation on them..

when I go to a grub terminal and type locate /boot/grub/stage1 I get (hd1,1)

It seems grub thinks my sata drive is the second drive, and my bios thinks it is the first drive...  so grub set everything up as sda being (hd1) but really it is (hd0)...

Maybe I should give in and change my boot order? :P

Just throwing out ideas, I'm waiting for the real verdict when you post :)

---

### Post by bulldog on 2006-12-25
Well sins you want to run linux and want to use GRUB,you have to accept that ubuntu calls the cards.

If it says your sda is (hd1) just accept it :D 
But that said we can change it.

If you're able to set the sata as master boot device in your BIOS,and you should be,we can reinstall GRUB on this disk.
But you have to boot from this disk in the future to see the GRUB menu.
Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a grub> prompt 
```
find /boot/grub/stage1 <-----should be (hd0,1)
```
This will return a location which you have to use in the next command. 
```
root (hd?,?)<----should be (hd0,1)  
```  
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```
Now Grub will be installed to the mbr.

If this is done without any errors you can reboot and boot from sata disk.
You should see the GRUB menu and you can boot into ubuntu.
Now we have to add the windows entry to your menu.lst but that's a minor thing to do,just try this and see if we can get this going shall we?

---

### Post by djur on 2006-12-25
The problem is:
find /boot/grub/stage1   returns:  (hd1,1)

---

### Post by bulldog on 2006-12-25
If you set the SATA disk as first boot device it shouldn't,you have the IDE as first boot device so the SATA disk is (hd1) and your ubuntu is on (hd1,1).

It must be set into the BIOS,I have an IDE disk and a SATA disk too,and I can make a boot choice by hitting F11 while booting,but that's not the same thing as changing the BIOS.

But if it's not bothering you,it's all change able so you may put GRUB on the IDE disk as well,we can modify your menu.lst accordingly.
Just let me know what you decide to do and we can altering GRUB to work with us.

---

### Post by djur on 2006-12-25
I have my SATA drive set to be the first boot device, but something is being confused somewhere along the lines...   My bios sets boot order (cdrom, hard disk, floppy, etc), and then you set your HD boot priority.  
mine is SATA, SCSI, IDE..

My thought is the SATA Drive is being recognized by grub at boot as the primary drive, and then once the system is booted it is being recognized as the second drive.

Since (hd0,1) boots ubuntu fine..  yet (hd1,1) is where /boot/grub/stage1 is located.

I'm just going to try installing to hd0 and see what happens..  if nothing else I can boot to the live CD again and reverse it.

---

### Post by bulldog on 2006-12-25
Strange things,computers :D  just try and we'll see what to do.

---

### Post by djur on 2006-12-25
I installed to (hd0)...  everything works exactly the same as before..  AND

If I try to install the (hd1) which it thinks I'm currently installed to EVEN AFTER just installing to (hd0), it spits out this:

```
grub> find /boot/grub/stage1
 (hd1,1)

grub> setup (hd1)

Error 12: Invalid device requested

grub> root (hd1)

grub> setup (hd1)

Error 17: Cannot mount selected partition

grub> 
```

---

### Post by djur on 2006-12-25
I think I'm going to change the boot order of my drives, simply because I'm running out of options.

---

### Post by bulldog on 2006-12-25
Well leave it on the (hd0) then.
No harm done.
Can you copy the menu.lst to the forum ```
gksudo gedit /boot/grub/menu.lst
```

Set this disk as primary boot device in your BIOS so we have that right.

---

### Post by djur on 2006-12-25
I disconnected my other drives to ensure they weren't part of the picture...  Everything is exactly the same which means it's booting from the SATA drive.  So I suppose I'm fine with respect to grub, now when I try to boot windows from (hd0,0) it says NTLDR is missing...  so I we still have the mystery of why windows did not install in a bootable fashion.

```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

### Post by bulldog on 2006-12-25
Because it points to the wrong hd (hda1):D 
```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1**<------- should be sda1**
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

---

