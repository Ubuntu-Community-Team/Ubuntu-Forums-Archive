---
title: "raid1 partition advice"
date: 2010-03-03
forum: Installation &amp; Upgrades
---

### Post by wadehw on 2010-03-03
hi everyone,

After reading many good reviews about using MSI wind PC/ubuntu nas, I rushed to order the barebone. I will using ubuntu server 9.10.

I order two 1 TB WD hds, my plan is to...

1st WD HD:  partition the sda into sda0(100G), sda1(~900G, raid) and sda2(4G, swap)
2nd WD HD: partition the sdb into  sdb0(~1TB, raid )and sdb1(4G, swap)

I will install the ubuntu os into sda0 and use sda2 as its swap,  and configure a raid 1 using sda1 and sdb0.  Since sdb0 is ~100G bigger than sda1, I heard that I will lose the ~100G HD, I am OK with it..

Will this work?  I am new to ubuntu, any comment is welcome.

-Wade

---

### Post by darkod on 2010-03-03
First, the numbering of partitions is starting from 1, not 0.

Any particular reason you want the root partition outside the raid1 array?

Why not:

sda1 - 250MB /boot, sda2 - ~1TB, sda3 - 4GB swap
sdb1 - 250MB /boot, sda2 - ~1TB, sdb3 - 4GB swap

Create software raid1 from sda1 and sdb1, not motherboard fakeraid, and use the 250MB raid1 device for /boot partition. Create software raid1 from sda2 and sdb2 into 1TB raid device.

Then, use the 1TB raid1 device as physical volume for LVM. This will allow you to create any kind of setup you want in the LVM and resize partitions dynamically.

This is just a general idea, I'm not too experienced in this. So any further comments are welcome of course. :)

---

### Post by whoop on 2010-03-03
I have a nas running with software raid 1:

3 raid1 array's:
md0: 15 GB for /
md1: all that is left for /home
md2: 4 GB for swap

So the partitioning for the drives is:
sda1 and sdb1 raid partitions to be used for /
sda2 and sdb2 raid partitions to be used for /home
sda3 and sdb3 raid partitions to be used for swap

As a precaution, it looks like software raid is pretty messed up in Lucid currently, can't seem to get it installed (with any configuration, even separate /boot raid array).
There doesn't seem to be anything wrong with the partitioning or creation of the array's but grub just won't install correctly:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/525425](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/525425)

The configuration I posted as well as darkod's should work for 9.10 though; let's just hope Lucid's raid is working properly when it gets released. 

Partitioning is a little bit art a little bit science ;)

---

### Post by wadehw on 2010-03-03
whoop's setting is close to mine, but I have no idea how to make it..  so I will go with darkod's :)

I read the installation guide to figure out how to configure your setting..
[https://help.ubuntu.com/9.10/serverguide/C/advanced-installation.html](https://help.ubuntu.com/9.10/serverguide/C/advanced-installation.html)

sda1 - 250MB /boot, sda2 - ~1TB, sda3 - 4GB swap
sdb1 - 250MB /boot, sda2 - ~1TB, sdb3 - 4GB swap

But You said..
"Create software raid1 from sda1 and sdb1, not motherboard fakeraid, and use the 250MB raid1 device for /boot partition. Create software raid1 from sda2 and sdb2 into 1TB raid device."

Do I need to create a raid1 for swap?

-Wade :(

---

### Post by darkod on 2010-03-04
> **wadehw said:**
> 

Do I need to create a raid1 for swap?

-Wade :(

I'm not too experienced with raid but I am considering it and reading about it a lot. From what I have seen mentioned about swap, having raid1 is pointless.
In most cases people would add both swap partitions to ubuntu, and there is a setting to set identical priority for both swap partitions. I just can't remember in which file right now.

So the OS itself is using two swap partitions but with identical priority at the same time, not starting to use the second only after the first is full. At least that's how I understood that. In effect, that would be like raid1 swap.

---

### Post by whoop on 2010-03-04
It really is advisable to have a swap raid1 array as well, if you ask me. One of the most important reasons to implement raid1 is uptime.
Consider you have your entire system raided except for swap. Your system is running and using some swap space, the hard-disk containing the (used) swap space breaks, result: your system goes down, if not, bad unpredictable stuff will/can happen.
When you have your swap raided, the above will not happen. You will (sooner or later :D) discover one of the drives is failing, shutdown, replace the drive, and let the system sync for a couple of hours and everything is back as it was.

So to sum it up:
raid1 swap, safer from memory failures, possibly same speed as a single disk.
double non raided swap: not safe from memory failures, possibly faster than a single disk.
single non raided swap: not safe from memory failures, it's on a single disk, so it has the speed of the single disk.

Note, when you use swap speed is important, cause the system uses it as RAM, but raid1 swap is not slow, it's just not faster than normal single disk swap.
Personally I just use swap as a safety matter, if a server of mine uses too much swap too much of the time, I upgrade my ram...

I also advise against using fake raid, it has no real benefit as it makes use of CPU cycles as well, it's proprietary, often less flexible and is not officially supported by Ubuntu. The only time I would use fake raid is with a multiboot with linux and a propriatary OS where both OS's need raid1 access to a mutual partition (I haven't had a need for this yet).

@wadehw: The advise I provided is not more of a challenge to setup than darkod's, if I am not mistaken.

---

### Post by wadehw on 2010-03-04
whoop,

I will remember to raid1 the swap.  

For a newbie like me, I really should buy a offTheShelf NAS. I was confident to build a DIY NAS in the beginning, but I do not feel that any more.  Building a NAS is not easy at all. Lots of skills are needed.  Originally, I thought I can find a successful case on the web and copy its config completely. But I cannot find one so far :(   Most of articles I found uses a CF card to run OS and raid1 the two 1TBs.  I will study their setting to see if their config is easier.  ouch :(

---

### Post by whoop on 2010-03-04
> **wadehw said:**
> whoop,

I will remember to raid1 the swap.  

For a newbie like me, I really should buy a offTheShelf NAS. I was confident to build a DIY NAS in the beginning, but I do not feel that any more.  Building a NAS is not easy at all. Lots of skills are needed.  Originally, I thought I can find a successful case on the web and copy its config completely. But I cannot find one so far :(   Most of articles I found uses a CF card to run OS and raid1 the two 1TBs.  I will study their setting to see if their config is easier.  ouch :(

Don' be scared, take your time, ask questions, experiment, read. It's fun. I'm sure you will be able to pull it off. That raid stuff is just the first fun bit. after that you will need to implement the actual functionality. You could implement that from scratch but you might want to take a look at Ebox for instance (it's in the repos). It's a newbie friendly nas solution, with a web interface. It also gives you real-time information on your raid array's :D

If you still have troubles bending your mind around that raid stuff, start as simple as possible, look at the attachment, it's a very simple software raid1 setup with just a raid1 / and raid1 swap, technically this is feasible. Just try to copy that exactly first (the size of you partitions will be different off course), my initial advise was the same only I made an extra raid1 array for /home. Don't be afraid to make mistakes.

In the screenshot you can see I use two drives, both with two partitions, all of the partitions are partitions for raid, the first partition of each drive is marked as bootable. After that I created two raid array's, using the raid configuration, linked the first array to the first partition of each drive as ext4 / and the second two partitions as swap.

---

