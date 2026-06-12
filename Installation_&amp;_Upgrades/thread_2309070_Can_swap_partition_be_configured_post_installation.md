---
title: "Can swap partition be configured post installation?"
date: 2016-01-07
forum: Installation &amp; Upgrades
---

### Post by Dáire Fagan on 2016-01-07
Hi

I have a 250GB SSD and much larger mechanical HDD storage. I am going to configure /home, /, and /boot partitions on the SSD but I would like to configure the 32GB (16GB RAM) swap partition on the mechanical drive. The issue I have with this is that the mechanical drive has data I need to go through first, delete some and backup the rest, before formatting and assigning new swap partition at the beginning of the drive.

Can I install ubuntu as normal, but choose no swap partition and later somehow assign it to the mechanical HDD when the drive is ready?

Please advise.

---

### Post by ubfan1 on 2016-01-07
Yes, and with that much memory, you probably won't even miss it when running without.

---

### Post by Dáire Fagan on 2016-01-07
[/QUOTE]

> **ubfan1 said:**
> Yes, and with that much memory, you probably won't even miss it when running without.

Actually I have only 8GB, but will be adding another 8GB soon enough. Do I need a swap at all? If it matters it will be a dual boot system.

---

### Post by QIII on 2016-01-07
The old rule of 2x RAM is archaic.  It came from a time when memory was expensive and limited.

With that much memory, as stated above, there really is no reason for swap (I don't use it any more) unless you plan to suspend -- in which case 110% of RAM is sufficient and swappiness should be set very low.

Dual boot won't matter.  Only one OS can run at a time.

---

### Post by Dáire Fagan on 2016-01-07
> **QIII said:**
> The old rule of 2x RAM is archaic.  It came from a time when memory was expensive and limited.

With that much memory, as stated above, there really is no reason for swap (I don't use it any more) unless you plan to suspend -- in which case 110% of RAM is sufficient and swappiness should be set very low.

Dual boot won't matter.  Only one OS can run at a time.

Any reason one one opt not to suspend? I know boot times should be much faster with the SSD (I have only ever installed ubuntu on HDDs), but surely resuming a session is much quicker than booting? I had thought if memory was used for suspending it would be lost if using another OS, but you post has made clear only the swap space is used for that.

---

### Post by QIII on 2016-01-07
Sorry - I meant hibernate.

Suspend maintains memory state in the RAM itself.

Hibernate used swap.

---

### Post by sammiev on 2016-01-07
My boot time is 9.2 seconds on a SSD and I use Htop to monitor how much memory and swap been used.

Swap was never been used so now I have a 1 meg swap and can suspend with no windows open and no issues.

Usually I shut down the computer even for short times with boot times been so quick.

---

### Post by 1clue on 2016-01-07
You don't even need swap to be a partition.

You  can:
```

sudo dd if=/dev/zero of=/var/swap bs=1073741824 count=16
sudo mkswap /var/swap
sudo swapon /var/swap

```

If you want it to be permanent you can put it in your fstab.

I'm not clear what you intend to do with the box.  If you have a lot of VMs running, for example, that can take up a crazy amount of memory.  Or a large database, or any number of other things.  I agree that most people who are just using Ubuntu as a workstation probably don't need to use swap if they have 16gb.

---

### Post by cybrsaylr on 2016-01-07
Thanks for all the good info on Swap partition that I've often wondered about.

I have 8GB of RAM and use System Monitor to watch what's going on with my PC for the past 6 years:
Got it a habit of using System Monitor to keep and eye on what my PC is doing.
[IMG]http://s2.postimg.org/in45gbqh5/image.png[/IMG]

Seldom if ever get into swap usage anymore. Years ago would get into swap being used when a program went 'bonkers' and just kept using more and more RAM! Don't know why this happened. It only  happened a few times. Usually noted this when this i7 PC began to perform weird due to all the RAM being used! Went into System Monitor which showed almost all the RAM in both PC and Swap was maxed out, causing some lag that should not happen with this i7 PC.

Still let Ubuntu install a Swap because drives are quite big now making the Swap partition negligible.   

Also have been using SSDs for 4 years as boot drives with the OS and mechanical HDDs for storage.  
SSDs are cheap now.
PC  boots up in 10 seconds and is good to go.
Installing a SSD is the best upgrade to any PC now!

---

### Post by 1clue on 2016-01-07
I just upgraded to 24g RAM because I was hitting swap with 12.

BTW my previous post, using a swap file, can be done while the system is up and running, without a reboot.  I've done this several times in production situations while I needed to diagnose a problem.

The system should never swap under normal circumstances.  Swapping is a mechanism to prevent the system from crashing when an atypical event happens.

That said, there are lots of uses for the virtual memory hardware in your system, including tmpfs.  I make lots of use of tmpfs for compiling and other scenarios where lots of temporary data is written to disk which is only needed to finish the task at hand.

I still use the 2xRAM guideline for swap size in systems that have swap at all.  It doesn't hurt to have that much, as long as you go by the rule that swapping is an error condition that needs to be dealt with ASAP.

@cybrsaylr,
I'm surprised you don't change the colors on your CPU grid.  It lets you keep track of which core is doing what a little better.

---

### Post by cybrsaylr on 2016-01-07
> **1clue said:**
> I still use the 2xRAM guideline for swap size in systems that have swap at all.  It doesn't hurt to have that much, as long as you go by the rule that swapping is an error condition that needs to be dealt with ASAP.

@cybrsaylr,
I'm surprised you don't change the colors on your CPU grid.  It lets you keep track of which core is doing what a little better.

Have seen some pros and cons for keeping or removing Swap, if you  have a lot or RAM on this board.
Guess it is better to have Swap for when those atypical events strike.

Just changed some of the colors in my CPU grid. Never thought of doing that, or that it could be done until you mentioned it. 
Thanks

---

### Post by Bucky Ball on 2016-01-07
Little off-topic but throwing it in: /home generally resides on the HDD, and /swap, if you have one. Everything else on the SSD.

---

