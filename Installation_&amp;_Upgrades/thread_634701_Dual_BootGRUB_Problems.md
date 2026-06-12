---
title: "Dual Boot/GRUB Problems"
date: 2007-12-08
forum: Installation &amp; Upgrades
---

### Post by jimmybond on 2007-12-08
I'm sorry if I posted on a problem that was previously mentioned, but I couldn't find one fully relevant.  I'm a total newb.  There are a lot -- most are relevant to some extent.  The dual boot sites found on Google aren't really helpful.  But it'd also be helpful if you can link me to some threads that are relevant.

Here's what I'm trying to do/what I did:

I have two HDs.  Master on Windows XP, and slave on Ubuntu, both connected with one IDE channel.  XP has already been installed first and boots correctly.

To install Ubuntu, I used the live CD (v 7.10) and installed it.  I selected the "use entire drive" option and picked my slave drive.

I also selected to install the boot loader on the (hd1), which is supposedly the slave drive.

The confirmation screen shows:

The partition tables of the following devices are changed:
SCSI1 (0,1,0)

The following partitions are going to be formatted:
partition #1 of SCSI1 (0,1,0)(sdb) as ext3
partition #5 of SCSI1 (0,1,0)(sdb) as swap

So when I restarted it, I had to configure the bios to boot to the slave drive first in order for the grub menu to show up, otherwise, it'd boot to windows automatically.

I get the grub menu to show up, but all the Ubuntu options give "Error 21: invalid or unsupported executable format."  If I select the Windows option, it doesn't boot either.  The only way to boot Windows is to go to BIOS and enable the master drive.

If I use Live CD again, and boot to open up a terminal, 
"sudo gedit /boot/grub/menu.lst" opens the file, but there is no text.

Thanks in advance.

---

### Post by PmDematagoda on 2007-12-08
While in the Live CD, could you post the result of:-
```

cat /etc/mtab
```

And:-

```
sudo fdisk -l
```

---

### Post by jimmybond on 2007-12-08
cat /etc/mtab gives:

```

proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
tmpfs /lib/modules/2.6.22-14-generic/volatile tmpfs rw, mode=0755 0 0
tmpfs /lib/modules/2.6.22-14-generic/volatile tmpfs rw, mode=0755 0 0
varrun /var/run tmpfs rw, noexec, nosuid, nodev, mode=0755 0 0
varlock /var/lock tmpfs rw, noexec, nosuid, nodev, mode=1777 0 0
udev /dev tmpfs rw, mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw, gid=5, mode=620 0 0
tmpfs /tmp tmpfs rw, nosuid, nodev 0 0

```


and sudo fdisk -l  yields:

```

Disk /dev/sda: 10.2 GB, 10262568960 bytes
255 heads, 63 sectors/track, 1247 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x29af29ae
   
     Device Boot     Start     End      Blocks          Id    System
/dev/sda1 *               1     1246    10008463+     7     HPFS/NTFS

Disk /dev/sdb: 4311 MB, 4311982080 bytes
255 heads, 63 sectors/track, 524 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x47d047cf

     Device Boot     Start     End       Blocks        Id    System
/dev/sdb1 *            1       494     3968023+     83    Linux
/dev/sdb2              495     524      240975        5     Extended
/dev/sdb5              495     524      240943+      82   Linux swap


```

---

### Post by logos34 on 2007-12-08
On the grub menu screen hit 'e' on the ubuntu kernel, then 'e' again on the 'root' line and change to (hd[COLOR="Red"]**0**[/COLOR],0).  Then 'b' to boot.  If it works make the change permanent:

gksudo gedit /boot/grub/menu.lst

change the root and 'groot' lines

---

### Post by jimmybond on 2007-12-08
After changing that, Ubuntu does load, but it discovers an error in sdb1 and forces itself into a fsck.  The check fails and gives:

```

[  143.040909] Buffer I/O error on device sdb1,  logical block595406
Error reading block 595406 (Attempt to read block from filesystem resulted in short read).

/dev/sdb1: UNEXPECTED INCONSISTENCY: RUN FSCK MANUALLY.
     (i.e., without -a or -p options)
fsck died with exit status 4

*An automatic file system check (fsck) of the root filesystem failed
A manual fsck must be performed, then the system restarted.
The fsck should be performed in maintenance mode with the 
root filesystem mounted in read-only mode.
*The root filesystem is currently mounted in read-only mode.
A maintenance shell will now be started.
After performing system maintenance, press CONTROL-D 
to terminate the maintenance shell and restart the system. 
```

Then it lists a bunch of bash commands and says command not found.
The final line is a command prompt.

The last time I used this hard drive, it was fine; I don't think there are errors on it.....

Also, If I choose the Windows XP option, it still responds Error 13.
The BIOS doesn't really allow me to choose the boot sequence, only shut a drive off or enable it, so i have to shut off the winxp master drive to enable the GRUB, which makes sense, since GRUB was installed at the slave ubuntu drive.
[http://support2.jp.dell.com/docs/systems/dim8200/syssetup.htm#1097056](http://support2.jp.dell.com/docs/systems/dim8200/syssetup.htm#1097056)

Now, when I try to boot Windows with the slave drive enabled, it gives a warning about how the IDE controller is operating outside of normal specifications.  It goes away if I turn the slave drive off, though.

---

### Post by logos34 on 2007-12-09
Boot from the ubuntu live cd and run:

sudo e2fsck -y -f -v /dev/sdb1

> **jimmybond said:**
> Also, If I choose the Windows XP option, it still responds Error 13.

Change windows 'root' line and add mapping:

> title		Windows XP
root		(hd**1**,0)
[B]map            (hd0) (hd1)
map            (hd1) (hd0)[/B]
savedefault
makeactive
chainloader	+1

You might also have to change /boot/grub/device.map to match. i.e.

(hd0) /dev/sdb
(hd1) /dev/sda

> The BIOS doesn't really allow me to choose the boot sequence, only shut a drive off or enable it, so i have to shut off the winxp master drive to enable the GRUB, which makes sense, since GRUB was installed at the slave ubuntu drive.
[http://support2.jp.dell.com/docs/systems/dim8200/syssetup.htm#1097056](http://support2.jp.dell.com/docs/systems/dim8200/syssetup.htm#1097056)

Now, when I try to boot Windows with the slave drive enabled, it gives a warning about how the IDE controller is operating outside of normal specifications.  It goes away if I turn the slave drive off, though.

You might check that the drives are jumpered correctly--either both set for 'CS' (cable select) or master and slave.  Or maybe try different hard disk detect settings in the bios--'user', 'auto', etc.  Maybe change the 'boot sequence' line so slave (primary drive1) is first (as far as I can make sense of that page)

EDIT: on second glance I guess maybe you're right--the bios doesn't seem to allow you to change the boot order, only 'display' the 'boot sequence' with <enter>.  If you have to turn off the primary drive 0 (master) to boot ubuntu then it looks like you won't be able to boot windows from the grub entry.

---

### Post by jimmybond on 2007-12-10
ok, I've gotten it to boot to Ubuntu; the file check fixed all the errors.  I don't know if it was the hard drive or motherboard or the switch, but it was making double-clicking noises inside the computer.  

When I boot into Ubuntu's desktop (now without the LiveCD of course), it goes through about five minutes of the same clicking and reports something like:
"Panel encountered problem while loading OAFIID: GNOME_FastUserSwitchApplet" with options to Delete or Don't Delete.
A second message with the same options says, the same about the "Deskbar_Applet"

I changed the root lines and the device.map lines and made them permanent.  making the windows hard drive active does nothing unless I enable it in the BIOS (which means grub won't load unless i turn the windows hard drive off and the slave drive on) and it can only boot from there.

Right now, the jumpers are set to Windows-Master, Ubuntu-Slave, should I change the jumpers to both Cable Select?  Possibly that can make a difference?

Thanks for your help.

---

### Post by logos34 on 2007-12-10
> **jimmybond said:**
> Right now, the jumpers are set to Windows-Master, Ubuntu-Slave, should I change the jumpers to both Cable Select?  Possibly that can make a difference?

possibly.  I've seen problems solved by switching the cable mode.

---

### Post by jimmybond on 2007-12-11
Nope, doesn't work.  Must be the BIOS Dell has.  I guess I'll have to change it enable it each time I'll boot to Windows.

Thanks a lot for helping me out!

---

