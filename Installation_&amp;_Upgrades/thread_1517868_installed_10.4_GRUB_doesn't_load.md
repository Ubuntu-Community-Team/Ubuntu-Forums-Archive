---
title: "installed 10.4 GRUB doesn't load"
date: 2010-06-25
forum: Installation &amp; Upgrades
---

### Post by Thomas,Bakker on 2010-06-25
Ok, i have Vista 64Bits Ultimate installed on an 1TB hard disk whit 3 partitons

I have a 2nd 160GB HD in my system which i installed Ubuntu 10.4 on.
All went ok, except after the installation finished and the system rebooted it booted straight into windows, whitout ever displaying GRUB.

Now i found a way to boot either system, by using the bios and setting the applicable HD to 1st device. (or something similar)

Any way on how to solve this? keeping to have to enter the BIOS to select the HD and Thus OS i want to boot aint very practical.

(im currently using ubuntu BTW)

i saw from the following thread;
[http://ubuntuforums.org/showthread.php?t=1517678](http://ubuntuforums.org/showthread.php?t=1517678)
that there is an boot info script which helps you guys helping me, here's the output.

```
    Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/mapper/pdc_ebfehihaia

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: unknown filesystem type ''

pdc_ebfehihaia1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

pdc_ebfehihaia2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

pdc_ebfehihaia3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

pdc_ebfehihaia4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

pdc_ebfehihaia5: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   299,808,767   299,806,720  83 Linux
/dev/sda2         299,810,814   312,580,095    12,769,282   5 Extended
/dev/sda5         299,810,816   312,580,095    12,769,280  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   204,802,047   204,800,000   7 HPFS/NTFS
/dev/sdb2         204,802,048   716,802,047   512,000,000   7 HPFS/NTFS
/dev/sdb3         716,802,048 1,331,320,815   614,518,768   7 HPFS/NTFS
/dev/sdb4       1,331,320,832 1,953,521,663   622,200,832   f W95 Ext d (LBA)
/dev/sdb5       1,331,322,880 1,953,521,663   622,198,784   6 FAT16


Drive: pdc_ebfehihaia ___________________ _____________________________________________________

Disk /dev/mapper/pdc_ebfehihaia: 1000.2 GB, 1000204795904 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953524992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/pdc_ebfehihaia1   *          2,048   204,802,047   204,800,000   7 HPFS/NTFS
/dev/mapper/pdc_ebfehihaia2        204,802,048   716,802,047   512,000,000   7 HPFS/NTFS
/dev/mapper/pdc_ebfehihaia3        716,802,048 1,331,320,815   614,518,768   7 HPFS/NTFS
/dev/mapper/pdc_ebfehihaia4      1,331,320,832 1,953,521,663   622,200,832   f W95 Ext d (LBA)
/dev/mapper/pdc_ebfehihaia5      1,331,322,880 1,953,521,663   622,198,784   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/pdc_ebfehihaia1 FAAC296DAC29261B                       ntfs                                     
/dev/mapper/pdc_ebfehihaia2 B8D24E8ED24E5134                       ntfs       Data                          
/dev/mapper/pdc_ebfehihaia3 ECDA7A9DDA7A642C                       ntfs       Spellen                       
/dev/mapper/pdc_ebfehihaia: PTTYPE="dos" 
/dev/sda1        13371c02-0be0-4597-a2be-010e6d383354   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        33db30e2-91bc-4286-8056-5bbee722c7a6   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        FAAC296DAC29261B                       ntfs                                     
/dev/sdb2        B8D24E8ED24E5134                       ntfs       Data                          
/dev/sdb3        ECDA7A9DDA7A642C                       ntfs       Spellen                       
/dev/sdb4: PTTYPE="dos" 
/dev/sdb                                                promise_fasttrack_raid_member                               
error: /dev/mapper/pdc_ebfehihaia4: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 13371c02-0be0-4597-a2be-010e6d383354
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
search --no-floppy --fs-uuid --set 13371c02-0be0-4597-a2be-010e6d383354
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
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 13371c02-0be0-4597-a2be-010e6d383354
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=13371c02-0be0-4597-a2be-010e6d383354 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 13371c02-0be0-4597-a2be-010e6d383354
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=13371c02-0be0-4597-a2be-010e6d383354 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 13371c02-0be0-4597-a2be-010e6d383354
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 13371c02-0be0-4597-a2be-010e6d383354
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=33db30e2-91bc-4286-8056-5bbee722c7a6 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  86.0GB: boot/grub/core.img
    .2GB: boot/grub/grub.cfg
  86.0GB: boot/initrd.img-2.6.32-21-generic
  86.0GB: boot/vmlinuz-2.6.32-21-generic
  86.0GB: initrd.img
  86.0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  d9 d9 c8 d0 c8 c0 67 67  e2 e0 e9 fb d9 fb d9 fb  |......gg........|
00000010  d9 fa c8 f8 c8 d0 65 e5  ed ed fa fb fb fb fb fb  |......e.........|
00000020  fb 8c c8 88 c8 f8 35 35  35 e7 8b 8c 8b 9c 8b 9c  |......555.......|
00000030  8c ac c8 98 c8 f0 35 65  65 e2 8c 9c 8d 9c 9d 9d  |......5ee.......|
00000040  9e bd c8 a0 c8 88 1d 37  76 e6 ad 9f be af bf af  |.......7v.......|
00000050  bf 9e c8 b0 c8 90 a1 2b  0a a8 9d 8d 9e 8d 9d 9d  |.......+........|
00000060  9d 9d c8 a8 c8 80 b3 94  b6 37 8c fb 8c eb 8c fb  |.........7......|
00000070  8d fb c8 80 c8 e0 b0 b0  b0 30 ea ea ea da ea da  |.........0......|
00000080  eb ea c8 e0 c8 d0 a2 b2  b0 b0 d9 d9 d9 d9 d9 d9  |................|
00000090  d9 d9 c8 d0 c8 c0 b6 36  36 36 c9 c8 c9 c8 d9 c8  |.......666......|
000000a0  d9 c8 c8 d8 c8 c0 9f 97  97 97 c8 c8 c8 c8 c8 c8  |................|
000000b0  c8 c8 c8 c0 c8 c8 32 32  22 20 c8 c8 c8 c8 c8 c8  |......22" ......|
000000c0  c8 c8 c8 c0 c8 c8 9f 9f  9d 9d c8 c8 c8 c8 c8 c8  |................|
000000d0  c8 c8 c9 c8 c8 c8 9d 9d  9d 9d c8 c8 c8 c8 c8 c8  |................|
000000e0  c8 c8 c8 c0 c8 c8 77 77  67 67 c8 d8 c8 d9 c8 d9  |......wwgg......|
000000f0  d8 d9 c8 d8 c8 c0 1d 3d  7d 7d d9 d9 d9 d9 d9 d9  |.......=}}......|
00000100  d9 d9 c8 d8 c8 c0 67 67  e2 e0 d9 d9 d9 d9 d9 d9  |......gg........|
00000110  d9 d9 c8 d0 c8 d8 7d 3d  37 77 e9 ea e9 ea e9 ea  |......}=7w......|
00000120  e9 ea c8 e8 c8 d0 e5 c5  c5 45 fa fb fa fb fa fb  |.........E......|
00000130  ea fb c8 f0 c8 e8 63 e3  e1 e5 bc bf ad bf 9d ae  |......c.........|
00000140  ad ae c8 b0 c8 98 c1 c1  65 65 8d fc 8d fb 8d fb  |........ee......|
00000150  8d fb c8 90 c8 f0 b4 94  94 94 fb ea eb ea eb ea  |................|
00000160  fb ea c8 f8 c8 e8 30 30  b0 90 da d9 da d9 da d9  |......00........|
00000170  da d9 c8 e8 c8 d0 9c 9f  9f 9f e9 ea e9 ea d9 ea  |................|
00000180  e9 ea c8 e0 c8 d0 35 3d  6d ed ea d9 ea d9 da d9  |......5=m.......|
00000190  da d9 c8 e8 c8 d8 32 30  30 34 d9 c8 d9 c9 d9 c9  |......2004......|
000001a0  d9 c9 c8 d8 c8 c0 b0 b0  b0 30 c8 c8 c8 c8 c8 c8  |.........0......|
000001b0  c8 c8 c8 c0 c8 c8 32 36  32 36 c8 c8 c8 c8 00 fe  |......2626......|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 d8 c2 00 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on pdc_ebfehihaia4



=============================== StdErr Messages: ===============================

hexdump: /dev/mapper/pdc_ebfehihaia4: No such file or directory
hexdump: /dev/mapper/pdc_ebfehihaia4: No such file or directory
```

---

### Post by Don Barzini on 2010-06-25
This link provides instructions for reinstalling Grub...

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Thomas,Bakker on 2010-06-25
Ok, i ran the ```
grub-install -v
``` from the terminal as said in the guide to see what version is installed. (if any)

It returns;
```
grub-install (GNU GRUB 1.98-1ubuntu5)

```

Thus i guess GRUB is installed but not configured correctly?

How do i configure it so that my drive whit Vista on it boots as default?

---

### Post by oldfred on 2010-06-25
Can you not just go into BIOS and set the system to boot the 160GB drive first. There often are two places one sets hd, fd, cd, usb etc another sets which hd is the first.

---

### Post by Don Barzini on 2010-06-25
> **Thomas,Bakker said:**
> How do i configure it so that my drive whit Vista on it boots as default?

Accorrding to the info you posted, Linux is on the first hard drive...**SDA** and Windows is on the second drive...**SDB**.

You should install GRUB to the MBR of SDA and then update-grub as per instructions at the link.

Your current grub.cfg doesn't look like it even contains an entry for Windows. You would be best booting off the first drive and then loading Windows from GRUB... once that is fixed.

You installed GRUB to the wrong place. Do you want to reinstall it to the MBR of the first drive?

---

### Post by Thomas,Bakker on 2010-06-25
> **Don Barzini said:**
> 
You installed GRUB to the wrong place. Do you want to install it to the MBR of the first drive?

As you may have noticed im quite new to linux, expecially GRUB.
But if your suggestion will make it work then i want to install GRUB to the MBR of the first drive.

Ty for the help BTW.

---

### Post by Don Barzini on 2010-06-25
> **Thomas,Bakker said:**
> i want to install GRUB to the MBR of the first drive.

Which is the Ubuntu drive.... right?

Try this...

Open a terminal window and enter the following....

```
sudo grub-install /dev/sda
```

Then proceed to run update-grub again

```
sudo update-grub
```

There will be some text that appears on the screen as it searches for operating systems.

Reboot the machine and see if your Windows version can load up.

---

### Post by Thomas,Bakker on 2010-06-25
Done that, here's the returns in the terminal;

```
thomas@thomas-desktop:~$ sudo grub-install /dev/sda
[sudo] password for thomas: 
Installation finished. No error reported.
thomas@thomas-desktop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
done
thomas@thomas-desktop:~$ 
```

I rebooted, got past the " bios select"  screen, then saw a black screen whit a blinking cursor, then the pc booted straight into ubuntu.

I'm getting the feeling Grub doesn't recognize my Vista installation, or maybe it doesn't detect my 1TB hard drive?
I noticed when installing ubuntu that i only had the option to install it on the 160GB HD and the 1TB one was not shown.

Anyway, ty for the help so far.
Its just past midnight over here and got to work in 6 hrs.

Ill check back after work.

---

### Post by darkod on 2010-06-25
=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of [COLOR=Red]/dev/mapper/pdc_ebfehihaia[/COLOR]

You used the 1TB disk in raid earlier and the meta data still existing there is making grub2 not recognize vista properly.

From ubuntu just remove the meta data with:

sudo dmraid -r -E /dev/sdb

And run the update-grub again after that and it should be fine.

Of course, do the above only if you are NOT running raid, it seems you are not. If you ARE, it will break your array.

---

### Post by Don Barzini on 2010-06-25
> **Thomas,Bakker said:**
> Ill check back after work.

Check your BIOS and look to see if there is a recent update for it.


....


Good call Darkod.

---

### Post by Thomas,Bakker on 2010-06-26
Great guys, thanx for the help. GRUB2 loads normally now.
Just booted in to Vista and back to ubuntu.

What i did was the following;

Type```
sudo dmraid -r -E /dev/sdb
```
As suggested by darkod

Then i reinstalled GRUB2 as suggested by Don Barzini using;

```
sudo grub-install /dev/sda
```

and then

```
sudo update-grub
```

rebooted and GRUB2 loaded normally.


Thanx again for the help guys.

---

