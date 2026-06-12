---
title: "trouble re-installing GRUB on MBR"
date: 2010-10-06
forum: Installation &amp; Upgrades
---

### Post by T-bone24 on 2010-10-06
Hi,
I've got a dual boot set up with Windows on my first hard drive and Ubuntu Lucid on my second.
Recently I had to Re-install Windows and it replaced GRUB on my master boot record.

On a long shot I tried to boot into Ubuntu by going into my boot options from my BIOS and booting into my secondary drive but this just brought up a GRUB command line.

So I booted into a Jaunty live cd (the Lucid live disk doesn't seem to like my graphics card) and in terminal I tried to run

```

sudo grub
root (hd0,0)
setup (hd0)

```after running the final line I get the error: "Error 17: Cannot mount selected partition".

I'm pretty certain that sda1 is my MBR so that would translate to (hd0,0) on GRUB right?

If it's any use to anyone here is my output of "fdisk -l";

```

Disk /dev/sda: 2000.3 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1aae7bbb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13      243202  1953410048    7  HPFS/NTFS

Disk /dev/sdb: 2000.3 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006b90a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1044     8385898+  82  Linux swap / Solaris
/dev/sdb2          121601      243202   976754688    7  HPFS/NTFS
/dev/sdb3            1045      121600   968366070    5  Extended
/dev/sdb5            1045      121600   968366038+  83  Linux

Partition table entries are not in disk order

```Any help is really appreciated.

---

### Post by ronparent on 2010-10-06
Download the Boot Info Script from this location: [http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055)

Run it and post the output (appears on the desktop) here. This should give readers enough information to suggest a fix. Thanks

---

### Post by oldfred on 2010-10-06
If you installed lucid you have grub2 unless you upgraded from 9.04. The boot info script will tell us for sure.

---

### Post by T-bone24 on 2010-10-07
The output of my boot info is:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks at sector 4090368 
    on boot drive #1 for the stage2 file. A stage2 file is at this location on 
    /dev/sdb. Stage2 looks on partition #1 for /boot/grub/grub.conf.

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

sdb1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sdb5 and 
                       looks at sector 16857683 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2000.3 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1aae7bbb

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848 3,907,026,943 3,906,820,096   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000.3 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0006b90a

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    16,771,859    16,771,797  82 Linux swap / Solaris
/dev/sdb2       1,953,515,520 3,907,024,895 1,953,509,376   7 HPFS/NTFS
/dev/sdb3          16,771,860 1,953,503,999 1,936,732,140   5 Extended
/dev/sdb5          16,771,923 1,953,503,999 1,936,732,077  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        FCFA2902FA28BB32                       ntfs       System Reserved               
/dev/sda2        7EF22BAFF22B6B1B                       ntfs                                     
/dev/sdb1        627d0c39-df51-4904-b082-e89ef6a2ef07   swap                                     
/dev/sdb2        80165E90165E86D6                       ntfs       Swap Space                    
/dev/sdb5        49c993cf-a5ae-432c-a8b2-db8198836cd2   ext4                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb2        /media/Swap Space        fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)


=========================== sdb5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=49c993cf-a5ae-432c-a8b2-db8198836cd2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=49c993cf-a5ae-432c-a8b2-db8198836cd2

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

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic
uuid        49c993cf-a5ae-432c-a8b2-db8198836cd2
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=49c993cf-a5ae-432c-a8b2-db8198836cd2 ro quiet splash 
initrd        /boot/initrd.img-2.6.32-24-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.32-24-generic (recovery mode)
uuid        49c993cf-a5ae-432c-a8b2-db8198836cd2
kernel        /boot/vmlinuz-2.6.32-24-generic root=UUID=49c993cf-a5ae-432c-a8b2-db8198836cd2 ro  single
initrd        /boot/initrd.img-2.6.32-24-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.31-22-generic
uuid        49c993cf-a5ae-432c-a8b2-db8198836cd2
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=49c993cf-a5ae-432c-a8b2-db8198836cd2 ro quiet splash 
initrd        /boot/initrd.img-2.6.31-22-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.31-22-generic (recovery mode)
uuid        49c993cf-a5ae-432c-a8b2-db8198836cd2
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=49c993cf-a5ae-432c-a8b2-db8198836cd2 ro  single
initrd        /boot/initrd.img-2.6.31-22-generic

title        Ubuntu 10.04.1 LTS, kernel 2.6.28-11-generic
uuid        49c993cf-a5ae-432c-a8b2-db8198836cd2
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=49c993cf-a5ae-432c-a8b2-db8198836cd2 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 10.04.1 LTS, kernel 2.6.28-11-generic (recovery mode)
uuid        49c993cf-a5ae-432c-a8b2-db8198836cd2
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=49c993cf-a5ae-432c-a8b2-db8198836cd2 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 10.04.1 LTS, memtest86+
uuid        49c993cf-a5ae-432c-a8b2-db8198836cd2
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=49c993cf-a5ae-432c-a8b2-db8198836cd2 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sdb1 during installation
UUID=627d0c39-df51-4904-b082-e89ef6a2ef07 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


  11.1GB: boot/grub/menu.lst
   8.6GB: boot/grub/stage2
   9.2GB: boot/initrd.img-2.6.28-11-generic
  13.5GB: boot/initrd.img-2.6.31-22-generic
  19.4GB: boot/initrd.img-2.6.32-24-generic
  11.1GB: boot/vmlinuz-2.6.28-11-generic
  19.6GB: boot/vmlinuz-2.6.31-22-generic
  16.9GB: boot/vmlinuz-2.6.32-24-generic
  19.4GB: initrd.img
  13.5GB: initrd.img.old
  16.9GB: vmlinuz
  19.6GB: vmlinuz.old
```

---

### Post by drs305 on 2010-10-07
While I would highly recommend Grub2 when you can boot to lucid, the boot info script shows that you have Grub legacy on the system. 

**It's been a while since I've installed Grub legacy so either wait for someone to verify the following unless you remember how Grub legacy works. **I believe it wouldn't mount (hd0,0), i.e. sda1, because that is your Windows partition. 

Currently Grub is installed on sdb's MBR and looks to sdb1 for it's files. They actually reside on sdb5. So the commands during the installation should be:
> 
root (hd1,4)
setup (hd1)


This would leave the sda MBR with Windows. You would have to make the computer boot the sdb drive first via the BIOS settings. You could put it on sda and specify (hd0) I suppose and leave sda as the boot drive.

---

### Post by T-bone24 on 2010-10-07
> **drs305 said:**
> Currently Grub is installed on sdb's MBR and looks to sdb1 for it's files. They actually reside on sdb5. So the commands during the installation should be:



Thank you so much, I could have sworn I already tried putting it on hd1,4 but it didn't work but I just tried it again after reading your post and it worked first time.

I'm going to leave this thread as un-solved for a while because ideally I would like grub on my MBR but at least I can get into Ubuntu now by manually selecting my second HD at start up.

---

### Post by drs305 on 2010-10-07
> **T-bone24 said:**
> Thank you so much, I could have sworn I already tried putting it on hd1,4 but it didn't work but I just tried it again after reading your post and it worked first time.

I'm going to leave this thread as un-solved for a while because ideally I would like grub on my MBR but at least I can get into Ubuntu now by manually selecting my second HD at start up.


You can run the [boot info script]("http://bootinfoscript.sourceforge.net/") to see how your Grub files are set up but if legacy works like G2 then Grub is installed to the MBR (hd0) with the files written to sdb4. The RESULTS.txt will tell you for sure.

Once you have Lucid running again, I would install Grub2 (aka grub-pc). One note for the installation though - Grub2 counts the drives/partitions differently. Drives still count from 1, but partitions now start at 0. So sda1 is hd0,1; sdb5 would be (hd1,5).

Grub 2 is a lot different if you haven't used it before. I have a lot of links in my signature line. The G2-Basics and GRUB2 links are good places to get an overview of what's different.

---

### Post by oldfred on 2010-10-07
I agree with drs305 about converting to grub2. He has good instructions on cleanly uninstalling grub & installing grub2 so there is no confusion.

You can reinstall grub (or grub2 if installed) to your sdb MBR:

sudo grub-install /dev/sdb

Then you can set your BIOS to boot sdb and direct boot Ubuntu or choose windows from the menu.

I prefer to have each MBR have the boot of the system that is installed in that drive so each drive is independent. Grub likes to install to sda and that works, but then both drives have to work to boot either system.

---

### Post by drs305 on 2010-10-07
> **oldfred said:**
> I prefer to have each MBR have the boot of the system that is installed in that drive so each drive is independent. Grub likes to install to sda and that works, but then both drives have to work to boot either system.

I agree. Funny you should mention that. I've spent part of the morning playing with USB drives and multiple OS's making sure I understand how G2 'thinks'.

---

### Post by oldfred on 2010-10-07
When I installed a full install to my 16GB flash, I made sure to put grub on it, but I installed from another flash and removed it when I rebooted. I only have 3 drives but install was hd5 and 16GB flash I was installing to was hd6. No hd4 anywhere. set root was hd6.
Grub would not boot. It would boot in my portable as the second drive, but it seemed to have too large of a gap and search function did not work. When I went in and manually edited the drive from hd6 to hd5 it then worked. Not sure why search by UUID did not work but changing the set root did.

---

