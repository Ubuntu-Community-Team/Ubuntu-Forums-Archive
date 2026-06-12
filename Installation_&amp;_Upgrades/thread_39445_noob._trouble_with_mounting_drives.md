---
title: "noob. trouble with mounting drives"
date: 2005-06-05
forum: Installation &amp; Upgrades
---

### Post by makoto on 2005-06-05
Hi, I installed Ubuntu today and have been trying to deal with a problem for countless hours now. Im a real noob to both Linux and Ubuntu so please be kind....
Here's the situation : I have two hard drive of 80G each.  The master use to have windows xp and the slave had files.  The master used to be Fat32 but was reformated into ntfs when I installed Ubuntu.  (I'm pretty sure anyway) The slave is NTFS.  Now here's the problem : I cannot access my drives.  They do not show up in place -- computer and I cannot access them from dev.    I have been reading ubuntuguide.org all day, have followed all instructions on mounting drives to no avail.  When I try to mount hte drives I get the message that they are already mounted yet I cannot access them..   

Here is my fstab config :

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  ntfs    umask=0222      0       0
/dev/hda1       /media/windows  ntfs    umask=0222      0       0


and here is what I get when i type mount in terminal :


pablo@DESKTOP:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw)
/dev/hdb1 on /media/windows type ntfs (rw,umask=0222)


It says both drives are mounted but when I go in DEV the icons for the drives have a red x over them and I get an error message when I try to access them,,,

Could someone enlighten me please?

---

### Post by janrinok on 2005-06-05
It might be a permissions problem.  Try 'sudo su -' and then access your ntfs drive.  If you can then see the contents then there is a problem with the permissions for 'normal' users.  However, while reading ntfs is not usually a problem writing to them can often cause heartache.  NTFS is closed source and the code to write to ntfs has been written by reverse engineering.
If you want to be able to move files from one OS to the other (both ways) the cleanest solution is to create a partition called, say, 'transfer'  and format it as fat32.  Both OS can read and write to fat32.  HTH.  Jan

---

