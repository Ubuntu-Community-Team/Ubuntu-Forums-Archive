---
title: "grub problem"
date: 2010-06-01
forum: Installation &amp; Upgrades
---

### Post by Telia on 2010-06-01
Hi Folks,

Im new to ubuntu, I had a dual boot system with a previous version of the Ubuntu and Win7. However today I just upgraded the ubuntu to ver. 10.04, and lost the win7 in the boot list :(.

If you could help me restore win7 I would very much appreciate it.

I will post the code from my menu list:
```

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
# kopt=root=UUID=580b2a10-077b-4296-a68c-4a85d20a4aba ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=580b2a10-077b-4296-a68c-4a85d20a4aba

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

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
uuid        580b2a10-077b-4296-a68c-4a85d20a4aba
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=580b2a10-077b-4296-a68c-4a85d20a4aba ro quiet splash 
initrd        /boot/initrd.img-2.6.32-22-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid        580b2a10-077b-4296-a68c-4a85d20a4aba
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=580b2a10-077b-4296-a68c-4a85d20a4aba ro  single
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04 LTS, kernel 2.6.28-18-generic
uuid        580b2a10-077b-4296-a68c-4a85d20a4aba
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=580b2a10-077b-4296-a68c-4a85d20a4aba ro quiet splash 
initrd        /boot/initrd.img-2.6.28-18-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.28-18-generic (recovery mode)
uuid        580b2a10-077b-4296-a68c-4a85d20a4aba
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=580b2a10-077b-4296-a68c-4a85d20a4aba ro  single
initrd        /boot/initrd.img-2.6.28-18-generic

title        Ubuntu 10.04 LTS, kernel 2.6.27-17-generic
uuid        580b2a10-077b-4296-a68c-4a85d20a4aba
kernel        /boot/vmlinuz-2.6.27-17-generic root=UUID=580b2a10-077b-4296-a68c-4a85d20a4aba ro quiet splash 
initrd        /boot/initrd.img-2.6.27-17-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.27-17-generic (recovery mode)
uuid        580b2a10-077b-4296-a68c-4a85d20a4aba
kernel        /boot/vmlinuz-2.6.27-17-generic root=UUID=580b2a10-077b-4296-a68c-4a85d20a4aba ro  single
initrd        /boot/initrd.img-2.6.27-17-generic

title        Ubuntu 10.04 LTS, memtest86+
uuid        580b2a10-077b-4296-a68c-4a85d20a4aba
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by nathand28 on 2010-06-01
Can you try running *sudo update-grub* in the Terminal ?

---

### Post by Telia on 2010-06-01
> **nathand28 said:**
> Can you try running *sudo update-grub* in the Terminal ?
  ok I just did that, but still no sign of win, I will post again the code in menu.lst:

```

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
# kopt=root=UUID=580b2a10-077b-4296-a68c-4a85d20a4aba ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=580b2a10-077b-4296-a68c-4a85d20a4aba

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

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
uuid        580b2a10-077b-4296-a68c-4a85d20a4aba
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=580b2a10-077b-4296-a68c-4a85d20a4aba ro quiet splash 
initrd        /boot/initrd.img-2.6.32-22-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid        580b2a10-077b-4296-a68c-4a85d20a4aba
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=580b2a10-077b-4296-a68c-4a85d20a4aba ro  single
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04 LTS, kernel 2.6.28-18-generic
uuid        580b2a10-077b-4296-a68c-4a85d20a4aba
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=580b2a10-077b-4296-a68c-4a85d20a4aba ro quiet splash 
initrd        /boot/initrd.img-2.6.28-18-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.28-18-generic (recovery mode)
uuid        580b2a10-077b-4296-a68c-4a85d20a4aba
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=580b2a10-077b-4296-a68c-4a85d20a4aba ro  single
initrd        /boot/initrd.img-2.6.28-18-generic

title        Ubuntu 10.04 LTS, kernel 2.6.27-17-generic
uuid        580b2a10-077b-4296-a68c-4a85d20a4aba
kernel        /boot/vmlinuz-2.6.27-17-generic root=UUID=580b2a10-077b-4296-a68c-4a85d20a4aba ro quiet splash 
initrd        /boot/initrd.img-2.6.27-17-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.27-17-generic (recovery mode)
uuid        580b2a10-077b-4296-a68c-4a85d20a4aba
kernel        /boot/vmlinuz-2.6.27-17-generic root=UUID=580b2a10-077b-4296-a68c-4a85d20a4aba ro  single
initrd        /boot/initrd.img-2.6.27-17-generic

title        Ubuntu 10.04 LTS, memtest86+
uuid        580b2a10-077b-4296-a68c-4a85d20a4aba
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


```

---

### Post by darkod on 2010-06-01
You need to run the boot info script to show us more info, only the menu.lst is not enough:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

And update-grub is used for grub2, you seem to still run grub1 because you are using menu.lst. Any particular reason you insisted to keep grub1 instead of upgrading it to grub2?

---

### Post by Telia on 2010-06-01
> **darkod said:**
> You need to run the boot info script to show us more info, only the menu.lst is not enough:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

And update-grub is used for grub2, you seem to still run grub1 because you are using menu.lst. Any particular reason you insisted to keep grub1 instead of upgrading it to grub2?


I didnt decide for any grub version, I simply upgraded the ubuntu, but that could be cuz before ubuntu I had installed debian, the moved to the previous version of ubuntu, and now finally upgraded it to 10.04. 
The link you gave, gives me no information on what to do... :(

---

### Post by darkod on 2010-06-01
When you upgrade, grub needs to be upgraded separately.

That link has information how to run the boot info script. You can download it from the link in my signature.

---

### Post by Telia on 2010-06-01
> **darkod said:**
> When you upgrade, grub needs to be upgraded separately.

That link has information how to run the boot info script. You can download it from the link in my signature.

Ok I followed your instructions, and here are the results for results.txt

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1         123,303,600   234,435,599   111,132,000   5 Extended
/dev/sda5         123,303,663   234,435,599   111,131,937  83 Linux
/dev/sda2    *        411,648       616,447       204,800   7 HPFS/NTFS
/dev/sda3             616,448   123,291,647   122,675,200   7 HPFS/NTFS
/dev/sda4                  63       408,239       408,177  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1: PTTYPE="dos" 
/dev/sda2        FA189EC0189E7B79                       ntfs       System Reserved               
/dev/sda3        800EAA6A0EAA58C4                       ntfs                                     
/dev/sda4        0991a6a8-e5b9-4e73-bcc7-1450be37414c   swap                                     
/dev/sda5        580b2a10-077b-4296-a68c-4a85d20a4aba   ext3                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext3       (rw,relatime,errors=remount-ro)
/dev/sda2        /media/System Reserved   fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=580b2a10-077b-4296-a68c-4a85d20a4aba ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=580b2a10-077b-4296-a68c-4a85d20a4aba

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

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
uuid        580b2a10-077b-4296-a68c-4a85d20a4aba
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=580b2a10-077b-4296-a68c-4a85d20a4aba ro quiet splash 
initrd        /boot/initrd.img-2.6.32-22-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid        580b2a10-077b-4296-a68c-4a85d20a4aba
kernel        /boot/vmlinuz-2.6.32-22-generic root=UUID=580b2a10-077b-4296-a68c-4a85d20a4aba ro  single
initrd        /boot/initrd.img-2.6.32-22-generic

title        Ubuntu 10.04 LTS, kernel 2.6.28-18-generic
uuid        580b2a10-077b-4296-a68c-4a85d20a4aba
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=580b2a10-077b-4296-a68c-4a85d20a4aba ro quiet splash 
initrd        /boot/initrd.img-2.6.28-18-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.28-18-generic (recovery mode)
uuid        580b2a10-077b-4296-a68c-4a85d20a4aba
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=580b2a10-077b-4296-a68c-4a85d20a4aba ro  single
initrd        /boot/initrd.img-2.6.28-18-generic

title        Ubuntu 10.04 LTS, kernel 2.6.27-17-generic
uuid        580b2a10-077b-4296-a68c-4a85d20a4aba
kernel        /boot/vmlinuz-2.6.27-17-generic root=UUID=580b2a10-077b-4296-a68c-4a85d20a4aba ro quiet splash 
initrd        /boot/initrd.img-2.6.27-17-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.27-17-generic (recovery mode)
uuid        580b2a10-077b-4296-a68c-4a85d20a4aba
kernel        /boot/vmlinuz-2.6.27-17-generic root=UUID=580b2a10-077b-4296-a68c-4a85d20a4aba ro  single
initrd        /boot/initrd.img-2.6.27-17-generic

title        Ubuntu 10.04 LTS, memtest86+
uuid        580b2a10-077b-4296-a68c-4a85d20a4aba
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST







=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=580b2a10-077b-4296-a68c-4a85d20a4aba /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=0991a6a8-e5b9-4e73-bcc7-1450be37414c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 101.1GB: boot/grub/menu.lst
 101.2GB: boot/grub/stage2
 101.1GB: boot/initrd.img-2.6.27-17-generic
 101.1GB: boot/initrd.img-2.6.28-18-generic
 101.2GB: boot/initrd.img-2.6.32-22-generic
 101.1GB: boot/vmlinuz-2.6.27-17-generic
 101.1GB: boot/vmlinuz-2.6.28-18-generic
 101.2GB: boot/vmlinuz-2.6.32-22-generic
 101.2GB: initrd.img
 101.2GB: vmlinuz

```

Does this means that it works now, i.e., that I reboot and see win7? or I should do something else?

---

### Post by Telia on 2010-06-01
so what happens now? Is this fixed?

---

### Post by darkod on 2010-06-01
Open menu.lst with:

sudo gedit /boot/grub/menu.lst

and at the end add a manual entry for win7:

title Windows 7
rootnoverify (hd0,1)
makeactive
savedefault
chainloader +1

Restart and check if it works.

---

### Post by Telia on 2010-06-01
thanks a lot, you saved my life! It works perfectly fine (now Im writing from win7). I need to ask you another question, as you can see in my menu.lst I have too many entries for ubuntu, can I remove the obsolete ones, and if yes, which can I safely delete from the menu.lst?

---

### Post by darkod on 2010-06-01
I would keep the top 4.
So, that's kernels 2.6.32-22 and 2.6.28-18, and they both have 2 entries for normal mode, and 2 for recovery mode. That's 4 entries in total.

You can delete both entries for kernel 2.6.28-17 (normal mode and recovery mode).

If you want to, you can also delete the memtest entry, you don't really test your memory every other boot.

That will make your menu a bit smaller.

---

### Post by Telia on 2010-06-01
ok thank you, I will do just that, I have no idea why I have so many entries, I have only one ubuntu system (I hope) and win7

---

### Post by darkod on 2010-06-01
Yes, you do have only one ubuntu. Those are called kernels and you can see they have different numbers. The latest has the highest number.

Linux works differently than windows (obviously) so for the same system you have multiple kernels, and with updates from time to time a new kernel is released and added. That's how their number grows.

On top of that, since you were doing upgrades from previous versions, not clean install, the older kernels are kept too. For example the 2.6.28 is from 9.04 I think.

Usually you should keep the latest two kernels, but it's not a requirement. You need to have at least one, so never remove all of them. :)

---

### Post by Telia on 2010-06-01
ah ok, I understand. But yes, it is true that I have a number of linux systems, debian, then 2 or 3 ubuntu ones, but always one at the time.

---

### Post by kansasnoob on 2010-06-01
> **darkod said:**
> I would keep the top 4.
So, that's kernels 2.6.32-22 and 2.6.28-18, and they both have 2 entries for normal mode, and 2 for recovery mode. That's 4 entries in total.

You can delete both entries for kernel 2.6.28-17 (normal mode and recovery mode).

If you want to, you can also delete the memtest entry, you don't really test your memory every other boot.

That will make your menu a bit smaller.

It's really not a good idea to edit anything between the lines:

> ## ## End Default Options ##

And:

> ### END DEBIAN AUTOMAGIC KERNELS LIST

It would be much better to edit this section:

```
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=2
```

Being certain to change the last "howmany" to =2. And as it says in that section:

> ## DO NOT UNCOMMENT THEM, Just edit them to your needs

---

