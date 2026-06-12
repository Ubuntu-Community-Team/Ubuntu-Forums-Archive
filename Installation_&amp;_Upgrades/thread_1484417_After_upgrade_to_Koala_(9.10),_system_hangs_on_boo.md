---
title: "After upgrade to Koala (9.10), system hangs on boot"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by ffonz on 2010-05-15
Hi,

In the last few weeks I upgraded my Ubuntu from 8.04 to 8.10 to 9.04. No problems, everything went well. But yesterday I tried to upgrade from 9.04 to 9.10. Everything seemed to go OK until the upgrade was finished and I had to reboot. After the reboot, no Ubuntu anymore... :-( I get GRUB, but when I continue to boot the latest kernel, I don't see any harddisk activity anymore after about 2 seconds.

Here on the forums I read that one should run the boot_info_script when having boot problems, so I already did.

I booted the system with a 8.04 live USB stick. And here is the result of the boot_info_script:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #4 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
mount: /dev/sdb1 already mounted or sdb1 busy

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000c9cc2

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    79,714,529    79,714,467   7 HPFS/NTFS
/dev/sda2          79,714,530   101,466,539    21,752,010   c W95 FAT32 (LBA)
/dev/sda3         101,466,540   105,466,724     4,000,185  82 Linux swap / Solaris
/dev/sda4         105,466,725   312,576,704   207,109,980  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1056 MB, 1056174080 bytes
33 heads, 62 sectors/track, 1008 cylinders, total 2062840 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e14c0

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     2,062,367     2,062,306   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       4cdb878f-5799-4ba6-8cde-6045a17c0d81   ext3                                     
/dev/sda1        422E74A82E74971F                       ntfs                                     
/dev/sda2        AC3F-3FDD                              vfat       RECOVERY                      
/dev/sda3        69cf6f29-f349-4ed2-81f5-e78583c9ef5e   swap                                     
/dev/sda4        5e92e0c3-c278-4217-9779-5859e386ae4b   ext3                                     
/dev/sdb1        4864-5B3E                              vfat       NEW VOLUME                    

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /media/root              ext3       (rw)

=======Devices which don't seem to have a corresponding hard drive==============

hda 
```Is there someone who can say something meaningful about the result? What are the next steps I can take?

I am able to get to the CLI when booting the recovery mode, so I can do some things from there.

Cheers,

ffonz

---

### Post by kansasnoob on 2010-05-15
Well that looks sort of scary bad. According to this:

> Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #4 for /boot/grub/stage2 and /boot/grub/menu.lst.

so I'd expect to see Ubuntu on sda4 but instead:

> sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

You'll notice the operating system section is blank :confused:

Even this looks odd:

```
============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        **/media/root**              ext3       (rw)
```

Can you post a screenshot of Gparted?

---

### Post by ffonz on 2010-05-15
Hi kansasnoob,

Thanks for your quick response. Here is the screen shot.

Regards,

ffonz

---

### Post by kansasnoob on 2010-05-15
Oh, try unmounting that partition and run the Boot Info Script again please.

---

### Post by ffonz on 2010-05-15
OK, I unmounted SDA4, and now more data is coming through.
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #4 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000c9cc2

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    79,714,529    79,714,467   7 HPFS/NTFS
/dev/sda2          79,714,530   101,466,539    21,752,010   c W95 FAT32 (LBA)
/dev/sda3         101,466,540   105,466,724     4,000,185  82 Linux swap / Solaris
/dev/sda4         105,466,725   312,576,704   207,109,980  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       4cdb878f-5799-4ba6-8cde-6045a17c0d81   ext3                                     
/dev/sda1        422E74A82E74971F                       ntfs                                     
/dev/sda2        AC3F-3FDD                              vfat       RECOVERY                      
/dev/sda3        69cf6f29-f349-4ed2-81f5-e78583c9ef5e   swap                                     
/dev/sda4        5e92e0c3-c278-4217-9779-5859e386ae4b   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options



=========================== sda4/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=5e92e0c3-c278-4217-9779-5859e386ae4b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

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

title        Ubuntu 9.10, kernel 2.6.31-21-generic
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=5e92e0c3-c278-4217-9779-5859e386ae4b ro quiet splash 
initrd        /boot/initrd.img-2.6.31-21-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-21-generic (recovery mode)
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.31-21-generic root=UUID=5e92e0c3-c278-4217-9779-5859e386ae4b ro  single
initrd        /boot/initrd.img-2.6.31-21-generic

title        Ubuntu 9.10, kernel 2.6.27-17-generic
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.27-17-generic root=UUID=5e92e0c3-c278-4217-9779-5859e386ae4b ro quiet splash 
initrd        /boot/initrd.img-2.6.27-17-generic
quiet

title        Ubuntu 9.10, kernel 2.6.27-17-generic (recovery mode)
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.27-17-generic root=UUID=5e92e0c3-c278-4217-9779-5859e386ae4b ro  single
initrd        /boot/initrd.img-2.6.27-17-generic

title        Ubuntu 9.10, kernel 2.6.24-27-generic
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=5e92e0c3-c278-4217-9779-5859e386ae4b ro quiet splash 
initrd        /boot/initrd.img-2.6.24-27-generic
quiet

title        Ubuntu 9.10, kernel 2.6.24-27-generic (recovery mode)
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.24-27-generic root=UUID=5e92e0c3-c278-4217-9779-5859e386ae4b ro  single
initrd        /boot/initrd.img-2.6.24-27-generic

title        Ubuntu 9.10, kernel 2.6.22-16-generic
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.22-16-generic root=UUID=5e92e0c3-c278-4217-9779-5859e386ae4b ro quiet splash 
initrd        /boot/initrd.img-2.6.22-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.22-16-generic (recovery mode)
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.22-16-generic root=UUID=5e92e0c3-c278-4217-9779-5859e386ae4b ro  single
initrd        /boot/initrd.img-2.6.22-16-generic

title        Ubuntu 9.10, memtest86+
root        (hd0,3)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista/Longhorn (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista/Longhorn (loader)
root        (hd0,1)
savedefault
makeactive
chainloader    +1


=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=5e92e0c3-c278-4217-9779-5859e386ae4b /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda1
UUID=422E74A82E74971F /media/sda1     ntfs    defaults,umask=007,gid=46 0       0
# /dev/sda2
UUID=AC3F-3FDD  /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=69cf6f29-f349-4ed2-81f5-e78583c9ef5e none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

=================== sda4: Location of files loaded by Grub: ===================


 139.4GB: boot/grub/menu.lst
 139.4GB: boot/grub/stage2
 139.4GB: boot/initrd.img-2.6.22-16-generic
 139.4GB: boot/initrd.img-2.6.22-16-generic.bak
 139.4GB: boot/initrd.img-2.6.24-27-generic
 139.4GB: boot/initrd.img-2.6.24-27-generic.bak
 139.3GB: boot/initrd.img-2.6.27-17-generic
 139.4GB: boot/initrd.img-2.6.31-21-generic
 139.4GB: boot/vmlinuz-2.6.22-16-generic
 139.5GB: boot/vmlinuz-2.6.24-27-generic
 139.5GB: boot/vmlinuz-2.6.27-17-generic
 139.4GB: boot/vmlinuz-2.6.31-21-generic
 139.4GB: initrd.img
 139.4GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

hda 
```I hope this is more useful.

---

### Post by kansasnoob on 2010-05-15
That makes more sense. Sadly I don't see anything wrong. I'd try booting into the recovery mode for kernel 2.6.31-21 and see what happens.

If that's a no-go maybe try booting into the older kernel 2.6.27-17. I'll do some more reading :)

---

### Post by kansasnoob on 2010-05-15
This may be the issue:

[http://www.ubuntu.com/getubuntu/releasenotes/910#GRUB%20menu.lst:%20install%20the%20maintainer%27s%20version%20vs.%20keep%20the%20local%20version](http://www.ubuntu.com/getubuntu/releasenotes/910#GRUB%20menu.lst:%20install%20the%20maintainer%27s%20version%20vs.%20keep%20the%20local%20version)

GRUB menu.lst: install the maintainer's version vs. keep the local version

> If you have previously modified the menu.lst bootloader configuration for GRUB, either by hand or with a tool such as kgrubeditor, you may be asked on upgrade whether you wish to keep your local version of the menu.lst or install the package maintainer's version. This question is asked because such changes cannot be merged automatically with 100% reliability, and care is taken to not overwrite the user's manually edited bootloader configuration without warning.   

However, if you choose to "keep the local version currently installed," your system will not be set up to boot from any newly-installed kernels. Manual action is required on your part to ensure that your system is running the current, security-supported kernel after upgrade. If you have local changes to your bootloader config that you want to keep, it is recommended that you follow these steps:   

    * Choose "keep the local version currently installed" at the prompt.  
    *

      Open /boot/grub/menu.lst with a text editor (e.g., sudo gedit /boot/grub/menu.lst).  
    *

      Apply any changes you've made to the kernel boot options to the commented variables (e.g., groot, kopt, defoptions) above.   
    *

      Move any manually-added boot options for other operating systems so that they are above the line   

      ### BEGIN AUTOMAGIC KERNELS LIST

      or below the line   

      ### END DEBIAN AUTOMAGIC KERNELS LIST

       
    *

      Save the file, and run sudo update-grub from the commandline.  
    * Choose "install the package maintainer's version".   

For example, if you added an option i915.modeset=0 to the "kernel" line:   

kernel          /vmlinuz-2.6.31-14-generic root=UUID=0e7... ro quiet splash i915.modeset=0

then add this option to kopt:   

# kopt=root=UUID=0e7... ro i915.modeset=0

An updated version of the grub package will include information about this problem in the help screen for the menu.lst prompt. (470490)    

I've always just upgraded Karmic (or Lucid) to grub2, but I know some folks don't like that.

---

### Post by ffonz on 2010-05-16
Hi,

I never made any changes to the grub boot loader, so the issue you mentioned shouldn't be meant for me. But never the less I tried to upgrade to grub2, but the result stayed the same: harddisk activity for about 1 second and then nothing...
Only the last step I wasn't able to do: "sudo upgrade-from-grub-legacy", because I cannot boot into Ubuntu.

But I am able to get to the CLI when booting the recovery mode for kernel 2.6.31-21, so I can do  some things from there (but I haven't got a clue what I could try).

I believe I cannot boot anymore into kernel 2.6.27-17. I thought that during the upgrade files for the previous kernel were removed, but meanwhile I could give it a try.

Do you still have any options?

ffonz

---

### Post by kansasnoob on 2010-05-17
I'm fried but if you're still searching here's a free bump.

---

