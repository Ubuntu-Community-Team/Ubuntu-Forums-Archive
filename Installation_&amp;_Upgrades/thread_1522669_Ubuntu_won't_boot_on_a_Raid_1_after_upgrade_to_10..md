---
title: "Ubuntu won't boot on a Raid 1 after upgrade to 10.04"
date: 2010-07-02
forum: Installation &amp; Upgrades
---

### Post by Kepesk on 2010-07-02
Well, it seems I've done it again.  I upgraded my ubuntu install to Lucid a couple of days ago, and I haven't been able to boot since.

I'm running on Raid 1 with /dev/md0 being the /boot partition and /dev/md1 being the / partition.  /dev/md0 is built from /dev/sda1 and /dev/sdb1, and /dev/md1 is built from /dev/sda2 amd /dev/sdb2.  Both are ext3.

It gives me this error right after GRUB:

```
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
- Check rootdelay= (did the system wait long enough?)
- Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/md1 does not exist. Dropping to a shell!
```

after which the thing drops me into initramfs.  I've ruled out a rootdelay problem, as I can wait a long time, type exit, and it just repeats the error.

When I examine the initramfs environment, I discover that /dev/md0 is assembled, but /dev/md1 has failed to assemble, which seems to rule out a module problem.  When I try to assemble it manually, it gives me this:

```
mdadm: no recogniseable superblock on /dev/sda2
```

Gotta love misspelled errors, right?  The same happens when I try to assemble degraded with just /dev/sdb2, so it doesn't seem likely that this is an error on one of the drives.

To test for a bad array, I booted to the live CD and did mdadm --assemble --scan, and it assembled the RAID partitions with no errors.  Why would I get a different result when booting from the live CD?

Where do I go from here?

---

### Post by Kepesk on 2010-07-02
Solved.  For some reason, the upgrade changed my /etc/mdadm/mdadm.conf to specify that the /dev/md1 raid used /dev/sda2 and /dev/sdb2 where the partitions were actually /dev/sda5 and /dev/sdb5.  I had forgotten that the partitions were extended, but I'm not sure why Ubuntu forgot too.

So if you run into this problem, boot with a liveCD and make sure your /etc/mdadm/mdadm.conf matches the drives that show in /dev (or in your preferred partition manager).

---

