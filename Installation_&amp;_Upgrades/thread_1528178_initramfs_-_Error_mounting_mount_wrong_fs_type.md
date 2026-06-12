---
title: "initramfs - Error mounting: mount: wrong fs type"
date: 2010-07-10
forum: Installation &amp; Upgrades
---

### Post by vheilman on 2010-07-10
I can't boot up my laptop. 

It stops at  "initramfs". 

Here's the background. 
The other day everything was running fine. I hadn't updated in about 2 months or so, so I ran update service and it did all it's work and asked if I wanted to reboot. I said "No", and would reboot later.
Before I got a chance to reboot, it was unplugged for a while and the battery dies and shutdown the system. Now, I have errors. I've tried to do some research, but not sure where to go from here.

So, I can boot from a LiveCD and I'm running off the CD drive. 

I tried to open the harddrive and get this: 

+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Here's some of my info below if it helps.

+++++++++++++++++++++++++++++++++++++

ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b297d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6992    56163208+  83  Linux
/dev/sda2            6993        7296     2441849+   5  Extended
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo mount -a
ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0

+++++++++++++++++++++++++++++++++++++++++

I read somewhere that it might be in my device.map that my harddrive is 
listed as raid, and not sata, but I don't know if that applies, or how to check.

What is the next step?

---

### Post by vheilman on 2010-07-10
I found a script that gave me the following info:
What's my next step? 


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   112,326,479   112,326,417  83 Linux
/dev/sda2         112,326,541   117,210,239     4,883,699   5 Extended
/dev/sda5         112,326,543   117,210,239     4,883,697  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        f8c9891b-c55d-4fde-ac81-0a01987b17f2   ext3                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        d7273146-7bf6-44c4-a976-aa6176a4eaea   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

---

### Post by bumanie on 2010-07-10
I think you should go to [here]("http://members.iinet.net.au/~herman546/p10.html#filesystem_check_on_an_ext3_filesystem") and read the section on ext2,3 & 4 filesystems - you may be lucky and find the problem might only be an unclean filesystem, due to unexpected shutdown. Do the filesystem check and then see if that fixes things, if not, follow up any errors that may get listed.

---

### Post by vheilman on 2010-07-10
did some filesystem checks and here is where I am now...
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****

/dev/sda1: ********** WARNING: Filesystem still has errors **********

/dev/sda1: 193828/3514368 files (1.4% non-contiguous), 2476697/14040802 blocks
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda1
Inode 141857 has EXTENTS_FL flag set on filesystem without extents support.               


/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
    (i.e., without -a or -p options)

---

