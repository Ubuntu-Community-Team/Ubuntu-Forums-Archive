---
title: "How do I repair my filesystem?"
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by wersdaluv on 2007-06-02
I had four partitions; namely my Ubuntu Partition, my PCLinuxOS Partition, my Home Partition, and my Swap Partition.

I deleted my PCLinuxOS Partition and created a new blank partition on the created free space and then, I installed Dream Linux on it and set my Home partition as the same home partition for Dream Linux. 

The installation of  Dream Linux asked me if I wanted to install GRUB and I chose to install GRUB on the root partition and not on the MBR.

When I restarted, I saw my old GRUB menu without Dream Linux as an option. I chose to boot with Ubuntu. After booting, the console said to me that I should manually fix my Filesystem. How do I fix my filesystem and put Dream Linux on the GRUB menu?

**EDIT**

When I first booted Ubuntu right after I installed DreamLinux, after logging in, an error message came out and said that my home partition is lost. When I rebooted, I was lucky that the file system check was forced since it was not checked after it was booted for 33 times. After that, every time I boot my Ubuntu install, this comes out of the terminal
```
 A log is being saved in var/log/fsck/checkfs if that location is writable.
Please repair the filesystem manually.
A maintenance shell will now be started.
bash: no job to control in this shell
bash: groups: command not found
bash: iespipe: command not found
bash: The: command not found
The program apt-get is not currently installed. You can do this by typing apt-get install apt
bash: apt-get: command not found
bash: dircolorsi: command not found
bash: The: command not found
The program apt-get is not currently installed. You can do this by typing apt-get install apt
bash: apt-get: command not found

```
In order for me to start Ubuntu, I will hit "Enter" then press Ctrl+D.

However, whenever I boot DreamLinux, no error comes out. 

I tried fsck using my Ubuntu Feisty Live CD and this is what came out
```
ubuntu@ubuntu:~$ fsck -t ext3 "/media/disk"
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: Is a directory while trying to open /media/disk

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


```

What do I do now?

EDIT AGAIN

I followed the instruction and...

```
ubuntu@ubuntu:~$ sudo e2fsck -b 8193 /dev/hda2
e2fsck 1.40-WIP (14-Nov-2006)
/dev/hda2 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes

e2fsck: Bad magic number in super-block while trying to open /dev/hda2

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>



```

What do I do now?

---

### Post by wersdaluv on 2007-06-02
Also, whenever I boot, after the [loading screen]("http://www.thecodingstudio.com/opensource/linux/screenshots/index.php?linux_distribution_sm=Ubuntu%207.04") (the black screen with the Ubuntu logo and the loading bar (see the second screenshot on the link)), there would be a maintenance shell that would instruct me to run "apt-get install apt", but when I run it, there would be another error.

---

### Post by wersdaluv on 2007-06-02
Here is the error report that come out after the loading screen every time I boot Ubuntu

```
 A log is being saved in var/log/fsck/checkfs if that location is writable.
Please repair the filesystem manually.
A maintenance shell will now be started.
bash: no job to control in this shell
bash: groups: command not found
bash: iespipe: command not found
bash: The: command not found
The program apt-get is not currently installed. You can do this by typing apt-get install apt
bash: apt-get: command not found
bash: dircolorsi: command not found
bash: The: command not found
The program apt-get is not currently installed. You can do this by typing apt-get install apt
bash: apt-get: command not found

```

---

### Post by kevinlyfellow on 2007-06-02
Does your file system work with a livecd?

run fsck on the partition when your using you livecd

---

### Post by confused57 on 2007-06-02
It's usually not advisable to share /home partitions with 2 different distros...some of your Ubuntu configuration files  were probably overwritten by Dreamlinux.  You could install your Dreamlinux grub to the mbr, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
then you "might" be able to boot Dreamlinux...from which you could probably mount your Ubuntu partition(s) & backup any important data.   My guess is that you would probably have to reinstall Ubuntu, I don't know for sure.

Added:  If you want to try doing a filesystem check, wouldn't hurt to try:
[http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem](http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem)
the gparted live cd is an easy way to do this, as described in the link

---

### Post by wersdaluv on 2007-06-02
> **kevinlyfellow said:**
> Does your file system work with a livecd?

run fsck on the partition when your using you livecd

Actually, the odd thing is that, even both Ubuntu and DreamLinux work. There is just an annoying failed filesystem check that will welcome me everytime I boot. I will boot my Feisty live CD and follow your instructions.

---

### Post by wersdaluv on 2007-06-02
> **confused57 said:**
> It's usually not advisable to share /home partitions with 2 different distros...some of your Ubuntu configuration files  were probably overwritten by Dreamlinux.  You could install your Dreamlinux grub to the mbr, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
then you "might" be able to boot Dreamlinux...from which you could probably mount your Ubuntu partition(s) & backup any important data.   My guess is that you would probably have to reinstall Ubuntu, I don't know for sure.

Added:  If you want to try doing a filesystem check, wouldn't hurt to try:
[http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem](http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem)
the gparted live cd is an easy way to do this, as described in the link

I guess no complication was made by the sharing of configuration files because I used different user names for the two distros.

I want to try your suggestion, but unfortunately, I ran out of CDs.

---

### Post by wersdaluv on 2007-06-02
> **kevinlyfellow said:**
> Does your file system work with a livecd?

run fsck on the partition when your using you livecd

I just ran fsck in the terminal and all that came out was
```
ubuntu@ubuntu:~$ fsck
fsck 1.40-WIP (14-Nov-2006)

```

Did I do it right?

---

### Post by kevinlyfellow on 2007-06-02
> **wersdaluv said:**
> I just ran fsck in the terminal and all that came out was
```
ubuntu@ubuntu:~$ fsck
fsck 1.40-WIP (14-Nov-2006)

```

Did I do it right?

```
fsck -t ext3 "mountpoint"
```
where mountpoint is the place where the partition is mounted.

---

### Post by wersdaluv on 2007-06-02
Thanks. 

Here is the output
```
ubuntu@ubuntu:~$ fsck -t ext3 "/media/disk"
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: Is a directory while trying to open /media/disk

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


```

There are instructions, but I choose not to move on because I am not sure of what to do. I do not want to mess up with partitions again.

What do I do now?

---

### Post by kevinlyfellow on 2007-06-02
> **wersdaluv said:**
> Thanks. 

Here is the output
```
ubuntu@ubuntu:~$ fsck -t ext3 "/media/disk"
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: Is a directory while trying to open /media/disk

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


```

There are instructions, but I choose not to move on because I am not sure of what to do. I do not want to mess up with partitions again.

What do I do now?

Smart move ;-).  I dont have a spare partition for me to practice on, so I can't really debug things before I say them. can you read the filesystem just fine?  

Also, are you sure that grub wasn't changed during the install?  I'm also wondering if it isn't something with the UUID

---

### Post by wersdaluv on 2007-06-02
> **kevinlyfellow said:**
> Smart move ;-).  I dont have a spare partition for me to practice on, so I can't really debug things before I say them. can you read the filesystem just fine?  

Also, are you sure that grub wasn't changed during the install?  I'm also wondering if it isn't something with the UUID

I am sorry, but I do not know much technical stuff so I do not really know what you mean by readingthe filesystem just fine. What I do know is that, my old Ubuntu install works fine after I exit the annoying failed filesystem check. Also, my DreamLinux install works fine, and it does not have a failed filesystem check.

As for my GRUB, it still is my old GRUB menu. When I installed DreamLinux, I chose to install its GRUB menu on the root partition only and not on the MBR. Also, I had to edit my old GRUB menu for DreamLinux to come out of the list.

---

### Post by kevinlyfellow on 2007-06-02
You answered my questions :-)  When I said "read the filesystem" I just meant you could look through it.

Can you post the results of the following commands while running Ubuntu? (The ubuntu on your hard drive, not live)
```
cat  /boot/grub/menu.lst
cat /etc/fstab
```

---

### Post by wersdaluv on 2007-06-02
> **kevinlyfellow said:**
> You answered my questions :-)  When I said "read the filesystem" I just meant you could look through it.

Can you post the results of the following commands while running Ubuntu? (The ubuntu on your hard drive, not live)
```
cat  /boot/grub/menu.lst
cat /etc/fstab
```

Thanks for the reply. :)

Here are the outputs:

For cat  /boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=dd05b7c1-877c-4c0a-a6db-23e64e087a31 ro

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
# defoptions=quiet splash irqpoll

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=dd05b7c1-877c-4c0a-a6db-23e64e087a31 ro quiet splash irqpoll
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=dd05b7c1-877c-4c0a-a6db-23e64e087a31 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=dd05b7c1-877c-4c0a-a6db-23e64e087a31 ro quiet splash irqpoll
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=dd05b7c1-877c-4c0a-a6db-23e64e087a31 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

title DreamLinux
# kernel path-to-kernel root=rootdevice kernelarguments
root (hd0,4)
kernel /boot/vmlinuz root=/dev/hda5 vga=0x317 vga=791 splash=silent nomce quiet
initrd = /boot/initrd


title DreamLinux (recovery mode)
# kernel path-to-kernel root=rootdevice kernelarguments
root (hd0,4)
kernel /boot/vmlinuz root=/dev/hda5 vga=0x317 vga=791 splash=silent nomce quiet  single


```

For cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=dd05b7c1-877c-4c0a-a6db-23e64e087a31 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=7a8ef331-aaa4-4285-abf3-26aba5026db9 /home           ext3    defaults        0       2
# /dev/hda5
UUID=8d40ae0a-7f90-4d12-b168-2733e7cb9cf0 /media/hda5     ext3    defaults        0       2
# /dev/hda3
UUID=0db8a86a-1a39-4a73-b8db-d90fffbd2ca5 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by kevinlyfellow on 2007-06-02
well, it looks like my idea was wrong... 
and I don't think I have any more left tonight.  If I think of anything, I'll let you know.

---

### Post by wersdaluv on 2007-06-02
> **kevinlyfellow said:**
> well, it looks like my idea was wrong... 
and I don't think I have any more left tonight.  If I think of anything, I'll let you know.

Thanks. 

I hope I figure this out.

---

### Post by wersdaluv on 2007-06-02
I edited the first post for updates.

:KS

---

