---
title: "Desperate: Upgrade from 10.4 64-bit to 10.10 - wont boot from raid"
date: 2010-12-02
forum: Installation &amp; Upgrades
---

### Post by Spyd on 2010-12-02
Hello Everyone, I am stumpped. 

Yesterday I upgraded my Dell T3500 from lucid64 to maverick64.

The system cannot boot the current image becuase it gives up waiting for root device. 
it gives something like:
```

---udevd-work[175]: '/sbin/modprobe -bv pci: v00008086d00002822sv00001028s00000293bc01sc04i00' unexpected exit with status 0x0009
ALRT! /dev/mapper/isw_bbfcjjefaj_ARRAY01 does not exist. dropping to a shell!


```

at which point it drops to busybox at the (initramfs) prompt.

I cannot boot  this kernel in either normal or recovery mode (ubuntu 10.10, Kernel 2.6.35-23-generic)

however, if I select the previous kernel in grub, (2.6.32-26) it will boot fine. This is my main production machine and it hosts my Project Management software for my team. I could use any advice or tips or any troubleshooting help I can get. 

I seem to come only here to have my life saved and this forum always saves me!
Thanks so much in advance....
Franco

---

### Post by ronparent on 2010-12-02
I would suspect that the upgrade did not complete properly. If you would, please go to this site and download the boot info script: [http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055)
Run the script on your desk top and post the results here.

The code you posted seems to indicate you are using a 'fakeraid'. That should not be material since 10.10 usually upgrades on a raid fine (I've done it multiple times). The results.txt from the boot info script should give a reasonably clear picture of why the loading stops at that message.

---

### Post by Spyd on 2010-12-03
> **ronparent said:**
> I would suspect that the upgrade did not complete properly. If you would, please go to this site and download the boot info script: [http://sourceforge.net/project/platformdownload.php?group_id=250055](http://sourceforge.net/project/platformdownload.php?group_id=250055)
Run the script on your desk top and post the results here.

The code you posted seems to indicate you are using a 'fakeraid'. That should not be material since 10.10 usually upgrades on a raid fine (I've done it multiple times). The results.txt from the boot info script should give a reasonably clear picture of why the loading stops at that message.

Thanks so much. here are the results: :popcorn:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/mapper/isw_bbfcjjefaj_ARRAY0 and 
    looks on the same drive in partition #1 for /boot/grub/stage2 and 
    /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_bbfcjjefaj_ARRAY01: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

isw_bbfcjjefaj_ARRAY02: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

isw_bbfcjjefaj_ARRAY05: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   599,738,579   599,738,517  83 Linux
/dev/sda2         599,738,580   625,137,344    25,398,765   5 Extended
/dev/sda5         599,738,643   625,137,344    25,398,702  82 Linux swap / Solaris


Drive: isw_bbfcjjefaj_ARRAY0 ___________________ _____________________________________________________

Disk /dev/mapper/isw_bbfcjjefaj_ARRAY0: 320.1 GB, 320070483968 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625137664 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/isw_bbfcjjefaj_ARRAY01                 63   599,738,579   599,738,517  83 Linux
/dev/mapper/isw_bbfcjjefaj_ARRAY02        599,738,580   625,137,344    25,398,765   5 Extended
/dev/mapper/isw_bbfcjjefaj_ARRAY05        599,738,643   625,137,344    25,398,702  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/isw_bbfcjjefaj_ARRAY01 ee0bd41b-0800-4ed9-baf0-a88d3a012648   ext4                                     
/dev/mapper/isw_bbfcjjefaj_ARRAY05 ed57e974-e90c-476c-9d0e-71ca1e9f2ee9   swap                                     
/dev/mapper/isw_bbfcjjefaj_ARRAY0: PTTYPE="dos" 
/dev/sda                                                isw_raid_member                               
/dev/sdb                                                isw_raid_member                               
error: /dev/mapper/isw_bbfcjjefaj_ARRAY02: No such file or directory
error: /dev/sda1: No such file or directory
error: /dev/sda2: No such file or directory
error: /dev/sda5: No such file or directory
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
isw_bbfcjjefaj_ARRAY0
isw_bbfcjjefaj_ARRAY01
isw_bbfcjjefaj_ARRAY05

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/mapper/isw_bbfcjjefaj_ARRAY01 /                        ext4       (rw,errors=remount-ro,commit=0)


================== isw_bbfcjjefaj_ARRAY01/boot/grub/menu.lst: ==================

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
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=/dev/mapper/isw_bbfcjjefaj_ARRAY01 ro

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

title		Ubuntu 10.10, kernel 2.6.35-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.35-23-generic root=/dev/mapper/isw_bbfcjjefaj_ARRAY01 ro quiet splash 
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.35-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.35-23-generic root=/dev/mapper/isw_bbfcjjefaj_ARRAY01 ro  single
initrd		/boot/initrd.img-2.6.35-23-generic

title		Ubuntu 10.10, kernel 2.6.32-26-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-26-generic root=/dev/mapper/isw_bbfcjjefaj_ARRAY01 ro quiet splash 
initrd		/boot/initrd.img-2.6.32-26-generic

title		Ubuntu 10.10, kernel 2.6.32-26-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.32-26-generic root=/dev/mapper/isw_bbfcjjefaj_ARRAY01 ro  single
initrd		/boot/initrd.img-2.6.32-26-generic

title		Ubuntu 10.10, kernel 2.6.31-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.31-22-generic root=/dev/mapper/isw_bbfcjjefaj_ARRAY01 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-22-generic

title		Ubuntu 10.10, kernel 2.6.31-22-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.31-22-generic root=/dev/mapper/isw_bbfcjjefaj_ARRAY01 ro  single
initrd		/boot/initrd.img-2.6.31-22-generic

title		Ubuntu 10.10, kernel 2.6.31-20-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.31-20-generic root=/dev/mapper/isw_bbfcjjefaj_ARRAY01 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 10.10, kernel 2.6.31-20-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.31-20-generic root=/dev/mapper/isw_bbfcjjefaj_ARRAY01 ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 10.10, kernel 2.6.31-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.31-14-generic root=/dev/mapper/isw_bbfcjjefaj_ARRAY01 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 10.10, kernel 2.6.31-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.31-14-generic root=/dev/mapper/isw_bbfcjjefaj_ARRAY01 ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 10.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

====================== isw_bbfcjjefaj_ARRAY01/etc/fstab: ======================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/isw_bbfcjjefaj_ARRAY01 /               ext4    errors=remount-ro 0       1
/dev/mapper/isw_bbfcjjefaj_ARRAY05 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

========== isw_bbfcjjefaj_ARRAY01: Location of files loaded by Grub: ==========


   3.0GB: boot/grub/menu.lst
    .3GB: boot/grub/stage2
   1.0GB: boot/initrd.img-2.6.31-14-generic
   1.3GB: boot/initrd.img-2.6.31-20-generic
  36.3GB: boot/initrd.img-2.6.31-22-generic
 234.9GB: boot/initrd.img-2.6.32-26-generic
 234.8GB: boot/initrd.img-2.6.35-23-generic
    .4GB: boot/vmlinuz-2.6.31-14-generic
    .6GB: boot/vmlinuz-2.6.31-20-generic
  11.3GB: boot/vmlinuz-2.6.31-22-generic
  35.8GB: boot/vmlinuz-2.6.32-26-generic
  36.0GB: boot/vmlinuz-2.6.35-23-generic
 234.8GB: initrd.img
 234.9GB: initrd.img.old
  36.0GB: vmlinuz
  35.8GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda5


Unknown BootLoader  on isw_bbfcjjefaj_ARRAY02



=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/sda5: No such file or directory
hexdump: /dev/mapper/isw_bbfcjjefaj_ARRAY02: No such file or directory
hexdump: /dev/mapper/isw_bbfcjjefaj_ARRAY02: No such file or directory

```

---

### Post by ronparent on 2010-12-03
That is quite informative.
> => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
This is not material because the boot loader for a fakeRAID0 has to be on the raid for a system mounted and booted from the raid. You are incidently booting from the old grub - we should fix that. 

> => Grub 0.97 is installed in the MBR of /dev/mapper/isw_bbfcjjefaj_ARRAY0 and 
    looks on the same drive in partition #1 for /boot/grub/stage2 and 
    /boot/grub/menu.lst.
This is the correct grub 1 installation for your setup - and it does seem to work properly for booting the Ubuntu 10.10, kernel 2.6.35-23-generic.  

> error: /dev/mapper/isw_bbfcjjefaj_ARRAY02
If ARRAY2 is the extended partition this message is probably not material! Then ARRAY5 would be the first partition in the extended. So despite my previous statement I don't have a clear picture why loading stops here!

This is just a hunch but why don't we try to install grub 2? Ususally a simple two step process handles this from the 10.10 live cd like in this reference: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

In your case you would mount the raid partition you upgraded 10.10 to.
```
sudo mount /dev/mapper/isw_bbfcjjefaj_ARRAY01 /mnt
```

You would then install grub to the mounted filesystem and write a new grub 2 boot loader to the overall boot array MBR.
```
sudo grub-install --root-directory=/mnt/ /dev/mapper/isw_bbfcjjefaj_ARRAY0
```

If everything was done properly and some odd ball system artifact doesn't intervene the system will probably boot properly to the new kernel. Let us know how it comes out. Good luck.

---

### Post by Spyd on 2010-12-03
Wow - thanks, Ok, so I mounted then installed grub and got:


```
Probing devices to guess BIOS drives. This may take a long time.
/dev/mapper/../dm-1 does not have any corresponding BIOS drive.

```

I will reboot and post the results,
BRB

---

### Post by Spyd on 2010-12-03
@ronparent: Ok, this did not solve the problem. exact same message as in OP.

just to clarify:

1) 2.6.35-23-generic will not boot
2) 2.6.32-26-generic does boot
3) I ran the boot script in 2.6.32-26-generic
4) I ran the suggested commands in 2.6.32-26-generic
5) Result is : FAILED - got same error as 1st post.
6) after above, I can STILL boot 10.10 using 2.6.32-26-generic 

Thanks for trying. Any other suggestions, anyone?

Thanks a million
Franco

---

### Post by ronparent on 2010-12-03
If you can still boot 2.6.32-26 you are actually booting the 10.04 release probably in a hybrid environment. You have to try to fix the upgrade. Booted to the 10.04 kernel try running 'sudo dpkg --configure -a' in a terminal. Post the results.

I'm pretty sure your partition table is ok or the 2.6.32-23 wouldn't boot. Booting on that kernel you should verify your raid by installing kpartx (sudo apt-get kpartx) and thereafter running gparted. Gparted will show your raid drive and partitions (with unallocated sda and sdb as well).

---

### Post by Spyd on 2010-12-06
> **ronparent said:**
> If you can still boot 2.6.32-26 you are actually booting the 10.04 release probably in a hybrid environment. You have to try to fix the upgrade. Booted to the 10.04 kernel try running 'sudo dpkg --configure -a' in a terminal. Post the results.
This did nothing.:shock:


> **ronparent said:**
> 
I'm pretty sure your partition table is ok or the 2.6.32-23 wouldn't boot. Booting on that kernel you should verify your raid by installing kpartx (sudo apt-get kpartx) and thereafter running gparted. Gparted will show your raid drive and partitions (with unallocated sda and sdb as well).
This is already installed :D but it said:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
kpartx is already the newest version.
kpartx set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.


```

Gparted was *NOT* installed :shock:, but I installed it and ran it and it shows me: (see attached)

---

### Post by ronparent on 2010-12-06
It looks like you are getting close to where you want to be. Now, booting to the 10.04, open a terminal. Enter these commands in sequence:

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

Hopefully this will cleanup and leave the 10.04 in upgradeable condition where you can intiate the upgrade again. Let us know if this gets you anywhere.:)

---

### Post by Spyd on 2010-12-06
@ronparent Thanks for trying to help, I really appreciate this, here is the result: 
```

.
.
.
Hit http://ca.archive.ubuntu.com maverick-updates/universe amd64 Packages
Hit http://security.ubuntu.com maverick-security/universe Sources
Hit http://security.ubuntu.com maverick-security/main amd64 Packages
Hit http://security.ubuntu.com maverick-security/multiverse amd64 Packages
Hit http://security.ubuntu.com maverick-security/restricted amd64 Packages
Hit http://security.ubuntu.com maverick-security/universe amd64 Packages
Reading package lists... Done
franco@sm53-fed0239:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

some other info:
```
uname -a
Linux sm53-fed0239 2.6.32-26-generic #48-Ubuntu SMP Wed Nov 24 10:14:11 UTC 2010 x86_64 GNU/Linux

```

```
cat /etc/issue
Ubuntu 10.10 \n \l

```


Now rebooting to try the latest kernel. will post results after reboot.

Ok, I am now booting into a perfect 10.10 but the second last kernel. the newest kernel is still giving me the exact same error as the OP. Is there some way to blow away that kernel and reupgrade to it?

---

### Post by Spyd on 2010-12-06
Perhaps I should uninstall the new kernel via synaptic and then reinstall?
Edit: Reinstalled the 35-23 kernel images, still cant boot it, exact same errors.

---

