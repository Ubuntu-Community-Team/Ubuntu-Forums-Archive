---
title: "Raid 1 disappears after reboot"
date: 2010-07-21
forum: Installation &amp; Upgrades
---

### Post by Skirmish on 2010-07-21
I've had one disk out of a 2 disk raid 1 array with 2 volumes die. I swapped out the disk for an identical model and rebuilt the array but *every* time (up to about the 5th now) the array disappears after rebooting The process I've been following has been:

1) Boot into linux properly or use the installation disk to boot into a command line from / mounted on /dev/md0

2) Copy the partition tables from sda to sdb where sda is the working disk and sdb is the replacement ```
sfdisk -d /dev/sda | sfdisk /dev/sdb
```

3) Add sdb1 to the / array ```
mdadm --add /dev/md0 /dev/sdb1
``` 
Add sdb5 to swap array ```
mdadm --add /dev/md1 /dev/sdb5
```

4) Wait untill both are fully resynced then as root update the mdadm.conf file
 ```
mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm/mdadm.conf
``` 

At this point /md0 shows up as healthy & containing both disks.

When I reboot though, I get an error along the lines of: Cannot add /dev/sdb1 to /dev/md0 device does not exist. Sure enough, when I look in /dev there is sda sda1 sda2 sda5 but only sdb - no sdb1 sdb2 or sdb5. md0 now shows up as clean - degraded
If i *don't* boot into the degraded raid and go into recovery console instead, i can see disks sdb1, 2 & 5.

My mdadm.conf looks like this, and I've confirmed the UUID of mdadm --detail /dev/md0 is the same as the UUID of /dev/md0 listed in the config file below.
```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=a5e4a1dc:da3032f2:a5472550:e945e8d6
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=26bd6a02:ecb7b3b5:b227cc48:3b0aba98

# This file was auto-generated on Fri, 26 Mar 2010 01:46:44 +1100
# by mkconf $Id$

```

This is driving me nuts! I've researched so many different tutorials on rebuilding a raid1 but can't manage to get this one up.
Any help greatly appreciated!

---

### Post by Skirmish on 2010-07-26
No ideas? I forgot to mention I'm running Ubuntu 9.10 x64 Server Edition...

---

### Post by jacekk015 on 2010-07-26
Put here result of:
```
sudo sfdisk -l -uS /dev/sda
```

---

### Post by HankB on 2010-07-26
> **Skirmish said:**
> No ideas? I forgot to mention I'm running Ubuntu 9.10 x64 Server Edition...I've been fiddling with a RAIDed root partition (10.04) and it looked like 'sfdisk' did not understand the partition information on my drives. I used 'parted' to modify a partition by setting the 'raid' flag and then added it to a raid device. I just rebooted that system and the raid partition is there with both drives.

At the moment I'm trying to figure out how to make both drives bootable. I can only boot from /dev/sdb where I installed 10.04 on a degraded RAID 1 partition. I've now added the partition from /dev/sda but cannot boot from /dev/sda. But that's probably the subject for another post. ;)

HTH

---

### Post by jacekk015 on 2010-07-26
> **HankB said:**
> I've been fiddling with a RAIDed root partition (10.04) and it looked like 'sfdisk' did not understand the partition information on my drives. I used 'parted' to modify a partition by setting the 'raid' flag and then added it to a raid device. I just rebooted that system and the raid partition is there with both drives.

At the moment I'm trying to figure out how to make both drives bootable. I can only boot from /dev/sdb where I installed 10.04 on a degraded RAID 1 partition. I've now added the partition from /dev/sda but cannot boot from /dev/sda. But that's probably the subject for another post. ;)

HTH

Make /dev/sda bootable in parted, fdisk or etc. and then:
```
**sudo grub-install /dev/md0**
```Look at [https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html](https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html)
```
If you do need to replace a faulty drive, after the drive has been replaced and synced, **grub** will need to be installed.  To install **grub** on the new drive, enter the following:
**sudo grub-install /dev/md0**

```

---

### Post by HankB on 2010-07-26
Thanks for the reply and the link to the advanced installation guide. I'm sure it would have saved me some effort had I found it sooner.
> **jacekk015 said:**
> Make /dev/sda bootable in parted, fdisk or etc.

The details in this turned out to be key. Even though I had installed and could boot 9.10 on the first drive, this requirement was not met in order to boot the RAID1 (10.04) installation. The partitioner had created a small first partition (1MB) and set the bios_grub flag on it on the second drive. I noticed that flag was not set on the corresponding partition on the first drive so I used 'parted' to set it. After that, I was able to install grub to /dev/md0 (using the command you listed above) and it worked this time. No partition on either drive is marked as bootable.

Incidentally, the 10.04 installer sets up a 'GPT' partition table that fdisk and sfdisk do not support.

thanks,
hank

---

### Post by jacekk015 on 2010-07-27
You can alway use sfdisk to duplicate disk partition table to other disks:
```
sfdisk -d /dev/sdb | sfdisk --force /dev/sda
```

---

### Post by HankB on 2010-07-27
> **jacekk015 said:**
> You can alway use sfdisk to duplicate disk partition ...
Unless the installer has created a GPT partition table which is not supported by sfdisk.

```
barta@tenere:~$ sudo sfdisk -d /dev/sda
[sudo] password for hbarta: 

**WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.**

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=        1, size=3907029167, Id=ee
/dev/sda2 : start=        0, size=        0, Id= 0
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
hbarta@tenere:~$ 
```(emphasis mine)

---

### Post by jacekk015 on 2010-07-27
Strange - my 10.04 install with partitions created with installer [partman] has created msdos partitions.
I've made that on Virtualbox which is sitting on Windows.
I've created 2 disks 8GB and they are working in RAID1 array.

---

### Post by HankB on 2010-07-27
Mine was a server install. I have no idea what it uses behind the scenes to partition the disk or if the partitioner makes any decision WRT disk size to use a different style partition table. I'm using 2 2TB drives.

---

### Post by Skirmish on 2010-07-29
> **jacekk015 said:**
> Put here result of:
```
sudo sfdisk -l -uS /dev/sda
```

Here you go jacekk015
```
Disk /dev/sda: 121601 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1            63 1941664094 1941664032  fd  Linux raid autodetect
/dev/sda2     1941664095 1953520064   11855970   5  Extended
/dev/sda3             0         -          0   0  Empty
/dev/sda4             0         -          0   0  Empty
/dev/sda5     1941664158 1953520064   11855907  fd  Linux raid autodetect

```

I've been doing sfdisk -d /dev/sda | sfdisk /dev/sdb successfully as part of my recovery attempt, is the any benefit to adding **force**?

Another weird thing I noticed is that after leaving the machine alone for a few days, I can see sdb1, 2 & 5 in /dev . Unfortunately after adding sdb1 to md0 it's begun resyncing again as though it never synced properly in the first place... I am sooo confused!

---

### Post by jacekk015 on 2010-07-29
From the beginning:
You have your OS installed on md0?
I don't see a boot flag marked on sda disk.

--force isn't needed if it does what it have to do.
--force mean do what I say even if I'm wrong.

Partitions on sda, and sdb should be identical.
Compare them.

Maybe it's a sdb disk failure - not holding partitions table ?

---

### Post by Skirmish on 2010-09-08
Sorry for the late reply, an urgent project came up.
To answer your question, yes the OS is on md0. I'm not sure about the boot flag on sda - I remember setting sda1 as bootable during the install wizard.

As far as I can tell partitions on sda and sdb *are* identical, up until the point I reboot after adding sdb to the array when the partitions disappear. I'll try just cloning the partitions and see if that holds on sdb.

---

