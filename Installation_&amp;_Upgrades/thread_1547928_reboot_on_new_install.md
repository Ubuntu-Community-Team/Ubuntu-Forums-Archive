---
title: "reboot on new install"
date: 2010-08-07
forum: Installation &amp; Upgrades
---

### Post by jrev on 2010-08-07
I installed the Debian Lenny LXDE on an eeepc Asus 900. from an auxiliary CD reader connected to the USB socket.
The installation completed without much problem on the second (sdb) disk
At reboot I got the message :

> root (hd1.1)
file system type unknown, partition type 0x5
kernel /boot/vmlinuz 2.6.26-2-686 root= /dev/sdb1 ro single
error 17 cannot mount  selected partition

Any clue  ? 

Thanks

---

### Post by presence1960 on 2010-08-07
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by jrev on 2010-08-08
```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.

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
    Operating System:  
    Boot files/dirs:   

sdd: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders, total 7880544 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc7702502

Partition  Boot         Start           End          Size  Id System



Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders, total 15761088 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0005932e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     9,349,829     9,349,767  83 Linux
/dev/sdb2           9,349,830    15,759,764     6,409,935   5 Extended
/dev/sdb5           9,349,893    10,265,534       915,642  82 Linux swap / Solaris
/dev/sdb6          10,265,598    15,759,764     5,494,167  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sdb1        256a381c-d74e-4b72-a9b9-15c78f8690b0   ext3                                     
/dev/sdb5                                               swap                                     
/dev/sdb6        9ac3ff11-beb4-4eaf-a749-35f631aae29e   ext3                                     
/dev/sdd         C062-D347                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/scd0        /live/image              iso9660    (ro,noatime)
/dev/sdd         /media/disk              vfat       (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077)
/dev/sdb1        /media/disk-1            ext3       (rw,nosuid,nodev,uhelper=hal)


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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

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
# kopt=root=/dev/sdb1 ro

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

title		Debian GNU/Linux, kernel 2.6.26-2-686
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.26-2-686 root=/dev/sdb1 ro quiet
initrd		/boot/initrd.img-2.6.26-2-686

title		Debian GNU/Linux, kernel 2.6.26-2-686 (single-user mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.26-2-686 root=/dev/sdb1 ro single
initrd		/boot/initrd.img-2.6.26-2-686

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb1       /               ext3    errors=remount-ro 0       1
/dev/sdb6       /home           ext3    defaults        0       2
/dev/sdb5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

=================== sdb1: Location of files loaded by Grub: ===================


   1.6GB: boot/grub/menu.lst
   1.6GB: boot/grub/stage2
   1.1GB: boot/initrd.img-2.6.26-2-686
   1.0GB: boot/initrd.img-2.6.26-2-686.bak
   1.1GB: boot/vmlinuz-2.6.26-2-686
   1.1GB: initrd.img
   1.1GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdc 
```
What should I do now : reinstall the Debian ?

---

### Post by presence1960 on 2010-08-08
Boot the Debian Live CD to desktop. Open a terminal and run gksu nautilus (or whatever your file manager is. Navigate to the menu.lst file on sdb and open the menu.lst file on sdb. Find this:

```
## ## End Default Options ##

title		Debian GNU/Linux, kernel 2.6.26-2-686
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.26-2-686 root=/dev/sdb1 ro quiet
initrd		/boot/initrd.img-2.6.26-2-686

title		Debian GNU/Linux, kernel 2.6.26-2-686 (single-user mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.26-2-686 root=/dev/sdb1 ro single
initrd		/boot/initrd.img-2.6.26-2-686
```

Change it to:

```
## ## End Default Options ##

title		Debian GNU/Linux, kernel 2.6.26-2-686
root		[COLOR="Red"](hd1,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.26-2-686 root=/dev/sdb1 ro quiet
initrd		/boot/initrd.img-2.6.26-2-686

title		Debian GNU/Linux, kernel 2.6.26-2-686 (single-user mode)
root		[COLOR="Red"](hd1,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.26-2-686 root=/dev/sdb1 ro single
initrd		/boot/initrd.img-2.6.26-2-686
```

Click Save on toolbar and reboot without Live CD.

If the above does not work try this method which is more work:

I would check in BIOS and make sure the sdb disk is set to boot first. From the small size of your hard disks I would say you have IDE hard disks and you may have to switch the master/slave connections in order to switch the order of the hard disks boot if you can't do so in BIOS.

Once you have sdb booting first try to boot and see what happens. if it doesn't work then you will need to reinstall GRUB Legacy 0.97 to the MBR of sdb. I am not familiar with debian but I will assume it is similar to ubuntu.

Boot off the debian live cd and boot to the desktop. Open a terminal and run this:

1. Type sudo grub. Should get text of which last line is grub>
2. Type "find /boot/grub/stage1". You'll get a response like "(hd0,0)". 
   Use whatever your computer spits out for the following lines.
3. Type "root (hd0,0)"
4. Type "setup (hd0)", to install GRUB to MBR
5. Quit grub by typing "quit".
6. Reboot and remove the bootable CD.

Before doing # 6 above open another terminal and run gksu nautilus (or whatever your file manager is on debian). Open the menu.lst file and locate this:

```
## ## End Default Options ##

title		Debian GNU/Linux, kernel 2.6.26-2-686
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.26-2-686 root=/dev/sdb1 ro quiet
initrd		/boot/initrd.img-2.6.26-2-686

title		Debian GNU/Linux, kernel 2.6.26-2-686 (single-user mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.26-2-686 root=/dev/sdb1 ro single
initrd		/boot/initrd.img-2.6.26-2-686
```

Change it to this:

```
## ## End Default Options ##

title		Debian GNU/Linux, kernel 2.6.26-2-686
root		[COLOR="Red"](hd0,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.26-2-686 root=/dev/sdb1 ro quiet
initrd		/boot/initrd.img-2.6.26-2-686

title		Debian GNU/Linux, kernel 2.6.26-2-686 (single-user mode)
root		[COLOR="Red"](hd0,0)[/COLOR]
kernel		/boot/vmlinuz-2.6.26-2-686 root=/dev/sdb1 ro single
initrd		/boot/initrd.img-2.6.26-2-686
```

Click Save on toolbar. Now reboot without the Live CD.


Either method will work. Personally I prefer the second method because in my experience with GRUB Legacy it is more reliable to have GRUB on the MBR of the disk which contains the linux install you want to boot. But this is not necessary.

---

### Post by jrev on 2010-08-08
excellent answer.
Many thanks for the trick

in fact it is (hd1.0) cause I installed the system on the second drive of the eeepc (which is bigger than (hd0.)

---

### Post by presence1960 on 2010-08-09
> **jrev said:**
> excellent answer.
Many thanks for the trick

in fact it is (hd1.0) cause I installed the system on the second drive of the eeepc (which is bigger than (hd0.)

You are welcome. 

With legacy GRUB the order of the disks in GRUB's menu.lst is not determined by how the OS reads the disk order but rather by the hard disk boot order as it is set up in BIOS. So if you keep sdb second in the BIOS hard disk order it is (hd1,0) in menu.lst. But if you make sdb first in the hard disk boot order in BIOS it then becomes (hd0,0) in menu.lst

This has caused more than a few people to be confused when using Legacy GRUB. GRUB 2 has eliminated that problem.

---

