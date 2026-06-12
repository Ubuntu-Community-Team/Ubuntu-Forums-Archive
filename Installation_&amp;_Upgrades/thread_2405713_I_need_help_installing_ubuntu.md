---
title: "I need help installing ubuntu"
date: 2018-11-10
forum: Installation &amp; Upgrades
---

### Post by dehlord on 2018-11-10
Hello! I decided to use ubuntu as my main OS but i didn't know it was this hard to get all things running. I have 1 ssd(120gb intel e5400s) and 1 hdd(1 tb wd black) and i want my ubuntu and apps to be on the ssd and on the hdd everything else (downloads, movies, music, etc). I have googled a lot about this but nobody said 
exactly what you need to do. How should i make my partitions? (/root, /swap, etc) and what drivers do i need to install?

Thank you.

---

### Post by TheFu on 2018-11-10
Welcome to the forums.

In order to help, we need some facts about your system.

First, is ubuntu already installed or not?

Second, how much Unix-like system knowledge do you have?  Windows won't help with most of this, since Windows does things very differently at this level.

Have you tried running it from the install media using the "Try Ubuntu" option?  That will provide a good idea whether any of your specific hardware will have troubles or not.  It isn't 100%, but if it works in the installer environment, then you can get it working again post-install.

As for partitioning, there are millions of different methods, each with pros/cons.

So, if you haven't installed, boot into the "Try Ubuntu" environment and install a package called inxi.  
```
$ sudo apt install inxi
```
Then run it with a few options -** inxi -Fz** and post the output back here as text using "code tags" like I did just above.  Things line up better that way and are much, much, easier to read.

If you haven't already installed, there are a few ideas worth understanding.  The best way is to plan to do a few installations to see how it turns out.  Nothing can replace that and installations only require about 15 minutes when you don't have to worry about wiping data or restoring anything.

Anyway, answer those 4 things and we can get started.  Based on your current skills, we can recommend beginner or intermediate level setups. It is important.

---

### Post by mitesh.agrwl on 2018-11-10
Hi,

Is there any plan to use other OS like Windows or Mac along with Ubuntu. If, yes please mention the disks on which they are installed. For a better insight run

```
`$ sudo fdisk -l
```

from a live usb/cd and paste the output here. The Fu has given better idea. Something new to learn!

---

### Post by dehlord on 2018-11-10
Yes, i've already installed ubuntu.
I don't have any knowledge in Unix-like systems.
Yes, i tried to run it from "Try Ubuntu" option and it works.
When i installed this version of Ubuntu, i got some errors regarding "/boot" and after something appeared on the screen saying xxx hasn't been found but it dissapeared in 2 seconds and ubuntu booted.
I'd like everything to be just right but it's very confusing :D what partitioning method do you recommend? I will use this PC for browsing,movies, maybe some games and programming.
I also formated my usb as gpt partition

---

### Post by dehlord on 2018-11-10
> **mitesh.agrwl said:**
> Hi,

Is there any plan to use other OS like Windows or Mac along with Ubuntu. If, yes please mention the disks on which they are installed. For a better insight run

```
`$ sudo fdisk -l
```

from a live usb/cd and paste the output here. The Fu has given better idea. Something new to learn!

No, i want to use Ubuntu alone.

---

### Post by TheFu on 2018-11-10
Please provide the requested information.  When posting errors, please be EXACT.  

Some overview information to help with acclimation:
* [http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html)
* [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)
Those will help with some basic understand that people new to Linux lack.

---

### Post by dehlord on 2018-11-10
> **TheFu said:**
> Please provide the requested information.  When posting errors, please be EXACT.  

Some overview information to help with acclimation:
* [http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html)
* [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)
Those will help with some basic understand that people new to Linux lack.

```

ubuntu@ubuntu:~$ sudo apt install inxi
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package inxi

```

```

ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/loop0: 1.8 GiB, 1905549312 bytes, 3721776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 87.9 MiB, 92123136 bytes, 179928 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 140.9 MiB, 147722240 bytes, 288520 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 2.3 MiB, 2355200 bytes, 4600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 13 MiB, 13619200 bytes, 26600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 14.5 MiB, 15208448 bytes, 29704 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 3.7 MiB, 3878912 bytes, 7576 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 42.1 MiB, 44183552 bytes, 86296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 514B5D0A-1F40-4BD0-880D-3FBEF6F5A635

Device     Start        End    Sectors   Size Type
/dev/sda1   2048 1953523711 1953521664 931.5G Linux filesystem


Disk /dev/sdb: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 8B457473-332C-4EF0-AF20-3DBC3C24CEF5

Device     Start       End   Sectors   Size Type
/dev/sdb1   2048 234440703 234438656 111.8G Linux filesystem


Disk /dev/sdc: 7.5 GiB, 8054112256 bytes, 15730688 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 4758D7FA-3FAF-4CDF-9E6E-393CA6BD3F96

Device     Start      End  Sectors  Size Type
/dev/sdc1   2048 15730654 15728607  7.5G Microsoft basic data

```

---

### Post by TheFu on 2018-11-10
Well, if inxi isn't available to be installed, there's something odd happening with the setup. It was enabled on all my recent desktop installs.

```
$ sudo apt-cache policy inxi
inxi:
  Installed: 2.2.35-0ubuntu1
  Candidate: 2.2.35-0ubuntu1
  Version table:
 *** 2.2.35-0ubuntu1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/universe i386 Packages
        100 /var/lib/dpkg/status
```
shows it is in the "universe" repo.  Please check that it is enabled on your system and try to install again.  The apt-cache command is handy for things like this, BTW.

The output should look like this:```

$ inxi -Fz
System:    Host: cb35 Kernel: 4.15.0-38-generic x86_64 (64 bit)
           Desktop: Openbox 3.6.1 Distro: Ubuntu 16.04 xenial
Machine:   System: GOOGLE (portable) product: Gandof v: 1.0
           Mobo: GOOGLE model: Gandof v: 1.0
           Bios: coreboot v: MrChromebox date: 02/04/2018
CPU:       Dual core Intel Core i3-5015U (-HT-MCP-) cache: 3072 KB 
           clock speeds: max: 2100 MHz 1: 857 MHz 2: 918 MHz 3: 972 MHz
           4: 815 MHz
Graphics:  Card: Intel Broadwell-U Integrated Graphics
           Display Server: X.Org 1.19.6 drivers: (unloaded: fbdev,vesa)
           Resolution: 1920x1080@60.02hz
           GLX Renderer: Mesa DRI Intel HD Graphics 5500 (Broadwell GT2)
           GLX Version: 3.0 Mesa 18.0.5
Audio:     Card-1 Intel Wildcat Point-LP High Definition Audio Controller
           driver: snd_hda_intel
           Card-2 Intel Broadwell-U Audio Controller driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.15.0-38-generic
Network:   Card: Intel Wireless 7260 driver: iwlwifi
           IF: wlp1s0 state: down mac: <filter>
Drives:    HDD Total Size: 60.0GB (72.9% used)
           ID-1: /dev/sda model: SB_M2_SSD size: 60.0GB
Partition: ID-1: / size: 51G used: 37G (78%) fs: ext4 dev: /dev/dm-1
           ID-2: /boot size: 473M used: 147M (33%) fs: ext2 dev: /dev/sda2
           ID-3: swap-1 size: 4.16GB used: 0.60GB (14%) fs: swap dev: /dev/dm-2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   None detected - is lm-sensors installed and configured?
Info:      Processes: 194 Uptime: 5 days Memory: 2551.6/3814.7MB
           Client: Shell (bash) inxi: 2.2.35 
```
Having that is pretty handy. yes?  The -z option removes stuff that might give away privacy.

I prefer to install an encrypted setup and LVM (Logical Volume Manager).  To see how that layout works, 
```
$ lsblk 
NAME                          MAJ:MIN RM  SIZE RO TYPE  MOUNTPOINT
sda                             8:0    0 55.9G  0 disk  
&#9500;&#9472;sda2                          8:2    0  488M  0 part  /boot
&#9500;&#9472;sda3                          8:3    0 54.9G  0 part  
&#9474; &#9492;&#9472;sda3_crypt                253:0    0 54.9G  0 crypt 
&#9474;   &#9500;&#9472;ubuntu--vg-root         253:1    0   51G  0 lvm   /
&#9474;   &#9492;&#9472;ubuntu--vg-swap_1       253:2    0  3.9G  0 lvm   [SWAP]
&#9492;&#9472;sda1                          8:1    0  512M  0 part  /boot/efi
```

This shows that sda3 is encrypted and that LVs (Logical Volumes) vg-root and vg-swap are held inside.  To see the used storage:
```
$ df -Th
Filesystem                        Type      Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root       ext4       51G   37G   11G  78% /
/dev/sda2                         ext2      473M  147M  302M  33% /boot
/dev/sda1                         vfat      511M  4.5M  507M   1% /boot/efi
istar:/DD                         nfs       3.5T  3.4T  140G  97% /DD
istar:/D                          nfs       3.5T  3.4T   85G  98% /D
istar:/misc/D5                    nfs       3.5T  3.3T  231G  94% /misc/D5 
```
I removed the non-important mounts - all the loop, tmpfs, and control group devices. These don't actually use storage since they are virtual file systems.  What is shown above is that the system is EFI booting, has a separate /boot/, partition which isn't encrypted, and a / logical volume which is inside an encrypted partition.  There is 37G available, so if I wanted, I could reduce / to be 25G in size (which is generally what I do for systems with lots of storage, then have separate /home/ LV to hold personal documents and settings for each userid on the system.
You can also see 3 NFS mounts for remote storage. Each is 3.5TB in size, so when this device is on the LAN, is has access to plenty of storage hosted on the "istar" NFS server.

If I had more storage, even 120G on an SSD, then I'd allocate it this way:
```

/boot - 1G    # this is 2x the default size.  Kernels go here and it used to be common to fill it up and have patching fail.
/boot/EFI - 512MB  # Minimal size for EFI. It is shared across all installed OSes.
/ - 25G   # having just 25G for the OS and programs is more than sufficient on Ubuntu. Actually, 15G should be sufficient.
/var - 10G # keeping /var/ on a separate partition is a security thing.
/home - the remaining ; unless I needed it for something else.
```

If I had a 2nd HDD, then I'd put /home/ or /Data/ onto it.  I would NOT span 2 disks into a single LV, though that is possible.   In Unix, an empty directory is all that is needed to provide a "mount point" for any storage.  The storage can be a partition or an LV. Doesn't matter.  Mounting for permanent storage is done in the /etc/fstab.  There are how-to guides for accomplishing that.

I would NOT allocate all the storage on the SSD.  I would leave at least 2-10G free to be added where needed later.  This is something that LVM makes easy without much planning. Simple partitioning without using LVM makes doing that much harder. Shifting an entire partition or 3 might be necessary.  I'd rather have a storage shortage that is easy to fix as a warning to get more soon, but not be completely trapped by not having any to allocate immediately.

All of this assumes that other storage is available to backup the necessary files each disk can fail at any time.  Earlier this year, the SSD in this machine failed.  It was 120G and less than 3 yrs old.  My backups made the recovery pretty easy after I swapped out the failed SSD for a new one even though it was 50% smaller.

But all the LVM stuff is probably more complexity than someone new to Linux should attempt.  It provides great flexibility at the cost of increased complexity.

Anyway, posting my real system info might be helpful.  Or not.   But let's start with inxi first, please.

---

