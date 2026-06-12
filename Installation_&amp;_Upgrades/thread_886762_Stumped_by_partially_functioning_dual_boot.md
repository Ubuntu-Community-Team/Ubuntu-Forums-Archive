---
title: "Stumped by partially functioning dual boot"
date: 2008-08-11
forum: Installation &amp; Upgrades
---

### Post by Rebelli0us on 2008-08-11
I have 2 SATA disks
There's a Windows installation in the 1st partition of disk 1
There's a Windows installation in the 1st partition of disk 2 (a bootable cloned backup)
There's Ubuntu 8.04 in the 2nd partition of disk 2

When I installed Ubuntu, I temporarily disabled the controller for disk 1 to protect the MBR. So Grub installed on the MBR of disk 2.

I can boot Linux just fine through the BIOS boot menu by selecting the 2nd disk as the boot-first device. Grub boots disk 2 -- Ubuntu or Windows on disk 2.

I used the dd command, as described in countless threads, to create bootsect.lnx, and placed a corresponding line in boot.ini on the 2nd disk

sudo dd if=/dev/sdb of=/media/Disk_2/bootsect.lnx bs=512 count=1

So now both Ubuntu and Windows 2 can boot each other just fine, but only when I boot disk 2 through the BIOS boot menu.

Problem: I cannot boot Ubuntu from boot.ini on disk 1.

I tried:
C:\bootsect.lnx="Ubuntu Linux"
and
D:\bootsect.lnx="Ubuntu Linux"

No luck, Grub just hangs

Question: How can I get Windows on disk 1 to boot Ubuntu on disk 2?

Do I need a different rendition of bootsect.lnx when booting from disk 1?



BTW, I love my new Ubuntu and I'm keeping it. I've burned several Live CDs for friends to try it, it's amazing how people resist change.

---

### Post by Pumalite on 2008-10-08
Check this thread:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by caljohnsmith on 2008-10-08
> **Rebelli0us said:**
> 
I used the dd command, as described in countless threads, to create bootsect.lnx, and placed a corresponding line in boot.ini on the 2nd disk

sudo dd if=/dev/[COLOR="Red"]sdb[/COLOR] of=/media/Disk_2/bootsect.lnx bs=512 count=1

You bumped that other thread today saying that you are still having this problem, so I thought I would respond. I think I might know exactly what your problem is, because I've tried to do the same thing myself until I figured out what was going on: the bottom line is that copying the MBR of sdb with the dd command above unfortunately won't work when trying to do the modified boot.ini approach to boot Grub from the Windows boot loader. The reason is because when you install Grub to the MBR, Grub installs its stage1 file into the MBR, but Grub also embeds its stage1.5 file in the free sectors just after the MBR. So when you copy just the MBR and put that in your boot.ini, and when you try to boot that MBR from the Windows boot loader, that Grub MBR can't find the stage1.5 file that should come in the sectors immediately following the MBR, because the MBR you copied is in an entirely different location now. 

The way around it is to install Grub and not let Grub embed its stage1.5 file, so that instead Grub points to the partition which has the stage1.5 to boot with. It is possible but a bit of trouble to do that when installing Grub to the MBR, but fortunately though, an easier solution exists: having Grub not embed its stage1.5 file is what happens by default when you install Grub to a partition boot sector rather than the MBR. So the bottom line is, install Grub to your Linux partition's boot sector, and use that with the dd command above. 

As an example, if Linux is on sdb2, to install Grub to its partition boot sector you would do:
```
sudo grub
grub> root (hd1,1)
grub> setup (hd1,1)
grub> quit
```
Then copy that boot sector with:
```
sudo dd if=/dev/[COLOR="Red"]sdb2[/COLOR] of=/media/Disk_2/bootsect.lnx bs=512 count=1
```
And then use the method you did with adding it to boot.ini, depending on whether Windows sees itself as on the C drive or D drive. Let me know how it goes, or if you need more specific info/details. :)

---

### Post by Rebelli0us on 2008-10-08
> **caljohnsmith said:**
> You bumped that other thread today saying that you are still having this problem, so I thought I would respond. I think I might know exactly what your problem is, because I've tried to do the same thing myself until I figured out what was going on: the bottom line is that copying the MBR of sdb with the dd command above unfortunately won't work when trying to do the modified boot.ini approach to boot Grub from the Windows boot loader. The reason is because when you install Grub to the MBR, Grub installs its stage1 file into the MBR, but Grub also embeds its stage1.5 file in the free sectors just after the MBR. So when you copy just the MBR and put that in your boot.ini, and when you try to boot that MBR from the Windows boot loader, that Grub MBR can't find the stage1.5 file that should come in the sectors immediately following the MBR, because the MBR you copied is in an entirely different location now. 

The way around it is to install Grub and not let Grub embed its stage1.5 file, so that instead Grub points to the partition which has the stage1.5 to boot with. It is possible but a bit of trouble to do that when installing Grub to the MBR, but fortunately though, an easier solution exists: having Grub not embed its stage1.5 file is what happens by default when you install Grub to a partition boot sector rather than the MBR. So the bottom line is, install Grub to your Linux partition's boot sector, and use that with the dd command above. 

As an example, if Linux is on sdb2, to install Grub to its partition boot sector you would do:
```
sudo grub
grub> root (hd1,1)
grub> setup (hd1,1)
grub> quit
```
Then copy that boot sector with:
```
sudo dd if=/dev/[COLOR="Red"]sdb2[/COLOR] of=/media/Disk_2/bootsect.lnx bs=512 count=1
```
And then use the method you did with adding it to boot.ini, depending on whether Windows sees itself as on the C drive or D drive. Let me know how it goes, or if you need more specific info/details. :)




Thank you. I'm a Linux newbie and worried I might screw everything up and render both OSes on disk 2 unbootable. But I'm willing to try. The Ubuntu partition editor gparted(?) shows several partitions sdba, sdbb (or is it sdb1, sdb2 ?) whereas GRUB uses the hd(x,x) designation. It gets confusing. I know I originally created 2 primary partitions, but Linux subdivided partition 2 into several more... and I'm not sure which one is to be made bootable.

After cloning windows onto disk 2, I use a registry fix to ensure that the clone always sees itself as booting from drive C. (Otherwise it wouldn't be a clone.) Will the procedure you describe also free up the MBR on disk 2 so I can reinstall the Windows boot loader there? (Because as it stands now, Windows on disk 2 is not self-booting but it relies on GRUB or Windows on disk 1 to boot it.)

---

### Post by caljohnsmith on 2008-10-08
> **Rebelli0us said:**
> 
Will the procedure you describe also free up the MBR on disk 2 so I can reinstall the Windows boot loader there? (Because as it stands now, Windows on disk 2 is not self-booting but it relies on GRUB or Windows on disk 1 to boot it.)
Yes, the procedure I roughly outlined will only work for putting Grub into the boot.ini file of Windows when they are both on the same drive; using a few special Grub tricks, it is possible to create a Grub boot sector that you could put in your boot.ini in your 1st drive to boot Grub on the second drive, but it is usually more trouble than it is worth. Can you simply set your 2nd drive in BIOS to always be the first to boot? If you can, probably the easiest solution for your situation would be to add Windows on the first drive to your Grub menu on the second drive. Would that work for you? 

Also, please post:
```
sudo fdisk -lu
```
So I can get a better idea of your setup.

---

### Post by Rebelli0us on 2008-10-08
Code box isn't working 




Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa047efeb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   312576704   156288321    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5e2ebc10

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   270341819   135170878+   7  HPFS/NTFS
/dev/sdb2       270341820   312576704    21117442+   5  Extended
/dev/sdb5       270341883   310729229    20193673+  83  Linux
/dev/sdb6       310729293   312576704      923706   82  Linux swap / Solaris






What happened to sdb3 & sdb4?

---

### Post by caljohnsmith on 2008-10-09
You don't have sdb3 and sdb4 because those would be primary partitions if you had them; instead you have sdb2 which is an extended partition, and your extended partition contains the logical partitions sdb5 and sdb6. Logical partitions always start with sdb5 and count up from there. :)

Anyway, go ahead and boot into Ubuntu on your 2nd drive, and then do:
```
gksudo gedit /boot/grub/menu.lst
```
At the end of that file add:
```
title Windows XP (1st drive)
rootnoverify (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Save, reboot, try the new Windows entry above from the Grub menu, and let me know exactly what happens.

---

### Post by Rebelli0us on 2008-10-09
right now it is:

-----------------------------------------
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c1f2856c-785e-45d7-82e2-9a0da4c4f7f9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=c1f2856c-785e-45d7-82e2-9a0da4c4f7f9 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c1f2856c-785e-45d7-82e2-9a0da4c4f7f9 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=c1f2856c-785e-45d7-82e2-9a0da4c4f7f9 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows 2000 Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
----------------------------------------


All the entries with "root (hd0,4)" and "root (hd0,0)" are wrong when I boot with disk 1 as the first boot device. Hmm? Maybe that's why grub hangs when I boot from boot.ini pointing to bootsect.lnx. So maybe I should change all hd0,4 to hd1,4

---

