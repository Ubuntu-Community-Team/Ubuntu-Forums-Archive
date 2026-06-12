---
title: "Need help reinstalling grub2"
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by Tjampman on 2010-06-07
Hi after having reinstalled windows XP I now need to get my PC to boot my grub menu...

I'm using Ubuntu 10.04 with grub 1.98
I have several disks and partitions, but the important ones is on my SDC drive, where SDC1 is windows, SDC2 is boot (300 MB), SDC6 /home, and SDC5 is /

I have been following this guide: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

But when I get to the final part, i get an error message.
```
$ sudo grub-install --root-directory=/media/0d104aff-ec8c-44c8-b811-92b993823444 /dev/sda
/usr/sbin/grub-setup: warn: Your embedding area is unusually small. core.img won't fit in it..
/usr/sbin/grub-setup: warn: Embedding is not possible. GRUB can only be installed in this setup by using blocklists. howevver, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.

```

I don't know what this means, other than not allowing me to install grub... What embedding area is to small? It can't be my boot partition, 'cause 300 mb should be more than enough, it has been so far.

What should I do to reinstall grub2?

BR Ole

---

### Post by wojox on 2010-06-07
Here. This is a whole lot easier. [Reinstalling GRUB 2 from LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

---

### Post by darkod on 2010-06-07
If you have ubuntu /boot partition (unless you are talking about win7 boot partition), don't forget to mount it too. If what you wrote is correct, you only need to do:

sudo mount /dev/sdc5 /mnt
sudo mount /dev/sdc2 /mnt/boot
sudo grub-install --root-directory=/mnt/ /dev/sdc

In the third command I assumed you want grub2 on /dev/sdc, change if otherwise. But grub2 can have a delay in booting if it's not on the ubuntu disk.

---

### Post by Tjampman on 2010-06-07
Yes yhank you it looks somewhat simpler.
I do have one question: 
> Mount the partition containing the Ubuntu installation.
What partitions should I mount? all three? /, /home and /boot or just the /boot partition?

thank you

---

### Post by darkod on 2010-06-07
It usually means only / but if you have separate /boot, you need to mount it too as said above.

---

### Post by Tjampman on 2010-06-07
Ok, I just tried what was described in the earlier post, but I get the same error as before, that "the embedding area is unusually small"...

---

### Post by Tjampman on 2010-06-07
Alright, I am still fumbling in the dark here... I have **un**succesfully tried the following:

```
$ sudo grub-setup -d /media/XXXX/boot/grub /dev/sdc
```

This gave the same error about "embedding is unusually small"

I also in desperation tried to unflag boot on SDC1 and flag boot on SDC2 but, that didn't work either, as i could not boot at all.

---

### Post by darkod on 2010-06-07
> **Tjampman said:**
> Alright, I am still fumbling in the dark here... I have **un**succesfully tried the following:

```
$ sudo grub-setup -d /media/XXXX/boot/grub /dev/sda
```This gave the same error about "embedding is unusually small"

I also in desperation tried to unflag boot on SDC1 and flag boot on SDC2 but, that didn't work either, as i could not boot at all.

I have no idea what this command does. I am used to using grub-install, not grub-setup, and what is mounted under /media, and why are you specifying the /boot/grub folder anyway?

Not sure what is going on when you try installing on /dev/sda, did you try to install grub2 to /dev/sdc, exactly as the commands are in post #3?

---

### Post by darkod on 2010-06-07
I just noticed this from your first post:

/usr/sbin/grub-setup: warn: Embedding is not possible. BRUB can only be installed in this setup

Are you using Grub2 at all, or you installed some modified bootloader BRUB? If you did, you should refer to its instructions for reinstall, not Grub2.

Your thread title is for Grub2 and you asked about reinstalling grub2 but it seems you have something else installed initially.

---

### Post by Tjampman on 2010-06-07
The grub-setup command I used as is from the method 2 rom this page: [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

When I tried it on my computer I used sdc!
(When copying and pasting in to the forum, I forgot to change sda to sdc - sorry for the confusion)

---

### Post by kansasnoob on 2010-06-07
It would probably be best if you'd post the full output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by darkod on 2010-06-07
> **kansasnoob said:**
> It would probably be best if you'd post the full output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

+1

At this point I have to agree. I thought it will be simple grub2 reinstall and didn't want to complicate with the script, but now it's better to run it so we can have clear idea what setup do you have.

I'm still confused by that BRUB message.

---

### Post by Tjampman on 2010-06-07
> **darkod said:**
> I just noticed this from your first post:

/usr/sbin/grub-setup: warn: Embedding is not possible. BRUB can only be installed in this setup

Are you using Grub2 at all, or you installed some modified bootloader BRUB? If you did, you should refer to its instructions for reinstall, not Grub2.

Sorry that is a spelling error, as I don't have access to my wifi on the Ubuntu live CD I had typed the above information manually on my laptop.

I have corrected the spelling mistake in my first post.

---

### Post by Tjampman on 2010-06-07
> **kansasnoob said:**
> It would probably be best if you'd post the full output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Alright, I will try that, but it will take a little while as I need to install the ndis wrapper and find my windows driver for the wireless card...

---

### Post by 1999panos on 2010-06-07
This happened to me too one day. I reinstalled Ubuntu in order to fix this. But now, I know how to do this very easy. 


You will need:

a PC (with an os installed! :P)
Internet connection


You download SUPER GRUB DISC. Which restores GRUB automatically. I read that it had saved lots of people. You can download it from here: [http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5) .

---

### Post by darkod on 2010-06-07
> **Tjampman said:**
> Alright, I will try that, but it will take a little while as I need to install the ndis wrapper and find my windows driver for the wireless card...

It might be faster downloading the script on another computer (it can even be in windows), put it on usb stick, then on the computer with the problem boot into live mode, copy the script to Desktop or where ever, execute it, and take the results.txt file on the stick again.

And post it from the other computer. Or from windows.

---

### Post by darkod on 2010-06-07
> **1999panos said:**
> This happened to me too one day. I reinstalled Ubuntu in order to fix this. But now, I know how to do this very easy. 


You will need:

a PC (with an os installed! :P)
Internet connection


You download SUPER GRUB DISC. Which restores GRUB automatically. I read that it had saved lots of people. You can download it from here: [http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5) .

There are still things to investigate and try. I don't recommend SGD until there are option to try. If you use SGD you ae not using grub from ubuntu and later it can create confusion.

For reinstall for example. The standard commands won't work because you are not running grub from ubuntu.

It has saved some people, but it has also created more problems for others. It all depends.

---

### Post by Tjampman on 2010-06-07
Alright here is the output from the boot info script, everything above sdc i.e. sde etc, is external drives or optical discs

It says there is some grub installations on both both sda and sdb, but that must be some old ones... 
Furthermore, i did some surfing around, and the error I am expecting seems to be related to the SDC1 starts at 19, and not 63. I don;t know how this has happened but I used the winXP install create the partition, but that has neverbeen a problem before.

Do you have any further suggestions?


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /grub/stage2 and /grub/menu.lst.
 => Grub  is installed in the MBR of /dev/sdb and looks at sector 280958203 on 
    boot drive #2 for the stage2 file, but no stage2 files can be found at 
    this location.
 => Windows is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd
 => No boot loader is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img /boot/grub/core.img

sdc3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab

sdc6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   280,575,224   280,575,162   7 HPFS/NTFS
/dev/sda2         280,575,225   321,669,494    41,094,270   5 Extended
Empty Partition


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.1 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders, total 156355584 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   156,344,579   156,344,517   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 640.1 GB, 640135028736 bytes
224 heads, 19 sectors/track, 293764 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             19   245,758,463   245,758,445   7 HPFS/NTFS
/dev/sdc2         245,762,048   246,347,775       585,728  83 Linux
/dev/sdc3         246,349,822   506,111,999   259,762,178   5 Extended
/dev/sdc5         246,349,824   304,941,055    58,591,232  83 Linux
/dev/sdc6         304,943,104   500,252,671   195,309,568  83 Linux
/dev/sdc7         500,254,720   506,111,999     5,857,280  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *          2,048 2,930,274,303 2,930,272,256   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1               2,048    78,137,343    78,135,296   7 HPFS/NTFS


GUID Partition Table detected, but does not seem to be used.

Partition           Start           End          Size System
/dev/sde1          16,065    78,140,126    78,124,062 Microsoft Windows

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        76E82078E820392F                       ntfs       Install                       
/dev/sda2: PTTYPE="dos" 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        D420F9CD20F9B718                       ntfs       misc                          
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        F8D49E2ED49DEEDE                       ntfs       WinXP                         
/dev/sdc2        2c71919e-5fc7-4f1b-a57a-2f3004d80669   ext3       Boot                          
/dev/sdc3: PTTYPE="dos" 
/dev/sdc5        3d559366-3f54-47af-8a2f-5466fd39127b   ext4       Ubuntu                        
/dev/sdc6        48e042eb-7475-49eb-ad9f-6820b30e3767   ext4       Ubuntu-home                   
/dev/sdc7        191c1677-c8e1-4e9a-8908-addbe25df910   swap                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        B408E28B08E24C44                       ntfs       WD-Antec                      
/dev/sdd: PTTYPE="dos" 
/dev/sde1        80B2D844B2D83FF8                       ntfs       40 Gigs                       
/dev/sde: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sde1        /media/40 Gigs           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdd1        /media/WD-Antec          fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sdc1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

============================= sdc2/grub/grub.cfg: =============================

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
set root='(hd2,5)'
search --no-floppy --fs-uuid --set 3d559366-3f54-47af-8a2f-5466fd39127b
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
set root='(hd2,3)'
search --no-floppy --fs-uuid --set 2c71919e-5fc7-4f1b-a57a-2f3004d80669
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,3)'
    search --no-floppy --fs-uuid --set 2c71919e-5fc7-4f1b-a57a-2f3004d80669
    linux    /vmlinuz-2.6.32-22-generic root=UUID=3d559366-3f54-47af-8a2f-5466fd39127b ro   quiet splash
    initrd    /initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,3)'
    search --no-floppy --fs-uuid --set 2c71919e-5fc7-4f1b-a57a-2f3004d80669
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /vmlinuz-2.6.32-22-generic root=UUID=3d559366-3f54-47af-8a2f-5466fd39127b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,3)'
    search --no-floppy --fs-uuid --set 2c71919e-5fc7-4f1b-a57a-2f3004d80669
    linux    /vmlinuz-2.6.32-21-generic root=UUID=3d559366-3f54-47af-8a2f-5466fd39127b ro   quiet splash
    initrd    /initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,3)'
    search --no-floppy --fs-uuid --set 2c71919e-5fc7-4f1b-a57a-2f3004d80669
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /vmlinuz-2.6.32-21-generic root=UUID=3d559366-3f54-47af-8a2f-5466fd39127b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd2,3)'
    search --no-floppy --fs-uuid --set 2c71919e-5fc7-4f1b-a57a-2f3004d80669
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd2,3)'
    search --no-floppy --fs-uuid --set 2c71919e-5fc7-4f1b-a57a-2f3004d80669
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdc1)" {
    insmod ntfs
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set e0f83cd2f83ca924
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sdc2: Location of files loaded by Grub: ===================


 125.9GB: boot/grub/core.img
 126.0GB: grub/core.img
 126.0GB: grub/grub.cfg
 125.8GB: initrd.img-2.6.32-21-generic
 125.8GB: initrd.img-2.6.32-22-generic
 125.8GB: vmlinuz-2.6.32-21-generic
 125.8GB: vmlinuz-2.6.32-22-generic

=============================== sdc5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=3d559366-3f54-47af-8a2f-5466fd39127b /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda3 during installation
UUID=2c71919e-5fc7-4f1b-a57a-2f3004d80669 /boot           ext3    defaults        0       2
# /home was on /dev/sda6 during installation
UUID=48e042eb-7475-49eb-ad9f-6820b30e3767 /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=191c1677-c8e1-4e9a-8908-addbe25df910 none            swap    sw              0       0
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc3

00000000  aa ab 31 96 4c a1 bb 4b  ff b9 e1 e5 15 16 2d 31  |..1.L..K......-1|
00000010  d4 2c 98 9d 0e fd e0 11  1e ef 10 64 c4 35 e1 7b  |.,.........d.5.{|
00000020  22 af 03 7b 2e 97 c8 e5  cf ea fb 1f 19 4a 19 57  |"..{.........J.W|
00000030  07 18 65 25 54 2d ca f5  43 30 c7 59 56 b1 76 74  |..e%T-..C0.YV.vt|
00000040  21 1e b3 23 1c 78 b3 ba  54 be 7b b7 ca 25 4b 95  |!..#.x..T.{..%K.|
00000050  62 1f ee 17 56 a4 52 0b  f2 5a 2a 89 b6 d4 3a 66  |b...V.R..Z*...:f|
00000060  bf 50 cd aa 94 d3 ea fb  db f0 6e fe f9 eb ff 02  |.P........n.....|
00000070  28 0d 43 54 56 75 36 1c  26 19 14 d4 76 51 02 c8  |(.CTVu6.&...vQ..|
00000080  b7 96 5c 6c 83 47 94 96  ba 21 e7 7e 4c 06 71 f7  |..\l.G...!.~L.q.|
00000090  6c e6 6f f0 fa 69 3b b9  a7 4c 08 25 a9 71 fa 87  |l.o..i;..L.%.q..|
000000a0  61 b1 25 22 08 4a 75 cc  ff fd 7c 03 57 73 83 80  |a.%".Ju...|.Ws..|
000000b0  c0 7a 71 cd 63 5a e1 86  b1 a4 cf f0 45 fe 95 ff  |.zq.cZ......E...|
000000c0  ff 3c 38 d3 8e 90 15 20  6f 51 f4 39 0d 40 7f 1c  |.<8.... oQ.9.@..|
000000d0  21 07 92 a9 a7 5d 72 00  9d 62 0f 5c d6 38 f7 eb  |!....]r..b.\.8..|
000000e0  81 50 75 6b 2b 75 11 c2  66 fd 90 ba 87 c0 a7 ca  |.Puk+u..f.......|
000000f0  bd c0 67 72 8d 1c 6d 4a  06 7f fe c3 59 08 c5 16  |..gr..mJ....Y...|
00000100  d1 8c aa db 79 b2 8e 7e  ed ff 56 1a 22 31 29 37  |....y..~..V."1)7|
00000110  b6 b5 a1 c6 c7 1a 52 c2  ee 45 00 c1 44 05 14 6d  |......R..E..D..m|
00000120  81 fc 17 a8 b5 94 b4 a3  30 30 64 63 7e 00 00 00  |........00dc~...|
00000130  00 00 01 b6 98 49 fc 14  9f ff ff 4e 9d 3a 55 27  |.....I.....N.:U'|
00000140  fa af ff ff d2 9a 5a 4e  9d 3a 74 e9 ff fe 9f fe  |......ZN.:t.....|
00000150  9f fa 74 e9 d3 a7 4e 9d  3a 7f ff fe 9d 2e 95 4e  |..t...N.:......N|
00000160  94 d3 a7 4b 49 ff ff d3  a7 4e 9d 3f ff ff f4 e9  |...KI....N.?....|
00000170  d3 ff fe 9e 9f a6 ff ff  ff ff ff 53 aa eb ff ff  |...........S....|
00000180  fd 2f ff ff aa 5f ab ff  ff ff 55 7f ff fa 53 5f  |./..._....U...S_|
00000190  aa 87 5f e9 17 ff ff d3  ff ff d3 ff ff ff ff ff  |.._.............|
000001a0  fa 7f ff a7 ff ff ff fa  9c 5f eb 75 ff 7f 30 31  |........._.u..01|
000001b0  77 62 e0 01 00 00 ff fa  a4 64 82 ff 07 00 00 df  |wb.......d......|
000001c0  d3 ff 83 df d3 ff 02 00  00 00 00 08 7e 03 00 df  |............~...|
000001d0  d3 ff 05 df d3 ff 42 0d  7e 03 c0 32 a4 0b 00 00  |......B.~..2....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Tjampman on 2010-06-07
> **Tjampman said:**
>  
Furthermore, i did some surfing around, and the error I am expecting seems to be related to the SDC1 starts at 19, and not 63. I don;t know how this has happened but I used the winXP install create the partition, but that has neverbeen a problem before.


Should I try to move the sdc1 partition with gparted? or will that just f*ck things up... I'd rather not have to reinstall windows yet again it is such a headache to get working with all drivers and programs needed...

---

### Post by darkod on 2010-06-07
> **Tjampman said:**
> Should I try to move the sdc1 partition with gparted? or will that just f*ck things up... I'd rather not have to reinstall windows yet again it is such a headache to get working with all drivers and programs needed...

Hold on. You are right, it's probably complaining because you don't have the first 63 sectors left aside. I'm not sure what to do right now.

Are all of the other disks external? Which one is internal that you can make first boot option?

---

### Post by Tjampman on 2010-06-07
My internal discs are sda, sdb and sdc, and I can make them all bootable in the BIOS

If I should try to make one of the other drives boot, I would prefer sda.

---

### Post by darkod on 2010-06-07
OK then, try this:

sudo mount /dev/sdc5 /mnt
sudo mount /dev/sdc2 /mnt/boot
sudo grub-install --root-directory=/mnt/ /dev/sda

That should not give the same error. Set sda to be first boot option in BIOS.

---

### Post by Tjampman on 2010-06-07
```
ubuntu@ubuntu:~$ sudo mount /dev/sdc5 /mnt
ubuntu@ubuntu:~$ sudo mount /dev/sdc2 /mnt/boot
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda
Installation finished. No error reported.

```

Alright, I'll try a restart and see how it goes...

---

### Post by Tjampman on 2010-06-07
SUCCESS 

Thank you very much for your patience and assistance, I can now boot in to Ubuntu again, and after ```
sudo update-grub
``` Windows XP is also working.

Have nice day :-)

---

### Post by darkod on 2010-06-07
Well, it's not the ideal situation, grub2 should usually be on the same disk as ubuntu. But it's a good quick fix. :)

I still have no idea why the /dev/sdc1 partition is starting at the 19th sector.

---

### Post by Tjampman on 2010-06-07
Well I'm happy that it works :-) but on the other hand I do not know what "not the ideal situation" means... I believe you mentioned earlier that it could cause a delay, and if that is all I can live with it as I do not notice any difference.

Regarding the 19th sector, I agree its a bit of a mystery, I had windows 7, installed before, and grub worked fine, so it must have happened when I used the WinXP installer to format the two win7 partitions (the strange boot one, and C:\). But as I said, that have never been a problem before.

---

### Post by cello75 on 2010-06-22
Hi - I just would like to leave a comment on Grub2 and dual-booting Windows (vista and 7) - because after upgrading my XP to Vista - I could not boot anymore and all tips and hints did not help - I always got the following message: 
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
/usr/sbin/grub-setup: error: If you really want blocklists, use --force

So - today - (!) I found a solution:
I used GParted to move the first partition on my (only) disk to "the right" to 'enlarge' the space for the first sectors (I had had only 4 or so sectors before the MSI-start-partition before) - so - GParted moved sda1 with ALL the files in it and resized sda1 - so the core.img would fit in. 
I do not know why it had worked before - but I had had a partition with a trial of windows 7 which I deleted - and now my system is: sda1 - MSI-partition sda2 - Vista - sda 4 - Ubuntu 10.04 - sda3 - swap. ;-) 
Many greetings

---

### Post by thahir1986 on 2010-06-22
thanks.

---

### Post by mountney on 2011-01-14
Tried re-installing Grub2 and still could not dual boot WinXP.

I had to create/[COLOR="Red"]modify[/COLOR] /etc/grub.d/11_Windows to boot WinXP...

#! /bin/sh -e
echo "Adding Windows XP" >&2
cat << EOF
menuentry "Windows XP" {
[COLOR="Red"]insmod ntfs[/COLOR]
set root=(hd1,1)
[COLOR="Red"]drivemap -s (hd0) \${root}[/COLOR]
chainloader +1
}
EOF

Then of course run update-grub and reboot...

Dell Optiplex GX520
2GB Ram
500GB Sata - Ubuntu 9.10 (/dev/sda)
250GB Sata - WinXP Professional (/dev/sdb)

Found that os-prober and thus 30_os-prober were NOT working so WinXP was not detected. Still researching why os-prober isn't detecting WinXP. I have three other systems, Debian 5 (64bit)/Win7 Ultimate (ASUS P6T), Ubuntu 10.04/WinXP (EPOX EP-4PLMI) and Ubuntu 9.10/WinXP (HP Pavilion dv8000 laptop) and on these os-prober/30_os-prober work fine.

Hope this helps some...

---

