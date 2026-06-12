---
title: "installed Ubuntu after XP, can't boot into XP"
date: 2010-09-26
forum: Installation &amp; Upgrades
---

### Post by unxzst on 2010-09-26
this isn't my first time, but it's got me stumped. I've gone through several threads' worth of suggestions, but nothing.

I can see all the windows files, boot.ini, and ntldr are present... Its just when I select XP from the Grub menu, nothing happens, just a blinking cursor, then hang.
  
I've tried restoring grub, twice. still can't boot XP. 

I tried lilo, same result (couldn't even get into a boot menu)

Screwing around with SuperGrub Disk for a while, trying auto-boot, MBR, and a few other options, with no results.

what else can I try? I don't have a Win recovery CD with me.

my next step would be to wipe everything on the HDD, and install ubuntu first. :(


some more detail, XP is in on hd(0,0) (or 0,1... not sure anymore!!) after that comes the extended partition with Linux being on hd(0,5)
i think the MBR is ok, because SuperGrub, grub, and ubuntu told me so...
what could it be??

---

### Post by Mark Phelps on 2010-09-27
Wiping the drive and installing Ubuntu first is going to do nothing to solve your XP problem, in fact, it will only make it worse.

Open a terminal in Ubuntu and run "sudo fdisk-lu" (that's a lowercase L, not a one).  That will allow us to see your partition layout.

When did the "XP unable to boot" problems first start?  Were you able to boot into XP for a while? Or did the problems start as soon as you installed Ubuntu?

---

### Post by unxzst on 2010-09-27
> **Mark Phelps said:**
> Wiping the drive and installing Ubuntu first is going to do nothing to solve your XP problem, in fact, it will only make it worse.

Open a terminal in Ubuntu and run "sudo fdisk-lu" (that's a lowercase L, not a one).  That will allow us to see your partition layout.

When did the "XP unable to boot" problems first start?  Were you able to boot into XP for a while? Or did the problems start as soon as you installed Ubuntu?
by "wiping everything" i meant formatting the whole drive, and installing by the wiki.

i used the command "fdisk -l" and got something like
sda1-xp
sda2-extended 
sda3-something
sda4-something
sda5-linux
sda6-swap.

this is my friend's computer that i screwed up (by advocating installing ubuntu!) and I'm not at the terminal currently. I'm going to try to set up a tunnel so i can work on it remotely (i don't know what to do about resetting the box...so its just an exercise)

the problem started right after installing ubuntu from a flash drive. i think the installer resized the xp partition and it didn't like that.

---

### Post by bokeifus on 2010-09-27
I am having the same issue. I installed Ubuntu exactly as the site said to. It had to resize the xp partition because it was the only OS installed on the computer. 

Once the computer restarted, I was able to get into Ubuntu with no problems. But then when I restarted the computer and tried to get back to my Windows XP, I had the same blinking cursor. I was debating leaving the computer running like that for a while and hoping it was doing something. I left it for about an hour and nothing. 

I figured that someone else had to have had the same problem as I am. I hope that we can fix the problem. I did backup all of the important data on the computer, but I would rather not wipe the computer out if there is a known way of fixing this issue. Thanks.

---

### Post by confused57 on 2010-09-27
It would probably help if you could post the output of the Results.txt from the bootinfo script:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by bokeifus on 2010-09-27
Thank you for helping me out. I would prefer not to reinstall everything over again. My guess is that the smart idea is to set the partitions upon installing Windows XP and then just simply pointing Ubuntu to the second partition on the install. I would love not to have to do all of that, so if you could help me get this thing working without all of that, that would be great.

Here is the RESULTS.TXT file.

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

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

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   293,025,615   293,025,553   7 HPFS/NTFS
/dev/sda2         293,025,790   390,721,535    97,695,746   5 Extended
/dev/sda5         293,025,792   386,633,727    93,607,936  83 Linux
/dev/sda6         386,635,776   390,721,535     4,085,760  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        8C3C128B3C127106                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        1e6b6168-57f8-4489-bb81-fccccb11749d   ext4                                     
/dev/sda6        200e78de-786f-46d8-8fde-3959619a4c9b   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sr1         /media/Motorola          iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
/dev/sda1        /media/8C3C128B3C127106  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

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
search --no-floppy --fs-uuid --set 1e6b6168-57f8-4489-bb81-fccccb11749d
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
search --no-floppy --fs-uuid --set 1e6b6168-57f8-4489-bb81-fccccb11749d
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 1e6b6168-57f8-4489-bb81-fccccb11749d
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=1e6b6168-57f8-4489-bb81-fccccb11749d ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 1e6b6168-57f8-4489-bb81-fccccb11749d
    echo    'Loading Linux 2.6.32-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=1e6b6168-57f8-4489-bb81-fccccb11749d ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 1e6b6168-57f8-4489-bb81-fccccb11749d
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 1e6b6168-57f8-4489-bb81-fccccb11749d
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 8c3c128b3c127106
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
# / was on /dev/sda5 during installation
UUID=1e6b6168-57f8-4489-bb81-fccccb11749d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=200e78de-786f-46d8-8fde-3959619a4c9b none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 180.9GB: boot/grub/core.img
 179.0GB: boot/grub/grub.cfg
 182.2GB: boot/initrd.img-2.6.32-24-generic-pae
 181.4GB: boot/vmlinuz-2.6.32-24-generic-pae
 182.2GB: initrd.img
 181.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  10 61 2b 2a 9a 99 f4 52  a2 be ed b8 13 29 cc a6  |.a+*...R.....)..|
00000010  2a b9 54 fb f0 55 66 22  c5 9e 85 cb 7b 04 01 a1  |*.T..Uf"....{...|
00000020  ba d8 b5 33 c0 f1 12 77  29 19 ba 66 f4 06 ea a6  |...3...w)..f....|
00000030  7b ed 7d 71 a2 a0 e9 54  41 2a 25 d4 c3 7d ab 4d  |{.}q...TA*%..}.M|
00000040  bb 08 c3 43 e6 06 1a 34  48 73 18 19 cd 2d 76 a5  |...C...4Hs...-v.|
00000050  06 09 14 60 72 54 64 64  d9 c0 70 5f b6 60 20 44  |...`rTdd..p_.` D|
00000060  a0 d1 05 2a e7 43 10 02  a2 dc 57 2d d4 2a 11 a8  |...*.C....W-.*..|
00000070  60 e9 c5 0b a8 ae b5 26  49 19 c5 49 35 7a 27 9c  |`......&I..I5z'.|
00000080  94 5e b7 82 c8 f2 8d 0a  03 c2 b0 94 11 40 36 09  |.^...........@6.|
00000090  bf 65 28 37 e4 a0 88 01  90 48 ba a2 c7 25 1c 29  |.e(7.....H...%.)|
000000a0  2d 89 83 9f d8 3a ca 43  eb 63 80 a3 e2 00 c1 d8  |-....:.C.c......|
000000b0  bb 31 3e 1e 04 ba ec 25  01 d1 d9 c7 01 82 36 45  |.1>....%......6E|
000000c0  44 91 20 84 0e c5 4a 10  a0 46 a9 c0 e3 75 b9 94  |D. ...J..F...u..|
000000d0  40 3b e7 3b 3f fe 01 95  78 12 65 e7 3c 1a a6 2e  |@;.;?...x.e.<...|
000000e0  fd 96 b7 79 93 92 48 ad  a1 61 13 18 c9 0f 8d 0e  |...y..H..a......|
000000f0  f6 28 11 a2 4e 2b 3e 65  c1 93 76 9f d9 fb ff 6a  |.(..N+>e..v....j|
00000100  3f 9d b5 05 37 e4 f7 e3  bd 87 bd e9 fe 40 e3 a4  |?...7........@..|
00000110  2e bd 14 04 06 ec c4 12  10 38 74 e1 61 df 07 05  |.........8t.a...|
00000120  6c ef bf 40 78 7d 2b 83  df 7e a8 f0 c0 96 87 02  |l..@x}+..~......|
00000130  3c 9a 7a 14 05 87 dd c0  bf 1e f2 6d 0f c9 0e 05  |<.z........m....|
00000140  05 48 2f 22 01 10 fe ad  25 bb 10 57 ee f8 fa 48  |.H/"....%..W...H|
00000150  1c 7f 2d 2c 20 0e b3 68  d2 c1 c0 18 7f 9f f6 9e  |..-, ..h........|
00000160  ff e9 47 79 06 85 7a 47  99 21 51 61 0b 87 91 0a  |..Gy..zG.!Qa....|
00000170  81 cf 03 00 a0 1c d6 05  0f f0 10 08 81 45 81 08  |.............E..|
00000180  12 81 12 1a 07 81 45 05  00 38 14 57 fa 69 68 00  |......E..8.W.ih.|
00000190  31 b7 9f 0a 07 87 35 b7  6b 7b a2 39 1e 57 cd 1c  |1.....5.k{.9.W..|
000001a0  78 0c 21 a8 0e 81 31 ab  24 56 f6 2b 56 d6 7f e8  |x.!...1.$V.+V...|
000001b0  1d 11 e2 f8 25 32 a1 79  c8 21 56 e0 d8 27 00 fe  |....%2.y.!V..'..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 58 94 05 00 fe  |...........X....|
000001d0  ff ff 05 fe ff ff 02 58  94 05 00 60 3e 00 00 00  |.......X...`>...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde

---

### Post by confused57 on 2010-09-28
It's possible that resizing the Window's partition corrupted the filesystem and it just needs a chkdsk.  You can boot an XP installation cd(not a recovery disk), press "r" for recovery, then run  chksdsk:
chkdsk c: /f /r

I've never personally run a chkdsk from an XP install cd...you may want to do a search for
chkdsk for a more thorough explanation.

Here's a tutorial for restoring Windows/grub
bootloaders:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by bokeifus on 2010-09-28
I tried the chkdsk, I also tried chkdsk c: /R. It turns out that /f does not exist. The chkdsk ran twice and no boot. 

I also tried fixboot from the windows cd and that did not fix it either. I did not try FIXMBR because it said that it could ruin all of the partitions from booting. I would love to avoid that. 

Is there anyone who has experienced this before and managed to fix it? I appreciate any help on this issue. 

Also, if there is no way to fix this problem, what should my next step be? Should I reinstall windows, then ubuntu? Setting the ubuntu partition while setting up the partition during windows installation?

BTW, I am new to ubuntu and I think it's great. I just have too many windows programs that I depend on now, so I need both operating systems.

Thanks for all the help so far.

---

### Post by confused57 on 2010-09-28
> **bokeifus said:**
> I tried the chkdsk, I also tried chkdsk c: /R. It turns out that /f does not exist. The chkdsk ran twice and no boot. 

I also tried fixboot from the windows cd and that did not fix it either. I did not try FIXMBR because it said that it could ruin all of the partitions from booting. I would love to avoid that. 

Is there anyone who has experienced this before and managed to fix it? I appreciate any help on this issue. 

Also, if there is no way to fix this problem, what should my next step be? Should I reinstall windows, then ubuntu? Setting the ubuntu partition while setting up the partition during windows installation?

BTW, I am new to ubuntu and I think it's great. I just have too many windows programs that I depend on now, so I need both operating systems.

Thanks for all the help so far.

Let's try creating a grub2 custom entry for booting XP:
[https://help.ubuntu.com/community/Grub2#Creating%20the%20Custom%20Menu](https://help.ubuntu.com/community/Grub2#Creating%20the%20Custom%20Menu)

```
sudo gedit /etc/grub.d/40_custom
```
then add this entry:
```
menuentry "Chainload Windows XP" {
    set root=(hd0,1)
    chainloader +1   
}
```
it would be best to just copy&paste the above entry into your 40_custom
save & quit, then see if XP will boot with this entry

---

### Post by bokeifus on 2010-09-28
Thank you for all of your help but I have school projects that need to get done, so I just wiped the disk and reinstalled windows. I saved all of my important files through ubuntu and then reinstalled windows xp completely. I saved a bunch of space for ubuntu to be installed on and when I installed ubuntu again and setup partitions manually, I created a small partition for swap space and the rest for ubuntu.

I booted up into windows and it works fine. Ubuntu also works fine. Thank god I have this all worked out. Sorry I didn't have the patience to fully try and figure this out. But for anyone else who may be having this problem, this is definitely an option that works.

Thanks a lot for all of your help. I appreciate that.

---

### Post by confused57 on 2010-09-28
Glad you were able to get a fully functioning dual boot working...a fresh install of XP is probably the best way to go anyhow.

---

