---
title: "XP installer deleted an empty partition... now Grub won't load"
date: 2008-07-30
forum: Installation &amp; Upgrades
---

### Post by tnunamak on 2008-07-30
I had a swap partition along with two ext3 partitions, all inside an extended partition. I shrank one of the two partitions to free up 10 gb, then I loaded the windows installer to install XP. I created a partition from this empty space, which it called a raw partition, but it wouldn't let me format it. I suspect that this is because it's part of the extended partition. Unfortunately I couldn't figure out how to use GParted to move this free space to its own partition outside of the extended one.

I gave up for the time being, and rebooted, but now Grub doesn't load. My computer just hangs at a black screen with a blinking underscore. Did I overwrite the MBR?

What's the easiest way to fix this? If I get Grub back, how can I install xp on the empty space?

---

### Post by Pumalite on 2008-07-30
You can reinstall Grub, but first let's find out what you have in your drive:
Post:
sudo fdisk -lu
You can also use Super Grub to boot Ubuntu and find out if it's still there.

---

### Post by tnunamak on 2008-07-30
Thanks. Here it is

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe3b9e3b9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   195366464    97683201    f  W95 Ext'd (LBA)
/dev/sda5             126   145307924    72653899+  83  Linux
/dev/sda6       165790863   193406534    13807836   83  Linux
/dev/sda7       193406598   195366464      979933+  82  Linux swap / Solaris

```

---

### Post by Rallg on 2008-07-30
In general, a Windows installer will over-write your disk's MBR, and direct boot to Windows. You would then re-install Grub, which would recognize both Windows and Linux partitions.

To "move" the free space outside of the extended partition, you might have to move the space to the front or back of the partition, then resize the extended partition by moving its starting or ending point. The free space will then appear preceding the new start, or following the new end.

Keep in mind that you are probably limited to 4 primary partitions.

Whenever a partition (any kind of partition) is moved or resized, its UUID changes. The Grub menu.lst file identifies partitions by UUID, but GParted does not inform Grub of the changes. So, some user have to hand-edit menu.lst using the Ubuntu live CD (be sure that you are editing menu.lst on the hard drive). In your particular case, whenyou re-install Grub after finishing your partitions and installing XP, the new Grub will identify the new partitions automatically.

I advise you against moving the starting point of any partition that was pre-installed with Windows. It can be done, but it is possible (not sure) that the starting point of the Windows partition is one factor used to determine if your installation is "Genuine."

Meanwhile, follow Pumalite's above advice.

---

### Post by Pumalite on 2008-07-30
You can use Super Grub to reinstall your Grub after you have booted Ubuntu and confirmed that everything is OK.

---

