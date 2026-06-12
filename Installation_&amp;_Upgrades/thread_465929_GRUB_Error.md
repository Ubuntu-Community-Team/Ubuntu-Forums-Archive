---
title: "GRUB Error"
date: 2007-06-06
forum: Installation &amp; Upgrades
---

### Post by Pumalite on 2007-06-06
Well guys, I-ve done it. Last night, while trying to install DVDDecrypter, looks like I messed up my GRUB becaused when rebooting I found the fatal message> Grub Error- I'm writing from Knoppix now and awaiting help. I googled the question of fixing GRUB and dearched the forums , but none of the answers seem to fit my problem. This is my fdisk -l>

root@1[knoppix]# fdisk -l

Disk /dev/hda: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        7269    58388211   83  Linux
/dev/hda2            7270        7709     3534300   83  Linux
/dev/hda3            7710        7984     2208937+  83  Linux
/dev/hda4            7985       14596    53110890   83  Linux

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1         262     2104483+  82  Linux swap / Solaris
/dev/hdb2             263        2179    15398302+  83  Linux
/dev/hdb3            2180        4998    22643617+  83  Linux

Disk /dev/hdd: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1               1        4870    39118243+  83  Linux
root@1[knoppix]#

I have Suse 10.2 occupying the last 2 harddrives, intalled first in dual boot with XP in hda< later, TrueImaged XP to External Drive, Gparted hda in two partitions and installed SimplyMepis in one of them : don't remember which one. Later, I installed Ubuntu in the other partition in hda. In Knoppix Desktop I have this images>
Hard Disk
hda1

Hard Disk
hda2

Hard Disk
hda3

Hard Disk
hda4

Hard Disk
hdb2

Hard Disk
hdb3

Hard Disk
hdd1

This is one of my fstab>from hda1

# Pluggable devices are handled by uDev, they are not in fstab
/dev/hda1 / ext3 defaults,noatime 1 1
none /proc proc defaults 0 0
none /proc/bus/usb usbfs devmode=0666 0 0
none /dev/pts devpts mode=0622 0 0
none /sys sysfs defaults 0 0
# Dynamic entries below
/dev/hda2 /mnt/hda2 ext3 noauto,users,exec 0 0
/dev/hda3 /mnt/hda3 auto noauto,users,exec 0 0
/dev/hda4 /mnt/hda4 ext3 noauto,users,exec 0 0
/dev/hdb1 swap swap sw,pri=1 0 0
/dev/hdb2 /mnt/hdb2 ext3 noauto,users,exec 0 0
/dev/hdb3 /mnt/hdb3 ext3 noauto,users,exec 0 0
/dev/hdd1 /mnt/hdd1 ext3 noauto,users,exec 0 0
/dev/cdrom /media/cdrom udf,iso9660 noauto,users,exec,ro 0 0
/dev/hdc /media/cdrom udf,iso9660 noauto,users,exec,ro 0 0
/dev/fd0 /media/floppy vfat,ext2 noauto,users,exec,rw 0 0
So, any ideas on how to fix it_ What should I use Ubuntu Live or Knoppix. What are the commands~
sorry about the ortography, my keyboard has been hijacked.

hda2 contains lost+found with a lock on top--cannot see it.

---

### Post by mainalisuyog on 2007-06-06
Do you have an ubuntu alternate install cd? U could boot from it, and select the "repair" mode. Then, select the partituion where u have ubuntu installed, and choose to reinstall grub.

---

### Post by confused57 on 2007-06-06
You could reinstall grub(probably Ubuntu's), using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Pumalite on 2007-06-06
> **confused57 said:**
> You could reinstall grub(probably Ubuntu's), using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Thanks a lot for your prompt reply. You saved my day! Your link took me to the perfect recipe. My only problem is that I ended up with a Mepis Grub, which doesn't recognize the other two distros, but I think it was mt own error. The command 'find' gave 3 choices and i chose the first one, which ended being Mepis Grub. Is probably a matter of repeating the process and choosing a different option this time. Am I right?

---

### Post by confused57 on 2007-06-06
That's correct, your Ubuntu root is probably (hd0,3)...glad it worked.

---

