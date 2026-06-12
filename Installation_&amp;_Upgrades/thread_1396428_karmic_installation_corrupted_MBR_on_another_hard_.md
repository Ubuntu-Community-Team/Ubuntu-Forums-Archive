---
title: "karmic installation corrupted MBR on another hard drive"
date: 2010-02-02
forum: Installation &amp; Upgrades
---

### Post by oygle on 2010-02-02
The computer that I have Ubuntu/Karmic just recently installed on, has 2 hard drives. Primary is Ubuntu, secondary is win95b. After the Karmic installation (which went perfectly), I now find that when I boot to the secondary drive, the MBR for win95b is reporting it is corrupted.

I can use win95b, **BUT** it runs in dos compatability mode, and there are no CD drives showing, despite the fact that BIOS reports 2 cd drives.

Can GParted fix the corrupted MBR on the win95b hard drive ?

Oygle

---

### Post by oldfred on 2010-02-02
An install does not corrupt a windows install, it sometimes totally overwrites it.

Just to confirm configuration, run this script:

Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

Restore basic windows style boot loader from ubuntu to sda (use sdb or sdc as appropriate )
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

---

### Post by oygle on 2010-02-02
Thanks, here are the results from the bootinfoscript ..

```


============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0002c46f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   149,372,369   149,372,307  83 Linux
/dev/sda2         149,372,370   156,296,384     6,924,015   5 Extended
/dev/sda5         149,372,433   156,296,384     6,923,952  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 20.5 GB, 20520493056 bytes
255 heads, 63 sectors/track, 2494 cylinders, total 40079088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x239d4641

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     7,454,159     7,454,097   b W95 FAT32
/dev/sdb2           7,454,160    40,066,109    32,611,950   f W95 Ext d (LBA)
/dev/sdb5           7,454,223    40,066,109    32,611,887   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        f6f356fc-bcc4-4d13-84aa-82ba817be5fb   ext3                                     
/dev/sda5        e8a64c58-bf57-45d6-a606-e36b0a051b2b   swap                                     
/dev/sdb1        1017-18D5                              vfat       W95_C                         
/dev/sdb5        4823-58FF                              vfat       W95_F                         

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,errors=remount-ro)
/dev/sr1         /media/Data disc         (02 Fe     iso9660 (ro,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set f6f356fc-bcc4-4d13-84aa-82ba817be5fb
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set f6f356fc-bcc4-4d13-84aa-82ba817be5fb
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=f6f356fc-bcc4-4d13-84aa-82ba817be5fb ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set f6f356fc-bcc4-4d13-84aa-82ba817be5fb
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=f6f356fc-bcc4-4d13-84aa-82ba817be5fb ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set f6f356fc-bcc4-4d13-84aa-82ba817be5fb
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=f6f356fc-bcc4-4d13-84aa-82ba817be5fb ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set f6f356fc-bcc4-4d13-84aa-82ba817be5fb
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=f6f356fc-bcc4-4d13-84aa-82ba817be5fb ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 95/98/Me (on /dev/sdb1)" {
	insmod fat
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 1017-18d5
	drivemap -s (hd0) ${root}
	chainloader +1
}
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=f6f356fc-bcc4-4d13-84aa-82ba817be5fb /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e8a64c58-bf57-45d6-a606-e36b0a051b2b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```




Here is the file device.map

```

(hd0)	/dev/sda
(hd1)	/dev/sdb

```

Here is the file grub.cfg

```

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set f6f356fc-bcc4-4d13-84aa-82ba817be5fb
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set f6f356fc-bcc4-4d13-84aa-82ba817be5fb
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=f6f356fc-bcc4-4d13-84aa-82ba817be5fb ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set f6f356fc-bcc4-4d13-84aa-82ba817be5fb
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=f6f356fc-bcc4-4d13-84aa-82ba817be5fb ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set f6f356fc-bcc4-4d13-84aa-82ba817be5fb
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=f6f356fc-bcc4-4d13-84aa-82ba817be5fb ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set f6f356fc-bcc4-4d13-84aa-82ba817be5fb
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=f6f356fc-bcc4-4d13-84aa-82ba817be5fb ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 95/98/Me (on /dev/sdb1)" {
	insmod fat
	set root=(hd1,1)
	search --no-floppy --fs-uuid --set 1017-18d5
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

```

Notice the menu option there for windows 95. This used to be in a file called menu.lst I think. Also, grub used to use device.map to swap the primary file, but it seems from the grub.cfg, that is no longer relevant ?

> **oldfred said:**
> 
Restore basic windows style boot loader from ubuntu to sda (use sdb or sdc as appropriate )
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

I'm quite happy with grub though, do I need lilo ?  Will using the lilo on the MBR overwite any Ubuntu info ? I guess not, as long as I have the correct device. Also will lilo only 'fix' the windooze MBR, as win95 does load okay, just for some reason there are no CD drives. I can access the CD drives though, on the same computer, when I boot to Ubuntu.

Thanks,

Oygle

---

### Post by oygle on 2010-02-02
This is what was at the very end of the menu.lst file before Karmic

```

### END DEBIAN AUTOMAGIC KERNELS LIST

title           Microsoft Windows 95b
map             (hd0) (hd1)
map             (hd1) (hd0)
root            (hd1,0)
savedefault
makeactive
chainloader   +1

```

---

### Post by oygle on 2010-02-02
I noticed that for Grub, the old setting for windows 95 is different to the new one

**old**  -  root            (hd1,0)

**new**  -  set root=(hd1,1)

could that be why win95b goes ballistic and runs in DOS compatability mode ?

---

### Post by oldfred on 2010-02-03
You are now using grub2 and they have updated some things. map has been replaced with mapdevice, root with set root=, and partition numbering now starts with 1 where grub legacy started at 0.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

I do not know if the script is not designed to look for the old win95 boot files or if some are missing. It would normally show XP, Vista, or 7 files so we can see if they are correct. Can you look in your partition and see if the boot files are there?

Since you have 2 drives you should be able to switch drives in BIOS and directly boot windows. Does that work and then can you repair your windows. Grub will only chainboot into a working windows.

Windows is installed in the MBR of /dev/sdb

---

### Post by Herman on 2010-02-03
I agree with oldfred, it might simplify things if you make the Windows hard disk your first hard disk.

The pair of 'map' commands in GRUB are for tricking Windows into thinking it's in the first hard disk to save users the work of editing the boot loader files in Windows.
I'm not sure about Windows 95 and 98, but in later versions of Windows if the boot.ini file is edited then the map commands aren't needed. 

If the hard drive you have Windows in is not the first hard drive then GRUB wouldn't have been installed to MBR in it anyway, so it isn't at all likely that GRUB2 had 'corrupted your MBR'. Titling your thread like that is a great way to attract attention though. 

In GRUB2 the partition numbering scheme is are different than for GRUB Legacy, **old**  -  root            (hd1,0) = **new**  -  set root=(hd1,1)

---

### Post by Herman on 2010-02-03
Hard disks are given a MBR when they are formatted. 
The hard disk's MBR is not part of any operating system, and is situated in sector zero of the hard disk and contains a very small area reserved for boot loader code, a disk ID number, the partition table for all the primary partitions and a aa55 bootable disk indicator. 
The boot code Windows puts in the MBR is relatively basic and is just  enough to direct the boot to the Windows boot sector.   
It doesn't really matter to Windows what  boot loader the code in the MBR is replaced with.
As long as something  points to the  Windows boot sector, Windows can be booted. 

The boot sector is typically located in sector number 63 for most Windows installations, but it can be elsewhere if circumstances require.
Sometimes there's a recovery partition or something like that in between the MBR and the Windows installation, or the user has moved the Windows partition somewhere else. Modern Windows operating systems don't begin until sector 2048.
The boot sector is important for booting Windows, it contains code to direct the boot to the boot loader files within the Windows file system. 

The important files needed for booting Windows 95 are : IO.SYS, MSDOS.SYS and COMMAND.COM and those should be found in the root of drive C: 
  You should be able to easily see those files when you mount your Windows 95 partition in Ubuntu.
 
If you need to fix problems booting Windows 95, you can go to [Bootdisk.com]("http://www.bootdisk.com/") and download a floppy disk for your version of Windows 95.
There are two different versions of Windows 95, the original version had the FAT16 file system and was later upgraded to the FAT32 file system. 
You need to make sure you download the correct boot floppy for your version of Windows 95.

Three of the commands in the floppy disc that may be useful for fixing the boot of Windows 95 are: 
scandisk C:   
fdisk /mbr
SYS C:
 
The first command, scandisk C:  runs a file system check in your C: drive.

The second command, fdisk /mbr, re-installs the Windows 95 boot loader in the IPL area of the MBR.
Only run this command if you really have to. If you're booting with GRUB you shouldn't need it because GRUB is normally quite capable of pointing out the location of the Windows boot sector. 
If you decide to delete Ubuntu and remove GRUB and will only want to boot Windows 95 then you need Windows 95 IPL in the MBR, and then you should run fdisk /mbr.

The third command, 'sys C:' runs SYS.COM will write a new boot sector and also refresh the important files in the root of drive C: that are needed for booting, which are: IO.SYS, MSDOS.SYS and COMMAND.COM, and that is the command that will fix most problems with Windows 95 if you neeed to run it.

---

### Post by oygle on 2010-02-04
> **oldfred said:**
> Can you look in your partition and see if the boot files are there?

The win95b boot files are there, I was able to d/load a win95b boot disk, so could compare some files. The only file that had changed the last few days was MSDOS.SYS , so I overwrote it with the MSDOS.SYS from the boot floppy.  Also I did a SYS a:\ c:\ , and it copied over the system files. All this was done by booting to floppy.

Having the floppy also enabled me to fix up autoexec.bat and config.sys, and now I can see the 2 CD-ROM drives, under win95b

> **oldfred said:**
> 
Since you have 2 drives you should be able to switch drives in BIOS and directly boot windows. Does that work and then can you repair your windows. Grub will only chainboot into a working windows.

Windows is installed in the MBR of /dev/sdb

Yes, thanks. At BIOS, I forced it to boot to drive D first (win95b hdd), and it wasn't running in md-dos compatability mode, and no 'MBR' messages. So , if I want to use win95b, I will just have to force it at bios, to boot to that drive first. It seems if GRUB takes over, that is causing the problems.

One thing I did notice when it booted okay, was an 'extra' CD rom drive appear under win95b. I _think_ this was win95b's attempt to try and access the Ubuntu HDD, as when I checked that drive, it said something about it was the only drive running in MS-DOS compat. mode.

It seems if GRUB takes over (boot to ubuntu hd first), it somehow stops the real mode drivers from being loaded to win95b.

Thanks,

Oygle

---

### Post by oygle on 2010-02-04
> **Herman said:**
> I'm not sure about Windows 95 and 98, but in later versions of Windows if the boot.ini file is edited then the map commands aren't needed.

I will look into that, thanks.  :)

> **Herman said:**
> If the hard drive you have Windows in is not the first hard drive then GRUB wouldn't have been installed to MBR in it anyway, so it isn't at all likely that GRUB2 had 'corrupted your MBR'. Titling your thread like that is a great way to attract attention though.


Yes, the Windows hdd is not the first, it is the secondary hdd on the controller.
 
Thanks,

Oygle

---

### Post by oygle on 2010-02-04
Herman, thanks for all your detailed information on Windows MBR and boot files, etc. I have run the SYS command, so all boot files should be okay.

Interestingly, a search for BOOT.INI showed no results. Will look into it.

Anyway, for now, I can boot to win95b by changing bios, and now also have the 2 cd-roms back, and the floppy drive appears there now also.

I'll mark this as solved. Thanks everone for your help.  :D

Oygle

---

### Post by Herman on 2010-02-04
:D There's no boot.ini in Windows 95 or 98, boot.ini is a file for the Windows NTLDR boot loader, that wasn't invented yet in the Windows 95 days.

Anyhow, I'm glad you can boot Windows 95 okay now, too bad it doesn't boot with GRUB2 for some reason, I wish I knew why not. Maybe I'll try out Karmic and Windows 98 or Lynx and Windows 98 dual boot some time soon as find out for myself.
By the way, there's nothing wrong with running Windows 95 or Windows 98 nowadays, especially if you're dual booting with a Linux operating system. My old Windows 98SE is as fast as lightning in an old PC Chips 'Book PC', and it will still do most of the things we expect a PC to do. It doesn't need a whopping big processor and 2 or more GB of RAM to run it either. My Windows 98SE machine has a 400 MHz processor and it used to run fine with only 128 MB or RAM but I have it boosted to 512 MB now so I can dual boot Ubuntu with it better. I haven't got around to adding a new version of Ubuntu with it yet but maybe I will soon, your thread has reminded me about it. :D

EDIT: Here's a link to a webpage I made about my Ubuntu / Windows 98 PC, [[COLOR=#000000]Book PC Gets Big Power Supply[/COLOR]]("http://sites.google.com/site/herman543/bookpcgetsbigpowersupply2"), I was running Ubuntu Hardy Heron in it then. I used to run Ubuntu Warty Warthog in this machine when Ubuntu first came out and I still have my Ubuntu Warty Warthog CD which I got off the front cover of a magazine.

---

### Post by oldfred on 2010-02-04
I cannot test anything so these are just guesses on my part.

It is my understanding that all the windows boot loaders in the MBR just look for a partition with the boot flag on and jump to the PBR partition boot record to continue loading windows. Also then old grub did the same thing in that from its menu you would tell it to jump to the PBR with windows. But if windows had problems it would usually crash as the jump to that partition had no way to recover. New grub tries to be smarter and loads drivers and does some checking before jumping. I would try removing some of the extra commands in grub2 to make it just jump to the win95 partition.

"Windows 95/98/Me (on /dev/sdb1)" {
   [COLOR=DarkRed] insmod fat[/COLOR]
    set root=(hd1,1)
    [COLOR=DarkRed]search --no-floppy --fs-uuid --set 1017-18d5[/COLOR]
    drivemap -s (hd0) ${root}
    chainloader +1
}

I would delete the lines in red and see it it works. I am also confused on the new drivemap replacement for map commands. Not sure if the one shown works or it needs to be (hd1) (hd0) or (hd1) ${root}. If you want to experiment you can but let us know what works if you do.
You would have to copy the entry into 40_custom and do and update-grub, you could copy several versions into 40_custom and see if any work.

---

### Post by meierfra. on 2010-02-04
> I do not know if the script is not designed to look for the old win95 boot files or if some are missing.
Version 0.50 of the boot info script did not look for win 95/98 or MSDOS files.  But I just filed a new release. So the boot info script now should be able to detect Win95.

oygle, could you do me a favor, and download the boot info script again, run it and post the RESULTS.txt? I would like to see whether my changes are actually working.


There is a problem with the "drivemap line" in grub.cfg and older Versions of Windows. So you might be able to solve your problem by installing Grub to the MBR of /dev/sdb

```
gksudo gedit /boot/grub/device.map
```
Change the file to

(hd0) /dev/sdb
(hd1) /dev/sda

Then

```

sudo grub-install  /dev/sdb
sudo update-grub

```

and set your bios to boot from /dev/sdb

---

### Post by oygle on 2010-02-05
> **Herman said:**
> Anyhow, I'm glad you can boot Windows 95 okay now, too bad it doesn't boot with GRUB2 for some reason, I wish I knew why not.

There is a [GRUB mailing list]("http://lists.gnu.org/mailman/listinfo/grub-devel") ; I may ask there ?

> **Herman said:**
> My Windows 98SE machine has a 400 MHz processor and it used to run fine with only 128 MB or RAM but I have it boosted to 512 MB now so I can dual boot Ubuntu with it better. I haven't got around to adding a new version of Ubuntu with it yet but maybe I will soon, your thread has reminded me about it.

Win95b runs okay on the old computer I have, an MSI mobo, 350 Mhz and only 256 Mb RAM. It actually runs much slower now with Karmic, significant performance drop, and that is with using EXT3 (I did install EXT4, read some horro stories, and re-installed it with EXT3)

I checked out your webpage about the old PC, very interesting indeed what you have done there. Talking about old equipment, only the other day a TPG monitor died on me, I'm pretty sure it was either 1994 or 1995 when I got it, so it lasted a long time.

Thanks,

Oygle

---

### Post by oygle on 2010-02-05
> **meierfra. said:**
> Version 0.50 of the boot info script did not look for win 95/98 or MSDOS files.  But I just filed a new release. So the boot info script now should be able to detect Win95.

oygle, could you do me a favor, and download the boot info script again, run it and post the RESULTS.txt? I would like to see whether my changes are actually working.

Have done so. Ran results.txt through a file compare, comparing it to the original one (previous boot info script), and there is now some extra info

```

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 95
    Boot files/dirs:   /IO.SYS /MSDOS.SYS /COMMAND.COM

```

Those last 2 lines were not there before, so it is detecting win95, thanks.

I'd be rather hesitant to install grub to the windows hdd, as it does boot okay now, if I set the bios to boot to drive D (secondary drive on controller) first.

Thanks,

Oygle

---

### Post by oygle on 2010-02-05
> **oldfred said:**
> I would try removing some of the extra commands in grub2 to make it just jump to the win95 partition.

"Windows 95/98/Me (on /dev/sdb1)" {
   [COLOR=DarkRed] insmod fat[/COLOR]
    set root=(hd1,1)
    [COLOR=DarkRed]search --no-floppy --fs-uuid --set 1017-18d5[/COLOR]
    drivemap -s (hd0) ${root}
    chainloader +1
}

I would delete the lines in red and see it it works.

Okay, I will try and get to do that, and let you know, thanks.

I am not conversant with 40_custom, so I'll leave that one.

Oygle

---

### Post by meierfra. on 2010-02-05
> Those last 2 lines were not there before, so it is detecting win95, thanks.
Great. Thanks for running the script again.

> I'd be rather hesitant to install grub to the windows hdd, as it does boot okay 
Removing Grub2 from the MBR is usually pretty easy. But if you want to be extra careful you can backup the MBR before hand:

```
sudo dd if=/dev/sdb of=MBR.bin count=63
```

---

### Post by oygle on 2010-02-07
> **meierfra. said:**
> Removing Grub2 from the MBR is usually pretty easy. But if you want to be extra careful you can backup the MBR before hand:

Thanks, but I don't want to risk not being able to boot to win95b. At least I can just use bios to control which drive is 'primary' and boot to that.

---

