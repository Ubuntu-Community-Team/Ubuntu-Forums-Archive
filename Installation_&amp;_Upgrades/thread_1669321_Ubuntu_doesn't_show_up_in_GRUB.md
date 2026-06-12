---
title: "Ubuntu doesn't show up in GRUB"
date: 2011-01-14
forum: Installation &amp; Upgrades
---

### Post by BigMoose on 2011-01-14
thanks for the quick response. Essentially I want a working copy of ubuntu. I am new to it so bare withme.

 I installed it from a cd and it wouldn't work. (froze in the process). I then tried to install it through windows wubi and that didn't work (wouldnt boot) since I was unaware it was a known issue and thought it was me doing something wrong I uninstalled it,reformatted the hard drive and tried to install via a cd again this time it fully iinstalled but when I rebooted it tells me unable to mount drives and a shell will be shown.

in the end I have no files on ubuntu so I would like to clean up all reminance of the previous installs and be able to use a working install. If you can tell me what I eed to do I would greatly appreciate it especially since I have been installing  and reistalling for the better part of 8 hours.Yexcuse the post sloppiness using my phone:))

---

### Post by bcbc on 2011-01-14
@BigMoose,
it sounds like you might have a problem with 10.10. In any case, your issue installing isn't really wubi-specific. Why don't you try 10.04.1 instead and do a normal install, not Wubi? If you have problems with this or really want 10.10, I suggest you create a new thread, detail your computer brand/model specs, graphics card etc.  and you'll get lots of help. Hope that helps.

---

### Post by BigMoose on 2011-01-15
I think it installed correctly since it shows up in the boot menu, the issue is when I select the ubuntu OS, it sends me to the GRUB prompt. In any case I am going to reformat those drives that you mentioned having files and repost the results file before i install to see if that things look normal before i attempt to re-install.

---

### Post by candtalan on 2011-01-15
> **BigMoose said:**
> I think it installed correctly since it shows up in the boot menu, the issue is when I select the ubuntu OS, it sends me to the GRUB prompt. In any case I am going to reformat those drives that you mentioned having files and repost the results file before i install to see if that things look normal before i attempt to re-install.

Maybe a bit late and also perhaps obvious, but - you did run as a live CD to start with, to verify that your hardware plays nice with the version of Ubuntu? 

Also, the CD itself, and how it is read in the target drive, is a potentially important issue. When booting from the CD, at an early stage, press a key when symbols appear at the bottom of the display. Then a menu appears which includes 'Test the CD for errors'. So even if the CD drive is sticking or whatever, the test will hopefully reveal any problem.
hth

---

### Post by BigMoose on 2011-01-16
> **candtalan said:**
> Maybe a bit late and also perhaps obvious, but - you did run as a live CD to start with, to verify that your hardware plays nice with the version of Ubuntu? 

Also, the CD itself, and how it is read in the target drive, is a potentially important issue. When booting from the CD, at an early stage, press a key when symbols appear at the bottom of the display. Then a menu appears which includes 'Test the CD for errors'. So even if the CD drive is sticking or whatever, the test will hopefully reveal any problem.
hth

Thanks cand, your not too late still working on it. Yes I did boot from a CD after the fact though (which is how I get the results text file) and it worked fine. I was able to surf the web and open applications. 

Looks like I might have screwed things up even now as now my machine is no longer booting for windows (I get a grub rescue prompt). I am trying to boot from an ubuntu cd to try and change the boot loader as I have seen in other threads, I fear I am digging my self in a while just to use ubuntu.

Edit: I was able to boot into windows (after reading this thread [http://ohioloco.ubuntuforums.org/showthread.php?t=1391875](http://ohioloco.ubuntuforums.org/showthread.php?t=1391875) more specifically post #2). I am glad I have been putting ubuntu on a seperate hardrive than my windows or else I would have been in nomads land. I am not sure if this is it, but I think the fact that windows is on drive sdc, and I tried to install ubuntu on sda using a cd and then tried to install wubi and ubuntu on sdb I am having all these problems. I will try a few more things and repost my results file if I am not able to figure it out. Thanks up to now for all the help.

---

### Post by candtalan on 2011-01-16
> **BigMoose said:**
> Thanks cand, your not too late still working on it. Yes I did boot from a CD after the fact though (which is how I get the results text file) and it worked fine. I was able to surf the web and open applications. 

Looks like I might have screwed things up even now as now my machine is no longer booting for windows (I get a grub rescue prompt). I am trying to boot from an ubuntu cd to try and change the boot loader as I have seen in other threads, I fear I am digging my self in a while just to use ubuntu.

Edit: I was able to boot into windows (after reading this thread [http://ohioloco.ubuntuforums.org/showthread.php?t=1391875](http://ohioloco.ubuntuforums.org/showthread.php?t=1391875) more specifically post #2). I am glad I have been putting ubuntu on a seperate hardrive than my windows or else I would have been in nomads land. I am not sure if this is it, but I think the fact that windows is on drive sdc, and I tried to install ubuntu on sda using a cd and then tried to install wubi and ubuntu on sdb I am having all these problems. With you using multiple partitions, it might be much easier to install and manage if you installed Ubuntu non wubi, and used the advanced Ubuntu installer option to manually nominate the target partitions for Ubuntu  /  and Ubuntu swap.>  I will try a few more things and repost my results file if I am not able to figure it out. Thanks up to now for all the help.
I believe wubi can get very hard to understand and manage if you choose an unusual drive to install into. (If your priority is to clean up your Windows consider using a Windows XP installation  CD to fixmbr, there are other ways also).

---

### Post by BigMoose on 2011-01-16
Thanks C my and, I think I will go ahead and try to fix mbr using the windows CD and reformat those other drives. I will then boot ubuntu 10.10 from a CD and get the results file and post it before I continue wasting any more time.

Update: I can't seem to find my windows cd, what other ways are there to fix fixmbr

Update #1: Ok I have uninstalled wubi and gone into ubuntu CD boot and ran the bookinfoscript and got the attached results. It appears as if I have been able to clean all traces of ubuntu from my computer and me mbr appears to be fixed. (Booted directly into windows without any issues or a boot menu).

It also appears as if I do not have GRUB on the computer.

I am thinking to install Ubuntu 10.10 into a CD and see how it works, should I proceed?

---

### Post by BigMoose on 2011-01-17
After installing Ubuntu 10.10 from a CD I have the attached results file. When I boot, it goes straight into windows without an option to go into Ubuntu.

Is there something that needs to be changed? 

If not should I open a seperate thread as suggested before(I don't want to further spam this thread). Thanks.

---

### Post by Rubi1200 on 2011-01-17
Which drive is set in BIOS to boot first?

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdi: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  According to the info in the boot sector, sdi has 0 
                       sectors.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   204,796,619   204,796,557   7 HPFS/NTFS
/dev/sda2         204,796,620 1,953,520,064 1,748,723,445   f W95 Ext d (LBA)
/dev/sda5         204,796,683 1,953,520,064 1,748,723,382   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048    74,864,639    74,862,592  83 Linux
/dev/sdb2          74,866,686    78,163,967     3,297,282   5 Extended
/dev/sdb5          74,866,688    78,163,967     3,297,280  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   160,826,714   160,826,652   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        B29C32FA9C32B8A5                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        0E64DFBE64DFA6AD                       ntfs       900 GB Driv                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        062c4444-ecb9-48a3-a516-a42993da7d85   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        51547e32-ad46-4e74-841c-776c479b3741   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        9690E6B790E69D4D                       ntfs       80G Storage                   
/dev/sdc: PTTYPE="dos" 
/dev/sdi         387D-2966                              vfat       PHONE                         
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found
error: /dev/sdh: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 062c4444-ecb9-48a3-a516-a42993da7d85
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 062c4444-ecb9-48a3-a516-a42993da7d85
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 062c4444-ecb9-48a3-a516-a42993da7d85
    linux    /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=062c4444-ecb9-48a3-a516-a42993da7d85 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 062c4444-ecb9-48a3-a516-a42993da7d85
    echo    'Loading Linux 2.6.35-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-24-generic-pae root=UUID=062c4444-ecb9-48a3-a516-a42993da7d85 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 062c4444-ecb9-48a3-a516-a42993da7d85
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 062c4444-ecb9-48a3-a516-a42993da7d85
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdc1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd2,msdos1)'
    search --no-floppy --fs-uuid --set b29c32fa9c32b8a5
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=062c4444-ecb9-48a3-a516-a42993da7d85 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=51547e32-ad46-4e74-841c-776c479b3741 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


   4.4GB: boot/grub/core.img
  17.6GB: boot/grub/grub.cfg
    .8GB: boot/initrd.img-2.6.35-24-generic-pae
   4.4GB: boot/vmlinuz-2.6.35-24-generic-pae
    .8GB: initrd.img
   4.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  ee 8f 19 a0 a7 91 03 84  a5 45 f1 a6 8a 9c 01 a3  |.........E......|
00000010  ce 01 95 56 25 88 e3 f8  19 2b 52 af 9b dc 27 0a  |...V%....+R...'.|
00000020  6b f2 ee ef 9a b1 b9 66  55 da 18 2a 2f 55 a5 e3  |k......fU..*/U..|
00000030  d6 c1 44 07 bc b7 7e a6  8c 07 fc 11 fa a6 7b 89  |..D...~.......{.|
00000040  00 c5 0b 82 08 06 97 52  e2 ff 0f b9 aa 84 81 20  |.......R....... |
00000050  7a 99 5f fc 3d 57 e4 2a  c6 5d c1 85 c2 bd 40 d1  |z._.=W.*.]....@.|
00000060  69 e1 9e 19 42 3f 41 a7  8d f4 fa 7b bc 0c df fb  |i...B?A....{....|
00000070  fd 77 13 e8 82 34 55 c6  34 ac 84 67 ce 60 87 42  |.w...4U.4..g.`.B|
00000080  65 57 3e 22 5b 00 c7 48  55 26 5c ad 34 01 3e 8d  |eW>"[..HU&\.4.>.|
00000090  30 11 8a 82 9e 3e 9e f7  84 69 9a 1f b9 de c1 0b  |0....>...i......|
000000a0  4f b8 59 25 06 8b fc 84  67 b8 b8 9e 03 4e 02 c3  |O.Y%....g....N..|
000000b0  18 4e e8 2f 19 e1 94 3a  0e 00 20 64 70 67 fb 41  |.N./...:.. dpg.A|
000000c0  2a 03 4e 02 d8 cf 46 c0  88 17 8e 59 46 34 f1 20  |*.N...F....YF4. |
000000d0  53 d5 16 ad 6d 59 ad 44  35 0c a0 82 0b 19 45 42  |S...mY.D5.....EB|
000000e0  76 c3 41 30 cf c2 23 50  38 69 1f 39 4e c4 06 8e  |v.A0..#P8i.9N...|
000000f0  8c f3 5e 6a c0 d4 2a 89  06 32 02 ec 07 8c ff 2e  |..^j..*..2......|
00000100  0b 75 54 ac 41 5d a2 05  6a 03 64 05 64 85 e3 c0  |.uT.A]..j.d.d...|
00000110  68 7f e0 5c 4c 14 ce 5d  96 02 c4 b8 1a 1f f1 81  |h..\L..]........|
00000120  78 f0 3c 40 6d 58 28 16  ba c8 dc 2a 3a 70 67 97  |x.<@mX(....*:pg.|
00000130  32 36 5d 39 68 a4 b8 34  21 f8 28 3e 44 5e 08 4a  |26]9h..4!.(>D^.J|
00000140  23 56 ac d1 49 93 89 a6  aa e3 65 05 47 cb 94 a7  |#V..I.....e.G...|
00000150  0d b0 a0 cf 95 fb 78 d2  66 78 4a 3e 05 02 a9 de  |......x.fxJ>....|
00000160  ea eb 95 38 46 d9 72 95  fd cf e8 ed 9d 89 9b 92  |...8F.r.........|
00000170  16 99 12 80 f8 30 e0 7e  02 f9 24 f0 17 da 17 84  |.....0.~..$.....|
00000180  2c 5c 40 9d 50 8d 92 71  21 32 19 52 93 3c 66 08  |,\@.P..q!2.R.<f.|
00000190  65 dd 98 a7 2d 9e df e5  d9 d6 ae c0 b0 48 53 19  |e...-........HS.|
000001a0  89 95 ad 56 ad f0 60 3e  c1 e7 13 66 73 0e 8f a4  |...V..`>...fs...|
000001b0  4d 41 87 03 f0 ee a3 a2  37 82 e3 c1 4c 0f 00 fe  |MA......7...L...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 50 32 00 00 00  |...........P2...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg sdh 
```

---

### Post by CharlesA on 2011-01-17
I've moved some posts from the Wubimega thread, as it doesn't really pertain to Wubi, more to Ubuntu in general.

I would start with running the bootinfo script in Rubi1200's sig and go from there. That'll answer some questions.

---

### Post by BigMoose on 2011-01-17
Let me state my current status regarding this issue. I have attached the latest result of the boot info script since I wasn't aware my posts were  moved and didn't know why I wasn't getting replies. :)

Computer Specs:
AMD 64 Phantom 555 Processor
4BG of Memory
sda: 40GB WD Harddrive (IDE - old one from a previous computer)
sdb: 80GB Hitachi IDE drive
sdc: 1TB Samsung SATA drive (100GB partitioned for windows and the rest is partitioned for storage)

My windows wasn't booting so I ran some commands in other posts for LILO to boot it which is why you see that entry in the results file.

Once I was in windows I used WUBI to install 10.4 onto the 80GB since installing UBUNTU 10.10 with a CD wasn't booting nor adding an entry to my boot menu.

So now I get a boot menu and when I choose UBUNTU I get the following errors:

"error: file not found
 error: you need to load the kernel first
          Failed to boot both default and fall back entries
Press any key to continue..."

Every time I press a key it displays the same message.

I am able to use a CD to boot in LIVE CD (I think thats what its called). I looked into the UBUNTU HD and look through some directories and the /boot/grub folder is empty if that helps debug).

All help is appreciated.

---

### Post by bcbc on 2011-01-17
So now you have installed Wubi again. But only the windows portion of the install has occurred. The Ubuntu install has not yet completed.

> "error: file not found
error: you need to load the kernel first
Failed to boot both default and fall back entries
Press any key to continue..."This isn't an error I am familiar with. But you should find a file /ubuntu/install/boot/grub/grub.cfg - that's the one that's supposed to run to complete the install. However, I don't think you get that far. 

I really don't recommend using Wubi in this case though - you have a dedicated drive and installing with Wubi is totally unnecessary. You just need to make sure when you install Ubuntu 10.04.1 that you tell it to place the grub2 bootloader on /dev/sda.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Lilo is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

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
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sdc1/Wubi: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   204,796,619   204,796,557   7 HPFS/NTFS
/dev/sda2         204,796,620 1,953,520,064 1,748,723,445   f W95 Ext d (LBA)
/dev/sda5         204,796,683 1,953,520,064 1,748,723,382   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    78,156,224    78,156,162   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   160,826,714   160,826,652   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        B29C32FA9C32B8A5                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        0E64DFBE64DFA6AD                       ntfs       900 GB Driv                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        9438382E383811AA                       ntfs       40G Storage                   
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        B480FBE480FBAB4E                       ntfs       UBUNTU OS                     
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/40G Storage       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc1/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 

```

---

### Post by BigMoose on 2011-01-17
Ok, I have uninstalled wubi and used a Windows boot CD to clean up my MBR.

I am not burning a version of 10.4.1 and will attempt to install. Thanks for the patience with me and I will keep you posted.

---

### Post by bcbc on 2011-01-18
> **BigMoose said:**
> Ok, I have uninstalled wubi and used a Windows boot CD to clean up my MBR.

I am not burning a version of 10.4.1 and will attempt to install. Thanks for the patience with me and I will keep you posted.
No problem! I don't know how long I'll be sticking around online tonight, but will help when I can - if someone doesn't jump in and help first ;)

---

### Post by BigMoose on 2011-01-18
@bcbc

Thanks for the response. After I had the windows cd "fix" my mbr (fixboot and fixmbr), I went and installed Ubuntu 10.0.4.1 on my 80GB drive (which was sdb) and as you suggested had GRUB installed on sda.

After the install and upon reboot, the system went straight to windows. I am thinking that when I did the fixboot and fixmbr, that things might have changed since it probably removed LILO. I tried changing the boot drive to boot from my 40GB drive (previously it was my SATA 100GB partition- where windows is installed) but I got a "Read Error" message (thats all it said) and i tried to boot from the 10.10 LIVE CD so that I can get a new results file from the bootinfoscript but it was running slow and I needed to head out to work.

I will update this post later in the day with the file when I get home. Just as a note, I purchased a new SATA drive that I will be installing once I get it in the mail, since the 40GB and 80BG hardrives are old (at least 4 or 5 years old), should I just wait to get that installed before I move further? Thanks for the help.

---

### Post by bcbc on 2011-01-18
Lilo (in the form you have used) and the Windows bootloader are equivalent for all intents and purposes.

Windows designates the startup program in it's partition boot sector. The windows bootloader just loads up whatever is in the partition boot sector. So changing this doesn't make a difference.

If you really installed grub2, then a) either you installed it somewhere other than /dev/sda, or b) you're not booting from /dev/sda - because there's no normal way grub2 will boot straight into Windows.

If you are planning to move drives around then maybe you should wait. But it doesn't hurt to figure all this out first either so that you understand more about your system and how to go about updating it so it keeps running smoothly when you modify it later.

---

### Post by presence1960 on 2011-01-18
> **bcbc said:**
> Lilo (in the form you have used) and the Windows bootloader are equivalent for all intents and purposes.

Windows designates the startup program in it's partition boot sector. The windows bootloader just loads up whatever is in the partition boot sector. So changing this doesn't make a difference.

If you really installed grub2, then a) either you installed it somewhere other than /dev/sda, or b) you're not booting from /dev/sda - because there's no normal way grub2 will boot straight into Windows.

If you are planning to move drives around then maybe you should wait. But it doesn't hurt to figure all this out first either so that you understand more about your system and how to go about updating it so it keeps running smoothly when you modify it later.

A new boot info script output will help confirm why he is booting to windows.

---

### Post by BigMoose on 2011-01-18
I have attached the updated bootinfoscript results file.

It appears as if what bc had thought is true, the sda doesn't have grub, which to me is odd since it asked where to install grub and I pointed to sda.

In any case it looks like grub 2 is installed on sdb which I think is from a prior install of 10.10 that I tried and is the drive that gave me a "Read Error" when I tried to boot from it.

It sounds to me like I need to install grub again onto sda. I am assuming there are some commands to do this. (I am just throwing out what I think to see if my interpretation of the file is correct :)

Also is there a way to remove that grub 2 since its misleading :).

---

### Post by bcbc on 2011-01-18
You have some issue that's for sure. When you installed Ubuntu, it was only aware of two drives (the 40GB and the 80GB). It installed Ubuntu on what was then /dev/sdb and installed grub on what was then /dev/sda. These correspond to /dev/sdc and /dev/sdb in your current bootinfoscript results. (you can tell this, because grub.cfg refers to itself as being on (hd1,1) when in fact /dev/sdc1 would be (hd2,1).

So I have no idea why the installer doesn't see your terabyte drive, but that is what is happening.

It should still boot if you reinstall grub2 (assuming Ubuntu can see it then).
```
sudo mount /dev/sdc1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

(because the search command overwrites the set root=(hd1,1) command)

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   204,796,619   204,796,557   7 HPFS/NTFS
/dev/sda2         204,796,620 1,953,520,064 1,748,723,445   f W95 Ext d (LBA)
/dev/sda5         204,796,683 1,953,520,064 1,748,723,382   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    78,156,224    78,156,162   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   154,195,967   154,193,920  83 Linux
/dev/sdc2         154,198,014   160,835,583     6,637,570   5 Extended
/dev/sdc5         154,198,016   160,835,583     6,637,568  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        B29C32FA9C32B8A5                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        0E64DFBE64DFA6AD                       ntfs       900 GB Driv                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        9438382E383811AA                       ntfs       40G Storage                   
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        14656ba3-f04b-4282-a1fa-c4e88f565b86   ext4                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        cc3d65b4-4c4a-4130-9b27-d8d83f52af93   swap                                     
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found
error: /dev/sdh: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/14656ba3-f04b-4282-a1fa-c4e88f565b86 ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda5        /media/900 GB Driv       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/B29C32FA9C32B8A5  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 14656ba3-f04b-4282-a1fa-c4e88f565b86
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set 14656ba3-f04b-4282-a1fa-c4e88f565b86
set locale_dir=($root)/boot/grub/locale
set lang=C.UTF-8
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 14656ba3-f04b-4282-a1fa-c4e88f565b86
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=14656ba3-f04b-4282-a1fa-c4e88f565b86 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 14656ba3-f04b-4282-a1fa-c4e88f565b86
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=14656ba3-f04b-4282-a1fa-c4e88f565b86 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 14656ba3-f04b-4282-a1fa-c4e88f565b86
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 14656ba3-f04b-4282-a1fa-c4e88f565b86
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdc1)" {
	insmod ntfs
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set b29c32fa9c32b8a5
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=14656ba3-f04b-4282-a1fa-c4e88f565b86 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=cc3d65b4-4c4a-4130-9b27-d8d83f52af93 none            swap    sw              0       0

=================== sdc1: Location of files loaded by Grub: ===================


   8.8GB: boot/grub/core.img
  17.3GB: boot/grub/grub.cfg
   8.8GB: boot/initrd.img-2.6.32-24-generic
   8.7GB: boot/vmlinuz-2.6.32-24-generic
   8.8GB: initrd.img
   8.7GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg sdh 

```

---

### Post by presence1960 on 2011-01-18
> **BigMoose said:**
> I have attached the updated bootinfoscript results file.

It appears as if what bc had thought is true, the sda doesn't have grub, which to me is odd since it asked where to install grub and I pointed to sda.

In any case it looks like grub 2 is installed on sdb which I think is from a prior install of 10.10 that I tried and is the drive that gave me a "Read Error" when I tried to boot from it.

It sounds to me like I need to install grub again onto sda. I am assuming there are some commands to do this. (I am just throwing out what I think to see if my interpretation of the file is correct :)

Also is there a way to remove that grub 2 since its misleading :).

This is what I would do. I would leave sda alone and put GRUB on the MBR of sdc. This way if one OS goes south you can boot either one by selecting the respective disk to boot first in BIOS.

Boot the ubuntu Live CD/USB and choose try ubuntu. When the desktop loads open a terminal and run ```
sudo mount /dev/sdc1 /mnt
```This will mount your ubuntu / partition.

next in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sdc
```This will put GRUB on the MBR of sdc and have it point to sdc1. Reboot without the Live CD/USB and go into BIOS and set sdc (82GB disk) as first hard disk in the hard disk boot order. Save changes to CMOS and continue booting. At the GRUB menu choose Ubuntu (take note if windows is on the GRUB menu!). When the desktop loads if windows was not on the GRUB menu open a terminal and run ```
sudo update-grub
```

Now you need to run one more command so when your ubuntu updates grub-pc irt will go to MBR of sdc rather than sda. Open a terminal and run sudo dpkg-reconfigure grub-pc

---

### Post by presence1960 on 2011-01-18
> **BigMoose said:**
> I have attached the updated bootinfoscript results file.

It appears as if what bc had thought is true, the sda doesn't have grub, which to me is odd since it asked where to install grub and I pointed to sda.

In any case it looks like grub 2 is installed on sdb which I think is from a prior install of 10.10 that I tried and is the drive that gave me a "Read Error" when I tried to boot from it.

It sounds to me like I need to install grub again onto sda. I am assuming there are some commands to do this. (I am just throwing out what I think to see if my interpretation of the file is correct :)

Also is there a way to remove that grub 2 since its misleading :).

This is what I would do. I would leave sda alone and put GRUB on the MBR of sdc. This way if one OS goes south you can boot either one by selecting the respective disk to boot first in BIOS.

Boot the ubuntu Live CD/USB and choose try ubuntu. When the desktop loads open a terminal and run ```
sudo mount /dev/sdc1 /mnt
```This will mount your ubuntu / partition.

next in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sdc
```This will put GRUB on the MBR of sdc and have it point to sdc1. Reboot without the Live CD/USB and go into BIOS and set sdc (82GB disk) as first hard disk in the hard disk boot order. Save changes to CMOS and continue booting. At the GRUB menu choose Ubuntu (take note if windows is on the GRUB menu!). When the desktop loads if windows was not on the GRUB menu open a terminal and run ```
sudo update-grub
```

Now you need to run one more command so when your ubuntu updates grub-pc it will go to MBR of sdc rather than sda. Open a terminal and run ```
sudo dpkg-reconfigure grub-pc
``` When you get to the windows where you are able to choose where to put GRUB select sdc and make sure the other disks are deselected. Continue and you will be set. Next time ubuntu updates grub-pc the update will go to MBR of sdc.

---

### Post by bcbc on 2011-01-18
+1 to what presence1960 says. That's a good idea to set it to boot from the Ubuntu drive.

---

### Post by presence1960 on 2011-01-18
here are screenshots of what that command will bring forth. Just hit OK until you get to the last window. Then select sdc and deselect everything else.

---

### Post by BigMoose on 2011-01-18
Ok so I ran the frist two commans (Copy and pasted what you provided) and rebooted.

When into the BIOS and changed the boot order to boot from the 82G, this gave me the "read error" again
Tried putting the 40G again, this gave me the "read error" again
Tried the 1TB and it booted directly into the windows.

Good news is Windows still works :) which was expected, bad news is GRUB 2 is installed in two places but neither work. :(

I have attached the updated file.

Edit: I ran the first two commands in what Presence recommended since I didn't notice your reply bc and when I ran the scound command it said something like installation complete with no errors.

---

### Post by bcbc on 2011-01-18
Did you try booting into Ubuntu after installing grub? Or did you change the boot order right after installing grub? Did you get a grub rescue prompt or just a read error?

What exactly is the error you are getting?

---

### Post by BigMoose on 2011-01-18
I changed the boot order. I never got the option to start ubuntu.

As for the error all I get is "Read Error"

---

### Post by bcbc on 2011-01-18
Grub is supposed to drop you to a rescue prompt if it fails to locate the Ubuntu partition. So I suspect there really is a read error - perhaps a failure of grub to read the sectors following the MBR that contain the bootloader code,  or perhaps the bios failing to read the MBR itself.
 
I'd go back in time and try and install grub to the drive with the windows bootloader. You'll just have to have a windows disk handy to patch it if this fails. If you don't feel comfortable doing this then maybe wait for that new drive to arrive.

---

### Post by BigMoose on 2011-01-18
I don't jave a problem with writing grubb to the sata since I have a win boot **** and it will only impact the mbr and not the windows iinstall and more importantly my 900gb partition.

so I make sure I use the correct ommands, what should I put (is it what you posted earlier in ur post an hour or two ago?

---

### Post by bcbc on 2011-01-18
> **BigMoose said:**
> I don't jave a problem with writing grubb to the sata since I have a win boot **** and it will only impact the mbr and not the windows iinstall and more importantly my 900gb partition.

so I make sure I use the correct ommands, what should I put (is it what you posted earlier in ur post an hour or two ago?

The commands depend entirely on the ordering of the disks which I can't see. But the last RESULTS.txt you posted had Ubuntu on /dev/sdb1 and the Windows drive on /dev/sdc so that would be:
```
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdc
```
Please confirm that nothing has changed since.

---

### Post by BigMoose on 2011-01-18
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sdc
Installation finished. No error reported.
ubuntu@ubuntu:~$ 

These are the results, I will be rebooting now.

---

### Post by BigMoose on 2011-01-18
Ok so i got this error now once i rebooted

"error: out of disk"
grub rescue>

---

### Post by bcbc on 2011-01-18
Try the following until you find /boot/grub:

```
ls (hd0,1)/boot/grub
ls (hd1,1)/boot/grub
ls (hd2,1)/boot/grub
```

Report back what you find (that's lower case LS)

---

### Post by BigMoose on 2011-01-18
ls (hd0,1)/boot/grub
-> error unkown filesystem
ls (hd1,1)/boot/grub
-> error: out of  disk
ls (hd2,1)/boot/grub
-> unknown filesystem

---

### Post by bcbc on 2011-01-18
Well... (hd1,1) which is /dev/sdb1 should be your Ubuntu partition and it says "out of disk". So grub is unable to read that. I'm wondering whether there's simply an problem with that drive. Is that the one you've always used to install Ubuntu on? If so, maybe you could try another drive. 
If you boot the live CD and go to the System, Administration, Disk Utility, does it report any errors?

It's curious though that you are able to install on it in the first place, but then grub can't read it when it needs to.

I'm running out of ideas. Drs305 is the grub expert here. This is from his [Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275") thread: 
> "out of disk" ,"device not found", "no such device" , "root device" Errors 
Causes are many, but can be caused by Grub2 not finding partitions/files it is looking for. Some possible areas to explore while troubleshooting:
Does your BIOS see the files? Older BIOS may not see past 8GB or 137GB of the partition. You may need to create a separate /boot partition or adjust the BIOS to use the 'large disk' mode or update the BIOS to allow it to use today's larger disks.
Some users may need to add "rootdelay=90" to the end of the "linux" line in /etc/default/grub. The might be necessary if the system takes a long time to recognize the drive.
The BIOS controller mode may need to be changed. Change the BIOS entry for the SATA Controller from from AHCI to Compatibility mode.

Maybe post on that thread and see if he can help.

---

### Post by BigMoose on 2011-01-19
I have done so much installing and uninstalling that it would be great to start from scratch. I am on the  verge of giving up on installing Ubuntu, long time ago I used Redhat and it didn't give me any trouble installing (not on this machine but a different machine I use to have). I am thinking about doing the following or just even waiting to install my other drive and see if I have any luck with that:

1. Restore my windows mbr using me restore CD
2. Reformat my 40 GB and 80GB drives
3. Remove grub from both other drives (If I can even do that)
4. Boot from the live CD and confirm everything is back to square run
5. Run some disk checks and repair utils on the drives see if anything is found
6. Start installing things one step at a time.

Let me know your thoughts.

---

### Post by bcbc on 2011-01-19
I can understand your frustration. I guess I've just been lucky - it always seems to work when I install. And I remember the old days (well not so far back) when installing linux took a few weekends. So for me Ubuntu is a breeze. But then my computers are quite boring vanilla types.

So, yeah I'd reinstall the windows bootloader - or lilo would work fine. I use lilo when I need to even though I have my windows disks as it's easier to do it from linux.

And then format away. By the way did you try installing Ubuntu to the 40 GB drive - grub rescue didn't seem to have a problem seeing that one.

---

### Post by BigMoose on 2011-01-19
Once I finish cleaning it all up, I was planning on installing it on the 40GB. I would rather leave the new drive purely for storage than partition it for OS, but will if this doesn't work.

Your help was much appreciated and I think I will still try to get it to work but probably put less time into it.

---

### Post by BigMoose on 2011-01-19
Ok so I installed Ubuntu 10.0.4.1 on the 40G and it seems to give me the same problems regardless of where GRUB is.

When I have it on the 1TB drive still gives me an out of memory error when I boot from that drive. I am thinking that the MBR of the 40GB and 80GB are bad since when those are set to boot I can't even read from them.

I think I am going to try and install the Windows OS on one of those and d/c my other drives to see if it is a hardware issue at this stage.

---

### Post by BigMoose on 2011-01-20
I read somewhere that if you previously had an OS on a harddrive and you didn't do a windows (from windows boot disk) that you could run into problems installing grub. So I went ahead and used my boot to empty out my two hard drives and lets see if this does the trick.

I have attached my latest results file after I cleaned out all instances of grub 2 which was done by using the XP boot cd to fixboot, fixmbr and delete the partitions on my 40G and 80G drives. Wish me luck. :)

---

### Post by BigMoose on 2011-01-25
I removed my two older drives and installed a new 2TD SATA drive and I no longer got any errors.

I was able to install 11.04 and it booted with GRUB 2 working properly so it must have been some bad MBR on those hard drives which isn't out of the question since they are pretty old.

---

### Post by bcbc on 2011-01-25
> **BigMoose said:**
> I removed my two older drives and installed a new 2TD SATA drive and I no longer got any errors.

I was able to install 11.04 and it booted with GRUB 2 working properly so it must have been some bad MBR on those hard drives which isn't out of the question since they are pretty old.
Good to hear you've got it all working. It seems you like the adventure if you're already trying out 11.04. Enjoy!

---

### Post by BigMoose on 2011-01-26
I sure do like adventure, but I have to admit I accidentally installed 11.04 by installing from the live CD desktop option to install which I think installed the latest version when I thought it would only install the 10.10. (At least some areas said I was using 11.04 but I didn't really know how to confirm it, I know my grub 2 is 1.98 (the version used for 10.10).

I am playing around with it already and it seems pretty cool, although I got WOW working on it, it is suffering from extreme lag compared to it running on Windows, but since I am not much of a gamer I can just use windows for WoW and get use to using ubuntu for everything else.

Thanks again for the help in trying to trouble shoot it, the volunteers that try to trouble shoot do a great job in trying to help people out which is great for newbies like me.

My only issue that i have seen is when I search for problems like mine and people mark their threads as solved, it would be great if when a person marked a thread solved a little text area would open up that would remind the person to put how they solved it so that future readers can see the solution that finally worked. Not sure where to suggest it but it is just a thought.

---

### Post by bcbc on 2011-01-26
> **BigMoose said:**
> I sure do like adventure, but I have to admit I accidentally installed 11.04 by installing from the live CD desktop option to install which I think installed the latest version when I thought it would only install the 10.10. (At least some areas said I was using 11.04 but I didn't really know how to confirm it, I know my grub 2 is 1.98 (the version used for 10.10).
OK, this is a known bug - you're actually running 10.10. Type "cat /etc/lsb-release" or run "lsb_release -a" and it will tell you it's 10.10. (That's a good idea - Natty is still early Alpha - so very unstable)

> **BigMoose said:**
> I am playing around with it already and it seems pretty cool, although I got WOW working on it, it is suffering from extreme lag compared to it running on Windows, but since I am not much of a gamer I can just use windows for WoW and get use to using ubuntu for everything else.I don't use Ubuntu for gaming - but I know graphics card support and/or running with Wine isn't always the best.

> **BigMoose said:**
> Thanks again for the help in trying to trouble shoot it, the volunteers that try to trouble shoot do a great job in trying to help people out which is great for newbies like me.You're welcome. That's what makes Ubuntu so great, in my opinion: the community.


> **BigMoose said:**
> My only issue that i have seen is when I search for problems like mine and people mark their threads as solved, it would be great if when a person marked a thread solved a little text area would open up that would remind the person to put how they solved it so that future readers can see the solution that finally worked. Not sure where to suggest it but it is just a thought.
The Solved thing is a problem - many don't use it, or they use it when the problem isn't really solved e.g. they reinstalled, or they don't say anywhere how it was solved. So you just have to keep searching for another solution.

---

