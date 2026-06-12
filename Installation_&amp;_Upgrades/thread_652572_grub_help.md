---
title: "grub help"
date: 2007-12-28
forum: Installation &amp; Upgrades
---

### Post by carverj on 2007-12-28
Hi there,
              I have a primary master disk called hda which has Vista and Ubuntu. Also have a secondary disk called sda on sata cable. This has Solaris 10 installed.
The BIOS won't seem to allow booting from the master, and so I would like to include the following grub entry into my working grub list:

```
#---------- ADDED BY BOOTADM - DO NOT EDIT ----------
title Solaris 10 11/06 s10x_u3wos_10 X86
root (hd0,0,a)
kernel /platform/i86pc/multiboot
module /platform/i86pc/boot_archive
#---------------------END BOOTADM--------------------
#---------- ADDED BY BOOTADM - DO NOT EDIT ----------
title Solaris failsafe
root (hd0,0,a)
kernel /boot/multiboot kernel/unix -s
module /boot/x86.miniroot-safe
#---------------------END BOOTADM--------------------
```

I have tried editing the root (hd0,0,a) line to boot, but get the error 22.
Any help appreciated!

---

### Post by meierfra on 2007-12-28
Could you post the output of  "sudo fdisk -l" and  the bottom half of "/boot/grub/menu.lst" from ubuntu. Do you have a "menu.lst" on the Solaris partition?

---

### Post by carverj on 2007-12-28
Sure, fdisk -l output:

```
Disk /dev/hda: 20.4 GB, 20485785600 bytes
255 heads, 63 sectors/track, 2490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x998d8ef5

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           2        2490    19992892+  bf  Solaris

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x81ad973d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6185    49676288    7  HPFS/NTFS
/dev/sda2            6186        9623    27615735   83  Linux
/dev/sda3            9624        9729      851445   82  Linux swap / Solaris

```

Grub menu.list (working for Ubuntu on sda):

```
# 
default		0

timeout		10

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a993f3a8-1c97-4e9d-9457-a125e08171f8 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a993f3a8-1c97-4e9d-9457-a125e08171f8 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

And the Solaris entry I would like to include to above list:

```
#---------- ADDED BY BOOTADM - DO NOT EDIT ----------
title Solaris 10 11/06 s10x_u3wos_10 X86
root (hd0,0,a)
kernel /platform/i86pc/multiboot
module /platform/i86pc/boot_archive
#---------------------END BOOTADM--------------------
#---------- ADDED BY BOOTADM - DO NOT EDIT ----------
title Solaris failsafe
root (hd0,0,a)
kernel /boot/multiboot kernel/unix -s
module /boot/x86.miniroot-safe
#---------------------END BOOTADM--------------------
```

Thanks for the lightning fast reply mate!

---

### Post by meierfra on 2007-12-28
I don't see anything wrong.  Error 22  probably  means that  "root (hd0,0,a)" is wrong.

Do

```

sudo grub
```

and at the "grub>" prompt:

```
find /platform/i86pc/multiboot
```

This should return (hd0,0,a). If not use, then use it in place of (hd0,0,a)

---

### Post by carverj on 2007-12-28
At least I will learn a lot about grub errors today
:)

```
grub> find /platform/i86pc/multiboot
find /platform/i86pc/multiboot

Error 15: File not found

```

---

### Post by meierfra on 2007-12-28
Well I don't know enough about Solaris to help you any further.  But let me try a  shot in the dark:


Use this for Solaris in menu.lst:

title Solaris 10 11/06 s10x_u3wos_10 X86
root (hd0,0)
chainloader +1


This should work, if Solaris put some booting information into the boot sector of hda1.

---

### Post by meierfra on 2007-12-29
I did some googeling and found this:

[http://www.sun.com/bigadmin/features/articles/grub_boot_solaris.jsp]("http://www.sun.com/bigadmin/features/articles/grub_boot_solaris.jsp")

a quote from Section 5:

> GRUB as obtained from sources other than Sun does not currently recognize Solaris on-disk VTOC and UFS formats. Sun has submitted changes to the GRUB project to support this; until they have been integrated, only the Solaris GRUB will work. If Linux installed GRUB on the master boot block, you will not be able to get to the Solaris OS even if you make the Solaris partition the active partition. In this case, you can chainload from the Linux GRUB by modifying the menu on Linux. Alternatively, you can replace the master boot sector with the Solaris GRUB in the above example, by using the installgrub(1M) command:

installgrub -m /boot/grub/stage1 /boot/grub/stage2 /dev/rdsk/c0t2d0s3

Before the Solaris VTOC and UFS implementation is propagated to the standard GRUB release, only the Solaris version of GRUB will work. 

---

### Post by carverj on 2007-12-29
Ok gotcha.
So what I have done is to change the jumpers, re-install solaris to the hard drive that boots in the hopes that it picks up all three OS's.
Well it picked up Windows which is a start. So how do I query ubuntu to find out what lines to add for it's entry?

In the meantime, will try adding the following line from previous post:

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=a993f3a8-1c97-4e9d-9457-a125e08171f8 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
```

Hope this works!!

---

### Post by meierfra on 2007-12-29
That should work. But I recommend the following instead:

title Ubuntu
root (hd1,1)
configfile /boot/grub/menu.lst


Once you choose Ubuntu from the Solars Grub Menu, the Ubuntu Grub menu will load. 
This has the advantage that you won't have to  edit your Solars menu.lst each time there is a Ubuntu kernel update.

To make this work nicely,  edit the Ubuntu menu.lst as follows:
 
add "hiddenmenu" 

and change 

"timeout 10" to "timeout 1"

Then you won't even notice the second Grub menu.

---

### Post by carverj on 2007-12-29
Yes that seems to work fine!!
Thank you again, as I was about to begin a search for a command or program to alert me
once the Ubuntu list was altered.
You seem to have saved me the effort!
Happy new year all!!!!!

---

