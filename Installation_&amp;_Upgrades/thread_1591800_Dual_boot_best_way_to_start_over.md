---
title: "Dual boot: best way to start over?"
date: 2010-10-09
forum: Installation &amp; Upgrades
---

### Post by spankler on 2010-10-09
Hi, I've got an older Dell Optiplex GX270 Pentium 4 2.6 GiHz w/ ubuntu 10.04 installed. I need to get it to a dual boot system w/ Windows XP. From what I've understood through these forums, it is way easier to have XP first, and then install 10.04. Is that a safe assumption? If so, what is the best way to reformat the HD? I am brand new to linux  and am looking forward to trying it, but I need some Windows apps for work. Please help!

---

### Post by techdude3177 on 2010-10-09
Remembering when I daul booted, I always ended up staying within the windows partition because I was lazy to log out of windows and log back into whatever linux distro.  Mainly because all the games I liked to play were only on windows until I found urban terror.
Anyways, if you already have ubuntu 10.04 already installed, I would be inclined to suggest installing a Virtual Machine of windows. Look into installing VirtualBox and installing windows on a VM there.  This will allow you to use linux on a day to day basis and still allow you to fire up windows whenever needed when you need that native software from windows.  Just keep in mind that you will be using virtual hardware and if you need to use that hardware as such like gaming. I would recommend partition your hard drive once of windows and once of whatever your favorite linux distro is.  Indeed install windows first and then install linux afterwords, grub will automatically find the windows boot partition and you should be all set!

---

### Post by lbrty on 2010-10-09
Welcome!

Yes, it is easier to install Ubuntu after Windows, however if you would like to review a tutorial that will show you how to install Windows after Ubuntu, click the link below.

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

What type of formatting are you looking to do? If you want to do a secure wipe where the files are not recoverable, then DBAN is for you. However I think in your case, you can just wipe the hard drive with the Windows OS (if you choose to start fresh and install Windows then Ubuntu). If you go the route above (install Windows after Ubuntu), you do not have to format anything just create a partition (which automatically formats that space to NTFS if you are installing Windows after Ubuntu).

[http://www.dban.org/](http://www.dban.org/)

Either way, backup all data to a SEPARATE drive(s)/CD(s)/USB flash drive(s)/etc before doing anything!

---
EDIT
As *techdude3177* stated, a virtual machine is a great option also depending on your preferences and what you are going to use Windows for (performance wise).

---

### Post by presence1960 on 2010-10-09
you do not have to get rid of a perfectly good linux installation to add windows. You want to shrink the linux partition to create space for windows using the ubuntu live cd or a gparted live cd. Then you can create an NTFS primary partition (not logical!!!). which to install windows onto. After the install reboot to make sure windows boots properly. If it does all you need to do is install GRUB back onto the MBR which BTW was overwritten with the windows boot loader. Then you will be good to go.

If you need specific instructions on all that just ask.

It would be more helpful if I could see exactly what you have on your machine, as there are many variables that may or may not be on your machine. Do this please:

Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

 This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by DanPerecky on 2010-10-09
specs from Dell:
> HDD Capacity . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .40GB 5400RPM, 40 & 80GB 7200RPM Parallel ATA, and 120GB 7200RPM Serial ATAIf you have the HD room, on your pc I would install Windows twice... once in a regular Dual Boot configuration, and also as a guest in a virtual machine. That way, if you need windoze in a pinch whilst running the great Ubuntu OS \\:D/, there you have it. 

I think it is legal as well. The windows EUL states a constriction being _one PC_. I think this is compliant with that (haven't checked lately)... If not ([-X??) then someone please correct this.

---

### Post by andrewthomas on 2010-10-09
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by spankler on 2010-10-10
Good God, a huge thank you to everyone.

 Techdude, I really like the idea of a VM. the only thing is I'm currently running XP thru Parallels on an iMac and it's slower than s**t. Do you think it would be better for me to do the more "complicated" method using partitions? (I just turned 50 and am trying desperately to catch up w/ my 11 y.o.)

Lrbty, I tried inst xp over ubuntu, after changing boot order in the BIOS, and it wouldn't do anything. I know the disk is good as it's the same one I used for the Parallels inst. So, I can't wipe it with the Windows OS.

As far as backing up data, I have absolutely none, it's a fresh install as of 10/7. Which means I have roughly 48 hrs total exp. w/ linux! (and I slept a lot)

Presence1960, here is the results.txt info:

```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   153,313,279   153,311,232  83 Linux
/dev/sda2         153,315,326   156,248,063     2,932,738   5 Extended
/dev/sda5         153,315,328   156,248,063     2,932,736  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        cbf70621-3d56-4b70-a217-32483981cdd7   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        1d6e8153-c8d1-40cd-b8c9-ec92e0387774   swap                                     
/dev/sda: PTTYPE="dos" 

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
search --no-floppy --fs-uuid --set cbf70621-3d56-4b70-a217-32483981cdd7
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
search --no-floppy --fs-uuid --set cbf70621-3d56-4b70-a217-32483981cdd7
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set cbf70621-3d56-4b70-a217-32483981cdd7
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=cbf70621-3d56-4b70-a217-32483981cdd7 ro   splash quiet
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set cbf70621-3d56-4b70-a217-32483981cdd7
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=cbf70621-3d56-4b70-a217-32483981cdd7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set cbf70621-3d56-4b70-a217-32483981cdd7
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=cbf70621-3d56-4b70-a217-32483981cdd7 ro   splash quiet
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set cbf70621-3d56-4b70-a217-32483981cdd7
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=cbf70621-3d56-4b70-a217-32483981cdd7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set cbf70621-3d56-4b70-a217-32483981cdd7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set cbf70621-3d56-4b70-a217-32483981cdd7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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
UUID=cbf70621-3d56-4b70-a217-32483981cdd7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1d6e8153-c8d1-40cd-b8c9-ec92e0387774 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  36.6GB: boot/grub/core.img
  49.5GB: boot/grub/grub.cfg
  36.7GB: boot/initrd.img-2.6.32-24-generic
  36.7GB: boot/initrd.img-2.6.32-25-generic
  36.6GB: boot/vmlinuz-2.6.32-24-generic
  36.6GB: boot/vmlinuz-2.6.32-25-generic
  36.7GB: initrd.img
  36.7GB: initrd.img.old
  36.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  8d 20 e4 86 78 74 c6 8e  87 54 0c 9d 75 e2 98 10  |. ..xt...T..u...|
00000010  62 29 01 f0 bf 2d 96 17  50 84 30 1d 21 f4 cd a7  |b)...-..P.0.!...|
00000020  ca 28 e8 15 41 c9 b0 29  20 ed 9e 3f f3 b1 68 9f  |.(..A..) ..?..h.|
00000030  0e f9 e2 e7 9c c2 e3 68  76 80 12 f9 d1 81 0b 01  |.......hv.......|
00000040  9d c3 ea 11 b3 fa 01 ef  4b c2 bf d7 a5 4f 48 fb  |........K....OH.|
00000050  e2 9a ea 86 a3 47 1d 90  66 00 db 8c e6 37 f8 21  |.....G..f....7.!|
00000060  b2 23 6d 47 ff 30 e7 d0  ca 00 b6 7e 6b bc 83 39  |.#mG.0.....~k..9|
00000070  c2 8a 96 4a 98 75 93 23  aa ef 98 c2 02 36 ac 4b  |...J.u.#.....6.K|
00000080  44 5f 11 69 31 07 93 7c  50 ce 57 ef 81 fa de 18  |D_.i1..|P.W.....|
00000090  de 52 3f 69 d0 90 ad dd  60 7d 3e 89 9a d1 5b 82  |.R?i....`}>...[.|
000000a0  53 c1 e0 9f 14 66 44 e1  c1 1d cd 1d 8a c5 90 bb  |S....fD.........|
000000b0  b2 86 a4 15 71 f2 bf 5e  92 e2 21 b9 4d 13 ed b1  |....q..^..!.M...|
000000c0  b9 13 ec 86 ee c3 c2 2a  0f 95 b1 f4 5d a4 e2 82  |.......*....]...|
000000d0  c6 28 a3 03 9e a9 ee 4b  78 e6 66 64 23 57 64 c0  |.(.....Kx.fd#Wd.|
000000e0  f6 fb 74 ae 50 76 9e 18  e2 a5 84 26 6f 77 9a 07  |..t.Pv.....&ow..|
000000f0  17 7c 98 94 0c 63 b1 34  86 6c eb 25 bf 82 c6 de  |.|...c.4.l.%....|
00000100  5b b0 05 79 ba da ec da  81 eb 3e f0 97 6e ce c9  |[..y......>..n..|
00000110  a7 98 fb 27 c0 ec 4c be  70 f9 48 74 d1 ce dd 5f  |...'..L.p.Ht..._|
00000120  ad ba 2e c9 9f 1f f5 0b  04 d5 c7 a0 09 a5 3f 56  |..............?V|
00000130  c2 99 4e 14 f1 8e e4 7f  a3 80 1f 31 cc df 50 3c  |..N........1..P<|
00000140  49 0e 54 95 a8 2d b6 48  5d 5d 57 18 8b f9 3d a6  |I.T..-.H]]W...=.|
00000150  df bb 35 70 6c eb eb 03  2b 77 7f 58 2d e8 15 b0  |..5pl...+w.X-...|
00000160  24 15 2c 00 73 d6 e2 16  86 19 6c f1 9b d9 3d f9  |$.,.s.....l...=.|
00000170  f5 68 f2 ab d9 7e 63 d4  fc 70 0e 44 27 b1 58 3c  |.h...~c..p.D'.X<|
00000180  3e 90 86 08 11 39 f3 24  75 8f 4f 3f 1c 39 4b 4f  |>....9.$u.O?.9KO|
00000190  7c 6b 30 56 34 af cb 11  f8 c3 bc 3c cb a3 95 8d  ||k0V4......<....|
000001a0  60 fa 67 5f 4d 7b 6a cf  ed 9b 62 a9 04 39 0c db  |`.g_M{j...b..9..|
000001b0  bd 82 72 dc 50 17 1f 99  8c 4e 8e 75 24 8e 00 fe  |..r.P....N.u$...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 c0 2c 00 00 00  |............,...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

Thanks to everyone! I know these kinds of ?'s are a pain in the ***, but I really looked and couldn't find anything that was working for me. Don

---

### Post by techdude3177 on 2010-10-10
So your running parallels? I never used it personally. But if you run the OS right off the native hardware that is less overhead which can be better performance.

---

### Post by presence1960 on 2010-10-10
> **spankler said:**
> Good God, a huge thank you to everyone.

 Techdude, I really like the idea of a VM. the only thing is I'm currently running XP thru Parallels on an iMac and it's slower than s**t. Do you think it would be better for me to do the more "complicated" method using partitions? (I just turned 50 and am trying desperately to catch up w/ my 11 y.o.)

Lrbty, I tried inst xp over ubuntu, after changing boot order in the BIOS, and it wouldn't do anything. I know the disk is good as it's the same one I used for the Parallels inst. So, I can't wipe it with the Windows OS.

As far as backing up data, I have absolutely none, it's a fresh install as of 10/7. Which means I have roughly 48 hrs total exp. w/ linux! (and I slept a lot)

Presence1960, here is the results.txt info:

```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   153,313,279   153,311,232  83 Linux
/dev/sda2         153,315,326   156,248,063     2,932,738   5 Extended
/dev/sda5         153,315,328   156,248,063     2,932,736  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        cbf70621-3d56-4b70-a217-32483981cdd7   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        1d6e8153-c8d1-40cd-b8c9-ec92e0387774   swap                                     
/dev/sda: PTTYPE="dos" 

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
search --no-floppy --fs-uuid --set cbf70621-3d56-4b70-a217-32483981cdd7
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
search --no-floppy --fs-uuid --set cbf70621-3d56-4b70-a217-32483981cdd7
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set cbf70621-3d56-4b70-a217-32483981cdd7
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=cbf70621-3d56-4b70-a217-32483981cdd7 ro   splash quiet
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set cbf70621-3d56-4b70-a217-32483981cdd7
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=cbf70621-3d56-4b70-a217-32483981cdd7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set cbf70621-3d56-4b70-a217-32483981cdd7
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=cbf70621-3d56-4b70-a217-32483981cdd7 ro   splash quiet
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set cbf70621-3d56-4b70-a217-32483981cdd7
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=cbf70621-3d56-4b70-a217-32483981cdd7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set cbf70621-3d56-4b70-a217-32483981cdd7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set cbf70621-3d56-4b70-a217-32483981cdd7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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
UUID=cbf70621-3d56-4b70-a217-32483981cdd7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1d6e8153-c8d1-40cd-b8c9-ec92e0387774 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  36.6GB: boot/grub/core.img
  49.5GB: boot/grub/grub.cfg
  36.7GB: boot/initrd.img-2.6.32-24-generic
  36.7GB: boot/initrd.img-2.6.32-25-generic
  36.6GB: boot/vmlinuz-2.6.32-24-generic
  36.6GB: boot/vmlinuz-2.6.32-25-generic
  36.7GB: initrd.img
  36.7GB: initrd.img.old
  36.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  8d 20 e4 86 78 74 c6 8e  87 54 0c 9d 75 e2 98 10  |. ..xt...T..u...|
00000010  62 29 01 f0 bf 2d 96 17  50 84 30 1d 21 f4 cd a7  |b)...-..P.0.!...|
00000020  ca 28 e8 15 41 c9 b0 29  20 ed 9e 3f f3 b1 68 9f  |.(..A..) ..?..h.|
00000030  0e f9 e2 e7 9c c2 e3 68  76 80 12 f9 d1 81 0b 01  |.......hv.......|
00000040  9d c3 ea 11 b3 fa 01 ef  4b c2 bf d7 a5 4f 48 fb  |........K....OH.|
00000050  e2 9a ea 86 a3 47 1d 90  66 00 db 8c e6 37 f8 21  |.....G..f....7.!|
00000060  b2 23 6d 47 ff 30 e7 d0  ca 00 b6 7e 6b bc 83 39  |.#mG.0.....~k..9|
00000070  c2 8a 96 4a 98 75 93 23  aa ef 98 c2 02 36 ac 4b  |...J.u.#.....6.K|
00000080  44 5f 11 69 31 07 93 7c  50 ce 57 ef 81 fa de 18  |D_.i1..|P.W.....|
00000090  de 52 3f 69 d0 90 ad dd  60 7d 3e 89 9a d1 5b 82  |.R?i....`}>...[.|
000000a0  53 c1 e0 9f 14 66 44 e1  c1 1d cd 1d 8a c5 90 bb  |S....fD.........|
000000b0  b2 86 a4 15 71 f2 bf 5e  92 e2 21 b9 4d 13 ed b1  |....q..^..!.M...|
000000c0  b9 13 ec 86 ee c3 c2 2a  0f 95 b1 f4 5d a4 e2 82  |.......*....]...|
000000d0  c6 28 a3 03 9e a9 ee 4b  78 e6 66 64 23 57 64 c0  |.(.....Kx.fd#Wd.|
000000e0  f6 fb 74 ae 50 76 9e 18  e2 a5 84 26 6f 77 9a 07  |..t.Pv.....&ow..|
000000f0  17 7c 98 94 0c 63 b1 34  86 6c eb 25 bf 82 c6 de  |.|...c.4.l.%....|
00000100  5b b0 05 79 ba da ec da  81 eb 3e f0 97 6e ce c9  |[..y......>..n..|
00000110  a7 98 fb 27 c0 ec 4c be  70 f9 48 74 d1 ce dd 5f  |...'..L.p.Ht..._|
00000120  ad ba 2e c9 9f 1f f5 0b  04 d5 c7 a0 09 a5 3f 56  |..............?V|
00000130  c2 99 4e 14 f1 8e e4 7f  a3 80 1f 31 cc df 50 3c  |..N........1..P<|
00000140  49 0e 54 95 a8 2d b6 48  5d 5d 57 18 8b f9 3d a6  |I.T..-.H]]W...=.|
00000150  df bb 35 70 6c eb eb 03  2b 77 7f 58 2d e8 15 b0  |..5pl...+w.X-...|
00000160  24 15 2c 00 73 d6 e2 16  86 19 6c f1 9b d9 3d f9  |$.,.s.....l...=.|
00000170  f5 68 f2 ab d9 7e 63 d4  fc 70 0e 44 27 b1 58 3c  |.h...~c..p.D'.X<|
00000180  3e 90 86 08 11 39 f3 24  75 8f 4f 3f 1c 39 4b 4f  |>....9.$u.O?.9KO|
00000190  7c 6b 30 56 34 af cb 11  f8 c3 bc 3c cb a3 95 8d  ||k0V4......<....|
000001a0  60 fa 67 5f 4d 7b 6a cf  ed 9b 62 a9 04 39 0c db  |`.g_M{j...b..9..|
000001b0  bd 82 72 dc 50 17 1f 99  8c 4e 8e 75 24 8e 00 fe  |..r.P....N.u$...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 c0 2c 00 00 00  |............,...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

Thanks to everyone! I know these kinds of ?'s are a pain in the ***, but I really looked and couldn't find anything that was working for me. Don

Your boot info script results show that you can shrink the linux partition (sda1) to create space for a windows partition. You can then use that space to install windows either by :
1. Leaving the space as unallocated and booting from the windows install media and installing to the unallocated space. or

2. Creating a primary NTFS partition from the unallocated space and then booting the windows install media and installing windows to that primary NTFS partition.

After the installation is complete reboot and make sure windows boots properly. If it does you can then install GRUB back onto the MBR. You will have a working dual boot setup.

A lot of people will tell you it is easier to install windows first, but that is because they do not understand what happens when you install windows after linux. All that happens is that Windows overwrites GRUB on the MBR with the windows boot loader. The fix takes a whopping 30 seconds to restore GRUB back to the MBR. You do not have to wipe a perfectly good linux install, then install windows (which is a pain) and then only have to reinstall your linux again which by the way was perfectly fine before it was removed. I don't see how having to reinstall 2 OSs is easier than having to only install windows. Ignorance will find many justifications for it's belief.

Again if you need specific help with this post back.

---

### Post by Hardparty on 2010-10-13
Kudos to keeping up with the times Spankler. 50 and learning Linux is amazing. Good for you.

I would love some help with my issue. I did the same steps and got this:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
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

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *     30,801,920   141,338,991   110,537,072   7 HPFS/NTFS
/dev/sda3         141,340,670   488,396,799   347,056,130   5 Extended
/dev/sda5         141,340,672   474,230,783   332,890,112  83 Linux
/dev/sda6         474,232,832   488,396,799    14,163,968  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8015 MB, 8015282176 bytes
32 heads, 63 sectors/track, 7765 cylinders, total 15654848 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    15,654,239    15,654,177   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3030-3030                              vfat       DellUtility                   
/dev/sda2        981E11881E116114                       ntfs       OS                            
/dev/sda3: PTTYPE="dos" 
/dev/sda5        b83e6f9a-fd42-492d-beae-175c8ea445db   ext4                                     
/dev/sda6        f9454b8d-f9c9-4f19-9f93-f7eb88b268a0   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        7432-FC17                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set b83e6f9a-fd42-492d-beae-175c8ea445db
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set b83e6f9a-fd42-492d-beae-175c8ea445db
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b83e6f9a-fd42-492d-beae-175c8ea445db
    linux    /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=b83e6f9a-fd42-492d-beae-175c8ea445db ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b83e6f9a-fd42-492d-beae-175c8ea445db
    echo    'Loading Linux 2.6.35-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-22-generic-pae root=UUID=b83e6f9a-fd42-492d-beae-175c8ea445db ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b83e6f9a-fd42-492d-beae-175c8ea445db
    linux    /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=b83e6f9a-fd42-492d-beae-175c8ea445db ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b83e6f9a-fd42-492d-beae-175c8ea445db
    echo    'Loading Linux 2.6.32-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=b83e6f9a-fd42-492d-beae-175c8ea445db ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b83e6f9a-fd42-492d-beae-175c8ea445db
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set b83e6f9a-fd42-492d-beae-175c8ea445db
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 981e11881e116114
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=b83e6f9a-fd42-492d-beae-175c8ea445db /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=f9454b8d-f9c9-4f19-9f93-f7eb88b268a0 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 162.7GB: boot/grub/core.img
 154.8GB: boot/grub/grub.cfg
 146.4GB: boot/initrd.img-2.6.32-25-generic-pae
 146.5GB: boot/initrd.img-2.6.35-22-generic-pae
 163.1GB: boot/vmlinuz-2.6.32-25-generic-pae
 163.5GB: boot/vmlinuz-2.6.35-22-generic-pae
 146.5GB: initrd.img
 146.4GB: initrd.img.old
 163.5GB: vmlinuz
 163.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  00 00 00 0f b7 84 04 b4  00 00 00 89 44 24 24 89  |............D$$.|
00000010  54 24 20 8d 44 24 35 eb  07 8d a4 24 00 00 00 00  |T$ .D$5....$....|
00000020  0f b6 70 01 0f b6 38 0f  b6 68 ff 8b d1 2b d6 8b  |..p...8..h...+..|
00000030  74 24 20 2b f7 8b 7c 24  24 2b fd 8b ef 0f af ef  |t$ +..|$$+......|
00000040  8b fa 0f af fa 8b d6 0f  af d6 03 ef 8d 54 95 00  |.............T..|
00000050  89 94 9c a4 00 00 00 43  83 c0 03 83 fb 04 7c c0  |.......C......|.|
00000060  8b b4 24 a4 00 00 00 33  c0 ba 01 00 00 00 8b ff  |..$....3........|
00000070  8b 8c 94 a4 00 00 00 3b  f1 7e 04 8b f1 8b c2 42  |.......;.~.....B|
00000080  83 fa 04 7c eb 8b 54 24  2c 8b 74 24 10 8b ca 83  |...|..T$,.t$....|
00000090  e0 03 d3 e0 8b 4c 24 28  41 83 c2 02 09 44 24 1c  |.....L$(A....D$.|
000000a0  83 f9 04 89 4c 24 28 89  54 24 2c 0f 8c 37 ff ff  |....L$(.T$,..7..|
000000b0  ff 8b 44 24 30 66 8b 4c  24 1c 46 83 fe 04 66 89  |..D$0f.L$.F...f.|
000000c0  08 89 74 24 10 0f 8c e9  fe ff ff 0f b7 54 24 4c  |..t$.........T$L|
000000d0  8b 84 24 44 05 00 00 0f  b7 4c 24 4e 8b 5c 24 54  |..$D.....L$N.\$T|
000000e0  8b ac 24 3c 05 00 00 66  89 10 0f b7 54 24 50 83  |..$<...f....T$P.|
000000f0  c0 02 66 89 08 0f b7 4c  24 52 83 c0 02 66 89 10  |..f....L$R...f..|
00000100  83 c0 02 66 89 08 8b 4c  24 5c 83 c3 04 83 c0 02  |...f...L$\......|
00000110  3b dd 89 84 24 44 05 00  00 89 5c 24 54 0f 8c ed  |;...$D....\$T...|
00000120  f7 ff ff 8b 54 24 40 83  c2 04 3b 94 24 40 05 00  |....T$@...;.$@..|
00000130  00 89 54 24 40 0f 8c 85  f7 ff ff 8b 44 24 60 85  |..T$@.......D$`.|
00000140  c0 74 0e 83 f8 01 74 09  50 e8 43 e8 34 00 83 c4  |.t....t.P.C.4...|
00000150  04 5b 5f 5e 5d 81 c4 24  05 00 00 c3 cc cc cc cc  |.[_^]..$........|
00000160  81 ec 20 05 00 00 53 8b  9c 24 2c 05 00 00 56 8b  |.. ...S..$,...V.|
00000170  b4 24 34 05 00 00 57 33  ff 89 7c 24 5c 3b df 0f  |.$4...W3..|$\;..|
00000180  84 4b 09 00 00 3b f7 0f  84 43 09 00 00 8b c3 99  |.K...;...C......|
00000190  83 e2 03 03 c2 c1 f8 02  55 85 c0 74 1f 8b c6 99  |........U..t....|
000001a0  83 e2 03 03 c2 c1 f8 02  85 c0 74 10 8b ac 24 34  |..........t...$4|
000001b0  05 00 00 89 6c 24 5c e9  d6 00 00 00 83 fb 00 fe  |....l$\.........|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 80 d7 13 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 80  d7 13 00 28 d8 00 00 00  |...........(....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```I bought my Dell Inspiron with Windows 7 installed. When I opened it I shrunk the windows partition and added Ubuntu 10.04. I am not sure how I managed it but my laptop doesn't load Grub all the time. I have had to make a USB Liveboot "CD" and an actual LiveCD. I am fed up and would love to start over. All I want is my Ubuntu on one half, and the other smaller partition for windows 7.

Any help would be greatly appreciated!
Thanks

Tanner

---

### Post by spankler on 2010-10-14
OK, everybody, first, thanks for all the help/tips/advice. It is much appreciated! For God knows what reason, my system wouldn't let me do anything as "root"--the ingrateful little traitor--so I did end up wiping the install, partitioning the disk, and upgrading to ubuntu 10.10. So far so god. Now, I guess what I should do is format the new partition to NTFS. I am including screenshots, b/c although it may be obvious to those who know what they're doing, it's not to me, and I'm afraid of reformatting the part I finally have working perfectly. Soo... in disk utility, I get this:

[IMG]http://i902.photobucket.com/albums/ac230/spankler/1.png[/IMG]

Then, after choosing the unformatted partition, I get this next screen. Please tell me (simply[-o<) what to do. My attempts thus far--not implemented as I was afraid of formatting the wrong thing) Also, what do people think is the best book out there to learn 10.10, assuming (correctly) that I am starting form a zero-knowledge base. Thanks again to all you folks, you've been really helpful! I'm doing my best to not post here unless I can't find understandable answers (to me) elsewhere in these fora. Don.

[IMG]http://i902.photobucket.com/albums/ac230/spankler/2.png[/IMG]

---

### Post by spankler on 2010-10-17
Please help! Pretty please? I sincerely do not want to screw this up and start over (again).

---

### Post by spankler on 2010-10-18
Why, after a successful (I thought) dual boot installation w/ a side-by-side lynx and meerkat install and XP does my system refuse to boot? It just gets to the Dell screen, giving boot options (none of which are making any difference) and keeps looping it. Last night, after re-installing the grub (lost after the XP install) everything was working fine. I powered down and this morning tried to restart and...this. I really don't want to have to reinstall everything and reconfigure and reinstall apps--what can I do? And more importantly, WTF did this happen to begin with? Please help!

](*,)Stop me before I install again...

---

### Post by KositaQ on 2010-10-20
Hi, I am a newbie, and I want to do just that. I presently have Ubuntu 10.10 and I love it, but unfortunately I have this Windows app that cannot even be run in Wine and my only choice is to do a dual boot windows install..Is there a step by step instructional link out there that you might know I can use to have Win XP installed after my wonderful Linux? I have tried almost everything and after I reboot I always get Linux again. Tks for your help ;)

---

