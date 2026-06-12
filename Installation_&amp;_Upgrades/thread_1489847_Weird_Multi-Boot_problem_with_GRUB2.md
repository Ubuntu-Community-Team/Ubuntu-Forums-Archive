---
title: "Weird Multi-Boot problem with GRUB2"
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by UbuFlavio on 2010-05-21
First of all, hello everyone :)

I am new to Ubuntu and Linux generally speaking, so please excuse me if I'm posting this in the wrong section. I hope it's fine here, but if it's not feel free to move it.

Anyway, here is my problem. I have set up a triple-boot system with XP, W7 and now Ubuntu. The multi-boot works fine (after many headaches :P). W7's boot manager is in charge and gives me three choices when I turn on the computer: XP, 7 and Ubuntu. All these choices work and boot their respective OS, but before I go on, I need to explain how my hard drive is partitioned:

1 - Boot     partition  (Primary/Active)  ------------>  only 100 MB, I decided to use this for boot files *only*
2 - XP        partition  (Primary)             ------------>  contains XP installation    (40 GB)
3 - W7       partition  (Primary)            ------------>  contains W7 installation    (40 GB)
4 - EXTENDED
5 - empty   partition  (Logical)              ------------> not formatted yet, I plan to use this later (24 GB)
6 - Ubuntu  partition (Logical)              ------------> Ubuntu 10.04 is installed here (23 GB, Ext4)
7 - Ubuntu Swap partition (Logical)     ------------> swap partition for Ubuntu (about 1 GB)
8 - data partition        (Logical)            ------------>  this is just for data (about 160 GB, NTFS)
9 - data partition        (Logical)             -----------> another data partition (about 2 GB, NTFS)

I installed XP first. Then, I installed W7. When I did this, W7's boot manager took over and at every start-up gave me the choice between loading XP or W7 (all primary partitions use NTFS file system also). Then I installed Ubuntu, and chose to have GRUB2 installed *not* in the MBR, but in Ubuntu's same partition. This way, it did not overwrite W7's boot manager. Then, using EasyBCD, I created an entry for Ubuntu in W7's boot manager. This worked perfectly and now when I select Ubuntu during start-up W7's boot manager hands over control to GRUB2 in Ubuntu's partition and I get the following 5 more choices:

- linux kernel
- linux kernel recovery mode
- memtest86
- memtest86 (with some other options)
- Windows 7 (loader) on /dev/sda1

Notice the last option ? Now, the problem is the following: if I select the last choice (Windows 7 loader on /dev/sda1), I would expect GRUB2 to hand control back to W7's boot manager and ask me to choose again between XP, W7 or Ubuntu. Instead, I get the "NTLDR is missing" error message. Obviously, NTLDR *is* present in my first primary partition, and in fact it regularly works and loads XP if I choose it directly when W7's boot manager loads the first time. But if I choose to go back to W7's boot manager from GRUB2, I get the error instead. If I manually copy NTLDR, NTDETECT.COM and BOOT.INI to my second primary partition (the one where XP is installed) then I do not get the error anymore and XP loads immediately when I select the last option from GRUB2.

Any idea why the computer is looking at the second primary partition instead of going back to the first one ? I tried to rebuild Grub.cfg using the command "sudo update-grub" that I found here on the forums, but nothing changed. I don't understand what I am doing wrong :confused:

Just in case it's needed, here is the output of the command "sudo fdisk -l":

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x120c120b

Device Boot      Start         End          Blocks         Id       System
/dev/sda1   *           1          12               96358+     7    HPFS/NTFS
/dev/sda2             13        5233        41937682+    7    HPFS/NTFS
/dev/sda3         5234       10454       41937682+    7    HPFS/NTFS
/dev/sda4       10455       38913     228596887      f     W95 Ext'd (LBA)
/dev/sda5       10455       13587       25165791      7    HPFS/NTFS
/dev/sda6       13588       16612       24298281    83    Linux
/dev/sda7       16613       16709           779121    82    Linux swap / Solaris
/dev/sda8       16710       38587     175735003+    7    HPFS/NTFS
/dev/sda9       38588       38913         2618563+    7    HPFS/NTFS


Thanks everyone.

---

### Post by darkod on 2010-05-21
Are you asking this because you want to know, or is this a problem for you? Once you selected ubuntu in EasyBCD, why would you want to go back to windows (any version)?

In fact, in your situation I would disable the os-prober file in ubuntu so it doesn't detect any other OS and in that case you will not see the grub2 menu at all, it will start booting ubuntu right away.

Once you have chosen your OS in EasyBCD, why the grub2 menu? It just delays things.

If you want to do this, I can give you the commands to run.

Otherwise, one explanation could be if win7 loader is on /dev/sda1 as reported, but ntldr and XP boot files are probably on /dev/sda2. So the message would be correct, no ntldr on /dev/sda1. Why would it be looking for it, I have no clue.

---

### Post by arrange on 2010-05-21
Could you post the output of *boot_info_script*, as explained here?
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by UbuFlavio on 2010-05-21
Hi guys, thanks for the replies :)
Here is the output:


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda6 and 
                       looks at sector 252107674 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       192,779       192,717   7 HPFS/NTFS
/dev/sda2             192,780    84,068,144    83,875,365   7 HPFS/NTFS
/dev/sda3          84,068,145   167,943,509    83,875,365   7 HPFS/NTFS
/dev/sda4         167,943,571   625,137,344   457,193,774   f W95 Ext d (LBA)
/dev/sda5         167,943,573   218,275,154    50,331,582   7 HPFS/NTFS
/dev/sda6         218,275,218   266,871,779    48,596,562  83 Linux
/dev/sda7         266,871,843   268,430,084     1,558,242  82 Linux swap / Solaris
/dev/sda8         268,430,148   619,900,154   351,470,007   7 HPFS/NTFS
/dev/sda9         619,900,218   625,137,344     5,237,127   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        01CAD5A8B1F00680                       ntfs       Boot                          
/dev/sda2        01CAD5A8B1F00680                       ntfs       Windows XP                    
/dev/sda3        741CAD881CAD45C8                       ntfs       Windows 7                     
/dev/sda4: PTTYPE="dos" 
/dev/sda6        ff081586-3139-480e-86e1-75d45e2695a7   ext4       Ubuntu                        
/dev/sda7        3f66502b-61f6-42e6-b809-b81f70b814db   swap                                     
/dev/sda8        6894E30094E2D01C                       ntfs                                     
/dev/sda9        80B0B818B0B8171E                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

; 
;Warning: Boot.ini is used on Windows XP and earlier operating systems. 
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options. 
; 
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT 

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set ff081586-3139-480e-86e1-75d45e2695a7
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
set root='(hd0,6)'
search --no-floppy --fs-uuid --set ff081586-3139-480e-86e1-75d45e2695a7
set locale_dir=($root)/boot/grub/locale
set lang=en
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set ff081586-3139-480e-86e1-75d45e2695a7
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=ff081586-3139-480e-86e1-75d45e2695a7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set ff081586-3139-480e-86e1-75d45e2695a7
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=ff081586-3139-480e-86e1-75d45e2695a7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set ff081586-3139-480e-86e1-75d45e2695a7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set ff081586-3139-480e-86e1-75d45e2695a7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 01cad5a8b1f00680
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=ff081586-3139-480e-86e1-75d45e2695a7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=3f66502b-61f6-42e6-b809-b81f70b814db none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 129.0GB: boot/grub/core.img
 129.0GB: boot/grub/grub.cfg
 129.0GB: boot/initrd.img-2.6.32-21-generic
 129.0GB: boot/vmlinuz-2.6.32-21-generic
 129.0GB: initrd.img
 129.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  59 f2 f5 d5 f6 7d bf 8e  99 7a 73 dd e4 df 3f fc  |Y....}...zs...?.|
00000010  f9 db e3 92 57 eb da 52  1e d9 57 fb 2f 16 be f0  |....W..R..W./...|
00000020  12 64 b7 a3 86 2c 79 3b  aa df fb 22 f0 3a d9 c5  |.d...,y;...".:..|
00000030  26 e5 fe bb d4 23 d2 7e  0d e4 52 c5 1f d9 86 eb  |&....#.~..R.....|
00000040  3d 9a 89 56 b6 13 eb 82  6f a6 c5 40 db 58 ca b6  |=..V....o..@.X..|
00000050  df a7 fc a2 4f df 9d fb  b4 e4 9c 70 41 1b a9 ca  |....O......pA...|
00000060  fb 71 76 bb 39 d7 bd 78  8b a2 6e bb 28 4a 46 dd  |.qv.9..x..n.(JF.|
00000070  e7 6f de 4f 9c d0 3f 1b  a5 10 74 2c 22 92 1e f0  |.o.O..?...t,"...|
00000080  47 1f e4 35 55 f0 1a 0e  83 b9 d5 5e 7c f8 93 3a  |G..5U......^|..:|
00000090  31 fc 9e 07 fd 65 64 7b  b8 b3 2f 71 24 46 7a 77  |1....ed{../q$Fzw|
000000a0  d3 d3 dd 67 9f b9 0f ff  34 aa df ef 71 de c4 ab  |...g....4...q...|
000000b0  06 cf 0b 86 ff 39 05 f0  12 01 55 3d 9f d9 de 3e  |.....9....U=...>|
000000c0  76 dc f8 f1 3d 46 36 9f  50 34 2a 6f 2a b7 60 9b  |v...=F6.P4*o*.`.|
000000d0  2f 98 b3 70 fe 92 a5 e3  dd 12 47 d4 1e 51 63 be  |/..p......G..Qc.|
000000e0  83 62 d4 ba 91 eb c7 d5  70 18 e5 38 63 48 be cb  |.b......p..8cH..|
000000f0  b8 cd 23 be 1f 57 77 e4  b6 3d a3 0f 28 f6 8d 5c  |..#..Ww..=..(..\|
00000100  75 b0 68 cd 18 db f1 5f  0f 15 9f bf 30 5b 3a 63  |u.h...._....0[:c|
00000110  f1 0c de a8 ab 17 6f dd  be 33 7a e1 cd a2 fb 77  |......o..3z....w|
00000120  7f 1a 7b 7d c4 8e fc e3  53 65 23 c5 ab f3 cf 94  |..{}....Se#.....|
00000130  e4 d7 78 33 fe d4 8c 03  f9 ad 03 7e 5b ed b0 a6  |..x3.......~[...|
00000140  24 7c 9a 5b 51 8f 86 43  66 76 dd b1 6e bb 3c ae  |$|.[Q..Cfv..n.<.|
00000150  cd e0 7c 10 31 f1 ed c6  05 e1 ba 07 5e fd 6f 1f  |..|.1.......^.o.|
00000160  df b2 ac 83 ee 55 63 87  fe 73 34 4b 05 23 c7 86  |.....Uc..s4K.#..|
00000170  4d 4e 58 be b5 77 38 5f  12 d9 b3 6b 8b 8e 4f 7e  |MNX..w8_...k..O~|
00000180  1c d4 74 d0 ed 19 b9 3a  e6 49 a8 e3 8b fb c5 af  |..t....:.I......|
00000190  76 12 f9 4f 6a bc c1 7f  64 b5 f1 2b 62 97 e9 32  |v..Oj...d..+b..2|
000001a0  9d 13 3d 12 43 ec 1b be  7b e9 3a 3a e6 5a d3 94  |..=.C...{.::.Z..|
000001b0  83 7d 02 9c 93 e2 ae 6f  1c b5 67 11 ff c5 00 01  |.}.....o..g.....|
000001c0  c1 fe 07 57 c6 fe 02 00  00 00 be ff ff 02 00 fe  |...W............|
000001d0  ff ff 05 fe ff ff c0 ff  ff 02 91 86 e5 02 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by arrange on 2010-05-21
The problem is that the first 2 partitions have identical UUIDs.

[COLOR="Silver"]/dev/sda1        01CAD5A8B1F00680                       ntfs       Boot                          
/dev/sda2        01CAD5A8B1F00680                       ntfs       Windows XP[/COLOR]

---

### Post by UbuFlavio on 2010-05-21
> **arrange said:**
> The problem is that the first 2 partitions have identical UUIDs.

[COLOR=Silver]/dev/sda1        01CAD5A8B1F00680                       ntfs       Boot                          
/dev/sda2        01CAD5A8B1F00680                       ntfs       Windows XP[/COLOR]

Thanks :P But... how do I fix it ? I must confess that until now I had no idea what an UUID was... :oops:

---

### Post by arrange on 2010-05-21
I'd rather use something like```
menuentry "Microsoft Windows (on /dev/sda1)" {
        set root=(hd0,1)
        chainloader +1
}

```in */etc/grub.d/40_custom*. For detail see
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

Changing UUID is a risky business I guess but if you insist:
[http://ubuntuforums.org/showthread.php?t=1240146](http://ubuntuforums.org/showthread.php?t=1240146)
[http://technet.microsoft.com/en-us/sysinternals/bb897436.aspx](http://technet.microsoft.com/en-us/sysinternals/bb897436.aspx)

---

### Post by UbuFlavio on 2010-05-21
> **arrange said:**
> I'd rather use something like```
menuentry "Microsoft Windows (on /dev/sda1)" {
        set root=(hd0,1)
        chainloader +1
}

```in */etc/grub.d/40_custom*. For detail see
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

Changing UUID is a risky business I guess but if you insist:
[http://ubuntuforums.org/showthread.php?t=1240146](http://ubuntuforums.org/showthread.php?t=1240146)
[http://technet.microsoft.com/en-us/sysinternals/bb897436.aspx](http://technet.microsoft.com/en-us/sysinternals/bb897436.aspx)

Cool! Thank you so much. I'll definitely check those links out. I don't know how I ended up with two identical UUIDs in the first place though :confused:

Anyway, as a side note... I'm definitely not an expert about that Boot Info Script, but there are another couple of things that make me suspicious. For example this one from sda6:

> 
Boot sector info:  Grub 2 is installed in the boot sector of sda6 and looks at sector 252107674 of the same hard drive for core.img, but core.img can not be found at this location.or this one from both sda8 and sda9:

> 
Boot sector info:  According to the info in the boot sector, sda8 starts at sector 63.What do they mean exactly ? Are they normal or am I supposed to fix these as well ? If so, is there a way to do that without deleting the whole partition and re-creating it ?

Thanks again and sorry for the trouble.

---

### Post by darkod on 2010-05-21
The message about sector 63 is normal. I think it has something to do that it leaves one cylinder on each partition as boot sector for that partition. That is how you could install grub2 onto a partition. One cylinder has 63 sectors.

The message about grub2 being on sda6 is also good because that is your ubuntu root partition. And you said it yourself, without grub2 on it, EasyBCD can't connect to it. Remove grub2 and you can't boot ubuntu.

Otherwise, when grub2 gets onto some partition by error, you can use this procedure/fix on the corresponding partition to remove it:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by UbuFlavio on 2010-05-21
> **darkod said:**
> The message about sector 63 is normal. I think it has something to do that it leaves one cylinder on each partition as boot sector for that partition. That is how you could install grub2 onto a partition. One cylinder has 63 sectors.
 
Hi Darkod, thanks for the explanation :) But if it's normal, then why do sda1, sda2 and sda3 say "No errors found in the Boot Parameter Block" ? (I apologize in advance for my questions... I understand they must seem very dumb to you :P)
 
> 
The message about grub2 being on sda6 is also good because that is your ubuntu root partition. And you said it yourself, without grub2 on it, EasyBCD can't connect to it. Remove grub2 and you can't boot ubuntu.
 
Yes, but actually what worries me about that one is the part that says that "Grub 2 [...] looks at sector 252107674 of the same hard drive for core.img, but core.img can not be found at this location." I did check if that file (core.img) exists and it is in the Grub folder. In fact, Grub 2 does work. Maybe that file is not in sector 252107674, but in such case, why is Grub 2 looking for it in that particular sector ? 
 
Thank you again :)

---

### Post by darkod on 2010-05-21
> **UbuFlavio said:**
> Hi Darkod, thanks for the explanation :) But if it's normal, then why do sda1, sda2 and sda3 say "No errors found in the Boot Parameter Block" ? (I apologize in advance for my questions... I understand they must seem very dumb to you :P)

Not dumb at all, but I can't explain it. Maybe it makes a difference that on those partitions you have OS, or at least OS boot files, and the other partitions are just data partitions.
 

 > 
Yes, but actually what worries me about that one is the part that says that "Grub 2 [...] looks at sector 252107674 of the same hard drive for core.img, but core.img can not be found at this location." I did check if that file (core.img) exists and it is in the Grub folder. In fact, Grub 2 does work. Maybe that file is not in sector 252107674, but in such case, why is Grub 2 looking for it in that particular sector ? 
 
Thank you again :)I didn't notice that. Again, can't explain it. But as long as it works, don't worry about it.

Actually, I never use grub installed onto a partition, so I'm not too familiar with these situations and why the script results are such.

---

