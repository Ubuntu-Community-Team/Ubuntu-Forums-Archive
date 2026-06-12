---
title: "Root partition is lost during boot"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by wijnhout on 2007-11-06
I've installed Ubuntu 7.10 on a clean IDE P-ATA disk. The mainboard is a GigaByte GA-K8N51GMF-9. The root partition is /dev/hdc1 and swap is /dev/hdc5. The install went fine, but the troubles start when booting into the freshly installed OS. 

The boot process starts, but around the time the USB drivers are loaded the process comes to a halt and after being patient for a few minutes, the dreaded "ALERT! /dev/hdc1 does not exists" message appears. I'm presented with a built-in shell, which I used to gather some info. First of all the /proc/modules shows that some relevant ide modules are loaded (ide-core and ide-disk). However when I'm looking in /dev/, there are no /dev/hdc1 and /dev/hdc5 devices, only a /dev/hdc. How did this happen? And more importantly, what can I do to fix it?

---

### Post by ROBarber on 2007-11-06
what you can see using partition manager?

if you don't have it you can install it using the following command:

apt-get install gparted

you can use the fdisk -l commnad to see all partitions with flags and format, but it's a rudimentary view of gparted.

---

### Post by LinuxGuy1234 on 2007-11-06
> **wijnhout said:**
> I've installed Ubuntu 7.10 on a clean IDE P-ATA disk. The mainboard is a GigaByte GA-K8N51GMF-9. The root partition is /dev/hdc1 and swap is /dev/hdc5. The install went fine, but the troubles start when booting into the freshly installed OS. 

The boot process starts, but around the time the USB drivers are loaded the process comes to a halt and after being patient for a few minutes, the dreaded "ALERT! /dev/hdc1 does not exists" message appears. I'm presented with a built-in shell, which I used to gather some info. First of all the /proc/modules shows that some relevant ide modules are loaded (ide-core and ide-disk). However when I'm looking in /dev/, there are no /dev/hdc1 and /dev/hdc5 devices, only a /dev/hdc. How did this happen? And more importantly, what can I do to fix it?

Wow! OK: in the grub.conf file, change the root line on the kernel line to /dev/hdc.

That should work. Before your system boots, go into a GRUB shell and type in:
e
(find root= in the kernel line)
e
(erase the old line (expect root= and put in /dev/hdc)
b

e means Edit and b means Boot. If it works change it in /boot/grub/grub.conf.
If you use LILO, that's a different story.

---

### Post by bulldog on 2007-11-06
> **wijnhout said:**
> I've installed Ubuntu 7.10 on a clean IDE P-ATA disk. The mainboard is a GigaByte GA-K8N51GMF-9. The root partition is /dev/hdc1 and swap is /dev/hdc5. The install went fine, but the troubles start when booting into the freshly installed OS. 

The boot process starts, but around the time the USB drivers are loaded the process comes to a halt and after being patient for a few minutes, the dreaded "ALERT! /dev/hdc1 does not exists" message appears. I'm presented with a built-in shell, which I used to gather some info. First of all the /proc/modules shows that some relevant ide modules are loaded (ide-core and ide-disk). However when I'm looking in /dev/, there are no /dev/hdc1 and /dev/hdc5 devices, only a /dev/hdc. How did this happen? And more importantly, what can I do to fix it?

If you can boot from the live cd,perform the next command in a terminal and post the output on the forum please.```
sudo fdisk -l
```
The menu.lst uses hd0,1 or hd2.0 instead of sdc1 so we have to find your linux first,before we can change the menu.lst.
How many hdd's do you have?

---

### Post by wijnhout on 2007-11-07
I have two harddisks. One P-ATA and a S-ATA disk, Ubuntu is installed on the P-ATA disk which is connected to the secondary IDE channel. A DVD drive is connected to the primary IDE channel.

Btw, the system starts booting allright, it is only after loading many kernel modules that the process stops. I will try to change the boot params as suggested and report back.

---

### Post by bulldog on 2007-11-07
If possible,connect the hdd to the first IDE channel [switch with the cd] and jumper it as master.
Sata hdd are set as master by default.
Change in the BIOS the boot order and make the IDE hdd master boot device and the Sata second boot device.

---

### Post by wijnhout on 2007-11-07
I've tried changing the root boot parameter to root=/dev/hdc, but that doesn't work, I get the error: "/dev/hdc unknown volume type".


Here are some results (using the live CD):

ubuntu@ubuntu:~$ cat /proc/partitions
major minor  #blocks  name
  22     0   40146624 hdc
   8     0  244198584 sda
   8     1   41945683 sda1
   8     2   40957717 sda2
   8     3   20482875 sda3
   8     4          1 sda4
   8     5   40957686 sda5
   8     6   61440561 sda6
   8     7   38411383 sda7
   7     0     657224 loop0

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hdc: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd906d906

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        4787    38451546   83  Linux
/dev/hdc2            4788        4998     1694857+   5  Extended
/dev/hdc5            4788        4998     1694826   82  Linux swap / Solaris

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbb13bb13

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5222    41945683+   7  HPFS/NTFS
/dev/sda2            5223       10321    40957717+   7  HPFS/NTFS
/dev/sda3           10322       12871    20482875    7  HPFS/NTFS
/dev/sda4           12872       30401   140809725    f  W95 Ext'd (LBA)
/dev/sda5           12872       17970    40957686    7  HPFS/NTFS
/dev/sda6           17971       25619    61440561    7  HPFS/NTFS
/dev/sda7           25620       30401    38411383+   7  HPFS/NTFS

As you can see fdisk correctly identifies the two partitions on /dev/hdc. However they do not appear as devices in /dev:

ubuntu@ubuntu:~$ ls /dev/hd*
/dev/hda  /dev/hdc

GParted also shows the partitions correctly. It seems as if the kernel somehow "forgets" to create the /dev/hdc1 and /dev/hdc5 nodes. GParted does show an important warning about /dev/hdc1:
"e2label: No such file or directory while trying to open /dev/hdc1. Couldn't find valid filesystem superblock.

Couldn't find valid filesystem superblock.

dumpe2fs 1.40.2 (12-Jul-2007)
dumpe2fs: No such file or directory while trying to open /dev/hdc1"

---

### Post by wijnhout on 2007-11-07
I´m writing this using the installed Ubuntu 7.10 OS ...

As suggested I swapped the IDE cables of the HD and the DVD drive (so the HD with Ubuntu became /dev/hda), set the root bootarg to root=/dev/hda, et voila, the system boots. So atleast I have found a workaround. Thanks for the suggestion!

Still it seems like a nasty bug in Ubuntu 7.10 ...

---

### Post by bulldog on 2007-11-07
Nice to hear you've got it going :)

It's not really a bug.
For a long time now,you have to set the hdd as master and cd-rom as slave.
With the new Sata system it's not important any more  because each device is a master.
You can set the boot order in the BIOS at your likings with the Sata devices.

---

### Post by wijnhout on 2007-11-08
I do not agree that this is not a bug, because:
* The DVD and HD were never on the same IDE channel and have always been master on their own IDE channel (DVD=hda, HD=hdc). The DVD was initially connected to the first IDE connector on the mainboard, the HD was later added to the second connector on the mainboard. The workaround was to change which cable went into which mainboard connector (making DVD=hdc and HD=hda). 
* The installer did not warn about any misconfiguration of my system.
I'm using Linux for about eight years now, so I'm not easily discouraged, but for new users I can imagine that they would drop 7.10 like a brick if they encounter the same problem. So hopefully this bug (or whatever you call it) will be solved in future versions of Ubuntu.

But luckily, all ended well for me ;-).

---

### Post by bulldog on 2007-11-08
I'm not starting a discussion on what should be or not. :)
By what I know of computers they have to have some sort of a standard configuration.
I have learned IDE hdd is primary master or secondary master,cd and dvd drives should be the primary slave or secondary slave.
In case of two devices the hdd is primary master and cd-dvd is secondary master not the other way around.
But as i said I won't argue on this because I know other people can have other experiences with the connection of the devices.

---

### Post by ROBarber on 2007-11-11
well done.
but it wasn't the boot flag for /dev/hdc1? fdisk shows that

---

