---
title: "dual boot efi windows and efi linux"
date: 2011-12-02
forum: Installation &amp; Upgrades
---

### Post by jake42 on 2011-12-02
Hi,

I have a new x64 HP computer that supports EFI.  I installed windows 7 pro using a EFI bootable usb thumb drive.  Windows 7 works great.  Now I want to install Ubuntu Lucid Lynx also by booting from a EFI bootable usb thumb drive.  Unfortunately Ubuntu doesn't seem to support EFI booting for installation.  So my plan is to boot the ubuntu installer using legancy mode and download grub 1.99 and do the following:
export EFI_ARCH=x86_64 ./configure --with-platform=efi --target=${EFI_ARCH} --program-prefix="" make
sudo mkdir -p /mnt/EFISYS # if the mount-point does not exist sudo modprobe dm-mod # required to make grub-probe stop complaining sudo mount -t vfat -o rw,users /dev/sdc1 /mnt/EFISYS sudo mkdir -p /mnt/EFISYS/efi/grub
cd <grub2_compiled_source_dir>/grub-core ../grub-mkimage -O ${EFI_ARCH}-efi -d . -o grub.efi -p "" part_gpt part_msdos ntfs ntfscomp hfsplus fat ext2 normal chain boot configfile linux multiboot sudo cp grub.efi *.mod *.lst /mnt/EFISYS/efi/grub
sudo touch /mnt/EFISYS/efi/grub/grub.cfg

The above is from [https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting) but doesn't cover exactly what I am trying to do.
That should be enough to get the system to boot the thumb drive using EFI right?
Once I get the system to EFI boot how should I partition the Linux system?  I have:
sda - window 7 x64 sp1
sda1 - windows 7 EFI partition
sda2 - msr Microsoft reserved partition
sda3 - windows 7 install

sdb - Linux blank hard drive

sdc - usb thumb drive

Does Linux need its own EFI partition?  Can it share with sda1?

Thanks

---

### Post by oldfred on 2011-12-03
I have not done any of this, but since I hope to soon I have saved some links. 
One bug in grub is that it overwrites the efi partition and reformats it to fat16. It should do neither. So be sure to make a backup of the Windows efi partition so you can restore that and reset to fat32 so Windows works. 
As I understand it, you just about need the very latest version of grub to really work with UEFI and even then may have to work around some bugs they still are fixing.

[SOLVED] Win 7, Natty dual boot on UEFI sort of working 
[http://ubuntuforums.org/showthread.php?t=1753717](http://ubuntuforums.org/showthread.php?t=1753717)
[SOLVED] UEFI Boot Problems 
quiet splash vt.handoff=7 rootdelay=90 reboot=a,w
[http://ubuntuforums.org/showthread.php?t=1857639](http://ubuntuforums.org/showthread.php?t=1857639)

For Arch but discusses grub2.
Grub2 efi info ArchLinux
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

Windows 7 64bit UEFI 2.x boot:
[http://www.insanelymac.com/forum/index.php?showtopic=186440](http://www.insanelymac.com/forum/index.php?showtopic=186440)
Dual boot UEFI & windows UEFI post 76
[http://ubuntuforums.org/showthread.php?t=1719851&page=8](http://ubuntuforums.org/showthread.php?t=1719851&page=8)
[http://ubuntuforums.org/showthread.php?t=1746194](http://ubuntuforums.org/showthread.php?t=1746194)
Many links & discussion:
[http://ubuntuforums.org/showthread.php?t=1734677](http://ubuntuforums.org/showthread.php?t=1734677)

Someone posted this, but they were also using refit:

```
find /boot/efi -name "*efi"
/boot/efi
/boot/efi/EFI/ubuntu/grubx64.efi
/boot/efi/EFI/BOOT/refit.efi
/boot/efi/EFI/BOOT/bootx64.efi
/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
/boot/efi/EFI/Microsoft/Boot/bootmgr.efi
/boot/efi/EFI/Microsoft/Boot/memtest.efi
/boot/efi/EFI/grub/grub.efi
/boot/efi/EFI/BOOT-backup/bootx64.efi
/boot/efi/EFI/BOOT-backup/BOOT/refit/refit.efi
/boot/efi/EFI/BOOT-backup/BOOT/bootx64.efi

sudo efibootmgr -v

```

UEFI bugs:
Deletes Windows efi partition
Installer should not format an existing EFI System Partition 
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669)
EFI SYSTEM PARTITION should be atleast 100 MiB size and formatted as FAT32, not FAT16
[https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/811485)
ctrl-x does not work in grub-efi
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/722950](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/722950)
grub-update fails to detect windows bootloader on a uefi system
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)
MSI UEFI bug work around A75MA-G55 UEFI boot entries disappear 
[http://forum-en.msi.com/index.php?topic=153411.0](http://forum-en.msi.com/index.php?topic=153411.0)

---

### Post by jake42 on 2011-12-17
The good news is my computer can EFI boot from my linux thumb drive.  I used the directions at 
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
The important part was to rename the /efi/grub directory to /etc/boot and rename grub.efi to bootx64.efi
I don't think HP has all of the bugs worked out of their EFI bios yet.  It should have worked without renaming anything.

However I having difficulties writing a valid grub.cfg.  So far all I can do is boot to a grub prompt.

---

### Post by oldfred on 2011-12-17
Did you review the Arch site with UEFI sub-heading:
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)
and this:
[UEFI]("https://wiki.archlinux.org/index.php/UEFI") systems 


It seems to go over grub2 and UEFI pretty well and does not look like much is Arch specific.

---

### Post by jake42 on 2011-12-18
Thank you for the Arch Linux link it solved my grub.cfg issue.

I now have a EFI booting USB thumb drive of Ubuntu.  During boot I get a fair amount warnings.  I also get a kernel panic when I try to reboot.
I am using Ubuntu 10.04 LTS, Linux kernel 2.6.39.4

I am not going to install Linux to the second hard drive as the above bugs haven't been fixed yet.  I hope they get fixed for 12.04 LTS.

---

### Post by jake42 on 2011-12-28
I managed to install Ubuntu 10 LTS on my system using EFI.  I started the installer and selected the option to manually create the partition layout.  I used the following layout on my 250GB drive:
200MB /dos fat32
240GB / ext4
8GB swap
 
Before I clicked on install I selected advanced and deselected the option to install grub.  I then clicked on install.  Everything installed fine.  I then opened a terminal and copied my grub2 configuration from my usb thumb drive to /target/dos
cp -R /cdrom/EFI /target/dos

Here is my grub.cfg
# Config file for GRUB2 - The GNU GRand Unified Bootloader
# /boot/grub/grub.cfg

# DEVICE NAME CONVERSIONS
#
#  Linux           Grub
# -------------------------
#  /dev/fd0        (fd0)
#  /dev/sda        (hd0)
#  /dev/sdb2       (hd1,2)
#  /dev/sda3       (hd0,3)
#

# Timeout for menu
set timeout=5

# Set default boot entry as Entry 0
set default=1

# Set default color
set color_normal=white/blue

# (0) Original
menuentry "x64 Linux" {
set root=(hd1,1)
linux /vmlinuz-2.6.39.4 root=/dev/sdb2 
initrd /initrd.img-2.6.39.4
}

# (1) custom kernel
menuentry "x64 Linux custom kernel" {
set root=(hd1,1)
linux /vmlinuz-3.1.6 root=/dev/sdb2 
initrd /initrd.img-3.1.6
}

# (2) Windows
menuentry "Windows" {
set root=(hd0,1)
chainloader (${root})/EFI/Boot/bootx64.efi 
}

So I have a pretty good system now.  I just need to fix the clock in Linux.  When I boot back into windows my clock is off by my timezone -5 hours.  I also need to write a xorg.conf, the default screen resolution is way too small and kandkresize doesn't have any other resolutions than the highest resolution the monitor supports.  I prefer 1280x800 instead of the 1440x960 that Ubuntu is using.  Finally I need to figure out how to boot Ubuntu without having X auto start.  It used to be easy, edit /etc/inittab and change 5 to 3.  I know Ubuntu is using upstart but there is no /etc/event.d directory that the documentation says should be there.

Since my BIOS doesn't allow me to specify which hard drive to EFI boot from I might move the grub files form the second hard drive to the first to enable grub2 to dual boot without me having to press F9 at exactly the right moment.

---

### Post by oldfred on 2011-12-28
We are trying to test a new bootinfoscript to verify that it has improvements. One is to correctly identify the efi files. Can you run this and post the results.txt? Thanks.

[http://ubuntuforums.org/showthread.php?t=1897412](http://ubuntuforums.org/showthread.php?t=1897412)
```

wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'

chmod a+x bootinfoscript
```

Then you can run it 

sudo bash bootinfoscript

---

### Post by jake42 on 2011-12-29
Thank you for the detailed instructions.  I appreciate it. Attached is the results.txt file.    

Please note that the /grub/grub.cfg is NOT the grub.cfg that I use.  The grub.cfg I use is in /dev/sdb1/EFI/Boot/ and can be found in my previous posting.

The /dev/sdb1/grub/grub.cfg came when I did a apt-get install grub2 which is rather pointless as all of the files have to be in /dev/sdb1/EFI/Boot/ for the system to boot. 

Thanks,

---

### Post by oldfred on 2011-12-29
Thanks Jake42, that helps as it does show efi boot files.

Posted in case anyone wants to see it.
```

                   Boot Info Script 0.60      [17 May 2011]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    54130 of the same hard drive for core.img. core.img is at this location 
    and looks in partition 1 for /grub.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /grub/grub.cfg /efi/Boot/bootx64.efi /efi/Boot/x64.efi 
                       /grub/core.img

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  BackTrack 5 R1 - Code Name 
                       Revolution 64 bit
    Boot files:        /etc/fstab

sdb3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
256 heads, 63 sectors/track, 30282 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 4,294,967,295 4,294,967,295  ee GPT

/dev/sda1 ends after the last sector of /dev/sda

GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       206,847       204,800 EFI System partition
/dev/sda2         206,848       468,991       262,144 Microsoft Reserved Partition (Windows)
/dev/sda3         468,992   488,396,799   487,927,808 Data partition (Windows/Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1   488,397,167   488,397,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1           2,048       391,167       389,120 Data partition (Windows/Linux)
/dev/sdb2         391,168   472,772,607   472,381,440 Data partition (Windows/Linux)
/dev/sdb3     472,772,608   488,394,751    15,622,144 Swap partition (Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        4896-78D2                              vfat       
/dev/sda3        98FC9E9BFC9E736C                       ntfs       
/dev/sdb1        EDD3-770E                              vfat       
/dev/sdb2        906a0a9c-9bbe-44d1-b641-972378260353   ext4       
/dev/sdb3        28ab343f-d249-4172-9440-2e7912cfa431   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /boot                    vfat       (rw,utf8,umask=007,gid=46)
/dev/sdb2        /                        ext4       (rw,errors=remount-ro)


============================= sdb1/grub/grub.cfg: ==============================

--------------------------------------------------------------------------------
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
set root='(hd1,2)'
search --no-floppy --fs-uuid --set 906a0a9c-9bbe-44d1-b641-972378260353
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  set gfxpayload=keep
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod fat
set root='(hd1,1)'
search --no-floppy --fs-uuid --set edd3-770e
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.39.4' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod fat
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set edd3-770e
    linux    /vmlinuz-2.6.39.4 root=UUID=906a0a9c-9bbe-44d1-b641-972378260353 ro   quiet splash
    initrd    /initrd.img-2.6.39.4
}
menuentry 'Ubuntu, with Linux 2.6.39.4 (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod fat
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set edd3-770e
    echo    'Loading Linux 2.6.39.4 ...'
    linux    /vmlinuz-2.6.39.4 root=UUID=906a0a9c-9bbe-44d1-b641-972378260353 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.39.4
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             grub/core.img                                  1
            ?? = ??             grub/grub.cfg                                  1
            ?? = ??             initrd.img-2.6.39.4                            1
            ?? = ??             initrd.img-3.1.6                               1
            ?? = ??             vmlinuz-2.6.39.4                               1
            ?? = ??             vmlinuz-3.1.6                                  1

=============================== sdb2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=906a0a9c-9bbe-44d1-b641-972378260353 /               ext4    errors=remount-ro 0       1
# /dos was on /dev/sdb1 during installation
UUID=EDD3-770E  /boot            vfat    utf8,umask=007,gid=46 0       1
/dev/sdb3       none            swap    sw              0       0
--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 02 fe 19  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 20 03 00 01 03 00 00  00 00 00 00 02 00 00 00  |. ..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 d2 78 96 48 4e  4f 20 4e 41 4d 45 20 20  |..).x.HNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200
```

---

### Post by Gert Hulselmans on 2012-01-02
@ Jake42
Can you download the last version of BIS and run it again?
The Boot Sector type should now display something else than "Unknown" (Paste that part).
```
sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi
```

---

### Post by nehaljwani on 2012-10-08
You don't necessarily need to dual boot Windows and Linux on UEFI. Follow the guide [http://www.youtube.com/watch?v=PEou2dIcMSE](http://www.youtube.com/watch?v=PEou2dIcMSE) to convert your UEFI to MBR-BIOS without loss of data. Or read about it here: [http://commandlinewani.blogspot.com/2012/09/how-to-install-ubuntu-1204-in-sony-vaio.html](http://commandlinewani.blogspot.com/2012/09/how-to-install-ubuntu-1204-in-sony-vaio.html)

---

