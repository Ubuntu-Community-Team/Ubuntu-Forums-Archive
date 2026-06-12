---
title: "Dual booting Unbuntu 9.10 with 9.04"
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by Solorflare on 2010-04-04
Is it possible to have two versions of ubuntu on the same hard drive?
I dual boot at the moment with Windows (grrr) and Ubuntu 9.10 on my laptop and I want to put ubuntu 9.04 on it as well.

Will this work?

---

### Post by RedSingularity on 2010-04-04
Sure it will work, provided you have enough space on the hard disk.

---

### Post by Solorflare on 2010-04-04
> **RedSingularity said:**
> Sure it will work, provided you have enough space on the hard disk.

Ok.
Thats not a problem the drive is 250gb.
Would the two ubuntu installations use the same SWAP partition?

---

### Post by RedSingularity on 2010-04-04
Good question.  I am not sure if they will use the same swap.  I would like to know the answer to that as well.  I assume that it will use different swaps because the installer for both ubuntu versions will want to install a swap for itself.

---

### Post by Solorflare on 2010-04-04
hopefully someone out there has the answer for us then.

---

### Post by oldfred on 2010-04-04
I have winXP, my old install of 9.04, my current 9.10, and 10.04 for my testing. No problems but your need to make sure not to share some things. If you have multiple drives it is better to have different boot loaders in each MBR.

You can and should use the same  swap unless for some strange reason you want to separately hibernate each. Ubuntu boots quicker than window comes out of hibernation.

You should not share /home as the different versions of software may have incompatible settings. If just upgrading you can copy the home over as software usually is designed to recognize and update, but then may not work with the older copy anymore.

I created /data and a share partition. Most of my data is in /data and some things are still in my share which was for XP and Ubuntu sharing.

How to Multi-boot (Maintain more then 2 OS) old grub
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)
Painless Linux Multi-boot Setup - see also comments
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions of data linking from above blog, based on more from comments
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

---

### Post by Solorflare on 2010-04-05
> **oldfred said:**
> I have winXP, my old install of 9.04, my current 9.10, and 10.04 for my testing. No problems but your need to make sure not to share some things. If you have multiple drives it is better to have different boot loaders in each MBR......

[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

Thanks.
I just popped my old 9.04 cd in and installed and it installed as a small partition, which I don't mind. And added a second swap partition.

My drive lay out is now...

[Windows][ntfs - for storage and sharing] [Ubuntu 9.10] [Ubuntu 9.04] [swap] [Swap]

and all seems to work well.

---

