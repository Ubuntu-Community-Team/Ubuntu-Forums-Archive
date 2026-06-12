---
title: "How to skip Windows Loader using GRUB2"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by vampire666eng on 2010-05-22
Hi there.

I would like to have some entries in GRUB2 so that I can directly boot Windows XP and Seven without having to load the Windows bootloader (so I would like to avoid one step, 
now is: load GRUB2 --> then Windows loader --> then Windows boots. 
I would like it to be: load GRUB2 --> then Windows boots). 
Is this possible?

This is what I have now in my grub.cfg

```

cat << EOF

menuentry "Windows Operating Systems (XP & Seven)" {
set root=(hd0,1)
chainloader (hd0,1)+1
}

menuentry 'Ubuntu 10.04 - Linux' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,7)'
	search --no-floppy --fs-uuid --set cd1b2614-9f2f-4a10-8b11-926c6d55d9c0
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=cd1b2614-9f2f-4a10-8b11-926c6d55d9c0 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}

menuentry 'Ubuntu 10.04 - Linux (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,7)'
	search --no-floppy --fs-uuid --set cd1b2614-9f2f-4a10-8b11-926c6d55d9c0
	echo	'Caricamento Linux 2.6.32-22-generic...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=cd1b2614-9f2f-4a10-8b11-926c6d55d9c0 ro single 
	echo	'Caricamento ramdisk iniziale...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}

EOF

```

As you can see, when GRUB2 is loaded I have:

Windows Operating Systems (XP & Seven)
Ubuntu 10.04 - Linux
Ubuntu 10.04 - Linux (recovery mode)

When I select "Windows Operating Systems (XP & Seven)" I find myself in the Windows loader with the option of running Window XP, Windows Seven, and an option to go back to GRUB2.

So in the Windows loader I have:

Windows XP
Windows Seven
Linux Operating Systems.

What I want in GRUB2:

Windows XP
Windows Seven
Ubuntu 10.04 - Linux
Ubuntu 10.04 - Linux (recovery mode)

So that when I select one of the Windows entries it will directly load the operating system and not the Windows loader.

Is this possible?

P.S.
Sda1 (HD0,1) is Windows XP
Sda2 (HD0,2) is Windows Seven
Sdb7 (HD1,7) is Ubuntu 10.04

Thanks a bunch. :)

---

### Post by darkod on 2010-05-22
The problem is that windows combines the boot files when you have two versions installed. After that there is nothing ubuntu can do to boot both versions directly.

You should be able to do this, if you are willing to play around with the windows boot files. Basically I think you would need to add XP boot files to the XP partition.

Just for information, if before installing the second version of windows, you moved the boot flag onto the new planned partition, the boot files of the second version would stay there and be independent of the first version.

---

### Post by vampire666eng on 2010-05-22
Thanks for the reply.
It looks like I would have to do some testing and probably "some messing up"...well, I do not feel to do that now (coward!8-[) so I guess I'll have to keep things as they are, which is fine. :)

Thanks again.

---

### Post by darkod on 2010-05-22
Also for your own info, you might wanna run the boot info script and look at the results, it's very informative:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

The script link is in my signature. You will clearly see part of the boot files combined on one partition.

XP uses boot.ini, ntldr and ntdetect.
7 uses bootmgr, boot/bcd and winload.

It will also give you info what is where if you decide to do anything later.

---

### Post by Arand on 2010-05-22
As far as I know, only the windows boot loader can boot windows, so you are locked by that.
However, you might be able to either boot two separate versions of BCD (with different defaults and no timeout), or boot NTLDR directly for XP.

This will required some considerable looking into though, and possibly some reinstalling and messing about with BCD.

And since I don't know how to do it specifically, I can only supply hints.

One major problem you have there, as far as I can see is that the Vista bootcode has replaced the XP bootcode on the first partition.
So my guess is that your options are either to install a separate instance of BCD which has its associated bootcode on (hd0,2 = sda2) and set defaults and timeouts on that.
Or somehow just migrate the Vista bootcode onto (hd0,2) (Don't know if it would be able to load BOOTMGR from another partition though (What would a simple dd do?)) and get the XP bootcode, and NTLDR setup on (hd0,1) (Windows recovery fixmbr&fixboot, and then reinstate grub mbr).

Those only guesses though, don't know if it would work/is possible.

References:
[http://en.wikipedia.org/wiki/Windows_Vista_startup_process](http://en.wikipedia.org/wiki/Windows_Vista_startup_process)
[http://en.wikipedia.org/wiki/Windows_NT_startup_process](http://en.wikipedia.org/wiki/Windows_NT_startup_process)
[http://en.wikipedia.org/wiki/NTLDR](http://en.wikipedia.org/wiki/NTLDR)
[http://articles.techrepublic.com.com/5100-10878_11-6169638.html](http://articles.techrepublic.com.com/5100-10878_11-6169638.html)

- Arand

---

### Post by vampire666eng on 2010-05-22
@darkod
Nice script darkod! Very useful, thanks!
I gave a quick look at the generated file, and there's lots of nice info there. I'll definitely check it out better afterworlds. 

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #7 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /grldr /ntldr 
                       /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr /ntldr /ntdetect.com

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 500.1 GB, 500107862016 byte
255 testine, 63 settori/tracce, 60801 cilindri, totale 976773168 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   144,199,439   144,199,377   7 HPFS/NTFS
/dev/sda2         144,199,440   976,768,064   832,568,625   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disco /dev/sdb: 500.1 GB, 500107862016 byte
255 testine, 63 settori/tracce, 60801 cilindri, totale 976773168 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   209,728,574   209,728,512   7 HPFS/NTFS
/dev/sdb2         209,728,636   976,773,119   767,044,484   f W95 Ext d (LBA)
/dev/sdb5         209,728,638   913,841,459   704,112,822   7 HPFS/NTFS
/dev/sdb6         968,773,632   976,773,119     7,999,488  82 Linux swap / Solaris
/dev/sdb7         913,842,176   968,767,487    54,925,312  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disco /dev/sdc: 400.1 GB, 400088457216 byte
16 testine, 63 settori/tracce, 775221 cilindri, totale 781422768 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          1,008   781,422,767   781,421,760   f W95 Ext d (LBA)
/dev/sdc5               1,071   781,422,767   781,421,697   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        400CA0950CA0878C                       ntfs       Windows XP (Seagate)          
/dev/sda2        7CC8F432C8F3E7F2                       ntfs       Windows 7 (Seagate)           
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4464E55864E54D6C                       ntfs       Programmi (Hitachi 2)         
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        150FEB997A0C56B9                       ntfs       VideoGames (Hitachi 2)        
/dev/sdb6        3f6297ae-a2b0-46e9-8eb9-295ac48fbdbc   swap                                     
/dev/sdb7        cd1b2614-9f2f-4a10-8b11-926c6d55d9c0   ext4                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1: PTTYPE="dos" 
/dev/sdc5        60BCECE3BCECB526                       ntfs       Downloads (Hitachi)           
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb7        /                        ext4       (rw,errors=remount-ro)
/dev/sdc5        /media/sdc5              fuseblk    (ro,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT /usepmtimer


=========================== sdb7/boot/grub/grub.cfg: ===========================

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
set root='(hd1,7)'
search --no-floppy --fs-uuid --set cd1b2614-9f2f-4a10-8b11-926c6d55d9c0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=1024x768
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,7)'
search --no-floppy --fs-uuid --set cd1b2614-9f2f-4a10-8b11-926c6d55d9c0
set locale_dir=($root)/boot/grub/locale
set lang=it
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=5
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root='(hd1,7)'
search --no-floppy --fs-uuid --set cd1b2614-9f2f-4a10-8b11-926c6d55d9c0
insmod tga
if background_image /boot/grub/amazing-black_1024x768.tga ; then
  set color_normal=white/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/light-gray
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

echo "Adding Windows Operating Systems to GRUB 2 menu" >&2
cat << EOF
menuentry "Windows Operating Systems (XP & Seven)" {
set root=(hd0,1)
chainloader (hd0,1)+1
}
menuentry 'Ubuntu 10.04 - Linux' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,7)'
	search --no-floppy --fs-uuid --set cd1b2614-9f2f-4a10-8b11-926c6d55d9c0
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=cd1b2614-9f2f-4a10-8b11-926c6d55d9c0 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu 10.04 - Linux (modalità ripristino)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,7)'
	search --no-floppy --fs-uuid --set cd1b2614-9f2f-4a10-8b11-926c6d55d9c0
	echo	'Caricamento Linux 2.6.32-22-generic...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=cd1b2614-9f2f-4a10-8b11-926c6d55d9c0 ro single 
	echo	'Caricamento ramdisk iniziale...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
EOF
### END /etc/grub.d/40_custom ###

=============================== sdb7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc       /proc        proc  nodev,noexec,nosuid         0  0  
/dev/sda7  /            ext4  errors=remount-ro           0  1  
/dev/sda6  none         swap  sw                          0  0  
/dev/sdc5  /media/sdc5  ntfs  nls=iso8859-1,ro,umask=000  0  0  

=================== sdb7: Location of files loaded by Grub: ===================


 470.2GB: boot/grub/core.img
 470.7GB: boot/grub/grub.cfg
 470.7GB: boot/initrd.img-2.6.32-21-generic
 471.1GB: boot/initrd.img-2.6.32-22-generic
 471.1GB: boot/vmlinuz-2.6.32-21-generic
 468.2GB: boot/vmlinuz-2.6.32-22-generic
 471.1GB: initrd.img
 470.7GB: initrd.img.old
 468.2GB: vmlinuz
 471.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  e8 12 01 b9 f0 01 be 10  7c bf 10 06 57 f3 a4 c3  |........|...W...|
00000010  8b 4e 14 83 f9 0e 75 08  8d 5e 07 43 02 07 e2 fb  |.N....u..^.C....|
00000020  8c 56 0c 8c 56 0e 75 69  8a 56 10 84 d2 79 62 e8  |.V..V.ui.V...yb.|
00000030  f6 00 bb aa 55 cd 13 72  6f 3b 5e 5c 75 6a d1 e9  |....U..ro;^\uj..|
00000040  73 66 b4 42 c6 46 02 01  eb 66 89 b6 f6 fe 8a 44  |sf.B.F...f.....D|
00000050  04 84 c0 74 0f 3c 05 74  0b 3c 0f 74 07 8a 14 80  |...t.<.t.<.t....|
00000060  e2 80 75 cb 83 c6 10 06  c4 5c 08 89 5e 08 8c 46  |..u......\..^..F|
00000070  0a 07 fe 8e f9 fe 75 d2  b0 31 c6 46 d7 50 88 46  |......u..1.F.P.F|
00000080  d4 be 6a 07 ac 84 c0 74  08 b4 0e b3 07 cd 10 eb  |..j....t........|
00000090  f3 e8 81 00 88 46 11 be  ae 07 3c 05 75 c6 cd 16  |.....F....<.u...|
000000a0  33 d2 89 56 08 89 56 0a  e8 7d 00 72 1b b8 01 02  |3..V..V..}.r....|
000000b0  bf 05 00 8b dc 56 50 50  32 e4 cd 13 58 8b f5 cd  |.....VPP2...X...|
000000c0  13 58 5e 73 03 4f 75 eb  b0 32 72 b2 40 8a 66 11  |.X^s.Ou..2r.@.f.|
000000d0  9e 7b 04 c6 47 02 0e 72  35 75 0c 88 57 40 c4 4e  |.{..G..r5u..W@.N|
000000e0  08 89 4f 1c 8c 47 1e 79  06 8a 4e 12 88 4f 25 80  |..O..G.y..N..O%.|
000000f0  c7 02 81 7f fe 55 aa 75  85 81 7f fa cd 19 75 09  |.....U.u......u.|
00000100  c6 47 fa e9 c7 47 fb 94  88 e8 1c 00 ff e4 74 ce  |.G...G........t.|
00000110  88 57 24 eb c9 5d 33 c0  8e d8 8e c0 8e d0 bc 00  |.W$..]3.........|
00000120  7c 55 bd a2 07 fc fb c3  b4 08 52 06 cd 13 07 72  ||U........R....r|
00000130  33 33 db 8a de 8b 46 0a  33 d2 83 e1 3f f7 f1 91  |33....F.3...?...|
00000140  97 8b 46 08 f7 f7 42 87  ca 3b da 72 17 43 f7 f3  |..F...B..;.r.C..|
00000150  8a f2 86 c5 d1 e8 d1 e8  0a c8 d0 cc d0 cc 0a f4  |................|
00000160  84 e4 74 02 b4 41 5b 8a  d3 c3 0d 0a 4d 42 52 20  |..t..A[.....MBR |
00000170  45 72 72 6f 72 20 00 0d  0a 00 72 65 73 73 20 61  |Error ....ress a|
00000180  6e 79 20 6b 65 79 20 74  6f 20 62 6f 6f 74 20 66  |ny key to boot f|
00000190  72 6f 6d 20 66 6c 6f 70  70 79 2e 2e 2e 00 00 00  |rom floppy......|
000001a0  00 00 10 00 01 00 00 7c  00 00 5f 55 51 00 00 00  |.......|.._UQ...|
000001b0  00 00 80 00 00 6d 0e 00  ea 2c eb 2c 00 00 80 01  |.....m...,.,....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 d1 4e 98 08 00 fe  |......?....N....|
000001d0  ff ff 07 fe ff ff 10 4f  98 08 31 fd 9f 31 00 00  |.......O..1..1..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

@Arand
thank you very much for your considerations and info/links.

I'm starting to think that probably all this is not worth the time and possible problems that may arise messing with these things...it's still interesting though. :wink:

---

