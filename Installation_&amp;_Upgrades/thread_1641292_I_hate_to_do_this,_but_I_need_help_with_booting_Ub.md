---
title: "I hate to do this, but I need help with booting Ubuntu 10.10"
date: 2010-12-08
forum: Installation &amp; Upgrades
---

### Post by thenags on 2010-12-08
I hate to do this, because I know it's asked all the time, but I just can't get it.

Let me start by saying that I've installed and uninstalled Ubuntu numerous times in the past and I've never had a problem.  After about 6 months of not having Ubuntu installed and hearing such good things about 10.10, I decided it was time to give it another shot.

I tried last week and eff'd up my Win7 bootloader somehow and could never get it fixed and ended up formatting my main drive.

I have 5 hard drives in the computer.  4 are very large SATA drives and one is an 80GB IDE drive.  I'd like to install to the 80GB again as I've done in the past.

I start by booting into the CD obviously and going through the first few steps.  I've tried selecting to 'Install alongside another operating system' and then telling it to use the whole 80GB.  That installs and then just boots right into Windows 7.  I've tried manually setting the partitions on the 80GB and giving 70GB for Ubuntu and 10GB for Swap and setting the Bootloader to the 80GB drive.  Exact same end result.

I then tried using EasyBCD and did an 'Add Entry' for Linux and selected GRUB 2.  Rebooted and got the menu asking what to boot to.  I select Linux and it gives me an error along the lines of (0,0).  I assume it's looking in the wrong spot for Ubuntu, but in EasyBCD it says it'll auto detect once I select 'GRUB 2'

Anyways, that's where I'm at now and help would be greatly appreciated.

---

### Post by thenags on 2010-12-08
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd
 => Grub 2 is installed in the MBR of /dev/sde and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sdd2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sde1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sde2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sde5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdg: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  According to the info in the boot sector, sdg has 
                       495616 sectors.. But according to the info from the 
                       partition table , it has 1982464 sectors.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   781,417,664   781,417,602   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 3,907,026,943 3,907,024,896   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdd2             206,848   293,044,223   292,837,376   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *          2,048   136,769,535   136,767,488  83 Linux
/dev/sde2         136,771,582   156,301,311    19,529,730   5 Extended
/dev/sde5         136,771,584   156,301,311    19,529,728  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        A484E17984E14E7C                       ntfs       400gb                         
/dev/sda: PTTYPE="dos" 
/dev/sdb1        20F4D917F4D8F050                       ntfs       2TB - Torrents                
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        56D89DADD89D8C3D                       ntfs       1TB                           
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        4E886F95886F7A7B                       ntfs       System Reserved               
/dev/sdd2        4276729A76728E83                       ntfs                                     
/dev/sdd: PTTYPE="dos" 
/dev/sde1        f3fad9c4-0cfc-40f7-9be5-3fa9409183b8   ext4                                     
/dev/sde2: PTTYPE="dos" 
/dev/sde5        3005e431-12d4-4a36-a7d6-f5279d43501d   swap                                     
/dev/sde: PTTYPE="dos" 
/dev/sdg         ACCF-92F8                              vfat       NAGS'S IPOD                   
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sde1/boot/grub/grub.cfg: ===========================

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
set root='(hd4,msdos1)'
search --no-floppy --fs-uuid --set f3fad9c4-0cfc-40f7-9be5-3fa9409183b8
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd4,msdos1)'
search --no-floppy --fs-uuid --set f3fad9c4-0cfc-40f7-9be5-3fa9409183b8
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
    set root='(hd4,msdos1)'
    search --no-floppy --fs-uuid --set f3fad9c4-0cfc-40f7-9be5-3fa9409183b8
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f3fad9c4-0cfc-40f7-9be5-3fa9409183b8 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd4,msdos1)'
    search --no-floppy --fs-uuid --set f3fad9c4-0cfc-40f7-9be5-3fa9409183b8
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=f3fad9c4-0cfc-40f7-9be5-3fa9409183b8 ro single 
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
    set root='(hd4,msdos1)'
    search --no-floppy --fs-uuid --set f3fad9c4-0cfc-40f7-9be5-3fa9409183b8
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd4,msdos1)'
    search --no-floppy --fs-uuid --set f3fad9c4-0cfc-40f7-9be5-3fa9409183b8
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdd1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd3,msdos1)'
    search --no-floppy --fs-uuid --set 4e886f95886f7a7b
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

=============================== sde1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sde1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sde5 during installation
UUID=3005e431-12d4-4a36-a7d6-f5279d43501d none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sde1: Location of files loaded by Grub: ===================


  64.5GB: boot/grub/core.img
  36.6GB: boot/grub/grub.cfg
    .7GB: boot/initrd.img-2.6.35-22-generic
  64.5GB: boot/vmlinuz-2.6.35-22-generic
    .7GB: initrd.img
  64.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sde2

00000000  5d 3b 71 29 5c e6 be c4  80 b1 ac 16 82 28 c8 10  |];q)\........(..|
00000010  f6 d5 be 03 9c 9e d6 96  3f 78 a3 5a 66 b4 c5 9a  |........?x.Zf...|
00000020  2e b4 98 e1 1f aa 95 0d  79 ad 96 61 ca 7a ad c2  |........y..a.z..|
00000030  44 fb ce f5 0c e9 df 96  8e 46 35 b3 ff d3 88 ff  |D........F5.....|
00000040  a5 13 8d cc 19 19 ae c2  2f 48 31 ed e8 70 fa 95  |......../H1..p..|
00000050  73 af 0a ff 75 21 aa 22  17 7b 9d bd 7c 3b 56 a3  |s...u!.".{..|;V.|
00000060  54 ec 2f 79 66 36 4f 44  e9 f1 50 ed 55 fc be 2f  |T./yf6OD..P.U../|
00000070  1d fe 0e f7 7d 00 c2 f1  9e 3f 3e 84 bb fe 56 db  |....}....?>...V.|
00000080  7e 59 06 91 d9 24 1e df  7a 01 b1 dc 6a 5d 93 15  |~Y...$..z...j]..|
00000090  db a2 3b 29 0c 02 a7 fc  ed 2e f3 4d e4 ba 64 29  |..;).......M..d)|
000000a0  e0 c0 63 9b d5 72 e7 c4  7c bf ad 90 29 f6 a5 6e  |..c..r..|...)..n|
000000b0  26 06 24 de fa f3 b4 18  a0 d5 5a b0 23 c1 7d 1b  |&.$.......Z.#.}.|
000000c0  a0 78 da 16 1b 0a 6d fe  fb 14 74 0d 82 ec 7f 2c  |.x....m...t....,|
000000d0  64 94 7a 23 4c 6d b4 5a  7c 4b f6 7b fd 1d cc 52  |d.z#Lm.Z|K.{...R|
000000e0  85 c5 7d 38 36 3e 14 b9  a8 78 0f 1a 27 36 af 0f  |..}86>...x..'6..|
000000f0  57 24 2b bf e7 57 3e ee  fb 01 db 94 a7 38 48 7a  |W$+..W>......8Hz|
00000100  e7 bd 4c fb 98 63 73 98  d8 89 ec 5b 9c 63 74 c8  |..L..cs....[.ct.|
00000110  28 63 0b cd 91 d3 0b 48  95 3e f4 6e 7c 43 c0 26  |(c.....H.>.n|C.&|
00000120  38 31 41 8c 19 02 9f be  bb 5c 2c 46 17 f7 8a e2  |81A......\,F....|
00000130  f2 c4 25 53 46 4a a8 e9  45 64 18 f8 31 20 ad 74  |..%SFJ..Ed..1 .t|
00000140  d6 1f 0a 7a 89 cc 8d 81  88 c4 ec dc f8 89 fc 7d  |...z...........}|
00000150  cc a0 7b 26 49 ef aa 48  d5 88 ab 14 6b c9 a5 2c  |..{&I..H....k..,|
00000160  8d 79 9d ea 5b d6 db 25  7e b5 53 61 d0 53 56 b7  |.y..[..%~.Sa.SV.|
00000170  53 e5 33 b5 26 37 82 ad  27 62 3f 4c 93 8c 88 3a  |S.3.&7..'b?L...:|
00000180  ef 7b ed 32 9e f2 7d 7a  9b 91 49 22 2e e8 6b 01  |.{.2..}z..I"..k.|
00000190  8c b3 3d 57 d1 81 90 51  76 64 6b 41 2e ba 0f c7  |..=W...QvdkA....|
000001a0  57 d4 0c ce 90 3c 8e ba  aa 7c 72 1f be c7 19 05  |W....<...|r.....|
000001b0  3f aa f9 fd ac 63 1c b0  3d ef 4e a8 34 3f 00 fe  |?....c..=.N.4?..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 00 2a 01 00 00  |............*...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============



```

---

### Post by wilee-nilee on 2010-12-08
I believe I see some of the problems, but this will take some help from a more experienced user, thanks for code tagging it.;)

I have left some information in another post though to start with.

---

### Post by thenags on 2010-12-08
There ya go.

---

### Post by wilee-nilee on 2010-12-08
> **thenags said:**
> There ya go.

Besides the grldr reference in the W7 setup you have grub in two MBR's, can you use a per-session boot from key prompt and choose the sde drive to boot from. My per-session key is f12, hit just like you would if trying to get to the bios. You could try putting the sde drive first in the bios but the key prompt is a good thing to know.

You also have multiple boot flags sda1, and sde1, both not needed. The sdd1 is correct for booting W7.

---

### Post by thenags on 2010-12-08
> **wilee-nilee said:**
> Besides the grldr reference in the W7 setup you have grub in two MBR's, can you use a per-session boot from key prompt and choose the sde drive to boot from. My per-session key is f12, hit just like you would if trying to get to the bios. You could try putting the sde drive first in the bios but the key prompt is a good thing to know.

You also have multiple boot flags sda1, and sde1, both not needed. The sdd1 is correct for booting W7.

I'd prefer to have grub come up and just default to Windows 7, so it'd boot automatically into Win7

---

### Post by wilee-nilee on 2010-12-08
> **thenags said:**
> I'd prefer to have grub come up and just default to Windows 7, so it'd boot automatically into Win7

But at this point are we not trying to get everything up and running?

We can adjust grub to default to W7 that is fairly easy, lets see if we can get it to boot the Ubuntu and W7 first. The grldr may be a problem here but fixable.

The grub.cfg portion of the script shows W7 so I think we are some what closer here, thanks for posting the script it just makes it more likely we can get you going, with a detailed framework of the whole setup.

Does this all make sense?

---

### Post by thenags on 2010-12-08
> **wilee-nilee said:**
> But at this point are we not trying to get everything up and running?

We can adjust grub to default to W7 that is fairly easy, lets see if we can get it to boot the Ubuntu and W7 first. The grldr may be a problem here but fixable.

The grub.cfg portion of the script shows W7 so I think we are some what closer here, thanks for posting the script it just makes it more likely we can get you going, with a detailed framework of the whole setup.

Does this all make sense?


Yep.  I'm open to try whatever.  As of right now GRUB doesn't load at all.  I'm just booting straight into Win7

---

### Post by wilee-nilee on 2010-12-08
> **thenags said:**
> Yep.  I'm open to try whatever.  As of right now GRUB doesn't load at all.  I'm just booting straight into Win7

I with you on this, per the history of grub2 and grub in general it likes being in the mbr of the Ubuntu install; which it is sde, that is why I'm trying to get you to boot from the sde drive. If you do you should see a grub menu with Ubuntu and W7, boot into Ubuntu and run in the terminal.
```
sudo update-grub
```

Then reboot the sde and try to see if W7 boots if it does even with the grldr reference then we are almost there. It is then then just modifying grub2=W7 default or using startup manager.

You have a unusual set up with the correct grub2=sde being way down the line as far as what is being read first at starting the computer. If you had set this up originally correctly you would probably of had W7 first in sda then Ubuntu. We are working with a as if situation as far as what can we do to get this working.

Are you booting straight into windows by booting the sde drive first?

---

### Post by thenags on 2010-12-08
> **wilee-nilee said:**
> I with you on this, per the history of grub2 and grub in general it likes being in the mbr of the Ubuntu install; which it is sde, that is why I'm trying to get you to boot from the sde drive. If you do you should see a grub menu with Ubuntu and W7, boot into Ubuntu and run in the terminal.
```
sudo update-grub
```Then reboot the sde and try to see if W7 boots if it does even with the grldr reference then we are almost there. It is then then just modifying grub2=W7 default or using startup manager.

You have a unusual set up with the correct grub2=sde being way down the line as far as what is being read first at starting the computer. If you had set this up originally correctly you would probably of had W7 first in sda then Ubuntu. We are working with a as if situation as far as what can we do to get this working.

**Are you booting straight into windows by booting the sde drive first?**


Right now my boot device is the 150GB hard drive which is sdd I believe.  I'll try changing it to the 80GB (sde) now and see what happens.

---

### Post by thenags on 2010-12-08
Just changed the boot device to sde and GRUB loaded right up.  I'm not in my Ubuntu install and going to do 'sudo update-grub' and try to get into Win7

---

### Post by wilee-nilee on 2010-12-08
l

---

### Post by wilee-nilee on 2010-12-08
> **thenags said:**
> Just changed the boot device to sde and GRUB loaded right up.  I'm not in my Ubuntu install and going to do 'sudo update-grub' and try to get into Win7

Do you mean you are in the Ubuntu install you only want to run the sudo update-grub from that install.

If you can't get into Ubuntu in the sde I will give you a couple of commands that should work just update where and whats going on.

---

### Post by thenags on 2010-12-08
> **wilee-nilee said:**
> Do you mean you are in the Ubuntu install you only want to run the sudo update-grub from that install.

If you can't get into Ubuntu in the sde I will give you a couple of commands that should work just update where and whats going on.


Whoops.  I'm meant I'm NOW in the Ubuntu install and about to do the next step you gave me.

---

### Post by thenags on 2010-12-08
And just booted into Windows 7 with no problems at all.

---

### Post by wilee-nilee on 2010-12-08
> **thenags said:**
> And just booted into Windows 7 with no problems at all.

So the easiest way of getting W7 as the default is by installing startup manger in Ubuntu it will allow you to put W7 as the default boot. At one time though the manager defaulted to that line chosen no matter what, so if you had a Kernel update in Ubuntu it had to be adjusted. 

So there is another way by actually modifying the grub2 set up. here is a link go to step 3. Changing Windows/Other OS Titles.
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

Now if any of this doesn't make sense just use the startup manager in Ubuntu to begin with, and post in the link for help drs305 will help you.

---

### Post by thenags on 2010-12-08
> **wilee-nilee said:**
> So the easiest way of getting W7 as the default is by installing startup manger in Ubuntu it will allow you to put W7 as the default boot. At one time though the manager defaulted to that line chosen no matter what, so if you had a Kernel update in Ubuntu it had to be adjusted. 

So there is another way by actually modifying the grub2 set up. here is a link go to step 3. Changing Windows/Other OS Titles.
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

Now if any of this doesn't make sense just use the startup manager in Ubuntu to begin with, and post in the link for help drs305 will help you.


Startup Manager worked great and everything is good to go now.

Thanks a ton for all the help!

---

### Post by wilee-nilee on 2010-12-08
> **thenags said:**
> Startup Manager worked great and everything is good to go now.

Thanks a ton for all the help!

No problem, my pleasure.;)

---

