---
title: "Getting raid 0 working with Ubuntu 7.10"
date: 2008-03-24
forum: Installation &amp; Upgrades
---

### Post by EjnarH on 2008-03-24
I am new to both Linux raid setups and am having trouble getting installing Ubuntu on my new system with a raid0 setup.

My motherboard is Gigabyte P35 DS3 (not DS3R, which apparently has increased raid support) and I am using two Samsung Spinpoint F1 750 GB hard drives in a raid 0 setup.

I am planning to set up a tripple boot system of Ubuntu 7.10 (64-bit), Win XP Pro (32-bit) and Win Vista Business (64-bit), using one of the NTFS partitions for shared files to be accessible from both Ubuntu and Windows. At this stage, I'll be grateful if I can just get sufficient information to get Ubuntu running, however.

When I try to install Ubuntu from a standard live CD, it is unable to see the raid drive. It starts booting up in low graphics mode (where I, as far as I know, cannot access dmraid), and then freezes up, at the kernel boot, when I continue the installation.

Using the alternate install CD, it still doesn't see the raid drive, but can see the two hard drives in it individually. I was able to perform a partition and install on one of the two hard drives which were supposedly making up a raid0 drive at the time, but when booting, I was unable to access that installation.

---

### Post by bigredradio on 2008-03-24
Hardware RAID should never become apparent to the operating system. This should happen at a much lower level. So in your case you should only see one disk. Because you are seeing two disks, I would question the hardware RAID setup. It could be that the module that is loaded for your controller does not support it. This has nothing to do with dmraid. dmraid is used for software RAID. Two totally different ways of creating RAID devices. Only hardware RAID will work if you are trying to access the data from multiple OSs. Software RAID will be limited to Linux only access.

I use VMware in Linux with both XP and Vista and it works great so that I have all three on at once. I only use it for development testing however, so if you are a gamer, you would want dual-boot.

---

