---
title: "tried to dual boot but failed!"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by yezzir on 2010-05-13
my laptop has 2 HDs.  i just upgraded one of them and installed windows 7 on it.  my goal was to have one whole HD dedicated to win 7 and another dedicated to ubuntu. so just a while ago, i tried to install ubuntu.  well it installed correctly, but unfortunately i cant choose between operating systems and i dont think it even recognizes windows 7 being installed.  

i checked to see if my windows HD is still intact, and it is.  i tried to run the windows 7 CD to repair it but it doesnt catch anything =(

any ideas?

---

### Post by yezzir on 2010-05-13
im pretty sure its the windows 7 loader that messed up but nothing that i have done so far seems to bring it back :(

---

### Post by byStanderone on 2010-05-13
... try a sudo update-grub

---

### Post by Tanayar on 2010-05-13
Can you choose between the harddrives in the BIOS? If you can boot both it's grub that doesn't work. Or are they both unbootable now?

---

### Post by wilee-nilee on 2010-05-13
Post this boot script in code tags. 
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Without the information that this script will contain we are just flailing in the dark. To post in code tags paste the script in the reply highlight it and click on the # on the reply panel, then hit submit reply.

---

### Post by yezzir on 2010-05-13
i can choose HD's but when i choose the windows HD it doesnt even boot up.  it gives me some kind of error which i will post up later tonight as i have to go to work right now (it says something about my ethernet card for some reason).  the ubuntu HD works fine.

wilee-nilee - i will do that when i get back

---

### Post by kansasnoob on 2010-05-13
> **wilee-nilee said:**
> Post this boot script in code tags. 
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Without the information that this script will contain we are just flailing in the dark. To post in code tags paste the script in the reply highlight it and click on the # on the reply panel, then hit submit reply.

+1! Why guess when you can test :)

---

### Post by wilee-nilee on 2010-05-13
> **kansasnoob said:**
> +1! Why guess when you can test :)

It didn't take very long for me to figure that out, I'm basically lazy, why not make it easy eh, well relatively easy. Many times I see what the problems are but I let the people who are much better at this give the advice, this is a great learning tool.

---

### Post by yezzir on 2010-05-13
ok i ran the script, here are the results

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   625,139,711   625,137,664   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   187,336,703   187,334,656  83 Linux
/dev/sdb2         187,338,750   195,371,007     8,032,258   5 Extended
/dev/sdb5         187,338,752   195,371,007     8,032,256  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        FAFE947FFE94363B                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        7771ba19-c0dc-4e8a-b6e1-d6952f1576d1   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        7c2fd557-948c-4a5b-a0a1-423b0634199c   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/UDF Volume        udf        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077)


=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 7771ba19-c0dc-4e8a-b6e1-d6952f1576d1
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 7771ba19-c0dc-4e8a-b6e1-d6952f1576d1
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 7771ba19-c0dc-4e8a-b6e1-d6952f1576d1
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=7771ba19-c0dc-4e8a-b6e1-d6952f1576d1 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 7771ba19-c0dc-4e8a-b6e1-d6952f1576d1
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=7771ba19-c0dc-4e8a-b6e1-d6952f1576d1 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 7771ba19-c0dc-4e8a-b6e1-d6952f1576d1
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 7771ba19-c0dc-4e8a-b6e1-d6952f1576d1
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=7c2fd557-948c-4a5b-a0a1-423b0634199c none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  58.1GB: boot/grub/core.img
  49.5GB: boot/grub/grub.cfg
  58.1GB: boot/initrd.img-2.6.32-21-generic
  58.1GB: boot/vmlinuz-2.6.32-21-generic
  58.1GB: initrd.img
  58.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  25 6b 32 86 02 82 c4 f0  e0 f0 8c f4 88 4a 69 3d  |%k2..........Ji=|
00000010  7d 8d 77 3a 58 8e 71 46  34 fc e9 99 de 9c 3f 40  |}.w:X.qF4.....?@|
00000020  69 4d 5f f9 46 6e 27 91  a4 1c f1 46 28 0e 30 a1  |iM_.Fn'....F(.0.|
00000030  a3 f4 fb c2 b3 96 a6 cc  a7 d7 03 5f 69 ad 6d ea  |..........._i.m.|
00000040  0c 0f 62 01 5e 49 76 25  1f 8b c9 13 92 15 43 55  |..b.^Iv%......CU|
00000050  5d 43 cf 55 4e 21 a8 a3  71 43 80 f1 b8 8b 47 b8  |]C.UN!..qC....G.|
00000060  73 f2 b3 2f df 95 7d 0f  2a 1d ed ee 83 a7 36 39  |s../..}.*.....69|
00000070  01 37 1f ef 0f 6c 6d 46  c5 a5 d6 56 85 8d 0f 83  |.7...lmF...V....|
00000080  27 d5 c2 9c 41 73 56 cb  78 de 1e 75 55 e5 2a 62  |'...AsV.x..uU.*b|
00000090  9b 87 c5 71 42 03 a8 23  3b 67 e4 47 c0 c4 d8 76  |...qB..#;g.G...v|
000000a0  0e 05 a5 4b 1d 0d 06 64  c2 93 eb 6d 8c b7 49 89  |...K...d...m..I.|
000000b0  f2 d3 8f 8a ab c7 9c f1  01 98 7b f8 fe 72 f4 14  |..........{..r..|
000000c0  96 88 f8 35 98 a3 51 c1  76 5e 6e 86 18 e2 8f 78  |...5..Q.v^n....x|
000000d0  b6 bb 88 04 6c 53 cd cb  99 e3 63 55 48 79 c5 52  |....lS....cUHy.R|
000000e0  7f 01 93 9b bb 30 5e d1  ca 06 e0 bc ba df 9b c2  |.....0^.........|
000000f0  01 56 cf 5a 73 73 c4 2e  1d de 45 62 6b 03 93 cf  |.V.Zss....Ebk...|
00000100  f8 d8 ad 1a 8c dd 64 1b  31 a7 77 c4 3c 1d a9 b3  |......d.1.w.<...|
00000110  5e 7d c5 68 25 2c 06 18  06 24 61 15 dc 4a 91 da  |^}.h%,...$a..J..|
00000120  58 b1 87 e5 06 e9 15 dd  a2 b5 b5 01 b2 5f de 7a  |X............_.z|
00000130  56 25 a7 11 f7 a4 2e 36  5e d7 09 46 8c a0 f9 2f  |V%.....6^..F.../|
00000140  e5 ed ad e8 01 d0 2b 7b  f8 20 f6 13 28 0b c4 c8  |......+{. ..(...|
00000150  c4 c0 68 43 c6 06 f7 7a  20 41 00 91 14 5b 25 0b  |..hC...z A...[%.|
00000160  a0 29 1b da 68 3f 0e f2  89 4d e7 06 c1 67 c3 d2  |.)..h?...M...g..|
00000170  ba 83 4b 18 6e 42 3a 81  ef 4c 4b 1d 5c 64 e4 e4  |..K.nB:..LK.\d..|
00000180  86 af 89 64 6f e2 51 e8  61 36 ee b7 b0 60 c9 f9  |...do.Q.a6...`..|
00000190  55 12 34 31 45 a6 71 3c  2c 72 18 24 14 3c 5c 41  |U.41E.q<,r.$.<\A|
000001a0  21 d3 75 83 5a fe 06 b7  d8 d8 d8 a4 cd 42 1b f0  |!.u.Z........B..|
000001b0  32 7a 73 ae e1 58 76 b1  0a d6 64 e7 c5 fc 00 fe  |2zs..Xv...d.....|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 90 7a 00 00 00  |............z...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by darkod on 2010-05-13
You are missing two windows boot files on its partition, /dev/sda1. Use your win7 dvd and there are instructions here how to repair it:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

The process should leave untouched your grub2 and ubuntu on /dev/sdb. After you have repaired the win7 boot process and you can boot directly into it when /dev/sda is first in BIOS, set /dev/sdb first in BIOS and after booting ubuntu run:

sudo update-grub

That should sort it out.

---

### Post by yezzir on 2010-05-13
> **darkod said:**
> You are missing two windows boot files on its partition, /dev/sda1. Use your win7 dvd and there are instructions here how to repair it:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

The process should leave untouched your grub2 and ubuntu on /dev/sdb. After you have repaired the win7 boot process and you can boot directly into it when /dev/sda is first in BIOS, set /dev/sdb first in BIOS and after booting ubuntu run:

sudo update-grub

That should sort it out.

unfortunately ive tried what is in that link before with no success :(  

bootrec.exe /fixmbr gives 'The operation was completed successfully.'

but bootrec.exe /fixboot gives 'Element not found.'

---

### Post by darkod on 2010-05-13
Have you tried using the automated process? I know the instructions say to do it manually, but sometimes the automated works better.
So, when it detects your win7 and it should, do not deselect it. Continue with the automated process and sometimes you need to run it 3-4 times because it fixes one bit at a time.

If that fails, you could try locating the files on the dvd and just copying them, hoping it works that way. Boot ubuntu, put the win7 dvd in the drive and from the root of the dvd copy 'bootmgr' to /dev/sda1. Then also copy the whole folder 'boot' to /dev/sda1. I have never tried it but it's worth a shot. :)

---

### Post by yezzir on 2010-05-13
> **darkod said:**
> Have you tried using the automated process? I know the instructions say to do it manually, but sometimes the automated works better.
So, when it detects your win7 and it should, do not deselect it. Continue with the automated process and sometimes you need to run it 3-4 times because it fixes one bit at a time.

If that fails, you could try locating the files on the dvd and just copying them, hoping it works that way. Boot ubuntu, put the win7 dvd in the drive and from the root of the dvd copy 'bootmgr' to /dev/sda1. Then also copy the whole folder 'boot' to /dev/sda1. I have never tried it but it's worth a shot. :)

well it also doesnt detect the windows 7 OS :(

i think i will try the 2nd thing you said though lol

---

### Post by yezzir on 2010-05-13
hmm exactly which two files are missing?

---

### Post by yezzir on 2010-05-13
FIXED!  i found another website where someone was having the same sort of problem (i dont remember the link as i am on windows right now lol).

i took out my ubuntu HD and just left the windows one in

to solve:
1. run gparted
2. under flags for the HD, set it to boot
3. run windows 7 repair dvd and repair
4. fin

---

### Post by wilee-nilee on 2010-05-14
Just for future reference you have to run more commands than just the one the best way to go is this with Vista or W7.
BootRec.exe /fixmbr
chkdsk /r
BootRec.exe /FixBoot
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd 
This set would have rebuilt the boot loader, but you would just have to reinstall grub to gthe MBR. If there are missing boot files though then I see why the auto-repair worked without the other HD in as I suspect without being able to look at the script as I type this, that grub was running the 2nd HD.

darkod's instructions should have worked I suspect that there was a bit of the good ole user error involved, but hey it happens to all of us at times. ;)

---

### Post by darkod on 2010-05-14
Windows depends on the boot flag to be on the partition with the boot files, in order to start properly. I didn't notice whether a boot flag was there on yours. Maybe the repair process is so 'intelligent' that it can't repair it if the boot flag is missing. We are talking about windows after all... :)

Anyway, glad you got it sorted out.

---

