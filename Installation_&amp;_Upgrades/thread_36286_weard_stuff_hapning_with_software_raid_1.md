---
title: "weard stuff hapning with software raid 1"
date: 2005-05-22
forum: Installation &amp; Upgrades
---

### Post by kisain on 2005-05-22
ok heres the problems:
1) forgot to create a swap partition (need to figure out how) 
2) can't access any harddrives in kubuntu(can in ubuntu)
3) nothing appears to be mounted.
------------------------------------------------------------------------------------------------------------------------------
when i type mount in consloe this is what happens
shane@ubuntu:~$ mount
/dev/md0 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw)
shane@ubuntu:~$
````````````````````````````````````````````````````````````````````````````````````````````````````````
now i don't know whats going on but it's weard very weard software raid seems to be runing as a modual or something but it is running
fstab reports the following:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/md0        /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
what worries me is the errors=remount-ro
````````````````````````````````````````````````````````````````````````````````````````````````````````
now as for the actual hard drives(have to use windows terms sorry guys)
drive c on the primary ide is 40.1GB and on the secondary ide the master is a 30.0GB hard drive
i partitiond them for software raid before i installed ubuntu(software raid 1) and set them up forgetting to create a swap file now because of the size diffrence there is 10GB that is not being used by anything i was told the hard drives for raid had to be the same size (so i made ubuntu think that they are ) so in essence i have 2 30GB hd's but the computer reports them as 29GB and 30 GB now i'm not shure what i did wrong here but damn it's got me confused (i'ma n00b so it's easy lol) now when i click on one of the hard drives it gives me the following error in kubuntu(Could not mount device.
The reported error was:
mount: can't find /dev/hdc1 in /etc/fstab or /etc/mtab)
now my question is : i thought linux has to be on a mounted partition for it to work if the partitions not mounted than how the heck?
anyone with a solution please help :(
````````````````````````````````````````````````````````````````````````````````````````````````````````
what i hope to accheve:
1) a swap partition 
2) the mounting errors gone(it says md0 is running but is it)
3) all the abouve without starting over
4) to be able to compile a wiki to help others with the same problem
````````````````````````````````````````````````````````````````````````````````````````````````````````
thank you all for your time and support
kisain(shane)

---

### Post by Kamping_Kaiser on 2005-05-23
[QUOTE=kisain]ok heres the problems:
1) forgot to create a swap partition (need to figure out how) 
2) can't access any harddrives in kubuntu(can in ubuntu)
3) nothing appears to be mounted.

fstab reports the following:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/md0        /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
what worries me is the errors=remount-ro
````````````````````````````````````````````````````````````````````````````````````````````````````````
[/quote]
errors=remount-ro is ok.
> 
now as for the actual hard drives(have to use windows terms sorry guys)
drive c on the primary ide is 40.1GB and on the secondary ide the master is a 30.0GB hard drive
i partitiond them for software raid before i installed ubuntu(software raid 1) and set them up forgetting to create a swap file now because of the size diffrence there is 10GB that is not being used by anything i was told the hard drives for raid had to be the same size (so i made ubuntu think that they are ) so in essence i have 2 30GB hd's but the computer reports them as 29GB and 30 GB now i'm not shure what i did wrong here but damn it's got me confused (i'ma n00b so it's easy lol) now when i click on one of the hard drives it gives me the following error in kubuntu(Could not mount device.
The reported error was:
mount: can't find /dev/hdc1 in /etc/fstab or /etc/mtab)
now my question is : i thought linux has to be on a mounted partition for it to work if the partitions not mounted than how the heck?
anyone with a solution please help :(
````````````````````````````````````````````````````````````````````````````````````````````````````````
what i hope to accheve:
1) a swap partition 
2) the mounting errors gone(it says md0 is running but is it)
3) all the abouve without starting over
4) to be able to compile a wiki to help others with the same problem
````````````````````````````````````````````````````````````````````````````````````````````````````````
thank you all for your time and support
kisain(shane)
1. you will need to resize with parted/qtparted
2. you dont have hdc1 in your fstab
3. you wont have to reinstall (unless you want)
4. i cant help you there :)

---

