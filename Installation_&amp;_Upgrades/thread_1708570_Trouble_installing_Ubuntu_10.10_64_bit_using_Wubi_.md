---
title: "Trouble installing Ubuntu 10.10 64 bit using Wubi inside Windows 7 64 bit"
date: 2011-03-16
forum: Installation &amp; Upgrades
---

### Post by adamantius7877 on 2011-03-16
I have searched all day through these forums so that I would not have to post a topic that has already been answered.  Unfortunately I was unable to find a solution so now I am posting this here.

I recently attempted to install Ubuntu 10.10 64 bit inside Windows 7 Pro 64 bit using Wubi and was given the error "No root file system is defined.  Please correct this from the partitioning menu."  which was given to me in an infinite loop and the only way out was to quit the installation which brought me to the Live demo that I assume was mounted, considering I never burned a CD.  I have attached the results.txt from when I ran the boot info script from [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

If anyone could help clarify why I might be getting this error it would be much appreciated.  I will continue to look for solutions while waiting for a response as well.  Thanks for your time.

Edit:  It would appear that an old Ubuntu 9.10 installation is still on my larger drive which is completely inaccessible due to a similar issue when I attempted to install inside windows previously.  It would also be good to note that I have Windows 7 Pro 64 bit installed on a RAID 0 set up of two 40GB SSD's

---

### Post by Rubi1200 on 2011-03-17
Hi and welcome to the forums :-)

Theoretically, Wubi installs to RAID are possible. In practice, this has not been well tested and not all configurations will work.

The best advice I can give right now is to look at this post and see if there is something that can help you:
[http://ubuntuforums.org/showpost.php?p=10316642&postcount=54](http://ubuntuforums.org/showpost.php?p=10316642&postcount=54)

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/mapper/pdc_bjbaebfeb
 => Windows is installed in the MBR of /dev/mapper/pdc_djcgdachd

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: /dev/sdb2 already mounted or sdb2 busy

sdb3: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: /dev/sdb2 already mounted or sdb2 busy
mount: /dev/sdb5 already mounted or sdb5 busy

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

pdc_bjbaebfeb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

pdc_bjbaebfeb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

pdc_bjbaebfeb2/Wubi: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: /dev/sdb2 already mounted or sdb2 busy
mount: /dev/sdb5 already mounted or sdb5 busy
mount: unknown filesystem type ''

pdc_djcgdachd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

pdc_djcgdachd2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.conf

pdc_djcgdachd3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: /dev/sdb2 already mounted or sdb2 busy
mount: /dev/sdb5 already mounted or sdb5 busy
mount: unknown filesystem type ''
mount: unknown filesystem type ''

pdc_djcgdachd4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

pdc_djcgdachd5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

pdc_djcgdachd6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
16 heads, 63 sectors/track, 2907021 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 2,612,080,799 2,612,078,752   7 HPFS/NTFS
/dev/sdb2    *  2,807,394,304 2,807,803,903       409,600  83 Linux
/dev/sdb3       2,807,803,904 2,930,276,351   122,472,448  8e Linux LVM
/dev/sdb4       2,612,080,800 2,807,392,895   195,312,096   5 Extended
/dev/sdb5       2,612,080,863 2,797,627,391   185,546,529  83 Linux
/dev/sdb6       2,797,627,455 2,807,392,895     9,765,441  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1               2,048   976,769,023   976,766,976   7 HPFS/NTFS


Drive: pdc_bjbaebfeb ___________________ _____________________________________________________

Disk /dev/mapper/pdc_bjbaebfeb: 80.0 GB, 79999795200 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156249600 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/pdc_bjbaebfeb1   *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/mapper/pdc_bjbaebfeb2            206,848   156,246,015   156,039,168   7 HPFS/NTFS


Drive: pdc_djcgdachd ___________________ _____________________________________________________

Disk /dev/mapper/pdc_djcgdachd: 1500.0 GB, 1499999961088 bytes
16 heads, 63 sectors/track, 2906435 cylinders, total 2929687424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/pdc_djcgdachd1              2,048 2,612,080,799 2,612,078,752   7 HPFS/NTFS
/dev/mapper/pdc_djcgdachd2   *  2,807,394,304 2,807,803,903       409,600  83 Linux
/dev/mapper/pdc_djcgdachd3      2,807,803,904 2,930,276,351   122,472,448  8e Linux LVM
/dev/mapper/pdc_djcgdachd4      2,612,080,800 2,807,392,895   195,312,096   5 Extended
/dev/mapper/pdc_djcgdachd5      2,612,080,863 2,797,627,391   185,546,529  83 Linux
/dev/mapper/pdc_djcgdachd6      2,797,627,455 2,807,392,895     9,765,441  82 Linux swap / Solaris

/dev/mapper/pdc_djcgdachd3 ends after the last sector of /dev/mapper/pdc_djcgdachd

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              iso9660    Ubuntu 10.10 amd64            
/dev/loop1                                              squashfs                                 
/dev/mapper/pdc_bjbaebfeb1 28BC930ABC92D1A4                       ntfs       System Reserved               
/dev/mapper/pdc_bjbaebfeb2 20449682449659FC                       ntfs                                     
/dev/mapper/pdc_bjbaebfeb: PTTYPE="dos" 
/dev/mapper/pdc_djcgdachd1 FC28534A285302D6                       ntfs       Large Drive                   
/dev/mapper/pdc_djcgdachd2 c811371d-bef2-4f68-a68e-5044af7b2a55   ext3                                     
/dev/mapper/pdc_djcgdachd5 6e0a7195-e2ea-4b89-b609-190e619395a5   ext3                                     
/dev/mapper/pdc_djcgdachd6 69ef8d2b-08c0-424f-bc83-5db371c18e7e   swap                                     
/dev/mapper/pdc_djcgdachd: PTTYPE="dos" 
/dev/sda                                                promise_fasttrack_raid_member                               
/dev/sdb1        FC28534A285302D6                       ntfs       Large Drive                   
/dev/sdb2        c811371d-bef2-4f68-a68e-5044af7b2a55   ext3                                     
/dev/sdb3        JP4xKF-lrCv-bwsK-GQNi-vkd1-NyjA-2aEM5j LVM2_member                               
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        6e0a7195-e2ea-4b89-b609-190e619395a5   ext3                                     
/dev/sdb6        69ef8d2b-08c0-424f-bc83-5db371c18e7e   swap                                     
/dev/sdb                                                promise_fasttrack_raid_member                               
/dev/sdc                                                promise_fasttrack_raid_member                               
/dev/sdd1        46E20807E207FA47                       ntfs       External_Zion                 
/dev/sdd: PTTYPE="dos" 
error: /dev/mapper/pdc_djcgdachd3: No such file or directory
error: /dev/mapper/pdc_djcgdachd4: No such file or directory

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
pdc_bjbaebfeb
pdc_bjbaebfeb1
pdc_bjbaebfeb2

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/loop0       /cdrom                   iso9660    (ro,noatime)
/dev/loop1       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        /media/External_Zion     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


======================== pdc_djcgdachd2/grub/grub.conf: ========================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,1)
#          kernel /vmlinuz-version ro root=/dev/mapper/vg_zion-lv_root
#          initrd /initrd-version.img
#boot=/dev/sdb2
default=0
timeout=5
splashimage=(hd0,1)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.30.10-105.2.23.fc11.x86_64)
    root (hd0,1)
    kernel /vmlinuz-2.6.30.10-105.2.23.fc11.x86_64 ro root=/dev/mapper/vg_zion-lv_root rhgb quiet
    initrd /initrd-2.6.30.10-105.2.23.fc11.x86_64.img
title Other
    rootnoverify (hd0,0)
    chainloader +1

============== pdc_djcgdachd2: Location of files loaded by Grub: ==============


1437.4GB: grub/grub.conf
1437.4GB: grub/menu.lst
1437.4GB: grub/stage2
1437.3GB: initrd-2.6.30.10-105.2.23.fc11.x86_64.img
1437.3GB: vmlinuz-2.6.30.10-105.2.23.fc11.x86_64

====================== pdc_djcgdachd5/boot/grub/grub.cfg: ======================

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
set root=(hd1,5)
search --no-floppy --fs-uuid --set 6e0a7195-e2ea-4b89-b609-190e619395a5
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
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 6e0a7195-e2ea-4b89-b609-190e619395a5
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=6e0a7195-e2ea-4b89-b609-190e619395a5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 6e0a7195-e2ea-4b89-b609-190e619395a5
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=6e0a7195-e2ea-4b89-b609-190e619395a5 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 6e0a7195-e2ea-4b89-b609-190e619395a5
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=6e0a7195-e2ea-4b89-b609-190e619395a5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 6e0a7195-e2ea-4b89-b609-190e619395a5
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=6e0a7195-e2ea-4b89-b609-190e619395a5 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry "Windows 7 Pro 64 Bit" {
insmod ntfs
set root=(hd0,2)
search --no-floppy --fs-uuid --set 982A00CF2A00AC76
chainloader +1
}
### END /etc/grub.d/11_Windows ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

========================== pdc_djcgdachd5/etc/fstab: ==========================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=6e0a7195-e2ea-4b89-b609-190e619395a5 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=69ef8d2b-08c0-424f-bc83-5db371c18e7e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

============== pdc_djcgdachd5: Location of files loaded by Grub: ==============


1337.7GB: boot/grub/core.img
1337.6GB: boot/grub/grub.cfg
1337.6GB: boot/initrd.img-2.6.31-14-generic
1337.6GB: boot/initrd.img-2.6.31-20-generic
1337.7GB: boot/vmlinuz-2.6.31-14-generic
1337.7GB: boot/vmlinuz-2.6.31-20-generic
1337.6GB: initrd.img
1337.6GB: initrd.img.old
1337.7GB: vmlinuz
1337.7GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on pdc_bjbaebfeb2/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200

Unknown BootLoader  on pdc_djcgdachd3


Unknown BootLoader  on pdc_djcgdachd4



=============================== StdErr Messages: ===============================

ERROR: pdc: wrong # of devices in RAID set "pdc_bjbaebfeb" [1/2] on /dev/sdc
ERROR: pdc: wrong # of devices in RAID set "pdc_bjbaebfeb" [1/2] on /dev/sda
ERROR: dos: partition address past end of RAID device
umount: /isodevice: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
hexdump: /dev/mapper/pdc_djcgdachd3: No such file or directory
hexdump: /dev/mapper/pdc_djcgdachd3: No such file or directory
hexdump: /dev/mapper/pdc_djcgdachd4: No such file or directory
hexdump: /dev/mapper/pdc_djcgdachd4: No such file or directory
ERROR: pdc: wrong # of devices in RAID set "pdc_bjbaebfeb" [1/2] on /dev/sdc
ERROR: pdc: wrong # of devices in RAID set "pdc_bjbaebfeb" [1/2] on /dev/sda
ERROR: dos: partition address past end of RAID device
```

---

### Post by adamantius7877 on 2011-03-18
Thanks for the welcome!  It feels good to be apart of a community that cares so much about Linux :)

I have read through the post that you linked and while I was unable to find a solution there, I was able to solve my problem in a different way.  First, I really wanted Ubuntu as my main os on my laptop and desktop. I pulled out my macbook and dual booted Ubuntu 10.10 32 bit alongside Snow Leopard 32 bit with no trouble at all.

My desktop was a much larger hassle.  My results.txt file shows I have 2 40GB ssd drives and a 1.5TB green drive which runs at a mere 5400RPMs.  I deleted the RAID 0 on the two solid states and installed Windows 7 64 bit on one ssd and then did a full install of Ubuntu 10.10 64 bit on the other one afterwards.

I installed Windows first which gave me the most trouble because I was unable to detect my hard drives due to leaving the BIOS set to RAID instead of ACHI.  Windows also gave me an error and would not install on the first ssd, I'm assuming because of a faulty Parition Table. I then decided to use GParted to partition and reformat before I installed any OS.  However, GParted would not run on the Ubuntu 10.10 64bit Live cd so I had to download and burn a GParted Live CD which I then used to partition the drives before I installed.  After using GParted, the installations went by smooth with no problems.

I also took the old installation of Ubuntu 9.10 which was stuck on the large green drive and reformatted it so I could use it as storage for my new Ubuntu install. 

Everything is installed and running great now on my desktop and laptop after staying up all night installing and troubleshooting the problems I was encountering. I just connected my second monitor earlier and am able to run the separate X Screens with no problems whatsoever, but thats just a bonus and is not relevant :).

Sorry for the wall of text.  No sleep + everything working = me pretty damn excited and had to tell someone :D

---

### Post by Rubi1200 on 2011-03-18
Excellent! I am really pleased you managed to get things sorted out after some hard work, but worth it I believe.

If you need any additional assistance, please feel free to ask here on the forums.

I am sure someone will always try and help if they can.

Enjoy :)

---

### Post by adamantius7877 on 2011-03-19
Hey, I know this isn't the right place for this but it pertains to what I have done recently and was just wondering if there was a quick answer.  When I took off the RAID 0 on my two solid state drives it didn't occur to me that my 1.5 TB drive is still set up as a RAID Ready device.  I noticed while deleting the extra linux partitions at the end of the 1.5TB drive that it was stating it was RAID, but the problem with it is that it was actually never a real RAID.  

**For Clarification, the drive has never actually been connected with another drive as a RAID, just has the status RAID READY.  This was done using my motherboards software for accessing and setting up a RAID**

If I delete the "Raid Ready" status will I still be able to access the information on the drive.  It is pertinent that I keep the data on the larger portion of the disk because it is my backup.  I can access them currently, I was just wondering what would happen or if there might be problems with this in the future.

If it helps, the motherboard I am using is a LanParty DK 790GX-M2RS Dark

---

