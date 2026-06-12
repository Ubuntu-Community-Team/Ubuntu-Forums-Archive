---
title: "mdadm raid-1 array broken after upgrade"
date: 2012-04-22
forum: Installation &amp; Upgrades
---

### Post by acidrop on 2012-04-22
hello all,

I had ubuntu 9.04 desktop on raid-1 configuration with 2 x 500gb sata disks with mdadm (created by alternate cdrom installation).
After an upgrade from ubuntu 9.04 to 10.04 lts, system boots fine but now running fdisk i can see that raid-1 array is broken and system boots and uses only the first disk (/dev/sda1).

My question is if i can assemble the raid again in a working system and not offline by a live cd?

Below I am posting fdisk and fstab settings:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00071ff0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          12       96358+  83  Linux
/dev/sda2              13         741     5855692+  82  Linux swap / Solaris
/dev/sda3             742       60800   482423917+   5  Extended
/dev/sda5             742       15330   117186111   83  Linux
/dev/sda6           15331       60800   365237743+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00071ff0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          12       96358+  83  Linux
/dev/sdb2              13         741     5855692+  82  Linux swap / Solaris
/dev/sdb3             742       60800   482423917+   5  Extended
/dev/sdb5             742       15330   117186111   83  Linux
/dev/sdb6           15331       60800   365237743+  83  Linux

``` 

fstab:

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/mapper/isw_cbhgjjjeed_versus15 during installation
UUID=3cadcb0f-bf7b-46e3-bf4e-0e7eb2d1754a /               ext3    relatime,errors=remount-ro 0       1
# /boot was on /dev/mapper/isw_cbhgjjjeed_versus11 during installation
UUID=b384ff1d-f54b-4d6d-bbfd-2dad94fee2a8 /boot           ext3    relatime        0       2
# /home was on /dev/mapper/isw_cbhgjjjeed_versus16 during installation
UUID=d139ce0d-23ea-4264-b98a-86fa8210cc09 /home           ext3    relatime        0       2
# swap was on /dev/mapper/isw_cbhgjjjeed_versus12 during installation
UUID=7dcacd9c-9f58-4633-add0-212c243be00e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

#none /proc/bus/usb usbfs devgid=123,devmode=664 0 0
```

thank you for any suggestions

---

### Post by darkod on 2012-04-22
I thought /dev/mapper/XXXX is used in fakeraid or hardware raid, not in mdadm software raid. Are you sure you used software raid?

The mdadm devices are called /dev/md0, /dev/md1, etc, not /dev/mapper/.

---

### Post by acidrop on 2012-04-22
good point

I can't remember well because this machine is working as a kind of file server in an office away from me and i don't remember well if i created a raid with mdadm or fakeraid.

Maybe your are right.. can you please suggest what can I do so that I can have some kind of redudancy with the hard disks but preferably without the need to boot offline from a live cd?

thank you

---

### Post by darkod on 2012-04-22
Sounds like the array is not active. In live mode you can activate a fakeraid array with:
sudo dmraid -ay

But I am not sure what is the best way to activate existing array permanently and keep the data safe at the same time.

You would probably need to enter with chroot into your installation and run the dmraid -ay command. And in some way check if the dmraid module will load at boot.

---

### Post by acidrop on 2012-04-22
$sudo dmraid -ay
RAID set "isw_cbhgjjjeed_versus1" already active
RAID set "isw_cbhgjjjeed_versus11" already active
RAID set "isw_cbhgjjjeed_versus12" already active
RAID set "isw_cbhgjjjeed_versus15" already active
RAID set "isw_cbhgjjjeed_versus16" already active

It seems that it is already active?
Maybe i should change just fstab entries to get it "recognized" by system?

---

### Post by darkod on 2012-04-22
> **acidrop said:**
> $sudo dmraid -ay
RAID set "isw_cbhgjjjeed_versus1" already active
RAID set "isw_cbhgjjjeed_versus11" already active
RAID set "isw_cbhgjjjeed_versus12" already active
RAID set "isw_cbhgjjjeed_versus15" already active
RAID set "isw_cbhgjjjeed_versus16" already active

It seems that it is already active?
Maybe i should change just fstab entries to get it "recognized" by system?

Sounds like it.

Also, maybe you will need to simply reinstall grub to the MBR. Maybe the array and the system is working fine, only the bootloader is messed up.

---

### Post by acidrop on 2012-04-22
ok.. will try it.. thanks for the help!

---

