---
title: "Ubuntu does not show up in the boot menu"
date: 2011-01-23
forum: Installation &amp; Upgrades
---

### Post by sai_pursnal on 2011-01-23
Hi,
     My system had Windows Vista initially. I installed Ubuntu 10.04 64 bit initially and everything was fine. I was able to use both the OS. 
Recently I installed Ubuntu 10.10 32 bit in the same partition as Ubuntu 10.04 by dividing it into two equal halves.
Now I am able to boot into 32 bit 10.10 but when I try to boot into the old 64 bit 10.04 it says 
unable to mount /root/proc, and some other "Unable to mount...." messages and it gives me a command prompt.
I entered into 32 bit 10.10 OS  and did update-grub2 and when I restart, the boot menu has no option for 64 bit 10.04 version at all... 
How can I restore my Ubuntu 64 bit 10.04 and boot into it...
Please advice me.... I have been using 64 bit OS for long time and have many important files...
Please help me..

---

### Post by sai_pursnal on 2011-01-23
This is the output I got from boot info script....
Please help me on what next can be done

/dev/sda5 says wrong fs and mounting failed...
how can I make that work again.....

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.
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
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       swsuspend
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: unknown filesystem type 'swsuspend'

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       128,519       128,457  de Dell Utility
/dev/sda2             129,024    31,586,303    31,457,280   7 HPFS/NTFS
/dev/sda3    *     31,586,304   357,771,571   326,185,268   7 HPFS/NTFS
/dev/sda4         357,773,310   625,141,759   267,368,450   5 Extended
/dev/sda5         357,773,312   485,985,279   128,211,968  83 Linux
/dev/sda6         614,199,296   625,141,759    10,942,464  82 Linux swap / Solaris
/dev/sda7         485,986,304   608,874,495   122,888,192  83 Linux
/dev/sda8         608,876,544   614,197,247     5,320,704  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4089 MB, 4089445376 bytes
33 heads, 63 sectors/track, 3841 cylinders, total 7987198 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     7,987,197     7,987,166   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        07DA-071E                              vfat       DellUtility                   
/dev/sda2        C026082126081AD4                       ntfs       RECOVERY                      
/dev/sda3        0ABA0AECBA0AD45B                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        ef783791-2076-45e2-8746-43960bb950ad   ext4                                     
/dev/sda6        318cf1b6-7cfe-4514-9695-f2cbac990675   swap                                     
/dev/sda7        3e917351-13bd-4ee1-bedc-310566fcc3f7   ext4                                     
/dev/sda8        35a16ad1-5239-428a-a35a-77fb2cbee517   swsuspend                                
/dev/sda: PTTYPE="dos" 
/dev/sdb1        6CF0-B46A                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 3e917351-13bd-4ee1-bedc-310566fcc3f7
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 3e917351-13bd-4ee1-bedc-310566fcc3f7
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 3e917351-13bd-4ee1-bedc-310566fcc3f7
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=3e917351-13bd-4ee1-bedc-310566fcc3f7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 3e917351-13bd-4ee1-bedc-310566fcc3f7
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=3e917351-13bd-4ee1-bedc-310566fcc3f7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 3e917351-13bd-4ee1-bedc-310566fcc3f7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 3e917351-13bd-4ee1-bedc-310566fcc3f7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 0aba0aecba0ad45b
    drivemap -s (hd0) ${root}
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

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=3e917351-13bd-4ee1-bedc-310566fcc3f7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=35a16ad1-5239-428a-a35a-77fb2cbee517 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 257.7GB: boot/grub/core.img
 283.4GB: boot/grub/grub.cfg
 274.8GB: boot/initrd.img-2.6.35-22-generic
 257.7GB: boot/vmlinuz-2.6.35-22-generic
 274.8GB: initrd.img
 257.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 5c a4 07 00 fe  |...........\....|
000001d0  ff ff 05 fe ff ff 02 b8  48 0f 00 00 a7 00 00 00  |........H.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 26 00  |.X.SYSLINUX...&.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 20 00 00 00  |........?... ...|
00000020  de df 79 00 69 1e 00 00  00 00 00 00 02 00 00 00  |..y.i...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 6a b4 f0 6c 4e  4f 20 4e 41 4d 45 20 20  |..)j..lNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 10 40 00 00  66 ba 00 00 00 00 bb 00  |}.f..@..f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by Bucky Ball on 2011-01-23
Have you tried:

sudo update-grub

... in a terminal?

---

### Post by sai_pursnal on 2011-01-23
Yeah I have done that...
Before doing update-grub, there was option for the 64 bit version in boot menu 
after doing that, the option disappeared from the menu

---

### Post by presence1960 on 2011-01-23
sda5 seems to be corrupted or have some other problem, that looks like it was the 10.04 partition. Boot the Live CD and choose try ubuntu. When the desktop loads open a terminal and run ```
sudo e2fsck /dev/sda5 -y -f -v -c
```This will run a file system check and if errors are found will attempt to fix them.

---

### Post by sai_pursnal on 2011-01-23
@presence1960
thanks for the reply
I ran the command, and it checked the drive /dev/sda5 and I think it attempted to fix some errors.
what should I do next?
how to get the OS option in boot menu?

Another problem that I found just now is even the 32 bit version 10.10 (which I mentioned in the first post) is not booting. It shows the same problem "Unable to mount /root/proc" and someother "Unable to mount...." and this is in /dev/sda7
So i tried running boot info script again and the script runs forever and the last line it shows is 
"Searching sda7 for information"

What could be the problem...

---

### Post by sai_pursnal on 2011-01-23
I tried running the command sudo e2fsck /dev/sda7 -y -f -v -c

It always shows this
root@ubuntu:~# sudo e2fsck /dev/sda7 -y -f -v -c
e2fsck 1.41.12 (17-May-2010)
e2fsck: Device or resource busy while trying to open /dev/sda7
Filesystem mounted or opened exclusively by another program?

I am sure I have no other program runnng... and I am doing this by booting Ubuntu from USB

---

### Post by presence1960 on 2011-01-23
> **sai_pursnal said:**
> I tried running the command sudo e2fsck /dev/sda7 -y -f -v -c

It always shows this
root@ubuntu:~# sudo e2fsck /dev/sda7 -y -f -v -c
e2fsck 1.41.12 (17-May-2010)
e2fsck: Device or resource busy while trying to open /dev/sda7
Filesystem mounted or opened exclusively by another program?

I am sure I have no other program runnng... and I am doing this by booting Ubuntu from USB

From the Live CD/USB boot to the desktop. Go System > Administration > Gparted Partition Editor. Look to see if sda7 is mounted. If it is right click sda7 and choose unmount. Then run the command again. Also you did not hibernate/suspend sda7 did you?

---

### Post by presence1960 on 2011-01-23
I see you have a Dell. You may want to disable the DataSafe software that came with the machine.

---

### Post by sai_pursnal on 2011-01-24
I checked the Gparted Partition editor and the /dev/sda7 is not mounted. I can see the "Unmount" option on right click is not active.

I tried the command e2fsck but failed with the same reason

I never suspended sda7 or I do not know how to do that...
boot info script worked fine once today
that was how i generated the result.txt that is in my second post...
but later on seeing 32 bit version also not working... I did boot from USB and found both
boot info script and e2fsck not working on /dev/sda7

Yes my system is DELL. How is Datasafe software related to this problem?

---

### Post by wilee-nilee on 2011-01-24
> **sai_pursnal said:**
> I checked the Gparted Partition editor and the /dev/sda7 is not mounted. I can see the "Unmount" option on right click is not active.

I tried the command e2fsck but failed with the same reason

I never suspended sda7 or I do not know how to do that...
boot info script worked fine once today
that was how i generated the result.txt that is in my second post...
but later on seeing 32 bit version also not working... I did boot from USB and found both
boot info script and e2fsck not working on /dev/sda7

Yes my system is DELL. How is Datasafe software related to this problem?

[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

---

### Post by sai_pursnal on 2011-01-24
@wilee-nilee and presence 1960
I checked whether Dell Datasafe is installed in my "Programs and Features" in Wndows Vista and I do not find any such software installed.

---

### Post by sai_pursnal on 2011-01-24
@ presence1960

Now that i ran e2fsck on my /dev/sda5 and fixed errors... how to get the OS. which is in /dev/sda5, option in the boot menu...
Please let me know...

---

### Post by Quackers on 2011-01-24
You could try re-installing grub first. 
From the live cd desktop open up a terminal and run these commands please
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
Then reboot and see what happens.
It may be necessary to purge and then re-install grub, but this is a quick way to find out.

---

### Post by presence1960 on 2011-01-24
> **sai_pursnal said:**
> @ presence1960

Now that i ran e2fsck on my /dev/sda5 and fixed errors... how to get the OS. which is in /dev/sda5, option in the boot menu...
Please let me know...

before you do anything run another boot info script and post the new output.

---

### Post by sai_pursnal on 2011-01-24
@presence1960
boot info script gets stuck at /dev/sda7 forever
I checked whether /dev/sda7 is mounted in "Gparted Partition Editor". It is not mounted
I checked whether Dell Datasafe software is installed in Vista, it is not installed
I could not check the other point u mentioned, whether did I hibernate /dev/sda7... I never did that
knowingly... but let me know how to check that...

---

### Post by presence1960 on 2011-01-24
> **sai_pursnal said:**
> @presence1960
boot info script gets stuck at /dev/sda7 forever
I checked whether /dev/sda7 is mounted in "Gparted Partition Editor". It is not mounted
I checked whether Dell Datasafe software is installed in Vista, it is not installed
I could not check the other point u mentioned, whether did I hibernate /dev/sda7... I never did that
knowingly... but let me know how to check that...

maybe your ubuntu on sda7 is trashed. But you can get the ubuntu on sda5 booting by following Quackers commands  he posted

---

### Post by sai_pursnal on 2011-01-25
@Quackers

sudo mount /dev/sda5 /mnt sudo grub-install --root-directory=/mnt /dev/sda
I typed these commands from Ubuntu booted from USB.
How long does it take to complete generally...
It ran for 30 min and still not completed...

---

### Post by Quackers on 2011-01-25
They are normally entered as separate lines!
It takes about 5 seconds, normally!

---

### Post by sai_pursnal on 2011-01-26
Yeah i entered them separately... copied wrongly here...
it ran for 30 min and still not completed!
is there any other alternative

---

### Post by Quackers on 2011-01-26
30 minutes is way too long. Something is wrong. See if pressing ctrl+c stops it running.
It may be worth running the boot script again please.
Also what does gparted screen show?

---

### Post by sai_pursnal on 2011-01-26
@Quackers
Thanks for the replies....
I tried running boot info script... but it gets stuck at "Searching for sda7 information".
I am also attaching screenshot of my gparted partition editor window....
I can see a red circle with an exclamatory mark on /dev/sda3 partition has Windows!
Please let me know if u need to know any other details...

If I am right sda5 has 64 bit linux and sda7 has 32 bit linux...

In case u did not follow my posts... I am just putting down what happened from beginning
I have Windows vista initially... then I installed Ubuntu 10.04 64 bit edition and dual boot worked fine for long time (6 months). Recently 2 weeks back, I tried to install a 32 bit linux Ubuntu 10.10 also. Installation completed fine. But on immediate reboot, 32 bit version OS worked fine, but when I tried to boot into 64 bit version, it kept failing saying "Unable to mount /root/proc" and someother "Unable to mount...". 
Then from USB I booted and ran boot info script and pasted it here in second post of this thread. Later on the same day, when I tried to boot into 32 bit version, it also kept failing saying the same as 64 bit version. 
From then boot info script fails to run... getting stuck at "Searching for sda7 info"....
In between I ran e2fsck on sda5 to fix any errors. It ran to completion and fixed some errors.

---

### Post by Quackers on 2011-01-26
In gparted right-click on both swap partitions and select "swapoff", then right click on sda7 and try deleting the partition - obviously, if it works you will lose your 32 bit installation, but it may solve all your problems too!). 
Then reboot and see what happens :-)
If ubuntu boots run sudo update-grub in a terminal.

The red circle next to /dev/sda3 may mean that Windows will want a chkdsk running before it will boot. If all other problems are solved, try booting Windows and see if it autoruns a chkdsk.

---

### Post by sai_pursnal on 2011-01-26
Let me get the steps right
From USB booted Desktop
1. On both the swap partitions, select "swap off".
2. select sda7, delete the partition

Then reboot

But by doing this, will we get 64 bit version option in the boot menu.
Or after the first two steps, do I need to any thing else before I reboot so that I get 64 bit version option in boot menu?

---

### Post by Quackers on 2011-01-26
If your 64 bit version is in sda5 (as you seem to think it is) you should be fine.

---

### Post by sai_pursnal on 2011-01-28
Thanks everyone,
I followed Quackers commands and deleted the partition that has my 32 bit version...
and on reboot, the boot menu automatically showed my 64 bit version.

@Quackers
Your advice helped a lot....
How did 64 bit version option come automatically on deleting the partition that has 32 bit OS?

---

### Post by Quackers on 2011-01-28
You're welcome :-)  Happy to hear things are better now!
I suspect something went wrong in the partitioning stage of the installation to sda7. It seems to have made both sda5 and sda7 corrupt, to some degree. I am pleasantly surprised to see that it allowed you to delete sda7 - I wasn't sure that it would allow it.

---

### Post by sai_pursnal on 2011-01-29
Initially I tried to "swap-off" the two swap spaces, it took long time and it never ended.
So I did close the gparted window after waiting for some time, when attempting to swap off both the swap spaces.
When I reopen the gparted window, it used to show "Swap On" for both the swap partitions.
Then I went ahead and placed a request for deleting /sda7 and when I applied the change,
it did not allow me. It said that there is an error.
But it showed "unallocated" for a partition before which it was /sda7
Then I tried to delete the swap space allocated for 32 bit OS, the same error popped up. But in the gparted window, it showed unallocated for the corresponding partition.
Then I ran boot info script, and it ran successfully to completion, and felt happy seeing the file system properly in /sda5 and identifying the 64 bit OS.
Then I rebooted and everything is in place as before.:p

---

### Post by Quackers on 2011-01-29
How do you mean? "everything is in place as before"? You mean sda7 is back now? You have problems again?

---

### Post by sai_pursnal on 2011-02-02
No... I said my old 64 bit version is working now as before... 
/sda7 is still unallocated space... it is not troubling me anymore... sorry for misleading...

---

### Post by Quackers on 2011-02-02
Oh, that's good then :-)
No problem :wink:

---

