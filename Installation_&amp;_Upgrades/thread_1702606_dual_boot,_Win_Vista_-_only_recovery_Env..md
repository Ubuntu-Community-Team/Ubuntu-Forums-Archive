---
title: "dual boot, Win Vista - only recovery Env."
date: 2011-03-08
forum: Installation &amp; Upgrades
---

### Post by dcvc on 2011-03-08
Hi Everybody,
Firstlyi want to specify that i read many threads and guides before posting this, tried to follow some advice and solutions but nothing worked (but I am a beginner user, and maybe i did something wrong!)

My laptop is a Lenovo SL410 (i bought it in China) which came with pre-installed Windows Vista.
I had many trouble with resizing the partition in order to make room for Ubuntu but i finally managed. I successfully installed Ubuntu 10.04 and everything works fine.

My problem is that Grub shows
"Windows Recovery Environment (loader) (on /dev/sda1)" instead of normal Windows Vista (which is on /dev/sda2)

If i choose Windows Recovery Env. i can load Vista but is not stable, keeps crashing, or giving me warning about low memory :confused:

Can anybody help me? 
 
thanks

---

### Post by Dutch70 on 2011-03-08
> **dcvc said:**
> Hi Everybody,
Firstlyi want to specify that i read many threads and guides before posting this, tried to follow some advice and solutions but nothing worked (but I am a beginner user, and maybe i did something wrong!)

My laptop is a Lenovo SL410 (i bought it in China) which came with pre-installed Windows Vista.
I had many trouble with resizing the partition in order to make room for Ubuntu but i finally managed. I successfully installed Ubuntu 10.04 and everything works fine.

My problem is that Grub shows
"Windows Recovery Environment (loader) (on /dev/sda1)" instead of normal Windows Vista (which is on /dev/sda2)

If i choose Windows Recovery Env. i can load Vista but is not stable, keeps crashing, or giving me warning about low memory :confused:

Can anybody help me? 
 
thanks

Welcome to UF dcvc.

I'm not quite sure what your question is, but why  would you try to boot into the recovery partition anyway? 
Please take a screenshot of your partitions in Gparted & use the little paper clip to **attach** it to your next post. I'm not sure if I can help, but someone can.

---

### Post by neoroses on 2011-03-08
Try downloading the super grub boot disk and see if that shows your window$ v partiton. if it does and you can boot to it, you can use the disk to re-write grub with the entries it finds

peace

---

### Post by dcvc on 2011-03-08
> **Dutch70 said:**
> Welcome to UF dcvc.

I'm not quite sure what your question is, but why  would you try to boot into the recovery partition anyway? 
Please take a screenshot of your partitions in Gparted & use the little paper clip to **attach** it to your next post. I'm not sure if I can help, but someone can.

sorry. My question is how can i boot into windows normally?
I try to boot into the recovery partition because I needed to use Windows and that's the only one i can choose.
Ok i'll try to take the screenshot, please wait :)

---

### Post by dcvc on 2011-03-08
> **neoroses said:**
> Try downloading the super grub boot disk and see if that shows your window$ v partiton. if it does and you can boot to it, you can use the disk to re-write grub with the entries it finds

peace
ok thanks. This super grub boot disk does everything by itself? 'cause i'm a beginner user..

---

### Post by dcvc on 2011-03-08
ok, here is the screenshot..  i hope i did it right.

---

### Post by oldfred on 2011-03-08
Grub mis-labels Vista  and Vista recovery. If you download Grub customizer it is probably the easiest way to rename the boot entry.

HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

drs305 wrote a Grub 2 Tweaks guide but it's pretty geeky stuff. If you are interested in editing the Grub2 scripts to rename a title, see Section 7 of the "Tweaks" link 
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
Grub 2 Title Tweaks-drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

The windows boot flag is on sda1, but your main install is sda2. Is the main install where you are at, as it has lots of room. Grub will not use boot flag to know what to boot if both partitions have all the boot files needed. Otherwise it sounds like grub is getting you to windows and you have some issues with Vista. Have you run chkdsk?

---

### Post by Dutch70 on 2011-03-08
You did fine. 

First try going to a terminal & run this command.
```
sudo apt-get update && sudo apt-get upgrade
```

and then this one...
```
sudo update-grub
```


Reboot and see if there is an option in your grub menu to select windows (on sda2), use the arrow keys to navigate.

If that doesn't work, then please post the output of bootinfoscriptwith the link below. Highlight it and use the "code" tags with the # sign in the toolbar of your post.
[[COLOR="Blue"]http://bootinfoscript.sourceforge.net/[/COLOR]]("http://bootinfoscript.sourceforge.net/")

---

### Post by dcvc on 2011-03-08
thank you for your answer

oldfred, i didn't try your solution yet because i'm afraid to mess with Grub and do some serious damage.. I run chkdsk, and i also try to fix it with vista recovery cd, but it didn't work.

dutch70 i did as you said but nothing changed.
Here is the output:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.2 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048     3,567,615     3,565,568   7 HPFS/NTFS
/dev/sda2           3,567,616   751,488,569   747,920,954   7 HPFS/NTFS
/dev/sda3         956,291,072   976,771,071    20,480,000   7 HPFS/NTFS
/dev/sda4         751,489,022   956,291,071   204,802,050   5 Extended
/dev/sda5         751,489,024   947,873,791   196,384,768  83 Linux
/dev/sda6         947,875,840   956,291,071     8,415,232  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7E1C8A251C89D913                       ntfs       SERVICEV003                   
/dev/sda2        42828C09828C039F                       ntfs       SW_Preload                    
/dev/sda3        D4708F72708F5A5E                       ntfs       Lenovo                        
/dev/sda4: PTTYPE="dos" 
/dev/sda5        b8d4abe7-1dfd-408c-a729-22ca2b9bab0c   ext3                                     
/dev/sda6        30aa1e3f-25d5-4737-bc9e-9dbbe2222912   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,errors=remount-ro)


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
search --no-floppy --fs-uuid --set b8d4abe7-1dfd-408c-a729-22ca2b9bab0c
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
search --no-floppy --fs-uuid --set b8d4abe7-1dfd-408c-a729-22ca2b9bab0c
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
menuentry 'Ubuntu, with Linux 2.6.32-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b8d4abe7-1dfd-408c-a729-22ca2b9bab0c
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=b8d4abe7-1dfd-408c-a729-22ca2b9bab0c ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b8d4abe7-1dfd-408c-a729-22ca2b9bab0c
    echo    'Loading Linux 2.6.32-29-generic ...'
    linux    /boot/vmlinuz-2.6.32-29-generic root=UUID=b8d4abe7-1dfd-408c-a729-22ca2b9bab0c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-29-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b8d4abe7-1dfd-408c-a729-22ca2b9bab0c
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=b8d4abe7-1dfd-408c-a729-22ca2b9bab0c ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b8d4abe7-1dfd-408c-a729-22ca2b9bab0c
    echo    'Loading Linux 2.6.32-28-generic ...'
    linux    /boot/vmlinuz-2.6.32-28-generic root=UUID=b8d4abe7-1dfd-408c-a729-22ca2b9bab0c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b8d4abe7-1dfd-408c-a729-22ca2b9bab0c
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=b8d4abe7-1dfd-408c-a729-22ca2b9bab0c ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b8d4abe7-1dfd-408c-a729-22ca2b9bab0c
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=b8d4abe7-1dfd-408c-a729-22ca2b9bab0c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b8d4abe7-1dfd-408c-a729-22ca2b9bab0c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set b8d4abe7-1dfd-408c-a729-22ca2b9bab0c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7e1c8a251c89d913
    drivemap -s (hd0) ${root}
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
/dev/sda5       /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=30aa1e3f-25d5-4737-bc9e-9dbbe2222912 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 432.8GB: boot/grub/core.img
 432.8GB: boot/grub/grub.cfg
 432.8GB: boot/initrd.img-2.6.32-21-generic
 432.8GB: boot/initrd.img-2.6.32-28-generic
 432.9GB: boot/initrd.img-2.6.32-29-generic
 432.8GB: boot/vmlinuz-2.6.32-21-generic
 432.8GB: boot/vmlinuz-2.6.32-28-generic
 432.9GB: boot/vmlinuz-2.6.32-29-generic
 432.9GB: initrd.img
 432.8GB: initrd.img.old
 432.9GB: vmlinuz
 432.8GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  69 00 65 00 6e 00 74 00  54 00 79 00 70 00 65 00  |i.e.n.t.T.y.p.e.|
00000010  3a 00 20 00 25 00 75 00  29 00 00 00 90 90 90 90  |:. .%.u.).......|
00000020  90 8b ff 55 8b ec 56 8b  75 08 85 f6 74 2a ff 36  |...U..V.u...t*.6|
00000030  68 60 58 be 1c 68 02 00  40 00 ff 35 0c d0 be 1c  |h`X..h..@..5....|
00000040  e8 30 bb fd ff 83 c4 10  68 c9 00 00 00 68 60 83  |.0......h....h`.|
00000050  bc 1c 56 e8 14 ff ff ff  5e 5d c2 04 00 90 90 90  |..V.....^]......|
00000060  50 00 72 00 6f 00 63 00  65 00 73 00 73 00 69 00  |P.r.o.c.e.s.s.i.|
00000070  6e 00 67 00 20 00 3a 00  20 00 53 00 71 00 6d 00  |n.g. .:. .S.q.m.|
00000080  55 00 6e 00 69 00 6e 00  69 00 74 00 69 00 61 00  |U.n.i.n.i.t.i.a.|
00000090  6c 00 69 00 7a 00 65 00  53 00 71 00 6d 00 44 00  |l.i.z.e.S.q.m.D.|
000000a0  61 00 74 00 61 00 20 00  66 00 6f 00 72 00 20 00  |a.t.a. .f.o.r. .|
000000b0  63 00 6c 00 69 00 65 00  6e 00 74 00 20 00 74 00  |c.l.i.e.n.t. .t.|
000000c0  79 00 70 00 65 00 3a 00  20 00 25 00 75 00 00 00  |y.p.e.:. .%.u...|
000000d0  90 90 90 90 90 8b ff 55  8b ec 53 56 57 68 dc 59  |.......U..SVWh.Y|
000000e0  be 1c bf 02 00 40 00 57  ff 35 0c d0 be 1c e8 82  |.....@.W.5......|
000000f0  ba fd ff 8b 5d 08 83 c4  0c f6 45 0c 01 be 40 e8  |....].....E...@.|
00000100  be 1c 74 30 8b 43 04 85  c0 74 29 6a 02 6a 14 56  |..t0.C...t)j.j.V|
00000110  50 e8 8a 57 00 00 56 ff  73 04 68 78 59 be 1c 57  |P..W..V.s.hxY..W|
00000120  ff 35 0c d0 be 1c e8 4a  ba fd ff 83 c4 14 ff 05  |.5.....J........|
00000130  80 f3 be 1c f6 45 0c 02  74 30 8b 43 08 85 c0 74  |.....E..t0.C...t|
00000140  29 6a 02 6a 14 56 50 e8  54 57 00 00 56 ff 73 08  |)j.j.VP.TW..V.s.|
00000150  68 78 59 be 1c 57 ff 35  0c d0 be 1c e8 14 ba fd  |hxY..W.5........|
00000160  ff 83 c4 14 ff 05 80 f3  be 1c 5f 5e 5b 5d c2 08  |.........._^[]..|
00000170  00 90 90 90 90 90 90 90  53 00 71 00 6d 00 45 00  |........S.q.m.E.|
00000180  6e 00 64 00 43 00 6c 00  69 00 65 00 6e 00 74 00  |n.d.C.l.i.e.n.t.|
00000190  53 00 65 00 73 00 73 00  69 00 6f 00 6e 00 73 00  |S.e.s.s.i.o.n.s.|
000001a0  3a 00 20 00 45 00 6e 00  64 00 65 00 64 00 20 00  |:. .E.n.d.e.d. .|
000001b0  73 00 65 00 73 00 73 00  69 00 6f 00 6e 00 00 fe  |s.e.s.s.i.o.n...|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 98 b4 0b 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 98  b4 0b 00 70 80 00 00 00  |...........p....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by dcvc on 2011-03-11
I downloaded Grub Customizer, I tried to add and mount the win vista partition but i get this message "This seems not to be a root file system (no fstab found)" ..i just tried to click few things, i was afraid to do something wrong. 

thanks

---

### Post by Dutch70 on 2011-03-11
Sorry I can't help you with this one dcvc. I was hoping someone with more knowledge would take a look at it.

---

### Post by Quackers on 2011-03-11
The entry labelled Vista Recovery is actually the partition which holds the first 2 Windows boot files, (/dev/sda1). If that isn't booting reliably then something is wrong.
You say in your first post that you had difficulty resizing the Windows partition so as to gain space for Ubuntu to install into. This may be where the problem arose.
In Vista or Windows 7 the Windows Disk Management screen is the easiest and safest way to resize a Windows system partition. It is also highly recommended that the system be defragmented first (at least once).
Which program did you use to resize it in the end?
If you can get Windows to boot I would suggest you schedule a chkdsk to be run on the next boot. You should keep running chkdsk until no errors are reported. This may solve your problem.
Further details on scheduling chkdsk in the link below. (It actually gives details for Windows 7, but as far as I'm aware Vista is the same).

[http://www.w7forums.com/use-chkdsk-check-disk-t448.html](http://www.w7forums.com/use-chkdsk-check-disk-t448.html)

---

### Post by dcvc on 2011-03-11
thanks for your answer and help :)

I tried to resize with Vista disk management but i couldn't do anything, i read that's because of some Lenovo security thing. I did a defrag before that. I followed the instruction i found on a blog (i can't find the link right now), where they suggest to move some files (but i couldn't) and disable the system restore.

At the end i resized the partion with gparted, which i guess, caused the problem. Or maybe i did something wrong while trying to resize in Win.. :(

When i boot the recovery environment, my wireless network settings are messed up, and the mouse moves too slow even if the pointer speed is set on "fast". 

I did run chkdsk couple of times and didn't show any errors!

---

