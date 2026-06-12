---
title: "Reinstall grub"
date: 2010-09-06
forum: Installation &amp; Upgrades
---

### Post by jambel on 2010-09-06
Hello,

I had an installation of ubuntu 9.10 and windows XP in separate hard drives and I used grub for OS selection. When 10.04 comes out, I decide to make a clean install and not an upgrade, so I put it on the same drive of previous linux installation and I ignore windows on purpose.

Now I need to boot on windows, is there any way to reinstall grub or is it possible from boot menu <F8> to select which drive I want to boot? When I select the drive that has windows a blank screen appears and nothing happens.

Any ideas?

Thanks!

---

### Post by kansasnoob on 2010-09-06
In order that we can understand your setup properly it would be best to see the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

It can be run either using your installed Ubuntu or a Live CD/USB. Also another set of instructions for running the script:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by jambel on 2010-09-06
ok, here is the output

> 
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  DEll Restore: Fat32
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   234,420,479   234,420,417   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   154,079,231   154,077,184  83 Linux
/dev/sdb2         154,081,278   160,086,015     6,004,738   5 Extended
/dev/sdb5         154,081,280   160,086,015     6,004,736  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   234,436,544   234,436,482  42 SFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        F8F48C6BF48C2E46                       ntfs                                     
/dev/sda                                                isw_raid_member                               
/dev/sdb1        ee0c7a6a-0de1-4379-9c4f-4a92c2661de2   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        6c0ca18c-67d0-40cc-8001-02927e78b4df   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        749C95E39C95A062                       ntfs                                     
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        FC28B52828B4E336                       ntfs       Seagate                       
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sdd1        /media/Seagate           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set ee0c7a6a-0de1-4379-9c4f-4a92c2661de2
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set ee0c7a6a-0de1-4379-9c4f-4a92c2661de2
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=4
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ee0c7a6a-0de1-4379-9c4f-4a92c2661de2
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=ee0c7a6a-0de1-4379-9c4f-4a92c2661de2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ee0c7a6a-0de1-4379-9c4f-4a92c2661de2
    echo    'Loading Linux 2.6.32-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=ee0c7a6a-0de1-4379-9c4f-4a92c2661de2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ee0c7a6a-0de1-4379-9c4f-4a92c2661de2
    linux    /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=ee0c7a6a-0de1-4379-9c4f-4a92c2661de2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ee0c7a6a-0de1-4379-9c4f-4a92c2661de2
    echo    'Loading Linux 2.6.32-23-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=ee0c7a6a-0de1-4379-9c4f-4a92c2661de2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ee0c7a6a-0de1-4379-9c4f-4a92c2661de2
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=ee0c7a6a-0de1-4379-9c4f-4a92c2661de2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ee0c7a6a-0de1-4379-9c4f-4a92c2661de2
    echo    'Loading Linux 2.6.32-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=ee0c7a6a-0de1-4379-9c4f-4a92c2661de2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ee0c7a6a-0de1-4379-9c4f-4a92c2661de2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ee0c7a6a-0de1-4379-9c4f-4a92c2661de2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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

#menuentry "Windows XP (on /dev/sda1)"{
#insmod ntfs
#set root='(hd0,1)'
#chainloader +1
#} 
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=ee0c7a6a-0de1-4379-9c4f-4a92c2661de2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=6c0ca18c-67d0-40cc-8001-02927e78b4df none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  71.0GB: boot/grub/core.img
  75.1GB: boot/grub/grub.cfg
  71.1GB: boot/initrd.img-2.6.32-22-generic-pae
  73.0GB: boot/initrd.img-2.6.32-23-generic-pae
  73.0GB: boot/initrd.img-2.6.32-24-generic-pae
  71.1GB: boot/vmlinuz-2.6.32-22-generic-pae
  72.7GB: boot/vmlinuz-2.6.32-23-generic-pae
  73.0GB: boot/vmlinuz-2.6.32-24-generic-pae
  73.0GB: initrd.img
  73.0GB: initrd.img.old
  73.0GB: vmlinuz
  72.7GB: vmlinuz.old
=============================== StdErr Messages: ===============================

ERROR: isw: wrong number of devices in RAID set "isw_dahgecjcei_Volume0" [1/2] on /dev/sda
ERROR: isw: wrong number of devices in RAID set "isw_dahgecjcei_Volume0" [1/2] on /dev/sda
ERROR: isw: wrong number of devices in RAID set "isw_dahgecjcei_Volume0" [1/2] on /dev/sda
ERROR: isw: wrong number of devices in RAID set "isw_dahgecjcei_Volume0" [1/2] on /dev/sda
ERROR: isw: wrong number of devices in RAID set "isw_dahgecjcei_Volume0" [1/2] on /dev/sda


---

### Post by kansasnoob on 2010-09-06
Well, I should first say that I know nothing about RAID, so we should take this into consideration:

> /dev/sda isw_raid_member 

> ERROR: isw: wrong number of devices in RAID set "isw_dahgecjcei_Volume0" [1/2] on /dev/sda
ERROR: isw: wrong number of devices in RAID set "isw_dahgecjcei_Volume0" [1/2] on /dev/sda
ERROR: isw: wrong number of devices in RAID set "isw_dahgecjcei_Volume0" [1/2] on /dev/sda
ERROR: isw: wrong number of devices in RAID set "isw_dahgecjcei_Volume0" [1/2] on /dev/sda
ERROR: isw: wrong number of devices in RAID set "isw_dahgecjcei_Volume0" [1/2] on /dev/sda 

That aside I see that grub2 is installed in the mbr's of /dev/sda and /dev/sdc. 

Win XP is on /dev/sda1 and Ubuntu is on /dev/sdb1.

Physical description of drives as follows:

> Disk /dev/sda: 120.0 GB
Disk /dev/sdb: 82.0 GB
Disk /dev/sdc: 120.0 GB
Disk /dev/sdd: 1000.2 GB

**That may be important to know if you need to change boot disc priority in BIOS** ;)

Now, I don't know why "30_os-prober" hasn't found Win XP, but it hasn't:

> ### BEGIN /etc/grub.d/30_os-prober ###
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

I'm sure you've tried simply running:

```
sudo update-grub
```

While booted into Ubuntu, eh? If not I'd try that first, but also while booted into Ubuntu I'd install grub2 to it's own drives mbr by running:

```
sudo grub-install /dev/sdb
```

Now, it may be that "30_os-prober" is failing to read XP because of the RAID thing. As I said I'm ignorant about RAID.

I do see that someone tried to add a custom entry for XP in "40_custom":

> ### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.

#menuentry "Windows XP (on /dev/sda1)"{
#insmod ntfs
#set root='(hd0,1)'
#chainloader +1
#}
### END /etc/grub.d/40_custom ###

But then it was later commented out. I'm thinking the entry should have been:

```
menuentry "Windows XP (on /dev/sda1)"{
         insmod ntfs
         set root='(hd0,1)'
         search --no-floppy --fs-uuid --set F8F48C6BF48C2E46
         drivemap -s (hd1) ${root}
         chainloader +1
} 
```

I an however guessing at the drivemap, maybe it should be:

```
drivemap -s (hd0) ${root}
```

So, you could try something like that if "sudo update-grub" fails to recognize it, just be sure to run "sudo update-grub" after editing any file in grub2.

Another thing to try, after installing grub2 to the mbr of 'sdb', would be to give 'sda' a Windows readable mbr using Lilo like this:

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sda mbr
```

Then if you adjust the BIOS to boot sda first you'll at least know if Windows will boot under it's own power. (Could be a bit of kludge figuring out which 120GB drive is sda).

NOTE: if you use Lilo as described above using your installed Ubuntu I always like to remove the package "lilo" when I'm done just to prevent it from messing things up during updates :)

Does any of that make sense?

---

### Post by jambel on 2010-09-06
Yes I had already run sudo update-grub and this is the output

> 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-24-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-23-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-23-generic-pae
Found linux image: /boot/vmlinuz-2.6.32-22-generic-pae
Found initrd image: /boot/initrd.img-2.6.32-22-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
ERROR: isw: wrong number of devices in RAID set "isw_dahgecjcei_Volume0" [1/2] on /dev/sda
done


The sdc is an empty hard drive, which once upon a time, accidentally select to install grub to all drives.

That someone tried to edit 40_custom was me but with no further luck, I just keep them as a remark.

I'll try your recommendations and come back.

I appreciate your help! ):P

---

### Post by jambel on 2010-09-06
another question, could be fixmbr instead of lilo make the job for autonomous windows boot on sda?

---

### Post by jambel on 2010-09-06
No luck yet..

I change the boot order from BIOS, I've install grub on /dev/sdb and I edit 40_custom with your recommendation but still nothing

any other idea?

this is the new boot script results

> 
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdc and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  DEll Restore: Fat32
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   234,420,479   234,420,417   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   154,079,231   154,077,184  83 Linux
/dev/sdb2         154,081,278   160,086,015     6,004,738   5 Extended
/dev/sdb5         154,081,280   160,086,015     6,004,736  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   234,436,544   234,436,482  42 SFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        F8F48C6BF48C2E46                       ntfs                                     
/dev/sda                                                isw_raid_member                               
/dev/sdb1        ee0c7a6a-0de1-4379-9c4f-4a92c2661de2   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        6c0ca18c-67d0-40cc-8001-02927e78b4df   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        749C95E39C95A062                       ntfs                                     
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set ee0c7a6a-0de1-4379-9c4f-4a92c2661de2
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
set root='(hd1,1)'
search --no-floppy --fs-uuid --set ee0c7a6a-0de1-4379-9c4f-4a92c2661de2
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=4
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ee0c7a6a-0de1-4379-9c4f-4a92c2661de2
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=ee0c7a6a-0de1-4379-9c4f-4a92c2661de2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ee0c7a6a-0de1-4379-9c4f-4a92c2661de2
    echo    'Loading Linux 2.6.32-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=ee0c7a6a-0de1-4379-9c4f-4a92c2661de2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ee0c7a6a-0de1-4379-9c4f-4a92c2661de2
    linux    /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=ee0c7a6a-0de1-4379-9c4f-4a92c2661de2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ee0c7a6a-0de1-4379-9c4f-4a92c2661de2
    echo    'Loading Linux 2.6.32-23-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=ee0c7a6a-0de1-4379-9c4f-4a92c2661de2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ee0c7a6a-0de1-4379-9c4f-4a92c2661de2
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=ee0c7a6a-0de1-4379-9c4f-4a92c2661de2 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ee0c7a6a-0de1-4379-9c4f-4a92c2661de2
    echo    'Loading Linux 2.6.32-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=ee0c7a6a-0de1-4379-9c4f-4a92c2661de2 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ee0c7a6a-0de1-4379-9c4f-4a92c2661de2
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ee0c7a6a-0de1-4379-9c4f-4a92c2661de2
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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

#menuentry "Windows XP (on /dev/sda1)"{
#insmod ntfs
#set root='(hd0,1)'
#chainloader +1
#}

menuentry "Windows XP (on /dev/sda1)"{
         insmod ntfs
         set root='(hd0,1)'
         search --no-floppy --fs-uuid --set F8F48C6BF48C2E46
         drivemap -s (hd0) ${root}
         chainloader +1
} 
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=ee0c7a6a-0de1-4379-9c4f-4a92c2661de2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=6c0ca18c-67d0-40cc-8001-02927e78b4df none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


  71.0GB: boot/grub/core.img
  27.6GB: boot/grub/grub.cfg
  71.1GB: boot/initrd.img-2.6.32-22-generic-pae
  73.0GB: boot/initrd.img-2.6.32-23-generic-pae
  73.0GB: boot/initrd.img-2.6.32-24-generic-pae
  71.1GB: boot/vmlinuz-2.6.32-22-generic-pae
  72.7GB: boot/vmlinuz-2.6.32-23-generic-pae
  73.0GB: boot/vmlinuz-2.6.32-24-generic-pae
  73.0GB: initrd.img
  73.0GB: initrd.img.old
  73.0GB: vmlinuz
  72.7GB: vmlinuz.old
=============================== StdErr Messages: ===============================

ERROR: isw: wrong number of devices in RAID set "isw_dahgecjcei_Volume0" [1/2] on /dev/sda
ERROR: isw: wrong number of devices in RAID set "isw_dahgecjcei_Volume0" [1/2] on /dev/sda
ERROR: isw: wrong number of devices in RAID set "isw_dahgecjcei_Volume0" [1/2] on /dev/sda
ERROR: isw: wrong number of devices in RAID set "isw_dahgecjcei_Volume0" [1/2] on /dev/sda
ERROR: isw: wrong number of devices in RAID set "isw_dahgecjcei_Volume0" [1/2] on /dev/sda


---

### Post by ronparent on 2010-09-06
Just a quick question. Are you currently using raid - it doesn't appear so? If you don't intend to use raid, that option should be turned off in bios (it probably is). Also you have to erase any raid meta data apparently written to sda (ie 'sudo dmraid -E /dev/sda' - you may have to check the syntax for this command). It is likely that an unintended raid tag on sda is preventing grub from finding windows on that drive.

---

### Post by kansasnoob on 2010-09-06
> **jambel said:**
> another question, could be fixmbr instead of lilo make the job for autonomous windows boot on sda?

Yes, you can use a Windows disc to restore a Windows mbr to /dev/sda. I'm just used to using a Linux disc for everything I can.

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by kansasnoob on 2010-09-06
> **ronparent said:**
> Just a quick question. Are you currently using raid - it doesn't appear so? If you don't intend to use raid, that option should be turned off in bios (it probably is). Also you have to erase any raid meta data apparently written to sda (ie 'sudo dmraid -E /dev/sda' - you may have to check the syntax for this command). It is likely that an unintended raid tag on sda is preventing grub from finding windows on that drive.

I knew someone that knows RAID would come along :D

---

### Post by jambel on 2010-09-06
it's SATA2 mode on BIOS not RAID and I'd never use a raid setting on ubuntu, so will dmraid work?

---

### Post by jambel on 2010-09-06
> **kansasnoob said:**
> Yes, you can use a Windows disc to restore a Windows mbr to /dev/sda. I'm just used to using a Linux disc for everything I can.

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Thanks kansasnoob, I'll give a shot later, got to go, thanks again!

---

### Post by dino99 on 2010-09-06
you need to remove dmraid first, then follow kansasnoob post:

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8417410](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8417410)

---

### Post by ronparent on 2010-09-06
> it's SATA2 mode on BIOS not RAID and I'd never use a raid setting on ubuntu, so will dmraid work?

Dmraid comes installed on 10.04. All versions earlier than 9.10 require separate installation (ie 'sudo apt-get install dmraid'). If a disk has ever been used in a raid setup, even if only in windows, the raid meta data will remain as junk when the raid is abandoned and the meta data has to be separately removed. 

Alternatively, you can also uninstall dmraid to rid yourself of its impact on the system. Unfortunately any future upgrade or install that reintroduces dmraid will bring its effect back to haunt you when you have long forgotten that the drive contained unused meta data. The long and short of it is that you are best rid of it if uneeded.  

kansasknoob - happy to pitch in if it is of any help ):P

---

### Post by jambel on 2010-09-06
Thanks everyone, my problem is solved with...

> 
sudo dmraid -rE


beers on me!

cheers

---

