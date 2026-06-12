---
title: "Won't re-start after install - Grub Loading"
date: 2011-06-28
forum: Installation &amp; Upgrades
---

### Post by Brad72 on 2011-06-28
I do an install of an old version of Ubuntu (9.1), after install system restarts and freezes on second screen with the words "Grub Loading". Please excuse my vagueness I am only very new at this.  

Can someone give some advice please

Thanks

---

### Post by drs305 on 2011-06-28
Brad72,

Welcome to the Ubuntu forums.

First, you are trying to install a version of Ubuntu that is no longer supported. The repositories (software source) is no longer in it's original location and updates aren't available via normal methods. Unless you have a specific need for 9.10 most of us are going to recommend you install a supported version (Lucid, Maverick, Natty). If you need a 'lighter' version, releases such as a current version of Lubuntu might be more suitable.

Having said that, if you really want 9.10, perhaps we can help you get it running. We don't know why it's failing. One tool we often use to troubleshoot boot issues is a script called the boot info script. 

If you boot the LiveCD and go to this site, you can download the script, extract it and run it. The instructions are on the linked site. It will generate a file called RESULTS.txt. We need to see the contents of that file, which will show us the status of the Ubuntu boot files. 
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by Brad72 on 2011-07-03
Hi DRS305,

Thanks for your reply, I have taken your advice and gone for Lubuntu, thanks..... BUT....I assume the PC must be in the middle of something the only disc it will try to boot from is the original 9.10.  I have tried the Lubuntu disc in another PC and it boots perfectly.  Please standby for a copy of results from 'boot info script' as suggested.

---

### Post by drs305 on 2011-07-03
Will the PC boot any other commercial CD? If it can at least you know the problem isn't with your hardware. If it won't, make sure the BIOS is set to boot the CD first, before the hard drive.

---

### Post by Brad72 on 2011-07-09
The only cd it will boot is the Ubuntu 9.10.  Any other bootable cds I have will not boot pc will hang at 'grub loading' then end up at 'BIOS error' after about 30 minutes.
 I have tried running boot info script as recommended but will not run, I get the following message in terminal;

ubuntu@ubuntu:~$ sudo bash -/Desktop/boot_info_script*.sh
bash: -/: invalid option
Usage:    bash [GNU long option] [option] ...
    bash [GNU long option] [option] script-file ...
GNU long options:
    --debug
    --debugger
    --dump-po-strings
    --dump-strings
    --help
    --init-file
    --login
    --noediting
    --noprofile
    --norc
    --posix
    --protected
    --rcfile
    --restricted
    --verbose
    --version
    --wordexp
Shell options:
    -irsD or -c command or -O shopt_option        (invocation only)
    -abefhkmnptuvxBCHP or -o option
ubuntu@ubuntu:~$

---

### Post by Brad72 on 2011-07-09
Ammendment...

On boot up it frezes on *Grub Loading* for about 30mins then

[I]error: biodisk write error
Failed to boot default entries
Press any key to continue...[/I]

If I hit a key it repeats.

---

### Post by Brad72 on 2011-07-09
Ammendment...

On boot up it frezes on *Grub Loading* for about 30mins then

[I]error: biodisk write error
Failed to boot default entries
Press any key to continue...[/I]

If I hit a key it repeats.

---

### Post by drs305 on 2011-07-09
> **Brad72 said:**
> The only cd it will boot is the Ubuntu 9.10.  Any other bootable cds I have will not boot pc will hang at 'grub loading' then end up at 'BIOS error' after about 30 minutes.

If you try booting a non-Ubuntu/non-OS CD and you are getting a "grub loading" message, the most likely problem is that the computer is not able to boot the CD and is reverting to the hard drive. The 'grub loading' message would come from a linux OS CD or from the hard drive. Make sure the BIOS is set to boot first from a CD, and also listen to make sure the CD spins up at boot. If the CD reader is bad, you might have to try to make a bootable thumb drive.

If you have 9.10 installed on your hard drive, go ahead and boot the 9.10 LiveCD. I found a few posts which might point to a possible problem - the /boot/grub/grubenv file. So we can try to delete that file on your hard drive by mounting your Ubuntu partition and removing the file.

I'll assume your Ubuntu partition is sda1, but change the command to the correct partition if it is not:
```
sudo mount /dev/sd**a1** /mnt
gksu nautilus /mnt/boot/grub
```
Find the file "grubenv" and delete it, then try rebooting.

If this doesn't work, I'd concentrate on trying to figure out whether your CD-ROM actually works, and if it doesn't investigate 'unetbootin' or another means of using a USB flash drive.

---

### Post by Brad72 on 2011-07-11
Ok bingo!!  I got Lubuntu to load onto pc...but....it freezes on Device listing screen on pc boot up....could this be related to new OS?  I have checked all cards and ribbons inside pc, reset CMOS, and checked hard drive is set as Master, but made no difference.  Your assistance is appreciated..thanks

---

### Post by drs305 on 2011-07-11
> **Brad72 said:**
> Ok bingo!!  I got Lubuntu to load onto pc...but....it freezes on Device listing screen on pc boot up....could this be related to new OS?  

I don't know which screen you are referring to. If it is saying it can't find a drive *after* you have selected an item from the Grub menu, it's possibly an error in /etc/fstab.

At what point is the screen appearing - after you make (or automatically made) a selection from the Grub menu? Before you see the Grub menu? If you never see a grub menu, hold down the SHIFT key to see if it appears - and does the error screen appear before or after this?

A screenshot or the exact error message would be helpful. If you are able to boot the CD or the OS, running the boot info script (BIS link in my signature line) and posting the contents of RESULTS.txt may also shed some light on the problem.

---

### Post by Brad72 on 2011-07-11
Hi,
The screen I freeze at is the second screen with PC reboot, CMOS prior to OS booting.

Anyway I have run Boot Info Script, terminal outcome below; followed by results.

ubuntu@ubuntu:~$  sudo bash ~/Desktop/boot_info_script.sh

```

boot_info_script version: 0.60        [17 May 2011]


"gawk" could not be found, using "busybox awk" instead.
This may lead to unreliable results.

Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda5 for information... 

Finished. The results are in the file "RESULTS.txt"
located in "/home/ubuntu/Desktop/".

ubuntu@ubuntu:~$ 


RESULTS...
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80025280000 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156299375 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   155,383,807   155,381,760  83 Linux
/dev/sda2         155,385,854   156,297,215       911,362   5 Extended
/dev/sda5         155,385,856   156,297,215       911,360  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/ramzswap0                                          swap       
/dev/sda1        0f27256d-3788-4313-ad69-d2c31952fe31   ext4       
/dev/sda5        d2f88c2e-d1ad-468f-a078-40e287969ef6   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 0f27256d-3788-4313-ad69-d2c31952fe31
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos1)'
search --no-floppy --fs-uuid --set=root 0f27256d-3788-4313-ad69-d2c31952fe31
set locale_dir=($root)/boot/grub/locale
set lang=en_AU
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
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 0f27256d-3788-4313-ad69-d2c31952fe31
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=0f27256d-3788-4313-ad69-d2c31952fe31 ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 0f27256d-3788-4313-ad69-d2c31952fe31
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=0f27256d-3788-4313-ad69-d2c31952fe31 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 0f27256d-3788-4313-ad69-d2c31952fe31
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 0f27256d-3788-4313-ad69-d2c31952fe31
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

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=0f27256d-3788-4313-ad69-d2c31952fe31 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d2f88c2e-d1ad-468f-a078-40e287969ef6 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  62.134326935 = 66.716225536   boot/grub/core.img                             1
  62.134338379 = 66.716237824   boot/grub/grub.cfg                             1
   8.188476562 = 8.792309760    boot/initrd.img-2.6.38-8-generic               3
  62.132598877 = 66.714370048   boot/vmlinuz-2.6.38-8-generic                  1
   8.188476562 = 8.792309760    initrd.img                                     3
  62.132598877 = 66.714370048   vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by Brad72 on 2011-07-11
[IMG]file:///home/ubuntu/Desktop/DSCN0797.JPG[/IMG]

Pic of screen I'm referring to.

Sorry thats not going to work..  It's the PCI device listing page

---

### Post by drs305 on 2011-07-11
Admin notes: I added code tags to your post. You can do that during psoting by pressing the # icon, which generates the [noparse]```
 
```[/noparse] tags. Then paste the content between the two tags. For posting images, you could try clicking the 'paper clip' icon to try to upload the image as an attachment.

Your RESULTS.txt looks fine. If you are getting the error before the Grub screen it's either a hardware or BIOS issue. You could check the BIOS settings and/or perhaps try to remove or disable any PCI devices which might be causing the problem. 

I'm afraid that's about all I can offer. 

Do you get the same error screen if you boot with the CD? If you can't resolve it and it occurs before the Grub menu you might want to start a new thread with a title indicating PCI startup problems. You could also search other resources if it's a hardware issue not related to Linux (if that is the case).

---

### Post by Brad72 on 2011-07-11
Ok..thanks for all your assistance anyway,

---

### Post by Brad72 on 2011-07-21
Hi there again,

Just one other question.  I realized something which may be causing an issue after checking everything on BIOS and hardware setup.  The computer previously had a 4Gig drive as master hard drive and an 80 Gig as an extra drive.  I removed the 4 Gig drive and made the 80 Gig the only drive, I changed to setting on drive and relocated it on the ribbon cable, the  computer recognizes it as the master drive but it seem it may not boot from it.

You found no issues with the Boot Info Script results which eliminates OS issue I guess, but is it possible the Hard drive has to be formatted in a way to be able to boot from it.

---

