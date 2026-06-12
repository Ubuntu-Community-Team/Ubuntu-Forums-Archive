---
title: "Ubuntu Partitioner - Is It Crap?"
date: 2006-07-23
forum: Installation &amp; Upgrades
---

### Post by menawollas on 2006-07-23
Hi,

I've been playing around with Ubuntu/Kubuntu for a few weeks, having done several reinstalls, and the Partioner (Gpparted ??) seems to be causing me no end of problems.

I have a multiboot system - two primary partitions for XP and Vista, and then extended partitions for Ubuntu, Kubuntu, swap, one Fat32 and tow NTFS partitions.

I originally set the structure up with Partition Magic, which I have always found very reliable. 

When I have intalled ubuntu, and let it create and format an ext2 from free space, it doesn't seem to recognise it at the next stage. When I reinstalled ubuntu, after a forced reboot, and wanted to reformat the ext2 partition, it complained about bad structures (shouldn't a reformat just recreate everything). The FAT32 partition is always marked as a warning - yet its readable and writeable from XP and Ubuntu (once installed). And when running PM from XP, it picks up partition table errors after I've used the Ubuntu partitioner, which it prompts to fix.

I'm up and running fine, but I noticed on a thread elsewhere that the partitioner was meant to be a bit flakey, so it just seems to me a shame that on the LTS release, what is possbily the most fundamental bit of software for weaning users from windows to Unix lets Ubuntu down. 

Or is it just me. I know that if I hadn't been a techhead for nearly 30 years, I would have given up in frustration at what I've been trying to do just to get a stable multiboot setup.

Is there a bugtraq for this? Is Edgy Eft going to be better? I feel frustrated that I waited to the release to try 6.06, as I would have certainly raised these points earlier.

---

### Post by ahallubuntu on 2006-07-23
Multi-boot systems are just more complicated than single-boot systems because  partitioning itself can be difficult to understand.  It is even more complicated if you have an old BIOS or older OS's like Windows 98 (FAT32 can't be larger than 32GB for example).

I just installed Ubuntu on my laptop, and I got confused about the partitioning at first because I had my partitions setup wrong (I'd forgotten that you can boot an OS from a logical partition nowadays).  After that, it worked smoothly.

I think a partition wizard would be better than what we have now with the Dapper Drake default installation.  Something like this:

Which one best describes your system:
- Ubuntu is the only OS installed on my system
- Ubuntu will be multi-booted with another operating system that is alredy on the same hard drive
- Ubuntu will be multi-booted with another operating system but will be installed on a separate hard drive

and then

How do you want to make partitions:

- Resize an existing partition to make room for Ubuntu partitions
- Make Ubuntu partitions in free space (there is currently X free space)

Etc.

You're right, some improvement is needed.

---

### Post by jsonder on 2006-07-24
Ok?

---

