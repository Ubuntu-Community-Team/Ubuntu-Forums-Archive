---
title: "Unknown command (loadfont) - Will not boot"
date: 2010-11-23
forum: Installation &amp; Upgrades
---

### Post by RamosDevil on 2010-11-23
I have a dual booting HP Pavilion laptop.  I originally had only Windows 7 running on it (64-bit) and installed Ubuntu 10.04 alongside Windows 7 (via a Ubuntu 10.04 install DVD) and never looked back. However, last night I installed Wine 1.2, shut the computer off, and the next time I booted up my laptop, I get an error when I attempt to boot Ubuntu using the Windows Boot Loader (unknown command (loadfont) - the laptop continually resets itself).  I am able to boot into Windows 7, but not Ubuntu.  I have followed all of the instructions on [this thread (1)]("http://ubuntuforums.org/showthread.php?t=1474253") AND [this thread (2)]("http://ubuntuforums.org/showthread.php?t=1474418"), both to no avail.  Using a live USB stick, I have been able to comment out the loadfont and associated lines in grub.cfg, yet that did not fix the problem.  When I change grub.cfg to grub.cfg.broken (as detailed in another post), I can boot into the grub prompt and manually boot.  Once into my laptop-native Ubuntu, I have performed the sudo update-grub command, yet when I reboot, I get the loadfont error again.  What else can I do?  I also uninstalled Wine and all of its components using Synaptic, being as it caused these problems in the first place.  Help!

---

### Post by Rubi1200 on 2010-11-24
Hi and welcome to the forums :)

I suggest you use a LiveCD to boot the computer and choose to try not install Ubuntu.

Click on the link at the bottom of my post and follow the instructions there.

Post the results back here so we can see what is where.

Thanks.

---

### Post by RamosDevil on 2010-11-24
Thanks for your help, Rubi1200.  I ran the script and this is what it came back with:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   601,966,591   601,966,529   7 HPFS/NTFS
/dev/sda2         601,966,592   625,135,615    23,169,024   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2020 MB, 2020904448 bytes
63 heads, 62 sectors/track, 1010 cylinders, total 3947079 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     3,945,059     3,944,998   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       01183a06-3c65-4181-8703-4557d17e9797   ext3                                     
/dev/loop2       ff2a46ac-5542-4ac3-860d-bd075506bac0   ext4                                     
/dev/sda1        23A85F0441831D29                       ntfs                                     
/dev/sda2        D606384806382C3D                       ntfs       HP_RECOVERY                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        38E4-BDEF                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


======================== sda1/Wubi/boot/grub/grub.cfg: ========================

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
insmod ntfs
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 23a85f0441831d29
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
insmod ntfs
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 23a85f0441831d29
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-25-generic" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 23a85f0441831d29
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 23a85f0441831d29
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 23a85f0441831d29
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 23a85f0441831d29
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-23-generic" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 23a85f0441831d29
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-23-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, Linux 2.6.32-23-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 23a85f0441831d29
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-23-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu, Linux 2.6.32-22-generic" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 23a85f0441831d29
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, Linux 2.6.32-22-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 23a85f0441831d29
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 23a85f0441831d29
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic (recovery mode)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 23a85f0441831d29
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 23a85f0441831d29
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set d606384806382c3d
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda1/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda1/Wubi: Location of files loaded by Grub: =================


   2.3GB: boot/grub/grub.cfg
   2.2GB: boot/initrd.img-2.6.32-21-generic
   2.4GB: boot/initrd.img-2.6.32-22-generic
   3.7GB: boot/initrd.img-2.6.32-23-generic
   9.5GB: boot/initrd.img-2.6.32-24-generic
  18.6GB: boot/initrd.img-2.6.32-25-generic
   2.2GB: boot/vmlinuz-2.6.32-21-generic
   2.2GB: boot/vmlinuz-2.6.32-22-generic
  11.4GB: boot/vmlinuz-2.6.32-23-generic
   6.5GB: boot/vmlinuz-2.6.32-24-generic
   4.3GB: boot/vmlinuz-2.6.32-25-generic
  18.6GB: initrd.img
   9.5GB: initrd.img.old
   4.3GB: vmlinuz
   6.5GB: vmlinuz.old
```

---

### Post by bcbc on 2010-11-24
Copy the c:\ubuntu\winboot\wubildr file over the c:\wubildr file (backup before overwriting)

---

### Post by RamosDevil on 2010-11-24
> **bcbc said:**
> Copy the c:\ubuntu\winboot\wubildr file over the c:\wubildr file (backup before overwriting)

I renamed the C:\wubildr file to C:\wubildr_old, then copied the C:\ubuntu\winboot\wibildr file to C:\.  I then restarted the computer, and again got:

"Try (hd0,0): NTFS5
error: unknown command 'loadfont'
error: file could not be found"

The laptop then rebooted. Did I miss a step? I renamed/copied the wubildr file using Windows 7 - not sure that would make a difference, but I figured it was worth noting.

---

### Post by bcbc on 2010-11-24
OK do this instead:
Boot a live CD, then edit grub.cfg as follows:
```
sudo mkdir /media/win 
sudo mount /dev/sda1 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
sudo cp /mnt/boot/grub/grub.cfg /mnt/boot/grub/grub.cfg.copy
sudo chmod +w /mnt/boot/grub/grub.cfg
gksu gedit /mnt/boot/grub/grub.cfg
```

Delete all lines up to (not including) the first line that starts with "menuentry"
Save, reboot.

---

### Post by RamosDevil on 2010-11-24
Seems like that did the trick.  After editing grub.cfg and removing those lines, I rebooted and I was able to boot normally.  Any idea what would have caused this to happen?  Every time I install Wine I seem to get booting problems, which only happens on this machine (I have had no problems with Wine on my Desktop computers).  Also, would you care to explain exactly what it is I did to make this work?  I understand that the grub configuration file somehow got messed up, did I just delete unnecessary commands or did I disable some features that were preventing me from booting?  I'm happy your solution works, but now I'd like to know HOW it works.  Thanks so much for the help.

---

### Post by bcbc on 2010-11-24
> **RamosDevil said:**
> Seems like that did the trick.  After editing grub.cfg and removing those lines, I rebooted and I was able to boot normally.  Any idea what would have caused this to happen?  Every time I install Wine I seem to get booting problems, which only happens on this machine (I have had no problems with Wine on my Desktop computers).  Also, would you care to explain exactly what it is I did to make this work?  I understand that the grub configuration file somehow got messed up, did I just delete unnecessary commands or did I disable some features that were preventing me from booting?  I'm happy your solution works, but now I'd like to know HOW it works.  Thanks so much for the help.

When you find out let me know :) 

Basically, what I know is that there was a grub update. Part of that update replaces the wubildr file on the root partition. (This doesn't happen on all wubi installs, just the ones that grub can identify - the ones installed on the main windows partition - due to another unrelated bug).

That's why I suggested to replace the wubildr with the leftover wubildr from the installation. For the 10.04 to 10.10 upgrade this gets Wubi Ubuntu booting again. 

However, that didn't work this time. So some other part of the grub update must be failing. Grub has a simple bootloader component, but it also has many modules plus the grub menu itself stored on the linux partition. The grub bootloader (wubildr for wubi installs) loads these modules and then it tries to process the grub menu. It's finding an incompatibility between the commands used in grub.cfg and the modules themselves. That's what those errors are.

So what you did is eliminate all those little commands that are causing the incompatibility (you could also have commented out the one it's complaining about - loadfont - but it's easier to just do what you did).

Honestly, I am puzzled by the grub devs. I reported this problem around July/August when 10.04.1 came out, but there were issues like this before that. This latest grub update - from the bug report - appears they did just a single test before promoting the fix.

When I tested the 10.04.1 bug, I found that after applying the workaround to get it booting, running "sudo update-grub" actually fixed the problem. It regenerates the grub.cfg menu identically as before as far I recall, so it must be doing something else that fixes the issue. Give it a try - at the worst you just follow the same workaround.

But since there's no wubi-specific documentation and the devs aren't sharing anything, your guess is as good as mine.

My recommendations for any wubi install is to lock the versions of grub-pc and grub-common (and lupin-support) in synaptic. The updates are never security related and they are very poorly tested.

---

### Post by Paper Pusher on 2010-11-26
my netbook has the same problem as op.
i will follow bcbc's instructions in the morning.

bcbc's comments are frightening.  the grub situation seems out of step with the spirit of ubuntu.

---

### Post by bcbc on 2010-11-26
> **Paper Pusher said:**
> my netbook has the same problem as op.
i will follow bcbc's instructions in the morning.

bcbc's comments are frightening.  the grub situation seems out of step with the spirit of ubuntu.

Here's the bug report for this latest fix where it certainly appears a single test case was used to decide it was OK: [https://bugs.launchpad.net/wubi/+bug/581760](https://bugs.launchpad.net/wubi/+bug/581760)

Also, bear in mind that these known wubi bugs remain unfixed:
[https://bugs.launchpad.net/wubi/+bug/610898](https://bugs.launchpad.net/wubi/+bug/610898) (this bug reported in July, but originally this was reported in April where the problems affected all installs, not just wubi: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724))
Bug 610898 also specifically mentions the booting problem with wubi installs on the same partition as windows.

The following bug is specifically on the lupin package that results in grub not being able to identify certain wubi installs: [https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/604417](https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/604417)

This bug documents the broken wubildr problem on upgrades from 10.04.1 to 10.10. This problem is very similar to the current wubildr problems on 10.04 and newly on 10.10, except there is at least an easy workaround: [https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/653134](https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/653134)

---

### Post by Paper Pusher on 2010-11-27
i installed wubi on my msws7se netbook because i thought wubi is less invasive and therefore safer.  bcbc's comments make me think wubi isn't such a good idea.

---

### Post by bcbc on 2010-11-27
> **Paper Pusher said:**
> i installed wubi on my msws7se netbook because i thought wubi is less invasive and therefore safer.  bcbc's comments make me think wubi isn't such a good idea.
There are two issues with Wubi and Grub. 

The first affects only the Wubi install, if you installed on the same partition as Windows i.e. C: drive. This is the one that stops Ubuntu booting after updating grub if you are on 10.04.1.

The second only affects installs that aren't on the same partition as Windows. It presents the screen asking where to install the grub bootloader during grub updates. This can lead a user unfamiliar with grub to overwrite their bootloader in the master boot record. This is actually easier to fix, since you just have to reinstall the bootloader. (The only issue might be if you have an OEM computer with a custom bootloader).

My feeling is when you choose to dual boot with an unfamiliar OS, whether through Wubi or a direct dual boot, of course there is always some risk. Wubi is no exception. But I wouldn't characterize Wubi as risky. 

Right now I'd say, just avoid any updates to packages grub-pc and grub-common.

---

### Post by WhatAbout on 2010-11-27
> **bcbc said:**
> OK do this instead:
Boot a live CD, then edit grub.cfg as follows:
```
sudo mkdir /media/win 
sudo mount /dev/sda1 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
sudo cp /mnt/boot/grub/grub.cfg /mnt/boot/grub/grub.cfg.copy
sudo chmod +w /mnt/boot/grub/grub.cfg
gksu gedit /mnt/boot/grub/grub.cfg
```Delete all lines up to (not including) the first line that starts with "menuentry"
Save, reboot.

You really dont need to delete the functions as they come in handy. The problem is that there are two places in the .cfg that get addressed wrongly, and as far as i can see, it should only affect people on wubi. Below you can see (I marked the lines red) where it goes wrong. The [COLOR=Red]root.disk[/COLOR] is not found in that folder if the root is set to (hd0,2) (this is true as long as its not the partition win is installed). So we need to correct these two lines to [COLOR=SeaGreen]loopback loop0 /host/ubuntu/disks/root.disk[/COLOR] as the root is going to be the point ubuntu is installed, and in this file system the root.disk is under the [COLOR=SeaGreen]/host/.../[/COLOR] (in my case and in default webui install). 

A part of my old grub.cfg file. (actually this is generated if you do sudo update-grub when booted):

```
insmod ntfs
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 8ce2a4f2e2a4e226
[COLOR=Red]loopback loop0 /ubuntu/disks/root.disk[/COLOR]
set root=(loop0)
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
insmod ntfs
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 8ce2a4f2e2a4e226
[COLOR=Red]loopback loop0 /ubuntu/disks/root.disk[/COLOR]
set root=(loop0)
set locale_dir=($root)/boot/grub/locale
set lang=en
```

---

### Post by bcbc on 2010-11-27
> **WhatAbout said:**
> You really dont need to delete the functions as they come in handy. The problem is that there are two places in the .cfg that get addressed wrongly, and as far as i can see, it should only affect people on wubi. Below you can see (I marked the lines red) where it goes wrong. The [COLOR=Red]root.disk[/COLOR] is not found in that folder if the root is set to (hd0,2) (this is true as long as its not the partition win is installed). So we need to correct these two lines to [COLOR=SeaGreen]loopback loop0 /host/ubuntu/disks/root.disk[/COLOR] as the root is going to be the point ubuntu is installed, and in this file system the root.disk is under the [COLOR=SeaGreen]/host/.../[/COLOR] (in my case and in default webui install). 

A part of my old grub.cfg file. (actually this is generated if you do sudo update-grub when booted):

```
insmod ntfs
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 8ce2a4f2e2a4e226
[COLOR=Red]loopback loop0 /ubuntu/disks/root.disk[/COLOR]
set root=(loop0)
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
insmod ntfs
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 8ce2a4f2e2a4e226
[COLOR=Red]loopback loop0 /ubuntu/disks/root.disk[/COLOR]
set root=(loop0)
set locale_dir=($root)/boot/grub/locale
set lang=en
```

No that's not true. Set root=(hd0,2) sets / to the second partition (/dev/sda2) which in this case is your windows partition. Then /ubuntu/disks/root.disk is actually your root.disk.
It's mounted as /host in the booted wubi install, but grub has to load itself (most of grub is on the root.disk).

You can go to a grub prompt and try it (assuming your windows partition is /dev/sda2):
ls (hd0,2)/ubuntu/disks/root.disk
is the same as:
set root=(hd0,2)
ls /ubuntu/disks/root.disk

Furthermore, that loopback line is actually what allows grub to find the kernel and initramfs to load ubuntu. Without it, you cannot boot a wubi install. (You'll see it later in the menuentries)

---

### Post by WhatAbout on 2010-11-27
The fact is that it is the root.disk grub cant find. And that if you specify that it is located in the /host folder the boot up will proceed normally.

I just went through with my own laptop and now my desktop. They had the same boot problem after the recent common-grub updates.

---

### Post by bcbc on 2010-11-27
> **WhatAbout said:**
> The fact is that it is the root.disk grub cant find. And that if you specify that it is located in the /host folder the boot up will proceed normally.

I just went through with my own laptop and now my desktop. They had the same boot problem after the recent common-grub updates.

On the contrary, that grub.cfg file is actually stored on the root.disk. So if grub can't see the root.disk, how can it see the grub.cfg file?

---

### Post by regindk on 2010-11-27
Been having the same problem, this is how I manipulated grub.cfg:

#if loadfont /usr/share/grub/unicode.pf2 ; then
#  set gfxmode=640x480
#  insmod gfxterm
#  insmod vbe
#  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
#    terminal gfxterm
#  fi
#fi

The whole block using the loadfont command has been commented out... smooth booting afterwards... use it at your own risk!

---

### Post by bcbc on 2010-11-28
> **regindk said:**
> Been having the same problem, this is how I manipulated grub.cfg:

#if loadfont /usr/share/grub/unicode.pf2 ; then
#  set gfxmode=640x480
#  insmod gfxterm
#  insmod vbe
#  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
#    terminal gfxterm
#  fi
#fi

The whole block using the loadfont command has been commented out... smooth booting afterwards... use it at your own risk!
That works. When you see what command is causing the failure you can eliminate that from the code. 

When 10.10 came out there were other commands/functions that weren't working with the upgrade e.g. gfxterm. I tried eliminating the loadfont section but it didn't work. Eventually I got it to work but it was a time consuming process to try to pin down the exact points of failure.
In the end I found it simply easier to delete all lines up to the first menuentry. It may be a bit extreme, but I haven't noticed any difference in function. 
It's also easier to explain and easier to do.

---

### Post by RedEyedMars on 2010-12-01
Just wanted to comment, as a newbie, what didn't work at first with the proposed solution was that the "win" folder was actually "Acer"... so when I changed that, I didn't get any error messages... just trying to help :)

cheers

---

### Post by andreasbuykx on 2010-12-19
Hi all, I tried the wubildr copy trick and it failed for me: I still get the error message. Unfortunately, my laptop doesn't allow me to boot from a CD: even with a Live CD inserted I get the windows/ubuntu boot menu. What possibilities do I have to get my laptop to boot from CD?

Thanks,
Andreas

---

### Post by Rubi1200 on 2010-12-19
Hi,
when the computer starts you need to press either F2 or F12 (sometimes Del depending on the manufacturer) to get into BIOS. From there, find the menu that allows you to change the boot device priority and set it to boot from the CD drive (usually a menu item that says Boot).

If that doesn't help, let us know and we can try something else.

Are you able to boot into Windows normally?

---

