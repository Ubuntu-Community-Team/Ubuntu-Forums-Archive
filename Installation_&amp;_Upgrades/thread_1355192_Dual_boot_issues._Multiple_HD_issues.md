---
title: "Dual boot issues. Multiple HD issues?"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by Frostywars on 2009-12-14
I have spent about 14 hours in the last two days researching, reading, trying, trying again, etc. I hate asking people what to do because with the right search options, just about anything can be resolved through other peoples problems getting fixed. Now however, I am stuck.   Sorry if this is really simple but, I am trying to boot Ubuntu and Windows 7 off of one hard drive with separate partitions.  Before I continue, I know my hard drive setup looks like a mess and I think that is why I am having problems, but I hope it can be resolved.   Here is my fdisk list: (will try to clean up the formating) >  D[SIZE=1]isk /dev/sda: 500.1 GB, 500107862016 bytes 255 heads, 63 sectors/track, 60801 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Disk identifier: 0x72b00fab     Device Boot      Start         End      Blocks   Id  System /dev/sda1   *           1       60802   488383488    7  HPFS/NTFS  Disk /dev/sdb: 500.1 GB, 500107862016 bytes 255 heads, 63 sectors/track, 60801 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Disk identifier: 0x023dec43     Device Boot      Start         End      Blocks   Id  System /dev/sdb1   *           1       60800   488375968+   7  HPFS/NTFS  Disk /dev/sdc: 500.1 GB, 500107862016 bytes 255 heads, 63 sectors/track, 60801 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Disk identifier: 0x023dec4c     Device Boot      Start         End      Blocks   Id  System /dev/sdc1   *           1       60802   488384512    7  HPFS/NTFS[/SIZE]  Disk /dev/sdd: 500.1 GB, 500107862016 bytes 255 heads, 63 sectors/track, 60801 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Disk identifier: 0x87d1cb24     Device Boot      Start         End      Blocks   Id  System **/dev/sdd1               1       45384   364546948+   7  HPFS/NTFS** /dev/sdd2   *       45385       60801   123837052+   5  Extended /dev/sdd5           60437       60801     2931862+  82  Linux swap / Solaris **/dev/sdd6           45385       59818   115941042   83  Linux** /dev/sdd7           59819       60435     4956021   82  Linux swap / Solaris  Partition table entries are not in disk order  [SIZE=1]Disk /dev/sde: 500.1 GB, 500107862016 bytes 255 heads, 63 sectors/track, 60801 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Disk identifier: 0x54b32ee1     Device Boot      Start         End      Blocks   Id  System /dev/sde1   *           1       60802   488384512    7  HPFS/NTFS  Disk /dev/sdf: 500.1 GB, 500107862016 bytes 255 heads, 63 sectors/track, 60801 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Disk identifier: 0xd5d905b9     Device Boot      Start         End      Blocks   Id  System /dev/sdf1   *           1       60802   488384512    7  HPFS/NTFS[/SIZE]    So from this fdisk read out, I determined that the Windows will boot from hd4,0 and the Linux build will boot from (hd4,5)   So I edited my grub to look like this: (I had to edit my grub because it wouldnt even start up due to the uuid things)  >   [SIZE=1]## default num # Set the default entry to the entry number NUM. Numbering starts from 0, and # the entry number 0 is the default if the command is not used. # # You can specify 'saved' instead of a number. In this case, the default entry # is the entry saved with the command 'savedefault'. # WARNING: If you are using dmraid do not use 'savedefault' or your # array will desync and will not let you boot your system. default        0   timeout        20  ## hiddenmenu # Hides the menu by default (press ESC to see the menu) #hiddenmenu  # Pretty colours #color cyan/blue white/blue [/SIZE]    title        Ubuntu **root            (hd4,5) kernel        /boot/vmlinuz-2.6.29.4 root=/dev/sdd6 ro** initrd        /boot/initrd.img-2.6.29.4 quiet  title        Ubuntu (recovery mode) **root            (hd4,5) kernel        /boot/vmlinuz-2.6.29.4 root=/dev/sdd6 ro  single** initrd        /boot/initrd.img-2.6.29.4  title        Ubuntu memtest86+ root            (hd4,5) kernel        /boot/memtest86+.bin quiet  [SIZE=1]### END DEBIAN AUTOMAGIC KERNELS LIST  # This is a divider, added to separate the menu items below from the Debian # ones. title        Other operating systems: root[/SIZE]   # This entry automatically added by the Debian installer for a non-linux OS # on /dev/sdd1 title        Windows 7 **root        (hd4,0)** savedefault map        (hd0) (hd4) map        (hd4) (hd0) chainloader    +1      When I installed Unbuntu, I told the grub to install to sdd rather then sdd1 or sdd6, so now I can not even recover my windows boot loader because grub has taken over everything.   When I try booting to linux with grub, it tells me there is no such partition. When I try booting to windows, it gives me the classic, NTDLR is missing error.   I have tried &quot;messing&quot; with grub and changing the HD values and trying to boot linux with no success. and as for windows, I dont think there is any hope :( I hope to at least be able to get back into windows though.

---

### Post by darkod on 2009-12-14
OK, few things.
First of all, sda-sdb-sdc-sdd does NOT always mean hd0-hd3. Also, the counting of hdds starts from 0, so if you thought your /dev/sdd is hd4, most probably it's hd3. But they do not always correlate like that, and that's the tricky part.
So, to get that dilemma out of the way, you can boot with ubuntu cd, Try Ubuntu option, and look in /boot/grub/device.map file. (I think it was in /boot/grub folder, not on my ubuntu machine right now to check).
device.map will show you the mapping sdX to hdY.

Also, depending if you have grub1 or grub2, the partitions are counted from 0 in grub1, but from 1 in grub2.
The above makes a difference when editing your (hdX,Y) entries.

---

### Post by darkod on 2009-12-14
Another option, while booted with the Try ubuntu option, download the script in my signature, put it on desktop for example, and execute with:
sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file with lots of details of your boot process. Copy the content here and please put CODE tags around it (hit # button in toolbar above).

---

### Post by Frostywars on 2009-12-14
```
============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/hdb
 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Grub 0.97 is installed in the MBR of /dev/sdd and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sde
 => Windows is installed in the MBR of /dev/sdf

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdd2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdd6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdd7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sde1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sdf1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

=========================== Drive/Partition Info: =============================

Drive: hdb ___________________ _____________________________________________________
Note: sector size is 2048 (not 512)

Disk /dev/hdb: 1393 MB, 1393655808 bytes
255 heads, 63 sectors/track, 42 cylinders, total 680496 sectors
Units = sectors of 1 * 2048 = 2048 bytes

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x72b00fab

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   976,769,023   976,766,976   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x023dec43

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   976,751,999   976,751,937   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x023dec4c

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048   976,771,071   976,769,024   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x87d1cb24

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63   729,093,959   729,093,897   7 HPFS/NTFS
/dev/sdd2    *    729,093,960   976,768,064   247,674,105   5 Extended
/dev/sdd5         970,904,340   976,768,064     5,863,725  82 Linux swap / Solaris
/dev/sdd6         729,094,086   960,976,169   231,882,084  83 Linux
/dev/sdd7         960,976,233   970,888,274     9,912,042  82 Linux swap / Solaris


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x54b32ee1

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *          2,048   976,771,071   976,769,024   7 HPFS/NTFS


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd5d905b9

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *          2,048   976,771,071   976,769,024   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="2AE65491E6545F5F" LABEL="Gawd Its Phat" TYPE="ntfs" 
/dev/sdb1: UUID="1ED0FC2AD0FC09B3" TYPE="ntfs" 
/dev/sdc1: UUID="52A49168A4914F7B" LABEL="Fatterester ***" TYPE="ntfs" 
/dev/sdd1: UUID="DE701B10701AEF51" TYPE="ntfs" 
/dev/sdd5: UUID="04021d3d-1877-4c7e-980b-77bbe905bc39" TYPE="swap" 
/dev/sdd6: UUID="e5326290-1598-4d25-a3c2-ccc39029a92e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdd7: UUID="7c6b3ccd-3734-4cdb-89b3-23032fbb4c30" TYPE="swap" 
/dev/sde1: UUID="3830DD4330DD08B0" TYPE="ntfs" 
/dev/sdf1: UUID="D49861C09861A22A" LABEL="Fatter ***" TYPE="ntfs" 

=============================== "mount" output: ===============================

tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/hdb on /media/cdrom0 type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)


=========================== sdd6/boot/grub/menu.lst: ===========================



## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0


timeout        20

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue




title        Ubuntu
root            (hd3,5)
kernel        /boot/vmlinuz-2.6.29.4 root=/dev/sdd6 ro
initrd        /boot/initrd.img-2.6.29.4
quiet

title        Ubuntu (recovery mode)
root            (hd3,5)
kernel        /boot/vmlinuz-2.6.29.4 root=/dev/sdd6 ro  single
initrd        /boot/initrd.img-2.6.29.4

title        Ubuntu memtest86+
root            (hd4,5)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title        Windows 7
root        (hd3,0)
savedefault
map        (hd0) (hd4)
map        (hd4) (hd0)
chainloader    +1


=============================== sdd6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdd6
UUID=e5326290-1598-4d25-a3c2-ccc39029a92e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdd7
UUID=7c6b3ccd-3734-4cdb-89b3-23032fbb4c30 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdd6: Location of files loaded by Grub: ===================


 393.0GB: boot/grub/menu.lst
 393.1GB: boot/grub/stage2
 393.0GB: boot/initrd.img-2.6.29.4
 393.0GB: boot/vmlinuz-2.6.29.4
 393.0GB: initrd.img
 393.0GB: initrd.img.old
 393.0GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

hda 
```


I changed the HD from (hd4,5) to (hd3,5) and even tried, hd 3,6 3,7 3,4   etc with no luck. and windows is still broke

---

### Post by darkod on 2009-12-14
You're right, it is a mess. :)
Look at the start of the results:
[COLOR=Red]=> Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #3 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.[/COLOR]

This shows that your /dev/sdd is called boot drive #3 which I guess would mean hd2. In menu.lst try to set the ubuntu entries with (hd2,5).
Also use hd2 in the windows entry but I don't think win7 will work. Towards the top of the results look at sdd1 description. You are missing win7 booting files /bootmgr and /boot/BCD from there. But you do have them on sda1, sde1 and sdf1. All over the place but not where they should be, in sdd1.

Try if ubuntu will boot with (hd2,5) and also tell me whether you have ubuntu 9.04 cd or earlier version? Not 9.10.

---

### Post by Frostywars on 2009-12-14
Amazing, that fixed linux. I also changed the hd number to the windows partition but its telling me the bootmgr is missing. 

I tried the cd repair, nothing. If I try the command, "bootrec /fixboot" from command prompt, you think I will break grub?

---

### Post by darkod on 2009-12-14
> **Frostywars said:**
> Amazing, that fixed linux. I also changed the hd number to the windows partition but its telling me the bootmgr is missing. 

I tried the cd repair, nothing. If I try the command, "bootrec /fixboot" from command prompt, you think I will break grub?

Yes, it should break grub but that's not an issue because you can easily restore it. That's why I asked if you had 9.04 cd. Because you have /boot/grub/stage2 and /boot/grub/menu.lst files, you have gub1, or grub legacy. The new 9.10 comes with grub2 and it can NOT be used to restore grub1.
But if you have 9.04, that can restore it because it uses grub1.
Also, before trying to repair the windows mbr set /dev/sdd disk as first in boot order in BIOS (I guess it already is). Windows requires that drive to be first in BIOS before repairing the MBR. Then use the manual commands from here (scroll to vista/7 section:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

After that, boot with 9.04 cd, Try Ubuntu option, and use the procedure to restore grub1 for 9.04 or before version from the same link as above.

---

### Post by Frostywars on 2009-12-14
WOW

ok, I ran the Windows 7 repair, and read through the test results. Windows was seeing the 4th HD as the 1st. So I went back to grub and changed the (hd2,5) to (hd0,0) just for the hell of it and now my windows 7 AND Linux are working perfectly. :popcorn:;):D:o:):P:KS

Im running ubuntu 8.10


Thank you very much for all your help. :D

---

### Post by darkod on 2009-12-14
No problem. Enjoy it now, you deserved it. :)

PS. From what you said now it seems /dev/sda was first in boot order all the time, and not /dev/sdd. If you see the results file there is grub on /dev/sda too, you might have been booting it all this time. That's why for multiple drives it's essential to control the order of the drives and where your bootloader (grub) is. Anyway, it's working now.

---

