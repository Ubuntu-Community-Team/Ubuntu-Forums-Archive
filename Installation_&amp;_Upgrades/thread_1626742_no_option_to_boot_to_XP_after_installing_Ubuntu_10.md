---
title: "no option to boot to XP after installing Ubuntu 10.04"
date: 2010-11-20
forum: Installation &amp; Upgrades
---

### Post by alex842 on 2010-11-20
Hello,

I've just installed ubuntu 10.04 onto my machine previously running only windows XP, however when I boot it loads straight into Ubuntu with no option of booting XP. Here are a few details of my system:

- The HD was partitioned into 2 parts. XP was installed first on one partition, and Ubuntu on the other.

- From Ubuntu i can still access files from the XP partition and the XP partition is still the same size so i'm sure i've not accidentally copied over it with Ubuntu!

- My system has an additional HD for storage only (C:) with the 2 o/s installed on the F:

I'm still quite new to linux so not sure how to fix this! In the past I have installed Ubuntu onto an XP machine and have always had a boot menu appear at startup giving options for which o/s to log into. I'd be really grateful for some help from the experts!

many thanks,
Alex

---

### Post by bcbc on 2010-11-20
First thing, boot Ubuntu and run "sudo update-grub" from the terminal (CTRL+ALT+t)

You can see from the output whether it finds Windows or not. Or reboot to make sure.

If not, then download and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net") and post the results back.

---

### Post by alex842 on 2010-11-20
Thanks for such a quick reply

updating grub did not find XP, however running the script did. Here is the output:


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd
 => Windows is installed in the MBR of /dev/mapper/isw_eciefgaaai_1.5TB_RAID1

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

isw_eciefgaaai_1.5TB_RAID11: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sde: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63 2,930,272,064 2,930,272,002   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   655,387,739   655,387,677   7 HPFS/NTFS
/dev/sdc2         655,388,670   976,773,119   321,384,450   5 Extended
/dev/sdc5         655,388,672   963,645,439   308,256,768  83 Linux
/dev/sdc6         963,647,488   976,773,119    13,125,632  82 Linux swap / Solaris


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 8589 MB, 8589934080 bytes
255 heads, 63 sectors/track, 1044 cylinders, total 16777215 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


Drive: isw_eciefgaaai_1.5TB_RAID1 ___________________ _____________________________________________________

Disk /dev/mapper/isw_eciefgaaai_1.5TB_RAID1: 1500.3 GB, 1500299530240 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930272520 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/isw_eciefgaaai_1.5TB_RAID11                 63 2,930,272,064 2,930,272,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/isw_eciefgaaai_1.5TB_RAID11 942C17D92C17B4E8                       ntfs       1.5TB_MOVIES                  
/dev/mapper/isw_eciefgaaai_1.5TB_RAID1: PTTYPE="dos" 
/dev/sda                                                isw_raid_member                               
/dev/sdb                                                isw_raid_member                               
/dev/sdc1        C410B32610B31E7C                       ntfs                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        8e24e90a-dca3-4afa-8c08-36d60376416b   ext4                                     
/dev/sdc6        a21dfd42-cacb-4d51-bf20-8baa3472aeb2   swap                                     
/dev/sdc: PTTYPE="dos" 
/dev/sde         6355-4BC5                              vfat                                     
error: /dev/sda1: No such file or directory

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
isw_eciefgaaai_1.5TB_RAID1
isw_eciefgaaai_1.5TB_RAID11

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdc5        /                        ext4       (rw,errors=remount-ro)
/dev/sde         /media/6355-4BC5         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sdc5/boot/grub/grub.cfg: ===========================

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
set root='(hd2,5)'
search --no-floppy --fs-uuid --set 8e24e90a-dca3-4afa-8c08-36d60376416b
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
set root='(hd2,5)'
search --no-floppy --fs-uuid --set 8e24e90a-dca3-4afa-8c08-36d60376416b
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 8e24e90a-dca3-4afa-8c08-36d60376416b
    linux    /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=8e24e90a-dca3-4afa-8c08-36d60376416b ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 8e24e90a-dca3-4afa-8c08-36d60376416b
    echo    'Loading Linux 2.6.32-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=8e24e90a-dca3-4afa-8c08-36d60376416b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 8e24e90a-dca3-4afa-8c08-36d60376416b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd2,5)'
    search --no-floppy --fs-uuid --set 8e24e90a-dca3-4afa-8c08-36d60376416b
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
### END /etc/grub.d/40_custom ###

=============================== sdc5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdc5 during installation
UUID=8e24e90a-dca3-4afa-8c08-36d60376416b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
UUID=a21dfd42-cacb-4d51-bf20-8baa3472aeb2 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdc5: Location of files loaded by Grub: ===================


 365.7GB: boot/grub/core.img
 445.2GB: boot/grub/grub.cfg
 365.7GB: boot/initrd.img-2.6.32-25-generic-pae
 365.7GB: boot/vmlinuz-2.6.32-25-generic-pae
 365.7GB: initrd.img
 365.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
```

---

### Post by oldfred on 2010-11-20
You said you installed windows on the same drive as Ubuntu. It shows an NTFS partition, but no boot files. Windows moves boot files to the first windows install. Were you booting thru a windows install inside the RAID? Not sure if script parses the RAID to find an install there. You may need to use windows tools to repair the windows install in sdc1, it that is a full install.

Do not know about RAID, so I cannot help on that.

---

### Post by bcbc on 2010-11-20
+1 on what oldfred said - there are no xp boot files

/dev/sda1 looks like it's got something weird in it's bootsector. It's shown as ntfs but something unknown is in it. I've seen this before when grub smears the bootsector so it might be worth running testdisk and seeing if it has a backup bootsector.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by alex842 on 2010-11-20
I think I now know what has happened..

I have a 500GB disk, partitioned into 2 parts, with XP (installed first) on the first partition and then Ubuntu on the second partition.

There is also a 1.5TB drive i use to save media files on

I think the boot files are somehow installed on the 1.5TB drive instead of the 500GB where the o/s are. A folder called 'system volume information' has appeared at the root of the 1.5TB containing files such as Mountpointmanagerremotedatabase.

If i play around with the boot order of my disk drives in bios it will only boot (to ubuntu) if i select the 1.5TB drive to boot from. If i swap the priority over to the 500GB i just get a message saying "reboot and select proper boot device or insert boot media in selected boot device and press a key"

I'm not sure what to do now.. is there any way to somehow swap the boot files over to the 500GB drive whilst logged into Ubuntu? It seems like the only other option would be to unplug all of the drives except for the 500GB and reinstall o/s again?

Any ideas?

---

### Post by oldfred on 2010-11-20
You can reinstall grub to sdc.

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sdc"  then just run:
sudo grub-install /dev/sdc
If that returns any errors run:
sudo grub-install --recheck /dev/sdc
Then:
sudo update-grub
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
spacebar to choose/unchoose drive, enter to accept, do not choose partitions, enter thru first couple screens.

---

### Post by alex842 on 2010-11-20
> **oldfred said:**
> You can reinstall grub to sdc.

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sdc"  then just run:
sudo grub-install /dev/sdc
If that returns any errors run:
sudo grub-install --recheck /dev/sdc
Then:
sudo update-grub
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
spacebar to choose/unchoose drive, enter to accept, do not choose partitions, enter thru first couple screens.

When running fdisk there does not seem to be a partition. Here is the response:

```
alex@alex-desktop:~$ sudo fdisk -l

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbf053e58

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      182401  1465136001    7  HPFS/NTFS

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbf053e59

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      182401  1465136001    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xba2eba2e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       40796   327693838+   7  HPFS/NTFS
/dev/sdc2           40797       60802   160692225    5  Extended
/dev/sdc5           40797       59985   154128384   83  Linux
/dev/sdc6           59985       60802     6562816   82  Linux swap / Solaris

Disk /dev/sdd: 8589 MB, 8589934080 bytes
255 heads, 63 sectors/track, 1044 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table

```

Thanks very much for helping me. Is there anything else I can try?

---

### Post by oldfred on 2010-11-20
We are looking for drive not partition. We want to install grub to sdc not a partition like sdc3. Then in BIOS set to boot sdc - the 500GB drive.

The instructions include the fdisk command just to verify that drive is still sdc as sometimes rebooting changes drive number.

---

### Post by alex842 on 2010-11-20
> **oldfred said:**
> We are looking for drive not partition. We want to install grub to sdc not a partition like sdc3. Then in BIOS set to boot sdc - the 500GB drive.

The instructions include the fdisk command just to verify that drive is still sdc as sometimes rebooting changes drive number.

Ok great! after running those commands to install grub to sdc and swapping bios back to the 500GB drive I have Ubuntu loading properly off the 500GB drive!

..however there is still no option to choose between Xp and Ubuntu (it loads into Ubuntu without a list of choices for operating system). Can this be resolved from inside ubuntu?

Thanks!

---

### Post by galactica48 on 2010-11-21
> **alex842 said:**
> Ok great! after running those commands to install grub to sdc and swapping bios back to the 500GB drive I have Ubuntu loading properly off the 500GB drive!

..however there is still no option to choose between Xp and Ubuntu (it loads into Ubuntu without a list of choices for operating system). Can this be resolved from inside ubuntu?

Thanks!

If I remember well, when you power on the computer, before Grub Menu starts, press and hold space bar. You should be able to see Ubuntu Menu and then you can select what operating system to boot.

---

### Post by oldfred on 2010-11-21
Your windows install in sdc1 has no boot files. Grub's osprober looks for those boot files to know what windows partition to boot.

If your sdc1 is a full windows install with /system and related folders, you can repair it with either Ubuntu or an XP install disk.

How to fix XP when the boot files are missing & info on windows in logical partitions
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
missing boot files meieifra - post 10
[http://ubuntuforums.org/showthread.php?t=1241394](http://ubuntuforums.org/showthread.php?t=1241394)

Description of the Windows XP Recovery Console for advanced users
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)

To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type this commands one at a time.

FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
or:
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 

BOOTCFG  /rebuild
[http://support.microsoft.com/kb/291980](http://support.microsoft.com/kb/291980)
[http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairbootini.htm)

Then you need to run this to get grub to find the windows install:
sudo update-grub

---

