---
title: "Installing Ubuntu on Dell Inspiron 6400"
date: 2007-12-08
forum: Installation &amp; Upgrades
---

### Post by superuser84 on 2007-12-08
Dear All,

Just joined Ubuntu forums and a big Hi to everyone here.

I am trying to install Ubuntu 7.04 on my Dell Inspiron 6400 laptop. As a first step, I am trying to partition the existing NTFS file system. I am following a tutorial at [http://www.homelandstupidity.us/2005/06/18/partitioning-to-dual-boot-linux-and-windows-walkthrough/](http://www.homelandstupidity.us/2005/06/18/partitioning-to-dual-boot-linux-and-windows-walkthrough/)

The tutorial says that I have to first create a 100MB boot space  before the C partition. But when I am running the PartitionMagic 8.0, I see there are following partitions

1. Dell Utility (FAT) 78.4 MB
2. Local Disc C (NTFS)  52  GB
3. Unallocated 7.8 MB
4. Local Disc (*) (CP/M Concurrent DOS, CTOS) 3074 MB
5 Unallocated 7.8 MB

Where should I add the linux boot partition (100 MB) and the actual partition (plan 15 GB)
Do you know of any tutorials that would be usefult to me.

Thanks,
J.

---

### Post by aysiu on 2007-12-08
That tutorial stinks. You don' t need a separate /boot partition, and you don't need Partition Magic, either.

Try this:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by superuser84 on 2007-12-10
Thanks Buddy....The tutorial was very useful. However, I feel the partitioning with Ubuntu utility was not very convenient. I had to fall back to Partition Magic.Installing Ubuntu was very easy.  Thanks to ubuntu 7.10, I have a good looking desktop and the power of the Linux Terminal.

Thanks,
J.

---

