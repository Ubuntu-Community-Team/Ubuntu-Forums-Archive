---
title: "Multiboot Ubuntu, Win7, Windows Vista, Windows Server 2003,OpenSolaris and Solaris 10"
date: 2010-07-12
forum: Installation &amp; Upgrades
---

### Post by MAFoElffen on 2010-07-12
Help!
(I know, you;re thinking I'm crazy, but I figured I wanted to run everything native for performance and development- but do testing within virtual machines)

Yes, I WAS running everything multiboot fine using (there is a later "until"):

Win7 Professional 64bit, Windows Vista Home Premium 64bit, Windows Small Business Server 2003, Ubuntu 9,10 64bit, OpenSolaris 64bit and Solaris 10 64bit

...on an:
ASUS8N32-SLI Deluxe Gaming Edition, AMD64 FX/60, 4 GB DDR1 PC3200 Premium RAM, onboard nVidia Nforce4, two GTX GeForce 6800GT Extreme SLI vidoeo cards (bridged), Creative Labs XFi Xtreme Ganer sound card, 500 GB IDE drive, 1 TB SATA drive and 350 GB SATA drive...

The Drives were set up as:
  primary boot:
    1 TB SATA (C:, sdc1)- (..,1)- WIN7, (...5) Ubuntu, (,,.6) Linux Swap, with the Grub2 boot menu from Ubuntu.
 second drive: 
    350 GB SATA (D:, sdb1)- (..,1) Windows Vista, (..,2) OpenSolaris, with the Grub2 Menu from OpenSolaris.
  third drive: 
    500 IDE (E:. sda1)-  (..,1) Windows Server 2003, Solaris 10, with the Grub2 boot menu from Solaris 10.

UNTILl I was having problems installing ALSA Sound Drivers in Ubuntu 9.10.  During that process, I opt'ed to Upgade to Ubuntu 10.05 beta through the Upgrade Manager(!)  What happened was during the upgrade it changed the Grub2 Menu... and the whole Booting Process all all drives instead of the Primary 1TB Drive that is was installed on.  What it did was it installed the Grub2 boot and menu from Ubuntu to ALL the drives instead of just to the primary drive. This over-wrote the MBR of all the drives!  From that point on, the only OS that boots is Ubuntu.  I can still access that data on all drives.  As a Beta Tester, I reported the problem, but never received resolution nor help correcting it.

I tried various things to resolve it.  I finally figured that the OS'es that were mostly setup and the installed with the most applications were Ubuntu and Win7.  I repartitioned, formated and reinstalled Windows Vista and OpenSolaris (smp164) on my 350 MB drive with the boot menu from OpenSolaris.

Then I upgraded Ubuntu from 10.04 beta 64bit to the 10.04 64bit (released) through the Upgrade Manager by just checking for updates... During the update process, it blasted the MBR's and subsequent Boot Menu's on the other drives again.  ...And I never have been able to get Win7 to boot back up yet on the drive Ubuntu is on.  I also haven't been able to get Windows Server to boot up, but that OS is now not needed on this.

Help!

---

### Post by MAFoElffen on 2010-07-12
I've used the Win7 and Vista Install disks to try to use "repair" (which is what both WIN Rescue disks use) to no avail.  It says there is nothing wrong... as it see's an MBR, but it is not the WIN MBR- it is Grub2.  Seems it overwrote the MBR's of those partitions.

I tried using a "Super Grub" Disk (v0.9799)... but it also fails.

---

### Post by oldfred on 2010-07-12
I know this will be a lot of info with all those systems, but this shows where everything is installed. Be sure to use the code tags or it will not be easy to review.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by MAFoElffen on 2010-07-12
I uninstalled Solaris 10 (from a mirror I had of this drive) before I got your post. I ran the script. Here is the results:
```
               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 1429149036 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda2 and 
                       looks at sector 157292465 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #2 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 1429144108 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc2 and 
                       looks at sector 1429147500 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   157,292,414   157,292,352   7 HPFS/NTFS
/dev/sda2    *    157,292,415   367,007,614   209,715,200  bf Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048 1,428,837,164 1,428,835,117   7 HPFS/NTFS
/dev/sdb2       1,428,837,165 1,953,520,064   524,682,900   5 Extended
/dev/sdb5       1,428,837,228 1,941,471,314   512,634,087  83 Linux
/dev/sdb6       1,941,471,378 1,953,520,064    12,048,687  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63    20,980,889    20,980,827   7 HPFS/NTFS
/dev/sdc2          20,980,890   976,768,383   955,787,494   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        E85C16665C163034                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        40E0BF86E0BF80A8                       ntfs       Mikes_1TB                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        8024e731-87f9-4956-aee1-5382947413ce   ext4                                     
/dev/sdb6        e65812a7-8fcc-45f0-9abb-6cfef5c1d0f4   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        F808ABFB08ABB6D2                       ntfs       SYS                           
/dev/sdc2        FA78A3B378A36CD7                       ntfs       DATA                          
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
search --no-floppy --fs-uuid --set 8024e731-87f9-4956-aee1-5382947413ce
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
search --no-floppy --fs-uuid --set 8024e731-87f9-4956-aee1-5382947413ce
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8024e731-87f9-4956-aee1-5382947413ce
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=8024e731-87f9-4956-aee1-5382947413ce ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8024e731-87f9-4956-aee1-5382947413ce
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=8024e731-87f9-4956-aee1-5382947413ce ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8024e731-87f9-4956-aee1-5382947413ce
    linux    /boot/vmlinuz-2.6.32-19-generic root=UUID=8024e731-87f9-4956-aee1-5382947413ce ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8024e731-87f9-4956-aee1-5382947413ce
    echo    'Loading Linux 2.6.32-19-generic ...'
    linux    /boot/vmlinuz-2.6.32-19-generic root=UUID=8024e731-87f9-4956-aee1-5382947413ce ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-18-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8024e731-87f9-4956-aee1-5382947413ce
    linux    /boot/vmlinuz-2.6.32-18-generic root=UUID=8024e731-87f9-4956-aee1-5382947413ce ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-18-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-18-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8024e731-87f9-4956-aee1-5382947413ce
    echo    'Loading Linux 2.6.32-18-generic ...'
    linux    /boot/vmlinuz-2.6.32-18-generic root=UUID=8024e731-87f9-4956-aee1-5382947413ce ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-18-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8024e731-87f9-4956-aee1-5382947413ce
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=8024e731-87f9-4956-aee1-5382947413ce ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-20-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8024e731-87f9-4956-aee1-5382947413ce
    echo    'Loading Linux 2.6.31-20-generic ...'
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=8024e731-87f9-4956-aee1-5382947413ce ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-20-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8024e731-87f9-4956-aee1-5382947413ce
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 8024e731-87f9-4956-aee1-5382947413ce
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 40e0bf86e0bf80a8
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=8024e731-87f9-4956-aee1-5382947413ce /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=e65812a7-8fcc-45f0-9abb-6cfef5c1d0f4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 731.7GB: boot/grub/core.img
 742.5GB: boot/grub/grub.cfg
 732.8GB: boot/initrd.img-2.6.31-20-generic
 734.9GB: boot/initrd.img-2.6.32-18-generic
 732.7GB: boot/initrd.img-2.6.32-19-generic
 732.8GB: boot/initrd.img-2.6.32-23-generic
 732.6GB: boot/vmlinuz-2.6.31-20-generic
 734.8GB: boot/vmlinuz-2.6.32-18-generic
 735.3GB: boot/vmlinuz-2.6.32-19-generic
 737.3GB: boot/vmlinuz-2.6.32-23-generic
 732.8GB: initrd.img
 732.7GB: initrd.img.old
 737.3GB: vmlinuz
 735.3GB: vmlinuz.old

================================ sdc1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows Server 2003 for Small Business Server" /noexecute=optout /fastdetect 
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 
```

---

### Post by oldfred on 2010-07-12
This usually works for windows, I do not know about the other systems. Do they have part of their boot loader in the boot slice/PBR/boot sector?

Since you already tried doing repairs you may have overwriten the backup.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

When the instructions said all drives they meant sda, sdb etc not partitions sda1, sda2 sdb1 etc. You overwrote the windows boot sector in the windows partition. With multiple boot loaders in every drive you also should not have installed to those drives. It did give a choice.

This is what the instructions say:
If you're unsure which drive is designated as boot drive by your BIOS, it is often a good idea to install GRUB to all of them.        

It also says:
Note: It is possible to install GRUB to partition boot records as well. However, this forces GRUB to use the blocklist mechanism, which makes it less reliable, and therefore is not recommended.

It then presents a check box with all drives and partitions. So everyone (And I think it its everyone) checks all the boxes. Only drives sda, sdb, etc should be checked. Not partitions sda1, sda2, sdb1, etc. It would have been better to present just drives after the first statement or not even presented partitions as the few that would want that can run that later.

Since it is confusing for the average user a bug report was filed:
Kansasnoob bug report:
[http://art.ubuntuforums.org/showthread.php?t=1475385](http://art.ubuntuforums.org/showthread.php?t=1475385)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)
[https://launchpad.net/ubuntu/+milestone/ubuntu-10.04.1](https://launchpad.net/ubuntu/+milestone/ubuntu-10.04.1)

---

### Post by MAFoElffen on 2010-07-12
For tranlation perposes to this script-
sda1 is Vista
sda2 is OpenSolaris
sdb1 is WIN7
sdb5 is Ubuntu
sdc1 is WinServer 2003
sdc2 is just Data with a NTFS file system.

And if I understand this results correctly-

Drive sdb is the only drive that has a partion 5, but all the drive's MBR's where overwritten (as a mirrored result) in error with Grub2 looking for /boot/grub in Partition 5.

Even though all the drives have Grub2 in the MBR: 
sda1 has a Grub2 boot sector with incorrect pointers?
sda2 has a Grub boot sector and cannot recognize the file system
sdb1 has a Grub2 boot sector with incorrect pointers?
sdb5 is correct
sdc1 is confused
sdc2 is a Data NTFS (not set as primary) but for some reason has a boot sector of Grub2 were it souldn't have a boot sector at all(???)

Okay... How do I go about correcting all this?  More important, what caused this so that Ubuntu 10.04 doesn't do this to others?  (This didn't happen with Koala...)

---

### Post by MAFoElffen on 2010-07-12
I can't remember what I did during the beta upgrade of 10.04.  But yesterday with the "update" to the release version I **only** had the drive (and not partitions) that contained Ubuntu selected (only box selected), but it again overwrote all drives.

What do I do to resolve all this (beyond a fresh install of all these OS'es again)?

It may be easier to do a fresh install but it would take weeks to get it all done with all the OS'es, additional device drivers, applications, tweaks, and reloading all my source and data.  Loading over my little ADHOC network and from CD'es and DVD'es ...around 2TB takes awhile any way you look at it.

---

### Post by MAFoElffen on 2010-07-12
Okay... I'll wait until tomorrow.  I'll hold off on trying other changes and repairs on my own until then.

If I don't get some other advice... I guess my plan in absence of someone's advice will be to repartition, reformat and reinstall Windows Vista and OpenSolaris on the 350GB drive (sda).  I'll get my data off sdc2 before doing anything with sdc- with plans to repartition, reformat and install Solaris 10 on sdc1, with sdc2 as NTFS DATA.  With drive sdb, I'll try to repair the sdb1 partion to get Win7 to boot.

The OpenSolaris partition could probably be repaired if I could figure out how to rebuild the MBR to point back to the boot sector which points to partition 2... I think that might work, but I'm not sure.

---

### Post by oldfred on 2010-07-12
I do not know if the testdisk process will work on the Solaris partitions. It does work on windows and linux.

Grub installed to a data partition makes no difference, it is using space otherwise not used.

There should be a way to reinstall all your boot loaders, I only know windows and Ubuntu. You need to see if OpenSolaris has a procedure to reinstall the boot loader. I would bet it does.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

The boot script or grub2 miss report drive so all the MBR that say same drive partition 5 will probalby boot sdb5. The script was set up to parse windows & linux partitions for boot files. It did not include Unix systems like OpenSolaris, so it does not tell anything about it.

---

### Post by MAFoElffen on 2010-07-12
I ran testdisk.  It did find the that boot sector of Win7 was different than it's  backup, so I copied over the backup.

During the process, I noted that the shutdown icon disappeared from the top title bar of Ubuntu.  Minor inconvenience which I got around.  When I rebooted, the video did not initialize during the boot nor during the grub "Menu" boot.  It got past the grub "Menu" timeout.  I heard the initial Ubuntu boot anthem and the video initialized at the login screen...  This has been another intermittent ongoing problem with 10.04 and the nVidia drivers(?).  It only does this sometimes after exiting Ubuntu 10.04.

I shutdown.  I turned off the power supply and display (Hannspree Xm, 1440x900), unplugged the video cable and replugged (sometimes resolved)- no difference.  I then disconnected the other drives (sometimes resolved)- no difference.

Will keep trying so I can test if TestDisk worked.  Will get back...

---

### Post by oldfred on 2010-07-12
I know nothing about openSolaris but the first link in google gave me this:

Thread: reinstall grub?             
[http://opensolaris.org/jive/thread.jspa?messageID=465862](http://opensolaris.org/jive/thread.jspa?messageID=465862)

[http://blogs.sun.com/avinashjoshi/entry/mount_opensolaris_zfs_partition_and](http://blogs.sun.com/avinashjoshi/entry/mount_opensolaris_zfs_partition_and)

I am sure there are more or more updated versions available.

---

### Post by MAFoElffen on 2010-07-13
:p Initial Success so far!!!

Thank you so very much! **TestDisk** successfully repaired my install of Win7,  It boots up from the Grub Menu of the 1TB drive (sdb),  What TestDisk found as backup of the boot sector pointed to Windows Bootmgr.  So it now goes from Grub to Windows' BootMgr to Win7... But it boots.

Sorry for the delay in getting back,,, Once Win7 booted, I had 3 months of updates to download and install.  (Besides a few "errands" to do for my fiance.)  This working from within Ubuntu has just confirmed my past opinion that Ubuntu and the Ubuntu Community is something to treasure and stay with.  Ubuntu is (handsdown) the most openly "community" supported system I have found, for a very "solid" and "dependable" operating system.

So now my plans for recovery has just changed, thanks to you:
* Basically I'll use the Current Ubuntu genaerated GRUB Menu to multiboot all my other OS'es.  Where as, before I had them as Isolated drives (as a different- separate multiboot Grub Menu on each drive for the Os'es on that particular drive...)
- My next step will be to backup the current Grub,cfg. (which is working for my main two OS'es)
- Run Ubuntu "Recovery Mode" the find the second 350GB drive and add Vista back to the main Grub Menu on my primary drive (the 1TB).
-  Use TestDisk to recover my installation of Vista.
-  Use my Virtual installs of OpenSolaris and Solaris 10 in VirtualBox under Vista to copy the lines from their Grub menus, to add them to the "custom section" of the Main Grub Menu to copy and modify to...
- Point a Main Grub Menu entriy to the install of OpenSolaris in sda2 to see if it comes up...

Yes... The Ubuntu Grub source scripts and it's "findos" doesn't seem to recognize Solaris or OpenSolaris... That may become an adventure on it's own, but we'll see.  My install of OpenSolaris was a little extensive- with applications and "other" device drivers specific to my equipment.  My install of Solaris 10 was not as tweaked, as I didn't "live" there much except for some work in Sun Studio.  I didn't have enough time spent in it to tweak it to my own flavor and likes.  A fresh install would get me close to where I was with it.  That's why I figure I could put that back onto my third drive "in place of" Windows Server... Which I'm thinking of just dumping all together.

---

### Post by MAFoElffen on 2010-07-13
> **oldfred said:**
> I know nothing about openSolaris but the first link in google gave me this:

Thread: reinstall grub?             
[http://opensolaris.org/jive/thread.jspa?messageID=465862](http://opensolaris.org/jive/thread.jspa?messageID=465862)

[http://blogs.sun.com/avinashjoshi/entry/mount_opensolaris_zfs_partition_and](http://blogs.sun.com/avinashjoshi/entry/mount_opensolaris_zfs_partition_and)

I am sure there are more or more updated versions available.

Will look at these this afternoon... Thanks.

---

### Post by cr4321 on 2010-07-13
Guys, the subject discussed above was way beyond me, but that complexity made me wonder if it could work out in a more simplistic way. I am just thinking aloud, so, if I am wrong - I would like to be corrected. I do not have the skills nor the resource to try it out practically.

Now as I understand, there are 3 disks and let us say 3 OS from MS and others from the Linux world.

First, I would plan to install the MS OS's (Win-7. XP and Vista) in each disk's Primary Partitions since these are very non tolerant OS's.

Suppose I have only one disk powered at a time and connected in their respective slots (P & S, Slave and Master). and install MS in the primary partion. Then within partitions in the Extended drive I will install all the Linux OS - with a single SWAP partition. I believe about 10 of them can be installed? I will have grub installed boot menu in the Primary partion of each drive.

So now, I have 3 drives -each of which is bootable into multiple OS - with the option to choose which drive/OS to boot from the BIOS setting.

Then I power up all the drives and all 3 drives are bootable - but only one can be chosen thru BIOS setting.

Can I then install grub into a pendrive and update it to capture all the OS's in the 3 disks? Then if I choose to boot from USB, will I be able to choose any of the OS from any of the drives?

I does seem as if it can work - though, I am sure, it will require some effort to do it practically!!

Interesting thought though.. Do you guys think it is workable? Would like to know.. Thanks.

cr

---

### Post by oldfred on 2010-07-13
If you boot grub you can from that boot just about anything. Sometimes chainloading to another system is required i.e. windows and sometimes you can directly boot another system

For booting Solaris form Grub I would just install Solaris's grub to the MBR of that drive and add a chainload entry from grub to that drive. I chainload from my main grub in sdc/sdc5 to other grubs in sda or sdb. Drive order seems to change somewhat as my chainload to sda is hd1 not hd0 as I would expect but sdc was boot drive so it became hd0.

When booting from sdc these entries work. (will be different if you boot sda or sdb.

menuentry "Lucid Lynx on sda Chainboot" {
set root=(hd1)
chainloader +1
}

menuentry "10.04  on sdb gpt Chainboot" {
set root=(hd2)
chainloader +1

---

### Post by MAFoElffen on 2010-07-13
Okay... I made a backup of the grub.cfg.  Then I used "testdisk" to repair my installation of Vista.  I updated the grub menu using "update-grub". 

Note: "find-os" still does not see OpenSolaris.  It also is confused with Windows Server, as it tries to ID it as Win7 and the script adds a line in the menu as Windows 7 on sdc1. (Which I know is really Windows Small Business Server 2003.)

Of course Ubuntu's File Browser does not recognize Solaris ZFS file systems.  I'm going to first bring up one of my VirtualBox instances of OpenSolaris to look at the grub menu there and see if I can add those entries to "/etc/grub.d/40_custom"... then use "update-grub" to add those entries.

Tryi to use "testdisk" on this partition?  TestDisk gets a little scary while try to look at a Solaris partion!  If you select Sun (instead of Intel) , it can't find anyhting.  This sort of tells me that that screen is more picking the hardware platform that it is running on.  If you select "Intel" then the drive, it see's and ID's the Solaris partion as the second partion. Once I selected that partition, Instead of analyzing the partion (as it did for the NTFS partition), it went directly to a screen asking me to select a file system from 20+ and then asked if I wanted to change the partion to one of those types!  **I backed out of there.**  

Since Ubuntu generally doesn't recognize Solaris, OpenSolaris, ZFS file systems and Solaris partitions- I highly suspect that the data within that partition is still safe and intact.

---

### Post by MAFoElffen on 2010-07-13
> **cr4321 said:**
> Now as I understand, there are 3 disks and let us say 3 OS from MS and others from the Linux world.
...
First, I would plan to install the MS OS's (Win-7. XP and Vista) in each disk's Primary Partitions since these are very non tolerant OS's.

Suppose I have only one disk powered at a time and connected in their respective slots (P & S, Slave and Master). and install MS in the primary partion. Then within partitions in the Extended drive I will install all the Linux OS - with a single SWAP partition. I believe about 10 of them can be installed? I will have grub installed boot menu in the Primary partion of each drive.

So now, I have 3 drives -each of which is bootable into multiple OS - with the option to choose which drive/OS to boot from the BIOS setting.

Then I power up all the drives and all 3 drives are bootable - but only one can be chosen thru BIOS setting.

Can I then install grub into a pendrive and update it to capture all the OS's in the 3 disks? Then if I choose to boot from USB, will I be able to choose any of the OS from any of the drives?
Yes.  What you described in the first part of your post is pretty much how I had my computer setup.

Windows OS'es like to be in the primary partitions, so I installed my Micro$oft OS'es in the first partitions of my drives.  That is why I installed Ubuntu, OpenSolaris and Solaris on subsequent partions on their respective drives.  OpenSolaris and Solaris do not like to be on the same drive(!), so that's why I installed them on different drives.  With OpenSolaris, I can share data between ZFS, NTFS and FAT32 data types.

For a long time I would use a BIOS popup (F8 on mine during BOOT) during POST to BOOT to various drives.  Since the POST on my computer is a little fast, it was a pain, skipping over that part in my post before I could react.

When you install Ubuntu, OpenSolaris and Solaris 10... each one's install wants to search that drive (or drives) and create it's own GRUB Menu to Boot from.  That is another reason I installed on different drives. When I originally setup these drives, I had the other drives disconnected during their installs.  This was okay, as if also adds special entriies that where specific to my hardware and installion.  (Which automatically added what I  would have had to research.)

Although having to recover from a glich which corrupted what I had, now I'm just simplifying my life by building a Grub menu to multiboot all my OS'es from one menu.

In your question... Yes, that Grub Menu could exist wherever "you" want to boot from.

---

### Post by MAFoElffen on 2010-07-13
Well... I checked out your links for rebuilding the Grub Menu for Open Solaris.  I could do that, if I disconnect the other drives before I do it- Then reconnect and add those entries to my main Grub Menu.

This is a generic OpenSolaris 32bit Grub boot sequence running under VirtualBox... (which would be installed to the root directly a of a single primary drive.
```
findroot (pool_rpool,0,a)
bootfs rpool/ROOT/opensolaris
splashimage /boot/solaris.xpm
foreground d25f00
background 115d93
kernel$ /platform/i86pc/kernel/$ISADIR/unix -B $ZFS-BOOTS, console=gr
module$ /platform/i86pc/$ISADIR/boot_archive
```I think I need to boot under the OpenSolaris Live disk to mount my OpenSolaris partition and read it's grub.conf (which is aliased as menu.lst) and see exactly what it says.  On difference is that I'm running 64bit.  

I'm thinking I may have to load ZFS support in Grub for the specific drive, which is also referenced differently under Solaris (Ex:c[FONT=tahoma,arial,helvetica,sans-serif]xxxxx)...[/FONT][FONT=tahoma,arial,helvetica,sans-serif]  I really don't want to  lose any settings and such that might be in the current grub.conf.   Remember, I have a lot of out-of-the-ordinary tuned hardware that I had to  define and specify myself. (Video, Sound and NIC devices)[/FONT]
[FONT=tahoma,arial,helvetica,sans-serif] 
If I get lost, I may have to ask about it over at the OpenSolaris Dev Board.  I'm running a dev version (snv_134 64bit) of OpenSolaris as the "current as of 3 months ago" release had xorg problems with bridged SLI's... (I have this week to catchup and get back on track with some things.)
[/FONT]

---

### Post by oldfred on 2010-07-13
I still think a chainboot entry would be the easiest way to solve the problem.

---

### Post by MAFoElffen on 2010-07-13
I think I'm on the right track with this:
[http://praveen.kumar.in/2010/02/20/chainloading-opensolaris-from-grub-2/](http://praveen.kumar.in/2010/02/20/chainloading-opensolaris-from-grub-2/)
...but it still won't load.  I think I might have to Boot up on the OpenSolaris snv_134 64bit LiveCD, mount my OpenSolis ZFS volume, then reinstall Grub to it.  Then retry.

---

### Post by MAFoElffen on 2010-07-14
I had tried that wih no sussess. Then I tried the entires above. Still had no luck.  

I tried to mount the ZFS file system from both an OpenSolaris and Solaris 10 LiveCD disks and failed](*,)
...then I started up GPart- And it couldn't read the data within the partition.  It was blasted.  I deleted the partition and reinstalled OpenSolaris.  I could not load OpenSolaris "Natively" from Grub2- but there was some discussion over at the Sun boards that this was a past bug with OpenSolaris. So I Called OpenSolaris'es Grub from Ubuntu's Grub2 menu by chainloading it (in etc/grub.d/40_custom) with:
```
menuentry "OpenSolaris 2010.03 snv_134 64bit" {
    set root='(hd1,2)'
    chainloader +1

```Success on all 4 so far.  Tomorrow I'll reinstall Solaris 10.

---

### Post by MAFoElffen on 2010-07-16
I uninstalled Windows Small Business Server 2003.  Go through this process, I am confident that I could have repaired it with testdisk and tried to brind it it- but I don't test with it anymore and it has been dormant for awhile anyway.

Another decision to this was that Ubuntu 10.04'es Grub2 "findos" operating system ID was really confused by this operating system.  It couldn't decide whether this was Windows 7, XP or NT.  This was very curious because the Grub2 files of Ubuntu 9.10 ID'ed it correctly and had no problems with it.

   The question this raises now is: [COLOR=Magenta]***Were there changes in "findos" of the scripts that causes this?***[COLOR=Black]

I think this issue may come up later and bite someone if they were using Windows Server..
[/COLOR][/COLOR]

---

### Post by MAFoElffen on 2010-07-17
[U][B]POSTSCRIPT:
[/B][/U]
After unistalling Windows Business Server and playing with Solaris 10 again, I remembered how resource intensive that OS was.  After getting it all setup, I backed up that "install" for prosperity (if I needed it in the future), then uninstalled it.

I decided to install Ubuntu 10.04 Server Edition on the third drive (in place of Solaris 10)...

---

