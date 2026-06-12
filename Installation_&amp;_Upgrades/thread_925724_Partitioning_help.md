---
title: "Partitioning help?"
date: 2008-09-20
forum: Installation &amp; Upgrades
---

### Post by dwdude on 2008-09-20
This is what my partitioning table currently looks like:
```

Partition      Filesystem   Size         Used        Unused
/dev/sda1      ntfs         107.42 GiB   64.12 GiB   43.29 GiB
unallocated                 58.60 GiB
/dev/sda2      extended     66.86 GiB
  /dev/sda5    ntfs         9.32 GiB     3.81 GiB
  unallocated               57.54 GiB

sda1 = Windows Vista
sda5 = Windows XP

```

What I want (and need somewhat) is a table that has: Windows Vista, Windows XP, Ubuntu, and Gentoo.

A shared /home and shared swap would be cool.

Swap gets 4048 MB and each linux distro should get 10GB each, then /home gets the rest.

My main questions are:
[COLOR="Blue"]1. How do I go about combining both unallocated spaces without reformatting my hard drive?

2. I've heard that sharing a /home between two distros isn't good. Is this true?

3. Would there be any other folders you would recommend putting on it's own partition?

4. What would you recommend me to do if I wanted to read/write files in between Linux and Windows? I've heard that there are programs for Windows that allow you to read from ext3 and vice versa for Linux, but would it be easier to just dedicate a partition for fat/fat32 for sharing?[/COLOR]


I need Ubuntu for one of my classes, then another class wants Gentoo, and I want Vista for games and other programs.

If XP is REALLY getting in the way of this working out, I could delete it as I don't use it much, but I'd like to keep it if possible.

Any help arranging this/answering questions would be appreciated.

I apologize for the vast amount of questions and all; I'm not a professional at this. 

Thanks,

Dave

---

### Post by Zuuted on 2008-09-21
I would highly suggest getting another HD and do no more than a dual-boot on each drive. I'd say run Ubuntu/Gentoo dual-booted on one drive, and Vista/XP Pro dual-booted on another drive... Although your best bet would be using a separate HD for each OS. Hard drives are pretty cheap these days.


As far as partitioning, I suggest using gparted within linux for resizing etc.

As far as sharing files between each partition, just access each one at the root level and create a share folder...


The setup I personally use is one HD with Vista Business/XP Pro (vista sucks, xp is just a bit better), and another HD with Ubuntu Studio... then other HDs for shared storage.


I hope this helps!
Peace!

---

