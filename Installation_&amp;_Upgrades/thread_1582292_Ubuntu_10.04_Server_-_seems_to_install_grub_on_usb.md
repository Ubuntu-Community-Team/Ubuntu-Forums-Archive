---
title: "Ubuntu 10.04 Server - seems to install grub on usb installation source"
date: 2010-09-26
forum: Installation &amp; Upgrades
---

### Post by sotn0r on 2010-09-26
hi, 

i've tried a few times now to install ubuntu server 10.04 x86 to my old workstation as single operating system.

i'm installing it from an usb drive. now everything works fine, the installation finishes and tells me to remove the usb drive to reboot from the hdd. 

when i reboot, the system does not start ubuntu server from the hdd. however, when i reboot after inserting the usb drive again, it boots from the usb drive to the ubuntu installation. 

it seems to me as if the installer would install the grub boot loader to the usb drive and not in the hdd.

can i somehow install the grub loader to the hdd afterwards ? or tell the installer to install it to the hdd while performing the installation ?

help would be appreciated :)

thanks

sotn0r

---

### Post by mörgæs on 2010-09-26
Hi, welcome to the forum.

I guess the safe and easy solution would be to install from a CD.

---

### Post by danielconvissor on 2010-09-26
> **sotn0r said:**
> 
when i reboot after inserting the usb drive again, it boots from the usb drive to the ubuntu installation. 


Perhaps the Master Boot Record is out of whack on your hard drive?  Or the partition isn't flagged as bootable?

Boot to your USB and select the option to run Ubuntu live from the flash drive (not the installer).  From there, run the following against your hard drive:

```

# Substitute the device letter for "L" and partition number for "N".
parted /dev/sdLN unit co print unit s print

```

---

### Post by ahaider7 on 2010-09-26
I am having the same problem, but with ubuntu 10.04 desktop. Can boot into ubuntu installation only when the LiveUSB is attached to pc.

> **danielconvissor said:**
> Perhaps the Master Boot Record is out of whack on your hard drive?  Or the partition isn't flagged as bootable?

Boot to your USB and select the option to run Ubuntu live from the flash drive (not the installer).  From there, run the following against your hard drive:

```

# Substitute the device letter for "L" and partition number for "N".
parted /dev/sdLN unit co print unit s print

```

I have run the above command from the ubuntu installation itself (not the live ubuntu). Here is the output
```

Model: Unknown (unknown)
Disk /dev/sdb9: 10.3GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  10.3GB  10.3GB  ext4

Model: Unknown (unknown)
Disk /dev/sdb9: 20049920s
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End        Size       File system  Flags
 1      0s     20049919s  20049920s  ext4
```

---

### Post by drs305 on 2010-09-26
Both of you should be able to install Grub2 to the MBR of your hard drive with the following:

Boot to your normal Ubuntu Desktop. If the USB/external drive has to be connected that's ok.

Determine the partition on your hard drive on which Ubuntu is installed. Normally, you can just use the "mount" command to see on which device **/** is mounted.

Mount that device and install Grub. Note the first command lists the drive and partition, but the second references *only* the drive.  Change the values XY to the appropriate designations (examples: sda1, sda5, sdb5, etc)

```
sudo mount /dev/sdXY /mnt  # Example: sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sd**X**  # Note only sd**a**, sd**b**, etc

```

---

### Post by danielconvissor on 2010-09-26
Oops, I didn't mean to put on the partition number.  Do this instead:
```

parted /dev/sdL unit co print unit s print

```

---

### Post by ahaider7 on 2010-09-26
> **danielconvissor said:**
> Oops, I didn't mean to put on the partition number.  Do this instead:
```

parted /dev/sdL unit co print unit s print

```

Here is the new result

```
Model: ATA ST3160815AS (scsi)
Disk /dev/sdb: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  43.0GB  43.0GB  primary   ntfs            boot
 2      43.0GB  75.2GB  32.2GB  primary   ntfs
 3      75.2GB  160GB   84.9GB  extended                  lba
 5      75.2GB  102GB   26.8GB  logical   ntfs
 6      102GB   129GB   26.8GB  logical   ntfs
 7      129GB   146GB   17.2GB  logical   ntfs
 8      146GB   150GB   3759MB  logical   linux-swap(v1)
 9      150GB   160GB   10.3GB  logical   ext4

Model: ATA ST3160815AS (scsi)
Disk /dev/sdb: 312581808s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start       End         Size        Type      File system     Flags
 1      63s         83891429s   83891367s   primary   ntfs            boot
 2      83891430s   146801969s  62910540s   primary   ntfs
 3      146802031s  312580095s  165778065s  extended                  lba
 5      146802033s  199222064s  52420032s   logical   ntfs
 6      199222128s  251642159s  52420032s   logical   ntfs
 7      251642223s  285185879s  33543657s   logical   ntfs
 8      285186048s  292528127s  7342080s    logical   linux-swap(v1)
 9      292530176s  312580095s  20049920s   logical   ext4

```

---

### Post by ahaider7 on 2010-09-26
> **drs305 said:**
> Both of you should be able to install Grub2 to the MBR of your hard drive with the following:

Boot to your normal Ubuntu Desktop. If the USB/external drive has to be connected that's ok.

Determine the partition on your hard drive on which Ubuntu is installed. Normally, you can just use the "mount" command to see on which device **/** is mounted.

Mount that device and install Grub. Note the first command lists the drive and partition, but the second references *only* the drive.  Change the values XY to the appropriate designations (examples: sda1, sda5, sdb5, etc)

```
sudo mount /dev/sdXY /mnt  # Example: sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sd**X**  # Note only sd**a**, sd**b**, etc

```

Before going through this step, I want a little clarification. I am in my normal desktop ubuntu installation. The usb device was required to boot only, now its removed. The / is mounted on /dev/sdb9

Do I need to execute the command 1 in this case (that is, mounting it as /mnt) ???

---

### Post by drs305 on 2010-09-26
> **ahaider7 said:**
> Before going through this step, I want a little clarification. I am in my normal desktop ubuntu installation. The usb device was required to boot only, now its removed. The / is mounted on /dev/sdb9

Do I need to execute the command 1 in this case (that is, mounting it as /mnt) ???

Thanks for asking. You could do it as above but you can simply run this command:
```
sudo grub-install /dev/sd**X**
```
I would plug your usb device in so Grub2 can access those files if necessary. I don't think you have to but I haven't used a USB to install.

It would probably be best to update-grub again as well.

---

### Post by ahaider7 on 2010-09-26
> **drs305 said:**
> Thanks for asking. You could do it as above but you can simply run this command:
```
sudo grub-install /dev/sd**X**
```I would plug your usb device in so Grub2 can access those files if necessary. I don't think you have to but I haven't used a USB to install.

It would probably be best to update-grub again as well.

I did as you told, but still not able to get my grub working :(. Ubuntu won't boot unless usb drive is plugged in.

Here is the output of [boot_info_script]("http://bootinfoscript.sourceforge.net/") in case it is helpful.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #9 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

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

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 16.0 GB, 16018046976 bytes
80 heads, 16 sectors/track, 24441 cylinders, total 31285248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          8,064    31,285,247    31,277,184   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    83,891,429    83,891,367   7 HPFS/NTFS
/dev/sdb2          83,891,430   146,801,969    62,910,540   7 HPFS/NTFS
/dev/sdb3         146,802,031   312,580,095   165,778,065   f W95 Ext d (LBA)
/dev/sdb5         146,802,033   199,222,064    52,420,032   7 HPFS/NTFS
/dev/sdb6         199,222,128   251,642,159    52,420,032   7 HPFS/NTFS
/dev/sdb7         251,642,223   285,185,879    33,543,657   7 HPFS/NTFS
/dev/sdb8         285,186,048   292,528,127     7,342,080  82 Linux swap / Solaris
/dev/sdb9         292,530,176   312,580,095    20,049,920  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        BAED-2D54                              vfat       AMMAR PRO                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        EA10005710002D5F                       ntfs                                     
/dev/sdb2        01CB3F90A5498350                       ntfs                                     
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        01CB3F90A71F2DB0                       ntfs                                     
/dev/sdb6        01CB3F90A8FC0400                       ntfs                                     
/dev/sdb7        01CB3F90AB062BE0                       ntfs                                     
/dev/sdb8        2911d302-a4da-4f74-94ba-c6e3c0fa9f0a   swap                                     
/dev/sdb9        7145d88a-c063-4b78-bce0-bc4e9d2a8d09   ext4                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb9        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /media/AMMAR PRO         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=5 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdb9/boot/grub/grub.cfg: ===========================

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
set root='(hd1,9)'
search --no-floppy --fs-uuid --set 7145d88a-c063-4b78-bce0-bc4e9d2a8d09
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
set root='(hd1,9)'
search --no-floppy --fs-uuid --set 7145d88a-c063-4b78-bce0-bc4e9d2a8d09
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,9)'
    search --no-floppy --fs-uuid --set 7145d88a-c063-4b78-bce0-bc4e9d2a8d09
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=7145d88a-c063-4b78-bce0-bc4e9d2a8d09 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,9)'
    search --no-floppy --fs-uuid --set 7145d88a-c063-4b78-bce0-bc4e9d2a8d09
    echo    'Loading Linux 2.6.32-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=7145d88a-c063-4b78-bce0-bc4e9d2a8d09 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,9)'
    search --no-floppy --fs-uuid --set 7145d88a-c063-4b78-bce0-bc4e9d2a8d09
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,9)'
    search --no-floppy --fs-uuid --set 7145d88a-c063-4b78-bce0-bc4e9d2a8d09
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ea10005710002d5f
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb9 during installation
UUID=7145d88a-c063-4b78-bce0-bc4e9d2a8d09 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb8 during installation
UUID=2911d302-a4da-4f74-94ba-c6e3c0fa9f0a none            swap    sw              0       0

=================== sdb9: Location of files loaded by Grub: ===================


 150.3GB: boot/grub/core.img
 154.6GB: boot/grub/grub.cfg
 150.8GB: boot/initrd.img-2.6.32-24-generic-pae
 150.8GB: boot/vmlinuz-2.6.32-24-generic-pae
 150.8GB: initrd.img
 150.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb3

00000000  ec e8 1f 99 f5 8f b0 7a  23 cf 5d 0f c4 92 17 70  |.......z#.]....p|
00000010  ae 9a 39 52 47 01 b5 db  c6 50 97 5f ca dc 62 1d  |..9RG....P._..b.|
00000020  95 d1 4f 7f 1d 18 1f a3  92 a5 64 0e 01 d0 58 d1  |..O.......d...X.|
00000030  ee 04 6c 26 ce 8c 3a 83  f1 d8 9d 0e cc 8c 16 f3  |..l&..:.........|
00000040  03 b9 53 d5 c1 63 37 12  7b 51 7a 01 e9 2e fd c4  |..S..c7.{Qz.....|
00000050  d6 2e 18 69 e0 9e 3b 3f  34 1b 1c 5d 20 de 23 c2  |...i..;?4..] .#.|
00000060  bc 4d a0 24 3f 3f 19 5e  d5 dd e8 69 22 c8 9b 3a  |.M.$??.^...i"..:|
00000070  bf 7a 19 b5 f2 46 c8 f9  67 7f 7d f3 0d f7 08 85  |.z...F..g.}.....|
00000080  e9 b9 d0 2c 12 f5 cc d6  04 aa b6 6e 92 f3 a5 82  |...,.......n....|
00000090  1f 0c b1 3b e0 f0 35 4a  e7 a5 fd c4 7c 30 a1 27  |...;..5J....|0.'|
000000a0  38 cb df e0 56 fa cf ff  a8 d8 74 54 1a 55 dd 94  |8...V.....tT.U..|
000000b0  67 60 d7 6d b5 a0 b1 c0  5b df 05 19 93 52 04 9d  |g`.m....[....R..|
000000c0  02 ae ef 2c e1 12 98 9a  57 48 07 eb 04 8b 99 b2  |...,....WH......|
000000d0  93 5b 20 bd de fb b0 72  18 48 7d 05 b9 56 fe 06  |.[ ....r.H}..V..|
000000e0  97 c9 af 07 8a 0a 76 3e  fb f2 c7 17 bf 33 70 de  |......v>.....3p.|
000000f0  bd bc bd 1e fe e4 97 ba  b9 72 65 37 81 05 2e 9d  |.........re7....|
00000100  8c 60 bd 95 07 98 6e ed  b2 3d 44 78 30 99 d3 1f  |.`....n..=Dx0...|
00000110  d2 40 32 8d 22 8a a6 35  23 1e b0 97 c6 8b 13 51  |.@2."..5#......Q|
00000120  25 9b e6 48 4c 2b 82 3d  74 21 cf a1 2e 3f fb ac  |%..HL+.=t!...?..|
00000130  fc 01 e2 9c 23 d0 78 9f  91 3c 03 ae 08 5e e4 ef  |....#.x..<...^..|
00000140  7e ab 92 51 6f 8e f4 73  a6 5b 09 ff bc a3 31 69  |~..Qo..s.[....1i|
00000150  e1 9b 9c 28 af 48 81 73  1a 3c 13 ea cd 78 aa f6  |...(.H.s.<...x..|
00000160  78 6d 36 1c 3d 1a 17 18  8c 09 b9 e6 e5 83 9a ac  |xm6.=...........|
00000170  10 e2 85 bb 40 bd 0a 69  1c 90 af c7 bc d7 2c 8e  |....@..i......,.|
00000180  d2 4b d4 06 96 c3 d7 c7  06 ac b7 c5 77 e5 4b 0e  |.K..........w.K.|
00000190  47 6e 29 d2 b0 b5 f0 96  68 03 41 4c a0 67 b2 f3  |Gn).....h.AL.g..|
000001a0  cd a9 6f d7 27 7c f9 4d  cd f6 79 a5 9c 65 0d 6c  |..o.'|.M..y..e.l|
000001b0  10 26 aa 9e 01 ea 16 d9  aa cc 71 57 1b c5 00 fe  |.&........qW....|
000001c0  ff ff 07 fe ff ff 02 00  00 00 c0 dd 1f 03 00 fe  |................|
000001d0  ff ff 05 fe ff ff c2 dd  1f 03 ff dd 1f 03 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by drs305 on 2010-09-26
> **ahaider7 said:**
> I did as you told, but still not able to get my grub working :(. Ubuntu won't boot unless usb drive is plugged in.


In your case, Ubuntu is installed on sd**b9** so you have to run the command as:
```
sudo grub-install /dev/sdb
```

This is going to replace the Windows MBR info with Grub2's. You may need to run "sudo update-grub" to ensure G2 picks up the Windows install and includes it in the Grub menu.

If the current sda is not your USB drive, you should also change the boot order after you install it so that BIOS points to your Ubuntu drive first.

If you look at the first part of the results.txt, you can see Grub is installed on sda and looks for the nonexistent sda9.
> > Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #9 for /boot/grub.


---

### Post by ahaider7 on 2010-09-26
> **ahaider7 said:**
> I did as you told, but still not able to get my grub working :(. Ubuntu won't boot unless usb drive is plugged in.

Here is the output of [boot_info_script]("http://bootinfoscript.sourceforge.net/") in case it is helpful.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #9 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

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

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 16.0 GB, 16018046976 bytes
80 heads, 16 sectors/track, 24441 cylinders, total 31285248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          8,064    31,285,247    31,277,184   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    83,891,429    83,891,367   7 HPFS/NTFS
/dev/sdb2          83,891,430   146,801,969    62,910,540   7 HPFS/NTFS
/dev/sdb3         146,802,031   312,580,095   165,778,065   f W95 Ext d (LBA)
/dev/sdb5         146,802,033   199,222,064    52,420,032   7 HPFS/NTFS
/dev/sdb6         199,222,128   251,642,159    52,420,032   7 HPFS/NTFS
/dev/sdb7         251,642,223   285,185,879    33,543,657   7 HPFS/NTFS
/dev/sdb8         285,186,048   292,528,127     7,342,080  82 Linux swap / Solaris
/dev/sdb9         292,530,176   312,580,095    20,049,920  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        BAED-2D54                              vfat       AMMAR PRO                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        EA10005710002D5F                       ntfs                                     
/dev/sdb2        01CB3F90A5498350                       ntfs                                     
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        01CB3F90A71F2DB0                       ntfs                                     
/dev/sdb6        01CB3F90A8FC0400                       ntfs                                     
/dev/sdb7        01CB3F90AB062BE0                       ntfs                                     
/dev/sdb8        2911d302-a4da-4f74-94ba-c6e3c0fa9f0a   swap                                     
/dev/sdb9        7145d88a-c063-4b78-bce0-bc4e9d2a8d09   ext4                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb9        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /media/AMMAR PRO         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=5 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdb9/boot/grub/grub.cfg: ===========================

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
set root='(hd1,9)'
search --no-floppy --fs-uuid --set 7145d88a-c063-4b78-bce0-bc4e9d2a8d09
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
set root='(hd1,9)'
search --no-floppy --fs-uuid --set 7145d88a-c063-4b78-bce0-bc4e9d2a8d09
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,9)'
    search --no-floppy --fs-uuid --set 7145d88a-c063-4b78-bce0-bc4e9d2a8d09
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=7145d88a-c063-4b78-bce0-bc4e9d2a8d09 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,9)'
    search --no-floppy --fs-uuid --set 7145d88a-c063-4b78-bce0-bc4e9d2a8d09
    echo    'Loading Linux 2.6.32-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=7145d88a-c063-4b78-bce0-bc4e9d2a8d09 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,9)'
    search --no-floppy --fs-uuid --set 7145d88a-c063-4b78-bce0-bc4e9d2a8d09
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,9)'
    search --no-floppy --fs-uuid --set 7145d88a-c063-4b78-bce0-bc4e9d2a8d09
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ea10005710002d5f
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb9 during installation
UUID=7145d88a-c063-4b78-bce0-bc4e9d2a8d09 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb8 during installation
UUID=2911d302-a4da-4f74-94ba-c6e3c0fa9f0a none            swap    sw              0       0

=================== sdb9: Location of files loaded by Grub: ===================


 150.3GB: boot/grub/core.img
 154.6GB: boot/grub/grub.cfg
 150.8GB: boot/initrd.img-2.6.32-24-generic-pae
 150.8GB: boot/vmlinuz-2.6.32-24-generic-pae
 150.8GB: initrd.img
 150.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb3

00000000  ec e8 1f 99 f5 8f b0 7a  23 cf 5d 0f c4 92 17 70  |.......z#.]....p|
00000010  ae 9a 39 52 47 01 b5 db  c6 50 97 5f ca dc 62 1d  |..9RG....P._..b.|
00000020  95 d1 4f 7f 1d 18 1f a3  92 a5 64 0e 01 d0 58 d1  |..O.......d...X.|
00000030  ee 04 6c 26 ce 8c 3a 83  f1 d8 9d 0e cc 8c 16 f3  |..l&..:.........|
00000040  03 b9 53 d5 c1 63 37 12  7b 51 7a 01 e9 2e fd c4  |..S..c7.{Qz.....|
00000050  d6 2e 18 69 e0 9e 3b 3f  34 1b 1c 5d 20 de 23 c2  |...i..;?4..] .#.|
00000060  bc 4d a0 24 3f 3f 19 5e  d5 dd e8 69 22 c8 9b 3a  |.M.$??.^...i"..:|
00000070  bf 7a 19 b5 f2 46 c8 f9  67 7f 7d f3 0d f7 08 85  |.z...F..g.}.....|
00000080  e9 b9 d0 2c 12 f5 cc d6  04 aa b6 6e 92 f3 a5 82  |...,.......n....|
00000090  1f 0c b1 3b e0 f0 35 4a  e7 a5 fd c4 7c 30 a1 27  |...;..5J....|0.'|
000000a0  38 cb df e0 56 fa cf ff  a8 d8 74 54 1a 55 dd 94  |8...V.....tT.U..|
000000b0  67 60 d7 6d b5 a0 b1 c0  5b df 05 19 93 52 04 9d  |g`.m....[....R..|
000000c0  02 ae ef 2c e1 12 98 9a  57 48 07 eb 04 8b 99 b2  |...,....WH......|
000000d0  93 5b 20 bd de fb b0 72  18 48 7d 05 b9 56 fe 06  |.[ ....r.H}..V..|
000000e0  97 c9 af 07 8a 0a 76 3e  fb f2 c7 17 bf 33 70 de  |......v>.....3p.|
000000f0  bd bc bd 1e fe e4 97 ba  b9 72 65 37 81 05 2e 9d  |.........re7....|
00000100  8c 60 bd 95 07 98 6e ed  b2 3d 44 78 30 99 d3 1f  |.`....n..=Dx0...|
00000110  d2 40 32 8d 22 8a a6 35  23 1e b0 97 c6 8b 13 51  |.@2."..5#......Q|
00000120  25 9b e6 48 4c 2b 82 3d  74 21 cf a1 2e 3f fb ac  |%..HL+.=t!...?..|
00000130  fc 01 e2 9c 23 d0 78 9f  91 3c 03 ae 08 5e e4 ef  |....#.x..<...^..|
00000140  7e ab 92 51 6f 8e f4 73  a6 5b 09 ff bc a3 31 69  |~..Qo..s.[....1i|
00000150  e1 9b 9c 28 af 48 81 73  1a 3c 13 ea cd 78 aa f6  |...(.H.s.<...x..|
00000160  78 6d 36 1c 3d 1a 17 18  8c 09 b9 e6 e5 83 9a ac  |xm6.=...........|
00000170  10 e2 85 bb 40 bd 0a 69  1c 90 af c7 bc d7 2c 8e  |....@..i......,.|
00000180  d2 4b d4 06 96 c3 d7 c7  06 ac b7 c5 77 e5 4b 0e  |.K..........w.K.|
00000190  47 6e 29 d2 b0 b5 f0 96  68 03 41 4c a0 67 b2 f3  |Gn).....h.AL.g..|
000001a0  cd a9 6f d7 27 7c f9 4d  cd f6 79 a5 9c 65 0d 6c  |..o.'|.M..y..e.l|
000001b0  10 26 aa 9e 01 ea 16 d9  aa cc 71 57 1b c5 00 fe  |.&........qW....|
000001c0  ff ff 07 fe ff ff 02 00  00 00 c0 dd 1f 03 00 fe  |................|
000001d0  ff ff 05 fe ff ff c2 dd  1f 03 ff dd 1f 03 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```


Oh! It working now.

Sorry for the last message. I just noticed that I had specified wrong partition (*sda* instead of *sdb*) in the grub-install command. Running the command again with proper input parameters does the job. Now I can easily booth into my fresh ubuntu installation.

Thanks a lot for your help.

---

