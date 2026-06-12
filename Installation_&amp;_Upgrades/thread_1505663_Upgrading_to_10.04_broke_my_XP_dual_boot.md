---
title: "Upgrading to 10.04 broke my XP dual boot"
date: 2010-06-09
forum: Installation &amp; Upgrades
---

### Post by rtrinkner on 2010-06-09
Hello,

My laptop happily dual-booted Ubuntu 9 as well as Windows XP until I upgraded to Ubuntu 10.04.  Now Grub launches Ubuntu just fine, but leaves me with a black screen and blinking cursor in the top left corner when I try to launch XP.  I can see that my Windows data files are fine, because I can access them from Ubuntu.

I've read on this forum that a user named "barkes"  had success fixing this problem by downloading a program called "checkdisk"  from the Ubuntu software center.  I can't find such a program when I search from my machine.

I'd greatly appreciate any help in fixing this situation.

Below, I've pasted the"solution" text from barkes's thread:

Thanks,

Richard

--------------------------------------------

                                  **Re: XP will not boot after installing 10.04**             
                                                                oldfred, Its  all good now!  

Per your suggestions I chose the "Rebuild BS" option inside checkdisk.  Checkdisk  calculated what the boot sector should be and showed where the current  and calculated were different.  I then chose the "write" option in checkdisk to make the change.

Upon reboot into windows, XP did its own disk checking and then all was  well.

-----------------

Here is what I did to solve my problem.

1. got checkdisk from Ubuntu Software  Center
2. sudo checkdisk
3. enter password
4. inside checkdisk select [CREATE]
5. then select the drive that has your windows on it and [PROCEED]
6. then [CONTINUE]
7. then [INTEL]
8. select Advanced
9. select your windows partition and then [BOOT].  If you have a problem  it will tell you here.  See my previous post in this thread to see what  the output looked like for my system.
10. I chose [Rebuild BS] at this point.
11. This will calculate what your Boot sector should look like
12. If you trust the results, select [write] to write the calculated  boot sector to your drive.

Thanks oldfred and the author of another post that suggested using checkdisk.

---

### Post by darkod on 2010-06-09
Boot your ubuntu and you should be able to install testdisk with:

sudo apt-get install testdisk

You can run it with:

sudo testdisk

The instructions to remove grub2 from the windows partition with testdisk are here:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

If you don't know which one is your XP partition, ask first (you can see it in the grub menu it will say like "on /dev/sda1").

---

### Post by rtrinkner on 2010-06-09
Thanks.  So did barkes mean "testdisk"  instead of "checkdisk?" 

Also, if I remove Grub 2 from my XP partition, will I no longer be able to dual boot Ubuntu?

Sorry to be a newb --

Richard

---

### Post by darkod on 2010-06-09
You are booting from grub2 on your hdd MBR, so removing the grub2 which is on the XP partition by mistake will not affect the dual boot.

There might be another procedure with a program named checkdisk, I know of this one with testdisk.

---

### Post by rtrinkner on 2010-06-09
Well, rats.  I installed testdisk and followed barkes's instructions.  I had the same error message, indicating that

Boot Sector
Warning: Incorrect number of heads/cylinder 240 (NTFS) != 255 (HD)

So I followed barkes's instructions to rebuild the BS using testdisk.

This routine completed successfully, and testdisk now reports no errors with the NTFS boot sector.

However, the boot problem remains:  when choosing to boot into XP, I receive a blinking cursor, and no activity on my laptop's hard drive access light.

Darkod, thanks very much for the suggestions.  Now when I try testdisk per your instructions, I do not receive a "BackupBS"  option.

Must I scrounge around for a Windows installation disk?  Or is there a fix I can do from within Ubuntu?  I don't have immediate access to this laptop's XP disk, because I'm a teacher home for the summer, and the IT department keeps the disks at work.

Thanks again!

---

### Post by rtrinkner on 2010-06-09
I found on SourceForge.net a reference to a problem with two boot folders being created on the NTFS partition:  one named Boot and one named boot.

How do I use linux to view the contetnts of the NTFS partition?  I can accress the contents of my Windows C: drive already through Ubuntu's file explorer, but there are no "boot"  folders of any kind here.  They must be in a boot partition that is different from the commonplace C drive.

The sourceforge.net recommendations are at [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

Thanks again,

Richard

---

### Post by darkod on 2010-06-09
For more details you would need to download and run the boot info script and post the content of the results file, as explained here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by darkod on 2010-06-09
> **rtrinkner said:**
> I found on SourceForge.net a reference to a problem with two boot folders being created on the NTFS partition:  one named Boot and one named boot.

How do I use linux to view the contetnts of the NTFS partition?  I can accress the contents of my Windows C: drive already through Ubuntu's file explorer, but there are no "boot"  folders of any kind here.  They must be in a boot partition that is different from the commonplace C drive.

The sourceforge.net recommendations are at [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

Thanks again,

Richard

The 'boot' folder started to be used by MS from Vista. You don't have it on XP. However, if you have any boot or Boot folder in C:, it shouldn't be there.

---

### Post by rtrinkner on 2010-06-09
Thanks very much for your help, Darkod.  Below, is the output from your analysis  program.  By the way, I notice that you're in Spain.  I lived in Las Palmas de Gran Canaria for two years.  Mil gracias!

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 101513585 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   101,177,369   101,177,307   7 HPFS/NTFS
/dev/sda2         101,177,370   156,296,384    55,119,015   5 Extended
/dev/sda5         101,177,433   153,918,764    52,741,332  83 Linux
/dev/sda6         153,918,828   156,296,384     2,377,557  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        445C99F10A043A9C                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        324e3c76-8f40-4ed1-b405-e3e3bcfbffef   ext4                                     
/dev/sda6        70905f0b-1511-41ae-a9e7-62ef45918d47   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda1        /media/windows           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer 

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 324e3c76-8f40-4ed1-b405-e3e3bcfbffef
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 324e3c76-8f40-4ed1-b405-e3e3bcfbffef
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
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 324e3c76-8f40-4ed1-b405-e3e3bcfbffef
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=324e3c76-8f40-4ed1-b405-e3e3bcfbffef ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 324e3c76-8f40-4ed1-b405-e3e3bcfbffef
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=324e3c76-8f40-4ed1-b405-e3e3bcfbffef ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 324e3c76-8f40-4ed1-b405-e3e3bcfbffef
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=324e3c76-8f40-4ed1-b405-e3e3bcfbffef ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 324e3c76-8f40-4ed1-b405-e3e3bcfbffef
    echo    'Loading Linux 2.6.31-20-generic ...'
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=324e3c76-8f40-4ed1-b405-e3e3bcfbffef ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 324e3c76-8f40-4ed1-b405-e3e3bcfbffef
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 324e3c76-8f40-4ed1-b405-e3e3bcfbffef
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 445c99f10a043a9c
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=324e3c76-8f40-4ed1-b405-e3e3bcfbffef /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=70905f0b-1511-41ae-a9e7-62ef45918d47 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda1 /media/windows ntfs defaults,uid=1000,gid=1000 0 0


=================== sda5: Location of files loaded by Grub: ===================


  51.9GB: boot/grub/core.img
  54.7GB: boot/grub/grub.cfg
  53.5GB: boot/initrd.img-2.6.31-20-generic
  67.8GB: boot/initrd.img-2.6.32-22-generic
  52.8GB: boot/vmlinuz-2.6.31-20-generic
  53.1GB: boot/vmlinuz-2.6.32-22-generic
  67.8GB: initrd.img
  53.5GB: initrd.img.old
  53.1GB: vmlinuz
  52.8GB: vmlinuz.old

---

### Post by oldfred on 2010-06-09
Testdisk has another alternative of rebuild boot sector. I would try that, otherwise it is find a XP disk to run windows repairs.

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

---

### Post by confused1 on 2010-06-10
I lost my ability to dual boot into XP after upgrading from Koala 9.10 to Lucid 10.04. Thanks darkod the testdisk solution worked just right for me.:p

---

### Post by rtrinkner on 2010-06-10
Sadly, I tried using ms-sys to fix the MBR of the XP partition, and that rendered my computer unbootable.   It just blinked a cursor at me.

I took the laptop to my company's IT department who replaced the HDD with a new XP-imaged HDD, and gave me the original HDD in case I wanted to try to salvage any data.  

I'll try to use a Ubuntu LiveCD to see if I can mount the old XP partition and copy files to a USB drive.

Thanks for all your  help, though.

Lessons I've learned:

1.  Avoid dual-boot machines.  I liked Linux just fine, but would only return to it if I could dedicate a machine to it.

2.  If you must use a dual boot machine, avoid upgrading GRUB if your current version is working just fine.

---

### Post by wilee-nilee on 2010-06-10
> **rtrinkner said:**
> Sadly, I tried using ms-sys to fix the MBR of the XP partition, and that rendered my computer unbootable.   It just blinked a cursor at me.

I took the laptop to my company's IT department who replaced the HDD with a new XP-imaged HDD, and gave me the original HDD in case I wanted to try to salvage any data.  

I'll try to use a Ubuntu LiveCD to see if I can mount the old XP partition and copy files to a USB drive.

Thanks for all your  help, though.

Lessons I've learned:

1.  Avoid dual-boot machines.  I liked Linux just fine, but would only return to it if I could dedicate a machine to it.

2.  If you must use a dual boot machine, avoid upgrading GRUB if your current version is working just fine.

Just so you know these rules only apply to you. You just made a upgrade mistake, we have all done something similar by acting without knowing. This could have been avoided by just having asked some questions on the forum, or even reading threads on the forum, there are like at all times a similar grub install problem on the main access pages at all times. Basically due to people just not knowing what there doing, which isn't a bad thing, you just have to reason through what you doing.

---

### Post by rtrinkner on 2010-06-11
No doubt, I made a mistake somewhere along the upgrade line.  Absolutely, mea culpa.

Still, I'm a techy person (former programmer, years in IT), and all I thought I was doing was clicking "next" during the upgrade process. 

As much as I hate to say it, there's something to be said for the legion of paid Microsoft testers.

I do look forward to returning to Linux when more of the wrinkles are ironed out. I'm a huge fan of the open source idea.

Thanks to everybody who tried to help --

Richard

---

