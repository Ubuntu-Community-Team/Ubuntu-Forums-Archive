---
title: "Trying to untangle OS loaders after W7 + Ubuntu"
date: 2011-01-31
forum: Installation &amp; Upgrades
---

### Post by AlterMind on 2011-01-31
Hello All,
I'd need some help to untangle some intricated OS loaders / boot menus after I did two software upgrades. My desktop computer hosts two hards disks, that i'll call Disk1 and Disk2. Let me describe the chronology:

_1. Initial situation_
Running Windows Vista on Disk1. No boot manager, loading Vista straight. Disk1 is the first disk to boot from and contains at its very beginning a small, hidden partition with factory recovery files.

_2. Install Win 7 on Disk2_
As requested, Win 7 got installed on Disk2 and, without asking anything, a boot manager was installed by Windows, allowing me to choose between Win 7 (default, on Disk2) and Vista (on Disk1). Both menu entries work. So far so good, apparently. As Disk1 is the first disk to boot, I guess that the boot menu is actually somewhere there ?

_3. Install Ubuntu 10.10 on Disk2_
First I free up some space at end of Disk2 for Ubuntu+swap to install, then let Ubuntu install. When things are over, I connect to Internet and let Ubutu proceed with required updates, seemingly including a kernel upograde too. 
Now, when I boot the PC I get GRUB first of all, which shows, in this order:
> 1. Ubuntu, with Linux 2.6.35-25-generic
2. Ubuntu, with Linux 2.6.35-25-generic (recovery mode)
3. Ubuntu, with Linux 2.6.35-22-generic
4. Ubuntu, with Linux 2.6.35-22-generic (recovery mode)
5. Memory test (memtest86+)
6. Memory test (memtest86+, serial console 115200)
7. Windows Vista (loader) (on /dev/sda1)
8. Windows 7 (loader) (on /dev/sda2)Now here are the issues:
a) the partition GRUB has identified in row "7" is actually the very first "hidden" system recovery partition and, honestly, I don't want it to appear in the menu
b) the partition identified in row "8" is indeed Disk1's second partition, i.e. the former Vista-only, i.e. the current LOADER to choose between Windows 7 (on Disk2) on Vista (on that actual partition)

This would indicate that the GRUB/Ubuntu setup didn't "undo" Windows 7 boot menu (which I may understand), but also didn't include a straight boot entry for Windows 7 on Disk2 in its own entries ?

What I quite expectedly would like to have is a boot menu (presumable GRUB?) as 'simple' as:
1. Ubuntu
2. Windows 7
3. Vista
which not only assumes untangling the two boot menu's, but also removing several entries in the GRUB config, which isn't easy I understood as the /boot/grub/grub.cfg file is automatically generated?

I also edited the grub.cfg file to add a new entry pointing directly at Win7 on Disk2 (i.e. presumably /dev/sdb0), but that wouldn't work (it actually started the recovery partition on /dev/sda1) meaning that Disk2 probably misses some MBR ?

Also, I have no idea where Windows stores his own boot menu file, and going through the 'My Computer' advance properties menus and dialog boxes only allows to check/uncheck options, i.e. not tune the file.

Thank you for your advice !

---

### Post by AlterMind on 2011-02-02
Hummm... Up please.  Thx !  ^_^

[COLOR=Indigo][gosh how do I get rid of this interim, no value 'reply' ?][/COLOR]

---

### Post by AlterMind on 2011-02-04
Hi again,
As I was browsing similar topics around here, I saw an advice to collect and post the boot info to facilitate investigation. So here it is:
_Note_: I could not find anything suspicious in this RESULTS.TXT file.  I howere made some comments in colour.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb  [COLOR=Purple]**[that's Win7]**[/COLOR]

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:                      [COLOR=Purple]**[this is the hidden recovery partition]**[/COLOR]
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista                      [COLOR=Purple]**[Vista, that's right]**[/COLOR]
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:                        [COLOR=Purple]**[that's my 'DATA' partition known as 'D:' under Vista]**[/COLOR]
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7                      [COLOR=Purple]**[that's the newly installed Win7 on 2nd disk]**[/COLOR]
    Boot files/dirs:   /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10                      [COLOR=Purple]**[yep, installed after shrinking sdb1 by 100 GB]**[/COLOR]
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    18,434,047    18,432,000  27 Hidden HPFS/NTFS
/dev/sda2    *     18,434,048   223,401,983   204,967,936   7 HPFS/NTFS
/dev/sda4         223,401,984   625,140,399   401,738,416   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048 2,734,445,407 2,734,443,360   7 HPFS/NTFS
/dev/sdb2       2,734,446,590 2,930,276,351   195,829,762   5 Extended
/dev/sdb5       2,734,446,592 2,921,144,319   186,697,728  83 Linux
/dev/sdb6       2,921,146,368 2,930,276,351     9,129,984  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        68E84C92E84C6104                       ntfs       WinRE                         
/dev/sda2        22884EA5884E76F7                       ntfs       SYSTEM                        
/dev/sda4        5ADC515ADC51318D                       ntfs       DATA                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        14FC0396FC0370F2                       ntfs       Système Win7                 
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        50f27f33-fc16-4c15-acf0-3c3eb5a93506   ext4                                     
/dev/sdb6        4d1e8659-c2bd-4e3c-b7d8-5542cc48aff5   swap                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 50f27f33-fc16-4c15-acf0-3c3eb5a93506
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 50f27f33-fc16-4c15-acf0-3c3eb5a93506
set locale_dir=($root)/boot/grub/locale
set lang=fr
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 50f27f33-fc16-4c15-acf0-3c3eb5a93506
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=50f27f33-fc16-4c15-acf0-3c3eb5a93506 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 50f27f33-fc16-4c15-acf0-3c3eb5a93506
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=50f27f33-fc16-4c15-acf0-3c3eb5a93506 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 50f27f33-fc16-4c15-acf0-3c3eb5a93506
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=50f27f33-fc16-4c15-acf0-3c3eb5a93506 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 50f27f33-fc16-4c15-acf0-3c3eb5a93506
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=50f27f33-fc16-4c15-acf0-3c3eb5a93506 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 50f27f33-fc16-4c15-acf0-3c3eb5a93506
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 50f27f33-fc16-4c15-acf0-3c3eb5a93506
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 68e84c92e84c6104
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 22884ea5884e76f7
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

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=50f27f33-fc16-4c15-acf0-3c3eb5a93506 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=4d1e8659-c2bd-4e3c-b7d8-5542cc48aff5 none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


1479.6GB: boot/grub/core.img
1430.2GB: boot/grub/grub.cfg
1400.9GB: boot/initrd.img-2.6.35-22-generic
1401.0GB: boot/initrd.img-2.6.35-25-generic
1479.6GB: boot/vmlinuz-2.6.35-22-generic
1479.6GB: boot/vmlinuz-2.6.35-25-generic
1401.0GB: initrd.img
1400.9GB: initrd.img.old
1479.6GB: vmlinuz
1479.6GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf sdg 
```Is anything else required ?

---

### Post by drs305 on 2011-02-04
You have provided the correct information, and we could help you tweak all your files via a terminal or text editor. However, there is a GUI app called Grub Customizer which can rearrange your Grub menu to your liking.

Here is a guide I wrote describing how to use it. If you find it doesn't accomplish what you want come back here and let us know what you still want.

[HOWTO: Grub Customizer]("http://ubuntuforums.org/showthread.php?p=10340183#post10340183")

---

### Post by AlterMind on 2011-02-04
> **drs305 said:**
> Here is a guide I wrote describing how to use it. If you find it doesn't accomplish what you want come back here and let us know what you still want.

[HOWTO: Grub Customizer]("http://ubuntuforums.org/showthread.php?p=10340183#post10340183")
Thanks a million, I'll dive into this immediately and get back to you :-)

I'm *à priori* not sure it will suffice, as it may not suppress Windows boot menu, but I'm not sure I actually have to do that either.

TTYL !

---

### Post by oldfred on 2011-02-05
When you install windows it combines all the boots into the first install with the boot flag. Your boot files for win7 were moved to the Vista partition and sdb1 is missing two boot files, so grub cannot directly boot it.
 /bootmgr /Boot/BCD

You should be able to add a boot flag to sdb1 and with windows repair CD repair it to add themissing files. You may be able to just copy the bootmgr  & BCD files but BCD will probably have to be updated.

Mostly about Vista but it is the same for 7. Lots of detail, but pictures explain a lot if you just want a quick overview.
To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

### Post by AlterMind on 2011-02-06
Thanks Oldfred, 

I've just been reviewing quickly the contents of the two actual cases you referenced, which seem to point at playing with boot flags and hiding/unhiding partitions, (re)installing Win in dedicated primary partitions and closing with Ubuntu. I'm ok to reinstall Win 7 and Ubuntu agaion as they're pretty recent, but I don't want to take any risk with my formerly existing Vista -- so I'll think this carefully over before making a decision. I may request some advice on my plan before execution  ^^

I also sas the multibooter page, tons of details and in-depth explanations, I may need to take some dedicated time to understand that, it may make me wiser before I actually start "playing".

Thanks again !

---

### Post by Quackers on 2011-02-06
AlterMind, does Ubuntu boot up when selected?

---

### Post by perspectoff on 2011-02-06
Ha ha ha. You've been hit by dueling installers.

This was an easy problem to solve in the days before Grub2. Now you have to spend a lot of time sorting it out.

I don't bother.

I merely have a small boot partition in which I store Grub Legacy (which is able to live in a partition all by itself).

Grub Legacy is used only to chainload the bootloader of whichever OS is being invoked. Each OS's bootloader is stored within the partition of the OS, and is free to update itself as it chooses, without bothering any other OS.

So Grub2 stays confined within the Ubuntu partition, and is not used for any other OS.

Complete independence.

I don't like the imperialistic design of those who say Grub2 should be used to load every other OS. Very irritating.

The solutions I use are outlined at

[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)

and

[http://kubuntuguide.org/Multiple_OS_Installation](http://kubuntuguide.org/Multiple_OS_Installation)

Grub Legacy can chainload the Windows bootloader on the first partition of the second hard drive, for example, by referring to it as (hd1,0)

(Grub Legacy starts counting at 0).

For example, the Grub Legacy menu item (in menu.lst in the boot partition) would merely read:

 title Windows on second hard drive
 root (hd1,0)
 makeactive
 chainloader +1

Easy, yeah?

---

### Post by Quackers on 2011-02-06
Ah! Living in the past :-)
Make the system more complicated to stop grub2 doing what it does.  Hmmm.
Not to mention 2 drive systems, where only the first drive is choosable as a boot device - not much use there either, if Ubuntu is on the second drive.

---

### Post by oldfred on 2011-02-06
You should not have to reinstall windows, but moving boot flags & repairing may be required. It is easier with XP. I do not know enough about the details of BCD which in effect replaced boot.ini.

How to fix Vista/Window 7 when the boot files are missing - rebuild BCD with bcdedit
[http://ubuntuforums.org/showpost.php?p=5726832&postcount=4](http://ubuntuforums.org/showpost.php?p=5726832&postcount=4)
Some advanced BCD rebuild, Vista post #17 on:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

[http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html](http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html)

How to fix Vista/Window 7 when the boot files are missing manual copy  & BCD edit
[http://ubuntuforums.org/showpost.php?p=5726832&postcount=4](http://ubuntuforums.org/showpost.php?p=5726832&postcount=4)

---

### Post by presence1960 on 2011-02-06
> **Quackers said:**
> Ah! Living in the past :-)
Make the system more complicated to stop grub2 doing what it does.  Hmmm.
Not to mention 2 drive systems, where only the first drive is choosable as a boot device - not much use there either, if Ubuntu is on the second drive.

+1

At least in here you won't get /BLOCKED/ for having a different opinion or for responding in kind when someone attacks you first.

---

### Post by AlterMind on 2011-02-06
> **Quackers said:**
> AlterMind, does Ubuntu boot up when selected?
Yes it does.  My concern are:
a) the two Windows menu entries identified by Grub confused me as the 1st pointed at the recovery partition while mentioning 'Vista' (the second named 'Win 7' actually launches Windows boot menu)
b) having to go through two menus to lauch Windows, while I was hoping the Grub install would have 'caught' the Windows 7 menu and have 'undone' these before offering its own menu
Happily enough, Grub-customiser helped in the 'cleanup' of the first menu, but that's only the first/small part of the things I need to do in order to get things as I'd like.

---

### Post by AlterMind on 2011-02-06
> **oldfred said:**
> You should not have to reinstall windows, but moving boot flags & repairing may be required. It is easier with XP. I do not know enough about the details of BCD which in effect replaced boot.ini.

How to fix Vista/Window 7 when the boot files are missing - rebuild BCD with bcdedit
[http://ubuntuforums.org/showpost.php?p=5726832&postcount=4](http://ubuntuforums.org/showpost.php?p=5726832&postcount=4)
Some advanced BCD rebuild, Vista post #17 on:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

[http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html](http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html)

How to fix Vista/Window 7 when the boot files are missing manual copy  & BCD edit
[http://ubuntuforums.org/showpost.php?p=5726832&postcount=4](http://ubuntuforums.org/showpost.php?p=5726832&postcount=4)
Thank you *so much* for the various "how to..." relevant references, I have some stuff to read before i'll play with bits and bytes, flags and BCD's  :-)

---

### Post by AlterMind on 2011-02-06
> **perspectoff said:**
> The solutions I use are outlined at

[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)
and
[http://kubuntuguide.org/Multiple_OS_Installation](http://kubuntuguide.org/Multiple_OS_Installation)
Grub Legacy can chainload the Windows bootloader on the first partition of the second hard drive, for example, by referring to it as (hd1,0)
(Grub Legacy starts counting at 0).
For example, the Grub Legacy menu item (in menu.lst in the boot partition) would merely read:

 title Windows on second hard drive
 root (hd1,0)
 makeactive
 chainloader +1

Easy, yeah?
It sounds easy indeed -- I certainly like the idea of this "independency" too !
Is there a recommended place to install this "tiny" Grub Legacy boot partition ?
I see that my recovery partition is 9GB big but actually ony 7GB are used. Would the 2GB remaining be enough (from shrinking the recovery partition)? That would then be on the first disk.
Thanks for the link to the guide, some *more*, things to read now...  but at least this Community comes with various options and solutions indeed !Also, t

---

### Post by oldfred on 2011-02-06
Legacy grub does not offer any advantages and some disadvantages. I resisted grub2 initially as I have a grub boot partition, but I have to manually maintain it every time a change occurs. Grub2's osprober is very good at finding other bootable systems, but neither grub2 nor old grub will let you boot a windows partition that does not have its boot files.

If you really want to know about grub & grub2 partitions.
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_Partition]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_Partition")
old grub partition
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition]("http://members.iinet.net.au/%7Eherman546/p15.html#How_to_make_a_separate_Grub_Partition")
Grub2
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition_]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition_")

I still install grub2 to USB flash drive partition to loopmount many different ISO's on the flash drive. But that is the only place I do not use the osprober and a full grub2 install.

---

### Post by Quackers on 2011-02-07
> **AlterMind said:**
> Yes it does.  My concern are:
a) the two Windows menu entries identified by Grub confused me as the 1st pointed at the recovery partition while mentioning 'Vista' (the second named 'Win 7' actually launches Windows boot menu)
b) having to go through two menus to lauch Windows, while I was hoping the Grub install would have 'caught' the Windows 7 menu and have 'undone' these before offering its own menu
Happily enough, Grub-customiser helped in the 'cleanup' of the first menu, but that's only the first/small part of the things I need to do in order to get things as I'd like.

Thanks.
The first line of your boot script output is curious to me. That's why I asked the question.
```
=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub
```
In this line it appears that grub is looking for Ubuntu boot files in partition #5 of drive sda. As there isn't a 5th partition on sda, and, in fact, your Ubuntu partition is the fifth partition on sdb, it seems to me that Ubuntu should not be booting. In other words, as it is at the moment, grub should not be able to find your Ubuntu installation because it is looking in the wrong place. 
I'm not sure what's happening there. 
With regard to grub and Vista, it is sometimes the case that grub can mis-name the Vista recovery option and the actual Vista partition. It only seems to happen with Vista, for some reason.

---

### Post by oldfred on 2011-02-07
Just for reference Quackers and others.

Either grub2 or the script identify the drive incorrectly in many cases. I first noticed it with my system as a grub2 in sda said it was booting same drive partition 5. But my install was in sdc5 and it booted just fine. I have only 3 partitions in sda, so it was obvious, but some systems it is not so obvious.

---

### Post by drs305 on 2011-02-07
Yes, it is a frequent occurence. I don't know why the script does this. When I see this - if the system boots I don't worry about it. If it doesn't, I suggest a simple "grub-install /dev/sdX" from a running OS (or with the root directory switch from the LiveCD) just to make sure it's looking to the correct drive.  If it's reporting the correct partition *number* it's almost always just the script misreporting it.

---

### Post by AlterMind on 2011-02-07
> **oldfred said:**
> Legacy grub does not offer any advantages and some disadvantages. I resisted grub2 initially as I have a grub boot partition, but I have to manually maintain it every time a change occurs. Grub2's osprober is very good at finding other bootable systems, but neither grub2 nor old grub will let you boot a windows partition that does not have its boot files.

One serious advantage I see, but please correct me if I'm wrong, is that none of the two issues I report would have appeared, as in such a configuration I could have prevented Windows 7 from creating its own boot menus and I would have manually created the additional boot entries for Ubuntu (and avoiding the Vista recovery partition confusion). So far, unless I'm mistaken, only the grub partition solution offers to chainload all OS's from a single menu, without fearing that forthcoming software installs (Windows/ Ubuntu) will try to grab the detected partitions into a self-managed menu (when it works -- and so far none of them worked, while I don't feel I have such an exotic configuration).  
You may argue that this requires some knowledge but it seems to me that solving it now requires me to know/ read/ understand *much* more before I can proceed with fixing things.  But maybe that's only my perception.

---

### Post by Quackers on 2011-02-07
Thanks oldfred and drs305 for that info. In my travels I have not seen this before, specifically, but it would answer a few Windows booting problems I've seen :-)

Altermind, Windows is making the Windows dual boot menu, by using one set of boot files (/bootmgr /Boot/BCD) in sda2, rather than 2 sets (one on sda2 and one on sdb2). 
I believe this can be remedied, if you wish, by disconnecting the second drive, repairing the Windows boot loader on the first drive with the Windows vista/7 repair disc; then re-connecting the second drive and disconnecting the first drive, then repairing the Windows bootloader on the second drive.
This way you will get 2 sets of Windows boot files (/bootmgr /Boot/BCD), one for each Windows installation, effectively separating the 2 systems.
Then you can re-connect both drives and re-install grub via the live cd.
You should then get a grub menu (after update-grub) with the choice between Windows Vista (which could be wrongly labelled), Windows 7 and Ubuntu.

---

### Post by AlterMind on 2011-02-12
Hi all,

First of all thanks for your different inputs from all. It's not that I've abandoned or yet solved my situation, it's simply that my work has kept me away from it, and that I needed to review the various reference doc or links you provided, and mitigate some of the confusion that arose.

To start, many of the "repair links" were referring to using Vista or Win7 repair CD but neither of them would show me anything in the "please select an OS to repair from the list" dialog, which puzzled me a lot. Also, many "command line" methods were using quite different instructions, including (in no consistent order): diskpart, bcdedit, bootsec, bootrec, and manual file copies of all kind :-)  I sort of need (and like) to understand what I do before I start, especially if I may put some important partition at risk (Vista).

Curiously, after I've run diskpart > list volume (and btw understood what BIOS boot parameter setting were useful or having no apparent effect), and inverted a couple of time the HDD boot sequence, now BOTH Vista and Win7 recovery CD's DO list both of the Windows OS to be selected for repair. Seems like a step forward. Btw Grub2 is still my boot manager, so far, with the nested Grub/Windows boot menus.

As Windows is pretty unclear about *what* it exactly will do during its repair process, but as I *assume* it will actually try to *install it's own OS as directly bootable from the C: drive where it is shown to be present*, let me ask a couple of questions:
1) currently, Vista is seen on C: and Win7 on D: (or vice versa if I invert the disk boot sequence in BIOS). Do I need to choose the boot sequence to have each time the Windows to repair seen as C: before repair ?
2) if I supposedly repair both (and assumingn that I inverted the disk boot sequence in BIOS between), can I expect that the boot disk sequence chosen in BIOS will actually determine the Windows OS that would be loaded straight ahead ? Or will each repair attempt actually create a dual boot menu showing Vista as C: or Win7 as C: depending on which disk is selected in the BIOS as first disk to try to boot from ?
3) once the dual repair will have been accomplished, I assume that Grub2 will no more be available and that I'll need to use the Ubuntu LiveCD ? Will I then need to reinstall Ubuntu to its hopefully still existing partition or how can I tell Ubuntu to install its Grub2 loader WITHOUT re-creating the nested menus, but rather creating a 'triple entries' boot menu ?

I hope what I'm trying to do isn't all too confusing -- I got my load of confusion yet so far, but still hanging on !  Also, do you need me to republish some config info ?
Thanks for the precious advice :-)

---

### Post by oldfred on 2011-02-12
I though windows also offered a find other windows systems to boot. Otherwise which ever you repair may move the boot files from the other and set up dual boot from within windows. You could copy files, fix and then return files. Never done it so I do not know for sure.

Quacker's suggestion of disconnecting drives & repairing would definitely prevent windows from seeing the other drive, but both may then they are drive 0.

The files windows moves are 
/bootmgr /Boot/BCD 

The BCD has the details of where windows is and what to boot.
How to fix Vista/Window 7 when the boot files are missing - rebuild BCD with bcdedit
[http://ubuntuforums.org/showpost.php?p=5726832&postcount=4](http://ubuntuforums.org/showpost.php?p=5726832&postcount=4)
Some advanced BCD rebuild, Vista post #17 on:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

---

