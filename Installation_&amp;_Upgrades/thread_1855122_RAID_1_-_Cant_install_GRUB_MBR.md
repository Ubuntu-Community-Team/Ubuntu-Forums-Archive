---
title: "RAID 1 - Cant install GRUB MBR"
date: 2011-10-05
forum: Installation &amp; Upgrades
---

### Post by Keypen on 2011-10-05
Im trying to install Ubuntu 11.04 64bit to a AMD Llano platform. The drives are two Samsung Ecogreen F4 2TB drives and I want to use RAID 1.

I partition the drives with Gpareted from the Live CD because I want system partition at 50GiB (Not 49, 52,4GiB or other size *), swap at 10GiB and the rest for /home.

The run alternative-CD, creates the MD things. MD0=system, MD1=swap, MD2=/home

It installs without any problems but when it is going to install Grub in the MBR I get this error:
> Unable to install GRUB in /dev/sdb
Executing 'grub-install /dev/sdb/ failed.

This is a fatal error.I did a little search and found this:
[http://ubuntuforums.org/archive/index.php/t-1559762.html](http://ubuntuforums.org/archive/index.php/t-1559762.html)

I complete the installation of Ubuntu without installing Grub to MBR, reboot and jump in to rescue mode på skivan. I run the command BLKID but i do not get any /dev/mapper but my three /dev/md0 /dev/md1 /dev/md2

I then try to install grub with a command but get a error message: grub-install --root-directory=/ /dev/md0
> /usr/sbin/grub-setup: warn: Attempting to install GRUB to a partitionless disk or to a partition. This is a BAD idea..
/usr/sbin/grub-setup: error: embedding is not possible, but this is required when the root device is on a RAID array or LLVM volume.I have no idea how to fix this. Can the problem be the AMDs Llano platform?

I have tested with a small system partiton at 10GB and a swap at 4GB created in the installation program but the exact same error.

I cant make the MD things bootable. I cant give them bootable flag in Ubuntu installation program.




(* Ubuntu and Mac OS X show the wrong size. Nag nag nag... Is their a way to fix this in Ubuntus installation program and everywhere ells in Ubuntu?)

---

### Post by YannBuntu on 2011-10-07
Hello
Please can you indicate your Boot-Info Summary URL ? ( [http://ubuntuforums.org/showthread.php?t=1821980](http://ubuntuforums.org/showthread.php?t=1821980) )

---

### Post by skrieder on 2011-10-07
I'm in the same boat. Raid 1 on two 1GB drives.

I get the same error when I try and install grub to the /dev/mapper/pdc_gbbgfbfjb2



                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => MS-DOS 3.30 through Windows 95 (A) is installed in the MBR of /dev/sdc.
 => No boot loader is installed in the MBR of /dev/mapper/pdc_gbbgfbfjb.

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

pdc_gbbgfbfjb1: ________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

pdc_gbbgfbfjb5: ________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

pdc_gbbgfbfjb2: ________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab /boot/grub/core.img

pdc_gbbgfbfjb3: ________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 2003 MB, 2003828736 bytes
64 heads, 63 sectors/track, 970 cylinders, total 3913728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                 129     3,907,007     3,906,879   6 FAT16


Drive: pdc_gbbgfbfjb _____________________________________________________________________

Disk /dev/mapper/pdc_gbbgfbfjb: 1000.0 GB, 999999995904 bytes
255 heads, 63 sectors/track, 121576 cylinders, total 1953124992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/pdc_gbbgfbfjb1              2,046    78,125,055    78,123,010   5 Extended
/dev/mapper/pdc_gbbgfbfjb5              2,048    78,125,055    78,123,008  82 Linux swap / Solaris
/dev/mapper/pdc_gbbgfbfjb2         78,125,056 1,562,499,071 1,484,374,016  83 Linux
/dev/mapper/pdc_gbbgfbfjb3      1,562,499,072 1,953,124,351   390,625,280   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/pdc_gbbgfbfjb2 fbf29a41-655c-4f41-8e87-0ee25efafba7   ext4       
/dev/sda                                                promise_fasttrack_raid_member 
/dev/sdb                                                promise_fasttrack_raid_member 
/dev/sdc1        0260-087A                              vfat       

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
pdc_gbbgfbfjb
pdc_gbbgfbfjb2
pdc_gbbgfbfjb3
pdc_gbbgfbfjb5

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/0260-087A         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


========================== pdc_gbbgfbfjb2/etc/fstab: ===========================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/pdc_gbbgfbfjb2 /               ext4    errors=remount-ro 0       1
/dev/mapper/pdc_gbbgfbfjb5 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

============== pdc_gbbgfbfjb2: Location of files loaded by Grub: ===============

           GiB - GB             File                                 Fragment(s)

 457.386955261 = 491.115503616  boot/grub/core.img                             1
 385.526367188 = 413.955784704  boot/initrd.img-2.6.38-8-generic               2
 457.385746002 = 491.114205184  boot/vmlinuz-2.6.38-8-generic                  1
 385.526367188 = 413.955784704  initrd.img                                     2
 457.385746002 = 491.114205184  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on pdc_gbbgfbfjb1



=============================== StdErr Messages: ===============================

hexdump: /dev/mapper/pdc_gbbgfbfjb1: No such file or directory
hexdump: /dev/mapper/pdc_gbbgfbfjb1: No such file or directory

---

### Post by Keypen on 2011-10-07
I got this answer:
[http://paste.ubuntu.com/704164/](http://paste.ubuntu.com/704164/)

This is the test of 10GB system and 4GB swap. I cant install GRUB in the MBR here either.

When I can this command the program locked at "Enable RAID.". It flooded the terminal Windows with a command i do not remember. I tried to close the program but then it started loading something ells. Boot-Info started:
```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update && sudo apt-get install -y boot-repair && gksu boot-repair
```

---

### Post by YannBuntu on 2011-10-08
Hello
Boot-Repair worked well, the behavior you saw is normal (the command line flood you saw corresponds to the pulse while Boot-Repair gets updated).

> **Keypen said:**
> I got this answer:
[http://paste.ubuntu.com/704164/](http://paste.ubuntu.com/704164/)

Boot-Repair detects an OS on /dev/md126, so if you click on the "Recommended repair" button, it will reinstall the GRUB of /dev/md126. The problem is that GRUB does not see any OS (os-prober does not detect any OS), so your GRUB menu will be empty.
Maybe you could try it, then add manually an entry for your OS in the GRUB menu (see [https://help.ubuntu.com/community/Grub2#Custom_Menu_Entries](https://help.ubuntu.com/community/Grub2#Custom_Menu_Entries) )

---

### Post by Quackers on 2011-10-08
skrieder, install grub to /dev/mapper/pdc_gbbgfbfjb not /dev/mapper/pdc_gbbgfbfjb2

---

### Post by Keypen on 2011-10-09
> **YannBuntu said:**
> Hello
Boot-Repair worked well, the behavior you saw is normal (the command line flood you saw corresponds to the pulse while Boot-Repair gets updated).



Boot-Repair detects an OS on /dev/md126, so if you click on the "Recommended repair" button, it will reinstall the GRUB of /dev/md126. The problem is that GRUB does not see any OS (os-prober does not detect any OS), so your GRUB menu will be empty.
Maybe you could try it, then add manually an entry for your OS in the GRUB menu (see [https://help.ubuntu.com/community/Grub2#Custom_Menu_Entries](https://help.ubuntu.com/community/Grub2#Custom_Menu_Entries) )
I tried this and the system still stoppes at the boot.

I "fixed" the boot with Boot-Info (It said it was fixed...) and added this to /boot/grub.d/grub.cfg (/media/system/boot/grub.d/grub.cfg under Live CD with mdadm and other stings loaded) BUT with my personal touch as correct kernel and uuid number.
```
menuentry "My Default Karmic" {
set root=(hd0,1)
search --no-floppy --fs-uuid --set cb201140-52f8-4449-9a95-749b27b58ce8
linux /boot/vmlinuz-2.6.31-11-generic root=UUID=cb201140-52f8-4449-9a95-749b27b58ce8 ro quiet splash
initrd /boot/initrd.img-2.6.31-11-generic
}
```But the system still stops at boot with that annoying blinking underscore.

I remember somewhere that I should edit /etc/grub/40_custom and then run "sudo update-grub" to generate /boot/grub.d/grub.cfg but that do not work cause I run the Live CD and that tries to generate /boot/grub.d/grub.cfg and not /media/system/boot/grub.d/grub.cfg. But it gave me some error in the terminal that looked like a error in the program or error because it was running from Live CD.

I remember that I did see somewhere that "set root=(hd0,1)" should be "set root=(md0,1)" for RAID but it feels wrong for me. I even tested it and it didnt work.

I have no idea what to do now, again.

---

### Post by Wednesday on 2011-10-09
I am having similar problems. I need help. I have made a fresh install from the alternate CD and have set up a raid 1 array with my first two disks. (Please ignore the other disks - one is blank and the other came with the dell machine). 
I created a set of identical partitions on the first two disks and then assembled the raid1 arrays. The Installation fails 
"unable to install grub in /dev/sda  
executing 'grub-install /dev/sda' failed".
I then booted into the repair disk and tried the following command:
grub-install --root-directory=/ /dev/md0

This failed with the following:

/usr/sbin/grub-setup: error:unable to identify a filesystem in /dev/sda; safety check can't be performed.

/dev/mapper seemed to only contain control and nothing else

I tried to follow the suggestion:
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update && sudo apt-get install -y boot-repair && gksu boot-repair
but a window appeared showing
" Enabling RAID. This may require several minutes" bit it did not stop ( I waited 20 mins).

I attach my message.txt from the boot_info_script
Please can somebody help me?
Thanks

---

### Post by YannBuntu on 2011-10-09
**@Keypen:** sorry i don't know how to solve this. Please wait for someone-else advice.
[B]
@Wednesday:[/B] please create a new thread and indicate its URL here. (so that we don't mix with Keypen's problem).

---

### Post by Wednesday on 2011-10-09
Hi Yannubuntu
I have reposted at
[http://ubuntuforums.org/showthread.php?p=11325166#post11325166](http://ubuntuforums.org/showthread.php?p=11325166#post11325166)
Thanks

---

