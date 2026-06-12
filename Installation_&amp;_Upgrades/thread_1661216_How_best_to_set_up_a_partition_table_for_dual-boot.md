---
title: "How best to set up a partition table for dual-boot using two Ubuntu distros"
date: 2011-01-06
forum: Installation &amp; Upgrades
---

### Post by matthanley on 2011-01-06
I'm putting together a new desktop soon, and I plan to dual-boot between standard Ubuntu and Ubuntu Studio. I won't be installing Windows.

To plan the partition table, I'd like some help understanding what directories can be shared between distros and what needs to be duplicated. Obviously, I plan to use the same /home partition for both distros, and I can use the same /swap partition for both, but what other directories could be shared between installs (*e.g.*, /tmp, /var, /proc, /dev and so on)? It seems like at the very least, / and /etc would need to be unique for each one. Am I on the right track?

I know how to actually partition the drives, I'm just looking for advice on the most efficient way to do this for two different Ubuntu installs, so I don't create redundant directories.

I've searched the forums already, and everything I've seen on dual-boot deals with Ubuntu/Windows or Ubuntu/Mac OS.

---

### Post by presence1960 on 2011-01-06
Usually not a good idea to share /home between distros due to the fact that a lot of settings for software are contained in /home. If your version of software varies between distros you may get into a bind. It is best to let each linux distro/version use it's own /home (which is built into the root filesystem) for settings. But you can keep a separate partition for data that both can access.

I have been multi-booting for almost two years now with no problems since I got away from using a shared /home. Have had 2 versions of Ubuntu, Mint, Crunchbang, Sabayon, Sabayon minimal, Windows XP, Vista & 7 at one time or another over those two years. Currently have 10.10, 9.10 and windows 7 with a shared data partition (actually a 500 GB disk), a partition for my mozilla profiles, a clonezilla partition which eliminates the need to boot from CD to make/restore images,my OS partitions, a 1 TB disk which is split for movies & videos and backup. Also have a 500 GB external disk for backup. As you can see I am quite big on backups. I always have my data backed up on two separate disks-one internal and the other external.

Here is the output of the boot info script of my machine without the external hard disk plugged in so you can get an idea of what I am talking about. The possible setups are almost limitless :

              ```
  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for (,msdos7)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => Testdisk is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda2 starts at sector 312223275.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   312,216,579   312,216,517   7 HPFS/NTFS
/dev/sda2         312,223,275   333,188,099    20,964,825   b W95 FAT32
/dev/sda3         333,188,100   354,168,989    20,980,890   7 HPFS/NTFS
/dev/sda4         354,169,051   488,392,064   134,223,014   5 Extended
/dev/sda5         354,169,053   417,079,529    62,910,477  83 Linux
/dev/sda6         417,079,593   425,465,459     8,385,867  82 Linux swap / Solaris
/dev/sda7         425,465,523   488,392,064    62,926,542  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   976,771,071   976,769,024   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   976,771,071   976,769,024   7 HPFS/NTFS
/dev/sdc2         976,771,072 1,953,523,711   976,752,640   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        5C21A069471313D7                       ntfs       windows7                      
/dev/sda2        039B-7ADA                              vfat       clonezilla-                   
/dev/sda3        42AAC3ED50603A5D                       ntfs       mozilla-profiles              
/dev/sda4: PTTYPE="dos" 
/dev/sda5        68133ee7-9788-4905-b012-452696873308   ext4       karmic 9.10                   
/dev/sda6        4f17c8fd-b57d-4870-864a-694c0610686f   swap                                     
/dev/sda7        391c9a74-1f03-491d-bb10-c63479885d8e   ext4       maverick 10.10                
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4730C00E046AD368                       ntfs       data                          
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        252A246463D88BBB                       ntfs       backup                        
/dev/sdc2        7D16100A2FE8899E                       ntfs       movies & video                
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found
error: /dev/sdg: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda7        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda3        /media/mozilla-profiles  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1        /media/data              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set 68133ee7-9788-4905-b012-452696873308
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=15
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 68133ee7-9788-4905-b012-452696873308
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=68133ee7-9788-4905-b012-452696873308 ro  splash vga=786  quiet splash
	initrd	/boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 68133ee7-9788-4905-b012-452696873308
	linux	/boot/vmlinuz-2.6.31-22-generic root=UUID=68133ee7-9788-4905-b012-452696873308 ro single  splash vga=786
	initrd	/boot/initrd.img-2.6.31-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 5c21a069471313d7
	chainloader +1
}
menuentry "'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 391c9a74-1f03-491d-bb10-c63479885d8e
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=391c9a74-1f03-491d-bb10-c63479885d8e ro splash quiet splash
	initrd /boot/initrd.img-2.6.35-24-generic
}
menuentry "'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 391c9a74-1f03-491d-bb10-c63479885d8e
	linux /boot/vmlinuz-2.6.35-24-generic root=UUID=391c9a74-1f03-491d-bb10-c63479885d8e ro single splash
	initrd /boot/initrd.img-2.6.35-24-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Clonezilla" {
set root=(hd0,2)
linux /live-hd/vmlinuz boot=live union=aufs vga=788 ip=frommedia live-media-path=/live-hd bootfrom=/dev/hda2 toram=filesystem.squashfs
initrd /live-hd/initrd.img
}
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
UUID=68133ee7-9788-4905-b012-452696873308 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=4f17c8fd-b57d-4870-864a-694c0610686f none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 181.6GB: boot/grub/core.img
 186.2GB: boot/grub/grub.cfg
 184.2GB: boot/initrd.img-2.6.31-22-generic
 183.4GB: boot/vmlinuz-2.6.31-22-generic
 184.2GB: initrd.img
 183.4GB: vmlinuz

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 391c9a74-1f03-491d-bb10-c63479885d8e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos7)'
search --no-floppy --fs-uuid --set 391c9a74-1f03-491d-bb10-c63479885d8e
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
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 391c9a74-1f03-491d-bb10-c63479885d8e
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=391c9a74-1f03-491d-bb10-c63479885d8e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 391c9a74-1f03-491d-bb10-c63479885d8e
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/boot/vmlinuz-2.6.35-24-generic root=UUID=391c9a74-1f03-491d-bb10-c63479885d8e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 391c9a74-1f03-491d-bb10-c63479885d8e
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=391c9a74-1f03-491d-bb10-c63479885d8e ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos7)'
	search --no-floppy --fs-uuid --set 391c9a74-1f03-491d-bb10-c63479885d8e
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=391c9a74-1f03-491d-bb10-c63479885d8e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set 5c21a069471313d7
	chainloader +1
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 68133ee7-9788-4905-b012-452696873308
	linux /boot/vmlinuz-2.6.31-22-generic root=UUID=68133ee7-9788-4905-b012-452696873308 ro splash vga=786 quiet splash
	initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode) (on /dev/sda5)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 68133ee7-9788-4905-b012-452696873308
	linux /boot/vmlinuz-2.6.31-22-generic root=UUID=68133ee7-9788-4905-b012-452696873308 ro single splash vga=786
	initrd /boot/initrd.img-2.6.31-22-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Clonezilla" {
set root=(hd0,2)
linux /live-hd/vmlinuz boot=live union=aufs vga=788 ip=frommedia live-media-path=/live-hd bootfrom=/dev/hda2 toram=filesystem.squashfs
initrd /live-hd/initrd.img
}
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=391c9a74-1f03-491d-bb10-c63479885d8e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=4f17c8fd-b57d-4870-864a-694c0610686f none            swap    sw              0       0

=================== sda7: Location of files loaded by Grub: ===================


 222.3GB: boot/grub/core.img
 231.1GB: boot/grub/grub.cfg
 222.7GB: boot/initrd.img-2.6.35-22-generic
 234.3GB: boot/initrd.img-2.6.35-24-generic
 222.5GB: boot/vmlinuz-2.6.35-22-generic
 222.5GB: boot/vmlinuz-2.6.35-24-generic
 234.3GB: initrd.img
 222.7GB: initrd.img.old
 222.5GB: vmlinuz
 222.5GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 
```

---

### Post by oldfred on 2011-01-06
+1 on presence1960 suggestions.

I have 3 or 4 partitions with versions of Ubuntu. I only for a while had a separate /home.  But once I realized how small it was it was not worth having as a separate partition, when you also have separate data partitions for all your data. I do sometimes copy a few settings from one /home to another. Swap is all I share, but I do have a swap on each drive. But if you hibernate you cannot share swap either.

Herman on advantages/disadvantges of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

---

### Post by matthanley on 2011-01-06
> **presence1960 said:**
> Usually not a good idea to share /home between distros due to the fact that a lot of settings...
Thanks to both of you for the tips. I got about this far into presence1960's reply before I had a forehead-slapping, *ah, crap, I shoulda though of that* moment.

Thanks for the link, oldfred. That's a pretty good explanation of the tradeoffs of having a lot of partitions. I always had a lot of partitions on my old computer (RIP) because, well, I've always done it that way. Reading that, though, I suppose partitioning my drives into smithereens isn't really necessary.

I have a not-very-old 400GB IDE drive that I used as /home on my old computer. I plan to reuse it on this new computer because it still works and the motherboard can support it, so why not. At this point, I'm thinking maybe:

[INDENT]Old drive, 400GB IDE
/dev/sda1: 200GB for / on standard Ubuntu
/dev/sda2: 200GB for / on Ubuntu Studio

New drive, 640GB SATA
/dev/sdb1: 4GB swap for standard Ubuntu
/dev/sdb2: 4GB swap for Ubuntu Studio
/dev/sdb3: Extended
/dev/sdb4: 200GB or so for /home on standard Ubuntu
/dev/sdb5: 200GB or so for /home on Ubuntu Studio
/dev/sdb6: ~236GB (minus overhead) for /home/<user>/shared on both distros.

(Just guessing on which will be /dev/sda and which will be /dev/sdb, but the point is the same either way.)[/INDENT]

This way, I'll have the swap partitions and /home on the new, sexy, faster drive, and I'll still have the option to screw around with the system configuration to my heart's content and not risk screwing up my data (much).

If you guys have thoughts on that, I'd love to hear them.

---

### Post by oldfred on 2011-01-06
One nice thing about Ubuntu is that it is easy to install and not difficult to reconfigure if you have hard drive space. There is no one right way, each of us have different opinions and how you use system and what you plan on doing will make a difference on what  is "right" for you.

I had just root & swap with with a shared (now NTFS) partition as I am dual booting XP. After upgrading in place for a couple of years I decided to do a clean install (and new drive so lots of new room). I moved my /home into a nice new partition, but then decided if I wanted to experiment with other installs a /data would be better. After I moved all my data out of /home it was about 1GB. I aggressively moved data folders, but not any settings out of /home.

I also like to have a complete system on each drive so I can boot something in case a drive has issues. By complete I mean all system folders, swap & the MBR. 

I might make root partitions smaller. I use 20-25GB but even with lots of apps have not used more than 6GB (now with /home also). I figure 4GB for /tmp if writing a DVD, so I never have used more than half of root.

Going with presence1960's backup ideas, you might want to have partitions on each drive for back of data from the other drive. I do not backup system, as I assume I will reinstall, but backup data, /home, copy any manually configured file in /etc to /home so it is backed up. I also export a list of installed apps using dpkg & a run of bootinfoscript so I have a system config available if need be.

---

### Post by matthanley on 2011-01-08
Well, I'm still deciding exactly how I want to set it up, but your advice got me going in the right direction.

Thanks a million!

---

