---
title: "Vista dual boot prob"
date: 2007-06-06
forum: Installation &amp; Upgrades
---

### Post by celticbhoy on 2007-06-06
I have a dual boot with Fiesty & Vista, and all was working well till last night. For some reason the Vista boot no longer boots up (just hangs at starting windows), I can get in by boot through the recovery partition, and have full access to everything.

The problem is that when I boot fiesty I no longer have access to the Vista partition, only my Linux, and Recovery partitions are showing up.

If I check the /media folder it shows as below :-

cdrom  cdrom0  disk  General  General_  sda1  sda2  usbdisk

where sda1 is the Vista partition.

fdisk -l gives :-

Disk /dev/sde: 507 MB, 507379712 bytes
16 heads, 63 sectors/track, 983 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1         983      495313+   6  FAT16

Disk /dev/sdg: 522 MB, 522043904 bytes
17 heads, 59 sectors/track, 1016 cylinders
Units = cylinders of 1003 * 512 = 513536 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   ?     1864179     2032364    84344761   69  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(68, 13, 10) logical=(1864178, 14, 6)
Partition 1 has different physical/logical endings:
     phys=(288, 115, 43) logical=(2032363, 13, 31)
Partition 1 does not end on cylinder boundary.
/dev/sdg2   ?     1696431     3560719   934940732+  73  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(371, 114, 37) logical=(1696430, 3, 15)
Partition 2 has different physical/logical endings:
     phys=(366, 32, 33) logical=(3560718, 13, 25)
Partition 2 does not end on cylinder boundary.
/dev/sdg3   ?           3           3           0   74  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(371, 114, 37) logical=(2, 9, 37)
Partition 3 has different physical/logical endings:
     phys=(372, 97, 50) logical=(2, 9, 36)
Partition 3 does not end on cylinder boundary.
/dev/sdg4               1     3424839  1717556736    0  Empty
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 0) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 0, 0) logical=(3424838, 16, 14)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

and finally mount gives :-

/dev/sdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sda2 on /media/sda2 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdg on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)
/dev/sde1 on /media/General_ type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=gary)

I think that the problem is with auto-mounting the disk at startup, but I dont know enough about this to try and fix it, any ideas or soultions would be welcome.

---

### Post by bodyboarding_bum on 2007-06-06
I don't know how to help... but my opinion... ditch vista, its ****. :p

---

### Post by celticbhoy on 2007-06-06
Need it for certain tasks

---

### Post by celticbhoy on 2007-06-06
I have just discovered that if I access the drive through /media/sda1, I can read the drive, so why does it not show on desktop as it used to ???

---

### Post by celticbhoy on 2007-06-06
I have checked the way both the recovery and the vista drives are mounted in automount and both have same command, but only the recovery drive shows on the desktop, anyone got any ideas???

---

### Post by Elrohir on 2007-06-06
> **celticbhoy said:**
> I have just discovered that if I access the drive through /media/sda1, I can read the drive, so why does it not show on desktop as it used to ??? maybe the UUID is messed up, did you reinstall Vista lately?

---

### Post by celticbhoy on 2007-06-06
Had a problem starting windows, and had to run a system recovery app to reset booting, thought I might have had a problem with grub but it was ok. It was after that this prob started. Assuming you right, how do I go about fixing it ???

---

### Post by Elrohir on 2007-06-06
> **celticbhoy said:**
> Had a problem starting windows, and had to run a system recovery app to reset booting, thought I might have had a problem with grub but it was ok. It was after that this prob started. Assuming you right, how do I go about fixing it ???
system recovery is much likely a reinstallation (I believe), but as you say assuming i'm right, do this:
```
sudo vol_id /dev/sda1 -u
```
this gives you a 16 digit HEX code, copy this code somewhere. now:
```
sudo gedit /etc/fstab
```
look for the line that says #/dev/sda1, right beneath it says UUID=<HEX CODE>, is it the same? if not, replace with the new code, save and exit...

---

### Post by celticbhoy on 2007-06-06
copy of fstab :-

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=8bc4dc09-6c2a-480e-9ea6-679fbeeb81d4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=9dfe2ffb-ec2b-437c-9e09-15540b67b87c none            swap    sw              0       0
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto     0       0
# Generated by Automatix
/dev/sda1   /media/sda1   ntfs-3g  defaults,locale=en_US.utf8    0    0
/dev/sda2   /media/sda2   ntfs-3g  defaults,locale=en_US.utf8    0    0
## End of Automatix mounted partitions

---

### Post by Elrohir on 2007-06-06
I see... Automatix... hmm... just before making a suggestion, why is it that you have 2 NTFS partitions?

---

### Post by celticbhoy on 2007-06-06
Vista & Recovery partition.

---

### Post by Elrohir on 2007-06-06
ok, in that case, assuming sda1 is Vista and sda2 is the recovery one do the following:
```
sudo vol_id /dev/sda# -u
```for each sda (1 and 2), copy those values somewhere
replace fstab contents with the following:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=8bc4dc09-6c2a-480e-9ea6-679fbeeb81d4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb5
UUID=9dfe2ffb-ec2b-437c-9e09-15540b67b87c none            swap    sw              0       0
/dev/cdrom       /media/cdrom0   udf,iso9660 user,noauto     0       0
# /dev/sda1
UUID=<code for /dev/sda1> /media/Vista ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda2
UUID=<code for /dev/sda2> /media/VistaRecovery ntfs-3g defaults,nls=utf8,umask=007,gid=46 0 2
# Generated by Automatix
# /dev/sda1   /media/sda1   ntfs-3g  defaults,locale=en_US.utf8    0    0
# /dev/sda2   /media/sda2   ntfs-3g  defaults,locale=en_US.utf8    0    0
## End of Automatix mounted partitions
```(crossing fingers here, just kidding) and that should do the trick... post your results!

---

### Post by celticbhoy on 2007-06-06
At work will post result when i get home

---

### Post by celticbhoy on 2007-06-06
cant get by the first bit of code, says 'error open volume'

---

### Post by celticbhoy on 2007-06-06
Just had a good look at output from 'fdisk -lu', and found that the Vista partition is not highlighted as a boot device. I am guessing that there is an issue with the MBR or something on this drive.

I know this is a Ubunutu forum but any help in fixing this drive would be welcome.

---

### Post by Elrohir on 2007-06-06
this is going over my head... anyone that has Vista can share his/her fstab file?

---

### Post by celticbhoy on 2007-06-06
Just checked with gparted, and the Vista drive is marked as a linux swap drive, think I must have goofed when I was messing aroung with a mem stick trying to emulate readyboost on vista. If I am right I need to turn the swap off on the drive to sort it.

---

### Post by celticbhoy on 2007-06-06
Now the problem seems to be that 'swapoff /dev/sda1' gives :-

swapoff: /dev/sda1: Invalid argument

Sooo, I gues that to remove the swap file, or set the drive identity back to ntfs there has to be some other command I am looking for

any ideas ????

---

### Post by celticbhoy on 2007-06-06
Is it possible that the only way to fix this partition is through windows, possibly by re-loading the original Vista MBR ???

---

