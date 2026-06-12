---
title: "WinXP drive disappearing in Windows after install"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by kabalak on 2006-06-06
Hallo,

 we installed Ubuntu 6.06 from the live CD and everything went fine, grub automatically detected the drives and after setting up the Linux partitions and formatting them, the installation and further customization worked.

But now as we have got a Dual Boot system, WinXP & Ubuntu work perfectly, but under WinXP the second NTFS partition D: is lost, it is not displayed under WinXP but appears under Linux.

HDD setup:

/dev/hda1       NTFS partition, C for WindowsXP (20 GB)
/dev/hda2|3    swap + ext3 for Ubuntu (10 GB)
/dev/hda4       NTFS partition, D for Data (> 100 GB)

How to get the 2nd NTFS partition alive under WinXP again?! Has it got something to do with MBR?

---

### Post by Vati-Khan on 2006-06-06
please post 

*cat /etc/fstab* 
and 
*cat /etc/mtab*

did you move Partitions, what was the setup before?

---

### Post by kabalak on 2006-06-06
[QUOTE=Vati-Khan]please post 

*cat /etc/fstab* 
and 
*cat /etc/mtab*

did you move Partitions, what was the setup before?[/QUOTE]

Will post /etc-files in the evening at home, the setup was the same before, I just deleted the previous Debian partitions (also /dev/hda2 + /dev/hda3 like now, I only made the swap partition 500 -> 512 MB big and made the ext3 partition correspondingly smaller) and created new partitions with the Ubuntu installer.

The order of the partitions is the same like before. With the old Debian installation we had not a problem like this: WinXP showed both NTFS drives  and we did also use grub like now.

---

### Post by toLa` on 2006-06-06
Does the partition display within fdisk? If it does, then its still there, it just needs mounting. In terminal (GNOME) Applications > Accessories > Terminal, type:

sudo fdisk -l to check if its listed.

Alternatively, check within Disk Management in XP (Right click My Comp > Manage > Disk Management (left hand side), and see if the disk is displayed there.

---

### Post by mannheim on 2006-06-06
I know this doesn't help, but this looks similar to the experience in [this thread.]("http://www.ubuntuforums.org/showthread.php?t=186395") There's a possibly-related bug reported [here.]("https://launchpad.net/distros/ubuntu/+source/parted/+bug/32529") It really seems to me that using the installer to do anything more than the very simplest partitioning tasks has turned out to be very risky.

---

### Post by kabalak on 2006-06-06
[QUOTE=toLa`]Does the partition display within fdisk? If it does, then its still there, it just needs mounting. In terminal (GNOME) Applications > Accessories > Terminal, type:

sudo fdisk -l to check if its listed.

Alternatively, check within Disk Management in XP (Right click My Comp > Manage > Disk Management (left hand side), and see if the disk is displayed there.[/QUOTE]

Within Disk Management of XP, the 2nd "lost" NTFS partition (Dönertier) is shown up, but without any drive letter :-k The 1st NTFS system partition C: is shown there with the drive letter.

---

### Post by rcarring on 2006-06-06
You need to assign a drive letter to the NTFS partition. XP knows it is there but drive is not mounted, that is why drive can be seen under Linux.

---

### Post by kabalak on 2006-06-06
[QUOTE=rcarring]You need to assign a drive letter to the NTFS partition. XP knows it is there but drive is not mounted, that is why drive can be seen under Linux.[/QUOTE]

Yes, but we cannot assign a drive letter, the menu entries are greyed out :-( And with the cmdline tool "diskpart" on WinXP (suggested by the WinXP help) the volume is not listed up at all. Very weird... 

Is there a way to assign a drive letter via Linux?

---

### Post by kabalak on 2006-06-06
**/etc/fstab** entries:```


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda4       /media/hda4     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda2       none            swap    sw              0       0

# SANE Treiberzeugs fuer Scanner
none /proc/bus/usb usbfs noauto,devmode=0666 0 0
```

**/etc/mtab** file:

```
/dev/hda3 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-23-386/volatile tmpfs rw 0 0
/dev/hda1 /media/hda1 ntfs rw,nls=utf8,umask=007,gid=46 0 0
/dev/hda4 /media/hda4 ntfs rw,nls=utf8,umask=007,gid=46 0 0
/dev/hdd /media/cdrom iso9660 ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8 0 0
```

But as I'm just seeing via fdisk, the Ubuntu installer has got changed the NTFS partition into a Linux partition! Would a simple change of the partition type solve the problem?! Interestingly the disks-admin tool in GNOME tells me that /dev/hda4 (the lost D: NTFS partition) is NTFS, weird...

```
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3825    30724281    7  HPFS/NTFS
/dev/hda2            3826        3890      522112+  82  Linux swap / Solaris
/dev/hda3            3891        5232    10779615   83  Linux
/dev/hda4            5233       19457   114262312+  82  Linux swap / Solaris

```

---

### Post by rcarring on 2006-06-06
Try changing the partition type. I would warn you this may not work, but you say the drive is being recognized as NTFS, so maybe it will (i.e. drive has not been changed to ext3)

---

### Post by kabalak on 2006-06-06
So, I did a backup of the date, but it was not necessary - after switching the partition type via fdisk to HPFS/NTFS it works under Windows again - thanks.

But it's astonishing that the Ubuntu installer or something in the installation process did change the partition type of an existing NTFS partition; this should never happen.

---

