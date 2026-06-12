---
title: "comp boots too grub 1.99"
date: 2011-05-24
forum: Installation &amp; Upgrades
---

### Post by benny777 on 2011-05-24
Hello i have just installed win xp on a seperate partion that proceeds after the ubuntu partion. windows has xisabled the partion. I tried reinztall grub thinking that might bring up the dual boot screen but the comp boots ztraight to the grub 1.99 shell command. plz help

---

### Post by Quackers on 2011-05-24
Welcome to UF
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder).
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by benny777 on 2011-05-24
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000203804160 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953523055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048   921,137,151   921,135,104  83 Linux
/dev/sda2    *    921,151,035 1,945,134,134 1,023,983,100   7 NTFS / exFAT / HPFS
/dev/sda3       1,945,139,198 1,953,521,663     8,382,466   5 Extended
/dev/sda5       1,945,139,200 1,953,521,663     8,382,464  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 7948 MB, 7948206080 bytes
11 heads, 10 sectors/track, 141125 cylinders, total 15523840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          8,192    15,523,839    15,515,648   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        55909635-7a16-470b-be0c-b0639b3a70f9   ext3       
/dev/sda2        CE2030DC2030CCE9                       ntfs       
/dev/sda5        7ceea944-d473-4eb4-af9e-a7748de8da47   swap       
/dev/sdb1                                               vfat       EOS_DIGITAL

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/EOS_DIGITAL       vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=55909635-7a16-470b-be0c-b0639b3a70f9 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=7ceea944-d473-4eb4-af9e-a7748de8da47 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 167.337066650 = 179.676807168  boot/grub/core.img                             1

================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

unlzma: Decoder error
 
```

---

### Post by Quackers on 2011-05-24
You appear to be missing an Ubuntu boot file (/boot/grub/grub.cfg).
I would suggest that you purge and re-install grub using the CHROOT section of the guide below.
The partition you need to mount is /dev/sda1 and grub should be installed to /dev/sda

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by oldfred on 2011-05-24
You are also missing kernels. Did you have a separate /boot partition and remove it?

Follow Quackers advice on chrooting and reinstalling grub2, but also run this while in chroot.

reinstall kernel:
sudo apt-get update
sudo apt-get install linux-image
sudo update-grub

---

### Post by benny777 on 2011-05-24
> **Quackers said:**
> You appear to be missing an Ubuntu boot file (/boot/grub/grub.cfg).
I would suggest that you purge and re-install grub using the CHROOT section of the guide below.
The partition you need to mount is /dev/sda1 and grub should be installed to /dev/sda

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)


Ok thanks, will report back when I have time to do that.

---

### Post by benny777 on 2011-05-24
> **oldfred said:**
> You are also missing kernels. Did you have a separate /boot partition and remove it?

Follow Quackers advice on chrooting and reinstalling grub2, but also run this while in chroot.

reinstall kernel:
sudo apt-get update
sudo apt-get install linux-image
sudo update-grub
  I have a seperate BOOT partition, but it 3 partions all up concerning ubuntu, main, boot and swap. I havent deleted the boot partion, I dont think anyaway, it is still visible in disk utility. I will run those commands you have suggested when I run quakers suggestion and report back with a success rate

---

### Post by oldfred on 2011-05-24
A boot flag is not a boot partition. Grub does not use a boot flag, windows boot loader (and some BIOS) have to have a boot flag.

---

### Post by benny777 on 2011-05-25
> **benny777 said:**
> Ok thanks, will report back when I have time to do that.


Hi guys OK I have gotten stuck. I was bale to mount all the partions, but I couldnt load the "I in..." stuff i type this..

sudo mount -B $i /mnt/temp$i

and get this


mount: can't find /mnt/temp in /etc/fstab or /etc/mtab

I might just do a complrete reinstall.

---

### Post by benny777 on 2011-05-25
> **benny777 said:**
> Hi guys OK I have gotten stuck. I was bale to mount all the partions, but I couldnt load the "I in..." stuff i type this..

sudo mount -B $i /mnt/temp$i

and get this


mount: can't find /mnt/temp in /etc/fstab or /etc/mtab

I might just do a complrete reinstall.
  Its ok I wont reinstall just types sudo -1 and got root., i will finish the tutorial and report back

---

