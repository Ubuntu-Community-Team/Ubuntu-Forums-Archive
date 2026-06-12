---
title: "Installing Ubuntu in a separate partition"
date: 2011-03-12
forum: Installation &amp; Upgrades
---

### Post by maxmiaggi on 2011-03-12
Hello everyone. I am a newbie.

I want to install ubuntu 10.10 in a separate partition. I use windows 7 home premium.

Here is my disk allocation profile:
C:\ 288GB
F:\ (Recovery Drive) 12GB

I shrunk the volume of C:\ to 160GB. Hence, 120GB remains unallocated now. C:\ and F:\ are primary partitions. When i create a new volume for the unallocated region, it creates an extended partition (logical drive). I guess OS can be installed only in primary drives.

Next, I dont want this F:\ and i am not able to remove it. While installing ubuntu, when i go for choosing partitions manually, i am confused regarding the drive to choose (sda, sda1, sda2, sda3, ?????).  Upon choosing any of them, it shows root file system not found.

Please help me...

---

### Post by srs5694 on 2011-03-12
> **maxmiaggi said:**
> I shrunk the volume of C:\ to 160GB. Hence, 120GB remains unallocated now. C:\ and F:\ are primary partitions. When i create a new volume for the unallocated region, it creates an extended partition (logical drive). I guess OS can be installed only in primary drives.

*Windows* must be installed to a primary partition. Linux isn't so limited; it's happy to reside in a logical partition.

That said, it's generally best to create partitions for an OS using that OS's installer or other utility in the OS in question. Thus, I'd just leave the unpartitioned space there, launch the Ubuntu installer, and create the Ubuntu partitions in the Ubuntu installer. I recommend doing a manual partitioning and creating three or four partitions:


[list]
[*]**root (/)** -- This is the main Linux partition, which holds the OS an almost everything else that's not given an explicit separate partition. Make it 5-20 GiB in size, depending on how much disk space you've got and how complete an installation you want.
[*]**swap** -- This is a partition that serves as an adjunct to RAM. Make it 1-2 times the size of your computer's RAM. Chances are everything will be fine if you make it smaller than this, except that you won't be able to use the suspend-to-disk (aka hibernate) function.
[*]**/home** -- This directory holds your user files. It should take up your remaining space, unless you also create the next partition, in which case you should split the remaining space between them in whatever way seems most reasonable to you.
[*]**A shared-data partition** -- This is a FAT or NTFS partition you use for files you want to access from both Linux and Windows. This is desirable because writing to the Windows C: partition from Linux is at least slightly dangerous. You can mount this partition wherever you like, so long as it's not a standard Linux directory. If you're unsure, use /mnt/windows (you'll probably have to type this as a custom mount point rather than select it as a standard option).
[/list]


> Next, I dont want this F:\ and i am not able to remove it.

I'm not positive, but I suspect that partition serves as your Windows installation medium. Thus, if you delete it and your Windows installation goes completely haywire, you won't be able to recover except by purchasing a new copy of Windows or by buying a set of recovery DVDs from your computer manufacturer. If I'm right, your computer probably has a pre-installed utility to burn a set of recovery DVDs, and if you run that utility, it will then be safe to delete that partition. You should do more research to verify this partition is what I think it is, though.

As to deleting it, you can do this from the Ubuntu installer.

> While installing ubuntu, when i go for choosing partitions manually, i am confused regarding the drive to choose (sda, sda1, sda2, sda3, ?????).  Upon choosing any of them, it shows root file system not found.

If you do as I advise and leave the space for Ubuntu unpartitioned when you start the installer, then you should be able to select the free space, click "Add" to add a partition, specify its mount point and other options, and repeat that process for each partition. I don't recall offhand whether you need to explicitly create a separate extended partition when you create logicals, but if so, I'd do that first and put Ubuntu entirely within logical partitions inside the extended partition.

---

### Post by maxmiaggi on 2011-03-13
Thanks a lot. I did as you said. Ubuntu got installed, but during boot-up, even though it boots from the hard-drive, it isnt able to recognise ubuntu. Windows starts up. It doesnt even pop up a choice for windows/ubuntu.

---

### Post by oldfred on 2011-03-13
If you used manual install it gives a choice on where to install grub's boot loader. Did you not install it to the MBR of your boot drive?

So we can see exactly where you are at:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by maxmiaggi on 2011-03-19
@oldfred: Here is what you have asked for... now what to do??

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda7 and 
                       looks at sector 482443456 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       401,624       401,562  de Dell Utility
/dev/sda2    *        403,456    19,531,916    19,128,461   7 HPFS/NTFS
/dev/sda3          19,535,872   369,535,871   350,000,000   7 HPFS/NTFS
/dev/sda4         369,539,070   625,141,759   255,602,690   f W95 Ext d (LBA)
/dev/sda5         369,539,072   449,357,431    79,818,360   7 HPFS/NTFS
/dev/sda6         449,357,824   461,078,527    11,720,704  82 Linux swap / Solaris
/dev/sda7         461,080,576   500,140,031    39,059,456  83 Linux
/dev/sda8         500,142,080   625,141,759   124,999,680  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4041 MB, 4041211904 bytes
128 heads, 63 sectors/track, 978 cylinders, total 7892992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     7,892,991     7,892,929   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        07DA-0111                              vfat       DellUtility                   
/dev/sda2        B0FCF691FCF65158                       ntfs       RECOVERY                      
/dev/sda3        F69AFAC19AFA7E05                       ntfs       THE GREAT MAX                 
/dev/sda4: PTTYPE="dos" 
/dev/sda5        40AEB084AEB0744E                       ntfs       New Volume                    
/dev/sda6        a1e31a67-53b4-47be-9387-d1ec7d9b29b4   swap                                     
/dev/sda7        a4793dbc-0c5d-482a-9b0f-b1e3445a42e2   ext4                                     
/dev/sda8        7c4e77f2-5632-4e19-83a5-a446fcd33d63   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        DE73-B1E1                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set a4793dbc-0c5d-482a-9b0f-b1e3445a42e2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set a4793dbc-0c5d-482a-9b0f-b1e3445a42e2
set locale_dir=($root)/boot/grub/locale
set lang=en
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set a4793dbc-0c5d-482a-9b0f-b1e3445a42e2
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=a4793dbc-0c5d-482a-9b0f-b1e3445a42e2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set a4793dbc-0c5d-482a-9b0f-b1e3445a42e2
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=a4793dbc-0c5d-482a-9b0f-b1e3445a42e2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set a4793dbc-0c5d-482a-9b0f-b1e3445a42e2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set a4793dbc-0c5d-482a-9b0f-b1e3445a42e2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set b0fcf691fcf65158
    chainloader +1
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
UUID=a4793dbc-0c5d-482a-9b0f-b1e3445a42e2 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda8 during installation
UUID=7c4e77f2-5632-4e19-83a5-a446fcd33d63 /home           ext4    defaults        0       2
# /mnt/windows was on /dev/sda5 during installation
UUID=40AEB084AEB0744E /mnt/windows    ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda6 during installation
UUID=a1e31a67-53b4-47be-9387-d1ec7d9b29b4 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 247.0GB: boot/grub/core.img
 251.3GB: boot/grub/grub.cfg
 245.2GB: boot/initrd.img-2.6.35-22-generic
 247.0GB: boot/vmlinuz-2.6.35-22-generic
 245.2GB: initrd.img
 247.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  42 fc 11 e7 e7 5c 90 48  ee d7 5b 29 8c 93 56 5e  |B....\.H..[)..V^|
00000010  0a 9e 44 0f 47 6b 57 1b  ca 9a 33 42 06 08 3c 74  |..D.GkW...3B..<t|
00000020  26 ac 51 28 24 45 93 f3  3c ed 26 c2 28 41 9f 3c  |&.Q($E..<.&.(A.<|
00000030  a8 2a 61 73 e3 14 d0 bd  af b7 3f 4a ba af 61 48  |.*as......?J..aH|
00000040  02 a7 42 58 03 7d 90 b5  01 43 d4 37 65 35 44 70  |..BX.}...C.7e5Dp|
00000050  01 dd 67 af ae d1 11 0d  8e d8 60 0b dd d4 18 34  |..g.......`....4|
00000060  bf 39 ba 3b 5e 97 4b bf  ff a5 85 3e 8d 95 35 99  |.9.;^.K....>..5.|
00000070  6b 9c db 13 f7 aa 13 b2  99 a8 fa 65 c1 b9 70 7a  |k..........e..pz|
00000080  20 a7 d7 3d a8 8c e0 86  33 79 ce ff 3b 11 3a 7d  | ..=....3y..;.:}|
00000090  28 74 bf e0 b2 7b 87 56  84 67 e8 79 fd fd 77 b6  |(t...{.V.g.y..w.|
000000a0  c7 04 cf 10 2f c9 85 c2  5d ec 22 4a 3e c7 02 68  |..../...]."J>..h|
000000b0  82 16 ba ed 0a e3 7c 18  fb 8b e2 95 82 6c 17 c4  |......|......l..|
000000c0  d6 b2 4d 44 70 36 05 90  7c fa 36 ba 9d 80 7b 53  |..MDp6..|.6...{S|
000000d0  f5 87 d9 e2 03 74 5e ff  7c 90 cd 0d a2 93 2d ca  |.....t^.|.....-.|
000000e0  4e 9f 42 c8 e1 61 f2 7c  df cc 0d 09 a4 56 87 2f  |N.B..a.|.....V./|
000000f0  65 83 73 35 31 c0 f9 d9  a9 95 72 7c 56 9f 3e fc  |e.s51.....r|V.>.|
00000100  ca c4 f2 a2 e9 b8 67 87  68 8c 8b 87 2a 55 30 3f  |......g.h...*U0?|
00000110  a1 fb 60 1c 75 9e e6 dd  c7 87 19 77 df e5 6f e4  |..`.u......w..o.|
00000120  44 7e b1 09 17 1c a8 65  30 65 a6 96 de a4 43 f3  |D~.....e0e....C.|
00000130  4c b4 a8 32 60 c6 2e 16  d5 74 9d 5f f6 a9 50 f2  |L..2`....t._..P.|
00000140  46 4b f5 b9 89 8f b0 1b  dd a9 94 b7 5e 71 0c 54  |FK..........^q.T|
00000150  6e cb bc 5d 1a 8c ec 25  48 ef 14 ae 70 9c a0 52  |n..]...%H...p..R|
00000160  af e4 db 5e 61 d1 56 95  44 b4 8c f3 4a d2 80 c4  |...^a.V.D...J...|
00000170  e7 96 1c fa 7a e9 f8 bb  e1 d1 b4 bb c3 a9 35 72  |....z.........5r|
00000180  56 e7 fc 12 91 ec 95 67  1a 8b de 87 f9 9b 96 d6  |V......g........|
00000190  e6 4c 13 36 c2 95 9c 75  76 df a3 3b f0 12 42 67  |.L.6...uv..;..Bg|
000001a0  ad 5d 7d 2d d3 9d 2b 19  1a 7d 01 4f 7e 94 01 08  |.]}-..+..}.O~...|
000001b0  d6 cd ed 26 21 20 86 50  0d cf a5 7a 09 f0 00 fe  |...&! .P...z....|
000001c0  ff ff 07 fe ff ff 02 00  00 00 78 ee c1 04 00 fe  |..........x.....|
000001d0  ff ff 05 fe ff ff 7a ee  c1 04 88 d9 b2 00 00 00  |......z.........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 e8 03  |.X.SYSLINUX.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  c1 6f 78 00 0c 1e 00 00  00 00 00 00 02 00 00 00  |.ox.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 e1 b1 73 de 4e  4f 20 4e 41 4d 45 20 20  |..)..s.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 08  40 00 00 66 ba 00 00 00  |..E}.f..@..f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by oldfred on 2011-03-20
You installed grub2 bootloader to the partition with Ubuntu - sda7, not the MBR - sda. You need to install grub to the MBR of drive sda.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda7 and want grub2 in drive sda's MBR:
#Find linux partition, change sda7 if not correct:
sudo fdisk -l
#confirm that linux is sda7
sudo mount /dev/sda7 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# After rebooting into working system
sudo update-grub

#More info here
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by maxmiaggi on 2011-03-21
@oldfred:

thanks a lot for the help. I did as you instructed. Here is an updated version of boot info script. Please have a look at it. It says that I have 8 partitions, sda1 to sda8. But when I go to Places>Computer, I am able to see only two partitions, one in which windows is installed, and the other one labelled 'File System', in which i guess linux is installed. What about the other partitions?

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda7 and 
                       looks at sector 482443456 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       401,624       401,562  de Dell Utility
/dev/sda2    *        403,456    19,531,916    19,128,461   7 HPFS/NTFS
/dev/sda3          19,535,872   369,535,871   350,000,000   7 HPFS/NTFS
/dev/sda4         369,539,070   625,141,759   255,602,690   f W95 Ext d (LBA)
/dev/sda5         369,539,072   449,357,431    79,818,360   7 HPFS/NTFS
/dev/sda6         449,357,824   461,078,527    11,720,704  82 Linux swap / Solaris
/dev/sda7         461,080,576   500,140,031    39,059,456  83 Linux
/dev/sda8         500,142,080   625,141,759   124,999,680  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07DA-0111                              vfat       DellUtility                   
/dev/sda2        B0FCF691FCF65158                       ntfs       RECOVERY                      
/dev/sda3        F69AFAC19AFA7E05                       ntfs       THE GREAT MAX                 
/dev/sda4: PTTYPE="dos" 
/dev/sda5        40AEB084AEB0744E                       ntfs       New Volume                    
/dev/sda6        a1e31a67-53b4-47be-9387-d1ec7d9b29b4   swap                                     
/dev/sda7        a4793dbc-0c5d-482a-9b0f-b1e3445a42e2   ext4                                     
/dev/sda8        7c4e77f2-5632-4e19-83a5-a446fcd33d63   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=600)
/dev/sda5        /mnt/windows             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda8        /home                    ext4       (rw,commit=600)
/dev/sda3        /media/THE GREAT MAX     fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set a4793dbc-0c5d-482a-9b0f-b1e3445a42e2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set a4793dbc-0c5d-482a-9b0f-b1e3445a42e2
set locale_dir=($root)/boot/grub/locale
set lang=en
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
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set a4793dbc-0c5d-482a-9b0f-b1e3445a42e2
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=a4793dbc-0c5d-482a-9b0f-b1e3445a42e2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set a4793dbc-0c5d-482a-9b0f-b1e3445a42e2
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=a4793dbc-0c5d-482a-9b0f-b1e3445a42e2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set a4793dbc-0c5d-482a-9b0f-b1e3445a42e2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set a4793dbc-0c5d-482a-9b0f-b1e3445a42e2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set b0fcf691fcf65158
    chainloader +1
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
UUID=a4793dbc-0c5d-482a-9b0f-b1e3445a42e2 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda8 during installation
UUID=7c4e77f2-5632-4e19-83a5-a446fcd33d63 /home           ext4    defaults        0       2
# /mnt/windows was on /dev/sda5 during installation
UUID=40AEB084AEB0744E /mnt/windows    ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda6 during installation
UUID=a1e31a67-53b4-47be-9387-d1ec7d9b29b4 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 247.0GB: boot/grub/core.img
 245.0GB: boot/grub/grub.cfg
 245.2GB: boot/initrd.img-2.6.35-22-generic
 247.0GB: boot/vmlinuz-2.6.35-22-generic
 245.2GB: initrd.img
 247.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  42 fc 11 e7 e7 5c 90 48  ee d7 5b 29 8c 93 56 5e  |B....\.H..[)..V^|
00000010  0a 9e 44 0f 47 6b 57 1b  ca 9a 33 42 06 08 3c 74  |..D.GkW...3B..<t|
00000020  26 ac 51 28 24 45 93 f3  3c ed 26 c2 28 41 9f 3c  |&.Q($E..<.&.(A.<|
00000030  a8 2a 61 73 e3 14 d0 bd  af b7 3f 4a ba af 61 48  |.*as......?J..aH|
00000040  02 a7 42 58 03 7d 90 b5  01 43 d4 37 65 35 44 70  |..BX.}...C.7e5Dp|
00000050  01 dd 67 af ae d1 11 0d  8e d8 60 0b dd d4 18 34  |..g.......`....4|
00000060  bf 39 ba 3b 5e 97 4b bf  ff a5 85 3e 8d 95 35 99  |.9.;^.K....>..5.|
00000070  6b 9c db 13 f7 aa 13 b2  99 a8 fa 65 c1 b9 70 7a  |k..........e..pz|
00000080  20 a7 d7 3d a8 8c e0 86  33 79 ce ff 3b 11 3a 7d  | ..=....3y..;.:}|
00000090  28 74 bf e0 b2 7b 87 56  84 67 e8 79 fd fd 77 b6  |(t...{.V.g.y..w.|
000000a0  c7 04 cf 10 2f c9 85 c2  5d ec 22 4a 3e c7 02 68  |..../...]."J>..h|
000000b0  82 16 ba ed 0a e3 7c 18  fb 8b e2 95 82 6c 17 c4  |......|......l..|
000000c0  d6 b2 4d 44 70 36 05 90  7c fa 36 ba 9d 80 7b 53  |..MDp6..|.6...{S|
000000d0  f5 87 d9 e2 03 74 5e ff  7c 90 cd 0d a2 93 2d ca  |.....t^.|.....-.|
000000e0  4e 9f 42 c8 e1 61 f2 7c  df cc 0d 09 a4 56 87 2f  |N.B..a.|.....V./|
000000f0  65 83 73 35 31 c0 f9 d9  a9 95 72 7c 56 9f 3e fc  |e.s51.....r|V.>.|
00000100  ca c4 f2 a2 e9 b8 67 87  68 8c 8b 87 2a 55 30 3f  |......g.h...*U0?|
00000110  a1 fb 60 1c 75 9e e6 dd  c7 87 19 77 df e5 6f e4  |..`.u......w..o.|
00000120  44 7e b1 09 17 1c a8 65  30 65 a6 96 de a4 43 f3  |D~.....e0e....C.|
00000130  4c b4 a8 32 60 c6 2e 16  d5 74 9d 5f f6 a9 50 f2  |L..2`....t._..P.|
00000140  46 4b f5 b9 89 8f b0 1b  dd a9 94 b7 5e 71 0c 54  |FK..........^q.T|
00000150  6e cb bc 5d 1a 8c ec 25  48 ef 14 ae 70 9c a0 52  |n..]...%H...p..R|
00000160  af e4 db 5e 61 d1 56 95  44 b4 8c f3 4a d2 80 c4  |...^a.V.D...J...|
00000170  e7 96 1c fa 7a e9 f8 bb  e1 d1 b4 bb c3 a9 35 72  |....z.........5r|
00000180  56 e7 fc 12 91 ec 95 67  1a 8b de 87 f9 9b 96 d6  |V......g........|
00000190  e6 4c 13 36 c2 95 9c 75  76 df a3 3b f0 12 42 67  |.L.6...uv..;..Bg|
000001a0  ad 5d 7d 2d d3 9d 2b 19  1a 7d 01 4f 7e 94 01 08  |.]}-..+..}.O~...|
000001b0  d6 cd ed 26 21 20 86 50  0d cf a5 7a 09 f0 00 fe  |...&! .P...z....|
000001c0  ff ff 07 fe ff ff 02 00  00 00 78 ee c1 04 00 fe  |..........x.....|
000001d0  ff ff 05 fe ff ff 7a ee  c1 04 88 d9 b2 00 00 00  |......z.........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by oldfred on 2011-03-21
I can easily explain 3. Swap & the extended partition will not be mounted as they are not usable as a user. Swap is automatically used if needed & the extended partition is just a container for all the logical, but does not have any data of its own. Your /home partition is mounted inside your / (root), but as a separate partition.

Generally you do not automatically get other partitions mounted unless you create a mount point and add that partition to the mount point in fstab. You can manually mount or use Nautilus (file manager) to mount it. Often in file manager other mountable partitions are just shown as 120GB or by label (New Volume, etc). Linux does not like spaces so that can make it more difficult to mount as you have to put it in quotes or add the /040 ASCII for space character.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by maxmiaggi on 2011-03-26
:):)

Thanks a lot guys!! I found out all the partitions in my drive.. they were located at different mount points! :)

Thanks a lot! Now I can call my self as a proud linux user too! ;)

---

