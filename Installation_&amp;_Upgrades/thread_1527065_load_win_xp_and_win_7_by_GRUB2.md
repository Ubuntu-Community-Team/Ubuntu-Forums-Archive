---
title: "load win xp and win 7 by GRUB2"
date: 2010-07-08
forum: Installation &amp; Upgrades
---

### Post by satanowicz on 2010-07-08
hi,

I'm using ubuntu 10.4 and GRUB2
How to force GRUB to load windows xp or windows 7 directly?
Now i have to load the win7 loader and then choose the M$ system I want
here's my boot info script output:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Dysk /dev/sda: 500.1 GB, bajtów: 500107862016
g&#322;owic: 255, sektorów/&#347;cie&#380;k&#281;: 63, cylindrów: 60801, w sumie sektorów: 976773168
Jednostka = sektorów, czyli 1 * 512 = 512 bajtów
Rozmiar sektora (logiczny/fizyczny) w bajtach: 512 / 512

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,046    47,696,984    47,694,939   f W95 Ext d (LBA)
/dev/sda5               2,048    20,973,567    20,971,520  27 Hidden HPFS/NTFS
/dev/sda6          20,973,632    21,178,367       204,736  27 Hidden HPFS/NTFS
/dev/sda7          21,178,432    46,331,459    25,153,028   7 HPFS/NTFS
/dev/sda8          46,331,523    47,696,984     1,365,462  82 Linux swap / Solaris
/dev/sda2    *    767,055,555   867,718,844   100,663,290   7 HPFS/NTFS
/dev/sda3         867,718,845   909,664,559    41,945,715   7 HPFS/NTFS
/dev/sda4         909,664,560   976,768,064    67,103,505  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1: PTTYPE="dos" 
/dev/sda2        58627C4859695D49                       ntfs       win7                          
/dev/sda3        7A8C5CBF8C5C7819                       ntfs                                     
/dev/sda4        568b05dc-fa76-4f52-afdc-6dc609a0e885   ext4                                     
/dev/sda5        E01849AD1849840E                       ntfs       BIOS_RVY                      
/dev/sda6        01CB1D994C7A0CE0                       ntfs       System                        
/dev/sda7        01CB1D99720BF860                       ntfs       OS_Install                    
/dev/sda8        f173f55c-1680-461d-a06a-1fe92d5eba75   swap       swap                          
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw,errors=remount-ro)


================================ sda2/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT 

=========================== sda4/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,4)'
search --no-floppy --fs-uuid --set 568b05dc-fa76-4f52-afdc-6dc609a0e885
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
insmod ext2
set root='(hd0,4)'
search --no-floppy --fs-uuid --set 568b05dc-fa76-4f52-afdc-6dc609a0e885
set locale_dir=($root)/boot/grub/locale
set lang=pl
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, za pomoc&#261; systemu Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 568b05dc-fa76-4f52-afdc-6dc609a0e885
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=568b05dc-fa76-4f52-afdc-6dc609a0e885 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, za pomoc&#261; systemu Linux 2.6.32-22-generic (tryb ratunkowy)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 568b05dc-fa76-4f52-afdc-6dc609a0e885
    echo    'Wczytywanie systemu Linux 2.6.32-22-generic...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=568b05dc-fa76-4f52-afdc-6dc609a0e885 ro single 
    echo    'Wczytywanie pocz&#261;tkowego dysku RAM...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 568b05dc-fa76-4f52-afdc-6dc609a0e885
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 568b05dc-fa76-4f52-afdc-6dc609a0e885
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 58627c4859695d49
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda5)" {
    insmod ntfs
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e01849ad1849840e
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda6)" {
    insmod ntfs
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 01cb1d994c7a0ce0
    chainloader +1
}
menuentry "Windows XP (loader) (on /dev/sda3)" {
    insmod ntfs
    set root=(hd0,3)
    chainloader +1
}
#menuentry "Windows 7 (loader) (on /dev/sda7)" {
#    insmod ntfs
#    set root='(hd0,7)'
#    search --no-floppy --fs-uuid --set 01cb1d99720bf860
#    chainloader +1
#}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=568b05dc-fa76-4f52-afdc-6dc609a0e885 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=f173f55c-1680-461d-a06a-1fe92d5eba75 none            swap    sw              0       0

=================== sda4: Location of files loaded by Grub: ===================


 474.4GB: boot/grub/core.img
 487.3GB: boot/grub/grub.cfg
 475.5GB: boot/initrd.img-2.6.32-22-generic
 466.1GB: boot/vmlinuz-2.6.32-22-generic
 475.5GB: initrd.img
 466.1GB: vmlinuz
```

---

### Post by oldfred on 2010-07-09
[http://ubuntuforums.org/showthread.php?t=1279218&highlight=booting+MS+products](http://ubuntuforums.org/showthread.php?t=1279218&highlight=booting+MS+products)
louieb's suggestion:
Just a note about dual booting 2 MS products. When you install the 2nd one - the installer will put its boot loader in the partition with the boot flag on (usually the partition holding the 1st MS product). And the 2nd product can only be booted thru the boot loader in the 1st product.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by satanowicz on 2010-07-09
both win7 and win xp are installed on primary partitions
the boot flag is set on the win7 partition 
if I understand You correctly I have to change the win xp partitions flag to boot?
and what do I have to change in GRUB configuration to let it boot those OS directly?

I've tried to boot win xp directly adding this in GRUB:
```
menuentry "Windows XP Pro" {
      set root=(hd0,3)
      chainloader +1
}
```it gives me a message about missing NTLDR

---

### Post by Mark Phelps on 2010-07-09
Read what oldfred told you -- in detail!

You can't select individual MS OS's in a multi-OS situation just by adding entries to GRUB.  There is a LOT of work involved -- and oldfred told you what needs to be done.

There is no shortcut around the detailed work required.

---

### Post by oldfred on 2010-07-09
You may be able to move the boot flag and run the standard set of repairs to the second install of windows to get it to put back the boot files. Not sure if it works, suggested it once or twice and never got an answer. In theory it is just like repairing after deleting the original  windows install which several have successfully done. You may be able to copy the XP files back to the XP partition and then run the repairs to make sure it sees them correctly.

It is very difficult to make windows in a logical partition boot as it generally has to boot thru a windows partition in a primary partition. So the install in sda7 may not be separately bootable. Boot flags only go on a primary partition (at least as far as windows is concerned).

Win 7 or Vista files:
/bootmgr /Boot/BCD /Windows/System32/winload.exe

XP files
/boot.ini /bootmgr /ntldr

You can manually edit boot.ini to have correct partition info, but have to use BCDEDIT.exe to modify Windows Vista or 7 boot options.

---

