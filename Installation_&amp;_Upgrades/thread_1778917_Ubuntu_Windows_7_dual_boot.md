---
title: "Ubuntu Windows 7 dual boot"
date: 2011-06-09
forum: Installation &amp; Upgrades
---

### Post by ufarmer on 2011-06-09
Hi,

I have Windows 7 already installed on my machine and I am trying to set up a dual boot with Ubuntu 11.04.

My previous experience with a dual boot was with Windows XP and Ubuntu 9.04.  In that case Windows was already installed and I booted from the Ubuntu CD and used the Ubuntu installation utility to partitition the disk and set up the dual boot.

I am trying to do the same thing now.  Namely boot from the Ubuntu 11.04 CD and use its utility to set up the dual boot.  However, when I boot from the CD I end up with a black text screen (after the splash screen) displaying:

udevd-work[122]: inotify_add_watch(6, /dev/dm-4, 10) failed: No such file or directory
udevd-work[122]: inotify_add_watch(6, /dev/dm-2, 10) failed: No such file or directory
udevd-work[122]: inotify_add_watch(6, /dev/dm-1, 10) failed: No such file or directory

BusyBox v1.17.1 (Ubuntu 1:1.17.1-10ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs) mount: mount /dev/loop0 on //filesystem.squashfs failed: Input/output error Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

None of this makes any sense to me.  Any advice is appreciated.

Thanks.

---

### Post by Neoxhadowespio on 2011-06-09
Maybe your ISO was bad. Retry the download, preferably Ubuntu 10.10 simply because it is more stable and because of a better window manager (Unity is very restricted).

---

### Post by oldfred on 2011-06-09
/dev/dm-4
Are you running LVM? I do not think the lvm2 driver is installed by default on the liveCD. You may have to use the alternative installer.

---

### Post by ufarmer on 2011-06-11
I re-downloaded 11.04 and this time the installation procedure began.  However, it did not present me with the graphical utility for resizing the existing Windows 7 partition and installing Ubuntu in the free space.  In fact it did not appear to be aware of Windows 7 at all.  I tried 10.10 with exactly the same results.  I also tried 9.04 (which worked with XP) but the installer claimed there were no other OSes on the computer.

Any advice is appreciated.

Regards.

---

### Post by oldfred on 2011-06-11
Post this:

```
sudo fdisk -lu
```

Often the part of gparted that is in the installer will not see partitions if you have used all 4 primary partitions. Sometimes gparted will not see a drive if the partition table has a bad entry.

---

### Post by ufarmer on 2011-06-11
I tried to run Ubuntu off of the disk but I couldn't find any way to get a terminal!  I tried to launch the GParted application from the desktop but it caused the system to crash.

Do you think it might work if I were to shrink the Windoze partition using Windoze?

Regards.

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **ufarmer said:**
> I tried to run Ubuntu off of the disk but I couldn't find any way to get a terminal!  I tried to launch the GParted application from the desktop but it caused the system to crash.

Do you think it might work if I were to shrink the Windoze partition using Windoze?

Regards.

[http://www.youtube.com/watch?v=GhnLk3gviWY](http://www.youtube.com/watch?v=GhnLk3gviWY)

She'll show you how to resize windows and install it that way.

---

### Post by YesWeCan on 2011-06-11
> **ufarmer said:**
> I tried to run Ubuntu off of the disk but I couldn't find any way to get a terminal!  I tried to launch the GParted application from the desktop but it caused the system to crash.

Do you think it might work if I were to shrink the Windoze partition using Windoze?

I would shrink using Windows anyhow. Maybe do a defrag first to make efficient use of space.

This is not the cause of your other problems, tho. I recently had a problem of my disk not showing up at all in the 11.04 installer and it turned out to be because of an old fakeraid block on the disk. I had to use 'sudo dmraid -E -r /dev/sda' to fix it. It was weird - the drive did not appear at all in the installer although it was seen plainly by fdisk and gparted.

If you are finding 11.04 hard to navigate, you could run a 10.10 live CD instead, install from it and then upgrade to 11.04 in situ. (or just keep 10.10 as some have recommended ;) )

---

### Post by ufarmer on 2011-06-11
I have four 1TB hard drives in a RAID 10 but it is managed by the hardware.  So shouldn't this just present itself as a single 2TB partition?  I am just wondering if the RAID might be causing my problems too.

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **ufarmer said:**
> I have four 1TB hard drives in a RAID 10 but it is managed by the hardware.  So shouldn't this just present itself as a single 2TB partition?  I am just wondering if the RAID might be causing my problems too.

Who did the raid installation last time?

---

### Post by ufarmer on 2011-06-11
I had it done by a technician (I am a hardware noob) but I know that there is a BIOS setting for choosing RAID types so I figured it was all hardware managed.  In Windoze 7 they have installed a RAID tool called Intel Matrix Storage Console but I don't know anything about it so I haven't touched it.

---

### Post by YesWeCan on 2011-06-11
> **ufarmer said:**
> I have four 1TB hard drives in a RAID 10 but it is managed by the hardware.  So shouldn't this just present itself as a single 2TB partition?  I am just wondering if the RAID might be causing my problems too.
Yes, this is indeed a crucial piece of information! :)
It sounds like you have a "fakeraid" set up (which is why Intel Matrix is required). You are not running a full hardware RAID by the sounds of it, otherwise all would be fine.

This makes things complicated. You are now talking about installing Ubuntu to a fakeraid: see [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by ufarmer on 2011-06-11
Thanks!  I'll check out the mobo and ask the technician to be sure if it's a hardware RAID or not.

---

### Post by YesWeCan on 2011-06-11
I think you would know if you had hardware RAID, you would have a card in there like this: [http://www.adaptec.com/en-us/products/controllers/hardware/sas/value/sas-6805/](http://www.adaptec.com/en-us/products/controllers/hardware/sas/value/sas-6805/)
With HW RAID the OS doesn't even realise there is a RAID at all - it just sees a disk.

There are basically 2 types, software and hardware. You seem to have Windows software RAID which happens to require some minor hardware components on the mobo to work. Linux software RAID, mdadm, requires no special hardware support. It is very misleading when a mobo claims to have RAID - what it means is that it has support for Windows software RAID.

---

### Post by ufarmer on 2011-06-11
Yes, I have been reading the mobo specs and I think you are completely right about the RAID.  Which is really annoying since one of the reasons I bought it was because I thought it had a hardware RAID.

---

