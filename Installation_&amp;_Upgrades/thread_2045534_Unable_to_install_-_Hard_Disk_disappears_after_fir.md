---
title: "Unable to install - Hard Disk disappears after first try"
date: 2012-08-21
forum: Installation &amp; Upgrades
---

### Post by cheenu_sri on 2012-08-21
Hi,

I am trying to install Ubuntu 12.04 32 bit onto a relatively old computer (2.6ghz Pentium D, 1 gig ram)

The problem I am facing is that the Hard Disk (80 GB - SATA, no AHCI) isn't getting detected properly.

The reason why I mention "detected properly" is that, if I do a live boot, I can see the 80 gb unused in disk utility, but cannot format it (as it stays busy forever).

With regard to the installer(FYI, installing through USB), it says that I have enough space (looking at my 80 gig hdd I suppose), and lets me proceed till the partition screen - at which point it only shows my 2 gig USB flash drive as an option, and once I come back to the first screen, it no longer shows a tick mark on space available (now it says that I dont have enough space).

After the installation fails, the disk util no longer shows the 80 gb hdd, instead just shows /dev/sda (the 80 gig volume in the hdd is/supposed to be on /dev/sda1)

GParted refreshes forever, and even fdisk -l just stalls.

I am really sorry if I have posted in the wrong area, or If this problem has been solved earlier (none of them match OR I am blind) - please guide me appropriately AND/OR move this thread appropriately.

Thanks in advance!

---

### Post by Bucky Ball on 2012-08-21
Welcome. Is the disk unmounted? When you are booted into the LiveCD, launch Gparted and right click, unmount it. 

You don't need to worry about partitioning the drive before you install. You can let Ubuntu do it automatically or you can do it manually by selecting 'Something Else' when you get to that part of the install. 

If the disk is free space that is a good thing. ;)

---

### Post by darkod on 2012-08-21
One reason the installer might not see the disk while fdisk and parted do, is if it was used in raid before and has meta data remains. The installer ignores disks with meta data, so everything will look normal until you reach the partitioning step.

You can double check existence (and remove it) of meta data with:
sudo dmraid -E -r /dev/sda

You can run it from live mode as long as it sees the disk as /dev/sda.

---

### Post by cheenu_sri on 2012-08-21
Aren't all disks mounted during live-cd's boot? Should I mount it explicitly?

With regard to partitioning before install - I try it only because the install fails - Ubuntu doesn't show me my 80 gig hdd on the partition screen and just shows my 2 gig USB (but somehow it did see my 80 gig hdd in the beginning cuz it said that there is 4.4 gig space!! SO, I assumed it could be a silly problem, and deleting the partition could help?
Quoting:
"With regard to the installer(FYI, installing through USB), it says that I  have enough space (looking at my 80 gig hdd I suppose), and lets me  proceed till the partition screen - at which point it only shows my 2  gig USB flash drive as an option, and once I come back to the first  screen, it no longer shows a tick mark on space available (now it says  that I dont have enough space)."

---

### Post by cheenu_sri on 2012-08-21
Yes, I know about RAID, so I removed dmraid and tried - still the same. Another thing. GParted is permanently on "Scanning all devices..." even before I try to install.

---

### Post by darkod on 2012-08-21
No, disks are not mounted during live cd boot. But on occasions if there is existing swap partition on the disk, the live cd can use it to work faster and actually mount the swap partition.

But for installation the disk should not be mounted anyway, so that is not your problem.

There might be something messed up with the partitions or partition table, so Gparted is taking forever scanning it. If there is no important data on the disk, you can try writing new blank msdos table without opening Gparted, or nothing.

Simply boot into live mode with the cd, open terminal and use parted to write msdos table:
```
sudo parted /dev/sda
mklabel msdos
quit
```

That should write new clean empty msdos table.

After that try printing the disk partitions (there won't be any, just to see if it will display OK or get stuck) with:
```
sudo fdisk -l
sudo parted -l
```

Then if all looks good, you can give Gparted a go and see if it will display the disk without getting stuck.

It sounds to me like faulty disk. I have two of these at home. Often they look good, but as soon as you intend reading or writing, it goes away. Since Gparted is intenting to read it, it just looks forever...

---

### Post by cheenu_sri on 2012-08-21
> **darkod said:**
> No, disks are not mounted during live cd boot. But on occasions if there is existing swap partition on the disk, the live cd can use it to work faster and actually mount the swap partition.

But for installation the disk should not be mounted anyway, so that is not your problem.

There might be something messed up with the partitions or partition table, so Gparted is taking forever scanning it. If there is no important data on the disk, you can try writing new blank msdos table without opening Gparted, or nothing.

Simply boot into live mode with the cd, open terminal and use parted to write msdos table:
```
sudo parted /dev/sda
mklabel msdos
quit
```

That should write new clean empty msdos table.

After that try printing the disk partitions (there won't be any, just to see if it will display OK or get stuck) with:
```
sudo fdisk -l
sudo parted -l
```

Then if all looks good, you can give Gparted a go and see if it will display the disk without getting stuck.

It sounds to me like faulty disk. I have two of these at home. Often they look good, but as soon as you intend reading or writing, it goes away. Since Gparted is intenting to read it, it just looks forever...
"sudo parted /dev/sda" gets stuck. Doesn't complete...

---

### Post by darkod on 2012-08-21
> **cheenu_sri said:**
> "sudo parted /dev/sda" gets stuck. Doesn't complete...

Sorry, but it looks like it's faulty. The same happens to the two disks I mentioned.

Double check the cables, sata ports, connections, etc. But if all of that looks good and a simple parted command is getting it stuck, I don't think you can use it.

---

### Post by cheenu_sri on 2012-08-21
Thanks for your help.

However, "sudo parted /dev/sda" finally went through:
GNU Parted 2.3
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) mklabel msdos
Error: Input/output error during read on /dev/sda
Retry/Ignore/Cancel?

Do note that the hdd is intact - I was running Windows XP on it till about 5 hours back. I tried deleting the partition through diskutils (and hence, now diskutils no longer shows it as an NTFS partition - this is before I try to install)

I am sure that the cables are in-tact, cuz as I said, installation does detect it and it does tell me that I have the required free space - however things get messed up once I proceed, and then onwards even diskutils doesn't help - I have to reboot.

I can't believe this is such an edge case - weird!

---

### Post by cheenu_sri on 2012-08-22
Hi All.

I just confirmed it.

This is a genuine problem with only UBUNTU builds (same on LUBUNTU and LINUX MINT) - the hard disk is read fine by any other OS. I just installed Windows, OpenSuSE and even FreeBSD - all seem to read it properly. 

I don't know how to provide relevant information - but the Ubuntu programmers might want to resolve this genuine issue.

Last time I used Ubuntu was almost 2 years ago and have been using OS X since..., and just thought that I should make use of old hardware lying around - and once again, Ubuntu failed. Bid adieu to Ubuntu - never in my life ever again!!!!!!

---

### Post by Bucky Ball on 2012-08-22
Pity. Reasonably problem free for many of us. Anyhow, please mark thread as 'Solved', if it is, to help others. Good luck. ;)

---

