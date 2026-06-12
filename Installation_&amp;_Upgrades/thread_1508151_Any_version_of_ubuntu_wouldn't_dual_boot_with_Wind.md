---
title: "Any version of ubuntu wouldn't dual boot with Windows Vista"
date: 2010-06-12
forum: Installation &amp; Upgrades
---

### Post by epz on 2010-06-12
Hello, 
 I recently had to add a Windows Vista partition to my beloved laptop which has Xubuntu installed.

  I preferred wiping the whole hard disk and installing vista first so i wouldn't have to reset grub but, when i boot xubuntu (tried all of them by the way) it won't be able to see (nor mount unless i mount it with ntfs-config or mount -t ntfs-3g /dev/sda2). 

 Seeing this I thought it wouldn't have been a problem at all, rather an advantage, since without me the Vista partition wouldn't mount (pretty useful according to me). 
Now the problem is that after i do that my vista partition won't start properly, I'll still find it in the grub (as Windows Vista (loader)) but it won't start, once selected it will load, prompt me to the loading windows (where you see all that junk about copyright by microsoft) and restart, without any error or such. 

 Here my partitions 
/dev/sda1  Xubuntu ext4 
/dev/sda2  Vista NTFS (of course lol)
 /dev/sda3  swap 
/dev/sda5  Fat32 (was meant to not make me mount ntfs but i forgot it lol) 

 If the informations I given are little or not enough please ask more and if you think you have enough i'd be very pleased if anyone of you might help me sort it out, i'd really be upset if now ubuntu started giving me pains since i hadn't any in like 4 years? and that's great compared to windows >.<

  Thanks alot 

  ps: hope you'll forgive my english I'm not anglophone and I wouldn't define my english that great lol.  

ps2: please don't suggest to use my laptop as freesbie or to suicide, i thought about it and i actually don't feel like it, also,  i dislike windows so noone flame it please or i'll have to agree =D. Oh and , yes, UBUNTUforums means that you aren't supposed to help me here but probably someone had my same problem? hopefully =P

---

### Post by X-Windows on 2010-06-12
Open the terminal and enter **sudo update-grub**. That should refresh your grub loader and check for other operating systems. There are more advanced ways to configure the grub others can help you with if that fails.

---

### Post by epz on 2010-06-12
thank you very much for your answer, sadly i tried it earlier and it didn't do anything.
 At the moment what rly makes me go O_O irl is the fact that the loading screen loads, after loading restart, this is sooo bad, i'll have to add sugar and like it tho since it's requested =/

---

### Post by epz on 2010-06-12
mmm do I have to assume im in troubles? 1 answer so far lol

---

### Post by darkod on 2010-06-12
I'm not sure I understood properly what is the problem? After you mount the vista partition, it can't boot properly? And as long as you never mount it, it boots fine?

You can run the boot info script to show any possible issues and post the content of the results file. There are instructions here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by epz on 2010-06-12
yes you got it, i mounted my vista partition from ubuntu (to move some files) when i restarted to use them (drivers and sp lol) it didn't work, vista goes to loading screen and then restarts with no errors.  About the script, do i need to be in a live session? Because its pretty painful here without nvidia drivers and i'll need to download xubuntu live (i used alternate >.

---

### Post by darkod on 2010-06-12
No, it works from hdd installation or live mode. Usually it's for people who can't boot ubuntu or at all, so the post is mostly written from the aspect of live mode. :)

---

### Post by epz on 2010-06-12
Here it is, sorry for the delay, been a little busy and thanks for your help so far.

```
     Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
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

/dev/sda1               2,048   245,762,047   245,760,000  83 Linux
/dev/sda2    *    245,762,048   467,914,751   222,152,704   7 HPFS/NTFS
/dev/sda3         467,916,798   487,444,479    19,527,682   5 Extended
/dev/sda5         467,916,800   483,538,943    15,622,144  82 Linux swap / Solaris
/dev/sda6         483,540,992   487,444,479     3,903,488   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        07896113-4cbc-4c72-b70d-103ebd810e9b   ext4                                     
/dev/sda2        3E16216E162127FB                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        02313af6-738b-413a-8c78-3e4b664348a8   swap                                     
/dev/sda6        A397-F2C8                              vfat                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 07896113-4cbc-4c72-b70d-103ebd810e9b
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 07896113-4cbc-4c72-b70d-103ebd810e9b
set locale_dir=($root)/boot/grub/locale
set lang=it
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 07896113-4cbc-4c72-b70d-103ebd810e9b
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=07896113-4cbc-4c72-b70d-103ebd810e9b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 07896113-4cbc-4c72-b70d-103ebd810e9b
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=07896113-4cbc-4c72-b70d-103ebd810e9b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 07896113-4cbc-4c72-b70d-103ebd810e9b
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=07896113-4cbc-4c72-b70d-103ebd810e9b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 07896113-4cbc-4c72-b70d-103ebd810e9b
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=07896113-4cbc-4c72-b70d-103ebd810e9b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 07896113-4cbc-4c72-b70d-103ebd810e9b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 07896113-4cbc-4c72-b70d-103ebd810e9b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 3e16216e162127fb
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=07896113-4cbc-4c72-b70d-103ebd810e9b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=02313af6-738b-413a-8c78-3e4b664348a8 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  17.3GB: boot/grub/core.img
  17.3GB: boot/grub/grub.cfg
  15.4GB: boot/initrd.img-2.6.32-21-generic
  15.5GB: boot/initrd.img-2.6.32-22-generic
  25.9GB: boot/vmlinuz-2.6.32-21-generic
    .2GB: boot/vmlinuz-2.6.32-22-generic
  15.5GB: initrd.img
  15.4GB: initrd.img.old
    .2GB: vmlinuz
  25.9GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  10 3f 2a e7 a6 84 44 40  8b e5 a7 e1 a1 aa 56 bd  |.?*...D@......V.|
00000010  28 3d 8e ae 02 2b eb 7f  48 7a 44 65 13 cf 7c df  |(=...+..HzDe..|.|
00000020  1d 32 17 83 30 92 b1 b5  b3 90 b7 ba 58 06 c4 de  |.2..0.......X...|
00000030  9e 65 f0 c9 de d4 5b 05  6c f0 27 06 7f b2 38 bd  |.e....[.l.'...8.|
00000040  8d 08 a7 86 ff 8b 8c af  86 9c ba 59 1c bc 5a d4  |...........Y..Z.|
00000050  4a c7 0c 46 63 00 38 27  8e cb 3b 86 17 57 78 65  |J..Fc.8'..;..Wxe|
00000060  a7 ed e3 e4 a5 8d c3 2a  f8 16 25 e0 43 b5 da ea  |.......*..%.C...|
00000070  a9 89 2c 9f 88 77 57 ef  5b 26 5a 89 7a f3 9e 8f  |..,..wW.[&Z.z...|
00000080  1b f2 90 d4 51 6b 0b 6d  aa c0 09 a6 ee 95 e1 1f  |....Qk.m........|
00000090  3b db d0 e3 84 0c 59 d3  37 8a 1b 0f 99 80 d5 00  |;.....Y.7.......|
000000a0  ad 96 12 af 12 17 dd 55  f9 99 fa 27 d0 84 0b f7  |.......U...'....|
000000b0  5f 57 2f e0 2c 88 91 bc  69 dd 01 e6 ae 01 d8 c2  |_W/.,...i.......|
000000c0  17 e4 35 dd b5 a6 c0 4a  44 f6 f3 5a a5 6d ad c9  |..5....JD..Z.m..|
000000d0  54 1d 59 2d 20 c0 85 88  e9 98 5b da c6 7d 8b 32  |T.Y- .....[..}.2|
000000e0  48 5a 21 c6 0c 00 f6 ed  46 00 5a bb 84 f0 a7 dc  |HZ!.....F.Z.....|
000000f0  2c a2 ea 78 3f 35 9d d9  a4 33 1d 6d 42 8a f1 b0  |,..x?5...3.mB...|
00000100  29 53 eb b2 3d 38 2a 7d  4f 51 f8 3b 38 0a 56 cb  |)S..=8*}OQ.;8.V.|
00000110  79 dc 7a 6e 03 77 13 be  42 95 bb fe 15 3b dd c0  |y.zn.w..B....;..|
00000120  54 19 12 0b f0 e2 31 65  71 a9 5b 1a 0b 85 2d 6b  |T.....1eq.[...-k|
00000130  5e a4 1b 93 63 17 cf 05  86 c5 63 ac e1 db 56 b0  |^...c.....c...V.|
00000140  ed 32 83 4b b3 82 49 49  0d bb 4e d6 51 2c ff 4d  |.2.K..II..N.Q,.M|
00000150  b6 c2 3b 23 50 4b 9b 7f  01 5c dd 7a 4b 6f 0b e4  |..;#PK...\.zKo..|
00000160  9d 53 1f 9f 28 43 c3 f8  ec 79 c8 0e 82 9c 93 32  |.S..(C...y.....2|
00000170  b6 07 bb c3 cc e2 ed ed  a3 51 e9 34 3e ae 4a 48  |.........Q.4>.JH|
00000180  3c 39 ed a2 5f 94 28 72  c9 3d 10 fb ba a0 4b 32  |<9.._.(r.=....K2|
00000190  04 64 ea 49 ce bd 48 17  4f 84 fb c8 c6 e9 74 28  |.d.I..H.O.....t(|
000001a0  f2 72 1b 47 8f 2b 76 cd  66 a9 86 1a 01 46 de 92  |.r.G.+v.f....F..|
000001b0  97 9b 00 1f 7b 1b a9 68  48 ab 76 f9 a3 69 00 fe  |....{..hH.v..i..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 60 ee 00 00 fe  |...........`....|
000001d0  ff ff 05 fe ff ff d5 65  ee 00 2d 92 3b 00 00 00  |.......e..-.;...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb 

```

---

### Post by darkod on 2010-06-12
I can't see anything wrong with it. :(

And I have no idea why mounting the vista partition would "break it". Ubuntu usually plays nice with other OSs.

But we can make a test. Lets see if mounting it with a command in terminal will do the same. If it's still set to mount automatically with ntfs-config or similar, open the program and disable the auto mount. Also if there is entry in /etc/fstab, comment it out with # in front.

Do you expect vista to boot after that?

---

### Post by epz on 2010-06-12
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=07896113-4cbc-4c72-b70d-103ebd810e9b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=02313af6-738b-413a-8c78-3e4b664348a8 none            swap    sw              0       0

```

unless I'm blind (probably lol) but  this is ok according to me.


and about unmounting i tried it, and to mount i used both ntfs config (first install then wiped hd) and terminal with mount -t ntfs-3g /dev/sda2


still thanks for your help so far.

---

### Post by epz on 2010-06-13
News: I noticed that after some trying the safe mode starts (vista), I don't know if that would ever help (last time i used windows was like...3 years ago?), would it mean anything?

---

### Post by fidelfloris on 2010-06-13
> **darkod said:**
> No, it works from hdd installation or live mode. Usually it's for people who can't boot ubuntu or at all, so the post is mostly written from the aspect of live mode. :)


Dear Ubuntu user,

I have a simular problem, if you tell me what you need to know maybe you can help me to?

Greetings Fidel

---

### Post by epz on 2010-06-13
Another thing, if I use gparted to mount the NTFS partition it will say that the device drive is locked, same with the fat32 partition I made to not make vista crash (use it to transfer files lol) even if i make it with gparted it wont mount because it's locked. I had to use ntfsconfig to mount that but if i use it with Vista's partition it won't make it start (the main problem).

---

### Post by darkod on 2010-06-13
> **epz said:**
> Another thing, if I use gparted to mount the NTFS partition it will say that the device drive is locked, same with the fat32 partition I made to not make vista crash (use it to transfer files lol) even if i make it with gparted it wont mount because it's locked. I had to use ntfsconfig to mount that but if i use it with Vista's partition it won't make it start (the main problem).

Can you boot vista at all? Without trying to mount it in ubuntu or anything?

Maybe it would be good to run chkdsk on the vista partition. Could it be that the filesystem is corrupted in a way? So mounting it is making it even more messed up.

You could also do basic ntfs fix from ubuntu, but the main thing is to run windows tool chkdsk. Usually it would create a setup to start chkdsk the next time you try to boot windows.

Try booting ubuntu, don't mount the vista partition, unmount it if it's mounted, and try to execute:

sudo ntfsfix /dev/sda2

After it's finished restart and select vista from the boot menu. Hopefully it will trigger a windows chkdsk, it should do that.

PS. If it says there is no ntfsfix you might need to install ntfsprogs:

sudo apt-get install ntfsprogs

---

### Post by epz on 2010-06-13
Sorry I don't get what you meant.

If i don't touch Vista's partition it boots, at the moment i wiped again the hard disk (lol either it works or i'll break it mwahaha)
and if I don't mount vista (but i can mount the support partition to move files) it will load without any error.

OFF TOPIC

next pain is: finding drivers -.- it pretends to find them on internet without being connected lololol. <-- this is a problem I can solve on my own once the main is fixed =P just some gossip lol

---

### Post by darkod on 2010-06-13
OK, so did you reinstall now or what?

If you didn't, if you still have the same vista, boot it and run:

chkdsk c: /f /r

---

### Post by epz on 2010-06-13
zomg, all was fine I installed vista SP2 (from dvd) and bam, dead again lol.

do i have to run both command? (first the one you suggested earlier and then the last)

---

### Post by darkod on 2010-06-13
> **epz said:**
> zomg, all was fine I installed vista SP2 (from dvd) and bam, dead again lol.

do i have to run both command? (first the one you suggested earlier and then the last)

No, if you reinstalled I don't see much point in running them.

So the new install of vista is getting corrupted again if tried to be mounted right?

I have no ideas right now. :(

---

### Post by epz on 2010-06-13
trying vista disk (i don't know how to translate in english lol system repair? , not a recover from backup a check for errors) it said I installed drivers which might not work O_O (sp2 is a driver now?)

---

