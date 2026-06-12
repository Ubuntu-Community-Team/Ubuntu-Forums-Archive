---
title: "Grub not working"
date: 2011-04-10
forum: Installation &amp; Upgrades
---

### Post by Grasber on 2011-04-10
Hi, I installed Ubuntu 10.10 in my secondary HDD that I partitioned as: 1. no format (50 GB) 2. regular ext4 (for  Ubuntu) 3. swap (at the end of the disk).
When installing, the installer asked me about the location of the boot loader or somthing like that, and I selected the secondary drive.

It all went very good, I even restarted de Pc once and Grub was working fine (it detected my Win7 installation too), but when I erased the partition with no format (the 1st one) to format it as NTFS, Grub wouldn't work again. It apparently was storing something related to Grub.

Now when I turn on the pc, there's a Grub rescue shell screen. On internet I found the commands that I can start Ubuntu with.
(The disks that the grub rescue can detect are [ls command]: (hd0) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1) (hd1) (hd1,msdos1)   (hd2) (hd2,msdos1) (fd0))

Now, what happens is that when I run the grub-update command inside Ubuntu, it' doesn't work.
I've got to point out that before running this command mi grub.cfg file had references to (hd0,msdos3) particion, wich I don't know. After running grub-update the references in the file changed to the unit  (hd0,msdos2), which is the one that I boot with in the grub rescue shell to make Ubuntu start. Then I restart and I see that it didn't work, there's a Grub rescue screen again.  I can see the references  in the variables prefix and root with the command 'set' and those are pointing to (hd0,msdos3).

Here's my grub.cfg file:
[pastebin.com/CpvfcGxp]("http://pastebin.com/CpvfcGxp")

Sorry about my english

---

### Post by lmarmisa on 2011-04-10
Please, open a terminal, type these commands and give us the outputs:

```

sudo fdisk -l
sudo blkid
cat /etc/fstab

```

---

### Post by Grasber on 2011-04-10
**>sudo fdisk -l**
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc300c300

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6079    48826368    7  HPFS/NTFS
/dev/sda2   *        6079        9763    29588480   83  Linux
/dev/sda3            9763       10012     1999872   82  Linux swap / Solaris

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x27f327f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       20674   156288000    7  HPFS/NTFS

Disk /dev/sdb: 1031 MB, 1031798784 bytes
255 heads, 63 sectors/track, 125 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0217934c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         126     1007584+   c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(124, 254, 63) logical=(125, 112, 51)

**>sudo blkid**
/dev/sda1: LABEL="Secundario" UUID="324EAD644EAD2199" TYPE="ntfs" 
/dev/sda2: UUID="78124ce7-f910-4861-a850-018baaa3cf0a" TYPE="ext4" 
/dev/sda3: UUID="fccbc41a-cd07-4425-9274-aa2de7a4a470" TYPE="swap" 
/dev/sdd1: UUID="9E90F68990F666E5" TYPE="ntfs" 
/dev/sdb1: LABEL="PENDRIVE" UUID="12DE-1232" TYPE="vfat" 

**>cat /etc/fstab**
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb3 during installation
UUID=78124ce7-f910-4861-a850-018baaa3cf0a /               ext4    errors=remount-ro 0       1
/dev/sdb1       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by oldfred on 2011-04-10
Your grub.cfg thinks grub is sda.

But your fstab thought everything was sdb.

# / was on /dev/sdb3 during installation
UUID=78124ce7-f910-4861-a850-018baaa3cf0a /               ext4    errors=remount-ro 0       1
/dev/sdb1       none            swap    sw              0       0

And mounting swap with /dev/sdb1 where now sdb1 is NTFS will not work.

You need to change the swap mount to:

UUID=fccbc41a-cd07-4425-9274-aa2de7a4a470        none            swap    sw              0       0

But I would like to see the full boot info script. It will show all of above data you posted but additional info on where you are booting from.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by Grasber on 2011-04-10
[LEFT]Oh, hell that sounds like everything's scrambled. :(

Here is the content of the file:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda2 and 
                       looks at sector 110561168 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #2 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    97,654,783    97,652,736   7 HPFS/NTFS
/dev/sda2    *     97,656,832   156,833,791    59,176,960  83 Linux
/dev/sda3         156,835,840   160,835,583     3,999,744  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1031 MB, 1031798784 bytes
255 heads, 63 sectors/track, 125 cylinders, total 2015232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     2,015,231     2,015,169   c W95 FAT32 (LBA)


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1               2,048   312,578,047   312,576,000   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        324EAD644EAD2199                       ntfs       Secundario                    
/dev/sda2        78124ce7-f910-4861-a850-018baaa3cf0a   ext4                                     
/dev/sda3        fccbc41a-cd07-4425-9274-aa2de7a4a470   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        12DE-1232                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 
/dev/sdd1        9E90F68990F666E5                       ntfs                                     
/dev/sdd: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdd1        /media/9E90F68990F666E5  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 78124ce7-f910-4861-a850-018baaa3cf0a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 78124ce7-f910-4861-a850-018baaa3cf0a
set locale_dir=($root)/boot/grub/locale
set lang=es
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 78124ce7-f910-4861-a850-018baaa3cf0a
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=78124ce7-f910-4861-a850-018baaa3cf0a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 78124ce7-f910-4861-a850-018baaa3cf0a
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=78124ce7-f910-4861-a850-018baaa3cf0a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 78124ce7-f910-4861-a850-018baaa3cf0a
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=78124ce7-f910-4861-a850-018baaa3cf0a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 78124ce7-f910-4861-a850-018baaa3cf0a
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=78124ce7-f910-4861-a850-018baaa3cf0a ro single 
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
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 78124ce7-f910-4861-a850-018baaa3cf0a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 78124ce7-f910-4861-a850-018baaa3cf0a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb3 during installation
UUID=78124ce7-f910-4861-a850-018baaa3cf0a /               ext4    errors=remount-ro 0       1
/dev/sdb1       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  56.5GB: boot/grub/core.img
  52.7GB: boot/grub/grub.cfg
  56.6GB: boot/grub/stage2
  52.8GB: boot/initrd.img-2.6.35-22-generic
  52.8GB: boot/initrd.img-2.6.35-28-generic
  57.2GB: boot/vmlinuz-2.6.35-22-generic
  57.1GB: boot/vmlinuz-2.6.35-28-generic
  52.8GB: initrd.img
  52.8GB: initrd.img.old
  57.1GB: vmlinuz
  57.2GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 04 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  c1 bf 1e 00 51 0f 00 00  00 00 00 00 02 00 00 00  |....Q...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 32 12 de 12 4e  4f 20 4e 41 4d 45 20 20  |..)2...NO NAME  |
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
00000110  c6 06 45 7d 00 66 b8 c6  1e 00 00 66 ba 00 00 00  |..E}.f.....f....|
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


=======Devices which don't seem to have a corresponding hard drive==============

sdc
```In case you want to know the list of commands that let me start Ubuntu from grub rescue:
> 
>set prefix=(hd0,2)/boot/grub
>set root=(hd0,2)
>insmod linux
>linux /vmlinuz root=/dev/sda2 ro
>initrd /initrd.img
>boot[/LEFT]

---

### Post by lmarmisa on 2011-04-10
You should update the content of file /etc/fstab as oldfred is proposing:

```

sudo cp /etc/fstab /etc/fstab.bak
sudo gedit /etc/fstab

```

Change the line

```

/dev/sdb1       none            swap    sw              0       0

```

with

```

UUID=fccbc41a-cd07-4425-9274-aa2de7a4a470        none            swap    sw              0       0

```

Save and exit.

Type these two commands then:

```

sudo grub-install /dev/sda
sudo update-grub

```

I believe this procedure will fix your problem.

---

### Post by Grasber on 2011-04-11
My god, it worked perfectly. Thank you so much!

---

### Post by oldfred on 2011-04-11
But your windows in sdd1 is not complete. Did you install windows to a second drive. It often then puts its boot partition in the first drive. The windows boot/recovery partition is a (hidden in windows) 100MB partition that the boot script show these two files:
/bootmgr /Boot/BCD

You main windows install then has this file which you have in sdd1:
/Windows/System32/winload.exe

You should be able to repair sdd1. You first need to put a boot flag (active partition in windows) on sdd1 with gparted or disk utility. Then use a windows repair CD to fix your install.

oldfred's Windows Vista/Win7 repair links posts #7 & #9:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

---

