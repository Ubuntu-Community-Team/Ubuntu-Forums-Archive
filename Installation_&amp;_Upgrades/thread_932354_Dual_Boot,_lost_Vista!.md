---
title: "Dual Boot, lost Vista!"
date: 2008-09-28
forum: Installation &amp; Upgrades
---

### Post by mikeman141 on 2008-09-28
Hey all,

I'm pretty new to linux.  I'm not sure if this is the best place to post so please let me know if there is a more appropriate category/forum.  I have a dell xps m1530, 3 gigs of ram, 300 gig HDD, intel core2 duo at 2 GHz, nvidea graphics.  I had installed xubuntu but decided I wanted the real deal so I deleted my xubuntu  partition to start over.  

Once I restarted, GRUB couldn't find the parition, or the files it needed to start.  ANd I couldn't boot my computer at all.  I downloaded and ran the systemrescuecd and created a new partition like the old one i deleted  and did some resizing and then installed regular ubuntu 8.04 via a cd I had made earlier.   

The installation went fine, and ubuntu is running (wireless issues aside).  I can even access my ntfs vista partition in the media directory.  All of my files appear to be intact.

However, when i restart my machine, if I have GRUB boot to vista, a few seconds later the machine just shuts down!  I don't understand why this is happening.  I shrank the windows partition , but that wouldn't delete the files right?  They all appear to still be there when I access the drive using ubuntu.  Any idea how to proceed?  Thanks so much.

---

### Post by WWSmith36 on 2008-09-28
Please post output of
```
sudo fdisk -l
```
and content of this command of this command after this line
## ## End Default Options ##
```
cat /boot/grub/menu.lst
```
We need you make sure you grub menu is right.  Also Vista will be a little freaked out the first time you load it,

---

### Post by Pumalite on 2008-09-28
Try to boot your Vista with Super Grub:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by mikeman141 on 2008-09-29
Here's the info.  Thanks a bunch

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x28000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          11       88326   de  Dell Utility
/dev/sda2              12        1317    10490445    b  W95 FAT32
/dev/sda3   *        1318       35530   274815922+   7  HPFS/NTFS
/dev/sda4           35531       38913    27173947+  83  Linux




title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ddcaad05-c146-4244-ae98-b44967adf3e0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ddcaad05-c146-4244-ae98-b44967adf3e0 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista/Longhorn (loader)
root		(hd0,2)
savedefault
makeactive
chainloader	+1

---

### Post by mikeman141 on 2008-09-29
the ntfs drive has the vista partition.

---

### Post by caljohnsmith on 2008-09-29
From your fdisk output, it looks like your Grub's menu.lst entry for Vista is correct. The fact that you don't get a Grub error when booting Vista, but instead your computer shuts down, means that most likely your problem is Vista, not Grub at this point. Did you use Linux's partition editor (gparted) to do your partitioning to make room for linux? If you did, that is most likely your problem; unfortunately Microsoft designed Vista so that Vista maintains its own HDD partition table outside of the main HDD partition table in the HDD's MBR (master boot record); in practicality that means that if you use anything other than Vista's Disk Management to make partition changes, you can break Vista.

Do you have a Vista Recover/Install CD? If not, you can download one [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). Just boot from the Vista Recovery CD, go to the command line, and run the following command:
```
bootrec /rebuildbcd
```
That will rebuild Vista's partition table, and hopefully that will be all it takes to get Vista working again. If not, let me know exactly what happens when you try and boot Vista after trying the above command.

---

### Post by Diablo713 on 2008-09-29
I had a similar problem, where i installed ubuntu then deleted the partition from vista then a grub error would come when ever i try to boot vista,to fix i loaded the vista bootloader from a a vista recovery disk,if thats the same problem you are having just pm me and i will send the instructions to you.

---

### Post by mikeman141 on 2008-09-29
I popped that Vista recovery disk in and clicked "repair" the computer did its thing, restarted, and problem solved!  Grub boots into either OS no problem.  Thanks a bunch.

---

### Post by Diablo713 on 2008-09-29
You were lucky that auto repair worked for you,in my case i had to do it with the command line.

---

