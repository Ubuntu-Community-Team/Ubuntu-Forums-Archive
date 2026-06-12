---
title: "installing ubuntu across 2 hard disks"
date: 2011-06-15
forum: Installation &amp; Upgrades
---

### Post by Foxkit on 2011-06-15
I'm looking for a way to install Ubuntu Desktop edition across 2 hard drives with/without RAID/LVM. My attempt at doing so so far has simply produced a lost+found directory at /home with 30 extra gigs that I could use. my computer has the following hard drives:
2 ATA HDS728040PLA320 hard drives
one mounted as / the other on /home as a lost and found directory.

OS: ubutnu 10.10 Desktop edition fresh install. 
Ubuntu Skill: minimal
My reason for wanting this extra space is that I simply only get around 35 gigs for a clean install of ubuntu. Since I came from Windows it could just be paranoia to want extra space. However, I'm also a gamer and games tend to fill up space fast. So another 35-41 gigs would be nice to use. Any help is apreciated since this will also be good experience for if I ever have to help a friend set up their computer likewise.

-Foxkit

---

### Post by oldfred on 2011-06-16
Post this so we can see what is where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by Foxkit on 2011-06-16
```
                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for (,msdos5)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 41.2 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders, total 80418240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     3,905,535     3,903,488  82 Linux swap / Solaris
/dev/sda2           3,907,582    80,416,767    76,509,186   5 Extended
/dev/sda5           3,907,584    80,416,767    76,509,184  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 41.2 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders, total 80418240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb2           3,907,582    80,416,767    76,509,186   5 Extended
/dev/sdb5           3,907,584    80,416,767    76,509,184  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        5bd2cdca-f003-4a6a-837d-4cbe66818568   swap       
/dev/sda5        6631cd3a-1d84-4289-ac97-b8b7fc52f37f   ext4       
/dev/sdb5        dd199cea-0698-404e-b310-249267772c0a   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb5        /home                    ext4       (rw,commit=0)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 6631cd3a-1d84-4289-ac97-b8b7fc52f37f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 6631cd3a-1d84-4289-ac97-b8b7fc52f37f
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 6631cd3a-1d84-4289-ac97-b8b7fc52f37f
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=6631cd3a-1d84-4289-ac97-b8b7fc52f37f ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 6631cd3a-1d84-4289-ac97-b8b7fc52f37f
	echo	'Loading Linux 2.6.35-28-generic ...'
	linux	/boot/vmlinuz-2.6.35-28-generic root=UUID=6631cd3a-1d84-4289-ac97-b8b7fc52f37f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 6631cd3a-1d84-4289-ac97-b8b7fc52f37f
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=6631cd3a-1d84-4289-ac97-b8b7fc52f37f ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 6631cd3a-1d84-4289-ac97-b8b7fc52f37f
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=6631cd3a-1d84-4289-ac97-b8b7fc52f37f ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 6631cd3a-1d84-4289-ac97-b8b7fc52f37f
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 6631cd3a-1d84-4289-ac97-b8b7fc52f37f
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=6631cd3a-1d84-4289-ac97-b8b7fc52f37f /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb5 during installation
UUID=dd199cea-0698-404e-b310-249267772c0a /home           ext4    defaults        0       2
# swap was on /dev/sda1 during installation
UUID=5bd2cdca-f003-4a6a-837d-4cbe66818568 none            swap    sw              0       0
/dev/sdb1       none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  24.219959259 = 26.005983232   boot/grub/core.img                             1
  26.154972076 = 28.083687424   boot/grub/grub.cfg                             1
   8.133953094 = 8.733765632    boot/initrd.img-2.6.35-22-generic              2
   8.175781250 = 8.778678272    boot/initrd.img-2.6.35-28-generic              2
  24.242279053 = 26.029948928   boot/vmlinuz-2.6.35-22-generic                 1
  24.247985840 = 26.036076544   boot/vmlinuz-2.6.35-28-generic                 1
   8.175781250 = 8.778678272    initrd.img                                     2
   8.133953094 = 8.733765632    initrd.img.old                                 2
  24.247985840 = 26.036076544   vmlinuz                                        1
  24.242279053 = 26.029948928   vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  3e c1 da 6e 86 f5 76 fb  cb a2 b2 b4 68 3c a8 74  |>..n..v.....h<.t|
00000010  65 e2 7b 9c c3 cd 32 78  e2 09 47 b9 88 fb f4 41  |e.{...2x..G....A|
00000020  e1 41 03 68 a0 9e 3e 52  31 bd 98 f5 29 f8 8e 30  |.A.h..>R1...)..0|
00000030  b5 88 1e c8 17 7c d2 9e  1e a2 fd e0 3b 76 05 5d  |.....|......;v.]|
00000040  44 9d 45 61 84 8c fb 07  d8 48 c3 50 6e 92 e5 91  |D.Ea.....H.Pn...|
00000050  ff a5 03 45 69 7c f0 b7  80 0a 54 30 31 5b 03 87  |...Ei|....T01[..|
00000060  10 5f d7 bf dd 74 d8 7f  d2 d0 33 fe 41 7b 86 b6  |._...t....3.A{..|
00000070  c6 38 f8 56 f5 bd f9 6d  1b 4b fa 8c 87 97 83 82  |.8.V...m.K......|
00000080  5b 44 73 a7 e0 64 c4 06  b6 3f 6a 8b 94 ed 20 9a  |[Ds..d...?j... .|
00000090  11 33 13 f3 c8 13 bb af  ca cb 56 65 cc 23 bf 85  |.3........Ve.#..|
000000a0  b9 eb e0 9c b0 cf 65 a8  70 72 0f a1 40 d3 b4 ff  |......e.pr..@...|
000000b0  69 bb b5 63 71 7f 74 0e  4e c8 f9 a6 3b a3 85 bc  |i..cq.t.N...;...|
000000c0  2c 4d fd 23 24 30 9e 1c  a6 a0 c4 3a f9 13 cc 88  |,M.#$0.....:....|
000000d0  da e7 5d fc 50 84 b2 77  06 b2 b7 5a 79 ad dc 06  |..].P..w...Zy...|
000000e0  07 ad 48 da a0 66 d6 2a  f2 94 82 75 56 0d 01 a2  |..H..f.*...uV...|
000000f0  3e a9 6e 40 d1 6f d7 10  27 a0 35 45 15 a8 5d 81  |>.n@.o..'.5E..].|
00000100  c6 66 b5 a7 ee 75 c2 71  10 60 bf aa bf fb b0 fd  |.f...u.q.`......|
00000110  fd ab 67 b8 d8 50 b3 66  2f fb 28 f3 17 41 32 2e  |..g..P.f/.(..A2.|
00000120  f8 7b 7f dc 24 7e 41 4f  10 ad 3f 76 e2 f3 39 1a  |.{..$~AO..?v..9.|
00000130  54 c5 de f0 18 fc 63 2a  34 03 64 3f 97 1b 98 48  |T.....c*4.d?...H|
00000140  e2 fc 56 ac 95 a8 ea fe  14 6b 32 55 d7 9a 4a 40  |..V......k2U..J@|
00000150  46 dc 7d a7 71 0d 30 17  ff 7f e5 67 5a 59 63 ae  |F.}.q.0....gZYc.|
00000160  f1 f5 94 57 f6 27 2e b6  98 12 37 2b 61 6c cf 12  |...W.'....7+al..|
00000170  15 1b ba 25 61 63 a5 74  5e 5e a1 4e 39 a9 75 14  |...%ac.t^^.N9.u.|
00000180  86 68 cc 0e 3b 7f 63 de  0d ca 54 b2 67 39 06 5f  |.h..;.c...T.g9._|
00000190  01 7b 49 6d c6 5d 22 79  db ba 56 75 70 a3 44 87  |.{Im.]"y..Vup.D.|
000001a0  86 10 3e d5 f8 b4 6b ff  cd 81 e2 79 2f 38 be 70  |..>...k....y/8.p|
000001b0  82 a9 65 dd 64 1a 9d d5  95 b1 f2 d3 53 19 00 3c  |..e.d.......S..<|
000001c0  0a f3 83 fe ff ff 02 00  00 00 00 70 8f 04 00 00  |...........p....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sdb2

00000000  3e c1 da 6e 86 f5 76 fb  cb a2 b2 b4 68 3c a8 74  |>..n..v.....h<.t|
00000010  65 e2 7b 9c c3 cd 32 78  e2 09 47 b9 88 fb f4 41  |e.{...2x..G....A|
00000020  e1 41 03 68 a0 9e 3e 52  31 bd 98 f5 29 f8 8e 30  |.A.h..>R1...)..0|
00000030  b5 88 1e c8 17 7c d2 9e  1e a2 fd e0 3b 76 05 5d  |.....|......;v.]|
00000040  44 9d 45 61 84 8c fb 07  d8 48 c3 50 6e 92 e5 91  |D.Ea.....H.Pn...|
00000050  ff a5 03 45 69 7c f0 b7  80 0a 54 30 31 5b 03 87  |...Ei|....T01[..|
00000060  10 5f d7 bf dd 74 d8 7f  d2 d0 33 fe 41 7b 86 b6  |._...t....3.A{..|
00000070  c6 38 f8 56 f5 bd f9 6d  1b 4b fa 8c 87 97 83 82  |.8.V...m.K......|
00000080  5b 44 73 a7 e0 64 c4 06  b6 3f 6a 8b 94 ed 20 9a  |[Ds..d...?j... .|
00000090  11 33 13 f3 c8 13 bb af  ca cb 56 65 cc 23 bf 85  |.3........Ve.#..|
000000a0  b9 eb e0 9c b0 cf 65 a8  70 72 0f a1 40 d3 b4 ff  |......e.pr..@...|
000000b0  69 bb b5 63 71 7f 74 0e  4e c8 f9 a6 3b a3 85 bc  |i..cq.t.N...;...|
000000c0  2c 4d fd 23 24 30 9e 1c  a6 a0 c4 3a f9 13 cc 88  |,M.#$0.....:....|
000000d0  da e7 5d fc 50 84 b2 77  06 b2 b7 5a 79 ad dc 06  |..].P..w...Zy...|
000000e0  07 ad 48 da a0 66 d6 2a  f2 94 82 75 56 0d 01 a2  |..H..f.*...uV...|
000000f0  3e a9 6e 40 d1 6f d7 10  27 a0 35 45 15 a8 5d 81  |>.n@.o..'.5E..].|
00000100  c6 66 b5 a7 ee 75 c2 71  10 60 bf aa bf fb b0 fd  |.f...u.q.`......|
00000110  fd ab 67 b8 d8 50 b3 66  2f fb 28 f3 17 41 32 2e  |..g..P.f/.(..A2.|
00000120  f8 7b 7f dc 24 7e 41 4f  10 ad 3f 76 e2 f3 39 1a  |.{..$~AO..?v..9.|
00000130  54 c5 de f0 18 fc 63 2a  34 03 64 3f 97 1b 98 48  |T.....c*4.d?...H|
00000140  e2 fc 56 ac 95 a8 ea fe  14 6b 32 55 d7 9a 4a 40  |..V......k2U..J@|
00000150  46 dc 7d a7 71 0d 30 17  ff 7f e5 67 5a 59 63 ae  |F.}.q.0....gZYc.|
00000160  f1 f5 94 57 f6 27 2e b6  98 12 37 2b 61 6c cf 12  |...W.'....7+al..|
00000170  15 1b ba 25 61 63 a5 74  5e 5e a1 4e 39 a9 75 14  |...%ac.t^^.N9.u.|
00000180  86 68 cc 0e 3b 7f 63 de  0d ca 54 b2 67 39 06 5f  |.h..;.c...T.g9._|
00000190  01 7b 49 6d c6 5d 22 79  db ba 56 75 70 a3 44 87  |.{Im.]"y..Vup.D.|
000001a0  86 10 3e d5 f8 b4 6b ff  cd 81 e2 79 2f 38 be 70  |..>...k....y/8.p|
000001b0  82 a9 65 dd 64 1a 9d d5  95 b1 f2 d3 53 19 00 3c  |..e.d.......S..<|
000001c0  0a f3 83 fe ff ff 02 00  00 00 00 70 8f 04 00 00  |...........p....|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

here is the info you asked for I think. Anything else I should be putting up here?

---

### Post by oldfred on 2011-06-16
Script looks just as you said. Your install is in sda5 and your /home is in sdb5.

But with 30+GB you have lots of room. If from windows you may not realize how much you have. But you cannot run those bloated windows games in Ubuntu anyway.

Your files will be saved in /home and programs in / (root). I have installed a lot of programs (but not games) and have used about 6GB of /. I have all my data in other partitions.

---

### Post by Foxkit on 2011-06-16
> **oldfred said:**
> 
Your files will be saved in /home and programs in / (root). I have installed a lot of programs (but not games) and have used about 6GB of /. I have all my data in other partitions.

So I'm worrying over nothing essentially? if so then maybe I should read more about what a lost+found folder is e.e

---

### Post by oldfred on 2011-06-16
You should be seeing more than just lost & found. But most of the files are hidden with a . at the front. You have to turn on show hidden files & folders to see your configuration files. 

I think lost & found is just where files that get corrupted may go. If you delete something it will then go into trash which may not yet exist.

---

### Post by Foxkit on 2011-06-16
alright, if I turn on see hidden files in my /home folder I see nothing new. just these two things:
lost+found
my-username(edited)

now I can't access lost+found, says I don't have permission to. but my-username is where Desktop,Picture, Music, Videos, and Downloads are kept along with the hidden files you mentioned earlier. Since its been verified that sdb5 mounts in /home i'm assuming that its mounting as the lost+found folder. If I didn't state this clearly enough in my OP I apologize. my main request was to see how one would go about installing Ubuntu across multiple hard drives, if at all possible. Or if it isn't, how to use a second hard drive as a data storage for linux, for things like media and music maybe.

edit1: I see what you mean, yes i'm being an idiot and worrying over nothing, sorry to bother you again. -Foxkit

---

