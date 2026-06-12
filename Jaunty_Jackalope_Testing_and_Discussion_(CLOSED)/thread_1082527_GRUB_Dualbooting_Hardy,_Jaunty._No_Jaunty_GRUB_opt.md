---
title: "GRUB: Dualbooting Hardy, Jaunty. No Jaunty GRUB option [Picture Included]"
date: 2009-02-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by justin_c18 on 2009-02-27
I just manually formatted my hard drive, my partitions goes as follows

       /dev/sda1 linux-swap 1.00GB
HARDY  /dev/sda2 ext3       36.78GB   boot flag
Jaunty /dev/sda3 ext3       36.76GB

/dev/sda2 has Hardy on it. Since it's flagged as the boot partition, it can boot. But, what I'm having problems with is Jaunty. Jaunty isn't in the GRUB menu. I can't boot into it.

What can I do to make the partition show in the grub menu so I can have an option to boot it if I want to? I'm not sure if I need to set the swap up either with that partition either. But I'd like to have both partitions use the one swap.

So, my questions are as follows:

How do I get Jaunty in the GRUB meny to boot?
If my swap isn't setup for Jaunty, how can I set it up?

GParted picture below

Thanks in advance.
Justin

[IMG]http://farm4.static.flickr.com/3385/3314694159_0165604337_o.png[/IMG]

---

### Post by caljohnsmith on 2009-02-27
Is your Jaunty partition actually ext4 instead of ext3 since that is what Jaunty uses by default, or did you deliberately choose ext3 when you installed Jaunty? If it is ext4, you won't be able to boot it using Hardy's Grub. In order to get a clearer picture of your setup, how about booting your Jaunty Live CD, download the **Boot Info Script** to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by justin_c18 on 2009-02-27
> **caljohnsmith said:**
> Is your Jaunty partition actually ext4 instead of ext3 since that is what Jaunty uses by default, or did you deliberately choose ext3 when you installed Jaunty? If it is ext4, you won't be able to boot it using Hardy's Grub. In order to get a clearer picture of your setup, how about booting your Jaunty Live CD, download the **Boot Info Script** to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

I'm pretty certain I did choose ext4 for my Jaunty installation. 

Here's the output of the script you told me to run.

```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.04.1
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu jaunty (development 
                       branch)
    Boot files/dirs:   /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2cd6e240

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     2,104,514     2,104,452  82 Linux swap / Solaris
/dev/sda2    *      2,104,515    79,200,449    77,095,935  83 Linux
/dev/sda3          79,200,450   156,296,384    77,095,935  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="857cd650-3fcc-4cf8-8b50-4bbbdaee26a2" TYPE="swap" 
/dev/sda2: LABEL="Hardy" UUID="6ccf4b83-d7ad-472d-a32f-3b70e3f74c77" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="fbd49655-279f-4144-a1c5-22d3d7e78551" TYPE="ext4" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-8-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-8-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


=========================== sda2/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=6ccf4b83-d7ad-472d-a32f-3b70e3f74c77 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6ccf4b83-d7ad-472d-a32f-3b70e3f74c77 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6ccf4b83-d7ad-472d-a32f-3b70e3f74c77 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=6ccf4b83-d7ad-472d-a32f-3b70e3f74c77 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda1
UUID=857cd650-3fcc-4cf8-8b50-4bbbdaee26a2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  28.5GB: boot/grub/menu.lst
  28.5GB: boot/grub/stage2
  28.4GB: boot/initrd.img-2.6.24-19-generic
  28.4GB: boot/initrd.img-2.6.24-19-generic.bak
  28.5GB: boot/vmlinuz-2.6.24-19-generic
  28.4GB: initrd.img
  28.5GB: vmlinuz

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=fbd49655-279f-4144-a1c5-22d3d7e78551 /               ext4    relatime,errors=remount-ro 0       1
# none was on /dev/sda1 during installation
UUID=857cd650-3fcc-4cf8-8b50-4bbbdaee26a2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda3: Location of files loaded by Grub: ===================


  42.3GB: boot/initrd.img-2.6.28-8-generic
  42.4GB: boot/vmlinuz-2.6.28-8-generic
  42.3GB: initrd.img
  42.4GB: vmlinuz

```

Since the partition is ext4, will I be able to still dualboot, or will I have to reformat it again into ext3?

Thanks a lot.
Justin

---

### Post by justin_c18 on 2009-02-28
ping

---

### Post by caljohnsmith on 2009-02-28
Justin, please be patient and respect the forum rules of not bumping your thread sooner that every 24 hours. I think we are on different time zones, and that's why I haven't been able to get back to you sooner. Based on the results of the script, it looks like you installed Jaunty without Grub, is that true? If you want to use ext4 for the Jaunty partition, you'll need to use Jaunty's version of Grub to boot both Jaunty and Hardy, because Hardy's version of Grub can't deal with ext4 partitions. I believe it would be possible to manually update Grub's stage1, stage1.5, and stage2 file in your Hardy install so you could use Hardy to boot Jaunty, but if your Jaunty install is new, I think it would be better to just reinstall Jaunty with Grub and use Jaunty to boot Hardy. Let me know how that goes or if you run into problems.

---

### Post by justin_c18 on 2009-02-28
> **caljohnsmith said:**
> Justin, please be patient and respect the forum rules of not bumping your thread sooner that every 24 hours. I think we are on different time zones, and that's why I haven't been able to get back to you sooner. Based on the results of the script, it looks like you installed Jaunty without Grub, is that true? If you want to use ext4 for the Jaunty partition, you'll need to use Jaunty's version of Grub to boot both Jaunty and Hardy, because Hardy's version of Grub can't deal with ext4 partitions. I believe it would be possible to manually update Grub's stage1, stage1.5, and stage2 file in your Hardy install so you could use Hardy to boot Jaunty, but if your Jaunty install is new, I think it would be better to just reinstall Jaunty with Grub and use Jaunty to boot Hardy. Let me know how that goes or if you run into problems.

Sorry about that, I won't do it anymore and thanks for the info. I'm reinstalling Jaunty right now, with the new bootloader. I thought I might have messed up the HDD's booting process. Anyway, I guess not.

Thanks, and hopefully the installation goes well.
Have a good day if I I'm not back here trying to explain myself once again. :)
Justin

---

### Post by justin_c18 on 2009-02-28
Everything is working fine it looks like. Even my swap is detected and working I think.

Thanks for the help dude, much appreciated.

---

### Post by caljohnsmith on 2009-02-28
Glad that everything is working OK now; cheers and enjoy your dual-boot Ubuntu setup. :)

---

