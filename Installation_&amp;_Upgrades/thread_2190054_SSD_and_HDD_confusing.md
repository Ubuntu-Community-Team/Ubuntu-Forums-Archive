---
title: "SSD and HDD confusing"
date: 2013-11-25
forum: Installation &amp; Upgrades
---

### Post by weber-jonathan on 2013-11-25
Hello!

I've read some crazy **** what can go wrong when using SSD, and, since I just got my first laptop with an ssd, I just wanted to confirm what is the right procedure to go on now.

I have installed Windows 8 on my system and I am completly annoyed. Windows 7 was really ok, but this new metro-thing is just unusable with no touch-screen. So I want to go back to Ubuntu, which I was using some years ago. I am currently downloading Ubuntu 13.10.

My computer has an 1TB sSATA HDD and an Intel 32GB SSD. Since the HDD is somehow loud (I installed Windows in it) I would like to install the pure system on the 32GB SSD and use the 1TB HDD for data. I would like to keep windows for compatibility. First of all: Is this a good idea? Will it work? Is 32GB enough? What about software I install later?

The much more important question: How and where do I have to configure the SSD? Because I have read some things about Write-Blocks and that these blocks should have the same sice and the OS write blocks? Guides I found offer different solutions for this but are not identically. What is the way to go for Ubuntu 13.10 and my system?

Thanks in advance for every help.

---

### Post by oldfred on 2013-11-25
Hard drive should not be loud???

All the new partitioning tools start partitions on 8 sector boundaries for compatibility with SSD and new 4K drives.
You just need to check that the start of all partitions is divisible by 8.

Was/Is this an Ultrabook? With UEFI and gpt partitioned drives?

Those with Ultrabooks have to turn off the Intel SRT and remove RAID meta-data from both drives. Some just install Ubuntu to hard drive and a few with larger SSD like yours install / (root) to SSD and /home or data partition(s) to hard drive.

Post this from live installer terminal, it will show current partitions:

sudo parted -l

---

### Post by fantab on 2013-11-26
By installing [**classic shell**]("http://www.pcworld.com/article/2026719/review-classic-shell-brings-the-start-menu-to-windows-8-for-free.html") you can make your Win8 feel like Win7.
Seriously, if you think your HDD is loud get it checked, perhaps you need a replacement.

Like the post above asks, boot with you ubuntu DVD/USB (aka ubuntu live), "Try Ubuntu without Installing", open Terminal [ctrl+alt+T] and post the output of the above mentioned command:

```
sudo parted -l
```

*NOTE*: Use only Windows partitioning tools for manage Windows partitions and Only Linux partitioning tools like, Gparted, to manage Linux Partitions.

---

