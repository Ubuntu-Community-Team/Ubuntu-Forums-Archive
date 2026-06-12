---
title: "HELP - no boot after installing 10.04"
date: 2010-06-29
forum: Installation &amp; Upgrades
---

### Post by steve888 on 2010-06-29
Can anyone please detail what I need to do?

I've installed Ubuntu 10.04 on a friends NEC VERSA P7200, which had Windows XP.

I set up two new partitions, sda3 (for /) and sda5 for swap.

After installing 10.04, I rebooted to get "unknown filesystem", then grub rescue> prompt.

After reading a ton of suggestions, and after typing insmod normal, normal, I get the Ubuntu splash screen with ability to boot into Ubuntu or windows.

sudo fdisk -l gives

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe91ce91c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         784     6297448+  1b  Hidden W95 FAT32
/dev/sda2   *         785        8199    59560987+   7  HPFS/NTFS
/dev/sda3            8200        9658    11718656   83  Linux
/dev/sda4            9659        9730      572417    5  Extended
/dev/sda5            9659        9730      572416   82  Linux swap / Solaris


Rebooting gives the same error, then if I type insmod normal, normal, at the grub rescue> prompt it allows selection of ubuntu/windows/test memory etc.

Any help hugely appreciated.

---

### Post by Rubi1200 on 2010-06-29
Hi,
if you still have the CD you used to install Ubuntu you can use it to boot the computer.

Choose the option to Try Ubuntu not install and then click on the link in my signature.

Follow the instructions there and post the results back here so someone can help you resolve this.

Please do not forget to wrap the text with the # tag; it makes for easier reading.

---

### Post by steve888 on 2010-06-29
> **Rubi1200 said:**
> Hi,
if you still have the CD you used to install Ubuntu you can use it to boot the computer.

Choose the option to Try Ubuntu not install and then click on the link in my signature.

Follow the instructions there and post the results back here so someone can help you resolve this.

Please do not forget to wrap the text with the # tag; it makes for easier reading.

thanks for replying so quickly.

I don't quite understand "click on the link in my signature"?

I've started the LiveCD, selected Try without installing, selected English, and then it booted. I couldn't find a 'my signature' in accessories or anywhere.

Where is this 'my signature'?

----------update:

I've googled for this "my signature" CAN ANYONE share where to find this MY SIGNATURE?

---

### Post by Rubi1200 on 2010-06-29
Dear steve888,
look at the bottom of my post and you will see Bootscript courtesy of meierfra. Click on the link there.

---

### Post by steve888 on 2010-06-29
> **Rubi1200 said:**
> Dear steve888,
look at the bottom of my post and you will see Bootscript courtesy of meierfra. Click on the link there.

boy, how dumb was that! :)

here's the file 

```
#          Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /boot/grub/core.img 
                       /IO.SYS /MSDOS.SYS /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /BOOT.INI /ntldr /NTDETECT.COM /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 140645248 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    12,594,959    12,594,897  1b Hidden W95 FAT32
/dev/sda2    *     12,594,960   131,716,934   119,121,975   7 HPFS/NTFS
/dev/sda3         131,717,120   155,154,431    23,437,312  83 Linux
/dev/sda4         155,156,478   156,301,311     1,144,834   5 Extended
/dev/sda5         155,156,480   156,301,311     1,144,832  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        50E4-4707                              vfat       BACKUP                        
/dev/sda2        1C2C17822C17565C                       ntfs       HDD                           
/dev/sda3        42cb2f57-0e4b-4d24-9dab-3e86e3d3ddd2   ext4                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        baf39842-7621-4322-ab7b-e8e1ab662180   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
C:\CMDCONS\BOOTSECT.DAT="Windows PE Recovery Process W/O Data losing" /cmdcons 
C:\BOOTSECT.DOS="MS-Dos OEMSETUP Recovery Process..." 

=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

================================ sda2/BOOT.INI: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

=================== sda2: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 42cb2f57-0e4b-4d24-9dab-3e86e3d3ddd2
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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 42cb2f57-0e4b-4d24-9dab-3e86e3d3ddd2
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 42cb2f57-0e4b-4d24-9dab-3e86e3d3ddd2
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=42cb2f57-0e4b-4d24-9dab-3e86e3d3ddd2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 42cb2f57-0e4b-4d24-9dab-3e86e3d3ddd2
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=42cb2f57-0e4b-4d24-9dab-3e86e3d3ddd2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 42cb2f57-0e4b-4d24-9dab-3e86e3d3ddd2
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=42cb2f57-0e4b-4d24-9dab-3e86e3d3ddd2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 42cb2f57-0e4b-4d24-9dab-3e86e3d3ddd2
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=42cb2f57-0e4b-4d24-9dab-3e86e3d3ddd2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 42cb2f57-0e4b-4d24-9dab-3e86e3d3ddd2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 42cb2f57-0e4b-4d24-9dab-3e86e3d3ddd2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 50e4-4707
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 1c2c17822c17565c
    drivemap -s (hd0) ${root}
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=42cb2f57-0e4b-4d24-9dab-3e86e3d3ddd2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=baf39842-7621-4322-ab7b-e8e1ab662180 none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


  72.0GB: boot/grub/core.img
  70.1GB: boot/grub/grub.cfg
  72.0GB: boot/initrd.img-2.6.32-21-generic
  72.1GB: boot/initrd.img-2.6.32-22-generic
  72.0GB: boot/vmlinuz-2.6.32-21-generic
  72.1GB: boot/vmlinuz-2.6.32-22-generic
  72.1GB: initrd.img
  72.0GB: initrd.img.old
  72.1GB: vmlinuz
  72.0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  93 d1 f8 b9 31 ec f7 ab  f5 de 6e 4c 70 0c 88 04  |....1.....nLp...|
00000010  60 66 ce 04 fd 49 4f f9  fd 8e 8f 08 2d 3e 83 23  |`f...IO.....->.#|
00000020  fc a2 da d4 cf ea ee 57  46 9f 1a 20 3f dc 1c 8f  |.......WF.. ?...|
00000030  ab 06 7d 2c 9e 68 f9 b8  1e 93 6c 9f 60 ca 4e 37  |..},.h....l.`.N7|
00000040  ee 29 c3 34 6d 59 8f 30  09 b0 57 ac 8c 9d 09 79  |.).4mY.0..W....y|
00000050  e3 96 e1 94 7a 08 37 b1  fd 21 9e 97 3f 3a 5f d0  |....z.7..!..?:_.|
00000060  36 e0 ce 03 5f f3 cc 00  99 13 21 b4 41 90 e0 44  |6..._.....!.A..D|
00000070  9b 44 30 6a 4f a2 d1 80  66 3e 1a 8e f6 24 31 49  |.D0jO...f>...$1I|
00000080  60 4f b6 c4 70 b4 27 39  03 4c 75 26 1c ed 09 31  |`O..p.'9.Lu&...1|
00000090  09 80 a2 09 47 7b 02 d1  04 40 89 09 47 7b 02 68  |....G{...@..G{.h|
000000a0  02 10 63 12 8e f6 04 62  c2 89 89 09 07 88 f1 b3  |..c....b........|
000000b0  13 f0 83 d1 17 e6 f9 19  87 73 50 f8 6c f2 71 73  |.........sP.l.qs|
000000c0  aa fb 83 38 3b bb 8b fa  ae fb c5 89 e1 22 a1 20  |...8;........". |
000000d0  f1 31 c6 f5 10 92 a8 9e  0b a5 77 ee 3b 1e 7f 76  |.1........w.;..v|
000000e0  9f 89 86 90 fc 7e d8 79  60 7e c8 7f e7 b7 4e d5  |.....~.y`~....N.|
000000f0  97 67 02 28 00 e9 53 a9  9a ff 10 b8 a6 a0 52 bb  |.g.(..S.......R.|
00000100  7f b0 a8 9c f1 88 38 ba  a6 fb 8a 54 d5 68 b7 b9  |......8....T.h..|
00000110  c0 14 d6 68 f6 dc e1 83  b3 e8 c1 89 32 51 64 8e  |...h........2Qd.|
00000120  ab 31 9d 85 94 6d b9 19  19 f9 ef 1f d4 c1 60 e0  |.1...m........`.|
00000130  a7 77 c2 73 0b a8 0a ad  cd 6c af 33 86 fc e1 81  |.w.s.....l.3....|
00000140  61 00 28 79 fe de 93 87  f2 c4 e7 80 7a e1 fd 83  |a.(y........z...|
00000150  54 b5 4f ad 04 0a 0e 04  e3 4c f0 40 9f b9 62 1e  |T.O......L.@..b.|
00000160  d6 06 c7 89 dc ec 9e 8e  2b e7 5c 74 95 5e d2 d9  |........+.\t.^..|
00000170  21 2c c4 0d 78 81 e5 ff  80 da 30 fe 97 38 ac 61  |!,..x.....0..8.a|
00000180  58 e6 01 03 58 fc 41 ed  9a 3b 8b f3 49 54 b5 d6  |X...X.A..;..IT..|
00000190  ff 2b f1 ed 43 e1 94 8c  ff 10 90 45 35 62 ff 5c  |.+..C......E5b.\|
000001a0  9d 9c 33 06 3d b5 ec 77  a0 e7 4d 75 c8 a4 14 e6  |..3.=..w..Mu....|
000001b0  bf 06 e1 55 36 56 e4 e4  9f 73 8f bb 84 31 00 fe  |...U6V...s...1..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 78 11 00 00 00  |...........x....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```t
Thanks for explaining.

Hope this is better

---

### Post by Rubi1200 on 2010-06-29
Hi,
thanks for getting this to us.

> boy, how dumb was that! :smile: Actually, no. Next time I need to be more precise with my instructions. Therefore, it is a learning experience for both of us.

Could you please go back and edit your post and wrap the results using the # tags?

Like this, just an example:



```
#          Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.

sda1: __________________________________________________  _______________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /boot/grub/core.img 
                       /IO.SYS /MSDOS.SYS /COMMAND.COM

sda2: __________________________________________________  _______________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /BOOT.INI /ntldr /NTDETECT.COM /boot/grub/core.img

sda3: __________________________________________________  _______________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 140645248 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________  _______________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________  _______________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  
```It makes it much easier to read. You can do this by clicking edit on your post then Advanced, highlight the whole text and then use the # tag.

Thanks!

---

### Post by darkod on 2010-06-29
1. Boot ubuntu with the manual way you can use. Delete the /boot/grub/core.img file from sda1 and sda2. (How did it get there???)

2. Then reinstall grub2 to the MBR with:

sudo grub-install /dev/sda

3. Try to update the grub.cfg with:

sudo update-grub

Restart and see if you can boot normally now.

---

### Post by steve888 on 2010-06-29
> **darkod said:**
> 1. Boot ubuntu with the manual way you can use. Delete the /boot/grub/core.img file from sda1 and sda2. (How did it get there???)

2. Then reinstall grub2 to the MBR with:

sudo grub-install /dev/sda

3. Try to update the grub.cfg with:

sudo update-grub

Restart and see if you can boot normally now.

Hi Darko

I followed your instructions (deleted boot/grub from sda1 and sda2), sudo grub-install, as above, but the sudo update-grub responds:

/etc/default/grub: 1: /#: not found

And wouldn't reboot,except with insmod normal, normal, as before.

---

### Post by darkod on 2010-06-29
> **steve888 said:**
> Hi Darko

I followed your instructions (deleted boot/grub from sda1 and sda2), sudo grub-install, as above, but the sudo update-grub responds:

/etc/default/grub: 1: /#: not found

And wouldn't reboot,except with insmod normal, normal, as before.

OK, how about:

sudo grub-mkconfig
sudo update-grub

Still the same error?

---

### Post by steve888 on 2010-06-29
> **darkod said:**
> OK, how about:

sudo grub-mkconfig
sudo update-grub

Still the same error?


here's the output of the first line (sudo grub-mkconfig (Judith is sitting nearby, so I've got my fingers crossed we're close :)

judith@judith-laptop:~$ sudo grub-mkconfig
/etc/default/grub: 1: /#: not found

------------------------

new output of boot_info_script follows:

                ```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /IO.SYS /MSDOS.SYS 
                       /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /BOOT.INI /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 140645248 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    12,594,959    12,594,897  1b Hidden W95 FAT32
/dev/sda2    *     12,594,960   131,716,934   119,121,975   7 HPFS/NTFS
/dev/sda3         131,717,120   155,154,431    23,437,312  83 Linux
/dev/sda4         155,156,478   156,301,311     1,144,834   5 Extended
/dev/sda5         155,156,480   156,301,311     1,144,832  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        50E4-4707                              vfat       BACKUP                        
/dev/sda2        1C2C17822C17565C                       ntfs       HDD                           
/dev/sda3        42cb2f57-0e4b-4d24-9dab-3e86e3d3ddd2   ext4                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        baf39842-7621-4322-ab7b-e8e1ab662180   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
C:\CMDCONS\BOOTSECT.DAT="Windows PE Recovery Process W/O Data losing" /cmdcons 
C:\BOOTSECT.DOS="MS-Dos OEMSETUP Recovery Process..." 

================================ sda2/BOOT.INI: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 42cb2f57-0e4b-4d24-9dab-3e86e3d3ddd2
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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 42cb2f57-0e4b-4d24-9dab-3e86e3d3ddd2
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 42cb2f57-0e4b-4d24-9dab-3e86e3d3ddd2
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=42cb2f57-0e4b-4d24-9dab-3e86e3d3ddd2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 42cb2f57-0e4b-4d24-9dab-3e86e3d3ddd2
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=42cb2f57-0e4b-4d24-9dab-3e86e3d3ddd2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 42cb2f57-0e4b-4d24-9dab-3e86e3d3ddd2
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=42cb2f57-0e4b-4d24-9dab-3e86e3d3ddd2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 42cb2f57-0e4b-4d24-9dab-3e86e3d3ddd2
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=42cb2f57-0e4b-4d24-9dab-3e86e3d3ddd2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 42cb2f57-0e4b-4d24-9dab-3e86e3d3ddd2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 42cb2f57-0e4b-4d24-9dab-3e86e3d3ddd2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 50e4-4707
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 1c2c17822c17565c
    drivemap -s (hd0) ${root}
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=42cb2f57-0e4b-4d24-9dab-3e86e3d3ddd2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=baf39842-7621-4322-ab7b-e8e1ab662180 none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


  72.0GB: boot/grub/core.img
  70.1GB: boot/grub/grub.cfg
  72.0GB: boot/initrd.img-2.6.32-21-generic
  72.1GB: boot/initrd.img-2.6.32-22-generic
  72.0GB: boot/vmlinuz-2.6.32-21-generic
  72.1GB: boot/vmlinuz-2.6.32-22-generic
  72.1GB: initrd.img
  72.0GB: initrd.img.old
  72.1GB: vmlinuz
  72.0GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  93 d1 f8 b9 31 ec f7 ab  f5 de 6e 4c 70 0c 88 04  |....1.....nLp...|
00000010  60 66 ce 04 fd 49 4f f9  fd 8e 8f 08 2d 3e 83 23  |`f...IO.....->.#|
00000020  fc a2 da d4 cf ea ee 57  46 9f 1a 20 3f dc 1c 8f  |.......WF.. ?...|
00000030  ab 06 7d 2c 9e 68 f9 b8  1e 93 6c 9f 60 ca 4e 37  |..},.h....l.`.N7|
00000040  ee 29 c3 34 6d 59 8f 30  09 b0 57 ac 8c 9d 09 79  |.).4mY.0..W....y|
00000050  e3 96 e1 94 7a 08 37 b1  fd 21 9e 97 3f 3a 5f d0  |....z.7..!..?:_.|
00000060  36 e0 ce 03 5f f3 cc 00  99 13 21 b4 41 90 e0 44  |6..._.....!.A..D|
00000070  9b 44 30 6a 4f a2 d1 80  66 3e 1a 8e f6 24 31 49  |.D0jO...f>...$1I|
00000080  60 4f b6 c4 70 b4 27 39  03 4c 75 26 1c ed 09 31  |`O..p.'9.Lu&...1|
00000090  09 80 a2 09 47 7b 02 d1  04 40 89 09 47 7b 02 68  |....G{...@..G{.h|
000000a0  02 10 63 12 8e f6 04 62  c2 89 89 09 07 88 f1 b3  |..c....b........|
000000b0  13 f0 83 d1 17 e6 f9 19  87 73 50 f8 6c f2 71 73  |.........sP.l.qs|
000000c0  aa fb 83 38 3b bb 8b fa  ae fb c5 89 e1 22 a1 20  |...8;........". |
000000d0  f1 31 c6 f5 10 92 a8 9e  0b a5 77 ee 3b 1e 7f 76  |.1........w.;..v|
000000e0  9f 89 86 90 fc 7e d8 79  60 7e c8 7f e7 b7 4e d5  |.....~.y`~....N.|
000000f0  97 67 02 28 00 e9 53 a9  9a ff 10 b8 a6 a0 52 bb  |.g.(..S.......R.|
00000100  7f b0 a8 9c f1 88 38 ba  a6 fb 8a 54 d5 68 b7 b9  |......8....T.h..|
00000110  c0 14 d6 68 f6 dc e1 83  b3 e8 c1 89 32 51 64 8e  |...h........2Qd.|
00000120  ab 31 9d 85 94 6d b9 19  19 f9 ef 1f d4 c1 60 e0  |.1...m........`.|
00000130  a7 77 c2 73 0b a8 0a ad  cd 6c af 33 86 fc e1 81  |.w.s.....l.3....|
00000140  61 00 28 79 fe de 93 87  f2 c4 e7 80 7a e1 fd 83  |a.(y........z...|
00000150  54 b5 4f ad 04 0a 0e 04  e3 4c f0 40 9f b9 62 1e  |T.O......L.@..b.|
00000160  d6 06 c7 89 dc ec 9e 8e  2b e7 5c 74 95 5e d2 d9  |........+.\t.^..|
00000170  21 2c c4 0d 78 81 e5 ff  80 da 30 fe 97 38 ac 61  |!,..x.....0..8.a|
00000180  58 e6 01 03 58 fc 41 ed  9a 3b 8b f3 49 54 b5 d6  |X...X.A..;..IT..|
00000190  ff 2b f1 ed 43 e1 94 8c  ff 10 90 45 35 62 ff 5c  |.+..C......E5b.\|
000001a0  9d 9c 33 06 3d b5 ec 77  a0 e7 4d 75 c8 a4 14 e6  |..3.=..w..Mu....|
000001b0  bf 06 e1 55 36 56 e4 e4  9f 73 8f bb 84 31 00 fe  |...U6V...s...1..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 78 11 00 00 00  |...........x....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by darkod on 2010-06-29
The script results look good, but it seems some grub2 files are missing/not installed.

If you run this what does it say which packages are installed:

```
grub-install -v && aptitude show grub|head -2 && aptitude show grub-pc|head -2 && aptitude show grub-common|head -2 && aptitude show os-prober|head -2
```

Copy paste the commands to avoid spelling errors. You can do that, copy here, and paste in terminal.

---

### Post by steve888 on 2010-06-29
> **darkod said:**
> The script results look good, but it seems some grub2 files are missing/not installed.

If you run this what does it say which packages are installed:

```
grub-install -v && aptitude show grub|head -2 && aptitude show grub-pc|head -2 && aptitude show grub-common|head -2 && aptitude show os-prober|head -2
```Copy paste the commands to avoid spelling errors. You can do that, copy here, and paste in terminal.
   
this is the output

grub-install (GNU GRUB 1.98-1ubuntu6)
Package: grub
State: not installed
Package: grub-pc
State: installed
Package: grub-common
State: installed
Package: os-prober
State: installed

if what you say is correct, maybe I have a faulty install cd - after the problems the first time, i did a full reinstall, same problems.

maybe there was a switch I missed. I've done a number of 10.04 installs (actually, I just remembered, I've done mostly upgrades to 10.04 without problems.

---

### Post by darkod on 2010-06-29
I'm puzzled. It all looks fine, but it complains about /etc/default/grub when you try to run update-grub.
I don't know how to fix that. :(

---

### Post by steve888 on 2010-06-29
> **darkod said:**
> I'm puzzled. It all looks fine, but it complains about /etc/default/grub when you try to run update-grub.
I don't know how to fix that. :(

Thanks Darko, I really appreciate the effort

I'll clear the partitions (linux, anyway) and reinstall.

---

### Post by Rubi1200 on 2010-06-29
If you are considering a reinstall anyway, can I have one (1) crack at this?

From the LiveCD, try this:

```
sudo mkdir /media/sda3

``````
sudo mount /dev/sda3 /media/sda3
``````
sudo grub-install --root-directory=/media/sda3 /dev/sda
``` Reboot the computer (without the CD) and let me know what happens please.

Not sure if you need to run 

```
sudo update-grub
```

Possibly.

---

### Post by steve888 on 2010-06-29
> **Rubi1200 said:**
> If you are considering a reinstall anyway, can I have one (1) crack at this?

From the LiveCD, try this:

```
sudo mkdir /media/sda3

``````
sudo mount /dev/sda3 /media/sda3
``````
sudo grub-install --root-directory=/media/sda3 /dev/sda
``` Reboot the computer (without the CD) and let me know what happens please.

Not sure if you need to run 

```
sudo update-grub
```Possibly.

I installed straight after my last post - so are the above lines instructions still valid?

I repartitioned/reformatted the disk to re-include two linux primary partitions for /  and swap.

Fresh install, same problem.

This is weird. I'm wondering if the XP has viruses that hijacked the boot blocks or something.

Found one trojan on the sda1 drive (the hidden recovery vfat disk).

currently running clam on the main sda2.
 
btw, My friend was muttering last night "I should just get a mac, all my friends say they're so easy to use"... :)  Working hard here for Ubuntu! I'm really keen to get this solved, so all help appreciated.

uhm, this might seem a dumb question, but I've googled and not found a definitive answer. the NEC Versa P7200 is a dual core laptop, is it a 64bit machine (I've installed standard 32 bit Ubuntu 10.04)?

---

### Post by darkod on 2010-06-29
> **steve888 said:**
> I installed straight after my last post - so are the above lines instructions still valid?

I repartitioned/reformatted the disk to re-include two linux primary partitions for /  and swap.

Fresh install, same problem.

This is weird. I'm wondering if the XP has viruses that hijacked the boot blocks or something.

Found one trojan on the sda1 drive (the hidden recovery vfat disk).

Still running clam on the main hd.

These commands did the same as we tried earlier with grub-install /dev/sda. When you have booted your hdd installation, you can just use that short version of the command.
From live mode, you need the additional commands to mount the root partition.
So basically, they do nothing new.

It is really strange that you can't boot even the new install. I'm really out of ideas.

---

### Post by steve888 on 2010-06-29
> **darkod said:**
> These commands did the same as we tried earlier with grub-install /dev/sda. When you have booted your hdd installation, you can just use that short version of the command.
From live mode, you need the additional commands to mount the root partition.
So basically, they do nothing new.

It is really strange that you can't boot even the new install. I'm really out of ideas.

here's the latest boot_info_script output


   ```
        Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 98
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /IO.SYS /MSDOS.SYS 
                       /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /BOOT.INI /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    12,594,959    12,594,897  1b Hidden W95 FAT32
/dev/sda2    *     12,594,960   131,716,934   119,121,975   7 HPFS/NTFS
/dev/sda3         131,716,935   154,962,989    23,246,055  83 Linux
/dev/sda4         154,962,990   156,296,384     1,333,395  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        50E4-4707                              vfat       BACKUP                        
/dev/sda2        1C2C17822C17565C                       ntfs       HDD                           
/dev/sda3        a654aa21-db96-4ee5-8387-18d6793672d9   ext4                                     
/dev/sda4        42ad74fe-338b-4e72-9350-1b1d36a91817   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /media/HDD               fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
C:\CMDCONS\BOOTSECT.DAT="Windows PE Recovery Process W/O Data losing" /cmdcons 
C:\BOOTSECT.DOS="MS-Dos OEMSETUP Recovery Process..." 

================================ sda2/BOOT.INI: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 

=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set a654aa21-db96-4ee5-8387-18d6793672d9
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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set a654aa21-db96-4ee5-8387-18d6793672d9
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set a654aa21-db96-4ee5-8387-18d6793672d9
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=a654aa21-db96-4ee5-8387-18d6793672d9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set a654aa21-db96-4ee5-8387-18d6793672d9
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=a654aa21-db96-4ee5-8387-18d6793672d9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set a654aa21-db96-4ee5-8387-18d6793672d9
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=a654aa21-db96-4ee5-8387-18d6793672d9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set a654aa21-db96-4ee5-8387-18d6793672d9
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=a654aa21-db96-4ee5-8387-18d6793672d9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set a654aa21-db96-4ee5-8387-18d6793672d9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set a654aa21-db96-4ee5-8387-18d6793672d9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 50e4-4707
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 1c2c17822c17565c
    drivemap -s (hd0) ${root}
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=a654aa21-db96-4ee5-8387-18d6793672d9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda4 during installation
UUID=42ad74fe-338b-4e72-9350-1b1d36a91817 none            swap    sw              0       0

=================== sda3: Location of files loaded by Grub: ===================


  76.1GB: boot/grub/core.img
  76.4GB: boot/grub/grub.cfg
  76.4GB: boot/initrd.img-2.6.32-21-generic
  76.5GB: boot/initrd.img-2.6.32-22-generic
  76.3GB: boot/vmlinuz-2.6.32-21-generic
  76.4GB: boot/vmlinuz-2.6.32-22-generic
  76.5GB: initrd.img
  76.4GB: initrd.img.old
  76.4GB: vmlinuz
  76.3GB: vmlinuz.old
```have run grub update:

judith@judith-laptop:~$ sudo update-grub
[sudo] password for judith: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows NT/2000/XP (loader) on /dev/sda1
Found Microsoft Windows XP Professional on /dev/sda2
done
"

same problem "unknown filesystem"
grub rescue>insmod normal
grub rescue>normal
...then splash screen with list of boot options...

could it be the bios?

or bios settings? I've had a look but didn't find anything obvious

---

### Post by darkod on 2010-06-29
It all looks good. But it doesn't work. :(

---

### Post by steve888 on 2010-06-29
> **darkod said:**
> It all looks good. But it doesn't work. :(

after running grub rescue> normal, splash screen and selecting linux,

after about a 15-20 second delay (blank screen) briefly I see a "unknown controller ... " (too fast to see all the detail)... then it continues booting.

Which log files would show the problem?

---

### Post by Rubi1200 on 2010-06-30
If you have the installation CD for XP, what about a fresh install of that and then Ubuntu? If, as you say, there might be a virus lurking somewhere, reformatting and reinstalling XP would surely get rid of it.

As darkod already pointed out, this is a bit strange because the bootscript results indicate that everything is normal.

In any event, I hope you get this resolved soon.

:-)

---

### Post by Rubi1200 on 2010-06-30
This may not help much, but what about trying Karmic Koala (9.10)? It may not be the latest and greatest, but it is stable and is supported until April 2011.

[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)

---

### Post by steve888 on 2010-07-01
> **Rubi1200 said:**
> If you have the installation CD for XP, what about a fresh install of that and then Ubuntu? If, as you say, there might be a virus lurking somewhere, reformatting and reinstalling XP would surely get rid of it.

As darkod already pointed out, this is a bit strange because the bootscript results indicate that everything is normal.

In any event, I hope you get this resolved soon.

:-)

Hi, thanks for the idea, but my friend has a stack of stuff on her Windows disk (long story -- she inherited the computer from partner, and hasn't had time to check through everything to see if she wants to keep, backup or delete).

So, was needing to keep the Windows XP partition as is (we could spend hours figuring out what was to be backed up yadda yadda).

Easiest solution I thought would be to dual boot with Ubuntu, set up systems as needed (e.g Firefox doesn't access the Internet under XP, and after an hour of trying to find the problem, decided to install Ubuntu.)

using Ubuntu I found 9 trojan viruses on her XP disk.

At present, the insmod normal, normal boot is getting a result, but little things like Ubuntu not shutting down the computer is annoying.

As for the other reply, installing Ubuntu 9.10, yes I could -- and I enjoyed using 9.10, but then we'd be losing the time and updates and ...

Probably the best thing is to back up to DVD all that she thinks might be worthwhile on the XP partition, then reinstall Windows XP and Ubuntu 10.04 (if that doesn't work then maybe install 9.10).

I've read to her comments from one website concerning ease of use of MAC versus Linux ("Linux easier"), to dissuade her from pulling the plug entirely on Linux.

:)

---

