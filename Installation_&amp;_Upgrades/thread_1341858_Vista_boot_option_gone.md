---
title: "Vista boot option gone?"
date: 2009-11-30
forum: Installation &amp; Upgrades
---

### Post by RC-ROi92 on 2009-11-30
Hi there. 

Just upgraded to Ubuntu 9.10. 

Installation went by perfectly and Ubuntu runs perfectly. Now i'm running a dual boot with Windows Vista side by side. And when i rebooted the windows vista boot option was gone. This must be because of menu.lst being reset. Though isn't it supposed to automatically detect windows partitions? 

Some help for making the vista boot option would be lovely

Thanks

I'm a complete noob when it comes to Linux so any help would be appreciated.

---

### Post by audiomick on 2009-11-30
I think the command is

```
sudo update-grub
```

---

### Post by RC-ROi92 on 2009-11-30
This did update my bootloader, but unfortunately did not fix my problem. I still have no vista option. I'm afraid that ubuntu has overrided my vista partition, as my OS partition is now very full(only 128 mb left).

---

### Post by darkod on 2009-11-30
In terminal execute:
sudo fdisk -l (small L)

That will show you all partitions and their filesystems.

---

### Post by RC-ROi92 on 2009-11-30
> **darkod said:**
> In terminal execute:
sudo fdisk -l (small L)

That will show you all partitions and their filesystems.

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+  de  Dell Utility
/dev/sda2              11        1316    10485760    7  HPFS/NTFS
/dev/sda3   *        1316       12891    92974025    7  HPFS/NTFS
/dev/sda4           12892       14594    13672340    f  W95 Ext'd (LBA)
/dev/sda5           14333       14594     2096128   dd  Unknown
/dev/sda6           12892       14265    11036623+  83  Linux
/dev/sda7           14266       14332      538146   82  Linux swap / Solaris

Partition table entries are not in disk order

that's the result. What now? :D

---

### Post by darkod on 2009-11-30
Well you see /dev/sda3 is 93GB ntfs, I guess your vista. The partition is there, first of all.

Read post #2 here from presence:
[http://ubuntuforums.org/showthread.php?t=1341553](http://ubuntuforums.org/showthread.php?t=1341553)

Post back the results.txt file and that will show your boot process. It will be easier to diagnose.

---

### Post by RC-ROi92 on 2009-11-30
Thank you very much! :) I'm loving the hospitality I'm getting here :) 

Here's the info: 

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /BOOT.INI /bootmgr /BOOTMGR /ntldr /NTLDR 
                       /NTDETECT.COM /ntdetect.com

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x18000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       160,649       160,587  de Dell Utility
/dev/sda2             161,792    21,133,311    20,971,520   7 HPFS/NTFS
/dev/sda3    *     21,133,312   207,081,361   185,948,050   7 HPFS/NTFS
/dev/sda4         207,093,976   234,438,655    27,344,680   f W95 Ext d (LBA)
/dev/sda5         230,246,400   234,438,655     4,192,256  dd 
/dev/sda6         207,093,978   229,167,224    22,073,247  83 Linux
/dev/sda7         229,167,288   230,243,579     1,076,292  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D7-0306" TYPE="vfat" 
/dev/sda2: UUID="36F48F06F48EC797" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda3: UUID="9CC0928CC0926C70" LABEL="OS" TYPE="ntfs" 
/dev/sda5: LABEL="MEDIADIRECT" UUID="7896-A09C" TYPE="vfat" 
/dev/sda6: UUID="341a9304-404a-48f0-9240-e11e742af7a7" TYPE="ext3" 
/dev/sda7: UUID="5c0168a9-c387-4931-bec7-cfe1b2981efc" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda3 on /media/OS type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/roi/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=roi)


================================ sda5/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768 

================================ sda5/BOOT.INI: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768 

=========================== sda6/boot/grub/menu.lst: ===========================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=341a9304-404a-48f0-9240-e11e742af7a7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=341a9304-404a-48f0-9240-e11e742af7a7

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title        Ubuntu 9.10, kernel 2.6.31-15-generic
uuid        341a9304-404a-48f0-9240-e11e742af7a7
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=341a9304-404a-48f0-9240-e11e742af7a7 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-15-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid        341a9304-404a-48f0-9240-e11e742af7a7
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=341a9304-404a-48f0-9240-e11e742af7a7 ro  single
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 9.10, memtest86+
uuid        341a9304-404a-48f0-9240-e11e742af7a7
kernel        /boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Dell Utility Partition
root        (hd0,0)
savedefault
makeactive
chainloader    +1





=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda6 :
UUID=341a9304-404a-48f0-9240-e11e742af7a7 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda7 :
UUID=5c0168a9-c387-4931-bec7-cfe1b2981efc none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda3 /media/OS ntfs-3g defaults,locale=en_US.UTF-8 0 0

=================== sda6: Location of files loaded by Grub: ===================


 106.0GB: boot/grub/menu.lst
 106.0GB: boot/grub/stage2
 106.0GB: boot/initrd.img-2.6.28-16-generic
 106.0GB: boot/initrd.img-2.6.31-15-generic
 106.0GB: boot/vmlinuz-2.6.28-16-generic
 106.0GB: boot/vmlinuz-2.6.31-15-generic
 106.0GB: initrd.img
 106.0GB: initrd.img.old
 106.0GB: vmlinuz
 106.0GB: vmlinuz.old
```

---

### Post by darkod on 2009-11-30
OK, if you start reading from the top, there are few things to point out:
grub 0.97 is installed which means grub1 (1.97 is grub2 don't ask why :) )
sda3 is Windows Vista
sda5 is Windows XP or at least some traces of XP that the script can pick up
sda6 is your Ubuntu 9.10

Little bit below, the label of sda5 is MEDIADIRECT. Not sure but this would be remains of Windows XP Media Centre I guess. There was similar thread few weeks ago, and as soon as that partition was deleted the problem was solved. Are you using anything from that partition and do you have working XP at all? You mentioned that you have only Vista.

That sda5 partition seems to be 4GB. Unless you use it, it's probably safe to delete it. Your Dell Utility partition is sda1 and the Recovery is sda2. So this sda5 doesn't look like having any role in the recovery if you ever need that.

This is only my opinion, I rarely recommend people to delete partitions, but it looks like it will help solving this, either just by deleting it or few extra steps after that.
How do you feel about it? Anything important on that 4GB partition?

---

### Post by oldfred on 2009-11-30
You upgraded so you still have old grub and menu.lst

I doubt if you want to boot this:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Dell Utility Partition
root        (hd0,0)
savedefault
makeactive
chainloader    +1

Change to this, makeactive not require if boot flag set (*):

title        Vista on sda3
root        (hd0,2)
savedefault
chainloader    +1

I do not know what sda5 is the media direct partition?

To check data use:
First update & houseclean
HouseKeeping:
sudo apt-get update 
sudo apt-get upgrade 
sudo apt-get autoremove
# removes .deb and other files used by synaptic to install
sudo apt-get autoclean

Check partition use:
df -Th | sort

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB

---

### Post by RC-ROi92 on 2009-11-30
I only use vista. And this is probably something from the mediacenter(who the hell uses that? ). And i have never used anything from that partition.

So how do we proceed? 

I really feel like a know nothing :D But still am loving the look and feel and the efficiency of ubuntu.

---

### Post by darkod on 2009-11-30
Because you can't boot Vista I guess you are now in Ubuntu. Open system -> administration -> gparted. It's best although ubuntu has alternative partition manager. If Gparted is not there open terminal first and do:
sudo apt-get install gparted

After you open gparted it will show you all the partitions on the disk, in a graphical layout on top and as a list below that.
If /dev/sda5 on that list has an icon like keys that means it's mounted and you can't delete it like that. In that case right-click on it and do Unmount from the options that show up.
After that right-click on it again and select Delete. That will just schedule the operation, it won't delete it immediately.
After that double check you have selected correct partition, and you're happy with the choice. Then only click on the big green tick mark icon and gparted will execute the operation.

I'm pretty sure this will sort you out. Because you use grub1 and not the automatic grub2 you might need to enter few command after, but we'll see about that when the time comes.
Since you are not using the partition even without this problem it is good practice not to keep unused 4GB partitions, use the space instead.
When working with Gparted be VERY CAREFUL when selecting the partition and all operations.

---

### Post by RC-ROi92 on 2009-11-30
> **oldfred said:**
> You upgraded so you still have old grub and menu.lst

I doubt if you want to boot this:
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Dell Utility Partition
root        (hd0,0)
savedefault
makeactive
chainloader    +1

Change to this, makeactive not require if boot flag set (*):

title        Vista on sda3
root        (hd0,2)
savedefault
chainloader    +1

I do not know what sda5 is the media direct partition?

To check data use:
First update & houseclean
HouseKeeping:
sudo apt-get update 
sudo apt-get upgrade 
sudo apt-get autoremove
# removes .deb and other files used by synaptic to install
sudo apt-get autoclean

Check partition use:
df -Th | sort

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB


Thanks I'm now running vista again! :) 

and Darkod thank you for taking the time to teach me the stuff! It was a great learning experience and it was a great help!

---

