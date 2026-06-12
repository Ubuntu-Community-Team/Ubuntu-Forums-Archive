---
title: "Root home as one partition or two?"
date: 2019-08-29
forum: Installation &amp; Upgrades
---

### Post by concerro on 2019-08-29
I'm going to install Ubuntu. I don't know if I should just make a partition that counts as root and home or make them into two separate partitions. I don't know the pros and cons of this decision.

Some info about the situation:
This is a personal laptop. I will not be using multiple distros, and the setup is basic so no advanced RAID configurations or anything else that might be overly complicated. 

The priorities are performance and data security. If I have to give up one for the other I'm looking at being able to restore files and data if something goes wrong down the line. I'll give up a few seconds of bootup time for this. 

If you need more info I'm more than happy to answer more questions.

---

### Post by CatKiller on 2019-08-29
If you're only using one physical drive, then having a separate partition for /home gives one advantage: if you need to reinstall the OS your settings are still in the same place. Whether that is sufficient motivation to set things up that way is entirely down to how likely you think you'll be to need to reinstall the OS.

You'll need regular external backups of your data in either case.

---

### Post by concerro on 2019-08-29
Thanks. I'll do two partitions then. I'll have to purchase another HD just for backup.

---

### Post by guiverc on 2019-08-29
I suspect it's personal preference as to which is best for you.

 I prefer /home on a separate partition as if I should need to re-install the OS & don't want to risk anything there, I can install over / (and not use my /home, and it'll create a /home directory on the / partition) then restore the use of /home later myself.  This is particularly useful if you want to switch to another OS (not all have the features of Ubuntu's installer & only allow install with format; so a separate home in that case is a must if you want to keep your user data).

Having a single partition is simpler, and you don't have to worry about running out of space in one, and having plenty of space in the other (ie. you don't have decide sizes of each). 

If you have plenty of disk space, I opt for two partitions (/ & /home), but if my disk space is limited - I only then use a single partition.  *my 2c anyway*

---

### Post by crip720 on 2019-08-29
If you go with two partitions /root should be around 30GBs. /home depends on how much you download, but bigger(rest of disk) is usually better.

---

### Post by cruzer001 on 2019-08-29
If ever you decide to try other linux distros a /home partition can mess with you.  I prefer to leave home where it is and just have a backup of home on a second drive.  With any backup plan installed, I do not consider it necessary to have a /home partition.

---

### Post by TheFu on 2019-08-29
> **crip720 said:**
> If you go with two partitions /root should be around 30GBs. /home depends on how much you download, but bigger(rest of disk) is usually better.

/root is the directory where root's HOME is.
/  is the root directory for the system.

Whether someone needs multiple partitions or multiple LVM logical volumes for any Unix install depends on the purpose of the system, which programs will be run, how much total storage will be connected, and how often they might want to switch or add distributions to that system.

Allocations for me are always, always, about my backup plan.  Backing up a / that is 25G in size is much easier than backing up a / that is 2TB in size.  The type of data that each partition/LV contains determines the type of backups needed.  The RTO and RPO determine how often and what types of backups are necessary. You can look up those terms.

So, a concrete example.[B]
Requirements:[/B]
* Laptop with a 500G SSD; all laptops/portable storage must be fully encrypted.
* Only LTS releases will be installed. Perhaps 1 other small distro, in addition. 
* Used for email, web browsing, photo editing, video editing, systems management of other systems via Ansible, virt-manager, ssh
* Some light virtual machine use locally using KVM, libvirt and virt-manager. Always toy VMs. No VM backups needed.
* Some remote x2go access
* Some video and audio media enjoyment, but those are always copies. No media file backup needed.
* Prefer a swap partition/LV - 4.1G is the size needed regardless of system RAM; Hibernation NOT used.

[B]Storage Solution:
[/B]* Fully encrypted storage, in Ubuntu that uses LVM and sets up the EFI, boot, and OS to use the entire disk (16.04)
* The resulting storage layout shows my solution:
```
$ lsblk
NAME                      MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda                         8:0    0 465.8G  0 disk  
&#9500;&#9472;sda2                      8:2    0   732M  0 part  /boot 
&#9500;&#9472;sda3                      8:3    0 464.6G  0 part  
&#9474; &#9492;&#9472;sda3_crypt            253:0    0 464.6G  0 crypt 
&#9474;   &#9500;&#9472;ubuntu--vg-root     253:1    0    25G  0 lvm   /
&#9474;   &#9500;&#9472;ubuntu--vg-stuff    253:4    0   100G  0 lvm   /stuff
&#9474;   &#9500;&#9472;ubuntu--vg-swap_1   253:2    0   4.1G  0 lvm   [SWAP]
&#9474;   &#9492;&#9472;ubuntu--vg-home--lv 253:3    0    75G  0 lvm   /home 
&#9492;&#9472;sda1                      8:1    0   512M  0 part  /boot/efi

$ dft  # df -hT with uninteresting loop/etc removed
Filesystem                      Type  Size  Used Avail Use% Mounted on
/dev/sda2                       ext2  721M  185M  500M  27% /boot
/dev/sda1                       vfat  511M  3.7M  508M   1% /boot/efi
/dev/mapper/ubuntu--vg-root     ext4   25G   12G   12G  52% / 
/dev/mapper/ubuntu--vg-home--lv ext4   74G   21G   51G  29% /home 
/dev/mapper/ubuntu--vg-stuff    ext4   99G  367M   93G   1% /stuff

$ sudo vgs
  VG        #PV #LV #SN Attr   VSize   VFree     
  ubuntu-vg   1   4   0 wz--n- 464.54g 260.08g

$ sudo lvs
  LV      VG        Attr       LSize   Pool Origin Data%
  home-lv ubuntu-vg -wi-ao----  75.00g
  root    ubuntu-vg -wi-ao----  25.00g 
  stuff   ubuntu-vg -wi-ao---- 100.00g
  swap_1  ubuntu-vg -wi-ao----   4.10g   

```

/boot is larger than normal. 500MB was never quite enough.  A full /boot usually happens during a kernel update. Failure is not an option at that point for me.

/  - 25G.  I've never needed more unless /var/ had some huge demands like a Plex Server or virtual machines. No those systems, either create a separate /var/ partition/LV and mount it or use symbolic linking to move the huge storage stuff elsewhere. Daily, automatic, versioned backups for selected directories.

/home - above it is clearly much larger than really needed.  Just because the disk HAS extra storage, that doesn't mean I should allocate it before it is needed.  Because I use LVM+ext4, adding unallocated storage to an LV is trivial while the system is running. The **vgs** command shows that over 200GB of storage isn't allocated to LVs. It can be added where needed, as needed.  Daily, automatic, versioned backups for the entire thing.

/stuff - this is where temporary media files (like for travel entertainment) get placed. It is also where temporary processing files can be placed for a few hours.  NO Backups of data from here.

I use rdiff-backup for the versioned backups and rsync for mirroring media files that don't change and tend to be huge. It wouldn't be practical to have versioning on 10GB files, right?

If I want to install another  Linux distro, I'd just make a new LV for that OS/Apps, but keep using the current swap LV and might mount the /home/ - maybe, maybe not.

---

### Post by ajgreeny on 2019-08-29
Another alternative is to keep /home within root and create a separate partition for data, and then use soft links to data folders in that into your home; it will appear to you that the flders are sitting in your home as normal, even though they are actually sitting in the separate data partition.

I have used that system many times in the past when I was using a variety of distros which could potentially have caused problems as a result of configuration differences, if I had used a shared /home partition.

---

### Post by TheFu on 2019-08-29
> **ajgreeny said:**
> Another alternative is to keep /home within root and create a separate partition for data, and then use soft links to data folders in that into your home; it will appear to you that the flders are sitting in your home as normal, even though they are actually sitting in the separate data partition.

I have used that system many times in the past when I was using a variety of distros which could potentially have caused problems as a result of configuration differences, if I had used a shared /home partition.

I use this technique too, sometimes.  Depends on whether the configuration files/settings are important to keep between installations.  Sometimes only the data matters, not the configs.

It is nice to have the flexibility.

---

