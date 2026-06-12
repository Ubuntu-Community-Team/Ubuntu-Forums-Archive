---
title: "Repairing Windows 7 boot after Ubuntu 10.10 install"
date: 2010-11-05
forum: Installation &amp; Upgrades
---

### Post by teddykgb715 on 2010-11-05
Hi all,

I've read various threads on this after googling, including one on this site, but I haven't found one that addresses my specific issue.

I had Windows 7 installed on an SSD. I wanted to try Ubuntu so I created a partition for it on the SSD and booted with the live CD to install Ubuntu. Went through the install and somehow Ubuntu carved out another partition on the SSD rather than using the one I had already created. Windows 7 would then not boot but Ubuntu would.

I booted with my 7 cd and ran the automatic startup repair, it didn't find any problems. I then ran the bootsect command on the drive with 7. It said it repaired the bootmgr but Windows still would not boot and now Ubuntu won't either.

I read somewhere else that it may be due to the partition that 7 was on being changed during the install. I don't care about the Ubuntu installation but I don't want to lose the 7 install, can I delete the ubuntu partition through booting with the 7 cd? Will that do any good?

Thank you all! I'm stumped even though I've done startup repairs before, just not after Ubuntu install.

---

### Post by coffeecat on 2010-11-05
> **teddykgb715 said:**
> I had Windows 7 installed on an SSD. I wanted to try Ubuntu so I created a partition for it on the SSD and booted with the live CD to install Ubuntu. Went through the install and somehow Ubuntu carved out another partition on the SSD rather than using the one I had already created.

Did you create the extra partition from Windows? If so, that would have been formatted NTFS which is no good for Linux. When you got to the partitioning stage of the installer, if you had chosen 'manual/advanced' you would have been able to reformat and use that partition. The installer did its best in the circumstances and, besides, it needed to create a separate swap partition as well as a root partition for Ubuntu. 

> **teddykgb715 said:**
>  Windows 7 would then not boot but Ubuntu would.

That might have been easily fixed before you tried to do a repair with the Windows 7 disc.

> **teddykgb715 said:**
> can I delete the ubuntu partition through booting with the 7 cd? Will that do any good?

Hold off. That could do more harm than good until we've ascertained the situation.

Here's what to do. Boot up with the Ubuntu live CD, make sure you are connected to the internet and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the script and post the contents of the RESULTS.txt file. **Please** enclose the file in code tags with the # button otherwise it will be ureadable.

That will give us all the information we need, including your partition layout. When posting please tell us whether you want to revert to Windows or try to get a Windows/Ubuntu dual-boot out of whatever is there together with a working dual-boot grub menu.

---

### Post by teddykgb715 on 2010-11-05
Thank you, I am heading out of town this weekend so I'll do this next week and report back.  I appreciate the help, I realized I was a bit hasty in my repair efforts.

---

### Post by coffeecat on 2010-11-05
I have this thread subscribed, so I'll be notified when there's another post to it. I'll look forward to reading the RESULTS.txt file next week.

Regards.

---

### Post by teddykgb715 on 2010-11-09
I believe I pasted this correctly.  Please let me know.  And to answer your question, I do like Ubuntu and would like to use it more so the ultimate goal would be to dual boot with Windows 7 and Ubuntu.  I don't want to reinstall Windows, but it's fine if I need to reinstall Ubuntu.  Whatever the easiest way to get there is.

Thank you SO MUCH for the assistance.  I really appreciate it.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /Boot/BCD

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sde3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sde5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sde6: _________________________________________________________________________

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

/dev/sda1               2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb2    *         16,065   976,768,064   976,752,000   5 Extended
/dev/sdb5              16,128   976,768,064   976,751,937   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048 3,907,026,943 3,907,024,896   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *          2,048   976,771,071   976,769,024   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *          2,048    85,457,415    85,455,368   7 HPFS/NTFS
/dev/sde3          85,458,942   104,562,687    19,103,746   5 Extended
/dev/sde5    *     85,458,944   103,647,231    18,188,288  83 Linux
/dev/sde6         103,649,280   104,562,687       913,408  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        72567CF0567CB687                       ntfs       Movies                        
/dev/sda: PTTYPE="dos" 
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        404DD8AF4E3A35BD                       ntfs       Movies                        
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        5A3857F13857CAA1                       ntfs       Movies                        
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        745EBC105EBBC8DE                       ntfs                                     
/dev/sdd: PTTYPE="dos" 
/dev/sde1        66F4B2F5F4B2C699                       ntfs                                     
/dev/sde3: PTTYPE="dos" 
/dev/sde5        ac721989-971a-42fb-ab41-49b953380539   ext4                                     
/dev/sde6        01958c2f-2771-46ba-90ba-cccba18ebebe   swap                                     
/dev/sde: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        /media/745EBC105EBBC8DE  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sde5/boot/grub/grub.cfg: ===========================

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
set default="4"
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
set root='(hd4,msdos5)'
search --no-floppy --fs-uuid --set ac721989-971a-42fb-ab41-49b953380539
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd4,msdos5)'
search --no-floppy --fs-uuid --set ac721989-971a-42fb-ab41-49b953380539
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
    set root='(hd4,msdos5)'
    search --no-floppy --fs-uuid --set ac721989-971a-42fb-ab41-49b953380539
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=ac721989-971a-42fb-ab41-49b953380539 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd4,msdos5)'
    search --no-floppy --fs-uuid --set ac721989-971a-42fb-ab41-49b953380539
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=ac721989-971a-42fb-ab41-49b953380539 ro single 
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
    set root='(hd4,msdos5)'
    search --no-floppy --fs-uuid --set ac721989-971a-42fb-ab41-49b953380539
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd4,msdos5)'
    search --no-floppy --fs-uuid --set ac721989-971a-42fb-ab41-49b953380539
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sde1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd4,msdos1)'
    search --no-floppy --fs-uuid --set 66f4b2f5f4b2c699
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

=============================== sde5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sde5 during installation
UUID=ac721989-971a-42fb-ab41-49b953380539 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sde6 during installation
UUID=01958c2f-2771-46ba-90ba-cccba18ebebe none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sde5: Location of files loaded by Grub: ===================


  48.6GB: boot/grub/core.img
  44.0GB: boot/grub/grub.cfg
  45.6GB: boot/initrd.img-2.6.35-22-generic
  45.4GB: boot/vmlinuz-2.6.35-22-generic
  45.6GB: initrd.img
  45.4GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sde3

00000000  53 74 ab 80 3d 22 cc 96  37 4a 48 4e 36 6d d3 d5  |St..="..7JHN6m..|
00000010  a1 ea 36 24 8a b9 d6 48  11 e5 40 c9 37 71 bc a9  |..6$...H..@.7q..|
00000020  bd b4 7c e8 8b 01 58 cf  26 43 c8 30 7b 4e c6 99  |..|...X.&C.0{N..|
00000030  b4 17 e9 49 33 71 c4 49  ca a4 0d f4 bd 8e 7c 2d  |...I3q.I......|-|
00000040  29 63 c0 53 e5 90 d7 64  99 b5 a6 10 5f 75 cf 64  |)c.S...d...._u.d|
00000050  0f cd 2a 01 e3 c8 ac b2  24 71 0d c8 bb 30 70 7f  |..*.....$q...0p.|
00000060  e0 f1 ce 69 ec 07 68 7a  bb 97 ac 27 34 c4 09 3b  |...i..hz...'4..;|
00000070  98 0e c6 b1 a8 04 0c ad  e1 08 ab 28 40 ed 3a 55  |...........(@.:U|
00000080  79 49 2d fb b4 16 99 8e  5b b8 e6 c2 8d f2 28 9b  |yI-.....[.....(.|
00000090  b3 5b 5e c9 dd 95 71 78  e9 ca f1 ce 68 0d b9 f0  |.[^...qx....h...|
000000a0  f0 d6 35 8c 72 66 39 c8  2d f5 f3 df d5 c8 72 11  |..5.rf9.-.....r.|
000000b0  b1 48 bf c5 d5 0b a6 29  ad 6b 4a 8b dd cb 4d 4e  |.H.....).kJ...MN|
000000c0  e5 fb d3 65 fa 7e ba ff  f1 b5 c9 b1 c1 56 31 8b  |...e.~.......V1.|
000000d0  f1 a7 c1 db 80 88 f7 5d  e7 0c 8b a3 48 e8 99 a3  |.......]....H...|
000000e0  fa 69 cd b4 48 e1 c9 09  15 d3 4b 89 ed 36 24 68  |.i..H.....K..6$h|
000000f0  a5 6f 90 ad 85 88 72 7a  fa cf d2 ed 4b 78 a8 d6  |.o....rz....Kx..|
00000100  8c 47 09 85 41 72 cb a7  a9 09 c8 57 49 cc 19 d3  |.G..Ar.....WI...|
00000110  66 d8 d9 fd c5 d6 36 a9  ca 62 be 6e 09 bf db ed  |f.....6..b.n....|
00000120  cc 5c cf b0 4f ba 44 d4  39 d5 40 3c 91 49 3f 45  |.\..O.D.9.@<.I?E|
00000130  c8 b1 d4 61 15 aa 89 d7  c8 c1 c9 b4 9c c2 c6 4c  |...a...........L|
00000140  11 cf 19 21 90 f7 12 35  91 7e f8 61 94 58 64 d9  |...!...5.~.a.Xd.|
00000150  9f a9 ce cb a9 95 36 23  5c 9e 78 29 d8 0b a9 c6  |......6#\.x)....|
00000160  a7 32 07 f3 49 1d 2e b9  de 17 09 c8 be 7b f3 2b  |.2..I........{.+|
00000170  c7 ee 1c 8a 0b 61 3d ea  e1 5b 8e af 16 53 f4 4e  |.....a=..[...S.N|
00000180  66 08 1b 0b c6 fe be df  cf 34 9c 93 47 02 df b2  |f........4..G...|
00000190  2a 09 1f f4 2a 45 ac 71  96 ca 08 29 d9 40 47 35  |*...*E.q...).@G5|
000001a0  36 70 0d 8c 0d 98 65 e9  cc 79 48 dc cb d3 b1 99  |6p....e..yH.....|
000001b0  c9 37 6c f8 d5 99 b7 f3  27 63 c9 d6 89 a1 80 fe  |.7l.....'c......|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 88 15 01 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 88  15 01 00 f8 0d 00 00 00  |................|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by coffeecat on 2010-11-09
I'm a bit too tired at the moment to be able to be sure I'm not missing something, so I'll limit myself to a couple of questions/comments and come back to this later.

Your SSD with Windows 7 would seem to be the 64GB sde. Which would (probably) be the fifth drive attached to the motherboard. The script results tell us that the Windows MBR has been restored to the mbr of sde and the Windows C: partition at sde1 seems to have the correct boot files in the boot sector. All as a result of your running bootrec.exe from the W7 repair disc, I guess. You did mean bootrec and not bootsect?

All of which, in theory, means that W7 should boot from sde. Question: is the sde SSD drive set in the BIOS to be the first boot disc? Because I notice that the Windows mbr is also on drives sda, sdc and sdd, and if any of them have a higher boot priority in the BIOS that could lead to problems.

Even though you have an Ubuntu installation on sde, I think it would be good strategy to see if we can get Windows booting with the Windows mbr before attempting to re-install grub. Someone might suggest reinstalling grub in order to dual-boot, but I think that would be a bad idea at the moment, at least until we can prove that Windows is bootable. There may be other reasons other than boot sector ones for it not booting.

---

### Post by wilee-nilee on 2010-11-09
Let us know if you put the sde drive first to boot does it boot W7?

---

### Post by teddykgb715 on 2010-11-09
Hi guys,

Thank you for the suggestions.  I never changed the bios from when I just had Windows 7 installed but I went into to double-check.  The SSD drive is set as drive one in the bios and is set to boot after the cd drive.

If I remove the cd and let it boot from the SSD it just brings up a cursor on a blank screen.  Prior to running the windows repair, it did bring up the GRUB boot menu, but when I selected the Windows 7 install it would not boot it.  Now the GRUB menu does not come up anymore.

And I did mean bootsect, not bootrec, as I found that in another thread.  Should I try bootrec?

Thanks guys.

---

### Post by wilee-nilee on 2010-11-09
Put the sde first in line in the bios. Also there is a key prompt per session like getting to the bios that actually brings up another boot from menu that you choose using the arrow keys. Mine is f12 it could be esc or another on your setup try the key prompt at power up to try and boot that actual sde HD.

As it is you wont see grub because you have the MS bootloader in the mbr master boot record. What I think coffecat and myself are doing here is making sure windows boots as normal before reloading grub. Reloading grub is fairly easy.

You also have bootflags on other partitions,shouldn't be a problem but may be in the sdd1 drive having one, and Ubuntu they are highlighted.

```
**/dev/sdd1**   ** ***          2,048   976,771,071   976,769,024   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *          2,048    85,457,415    85,455,368   7 HPFS/NTFS
/dev/sde3          85,458,942   104,562,687    19,103,746   5 Extended
**/dev/sde5**   ** * **    85,458,944   103,647,231    18,188,288  83 Linux
/dev/sde6         103,649,280   104,562,687       913,408  82 Linux swap / Solaris


```

I also have no idea what double-check is.

It may be that the boot flag on sdd1 is causing problems there is this in the partition. /Boot/BCD

---

### Post by teddykgb715 on 2010-11-09
Sorry by double check I meant I went in to the Bios to make sure it was set up correctly.  The sde is set as HDD #1 in the bios.

I just tried the boot menu method, selecting the SSD and it brings me to the cursor, so Windows won't boot up that way either.

I removed the bootflag from the drive that didn't need it.

---

### Post by wilee-nilee on 2010-11-09
Can you tell me the bootsect stuff or link me to what that was.

---

### Post by teddykgb715 on 2010-11-09
I can't find the post now, I thought I'd bookmarked it.  But this is the command I used:

bootsect /nt60 C:/ mbr

Where C: was replaced by the boot drive as identified by the Windows 7 disc as being the one with 7 on it, in this case E:.

Hope that helps you research further.  I'll check back on this first thing in the morning here in MN.

---

### Post by teddykgb715 on 2010-11-09
This was not the original post I referenced, but here is an ehow post on this:

[http://www.ehow.com/how_4836283_repair-mbr-windows.html](http://www.ehow.com/how_4836283_repair-mbr-windows.html)

---

### Post by wilee-nilee on 2010-11-09
I'm not sure where the problem is. The scipt looks basically okay, but it only gives fairly general information.

If it was me I would use a commands set to set up the bootup files and mbr, but running the auto repair 3 times, yes 3 times, on the W7 partition will do the same. If it didn't work then I would boot to the repair command terminal on the W7 disc and run chkdsk /r and accept a restart for it if needed.

Beyond that I would be stumped and just reinstall, as I have everything on a external anyway. Maybe not stumped really but I rather reinstall then sit around waiting for help. That is why everything is backed up of the computer including a images of the whole HD.

You might try the W7 forum there are people there that may have a clue to getting W7 up and running. I would post there and include a screen shot of the disk manger to make it easy for them.
[http://www.sevenforums.com/](http://www.sevenforums.com/)

I only suggest the other forum really in hoping you get back in shape as the computer is right now.

---

### Post by coffeecat on 2010-11-10
I agree with everything wilee-nilee has said. Only two things to add:

The bootflag on sde5, the Ubuntu root partition. I thought that you couldn't have a bootflag set on two partitions on the same drive at the same time. If I'm right about this, then something odd has happened. It may be that the bootflag on sde5 is interfering with Windows booting from sde1. Whatever - Windows must have the boot flag set but Ubuntu/Linux doesn't care whether it is or not. So it would be a good idea to unset the bootflag from sde5. 

I must admit that the bootsect utility is new to me. But thanks for the link because I am in the process of doing some research for possibly writing a comprehensive howto for repairing the Windows mbr. It's a topic that comes up with depressing regularity on the forum here. The bootrec utility you can get to in the command prompt in the Vista/W7 repair/install disc. How to use it here:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

But I doubt whether that adds anything to what you've already done. You could try running 'bootrec /FixMbr' and 'bootrec /FixBoot' if all else fails, but it's possible that bootsect has done all that already.

---

### Post by Mark Phelps on 2010-11-10
> **coffeecat said:**
> 
I must admit that the bootsect utility is new to me. But thanks for the link because I am in the process of doing some research for possibly writing a comprehensive howto for repairing the Windows mbr. 

Then, you might want to go to a Windows 7 forum and look through their tutorials:  

[=Installation and Setup"]http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html?filter[3]=Installation and Setup]("http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html?filter[3)

You'll notice the one for Bootsect also has a link to a tutorial written for using Bootrec.

---

### Post by teddykgb715 on 2010-11-10
Well guys, I'm giving up.  I'm going to start fresh and reinstall Windows.  Can you guys point me to a good guide for then installing Ubuntu onto the same SSD for a dual boot?  I don't want to royally screw things up again!

---

### Post by coffeecat on 2010-11-10
> **Mark Phelps said:**
> Then, you might want to go to a Windows 7 forum and look through their tutorials:  

[=Installation%20and%20Setup"]http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html?filter[3]=Installation and Setup]("http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html?filter[3)

You'll notice the one for Bootsect also has a link to a tutorial written for using Bootrec.

Thanks for that. That's useful.
 
> **teddykgb715 said:**
> Well guys, I'm giving up.  I'm going to start fresh and reinstall Windows.  Can you guys point me to a good guide for then installing Ubuntu onto the same SSD for a dual boot?  I don't want to royally screw things up again!

This will probably cover a lot of things you know already, but it has some useful stuff:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

I would suggest preparing the Windows 7 partition(s) beforehand, rather than letting the Ubuntu installer resize the C: partition. Either use the W7 install DVD to do this, but leave enough unused space for Ubuntu, or prepare all your partitions beforehand with Gparted in the Ubuntu live CD. Windows 7 is happy to install itself to a NTFS partition created by Gparted, but can take unkindly to being resized by Gparted after it is installed. This way you can decide whether to have W7 on a single partition, or set up one of those separate small boot partitions which the W7 installer will create if left to its own devices.

Having installed Windows, then boot up with the Ubuntu live CD and go into Gparted to create your Linux partitions before you start the installer. Once in the installer you then need to choose the manual (advanced) option at the partitioning stage. You don't need to tell the installer to use the swap partition that you've prepared - it will pick this up automatically. You can, I believe, create partitions in unused space in the manual stage of the installer instead of going into Gparted first.

---

