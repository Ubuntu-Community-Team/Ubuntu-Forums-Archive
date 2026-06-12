---
title: "Laptop internal HDD appears as SDB instead of SDA"
date: 2019-10-28
forum: Installation &amp; Upgrades
---

### Post by lordofscripts on 2019-10-28
I am using an Acer laptop and intended to use Ubuntu installed on an external SATA disk connected via one of the USB ports. The dsk is recognized properly and I have access to it as a mounted disk when I TRY Ubuntu  as I have not installed.

In the Legacy BIOS list the CD/DVD appears first in the boot sequence, followed by the internal HDD of the laptop and then the external USB drive where I intend to install. I would expect the internal drive to always be /dev/sda and the external /dev/sdb but luckily I noticed this early or my whole Windows installation would have been wiped out! as it is /dev/sda is the EXTERNAL USB hard drive, I do not understand WHY.

---

### Post by Skaperen on 2019-10-28
the boot list order has nothing to do with the device name order.  if you boot from the external USB drive and it gets mounted as / then it is forced to be sda by the kernel.  this can also happen in some other cases.  which device did you boot from?  is it a USB memory stick?  what size is it?  what image name did you put on it?

when that system is up, do these commands and post the results in code tags:
```

cat /proc/partitions;df /

```

---

### Post by lordofscripts on 2019-10-28
My boot list is as follows:
  [1] CD/DVD  <---- The Ubuntu media disk is there
  [2]  500MB Internal HDD    <---- Has several partitions from factory. Windows 10 is installed there (upgraded from Windows 8.1 which was the original OS)
  [3]  1TB external USB HDD  <---- one empty 1TB partition, nothing there. Did NOT boot from here.

The laptop booted from the DVD which contains the Ubuntu live system. The DVD drive is internal, so is the 500MB HDD which should be seen as /dev/sda. The third drive,from which it did NOT boot and has NOTHING in it is seen as /dev/sda. but being external and not being booted from I would expect to be /dev/sdb

ubuntu@ubuntu:~$ cat /proc/partitions ;df /
major minor  #blocks  name

   7        0    1935764 loop0
   7        1      91264 loop1
   7        2      55812 loop2
   7        3     153508 loop3
   7        4       4300 loop4
   7        5      15100 loop5
   7        6        956 loop6
   7        7      45240 loop7
   8        0  976762584 sda
   8        1  976759808 sda1
   8       16  488386584 sdb
   8       17     409600 sdb1
   8       18     307200 sdb2
   8       19     131072 sdb3
   8       20  470317296 sdb4
   8       21     909312 sdb5
   8       22   16310272 sdb6
  11        0    2406096 sr0
Filesystem     1K-blocks   Used Available Use% Mounted on
/cow             1909968 655296   1254672  35% /

---

### Post by Holger_Gehrke on 2019-10-28
Devices get names in the order they declare themselves to be available and ready to udev during system start up. This is completely independent of anything but timing. There are persistent symlinks in /dev/disk/by-id/ which are named in a complex scheme that includes manufacturer, model, serial number and partition (if applicable). Using these for mounting from the command line (using tab-completion to save a lot of typing) has probably saved my data from some horrible fate more than once. For mounting in /etc/fstab you can also use these or use 'UUID=<uuid of the drive as reported by "lsblk -fs">' or 'LABEL=<user assigned file system label>' instead of a device name.

Holger

---

### Post by lordofscripts on 2019-10-29
I am aware of the device naming andnumbering. I don´t think it depends on timing, otherwise what today is sda for boot, it may be sdc some other day depending on "timing". That I know, internal hardware is always enumerated first because it is fixed, so first SATA i/f 1,then 2, etc. with whatever is attached to them. External devices -which change from time to time- have a higher sequence. At least that is how it was when I was a Linux fanatic many years ago.

For that reason my logic is that the internal HDD would be /dev/sda and expected any EXTERNAL drive to be either /dev/sdb or /dev/sdc depending on whether the DVD bay was on the same type of interface and "counted" first or not. I performed countless installations since Yggdrassil but granted, I have not done a Linux installation in the past 8 years or so.

---

### Post by oldfred on 2019-10-29
On several systems, both BIOS & UEFI, internal drives are first and then if I plug in a flash drive it is later like sdf.
But if I reboot with flash drive plugged in, flash drive is first, and every hard drive is later in boot order.

On my old BIOS system I had sdc as default boot and boot order did not change, or it still booted that drive. But reboot with flash drive changed everything all around as far as device order was.

---

### Post by TheFu on 2019-10-29
In Linux for decades, the order that devices are found by the kernel has not been fixed. To get around that issue, UUIDs are typically used for mounting partitions.  If the SATA/SCSI driver is used, then sd[a-z] will be used for the device names.  systemd has made this happen more often, thanks to parallel discovery methods.  [https://help.ubuntu.com/lts/installation-guide/i386/apcs04.html](https://help.ubuntu.com/lts/installation-guide/i386/apcs04.html)
Beliefs and the facts differ.   Holger_Gehrke's explanation is true.

There are other methods to specify partitions ... look under /dev/disk/by-*/ for the different options. 
```
by-id/       by-label/    by-partuuid/ by-path/     by-uuid/     
```
I use by-label/ links for non-internal devices and by-path/ on systems with lots and lots of disks and controllers.

At boot, the links where those canonical names point are corrected to the real devices, so the links we use don't change between boots.

How to deal with that at the grub level, I don't know. It has never been an issue for me, but I bet the BIOS has a way to control boot search order using USB first, if that is the need.  That is a good way for the system to be hacked if you leave it enabled and don't have a good password for BIOS access.

---

### Post by Skaperen on 2019-10-29
internal vs. external does not affect the order of device naming.  a hard drive attached via SCSI, SATA, IDE, USB, or any other kind of connective bus does not change anything about it by being inside the box or outside.  about the only kind of storage device that can be expected to be first every time is flash memory directly attached to the CPU bus.  it would not have timing responses to consider and would be ready as soon as integrated drivers were initialized.

**do not depend on these names to consistently identify devices.**

before UUIDs were implemented i would mount devices at a temporary mount point in read-only mode and check for something particular, such as a file, or get some specific info from the partition table.  but general purpose system setup, like a live ISO, can't do that (the ISO may be at /dev/sr0 or not).

---

### Post by Skaperen on 2019-10-29
did you ever work on IBM mainframes?  there is an architecture where device order is consistent, as long as you don't change what is plugged in.  but if you add a new hard drive at a very low number, that can bump up a lot of other disk drives.  putting a disk drive at 0x100 would be the only way to be sure it was /dev/sda (unless they put USB at channel 0 ... doubtful).

---

