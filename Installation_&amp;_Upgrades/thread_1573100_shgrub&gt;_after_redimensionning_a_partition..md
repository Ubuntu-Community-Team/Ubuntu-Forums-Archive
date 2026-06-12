---
title: "sh:grub&gt; after redimensionning a partition."
date: 2010-09-12
forum: Installation &amp; Upgrades
---

### Post by Factran on 2010-09-12
Hello !
I have a grub problem :
I resized a partition and now I boot directly into GNU grub rescue

```
sh:grub:>
```

if I type 
```
sh:grub> linux /boot/vmlinuz-2.6.32-22-generic
sh:grub> initrd /boot/initrd.img-2.6.32-22.generic
sh:grub> boot
```

I have the following messages :

```
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
 - Check rootdelay= (did the system wait long enough?)
 - Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)

ALERT! does not exist. Dropping to a shell!


BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _

```

Here is the /proc/cmdline I have 
```
(initramfs) cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic
```

I use Grub 2. I can boot via live CD. 
I have a boot directory in one of my logical partition, grub doesn't seem to find it.
What can I do to boot ?
Could you give me some pointers ?

---

### Post by drs305 on 2010-09-12
Your UUIDs may have changed. If you want to try to boot by editing the boot option, at the grub menu press "e" to open the menuentry for editing. Cursor to the "search" line (if it exists) and remove it by holding down the DEL key. 

In the "linux" line, change the "root=UUID=..." to "... root=/dev/sdXY ..."
with the correct XY values for your Ubuntu partition.

Then CTRL-X to boot. Once into Ubuntu, update grub with "sudo update-grub".

If this doesn't get your machine booting, run *meierfra's* [boot info script]("http://bootinfoscript.sourceforge.net/") and post the results between "code" tags. Generate the tags by pressing the # symbol in the post's menubar.

---

### Post by Factran on 2010-09-12
No, I don't reach the grub menu, I directly go into grub rescue, so I couldn't boot in my ubuntu and make "sudo update-grub"

Here is the result.txt
Thanks  !

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => Grub 0.97 is installed in the MBR of /dev/sdf and looks on boot drive #3 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdf1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa0000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       128,519       128,457  de Dell Utility
/dev/sda2             129,024    31,586,303    31,457,280   7 HPFS/NTFS
/dev/sda3    *     31,586,304   148,773,803   117,187,500   7 HPFS/NTFS
/dev/sda4         148,777,965 1,250,258,624 1,101,480,660   5 Extended
/dev/sda5         148,778,028   300,335,174   151,557,147  83 Linux
/dev/sda6       1,232,169,498 1,250,258,624    18,089,127  82 Linux swap / Solaris
/dev/sda7         300,335,238 1,139,651,099   839,315,862  83 Linux
/dev/sda8       1,139,651,163 1,232,169,434    92,518,272  83 Linux


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 255 MB, 255852544 bytes
8 heads, 63 sectors/track, 991 cylinders, total 499712 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdf1    *             63       499,463       499,401   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        07D9-080A                              vfat       DellUtility                   
/dev/sda2        507AFFF37AFFD426                       ntfs       RECOVERY                      
/dev/sda3        FC9C02319C01E6CC                       ntfs       OS                            
/dev/sda5        fe7a46c0-ace7-49cd-92e2-aac1aed53e9b   ext3                                     
/dev/sda6        7d82db34-dbc6-4d4c-9801-ecb70f9c1a4a   swap                                     
/dev/sda7        0c35e852-9dd1-4000-830c-0dfa9abdecc3   ext4       maison                        
/dev/sda8        952be256-de62-45e1-8997-d7639d3c2080   ext3                                     
/dev/sdf1        C034-CA06                              vfat       256MBHEOUI                    

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sda5        /media/fe7a46c0-ace7-49cd-92e2-aac1aed53e9b ext3       (rw,nosuid,nodev,uhelper=devkit)
/dev/sdf1        /media/256MBHEOUI        vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=fe7a46c0-ace7-49cd-92e2-aac1aed53e9b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=fe7a46c0-ace7-49cd-92e2-aac1aed53e9b

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

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic
root		(hda0,4)
kernel		/boot/vmlinuz-2.6.32-22-generic root=/dev/sda5 ro  
initrd		/boot/initrd.img-2.6.32-22-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.32-22-generic (recovery mode)
uuid		fe7a46c0-ace7-49cd-92e2-aac1aed53e9b
kernel		/boot/vmlinuz-2.6.32-22-generic root=UUID=fe7a46c0-ace7-49cd-92e2-aac1aed53e9b ro  single
initrd		/boot/initrd.img-2.6.32-22-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-21-generic
uuid		fe7a46c0-ace7-49cd-92e2-aac1aed53e9b
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=fe7a46c0-ace7-49cd-92e2-aac1aed53e9b ro quiet splash 
initrd		/boot/initrd.img-2.6.31-21-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.31-21-generic (recovery mode)
uuid		fe7a46c0-ace7-49cd-92e2-aac1aed53e9b
kernel		/boot/vmlinuz-2.6.31-21-generic root=UUID=fe7a46c0-ace7-49cd-92e2-aac1aed53e9b ro  single
initrd		/boot/initrd.img-2.6.31-21-generic

title		Ubuntu 10.04 LTS, kernel 2.6.31-10-rt
uuid		fe7a46c0-ace7-49cd-92e2-aac1aed53e9b
kernel		/boot/vmlinuz-2.6.31-10-rt root=UUID=fe7a46c0-ace7-49cd-92e2-aac1aed53e9b ro quiet splash 
initrd		/boot/initrd.img-2.6.31-10-rt
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.31-10-rt (recovery mode)
uuid		fe7a46c0-ace7-49cd-92e2-aac1aed53e9b
kernel		/boot/vmlinuz-2.6.31-10-rt root=UUID=fe7a46c0-ace7-49cd-92e2-aac1aed53e9b ro  single
initrd		/boot/initrd.img-2.6.31-10-rt

title		Ubuntu 10.04 LTS, kernel 2.6.28-16-generic
uuid		fe7a46c0-ace7-49cd-92e2-aac1aed53e9b
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=fe7a46c0-ace7-49cd-92e2-aac1aed53e9b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-16-generic
quiet

title		Ubuntu 10.04 LTS, kernel 2.6.28-16-generic (recovery mode)
uuid		fe7a46c0-ace7-49cd-92e2-aac1aed53e9b
kernel		/boot/vmlinuz-2.6.28-16-generic root=UUID=fe7a46c0-ace7-49cd-92e2-aac1aed53e9b ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 10.04 LTS, memtest86+
uuid		fe7a46c0-ace7-49cd-92e2-aac1aed53e9b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Vista (loader)
rootnoverify	(hd0,2)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=fe7a46c0-ace7-49cd-92e2-aac1aed53e9b /               ext3    relatime,errors=remount-ro 0       1
# /home was /dev/sda7
UUID=0c35e852-9dd1-4000-830c-0dfa9abdecc3 /home		  ext4	  defaults        0       2 
# swap was on /dev/sda6 during installation
UUID=7d82db34-dbc6-4d4c-9801-ecb70f9c1a4a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /home was /dev/sda7

=================== sda5: Location of files loaded by Grub: ===================


  76.4GB: boot/grub/core.img
  76.4GB: boot/grub/menu.lst
  77.8GB: boot/grub/stage2
  76.4GB: boot/initrd.img-2.6.28-16-generic
  76.4GB: boot/initrd.img-2.6.31-10-rt
  76.4GB: boot/initrd.img-2.6.31-21-generic
  76.4GB: boot/initrd.img-2.6.32-22-generic
  77.8GB: boot/vmlinuz-2.6.28-16-generic
  76.3GB: boot/vmlinuz-2.6.31-10-rt
  76.4GB: boot/vmlinuz-2.6.31-21-generic
  76.3GB: boot/vmlinuz-2.6.32-22-generic
  76.4GB: initrd.img
  76.4GB: initrd.img.old
  76.3GB: vmlinuz
  76.3GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 

```

---

### Post by Factran on 2010-09-12
On section "Drive/Partition Info:", I see that "/dev/sda3" is bootable.
My boot partition is /dev/sda5.
How do I change it ?

---

### Post by drs305 on 2010-09-12
Edit:

I have created a HOWTO on the procedure below. Please refer to that thread if you want to use the chroot method described below.
[HOWTO: Purge and Reinstall Grub 2 from the Live CD ]("http://ubuntuforums.org/showthread.php?t=1581099")

> **Factran said:**
> On section "Drive/Partition Info:", I see that "/dev/sda3" is bootable.
My boot partition is /dev/sda5.
How do I change it ?

That boot flag is only used by Windows - it doesn't affect your Linux install.

You are running Lucid but appear to still have Grub legacy. Unless you have a reason for keeping Grub legacy, I'd recommend upgrading to Grub 2 - especially since you need to fix your system anyway. If you have strong feelings about keeping Grub legacy, don't feel pressure to upgrade.

We'll do this from the LiveCD, so it will involve 'chroot-ing' into your actual installation. Otherwise, the commands would not act on your real install but on the LiveCD files.

1. Boot to the LiveCD Desktop and open a terminal (Applications, Accessories, Terminal).

A note about copying: Use the copy function to copy these commands. It's easier and more accurate. To paste into a linux terminal, use CTRL-*SHIFT*-V. So copy from this post with your standard CTRL-C, but paste into a terminal with CTRL-SHIFT-V. *Even easier, highlight the command(s) with your mouse, then click in the terminal with your middle mouse button!*

1. Chroot into your real system. The following set of commands will mount the necessary system files to allow the chroot and place you in a terminal where the commands will work on your real installation. Your prompt should include "root", which indicates you are in the chroot environment. 

```

sudo mount /dev/[COLOR="DarkRed"]**sda5**[/COLOR] /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo chroot /mnt

``` 
[LIST]
[*]If you get an error message about not finding "resolv.conf", run this command:
[*]```

sudo mount /dev/[COLOR="DarkRed"]**sda5**[/COLOR] /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo chroot /mnt

```
[/LIST]

Run the first command below to ensure you have an Internet connection and will be able to retrieve the necessary Grub packages. *If the first command fails, do not run the other commands as you may not be able to download the grub packages for installation!*

```

apt-get update   [COLOR="Red"]# If this command doesn't work, do not proceed.[/COLOR]
apt-get purge grub grub-pc grub-common

``` 
This will remove grub, grub-pc (Grub2, if parts of it are installed) and grub-common. You will get a warning during the install about removing the bootloader. TAB to highlight "OK" and press ENTER.  
Next, reinstall the grub packages:
```
apt-get install grub-common grub-pc
``` 
You will be given the opportunity to add extra kernel options to the kernel line. If you don't know, you probably don't need them ;  TAB to highlight "OK" and press ENTER. 

When presented with the device option, highlight **[COLOR="DarkRed"]sda[/COLOR]**. Make sure **[COLOR="DarkRed"]sda[/COLOR]** has an asterisk next to it. If it doesn't, highlight it and press the SPACE bar to select it. TAB to "OK" and press ENTER. When it has finishing the installation, you should have Grub2 installed; continue below.

The last command in the chroot environment is to update grub. This command shouldn't be necessary, but it won't hurt to update Grub once more before exiting.  
```
 
update-grub 

``` 

Exit the chroot environment: 
```
exit
``` 
If you have successfully exited chroot, the terminal prompt should return to the one you normally see.
Unmount what you previously mounted: 
```

sudo umount /mnt/dev/pts && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt/dev && sudo umount /dev/**[COLOR="DarkRed"]sda5[/COLOR]**

``` 
Reboot your system.

If you have any questions, just ask.

---

### Post by Factran on 2010-09-12
That worked. Flawlessly.
Impressive !
I wish this post will rank high in google for reference !

May I suggest you change the 
```
purge grub grub-pc grub-common
```
by
```
apt-get purge grub grub-pc grub-common
```
?

Thanks a lot !!

---

### Post by drs305 on 2010-09-12
Change made - thanks. I normally just have the user purge grub-common, which would automatically purge grub-pc at the same time. I didn't follow my own advice and typed when I should have copied. 

Happy Ubuntu-ing!  :-)

---

### Post by BornTwisted on 2010-09-30
Thanks for writing that up drs305 it's much appreciated :)

The resinstall of grub using your instructions worked flawlessly after a failed install that left me with a flashing white underscore on boot.

> **drs305 said:**
> Edit:

I have created a HOWTO on the procedure below. Please refer to that thread if you want to use the chroot method described below.
[HOWTO: Purge and Reinstall Grub 2 from the Live CD ]("http://ubuntuforums.org/showthread.php?t=1581099")


---

