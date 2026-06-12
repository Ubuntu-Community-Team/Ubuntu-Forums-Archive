---
title: "Dualboot Vista and Ubuntu 10.10"
date: 2011-01-25
forum: Installation &amp; Upgrades
---

### Post by _Impact_ on 2011-01-25
I have Vista installed and would like to dualboot with Ubuntu 10.10. 

I've used Wubi until now, it failed to upgrade to Ubuntu 10.10 (something went wrong) so I decided it's time to install Ubuntu properly. 

The problem is that there is only one hard-drive (Disk 0) with 4 Windows partitions on it. 

If I try to shrink C, the Windows Disk Manager says the available shrink space is 0 mb!!! :)

Do I need to delete one partition, like for example Data D?

I would also like to keep Vista intact, I will definitely need it in the future :)

Btw, Ubuntu rocks!!!! \\:D/

Thanx!!!

---

### Post by oldfred on 2011-01-25
You have to decide what partition to delete and then shrink c: and/ or D: to make room for an extended partition with many logical partitions. Do not use Windows to create more partitions as it will convert from basic to SFS which is not compatible with anything.

One partition should be a recovery partition that is an image of your drive as purchased. You should make the recovery DVD(s). If it lets you also make a repair CD you need to do that also. Some vendors only let you make one copy & have to buy any additional, so this is one possibility to delete.

You may have a vendor utilities which you can backup and if you want reinstall into a new logical partitiion. Some portables may have keys tied to certain functions, if you relie on those, you may loose that (or not).

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)
[http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html](http://www.thpc.info/how/shrink_partition_in_windows_7_vista.html)


GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Partitioning basics with some info on /data, older but still good
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

### Post by kansasnoob on 2011-01-25
That shows both Acer (C) and Data (D) have significant data stored on them, and of course Acer (C) is the actual OS.

You need to google EISA configuration and then shake your head and rethink things :o

No easy way to deal with that. Just an example:

[http://www.ehow.com/how_5037808_remove-eisa-configuration-hard-drive.html](http://www.ehow.com/how_5037808_remove-eisa-configuration-hard-drive.html)

If I were you I'd refer to this thread and rethink Wubi:

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by dirghrabadia on 2011-01-25
> 
 
so I decided it's time to install Ubuntu properly. 


 
+1.
 
 
Also, as a precaution, don't go with 'Install alongside' option with 10.10, instead go with manual option for selecting the partition, as 10.10 is known to (a few atleast) wipe Windows when you go with the former option. Enjoy :)

---

### Post by _Impact_ on 2011-01-26
> **kansasnoob said:**
> That shows both Acer (C) and Data (D) have significant data stored on them, and of course Acer (C) is the actual OS.

You need to google EISA configuration and then shake your head and rethink things :o

No easy way to deal with that. Just an example:

[http://www.ehow.com/how_5037808_remove-eisa-configuration-hard-drive.html](http://www.ehow.com/how_5037808_remove-eisa-configuration-hard-drive.html)

If I were you I'd refer to this thread and rethink Wubi:

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

Thanks for all the replies.

Ok so what if I backed up all data from partition DATA D, deleted this partition, created a new one instead and installed Ubuntu 10.10 from a LiveCD on it, would that work? Or is there something that I need to understand about EISA?

---

### Post by Quackers on 2011-01-26
Yes, if you backup what you need from D: then delete that partition with the Disk Management utility (right-click on the D: and choose delete).
You can also try defragmenting the C: partition once, or even twice. Then try again to shrink it.
Do not then create any new partitions with that disk management utility.
Instead use either gparted on the live cd, or the actual Ubuntu installer (by selecting the "specify manually" option in the partitioning stage of the installation) to create an extended partition.
Inside this extended partition you can then create your Ubuntu partitions and (if required) a new data partition. All of these new partitions would be created as logical partitions.

Also, as dirghrabadia has stated, it is not safe when using the 10.10 installer, to use the "install alongside" option. It has a nasty habit of eating existing operating systems.

---

### Post by _Impact_ on 2011-02-03
One more question: I deleted the D partition (with windows) , created an extended instead and logical inside this extended (done with GParted). Now I'm about to install Ubuntu 10.10 on this logical partition, but it asks me which device to use for the boot loader installation and gives me choices:

dev/sda/ Hitachi etc.  (the whole drive)
dev/sda1 Windows Vista (loader)
dev/sda2 Windows Recovery Environment (loader)
dev/sda5 
dev/sda3 Windows XP Embedded

Which one should I select?

Thanks!!!

---

### Post by kansasnoob on 2011-02-03
> **_Impact_ said:**
> One more question: I deleted the D partition (with windows) , created an extended instead and logical inside this extended (done with GParted). Now I'm about to install Ubuntu 10.10 on this logical partition, but it asks me which device to use for the boot loader installation and gives me choices:

**[COLOR="Red"]dev/sda[/COLOR]**/ Hitachi etc.  (the whole drive)
dev/sda1 Windows Vista (loader)
dev/sda2 Windows Recovery Environment (loader)
dev/sda5 
dev/sda3 Windows XP Embedded

Which one should I select?

Thanks!!!

Definitely /dev/sda

That's what we refer to as the MBR of the drive.

---

### Post by _Impact_ on 2011-02-03
The installation went fine, but now GRUB doesn't give me the option to boot Vista. What can I do (I searched for awhile, but didn't find anything understandable for my newbie intellect).

Thanks!

---

### Post by kansasnoob on 2011-02-03
Try running this command from the Terminal:

```
sudo update-grub
```

If that fails to find Windows then post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Alternate instructions:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

Remember the EISA setup scared me, I hope we can figure this out.

---

### Post by _Impact_ on 2011-02-03
Thanks for the replies Kansasnoob. I'm enjoying Ubuntu already. Here's the result:



   Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    22,523,129    22,523,067  12 Compaq diagnostics
/dev/sda2    *     22,523,904   255,698,935   233,175,032   7 HPFS/NTFS
/dev/sda3         255,698,942   481,554,431   225,855,490   5 Extended
/dev/sda5         255,698,944   481,554,431   225,855,488  83 Linux
/dev/sda4         481,554,432   488,394,751     6,840,320  12 Compaq diagnostics


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        6822B84EE49BED2A                       ntfs       PQSERVICE                     
/dev/sda2        2698BFEC98BFB91F                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        16D4F3CBD4F3AADF                       ntfs                                     
/dev/sda5        00f69496-a48e-4720-a4a2-93b4fefd3a2e   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 00f69496-a48e-4720-a4a2-93b4fefd3a2e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 00f69496-a48e-4720-a4a2-93b4fefd3a2e
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 00f69496-a48e-4720-a4a2-93b4fefd3a2e
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=00f69496-a48e-4720-a4a2-93b4fefd3a2e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 00f69496-a48e-4720-a4a2-93b4fefd3a2e
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=00f69496-a48e-4720-a4a2-93b4fefd3a2e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 00f69496-a48e-4720-a4a2-93b4fefd3a2e
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=00f69496-a48e-4720-a4a2-93b4fefd3a2e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 00f69496-a48e-4720-a4a2-93b4fefd3a2e
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=00f69496-a48e-4720-a4a2-93b4fefd3a2e ro single 
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
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 00f69496-a48e-4720-a4a2-93b4fefd3a2e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 00f69496-a48e-4720-a4a2-93b4fefd3a2e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 6822b84ee49bed2a
	chainloader +1
}
menuentry "Microsoft Windows XP Embedded (on /dev/sda4)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set 16d4f3cbd4f3aadf
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
UUID=00f69496-a48e-4720-a4a2-93b4fefd3a2e /               ext4    errors=remount-ro 0       1

=================== sda5: Location of files loaded by Grub: ===================


 169.7GB: boot/grub/core.img
 242.9GB: boot/grub/grub.cfg
 132.1GB: boot/initrd.img-2.6.35-22-generic
 132.1GB: boot/initrd.img-2.6.35-25-generic
 169.7GB: boot/vmlinuz-2.6.35-22-generic
 169.7GB: boot/vmlinuz-2.6.35-25-generic
 132.1GB: initrd.img
 132.1GB: initrd.img.old
 169.7GB: vmlinuz
 169.7GB: vmlinuz.old

================================ sda4/boot.ini: ================================

[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /maxmem=768
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
00000010  1d 01 00 00 1f 00 00 00  1d 01 00 00 00 00 00 00  |................|
00000020  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
00000030  1e 01 00 00 1f 00 00 00  1e 01 00 00 00 00 00 00  |................|
00000040  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
00000050  1f 01 00 00 1f 00 00 00  1f 01 00 00 00 00 00 00  |................|
00000060  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
00000070  20 01 00 00 20 00 00 00  20 01 00 00 00 00 00 00  | ... ... .......|
00000080  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
00000090  21 01 00 00 21 00 00 00  21 01 00 00 00 00 00 00  |!...!...!.......|
000000a0  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
000000b0  22 01 00 00 22 00 00 00  22 01 00 00 00 00 00 00  |"..."...".......|
000000c0  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
000000d0  23 01 00 00 23 00 00 00  23 01 00 00 00 00 00 00  |#...#...#.......|
000000e0  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
000000f0  24 01 00 00 23 00 00 00  24 01 00 00 00 00 00 00  |$...#...$.......|
00000100  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
00000110  25 01 00 00 24 00 00 00  25 01 00 00 00 00 00 00  |%...$...%.......|
00000120  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
00000130  26 01 00 00 24 00 00 00  26 01 00 00 00 00 00 00  |&...$...&.......|
00000140  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
00000150  27 01 00 00 24 00 00 00  27 01 00 00 00 00 00 00  |'...$...'.......|
00000160  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
00000170  28 01 00 00 24 00 00 00  28 01 00 00 00 00 00 00  |(...$...(.......|
00000180  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
00000190  29 01 00 00 25 00 00 00  29 01 00 00 00 00 00 00  |)...%...).......|
000001a0  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
000001b0  2a 01 00 00 26 00 00 00  2a 01 00 00 00 00 00 fe  |*...&...*.......|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 48 76 0d 00 00  |...........Hv...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

---

### Post by _Impact_ on 2011-02-03
Why do I have a feeling I just wiped my Vista?:-o

---

### Post by kansasnoob on 2011-02-03
Don't panic just yet. I want you to boot into Ubuntu and install Gparted:

```
sudo apt-get install gparted
```

You'll then find it in System > Administration. I need you to use it to remove the boot flag on sda2 and place a boot flag on sda1. Sample image:

[ATTACH]182604[/ATTACH]

Then run "sudo update-grub" again and see what happens if you select the boot entry for sda1.

If that's still a no-go please post the output of this command:

```
sudo parted -l
```

BTW that's a lower case L at the end.

---

### Post by kansasnoob on 2011-02-03
Just FYI what really puzzles me is this:

> sda4: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: **[COLOR="Red"]Windows XP[/COLOR]**
Boot files/dirs: /boot.ini /ntldr /NTDETECT.COM

Was this perhaps an upgrade from XP to Vista?

---

### Post by _Impact_ on 2011-02-03
Changed flags, but still the same, if I boot to Windows Vista Loader (dev/sda1) it goes to Acer eRecovery Management and asks whether I want to:

Repair startup or

Restore system to factory defaults 

I tried restore system, it restored, but nothing changed in the GRUB menu. 

Here's the output from parted -l:

```
Model: ATA Hitachi HTS54252 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  11.5GB  11.5GB  primary   ntfs         diag
 2      11.5GB  131GB   119GB   primary   ntfs         boot
 3      131GB   247GB   116GB   extended
 5      131GB   247GB   116GB   logical   ext4
 4      247GB   250GB   3502MB  primary   ntfs         diag

```


I did not upgrade from XP to Vista, I bought the laptop with Vista on it.


By the way, I did the remove flag from sda2 and put it to sda1, I don't know why this doesn't show in the output. 

Also I think the Vista is still there, because before doing the Restore from Acer eRecovery Management, Ubuntu would connect to the Router set up on Vista, but after the Restore, the Router is not there. Am I right in assuming that Vista is still alive?

BTW, thanks a lot for your replies!!!

The following screenshot is after I did the system restore after booting into sda1 (Acer eRecovery Management) - now there's 11GB of used space on the second partition (Vista), instead of a few MB as it was before.

The following screenshot is after I booted into Acer eRecovery Management (dev/sda1) and selected System Restore. Notice GParted now shows 11 GB of used space on the second partition, and not a few MB as it was before the System Restore. Unfortunately, GRUB is still not showing Vista.

---

### Post by Quackers on 2011-02-03
Try putting the boot flag back on sda2 (if it's not there now) and try again.
I would have expected Windows to be in the mbr of the drive, if the recovery had worked.
Also please re-run the boot script after moving the boot flag. Thanks.

---

### Post by oldfred on 2011-02-03
The installer definitely saw the window Vista partition. It seem to reverse the descriptions on which is recover and which is the main install. So sda2 was the main install.
dev/sda1 Windows Vista (loader)
dev/sda2 Windows Recovery Environment (loader)

Did you change Vista's partition size? That would make Vista want to run chkdsk and then perhaps the boot script cannot see the boot files in the sda2 partition as it cannot mount it with the chkdsk flag (needed) set.

From Ubuntu can you see the /windows and /Windows/System32 folders? If so just run chkdsk from a Vista repair CD. Or it may not let you mount it either with the chkdsk flag set. 
Vista/7 CHKDSK
chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. Rerun until no errors.

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by kansasnoob on 2011-02-03
Going back to post #1 partitions were (in order from left to right):

10.74 GB EISA
111.19 GB System/Boot (44% free)
107.69 GB Data
3.26 GB EISA

Then look at parted -l now:

```
Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  11.5GB  11.5GB  primary   ntfs         diag
 2      11.5GB  131GB   119GB   primary   ntfs         boot
 3      131GB   247GB   116GB   extended
 5      131GB   247GB   116GB   logical   ext4
 4      247GB   250GB   3502MB  primary   ntfs         diag
```

Now, we have to take into consideration that sizes are read slightly different between Windows and Linux, but consider them proportionately. The old data partition (aka: drive D) was a bit smaller than the system partition (aka: drive C). And that's still true looking at both the parted output and the screenshot in post #15 (in fact the sizes shown in the Gparted screenshot are nearly identical to what Windows disc utility showed in post #1).

Most worrisome! The Boot Info Script showed no OS or boot files in sda2, and the screenshot in post #15 now shows only 11.96 GB used of sda2 as compared to Windows having shown 44% free :(

That indicates to me that sda2 was somehow formatted, eh?

I'm thinking of this from PhotoRec:

[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

> For lost/deleted partitions or deleted files from a FAT or NTFS file system, try TestDisk first - it's usually faster and TestDisk can retrieved the original file names.

The link referred to there:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

NOTE: I'm not proficient using TestDisk! I have however had very good luck following the step-by-step guide! I've particularly had good luck with this:

[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

---

### Post by _Impact_ on 2011-02-03
> **Quackers said:**
> Try putting the boot flag back on sda2 (if it's not there now) and try again.
I would have expected Windows to be in the mbr of the drive, if the recovery had worked.
Also please re-run the boot script after moving the boot flag. Thanks.

OK I changed the flags back. Here's the new output from boot info script: 


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    22,523,129    22,523,067  12 Compaq diagnostics
/dev/sda2    *     22,523,904   255,698,935   233,175,032   7 HPFS/NTFS
/dev/sda3         255,698,942   481,554,431   225,855,490   5 Extended
/dev/sda5         255,698,944   481,554,431   225,855,488  83 Linux
/dev/sda4         481,554,432   488,394,751     6,840,320  12 Compaq diagnostics


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        6822B84EE49BED2A                       ntfs       PQSERVICE                     
/dev/sda2        52402B81402B6AC5                       ntfs       ACER                          
/dev/sda3: PTTYPE="dos" 
/dev/sda4        16D4F3CBD4F3AADF                       ntfs                                     
/dev/sda5        00f69496-a48e-4720-a4a2-93b4fefd3a2e   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 00f69496-a48e-4720-a4a2-93b4fefd3a2e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 00f69496-a48e-4720-a4a2-93b4fefd3a2e
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 00f69496-a48e-4720-a4a2-93b4fefd3a2e
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=00f69496-a48e-4720-a4a2-93b4fefd3a2e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 00f69496-a48e-4720-a4a2-93b4fefd3a2e
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=00f69496-a48e-4720-a4a2-93b4fefd3a2e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 00f69496-a48e-4720-a4a2-93b4fefd3a2e
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=00f69496-a48e-4720-a4a2-93b4fefd3a2e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 00f69496-a48e-4720-a4a2-93b4fefd3a2e
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=00f69496-a48e-4720-a4a2-93b4fefd3a2e ro single 
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
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 00f69496-a48e-4720-a4a2-93b4fefd3a2e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 00f69496-a48e-4720-a4a2-93b4fefd3a2e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 6822b84ee49bed2a
	chainloader +1
}
menuentry "Microsoft Windows XP Embedded (on /dev/sda4)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set 16d4f3cbd4f3aadf
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
UUID=00f69496-a48e-4720-a4a2-93b4fefd3a2e /               ext4    errors=remount-ro 0       1

=================== sda5: Location of files loaded by Grub: ===================


 169.7GB: boot/grub/core.img
 243.0GB: boot/grub/grub.cfg
 132.1GB: boot/initrd.img-2.6.35-22-generic
 132.1GB: boot/initrd.img-2.6.35-25-generic
 169.7GB: boot/vmlinuz-2.6.35-22-generic
 169.7GB: boot/vmlinuz-2.6.35-25-generic
 132.1GB: initrd.img
 132.1GB: initrd.img.old
 169.7GB: vmlinuz
 169.7GB: vmlinuz.old

================================ sda4/boot.ini: ================================

[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /maxmem=768
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
00000010  1d 01 00 00 1f 00 00 00  1d 01 00 00 00 00 00 00  |................|
00000020  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
00000030  1e 01 00 00 1f 00 00 00  1e 01 00 00 00 00 00 00  |................|
00000040  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
00000050  1f 01 00 00 1f 00 00 00  1f 01 00 00 00 00 00 00  |................|
00000060  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
00000070  20 01 00 00 20 00 00 00  20 01 00 00 00 00 00 00  | ... ... .......|
00000080  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
00000090  21 01 00 00 21 00 00 00  21 01 00 00 00 00 00 00  |!...!...!.......|
000000a0  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
000000b0  22 01 00 00 22 00 00 00  22 01 00 00 00 00 00 00  |"..."...".......|
000000c0  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
000000d0  23 01 00 00 23 00 00 00  23 01 00 00 00 00 00 00  |#...#...#.......|
000000e0  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
000000f0  24 01 00 00 23 00 00 00  24 01 00 00 00 00 00 00  |$...#...$.......|
00000100  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
00000110  25 01 00 00 24 00 00 00  25 01 00 00 00 00 00 00  |%...$...%.......|
00000120  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
00000130  26 01 00 00 24 00 00 00  26 01 00 00 00 00 00 00  |&...$...&.......|
00000140  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
00000150  27 01 00 00 24 00 00 00  27 01 00 00 00 00 00 00  |'...$...'.......|
00000160  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
00000170  28 01 00 00 24 00 00 00  28 01 00 00 00 00 00 00  |(...$...(.......|
00000180  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
00000190  29 01 00 00 25 00 00 00  29 01 00 00 00 00 00 00  |)...%...).......|
000001a0  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
000001b0  2a 01 00 00 26 00 00 00  2a 01 00 00 00 00 00 fe  |*...&...*.......|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 48 76 0d 00 00  |...........Hv...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by kansasnoob on 2011-02-03
> **_Impact_ said:**
> OK I changed the flags back. Here's the new output from boot info script: 


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    22,523,129    22,523,067  12 Compaq diagnostics
/dev/sda2    *     22,523,904   255,698,935   233,175,032   7 HPFS/NTFS
/dev/sda3         255,698,942   481,554,431   225,855,490   5 Extended
/dev/sda5         255,698,944   481,554,431   225,855,488  83 Linux
/dev/sda4         481,554,432   488,394,751     6,840,320  12 Compaq diagnostics


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        6822B84EE49BED2A                       ntfs       PQSERVICE                     
/dev/sda2        52402B81402B6AC5                       ntfs       ACER                          
/dev/sda3: PTTYPE="dos" 
/dev/sda4        16D4F3CBD4F3AADF                       ntfs                                     
/dev/sda5        00f69496-a48e-4720-a4a2-93b4fefd3a2e   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 00f69496-a48e-4720-a4a2-93b4fefd3a2e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 00f69496-a48e-4720-a4a2-93b4fefd3a2e
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 00f69496-a48e-4720-a4a2-93b4fefd3a2e
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=00f69496-a48e-4720-a4a2-93b4fefd3a2e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 00f69496-a48e-4720-a4a2-93b4fefd3a2e
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/boot/vmlinuz-2.6.35-25-generic root=UUID=00f69496-a48e-4720-a4a2-93b4fefd3a2e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 00f69496-a48e-4720-a4a2-93b4fefd3a2e
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=00f69496-a48e-4720-a4a2-93b4fefd3a2e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 00f69496-a48e-4720-a4a2-93b4fefd3a2e
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=00f69496-a48e-4720-a4a2-93b4fefd3a2e ro single 
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
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 00f69496-a48e-4720-a4a2-93b4fefd3a2e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 00f69496-a48e-4720-a4a2-93b4fefd3a2e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 6822b84ee49bed2a
	chainloader +1
}
menuentry "Microsoft Windows XP Embedded (on /dev/sda4)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos4)'
	search --no-floppy --fs-uuid --set 16d4f3cbd4f3aadf
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
UUID=00f69496-a48e-4720-a4a2-93b4fefd3a2e /               ext4    errors=remount-ro 0       1

=================== sda5: Location of files loaded by Grub: ===================


 169.7GB: boot/grub/core.img
 243.0GB: boot/grub/grub.cfg
 132.1GB: boot/initrd.img-2.6.35-22-generic
 132.1GB: boot/initrd.img-2.6.35-25-generic
 169.7GB: boot/vmlinuz-2.6.35-22-generic
 169.7GB: boot/vmlinuz-2.6.35-25-generic
 132.1GB: initrd.img
 132.1GB: initrd.img.old
 169.7GB: vmlinuz
 169.7GB: vmlinuz.old

================================ sda4/boot.ini: ================================

[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /maxmem=768
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
00000010  1d 01 00 00 1f 00 00 00  1d 01 00 00 00 00 00 00  |................|
00000020  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
00000030  1e 01 00 00 1f 00 00 00  1e 01 00 00 00 00 00 00  |................|
00000040  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
00000050  1f 01 00 00 1f 00 00 00  1f 01 00 00 00 00 00 00  |................|
00000060  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
00000070  20 01 00 00 20 00 00 00  20 01 00 00 00 00 00 00  | ... ... .......|
00000080  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
00000090  21 01 00 00 21 00 00 00  21 01 00 00 00 00 00 00  |!...!...!.......|
000000a0  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
000000b0  22 01 00 00 22 00 00 00  22 01 00 00 00 00 00 00  |"..."...".......|
000000c0  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
000000d0  23 01 00 00 23 00 00 00  23 01 00 00 00 00 00 00  |#...#...#.......|
000000e0  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
000000f0  24 01 00 00 23 00 00 00  24 01 00 00 00 00 00 00  |$...#...$.......|
00000100  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
00000110  25 01 00 00 24 00 00 00  25 01 00 00 00 00 00 00  |%...$...%.......|
00000120  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
00000130  26 01 00 00 24 00 00 00  26 01 00 00 00 00 00 00  |&...$...&.......|
00000140  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
00000150  27 01 00 00 24 00 00 00  27 01 00 00 00 00 00 00  |'...$...'.......|
00000160  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
00000170  28 01 00 00 24 00 00 00  28 01 00 00 00 00 00 00  |(...$...(.......|
00000180  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
00000190  29 01 00 00 25 00 00 00  29 01 00 00 00 00 00 00  |)...%...).......|
000001a0  aa aa aa aa bb bb bb bb  cc cc cc cc dd dd dd dd  |................|
000001b0  2a 01 00 00 26 00 00 00  2a 01 00 00 00 00 00 fe  |*...&...*.......|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 48 76 0d 00 00  |...........Hv...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

If you're booted into Ubuntu and look in that partition do you see your data?

Gparted shows that it's gone! I do wish you hadn't selected the restore option, but I believe 90% or more of that data can be recovered!

---

### Post by _Impact_ on 2011-02-03
> **oldfred said:**
> Did you change Vista's partition size? That would make Vista want to run chkdsk and then perhaps the boot script cannot see the boot files in the sda2 partition as it cannot mount it with the chkdsk flag (needed) set.

[COLOR="Blue"]I did TRY to resize using Disk Management Tool from Vista, but it was not successful. Before trying to resize I did what that post said: 
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/")
However, I did not find any c:\pagefile.sys file (so did not remove it), then used Perfect Disk to defragment, it could only defragment up to 22% then my computer would freeze (I think this freeze has something to do with the fact that I got my vista infected a few days ago trying to install a cracked antivirus which then installed somekind of rootkit. I didn't know there's such thing as a free antivirus :) )


[/COLOR]


From Ubuntu can you see the /windows and /Windows/System32 folders? 

[COLOR="blue"]Yep!! The restored Vista, without any application installed by me[/COLOR]

If so just run chkdsk from a Vista repair CD. Or it may not let you mount it either with the chkdsk flag set. 
Vista/7 CHKDSK
chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. Rerun until no errors.


[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

[COLOR="blue"]
When I use the repair repair DVD, the only options I have is to Sartup Repair, System Restore, or Command Prompt. Do I use just write the code above in Command Prompt?
By the way, I did a CHKDSK on Vista before installing Ubuntu. There we 4 errors that could not be repaired, which had something to do with Vista Sidebar.
[/COLOR]

---

### Post by _Impact_ on 2011-02-03
> **kansasnoob said:**
> Going back to post #1 partitions were (in order from left to right):

10.74 GB EISA
111.19 GB System/Boot (44% free)
107.69 GB Data
3.26 GB EISA

Then look at parted -l now:

```
Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  11.5GB  11.5GB  primary   ntfs         diag
 2      11.5GB  131GB   119GB   primary   ntfs         boot
 3      131GB   247GB   116GB   extended
 5      131GB   247GB   116GB   logical   ext4
 4      247GB   250GB   3502MB  primary   ntfs         diag
```

Now, we have to take into consideration that sizes are read slightly different between Windows and Linux, but consider them proportionately. The old data partition (aka: drive D) was a bit smaller than the system partition (aka: drive C). And that's still true looking at both the parted output and the screenshot in post #15 (in fact the sizes shown in the Gparted screenshot are nearly identical to what Windows disc utility showed in post #1).

Most worrisome! The Boot Info Script showed no OS or boot files in sda2, and the screenshot in post #15 now shows only 11.96 GB used of sda2 as compared to Windows having shown 44% free :(

That indicates to me that sda2 was somehow formatted, eh?

I'm thinking of this from PhotoRec:

[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)



The link referred to there:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

NOTE: I'm not proficient using TestDisk! I have however had very good luck following the step-by-step guide! I've particularly had good luck with this:

[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)


Kansasbob, I did not actually have any precious data on Vista that I want to recover, I backed up all my personal files to an external drive before installing Ubuntu, so if Vista is already restored from scratch, I'm very happy with that, only if I could access it from GRUB...

Or do you still think I should try to undelete the files?

---

### Post by _Impact_ on 2011-02-03
Just in case this helps, these are the options offered by GRUB:

Ubuntu, with Linux 2.6.35-25 generic
Ubuntu, with Linux 2.6.35-25 recovery mode
Ubuntu, with Linux 2.6.35-22 generic
Ubuntu, with Linux 2.6.35-22 recovery mode
Memory test (memtest 86+)
Memory test (memtest 86+, serial console 115200)
Windows Vista (loader) (on /dev/sda1)
Microsoft Windows XP Embedded (on /dev/sda4)

---

### Post by kansasnoob on 2011-02-03
> **_Impact_ said:**
> Kansasbob, I did not actually have any precious data on Vista that I want to recover, I backed up all my personal files to an external drive before installing Ubuntu, so if Vista is already restored from scratch, I'm very happy with that, only if I could access it from GRUB...

**[COLOR="Red"]Or do you still think I should try to undelete the files?[/COLOR]**

It's up to you really. Since you ran that restore operation I don't know if you'll get boot files back or not. I am curious how that partition got hosed. I mean the size still seems right!

The reason I warned you about EISA configuration is because it's seriously bit me in the nether regions before! I once had to reconfigure the innards of a puter due to that!

In that case the computer was actually using a separate controller for the hard drive and the whole thing blew my mind! I did get the job done but it was a major pain!

---

### Post by oldfred on 2011-02-03
It still cannot see the sda2 partition. I would try running chkdsk from the windows command prompt. And rerun until no errors.

If chkdsk does not run:

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

---

### Post by _Impact_ on 2011-02-03
> **oldfred said:**
> It still cannot see the sda2 partition. I would try running chkdsk from the windows command prompt. And rerun until no errors.

If chkdsk does not run:

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

I ran ```
chkdsk C: /r
``` in command prompt and all was fine, it said Windows replaced bad clusters in file 36552 of name \Windows\INSTAL 1\2559d.msp and has made corrections to the file system. 

When I wrote this:

```
chkdsk C: /f
```

It said: Chkdsk cannot run because the volume is in use by another process. Chkdsk may run if this volume is dismounted first. ALL OPENED HANDLES TO THIS VOLUME WOULD THEN BE INVALID. Would you like to force a dismount of this volume? (Y/N)

GRUB still does not show the option for Vista. 

I'll try testdisk now.



I installed testdisk from Ubuntu Software Center and then Alt+F2 to run it, it now uses 100% of CPU2 but I can't see it!

---

### Post by _Impact_ on 2011-02-04
OK it finally worked - I ran sudo update-grub and now the sda2 showed up and booted into Vista!!!

Ho ho I'm so happy, thanks to all of you guys!!!=D>=D>=D>

HOWEVER! You might have guessed it, after Windows configured my computer, the GRUB menu is gone, there is no dualboot menu at all, it boots straight into Vista!!! I'm praying there's a simple solution to that... [-o<

Is there? Cause I'm about to mark this thread as SOLVED...

---

### Post by Quackers on 2011-02-04
It sounds like you need to re-install grub to the mbr of the drive, from the terminal in the live cd desktop.
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
This assumes that your Ubuntu root partition is sda5 (I think it is, but check).

When you reboot after the above, Ubuntu will boot directly. When it does, open a terminal and run ```
sudo update-grub
```
and watch as grub.cfg is configured to see if the Vista Loader is picked up. If so, reboot and choose vista from the grub menu to see if it boots ok.

---

### Post by _Impact_ on 2011-02-04
> **Quackers said:**
> It sounds like you need to re-install grub to the mbr of the drive, from the terminal in the live cd desktop.
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
This assumes that your Ubuntu root partition is sda5 (I think it is, but check).


After I ran ```
sudo grub-install --root-directory=mnt /dev/sda
``` it said:

```
usr/sbin/grub-probe: error: cannot find a device for mnt/boot/grub (is /dev mounted?)
```

And it booted straight to Vista again...:confused:


ooops looks like I missed a / 

trying again

---

### Post by _Impact_ on 2011-02-04
```
sudo grub-install --root-directory=/mnt /dev/sda
```

Here's what the terminal gave me:

/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.
This software may cause boot or other problems in future. Please ask its authors not to share data in the boot track..
Installation finished. No error reported.

After restart I was able to see GRUB again, with possibilities to boot Ubuntu as well as Vista on /dev/sda2 -> both booting just fine. 

After 

```
sudo update-grub
```

Instead of the Vista option, now there's Windows Recovery Environment ( on /dev/sda2), but it boots normally to Vista. I think it's just the name that got hijacked. 


So now I can officially mark the thread as SOLVED.

Thanks to all of you guys for support!!! God bless Ubuntu [-o<

---

### Post by oldfred on 2011-02-04
Glad it worked.

The flexnet issue is from some proprietary software you have installed in windows. Adobe Photoshop, CAD/CAM, Rosetta Stone, Matlab others. Grub did a workaround for that, but windows 7 particularly has other software with similar issues.

Some have issues with the names in the grub menu and one way to fix it is to copy the Vista entries to 40_custom and edit entry. Then turn off osprober, so old entries are not found. You can turn os prober back on if you add another system someday.

Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit title:
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

#If the new entry works:
#In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
#or
sudo chmod a-x /etc/grub.d/30_os-prober
#and another:
sudo update-grub

---

