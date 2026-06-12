---
title: "Need help partition HD"
date: 2011-05-20
forum: Installation &amp; Upgrades
---

### Post by mawil1013 on 2011-05-20
I need some help, I'm looking to partition HD to place Ubuntu 11, and not destroy Windows Vista,

here's what I see,

Allocate drive space,

/dev/sda
/dev/sda1 ntfs 310641 MB unknown
/dev/sda2 ntfs   9428 MB 8346 MB

below that,

Device for boot loader installation
/dev/sda ATA ST3320820AS (320.1GB)


what to do next?

*UPDATE: I think my HD is bad, I went ahead with the full install and get; Error: Input/output error during read on/dev/sda.

The reason I started this was problems with HD and Vista OS, but after running Ubuntu live CD and being able to see the HD contents which showed Main partition with a boot exclamation and the recovery partition I thought it might be OK still.

---

### Post by Dutch70 on 2011-05-20
First you need to shrink Vista (from within Vista only) to make room for Ubuntu.
There are plenty of tutorials on the net. It's best you follow one of them.

Then you'll need to create 2 partitions for Ubuntu. 1 for "/" aka "root" & 1 for "swap" equal to or slightly larger than your physical RAM. I would create an extended partition, then create the 2 logical partitions inside the extended prtn, which is like a container for logical prtns.

If you want a separate /home partition, which is a really good idea, you can follow this guide, or find another on the web.
[[COLOR="Red"]http://www.psychocats.net/ubuntu/separatehome[/COLOR]]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by Mr. Shannon on 2011-05-20
Just to correct something.  Ubuntu 11.04, and I think Debian as well no longer require you to explicitly create extended partitions during install.  They are created automatically when you create logical partitions.

---

### Post by Dutch70 on 2011-05-21
> **Mr. Shannon said:**
> Just to correct something.  Ubuntu 11.04, and I think Debian as well no longer require you to explicitly create extended partitions during install.  They are created automatically when you create logical partitions.

I wouldn't do it "during installation" I'd do it prior to installation & since you only get to create 1 extended partition. 
What would be the benefit of it doing it for you? 

What if I want a 15GB logical partition, but I want my 1 extended partition to be 100GB? How does that work exactly?

This link may help also...
[[COLOR="Red"]https://help.ubuntu.com/community/HowtoPartition[/COLOR]]("https://help.ubuntu.com/community/HowtoPartition")

---

