---
title: "How to create aligned partitions with fdisk on EBS?"
date: 2010-07-17
forum: Installation &amp; Upgrades
---

### Post by Erik-NA on 2010-07-17
After reading Markus Ewald blogpost on [http://www.nuclex.org/blog/personal/80-aligning-an-ssd-on-linux](http://www.nuclex.org/blog/personal/80-aligning-an-ssd-on-linux) about Aligning an SSD on Linux I decided to give it a try.

I have bought two 80 GB Intel X25-M SSD for my home server. The plan is to install Ubuntu 10.04 64-bit server and use the SSDs as system discs and vmware data storage using software raid for redundancy.

After reading the blog post I am not sure how to make all my partitions aligned and set up on EBS (Erase Boundary Size)

I am planning for four partitions:
[LIST=1]
[*]Boot, size 1GB
[*]Root, size 25GB
[*]Swap, size 4GB
[*]Data storage for vmware server, size 40GB
[/LIST]

According to Markus Ewald I should use 32 heads and 32 sectors.

Using the live CD, I started using fdisk -S 32 -H 32 /dev/sda

Fdisk can create partitions using cylinders or sectors, and now I ran into trouble.

First partition /boot must start on cylinder 2 (or sector 1024). Size is 1 GB and the following partition should be aligned and start on a new EBS block. How do I do this with fdisk?

Should the next partition start on a new cylinder? Otherwise, after formatting, fdisk gives a warning that the partition is not aligned to the cylinder size? 

The overall question is how to format four aligned partitions which all are aligned with Intels X25-M EBS. EBS for Intel X25-M is either 128KB or 512KB (Have not found a confirmed value yet)

---

### Post by Erik-NA on 2010-07-17
Trying to reply myself

After some tweaking fdisk -l reports the following for /dev/sda:

```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
32 heads, 32 sectors/track, 152638 cylinders
Units = cylinders of 1024 * 512 = 524288 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: --blah--

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2        1955     1000448   83  Linux
/dev/sda2            1956       50784    25000448   83  Linux
/dev/sda3           50785       58597     4000256   82  Linux swap / Solaris
/dev/sda4           58598      152638    48148992   83  Linux

```

After reading Markus Ewald again and again and again I found out that one cylinder stores 1024 bytes. fdisk handles cylinders in units. One unit is 512 cylinders which is 1024*512 = 52 4288 bytes.

Markus Ewald points out that unit size happens to be on SSD's maximum erase block size. So what is the problem? Just create the partitions on cylinder boundary.

---

