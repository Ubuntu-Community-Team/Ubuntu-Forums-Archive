---
title: "Ubuntu on external drive Grub error 21"
date: 2008-08-30
forum: Installation &amp; Upgrades
---

### Post by bereta on 2008-08-30
Hello 

I have installed ubuntu 8 on an external drive (not a USB stick) and it works quite good, better than I expected. The problem is that now I can't boot my laptop unless the external drive is connected to the laptop. 

When I boot the laptop without the external drive connected I get:
Grub loading stage 1.5
Grub loading, please wait.....
error 21

I have googled this and error 21 means grub is looking for a configuration file that does not exist (its on the external drive in my case)...

My question is...

How can i fix this so that when the external drive is connected it boots into ubuntu and when not connected i can boot into vista/xp (i have dual boot)?:confused::confused::confused:

Thanks

---

### Post by cdtech on 2008-08-30
You'll need to boot without the USB drive plugged in and boot with the Window's install disc. Boot into the recovery mode and fix the MBR for Windows using something like "fixmbr". This will allow you to boot into window's as original. Set the BIOS boot order for USB - CDROM - then Hard drive.

Once you have that done you'll need to re install your GRUB bootloader to the USB device and not the MBR of your primary drive. Now when you have the USB drive unplugged it will boot into Window's and with it plugged in the BIOS will see the USB drive and use GRUB to boot the USB drive.

Does that make sense?   :)

---

### Post by bereta on 2008-08-30
Thanks for the reply

Ok I have fixed vista/xp, I knew something about the MBR needing to be restored but I don't have a vista install DVD all that came with my laptop was a recovery DVD witch is kind of like a ghost image of vista. 

Any ways I found this program called EasyBCD 1.7.2 that you install in vista and then you can edit the vista boot loader, It also has an option of repairing/restoring the vista MBR.

Now how do I install GRUB on the external drive and not affect the primary drive? I mean I boot of the live CD and than what are the commands?

Thanks

---

### Post by cdtech on 2008-08-30
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

### Post by bereta on 2008-08-30
I have done what you explained and I get this:

ubuntu@ubuntu:~$ sudo grub-install /dev/hd1
Probing devices to guess BIOS drives. This may take a long time.
/dev/hd1: Not found or not a block device.
ubuntu@ubuntu:~$ 

I have also found this page on the ubuntu docks: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub) I have tried the first part...
> find /boot/grub/stage1

Using this information, set the root device:

grub> root (hd0,1)

Install Grub:

grub> setup (hd0)
And it looks like it worked (it said success ) but computer will not boot of the USB drive. And yes I have the boot order all in the correct sequence, and I have also set hd1,0 (the usb drive first partition ) as a boot partition with gparted.

---

### Post by cdtech on 2008-08-30
> find /boot/grub/stage1

Using this information, set the root device:

grub> root (hd0,1)

Install Grub:

grub> setup (hd0) 

I don't understand. You have Ubuntu installed on a USB  drive. When you type "find /boot/grub/stage1" with the USB drive connected, you should see something like "find /boot/grub/stage1 (hd2,0)", you should do "setup (hd2 or whatever your USB drive is). The hd0 is your primary drive.

---

### Post by cdtech on 2008-08-31
Try using the sda device instead of the hd device name.
```
grub-install /dev/sdb1
```
Find the drive name using "sudo fdisk -l"

---

### Post by bereta on 2008-08-31
that was just a quote from the dock, my USB drive is hd1,0.
So when I do find /boot/grub/stage1 I get (hd1,0)

---

### Post by bereta on 2008-08-31
This is what i get with sdb1

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4c2cd691

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         638     5120000   1c  Hidden W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         638        9394    70332416    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            9394       14594    41766912    f  W95 Ext'd (LBA)
Partition 3 does not end on cylinder boundary.
/dev/sda5            9394       14594    41765888    7  HPFS/NTFS

Disk /dev/sdb: 6495 MB, 6495068160 bytes
255 heads, 63 sectors/track, 789 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f7e6be9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         749     6016311   83  Linux
/dev/sdb2             750         789      321300    5  Extended
/dev/sdb5             750         789      321268+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ grub-install /dev/sdb1
Could not find device for /boot: Not found or not a block device.
ubuntu@ubuntu:~$

---

### Post by cdtech on 2008-08-31
then just try "sudo grub-install /dev/sdb1"

---

### Post by cdtech on 2008-08-31
I would use the Live CD and mount the partition to see if you even have a /boot directory:
```
mount /dev/sdb1 /media/disk-1
```
Be sure you have a directory within /media to mount to and have a look see.

---

### Post by bereta on 2008-08-31
lol thats the same thing (root privlages stay active for about 5 min after sudo...)

I'm looking at that doc I have linked above, and it looks like there may be more to this. Check out the troubleshooting section.

Thanks alot for all the time your putting into this.

---

### Post by cdtech on 2008-08-31
no problem, I'm just as curious as you at this point..:lolflag:

---

### Post by bereta on 2008-08-31
ok I'm making some progress, I have mounted sdb1 to /boot/ and did 
sudo /sbin/grub-install /dev/sdb
it installed grub .....yes!
But the problem now is that the laptop does not boot of the drive automaticali. I have forced it to boot of the USB drive, but all I get is a grub prompt, looks like the menu is not active or something.

Any sugestions?

---

