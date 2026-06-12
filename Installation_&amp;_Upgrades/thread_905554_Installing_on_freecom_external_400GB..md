---
title: "Installing on freecom external 400GB."
date: 2008-08-30
forum: Installation &amp; Upgrades
---

### Post by BabyBoy on 2008-08-30
Hey all,

I recently tried to install ubuntu on my external USB freecom 400GB HD.
What I did was boot live CD double click the desktop installer so I could chat on msn at the same time :) , I mounted the XHD and selected auto partition just one question where do I put the grub loader on the XHD drive or it says Hd0 or something else.....

Becuase when I load it the biod does not detect the hard drive....
It will not load up I have been into bios and it has not detected it.
Its also screwed up my windows XP drive as it cannot boot windows either!

Any help on this one is much thanked. :confused:

---

### Post by cdtech on 2008-08-30
The best method for an external USB drive is to let the installation install the GRUB bootloader to the USB drive, you can see which drive the USB device is typing on a command line:
```
sudo fdisk -l
```
(It should be something like "sdc")

You should have a setting within your BIOS to allow boot from USB. With this option, when you have the USB drive connected, your BIOS will boot from the external drive (if your boot order is 'USB - CDROM - HARD DRIVE'). You can re install GRUB but you'll need to repair your MBR on your Window's drive.

Does this make sense to you?

---

### Post by BabyBoy on 2008-08-30
Ok this is what I got.

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       35767   287298396    7  HPFS/NTFS
/dev/sda2           35768       36481     5735205    c  W95 FAT32 (LBA)

Disk /dev/sdf: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000abc95

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1       47884   384628198+  83  Linux
/dev/sdf2           47885       48641     6080602+   5  Extended
/dev/sdf5           47885       48641     6080571   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

```

Looks to me like linux and windows are perfectly installed I guess its to do with boot loading etc... Im confused. It will not load windows.

---

### Post by cdtech on 2008-08-30
Looks good. First thing you need to do is unplug the USB drive, boot from the Window's install disc and select recovery mode. Select to repair MBR for your Window's installation (fixmbr).

Once you can boot into Window's successfully without the USB drive installed, insert the Ubuntu Live CD and reboot. Plug the USB drive in (this should auto mount). Open a terminal (Accessories > Terminal) and type:
```
sudo grub
```
This will give a "grub" prompt:
```
 grub>
type:
 grub> find /boot/grub/stage1
find /boot/grub/stage1
 **(hd0,0)**
grub>
```
This shows stage1 on my install within the primary drive first partition (hd0,0). Yours will probalbly show (**hd5**,0) or something along those lines. Use the output for the following:
```
 grub> grub-install /dev/**hd5** (whatever was returned from above)
```
You should now have the GRUB bootloader insalled on the USB drive away from the Window's install. If you have your boot order correct (USB - CDROM - HARD DRIVE) you should be able to boot with your USB drive connected and it will boot Ubuntu. With it unplugged it will boot Window's.

Good Luck, let me know how it turns out........

**Update::.**
Examples of the difference from the GNU/Linux and GRUB device names:

**1st Physical Hard Drive:**
Linux IDE: GRUB IDE: Linux SCSI: GRUB SCSI:
/dev/hda1 ----(hd0,0)----- /dev/sda1-------(hd0,0)
/dev/hda2 ----(hd0,1)----- /dev/sda2-------(hd0,1)
/dev/hda3 ----(hd0,2)----- /dev/sda1-------(hd0,2)
/dev/hda4 ----(hd0,3)------/dev/sda2-------(hd0,3)

**2nd Physical Hard Drive:**
Linux IDE: GRUB IDE: Linux SCSI: GRUB SCSI:
/dev/hdb1---- (hd1,0)----- /dev/sdb1------ (hd1,0)
/dev/hdb2---- (hd1,1)----- /dev/sdb2------ (hd1,1)
/dev/hdb3---- (hd1,2)----- /dev/sdb1------ (hd1,2)
/dev/hdb4---- (hd1,3)----- /dev/sdb2-------(hd1,3)

---

