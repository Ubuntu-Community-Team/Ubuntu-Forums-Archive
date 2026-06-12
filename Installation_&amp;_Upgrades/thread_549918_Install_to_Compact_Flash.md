---
title: "Install to Compact Flash"
date: 2007-09-13
forum: Installation &amp; Upgrades
---

### Post by glen66 on 2007-09-13
Hi All

I'm wanting to run Dapper Server from a 2gb CF card, and I've installed it successfully.

Question is how do I minimise writes to the card?

Thanks in advance.

Glen

---

### Post by Insightfill on 2007-09-13
Honestly, if the question is that of "CF Card Lifetime", you'll probably find that it will outlast most hard drives.  The early days of these solid state memory things weren't that good, but they've improved dramatically, to the point of being considered as laptop drive replacements by OEMs.

I found [this]("http://www.storagesearch.com/ssdmyths-endurance.html") on a quick Google for "flash memory MTBF", but you can find other sources.  Many sources say that you can spend all day writing and clearing a piece of flash for years (5-50, depending on stats and model) before it starts going bad.  That's continuous disk writes, and a real world situation is only doing a small number of that.  Microsoft actually enabled the use of [flash drives as a page file cache in Vista]("http://en.wikipedia.org/wiki/ReadyBoost"), and you probably don't get more wear-tear than that.

The flash memory circuit will do its best to wear-level the writes around the disk in an even fashion.  If you want to aid this process, you can consider re-formatting the disk using [JFFS2]("http://en.wikipedia.org/wiki/JFFS2") instead.

I would say "don't worry about it".  Keep regular backups of changed files using Rsync to a different device or location (as you would with any other server), and swap when you need to, or ask your children to do so when they inherit the system.

BTW: what CF-IDE adapter did you end up going with?  I'm considering a similar project to produce a low power, ultra quiet machine; while the adapters are generally pretty cheap, I've read varying reports as to their effectiveness with different BIOSes.  Also: what make of CF card?

---

### Post by Insightfill on 2007-09-13
Re: ReadyBoost.

Sorry, did a little more research.  Article says ALL reads are cached there, not just page file.  However, page file is read-write from flash.

---

### Post by tgalati4 on 2007-09-13
I'm using Emphase 4 GB, IDE flash modules.  They are rated to 4 million read/write cycles.  I've had a few returns (wouldn't format properly, bad sectors) out of a batch of 10.

I'm using Damn Small Linux (DSL) for an automotive, embedded application.  Runs completely in RAM, boots off a small (200 MB) boot partition that is read-only.  I have a swap and 2 data partitions on the drive for rsyncing data to it.  These are formatted as ext2 as I don't need journalling.

No problems so far, but check back in a year.

---

### Post by Lepakko on 2007-09-13
> **glen66 said:**
> 
Question is how do I minimise writes to the card?

First of all, you should disable swap. It's also a good idea not to use a journaling filesystem like ext3 but ext2 instead, since journaling can be quite heavy on the flash. For temporary files etc. you can create a ramdisk, with which you can save files in RAM as if you were saving them in a regular fashion, and copy them from there to flash when necessary. RAM is your best friend when working with compact flash.

If you want to have it easy use Puppy Linux or Damn Small Linux, which can be fully loaded into RAM (Puppy does this by default). Or, with Ubuntu, if you want to play safe, you can mount your / as read only after configuring the system, with /var and /tmp either on a hard drive or a ramdisk.

As for not being afraid about writing on a flash, I wouldn't be so sure. There are solid state drives and flash drives manufactured for industrial use that can handle enough writes, but most standard flash cards are far away from that. There was a Windows XP not long ago installed on 2Gb flash card, which was rendered useless after a few hours of use. Flash cards with Linux can also wear off with time if the user is not careful with the var files, especially the logs.

---

### Post by basilb27 on 2007-09-29
I just installed Feisty to a 2GB compact flash card using the standard install disc. The only difference to a bog standard install was to go down the manual partitioning route rather than the guided.
I created a single ext2 partition using the whole drive withno swap partition and completed the install. It took a long time but it got there in the end. Must have taken a couple of hours and seemed to take the longest time copying the files onto the drive, but basically left it overnight and came down in the morning to find it installed.
It took 1.6 GB and I removed open office to give me a bit more free space. It works fine up to now.
Had previously tried installing Xubuntu on the same flash card, but this wasn't successful as I never managed to get past the partitioning phase of the install. Didn't really think a standard Feisty install would work but was happy to be proved wrong.

---

