---
title: "Can't boot anymore after upgrade from 20.04 to 22.04 (RAID)"
date: 2023-01-08
forum: Installation &amp; Upgrades
---

### Post by obruchez on 2023-01-08
I have a system with 2 SSDs configured as RAID 1 and installed Ubuntu on them many years ago. I upgraded without any problem from 18.04 to 20.04. Now, after upgrading to 22.04, Ubuntu doesn't boot anymore.

I get the following:

```

[0.216455] x86/cpu: VMX (outside TXT) disabled by BIOS
[0.216460] x86/cpu: SGX disabled by BIOS.
Gave up waiting for suspend/resume device
Gave up waiting for root file system device. Common problems:
- Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
- Missing modules (cat /proc/modules; 1s /dev)
ALERT!  UUID=50514972-1c10-4dc3-af85-5d7b06b8636b does not exist. Dropping to a shell!


BusyBox v1.30.1 (Ubuntu 1:1.30.1-7ubuntu3) built-in shell (ash)
Enter 'help' for a list of built-in commands.


(initramfs)

```

The BIOS is up-to-date.

I booted Ubuntu from a USB stick and tried to use boot-repair, as described here:

[https://linuxconfig.org/ubuntu-22-04-not-booting-troubleshooting-guide](https://linuxconfig.org/ubuntu-22-04-not-booting-troubleshooting-guide)

It doesn't recommend any repair. The information from boot-repair is available here:

[https://paste.ubuntu.com/p/xWzyzy7bP8/](https://paste.ubuntu.com/p/xWzyzy7bP8/)

Also, this is how my 2 SSDs appear from the live Ubuntu:

[https://www.flickr.com/gp/bruchez/3167i0RmN0](https://www.flickr.com/gp/bruchez/3167i0RmN0)
[https://www.flickr.com/gp/bruchez/9566RpZ265](https://www.flickr.com/gp/bruchez/9566RpZ265)

What can I do?

Any help would be greatly appreciated!

---

### Post by MAFoElffen on 2023-01-10
If it were me. I would first try to boot as Rescue mode > fschk > Yes

If that does not work, then from LiveCD...
```

sudo fschk -p /dev/sda2

```
Then if it doesn't help mark /dev/sda2 as failed and replace it
```

mdadm --manage /dev/md0 --fail /dev/sda2
mdadm --manage /dev/md0 --remove /dev/sda2

```
Switch out the disk and copy the partition table. create the mirrored EFI partition and swap. Then add the new /dev/sda2 partition back into the array...

---

### Post by obruchez on 2023-01-13
Thanks for your reply, MAFoElffen!

So I've tried to boot in "recovery mode" (this is the same as rescue mode, right?) by selecting "Advanced options for Ubuntu" in GRUB. I get the same error as previously (i.e. going straight to BusyBox).

I've booted from by USB stick again ("Try Ubuntu", etc.).

By fschk, you mean fsck, I guess?

Initially, I don't see the partitions in /dev, only /dev/sda and /dev/sdb. It's only after running boot-repair that I see them (/dev/sda1, /dev/sda2, /dev/sda3, /dev/sdb1, etc.).

I can't do a "non read-only" fsck on /dev/sda2. It complains that /dev/sda2 is in use ("Cannot continue, aborting.").

If I attempt an fsck in dry-run, it works, but it does't list any problem with the partition.

I'd like to attempt something with mdadm, but /dev/md0 doesn't exist (no md* device whatsoever in /dev).

I also can't mount /dev/sda2: "/dev/sda2 already mounted or mount point busy."

If I try to list the mount point with findmnt or lsblk, it doesn't list anything.

I'd like at least to retrieve the data from my SSD disks...

At this point, I'm completely lost.

Thanks for any help.

---

