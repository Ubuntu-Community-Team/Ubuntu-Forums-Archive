---
title: "triple boot problems"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by jonnym2008 on 2011-05-09
Hello

First I'm a Ubuntu newbie so be gentle, I've been trailing it on a USB stick and Wow I'm blown away.

I've got Windows XP 32-bit on my primary drive and Windows 7 64-bit duel booted on my slave drive.  I've installed Ubuntu 11.04 using " install alongside Windows 7" Option.  So Im not sure where it installed to.

I rebooted as per instructions but I got the win7 boot file is corrupt error and no sign of Ubuntu.  I then used the win7 disk to repair it.  I can't find Ubuntu on the disk looking for it using windows7 and I can't boot to it.

Using the Ubuntu USB stick again I chose install, it recognises that that Ubuntu is there and gives me options none of which help.  I've tried reinstalling it which didn't help.

Would uninstalling Ubuntu and reinstalling it on a partition which I've created help cure it?  If so how do I go about it?
Or is there any other advice to get it working as is?

Thanks for any help

Jonnym2008

---

### Post by wilee-nilee on 2011-05-09
> **jonnym2008 said:**
> Hello

First I'm a Ubuntu newbie so be gentle, I've been trailing it on a USB stick and Wow I'm blown away.

I've got Windows XP 32-bit on my primary drive and Windows 7 64-bit duel booted on my slave drive.  I've installed Ubuntu 11.04 using " install alongside Windows 7" Option.  So Im not sure where it installed to.

I rebooted as per instructions but I got the win7 boot file is corrupt error and no sign of Ubuntu.  I then used the win7 disk to repair it.  I can't find Ubuntu on the disk looking for it using windows7 and I can't boot to it.

Using the Ubuntu USB stick again I chose install, it recognises that that Ubuntu is there and gives me options none of which help.  I've tried reinstalling it which didn't help.

Would uninstalling Ubuntu and reinstalling it on a partition which I've created help cure it?  If so how do I go about it?
Or is there any other advice to get it working as is?

Thanks for any help

Jonnym2008

So when you install Ubuntu, and you want the Grub bootloader to work it is a real pain if put on a slave, maybe not a workable situation. This being said follow this and post the bootscript.

So from a booted live Ubuntu cd, thumbdrive, or Ubuntu installation lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

When you install XP then W7 the boot of the MS are intertwined, so your still booting off the master, probably, and getting a MS boot gui for a choice of XP or W7.

So you can't just insert the grub bootloader to the mbr in the master HD without the Ubuntu installation there as well and have stability generally.

If your in good shape as far as everything is installed, an the grub=Ubuntu's bootloader is in the slave mbr=master boot record, this may be a case for the use of the easybcd bootloader to call to the slaves mbr to show the grub menu, not sure, and know zero about easybcd.

Post the script and we will see the locals who know comment I suspect. Be sure to use the code tags as described or look in my signature for a manual wrapping of the text when posted.

---

### Post by jonnym2008 on 2011-05-09
Thanks for the help.  Here is the info you requested.

I hope it helps!

Jonnym2008

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks for b2can.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

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
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   874,353,689   874,353,627   7 HPFS/NTFS
/dev/sda2         874,353,690   976,768,064   102,414,375   f W95 Ext d (LBA)
/dev/sda5         874,353,753   976,768,064   102,414,312   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63 1,890,605,504 1,890,605,442   7 HPFS/NTFS
/dev/sdb2       1,890,607,102 1,953,523,711    62,916,610   5 Extended
/dev/sdb5       1,945,139,200 1,953,523,711     8,384,512  82 Linux swap / Solaris
/dev/sdb6       1,890,607,104 1,936,752,639    46,145,536  83 Linux
/dev/sdb7       1,936,754,688 1,945,135,103     8,380,416  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        8E04C37C04C36635                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        1578AFC0161DACB9                       ntfs       backup                        
/dev/sda: PTTYPE="dos" 
/dev/sdb1        322CC21C2CC1DB4D                       ntfs       Windows7                      
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        e139c63b-d3a9-4ade-85e2-0379bada33e9   swap                                     
/dev/sdb6        ff93f39f-648a-4fb2-9906-6e7cea3ef29d   ext4                                     
/dev/sdb7        2e2861d9-8a56-4350-b4d5-3e57465e7d27   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        A2A4D0CDA4D0A557                       ntfs       BackUp                        
/dev/sdc: PTTYPE="dos" 
/dev/sdd         D465-6DE4                              vfat       PENDRIVE                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdd         /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT /USEPMTIMER

=========================== sdb6/boot/grub/grub.cfg: ===========================

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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sdc,msdos6)'
search --no-floppy --fs-uuid --set=root ff93f39f-648a-4fb2-9906-6e7cea3ef29d
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sdc,msdos6)'
search --no-floppy --fs-uuid --set=root ff93f39f-648a-4fb2-9906-6e7cea3ef29d
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos6)'
	search --no-floppy --fs-uuid --set=root ff93f39f-648a-4fb2-9906-6e7cea3ef29d
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=ff93f39f-648a-4fb2-9906-6e7cea3ef29d ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos6)'
	search --no-floppy --fs-uuid --set=root ff93f39f-648a-4fb2-9906-6e7cea3ef29d
	echo	'Loading Linux 2.6.38-8-generic-pae ...'
	linux	/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=ff93f39f-648a-4fb2-9906-6e7cea3ef29d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos6)'
	search --no-floppy --fs-uuid --set=root ff93f39f-648a-4fb2-9906-6e7cea3ef29d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sdc,msdos6)'
	search --no-floppy --fs-uuid --set=root ff93f39f-648a-4fb2-9906-6e7cea3ef29d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sdb,msdos1)'
	search --no-floppy --fs-uuid --set=root 8E04C37C04C36635
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

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdc6       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc7 during installation
UUID=2e2861d9-8a56-4350-b4d5-3e57465e7d27 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb6: Location of files loaded by Grub: ===================


 976.7GB: boot/grub/core.img
 989.8GB: boot/grub/grub.cfg
 969.2GB: boot/initrd.img-2.6.38-8-generic-pae
 968.6GB: boot/vmlinuz-2.6.38-8-generic-pae
 969.2GB: initrd.img
 968.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdd

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  00 98 77 00 d8 1d 00 00  00 00 00 00 02 00 00 00  |..w.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 e4 6d 65 d4 4e  4f 20 4e 41 4d 45 20 20  |..).me.NO NAME  |
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
00000110  c6 06 45 7d 00 66 b8 d8  3b 00 00 66 ba 00 00 00  |..E}.f..;..f....|
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



```

---

### Post by jonnym2008 on 2011-05-09
I've tried to update the boot record using EasyBCD.  I added a new entry, selected the Linux/BSD tab, selected Type: GRUB(legacy) and Device: Partition 3(Linux-22 GiB), I didn't select the tick box "GRUB isn't installed to MBR/bootsector"

The option appeared in the boot menu but on clicking I just got a flashing cursor line on a black screen.  So back to you guys, I'm running out of ideas.

thanks for your help

Jonnym2008

---

### Post by wilee-nilee on 2011-05-09
Lets have the others look at this for advice disregard the first post, I left here, lets be safe here.

---

### Post by jonnym2008 on 2011-05-09
OK no worries.  
I've found the installation on the Windows7 HDD.  I had shrunk the volume by 30GB to allow the install and it seems to have used the space making a 22GB partition and 2x 4gb partitions.

I see from the below excerpt from the Boot info above that grub is installed.
 "sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img"


I wonder if I should be using Grub2 in EasyBCD as it also says" Grub 2 is installed in the MBR of /dev/sdb and looks for b2can."


I'm grasping at straws with too little knowledge :oops:

thanks again 

Jonnym2008

---

### Post by wilee-nilee on 2011-05-09
> **jonnym2008 said:**
> OK no worries.  
I've found the installation on the Windows7 HDD.  I had shrunk the volume by 30GB to allow the install and it seems to have used the space making a 22GB partition and 2x 4gb partitions.

I see from the below excerpt from the Boot info above that grub is installed.
 "sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img"


I wonder if I should be using Grub2 in EasyBCD as it also says" Grub 2 is installed in the MBR of /dev/sdb and looks for b2can."


I'm grasping at straws with too little knowledge :oops:

thanks again 

Jonnym2008

Yes grub is installed in the Ubuntu system, and the sdb mbr, have you tried to boot from the sdb drive? This can be done by putting the sdb ahead of the sda in the bios or with a key prompt at powering on like you would do to get to the bios, my per session boot key for a menu is f12 yours may be the same or different. Booting a Ubunntu cd will tell you this at the bottom of the screen, goes by fast though.

---

### Post by jonnym2008 on 2011-05-09
I’ve got it working!  in fact this entry is the very first thing I have done on an installed Ubuntu!!!

Proof that a good substitute for brains is brute force and ignorance.  Mostly ignorance and trying every combination possible.

Using Grub2 rather than grub (legacy) in EasyBCD.

heres what I did: Using EasyBCD. I added a new entry, selected the Linux/BSD tab, selected Type: GRUB2 and Device: Partition 3(Linux-22 GiB)

Bobs your uncle...and Fannys your aunt:P


thanks for your help, without boot info I couldn’t have worked it out

Jonnym2008

---

### Post by wilee-nilee on 2011-05-09
> **jonnym2008 said:**
> I’ve got it working!  in fact this entry is the very first thing I have done on an installed Ubuntu!!!

Proof that a good substitute for brains is brute force and ignorance.  Mostly ignorance and trying every combination possible.

Using Grub2 rather than grub (legacy) in EasyBCD.

heres what I did: Using EasyBCD. I added a new entry, selected the Linux/BSD tab, selected Type: GRUB2 and Device: Partition 3(Linux-22 GiB)

Bobs your uncle...and Fannys your aunt:P


thanks for your help, without boot info I couldn’t have worked it out

Jonnym2008

You are so awesome, now stick around to help those user's who use easybcd, not many of us are familiar with it.;)

Check as well if booting from the sdb uses grub correctly, if so you have a back up to get you into all the OS's if there is a problem from booting from the sda.

---

### Post by jonnym2008 on 2011-05-09
I’m such a nub I don’t even know what sdb and sda are!

---

### Post by Quackers on 2011-05-09
/dev/sda is your 500GB hard drive and /dev/sdb is your 1TB hard drive. Wilee-nilee's last suggestion (to change the boot order in your bios so that sdb boots before sda) was a good one, and may have done the job. But as everything is now working I'm sure you're happy as it is :-)

---

### Post by jonnym2008 on 2011-05-10
Ahhh makes sense now.  I'm going to leave it as is...if it aint broken don't fix it.  

Thanks

Jonnym2008

---

