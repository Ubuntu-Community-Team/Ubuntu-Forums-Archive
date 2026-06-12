---
title: "Installed Ubuntu 11.04 alongside Windows 7 and Ubuntu does not boot"
date: 2011-05-17
forum: Installation &amp; Upgrades
---

### Post by tplanter2011 on 2011-05-17
Hi all,

I installed Ubuntu 11.04 last night and when I reboot, my system goes directly to Windows 7.  I checked this forum for similar problems and downloaded the boot info script.  Here are the results.txt.   

Thanks in advance for your help!

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 7 for /boot/grub.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.

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
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920    24,080,383    23,998,464   7 NTFS / exFAT / HPFS
/dev/sda3          24,080,384 1,953,521,663 1,929,441,280   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   507,521,362   507,521,300   c W95 FAT32 (LBA)
/dev/sdb2         507,523,070   625,141,759   117,618,690   5 Extended
/dev/sdb5         616,837,120   625,141,759     8,304,640  82 Linux swap / Solaris
/dev/sdb6         608,532,480   616,830,975     8,298,496  82 Linux swap / Solaris
/dev/sdb7         507,523,072   600,225,791    92,702,720  83 Linux
/dev/sdb8         600,227,840   608,526,335     8,298,496  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3030-3030                              vfat       DellUtility
/dev/sda2        A8903D10903CE68A                       ntfs       RECOVERY
/dev/sda3        38AE3FE4AE3F98F8                       ntfs       OS
/dev/sdb1                                               vfat       
/dev/sdb5        a4957aa0-d0ae-43e2-b4c6-1d0ace52c7d2   swap       
/dev/sdb6        3faea9d2-910e-4556-a35c-1406af2d0826   swap       
/dev/sdb7        813bcf78-26a9-4de2-a138-08ef7ceed34b   ext4       
/dev/sdb8                                               swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sdb7/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sdb,msdos7)'
search --no-floppy --fs-uuid --set=root 813bcf78-26a9-4de2-a138-08ef7ceed34b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdb,msdos7)'
search --no-floppy --fs-uuid --set=root 813bcf78-26a9-4de2-a138-08ef7ceed34b
set locale_dir=($root)/boot/grub/locale
set lang=en_CA
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos7)'
    search --no-floppy --fs-uuid --set=root 813bcf78-26a9-4de2-a138-08ef7ceed34b
    linux    /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=813bcf78-26a9-4de2-a138-08ef7ceed34b ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos7)'
    search --no-floppy --fs-uuid --set=root 813bcf78-26a9-4de2-a138-08ef7ceed34b
    echo    'Loading Linux 2.6.38-8-generic-pae ...'
    linux    /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=813bcf78-26a9-4de2-a138-08ef7ceed34b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos7)'
    search --no-floppy --fs-uuid --set=root 813bcf78-26a9-4de2-a138-08ef7ceed34b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos7)'
    search --no-floppy --fs-uuid --set=root 813bcf78-26a9-4de2-a138-08ef7ceed34b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root A8903D10903CE68A
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

=============================== sdb7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb7       /               ext4    errors=remount-ro 0       1
/dev/sdb8       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 252.143894196 = 270.737444864  boot/grub/core.img                             1
 268.305988312 = 288.091361280  boot/grub/grub.cfg                             1
 247.103713989 = 265.325592576  boot/initrd.img-2.6.38-8-generic-pae           2
 246.455505371 = 264.629583872  boot/vmlinuz-2.6.38-8-generic-pae              1
 247.103713989 = 265.325592576  initrd.img                                     2
 246.455505371 = 264.629583872  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb2

00000000  bd c1 80 4d b7 27 4e 9d  3a 74 e9 d3 d1 d1 b4 88  |...M.'N.:t......|
00000010  e1 a4 75 54 3f 0f c2 f0  54 6f 78 48 24 20 fd 3a  |..uT?...ToxH$ .:|
00000020  38 50 17 0d de 24 30 54  1f 7a ec 4a 19 c4 45 42  |8P...$0T.z.J..EB|
00000030  48 28 10 42 3d 15 cd aa  0d e1 20 1d 8b 1d 11 04  |H(.B=..... .....|
00000040  e4 8a 39 11 11 d4 87 28  87 46 f7 bc 24 03 61 77  |..9....(.F..$.aw|
00000050  a7 44 10 67 d3 a7 4e 9d  3a 74 87 26 92 fb 49 30  |.D.g..N.:t.&..I0|
00000060  1f 05 c2 e4 3c 7f f5 43  a1 b0 88 22 d5 8f 0b 04  |....<..C..."....|
00000070  10 ae 3a 90 45 42 fa 74  97 0d c1 c1 bd eb e0 c0  |..:.EB.t........|
00000080  0d 8e 38 18 1b c2 20 15  47 9e 14 0e 93 78 5c 6f  |..8... .G....x\o|
00000090  7b d2 7d 34 d0 0e 00 e4  e3 9c 18 1b 82 e3 73 9c  |{.}4..........s.|
000000a0  88 50 05 6a 5b 24 9d 20  7b 07 e9 d3 a7 4e 9d 11  |.P.j[$. {....N..|
000000b0  d3 49 03 a0 37 0f 81 47  2c 72 93 c7 72 1f 0d 86  |.I..7..G,r..r...|
000000c0  84 6d 3b 0f f8 f8 70 5e  38 e0 c0 61 87 27 d1 0d  |.m;...p^8..a.'..|
000000d0  cd 82 43 78 24 18 09 8e  57 c4 01 f8 68 30 11 6d  |..Cx$...W...h0.m|
000000e0  bb 94 4c d9 a5 92 cb 2a  bb a7 82 c2 4c 89 03 63  |..L....*....L..c|
000000f0  79 f3 c8 91 1c 45 06 15  06 1d 28 96 10 4e 9d 3a  |y....E....(..N.:|
00000100  74 e9 c2 a0 4c 95 3e 71  42 50 31 d4 20 82 e9 e3  |t...L.>qBP1. ...|
00000110  e0 b0 49 a7 9d 48 20 41  ea 7f d1 b0 8e 8e 90 5e  |..I..H A.......^|
00000120  06 a9 30 a2 50 61 41 a8  2e 98 a4 3b 3c 97 0a 04  |..0.PaA....;<...|
00000130  82 17 a2 48 39 06 05 23  a8 d9 4b 48 a7 4e 9c 22  |...H9..#..KH.N."|
00000140  38 7d 22 84 93 60 44 04  90 68 85 ca 7c 37 7d 80  |8}"..`D..h..|7}.|
00000150  c8 72 e7 a4 10 70 94 9f  fd 34 13 a7 4e 8f a3 a3  |.r...p...4..N...|
00000160  a3 a4 15 c1 ba 82 c4 1f  87 63 e1 80 c5 e9 60 5d  |.........c....`]|
00000170  42 a9 25 52 4d 04 e9 d2  c5 2f b2 1c 1b 9c 1c 1b  |B.%RM..../......|
00000180  9c 91 22 09 62 88 2f 02  68 a0 36 0b 24 ae 50 a8  |..".b./.h.6.$.P.|
00000190  16 8e d2 b3 29 d3 fe 8f  4e 9d 21 40 49 7d 7e 8e  |....)...N.!@I}~.|
000001a0  8d 84 70 50 70 f0 7c 01  76 65 ce 73 82 23 7a 54  |..pPp.|.ve.s.#zT|
000001b0  0c 53 61 2c 52 85 36 13  a5 0a 74 9a 41 3a 00 fe  |.Sa,R.6...t.A:..|
000001c0  ff ff 82 fe ff ff 02 00  84 06 00 b8 7e 00 00 fe  |............~...|
000001d0  ff ff 05 fe ff ff 02 30  05 06 00 b8 7e 00 00 00  |.......0....~...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
unlzma: Decoder error

---

### Post by oldfred on 2011-05-17
Welcome to the forum.

First time I have seen boot script .60.

I do not see how you are booting windows directly. You have grub2 in sda's MBR and it should boot Ubuntu in sdb7. An install in sdb's MBR was for one of your previous installs and will not boot anything as sdb6 is one of 3 swaps. Are you booting sda or sdb?

For some reason sdb8 is not showing a UUID and you are using /dev/sdxy as the fstab's rather than UUIDs. Did you edit fstab as it normally shows UUIDs.

I would from Ubuntu in sdb7 install grub2's boot loader to the MBR of sdb and set BIOS to boot sdb. I like to have different systems on different drives like you do but also have that systems's boot loader in the MBR of the drive so you can boot from BIOS. But use grub2 to boot normally as it lets you boot windows and Ubuntu. You also will want to update where grub's bootloader reinstalls by default so updates install to sdb not sda.

#reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

You can then install a windows boot loader to the MBR of sda. If you have a windows disk you can run the BootRec.exe /fixMBR   from a windows repair console or install lilo's boot loader to the MBR of sda as it works just like windows in looking for a partition with the boot flag and jumping to that partition for more boot code.

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing testdisk with Synaptic.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

---

### Post by tplanter2011 on 2011-05-17
Thanks so much for your response.   I'm a total newbie, though, and don't understand your answer :confused:.
This was the result of installing Ubuntu directly from the CD.

Is there a simple, first step I can try?

Thanks again,

---

### Post by oldfred on 2011-05-17
Are you booting windows as you say. I do not see how.

If in BIOS you set sda (your 1TB drive) as the boot drive does it boot Ubuntu? Or use your one time boot key (f12 on my computer) to select sda does it boot Ubuntu?

---

### Post by djRif on 2011-05-17
dude some simple suggestions to try first...

just some basic information queries here: when you start up do you even see the GRUB menu? Pressing the ESC button before windows starts loading can halt the process and you can see if Grub is actually there...

Second.. Its possible that the grub loader is on an additional or secondary drive.. (just speculating) if you have more than one physical drive its possible that the boot loader was installed on the secondary drive... If you do have more than one drive, go into BIOS setup and select the second drive as bootup and see what happens.. Just some suggestions (I am a bit of a noob myself.

I have to say i hate grub... every time I have installed Ubuntu (i dual boot into win7 and Ubuntu) there is some kind of minor problem... sigh

---

### Post by tplanter2011 on 2011-05-17
Thanks so much for your responses...

My computer ended up not booting at all... I got a message saying Error: no such device grub rescue and I fixed it following the instructions on this thread [http://ubuntuforums.org/showthread.php?t=1549194](http://ubuntuforums.org/showthread.php?t=1549194)

My computer now, as it did before, just boots directly to Windows 7 as if I hadn't installed Ubuntu at all.  If I press F12 and boot from the hard drive, I don't get the Ubuntu option.  

I had previously installed Ubuntu inside Windows and it worked perfectly this way... but I had no access to my C: drive.

and no, I don't see the grub menu, and only have one hard drive option to boot from when I press F12

---

### Post by oldfred on 2011-05-17
If you only have one boot drive which I understand some Dell's are set up that way, you have to have grub2 installed in that drive. Is that drive sda 1000GB or or sdb 320GB?

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD,and you want grub2's bootloader in drive sda's MBR:
sudo mount /dev/sdb7 /mnt
#If grub 1.99 with Natty uses boot not root
sudo grub-install --boot-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --boot-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

