---
title: "Grub Upgrade - Dangerous Direction Screenshot"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by MikeB007 on 2010-05-06
Symptom: 

initiated update.  Grub update required user input.  The 'help' message is incorrect.  Attached is a .jpg of a Grub message during the upgrade.

Question:  

how does this get corrected?  I would post an alternative wording but honestly, I have no idea what is appropriate direction to a user at this point.

---

### Post by quixote on 2010-05-07
This is officially a type of bug; user-interface bug, but still a bug.  So you would report it on the lucid section of [launchpad]("https://launchpad.net/ubuntu/lucid").  That involves setting up a launchpad account.  It's a bit of a bother first time around, but it's the only way ubuntu can get better.

First, search on a few key words to make sure the bug wasn't already filed.

Also, explain what the bug is.  I take it your grub was NOT on an unexistent drive even though the help popup said it was?

---

### Post by MikeB007 on 2010-05-08
Thank you.  i'll head over and do as you suggest.

The bug is the recommendation to install grub on all partitions eg. sdb, sdb1, sdb2, ...  That isn't a good thing (at least for a dual boot sys) as i learned first hand.

Cheers.

---

### Post by kansasnoob on 2010-05-08
I filed this bug report:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

> This is a horrible way to file a bug report and I'm aware of that, but this needs to be considered.

Throughout various upgrade and/or update procedures in Ubuntu and it's variants the user gets a display asking where to install grub(2). There is a suggestion that if in doubt to install to the mbr of all drives.

Unfortunately most new (and some old) users have no idea how drives/partitions are designated in Ubuntu, and they're clueless as to what an mbr is!

So basically you see a screen that says, "if in doubt select all", and you do so. Now, I'm aware those are not the exact words but I've been following (and trying to help folks fix) these problems since Lucid was released.

It's particularly troublesome when someone installs grub2 to an NTFS partition with a Win OS so I'd at least suggest making grub installation to an NTFS (or any FAT) partition very difficult.

Honestly I'm not sure what the solution should be, but I know Colin Watson deals with a lot of these grub2 issues and I've come to trust his judgment. Consider the following options:

#1: Display nothing but drives, that is "sda", "sdb", etc, and NO individual partitions. But create another "advanced" tab/option to allow installation to a partition.

#2: Increase the amount of text explaining the difference between drives and partitions, why it's a bad idea to install to a partition etc. IMHO that's a horrible option. (The more text the less likely a new user is to read it.)

#3: Figure out a way to always have grub(2) install itself where it was to begin with. (maybe a bad idea if the original install was wrong.)

While I think option #1 is great I have no idea how complicated that would be.

Does any of that make sense?

I'd be glad to test any potential "fixes" :^)

So I would suggest changing the status of that bug report from new to confirmed, and adding any comments you feel appropriate. 

Note: You catch more flies with honey than vinegar! So always be polite at Launchpad no matter how much you disagree with the devs, it's OK to state your disappointment, try to express why you feel you're right, but once the language becomes tense all action basically comes to an end.

---

### Post by kansasnoob on 2010-05-08
Oh, and don't expect action real soon. UDS-M is coming up and then Maverick Alpha1, I already have the toolchain up.

---

### Post by quixote on 2010-05-08
I didn't even catch the fact that it could be suggesting to install to all drives.  Sheesh.  Bug, indeed!  I'll head on over to Launchpad and second it.

---

### Post by nomansland on 2010-05-08
As a noob trying to upgrade a multiboot system (WinXP, Ubuntu 9.10, and Mepis 8.0 and 8.5), I didn't know what to do with this and followed the advice in the help screen, resulting in the loss of ability to boot into WinXP (even though the grub screen has that option available, but it jut goes into a black screen with blinking cursor). I believe I have something similar to the setup in the screen grab (sda with Win only, sdb with partitions for the linux distros) and it worked fine before the upgrade (which actually was using the grub installed previously with my 9.10 install and currently with the last Mepis install). 

Any suggestions on how I should try to fix this, or if I should just reinstall 10.04 from CD (all really important files are on a separate NAS, so no biggie here, except I don't want to reinstall WinXP and required programs - that would be a major pita; wish I didn't need Autocad and some other engineering software to make a living and could just move to linux, but ...)? If reinstall is the right answer, how should the grub be setup for a dual drive arrangement?

Thanks for any suggestions you can offer.

---

### Post by arpanaut on 2010-05-08
> I filed this bug report:

[https://bugs.launchpad.net/ubuntu/+s...b2/+bug/576724](https://bugs.launchpad.net/ubuntu/+s...b2/+bug/576724)

Thanks, kansasnoob, I added my two-bits.
I knew that this was going to be a train wreck, but Lucid final had "left the station" by the time I noticed.

@nomansland: I don't think that a re-install will be necessary, but your Windows boot will need to be fixed before re-installing grub will be effective in being able to boot windows from grub.  Search around many possible fixes for Win. boot.  Wish I knew the definitive answer.

---

### Post by kansasnoob on 2010-05-08
> **nomansland said:**
> As a noob trying to upgrade a multiboot system (WinXP, Ubuntu 9.10, and Mepis 8.0 and 8.5), I didn't know what to do with this and followed the advice in the help screen, resulting in the loss of ability to boot into WinXP (even though the grub screen has that option available, but it jut goes into a black screen with blinking cursor). I believe I have something similar to the setup in the screen grab (sda with Win only, sdb with partitions for the linux distros) and it worked fine before the upgrade (which actually was using the grub installed previously with my 9.10 install and currently with the last Mepis install). 

Any suggestions on how I should try to fix this, or if I should just reinstall 10.04 from CD (all really important files are on a separate NAS, so no biggie here, except I don't want to reinstall WinXP and required programs - that would be a major pita; wish I didn't need Autocad and some other engineering software to make a living and could just move to linux, but ...)? If reinstall is the right answer, how should the grub be setup for a dual drive arrangement?

Thanks for any suggestions you can offer.

Slow down! Reinstalling Ubuntu will do no good if this is the problem:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

If you're unsure and need additional help please start a new thread and include the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by coffeecat on 2010-05-08
> **nomansland said:**
> Thanks for any suggestions you can offer.

If you installed grub to the boot sector of the Windows partition, this link may help:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

It may be useful to run the Boot Info Script first to see whether grub is really in your Windows partition boot sector. Link here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Re-installing 10.04 won't help to repair the boot sector in a Windows partition. You need the Windows tools or testdisk as described in the first link above.

**Edit:** kansasnoob beat me to it with exactly the same links. Great minds clearly think alike. :wink:

---

### Post by Blade Runner on 2010-05-10
Hi Guys

I've been reading through threads to try and resolve the issues I'm having and this seems to address what's happening.

I upgraded from 9.10 to 10.04 but on reboot get the following error message:

> error: the symbol 'grub_puts_' not found

I have 3 internal SATA drives - one with ubuntu, one ext3 for file storage and one with Win XP. I also have an external USB hard drive. All drives were plugged in and detected when I performed the upgrade. One thread suggested I disconnect all the other drives to resolve the boot issue but this did not solve it.

Below is the output of the boot script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 2277439 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5b046c26

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    40,001,849    40,001,787  83 Linux
/dev/sda2          40,001,850    44,002,034     4,000,185  82 Linux swap / Solaris
/dev/sda3          44,002,035   488,392,064   444,390,030  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        b2c75f0e-0c99-4c9b-bfee-205bfdde9cef   ext3                                     
/dev/sda2        4690fb24-4bf7-4a80-a808-6eee5db736ae   swap                                     
/dev/sda3        e057fc0b-1aec-4ad9-bb76-a50ed5a0cbc0   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda1        /media/b2c75f0e-0c99-4c9b-bfee-205bfdde9cef ext3       (rw,nosuid,nodev,uhelper=devkit)


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
search --no-floppy --fs-uuid --set b2c75f0e-0c99-4c9b-bfee-205bfdde9cef
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
search --no-floppy --fs-uuid --set b2c75f0e-0c99-4c9b-bfee-205bfdde9cef
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
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b2c75f0e-0c99-4c9b-bfee-205bfdde9cef
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=b2c75f0e-0c99-4c9b-bfee-205bfdde9cef ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b2c75f0e-0c99-4c9b-bfee-205bfdde9cef
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=b2c75f0e-0c99-4c9b-bfee-205bfdde9cef ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b2c75f0e-0c99-4c9b-bfee-205bfdde9cef
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=b2c75f0e-0c99-4c9b-bfee-205bfdde9cef ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b2c75f0e-0c99-4c9b-bfee-205bfdde9cef
	echo	'Loading Linux 2.6.31-21-generic ...'
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=b2c75f0e-0c99-4c9b-bfee-205bfdde9cef ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b2c75f0e-0c99-4c9b-bfee-205bfdde9cef
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b2c75f0e-0c99-4c9b-bfee-205bfdde9cef
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP Media Center Edition (on /dev/sdb1)" {
	insmod ntfs
	set root='(/dev/sdb,1)'
	search --no-floppy --fs-uuid --set 540c6a1f0c69fc7c
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
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=b2c75f0e-0c99-4c9b-bfee-205bfdde9cef / ext3 errors=remount-ro 0 1
# Entry for /dev/sda3 :
UUID=e057fc0b-1aec-4ad9-bb76-a50ed5a0cbc0 /home ext3 defaults 0 2
# Entry for /dev/sda2 :
UUID=4690fb24-4bf7-4a80-a808-6eee5db736ae none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sdb1 /media/WINDOZE ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sdc1 /media/PHAT03 ntfs-3g defaults,locale=en_GB.UTF-8 0 0

=================== sda1: Location of files loaded by Grub: ===================


   1.1GB: boot/grub/core.img
   1.1GB: boot/grub/grub.cfg
   1.1GB: boot/initrd.img-2.6.31-21-generic
   1.1GB: boot/initrd.img-2.6.32-22-generic
   1.1GB: boot/vmlinuz-2.6.31-21-generic
   1.1GB: boot/vmlinuz-2.6.32-22-generic
   1.1GB: initrd.img
   1.1GB: initrd.img.old
   1.1GB: vmlinuz
   1.1GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd 
```

I too got hit with the following: [http://art.ubuntuforums.org/showthread.php?t=1475385](http://art.ubuntuforums.org/showthread.php?t=1475385) but I didn't install grub to all drives. I did, however, select to install to sda1 - the boot partition - thinking this was the correct option, which by what I've been reading is incorrect, as instead of installing grub to the root partition I should have installed it to the drive, ie. sda. Is this correct? If so how do I now change this as it's looking for core.img but it cannot be found at that location.

Any help much appreciated :)

BR

---

### Post by kansasnoob on 2010-05-10
> **Blade Runner said:**
> Hi Guys

I've been reading through threads to try and resolve the issues I'm having and this seems to address what's happening.

I upgraded from 9.10 to 10.04 but on reboot get the following error message:



I have 3 internal SATA drives - one with ubuntu, one ext3 for file storage and one with Win XP. I also have an external USB hard drive. All drives were plugged in and detected when I performed the upgrade. One thread suggested I disconnect all the other drives to resolve the boot issue but this did not solve it.

Below is the output of the boot script:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 2277439 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5b046c26

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    40,001,849    40,001,787  83 Linux
/dev/sda2          40,001,850    44,002,034     4,000,185  82 Linux swap / Solaris
/dev/sda3          44,002,035   488,392,064   444,390,030  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        b2c75f0e-0c99-4c9b-bfee-205bfdde9cef   ext3                                     
/dev/sda2        4690fb24-4bf7-4a80-a808-6eee5db736ae   swap                                     
/dev/sda3        e057fc0b-1aec-4ad9-bb76-a50ed5a0cbc0   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda1        /media/b2c75f0e-0c99-4c9b-bfee-205bfdde9cef ext3       (rw,nosuid,nodev,uhelper=devkit)


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
search --no-floppy --fs-uuid --set b2c75f0e-0c99-4c9b-bfee-205bfdde9cef
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
search --no-floppy --fs-uuid --set b2c75f0e-0c99-4c9b-bfee-205bfdde9cef
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
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b2c75f0e-0c99-4c9b-bfee-205bfdde9cef
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=b2c75f0e-0c99-4c9b-bfee-205bfdde9cef ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b2c75f0e-0c99-4c9b-bfee-205bfdde9cef
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=b2c75f0e-0c99-4c9b-bfee-205bfdde9cef ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b2c75f0e-0c99-4c9b-bfee-205bfdde9cef
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=b2c75f0e-0c99-4c9b-bfee-205bfdde9cef ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b2c75f0e-0c99-4c9b-bfee-205bfdde9cef
	echo	'Loading Linux 2.6.31-21-generic ...'
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=b2c75f0e-0c99-4c9b-bfee-205bfdde9cef ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b2c75f0e-0c99-4c9b-bfee-205bfdde9cef
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set b2c75f0e-0c99-4c9b-bfee-205bfdde9cef
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP Media Center Edition (on /dev/sdb1)" {
	insmod ntfs
	set root='(/dev/sdb,1)'
	search --no-floppy --fs-uuid --set 540c6a1f0c69fc7c
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
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=b2c75f0e-0c99-4c9b-bfee-205bfdde9cef / ext3 errors=remount-ro 0 1
# Entry for /dev/sda3 :
UUID=e057fc0b-1aec-4ad9-bb76-a50ed5a0cbc0 /home ext3 defaults 0 2
# Entry for /dev/sda2 :
UUID=4690fb24-4bf7-4a80-a808-6eee5db736ae none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sdb1 /media/WINDOZE ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sdc1 /media/PHAT03 ntfs-3g defaults,locale=en_GB.UTF-8 0 0

=================== sda1: Location of files loaded by Grub: ===================


   1.1GB: boot/grub/core.img
   1.1GB: boot/grub/grub.cfg
   1.1GB: boot/initrd.img-2.6.31-21-generic
   1.1GB: boot/initrd.img-2.6.32-22-generic
   1.1GB: boot/vmlinuz-2.6.31-21-generic
   1.1GB: boot/vmlinuz-2.6.32-22-generic
   1.1GB: initrd.img
   1.1GB: initrd.img.old
   1.1GB: vmlinuz
   1.1GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd 
```

I too got hit with the following: [http://art.ubuntuforums.org/showthread.php?t=1475385](http://art.ubuntuforums.org/showthread.php?t=1475385) but I didn't install grub to all drives. I did, however, select to install to sda1 - the boot partition - thinking this was the correct option, which by what I've been reading is incorrect, as instead of installing grub to the root partition I should have installed it to the drive, ie. sda. Is this correct? If so how do I now change this as it's looking for core.img but it cannot be found at that location.

Any help much appreciated :)

BR

Look here:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

Please also go to the Bug Report and add that you're effected and leave a comment! Devs don't read the forums.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

---

### Post by Blade Runner on 2010-05-10
Hi

Thanks for the response, however, I'm not trying to repair my Windows disk. In fact all disks have been disconnected bar my primary ubuntu disk, which is whats reporting the grub error.

Following the testdisk instructions (to see if it would also apply to linux) I get as far as the  > Fifth screen:  Select the Windows system partition  and choose "boot" but there is no option to choose boot - the primary partition is already flagged as bootable.

Looking at the output of the boot info script:

```
sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 2277439 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

```

How do I resolve the incorrect location? Any ideas?

TIA

BR

---

### Post by oldfred on 2010-05-10
the PBR partition boot record or boot sector is not used normally except by windows or those chainbooting from another boot loader. Having grub installed to a Ubuntu partition will not cause any problem as long as the grub in the MBR points to the correct partition and you are not chainbooting (uncommon).

---

### Post by paulm2822 on 2010-05-14
wow I got bit by this too! see:

[http://ubuntuforums.org/showthread.php?p=9287278&posted=1#post9287278](http://ubuntuforums.org/showthread.php?p=9287278&posted=1#post9287278)

---

### Post by kansasnoob on 2010-05-15
I was playing with Debian Squeeze trying to resolve an issue with usplash and happened to change from grub-legacy to grub2 and they've got it right (at least closer to right):

[ATTACH]157072[/ATTACH]

I'll post this info at my bug report also.

---

### Post by kansasnoob on 2010-05-15
My bug report post:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724/comments/15](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724/comments/15)

---

### Post by kansasnoob on 2010-05-15
I'd love it if someone with insider contacts to the devs could draw some attention to this :)

---

