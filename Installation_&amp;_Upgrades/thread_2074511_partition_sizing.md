---
title: "partition sizing"
date: 2012-10-21
forum: Installation &amp; Upgrades
---

### Post by unibroker on 2012-10-21
I will be reinstalling my Ubuntu 12.04 64Bit as my root partition is too small.  I'll mainly use this for android compiling. I'm going with 2 partitions; root and /home.  How does 15GB for root sound?

---

### Post by Jedcurtis on 2012-10-21
> **unibroker said:**
> I will be reinstalling my Ubuntu 12.04 64Bit as my root partition is too small.  I'll mainly use this for android compiling. I'm going with 2 partitions; root and /home.  How does 15GB for root sound?

I've had 12.04 64bit going since April.  My / partition is 18Gb, and I'm only using 7Gb of it.  I also have a /home partition as well.  I'm fortunate enough to have a SSD drive though it is only 256Gb.  So, in my humble opinion (IMHO :)) I'm wasting more than 10Gb of space in my / partition.  If I was going to a redo, I'd only have a / partition of 10Gb.

With all that said, short of having a massive music/video collection, I can't imagine ever filling up my drive while I'm using Linux.  Unlike Windows, there's not a lot of hugely bloated code (software) out there for Linux.  So I suppose that it's your call obviously, and we're all different kinds of users.  I can't imagine ever having my / partition reach 10Gb, much less 15Gb.

Thanks,
Jed

---

### Post by unibroker on 2012-10-21
> **Jedcurtis said:**
> I've had 12.04 64bit going since April.  My / partition is 18Gb, and I'm only using 7Gb of it.  I also have a /home partition as well.  I'm fortunate enough to have a SSD drive though it is only 256Gb.  So, in my humble opinion (IMHO :)) I'm wasting more than 10Gb of space in my / partition.  If I was going to a redo, I'd only have a / partition of 10Gb.

With all that said, short of having a massive music/video collection, I can't imagine ever filling up my drive while I'm using Linux.  Unlike Windows, there's not a lot of hugely bloated code (software) out there for Linux.  So I suppose that it's your call obviously, and we're all different kinds of users.  I can't imagine ever having my / partition reach 10Gb, much less 15Gb.

Thanks,
Jed

Thanks for the response.  I'm leaning toward 15GB for / but I was checking because I've heard some environments for compiling using bigger.  I guess I could always go 20GB and give up some if I wasn't utilizing it.

---

### Post by oldfred on 2012-10-22
I use 25GB on my SSD and have filled 9GB including /home of about 2GB but have most data except .wine in partitions on my rotating drives.

On SSD Arch suggests only using 25% of partition. I do know when creating a DVD to write it may write 4GB into tmp, so you do need some extra room as working space.

[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

---

### Post by Jedcurtis on 2012-10-22
> **oldfred said:**
> I use 25GB on my SSD and have filled 9GB including /home of about 2GB but have most data except .wine in partitions on my rotating drives.

On SSD Arch suggests only using 25% of partition. I do know when creating a DVD to write it may write 4GB into tmp, so you do need some extra room as working space.

[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

Yes, oldfred is correct.  I had forgotten the emailing that went on between myself and Lite-on, the mfg of my SSD.  I actually did have to have the first drive replaced (though I'm not sure I'm totally willing to take the blame fully!) because "they said" (Lite-on) that I should have accounted for a full 1/3 of the drives partitions to remain empty.  We also got into a bit of techy talk about TRIM and such as well, but if you have a newer SSD, they are supposed to be fully functional by now.  However I take back what I said; if your doing a lot of compiling, you **will** want some free space remaining in the / partition.

@oldfred, was it advised to use only 25% of the drive or to leave at least 25% empty?  I'm curious only because I've been using the rule of thumb that I can use up to 70% of the space in any given partition.  This was info I learned of while talking to tech support at Lite-on.  It was in April and I haven't searched through all my email yet to verify which is correct.  Use only 25% (1/4 of the partition) or 66% (approx 2/3 of the partition).  I'd be curious to know as I'm following the latter guidelines of leaving a third of the partition free and have had no ill effects.

Almost everything I do is instantaneous with my current config.  I also should put it out there that I only have Linux installed on the laptop.  Even when doing a re-start, I'm back in and fully functional (typing in password, etc.) in less than 30 seconds.  It is even less time when powering up from a turned off state.  I've never had a machine that burned DVD's or CD's as fast as this one.

Thanks,
Jed

---

### Post by oldfred on 2012-10-22
I guess I had it backward. I thought it was different for the / partition on the SSD.

From the Arch site:
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

> Buying the right sized SSD is key. As with all filesystems, target  <75 % occupancy for all SSD partitions to ensure efficient use by the  kernel. 

I do not use this setting but if compiling a lot:

 Compiling in tmpfs

> Intentionally compiling in /tmp is a great idea to minimize this problem. For systems with >4 GB of memory, the tmp line in /etc/fstab can be tweaked to use more than 1/2 the physical memory on the system via the size= flag as /tmp keeps filling up.

Example of a machine with 8 GB of physical memory:

tmpfs /tmp tmpfs nodev,nosuid,size=7G 0 0




---

### Post by unibroker on 2012-10-22
Maybe I should start a new thread with this additional question.

Am I going about this in the wrong way?  I am currently triple boot; WinXP, Ubuntu 12.04 32bit, Ubuntu 12.04 64bit with the last to be used for android building.  The alternative to the triple boot was something like Virtual Box but I read there are performance issues with that.

---

