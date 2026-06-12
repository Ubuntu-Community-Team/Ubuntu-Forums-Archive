---
title: "Installing in free space"
date: 2008-07-21
forum: Installation &amp; Upgrades
---

### Post by rob_botch on 2008-07-21
Firstly let me explain my hard drive. It has 4 partitions, all set up when I bought my laptop. One contains Windows, another (DATA) contains Documents, Videos etc., one has Acer InstantOn Arcade and the 4th is called PQSERVICE and I don't know what it does!

I used gParted to resize the DATA partition from 140GB to 120GB, to free up 20GB for Linux. (Incidentally, this took ages, much longer than when I used a Windows program, I think PartitionMagic, on my old computer - are there any other free tools that anyone can recommend?).

Booting the Fedora install DVD worked fine until it came to the point of partitioning. Ths option of "use free space" returned an error saying that there wasn't enough free space. Manually trying to allocate space showed the 4 partitions outlined earlier plus one ~20GB area and a 6MB area, both labelled "free space". Trying to create any partitions in the larger of these returned the same error message. t this point I gave up on Fedora and tried Ubuntu, which I have installed on other computers numerous times.

On Ubuntu, the partitioning stage was a bit different. The "free space" was labeled "unusable"!

Does anyone know what I have done wrong , or how to solve it? I'm guessing it's a problem with how I used gParted, but everything I did seemed to make sense!

Any help would be hugely appreciated - I dn't want to be stuck with just one OS!

Robert

---

### Post by zvacet on 2008-07-21
You can have max 4 primary partitions,and it looks like you have them allready.Mark free space as extended partition.For installing and partitioning look [here.]("http://psychocats.s465.sureserver.com/ubuntu/installing#partitioning")You can try manual way.

---

### Post by RuleMaker on 2008-07-21
> are there any other free tools that anyone can recommend?
You dont need any other partitioner than the one that is built inside the installation.
Choose manual partitioning:
Just right click on the free space, choose "Edit partition" and select what type of partition you want to have (probably ext2) and set the mount point to "/".
However, you'll need one more partition (about 1 Gb) to use it as a swap.

---

### Post by capatt on 2008-07-21
I have the same issue.  Isn't an Extended partition, simply a Primary partition into which you can add many logical drives?  Using the solution above would yield 5 primary partitions, would it not?

---

### Post by zvacet on 2008-07-21
Read [this]("http://en.wikipedia.org/wiki/Extended_partition") if you want more information about extended partition.

---

