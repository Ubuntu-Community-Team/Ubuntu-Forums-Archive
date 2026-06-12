---
title: "How to setup Bare Metal Ubuntu 16.04 Server (Vultr) to RAID0 with mdadm"
date: 2020-12-25
forum: Installation &amp; Upgrades
---

### Post by onurkeles on 2020-12-25
Hello all,

I have been researching about mdadm to set my server to RAID0. I have 2x240gb and I would like to set it up to RAID0. Here are information about the server. Any guide or help are appreciate it.

thanks

```
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
unused devices: <none>
```

```
fdisk -l
Disk /dev/sdb: 223.6 GiB, 240057409536 bytes, 468862128 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xef997454


Device     Boot Start       End   Sectors   Size Id Type
/dev/sdb1        2048 468862127 468860080 223.6G 83 Linux




Disk /dev/sda: 223.6 GiB, 240057409536 bytes, 468862128 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x73ac5079


Device     Boot Start       End   Sectors   Size Id Type
/dev/sda1  *     2048 468862094 468860047 223.6G 83 Linux



```

---

### Post by TheFu on 2020-12-26
Support for 16.04 ends in a few months. Today, 20.04 mnimal should be used and, if absolutely needed, 16.04 minimal would go into an lxd container.  There are many reasons for going this direction.

As for vultr, VPS setup is different enough from what normal ubuntu does as to need specific instructions. Seek those out on vltr support. Knowing little about vultr, I don't know how to accomplish this, but I'd probably try by pre-setting up lvm as striped, and would avoid mdadm. The, I'd attempt to convince ubuntu server to "custom install" into existing storage.  Plan on a  few attempts to be necessary. Ths assumes you don't go the lxd route, which would provide easer RAID setup wth any block devices.

Plus with lxd+zfs, you can easily clone the container to any other lxd platform.

With the risk of data loss effectively doubled, be 100% certain you have any important data, settings, and programs backed up.

---

### Post by onurkeles on 2020-12-26
> **TheFu said:**
> Support for 16.04 ends in a few months. Today, 20.04 mnimal should be used and, if absolutely needed, 16.04 minimal would go into an lxd container.  There are many reasons for going this direction.

As for vultr, VPS setup is different enough from what normal ubuntu does as to need specific instructions. Seek those out on vltr support. Knowing little about vultr, I don't know how to accomplish this, but I'd probably try by pre-setting up lvm as striped, and would avoid mdadm. The, I'd attempt to convince ubuntu server to "custom install" into existing storage.  Plan on a  few attempts to be necessary. Ths assumes you don't go the lxd route, which would provide easer RAID setup wth any block devices.

Plus with lxd+zfs, you can easily clone the container to any other lxd platform.

With the risk of data loss effectively doubled, be 100% certain you have any important data, settings, and programs backed up.


Hi TheFu, thanks for the reply. I have been using Vultr compute units and I was happy up until that Vultr support mentioned that they won't provide any support for software or boot RAID configurations. Their system setup is supporting only software RAID1, not RAID0. I tried to ask them but they just sent me link for mdadm. Anyways, I have been researching about mdadm and trying different options but so far no luck.

I am researching lxd platform but I need a lot of storage/RAM. It seems like a bit more costly. Is there company that you can recommend?

thanks and happy holidays

---

### Post by TheFu on 2020-12-27
I suspect you are thinking of storage like Windows does it, not how nix does it.Having the OS striped doesn't gain anything on SSD except complexity and higher failure risk. The OS can be minimal, then make the data storage striped using any method you like.  I'd use lvm for both the OS - this is a standard install optin, then create other PVs for the striped data storage. No need for mdadm, plus lvm is much more flexible.  

LXD is f/loss and has tiny overhead. Canonical is behind it. I only mentioned it if you actually needed an OS striped, but I doubt that is true. LXD would run under any Linux OS as a container. It is almost like a virtual machine, just 10x lighter.  Costly? You've lost me there. There is no cost.  **sudo snap install lxd**

Don't make things more complex than needed.

Heck, if you don't need striped storage, use lvm and concatenate the storage. This is trivial.  Splitting storage across 2+ disks is a terrible idea, but I doubt I can convince you of that.  The storage failure will, eventually.

---

### Post by onurkeles on 2020-12-27
yeah I misunderstood you. I am reading and learning more about LXD now. Yeah this way might be a lot better. Thanks for all the input The Fu

---

