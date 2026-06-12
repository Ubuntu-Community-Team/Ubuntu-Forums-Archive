---
title: "Install issues 12.04"
date: 2012-10-28
forum: Installation &amp; Upgrades
---

### Post by keheikev on 2012-10-28
I am in a similar fix trying to install ubuntu 12.04 but now getting error 55. Should I go with the live disk on my install disk in order to run the above file from the former case? Not the lilo install. I do not know how to use a file in a live cd situation.
regards
:kihei

---

### Post by oldfred on 2012-10-28
Moved to your own thread. The thread you were in was 2 years old, so does not apply to your issues. 

Not familiar with error 55?

Were are you at? Have you installed, what system and what do you currently have installed. 
Run liveCD and post this first from terminal, you can just copy & paste into a new message.

```
sudo fdisk -lu
```

---

### Post by keheikev on 2012-11-02
I will hand copy the output from
sudo fdisk -lu 

Not sure how to run the live disk as I downloaded the install disk. It doesn't explictly say live disk but I guess its just the try ubuntu choice. 

The system is very similar to the thread involving upgrading to a two hdd system. I had done a full windows 7 install on the terabyte drive and then reinstalled 10.04 on the two drive system.
Now I am trying to install ubuntu 12.04
 Error 55 from what I have gathered is when grub is having trouble as to where to put the master boot record? 
Kevin

---

### Post by oldfred on 2012-11-02
If you have the Desktop version it is a liveCD or USB. The alternative or server installs are not liveCDs. If you have installed download Boot-Repair to liveCD or download full RepairCD and run the BootInfo report.

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by keheikev on 2012-11-02
how can I run the terminal from the live cd for ubuntu 12.04
Kevin

---

### Post by speedwlk on 2012-11-02
Once the livecd is running in the desktop mode, you can use "Ctrl+Alt+T" combination to start a terminal.

Alternatively, go to the dash on the left hand top corner and search using the keyword "terminal".

Hope it helps.

---

### Post by keheikev on 2012-11-02
> **speedwlk said:**
> Once the livecd is running in the desktop mode, you can use "Ctrl+Alt+T" combination to start a terminal.

Alternatively, go to the dash on the left hand top corner and search using the keyword "terminal".

Hope it helps.
I went to the virtual console cntrl+alt+F1 so I will get back to the graphical interface using alt+F7 and cntrl+T. I would rather not try to figure out how to email the output from the command or transcribe it. I have to take a car in to autobody.
Kevin

---

### Post by keheikev on 2012-11-02
ubuntu@ubuntu:~$ SUDO FDISK -LU
SUDO: command not found
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcab10bee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   232813979   116406958+   7  HPFS/NTFS/exFAT
/dev/sda2       470238615   488392064     9076725    c  W95 FAT32 (LBA)
/dev/sda3       460503225   470238614     4867695    5  Extended
/dev/sda4       232813980   460503224   113844622+  83  Linux
/dev/sda5       460503288   470238614     4867663+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xff296f63

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   841279535   420638744    7  HPFS/NTFS/exFAT
/dev/sdb2       841281534  1953523711   556121089    5  Extended
/dev/sdb5      1466525696  1947236351   240355328   83  Linux
/dev/sdb6      1947238400  1953523711     3142656   82  Linux swap / Solaris
/dev/sdb7       841281536  1466525695   312622080   83  Linux

Partition table entries are not in disk order

---

### Post by oldfred on 2012-11-02
You have two drives. Have you tried booting in BIOS from other drive?

You show LInux partitions on both drives, do you have two different installs?

Best to post link to BootInfo report, so we can see details.

---

### Post by keheikev on 2012-11-03
I booted from the bios but now it says I have a raid system in bios. At least I know the data is accessible. It would not boot from the 0 drive grub returns error 15. From the 1 drive which is the terabyte drive I can boot.
I am not sure how to post a link here for the bootinfo. Its an hp a1620dn with 3GB of RAM.
Kevin

---

### Post by oldfred on 2012-11-03
The standard Desktop installer nor gparted work with RAID systems. Either the alternative installer or the server installer are required.

You can add RAID drivers to the desktop so you can run repairs in a liveCD mode or do some things. There are many types of RAID, so you have to use the correct tools for your version of RAID to modify partitions.

If you are not really running RAID then you have to remove RAID meta-data from the drives. Then the Desktop installer will work as it is not RAID. But BIOS should not be in RAID unless you have RAID. It should be AHCI or Large or LBA as drive setting.

Generally with drives of two different sizes you are not running RAID although some new systems have Intel SRT which uses RAID to make a SSD work with a hard drive.

If you are sure you do not have RAID.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings

---

### Post by keheikev on 2012-11-03
Wow give me a little time to digest what I can do. I know the system is from 2004 so it does not have Intel SRT. I will have a look in bios in a few minutes as I recall I activated some kind of Intel software technology that starts after the bios screen. It sounds like I need to delete the meta data.
thanks
Hope Sandy did not effect you too much.
Kevin

---

### Post by oldfred on 2012-11-03
Even with 3GB, is system so old as not to have the PAE extensions?

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)
PAE is provided by Intel Pentium Pro and above CPUs, including all later Pentium-series processors (except most 400 MHz-bus versions of the Pentium M)

---

### Post by keheikev on 2012-11-17
Do I want the ubuntuSecure remix or boot repair disk. Or the second option to go from terminal from the live cd environment?
In boot menu from bios I have a raid 1 and 0 HDD, but in setup there is no raid listed. I am only able to boot from the second drive,the newer 1 TB where 12.04 is installed.
 I believe the second install is when I formated the previous version of ubuntu as I only used it for testing and learning. It may be a second install of 12.04 however as I did install twice as GRUB was reporting error 55 and 15 so I thought that it did not work, the install that is...

Kevin

---

### Post by keheikev on 2012-11-17
So did check the BIOS settings and at some point RAID was selected as the mode for the two drives. I set it to AHCI (?) as even I know IDE isn't right. It sounds like I need to erase meta data and then I should have a grub loader with a subloader for win 7? Do I need to go outside the o/s's with live cd to do this? Also I should not have to reinstall the ubuntu 12.04 as all seems well. 
Kevin
> sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

---

### Post by oldfred on 2012-11-17
You can run Boot-Repair from an Ubuntu liveCD. You just download it into the liveCD mode. But you have to do that every time you reboot as it does not get saved.

Not sure we have determined if system is 32 bit and whether it even can run full new Ubuntu as you have to have a chip with PAE extensions now. Lubuntu or Xubuntu then would be the versions you want. I think most Pentiums were PAE, only the portable Pentium Ms are not.

---

### Post by keheikev on 2012-11-17
Intel® Pentium(R) D CPU 3.00GHz × 2 
64-bit
so I think were okay its been running win7 64 and ubuntu 10.04 64 bit

---

### Post by keheikev on 2012-11-17
eew 
Now after I changed sata mode to acpi the win 7 install will not boot. It tries a repair boot but the install hangs once I esc to select the drive and then from grub sdb1. So I changed back to raid and it runs.
Can I download and run repair boot from within the 12.04 install or do I need to be running external to OS; out at grub or live cd?
hope this makes sense...
Kevin

---

### Post by oldfred on 2012-11-17
You can run Boot-Repair from any Ubuntu you can boot.

Boot-Repair will not fix most Windows issues. With AHCI you may need to add the drivers to Windows 7 before changing to AHCI in BIOS. 
XP does not have an easy way to install AHCI drivers as it just about has to be done as part of a new install.

---

### Post by keheikev on 2012-11-18
Here is the boot info report link.
[http://paste.ubuntu.com/1367672/](http://paste.ubuntu.com/1367672/)

---

### Post by oldfred on 2012-11-18
I think your original issue of error 55 is from grub legacy in sda. Grub legacy uses error codes, I had not seen codes over 20 something so did not recognize it right away. 

If you can boot from sdb does not system work ok? 

You do have 3 Windows & 3 Ubuntu's. It looks like you installed Windows to sdb but had booting set from sda, so Windows 7 put its boot files in sda1. Then somewhere you installed grub legacy to the MBR of sda. 

I might put a Windows boot loader in sda and have grub2 for which every Ubuntu you want to boot in sdb and set BIOS to boot from sdb. Then if an issue you might be able to boot from sda.

---

### Post by keheikev on 2012-11-20
Yes the system works great from sdb, I have to hold down the esc key everytime I boot however.  With windows thats more than weekly:(.
 I can't see how the sata mode could change from acpi to raid. If I were in a raid system would I not be able to see the contents of the 250 GB mirror?
I am surmising that the raid mode is just a set of protocols and really only is raid setting is only a building block of the software raid.
When I change back to acpi and esc to the boot menu it gives the drives in a list not the raid 0 and raid 1 listing. Yes I know I have win 7 on sdb but I dont think its mbr is on sda as it was totally a separate install. 
I think the legacy grub may have been installed from an older version of ubuntu like 6.0 that was upgraded thru a couple versions. 
I do not know how to>  might put a Windows boot loader in sda and have grub2 for which every Ubuntu you want to boot in sdb and set BIOS to boot from sdb. Then if an issue you might be able to boot from sda.
Do you think it would be worth a shot to do the recommended fixes from boot repair?
Basically the changes to the system was the clean install of ubuntu 12.04 directed to the old 10.014 partition. I would like to not have to go to bios or boot menu every startup.
Again I dont think an install would change a sata mode setting but then again what a long strange road its been.
Kevin

---

### Post by oldfred on 2012-11-20
Boot-Repair seems to offer several choices. Install grub to all MBR, or Windows to one.

I would install grub to sdb and install Windows (or syslinux which is a Windows like boot loader) to sda. Then set BIOS to boot from sdb.

What setting is BIOS in for drive access? RAID, IDE, Large or LBA or AHCI? Best not to use RAID nor IDE.

---

### Post by keheikev on 2012-11-20
> **oldfred said:**
> 

I would install grub to sdb and install Windows (or syslinux which is a Windows like boot loader) to sda. Then set BIOS to boot from sdb.
So use boot repair to set the grub to sdb and install the windows to sda?Why have the o/s on one drive and the bootloader on the smaller sda drive? I think my bios just boots from drive [name] not from what the o/s call them.In order to install the windows boot mess I think I would have to reinstall or repair install windows? or use boot repair...

> **oldfred said:**
> What setting is BIOS in for drive access? RAID, IDE, Large or LBA or AHCI? Best not to use RAID nor IDE.
Its the RAID setting in BIOS could an ubuntu install have selected that? The original 250 gb drive that came with the hp is a sata drive.
Kevin

---

### Post by keheikev on 2012-11-20
Or maybe I just need to remove some meta data per presence thread.

---

### Post by oldfred on 2012-11-20
If you used the RAID at all you should remove the RAID meta-data. I do not think running those commands if you do not have RAID change anything else.

I always suggest with multiple drives to install different operating systems on each drive and have that systems boot loader on the same drive. Then when, not if, one drive fails you can still change boot order to boot the other drive. And since grub allows you to boot multiple installs change BIOS to boot with grub as the default.

Operating system installs do not change BIOS settings. A BIOS update will change settings back to default. I lost some settings so last time I updated BIOS I used Camera to take screenshots of every screen.

Some info on how BIOS & Windows boot. Grub does not use PBR or partition boot sector.
       Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by keheikev on 2012-11-22
> **oldfred said:**
>  I do not think running those commands if you do not have RAID change anything else. ??

I always suggest with multiple drives to install different operating systems on each drive and have that systems boot loader on the same drive. Then when, not if, one drive fails you can still change boot order to boot the other drive. And since grub allows you to boot multiple installs change BIOS to boot with grub as the default.

Some info on how BIOS & Windows boot. Grub does not use PBR or partition boot sector.
       Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
What a gem what a gem what a gem Happy Thanksgiving. I did apply the default repairs from boot repair it did say the mbr was quite far from sda where the new install lives.

Ubuntu Pastebin
[http://paste.ubuntu.com/1378552/](http://paste.ubuntu.com/1378552/)
```
Paste from boot-repair at Fri, 23 Nov 2012 02:09:21 +0000
Download as text

========================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 7 for /boot/grub.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos7)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda4: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   232,813,979   232,813,917   7 NTFS / exFAT / HPFS
/dev/sda2         470,238,615   488,392,064    18,153,450   c W95 FAT32 (LBA)
/dev/sda3         460,503,225   470,238,614     9,735,390   5 Extended
/dev/sda5         460,503,288   470,238,614     9,735,327  82 Linux swap / Solaris
/dev/sda4         232,813,980   460,503,224   227,689,245  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   841,279,535   841,277,488   7 NTFS / exFAT / HPFS
/dev/sdb2         841,281,534 1,953,523,711 1,112,242,178   5 Extended
/dev/sdb5       1,466,525,696 1,947,236,351   480,710,656  83 Linux
/dev/sdb6       1,947,238,400 1,953,523,711     6,285,312  82 Linux swap / Solaris
/dev/sdb7         841,281,536 1,466,525,695   625,244,160  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        DC4892E04892B92A                       ntfs       HP_PAVILION
/dev/sda2        4B6E-6BC0                              vfat       HP_RECOVERY
/dev/sda4        565afa23-0885-4b73-8d72-6cdb91f4ed69   ext3       
/dev/sda5        552e4939-4fd9-4b37-a3bd-e59c47513fea   swap       
/dev/sdb1        50ECB185ECB165BE                       ntfs       
/dev/sdb5        2023e0da-16ca-4474-9540-d1b7c0bd1dda   ext4       
/dev/sdb6        667f9db0-a3e1-4996-a9ce-e1ce13b977f9   swap       
/dev/sdb7        da2467af-bbfc-4693-8535-34722a88571b   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda4        /media/565afa23-0885-4b73-8d72-6cdb91f4ed69 ext3       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1        /media/50ECB185ECB165BE  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb5        /media/2023e0da-16ca-4474-9540-d1b7c0bd1dda ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb7        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
--------------------------------------------------------------------------------

================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=0
default=C:\CMDCONS\BOOTSECT.DAT
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
--------------------------------------------------------------------------------

=========================== sda4/boot/grub/grub.cfg: ===========================

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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set=root 565afa23-0885-4b73-8d72-6cdb91f4ed69
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos4)'
  search --no-floppy --fs-uuid --set=root 565afa23-0885-4b73-8d72-6cdb91f4ed69
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set=root 565afa23-0885-4b73-8d72-6cdb91f4ed69
    linux    /boot/vmlinuz-3.2.0-29-generic root=UUID=565afa23-0885-4b73-8d72-6cdb91f4ed69 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-29-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set=root 565afa23-0885-4b73-8d72-6cdb91f4ed69
    echo    'Loading Linux 3.2.0-29-generic ...'
    linux    /boot/vmlinuz-3.2.0-29-generic root=UUID=565afa23-0885-4b73-8d72-6cdb91f4ed69 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-29-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set=root 565afa23-0885-4b73-8d72-6cdb91f4ed69
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set=root 565afa23-0885-4b73-8d72-6cdb91f4ed69
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root DC4892E04892B92A
    chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 4B6E-6BC0
    drivemap -s (hd0) ${root}
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

=============================== sda4/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=565afa23-0885-4b73-8d72-6cdb91f4ed69 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=552e4939-4fd9-4b37-a3bd-e59c47513fea none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda4: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 137.194166183 = 147.311114240  boot/grub/core.img                             1
 137.194173813 = 147.311122432  boot/grub/grub.cfg                             1
 137.255277634 = 147.376732160  boot/initrd.img-3.2.0-29-generic               6
 137.241666794 = 147.362117632  boot/vmlinuz-3.2.0-29-generic                  3
 137.255277634 = 147.376732160  initrd.img                                     6
 137.241666794 = 147.362117632  vmlinuz                                        3

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set=root 2023e0da-16ca-4474-9540-d1b7c0bd1dda
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos5)'
  search --no-floppy --fs-uuid --set=root 2023e0da-16ca-4474-9540-d1b7c0bd1dda
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set=root 2023e0da-16ca-4474-9540-d1b7c0bd1dda
    linux    /boot/vmlinuz-3.2.0-29-generic root=UUID=2023e0da-16ca-4474-9540-d1b7c0bd1dda ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-29-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set=root 2023e0da-16ca-4474-9540-d1b7c0bd1dda
    echo    'Loading Linux 3.2.0-29-generic ...'
    linux    /boot/vmlinuz-3.2.0-29-generic root=UUID=2023e0da-16ca-4474-9540-d1b7c0bd1dda ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-29-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set=root 2023e0da-16ca-4474-9540-d1b7c0bd1dda
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set=root 2023e0da-16ca-4474-9540-d1b7c0bd1dda
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root DC4892E04892B92A
    chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 4B6E-6BC0
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 3.2.0-29-generic (on /dev/sda4)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set=root 565afa23-0885-4b73-8d72-6cdb91f4ed69
    linux /boot/vmlinuz-3.2.0-29-generic root=UUID=565afa23-0885-4b73-8d72-6cdb91f4ed69 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.2.0-29-generic
}
menuentry "Ubuntu, with Linux 3.2.0-29-generic (recovery mode) (on /dev/sda4)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set=root 565afa23-0885-4b73-8d72-6cdb91f4ed69
    linux /boot/vmlinuz-3.2.0-29-generic root=UUID=565afa23-0885-4b73-8d72-6cdb91f4ed69 ro recovery nomodeset
    initrd /boot/initrd.img-3.2.0-29-generic
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

=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=2023e0da-16ca-4474-9540-d1b7c0bd1dda /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=667f9db0-a3e1-4996-a9ce-e1ce13b977f9 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 835.467685699 = 897.076596736  boot/grub/core.img                             1
 857.507614136 = 920.741789696  boot/grub/grub.cfg                             1
 700.428279877 = 752.079138816  boot/initrd.img-3.2.0-29-generic               2
 857.505874634 = 920.739921920  boot/vmlinuz-3.2.0-29-generic                  1
 700.428279877 = 752.079138816  initrd.img                                     2
 857.505874634 = 920.739921920  vmlinuz                                        1

=========================== sdb7/boot/grub/grub.cfg: ===========================

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
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd1,msdos7)'
search --no-floppy --fs-uuid --set=root da2467af-bbfc-4693-8535-34722a88571b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd1,msdos7)'
  search --no-floppy --fs-uuid --set=root da2467af-bbfc-4693-8535-34722a88571b
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.2.0-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set=root da2467af-bbfc-4693-8535-34722a88571b
    linux    /boot/vmlinuz-3.2.0-33-generic root=UUID=da2467af-bbfc-4693-8535-34722a88571b ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-33-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set=root da2467af-bbfc-4693-8535-34722a88571b
    echo    'Loading Linux 3.2.0-33-generic ...'
    linux    /boot/vmlinuz-3.2.0-33-generic root=UUID=da2467af-bbfc-4693-8535-34722a88571b ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-33-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.2.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set=root da2467af-bbfc-4693-8535-34722a88571b
    linux    /boot/vmlinuz-3.2.0-29-generic root=UUID=da2467af-bbfc-4693-8535-34722a88571b ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-29-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set=root da2467af-bbfc-4693-8535-34722a88571b
    echo    'Loading Linux 3.2.0-29-generic ...'
    linux    /boot/vmlinuz-3.2.0-29-generic root=UUID=da2467af-bbfc-4693-8535-34722a88571b ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-29-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set=root da2467af-bbfc-4693-8535-34722a88571b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos7)'
    search --no-floppy --fs-uuid --set=root da2467af-bbfc-4693-8535-34722a88571b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root DC4892E04892B92A
    chainloader +1
}
menuentry "Windows NT/2000/XP (on /dev/sda2)" --class windows --class os {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 4B6E-6BC0
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 3.2.0-29-generic (on /dev/sda4)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set=root 565afa23-0885-4b73-8d72-6cdb91f4ed69
    linux /boot/vmlinuz-3.2.0-29-generic root=UUID=565afa23-0885-4b73-8d72-6cdb91f4ed69 ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.2.0-29-generic
}
menuentry "Ubuntu, with Linux 3.2.0-29-generic (recovery mode) (on /dev/sda4)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set=root 565afa23-0885-4b73-8d72-6cdb91f4ed69
    linux /boot/vmlinuz-3.2.0-29-generic root=UUID=565afa23-0885-4b73-8d72-6cdb91f4ed69 ro recovery nomodeset
    initrd /boot/initrd.img-3.2.0-29-generic
}
menuentry "Windows 7 (loader) (on /dev/sdb1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 50ECB185ECB165BE
    chainloader +1
}
menuentry "Ubuntu, with Linux 3.2.0-29-generic (on /dev/sdb5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set=root 2023e0da-16ca-4474-9540-d1b7c0bd1dda
    linux /boot/vmlinuz-3.2.0-29-generic root=UUID=2023e0da-16ca-4474-9540-d1b7c0bd1dda ro quiet splash $vt_handoff
    initrd /boot/initrd.img-3.2.0-29-generic
}
menuentry "Ubuntu, with Linux 3.2.0-29-generic (recovery mode) (on /dev/sdb5)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set=root 2023e0da-16ca-4474-9540-d1b7c0bd1dda
    linux /boot/vmlinuz-3.2.0-29-generic root=UUID=2023e0da-16ca-4474-9540-d1b7c0bd1dda ro recovery nomodeset
    initrd /boot/initrd.img-3.2.0-29-generic
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

=============================== sdb7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb7 during installation
UUID=da2467af-bbfc-4693-8535-34722a88571b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=667f9db0-a3e1-4996-a9ce-e1ce13b977f9 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdb7: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 677.496471405 = 727.456296960  boot/grub/core.img                             1
 411.283226013 = 441.612001280  boot/grub/grub.cfg                             1
 402.659713745 = 432.352575488  boot/initrd.img-3.2.0-29-generic               2
 403.041748047 = 432.762781696  boot/initrd.img-3.2.0-33-generic               2
 423.287818909 = 454.501834752  boot/vmlinuz-3.2.0-29-generic                  1
 402.627674103 = 432.318173184  boot/vmlinuz-3.2.0-33-generic                  1
 403.041748047 = 432.762781696  initrd.img                                     2
 402.659713745 = 432.352575488  initrd.img.old                                 2
 402.627674103 = 432.318173184  vmlinuz                                        1
 423.287818909 = 454.501834752  vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  e9 a7 00 52 45 43 4f 56  45 52 59 00 02 08 20 00  |...RECOVERY... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 97 45 07 1c  |........?....E..|
00000020  ea ff 14 01 1e 45 00 00  00 00 00 00 02 00 00 00  |.....E..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 c0 6b 6e 4b 48  50 5f 52 45 43 4f 56 45  |..).knKHP_RECOVE|
00000050  52 59 46 41 54 33 32 20  20 20 8b d0 c1 e2 02 80  |RYFAT32   ......|
00000060  e6 01 66 c1 e8 07 66 3b  46 f8 74 2a 66 89 46 f8  |..f...f;F.t*f.F.|
00000070  66 03 46 f4 66 0f b6 5e  28 80 e3 0f 74 0f 3a 5e  |f.F.f..^(...t.:^|
00000080  10 0f 83 90 00 66 0f af  5e 24 66 03 c3 bb e0 07  |.....f..^$f.....|
00000090  b9 01 00 e8 cf 00 8b da  66 8b 87 00 7e 66 25 ff  |........f...~f%.|
000000a0  ff ff 0f 66 3d f8 ff ff  0f c3 33 c9 8e d9 8e c1  |...f=.....3.....|
000000b0  8e d1 66 bc f4 7b 00 00  bd 00 7c 66 0f b6 46 10  |..f..{....|f..F.|
000000c0  66 f7 66 24 66 0f b7 56  0e 66 03 56 1c 66 89 56  |f.f$f..V.f.V.f.V|
000000d0  f4 66 03 c2 66 89 46 fc  66 c7 46 f8 ff ff ff ff  |.f..f.F.f.F.....|
000000e0  66 8b 46 2c 66 50 e8 af  00 bb 70 00 b9 01 00 e8  |f.F,fP....p.....|
000000f0  73 00 bf 00 07 b1 0b be  a9 7d f3 a6 74 2a 03 f9  |s........}..t*..|
00000100  83 c7 15 81 ff 00 09 72  ec 66 40 4a 75 db 66 58  |.......r.f@Ju.fX|
00000110  e8 47 ff 72 cf be b4 7d  ac 84 c0 74 09 b4 0e bb  |.G.r...}...t....|
00000120  07 00 cd 10 eb f2 cd 19  66 58 ff 75 09 ff 75 0f  |........fX.u..u.|
00000130  66 58 bb 00 20 66 83 f8  02 72 da 66 3d f8 ff ff  |fX.. f...r.f=...|
00000140  0f 73 d2 66 50 e8 50 00  0f b6 4e 0d e8 16 00 c1  |.s.fP.P...N.....|
00000150  e1 05 03 d9 66 58 53 e8  00 ff 5b 72 d8 8a 56 40  |....fXS...[r..V@|
00000160  ea 00 00 00 20 66 60 66  6a 00 66 50 53 6a 00 66  |.... f`fj.fPSj.f|
00000170  68 10 00 01 00 8b f4 b8  00 42 8a 56 40 cd 13 be  |h........B.V@...|
00000180  c7 7d 72 94 67 83 44 24  06 20 66 67 ff 44 24 08  |.}r.g.D$. fg.D$.|
00000190  e2 e3 83 c4 10 66 61 c3  66 48 66 48 66 0f b6 56  |.....fa.fHfHf..V|
000001a0  0d 66 f7 e2 66 03 46 fc  c3 4e 54 4c 44 52 20 20  |.f..f.F..NTLDR  |
000001b0  20 20 20 20 0d 0a 4e 6f  20 53 79 73 74 65 6d 20  |    ..No System |
000001c0  44 69 73 6b 20 6f 72 0d  0a 44 69 73 6b 20 49 2f  |Disk or..Disk I/|
000001d0  4f 20 65 72 72 6f 72 0d  0a 50 72 65 73 73 20 61  |O error..Press a|
000001e0  20 6b 65 79 20 74 6f 20  72 65 73 74 61 72 74 0d  | key to restart.|
000001f0  0a 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 


ADDITIONAL INFORMATION :
=================== log of boot-repair 2012-11-22__18h08 ===================
boot-repair version : 3.194~ppa62~precise
boot-sav version : 3.194~ppa62~precise
glade2script version : 3.2.2~ppa45~precise
boot-sav-extra version : 3.194~ppa62~precise
boot-repair is executed in installed-session (Ubuntu 12.04.1 LTS, precise, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/boot/vmlinuz-3.2.0-33-generic root=UUID=da2467af-bbfc-4693-8535-34722a88571b ro quiet splash vt.handoff=7

=================== os-prober:
/dev/sdb7:The OS now in use - Ubuntu 12.04.1 LTS CurrentSession:linux
/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sda2:Windows NT/2000/XP:Windows1:chain
/dev/sda4:Ubuntu 12.04.1 LTS (12.04):Ubuntu:linux
/dev/sdb1:Windows 7 (loader):Windows2:chain
/dev/sdb5:Ubuntu 12.04.1 LTS (12.04):Ubuntu1:linux

=================== blkid:
/dev/sda1: LABEL="HP_PAVILION" UUID="DC4892E04892B92A" TYPE="ntfs"
/dev/sda2: LABEL="HP_RECOVERY" UUID="4B6E-6BC0" TYPE="vfat"
/dev/sda4: UUID="565afa23-0885-4b73-8d72-6cdb91f4ed69" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda5: UUID="552e4939-4fd9-4b37-a3bd-e59c47513fea" TYPE="swap"
/dev/sdb1: UUID="50ECB185ECB165BE" TYPE="ntfs"
/dev/sdb5: UUID="2023e0da-16ca-4474-9540-d1b7c0bd1dda" TYPE="ext4"
/dev/sdb6: UUID="667f9db0-a3e1-4996-a9ce-e1ce13b977f9" TYPE="swap"
/dev/sdb7: UUID="da2467af-bbfc-4693-8535-34722a88571b" TYPE="ext4"


2 disks with OS, 6 OS : 3 Linux, 0 MacOS, 3 Windows, 0 unknown type OS.

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.


=================== /etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"




=================== /etc/grub.d/ :
drwxr-xr-x  2 root root     4096 Nov 20 19:06 grub.d
total 56
-rwxr-xr-x 1 root root 6743 Sep 12 13:18 00_header
-rwxr-xr-x 1 root root 5522 May 17  2012 05_debian_theme
-rwxr-xr-x 1 root root 7407 May 17  2012 10_linux
-rwxr-xr-x 1 root root 6335 May 17  2012 20_linux_xen
-rwxr-xr-x 1 root root 1588 Nov 27  2011 20_memtest86+
-rwxr-xr-x 1 root root 7603 May 17  2012 30_os-prober
-rwxr-xr-x 1 root root  214 May 17  2012 40_custom
-rwxr-xr-x 1 root root   95 May 17  2012 41_custom
-rw-r--r-- 1 root root  483 May 17  2012 README


ls: cannot access : No such file or directory


=================== /media/565afa23-0885-4b73-8d72-6cdb91f4ed69/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"




=================== /media/565afa23-0885-4b73-8d72-6cdb91f4ed69/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Aug 23 09:56 grub.d
total 56
-rwxr-xr-x 1 root root 6715 May 17  2012 00_header
-rwxr-xr-x 1 root root 5522 May 17  2012 05_debian_theme
-rwxr-xr-x 1 root root 7407 May 17  2012 10_linux
-rwxr-xr-x 1 root root 6335 May 17  2012 20_linux_xen
-rwxr-xr-x 1 root root 1588 Nov 27  2011 20_memtest86+
-rwxr-xr-x 1 root root 7603 May 17  2012 30_os-prober
-rwxr-xr-x 1 root root  214 May 17  2012 40_custom
-rwxr-xr-x 1 root root   95 May 17  2012 41_custom
-rw-r--r-- 1 root root  483 May 17  2012 README




=================== /media/2023e0da-16ca-4474-9540-d1b7c0bd1dda/etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"




=================== /media/2023e0da-16ca-4474-9540-d1b7c0bd1dda/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Aug 23 09:56 grub.d
total 56
-rwxr-xr-x 1 root root 6715 May 17  2012 00_header
-rwxr-xr-x 1 root root 5522 May 17  2012 05_debian_theme
-rwxr-xr-x 1 root root 7407 May 17  2012 10_linux
-rwxr-xr-x 1 root root 6335 May 17  2012 20_linux_xen
-rwxr-xr-x 1 root root 1588 Nov 27  2011 20_memtest86+
-rwxr-xr-x 1 root root 7603 May 17  2012 30_os-prober
-rwxr-xr-x 1 root root  214 May 17  2012 40_custom
-rwxr-xr-x 1 root root   95 May 17  2012 41_custom
-rw-r--r-- 1 root root  483 May 17  2012 README


=================== UEFI/Legacy mode :
This installed-session is not in EFI-mode.


=================== PARTITIONS & DISKS:
sdb7    : sdb,    not-sepboot,    grubenv-ok    grub2,    grub-pc,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    .
sda1    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    ntldr,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda1.
sda2    : sda,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    NTLDR,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda2.
sda4    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /media/565afa23-0885-4b73-8d72-6cdb91f4ed69.
sdb1    : sdb,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    is-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /media/50ECB185ECB165BE.
sdb5    : sdb,    not-sepboot,    grubenv-ok    grub2,    grub-pc,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /media/2023e0da-16ca-4474-9540-d1b7c0bd1dda.

sdb    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes
sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    63 sectors * 512 bytes


=================== parted -l:

Model: ATA SAMSUNG SP2504C (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
1      32.3kB  119GB  119GB   primary   ntfs            boot
4      119GB   236GB  117GB   primary   ext3
3      236GB   241GB  4985MB  extended
5      236GB   241GB  4984MB  logical   linux-swap(v1)
2      241GB   250GB  9295MB  primary   fat32           lba


Model: ATA ST31000333AS (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      1049kB  431GB   431GB   primary   ntfs            boot
2      431GB   1000GB  569GB   extended
7      431GB   751GB   320GB   logical   ext4
5      751GB   997GB   246GB   logical   ext4
6      997GB   1000GB  3218MB  logical   linux-swap(v1)

=================== parted -lm:

BYT;
/dev/sda:250GB:scsi:512:512:msdos:ATA SAMSUNG SP2504C;
1:32.3kB:119GB:119GB:ntfs::boot;
4:119GB:236GB:117GB:ext3::;
3:236GB:241GB:4985MB:::;
5:236GB:241GB:4984MB:linux-swap(v1)::;
2:241GB:250GB:9295MB:fat32::lba;

BYT;
/dev/sdb:1000GB:scsi:512:512:msdos:ATA ST31000333AS;
1:1049kB:431GB:431GB:ntfs::boot;
2:431GB:1000GB:569GB:::;
7:431GB:751GB:320GB:ext4::;
5:751GB:997GB:246GB:ext4::;
6:997GB:1000GB:3218MB:linux-swap(v1)::;


=================== mount:
/dev/sdb7 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/kevin/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=kevin)
/dev/sda4 on /media/565afa23-0885-4b73-8d72-6cdb91f4ed69 type ext3 (rw,nosuid,nodev,uhelper=udisks)
/dev/sdb1 on /media/50ECB185ECB165BE type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdb5 on /media/2023e0da-16ca-4474-9540-d1b7c0bd1dda type ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sda1 on /mnt/boot-sav/sda1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda2 on /mnt/boot-sav/sda2 type vfat (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 sda5 size slaves stat subsystem trace uevent
/sys/block/sdb (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 sdb2 sdb5 sdb6 sdb7 size slaves stat subsystem trace uevent
/sys/block/sdc (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdd (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sde (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sdf (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom cdrw char console core cpu cpu_dma_latency disk dri dvd dvdrw ecryptfs fb0 fd full fuse fw0 hidraw0 hpet input kmsg log lp0 mapper mcelog mem net network_latency network_throughput null oldmem parport0 port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sda5 sdb sdb1 sdb2 sdb5 sdb6 sdb7 sdc sdd sde sdf sg0 sg1 sg2 sg3 sg4 sg5 sg6 shm snapshot snd sr0 stderr stdin stdout uinput urandom usbmon0 usbmon1 usbmon2 usbmon3 usbmon4 usbmon5 vga_arbiter zero
ls /dev/mapper:  control

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sdb7      ext4      294G  3.6G  275G   2% /
udev           devtmpfs  1.5G   12K  1.5G   1% /dev
tmpfs          tmpfs     603M  868K  602M   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     1.5G  160K  1.5G   1% /run/shm
/dev/sda4      ext3      107G  2.8G   99G   3% /media/565afa23-0885-4b73-8d72-6cdb91f4ed69
/dev/sdb1      fuseblk   402G  107G  295G  27% /media/50ECB185ECB165BE
/dev/sdb5      ext4      226G  2.6G  212G   2% /media/2023e0da-16ca-4474-9540-d1b7c0bd1dda
/dev/sda1      fuseblk   112G   84G   28G  76% /mnt/boot-sav/sda1
/dev/sda2      vfat      8.7G  8.2G  452M  95% /mnt/boot-sav/sda2

=================== fdisk -l:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcab10bee

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   232813979   116406958+   7  HPFS/NTFS/exFAT
/dev/sda2       470238615   488392064     9076725    c  W95 FAT32 (LBA)
/dev/sda3       460503225   470238614     4867695    5  Extended
/dev/sda4       232813980   460503224   113844622+  83  Linux
/dev/sda5       460503288   470238614     4867663+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xff296f63

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   841279535   420638744    7  HPFS/NTFS/exFAT
/dev/sdb2       841281534  1953523711   556121089    5  Extended
/dev/sdb5      1466525696  1947236351   240355328   83  Linux
/dev/sdb6      1947238400  1953523711     3142656   82  Linux swap / Solaris
/dev/sdb7       841281536  1466525695   312622080   83  Linux

Partition table entries are not in disk order


User choice: Is sdb (1000GB) a removable disk? no
=================== Final advice in case of recommended repair
Please do not forget to make your BIOS boot on sdb (1000GB) disk!

The boot files of [The OS now in use - Ubuntu 12.04.1 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

=================== Default settings
Recommended-Repair
This setting would reinstall the grub2 of sdb7 into the MBRs of all disks (except USB without OS).
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot

=================== Settings chosen by the user
Boot-Info
This setting will not act on the MBR.



No change has been performed on your computer. See you soon!

Download as text
```
:KS

---

### Post by oldfred on 2012-11-22
Does it boot ok?
You seem to have several installs, 3 Windows & 3 Ubuntu.

With the link to pastebin, you did not need to post the BootInfo report. But if you post long formated info please use code tags. Hightlight like copy and click on # in edit panel above your post.

---

### Post by keheikev on 2012-11-23
Sorry for the long post just looking to see if I need any further modification to grub. I think both the grub 2 and the windows 7 bootloader are on the terabyte drive sdb if thats what boot repair shows. Anyway the link to multibooters was fantastic.
Kevin

---

### Post by keheikev on 2012-11-24
It is booting fine. ;)  I believe all my old Ubuntu versions have been formatted so the only one I am booting is partition 7 on sdb not the other 12.04  partition 4 on sda. I think we discussed what I want is grub 2 on sda and windows boot mgr on sdb so that if a drive fails i just change the boot order. I think I made a mistake partitioning the terabyte drive for both Ubuntu by using the installers partitioner to use unused space there.
The other thing I need to do is remove the metadata for both drives and switch to AHCI instead of the raid setting.
In my view I have 2 Linux o/s and 3 windows, window7, xp and a recovery partition?
Old fred this whole experience is showing me how much more robust Linux is compared to windows.
Kevin
[http://paste.ubuntu.com/1378552/](http://paste.ubuntu.com/1378552/)

---

### Post by oldfred on 2012-11-24
If both systems are on sdb, it does not matter on boot loaders as much. Both will depend on sdb as even if grub is booting from the MBR of sda, it still has to find the rest of its files on sdb.

But Boot-Repair should let you install a Windows like boot loader to sdb, or you can use a Windows repairCD which you should have to fixMBR.

       How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

    
Or from Ubuntu you can just install lilo to sdb. Lilo works like Windows in it has more boot code in the partition boot sector and chain loads to the partition with the boot flag. Lilo is better than Windows in that it will boot a logical partition. But you do not want the full lilo, just the MBR boot loader.

       Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sdb mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

---

### Post by keheikev on 2013-01-13
Well I am about ready to mark the thread solved but I have a couple questions. I was able to get the thing booting in ahci  instead of raid but the problem turned out was it must have been installed in raid mode so I had to turn the windows 7 ahci drivers on with a microsoft fixit. My ubuntu system running 12.04 did not recognize the command dmraid for the meta data removal from the presence thread... Is that obtained thru adding a package to the system?
Now basically after reviewing the link on multiboot systems can you see from my post if my windows 7 system depends on the xp install's PBR? So if sda tanks things are not good.


Kevin 
:popcorn:

---

