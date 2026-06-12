---
title: "Unknown error during installation"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by regua on 2010-10-25
I'm trying to install 64-bit Ubuntu 10.10 on my Lenovo Y530 laptop. I get an error during the installation, I've attached the screenshot.

When I click OK, the mouse pointer indicates that the system is loading something, but nothing happens.

Strangely enough, the exact same thing with the exact same error message happens when I try to install Ubuntu 9.10.

I have no idea what to do because the error message is, well, quite cryptic. I suppose it's not a hardware issue as I have been successfully running 64-bit Ubuntu on this machine. Any help?

---

### Post by gyussz on 2010-10-25
I'd try to uncheck the *Download Updates While Installing*, and the *Install third-party software* check-boxes. 

(I usually install them after a successful installation.)

---

### Post by regua on 2010-10-25
Oh, I'm not *that* stupid, I've already tried all the simplest solutions. ;)

Right now I'm downloading the text-based Ubuntu installer to see if it helps.

---

### Post by Rubi1200 on 2010-10-25
Do you have any "unusual" setups like a RAID array or GPT?

---

### Post by regua on 2010-10-25
No. I've also never encountered any problems with installing an operating system, and I've installed quite a few.

---

### Post by halj32 on 2010-10-25
did you check the ISO's MD5 before burning & before installing?
some CD's/DVD's have errors

---

### Post by srs5694 on 2010-10-25
Try hitting Ctrl+Alt+F1, then all the function keys in sequence until you get back to the GUI. It's possible there'll be a more intelligible error message on one of them (probably F1).

---

### Post by regua on 2010-10-25
I just tried the text-based installation disc - same thing, but this time with a "Partition disks" header written above the question marks.

Normally I would just format the disk and it'd probably fix the problem, but this time I'm installing the system over an existing Ubuntu installation and I don't want to lose any personal data.

---

### Post by Rubi1200 on 2010-10-25
Using a LiveCD or LiveUSB, post the results from the boot-script linked at the bottom of my post please.

Perhaps the results will help us get to the bottom of this.

Thanks.

---

### Post by regua on 2010-10-25
> **Rubi1200 said:**
> Using a LiveCD or LiveUSB, post the results from the boot-script linked at the bottom of my post please.
RESULTS.txt attached.

Also, I tried running the installation again, and this time when the ??? error appeared, a crash of the Parted server was reported. I googled the problem and the only solution I found was not to use certain types of USB flash drives; I'm running a LiveCD, though.

---

### Post by Rubi1200 on 2010-10-25
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda7 starts at sector 271482498.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    68,372,639    68,372,577   7 HPFS/NTFS
/dev/sda2          68,372,640    76,180,229     7,807,590  82 Linux swap / Solaris
/dev/sda3          76,180,230   134,769,284    58,589,055  83 Linux
/dev/sda4         134,769,285   976,768,064   841,998,780   5 Extended
/dev/sda5         976,382,568   976,768,064       385,497  83 Linux
/dev/sda6         134,769,411   271,482,434   136,713,024  83 Linux
/dev/sda7         271,482,498   476,279,054   204,796,557   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        E0B6AE52B6AE28CC                       ntfs                                     
/dev/sda2        8b36d14f-ac05-4c3c-bcef-2b687c58dc7e   swap                                     
/dev/sda3        fe37651d-9202-4932-9cbd-878d6446bb15   ext4                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        b9ad016b-7ae6-4926-8591-077a321cd774   ext4                                     
/dev/sda6        5a7b7487-8dd1-46dc-ac37-4ec66bb80e9d   ext4                                     
/dev/sda7        9914-8F92                              vfat       Common                        
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=fe37651d-9202-4932-9cbd-878d6446bb15 / ext4 errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=b9ad016b-7ae6-4926-8591-077a321cd774 /boot ext4 defaults 0 2
# Entry for /dev/sda6 :
UUID=5a7b7487-8dd1-46dc-ac37-4ec66bb80e9d /home ext4 defaults 0 2
# Entry for /dev/sda2 :
UUID=8b36d14f-ac05-4c3c-bcef-2b687c58dc7e none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda7 /media/common vfat defaults,uid=1000 0 0
/dev/sda1 /media/windows ntfs-3g defaults,locale=en_US.UTF-8 0 0

============================= sda5/grub/grub.cfg: =============================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set fe37651d-9202-4932-9cbd-878d6446bb15
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set b9ad016b-7ae6-4926-8591-077a321cd774
set locale_dir=($root)/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b9ad016b-7ae6-4926-8591-077a321cd774
    linux    /vmlinuz-2.6.35-22-generic root=UUID=fe37651d-9202-4932-9cbd-878d6446bb15 ro   quiet splash
    initrd    /initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b9ad016b-7ae6-4926-8591-077a321cd774
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=UUID=fe37651d-9202-4932-9cbd-878d6446bb15 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b9ad016b-7ae6-4926-8591-077a321cd774
    linux    /vmlinuz-2.6.32-25-generic root=UUID=fe37651d-9202-4932-9cbd-878d6446bb15 ro   quiet splash
    initrd    /initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b9ad016b-7ae6-4926-8591-077a321cd774
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /vmlinuz-2.6.32-25-generic root=UUID=fe37651d-9202-4932-9cbd-878d6446bb15 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b9ad016b-7ae6-4926-8591-077a321cd774
    linux    /vmlinuz-2.6.31-21-generic root=UUID=fe37651d-9202-4932-9cbd-878d6446bb15 ro   quiet splash
    initrd    /initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b9ad016b-7ae6-4926-8591-077a321cd774
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /vmlinuz-2.6.31-21-generic root=UUID=fe37651d-9202-4932-9cbd-878d6446bb15 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set e0b6ae52b6ae28cc
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=================== sda5: Location of files loaded by Grub: ===================


 499.9GB: grub/core.img
 499.9GB: grub/grub.cfg
 500.0GB: initrd.img-2.6.31-21-generic
 499.9GB: initrd.img-2.6.32-25-generic
 499.9GB: initrd.img-2.6.35-22-generic
 499.9GB: vmlinuz-2.6.31-21-generic
 499.9GB: vmlinuz-2.6.32-25-generic
 499.9GB: vmlinuz-2.6.35-22-generic
```

---

### Post by srs5694 on 2010-10-26
The only thing that struck me as odd was this, in reference to /dev/sda7:

```

    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda7 starts at sector 271482498.

```

I'm not an expert on FAT, though, so I don't know how much of a problem this is or whether it might cause the installer to act up. If the partition doesn't hold any important data, or if you can easily back it up, you might try deleting the partition and then trying again; however, this is a bit of a shot in the dark; there's a very good chance that it won't help.

Perhaps somebody else will spot a problem I missed....

---

### Post by regua on 2010-10-26
Just had a look at Parted and some partitions seem to be out of order (/dev/sda5 at the end), but can that cause the error during installation? I'd rather not remove any partitions if that's absolutely necessary.

[img]http://img9.imageshack.us/img9/1055/partde.png[/img]

---

### Post by srs5694 on 2010-10-26
Partitions can be out of order. That's not an error, and I've never heard of the Ubuntu installer squawking unnecessarily about that. That said, out-of-order partitions can be confusing, so it's usually best to try to keep them in order. You can sort them by entering fdisk, typing "x" to get to the experts' menu, typing "f" to sort the partitions, and then typing "w" to save your changes. Be aware, however, that this can cause problems if your /etc/fstab file or boot loader refer to partitions by under rather than by their UUID values or labels.

---

### Post by halj32 on 2010-10-28
if your not connected to the net untick download updates & 3rd party sofdtware

goodluck

---

### Post by regua on 2010-10-28
None of the solutions worked, unfortunately.

I have browsed some similar bug reports, and many users claim that what causes the parted_server crash is a USB flash drive or an SD card connected to the computer during installation; I don't have any of these, I even disconnected my USB mouse to see if that helps but it didn't.

Any more ideas, guys? I really don't want to have to format the disk to install Ubuntu.

---

### Post by chronossc on 2010-10-28
Well, I having same screen, with two disks without any so except windows.

The history is, I lost a 320G WD Disk and get a new 1TB Seagate Barracuda disk.

So my conf here is:

sda = 320G Seagate Barracuda 
sdb = 1TB Seagate Barracuda 

With that, and ** ANY ** operating system, the livecd doesn't works in install.

Switching HD positions, with ANY SO, not works too.

So I installed Windows 7 with following configuration:

sda = 1TB disk
sdb = 320G disk

Windows 7 get two partitions of SDA disk, with total of 80G.

Same stuff happens.

I have a microsoft wireless keyboard, and a usb mouse plugged, but it isn't really the problem. I used same media to install ubuntu two days before on SWAP partition of 320G disk, to rescue stuff of WD lost disk.

Maybe that is something related to BIG disks, >= 500G ?

---

### Post by chronossc on 2010-10-28
Here is details showed by mentioned boot script:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total de 1953525168 setores
Unidades = setores de 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   163,842,047   163,635,200   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total de 625142448 setores
Unidades = setores de 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   608,365,484   608,365,422   c W95 FAT32 (LBA)
/dev/sdb2         608,366,592   625,141,759    16,775,168  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        8A6C24BA6C24A2C5                       ntfs       System Reserved               
/dev/sda2        664C36794C3643D9                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        492D-AB37                              vfat                                     
/dev/sdb2        661c8b67-824b-4a51-bb32-5e889038acac   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/492D-AB37         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)

=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 

```
Here is a backtrace that I see in /var/log/messages when I run installer:

```
 Oct 28 21:23:54 ubuntu ubiquity[4921]: Step_before = stepLanguage
Oct 28 21:23:55 ubuntu ubiquity[4921]: switched to page prepare
Oct 28 21:24:19 ubuntu ubiquity: 
Oct 28 21:24:19 ubuntu ubiquity: Procurando drivers disponíveis...
Oct 28 21:24:20 ubuntu ubiquity[4921]: Step_before = stepPrepare
Oct 28 21:24:20 ubuntu activate-dmraid: No Serial ATA RAID disks detected
Oct 28 21:24:20 ubuntu kernel: [  628.952249] JFS: nTxBlock = 8192, nTxLock = 65536
Oct 28 21:24:20 ubuntu kernel: [  629.282508] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
Oct 28 21:24:20 ubuntu kernel: [  629.285015] SGI XFS Quota Management subsystem
Oct 28 21:24:29 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
Oct 28 21:24:29 ubuntu ntfsresize: Device name        : /dev/sda1
Oct 28 21:24:29 ubuntu ntfsresize: NTFS volume version: 3.1
Oct 28 21:24:29 ubuntu ntfsresize: Cluster size       : 4096 bytes
Oct 28 21:24:29 ubuntu ntfsresize: Current volume size: 104854016 bytes (105 MB)
Oct 28 21:24:29 ubuntu ntfsresize: Current device size: 104857600 bytes (105 MB)
Oct 28 21:24:29 ubuntu ntfsresize: Checking filesystem consistency ...
Oct 28 21:24:29 ubuntu ntfsresize: Accounting clusters ...
Oct 28 21:24:29 ubuntu ntfsresize: Space in use       : 26 MB (24,5%)
Oct 28 21:24:29 ubuntu ntfsresize: Collecting resizing constraints ...
Oct 28 21:24:29 ubuntu ntfsresize: You might resize at 35217408 bytes or 36 MB (freeing 69 MB).
Oct 28 21:24:29 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
Oct 28 21:24:30 ubuntu ntfsresize: ntfsresize v2.0.0 (libntfs 10:0:0)
Oct 28 21:24:30 ubuntu ntfsresize: Device name        : /dev/sda2
Oct 28 21:24:30 ubuntu ntfsresize: NTFS volume version: 3.1
Oct 28 21:24:30 ubuntu ntfsresize: Cluster size       : 4096 bytes
Oct 28 21:24:30 ubuntu ntfsresize: Current volume size: 83781218816 bytes (83782 MB)
Oct 28 21:24:30 ubuntu ntfsresize: Current device size: 83781222400 bytes (83782 MB)
Oct 28 21:24:30 ubuntu ntfsresize: Checking filesystem consistency ...
Oct 28 21:24:30 ubuntu ntfsresize: Accounting clusters ...
Oct 28 21:24:30 ubuntu ntfsresize: Space in use       : 15575 MB (18,6%)
Oct 28 21:24:30 ubuntu ntfsresize: Collecting resizing constraints ...
Oct 28 21:24:30 ubuntu ntfsresize: You might resize at 15574208512 bytes or 15575 MB (freeing 68207 MB).
Oct 28 21:24:30 ubuntu ntfsresize: Please make a test run using both the -n and -s options before real resizing!
Oct 28 21:24:38 ubuntu ubiquity: *** buffer overflow detected ***: parted_server terminated
Oct 28 21:24:38 ubuntu ubiquity: ======= Backtrace: =========
Oct 28 21:24:38 ubuntu ubiquity: /lib/libc.so.6(__fortify_fail+0x37)[0x7f0284085537]
Oct 28 21:24:38 ubuntu ubiquity: /lib/libc.so.6(+0xfe3f0)[0x7f02840843f0]
Oct 28 21:24:38 ubuntu ubiquity: /lib/libparted.so.0(+0x28070)[0x7f0284331070]
Oct 28 21:24:38 ubuntu ubiquity: /lib/libparted.so.0(+0x28154)[0x7f0284331154]
Oct 28 21:24:38 ubuntu ubiquity: ======= Memory map: ========
Oct 28 21:24:38 ubuntu ubiquity: 00400000-00412000 r-xp 00000000 00:11 10243                              /bin/parted_server
Oct 28 21:24:38 ubuntu ubiquity: 00611000-00612000 r--p 00011000 00:11 10243                              /bin/parted_server
Oct 28 21:24:38 ubuntu ubiquity: 00612000-00613000 rw-p 00012000 00:11 10243                              /bin/parted_server
Oct 28 21:24:38 ubuntu ubiquity: 01d3c000-01ed0000 rw-p 00000000 00:00 0                                  [heap]
Oct 28 21:24:38 ubuntu ubiquity: 7f027d85d000-7f027d872000 r-xp 00000000 00:11 1740                       /lib/libgcc_s.so.1
Oct 28 21:24:38 ubuntu ubiquity: 7f027d872000-7f027da71000 ---p 00015000 00:11 1740                       /lib/libgcc_s.so.1
Oct 28 21:24:38 ubuntu ubiquity: 7f027da71000-7f027da72000 r--p 00014000 00:11 1740                       /lib/libgcc_s.so.1
Oct 28 21:24:38 ubuntu ubiquity: 7f027da72000-7f027da73000 rw-p 00015000 00:11 1740                       /lib/libgcc_s.so.1
Oct 28 21:24:38 ubuntu ubiquity: 7f027da80000-7f0283522000 rw-p 00000000 00:00 0 
Oct 28 21:24:38 ubuntu ubiquity: 7f0283522000-7f028353e000 r-xp 00000000 00:11 204                        /lib/libselinux.so.1
Oct 28 21:24:38 ubuntu ubiquity: 7f028353e000-7f028373d000 ---p 0001c000 00:11 204                        /lib/libselinux.so.1
Oct 28 21:24:38 ubuntu ubiquity: 7f028373d000-7f028373e000 r--p 0001b000 00:11 204                        /lib/libselinux.so.1
Oct 28 21:24:38 ubuntu ubiquity: 7f028373e000-7f028373f000 rw-p 0001c000 00:11 204                        /lib/libselinux.so.1
Oct 28 21:24:38 ubuntu ubiquity: 7f028373f000-7f0283740000 rw-p 00000000 00:00 0 
Oct 28 21:24:38 ubuntu ubiquity: 7f0283740000-7f028375c000 r-xp 00000000 00:11 1898                       /lib/libblkid.so.1.1.0
Oct 28 21:24:38 ubuntu ubiquity: 7f028375c000-7f028395b000 ---p 0001c000 00:11 1898                       /lib/libblkid.so.1.1.0
Oct 28 21:24:38 ubuntu ubiquity: 7f028395b000-7f028395e000 r--p 0001b000 00:11 1898                       /lib/libblkid.so.1.1.0
Oct 28 21:24:38 ubuntu ubiquity: 7f028395e000-7f028395f000 rw-p 0001e000 00:11 1898                       /lib/libblkid.so.1.1.0
Oct 28 21:24:38 ubuntu ubiquity: 7f028395f000-7f028397b000 r-xp 00000000 00:11 2207                       /lib/libdevmapper.so.1.02.1
Oct 28 21:24:38 ubuntu ubiquity: 7f028397b000-7f0283b7a000 ---p 0001c000 00:11 2207                       /lib/libdevmapper.so.1.02.1
Oct 28 21:24:38 ubuntu ubiquity: 7f0283b7a000-7f0283b7b000 r--p 0001b000 00:11 2207                       /lib/libdevmapper.so.1.02.1
Oct 28 21:24:38 ubuntu ubiquity: 7f0283b7b000-7f0283b7d000 rw-p 0001c000 00:11 2207                       /lib/libdevmapper.so.1.02.1
Oct 28 21:24:38 ubuntu ubiquity: 7f0283b7d000-7f0283b7f000 r-xp 00000000 00:11 50                         /lib/libdl-2.12.1.so
Oct 28 21:24:38 ubuntu ubiquity: 7f0283b7f000-7f0283d7f000 ---p 00002000 00:11 50                         /lib/libdl-2.12.1.so
Oct 28 21:24:38 ubuntu ubiquity: 7f0283d7f000-7f0283d80000 r--p 00002000 00:11 50                         /lib/libdl-2.12.1.so
Oct 28 21:24:38 ubuntu ubiquity: 7f0283d80000-7f0283d81000 rw-p 00003000 00:11 50                         /lib/libdl-2.12.1.so
Oct 28 21:24:38 ubuntu ubiquity: 7f0283d81000-7f0283d85000 r-xp 00000000 00:11 1900                       /lib/libuuid.so.1.3.0
Oct 28 21:24:38 ubuntu ubiquity: 7f0283d85000-7f0283f84000 ---p 00004000 00:11 1900                       /lib/libuuid.so.1.3.0
Oct 28 21:24:38 ubuntu ubiquity: 7f0283f84000-7f0283f85000 r--p 00003000 00:11 1900                       /lib/libuuid.so.1.3.0
Oct 28 21:24:38 ubuntu ubiquity: 7f0283f85000-7f0283f86000 rw-p 00004000 00:11 1900                       /lib/libuuid.so.1.3.0
Oct 28 21:24:38 ubuntu ubiquity: 7f0283f86000-7f0284100000 r-xp 00000000 00:11 26                         /lib/libc-2.12.1.so
Oct 28 21:24:38 ubuntu ubiquity: 7f0284100000-7f02842ff000 ---p 0017a000 00:11 26                         /lib/libc-2.12.1.so
Oct 28 21:24:38 ubuntu ubiquity: 7f02842ff000-7f0284303000 r--p 00179000 00:11 26                         /lib/libc-2.12.1.so
Oct 28 21:24:38 ubuntu ubiquity: 7f0284303000-7f0284304000 rw-p 0017d000 00:11 26                         /lib/libc-2.12.1.so
Oct 28 21:24:38 ubuntu ubiquity: 7f0284304000-7f0284309000 rw-p 00000000 00:00 0 
Oct 28 21:24:38 ubuntu ubiquity: 7f0284309000-7f028437c000 r-xp 00000000 00:11 2203                       /lib/libparted.so.0.0.1
Oct 28 21:24:38 ubuntu ubiquity: 7f028437c000-7f028457b000 ---p 00073000 00:11 2203                       /lib/libparted.so.0.0.1
Oct 28 21:24:38 ubuntu ubiquity: 7f028457b000-7f028457e000 r--p 00072000 00:11 2203                       /lib/libparted.so.0.0.1
Oct 28 21:24:38 ubuntu ubiquity: 7f028457e000-7f028457f000 rw-p 00075000 00:11 2203                       /lib/libparted.so.0.0.1
Oct 28 21:24:38 ubuntu ubiquity: 7f028457f000-7f0284585000 rw-p 00000000 00:00 0 
Oct 28 21:24:38 ubuntu ubiquity: 7f0284585000-7f02845a5000 r-xp 00000000 00:11 20                         /lib/ld-2.12.1.so
Oct 28 21:24:38 ubuntu ubiquity: 7f0284791000-7f0284796000 rw-p 00000000 00:00 0 
Oct 28 21:24:38 ubuntu ubiquity: 7f02847a1000-7f02847a5000 rw-p 00000000 00:00 0 
Oct 28 21:24:38 ubuntu ubiquity: 7f02847a5000-7f02847a6000 r--p 00020000 00:11 20                         /lib/ld-2.12.1.so
Oct 28 21:24:38 ubuntu ubiquity: 7f02847a6000-7f02847a7000 rw-p 00021000 00:11 20                         /lib/ld-2.12.1.so
Oct 28 21:24:38 ubuntu ubiquity: 7f02847a7000-7f02847a8000 rw-p 00000000 00:00 0 
Oct 28 21:24:38 ubuntu ubiquity: 7fffe1b50000-7fffe1b71000 rw-p 00000000 00:00 0                          [stack]
Oct 28 21:24:38 ubuntu ubiquity: 7fffe1bff000-7fffe1c00000 r-xp 00000000 00:00 0                          [vdso]
Oct 28 21:24:38 ubuntu ubiquity: ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
```

---

### Post by srs5694 on 2010-10-28
I note that Boot Info Script is reporting that /dev/sdc, /dev/sdd, /dev/sde, and /dev/sdf all exist but have no media present. Do you have any removable disks, USB flash drives, CF card readers, or the like in the system? If so, try unplugging them. If not, then something is causing Linux to mistakenly believe you've got disks that you don't have, and you should investigate that. Along those lines, *if* those disks really aren't present, boot the Ubuntu live CD, open a Terminal, type "dmesg", and post the output here.

---

### Post by chronossc on 2010-10-28
Nop, any other kind of storage connect.

After all, I disconnect my sdb (320G Disk), and tryed again, then installed normally (finished just now).

The 320G disk have a BIG FAT32 partition and a 8G swap, it's normal and don't makes any sense disconnect it to install, but worked hehe... after install I connect it again and access it normally.

---

### Post by regua on 2010-10-30
I tried mounting all partitions before installation so the installer couldn't use them, but that doesn't help.

Any more ideas, guys?

---

