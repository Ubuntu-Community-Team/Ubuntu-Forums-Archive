---
title: "Boot fails after recompiling custom kernel: Unable to mount root fs on unknown..."
date: 2013-03-05
forum: Installation &amp; Upgrades
---

### Post by metx1 on 2013-03-05
Boot fails after recompiling to a custom kernel (with modules kernel. replacing a precompiled static kernel) in Ubuntu server 12.10 (x64). 


Current boot error message:
[B]
Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
[FONT=arial]Pid: 1, comm: swapper Not tainted 3.2.12 [/FONT][/B]


The simple current and (unique) grub.cfg entry:

> menuentry "Ubuntu 12.10, kernel 3.2.13-custom-std-ipv6-64" {
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  ef29aa38-32ed-41ed-aa21-7b6cd87d0f73
        else
          search --no-floppy --fs-uuid --set=root ef29aa38-32ed-41ed-aa21-7b6cd87d0f73
        fi
                linux   /boot/bzImage-3.2.13-custom-std-ipv6-64 root=/dev/sda1 ro
}

The complete grub.cfg is available here: [http://paste.ubuntu.com/5588079/](http://paste.ubuntu.com/5588079/)


The current boot wide diagnose about, b., file system, id devices, and partitions 
(with bootinforscript project available in sourceforge)

> Boot Info Script 0.61      [1 April 2012]

============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of
    the same hard drive for core.img. core.img is at this location and looks
    in partition 72 for .

sda1: __________________________________________________________________________
File system:       ext4
    Boot sector type:  -
    Boot sector info:
    Mounting failed:   mount: /dev/sda1 already mounted or sda1 busy

sda2: __________________________________________________________________________
File system:       ext4
    Boot sector type:  -
    Boot sector info:
    Operating System:
    Boot files:

sda3: __________________________________________________________________________
File system:       swap
    Boot sector type:  -
    Boot sector info:

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          4,096    40,962,047    40,957,952  83 Linux
/dev/sda2          40,962,048   975,718,399   934,756,352  83 Linux
/dev/sda3         975,718,400   976,764,927     1,046,528  82 Linux swap / Sola$

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL
/dev/sda1    *          4,096      40,962,047     40,957,952    83 Linux
/dev/sda2          40,962,048   975,718,399    934,756,352  83 Linux
/dev/sda3         975,718,400   976,764,927    1,046,528     82 Linux swap / Sola$

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        ef29aa38-32ed-41ed-aa21-7b6cd87d0f73   ext4
/dev/sda2        3117e4d8-aa51-48b4-b1c1-63d452fd5d06   ext4
/dev/sda3        65c83936-878b-4968-a828-704130595036   swap

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/root          /                            ext4       (rw,relatime,errors=remount-ro,user_xattr,barrier=1,data=ordered)
/dev/sda2        /home                    ext4       (rw,relatime,user_xattr,barrier=1,data=ordered)

=============================== StdErr Messages: ===============================

No volume groups found
mdadm: No arrays found in config file or automatically


I can't proceed with any change in config, following other posts and how-to's are always bringing it at the same point. Anyone could help me to solve this issue?


with "head_ack_e"... ><


**SOLVED** following this thread: [http://askubuntu.com/questions/207080/where-to-re-build-kernel-from-in-http-kernel-ubuntu-com-kernel-ppa-mainline](http://askubuntu.com/questions/207080/where-to-re-build-kernel-from-in-http-kernel-ubuntu-com-kernel-ppa-mainline)

Adding only the _installation of headers, kernel and libs .deb generated_

and _moving up the newest entry with the new kernel in the grub order_. 

Finally I got it. ;)

---

### Post by metx1 on 2013-03-06
Unable to boot in grub rescue console is no manner to acces to the server.

grub rescue> set 
grub rescue> root=(hd0,1)
grub rescue> prefix=(hd0,1)/boot/grub

grub rescue> linux (hd0,1)/boot/vmlinuz-3.2.12 root= /dev/sda1 ro
grub rescue>  initrd (hd0,1)/boot/initrd.img-3.2.12   
grub rescue>  boot 

(other attempts including)
insmod part_msdos
insmod ext2
insmod gzio

I'm reciviend the following message:

[B]List of al partitions:
No filesystem could mount root, tried:
Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block(1,0)
Pid: 1, comm: swapper Not tainted 3.2.12[FONT=arial]


[/FONT][/B]This issues are happening in a dedicated server, analyzing the boot with the vKVM service. 

Anyone know the reasons of it, and which would be the exact grub config. to boot properly in the re-compiled kernel? Could be also a problem of the vmlinuz image and the initrd.img ?

Thanks ;)

---

### Post by nasmit on 2013-03-16
hey,

I have the same problem right now. It is not clear how you solved it. I compiled kernel 3.6.0.rc7 and when I try to boot from it, it brings the same error message as you decribed.
I am sick of this and I am doing my project.....pls help.

..nas

---

