---
title: "Very Old PC-Problems with GRUB-Maybe BIOS limitation/setting?"
date: 2010-12-24
forum: Installation &amp; Upgrades
---

### Post by driv3r_lnx on 2010-12-24
Hello guys,

I'm encountering problems with GRUB and I'm fighting to make it work properly the last days without any success.

I installed initially Xubuntu 10.04 i386 on a Pentium II 350/QDI Mo/bo with 512MB RAM with Geforce 2 MX.

I had the same problem with the original HDD (Quantum Fireball 10GB) and I installed a WD Caviar 250GB, which I thought will solve the GRUB loading problem (sometimes Quantum wasn't recognized).

I've tried both Xubuntu and Lubuntu installations without any success in both cases, but with different boot problems each time.
Of course tried to fix them manually (apart from different clean install attempts) but none of the previous posted solutions in forums I've read worked.

The partions creations go like that:

1st- swap -sda1
2nd- /boot -sda2
3rd- / -sda3
4th- /home -sda4

which always worked fine for me on any distro I've used so far,but not here on this old PC.

**_Xubuntu:_**

*Not found any [active partition] in HDD*

Tried to change the boot partion manually through Gparted in Live CD (to /boot-default was swap) or even the / but never did overcome this error message.Confirmed each time that boot partion changed with
> fdisk -l

---

**_Lubuntu:_**

[I]error:unknown filesystem
grub rescue>[/I]

The situation here never changed since I've tried to re-install GRUB again and again without any success to load it properly.

> sudo mount -t ext4 /dev/sda2/ /mnt/boot (tried to /mnt/ only)

> sudo grub-install --root-directory=/mnt/ /dev/sda/

Tried to install it in /dev/sda2/ but it doesn't allow me without enforcing it, because it's recommended to install GRUB in MBR.

> sudo grub-install --root-directory=/mnt/boot/ /dev/sda/
/usr/sbin/grub-probe: error: cannot stat `/dev/sda/'.

> sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

Any help would be highly appreciated because I think that it maybe a hardware/BIOS settings/problem that cannot figure out, or I maybe doing something very wrong in every attempt.

Lastly I have to mention that tried to install from scratch the Lubuntu version with the default partioning setup, where it uses the entire hard-drive and now it throws me into GRUB with the "Minimal Bash-like editing..." grub> which lead me here to ask for your help.

Thank you

---

### Post by kansasnoob on 2010-12-24
I'd begin by going to Gparted clicking on Device and Create partition table. That should create an MSDOS partition table.

Then create a layout like this with Gparted:

[ATTACH]179272[/ATTACH]

I'd keep the "/boot" between 500MB and 700MB, and the "/" between 6GB and 8GB. Based on 512MB of RAM slightly more than 1GB of SWAP should be sufficient. Since my test drive is only 80GB I used a smaller "/home" so that's the partition you'll want to increase in size to use up your whole disc.

Particularly notice that only "/boot" and "/" are primary partitions! I created an extended partition to contain logical partitions for both "/home" and SWAP.

You will, of course, need to select the proper devices during installation so jot down the designations if needed.

**Notice also I used the ext3 filesystem!** I have an old Micron w/Pentium II and ext 4 doesn't like it.

---

### Post by oldfred on 2010-12-24
Do you have an Intel motherboard?

[I]Not found any [active partition] in HDD

[/I]That is not a Linux or Grub error. Windows uses the term active partition for the boot flag. Ubuntu/grub does not need a boot flag. But some BIOS check for the active partition before they let you boot. So I think that error is from BIOS. All you have to do is put a boot flag on any primary partition (within the first 137GB of drive), grub will not care & BIOS will work.

---

### Post by driv3r_lnx on 2010-12-25
Thank you guys for your replies.

kansasnoob-
I'm gonna follow your suggestions regarding the partitions order and use ext3 to be in the safe zone. I'm curious if it was affected by that.

oldfred-
The mobo is QDI, not anymore in business. The strange thing is that this error was occurring only with Xubuntu distro installation and not with Lubuntu, even if I was following the exact procedure as described before in both distros. I was changing the boot flag from partition to partition to see if it actually had any effect, but nothing did happen. I assume that it was a different GRUB version's fault (Xubuntu 10.04/Lubuntu 10.10).

I'm gonna re-install everything from the scratch and post the results here.

Thank you for your time and I wish you all the best and Merry Christmas to everybody!

Cheers!

---

### Post by driv3r_lnx on 2010-12-26
Well I did re-install Lubuntu on the 250GB HDD with ext3 and partitions as suggested above but the same persistent problem occurred:

> Veryfying DMI Pool Data
error:unknown filesystem.
grub rescue>

Tried to re-install GRUB again

> sudo ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b4f97

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          32      256000   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              32        1945    15360000   83  Linux
/dev/sda3            1945       30402   228580353    5  Extended
/dev/sda5            1945       30246   227328000   83  Linux
/dev/sda6           30246       30402     1251328   82  Linux swap / Solaris

> ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda1 /mnt

> ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda
Installation finished. No error reported.

Honestly I cannot imagine what could it be, BIOS settings don't seem to create any problem, nothing changed even with the factory default settings.

Any further idea would be highly welcome, I ran out of ideas that may work at all.

Thank you a lot for your precious time.

---

### Post by oldfred on 2010-12-26
If you have the separate /boot partition you have to also mount /boot & / (root)

If separate /boot
$ sudo mount /dev/sda2 /mnt
$ sudo mount /dev/sda1 /mnt/boot
$ grub-install --root-directory=/mnt /dev/sda

drs305 also has good instructions on the full chroot method when the short method above does not work. You just probably do not have to uninstall old grub but do the full uninstall & reinstall of grub2 (grub-pc).
chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)


Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by driv3r_lnx on 2010-12-27
Hi there again.

Unfortunately neither of both solutions worked, the system insists returning the same error message during boot time.

Short and long (chroot/uninstall/re-install) method were executed fine without any complications but still nothing changed anything since the beginning. It still remains extremely strange why it constantly pops the same error while with the LiveCD when I choose to boot from local hard drive it appears again the same error (unknown filesystem.grub rescue>).

Booting from the first local drive option in LiveCD worked fine in Xubuntu installation, while experiencing the [Not found any [active partition] in HDD] message.

I did follow the Grub restoration thread method, but the same thing happened.

Any other recommendation to fix the problem would be highly welcome to be tested

---

### Post by oldfred on 2010-12-27
Maybe this will tell us something else is missing?

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by driv3r_lnx on 2010-12-27
Thank you for your help.Here are the generated results and I copied the entire text as is.

Quick note:

The 250GB HDD was fully formated with Gparted with new partition table (msdos) and ext3 (all other attempts were in ext4), as was suggested from kansasnoob, but I don't understand what are the unknown MBRs and the Vista/7 boot sectors.(only the WD250GB is connected on the system, which had had WinXP only before,should all the Windows details be fully erased after the full format with Gparted?)

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       514,047       512,000  83 Linux
/dev/sda2             514,048    31,234,047    30,720,000  83 Linux
/dev/sda3          31,236,094   488,396,799   457,160,706   5 Extended
/dev/sda5          31,236,096   485,892,095   454,656,000  83 Linux
/dev/sda6         485,894,144   488,396,799     2,502,656  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 16.4 GB, 16441481728 bytes
64 heads, 32 sectors/track, 15679 cylinders, total 32112269 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  32    32,110,591    32,110,560   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        12f418e1-dbd2-4bd9-a468-c81e8682b381   ext3                                     
/dev/sda2        df2fcbe3-e876-43e0-94f4-2e9cb3190008   ext3                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        4c87418a-e2d8-4906-976d-5344a68b0150   ext3                                     
/dev/sda6        bd6b46f8-bbc9-4211-a769-5f4b5eb7f9b6   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0F0639B048215D71                       ntfs       Own3D                         
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


============================= sda1/grub/grub.cfg: =============================

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
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set df2fcbe3-e876-43e0-94f4-2e9cb3190008
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 12f418e1-dbd2-4bd9-a468-c81e8682b381
set locale_dir=($root)/grub/locale
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
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 12f418e1-dbd2-4bd9-a468-c81e8682b381
	linux	/vmlinuz-2.6.35-22-generic root=UUID=df2fcbe3-e876-43e0-94f4-2e9cb3190008 ro   quiet splash
	initrd	/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 12f418e1-dbd2-4bd9-a468-c81e8682b381
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/vmlinuz-2.6.35-22-generic root=UUID=df2fcbe3-e876-43e0-94f4-2e9cb3190008 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 12f418e1-dbd2-4bd9-a468-c81e8682b381
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 12f418e1-dbd2-4bd9-a468-c81e8682b381
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .1GB: grub/core.img
    .1GB: grub/grub.cfg
    .0GB: initrd.img-2.6.35-22-generic
    .0GB: vmlinuz-2.6.35-22-generic

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=df2fcbe3-e876-43e0-94f4-2e9cb3190008 /               ext3    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=12f418e1-dbd2-4bd9-a468-c81e8682b381 /boot           ext3    defaults        0       2
# /home was on /dev/sda5 during installation
UUID=4c87418a-e2d8-4906-976d-5344a68b0150 /home           ext3    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=bd6b46f8-bbc9-4211-a769-5f4b5eb7f9b6 none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


  15.7GB: boot/grub/core.img
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  3c f8 00 bb ba e3 b9 61  a4 46 4c 87 7b b8 a1 b6  |<......a.FL.{...|
00000010  52 8c 8c 90 13 73 6f 96  c3 b6 1e e4 74 53 4a dd  |R....so.....tSJ.|
00000020  91 4d cb 83 7b e9 fd ae  b2 7a a5 ad 66 8c 35 15  |.M..{....z..f.5.|
00000030  a6 cd 6a 8a 52 28 78 25  59 14 8c f9 fc 7e bd 5e  |..j.R(x%Y....~.^|
00000040  f0 b2 19 f0 fc 9f d7 72  9b 94 7c aa 62 b6 5b c4  |.......r..|.b.[.|
00000050  fd 00 7d b1 15 72 33 f1  e2 d4 c1 35 af af 99 31  |..}..r3....5...1|
00000060  cb 5b cd d3 92 88 51 c3  79 1e e1 a0 c1 f4 0c ac  |.[....Q.y.......|
00000070  d2 bb a7 26 21 30 1c f8  33 38 1c 8a 01 b4 4a 66  |...&!0..38....Jf|
00000080  4d db e5 fb 71 6f 48 4d  1f 16 5c bf e6 87 42 f1  |M...qoHM..\...B.|
00000090  9d 61 8e a8 2b e7 41 b5  05 26 cf d6 c1 bb 1c c3  |.a..+.A..&......|
000000a0  fc 6b b6 71 ee 06 74 f0  45 a8 b7 79 58 88 ae 07  |.k.q..t.E..yX...|
000000b0  f1 55 6c 6a 5c a4 2b 4d  e9 2c 5b de fb cf 8d 58  |.Ulj\.+M.,[....X|
000000c0  ae 77 3e 4b 3e 4f 2f 42  11 db 46 b4 98 6e 74 49  |.w>K>O/B..F..ntI|
000000d0  94 e0 2b 9b a8 7d c4 8e  c4 ab 04 98 30 1f 02 39  |..+..}......0..9|
000000e0  97 82 99 df 0a fa c6 aa  5b 80 88 de a6 dd 22 32  |........[....."2|
000000f0  01 6a 83 98 9a 75 95 18  2a d7 bc 7b 11 3d da f6  |.j...u..*..{.=..|
00000100  61 fb d9 d7 e1 d6 c3 1d  5d 84 1d ec 34 05 e2 ac  |a.......]...4...|
00000110  d5 92 13 72 bf 8a 14 7f  8c f5 5b fd 2f f6 e0 73  |...r......[./..s|
00000120  a4 c5 d8 52 77 82 3b f6  69 66 8e d8 25 ed de 2e  |...Rw.;.if..%...|
00000130  e1 23 31 fb e3 7f bd db  47 1c 8e 63 ca 8c fc 19  |.#1.....G..c....|
00000140  5d d0 3d 8f 3a c4 9b 50  f9 7d 2e 4f a8 a2 b6 16  |].=.:..P.}.O....|
00000150  fa e5 56 59 d1 d7 25 56  e8 71 7d e8 84 02 20 9b  |..VY..%V.q}... .|
00000160  8c 0c 83 02 43 e9 ab f8  68 63 03 09 b3 18 a2 71  |....C...hc.....q|
00000170  de 20 60 37 2a a0 e1 b6  68 ce 0f e4 a6 56 03 07  |. `7*...h....V..|
00000180  90 07 35 28 85 9f 6d ba  05 06 fa a9 26 16 8d a9  |..5(..m.....&...|
00000190  52 12 86 d8 8d 26 e0 e0  74 fb bf bc 63 fe 9f 9f  |R....&..t...c...|
000001a0  0f cc 47 a0 0e 09 f2 a4  01 0a a7 a9 cd 0d 93 f1  |..G.............|
000001b0  92 53 11 86 a6 a6 19 e3  98 fe 54 25 d7 13 00 fe  |.S........T%....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 80 19 1b 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 80  19 1b 00 38 26 00 00 00  |...........8&...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by psusi on 2010-12-27
You didn't have /boot mounted when you reinstalled grub.  Also try typing ls (hd0,1)/ at the grub rescue prompt.

---

### Post by driv3r_lnx on 2010-12-27
It may seem that I'm either an extreme linux newbie or I want to make you lose your patience by helping me (which both cases do  not represent the reality), I'm having the same problems again and again and before posting again I tried everything twice to make sure that I'm not skipping anything.

I realized that is essential to mount both /boot and /, but something tells me that the PC denies the last 10 days to accept linux at all for some non-logical reason.

Results No.2
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/grub.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       514,047       512,000  83 Linux
/dev/sda2             514,048    31,234,047    30,720,000  83 Linux
/dev/sda3          31,236,094   488,396,799   457,160,706   5 Extended
/dev/sda5          31,236,096   485,892,095   454,656,000  83 Linux
/dev/sda6         485,894,144   488,396,799     2,502,656  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        12f418e1-dbd2-4bd9-a468-c81e8682b381   ext3                                     
/dev/sda2        df2fcbe3-e876-43e0-94f4-2e9cb3190008   ext3                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        4c87418a-e2d8-4906-976d-5344a68b0150   ext3                                     
/dev/sda6        bd6b46f8-bbc9-4211-a769-5f4b5eb7f9b6   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


============================= sda1/grub/grub.cfg: =============================

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
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set df2fcbe3-e876-43e0-94f4-2e9cb3190008
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 12f418e1-dbd2-4bd9-a468-c81e8682b381
set locale_dir=($root)/grub/locale
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
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 12f418e1-dbd2-4bd9-a468-c81e8682b381
	linux	/vmlinuz-2.6.35-22-generic root=UUID=df2fcbe3-e876-43e0-94f4-2e9cb3190008 ro   quiet splash
	initrd	/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 12f418e1-dbd2-4bd9-a468-c81e8682b381
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/vmlinuz-2.6.35-22-generic root=UUID=df2fcbe3-e876-43e0-94f4-2e9cb3190008 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 12f418e1-dbd2-4bd9-a468-c81e8682b381
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 12f418e1-dbd2-4bd9-a468-c81e8682b381
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .2GB: grub/core.img
    .2GB: grub/grub.cfg
    .0GB: initrd.img-2.6.35-22-generic
    .0GB: vmlinuz-2.6.35-22-generic

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=df2fcbe3-e876-43e0-94f4-2e9cb3190008 /               ext3    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=12f418e1-dbd2-4bd9-a468-c81e8682b381 /boot           ext3    defaults        0       2
# /home was on /dev/sda5 during installation
UUID=4c87418a-e2d8-4906-976d-5344a68b0150 /home           ext3    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=bd6b46f8-bbc9-4211-a769-5f4b5eb7f9b6 none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


  15.7GB: boot/grub/core.img
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  3c f8 00 bb ba e3 b9 61  a4 46 4c 87 7b b8 a1 b6  |<......a.FL.{...|
00000010  52 8c 8c 90 13 73 6f 96  c3 b6 1e e4 74 53 4a dd  |R....so.....tSJ.|
00000020  91 4d cb 83 7b e9 fd ae  b2 7a a5 ad 66 8c 35 15  |.M..{....z..f.5.|
00000030  a6 cd 6a 8a 52 28 78 25  59 14 8c f9 fc 7e bd 5e  |..j.R(x%Y....~.^|
00000040  f0 b2 19 f0 fc 9f d7 72  9b 94 7c aa 62 b6 5b c4  |.......r..|.b.[.|
00000050  fd 00 7d b1 15 72 33 f1  e2 d4 c1 35 af af 99 31  |..}..r3....5...1|
00000060  cb 5b cd d3 92 88 51 c3  79 1e e1 a0 c1 f4 0c ac  |.[....Q.y.......|
00000070  d2 bb a7 26 21 30 1c f8  33 38 1c 8a 01 b4 4a 66  |...&!0..38....Jf|
00000080  4d db e5 fb 71 6f 48 4d  1f 16 5c bf e6 87 42 f1  |M...qoHM..\...B.|
00000090  9d 61 8e a8 2b e7 41 b5  05 26 cf d6 c1 bb 1c c3  |.a..+.A..&......|
000000a0  fc 6b b6 71 ee 06 74 f0  45 a8 b7 79 58 88 ae 07  |.k.q..t.E..yX...|
000000b0  f1 55 6c 6a 5c a4 2b 4d  e9 2c 5b de fb cf 8d 58  |.Ulj\.+M.,[....X|
000000c0  ae 77 3e 4b 3e 4f 2f 42  11 db 46 b4 98 6e 74 49  |.w>K>O/B..F..ntI|
000000d0  94 e0 2b 9b a8 7d c4 8e  c4 ab 04 98 30 1f 02 39  |..+..}......0..9|
000000e0  97 82 99 df 0a fa c6 aa  5b 80 88 de a6 dd 22 32  |........[....."2|
000000f0  01 6a 83 98 9a 75 95 18  2a d7 bc 7b 11 3d da f6  |.j...u..*..{.=..|
00000100  61 fb d9 d7 e1 d6 c3 1d  5d 84 1d ec 34 05 e2 ac  |a.......]...4...|
00000110  d5 92 13 72 bf 8a 14 7f  8c f5 5b fd 2f f6 e0 73  |...r......[./..s|
00000120  a4 c5 d8 52 77 82 3b f6  69 66 8e d8 25 ed de 2e  |...Rw.;.if..%...|
00000130  e1 23 31 fb e3 7f bd db  47 1c 8e 63 ca 8c fc 19  |.#1.....G..c....|
00000140  5d d0 3d 8f 3a c4 9b 50  f9 7d 2e 4f a8 a2 b6 16  |].=.:..P.}.O....|
00000150  fa e5 56 59 d1 d7 25 56  e8 71 7d e8 84 02 20 9b  |..VY..%V.q}... .|
00000160  8c 0c 83 02 43 e9 ab f8  68 63 03 09 b3 18 a2 71  |....C...hc.....q|
00000170  de 20 60 37 2a a0 e1 b6  68 ce 0f e4 a6 56 03 07  |. `7*...h....V..|
00000180  90 07 35 28 85 9f 6d ba  05 06 fa a9 26 16 8d a9  |..5(..m.....&...|
00000190  52 12 86 d8 8d 26 e0 e0  74 fb bf bc 63 fe 9f 9f  |R....&..t...c...|
000001a0  0f cc 47 a0 0e 09 f2 a4  01 0a a7 a9 cd 0d 93 f1  |..G.............|
000001b0  92 53 11 86 a6 a6 19 e3  98 fe 54 25 d7 13 00 fe  |.S........T%....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 80 19 1b 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 80  19 1b 00 38 26 00 00 00  |...........8&...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

Results No.3
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       514,047       512,000  83 Linux
/dev/sda2             514,048    31,234,047    30,720,000  83 Linux
/dev/sda3          31,236,094   488,396,799   457,160,706   5 Extended
/dev/sda5          31,236,096   485,892,095   454,656,000  83 Linux
/dev/sda6         485,894,144   488,396,799     2,502,656  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 16.4 GB, 16441481728 bytes
64 heads, 32 sectors/track, 15679 cylinders, total 32112269 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  32    32,110,591    32,110,560   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        12f418e1-dbd2-4bd9-a468-c81e8682b381   ext3                                     
/dev/sda2        df2fcbe3-e876-43e0-94f4-2e9cb3190008   ext3                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        4c87418a-e2d8-4906-976d-5344a68b0150   ext3                                     
/dev/sda6        bd6b46f8-bbc9-4211-a769-5f4b5eb7f9b6   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0F0639B048215D71                       ntfs       Own3D                         
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/Own3D             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


============================= sda1/grub/grub.cfg: =============================

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
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set df2fcbe3-e876-43e0-94f4-2e9cb3190008
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 12f418e1-dbd2-4bd9-a468-c81e8682b381
set locale_dir=($root)/grub/locale
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
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 12f418e1-dbd2-4bd9-a468-c81e8682b381
	linux	/vmlinuz-2.6.35-22-generic root=UUID=df2fcbe3-e876-43e0-94f4-2e9cb3190008 ro   quiet splash
	initrd	/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 12f418e1-dbd2-4bd9-a468-c81e8682b381
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/vmlinuz-2.6.35-22-generic root=UUID=df2fcbe3-e876-43e0-94f4-2e9cb3190008 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 12f418e1-dbd2-4bd9-a468-c81e8682b381
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 12f418e1-dbd2-4bd9-a468-c81e8682b381
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/core.img
    .2GB: grub/core.img
    .2GB: grub/grub.cfg
    .0GB: initrd.img-2.6.35-22-generic
    .0GB: vmlinuz-2.6.35-22-generic

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=df2fcbe3-e876-43e0-94f4-2e9cb3190008 /               ext3    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=12f418e1-dbd2-4bd9-a468-c81e8682b381 /boot           ext3    defaults        0       2
# /home was on /dev/sda5 during installation
UUID=4c87418a-e2d8-4906-976d-5344a68b0150 /home           ext3    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=bd6b46f8-bbc9-4211-a769-5f4b5eb7f9b6 none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


  15.8GB: boot/grub/core.img
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  3c f8 00 bb ba e3 b9 61  a4 46 4c 87 7b b8 a1 b6  |<......a.FL.{...|
00000010  52 8c 8c 90 13 73 6f 96  c3 b6 1e e4 74 53 4a dd  |R....so.....tSJ.|
00000020  91 4d cb 83 7b e9 fd ae  b2 7a a5 ad 66 8c 35 15  |.M..{....z..f.5.|
00000030  a6 cd 6a 8a 52 28 78 25  59 14 8c f9 fc 7e bd 5e  |..j.R(x%Y....~.^|
00000040  f0 b2 19 f0 fc 9f d7 72  9b 94 7c aa 62 b6 5b c4  |.......r..|.b.[.|
00000050  fd 00 7d b1 15 72 33 f1  e2 d4 c1 35 af af 99 31  |..}..r3....5...1|
00000060  cb 5b cd d3 92 88 51 c3  79 1e e1 a0 c1 f4 0c ac  |.[....Q.y.......|
00000070  d2 bb a7 26 21 30 1c f8  33 38 1c 8a 01 b4 4a 66  |...&!0..38....Jf|
00000080  4d db e5 fb 71 6f 48 4d  1f 16 5c bf e6 87 42 f1  |M...qoHM..\...B.|
00000090  9d 61 8e a8 2b e7 41 b5  05 26 cf d6 c1 bb 1c c3  |.a..+.A..&......|
000000a0  fc 6b b6 71 ee 06 74 f0  45 a8 b7 79 58 88 ae 07  |.k.q..t.E..yX...|
000000b0  f1 55 6c 6a 5c a4 2b 4d  e9 2c 5b de fb cf 8d 58  |.Ulj\.+M.,[....X|
000000c0  ae 77 3e 4b 3e 4f 2f 42  11 db 46 b4 98 6e 74 49  |.w>K>O/B..F..ntI|
000000d0  94 e0 2b 9b a8 7d c4 8e  c4 ab 04 98 30 1f 02 39  |..+..}......0..9|
000000e0  97 82 99 df 0a fa c6 aa  5b 80 88 de a6 dd 22 32  |........[....."2|
000000f0  01 6a 83 98 9a 75 95 18  2a d7 bc 7b 11 3d da f6  |.j...u..*..{.=..|
00000100  61 fb d9 d7 e1 d6 c3 1d  5d 84 1d ec 34 05 e2 ac  |a.......]...4...|
00000110  d5 92 13 72 bf 8a 14 7f  8c f5 5b fd 2f f6 e0 73  |...r......[./..s|
00000120  a4 c5 d8 52 77 82 3b f6  69 66 8e d8 25 ed de 2e  |...Rw.;.if..%...|
00000130  e1 23 31 fb e3 7f bd db  47 1c 8e 63 ca 8c fc 19  |.#1.....G..c....|
00000140  5d d0 3d 8f 3a c4 9b 50  f9 7d 2e 4f a8 a2 b6 16  |].=.:..P.}.O....|
00000150  fa e5 56 59 d1 d7 25 56  e8 71 7d e8 84 02 20 9b  |..VY..%V.q}... .|
00000160  8c 0c 83 02 43 e9 ab f8  68 63 03 09 b3 18 a2 71  |....C...hc.....q|
00000170  de 20 60 37 2a a0 e1 b6  68 ce 0f e4 a6 56 03 07  |. `7*...h....V..|
00000180  90 07 35 28 85 9f 6d ba  05 06 fa a9 26 16 8d a9  |..5(..m.....&...|
00000190  52 12 86 d8 8d 26 e0 e0  74 fb bf bc 63 fe 9f 9f  |R....&..t...c...|
000001a0  0f cc 47 a0 0e 09 f2 a4  01 0a a7 a9 cd 0d 93 f1  |..G.............|
000001b0  92 53 11 86 a6 a6 19 e3  98 fe 54 25 d7 13 00 fe  |.S........T%....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 80 19 1b 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 80  19 1b 00 38 26 00 00 00  |...........8&...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

Mounted partitions while/after re-installing the Grub2
```
root@ubuntu:/# mount | tail -l
/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro,barrier=0,data=ordered)
/dev/sda1 on /boot type ext3 (rw,relatime,errors=continue,barrier=0,data=ordered)
/dev/sda5 on /home type ext3 (rw,relatime,errors=continue,barrier=0,data=ordered)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
none on /proc type proc (rw,nosuid,nodev,noexec,relatime)
none on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
none on /dev type devtmpfs (rw,relatime,size=246068k,nr_inodes=61517,mode=755)

ubuntu@ubuntu:~$ sudo mount | tail -l
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /mnt/boot type ext3 (rw)
/dev/sda2 on /mnt type ext3 (rw)

```

---

### Post by presence1960 on 2010-12-27
Why do you need a separate /boot partition? The main reason to have one is when your BIOS is so old that it can't read past a certain point on your hard disk, thus it can't locate the files necessary to boot. You have nothing but linux on that disk, why not just install it the "ordinary" way rather than with a separate /boot partition? See if that works, what have you got to lose?

---

### Post by oldfred on 2010-12-27
I do not see anything really out of place in you results.txt. You do have core.img installed in three places but I do not think that would prevent booting as everything looks correct to me.

Sometimes when the standard grub reinstall does not work we have to do the full chroot method but even with that we have to also mount the /boot partition - see note in instructions from drd305. You would not have to run the grub legacy uninstall, but sometimes just uninstalling and reinstalling grub2 (grub-pc) solves boot issues.

chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

full chroot version:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD")

---

### Post by cavalier911 on 2010-12-28
Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/grub.

What's in **bold** is UUID of /dev/sda2 which is wrong,it should be the UUID of the partition containing kernel and initrd which is /dev/sda1  

    /dev/sda1        12f418e1-dbd2-4bd9-a468-c81e8682b381   ext3  

What's underlined should be UUID of /dev/sda2 the root filesystem.

> ### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set _12f418e1-dbd2-4bd9-a468-c81e8682b381_
	linux	/vmlinuz-2.6.35-22-generic root=UUID=**df2fcbe3-e876-43e0-94f4-2e9cb3190008** ro   quiet splash
	initrd	/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set _12f418e1-dbd2-4bd9-a468-c81e8682b381_
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/vmlinuz-2.6.35-22-generic root=UUID=**df2fcbe3-e876-43e0-94f4-2e9cb3190008** ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

To test copy/save whats between the code tags to /etc/grub.d/40_custom

```
menuentry 'Lubuntu 10.10' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set df2fcbe3-e876-43e0-94f4-2e9cb3190008
	linux	/vmlinuz-2.6.35-22-generic root=UUID=12f418e1-dbd2-4bd9-a468-c81e8682b381 ro  
	initrd	/initrd.img-2.6.35-22-generic
}
```

Run ```
sudo update-grub
```

This corrected stanza should be at the bottom of menu.

Good luck ;)

---

### Post by psusi on 2010-12-28
> **cavalier911 said:**
> 
What's in **bold** is UUID of /dev/sda2 which is wrong,it should be the UUID of the partition containing kernel and initrd which is /dev/sda1

No, it isn't wrong.  The root kernel argument tells the kernel where the root fs is, which is /dev/sda2.

The root GRUB argument needs to point to /boot, which it does.

---

### Post by driv3r_lnx on 2010-12-30
Thank you guys all for your interest.
Since I'm planning to use exclusively linux I'm gonna give it another shoot and create/install only 3 main partition without /boot.

1.swap
2./
3./home

I'll post the results of this attempt again.

Really appreciated your efforts to help :KS

---

### Post by driv3r_lnx on 2010-12-31
Same characters,same story.

Even without the /boot partition the story repeats itself and I'm unable to boot the installation after another -from scratch- attempt to find out a solution. I didn't try to re-install GRUB at all, since it is not the case of the problem.

Wisdom and patience runs out, sometimes I think why some decent things (windows) seem to be made in heaven and are instantly working, while the truth is totally the contrary.
Any other old-school solution that may help is welcome and I'm still willing to try it, 15 days is more than enough to keep up with something so simple that it resists, but this is the entire lesson of this thread.

Whatever is the case, I would like to wish you all the best for success,happiness and fulfillment in 2011 for every plan/dream you may have.

Plenty of cheers!

---

