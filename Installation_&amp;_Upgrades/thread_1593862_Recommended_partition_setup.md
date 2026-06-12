---
title: "Recommended partition setup"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by noiseordinance on 2010-10-11
Hi there. I tried getting creative with my partitions during my last laptop setup and the result is an unpartitioned 30GB block. I'm going to wipe my laptop and start clean, and I'd like some partition advice.

My hard drive is 160GB. I want to install Windows 7, Ubuntu 10.10, and an NTFS partition for storage that can be accessed by both operating systems. I'm thinking I want 30GB for both OS's and the remaining 100GB for the partition.

Which OS should I install first? Should I install Windows 7, create three partitions (30GB / 100GB / 30GB) and install Windows 7 on the first partition and let Ubuntu install on the last partition with my 100GB storage in the middle?

Thanks for any pointers. :)

---

### Post by srs5694 on 2010-10-11
Yes, your plan is basically sound. A couple further pieces of advice:


[list]
[*]You should probably create a swap partition for Linux, of at least the size of your RAM. The main purpose of swap space is to function as an adjunct to RAM; if you run many or big programs, the computer begins using swap space rather than just terminating programs. Swap serves a second purpose that may be particularly important with laptops, though: You can use a suspend-to-disk/hibernate function to shut down the computer and bring it up quickly with all your programs already running. To do this, though, you need swap space that's at least as large as your RAM.
[*]I'd create a primary partition for Windows and then create everything else as logical partitions. This will maximize your flexibility should you later decide to install more OSes that require primary partitions, such as FreeBSD. (With four partitions, as I'm recommending, you wouldn't be able to create *any* new partitions without jumping through awkward hoops unless you create at least one as a logical partition.)
[/list]

---

### Post by Megaptera on 2010-10-12
A useful guide here (though I see you're dual-booting) that may help?

[http://www.linuxbsdos.com/2010/05/26/manual-disk-partitioning-guide-for-linux-mint-9-and-ubuntu-10-04/](http://www.linuxbsdos.com/2010/05/26/manual-disk-partitioning-guide-for-linux-mint-9-and-ubuntu-10-04/)

---

