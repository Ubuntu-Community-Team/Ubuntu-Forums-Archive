---
title: "full ubuntu installation on usb hdd"
date: 2011-08-13
forum: Installation &amp; Upgrades
---

### Post by takaya.aiba on 2011-08-13
hi,

please help.

ive been searching for the past week on how to install ubuntu onto a usb hdd and i have had no luck whatsoever.
it looks as though i can use tools like the startup disk creator, unetbootin, or pendrivelinux, but that these tools will restrict the size of the install to 4GB.

how can i install ubuntu to a usb as though it were a regular internal drive?

someone has to know! i dont want to be doomed to windows os =[

regards,
takaya

---

### Post by oldfred on 2011-08-13
Welcome to the forums.

It is just like a standard install. But you do want to install the grub2 bootloader to the MBR of the external drive and set BIOS to boot that first. Then when unplugged it will default back to the internal drive.

The only way to get a choice on where to install grub's boot loader is to use manual install or Something Else in Natty.

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by takaya.aiba on 2011-08-14
thankyou oldfred for your prompt reply!
unfortunately i did not have very much luck.

i followed the instructions listed here:
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

my internal drive was listed as 'sda'
the external drive im hoping to install to was 'sdb'

i created the swap partition and the / partition on 'sdb'
then i tried to install the boot loader onto /dev/sdb

when the machine starts up, i tell it to boot off the usb. the screen then goes black with a blinking white cursor at the top. it seems as though its about to start loading an OS but nothing happens.


thanks again,
takaya

---

### Post by dr1094 on 2011-08-14
The website for ubuntu download actually gives you instructions on how to install ubuntu on a usb. follow this link: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Under step 2, after the sentence 'I would like to create a:' click "usb stick" and simply follow all relevant steps. I hope this is what you were looking for.

As for running ubuntu from a USB, I have done it before using this method. It didn't work out well for me, the system would freeze, and eventually my 16 gig filled up, the system stopped responding, became useless (on the usb), your best bet is to either install it on the computer or alongside windows.

cheers,

---

### Post by takaya.aiba on 2011-08-14
hi dr1094, thanks for your help.

i would use the procedure listed here:
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
but as far as i can tell you are only able to set a persistent file size of 4GB using Univeral USB Installer?

another option i have considered is the 'Make Startup Disk' tool that runs from the LiveCD.
however it seems that both of the installation methods limit the size of the ubuntu partition?

i want to be able to dedicate the entire 500GB usb hdd to the ubuntu installation.

anyway, thanks for your help.
i would be completely lost without this ubuntu forum and posts like yours.

takaya

---

### Post by oldfred on 2011-08-14
With external plugged in, run this from LiveCd/USB.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by C.S.Cameron on 2011-08-14
Following step by step for Full install of 11.04 to USB device, partition sizes given are for 8GB drive, adjust size to suit:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the USB drive.
Insert the Live CD or Live USB.
Start the computer, the CD / flash drive should boot, (you need to adjust BIOS to boot USB).
Select language
Select "Forward".
Select Download updates while installing and Select Install this third-party software.
(Notice that at least 4.4 GB drive space is required, 4GB bootable flash drive users must choose another distro for a full install).
Forward
If prompted unmount partitions.
Select "Something else"
Forward
Confirm "Device for boot loader installation:"is correct, (If you left your internal HDD plugged in make sure the USB drive root is selected - sdb not sdb1).
(Optional Windows data partition)
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1000
"Location = Beginning".
"Use as: = FAT32 file system"
And "Mount point = windows".
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1 to 2 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional swap partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB), Beginning and "Use as" = "swap area" then OK.
(Importent)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Forward.
Select Keyboard layout.
Forward.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select forward.
Wait until install is complete.
Turn off computer and enable the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.

---

### Post by takaya.aiba on 2011-08-15
hi c.s.cameron! thankyou for your suggestion. 
as far as i can tell that is the method, or at least one of the methods i have tried. 

oldfred, here is the output of the script you asked me to execute.

thankyou both for your assistance. hopefully this will help you to identify the issue.

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 2 for (,msdos2)/boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /boot/bcd

sda4: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       409,599       407,552   7 NTFS / exFAT / HPFS
/dev/sda2             409,600 1,434,288,127 1,433,878,528   7 NTFS / exFAT / HPFS
/dev/sda3       1,434,288,128 1,464,936,447    30,648,320   7 NTFS / exFAT / HPFS
/dev/sda4       1,464,936,448 1,465,147,119       210,672   c W95 FAT32 (LBA)


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048    11,999,231    11,997,184  82 Linux swap / Solaris
/dev/sdb2    *     11,999,232   976,771,071   964,771,840  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        A040F60140F5DE4A                       ntfs       SYSTEM
/dev/sda2        C28409F68409EE2B                       ntfs       
/dev/sda3        AC1A0D781A0D4136                       ntfs       RECOVERY
/dev/sda4        E809-18DB                              vfat       HP_TOOLS
/dev/sdb1        5fdc5e58-6389-4045-808e-54adc9b40eef   swap       
/dev/sdb2        4bac68de-341f-4368-9421-49e6e394795c   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb2        /media/4bac68de-341f-4368-9421-49e6e394795c ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sdb2/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set 4bac68de-341f-4368-9421-49e6e394795c
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos2)'
search --no-floppy --fs-uuid --set 4bac68de-341f-4368-9421-49e6e394795c
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
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 4bac68de-341f-4368-9421-49e6e394795c
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=4bac68de-341f-4368-9421-49e6e394795c ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 4bac68de-341f-4368-9421-49e6e394795c
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=4bac68de-341f-4368-9421-49e6e394795c ro single 
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
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 4bac68de-341f-4368-9421-49e6e394795c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos2)'
    search --no-floppy --fs-uuid --set 4bac68de-341f-4368-9421-49e6e394795c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a040f60140f5de4a
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set c28409f68409ee2b
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set ac1a0d781a0d4136
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
--------------------------------------------------------------------------------

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
UUID=4bac68de-341f-4368-9421-49e6e394795c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb1 during installation
UUID=5fdc5e58-6389-4045-808e-54adc9b40eef none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 303.857418060 = 326.264418304  boot/grub/core.img                             1
 239.858478546 = 257.546080256  boot/grub/grub.cfg                             1
 448.103668213 = 481.147650048  boot/initrd.img-2.6.35-22-generic              2
 303.855888367 = 326.262775808  boot/vmlinuz-2.6.35-22-generic                 1
 448.103668213 = 481.147650048  initrd.img                                     2
 303.855888367 = 326.262775808  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 02 d2 19  |.X.MSDOS5.0.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 28 51 57  |........?....(QW|
00000020  f0 36 03 00 17 03 00 00  00 00 00 00 02 00 00 00  |.6..............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 db 18 09 e8 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
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

### Post by oldfred on 2011-08-15
Boot script looks normal and it looks like you should be able to boot from sdb. 

We have seen a few cases where larger hard drives 500GB & over with one very large / (root) partition have trouble booting. I still think it is a BIOS setting that makes it seem like very old BIOS/drives that could boot only from inside the 137GB limit.

A couple of users tried this and it works and a couple it did not work. Shrink your / partition to be 50GB with gparted. You may have to reinstall grub2's boot loader. Or reinstall with 25GB / and make the rest of the drive /home.

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html)

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by takaya on 2011-10-25
thanks for the advice!

im going to try to reinstall with 25 GB for /
and dedicate the remaining space to my /home directory.

i think this is what you meant =]

---

### Post by takaya on 2012-01-19
i found that if youre unable to remove your internal drive(s), using vmware or another virtualisation software will suffice. 

using vmware, just create a new ubuntu virtual machine using a physical hdd, and point it to the usb hdd in question. 
this way you can install ubuntu to the usb hdd, and it will be bootable off other machines.

---

