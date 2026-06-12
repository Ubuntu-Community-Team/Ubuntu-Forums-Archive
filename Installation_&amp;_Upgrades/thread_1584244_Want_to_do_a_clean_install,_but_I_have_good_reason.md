---
title: "Want to do a clean install, but I have good reason to think I will break the computer"
date: 2010-09-28
forum: Installation &amp; Upgrades
---

### Post by rhoparkour on 2010-09-28
I have this Compaq Presario I want to clean install Ubuntu on, but there is one problem.

When trying it out from livecd or using the installed ubutnu partition , I can't mount the main windows partition, it gives me an error (see bootinfoscript output at the end, it's the same error).

I have to completely disable grub to run vista, it seems that grub just won't recognize the vista partition (it recognizes the recovery one, though and boots into that one if I choose vista at the grub menu).

Mind you, I had tried to do a dual boot on this. Shrank the windows partition with the windows tools to make room for Ubuntu, still had problems. Vista is working fine, after disabling grub.  Seems the solution for the problems with my dual boot is to just go all out Ubuntu, which is fine.

So now, my question is: with this problem can I do a clean install and not ruin this computer? Is the fault a hardware or a software fault that can be fixed by formatting the drive during this clean install?

Bootinfoscript to see what I mean, look at the vista partition sda1:

```

rho@Verde:~/Downloads$ cat RESULTS.txt 
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   188,514,838   188,514,776   7 HPFS/NTFS
/dev/sda2         218,419,740   234,436,544    16,016,805   7 HPFS/NTFS
/dev/sda3         188,516,350   218,419,199    29,902,850   5 Extended
/dev/sda5         188,516,352   217,069,567    28,553,216  83 Linux
/dev/sda6         217,071,616   218,419,199     1,347,584  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        A2E2F499E2F472C1                       ntfs                                     
/dev/sda2        2C88743C8874071C                       ntfs       PRESARIO_RP                   
/dev/sda3: PTTYPE="dos" 
/dev/sda5        9defec7f-50e5-4477-b9e5-09965f467fa7   ext4                                     
/dev/sda6        05c7c5db-6da2-4ff6-a7e2-db7a5f00c069   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 9defec7f-50e5-4477-b9e5-09965f467fa7
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 9defec7f-50e5-4477-b9e5-09965f467fa7
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 9defec7f-50e5-4477-b9e5-09965f467fa7
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=9defec7f-50e5-4477-b9e5-09965f467fa7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 9defec7f-50e5-4477-b9e5-09965f467fa7
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=9defec7f-50e5-4477-b9e5-09965f467fa7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 9defec7f-50e5-4477-b9e5-09965f467fa7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 9defec7f-50e5-4477-b9e5-09965f467fa7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 2c88743c8874071c
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=9defec7f-50e5-4477-b9e5-09965f467fa7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=05c7c5db-6da2-4ff6-a7e2-db7a5f00c069 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 101.0GB: boot/grub/core.img
  99.0GB: boot/grub/grub.cfg
 101.0GB: boot/initrd.img-2.6.32-24-generic
 101.0GB: boot/vmlinuz-2.6.32-24-generic
 101.0GB: initrd.img
 101.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  91 a0 32 15 1d 7b 2d ee  80 21 8a 30 18 ed 23 b2  |..2..{-..!.0..#.|
00000010  4d 73 66 c1 2b 67 9a d5  0d 87 30 d2 7d a0 d9 b9  |Msf.+g....0.}...|
00000020  02 e8 cc a5 f0 15 16 21  c1 5f 60 7c 81 15 a9 63  |.......!._`|...c|
00000030  1e 81 7c 63 09 13 89 78  07 44 da c0 ae 95 ef 0b  |..|c...x.D......|
00000040  d0 c9 7a 81 55 57 88 e0  53 2a cb 3e b9 26 c8 43  |..z.UW..S*.>.&.C|
00000050  2e af 9f e3 1d e6 7a 88  f1 af ac ae 11 97 99 b1  |......z.........|
00000060  04 80 71 1f 49 79 af af  d8 33 3e a7 70 75 40 b4  |..q.Iy...3>.pu@.|
00000070  0c ac c9 02 90 d1 f3 2c  bf 82 15 89 de ec 84 15  |.......,........|
00000080  75 e3 32 4e f7 5c 6c a8  7e a3 b1 84 3e 7c 53 b5  |u.2N.\l.~...>|S.|
00000090  40 86 be 78 00 59 1e 92  96 9a 7b 37 09 0e 0c 88  |@..x.Y....{7....|
000000a0  fd 34 09 aa 47 a3 78 a0  23 6e 5d 53 28 27 0e eb  |.4..G.x.#n]S('..|
000000b0  19 e0 2b d9 79 f4 49 d2  eb b3 e8 52 27 7c 78 a9  |..+.y.I....R'|x.|
000000c0  4b 0f d9 28 2c 86 fa 26  8d a1 1c 10 9a ba 22 46  |K..(,..&......"F|
000000d0  d9 4e 10 63 ba 7e c3 cc  72 29 b7 6c 01 e2 43 fd  |.N.c.~..r).l..C.|
000000e0  db 24 f1 0c c5 95 c0 60  f3 4b ab 7d 88 af da b8  |.$.....`.K.}....|
000000f0  5d fc 00 ca 9f 4f 62 8f  0e ad 8b 7a 66 12 a5 6a  |]....Ob....zf..j|
00000100  40 c9 85 06 3a 50 87 58  aa a7 ba a6 6e ab 8b 5d  |@...:P.X....n..]|
00000110  fa e6 c9 19 f5 6b dc 2a  6a ec fb 4c 2e f5 c0 7a  |.....k.*j..L...z|
00000120  d5 eb 0e f5 c4 2a 72 92  df 08 5d 36 28 79 bd 77  |.....*r...]6(y.w|
00000130  bc ed ff 47 09 ac f1 a7  e0 d5 78 d0 bd fe ec 9a  |...G......x.....|
00000140  05 f8 49 96 0f 9a 1d 9c  3f 14 16 a9 1d a3 d1 c6  |..I.....?.......|
00000150  a0 ed c6 f6 c4 cf 55 fc  b4 ba 6e e3 09 ba 83 db  |......U...n.....|
00000160  d8 a7 e5 cd 73 4d 11 ff  a7 4b 40 07 6d 74 58 b6  |....sM...K@.mtX.|
00000170  10 ec c2 33 78 e5 28 90  d9 b1 01 7b 8e 20 bb af  |...3x.(....{. ..|
00000180  f6 33 9d ab 9b af 96 26  f4 70 f6 9c b1 be b1 1d  |.3.....&.p......|
00000190  f5 50 37 3d be 26 5d 78  97 b6 10 af c7 6b a2 73  |.P7=.&]x.....k.s|
000001a0  27 09 39 2e a0 8e e3 db  0b 98 74 b8 79 91 fe f8  |'.9.......t.y...|
000001b0  f5 2c e8 97 a0 2a 9b 96  6f 06 8a 7d b9 77 00 fe  |.,...*..o..}.w..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 b0 b3 01 00 fe  |................|
000001d0  ff ff 05 fe ff ff ca b2  b3 01 38 95 14 00 00 00  |..........8.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by quixote on 2010-09-29
Did you run chkdsk /f as the bootinfo script suggests?  It's a good idea to do that.  Or whatever Vista prefers.  Chkdsk sound kind of DOS-days to me.  Didn't they move to scandisk or something more recently?  (It's been years since I used Windows, and then it was XP, so my memory on all this is iffy.)

The weirdness with grub not giving you the right Vista choice is because there's something wrong with the MBR.  You have some sort of MBR on sda3, and since that's your extended partition it definitely shouldn't be there.  It should be on /dev/sda, i.e in the MBR of the whole device, and not on a specific partition. You obviously have a functioning grub2 there, but maybe it's not accessing your main Vista partition because of errors on that partition, which chkdsk would presumably fix.  (Putting grub on a partition used to be considered okay, but since Grub2 they've frowned on it.  I don't know the technical details of what changed.)

After you run chkdsk (or the equivalent) on the main Vista partition and it reports no errors, try [reinstalling grub2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202").

---

### Post by lisati on 2010-09-29
I wouldn't sweat it over grub's identification of the Windows partition too much. On my server machine, which has a recovery and small XP partition "just in case", I had to manually edit grub's descriptions because grub had accidentally swapped the descriptions. A similar thing happened on my laptop, which has Vista. On both machines the Windows partitions seem to boot correctly even though the description is incorrect.

---

### Post by rhoparkour on 2010-09-30
Well, I did run chkdisk /f, twice before the bootscript.

So, do you guys think a clean install is safe? I don't mind losing Vista at all, the owner of the computer has already worked enough on mine to see that Ubuntu is capable of everything she needs, and it would be nice to have all the extra space on the drive!

---

### Post by quixote on 2010-09-30
If your computer is working well when you run your current install of ubuntu -- wireless works, sound works, usb works, printer works, and anything else you need -- then a clean install will be fine.  Having Vista on the computer neither helps nor hurts the ubuntu install, so it won't run any different if Vista isn't there.

When you're reinstalling ubuntu, select manual partitioning and be sure NOT to select the Vista partition for formatting.  Then it won't touch it.  The fact that grub is currently confused may or may not change, like lisati says it doesn't always matter all that much, but the Vista will still be there.

---

### Post by rhoparkour on 2010-09-30
I´m not really worried about having vista or not, please take a look at thje first few lines of the bootinfoscript, there seems to be aproblem in the windows partition. 
 
Let me refrase this question, will this matter when performing a fresh ubuntu install?
 
Again, losing vista is not a problem, I know the comp will run great without it.
 
Let me rephrase this, is the partition ´formatable´? So that it can be formatted into an ubuntu partition. Again, the bootinfoscript error suggest that I may run into trouble when Ubuntu formats the drive to install itself.
 
Thanks for the help! I´m staring to think a fresh clean ubuntu install will format the drive and solve the problem in the bootinfoscript.

---

### Post by quixote on 2010-09-30
Given that your Vista runs okay, the errors aren't likely to be hardware.  If you reformat the whole drive for ubuntu, any hd format or ntfs errors will disappear.  (They wouldn't, obviously, if it was a hardware issue.  But if you reformat to a new filesystem, ext4 for ubuntu, the old filesystem's problems become moot.)  If you don't want to reformat the Vista partition, I don't think you need to.  It'll continue to complain about this stuff, but since things run regardless, you don't absolutely have to get rid of it unless you want to.

So, just to be clear, no, I don't think it will matter at all for a clean install.

---

### Post by rhoparkour on 2010-09-30
Sounds good, it would be nice to free up space by killing Vista at last on that computer!

I'll mark this as solved when I do it this weekend...

Thank you for the help.

---

