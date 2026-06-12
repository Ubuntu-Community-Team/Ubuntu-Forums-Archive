---
title: "FakeRaidHowto"
date: 2006-09-12
forum: Installation &amp; Upgrades
---

### Post by Hazr0x on 2006-09-12
Hey, I'm installing Ubuntu on my RAID computer using the FakeRaidHowto on the wiki.

I was curious, when I use fdisk, would I set a bootable flag for /boot and also change the type of the swap? I was wondering if this would disturb the installation of the RAID device or something.

Oh, and, let's say if i wanted to install Kubuntu, would I just replace

sudo apt-get install ubuntu-base ubuntu-desktop

with

sudo apt-get install ubuntu-base kubuntu-desktop kde kde-core

Thanks!

Haz

---

### Post by mike3k on 2006-09-12
My EIDE card has hardware RAID capability, but it's BIOS based and works only in Windows. The easiest way to deal with it is just ignore it and use software RAID.

You'll see two or more drives as separate devices. Partition each one and set the partition type to RAID autodetect. Use 'mdadm create' to assemble the partitions into a RAID array, example:
```

mdadm create /dev/md0 --level=raid1 --raid-devices=/dev/hdb1 /dev/hdc1 /dev/hdd1

```

---

