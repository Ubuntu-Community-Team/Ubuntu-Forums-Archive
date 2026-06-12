---
title: "/etc/fstab file is corrupted"
date: 2009-09-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by arvvvs on 2009-09-16
File:
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda4 during installation
UUID=56404154-08ed-4b0a-a7a9-d12292d7a27f /               ext4    relatime,errors=remount-ro 0       1
# none was on /dev/sda5 during installation
UUID=acb946db-5a44-4c59-afe7-ae37f8953b06 none            swap    sw              0       0

LSUSB:
Bus 008 Device 002: ID 046d:0a02 Logitech, Inc. Premium Stereo USB Headset 350
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 05ac:1262 Apple, Inc. iPod Nano 3.Gen
Bus 002 Device 002: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 046d:08ce Logitech, Inc. QuickCam Pro 5000
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

sudo fsdisk -l
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06e858c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3828    30746624    7  HPFS/NTFS
/dev/sda2            3829        7907    32764567+   b  W95 FAT32
/dev/sda3            7908       28092   162136012+   5  Extended
/dev/sda4           28093       37818    78124095   83  Linux
/dev/sda5            7908        8826     7381836   82  Linux swap / Solaris
/dev/sda6            8827       22209   107498916    7  HPFS/NTFS
/dev/sda7           22210       28092    47255166   83  Linux
Note: sector size is 4096 (not 512)

Disk /dev/sdf: 3892 MB, 3892056064 bytes
38 heads, 42 sectors/track, 595 cylinders
Units = cylinders of 1596 * 4096 = 6537216 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1         596     3800580    b  W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 1, 22)
Partition 1 has different physical/logical endings:
     phys=(59, 37, 42) logical=(595, 13, 42)
Help?
So now I cannot mount anything, and if i try it says Not Authorized

So basically I cannot mount partitions, or any USB devices.  Every time I do I get error messages saying Unable to Mount Not Authorized

---

### Post by arvvvs on 2009-09-17
*BUMP* 
Could do with answers badly...

---

### Post by taavikko on 2009-09-17
> **arvvvs said:**
> *BUMP* 
Could do with answers badly...

What's the problem?
fstab doesn't handle dynamically mounted devices (USB-sticks etc.)
fstab will only mount partitions that are supposed to (defined in it)

So, you're trying to mount external partition? error messages?

---

### Post by ubongo2008 on 2009-09-17
> **arvvvs said:**
> 
So now I cannot mount anything, and if i try it says Not Authorized


you can always mount even with no fstab at all.
you will have to provide 3 things to mount

1. Filesystemtype (-t vfat for fat32, -t ntfs-3g for ntfs ... )
2. Mountpoint
3. The device / volume you want to mount 
4. you may pass options to mount too like (read only = ro or read/write = rw or noatime or relatime ...)

example: **mount -t ntfs-3g** *volume* mount_point [B][-o *option*[,...]]



[/B]

---

### Post by arvvvs on 2009-09-17
Thanks,
 but is there any way I can fix it as I can't mount either USB drives, or Partitions without using the complicated method.  Like is there any way to fix the fstab file?

---

### Post by VMC on 2009-09-17
Is your group assignment messed up, perhaps. cat out "/etc/group", and check that you belong to the correct groups.

---

### Post by arvvvs on 2009-09-17
Don't know how to interpret it so here:
> ```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:arvvvs
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:arvvvs
fax:x:21:
voice:x:22:
cdrom:x:24:arvvvs
floppy:x:25:
tape:x:26:
sudo:x:27:
audio:x:29:pulse,arvvvs
dip:x:30:
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:arvvvs
sasl:x:45:
plugdev:x:46:arvvvs
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
syslog:x:102:
klog:x:103:
fuse:x:104:
ssl-cert:x:105:
lpadmin:x:106:arvvvs
crontab:x:107:
mlocate:x:108:
ssh:x:109:
avahi-autoipd:x:110:
gdm:x:111:
netdev:x:112:
pulse:x:113:
pulse-access:x:114:
messagebus:x:116:
polkituser:x:117:
avahi:x:118:
haldaemon:x:119:
admin:x:120:arvvvs
arvvvs:x:1000:
sambashare:x:121:arvvvs
winbindd_priv:x:122:
saned:x:123:
vboxusers:x:124:arvvvs
rtkit:x:115:
couchdb:x:125:
```

---

### Post by VMC on 2009-09-17
It looks the same as mine. Your topic is misleading. Or your assuming its fstab. Your fstab is normal. 

You can try and add another user as a test and see if that user can access Removable Media?

---

### Post by arvvvs on 2009-09-17
Your right... I logged in as another user after creating an account and it worked... so now how do i fix it for my main account

---

### Post by arvvvs on 2009-09-17
Thanks it actually works now

---

