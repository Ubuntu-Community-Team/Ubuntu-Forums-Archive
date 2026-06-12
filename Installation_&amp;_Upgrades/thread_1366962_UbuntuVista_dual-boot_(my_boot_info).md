---
title: "Ubuntu/Vista dual-boot (my boot info)"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by DecioSP on 2009-12-29
I am still having problems with ubuntu/vista dual boot.
Since I read the instructions of some users about the sudo bash ~/Desktop/boot_info_script*.sh
So I did the command in order to try to fix this problem that are lasting for more than 15 days.
Tried to reinstall, reformat, etc. with no success at all, so if someone could help me here I would be grateful. 


```
============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub 1.97
    Boot sector info:  Grub 1.97 is installed in the boot sector of sda1 and 
                       looks at sector 1322472136 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 1.97
    Boot sector info:  Grub 1.97 is installed in the boot sector of sda3 and 
                       looks at sector 1322594472 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #3 for /boot/grub.
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb6: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1 1,465,149,167 1,465,149,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1              34       262,177       262,144 Microsoft Windows
/dev/sda2         264,192 1,317,691,375 1,317,427,184 Linux (usually)
/dev/sda3   1,317,691,376 1,343,082,001    25,390,626 Linux (usually)
/dev/sda4   1,343,082,002 1,351,480,439     8,398,438 Linux Swap
/dev/sda5   1,351,480,440 1,445,617,158    94,136,719 Linux (usually)
/dev/sda6   1,445,617,159 1,465,148,409    19,531,251 Linux (usually)

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4f1e321c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   204,802,047   204,800,000   7 HPFS/NTFS
/dev/sdb2         204,802,048   206,850,047     2,048,000   7 HPFS/NTFS
/dev/sdb3         206,850,048   309,250,047   102,400,000   7 HPFS/NTFS
/dev/sdb4         309,250,048 1,953,533,951 1,644,283,904   f W95 Ext d (LBA)
Invalid MBR Signature found
/dev/sdb5     ?   443,440,447 4,620,444,349 4,177,003,903  7f Unknown
/dev/sdb6     ?   401,491,834 1,168,853,880   767,362,047  5f Unknown

/dev/sdb4 ends after the last sector of /dev/sdb
/dev/sdb5 ends after the last sector of /dev/sdb
the logical partition /dev/sdb5 is not contained in the extended partition /dev/sdb4
/dev/sdb5 overlaps with /dev/sdb6
/dev/sdb6 ends after the last sector of /dev/sdb

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda2: UUID="8284E30784E2FC93" TYPE="ntfs" 
/dev/sda3: UUID="7102d01b-2d4e-4b00-8542-792f3942f123" TYPE="ext4" 
/dev/sda4: UUID="fadb5492-eb15-42f1-9c39-39478d3385ba" TYPE="swap" 
/dev/sda5: UUID="6092bae9-6a57-4727-a0ed-0f3e7738848c" TYPE="ext4" 
/dev/sda6: UUID="6c6eedbd-4f91-4cc7-8497-fd6424f12bf5" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb: TYPE="isw_raid_member" 
/dev/sdc: TYPE="isw_raid_member" 
/dev/mapper/isw_bejagaacfi_1tb1: UUID="085C87985C877F66" LABEL="Vista" TYPE="ntfs" 
/dev/mapper/isw_bejagaacfi_1tb2: UUID="9A08945208942F6F" LABEL="Drivers" TYPE="ntfs" 
/dev/mapper/isw_bejagaacfi_1tb3: UUID="606CAEAD6CAE7E02" TYPE="ntfs" 
/dev/mapper/isw_bejagaacfi_1tb5: UUID="5A5857D55857AF0F" TYPE="ntfs" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


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
search --no-floppy --fs-uuid --set 7102d01b-2d4e-4b00-8542-792f3942f123
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 7102d01b-2d4e-4b00-8542-792f3942f123
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=7102d01b-2d4e-4b00-8542-792f3942f123 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 7102d01b-2d4e-4b00-8542-792f3942f123
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=7102d01b-2d4e-4b00-8542-792f3942f123 ro single 
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
menuentry "Windows Vista (loader) (on /dev/mapper/isw_bejagaacfi_1tb1)" {
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
UUID=7102d01b-2d4e-4b00-8542-792f3942f123 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=6092bae9-6a57-4727-a0ed-0f3e7738848c /home           ext4    defaults        0       2
# swap was on /dev/sda4 during installation
UUID=fadb5492-eb15-42f1-9c39-39478d3385ba none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


 674.6GB: boot/grub/grub.cfg
 674.6GB: boot/initrd.img-2.6.31-14-generic
 674.6GB: boot/vmlinuz-2.6.31-14-generic
 674.6GB: initrd.img
 674.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1


Unknown BootLoader  on sdb2


Unknown BootLoader  on sdb3


Unknown BootLoader  on sdb4


Unknown BootLoader  on sdb5


Unknown BootLoader  on sdb6



=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 
=============================== StdErr Messages: ===============================

hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/sdb3: No such file or directory
hexdump: /dev/sdb4: No such file or directory
hexdump: /dev/sdb4: No such file or directory
hexdump: /dev/sdb5: No such file or directory
hexdump: /dev/sdb5: No such file or directory
hexdump: /dev/sdb6: No such file or directory
hexdump: /dev/sdb6: No such file or directory
```

---

### Post by oldfred on 2009-12-29
I have not followed the issues with raid other than if a drive was ever raid it leaves a signature that interferes with the install of grub unless you have the add in modules. Those modules I think are normally included with the server install but can be separate downloaded.

I also do not follow GPT partitioning since that is more Apple and a few windows servers.

But you do not have a grub boot loader. If you can boot you must have sdb set as the boot drive for windows. You have installed grub to several partition boot sectors but that will not let you boot unless you chainboot from another system. They (whoever they are) do not recommend grub2 in the PBR but you can are your own risk. I did and chainboot to the orginal alpha install of Karmic and it worked for me.  

You should install grub2 to the MBR of sda and set sda to the boot drive.

---

### Post by DecioSP on 2009-12-29
At first let me thanks for the fast response.
But I have some doubts about what you said. 
In fact  sdb is my boot drive, and i tried to use EasyBCD sometimes in the previous installations to make the windows boot loader point to sda3 where grub is installed, but it keeps opening an grub 0.4.4 dos version.
Regards the other suggestion you made, can i set sda as my boot drive via live cd? It wont bring problems to run Vista and XP in the others partitions?

---

### Post by oldfred on 2009-12-29
I am not very familar with EASYBCD but several users seem to have had success with it. I think you need the very newest version as tha now supports the ext4 format of Karmic. You should then be able to use that to chainboot into grub.

You also can use grub to boot and it can chainboot into windows. I do not know for sure if the raid would cause any issues or not. You have to change the boot order in BIOS. All computers use BIOS to select a boot drive and then load from the MBR the next part of the boot sequence. The MBR then just points to windows or grub or easyBCD or whatever bootloader you use. One advantage of grub2 in the MBR of sda is that at any time you can switch back in BIOS to boot sdb and windows will still boot. I have 3 drives and 4 operating systems (XP & 3 Ubus) and have different boot loaders in each MBR.

---

