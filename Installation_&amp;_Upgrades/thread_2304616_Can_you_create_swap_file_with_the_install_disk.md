---
title: "Can you create swap file with the install disk?"
date: 2015-11-28
forum: Installation &amp; Upgrades
---

### Post by lambdafox on 2015-11-28
Is it possible to tell the installer to create a swap file instead of a partition?

Or can you only do this by changing it after installation?

---

### Post by Bucky Ball on 2015-11-28
Choose 'Something Else' at the partitioning section of the install and manually create one (create a 2Gb partition and set it as 'swapspace').

A regular install should create a /swap partition by default. It didn't???

---

### Post by grahammechanical on 2015-11-28
> Is it possible to tell the installer to create a swap file instead of a partition?

I do not think so. Linux, as far as I know, uses swap partitions and not swap files inside the OS partition. But it just goes to show how much or how little I know. Have I look at this.

[https://www.linux.com/news/software/applications/8208-all-about-linux-swap-space](https://www.linux.com/news/software/applications/8208-all-about-linux-swap-space)

Regards

---

### Post by Bucky Ball on 2015-11-28
Ah, my mistake. A swap *file*! Yes, was reading about a way of doing that the other day. 

Always good to do a [bit of research]("https://duckduckgo.com/?q=create+a+swap+file+ubuntu") prior to posting. [Try this]("http://www.cyberciti.biz/faq/ubuntu-linux-create-add-swap-file/"). :)

---

### Post by ajgreeny on 2015-11-28
There's a lot of info also at [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq), but it relates to adding a swap-file after installing, so you could install using the Something Else option, omit a swap partition totally from the install, then add swap-file after first boot.

---

### Post by Bucky Ball on 2015-11-28
> **ajgreeny said:**
> There's a lot of info also at [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq), but it relates to adding a swap-file after installing, so you could install using the Something Else option, omit a swap partition totally from the install, then add swap-file after first boot.

+1. That should work. If it didn't, you could install with a /swap, once installed, switch swapoff and delete it, then create the /swap directory.

---

### Post by tokyobadger on 2015-11-29
> **lambdafox said:**
> Is it possible to tell the installer to create a swap file instead of a partition?

Or can you only do this by changing it after installation?
1. As you've seen a swap file (as opposed to swap partition) can be implemented  in linux
2. The ubuntu installer won't do it - I'd think the only distros that might support this would be linux from scratch, gentoo, arch and their derivatives

Take a few steps back - why do you need swap?
I have an E6700 with 4G RAM running full Ubuntu 14.04 (desktop not server) and only falls down at distinguishing Marmite from Vegemite when making my toast in the colder months ;-)

---

### Post by lambdafox on 2015-12-05
linux newbbie so i am learning as I go...  I infer from old posts that there was historically a performance advantage to using a partition.  As I read it that is no longer true.  A swaap file offers the advantage of being resizable.  Supposedly it is also a better choice for SSDs.  Having learned that I was surprised to see the installer sets up a swap partition by default instead.   In my hacking around plans I want to make some minor changes to android and / or cyanogen mod.  for every day, like u swap is not a problem.

---

### Post by Vladlenin5000 on 2015-12-05
Have you considered the possibility that you actually might NOT need swap at all?
Besides, current generation of SSDs have the same lifespan as the old HDDs so why bother with such details?

---

### Post by efflandt on 2015-12-06
It really comes down to how much RAM do you have and do you really need swap (what all do you run on your computer and do you hibernate it at all)? If you have enough RAM, the only thing you would need swap for is to hibernate (not for just suspend).

My desktop PC has 8 GB RAM, does not use much power when idle (w/efficient GTX 750 Ti graphics), and Win7 with its utility and RECOVERY partitions was already using 3 msdos partitions, so I only have 1 partition for 64-bit Ubuntu 14.04 and no swap. My gaming laptop also has 8 GB RAM, quickly boots 64-bit 14.04 from mSATA SSD card, so to save wear on the SSD I do not hibernate, I just shut it down when not actively being used. I don't even have swap on my tablet PC which boots Win7 from its internal 32 GB SSD or Ubuntu or Lubuntu 12.04 on SD card with common /home partition and only has 2 GB RAM because it is somewhat slow (1 GHz 2 core) and I do not do anything intensive on it.

---

### Post by lambdafox on 2015-12-09
> **Vladlenin5000 said:**
> Have you considered the possibility that you actually might NOT need swap at all

Yes, I have.  My conclusion was that I do.

That was not my question. 

My question was whether there is some way in the installer to over ride its default behavior.  My comments on the rest were only to point out why I thought that default behavior was odd.

---

