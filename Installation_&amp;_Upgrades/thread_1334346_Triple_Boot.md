---
title: "Triple Boot"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by mahiyar on 2009-11-22
Hi, Currently I have a 500gb hard disk. Here is the scheme of things 

mahiyar@mahiyar-desktop:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4a224a21

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10198    81915403+   7  HPFS/NTFS
/dev/sda2           10199       27099   135757282+   f  W95 Ext'd (LBA)
/dev/sda3           54399       60801    51432097+  83  Linux
/dev/sda5           10199       15297    40957686    7  HPFS/NTFS
/dev/sda6           15298       21117    46749118+   7  HPFS/NTFS
/dev/sda7           26597       27099     4040316   82  Linux swap / Solaris
/dev/sda8           21118       26596    44010036    b  W95 FAT32

Partition table entries are not in disk order

So as sda1 is the windows partition, sda2 is extended containing swap, and other partitions, sda3 is the Karmic partition. Currently win xp and karmic are existing together peacefully with grub 2 and all. Now if I wish to install windows 7 and also decide to keep win xp (windows 7 will be on a try out basis), whats the best way of going about. Please advise.

---

### Post by oldfred on 2009-11-22
It is always best to install to a primary partition, it looks like you have one left. Win7 will install to a logical partition and combine its boot with the XP boot. But if you ever delete XP you will have to reinstall Win7. In windows you choose which windows to boot. From grub you can only choose the one windows that has the boot files. 

There is a work around if you want. All versions of windows must be in primary partitions. You then from windows can only boot one of the windows but from grub can choose either directly.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by mahiyar on 2009-11-24
How about this --- 

I have another SATA drive of 180GB lying around. I disconnect the current 500gb drive, and connect the 180GB drive. Install windows 7 on it. After the install is complete and all I reattach the 500Gb drive, make it first device from BIOS, now my old grub menu and all would be availabe, once I go in Ubuntu I run grub-config command where it will automatically catch Win 7 entry.

Is this scheme OK?

---

### Post by oldfred on 2009-11-24
Should work that way. Grub2 will automatically add the map commands now mapdrive in grub2 to make windows still think it is first when you select it.

I always like having each operating system on a separate drive and having that drive MBR boot to that drive. Since Windows is not easy to boot to other, having grub/Ubuntu first makes it easy to also boot windows.

It is good that both drives are Sata as there still seem to be issues with mixed Sata & Pata configurations, and I think it depends on the motherboard/BIOS setup.

---

### Post by mahiyar on 2009-11-24
Thanks oldfred, so I will go ahead with my plan, maybe next week after I complete this exercise successfully, I will write a final post and mark the thread solved.

---

### Post by presence1960 on 2009-11-24
> **oldfred said:**
> It is always best to install to a primary partition, it looks like you have one left. Win7 will install to a logical partition and combine its boot with the XP boot. But if you ever delete XP you will have to reinstall Win7. In windows you choose which windows to boot. From grub you can only choose the one windows that has the boot files. 

There is a work around if you want. All versions of windows must be in primary partitions. You then from windows can only boot one of the windows but from grub can choose either directly.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

+1 can't go wrong there.

---

### Post by mahiyar on 2009-11-29
Ok. Success, without a hitch. Disconnected the original drive, connected the second smaller drive, installed windows 7 on it, reconnected the back the original drive (keeping the smaller one), made it bootable, booted to Ubuntu ran update-grub, win 7 discovered, that was all, now I have ubuntu 9.10, winxp and win7 from single menu. grub2 is really powerfull. Marking the thread as solved.

---

### Post by xinam on 2010-09-04
What happens to the assigned letters to these volumes?
Won't you have 2 C:\ assignment for your volumes?

Hope the question is clear :\

---

### Post by presence1960 on 2010-09-04
which ever windows install you boot into will have it's root as C:, the other will be assigned another letter designation. Example: Windows vista and windows 7 are installed as described above. When you boot Vista- it's root will be assigned C; and 7's will be assigned another letter which will be determined by what other partitions/disks you have on your machine. When you boot into 7, 7's root will be assigned C; and vista's will be assigned another letter depending on the other partitions/disks on your machine.

When using Linux and GRUB we need to forget the windows way of assigning partitions/disks designations (C:, D:, E:, etc.) because that means absolutely nothing in Linux. It only means something in Windows.

---

### Post by xinam on 2010-09-04
Thank You presence1960,
I knew that these didn't matter on the Linux side.

Just didn't know that they would readjust (as I seem to understand) dynamically whether you would boot on 7 or Vista or XP.

Trying this install at the moment:

Installed Windows XP on [sda] (931GB) and on created Primary partition label=WinXP (40GB) NTFS [sda1]
Unplugged [sda]
Installed Windows 7 on [sdb] (69GB) and on created Primary partition label=Win7 (69GB) NTFS [sdb1]
Plugged back [sda]
Used GParted to create other partitions on [sda] (Didn't find any way to create an extended partition from Ubuntu Desktop 10.04)
Created Extended partition on [sda] 1024MB away from [sda1] (Leaving space for Ext4 /boot partition)
Created Logical partition label=Data (40GB) NTFS [sda4]
Created Logical partition label=Download (60GB) NTFS [sda5]
Created Logical partition label=Game (100GB) NTFS [sda6]
Created Logical partition label=Media (613GB) NTFS [sda7]
Created Logical partition label=Share (32GB) Fat32 [sda8]

Reboot and put Ubuntu Desktop 10.04 DVD:

Pressed any key at the splash screen (as it crashes on start up)
Chose "Try Ubuntu without installing"
Clicked on icon "Install Ubuntu 10.04"

Chose advanced partitioning:
Created Primary partition mount=/boot (1GB) [sda3] Ext4
Created Logical partition mount=/ (12GB) [sda9] Ext4 (on remaining space after [sda8])
Created Logical partition mount=/home (28GB) [sda10] Ext4
Created Logical partition swap space (5GB) swap space

Continuing install (Don't know where to tell the boot loader to install on [sda3] mount=/boot it defaults to tell it installs on [sda])

At the end of the install an error message poped up (should have written it down :( )

Rebooted

(No boot menu) Win7 boots ok, but shouldn't Ubuntu boots first now that I suppose GRub is installed? If not, how would I manually install GRub on [sda3] mount=/boot?

---

### Post by xinam on 2010-09-04
Hmmm... maybe I should start a new thread as this one is [Solved]...
Even though the question stays the same?

Triple booting Win 7, Win XP, Ubuntu
Win 7 and Win Xp on 2 drives
one boot menu

---

### Post by xinam on 2010-09-04
Ok I see from Live CD that my /boot/grub folder in my 1GB filesystem is empty...
Following this thread to reinstall it :
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")[URL="https://help.ubuntu.com/community/GRub2#Reinstalling%20from%20LiveCD"]
[/URL]

---

### Post by xinam on 2010-09-05
Can there be a problem because my partition [sda3] mount=/boot isn't big enough? (1024MB)
What's the recommended size for the /boot partition? 

(I'll google that, and comeback to tell if that was the case)

---

### Post by presence1960 on 2010-09-05
> **xinam said:**
> Can there be a problem because my partition [sda3] mount=/boot isn't big enough? (1024MB)
What's the recommended size for the /boot partition? 

(I'll google that, and comeback to tell if that was the case)

There is no need for a separate boot partition unless you have an older BIOS which is limited to how far on your hard disk it can look for files needed to boot. I would advise against a separate boot partition except in that case- it really is totally unnecessary.

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by xinam on 2010-09-05
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 84157536 of 
    the same hard drive for core.img, but core.img can not be found at this 
    location.
 => Windows is installed in the MBR of /dev/sdb

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

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda9 starts at sector 1784676634.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab

sda11: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda12: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
22 heads, 26 sectors/track, 3415253 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             26    83,886,087    83,886,062   7 HPFS/NTFS
/dev/sda2          85,983,064 1,953,523,711 1,867,540,648   5 Extended
/dev/sda5          85,983,066   169,869,127    83,886,062   7 HPFS/NTFS
/dev/sda6         169,869,154   295,698,259   125,829,106   7 HPFS/NTFS
/dev/sda7         295,698,286   505,413,479   209,715,194   7 HPFS/NTFS
/dev/sda8         505,413,506 1,784,676,607 1,279,263,102   7 HPFS/NTFS
/dev/sda9       1,784,676,634 1,851,785,363    67,108,730   b W95 FAT32
/dev/sda10      1,851,787,264 1,875,785,727    23,998,464  83 Linux
/dev/sda11      1,875,787,776 1,931,786,239    55,998,464  83 Linux
/dev/sda12      1,943,525,376 1,953,523,711     9,998,336  82 Linux swap / Solaris
/dev/sda3          83,888,128    85,981,183     2,093,056  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 74.4 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders, total 145226112 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   145,223,679   145,221,632   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       f73aba87-3d50-4a5d-83c3-42ebfd5cb5d4   ext4                                     
/dev/sda11       0c6bf05b-f8af-42d4-a9b0-a7c7aa701978   ext4                                     
/dev/sda12       3e2a89f6-1ec8-4e2c-9d28-a62e84b68f67   swap                                     
/dev/sda1        7E7C0CDF7C0C9455                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        f286f153-08ec-4481-9132-fab1946040eb   ext4                                     
/dev/sda5        294D407D765559A9                       ntfs       Data                          
/dev/sda6        44C58FD85F96F150                       ntfs       Download                      
/dev/sda7        204B0B2D0936CDA8                       ntfs       Game                          
/dev/sda8        7BE1626072B96881                       ntfs       Media                         
/dev/sda9        CDD8-896E                              vfat       Share                         
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1E52F2EB52F2C695                       ntfs       Win7                          
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda10       /                        ext4       (rw,errors=remount-ro)
/dev/sda11       /home                    ext4       (rw)
/dev/sda3        /boot                    ext4       (rw)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professionnel" /fastdetect

=============================== sda10/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda10 during installation
UUID=f73aba87-3d50-4a5d-83c3-42ebfd5cb5d4 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda3 during installation
UUID=f286f153-08ec-4481-9132-fab1946040eb /boot           ext4    defaults        0       2
# /home was on /dev/sda11 during installation
UUID=0c6bf05b-f8af-42d4-a9b0-a7c7aa701978 /home           ext4    defaults        0       2
# swap was on /dev/sda12 during installation
UUID=3e2a89f6-1ec8-4e2c-9d28-a62e84b68f67 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda10: Location of files loaded by Grub: ===================


 948.2GB: initrd.img
 948.2GB: vmlinuz

============================= sda3/grub/grub.cfg: =============================

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
set root='(hd0,10)'
search --no-floppy --fs-uuid --set f73aba87-3d50-4a5d-83c3-42ebfd5cb5d4
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
set root='(hd0,3)'
search --no-floppy --fs-uuid --set f286f153-08ec-4481-9132-fab1946040eb
set locale_dir=($root)/grub/locale
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
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set f286f153-08ec-4481-9132-fab1946040eb
    linux    /vmlinuz-2.6.32-21-generic root=UUID=f73aba87-3d50-4a5d-83c3-42ebfd5cb5d4 ro   quiet splash
    initrd    /initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set f286f153-08ec-4481-9132-fab1946040eb
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /vmlinuz-2.6.32-21-generic root=UUID=f73aba87-3d50-4a5d-83c3-42ebfd5cb5d4 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set f286f153-08ec-4481-9132-fab1946040eb
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set f286f153-08ec-4481-9132-fab1946040eb
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professionnel (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 7e7c0cdf7c0c9455
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set 1e52f2eb52f2c695
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda3: Location of files loaded by Grub: ===================


  43.0GB: grub/core.img
  43.1GB: grub/grub.cfg
  43.1GB: initrd.img-2.6.32-21-generic
  43.0GB: vmlinuz-2.6.32-21-generic


```

---

### Post by xinam on 2010-09-05
With the last boot info, I got Ubuntu to install fine.

Problem seemed to be because I was partitioning the entire disk, leaving no non-allocated space before the install of Ubuntu Desktop 10.04.
At the end of Ubuntu install the error I was getting were:

[LIST=1]
[*]Sorry the program gdu_notification_daemon closed unexpectedly
[*]Sorry the program ubiquity closed unexpectedly
[/LIST]

But now when I reboot, I see Grub menu containing the 3 OS.
Win7 boots no problem
Ubuntu Desktop 10.04 boots no problem
WinXP boots, but produce a blue sceen UNMOUNTABLE_VOLUME or something...

When I first installed Windows XP Pro:
At the install I was only seeing 132GB of available space for the install, when there really was 1TB.
(Seems to be a well known problem for WinXP Pro, maybe got to update before partitioning with GParted to get LBA 48 support?)
But Booted fine on the 40GB created partition

Problems come after partitioning the rest of the space with GParted

Windows XP gets Blue Screen while booting...

Thanks for taking the time to help me with this presence1960

---

### Post by oldfred on 2010-09-05
Check BIOS settings:

When I got a new motherboard I tried using AHCI mode. Ubuntu booted but XP did not. I changed back to Disabled in BIOS on AHCI and XP booted again. I think I saw some say you could add drivers for SATA something but I never have.

---

### Post by xinam on 2010-09-06
Ok, I've managed to get everything working:

To fix Windows XP Blue Screen at boot, I had to update Windows XP Pro.
Slipstreamed a new Windows XP Pro CD with SP3 preinstalled. (even though SP1 or SP2 should do)

I reinstalled Windows XP
Partitioned the disk with GParted (except for the ext4 for Ubuntu, which I did from the Ubuntu CD. Heard that GParted had trouble with Ext4 format)
I reinstalled Ubuntu Desktop 10.04 without individual /boot partition as presence1960 suggested.

partition mount=/ as Primary
partition mount=/home as Logical in Extended

Thank You all

---

