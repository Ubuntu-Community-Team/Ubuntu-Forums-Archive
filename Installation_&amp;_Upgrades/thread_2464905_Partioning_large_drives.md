---
title: "Partioning large drives"
date: 2021-07-15
forum: Installation &amp; Upgrades
---

### Post by ooleyman on 2021-07-15
I have 2 2TB NVMe hard drives. I plan on using VMWare Workstation to virtualize Windows 10 for the "hopefully" rare times that I need Windows. I've not found any suggestions. The all point to having drives less than 500 GB or so. Where are programs and data stored?

---

### Post by scorp123 on 2021-07-15
> **ooleyman said:**
> Where are programs and data stored?

[https://www.howtogeek.com/howto/35676/how-to-choose-a-partition-scheme-for-your-linux-pc/]("https://www.howtogeek.com/howto/35676/how-to-choose-a-partition-scheme-for-your-linux-pc/")

---

### Post by TheFu on 2021-07-15
> **ooleyman said:**
> I have 2 2TB NVMe hard drives. I plan on using VMWare Workstation to virtualize Windows 10 for the "hopefully" rare times that I need Windows. I've not found any suggestions. The all point to having drives less than 500 GB or so. Where are programs and data stored?

These forums are full of people asking about "disk layouts."  Search for those threads. For example:
[Https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](Https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277)
So ... follow that layout for the OS, settings, etc. and have a place for "stuff". No need to allocate all the storage for use up front. If you decide to use ZFS or LVM for volume management, there are all sorts of things that can be done to efficiently use the storage. Going with simple partitions prevents those things.

How much do you know about Linux and besides running 1 VM, what is the purpose for all that storage?

IMHO, I can't imaging what I'd do with more than about 100G of NVMe storage on any Linux system.  The OS and programs just don't need that much space.  It isn't like Linux is as bloated as MS-Windows.  My main desktop uses 40GB of storage.  I keep files I'm not actively using on NFS storage which is available on the network.  All the other storage on the system is for "stuff" and considered unimportant.  The NAS has over 30TB of storage with primary and backup disks.  That data is completely different from the OS, settings, applications, running on my desktop.

With 20.04 and later, Ubuntu desktops have bloated up for a number of reasons, so while the /boot, /boot/efi, recommendations are all the same, the / (root partition/LV) should probably be 35-40GB now.  This assumes you'll create a separate swap partition/LV.

Disk layouts really should be about backup and recovery needs and about being able to reload the OS or upgrade the OS without impacting your personal files usually kept in /home/ somewhere.  /home should be a separate allocation.  /var may need to be separate, but that's a judgement call.  

On my VM hosts, keep storage just for VMs. For toy VMs that use file-based storage, I specifically add an LV with 150-200GB of storage where VMs are typically located.
```
$ df .
Filesystem                         Size  Used Avail Use% Mounted on
/dev/mapper/hadar--vg-libvirt--lv  173G  127G   37G  78% /var/lib/libvirt
```

For my production VMs, I provide direct LV storage to each VM.  That doesn't show up as mounted anywhere in the hypervisor host.  LV = Logical Volume, it is one of the 3 main objects that LVM uses. There are many, many, many, reasons to use LVM, but mostly for flexibility. The key with LVM is to never, ever, allocate all the storage. Adding more storage is 5 seconds on a running system and not having it all allocated means we can be very flexible about sizing.  If you do the install and check the "Use LVM" box, you'll get some flexibility, but the default setup over allocates storage for / massively by default.  I always go back immediately post-install and shrink / down, create a few other LVs, mount those where desired and still usually have 300+ GB left on the SSD for other needs.

---

### Post by ooleyman on 2021-07-16
Thank you very much for your quick reply, TheFu. I've been using Debian based distros on and off for about 10 years. I have that much space because I'm stuck in a nursing home rendered paraplegic and more by certain medical issues at age 46 and computers are my only link to the outside world and I've accumulated terabytes of data and I am like the hoarders you see on TV and cannot delete anything.

---

### Post by TheFu on 2021-07-16
> **ooleyman said:**
> Thank you very much for your quick reply, TheFu. I've been using Debian based distros on and off for about 10 years. I have that much space because I'm stuck in a nursing home rendered paraplegic and more by certain medical issues at age 46 and computers are my only link to the outside world and I've accumulated terabytes of data and I am like the hoarders you see on TV and cannot delete anything.

4TB really isn't much space.  The "data" areas really don't matter in the storage layout.  The core partitions/logical volumes for almost every system are the same, with just a few tiny tweaks that are almost always unimportant.  By using LVM, we can resize up slightly in 5 seconds. If using normal partitions, changing partition sizes is a big hassle, requires booting from a Live Ubuntu/Try Ubuntu flash drive, and likely hours of shifting partitions left or right on the disk.  LVM removes those issues, but there is a price.  A slight amount of added complexity.

In 25 yrs, I've never guessed correctly how much storage any partition/LV needs at installation time.  So my answer is simple.  Start with my best guess for what I need in the next 3 months for allocations, but have the ability to expand an LV easily when and where needed.

---

