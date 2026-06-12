---
title: "Attaching NEW Hard Disk Changes Device Name FROM: /dev/sdb (HOME) TO: /dev/sdc (HOME)"
date: 2010-09-06
forum: Installation &amp; Upgrades
---

### Post by AlexanderDGreat on 2010-09-06
Here's my story. I have:
1x 250gb /dev/sda - /boot, /swap, /(root) - *physical hard disk*
1x 1tb /dev/**sdb** - /home - [I]separate physical hard disk
[/I]
BUT WHEN I ATTACH A NEW HARD DISK (for backups) **/dev/sdb (/home)** _BECOMES_ **/dev/sdc (/home)**, which is confusing for me!

After attaching a new hard disk, now it looks like:
1x 250gb /dev/sda - /boot, /swap, /(root)
1x 1tb /dev/**sdb** - /backups - *NEW separate physical hard disk*
1x 1tb /dev/**sdc** - /home

Why did /home move to **/sdc**? Isn't my HOME partition suppose to retain /**sdb** while the new Hard Disk "backups" be assigned to /**sdc** ???

Bottom line, I want my hard drives to look like this:
1x 250gb /dev/sda - /boot, /swap, /(root)
1x 1tb /dev/**sdb** - /home
1x 1tb /dev/**sdc** - /backups

What am I doing wrong? Is there something I need to know? What should I do? Thanks for reading. :)

---

### Post by sisco311 on 2010-09-06
Instead of /dev/sd*# use UUIDs, LABELs or symlinks.  

[uhelp]community/UsingUUID[/uhelp]

---

### Post by AlexanderDGreat on 2010-09-06
Hi sisco311, I'm not exactly sure what you mean, but I'm not doing anything on my system. I'm not mounting anything on fstab, if that's what you mean.

Every Device & Partition Name of my hard disks are fine, until I attached a new Hard disk, and it changed my /home from sdb to sdc.

Shouldn't the new hard disk acquire sdc ---> since it's the newest, sdA, sdB, sdC... right?

But that's not what's happening.

Any ideas why this is so?

---

### Post by jocko on 2010-09-06
> **AlexanderDGreat said:**
> Shouldn't the new hard disk acquire sdc ---> since it's the newest, sdA, sdB, sdC... right?

But that's not what's happening.

Any ideas why this is so?

Device nodes are set up dynamically on each boot, and there is probably no easy way the kernel can know which disk was connected in which order (might even be that the kernel just inherits the order from the boot loader, which is even more ignorant).
As far as I understand /dev/sda is always given to the first hard drive in the bios boot order (probably has to be this way since that's the drive that contains the boot loader).

The other drives are probably just designated their device nodes in the order they are detected on that particular boot, which can probably depend on several different things (but it could be that the drive set as number two in the boot order will become sdb? Haven't tested, so I don't know...).
If your motherboard have more than one hard disk controller, maybe one is detected before the other (but the exact order could randomly change from boot to boot, which is one reason why uuids were invented)... Maybe your backup drive is slightly faster at responding to some signal, which causes it to be detected before the other...

Why is it so important for you to have /home on /dev/sdb? Is it simply that you have (mis-)configured fstab to mount by device nodes instead of uuid, so your machine now fails to mount /home? Or is there some other reason why your /home just has to have /dev/sdb?
In old grub 1 you could re-map the order of the hard drives, but I'm not sure how to do it, or if it is even possible in grub 2.

---

### Post by oldfred on 2010-09-06
On my system the drive order is the order they are plugged into the SATA ports. That has not changed. But grub follows the BIOS and if I boot sdc it becomes hd0 just for the boot, it still is sdc.

Are you backing up in a way that copies the UUIDs to the backup drive. We have seen where the system then boots whichever drive comes up to speed first and may use the backup as the production system.

---

### Post by AlexanderDGreat on 2010-09-07
Hi jocko & oldred - thanks for replying.

> Maybe your backup drive is slightly faster at responding to some signal, which causes it to be detected before the other... - So Hitachi is faster than Seagate. Damn you sea guys.

> Why is it so important for you to have /home on /dev/sdb? - It's just out of my systematic thinking. I have 3 harddisks, figured it would be logical that the last one be called **letter C.** My other server doesn't have this problem. It follows A, B, C.

> Is it simply that you have (mis-)configured fstab to mount by device nodes instead of uuid, so your machine now fails to mount /home?

Actually, here's my fstab:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0

# / was on /dev/sda9 during installation
UUID=3a0b75a2-a818-4d1e-8111-a0bf793757cd /               ext4    errors=remount-ro 0       1

# /boot was on /dev/sda7 during installation
UUID=157cf8ac-e464-44f0-9f70-e8a090280a27 /boot           ext4    defaults        0       2

**# /home was on /dev/sdb1 during installation**
UUID=b6796cf6-a67e-404d-a517-4a7f3213a54d /home           ext4    defaults        0       2

# swap was on /dev/sda8 during installation
UUID=204dc857-a6b1-4394-a007-2ca5a8ea5e23 none            swap    sw              0       0


#automount backups
/dev/disk/by-label/backups/ /media/backups/	ext4	defaults	0	2

```

Didn't do a single thing in it. But notice home is correctly placed under **SDB**. So something happens upon the login to Ubuntu and not on booting?

But my sudo fdisk -l also lists **SDC** first before **SDB**. Isn't that strange?

```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a954e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       30402   192999214+   5  Extended
/dev/sda5            6375        7649    10241406    7  HPFS/NTFS
/dev/sda6            7650       24221   133114558+   7  HPFS/NTFS
/dev/sda7   *       24222       24343      975872   83  Linux
/dev/sda8           24343       25559     9764864   82  Linux swap / Solaris
/dev/sda9           25559       30402    38899712   83  Linux

Disk **/dev/sdc:** 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000914d0

   Device Boot      Start         End      Blocks   Id  System
**/dev/sdc1**               1      121601   976760001   83  Linux

Disk **/dev/sdb**: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000703c6

   Device Boot      Start         End      Blocks   Id  System
**/dev/sdb1 **              1      121601   976760001   83  Linux
```
 
I dual boot this computer with Windows XP. But Windows & Ubuntu is on SDA, does that do anything? Don't think so right?

> On my system the drive order is the order they are plugged into the SATA ports. - Yup mine too! But on the desktop the third drive is still **SDB**.

> Are you backing up in a way that copies the UUIDs to the backup drive. - I'm not sure what you mean, I just backup via rsync -avz to the third hard disk.

---

### Post by Hobgoblin on 2010-09-07
It is because however you are attaching the new drive it is becoming the 2nd drive in the BIOS, this then becomes /dev/sdb

fstab does not use the device for this very reason.  It uses the UUID which uniquely identifies the drive rather than where it is in the order of devices.

Note "# /home **was on /dev/sdb1** during installation". i.e. when you installed Ubuntu the partition you are using for /home was on /dev/sdb, it does not have to always be there because it will be mounted according to UUID and not device.

I don't know why you care which device it is attached to, you would rarely use the device name.  You would normally just use the mount point.

Your /media/backups appears to be mounting by partition label so that should always mount correctly - by which I mean it will mount to the correct path (/media/backups) unless you have 2 partitions with the same label.

If you really want to get /home back on /dev/sdb you need to look at how they are attached.  Are they SATA or IDE drives?  If they are IDE then what is on which cable?  If SATA then what SATA ports are they attached to? Are they in the BIOS boot list and if so what order do they appear in there?

---

### Post by confused57 on 2010-09-07
I had the exact same thing happen on a newly built pc, initially with only 2 hard drives:
sda = (hd0) 1TB Hitachi with Ubuntu 8.04
sdb = (hd1) 640MB WD with Windows XP
The menu.lst entry for XP is "root (hd1,0)" with map entries.

I added a 1TB Hitachi as a 3rd HD.  The HD's are connected in sequence to the MB SATA controllers.  Once I added the 3rd HD, Ubuntu recognized the drives as:
sda = (hd0) 1TB Hitachi
sdc = (hd1) 640MB WD
sdb = (hd2) 1TB Hitachi(new drive).

Windows XP still boots fine from 8.04 with root (hd1,0), so that leads me to believe that sdc is indeed (hd1), especially since I'm booting from 8.04's legacy grub.  Also "fdisk -l" lists sda, sdc, then sdb, same as the OP saw.

When I press F12 for bios boot menu and select Hard Drive, the 2 Hitachi's are listed first then the WD.  There might be something to the suggestion that the Hitachi are recognized before the WD in bios?

I don't have any solutions for this, I just have to keep it in mind if I have to reinstall grub or install another distro.

---

### Post by sisco311 on 2010-09-08
> **Hobgoblin said:**
> 
If you really want to get /home back on /dev/sdb you need to look at how they are attached.  Are they SATA or IDE drives?  If they are IDE then what is on which cable?  If SATA then what SATA ports are they attached to? Are they in the BIOS boot list and if so what order do they appear in there?

Hmmm, that's no longer true (since 2003???, I think). The kernel usually just assigns unpredictable device names based on the order of discovery. 

Back in "the old times" device node names were assigned based on the bus device number, but now that's not a viable solution. Even SATA disks are hot swappable (I don't want to talk about USB drives, keyboards, mice, printers, web cams...). 

udev solves this issue by creating unique and meaningful symlinks. Meaningful symlinks provide a way to reliably identify devices based on their properties or current configuration.

See:
[http://kernel.org/pub/linux/utils/kernel/hotplug/udev_vs_devfs](http://kernel.org/pub/linux/utils/kernel/hotplug/udev_vs_devfs)
[http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)
```
man udev
```
The gentoo wiki is usually good:
[http://www.gentoo.org/doc/en/udev-guide.xml](http://www.gentoo.org/doc/en/udev-guide.xml)
For even more details check out the Linux Kernel documentation
[http://www.kernel.org/doc/](http://www.kernel.org/doc/)

---

### Post by AlexanderDGreat on 2010-09-08
> If you really want to get /home back on /dev/sdb you need to look at how they are attached. Are they SATA or IDE drives? If they are IDE then what is on which cable? If SATA then what SATA ports are they attached to? Are they in the BIOS boot list and if so what order do they appear in there? - Sata Cables. Sata ports are in order.

I'm a logical thinker, The SATA 0, 1, 2 ,3 - are in the ORDER I partition my hard disks:

/boot, /swap, /root - SDA SATA0
/home - SDB SATA1
/backups - SDC SATA2
/dev/sr0 - DVDROM SATA3

so I don't think I have an issue there. But in Ubuntu it's /backups - SDB, /home - SDC - quite the opposite.

---

### Post by jocko on 2010-09-08
> **AlexanderDGreat said:**
> - Sata Cables. Sata ports are in order.

I'm a logical thinker, The SATA 0, 1, 2 ,3 - are in the ORDER I partition my hard disks:

/boot, /swap, /root - SDA SATA0
/home - SDB SATA1
/backups - SDC SATA2
/dev/sr0 - DVDROM SATA3

so I don't think I have an issue there. But in Ubuntu it's /backups - SDB, /home - SDC - quite the opposite.
You still haven't told us why it matters.
Try swapping the sata cables around and put your backup drive on SATA1 and home on SATA2, but I guess it won't matter. Your backup drive is probably just a little bit faster at being detected by the bios, boot loader, kernel, udev or whatever it is that sets the order... Is it newer or better in any way?

---

### Post by gratou on 2011-03-14
> **jocko said:**
> You still haven't told us why it matters.
Try swapping the sata cables around and put your backup drive on SATA1 and home on SATA2, but I guess it won't matter. Your backup drive is probably just a little bit faster at being detected by the bios, boot loader, kernel, udev or whatever it is that sets the order... Is it newer or better in any way?

zfs pools reference the device letters. switching cables doesn't help. :(

---

### Post by dimepag on 2011-04-25
I use dd command to create bootable USB sticks

"dd if=/directory/file.img of=/dev/sdd"


Why do you have to change the drive letters? I Almost flushed away 1.5 terabytes of precious homevideos and stuff, omg fortunately I started the Disk Utility before and noticed that the USB sticks "/dev/sdd" has changed to "/dev/sda"

This is very stupid indeed, Ubuntu Team. Tell me one good reason why in the **** there is need to change those letters when i reboot the machine?

Now I cannot never use Bash history commands if I use /dev/sdx or /dev/hdx and I've been using then about 20 years.

Nice thing this DRIVE LETTER LOTTERY you geniuses have figured out!

---

### Post by dimepag on 2011-04-29
well Now i DID flush 2 terabytes of my personal data to bit heaven

Now my 2 terabytes homevideos etc /dev/sdd1 is filled with .iso garbage when i did wrong DD command

I hate you Ubuntu

I really really Hate you and please you guys who decided to make this drive lettering lottery, you guys wont meet me in IRL never

---

