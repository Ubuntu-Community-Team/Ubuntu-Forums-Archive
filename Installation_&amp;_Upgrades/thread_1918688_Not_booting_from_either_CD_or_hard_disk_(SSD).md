---
title: "Not booting from either CD or hard disk (SSD)"
date: 2012-02-01
forum: Installation &amp; Upgrades
---

### Post by Claritux on 2012-02-01
I have a newly purchased home built computer that I want to dual boot Ubuntu and Windows 7 on:
Intel &#8211; Core i7 2600K
ASUS Sabertooth P67 REV 3.0
Corsair Vengeance DDR3 1600MHz 2x4GB
NVIDIA GeForce GTX 570
Corsair SSD Force Series 3, 120GB 2.5"
Seagate Barracuda 7200.12 1TB
Samsung DVD±RW/Blu-Ray Reader SH-B123L

The main idea is to run both Ubuntu and Windows from the SSD, with a separate *hard disk* partition for the Windows install to put files on and a separate home partition for Ubuntu on the same hard disk. Windows installed itself on the SSD without problems, but I am having major problems getting Ubuntu to run. The first problem I encountered was that I was not able to boot up the Live-CD whatsoever. It seems like it gets stuck at a random(?) place when registering hardware components. However, I were able to run and install from the alternate CD installer. Now, when trying to boot to Ubuntu after a fresh install I first get to a completely purple screen. After doing a power shut (could probably use REISUB, didn't think of it at the time when I tried) I can at least access GRUB, but I still get nowhere when trying to boot. I tried following the guide from [this]("http://ubuntuforums.org/showpost.php?p=11343673&postcount=2") post and remove splash screen etc. via recovery mode, but when booting regularly after using recovery mode the boot up gets stuck before I am able to reach a command prompt. I suspect it gets stuck for the same reason that I can't get the Live-CD to boot. Also, for some reason the GRUB install won't recognize the Windows partition, so currently I am stuck with no bootable operating system.

PS: I have also tried running a Fedora Live-CD with exactly the same problem.

---

### Post by oldfred on 2012-02-01
Did your install 64bit Windows? And if so, is it in UEFI or BIOS?

 If UEFi the first partition must be efi and the drive will be gpt not MBR(msdos).

Post this (or sdb or both):

 sudo parted /dev/sda unit s print

---

### Post by archangel2003 on 2012-02-01
I wanted the UBUNTU 10 LTS version on my new lap top.
I partitioned the HD space and everything.
The problem is that when I use a flash or disc to install UBUNTU 10, it will not boot.
The only option that worked was the direct download in Windows.
However, the only version available with that method was the UBUNTU 11, AND IT SERIOUSLY SUCKS COMPARED TO UBUNTU 10!

Who decided to only allow 11 with the in windows option?

My daughter installed UBUNTU 10 on my last lap top and I EXCLUSIVELY used it and almost never felt the need to touch the XP partition. 

Now I'm using 7 and rarely touch the UBUNTU 11.

So now that I have Ubuntu 11,  I tried it and used the disc option to make the start up disc for UBUNTU 10.
Even watched a video to see it done.

UBUNTU 11 works for making a start up disc right up until the point of selecting the disc for writing the image to, then it does not recognize the empty disc in the drive.

I had to click and drag the UBUNTU 10 into the disc directly and burn it, but I don't think it's making a proper start up disc that way because the disc whirrs, but nothing happens, then it gives me the standard boot choices to choose from, and yes, I told it to boot from the disc first.

I'm so frustrated I feel like I just want to delete the UBUNTU partition and say screw it!

How in the heck do I get UBUNTU 10 on my new computer??

---

### Post by Claritux on 2012-02-01
archangel2003:
I don't mean to be rude, but I'd rather want this thread to be about how to fix my computer than Ubuntu 10.XX Vs 11.XX.

> **oldfred said:**
> Did your install 64bit Windows? And if so, is it in UEFI or BIOS?

 If UEFi the first partition must be efi and the drive will be gpt not MBR(msdos).

Post this (or sdb or both):

 sudo parted /dev/sda unit s print

Yes, the Windows install is 64bit and I'm trying to install 64bit 11.10. As far as I understand it is in UEFI, but my knowledge about it is a little limited. I'll see if I can get the command to run, but so far I can't access any command line while booting normally. Will it be ok to run it from recovery mode or the rescue mode on the alternate CD?

---

### Post by oldfred on 2012-02-01
Need to see how your drive is partitioned. 

If Windows made it UEFI and you want Ubuntu 10.04 or 10.10, you may have to reinstall Windows in BIOS/MBR mode.

I find that the fallback to be close but not exactly the same as the old gnome.

sudo apt-get install gnome-session-fallback
sudo apt-get install gnome-tweak-tool
sudo apt-get install gnome-panel
Before you log in, click the gear icon and select GNOME Classic.

---

### Post by Claritux on 2012-02-01
From recovery:
[http://dl.dropbox.com/u/955480/IMAG0039.jpg](http://dl.dropbox.com/u/955480/IMAG0039.jpg)

---

### Post by Claritux on 2012-02-01
> **oldfred said:**
> Need to see how your drive is partitioned. 

If Windows made it UEFI and you want Ubuntu 10.04 or 10.10, you may have to reinstall Windows in BIOS/MBR mode.

I find that the fallback to be close but not exactly the same as the old gnome.

sudo apt-get install gnome-session-fallback
sudo apt-get install gnome-tweak-tool
sudo apt-get install gnome-panel
Before you log in, click the gear icon and select GNOME Classic.

It's currently impossible for me to run any sort of GUI, and I'm prevented from installing anything since I can't get to a command window by booting normally. (Recovery says Read-only file system if I try to use apt-get.)

---

### Post by oldfred on 2012-02-01
I thought you could not install, not that liveCD does not work.

All of above assumed a working liveCD which is what you have to have before installing.

You may need boot parameters on liveCD.

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Resetting an out&#8208;of&#8208;range resolution (does not include grub's set gfxmode=640x480)
[https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution](https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution)
Repair grub's video mode and other settings
[https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Some other parameters that worked
[SOLVED] UEFI Boot Problems 
quiet splash vt.handoff=7 rootdelay=90 reboot=a,w
[http://ubuntuforums.org/showthread.php?t=1857639](http://ubuntuforums.org/showthread.php?t=1857639)

---

### Post by Claritux on 2012-02-02
:D I've got a working desktop. The graphic card was the source of the problem or in fact the open source NOVEAU driver. I was a little to quick when I said I couldn't get to any command prompt by regular booting. After I followed the guide from the [post]("http://ubuntuforums.org/showpost.php?p=11343673&postcount=2") I thought I originally mentioned I was in fact able to get to a command prompt by Ctrl+Alt+F(X). (At this stage I tried out another graphic card which allowed me to run "sudo service lightdm start" and get a working desktop so I could conclude that the graphic card was the problem.) I then downloaded the appropriate driver install file from NVIDIAs website and proceeded with running it from command line. When I ran it the first time it complained about the NOVEAU driver and asked me if I wanted to disable it. After that I rebooted and found myself able to get a working desktop with my original graphics card. I then ran the install file a second time (Note: This can't be done while X is running) and installed the graphic drivers.

Now I only need to get access to Windows from GRUB. I'm going do a reinstall of Ubuntu since I messed up a couple of things while troubleshooting, but do I need to get a working EFI partition in order to accomplish this?*

Edit:*In order to get GRUB to discover Windows.

---

### Post by oldfred on 2012-02-02
Grub should have found Windows. Unless you installed Windows in efi and Ubuntu in BIOS/mbr.

Have you tried this?
sudo update-grub

If not then we need the full output from the bootinfo script to see what is where.Test version has some fixes:

wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by Claritux on 2012-02-02
```
                   Boot Info Script 0.60      [17 May 2011]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid ca7dc3bd-a316-41fd-9900-31d5eb35650a root 
    set prefix=($root)/boot/grub
    ---------------------------------------------------------------------------
    -----.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048   143,362,047   143,360,000   7 NTFS / exFAT / HPFS
/dev/sda2    *    143,362,048   234,440,703    91,078,656  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb2    *  1,172,275,200 1,953,523,711   781,248,512  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        EAA036E6A036B941                       ntfs       
/dev/sda2        df7b3067-4b85-4269-8225-5ed0c6bee3e5   ext4       
/dev/sdb2        41797c1f-8f3c-4525-a412-ceb338d39bce   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb2        /home                    ext4       (rw,commit=0)


=========================== sda2/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set=root df7b3067-4b85-4269-8225-5ed0c6bee3e5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos2)'
  search --no-floppy --fs-uuid --set=root df7b3067-4b85-4269-8225-5ed0c6bee3e5
  set locale_dir=($root)/boot/grub/locale
  set lang=nb_NO
  insmod gettext
fi
terminal_output gfxterm
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
menuentry 'Ubuntu, med Linux 3.0.0-15-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root df7b3067-4b85-4269-8225-5ed0c6bee3e5
	linux	/boot/vmlinuz-3.0.0-15-generic root=UUID=df7b3067-4b85-4269-8225-5ed0c6bee3e5 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-15-generic
}
menuentry 'Ubuntu, med Linux 3.0.0-15-generic (gjenopprettelsesmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root df7b3067-4b85-4269-8225-5ed0c6bee3e5
	echo	'Laster Linux 3.0.0-15-generic ...'
	linux	/boot/vmlinuz-3.0.0-15-generic root=UUID=df7b3067-4b85-4269-8225-5ed0c6bee3e5 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-15-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, med Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root df7b3067-4b85-4269-8225-5ed0c6bee3e5
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=df7b3067-4b85-4269-8225-5ed0c6bee3e5 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, med Linux 3.0.0-12-generic (gjenopprettelsesmodus)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root df7b3067-4b85-4269-8225-5ed0c6bee3e5
	echo	'Laster Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=df7b3067-4b85-4269-8225-5ed0c6bee3e5 ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root df7b3067-4b85-4269-8225-5ed0c6bee3e5
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set=root df7b3067-4b85-4269-8225-5ed0c6bee3e5
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=df7b3067-4b85-4269-8225-5ed0c6bee3e5 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb2 during installation
UUID=41797c1f-8f3c-4525-a412-ceb338d39bce /home           ext4    defaults        0       2
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  92.489231110 = 99.309555712   boot/grub/core.img                             1
 102.543945312 = 110.105722880  boot/grub/grub.cfg                             1
  71.744243622 = 77.034795008   boot/initrd.img-3.0.0-12-generic               2
  71.990329742 = 77.299027968   boot/initrd.img-3.0.0-15-generic               2
  68.579536438 = 73.636716544   boot/vmlinuz-3.0.0-12-generic                  1
  71.763153076 = 77.055098880   boot/vmlinuz-3.0.0-15-generic                  1
  71.990329742 = 77.299027968   initrd.img                                     2
  71.744243622 = 77.034795008   initrd.img.old                                 2
  71.763153076 = 77.055098880   vmlinuz                                        1
  68.579536438 = 73.636716544   vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
xz: (stdin): Compressed data is corrupt

```

sudo update-grub does not help

---

### Post by Claritux on 2012-02-03
sudo parted /dev/sda unit s print

```
Model: ATA Corsair Force 3 (scsi)
Disk /dev/sda: 234441648s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start       End         Size        Type     File system  Flags
 1      2048s       143362047s  143360000s  primary  ntfs
 2      143362048s  234440703s  91078656s   primary  ext4         boot
```

---

### Post by oldfred on 2012-02-03
Windows 7's default install is to two partitions, but can be installed in one. The first is a small hidden 100MB boot/repair partition. Your Windows boot partition is missing.

Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
[COLOR=Red]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe 

You can put bootmgr & the /Boot/BCD into your sda1 partition, repair BCD and possibly other repairs and your Windows install then should work.

If you have a Windows repairCD, some have just copied the files & then run the Windows repairs.

Both drives are MBR(msdos). The grub you have installed to the MBR of the 1TB drive is looking for a UUID that does not exist, so you cannot boot from sdb. Otherwise your install looks normal.

Edit:
Grub does not use boot flag, but Windows uses it for booting, install or repair as it is the active partition in Windows. Use gparted or Disk Utility (or Windows) to set sda1, the NTFS partition as bootable.

---

### Post by Claritux on 2012-02-04
Solved! I ended up reinstalling Windows and reinstalling GRUB to /dev/sda. Windows shows up nicely now. Thanks for the help!

---

