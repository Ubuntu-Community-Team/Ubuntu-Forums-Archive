---
title: "Dual Boot Noproblem, what about four systems ?"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by Qbito on 2008-05-10
Hello to everyone:)

I decide to break domination of MS systems on my PC and install it Ubuntu. But why to make life easier ? I decide to install two ubuntu Desktop i Server (just for exercise). Everything was fine till I install it Windows 2003 Server. When I'm choosing from GRUB boot loader menu: XP is starting and is fine, but when I'm choosing Win 2003 Server is starting but is removing automatically MBR and after restart I don't see GRUb loader but only MS one. And I need to go through whole Live CD proces. 

The question is is it just Win 2003 problem or it's me :)

The other question: How can I check which partiion chose Linux desktop and which for Linux Server. When I'm doing fdisk -l is shoing me sda I resume its first disk and then 1,2,3, for partitions and sdb for second disk and 1,2,3,.. for part. But in menu.lst I need to chose hdX,Y what is X what is Y.

I apologize for this sort of question but I'm stuck and I can't find nothing about four systems on one PC.

Thanks

---

### Post by Pumalite on 2008-05-10
You can reinstall Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Post:
sudo fdisk -l
cat /boot/grub/menu.lst

---

### Post by luvr on 2008-05-10
> **Qbito said:**
> The question is is it just Win 2003 problem or it's me
Must be a Windows 2003 issue. Windows Server systems probably want to be the **only** Operating System installed on the computer. (Which, admittedly, makes some kind of sense in a production environment, but severely limits your options if you're running it on a test machine.)

> The other question: How can I check which partiion chose Linux desktop and which for Linux Server.
Not sure, but I guess you could be looking into the *"menu.lst"* file on both partitions, and see what that says.

> in menu.lst I need to chose hdX,Y what is X what is Y.
The *X* and *Y* are **numbers.**
*X* represents the *disk* number, and starts counting from **0** (not 1). So, *"(hd0)"* will be your first harddisk (i.e., *"sda"*), *"(hd1)"* will be your second harddisk (i.e., *"sdb"*), etc.
*Y* represents the *partition* number, and also starts counting from **0** (not 1). So, *"(hd0,0)"* will be the first partition of your first harddisk (i.e., *"sda1"*), *"(hd0,1)"* will be the second partition of your first harddisk (i.e., *"sda2"*), etc.; *"(hd1,0)"* will be the first partition of your second harddisk (i.e., *"sdb1"*), *"(hd1,1)"* will be the second partition of your second harddisk (i.e., *"sdb2"*), etc.

I apologize for this sort of question but I'm stuck and I can't find nothing about four systems on one PC.

Thanks[/QUOTE]

---

### Post by Qbito on 2008-05-10
Hi thsts my fdisk -l:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf155f155

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8766    70412863+   7  HPFS/NTFS
/dev/sda2            8767       60801   417971137+   f  W95 Ext'd (LBA)
/dev/sda5            8767       15322    52661038+  83  Linux
/dev/sda6           15323       16678    10892038+  82  Linux swap / Solaris
/dev/sda7           16679       28836    97659103+  83  Linux
/dev/sda8   *       28837       59296   244669918+  83  Linux
/dev/sda9           59297       60049     6048441   82  Linux swap / Solaris
/dev/sda10          60050       60801     6040408+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04d004cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           1        8001    7  HPFS/NTFS
/dev/sdb2               2       38913   312560640    f  W95 Ext'd (LBA)
/dev/sdb5               2        8824    70870716    7  HPFS/NTFS
/dev/sdb6            8825       38913   241689861    7  HPFS/NTFS

and that's my menu.lst:

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f4dcd422-f2a0-4151-8f47-7a8828c1566e ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=f4dcd422-f2a0-4151-8f47-7a8828c1566e ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


Can you tell my from fdisk-l where is my Ubuntu Server and which partition I need to chose on menu.lst ?

---

### Post by Pumalite on 2008-05-10
This is not the full output of your menu.lst
Copy and paste here.

---

