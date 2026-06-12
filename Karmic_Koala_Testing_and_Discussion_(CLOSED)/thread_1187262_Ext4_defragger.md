---
title: "Ext4 defragger"
date: 2009-06-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by phenest on 2009-06-14
There was talk of a defragger to be included in Karmic. Is it still in development or can we try it out?

---

### Post by olskar on 2009-06-14
> **phenest said:**
> There was talk of a defragger to be included in Karmic. Is it still in development or can we try it out?

Where was that talked about?

---

### Post by H2SO_four on 2009-06-14
I may be wrong, but when the linux filesystem was explained to me I was told that when writing to disk the file isn't fragmented on the drive.

---

### Post by Therion on 2009-06-14
Here's the best explanation I've come across that explains why Linux distros really don't need defragmenting.

[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

### Post by Angry_Anonymous on 2009-06-14
Linux needs online defragmentation. One case: convert ext3 to ext4 brings all ext4 improvements only for newly created files, old files will be treated as they are on ext3, not ext4. Online defrag will convert files into true ext4 ones.

---

### Post by phenest on 2009-06-14
> **olskar said:**
> Where was that talked about?

During Jaunty development.

The reason I ask is because of converting from ext3 to ext4. I have a /home partition that is ext3 and I don't want to convert to ext4 if I'm not going to get any benefits.

---

### Post by davideotape on 2009-06-14
[http://en.wikipedia.org/wiki/Ext4#Online_defragmentation](http://en.wikipedia.org/wiki/Ext4#Online_defragmentation) is the best I can find.

---

### Post by davideotape on 2009-06-14
[https://bugs.edge.launchpad.net/ubuntu/+bug/321528](https://bugs.edge.launchpad.net/ubuntu/+bug/321528) also looks very interesting

EDIT: [http://polishlinux.org/apps/cli/ext4-defragmentation-with-e4defrag/](http://polishlinux.org/apps/cli/ext4-defragmentation-with-e4defrag/) shows that this is possible, but it requires a lot of kernel tampering, which I would not recommend.

---

### Post by MacUntu on 2009-06-14
I'm interested in this too but hitting bugs while defragging seems dangerous. :D

@"does not need defragmentation": yes, system files have a small average size and therefore it's very unlikely that they get fragmented. User data on the other might be fragmented and definitely is on my 60% full file system (which increases access times).

Might not be an issue with SSD though.

---

### Post by Regenweald on 2009-06-14
When i converted my drives to ext4 recently, fsck showed that the ext3 drives were 5% fragmented. That is amazing after over a year of use and considering that 20% seems to be the accepted level of fragmentation for a system. So we do need online defragmentation, once a year in my case.......

---

### Post by ssam on 2009-06-15
its in development [http://lwn.net/Articles/334531/](http://lwn.net/Articles/334531/) not sure when it will be ready.

---

### Post by alphacrucis2 on 2009-06-15
> **phenest said:**
> During Jaunty development.

The reason I ask is because of converting from ext3 to ext4. I have a /home partition that is ext3 and I don't want to convert to ext4 if I'm not going to get any benefits.

I suppose you could just copy the files to say an external drive. Then copy them back.

---

### Post by Kamilion on 2009-07-19
Found it.

[http://thread.gmane.org/gmane.linux.file-systems/32218](http://thread.gmane.org/gmane.linux.file-systems/32218)

```

> Ted also pushed them as part of the 2.6.31 merge window, so testers
> will be able to test with 2.6.30-git14 or newer without having to
> apply the patches separately..

You may need a slightly modified userspace utility from what Akira-san
posted, which you can get here:

```
[e4defrag.c](http://repo.or.cz/w/ext4-patch-queue.git?a=blob_plain;f=online-defrag-cmd;h=7d42ad5cdb6813d262201d6806531f189d3d1f57;hb=35e9fa546ac349cb9a7c4ee9e45ff9747edd9335)
```

This reflects a change that I made in the structure passed in the new
EXT4_IOC_MOVE_EXT ioctl.

Note that I have not done a lot of stress testing of the defrag
functionality, so please be careful using it on production systems.
Please make sure you backup your files before trying to use it.

```

Needs linux-image-2.6.31-020631rc3-generic_2.6.31-020631rc3 from [the Mainline Kernel PPA](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds) for the required patches that allow e4defrag to work.

Good luck, file any bugs you find!

---

