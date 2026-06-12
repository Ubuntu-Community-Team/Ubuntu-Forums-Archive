---
title: "Problem after installing Ubuntu"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by JohnyXD on 2010-10-11
I just installed Ubuntu 10.04 desktop and of course, it's AWESOME! :biggrin:
I have chosen Dual boot with Windows Vista, the thing is: I can't boot properly on Windows, I choose it from the boot screen (grub... I guess :P ) and then it loads Windows and then the screen goes black!
this is my first (successful) install for Ubuntu so any details would be appreciated
note: I think my PC has acceptable features and Windows was running normally before the install

---

### Post by rastynakata on 2010-10-11
are you using wubi?

---

### Post by JohnyXD on 2010-10-12
yeah

---

### Post by JohnyXD on 2010-10-12
I know that some of you will say "Why is he even keeping Windows Vista?"
Well... It's not that I'm keeping it but I just have a few things I'd like to retrieve like my bookmarks on Firefox
And it's not really nice to say that I can't use Windows anymore because of Ubuntu -_-
Please I need help! Get rid of this black screen for me X'(

---

### Post by bcbc on 2010-10-12
if you installed wubi, you should first have the windows boot manager that offers either windows or ubuntu. Not grub. Only after selecting Ubuntu does the grub menu show up.

Please run the [bootinfoscript]("http://bootinfoscript.sourceforge.net") and paste the results so we can take a look at what's up.

---

### Post by JohnyXD on 2010-10-13
ummm... is this right? (there was no file with the name RESULTS.txt)


wajih@johny:~$ sudo bash /home/wajih/Downloads/boot_info_script055.sh
/home/wajih/Downloads/boot_info_script055.sh: line 2: syntax error near unexpected token `newline'
/home/wajih/Downloads/boot_info_script055.sh: line 2: `<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">'
wajih@johny:~$

---

### Post by bcbc on 2010-10-13
> **JohnyXD said:**
> ummm... is this right? (there was no file with the name RESULTS.txt)


wajih@johny:~$ sudo bash /home/wajih/Downloads/boot_info_script055.sh
/home/wajih/Downloads/boot_info_script055.sh: line 2: syntax error near unexpected token `newline'
/home/wajih/Downloads/boot_info_script055.sh: line 2: `<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">'
wajih@johny:~$

Try again - it seems like you downloaded something other than boot info script. The first few lines should look like this:
> #!/bin/bash
VERSION=0.55
DATE="February 15th, 2010"
#to use this script:
#
#     sudo bash boot_info_script055.sh
#or
#     su -
#     bash boot_info_script055.sh
#
#
### last-modified 
#
#author  Ulrich Meierfrankenfeld (aka meierfra.) 
# with  contributions from caljohnsmith
# (both members of ubuntuforums.org)
# and Gert Hulselmans
#


---

### Post by JohnyXD on 2010-10-13
you're right :D
It was partially downloaded for some reason
anyway, the contents of RESULTS.txt are:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    25,173,854    25,173,792  27 Hidden HPFS/NTFS
/dev/sda2    *     25,173,855   700,104,907   674,931,053   7 HPFS/NTFS
/dev/sda3         812,933,120   976,771,071   163,837,952   7 HPFS/NTFS
/dev/sda4         700,106,750   812,933,119   112,826,370   5 Extended
/dev/sda5         700,106,752   808,232,959   108,126,208  83 Linux
/dev/sda6         808,235,008   812,933,119     4,698,112  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        B42CF9592CF916D8                       ntfs       _OEMBP                        
/dev/sda2        06D0FAC5D0FABA4F                       ntfs       HDD                           
/dev/sda3        7CF8B7AFF8B76654                       ntfs       DATA                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        5b3a7d59-00f5-4b62-835e-3a60fbfca997   ext4                                     
/dev/sda6        a3b9e0fd-65a0-4564-8e4f-561001f918e6   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 5b3a7d59-00f5-4b62-835e-3a60fbfca997
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 5b3a7d59-00f5-4b62-835e-3a60fbfca997
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 5b3a7d59-00f5-4b62-835e-3a60fbfca997
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=5b3a7d59-00f5-4b62-835e-3a60fbfca997 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 5b3a7d59-00f5-4b62-835e-3a60fbfca997
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=5b3a7d59-00f5-4b62-835e-3a60fbfca997 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 5b3a7d59-00f5-4b62-835e-3a60fbfca997
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=5b3a7d59-00f5-4b62-835e-3a60fbfca997 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 5b3a7d59-00f5-4b62-835e-3a60fbfca997
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=5b3a7d59-00f5-4b62-835e-3a60fbfca997 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 5b3a7d59-00f5-4b62-835e-3a60fbfca997
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 5b3a7d59-00f5-4b62-835e-3a60fbfca997
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set b42cf9592cf916d8
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 06d0fac5d0faba4f
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=5b3a7d59-00f5-4b62-835e-3a60fbfca997 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=a3b9e0fd-65a0-4564-8e4f-561001f918e6 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 386.5GB: boot/grub/core.img
 363.2GB: boot/grub/grub.cfg
 386.6GB: boot/initrd.img-2.6.32-21-generic
 386.7GB: boot/initrd.img-2.6.32-25-generic
 386.7GB: boot/vmlinuz-2.6.32-21-generic
 386.6GB: boot/vmlinuz-2.6.32-25-generic
 386.7GB: initrd.img
 386.6GB: initrd.img.old
 386.6GB: vmlinuz
 386.7GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  05 06 13 9f 7c 62 c1 78  25 91 51 fc 36 a1 cd d9  |....|b.x%.Q.6...|
00000010  d9 4c 75 02 2f 70 b8 ba  a9 b1 fd 17 9e 4a 1a 32  |.Lu./p.......J.2|
00000020  1a 20 3b 38 8e 1f 6f 07  c0 e9 20 e2 01 83 51 1b  |. ;8..o... ...Q.|
00000030  37 71 51 55 55 25 cc 9d  f0 b6 50 7f 99 e9 6a ea  |7qQUU%....P...j.|
00000040  70 3b 40 bb c3 4b 7b d7  d6 49 ec e2 76 69 51 d1  |p;@..K{..I..viQ.|
00000050  74 59 e5 7e 0c 5d 3f f8  14 bf 19 6a 6f ee 68 77  |tY.~.]?....jo.hw|
00000060  50 4d 60 70 63 83 b4 41  4a 49 2e 18 86 1e 8e 31  |PM`pc..AJI.....1|
00000070  22 b2 db a6 95 6e 69 23  09 52 ae 31 7d 2b 4f 72  |"....ni#.R.1}+Or|
00000080  df 35 13 e9 a4 22 23 81  83 d5 7c de d4 dc 4d 2d  |.5..."#...|...M-|
00000090  8e 36 b0 3a bf bc a7 eb  72 4c 52 e3 69 55 57 11  |.6.:....rLR.iUW.|
000000a0  9a ab e5 9b fa 75 67 0b  45 b9 62 4b f3 7a 56 53  |.....ug.E.bK.zVS|
000000b0  90 8a 34 79 0b 17 63 9c  a0 d8 23 27 25 d1 cd df  |..4y..c...#'%...|
000000c0  3f 09 c0 ea 5d 33 31 1f  43 fa 2b 9f 6a a4 9b f0  |?...]31.C.+.j...|
000000d0  02 cb 27 2c 3c 25 45 98  e7 7f 38 dd 02 8c cd 94  |..',<%E...8.....|
000000e0  94 52 64 b5 fb af b6 db  0a 17 cb 59 c5 2a 9e f9  |.Rd........Y.*..|
000000f0  e9 b8 7f 74 b0 05 dc 5f  28 5f d3 15 f5 85 33 56  |...t..._(_....3V|
00000100  b3 92 22 72 09 7b c4 bd  76 c6 35 34 30 e0 70 80  |.."r.{..v.540.p.|
00000110  ed af d2 51 26 2a ba 94  ea e4 5b 41 d6 2c c7 f8  |...Q&*....[A.,..|
00000120  b5 57 5d 2e df 09 72 9b  57 79 48 07 47 4e 9e a9  |.W]...r.WyH.GN..|
00000130  e1 0b 6c 15 c7 dd a4 c4  96 0c d3 6c 28 70 da 15  |..l........l(p..|
00000140  5a b3 dd 8a 31 58 25 16  7f 65 5f 35 05 bc 63 f4  |Z...1X%..e_5..c.|
00000150  40 a8 fd 54 c0 7e 2c 45  fd 6e f8 d6 96 15 3f 55  |@..T.~,E.n....?U|
00000160  6d 95 4e 9f f7 8d 91 21  1a 74 9d bf b5 45 f2 2f  |m.N....!.t...E./|
00000170  68 b2 22 92 af 05 39 de  39 e2 4f f5 3c 4b bb 4f  |h."...9.9.O.<K.O|
00000180  b8 ad 6d 5e 9f 9b dd ca  64 0b c9 1c cd 8b 9a ae  |..m^....d.......|
00000190  4b d0 df 42 ac ce e1 6e  67 b5 65 7c 5f 64 0a 85  |K..B...ng.e|_d..|
000001a0  42 9e 95 02 2c 8f 10 82  0c 0d 40 67 5f 0f 09 6d  |B...,.....@g_..m|
000001b0  f1 00 78 47 2b 64 33 46  36 73 67 0a 46 19 00 fe  |..xG+d3F6sg.F...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 e0 71 06 00 fe  |............q...|
000001d0  ff ff 05 fe ff ff 02 e0  71 06 00 b8 47 00 00 00  |........q...G...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde

---

### Post by bcbc on 2010-10-13
FYI it's not a wubi install (wubi is the windows ubuntu installer that installs ubuntu to a virtual disk). You have a real dual boot installed direct to partition.

I think the problem is that grub has identified your windows as 'windows recovery environment'. To me it appears that that one is in fact your windows. So try that.
Also, run "sudo update-grub". Sometimes the grub menu doesn't correctly pick up windows the first time.

---

### Post by JohnyXD on 2010-10-13
yeah I noticed that already, when I try to run Windows it goes to the recovery and vice versa
anyway I used "sudo update-grub" and I'll post the results in about 30~35 min(time for rebooting AFTER I go grab a bite cuz I'm starving :P )

---

### Post by JohnyXD on 2010-10-13
Nothing changed :'(
not even the order between win vista and win recovery and the black screen is still there X'(

---

### Post by bcbc on 2010-10-13
Did you let the Ubuntu installer partition your drive? This is known to cause problems with Vista and win7. 

You should boot from your vista repair CD and let it repair itself.

---

### Post by JohnyXD on 2010-10-13
Yeah, that could work!! it's just that... I have the original licensed Win Vista and all but... I didn't get a CD with with my PC -_-
will recovery work?

---

### Post by bcbc on 2010-10-13
> **JohnyXD said:**
> Yeah, that could work!! it's just that... I have the original licensed Win Vista and all but... I didn't get a CD with with my PC -_-
will recovery work?

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by JohnyXD on 2010-10-13
thanks a bunch :D
I'll go buy an empty CD tomorrow and try the recovery :)
BTW, is the recovery in the boot menu not good (sorry if it's silly, I didn't get the difference :P )

---

### Post by bcbc on 2010-10-13
> **JohnyXD said:**
> thanks a bunch :D
I'll go buy an empty CD tomorrow and try the recovery :)
BTW, is the recovery in the boot menu not good (sorry if it's silly, I didn't get the difference :P )

The recovery supplied on computers tend to restore to the factory default (i.e. wipe everything you currently have). I don't know what your particular recovery partition does - perhaps it has a repair option.

I haven't ever had to repair a vista install so I can't really advise on that. There are others on the forums who know more. But note if your windows repair ends up reinstalling the windows bootloader, then you'll have to reinstall grub using a live CD. [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by corcomp84 on 2010-10-13
from what I can see, that wubi thing sucks... I have been looking at the forums and lots of problems.. I would just install it the right way, directly to the partition.. that way you dont have all of these problems.. but what I would do before you go any further is go into your bios and disable automatic restart on system error.. that way you can see what exactly is failing... it will turn to a blue screen and you will be able to post the results..

---

### Post by bcbc on 2010-10-13
> **corcomp84 said:**
> from what I can see, that wubi thing sucks... I have been looking at the forums and lots of problems.. I would just install it the right way, directly to the partition.. that way you dont have all of these problems.. but what I would do before you go any further is go into your bios and disable automatic restart on system error.. that way you can see what exactly is failing... it will turn to a blue screen and you will be able to post the results..

Thanks for sharing. This isn't a wubi install.

---

### Post by corcomp84 on 2010-10-13
o I am sorry I thought they said it was on an earlier post..

---

### Post by corcomp84 on 2010-10-13
> **rastynakata said:**
> are you using wubi?

> **JohnyXD said:**
> yeah


I must have misunderstood: stood..

---

### Post by bcbc on 2010-10-13
> **corcomp84 said:**
> o I am sorry I thought they said it was on an earlier post..

Read the entire thread before imparting your wisdom in the future. The OP was mistaken.

And PS, the Community Cafe or the Testimonials subforum is a better place for your personal opinion about what sucks in Ubuntu.

---

### Post by corcomp84 on 2010-10-13
just trying to help, and I don't feel any thing sucks about Ubuntu,, only thing that sucks is when we have to cater to windows needs..  And I appreciate your wisdom and apologize for my limited reading of the post, thank you..

---

### Post by bcbc on 2010-10-13
> **corcomp84 said:**
> just trying to help, and I don't feel any thing sucks about Ubuntu,, only thing that sucks is when we have to cater to windows needs..  And I appreciate your wisdom and apologize for my limited reading of the post, thank you..

Wubi caters to windows users who don't know how or can't create a new partition for Ubuntu - and also to users who don't know anything about Ubuntu and would be unwilling to go to the trouble of partitioning just to check it out. These users are likely the future ubuntu users who will be sharing how great it is with their friends and family. So, in my opinion, just dismissing wubi as a 'windows' aberration is not helpful. That is my opinion, but wubi is also fully-supported by Canonical - therefore I am clearly not alone in that opinion. So that's why I get a little touchy when you say it sucks.
BUT... perhaps I was a little harsh towards you - for that I apologize. So, let's give this thread back to the OP and leave the wubi debate for another time and place.

---

### Post by JohnyXD on 2010-10-13
I don't really mind since I have learned a few things too :P

---

