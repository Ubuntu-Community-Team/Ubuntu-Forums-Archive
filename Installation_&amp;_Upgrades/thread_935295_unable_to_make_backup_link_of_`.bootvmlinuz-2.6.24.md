---
title: "unable to make backup link of `./boot/vmlinuz-2.6.24-19-generic' before installing ne"
date: 2008-10-01
forum: Installation &amp; Upgrades
---

### Post by rvtlsl on 2008-10-01
Hello All,

I am just 3 days old to Ubuntu. I have installed everything perfectly with a dual boot along with XP home. After installing I got a notification to install 117 updates. I wasnt able to install any of those, I have been getting this error message:

**E: /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.41_i386.deb: unable to make backup link of `./boot/vmlinuz-2.6.24-19-generic' before installing new version**

Then went through the forums and finally found the following command which allowed me to install 116 out of 117;

**sudo rm /var/lib/dpkg/lock**

But for some reason I am not able to upgrade my kernel to linux-image-2.6.24-19-kernel.

Can some one please help me to resolve this issue.

Thank you

---

### Post by Patrick Snyder on 2008-10-01
I have the exact same problem.  (In fact I found this thread by pasting that exact same error message into Google).  I used the window's installer without making a new partition partition.  I'm running off of an external HD connected by USB.  Could either of these be the issue?

Thanks in advance (^_^)/

---

### Post by rvtlsl on 2008-10-01
Nope. Neither should be an issue because, 
I didnt have this issue when I installed on my three partitioned harddrive(1-windows, 2-linux,3-movies and music). Later I thought it would be better to merge 2 and 3 as I wanted to install Oracle on it. I have formatted the whole hard drive and created two partitions, one for xp and and the other for Ubuntu. Now I get this problem. My xp partition is NTFS and my Ubuntu partition is FAT32. 

We can live without this upgrade but I want to keep my computer up to date so trying hard to get rid of this. 

Can anyone please help us here. Thank you

---

### Post by z7510000 on 2009-02-06
I have the same issue and think that it's better for us to collect all comments into one place. You guys can follow the link below as some ubuntu developers may look into the bug.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/289718](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/289718)

---

