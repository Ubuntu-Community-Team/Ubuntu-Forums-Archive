---
title: "Dual Boot Linux and XP"
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by jouell on 2010-06-04
Hi all,

I have the following PC set up:

Dell  8400 with 3 GB of RAM with 3 160 GB SATA drives:

The  first one has Windows XP installed on it. 

The  second one has been newly formatted and Ubuntu 10.04 has just been  installed on it (20 GB / and 6 GB swap) with grub being installed on the  first partition and not the master boot record. The  remainder will be for storage for Windows. 

The third  drive is simply storage for Windows.

At this point I am  able to boot XP just fine, but I'm not able to boot Linux. I just  getting a blinking cursor or the PC just reboots when I choose Linux.

I  believe I have set up my boot.ini properly using:

C:\bootsectc.lnx="Linux  Ubuntu"

after running   dd if=/dev/sdc1 of=bootsect.lnx  bs=512 count=1 and putting that file in place.

For  reference, I don't believe this is a Linux problem, as much as I am  simply trying to guide the ntldr to be properly pointed to a place where  it can boot Linux, however I don't think anyone at  Microsoft would care to help me with this install too much.


NOTE: When  I go into the bios and disable the first and the third hard drives,  grub pops right up and I'm able to boot Linux with no problem, so that  piece is fine.

I think it's  just now trying to get the correct  syntax so I can boot Linux without having to disable drives and reenable  them.


For kicks I even tried these syntax types in boot.ini:
multi(0)disk(0)rdisk(1)partition(1)="Linux11"
(i.e. 2nd  disk, 1st partition ...etc...)

I read many troubleshooting  documents on dual booting and so forth but I just can't get this right.

For reference, I stated the way XP views my Hard Drives in the intro, which seem to be a different order than Linux sees them, yet I believe I've tried all the combos of settings for this to work (yet clearly have not).


I have attached the output of boot_info_script*.sh here:

Many thanks in advance
-jouell


```


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 95
    Boot files/dirs:   /IO.SYS /MSDOS.SYS /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     Grub 2 in the file /bootsectc1.lnx looks at sector 
                       17307672 of the same hard drive for core.img, but 
                       core.img can not be found at this location. Grub 2 in 
                       the file /bootsectc.lnx looks at sector 1 of the same 
                       hard drive for core.img, but core.img can not be found 
                       at this location. Grub 2 in the file /bootsect.lnx 
                       looks at sector 17307672 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   /BOOT.INI /NTLDR /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb1 has 
                       312575999 sectors, but according to the info from 
                       fdisk, it has 312576641 sectors.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sdc1 and 
                       looks at sector 17307672 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       128,519       128,457  de Dell Utility
/dev/sda2    *        128,520   302,760,989   302,632,470   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   312,576,704   312,576,642  42 SFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048    39,063,551    39,061,504  83 Linux
/dev/sdc2          39,063,552    54,687,743    15,624,192  82 Linux swap / Solaris
/dev/sdc3          54,687,744   312,576,704   257,888,961   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63 1,953,520,064 1,953,520,002   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        07D5-0219                              vfat       DellUtility                   
/dev/sda2        C04806BC4806B168                       ntfs       Disk1 - C                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        C2E48744E48739A5                       ntfs       Disk3 - H                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        17bf8b72-f108-4360-a3fb-d2bc20b3103e   ext3                                     
/dev/sdc2        630456f3-1281-4ffc-bddb-6892ede8b9af   swap                                     
/dev/sdc3        F2D02580D0254C63                       ntfs       G                             
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        3E35-DD37                              vfat       Elements                      
/dev/sdd: PTTYPE="dos" 
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda2/BOOT.INI: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect
c:\bootsect.lnx="Linux"

=========================== sdc1/boot/grub/grub.cfg: ===========================

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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 17bf8b72-f108-4360-a3fb-d2bc20b3103e
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
set root='(hd2,1)'
search --no-floppy --fs-uuid --set 17bf8b72-f108-4360-a3fb-d2bc20b3103e
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 17bf8b72-f108-4360-a3fb-d2bc20b3103e
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=17bf8b72-f108-4360-a3fb-d2bc20b3103e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 17bf8b72-f108-4360-a3fb-d2bc20b3103e
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=17bf8b72-f108-4360-a3fb-d2bc20b3103e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 17bf8b72-f108-4360-a3fb-d2bc20b3103e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 17bf8b72-f108-4360-a3fb-d2bc20b3103e
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

=============================== sdc1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc1 during installation
UUID=17bf8b72-f108-4360-a3fb-d2bc20b3103e /               ext3    errors=remount-ro 0       1
# swap was on /dev/sdc2 during installation
UUID=630456f3-1281-4ffc-bddb-6892ede8b9af none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc1: Location of files loaded by Grub: ===================


   8.8GB: boot/grub/core.img
   8.9GB: boot/grub/grub.cfg
   8.8GB: boot/initrd.img-2.6.32-21-generic
   8.9GB: boot/vmlinuz-2.6.32-21-generic
   8.8GB: initrd.img
   8.9GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sde 


```

---

### Post by wilee-nilee on 2010-06-04
It only boots to windows because it is using the MS boot in sdb. With 3 hard drives installing grub to a partition is the wrong way to go, you should of installed it to the bootloader Lucid was installed in and if you want to keep separate bootloaders choose the HD to boot from on startup.
Windows also wont read ext4, easybcd2 I think can, but really your making it much more difficult then it needs to be. I would just install grub correctly and let it chainload XP.

I use XP and W7 and just let grub2 do the voodoo that it does so well; if setup correctly.

Actually Lucid should boot if you just boot from sdc.

---

### Post by jouell on 2010-06-04
Thanks wilee-nilee

It only boots to windows because it is using the MS boot in sdb. With 3  hard drives installing grub to a partition is the wrong way to go, you  should of installed it to the bootloader Lucid was installed in

>>OK, I think you're suggestion is to install grub to the MBR of  the disk Ubuntu will be installed on (sdc here). I can re-install  easily and do so.
 
and if  you want to keep separate bootloaders choose the HD to boot from on  startup.
>>OK, How would I do that? I'd prefer not to need to touch  the bios every time.

I would just install  grub correctly and let it chainload XP.
>>OK, but how will grub be able to load if the BIOS  looks and finds ntldr before it finds grub? My Goal  is to allow XP (ntldr) to present a menu and then choose Linux.

I use XP and W7 and just let grub2 do the voodoo that it does so well;  if setup correctly.
>>Very Cool. 
>>Thanks.
>>jouell

---

### Post by wilee-nilee on 2010-06-04
Actually I just noticed something else hold on.

You might just confirm as well what it is you want besides working OS's, do you want separate boots for XP and Linux or a bootloader that will run the whole booting process. 

I think if you just set sdc to boot 1st in bios it should boot Linux. You already have grub in the MBR of sdc.
If Linux boots just run sudo update grub to load XP into the grub list.

A choice of boot would be a key prompt mine is f12.

---

### Post by darkod on 2010-06-04
> **jouell said:**
> 
I would just install  grub correctly and let it chainload XP.
>>OK, but how will grub be able to load if the BIOS  looks and finds ntldr before it finds grub? My Goal  is to allow XP (ntldr) to present a menu and then choose Linux.


You tell the BIOS from which disk to try to boot first. As already said, just set the ubuntu disk as first option in BIOS and it should be fine. I guess you had the XP disk disconnected because it's not in grub.cfg at the moment, but simply doing in ubuntu:

sudo update-grub

will detect it and make a dual boot menu.

---

### Post by wilee-nilee on 2010-06-04
> **darkod said:**
> You tell the BIOS from which disk to try to boot first. As already said, just set the ubuntu disk as first option in BIOS and it should be fine. I guess you had the XP disk disconnected because it's not in grub.cfg at the moment, but simply doing in ubuntu:

sudo update-grub

will detect it and make a dual boot menu.

Thanks for confirming, I had seen posts that it didn't seem to be a problem if grub had been put in the Ubuntu partition.

The thing I missed was that the OP wants to have a MS boot with choice of Ubuntu. easybcd2 supposedly will do this but I don't recommend it, darkod knows much more about all of this so I would go by their advice in this.

I run into people at the W7 forum that dual boot and want to do this, they seem scared of grub, it seems it just is a foreign program to them, and some of the real regular helpers really with no understanding of it flag it as a problem no matter what. So I think it is easy to become concerned by its use when your not familiar with it. I started with open source so it is my preference, I think it is much easier to manipulate.

---

### Post by darkod on 2010-06-04
> **wilee-nilee said:**
> Thanks for confirming, I had seen posts that it didn't seem to be a problem if grub had been put in the Ubuntu partition.

You're right. I guess that's because grub2 from the MBR boots linux directly calling the boot files on the partition. So it doesn't mind if grub2 is also put on the partition boot sector.
But for windows, grub2 just calls on the boot process to continue from that particular partition, and having grub2 on that partition is getting in the way.

For vista and 7 I'm not sure if you can avoid this by changing

chainloader +1

in

chainloader /bootmgr

and call the file directly. I use the latter on my usb stick with install files of win7, lucid 32bit, lucid 64bit and clonezilla and starting the win7 installer works like that.

---

### Post by jouell on 2010-06-04
Thank you all for the suggestions.  I get the impression that the answer here would just be to simply let grub take care of the boot loading and be done with it.

As some have mentioned yes there is some fear in terms of using grub as the "master boot loader" of the whole system.  I didn't want to do something that intrusive, because we are having some other technical difficulties in actually getting an image of the XP system, just in case something bad happens. Once that is sorted, I can definitely do so.

Unfortunately the bios doesn't allow the ability to choose which drive up from. It just looks at the first and goes down the list....

Best
-jouell

---

### Post by darkod on 2010-06-04
> **jouell said:**
> 
Unfortunately the bios doesn't allow the ability to choose which drive up from. It just looks at the first and goes down the list....


Are you sure about that? Most boards since years ago offer that option. You have to make difference between device order, and hdd order.
Device order would be: cd-rom, hdd, usb hdd, etc
The hdd order is the order just of the hdds. You will still boot from cd if cd-rom is before hdd in device order. Look around the BIOS again.

If you really can't control the hdd order, another thing to try is plugging the ubuntu disk in the first sata port, or what ever port it tries to boot first from.

---

### Post by jouell on 2010-06-07
> **darkod said:**
> Are you sure about that? Most boards since years ago offer that option. You have to make difference between device order, and hdd order.
Device order would be: cd-rom, hdd, usb hdd, etc
The hdd order is the order just of the hdds. You will still boot from cd if cd-rom is before hdd in device order. Look around the BIOS again.

If you really can't control the hdd order, another thing to try is plugging the ubuntu disk in the first sata port, or what ever port it tries to boot first from.

Yes, I've searched but there is no option for that. It's about 6 years old....

Thanks I can swap the drives with some effort for sure.

---

### Post by jouell on 2010-06-15
All, I ended up installed grub to the MBR of my first drive with a menu.lst as follows:

```


# GRUB configuration file '/boot/grub/menu.lst'.
# generated by 'grubconfig'.  Tue Jun 15 19:52:09 2010
#
# The backup copy of the MBR for drive '/dev/sda' is
# here '/boot/grub/mbr.sda.10072'.  You can restore it like this.
# dd if=mbr.sda.10072 of=/dev/sda bs=512 count=1
#
# Start GRUB global section
#timeout 30
#color light-gray/blue black/light-gray
# End GRUB global section
# Other bootable partition config begins
  title Windows on (/dev/sda2)
  map (hd0,0) (hd0,1)
  map (hd0,1) (hd0,0)
  rootnoverify (hd0,1)
  makeactive
  chainloader +1
# Other bootable partition config ends
# Linux bootable partition config begins
  title Linux on (/dev/sdb1)
  root (hd1,0)
  kernel /boot/vmlinuz root=/dev/sdb1 ro vga=normal


```


That allowed my not to worry about my BIOS limitation (HD boot order), physical HD swapping,  AND to wave bye the XP loader.

Attached is my Grub confirmation screen shot.
[ATTACH]160591[/ATTACH]

Thanks again to all!
jouell

---

### Post by wilee-nilee on 2010-06-15
@jouell, always start your own thread, and post the script in my sig in code tags as suggested. You can also get code tags set by pasting the script readout to the thread highlight the text then clicking on the # in the posting gui.;)

---

### Post by darkod on 2010-06-15
> **wilee-nilee said:**
> @jouell, always start your own thread, and post the script in my sig in code tags as suggested. You can also get code tags set by pasting the script readout to the thread highlight the text then clicking on the # in the posting gui.;)

:)

It is his own thread. And he is just letting us know he solved the problem. :) Why are you so harsh on the poor fellow???

---

### Post by wilee-nilee on 2010-06-15
> **darkod said:**
> :)

It is his own thread. And he is just letting us know he solved the problem. :) Why are you so harsh on the poor fellow???

My bad I wasn't paying attention, I wasn't being harsh at all, just not paying attention. We both know that many post on another thread even months later, with problems that can't be fixed with the solutions in the thread nor without more details.;)

We all get crotchety at times, it can be trying at times in trying to help others when your not actually there to see what they have done or are doing.

In this case I was just not paying attention, and had removed the instant notification, as it had been solved and you had posted so I knew if it could be fixed you would know whats up.:) The threads sort of get lost in a stream of data at times.

---

