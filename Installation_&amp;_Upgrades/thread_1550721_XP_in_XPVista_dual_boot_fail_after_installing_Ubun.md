---
title: "XP in XP/Vista dual boot fail after installing Ubuntu"
date: 2010-08-11
forum: Installation &amp; Upgrades
---

### Post by Cavaradossi on 2010-08-11
Hello,

I have two HDDs, one 500GB and one 1TB. The 500GB is used for operating systems, where XP and Vista have been dual booting. Now, I've installed Ubuntu 10.04 on a seperate partition on the same disk. When I restarted after the installation was complete, the grub loader never appeared and I went straight to the Windows loader. I guess this happened because some grub startup files were written to the 1TB drive, since this is the sda while the 500GB is sdb. When I chanced the boot priority in the bios to prefer the 1TB sda disk, grub and Ubuntu loaded perfectly. Windows loader worked as it used to and Vista loaded without any problems. But when I now choose XP from the Windows loader, my computer restarts immediately! Changing boot priority back to the 500GB disk, both XP and Vista works perfectly, but there is no grub loader.

Is there any way I can fix this without reinstalling XP and Vista onto the 1TB disk, and without having to change the boot priority every time I want to change between Ubuntu and XP?

---

### Post by oldfred on 2010-08-11
Welcome to the forums.

So we can see what is installed where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

Windows combines boot loaders into one active (boot flag) partitions. So when booting Vista do you not get a choice of Vista or XP. Grub will not let you directly boot both windows. You may be able to repair the XP partition to get it to separately boot if that is the problem.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by Cavaradossi on 2010-08-12
Thanks for helping, oldfred. Here's the result.txt:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /grldr /ntldr 
                       /NTDETECT.COM /ntdetect.com

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sdb3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   512,007,614   512,007,552   7 HPFS/NTFS
/dev/sda2         512,007,615 1,953,503,999 1,441,496,385   f W95 Ext d (LBA)
/dev/sda5         512,007,678   921,600,854   409,593,177   7 HPFS/NTFS
/dev/sda6         921,600,918 1,536,006,779   614,405,862   7 HPFS/NTFS
/dev/sda7       1,536,006,843 1,953,503,999   417,497,157   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   245,762,369   245,762,307   7 HPFS/NTFS
/dev/sdb2         245,762,370   491,524,739   245,762,370   7 HPFS/NTFS
/dev/sdb3         491,524,740   628,243,489   136,718,750  83 Linux
/dev/sdb4         628,244,478   976,768,064   348,523,587   f W95 Ext d (LBA)
/dev/sdb5         655,371,738   757,769,984   102,398,247   7 HPFS/NTFS
/dev/sdb6         757,770,048   976,768,064   218,998,017   7 HPFS/NTFS
/dev/sdb7         628,244,480   655,370,239    27,125,760  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        64A48164A4813996                       ntfs       Musikk                        
/dev/sda2: PTTYPE="dos" 
/dev/sda5        828C8BE38C8BD059                       ntfs       Film                          
/dev/sda6        54A8987AA8985BF4                       ntfs                                     
/dev/sda7        E830A02E30A00622                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        A078187A78185180                       ntfs       Windows XP                    
/dev/sdb2        0A48ADA048AD8B51                       ntfs       Windows Vista                 
/dev/sdb3        d0da010b-6f67-48b1-b5b2-98bf4027cd22   ext4                                     
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        7E806C67806C283B                       ntfs       Temp                          
/dev/sdb6        1C08863508860DC8                       ntfs       Spill                         
/dev/sdb7        4d531762-b35f-4e51-8142-fb761125631c   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb3        /                        ext4       (rw,errors=remount-ro)


================================ sdb1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT /USEPMTIMER /usepmtimer 

=========================== sdb3/boot/grub/grub.cfg: ===========================

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
set root='(hd1,3)'
search --no-floppy --fs-uuid --set d0da010b-6f67-48b1-b5b2-98bf4027cd22
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
set root='(hd1,3)'
search --no-floppy --fs-uuid --set d0da010b-6f67-48b1-b5b2-98bf4027cd22
set locale_dir=($root)/boot/grub/locale
set lang=nb
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set d0da010b-6f67-48b1-b5b2-98bf4027cd22
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=d0da010b-6f67-48b1-b5b2-98bf4027cd22 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set d0da010b-6f67-48b1-b5b2-98bf4027cd22
    echo    'Loading Linux 2.6.32-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=d0da010b-6f67-48b1-b5b2-98bf4027cd22 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set d0da010b-6f67-48b1-b5b2-98bf4027cd22
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set d0da010b-6f67-48b1-b5b2-98bf4027cd22
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set a078187a78185180
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb3 during installation
UUID=d0da010b-6f67-48b1-b5b2-98bf4027cd22 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb7 during installation
UUID=4d531762-b35f-4e51-8142-fb761125631c none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb3: Location of files loaded by Grub: ===================


 303.3GB: boot/grub/core.img
 318.4GB: boot/grub/grub.cfg
 303.4GB: boot/initrd.img-2.6.32-24-generic-pae
 303.4GB: boot/vmlinuz-2.6.32-24-generic-pae
 303.4GB: initrd.img
 303.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb4

00000000  6d 93 db 27 b4 ab 4a ac  0b 06 13 4c 26 86 ae 2a  |m..'..J....L&..*|
00000010  ed e3 66 c3 23 30 73 7b  08 c7 2c 70 e1 45 06 95  |..f.#0s{..,p.E..|
00000020  f7 4d 96 cc f9 33 54 d5  91 4d a6 0e ee c3 ef ce  |.M...3T..M......|
00000030  c4 f0 cf a9 a4 6a 69 19  17 12 2e 1a 2d a2 e6 89  |.....ji.....-...|
00000040  a1 cd bb 9b 75 ab 4a c5  65 a1 59 57 93 14 c3 96  |....u.J.e.YW....|
00000050  88 76 47 a1 18 42 cd 72  c4 1d 49 9c 68 d9 98 99  |.vG..B.r..I.h...|
00000060  81 28 b1 16 d1 32 1c 51  b2 1c 47 14 b1 c5 29 aa  |.(...2.Q..G...).|
00000070  e3 55 cc b2 cb 2c 13 04  9e ad 3d 5c d4 4d 4b 74  |.U...,....=\.MKt|
00000080  91 b9 4d fc fb 07 2d 5c  2c b3 23 30 25 6b 8b 3b  |..M...-\,.#0%k.;|
00000090  ab b4 93 5a 29 b3 a3 c1  a4 da b3 40 ff fd b2 04  |...Z)......@....|
000000a0  77 55 44 55 44 66 55 44  44 44 55 b6 4b 6d b5 b2  |wUDUDfUDDDU.Km..|
000000b0  40 00 00 00 00 00 00 0a  5a aa a0 3a aa aa aa aa  |@.......Z..:....|
000000c0  b1 c7 51 25 12 3c f2 8a  34 d7 1c 89 e8 62 7a 18  |..Q%.<..4....bz.|
000000d0  e0 8e 38 22 8a 38 a3 8e  38 e3 8e 39 22 8a 38 a3  |..8".8..8..9".8.|
000000e0  8e 29 e3 0b 25 62 0a 24  62 2b 81 0a e0 48 b9 11  |.)..%b.$b+...H..|
000000f0  72 1e 99 e9 87 01 c1 4e  52 9c aa b7 ab 76 85 e6  |r......NR....v..|
00000100  61 98 95 d5 6b 67 a7 68  5a 66 76 81 65 f4 a4 4a  |a...kg.hZfv.e..J|
00000110  59 48 64 62 38 53 87 12  86 03 62 a2 df 62 a2 e0  |YHdb8S....b..b..|
00000120  90 bc e4 2f 3a 9a 95 35  1a 1d a1 db b6 ef 27 9e  |.../:..5......'.|
00000130  4f 35 51 55 19 51 a1 5b  56 d6 ed 71 49 35 a4 47  |O5QU.Q.[V..qI5.G|
00000140  83 54 58 cc 31 6a 18 a1  66 37 63 79 49 76 ec 95  |.TX.1j..f7cyIv..|
00000150  ae c3 c4 bd c4 c4 bd 8b  08 e2 c2 36 70 0c e0 1d  |...........6p...|
00000160  15 d1 5c 67 19 cf bb 9f  72 39 23 92 7c 9d 54 56  |..\g....r9#.|.TV|
00000170  38 1d 0b 26 53 74 87 59  7a 71 16 29 65 a3 27 85  |8..&St.Yzq.)e.'.|
00000180  57 54 68 76 75 5a b1 40  98 5a 26 98 5a 25 0b 52  |WThvuZ.@.Z&.Z%.R|
00000190  82 d4 ad 2e 5a 5c a1 d6  1d 50 94 25 37 42 6e 8c  |....Z\...P.%7Bn.|
000001a0  ee ce e1 bc 78 44 1b d2  29 6b 19 a4 99 44 88 48  |....xD..)k...D.H|
000001b0  95 df ca 7a 85 b6 79 4c  99 59 97 6c a6 76 00 01  |...z..yL.Y.l.v..|
000001c0  c1 ff 07 fe ff ff dc ed  9d 01 27 79 1a 06 00 fe  |..........'y....|
000001d0  ff ff 05 fe ff ff 03 67  b8 07 40 a5 0d 0d 00 00  |.......g..@.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by presence1960 on 2010-08-12
Boot from the ubuntu Live CD and go to the desktop. Open a terminal and run ```
sudo mount /dev/sdb3 /mnt
``` This will mount your ubuntu / partition.

Next in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```This will put GRUB 2 on the MBR of the 500GB disk.

Reboot without the Live CD. Go into BIOS and put sdb (500 GB) as first in the hard disk boot order. Save changes to CMOS and continue booting. You should now have GRUB. Boot into Ubuntu and open a terminal and run ```
sudo update-grub
```

P.S. You installed Vista without marking it's partition as bootable prior to the installation so your Vista boot files are combined with XP. You may have to choose XP from the GRUB menu and will be given the choice of choosing either XP or Vista. Let us know how it turns out.

---

### Post by Cavaradossi on 2010-08-12
Ah, that solved it! Thank you very much!!

---

