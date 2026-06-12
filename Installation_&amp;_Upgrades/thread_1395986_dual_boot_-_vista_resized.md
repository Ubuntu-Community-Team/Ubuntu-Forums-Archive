---
title: "dual boot - vista resized"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by senchan on 2010-02-01
ok after installing ubuntu on another partition, i couldn't boot my vista and reinstalling grub and recovering bootmbr didn't help, it still gets booted but freezes just after loading screen or sometimes a little after..

so the only guess is that the partition vista is on has been resized..so i've read all about gparted and how to resize partitions, but what bothers me is - **how do i know the original size of the vista partition?** i mean what good is resizing it again if I don't know how much space it had before? help please

---

### Post by QIII on 2010-02-01
When you initially installed the dual boot configuration, did you first defrag Vista (a couple of times is best) and then use the utilities in Vista itself to resize the Vista partition?

---

### Post by senchan on 2010-02-01
> **QIII said:**
> When you initially installed the dual boot configuration, did you first defrag Vista (a couple of times is best) and then use the utilities in Vista itself to resize the Vista partition?

How to defrag or use utilities when i can't even start vista properly?

---

### Post by QIII on 2010-02-01
That would difficult now, of course.  

The question referred to how it was installed initially, since that may bear on the approach to resolving the issue.

---

### Post by senchan on 2010-02-01
> **QIII said:**
> That would difficult now, of course.  

The question referred to how it was installed initially, since that may bear on the approach to resolving the issue.

Ubuntu was installed on D partition when Vista was already working on C partition. 
So Vista was installed way before Ubuntu, as you may have already concluded.

Anyway, I could boot Vista from DVD, and defragment the disk from there, but I won't do it unless you are positive it would solve the problem? Because if the partition got resized I don't have the feeling that defragmenting would help..as it was said before - resizing the partition back to it's original size would definitely help, but, I repeat, I don't know what that original size was. Format and reinstall vista or someone has a better idea?

Or should I just resize it to something like 65 GB because I know that it wasn't bigger than that? Wouldn't that screw up the D partition (and ubuntu) the same way the C got screwed up?

---

### Post by darkod on 2010-02-01
What do you mean ubuntu installed on D: partition? Linux partitions are not recognized by windows and as such don't have letters assigned to them.
Did you actually install wubi on D:? That should be specified because it's not the same and someone reading this should know.
For example, if you did install wubi and you tried some procedure to reinstall grub to the MBR as you said, you were NOT supposed to do that. With wubi you DO NOT have grub on the MBR.
Also, if you used wubi, any corruption of the vista partition is hardly related with it. It's working from within windows itself.

---

### Post by senchan on 2010-02-01
> **darkod said:**
> What do you mean ubuntu installed on D: partition? Linux partitions are not recognized by windows and as such don't have letters assigned to them.
Did you actually install wubi on D:? That should be specified because it's not the same and someone reading this should know.
For example, if you did install wubi and you tried some procedure to reinstall grub to the MBR as you said, you were NOT supposed to do that. With wubi you DO NOT have grub on the MBR.
Also, if you used wubi, any corruption of the vista partition is hardly related with it. It's working from within windows itself.

well, I am confused by this post. what is wubi? i'm a noob.
but to make this easier for you to understand - when i cd to host and do ls command then i see all the contents of my former D partition that was on windows. so that means it is on D, so to speak

---

### Post by oldfred on 2010-02-01
We are confused too. It may be best to run this script to document your configuration. (This is the same script darko has in his signature)


Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by senchan on 2010-02-01
:D

Ok, here it is.

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /grldr /ntldr /NTDETECT.COM /wubildr.mbr

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbf8550f6

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     8,177,084     8,177,022  12 Compaq diagnostics
/dev/sda2    *      8,177,085   120,792,734   112,615,650   7 HPFS/NTFS
/dev/sda3    *    120,792,735   234,436,544   113,643,810   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4060 MB, 4060086272 bytes
255 heads, 63 sectors/track, 493 cylinders, total 7929856 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *            128     7,929,855     7,929,728   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       bbf36969-f95e-47a5-9829-a54908e203ad   ext4                                     
/dev/sda1        0E4E-05CE                              vfat       PQSERVICE                     
/dev/sda2        1440AC2B40AC1590                       ntfs                                     
/dev/sda3        9FFB-3ED0                              vfat       ACERDATA                      
/dev/sdb1        A220E47D20E45A35                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro)
/dev/sda3        /host                    vfat       (rw)
/dev/sda2        /media/windows           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda3        /D                       vfat       (rw,iocharset=utf8,umask=000)
/dev/sdb1        /media/A220E47D20E45A35  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


======================== sda3/Wubi/boot/grub/menu.lst: ========================

title "Windows Vista"
root (sd0,0)
chainloader +1
boot 


======================== sda3/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
    insmod fat
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 9ffb-3ed0
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-17-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
    insmod fat
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 9ffb-3ed0
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-17-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
    insmod fat
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 9ffb-3ed0
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
    insmod fat
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 9ffb-3ed0
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
    insmod fat
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 0e4e-05ce
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 1440ac2b40ac1590
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda3/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
/host/ubuntu/disks/root.disk / ext4 loop,errors=remount-ro 0 1
/host/ubuntu/disks/swap.disk none swap loop,sw 0 0
/dev/sda2 /media/windows ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda3 /D vfat iocharset=utf8,umask=000 0 0

```

---

### Post by darkod on 2010-02-01
Disk /dev/sda: [COLOR=Red]120.0 GB[/COLOR], 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbf8550f6

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     8,177,084     8,177,022  12 Compaq diagnostics
/dev/sda2    *      8,177,085   120,792,734 [COLOR=Red]  112,615,650[/COLOR]   7 HPFS/NTFS
/dev/sda3    *    120,792,735   234,436,544 [COLOR=Red]  113,643,810[/COLOR]   c W95 FAT32 (LBA)

You have a 120GB hdd, and on top of the compaq partition you have one ntfs partition of approx 54GB, and one fat32 partition of 54GB. Together with the compaq partition that makes all of your 120GB disk, or more precisely 111.9GiB (real gigabytes).

What is missing?

---

### Post by senchan on 2010-02-01
> **darkod said:**
> Disk /dev/sda: [COLOR=Red]120.0 GB[/COLOR], 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbf8550f6

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     8,177,084     8,177,022  12 Compaq diagnostics
/dev/sda2    *      8,177,085   120,792,734 [COLOR=Red]  112,615,650[/COLOR]   7 HPFS/NTFS
/dev/sda3    *    120,792,735   234,436,544 [COLOR=Red]  113,643,810[/COLOR]   c W95 FAT32 (LBA)

You have a 120GB hdd, and on top of the compaq partition you have one ntfs partition of approx 54GB, and one fat32 partition of 54GB. Together with the compaq partition that makes all of your 120GB disk, or more precisely 111.9GiB (real gigabytes).

What is missing?

Well yes, my disk is 120GB.
But according to this I have one of 112GB and one of 113GB :S Or am I reading this wrong? Although it looks fine as you described it, but I don't understand where u got the 54GB figures from..btw when i mounted the "c" partition, it's name is "58GB filesystem"..so could it be the partition got enlarged for 4 GB?

---

### Post by darkod on 2010-02-01
Units = sectors of 1 * 512 = 512 bytes

One unit is 512B or 0.5KB. So 112mil units don't make 112GB, they make approx half of that or 54GB.

Don't worry about small differences like 54 or 58, it all depends on that difference between gigabytes as 1,000,000,000 bytes, or real gigabyte in computer terms (binary) which are 1024x1024x1024 bytes. Your partitions seem to be there and working fine.

---

### Post by senchan on 2010-02-01
so the problem is in grub in your opinion?

---

### Post by oldfred on 2010-02-01
Because you have the wubi install you still boot with windows in the MBR then if you choose ubuntu grub takes over. So if you cannot even get to the choice of windows or ubuntu you need to reinstall the Vista boot loader with your Vista CD.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

There has been an issue with grub and wubi:

Fix for grub2 problem with wubi - you may want to download this also
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

