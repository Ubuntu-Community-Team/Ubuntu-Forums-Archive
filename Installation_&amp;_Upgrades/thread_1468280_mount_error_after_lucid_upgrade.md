---
title: "mount error after lucid upgrade"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by MisterEwok on 2010-05-01
I upgraded to the 10.04 from 9.10 with no problems. But now when I start up my computer, the purple startup screen says this under the logo:

"An error occurred while mounting /proc/bus/usb"

And it says something like press "S" to skip and "M" to try to do it manually. And I have no idea what /proc/bus/usb is (since my flash drive still mounts and works normally) and much less how to manually mount something.

So far I haven't noticed any effects of this error on functionality. But it would be nice to fix it.

Thanks.

---

### Post by manolomanolo on 2010-05-01
Similar problem here. While starting up the system I get:

"**An error occurred while mounting /media/cdrom0**"

and then

"**The disk drive for /COMMON is not ready yet or not present**"

In both cases it gives me the choice to **press S to skip or M to manual fix** the problem.

/COMMON is a ntfs partition. In Karmic I was asked for superuser password to mount that partition and Lucid mounts it with no problems and with no password despite the initial message :confused:

It could be good to solve those problems since the system startup hangs until someone press S or M on the keyboard...

Thanks.

---

### Post by Marblemike on 2010-05-01
I had a similar problem on my parents computer. Their documents are located on a second NTFS drive which was /dev/sda1 prior to the upgrade, and ubuntu was installed on /dev/sdb1. Somehow, the two were swapped during the upgrade and I fixed the error message by changing the line

```
/dev/sda1 /media/2C94F65894F623CC ntfs-3g defaults,locale=en_ZA.UTF-8 0 0
```

to 

```
/dev/sdb1 /media/2C94F65894F623CC ntfs-3g defaults,locale=en_ZA.UTF-8 0 0
```

in /etc/fstab.

The partition mounts on boot now, without any error.

---

### Post by hudi on 2010-05-01
I had the same mount problem (/proc/bus/usb).
Try deleting the line containing /proc/bus/usb in /etc/fstab. I read in other posts that it's not needed anymore.

---

### Post by OzzyFrank on 2010-05-06
Yeah, edit the line out of **fstab** and all should be fine!

---

### Post by manolomanolo on 2010-05-07
Hi guys. i solved both my mount problems occurring at startup.

**As for cdrom**, it was loaded by fstab with the "auto" option which is not a problem in case of having a cd or a dvd inside the device. When the device is empty (that is, no cd/dvd inserted) then the mount problem arise. in case of inserting a cd/dvd after startup is completed I get an error message from Gnome informing that the device will be mounted "ro" (read-only mode). I supposed that fstab mounted the device that way because of upgrading ubuntu from the ISO cdrom of the new release (10.04) mounted as virtual device as reported here
[http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD]("http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD")

Googling a bit suggested me to edit the /etc/fstab and substitute the following options:
"auto" with "noauto"
"rw" with "ro"

**As for the COMMON partition**, well the problem was that fstab was trying to mount something (don't know what!) into the /COMMON directory.

So at the moment my /etc/fstab is the following and everything works fine at startup (even if I haven't still tried to burn a cd/dvd):
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	defaults	0	0
#Entry for /dev/sda1 :
UUID=f2821b42-2df9-461b-a040-7bbe3084bb43	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda4 :
UUID=5513-BEBE	/WIN7	vfat	utf8,umask=007,gid=46	0	1
#Entry for /dev/sda3 :
UUID=28EF5D6B27F4AAF8	/media/COMMON	ntfs-3g	defaults,nosuid,nodev,locale=en_GB.UTF-8	0	0
#UUID=1B14-0211	/COMMON	vfat	utf8,umask=007,gid=46	0	1
UUID=667a70d3-6777-46ae-9269-3f90cfa4caed	none	swap	sw	0	0
/dev/scd0	/media/cdrom0	udf,iso9660	ro,user,noauto,exec,utf8	0	0
manolo@manolo-laptop:/media/COMMON$ 


Please note I put a comment (#) before the line giving problems with the /COMMON directory.

---

### Post by nate1010smith on 2010-05-14
I was having a similar problem and getting the "**press S to skip or M to manual fix**" message because of an ntfs partition.

In my case it was the UUID on the partion was different from the one listed in my fstab

I changed: 
```
UUID=740006CB000693F0 /media/sda2     ntfs    defaults,umask=007,gid=46 0       0
```To:
```
UUID=23D2B8D33825BAD7 /media/sda2     ntfs    defaults,umask=007,gid=46 0       0
```and it booted without any errors.

I don't have any explanation for why the UUID would by different after the upgrade and I don't have a record of either my fstab or the partition's UUID so I can't say for sure which one changed. I didn't touch my partition table so I expect that something happened to the fstab during the upgrade. There's also the possibility that the UUID in the fstab has always been wrong but I wasn't getting any boot/mount errors before the upgrade.

---

### Post by ph0neman on 2010-05-28
I had a similar issue: 

I was getting an error "an error occurred unable to mount static" 

Here are the contents of the fstab:

```
/etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=3c15d390-a2f7-4e96-9472-80fad7f0f3a3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5762c250-bd68-42e5-872e-98e1939310b1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

after some looking I realized the first line needed to be # commented out.  After doing so... system boots fine... this thread kickstarted the thought process... thanks!

---

