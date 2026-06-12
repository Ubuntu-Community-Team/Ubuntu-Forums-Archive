---
title: "Re: Discussion - https://help.ubuntu.com/community/BootPartition"
date: 2020-03-03
forum: Installation &amp; Upgrades
---

### Post by freonpsandoz on 2020-03-03
From the instructions: "[COLOR=#333333][FONT=Ubuntu]Important: to resize Windows Vista/7/8 partitions, don't use gParted but Windows tools instead." I assume that this advice applies to Windows 10 also. If Windows was installed before Ubuntu, the normal configuration after installing Ubuntu for dual-boot will have the bootable Windows NTFS partition before the Ubuntu partition. Mine also has a 100MB "System Reserved" partition before the NTFS partition. I plan to use GParted to shrink and move the Ubuntu partition, then use Windows tools to expand the NTFS partition and move the "System Reserved" and the NTFS partition, leaving 1GB unused at the start. I then plan to use GParted to create a partition at the start and Boot Repair to make it the boot partition. Is this correct, or does the boot partition need to be placed *after* the "System Reserved" partition?  Thanks.

.[/FONT][/COLOR][ATTACH=CONFIG]285143[/ATTACH][COLOR=#333333][FONT=Ubuntu]
[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]

[/FONT][/COLOR]

---

### Post by jeremy31 on 2020-03-03
Split from an old thread at [https://ubuntuforums.org/showthread.php?t=2027546](https://ubuntuforums.org/showthread.php?t=2027546)

---

### Post by TheFu on 2020-03-03
I wouldn't use boot-repair for fixing anything anymore.  Just good for gathering information.

That is a bunch of risky steps.  Before starting, make 100% certain that you backup AND know how to restore everything you cannot lose.

I would expect to need grub-install, update-grub, perhaps mkinitramfs and to edit the fstab manually.  If the system doesn't boot when you are all done, have a "Try Ubuntu" flash drive ready AND test that it works before beginning. You'll need it to resize the Linux partitions anyway.

If you are using encryption or LVM2, things are a little more complex.

---

### Post by yancek on 2020-03-03
I don't really use windows so I'm not sure if moving the system reserved partition to a new location will create problems.  I'm not sure what the purpose of these changes is other than wanting to shrink the Ubuntu partition and enlarge one of your windows partitions.  The Disk management image you posted doesn't really give enough information to tell if this will be easily done.  Posting the output from fdisk or gdisk from your Ubuntu media would be more useful.

---

### Post by TheFu on 2020-03-03
> **yancek said:**
> I don't really use windows so I'm not sure if moving the system reserved partition to a new location will create problems.  I'm not sure what the purpose of these changes is other than wanting to shrink the Ubuntu partition and enlarge one of your windows partitions.  The Disk management image you posted doesn't really give enough information to tell if this will be easily done.  Posting the output from fdisk or gdisk from your Ubuntu media would be more useful.

Or better, **lsblk -e 7 -o name,size,type,fstype,mountpoint**
and perhaps** df -hT -x squashfs -x tmpfs -x devtmpfs** when the system is normally booted.

---

### Post by yancek on 2020-03-04
The fdisk command would be useful in that it shows the sectors and hence one can tell if partitions are contiguous.

---

### Post by TheFu on 2020-03-04
> **yancek said:**
> The fdisk command would be useful in that it shows the sectors and hence one can tell if partitions are contiguous.

Is there an option that will remove all loop device output from fdisk or parted commands?  Having those displayed are useless for storage. Just gets in the way of seeing the important data.

Normally, a **sudo fdisk -lm** would be my preference - then snaps came along and screwed the output.  Spent some time earlier this week looking for a non-perl/non-grep solution and didn't find one.  I'll try to make a 1-liner that only shows real storage.  Sorta like the **lsblk** command above removes all snap mounts, while keeping any LVM2 LVs.

---

### Post by SeijiSensei on 2020-03-04
> **TheFu said:**
> Is there an option that will remove all loop device output from fdisk or parted commands?  Having those displayed are useless for storage. Just gets in the way of seeing the important data.
I'm not sure I know what you're asking. If you specify a device with fdisk
```
sudo fdisk /dev/sdb
```
only the partition structure on that device is displayed. I've never seen any loop devices using fdisk.

---

### Post by TheFu on 2020-03-04
> **SeijiSensei said:**
> I'm not sure I know what you're asking. If you specify a device with fdisk
```
sudo fdisk /dev/sdb
```
only the partition structure on that device is displayed. I've never seen any loop devices using fdisk.

```
sudo fdisk -l
```
For when you don't know all the device names.

---

