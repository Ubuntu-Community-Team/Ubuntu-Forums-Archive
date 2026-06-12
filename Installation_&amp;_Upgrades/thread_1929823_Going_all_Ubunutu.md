---
title: "Going all Ubunutu"
date: 2012-02-22
forum: Installation &amp; Upgrades
---

### Post by facefur on 2012-02-22
I just finished installing 11.10 on my older HP zv5000 laptop.  I left the old Windows XP in place, sort of just in case.  11.10 seems to be working fine and updated.  Now, I'd like to get rid of the old XP partition and open the entire hard drive (all 60 GB :o) to Linux.  Is there an easy way to do that?  My first thought was just to reinstall and let it have the entire drive, but the CD hangs during boot up.

---

### Post by 23dornot23d on 2012-02-22
Can you run gparted and post a screen shot of the way the drive is layed out

and also run ,, [[COLOR=Blue]_**bootinfoscript**_[/COLOR]]("http://bootinfoscript.sourceforge.net/") and post the results back please ....

it will give you more chance of a good answer to this problem .....

---

### Post by facefur on 2012-02-22
Results of gparted:

  Device      File System Mount  Size       Flags
 /dev/sda1    ntfs               40.00 GiB  Bootflag
 /dev/sda2    extended           15.89 GiB
   /dev/sda5  ext4        /      15.14 GiB
   /dev/sad6  linux swap            765 MiB

Could not get "boot .. " to run, and link takes me to a Gimp thread.
The boot screen offers Ubuntu, Ubuntu (recovery mode), memory tests, and Windows XP.
I'm never certain that resizing a partition won't destroy what's there.

---

### Post by 23dornot23d on 2012-02-22
Sorry here is the link again ....  as it will give a lot more detailed information ...

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

I was reading on GIMP and must have had that link still in my clipboard ... sorry

---

### Post by facefur on 2012-02-22
Feeling very unfamiliar here.  I have the boot script, but can't seem to get it to run. I set permission to run as a program, and it appears to execute, but the terminal disappearsa almost immediately.

---

### Post by 23dornot23d on 2012-02-22
It should have created a Results file 

 

[LIST]
[*] If you already have an existing RESULTS.txt, subsequent files will be called RESULTS1.txt, RESULTS2.txt,...
[*] Open RESULTS.txt in your favorite text editor.
[*] If you came here from a Linux forum, paste the content of  RESULTS.txt into your next post. Make sure to use the appropriate  formating.  For example in the Ubuntu forums click on the code tags (the symbol #)  before pasting RESULTS.txt.
[/LIST]


It sometimes ends up in the Downloads folder ...... if it seemed quick - maybe you need to pull the file out
of the Downloads folder and put it on your Desktop to do the commands they show ..... [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by facefur on 2012-02-22
Once I looked at the sript itself, it gave the run syntax (requires bash).  I found the RESULTS file, posted below.
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of the same hard drive for core.img. core.img is at this location and looks foron this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    83,891,429    83,891,367   7 NTFS / exFAT / HPFS
/dev/sda2          83,892,222   117,209,087    33,316,866   5 Extended
/dev/sda5          83,892,224   115,640,319    31,748,096  83 Linux
/dev/sda6         115,642,368   117,209,087     1,566,720  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        8EACB4C2ACB4A5DD                       ntfs       
/dev/sda5        87157890-029e-41a5-bfab-4b4052dd1f6e   ext4       
/dev/sda6        0b132bb7-8b00-4080-ab25-b64b832e2950   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect /NoExecute=OptIn
--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 87157890-029e-41a5-bfab-4b4052dd1f6e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 87157890-029e-41a5-bfab-4b4052dd1f6e
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
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
menuentry 'Ubuntu, with Linux 3.0.0-16-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 87157890-029e-41a5-bfab-4b4052dd1f6e
	linux	/boot/vmlinuz-3.0.0-16-generic root=UUID=87157890-029e-41a5-bfab-4b4052dd1f6e ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-16-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-16-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 87157890-029e-41a5-bfab-4b4052dd1f6e
	echo	'Loading Linux 3.0.0-16-generic ...'
	linux	/boot/vmlinuz-3.0.0-16-generic root=UUID=87157890-029e-41a5-bfab-4b4052dd1f6e ro recovery nomodeset 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-3.0.0-16-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 87157890-029e-41a5-bfab-4b4052dd1f6e
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=87157890-029e-41a5-bfab-4b4052dd1f6e ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 87157890-029e-41a5-bfab-4b4052dd1f6e
	echo	'Loading Linux 3.0.0-12-generic ...'
	linux	/boot/vmlinuz-3.0.0-12-generic root=UUID=87157890-029e-41a5-bfab-4b4052dd1f6e ro recovery nomodeset 
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
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 87157890-029e-41a5-bfab-4b4052dd1f6e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set=root 87157890-029e-41a5-bfab-4b4052dd1f6e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 8EACB4C2ACB4A5DD
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
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=87157890-029e-41a5-bfab-4b4052dd1f6e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=0b132bb7-8b00-4080-ab25-b64b832e2950 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/initrd.img-3.0.0-16-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-16-generic                  1
               =                initrd.img                                     2
               =                initrd.img.old                                 2
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

---

### Post by 23dornot23d on 2012-02-22
[ just looked again ... the boot flag is only for windows and seeing that you are removing it - this is not a problem]

[ There is still a problem with the way you use this first part of the drive though ]
The problem then comes .... the space you gain ....... is of no real use ....
unless you move and resize the extended partition sda2 to take the space which in
turn pulls sda5 down to it .... moving its boot start point .....

very risky the partition manager will warn you that sda5 is moving - 
( I have done this before on my system though - and it still booted ok - but as I say not really advised )
[COLOR=Red][B]
AND AS ALWAYS ..... before doing anything with Partitions .... MAKE A BACKUP FIRST OF important DATA[/B][/COLOR]

and I am guessing you need extra space as you may be running out in sda5 .... this 
you need to confirm

If you just want the extra space to store things in - but not for extra root space .... then the simple thing would be to use it as a separate partition 

which it will probably name as sda7 and it should put it between (sda1 and the extended partition sda2) retaining the position of (sda2 and sda5)

Grub is on sda .... 

> 
=> Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at  sector 1 of the same hard drive for core.img. core.img is at this  location and looks foron this drive.
[B][COLOR=Blue]which then boots linux on sda5
[/COLOR][/B]
> 
sda5: __________________________________________________  ________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
**[COLOR=Blue]Looking again the bootflag is probably the Windows one and if you are removing it ... then that not a problem anymore[/COLOR]**

> 
Device      File System Mount  Size       Flags
 /dev/sda1    ntfs               40.00 GiB  Bootflag
How do you want to use the space gained would be my question ..... just for storage
of DATA ....

or was it to give you more room in / root for programs .... ?


_____________________________________________________________________________

[B]If it was me in this situation - 

I would reformat the Windows partition to ext4 and then by installing a New Linux Distro into sda1

you would still retain the sda5 ...... in its current position ..... and the new install would pick it up
too .... 

This would give you a Dual boot with 2 Choices of Linux ...... best I can think of at the moment ,,,,[/B]

---

### Post by facefur on 2012-02-22
I think my intent is to devote the entire drive to Ubuntu, giving myself room for both data and programs.  Since the drive is only 60G, having two installs doesn't gain me much.

At this point, I don't have much on the Ubunutu side, having just installed earlier today. I'm thinking maybe just clear all the partitions and reinstall from the CD again.  At present, the CD seems to be running into the existing installation and won't finish booting.

Is that a doable thing?

---

### Post by 23dornot23d on 2012-02-22
Yes if you install clean and use the full drive that should be simple ....

Make sure you have all Data you need though ....

Emails - addresses
Photos - 
Documents etc .....



The Drive gets wiped completely .... and you start from scratch .... 

My way is to buy new USB hard drives nowadays ..... 

Less risk of losing something ... that may have been important ....

But if you are sure you have everything - then a clean install is good .... the 
install works out the partitions ....

You have a choice to set them up to the sizes you want .....

---

### Post by IWantFroyo on 2012-02-22
Has the disk worked before? If it works once then it should work again.

Have you double checked your boot settings? Try finding your boot priorities and switching them all to the CD drive. If it then tells you that you need to insert a valid system image, then you have a problem.

---

### Post by 23dornot23d on 2012-02-22
> 
 At present, the CD seems to be running into the existing installation and won't finish booting.


I am not sure what you mean by this .... the CD if ok should look for the existing
partition layout on the Hard Drive .... this sometimes takes some time on big hard
drives - but the 60 Gig should be reasonably fast .....

As a safeguard ...... if this is your only computer and system ..... Boot into the
system you installed today .....

Make sure before hand ...

That you have at least 2 good UBUNTU installation CDs   ...... 

Possibly ..... two that you know will work on your machine ....

Trying to make this as safe as possible ... 

( I have loads of Install CDs - but some people only have one - and if it fails you could 
end up stuck )

---

### Post by IWantFroyo on 2012-02-22
> **23dornot23d said:**
> That you have at least 2 good UBUNTU installation CDs   ...... 

Possibly ..... two that you know will work on your machine ....

Trying to make this as safe as possible ... 

( I have loads of Install CDs - but some people only have one - and if it fails you could 
end up stuck )

Hear hear. This is why I stopped using DVD-RWs. I would use one DVD for everything, and when I screwed up I got stuck.
I have a small library of Ubuntu and openSUSE install disks now. Plus a Debian.

---

### Post by epichacker1 on 2012-03-03
You can remove all Windows Partitions and increase the Ubuntu Partition, or just use the Clean Install tool. The Clean Install tool will remove all partitions and make one for Ubuntu, so if you don't want to use GParted this partitioning method will work. You can add more partitions if you like. If at any time you want to reinstall Windows and keep Ubuntu, you can decrease the Ubuntu partition size to make room for the Windows partition. That way you can dual boot. Before you do any of this, you should back up Windows in case Ubuntu doesnt install correctly. If the CD works once, it should boot up again correctly, check to make sure you have enough memory to run the installation. If the computer won't boot from the Ubuntu disc, you can use another computer to get your iso file, then run it in the compuer you want. And, is your CD bootable or not? It should work, since your last CD was. I would make a new Ubuntu installation CD and run it, and in the future, you may want to make a back-up copy. You may want to make sure that the BIOS is configured to load the CD ROM first, your hard drive may be having a problem, a Ubuntu clean install should fix that.

---

