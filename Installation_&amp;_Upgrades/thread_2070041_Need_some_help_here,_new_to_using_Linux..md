---
title: "Need some help here, new to using Linux."
date: 2012-10-11
forum: Installation &amp; Upgrades
---

### Post by Redstiza on 2012-10-11
I am very new to using any kind of Linux based system.  The HP Pavilion dv2000 I had bought from someone else (Big mistake, I know) had an unofficial version of Windows 7.  It stopped booting up that ISO completely one day so I needed a temporary fix to my problem until I can finish getting the parts needed for a custom built desktop that won't be finished for a while.  I found that a new ISO would be better and I remember trying out Ubuntu a few years ago and enjoyed it.  Here's where the problem starts:

I have tried installing with a CD to the main 150GB hard drive in order   to delete everything on there and start fresh, I tried to search for   grub in terminal using grub> find/boot/grub/state1, but was told that   program 'grub' is not installed.  It says to type sudo apt-get install   grub.  I did that and restarted the computer, but it still won't boot   without the CD. The screen just displays an error:

Error: no such device:  84de2031-fbf6-435a-b14b-b024638f4ed5
grub rescue>

Putting the CD in just lets me start in live  mode, or install again.   Switching back to live mode and opening  terminal to try and locate  grub, I am told again that it does not exist  and tells me i can install  it again.  I don't think grub is being put on  my 150G HDD, but instead  the CD for some reason.

I do not know much about commands and code, if someone could just give me a basic step by step walk through on how to fix this it would be greatly appreciated.

---

### Post by Bucky Ball on 2012-10-11
*Thread Moved to** Installtions & Upgrades***


Welcome,

Please note for future reference; a desciptive thread title will get you far! You can edit this one to something more descriptive by editing the first post then click 'Go Advanced'.

The CD is not writable so that rules that out. From the LiveCD you can install Boot Repair, though, from Software Centre (I think) or if not, all details here:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

That would be quickest and easiest if it works. If not, then we dig on ...

BTW, you want grub on sda. Just that, not sda1, 2 etc. If you do a manual partition (Something Else) I think that is where you check where grub is going. It is sometime during install.

---

### Post by Redstiza on 2012-10-11
> **Bucky Ball said:**
> *Thread Moved to** Installtions & Upgrades***


Welcome,

Please note for future reference; a desciptive thread title will get you far! You can edit this one to something more descriptive by editing the first post then click 'Go Advanced'.

The CD is not writable so that rules that out. From the LiveCD you can install Boot Repair, though, from Software Centre (I think) or if not, all details here:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

That would be quickest and easiest if it works. If not, then we dig on ...

BTW, you want grub on sda. Just that, not sda1, 2 etc. If you do a manual partition (Something Else) I think that is where you check where grub is going. It is sometime during install.

Thanks for replying so quickly, I did not know where to post this in so thanks for moving it also.  

So what you're saying is that I need to write another CD for boot repair, it's not on the CD where the installation files are?  Just wanted to make sure I don't mind doing that.

I'll give that a try and see what happens.

---

### Post by Redstiza on 2012-10-11
I tried to use Boot Repair, it finished and said it was successful, but I still get the error: no such device thing when trying to boot.

---

### Post by oldfred on 2012-10-12
From Boot-Repair run the BootInfo report and post the link it creates for the report in pastebin.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by Redstiza on 2012-10-12
I can't connect to wireless on that laptop when the boot repair program is running, is that needed?  It asked me to when I tried to run the repair part the first time.

---

### Post by YannBuntu on 2012-10-12
Hi
You can run Boot-Repair without internet, but then it will display the BootInfo summary in a text viewer, so you will have to copy its content and paste it in this thread between [ CODE ] tags.

---

### Post by Redstiza on 2012-10-12
Alright then, here's what shows up in the text opened by Bootinfo:

```
Boot Info Script 0.61.full + Boot-Repair extra info      [Boot-Info September 18th 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   309,567,487   309,565,440  83 Linux
/dev/sda2         309,569,534   312,580,095     3,010,562   5 Extended
/dev/sda5         309,569,536   312,580,095     3,010,560  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        bb80684f-abb8-4331-92ad-54244f467422   ext4       
/dev/sda5        6dbc8895-a235-42b5-9117-b88fe134cca5   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sr0         /live/image              iso9660    (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root bb80684f-abb8-4331-92ad-54244f467422
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root bb80684f-abb8-4331-92ad-54244f467422
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
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
menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root bb80684f-abb8-4331-92ad-54244f467422
    linux    /boot/vmlinuz-3.2.0-29-generic-pae root=UUID=bb80684f-abb8-4331-92ad-54244f467422 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-29-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root bb80684f-abb8-4331-92ad-54244f467422
    echo    'Loading Linux 3.2.0-29-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-29-generic-pae root=UUID=bb80684f-abb8-4331-92ad-54244f467422 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-29-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root bb80684f-abb8-4331-92ad-54244f467422
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root bb80684f-abb8-4331-92ad-54244f467422
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
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=bb80684f-abb8-4331-92ad-54244f467422 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6dbc8895-a235-42b5-9117-b88fe134cca5 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1
            ?? = ??             boot/grub/grub.cfg                             1
            ?? = ??             boot/initrd.img-3.2.0-29-generic-pae           2
            ?? = ??             boot/vmlinuz-3.2.0-29-generic-pae              1
            ?? = ??             initrd.img                                     2
            ?? = ??             vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  20 62 b9 d5 18 38 f2 cc  6c cc d4 78 55 23 cc 38  | b...8..l..xU#.8|
00000010  8f 70 96 cd cb 5b 39 f0  4e ff 94 29 51 b6 07 13  |.p...[9.N..)Q...|
00000020  d3 69 2c 2b ef 87 27 70  84 2a d3 78 83 8c 1a 57  |.i,+..'p.*.x...W|
00000030  9f bf 65 1f c0 5a df dd  8e 43 a7 58 0b 75 9b f3  |..e..Z...C.X.u..|
00000040  18 58 ff 70 74 56 0b af  71 6e 0e d8 29 6a 22 4b  |.X.ptV..qn..)j"K|
00000050  c8 f4 5d 14 3c 3a 5e e4  06 83 74 ca 6b 7b 91 e4  |..].<:^...t.k{..|
00000060  23 ed a5 a7 f3 c2 41 b0  41 1f 87 ac 61 81 85 ef  |#.....A.A...a...|
00000070  66 16 fe 1d f2 f6 85 46  20 5c 22 df 00 2b e9 34  |f......F \"..+.4|
00000080  58 96 69 1c 49 84 cc e2  7a 34 ea 67 10 68 6b 67  |X.i.I...z4.g.hkg|
00000090  c0 c3 9b ef b3 d5 7e 1d  9f 1c 51 7d db ac f7 58  |......~...Q}...X|
000000a0  e7 df 06 50 8f 44 50 b2  b5 b3 ea c9 27 a7 6e a9  |...P.DP.....'.n.|
000000b0  90 e0 8e 13 58 40 c9 ed  c0 84 1e a8 5a 6f 82 27  |....X@......Zo.'|
000000c0  3d 7a d5 f2 d8 9b ed c0  c7 92 5d 3a cb 41 ef 73  |=z........]:.A.s|
000000d0  4f 07 51 e7 07 33 9d f3  2c 18 47 ad 6a b5 9f 02  |O.Q..3..,.G.j...|
000000e0  c9 9b 45 ce 5a 1b 6c 3d  ae 1f d5 7b 2e 26 1b d5  |..E.Z.l=...{.&..|
000000f0  09 fa 1b 75 f4 a0 6c 8b  be cb 9a c1 e1 69 df 6f  |...u..l......i.o|
00000100  cf 72 cc db 5c 5a ed 7a  0d 80 b0 97 b1 9e 94 a1  |.r..\Z.z........|
00000110  70 d3 7c cd 0b ce c0 10  eb 12 88 bb 60 8f c1 5b  |p.|.........`..[|
00000120  0f 6d 49 7f d6 83 19 02  9f c7 a0 35 f2 a2 21 da  |.mI........5..!.|
00000130  44 0f c6 e1 d3 06 12 3f  e5 76 56 0f 09 b8 3c 20  |D......?.vV...< |
00000140  3b d6 4b a4 5d ff fa ac  6b 2a 39 be a7 59 46 6e  |;.K.]...k*9..YFn|
00000150  21 fd d9 4e ac 1a 27 ce  69 5a 37 a2 20 19 f1 72  |!..N..'.iZ7. ..r|
00000160  5b 14 0a e0 37 c2 07 e9  0c 2e 16 7e 9f 3d b4 b9  |[...7......~.=..|
00000170  0e db 8d 2b e1 40 9b 56  de fb ca 7c 0d de 0c 76  |...+.@.V...|...v|
00000180  36 09 c0 10 53 bd 4c 1c  f8 41 9e 93 a5 73 84 ea  |6...S.L..A...s..|
00000190  7d 1b 83 eb 53 af 5e 86  35 28 c0 46 6c 3f 0c 19  |}...S.^.5(.Fl?..|
000001a0  18 64 52 36 c6 65 57 6d  9e 06 11 d6 8b 5e e5 48  |.dR6.eWm.....^.H|
000001b0  d8 6d da d7 64 1e 12 0b  bd a5 c4 d3 a9 0c 00 fe  |.m..d...........|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 f0 2d 00 00 00  |............-...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

File descriptor 7 (pipe:[5527]) leaked on lvscan invocation. Parent PID 8235: bash
File descriptor 8 (pipe:[5527]) leaked on lvscan invocation. Parent PID 8235: bash
  No volume groups found
mdadm: No arrays found in config file or automatically

ADDITIONAL INFORMATION :
=================== log of boot-repair 2012-10-12__16h42 ===================
boot-repair version : 3.193-0ppa22~lucid
boot-sav version : 3.193-0ppa39~lucid
glade2script-gtk2 version : 0.0.1-0ppa4~lucid
boot-sav-nonfree version :
Please connect internet. Then close this window.
/usr/share/boot-sav/gui-update.sh: line 77: add-apt-repository: command not found
/usr/share/boot-sav/gui-update.sh: line 77: add-apt-repository: command not found
deb [http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu](http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu) lucid main
/usr/share/boot-sav/gui-update.sh: line 77: add-apt-repository: command not found
/usr/share/boot-sav/gui-update.sh: line 77: add-apt-repository: command not found
deb [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) lucid main
W: Failed to fetch [http://cdn.debian.net/debian/dists/squeeze/Release.gpg](http://cdn.debian.net/debian/dists/squeeze/Release.gpg)  Could not resolve 'cdn.debian.net'

W: Failed to fetch [http://cdn.debian.net/debian/dists/squeeze/main/i18n/Translation-en.bz2](http://cdn.debian.net/debian/dists/squeeze/main/i18n/Translation-en.bz2)  Could not resolve 'cdn.debian.net'

W: Failed to fetch [http://cdn.debian.net/debian/dists/squeeze/main/i18n/Translation-en_US.bz2](http://cdn.debian.net/debian/dists/squeeze/main/i18n/Translation-en_US.bz2)  Could not resolve 'cdn.debian.net'

W: Failed to fetch [http://security.debian.org/dists/squeeze/updates/Release.gpg](http://security.debian.org/dists/squeeze/updates/Release.gpg)  Could not resolve 'security.debian.org'

W: Failed to fetch [http://security.debian.org/dists/squeeze/updates/main/i18n/Translation-en.bz2](http://security.debian.org/dists/squeeze/updates/main/i18n/Translation-en.bz2)  Could not resolve 'security.debian.org'

W: Failed to fetch [http://security.debian.org/dists/squeeze/updates/main/i18n/Translation-en_US.bz2](http://security.debian.org/dists/squeeze/updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.debian.org'

W: Failed to fetch [http://cdn.debian.net/debian/dists/squeeze-updates/Release.gpg](http://cdn.debian.net/debian/dists/squeeze-updates/Release.gpg)  Could not resolve 'cdn.debian.net'

W: Failed to fetch [http://cdn.debian.net/debian/dists/squeeze-updates/main/i18n/Translation-en.bz2](http://cdn.debian.net/debian/dists/squeeze-updates/main/i18n/Translation-en.bz2)  Could not resolve 'cdn.debian.net'

W: Failed to fetch [http://cdn.debian.net/debian/dists/squeeze-updates/main/i18n/Translation-en_US.bz2](http://cdn.debian.net/debian/dists/squeeze-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'cdn.debian.net'

W: Failed to fetch [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/lucid/Release.gpg](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/lucid/Release.gpg)  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/lucid/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/lucid/main/i18n/Translation-en.bz2)  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch [http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/lucid/Release.gpg](http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/lucid/Release.gpg)  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch [http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/lucid/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/lucid/main/i18n/Translation-en.bz2)  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch [http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Could not resolve 'ppa.launchpad.net'

W: Some index files failed to download, they have been ignored, or old ones used instead.

0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 63 not upgraded.
WARNING: The following packages cannot be authenticated!
os-uninstaller
Err [http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/](http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/) lucid/main os-uninstaller all 3.18-0ppa13~lucid
Could not resolve 'ppa.launchpad.net'
Failed to fetch [http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/pool/main/o/os-uninstaller/os-uninstaller_3.18-0ppa13~lucid_all.deb](http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/pool/main/o/os-uninstaller/os-uninstaller_3.18-0ppa13~lucid_all.deb)  Could not resolve 'ppa.launchpad.net'
E: Some files failed to download

0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 63 not upgraded.
WARNING: The following packages cannot be authenticated!
boot-repair
Err [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/) lucid/main boot-repair all 3.193-0ppa22~lucid
Could not resolve 'ppa.launchpad.net'
Failed to fetch [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/pool/main/b/boot-repair/boot-repair_3.193-0ppa22~lucid_all.deb](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/pool/main/b/boot-repair/boot-repair_3.193-0ppa22~lucid_all.deb)  Could not resolve 'ppa.launchpad.net'
E: Some files failed to download
File descriptor 7 (pipe:[5527]) leaked on lvs invocation. Parent PID 3599: /bin/sh
File descriptor 8 (pipe:[5527]) leaked on lvs invocation. Parent PID 3599: /bin/sh
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 18.07.2012, squeeze, Debian, i686)
CPU op-mode(s):        64-bit
initrd=/live/initrd.img boot=live config   quiet BOOT_IMAGE=/live/vmlinuz

=================== os-prober:
/dev/sda1:Ubuntu 12.04.1 LTS (12.04):Ubuntu:linux

=================== blkid:
/dev/sda1: UUID="bb80684f-abb8-4331-92ad-54244f467422" TYPE="ext4"
/dev/sda5: UUID="6dbc8895-a235-42b5-9117-b88fe134cca5" TYPE="swap"
/dev/loop0: TYPE="squashfs"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

0+1 records in
0+1 records out
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.


=================== sda1/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel ofBoot Info Script 0.61.full + Boot-Repair extra info      [Boot-Info September 18th 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   309,567,487   309,565,440  83 Linux
/dev/sda2         309,569,534   312,580,095     3,010,562   5 Extended
/dev/sda5         309,569,536   312,580,095     3,010,560  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        bb80684f-abb8-4331-92ad-54244f467422   ext4       
/dev/sda5        6dbc8895-a235-42b5-9117-b88fe134cca5   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sr0         /live/image              iso9660    (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set=root bb80684f-abb8-4331-92ad-54244f467422
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root bb80684f-abb8-4331-92ad-54244f467422
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
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
menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root bb80684f-abb8-4331-92ad-54244f467422
    linux    /boot/vmlinuz-3.2.0-29-generic-pae root=UUID=bb80684f-abb8-4331-92ad-54244f467422 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-29-generic-pae
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root bb80684f-abb8-4331-92ad-54244f467422
    echo    'Loading Linux 3.2.0-29-generic-pae ...'
    linux    /boot/vmlinuz-3.2.0-29-generic-pae root=UUID=bb80684f-abb8-4331-92ad-54244f467422 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-29-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root bb80684f-abb8-4331-92ad-54244f467422
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root bb80684f-abb8-4331-92ad-54244f467422
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
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=bb80684f-abb8-4331-92ad-54244f467422 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6dbc8895-a235-42b5-9117-b88fe134cca5 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1
            ?? = ??             boot/grub/grub.cfg                             1
            ?? = ??             boot/initrd.img-3.2.0-29-generic-pae           2
            ?? = ??             boot/vmlinuz-3.2.0-29-generic-pae              1
            ?? = ??             initrd.img                                     2
            ?? = ??             vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  20 62 b9 d5 18 38 f2 cc  6c cc d4 78 55 23 cc 38  | b...8..l..xU#.8|
00000010  8f 70 96 cd cb 5b 39 f0  4e ff 94 29 51 b6 07 13  |.p...[9.N..)Q...|
00000020  d3 69 2c 2b ef 87 27 70  84 2a d3 78 83 8c 1a 57  |.i,+..'p.*.x...W|
00000030  9f bf 65 1f c0 5a df dd  8e 43 a7 58 0b 75 9b f3  |..e..Z...C.X.u..|
00000040  18 58 ff 70 74 56 0b af  71 6e 0e d8 29 6a 22 4b  |.X.ptV..qn..)j"K|
00000050  c8 f4 5d 14 3c 3a 5e e4  06 83 74 ca 6b 7b 91 e4  |..].<:^...t.k{..|
00000060  23 ed a5 a7 f3 c2 41 b0  41 1f 87 ac 61 81 85 ef  |#.....A.A...a...|
00000070  66 16 fe 1d f2 f6 85 46  20 5c 22 df 00 2b e9 34  |f......F \"..+.4|
00000080  58 96 69 1c 49 84 cc e2  7a 34 ea 67 10 68 6b 67  |X.i.I...z4.g.hkg|
00000090  c0 c3 9b ef b3 d5 7e 1d  9f 1c 51 7d db ac f7 58  |......~...Q}...X|
000000a0  e7 df 06 50 8f 44 50 b2  b5 b3 ea c9 27 a7 6e a9  |...P.DP.....'.n.|
000000b0  90 e0 8e 13 58 40 c9 ed  c0 84 1e a8 5a 6f 82 27  |....X@......Zo.'|
000000c0  3d 7a d5 f2 d8 9b ed c0  c7 92 5d 3a cb 41 ef 73  |=z........]:.A.s|
000000d0  4f 07 51 e7 07 33 9d f3  2c 18 47 ad 6a b5 9f 02  |O.Q..3..,.G.j...|
000000e0  c9 9b 45 ce 5a 1b 6c 3d  ae 1f d5 7b 2e 26 1b d5  |..E.Z.l=...{.&..|
000000f0  09 fa 1b 75 f4 a0 6c 8b  be cb 9a c1 e1 69 df 6f  |...u..l......i.o|
00000100  cf 72 cc db 5c 5a ed 7a  0d 80 b0 97 b1 9e 94 a1  |.r..\Z.z........|
00000110  70 d3 7c cd 0b ce c0 10  eb 12 88 bb 60 8f c1 5b  |p.|.........`..[|
00000120  0f 6d 49 7f d6 83 19 02  9f c7 a0 35 f2 a2 21 da  |.mI........5..!.|
00000130  44 0f c6 e1 d3 06 12 3f  e5 76 56 0f 09 b8 3c 20  |D......?.vV...< |
00000140  3b d6 4b a4 5d ff fa ac  6b 2a 39 be a7 59 46 6e  |;.K.]...k*9..YFn|
00000150  21 fd d9 4e ac 1a 27 ce  69 5a 37 a2 20 19 f1 72  |!..N..'.iZ7. ..r|
00000160  5b 14 0a e0 37 c2 07 e9  0c 2e 16 7e 9f 3d b4 b9  |[...7......~.=..|
00000170  0e db 8d 2b e1 40 9b 56  de fb ca 7c 0d de 0c 76  |...+.@.V...|...v|
00000180  36 09 c0 10 53 bd 4c 1c  f8 41 9e 93 a5 73 84 ea  |6...S.L..A...s..|
00000190  7d 1b 83 eb 53 af 5e 86  35 28 c0 46 6c 3f 0c 19  |}...S.^.5(.Fl?..|
000001a0  18 64 52 36 c6 65 57 6d  9e 06 11 d6 8b 5e e5 48  |.dR6.eWm.....^.H|
000001b0  d8 6d da d7 64 1e 12 0b  bd a5 c4 d3 a9 0c 00 fe  |.m..d...........|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 f0 2d 00 00 00  |............-...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

File descriptor 7 (pipe:[5527]) leaked on lvscan invocation. Parent PID 8235: bash
File descriptor 8 (pipe:[5527]) leaked on lvscan invocation. Parent PID 8235: bash
  No volume groups found
mdadm: No arrays found in config file or automatically

ADDITIONAL INFORMATION :
=================== log of boot-repair 2012-10-12__16h42 ===================
boot-repair version : 3.193-0ppa22~lucid
boot-sav version : 3.193-0ppa39~lucid
glade2script-gtk2 version : 0.0.1-0ppa4~lucid
boot-sav-nonfree version :
Please connect internet. Then close this window.
/usr/share/boot-sav/gui-update.sh: line 77: add-apt-repository: command not found
/usr/share/boot-sav/gui-update.sh: line 77: add-apt-repository: command not found
deb [http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu](http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu) lucid main
/usr/share/boot-sav/gui-update.sh: line 77: add-apt-repository: command not found
/usr/share/boot-sav/gui-update.sh: line 77: add-apt-repository: command not found
deb [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu) lucid main
W: Failed to fetch [http://cdn.debian.net/debian/dists/squeeze/Release.gpg](http://cdn.debian.net/debian/dists/squeeze/Release.gpg)  Could not resolve 'cdn.debian.net'

W: Failed to fetch [http://cdn.debian.net/debian/dists/squeeze/main/i18n/Translation-en.bz2](http://cdn.debian.net/debian/dists/squeeze/main/i18n/Translation-en.bz2)  Could not resolve 'cdn.debian.net'

W: Failed to fetch [http://cdn.debian.net/debian/dists/squeeze/main/i18n/Translation-en_US.bz2](http://cdn.debian.net/debian/dists/squeeze/main/i18n/Translation-en_US.bz2)  Could not resolve 'cdn.debian.net'

W: Failed to fetch [http://security.debian.org/dists/squeeze/updates/Release.gpg](http://security.debian.org/dists/squeeze/updates/Release.gpg)  Could not resolve 'security.debian.org'

W: Failed to fetch [http://security.debian.org/dists/squeeze/updates/main/i18n/Translation-en.bz2](http://security.debian.org/dists/squeeze/updates/main/i18n/Translation-en.bz2)  Could not resolve 'security.debian.org'

W: Failed to fetch [http://security.debian.org/dists/squeeze/updates/main/i18n/Translation-en_US.bz2](http://security.debian.org/dists/squeeze/updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.debian.org'

W: Failed to fetch [http://cdn.debian.net/debian/dists/squeeze-updates/Release.gpg](http://cdn.debian.net/debian/dists/squeeze-updates/Release.gpg)  Could not resolve 'cdn.debian.net'

W: Failed to fetch [http://cdn.debian.net/debian/dists/squeeze-updates/main/i18n/Translation-en.bz2](http://cdn.debian.net/debian/dists/squeeze-updates/main/i18n/Translation-en.bz2)  Could not resolve 'cdn.debian.net'

W: Failed to fetch [http://cdn.debian.net/debian/dists/squeeze-updates/main/i18n/Translation-en_US.bz2](http://cdn.debian.net/debian/dists/squeeze-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'cdn.debian.net'

W: Failed to fetch [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/lucid/Release.gpg](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/lucid/Release.gpg)  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/lucid/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/lucid/main/i18n/Translation-en.bz2)  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch [http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/lucid/Release.gpg](http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/lucid/Release.gpg)  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch [http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/lucid/main/i18n/Translation-en.bz2](http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/lucid/main/i18n/Translation-en.bz2)  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch [http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Could not resolve 'ppa.launchpad.net'

W: Some index files failed to download, they have been ignored, or old ones used instead.

0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 63 not upgraded.
WARNING: The following packages cannot be authenticated!
os-uninstaller
Err [http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/](http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/) lucid/main os-uninstaller all 3.18-0ppa13~lucid
Could not resolve 'ppa.launchpad.net'
Failed to fetch [http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/pool/main/o/os-uninstaller/os-uninstaller_3.18-0ppa13~lucid_all.deb](http://ppa.launchpad.net/yannubuntu/os-uninstaller/ubuntu/pool/main/o/os-uninstaller/os-uninstaller_3.18-0ppa13~lucid_all.deb)  Could not resolve 'ppa.launchpad.net'
E: Some files failed to download

0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 63 not upgraded.
WARNING: The following packages cannot be authenticated!
boot-repair
Err [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/) lucid/main boot-repair all 3.193-0ppa22~lucid
Could not resolve 'ppa.launchpad.net'
Failed to fetch [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/pool/main/b/boot-repair/boot-repair_3.193-0ppa22~lucid_all.deb](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/pool/main/b/boot-repair/boot-repair_3.193-0ppa22~lucid_all.deb)  Could not resolve 'ppa.launchpad.net'
E: Some files failed to download
File descriptor 7 (pipe:[5527]) leaked on lvs invocation. Parent PID 3599: /bin/sh
File descriptor 8 (pipe:[5527]) leaked on lvs invocation. Parent PID 3599: /bin/sh
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 18.07.2012, squeeze, Debian, i686)
CPU op-mode(s):        64-bit
initrd=/live/initrd.img boot=live config   quiet BOOT_IMAGE=/live/vmlinuz

=================== os-prober:
/dev/sda1:Ubuntu 12.04.1 LTS (12.04):Ubuntu:linux

=================== blkid:
/dev/sda1: UUID="bb80684f-abb8-4331-92ad-54244f467422" TYPE="ext4"
/dev/sda5: UUID="6dbc8895-a235-42b5-9117-b88fe134cca5" TYPE="swap"
/dev/loop0: TYPE="squashfs"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

0+1 records in
0+1 records out
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.


=================== sda1/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10 FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"




=================== sda1/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Aug 17 22:08 grub.d
total 56
-rwxr-xr-x 1 root root 6715 May 17 07:22 00_header
-rwxr-xr-x 1 root root 5522 May 17 07:07 05_debian_theme
-rwxr-xr-x 1 root root 7407 May 17 07:22 10_linux
-rwxr-xr-x 1 root root 6335 May 17 07:22 20_linux_xen
-rwxr-xr-x 1 root root 1588 Nov 27  2011 20_memtest86+
-rwxr-xr-x 1 root root 7603 May 17 07:22 30_os-prober
-rwxr-xr-x 1 root root  214 May 17 07:22 40_custom
-rwxr-xr-x 1 root root   95 May 17 07:22 41_custom
-rw-r--r-- 1 root root  483 May 17 07:22 README


=================== dmesg | grep EFI :
This live-session is not EFI-compatible.


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc,    update-grub,    32,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sda1.

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA ST9160821AS (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
1      1049kB  158GB  158GB   primary   ext4            boot
2      158GB   160GB  1541MB  extended
5      158GB   160GB  1541MB  logical   linux-swap(v1)



                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label

=================== parted -lm:

BYT;
/dev/sda:160GB:scsi:512:512:msdos:ATA ST9160821AS;
1:1049kB:158GB:158GB:ext4::boot;
2:158GB:160GB:1541MB:::;
5:158GB:160GB:1541MB:linux-swap(v1)::;


                                                                          
Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.

                                                                          
Error: /dev/sr0: unrecognised disk label


=================== mount:
aufs on / type aufs (rw)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
/dev/sr0 on /live/image type iso9660 (ro,noatime)
tmpfs on /live/cow type tmpfs (rw,noatime,mode=755)
tmpfs on /live type tmpfs (rw,relatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sda1 on /mnt/boot-sav/sda1 type ext4 (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro sda1 sda2 sda5 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  block bsg btrfs-control bus cdrom cdrw char console core cpu_dma_latency disk dri dvd dvdrw fb0 fd full fuse fw0 hidraw0 hidraw1 hidraw2 hpet initctl input kmsg log MAKEDEV md mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 scd0 sda sda1 sda2 sda5 sg0 sg1 shm snapshot snd sndstat sr0 stderr stdin stdout urandom usb v4l vga_arbiter video0 xconsole zero
ls /dev/md:

=================== df -Th:

Filesystem    Type    Size  Used Avail Use% Mounted on
aufs          aufs    728M  7.4M  720M   2% /
tmpfs        tmpfs    728M     0  728M   0% /lib/init/rw
udev         tmpfs    723M  188K  722M   1% /dev
tmpfs        tmpfs    728M     0  728M   0% /dev/shm
/dev/sr0   iso9660    339M  339M     0 100% /live/image
tmpfs        tmpfs    728M  7.4M  720M   2% /live/cow
tmpfs        tmpfs    728M     0  728M   0% /live
tmpfs        tmpfs    728M  8.0K  728M   1% /tmp
/dev/sda1     ext4    146G  2.6G  136G   2% /mnt/boot-sav/sda1

=================== fdisk -l:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00032193

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19270   154782720   83  Linux
/dev/sda2           19270       19458     1505281    5  Extended
/dev/sda5           19270       19458     1505280   82  Linux swap / Solaris


EFIFILEPRESENCE , QTY_SUREEFIPART 0
EFIFILEPRESENCE , QTY_SUREEFIPART 0

=================== Default settings
Recommended-Repair
This setting would reinstall the grub2 of sda1 into the MBR of sda.
Additional repair would be performed: unhide-bootmenu-10s

=================== Settings chosen by the user
Boot-Info
This setting will not act on the MBR.



No change has been performed on your computer. See you soon!
Please connect internet. Then close this window.
```

---

### Post by cybrsaylr on 2012-10-12
FWIW agree HP has the worst reliability when it comes to laptops.

Can you boot up into W7 at all?

Had a friend with an HP laptop that wouldn't boot into Vista anymore. Just got a black screen saying to run HP diagnostics & repair but wouldn't even run either correctly. However it ran Ubuntu 12.04 Live CD perfectly but would not install 12.04. Turned out that HP laptop had a bad HDD. Put a new HDD in and it runs great.

---

### Post by nothingspecial on 2012-10-12
Hi

When pasting terminal output, please use code tags. The easiest way to do this is highlight the pasted text then click the # in the formatting option at the top of the posting box.

Thanks.

---

### Post by Redstiza on 2012-10-12
I can't even boot into Windows 7,  I probably just need to install grub or grub2 so it can boot from the hard drive.

---

### Post by Redstiza on 2012-10-12
> **nothingspecial said:**
> Hi

When pasting terminal output, please use code tags. The easiest way to do this is highlight the pasted text then click the # in the formatting option at the top of the posting box.

Thanks.

Oh, sorry I didn't know that was for stuff like that.  Thanks for putting it in a code box.

---

### Post by Redstiza on 2012-10-12
I am trying to run Boot Repair while running Ubuntu live off the CD and see if that works.
When I use the steps on the Grub2/Installing Community Documentation,  I put this into terminal:

```
sudo fdisk -l
```and it gives me a list of the partitions.  I'm assuming that the first one, sda1 is the one where I installed Ubuntu over Windows 7 since it has the largest number of blocks and says under system: Linux.  If not, then is there something like sda0, or is sda1 the default HD.

Edit:  I tried installing it like in the document, but still get an error can't open file when starting up.  At least now it's recognizing that Ubuntu is there since it gets to the loading screen before failing.

---

### Post by YannBuntu on 2012-10-12
Hello

The Boot-Info shows that you have erased Windows and installed Ubuntu instead.
I see no problem, except that your Ubuntu boot files may be too far from the start of the disk. To fix this, use [Gparted]("https://help.ubuntu.com/community/GParted") (included in the Ubuntu CD) to reduce your sda1 partition from 158GB to 100GB.

> **Redstiza said:**
> it gets to the loading screen before failing.

What is this screen looking like? do you see the GRUB menu?

---

### Post by Redstiza on 2012-10-13
> **YannBuntu said:**
> Hello

The Boot-Info shows that you have erased Windows and installed Ubuntu instead.
I see no problem, except that your Ubuntu boot files may be too far from the start of the disk. To fix this, use [Gparted]("https://help.ubuntu.com/community/GParted") (included in the Ubuntu CD) to reduce your sda1 partition from 158GB to 100GB.



What is this screen looking like? do you see the GRUB menu?

I have tried to install Ubuntu again, only this time I was setting up the partitions manually so that it would install grub in the correct area.  It was going fine until the Installer kept crashing.  I made a new CD and let it burn slower, but now it tells me either the hard drive is old and needs to be replaced, or that it's overheating.  The laptop gets hot enough to burn me sometimes so I figured it was that and placed the whole thing on top of a small fan I had.  I got to the point where I was at the 'something else' menu, but it wouldn't let me click install after setting up the partitions (the button was grayed out.)  So I restarted the computer, and now I can't even get to that menu because the buttons for continue are greyed out when I select something else, erase previous os and install Ubuntu, or install Ubuntu alongside.

Also, the screen was just purple, it had the Ubuntu logo with dots under it, then went to the other screen.  There wasn't any GRUB menu.

---

### Post by Paulgirardin on 2012-10-14
If it is a single boot with no other OS I don't think it normally shows a GRUB menu.Only my dual boots show a menu.
You might be able to display the GRUB menu by hitting <left shift> repeatedly when the system is booting.

If your HDD is faulty you could put Puppy Linux on a USB stick or a CD and boot that.
Puppy will run on a system with no HDD.

---

### Post by Bucky Ball on 2012-10-14
That overheating problem doesn't sound good. What is getting hot in there? Is it the HD or something else? Is this a laptop or desktop? Has this just started happening or does it generally get that hot?

---

### Post by Redstiza on 2012-10-15
> **Bucky Ball said:**
> That overheating problem doesn't sound good. What is getting hot in there? Is it the HD or something else? Is this a laptop or desktop? Has this just started happening or does it generally get that hot?

It's been happening for a while, but no matter how cool I get that laptop by putting it on top of fans, I still get the error.  It's most likely the hard drive.  I am going to order a new on off amazon and see if that's the problem.

---

