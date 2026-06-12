---
title: "Not booting after new install"
date: 2010-08-22
forum: Installation &amp; Upgrades
---

### Post by jeckel20003 on 2010-08-22
This is my first time working with Ubuntu. My computer has 2 internal HDDs. I have a 250GB SATA that I am running Windows XP off of and I have a 160GB IDE that I was going to use to install Ubuntu 10.04. I used a program to shred the drive before doing anything. I then used a USB to install Ubuntu to the drive. Everything seemed to install fine. I didn't get any errors. When the computer restarted after the install, I used the BIOS boot menu to boot from the 160GB drive that now has Ubuntu on it. When it tries to boot from the drive, I just get a message that says "Read Error". That is all it says. I have tried installing several times and keep getting the same error. I used to use the 160GB as extra storage while using Windows XP. I never had any problems saving to it or reading from it. So I don't think there is anything wrong with the drive. I can still boot from my 250GB Windows drive and I can run Ubuntu from my USB with no problems. Any ideas?

---

### Post by oldfred on 2010-08-22
Did grub2 install to the IDE drive?

Lets see where everything is at:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by jeckel20003 on 2010-08-22
Okay, I tried that and this is what I got.


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdg

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdg1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   241,924,964   241,924,902   7 HPFS/NTFS
/dev/sda2         241,926,142   320,172,031    78,245,890   5 Extended
/dev/sda5         241,926,144   316,870,655    74,944,512  83 Linux
/dev/sda6         316,872,704   320,172,031     3,299,328  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
240 heads, 63 sectors/track, 32301 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   488,391,119   488,391,057   7 HPFS/NTFS


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 4100 MB, 4100980736 bytes
16 heads, 63 sectors/track, 7946 cylinders, total 8009728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdg1    *             63     8,009,727     8,009,665   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        DAB0E63CB0E61EAF                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        52899868-53fc-4b9a-ae2c-77951db4a0ec   ext4                                     
/dev/sda6        63ebea22-f6be-4414-a3f5-ac806d95e646   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2DDBBB9270E45896                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdg1        5DF3-0227                              vfat       USB DRIVE                     
/dev/sdg: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdg1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
search --no-floppy --fs-uuid --set 52899868-53fc-4b9a-ae2c-77951db4a0ec
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
search --no-floppy --fs-uuid --set 52899868-53fc-4b9a-ae2c-77951db4a0ec
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 52899868-53fc-4b9a-ae2c-77951db4a0ec
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=52899868-53fc-4b9a-ae2c-77951db4a0ec ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 52899868-53fc-4b9a-ae2c-77951db4a0ec
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=52899868-53fc-4b9a-ae2c-77951db4a0ec ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 52899868-53fc-4b9a-ae2c-77951db4a0ec
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 52899868-53fc-4b9a-ae2c-77951db4a0ec
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP Media Center Edition (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 2ddbbb9270e45896
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
UUID=52899868-53fc-4b9a-ae2c-77951db4a0ec /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=63ebea22-f6be-4414-a3f5-ac806d95e646 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 145.4GB: boot/grub/core.img
 139.4GB: boot/grub/grub.cfg
 124.2GB: boot/initrd.img-2.6.32-21-generic
 145.4GB: boot/vmlinuz-2.6.32-21-generic
 124.2GB: initrd.img
 145.4GB: vmlinuz

================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect /usepmtimer 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  c7 5d 9b 12 84 58 51 3d  61 ec 5d 02 99 ef 8c 09  |.]...XQ=a.].....|
00000010  04 72 fe 08 50 f3 84 93  8e d4 4d 36 f1 0c c2 c1  |.r..P.....M6....|
00000020  d3 1d ae e3 f9 46 a2 fa  18 f9 98 2a 98 8f d6 ac  |.....F.....*....|
00000030  97 3b 15 69 31 3c e3 c8  ff 57 46 c4 dd 85 a2 41  |.;.i1<...WF....A|
00000040  f1 e9 dc a0 e9 04 c0 91  83 2c a0 28 53 3a 3e 34  |.........,.(S:>4|
00000050  c1 84 ed cc 51 0b f2 2a  27 f5 30 bd ca 3d 05 79  |....Q..*'.0..=.y|
00000060  28 a9 6f 72 da fc 73 a9  aa 6d bf 25 52 59 8e 46  |(.or..s..m.%RY.F|
00000070  87 35 cc 57 36 c6 7a 62  0e 94 55 48 3e 9c b2 10  |.5.W6.zb..UH>...|
00000080  80 45 ad 80 56 95 82 ea  93 a5 3b 49 1e 52 8c 8d  |.E..V.....;I.R..|
00000090  f3 36 fb 32 6a d7 43 17  bc 1d fb 8e c3 0a 73 af  |.6.2j.C.......s.|
000000a0  01 a5 df f3 e4 37 b7 fe  48 ba 5d bb 3e 8f 01 ae  |.....7..H.].>...|
000000b0  0c 6f c2 86 75 a4 15 f2  3a 79 6b b6 e0 ef 0e fe  |.o..u...:yk.....|
000000c0  b4 b1 4c f2 0d 4a d8 8a  d1 96 6d a4 3a 76 b4 54  |..L..J....m.:v.T|
000000d0  da c8 68 7b dd 97 b8 9b  8f 8e ed e9 1e b3 4c a4  |..h{..........L.|
000000e0  a0 52 3e a6 57 36 ae 39  34 1f b3 2b 9b 71 6f 25  |.R>.W6.94..+.qo%|
000000f0  66 2a 37 38 2c 16 f3 b9  c3 46 c8 4f 03 be f5 4a  |f*78,....F.O...J|
00000100  cd 6e fb 36 4c 64 01 b0  7b 3f 76 79 e8 e7 f8 c9  |.n.6Ld..{?vy....|
00000110  b7 7b 75 e6 e9 8b 90 f4  df 88 46 0f 19 78 d1 97  |.{u.......F..x..|
00000120  44 ee cc cb 74 3a 99 9a  ae dd 00 b5 a9 40 18 e9  |D...t:.......@..|
00000130  d5 a5 6b ac 9d 5d 55 f6  e9 3b ad 52 e8 4a a7 34  |..k..]U..;.R.J.4|
00000140  0c bb f9 8d 56 21 3d 9d  d3 e1 97 08 67 e3 97 2d  |....V!=.....g..-|
00000150  c9 8e 61 b3 cf f4 0b 64  ec 49 46 3f f7 9a 41 c8  |..a....d.IF?..A.|
00000160  2d bb ca a3 7a 82 b7 61  f4 32 84 9a a8 3a 3d 3c  |-...z..a.2...:=<|
00000170  9a 20 9e 22 07 b8 7a e9  ed 99 59 ff ce d1 65 fc  |. ."..z...Y...e.|
00000180  b0 d8 87 36 68 c3 cd 8f  18 ba 0f 92 f7 ac d2 bf  |...6h...........|
00000190  50 41 6c 22 ce 11 69 2b  f6 13 2e b9 f5 58 dc 78  |PAl"..i+.....X.x|
000001a0  9c f9 77 6d a9 4e 48 cf  48 60 7f 19 d9 a1 1d 5d  |..wm.NH.H`.....]|
000001b0  f4 db 11 db aa 67 a1 d2  0e 9f 0c 96 f5 95 00 fe  |.....g..........|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 90 77 04 00 fe  |............w...|
000001d0  ff ff 05 fe ff ff 02 90  77 04 00 60 32 00 00 00  |........w..`2...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by oldfred on 2010-08-22
It looks like grub is installed correctly. Your windows boot.ini in drive sdb or drive 1 refers to drive 0, so maybe you are booting the 250GB drive adn with the 163.GB drive windows does not see it correctly?? Check if in BIOS you are booting the 163.9GB drive. Grub's drivemap command is to make windows think it is the first drive even when it is not.

---

### Post by jeckel20003 on 2010-08-22
I've just been hitting ESC when the computer first starts up so I can pick the boot device. From there I've been picking the 160GB drive that has Ubuntu. I haven't actually tried going into the BIOS and switching the HDD to boot from the 160GB which would eliminate having to pick that HDD when the computer starts. I'll give that a try. As I said, I'm new to Ubuntu so I know nothing about it.

---

### Post by jeckel20003 on 2010-08-22
Went into the BIOS and changed the drive to boot from to the 160GB Ubuntu. Didn't make any difference. Didn't think it really would. Reinstalled Ubuntu on the 160GB drive with the 250GB drive disconnected. Got the same "Read Error" as before. When I am getting ready to install and I get to the point of picking a drive and how to install, it says the drive has Ubuntu 10.04 on it and asks if I want to make Ubuntu install side by side with the Ubuntu already installed. So I would think that Ubuntu has installed correctly on the drive but for some reason it just won't boot. This has been a really disappointing experience for me. From what I have seen so far, Ubuntu looks like a really nice OS and I would really like to try it out. I would definitely look at installing it as opposed to Windows on my next desktop build. That is once I get to try it out more.

---

### Post by oldfred on 2010-08-23
Sometimes while everything looks ok grub2 just has to be reinstalled to the MBR.

Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

---

### Post by jeckel20003 on 2010-08-23
Tried sudo mount /dev/sda5 /mnt
and it says "mount: special device /dev/sda5 does not exist"
Tried sudo grub-install --root-directory=/mnt /dev/sda
and it says "error: cannot find a device for /mnt/boot/grub (is /dev mounted?)"
Tried sudo grub-install --recheck --root-directory=/mnt /dev/sda
and it gives the same error as the one before

---

### Post by xaliqen on 2010-08-23
I think this has already been covered, but you shouldn't have to change any startup disks in your BIOS since GRUB will handle everything for you if it's configured properly.  In fact, changing the boot disk in the BIOS can easily cause problems, so I would recommend not doing this unless it's necessary.

If you need to restore GRUB, you can try Super Grub disk, which is targeted specifically at rescuing and troubleshooting systems with GRUB and MBR problems.

Check among the [list of issues]("http://www.supergrubdisk.org/wiki/Boot_Problems"), and see if one of them matches your setup.

---

### Post by jeckel20003 on 2010-08-23
Found this link. [http://ubuntuforums.org/showthread.php?t=1558493](http://ubuntuforums.org/showthread.php?t=1558493)
It says:

**[COLOR=DarkRed]External Drive Installs and MBR - Bug [/COLOR][bug/414996]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/414996")**
When installing Ubuntu to a USB drive, the potential exists for GRUB 2  to write to the hard drive's MBR or split the installation between the  hard drive and the USB drive (rather than completely on the USB device).  This can render the main drive unbootable. 

Workaround: During the final stages of the install there is an  "Advanced" button which allows the user to select the install location. 

I also tried what it said to do to reinstall Grub 2. Didn't get any errors but my drive still says "Read Error" when I try to boot from it.

---

### Post by xaliqen on 2010-08-23
Just to confirm, did you change the BIOS setup back to what it was at the time you installed Ubuntu?  Otherwise, the system could be looking for the MBR on the wrong hard drive.

If you need to reinstall GRUB, there are a number of easy ways to do that without reinstalling Ubuntu (super grub disk, etc...).

If there are strange issues in your current hd setup, then you can look at what's going on with the partitions in a [gparted live cd]("http://gparted.sourceforge.net/livecd.php").

Boot problems can be very frustrating, but they usually have an elegant solution once the core issue is discovered.

---

### Post by jeckel20003 on 2010-08-23
I only have my 160GB drive connected right now. I installed Ubuntu the last time with only this drive connected. I just ran Super Grub Disk and it didn't help me out any. I used "Auto ;-)" and it says:

findf /grub/stage1 /boot/grub/stage1
Error 15: File not found

---

### Post by xaliqen on 2010-08-23
It looks like GRUB may not be installed on the hard drive.  In that case, you may need to use the rescatux disk (on the same site as super grub) to specify linux boot and rewrite GRUB to the MBR.

If asked where to write the MBR, remember to choose the HD that will be first in your boot-order in the BIOS.

You could also try the old solution in [this thread]("http://ubuntuforums.org/showthread.php?t=297261"), and install GRUB from an Ubuntu installation CD.

---

### Post by oldfred on 2010-08-23
If it said it was looking for stage 1 that is old grub. There is  a version of super grub for grub2 also.

If you have installed parts of old grub and grub2 that can cause problems also.

---

### Post by jeckel20003 on 2010-08-23
What I am trying to do is have one hdd with windows and one hdd with ubuntu. I was then wanting to have the windows hdd as the first boot device in BIOS and wanted to be able to hit ESC when the computer first starts up so I can bring up the menu where I can choose which device to boot from and pick ubuntu if I want to run it. That way windows would always boot up no matter what but if I wanted to run ubuntu I could choose its hdd as the boot device when the computer first starts up. I'm assuming that is possible. So this would make the windows hdd first in my boot order in BIOS. Would I write GRUB to the MBR on the windows hdd?

---

### Post by jeckel20003 on 2010-08-23
Yes I downloaded the Super Grub for the old GRUB. I read 10.04 uses GRUB2 but I thought from the previous post that that was the Super Grub I was supposed to use. Like I said, I'm new to this.

---

### Post by xaliqen on 2010-08-23
Yes, GRUB and the MBR would be on the windows disk (assuming the windows disk is specified as first in the BIOS load-order).  GRUB should reference any other systems present on other disks and boot to those disks when told to do so.

There may be issues I'm unaware of when using different drive setups, but using just one MBR for all systems across all disks is how things are supposed to work when everything is up and running.  Here's a [more detailed description of how it works]("http://en.wikipedia.org/wiki/GRUB#Boot_process").

> **jeckel20003 said:**
> Yes I downloaded the Super Grub for the old GRUB. I read 10.04 uses GRUB2 but I thought from the previous post that that was the Super Grub I was supposed to use. Like I said, I'm new to this.

Sorry, I should have specified you'll need to select options related to GRUB2.  I thought super grub attempts to auto-detect both, but my memory's a bit rusty.

Here's more documentation on [installing GRUB2 from the Ubuntu live cd]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD"), if you want to try that route.

---

### Post by oldfred on 2010-08-24
When you tried to reinstall grub2 and it would not let you mount "special' device sda5 had you not plugged in the drive or was entire drive not mounted as sda?

from liveCD when you want to run the reinstall of grub
```

sudo fdisk -l
```

and it should show sda5 as a linux partition.

---

### Post by jeckel20003 on 2010-08-24
I know that when you use the option of installing ubuntu by partitioning an hdd so that you have windows and ubuntu on the same hdd it will ask at startup which OS you want to run. Does it do the same thing if you have windows on one hdd and ubuntu on another hdd? I'm assuming it would if the MBR is located on the boot first hdd which would be windows in my situation. So trying to change the boot first hdd to the ubuntu drive wouldn't work because the windows hdd has the MBR on it. Is that correct? I've tried using the process you had in the link to reinstall GRUB but it didn't work. However, I have my windows hdd disconnected right now and I was trying to install it to the ubuntu hdd so if the MBR is located on my windows hdd that might explain why it didn't work and ubuntu still wouldn't load. The last time I tried installing ubuntu I did it with the 160GB hdd being the only hdd connected so shouldn't that have caused it to have created a MBR on the 160GB? I haven't ever had to deal with MBRs or even their existence until doing this so it's a learning experience for me.

---

### Post by jeckel20003 on 2010-08-24
From what I can tell, sda should be the 160GB drive and sdb should be the 250GB drive. So all of the sda drive should have been mounted. I'll have to give Rescatux a try tomorrow.

---

### Post by oldfred on 2010-08-24
In the old days with IDE only the primary master would be the boot drive (and floppy). Now with SATA and improved BIOS you can set any drive as the boot drive in BIOS or select a drive with f12 (or other key) to boot one time.

Each drive has a MBR which can be used for booting, but the BIOS will only use one. Now you can select CD, USB devices, Flash drives and just about anything to boot. All you have to do is install a boot loader into that drives MBR.

While discussing windows and very detailed you can just review pictures & diagrams to understand windows booting:
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by xaliqen on 2010-08-24
> **jeckel20003 said:**
> I know that when you use the option of installing ubuntu by partitioning an hdd so that you have windows and ubuntu on the same hdd it will ask at startup which OS you want to run. Does it do the same thing if you have windows on one hdd and ubuntu on another hdd?

Yes.  To use a strange analogy, think of MBR and GRUB as the only old-fashioned paper card-catalogue in a library-system spread across multiple universities (multiple hard drives).  It lists all the partitions with bootable operating systems it knows about, but it's only installed in one location, which is in the main library at the largest university (primary HD specified in the BIOS).

To reference the information you need, you have to go to that main university library (reference the MBR on the primary HD).  If you change the primary HD in your BIOS, then it could cause problems because there's no card catalogue in the library there (the MBR with GRUB isn't on that HD).

You *can* install different MBRs on different hard drives, and change primary drives in the BIOS for different boot setups.  But, this is a recipe for confusion (and problems) unless you have an *extremely* good reason for setting things up that way.

Hmm... I don't know if that cleared anything up or not, but the basic principle is that there's one MBR to rule them all.

---

### Post by jeckel20003 on 2010-08-24
Burnt a LiveCD just to give it a try since I have been trying to install from a USB. Got done installing and it gave the same "Read Error". Tried rescatux and when I click on "Restore Grub / Fix Linux Boot" the box it is in just flashes and goes right back to the main menu it starts at. If I click it a couple more times it will finally say to pick a hdd but there is a bubble to click but no hdd listed anywhere. If I click on it it asks to pick a partition but once again there is a bubble to click but no partitions listed. Opened a terminal and used "sudo fdisk -l" and it showed me the hdd and partitions on it. Tried Super Grub2 Disk. Had it detect any OS and it came back with none found. It also couldn't find a Grub2 configuration file or a Grub2 installation. I had it list devices/partitions and it found my 160GB hdd. I think I'm going to try and wipe the whole drive clean again with a hdd shred program before I try anything else.

---

### Post by oldfred on 2010-08-25
Have you checked your BIOS settings for the hard drive.

A recent post had this comment:
BIOS should be set for IDE compatibility mode
The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.

ALERT! /dev/disk ... does not exist." error
Boot the machine and go to BIOS configuration (F2) and change:
Advanced -> SATA Controller Mode
from "AHCI" to "Compatibility"

---

### Post by jeckel20003 on 2010-08-26
Used Zilla Data Nuker to shred the drive. Formatted the drive. Installed Ubuntu from the LiveCD. Got "Read Error". Went into the BIOS and changed the hdd from AUTO to LBA. Got "Read Error". Couldn't find anything about SATA controller mode in the BIOS. Still have my SATA hdd disconnected though. Tried Super Grub2 Disk again. It couldn't find an OS. Tried "Enable GRUB2's PATA Support (to work around BIOS bugs/limitations)" just to see what it would do. After it was done, I had it try to find an OS again. It found the Ubuntu installation and booted it. I ran Ubuntu for a little while with absolutely no problems. It even did a bunch of updates. Restarted the computer, it tried to boot from the hdd and I got "Read Error" again. So that's where I am right now. Sounds like this problem might be because of my BIOS? Granted the motherboard is a few years old. It's a Foxconn [NF4SK8AA-8EKRS]("http://www.foxconnchannel.com/product/motherboards/detail_overview.aspx?id=en-us0000008")
[]("http://www.foxconnchannel.com/product/motherboards/detail_overview.aspx?id=en-us0000008")

---

### Post by adrian15 on 2010-08-26
> **jeckel20003 said:**
> Tried rescatux and when I click on "Restore Grub / Fix Linux Boot" the box it is in just flashes and goes right back to the main menu it starts at. If I click it a couple more times it will finally say to pick a hdd but there is a bubble to click but no hdd listed anywhere.

You should click once and wait, you might double-click I suppose. It's normal that no partitions containing Ubuntu are found because Ubuntu lastest versions are ext4 based.

Unfortunately [nodoby at ubuntu forums tested Rescatux](http://georgia.ubuntuforums.org/showthread.php?t=1527624) and reported that strange behaviour.

Yesterday, I found another user in rescatux's chat that had the same problem as you.

The current workaround is that if your computer is 64bit (this is independent of Ubuntu installation being amd64 or not itself) you can use Rescatux 0.10 AMD 64.

adrian15

---

### Post by oldfred on 2010-08-26
My motherboard also had a setting for IDE (PATA) compatibility. Look for something like that.

Once in Ubuntu did you reinstall grub2 from there?

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by jeckel20003 on 2010-08-26
Finally got Ubuntu working. So far anyway. Haven't had a lot of time to mess around with it much yet since I just got it working a few hours ago. After reading oldfred's last post about IDE compatibility, I looked through my BIOS again. Went into advanced BIOS and found two options that had to do with IDE. Tried disabling "IDE HDD Block Mode" and it didn't make a difference. So then I tried disabling "IDE DMA Transfer Access" which had no explanation in the BIOS as to what it did. Restarted the computer and Ubuntu booted up no problem. According to the motherboard manual "This item is used to enable or disable the DMA transfer function of the IDE hard drive." Ubuntu had all of the changes and updates I made yesterday when I booted it with Super Grub2 Disk. Shut it down and connected my SATA Windows hdd and everything works fine. I have the Windows hdd set as the first boot hdd so it automatically boots Windows. If I want to run Ubuntu, I can press ESC when the computer starts up to bring up the boot menu and boot from the Ubuntu hdd. So it is working perfectly so far. I've only tried booting Windows and Ubuntu one time each. So I guess my problem was with the BIOS the whole time. Thanks to everyone who helped me out. I'm sure it's a little annoying trying to help out someone who doesn't really know much about the subject but I appreciate all of the help.

---

