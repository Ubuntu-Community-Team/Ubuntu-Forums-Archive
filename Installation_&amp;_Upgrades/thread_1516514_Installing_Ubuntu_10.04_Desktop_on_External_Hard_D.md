---
title: "Installing Ubuntu 10.04 Desktop on External Hard Drive"
date: 2010-06-23
forum: Installation &amp; Upgrades
---

### Post by Virtua-Touch on 2010-06-23
I have a portable 320 GB USB HP SimpleSave external hard drive, and I want to install Ubuntu 10.04 Desktop to use on both of my computers when Windows is letting me down. :P The last time I tried to install 10.04 a week after it came out, I was presented with tons of errors, even though I did it the same exact way I did it with 9.10 that worked. I would like some help on the subject of installing them on usb hard drives. Most the time, it's GRUB being antsy about where it's installed. IF I don't change where to install GRUB, it won't let me boot on any other computer, or USB port. Thanks in advance. 

[http://bit.ly/dBMedC](http://bit.ly/dBMedC)

---

### Post by darkod on 2010-06-23
You just have to install grub2 to the MBR of the ext hdd if you want to move it around and boot computers without it too.
Click the Advanced button at the last installer screen, and tell it to install to your usb hdd, for example /dev/sdb if that's the device name of the usb hdd.
And of course any computer you want to use it on has to be able to boot from usb.

---

### Post by Virtua-Touch on 2010-06-23
Ok. I shall try this.

---

### Post by efflandt on 2010-06-24
Installing and trying it on an external hard drive can be useful to iron out issues before actually installing it on an internal drive.  For example I discovered that the Asus mobo on my HP desktop PC from 2004 does not like the new default partition alignment of 10.04 and would not boot with that.  So I had to reinstall using **partman/alignment=cylinder** kernel boot parameter before it would work.

That gave me more confidence when installing it to my internal drive.  But I still have a strange issue with that PC only in that it boots fine from a 160 GB USB drive or the far end of its 200 GB internal drive, but it will not boot from farther out on a 500 GB USB drive (dumps to grub rescue with error: unknown filesystem, which is ext3).  It auto mounts the 500 GB USB drive partitions once Linux is running, and the 500 GB drive boots fine on 2 different laptops.

I also have to use either **nomodeset** or **radeon.modeset=0** on that desktop PC because the new default kernel mode setting (kms) of 10.04 is sluggish on that PC and interferes with suspend and hibernate.

---

### Post by Virtua-Touch on 2010-06-24
I got it to install and didn't boot it on the comp I installed it on. Instead, I took it to my other computer and it booted up fine, no lag, no missing mouse, GRUB wasn't yelling at me. Yay!

---

### Post by Virtua-Touch on 2010-06-24
Bad news. Trying to boot Ubuntu on my main computer this time to update it, my computer went straight to grub console, and won't let me boot. It says the kernel isn't loaded when I type in boot. How do I load my Ubuntu kernel which is on my external hard drive?

---

### Post by darkod on 2010-06-24
If you installed grub2 to the usb hdd, then your computer shouldn't have been affected.

It does sound like you messed up the bootloader on your main computer though.

If you run the boot info script, it will show more details. If you need instructions, here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by Virtua-Touch on 2010-06-25
This is what the results file shows. I have a 1 TB HDD (sdc), a 500 GB HDD (sdb), and a 160 GB HDD (sda). My external hard drive is sdf, which as you can see is split into three partitions, the main EXT4, the swap, and an extended partition. Also, my menu.lst file is missing in my /boot/grub folder. I think the problem is that GRUB 2 is installed in the MBR of the 160 and the 500 GB HDD's, which it shouldn't considering I only installed GRUB on my external. But what doesn't make sense is that it boots fine on my other computer (no Internet) yet on the computer with Internet, it doesn't boot. Just jumps into the GRUB console.

SO anyways, maybe this file will help. Thanks for the script. I tried looking through it and was trying to troubleshoot it myself but couldn't for the life of me figure it out. Thanks in advance for the help.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=927c8bc2-1bd8-48b3-b0d5-0750d9ca3fed)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks for 
    (UUID=16055c99-b22a-4544-9190-afcca3e15596)/boot/grub.
 => Windows is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sde
 => Grub 2 is installed in the MBR of /dev/sdf and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
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
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdf1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdf2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdf5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   312,576,715   312,576,653   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   976,769,023   976,766,976   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048 1,953,521,663 1,953,519,616   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 8036 MB, 8036285952 bytes
255 heads, 63 sectors/track, 977 cylinders, total 15695871 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sde1                  44    15,679,439    15,679,396   b W95 FAT32


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 319.4 GB, 319370035200 bytes
255 heads, 63 sectors/track, 38827 cylinders, total 623769600 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *          2,048   604,110,847   604,108,800  83 Linux
/dev/sdf2         604,112,894   623,767,551    19,654,658   5 Extended
/dev/sdf5         604,112,896   623,767,551    19,654,656  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        2254139D54137331                       ntfs       Storage                       
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5CBC3D1CBC3CF25E                       ntfs       Wayne's 2                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        60202E0D202DEB2C                       ntfs                                     
/dev/sdc: PTTYPE="dos" 
/dev/sde1        6EBC-27F2                              vfat       CRUZER                        
/dev/sde: PTTYPE="dos" 
/dev/sdf1        24691062-8b30-4dd3-8dc3-0b39b83907f2   ext4                                     
/dev/sdf2: PTTYPE="dos" 
/dev/sdf5        970a3bb8-c0b0-4ac3-ab71-53cfec0774a0   swap                                     
/dev/sdf: PTTYPE="dos" 
error: /dev/sdd: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdf1        /media/24691062-8b30-4dd3-8dc3-0b39b83907f2 ext4       (rw,nosuid,nodev,uhelper=udisks)


=========================== sdf1/boot/grub/grub.cfg: ===========================

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
set root='(hd4,1)'
search --no-floppy --fs-uuid --set 24691062-8b30-4dd3-8dc3-0b39b83907f2
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
set root='(hd4,1)'
search --no-floppy --fs-uuid --set 24691062-8b30-4dd3-8dc3-0b39b83907f2
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd4,1)'
	search --no-floppy --fs-uuid --set 24691062-8b30-4dd3-8dc3-0b39b83907f2
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=24691062-8b30-4dd3-8dc3-0b39b83907f2 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd4,1)'
	search --no-floppy --fs-uuid --set 24691062-8b30-4dd3-8dc3-0b39b83907f2
	echo	'Loading Linux 2.6.32-22-generic-pae ...'
	linux	/boot/vmlinuz-2.6.32-22-generic-pae root=UUID=24691062-8b30-4dd3-8dc3-0b39b83907f2 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd4,1)'
	search --no-floppy --fs-uuid --set 24691062-8b30-4dd3-8dc3-0b39b83907f2
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd4,1)'
	search --no-floppy --fs-uuid --set 24691062-8b30-4dd3-8dc3-0b39b83907f2
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdc1)" {
	insmod ntfs
	set root='(hd2,1)'
	search --no-floppy --fs-uuid --set 60202e0d202deb2c
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdf1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdf1 during installation
UUID=24691062-8b30-4dd3-8dc3-0b39b83907f2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdf5 during installation
UUID=970a3bb8-c0b0-4ac3-ab71-53cfec0774a0 none            swap    sw              0       0

=================== sdf1: Location of files loaded by Grub: ===================


  49.5GB: boot/grub/core.img
 268.5GB: boot/grub/grub.cfg
  49.5GB: boot/initrd.img-2.6.32-22-generic-pae
  49.5GB: boot/vmlinuz-2.6.32-22-generic-pae
  49.5GB: initrd.img
  49.5GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdf2

00000000  02 89 c2 74 3c 8d 74 26  00 8d bc 27 00 00 00 00  |...t<.t&...'....|
00000010  ff 45 00 bf 94 c0 08 b7  8d 43 14 be 7d 17 00 00  |.E.......C..}...|
00000020  89 7c 24 10 8b 54 24 60  89 74 24 0c 89 44 24 08  |.|$..T$`.t$..D$.|
00000030  8b 42 18 89 14 24 89 44  24 04 e8 21 08 d0 ff eb  |.B...$.D$..!....|
00000040  80 8b 4c 24 60 8b 52 4c  8b 81 58 01 00 00 8b 08  |..L$`.RL..X.....|
00000050  89 54 24 04 89 04 24 ff  51 14 89 44 24 24 3b 45  |.T$...$.Q..D$$;E|
00000060  04 7c ad 3b 45 08 7f a8  8b b3 a0 00 00 00 89 74  |.|.;E..........t|
00000070  24 28 89 f2 8b 46 04 83  f8 26 0f 84 b1 00 00 00  |$(...F...&......|
00000080  83 f8 72 74 07 3d 91 00  00 00 75 84 8b 7c 24 28  |..rt.=....u..|$(|
00000090  8b 44 24 60 89 7c 24 04  89 04 24 e8 a0 b4 d3 ff  |.D$`.|$...$.....|
000000a0  84 c0 0f 85 68 ff ff ff  8b 77 7c 85 f6 0f 85 5d  |....h....w|....]|
000000b0  ff ff ff 8b 4c 24 28 8b  89 84 00 00 00 89 4c 24  |....L$(.......L$|
000000c0  20 83 79 04 26 0f 85 45  ff ff ff 8d 44 24 2c b9  | .y.&..E....D$,.|
000000d0  07 00 00 00 89 44 24 04  8b 44 24 28 89 4c 24 08  |.....D$..D$(.L$.|
000000e0  05 90 00 00 00 89 04 24  e8 73 ad d3 ff 84 c0 0f  |.......$.s......|
000000f0  84 1b ff ff ff 8b 54 24  28 0f b6 83 a4 00 00 00  |......T$(.......|
00000100  81 7a 04 91 00 00 00 8b  44 84 2c 0f 84 02 01 00  |.z......D.,.....|
00000110  00 8b 54 24 24 01 d0 89  44 24 24 3b 45 04 0f 8c  |..T$$...D$$;E...|
00000120  ec fe ff ff 3b 45 08 0f  8f e3 fe ff ff 8b 54 24  |....;E........T$|
00000130  20 8b 42 74 85 c0 0f 84  d4 fe ff ff 8b 74 24 60  | .Bt.........t$`|
00000140  8b 40 0c 8b 56 2c 8b 0a  89 14 24 89 44 24 04 ff  |.@..V,....$.D$..|
00000150  51 04 ba 8c c0 08 b7 b9  05 00 00 00 fc 89 d7 89  |Q...............|
00000160  c6 f3 a6 0f 85 a7 fe ff  ff 8b 5d 0c b9 f1 c0 08  |..........].....|
00000170  b7 bf ff ff ff ff 8b 44  24 24 89 4c 24 04 29 d8  |.......D$$.L$.).|
00000180  8d 5c 24 3c 89 1c 24 89  44 24 08 e8 40 b6 88 00  |.\$<..$.D$..@...|
00000190  8b 74 24 60 8b 46 2c 8b  10 89 5c 24 04 89 04 24  |.t$`.F,...\$...$|
000001a0  ff 12 ba 02 00 00 00 89  54 24 14 89 7c 24 0c 89  |........T$..|$..|
000001b0  44 24 10 8b 7d 0c 29 7c  24 24 8b 44 24 24 00 fe  |D$..}.)|$$.D$$..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 e8 2b 01 00 00  |............+...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdd 
```

[COLOR="DarkRed"]**I've decided I'm going to wipe the drive and start over, but I'm gonna make sure I do it right.**[/COLOR]

---

### Post by oldfred on 2010-06-26
You just need to set drive order correctly. Your grubs in sda & sdb point to partitions that are not valid anymore.

If you set internal to boot from sdc it should boot directly to windows. If you set to boot from external it should boot you Ubuntu install in the external.

Set boot order to external, then internal. 

Set drive order to boot sdc 1000GB first.

---

### Post by Virtua-Touch on 2010-06-26
But I always get dropped into the GRUB console. I'll try setting it up so it's external first and then my internal.

---

### Post by darkod on 2010-06-26
> **Virtua-Touch said:**
> But I always get dropped into the GRUB console. I'll try setting it up so it's external first and then my internal.

That's because you have the wrong disk set as first option. As mentioned, when considering only hdd order (which excludes ext hdds), you should always have sdc, the 1TB disk, as first.

And whether you boot from your ext hdd or not, it depends which device is first, USB-HDD or HDD. But that has nothing to do with the boot order of the actual internal hdds. On sda and sdb you have old broken grubs and if you boot any of them as first you will get the console.

---

### Post by Virtua-Touch on 2010-06-26
Thanks for the info. I'll try it out.

---

### Post by Virtua-Touch on 2010-06-27
It did not work. It just bypassed the GRUB console and booted straight into Windows. I had my BIOS setup hdd priority: 1 - HP External HDD, 2 - 1000 GB HDD, 3 - 500 GB HDD, 4 - 160 GB HDD and then boot priority 1 - HP External HDD, 2 - CDROM, 3 - Other thingy. I think with the current setup, I'm going to try and wipe it and try one more time and see if it will boot. (I have two ubuntus on my hdd right now, one from this comp and one that I installed on the other comp)

No dice. Dropped me into the grub console again. I don't understand this at all. I've never installed GRUB on any of these hard drives before. How did it make its way into the other hard drives? It's almost the hair pulling point.

---

### Post by Virtua-Touch on 2010-06-28
Sorry for the triple post but I really need this working.

---

### Post by oldfred on 2010-06-28
Well you have the internal set to the sdc drive and it boots windows ok.

The external should boot. Did you by any chance unplug the 8GB USB flash drive before booting. Then the external is sde not sdf and that may cause confusion. The search using UUID should correct the error in set root if the drive numbering changes.

I did the same thing with my USB flash drives. I installed from sde to sdf and removed sde. I had to manually edit the menu entry to get it to boot and then reinstall grub and update grub to fix it.

Do you get a grub menu when you boot from the external?

---

### Post by Virtua-Touch on 2010-06-29
No. My computer turns on, shows up the screen with Memory testing, hard drives, etc etc, and then it drops straight into grub console.

---

### Post by darkod on 2010-06-29
This is becoming very confusing. Are you telling us you get a grub rescue console even if you unplug the ext hdd, unplug the usb stick, set the 1TB disk as first hdd to boot from and try to boot???

That's almost impossible. You have windows bootloader on sdc according to the script, and windows on it. So it should just boot windows if that's the first hdd to boot from.

Does it still not work?

---

### Post by Virtua-Touch on 2010-06-29
Alright. Let me straight some things out for you.

In my BIOS, I have it set up like this

1st Drive - HP External HDD
2nd Drive - 1000 GB HDD 
3rd Drive - 500 GB HDD (Default)
4th Drive - 160 GB HDD (Default)

My boot priority list is as follows:

1st Device - HP External HDD
2nd Device - CDROM
3rd Device - Floppy

If my external hard drive is not plugged in, I boot into Windows (1TB Drive) fine without any messages or consoles showing up.

If I plug my external in, it is the first drive to boot so it drops me into the GRUB console. It's displayed:

```
[CENTER]GRUB version 0.98[/CENTER]

[ Minimal BASH-like line editing is supported. For the first word, TAB 
 lists possible command completions. Anywhere else TAB lists the possible
 completions of device/filename. ]

grub>
```

I'm not sure if that's the rescue console, because I've never had this problem before. I haven't tried unplugging my flash drives. I'll see if that fixes it.

---

### Post by darkod on 2010-06-29
OK, I thought you complain that you can't boot windows even with the ext hdd unplugged. Lets move on.

If it says Grub version 0.98 that's grub1 or grub legacy you have on your ext hdd. It shouldn't be there at all. So it seems some commands that should have been executed during this topic earlier to install grub2 were not run or not successful.

But lets see the current situation. Connect the ext hdd and run the script again, and post the results. Don't try anything until we see them. If we are lucky you only need to reinstall grub2 to the MBR of the ext hdd because you need grub2 there, not grub1.

---

### Post by Virtua-Touch on 2010-06-29
I apologize. It's GRUB version 1.98-1ubuntu5. I was trying to remember out of sheer memory. I have a video uploading of exactly what happens. I have removed my two flash drives, by the way.

This video shows me in the BIOS and how my drives are setup and then booting into Ubuntu.

[http://www.youtube.com/watch?v=gTREiM3RmMk&feature=player_embedded](http://www.youtube.com/watch?v=gTREiM3RmMk&feature=player_embedded)

---

### Post by darkod on 2010-06-29
> **Virtua-Touch said:**
> I apologize. It's GRUB version 1.98-1ubuntu5. I was trying to remember out of sheer memory. I have a video uploading of exactly what happens. I have removed my two flash drives, by the way.

This video shows me in the BIOS and how my drives are setup and then booting into Ubuntu.

[http://www.youtube.com/watch?v=gTREiM3RmMk&feature=player_embedded](http://www.youtube.com/watch?v=gTREiM3RmMk&feature=player_embedded)

OK, I think we probably tried this but lets give it another shot. If you boot with ubuntu cd, return cd-rom before the ext hdd and boot with the cd in live mode with the ext hdd connected. If you are booting from usb ubuntu stick, boot with it and connect the ext hdd later.

To make sure your 320GB ext hdd is still sdf, check with fdisk:

sudo fdisk -l

If it's still sdf, the partition(s) might have mounted when you plugged the usb ext hdd, so just in case unmount and then mount to reinstall grub2:

sudo umount /dev/sdf1 (not a typo, the command is umount)
sudo mount /dev/sdf1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdf

Restart wtihout the stick (or cd) but with the usb hdd connected and if we are lucky, you will see the grub2 menu.

---

### Post by Virtua-Touch on 2010-06-29
Damn, it didn't work. Still jumping into the GRUB console.

Do you think burning the alternate install and using that might work?

---

### Post by darkod on 2010-06-29
> **Virtua-Touch said:**
> Damn, it didn't work. Still jumping into the GRUB console.

Do you think burning the alternate install and using that might work?

I have no clue. I don't know why it's doing this, so I don't know if the alternate cd can help.

---

### Post by Virtua-Touch on 2010-06-29
I'm starting to think that If I unplug my 160 and 500 it might boot. Maybe it's the remnants of grub on those drives that's causing it.

---

### Post by darkod on 2010-06-29
> **Virtua-Touch said:**
> I'm starting to think that If I unplug my 160 and 500 it might boot. Maybe it's the remnants of grub on those drives that's causing it.

I thought about that, but it all points that you are booting from the ext hdd when connected. You can give it a shot anyway.

---

### Post by Virtua-Touch on 2010-06-29
Well, I think I've figured it out. This is what I did.

1) Unplugged 160 and 500 GB Power cables
2) Started up computer
3) Unfortunately, didn't boot right away. Gave me the GRUB console
4) Typed 'ls' to search for drives
5) hd0 and hd1 showed up which were my ext and my 1000gb
6) Typed search -f /vmlinuz Which returned hd0,1 (honestly doesn't make sense, but my dad has the 1TB in an awkward order.
7) Typed set prefix=(hd0,1)/boot/grub
8) Typed set root=(hd0,1)
9) Typed ls /boot
10) Typed insmod /boot/grub/linux.mod
11) Typed linux /vmlinuz root=/dev/sdb1 ro (My external I guess is SDB1 but (hd0,1)
12) Typed initrd /initrd.img
13) Initiated boot command.
14) Booted.

I'm posting from my ubuntu right now and updating as I type. 

Thanks for all the help. Now, maybe when I plug them in again, I'll probably just have to figure which drive my ext is again so I don't have to keep unpluggin my internals.

For anyone else needing help for this, go to this link and scroll down to Booting from the Rescue Mode.
[http://www.ubuntuforums.org/showthread.php?t=1195275](http://www.ubuntuforums.org/showthread.php?t=1195275)

---

