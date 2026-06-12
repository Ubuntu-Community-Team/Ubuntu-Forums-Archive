---
title: "Failed attempt to add Ubuntu 14.04.3 LTS amd64 to Windows 10 machine"
date: 2015-12-25
forum: Installation &amp; Upgrades
---

### Post by dgshaver on 2015-12-25
Hi All,

New to Ubuntu.  Have been starting to use Ubuntu 14 at work, and wanted to create a dual boot configuration on an existing Windows 10 machine I have at home (i7, 1 TB internal HDD, 1 TB USB drive, 8GB of RAM).

Shrunk the primary partition on my internal HDD to free up 100GB of space to use for Ubuntu install.  Started Ubuntu install and created an EXT4 partition and 8 GB of swap space.  Install seemed to go through cleanly and then the dreaded:
```
ALERT! /dev/disk/by-uuid/94a5bb9b-d671-4aa3-819d-6e320f8acd15 does not exist.
Dropping to a shell!
(initramfs)
```

Tried a couple of re-installs.  First time I just reformatted /dev/sda4.  Second time I deleted /dev/sda4 which resulted in the creation of /dev/sda6

Did an ls -al /dev/disk/by-uuid and 94a5bb9b-d671-4aa3-819d-6e320f8acd15 is present:
```
<me>@ubuntu14:~$ ls -al /dev/disk/by-uuid
total 0
drwxr-xr-x 2 root root 160 Dec 25 19:09 .
drwxr-xr-x 6 root root 120 Dec 25 19:08 ..
lrwxrwxrwx 1 root root  10 Dec 25 19:09 1EC85BD6C85BAB33 -> ../../sda1
lrwxrwxrwx 1 root root  10 Dec 25 19:09 2A8A9FFB8A9FC1AD -> ../../sda3
lrwxrwxrwx 1 root root  10 Dec 25 19:09 4E1AEA7B1AEA6007 -> ../../sdb1
lrwxrwxrwx 1 root root  10 Dec 25 19:09 94a5bb9b-d671-4aa3-819d-6e320f8acd15 -> ../../sda6
```

Did some research and found a few things to check.  

```
<me>@ubuntu14:~$ sudo blkid
[sudo] password for <me>: 
/dev/sda1: LABEL="System Reserved" UUID="1EC85BD6C85BAB33" TYPE="ntfs" 
/dev/sda2: UUID="F298678998674B65" TYPE="ntfs" 
/dev/sda3: UUID="2A8A9FFB8A9FC1AD" TYPE="ntfs" 
/dev/sda5: UUID="e6050779-7b44-48e4-b05f-dfc19a4a537f" TYPE="swap" 
/dev/sda6: UUID="94a5bb9b-d671-4aa3-819d-6e320f8acd15" TYPE="ext4" 
/dev/sdb1: LABEL="My Passport" UUID="4E1AEA7B1AEA6007" TYPE="ntfs"
```

```
<me>@ubuntu14:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=94a5bb9b-d671-4aa3-819d-6e320f8acd15 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=e6050779-7b44-48e4-b05f-dfc19a4a537f none            swap    sw              0       0
```

```
<me>@ubuntu14:~$ blkid -U 94a5bb9b-d671-4aa3-819d-6e320f8acd15
/dev/sda6
```

So far, so good.  Everything seems to be in order. 

Then I did a "sudo fdisk -l" and found this?  Does the asterisk in the "boot" column for /dev/sda1 indicate that it's the boot partition (see below)?  There seem to be a couple other worry items in the output as well:
- The last couple lines of the output have /dev/sdb1 (the USB 1 TB drive I mentioned earlier) listed under "Device Boot" 
- Partition table entries are not in disk order

```
<me>@ubuntu14:~$ sudo fdisk -l
[sudo] password for <me>: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x67b5e83f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      718847      358400    7  HPFS/NTFS/exFAT
/dev/sda2          718848  1747800063   873540608    7  HPFS/NTFS/exFAT
/dev/sda3      1952600064  1953521663      460800   27  Hidden NTFS WinRE
/dev/sda4      1747802110  1952600063   102398977    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5      1936603136  1952600063     7998464   82  Linux swap / Solaris
/dev/sda6      1747802112  1936603135    94400512   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000170586112 bytes
255 heads, 63 sectors/track, 121597 cylinders, total 1953458176 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00023f15

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1953458175   976728064    7  HPFS/NTFS/exFAT
```

Saw some mount commands listed [here]("http://askubuntu.com/questions/516217/alert-dev-disk-by-uuid-xxxxxxxxx-does-not-exist-dropping-to-a-shell") that may correct the problem but being that I have data I cannot lose on the Windows partitions, I decided I'd better seek guidance. :) 

Finally, after typing exit from the initramfs prompt the image actually booted and I'm able to log in. That made me wonder whether if the cause was what the message warned me about in the first place and I tried adding rootdelay=10 to /etc/default/grub, grub-update and reboot but no luck.  The grub-update did add Windows to the boot menu though (maybe that's what the * above for /dev/sda1 is for).

My head is spinning.  :)

What's my ask?
- How can I get a clean boot without the !ALERT message?
- Should I be worried that Grub has my Windows 10 partition listed as Windows 8 (was updated from 8 to 10).  When I tried to boot it Windows started to repair the file system so I shut it off.  Deal with that later

Thanks in advance for the help!

---

### Post by Bucky Ball on 2015-12-25
Welcome. Please use code tags for terminal output. Easier to read, neater, space saving. See last link in my signature. I have done one output in your post as an example. :)

Nothing to help at this point, but will say this: 10Gb is a bit modest (where do you intend to store your personal data?) and you don't need anything like 8Gb /swap. 2Gb is fine unless you intend hibernating with a heap of stuff going on. Don't need it. /swap, under normal circumstances, will probably barely ever get used anyway. 

You want 20-25Gb for a Ubuntu install, just the OS, as your install will grow as you add more apps, then you need somewhere for your personal data. If you want to share it with Windows you need to create an NTFS partition that both Win and Ubuntu can read and write to. If you already have an NTFS data partition, NOT the Win OS partition, then you can use that (there are a few ways of doing this, and one of them is symlinks).

---

### Post by dgshaver on 2015-12-25
Thanks for the pointers!

I think **/dev/sda6 **(OS and data) is ~90GB?
```

<me>@ubuntu14:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda6        89G  4.0G   81G   5% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            7.8G  4.0K  7.8G   1% /dev
tmpfs           1.6G  1.5M  1.6G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            7.8G  220K  7.8G   1% /run/shm
none            100M   44K  100M   1% /run/user
/dev/sdb1       932G  560G  372G  61% /media/<me>/My Passport

```

---

### Post by ubfan1 on 2015-12-26
Right, 90G.  Note the partitioning is the MSDOS type, not gpt, so this not a UEFI machine, but running W10 upgraded from W8.  Implying this was not a preinstalled W8 on this machine.   Not the situation most people would be familiar with, but perfectly usable.

---

### Post by dgshaver on 2015-12-26
Thanks.  Here's a pastebin link to boot-repair BootInfo summary:
[http://paste.ubuntu.com/14214151/](http://paste.ubuntu.com/14214151/)

---

### Post by oldfred on 2015-12-26
Ubuntu/grub does not use boot flag.
Windows (to directly boot with its boot loader) must have boot flag on the primary NTFS partition with the boot files. Running Boot-Repair will usually copy those boot files to main install also, so grub2's os-prober finds both to add to boot menu.
With UEFI boot, boot flag has totally different meaning, but must only be on the ESP - efi system partition. 

Grub2's os-prober is not updated, yet to see Windows 10 descriptions. It usually checks for all  types and if no match just calls it recovery partition.

You must have Windows fast start up or always on hibernation off, if you are dual booting.
Leaving that on may create issues, or do you have BIOS setting for hard drive in IDE, not AHCI? Older systems needed IDE for very old drives. And some of those old systems could not boot from files beyond about 137GB on drive. IDE setting may replicate that.

---

