---
title: "Grub2 will not boot other OS on a 2nd sata drive?"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by xoros on 2010-05-10
My bios seems to support only booting a drive in position sata-0

Ubuntu 10.04 install is on the drive in sata-0  
Vista install is a second drive in sata-1

*Ubuntu loads fine but when trying to load Vista from grub2 menu I get:
> **error: hd1,1 cannot get C/H/S values.**

*Vista will boot fine if I swap the physical sata cables and place the vista drive in sata-0. 
(But then I have no way to boot Ubuntu - get similar error when I've tried Easybcd to boot Ubuntu (then on sata-1) - so I reverted back to Vista's bootloader with bootrec.exe FixBoot / FixMbr )
Everything comes up fine when I run update-grub.

Is there any way to get grub to boot the Vista drive?  
Or is this a lost cause due to my bios? 
If anyone can help, it would be appreciated.


I ran bootinfo script:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sda2: _________________________________________________________________________

    File system:       xfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       xfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       xfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       xfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       514,079       514,017  83 Linux
/dev/sda2             514,080   105,370,334   104,856,255  83 Linux
/dev/sda3         105,370,335   106,414,559     1,044,225  82 Linux swap / Solaris
/dev/sda4         106,414,621   976,768,064   870,353,444   5 Extended
/dev/sda5         106,414,623   959,787,359   853,372,737  83 Linux
/dev/sda6         976,559,283   976,768,064       208,782  83 Linux
/dev/sda7         959,787,423   976,559,219    16,771,797  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   312,496,127   312,494,080   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        0e5a8bc3-1c6a-4ed3-a724-bda4c26ab334   ext2       boot                          
/dev/sda2        3adc06f8-dbad-4143-b533-b0f4b8446273   xfs        root                          
/dev/sda3        7ef54bd1-3613-42cf-9292-717b82ee2847   swap                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        aa711fe6-6e16-4a26-b528-26a8bf41daa2   xfs        home                          
/dev/sda6        1ab6aeaf-9708-4910-a7b5-a30d08d2f6c4   xfs        tmp                           
/dev/sda7        a24188bf-0cf5-4586-bed6-d624a860b396   xfs        var                           
/dev/sda: PTTYPE="dos" 
/dev/sdb1        521E29011E28DFA9                       ntfs                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        xfs        (rw)
/dev/sda1        /boot                    ext2       (rw)
/dev/sda5        /home                    xfs        (rw)
/dev/sda6        /tmp                     xfs        (rw)
/dev/sda7        /var                     xfs        (rw)
/dev/sdb1        /media/521E29011E28DFA9  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


============================= sda1/grub/grub.cfg: =============================

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
insmod xfs
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 3adc06f8-dbad-4143-b533-b0f4b8446273
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 0e5a8bc3-1c6a-4ed3-a724-bda4c26ab334
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 0e5a8bc3-1c6a-4ed3-a724-bda4c26ab334
	linux	/vmlinuz-2.6.32-22-generic root=UUID=3adc06f8-dbad-4143-b533-b0f4b8446273 ro   quiet splash
	initrd	/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 0e5a8bc3-1c6a-4ed3-a724-bda4c26ab334
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/vmlinuz-2.6.32-22-generic root=UUID=3adc06f8-dbad-4143-b533-b0f4b8446273 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 0e5a8bc3-1c6a-4ed3-a724-bda4c26ab334
	linux	/vmlinuz-2.6.32-21-generic root=UUID=3adc06f8-dbad-4143-b533-b0f4b8446273 ro   quiet splash
	initrd	/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 0e5a8bc3-1c6a-4ed3-a724-bda4c26ab334
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/vmlinuz-2.6.32-21-generic root=UUID=3adc06f8-dbad-4143-b533-b0f4b8446273 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 0e5a8bc3-1c6a-4ed3-a724-bda4c26ab334
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 0e5a8bc3-1c6a-4ed3-a724-bda4c26ab334
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set 521e29011e28dfa9
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: grub/core.img
    .0GB: grub/grub.cfg
    .0GB: initrd.img-2.6.32-21-generic
    .0GB: initrd.img-2.6.32-22-generic
    .0GB: vmlinuz-2.6.32-21-generic
    .0GB: vmlinuz-2.6.32-22-generic

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=3adc06f8-dbad-4143-b533-b0f4b8446273 /               xfs     defaults        0       1
# /boot was on /dev/sda1 during installation
UUID=0e5a8bc3-1c6a-4ed3-a724-bda4c26ab334 /boot           ext2    defaults        0       2
# /home was on /dev/sda5 during installation
UUID=aa711fe6-6e16-4a26-b528-26a8bf41daa2 /home           xfs     defaults        0       2
# /tmp was on /dev/sda6 during installation
UUID=1ab6aeaf-9708-4910-a7b5-a30d08d2f6c4 /tmp            xfs     defaults        0       2
# /var was on /dev/sda7 during installation
UUID=a24188bf-0cf5-4586-bed6-d624a860b396 /var            xfs     defaults        0       2
# swap was on /dev/sda3 during installation
UUID=7ef54bd1-3613-42cf-9292-717b82ee2847 none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


    .3GB: initrd.img
    .3GB: initrd.img.old
    .2GB: vmlinuz
    .2GB: vmlinuz.old
```

---

### Post by frantid on 2010-05-10
Your second drive doesn't start on sector 63, the usual ntfs start sector.  Bios might be okay loading it, but seems like grub is having a problem loading it.

could you run:

```
sudo parted /dev/sdb unit s print
```

How was this drive used in the past?  Did you format especially in this manner, was it part of a raid?  I would run some drive check tests on it.  Like from within gparted or with fsck and with testdisk.

---

### Post by xoros on 2010-05-10
Thank you for the reply Frantid. 

The drive had always just been the single drive in the system,  I had formatted it with Vista's install disk when I had loaded Vista.  

Here is the output you requested:
```
Model: ATA WDC WD1600ADFS-7 (scsi)
Disk /dev/sdb: 312500000s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End         Size        Type     File system  Flags
 1      2048s  312496127s  312494080s  primary  ntfs         boot

```

Is there a way to correct this?

---

### Post by frantid on 2010-05-10
I want to double check somethings.  That was just my first instinct after looking at it.

if you have gparted, can you select that drive and run a check on it?  can't do fsck because it's ntfs

edit -- I mean partition.

---

### Post by xoros on 2010-05-10
gparted showed it completed, I'm assuming no errors were found. 

[IMG]http://img72.imageshack.us/img72/1713/gpartedfscheck.png[/IMG]

---

### Post by frantid on 2010-05-10
don't resize it, give me a second here.

---

### Post by frantid on 2010-05-10
boot into grub, highlight the vista menu entry press e

Make it look like this

```
insmod ntfs
set root='(hd1)'
chainloader +1
```You can just use the arrow keys to move around after you pressed "e", just backspace over what you don't want.

if that one doesn't work try this one

```
insmod ntfs
set root='(hd1,1)'
chainloader +1
```


edit:  I forgot to say after you edit the entry press Ctrl-x to boot.

---

### Post by xoros on 2010-05-10
Ok, I took out this line that was there 
```
search --no-floppy --fs-uuid --set 521e29..(etc)
```

Made it look like your code, 
hit ctrl x and it just kept showing the same edit screen. :confused: 
It did that with both codes. 
  
So, then hit esc and went back to main menu, but just showed error again upon selecting vista. 

Should I get rid of that unallocated space somehow that shows in gparted?

---

### Post by frantid on 2010-05-10
No, vista get's sticky about it.  If you resize vista, it won't boot from there anymore. 

When you're editing, Ctrl-x should work.  you have to hit them at the same time.

You can also, push c from the main menu and type it in.  You can use "tab" key to complete the word you're typing to make it easier, then type boot

---

### Post by xoros on 2010-05-10
Ctrl-x just kept re-displaying the edit section, like it just looped the edit screen. 
I'll try c - command line.

---

### Post by darkod on 2010-05-10
> **frantid said:**
> Your second drive doesn't start on sector 63, the usual ntfs start sector.  Bios might be okay loading it, but seems like grub is having a problem loading it.

could you run:

```
sudo parted /dev/sdb unit s print
```How was this drive used in the past?  Did you format especially in this manner, was it part of a raid?  I would run some drive check tests on it.  Like from within gparted or with fsck and with testdisk.

Sorry for jumping in, but I don't think it's the drive not starting at sector 63, it's the actual partition #1. It doesn't really matter, you can for example leave unallocated space in front and create partition at the back of the disk. It shouldn't care.

It seems to be more related with BIOS/mobo.

Do you have only two SATA ports? Since you never mentioned trying the disk in a third port, I guess yes.
Check in BIOS for any strange settings to SATA interface, like RAID, AHCI, Native IDE. Using native IDE is fine but it should also work fine as AHCI. You don't want RAID of course.

See if there is maybe some setting telling SATA1 to be something else.

You said even EasyBCD produces error trying to boot ubuntu when the ubuntu disk is on SATA1 so it doesn't sound OS related.

---

### Post by frantid on 2010-05-10
No worries, I can always learn more.

---

### Post by xoros on 2010-05-10
First here is what output from using 'c' in grub:

```
grub> insmod ntfs
grub> set root='(hd1)'
grub> chainloader +1
error: hd1 cannot get C/H/S values.
grub> insmod ntfs
grub> set root='(hd1,1)'
grub> chainloader +1
error: hd1,1 cannot get C/H/S values.
grub> boot
error: no loaded kernel.
grub> 
```

In response to darko;  There is only an option to turn Raid "On" or "Off" per sata hdd, and to disable/enable the drive.  

It shows only on SATA-0: "**this device is controlled by bios**"  

And the boot order just shows hdd in the list - no sub-specific options for that.  

In other words, grub will NOT be able to boot anything other than SATA-0 (which is the only drive supported in bios) ??

---

### Post by frantid on 2010-05-10
if you're in the grub command line and you do 

ls (hd1,1)/

does it show anything?

---

### Post by xoros on 2010-05-10
@frantid 
The ls command returns the same error:
```
error: hd1,1 cannot get C/H/S values.
```

---

### Post by frantid on 2010-05-10
have you ever run testdisk against this drive?  When it asks if the partition was created by vista, hit yes.

---

### Post by xoros on 2010-05-10
An additional note though; 
I am able to mount and see all my Vista files in Ubuntu. 

If nothing else does someone know a wiring diagram so I can put in a switch to switch the sata positions??  

Most sata switches i've found online only control the power to the drives.. in my case in need to control the sata positions.

---

### Post by xoros on 2010-05-10
@frantid 
I will try testdisk and report back, have not tried that yet.
thanks

---

### Post by darkod on 2010-05-10
All this is extremely weird. :)

The setting saying this device is controlled by BIOS, does it say the same for SATA1 or it doesn't have that option?

If you go in Basic or Advanced BIOS settings menu I guess it lists both drives right?

Very strange.

---

### Post by frantid on 2010-05-10
If you want to read about the ugliness of the vista created partition:

[http://thestarman.pcministry.com/asm/mbr/VistaMBR.htm](http://thestarman.pcministry.com/asm/mbr/VistaMBR.htm)

Notice they dropped the practice for win7.  Look at the fdisk for that drive, I've never seen a drive with straight even 000's on capacity.

You maybe able to resize it inside vista with disk management.

got to go for a sec.

---

### Post by xoros on 2010-05-10
Edit: see post below for other testdisk results.. I guess there is 1 error. 
Seeing how testdisk shows chs values is there any way to manually use those values in grub (per the grub chs error asking for the values)?

[IMG]http://img339.imageshack.us/img339/908/testdisk1.png[/IMG]

---

### Post by xoros on 2010-05-10
@darko
In the bios it only lists the 4 hdd sata's:
sata-0
sata-1
sata-2
sata-3

And 2 other sata entries for optical drives:
sata-4
sata-5  

When I choose sata-0,  yes it only states near the bottom of the screen that; that one is controlled by bios.  
There is no other option for "being controlled by bios" on sata-0 or any of the other sata-(x) entries.  

It's just like a sentence at the bottom of sata-0's screen.

---

### Post by xoros on 2010-05-10
What is odd during the testdisk analyze, I saw no entry for vista so I picked Intel/pc format in the options...  during the analyze it came up with linux entries (possible from a previous Ubuntu install I had on that hard drive)??  and 1 error message. 

From the log file: 
```
Warning: can't get size for Disk /dev/mapper/control - 0 B - CHS 1 1 1, sector size=512
Hard disk list
Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63, sector size=512 - ATA WDC WD5000AAKS-0
Disk /dev/sdb - 160 GB / 149 GiB - CHS 19452 255 63, sector size=512 - ATA WDC WD1600ADFS-7

Partition table type (auto): Intel
/dev/sdb: Device Configuration Overlay (DCO) present.
Disk /dev/sdb - 160 GB / 149 GiB - ATA WDC WD1600ADFS-7
Partition table type: Intel

Analyse Disk /dev/sdb - 160 GB / 149 GiB - CHS 19452 255 63
Geometry from i386 MBR: head=255 sector=63
Current partition structure:
 1 * HPFS - NTFS              0  32 33 19451 250 63  312494080
Computes LBA from CHS for Disk /dev/sdb - 160 GB / 149 GiB - CHS 19453 255 63
Allow partial last cylinder : Yes
search_vista_part: 1

search_part()
Disk /dev/sdb - 160 GB / 149 GiB - CHS 19453 255 63
     Linux                    0   1  1  2431 254 62   39070016
     EXT3 Large file Sparse superblock Recover, 20 GB / 18 GiB
     Linux                16871  27 53 17864  26 50   15952480
     EXT3 Large file Sparse superblock Recover, 8167 MB / 7789 MiB
     Linux                18379   1  1 19439 254 57   17044896
     EXT3 Large file Sparse superblock, 8726 MB / 8322 MiB
     Linux                19440   1  1 19451 254 58     192712
     EXT3 Sparse superblock, 98 MB / 94 MiB
get_geometry_from_list_part_aux head=255 nbr=6
get_geometry_from_list_part_aux head=8 nbr=3
get_geometry_from_list_part_aux head=16 nbr=3
get_geometry_from_list_part_aux head=32 nbr=2
get_geometry_from_list_part_aux head=64 nbr=2
get_geometry_from_list_part_aux head=128 nbr=2
get_geometry_from_list_part_aux head=240 nbr=3
get_geometry_from_list_part_aux head=255 nbr=6
```

---

### Post by darkod on 2010-05-10
> **xoros said:**
> @darko
In the bios it only lists the 4 hdd sata's:
sata-0
sata-1
sata-2
sata-3

And 2 other sata entries for optical drives:
sata-4
sata-5  

When I choose sata-0,  yes it only states near the bottom of the screen that; that one is controlled by bios.  
There is no other option for "being controlled by bios" on sata-0 or any of the other sata-(x) entries.  

It's just like a sentence at the bottom of sata-0's screen.

Have you tried putting the vista disk on sata2 or sata3? Even sata4 and sata5 should work, they are not specified to be used only for optical drives, it depends what device you plug in.

---

### Post by xoros on 2010-05-10
> **darkod said:**
> Even sata4 and sata5 should work, they are not specified to be used only for optical drives, it depends what device you plug in.

Well on my motherboard the slots (cable sockets) for 4 and 5 are specifically labeled "ODD" and the others are labeled "HDD".  Not sure if that made a difference.

Will try what you suggest and tell results, thanks.

---

### Post by xoros on 2010-05-10
Just messing around in bios,  I turned on all the sata entries and it ended up bios assigning sata-3 to the vista drive! 

So now in bios it shows in the sata-3 entry: "controlled by bios"  -- along with sata-0's entry showing the same sentence. 

Grub now boots into vista perfectly ... wow.  

Thank you both for your help in this matter,  I guess it ended up being either: 

a. I should have from the start plugged it into the sata-3 slot??
or
b. I had to let bios assign it by turning all sata ports on

Either way, i'm glad its working,  thank you both again!

---

### Post by darkod on 2010-05-10
If you didn't move the cable it would mean it was in sata3 all the time, not in sata1. But the port was not enabled in BIOS.

Anyway, good to hear it's working fine now. Enjoy it. :)

---

### Post by frantid on 2010-05-10
Great job!

I almost never suspect hardware, ... almost unless some new parts have been .  Thanks darkod for jumping in.

---

### Post by xoros on 2010-05-10
> **darkod said:**
> If you didn't move the cable it would mean it was in sata3 all the time, not in sata1. But the port was not enabled in BIOS.


But here is the thing,  I used the sata-1 slot w/ sata-1 cable.  So I figured I only needed to enable sata-1 selection in bios.  

Bios showed that drive (the drive info was listed on sata-1's screen) was in sata-1, but it didn't have that "**this drive is controlled by bios**" message. 

So how did bios control it from sata-3 in the first place when it isn't (**and still is not**) plugged into the sata-3 spot?? 

:confused:  I don't know I guess my bios is just really weird?

**This brings up the question should I move the cable physically to the sata-3 socket on motherboard?**

---

### Post by darkod on 2010-05-10
Leave everything as it is, and enjoy it. :)

---

