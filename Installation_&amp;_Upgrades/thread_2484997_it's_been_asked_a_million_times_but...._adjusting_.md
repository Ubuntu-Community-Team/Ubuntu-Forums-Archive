---
title: "it's been asked a million times but.... adjusting partitions for an install....HELP"
date: 2023-03-16
forum: Installation &amp; Upgrades
---

### Post by pjstock on 2023-03-16
I love using Ubuntu.
I HATE installing Ubuntu. 
because I usually either make a bad installation / partitioning decision OR I can never figure out how to adjust partitions and disk space.
or basically, I admit, I do not understand partitioning and when I try to read up on partitioning i never seem to find an explanation that applies to the situation I am facing.

and here we are again.
I am trying to install on an old outdated Windows 10 system but everything I try to do to adjust these partitions seems to fail.
don't I just want:
1, a partition to maintain Windows (that I would rarely use but sometimes find handy when something doesn't work with Linux. )
that 12GB partition looks to already have W10 so I would keep it.
 2. a big data partition. there is about 500GB that seem available for that.
 3. a ... approx 15-20gb partition for Ubuntu?

why can I not "shrink" the big 500gb data partition to take a chunk for a Ubuntu install partition?
when I try to shave off 20Gbs from the 450+ GB paqrtition, it fails.

(and. low priority. how do I get rid of these little useless scraps?)

I know the "Give a man a fish vs teach a man to fish" thing. but I cannot seem to grasp this.
could someone PLEASE talk me through this. 

I would like to once. Just Once. do a smart Ubuntu install.

Peter

---

### Post by MAFoElffen on 2023-03-16
**Stop Please.** Take a breath and breath. Take a look at the filesystem type that says "NTFS" for that 500GB partition... Which means it was created and is probably in use by Windows. Then Close down Linux and start Windows.

The background of not using Linux to shrink an NTFS partition , is that it will break the indexes that Windows uses to find files quickly... That index would have to be rebuilt if you did that.

In Windows, start the Disk storage manager, and shrink the partition from there. While you are in Windows, make sure fast-boot hibernation is turned off, as well as bit-locker.

**Note** that I think 30-45 GB is the right size for an Ubuntu Desktop root partition. 12GB is very tight for just the OS itself, after a few updates. That breathing room is really not going to take that much more out of that 500GB right? Better to be prepared now, while you are doing it, that trying to do it all over again later.

---

### Post by pjstock on 2023-03-16
thank you.
(who knew? )
I'll try that.

---

### Post by pjstock on 2023-03-16
got it.  
thank you.
but why (for future reference) was that not possible via the Ubuntu install procedure? or through GPT?

last questions.
what now would be the ideal format of the 25GB I shaved off this partition.?|
and what would be the ideal Root designation? /? or /root? or /home?
(or is that very personal and so no one solution fits all?)

---

### Post by MAFoElffen on 2023-03-16
Depends on what you do and what it's job will be.

I do some dev work and lots of testing. I usually spin up VM's with a minimum of 25GB. I used to allocate just 15GB for them, but after applying some updates, they are full in what seems to be no time at all.

All my machines are dual-boot, (except for 1 Raspberry Pi4 that I have in the living room). All of them are setup with a Windows OS partition, an Ubuntu OS partition, a Linux Home partition, and a shared data partition formatted as NTFS.

Why? Because I've learn through years of expereince to keep OS system files to themselves, so if something goes wrong, that the OS can be reinstalled or upgraded, with my old data still there, just needing to mount it. Therefore the separate home partition. Why a separate data partition formatted as NTFS? Because with Windows, OSX, UNIX, and Linux, all of them can mount, read, and write to NTFS. That is a common denominator that I can store data on that can be used with whatever I am booted as.

Note that in Linux land, the base, root directory is /. /home lives under /. /root is the root user directory and lives under /. That is summarized, but I hope that clears that up. Tell me if you need more of a visual on that.

I hardly use Windows, OSX or UNIX anymore. But there are times... I live mostly on Ubuntu, from day to day.

You could install everything Ubuntu as / (root drive) in your 25Gb partition that you freed up, then later add an fstab entry to mount your 475GB NTFS partition. If you start to run tight later, then either adjust your partitions again, or add another drive and split out your home directory. Home directories seems to collect things we want to keep.

EDIT: A visual
```

mafoelffen@Mikes-B460M:~$ sudo tree -L 1 /
/
&#9500;&#9472;&#9472; bin -> usr/bin
&#9500;&#9472;&#9472; boot
&#9500;&#9472;&#9472; cdrom
&#9500;&#9472;&#9472; data
&#9500;&#9472;&#9472; dev
&#9500;&#9472;&#9472; etc
&#9500;&#9472;&#9472; home
&#9500;&#9472;&#9472; lib -> usr/lib
&#9500;&#9472;&#9472; lib32 -> usr/lib32
&#9500;&#9472;&#9472; lib64 -> usr/lib64
&#9500;&#9472;&#9472; libx32 -> usr/libx32
&#9500;&#9472;&#9472; media
&#9500;&#9472;&#9472; mnt
&#9500;&#9472;&#9472; opt
&#9500;&#9472;&#9472; proc
&#9500;&#9472;&#9472; root
&#9500;&#9472;&#9472; run
&#9500;&#9472;&#9472; sbin -> usr/sbin
&#9500;&#9472;&#9472; snap
&#9500;&#9472;&#9472; srv
&#9500;&#9472;&#9472; sys
&#9500;&#9472;&#9472; tmp
&#9500;&#9472;&#9472; usr
&#9492;&#9472;&#9472; var

```

---

