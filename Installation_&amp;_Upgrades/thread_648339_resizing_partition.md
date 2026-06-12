---
title: "resizing partition"
date: 2007-12-23
forum: Installation &amp; Upgrades
---

### Post by vavoem on 2007-12-23
I used to dual boot with windows XP. Since i never use XP i removed it from sda1 and formatted that partition as ext3 then i changed the line in fstab to mount it /dev/sda1 to /home/username/data

This gives ME back a lot of space however not to the entire OS
I want the diskspace to be available to the whole os.
How do i go about and give the space back to the OS i have read a lot of stuff about people who messed up their grub and i dont want to be one of them

this is my partition table
```
df -ahT
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda2     ext3    9.2G  7.4G  1.4G  85% /
proc          proc       0     0     0   -  /proc
/sys         sysfs       0     0     0   -  /sys
varrun       tmpfs    252M  132K  252M   1% /var/run
varlock      tmpfs    252M     0  252M   0% /var/lock
procbususb   usbfs    252M  108K  252M   1% /proc/bus/usb
udev         tmpfs    252M  108K  252M   1% /dev
devshm       tmpfs    252M     0  252M   0% /dev/shm
devpts      devpts       0     0     0   -  /dev/pts
lrm          tmpfs    252M   33M  219M  14% /lib/modules/2.6.20-16-generic/volatile
//192.168.1.6/g$
             smbfs    116G   93G   23G  81% /mnt/gdrive
binfmt_misc
       binfmt_misc       0     0     0   -  /proc/sys/fs/binfmt_misc
/dev/sda1     ext3     21G  173M   20G   1% /home/maarten/data

```

---

### Post by nzadLithium on 2007-12-23
use gparted to form it all back into one partition (resize). If you do this its best to backup any important data i dont think it will try to wipe anything but just in case i would backup.

Alternatively you might be able to setup both partitions similar to raid but i dont know how to go about that.

---

### Post by vavoem on 2007-12-23
You mean delete sda1 and then resize sda2? This won't affect grub?

---

### Post by logos34 on 2007-12-23
ubuntu root will remain 'sda2' even if you delete sda1 and resize....so grub should be ok.

To grow / you'll have to use gparted on the Gparted live cd (root cannot be mounted and I believe you'll need gparted 0.3.4 because you're enlarging the partition into the empty space toward the front of the disk)

---

### Post by vavoem on 2007-12-23
Thanx a bunch guys
Finally enough space to setup some shared VMware machines
Linux :guitar:

And you 2

---

