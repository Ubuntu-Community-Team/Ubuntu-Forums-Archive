---
title: "convert to lvm"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by ghotra on 2006-10-31
Hi, I just installed edgy...and as far as I can tell, I am not using lvm.  After 'sudo apt-get install lvm2', I did:

```

$ sudo lvm
lvm> pvscan
 No matching physical volumes found
lvm> lvscan
 No volume groups found

```

I would like to start using lvm...here is my current setup.

```

$ sudo fdisk /dev/sda

The number of cylinders for this disk is set to 14593.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14201   114069501   83  Linux
/dev/sda2           14202       14593     3148740    5  Extended
/dev/sda5           14202       14593     3148708+  82  Linux swap / Solaris

Command (m for help): 

```

Currently, I have a single partition which holds my OS and my boot.  I know that I need to make /boot so that it is not LVM.  Is that a correct statement?  

How do I go about setting my machine up? Note, I'm not so sure that I am not using LVM as the following might suggest:

```

[FONT="Fixedsys"]$ df --si
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda1              115G    17G    93G  15% /
varrun                 526M   123k   526M   1% /var/run
varlock                526M   4.1k   526M   1% /var/lock
procbususb              11M   103k    11M   1% /proc/bus/usb
udev                    11M   103k    11M   1% /dev
devshm                 526M      0   526M   0% /dev/shm
lrm                    526M    19M   508M   4% /lib/modules/2.6.17-10-generic/volatile
/dev/scd0              733M   733M      0 100% /media/cdrom0

$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4de5be5e-5826-4107-8032-116a70828f2d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=3986d72c-d00d-4e99-aff3-d97faa9a13be none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0[/FONT]

```

---

