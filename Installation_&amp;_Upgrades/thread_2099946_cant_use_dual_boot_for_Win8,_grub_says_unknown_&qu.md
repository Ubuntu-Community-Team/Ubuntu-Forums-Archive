---
title: "cant use dual boot for Win8, grub says: unknown &quot;drivemap&quot;"
date: 2012-12-31
forum: Installation &amp; Upgrades
---

### Post by hmag on 2012-12-31
Hello,

I am new to Ubuntu but not to Linux, since 10+ years I have been using Slackware, Mandrake, Aurox, Gentoo. I came to Ubunto for support and simplified installation procedure.

Thus, I just successfully installed Ubuntu on a new Asus laptop. All hardware well recognized and dual boot working:P.... partially only.:confused:

In fact, I now can only boot Ubuntu and the access to the Windows boot loaders is refused bu grub, it says :
```
error, unknown: "drivemap"
error, invalid efi file path
```Although I won't use Windows alot, I yet need it because I may sometimes need it for win things coming from my work...

I am currently using Ubuntu on my laptop to write this.
It seems I am not so far from the solution, maybe a matter of grub2 setting ... I hope it is not more. Below my mtab if it helps. Early thanks for help. ):P
hmag

```
/dev/sda8 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
/dev/sda1 /boot/efi vfat rw 0 0
/dev/sda9 /home ext4 rw 0 0
/dev/sda7 /windows vfat rw,utf8,umask=007,gid=46 0 0
gvfs-fuse-daemon /home/hmag/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=hmag 0 0

```

---

### Post by darkod on 2012-12-31
If you windows came preinstalled in UEFI mode, did you install ubuntu in uefi mode too?
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2012-12-31
You can convert a BIOS/Legacy install to UEFI install if you installed the 64 bit version of 12.10. You uninstall grub-pc(BIOS) and install grub-efi(UEFI). 
Grub2's os-prober also has a bug in that it finds the old BIOS chain load entries and really needs a chain load to the efi entry. 
       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

I think you manually can do all those fixes, but it is easier just to run Boot-Repair.

Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)

    Does your Asus also have Intel SRT?
       Asus S46CA Ultrabook Problems with Windows Recovery and grub after dual-boot install with Ubuntu 12.04
[http://ubuntuforums.org/showthread.php?t=2098477](http://ubuntuforums.org/showthread.php?t=2098477)
> UEFI boot - In order to get into Windows Recovery, I had to hit F9 before GRUB appeared. My mistake was to wait for GRUB to appear, select one of the 2 working Windows options (Windows UEFI loader or Windows Boot UEFI bootx64.efi.bkp) and by that time I was past the possibility to get into Windows recovery system.

---

### Post by hmag on 2013-01-01
Hey!
Thanks for your quick answer. First of all, happy new year 2013.
Based on the info you provided and the return from bootinfoscript, I  actually installed an UEFI 64 bits version of Gentoo. Bootinfoscript  seems to find all Ok including for Windows8 partitions, thus all the  issue seems related to the 
```
error, unknown:  "drivemap"
```...then possibly leading links to uefi entries to be wrong and then causing the 2nd message :
```
error, invalid efi file path
```??? :confused:

HMag

PS: below , return from bootinfoscript
  ```
Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/ubuntu/grubx64.efi

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount : type de système de fichiers «  » inconnu

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda11: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 têtes, 63 secteurs/piste, 60801 cylindres, total 976773168 secteurs
Unités = secteurs de 1 * 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 4096 octets

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   976,773,167   976,773,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       616,447       614,400 EFI System partition
/dev/sda2         616,448     1,845,247     1,228,800 Windows Recovery Environment (Windows)
/dev/sda3       1,845,248     2,107,391       262,144 Microsoft Reserved Partition (Windows)
/dev/sda4       2,107,392   295,076,141   292,968,750 Data partition (Windows/Linux)
/dev/sda5     392,816,640   490,472,889    97,656,250 Data partition (Windows/Linux)
/dev/sda6     934,830,080   976,773,119    41,943,040 Windows Recovery Environment (Windows)
/dev/sda7     295,077,888   392,816,639    97,738,752 Data partition (Windows/Linux)
/dev/sda8     490,473,472   589,125,631    98,652,160 Data partition (Windows/Linux)
/dev/sda9     589,125,632   745,375,743   156,250,112 Data partition (Windows/Linux)
/dev/sda10    745,375,744   901,625,855   156,250,112 Data partition (Windows/Linux)
/dev/sda11    901,625,856   934,828,031    33,202,176 Swap partition (Linux)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        4496-B46A                              vfat       SYSTEM
/dev/sda10       2fd81e9c-3aab-4ca5-a2a3-d52fd8e078a7   ext4       
/dev/sda11       2a91ad88-9c0c-4f6b-9604-eb7b0d8ae528   swap       
/dev/sda2        FCC6FEADC6FE6774                       ntfs       Recovery
/dev/sda4        46CE64E7CE64D0AB                       ntfs       OS
/dev/sda5        480204070203F8A8                       ntfs       Data
/dev/sda6        86380641380630AB                       ntfs       Restore
/dev/sda7        D6CA-FA16                              vfat       
/dev/sda8        780bfa4d-b3ee-45ca-8fae-794640236822   ext4       
/dev/sda9        37359278-b379-4342-9a20-66d480da90bb   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /boot/efi                vfat       (rw)
/dev/sda7        /windows                 vfat       (rw,utf8,umask=007,gid=46)
/dev/sda8        /                        ext4       (rw,errors=remount-ro)
/dev/sda9        /home                    ext4       (rw)


=========================== sda8/boot/grub/grub.cfg: ===========================

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
  insmod efi_gop
  insmod efi_uga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_gpt
insmod ext2
set root='(hd0,gpt8)'
search --no-floppy --fs-uuid --set=root 780bfa4d-b3ee-45ca-8fae-794640236822
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_gpt
  insmod ext2
  set root='(hd0,gpt8)'
  search --no-floppy --fs-uuid --set=root 780bfa4d-b3ee-45ca-8fae-794640236822
  set locale_dir=($root)/boot/grub/locale
  set lang=fr_FR
  insmod gettext
fi
terminal_output gfxterm
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
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
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
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, avec Linux 3.2.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt8)'
    search --no-floppy --fs-uuid --set=root 780bfa4d-b3ee-45ca-8fae-794640236822
    linux    /boot/vmlinuz-3.2.0-29-generic root=UUID=780bfa4d-b3ee-45ca-8fae-794640236822 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-29-generic
}
menuentry 'Ubuntu, avec Linux 3.2.0-29-generic (mode de dépannage)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt8)'
    search --no-floppy --fs-uuid --set=root 780bfa4d-b3ee-45ca-8fae-794640236822
    echo    'Chargement de Linux 3.2.0-29-generic ...'
    linux    /boot/vmlinuz-3.2.0-29-generic root=UUID=780bfa4d-b3ee-45ca-8fae-794640236822 ro recovery nomodeset 
    echo    'Chargement du disque mémoire initial ...'
    initrd    /boot/initrd.img-3.2.0-29-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt8)'
    search --no-floppy --fs-uuid --set=root 780bfa4d-b3ee-45ca-8fae-794640236822
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt8)'
    search --no-floppy --fs-uuid --set=root 780bfa4d-b3ee-45ca-8fae-794640236822
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_gpt
    insmod ntfs
    set root='(hd0,gpt2)'
    search --no-floppy --fs-uuid --set=root FCC6FEADC6FE6774
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 8 (loader) (on /dev/sda4)" --class windows --class os {
    insmod part_gpt
    insmod ntfs
    set root='(hd0,gpt4)'
    search --no-floppy --fs-uuid --set=root 46CE64E7CE64D0AB
    drivemap -s (hd0) ${root}
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

=============================== sda8/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=780bfa4d-b3ee-45ca-8fae-794640236822 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=4496-B46A  /boot/efi       vfat    defaults        0       1
# /home was on /dev/sda9 during installation
UUID=37359278-b379-4342-9a20-66d480da90bb /home           ext4    defaults        0       2
# /windows was on /dev/sda7 during installation
UUID=D6CA-FA16  /windows        vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda11 during installation
UUID=2a91ad88-9c0c-4f6b-9604-eb7b0d8ae528 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda8: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-29-generic               2
               =                boot/vmlinuz-3.2.0-29-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 02 08 5e 1b  |.X.MSDOS5.0...^.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 60 09 00 51 02 00 00  00 00 00 00 02 00 00 00  |.`..Q...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 6a b4 96 44 4e  4f 20 4e 41 4d 45 20 20  |..)j..DNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 56 40 88 4e 02 8a 56  |{......|.V@.N..V|
00000070  40 b4 41 bb aa 55 cd 13  72 10 81 fb 55 aa 75 0a  |@.A..U..r...U.u.|
00000080  f6 c1 01 74 05 fe 46 02  eb 2d 8a 56 40 b4 08 cd  |...t..F..-.V@...|
00000090  13 73 05 b9 ff ff 8a f1  66 0f b6 c6 40 66 0f b6  |.s......f...@f..|
000000a0  d1 80 e2 3f f7 e2 86 cd  c0 ed 06 41 66 0f b7 c9  |...?.......Af...|
000000b0  66 f7 e1 66 89 46 f8 83  7e 16 00 75 39 83 7e 2a  |f..f.F..~..u9.~*|
000000c0  00 77 33 66 8b 46 1c 66  83 c0 0c bb 00 80 b9 01  |.w3f.F.f........|
000000d0  00 e8 2c 00 e9 a8 03 a1  f8 7d 80 c4 7c 8b f0 ac  |..,......}..|...|
000000e0  84 c0 74 17 3c ff 74 09  b4 0e bb 07 00 cd 10 eb  |..t.<.t.........|
000000f0  ee a1 fa 7d eb e4 a1 7d  80 eb df 98 cd 16 cd 19  |...}...}........|
00000100  66 60 80 7e 02 00 0f 84  20 00 66 6a 00 66 50 06  |f`.~.... .fj.fP.|
00000110  53 66 68 10 00 01 00 b4  42 8a 56 40 8b f4 cd 13  |Sfh.....B.V@....|
00000120  66 58 66 58 66 58 66 58  eb 33 66 3b 46 f8 72 03  |fXfXfXfX.3f;F.r.|
00000130  f9 eb 2a 66 33 d2 66 0f  b7 4e 18 66 f7 f1 fe c2  |..*f3.f..N.f....|
00000140  8a ca 66 8b d0 66 c1 ea  10 f7 76 1a 86 d6 8a 56  |..f..f....v....V|
00000150  40 8a e8 c0 e4 06 0a cc  b8 01 02 cd 13 66 61 0f  |@............fa.|
00000160  82 74 ff 81 c3 00 02 66  40 49 75 94 c3 42 4f 4f  |.t.....f@Iu..BOO|
00000170  54 4d 47 52 20 20 20 20  00 00 00 00 00 00 00 00  |TMGR    ........|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 44 69  |..............Di|
000001b0  73 6b 20 65 72 72 6f 72  ff 0d 0a 50 72 65 73 73  |sk error...Press|
000001c0  20 61 6e 79 20 6b 65 79  20 74 6f 20 72 65 73 74  | any key to rest|
000001d0  61 72 74 0d 0a 00 00 00  00 00 00 00 00 00 00 00  |art.............|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  ac 01 b9 01 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

hmag@asus2:~/Téléchargements/BootInfoScript$
```

---

### Post by hmag on 2013-01-01
Hello,

Finally, boot-repair, as claimed by the excellent name of this excellent piece of code, did it perfectly by re-installing grub and fixing efi stuff. :p:p:p

boot-repair provided : [http://paste.ubuntu.com/1484640/](http://paste.ubuntu.com/1484640/)

I now just have to learn about grub2 to simplify my dual boot menu, and dig into apt-get and Ubuntu after many years of source code compilation and risky cpu overheating using 'portage' and 'emerge' in the gentoo source distrib ... ;-)

I will mark this thread as SOLVED.
And thanks again for the great help.
HMag):P

---

### Post by oldfred on 2013-01-01
You can easily turn off os-prober, so you do not get the incorrect entries. The correct one's are in 25_custom, so they will stay there. You can also turn off parts of the script.

       In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober

I prefer to do things manually but I was forced to learn as there were no scripts and little info on grub2 when it first came out, drs305 was one of the first to post the ways to customize & use grub2:
       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
Older thread
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

Some suggest Grub Customizer, but it has its own way of changing things around.
       New Grub Customizer works with 12.10
[http://www.webupd8.org/2012/09/grub-customizer-30-released.html](http://www.webupd8.org/2012/09/grub-customizer-30-released.html)

            The Grub 2 Guide - drs305 also link to grub customizer
Ubuntu Community Documentation site
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by hmag on 2013-01-03
Thanks OldFred for all these advises !
Before you provided those, I already decided to manually customize grub.cfg.
The comments inserted by automatic generation of grub.cfg are very helpful to understand its construction process. Thus relatively to /etc/default/grub/30_os-prober I changed all contents to comments ;-) - nevertheless removing the x bit is probably a better and more esteathic solution !
Regards
HMag

---

