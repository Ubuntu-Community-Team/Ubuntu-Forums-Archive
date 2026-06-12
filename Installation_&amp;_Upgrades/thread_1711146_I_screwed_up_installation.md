---
title: "I screwed up installation"
date: 2011-03-20
forum: Installation &amp; Upgrades
---

### Post by Reier on 2011-03-20
Hey all.

Came across Ubuntu a while ago and thought it looked interesting. I've never done another OS on my computer so I thought it would be a good experience. 
I am completely new at this, bear in mind. 
So I went to the website, read everything, yadda yadda. After much trouble getting it to load on my computer, (USB and CD were PAINS to get running, believe me), I FINALLY got to the Ubuntu 10.10 installation screen. I got to the part where I made a username and stuff, but it wouldn't let me go on after I entered the stuff in. Now I realize I could not have a capital in the username, but it did not tell me that at the time, so I was very confused. I really tried everything I could think of to get it to go (except making the first letter lower case, unfortunately), so I had to reboot the dang thing. I realize this was a mistake, as it ATE 80 GB of my HD space I found out later.
So, I tried it again, and figured out how to get past the register screen, and it pretty much installs without a hitch. Until I get to the part where you have to reboot, that is. I press the reboot button like it tells me to, and it goes through its little code lines, and whams out some dumb error. I unfortunately did not see what it was, I deeply apologize, as I realize it's probably vitally important now. 
So, I had to shut off the thing. I was glad to see the dual boot screen when I started my computer. I was not glad to see when I tried Ubuntu it wouldn't load. Now I dunno what to do. I lost 120 GB HD space I could use on my working Windows 7 system. I kinda want Ubuntu (80 GB or so, not 120), but it worst comes to worst I would rather uninstall it than have 120 gigs of useless junk sitting around I can't do anything with, or delete.
I know I screwed up, but if you could help, I would be really, really thankful.

Recap

320 GB Gateway NV5468u Windows 7 laptop
Attempted installation of dual boot Ubuntu 10.10 Desktop edition

Thanks in advance.

---

### Post by Hedgehog1 on 2011-03-20
These things happen.

Let's see what can be saved, shall we?

Please boot off the LiveCD/LiveUSB, select TRY, and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.


***The Hedge***

:KS

p.s. You wanted to end up with as dual-boot Win7 / Ubuntu 10.10 PC, right?

---

### Post by Dutch70 on 2011-03-21
Hello Reier & welcome to UF

 I know it's a frustrating & a little spooky at first, but try & take it easy. As long as you can boot into windows, I seriously doubt you've lost anything.

After... you do what Hedge asked & while you're logged-in to the live cd/usb. Open Gparted & take a screenshot(pic) of it. 
Attach it to your next post using the "paper clip" in the toolbar. So we can get a visual of your partitions. 
It's probably easier to put it in a separate post from your boot info script.

Also, could you give us a little more info on exactly what you mean by ..."it wouldn't load"? 
What **did** it do? what was on the screen? How long did you give it to load? Have you tried again? 

You're probably much closer than you realize to having a dual boot system.

---

### Post by Reier on 2011-03-21
Thanks for helping, guys.

@hedge

                > Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

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

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

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

/dev/sda1               2,048    24,578,047    24,576,000  27 Hidden HPFS/NTFS
/dev/sda2    *     24,578,048    24,782,847       204,800   7 HPFS/NTFS
/dev/sda3          24,782,848   444,164,461   419,381,614   7 HPFS/NTFS
/dev/sda4         444,166,142   625,141,759   180,975,618   5 Extended
/dev/sda5         507,791,360   620,259,327   112,467,968  83 Linux
/dev/sda6         620,261,376   625,141,759     4,880,384  82 Linux swap / Solaris
/dev/sda7         444,166,144   505,075,711    60,909,568  83 Linux
/dev/sda8         505,077,760   507,783,167     2,705,408  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2032 MB, 2032140288 bytes
16 heads, 32 sectors/track, 7752 cylinders, total 3969024 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064     3,969,023     3,960,960   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        DAA41C49A41C2B11                       ntfs       PQSERVICE                     
/dev/sda2        965C6D2C5C6D0877                       ntfs       SYSTEM RESERVED               
/dev/sda3        52B8796DB8795109                       ntfs       Gateway                       
/dev/sda4: PTTYPE="dos" 
/dev/sda5        8800d490-a41d-4f18-b74f-0b5b65cd6de6   ext4                                     
/dev/sda6        6f237a64-013c-4343-a1ed-696fe3f9b056   swap                                     
/dev/sda7        9e514730-1c24-4c00-9a67-e47d58b59a41   ext4                                     
/dev/sda8        b59ffd96-d9aa-455d-9d53-cfcd2858ca82   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        15FA-2442                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
UUID=8800d490-a41d-4f18-b74f-0b5b65cd6de6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=6f237a64-013c-4343-a1ed-696fe3f9b056 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 303.0GB: boot/vmlinuz-2.6.35-22-generic
 303.0GB: vmlinuz

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
search --no-floppy --fs-uuid --set 9e514730-1c24-4c00-9a67-e47d58b59a41
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 9e514730-1c24-4c00-9a67-e47d58b59a41
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 9e514730-1c24-4c00-9a67-e47d58b59a41
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=9e514730-1c24-4c00-9a67-e47d58b59a41 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 9e514730-1c24-4c00-9a67-e47d58b59a41
    echo    'Loading Linux 2.6.35-28-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=9e514730-1c24-4c00-9a67-e47d58b59a41 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 9e514730-1c24-4c00-9a67-e47d58b59a41
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos7)'
    search --no-floppy --fs-uuid --set 9e514730-1c24-4c00-9a67-e47d58b59a41
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set daa41c49a41c2b11
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 965c6d2c5c6d0877
    chainloader +1
}
menuentry "Ubuntu 10.10 (10.10) (on /dev/sda5)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 8800d490-a41d-4f18-b74f-0b5b65cd6de6
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda5
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
UUID=9e514730-1c24-4c00-9a67-e47d58b59a41 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=b59ffd96-d9aa-455d-9d53-cfcd2858ca82 none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 236.7GB: boot/grub/core.img
 236.1GB: boot/grub/grub.cfg
 245.0GB: boot/initrd.img-2.6.35-28-generic-pae
 236.6GB: boot/vmlinuz-2.6.35-28-generic-pae
 245.0GB: initrd.img
 236.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 04 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 80 1f 00 00  |........?.......|
00000020  80 70 3c 00 1b 1e 00 00  00 00 00 00 02 00 00 00  |.p<.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 42 24 fa 15 4e  4f 20 4e 41 4d 45 20 20  |..)B$..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 5a  3c 00 00 66 ba 00 00 00  |..E}.f.Z<..f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


@dutch
Not sure I understand what you want I should do. What is Gparted for instance?

---

### Post by oldfred on 2011-03-21
Boot script looks normal to me. You do have two installs sda5 which does not look complete & sda7 which does.

Do you get a grub menu to choose sda7, windows & sda5 systems?
If so then you have grub booted but may have video issues or other Ubuntu boot issues.

---

### Post by Reier on 2011-03-21
@fred

My options when I boot look like this:

> 
GNU GRUB version 1.98+20100804-5ubuntu3

----------------------------------------------------------
Ubuntu with Linux 2.6.35-28-generic-pae
Ubuntu with Linux 2.6.35-28-generic-pae (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows Vista (loader) (on /dev/sda1)
Windows 7 (loader) (on /dev/sda2
Ubuntu 10.10 (10.10) (on /dev/sda5)
When I try the last one (which I assume is the right one, though none of the Ubuntu ones work), it goes through gobs of code which I don't understand. After it does some code, it stops, always in the same place.

It would take forever to type out everything on the screen, but a few things I noticed were things like this (not typed exactly like I saw them):

cannot open rood device sda5 - unknown block, Kernel panic - not syncing, unable to mount root fs, etc...

I have no clue what they mean or anything but it shows what kind of stuff goes on when I try to boot Ub 10.10. Windows 7 works fine though.

---

### Post by Hedgehog1 on 2011-03-21
> **Reier said:**
> Thanks for trying to help, guys.  
 
Good news Reier! Dutch70 was quite right, you have not lost any data. <whew>
 
You did successfuly shrink your NTFS (Windows) parition before you rebooted; so you are OK.
 
Here is the net result of the two installs:
 
```
Partition Boot Start End Size Id System
 
/dev/sda1 2,048 24,578,047 24,576,000 27 Hidden HPFS/NTFS
/dev/sda2 * 24,578,048 24,782,847 204,800 7 HPFS/NTFS
/dev/sda3 24,782,848 444,164,461 419,381,614 7 HPFS/NTFS
[COLOR=red]**/dev/sda4 444,166,142 625,141,759 180,975,618 5 Extended**[/COLOR]
**[COLOR=seagreen]__/dev/sda5 507,791,360 620,259,327 112,467,968 83 Linux[/COLOR]**
**[COLOR=seagreen]__/dev/sda6 620,261,376 625,141,759 4,880,384 82 Linux swap / Solaris[/COLOR]**
[COLOR=royalblue]**__/dev/sda7 444,166,144 505,075,711 60,909,568 83 Linux**[/COLOR]
**[COLOR=royalblue]__/dev/sda8 505,077,760 507,783,167 2,705,408 82 Linux swap / Solaris[/COLOR]**

```
 
The install shrank your 'D:' drive (the third partition on the first drive, called /dev/sda3 in Linux) twice (once for each install).
 
It created an 'extended' partiton (/dev/sda4 - in Red) and two logical partitions in the first install attempt (/dev/sda5 & /dev/sda6 - in green). The are incomplete.
 
It created two more logical partitions in the second install (/dev/sda7 & /dev/sda7 in blue). These appear to be complete.
 
Ubuntu does not start because the 1/2 installed first set are showing in the grub (**GR**and **U**nified **B**ooot loader) menu, not the final and (apparently) complete 2nd set.
 
We have three ways of correcting this situation:
 
1) Completely remove Ubuntu and give all the space back to windows.
2) Completely remove Ubuntu and do fresh install where YOU drive it, using only the partitons we will help you create manually.
3) We can rescue this install by removing /dev/sda5 &/dev/sda6, shrink /dev/sda4, Reinstall grub from the LiveCD, and finally from windows 'disk manager' take bake the space of the 1st install.
 
Option 2 & 3 requires you run gparted (**G**nome **PART**ition **ED**itor) from the live CD. This is a great learning opportunity - but the decision is yours.
 
Ponder it and let us know.
 
 
***The Hedge***
 
:KS

---

### Post by Reier on 2011-03-21
Wow thanks!

What I would like is 80 GB Ubuntu (though if worst comes to worst I can use the 120 GB I goofed on, though it is not ideal), and the rest Windows 7. So which ever option lets me do that with the least trouble. ;p I suppose #2 (or 3??)
Not very good with scripting/code etc stuff but I'm sure I can do it with help.

---

### Post by oldfred on 2011-03-21
I have to agree with The Hedge. And I think #2 would be the best choice. With most systems you can install in about an hour. 

I prefer to keep smaller system partitions. That is the part that can get corrupted and then you can more easily reinstall. You still have to do backups of your data. I also do not like to write into another system unless I have to for repairs. So I create a shared NTFS partition for read/write but only mount windows system as read only (if at all).

Every user ends up with what is best for them, but that even changes. But this is my suggestion:

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

I like to use gparted to set up partitions in advance. You also then can delete the existing partitions. Use manual install and specify which partition is / (root), swap & /home.
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

The liveCD will mount one or both swap partitions. Right click on the partition and swap off to let you edit all the partitions in the extended partition.

---

### Post by Reier on 2011-03-21
So uh....what do I do...?

---

### Post by Dutch70 on 2011-03-21
[COLOR="Red"]**You can skip this & follow Hedge's guide, since he is back. I'll leave it here for the record.*[/COLOR]

First, go to System>Admin>Gparted, to open the Gnome Partition Editor. You'll find the tool to take a screenshot with under Applications>Accessories. Open it also, tick "select area of screen to grab" & "take screenshot". This will leave you with a "+" sign on the screen, use that to select the area to take a pic of Gparted & save it to your desktop.

*This is not really necessary, but will make it easier if I/we have a visual of your partitions.* 

In your next post, click the paper clip in the toolbar. Click "Browse" in the window it brings up. Navigate to your desktop where the pic of Gparted is, select it & click open. Then click "Upload", wait for it to finish & close the window. You won't see the pic in your post, but it's there. Preview or Submit the post.

Once we have this, we'll proceed to delete your Ubuntu partitions and recreate them correctly. One other thing we need to know, is how much physical RAM you have on your computer & if you intend to add any in the near future.

I've included an example pic of what you want your partitions to look like when your finished. My only regret with this hdd, is only giving Ubuntu 100GB when I first started with it. Now I have 200+ GB in vista that I never use. Now that's wasted GB's.:)

Dutch

---

### Post by Hedgehog1 on 2011-03-21
Boy did I spend a lot of time running in my Hedgie wheel today (translation: very long day at the office).

> **Reier said:**
> So uh....what do I do...?

Excellent Question Reier!

Lets take option 2 then - a complete uninstall of Ubuntu, recover space on your disk for windows, and finally a controlled re-install of Ubuntu.

To start with, we need to make your computer boot directly to windows BEFORE we remove Ubuntu and the GRUB boot loader.

[SIZE="3"]We nerds call this the 'FIXMBR step'[/SIZE]

To make a Windows 7 / Vista emergency repair disk (in case you don't already have one made):
[IMG]http://img641.imageshack.us/img641/9550/small50createrepairdisk.png[/IMG]

Boot from the windows 7 / Vista  emergency repair disk, do the following:
[IMG]http://img10.imageshack.us/img10/5826/small51runningrecoveryd.png[/IMG]
[IMG]http://img856.imageshack.us/img856/3690/small52selectingwindows.png[/IMG]
[IMG]http://img826.imageshack.us/img826/3484/small53commandprompt.png[/IMG]
[IMG]http://img215.imageshack.us/img215/9547/small54bootrec.png[/IMG]

At the Windows command line interface, type: **bootrec /FixMbr**

See - there was a 'fixmbr' in there, eventually...

---

### Post by Hedgehog1 on 2011-03-21
Once your computer is booting directly into windows, the next step is to reclaim some of the disk space.

I think you wanted to leave 80 gigs to Ubuntu.  You can run Ubuntu with much less, so I will use the calculations for a total of 40 gigs, and you can adjust that larger if you want.

Once in Windows, the tool for managing disks and partitions on disk is called the Windows Disk Manager. 

Here is where you'll find it:

[IMG]http://img718.imageshack.us/img718/7687/small55diskmanagement.png[/IMG]


Now these screen shots are for a person who only installed Ubuntu once.  Since you installed it twice, you will have 5 partitions to remove instead of 3. ***Not a biggie.***

Here is your partition layout:

```

/dev/sda1 2,048 24,578,047 24,576,000 27 Hidden HPFS/NTFS
/dev/sda2 * 24,578,048 24,782,847 204,800 7 HPFS/NTFS
/dev/sda3 24,782,848 444,164,461 419,381,614 7 HPFS/NTFS
[COLOR=red]**/dev/sda4 444,166,142 625,141,759 180,975,618 5 Extended**[/COLOR]
**[COLOR=seagreen]__/dev/sda5 507,791,360 620,259,327 112,467,968 83 Linux[/COLOR]**
**[COLOR=seagreen]__/dev/sda6 620,261,376 625,141,759 4,880,384 82 Linux swap / Solaris[/COLOR]**
[COLOR=royalblue]**__/dev/sda7 444,166,144 505,075,711 60,909,568 83 Linux**[/COLOR]
**[COLOR=royalblue]__/dev/sda8 505,077,760 507,783,167 2,705,408 82 Linux swap / Solaris[/COLOR]**

```

We will start deleting paritions from the right hand side - and if a partition says 'NTFS'  **Do Not Delete it.**

So delete the first two:

```
[COLOR=royalblue]**__/dev/sda7 444,166,144 505,075,711 60,909,568 83 Linux**[/COLOR]
**[COLOR=royalblue]__/dev/sda8 505,077,760 507,783,167 2,705,408 82 Linux swap / Solaris[/COLOR]**

```

Remove Swap Partiton

[IMG]http://img97.imageshack.us/img97/4905/small56deleteswap.png[/IMG]
[IMG]http://img231.imageshack.us/img231/2992/small57freespace.png[/IMG]

Remove Ubuntu Partition

[IMG]http://img96.imageshack.us/img96/5986/small58deleteubuntu.png[/IMG]

Now delete the extra set (Repeating the above steps):
```

**[COLOR=seagreen]__/dev/sda5 507,791,360 620,259,327 112,467,968 83 Linux[/COLOR]**
**[COLOR=seagreen]__/dev/sda6 620,261,376 625,141,759 4,880,384 82 Linux swap / Solaris[/COLOR]**

```


Remove extended Partition (yeah, it says 'free space', but its really a partition)

```
[COLOR=red]**/dev/sda4 444,166,142 625,141,759 180,975,618 5 Extended**[/COLOR]

```

[IMG]http://img848.imageshack.us/img848/8053/small59deleteextended.png[/IMG]

Deleting stuff is easy.  Just be careful...

---

### Post by Hedgehog1 on 2011-03-21
> **Dutch70 said:**
> [COLOR="Red"]**You can skip this & follow Hedge's guide, since he is back. I'll leave it here for the record.*[/COLOR]


Thanks Dutch70 - I appreciate you filling in.   You are ALWAYS welcome to do so.  Would have been on line sooner, but it really was a very, VERY long day at the keyboard...

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-03-21
So, you now have this **GAPING HOLE** of empty, unused space on your hard drive.

*It is the kind of thing that brings a Hedgehog to tears, really.*

So now we are going to reclaim all but 40 gigs of the disk space for windows.  That last 40 gigs is for Ubuntu, and we will prepare it as part of the Ubuntu install.

OK - getting your space back is really easy:

[IMG]http://img3.imageshack.us/img3/7880/small61extendwin7volume.png[/IMG]

Please 'extend' the space leaving about 40 gigs 'unallocated'.

Cool huh?  The Windows Disk Manager is a lot more powerful than it used to be.  Gparted does more, but this tool has been (mostly) getting better each windows release.

Next step (when you feel brave enough) is a controlled install of Ubuntu.

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-03-22
To install Ubuntu, we will once again boot off the LiveCD/LiveUSB.

In addition to being an installer, the LiveCD/LiveUSB is a complete Ubuntu system.  Folks who have lost a hard drive can still boot from the LiveCD/LiveUSB and surf the web.  But I digress...

Because the LiveCD/LiveUSB is a complete Ubuntu system, we can run the tools to manage a computer from it, as well.  This is a powerful thing!

When you first boot, you get this screen:

[IMG]http://img858.imageshack.us/img858/9995/small06tryubuntu.png[/IMG]

Select the 'TRY' option and you get:

[IMG]http://img202.imageshack.us/img202/5771/small07trygui.png[/IMG]

I think have have been here before, right?

This time, we are going to run gparted (**G**nome **PART**iton **M**anager) from the LiveCD/LiveUSB.

To run it, menu to System >> Administration >> Gparted partition editor.

When you bring this up, you will see a screen like the one that Dutch70 had in his post.  That was his gparted screen shot.  Here is mine:

[IMG]http://img858.imageshack.us/img858/8396/marcgparted.png[/IMG]

You will see a pattern in all of these - an extended partition with logical partitions inside it.

We have to do this because if we want want to share a disk with Windows, the partition style must be the Windows style.

Windows MBR style only allows 4 primary partitions. Here is an example from an all-windows HP PC:

[IMG]http://img859.imageshack.us/img859/8806/hp4partitions02.png[/IMG]

To get more, you have to make an extended partition to hold them.  No Biggie, we just make one and put our Ubuntu partitions in that one.

---

### Post by Hedgehog1 on 2011-03-22
After the double install of Ubuntu, you had this:

```
/dev/sda1 2,048 24,578,047 24,576,000 27 Hidden HPFS/NTFS
/dev/sda2 * 24,578,048 24,782,847 204,800 7 HPFS/NTFS
/dev/sda3 24,782,848 444,164,461 419,381,614 7 HPFS/NTFS
[COLOR=red]**/dev/sda4 444,166,142 625,141,759 180,975,618 5 Extended**[/COLOR]
**[COLOR=seagreen]__/dev/sda5 507,791,360 620,259,327 112,467,968 83 Linux[/COLOR]**
**[COLOR=seagreen]__/dev/sda6 620,261,376 625,141,759 4,880,384 82 Linux swap / Solaris[/COLOR]**
[COLOR=royalblue]**__/dev/sda7 444,166,144 505,075,711 60,909,568 83 Linux**[/COLOR]
**[COLOR=royalblue]__/dev/sda8 505,077,760 507,783,167 2,705,408 82 Linux swap / Solaris[/COLOR]**

```

What we really wanted is this:

```
/dev/sda1 2,048 24,578,047 24,576,000 27 Hidden HPFS/NTFS
/dev/sda2 * 24,578,048 24,782,847 204,800 7 HPFS/NTFS
/dev/sda3 24,782,848 444,164,461 419,381,614 7 HPFS/NTFS
[COLOR=red]**/dev/sda4 444,166,142 625,141,759 180,975,618 5 Extended**[/COLOR]
**[COLOR=royalblue]__/dev/sda5 507,791,360 620,259,327 112,467,968 83 Linux[/COLOR]**
**[COLOR=royalblue]__/dev/sda6 620,261,376 625,141,759 4,880,384 82 Linux swap / Solaris[/COLOR]**

```

So, that is what we will build using gparted.

The following picture were using **/dev/sda3** as the extended partition.  You will be working in **/dev/sda4**, so you kinda need to translate the pictures a little.

Right Click, on the empty area (after /dev/sda3, in your case), select new and create extended sda4. Press click check mark button at the top to make the change real.

[IMG]http://img69.imageshack.us/img69/5967/hp4partitions05.png[/IMG]

Create your sda5 Ubuntu partition, leaving a little room for swap space after it.  Swap space should be about the size of your RAM, plus a tiny bit more.  All the other space can be this partition.

Format this ext4 - and press that check mark button again:

[IMG]http://img863.imageshack.us/img863/4839/hp4partitions06.png[/IMG]

Create sda6 and make it swap space:

[IMG]http://img855.imageshack.us/img855/3999/hp4partitions07.png[/IMG]

Press the check mark button again.

Congrads! You have prepped the Ubuntu partitions.

:p

You can exit gparted now.

---

### Post by Hedgehog1 on 2011-03-22
Install time!

No Worries - you have it covered this time.

Some important difference between this install the first one are:

1) You changed the size of your Windows partitions using windows tools.  Whenever possible, use Windows Disk Manager for Windows partitions, and gparted for Linux partitions.  Last time you installed, gparted did the shrink of the NTFS partition for you (in the background).  

2) This time you have created the partitions you want, and are in complete control of the install.

So, double click the 'Install Ubuntu 10.10', and lets get rolling.

You will eventually get to this screen:

[IMG]http://img705.imageshack.us/img705/2588/hp4partitions09.png[/IMG]

You want to specify your partitions manually.  This allows you a lot of control, even for doing fancy stuff at install time.

Once again - these pictures show **/dev/sda3** as the extended partition.  Yours is **/dev/sda4**.  

[IMG]http://img849.imageshack.us/img849/9937/hp4partitions10.png[/IMG]

I am hoping that things are not completely unfamiliar to you as you see this screen for the first time.

You see your **/dev/sda5** & **/dev/sda6** partitons, right where you left them.

[SIZE="3"]***IMPORTANT NOTE: DO NOT PRESS THE "New Partition Map" BUTTON.  It will wipe the complete disk.  It should not be available for you, but just in case.***[/SIZE]

Yeah - I think I made the warning 'big' enough.

---

### Post by Dutch70 on 2011-03-22
Reier, you can chime in at any time here. :)

 I don't want to overwhelm you, all this is really quite simple. Although it may not seem like it at first, you'll be surprised at how simple it was when you're finished. 

*I think when Hedge said to leave 40GB unallocated, he meant to say 80GB since that is what you wanted for Ubuntu.* 

It is only necessary to have the 2 partitions, "/" (root) & Swap. However, its a really good idea to have 3. The extra one would be /home, as you can see in both mine & Hedge's pics of Gparted. It's no big deal, just one extra partition. 

 In order to do that, you'll want to create 3 logical partitions inside of the extended. 

sda5 for "/" = 15GB (similar to program files in windows)
sda6 for swap = equal to the size of your RAM, plus a few MB if you wish, (similar to pagefile)
sda7 for /home = the remainder of your 80GB partition. (similar to documents & settings)

Basically you would just need to shrink the largest partition that created in the other step down to 15GB & select the new unallocated space to create your /home.

---

### Post by Hedgehog1 on 2011-03-22
**EDIT:** *Reier, please take a look at post#21 on this thread.  It has to do with  Dutch70's suggestion.*

We will add some extra data to **sda5** and **sda6**.  With **sda5** highlighted, press the [CHANGE] button:

[IMG]http://img861.imageshack.us/img861/5274/hp4partitions11.png[/IMG]

These settings prepare the partition to be ext4, & '/'

'/' is said out load as: 'root'.  This is where the Linux files system begins.

Repeat the steps for the swap area (This usually set itself up OK):

[IMG]http://img26.imageshack.us/img26/4934/hp4partitions12.png[/IMG]

Please make sure the 'Device for boot loader installation' is set to **/dev/sda**, not /dev/sda1 or /dev/sda5 or any other number, but **/dev/sda**.

You are ready to install.  Press [Install Now].

[IMG]http://img857.imageshack.us/img857/6342/hp4partitions13.png[/IMG] 


This is all much easier with pictures.


***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-03-22
> **Dutch70 said:**
> ... 

 In order to do that, you'll want to create 3 logical partitions inside of the extended. 

sda5 for '/' = 15GB (similar to program files in windows)
sda6 for swap = equal to the size of your RAM, plus a few MB if you wish, (similar to pagefile)
sda7 for '/home' = the remainder of your 80GB partition. (similar to documents & settings)

Reier,

If you look at Dutch70's gparted screen shot, or at mine, you will see we both have a separate '/home' partition. 

My '/home' partition is 750 gigs.  And like Dutch70, it is also where "I keep all my stuff".

It is an option worth considering.

It would change your partition layout to:

[B]/dev/sda4 - extended - 80 gig
__/dev/sda5 - 15 gig ext4, '/', Ubuntu system
__/dev/sda6 - Swap (ram size plus a bit - *GUESSING* 2.1 gig)
__/dev/sda7 - 63.9 gig ext4 '/home' - where you keep your 'stuff' separate from the OS 'stuff'.[/B]

You are welcome to do so.  It only adds a few extra steps for the third partition:

* Create 3 partitions in gparted (instead of 2)
* Set /dev/sda7 to be '/home' in the allocation step.


***The Hedge***

:KS

p.s. Whew - I am tired after all that.  Time for a quick Hedgie *'power nap'*.

---

### Post by Reier on 2011-03-22
Wow you guys are really helpful. I was in bed this whole time ;p
I'll try it later and give you a report. Thanks so far, this is great.

---

### Post by Hedgehog1 on 2011-03-26
Here is a set of screen shots showing the install with the third '/home' partition:


In gparted, create 3 partitions:

1) ext4 '/'
2) Linux swap
3) ext4 '/home'

[IMG]http://img215.imageshack.us/img215/8985/01gparted.png[/IMG]
 
Once your three partitions are laid out, you will start the install and eventually get to this screen:

[IMG]http://img829.imageshack.us/img829/4196/02specifypartitons.png[/IMG]

Here is what the allocation screen looks like:

[IMG]http://img27.imageshack.us/img27/6770/03allocdrivespace1.png[/IMG]

Remeber, you need to translate the sda5=sdb1, sda6=sdb2 & sda7=sdb3. Now you will 'map' the three partitions on /dev/sdb.

First, make /dev/sdb1 your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

Next, set up the swap partition.  This usually sets itself up just fine, but double check it.

[IMG]http://img263.imageshack.us/img263/7656/06allocdrivespace4.png[/IMG]

---

### Post by Hedgehog1 on 2011-03-26
The last partition to setup is the '/home' one:

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

This brings you to here:

[IMG]http://img34.imageshack.us/img34/6017/08allocdrivespace6.png[/IMG]

[SIZE="4"]**Please install the Boot Loader on /dev/sda !**[/SIZE]

Press "Install Now" and you are on your way:

[IMG]http://img855.imageshack.us/img855/7153/09installbegin.png[/IMG]

Here is a view of the final layout of the partitions:

[IMG]http://img853.imageshack.us/img853/841/10diskutility2.png[/IMG]


***The Hedge***

:KS

---

### Post by Reier on 2011-03-26
[delete]

---

### Post by Hedgehog1 on 2011-03-26
Hey - with photos like that you should be a wedding photographer.

I think the photo showed:

/dev/sda5 Make this your: '/' (root) (Format as ext4)
/dev/sda6 Make this your: linux-swap

Install the Boot Loader on /dev/sda  (the default)

Once that is done, you are good to go.

***The Hedge***

:KS

p.s. Sorry for the information overload.  It is an engineer thing - we cannot help ourselves some days...

---

### Post by oldfred on 2011-03-26
You are at The Hedge's posts 23 on where you choose sda5 and using combo boxes tell it that it should be / (root) and ext4. 

If you turn flash off it works better. LiveCD will let you do screenshots. If partitioning is done then you can run sudo fdisk -lu to show partitions. 
Then restarting installer with manual install goes quick as partitions are defined and you get to where  your are now very quickly. 

Then choose /, it finds swap automatically. You specify to install grub2's boot loader to sda (the drive) not sda1 or sda2 (partitions).

---

### Post by Reier on 2011-03-26
OK, hold on. One more thing. When I press install it asks me:
> Do you want to return to the partitioner?
----------
The file system on /dev/sda5 assigned to / has not been marked for formatting. Directories containing system files (blahblah) the exist under mountpoint yaddayadda will be deleted during install.

This major or am I overreacting? Just to be safe. I have the tendency to screw things up w/o excruciatingly detailed info on some things like this. ;p

---

### Post by Hedgehog1 on 2011-03-26
> **Reier said:**
> OK, hold on. One more thing. When I press install it asks me:


This major or am I overreacting? Just to be safe.

For a new install, it is OK to have the installer format the drive again.   Go back and mark it to format (and keep it happy).


***The Hedge***

:KS

---

### Post by Reier on 2011-03-26
Well, I did everything you said. I really do appreciate all the time you guys have put into this.
Unfortunately it banged out the same dang error as last time.

I did get a (lame) photo this time though.

[img]http://localhostr.com/file/7iCiLu1/Untitled.png[/img]

It says

> [ 3904.{number}] end_request: I/O error, dev sdb, sector {number}

Should I turn it off manually or what?

---

### Post by Hedgehog1 on 2011-03-26
yeah, you can shut it off manually.

This is not how we wanted this post to go... Not at all...

***The Hedge***

---

### Post by Hedgehog1 on 2011-03-26
Reier,

if you want to keep going, we can pick up with a fresh look at your hard drives as they sit now:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

***The Hedge***

:KS

---

### Post by Reier on 2011-03-26
Hold on.
On the dual boot thingy when you start the computer, there is no longer the Ubuntu 10.10 option at the bottom. The top one (Ubuntu with Linux or something) is still there, however. It *seems* to work. As in it boots up fine with no errors at least and I can do stuff with it. I assume this is good? Was the installation successful after all, then?

---

### Post by Hedgehog1 on 2011-03-26
[SIZE="4"]Dude!!![/SIZE]

I think you have a working install!


***The 'excited' Hedge***

:KS

---

### Post by Reier on 2011-03-26
Sweeeeet
So why'd it do the error thingy and not add the 'Ubuntu 10.10' option on the dual boot screen then?

---

### Post by Hedgehog1 on 2011-03-26
I cannot say at this time...  I have not seen that before to have a chance to track it down on my own systems...

Let's just blame it on 'marketing' until we know for sure.

***The Hedge***

:KS

---

### Post by Reier on 2011-03-26
K then.
Thanks a TON, bro. You've helped out loads.

---

### Post by Dutch70 on 2011-03-26
Yay \o/  LOL

I've been following this thread so long I feel like doin a l'il jiggy myself! \\:D/

---

### Post by Hedgehog1 on 2011-03-26
> **Reier said:**
> K then.
Thanks a TON, bro. You've helped out loads.

You are welcome.  I look forward to NORMAL Ubuntu questions from you in the future... :D

***The Hedge***

:KS

p.s. I would dance like Dutch70, but it is just to much trouble to move all the furniture first...

---

### Post by reqqq on 2011-03-26
firstly is my first post in here & have to say many thanks to this perfect ubuntu forum-i am trying to read first and then post something .after a year of reading i did something so stupid as i see now and i want your knowledge on something 
i wanted to expand my disc space using an sd card and did this 

sudo mv /home/name_of_home_folder  home/name_of_home_folder_bk 
sudo mkdir /home/name_of_home_folder 
sudo mount /dev/sdXX(sd card) /home/name_of_home_folder 

after this i cannot boot says cannot boot ,nautilus cant find home folder etc &more
after doing alt-ctrl-f1 and doing login i can find my old home folder with all inside 
the point is how i can change to my old home folder -have to find the solution  in order not to do format again :) i use ubuntu desktop edition on an acer aspire one netbook with ssd 8gb -
please help

---

### Post by oldfred on 2011-03-26
@ Reier
Were you trying to boot the install you deleted. Then it would give lots of errors. do this to remove it from the menu.
sudo update-grub

@reqqq
Please start a new thread as your issue is a lot different than this thread. Then you can have a title that will draw those that know about your issue. I think you cannot move home that way but have to edit fstab.

---

