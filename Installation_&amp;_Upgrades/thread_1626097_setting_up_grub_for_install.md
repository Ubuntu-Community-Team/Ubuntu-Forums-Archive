---
title: "setting up grub for install"
date: 2010-11-19
forum: Installation &amp; Upgrades
---

### Post by Ansible on 2010-11-19
Short version: how to get grub installed correctly on a second HD, which will be the boot disk when I change the boot order in the bios.

Long version:
Ok here's the deal.  I installed ubuntu on HD #1 a while back.  My Mobo died and I got a new one, which unlike the old one has no IDE bus.  Thus using a CD drive is not an option here - i'd rather not buy a SATA cd drive just for this.  I also got another HD, "HD #2".  I can boot into ubuntu on HD1 still but its unstable - something to do with the video drivers I suspect.  

Anyway, now I want to install ubuntu studio onto HD#2 and use that as the boot drive from now on.  I set up a partition on HD#2 for the installer, copied the install CD ISO into there, set up another partition for the OS, and I was able to install grub too.  However, when I try to boot onto that drive, grub never gets to its second stage.  

I suspect that its the addressing of grub devices that is to blame - when I set up grub I tell it where the install partition is, but that's relative to HD#1 being the boot disk.  When HD#2 is boot, the numbering is off and the grub files can't be found.

Anyway, can someone help me with the grub syntax needed here? thx.

---

### Post by oldfred on 2010-11-20
To see what you have installed where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by Ansible on 2010-11-21
Thx.  Here's the result, sure enough the grub on /dev/sdb appears to point to the wrong place.  I'd like it to point at the grub stuff in /dev/sdb4 when I change the BIOS to have sdb as the boot drive.  Whats in /dev/sdb4 is the contents of a 10.4 ubuntu studio install ISO.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on boot drive #1 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  Unknown
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0003be9d

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 1,459,183,949 1,459,183,887  83 Linux
/dev/sda2       1,459,183,950 1,465,144,064     5,960,115   5 Extended
/dev/sda5       1,459,184,013 1,465,144,064     5,960,052  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00012d81

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 2,405,990,789 2,405,990,727  83 Linux
/dev/sdb2       2,405,990,790 2,917,885,949   511,895,160  83 Linux
/dev/sdb3       2,922,078,915 2,930,272,064     8,193,150  82 Linux swap / Solaris
/dev/sdb4       2,917,885,950 2,922,078,914     4,192,965  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              iso9660    Ubuntu-Studio 10.04 LTS i386  
/dev/sda1        203b52df-d0ff-444d-8eab-639c870bcb6c   ext3                                     
/dev/sda5        ed480a94-c48a-4be4-a557-cdb1c72913b8   swap                                     
/dev/sdb1        784596cd-9e0b-44b6-9249-1ca6b1dd04f9   ext3                                     
/dev/sdb2        1d75d7c8-065c-450b-9a42-11ef0ce48892   ext3       bewt                          
/dev/sdb3        d2dbcf16-266c-43f5-9449-8ecbcd510981   swap       swap                          
/dev/sdb4        eb7fb9c5-3673-48ca-9d1b-b862c9d74aea   ext3       installer                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sdb4        /tmp/installer           ext3       (rw)
/dev/loop0       /tmp/install_cd          iso9660    (rw)


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=203b52df-d0ff-444d-8eab-639c870bcb6c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-17-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-17-generic root=UUID=203b52df-d0ff-444d-8eab-639c870bcb6c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-17-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-17-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-17-generic root=UUID=203b52df-d0ff-444d-8eab-639c870bcb6c ro  single
initrd		/boot/initrd.img-2.6.27-17-generic

title		Ubuntu 8.10, kernel 2.6.27-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-16-generic root=UUID=203b52df-d0ff-444d-8eab-639c870bcb6c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-16-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-16-generic root=UUID=203b52df-d0ff-444d-8eab-639c870bcb6c ro  single
initrd		/boot/initrd.img-2.6.27-16-generic

title		Ubuntu 8.10, kernel 2.6.27-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-15-generic root=UUID=203b52df-d0ff-444d-8eab-639c870bcb6c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-15-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-15-generic root=UUID=203b52df-d0ff-444d-8eab-639c870bcb6c ro  single
initrd		/boot/initrd.img-2.6.27-15-generic

title		Ubuntu 8.10, kernel 2.6.27-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=203b52df-d0ff-444d-8eab-639c870bcb6c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=203b52df-d0ff-444d-8eab-639c870bcb6c ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=203b52df-d0ff-444d-8eab-639c870bcb6c ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=203b52df-d0ff-444d-8eab-639c870bcb6c ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=203b52df-d0ff-444d-8eab-639c870bcb6c ro quiet splash 
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.10, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=203b52df-d0ff-444d-8eab-639c870bcb6c ro  single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=203b52df-d0ff-444d-8eab-639c870bcb6c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=ed480a94-c48a-4be4-a557-cdb1c72913b8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 646.4GB: boot/grub/menu.lst
 675.1GB: boot/grub/stage2
  76.9GB: boot/initrd.img-2.6.24-23-generic
  51.6GB: boot/initrd.img-2.6.24-23-generic.bak
  10.4GB: boot/initrd.img-2.6.27-11-generic
 646.3GB: boot/initrd.img-2.6.27-14-generic
 646.4GB: boot/initrd.img-2.6.27-15-generic
 283.1GB: boot/initrd.img-2.6.27-16-generic
 646.4GB: boot/initrd.img-2.6.27-17-generic
  51.5GB: boot/vmlinuz-2.6.24-23-generic
 721.6GB: boot/vmlinuz-2.6.27-11-generic
 646.3GB: boot/vmlinuz-2.6.27-14-generic
 646.3GB: boot/vmlinuz-2.6.27-15-generic
 646.4GB: boot/vmlinuz-2.6.27-16-generic
 646.4GB: boot/vmlinuz-2.6.27-17-generic
 646.4GB: initrd.img
 283.1GB: initrd.img.old
 646.4GB: vmlinuz
 646.4GB: vmlinuz.old

=================== sdb4: Location of files loaded by Grub: ===================


1495.6GB: boot/grub/stage2
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb3

00000000  8f a2 25 e4 22 11 74 98  70 b5 29 8e 17 4f 48 6c  |..%.".t.p.)..OHl|
00000010  96 47 06 13 a6 81 31 75  12 19 82 fb ac 20 4f ad  |.G....1u..... O.|
00000020  89 6e 3c c2 e4 b5 a9 da  c3 f8 4c 07 bf 6d 69 b2  |.n<.......L..mi.|
00000030  67 09 45 42 79 35 59 e1  59 71 7d 84 6b 23 2f 14  |g.EBy5Y.Yq}.k#/.|
00000040  4e d5 17 90 87 d5 ee 16  90 ba 94 3e 4c 22 b2 bc  |N..........>L"..|
00000050  b9 12 53 94 04 6f 9e 18  b4 68 84 9d 7e a7 8e ef  |..S..o...h..~...|
00000060  46 7a 78 34 0f 46 10 13  50 a0 12 46 c3 fa 84 ea  |Fzx4.F..P..F....|
00000070  5d 2f be 8d 8e b2 81 ed  31 54 af 0a 23 e7 ee 9e  |]/......1T..#...|
00000080  02 eb a7 0a aa bd f7 b5  1b a9 33 63 3b 55 91 1e  |..........3c;U..|
00000090  2f d8 6f 53 bb f3 d1 51  42 c7 ec 9a c4 a2 f4 67  |/.oS...QB......g|
000000a0  a3 fa bb 39 7f 1a 0c a8  ca 00 03 3d 22 80 26 f0  |...9.......=".&.|
000000b0  b0 64 23 15 ce 7a 0a 1b  04 89 78 ce 04 82 1a ab  |.d#..z....x.....|
000000c0  2e 0f 4c 74 30 c3 19 92  21 83 ff fb a0 64 10 88  |..Lt0...!....d..|
000000d0  f6 4b 68 d0 d3 4f 61 48  08 e0 1c 1e 08 00 01 19  |.Kh..OaH........|
000000e0  21 9f 43 ad bd 85 e8 01  80 72 00 10 00 04 98 f2  |!.C......r......|
000000f0  95 a2 51 10 79 16 14 8e  8c 6e 27 0e 6f 10 90 e2  |..Q.y....n'.o...|
00000100  26 27 3a 5c 24 e9 ab e4  66 2b 74 4f 23 58 84 69  |&':\$...f+tO#X.i|
00000110  42 09 64 ea d0 ae 7c fc  f3 8c 13 ab 32 b9 a2 c1  |B.d...|.....2...|
00000120  c8 f4 48 1e 5c 2b 25 3a  28 1f 13 47 d8 89 c5 d4  |..H.\+%:(..G....|
00000130  e7 50 db 5c 54 49 3f 24  1e c4 62 a9 72 32 f3 04  |.P.\TI?$..b.r2..|
00000140  d3 f2 65 10 0f 59 58 27  be 7e 58 2d 3f 75 83 e8  |..e..YX'.~X-?u..|
00000150  48 cb c5 d7 5e e6 33 09  c7 8d 6f 42 c4 0d b5 4b  |H...^.3...oB...K|
00000160  89 44 f1 30 f8 c0 49 3a  33 5f 11 68 c4 92 f1 59  |.D.0..I:3_.h...Y|
00000170  61 c1 97 dd eb 2f 5d 72  d1 e1 85 bc e6 8d 20 3f  |a..../]r...... ?|
00000180  85 37 d8 e8 da b4 54 71  d1 ec b6 60 09 a5 c4 35  |.7....Tq...`...5|
00000190  79 49 ed ac 6c bb 9e 00  00 00 00 00 00 00 02 03  |yI..l...........|
000001a0  91 84 80 01 4e ea 81 92  0a b4 21 95 06 5e 52 cc  |....N.....!..^R.|
000001b0  98 82 ae 64 71 f6 88 29  a3 a7 51 67 22 28 64 14  |...dq..)..Qg"(d.|
000001c0  8a 13 a5 40 c6 7f 30 a7  4b e2 f3 27 75 4f 40 8c  |...@..0.K..'uO@.|
000001d0  d1 6a 64 a4 51 20 ba 22  3f 10 fa 41 5e 7c 94 75  |.jd.Q ."?..A^|.u|
000001e0  b8 ee 6a af f1 d3 a2 52  63 94 ae 17 07 f4 ac 16  |..j....Rc.......|
000001f0  ee 34 ac 85 e1 10 8e 3e  36 c1 e1 7b 8c 14 99 f9  |.4.....>6..{....|
00000200


```

---

### Post by dino99 on 2010-11-21
What you should have:

- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing in manual mode by the "alternate" iso.
- swap : about 2 Gb (4 Gb if suspend/hibernate is used)
- /home : ext3 or ext4 format, unlimited space to store your data and settings

Looking the script output, i may say: clean the room first :(
- only 1 swap for all the distro
- why so many old kernels (the latest 2 are enough for each release)
- grub2 (10.04) & grub (legacy, 8.04) are not good friends, only grub-pc & grub-common need to be installed. So with synaptic: remove/purge ALL the grub related installed packages and menu.lst too, then install grub-pc & grub-common (you can install grub2 on both hdd , the installer will ask you about, only check the box(es) you like)

---

### Post by oldfred on 2010-11-21
It may have been possible from old grub to boot an ISO, but I have done it from grub2 from a hard drive. I usually use grub2 to boot my USB drive to loopmount the ISO, so I can have more than one ISO on the same flash drive.

Direct boot on hard drive:
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

Herman has lots of good info on grub & grub2.
Herman on separate grub partition:
[http://ubuntuforums.org/showthread.php?t=1320270](http://ubuntuforums.org/showthread.php?t=1320270)
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-install](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-install)

Almost all new motherboards still have one PATA connector just for your old CD or an old hard drive.

If you have a new motherboard it will let you boot USB flash drives which I now prefer to use over burning a new CD every time the install is updated or any of the repair CDs that I have get updated. I just have them all one one 4GB flash drive adn update regularly.

---

### Post by Ansible on 2010-11-28
My mobo is a zotac mini ITX and has no PATA connector - its SATA or USB only. 

Dino, I have 2 swaps because I plan on having the system run with either of the HDs by itself, with the other one removed.  I don't care how many old kernels are there because I have the space and I don't see them on boot.  Plus I'm probably going to replace that old install completely anyway, so why clean it up?

Anyway, thx for the help guys.  I cut the gordian knot of grub configuration by clearing out a 100g USB drive I had laying around and putting the installer there.  Then I removed the 750g drive from the system to make sure grub didn't go on there by accident and installed.  Now I can switch between the two disks using the BIOS, or just remove one of them and it works.

---

