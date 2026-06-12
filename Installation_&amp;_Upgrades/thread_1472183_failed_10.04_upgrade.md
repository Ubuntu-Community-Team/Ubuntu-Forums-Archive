---
title: "failed 10.04 upgrade"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by jimbo12345 on 2010-05-04
Hi,

Just received an update from 9.04 to 10.04.  Clicked through to install it.  Now it's dead.  It got as far as 40% of the way through installing the files.  left it for 12 hours while away.  Came back & still on 40% so I gave up and shut the thing off (I knew this would cause problems).  Now after a reboot, get many error messages - too many to note down.  Loads as far as the login screen, can't get any further than that.    Any ideas? or quick fixes that won't require thousands of shell commands?

---

### Post by zvacet on 2010-05-04
Boot in recovery mode and type

```
 dpkg --configure -a

 apt-get -f install
```

---

### Post by jimbo12345 on 2010-05-04
Hi there,

I ran - 

sudo apt-get dist-upgrade -f  

or something like that.  Unfortunately, now i'm left with some error, and this prompt appears when i boot the computer 

grub rescue>   

Can't access Windows or anything anymore.  I'm having to use an Ubuntu trial disk just to get to this point so i can get on here to use the forums.

By the way, ubuntu is installed within my windows drive - c:/ubuntu.

Any ideas/quick fixes?

---

### Post by jimbo12345 on 2010-05-05
I think what has happened is i've installed grub onto my windows hard drive - i normally use windows boot menu, then choose ubuntu from that list, but i think grub has taken over, but isnt finding anything to boot.   Anyone have any ideas on restoring this?  I'm now stuck with a dead pc, but i can't afford to format it or reinstall everything - it's taken me 2 months of solid messing about just to get ubuntu at a usable state with my hardware etc

---

### Post by jimbo12345 on 2010-05-07
Well, it's been 3 days now, and having lost 4 years worth of data due to this upgrade.  I guess by the flurry of replies/help that my system is a lost cause now.  Guess its time to get the Windows CD back out.

---

### Post by frantid on 2010-05-07
can you boot the livecd and run this script?

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

post results here by pasting the text in between code tags -- i.e. click on the # sign in the reply box and paste in between the brakets ] [

---

### Post by Bios Element on 2010-05-07
> **jimbo12345 said:**
> Well, it's been 3 days now, and having lost 4 years worth of data due to this upgrade.  I guess by the flurry of replies/help that my system is a lost cause now.  Guess its time to get the Windows CD back out.

Threatening us with 'leaving' won't get you help any quicker. The lack of responses typically relates to cases where people aren't sure what to do since it could be any number of things causing the problem.

Furthermore, you've 'lost' nothing as long as you didn't corrupt the drive when you shut it down which is very unlikely. You could always use a LiveCD to copy your /home partition off to another drive before re-installing whatever system you want on it.

---

### Post by jimbo12345 on 2010-05-09
frantid,  thanks, i'll give it a try, but this is all a bit over my head, so don't be surprised if I don't get anywhere...  At the moment, I haven't made any changes to my Windows installation - it's still there on the drive, but something has gone wrong with windows boot menu - it just freezes before the menu comes up, with no errors and no text when trying to boot.  I've tried using a Vista recovery cd to fix it, and it sees my windows installation, and attempts to scan/fix the boot menu, but it says there are no errors.  I'm wondering if theres a way of reinstalling windows boot menu without damaging the windows installation.

Bios Element,  I haven't threatened to leave 'You'  I simply know how to use windows and that is my 1st option of any recovery, therefore is my first port of call when trying to rescue anything I have on my system.   So far with this, i have rendered CD-RW's completely unreadable when trying to format within K3b.   Killed the MBR with a simple upgrade process and the list goes on.  Sure I like a challenge, hence my decision to have a play with Linux, but it's still a system which is far too easy to do irrepairable damage both to hardware and software for the average user.  Otherwise it's come on leaps and bounds since the first time I used it/had nightmare with it in the mid 90's.  However the nightmares continue....

---

### Post by jimbo12345 on 2010-05-09
Frantid - info as requested...
By the way, i'll explain a little further about my situation - At the moment, i now have a working system, but to do so, i've had to do a fresh ubuntu install from the CD, and created a new partition within the Windows boot drive - drive C, or sda1, which is now where ubuntu resides, however, the actual windows install is on drive D, or sdb1.  Now from this script, i've noticed that grub 0.95 has been installed in the MBR of sdb1, however, if i understand correctly, this should be the Windows boot menu.  At the minute when booting, grub does show the Vista loader within its menu, so it is being recognised, but when you select this option, nothing happens, no errors, i'm just left with a blank screen with a flashing cursor in the top left corner, no hard disk activity, and no windows boot menu.  Also FIXMBR does not fix this, it seems the windows boot menu is there and is recognised, but is corrupted somehow.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 0.95 is installed in the MBR of /dev/sdb and looks on boot drive #1 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 546616 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

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

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr /wubildr

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     9,767,519     9,767,457   7 HPFS/NTFS
/dev/sda2           9,767,520    78,156,224    68,388,705   5 Extended
/dev/sda5           9,767,583    75,248,459    65,480,877  83 Linux
/dev/sda6          75,248,523    78,156,224     2,907,702  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   232,476,614   232,476,552   7 HPFS/NTFS
/dev/sdb2         232,476,615   234,436,544     1,959,930   f W95 Ext d (LBA)
/dev/sdb5         232,476,678   234,436,544     1,959,867   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        2270B2AB70B28557                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        a28be7fe-3ff4-4434-a69c-e45e0f0391f9   ext4                                     
/dev/sda6        2d248735-5cd6-439a-9af7-5d4087e48526   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        3A5CE0C45CE07BCF                       ntfs       Stuff                         
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        086E-F2B5                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sdb1        /media/sdb1              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
    search --no-floppy --fs-uuid --set a28be7fe-3ff4-4434-a69c-e45e0f0391f9
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=a28be7fe-3ff4-4434-a69c-e45e0f0391f9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set a28be7fe-3ff4-4434-a69c-e45e0f0391f9
    echo    'Loading Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=a28be7fe-3ff4-4434-a69c-e45e0f0391f9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set a28be7fe-3ff4-4434-a69c-e45e0f0391f9
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=a28be7fe-3ff4-4434-a69c-e45e0f0391f9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set a28be7fe-3ff4-4434-a69c-e45e0f0391f9
    echo    'Loading Linux 2.6.31-21-generic ...'
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=a28be7fe-3ff4-4434-a69c-e45e0f0391f9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set a28be7fe-3ff4-4434-a69c-e45e0f0391f9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set a28be7fe-3ff4-4434-a69c-e45e0f0391f9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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
proc                                       /proc           proc         defaults                                           0  0  
# / was on /dev/sda5 during installation
UUID=a28be7fe-3ff4-4434-a69c-e45e0f0391f9  /               ext4         errors=remount-ro                                  0  1  
# swap was on /dev/sda6 during installation
UUID=2d248735-5cd6-439a-9af7-5d4087e48526  none            swap         sw                                                 0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8                              0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8                           0  0  
/dev/sdb5                                  /media/sdb5     vfat         uid=jamie,gid=jamie,noauto                         0  0  
/dev/sdc1                                  /media/sdc1     vfat         uid=jamie,gid=jamie,users,noauto,user              0  0  
/dev/sdb1                                  /media/sdb1     ntfs         nls=iso8859-1,umask=000,gid=jamie,owner,uid=jamie  0  0  

=================== sda5: Location of files loaded by Grub: ===================


   7.7GB: boot/grub/core.img
  18.0GB: boot/grub/grub.cfg
   6.4GB: boot/initrd.img-2.6.31-21-generic
   8.9GB: boot/initrd.img-2.6.32-22-generic
   5.8GB: boot/vmlinuz-2.6.31-21-generic
   6.2GB: boot/vmlinuz-2.6.32-22-generic
   8.9GB: initrd.img
   6.4GB: initrd.img.old
   6.2GB: vmlinuz
   5.8GB: vmlinuz.old

```

---

### Post by mulder_edu on 2010-08-10
I'm not sure if you're still working on this, but when I had a similar problem, this is what I did:
My problem was actually that I had removed an ubuntu install (which I had trashed by mistake), which left me with no boot loader. My other partition was XP, but this should be similar.

In Windows XP, you'll want to boot to the install disk and login to the recovery console (the option to repair, rather than install), and then run these commands.  In Vista, you'll boot to the recovery disk, and select the command prompt when you're given a list of recovery options.  Then try this:

In XP:
<code>
fixmbr
fixboot
</code>

In Vista or 7:
<code>
bootrec /FixMbr
bootrec /FixBoot
</code>

That will fix the master boot record and restore the boot sector (for windows).  I think the startup recovery tool in Vista just rebuilds the Bcd (the database Vista and 7 boot from), and I don't think it goes through these steps.  I think these aren't automatic because it's more of a last ditch effort to fix the problem.  This is usually the first thing I do though when I run into the Windows startup problem.

Good Luck!

Oh, I missed your comment that you'd already tried fixmbr.  Hope someone else has any ideas.  I'm sure we'll run into this problem again in future distros.

---

