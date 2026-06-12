---
title: "Cant Log In to Xubuntu 11.10"
date: 2011-12-05
forum: Installation &amp; Upgrades
---

### Post by roofusthedoofus1 on 2011-12-05
Helo there everyone,

Hope this is in the right place,

After what i think may have been a dodgy shutdown I can't log in.  When i click login after entering the username and password it bounces back to the login screen.  

I've searched the interwebs for solutions to this problem and the most successful one seems to be deleting the Xauthority file.  Unfortunately this doesnt work for me, nothing changes.  

I can log no problem using the terminal after pressing Ctrl-Alt-F1 and can see all my files there, there's no problem with the file system it seems.

I've been able to add a new user through logging in as guest, though it is very restricted despite being able to change the new user to administrator.

Really at a loss as to what to do next.  I'm new to ubuntu but not to computers, so not that great with messing around in a terminal.  My computer is a Dell Inspiron 6000 if thats anything relevant....

Thanks in advance for your help...

---

### Post by BC59 on 2011-12-05
Run the Boot Info Script: 
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Instructions are [here]("http://bootinfoscript.sourceforge.net/")

Then post the results.txt

---

### Post by roofusthedoofus1 on 2011-12-05
Here's result.txt...


```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda6: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   308,424,703   308,422,656  83 Linux
/dev/sda2         308,426,750   312,580,095     4,153,346   5 Extended
/dev/sda5         310,503,424   312,580,095     2,076,672  82 Linux swap / Solaris
/dev/sda6         308,426,752   310,503,423     2,076,672  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________
Note: sector size is 1024 (not 512)

Disk /dev/sdb: 3986 MB, 3986644992 bytes
255 heads, 63 sectors/track, 242 cylinders, total 3893208 sectors
Units = sectors of 1 * 1024 = 1024 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63     3,893,147     3,893,085   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/cryptswap1 4a3f03d3-b9d7-4a5a-815d-e0f99d6676ef   swap       
/dev/sda1        fddf3be9-6900-47f1-a9c7-93fe434265bd   ext4       
/dev/sdb1        9836-7528                              vfat       

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
cryptswap1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /media/9836-7528         vfat       (rw,nosuid,nodev,uid=1002,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)


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
search --no-floppy --fs-uuid --set=root fddf3be9-6900-47f1-a9c7-93fe434265bd
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos1)'
  search --no-floppy --fs-uuid --set=root fddf3be9-6900-47f1-a9c7-93fe434265bd
  set locale_dir=($root)/boot/grub/locale
  set lang=en_IE
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
menuentry 'Ubuntu, with Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root fddf3be9-6900-47f1-a9c7-93fe434265bd
	linux	/boot/vmlinuz-3.0.0-13-generic root=UUID=fddf3be9-6900-47f1-a9c7-93fe434265bd ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root fddf3be9-6900-47f1-a9c7-93fe434265bd
	echo	'Loading Linux 3.0.0-13-generic ...'
	linux	/boot/vmlinuz-3.0.0-13-generic root=UUID=fddf3be9-6900-47f1-a9c7-93fe434265bd ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-13-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root fddf3be9-6900-47f1-a9c7-93fe434265bd
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=fddf3be9-6900-47f1-a9c7-93fe434265bd ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root fddf3be9-6900-47f1-a9c7-93fe434265bd
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=fddf3be9-6900-47f1-a9c7-93fe434265bd ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root fddf3be9-6900-47f1-a9c7-93fe434265bd
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=fddf3be9-6900-47f1-a9c7-93fe434265bd ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-11-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-11-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root fddf3be9-6900-47f1-a9c7-93fe434265bd
	echo	'Loading Linux 2.6.38-11-generic ...'
	linux	/boot/vmlinuz-2.6.38-11-generic root=UUID=fddf3be9-6900-47f1-a9c7-93fe434265bd ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-11-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root fddf3be9-6900-47f1-a9c7-93fe434265bd
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root fddf3be9-6900-47f1-a9c7-93fe434265bd
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=fddf3be9-6900-47f1-a9c7-93fe434265bd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
#UUID=4ffd61c7-57b1-47d6-92f0-b2b23c640410 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.38-11-generic              2
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/initrd.img-3.0.0-13-generic               3
               =                boot/vmlinuz-2.6.38-11-generic                 2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-13-generic                  1
               =                initrd.img                                     3
               =                initrd.img.old                                 2
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sdb1

00000000  eb 58 90 4d 53 44 4f 53  35 2e 30 00 04 08 2a 01  |.X.MSDOS5.0...*.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  5d 67 3b 00 6b 07 00 00  00 00 00 00 02 00 00 00  |]g;.k...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 28 75 36 98 4e  4f 20 4e 41 4d 45 20 20  |..)(u6.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 33 c9 8e d1 bc f4  |  FAT32   3.....|
00000060  7b 8e c1 8e d9 bd 00 7c  88 4e 02 8a 56 40 b4 41  |{......|.N..V@.A|
00000070  bb aa 55 cd 13 72 10 81  fb 55 aa 75 0a f6 c1 01  |..U..r...U.u....|
00000080  74 05 fe 46 02 eb 2d 8a  56 40 b4 08 cd 13 73 05  |t..F..-.V@....s.|
00000090  b9 ff ff 8a f1 66 0f b6  c6 40 66 0f b6 d1 80 e2  |.....f...@f.....|
000000a0  3f f7 e2 86 cd c0 ed 06  41 66 0f b7 c9 66 f7 e1  |?.......Af...f..|
000000b0  66 89 46 f8 83 7e 16 00  75 38 83 7e 2a 00 77 32  |f.F..~..u8.~*.w2|
000000c0  66 8b 46 1c 66 83 c0 0c  bb 00 80 b9 01 00 e8 2b  |f.F.f..........+|
000000d0  00 e9 2c 03 a0 fa 7d b4  7d 8b f0 ac 84 c0 74 17  |..,...}.}.....t.|
000000e0  3c ff 74 09 b4 0e bb 07  00 cd 10 eb ee a0 fb 7d  |<.t............}|
000000f0  eb e5 a0 f9 7d eb e0 98  cd 16 cd 19 66 60 80 7e  |....}.......f`.~|
00000100  02 00 0f 84 20 00 66 6a  00 66 50 06 53 66 68 10  |.... .fj.fP.Sfh.|
00000110  00 01 00 b4 42 8a 56 40  8b f4 cd 13 66 58 66 58  |....B.V@....fXfX|
00000120  66 58 66 58 eb 33 66 3b  46 f8 72 03 f9 eb 2a 66  |fXfX.3f;F.r...*f|
00000130  33 d2 66 0f b7 4e 18 66  f7 f1 fe c2 8a ca 66 8b  |3.f..N.f......f.|
00000140  d0 66 c1 ea 10 f7 76 1a  86 d6 8a 56 40 8a e8 c0  |.f....v....V@...|
00000150  e4 06 0a cc b8 01 02 cd  13 66 61 0f 82 75 ff 81  |.........fa..u..|
00000160  c3 00 02 66 40 49 75 94  c3 42 4f 4f 54 4d 47 52  |...f@Iu..BOOTMGR|
00000170  20 20 20 20 00 00 00 00  00 00 00 00 00 00 00 00  |    ............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 0d 0a 52 65  |..............Re|
000001b0  6d 6f 76 65 20 64 69 73  6b 73 20 6f 72 20 6f 74  |move disks or ot|
000001c0  68 65 72 20 6d 65 64 69  61 2e ff 0d 0a 44 69 73  |her media....Dis|
000001d0  6b 20 65 72 72 6f 72 ff  0d 0a 50 72 65 73 73 20  |k error...Press |
000001e0  61 6e 79 20 6b 65 79 20  74 6f 20 72 65 73 74 61  |any key to resta|
000001f0  72 74 0d 0a 00 00 00 00  00 ac cb d8 00 00 55 aa  |rt............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in


```

---

### Post by BC59 on 2011-12-05
You have to boot from a live Ubuntu 11.10 CD, then choose Try Ubuntu and go to the desktop. Open a terminal by CTRL+ALT+T.

Then mount sda1:


```
sudo mount /dev/sda1 /mnt
```
Install grub:


```
sudo grub-install --root-directory=/mnt /dev/sda
```

If you have problems, run from your Ubuntu installation:```
sudo update-grub
```

---

### Post by roofusthedoofus1 on 2011-12-05
Thanks for your help!! i'll try this when i can get a hold of a blank CD.  Is it possible to do all this from the recovery console?

---

### Post by ubume2 on 2011-12-05
If you can log in to recovery console, I think you can.

You don't need to mount.

$ sudo grub-install /dev/sda
$ sudo update-grub

Edit: :oops: That just restores grub. From recovery you need to reset password.
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by roofusthedoofus1 on 2011-12-05
Hey,

Thanks for your help also!

I restored and updated grub however when i try to reset the password it gives an 'authentication token manipulation error' and i cant seem to change the password...

any ideas?

thanks again

---

### Post by roofusthedoofus1 on 2011-12-06
ok i managed to change it but still can't log in.

any other help is v appreciated

---

### Post by BC59 on 2011-12-06
Look here there are some solutions:


[http://www.linuxquestions.org/questions/linux-security-4/authentication-token-manipulation-error-2813/](http://www.linuxquestions.org/questions/linux-security-4/authentication-token-manipulation-error-2813/)

---

### Post by Toz on 2011-12-06
> **roofusthedoofus1 said:**
> I've searched the interwebs for solutions to this problem and the most successful one seems to be deleting the Xauthority file.  Unfortunately this doesnt work for me, nothing changes.

The .ICEauthority file is also known to cause similar problems. Try deleting it and rebooting. Have a look at all of the permissions in your $HOME to make sure you are the owner:
```
ls -l ~
```

The **~/.xsession-errors** log file may yield some clues as to what is happening.

---

### Post by MAFoElffen on 2011-12-06
> **roofusthedoofus1 said:**
> Helo there everyone,

Hope this is in the right place,

After what i think may have been a dodgy shutdown I can't log in.  When i click login after entering the username and password it bounces back to the login screen.  

I've searched the interwebs for solutions to this problem and the most successful one seems to be deleting the Xauthority file.  Unfortunately this doesnt work for me, nothing changes.  

I can log no problem using the terminal after pressing Ctrl-Alt-F1 and can see all my files there, there's no problem with the file system it seems.

I've been able to add a new user through logging in as guest, though it is very restricted despite being able to change the new user to administrator.

Really at a loss as to what to do next.  I'm new to ubuntu but not to computers, so not that great with messing around in a terminal.  My computer is a Dell Inspiron 6000 if thats anything relevant....

Thanks in advance for your help...
Stop. Take a breath. Relax.

I'm sorry that you took some side trips suggested by others. The previous solutions about grub would have helped you if you were having a problem with a Grub password... But from reading your first post, you are having a more common problem when you get past the Plymouth splash, to the graphical login screen/logging into Linux from the Desktop Manager...  This is rather a problem with the ".xauthority" file. 

Here you go:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Reseting Authories Profile For Logging into X]("http://ubuntuforums.org/showpost.php?p=11404605&postcount=766")**[/SIZE][/COLOR][/SIZE][/COLOR]

---

### Post by RichBR549 on 2011-12-14
> **Toz said:**
> The .ICEauthority file is also known to cause similar problems. Try deleting it and rebooting. Have a look at all of the permissions in your $HOME to make sure you are the owner:
```
ls -l ~
```

The **~/.xsession-errors** log file may yield some clues as to what is happening.

I had this problem today after an update and this is the one solution that worked for me. permissions were OK, but the .xsession-errors file showed an error with the .ICEauthority file.   delete and reboot worked. Thanks.

---

### Post by roofusthedoofus1 on 2011-12-17
Thanks everyone for their suggestions and patience with this one, drivin me bananas so it is....

The situation is as follows now:  I still get bounced back to the login screen when i try to log in.  I think it's an ownership issue or something.  When i log in under non-graphical mode (CTRL+ALT+F1) i can only get access-your-private-data.desktop and it's readme.txt file.  contents are as follows:

```
dr-x------ 2 satan root 4096 2011-10-10 18.33 .
drwxr-xr-x 6 root root 4096 2011-11-26 13.26 ..
lrwxrwxrwx 1 satan root    56 2011-10-10 18.33 Access-Your-Private-Data.Desktop 
lrwxrwxrwx 1 satan root    31 2011-10-10 18.33 .ecryptfs
lrwxrwxrwx 1 satan root    30 2011-10-10 18.33 .Private
lrwxrwxrwx 1 satan root    52 2011-10-10 18.33 Readme.txt

```
... if this is any help.  So i seem to have locked myself out of the hard disk, nice one.  I tried using the installation CD to access it but i'm out of my depth with that one and don't want to mess it up more than i already have.  

So if you have any suggestions, i'm all ears and very thankful...

---

### Post by roofusthedoofus1 on 2011-12-17
ok, finally in!

deleted  the .ICEauthority file decrypted my private directory and i got in, thanks everyone for their help and advice it's great that there's people like you to help out

smiley face

---

