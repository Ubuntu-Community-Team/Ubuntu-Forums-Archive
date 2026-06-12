---
title: "Boot Loader does not appear after installing Ubuntu 10.04"
date: 2010-08-03
forum: Installation &amp; Upgrades
---

### Post by Neo_Me on 2010-08-03
I dual boot WinXP SP3 and Win 7 64bit.

C - win xp D - win7 E- data F - data

Today I installed Ubuntu to C or win xp partition.

 I can access the other partitions but when restarting I cannot see the boot loader. It directly boots to Ubuntu. My Win7 partition is still there , but I cannot boot into it.

Please Help.

---

### Post by presence1960 on 2010-08-03
Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

 This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by Neo_Me on 2010-08-03
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *      9,711,616   209,711,103   199,999,488  83 Linux
/dev/sda2         209,712,571 1,953,503,999 1,743,791,429   f W95 Ext d (LBA)
/dev/sda5         209,712,573   419,425,019   209,712,447   7 HPFS/NTFS
/dev/sda6         419,425,083 1,186,464,509   767,039,427   7 HPFS/NTFS
/dev/sda7       1,186,464,573 1,953,503,999   767,039,427   7 HPFS/NTFS
/dev/sda3               2,048     9,711,615     9,709,568  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        ea330757-d155-49ce-8f16-1d28e4ae231a   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        b3902ddd-cac6-4033-9c0f-db87eb81c78f   swap                                     
/dev/sda5        AAB0352DB035017D                       ntfs                                     
/dev/sda6        78403B2B403AF00C                       ntfs                                     
/dev/sda7        FC7C414C7C4102BE                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)
/dev/sda5        /media/AAB0352DB035017D  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda7        /media/FC7C414C7C4102BE  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda6        /media/78403B2B403AF00C  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


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
search --no-floppy --fs-uuid --set ea330757-d155-49ce-8f16-1d28e4ae231a
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
search --no-floppy --fs-uuid --set ea330757-d155-49ce-8f16-1d28e4ae231a
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
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set ea330757-d155-49ce-8f16-1d28e4ae231a
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=ea330757-d155-49ce-8f16-1d28e4ae231a ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set ea330757-d155-49ce-8f16-1d28e4ae231a
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=ea330757-d155-49ce-8f16-1d28e4ae231a ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set ea330757-d155-49ce-8f16-1d28e4ae231a
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set ea330757-d155-49ce-8f16-1d28e4ae231a
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=b3902ddd-cac6-4033-9c0f-db87eb81c78f none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   9.4GB: boot/grub/core.img
  48.0GB: boot/grub/grub.cfg
   9.4GB: boot/initrd.img-2.6.32-21-generic
   9.4GB: boot/vmlinuz-2.6.32-21-generic
   9.4GB: initrd.img
   9.4GB: vmlinuz
```

---

### Post by Neo_Me on 2010-08-03
done

---

### Post by mikewhatever on 2010-08-03
I am afraid you've deleted the W7's boot files, which were, most likely, on the C partition. Ouch!

---

### Post by presence1960 on 2010-08-03
Your windows 7 boot files were on the XP partition. When you installed ubuntu over that you sent them to their death.

Another problem is that your windows 7 is on an logical partition (sda5) inside an extended partition (sda2). The bad news is that windows needs to be on a primary partition to boot. When you had XP the boot files were located on XP's partition (sda1) which is a primary partition.

Unless someone knows some tricks you may have to reinstall windows 7 to a primary partition. This will overwrite GRUB on the MBR so after you install 7 and verify it is working properly you will have to reinstall GRUB so you can boot into both OSs. See [here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") for reinstalling GRUB. Use the first method (Simplest) to reinstall GRUB.

---

### Post by Neo_Me on 2010-08-03
> **mikewhatever said:**
> I am afraid you've deleted the W7's boot files, which were, most likely, on the C partition. Ouch!

I am sorry but I dont understand. Why are the boot files in C ? I mean shouldnt it be in D ?

Also , anyway to change it back ?

---

### Post by Neo_Me on 2010-08-03
> **presence1960 said:**
> Your windows 7 boot files were on the XP partition. When you installed ubuntu over that you sent them to their death.

Another problem is that your windows 7 is on an logical partition (sda5) inside an extended partition (sda2). The bad news is that windows needs to be on a primary partition to boot. When you had XP the boot files were located on XP's partition (sda1) which is a primary partition.

Unless someone knows some tricks you may have to reinstall windows 7 to a primary partition. This will overwrite GRUB on the MBR so after you install 7 and verify it is working properly you will have to reinstall GRUB so you can boot into both OSs. See [here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD") for reinstalling GRUB. Use the first method (Simplest) to reinstall GRUB.

So , If I back up my data and reinstall windows 7 on the same partition , will it be alright >?

---

### Post by presence1960 on 2010-08-03
> **Neo_Me said:**
> I am sorry but I dont understand. Why are the boot files in C ? I mean shouldnt it be in D ?

Also , anyway to change it back ?

That is how windows works, so complain to Microsoft. When you install another version of windows it combines the boot files with the existing windows OS on the machine. Unless you mark the new partition you are installing the second windows onto as bootable. In that case it does need to be a primary partition.

Unfortunately you didn't do that and the installer combined both windows boot process with the existing XP installation and as windows does automatically made the second windows install a logical partition. When this is done you can not remove the version of windows on the primary partition (in your case XP0 and still be able to boot the second version you installed.

---

### Post by presence1960 on 2010-08-03
> **Neo_Me said:**
> So , If I back up my data and reinstall windows 7 on the same partition , will it be alright >?

No you need to put windows 7 on a primary partition. Use gparted to delete the sda5, sda6 & sda7 partitions, then delete the sda2 partition. Using the unallocated space left from doing that create a primary NTFS partition and install windows to that. Then verify windows works properly. next install GRUB to MBR using the link I provided earlier.

P.S. Back all data especially what is on sda6 & sda7. As everything in the extended partition will be removed!

---

### Post by Neo_Me on 2010-08-05
> **presence1960 said:**
> No you need to put windows 7 on a primary partition. Use gparted to delete the sda5, sda6 & sda7 partitions, then delete the sda2 partition. Using the unallocated space left from doing that create a primary NTFS partition and install windows to that. Then verify windows works properly. next install GRUB to MBR using the link I provided earlier.

P.S. Back all data especially what is on sda6 & sda7. As everything in the extended partition will be removed!

I honestly didnt understand what you said about logical and primary partitions, but i figured backing up everything and starting anew should work.

So, right now , I reinstalled Win7 , backed up all data and now I want to know how to create 4 primary partitions.

---

### Post by oldfred on 2010-08-05
Windows has to be on a primary partition. Linux does not have to be. Make three primary and use the fourth as the extended for the rest of the drive so you can make extra logical partitions.

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)


To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by presence1960 on 2010-08-05
Before installing an OS one should already know what primary, extended and logical partitions are. When one does not know what these are is when one gets into trouble sometimes. 

I would suggest some reading for you to get up to speed so you can successfully create a dual boot set up that will work the first time for you. See [here]("https://help.ubuntu.com/community/HowtoPartition").

Without the understanding of partitioning you will continue to struggle in the area of OS installations.

---

