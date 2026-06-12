---
title: "Grub is too slow to boot"
date: 2010-03-18
forum: Installation &amp; Upgrades
---

### Post by z_diver on 2010-03-18
When booting a fresh install of Karmic 9.10 grub grumbles quite a bit.  I do have 2 600gb sata drives with various partitions but never have the older grubs taken a solid 15 seconds to sort out the drives before launching.

Is this typical for other users?

---

### Post by daddyjames on 2010-03-18
I have had a similar issue with grub taking a LOOONG time to boot the system. Operating on a 64 bit, Wiindows 7/Ubuntu (installed on separate harddrives).  Intel i7 860 cpu, 12 gb ram.  Just installed ubuntu 4 days ago.

---

### Post by presence1960 on 2010-03-18
> **z_diver said:**
> When booting a fresh install of Karmic 9.10 grub grumbles quite a bit.  I do have 2 600gb sata drives with various partitions but never have the older grubs taken a solid 15 seconds to sort out the drives before launching.

Is this typical for other users?

Let's take a look at what you have first. Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

 This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by oldfred on 2010-03-18
If you want specific help post presence's recommended boot_info_script that documents the details of your boot.

There is a known bug in grub on multi-drive systems that adds about 20 secs.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)
Slow boot, multi drives, known issue, move boot to same drive & adjust BIOS
sudo dpkg-reconfigure grub-pc
Very long boot solved with experimental grub1.98 post8
[http://ubuntuforums.org/showthread.php?t=1367488](http://ubuntuforums.org/showthread.php?t=1367488)
Slow boot change device.map
[http://ubuntuforums.org/showthread.php?t=1313207](http://ubuntuforums.org/showthread.php?t=1313207)

---

### Post by z_diver on 2010-03-18
OK, I decided to to some comunity service and installed Felix's PPA and grub 1.98.  The actual installation process took quite a bit longer than I thought it might.  After a 3 to 4 minute install I was prompted for what I'd like to do about grub:  I chose to use the package maintainer's version (not selected by default) and it took another 2 min to finish that.  I'm writing this before rebooting because if I can't get back in at least there will be some record of what went wrong! ;)

---

### Post by z_diver on 2010-03-18
Well, I made it back but on an earlier OS.  Grub 1.98 is uses a nice graphical boot loader (finally) but not one choice worked.  Luckily by selecting the startup disk through my Bios I was able to boot from an earlier version of grub residing my second hard sata drive which still worked perfectly.

Admittedly, I'm a an Ubuntu fanboy but this is a real mess!  Here I've tried four individual 9.10 installs on 3 separate machines and each one of them has ultimately been unable to boot after upgrades.  That's worse than beta track records.  The reason I initially liked Ubuntu was because of it's inherant stability!!! :lolflag:

---

### Post by z_diver on 2010-03-18
I redownloaded the script which really does work wonders.  Here is it's entire output.



```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 5.10 "Breezy Badger"
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d005c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   506,368,799   506,368,737  83 Linux
/dev/sda2         506,368,800   510,465,374     4,096,575  82 Linux swap / Solaris
/dev/sda3         510,465,375   586,067,264    75,601,890  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004ce4e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    82,043,954    82,043,892  83 Linux
/dev/sdb2    *     82,043,955   183,767,534   101,723,580  83 Linux
/dev/sdb3         185,872,050   188,281,799     2,409,750  82 Linux swap / Solaris
/dev/sdb4         188,281,800   585,264,014   396,982,215  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        af66c246-af24-45d4-8369-22ed880770cc   ext3       Backups                       
/dev/sda2        1d77ac44-5ba1-447f-839b-7afde2ee764f   swap                                     
/dev/sda3        bd083dc5-0d01-4d53-bc86-119cd6aa4a31   ext3                                     
/dev/sdb1        908e6c12-ae7d-457b-bacd-e37d7337e1c3   ext4       9.10                          
/dev/sdb2        1356716e-f848-46ef-8e5a-5bb2e2b705f2   ext3       8.10                          
/dev/sdb3        3b858d09-1df1-4dce-b2fc-94e519cac9f1   swap                                     
/dev/sdb4        7582600e-704f-4966-8c46-cf39f8636d0a   ext3       old-homes                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb2        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/scd0        /media/cdrom1            iso9660    (ro,nosuid,nodev,utf8,user=chuckh)


=========================== sda3/boot/grub/menu.lst: ===========================

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title        Ubuntu, kernel 2.6.12-10-386 
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.12-10-386 root=/dev/sda3 ro quiet splash
initrd        /boot/initrd.img-2.6.12-10-386
savedefault
boot

title        Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.12-10-386 root=/dev/sda3 ro single
initrd        /boot/initrd.img-2.6.12-10-386
boot

title        Ubuntu, memtest86+
root        (hd0,2)
kernel        /boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title        SUSE LINUX 10.0 (on /dev/hda3)
root        (hd0,2)
kernel        /boot/vmlinuz root=/dev/hda3 vga=0x31a selinux=0 resume=/dev/hda2 splash=silent showopts 
initrd        /boot/initrd
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title        Failsafe -- SUSE LINUX 10.0 (on /dev/hda3)
root        (hd0,2)
kernel        /boot/vmlinuz root=/dev/hda3 vga=normal showopts ide=nodma apm=off acpi=off noresume selinux=0 nosmp noapic maxcpus=0 edd=off 3 
initrd        /boot/initrd
savedefault
boot


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1    /mnt/sata    ext3    defaults,errors=remount-ro 0    1
/dev/sda3    /        ext3    defaults,errors=remount-ro 0    1
/dev/sdb4       /mnt/sdb4       ext3    defaults,errors=remount-ro 0    1
#/dev/hda5       none            swap    sw        0    0
#/dev/hdb2    /mnt/200    ext3    defaults,errors=remount-ro 0    1    
/dev/sda2       none            swap    sw        0    0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

=================== sda3: Location of files loaded by Grub: ===================


 277.6GB: boot/grub/menu.lst
 277.6GB: boot/grub/stage2
 277.5GB: boot/initrd.img-2.6.12-10-386
 277.6GB: boot/vmlinuz-2.6.12-10-386
 277.5GB: initrd.img
 277.6GB: vmlinuz

=========================== sdb2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=1356716e-f848-46ef-8e5a-5bb2e2b705f2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1356716e-f848-46ef-8e5a-5bb2e2b705f2

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

title        Ubuntu 8.10, kernel 2.6.27-11-generic
uuid        1356716e-f848-46ef-8e5a-5bb2e2b705f2
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=1356716e-f848-46ef-8e5a-5bb2e2b705f2 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid        1356716e-f848-46ef-8e5a-5bb2e2b705f2
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=1356716e-f848-46ef-8e5a-5bb2e2b705f2 ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        1356716e-f848-46ef-8e5a-5bb2e2b705f2
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=1356716e-f848-46ef-8e5a-5bb2e2b705f2 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        1356716e-f848-46ef-8e5a-5bb2e2b705f2
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=1356716e-f848-46ef-8e5a-5bb2e2b705f2 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        1356716e-f848-46ef-8e5a-5bb2e2b705f2
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title        Ubuntu, kernel 2.6.12-10-386 (on /dev/sda3)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.12-10-386 root=/dev/sda3 ro quiet splash 
initrd        /boot/initrd.img-2.6.12-10-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title        Ubuntu, kernel 2.6.12-10-386 (recovery mode) (on /dev/sda3)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.12-10-386 root=/dev/sda3 ro single 
initrd        /boot/initrd.img-2.6.12-10-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title        Ubuntu, memtest86+ (on /dev/sda3)
root        (hd0,2)
kernel        /boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu, kernel 2.6.20-17-generic (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.20-17-generic root=UUID=0fd7a4dd-37a7-4b28-8dba-33fe3a9e0d4b ro quiet splash 
initrd        /boot/initrd.img-2.6.20-17-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu, kernel 2.6.20-17-generic (recovery mode) (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.20-17-generic root=UUID=0fd7a4dd-37a7-4b28-8dba-33fe3a9e0d4b ro single 
initrd        /boot/initrd.img-2.6.20-17-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu, kernel 2.6.20-16-generic (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=0fd7a4dd-37a7-4b28-8dba-33fe3a9e0d4b ro quiet splash 
initrd        /boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=0fd7a4dd-37a7-4b28-8dba-33fe3a9e0d4b ro single 
initrd        /boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu, kernel 2.6.20-15-generic (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=0fd7a4dd-37a7-4b28-8dba-33fe3a9e0d4b ro quiet splash 
initrd        /boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=0fd7a4dd-37a7-4b28-8dba-33fe3a9e0d4b ro single 
initrd        /boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu, memtest86+ (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/memtest86+.bin  
savedefault
boot


=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=1356716e-f848-46ef-8e5a-5bb2e2b705f2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=1d77ac44-5ba1-447f-839b-7afde2ee764f none            swap    sw              0       0
# /dev/sdb3
UUID=3b858d09-1df1-4dce-b2fc-94e519cac9f1 none            swap    sw              0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


  66.5GB: boot/grub/menu.lst
  66.5GB: boot/grub/stage2
  66.4GB: boot/initrd.img-2.6.27-11-generic
  66.4GB: boot/initrd.img-2.6.27-7-generic
  66.4GB: boot/vmlinuz-2.6.27-11-generic
  66.4GB: boot/vmlinuz-2.6.27-7-generic
  66.4GB: initrd.img
  66.4GB: initrd.img.old
  66.4GB: vmlinuz
  66.4GB: vmlinuz.old
```

---

### Post by oldfred on 2010-03-18
The script says it cannot mount your sdb1, so we cannot see if the files are there or not:
    Mounting failed:
mount: unknown filesystem type 'ext4'

But the rest shows it. Can you see your normal boot and boot/grub folders in sdb?

Your grub in sda tries to load from sda1 which you have labeled backup and shows no grub files.

I am wondering if your grub legacy(0.97) is too old to boot into ext4 partition. It was either 9.04 or later that old grub was patched to be able to see the new ext4 partitions.

---

### Post by z_diver on 2010-03-18
I made a 9.10 CD and rebooted with that.  Obviously that reads ext4 fine.  After thinking about it, I bet I could have dl'ed a driver for 8.10 to read ext4 though.  


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 5.10 "Breezy Badger"
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d005c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   506,368,799   506,368,737  83 Linux
/dev/sda2         506,368,800   510,465,374     4,096,575  82 Linux swap / Solaris
/dev/sda3         510,465,375   586,067,264    75,601,890  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004ce4e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    82,043,954    82,043,892  83 Linux
/dev/sdb2    *     82,043,955   183,767,534   101,723,580  83 Linux
/dev/sdb3         185,872,050   188,281,799     2,409,750  82 Linux swap / Solaris
/dev/sdb4         188,281,800   585,264,014   396,982,215  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        af66c246-af24-45d4-8369-22ed880770cc   ext3       Backups                       
/dev/sda2        1d77ac44-5ba1-447f-839b-7afde2ee764f   swap                                     
/dev/sda3        bd083dc5-0d01-4d53-bc86-119cd6aa4a31   ext3                                     
/dev/sdb1        908e6c12-ae7d-457b-bacd-e37d7337e1c3   ext4       9.10                          
/dev/sdb2        1356716e-f848-46ef-8e5a-5bb2e2b705f2   ext3       8.10                          
/dev/sdb3        3b858d09-1df1-4dce-b2fc-94e519cac9f1   swap                                     
/dev/sdb4        7582600e-704f-4966-8c46-cf39f8636d0a   ext3       old-homes                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=========================== sda3/boot/grub/menu.lst: ===========================

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title        Ubuntu, kernel 2.6.12-10-386 
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.12-10-386 root=/dev/sda3 ro quiet splash
initrd        /boot/initrd.img-2.6.12-10-386
savedefault
boot

title        Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.12-10-386 root=/dev/sda3 ro single
initrd        /boot/initrd.img-2.6.12-10-386
boot

title        Ubuntu, memtest86+
root        (hd0,2)
kernel        /boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title        SUSE LINUX 10.0 (on /dev/hda3)
root        (hd0,2)
kernel        /boot/vmlinuz root=/dev/hda3 vga=0x31a selinux=0 resume=/dev/hda2 splash=silent showopts 
initrd        /boot/initrd
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda3.
title        Failsafe -- SUSE LINUX 10.0 (on /dev/hda3)
root        (hd0,2)
kernel        /boot/vmlinuz root=/dev/hda3 vga=normal showopts ide=nodma apm=off acpi=off noresume selinux=0 nosmp noapic maxcpus=0 edd=off 3 
initrd        /boot/initrd
savedefault
boot


=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1    /mnt/sata    ext3    defaults,errors=remount-ro 0    1
/dev/sda3    /        ext3    defaults,errors=remount-ro 0    1
/dev/sdb4       /mnt/sdb4       ext3    defaults,errors=remount-ro 0    1
#/dev/hda5       none            swap    sw        0    0
#/dev/hdb2    /mnt/200    ext3    defaults,errors=remount-ro 0    1    
/dev/sda2       none            swap    sw        0    0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

=================== sda3: Location of files loaded by Grub: ===================


 277.6GB: boot/grub/menu.lst
 277.6GB: boot/grub/stage2
 277.5GB: boot/initrd.img-2.6.12-10-386
 277.6GB: boot/vmlinuz-2.6.12-10-386
 277.5GB: initrd.img
 277.6GB: vmlinuz

=========================== sdb1/boot/grub/grub.cfg: ===========================

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
insmod ext2
set root=(hd1,1)
search --no-floppy --fs-uuid --set 908e6c12-ae7d-457b-bacd-e37d7337e1c3
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
  insmod ext2
  set root=(hd1,1)
  search --no-floppy --fs-uuid --set 908e6c12-ae7d-457b-bacd-e37d7337e1c3
  insmod gfxmenu
  set theme=($root)/boot/grub/debian-theme/theme.txt
  set menuviewer=gfxmenu
fi
insmod ext2
set root=(hd1,1)
search --no-floppy --fs-uuid --set 908e6c12-ae7d-457b-bacd-e37d7337e1c3
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
insmod ext2
set root=(hd1,1)
search --no-floppy --fs-uuid --set 908e6c12-ae7d-457b-bacd-e37d7337e1c3
insmod png
loadfont /boot/grub/dejavu_sans_10.pf2
loadfont /boot/grub/dejavu_sans_12.pf2
loadfont /boot/grub/dejavu_sans_bold_14.pf2
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, with Linux 2.6.31-20-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set gfxpayload=keep
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 908e6c12-ae7d-457b-bacd-e37d7337e1c3
    echo    Loading Linux 2.6.31-20-generic ...
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=908e6c12-ae7d-457b-bacd-e37d7337e1c3 ro   quiet splash
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, with Linux 2.6.31-20-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set gfxpayload=keep
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 908e6c12-ae7d-457b-bacd-e37d7337e1c3
    echo    Loading Linux 2.6.31-20-generic ...
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=908e6c12-ae7d-457b-bacd-e37d7337e1c3 ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, with Linux 2.6.31-19-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set gfxpayload=keep
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 908e6c12-ae7d-457b-bacd-e37d7337e1c3
    echo    Loading Linux 2.6.31-19-generic ...
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=908e6c12-ae7d-457b-bacd-e37d7337e1c3 ro   quiet splash
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, with Linux 2.6.31-19-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set gfxpayload=keep
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 908e6c12-ae7d-457b-bacd-e37d7337e1c3
    echo    Loading Linux 2.6.31-19-generic ...
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=908e6c12-ae7d-457b-bacd-e37d7337e1c3 ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, with Linux 2.6.31-14-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set gfxpayload=keep
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 908e6c12-ae7d-457b-bacd-e37d7337e1c3
    echo    Loading Linux 2.6.31-14-generic ...
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=908e6c12-ae7d-457b-bacd-e37d7337e1c3 ro   quiet splash
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, with Linux 2.6.31-14-generic (recovery mode)" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set gfxpayload=keep
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 908e6c12-ae7d-457b-bacd-e37d7337e1c3
    echo    Loading Linux 2.6.31-14-generic ...
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=908e6c12-ae7d-457b-bacd-e37d7337e1c3 ro single 
    echo    Loading initial ramdisk ...
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, kernel 2.6.12-10-386 (on /dev/sda3)" {
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set bd083dc5-0d01-4d53-bc86-119cd6aa4a31
    linux /boot/vmlinuz-2.6.12-10-386 root=/dev/sda3 ro quiet splash
    initrd /boot/initrd.img-2.6.12-10-386
}
menuentry "Ubuntu, kernel 2.6.12-10-386 (recovery mode) (on /dev/sda3)" {
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set bd083dc5-0d01-4d53-bc86-119cd6aa4a31
    linux /boot/vmlinuz-2.6.12-10-386 root=/dev/sda3 ro single
    initrd /boot/initrd.img-2.6.12-10-386
}
menuentry "Ubuntu, memtest86+ (on /dev/sda3)" {
    insmod ext2
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set bd083dc5-0d01-4d53-bc86-119cd6aa4a31
    linux /boot/memtest86+.bin 
}
menuentry "Ubuntu 8.10, kernel 2.6.27-11-generic (on /dev/sdb2)" {
    insmod ext2
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set 1356716e-f848-46ef-8e5a-5bb2e2b705f2
    linux /boot/vmlinuz-2.6.27-11-generic root=UUID=1356716e-f848-46ef-8e5a-5bb2e2b705f2 ro quiet splash
    initrd /boot/initrd.img-2.6.27-11-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode) (on /dev/sdb2)" {
    insmod ext2
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set 1356716e-f848-46ef-8e5a-5bb2e2b705f2
    linux /boot/vmlinuz-2.6.27-11-generic root=UUID=1356716e-f848-46ef-8e5a-5bb2e2b705f2 ro single
    initrd /boot/initrd.img-2.6.27-11-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-7-generic (on /dev/sdb2)" {
    insmod ext2
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set 1356716e-f848-46ef-8e5a-5bb2e2b705f2
    linux /boot/vmlinuz-2.6.27-7-generic root=UUID=1356716e-f848-46ef-8e5a-5bb2e2b705f2 ro quiet splash
    initrd /boot/initrd.img-2.6.27-7-generic
}
menuentry "Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode) (on /dev/sdb2)" {
    insmod ext2
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set 1356716e-f848-46ef-8e5a-5bb2e2b705f2
    linux /boot/vmlinuz-2.6.27-7-generic root=UUID=1356716e-f848-46ef-8e5a-5bb2e2b705f2 ro single
    initrd /boot/initrd.img-2.6.27-7-generic
}
menuentry "Ubuntu 8.10, memtest86+ (on /dev/sdb2)" {
    insmod ext2
    set root=(hd1,2)
    search --no-floppy --fs-uuid --set 1356716e-f848-46ef-8e5a-5bb2e2b705f2
    linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=908e6c12-ae7d-457b-bacd-e37d7337e1c3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=1d77ac44-5ba1-447f-839b-7afde2ee764f none            swap    sw              0       0
# swap was on /dev/sdb3 during installation
UUID=3b858d09-1df1-4dce-b2fc-94e519cac9f1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


   2.9GB: boot/grub/core.img
   3.1GB: boot/grub/grub.cfg
   1.3GB: boot/initrd.img-2.6.31-14-generic
   1.9GB: boot/initrd.img-2.6.31-19-generic
  12.9GB: boot/initrd.img-2.6.31-20-generic
   1.1GB: boot/vmlinuz-2.6.31-14-generic
    .6GB: boot/vmlinuz-2.6.31-19-generic
  23.7GB: boot/vmlinuz-2.6.31-20-generic
  12.9GB: initrd.img
   1.9GB: initrd.img.old
  23.7GB: vmlinuz
    .6GB: vmlinuz.old

=========================== sdb2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=1356716e-f848-46ef-8e5a-5bb2e2b705f2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=1356716e-f848-46ef-8e5a-5bb2e2b705f2

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

title        Ubuntu 8.10, kernel 2.6.27-11-generic
uuid        1356716e-f848-46ef-8e5a-5bb2e2b705f2
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=1356716e-f848-46ef-8e5a-5bb2e2b705f2 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid        1356716e-f848-46ef-8e5a-5bb2e2b705f2
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=1356716e-f848-46ef-8e5a-5bb2e2b705f2 ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        1356716e-f848-46ef-8e5a-5bb2e2b705f2
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=1356716e-f848-46ef-8e5a-5bb2e2b705f2 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        1356716e-f848-46ef-8e5a-5bb2e2b705f2
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=1356716e-f848-46ef-8e5a-5bb2e2b705f2 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        1356716e-f848-46ef-8e5a-5bb2e2b705f2
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title        Ubuntu, kernel 2.6.12-10-386 (on /dev/sda3)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.12-10-386 root=/dev/sda3 ro quiet splash 
initrd        /boot/initrd.img-2.6.12-10-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title        Ubuntu, kernel 2.6.12-10-386 (recovery mode) (on /dev/sda3)
root        (hd0,2)
kernel        /boot/vmlinuz-2.6.12-10-386 root=/dev/sda3 ro single 
initrd        /boot/initrd.img-2.6.12-10-386
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title        Ubuntu, memtest86+ (on /dev/sda3)
root        (hd0,2)
kernel        /boot/memtest86+.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu, kernel 2.6.20-17-generic (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.20-17-generic root=UUID=0fd7a4dd-37a7-4b28-8dba-33fe3a9e0d4b ro quiet splash 
initrd        /boot/initrd.img-2.6.20-17-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu, kernel 2.6.20-17-generic (recovery mode) (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.20-17-generic root=UUID=0fd7a4dd-37a7-4b28-8dba-33fe3a9e0d4b ro single 
initrd        /boot/initrd.img-2.6.20-17-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu, kernel 2.6.20-16-generic (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=0fd7a4dd-37a7-4b28-8dba-33fe3a9e0d4b ro quiet splash 
initrd        /boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu, kernel 2.6.20-16-generic (recovery mode) (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.20-16-generic root=UUID=0fd7a4dd-37a7-4b28-8dba-33fe3a9e0d4b ro single 
initrd        /boot/initrd.img-2.6.20-16-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu, kernel 2.6.20-15-generic (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=0fd7a4dd-37a7-4b28-8dba-33fe3a9e0d4b ro quiet splash 
initrd        /boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu, kernel 2.6.20-15-generic (recovery mode) (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=0fd7a4dd-37a7-4b28-8dba-33fe3a9e0d4b ro single 
initrd        /boot/initrd.img-2.6.20-15-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Ubuntu, memtest86+ (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/memtest86+.bin  
savedefault
boot


=============================== sdb2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=1356716e-f848-46ef-8e5a-5bb2e2b705f2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=1d77ac44-5ba1-447f-839b-7afde2ee764f none            swap    sw              0       0
# /dev/sdb3
UUID=3b858d09-1df1-4dce-b2fc-94e519cac9f1 none            swap    sw              0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb2: Location of files loaded by Grub: ===================


  66.5GB: boot/grub/menu.lst
  66.5GB: boot/grub/stage2
  66.4GB: boot/initrd.img-2.6.27-11-generic
  66.4GB: boot/initrd.img-2.6.27-7-generic
  66.4GB: boot/vmlinuz-2.6.27-11-generic
  66.4GB: boot/vmlinuz-2.6.27-7-generic
  66.4GB: initrd.img
  66.4GB: initrd.img.old
  66.4GB: vmlinuz
  66.4GB: vmlinuz.old
```

---

### Post by z_diver on 2010-03-18
> **z_diver said:**
>  After thinking about it, I bet I could have dl'ed a driver for 8.10 to read ext4 though. 
Well, actually it doesn't look lik that's the case.  I have e2fsprogs installed in 8.10 which claims to provide support for ext4 file systems but file manager sure doesn't want to mount the 9.10 partition.

---

### Post by oldfred on 2010-03-18
Script now looks normal. Have you tried installing grub2 to sdb for your install from sdb1? That should eliminated the 20 sec delay and get you booting again.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Ubuntu install on sdb1
While in the LiveCD, open terminal and run:
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sdb

Then reboot and in Ubuntu:
sudo update-grub

---

### Post by z_diver on 2010-03-18
I'm somewhat hesitant to overwrite the 0.97 grub on sdb because it does at least allow me to boot into 8.10 effortlessly.

Is there any reason that the current 1.98 would not be working?  I don't see any errors but if anyone can please let me know.  

For what it's worth, I get a [COLOR=DarkRed]File not found[/COLOR] error no matter what I choose in the graphical 1.98 menu(which pops right up by the way) and upon pressing [COLOR=DarkRed]E[/COLOR] to edit commands it looks like grub is at least indicating [COLOR=DarkRed]set root (hd1,1)[/COLOR].  So ???

How difficult would it be to correct an error(if found) by hand?  As you may have noticed, I have 0 experience with grub2 though a little with grub.

Thanks!

---

### Post by oldfred on 2010-03-18
I do not understand how your grub2 is working? You have it in sda and it is looking at partition #1 on sda. The script shows nothing there. Is a grub directory in a non-standard location so the script is not seeing it. If you have grub only it should be like a grub only partition and you can edit the grub files just like any other version of grub2. 

 GRUB 2 has three main parts:

   1. /etc/default/grub - the file containing GRUB 2 menu settings.
   2. /etc/grub.d/ - the directory containing GRUB 2 menu creating scripts.
   3. /boot/grub/grub.cfg - the GRUB 2 configuration file, not editable.

---

### Post by presence1960 on 2010-03-19
> **z_diver said:**
> I'm somewhat hesitant to overwrite the 0.97 grub on sdb because it does at least allow me to boot into 8.10 effortlessly.

Is there any reason that the current 1.98 would not be working?  I don't see any errors but if anyone can please let me know.  

For what it's worth, I get a [COLOR=DarkRed]File not found[/COLOR] error no matter what I choose in the graphical 1.98 menu(which pops right up by the way) and upon pressing [COLOR=DarkRed]E[/COLOR] to edit commands it looks like grub is at least indicating [COLOR=DarkRed]set root (hd1,1)[/COLOR].  So ???

How difficult would it be to correct an error(if found) by hand?  As you may have noticed, I have 0 experience with grub2 though a little with grub.

Thanks!

Those who hesitate are lost! Do you want 9.10? Then this is what you need to do:

Boot the 9.10 LIve CD and choose "try ubuntu without any changes", when the desktop loads open a terminal and run ```
sudo mount /dev/sdb1 /mnt
```This will mount the 9.10 / partition. Next in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```This will put GRUB on MBR of sdb and you will now be able to boot all your OSs. Reboot without the Live CD & go into BIOS and set the sdb disk as first disk to boot in the hard disk boot order. Save changes to CMOS and boot into 9.10. Open a terminal and run ```
sudo update-grub
```this will update your GRUB menu for you.

---

### Post by daddyjames on 2010-03-19
(At the risk of being rude) I have been experiencing the same issue of boot time slowness.  

Don't want to step on anyone's toes - if I should open my own thread, please let me know.

I have been following along, and do not seem to be having the same difficulty of not seeing one of the drives/partitions . . . as far as I can determine.  

If appropriate, may I also dip my bucket in the well of wisdom, and see what may be causing the slow time?  Could it be because Grub 2 is installed in /dev/sda, but is looking for files in /dev/sdb (where ubuntu 9.10 is installed)?

Here is the Results.doc (if I have done it incorrectly, please have patience):
```
              Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=b1c95159-f0a6-4d76-a011-003ef46de78e)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/BCD

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848 1,929,236,479 1,929,029,632   7 HPFS/NTFS
/dev/sda3       1,929,236,480 1,953,521,663    24,285,184   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x75a701ae

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   988,479,449   988,479,387   7 HPFS/NTFS
/dev/sdb2         988,479,450 1,953,520,064   965,040,615   5 Extended
/dev/sdb5         988,479,513 1,914,385,724   925,906,212  83 Linux
/dev/sdb6       1,914,385,788 1,953,520,064    39,134,277  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        F8586B12586ACF46                       ntfs       SYSTEM                        
/dev/sda2        182A92A82A928284                       ntfs       HP                            
/dev/sda3        EA6A0E086A0DD26D                       ntfs       FACTORY_IMAGE                 
/dev/sdb1        769C48769C4832C3                       ntfs       HP2                           
/dev/sdb5        b1c95159-f0a6-4d76-a011-003ef46de78e   ext4                                     
/dev/sdb6        6c024c92-993b-4daa-a257-4f202ce968ac   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root=(hd1,5)
search --no-floppy --fs-uuid --set b1c95159-f0a6-4d76-a011-003ef46de78e
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
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set b1c95159-f0a6-4d76-a011-003ef46de78e
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=b1c95159-f0a6-4d76-a011-003ef46de78e ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set b1c95159-f0a6-4d76-a011-003ef46de78e
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=b1c95159-f0a6-4d76-a011-003ef46de78e ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set b1c95159-f0a6-4d76-a011-003ef46de78e
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b1c95159-f0a6-4d76-a011-003ef46de78e ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set b1c95159-f0a6-4d76-a011-003ef46de78e
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b1c95159-f0a6-4d76-a011-003ef46de78e ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set f8586b12586acf46
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set ea6a0e086a0dd26d
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=b1c95159-f0a6-4d76-a011-003ef46de78e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=6c024c92-993b-4daa-a257-4f202ce968ac none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 506.3GB: boot/grub/core.img
 506.9GB: boot/grub/grub.cfg
 506.8GB: boot/initrd.img-2.6.31-14-generic
 509.2GB: boot/initrd.img-2.6.31-20-generic
 506.7GB: boot/vmlinuz-2.6.31-14-generic
 509.0GB: boot/vmlinuz-2.6.31-20-generic
 509.2GB: initrd.img
 506.8GB: initrd.img.old
 509.0GB: vmlinuz
 506.7GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by z_diver on 2010-03-19
OK, this halfway worked.  I ran the commands you listed.  All good.  Upon entering bios I found no control over sata disks.  The only options were for cdrom/floppy/drive C up or down - on or off.  I exited and let it boot but now have just get: grub rescue> prompt.

I've checked a few threads concerning users that have gotten to the grub rescue> prompt but haven't figured out if any have successfully escaped.  ;)  FWIW I'll throw this out there tonight and check back in the morning... 

[COLOR=DarkRed]Should I try to switch the cables that go to the sata drives... the attachment points are a couple of years old and may be brittle?[/COLOR]

Well, thanks Presence and Fred for all the effort you've put into solving grub problems on these boards.  Your patience is much appreciated.

---

### Post by oldfred on 2010-03-19
z_diver
I have seen a lot of people say their BIOS does not let them select the drive to boot.
Could you please check again. It is not normally in the same place as the boot order selection. In the old days with ide it was a master/slave setting on the drive. The BIOS may call it something else, but I have touble believing that there is not a setting somewhere. 
If you move drive order on motherboard the sda & sdb settings will change and depending on how settings are throughout system, some changes may be required.

daddyjames
It would be better to have your own thread unless the only issue is solved by post #4 above. Have you moved grub and boot to the same drive as presence & I recommended to z_diver?

---

### Post by z_diver on 2010-03-19
I have a Dell PowerEdge 400SC, which is an older server class machine with Dell Bios rev A09.  While it has a 3 entries concerning boot options, and it looks very promissing from the outset none offer the ability to directly select which sata to boot from. Note: I downloaded the latest rev. from late 2006 but that comes in an .exe so unless I find a Win98 floppy I don't have an easy way to test it.

ATM I just press f12 on boot allowing accessing to the boot menu - select Secondary Sata to go directly to the working instance of grub on sdb.  I really think that in the short term, that's what I'm going to do. 

Below is the printout of [COLOR=DarkRed]sudo update-grub[/COLOR] which I ran after getting back into 9.10.  Any idea what video.lst is?

```
chuckh@arapito:~$ sudo update-grub
[sudo] password for chuckh: 
[COLOR=DarkRed]head: cannot open `/boot/grub/video.lst' for reading: No such file or directory[/COLOR]
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu (The Breezy Badger Release) (5.10) on /dev/sda3
Found Ubuntu 8.10 (8.10) on /dev/sdb2
done

```

---

### Post by oldfred on 2010-03-19
I do not have video.lst on my system, no idea what it was looking for. Is that listed somewhere in a config file by mistake?
More important does it boot ok? It seems to have automatically found all your systems.

I would think if you have a f12 - secondary SATA choice at boot that somewhere in BIOS you can switch primary and secondary drives as a default.

---

### Post by daddyjames on 2010-03-19
> **oldfred said:**
> z_diver
I have seen a lot of people say their BIOS does not let them select the drive to boot.
Could you please check again. It is not normally in the same place as the boot order selection. In the old days with ide it was a master/slave setting on the drive. The BIOS may call it something else, but I have touble believing that there is not a setting somewhere. 
If you move drive order on motherboard the sda & sdb settings will change and depending on how settings are throughout system, some changes may be required.

daddyjames
It would be better to have your own thread unless the only issue is solved by post #4 above. Have you moved grub and boot to the same drive as presence & I recommended to z_diver?
oldfred: No I have not done that just yet, missed that part when I scanned it over.  I will try it, and let you know how things turn out.  If I continue to have issues, I will open another thread.  Thank you for letting me know the proper thread etiquette.  

z_diver: apologies for intruding on this thread.  Good luck, I hope that your issues are solved soon.

---

### Post by z_diver on 2010-03-19
> **oldfred said:**
> I do not have video.lst on my system, no idea what it was looking for. Is that listed somewhere in a config file by mistake?
More important does it boot ok? It seems to have automatically found all your systems.

I would think if you have a f12 - secondary SATA choice at boot that somewhere in BIOS you can switch primary and secondary drives as a default.
I know... with three menu items and labels like Drive Conf, HD drive Sequence and Boot Sequence you'd THINK they'd have something.  But no, they all list hd C or cdrom and not the satas, at least in this ver of the bios.

I guess video.lst is a setting that came from felix zielcke's 1.98 Grub2 update.  No biggie.

By all means thank you for your help.  I guess they'll get Grub2 working soon but until then you guys will be saving a LOT of butts.  It's great to have someone that knows the limits and capabilities of the new bootloader.

Ciao!

---

