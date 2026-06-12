---
title: "Dual Boot To Single Boot 12.04 - gparted or reinstall?"
date: 2012-06-22
forum: Installation &amp; Upgrades
---

### Post by Rob Sayer on 2012-06-22
I have a new cold install of 12.04, dual boot with Windows 7.  Installed from LiveCD.  Everything seems to work fine so far.

I want to yank the Windows on this one ... maybe make my newer machine dual boot when I install  12.04 on it.

Should I just reinstall or use gparted?  Would reinstalling give me better performance?  It seems easier.

---

### Post by wilee-nilee on 2012-06-22
Could you use this command in ubuntu to show what is actually on the HD, and post it.

```
sudo fdisk -lu
```

---

### Post by Rob Sayer on 2012-06-22
Thanks.  Here you go (hope I get the quote part right):

> Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x54dc1e55

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2          409600   198091140    98840770+   7  HPFS/NTFS/exFAT
/dev/sda3       198092798   488396799   145152001    5  Extended
/dev/sda5       198092800   482639871   142273536   83  Linux
/dev/sda6       482641920   488396799     2877440   82  Linux swap / Solaris

---

### Post by darkod on 2012-06-23
You can do it how ever you want.

A new reinstall taking the whole hdd would work.

It would also work if you delete sda1 and sda2 and expand the ubuntu partitions. But since sda5 and sda6 are logical partitions inside the extended partition (sda3), you will have to expand the extended first to include the unallocated space, and then sda5.

Also, that would leave your hdd with only an extended partition which is weird to me because I only use the extended if I have used up three primary partitions, but the hdd can work with only extended on it. No rules against that scenario.

So, it's up to you.

You might wanna consider making a new clean install and using the manual method so that you can create a separate /home partition.

---

### Post by Rob Sayer on 2012-06-23
Actually, I am going to do a full reinstall from cd ... I only installed ubuntu at all 5 days ago.  I have a newer machine (that's next) so I didn't have a lot of data to juggle around.

Basically I've mostly been getting comfortable with the file system.  There's not may programs to reinstall, and I was using most all of them in windows anyway.

So it's really not that much work.  Thanks anyway for your time.

---

