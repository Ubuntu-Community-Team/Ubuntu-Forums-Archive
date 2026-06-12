---
title: "configure grub for 3 hdds with 3 operating systems"
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by frenchcr on 2009-12-18
i have three harddrives

one with xp
one with ubuntu 9.10
one with w7

I need to fix grub as i can boot into ubuntu and w7 but not xp.

please advise...heres a copy of my menu.lst..

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)

# splashimage (hd0,0)/boot/grub/images/filename.tar.gz

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

title Windows 7
root (hd2,0)
makeactive
chainloader +1

title Windows XP
root (hd1,0)
makeactive
chainloader +1

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
# kopt=root=UUID=12abde31-38fe-4156-b693-95344b1b56ef ro

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

title		Ubuntu 9.10, kernel 2.6.31-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=12abde31-38fe-4156-b693-95344b1b56ef ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=12abde31-38fe-4156-b693-95344b1b56ef ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


```

---

### Post by darkod on 2009-12-18
I am not too experienced with dual booting two win versions but from what I've heard windows combines the bootloaders. Maybe that's the reason why you can't seem to boot XP. Win7 should have combined both boot files and choosing 7 should actually offer 7 and XP.
To resolve the dilemma you can also download the script in my signature, move it on desktop for example, and run it with:
sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file with lots of info about your boot process and boot files. Take a look and if you want to copy the top section here, it includes the boot files. It will show where your 7 and XP boot files are.

---

### Post by oldfred on 2009-12-18
Run the boot info script that darko suggests so we can see your setup. We can see if the boot files are there and partition numbers to use.

I for a short time had a fourth drive with an old install of windows. Grub automatically added the map commands as windows has to think it is the first drive even when it is not.

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdd1
title        Microsoft Windows XP Professional
rootnoverify    (hd3,0)
savedefault
map        (hd0) (hd3)
map        (hd3) (hd0)
chainloader    +1

---

### Post by frenchcr on 2009-12-19
> **darkod said:**
> I am not too experienced with dual booting two win versions but from what I've heard windows combines the bootloaders. Maybe that's the reason why you can't seem to boot XP. Win7 should have combined both boot files and choosing 7 should actually offer 7 and XP.
To resolve the dilemma you can also download the script in my signature, move it on desktop for example, and run it with:
sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file with lots of info about your boot process and boot files. Take a look and if you want to copy the top section here, it includes the boot files. It will show where your 7 and XP boot files are.

Nice script, heres the output...

```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004a1b0

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   476,230,859   476,230,797  83 Linux
/dev/sda2         476,230,860   488,392,064    12,161,205   5 Extended
/dev/sda5         476,230,923   488,392,064    12,161,142  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5b785b78

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   488,375,999   488,375,937   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8a8a0c39

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sdc2             206,848   976,771,071   976,564,224   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
16 heads, 63 sectors/track, 1938021 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd9379a69

Partition  Boot         Start           End          Size  Id System

/dev/sdd1    *             63 1,953,522,143 1,953,522,081   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="12abde31-38fe-4156-b693-95344b1b56ef" TYPE="ext3" 
/dev/sda5: UUID="024b61f8-1f16-4448-a490-4269aeece5ab" TYPE="swap" 
/dev/sdb1: UUID="3654448954444DB5" LABEL="Local Disk" TYPE="ntfs" 
/dev/sdc1: UUID="A2CC2DC4CC2D9397" LABEL="System Reserved" TYPE="ntfs" 
/dev/sdc2: UUID="1C4C2F574C2F2B4A" TYPE="ntfs" 
/dev/sdd1: UUID="0020F53520F53270" LABEL="Storage" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/frenchcr/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=frenchcr)


=========================== sda1/boot/grub/menu.lst: ===========================

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)

# splashimage (hd0,0)/boot/grub/images/filename.tar.gz

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

title Windows 7
root (hd2,0)
makeactive
chainloader +1

title Windows XP
root (hd3,0)
makeactive
chainloader +1

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
# kopt=root=UUID=12abde31-38fe-4156-b693-95344b1b56ef ro

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

title		Ubuntu 9.10, kernel 2.6.31-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=12abde31-38fe-4156-b693-95344b1b56ef ro quiet splash 
initrd		/boot/initrd.img-2.6.31-14-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.31-14-generic root=UUID=12abde31-38fe-4156-b693-95344b1b56ef ro  single
initrd		/boot/initrd.img-2.6.31-14-generic

title		Ubuntu 9.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST






=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=12abde31-38fe-4156-b693-95344b1b56ef /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda5
UUID=024b61f8-1f16-4448-a490-4269aeece5ab none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto     0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initrd.img-2.6.22-14-generic
    .0GB: boot/initrd.img-2.6.28-15-generic
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-15-generic
    .0GB: boot/vmlinuz-2.6.28-15-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-15-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect /usepmtimer
=======Devices which don't seem to have a corresponding hard drive==============

sde sdf 
```

---

### Post by darkod on 2009-12-19
OK, first, I'm suspecting your XP drive is actually hd1 not hd3. Not to wonder in the dark, open the file /boot/grub/device.map and check to what is /dev/sdb mapped, as hd1 or hd3.

Also, as Fred said, you might need to adjust the XP entry as:

title Windows XP
rootnoverify (hd1,0)
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

If device.map shows that /dev/sdb is hd3, replace hd1 with hd3 in the above. See how it goes.

---

### Post by frenchcr on 2009-12-19
> **darkod said:**
> OK, first, I'm suspecting your XP drive is actually hd1 not hd3. Not to wonder in the dark, open the file /boot/grub/device.map and check to what is /dev/sdb mapped, as hd1 or hd3.

Also, as Fred said, you might need to adjust the XP entry as:

title Windows XP
rootnoverify (hd1,0)
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

If device.map shows that /dev/sdb is hd3, replace hd1 with hd3 in the above. See how it goes.


In device.map its just got... 

(hd0)	/dev/sda

...theres nothing else in there.

---

### Post by darkod on 2009-12-19
Hmmm, as far as I know you should have all your 4 drives mapped as hd0 to hd3 but not always they are in same order corresponding with sda to sdd.
Try it with hd1 anyway, and maybe Fred will jump in to confirm you need to update device.map and how to do it.
You definitely know it's not working with hd3 so try with hd1. If win7 is working with hd2 then it's definitely hd2 for that disk, and hd0 is for ubuntu, that leaves hd1 or hd3 for XP.

---

### Post by oldfred on 2009-12-19
I see XP as sdb1 hd(1,0), Vista as sdc1 hd(2,0) and 7 as sdc2 hd(2,1) but I am not sure that you have all  the windows boot files in each partition. Windows normally installs each additional copy of windows and moves essential files to the partition with the boot flag so when you boot the first windows you can also choose the second.

With different drives I am not as sure. Many install a second windows with the other drive disconnected (which I normally would not recommend) or turn off the boot flag so windows does not see the first install.

When you booted windows before did it give you a choice of all three? You may be able to repair Vista and 7 buy turning off all the boot flags except for the one you want to repair. You should set that drive to first in boot order so when windows installs to the MBR it just rewrites that MBR not your sda grub.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

You can also set flag with gparted. Only one partition can have the boot flag on. (even though it may let you set more then windows will have issues)
   #make a partition active ("makeactive" in grub legacy)
    parttool (hd0,4) boot+

    #remove active flag from a partition
    parttool (hd0,3) boot-

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista Recovery Disc 
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by frenchcr on 2009-12-19
> **darkod said:**
> 
you might need to adjust the XP entry as:

title Windows XP
rootnoverify (hd1,0)
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1



This fixed the problem, i just copied and pasted it over the entry for xp i gave in above post.

Still dont know how it works though :confused:

---

### Post by frenchcr on 2009-12-19
this could be my fault.

one drive is just a storage drive

the other three have ubuntu xp and w7 on them.

i.e. i have 4 drives, just three with os's on them.

...also to answer your query, i installed them on their drives while all other drives were unplugged. its always safer that way. then you just reinstall grub and reconfigure it, but this is not always neccessary depending on the order you do it all in...was this time as you can see. 


thanks for all your help folks...been on two year break from linux and am a bit rusty just now.



> **oldfred said:**
> I see XP as sdb1 hd(1,0), Vista as sdc1 hd(2,0) and 7 as sdc2 hd(2,1) but I am not sure that you have all  the windows boot files in each partition. Windows normally installs each additional copy of windows and moves essential files to the partition with the boot flag so when you boot the first windows you can also choose the second.

With different drives I am not as sure. Many install a second windows with the other drive disconnected (which I normally would not recommend) or turn off the boot flag so windows does not see the first install.

When you booted windows before did it give you a choice of all three? You may be able to repair Vista and 7 buy turning off all the boot flags except for the one you want to repair. You should set that drive to first in boot order so when windows installs to the MBR it just rewrites that MBR not your sda grub.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

You can also set flag with gparted. Only one partition can have the boot flag on. (even though it may let you set more then windows will have issues)
   #make a partition active ("makeactive" in grub legacy)
    parttool (hd0,4) boot+

    #remove active flag from a partition
    parttool (hd0,3) boot-

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista Recovery Disc 
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by darkod on 2009-12-19
> **oldfred said:**
> I see XP as sdb1 hd(1,0), Vista as sdc1 hd(2,0) and 7 as sdc2 hd(2,1) but I am not sure that you have all  the windows boot files in each partition. 

It's OK Fred, sdc1 is only a 200MB boot partition and I guess that's why /bootmgr and /boot/BCD are there. Otherwise it would really seem as if the boot files are split over two partitions.

You don't understand how the XP entry works?
root (hdX,Y) is usualy used for linux, for windows (especially for XP) it's better to use rootnoverify (hdX,Y).
Also the map command is needed for XP because it needs to "think" it's on the first drive (counted from 0 in linux, hence hd0). That's why we are mapping hd0 and hd1 to each other.
And that's it basically.
When you looked in device.map earlier and it had only hd0 /dev/sda I knew you installed the OS with other drives disconnected. That's why it didn't map them. Yes, sometimes it sounds safer like that, but as you saw yourself, it prevents linux detecting other OSs automatically and you had to adjust manually the entries.
Anyway, it's all sorted now and working fine for you.

---

### Post by frenchcr on 2009-12-19
> **darkod said:**
> It's OK Fred, sdc1 is only a 200MB boot partition and I guess that's why /bootmgr and /boot/BCD are there. Otherwise it would really seem as if the boot files are split over two partitions.

You don't understand how the XP entry works?
root (hdX,Y) is usualy used for linux, for windows (especially for XP) it's better to use rootnoverify (hdX,Y).
Also the map command is needed for XP because it needs to "think" it's on the first drive (counted from 0 in linux, hence hd0). That's why we are mapping hd0 and hd1 to each other.
And that's it basically.
When you looked in device.map earlier and it had only hd0 /dev/sda I knew you installed the OS with other drives disconnected. That's why it didn't map them. Yes, sometimes it sounds safer like that, but as you saw yourself, it prevents linux detecting other OSs automatically and you had to adjust manually the entries.
Anyway, it's all sorted now and working fine for you.

;-) thanks Darko, thanks for all your help...a nice clear explanation there, i can see how it works now.

Merry Christmas to you!

---

