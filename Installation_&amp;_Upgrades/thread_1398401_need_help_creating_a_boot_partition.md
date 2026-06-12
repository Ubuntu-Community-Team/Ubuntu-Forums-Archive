---
title: "need help creating a boot partition"
date: 2010-02-04
forum: Installation &amp; Upgrades
---

### Post by inoh on 2010-02-04
I am trying to dual boot Vista and Ubuntu 9.10. I had both working fine for a little while, but after upgrading GRUB 2, Vista would not boot.  Could not get past the loading bar.  Tried to use system restore from the recovery cd, files corrupt.  I did a factory restore and had to recover GRUB 2.  Booted Vista one more time and now it wont boot again.  I understand there is a bug with GRUB 2 and HP machines.  I am running a Compaq cq60-215dx.

After looking around the best solution is [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu).

How can I set this up without starting over?


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2d900954

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8365    67191831    7  HPFS/NTFS
/dev/sda2           28982       30401    11406150    7  HPFS/NTFS
/dev/sda3            8500       28800   163067782+  83  Linux
/dev/sda4            8366        8499     1076355    5  Extended
/dev/sda5            8366        8499     1076323+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by oldfred on 2010-02-04
Grub2 does not like to install to a partition but can be forced to install. I did it with the beta and chainbooted into the beta for a while. They say since it links to a file (hard drive address) and if the file gets moved (partition changes or aggressive fscks) for any reason then you will have boot problems. But then you just have to reinstall.

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_PartitionIf](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_PartitionIf) you can boot into your system from the liveCD:
grub-setup --force /dev/sda3
Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea.
Embedding is not possible, GRUB can only be installed in this setup by using blocklists. However blocklists are UNRELIABLE and its use is discouraged.
error: If you really want blocklists, use --force 

Did you check to see if you are running any of the HP software that causes the grub corruption - its not grub but HP writing hidden stuff into the MBR.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)
Except you do want to install to a partition. See notes after version 3 full  chroot.

---

### Post by kansasnoob on 2010-02-04
> **inoh said:**
> I am trying to dual boot Vista and Ubuntu 9.10. I had both working fine for a little while, but after upgrading GRUB 2, Vista would not boot.  Could not get past the loading bar.  Tried to use system restore from the recovery cd, files corrupt.  I did a factory restore and had to recover GRUB 2.  Booted Vista one more time and now it wont boot again.  I understand there is a bug with GRUB 2 and HP machines.  I am running a Compaq cq60-215dx.

After looking around the best solution is [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu).

How can I set this up without starting over?


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2d900954

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8365    67191831    7  HPFS/NTFS
/dev/sda2           28982       30401    11406150    7  HPFS/NTFS
/dev/sda3            8500       28800   163067782+  83  Linux
/dev/sda4            8366        8499     1076355    5  Extended
/dev/sda5            8366        8499     1076323+  82  Linux swap / Solaris

Partition table entries are not in disk order

Revert to legacy grub:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

I'm sure that bug will be fixed in Lucid.

Note: You will have to add Windows to the legacy grub menu.lst.

If you want personalized instructions post the output of the Boot Info Script:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by inoh on 2010-02-04
oldfred: how do i find the HP software that might be causing the problem?

kansasnoob:

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe 
                       /grub/core.img

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2d900954

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   134,383,724   134,383,662   7 HPFS/NTFS
/dev/sda2         465,579,765   488,392,064    22,812,300   7 HPFS/NTFS
/dev/sda3         136,536,435   462,671,999   326,135,565  83 Linux
/dev/sda4         134,383,725   136,536,434     2,152,710   5 Extended
/dev/sda5         134,383,788   136,536,434     2,152,647  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        3CF4EF3CF4EEF6D4                       ntfs                                     
/dev/sda3        58a8117f-abd4-419e-ad7f-e04d9c1a7c3e   ext4                                     
/dev/sda5        9cc85652-54dd-4a4c-a9d5-e10e2ec2b400   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /windows                 fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


=================== sda1: Location of files loaded by Grub: ===================


    .0GB: grub/core.img

=========================== sda3/boot/grub/grub.cfg: ===========================

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
insmod ext2
set root=(hd0,3)
search --no-floppy --fs-uuid --set 58a8117f-abd4-419e-ad7f-e04d9c1a7c3e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
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
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 58a8117f-abd4-419e-ad7f-e04d9c1a7c3e
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=58a8117f-abd4-419e-ad7f-e04d9c1a7c3e ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 58a8117f-abd4-419e-ad7f-e04d9c1a7c3e
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=58a8117f-abd4-419e-ad7f-e04d9c1a7c3e ro single 
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 58a8117f-abd4-419e-ad7f-e04d9c1a7c3e
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=58a8117f-abd4-419e-ad7f-e04d9c1a7c3e ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 58a8117f-abd4-419e-ad7f-e04d9c1a7c3e
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=58a8117f-abd4-419e-ad7f-e04d9c1a7c3e ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 3cf4ef3cf4eef6d4
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=58a8117f-abd4-419e-ad7f-e04d9c1a7c3e /               ext4    errors=remount-ro 0       1
# /windows was on /dev/sda1 during installation
UUID=3CF4EF3CF4EEF6D4 /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# swap was on /dev/sda5 during installation
UUID=9cc85652-54dd-4a4c-a9d5-e10e2ec2b400 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  19 17 0a 00 19 17 0a 00  19 17 0a 00 19 17 0a 00  |................|
00000010  19 17 0a 00 18 16 08 00  18 16 08 00 19 17 0a 00  |................|
00000020  18 16 08 00 18 16 08 00  19 17 0a 00 19 17 0a 00  |................|
00000030  18 16 08 00 18 16 08 00  18 15 0a 00 18 15 0a 00  |................|
00000040  16 15 0a 00 16 15 0a 00  12 0e 06 00 12 0e 06 00  |................|
00000050  11 10 07 00 13 11 08 00  13 11 08 00 14 12 09 00  |................|
00000060  16 14 0d 00 1a 17 11 00  17 18 11 00 19 19 12 00  |................|
00000070  1b 1a 16 00 1d 1c 18 00  1b 1d 18 00 1b 1d 18 00  |................|
00000080  1b 1d 18 00 1c 1e 19 00  1c 1e 19 00 1c 1e 19 00  |................|
00000090  1c 1e 19 00 1c 1e 19 00  1c 1e 19 00 1c 1e 19 00  |................|
000000a0  1c 1e 19 00 1c 1e 19 00  1b 1e 16 00 1b 1e 16 00  |................|
000000b0  19 1b 14 00 19 1b 14 00  15 19 0f 00 13 16 0d 00  |................|
000000c0  10 13 09 00 0f 12 08 00  0f 10 07 00 0e 0f 06 00  |................|
000000d0  11 10 07 00 11 10 07 00  11 10 07 00 11 10 07 00  |................|
000000e0  13 11 08 00 11 10 07 00  10 0f 06 00 11 10 07 00  |................|
000000f0  13 11 08 00 14 12 09 00  15 13 0a 00 17 16 0d 00  |................|
00000100  17 16 0d 00 1a 18 0f 00  17 19 12 00 17 19 12 00  |................|
00000110  17 19 12 00 18 1a 13 00  18 1a 13 00 19 1b 14 00  |................|
00000120  19 1b 14 00 19 1b 14 00  18 1a 13 00 18 1a 13 00  |................|
00000130  18 1a 13 00 18 1a 13 00  18 1a 13 00 18 1a 13 00  |................|
*
00000150  18 1a 13 00 19 1b 14 00  19 1b 14 00 1a 1d 15 00  |................|
00000160  1a 1d 15 00 1a 1d 15 00  1b 1e 16 00 1b 1e 16 00  |................|
00000170  1b 1e 16 00 1a 1d 15 00  1a 1d 15 00 19 1b 14 00  |................|
00000180  19 1b 14 00 19 1b 14 00  18 1a 13 00 18 1a 13 00  |................|
00000190  18 1a 13 00 18 1a 13 00  18 1a 13 00 18 1a 13 00  |................|
*
000001c0  18 1a 13 00 18 1a 13 00  17 19 12 00 18 1a 13 00  |................|
000001d0  18 1a 13 00 18 1a 13 00  18 1a 13 00 18 1a 13 00  |................|
000001e0  18 1a 13 00 18 1a 13 00  19 1c 14 00 18 1a 13 00  |................|
000001f0  19 1c 14 00 18 1a 13 00  16 18 11 00 18 1a 13 00  |................|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb

---

### Post by oldfred on 2010-02-04
There are a variety of programs, now meierfra. has posted a page with many.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)

I was copying comments and saved all these, one prime one - HP Recovery tools and all its software:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct issues with MBR
[http://ubuntuforums.org/showthread.php?t=923576](http://ubuntuforums.org/showthread.php?t=923576)
[http://ubuntuforums.org/showthread.php?t=1344828](http://ubuntuforums.org/showthread.php?t=1344828)
[http://ubuntuforums.org/showthread.php?p=8433673](http://ubuntuforums.org/showthread.php?p=8433673)
Found out today after numerous searches the issue. I found the answer here -- I had heard dynamic disk partioning may be the cause (which I don't have) or virus software (which I removed). I have a Compaq netbook -- HP product. Turns out they have HP Recovery tools that will overwrite parts of the MBR. The thing is, I uninstalled every single piece of their recovery software, sync software, etc, cuz I didn't want any of that crap. I went into services, and lo-and -behold -- there was the hpqwmiex service running. So I disabled it, did the update-grub thing again, logged into Windows then back into Ubuntu, and all is well!
Another windows issue that caused grub2 issues.
Looks like I found the culprit. It was Norton Ghost running in the background, that I had just recently installed. I disabled it during startup through msconfig and no more trouble. 
Thus it seems the my antivirus scans the master boot record and as it finds something strange (Grub), it kind of deletes it and make my Boot bugged.

---

