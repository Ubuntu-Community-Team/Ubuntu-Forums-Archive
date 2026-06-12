---
title: "adding lvm on a running system"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by wmd on 2010-05-13
Hello,

I'm running low on disk space on my 10.04 server install. I'm running my normal partitioning without any lvm.

Is there a way I can create a new lvm set from my /home which is almost full and a new hdd to expand space just on that partition without killing everything on it?

ty, wmd.

---

### Post by wmd on 2010-05-14
Anyone?

---

### Post by srs5694 on 2010-05-14
Yes, but it's a multi-stage process. In brief (lacking much detail):


[list=1]
[*]Install your new hard disk and create an LVM configuration on it. Consult the [LVM HOWTO](http://tldp.org/HOWTO/LVM-HOWTO/) or do a Google search for documentation. (FWIW, I wrote a three-piece article on RAID and LVM for Linux Magazine about four years ago. You can read it [here.](http://www.linux-mag.com/id/2453) You can skip part 2 for a non-RAID LVM setup.)
[*]Create a logical volume to hold /home.
[*]Copy your current /home directory to the LVM's to-be-/home logical volume. Try Googling "linux moving /home" to find some sites that discuss the basics. Most of them describe moving /home to a separate partition, but the same principles apply.
[*]When you're satisfied that your LVM-based /home is working, you can delete the files from your old /home directory. If you'd used a separate partition for /home, you can unmount that partition, reconfigure it as a physical volume, add it to your LVM, and expand your /home logical volume. If /home was just a normal directory, just delete the files. If desired, you can then shrink your root (/) partition, create a new partition in the empty space, and add it to your LVM.
[/list]

---

### Post by wmd on 2010-05-19
Thank you for your input but after reading all of this I guess I'll just go without LVM. The fact that losing one disk is killing the whole set is not acceptable on my non-raid setup, I will need to invest in hw raid sometime..  :-/

---

### Post by darkod on 2010-05-19
> **wmd said:**
> Thank you for your input but after reading all of this I guess I'll just go without LVM. The fact that losing one disk is killing the whole set is not acceptable on my non-raid setup, I will need to invest in hw raid sometime..  :-/

LVM helps with resizing partitions on the go. Not with redundancy. Having said that, your current system doesn't offer redundancy too, right? If a disk fails, you're in trouble.

So, introducing LVM doesn't bring more danger into your setup.

RAID is another story. And it's not necessary to invest in HW raid, you can use software raid in ubuntu. In some cases it's even preferred, it looks like it's working better than mobo raid or low end raid controllers. High end controllers are again a different story. :)

But introducing software raid is also a U-turn on already operating system. I have no idea whether it can be done without too much hassle and danger. :)

---

### Post by wmd on 2010-05-19
In my current setup it would indeed result in a higher chance of total failure, having one logical volume spanning 2 partitions on two disks doubles the propability of total loss of said volume. Having one 1.8TB partition on a single disk added to a 800something GB partition on another also introduces a higher chance of failure since most of the data is stored one of the disks, when this one with more data and therefore higher chance of fs corrution has a spanning lvm partition to another drive, the whole pool gains propability of failure.

HW raid is the only way to go I think, I'd propably be looking at a Adaptec 5445 or 5805 in raid6 with some 2tb drives. But that has to wait for some time...  :)

---

