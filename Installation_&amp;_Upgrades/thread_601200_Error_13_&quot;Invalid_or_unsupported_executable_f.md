---
title: "Error 13: &quot;Invalid or unsupported executable format&quot;"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by robinlee_r on 2007-11-03
Hi 

I have run into this problem, where I have this machine, with 3 drives, being the master hd0, second drive is hda, there is another under sda, this one is the one that contains the instance of Ubuntu 7.04, I went with the manual install option when it came to select the partition to install the software (master is an instance of suse 10.2), now after ubuntu installs, I go ahead and select the entry ubuntu from grub, whis is allocated unser /dev/sda5,but I keep getting the following error:

Error 13: "Invalid or unsupported executable format"

I have checked the menu.lst on the ubuntu instance, and I had to fix. the root partition was poiting to /dev/sda4 instead of 5, but even afetr that I keep getting the same error, I also tried changing the line rootnoverify from hd0,0 to hd1,0, hd1, hd2 but nothing.

Could somebody help out?
Thanks on advance

Robin

cat /boot/grub/menu.lst
# Modified by YaST2. Last modification on Thu Nov  1 21:55:54 EDT 2007
default 2
timeout 8
##YaST - generic_mbr
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 10.2
    kernel (hd0,3)/boot/vmlinuz root=/dev/disk/by-label//1 resume=/dev/hda3 splash=silent showopts
    initrd (hd0,3)/boot/initrd-2.6.18.8-0.5-default

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 10.2
    kernel (hd0,3)/boot/vmlinuz root=/dev/disk/by-label//1 showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off 3
    initrd (hd0,3)/boot/initrd-2.6.18.8-0.5-default

title openSUSE 10.2 - 2.6.18.8-0.5
    kernel (hd0,3)/boot/vmlinuz-2.6.18.8-0.5-default root=/dev/disk/by-label//1 resume=/dev/hda3 splash=silent showopts
    initrd (hd0,3)/boot/initrd-2.6.18.8-0.5-default

title Failsafe -- openSUSE 10.2 - 2.6.18.8-0.5
    kernel (hd0,3)/boot/vmlinuz-2.6.18.8-0.5-default root=/dev/disk/by-label//1 showopts ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off
    initrd (hd0,3)/boot/initrd-2.6.18.8-0.5-default

title suse 10.2 64
    rootnoverify (hd0,0)
    chainloader (hd1,1)+1

title Centos 4
    rootnoverify (hd0,0)
    chainloader (hd0,1)+1

title Fedora 7
    rootnoverify (hd0,0)
    chainloader (hd1,2)+1

title ubuntu
    rootnoverify (hd0,0)
    chainloader (hd1,4)+1
Suse102:/boot/grub #                                            




Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1            5951       17000    88759125    c  W95 FAT32 (LBA)
/dev/hda2               1        1275    10241406   83  Linux
/dev/hda3            1276        1466     1534207+  82  Linux swap / Solaris
/dev/hda4   *        1467        5950    36017730   83  Linux

Partition table entries are not in disk order

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       15701   126118251   83  Linux
/dev/sda2   *       15702       16485     6297480   83  Linux
/dev/sda3           16486       17601     8964270   83  Linux
/dev/sda4           17602       38913   171188640    f  W95 Ext'd (LBA)
/dev/sda5           17602       18717     8964238+  83  Linux

Disk /dev/hde: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1        4865    39078081    7  HPFS/NTFS
Suse102:~ #

---

### Post by fdv1 on 2007-11-03
I can only point you to this, it seems the most logical explanation:
[http://ubuntuforums.org/showthread.php?t=282545](http://ubuntuforums.org/showthread.php?t=282545)

---

