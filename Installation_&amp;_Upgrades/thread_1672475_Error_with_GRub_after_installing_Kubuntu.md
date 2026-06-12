---
title: "Error with GRub after installing Kubuntu"
date: 2011-01-20
forum: Installation &amp; Upgrades
---

### Post by z_AML_z on 2011-01-20
So here is the problem...I have windows 7 installed on my copmuter and I ran the alternate disc cause the live disc didn't work for me. So installing was smmoth and I did everything right excpet for the grub part. It asked to be a master loader or something and I said yes. After restarting I see the grub menu but I only see two ubuntus(recovery mode) on the list and 2 test thingys ( memory test) So I go to the ubuntu tab and I get kubuntu ( as ecpected). Right now I am using kubuntu and it is fine but?!? Where is my Windows?!?

---

### Post by Quackers on 2011-01-20
Try opening a terminal and running
```
sudo update-grub
```
and watch as grub.cfg is run, to see if the Windows Loader is picked up. If it is, reboot and try to boot Windows.

---

### Post by z_AML_z on 2011-01-20
Thanks for the quick response but still no luck

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```

I know for a fact that my windows partition is not corrupted or anything because I can still view it from kubuntu

---

### Post by Quackers on 2011-01-20
Ok, good :-)
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by z_AML_z on 2011-01-20
Her is the results

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for (,msdos4)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$MFTMirr does not match $MFT (record 1).
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
$MFTMirr does not match $MFT (record 1).
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
$MFTMirr does not match $MFT (record 1).
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
$MFTMirr does not match $MFT (record 1).
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,048   428,185,599   425,111,552   7 HPFS/NTFS
/dev/sda3         428,187,646   476,026,879    47,839,234   f W95 Ext d (LBA)
/dev/sda5         428,187,648   467,250,147    39,062,500   7 HPFS/NTFS
/dev/sda6         467,251,200   476,026,879     8,775,680  82 Linux swap / Solaris
/dev/sda4         476,026,880   488,392,703    12,365,824  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/cryptswap1 41804bc5-ba02-40d2-859a-f7cefdfc8aa3   swap                                     
/dev/sda1        0A6AC6C76AC6AF2F                       ntfs       TOSHIBA SYSTEM VOLUME         
/dev/sda2        ACD2F5BDD2F58C38                       ntfs       SQ004982V02                   
/dev/sda3: PTTYPE="dos" 
/dev/sda4        b126fe83-9273-47c7-986e-ece33c5ea1f6   ext4                                     
/dev/sda5        C804F69504F6862A                       ntfs       Amlesh                        
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
cryptswap1

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda1        /media/TOSHIBA SYSTEM VOLUME fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5        /media/Amlesh            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set b126fe83-9273-47c7-986e-ece33c5ea1f6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set b126fe83-9273-47c7-986e-ece33c5ea1f6
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
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set b126fe83-9273-47c7-986e-ece33c5ea1f6
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=b126fe83-9273-47c7-986e-ece33c5ea1f6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set b126fe83-9273-47c7-986e-ece33c5ea1f6
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=b126fe83-9273-47c7-986e-ece33c5ea1f6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set b126fe83-9273-47c7-986e-ece33c5ea1f6
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set b126fe83-9273-47c7-986e-ece33c5ea1f6
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=b126fe83-9273-47c7-986e-ece33c5ea1f6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
#UUID=9f9eb7ab-9c02-4d98-b0dc-3c649cdd4219 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

=================== sda4: Location of files loaded by Grub: ===================


 246.4GB: boot/grub/core.img
 246.5GB: boot/grub/grub.cfg
 245.4GB: boot/initrd.img-2.6.35-22-generic
 244.1GB: boot/vmlinuz-2.6.35-22-generic
 245.4GB: initrd.img
 244.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  8d 8d 4c ff ff ff 88 5d  fc ff 15 f8 12 ea 05 e9  |..L....]........|
00000010  b6 fe ff ff cc cc cc cc  cc 68 b4 00 00 00 b8 e3  |.........h......|
00000020  b1 ea 05 e8 b7 10 00 00  8b 75 08 33 db 8d 4d d4  |.........u.3..M.|
00000030  89 5d fc 89 9d 50 ff ff  ff c7 06 05 40 00 80 ff  |.]...P......@...|
00000040  15 ec 12 ea 05 8d 8d 58  ff ff ff c6 45 fc 01 ff  |.......X....E...|
00000050  15 68 13 ea 05 8b 3d e8  12 ea 05 8d 4d 0c c6 45  |.h....=.....M..E|
00000060  fc 02 ff d7 50 e8 17 f8  ff ff 85 c0 74 1b 8d 85  |....P.......t...|
00000070  58 ff ff ff 50 8d 45 d4  50 8d 45 0c 50 e8 4b fc  |X...P.E.P.E.P.K.|
00000080  ff ff 89 06 e9 d5 00 00  00 53 53 53 8d 8d 40 ff  |.........SSS..@.|
00000090  ff ff ff 15 0c 13 ea 05  83 ec 1c 8d 45 0c 8b cc  |............E...|
000000a0  89 a5 54 ff ff ff 50 c6  45 fc 03 ff 15 98 13 ea  |..T...P.E.......|
000000b0  05 8d 45 b8 50 e8 b5 e2  ff ff 53 6a 03 8d 4d b8  |..E.P.....Sj..M.|
000000c0  c6 45 fc 04 ff d7 50 8d  85 40 ff ff ff 50 8d 8d  |.E....P..@...P..|
000000d0  60 ff ff ff ff 15 94 13  ea 05 8d 8d 60 ff ff ff  |`...........`...|
000000e0  c6 45 fc 05 ff 15 90 13  ea 05 8d 8d 60 ff ff ff  |.E..........`...|
000000f0  85 c0 74 35 53 53 53 8d  45 d4 50 68 87 15 00 00  |..t5SSS.E.Ph....|
00000100  ff 15 64 13 ea 05 3b c3  89 06 7c 25 53 53 53 8d  |..d...;...|%SSS.|
00000110  85 58 ff ff ff 50 68 82  15 00 00 8d 8d 60 ff ff  |.X...Ph......`..|
00000120  ff ff 15 60 13 ea 05 eb  06 ff 15 8c 13 ea 05 89  |...`............|
00000130  06 8d 8d 60 ff ff ff c6  45 fc 04 ff 15 6c 13 ea  |...`....E....l..|
00000140  05 8d 4d b8 c6 45 fc 03  ff 15 d8 12 ea 05 8d 8d  |..M..E..........|
00000150  40 ff ff ff c6 45 fc 02  ff 15 f8 12 ea 05 39 1e  |@....E........9.|
00000160  0f 8c 97 00 00 00 8d 4d  d4 ff d7 50 68 00 00 02  |.......M...Ph...|
00000170  00 53 bf 01 00 01 00 57  6a 0a ff 15 e8 10 ea 05  |.S.....Wj.......|
00000180  89 85 54 ff ff ff 3b c3  74 5d 8b 8d 58 ff ff ff  |..T...;.t]..X...|
00000190  89 8d 48 ff ff ff 8b 8d  5c ff ff ff 53 89 8d 4c  |..H.....\...S..L|
000001a0  ff ff ff 8d 8d 48 ff ff  ff 51 68 00 00 01 00 53  |.....H...Qh....S|
000001b0  57 50 ff 15 1c 11 ea 05  89 85 50 ff ff ff 00 fe  |WP........P.....|
000001c0  ff ff 07 fe ff ff 02 00  00 00 e4 0b 54 02 00 fe  |............T...|
000001d0  ff ff 05 fe ff ff 5f 0d  54 02 a3 ea 85 00 00 00  |......_.T.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb 

```

---

### Post by Quackers on 2011-01-20
Are you using a raid array?

---

### Post by z_AML_z on 2011-01-20
nope only partitions

---

### Post by Quackers on 2011-01-20
Are you using encryption?

---

### Post by z_AML_z on 2011-01-20
Nope

---

### Post by Quackers on 2011-01-20
Sorry about the 20 questions :-) but your boot script output is one I've not seen before.
Your /dev/sda2 partition (probably C: in Windows) and your /dev/sda6 partition (swap) are showing as unmounted. It says that your Master File Table mirror does not match your Master File Table for those 2 partitions. It also suggests that either the file system is inconsistent, or the hard drive could have a hardware fault.
As I have not seen this output before I can only make broad suggestions.
You could run a HDD check to test the hard drive.
You could run a chkdsk on the Windows drive.
See if any errors are reported.
Obviously, you could see if somebody else suggests something more definitive.

---

### Post by z_AML_z on 2011-01-21
How would I do that in kubuntu or a ubuntu live disc....Man i am better of with ubuntu...been using ubuntu for quite a while but then decided I wanted to try kde...wosrt mistake ever....

---

### Post by Quackers on 2011-01-21
To be honest the more I look at your boot script output, together with what you have written, the odder it all looks. The only Linux system that shows on the boot script is Ubuntu 10.10 on sda4. There is no Kubuntu in evidence at all, and it can't be on the unmounted partitions because one is NTFS and the other is swap.
According to the boot script you should be able to boot Ubuntu 10.10
This is very odd indeed :-(

---

### Post by z_AML_z on 2011-01-21
Should I format sda2? I keep all my personel documents on another partition anyway what do you say? I have the windows installation disc at hand right now...

trust me it says ubuntu but It was the kubuntu installation disc I used and it has kde written all over it...Blueness everywhere

---

### Post by hasanujjaman on 2011-01-21
1. Uninstall GRUB (Use "**Super Grub Disk**" ).
2. Boot into Windows.Check all the partitions.
3. Shutdown Windows properly.
4. Check whether Windows starts properly or not at the next boot.
5. If everything goes okay,then reinstall grub either using **Super Grub Disk** or using **ubuntu live cd**.

---

### Post by Quackers on 2011-01-21
> **z_AML_z said:**
> Should I format sda2? I keep all my personel documents on another partition anyway what do you say? I have the windows installation disc at hand right now...

trust me it says ubuntu but It was the kubuntu installation disc I used and it has kde written all over it...Blueness everywhere
If it was just a Windows problem I would say that was an option. But the swap partition is reporting the same errors.
It may be worthwhile booting from the Windows disc and entering the recovery console then the command prompt and run chkdsk C: /r and see if errors are found. If errors are reported re-run the same command until no errors are reported.

---

### Post by z_AML_z on 2011-01-21
> **hasanujjaman said:**
> 1. Uninstall GRUB (Use "**Super Grub Disk**" ).
2. Boot into Windows.Check all the partitions.
3. Shutdown Windows properly.
4. Check whether Windows starts properly or not at the next boot.
5. If everything goes okay,then reinstall grub either using **Super Grub Disk** or using **ubuntu live cd**.

I succesfully booted into windows and am currently trying to see if windows goes okay on the next boot.

anyway I am more focused on removing Kubuntu and the grub How would I do that?

EDIT: Succesfully got grub removed and I just booted to meh Windows :) Now time to remove kubuntu should I just delete the partition?

---

