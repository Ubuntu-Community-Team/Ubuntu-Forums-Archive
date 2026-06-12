---
title: "Ubuntu 14.04.1 RAID-1 boot fails with error - mdadm: CREATE group disk not found"
date: 2014-09-03
forum: Installation &amp; Upgrades
---

### Post by atp2 on 2014-09-03
After a failed upgrade to Ubuntu 14.04.1, my machine would not boot at all (nothing at all on the screen after BIOS), so I re-installed *without* reformatting the disks.  Now it gets further along, but still cannot boot, instead getting stuck in some sort of mdadm loop.

When the boot starts, first I see the [error: diskfile writes are not supported]("http://askubuntu.com/questions/468466/why-this-occurs-error-diskfilter-writes-are-not-supported") message due to [bug 1274320]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1274320").  But AFAICT, that isn't actually the cause of my boot problems, as after a few seconds the boot proceeds, and I see kernel dmesg output scroll by.  But then it gets stuck saying this over and over again, seemingly forever:

```

Incrementally starting RAID arrays...
mdadm: CREATE user root not found
mdadm: CREATE group disk not found
Incrementally started RAID arrays.

```

No matter how long I let it run, it just sits there occasionally repeating more of the same.  Help?  What should I look at or try to further diagnose and fix this?

I used the Boot Repair disk to record info about my system, it is here:  [http://paste.ubuntu.com/8135727/](http://paste.ubuntu.com/8135727/)

It's not obvious to mee from that Boot Repair info, but this machine has three disks for RAID-1 (one hot spare) and all three disks are partitioned exactly the same way, like this:

```

sda1, 150 GB, ext4, / (root partition)
sda5,   8 GB, swap
sda6, 842 GB, xfs, /data

```

I also posted additional info about how the failed upgrade and how the box got to this state about a week ago in my [Upgrade to 14.04.1 failed, RAID-1 mdadm, Boot Repair]("http://ubuntuforums.org/showthread.php?t=2241201") thread.

---

### Post by shurguywutt on 2014-11-05
I am having a very similar issue.  Did you find a fix?  [http://ubuntuforums.org/showthread.php?t=2251656]("http://ubuntuforums.org/showthread.php?t=2251656")

---

### Post by atp2 on 2014-11-06
> **shurguywutt said:**
> I am having a very similar issue.  Did you find a fix?
No, no exactly.  I instead ended up [again re-installing]("http://ubuntuforums.org/showthread.php?t=2241201&p=13137242#post13137242"), but this time formatting all the partitions.  That worked!  Which is *strange*.  It seems that the re-format wiped out some sort of bad state or settings, and that fixed things.  But why, I don't know.

---

### Post by RedScourge on 2014-11-24
For some reason, the Ubuntu installer gets all screwy if there are existing partitions on the drive. I think it tries to save you from yourself, but it ends up just frustrating the hell out of most people who simply want to wipe the partitions and start over. Ironically, I had to boot off a Windows 7 disc so I could blow away the existing Linux partitions so that Ubuntu 14.04.1 would actually let me set up a RAID and have it work properly on previously used drives. I tried to file a bug report in Launchpad, but that place seems to assume every bug has to involve a package.

---

