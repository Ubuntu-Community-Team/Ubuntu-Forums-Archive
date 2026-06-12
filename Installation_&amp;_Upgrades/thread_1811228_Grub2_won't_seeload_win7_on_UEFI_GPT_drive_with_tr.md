---
title: "Grub2 won't see/load win7 on UEFI GPT drive with triple boot"
date: 2011-07-24
forum: Installation &amp; Upgrades
---

### Post by sk3499 on 2011-07-24
Hey all, I started this on another thread but was told to make a new one.



PROBLEM:
Grub2 can't see or load windows 7 after I installed Fedora and then Ubuntu on my drive. My computer has UEFI support, so my hard drive is GPT only. This boots fine for all 3 OS's independently. The problem is with grub2, I can't get it to see windows even when I manually enter options such as :

ATTEMPTED SOLUTIONS:

My Entry 1:
insmod part_gpt
insmod ntfs
set root='(/dev/sda,gpt3)'
chainloader +1

My entry 2: (suggested by srs5694):
menuentry "Windows x86_64 UEFI-GPT" {
   search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
   chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

Neither of these work. The first one says 'no such disk', even though I know that's the windows partition. The second one just sits at a blank maroon colored screen when i hit the option in grub2.

INTERESTING THING:
I can still boot windows by going into the BIOS boot menu when the computer starts up. I see 'Windows Boot Manager'; if I click that it goes straight to booting up windows. Why can't Grub2 see that, or how do I point it at the right place?

Any help would be appreciated.





OUTPUT FROM THE BOOT SCRIPT:

sda1: __________________________________________________ ________________________

File system: vfat
Boot sector type: Unknown
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: 
Boot files: 

sda2: __________________________________________________ ________________________

File system: 
Boot sector type: -
Boot sector info: 
Mounting failed: mount: unknown filesystem type ''

sda3: __________________________________________________ ________________________

File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows 7
Boot files: /Windows/System32/winload.exe

sda4: __________________________________________________ ________________________

File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: According to the info in the boot sector, sda4 has 
118606544 sectors, but according to the info from 
fdisk, it has 1192348379 sectors.
Operating System: 
Boot files: 

sda5: __________________________________________________ ________________________

File system: ext4
Boot sector type: -
Boot sector info: 
Operating System: Fedora release 15 (Lovelock) 
Kernel on an ()
Boot files: /etc/fstab

sda6: __________________________________________________ ________________________

File system: swap
Boot sector type: -
Boot sector info: 

sda7: __________________________________________________ ________________________

File system: vfat
Boot sector type: -
Boot sector info: According to the info in the boot sector, sda7 starts 
at sector 733008604. But according to the info from 
fdisk, sda7 starts at sector 1806750428. According to 
the info in the boot sector, sda7 has 0 sectors.
Operating System: 
Boot files: 

sda8: __________________________________________________ ________________________

File system: vfat
Boot sector type: -
Boot sector info: According to the info in the boot sector, sda8 starts 
at sector 733047667. But according to the info from 
fdisk, sda8 starts at sector 1806789491. According to 
the info in the boot sector, sda8 has 0 sectors.
Operating System: 
Boot files: 

sda9: __________________________________________________ ________________________

File system: swap
Boot sector type: -
Boot sector info: 

sda10: __________________________________________________ _______________________

File system: ext4
Boot sector type: -
Boot sector info: 
Operating System: Ubuntu 11.04
Boot files: /boot/grub/grub.cfg /etc/fstab

sda11: __________________________________________________ _______________________

File system: swap
Boot sector type: -
Boot sector info: 

...

GUID Partition Table detected.

Partition Start Sector End Sector # of Sectors System
/dev/sda1 2,048 206,847 204,800 EFI System partition
/dev/sda2 206,848 468,991 262,144 Microsoft Reserved Partition (Windows)
/dev/sda3 468,992 614,402,047 613,933,056 Data partition (Windows/Linux)
/dev/sda4 614,402,048 1,806,750,427 1,192,348,380 Data partition (Windows/Linux)
/dev/sda5 2,209,224,704 2,629,066,751 419,842,048 Data partition (Windows/Linux)
/dev/sda6 2,629,066,752 2,639,306,751 10,240,000 Swap partition (Linux)
/dev/sda7 1,806,750,428 1,806,789,490 39,063 EFI System partition
/dev/sda8 1,806,789,491 1,806,828,553 39,063 EFI System partition
/dev/sda9 2,192,482,851 2,209,224,703 16,741,853 Swap partition (Linux)
/dev/sda10 1,806,828,554 2,175,742,616 368,914,063 Data partition (Windows/Linux)
/dev/sda11 2,175,742,617 2,192,482,850 16,740,234 Swap partition (Linux)

---

### Post by srs5694 on 2011-07-24
When posting text-mode program output, it's helpful to place it between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags. That preserves formatting and keeps it legible.

Your entry #1 just plain won't work on a UEFI boot because that's the way GRUB boots Windows on a BIOS system, not on a UEFI system.

Your entry #2 might not be working because a file may be named differently. You can check the names by examining the files in the EFI System Partition (ESP), which in your case is /dev/sda1. Because you've provided only some of the Boot Info Script output, I can't be sure where (or even if) it's mounted in Linux by default, but it's normally mounted at /boot/efi. Thus, "sudo find /boot/efi" will reveal all of the files on that partition. You can scan the results for the referenced file (/efi/Microsoft/Boot/bootmgfw.efi) to see if it's present, or if it's located in some other directory, and change the pathname reference if it's located somewhere else.

Another option would be to install [rEFIt,](http://refit.sourceforge.net) which you can configure as the primary boot loader for your system; it will then give you the option of booting Linux or Windows. There are some important caveats with rEFIt, though:


[list]
[*]The combined 32-/64-bit version of rEFIt doesn't work on x86-64 UEFI systems (at least, not that I've heard of); you've got to install a straight 64-bit version of the boot loader. The refit package in Ubuntu includes such a version, in /usr/lib/refit/x64/refit.efi; you'd copy that file to its own subdirectory on the ESP (as in /boot/efi/EFI/refit/refit.efi) along with the /usr/lib/refit/refit/refit.conf configuration file.
[*]On some UEFI systems, rEFIt suffers from various types of video glitches when run in its standard graphical mode. If you have such problems, you can edit its refit.conf configuration file and uncomment the "textonly" line. This will run it in text-only mode, which lacks the eye candy but also lacks the video glitches.
[*]rEFIt can only boot other EFI boot loaders; it can't boot any OS directly. Thus, you'll still need both the Windows boot loader and GRUB or some other Linux boot loader to be installed in your ESP. In other words, don't delete either of these boot loaders once you get rEFIt working!
[/list]

---

### Post by srs5694 on 2011-07-24
Another idea: Try changing the Windows entry to read:

```

menuentry "Windows x86_64 UEFI-GPT" {
   set root='(hd0,gpt1)'
   chainloader /efi/Microsoft/Boot/bootmgfw.efi
}

```

---

### Post by sk3499 on 2011-07-24
> **srs5694 said:**
> Another idea: Try changing the Windows entry to read:

```

menuentry "Windows x86_64 UEFI-GPT" {
   set root='(hd0,gpt1)'
   chainloader /efi/Microsoft/Boot/bootmgfw.efi
}

```

I just tried this one...

'no such partition' is what I get if I leave it like you have it with hd0; if I change it to /dev/sda I get 'no such disk' ... even though /dev/sda is what the other ones use.

I will try your first post answer now

---

### Post by sk3499 on 2011-07-24
> **srs5694 said:**
> When posting text-mode program output, it's helpful to place it between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags. That preserves formatting and keeps it legible.

Your entry #1 just plain won't work on a UEFI boot because that's the way GRUB boots Windows on a BIOS system, not on a UEFI system.

Your entry #2 might not be working because a file may be named differently. You can check the names by examining the files in the EFI System Partition (ESP), which in your case is /dev/sda1. Because you've provided only some of the Boot Info Script output, I can't be sure where (or even if) it's mounted in Linux by default, but it's normally mounted at /boot/efi. Thus, "sudo find /boot/efi" will reveal all of the files on that partition. You can scan the results for the referenced file (/efi/Microsoft/Boot/bootmgfw.efi) to see if it's present, or if it's located in some other directory, and change the pathname reference if it's located somewhere else.

Another option would be to install [rEFIt,]("http://refit.sourceforge.net") which you can configure as the primary boot loader for your system; it will then give you the option of booting Linux or Windows. There are some important caveats with rEFIt, though:


[LIST]
[*]The combined 32-/64-bit version of rEFIt doesn't work on x86-64 UEFI systems (at least, not that I've heard of); you've got to install a straight 64-bit version of the boot loader. The refit package in Ubuntu includes such a version, in /usr/lib/refit/x64/refit.efi; you'd copy that file to its own subdirectory on the ESP (as in /boot/efi/EFI/refit/refit.efi) along with the /usr/lib/refit/refit/refit.conf configuration file.
[*]On some UEFI systems, rEFIt suffers from various types of video glitches when run in its standard graphical mode. If you have such problems, you can edit its refit.conf configuration file and uncomment the "textonly" line. This will run it in text-only mode, which lacks the eye candy but also lacks the video glitches.
[*]rEFIt can only boot other EFI boot loaders; it can't boot any OS directly. Thus, you'll still need both the Windows boot loader and GRUB or some other Linux boot loader to be installed in your ESP. In other words, don't delete either of these boot loaders once you get rEFIt working!
[/LIST]


This is what I get from the find:
```

>>sudo find /boot/efi
/boot/efi
/boot/efi/EFI
/boot/efi/EFI/ubuntu
/boot/efi/EFI/ubuntu/grubx64.efi

```

I don't see the windows file. Using 'sudo find / -name "bootmgfw.efi" ' I also don't see any results.

---

### Post by sk3499 on 2011-07-24
Here is the full script output

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 
    817218283 of the same hard drive for core.img, but core.img can not be 
    found at this location.
 => Windows is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdc.
 => Windows is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda4 has 
                       118606544 sectors, but according to the info from 
                       fdisk, it has 1192348379 sectors.
    Operating System:  
    Boot files:        

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora release 15 (Lovelock) 
                       Kernel on an ()
    Boot files:        /etc/fstab

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   According to the info in the boot sector, sda7 starts 
                       at sector 733008604. But according to the info from 
                       fdisk, sda7 starts at sector 1806750428. According to 
                       the info in the boot sector, sda7 has 0 sectors.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   According to the info in the boot sector, sda8 starts 
                       at sector 733047667. But according to the info from 
                       fdisk, sda8 starts at sector 1806789491. According to 
                       the info in the boot sector, sda8 has 0 sectors.
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda11: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdd1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdd2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 4,294,967,295 4,294,967,295  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       206,847       204,800 EFI System partition
/dev/sda2         206,848       468,991       262,144 Microsoft Reserved Partition (Windows)
/dev/sda3         468,992   614,402,047   613,933,056 Data partition (Windows/Linux)
/dev/sda4     614,402,048 1,806,750,427 1,192,348,380 Data partition (Windows/Linux)
/dev/sda5   2,209,224,704 2,629,066,751   419,842,048 Data partition (Windows/Linux)
/dev/sda6   2,629,066,752 2,639,306,751    10,240,000 Swap partition (Linux)
/dev/sda7   1,806,750,428 1,806,789,490        39,063 EFI System partition
/dev/sda8   1,806,789,491 1,806,828,553        39,063 EFI System partition
/dev/sda9   2,192,482,851 2,209,224,703    16,741,853 Swap partition (Linux)
/dev/sda10  1,806,828,554 2,175,742,616   368,914,063 Data partition (Windows/Linux)
/dev/sda11  2,175,742,617 2,192,482,850    16,740,234 Swap partition (Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
256 heads, 63 sectors/track, 242251 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1 4,294,967,295 4,294,967,295  ee GPT

/dev/sdb1 ends after the last sector of /dev/sdb

GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1              34       262,177       262,144 Microsoft Reserved Partition (Windows)
/dev/sdb2         264,192 3,907,028,991 3,906,764,800 Data partition (Windows/Linux)

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
240 heads, 63 sectors/track, 129201 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048 1,953,521,663 1,953,519,616   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 3000.6 GB, 3000592982016 bytes
256 heads, 63 sectors/track, 363376 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1                   1 4,294,967,295 4,294,967,295  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdd1              34       262,177       262,144 Microsoft Reserved Partition (Windows)
/dev/sdd2         264,192 2,639,306,751 2,639,042,560 Data partition (Windows/Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        923D-EAA5                              vfat       
/dev/sda10       6983d3f0-1eaa-4234-a1fe-f11b80f6bb4d   ext4       
/dev/sda11       28bdf57e-b657-4b0d-b66a-7e646bd6ff6c   swap       
/dev/sda3        26B858B7B8588769                       ntfs       
/dev/sda4        D0F8E52FF8E5150E                       ntfs       DATA_PARTITION
/dev/sda5        982faab9-5079-43cd-b8aa-61b0235e31f4   ext4       
/dev/sda6        5d2b1aa5-030a-40ec-b938-9128237a0adf   swap       
/dev/sda7        554E-0379                              vfat       
/dev/sda8        5E83-C879                              vfat       
/dev/sda9        340bf354-bf1a-4bc3-9eb9-3920ba63b146   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda10       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda7        /boot/efi                vfat       (rw)


=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------

#
# /etc/fstab
# Created by anaconda on Sat Jul 23 15:30:30 2011
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
UUID=982faab9-5079-43cd-b8aa-61b0235e31f4 /                       ext4    defaults        1 1
UUID=923D-EAA5          /boot/efi               vfat    umask=0077,shortname=winnt 0 0
UUID=5d2b1aa5-030a-40ec-b938-9128237a0adf swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

1054.445617676 = 1132.202360832 boot/initramfs-2.6.38.6-26.rc1.fc15.x86_64.img  2
1054.289390564 = 1132.034613248 boot/initramfs-2.6.38.8-35.fc15.x86_64.img     2
1151.565715790 = 1236.484272128 boot/initrd-plymouth.img                       1
1151.571636200 = 1236.490629120 boot/vmlinuz-2.6.38.6-26.rc1.fc15.x86_64       1
1151.577674866 = 1236.497113088 boot/vmlinuz-2.6.38.8-35.fc15.x86_64           1

========================== sda10/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_gpt
insmod ext2
set root='(/dev/sda,gpt10)'
search --no-floppy --fs-uuid --set=root 6983d3f0-1eaa-4234-a1fe-f11b80f6bb4d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(/dev/sda,gpt10)'
search --no-floppy --fs-uuid --set=root 6983d3f0-1eaa-4234-a1fe-f11b80f6bb4d
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-10-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt10)'
    search --no-floppy --fs-uuid --set=root 6983d3f0-1eaa-4234-a1fe-f11b80f6bb4d
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=6983d3f0-1eaa-4234-a1fe-f11b80f6bb4d ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-10-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-10-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt10)'
    search --no-floppy --fs-uuid --set=root 6983d3f0-1eaa-4234-a1fe-f11b80f6bb4d
    echo    'Loading Linux 2.6.38-10-generic ...'
    linux    /boot/vmlinuz-2.6.38-10-generic root=UUID=6983d3f0-1eaa-4234-a1fe-f11b80f6bb4d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-10-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt10)'
    search --no-floppy --fs-uuid --set=root 6983d3f0-1eaa-4234-a1fe-f11b80f6bb4d
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=6983d3f0-1eaa-4234-a1fe-f11b80f6bb4d ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt10)'
    search --no-floppy --fs-uuid --set=root 6983d3f0-1eaa-4234-a1fe-f11b80f6bb4d
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=6983d3f0-1eaa-4234-a1fe-f11b80f6bb4d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/11_Windows ###
menuentry "Windows 7" {
insmod part_gpt
insmod ntfs
set root='(/dev/sda,gpt3)'
chainloader +1
}
### END /etc/grub.d/11_Windows ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt10)'
    search --no-floppy --fs-uuid --set=root 6983d3f0-1eaa-4234-a1fe-f11b80f6bb4d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt10)'
    search --no-floppy --fs-uuid --set=root 6983d3f0-1eaa-4234-a1fe-f11b80f6bb4d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Fedora release 15 (Lovelock) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt5)'
    search --no-floppy --fs-uuid --set=root 982faab9-5079-43cd-b8aa-61b0235e31f4
    linux /boot/vmlinuz-2.6.38.6-26.rc1.fc15.x86_64 root=/dev/sda5
    initrd /boot/initramfs-2.6.38.6-26.rc1.fc15.x86_64.img
}
menuentry "Fedora release 15 (Lovelock) (on /dev/sda5)" --class gnu-linux --class gnu --class os {
    insmod part_gpt
    insmod ext2
    set root='(/dev/sda,gpt5)'
    search --no-floppy --fs-uuid --set=root 982faab9-5079-43cd-b8aa-61b0235e31f4
    linux /boot/vmlinuz-2.6.38.8-35.fc15.x86_64 root=/dev/sda5
    initrd /boot/initramfs-2.6.38.8-35.fc15.x86_64.img
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
--------------------------------------------------------------------------------

=============================== sda10/etc/fstab: ===============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda10 during installation
UUID=6983d3f0-1eaa-4234-a1fe-f11b80f6bb4d /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda7 during installation
UUID=554E-0379  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda11 during installation
UUID=28bdf57e-b657-4b0d-b66a-7e646bd6ff6c none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda10: Location of files loaded by Grub: ===================

           GiB - GB             File                                 Fragment(s)

 879.832585335 = 944.713044992  boot/grub/grub.cfg                             1
 863.528393745 = 927.206552576  boot/initrd.img-2.6.38-10-generic              1
 863.500493050 = 927.176594432  boot/initrd.img-2.6.38-8-generic               2
 862.446118355 = 926.044468224  boot/vmlinuz-2.6.38-10-generic                 2
 957.695809364 = 1028.318045184 boot/vmlinuz-2.6.38-8-generic                  1
 863.528393745 = 927.206552576  initrd.img                                     1
 863.500493050 = 927.176594432  initrd.img.old                                 2
 862.446118355 = 926.044468224  vmlinuz                                        2
 957.695809364 = 1028.318045184 vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 02 fe 19  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 20 03 00 01 03 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 a5 ea 3d 92 4e  4f 20 4e 41 4d 45 20 20  |..)..=.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200

Unknown BootLoader on sdb2

00000000  5c 86 8f c0 35 20 dc 56  74 ea 8e 64 75 5c 29 d6  |\...5 .Vt..du\).|
00000010  79 2a 96 15 92 99 48 62  43 ca d5 04 ee 3b c3 6e  |y*....HbC....;.n|
00000020  7f af 82 74 67 79 3f 1b  c0 68 4d d8 ef 4e fc f1  |...tgy?..hM..N..|
00000030  71 7c f7 9b 2f 94 d1 90  08 a7 56 a0 af e4 47 b8  |q|../.....V...G.|
00000040  77 aa 8d 83 4a e0 92 29  5f e2 f5 e6 12 e5 7d c4  |w...J..)_.....}.|
00000050  de ea 6c 90 16 fa f3 91  97 55 2a 18 a8 24 14 ee  |..l......U*..$..|
00000060  2d c6 ac b8 c3 0c 95 9f  1d 77 5e 61 ca a4 3a 5f  |-........w^a..:_|
00000070  e2 08 da 2c 1c 2b b3 42  ec d4 f8 b2 bc 59 75 c1  |...,.+.B.....Yu.|
00000080  3e da 85 e2 a9 67 63 f3  d8 49 43 fc a6 f4 05 b5  |>....gc..IC.....|
00000090  f8 2e bf 30 82 2e d4 64  ee ae 0b 00 b3 b9 d7 6e  |...0...d.......n|
000000a0  87 dd 71 e8 da af ac ba  0b 77 61 76 84 d7 c5 f3  |..q......wav....|
000000b0  67 f0 0d ca 7b 7b 62 db  15 a4 34 3a 4c 20 9f 09  |g...{{b...4:L ..|
000000c0  b4 19 17 7c 4a d4 d4 d8  77 0b ac 29 4b 6a 05 dd  |...|J...w..)Kj..|
000000d0  07 a0 44 af 04 4b ac 73  1c d6 0f c5 85 99 5c 27  |..D..K.s......\'|
000000e0  8f d9 a4 51 01 86 99 62  86 b6 e3 c1 95 8f a6 e8  |...Q...b........|
000000f0  dc f9 08 92 58 de 97 2f  db f7 29 d2 49 1d c8 1e  |....X../..).I...|
00000100  48 f2 1c e8 e2 95 af c1  a9 d1 ed 78 f6 37 43 c9  |H..........x.7C.|
00000110  ac 77 15 57 ea e1 72 96  4e df ca cb 06 8d d0 6f  |.w.W..r.N......o|
00000120  a3 58 78 9a b2 81 ba 80  b0 85 7d 62 4c f2 fb 34  |.Xx.......}bL..4|
00000130  5a 6a 89 8d 2c 30 3e 8d  20 69 b8 8d a4 f5 24 97  |Zj..,0>. i....$.|
00000140  a2 6d fb c9 8f 2c 48 02  4f 46 53 e4 2b a1 e3 98  |.m...,H.OFS.+...|
00000150  87 2f 49 21 26 e6 45 1e  14 e5 a5 68 d5 7b 5e 6b  |./I!&.E....h.{^k|
00000160  a3 c7 2c ae a5 b6 87 2e  e2 61 3b 4e 4b c0 cd a0  |..,......a;NK...|
00000170  c4 40 85 67 f5 9c 54 a2  64 bc 92 b1 ae 27 6f 58  |.@.g..T.d....'oX|
00000180  df 16 37 fa b8 f3 9f be  63 a7 5b f6 89 63 89 b1  |..7.....c.[..c..|
00000190  13 d1 e1 75 6c ba 8b 16  c6 15 4d 03 5d 83 5f f3  |...ul.....M.]._.|
000001a0  c9 1f 89 55 57 24 82 15  63 89 17 90 7d 70 4d e2  |...UW$..c...}pM.|
000001b0  a4 8d 84 59 3a 3c ab 70  cc 7e 8c 2e 43 fe 6e a6  |...Y:<.p.~..C.n.|
000001c0  9b c6 a3 fd e2 a1 dd a0  bd cf ab c1 49 bb 28 fc  |............I.(.|
000001d0  46 d6 a2 72 3f 30 d2 d3  75 f3 ef ff 70 ff 9a 05  |F..r?0..u...p...|
000001e0  1a 79 98 1d b3 55 ff 91  04 21 2d e8 f6 b5 3d 80  |.y...U...!-...=.|
000001f0  e1 47 ec 62 3c a8 56 22  b9 0b 1d 92 a4 8d c6 86  |.G.b<.V"........|
00000200

Unknown BootLoader on sdc1

00000000  32 3c 53 70 f9 a0 22 cb  aa c9 4b c8 24 3c a5 50  |2<Sp.."...K.$<.P|
00000010  18 34 cf fc ac 5b 51 3c  cd 46 8b 02 94 11 a0 6c  |.4...[Q<.F.....l|
00000020  09 08 57 1b 21 5c 20 ff  89 c8 94 b2 38 e5 5b 53  |..W.!\ .....8.[S|
00000030  b5 b9 27 9c 67 0c 97 76  52 de e5 d3 a8 97 c3 21  |..'.g..vR......!|
00000040  d8 bf 3e 2c 0b cb 2b ce  3b fe 9d c2 aa c6 59 b0  |..>,..+.;.....Y.|
00000050  04 6f 39 c2 0c f8 34 7d  a4 98 8c 2d 1f b6 c9 99  |.o9...4}...-....|
00000060  90 f2 ca 80 87 7a 11 8a  b9 1c 5c be e8 32 92 c9  |.....z....\..2..|
00000070  7a ad 8a b6 f8 c0 55 ee  da 5b a2 c6 24 f0 db f4  |z.....U..[..$...|
00000080  ac 6e ed c6 f2 8c b4 ca  fc f2 eb 59 11 e7 25 fd  |.n.........Y..%.|
00000090  31 e3 f3 45 8f 37 50 b4  a4 ca 75 d1 ea 8e e1 7c  |1..E.7P...u....||
000000a0  40 f4 b8 1f 48 50 7c cf  39 65 86 02 6d 7e 9d 8e  |@...HP|.9e..m~..|
000000b0  31 d8 f7 57 1e e2 f4 87  9b 15 82 a6 68 ac ae de  |1..W........h...|
000000c0  ff a7 b1 ee 1c d7 91 61  6a 94 30 38 e6 23 95 bb  |.......aj.08.#..|
000000d0  a1 bf e6 4f 77 8a 67 fe  fc f0 d7 7b 5a ab 8d 61  |...Ow.g....{Z..a|
000000e0  36 b9 db 51 76 8b 81 be  8a b9 cf d8 72 e1 62 a6  |6..Qv.......r.b.|
000000f0  81 9a 2b 70 a1 6f 42 93  39 48 f2 e4 db 96 c5 18  |..+p.oB.9H......|
00000100  6d 06 5e 5f 67 a3 2f 16  d1 90 81 a4 2f b7 d2 55  |m.^_g./...../..U|
00000110  58 27 e5 c8 0c 5b 63 e6  0e 7d c4 40 71 d6 50 15  |X'...[c..}.@q.P.|
00000120  5e bf 6a e5 79 80 9a f8  39 fc d9 ff 42 e0 25 35  |^.j.y...9...B.%5|
00000130  5c a3 1c df d3 a1 7f 35  8f e4 56 53 96 b5 20 ef  |\......5..VS.. .|
00000140  41 61 c7 30 d6 1f 19 a9  17 15 20 85 b6 a8 8e d1  |Aa.0...... .....|
00000150  ed 0b 01 e8 de 39 9a 58  cb 94 fa 10 60 c6 62 f2  |.....9.X....`.b.|
00000160  4a 81 9e 41 79 d4 2a 9a  8e 27 f6 8a 6d 66 92 7c  |J..Ay.*..'..mf.||
00000170  df 17 0d 2d 0f e6 ac 2c  a2 dc 33 51 f0 99 54 a6  |...-...,..3Q..T.|
00000180  ca b4 27 d8 e7 fc 32 3d  db 82 b4 a4 ba a2 01 06  |..'...2=........|
00000190  50 89 f2 89 94 f1 d3 f1  32 ff 85 b1 c8 c8 fa 69  |P.......2......i|
000001a0  5f 62 5c a1 fc 52 cf 91  6e a0 47 e4 55 d7 a8 c3  |_b\..R..n.G.U...|
000001b0  6c c6 dd 42 02 40 23 0d  d2 5a 44 c0 fe ee 87 53  |l..B.@#..ZD....S|
000001c0  37 f1 fd 6f a8 00 1a f5  2b c8 19 3b 51 a3 3e ef  |7..o....+..;Q.>.|
000001d0  cd af 0a fa 9a fa 8e 1d  40 f1 1b 0b 7a 6e 21 5c  |........@...zn!\|
000001e0  e3 3c f3 3d b6 20 f2 80  34 fd 13 63 32 5a 3f 60  |.<.=. ..4..c2Z?`|
000001f0  b8 c1 0d 07 f4 10 16 2a  3b 08 5c f9 b3 c4 b7 e3  |.......*;.\.....|
00000200

Unknown BootLoader on sdd2

00000000  94 0d e2 70 ea 2c 7f 74  9f 74 1c 6e 43 4c cf 84  |...p.,.t.t.nCL..|
00000010  04 5f 8b b1 ed eb 5a 2e  54 62 2e 82 5f e5 84 69  |._....Z.Tb.._..i|
00000020  b9 b5 a5 9c 79 f9 95 30  13 f0 fe c1 14 e5 e5 ea  |....y..0........|
00000030  fc 94 6e 49 6d 0d 28 cd  5a 10 a2 ed 7e de 69 c1  |..nIm.(.Z...~.i.|
00000040  41 94 5e 21 9e 9b 0e 35  f7 e6 34 aa a8 a8 79 93  |A.^!...5..4...y.|
00000050  31 37 fc 9e d1 fd fb 02  07 af 4d 74 d6 d8 76 04  |17........Mt..v.|
00000060  37 e9 a1 fe 92 7a 39 f0  5a 0e e5 dd 97 c8 c1 ea  |7....z9.Z.......|
00000070  27 19 ca 11 70 29 76 24  b4 f7 f4 8f c6 6c 04 f3  |'...p)v$.....l..|
00000080  d4 18 7c 79 e7 62 f3 1e  39 e2 6a 18 82 a2 d9 a8  |..|y.b..9.j.....|
00000090  39 80 fc 8e 69 16 c8 25  10 02 91 f0 7f 44 e3 ef  |9...i..%.....D..|
000000a0  50 67 f2 f7 7c 26 6b 11  0b 6e bb 01 2a 0b 3d 2d  |Pg..|&k..n..*.=-|
000000b0  20 7d 75 51 b8 16 9c d8  f6 2d 39 63 1c da a6 43  | }uQ.....-9c...C|
000000c0  b9 18 1f a6 08 04 ef 8a  09 6b a9 2d b5 ba 74 94  |.........k.-..t.|
000000d0  c4 50 24 ca e1 7b 4c 27  cb 98 c9 06 d7 f4 13 3e  |.P$..{L'.......>|
000000e0  44 c6 1c 80 9d 58 23 0f  27 ce 16 b6 10 2c 5a f4  |D....X#.'....,Z.|
000000f0  c7 d3 70 6d 92 e3 c8 4e  8e 96 28 fa a0 72 e5 59  |..pm...N..(..r.Y|
00000100  14 1a 21 24 1a 63 05 ae  f0 c4 97 6c 87 a2 50 f8  |..!$.c.....l..P.|
00000110  a9 43 f7 56 1f 86 c2 01  7b 98 a1 4f 7c 13 28 52  |.C.V....{..O|.(R|
00000120  f7 19 e5 f1 4c 7c 39 4d  de 5b 34 a5 21 36 67 a0  |....L|9M.[4.!6g.|
00000130  5d 23 18 cb e7 4d a5 95  a0 95 5b 0c 18 5b e4 f1  |]#...M....[..[..|
00000140  42 e8 22 84 12 74 07 43  fd 0c 96 c8 9b a7 26 e3  |B."..t.C......&.|
00000150  f3 46 45 0e 62 a3 29 4b  e7 41 8e 82 c4 a7 77 83  |.FE.b.)K.A....w.|
00000160  25 33 1a 33 d5 5e b9 2e  36 ba 46 25 cd df a1 ca  |%3.3.^..6.F%....|
00000170  bb f4 3d 26 e7 2b 8e cd  10 94 f2 8c 70 00 fe c8  |..=&.+......p...|
00000180  dc 53 31 bb fa 1e 16 2b  ac 2d 7a c5 ac f2 db c0  |.S1....+.-z.....|
00000190  3a 08 9e 80 0f 09 08 c9  f9 0f 1b 4e 5b fc 7a 7f  |:..........N[.z.|
000001a0  15 5a 0b 1f bd df 4f 43  81 72 51 a2 ec b6 db b6  |.Z....OC.rQ.....|
000001b0  2c 62 90 27 13 52 14 d5  05 72 4a 03 57 a3 36 48  |,b.'.R...rJ.W.6H|
000001c0  08 aa 0b a2 4e a2 d6 77  5d 38 b4 f7 44 a2 73 c8  |....N..w]8..D.s.|
000001d0  f8 85 bb e3 b7 7f 1d ad  54 38 54 25 c9 1c b9 7b  |........T8T%...{|
000001e0  fa b5 44 46 e9 f7 5e 75  8a 80 a9 35 4e 60 16 e3  |..DF..^u...5N`..|
000001f0  04 e5 44 a0 5c 49 2f 7b  b3 00 0d 5f ac 2e 4a 35  |..D.\I/{..._..J5|
00000200




```

---

### Post by oldfred on 2011-07-24
@srs5694
Boot script does not parse efi partition nor look for efi boot files. We need to have it modified to also look for those files, but I do not know details nor have a way to test. Perhaps you could PM Gert Hulselmans with the files & folders to include in the scripts search. It looks like it should be relatively easy to modify. (Famous last words from someone who knows little about scripts.)

Whey are there two more efi partitions sda7 & sda8. Is there any data in them?

---

### Post by sk3499 on 2011-07-24
> **oldfred said:**
> @srs5694
Boot script does not parse efi partition nor look for efi boot files. We need to have it modified to also look for those files, but I do not know details nor have a way to test. Perhaps you could PM Gert Hulselmans with the files & folders to include in the scripts search. It looks like it should be relatively easy to modify. (Famous last words from someone who knows little about scripts.)

Whey are there two more efi partitions sda7 & sda8. Is there any data in them?
I have no idea why there are so many partitions the ubuntu and fedora installers created a bunch more than I had.

---

### Post by srs5694 on 2011-07-24
I hadn't noticed the fact that there are *three* ESPs on the disk. I recommend consolidating all the files from all three of them on /dev/sda1 and then editing /etc/fstab to mount /dev/sda1 at /boot/efi. If the bootmgfw.efi file is on a different ESP than the grubx64.efi file, then that might conceivably account for the problem.

FWIW, this is all probably a result of some flakiness in both the Windows and Ubuntu installers:


[list]
[*]Windows 7's installer insists on seeing a FAT-32 ESP. If you've got a FAT-16 ESP, the Windows installer will attempt to create a new ESP.
[*]Ubuntu's installer creates a new FAT-16 filesystem on the ESP, even if a valid ESP already exists. This renders Windows unbootable.
[/list]


Since you can boot Windows by selecting it in the firmware, my assumption was that you'd somehow avoided the catch-22 of the above two issues; however, it now appears that something more complex has happened. My guess is that you've done two or three Linux installations, and perhaps used the Windows install disc to repair a broken installation. This has left you with three swap partitions, three ESPs, and possibly some redundant or unused Linux installations. You need just one swap partition and one ESP. How many Linux partitions you need is up to you, of course. In any event, you should figure out what's on each of those partitions, delete the ones you don't need, and resize the rest to fill the space (or just leave gaps if they're small -- your /dev/sda7 and /dev/sda8 are puny little things, for instance).

---

### Post by sk3499 on 2011-07-25
> **srs5694 said:**
> I hadn't noticed the fact that there are *three* ESPs on the disk. I recommend consolidating all the files from all three of them on /dev/sda1 and then editing /etc/fstab to mount /dev/sda1 at /boot/efi. If the bootmgfw.efi file is on a different ESP than the grubx64.efi file, then that might conceivably account for the problem.

FWIW, this is all probably a result of some flakiness in both the Windows and Ubuntu installers:


[list]
[*]Windows 7's installer insists on seeing a FAT-32 ESP. If you've got a FAT-16 ESP, the Windows installer will attempt to create a new ESP.
[*]Ubuntu's installer creates a new FAT-16 filesystem on the ESP, even if a valid ESP already exists. This renders Windows unbootable.
[/list]


Since you can boot Windows by selecting it in the firmware, my assumption was that you'd somehow avoided the catch-22 of the above two issues; however, it now appears that something more complex has happened. My guess is that you've done two or three Linux installations, and perhaps used the Windows install disc to repair a broken installation. This has left you with three swap partitions, three ESPs, and possibly some redundant or unused Linux installations. You need just one swap partition and one ESP. How many Linux partitions you need is up to you, of course. In any event, you should figure out what's on each of those partitions, delete the ones you don't need, and resize the rest to fill the space (or just leave gaps if they're small -- your /dev/sda7 and /dev/sda8 are puny little things, for instance).

Just for the record, no i never did a windows repair, though I am contemplating it, but I doubt this would work any better with the windows BCD. (Unless someone knows something I don't about how this might be easier using the windows boot manager).

I also only did 1 install of fedora then 1 install of ubuntu.

I don't know if I want to mess with the linux partitions, they are working fine, and the drives 3TB, I don't really need the 10GB wasted by the 2 redundant swap spaces.

Lacking a better solution for now, I am thinking about just telling the firmware to boot windows by default (since I use it more on that machine), and skip GRUB, unless I specifically tell it to boot to GRUB.

---

