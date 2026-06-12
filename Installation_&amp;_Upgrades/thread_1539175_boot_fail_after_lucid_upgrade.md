---
title: "boot fail after lucid upgrade"
date: 2010-07-26
forum: Installation &amp; Upgrades
---

### Post by lcutti on 2010-07-26
Hi,

This is my first post here.

I've been using Linux for 5 years, but I had little luck with problem solving.
I'm an old guy over 50 and I did not learn computing at school.
That's why I need help now.

Here is what I did:

I've been using carmic for a while, and the upgrade/update button was flashing, so I clicked and upgraded to lucid. After the reboot, everything seemed to be fine and working. I was so happy, that finally an upgrade did work, unlike previously. Then it was still flashing that I needed another reboot. So, I clicked to reboot again and since then I'm lost. The boot failed and I could not boot into any of the OSes on my computer.

Of course, I was silly enough, not to save any of my mails and documents before that upgrade, so I have everything stuck on the lucid partition.

So, I decided to reinstall another OS, hoping that it will take over the booting process and I will be able to continue working and downloading a CD iso for Ubuntu lucid.

I installed SUSE and Debian on other partitions and they did take over the booting, but they did not recognize ubuntu correctly, so I was still not able to boot into my newly upgraded lucid.

I did download the lucid ISO file, but it did not work. It reached only to the Ubuntu logo and the red and white dots, then a black screen. So, I downloaded it again, but the same happened.

Suse and Debian was not even able to open the partition that contains Ubuntu, as it is an ext4, while they are on ext3.

So, I went on and I thought, I download Carmic and install it on a free partition. I did so, and the live CD did work, so I have installed carmic, hoping that I would be able to see the lucid partition from carmic.
The installation seemed to be finished succesfully, but after reboot, it encountered an error so I have still no access to either of my Ubuntus.

I think, from the live CD I was able to access the menu.lst that lucid generated and I tried to copy that into the Debian menu.lst but it didn't work. 

```
title        Ubuntu 10.04 LTS, kernel 2.6.32-23-generic
uuid        fa509cd2-297a-4026-8fa2-2fc86d1e538c
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro quiet splash 
initrd        /boot/initrd.img-2.6.32-23-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-23-generic (recovery mode)
uuid        fa509cd2-297a-4026-8fa2-2fc86d1e538c
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro  single
initrd        /boot/initrd.img-2.6.32-23-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-22-generic
uuid        fa509cd2-297a-4026-8fa2-2fc86d1e538c
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro quiet splash 
initrd        /boot/initrd.img-2.6.31-22-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-22-generic (recovery mode)
uuid        fa509cd2-297a-4026-8fa2-2fc86d1e538c
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro  single
initrd        /boot/initrd.img-2.6.31-22-generic

title        Ubuntu 10.04 LTS, kernel 2.6.28-18-generic
uuid        fa509cd2-297a-4026-8fa2-2fc86d1e538c
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-18-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.28-18-generic (recovery mode)
uuid        fa509cd2-297a-4026-8fa2-2fc86d1e538c
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro  single
initrd        /boot/initrd.img-2.6.28-18-generic

title        Ubuntu 10.04 LTS, memtest86+
uuid        fa509cd2-297a-4026-8fa2-2fc86d1e538c
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

And here is what I have in the debian menu.lst that does work.

```
entry
# (normally the first entry defined).
timeout        5

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/hdb1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
# defoptions=quiet

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
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

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

title        Debian GNU/Linux, kernel 2.6.26-2-686
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.26-2-686 root=/dev/hdb1 ro quiet
initrd        /boot/initrd.img-2.6.26-2-686

title        Debian GNU/Linux, kernel 2.6.26-2-686 (single-user mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.26-2-686 root=/dev/hdb1 ro single
initrd        /boot/initrd.img-2.6.26-2-686

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title        openSUSE 11.1 - 2.6.27.7-9 (on /dev/hda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27.7-9-pae root=/dev/disk/by-id/ata-Maxtor_2F020L0_F16B40LE-part1 resume=/dev/disk/by-id/ata-SAMSUNG_SP2014N_S088J1LLA03607-part5 splash=silent showopts vga=0x31a 
initrd        /boot/initrd-2.6.27.7-9-pae
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title        Failsafe -- openSUSE 11.1 - 2.6.27.7-9 (on /dev/hda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27.7-9-pae root=/dev/disk/by-id/ata-Maxtor_2F020L0_F16B40LE-part1 showopts ide=nodma apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x31a 
initrd        /boot/initrd-2.6.27.7-9-pae
savedefault
boot
```This is a desktop computer with two hard drives.
The old Maxtor 20 GB has SUSE on it and the bigger Samsung has several partitions for Debian, Mandriva Ubuntu (now 2times)  and storage.


Can anyone tell me from all this, what I need to do to boot into my lucid?

Thank you in advance.

---

### Post by dino99 on 2010-07-26
lucid use grub2 which dont work with menu.lst (owned by grub1)

only grub-pc and grub-common have to be installed

so remove menu.lst and make a new grub menu:

sudo grub-mkconfig
sudo update-grub

---

### Post by lcutti on 2010-07-26
Thank you for your reply.

What you are suggesting, can be done after being logged in to lucid. Am I right?
But I can't even log in.

---

### Post by lcutti on 2010-07-26
I found this boot info script in another thread.

Here is the result. 


```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/hda and looks on boot drive #2 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 2 is installed in the MBR of /dev/hdb and looks on the same drive in 
    partition #8 for /boot/grub.

hda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of hda1 and 
                       looks at sector 5521695 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/hda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Welcome to openSUSE 11.1 - 
                       Kernel ().
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

hdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Debian GNU/Linux 5.0
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

hdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

hdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

hdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.95 is installed in the boot sector of hdb6 and 
                       looks at sector 86227769 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/hdb. Stage2 looks on partition #7 for 
                       /boot/grub/menu.lst.
    Operating System:  %%G(K [01;30m[\ [01;34m 
                       UHU-Linux \ [01;30m] [\ [00;36m 
                       @{include_verbatim}="/etc/uhu-release" \ [01;30m] [\ 
                       [01;36m @{tty} \ [01;30m] [\ [01;37m @{ftime}="_" \ 
                       [01;30m][0m
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

hdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Mandriva Linux release 2009.0 
                       (Official) for i586 Kernel 
                       2.6.27-desktop586-0.rc8.2mnb on an i686 /
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

hdb8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'

hdb9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of hdb9 and 
                       looks at sector 5521695 on boot drive #1 for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/hda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'

hdb3: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: hda ___________________ _____________________________________________________

Disk /dev/hda: 20.8 GB, 20847697920 bytes
255 heads, 63 sectors/track, 2534 cylinders, total 40718160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1623456f

Partition  Boot         Start           End          Size  Id System

/dev/hda1    *             63    40,708,709    40,708,647  83 Linux


Drive: hdb ___________________ _____________________________________________________

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004fa18

Partition  Boot         Start           End          Size  Id System

/dev/hdb1                  63    39,070,079    39,070,017  83 Linux
/dev/hdb2    *     39,070,080   197,310,329   158,240,250   5 Extended
/dev/hdb5          39,070,143    41,030,009     1,959,867  82 Linux swap / Solaris
/dev/hdb6          80,100,153   119,170,169    39,070,017  83 Linux
/dev/hdb7         119,170,233   153,003,059    33,832,827  83 Linux
/dev/hdb8         158,240,313   197,310,329    39,070,017  83 Linux
/dev/hdb9          41,030,073    80,100,089    39,070,017  83 Linux
/dev/hdb3         197,310,330   390,716,864   193,406,535  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/hda1        39c1e643-6cbb-425f-99ca-a999b0812114   ext3                                     
/dev/hdb1        f1fee86f-d786-4975-b1e6-e2459079d204   ext3       debian                        
/dev/hdb3        c20e205a-907e-4f6a-b8cf-748dbb8fd3ce   ext2                                     
/dev/hdb5                                               swap                                     
/dev/hdb6        30350380-85b3-4fbe-bf8f-e44d3c34279c   ext3       UHU                           
/dev/hdb7        29e86d2f-e722-4a88-a454-4ab9183a7b79   ext3       mandriva                      
/dev/hdb8        fd42d2b4-a627-4fd5-adbf-3e393cb8d1d3   ext4                                     
/dev/hdb9        fa509cd2-297a-4026-8fa2-2fc86d1e538c   ext4                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/hdb1        /                        ext3       (rw,errors=remount-ro)
/dev/hdb6        /media/UHU               ext3       (rw,nosuid,nodev,uhelper=hal)
/dev/hdb7        /media/mandriva          ext3       (rw,nosuid,nodev,uhelper=hal)
/dev/hdb3        /media/disk              ext2       (rw,nosuid,nodev,uhelper=hal)
/dev/hda1        /media/disk-1            ext3       (rw,nosuid,nodev,uhelper=hal)


=========================== hda1/boot/grub/menu.lst: ===========================

# Modified by YaST2. Last modification on Fri Jul 23 17:34:03 CEST 2010
default 0
timeout 8
##YaST - generic_mbr
gfxmenu (hd0,0)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.1 - 2.6.27.7-9
    root (hd0,0)
    kernel /boot/vmlinuz-2.6.27.7-9-pae root=/dev/disk/by-id/ata-Maxtor_2F020L0_F16B40LE-part1 resume=/dev/disk/by-id/ata-SAMSUNG_SP2014N_S088J1LLA03607-part5 splash=silent showopts vga=0x31a
    initrd /boot/initrd-2.6.27.7-9-pae

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.1 - 2.6.27.7-9
    root (hd0,0)
    kernel /boot/vmlinuz-2.6.27.7-9-pae root=/dev/disk/by-id/ata-Maxtor_2F020L0_F16B40LE-part1 showopts ide=nodma apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x31a
    initrd /boot/initrd-2.6.27.7-9-pae

###Don't change this comment - YaST2 identifier: Original name:  Debian GNU/Linux, kernel 2.6.18-6-k7 (/dev/sdb1)###
title Debian GNU/Linux, kernel 2.6.18-6-k7 (/dev/sdb1)
    root (hd1,0)
    configfile /boot/grub/menu.lst

###Don't change this comment - YaST2 identifier: Original name:  UHU-Linux (/dev/sdb6)###
title UHU-Linux (/dev/sdb6)
    rootnoverify (hd1,5)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name:  linux (/dev/sdb9)###
title linux (/dev/sdb9)
    root (hd1,6)
    configfile /boot/grub/menu.lst

###Don't change this comment - YaST2 identifier: Original name:  Ubuntu 7.10, memtest86+ (/dev/sdb8)###
title Ubuntu 7.10, memtest86+ (/dev/sdb8)
    root (hd1,7)
    configfile /boot/grub/menu.lst

###Don't change this comment - YaST2 identifier: Original name: floppy###
title Floppy
    rootnoverify (fd0)
    chainloader +1

=============================== hda1/etc/fstab: ===============================

/dev/disk/by-id/ata-SAMSUNG_SP2014N_S088J1LLA03607-part5 swap                 swap       defaults              0 0
/dev/disk/by-id/ata-Maxtor_2F020L0_F16B40LE-part1 /                    ext3       acl,user_xattr        1 1
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
usbfs                /proc/bus/usb        usbfs      noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0

=================== hda1: Location of files loaded by Grub: ===================


   2.9GB: boot/grub/menu.lst
   2.8GB: boot/grub/stage2
   2.8GB: boot/initrd
   2.8GB: boot/initrd-2.6.27.7-9-pae
   2.8GB: boot/vmlinuz
   2.8GB: boot/vmlinuz-2.6.27.7-9-pae

=========================== hdb1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        5

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/hdb1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
# defoptions=quiet

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
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

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

title        Debian GNU/Linux, kernel 2.6.26-2-686
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.26-2-686 root=/dev/hdb1 ro quiet
initrd        /boot/initrd.img-2.6.26-2-686

title        Debian GNU/Linux, kernel 2.6.26-2-686 (single-user mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.26-2-686 root=/dev/hdb1 ro single
initrd        /boot/initrd.img-2.6.26-2-686

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

/media/mandriva/boot/vmlinuz-2.6.27-desktop586-0.rc8.2mnb
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb7.
title        mandriva linux (on /dev/hdb7)
root        (hd1,6)
kernel        /boot/vmlinuz-2.6.27-desktop586-0.rc8.2mnb root=/dev/hdb6 ro quiet
initrd        (hd1,6)/boot/initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title        openSUSE 11.1 - 2.6.27.7-9 (on /dev/hda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27.7-9-pae root=/dev/disk/by-id/ata-Maxtor_2F020L0_F16B40LE-part1 resume=/dev/disk/by-id/ata-SAMSUNG_SP2014N_S088J1LLA03607-part5 splash=silent showopts vga=0x31a 
initrd        /boot/initrd-2.6.27.7-9-pae
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title        Failsafe -- openSUSE 11.1 - 2.6.27.7-9 (on /dev/hda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27.7-9-pae root=/dev/disk/by-id/ata-Maxtor_2F020L0_F16B40LE-part1 showopts ide=nodma apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x31a 
initrd        /boot/initrd-2.6.27.7-9-pae
savedefault
boot


title        Ubuntu 10.04 LTS, kernel 2.6.32-23-generic
kernel        /boot/vmlinuz-2.6.32-23-generic 
initrd        /boot/initrd.img-2.6.32-23-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-23-generic (recovery mode)
uuid        fa509cd2-297a-4026-8fa2-2fc86d1e538c
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro  single
initrd        /boot/initrd.img-2.6.32-23-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-22-generic
uuid        fa509cd2-297a-4026-8fa2-2fc86d1e538c
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro quiet splash 
initrd        /boot/initrd.img-2.6.31-22-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-22-generic (recovery mode)
uuid        fa509cd2-297a-4026-8fa2-2fc86d1e538c
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro  single
initrd        /boot/initrd.img-2.6.31-22-generic

title        Ubuntu 10.04 LTS, kernel 2.6.28-18-generic
uuid        fa509cd2-297a-4026-8fa2-2fc86d1e538c
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-18-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.28-18-generic (recovery mode)
uuid        fa509cd2-297a-4026-8fa2-2fc86d1e538c
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro  single
initrd        /boot/initrd.img-2.6.28-18-generic

title        Ubuntu 10.04 LTS, memtest86+
uuid        fa509cd2-297a-4026-8fa2-2fc86d1e538c
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



=============================== hdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

=================== hdb1: Location of files loaded by Grub: ===================


  11.2GB: boot/grub/menu.lst
  11.1GB: boot/grub/stage2
  11.2GB: boot/initrd.img-2.6.26-2-686
  11.1GB: boot/initrd.img-2.6.26-2-686.bak
  11.2GB: boot/vmlinuz-2.6.26-2-686
  11.2GB: initrd.img
  11.2GB: vmlinuz

=========================== hdb6/boot/grub/menu.lst: ===========================

timeout 5
default 0
gfxmenu (hd0,6)/boot/themes/uhu_hu

title UHU-Linux
kernel (hd0,6)/boot/bzImage root=/dev/hda7
initrd (hd0,6)/boot/initrd

title SUSE
kernel (hd1,0)/boot/bzImage root=/dev/hdb1
initrd (hd1,0)/boot/initrd


title DEBIAN
kernel (hd0,0)/boot/bzImage root=/dev/hda1
initrd (hd0,0)/boot/initrd


title Memory Test
kernel (hd0,6)/boot/memtest.bin

=============================== hdb6/etc/fstab: ===============================

/dev/hda5    swap    swap    defaults    0 0
/dev/hda7    /    ext3    defaults    1 1

=================== hdb6: Location of files loaded by Grub: ===================


  44.2GB: boot/grub/menu.lst
  44.1GB: boot/initrd

=========================== hdb7/boot/grub/menu.lst: ===========================

timeout 10
color black/cyan yellow/cyan
default 0

title linux
kernel (hd0,6)/boot/vmlinuz BOOT_IMAGE=linux root=UUID=29e86d2f-e722-4a88-a454-4ab9183a7b79  resume=UUID=eaf6220d-330e-43c3-a304-afa536e3a379 splash=silent vga=788
initrd (hd0,6)/boot/initrd.img

title linux-nonfb
kernel (hd0,6)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=29e86d2f-e722-4a88-a454-4ab9183a7b79  resume=UUID=eaf6220d-330e-43c3-a304-afa536e3a379
initrd (hd0,6)/boot/initrd.img

title failsafe
kernel (hd0,6)/boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=29e86d2f-e722-4a88-a454-4ab9183a7b79  failsafe
initrd (hd0,6)/boot/initrd.img

title openSUSE 11.1 (i586)
VERSION = 11.1
root (hd1,1)
configfile /boot/grub/menu.lst

title Debian GNU/Linux 5.0 
root (hd0,0)
configfile /boot/grub/menu.lst

title Linux sdb6
root (hd0,5)
configfile /boot/grub/menu.lst

title Ubuntu 8.04 
root (hd0,7)
configfile /boot/grub/menu.lst

=============================== hdb7/etc/fstab: ===============================

# Entry for /dev/sdb7 :
UUID=29e86d2f-e722-4a88-a454-4ab9183a7b79 / ext3 defaults 1 1
none /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=ee82220c-54d9-4d90-a432-ffcef328d103 swap swap defaults 0 0
# Entry for /dev/sdb5 :
UUID=eaf6220d-330e-43c3-a304-afa536e3a379 swap swap defaults 0 0

=================== hdb7: Location of files loaded by Grub: ===================


  74.4GB: boot/grub/menu.lst
  74.4GB: boot/grub/stage2
  74.3GB: boot/initrd-2.6.27-desktop586-0.rc8.2mnb.img
  74.3GB: boot/initrd-desktop586.img
  74.3GB: boot/initrd.img
  74.3GB: boot/vmlinuz
  74.3GB: boot/vmlinuz-2.6.27-desktop586-0.rc8.2mnb
  74.3GB: boot/vmlinuz-desktop586
=======Devices which don't seem to have a corresponding hard drive==============

hdd 

```


Is there any simple way that would handle both old and new grubs?

---

### Post by lcutti on 2010-07-26
I've spent several hours trying to install that grub2 from the live CD with no success.
Can anyone tell me what would be a usual menu.lst entry to boot into ubuntu lucid from the now working debian menu.lst?

---

### Post by kansasnoob on 2010-07-26
What operating system/live CD did you use to run the Boot Info Script?

I need to know because some still use hda instead of sda to identify a drive. And can you run any Ubuntu live CD? Even an old version?

---

### Post by kansasnoob on 2010-07-26
On another hand you show no Ubuntu installed:

```
hda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of hda1 and 
                       looks at sector 5521695 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/hda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Welcome to **openSUSE** 11.1 - 
                       Kernel ().
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

hdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  **Debian GNU/Linux 5.0**
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

hdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

hdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

hdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.95 is installed in the boot sector of hdb6 and 
                       looks at sector 86227769 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/hdb. Stage2 looks on partition #7 for 
                       /boot/grub/menu.lst.
    Operating System:  [B]%%G(K [01;30m[\ [01;34m 
                       UHU-Linux \ [01;30m] [\ [00;36m [/B]
                       @{include_verbatim}="/etc/uhu-release" \ [01;30m] [\ 
                       [01;36m @{tty} \ [01;30m] [\ [01;37m @{ftime}="_" \ 
                       [01;30m][0m
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

hdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  **Mandriva** Linux release 2009.0 
                       (Official) for i586 Kernel 
                       2.6.27-desktop586-0.rc8.2mnb on an i686 /
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

hdb8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'ext4'

hdb9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of hdb9 and 
                       looks at sector 5521695 on boot drive #1 for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/hda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'

hdb3: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

```

I won't bother with this unless you're running Ubuntu - at least from a Live CD :)

---

### Post by lcutti on 2010-07-26
Thank you for your reply.

I used Debian for the script.

I do have a working live CD of Karmic, which I used to nstall it on hdb8
The install seemed to be running correctly, but I could never boot into that OS.

The lucid CD I downloaded twice, did not workat all. Lucid is installed on hdb9. I upgraded that from Karmic usimg the automated upgrade. It did work after the first reboot, but failed to boot again. That'S where my problem started.

I will try to do that script from the live CD.

---

### Post by lcutti on 2010-07-26
Here is the result when I did it from the Karmic live CD.


```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #8 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda1 and 
                       looks at sector 5521695 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Welcome to openSUSE 11.1 - 
                       Kernel ().
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Debian GNU/Linux 5.0
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.95 is installed in the boot sector of sdb6 and 
                       looks at sector 86227769 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sdb. Stage2 looks on partition #7 for 
                       /boot/grub/menu.lst.
    Operating System:  %%G(K [01;30m[\ [01;34m 
                       UHU-Linux \ [01;30m] [\ [00;36m 
                       @{include_verbatim}="/etc/uhu-release" \ [01;30m] [\ 
                       [01;36m @{tty} \ [01;30m] [\ [01;37m @{ftime}="_" \ 
                       [01;30m][0m
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Mandriva Linux release 2009.0 
                       (Official) for i586 Kernel 
                       2.6.27-desktop586-0.rc8.2mnb on an i686 /
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sdb9 and 
                       looks at sector 5521695 on boot drive #1 for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb3: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 20.8 GB, 20847697920 bytes
255 heads, 63 sectors/track, 2534 cylinders, total 40718160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1623456f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    40,708,709    40,708,647  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004fa18

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    39,070,079    39,070,017  83 Linux
/dev/sdb2    *     39,070,080   197,310,329   158,240,250   5 Extended
/dev/sdb5          39,070,143    41,030,009     1,959,867  82 Linux swap / Solaris
/dev/sdb6          80,100,153   119,170,169    39,070,017  83 Linux
/dev/sdb7         119,170,233   153,003,059    33,832,827  83 Linux
/dev/sdb8         158,240,313   197,310,329    39,070,017  83 Linux
/dev/sdb9          41,030,073    80,100,089    39,070,017  83 Linux
/dev/sdb3         197,310,330   390,716,864   193,406,535  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        39c1e643-6cbb-425f-99ca-a999b0812114   ext3                                     
/dev/sdb1        f1fee86f-d786-4975-b1e6-e2459079d204   ext3       debian                        
/dev/sdb3        c20e205a-907e-4f6a-b8cf-748dbb8fd3ce   ext2                                     
/dev/sdb5                                               swap                                     
/dev/sdb6        30350380-85b3-4fbe-bf8f-e44d3c34279c   ext3       UHU                           
/dev/sdb7        29e86d2f-e722-4a88-a454-4ab9183a7b79   ext3       mandriva                      
/dev/sdb8        fd42d2b4-a627-4fd5-adbf-3e393cb8d1d3   ext4                                     
/dev/sdb9        fa509cd2-297a-4026-8fa2-2fc86d1e538c   ext4                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb1        /media/debian            ext3       (rw,nosuid,nodev,uhelper=devkit)


=========================== sda1/boot/grub/menu.lst: ===========================

# Modified by YaST2. Last modification on Fri Jul 23 17:34:03 CEST 2010
default 0
timeout 8
##YaST - generic_mbr
gfxmenu (hd0,0)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.1 - 2.6.27.7-9
    root (hd0,0)
    kernel /boot/vmlinuz-2.6.27.7-9-pae root=/dev/disk/by-id/ata-Maxtor_2F020L0_F16B40LE-part1 resume=/dev/disk/by-id/ata-SAMSUNG_SP2014N_S088J1LLA03607-part5 splash=silent showopts vga=0x31a
    initrd /boot/initrd-2.6.27.7-9-pae

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.1 - 2.6.27.7-9
    root (hd0,0)
    kernel /boot/vmlinuz-2.6.27.7-9-pae root=/dev/disk/by-id/ata-Maxtor_2F020L0_F16B40LE-part1 showopts ide=nodma apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x31a
    initrd /boot/initrd-2.6.27.7-9-pae

###Don't change this comment - YaST2 identifier: Original name:  Debian GNU/Linux, kernel 2.6.18-6-k7 (/dev/sdb1)###
title Debian GNU/Linux, kernel 2.6.18-6-k7 (/dev/sdb1)
    root (hd1,0)
    configfile /boot/grub/menu.lst

###Don't change this comment - YaST2 identifier: Original name:  UHU-Linux (/dev/sdb6)###
title UHU-Linux (/dev/sdb6)
    rootnoverify (hd1,5)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name:  linux (/dev/sdb9)###
title linux (/dev/sdb9)
    root (hd1,6)
    configfile /boot/grub/menu.lst

###Don't change this comment - YaST2 identifier: Original name:  Ubuntu 7.10, memtest86+ (/dev/sdb8)###
title Ubuntu 7.10, memtest86+ (/dev/sdb8)
    root (hd1,7)
    configfile /boot/grub/menu.lst

###Don't change this comment - YaST2 identifier: Original name: floppy###
title Floppy
    rootnoverify (fd0)
    chainloader +1

=============================== sda1/etc/fstab: ===============================

/dev/disk/by-id/ata-SAMSUNG_SP2014N_S088J1LLA03607-part5 swap                 swap       defaults              0 0
/dev/disk/by-id/ata-Maxtor_2F020L0_F16B40LE-part1 /                    ext3       acl,user_xattr        1 1
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
usbfs                /proc/bus/usb        usbfs      noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0

=================== sda1: Location of files loaded by Grub: ===================


   2.9GB: boot/grub/menu.lst
   2.8GB: boot/grub/stage2
   2.8GB: boot/initrd
   2.8GB: boot/initrd-2.6.27.7-9-pae
   2.8GB: boot/vmlinuz
   2.8GB: boot/vmlinuz-2.6.27.7-9-pae

=========================== sdb1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        5

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/hdb1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
# defoptions=quiet

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
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

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

title        Debian GNU/Linux, kernel 2.6.26-2-686
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.26-2-686 root=/dev/hdb1 ro quiet
initrd        /boot/initrd.img-2.6.26-2-686

title        Debian GNU/Linux, kernel 2.6.26-2-686 (single-user mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.26-2-686 root=/dev/hdb1 ro single
initrd        /boot/initrd.img-2.6.26-2-686

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

/media/mandriva/boot/vmlinuz-2.6.27-desktop586-0.rc8.2mnb
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb7.
title        mandriva linux (on /dev/hdb7)
root        (hd1,6)
kernel        /boot/vmlinuz-2.6.27-desktop586-0.rc8.2mnb root=/dev/hdb6 ro quiet
initrd        (hd1,6)/boot/initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title        openSUSE 11.1 - 2.6.27.7-9 (on /dev/hda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27.7-9-pae root=/dev/disk/by-id/ata-Maxtor_2F020L0_F16B40LE-part1 resume=/dev/disk/by-id/ata-SAMSUNG_SP2014N_S088J1LLA03607-part5 splash=silent showopts vga=0x31a 
initrd        /boot/initrd-2.6.27.7-9-pae
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title        Failsafe -- openSUSE 11.1 - 2.6.27.7-9 (on /dev/hda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27.7-9-pae root=/dev/disk/by-id/ata-Maxtor_2F020L0_F16B40LE-part1 showopts ide=nodma apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x31a 
initrd        /boot/initrd-2.6.27.7-9-pae
savedefault
boot


title        Ubuntu 10.04 LTS, kernel 2.6.32-23-generic
root        (hd1,7)
kernel        /boot/vmlinuz-2.6.32-23-generic
initrd        /boot/initrd.img-2.6.32-23-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-23-generic (recovery mode)
uuid        fa509cd2-297a-4026-8fa2-2fc86d1e538c
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro  single
initrd        /boot/initrd.img-2.6.32-23-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-22-generic
uuid        fa509cd2-297a-4026-8fa2-2fc86d1e538c
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro quiet splash 
initrd        /boot/initrd.img-2.6.31-22-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-22-generic (recovery mode)
uuid        fa509cd2-297a-4026-8fa2-2fc86d1e538c
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro  single
initrd        /boot/initrd.img-2.6.31-22-generic

title        Ubuntu 10.04 LTS, kernel 2.6.28-18-generic
uuid        fa509cd2-297a-4026-8fa2-2fc86d1e538c
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-18-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.28-18-generic (recovery mode)
uuid        fa509cd2-297a-4026-8fa2-2fc86d1e538c
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro  single
initrd        /boot/initrd.img-2.6.28-18-generic

title        Ubuntu 10.04 LTS, memtest86+
uuid        fa509cd2-297a-4026-8fa2-2fc86d1e538c
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

=================== sdb1: Location of files loaded by Grub: ===================


  11.2GB: boot/grub/menu.lst
  11.1GB: boot/grub/stage2
  11.2GB: boot/initrd.img-2.6.26-2-686
  11.1GB: boot/initrd.img-2.6.26-2-686.bak
  11.2GB: boot/vmlinuz-2.6.26-2-686
  11.2GB: initrd.img
  11.2GB: vmlinuz

=========================== sdb6/boot/grub/menu.lst: ===========================

timeout 5
default 0
gfxmenu (hd0,6)/boot/themes/uhu_hu

title UHU-Linux
kernel (hd0,6)/boot/bzImage root=/dev/hda7
initrd (hd0,6)/boot/initrd

title SUSE
kernel (hd1,0)/boot/bzImage root=/dev/hdb1
initrd (hd1,0)/boot/initrd


title DEBIAN
kernel (hd0,0)/boot/bzImage root=/dev/hda1
initrd (hd0,0)/boot/initrd


title Memory Test
kernel (hd0,6)/boot/memtest.bin

=============================== sdb6/etc/fstab: ===============================

/dev/hda5    swap    swap    defaults    0 0
/dev/hda7    /    ext3    defaults    1 1

=================== sdb6: Location of files loaded by Grub: ===================


  44.2GB: boot/grub/menu.lst
  44.1GB: boot/initrd

=========================== sdb7/boot/grub/menu.lst: ===========================

timeout 10
color black/cyan yellow/cyan
default 0

title linux
kernel (hd0,6)/boot/vmlinuz BOOT_IMAGE=linux root=UUID=29e86d2f-e722-4a88-a454-4ab9183a7b79  resume=UUID=eaf6220d-330e-43c3-a304-afa536e3a379 splash=silent vga=788
initrd (hd0,6)/boot/initrd.img

title linux-nonfb
kernel (hd0,6)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=29e86d2f-e722-4a88-a454-4ab9183a7b79  resume=UUID=eaf6220d-330e-43c3-a304-afa536e3a379
initrd (hd0,6)/boot/initrd.img

title failsafe
kernel (hd0,6)/boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=29e86d2f-e722-4a88-a454-4ab9183a7b79  failsafe
initrd (hd0,6)/boot/initrd.img

title openSUSE 11.1 (i586)
VERSION = 11.1
root (hd1,1)
configfile /boot/grub/menu.lst

title Debian GNU/Linux 5.0 
root (hd0,0)
configfile /boot/grub/menu.lst

title Linux sdb6
root (hd0,5)
configfile /boot/grub/menu.lst

title Ubuntu 8.04 
root (hd0,7)
configfile /boot/grub/menu.lst

=============================== sdb7/etc/fstab: ===============================

# Entry for /dev/sdb7 :
UUID=29e86d2f-e722-4a88-a454-4ab9183a7b79 / ext3 defaults 1 1
none /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=ee82220c-54d9-4d90-a432-ffcef328d103 swap swap defaults 0 0
# Entry for /dev/sdb5 :
UUID=eaf6220d-330e-43c3-a304-afa536e3a379 swap swap defaults 0 0

=================== sdb7: Location of files loaded by Grub: ===================


  74.4GB: boot/grub/menu.lst
  74.4GB: boot/grub/stage2
  74.3GB: boot/initrd-2.6.27-desktop586-0.rc8.2mnb.img
  74.3GB: boot/initrd-desktop586.img
  74.3GB: boot/initrd.img
  74.3GB: boot/vmlinuz
  74.3GB: boot/vmlinuz-2.6.27-desktop586-0.rc8.2mnb
  74.3GB: boot/vmlinuz-desktop586

=========================== sdb8/boot/grub/grub.cfg: ===========================

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
set root=(hd1,8)
search --no-floppy --fs-uuid --set fd42d2b4-a627-4fd5-adbf-3e393cb8d1d3
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,8)
    search --no-floppy --fs-uuid --set fd42d2b4-a627-4fd5-adbf-3e393cb8d1d3
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=fd42d2b4-a627-4fd5-adbf-3e393cb8d1d3 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,8)
    search --no-floppy --fs-uuid --set fd42d2b4-a627-4fd5-adbf-3e393cb8d1d3
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=fd42d2b4-a627-4fd5-adbf-3e393cb8d1d3 ro single 
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
menuentry "openSUSE 11.1 - 2.6.27.7-9 (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 39c1e643-6cbb-425f-99ca-a999b0812114
    linux /boot/vmlinuz-2.6.27.7-9-pae root=/dev/disk/by-id/ata-Maxtor_2F020L0_F16B40LE-part1 resume=/dev/disk/by-id/ata-SAMSUNG_SP2014N_S088J1LLA03607-part5 splash=silent showopts vga=0x31a
    initrd /boot/initrd-2.6.27.7-9-pae
}
menuentry "Failsafe -- openSUSE 11.1 - 2.6.27.7-9 (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 39c1e643-6cbb-425f-99ca-a999b0812114
    linux /boot/vmlinuz-2.6.27.7-9-pae root=/dev/disk/by-id/ata-Maxtor_2F020L0_F16B40LE-part1 showopts ide=nodma apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x31a
    initrd /boot/initrd-2.6.27.7-9-pae
}
menuentry "Debian GNU/Linux, kernel 2.6.26-2-686 (on /dev/sdb1)" {
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set f1fee86f-d786-4975-b1e6-e2459079d204
    linux /boot/vmlinuz-2.6.26-2-686 root=/dev/hdb1 ro quiet
    initrd /boot/initrd.img-2.6.26-2-686
}
menuentry "Debian GNU/Linux, kernel 2.6.26-2-686 (single-user mode) (on /dev/sdb1)" {
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set f1fee86f-d786-4975-b1e6-e2459079d204
    linux /boot/vmlinuz-2.6.26-2-686 root=/dev/hdb1 ro single
    initrd /boot/initrd.img-2.6.26-2-686
}
menuentry "UHU-Linux (on /dev/sdb6)" {
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set 30350380-85b3-4fbe-bf8f-e44d3c34279c
    linux /boot/bzImage root=/dev/hda7
    initrd (hd0,6)/boot/initrd
}
menuentry "SUSE (on /dev/sdb6)" {
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set 30350380-85b3-4fbe-bf8f-e44d3c34279c
    linux /boot/bzImage root=/dev/hdb1
    initrd (hd1,0)/boot/initrd
}
menuentry "DEBIAN (on /dev/sdb6)" {
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set 30350380-85b3-4fbe-bf8f-e44d3c34279c
    linux /boot/bzImage root=/dev/hda1
    initrd (hd0,0)/boot/initrd
}
menuentry "Memory Test (on /dev/sdb6)" {
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set 30350380-85b3-4fbe-bf8f-e44d3c34279c
    linux /boot/memtest.bin 
}
menuentry "linux (on /dev/sdb7)" {
    insmod ext2
    set root=(hd1,7)
    search --no-floppy --fs-uuid --set 29e86d2f-e722-4a88-a454-4ab9183a7b79
    linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=29e86d2f-e722-4a88-a454-4ab9183a7b79 resume=UUID=eaf6220d-330e-43c3-a304-afa536e3a379 splash=silent vga=788
    initrd (hd0,6)/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sdb7)" {
    insmod ext2
    set root=(hd1,7)
    search --no-floppy --fs-uuid --set 29e86d2f-e722-4a88-a454-4ab9183a7b79
    linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=29e86d2f-e722-4a88-a454-4ab9183a7b79 resume=UUID=eaf6220d-330e-43c3-a304-afa536e3a379
    initrd (hd0,6)/boot/initrd.img
}
menuentry "failsafe (on /dev/sdb7)" {
    insmod ext2
    set root=(hd1,7)
    search --no-floppy --fs-uuid --set 29e86d2f-e722-4a88-a454-4ab9183a7b79
    linux /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=29e86d2f-e722-4a88-a454-4ab9183a7b79 failsafe
    initrd (hd0,6)/boot/initrd.img
}
menuentry "Ubuntu 10.04 LTS, kernel 2.6.32-23-generic (on /dev/sdb9)" {
    insmod ext2
    set root=(hd1,9)
    search --no-floppy --fs-uuid --set fa509cd2-297a-4026-8fa2-2fc86d1e538c
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro quiet splash
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu 10.04 LTS, kernel 2.6.32-23-generic (recovery mode) (on /dev/sdb9)" {
    insmod ext2
    set root=(hd1,9)
    search --no-floppy --fs-uuid --set fa509cd2-297a-4026-8fa2-2fc86d1e538c
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro single
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu 10.04 LTS, kernel 2.6.31-22-generic (on /dev/sdb9)" {
    insmod ext2
    set root=(hd1,9)
    search --no-floppy --fs-uuid --set fa509cd2-297a-4026-8fa2-2fc86d1e538c
    linux /boot/vmlinuz-2.6.31-22-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro quiet splash
    initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu 10.04 LTS, kernel 2.6.31-22-generic (recovery mode) (on /dev/sdb9)" {
    insmod ext2
    set root=(hd1,9)
    search --no-floppy --fs-uuid --set fa509cd2-297a-4026-8fa2-2fc86d1e538c
    linux /boot/vmlinuz-2.6.31-22-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro single
    initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu 10.04 LTS, kernel 2.6.28-18-generic (on /dev/sdb9)" {
    insmod ext2
    set root=(hd1,9)
    search --no-floppy --fs-uuid --set fa509cd2-297a-4026-8fa2-2fc86d1e538c
    linux /boot/vmlinuz-2.6.28-18-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro quiet splash
    initrd /boot/initrd.img-2.6.28-18-generic
}
menuentry "Ubuntu 10.04 LTS, kernel 2.6.28-18-generic (recovery mode) (on /dev/sdb9)" {
    insmod ext2
    set root=(hd1,9)
    search --no-floppy --fs-uuid --set fa509cd2-297a-4026-8fa2-2fc86d1e538c
    linux /boot/vmlinuz-2.6.28-18-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro single
    initrd /boot/initrd.img-2.6.28-18-generic
}
menuentry "Ubuntu 10.04 LTS, memtest86+ (on /dev/sdb9)" {
    insmod ext2
    set root=(hd1,9)
    search --no-floppy --fs-uuid --set fa509cd2-297a-4026-8fa2-2fc86d1e538c
    linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb8 during installation
UUID=fd42d2b4-a627-4fd5-adbf-3e393cb8d1d3 /               ext4    errors=remount-ro 0       1
/dev/sdb5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb8: Location of files loaded by Grub: ===================


  83.6GB: boot/grub/core.img
  83.6GB: boot/grub/grub.cfg
  81.1GB: boot/grub/stage2
  81.7GB: boot/initrd.img-2.6.31-14-generic
  83.0GB: boot/vmlinuz-2.6.31-14-generic
  81.7GB: initrd.img
  83.0GB: vmlinuz

=========================== sdb9/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=fa509cd2-297a-4026-8fa2-2fc86d1e538c

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

title        Ubuntu 10.04 LTS, kernel 2.6.32-23-generic
uuid        fa509cd2-297a-4026-8fa2-2fc86d1e538c
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro quiet splash 
initrd        /boot/initrd.img-2.6.32-23-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-23-generic (recovery mode)
uuid        fa509cd2-297a-4026-8fa2-2fc86d1e538c
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro  single
initrd        /boot/initrd.img-2.6.32-23-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-22-generic
uuid        fa509cd2-297a-4026-8fa2-2fc86d1e538c
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro quiet splash 
initrd        /boot/initrd.img-2.6.31-22-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-22-generic (recovery mode)
uuid        fa509cd2-297a-4026-8fa2-2fc86d1e538c
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro  single
initrd        /boot/initrd.img-2.6.31-22-generic

title        Ubuntu 10.04 LTS, kernel 2.6.28-18-generic
uuid        fa509cd2-297a-4026-8fa2-2fc86d1e538c
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-18-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.28-18-generic (recovery mode)
uuid        fa509cd2-297a-4026-8fa2-2fc86d1e538c
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro  single
initrd        /boot/initrd.img-2.6.28-18-generic

title        Ubuntu 10.04 LTS, memtest86+
uuid        fa509cd2-297a-4026-8fa2-2fc86d1e538c
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title        openSUSE 11.1 (i586) (on /dev/sda2)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.27.7-9-pae root=/dev/sda2 
initrd        /boot/initrd-2.6.27.7-9-pae
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title        openSUSE 11.1 (i586) (on /dev/sda2)
root        (hd0,1)
kernel        /boot/vmlinux-2.6.27.7-9-pae.gz root=/dev/sda2 
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Debian GNU/Linux, kernel 2.6.18-6-k7 (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.18-6-k7 root=/dev/hdb1 ro 
initrd        /boot/initrd.img-2.6.18-6-k7
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Debian GNU/Linux, kernel 2.6.18-6-k7 (single-user mode) (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.18-6-k7 root=/dev/hdb1 ro single 
initrd        /boot/initrd.img-2.6.18-6-k7
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Debian GNU/Linux, kernel 2.6.18-5-k7 (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.18-5-k7 root=/dev/hdb1 ro 
initrd        /boot/initrd.img-2.6.18-5-k7
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Debian GNU/Linux, kernel 2.6.18-5-k7 (single-user mode) (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.18-5-k7 root=/dev/hdb1 ro single 
initrd        /boot/initrd.img-2.6.18-5-k7
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Debian GNU/Linux, kernel 2.6.18-4-k7 (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.18-4-k7 root=/dev/hdb1 ro 
initrd        /boot/initrd.img-2.6.18-4-k7
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Debian GNU/Linux, kernel 2.6.18-4-k7 (single-user mode) (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.18-4-k7 root=/dev/hdb1 ro single 
initrd        /boot/initrd.img-2.6.18-4-k7
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb6.
title        UHU-Linux (on /dev/sdb6)
root        (hd1,5)
kernel        /boot/bzImage root=/dev/hda7 
initrd        (hd0,6)/boot/initrd
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb6.
title        SUSE (on /dev/sdb6)
root        (hd1,5)
kernel        /boot/bzImage root=/dev/hdb1 
initrd        (hd1,0)/boot/initrd
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb6.
title        DEBIAN (on /dev/sdb6)
root        (hd1,5)
kernel        /boot/bzImage root=/dev/hda1 
initrd        (hd0,0)/boot/initrd
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb6.
title        Memory Test (on /dev/sdb6)
root        (hd1,5)
kernel        /boot/memtest.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb7.
title        linux (on /dev/sdb7)
root        (hd1,6)
kernel        /boot/vmlinuz BOOT_IMAGE=linux root=UUID=80fb0743-4982-417a-805e-4aeae82fb6df resume=UUID=61dce549-6f8b-4333-9f0d-cc00e91aa4b0 splash=silent vga=788 
initrd        (hd1,6)/boot/initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb7.
title        linux-nonfb (on /dev/sdb7)
root        (hd1,6)
kernel        /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=80fb0743-4982-417a-805e-4aeae82fb6df resume=UUID=61dce549-6f8b-4333-9f0d-cc00e91aa4b0 
initrd        (hd1,6)/boot/initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb7.
title        failsafe (on /dev/sdb7)
root        (hd1,6)
kernel        /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=80fb0743-4982-417a-805e-4aeae82fb6df failsafe 
initrd        (hd1,6)/boot/initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb8.
title        Ubuntu 7.10, memtest86+ (on /dev/sdb8)
root        (hd1,7)
kernel        /boot/memtest86+.bin  
savedefault
boot


=============================== sdb9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb9 during installation
UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c /               ext4    relatime,errors=remount-ro 0       1
/dev/sda1       none            swap    sw              0       0
/dev/sdb5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb9: Location of files loaded by Grub: ===================


  24.9GB: boot/grub/menu.lst
  21.1GB: boot/grub/stage2
  21.1GB: boot/initrd.img-2.6.28-18-generic
  35.7GB: boot/initrd.img-2.6.31-22-generic
  39.9GB: boot/initrd.img-2.6.32-23-generic
  35.8GB: boot/vmlinuz-2.6.28-18-generic
  39.4GB: boot/vmlinuz-2.6.31-22-generic
  38.8GB: boot/vmlinuz-2.6.32-23-generic
  39.9GB: initrd.img
  35.7GB: initrd.img.old
  38.8GB: vmlinuz
  39.4GB: vmlinuz.old

```

---

### Post by kansasnoob on 2010-07-26
Well look at hdb9:

```
hdb9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of hdb9 and 
                       looks at sector 5521695 on boot drive #1 for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/hda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'

```

Bad news from the get-go. I have no idea what you're doing.

---

### Post by lcutti on 2010-07-26
[SIZE=4]Does it make any extra confusion in partition numbering, that there is no sdb4 partition?[/SIZE]

---

### Post by banskt on 2010-07-26
Well, I think the problem is with the ext4 partition.

I hope that if you re-install Ubuntu with ext3 formatting, then things will work... but I am known to be wrong many times.

But, I had run into similar problems when I tried ext4, but things were resolved when I installed Ubuntu 10.04 with ext3 partitioning.

Edit: ext4 works fine for clean install, but somehow for upgrading, its create problems sometimes.

However, if you do not want the other OS'es (like Opensuse, Debian, etc), I would suggest you should do a clean install. If you have /home on a separate partition, remove all other partitions except that... and install ubuntu.

---

### Post by kansasnoob on 2010-07-27
> **banskt said:**
> Well, I think the problem is with the ext4 partition.

I hope that if you re-install Ubuntu with ext3 formatting, then things will work... but I am known to be wrong many times.

But, I had run into similar problems when I tried ext4, but things were resolved when I installed Ubuntu 10.04 with ext3 partitioning.

Nonsense!

---

### Post by lcutti on 2010-07-27
> **kansasnoob said:**
> Well look at hdb9:

```
hdb9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of hdb9 and 
                       looks at sector 5521695 on boot drive #1 for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/hda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Mounting failed:
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'

```Bad news from the get-go. I have no idea what you're doing.

That was in the old result file, that I made with Debian. It is not like that in the new result file.

---

### Post by banskt on 2010-07-27
> **kansasnoob said:**
> Nonsense!

Well, thank you, sir! I didn't want to make quite a sense... yes, the problem might be something else, and I am sure it is. However, that fixed my issue ;) .... and I was having similar problems...

---

### Post by lcutti on 2010-07-27
I did make a clean install of Karmic on sdb8, but it would not boot.
I do not have a working CD of Lucid, I have downloaded it twice but it did not work.

---

### Post by lcutti on 2010-07-27
ow I trzed to install  Karmic on on SDB8 with ext4 and sdb6 with ext3.
While installing, I tried to select hd0 or /dev/hda but with the same result.
In both cases I get

GRUB loading
_ and fast blinking cursor.

It seems, that it has overwritten Debians grub, since it is not starting any more.


Here is my new boot info script result

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=b2466a87-691a-4776-9511-5de4c411cf43)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sda1 and 
                       looks at sector 5521695 of the same hard drive for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Welcome to openSUSE 11.1 - 
                       Kernel ().
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Debian GNU/Linux 5.0
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Mandriva Linux release 2009.0 
                       (Official) for i586 Kernel 
                       2.6.27-desktop586-0.rc8.2mnb on an i686 /
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub
    Boot sector info:  Grub 0.97 is installed in the boot sector of sdb9 and 
                       looks at sector 5521695 on boot drive #1 for the 
                       stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #1 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb3: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 20.8 GB, 20847697920 bytes
255 heads, 63 sectors/track, 2534 cylinders, total 40718160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1623456f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    40,708,709    40,708,647  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004fa18

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    39,070,079    39,070,017  83 Linux
/dev/sdb2    *     39,070,080   197,310,329   158,240,250   5 Extended
/dev/sdb5          39,070,143    41,030,009     1,959,867  82 Linux swap / Solaris
/dev/sdb6          80,100,153   119,170,169    39,070,017  83 Linux
/dev/sdb7         119,170,233   153,003,059    33,832,827  83 Linux
/dev/sdb8         158,240,313   197,310,329    39,070,017  83 Linux
/dev/sdb9          41,030,073    80,100,089    39,070,017  83 Linux
/dev/sdb3         197,310,330   390,716,864   193,406,535  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        39c1e643-6cbb-425f-99ca-a999b0812114   ext3                                     
/dev/sdb1        f1fee86f-d786-4975-b1e6-e2459079d204   ext3       debian                        
/dev/sdb3        c20e205a-907e-4f6a-b8cf-748dbb8fd3ce   ext2                                     
/dev/sdb5                                               swap                                     
/dev/sdb6        b2466a87-691a-4776-9511-5de4c411cf43   ext3                                     
/dev/sdb7        29e86d2f-e722-4a88-a454-4ab9183a7b79   ext3       mandriva                      
/dev/sdb8        ebb2ee4e-cfd1-4e58-b860-0cfdf836be1b   ext4                                     
/dev/sdb9        fa509cd2-297a-4026-8fa2-2fc86d1e538c   ext4                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb1        /media/debian            ext3       (rw,nosuid,nodev,uhelper=devkit)


=========================== sda1/boot/grub/menu.lst: ===========================

# Modified by YaST2. Last modification on Fri Jul 23 17:34:03 CEST 2010
default 0
timeout 8
##YaST - generic_mbr
gfxmenu (hd0,0)/boot/message
##YaST - activate

###Don't change this comment - YaST2 identifier: Original name: linux###
title openSUSE 11.1 - 2.6.27.7-9
    root (hd0,0)
    kernel /boot/vmlinuz-2.6.27.7-9-pae root=/dev/disk/by-id/ata-Maxtor_2F020L0_F16B40LE-part1 resume=/dev/disk/by-id/ata-SAMSUNG_SP2014N_S088J1LLA03607-part5 splash=silent showopts vga=0x31a
    initrd /boot/initrd-2.6.27.7-9-pae

###Don't change this comment - YaST2 identifier: Original name: failsafe###
title Failsafe -- openSUSE 11.1 - 2.6.27.7-9
    root (hd0,0)
    kernel /boot/vmlinuz-2.6.27.7-9-pae root=/dev/disk/by-id/ata-Maxtor_2F020L0_F16B40LE-part1 showopts ide=nodma apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x31a
    initrd /boot/initrd-2.6.27.7-9-pae

###Don't change this comment - YaST2 identifier: Original name:  Debian GNU/Linux, kernel 2.6.18-6-k7 (/dev/sdb1)###
title Debian GNU/Linux, kernel 2.6.18-6-k7 (/dev/sdb1)
    root (hd1,0)
    configfile /boot/grub/menu.lst

###Don't change this comment - YaST2 identifier: Original name:  UHU-Linux (/dev/sdb6)###
title UHU-Linux (/dev/sdb6)
    rootnoverify (hd1,5)
    chainloader +1

###Don't change this comment - YaST2 identifier: Original name:  linux (/dev/sdb9)###
title linux (/dev/sdb9)
    root (hd1,6)
    configfile /boot/grub/menu.lst

###Don't change this comment - YaST2 identifier: Original name:  Ubuntu 7.10, memtest86+ (/dev/sdb8)###
title Ubuntu 7.10, memtest86+ (/dev/sdb8)
    root (hd1,7)
    configfile /boot/grub/menu.lst

###Don't change this comment - YaST2 identifier: Original name: floppy###
title Floppy
    rootnoverify (fd0)
    chainloader +1

=============================== sda1/etc/fstab: ===============================

/dev/disk/by-id/ata-SAMSUNG_SP2014N_S088J1LLA03607-part5 swap                 swap       defaults              0 0
/dev/disk/by-id/ata-Maxtor_2F020L0_F16B40LE-part1 /                    ext3       acl,user_xattr        1 1
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
usbfs                /proc/bus/usb        usbfs      noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0

=================== sda1: Location of files loaded by Grub: ===================


   2.9GB: boot/grub/menu.lst
   2.8GB: boot/grub/stage2
   2.8GB: boot/initrd
   2.8GB: boot/initrd-2.6.27.7-9-pae
   2.8GB: boot/vmlinuz
   2.8GB: boot/vmlinuz-2.6.27.7-9-pae

=========================== sdb1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        5

# Pretty colours
color cyan/blue white/blue

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
# kopt=root=/dev/hdb1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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
# defoptions=quiet

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
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

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

title        Debian GNU/Linux, kernel 2.6.26-2-686
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.26-2-686 root=/dev/hdb1 ro quiet
initrd        /boot/initrd.img-2.6.26-2-686

title        Debian GNU/Linux, kernel 2.6.26-2-686 (single-user mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.26-2-686 root=/dev/hdb1 ro single
initrd        /boot/initrd.img-2.6.26-2-686

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

/media/mandriva/boot/vmlinuz-2.6.27-desktop586-0.rc8.2mnb
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdb7.
title        mandriva linux (on /dev/hdb7)
root        (hd1,6)
kernel        /boot/vmlinuz-2.6.27-desktop586-0.rc8.2mnb root=/dev/hdb6 ro quiet
initrd        (hd1,6)/boot/initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title        openSUSE 11.1 - 2.6.27.7-9 (on /dev/hda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27.7-9-pae root=/dev/disk/by-id/ata-Maxtor_2F020L0_F16B40LE-part1 resume=/dev/disk/by-id/ata-SAMSUNG_SP2014N_S088J1LLA03607-part5 splash=silent showopts vga=0x31a 
initrd        /boot/initrd-2.6.27.7-9-pae
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda1.
title        Failsafe -- openSUSE 11.1 - 2.6.27.7-9 (on /dev/hda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.27.7-9-pae root=/dev/disk/by-id/ata-Maxtor_2F020L0_F16B40LE-part1 showopts ide=nodma apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x31a 
initrd        /boot/initrd-2.6.27.7-9-pae
savedefault
boot


title        Ubuntu 10.04 LTS, kernel 2.6.32-23-generic
root        (hd1,8)
kernel        /boot/vmlinuz-2.6.32-23-generic root=/dev/sdb9 ro quiet
initrd        /boot/initrd.img-2.6.32-23-generic


title        Ubuntu 10.04 LTS, kernel 2.6.32-23-generic (recovery mode)
uuid        fa509cd2-297a-4026-8fa2-2fc86d1e538c
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro  single
initrd        /boot/initrd.img-2.6.32-23-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-22-generic
uuid        fa509cd2-297a-4026-8fa2-2fc86d1e538c
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro quiet splash 
initrd        /boot/initrd.img-2.6.31-22-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-22-generic (recovery mode)
uuid        fa509cd2-297a-4026-8fa2-2fc86d1e538c
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro  single
initrd        /boot/initrd.img-2.6.31-22-generic

title        Ubuntu 10.04 LTS, kernel 2.6.28-18-generic
uuid        fa509cd2-297a-4026-8fa2-2fc86d1e538c
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-18-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.28-18-generic (recovery mode)
uuid        fa509cd2-297a-4026-8fa2-2fc86d1e538c
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro  single
initrd        /boot/initrd.img-2.6.28-18-generic

title        Ubuntu 10.04 LTS, memtest86+
uuid        fa509cd2-297a-4026-8fa2-2fc86d1e538c
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST



=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

=================== sdb1: Location of files loaded by Grub: ===================


  11.2GB: boot/grub/menu.lst
  11.1GB: boot/grub/stage2
  11.2GB: boot/initrd.img-2.6.26-2-686
  11.1GB: boot/initrd.img-2.6.26-2-686.bak
  11.2GB: boot/vmlinuz-2.6.26-2-686
  11.2GB: initrd.img
  11.2GB: vmlinuz

=========================== sdb6/boot/grub/grub.cfg: ===========================

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
set root=(hd1,6)
search --no-floppy --fs-uuid --set b2466a87-691a-4776-9511-5de4c411cf43
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set b2466a87-691a-4776-9511-5de4c411cf43
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b2466a87-691a-4776-9511-5de4c411cf43 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set b2466a87-691a-4776-9511-5de4c411cf43
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b2466a87-691a-4776-9511-5de4c411cf43 ro single 
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
menuentry "openSUSE 11.1 - 2.6.27.7-9 (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 39c1e643-6cbb-425f-99ca-a999b0812114
    linux /boot/vmlinuz-2.6.27.7-9-pae root=/dev/disk/by-id/ata-Maxtor_2F020L0_F16B40LE-part1 resume=/dev/disk/by-id/ata-SAMSUNG_SP2014N_S088J1LLA03607-part5 splash=silent showopts vga=0x31a
    initrd /boot/initrd-2.6.27.7-9-pae
}
menuentry "Failsafe -- openSUSE 11.1 - 2.6.27.7-9 (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 39c1e643-6cbb-425f-99ca-a999b0812114
    linux /boot/vmlinuz-2.6.27.7-9-pae root=/dev/disk/by-id/ata-Maxtor_2F020L0_F16B40LE-part1 showopts ide=nodma apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x31a
    initrd /boot/initrd-2.6.27.7-9-pae
}
menuentry "Debian GNU/Linux, kernel 2.6.26-2-686 (on /dev/sdb1)" {
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set f1fee86f-d786-4975-b1e6-e2459079d204
    linux /boot/vmlinuz-2.6.26-2-686 root=/dev/hdb1 ro quiet
    initrd /boot/initrd.img-2.6.26-2-686
}
menuentry "Debian GNU/Linux, kernel 2.6.26-2-686 (single-user mode) (on /dev/sdb1)" {
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set f1fee86f-d786-4975-b1e6-e2459079d204
    linux /boot/vmlinuz-2.6.26-2-686 root=/dev/hdb1 ro single
    initrd /boot/initrd.img-2.6.26-2-686
}
menuentry "linux (on /dev/sdb7)" {
    insmod ext2
    set root=(hd1,7)
    search --no-floppy --fs-uuid --set 29e86d2f-e722-4a88-a454-4ab9183a7b79
    linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=29e86d2f-e722-4a88-a454-4ab9183a7b79 resume=UUID=eaf6220d-330e-43c3-a304-afa536e3a379 splash=silent vga=788
    initrd (hd0,6)/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sdb7)" {
    insmod ext2
    set root=(hd1,7)
    search --no-floppy --fs-uuid --set 29e86d2f-e722-4a88-a454-4ab9183a7b79
    linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=29e86d2f-e722-4a88-a454-4ab9183a7b79 resume=UUID=eaf6220d-330e-43c3-a304-afa536e3a379
    initrd (hd0,6)/boot/initrd.img
}
menuentry "failsafe (on /dev/sdb7)" {
    insmod ext2
    set root=(hd1,7)
    search --no-floppy --fs-uuid --set 29e86d2f-e722-4a88-a454-4ab9183a7b79
    linux /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=29e86d2f-e722-4a88-a454-4ab9183a7b79 failsafe
    initrd (hd0,6)/boot/initrd.img
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdb8)" {
    insmod ext2
    set root=(hd1,8)
    search --no-floppy --fs-uuid --set ebb2ee4e-cfd1-4e58-b860-0cfdf836be1b
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=ebb2ee4e-cfd1-4e58-b860-0cfdf836be1b ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdb8)" {
    insmod ext2
    set root=(hd1,8)
    search --no-floppy --fs-uuid --set ebb2ee4e-cfd1-4e58-b860-0cfdf836be1b
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=ebb2ee4e-cfd1-4e58-b860-0cfdf836be1b ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu 10.04 LTS, kernel 2.6.32-23-generic (on /dev/sdb9)" {
    insmod ext2
    set root=(hd1,9)
    search --no-floppy --fs-uuid --set fa509cd2-297a-4026-8fa2-2fc86d1e538c
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro quiet splash
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu 10.04 LTS, kernel 2.6.32-23-generic (recovery mode) (on /dev/sdb9)" {
    insmod ext2
    set root=(hd1,9)
    search --no-floppy --fs-uuid --set fa509cd2-297a-4026-8fa2-2fc86d1e538c
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro single
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu 10.04 LTS, kernel 2.6.31-22-generic (on /dev/sdb9)" {
    insmod ext2
    set root=(hd1,9)
    search --no-floppy --fs-uuid --set fa509cd2-297a-4026-8fa2-2fc86d1e538c
    linux /boot/vmlinuz-2.6.31-22-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro quiet splash
    initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu 10.04 LTS, kernel 2.6.31-22-generic (recovery mode) (on /dev/sdb9)" {
    insmod ext2
    set root=(hd1,9)
    search --no-floppy --fs-uuid --set fa509cd2-297a-4026-8fa2-2fc86d1e538c
    linux /boot/vmlinuz-2.6.31-22-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro single
    initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu 10.04 LTS, kernel 2.6.28-18-generic (on /dev/sdb9)" {
    insmod ext2
    set root=(hd1,9)
    search --no-floppy --fs-uuid --set fa509cd2-297a-4026-8fa2-2fc86d1e538c
    linux /boot/vmlinuz-2.6.28-18-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro quiet splash
    initrd /boot/initrd.img-2.6.28-18-generic
}
menuentry "Ubuntu 10.04 LTS, kernel 2.6.28-18-generic (recovery mode) (on /dev/sdb9)" {
    insmod ext2
    set root=(hd1,9)
    search --no-floppy --fs-uuid --set fa509cd2-297a-4026-8fa2-2fc86d1e538c
    linux /boot/vmlinuz-2.6.28-18-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro single
    initrd /boot/initrd.img-2.6.28-18-generic
}
menuentry "Ubuntu 10.04 LTS, memtest86+ (on /dev/sdb9)" {
    insmod ext2
    set root=(hd1,9)
    search --no-floppy --fs-uuid --set fa509cd2-297a-4026-8fa2-2fc86d1e538c
    linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb6 during installation
UUID=b2466a87-691a-4776-9511-5de4c411cf43 /               ext3    errors=remount-ro 0       1
/dev/sdb5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb6: Location of files loaded by Grub: ===================


  57.5GB: boot/grub/core.img
  57.5GB: boot/grub/grub.cfg
  57.6GB: boot/initrd.img-2.6.31-14-generic
  57.6GB: boot/vmlinuz-2.6.31-14-generic
  57.6GB: initrd.img
  57.6GB: vmlinuz

=========================== sdb7/boot/grub/menu.lst: ===========================

timeout 10
color black/cyan yellow/cyan
default 0

title linux
kernel (hd0,6)/boot/vmlinuz BOOT_IMAGE=linux root=UUID=29e86d2f-e722-4a88-a454-4ab9183a7b79  resume=UUID=eaf6220d-330e-43c3-a304-afa536e3a379 splash=silent vga=788
initrd (hd0,6)/boot/initrd.img

title linux-nonfb
kernel (hd0,6)/boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=29e86d2f-e722-4a88-a454-4ab9183a7b79  resume=UUID=eaf6220d-330e-43c3-a304-afa536e3a379
initrd (hd0,6)/boot/initrd.img

title failsafe
kernel (hd0,6)/boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=29e86d2f-e722-4a88-a454-4ab9183a7b79  failsafe
initrd (hd0,6)/boot/initrd.img

title openSUSE 11.1 (i586)
VERSION = 11.1
root (hd1,1)
configfile /boot/grub/menu.lst

title Debian GNU/Linux 5.0 
root (hd0,0)
configfile /boot/grub/menu.lst

title Linux sdb6
root (hd0,5)
configfile /boot/grub/menu.lst

title Ubuntu 8.04 
root (hd0,7)
configfile /boot/grub/menu.lst

=============================== sdb7/etc/fstab: ===============================

# Entry for /dev/sdb7 :
UUID=29e86d2f-e722-4a88-a454-4ab9183a7b79 / ext3 defaults 1 1
none /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=ee82220c-54d9-4d90-a432-ffcef328d103 swap swap defaults 0 0
# Entry for /dev/sdb5 :
UUID=eaf6220d-330e-43c3-a304-afa536e3a379 swap swap defaults 0 0

=================== sdb7: Location of files loaded by Grub: ===================


  74.4GB: boot/grub/menu.lst
  74.4GB: boot/grub/stage2
  74.3GB: boot/initrd-2.6.27-desktop586-0.rc8.2mnb.img
  74.3GB: boot/initrd-desktop586.img
  74.3GB: boot/initrd.img
  74.3GB: boot/vmlinuz
  74.3GB: boot/vmlinuz-2.6.27-desktop586-0.rc8.2mnb
  74.3GB: boot/vmlinuz-desktop586

=========================== sdb8/boot/grub/grub.cfg: ===========================

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
set root=(hd1,8)
search --no-floppy --fs-uuid --set ebb2ee4e-cfd1-4e58-b860-0cfdf836be1b
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,8)
    search --no-floppy --fs-uuid --set ebb2ee4e-cfd1-4e58-b860-0cfdf836be1b
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=ebb2ee4e-cfd1-4e58-b860-0cfdf836be1b ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,8)
    search --no-floppy --fs-uuid --set ebb2ee4e-cfd1-4e58-b860-0cfdf836be1b
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=ebb2ee4e-cfd1-4e58-b860-0cfdf836be1b ro single 
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
menuentry "openSUSE 11.1 - 2.6.27.7-9 (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 39c1e643-6cbb-425f-99ca-a999b0812114
    linux /boot/vmlinuz-2.6.27.7-9-pae root=/dev/disk/by-id/ata-Maxtor_2F020L0_F16B40LE-part1 resume=/dev/disk/by-id/ata-SAMSUNG_SP2014N_S088J1LLA03607-part5 splash=silent showopts vga=0x31a
    initrd /boot/initrd-2.6.27.7-9-pae
}
menuentry "Failsafe -- openSUSE 11.1 - 2.6.27.7-9 (on /dev/sda1)" {
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 39c1e643-6cbb-425f-99ca-a999b0812114
    linux /boot/vmlinuz-2.6.27.7-9-pae root=/dev/disk/by-id/ata-Maxtor_2F020L0_F16B40LE-part1 showopts ide=nodma apm=off noresume nosmp maxcpus=0 edd=off powersaved=off nohz=off highres=off processor.max_cstate=1 x11failsafe vga=0x31a
    initrd /boot/initrd-2.6.27.7-9-pae
}
menuentry "Debian GNU/Linux, kernel 2.6.26-2-686 (on /dev/sdb1)" {
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set f1fee86f-d786-4975-b1e6-e2459079d204
    linux /boot/vmlinuz-2.6.26-2-686 root=/dev/hdb1 ro quiet
    initrd /boot/initrd.img-2.6.26-2-686
}
menuentry "Debian GNU/Linux, kernel 2.6.26-2-686 (single-user mode) (on /dev/sdb1)" {
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set f1fee86f-d786-4975-b1e6-e2459079d204
    linux /boot/vmlinuz-2.6.26-2-686 root=/dev/hdb1 ro single
    initrd /boot/initrd.img-2.6.26-2-686
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (on /dev/sdb6)" {
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set ba6704d3-4229-4c69-97dd-28b581f5a0e0
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=ba6704d3-4229-4c69-97dd-28b581f5a0e0 ro quiet splash
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode) (on /dev/sdb6)" {
    insmod ext2
    set root=(hd1,6)
    search --no-floppy --fs-uuid --set ba6704d3-4229-4c69-97dd-28b581f5a0e0
    linux /boot/vmlinuz-2.6.31-14-generic root=UUID=ba6704d3-4229-4c69-97dd-28b581f5a0e0 ro single
    initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "linux (on /dev/sdb7)" {
    insmod ext2
    set root=(hd1,7)
    search --no-floppy --fs-uuid --set 29e86d2f-e722-4a88-a454-4ab9183a7b79
    linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=29e86d2f-e722-4a88-a454-4ab9183a7b79 resume=UUID=eaf6220d-330e-43c3-a304-afa536e3a379 splash=silent vga=788
    initrd (hd0,6)/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sdb7)" {
    insmod ext2
    set root=(hd1,7)
    search --no-floppy --fs-uuid --set 29e86d2f-e722-4a88-a454-4ab9183a7b79
    linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=29e86d2f-e722-4a88-a454-4ab9183a7b79 resume=UUID=eaf6220d-330e-43c3-a304-afa536e3a379
    initrd (hd0,6)/boot/initrd.img
}
menuentry "failsafe (on /dev/sdb7)" {
    insmod ext2
    set root=(hd1,7)
    search --no-floppy --fs-uuid --set 29e86d2f-e722-4a88-a454-4ab9183a7b79
    linux /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=29e86d2f-e722-4a88-a454-4ab9183a7b79 failsafe
    initrd (hd0,6)/boot/initrd.img
}
menuentry "Ubuntu 10.04 LTS, kernel 2.6.32-23-generic (on /dev/sdb9)" {
    insmod ext2
    set root=(hd1,9)
    search --no-floppy --fs-uuid --set fa509cd2-297a-4026-8fa2-2fc86d1e538c
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro quiet splash
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu 10.04 LTS, kernel 2.6.32-23-generic (recovery mode) (on /dev/sdb9)" {
    insmod ext2
    set root=(hd1,9)
    search --no-floppy --fs-uuid --set fa509cd2-297a-4026-8fa2-2fc86d1e538c
    linux /boot/vmlinuz-2.6.32-23-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro single
    initrd /boot/initrd.img-2.6.32-23-generic
}
menuentry "Ubuntu 10.04 LTS, kernel 2.6.31-22-generic (on /dev/sdb9)" {
    insmod ext2
    set root=(hd1,9)
    search --no-floppy --fs-uuid --set fa509cd2-297a-4026-8fa2-2fc86d1e538c
    linux /boot/vmlinuz-2.6.31-22-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro quiet splash
    initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu 10.04 LTS, kernel 2.6.31-22-generic (recovery mode) (on /dev/sdb9)" {
    insmod ext2
    set root=(hd1,9)
    search --no-floppy --fs-uuid --set fa509cd2-297a-4026-8fa2-2fc86d1e538c
    linux /boot/vmlinuz-2.6.31-22-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro single
    initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu 10.04 LTS, kernel 2.6.28-18-generic (on /dev/sdb9)" {
    insmod ext2
    set root=(hd1,9)
    search --no-floppy --fs-uuid --set fa509cd2-297a-4026-8fa2-2fc86d1e538c
    linux /boot/vmlinuz-2.6.28-18-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro quiet splash
    initrd /boot/initrd.img-2.6.28-18-generic
}
menuentry "Ubuntu 10.04 LTS, kernel 2.6.28-18-generic (recovery mode) (on /dev/sdb9)" {
    insmod ext2
    set root=(hd1,9)
    search --no-floppy --fs-uuid --set fa509cd2-297a-4026-8fa2-2fc86d1e538c
    linux /boot/vmlinuz-2.6.28-18-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro single
    initrd /boot/initrd.img-2.6.28-18-generic
}
menuentry "Ubuntu 10.04 LTS, memtest86+ (on /dev/sdb9)" {
    insmod ext2
    set root=(hd1,9)
    search --no-floppy --fs-uuid --set fa509cd2-297a-4026-8fa2-2fc86d1e538c
    linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb8 during installation
UUID=ebb2ee4e-cfd1-4e58-b860-0cfdf836be1b /               ext4    errors=remount-ro 0       1
/dev/sdb5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb8: Location of files loaded by Grub: ===================


  83.6GB: boot/grub/core.img
  83.6GB: boot/grub/grub.cfg
  81.7GB: boot/initrd.img-2.6.31-14-generic
  83.0GB: boot/vmlinuz-2.6.31-14-generic
  81.7GB: initrd.img
  83.0GB: vmlinuz

=========================== sdb9/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=fa509cd2-297a-4026-8fa2-2fc86d1e538c

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

title        Ubuntu 10.04 LTS, kernel 2.6.32-23-generic
uuid        fa509cd2-297a-4026-8fa2-2fc86d1e538c
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro quiet splash 
initrd        /boot/initrd.img-2.6.32-23-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.32-23-generic (recovery mode)
uuid        fa509cd2-297a-4026-8fa2-2fc86d1e538c
kernel        /boot/vmlinuz-2.6.32-23-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro  single
initrd        /boot/initrd.img-2.6.32-23-generic

title        Ubuntu 10.04 LTS, kernel 2.6.31-22-generic
uuid        fa509cd2-297a-4026-8fa2-2fc86d1e538c
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro quiet splash 
initrd        /boot/initrd.img-2.6.31-22-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.31-22-generic (recovery mode)
uuid        fa509cd2-297a-4026-8fa2-2fc86d1e538c
kernel        /boot/vmlinuz-2.6.31-22-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro  single
initrd        /boot/initrd.img-2.6.31-22-generic

title        Ubuntu 10.04 LTS, kernel 2.6.28-18-generic
uuid        fa509cd2-297a-4026-8fa2-2fc86d1e538c
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro quiet splash 
initrd        /boot/initrd.img-2.6.28-18-generic
quiet

title        Ubuntu 10.04 LTS, kernel 2.6.28-18-generic (recovery mode)
uuid        fa509cd2-297a-4026-8fa2-2fc86d1e538c
kernel        /boot/vmlinuz-2.6.28-18-generic root=UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c ro  single
initrd        /boot/initrd.img-2.6.28-18-generic

title        Ubuntu 10.04 LTS, memtest86+
uuid        fa509cd2-297a-4026-8fa2-2fc86d1e538c
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title        openSUSE 11.1 (i586) (on /dev/sda2)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.27.7-9-pae root=/dev/sda2 
initrd        /boot/initrd-2.6.27.7-9-pae
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title        openSUSE 11.1 (i586) (on /dev/sda2)
root        (hd0,1)
kernel        /boot/vmlinux-2.6.27.7-9-pae.gz root=/dev/sda2 
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Debian GNU/Linux, kernel 2.6.18-6-k7 (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.18-6-k7 root=/dev/hdb1 ro 
initrd        /boot/initrd.img-2.6.18-6-k7
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Debian GNU/Linux, kernel 2.6.18-6-k7 (single-user mode) (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.18-6-k7 root=/dev/hdb1 ro single 
initrd        /boot/initrd.img-2.6.18-6-k7
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Debian GNU/Linux, kernel 2.6.18-5-k7 (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.18-5-k7 root=/dev/hdb1 ro 
initrd        /boot/initrd.img-2.6.18-5-k7
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Debian GNU/Linux, kernel 2.6.18-5-k7 (single-user mode) (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.18-5-k7 root=/dev/hdb1 ro single 
initrd        /boot/initrd.img-2.6.18-5-k7
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Debian GNU/Linux, kernel 2.6.18-4-k7 (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.18-4-k7 root=/dev/hdb1 ro 
initrd        /boot/initrd.img-2.6.18-4-k7
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title        Debian GNU/Linux, kernel 2.6.18-4-k7 (single-user mode) (on /dev/sdb1)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.18-4-k7 root=/dev/hdb1 ro single 
initrd        /boot/initrd.img-2.6.18-4-k7
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb6.
title        UHU-Linux (on /dev/sdb6)
root        (hd1,5)
kernel        /boot/bzImage root=/dev/hda7 
initrd        (hd0,6)/boot/initrd
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb6.
title        SUSE (on /dev/sdb6)
root        (hd1,5)
kernel        /boot/bzImage root=/dev/hdb1 
initrd        (hd1,0)/boot/initrd
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb6.
title        DEBIAN (on /dev/sdb6)
root        (hd1,5)
kernel        /boot/bzImage root=/dev/hda1 
initrd        (hd0,0)/boot/initrd
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb6.
title        Memory Test (on /dev/sdb6)
root        (hd1,5)
kernel        /boot/memtest.bin  
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb7.
title        linux (on /dev/sdb7)
root        (hd1,6)
kernel        /boot/vmlinuz BOOT_IMAGE=linux root=UUID=80fb0743-4982-417a-805e-4aeae82fb6df resume=UUID=61dce549-6f8b-4333-9f0d-cc00e91aa4b0 splash=silent vga=788 
initrd        (hd1,6)/boot/initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb7.
title        linux-nonfb (on /dev/sdb7)
root        (hd1,6)
kernel        /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=80fb0743-4982-417a-805e-4aeae82fb6df resume=UUID=61dce549-6f8b-4333-9f0d-cc00e91aa4b0 
initrd        (hd1,6)/boot/initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb7.
title        failsafe (on /dev/sdb7)
root        (hd1,6)
kernel        /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=80fb0743-4982-417a-805e-4aeae82fb6df failsafe 
initrd        (hd1,6)/boot/initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb8.
title        Ubuntu 7.10, memtest86+ (on /dev/sdb8)
root        (hd1,7)
kernel        /boot/memtest86+.bin  
savedefault
boot


=============================== sdb9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb9 during installation
UUID=fa509cd2-297a-4026-8fa2-2fc86d1e538c /               ext4    relatime,errors=remount-ro 0       1
/dev/sda1       none            swap    sw              0       0
/dev/sdb5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb9: Location of files loaded by Grub: ===================


  24.9GB: boot/grub/menu.lst
  21.1GB: boot/grub/stage2
  21.1GB: boot/initrd.img-2.6.28-18-generic
  35.7GB: boot/initrd.img-2.6.31-22-generic
  39.9GB: boot/initrd.img-2.6.32-23-generic
  35.8GB: boot/vmlinuz-2.6.28-18-generic
  39.4GB: boot/vmlinuz-2.6.31-22-generic
  38.8GB: boot/vmlinuz-2.6.32-23-generic
  39.9GB: initrd.img
  35.7GB: initrd.img.old
  38.8GB: vmlinuz
  39.4GB: vmlinuz.old

```

---

### Post by lcutti on 2010-07-27
Could anyone tell me a simple solution to just boot into the 10.4 on sdb9 and forget all the other partitions?

---

