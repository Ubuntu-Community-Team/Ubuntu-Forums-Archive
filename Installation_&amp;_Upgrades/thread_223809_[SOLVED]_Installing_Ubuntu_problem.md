---
title: "[SOLVED] Installing Ubuntu problem"
date: 2006-07-26
forum: Installation &amp; Upgrades
---

### Post by RonB123123 on 2006-07-26
Hello,

I'm using a dual boot system with Windows XP and Ubuntu 6.0.6.

Our computer has only a 50 GB drive and it has already been partioned and if we try to reinstall ubuntu it will not reinstall over the same partion it was installed on before. And so it will try to partition the drive again in which case nothing will work, because it will run out of space. So how do we uninstall Ubuntu first and get it back to the single boot xp so we can re partition and reinstall ubuntu again?

For some history: 
We used the previous version of Ubuntu (around 5.x.x) and we tried to upgrade to the newer version of Ubuntu (which was 6.0.6) and it did not work for some weird reason. And we can not boot into Ubuntu but XP works fine.

I wish Ubuntu woudl give you the option of installing a new iubuntu version over the same partition that the older version of ubuntu was installed in before.

---

### Post by aysiu on 2006-07-26
> **RonTheCon said:**
> 
I wish Ubuntu woudl give you the option of installing a new iubuntu version over the same partition that the older version of ubuntu was installed in before. It does. You have to choose the **Manually Edit the Partition Table** option. See these two pages for more details:

**Desktop CD**:
[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

**Alternate CD**:
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

---

### Post by RonB123123 on 2006-07-27
Thank you very very much. I really appreciate it and I will try it out some time tomorrow. :)

---

### Post by ahallubuntu on 2006-07-27
Yeah, use guided partitioning after you select "manual edit the partition table."  This is very confusing, I admit!  I re-installed Ubuntu this week and found that the install disk was mounting my existing Ubuntu partitions (root and swap) as "media" partitions.  So I had to tell it in Guided Partitioning to mount the root partition as "/" instead of as "/media/sda5" (I have a SATA disk so  yours may be "/media/hda5" or something like that) and then the swap partition as a swap partition instead of as "/media/sda7".  

There's also an option to format each of these partitions - you can skip that and let it overwrite existing files, but that may not be very clean - unless you are keeping /home from the previous install or something.  I recommend re-formatting both / and swap at this point before the installation continues - just hit Enter over that option to change it.  Before the partition editor commences from here it will ask you if you are sure you want to change/format those partitions.  Just make sure you pick the right ones!

---

### Post by Herman on 2006-07-27
> Our computer has only a 50 GB drive and it has already been partioned and if we try to reinstall ubuntu it will not reinstall over the same partion it was installed on before. And so it will try to partition the drive again in which case nothing will work, because it will run out of space. So how do we uninstall Ubuntu first and get it back to the single boot xp so we can re partition and reinstall ubuntu again? The way I always do it using the 'Alternate CD,  is to choose 'manual partitioning', and then I just *delete the old  Ubuntu partitions* so that I have an area of 'Free Space', and then I make new partitions in the free space.   
There is no need to re-install the Windows XP bootloader if you are re-installing Ubuntu again right away, as Ubuntu will re-install grub again for you.
Regards, Herman :smile:

---

