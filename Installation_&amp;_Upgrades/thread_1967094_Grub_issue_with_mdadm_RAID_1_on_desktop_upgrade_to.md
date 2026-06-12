---
title: "Grub issue with mdadm RAID 1 on desktop upgrade to 12.04"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by Ron Jones on 2012-04-27
When I built my 11.04 system, I used the alternate installation disk, and configured software raid using mdadm. As it was a first for me, I was impressed with how simple it was when you follow the instructions.

upgrading to 11.10 went off without a hitch.

Upgrading to 12.04 went equally well. However, upon completion, I found that GRUB offered me only the latest kernel from 11.10 (3.0.0-something). So, I used the tweaker to remove that kernel, ran sudo update-grub, and thought it was all good.

When I rebooted, there was no image (but grub still offered the 3.0.0 kernel. So, I used the grub command line, and the setroot, boot, initrd, and boot commands to boot into the 3.2.0.24-generic kernel that came with 12.10 and was in /boot.

Once I got the machine GUI'd up, I purged and reinstalled GRUB.

Therein lies my concern.

My RAID 1 array consists of two 500 GB drives (sda & sdb), each with two identical partitions (sdx1) 4GB, and (sdx2) 496GB.

These two drives make up md1 (4gb) and md0 (496gb).

When I issued the command prompt (above), I specified md0 as the boot partition. However, when I purged GRUB, and reinstalled it (actually, it was grub-pc), I was unable to install it to md0. Rather, after purging, during re-installation,  I had to install grub to /dev/sda and /dev/sdb (using sudo dpkg-reconfigure grub-pc).

Can anyone tell me if this is right? I thought that everything would mount to md0 instead of the individual hard drives?

Thanks,
Ron

---

### Post by darkod on 2012-04-27
It sounds right. The bootloader goes to the MBR of the disks, not to partitions. And since you are running software raid which the OS creates, the bootloader would go to both disks to the MBR, in other words /dev/sda and /dev/sdb.

If it was fakeraid or hardware raid, it would go onto the raid device because the raid device is the whole disk anyway.

With software raid, the parts of the raid are partitions, and the bootloader doesn't go to partitions (with some special exceptions).

The system is booting fine, right?

---

### Post by Ron Jones on 2012-04-27
> **darkod said:**
> It sounds right. The bootloader goes to the MBR of the disks, not to partitions. And since you are running software raid which the OS creates, the bootloader would go to both disks to the MBR, in other words /dev/sda and /dev/sdb.

If it was fakeraid or hardware raid, it would go onto the raid device because the raid device is the whole disk anyway.

With software raid, the parts of the raid are partitions, and the bootloader doesn't go to partitions (with some special exceptions).

The system is booting fine, right?
Thanks! that makes me feel a good bit better.

I hadn't tried to reboot it yet, because I was concerned that I had flubbed it somehow and rebooting would only lead to a big headache, and a general feeling of rashness and stupidity.

But, I'll give it a go now that it seems all is as it should be.

---

