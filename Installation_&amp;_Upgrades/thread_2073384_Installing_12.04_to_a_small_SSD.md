---
title: "Installing 12.04 to a small SSD"
date: 2012-10-19
forum: Installation &amp; Upgrades
---

### Post by ac0ax on 2012-10-19
Can anyone assist me in installing 12.04 to a 32GB SSD in a laptop with 3GB of ram.

What I mean by assisting is getting the best performance from it. I've been reading a lot post about it but its a clear as mud to noob like myself. 

I think what I really need is a walk-though. Step 1..step 2..etc.

---

### Post by bart.a on 2012-10-23
Can you tell us what your goal is? What hardware have you've got and what do you intend to use it for?

Is it running office related programs or watching movies or mainly using internet based stuff?

---

### Post by bart.a on 2012-10-23
For performance and longer lifetime of your SSD you need to make some changes to the standard filesystem..
You should choose for the ext4 file system on install by the way because it supports TRIM..

**0. partition alignment**

This can only be done with a clean system before you install Linux. Make a new primary partition and enter a start sector of at least 2,048 The general rule is that the starting sector must be divisible by 512, but to cater for all variations of SSD page size and filesystem block size, 2,048 is a good idea (and equates to 1MB).

**1. fstab**

after install open up the terminal (CTRL + T) and run:
```
sudo gedit -w /etc/fstab
```
this should open a text window and you will be able to make changes to the file system. So be carefull.

Then for the SSD device in your system remove 'relatime' if present and add 'noatime,nodiratime,discard' so it looks something like this:
```
/dev/sda   /   ext4   noatime,nodiratime,discard,errors=remount-ro 0 1
```
the 'discard' part activates the TRIM.. the other parts stops updating metadata from being updated every time a file is accessed.

**2. schedular**

The scheduler helps organise reads and writes in the I/O queue to maximise performance. The default scheduler in the Linux kernel is CFQ (Completely Fair Queuing), which is designed with the rotational latencies of spinning platter drives in mind. So while it works well for standard hard drives, it doesn't work so well when it comes to SSDs.
As CFQ is the default, change SSDs to use deadline by opening up a terminal and running:

```
sudo gedit -w /etc/rc.local
```

Then add the following line for each SSD in your system:
 
```
echo deadline >/sys/block/sda/queue/scheduler
```

**3. swap tmp and applications**

Do you have a mechanical drive in your system? Then use a part of it (if you can) to provide for the swap and for temporary files and browser cache. That writes and rewrites a lot of data that you don't realy use longterm but does wear out your SSD.

If you do not have a mechanical drive. Keep a swap partition available, but add the following to the rc.local file:

```
sudo gedit -w /etc/rc.local
```

and add:

```
echo 0 > /proc/sys/vm/swappiness
```

And Linux won't use swap at all unless physical memory is completely filled.

Next, to reduce unnecessary writes to the SSD move the temp directories into a ram disk using the 'tmpfs' filesystem, which dynamically expands and shrinks as needed. 

In your /etc/fstab, add the following:

```
sudo gedit -w /etc/fstab
```

```

tmpfs   /tmp       tmpfs   defaults,noatime,mode=1777   0  0

tmpfs   /var/spool tmpfs   defaults,noatime,mode=1777   0  0

tmpfs   /var/tmp   tmpfs   defaults,noatime,mode=1777   0  0

tmpfs   /var/log   tmpfs   defaults,noatime,mode=0755   0  0

```

the last line discards log files between boots.

That's it.. I found this [here]("http://apcmag.com/how-to-maximise-ssd-performance-with-linux.htm").. So thank you Ashton Mills..

Hope this serves your needs..

---

### Post by geomcd1949 on 2012-10-24
How do you align partitions (sec. 0) without having the operating system installed?

---

### Post by snowpine on 2012-10-24
> **ac0ax said:**
> Can anyone assist me in installing 12.04 to a 32GB SSD in a laptop with 3GB of ram.

What I mean by assisting is getting the best performance from it. I've been reading a lot post about it but its a clear as mud to noob like myself. 

I think what I really need is a walk-though. Step 1..step 2..etc.

Here is an easy 1-2-3 guide to installing Ubuntu on a SSD:

[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)

It is true that there are some optimizations you can make (described by other users in this thread) for a possible *slight* performance boost, but the default easy install should be fine for 99% of users. Ubuntu is designed to run on SSDs and no additional steps are required. :)

---

### Post by bart.a on 2012-10-24
> **snowpine said:**
> It is true that there are some optimizations you can make (described by other users in this thread) for a possible *slight* performance boost, but the default easy install should be fine for 99% of users. Ubuntu is designed to run on SSDs and no additional steps are required. :)

It does work fine on SSD and a default install is fine for 99% of the users, but the OP specifically asked for performance tips.. And I believe the default is still based on revolving mechanical disks, also in the ext4 file system.. And even if I'm wrong about that, the tips given result in less write and rewrite actions which extends the SSD's lifetime..

---

### Post by ac0ax on 2012-11-05
Thank you Bart.a. That seemed to help quite a bit as now the HDD light is not flashing as much as it was before the settings.

---

### Post by bart.a on 2012-11-05
> **ac0ax said:**
> Thank you Bart.a. That seemed to help quite a bit as now the HDD light is not flashing as much as it was before the settings.

Glad I could be of service..

Could you mark your post as [SOLVED]? When you've got all the answers you need that is..

---

