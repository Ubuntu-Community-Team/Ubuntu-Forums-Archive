---
title: "Dual Boot on system, Win 7 SP1 wont install...help"
date: 2011-02-23
forum: Installation &amp; Upgrades
---

### Post by M3rc Nate on 2011-02-23
So heres the thread i had a while back ( [http://ubuntuforums.org/showthread.php?t=1501977](http://ubuntuforums.org/showthread.php?t=1501977) ) that had you guys help me setup the pretty standard dual boot of Win 7 and Ubuntu. I have 2 hard drives, main one (640gig) and backup (80gb). I have Win7 installed on the 640 and ubuntu on the 80. 
 
So i have tried installing the SP1 twice today and it has failed. When i click on details on why it failed, it says: [http://windows.microsoft.com/en-US/windows7/windows-7-windows-server-2008-r2-service-pack-1-sp1-installation-error-0x800F0A12](http://windows.microsoft.com/en-US/windows7/windows-7-windows-server-2008-r2-service-pack-1-sp1-installation-error-0x800F0A12)
 
I can only imagine that this has to do with my Dual Boot. Is there anything i can do or am i stuck? I THINK that my grub and master boot and all that was on the second hard drive and it is the first drive in line to boot up...so i thought i wouldnt have any issues. Not totally sure though. 
 
Any advice or anything? Im tempted to just remove Ubuntu, its cool to say i have it, but i honestly havent loaded up onto it more than 5 times since i installed it. When you have windows already...its near impossible to want to get onto a free OS that doesnt have the codecs or programs and im not familiar with it. If it was all i had though, (aka didnt own Windows) then obviously it would be my main OS and im sure id love it and have is customized and perfect.

---

### Post by dkfroggy on 2011-02-23
For SP1 to install on multi boot machines, windows' system partition has to be active. So you have to set the boot flag to system (with gparted, for instance)

---

### Post by M3rc Nate on 2011-02-23
> **dkfroggy said:**
> For SP1 to install on multi boot machines, windows' system partition has to be active. So you have to set the boot flag to system (with gparted, for instance)
 
Im sorry im pretty noob at all this. I dont know exactly what you mean. Or how to do that (then undo it when i want it to go back to how its setup). :/

---

### Post by dkfroggy on 2011-02-23
[http://blogs.technet.com/b/joscon/archive/2011/02/17/windows-7-2008-r2-service-pack-1-fails-with-0x800f0a12.aspx](http://blogs.technet.com/b/joscon/archive/2011/02/17/windows-7-2008-r2-service-pack-1-fails-with-0x800f0a12.aspx)

---

### Post by M3rc Nate on 2011-02-23
> **dkfroggy said:**
> [http://blogs.technet.com/b/joscon/archive/2011/02/17/windows-7-2008-r2-service-pack-1-fails-with-0x800f0a12.aspx](http://blogs.technet.com/b/joscon/archive/2011/02/17/windows-7-2008-r2-service-pack-1-fails-with-0x800f0a12.aspx)
 
So it tells me to do these 2 things:
 
1.  Run DISKPART
2.  automount enable
 
But doesnt tell me HOW to do them. And if i need to undo what im doing after i have installed SP1 so the dual boot will be normal, and if i do, how do i do that?

---

### Post by dkfroggy on 2011-02-23
Bring me your computer and I'll fix it for you!!!

---

### Post by M3rc Nate on 2011-02-23
> **dkfroggy said:**
> Bring me your computer and I'll fix it for you!!!
 
I just googled it, lol you could have just told me to go into the Command Prompt and type diskpart then type automount enable ....
 
Just tripple checking, that is what i want to do in my specific dual boot case correct? Checking cause the original site you linked, wasnt very specific on it being applied to dualboot PC's.

---

### Post by dkfroggy on 2011-02-23
Yes, I could have. But I didn't. Maybe because you stop reading after 5 lines? 
You should read the **entire** post linked above, comments included.

---

### Post by oldfred on 2011-02-23
When you installed the dual boot before, I think you had the windows boot partition on one drive and the main windows install on the other. Did we end up overwriting the boot partition, but still have the main install on the other drive? 

Any repairs to windows have to have the partition to repair active. We see it as a boot flag(*) in fdisk. As posted above you can do it from windows, or you can use gparted.

All of the repairs are to the active partition. If multiple installs of windows you have to move boot flag to repair the other install.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

---

### Post by M3rc Nate on 2011-02-23
> **oldfred said:**
> When you installed the dual boot before, I think you had the windows boot partition on one drive and the main windows install on the other. Did we end up overwriting the boot partition, but still have the main install on the other drive? 
 
Any repairs to windows have to have the partition to repair active. We see it as a boot flag(*) in fdisk. As posted above you can do it from windows, or you can use gparted.
 
All of the repairs are to the active partition. If multiple installs of windows you have to move boot flag to repair the other install.
 
How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)
 
Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixMBR #updates MBR master boot record do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
 
I _think_ so, if i remember right, my 640Gb has Windows 7 OS on it, but the 80Gb has Ubuntu, the Grub and all the bootloaders. And then i have my Bios setup so the priority boot is the 80Gb, so the 80Gb boots, i see the Grub and choose whether to boot into Ubuntu or Win7. 
 
I think what i want to do is have my 640Gb HDD have windows 7 _fully_ on it. MBR and all. I want my 80Gb to have Ubuntu on it, but not have dual boot. It will have Ubuntu on it, but as its on OS on its own drive. Does that make sense? Essentially i want a normal windows 7 computer, with a secondary hard drive that has the full ubuntu OS installed on it, but the only way to load it up and boot into Ubuntu is go into the bios, change the boot priority to my 80Gb and when it restarts, it boots _directly_ into Ubuntu. No grub, no dual boot. 
How do i do that?

---

### Post by oldfred on 2011-02-23
post boot script so we know where you are at currently.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by M3rc Nate on 2011-02-23
```
                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

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

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848 1,250,260,991 1,250,054,144   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048    29,296,639    29,294,592  83 Linux
/dev/sdb2          29,298,686   156,301,311   127,002,626   5 Extended
/dev/sdb5         152,395,776   156,301,311     3,905,536  82 Linux swap / Solaris
/dev/sdb6          29,298,688   152,393,727   123,095,040  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        38F08276F0823A60                       ntfs       System Reserved               
/dev/sda2        9EDCA32FDCA3011F                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5a41234b-ae62-4a6c-8457-a7acda80ac5d   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        58fff04a-da5d-4cde-8411-56d2f46ff1a2   swap                                     
/dev/sdb6        ca58785e-478d-4c8a-bf77-2aaf849c79bb   ext4                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sdb6        /home                    ext4       (rw)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 5a41234b-ae62-4a6c-8457-a7acda80ac5d
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 5a41234b-ae62-4a6c-8457-a7acda80ac5d
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
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 5a41234b-ae62-4a6c-8457-a7acda80ac5d
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=5a41234b-ae62-4a6c-8457-a7acda80ac5d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 5a41234b-ae62-4a6c-8457-a7acda80ac5d
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=5a41234b-ae62-4a6c-8457-a7acda80ac5d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 5a41234b-ae62-4a6c-8457-a7acda80ac5d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 5a41234b-ae62-4a6c-8457-a7acda80ac5d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 38f08276f0823a60
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb6 during installation
UUID=ca58785e-478d-4c8a-bf77-2aaf849c79bb /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=58fff04a-da5d-4cde-8411-56d2f46ff1a2 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  11.4GB: boot/grub/core.img
  11.4GB: boot/grub/grub.cfg
  11.4GB: boot/initrd.img-2.6.32-21-generic
  11.4GB: boot/vmlinuz-2.6.32-21-generic
  11.4GB: initrd.img
  11.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  73 5b ea 53 e3 f5 42 51  79 7e 01 e2 e5 6a ea de  |s[.S..BQy~...j..|
00000010  95 fe 05 1a 9e 5e 31 ef  fa 7f 12 0a c0 3c b8 1a  |.....^1......<..|
00000020  80 6f bd 9e 08 6a d5 4d  69 56 2a 18 1b 53 c3 23  |.o...j.MiV*..S.#|
00000030  28 70 da 70 ca 92 ff d0  3c 5d 64 50 22 7d 98 05  |(p.p....<]dP"}..|
00000040  b5 92 45 0d 8e d8 30 71  1c f2 a7 36 68 6a 64 3e  |..E...0q...6hjd>|
00000050  56 ea e3 20 46 0b b8 cf  3e 78 97 b4 fd 7d 8a 0c  |V.. F...>x...}..|
00000060  16 a9 e2 21 60 f9 ab aa  76 12 9c 02 7f 8b dd 71  |...!`...v......q|
00000070  14 ea 95 aa de 28 d9 1f  10 45 a1 31 11 2b ea da  |.....(...E.1.+..|
00000080  fc 59 a1 5e 28 99 8b 9f  5a cd c7 80 4c 17 30 10  |.Y.^(...Z...L.0.|
00000090  ae 83 6b 65 f7 0a a3 0d  75 60 d9 c2 10 61 0c 10  |..ke....u`...a..|
000000a0  3e 01 a0 8b 78 b3 59 4b  09 14 43 82 44 c9 31 4f  |>...x.YK..C.D.1O|
000000b0  f7 88 38 53 c7 2a 3d 12  a0 22 69 b1 6f d0 a8 6c  |..8S.*=.."i.o..l|
000000c0  18 15 5d 6b 78 8f ed 88  34 da d2 1e 3b a3 78 bc  |..]kx...4...;.x.|
000000d0  e0 bc e2 d9 e6 b3 8e 70  14 ca 20 e0 28 be a4 1c  |.......p.. .(...|
000000e0  c1 82 f2 e1 15 7c 61 38  63 04 bf c2 e5 43 a2 23  |.....|a8c....C.#|
000000f0  07 c1 cb 45 30 e1 a9 e7  e3 cc c1 17 ba 0c 63 e5  |...E0.........c.|
00000100  cd e7 d9 11 5c e5 6a bd  b1 72 70 29 86 11 1d 18  |....\.j..rp)....|
00000110  59 7f ac 87 41 8b 81 e0  3f b5 aa c1 81 04 bb c1  |Y...A...?.......|
00000120  03 91 45 f6 b3 63 30 02  07 f4 7e 0a 2f cb d9 10  |..E..c0...~./...|
00000130  c0 62 20 61 28 14 34 10  c7 45 d7 e0 7d 56 ea 64  |.b a(.4..E..}V.d|
00000140  64 20 a3 a3 ef 5a 5d 00  e8 29 21 2f 3b 02 e0 15  |d ...Z]..)!/;...|
00000150  ea c7 08 23 5c d1 6a 7c  22 6d ce 3e 3f 3a 06 c1  |...#\.j|"m.>?:..|
00000160  a4 3c 2e 05 3a 56 98 44  a6 95 d3 59 11 d1 a0 57  |.<..:V.D...Y...W|
00000170  08 4d 62 b2 f9 1a 06 1b  26 0f 1a 84 98 84 67 4e  |.Mb.....&.....gN|
00000180  91 03 9c 69 81 fa 51 16  64 63 c0 c3 34 7c 13 10  |...i..Q.dc..4|..|
00000190  06 c6 33 cc 29 e2 f5 71  aa 97 62 dd 42 f6 6e ae  |..3.)..q..b.B.n.|
000001a0  78 02 60 55 60 19 6c 8a  16 dc b9 72 c4 16 1d 1b  |x.`U`.l....r....|
000001b0  83 01 c0 6b 83 b1 2b 07  3b 0b 73 9e 6e 21 00 fe  |...k..+.;.s.n!..|
000001c0  ff ff 82 fe ff ff 02 50  56 07 00 98 3b 00 00 fe  |.......PV...;...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 48 56 07 00 00  |...........HV...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

 
```

---

### Post by oldfred on 2011-02-23
It looks like what you want. All your windows files & MBR are on sda, and Ubuntu & grub's boot loader are on sdb.

If you use BIOS to boot sda you should only get windows. If you use BIOS to boot the 80GB drive you should get grub and a menu to boot either.

If you want to not use grub's menu to choose which to boot you can set the default to Ubuntu (which it normally is) and set timeout to almost 0. Those who set to 0 seem not to be able to get back into menu ever to fix things, except from liveCD.

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)
Download and install "StartUp-Manager from Synaptic package downloads. It will be listed under System/Administration menu. You can set it to default with Ubuntu (different versions) or Windows. You can also set the start up time in seconds.
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)
HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)


Grub 2 Title Tweaks
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

drs305's hack to get hidden timeout to work:
[http://ubuntuforums.org/showthread.php?t=1319672](http://ubuntuforums.org/showthread.php?t=1319672)

---

### Post by M3rc Nate on 2011-02-23
> **oldfred said:**
> It looks like what you want. All your windows files & MBR are on sda, and Ubuntu & grub's boot loader are on sdb.

If you use BIOS to boot sda you should only get windows. If you use BIOS to boot the 80GB drive you should get grub and a menu to boot either.

If you want to not use grub's menu to choose which to boot you can set the default to Ubuntu (which it normally is) and set timeout to almost 0. Those who set to 0 seem not to be able to get back into menu ever to fix things, except from liveCD.

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)
Download and install "StartUp-Manager from Synaptic package downloads. It will be listed under System/Administration menu. You can set it to default with Ubuntu (different versions) or Windows. You can also set the start up time in seconds.
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)
HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)


Grub 2 Title Tweaks
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

drs305's hack to get hidden timeout to work:
[http://ubuntuforums.org/showthread.php?t=1319672](http://ubuntuforums.org/showthread.php?t=1319672)

Thanks! So if i set it up in the bios to have my 640Gb be first boot priority and when i turn on PC it goes automatically to Windows 7, will the SP1 install correctly?
Second question, can i adjust the countdown time amount and which OS is automatically chosen?

---

### Post by oldfred on 2011-02-23
Windows has its own settings which I know nothing about (except XP). Windows will not see the partitions that are Linux based. It may see the drive but say it is empty. I would expect windows to see the install, but again those are windows issues.

Settings for grub2 are in:
/etc/default/grub - the file containing GRUB 2 menu settings.

Manual editing & various gui tools posted above.

---

### Post by M3rc Nate on 2011-02-23
> **oldfred said:**
> Windows has its own settings which I know nothing about (except XP). Windows will not see the partitions that are Linux based. It may see the drive but say it is empty. I would expect windows to see the install, but again those are windows issues.

Settings for grub2 are in:
/etc/default/grub - the file containing GRUB 2 menu settings.

Manual editing & various gui tools posted above.

Well i havent messed with the editing and tools yet. But i did change the boot priority so it booted first from my 640Gb HDD (windows 7 OS) and tried the SP1 install and it worked perfectly. Problem solved. Interested note, i hadnt been on my 10.04 Ubuntu probably since october, so when on it doing what you asked, there was like a list of 100 things that needed updating, and now when i get to the boot menu (where i choose Windows 7 or Ubuntu or Memtest) now there are 4 Ubuntu options, two with safe modes and two without, them having different numbers by them. Not sure if the update that ran and installed had installed the new ubuntu that was released or not. But something updated and changed stuff a bit.

---

### Post by wilee-nilee on 2011-02-23
> **M3rc Nate said:**
> Well i havent messed with the editing and tools yet. But i did change the boot priority so it booted first from my 640Gb HDD (windows 7 OS) and tried the SP1 install and it worked perfectly. Problem solved. Interested note, i hadnt been on my 10.04 Ubuntu probably since october, so when on it doing what you asked, there was like a list of 100 things that needed updating, and now when i get to the boot menu (where i choose Windows 7 or Ubuntu or Memtest) now there are 4 Ubuntu options, two with safe modes and two without, them having different numbers by them. Not sure if the update that ran and installed had installed the new ubuntu that was released or not. But something updated and changed stuff a bit.

The extras in the grub menu are a additional kernel update perfectly normal. Listed differently then you describe the kernel lines that are recovery are every other correct. They are kernel sets notice the same numbers.

---

