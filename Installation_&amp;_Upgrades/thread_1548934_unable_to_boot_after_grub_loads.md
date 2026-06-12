---
title: "unable to boot after grub loads"
date: 2010-08-09
forum: Installation &amp; Upgrades
---

### Post by konig85 on 2010-08-09
Hi Im a noob with linux so if anyone has a solution or suggestion it wud help if you give exact instructions.

The problem is I've set up a dual boot with Xp and Ubuntu 10.04. Ubuntu was  working fine till 2 days back but now when I select Ubuntu from the grub screen i get a whole lot of numbers next which it'll say Usb drive or sd card reader etc.. these go by quickly and then the comp stops running. If i press enter on the keyboard I get  Initramfs and then i can type but nothing happens even if I type reboot. if I press cntrl+alt+F2 then i get a blank screen with flashing cursor. Same with recovery mode. Windows boots fine. The grub2 screen comes fine. The last thing i did before this happened is reconfigure the grub2 screen, but it seems to be fine (i had added a background img and reordered the boot options) I did not edit grub.cfg. Any help would be appreciated.. I would prefer not to reinstall it as iv done it a half a dozen times already in  the last few weeks..

---

### Post by vitothegreat on 2010-08-09
Since 9.10 there have already been billions of similar threads about grub not working with dual-boot. You can use 'search' and spend the rest of your life reading those threads and trying to find the answer or you can just use EasyBCD. It's extremely easy to use and doesn't require any technical knowledge so you should be fine.

---

### Post by ajgreeny on 2010-08-09
I would steer clear of easybcd from what others have said about it and try to get grub back.  Can you boot the live CDand then download and run the boot_info_script from meierfra, which is extremely useful in sorting out the reasons for the problem.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by konig85 on 2010-08-09
@vitothegreat 

was trying easybcd but it cant find the boot file.. and anyway grub screen comes its after selecting ubuntu the problem arises..

@ajgreeny iv run the boot info script am pasting the results below hope u find the reason.

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdg

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63. According to the info in the boot 
                       sector, sda5 has 159426288 sectors, but according to 
                       the info from fdisk, it has 163252529 sectors.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Boot file info:     Grub 2 in the file /super_grub_disk_hybrid-1.98s1.iso 
                       looks at sector 1 of the same hard drive for core.img, 
                       but core.img can not be found at this location.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdg1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *    543,784,960   976,766,975   432,982,016   7 HPFS/NTFS
/dev/sda2              15,181   543,775,679   543,760,499   f W95 Ext d (LBA)
/dev/sda5              15,183   163,267,712   163,252,530   7 HPFS/NTFS
/dev/sda6         440,944,623   543,775,679   102,831,057   7 HPFS/NTFS
/dev/sda7         163,268,608   429,576,191   266,307,584  83 Linux
/dev/sda8         429,578,240   440,936,447    11,358,208  82 Linux swap / Solaris


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 1023 MB, 1023409664 bytes
255 heads, 63 sectors/track, 124 cylinders, total 1998847 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg1    *             63     1,998,846     1,998,784   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        A690278F902764D1                       ntfs       Entertainment                 
/dev/sda2: PTTYPE="dos" 
/dev/sda5        CEA8FDD7A8FDBDD1                       ntfs                                     
/dev/sda6        01CB32F2FC329940                       ntfs       Backup                        
/dev/sda7        f6863e7e-2a26-4ccc-8595-c2d253fbe72c   ext4                                     
/dev/sda8        ac06c408-08fa-495a-996e-ec24c45baf9f   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdg1        9CC0-17D1                              vfat                                     
/dev/sdg: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdg1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

================================ sda5/boot.ini: ================================

[boot loader] 
timeout= 
[operating systems] 

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
set default="4"
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
set root='(hd0,7)'
search --no-floppy --fs-uuid --set f6863e7e-2a26-4ccc-8595-c2d253fbe72c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768s
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,7)'
search --no-floppy --fs-uuid --set f6863e7e-2a26-4ccc-8595-c2d253fbe72c
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
insmod ext2
set root='(hd0,7)'
search --no-floppy --fs-uuid --set f6863e7e-2a26-4ccc-8595-c2d253fbe72c
insmod tga
if background_image /boot/grub/Windbuchencom.tga ; then
  set color_normal=blue/black
  set color_highlight=light-cyan/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set f6863e7e-2a26-4ccc-8595-c2d253fbe72c
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=f6863e7e-2a26-4ccc-8595-c2d253fbe72c ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set f6863e7e-2a26-4ccc-8595-c2d253fbe72c
    echo    'Loading Linux 2.6.32-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=f6863e7e-2a26-4ccc-8595-c2d253fbe72c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set f6863e7e-2a26-4ccc-8595-c2d253fbe72c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set f6863e7e-2a26-4ccc-8595-c2d253fbe72c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set a690278f902764d1
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

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
# / was on /dev/sda7 during installation
UUID=f6863e7e-2a26-4ccc-8595-c2d253fbe72c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=ac06c408-08fa-495a-996e-ec24c45baf9f none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


  92.3GB: boot/grub/core.img
  92.4GB: boot/grub/grub.cfg
  92.4GB: boot/initrd.img-2.6.32-24-generic-pae
  92.3GB: boot/vmlinuz-2.6.32-24-generic-pae
  92.4GB: initrd.img
  92.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  a0 4e f0 ae 4c bb 44 8a  9e b4 3c 82 03 97 38 81  |.N..L.D...<...8.|
00000010  a2 ad 9a a2 03 47 14 12  3b 8c 4b a8 9e ba 06 20  |.....G..;.K.... |
00000020  84 ec a5 18 ef e6 de d7  f2 91 0e 8e 3f ca c0 36  |............?..6|
00000030  70 49 ce aa 51 34 9d 5f  93 84 82 e0 02 da 52 53  |pI..Q4._......RS|
00000040  5c b1 2d 7f 73 69 c9 da  ab ce 7a bf c1 71 23 e8  |\.-.si....z..q#.|
00000050  4d ba a5 b6 90 35 4a c0  ce ca 32 d0 84 60 55 bc  |M....5J...2..`U.|
00000060  df e7 a0 db a8 3d f5 7e  76 c7 68 7f 80 60 eb 44  |.....=.~v.h..`.D|
00000070  28 bf d2 8d d5 d0 5c b0  65 5c dc f8 3a e7 b5 f3  |(.....\.e\..:...|
00000080  78 98 61 ba 91 4e 25 ce  b5 59 44 ad 8d a7 01 29  |x.a..N%..YD....)|
00000090  9b 78 9c 2a 00 a2 e2 f9  f3 cf 6f b2 db 18 5a 03  |.x.*......o...Z.|
000000a0  d8 a4 39 f0 b1 dd a8 41  60 63 f5 27 56 c6 a1 e8  |..9....A`c.'V...|
000000b0  35 a5 b9 ed 7c 8d d2 31  f2 69 a8 e4 c6 a2 f5 f4  |5...|..1.i......|
000000c0  61 03 8f 98 6a 3e 6a 78  38 0e 18 e4 05 0a 3f b9  |a...j>jx8.....?.|
000000d0  57 a3 ec 02 f4 9f f2 10  43 2c ee 9b d5 af 47 9f  |W.......C,....G.|
000000e0  c9 d9 b5 47 cc ac 41 61  dd 03 af ad a4 ea 20 a1  |...G..Aa...... .|
000000f0  a9 84 3f 76 13 52 f9 12  f6 fc 4c 50 56 f6 a3 9e  |..?v.R....LPV...|
00000100  4b 84 1e e3 bd a8 8f e1  8c 8a bc 72 01 00 e9 fc  |K..........r....|
00000110  25 40 35 55 8a b8 30 80  a8 c9 c6 ce 57 68 46 db  |%@5U..0.....WhF.|
00000120  41 7b 17 80 9a 37 3a 7e  6d 75 25 fb a6 97 12 ad  |A{...7:~mu%.....|
00000130  d1 5b 9e 2a ed 22 99 5a  77 03 bf cb a2 07 15 41  |.[.*.".Zw......A|
00000140  80 fd c2 61 b9 74 94 a9  4c b5 81 6b bb 30 f1 f9  |...a.t..L..k.0..|
00000150  d4 82 d3 e4 14 65 2a 3e  43 78 1b 93 71 ea b0 11  |.....e*>Cx..q...|
00000160  b1 99 a6 19 74 4e b9 ac  d7 9c 53 a2 3b 54 5a e2  |....tN....S.;TZ.|
00000170  de ff 17 ac 8c 8c 91 be  02 4a 95 8d 40 8a 49 c8  |.........J..@.I.|
00000180  48 7f 11 32 de 4e 4c 63  89 77 87 96 29 c2 46 4f  |H..2.NLc.w..).FO|
00000190  c2 5e 9b 57 bc c2 f5 fc  cb 72 e9 90 2b f5 82 ac  |.^.W.....r..+...|
000001a0  f1 cc 0c 6e ad a9 fc 2f  b6 67 7d 28 d8 72 1a fb  |...n.../.g}(.r..|
000001b0  62 b5 4b 3a f5 ff 4f 60  48 15 50 4d 64 94 00 01  |b.K:..O`H.PMd...|
000001c0  01 01 07 1e ff ff 02 00  00 00 32 09 bb 09 00 fe  |..........2.....|
000001d0  ff ff 05 fe ff ff b3 ec  47 1a c0 33 21 06 00 00  |........G..3!...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde sdf

---

### Post by vitothegreat on 2010-08-09
> **ajgreeny said:**
> I would steer clear of easybcd from what others have said about it

Interesting, I've been using it for quite some time and didn't have any problems at all.
Could you be more specific about it?

---

### Post by ajgreeny on 2010-08-09
> **vitothegreat said:**
> Interesting, I've been using it for quite some time and didn't have any problems at all.
Could you be more specific about it?
Not really, I'm afraid; I say that having never used it, but having read comments from those who have and found it not easy to use, and did not solve their problem.

However, I also say it having never had a grub problem, legacy or grub2, that did not sort itself very easily and quickly after a forum search and a couple or so terminal commands.

@OP
When you changed the boot order, what did you do, and can you change it back again to the way it was?  Grub is on sda so that needs to be first in your device boot order to get to the grub config files on sda7. Or do you mean that you tried to get windows to boot as default?

---

### Post by konig85 on 2010-08-09
what i meant by changing the boot order is that i got windows to load first.. i had edited  40_custom file.. and no i dont think i can change it now as i cant start ubuntu unless its possible to change it using the live cd...

---

### Post by oldfred on 2010-08-09
It seems like grub is working and it is Ubuntu that is not. Windows boots, Ubuntu starts booting.

From grub menu, use e for edit and remove the quiet splash. You will see all the numbers which should be times as it load modules, boots. What is important is what is on the screen as it stops. The last commands should be the one's that are not working. Error messages, repeating attempts to load a driver, or extremely long time between entries.

You should also be able to view log files from live CD. The will be in /var/log for whatever the mount point is for you system not the liveCD. 
/media/?/var/log. The end of the log files may have the error messages or timeout of something that does not load correctly. I would look at messages or kernel first but I look at any that have current update.

---

### Post by Computer Guru on 2010-08-09
> **ajgreeny said:**
> Not really, I'm afraid; I say that having never used it, but having read comments from those who have and found it not easy to use, and did not solve their problem.

That's true enough - there was a period of time after Ubuntu 9 and before EasyBCD 1.7.2 when EasyBCD didn't support the uuid method used in the GRUB files and again after Ubuntu 10 and before EasyBCD 2.x when EasyBCD didn't support GRUB2. 

But now EasyBCD has full support for the latest Ubuntu: [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

However, there is still a remaining issue with the Grub4Dos components wherein users get a "Try (HDx,y)" message under certain weird hardware configurations / partition formattings that trigger a Grub4Dos bug, I've contacted the authors of G4D about this several times and hope to hear back from them soon.

---

