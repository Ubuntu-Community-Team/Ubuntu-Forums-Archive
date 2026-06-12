---
title: "&quot;serious erros where found while checking&quot; after 11.10 upgrade"
date: 2011-12-04
forum: Installation &amp; Upgrades
---

### Post by MrKnoedelmann on 2011-12-04
Hi,

since I upgraded to (K)ubuntu 11.10 I get this error on each kdm start:
"serious erros where found while checking /mnt/winxp" - ignore, skip, manual..

after choosing "ignore" the login screen appears and /mnt/winxp is mounted.

I guess its a bug as there is no problem mounting /mnt/winxp (this worked well before 11.10). 

Where do I get information about that "serious errors"? What kind of errors are so serious and no hint is given what to do (fsck, syslog, s.m.a.r.t)?

No errors in kdm.log, syslog or dmesg output.


[FONT="Courier New"]root@section60:~/Documents# mount
/dev/sdb2 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
**/dev/sda1 on /mnt/winxp type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)**

root@section60:~/Documents# umount /mnt/winxp
root@section60:~/Documents# mount /mnt/winxp
root@section60:~/Documents# echo $?
0
root@section60:~/Documents# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=fcd9e2ac-fcb3-49df-b4bd-a775a77bb5bb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb1 during installation
UUID=0f55c2a3-54ab-4ddc-b67e-152d6647e796 none            swap    sw              0       0
**/dev/sda1       /mnt/winxp                                ntfs    rw    0      2**

root@section60:~/Documents# uname -a
Linux section60 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:27:26 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
root@section60:~/Documents# lsb
lsblk        lsb_release  
root@section60:~/Documents# lsb_release 
No LSB modules are available.
root@section60:~/Documents# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 11.10
Release:        11.10
Codename:       oneiric
root@section60:~/Documents#[/FONT]


any help would be much appreciated

---

### Post by AbdulRahiem on 2011-12-05
I do not have a solution, but perhaps some more information.

I was getting the same message, under various flavours of Ubuntu. After disabling my various NTFS drives in the fstab, the error message went away, at least it did in Kubuntu. When trying Xubuntu, the error changed to the "Door" instead (whatever that means) and having to press "I" just once.

With the drives active in the fstab, VMware would not give them back after running a virtual copy of Windows. Instead, there was a reference to "mbat" (if I remember the name correctly) reporting the relevant drives as being busy. When, for sure, they were not. Manually unmounting and remounting threw all sorts of similar warning messages, but there were no apparent difficulties in running the drives. Parallels and VirtualBox did not have difficulties with giving the drives back after running Windows vitually. For unrelated reasons (nothing to do with licence fees, because I've got a licence anyway), I have uninstalled Parallels and now work only with VirtualBox.

The choice is now between the following:

1. Activate the NTFS drives in the fstab and  press the "I" for each drive when booting. No apparent ill effects afterwards and everything works well.

2. Disable the NTFS drives in the fstab, but then before I can access data on any of those drives, I must either mount them manually one by one (because they are now not active in the fstab, 'mount -a' won't work), or first access them through a file manager, so that they get mounted that way.

I found (poor) solution 1 the least disruptive.

The NTFS drives concerned are two on physical on-board hard disks and two on separate USB disks (not sticks). A small FAT32 drive on a USB stick is not affected by any of this.

Best regards,

---

### Post by kio_http on 2011-12-05
Since it seems you have WIndows Xp, boot XP and in My computer right click on all the NTFS drives and select properties. Do the "Check disk for errors" option

---

### Post by MrKnoedelmann on 2011-12-07
After RTFM a little, I found the solution:

As upstart starts a lot of tasks its almost impossible to figure out what task reported the problem. the manpage 7 of upstart-events gave me a hint where to look at.

I startet my GNU/Linux and choosed "m" for manual recovery:

[FONT="Courier New"]Filesystem check or mount failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and continue booting after re-trying
filesystems.  Any further errors will be ignored
Give root password for maintenance
(or type Control-D to continue):
root@amazonas-sk:~# mount
/dev/sda6 on / type xfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda3 on /boot type ext3 (rw)
/dev/sdb1 on /mnt/sdb1 type ext4 (rw)
root@amazonas-sk:~# mountall
fsck from util-linux 2.19.1
swapon: /dev/sda5: swapon failed: Device or resource busy
mountall: swapon /dev/sda5 [1125] terminated with status 255
mountall: Problem activating swap: /dev/sda5
[COLOR="Red"][B]fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.ntfs for /dev/sda1[/B][/COLOR]
mountall: fsck /mnt/250GBHDD0PRI0 [1121] terminated with status 8
mountall: Unrecoverable fsck error: /mnt/250GBHDD0PRI0
mountall: Skipping mounting /mnt/250GBHDD0PRI0 since Plymouth is not available[/FONT]


According to man 5 fstab:
*If the sixth field is  not present  or  zero,  a  value  of zero is returned and fsck will assume that the filesystem does not need to be  checked.*

so I just deleted the 6th field in /etc/fstab for my ntfs-volumes. 

That's all!

hth

(indeed very serious errors :()

---

