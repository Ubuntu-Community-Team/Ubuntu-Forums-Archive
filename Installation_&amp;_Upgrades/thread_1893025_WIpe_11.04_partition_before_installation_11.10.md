---
title: "WIpe 11.04 partition before installation 11.10"
date: 2011-12-09
forum: Installation &amp; Upgrades
---

### Post by Macamba on 2011-12-09
Hi,

My computer is in shambles. I did an update in 11.04 (probably something to do with energy management), went afk, came back, needed to reboot my computer, and got a "Error: no such device $UUID". I got my Live CD 11.04, booted it, got the question if I wanted to upgrade to 11.10, went along with it, but ended up in "No space left on device". 

What do I need to do now? 
[LIST]
[*]I have no access to my Windows partitions, so am not able to backup my documents.
[*]Need to wipe my 11.04 root partition, but am not able to mount my partitions.
[*]At the moment I'm out of options.
[/LIST]

So, wipe the 11.04 partition of a hard disk I'm not able to mount?

Help? :confused:

Macamba

---

### Post by darkod on 2011-12-09
Do you have anything important inside the 11.04 that you would lose if overwriting it with 11.10?

---

### Post by Macamba on 2011-12-09
No. Only configuration of programs will be lost. That can always be recreated when necessary. 

However, I surely would like to backup my Windows data (documents and mailbox). And when I perform  a 'sudo fdisk -l' I only get my second internal harddrive and an external harddrive ready to be used for my backup.

Edit: Oh, and my Linux partitions are also on this internal HD.

Edit 2: Try to make it clearer:
1 I have one HD with Windows and Ubuntu (root and home on separate partitions)
2 I have a second HD with data
3 I have an external HD I activated so it can be used to backup my Windows stuff.

---

### Post by darkod on 2011-12-09
But the HDD 1 is not even reported as discovered, right?

---

### Post by Macamba on 2011-12-09
Yes. That is the problem I might need to tackle.

Strange however that I was able to upgrade to 11.10, I'm not able to fdisk -l.

---

### Post by darkod on 2011-12-09
Uhh, even if the upgrade went wrong, if at least the disk was reported as present it would give you something to work with. Like this I don't know.

Because even if the partition table is corrupted, etc, at least disks are usually seen as present. So you can use tools like fixparts, or testdisk, to try to repair your disk partition table.

About getting the data off, you need to "see" it for that too. Once you see it, it's easy to copy to ext HDD with ubuntu cd booted in live mode.

---

### Post by Macamba on 2011-12-09
So if a fdisk -l delivers a:
Disk /dev/sda: 82.0 GB <SNIP>
Distk /dev/sdc: 10000.2 GB, <SNIP>
and my /dev/sdb containing all data is lost in /dev/null I have a problem? :cry:

---

### Post by Macamba on 2011-12-11
Today, after a days rest, my system booted without problems. 

Thanks for the help on my problem.

---

