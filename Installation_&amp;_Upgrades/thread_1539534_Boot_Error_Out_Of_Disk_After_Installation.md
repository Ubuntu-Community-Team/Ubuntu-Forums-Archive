---
title: "Boot Error Out Of Disk After Installation"
date: 2010-07-26
forum: Installation &amp; Upgrades
---

### Post by DuckyVader on 2010-07-26
I just installed Ubuntu Linux 10.04 from the live disk, but after I tried to boot up I got a message saying Error out of disk. I don't really know why it's telling me this, if it's telling me about my disk space, I think I have enough. It's a 250gb hardrive. When I installed ubuntu I put the option to just erase the entire disk and install. 

This is what I get when I execute sudo fdisk -l:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00024db1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29700   238557184   83  Linux
/dev/sda2           29700       30402     5639169    5  Extended
/dev/sda5           29700       30402     5639168   82  Linux swap / Solaris


I really have no idea what the problem is. I would really appreciate it if somebody could push me in the right direction. Thanks.

---

### Post by ldouble_e on 2010-07-27
I'm having the same issue and no one here has the ability to fix it unfortunately. I'm still working on the issue feverishly. Basically I'm teaching myself how to build an OS so  can figure this out. I'll let you know if I solve it.

Everthing is there and it is not a disk issue as far as size. It's a bug in the coding as far as I can tell. Under /usr/lib/grub/grub-mkconfig_lib
```
# If there's a filesystem UUID that GRUB is capable of identifying, use it;
    # otherwise set root as per value in device.map.
    echo "set root=`${grub_probe} --device ${device} --target=drive`"
    if fs_uuid="`${grub_probe} --device ${device} --target=fs_uuid 2> /dev/null`" ; then
       echo "search --no-floppy --fs-uuid --set ${fs_uuid}"
    fi

```

The "search --no-floppy" portion being deleted sometimes solves the problem. 

Another place to try is /etc/grub.d/10_linux
Find the lines:
```
recordfail=1
if [-n ${have_grubenv}]
```
and comment them out by placing a "#" in front of them like so.
```
#recordfail=1
#if [-n ${have_grubenv}]
```
then save and close it out. To save you must be root. to open the files mentioned use 

```
gksudo gedit /etc/grub.d/10_linux
gksudo gedit /usr/lib/grub/grub-mkconfig_lib
```

If these don't work you are in my boat. Updating or repairing the grub won't help and that is all the info most people will give you.

---

### Post by DuckyVader on 2010-07-27
Tried both those things. Didn't work. Thanks for trying to help. 'ma put down a little more about what's going on my laptop. Ok when I go to Places>Computer I have 3 Icons. First one says **250GB Hard Disk: 244GB File System**. The second one says **CD/DVD Drive**. The third one says **File System**. When I try to double click on the first one it shows up a window that says:

**Unable to mount location**

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


When I typed in "dmesg | tail" in Terminal I get this:

[ 4000.071411] sd 1:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4000.071415] sd 1:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
[ 4000.071418] Descriptor sense data with sense descriptors (in hex):
[ 4000.071420]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 4000.071427]         00 00 08 60 
[ 4000.071431] sd 1:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 4000.071436] sd 1:0:0:0: [sda] CDB: Read(10): 28 00 00 00 08 60 00 00 08 00
[ 4000.071443] end_request: I/O error, dev sda, sector 2144
[ 4000.071454] ata2: EH complete
[ 4000.071466] EXT4-fs (sda1): can't read group descriptor 11



I don't know what this means. Also why would their be 2 File Systems? Right now I'm using Ubuntu from my SD memory card, that's how I booted up. But I installed it using a live disk. So is the third icon that just says File System from the memory card?

---

### Post by ldouble_e on 2010-07-27
You might want to try this link. [http://ezinearticles.com/?Resolving-Mount---Wrong-fs-Type-Error-in-Ext4-Linux-File-System&id=3635354](http://ezinearticles.com/?Resolving-Mount---Wrong-fs-Type-Error-in-Ext4-Linux-File-System&id=3635354)

It will give you something to try anyway. I'm still not finding anything on my end, although I feel I may be close.

---

### Post by oldfred on 2010-07-27
Some more things to try:

[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Part of testdisk which is in the repositories or most recovery CDs. 
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)
[http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html](http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html)
[http://ubuntuforums.org/showthread.php?t=1443110](http://ubuntuforums.org/showthread.php?t=1443110)

---

### Post by DuckyVader on 2010-07-28
Ok, I got it to go into Grub Rescue mode I'm guessing. When I try to boot, it says disk error grub rescue and it lets me type commands. Now I went to the grub rescue ubuntu web page here: [https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode) on the part where it says 
**Grub  shows rescue prompt (and does not continue to boot)**

You may have a buggy bios and the location of your /boot/* files is not  under the 1024 cylinder boundary. Create a small partition on the  beginning of the disk, mount it as /mnt/b, cp -av /boot/* /mnt/b; umount  /mnt/b; mount /dev/small_partition /boot; grub-install  /dev/<device>. 


Can anybody tell me exactly how to do this? I created a small partition with gparted, and I go into Disk Utility and I see the partition I made, do I make it an ext4 type or what? And how do I mount it exactly as it says above?

---

### Post by confused57 on 2010-07-28
> **DuckyVader said:**
> Ok, I got it to go into Grub Rescue mode I'm guessing. When I try to boot, it says disk error grub rescue and it lets me type commands. Now I went to the grub rescue ubuntu web page here: [https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode) on the part where it says 
**Grub  shows rescue prompt (and does not continue to boot)**

You may have a buggy bios and the location of your /boot/* files is not  under the 1024 cylinder boundary. Create a small partition on the  beginning of the disk, mount it as /mnt/b, cp -av /boot/* /mnt/b; umount  /mnt/b; mount /dev/small_partition /boot; grub-install  /dev/<device>. 


Can anybody tell me exactly how to do this? I created a small partition with gparted, and I go into Disk Utility and I see the partition I made, do I make it an ext4 type or what? And how do I mount it exactly as it says above?

Those instructions are rather hard to follow, but the easiest way would be to reinstall Ubuntu, select "Manual" partitioning, then just install on the partitions you already have:
1.)Small partition at beginning of drive:
   Mountpoint - /boot
   Format as  - ext3
   Use as  -  primary partition

2.)Second partition(that you already have):
   Mountpoint - /
   Format as  - ext4(or ext3)
   Use as   -  primary partition

3.)Third partition:
   Mountpoint - swap
   Logical partition
   (you shouldn't need to fill in anything else
    for making this swap).

You should end up with:
sda1  -  small /boot partition at beginning(approx. 500 Mb should be enough)
sda2  -  / (root partition)
sda3  -  Extended partition
sda5  -  swap partition located within ext3 extended

---

### Post by drs305 on 2010-07-28
I wrote most of the community doc you referenced, but don't think I authored the 'buggy BIOS' section. While that could be the cause, it would be most likely with an older computer. 

I'd try the steps in the same document on trying to boot from the grub rescue prompt, if you aren't successful, before going to the effort of repartitioning your system, I'd recommend running the boot info script by *meierfra* so we can see what the status of your system is. You can run the script after booting from the LiveCD and opening a terminal via Applications, Accessories, Terminal.

[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

Copy the RESULTS in a post here, between 'code' tags. You generate the tags by pressing the # icon in the post's menu.

---

### Post by DuckyVader on 2010-07-28
Ok thanks confused57 I'ma try that a little later.

I used boot info script, this is my results:

```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   464,712,317   464,712,255   c W95 FAT32 (LBA)
/dev/sda2         477,118,462   488,396,799    11,278,338   5 Extended
/dev/sda5         477,118,464   488,396,799    11,278,336  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2041 MB, 2041577472 bytes
61 heads, 60 sectors/track, 1089 cylinders, total 3987456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *            247     3,987,455     3,987,209   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        03b4ffcf-4829-40ce-93b0-85cc642d3e3c   ext4       New Volume                    
/dev/sda2: PTTYPE="dos" 
/dev/sda5        f243339c-0e49-4bf0-89e4-9f42c093c857   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        FE3F-8FA4                              vfat       NIKON D40                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/New Volume        ext4       (rw,nosuid,nodev,uhelper=udisks)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  2a c6 cd af d1 7f 65 f0  2d b6 db a3 df bf e1 6f  |*.....e.-......o|
00000010  ed 2d d0 25 8c c6 d4 47  9d e7 e2 da 5f 00 9d ef  |.-.%...G...._...|
00000020  72 e9 3c 77 b2 38 be 16  4a bf ac 6a 91 ed d0 8b  |r.<w.8..J..j....|
00000030  bd 5c ab dd 60 0f a5 f2  e4 17 e4 20 77 20 94 91  |.\..`...... w ..|
00000040  83 dc 1c 91 91 83 f8 c2  28 91 ff 9d ac fc ef 1c  |........(.......|
00000050  29 ff 3b e6 fc ca 02 91  f7 e3 ac bc 1f 1f 29 ef  |).;...........).|
00000060  c7 e6 bc d1 9a ce 73 8b  69 95 75 2e b1 94 46 7a  |......s.i.u...Fz|
00000070  8d 7e 32 27 75 c1 f0 a0  b3 87 07 9d 42 50 29 8e  |.~2'u.......BP).|
00000080  96 f6 36 5a 1b 09 3a 43  04 9d 71 a9 7f 91 d8 e4  |..6Z..:C..q.....|
00000090  aa 93 29 5d 22 25 e0 15  7f 15 5e b1 07 4c 66 25  |..)]"%....^..Lf%|
000000a0  b1 dd e5 bc 5e 99 ca 96  be 7c c4 4f b0 4b 75 48  |....^....|.O.KuH|
000000b0  c0 15 5b d0 01 5c 81 53  84 43 66 33 84 d9 99 eb  |..[..\.S.Cf3....|
000000c0  37 1b 92 8b 0a ac 0b 61  7d 96 68 30 dc 33 eb f6  |7......a}.h0.3..|
000000d0  3e 3f 95 3c 34 49 bf bc  f0 4a 2e 87 f3 09 5c cf  |>?.<4I...J....\.|
000000e0  e3 1d b0 d4 52 91 0d fe  73 07 0a 46 d9 0f 39 eb  |....R...s..F..9.|
000000f0  7b 88 47 f5 14 d8 0f 0d  14 d4 cb 07 8e b6 65 be  |{.G...........e.|
00000100  06 0a 66 d8 0f 11 b7 1d  d5 6b 9b d9 53 d0 d8 79  |..f......k..S..y|
00000110  36 b1 cf 81 82 e2 46 43  da cc 9b d3 53 90 da cb  |6.....FC....S...|
00000120  d2 b0 dd 26 a5 e1 53 ac  90 86 5f 06 87 8f 14 56  |...&..S..._....V|
00000130  03 fe 30 75 12 57 56 8b  6f 8c 87 df 2c 13 fb 39  |..0u.WV.o...,..9|
00000140  c2 84 0b 1b 2d 99 32 3c  39 65 78 8e 54 86 c7 5c  |....-.2<9ex.T..\|
00000150  86 72 99 9e df 9f 93 df  7f a4 fc 7e 73 fe e8 37  |.r.........~s..7|
00000160  3b cf 29 56 5c 7c e3 54  51 4f c1 9c 46 fa 8c 7e  |;.)V\|.TQO..F..~|
00000170  38 28 0f 28 ed 82 77 b6  a3 26 48 59 3e 27 c1 1f  |8(.(..w..&HY>'..|
00000180  2c 2c b5 93 44 0f eb 56  c4 8b 03 4d 6d 03 05 b5  |,,..D..V...Mm...|
00000190  b3 07 1a ad a3 1a 1b 7b  69 78 1a 7b 1a d3 8d ea  |.......{ix.{....|
000001a0  a6 0d da 98 46 1a b6 c6  c3 f5 34 6a 32 84 ef 98  |....F.....4j2...|
000001b0  d6 3f f2 fd e7 36 3a 21  68 50 c8 61 75 93 00 fe  |.?...6:!hP.au...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 18 ac 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```Wow messy. So on the sda1 part, it looks like I don't even have linux installed.0.o?

---

### Post by drs305 on 2010-07-28
I've spent the last few minutes trying to decipher your sda1, apparently with about as much success as Grub and the boot info script.  ;-)

Your sda1 shows:

> sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   


While a normal install would look like:
>   File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img


What concerned me about your results, other than there appears to be no OS on sda1, is that it is reported as ext4 in several places but also at one point as FAT32.

Since you say you got to a grub rescue prompt, it *should* mean that Grub knows about your installation but can't boot to it. That's actually a better result than a straight "grub" prompt, when Grub simply has no clue at all. Although it appears you have no OS or boot files, "grub rescue" may mean you really do. 

At this point, I'd recommend you reinstall Grub2 from the Live CD and see if it restores things. I really don't know if it will work with the format discrepancy and RESULTS.txt anomolies, but it's probably your best and quickest solution.

Boot to the LiveCD desktop, mount your sda1 *partition* and install to the *sda* device.
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Then reboot and see if it now boots.

If it doesn't, I would probably wait to see if someone comes up with another recommendation. If not or if you want to get your system running as quickly as possible, I'd probably reinstall since this is a new install and you probably haven't spent any time yet tweaking things.

---

### Post by confused57 on 2010-07-28
The bootinfo script does reveal quite a bit about a system. If you do decide to reinstall, you shouldn't need a separate /boot partition, unless you have a really old computer, as drs305 mentioned.

---

### Post by DuckyVader on 2010-07-28
Ok yeah I really haven't changed anything so i'ma just go ahead and reinstall with manual partitioning.

Ok so the first partition should be 500MB. How much for the 2nd and 3rd?

---

### Post by confused57 on 2010-07-28
> **DuckyVader said:**
> Ok yeah I really haven't changed anything so i'ma just go ahead and reinstall with manual partitioning.

Ok so the first partition should be 500MB. How much for the 2nd and 3rd?
Ignore the instructions I gave you in my other post.  Here's a guide for partitioning basics:
[http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning](http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning)

Everyone has their personal preferences & needs for a partition scheme.  If it were my system, here's how I'd proceed:
   Open the disk partitioner(gparted) & delete the partitions you have.  Then select "Manual" partitioning and set up the following partitions:
1.) Primary partition
    ext4
    mountpoint /  
    10 Gb

2.) Primary partition
    ext3  (or ext4)
    mountpoint /home
    20 Gb

3.) Logical partition
    swap
    probably 2 Gb or more(since you have a laptop & may need extra for hibernation). 

4.) Logical partition
    Mountpoint:  /media/Data(you can change Data to whatever you want to call your "data" partition.
    ext3
    Allot rest of drive for this partition.

You may need to create an Extended partition, before you can make any logical partitions inside it.

I may have overlooked something, but this is basically the way I would set up a system, and you may want to wait on someone else to give you some other ideas.  Having only 10 Gb for your root would solve any bios restrictions, rather than having a small /boot partition, if this possibly caused your initial problems.

You should probably need only 1-1.5 Gb swap, if you have a desktop pc.

---

