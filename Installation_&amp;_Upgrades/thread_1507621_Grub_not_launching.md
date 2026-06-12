---
title: "Grub not launching"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by jeanloup on 2010-06-11
Hi folks,

Ever since I've upgraded to Ubuntu 10.04 I've had no end of trouble and when I finally find a solution for something, it seems something else pops up. Still what's been pretty consistent so far is just how hard Grub is making my life.

I'll spare you the trouble I've had to begin with which led to my getting a brand new hard drive (though I'm sure the old one is still fine)

Essentially, I've got this new 160GB SATA drive which I first put XP back on (I always put Windows first, makes partitioning easier) and then with the Ubuntu live CD I partitioned the disk into appropriate size drives for /, /home and swap. The installation went fine and I can launch Ubuntu without too many problems (it froze on me a few times for no apparent reason).

My problem is, when the computer boots up, Grub no longer shows up to give me a choice between Linux and Windows and I've been banging my head with command-line configurations to try and work out why that is. So far I've found nothing that can shed some light on why it just forgets about Grub. It might be a hardware problem, but if so then what? It could be something to do with Grub or maybe it's something to do with the way windows is installed.

I've re-installed Ubuntu just now (for the 4th time I think) and having tried to be more thorough in defining mount points while assigning partitions, I noticed it gave my windows partition the boot flag and added a /boot folder on the partition itself... that didn't stop the machine to just boot into Ubuntu.

My fdisk isn't that out of this world, I have
/dev/sda1 ntfs 50GB /windows
/dev/sda2 ext4 18GB /
/dev/sda3 swap 2GB
/dev/sda4 ext4 40GB /home

and about ~45GB unallocated while I ponder whether it's worth trying to save some space for another OS / another Linux

I can provide more info if anyone can help but I'm getting quite tired with this, I really want Ubuntu to work but it seems to run on some software which isn't terribly complete... I miss the days when I could just configure lilo within a GUI :(

Thanks for any light you can shed

---

### Post by drs305 on 2010-06-11
Download and run *meierfra's* boot info script. If it's a Grub issue the results from the script might show us where the problem lies.
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")


Please place the results between "code" tags, which you generate by pressing the # icon in the post's menu.

---

### Post by darkod on 2010-06-11
There shouldn't be a boot folder on the XP partition. XP boot files don't use a boot folder, and ubuntu shouldn't have anything to do with the windows boot files.

One of the reasons it shows only ubuntu (and boots ubuntu directly probably) is if it can't read the XP boot files properly. Grub2 depends on detecting correct boot files to determine which OS, if any, is installed to which partition. No boot files, no XP entry in grub2, no menu to select from (it thinks you've got only ubuntu).

Maybe this is related to the mysterious boot folder on /dev/sda1, maybe not.

If you run the boot info script as per these instructions it should show more details:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by BoneKracker on 2010-06-11
Ubuntu wouldn't be starting if GRUB weren't working (or some other bootloader was set up to load it, which I assume isn't the case).

It may be that it's not configured with a timeout value, in which case it would immediately boot the default option.

I can't tell you precisely how to fix this because I don't use Ubuntu, but I know there is some Ubuntu-specific GRUB-2 documentation either in these forums to linked to from here.

Also, I don't know if it still works this way in GRUB-2, but in the old GRUB, if there was no timeout value you could force it to bring the menu up anyway by pressing Esc or something at just the right moment during the boot process (when GRUB is just starting).  Before you try that, you should try to find the GRUB-2 documentation and see.

---

### Post by darkod on 2010-06-11
The timeout value, and the default OS and other settings are in /etc/default/grub. You need to run sudo update-grub after any change in the config files to create updated grub.cfg.

For grub2 you press Shift to force the menu to show, but you need to time it before it actually starts loading ubuntu.

---

### Post by jeanloup on 2010-06-12
Hey folks,

Thanks for the suggestions, regarding timeout values, just looking at them doesn't suggest it just boots in, ie, the value is set at 10, not 0. One thing it could be is when I installed XP, my old HDD was still connected and has a similar config on it which may have confused Windows when it installed on the new drive. why it would do that I don't know, but it's just possible the boot sector for Windows isn't actually on this new drive.

Anyway, here's the results of my boot info script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   102,526,829   102,526,767   7 HPFS/NTFS
/dev/sda2    *    102,526,830   139,492,394    36,965,565  83 Linux
/dev/sda3         139,492,395   143,653,229     4,160,835  82 Linux swap / Solaris
/dev/sda4         143,653,230   225,745,379    82,092,150  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        8C200D75200D6792                       ntfs                                     
/dev/sda2        d4e59ff9-2a46-4d81-b612-de46d1784c53   ext4                                     
/dev/sda3        ea9c2244-c698-4d80-900a-8d09c880dea6   swap                                     
/dev/sda4        6ba04cc0-b438-41a4-bd13-1855cdeb24f8   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /windows                 fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda4        /home                    ext4       (rw)


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set d4e59ff9-2a46-4d81-b612-de46d1784c53
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
set root='(hd0,2)'
search --no-floppy --fs-uuid --set d4e59ff9-2a46-4d81-b612-de46d1784c53
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
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set d4e59ff9-2a46-4d81-b612-de46d1784c53
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=d4e59ff9-2a46-4d81-b612-de46d1784c53 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set d4e59ff9-2a46-4d81-b612-de46d1784c53
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=d4e59ff9-2a46-4d81-b612-de46d1784c53 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set d4e59ff9-2a46-4d81-b612-de46d1784c53
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=d4e59ff9-2a46-4d81-b612-de46d1784c53 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set d4e59ff9-2a46-4d81-b612-de46d1784c53
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=d4e59ff9-2a46-4d81-b612-de46d1784c53 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set d4e59ff9-2a46-4d81-b612-de46d1784c53
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set d4e59ff9-2a46-4d81-b612-de46d1784c53
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
UUID=d4e59ff9-2a46-4d81-b612-de46d1784c53 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=6ba04cc0-b438-41a4-bd13-1855cdeb24f8 /home           ext4    defaults        0       2
# /windows was on /dev/sda1 during installation
UUID=8C200D75200D6792 /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# swap was on /dev/sda3 during installation
UUID=ea9c2244-c698-4d80-900a-8d09c880dea6 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  56.9GB: boot/grub/core.img
  54.9GB: boot/grub/grub.cfg
  56.9GB: boot/initrd.img-2.6.32-21-generic
  57.0GB: boot/initrd.img-2.6.32-22-generic
  56.9GB: boot/vmlinuz-2.6.32-21-generic
  56.9GB: boot/vmlinuz-2.6.32-22-generic
  57.0GB: initrd.img
  56.9GB: initrd.img.old
  56.9GB: vmlinuz
  56.9GB: vmlinuz.old

```
For some reason sda1 (windows) had the boot flag, so I'm changing it back to sda2 (ubuntu) and see what happens. I suspect that's why I now have a /boot folder under the mount directory /windows. My update manager is currently running so I'll report back when I'm able to reboot. 

Cheers

Edit: Update manager put a new version of the kernel thus giving me a choice between 2 kernels to boot but grub is still not showing up on first boot. 

Also FYI, here's the contents of /etc/default/grub

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

---

### Post by wilee-nilee on 2010-06-12
So your missing the boot files in sda1 XP and grub is there instead. This is fixable, I know the process for getting grub out of sda1, but am not sure the best way to get the XP boot files in. But the two people who responded drs305,and darkod are. So letting them help should get this fixed. I have a method I would use but it is a longer way around then their methods. Moving the boot flag as you have already discovered didn't make any difference.

Basicaly you have this,
File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot/grub/core.img

And it should look like this,
File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   **/boot.ini /ntldr /NTDETECT.COM**

---

### Post by jeanloup on 2010-06-12
The lack of a boot sector for XP would explain why it's not detected by Grub, and therefore re-inforces my convinction that I'm just gonna have to re-install XP.

However, it still doesn't explain why Grub isn't showing up despite clearly detecting 2 versions of the Linux kernel... or am I missing something like "well they're both Linux so it won't give you a choice anyway"...?

---

### Post by wilee-nilee on 2010-06-12
> **jeanloup said:**
> The lack of a boot sector for XP would explain why it's not detected by Grub, and therefore re-inforces my convinction that I'm just gonna have to re-install XP.

However, it still doesn't explain why Grub isn't showing up despite clearly detecting 2 versions of the Linux kernel... or am I missing something like "well they're both Linux so it won't give you a choice anyway"...?

If you just custom reinstalled XP into the partition it is in now and reloaded grub to the MBR you would be set. But the files I highlighted can be loaded into the XP partition after removing the grub boot files in the XP partition. So you can wait for help from somebody who knows this method, or just reinstall XP.

Now grub somehow got into sda1, this is only accomplished by the user doing this, or missing a process like checking the advanced button in the Ubuntu install on the last gui of the install setup. That advanced button will show you where grub is pointed and it should be to sda the MBR. You also mentioned having the old HD still attached, this may have been part of the problem.

If it was me I wouldn't just start reinstalling again, this has not worked for you so far. I think after this is all fixed and you take a closer look at what has happened you will see where the mistakes were made. 

I will say that I have yet to see a bootloader problem that was not basically user error by not being familiar with how this all works, I'm not sure this is reassuring but your not alone. There are some suspected OS errors but none confirmed.

---

### Post by drs305 on 2010-06-12
> **jeanloup said:**
> The lack of a boot sector for XP would explain why it's not detected by Grub, and therefore re-inforces my convinction that I'm just gonna have to re-install XP.

You have to restore the Windows boot files, since they are no longer present in sda1.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector")
Here is another link, whose process is mentioned briefly in the above link if you can't or don't want to use TestDisk. You would refer to the "Restore XP" section.
[http://ubuntuforums.org/showthread.php?t=1014708]("http://ubuntuforums.org/showthread.php?t=1014708")

> 
However, it still doesn't explain why Grub isn't showing up despite clearly detecting 2 versions of the Linux kernel... or am I missing something like "well they're both Linux so it won't give you a choice anyway"...?

Grub2 only sees Linux installed in your main Ubuntu partition. The default action for a "one-OS" system is to boot directly without displaying a menu. Even though you have 2 kernels, the menu display is only activated when there are additional entries in the *30_os-prober* section of grub.cfg. As you surmised, Grub2 doesn't consider additional kernels of the current linux OS reason to display the menu. 

You should be able to display the menu with the SHIFT key if you want to display the menu to pick an older kernel.

---

### Post by oldfred on 2010-06-12
For windows to see the windows partition the boot flag has to be on the windows partition. Linux does not use the boot flag. three ways to get files back, which ever works best for you.

Description of the Windows XP Recovery Console for advanced users
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type this commands one at a time.

FIXMBR  C:  <--DO NOT run if you want to keep grub in the MBR
FIXBOOT  C:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\

or:

Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 

Rebuild boot.ini
BOOTCFG  /rebuild
[http://support.microsoft.com/kb/291980](http://support.microsoft.com/kb/291980)
[http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm)

or

How to fix XP when the boot files are missing & info on windows in logical partitions
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
missing boot files meieifra - post 10
[http://ubuntuforums.org/showthread.php?t=1241394](http://ubuntuforums.org/showthread.php?t=1241394)

---

### Post by jeanloup on 2010-07-04
Oh I'd totally forgotten about this thread. Just wanted to say thanks for all the advice. At the end, I just re-installed Windows with all other drives disconnected and it went all fine. So somehow the boot sector for Windows had been put on a different drive, which is odd but there you go.

---

### Post by darkod on 2010-07-04
> **jeanloup said:**
> Oh I'd totally forgotten about this thread. Just wanted to say thanks for all the advice. At the end, I just re-installed Windows with all other drives disconnected and it went all fine. So somehow the boot sector for Windows had been put on a different drive, which is odd but there you go.

Actually it's not odd at all. With multiple disks you have to be careful when installing or repairing windows. It will always put it's bootloader to the disk which is first in the hdd boot order. So you need to set the windows disk as first before starting the procedure, even if later you are not using it as main boot disk.

Windows doesn't give you an option to select where to install the bootloader and it will simply install it onto the disk first in boot order.

---

