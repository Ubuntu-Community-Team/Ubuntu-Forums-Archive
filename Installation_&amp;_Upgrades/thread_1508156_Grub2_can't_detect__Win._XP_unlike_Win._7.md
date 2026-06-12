---
title: "Grub2 can't detect  Win. XP unlike Win. 7"
date: 2010-06-12
forum: Installation &amp; Upgrades
---

### Post by Baba-Ali on 2010-06-12
Hello everybody,

I have a laptop Acer Aspire 5538 (AMD Turion 64x2).
I just installed Ubuntu 10.04. I like it but I still need windowsXP to run some ''old'' softwares.
So Installed WindowsXP Media Center and Windows7 Home Premium (from my recovery DVDs).
But Grub2 only detect Ubuntu and Windows7, and not WindowsXP!!!
I undated Grub2, reinstalled it, manually modified it ... but no success:confused:
I finally reinstalled WindowsXP M.C. and reboot on Ubuntu by reinstalling Grub2 with the liveCD : no solution !!

(even before installing Ubuntu, Windows7 wasn't able to detect WindowsXP)

I think that's because of the ****ing Windows7.

Please help! I really spent so much time with this computer since I bought it 5 months ago :confused:

---

### Post by darkod on 2010-06-12
Run the boot info script and post the content of the results file as explained here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

Lets see what setup do you have. Unless you move the boot flag before installing a second windows, windows installer is designed to combine boot files so in any case you will get only one windows entry in grub menu. Then selecting that will allow you to choose from the two windows versions.

The only way to avoid that is to move the boot flag to the dedicated partition before installing the second windows.

---

### Post by Baba-Ali on 2010-06-13
Hi Darko,

Thanks for your interest. Here are the result (I have a 32bits Ubuntu) :

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda10 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    83,891,429    83,891,367   7 HPFS/NTFS
/dev/sda2          83,891,491   488,375,999   404,484,509   f W95 Ext d (LBA)
/dev/sda5          83,891,493   167,782,859    83,891,367   7 HPFS/NTFS
/dev/sda6         167,784,448   169,783,295     1,998,848  82 Linux swap / Solaris
/dev/sda7         169,785,344   209,727,487    39,942,144  83 Linux
/dev/sda8         209,728,638   251,674,289    41,945,652   7 HPFS/NTFS
/dev/sda9         251,674,353   356,530,544   104,856,192   7 HPFS/NTFS
/dev/sda10        356,530,608   488,375,999   131,845,392   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       ECD8D977D8D9408E                       ntfs       PerData                       
/dev/sda1        9A20F75020F7323D                       ntfs       Acer                          
/dev/sda2: PTTYPE="dos" 
/dev/sda5        EC34A8E334A8B1CE                       ntfs       XP MediaCenter                
/dev/sda6        6727288f-8592-4f0f-96bb-b13ea0825341   swap                                     
/dev/sda7        9e75fb56-42c1-4307-aa29-40505a3484d4   ext4                                     
/dev/sda8        AE34D76E34D737D3                       ntfs       ArUbuntu                      
/dev/sda9        968CE5DC8CE5B741                       ntfs       Debian                        
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 

=========================== sda7/boot/grub/grub.cfg: ===========================

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
if terminal_input console ; then true ; else
  # For backward compatibility with versions of terminal.mod that don't
  # understand terminal_input
  terminal console
fi
if terminal_output console ; then true ; else
  # For backward compatibility with versions of terminal.mod that don't
  # understand terminal_output
  terminal console
fi
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 9e75fb56-42c1-4307-aa29-40505a3484d4
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=9e75fb56-42c1-4307-aa29-40505a3484d4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 9e75fb56-42c1-4307-aa29-40505a3484d4
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=9e75fb56-42c1-4307-aa29-40505a3484d4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 9e75fb56-42c1-4307-aa29-40505a3484d4
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=9e75fb56-42c1-4307-aa29-40505a3484d4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 9e75fb56-42c1-4307-aa29-40505a3484d4
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=9e75fb56-42c1-4307-aa29-40505a3484d4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 9e75fb56-42c1-4307-aa29-40505a3484d4
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 9e75fb56-42c1-4307-aa29-40505a3484d4
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9a20f75020f7323d
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###


#####################################################
#####################################################
### BEGIN /etc/grub.d/70_os-prober ###
menuentry "Microsoft Windows XP 2002 SP2 Media Center" {
    #insmod ntfs
    set root='(hd0,2)'
    #search --no-floppy --fs-uuid --set XP MediaCenter
    chainloader +1
}
### END /etc/grub.d/70_os-prober ###
#####################################################
#####################################################


### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

set gfxmode="640x480"
set gfxfont="Unifont Regular 16"
loadfont /boot/grub/themes/fonts/unifont.pf2
loadfont /boot/grub/themes/fonts/aqui.pf2
loadfont /boot/grub/themes/fonts/edges.pf2
loadfont /boot/grub/themes/fonts/lime.pf2
loadfont /boot/grub/themes/fonts/7x13B.pf2
loadfont /boot/grub/themes/fonts/smoothansi.pf2
loadfont /boot/grub/themes/fonts/Helvetica-Bold-14.pf2
insmod vbe
insmod png
insmod coreui

#themes:

#ubuntu theme:
load_config /boot/grub/themes/ubuntu/theme.txt
#winter theme:
#load_config /boot/grub/themes/winter/theme.txt
#proto theme:
#load_config /boot/grub/themes/proto/theme.txt
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda10 during installation
UUID=9e75fb56-42c1-4307-aa29-40505a3484d4 /               ext4    errors=remount-ro 0       1
/dev/sda9       none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 104.2GB: boot/grub/core.img
 104.5GB: boot/grub/grub.cfg
 104.4GB: boot/initrd.img-2.6.32-21-generic
 104.5GB: boot/initrd.img-2.6.32-22-generic
 104.4GB: boot/vmlinuz-2.6.32-21-generic
 104.5GB: boot/vmlinuz-2.6.32-22-generic
 104.5GB: initrd.img
 104.4GB: initrd.img.old
 104.5GB: vmlinuz
 104.4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  8d 0e b9 1a c7 c8 ec 2c  86 c2 27 1b 8c 40 64 4c  |.......,..'..@dL|
00000010  db bd 1c 52 c4 69 ba 4e  22 f8 a4 43 79 94 f7 17  |...R.i.N"..Cy...|
00000020  0b 7d 20 5e 8f 7d a3 56  08 a4 ca f9 54 70 4f 3c  |.} ^.}.V....TpO<|
00000030  46 a6 ef ae 72 f3 14 68  96 9c b4 29 12 d9 d8 85  |F...r..h...)....|
00000040  2c 2b db 4a d2 68 3a 7a  52 52 a9 36 1d 45 a0 8c  |,+.J.h:zRR.6.E..|
00000050  52 47 40 92 18 86 ab 99  56 26 bd 34 f2 45 4e 8a  |RG@.....V&.4.EN.|
00000060  38 86 46 68 b0 54 25 46  ff 2e fd 2a 10 ad 40 cd  |8.Fh.T%F...*..@.|
00000070  2f 84 cc b4 84 60 5b 86  90 0f e1 47 24 eb 02 29  |/....`[....G$..)|
00000080  b1 af ba f0 4a 41 a4 10  24 99 b3 e1 94 fb 90 a8  |....JA..$.......|
00000090  7f 8f ba fc 13 22 9b 53  8b 18 52 5b 8c 4b 11 d2  |.....".S..R[.K..|
000000a0  82 2b 32 3e 97 57 5f b6  41 4c 55 71 12 88 fe 49  |.+2>.W_.ALUq...I|
000000b0  c5 d1 89 1b e9 14 46 ca  3a 06 e6 65 56 f3 64 e1  |......F.:..eV.d.|
000000c0  f2 eb ad a1 9d 74 b4 f8  43 14 4e 48 07 4a 95 97  |.....t..C.NH.J..|
000000d0  d1 ca 20 a9 a4 dc 2c a6  f5 4b e3 54 e8 d8 d8 5c  |.. ...,..K.T...\|
000000e0  9a db a8 c6 c4 2f cd 97  af 10 91 22 5b ec c6 ac  |...../....."[...|
000000f0  80 17 d4 89 d5 c0 4c ad  49 65 d6 87 5a 82 7e e1  |......L.Ie..Z.~.|
00000100  82 9d a4 b5 84 a4 b4 b2  d6 83 eb 11 f7 9e da ff  |................|
00000110  4b bf a5 a2 0f 5a 1b a5  13 2e 4a 6c 2a 9d 58 44  |K....Z....Jl*.XD|
00000120  76 90 a8 39 f3 8c ea e6  b5 49 b6 0e d3 6a 9b 5e  |v..9.....I...j.^|
00000130  9f f5 0f 56 bc c2 84 eb  96 cd d9 44 b4 eb 21 2c  |...V.......D..!,|
00000140  0c 30 ab d8 c5 e1 d6 98  2a 98 78 f1 bb ab 48 d4  |.0......*.x...H.|
00000150  8b 0d bc b2 5d 23 68 d8  c4 0a 3c c0 e4 fb 7e ab  |....]#h...<...~.|
00000160  75 28 cd d7 6a 48 98 f7  34 d3 64 fa 0b e5 9a 88  |u(..jH..4.d.....|
00000170  e2 63 ca 24 92 dd 22 47  5d fc 48 bc b3 2b 36 9f  |.c.$.."G].H..+6.|
00000180  17 08 05 04 95 48 aa 84  4c a2 99 bf ac 44 9e fd  |.....H..L....D..|
00000190  86 c8 d6 f1 89 a9 c5 a4  da 25 64 e2 6b 19 4c 8e  |.........%d.k.L.|
000001a0  27 c6 b4 d8 66 2e dd a3  ea 7c f0 b5 b6 57 ca e9  |'...f....|...W..|
000001b0  6a 4a 98 43 22 54 6e a2  05 04 41 f8 fe ae 00 01  |jJ.C"Tn...A.....|
000001c0  c1 ff 07 fe ff ff 02 00  00 00 a7 14 00 05 00 00  |................|
000001d0  c1 ff 05 84 fc ff a9 14  00 05 34 86 1e 00 00 00  |..........4.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```For information, the ArUbuntu and Debian partitions have no OS installed.

Thank you.

---

### Post by Baba-Ali on 2010-06-13
Hi again,

Good news n bad news:
According to these results, I was able to correct my manual modification of the GRUB file. So I am now able to boot on WinXP. The bad news is that the Win7 choice on the GRUB menu, boots on WinXP too !!

```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9a20f75020f7323d
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###


#####################################################
#####################################################
### BEGIN /etc/grub.d/70_os-prober ###
menuentry "Microsoft Windows XP 2002 SP2 Media Center" {
    insmod ntfs
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set EC34A8E334A8B1CE
    chainloader +1
}
### END /etc/grub.d/70_os-prober ###
#####################################################
#####################################################
```Is it because of the ''chaineloader'' line?

---

### Post by darkod on 2010-06-13
When you select win7 from the grub menu, does it show you another menu to select between 7 and XP or not?
That is what it should happen because the boot files are combined on your 7 partition. Plus XP is on a logical partition and can't have its boot files on it anyway. Only on primary.

---

### Post by Baba-Ali on 2010-06-14
Hi,

No, there is no other menu !

---

### Post by Baba-Ali on 2010-06-14
Hello  everybody,

I have a laptop Acer Aspire 5538 (AMD Turion 64x2) with Ubuntu 10.04 (32bits), WinXP SP2 2002 MediaCenter (32bits) and Win7 Home Premium (64bits, from my  recovery DVDs) OS installed.

In the first time, GRUB2 only detected Ubuntu and Windows7. But according to an answer to my last post on the forum, I installed [Boot Info Script]("http://sourceforge.net/projects/bootinfoscript/") ([http://ubuntuforums.org/showpost.php...01&postcount=4]("http://ubuntuforums.org/showpost.php?p=8844901&postcount=4")) and I got the following results:

```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda10 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    83,891,429    83,891,367   7 HPFS/NTFS
/dev/sda2          83,891,491   488,375,999   404,484,509   f W95 Ext d (LBA)
/dev/sda5          83,891,493   167,782,859    83,891,367   7 HPFS/NTFS
/dev/sda6         167,784,448   169,783,295     1,998,848  82 Linux swap / Solaris
/dev/sda7         169,785,344   209,727,487    39,942,144  83 Linux
/dev/sda8         209,728,638   251,674,289    41,945,652   7 HPFS/NTFS
/dev/sda9         251,674,353   356,530,544   104,856,192   7 HPFS/NTFS
/dev/sda10        356,530,608   488,375,999   131,845,392   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       ECD8D977D8D9408E                       ntfs       PerData                       
/dev/sda1        9A20F75020F7323D                       ntfs       Acer                          
/dev/sda2: PTTYPE="dos" 
/dev/sda5        EC34A8E334A8B1CE                       ntfs       XP MediaCenter                
/dev/sda6        6727288f-8592-4f0f-96bb-b13ea0825341   swap                                     
/dev/sda7        9e75fb56-42c1-4307-aa29-40505a3484d4   ext4                                     
/dev/sda8        AE34D76E34D737D3                       ntfs       ArUbuntu                      
/dev/sda9        968CE5DC8CE5B741                       ntfs       Debian                        
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 

=========================== sda7/boot/grub/grub.cfg: ===========================

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
if terminal_input console ; then true ; else
  # For backward compatibility with versions of terminal.mod that don't
  # understand terminal_input
  terminal console
fi
if terminal_output console ; then true ; else
  # For backward compatibility with versions of terminal.mod that don't
  # understand terminal_output
  terminal console
fi
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 9e75fb56-42c1-4307-aa29-40505a3484d4
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=9e75fb56-42c1-4307-aa29-40505a3484d4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 9e75fb56-42c1-4307-aa29-40505a3484d4
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=9e75fb56-42c1-4307-aa29-40505a3484d4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 9e75fb56-42c1-4307-aa29-40505a3484d4
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=9e75fb56-42c1-4307-aa29-40505a3484d4 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 9e75fb56-42c1-4307-aa29-40505a3484d4
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=9e75fb56-42c1-4307-aa29-40505a3484d4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 9e75fb56-42c1-4307-aa29-40505a3484d4
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set 9e75fb56-42c1-4307-aa29-40505a3484d4
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9a20f75020f7323d
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###


#####################################################
#####################################################
### BEGIN /etc/grub.d/70_os-prober ###
menuentry "Microsoft Windows XP 2002 SP2 Media Center" {
    #insmod ntfs
    set root='(hd0,2)'
    #search --no-floppy --fs-uuid --set XP MediaCenter
    chainloader +1
}
### END /etc/grub.d/70_os-prober ###
#####################################################
#####################################################


### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

set gfxmode="640x480"
set gfxfont="Unifont Regular 16"
loadfont /boot/grub/themes/fonts/unifont.pf2
loadfont /boot/grub/themes/fonts/aqui.pf2
loadfont /boot/grub/themes/fonts/edges.pf2
loadfont /boot/grub/themes/fonts/lime.pf2
loadfont /boot/grub/themes/fonts/7x13B.pf2
loadfont /boot/grub/themes/fonts/smoothansi.pf2
loadfont /boot/grub/themes/fonts/Helvetica-Bold-14.pf2
insmod vbe
insmod png
insmod coreui

#themes:

#ubuntu theme:
load_config /boot/grub/themes/ubuntu/theme.txt
#winter theme:
#load_config /boot/grub/themes/winter/theme.txt
#proto theme:
#load_config /boot/grub/themes/proto/theme.txt
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda10 during installation
UUID=9e75fb56-42c1-4307-aa29-40505a3484d4 /               ext4    errors=remount-ro 0       1
/dev/sda9       none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 104.2GB: boot/grub/core.img
 104.5GB: boot/grub/grub.cfg
 104.4GB: boot/initrd.img-2.6.32-21-generic
 104.5GB: boot/initrd.img-2.6.32-22-generic
 104.4GB: boot/vmlinuz-2.6.32-21-generic
 104.5GB: boot/vmlinuz-2.6.32-22-generic
 104.5GB: initrd.img
 104.4GB: initrd.img.old
 104.5GB: vmlinuz
 104.4GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  8d 0e b9 1a c7 c8 ec 2c  86 c2 27 1b 8c 40 64 4c  |.......,..'..@dL|
00000010  db bd 1c 52 c4 69 ba 4e  22 f8 a4 43 79 94 f7 17  |...R.i.N"..Cy...|
00000020  0b 7d 20 5e 8f 7d a3 56  08 a4 ca f9 54 70 4f 3c  |.} ^.}.V....TpO<|
00000030  46 a6 ef ae 72 f3 14 68  96 9c b4 29 12 d9 d8 85  |F...r..h...)....|
00000040  2c 2b db 4a d2 68 3a 7a  52 52 a9 36 1d 45 a0 8c  |,+.J.h:zRR.6.E..|
00000050  52 47 40 92 18 86 ab 99  56 26 bd 34 f2 45 4e 8a  |RG@.....V&.4.EN.|
00000060  38 86 46 68 b0 54 25 46  ff 2e fd 2a 10 ad 40 cd  |8.Fh.T%F...*..@.|
00000070  2f 84 cc b4 84 60 5b 86  90 0f e1 47 24 eb 02 29  |/....`[....G$..)|
00000080  b1 af ba f0 4a 41 a4 10  24 99 b3 e1 94 fb 90 a8  |....JA..$.......|
00000090  7f 8f ba fc 13 22 9b 53  8b 18 52 5b 8c 4b 11 d2  |.....".S..R[.K..|
000000a0  82 2b 32 3e 97 57 5f b6  41 4c 55 71 12 88 fe 49  |.+2>.W_.ALUq...I|
000000b0  c5 d1 89 1b e9 14 46 ca  3a 06 e6 65 56 f3 64 e1  |......F.:..eV.d.|
000000c0  f2 eb ad a1 9d 74 b4 f8  43 14 4e 48 07 4a 95 97  |.....t..C.NH.J..|
000000d0  d1 ca 20 a9 a4 dc 2c a6  f5 4b e3 54 e8 d8 d8 5c  |.. ...,..K.T...\|
000000e0  9a db a8 c6 c4 2f cd 97  af 10 91 22 5b ec c6 ac  |...../....."[...|
000000f0  80 17 d4 89 d5 c0 4c ad  49 65 d6 87 5a 82 7e e1  |......L.Ie..Z.~.|
00000100  82 9d a4 b5 84 a4 b4 b2  d6 83 eb 11 f7 9e da ff  |................|
00000110  4b bf a5 a2 0f 5a 1b a5  13 2e 4a 6c 2a 9d 58 44  |K....Z....Jl*.XD|
00000120  76 90 a8 39 f3 8c ea e6  b5 49 b6 0e d3 6a 9b 5e  |v..9.....I...j.^|
00000130  9f f5 0f 56 bc c2 84 eb  96 cd d9 44 b4 eb 21 2c  |...V.......D..!,|
00000140  0c 30 ab d8 c5 e1 d6 98  2a 98 78 f1 bb ab 48 d4  |.0......*.x...H.|
00000150  8b 0d bc b2 5d 23 68 d8  c4 0a 3c c0 e4 fb 7e ab  |....]#h...<...~.|
00000160  75 28 cd d7 6a 48 98 f7  34 d3 64 fa 0b e5 9a 88  |u(..jH..4.d.....|
00000170  e2 63 ca 24 92 dd 22 47  5d fc 48 bc b3 2b 36 9f  |.c.$.."G].H..+6.|
00000180  17 08 05 04 95 48 aa 84  4c a2 99 bf ac 44 9e fd  |.....H..L....D..|
00000190  86 c8 d6 f1 89 a9 c5 a4  da 25 64 e2 6b 19 4c 8e  |.........%d.k.L.|
000001a0  27 c6 b4 d8 66 2e dd a3  ea 7c f0 b5 b6 57 ca e9  |'...f....|...W..|
000001b0  6a 4a 98 43 22 54 6e a2  05 04 41 f8 fe ae 00 01  |jJ.C"Tn...A.....|
000001c0  c1 ff 07 fe ff ff 02 00  00 00 a7 14 00 05 00 00  |................|
000001d0  c1 ff 05 84 fc ff a9 14  00 05 34 86 1e 00 00 00  |..........4.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```(For information, the ArUbuntu and Debian partitions have no OS  installed).

According to these results, I was able to correct my manual modification  of the GRUB file:

```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 9a20f75020f7323d
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###


#####################################################
#####################################################
### BEGIN /etc/grub.d/70_os-prober ###
menuentry "Microsoft Windows XP 2002 SP2 Media Center" {
    insmod ntfs
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set EC34A8E334A8B1CE
    chainloader +1
}
### END /etc/grub.d/70_os-prober ###
#####################################################
#####################################################
```So I am now able to boot on WinXP but the Win7 choice on the GRUB menu, boots on WinXP too without any other menu allowing  to make selection between WinXP and Win7 !!

Please Help!

---

### Post by darkod on 2010-06-14
Depending how you installed both version of windows, the problem is that windows combines the boot files when two or more versions are installed. In theory, after selecting Windows from the grub2 boot menu, you should see another menu from the windows bootloader where you can select XP or 7. But in your case it seems the windows combine process went wrong, or maybe the order in which you install the two windows versions makes a difference.

You can see all windows boot files grouped on /dev/sda1.

Grub2 or ubuntu has nothing to do with this.

I'm not sure if you can use a win7 repair cd and sort it out so that it combines the XP and 7 boot files correctly.

---

### Post by oldfred on 2010-06-14
I know when you install the second windows you can separate them. Not sure if you can move boot flag and repair them??

[http://ubuntuforums.org/showthread.php?t=1279218&highlight=booting+MS+products](http://ubuntuforums.org/showthread.php?t=1279218&highlight=booting+MS+products)
louieb's suggestion:
Just a note about dual booting 2 MS products. When you install the 2nd one - the installer will put its boot loader in the partition with the boot flag on (usually the partition holding the 1st MS product). And the 2nd product can only be booted thru the boot loader in the 1st product.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by Iowan on 2010-06-14
Threads merged.

---

