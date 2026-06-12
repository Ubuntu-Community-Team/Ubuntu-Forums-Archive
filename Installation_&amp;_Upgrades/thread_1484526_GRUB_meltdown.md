---
title: "GRUB meltdown?"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by Moozillaaa on 2010-05-15
I rebooted, and got a new GRUB error:

Anybody seen this before?

        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        set quiet=1
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 7b4afbe0-28fe-4403-bd86-c4364bf10f98
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=7b4afbe0-28fe-4403-bd86-c4364bf10f98 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic

---

### Post by kansasnoob on 2010-05-15
Please post the output of the Boot Info Script:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Moozillaaa on 2010-05-15
I ran this executable last week...

:confused:> 

chucknb@chucknb-desktop:~$ sudo bash boot_info_script055.sh
[sudo] password for chucknb: 
bash: boot_info_script055.sh: No such file or directory
chucknb@chucknb-desktop:~$ 


---

### Post by kansasnoob on 2010-05-15
You must specify the file location. Like I have it DL'ed in my Downloads and I just cd <Location>, example (notice at the end if you've run it before it even gives you the name of the new RESULTS.txt):

> lance@lance-desktop:~$ cd Downloads
lance@lance-desktop:~/Downloads$ sudo bash boot_info_script055.sh
[sudo] password for lance: 
Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda4 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
Searching sda7 for information... 
Searching sda8 for information... 
Searching sda9 for information... 
Searching sda10 for information... 
Searching sda11 for information... 
Searching sda12 for information... 
Searching sda13 for information... 
Searching sda14 for information... 
Searching sda15 for information... 
Searching sda16 for information... 
Searching sda17 for information... 
Searching sda18 for information... 
Searching sda19 for information... 
Searching sdb1 for information... 
Searching sdb2 for information... 
Searching sdb5 for information... 
Searching sdb6 for information... 
Searching sdb7 for information... 
Finished. The results are in the file **[COLOR="Red"]RESULTS4.txt[/COLOR]** located in /mnt/sda9

---

### Post by Moozillaaa on 2010-05-15
Device 'c', is a USB temporary device (to boot this diagnostics)

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
 => HP/Gateway is installed in the MBR of /dev/sdb
 => Grub 0.97 is installed in the MBR of /dev/sdc and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda4 and 
                       looks at sector 27459018 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #4 for 
                       /boot/grub/grub.conf.
    Operating System:  Fedora release 10 (Cambridge) 
                       Kernel on an ()
    Boot files/dirs:   /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOT/BCD

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sdb5 and 
                       looks at sector 132472595 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  PCLinuxOS release 2007 
                       (PCLinuxOS) for i586 Kernel 2.6.18.8.tex5 on a 
                       Dual-processor i686 /
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.4 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4b36bdea

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    25,607,609    25,607,547   7 HPFS/NTFS
/dev/sda2          50,122,800   173,003,984   122,881,185  83 Linux
/dev/sda3         173,003,985   234,436,544    61,432,560   5 Extended
/dev/sda5         173,004,048   189,374,219    16,370,172  83 Linux
/dev/sda6         226,853,928   234,436,544     7,582,617  82 Linux swap / Solaris
/dev/sda7         189,374,283   197,551,304     8,177,022  82 Linux swap / Solaris
/dev/sda8         197,551,368   226,853,864    29,302,497  83 Linux
/dev/sda4          25,607,610    50,122,799    24,515,190  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x393115b2

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   128,327,219   128,327,157   7 HPFS/NTFS
/dev/sdb2         217,288,704   234,432,511    17,143,808   7 HPFS/NTFS
/dev/sdb3         128,327,220   169,341,164    41,013,945   5 Extended
/dev/sdb5         128,327,283   169,341,164    41,013,882  83 Linux
/dev/sdb4         169,341,165   203,125,859    33,784,695  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb015a805

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    81,915,434    81,915,372   7 HPFS/NTFS
/dev/sdc2          81,915,435   450,558,989   368,643,555  83 Linux
/dev/sdc3         450,558,990   458,752,139     8,193,150  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        D6AC129BF4974A14                       ntfs       XPPro                         
/dev/sda2        fdcf20ef-a198-45be-877c-3dbc01c64ef5   ext3                                     
/dev/sda4        e167cb3e-f1fc-4852-804a-a22457aece41   ext3       /                             
/dev/sda6        5cc048de-889c-4a1c-ab56-45c1e2933d6d   swap                                     
/dev/sda7        ad886fc1-dcb3-4c66-b627-2b59da7500eb   swap                                     
/dev/sdb1        FEFEB4A2FEB4549D                       ntfs                                     
/dev/sdb2        10FCA6F2FCA6D0F0                       ntfs       HP_RECOVERY                   
/dev/sdb4        b41368bf-9c87-48fc-ab6f-191cadc42e45   ext3                                     
/dev/sdb5        0b8d1aab-414a-4f4e-9e53-8a515ad426e6   ext2                                     
/dev/sdc1        809C18619C1853CE                       ntfs                                     
/dev/sdc2        32a7f436-76a6-4cca-966f-2d24d2e2702a   ext3                                     
/dev/sdc3        73f18d48-1e6c-4bb6-ab1f-1e567b41622c   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc2        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sdc1        /media/disk              fuseblk    (rw,nosuid,nodev,noatime,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer 

=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root=(hd0,2)
search --no-floppy --fs-uuid --set fdcf20ef-a198-45be-877c-3dbc01c64ef5
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
menuentry "Ubuntu, Linux 2.6.31-21-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set fdcf20ef-a198-45be-877c-3dbc01c64ef5
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=fdcf20ef-a198-45be-877c-3dbc01c64ef5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set fdcf20ef-a198-45be-877c-3dbc01c64ef5
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=fdcf20ef-a198-45be-877c-3dbc01c64ef5 ro single 
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set fdcf20ef-a198-45be-877c-3dbc01c64ef5
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=fdcf20ef-a198-45be-877c-3dbc01c64ef5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set fdcf20ef-a198-45be-877c-3dbc01c64ef5
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=fdcf20ef-a198-45be-877c-3dbc01c64ef5 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set fdcf20ef-a198-45be-877c-3dbc01c64ef5
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=fdcf20ef-a198-45be-877c-3dbc01c64ef5 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set fdcf20ef-a198-45be-877c-3dbc01c64ef5
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=fdcf20ef-a198-45be-877c-3dbc01c64ef5 ro single 
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
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set d6ac129bf4974a14
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Fedora release 10 (Cambridge) (on /dev/sda4)" {
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set e167cb3e-f1fc-4852-804a-a22457aece41
    linux /boot/vmlinuz-2.6.26.8-57.fc8 root=/dev/sda4
}
menuentry "Fedora release 10 (Cambridge) (on /dev/sda4)" {
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set e167cb3e-f1fc-4852-804a-a22457aece41
    linux /boot/vmlinuz-2.6.27.21-170.2.56.fc10.i686 root=/dev/sda4
}
menuentry "Fedora release 10 (Cambridge) (on /dev/sda4)" {
    insmod ext2
    set root=(hd0,4)
    search --no-floppy --fs-uuid --set e167cb3e-f1fc-4852-804a-a22457aece41
    linux /boot/vmlinuz-2.6.27.41-170.2.117.fc10.i686 root=/dev/sda4
}
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set fefeb4a2feb4549d
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb2)" {
    insmod ntfs
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set 10fca6f2fca6d0f0
    chainloader +1
}
menuentry "PCLOS (on /dev/sdb5)" {
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 0b8d1aab-414a-4f4e-9e53-8a515ad426e6
    linux /boot/vmlinuz BOOT_IMAGE=linux root=/dev/sdb5 acpi=on resume=/dev/sda7 splash=silent vga=788
    initrd (hd1,4)/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sdb5)" {
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 0b8d1aab-414a-4f4e-9e53-8a515ad426e6
    linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=/dev/sdb5 acpi=on resume=/dev/sda7
    initrd (hd1,4)/boot/initrd.img
}
menuentry "failsafe (on /dev/sdb5)" {
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set 0b8d1aab-414a-4f4e-9e53-8a515ad426e6
    linux /boot/vmlinuz BOOT_IMAGE=failsafe root=/dev/sdb5 failsafe acpi=on resume=/dev/sda7
    initrd (hd1,4)/boot/initrd.img
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry "Fedora release 10 (Cambridge) (on /dev/sda4)" {
    insmod ext2
    set root=(hd0,4)
        search --no-floppy --fs-uuid --set e167cb3e-f1fc-4852-804a-a22457aece41
        linux /boot/vmlinuz-2.6.26.8-57.fc8
        initrd /boot/initrd-2.6.26.8-57.fc8.img
}
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=fdcf20ef-a198-45be-877c-3dbc01c64ef5 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=5cc048de-889c-4a1c-ab56-45c1e2933d6d none            swap    sw              0       0
# swap was on /dev/sda7 during installation
UUID=ad886fc1-dcb3-4c66-b627-2b59da7500eb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  45.9GB: boot/grub/core.img
  82.0GB: boot/grub/grub.cfg
  46.0GB: boot/initrd.img-2.6.31-14-generic
  46.0GB: boot/initrd.img-2.6.31-20-generic
  78.2GB: boot/initrd.img-2.6.31-21-generic
  45.9GB: boot/vmlinuz-2.6.31-14-generic
  46.0GB: boot/vmlinuz-2.6.31-20-generic
  78.3GB: boot/vmlinuz-2.6.31-21-generic
  78.2GB: initrd.img
  46.0GB: initrd.img.old
  78.3GB: vmlinuz
  46.0GB: vmlinuz.old

=============================== sda4/etc/fstab: ===============================

LABEL=/                 /                       ext3    defaults        1 1
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
/dev/sda5               swap                    swap    defaults        0 0

=================== sda4: Location of files loaded by Grub: ===================


  14.0GB: boot/grub/stage2
  16.5GB: boot/initrd-2.6.26.8-57.fc8.img
  16.6GB: boot/initrd-2.6.27.21-170.2.56.fc10.i686.img
  16.4GB: boot/initrd-2.6.27.41-170.2.117.fc10.i686.img
  16.5GB: boot/vmlinuz-2.6.26.8-57.fc8
  16.3GB: boot/vmlinuz-2.6.27.21-170.2.56.fc10.i686
  16.3GB: boot/vmlinuz-2.6.27.41-170.2.117.fc10.i686

=========================== sdb5/boot/grub/menu.lst: ===========================

timeout 10
color black/cyan yellow/cyan
gfxmenu (hd1,4)/usr/share/gfxboot/themes/pclinuxos/boot/message
default 0

title PCLOS
kernel (hd1,4)/boot/vmlinuz BOOT_IMAGE=linux root=/dev/sdb5  acpi=on resume=/dev/sda7 splash=silent vga=788
initrd (hd1,4)/boot/initrd.img

title linux-nonfb
kernel (hd1,4)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=/dev/sdb5  acpi=on resume=/dev/sda7
initrd (hd1,4)/boot/initrd.img

title failsafe
kernel (hd1,4)/boot/vmlinuz BOOT_IMAGE=failsafe root=/dev/sdb5  failsafe acpi=on resume=/dev/sda7
initrd (hd1,4)/boot/initrd.img

title XPPro
root (hd0,0)
makeactive
chainloader +1

title Vista
root (hd1,0)
map (0x81) (0x80)
map (0x80) (0x81)
makeactive
chainloader +1

title HP Vista Recovery
root (hd1,1)
map (0x81) (0x80)
map (0x80) (0x81)
makeactive
chainloader +1

=============================== sdb5/etc/fstab: ===============================

## fstab created by Livecd-install 

none    /proc    proc    defaults    0 0
none    /dev/pts    devpts    mode=0620    0 0
none    /proc/bus/usb    usbfs    defaults    0 0

# cdrom: TSSTcorpCD/DVDW TS-L632M
#    /dev/hda    /mnt/cdrom    auto    user,exec,ro,noauto    0 0

# /dev/sda1, size=25607547, type=7: NTFS (primary)
/dev/sda1    /mnt/win_c    ntfs    user,exec,ro,noauto,nls=utf8,umask=0    0 0

# /dev/sda2, size=122881185, type=131: Journalised FS: ext3 (primary)
/dev/sda2    /mnt/sda2    ext3    user,exec,rw,noauto    0 0

# /dev/sda4, size=24515190, type=131: Journalised FS: ext3 (primary)
/dev/sda4    /mnt/sda4    ext3    user,exec,rw,noauto    0 0

# /dev/sda5, size=16370172, type=131: Linux native (extended)
/dev/sda5    /mnt/sda5    ext2    user,exec,rw,noauto    0 0

# /dev/sda6, size=7582617, type=130: Linux swap (extended)
/dev/sda6 swap swap defaults 0 0

# /dev/sda7, size=8177022, type=130: Linux swap (extended)
/dev/sda7 swap swap defaults 0 0

# /dev/sda8, size=29302497, type=131: Linux native (extended)
/dev/sda8    /mnt/sda8    ext2    user,exec,rw,noauto    0 0

# /dev/sdb1, size=128319425, type=7: NTFS (primary)
/dev/sdb1    /mnt/win_d    ntfs    user,exec,ro,noauto,nls=utf8,umask=0    0 0

# /dev/sdb2, size=17143808, type=7: NTFS (primary)
/dev/sdb2    /mnt/win_e    ntfs    user,exec,ro,noauto,nls=utf8,umask=0    0 0

# /dev/sdb5, size=41013882, type=131: Linux native (extended)
/dev/sdb5 / ext2 noatime 1 1

=================== sdb5: Location of files loaded by Grub: ===================


  67.7GB: boot/grub/menu.lst
  67.8GB: boot/grub/stage2
  67.7GB: boot/initrd-2.6.18.8.tex5.img
  67.7GB: boot/initrd.img
  67.7GB: boot/vmlinuz
  67.7GB: boot/vmlinuz-2.6.18.8.tex5

================================ sdc1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sdc2/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=32a7f436-76a6-4cca-966f-2d24d2e2702a ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=32a7f436-76a6-4cca-966f-2d24d2e2702a ro quiet splash
initrd        /boot/initrd.img-2.6.24-27-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=32a7f436-76a6-4cca-966f-2d24d2e2702a ro single
initrd        /boot/initrd.img-2.6.24-27-generic

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=32a7f436-76a6-4cca-966f-2d24d2e2702a ro quiet splash
initrd        /boot/initrd.img-2.6.24-26-generic
quiet

title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=32a7f436-76a6-4cca-966f-2d24d2e2702a ro single
initrd        /boot/initrd.img-2.6.24-26-generic

title        Ubuntu 8.04.4 LTS, memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Home Edition
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title        Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (on /dev/sda3)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=828568e1-8bbb-45a1-a7ed-60244e9e9630 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-27-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title        Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode) (on /dev/sda3)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=828568e1-8bbb-45a1-a7ed-60244e9e9630 ro single 
initrd        /boot/initrd.img-2.6.24-27-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (on /dev/sda3)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=828568e1-8bbb-45a1-a7ed-60244e9e9630 ro quiet splash 
initrd        /boot/initrd.img-2.6.24-26-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode) (on /dev/sda3)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=828568e1-8bbb-45a1-a7ed-60244e9e9630 ro single 
initrd        /boot/initrd.img-2.6.24-26-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title        Ubuntu 8.04.4 LTS, memtest86+ (on /dev/sda3)
root        (hd0,2)
kernel        /boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdf1.
title        Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (on /dev/sdf1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=654332b6-ba09-4f40-adbd-81d10e04db9f ro quiet splash 
initrd        /boot/initrd.img-2.6.24-27-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdf1.
title        Ubuntu 8.04.4 LTS, kernel 2.6.24-27-generic (recovery mode) (on /dev/sdf1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=654332b6-ba09-4f40-adbd-81d10e04db9f ro single 
initrd        /boot/initrd.img-2.6.24-27-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdf1.
title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (on /dev/sdf1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=654332b6-ba09-4f40-adbd-81d10e04db9f ro quiet splash 
initrd        /boot/initrd.img-2.6.24-26-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdf1.
title        Ubuntu 8.04.4 LTS, kernel 2.6.24-26-generic (recovery mode) (on /dev/sdf1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=654332b6-ba09-4f40-adbd-81d10e04db9f ro single 
initrd        /boot/initrd.img-2.6.24-26-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdf1.
title        Ubuntu 8.04.4 LTS, memtest86+ (on /dev/sdf1)
root        (hd1,0)
kernel        /boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdh1
title        Microsoft Windows XP Professional
root        (hd3,0)
savedefault
makeactive
map        (hd0) (hd3)
map        (hd3) (hd0)
chainloader    +1


=============================== sdc2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=32a7f436-76a6-4cca-966f-2d24d2e2702a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdf5
UUID=5aff062a-5f40-4ab9-84d9-32b503af07b9 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdc2: Location of files loaded by Grub: ===================


  44.9GB: boot/grub/menu.lst
  44.9GB: boot/grub/stage2
  44.9GB: boot/initrd.img-2.6.24-26-generic
  45.0GB: boot/initrd.img-2.6.24-27-generic
  44.9GB: boot/initrd.img-2.6.24-27-generic.bak
  44.9GB: boot/vmlinuz-2.6.24-26-generic
  44.9GB: boot/vmlinuz-2.6.24-27-generic
  45.0GB: initrd.img
  44.9GB: initrd.img.old
  44.9GB: vmlinuz
  44.9GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda5

00000000  6b 58 d3 77 44 4c 00 bd  06 f7 0c 71 bf b6 3f 77  |kX.wDL.....q..?w|
00000010  5e 32 79 8e 08 3a 92 2f  06 61 e2 e8 94 51 3b 0f  |^2y..:./.a...Q;.|
00000020  c6 57 5a 19 4f b4 a3 df  5b 68 66 0e ad 22 6b 67  |.WZ.O...[hf.."kg|
00000030  f6 1c ff 70 16 36 08 ca  c2 e1 2e 7a 36 b6 30 8b  |...p.6.....z6.0.|
00000040  45 38 c6 c8 5c c8 dc 76  e3 70 09 bc c6 ff ee 8d  |E8..\..v.p......|
00000050  43 78 0e f5 5f e6 e2 58  18 ef f3 2c 40 50 63 29  |Cx.._..X...,@Pc)|
00000060  48 04 b2 00 6f e1 2f 45  5d e4 4d c7 22 0c 31 5a  |H...o./E].M.".1Z|
00000070  f3 b3 87 f6 fe e7 27 75  13 33 b0 e9 a2 9b 23 f3  |......'u.3....#.|
00000080  09 e8 b9 d7 b9 17 81 cc  8e e3 22 90 34 d2 09 2c  |..........".4..,|
00000090  7a 8f bd 8c db f0 41 79  7b 38 8b 6e ab 73 67 a0  |z.....Ay{8.n.sg.|
000000a0  9d d9 24 a4 99 38 6e 20  a4 3a 75 4b b1 ff 02 3b  |..$..8n .:uK...;|
000000b0  bb 9b ca 65 9a e6 7f b4  9a 86 7c c4 5b 61 34 02  |...e......|.[a4.|
000000c0  ba 51 f8 2e 9d fc b6 21  99 77 fa ec 02 92 d0 ab  |.Q.....!.w......|
000000d0  08 4d 57 d7 07 1e 2d 80  fc 03 18 a5 f7 2e 0c 80  |.MW...-.........|
000000e0  f4 68 bd 97 af e2 98 8e  4b 89 4b bd 37 cb 52 40  |.h......K.K.7.R@|
000000f0  24 3d 19 c4 41 18 45 71  1c 0d 70 0a 06 5d 82 e3  |$=..A.Eq..p..]..|
00000100  20 f5 61 1b 9a 4e 3e be  fa 1c 1c 79 e2 cc 23 a2  | .a..N>....y..#.|
00000110  f0 ef da af 79 d2 ce 70  01 0b 9a e9 19 0a 20 73  |....y..p...... s|
00000120  e8 ac ea 17 90 e8 68 e0  7e 66 aa c5 d5 d1 ad 0e  |......h.~f......|
00000130  20 c4 a9 b1 4e 95 bd c6  7d 41 08 bc ca 78 89 cd  | ...N...}A...x..|
00000140  8b 96 6e eb 7f 42 cd b6  77 33 3f 46 f1 82 93 46  |..n..B..w3?F...F|
00000150  e0 82 34 92 71 44 e5 64  84 d1 d6 53 28 fe 60 a8  |..4.qD.d...S(.`.|
00000160  74 db 12 59 b1 5b 7b 75  e0 02 42 78 84 04 73 7b  |t..Y.[{u..Bx..s{|
00000170  27 24 7a d3 f6 f9 ab 66  35 a8 86 88 7b c9 c8 6c  |'$z....f5...{..l|
00000180  2f 4b e1 66 3e 45 cc ec  f7 74 10 6b c1 b5 cb 1a  |/K.f>E...t.k....|
00000190  c7 a0 69 af 5d 6f e1 a3  0d f2 12 60 70 54 fb f1  |..i.]o.....`pT..|
000001a0  d5 31 c1 a8 cb a4 33 c4  fe 9a b7 10 43 7c b6 84  |.1....3.....C|..|
000001b0  9f d3 c8 67 8a 3e 6a d2  83 90 48 ff 55 13 5d 0f  |...g.>j...H.U.].|
000001c0  ec 68 6c b9 bd 6b fd 58  4b d6 19 bb d7 97 7a 43  |.hl..k.XK.....zC|
000001d0  64 26 6d 17 56 06 64 2e  30 96 06 d1 57 46 44 e0  |d&m.V.d.0...WFD.|
000001e0  c1 8b 75 89 47 00 5c eb  af 92 9b 8c c9 c5 de 91  |..u.G.\.........|
000001f0  55 fc f1 2e 43 77 93 24  99 bf 56 7d d5 3b f1 5b  |U...Cw.$..V}.;.[|
00000200

Unknown BootLoader  on sda8

00000000  1e ae 81 2d ad e3 0e 40  a4 7d 98 53 3d 83 39 6f  |...-...@.}.S=.9o|
00000010  a1 d7 78 b0 17 7c b7 a4  77 a9 d6 42 b6 21 24 1a  |..x..|..w..B.!$.|
00000020  d1 b2 2a d4 68 83 e4 fd  e0 cf 7c a8 ca 21 37 2d  |..*.h.....|..!7-|
00000030  8d b1 50 dc b3 e4 87 c0  2e e5 2f f3 71 d2 6b 1c  |..P......./.q.k.|
00000040  ba 3b 87 7f dd 1d 25 12  de a7 4e 58 46 a2 50 c5  |.;....%...NXF.P.|
00000050  20 a2 42 c5 ff 9a 5f 75  67 59 0e e9 9b 5f 39 51  | .B..._ugY..._9Q|
00000060  87 07 87 59 ac 5e 1f 0d  d5 e8 7c b3 85 45 a9 72  |...Y.^....|..E.r|
00000070  4b 92 72 72 4a 62 9f b4  1b 5a b6 f0 3c 63 e1 ee  |K.rrJb...Z..<c..|
00000080  0d 2a f6 5c 76 00 4e 5b  f1 51 4d f0 95 18 4f 5e  |.*.\v.N[.QM...O^|
00000090  9c c4 b9 5e 6b 6c 7a 55  4f e5 94 25 93 6d 01 c3  |...^klzUO..%.m..|
000000a0  db 7a 0d 97 90 bb e8 32  77 01 7c fe 6a 39 9b 5c  |.z.....2w.|.j9.\|
000000b0  08 48 32 b6 f2 6e f7 7a  bc 4a 66 9c b8 23 d4 64  |.H2..n.z.Jf..#.d|
000000c0  b8 a9 74 99 ba 90 29 be  c4 ea af 14 36 a7 88 9e  |..t...).....6...|
000000d0  80 50 ca a4 a6 32 c5 b7  30 d7 d6 00 46 8b b4 1d  |.P...2..0...F...|
000000e0  75 f9 32 9f 5b b9 34 69  20 4d 34 ba ae 6a 3e 82  |u.2.[.4i M4..j>.|
000000f0  4d c6 35 72 17 f4 35 60  17 d8 08 24 cf c8 5e 12  |M.5r..5`...$..^.|
00000100  09 20 62 7f e1 ba ab 16  00 ab 9d 13 1e ce b6 0c  |. b.............|
00000110  f1 ea 63 1c d8 5b b9 d7  c1 97 1c c5 20 db 3f 59  |..c..[...... .?Y|
00000120  15 f3 6f e9 8d 08 99 3f  96 88 96 84 e7 d6 92 e4  |..o....?........|
00000130  09 b5 88 33 eb 37 49 be  06 fc 4b 59 50 69 f6 f4  |...3.7I...KYPi..|
00000140  65 b0 2e ae 78 58 56 81  88 04 ce 76 7c ef f5 3b  |e...xXV....v|..;|
00000150  95 cc bc c0 43 12 d4 d2  20 81 07 2c b3 10 b2 79  |....C... ..,...y|
00000160  88 9b c7 1e 03 7f 31 04  82 b7 e5 8e d8 08 03 21  |......1........!|
00000170  c9 9f 32 66 61 c1 ee ab  cb e5 48 b4 43 e8 0f 85  |..2fa.....H.C...|
00000180  48 33 f0 39 66 13 18 fd  97 dd 5d 4b 57 ca 44 4e  |H3.9f.....]KW.DN|
00000190  ce 10 6e 7d 83 4c 4c f2  dc 62 e4 99 60 11 05 96  |..n}.LL..b..`...|
000001a0  6d 0b e4 4f a9 81 33 e8  c2 7b 47 01 f1 83 16 ca  |m..O..3..{G.....|
000001b0  8b 87 eb a0 d4 1b ad ae  ab da b8 0f c5 12 97 65  |...............e|
000001c0  ee e4 91 10 a7 f8 09 77  4b 8f 99 09 d6 92 16 b9  |.......wK.......|
000001d0  59 56 7f 1b 60 54 10 4d  9f 1c 59 ab d0 16 56 81  |YV..`T.M..Y...V.|
000001e0  02 70 23 92 8b f8 27 be  42 25 40 46 24 0a 3f d6  |.p#...'.B%@F$.?.|
000001f0  64 8e a4 cf a7 7a be fc  96 b4 e6 79 7e 7f 45 81  |d....z.....y~.E.|
00000200


```

---

### Post by kansasnoob on 2010-05-16
> **Moozillaaa said:**
> I rebooted, and got a new GRUB error:

Anybody seen this before?

        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        set quiet=1
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 7b4afbe0-28fe-4403-bd86-c4364bf10f98
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=7b4afbe0-28fe-4403-bd86-c4364bf10f98 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic

Well, I've been looking but the UUID listed in this post "7b4afbe0-28fe-4403-bd86-c4364bf10f98" doesn't appear in your blkid:

```
blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        D6AC129BF4974A14                       ntfs       XPPro                         
/dev/sda2        fdcf20ef-a198-45be-877c-3dbc01c64ef5   ext3                                     
/dev/sda4        e167cb3e-f1fc-4852-804a-a22457aece41   ext3       /                             
/dev/sda6        5cc048de-889c-4a1c-ab56-45c1e2933d6d   swap                                     
/dev/sda7        ad886fc1-dcb3-4c66-b627-2b59da7500eb   swap                                     
/dev/sdb1        FEFEB4A2FEB4549D                       ntfs                                     
/dev/sdb2        10FCA6F2FCA6D0F0                       ntfs       HP_RECOVERY                   
/dev/sdb4        b41368bf-9c87-48fc-ab6f-191cadc42e45   ext3                                     
/dev/sdb5        0b8d1aab-414a-4f4e-9e53-8a515ad426e6   ext2                                     
/dev/sdc1        809C18619C1853CE                       ntfs                                     
/dev/sdc2        32a7f436-76a6-4cca-966f-2d24d2e2702a   ext3                                     
/dev/sdc3        73f18d48-1e6c-4bb6-ab1f-1e567b41622c   swap 
                 7b4afbe0-28fe-4403-bd86-c4364bf10f98                                    
```

Note: I added the one in question at the very bottom for easy comparison.

Are you certain that's your new RESULTS.txt?

You mentioned running it before and if the old one still exists the new one will be RESULTS1.txt, etc, etc. Example:

```
lance@lance-desktop:~$ ls ~/Downloads
boot_info_script055.sh          **RESULTS2.txt**
gparted-live-0.4.6-1.iso        **RESULTS2.txt.tar.gz**
KNOPPIX_V6.2.1CD-2010-01-31-EN  **RESULTS3.txt**
LinuxMint-7.iso                 **RESULTS4.txt**
linuxmint-9-gnome-rc-i386.iso   **RESULTS.txt**
lost+found                      ubuntu-10.04-desktop-i386.iso
lubuntu-10.04.iso               ubuntu-8.04.4-desktop-i386.iso
pclinuxos-gnome-2010.iso        ubuntu-9.04-desktop-i386.iso
pmagic-4.9.iso.zip              ubuntu-9.10-desktop-i386.iso
**RESULTS1.txt**

```

Which OS are you trying to boot when that appears?

Which OS's still boot and which don't?

Also, I'm getting super tired so I may have to resume looking at this tomorrow :)

---

### Post by Moozillaaa on 2010-05-16
Hmmm... no, I'm not sure it's the new script return - I'll have to confirm that one.

When I get the 'recordfail' error, I'm trying to boot 9.10 **sda2** - that's the default boot. 

XP **sda1**, and Vista **sdb1** is the only ones that will boot.

F10 **sda4** will not load, nor will PCLOS **sdb5**.

XP and Hardy on dev '**c**' are USB device.

Thanks again for lookin' it over there!

---

### Post by Moozillaaa on 2010-05-16
My partition is packed tight with data.

Found a thread with this boot error, and the solution was freeing space up. Still working on this here...

---

### Post by Moozillaaa on 2010-05-16
I put some MPEG's onto this install from another machine, and put too many on it. So it would not boot, giving an error message:> 

Install problem!
The configuration defaults for Gnome Power Manager have not been installed correctly. Please contact your computer administrator.

It was not a GRUB problem.

Thanks for lookin' there...

---

