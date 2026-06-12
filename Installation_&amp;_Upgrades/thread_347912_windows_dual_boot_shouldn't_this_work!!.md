---
title: "windows dual boot: shouldn't this work!?!"
date: 2007-01-28
forum: Installation &amp; Upgrades
---

### Post by jdmux on 2007-01-28
Hi,
I went about configuring what I thought would be a dual boot system, but
for some reason windows won't boot. Here's what I did.

Installed Ubuntu first on 2 drives. Left one partition on the second drive
(/dev/sda1) to do the windows install. When I ran the windows installer
it wanted to write to the MBR on /dev/sda, which is fully an ext3 drive (except
for the swap partition), and I didn't want that. I thought, no problem, I'll just do
the windows install with the drive which it's on attached to the sata0 controller,
so that it will write to the MBR of that drive (which is sdb when I have both drives
connected). I thought this would work, since when I attach both drives I'll just tell grub
to look for windows on (hd1,0). I installed windows, shutdown, put the drive
configuration back to the way I wanted it, and tried to boot into windows with
no luck. When I select windows from grub it just hangs at "starting up".

Did I make an incorrect assumption?

Here is my menu.lst

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda5 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,4)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

title           Windows XP
rootnoverify    (hd1,0)
makeactive
chainloader     +1


and my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda5       /       ext3    defaults,errors=remount-ro 0       1
/dev/sda6       /home   ext3    defaults        0       2
/dev/sda1       none    swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda3       /media/scratch1 ext3    users,rw        0       0

## 250GB disk, /dev/sdb1 is the windows partition
/dev/sdb2       /media/Music    ext3    users,rw        0       0
/dev/sdb3       /media/Pictures ext3    users,rw        0       0
/dev/sdb5       /media/Video    ext3    users,rw        0       0
/dev/sdb6       /media/scratch2 ext3    users,rw        0       0

---

### Post by jdmux on 2007-01-28
The key was getting the right grub menu. I found this on the gentoo forums:

title           Windows XP
map (hd0) (hd1) # Tell the first hard drive to pretend to be the second
map (hd1) (hd0) # Tell the second hard drive to pretend to be the first
root (hd1,0) # Tell GRUB Windows is on /dev/hdb1 (No pretending here)
rootnoverify (hd1,0) # GRUB won't attempt to mount the Windows drive
makeactive # Sets the partition to active

---

### Post by confused57 on 2007-01-28
> **jdmux said:**
> The key was getting the right grub menu. I found this on the gentoo forums:

title           Windows XP
map (hd0) (hd1) # Tell the first hard drive to pretend to be the second
map (hd1) (hd0) # Tell the second hard drive to pretend to be the first
root (hd1,0) # Tell GRUB Windows is on /dev/hdb1 (No pretending here)
rootnoverify (hd1,0) # GRUB won't attempt to mount the Windows drive
makeactive # Sets the partition to active
Excellent explanation of what each line does.

The Window's entry to boot on a 2nd hd is listed here:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

