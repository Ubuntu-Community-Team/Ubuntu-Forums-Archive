---
title: "New Install Won't Boot."
date: 2014-04-03
forum: Installation &amp; Upgrades
---

### Post by vincej on 2014-04-03
Hi - I have a desktop which used to have a dual boot xp / Ubuntu. I don't want the xp and I want to reclaim the space for Ubuntu. The disk had been logically divided into /dev/sda and dev/sdb. I ran DBAN on it to clean everything out. 

When I go to install I still see 2 logical drives sda (250GB) and sdb (500GB) 

I make sda swap and sdb root / 

I nominate the sdb as the boot disc.  

Ubuntu appears to install fine, however, then I go to restart and nothing ... just a blinking cursor. 

Ok - so I have to admit that I was unsure what to do in terms of specifying swap and root. 

I have specified sdb as "boot", and when I look again now with a live install disc into the drive it is indeed flagged as "boot"

In a perfect world I would prefer to somehow remove one of the logical drives so that I can have just 1 drive of 750GB back. But I do not have  windows disk, and I have Googled to death how to do that without result. 

I'm quite confused the best way forward.

MANY Thanks for all you advice !

---

### Post by oldfred on 2014-04-04
If drives are sda & sdb, that is not logical drives, but two actual physical drives.

If Ubuntu installed correctly you may have grub boot loader in the MBR of the other drive. Have you in BIOS tried booting sda, or sdb?
Grub does not use boot flag. But some BIOS will not let you boot without one, so we suggest a boot flag on a primary partition on every hard drive.

You normally only need / (root) of 20 or 25GB, swap equal to RAM in GiB if you want to hibernate or 2or 3GB otherwise if you have lots of RAM and do not hibernate.

Then rest of drive(s) and partitions can be /home or data partitions. I use data partitions and a partition on the other drive for short term backup.

       [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

May be best to see details.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

