---
title: "Ran from usb, but after install now boots busy box"
date: 2011-10-06
forum: Installation &amp; Upgrades
---

### Post by FTBBoy2115 on 2011-10-06
I was able to run fine from my USB thumb drive Ubuntu 11.04 but since I have installed it to the HD it's acting buggy. I think I read that it was a known issue, but not positive. Please help!
It took two attempts to get it this far. The first time, I don't remember exactly what went down, but I ended up having to delete the new partitions and try again.
Here is my bootlog:
Notice the last partition...doesn't look good

Also, earlier when I got the boot OS (either Ubuntu norm, recovery, or windows) option screen, I selected "e" for edit and saw that toward the top I believe it said something like register failed. Not positive on the wording...

                  Boot Info Script 0.60    from 17 May 2011


```
============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.02 debian-20101016 ...........>...r>........8.....0...~.k...~...f...M.f.f....f..8~....>2}
    Boot sector info:   Syslinux looks at sector 1433624 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdb1 starts at sector 
                       0. But according to the info from fdisk, sdb1 starts 
                       at sector 62.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63       112,454       112,392  de Dell Utility
/dev/sda2             112,640    21,084,159    20,971,520   7 NTFS / exFAT / HPFS
/dev/sda3    *     21,084,160   192,938,363   171,854,204   7 NTFS / exFAT / HPFS
/dev/sda4         192,940,030   229,183,487    36,243,458   f W95 Extended (LBA)
/dev/sda5         220,831,744   229,183,487     8,351,744  82 Linux swap / Solaris
/dev/sda6         192,940,032   212,463,615    19,523,584  83 Linux
/dev/sda7         212,465,664   220,829,695     8,364,032  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8006 MB, 8006926336 bytes
247 heads, 62 sectors/track, 1021 cylinders, total 15638528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             62    15,635,593    15,635,532   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       894d145f-2e97-4976-8e7c-f6b8f445e5e8   ext3       
/dev/sda1        07D8-0C07                              vfat       DellUtility
/dev/sda2        74F87172F8713408                       ntfs       RECOVERY
/dev/sda3        32D41E45D41E0C2B                       ntfs       OS
/dev/sda5        5a3f7268-7551-40db-84e6-bed9c2d1acd9   swap       
/dev/sda6        76cd2c50-5b75-49a4-9b34-8e186bae010b   ext4       
/dev/sda7        1bd3c373-dab3-4c04-a404-e03510d0a131   swap       
/dev/sdb1        28DC-F262                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 76cd2c50-5b75-49a4-9b34-8e186bae010b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 76cd2c50-5b75-49a4-9b34-8e186bae010b
set locale_dir=($root)/boot/grub/locale
set lang=en_US
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 76cd2c50-5b75-49a4-9b34-8e186bae010b
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=76cd2c50-5b75-49a4-9b34-8e186bae010b ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 76cd2c50-5b75-49a4-9b34-8e186bae010b
    echo    'Loading Linux 2.6.38-11-generic ...'
    linux    /boot/vmlinuz-2.6.38-11-generic root=UUID=76cd2c50-5b75-49a4-9b34-8e186bae010b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 76cd2c50-5b75-49a4-9b34-8e186bae010b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 76cd2c50-5b75-49a4-9b34-8e186bae010b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda3)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root 32D41E45D41E0C2B
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

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=76cd2c50-5b75-49a4-9b34-8e186bae010b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=1bd3c373-dab3-4c04-a404-e03510d0a131 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 100.288417816 = 107.683868672  boot/grub/core.img                             1
  97.499176025 = 104.688943104  boot/grub/grub.cfg                             1
  97.563381195 = 104.757882880  boot/initrd.img-2.6.38-11-generic              1
  98.297988892 = 105.546661888  boot/vmlinuz-2.6.38-11-generic                 1
  97.563381195 = 104.757882880  initrd.img                                     1
  98.297988892 = 105.546661888  vmlinuz                                        1

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50
ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  c8 aa 20 11 49 24 0d c9  1d 13 40 70 06 80 d3 10  |.. .I$....@p....|
00000010  6e 9b 05 4c 00 5c 01 70  21 00 61 30 04 e0 21 48  |n..L.\.p!.a0..!H|
00000020  25 7f e8 0c 48 61 01 5a  0d f0 0d f0 c2 69 08 bc  |%...Ha.Z.....i..|
00000030  01 00 0e 80 2c 5c 91 77  cb 09 5e 20 11 51 e0 d2  |....,\.w..^ .Q..|
00000040  12 06 86 0d 04 bf fd 7b  b0 4d 53 50 1c 75 5d 9d  |.......{.MSP.u].|
00000050  00 00 00 01 10 42 68 17  40 03 e0 c0 42 ff 30 03  |.....Bh.@...B.0.|
00000060  7e 09 80 0e 06 a0 2b c1  0b fe 5c 81 a0 0c 81 0f  |~.....+...\.....|
00000070  fd 00 0e d0 09 80 0c c4  08 9a 49 f4 71 2e ec 1f  |..........I.q...|
00000080  19 16 18 8c b9 38 20 0d  4a 76 b2 44 93 e8 eb 88  |.....8 .Jv.D....|
00000090  1f 36 37 4e 48 b9 93 6c  8d 01 bb 8d b2 4b d3 11  |.67NH..l.....K..|
000000a0  0a a6 00 97 fa d8 62 15  16 ce f4 9c 7c 90 09 e0  |......b.....|...|
000000b0  3d 4c c0 7a 06 6b b8 ac  64 9a ca 27 20 8d 27 04  |=L.z.k..d..' .'.|
000000c0  d6 90 8a 42 a3 5e e6 08  a0 c0 11 ae 5b 49 ba 46  |...B.^......[I.F|
000000d0  10 60 39 9f 1b 77 55 33  68 c6 00 f3 46 6b a7 8c  |.`9..wU3h...Fk..|
000000e0  92 c2 10 06 8f a1 51 be  89 25 df 65 4a 00 a9 e4  |......Q..%.eJ...|
000000f0  be 4e 1a 59 d1 2f a0 05  28 c1 68 b1 a3 7b 11 62  |.N.Y./..(.h..{.b|
00000100  11 49 4e 32 18 d7 0f 18  4d 12 1c 0c 23 06 3f e0  |.IN2....M...#.?.|
00000110  92 00 66 44 de 03 6e 31  89 f0 4a 4e 92 35 29 46  |..fD..n1..JN.5)F|
00000120  b2 b3 e1 f7 0e 59 0b 0c  4c 26 e0 c2 b0 cf dc 3d  |.....Y..L&.....=|
00000130  56 92 83 3e 36 bf 4f 75  00 41 e6 25 f7 93 8e 97  |V..>6.Ou.A.%....|
00000140  70 c6 37 32 4e 0c c3 e0  dc 84 32 c8 de 03 39 30  |p.72N.....2...90|
00000150  19 28 bf fb de 3a 5d 31  94 4c 2c ae 19 f6 f4 4b  |.(...:]1.L,....K|
00000160  26 28 d8 b2 1a 4e fc 9d  a0 c2 68 4a 79 e1 76 84  |&(...N....hJy.v.|
00000170  aa 1b a8 68 2f 30 b2 d2  34 34 98 50 18 c0 11 c1  |...h/0..44.P....|
00000180  9c e0 34 8d 00 60 b7 03  e1 60 6a 01 04 1a 8c d5  |..4..`...`j.....|
00000190  73 e4 c1 28 fb e6 c6 b4  ea 80 fd db 4e 6e 07 7b  |s..(........Nn.{|
000001a0  a3 ea 4d d8 61 91 90 e2  4f a8 ba cd 92 00 cd 8d  |..M.a...O.......|
000001b0  8a 8b ad 12 b0 4a 6b ab  a0 1d 3c 60 26 9d 00 fe  |.....Jk...<`&...|
000001c0  ff ff 82 fe ff ff 02 98  a9 01 00 70 7f 00 00 fe  |...........p....|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 e8 29 01 00 00  |............)...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by lcman on 2011-10-06
The partitions look messed up! Can't you do a reinstall? I'm guessing you used the usb creator in ubuntu to create a bootable usb, so, use Unetbootin this time! I've had problems with the official usb creator myself. It might or might not be the problem.

When renstalling, delete all of the linux partitions and keep only the msdos ones. Create a / logical with ext4, a 200-500MB primary /boot with ext4 and a swap with 2x your physical memory. You can create a separate /home if you want, doesn't really matter. 

Then, make sure you install the bootloader on the main drive, that is, the drive that is connected to port0/1 in your controller.

That should work!

---

### Post by FTBBoy2115 on 2011-10-08
I can't even do that much. I now can't even boot into a Ubuntu desktop. I've got Ubuntu Rescue on my flash and when it boots, it gives me the options

```
Default
Start of install Ubuntu
Check CD for defects
Memory test
Boot from first hard disk
```If I select the first two, it boots to ubuntu, but without any desktop, just terminal. Reminds me of MS-DOS days.
It'll show the OS loading screen (maroon background with "ubuntu ##" when I think I'm going to get a desktop, it shows full screen terminal:

```
Welcome to Ubuntu 11.04 (GNU/Linux 2.6.38-8-generic i686)

*Documentation: https://help.ubuntu.com/
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$

```

If I select the last "Boot from first hard disk", it boots and says:

```
Busy Box v1.17.1 (Ubuntu 1:1.17-10ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```When I boot into terminal only ubuntu, it seems I don't have full ability like when it's fully installed...don't know if this is to be expected. Tried sudo apt-get install update and it won't/can't do it. 

PLEASE help. I've read so much and can't seem to get anywhere. With this OS version, I've got testdisk available, but I've tried to read the documentation provided from the makers, but it's pretty advanced and a bit confusing for me. I'm not sure exactly what the problem is, so I'm not quite sure how to go about finding the solution.

Note: I'm tried to install as a dual boot, so I have info on the HD I need, or else I would try to reformat the whole thing...
Anyway Please help me determine the problem so I can make progress on this. What tools are on this USB drive that some with this package and how do I use them and actually understand what's going on?

Thanks

---

### Post by FTBBoy2115 on 2011-10-08
I just tried to let the HD to boot again, and I got the other common screen 

```
error: unknown filesystem.
grub rescue>
```

I tried the
```
 rootverify (hd0,0)
``` 
as was mentioned here: [HTML]http://ubuntuforums.org/archive/index.php/t-1359802.html[/HTML]
but I get
```
Unknown command 'rootverify'
grub resuce>
```
I've also tried set root, and I'm not sure if it worked either. It just goes to the next line like I didn't do anything. So I try the next command as in the link I provided, but no good. This is what I get:

```
grub rescue> set root=(hd0,0)
grub rescue> makeactive
Unknown command 'makeactive'
grub rescue>
```

---

### Post by FTBBoy2115 on 2011-10-08
I have found another forum thread [http://ubuntuforums.org/showthread.php?t=1856125](http://ubuntuforums.org/showthread.php?t=1856125)
And it mentioned near the beginning about using the command:
```

sudo fdisk -l && sudo sfdisk -luS

```Quick Q about that, I tried piping it to less text reader( ...sfdisk -luS | less) and I couldn't get it to page up and down. Just put a bunch of ~ ~ ~ down the screen below my partition info when I tried to scroll.

But, anyway back to my BIG problem, when I used the fdisk command mentioned above, I get towards the top 
```
 
/dev/sda1                       1            7           56196          de     Dell Utility
/dev/sda2                       8         1313    10482412          de     HPFS/NFTS
Warning: Partition 2 does not end on cylinder boundary.

```
it repeats that for the rest of my partitions.

---

### Post by FTBBoy2115 on 2011-10-08
OK! So I've finally gotten something right! (Kinda feel like I'm talking to myself here)
I wasn't getting internet w/ my wifi card so I plugged right into my LAN and typed "ifconfig eth0 up" to get it to connect. Got lilo and gparted installed (thought I could make progress w those)

From what I read, I guess the fact that my partitions were saying they were out boundary was irreverent. The locations didn't intersect, although there wasn't any between.

Moving on, I then got grub:

sudo apt-get update
sudo apt-get install grub

I couldn't really make much progress with that since it was legacy grub. "set root=(" didn't' work in this version of grub. 

Determined it's version with:
sudo grub-install -v

So I updated grub:
sudo apt-get install grub-pc

After that, I was kinda unsure where to go next since I couldn't find a fitting next step anywhere. I don't remember doing anything else b4 rebooting.

So it booted right into windows!!! YAY!! Finally!

Btw, I did sudo each time bc it wouldn't' let me elevate permission with su. I couldn't remember/didn't know the password.

Now to figure out what went wrong, and how I can get Ubuntu on my laptop.
I found in my BIOS that my setting for my HD was AHCI. I'd seen that the bios setting can mess with it a little bit, so I switched it to ATA. Not sure if that's right, but gotta try and make progress when my laptop is down for the count.

Ahhh nice to finally see it boot back into SOME operating system :D

---

