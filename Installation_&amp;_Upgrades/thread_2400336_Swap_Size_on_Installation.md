---
title: "Swap Size on Installation"
date: 2018-09-05
forum: Installation &amp; Upgrades
---

### Post by dstein on 2018-09-05
I recently installed Ubuntu on a new computer.

For partitioning the drive, I let the installer do everything automatically.

I was surprised to see that the swap partition is 976 MB.

I have 32 GB of ram and a 4 TB hard drive.

Is this relatively small swap partition size expected behavior?

Thanks.

---

### Post by deadflowr on 2018-09-05
New version of Ubuntu create swap files instead of a swap partition, though a swap partition will be used if one exists.
the size is relative to the disk space available.
more here: [http://blog.surgut.co.uk/2016/12/swapfiles-by-default-in-ubuntu.html]("http://blog.surgut.co.uk/2016/12/swapfiles-by-default-in-ubuntu.html")

---

### Post by oldfred on 2018-09-05
How small did you make / (root) partition? Or total space?
Post this:
sudo parted -l

Unless hibernating, which is not recommended particularly if dual booting, you do not need a large swap. And some with lots of RAM like you have, do not have any swap. You do not want swap used unless absolutely needed. And only if editing large videos in RAM may you need swap, but then really should add more RAM. 
My old BIOS system had 4GB of RAM, and normal use, never used swap. 

My current system, show no swap used and lots of RAM available, some in RAM caching.
```
fred@bionic-z97:~$ free
              total        used        free      shared  buff/cache   available
Mem:        8109864     1527040     4792000      108516     1790824     6475044
Swap:       2149372           0     2149372

```

---

### Post by dstein on 2018-09-05
deadflower and oldfred, thanks for your replies.

I've disabled the swap partition and created a swap file that is much larger. I am not sure why the installer created a 1GB swap partition.

---

