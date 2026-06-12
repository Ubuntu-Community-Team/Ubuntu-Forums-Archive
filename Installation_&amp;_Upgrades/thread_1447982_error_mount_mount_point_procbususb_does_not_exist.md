---
title: "error: mount: mount point /proc/bus/usb does not exist"
date: 2010-04-06
forum: Installation &amp; Upgrades
---

### Post by speed32219 on 2010-04-06
If I run the folowing commands:
sudo mount -t usbfs none /proc/bus/usbmount
sudo cat /proc/bus/usb/devices

to verify what dirvers are being used for my usb attached remote control receiver, I get the following error in bold. (pretty sure usbhid which I need to change for my remote to work properly) .

**mount: mount point /proc/bus/usb does not exist**

Here is my fstab.

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=b535a1ba-55dc-47ef-82f4-451a17c0394a /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=bd12cdab-42af-4c44-8904-770101c8e310 /home           ext3    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=27ae14f2-c1c6-40fb-a657-15a91aa11fd3 none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=32f440ff-926a-49cc-b9af-a63939ff0ee6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1       /media/disk1    ext3    defaults        0       0
/dev/sdb2       /media/disk2    ext3    defaults        0       0

```

Here is lsusb
**Bus 003 Device 002: ID 15c2:0043 SoundGraph Inc.**
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

It's like uhci is not loaded.  Any suggestions

---

