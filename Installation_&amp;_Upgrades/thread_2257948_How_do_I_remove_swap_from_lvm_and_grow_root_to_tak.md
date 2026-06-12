---
title: "How do I remove swap from lvm and grow root to take its place"
date: 2014-12-23
forum: Installation &amp; Upgrades
---

### Post by lance bermudez on 2014-12-23
I'm using Lubuntu. How do I remove my swap and make my root partion grow to take its place? Both are on the same drive and are under an encrypted lvm. I can not use sudo /usr/bin/system-config-lvm it crashes after I open it with this 
```
:~$ sudo /usr/bin/system-config-lvm
/usr/share/system-config-lvm/system-config-lvm.py:53: Warning: Attempt to add property GnomeProgram::sm-connect after class was initialised
  gnome.program_init (PROGNAME, VERSION)
/usr/share/system-config-lvm/system-config-lvm.py:53: Warning: Attempt to add property GnomeProgram::show-crash-dialog after class was initialised
  gnome.program_init (PROGNAME, VERSION)
/usr/share/system-config-lvm/system-config-lvm.py:53: Warning: Attempt to add property GnomeProgram::display after class was initialised
  gnome.program_init (PROGNAME, VERSION)
/usr/share/system-config-lvm/system-config-lvm.py:53: Warning: Attempt to add property GnomeProgram::default-icon after class was initialised
  gnome.program_init (PROGNAME, VERSION)
The program 'system-config-lvm.py' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 2459 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

:~$ sudo fdisk -l
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000eea0d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758  1953523711   976510977    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5          501760  1953523711   976510976   83  Linux

Disk /dev/mapper/sda5_crypt: 999.9 GB, 999945142272 bytes
255 heads, 63 sectors/track, 121569 cylinders, total 1953017856 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/sda5_crypt doesn't contain a valid partition table

Disk /dev/mapper/lubuntu--vg-root: 994.6 GB, 994565947392 bytes
255 heads, 63 sectors/track, 120915 cylinders, total 1942511616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/lubuntu--vg-root doesn't contain a valid partition table

Disk /dev/mapper/lubuntu--vg-swap_1: 5330 MB, 5330960384 bytes
255 heads, 63 sectors/track, 648 cylinders, total 10412032 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/lubuntu--vg-swap_1 doesn't contain a valid partition table

:~# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/lubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=8e630976-83dc-44bf-8139-06f2fe25e8d6 /boot           ext2    defaults        0       2
/dev/mapper/lubuntu--vg-swap_1 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0


:~# pvdisplay
  --- Physical volume ---
  PV Name               /dev/mapper/sda5_crypt
  VG Name               lubuntu-vg
  PV Size               931.27 GiB / not usable 2.00 MiB
  Allocatable           yes 
  PE Size               4.00 MiB
  Total PE              238405
  Free PE               11
  Allocated PE          238394
  PV UUID               q7ES2Q-Sbg6-0Itt-dW1j-gftZ-qi3Y-NY1EXH

:~# vgdisplay
  --- Volume group ---
  VG Name               lubuntu-vg
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               1
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               931.27 GiB
  PE Size               4.00 MiB
  Total PE              238405
  Alloc PE / Size       238394 / 931.23 GiB
  Free  PE / Size       11 / 44.00 MiB
  VG UUID               1wfbpf-QZX3-JBi8-xUUf-WKF5-MKUB-uu9ZnF

:~# lvdisplay
  --- Logical volume ---
  LV Path                /dev/lubuntu-vg/root
  LV Name                root
  VG Name                lubuntu-vg
  LV UUID                W0RADw-9s7P-AZGa-2z5B-cmqN-akBO-W1Fbkc
  LV Write Access        read/write
  LV Creation host, time lubuntu, 2014-12-15 11:45:38 -0700
  LV Status              available
  # open                 1
  LV Size                926.26 GiB
  Current LE             237123
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1
   
  --- Logical volume ---
  LV Path                /dev/lubuntu-vg/swap_1
  LV Name                swap_1
  VG Name                lubuntu-vg
  LV UUID                xjc17a-xgEQ-4WZ8-17wd-7dW9-mJUb-FnJdyi
  LV Write Access        read/write
  LV Creation host, time lubuntu, 2014-12-15 11:45:39 -0700
  LV Status              available
  # open                 0
  LV Size                4.96 GiB
  Current LE             1271
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:2
```

---

### Post by nerdtron on 2014-12-23
It's really hard to read the text without the [noparse]```
 and code here between tags 
``` [/noparse] code tags.

Anyway the first step here I think is to disable the swap so that you can reclaim the space you assigned it.

---

### Post by MAFoElffen on 2014-12-24
> **nerdtron said:**
> Anyway the first step here I think is to disable the swap so that you can reclaim the space you assigned it.
1000's of ways to do the same thing. I would do the same with a differing perspective.

Maybe just me, but I think it's makes sense to get something defined and working before you do away with the old completely. That way you still have a fallback to recover to. True, it will do fine without a swap, but just good practices.

So following that logic, if you define a new swap partition (sounded like it was going to be elsewhere)... comment out the old line for the swap mount fstab file and add the new line pointing to the new swap... Test to make sure it's working. When it is, then remove the old swap and then grow the root. A stystem will run better with swap on a faster, separate disk.

But if I read that differently... then it reads as it you are doing with your swap altogether. (Even Win OS'es use virtual memory...) Swap is usually 1.5 times the installed memory. It will run without, but I find it runs better with. Swap is used if you exceed the installed memory and when it goes into a hibernation or sleep state. It writes everything from RAM to disk, so that it can shut down and return to that same state, previous to that, again.

It you still want to do that... Then the previous post. Remove the line in the fstab. Remove the LVM swap vg. Grow the root vg. Then you can reboot... it will have LVM errors if you don't go through that all in that logical order.

---

### Post by lance bermudez on 2014-12-24
I have turned off the swap so now how do I make root grow to take it place? what the the command?

---

