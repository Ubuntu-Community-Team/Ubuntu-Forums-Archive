---
title: "XP/Ubuntu dual boot install fails with BSOD (bear with me please)"
date: 2010-09-27
forum: Installation &amp; Upgrades
---

### Post by welshmike on 2010-09-27
BSOD STOP: 0X0000007B installing XP prior to installing dual boot XP/Ubuntu.

I purchased a Novatech i3 notebook with no operating system installed.
It has a SATA HDD.
On booting Ubuntu 10.04 from my live USB flash drive I noticed that the notebook's HDD contained a FreeDOS partition.

   1. I ran GParted to delete the HDD partition containing FreeDOS leaving an empty 250GB HDD.
   2. I then created as the first partition a primary 30GB NTFS for XP installation
   3. In the remaining space I created an extended partition and within it two near equal size partitions of about 120GB each. The first I formatted as ext4 and the second as NTFS.
   4. I deleted the above ext4 partition so I could assign that free space for the Ubuntu installation.
   5. I started to install XP from a CD and after a while the install crashed with a BSOD STOP: 0X0000007B.

I have since successfully installed Ubuntu 10.04 but would like to start again and install XP then Ubuntu.

Please does anyone know how I proceed?

---

### Post by ipatfrmww on 2010-09-27
I would say that it is just that, start again. Maybe you need a fully blank hard drive before you do the XP install (although you shouldn't NEED to)

Resize the XP partition after the install and make partitions with gparted later instead.

Don't rely on windows to understand the partition table, it might be an error related to your hardware and windows though or it could have been bad luck, BSOD isn't a very common thing for XP to experience so it was probably just having a bad day.

---

### Post by welshmike on 2010-09-27
> **ipatfrmww said:**
> I would say that it is just that, start again. Maybe you need a fully blank hard drive before you do the XP install (although you shouldn't NEED to)

Resize the XP partition after the install and make partitions with gparted later instead.

Don't rely on windows to understand the partition table, it might be an error related to your hardware and windows though or it could have been bad luck, BSOD isn't a very common thing for XP to experience so it was probably just having a bad day.

Thanks ipatfrmww,

I used GParted to delete all the partitions leaving a blank hard drive.
1. Same BSOD on trying to install XP. 
2. Booting Partition Magic CD gives: 
NO DRIVES ARE ATTACHED, OR DRIVES ARE POWERED DOWN
THE DEVICE DRIVER IS NOT INSTALLED.
3. When booting from Acronis True Image 11 Home CD the backup creation Wizard does not show my netbook's hard drive.
4. When booting from the hard drive I get 
error: no partition
grub rescue>
This does not recognise any grub commands.

---

### Post by Rubi1200 on 2010-09-27
I would start troubleshooting the problem by running memtest from the Ubuntu CD.

Also, whilst on the LiveCD please post the results of the bootscript linked at the bottom of my post.

Thanks.

---

### Post by Mark Phelps on 2010-09-27
You specifically mentioned SATA drives, therefore, go into your BIOS, and if the SATA setting says AHCI, change it to COMPATIBILITY MODE.  Reboot.

That has been known to fix the "7B" BSOD problems on some XP PCs.

---

### Post by welshmike on 2010-09-27
> **Rubi1200 said:**
> I would start troubleshooting the problem by running memtest from the Ubuntu CD.

Also, whilst on the LiveCD please post the results of the bootscript linked at the bottom of my post.

Thanks.

Thanks for reply.

I already went ahead and installed just Ubuntu. 

Sorry, I wasn't given memtest option when about to boot from live USB flash drive.

bootscript results:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
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

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb1 has 
                       976770080 sectors, but according to the info from 
                       fdisk, it has 976784066 sectors.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,046   283,594,751   283,592,706   5 Extended
/dev/sda5               2,048   272,379,903   272,377,856  83 Linux
/dev/sda6         272,381,952   283,594,751    11,212,800  82 Linux swap / Solaris
/dev/sda2         283,595,445   488,392,064   204,796,620   7 HPFS/NTFS
/dev/sda3          69,802,425   488,392,064   418,589,640   0 Empty

/dev/sda1 overlaps with /dev/sda3
/dev/sda5 overlaps with /dev/sda3
/dev/sda6 overlaps with /dev/sda3
/dev/sda2 overlaps with /dev/sda3

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   976,784,129   976,784,067   7 HPFS/NTFS

/dev/sdb1 ends after the last sector of /dev/sdb

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1: PTTYPE="dos" 
/dev/sda2        7CF7CB4334F17E0E                       ntfs       Data                          
/dev/sda5        71b498bd-d621-4d83-87dd-2f14b97a43a6   ext4                                     
/dev/sda6        8774472e-a30e-4966-ad56-8d61be633db1   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0A8056108056031D                       ntfs       500GBFreecm                   
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/500GBFreecm       fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set 71b498bd-d621-4d83-87dd-2f14b97a43a6
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
search --no-floppy --fs-uuid --set 71b498bd-d621-4d83-87dd-2f14b97a43a6
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
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 71b498bd-d621-4d83-87dd-2f14b97a43a6
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=71b498bd-d621-4d83-87dd-2f14b97a43a6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 71b498bd-d621-4d83-87dd-2f14b97a43a6
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=71b498bd-d621-4d83-87dd-2f14b97a43a6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 71b498bd-d621-4d83-87dd-2f14b97a43a6
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=71b498bd-d621-4d83-87dd-2f14b97a43a6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 71b498bd-d621-4d83-87dd-2f14b97a43a6
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=71b498bd-d621-4d83-87dd-2f14b97a43a6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 71b498bd-d621-4d83-87dd-2f14b97a43a6
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 71b498bd-d621-4d83-87dd-2f14b97a43a6
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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
UUID=71b498bd-d621-4d83-87dd-2f14b97a43a6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=8774472e-a30e-4966-ad56-8d61be633db1 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 105.3GB: boot/grub/core.img
  37.0GB: boot/grub/grub.cfg
 105.4GB: boot/initrd.img-2.6.32-21-generic
  33.3GB: boot/initrd.img-2.6.32-25-generic
 105.3GB: boot/vmlinuz-2.6.32-21-generic
 105.3GB: boot/vmlinuz-2.6.32-25-generic
  33.3GB: initrd.img
 105.4GB: initrd.img.old
 105.3GB: vmlinuz
 105.3GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  59 65 a8 1d b4 52 d0 7b  ad c9 9e ff ce 8b 2c 96  |Ye...R.{......,.|
00000010  7d c4 68 00 16 11 ba 86  b4 e1 c1 de e9 c2 39 6c  |}.h...........9l|
00000020  38 08 3d 55 59 30 c7 e7  d8 2f a5 4d 26 9a 63 f6  |8.=UY0.../.M&.c.|
00000030  5d 34 62 5c 75 7c 73 31  72 e3 ab fa a0 35 69 6d  |]4b\u|s1r....5im|
00000040  b5 da f9 60 26 d2 a4 f0  07 3e 73 97 41 21 c9 6e  |...`&....>s.A!.n|
00000050  7d 04 96 76 6e c1 b9 82  d3 33 f6 87 ef 58 3c f2  |}..vn....3...X<.|
00000060  51 e5 08 45 9e 72 f5 27  02 02 b4 aa 6e 31 7e 81  |Q..E.r.'....n1~.|
00000070  32 29 e7 8c 96 3d 81 57  0f df 60 49 b4 17 91 36  |2)...=.W..`I...6|
00000080  c8 e0 5e 54 b8 b7 0f 86  25 b7 ba 4d f2 f7 5f c4  |..^T....%..M.._.|
00000090  5a f3 95 2e b0 b5 72 d2  fa f7 60 f5 e4 fe cc 28  |Z.....r...`....(|
000000a0  f1 58 99 67 b1 39 52 b6  b6 94 46 3c f8 2e f8 22  |.X.g.9R...F<..."|
000000b0  e6 74 9a 15 71 3e 65 49  ba 75 72 8c 59 f8 77 7a  |.t..q>eI.ur.Y.wz|
000000c0  af 56 c5 51 11 7e c1 77  f2 38 b0 06 ae 39 e9 6f  |.V.Q.~.w.8...9.o|
000000d0  5c 7a 71 70 bb 04 e5 e9  5f 8b 36 b5 fa 10 00 3d  |\zqp...._.6....=|
000000e0  c8 ef f7 ab 6e 37 98 16  c9 dc 2e 10 6a db 37 bf  |....n7......j.7.|
000000f0  1c 0e 32 e6 5d 53 84 93  90 27 f1 96 9a be 88 5c  |..2.]S...'.....\|
00000100  b5 f9 3e 74 6f 4f 2b 5f  f2 c4 cc ce 82 c7 10 95  |..>toO+_........|
00000110  ff b5 14 3e 63 39 0a 18  7f 6b 98 af b7 c2 17 e3  |...>c9...k......|
00000120  9f fe ac 22 a3 05 29 b3  e3 f4 25 13 3b b7 e7 f1  |..."..)...%.;...|
00000130  af 34 cb 89 e7 24 e5 54  fe da 28 44 2d 12 50 9e  |.4...$.T..(D-.P.|
00000140  01 a9 f3 8f 9d 29 49 b3  ac df c3 1d 20 d7 5c 64  |.....)I..... .\d|
00000150  be 9f c9 e1 dc b8 a6 d7  fb fb 67 73 0c 41 e2 fc  |..........gs.A..|
00000160  b1 0a 13 87 09 ad 17 a0  54 19 81 c1 2e ae c1 b1  |........T.......|
00000170  42 85 4d ec b4 5e 60 50  3a 78 ef 46 4d a6 81 99  |B.M..^`P:x.FM...|
00000180  c6 be 8d 5d 5b 1c 01 11  42 d1 5c 95 43 cd f8 b1  |...][...B.\.C...|
00000190  a5 0e d3 ca 95 3a e4 61  98 e6 e8 ad 93 88 34 b6  |.....:.a......4.|
000001a0  11 4f 0b 5a 23 62 9a 11  d5 b7 e3 30 ec 71 6c a5  |.O.Z#b.....0.ql.|
000001b0  68 ce 15 dd 17 77 39 ab  21 c9 ca c8 4d 35 12 0a  |h....w9.!...M5..|
000001c0  8f f1 9c 74 1e e1 6e 27  80 8c 62 9f da 2a b4 ec  |...t..n'..b..*..|
000001d0  ff 77 7b d1 dd 05 fd 2c  23 6f 5a de e5 a1 fd 49  |.w{....,#oZ....I|
000001e0  75 d5 e0 96 91 6d 56 5a  cf 67 34 3e cd 07 f3 34  |u....mVZ.g4>...4|
000001f0  a3 a7 e1 3f e3 ce c7 96  c9 33 e0 49 45 73 8c 21  |...?.....3.IEs.!|
00000200


```

---

### Post by welshmike on 2010-09-27
> **Mark Phelps said:**
> You specifically mentioned SATA drives, therefore, go into your BIOS, and if the SATA setting says AHCI, change it to COMPATIBILITY MODE.  Reboot.

That has been known to fix the "7B" BSOD problems on some XP PCs.

Thanks for your helpful reply.

I set AHCI to Disabled and XP install gets past the point of BSOD. So I'm hopeful that XP will install. I will now need to repartition my HDD and start again (edit: Oh no! a wasted 55 minutes while XP installs and then there's SP3, Windows updates and a couple of legacy apps to install. OTOH Ubuntu 10.04 installed before in 15 minutes).
Acronis True Image 11 Bootable CD Home still does not recognise my notebooks HDD. I'll run that again once XP is installed.

---

### Post by Rubi1200 on 2010-09-27
I would try starting over again because of the new setting as suggested above. Install Windows first and then Ubuntu.

If you run into problems either ask or run the bootscript again and post it here.

Good luck!

---

### Post by welshmike on 2010-09-27
> **Rubi1200 said:**
> I would try starting over again because of the new setting as suggested above. Install Windows first and then Ubuntu.

If you run into problems either ask or run the bootscript again and post it here.

Good luck!

Thanks for the encouragement. XP installing now, started 28 minutes ago (at 15:40), 23 minutes left to go. ZZZZZ.
(16:45) Oh! and now its all those eight MSi drivers to install for XP. They all all there in Ubuntu.
(17:40) Drivers installed.

---

### Post by Mark Phelps on 2010-09-27
> **welshmike said:**
> Acronis True Image 11 Bootable CD Home still does not recognise my notebooks HDD. I'll run that again once XP is installed.


Recognizing that this is NOT an Acronis support forum ... nonetheless, that does surprise me.

The default ATI Home boot CD is actually a Linux disk (forget which distro, but it's NOT Ubuntu), and it should be able to recognize SATA drives.

Did you try booting from it again AFTER you disable AHCI?

---

### Post by welshmike on 2010-09-27
> **Mark Phelps said:**
> Recognizing that this is NOT an Acronis support forum ... nonetheless, that does surprise me.

The default ATI Home boot CD is actually a Linux disk (forget which distro, but it's NOT Ubuntu), and it should be able to recognize SATA drives.
Did you try booting from it again AFTER you disable AHCI?

(This from my Novatech i3 dual boot XP/Ubuntu).

With AHCI enabled ATI does not recognise my internal HDD or external (backup) HDD. Ubuntu boots, XP does not.
With AHCI disabled ATI recognises only my external HDD. Ubuntu boots, XP boots.

---

### Post by Rubi1200 on 2010-09-28
> **welshmike said:**
> (This from my Novatech i3 dual boot XP/Ubuntu).

With AHCI enabled ATI does not recognise my internal HDD or external (backup) HDD. Ubuntu boots, XP does not.
With AHCI disabled ATI recognises only my external HDD. Ubuntu boots, XP boots.
So, are you saying the problem is resolved? It seems that way. Let us know if you need more help with anything.

---

### Post by welshmike on 2010-09-28
> **Rubi1200 said:**
> So, are you saying the problem is resolved? It seems that way. Let us know if you need more help with anything.

Thanks. Everyone has been a great help.

The problem with ATI remains unsolved because when running from its boot CD it does not recognise my notebook's HDD. 
So I cannot recover a system true image backup unless I do it from XP by running the ATI app.

---

### Post by Rubi1200 on 2010-09-28
What about looking into Clonezilla?
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by welshmike on 2010-09-28
Thanks. I had a look at Clonezilla a while ago. I will have a look again.

---

### Post by welshmike on 2010-09-28
I bit off thread but here's feedback to the helpful team.

I've now run Clozilla from a live CD and am impressed:

It took 12 minutes to save an image of my notebook's 250GB HDD of which 20GB is used.
The saved image on my 500GB external USB HDD was 12GB.

One small point. The name of the directory that I created to hold the image could not contain spaces as Clonezilla would not recognise it.
In my case name Backups - Clonezilla was not recognised, Backups-Clonezilla was.

---

### Post by Acronis Support on 2010-09-28
Hi all!

**welshmike**, I'm glad to know you got the issue solved, but just wanted to add for future: 
it's highly possible that the issue was caused by the lack of drivers on the original media. We have a solution for it: all you need to do is download the updated ISO from your account (please note that you should have a product registered) as described in this [KB article]("http://kb.acronis.com/content/4828"). 

After that just burn the ISO onto the CD with the help of any suitable software and boot your machine from it. This should fix the problem. 

Should you need anything else or have any further questions - feel free to contact us at your earliest convenience, we will be happy to help you! You can always contact us [directly]("http://kb.acronis.com/content/8153") or via [Forum]("http://forum.acronis.com/"). 

Thank you!

-- 
Best regards
Yana | Acronis Support Professional
Acronis Customer Central

---

