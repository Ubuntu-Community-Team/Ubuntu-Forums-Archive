---
title: "Cannot install without repartitioning?"
date: 2006-12-22
forum: Installation &amp; Upgrades
---

### Post by Fibonacci on 2006-12-22
Hello,

I finally decided to try Ubuntu (Edgy Eft) for real (took me long enough :P). That is, installing it. To do that, I'm going to overwrite my previous GNU/Linux installation; I have backed up all files from that partition (ext3, of course) so I wouldn't mind losing the data - in fact, I want to erase that data and ONLY that data. Problem is, the Ubuntu installer won't let me do that, but instead offers me a choice between physical hard drives only.

I have the following hard drives:
/dev/hda, with a single NTFS partition.
/dev/hdb, partitioned in:
  /dev/hdb1, ext3, this is where I want to install Ubuntu.
  /dev/hdb5, FAT32, this data **MUST NOT BE TOUCHED AT ALL** (don't ask why it's 5 instead of 2, both Knoppix and Fedora assign it that number).
/dev/sda, FAT32, with a single partition.

What the installer does, is offer me the choice between the three hard drives and not between the four partitions; and **I DO NOT WANT TO REPARTITION ANY OF MY DRIVES**. I just want to install Ubuntu on /dev/hdb1, NOT in the whole /dev/hdb.

Backing up /dev/hdb5 is out of the question - it contains about 60GB of data.

Is there any way of installing to an existing partition? I know from experience there is on Anaconda.

Thanks in advance,

-Fibo

---

### Post by bruenig on 2006-12-22
If you go into manually edit the partition table, you ought to be able to change around partitions. Perhaps you could take some screenshots of the problem and post them? Not sure exactly what the issue is.

---

### Post by Fibonacci on 2006-12-22
> **bruenig said:**
> If you go into manually edit the partition table, you ought to be able to change around partitions.

But I do not want to "change around partitions".

> **bruenig said:**
> Perhaps you could take some screenshots of the problem and post them? Not sure exactly what the issue is.

The problem is that I want to install Ubuntu on /dev/hdb1. I do not want to install Ubuntu on /dev/hdb. I do not want to overwrite the contents of /dev/hdb5. The Ubuntu installer does not give that option. The Ubuntu installer gives me /dev/hda, /dev/hdb, and /dev/sda as options. I don't want to install Ubuntu on any of those. I want to install it on /dev/hdb1.

---

### Post by bruenig on 2006-12-22
> **Fibonacci said:**
> But I do not want to "change around partitions".



The problem is that I want to install Ubuntu on /dev/hdb1. I do not want to install Ubuntu on /dev/hdb. I do not want to overwrite the contents of /dev/hdb5. The Ubuntu installer does not give that option. The Ubuntu installer gives me /dev/hda, /dev/hdb, and /dev/sda as options. I don't want to install Ubuntu on any of those. I want to install it on /dev/hdb1.

Go to manually edit the partition table. Leave the partitions like they are, just hit continue, and then the next part of the installer will ask you to set mountpoints and give you the option to format. You should be able to set hdb1 as / and tell it to format it.

---

### Post by Fibonacci on 2006-12-22
> **bruenig said:**
> Go to manually edit the partition table. Leave the partitions like they are, just hit continue, and then the next part of the installer will ask you to set mountpoints and give you the option to format. You should be able to set hdb1 as / and tell it to format it.

And it won't mess with hdb5, right?

---

### Post by Sef on 2006-12-22
> And it won't mess with hdb5, right?

Correct.  It should not mess with hdb5.  However, no one can give you a 100% guarantee that there won't be a problem.  You should by a big enough external hard drive big enough to back up hdb5.

---

### Post by Fibonacci on 2006-12-22
Crashed when I clicked on the manual edit option.

---

### Post by Fibonacci on 2006-12-22
Solved it by the simple operation of creating a swap file on /dev/sda1 and then activating swap on that file :P
Now I'm posting this from Ubuntu. From my local installation, I mean. Thank you guys!

---

