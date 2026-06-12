---
title: "partition, mount point of ext3 &amp; dual boot"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by themis on 2010-02-19
Hello,

I attach a picture of my future disk partitioning,
as I thought it should be.

As you can see, the first two partitions are 2 different windows installations. 

At the end of the disk, I have specified a partition as 
    ext3 104855 MB (sda9)
and swap 8192   MB (sda8). 

**What should the the mount point of sda9 be????**
Should I specify a partition for /, /boot, /home, /tmp, ...etc?
Or it is ok to make **mount point** '/'??
I am a little lost here!

Is there something I should change?

Thanks!

---

### Post by stlsaint on 2010-02-19
It is good practice to make a seperate partition for /, /boot/ and /home.

---

### Post by themis on 2010-02-19
stlsaint thank you for the quick reply!

> **stlsaint said:**
> It is good practice to make a seperate partition for /, /boot/ and /home.

Can you specify the size of these partitions?
I give totally 100 GB for these!
So I need 4 partitions?
/
/home
/boot
and one for the rest, or I didn't get it right?

---

### Post by themis on 2010-02-19
And something else...

I have a 4GB RAM , is it correct to have a 8 GB swap?
I decided it based on thread readings.

I also read that swap shpuld be placed in the first 1024 cylinders...:-k
how can I achieve that?

---

### Post by darkod on 2010-02-19
6GB swap is enough for 4GB ram. More than plenty.

For standard home desktop usually you would have / and /home. / is the main partition, you can't install linux without it, like C: in windows. Separate /home is optional, otherwise there will just be home folder in /. But separate /home partition allows you to reinstall ubuntu with formatting / while keeping your home folder which is in /home in that case.

Older BIOSes are not able to read the boot files beyond 137GB so that is the only case where you would need separate /boot at the beginning of the drive. Otherwise, it's /, /home and swap.

For / size, about 20-25GB is plenty because adding software doesn't take as much space as in windows. And all your other data will be in /home.

---

### Post by themis on 2010-02-19
Thank you very much darkod!

---

