---
title: "not booting with 2nd drive"
date: 2010-12-19
forum: Installation &amp; Upgrades
---

### Post by kapochek on 2010-12-19
I have been having trouble with my latest LinuxMCE core server (based on  Kubuntu 8.10). It will load the OS with no problems on the IDE drive,  unless I have another, or multiple, hard drive installed. It doesn't  matter if I loaded onto the IDE or SATA drives, it gives me the "ALERT!  /dev/disk/by-uuid....does not exist. Dropping to shell." I thought it  might be the loader, as just to get it into 'live' mode I need to enter  'pci=nomsi'. I tried to load Fedora (to try AMAHI), but it just sent me  into a grub loop. If I try to have the second disk installed while  running the install, it gets frozen at the busybox. The whole reason for  going to this combo of system and OS was to be able to have multiple  pci/e cards for security, TV tuning, etc, and have a minimum of 8TB  onboard which can stay on 24/7/365. 120 gig just won't cut it!
Basic system:
XFX 750a motherboard, nvidia 8200 graphics, onboard sound LAN sata raid, etc
AMD BE-2300 DualCore @1900mhz
Trendnet teg-pcitxr Gig LAN card (need two LAN for MCE)
Seagate st332000542as hard drive (unformatted, plan to use as storage)
WD1200 PATA drive/ WD1200 7200rpm laptop SATA that I'm trying to use as / (one at a time!)
Samsung external DVD to load OS

I hope to eventually use the laptop drive as the root to keep running costs down. 
Any help would be appreciated, as I'm going crazy and had to trim my hair to keep from pulling any more out!!

---

### Post by oldfred on 2010-12-19
Welcome to the forum.

Can you boot with both drives installed, if you use liveCD? We would prefer to see all the drives info from this script.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by kapochek on 2010-12-20
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/mapper/pdc_chaaaiige and looks 
    on the same drive in partition #1 for /boot/grub/stage2 and 
    /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: /dev/sda1 already mounted or sda1 busy

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

pdc_chaaaiige1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

pdc_chaaaiige2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

pdc_chaaaiige5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   224,829,674   224,829,612  83 Linux
/dev/sda2         224,829,675   234,436,544     9,606,870   5 Extended
/dev/sda5         224,829,738   234,436,544     9,606,807  82 Linux swap / Solaris


Drive: pdc_chaaaiige ___________________ _____________________________________________________

Disk /dev/mapper/pdc_chaaaiige: 120.0 GB, 120034033664 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441472 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/pdc_chaaaiige1                 63   224,829,674   224,829,612  83 Linux
/dev/mapper/pdc_chaaaiige2        224,829,675   234,436,544     9,606,870   5 Extended
/dev/mapper/pdc_chaaaiige5        224,829,738   234,436,544     9,606,807  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/pdc_chaaaiige1 206a66a3-5899-4f75-b293-f919c5a0d929   ext3                                     
/dev/mapper/pdc_chaaaiige5 3926f7de-5353-4b56-b5f5-aa206e7c924c   swap                                     
/dev/mapper/pdc_chaaaiige: PTTYPE="dos" 
/dev/sda1        206a66a3-5899-4f75-b293-f919c5a0d929   ext3                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        3926f7de-5353-4b56-b5f5-aa206e7c924c   swap                                     
/dev/sda                                                promise_fasttrack_raid_member                               
error: /dev/mapper/pdc_chaaaiige2: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


====================== pdc_chaaaiige1/boot/grub/menu.lst: ======================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=206a66a3-5899-4f75-b293-f919c5a0d929 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=206a66a3-5899-4f75-b293-f919c5a0d929

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		206a66a3-5899-4f75-b293-f919c5a0d929
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=206a66a3-5899-4f75-b293-f919c5a0d929 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		206a66a3-5899-4f75-b293-f919c5a0d929
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=206a66a3-5899-4f75-b293-f919c5a0d929 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		206a66a3-5899-4f75-b293-f919c5a0d929
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

========================== pdc_chaaaiige1/etc/fstab: ==========================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=206a66a3-5899-4f75-b293-f919c5a0d929 /               ext3    relatime,errors=remount-ro,user_xattr 0       1      
# /dev/sdb5
UUID=3926f7de-5353-4b56-b5f5-aa206e7c924c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

============== pdc_chaaaiige1: Location of files loaded by Grub: ==============


  54.5GB: boot/grub/menu.lst
  54.6GB: boot/grub/stage2
  54.6GB: boot/initrd.img-2.6.27-7-generic
  54.6GB: boot/vmlinuz-2.6.27-7-generic
  54.6GB: initrd.img
  54.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on pdc_chaaaiige2



=============================== StdErr Messages: ===============================

hexdump: /dev/mapper/pdc_chaaaiige2: No such file or directory
hexdump: /dev/mapper/pdc_chaaaiige2: No such file or directory

```

here is the results as requested, live CD takes way too long to get anything done, tried to download script for over an hour, and just doing this reply has been another 30min. need sleep....

---

### Post by oldfred on 2010-12-20
Are you using LVM or RAID. I am not really familiar with either. 

But it is saying your LVM mapper is missing this:

/dev/mapper/pdc_chaaaiige2

---

### Post by kapochek on 2010-12-24
The BIOS was set at 'ahcp mode, with linux did enabled' I didn't want to enable RAID as I was planning to run different sized drives and don't want to lose disk space. I went with ahcp because of the NCQ and hot swap capabilities.
From what I see, the sda1 drive is the IDE drive and the  sdb1:pdc_chaaaiige2 is the SATA drive. I never got the SATA drive to  fully load an OS, so that may be why that 2nd partition was coming up missing.  What still makes no sense, the 2TB SATA drive was also connected, but  wasn't found. My problems still stand... if any SATA drives are  installed, the OS will not load.
Is there a possibility that the SATA  driver is not being loaded/ not in the kernel or that the driver is  wrong for this chipset? I think I read in another forum (months ago and  can't find it now) that the Nvidia 750a/ 8200 chips weren't working with  the standard nv driver that gets auto-loaded. If so, where can I find  the proper driver/ kernel?
 BTW, I was finally able to get Fedora to  install properly by using a new SATA DVD and setting the SATA to 'SATA' which supposedly runs it in IDE mode. I will try to install Kubuntu again in this fashion  today, as I really wish to get this system running ASAP! Thanks in  advance for your help.

---

### Post by kapochek on 2010-12-24
I tried to install Kubuntu 10.04LTS to the SATA 1200 drive without the IDE disk installed and all other variables thesame as the previous Fedora install. When rebooted, gave the same fail as before. Ran the script again with these results:                                
```

Boot Info Script 0.55    dated February 15th, 2010                    
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
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

/dev/sda1    *             63   224,829,674   224,829,612  83 Linux
/dev/sda2         224,829,675   234,436,544     9,606,870   5 Extended
/dev/sda5         224,829,738   234,436,544     9,606,807  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 3,907,024,064 3,907,024,002  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 8457 MB, 8457814016 bytes
70 heads, 1 sectors/track, 235988 cylinders, total 16519168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *            264    16,519,167    16,518,904   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        75a8dc0c-189c-44f5-91d3-347558a58253   ext3                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        67565d4a-0fa4-4236-8a86-0b74ea6c438d   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        f8ddb5d0-dce5-4dfd-a634-84e85fd62c50   ext3                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        7496-E4B2                              vfat       LINUXMCE                      
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/disk              ext3       (rw,nosuid,nodev,uhelper=hal)
/dev/sda1        /media/disk-1            ext3       (rw,nosuid,nodev,uhelper=hal)


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=75a8dc0c-189c-44f5-91d3-347558a58253 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=75a8dc0c-189c-44f5-91d3-347558a58253

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		75a8dc0c-189c-44f5-91d3-347558a58253
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=75a8dc0c-189c-44f5-91d3-347558a58253 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		75a8dc0c-189c-44f5-91d3-347558a58253
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=75a8dc0c-189c-44f5-91d3-347558a58253 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		75a8dc0c-189c-44f5-91d3-347558a58253
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=75a8dc0c-189c-44f5-91d3-347558a58253 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=67565d4a-0fa4-4236-8a86-0b74ea6c438d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  29.2GB: boot/grub/menu.lst
  29.2GB: boot/grub/stage2
  29.1GB: boot/initrd.img-2.6.27-7-generic
  29.2GB: boot/vmlinuz-2.6.27-7-generic
  29.1GB: initrd.img
  29.2GB: vmlinuz

```

Sorry if the code fill didn't work, but the # on the panel wouldn't work and everything is working too slowly to retry anything. The sdc showing is a USB flash drive I used to transfer the script from another computer to this one. I guess now the 2nd SATA drive is working now too. 
Seeing all partitions showing and still getting the same results while booting, leading me to driver issue. Any ideas out there?!

---

### Post by oldfred on 2010-12-24
This discusses some of the issues.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix)

You new boot script does not show an install in sdb. Is this a copy from before you ran it.

We have seen some with very large drives and only one partition have some grub issues. I would try a much smaller root partition of 20 or 25GB and then make the rest of sdb into /home or even more data partitions.

---

### Post by kapochek on 2010-12-25
The thread you sent me to had nothing to do with my problem, although some of the symptoms were similar. I tried run the blkid_debug, but it wouldn't run due to the "p" not being a valid option. I ran it without the '-p' and got no response. So for S&G I ran the hexdump @ 0x410 and the results were:
0000410  1ff5
0000412
That's telling me this bug is apparently not the issue with this install.

In the second bootscript the drives are rearranged due to removing the IDE drive from the system (needed it for a Media Director for another room). In this script the sda is the 1200Gb SATA drive (boot/ OS/ app) and the sdb is the 2Tb data drive (no boot nor OS). 

 I really don't have the option for making the root partition smaller, as the LinuxMCE uses a lot of space when installed with all the modules and applications I'll need running on the system once completed. I'm already looking at possibly running a PhenomII 910e to handle the workload without glitches (2.6Ghz, x4, 65w vs 2.3Ghz, x2, 45w)!

---

