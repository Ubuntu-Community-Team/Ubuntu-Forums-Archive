---
title: "Issues with GRUB after _fresh_ install."
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by Sutur on 2007-10-18
I have just managed to install Gutsy Gibbon for the first time.

Installed over a 6.10 version of Ubuntu that was irreparable with GRUB already installed on the MBR.

I receive the following error when I attempt to boot a fresh installation of Gutsy:

```

"Error 15: File not found."
```

Attempting to boot automatically discovered Windows XP gives me this error:

```
"Error 22: No such partition."
```

I believe the menu.lst file inside /boot/grub file points to the correct disks and partitions, so I don't really know where to begin in fixing this problem.

Below is the relevant information from my menu.lst file:

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=62b86a56-af02-4f82-a70e-434694d7cab4 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd3,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=62b86a56-af02-4f82-a70e-434694d7cab4 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd3,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb3
title		Microsoft Windows XP Professional
root		(hd3,2)
savedefault
makeactive
map		(hd0) (hd3)
map		(hd3) (hd0)
chainloader	+1
```

I hope this helps some good Samaritan fix my problem. Really appreciate the volunteer help associated with the Linux community.

Thank you.

---

### Post by Sutur on 2007-10-18
Bump for help.

---

### Post by Sutur on 2007-10-19
Updated:

Tried to re-install GRUB using a few tutorials. Looks like this problem might be more complex than I had anticipated. Does this help anyone?

```
grub> setup (hd3,0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/reiserfs_stage1_5" exists... yes
 Running "embed /boot/grub/reiserfs_stage1_5 (hd3,0)"...  20 sectors are embedd
ed.
succeeded
 Running "install /boot/grub/stage1 (hd3,0) (hd3,0)1+20 p (hd3,0)/boot/grub/sta
ge2 /boot/grub/menu.lst"... failed

Error 6: Mismatched or corrupt version of stage1/stage2

grub> 
```

---

### Post by logos34 on 2007-10-19
you have 4 hard disks?  Which one is set to boot first in the Bios?

post output of:

**sudo fdisk -l**

> Error 6: Mismatched or corrupt version of stage1/stage2
looks like you may want to run [grub-install]("http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html")

Edit: also, you should have installed grub to hd0 (boot drive) rather than hd3,0 (root partition)

---

### Post by Sutur on 2007-10-19
I have 8 drives:
[LIST]
[*]2 IDE HDD
[*]3 SATA HDD
[*]2 IDE DVDRW
[*]1 SATA DVDRW
[/LIST]

Bios will boot the 1st SATA HDD first (hd3 in grub, /dev/sdb1 everywhere else).

After attempting to reinstall grub a second time using the exact same code it succeeded, but it still wouldn't boot either OS. I also tried installing grub to (hd0) but that was also unsuccessful.

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000eb252

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       30401   244196001    b  W95 FAT32

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x55c6484a

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       30401   244196001   83  Linux

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x237c237c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       48640   390700768+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00022990

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12748   102398278+  83  Linux
/dev/sdb2           12749       13131     3076447+  82  Linux swap / Solaris
/dev/sdb3   *       13132       30401   138721275    7  HPFS/NTFS

Disk /dev/sdc: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x237c237d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       48641   390708801   83  Linux
```

---

### Post by logos34 on 2007-10-19
ok, try this:

on the grub menu screen highlight the gustsy kernel and press 'e' to edit...hit 'e' again on 'root' line and change to '(hd**[COLOR="Red"]0[/COLOR]**,0)'. Then press 'enter' and 'b' to boot.

anything?

---

### Post by Sutur on 2007-10-19
Yep that's the ticket - well done mate!

So what was I doing wrong? And how can I fix it permanently?

---

### Post by logos34 on 2007-10-19
gksudo gedit /boot/grub/menu.lst

>change all instances of (hd3,0) to (hd0,0)

change windows to:
> 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb3
title		Microsoft Windows XP Professional
root		(hd**0**,2)
savedefault
makeactive
chainloader	+1

---

### Post by Sutur on 2007-10-19
Thank you!

---

