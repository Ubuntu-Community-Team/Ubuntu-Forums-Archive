---
title: "My grub problem, can't find windows partition"
date: 2011-02-05
forum: Installation &amp; Upgrades
---

### Post by Harbard on 2011-02-05
I was forced to move things around on my system, so I just reinstalled everything and tried a new partition layout on my drive.

I installed Windows XP first, then Ubuntu 10.10.  Now the Windows partition does not show up in the boot list.  After searching through many othe posts and not seeing a solution that will work for me....need help.  Unfortunately I absolutely have to run Windows, else I would just delete the damn thing.

Here is the output from the bootinfo script:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   104,857,599   104,857,537   7 HPFS/NTFS
/dev/sda2         104,859,646   419,430,399   314,570,754   5 Extended
/dev/sda5         104,859,648   125,831,167    20,971,520  82 Linux swap / Solaris
/dev/sda6         125,833,216   419,430,399   293,597,184  83 Linux
/dev/sda3         419,430,400   734,003,199   314,572,800  83 Linux
/dev/sda4         734,003,200 1,465,147,391   731,144,192  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        2C44EB5A44EB2574                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        e252c92f-ea5d-4deb-af37-2b819e188cbf   ext4       linux2                        
/dev/sda4        a036822c-be75-4418-bce6-c4022c80dde7   ext4       homebase                      
/dev/sda5        5516d386-0725-4806-9653-3db9ecbd6594   swap                                     
/dev/sda6        09f876c7-283e-47c6-969c-bc92880487d6   ext4       distro1                       
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/2C44EB5A44EB2574  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda6        /media/distro1           ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda3        /media/linux2            ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda4        /media/homebase          ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /fastdetect


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 09f876c7-283e-47c6-969c-bc92880487d6
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 09f876c7-283e-47c6-969c-bc92880487d6
set locale_dir=($root)/boot/grub/locale
set lang=en
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 09f876c7-283e-47c6-969c-bc92880487d6
	linux	/boot/vmlinuz-2.6.35-25-generic-pae root=UUID=09f876c7-283e-47c6-969c-bc92880487d6 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 09f876c7-283e-47c6-969c-bc92880487d6
	echo	'Loading Linux 2.6.35-25-generic-pae ...'
	linux	/boot/vmlinuz-2.6.35-25-generic-pae root=UUID=09f876c7-283e-47c6-969c-bc92880487d6 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-25-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 09f876c7-283e-47c6-969c-bc92880487d6
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos6)'
	search --no-floppy --fs-uuid --set 09f876c7-283e-47c6-969c-bc92880487d6
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=09f876c7-283e-47c6-969c-bc92880487d6 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda4 during installation
UUID=a036822c-be75-4418-bce6-c4022c80dde7 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=5516d386-0725-4806-9653-3db9ecbd6594 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 111.8GB: boot/grub/core.img
 103.5GB: boot/grub/grub.cfg
  66.2GB: boot/initrd.img-2.6.35-25-generic-pae
 111.8GB: boot/vmlinuz-2.6.35-25-generic-pae
  66.2GB: initrd.img
 111.8GB: vmlinuz


```

I think it is related to my specifying a separate /home partition.  I have tried reinstalling grub2 and updating grub2.  No luck.  I assume I need to manually edit grub.

Thanks in advance.

---

### Post by presence1960 on 2011-02-05
Did you try booting to ubuntu and running from terminal ```
sudo update-grub
```

---

### Post by Harbard on 2011-02-05
yep..here are the results:

```

dan@alpha:~$ sudo update-grub
[sudo] password for dan: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-25-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-25-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
done
dan@alpha:~$ 

```

It is not seeing the Windows partition.

---

### Post by Harbard on 2011-02-05
update:

I booted from my Windows disk and used fixmbr to restore the the mbr to it's original state.  This worked to get me into Windows.  Now, of course, I can't boot into Linux.  So I re-installed grub 2 from a live disk and it still won't detect the Windows installation.

So is there anyway to manually get the Windows information into grub?

---

### Post by patocardo on 2011-02-05
I have a similar problem. But I know what causes it: I accidentally deleted windows root files.
Any one do know how to restore/copy/download the windows XP pro SP2 root files?
Additionally, I have installed two winXP versions, and I want to avoid reinstall the system, recover grub, etc. etc.

---

### Post by wilee-nilee on 2011-02-05
> **Harbard said:**
> update:

I booted from my Windows disk and used fixmbr to restore the the mbr to it's original state.  This worked to get me into Windows.  Now, of course, I can't boot into Linux.  So I re-installed grub 2 from a live disk and it still won't detect the Windows installation.

So is there anyway to manually get the Windows information into grub?

I think you need to run a chkdsk. If you install gparted in Ubuntu and look at the XP partition and its information by right clicking you may see this indicated.

Can you open the XP from Ubuntu does it show in the computer tab or in the left panel in home?

---

### Post by wilee-nilee on 2011-02-05
> **patocardo said:**
> I have a similar problem. But I know what causes it: I accidentally deleted windows root files.
Any one do know how to restore/copy/download the windows XP pro SP2 root files?
Additionally, I have installed two winXP versions, and I want to avoid reinstall the system, recover grub, etc. etc.

You need to start your own thread. There are no legit XP downloads at this time not associated with the computer vendors.

In your own thread though post the bootscript in my signature. You might try a chkdsk /r as well.

---

### Post by Harbard on 2011-02-05
Not sure exactly what you are asking.....

The windows partition can be mounted and accessed normally.  There was no indication that the file system is corrupt.  Though I used gparted to check the file system anyway, no errors reported.

I am wondering if it's problem that I have the Windows partition on sda1 (a primary partition) and the Ubuntu installation (and the boot directory) in a logical partition sda6 and /home on a primary partition sda4.  

Maybe the easiest solution is just re-arrange my partitions?

Things are arranged thusly:

sda1:  ntfs (Windows) primary partition
sda2: extended
     sda5:  linux-swap
     sda6:  ext4 (Ubuntu)
sda3: ext4 (unused at the moment)
sda4:  ext4 (/home)

---

### Post by wilee-nilee on 2011-02-05
Here is a link for editing grub2 proceed with caution, it will open at this part of the menu. The only thing I don't have is the correct stanzas to add.
[https://help.ubuntu.com/community/Grub2#Custom%20Menu%20Entries](https://help.ubuntu.com/community/Grub2#Custom%20Menu%20Entries)

You might wait for presence1960 to post again they are quite knowledgeable, or another who knows the stanzas or a fix. 

The script looks good the extended partition is okay, although it being sda2 makes me wonder if this is a MS extended. I believe Linux starts the extended at sda4, this may be a problem I'm not sure.

---

### Post by Harbard on 2011-02-06
okay, I found a solution.

After deleting all partitions re-installing windows, re-install Unbuntu 10.10, messing with MBR, grub and anything else I could think of...the ultimate solution was install Fedora 14.  This picked up Windows and allows me to dual boot.  This is very unsatisfactory though.  I want to have the same distro on all my computers.  Plus, I want to have a separate /home patition.

All in all, changing to 10.10 was a mistake.  Either grub 2 is hosed up or the installer for 10.10 is.

---

### Post by patocardo on 2011-02-07
> **wilee-nilee said:**
> You need to start your own thread. There are no legit XP downloads at this time not associated with the computer vendors.

In your own thread though post the bootscript in my signature. You might try a chkdsk /r as well.

Thanks wilee-nilee! I'm opening my own thread now with the Title :"cannot run windows anymore"

---

### Post by oldfred on 2011-02-07
This is a typical windows entry. We used to have to add entries with old grub, but almost never with grub2's osprober and a working windows.

gksudo gedit /etc/grub.d/40_custom

```
menuentry "WinXP" {
    set root=(hd0,1)
    insmod chain
    chainloader +1 
}

```
Then run this to add it to grub.cfg:
sudo update-grub


Some entries add these lines:
insmod ntfs

and a search line that overrides the set root if set root does not work.
search --no-floppy --fs-uuid --set 2C44EB5A44EB2574

---

