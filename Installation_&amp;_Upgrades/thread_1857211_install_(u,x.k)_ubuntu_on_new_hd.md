---
title: "install (u,x.k) ubuntu on new hd"
date: 2011-10-09
forum: Installation &amp; Upgrades
---

### Post by larrypg on 2011-10-09
Hello all,  I have done quite a lot of reading but I am not very sure of some of the answers.  I will be installing one of the versions of 11.10 (64 bit) but not sure yet if it will be U,X, or K (probably does not matter).
 
I have done several installs but they have either been via wubi or a separate hd.  My new computer has only one hd and I want to make a real install (not wubi).  That is what brings up the questions.

The hd I am working with is 2 TB.  It is set up with three primary partitions and one that I made by shrinking the Windows 7 partition and made it an extended partition.  

The partitions are set up as follows:   sda1 39.19 MiB (fat 16 ) DellUtility, sda2 16.25 GiB (ntfs) RECOVERY(with a boot flag), sda3 1.33 Tib (ntfs) Windows 7, and the rest of the hd that I made as an extended partition of 488.28 GiB.
 
I will be making the following logical partitions (depending on the comments):  /boot(depends on if I need to), / 20 Gib, swap 12 GiB, and the rest for /home.  

The questions and comments I have (in no particular order) are as follows:

I would rather not have another program such as EasyBCD to help with the booting but I guess I will if that is best.  

Does the fact that the extended partition starts 1.5 TB from the beginning of the hd make a difference?

BIG QUESTION: Where should grub be installed to and where should the boot loader be installed to.  I am not positive that they are separate.  If GRUB2 is installed to the /boot partition (if needed)  or / partition will the bootloader installed to the MBR mess up Windows 7 booting.  

I probably have my info wrong as far as grub goes but at least it is a start for others to respond to.  

Sorry for the long post and thanks for any responses,

Larry

---

### Post by oldfred on 2011-10-10
I do not recommend a separate /boot unless you have a very old system that only boots from the first 137GB or a server like system with RAID or LVM.

If dual booting with Windows is is best to have a shared NTFS partition for any data you want in both systems. Many Windows users suggest a d: partition for data anyway so when you reinstall Windows your data is safe. Backups still required. Only mount your Windows system (c: ) partition as read only to avoid issues.

Smaller system partitions for both Windows & Linux help performance slightly on large drives as heads do not have to travel over larger partitions for the most used system files.

You only need swap equal to RAM in GiB if you want to hibernate and have 12GB of programs loaded. Most systems with over 4GB of RAM only need some swap like 2GB. Some suggest swap files also.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

We sometimes confuse users on grub install. Grub has lots of parts in different places but we usually mean the small part of grub2 that is the boot loader. It is normally installed to the MBR and loads the grub files in /boot/grub folder. You want to install to the MBR of sda.

Only if using some DRM software or a few Windows virus checkers that think grub2's boot loader in the MBR is a virus should you consider installing grub2's boot loader to the / (root) partition. It makes Windows more reliable  (but DRM has many issues)  but grub less reliable. Updates to grub often then require you to reinstall grub2's boot loader to the partition. And you still have to install a third party boot loader like EasyBCD.

 GRUB 2 - GRand Unified Bootloader has three main parts plus a boot loader installed to the MBR:

   1. /etc/default/grub - the file containing GRUB 2 menu settings.
   2. /etc/grub.d/ - the directory containing GRUB 2 menu creating scripts.And a place for totally custom entries 40_custom.
   3. /boot/grub/grub.cfg - the GRUB 2 configuration file, not editable.

Also make a Windows repairCD and have good backups before starting anything. Best to have Vendor recovery DVDs and full system backup.

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by larrypg on 2011-10-12
Thanks for the response.  I have a recovery cd and since the computer is so new there is not really anything that is essential.  I will include the Boot Info Script here just to see if anyone can see potential problems.  The wubi part will not be in it as I will be deleting that before I install to the extended partition.

```
                   Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda3/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920    34,156,543    34,074,624   7 NTFS / exFAT / HPFS
/dev/sda3          34,156,544 2,883,026,943 2,848,870,400   7 NTFS / exFAT / HPFS
/dev/sda4       2,883,026,944 3,907,028,991 1,024,002,048   5 Extended
Empty Partition.


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0       cc682d7c-629a-4017-b186-e8f1a30f7ac4   ext4       
/dev/sda1        5450-4444                              vfat       DellUtility
/dev/sda2        88AAC68AAAC6746A                       ntfs       RECOVERY
/dev/sda3        C8F2C903F2C8F72A                       ntfs       OS

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda3        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


======================== sda3/Wubi/boot/grub/grub.cfg: =========================

--------------------------------------------------------------------------------
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
true
}

insmod part_msdos
insmod ntfs
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root C8F2C903F2C8F72A
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.38-11-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root C8F2C903F2C8F72A
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=C8F2C903F2C8F72A loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, Linux 2.6.38-11-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root C8F2C903F2C8F72A
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-11-generic root=UUID=C8F2C903F2C8F72A loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.38-11-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root C8F2C903F2C8F72A
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=C8F2C903F2C8F72A loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root C8F2C903F2C8F72A
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=C8F2C903F2C8F72A loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos2)'
    search --no-floppy --fs-uuid --set=root 88AAC68AAAC6746A
    chainloader +1
}
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
--------------------------------------------------------------------------------

============================= sda3/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------

================= sda3/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

  20.154464722 = 21.640691712   boot/grub/grub.cfg                             1
   1.629459381 = 1.749618688    boot/initrd.img-2.6.38-11-generic              2
   1.035671234 = 1.112043520    boot/initrd.img-2.6.38-8-generic               1
   0.980781555 = 1.053106176    boot/vmlinuz-2.6.38-11-generic                 1
  26.326114655 = 28.267450368   boot/vmlinuz-2.6.38-8-generic                  1
   1.629459381 = 1.749618688    initrd.img                                     2
   1.035671234 = 1.112043520    initrd.img.old                                 1
   0.980781555 = 1.053106176    vmlinuz                                        1
  26.326114655 = 28.267450368   vmlinuz.old                                    1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 


    
```

---

### Post by oldfred on 2011-10-12
I have a bunch of / (root) partitions of 20 to 25GB. I boot Maverick as my working system but have Natty & Oneiric. I still have my old installs as working / and a new install of Kubuntu. One or two others for Puppy and maybe something totally else.

If using Windows a lot you should have the shared NTFS partition and only set sda3 (c: ) partition as read only if you mount it at all. That avoids some Windows issues.

If storing most of your data in a shared partition you do not need much /home and/or then it can be in a slightly larger /. I keep /home in / but am very aggressive in moving all my data files to either /mnt/shared (NTFS) or /mnt/data(ext3) partitions even some hidden folders like the Filefox & Thunderbird profiles which I shared with Windows XP. Since using XP so little now I use the shared less, but still have my profiles in the shared partition. My /home is about 1GB with most of that .wine for Picasa.

---

